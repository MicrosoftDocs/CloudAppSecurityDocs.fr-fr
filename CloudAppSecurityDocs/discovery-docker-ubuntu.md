---
title: Configurer le chargement automatique des journaux pour des rapports continus | Documentation Microsoft
description: "Cette rubrique aborde le processus de configuration du chargement automatique des journaux pour une création continue de rapports dans Cloud App Security à l’aide de Docker sur un système Ubuntu."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/16/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: cc29a6cb-1c03-4148-8afd-3ad47003a1e3
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: e32eebc75355e8016fcdb62a1b113431db346c31
ms.sourcegitcommit: ae4c8226f6037c5eb286eb27142d6bbb397609e9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2017
---
# <a name="set-up-and-configuration-on-ubuntu"></a>Installation et configuration sur Ubuntu

## <a name="technical-requirements"></a>Spécifications techniques

-   Système d’exploitation : Ubuntu 14.04 ou version ultérieure

-   Espace disque : 250 Go

-   Processeur : 2

-   RAM : 4 Go

-   Paramètres du pare-feu :

    -   Autoriser le collecteur de journaux à recevoir le trafic FTP et Syslog entrant

    -   Autoriser le collecteur de journaux à lancer le trafic sortant sur le portail (par exemple, contoso.cloudappsecurity.com) sur le port 443

## <a name="log-collector-performance"></a>Performances du collecteur de journaux

Le collecteur de journaux peut gérer correctement une capacité allant jusqu’à 50 Go par heure. Les principaux goulots d’étranglement dans le processus de collecte des journaux sont les suivants :

-   Bande passante réseau : votre bande passante réseau détermine la vitesse de chargement des journaux.

-   Performances d’E/S de la machine virtuelle allouées par votre service informatique : détermine la vitesse à laquelle les journaux sont écrits sur le disque du collecteur de journaux. Le collecteur de journaux dispose d’un mécanisme de sécurité intégré qui surveille le débit auquel les journaux arrivent et le compare au débit de chargement. En cas de congestion, le collecteur de journaux commence à supprimer des fichiers journaux. Si votre configuration dépasse généralement 50 Go par heure, il est recommandé de répartir le trafic entre plusieurs collecteurs de journaux.

## <a name="step-1--web-portal-configuration-define-data-sources-and-link-them-to-a-log-collector"></a>Étape 1 : configuration du portail web  - définir les sources de données et les lier à un collecteur de journaux

1.  Accédez à la page des paramètres de chargement automatisé :  <br></br>Dans le portail Cloud App Security, cliquez sur l’icône des paramètres ![icône des paramètres](./media/settings-icon.png), puis sur **Collecteurs de journaux**.

2.  Pour chaque pare-feu ou proxy à partir desquels vous voulez charger des journaux, créez une source de données correspondante :

    ![ubuntu1](./media/ubuntu1.png)

    a. Cliquez sur **Ajouter une source de données**.

    b. **Nommez** votre proxy ou pare-feu.

    c. Sélectionnez l’appareil dans la liste **Source**.

    d. Comparez votre journal à l’exemple de format de journal attendu. Si votre format de fichier journal ne correspond pas à cet exemple, vous devez ajouter votre source de données en tant qu’**Autre**.

    e. Définissez le **Type de récepteur** sur **FTP**, **FTPS**, **Syslog – UDP**, **Syslog – TCP** ou **Syslog – TLS**.
    >[!NOTE]
    >L’intégration aux protocoles de transfert sécurisé (FTPS et Syslog – TLS) nécessite souvent que des paramètres supplémentaires soient configurés dans votre pare-feu/proxy.

    f. Répétez ce processus pour chaque pare-feu ou proxy dont les journaux peuvent être utilisés pour détecter le trafic sur votre réseau.

3.  Accédez à l’onglet **Collecteurs de journaux** en haut.

    a. Cliquez sur **Ajouter un collecteur de journaux**.

    b. Donnez un **nom** au collecteur de journaux.

    c. Entrez l’**Adresse IP de l’hôte** de la machine que vous allez utiliser pour déployer Docker.

    d. Sélectionnez toutes les **sources de données** que vous voulez connecter au collecteur, puis cliquez sur **Mettre à jour** pour enregistrer la configuration et afficher les étapes de déploiement suivantes.

    ![ubuntu2](./media/ubuntu2.png)

    >  [!NOTE]
    > - Un seul collecteur de journaux peut gérer plusieurs sources de données.
    >- Copiez le contenu de l’écran, car vous aurez besoin des informations lors de la configuration du collecteur de journaux pour communiquer avec Cloud App Security. Si vous avez sélectionné Syslog, ces informations vont inclure des informations sur le port utilisé par l’écouteur Syslog pour écouter.

