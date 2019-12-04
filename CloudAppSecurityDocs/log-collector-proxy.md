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
ms.openlocfilehash: db16695ffa6cc9c20d04616553256cba95de1550
ms.sourcegitcommit: 7c93b6f93d2699d466b172590710ed01697bbdad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74720524"
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

![dockr PS](media/docker-1.png)

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

2. À partir de bash dans le conteneur, accédez au répertoire jre Java. Pour éviter une erreur de chemin liée à la version, utilisez la commande suivante :

    ```bash
    cd 'find /opt/jdk/*/jre -iname bin'
    ```

3. Importez le certificat racine, que vous avez copié précédemment, à partir du dossier *discovery* dans le magasin de clés Java et définissez un mot de passe. Le mot de passe par défaut est « changeit » :

    ```bash
    ./keytool --import --noprompt --trustcacerts --alias SelfSignedCert --file /var/adallom/ftp/discovery/Proxy-CA.crt --keystore ../lib/security/cacerts --storepass changeit
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

![Statu](media/docker-5.png "Status")

>[!NOTE]
> Si vous devez mettre à jour la configuration du collecteur de journaux, pour ajouter ou supprimer une source de données, par exemple, vous devez normalement **supprimer** le conteneur et effectuer de nouveau les étapes précédentes. Pour éviter cela, vous pouvez réexécuter l’outil *collector_config* avec le nouveau jeton d’API généré dans le portail Cloud App Security.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Stratégies d’activité utilisateur](user-activity-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
