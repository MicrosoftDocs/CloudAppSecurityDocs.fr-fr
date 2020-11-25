---
title: Gestion avancée des collecteurs de journaux
description: Cet article fournit des informations sur la façon dont les tâches de gestion avancées pour Cloud App Security Cloud Discovery des collecteurs de journaux.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/25/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: b003f47c33ef2ed749df3138ed1b6cd2a83232d3
ms.sourcegitcommit: a0a8e25bda77fb21f280a0e504896be85b89ed6f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96034956"
---
# <a name="advanced-log-collector-management"></a>Gestion avancée des collecteurs de journaux

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Cet article fournit des informations sur les options de configuration avancée suivantes pour Cloud App Security Cloud Discovery collecteurs de journaux :

- [Modifier la configuration FTP du collecteur de journaux](#modify-the-log-collector-ftp-configuration)
- [Activer le collecteur de journaux derrière un proxy](#enable-the-log-collector-behind-a-proxy)
- [Déplacer le collecteur de journaux vers une autre partition de données sur Linux](#move-the-log-collector-to-a-different-data-partition-on-linux)
- [Inspecter l’utilisation du disque du collecteur de journaux sur Linux](#inspect-the-log-collector-disk-usage-on-linux)
- [Déplacer le collecteur de journaux vers un hôte accessible](#move-the-log-collector-to-an-accessible-host)
- [Définir des ports personnalisés pour les récepteurs syslog et FTP pour les collecteurs de journaux sur Linux](#define-custom-ports-for-syslog-and-ftp-receivers-for-log-collectors-on-linux)
- [Valider le format du journal et du trafic reçu par log Collector sur Linux](#validate-the-traffic-and-log-format-received-by-log-collector-on-linux)

## <a name="modify-the-log-collector-ftp-configuration"></a>Modifier la configuration FTP du collecteur de journaux

Procédez comme suit pour modifier la configuration de votre Cloud App Security Cloud Discovery ancrage.

### <a name="docker-deployment"></a>Déploiement de Docker

Vous devrez peut-être modifier la configuration de l’Cloud App Security Cloud Discovery ancrage.

#### <a name="changing-the-ftp-password"></a>Modification du mot de passe FTP

1. Connectez-vous à l’hôte du collecteur de journaux.

1. Exécutez `docker exec -it <collector name> pure-pw passwd <ftp user>`

    1. Saisissez le nouveau mot de passe.
    1. Saisissez à nouveau le nouveau mot de passe pour le confirmer.

1. Exécutez `docker exec -it <collector name> pure-pw mkdb` pour appliquer la modification.

    ![modifier le mot de passe FTP](media/log-collector-advanced-tasks/ftp-connect.png)

#### <a name="customize-certificate-files"></a>Personnaliser les fichiers de certificats

Procédez comme suit pour personnaliser les fichiers de certificat que vous utilisez pour sécuriser les connexions à l’arrimeur Cloud Discovery.

1. Ouvrez un client FTP et connectez-vous au collecteur de journaux.

    ![Se connecter au client FTP](media/log-collector-advanced-tasks/ftp-connect.png)

1. Accédez au répertoire `ssl_update`.
1. Chargez les nouveaux fichiers de certificats dans le répertoire `ssl_update` (les noms sont obligatoires).

    ![Charger les fichiers de certificat](media/log-collector-advanced-tasks/new-certs.png)

    - **Pour FTP :** un seul fichier est nécessaire. Le fichier a la clé et les données de certificat, dans cet ordre, et est nommé **pure-ftpd.pem**.
    - **Pour Syslog :** trois fichiers sont nécessaires (**ca.pem**, **server-key.pem et **server-cert.pem**). Si l’un des fichiers est absent, la mise à jour n’a pas lieu.

1. Dans une fenêtre de terminal, exécutez : `docker exec -t <collector name> update_certs` . La commande doit produire une sortie semblable à celle illustrée dans la capture d’écran suivante.

    ![Mettre à jour les fichiers de certificat](media/log-collector-advanced-tasks/update-certs.png)

1. Dans une fenêtre de terminal, exécutez : `docker exec <collector name> chmod -R 700 /etc/ssl/private/` .

## <a name="enable-the-log-collector-behind-a-proxy"></a>Activer le collecteur de journaux derrière un proxy

Une fois que vous avez configuré le collecteur de journaux, si vous travaillez derrière un proxy, le collecteur de journaux peut avoir des difficultés pour envoyer des données à Cloud App Security. Cela peut se produire quand le collecteur de journaux ne fait pas confiance à l’autorité de certification racine du proxy et qu’il ne peut pas se connecter à Microsoft Cloud App Security pour récupérer sa configuration ou charger les journaux reçus.

Procédez comme suit pour activer votre collecteur de journaux derrière un proxy.

>[!NOTE]
> Pour plus d’informations sur la modification des certificats utilisés par le collecteur de journaux pour syslog ou FTP, et pour résoudre les problèmes de connectivité à partir des pare-feu et proxys vers le collecteur de journaux, consultez [modifier la configuration FTP du collecteur de journaux](#modify-the-log-collector-ftp-configuration).
>

### <a name="set-up-the-log-collector-behind-a-proxy"></a>Configurer le collecteur de journaux derrière un proxy

Assurez-vous d’avoir effectué les étapes nécessaires pour l’exécution de Docker sur un ordinateur Windows ou Linux et que vous avez téléchargé l’image Docker Cloud App Security sur l’ordinateur. Pour plus d’informations, consultez [Configurer le chargement automatique des journaux pour des rapports continus](discovery-docker.md).

#### <a name="validate-docker-log-collector-container-creation"></a>Valider la création de conteneur du collecteur de journaux Docker

Dans l’interpréteur de commandes, vérifiez que le conteneur a été créé et qu’il est en cours d’exécution à l’aide de la commande suivante :

```bash
docker ps
```

![docker ps](media/log-collector-advanced-tasks/docker-1.png)

#### <a name="copy-proxy-root-ca-certificate-to-the-container"></a>Copier le certificat d’autorité de certification racine du proxy sur le conteneur

À partir de votre machine virtuelle, copiez le certificat d’autorité de certification sur le conteneur Cloud App Security. Dans l’exemple suivant, le conteneur est nommé *Ubuntu-LogCollector* et le certificat d’autorité de certification est nommé *Proxy-CA.crt*.
Exécutez la commande sur l’hôte Ubuntu. La commande copie le certificat dans un dossier du conteneur d’exécution :

```bash
docker cp Proxy-CA.crt Ubuntu-LogCollector:/var/adallom/ftp/discovery
```

#### <a name="set-the-configuration-to-work-with-the-ca-certificate"></a>Définir la configuration pour qu’elle fonctionne avec le certificat d’autorité de certification

1. Accédez au conteneur, à l’aide de la commande suivante. Cela ouvre bash dans le conteneur du collecteur de journaux :

    ```bash
    docker exec -it Ubuntu-LogCollector /bin/bash
    ```

1. Dans une fenêtre bash à l’intérieur du conteneur, accédez au `jre` dossier Java. Pour éviter une erreur de chemin d’accès liée à la version, utilisez la commande suivante :

    ```bash
    cd "$(find /opt/jdk/*/jre -name "bin" -printf '%h' -quit)"
    cd bin
    ```

1. Importez le certificat racine que vous avez copié précédemment, à partir du dossier de *découverte* dans le magasin de clés Java et définissez un mot de passe. Le mot de passe par défaut est « changeit ». Pour plus d’informations sur la modification du mot de passe, consultez [Comment modifier le mot de passe du magasin de clés Java](#how-to-change-the-java-keystore-password).

    ```bash
    ./keytool --import --noprompt --trustcacerts --alias SelfSignedCert --file /var/adallom/ftp/discovery/Proxy-CA.crt --keystore ../lib/security/cacerts --storepass <password>
    ```

1. Confirmez que le certificat a été importé correctement dans le magasin de clés d’autorité de certification, en utilisant la commande suivante pour rechercher l’alias que vous avez fourni lors de l’importation (*SelfSignedCert*) :

    ```bash
    ./keytool --list --keystore ../lib/security/cacerts | grep self
    ```

    ![keytool](media/log-collector-advanced-tasks/docker-2.png "keytool")

Votre certificat d’autorité de certification de proxy importé doit s’afficher.

#### <a name="set-the-log-collector-to-run-with-the-new-configuration"></a>Configurer le collecteur de journaux pour qu’il s’exécute avec la nouvelle configuration

Le conteneur est maintenant prêt.

Exécutez la commande **collector_config** à l’aide du jeton d’API que vous avez utilisé lors de la création de votre collecteur de journaux :

![Jeton d’API](media/log-collector-advanced-tasks/docker-3.png "Jeton d’API")

Lorsque vous exécutez la commande, spécifiez votre propre jeton d’API :

```bash
collector_config abcd1234abcd1234abcd1234abcd1234 ${CONSOLE} ${COLLECTOR}
```

![Mise à jour de la configuration](media/log-collector-advanced-tasks/docker-4.png "Mise à jour de la configuration")

Le collecteur de journaux est désormais en mesure de communiquer avec Cloud App Security. Après lui avoir envoyé des données, l’état passe de **Sain** à **Connecté** dans le portail Cloud App Security.

![État](media/log-collector-advanced-tasks/docker-5.png "Statut")

>[!NOTE]
> Si vous devez mettre à jour la configuration du collecteur de journaux, pour ajouter ou supprimer une source de données, par exemple, vous devez normalement **supprimer** le conteneur et effectuer de nouveau les étapes précédentes. Pour éviter cela, vous pouvez réexécuter l’outil *collector_config* avec le nouveau jeton d’API généré dans le portail Cloud App Security.

### <a name="how-to-change-the-java-keystore-password"></a>Modification du mot de passe du magasin de clés Java

1. Arrêtez le serveur keystore Java.

<!-- /opt/jdk/amazon-corretto-8.222.10.1-linux-x64/jre/lib/security -->

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

## <a name="move-the-log-collector-to-a-different-data-partition-on-linux"></a>Déplacer le collecteur de journaux vers une autre partition de données sur Linux

De nombreuses entreprises ont besoin de déplacer des données vers une partition distincte. Procédez comme suit pour déplacer vos images du collecteur de journaux d’ancrage Cloud App Security vers une partition de données sur votre hôte Linux.

Les étapes suivantes décrivent le déplacement des données vers une partition nommée *datastore* et suppose que vous avez déjà monté la partition.

> [!NOTE]
> L’ajout et la configuration d’une nouvelle partition sur votre hôte Linux ne sont pas dans le cadre de ce guide.

![Liste des partitions Linux](media/log-collector-advanced-tasks/move-lc-new-partition-linux-disk-list.png)

1. Arrêtez le service d’ancrage à l’aide de cette commande :

    ```bash
    service docker stop
    ```

1. Déplacez les données du collecteur de journaux vers la nouvelle partition à l’aide de la commande suivante :

    ```bash
    mv /var/lib/docker /datastore/docker
    ```

1. Supprimez l’ancien répertoire de stockage de l’arrimeur (/var/lib/docker) et créez un lien symbolique vers le nouveau répertoire (/datastore/docker).

    ```bash
    rm -rf /var/lib/docker && ln -s /datastore/docker /var/lib/
    ```

1. Démarrez le service d’ancrage à l’aide de cette commande :

    ```bash
    service docker start
    ```

1. Vérifiez éventuellement l’état de votre collecteur de journaux à l’aide de la commande suivante :

    ```bash
    docker ps
    ```

## <a name="inspect-the-log-collector-disk-usage-on-linux"></a>Inspecter l’utilisation du disque du collecteur de journaux sur Linux

Procédez comme suit pour vérifier l’utilisation du disque et l’emplacement de votre collecteur de journaux.

1. Identifiez le chemin d’accès au répertoire où sont stockées les données du collecteur de journaux à l’aide de cette commande :

    ```bash
    docker inspect <collector_name> | grep WorkDir
    ```

    ![Identifier le répertoire du collecteur de journaux](media/log-collector-advanced-tasks/inspect-lc-linux-disk-usage-directory.png)

1. Obtient la taille sur le disque du collecteur de journaux à l’aide du chemin d’accès identifié sans le suffixe « /Work » :

    ```bash
    du -sh /var/lib/docker/overlay2/<log_collector_id>/
    ```

    ![Obtient la taille du collecteur de journaux sur le disque](media/log-collector-advanced-tasks/inspect-lc-linux-disk-usage-size.png)

    > [!NOTE]
    > Si vous avez seulement besoin de connaître la taille sur le disque, vous pouvez utiliser cette commande : `docker ps -s`

## <a name="move-the-log-collector-to-an-accessible-host"></a>Déplacer le collecteur de journaux vers un hôte accessible

Dans les environnements réglementés, l’accès aux hubs d’ancrage où l’image du collecteur de journaux est hébergée peut être bloqué. Cela empêche Cloud App Security d’importer les données du collecteur de journaux et peut être résolu en déplaçant l’image du collecteur de journaux vers un hôte accessible.

Procédez comme suit pour télécharger l’image du collecteur de journaux à l’aide d’un ordinateur qui a accès au hub Dockr et l’importer sur votre ordinateur hôte de destination.

> [!NOTE]
>
> - L’image téléchargée peut être importée dans votre dépôt privé ou directement sur votre hôte. Les étapes suivantes vous guident tout au long du téléchargement de votre image du collecteur de journaux sur votre ordinateur Windows, puis utilise WinSCP pour déplacer le collecteur de journaux vers votre hôte de destination.
> - Pour installer l’ordinateur de la station d’accueil sur votre ordinateur hôte, téléchargez le système d’exploitation de votre choix :
>   - https://download.docker.com/linux/ubuntu
>   - https://download.docker.com/linux/centos/
>   - https://download.docker.com/linux/rhel/
>
> Après le téléchargement, utilisez le [Guide d’installation hors connexion](https://docs.docker.com/datacenter/dtr/2.0/install/install-dtr-offline/#download-the-offline-package) pour installer le système d’exploitation.

Démarrez le processus en [exportant l’image du collecteur de journaux](#export-the-log-collector-image-from-your-docker-hub) , puis [importez l’image sur votre ordinateur hôte de destination](#import-and-load-the-log-collector-image-to-your-destination-host).

### <a name="export-the-log-collector-image-from-your-docker-hub"></a>Exporter l’image du collecteur de journaux à partir de votre Hub Dockr

Utilisez les étapes relatives au système d’exploitation du concentrateur de l’ordinateur d’amarrage dans lequel se trouve l’image du collecteur de journaux.

#### <a name="exporting-the-image-on-linux"></a>Exportation de l’image sur Linux

1. Sur un ordinateur Linux qui a accès au hub Dockr, exécutez la commande suivante. L’image du collecteur de journaux est alors installée et téléchargée.

    ```bash
    curl -o /tmp/MCASInstallDocker.sh https://adaprodconsole.blob.core.windows.net/public-files/MCASInstallDocker.sh && chmod +x /tmp/MCASInstallDocker.sh; /tmp/MCASInstallDocker.sh
    ```

1. Exportez l’image du collecteur de journaux.

    ```bash
    docker save --output /tmp/mcasLC.targ mcr.microsoft.com/mcas/logcollector
    chmod +r /tmp/mcasLC.tar
    ```

    > [!NOTE]
    > Il est important d’utiliser le paramètre de **sortie** pour écrire dans un fichier, au lieu de *stdout*.

1. Téléchargez l’image du collecteur de journaux sur votre ordinateur Windows sous `C:\mcasLogCollector\` à l’aide de WinSCP.

    ![Télécharger le collecteur de journaux sur l’ordinateur Windows](media/log-collector-advanced-tasks/move-lc-to-accessible-host-download-linux-winscp.png)

#### <a name="exporting-the-image-on-windows"></a>Exportation de l’image sur Windows

1. Sur un ordinateur Windows 10 qui a accès au concentrateur de l’Ancreur, installez le Bureau de l' [amarrage](https://docs.docker.com/docker-for-windows/install/).

1. Téléchargez l’image du collecteur de journaux.

    ```dos
    docker login -u caslogcollector -p C0llector3nthusiast
    docker pull mcr.microsoft/mcas/logcollector
    ```

1. Exportez l’image du collecteur de journaux.

    ```dos
    docker save --output C:\mcasLogCollector\mcasLC.targ mcr.microsoft.com/mcas/logcollector
    ```

    > [!NOTE]
    > Il est important d’utiliser le paramètre de **sortie** pour écrire dans un fichier, au lieu de *stdout*.

### <a name="import-and-load-the-log-collector-image-to-your-destination-host"></a>Importer et charger l’image du collecteur de journaux sur votre hôte de destination

Procédez comme suit pour transférer l’image exportée vers votre ordinateur hôte de destination.

1. Chargez l’image du collecteur de journaux sur votre ordinateur hôte de destination sous `/tmp/` .

    ![Charger le collecteur de journaux sur l’hôte de destination](media/log-collector-advanced-tasks/move-lc-to-accessible-host-upload-host-winscp.png)

1. Sur l’ordinateur hôte de destination, importez l’image du collecteur de journaux dans le référentiel d’images de l’arrimeur à l’aide de la commande suivante :

    ```bash
    docker load --input /tmp/mcasLC.tar
    ```

    ![Importer l’image du collecteur de journaux dans le référentiel de l’ancrage](media/log-collector-advanced-tasks/move-lc-to-accessible-host-import-docker-repo.png)

1. Si vous le souhaitez, vérifiez que l’importation s’est terminée avec succès à l’aide de cette commande :

    ```bash
    docker image ls
    ```

    ![Vérifier que l’importation d’image du collecteur de journaux a réussi](media/log-collector-advanced-tasks/move-lc-to-accessible-host-verify-docker-image.png)

    Vous pouvez maintenant commencer à [créer votre collecteur de journaux](discovery-docker.md) à l’aide de l’image de l’hôte de destination.

## <a name="define-custom-ports-for-syslog-and-ftp-receivers-for-log-collectors-on-linux"></a>Définir des ports personnalisés pour les récepteurs syslog et FTP pour les collecteurs de journaux sur Linux

Certaines organisations ont besoin de définir des ports personnalisés pour les services syslog et FTP.
Lorsque vous ajoutez une source de données, Cloud App Security collecteurs de journaux utilise des numéros de port spécifiques pour écouter les journaux de trafic d’une ou plusieurs sources de données.

Le tableau suivant répertorie les ports d’écoute par défaut pour les récepteurs :

| Type de récepteur | Ports |
| --- | --- |
| syslog | \* UDP/514-UDP/51x<br />\* TCP/601-TCP/60X |
| FTP | \* TCP/21 |

Procédez comme suit pour définir des ports personnalisés.

1. Dans Cloud App Security, cliquez sur l’icône des paramètres, puis sur **collecteurs de journaux**.

1. Dans l’onglet **collecteurs de journaux** , ajoutez ou modifiez un collecteur de journaux et, après la mise à jour des sources de données, copiez la commande exécuter à partir de la boîte de dialogue.

    ![Copier la commande exécuter à partir de l’Assistant collecteur de journaux](media/log-collector-advanced-tasks/define-lc-custom-ports-copy-default-run-command.png)

    > [!NOTE]
    > S’il est utilisé comme fourni, la commande fournie par l’Assistant Configure le collecteur de journaux pour utiliser les ports 514/UDP et 515/UDP.
    >
    > ```bash
    > (echo <credentials>) | docker run --name LogCollector1 -p 514:514/udp -p 515:515/udp -p 21:21 -p 20000-20099:20000-20099 -e "PUBLICIP='10.0.0.100'" -e "PROXY=" -e "SYSLOG=true" -e "CONSOLE=machine.us2.portal.cloudappsecurity.com" -e "COLLECTOR=LogCollector1" --security-opt apparmor:unconfined --cap-add=SYS_ADMIN --restart unless-stopped -a stdin -i mcr.microsoft.com/mcas/logcollector starter
    > ```
    >
    > ![Exécuter la commande à partir de l’Assistant collecteur de journaux](media/log-collector-advanced-tasks/define-lc-custom-ports-default-run-command.png)

1. Avant d’utiliser la commande sur votre ordinateur hôte, modifiez la commande pour utiliser vos ports personnalisés. Par exemple, pour configurer le collecteur de journaux afin d’utiliser les ports UDP 414 et 415, modifiez la commande comme suit :

    ```bash
    (echo <credentials>) | docker run --name LogCollector1 -p 414:514/udp -p 415:515/udp -p 21:21 -p 20000-20099:20000-20099 -e "PUBLICIP='10.0.0.100'" -e "PROXY=" -e "SYSLOG=true" -e "CONSOLE=machine.us2.portal.cloudappsecurity.com" -e "COLLECTOR=LogCollector1" --security-opt apparmor:unconfined --cap-add=SYS_ADMIN --restart unless-stopped -a stdin -i mcr.microsoft.com/mcas/logcollector starter
    ```

    ![Exécuter une commande personnalisée sur votre hôte](media/log-collector-advanced-tasks/define-lc-custom-ports-custom-run-command.png)

    > [!NOTE]
    > Seul le mappage de l’ancrage est modifié. Les ports attribués en interne ne sont pas modifiés, ce qui vous permet de choisir n’importe quel port d’écoute sur l’ordinateur hôte.

## <a name="validate-the-traffic-and-log-format-received-by-log-collector-on-linux"></a>Valider le format du journal et du trafic reçu par log Collector sur Linux

Parfois, vous devrez peut-être examiner des problèmes tels que les suivants :

- **Les collecteurs de journaux reçoivent des données**: Vérifiez que les collecteurs de journaux reçoivent des messages syslog de vos appliances et ne sont pas bloqués par les pare-feu.
- Les **données reçues sont au format de journal correct**: validez le format du journal pour vous aider à résoudre les erreurs d’analyse en comparant le format de journal attendu par Cloud App Security et celui envoyé par votre appliance.

Procédez comme suit pour valider le trafic reçu par les collecteurs de journaux.

1. Connectez-vous à votre serveur hébergeant le conteneur d’ancrage.

1. Vérifiez que log Collector reçoit des messages syslog en utilisant l’une des méthodes suivantes :

    - À l’aide de *tcpdump* ou d’une commande similaire pour analyser le trafic réseau sur le port 514 :

        ```bash
        tcpdump -Als0 port 514
        ```

        Si tout est correctement configuré, vous devriez voir le trafic réseau de vos appliances.

        ![Commande analyser le trafic réseau tcpdump](media/log-collector-advanced-tasks/validate-traffic-and-log-format-tcpdump-analyze-traffic.png)

    - À l’aide de *netcat*, ou d’une commande similaire pour analyser le trafic réseau sur l’ordinateur hôte :

        1. Installez *netcat* et *wget*.

        1. Téléchargez et, si nécessaire, décompressez un exemple de journal, comme suit :
            1. Dans le portail Cloud App Security, cliquez sur **découvrir**, puis sur **créer un rapport d’instantané**.
            1. Sélectionnez la **source de données** à partir de laquelle vous souhaitez charger les fichiers journaux.
            1. Cliquez sur **afficher et vérifier** , puis cliquez avec le bouton droit sur **Télécharger l’exemple de journal** et copiez le lien adresse URL.
            1. Cliquez sur **Fermer**.
            1. Cliquez sur **Annuler**.

        ```bash
        wget <URL_address_to_sample_log>
        ```

        1. Exécutez `netcat` pour diffuser les données dans le collecteur de journaux.

        ```bash
        cat <path_to_downloaded_sample_log>.log | nc -w 0 localhost <datasource_port>
        ```

        Si le collecteur est correctement configuré, les données du journal sont présentes dans le fichier de messages et, peu après, elles sont téléchargées vers le portail Cloud App Security.

    - En inspectant les fichiers appropriés au sein du conteneur Cloud App Security ancrage :
        1. Connectez-vous au conteneur à l’aide de la commande suivante :

        ```bash
        docker exec -it <Container Name> bash
        ```

        1. Déterminez si les messages syslog sont écrits dans le fichier de messages à l’aide de cette commande :

        ```bash
        cat /var/adallom/syslog/<your_log_collector_port>/messages
        ```

        Si tout est correctement configuré, vous devriez voir le trafic réseau de vos appliances.

        > [!NOTE]
        > Ce fichier sera toujours écrit dans jusqu’à ce qu’il atteigne la taille de 40 Ko.

        ![Commande analyser le trafic réseau CAT](media/log-collector-advanced-tasks/validate-traffic-and-log-format-cat-analyze-traffic.png)

1. Examinez les journaux qui ont été téléchargés vers Cloud App Security dans le `/var/adallom/discoverylogsbackup` répertoire.

    ![Examiner les fichiers journaux chargés](media/log-collector-advanced-tasks/validate-traffic-and-log-format-review-uploaded-logs.png)

1. Validez le format de journal reçu par le collecteur de journaux en comparant les messages stockés dans `/var/adallom/discoverylogsbackup` à l’exemple de format de journal fourni dans l’assistant Cloud App Security **créer un collecteur de journaux** .

> [!NOTE]
> Si vous souhaitez utiliser votre propre exemple de journal, mais que vous n’avez pas accès à l’appliance, utilisez les commandes suivantes pour écrire la sortie du fichier de *messages* (situé dans le répertoire syslog du collecteur de og) dans un fichier local sur l’ordinateur hôte.
>
> ```bash
> docker exec CustomerLogCollectorName tail -f -q /var/adallom/syslog/<datasource_port>/messages > /tmp/log.log
> ```
>
> Comparez le fichier de sortie ( `/tmp/log.log` ) aux messages stockés dans `/var/adallom/discoverylogsbackup` .

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Déployer Cloud Discovery](set-up-cloud-discovery.md)

> [!div class="nextstepaction"]
> [Stratégies d’activité utilisateur](user-activity-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
