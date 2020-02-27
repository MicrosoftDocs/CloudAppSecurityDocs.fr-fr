---
title: Activer le collecteur de journaux derrière un proxy-Cloud App Security | Microsoft Docs
description: Cet article fournit des informations sur la façon d’activer l’Cloud App Security Cloud Discovery collecteur de journaux à partir d’un proxy.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 8/6/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 2b6d888c90a3e21ee98002372c16484f6a471610
ms.sourcegitcommit: d340917143d37ded0dd342a277a1b6ad267f9a7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77618449"
---
# <a name="enable-the-log-collector-behind-a-proxy"></a>Activer le collecteur de journaux derrière un proxy

Une fois que vous avez configuré le collecteur de journaux, si vous exécutez derrière un proxy, le collecteur de journaux peut avoir des difficultés à envoyer des données à Cloud App Security. Cela peut se produire si le collecteur de journaux n’approuve pas l’autorité de certification racine du proxy et n’est pas en mesure de se connecter à Microsoft Cloud App Security pour récupérer sa configuration ou charger les journaux reçus.

>[!NOTE]
> Pour plus d’informations sur la façon de modifier les certificats utilisés par le collecteur de journaux pour syslog ou FTP, et pour résoudre les problèmes de connectivité à partir des pare-feu et proxys vers le collecteur de journaux, consultez [configuration du protocole FTP du collecteur de journaux](log-collector-ftp.md).
>

## <a name="set-up-the-log-collector-behind-a-proxy"></a>Configurer le collecteur de journaux derrière un proxy

Assurez-vous que vous avez effectué les étapes nécessaires sur un ordinateur Windows ou Linux et que vous avez téléchargé le Cloud App Security image de l’arrimeur sur l’ordinateur. Pour plus d’informations, consultez [configurer le chargement automatique des journaux pour les rapports continus](discovery-docker.md).

### <a name="validate-docker-log-collector-container-creation"></a>Valider la création du conteneur du collecteur de journaux de l’ancrage

Dans l’interpréteur de commandes, vérifiez que le conteneur a été créé et qu’il s’exécute à l’aide de la commande suivante :

```bash
docker ps
```

![dockr PS](media/docker-1.png)

### <a name="copy-proxy-root-ca-certificate-to-the-container"></a>Copier le certificat d’autorité de certification racine du proxy dans le conteneur

À partir de votre machine virtuelle, copiez le certificat d’autorité de certification dans le conteneur Cloud App Security. Dans l’exemple suivant, le conteneur est nommé *Ubuntu-LogCollector* et le certificat de l’autorité de certification est nommé *proxy-ca. CRT*.
Exécutez la commande sur l’hôte Ubuntu. Il copie le certificat dans un dossier dans le conteneur en cours d’exécution :

```bash
docker cp Proxy-CA.crt Ubuntu-LogCollector:/var/adallom/ftp/discovery
```

### <a name="set-the-configuration-to-work-with-the-ca-certificate"></a>Définir la configuration de façon à ce qu’elle fonctionne avec le certificat de l’autorité de certification

1. Accédez au conteneur à l’aide de la commande suivante. Il ouvre bash dans le conteneur log Collector :

    ```bash
    docker exec -it Ubuntu-LogCollector /bin/bash
    ```

2. À partir de l’bash dans le conteneur, accédez au dossier Java *JRE* . Pour éviter une erreur de chemin d’accès liée à la version, utilisez la commande suivante :

    ```bash
    cd "$(find /opt/jdk/*/jre -name "bin" -printf '%h' -quit)"
    ```

3. Importez le certificat racine que vous avez copié précédemment, à partir du dossier de *découverte* dans le magasin de clés Java et définissez un mot de passe. Le mot de passe par défaut est « changeit ». Pour plus d’informations sur la modification du mot de passe, consultez [Comment modifier le mot de passe du magasin de clés Java](#how-to-change-the-java-keystore-password).

    ```bash
    ./keytool --import --noprompt --trustcacerts --alias SelfSignedCert --file /var/adallom/ftp/discovery/Proxy-CA.crt --keystore ../lib/security/cacerts --storepass <password>
    ```

4. Vérifiez que le certificat a été importé correctement dans le magasin de clés de l’autorité de certification, en utilisant la commande suivante pour Rechercher l’alias que vous avez fourni lors de l’importation (*SelfSignedCert*) :

    ```bash
    ./keytool --list --keystore ../lib/security/cacerts | grep self
    ```

    ![keytool](media/docker-2.png "keytool")

Vous devez voir votre certificat d’autorité de certification proxy importé.

### <a name="set-the-log-collector-to-run-with-the-new-configuration"></a>Définir le collecteur de journaux pour qu’il s’exécute avec la nouvelle configuration

Le conteneur est maintenant prêt.

Exécutez la commande **collector_config** à l’aide du jeton d’API que vous avez utilisé lors de la création de votre collecteur de journaux :

![Jeton d’API](media/docker-3.png "Jeton d’API")

Quand vous exécutez la commande, spécifiez votre propre jeton d’API :

```bash
collector_config abcd1234abcd1234abcd1234abcd1234 ${CONSOLE} ${COLLECTOR}
```

![Mise à jour de la configuration](media/docker-4.png "Mise à jour de la configuration")

Le collecteur de journaux peut désormais communiquer avec Cloud App Security. Une fois les données envoyées, l’état passe de **sain** à **connecté** dans le portail Cloud App Security.

![État](media/docker-5.png "Statut")

>[!NOTE]
> Si vous devez mettre à jour la configuration du collecteur de journaux, pour ajouter ou supprimer une source de données par exemple, vous devez normalement **supprimer** le conteneur et effectuer à nouveau les étapes précédentes. Pour éviter ce risque, vous pouvez réexécuter l’outil *collector_config* avec le nouveau jeton d’API généré dans le portail Cloud App Security.

## <a name="how-to-change-the-java-keystore-password"></a>Modification du mot de passe du magasin de clés Java

1. Arrêtez le serveur keystore Java.
1. Ouvrez un interpréteur de commandes bash dans le conteneur et accédez au dossier *AppData/conf* .
1. Modifiez le mot de passe du magasin de clés du serveur à l’aide de la commande suivante :

    ```bash
    keytool -storepasswd -new newStorePassword -keystore server.keystore
    -storepass changeit
    ```

    > [!NOTE]
    > Le mot de passe du serveur par défaut est *changeit*.

1. Modifiez le mot de passe du certificat à l’aide de la commande suivante :

    ```bash
    keytool -keypasswd -alias server -keypass changeit -new newKeyPassword -keystore server.keystore -storepass newStorePassword
    ```

    > [!NOTE]
    > L’alias de serveur par défaut est *Server*.

1. Dans un éditeur de texte, ouvrez le fichier *Server-install\conf\server\secured-installed.Properties* , puis ajoutez les lignes de code suivantes, puis enregistrez les modifications :
    1. Spécifiez le nouveau mot de passe du magasin de clés Java pour le serveur : `server.keystore.password=newStorePassword`
    1. Spécifiez le nouveau mot de passe du certificat pour le serveur : `server.key.password=newKeyPassword`
1. Démarrez le serveur.

## <a name="next-steps"></a>Étapes suivantes :

> [!div class="nextstepaction"]
> [Stratégies d’activité utilisateur](user-activity-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
