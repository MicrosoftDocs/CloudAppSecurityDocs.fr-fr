---
title: Configurer le chargement automatique de journal à l’aide de Docker dans Azure
description: Cet article décrit le processus de configuration du chargement automatique des journaux pour les rapports continus dans Cloud App Security à l’aide d’un docker sur Linux dans Azure.
ms.date: 12/02/2020
ms.topic: how-to
ms.openlocfilehash: 6c4f7243758dce46e5469d503ec572a18a7a2afe
ms.sourcegitcommit: 53e485ed8460f1123b3b55277fa5991b427b5302
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96512948"
---
# <a name="docker-on-linux-in-azure"></a>Docker sur Linux dans Azure

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Vous pouvez configurer le chargement automatique des journaux pour des rapports continus dans Cloud App Security à l’aide d’un docker sur Ubuntu, Red Hat Enterprise Linux (RHEL) ou CentOS dans Azure.

## <a name="prerequisites"></a>Prérequis

* Système d’exploitation :
    * Ubuntu 14,04, 16,04 et 18,04
    * RHEL 7,2 ou version ultérieure
    * CentOS 7,2 ou version ultérieure

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

    ![Icône des paramètres](media/settings-icon.png)

1. Pour chaque pare-feu ou proxy à partir duquel vous souhaitez charger des journaux, créez une source de données correspondante.

    1. Cliquez sur **Ajouter une source de données**.  
    ![Ajouter une source de données](media/add-data-source.png)
    1. **Nommez** votre proxy ou pare-feu.  
      ![Nom du proxy ou du pare-feu](media/ubuntu1.png)
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
    1. Donnez un **nom** au collecteur de journaux.
    1. Entrez l’**adresse IP de l’hôte** de la machine sur laquelle sera déployé le Docker. L’adresse IP de l’hôte peut être remplacée par le nom de l’ordinateur s’il existe un serveur DNS (ou un équivalent) qui résout le nom d’hôte.
    1. Sélectionnez toutes les **sources de données** que vous souhaitez connecter au collecteur, puis cliquez sur **mettre à jour** pour enregistrer la configuration.  
    ![Sélectionner des sources de données](media/ubuntu2.png)

1. Des informations supplémentaires sur le déploiement s’affichent. **Copiez** la commande d’exécution à partir de la boîte de dialogue. Vous pouvez utiliser l’icône de copie dans le Presse-papiers. ![icône de copie dans le Presse-papiers](media/copy-icon.png)