4.  Des informations supplémentaires sur le déploiement vont s’afficher.

 ![ubuntu3](./media/ubuntu3.png)

5.  **Copiez** la commande Exécuter à partir de la boîte de dialogue. Vous pouvez également utiliser l’icône ![Copier dans le Presse-papiers](./media/copy-icon.png).

6.  **Exportez** la configuration de source de données attendue. Cette configuration décrit la façon dont vous devez configurer l’exportation de journaux dans vos appliances.

  ![ubuntu4](./media/ubuntu4.png)

## <a name="step-2--on-premises-deployment-of-your-machine"></a>Étape 2 : Déploiement local de votre machine

> [!Note]
> La procédure suivante décrit le déploiement dans Ubuntu. La procédure de déploiement pour les autres plateformes est légèrement différente.

1.  Ouvrez un terminal sur votre machine Ubuntu.

2.  Utilisez les privilèges racine à l’aide de la commande suivante : `Sudo - i`

3.  Désinstallez les anciennes versions, puis installez Docker CE en exécutant la commande suivante :

    `curl -o /tmp/MCASInstallDocker.sh
    https://adaprodconsole.blob.core.windows.net/public-files/MCASInstallDocker.sh
    && chmod +x /tmp/MCASInstallDocker.sh; sudo /tmp/MCASInstallDocker.sh`

    ![ubuntu5](./media/ubuntu5.png)

4.  Déployez l’image du collecteur à l’aide de la commande Exécuter générée dans le portail.

    ![ubuntu6](./media/ubuntu6.png)

    >[!NOTE]
    >Si vous avez besoin de configurer un proxy, ajoutez l’adresse IP et le port du proxy sous celui-ci. Par exemple, si les détails de votre proxy sont 192.168.10.1:8080, votre commande Exécuter ressemblera à ceci :<br></br>
     `Sudo docker run --name casCollector -p 21:21 -p 20000-20099:20000-20099 -e
    "PUBLICIP='192.168.1.1'" -e "PROXY=192.168.10.1:8080" -e
    "TOKEN=41f8f442c9a30519a058dd3bb9a19c79eb67f34a8816270dc4a384493988863a" -e
    "CONSOLE=tenant2.eu1-rs.adallom.com" -e "COLLECTOR=casCollector" --security-opt
    apparmor:unconfined --cap-add=SYS_ADMIN -dt microsoft/caslogcollector starter`

    ![ubuntu7](./media/ubuntu7.png)

5.  Pour vérifier que le collecteur s’exécute correctement, exécutez la commande suivante : `Docker logs \<collector_name\>`

Vous devriez voir le message suivant : **Terminé avec succès**

  ![ubuntu8](./media/ubuntu8.png)

## <a name="step-4---on-premises-configuration-of-your-network-appliances"></a>Étape 4 : configuration locale de vos équipements de réseau

Configurez vos pare-feu réseau et proxys pour exporter régulièrement les journaux vers le port Syslog dédié du répertoire FTP selon les instructions données dans la boîte de dialogue, par exemple :

    BlueCoat_HQ - Destination path: \<<machine_name>>\BlueCoat_HQ\

## <a name="step-5---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>Étape 5 : vérifier la réussite du déploiement dans le portail Cloud App Security

Consultez l’état du collecteur dans le tableau **Collecteur de journaux** et vérifiez que l’état est **Connecté**. Si l’état est **Créé**, il est possible que la connexion du collecteur de journaux et l’analyse ne soient pas effectuées.

 ![ubuntu9](./media/ubuntu9.png)

Vous pouvez également accéder au **Journal de gouvernance** et vérifier que les journaux sont régulièrement chargés sur le portail.

Si vous rencontrez des problèmes lors du déploiement, consultez [Dépannage de Cloud Discovery](troubleshooting-cloud-discovery.md).

## <a name="see-also"></a>Voir aussi
[Utilisation des données Cloud Discovery](working-with-cloud-discovery-data.md)  
[Pour obtenir de l’aide technique, visitez la page de support assisté Cloud App Security](http://support.microsoft.com/oas/default.aspx?prid=16031)  
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier](https://premier.microsoft.com/)

