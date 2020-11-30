---
title: Déployer des rapports continus pour des Cloud App Security à l’aide d’un ancrage sur Windows
description: Cet article décrit la procédure de configuration du chargement automatique des journaux pour des rapports continus dans Cloud App Security à l’aide d’un Docker sur Windows dans une serveur local.
ms.date: 11/19/2019
ms.topic: how-to
ms.openlocfilehash: 3fe411948dd2f0fe64917d69047351d835744ac0
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96311806"
---
# <a name="docker-on-windows-on-premises"></a>Docker sur Windows en local

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Vous pouvez configurer le chargement automatique des journaux pour des rapports continus dans Cloud App Security à l’aide d’un Docker sur Windows.

## <a name="prerequisites"></a>Prérequis

* Système d’exploitation :
  * **Windows 10** (mise à jour des créateurs de automne)
  * Windows Server **version 1709 +** (sac)
  * **Windows Server 2019 (LTSC)**

* Espace disque : 250 Go

* Processeur : 2

* RAM : 4 Go

* Configurez votre pare-feu, comme décrit dans [Configuration réseau requise](network-requirements.md#log-collector)

* La virtualisation du système d’exploitation doit être activée avec Hyper-V

> [!IMPORTANT]
>
> * Un utilisateur doit être connecté pour que l’arrimeur collecte les journaux. Nous vous recommandons de recommander aux utilisateurs de votre conseiller de se déconnecter sans fermer la session.
> * Docker pour Windows n’est pas officiellement pris en charge dans les scénarios de virtualisation VMWare.
> * Docker pour Windows n’est pas officiellement pris en charge dans les scénarios de virtualisation imbriquée. Si vous envisagez toujours d’utiliser la virtualisation imbriquée, reportez-vous au [Guide officiel de l’ancrage](https://docs.docker.com/docker-for-windows/troubleshoot/#running-docker-desktop-in-nested-virtualization-scenarios).

> [!NOTE]
> Si vous disposez d’un collecteur de journaux existant et que vous souhaitez le supprimer avant de le déployer à nouveau, ou si vous souhaitez simplement le supprimer, exécutez les commandes suivantes :
>
> ```console
> docker stop <collector_name>
> docker rm <collector_name>
> ```

## <a name="log-collector-performance"></a>Performances du collecteur de journaux

Le collecteur de journaux peut gérer correctement une capacité allant jusqu’à 50 Go par heure. Les principaux goulots d’étranglement dans le processus de collecte des journaux sont les suivants :

* Bande passante réseau - Votre bande passante réseau détermine la vitesse de chargement des journaux.

* Performances d’e/s de la machine virtuelle : détermine la vitesse à laquelle les journaux sont écrits sur le disque du collecteur de journaux. Le collecteur de journaux dispose d’un mécanisme de sécurité intégré qui surveille le débit auquel les journaux arrivent et le compare au débit de chargement. En cas de congestion, le collecteur de journaux commence à supprimer des fichiers journaux. Si votre configuration dépasse généralement 50 Go par heure, nous vous recommandons de diviser le trafic entre plusieurs collecteurs de journaux.

## <a name="set-up-and-configuration"></a>Installation et configuration

### <a name="step-1--web-portal-configuration-define-data-sources-and-link-them-to-a-log-collector"></a>Étape 1 : configuration du portail web  - définir les sources de données et les lier à un collecteur de journaux

1. Accédez à la page de paramètres **Chargement automatique de journal**.

    1. Dans le portail Cloud App Security, cliquez sur l’icône des paramètres, puis sur **Collecteurs de journaux**.

    ![Icône des paramètres](media/settings-icon.png)

1. Pour chaque pare-feu ou proxy à partir duquel vous souhaitez charger des journaux, créez une source de données correspondante.

    1. Cliquez sur **Ajouter une source de données**.  
    ![Ajouter une source de données](media/add-data-source.png)
    1. **Nommez** votre proxy ou pare-feu.  
    ![Ajouter un nom pour la source de données](media/ubuntu1.png)
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
    1. Sélectionnez toutes les **sources de données** que vous souhaitez connecter au collecteur, puis cliquez sur **mettre à jour** pour enregistrer la configuration.
    ![Sélectionner la source de données à connecter](media/ubuntu2.png)

1. Des informations supplémentaires sur le déploiement s’affichent. **Copiez** la commande d’exécution à partir de la boîte de dialogue. Vous pouvez utiliser l’icône copier dans le presse-papiers, ![ copier dans le presse-papiers ](media/copy-icon.png) . Vous en aurez besoin ultérieurement.

1. **Exportez** la configuration de sources de données attendue. Cette configuration décrit comment définir l’exportation du journal dans vos appliances.

    ![Créer le collecteur de journaux](media/windows7.png)

    > [!NOTE]
    >
    > * Un seul collecteur de journaux peut gérer plusieurs sources de données.
    > * Copiez le contenu de l’écran, car vous aurez besoin des informations lors de la configuration du collecteur de journaux pour communiquer avec Cloud App Security. Si vous avez sélectionné Syslog, ces informations vont inclure des informations sur le port utilisé par l’écouteur Syslog pour écouter.
    > * Pour les utilisateurs qui envoient des données de journal via FTP pour la première fois, nous vous recommandons de modifier le mot de passe de l’utilisateur FTP. Pour plus d’informations, consultez [modification du mot de passe FTP](log-collector-advanced-management.md#changing-the-ftp-password).

### <a name="step-2--on-premises-deployment-of-your-machine"></a>Étape 2 : Déploiement local de votre ordinateur

La procédure suivante décrit le déploiement dans Windows. Les étapes de déploiement pour d’autres plateformes sont légèrement différentes.

1. Ouvrez un terminal PowerShell en tant qu’administrateur sur votre ordinateur Windows.

1. Exécutez la commande suivante pour télécharger le fichier de script PowerShell du programme d’installation de Windows Dockr : `Invoke-WebRequest https://adaprodconsole.blob.core.windows.net/public-files/LogCollectorInstaller.ps1 -OutFile (Join-Path $Env:Temp LogCollectorInstaller.ps1)`

    Pour vérifier que le programme d’installation est signé par Microsoft, consultez [valider la signature du programme d’installation](#validate-signature)

1. Pour activer l’exécution du script PowerShell, exécutez `Set-ExecutionPolicy RemoteSigned`

1. Exécuter : `& (Join-Path $Env:Temp LogCollectorInstaller.ps1)` installe le client docker sur votre ordinateur. L’installation du conteneur de collecteur de journaux redémarre deux fois l’ordinateur et vous oblige à vous reconnecter. **Assurez-vous que le client Dockr est configuré pour utiliser des conteneurs Linux.**

1. Après chaque redémarrage, ouvrez un terminal PowerShell en tant qu’administrateur sur votre ordinateur, puis réexécutez : `& (Join-Path $Env:Temp LogCollectorInstaller.ps1)`

1. Avant la fin de l’installation, vous devez coller la commande d’exécution copiée précédemment.

1. Déployez l’image du collecteur sur la machine hôte en important la configuration du collecteur. Importez la configuration en copiant la commande d’exécution générée dans le portail. Si vous devez configurer un proxy, ajoutez l’adresse IP et le numéro de port du proxy. Par exemple, si les détails de votre proxy sont 192.168.10.1:8080, votre commande d’exécution mise à jour est :

    ```console
    (echo db3a7c73eb7e91a0db53566c50bab7ed3a755607d90bb348c875825a7d1b2fce) | docker run --name MyLogCollector -p 21:21 -p 20000-20099:20000-20099 -e "PUBLICIP='192.168.1.1'" -e "PROXY=192.168.10.1:8080" -e "CONSOLE=mod244533.us.portal.cloudappsecurity.com" -e "COLLECTOR=MyLogCollector" --security-opt apparmor:unconfined --cap-add=SYS_ADMIN --restart unless-stopped -a stdin -i mcr.microsoft.com/mcas/logcollector starter
    ```

    ![Créer le collecteur de journaux](media/windows7.png)

1. Vérifiez que le collecteur s’exécute correctement à l’aide de la commande suivante : `docker logs <collector_name>`

Le message suivant doit s’afficher : **terminé !**

![Vérifier que le collecteur s’exécute correctement](media/ubuntu8.png)

### <a name="step-3---on-premises-configuration-of-your-network-appliances"></a>Étape 3 : Configuration locale de vos appliances réseau

Configurez vos pare-feu et proxys réseau pour exporter régulièrement les journaux vers le port Syslog dédié du répertoire FTP conformément aux instructions données dans la boîte de dialogue. Par exemple :

```console
BlueCoat_HQ - Destination path: \<<machine_name>>\BlueCoat_HQ\
```

### <a name="step-4---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>Étape 4 : Vérifier la réussite du déploiement dans le portail Cloud App Security

Consultez l’état du collecteur dans le tableau **Collecteur de journaux** et vérifiez que l’état est **Connecté**. Si l’état est **Créé**, il est possible que la connexion du collecteur de journaux et l’analyse n’aient pas été effectuées.

![Vérifier que le collecteur a été correctement déployé](media/ubuntu9.png)

Vous pouvez aussi accéder au **journal de gouvernance** et vérifier que les journaux sont régulièrement chargés sur le portail.

Si vous rencontrez des problèmes lors du déploiement, consultez [Dépannage de Cloud Discovery](troubleshooting-cloud-discovery.md).

### <a name="optional---create-custom-continuous-reports"></a>Facultatif : créer des rapports continus personnalisés <a name="continuous-reports"></a>

Vérifiez que les journaux sont chargés sur Cloud App Security et que les rapports sont générés. Après vérification, créez des rapports personnalisés. Vous pouvez créer des rapports de découverte personnalisés basés sur les groupes d’utilisateurs Azure Active Directory. Par exemple, pour voir l’utilisation cloud de votre service marketing, importez le groupe marketing à l’aide de la fonctionnalité d’importation des groupes d’utilisateurs. Créez ensuite un rapport personnalisé pour ce groupe. Vous pouvez également personnaliser un rapport en fonction d’une balise d’adresse IP ou de plages d’adresses IP.

1. Dans le portail Cloud App Security, dans les Paramètres (icône d’engrenage), sélectionnez Paramètres Cloud Discovery, puis **Rapports continus**.
1. Cliquez sur le bouton **Créer un rapport** et renseignez les champs.
1. Sous **Filtres**, vous pouvez filtrer les données par source de données, par [groupe d’utilisateurs importé](user-groups.md) ou par [balises et plages d’adresses IP](ip-tags.md).

    ![Rapport continu personnalisé](media/custom-continuous-report.png)

### <a name="optional---validate-installer-signature"></a>Facultatif : Valider la signature du programme d’installation <a name="validate-signature"></a>

Pour vérifier que le programme d’installation de Docker est signé par Microsoft :

1. Cliquez avec le bouton droit sur le fichier et sélectionnez **Propriétés**.
1. Cliquez sur **Signatures numériques** et vérifiez la présence du message **Cette signature numérique est valide**.
1. Vérifiez que l’option **Microsoft Corporation** figure en tant qu’entrée unique sous **Nom du signataire**.

    ![Signature numérique valide](media/digital-signature-successful.png)

Si la signature numérique n’est pas valide, vous recevez le message **Cette signature numérique n’est pas valide** :

![La signature numérique n’est pas valide](media/digital-signature-unsuccessful.png)

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Modifier la configuration FTP du collecteur de journaux](log-collector-advanced-management.md)

[!INCLUDE [Open support ticket](includes/support.md)]
