---
title: Configurer le chargement automatique de journal à l’aide de Docker dans Azure
description: Cet article décrit la procédure de configuration du chargement automatique de journaux pour des rapports continus dans Cloud App Security à l’aide de Docker sur Ubuntu ou RHEL dans Azure.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 05/04/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 5b952a924b7b26e4d45ffb981698f660e53a0558
ms.sourcegitcommit: baa9cb55d9d82808602a58ee24eeba7d83e92742
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82739022"
---
# <a name="set-up-and-configuration-on-ubuntu-or-rhel-in-azure"></a>Installation et configuration sur Ubuntu ou RHEL dans Azure

*S’applique à : Microsoft Cloud App Security*

Vous pouvez configurer le chargement automatique de journaux pour des rapports continus dans Cloud App Security à l’aide de Docker sur Ubuntu ou Red Hat Enterprise Linux (RHEL) dans Azure. Cet article décrit comment configurer le chargement automatique des journaux.

## <a name="prerequisites"></a>Prérequis

* Système d’exploitation : Ubuntu 16,04 et 18,04, RHEL 7,2 ou version ultérieure, ou CentOS 7,2 ou version ultérieure

* Espace disque : 250 Go

* Processeur : 2

* RAM : 4 Go

* Configurez votre pare-feu, comme décrit dans [Configuration réseau requise](network-requirements.md#log-collector)

> [!NOTE]
> Si vous disposez d’un collecteur de journaux existant et que vous souhaitez le supprimer avant de le déployer à nouveau, ou si vous souhaitez simplement le supprimer, exécutez les commandes suivantes :
>
> ```console
> docker stop <collector_name>
> docker rm <collector_name>
> ```

## <a name="log-collector-performance"></a>Performances du collecteur de journaux

Le collecteur de journaux peut gérer correctement la capacité des journaux pouvant atteindre jusqu’à 50 Go par heure, comprenant jusqu’à 10 sources de données. Les principaux goulots d’étranglement dans le processus de collecte des journaux sont les suivants :

* Bande passante réseau - Votre bande passante réseau détermine la vitesse de chargement des journaux.

* Performances d’e/s de la machine virtuelle : détermine la vitesse à laquelle les journaux sont écrits sur le disque du collecteur de journaux. Le collecteur de journaux dispose d’un mécanisme de sécurité intégré qui surveille le débit auquel les journaux arrivent et le compare au débit de chargement. En cas de congestion, le collecteur de journaux commence à supprimer des fichiers journaux. Si votre configuration dépasse généralement 50 Go par heure, nous vous recommandons de fractionner le trafic entre plusieurs collecteurs de journaux.

> [!NOTE]
> Si vous avez besoin de plus de 10 sources de données, nous vous recommandons de fractionner les sources de données entre plusieurs collecteurs de journaux.

## <a name="set-up-and-configuration"></a>Installation et configuration  

### <a name="step-1--web-portal-configuration-define-data-sources-and-link-them-to-a-log-collector"></a>Étape 1 : configuration du portail web  - définir les sources de données et les lier à un collecteur de journaux

1. Accédez à la page de paramètres **Chargement automatique de journal**.

    1. Dans le portail Cloud App Security, cliquez sur l’icône des paramètres, puis sur **Collecteurs de journaux**.

    ![icône des paramètres](media/settings-icon.png)

1. Pour chaque pare-feu ou proxy à partir duquel vous souhaitez charger des journaux, créez une source de données correspondante.

    1. Cliquez sur **Ajouter une source de données**.  
    ![Ajouter une source de données](media/add-data-source.png)
    1. **Nommez** votre proxy ou pare-feu.  
      ![ubuntu1](media/ubuntu1.png)
    1. Sélectionnez l’appareil dans la liste **Source**. Si vous sélectionnez **Format de journal personnalisé** pour utiliser une appliance réseau qui n’est pas listée, consultez [Utilisation de l’analyseur de journal personnalisé](custom-log-parser.md) pour obtenir des instructions de configuration.
    1. Comparez votre journal à l’exemple de format de journal attendu. Si le format de votre fichier journal ne correspond pas à cet exemple, vous devez ajouter votre source de données en sélectionnant **Autre**.
    1. Définissez le **Type de récepteur** sur **FTP**, **FTPS**, **Syslog – UDP** ou **Syslog – TCP** ou **Syslog – TLS**.

    >[!NOTE]
    >L’intégration à des protocoles de transfert sécurisés (FTPS et Syslog – TLS) nécessite souvent un paramètre supplémentaire ou votre pare-feu/proxy.

    f. Répétez ce processus pour chaque pare-feu ou proxy dont les journaux peuvent être utilisés pour détecter le trafic sur votre réseau. Nous vous recommandons de configurer une source de données dédiée par appareil réseau pour vous permettre de :

    * Superviser l’état de chaque appareil séparément à des fins d’investigation
    * Explorer le Shadow IT Discovery par appareil, si chaque appareil est utilisé par un segment d’utilisateur différent

1. Accédez à l’onglet **Collecteurs de journaux** en haut.

    1. Cliquez sur **Ajouter un collecteur de journaux**.
    1. Donnez un **nom**au collecteur de journaux.
    1. Entrez l’**adresse IP de l’hôte** de la machine sur laquelle sera déployé le Docker. L’adresse IP de l’hôte peut être remplacée par le nom de l’ordinateur s’il existe un serveur DNS (ou un équivalent) qui résout le nom d’hôte.
    1. Sélectionnez toutes les **sources de données** que vous souhaitez connecter au collecteur, puis cliquez sur **mettre à jour** pour enregistrer la configuration.  
    ![ubuntu2](media/ubuntu2.png)

1. Des informations supplémentaires sur le déploiement s’affichent. **Copiez** la commande d’exécution à partir de la boîte de dialogue. Vous pouvez utiliser l’icône de copie dans le Presse-papiers. ![icône de copie dans le Presse-papiers](media/copy-icon.png)

1. **Exportez** la configuration de sources de données attendue. Cette configuration décrit comment définir l’exportation du journal dans vos appliances.

    ![Créer le collecteur de journaux](media/windows7.png)

    > [!NOTE]
    >
    > * Un seul collecteur de journaux peut gérer plusieurs sources de données.
    > * Copiez le contenu de l’écran, car vous aurez besoin des informations lors de la configuration du collecteur de journaux pour communiquer avec Cloud App Security. Si vous avez sélectionné Syslog, ces informations vont inclure des informations sur le port utilisé par l’écouteur Syslog pour écouter.
    > * Pour les utilisateurs qui envoient des données de journal via FTP pour la première fois, nous vous recommandons de modifier le mot de passe de l’utilisateur FTP. Pour plus d’informations, consultez [modification du mot de passe FTP](log-collector-ftp.md#changing-the-ftp-password).

### <a name="step-2--deployment-of-your-machine-in-azure"></a>Étape 2 : déploiement de la machine dans Azure

> [!NOTE]
> La procédure suivante décrit le déploiement dans Ubuntu. Les étapes de déploiement pour d’autres plateformes sont légèrement différentes.

1. Créez une nouvelle machine Ubuntu dans votre environnement Azure.
1. Une fois la machine configurée, ouvrez les ports ainsi :

    1. Dans l’affichage Ordinateur, accédez à **Réseau** et sélectionnez l’interface souhaitée en double-cliquant dessus.
    1. Accédez à **Groupe de sécurité réseau** et sélectionnez le groupe de sécurité réseau qui convient.
    1. Accédez à **règles de sécurité de trafic entrant** , puis ![cliquez sur **Ajouter**, Ubuntu Azure](media/ubuntu-azure.png)
    1. Ajoutez les règles suivantes (en mode **Avancé**) :

    |Nom|Plages de ports de destination|Protocol|Source|Destination|
    |----|----|----|----|----|
    |caslogcollector_ftp|21|TCP|<Sous-réseau d’adresse IP de votre appliance>|Quelconque|
    |caslogcollector_ftp_passive|20000-20099|TCP|<Sous-réseau d’adresse IP de votre appliance>|Quelconque|
    |caslogcollector_syslogs_tcp|601-700|TCP|<Sous-réseau d’adresse IP de votre appliance>|Quelconque|
    |caslogcollector_syslogs_udp|514-600|UDP|<Sous-réseau d’adresse IP de votre appliance>|Quelconque|

    ![Règles Ubuntu Azure](media/inbound-rule.png)

1. Revenez à l’ordinateur et cliquez sur **Se connecter** pour ouvrir un terminal dessus.

1. Appliquez les privilèges racines avec `sudo -i`.

1. Si vous acceptez les [termes du contrat de licence logiciel](https://go.microsoft.com/fwlink/?linkid=862492), désinstallez les anciennes versions et installez Docker CE en exécutant la commande suivante :

    ```bash
    curl -o /tmp/MCASInstallDocker.sh https://adaprodconsole.blob.core.windows.net/public-files/MCASInstallDocker.sh && chmod +x /tmp/MCASInstallDocker.sh; /tmp/MCASInstallDocker.sh
    ```

    ![Commande Ubuntu Azure](media/ubuntu-azure-command.png)

1. Dans la fenêtre **Créer un collecteur de journaux** du portail Cloud App Security, copiez la commande pour importer la configuration du collecteur sur la machine hôte :

    ![Ubuntu Azure](media/windows7.png)

1. Exécutez la commande pour déployer le collecteur de journaux.

    ```bash
    (echo db3a7c73eb7e91a0db53566c50bab7ed3a755607d90bb348c875825a7d1b2fce) | docker run --name MyLogCollector -p 21:21 -p 20000-20099:20000-20099 -e "PUBLICIP='192.168.1.1'" -e "PROXY=192.168.10.1:8080" -e "CONSOLE=mod244533.us.portal.cloudappsecurity.com" -e "COLLECTOR=MyLogCollector" --security-opt apparmor:unconfined --cap-add=SYS_ADMIN --restart unless-stopped -a stdin -i microsoft/caslogcollector starter
    ```

    ![Proxy Ubuntu](media/ubuntu-proxy.png)

1. Pour vérifier que le collecteur s’exécute correctement, exécutez la commande suivante : `Docker logs <collector_name>`. Vous devriez obtenir les résultats : **Terminé avec succès !**

    ![ubuntu8](media/ubuntu8.png)

### <a name="step-3---on-premises-configuration-of-your-network-appliances"></a>Étape 3 : Configuration locale de vos appliances réseau

Configurez vos pare-feu et proxys réseau pour exporter régulièrement les journaux vers le port Syslog dédié du répertoire FTP conformément aux instructions données dans la boîte de dialogue. Par exemple :

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
> [Configuration FTP du collecteur de journaux](log-collector-ftp.md)

[!INCLUDE [Open support ticket](includes/support.md)]
