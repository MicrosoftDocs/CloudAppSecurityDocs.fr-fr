---
title: Configurer le chargement automatique de journal à l’aide de Docker en local
description: Cet article décrit la procédure de configuration du chargement automatique des journaux pour des rapports continus dans Cloud App Security à l’aide d’un Docker sur un serveur Ubuntu ou RHEL local.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/19/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 12e09ac4a3f7e15aecbdac15c781e59f618850ac
ms.sourcegitcommit: aa227a88d09eff15953d10663386f85ff68095b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74203518"
---
# <a name="docker-on-ubuntu-and-rhel-on-premises"></a>Docker sur Ubuntu et RHEL (local)

*S’applique à : Microsoft Cloud App Security*

Vous pouvez configurer le chargement automatique des journaux pour des rapports continus dans Cloud App Security à l’aide d’un Docker sur un serveur Ubuntu ou RHEL local.

## <a name="technical-requirements"></a>Spécifications techniques

* OS: Ubuntu 14.04, 16.04, and 18.04; RHEL 7.2 or higher, or CentOS 7.2 or higher 

* Espace disque : 250 Go

* Processeur : 2

* RAM : 4 Go

* Configurez votre pare-feu, comme décrit dans [Configuration réseau requise](network-requirements.md#log-collector)

> [!NOTE]
> If you have an existing log collector and want to remove it before deploying it again, or if you simply want to remove it, run the following commands:
>
> ```console
> docker stop <collector_name>
> docker rm <collector_name>
> ```

## <a name="log-collector-performance"></a>Performances du collecteur de journaux

Le collecteur de journaux peut gérer correctement une capacité allant jusqu’à 50 Go par heure. Les principaux goulots d’étranglement dans le processus de collecte des journaux sont les suivants :

* Bande passante réseau - Votre bande passante réseau détermine la vitesse de chargement des journaux.

* Performances d’E/S de la machine virtuelle - Détermine la vitesse à laquelle les journaux sont écrits sur le disque du collecteur de journaux. Le collecteur de journaux dispose d’un mécanisme de sécurité intégré qui surveille le débit auquel les journaux arrivent et le compare au débit de chargement. En cas de congestion, le collecteur de journaux commence à supprimer des fichiers journaux. Si votre configuration dépasse généralement 50 Go par heure, nous vous recommandons de diviser le trafic entre plusieurs collecteurs de journaux.

## <a name="set-up-and-configuration"></a>Installation et configuration  

### <a name="step-1--web-portal-configuration-define-data-sources-and-link-them-to-a-log-collector"></a>Étape 1 : configuration du portail web  - définir les sources de données et les lier à un collecteur de journaux

1. Accédez à la page de paramètres **Chargement automatique de journal**.

    1. Dans le portail Cloud App Security, cliquez sur l’icône des paramètres, puis sur **Collecteurs de journaux**.

    ![icône des paramètres](media/settings-icon.png)

1. Pour chaque pare-feu ou proxy à partir duquel vous souhaitez charger des journaux, créez une source de données correspondante.

    1. Cliquez sur **Ajouter une source de données**.  
    ![Add a data source](media/add-data-source.png)
    1. **Nommez** votre proxy ou pare-feu.  
    ![ubuntu1](media/ubuntu1.png)
    1. Sélectionnez l’appareil dans la liste **Source**. Si vous sélectionnez **Format de journal personnalisé** pour utiliser une appliance réseau qui n’est pas listée, consultez [Utilisation de l’analyseur de journal personnalisé](custom-log-parser.md) pour obtenir des instructions de configuration.
    1. Comparez votre journal à l’exemple de format de journal attendu. Si le format de votre fichier journal ne correspond pas à cet exemple, vous devez ajouter votre source de données en sélectionnant **Autre**.
    1. Définissez le **Type de récepteur** sur **FTP**, **FTPS**, **Syslog – UDP** ou **Syslog – TCP** ou **Syslog – TLS**.

    > [!NOTE]
    > L’intégration à des protocoles de transfert sécurisés (FTPS et Syslog – TLS) nécessite souvent un paramètre supplémentaire ou votre pare-feu/proxy.

    f. Répétez ce processus pour chaque pare-feu ou proxy dont les journaux peuvent être utilisés pour détecter le trafic sur votre réseau. Nous vous recommandons de configurer une source de données dédiée par appareil réseau pour vous permettre de :

    * Superviser l’état de chaque appareil séparément à des fins d’investigation
    * Explorer le Shadow IT Discovery par appareil, si chaque appareil est utilisé par un segment d’utilisateur différent

1. Accédez à l’onglet **Collecteurs de journaux** en haut.

    1. Cliquez sur **Ajouter un collecteur de journaux**.
    1. Donnez un **nom** au collecteur de journaux.
    1. Entrez l’**adresse IP de l’hôte** de la machine sur laquelle sera déployé le Docker. L’adresse IP de l’hôte peut être remplacée par le nom de l’ordinateur s’il existe un serveur DNS (ou un équivalent) qui résout le nom d’hôte.
    1. Select all **Data sources** that you want to connect to the collector, and click **Update** to save the configuration.

    ![ubuntu2](media/ubuntu2.png)

1. Des informations supplémentaires sur le déploiement s’affichent. **Copiez** la commande d’exécution à partir de la boîte de dialogue. Vous pouvez utiliser l’icône de copie dans le Presse-papiers. ![icône de copie dans le Presse-papiers](media/copy-icon.png)

1. **Exportez** la configuration de sources de données attendue. Cette configuration décrit comment définir l’exportation du journal dans vos appliances.

    ![Créer le collecteur de journaux](media/windows7.png)

    > [!NOTE]
    >
    > * Un seul collecteur de journaux peut gérer plusieurs sources de données.
    > * Copiez le contenu de l’écran, car vous aurez besoin des informations lors de la configuration du collecteur de journaux pour communiquer avec Cloud App Security. Si vous avez sélectionné Syslog, ces informations vont inclure des informations sur le port utilisé par l’écouteur Syslog pour écouter.
    > * For users sending log data via FTP for the first time, we recommend changing the password for the FTP user. For more information, see [Changing the FTP password](log-collector-ftp.md#changing-the-ftp-password).

### <a name="step-2--on-premises-deployment-of-your-machine"></a>Étape 2 : Déploiement local de votre ordinateur

La procédure suivante décrit le déploiement dans Ubuntu. Les étapes de déploiement pour d’autres plateformes sont légèrement différentes.

1. Ouvrez un terminal sur votre ordinateur Ubuntu.

1. Changez les privilèges racine à l’aide de la commande : `sudo -i`

1. Pour contourner un proxy dans votre réseau, exécutez les deux commandes suivantes :

    ```bash
    export http_proxy='<IP>:<PORT>' (e.g. 168.192.1.1:8888)
    export https_proxy='<IP>:<PORT>'
    ```

1. Si vous acceptez les [termes du contrat de licence logiciel](https://go.microsoft.com/fwlink/?linkid=862492), désinstallez les anciennes versions et installez Docker CE en exécutant la commande suivante :

    ```bash
    curl -o /tmp/MCASInstallDocker.sh https://adaprodconsole.blob.core.windows.net/public-files/MCASInstallDocker.sh && chmod +x /tmp/MCASInstallDocker.sh; /tmp/MCASInstallDocker.sh
    ```

    > [!NOTE]
    > Si cette commande ne parvient pas à valider votre certificat de proxy, exécutez la commande en ajoutant `curl -k` au début.

    ![ubuntu5](media/ubuntu5.png)

1. Déployez l’image du collecteur sur la machine hôte en important la configuration du collecteur. Importez la configuration en copiant la commande d’exécution générée dans le portail. Si vous devez configurer un proxy, ajoutez l’adresse IP et le numéro de port du proxy. Par exemple, si les détails de votre proxy sont 192.168.10.1:8080, votre commande d’exécution mise à jour est :

    ```bash
    (echo 6f19225ea69cf5f178139551986d3d797c92a5a43bef46469fcc997aec2ccc6f) | docker run --name MyLogCollector -p 21:21 -p 20000-20099:20000-20099 -e "PUBLICIP='192.2.2.2'" -e "PROXY=192.168.10.1:8080" -e "CONSOLE=tenant2.eu1-rs.adallom.com" -e "COLLECTOR=MyLogCollector" --security-opt apparmor:unconfined --cap-add=SYS_ADMIN --restart unless-stopped -a stdin -i microsoft/caslogcollector starter
    ```

    ![Créer le collecteur de journaux](media/windows7.png)

1. Vérifiez que le collecteur s’exécute correctement à l’aide de la commande suivante : `docker logs <collector_name>`

You should see the message: **Finished successfully!** 
![ubuntu8](media/ubuntu8.png)

### <a name="step-3---on-premises-configuration-of-your-network-appliances"></a>Étape 3 : Configuration locale de vos appliances réseau

Configurez vos pare-feu et proxys réseau pour exporter régulièrement les journaux vers le port Syslog dédié du répertoire FTP conformément aux instructions données dans la boîte de dialogue. Exemple :

```bash
BlueCoat_HQ - Destination path: \<<machine_name>>\BlueCoat_HQ\
```

### <a name="step-4---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>Étape 4 : Vérifier la réussite du déploiement dans le portail Cloud App Security

Consultez l’état du collecteur dans le tableau **Collecteur de journaux** et vérifiez que l’état est **Connecté**. Si l’état est **Créé**, il est possible que la connexion du collecteur de journaux et l’analyse n’aient pas été effectuées.

![ubuntu9](media/ubuntu9.png)

Vous pouvez aussi accéder au **journal de gouvernance** et vérifier que les journaux sont régulièrement chargés sur le portail.

Si vous rencontrez des problèmes lors du déploiement, consultez [Dépannage de Cloud Discovery](troubleshooting-cloud-discovery.md).

### <a name="optional---create-custom-continuous-reports"></a>Facultatif : Créer des rapports continus personnalisés

Vérifiez que les journaux sont chargés sur Cloud App Security et que les rapports sont générés. Après vérification, créez des rapports personnalisés. Vous pouvez créer des rapports de découverte personnalisés basés sur les groupes d’utilisateurs Azure Active Directory. Par exemple, pour voir l’utilisation cloud de votre service marketing, importez le groupe marketing à l’aide de la fonctionnalité d’importation des groupes d’utilisateurs. Créez ensuite un rapport personnalisé pour ce groupe. Vous pouvez également personnaliser un rapport en fonction d’une balise d’adresse IP ou de plages d’adresses IP.

1. Dans le portail Cloud App Security, dans les Paramètres (icône d’engrenage), sélectionnez Paramètres Cloud Discovery, puis **Rapports continus**.
1. Cliquez sur le bouton **Créer un rapport** et renseignez les champs.
1. Sous **Filtres**, vous pouvez filtrer les données par source de données, par [groupe d’utilisateurs importé](user-groups.md) ou par [balises et plages d’adresses IP](ip-tags.md).

![Rapport continu personnalisé](media/custom-continuous-report.png)

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Log collector FTP configuration](log-collector-ftp.md)

[Les clients Premier peuvent également choisir Cloud App Security directement dans le portail Premier.](https://premier.microsoft.com/)
