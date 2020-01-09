---
title: Activer le collecteur de journaux derrière un proxy - Cloud App Security | Microsoft Docs
description: Cet article fournit des informations sur la façon d’activer le collecteur de journaux Cloud App Security Cloud Discovery derrière un proxy.
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
ms.openlocfilehash: c5d4132dd88f8bf7364a77ee8a3e282c1af7fa02
ms.sourcegitcommit: 010725c70ff7b3fc9abdad92203eec6e72bb7473
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/26/2019
ms.locfileid: "75492086"
---
# <a name="enable-the-log-collector-behind-a-proxy"></a>Activer le collecteur de journaux derrière un proxy

Une fois que vous avez configuré le collecteur de journaux, si vous travaillez derrière un proxy, le collecteur de journaux peut avoir des difficultés pour envoyer des données à Cloud App Security. Cela peut se produire quand le collecteur de journaux ne fait pas confiance à l’autorité de certification racine du proxy et qu’il ne peut pas se connecter à Microsoft Cloud App Security pour récupérer sa configuration ou charger les journaux reçus.

>[!NOTE]
> Pour plus d’informations sur la façon de modifier les certificats utilisés par le collecteur de journaux pour syslog ou FTP, et pour résoudre les problèmes de connectivité à partir des pare-feu et proxys vers le collecteur de journaux, consultez [configuration du protocole FTP du collecteur de journaux](log-collector-ftp.md).
>

## <a name="set-up-the-log-collector-behind-a-proxy"></a>Configurer le collecteur de journaux derrière un proxy

Assurez-vous d’avoir effectué les étapes nécessaires pour l’exécution de Docker sur un ordinateur Windows ou Linux et que vous avez téléchargé l’image Docker Cloud App Security sur l’ordinateur. Pour plus d’informations, consultez [Configurer le chargement automatique des journaux pour des rapports continus](discovery-docker.md).

### <a name="validate-docker-log-collector-container-creation"></a>Valider la création de conteneur du collecteur de journaux Docker

Dans l’interpréteur de commandes, vérifiez que le conteneur a été créé et qu’il est en cours d’exécution à l’aide de la commande suivante :

```bash
docker ps
```

![docker ps](media/docker-1.png)

### <a name="copy-proxy-root-ca-certificate-to-the-container"></a>Copier le certificat d’autorité de certification racine du proxy sur le conteneur

À partir de votre machine virtuelle, copiez le certificat d’autorité de certification sur le conteneur Cloud App Security. Dans l’exemple suivant, le conteneur est nommé *Ubuntu-LogCollector* et le certificat d’autorité de certification est nommé *Proxy-CA.crt*.
Exécutez la commande sur l’hôte Ubuntu. La commande copie le certificat dans un dossier du conteneur d’exécution :

```bash
docker cp Proxy-CA.crt Ubuntu-LogCollector:/var/adallom/ftp/discovery
```

### <a name="set-the-configuration-to-work-with-the-ca-certificate"></a>Définir la configuration pour qu’elle fonctionne avec le certificat d’autorité de certification

1. Accédez au conteneur, à l’aide de la commande suivante. Cela ouvre bash dans le conteneur du collecteur de journaux :

    ```bash
    docker exec -it Ubuntu-LogCollector /bin/bash
    ```

2. À partir de l’bash dans le conteneur, accédez au dossier Java *JRE* . Pour éviter une erreur de chemin liée à la version, utilisez la commande suivante :

    ```bash
    cd 'find /opt/jdk/*/jre -iname bin'
    ```

3. Importez le certificat racine que vous avez copié précédemment, à partir du dossier de *découverte* dans le magasin de clés Java et définissez un mot de passe. Le mot de passe par défaut est « changeit ». Pour plus d’informations sur la modification du mot de passe, consultez [Comment modifier le mot de passe du magasin de clés Java](#how-to-change-the-java-keystore-password).

    ```bash
    ./keytool --import --noprompt --trustcacerts --alias SelfSignedCert --file /var/adallom/ftp/discovery/Proxy-CA.crt --keystore ../lib/security/cacerts --storepass <password>
    ```

4. Confirmez que le certificat a été importé correctement dans le magasin de clés d’autorité de certification, en utilisant la commande suivante pour rechercher l’alias que vous avez fourni lors de l’importation (*SelfSignedCert*) :

    ```bash
    ./keytool --list --keystore ../lib/security/cacerts | grep self
    ```

    ![keytool](media/docker-2.png "keytool")

Votre certificat d’autorité de certification de proxy importé doit s’afficher.

### <a name="set-the-log-collector-to-run-with-the-new-configuration"></a>Configurer le collecteur de journaux pour qu’il s’exécute avec la nouvelle configuration

Le conteneur est maintenant prêt.

Exécutez la commande **collector_config** à l’aide du jeton d’API que vous avez utilisé lors de la création de votre collecteur de journaux :

![Jeton d’API](media/docker-3.png "Jeton d’API")

Lorsque vous exécutez la commande, spécifiez votre propre jeton d’API :

```bash
collector_config abcd1234abcd1234abcd1234abcd1234 ${CONSOLE} ${COLLECTOR}
```

![Mise à jour de la configuration](media/docker-4.png "Mise à jour de la configuration")

Le collecteur de journaux est désormais en mesure de communiquer avec Cloud App Security. Après lui avoir envoyé des données, l’état passe de **Sain** à **Connecté** dans le portail Cloud App Security.

![Statut](media/docker-5.png "Status")

>[!NOTE]
> Si vous devez mettre à jour la configuration du collecteur de journaux, pour ajouter ou supprimer une source de données, par exemple, vous devez normalement **supprimer** le conteneur et effectuer de nouveau les étapes précédentes. Pour éviter cela, vous pouvez réexécuter l’outil *collector_config* avec le nouveau jeton d’API généré dans le portail Cloud App Security.

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

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Stratégies d’activité utilisateur](user-activity-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
