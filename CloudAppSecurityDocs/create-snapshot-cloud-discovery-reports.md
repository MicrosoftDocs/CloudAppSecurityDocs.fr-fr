---
title: Créer des rapports d’instantané de l’utilisation des applications cloud dans Cloud Discovery
description: Cet article fournit des informations sur le chargement manuel de journaux pour créer un rapport d’instantané de vos applications Cloud Discovery.
ms.date: 04/07/2019
ms.topic: how-to
ms.openlocfilehash: ad1f2ad7c94d543cdd82f655e4b27aaa987bf290
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96312061"
---
# <a name="create-snapshot-cloud-discovery-reports"></a>Créer des rapports d’instantanés Cloud Discovery

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Il est important de charger un journal manuellement et de laisser Microsoft Cloud App Security l’analyser avant d’essayer d’utiliser le collecteur de journaux automatique. Pour plus d’informations sur le fonctionnement du collecteur de journaux et le format de journal attendu, consultez [Utilisation de journaux de trafic pour Cloud Discovery](#log-format).

Si vous n’avez pas encore de journal et que vous voulez voir à quoi ressemble un journal, téléchargez un exemple de fichier journal. Suivez la procédure ci-dessous pour voir à quoi doit ressembler votre journal.

Pour créer un rapport d’instantané :

1. Collectez les fichiers journaux de votre pare-feu et de votre proxy, via lesquels les utilisateurs de votre organisation accèdent à Internet. Veillez à collecter les journaux pendant les heures de pointe représentatives de toute l’activité utilisateur dans votre organisation.

1. Dans le portail Cloud App Security, cliquez sur **découvrir**, puis sur **créer un rapport d’instantané**.

    ![Créer un rapport d’instantané](media/create-new-snapshot-report.png)

1. Entrer un **nom de rapport** et une **Description**

    ![Nouveau rapport d’instantané](media/new-snapshot-report.png)

1. Sélectionnez la **source de données** à partir de laquelle vous souhaitez charger les fichiers journaux.

1. Examinez le format de votre journal pour vérifier qu’il est mis en forme correctement en vous basant sur l’exemple de journal que vous pouvez télécharger. Cliquez sur **afficher et vérifier** , puis sur **Télécharger l’exemple de journal**. Comparez votre journal à l’exemple fourni pour vérifier qu’il est compatible.

    ![Vérifier le format de votre journal](media/cloud-discovery-snapshot-verify.png)

    > [!NOTE]
    > L’exemple de format FTP est pris en charge dans les instantanés et dans le chargement automatique, tandis que syslog n’est pris en charge que dans le chargement automatique. Le téléchargement d’un exemple de journal télécharge un exemple de journal FTP.

1. **Choisissez les journaux d’activité de trafic** que vous souhaitez charger. Vous pouvez charger jusqu’à 20 fichiers à la fois. Les fichiers compressés et zippés sont également pris en charge.

1. Cliquez sur **Créer**.

1. Une fois le chargement terminé, un message d’état s’affiche dans le coin supérieur droit de votre écran pour vous informer que le journal a correctement été chargé.

1. Une fois que vos fichiers journaux sont chargés, un certain temps est nécessaire pour leur extraction et leur analyse.
    Après le traitement de vos fichiers journaux, vous recevez un e-mail pour vous avertir que l’opération est terminée.

1. Une bannière de notification apparaît dans la barre d’état en haut du **tableau de bord Cloud Discovery**. La bannière se met à jour avec l’état du traitement de vos fichiers journaux.
    ![barre de menus du traitement des fichiers journaux](media/processing-log-file-menu-bar.png)

1. Une fois les journaux téléchargés, une notification vous informant que le traitement du fichier journal s’est terminé correctement doit s’afficher. À ce stade, vous pouvez afficher le rapport en cliquant sur le lien dans la barre d’État, ou en cliquant sur l' ![icône](media/settings-icon.png "Icône des paramètres")paramètres roue dentée paramètres, puis sélectionnez **paramètres**.

1. Ensuite, sous **Cloud Discovery**, sélectionnez **instantané rapports**, puis sélectionnez votre rapport d’instantané.

    ![gestion des rapports d’instantanés](media/snapshot-report-managment.png)

## <a name="using-traffic-logs-for-cloud-discovery"></a>Utilisation des journaux de trafic pour Cloud Discovery <a name="log-format"></a>

Cloud Discovery utilise les données de vos journaux de trafic. Plus le journal est détaillé, meilleure est la visibilité. Cloud Discovery nécessite des données de trafic web avec les attributs suivants :

- Date de la transaction
- IP Source
- Utilisateur source (vivement recommandé)
- Adresse IP de destination
- URL de destination **recommandée** (les URL assurent une meilleure précision pour la détection d’applications cloud que les adresses IP)
- Quantité totale de données (les informations de données sont extrêmement précieuses)
- Quantité de données chargées ou téléchargées (fournit des informations sur les modèles d’utilisation des applications cloud)
- Action effectuée (autorisée/bloquée)

Cloud Discovery ne peut pas afficher ni analyser des attributs qui ne se trouvent pas dans vos journaux.
Par exemple, le format de journal standard **Pare-feu Cisco ASA** ne contient pas le **nombre d’octets chargés par transaction**, le **nom d’utilisateur** et **l’URL cible** (il contient seulement l’adresse IP cible).
Par conséquent, ces attributs ne sont pas affichés dans les données Cloud Discovery pour ces journaux et la visibilité sur les applications cloud est limitée. Pour les pare-feu Cisco ASA, il est nécessaire de définir le niveau d’informations 6.

Pour générer correctement un rapport Cloud Discovery, vos journaux de trafic doivent respecter les conditions suivantes :

1. La [source de données est prise en charge](set-up-cloud-discovery.md#supported-firewalls-and-proxies).
2. Le format de journal correspond au format standard attendu (le format est vérifié lors du chargement par l’outil Log).
3. Les événements ne datent pas de plus de 90 jours.
4. Le fichier journal est valide et inclut des informations sur le trafic sortant.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
