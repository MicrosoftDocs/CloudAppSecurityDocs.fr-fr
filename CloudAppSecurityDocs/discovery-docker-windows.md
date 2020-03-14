---
title: Déployer des rapports continus pour des Cloud App Security à l’aide d’un ancrage sur Windows | Microsoft Docs
description: Cet article décrit le processus de configuration du chargement automatique des journaux pour les rapports continus dans Cloud App Security à l’aide d’un ancrage sur Windows sur un serveur local.
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
ms.openlocfilehash: 9122a5c5cdde5f2a1ed02946970825b75155acc2
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285583"
---
# <a name="docker-on-windows-on-premises"></a>Ancrer sur Windows sur site

*S’applique à : Microsoft Cloud App Security*

Vous pouvez configurer le chargement automatique des journaux pour des rapports continus dans Cloud App Security à l’aide d’un ancrage sur Windows.

## <a name="prerequisites"></a>Composants requis

* Système d’exploitation : **Windows 10** (mise à jour des créateurs de automne), Windows Server **version 1709 +** (sac) ou **Windows Server 2019 (LTSC)**

* Espace disque : 250 Go

* Processeur : 2

* RAM : 4 Go

* Définir votre pare-feu comme décrit dans [Configuration réseau requise](network-requirements.md#log-collector)

* La virtualisation sur le système d’exploitation doit être activée avec Hyper-V

> [!IMPORTANT]
> Un utilisateur doit être connecté pour que l’arrimeur collecte les journaux. Nous vous recommandons de recommander aux utilisateurs de votre conseiller de se déconnecter sans fermer la session.

> [!NOTE]
> Si vous disposez d’un collecteur de journaux existant et que vous souhaitez le supprimer avant de le déployer à nouveau, ou si vous souhaitez simplement le supprimer, exécutez les commandes suivantes :
>
> ```console
> docker stop <collector_name>
> docker rm <collector_name>
> ```

## <a name="log-collector-performance"></a>Performances du collecteur de journaux

Le collecteur de journaux peut gérer correctement une capacité allant jusqu’à 50 Go par heure. Les principaux goulots d’étranglement dans le processus de collecte des journaux sont les suivants :

* Bande passante réseau : la bande passante réseau détermine la vitesse de chargement des journaux.

* Performances d’e/s de la machine virtuelle : détermine la vitesse à laquelle les journaux sont écrits sur le disque du collecteur de journaux. Le collecteur de journaux dispose d’un mécanisme de sécurité intégré qui surveille le débit auquel les journaux arrivent et le compare au débit de chargement. En cas de congestion, le collecteur de journaux commence à supprimer des fichiers journaux. Si votre configuration dépasse généralement 50 Go par heure, il est recommandé de répartir le trafic entre plusieurs collecteurs de journaux.

## <a name="set-up-and-configuration"></a>Installation et configuration

### <a name="step-1--web-portal-configuration-define-data-sources-and-link-them-to-a-log-collector"></a>Étape 1 : configuration du portail web  - définir les sources de données et les lier à un collecteur de journaux

1. Accédez à la page Paramètres de **chargement automatique des journaux** .

    1. Dans le portail Cloud App Security, cliquez sur l’icône des paramètres, puis sur **collecteurs de journaux**.

    ![icône Paramètres](media/settings-icon.png)

1. Pour chaque pare-feu ou proxy à partir duquel vous souhaitez télécharger des journaux, créez une source de données correspondante.

    1. Cliquez sur **Ajouter une source de données**.  
    ![ajouter une source de données](media/add-data-source.png)
    1. **Nommez** votre proxy ou pare-feu.  
    ![ubuntu1](media/ubuntu1.png)
    1. Sélectionnez l’appareil dans la liste **Source**. Si vous sélectionnez **format de journal personnalisé** pour utiliser une appliance réseau qui n’est pas listée, consultez [utilisation de l’analyseur de journal personnalisé](custom-log-parser.md) pour obtenir des instructions de configuration.
    1. Comparez votre journal à l’exemple de format de journal attendu. Si votre format de fichier journal ne correspond pas à cet exemple, vous devez ajouter votre source de données en tant qu' **autre**.
    1. Définissez le **Type de récepteur** sur **FTP**, **FTPS**, **Syslog – UDP**, **Syslog – TCP** ou **Syslog – TLS**.

    > [!NOTE]
    > L’intégration aux protocoles de transfert sécurisé (FTPS et Syslog – TLS) nécessite souvent que des paramètres supplémentaires soient configurés dans votre pare-feu/proxy.

    f. Répétez ce processus pour chaque pare-feu ou proxy dont les journaux peuvent être utilisés pour détecter le trafic sur votre réseau. Il est recommandé de configurer une source de données dédiée par périphérique réseau pour vous permettre d’effectuer les opérations suivantes :

    * Surveiller l’état de chaque appareil séparément, à des fins d’investigation.
    * Explorez Shadow IT Discovery par appareil, si chaque appareil est utilisé par un segment d’utilisateur différent.

1. Accédez à l’onglet **Collecteurs de journaux** en haut.

    1. Cliquez sur **Ajouter un collecteur de journaux**.
    1. Donnez un **nom** au collecteur de journaux.
    1. Entrez l' **adresse IP** de l’ordinateur hôte que vous allez utiliser pour déployer l’ancrage. L’adresse IP de l’hôte peut être remplacée par le nom de l’ordinateur, s’il existe un serveur DNS (ou équivalent) qui va résoudre le nom d’hôte.
    1. Sélectionnez toutes les **sources de données** que vous souhaitez connecter au collecteur, puis cliquez sur **mettre à jour** pour enregistrer la configuration.
    ![ubuntu2](media/ubuntu2.png)

1. Des informations supplémentaires sur le déploiement vont s’afficher. **Copiez** la commande Exécuter à partir de la boîte de dialogue. Vous pouvez utiliser l’icône copier dans le presse-papiers, ![icône copier dans le presse-papiers](media/copy-icon.png). Vous en aurez besoin plus tard.

1. **Exportez** la configuration de source de données attendue. Cette configuration décrit la façon dont vous devez configurer l’exportation de journaux dans vos appliances.

    ![Créer un collecteur de journaux](media/windows7.png)

    > [!NOTE]
    >
    > * Un seul collecteur de journaux peut gérer plusieurs sources de données.
    > * Copiez le contenu de l’écran, car vous aurez besoin des informations lors de la configuration du collecteur de journaux pour communiquer avec Cloud App Security. Si vous avez sélectionné Syslog, ces informations vont inclure des informations sur le port utilisé par l’écouteur Syslog pour écouter.
    > * Pour les utilisateurs qui envoient des données de journal via FTP pour la première fois, nous vous recommandons de modifier le mot de passe de l’utilisateur FTP. Pour plus d’informations, consultez [modification du mot de passe FTP](log-collector-ftp.md#changing-the-ftp-password).

### <a name="step-2--on-premises-deployment-of-your-machine"></a>Étape 2 : Déploiement local de votre machine

Les étapes suivantes décrivent le déploiement dans Windows. La procédure de déploiement pour les autres plateformes est légèrement différente.

1. Ouvrez un terminal PowerShell en tant qu’administrateur sur votre ordinateur Windows.

1. Exécutez la commande suivante pour télécharger le fichier de script PowerShell du programme d’installation de Windows Dockr : `Invoke-WebRequest https://adaprodconsole.blob.core.windows.net/public-files/LogCollectorInstaller.ps1 -OutFile (Join-Path $Env:Temp LogCollectorInstaller.ps1)`

    Pour vérifier que le programme d’installation est signé par Microsoft, consultez [valider la signature du programme d’installation](#validate-signature)

1. Pour activer l’exécution du script PowerShell, exécutez `Set-ExecutionPolicy RemoteSigned`

1. Exécuter : `& (Join-Path $Env:Temp LogCollectorInstaller.ps1)` installe le client docker sur votre ordinateur. Pendant l’installation du conteneur log Collector, l’ordinateur est redémarré deux fois et vous devez vous reconnecter. **Assurez-vous que le client Dockr est configuré pour utiliser des conteneurs Linux.**

1. Après chaque redémarrage, ouvrez un terminal PowerShell en tant qu’administrateur sur votre ordinateur, puis réexécutez : `& (Join-Path $Env:Temp LogCollectorInstaller.ps1)`

1. Avant la fin de l’installation, vous devrez coller la commande d’exécution que vous avez copiée précédemment.

1. Déployez l’image du collecteur sur l’ordinateur hôte en important la configuration du collecteur. Importez la configuration en copiant la commande Run générée dans le portail. Si vous devez configurer un proxy, ajoutez l’adresse IP et le numéro de port du proxy. Par exemple, si les détails de votre proxy sont 192.168.10.1:8080, votre commande Exécuter ressemblera à ceci :

    ```console
    (echo db3a7c73eb7e91a0db53566c50bab7ed3a755607d90bb348c875825a7d1b2fce) | docker run --name MyLogCollector -p 21:21 -p 20000-20099:20000-20099 -e "PUBLICIP='192.168.1.1'" -e "PROXY=192.168.10.1:8080" -e "CONSOLE=mod244533.us.portal.cloudappsecurity.com" -e "COLLECTOR=MyLogCollector" --security-opt apparmor:unconfined --cap-add=SYS_ADMIN --restart unless-stopped -a stdin -i microsoft/caslogcollector starter
    ```

    ![Créer un collecteur de journaux](media/windows7.png)

1. Vérifiez que le collecteur s’exécute correctement avec la commande suivante : `docker logs <collector_name>`

Vous devriez voir le message suivant : **Terminé avec succès**

![ubuntu8](media/ubuntu8.png)

### <a name="step-3---on-premises-configuration-of-your-network-appliances"></a>Étape 3 : configuration locale de vos appliances réseau

Configurez vos pare-feu réseau et proxys pour exporter régulièrement les journaux vers le port syslog dédié du répertoire FTP selon les instructions de la boîte de dialogue. Par exemple :

```console
BlueCoat_HQ - Destination path: \<<machine_name>>\BlueCoat_HQ\
```

### <a name="step-4---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>Étape 4 : vérifier la réussite du déploiement dans le portail Cloud App Security

Consultez l’état du collecteur dans le tableau **Collecteur de journaux** et vérifiez que l’état est **Connecté**. S’il est **créé**, il est possible que la connexion du collecteur de journaux et l’analyse ne soient pas terminées.

![ubuntu9](media/ubuntu9.png)

Vous pouvez également accéder au **Journal de gouvernance** et vérifier que les journaux sont régulièrement chargés sur le portail.

Si vous rencontrez des problèmes pendant le déploiement, consultez [résolution des problèmes Cloud Discovery](troubleshooting-cloud-discovery.md).

### Facultatif : créer des rapports continus personnalisés<a name="continuous-reports"></a>

Vérifiez que les journaux sont téléchargés vers Cloud App Security et que les rapports sont générés. Après la vérification, créez des rapports personnalisés. Vous pouvez créer des rapports de découverte personnalisés basés sur des groupes d’utilisateurs Azure Active Directory. Par exemple, si vous souhaitez voir l’utilisation du Cloud de votre service marketing, importez le groupe marketing à l’aide de la fonctionnalité importer un groupe d’utilisateurs. Créez ensuite un rapport personnalisé pour ce groupe. Vous pouvez également personnaliser un rapport en fonction d’une balise d’adresse IP ou de plages d’adresses IP.

1. Dans le portail Cloud App Security, sous l’roue dentée paramètres, sélectionnez Cloud Discovery paramètres, puis sélectionnez **rapports continus**.
1. Cliquez sur le bouton **Créer un rapport** et renseignez les champs.
1. Sous **Filtres**, vous pouvez filtrer les données par source de données, par [groupe d’utilisateurs importé](user-groups.md) ou par [balises et plages d’adresses IP](ip-tags.md).

    ![Rapport continu personnalisé](media/custom-continuous-report.png)

### Facultatif-valider la signature du programme d’installation<a name="validate-signature"></a>

Pour vous assurer que le programme d’installation de dockr est signé par Microsoft :

1. Cliquez avec le bouton droit sur le fichier et sélectionnez **Propriétés**.
1. Cliquez sur **signatures numériques** et assurez-vous qu’elle indique que **cette signature numérique est correcte**.
1. Assurez-vous que **Microsoft Corporation** est indiqué comme seule entrée sous le **nom du signataire**.

    ![Signature numérique valide](media/digital-signature-successful.png)

Si la signature numérique n’est pas valide, elle indique que la **signature numérique n’est pas valide**:

![Signature numérique non valide](media/digital-signature-unsuccessful.png)

## <a name="next-steps"></a>Étapes suivantes :

> [!div class="nextstepaction"]
> [Configuration FTP du collecteur de journaux](log-collector-ftp.md)

[!INCLUDE [Open support ticket](includes/support.md)]