1. **Exportez** la configuration de sources de données attendue. Cette configuration décrit comment définir l’exportation du journal dans vos appliances.

    ![Créer le collecteur de journaux](media/windows7.png)

    > [!NOTE]
    >
    > * Un seul collecteur de journaux peut gérer plusieurs sources de données.
    > * Copiez le contenu de l’écran, car vous aurez besoin des informations lors de la configuration du collecteur de journaux pour communiquer avec Cloud App Security. Si vous avez sélectionné Syslog, ces informations vont inclure des informations sur le port utilisé par l’écouteur Syslog pour écouter.
    > * Pour les utilisateurs qui envoient des données de journal via FTP pour la première fois, nous vous recommandons de modifier le mot de passe de l’utilisateur FTP. Pour plus d’informations, consultez [modification du mot de passe FTP](log-collector-advanced-management.md#changing-the-ftp-password).

### <a name="step-2--deployment-of-your-machine-in-azure"></a>Étape 2 : déploiement de la machine dans Azure

> [!NOTE]
> La procédure suivante décrit le déploiement dans Ubuntu. Les étapes de déploiement pour d’autres plateformes sont légèrement différentes.

1. Créez une nouvelle machine Ubuntu dans votre environnement Azure.
1. Une fois la machine configurée, ouvrez les ports ainsi :

    1. Dans l’affichage Ordinateur, accédez à **Réseau** et sélectionnez l’interface souhaitée en double-cliquant dessus.
    1. Accédez à **Groupe de sécurité réseau** et sélectionnez le groupe de sécurité réseau qui convient.
    1. Accédez à **règles de sécurité de trafic entrant** , puis cliquez sur **Ajouter**, ![ Ajouter des règles de sécurité de trafic entrant.](media/ubuntu-azure.png)
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

1. Si vous acceptez les termes du contrat de [licence logicielle](https://go.microsoft.com/fwlink/?linkid=862492), désinstallez les anciennes versions et installez dockr ce en exécutant les commandes appropriées pour votre environnement :

#### <a name="centos"></a>[CentOS](#tab/centos)

1. Supprimer les anciennes versions de l’arrimeur : `yum erase docker docker-engine docker.io`
1. Installez les composants requis du moteur de l’ancrage : `yum install -y yum-utils`
1. Ajouter un référentiel d’ancrage :

    ```bash
    yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
    yum makecache
    ```

1. Installer le moteur de l’amarrage : `yum -y install docker-ce`
1. Démarrer l’ancrage

    ```bash
    systemctl start docker
    systemctl enable docker
    ```

1. Installation de l’amarrage de test : `docker run hello-world`

#### <a name="red-hat"></a>[Red Hat](#tab/red-hat)

1. Supprimer les anciennes versions de l’arrimeur : `yum erase docker docker-engine docker.io`
1. Installez les composants requis du moteur de l’ancrage :

    ```bash
    yum install -y yum-utils
    yum install -y https://download.docker.com/linux/centos/7/x86_64/stable/Packages/containerd.io-1.3.7-3.1.el7.x86_64.rpm
    ```

1. Ajouter un référentiel d’ancrage :

    ```bash
    yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
    yum makecache
    ```

1. Installer le moteur de l’amarrage : `yum -y install docker-ce`
1. Démarrer l’ancrage

    ```bash
    systemctl start docker
    systemctl enable docker
    ```

1. Installation de l’amarrage de test : `docker run hello-world`

#### <a name="ubuntu"></a>[Ubuntu](#tab/ubuntu)

1. Supprimer les anciennes versions de l’arrimeur : `apt-get remove docker docker-engine docker.io`
1. Si vous installez sur Ubuntu 14,04, installez le package linux-image-extra.

    ```bash
    apt-get update -y
    apt-get install -y linux-image-extra-$(uname -r) linux-image-extra-virtual
    ```

1. Installez les composants requis du moteur de l’ancrage :

    ```bash
    apt-get update -y
    (apt-get install -y apt-transport-https ca-certificates curl software-properties-common && curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add - )
    ```

1. Vérifier que l’UID de l’empreinte digitale de clé apt est docker@docker.com:`apt-key fingerprint | grep uid`
1. Installer le moteur de l’amarrage :

    ```bash
    add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
    apt-get update -y
    apt-get install -y docker-ce
    ```

1. Installation de l’amarrage de test : `docker run hello-world`

---

1. Dans la fenêtre **Créer un collecteur de journaux** du portail Cloud App Security, copiez la commande pour importer la configuration du collecteur sur la machine hôte :

    ![Commande de copie pour importer la configuration du collecteur sur l’ordinateur hôte](media/windows7.png)

1. Exécutez la commande pour déployer le collecteur de journaux.

    ```bash
    (echo db3a7c73eb7e91a0db53566c50bab7ed3a755607d90bb348c875825a7d1b2fce) | docker run --name MyLogCollector -p 21:21 -p 20000-20099:20000-20099 -e "PUBLICIP='192.168.1.1'" -e "PROXY=192.168.10.1:8080" -e "CONSOLE=mod244533.us.portal.cloudappsecurity.com" -e "COLLECTOR=MyLogCollector" --security-opt apparmor:unconfined --cap-add=SYS_ADMIN --restart unless-stopped -a stdin -i mcr.microsoft.com/mcas/logcollector starter
    ```

    ![Proxy Ubuntu](media/ubuntu-proxy.png)

1. Pour vérifier que le collecteur s’exécute correctement, exécutez la commande suivante : `Docker logs <collector_name>`. Vous devriez obtenir les résultats : **Terminé avec succès !**

    ![Commande pour vérifier que le collecteur de journaux s’exécute correctement](media/ubuntu8.png)

### <a name="step-3---on-premises-configuration-of-your-network-appliances"></a>Étape 3 : Configuration locale de vos appliances réseau

Configurez vos pare-feu et proxys réseau pour exporter régulièrement les journaux vers le port Syslog dédié du répertoire FTP conformément aux instructions données dans la boîte de dialogue. Par exemple :

```bash
BlueCoat_HQ - Destination path: \<<machine_name>>\BlueCoat_HQ\
```

### <a name="step-4---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>Étape 4 : Vérifier la réussite du déploiement dans le portail Cloud App Security

Consultez l’état du collecteur dans le tableau **Collecteur de journaux** et vérifiez que l’état est **Connecté**. Si l’état est **Créé**, il est possible que la connexion du collecteur de journaux et l’analyse n’aient pas été effectuées.

![Vérifier l’état du collecteur dans le collecteur de journaux](media/ubuntu9.png)

Vous pouvez aussi accéder au **journal de gouvernance** et vérifier que les journaux sont régulièrement chargés sur le portail.

Vous pouvez également vérifier l’état du collecteur de journaux à partir du conteneur de l’ancrage à l’aide des commandes suivantes :

1. Connectez-vous au conteneur à l’aide de la commande suivante : `docker exec -it <Container Name> bash`
1. Vérifiez l’état du collecteur de journaux à l’aide de cette commande : `collector_status -p`

Si vous rencontrez des problèmes lors du déploiement, consultez [Dépannage de Cloud Discovery](troubleshooting-cloud-discovery.md).

### <a name="optional---create-custom-continuous-reports"></a>Facultatif : Créer des rapports continus personnalisés

Vérifiez que les journaux sont chargés sur Cloud App Security et que les rapports sont générés. Après vérification, créez des rapports personnalisés. Vous pouvez créer des rapports de découverte personnalisés basés sur les groupes d’utilisateurs Azure Active Directory. Par exemple, pour voir l’utilisation cloud de votre service marketing, importez le groupe marketing à l’aide de la fonctionnalité d’importation des groupes d’utilisateurs. Créez ensuite un rapport personnalisé pour ce groupe. Vous pouvez également personnaliser un rapport en fonction d’une balise d’adresse IP ou de plages d’adresses IP.

1. Dans le portail Cloud App Security, dans les Paramètres (icône d’engrenage), sélectionnez Paramètres Cloud Discovery, puis **Rapports continus**. 
1. Cliquez sur le bouton **Créer un rapport** et renseignez les champs.
1. Sous **Filtres**, vous pouvez filtrer les données par source de données, par [groupe d’utilisateurs importé](user-groups.md) ou par [balises et plages d’adresses IP](ip-tags.md). 

     ![Rapport continu personnalisé](media/custom-continuous-report.png)

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Modifier la configuration FTP du collecteur de journaux](log-collector-advanced-management.md)

[!INCLUDE [Open support ticket](includes/support.md)]
