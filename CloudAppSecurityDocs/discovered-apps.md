---
title: Utilisation des applications découvertes dans Cloud App Security
description: Cet article décrit le processus d’identification et de correction des applications Cloud Discovery risquées dans Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 09/25/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: a63546a3404cdf4c48a56b800f5d80d09ee5971e
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285473"
---
# <a name="working-with-discovered-apps"></a>Utilisation des applications découvertes

*S’applique à : Microsoft Cloud App Security*

Le tableau de bord Cloud Discovery est conçu pour vous donner plus d’informations sur l’utilisation des applications cloud dans votre organisation. Il fournit une vue d’ensemble des types d’applications utilisés, des alertes ouvertes et des niveaux de risque des applications de votre organisation. Il vous montre également les principaux utilisateurs des applications et fournit un plan du lieu du siège social d’une application. Le tableau de bord Cloud Discovery présente de nombreuses options pour filtrer les données. Le filtrage vous permet de générer des vues spécifiques en fonction de ce qui vous intéresse le plus à l’aide de graphiques faciles à comprendre pour vous offrir une vue d’ensemble d’un coup d’œil.

![tableau de bord Cloud Discovery](media/cloud-discovery-dashboard.png)

## <a name="review-the-cloud-discovery-dashboard"></a>Consulter le tableau de bord Cloud Discovery

La première chose à faire pour obtenir une image générale de vos applications Cloud Discovery consiste à consulter les informations suivantes dans le tableau de bord Cloud Discovery :

1. Examinez d’abord l’utilisation globale de l’application Cloud dans votre organisation dans la **vue d’ensemble de l’utilisation de haut niveau**.

1. Explorez ensuite un niveau plus profond pour voir quelles sont les **principales catégories** utilisées dans votre organisation pour chacun des différents paramètres d’utilisation. Vous pouvez voir la quantité de cette utilisation en cas de sanctions sur les applications.

1. Allez encore plus loin et affichez toutes les applications dans une catégorie spécifique sous l’onglet **applications découvertes** .

1. Vous pouvez voir les **principaux utilisateurs et adresses IP sources** pour identifier les utilisateurs qui emploient le plus les applications cloud dans votre organisation.
1. Vérifiez comment les applications découvertes sont réparties en fonction de l’emplacement géographique (d’après le siège social) dans le **Plan des sièges sociaux des applications**.

1. Enfin, n’oubliez pas de consulter le score de risque de l’application découverte dans la **vue d’ensemble des risques des applications**. Vérifiez l' **État des alertes de découverte** pour afficher le nombre d’alertes ouvertes à examiner.

## <a name="deep-dive-into-discovered-apps"></a>Examen approfondi des applications découvertes

Si vous souhaitez approfondir la présentation des données fournies par Cloud Discovery, utilisez les filtres pour vérifier les applications qui sont risquées et celles qui sont couramment utilisées.

Par exemple, si vous voulez identifier les applications de collaboration et de stockage cloud à risque couramment utilisées, vous pouvez utiliser la page Applications découvertes pour rechercher les applications souhaitées. Ensuite, vous pouvez ne pas approuver [ou bloquer](governance-discovery.md) les éléments comme suit :

1. Dans la page **Applications découvertes**, sous **Parcourir par catégorie**, sélectionnez **Stockage cloud** et **Collaboration**.

1. Ensuite, utilisez les filtres avancés et définissez le **facteur de risque de conformité** sur **SOC 2** égal à **faux**

1. Pour **l’utilisation**, définissez **les utilisateurs** sur plus de 50 utilisateurs et **l’utilisation** des **transactions** sur une valeur supérieure à 100.

1. Définir le **facteur de risque de sécurité** pour les **données au chiffrement Rest** est égal à **non pris en charge**. Définissez ensuite le **score de risque** sur une valeur égale ou inférieure à 6.

![Filtres d’application découverte](media/discovered-app-filters.png)

Une fois que les résultats sont filtrés, vous pouvez [ne pas approuver et bloquer](governance-discovery.md) ces applications en cochant la case d’action en bloc pour ne pas les approuver toutes en une seule action. Une fois qu’ils ne sont pas approuvés, vous pouvez utiliser un script de blocage pour empêcher leur utilisation dans votre environnement.

Cloud Discovery vous permet d’approfondir l’utilisation du Cloud de votre organisation. Vous pouvez identifier des instances spécifiques en cours d’utilisation en étudiant les sous-domaines découverts.

Par exemple, vous pouvez différencier les différents sites SharePoint.

Cela est pris en charge uniquement dans les pare-feu et les proxys qui contiennent des données d’URL cibles. Pour plus d’informations, consultez la liste des appareils pris en charge dans les [pare-feu et proxys pris en charge](set-up-cloud-discovery.md#supported-firewalls-and-proxies).

![informations sur le sous-domaine](media/discovery-domains.png)

## <a name="discover-resources-and-custom-apps"></a>Découvrir les ressources et les applications personnalisées

Cloud Discovery vous permet également d’explorer en profondeur vos ressources IaaS et PaaS. Vous pouvez découvrir les activités de vos plateformes d’hébergement de ressources en voyant les accès aux données de vos ressources et de vos applications auto-hébergées, notamment les comptes de stockage, l’infrastructure et les applications personnalisées hébergées sur Azure, Google Cloud Platform et AWS. Non seulement vous pouvez voir l’utilisation générale dans vos solutions IaaS, mais aussi obtenir une visibilité sur les ressources spécifiques qui sont hébergées sur chacune d’elles et l’utilisation générale des ressources pour aider à atténuer les risques par ressource.

Par exemple, à partir de Cloud App Security, vous pouvez superviser l’activité de chargement d’une grande quantité de données en découvrant sur quelle ressource elles sont chargées et en explorant les détails pour voir qui a effectué l’activité.

> [!NOTE]
> Cela est pris en charge uniquement dans les pare-feu et les proxys qui contiennent des données d’URL cibles. Pour plus d’informations, consultez la liste des appareils pris en charge dans les [pare-feu et proxys pris en charge](set-up-cloud-discovery.md#supported-firewalls-and-proxies).

Pour voir les ressources découvertes :

1. Dans le portail Cloud App Security, sélectionnez **Découvrir**, puis **Ressources découvertes**.

    ![Menu des ressources découvertes](media/discovered-resources-menu.png)

1. Dans la page des ressources découvertes, vous pouvez explorer chaque ressource pour voir les types de transactions effectuées, qui y a accédé et aller encore plus dans les détails pour en savoir plus sur les utilisateurs.

   ![Découverte de ressources](media/discovery-resources.png)

1. Pour les applications personnalisées, vous pouvez cliquer sur les trois boutons à la fin de la ligne et sélectionnez **Ajouter une application personnalisée**. Cette opération ouvre la fenêtre **Ajouter une application personnalisée** qui vous permet de nommer et identifier l’application afin de pouvoir l’inclure dans le tableau de bord Cloud Discovery.

## <a name="generate-cloud-discovery-executive-report"></a>Générer un rapport de Cloud Discovery Executive

La meilleure façon d’obtenir une vue d’ensemble de l’utilisation des clichés instantanés au sein de votre organisation consiste à générer un rapport de Cloud Discovery Executive. Ce rapport identifie les principaux risques potentiels et vous aide à planifier un flux de travail afin d’atténuer et de gérer les risques jusqu’à ce qu’ils soient résolus.

Pour générer un rapport de Cloud Discovery Executive :

1. Dans le **tableau de bord Cloud Discovery**, cliquez sur les trois points dans l’angle supérieur droit du tableau de bord, puis sélectionnez **générer Cloud Discovery rapport exécutif**.
1. Si vous le souhaitez, modifiez le nom du rapport.
1. Cliquez sur **Générer**.

## <a name="exclude-entities"></a>Exclure des entités

Si vous avez des utilisateurs système, des adresses IP ou des ordinateurs bruyants, mais non intéressants, ou des applications qui ne sont pas pertinentes, vous pouvez exclure leurs données du Cloud Discovery données analysées. Par exemple, vous pouvez exclure toutes les informations provenant de 127.0.0.1 ou de l’hôte local.

Pour créer une exclusion :

1. Dans le portail, sous l’icône Paramètres, sélectionnez **Paramètres Cloud Discovery**.

1. Cliquez sur l’onglet **Exclure des entités**.

1. Choisissez l’onglet **utilisateurs exclus**, **adresses IP exclues**ou **machines exclues** , puis cliquez sur le bouton + pour ajouter votre exclusion.

1. Ajoutez un alias d’utilisateur, une adresse IP ou un nom d’ordinateur. Nous vous recommandons d’ajouter des informations sur la raison pour laquelle l’exclusion a été effectuée.

    ![exclure un utilisateur](media/exclude-user.png "exclure un utilisateur")

## <a name="manage-continuous-reports"></a>Gérer les rapports continus

Les rapports continus personnalisés vous apportent une plus grande granularité lors de la surveillance des données de journaux Cloud Discovery de votre organisation. En créant des rapports personnalisés, il est possible de filtrer sur des emplacements géographiques, des réseaux et des sites ou des unités d’organisation spécifiques. Par défaut, seuls les rapports suivants apparaissent dans votre sélecteur de rapports Cloud Discovery :

- Le **rapport global** regroupe toutes les informations du portail provenant de toutes les sources de données que vous avez incluses dans vos journaux.  Le rapport global n’inclut pas de données de Microsoft Defender ATP.

- Le **rapport spécifique à la source de données** affiche uniquement les informations d’une source de données spécifique.

Pour créer un rapport continu :

1. Dans le portail, sous l’icône Paramètres, sélectionnez **Paramètres Cloud Discovery**.

1. Cliquez sur l’onglet **rapport continu** .

1. Cliquez sur le bouton **Créer un rapport**.

1. Entrez un nom de rapport.

1. Sélectionnez les sources de données à inclure (toutes ou certaines).

1. Définissez les filtres de votre choix sur les données. Ces filtres peuvent être des **groupes d’utilisateurs**, des **balises d’adresse IP**ou des **plages d’adresses IP**. Pour plus d’informations sur l’utilisation de balises d’adresse IP et de plages d’adresses IP, voir [Organiser les données selon vos besoins](ip-tags.md).

    ![créer un rapport continu personnalisé](media/create-custom-continuous-report.png)

> [!NOTE]
> Tous les rapports personnalisés sont limités à un maximum de 1 Go de données non compressées. S’il y a plus de 1 Go de données, les 1 premiers Go de données seront exportés dans le rapport.

## <a name="deleting-cloud-discovery-data"></a>Suppression de données Cloud Discovery

Plusieurs raisons peuvent vous amener à supprimer vos données Cloud Discovery. Nous vous recommandons de les supprimer dans les cas suivants :

- Vous avez chargé manuellement des fichiers journaux, l’eau a longtemps coulé sous les ponts avant que vous ne mettiez à jour le système avec de nouveaux fichiers journaux et vous ne voulez pas que les anciennes données affectent vos résultats.

- Lorsque vous définissez une nouvelle vue de données personnalisée, elle s’applique uniquement aux nouvelles données à partir de ce point. Par conséquent, vous pouvez effacer les anciennes données, puis charger à nouveau vos fichiers journaux pour permettre à la vue de données personnalisée de récupérer des événements dans les données du fichier journal.

- Si de nombreux utilisateurs ou adresses IP ont récemment commencé à travailler à nouveau après avoir été hors connexion pendant un certain temps, leur activité est identifiée comme anormale et peut entraîner des fausses violations positives.

Pour supprimer des données Cloud Discovery :

1. Dans le portail, sous l’icône Paramètres, sélectionnez **Paramètres Cloud Discovery**.

1. Cliquez sur l’onglet **Supprimer les données**.

    Il est important de bien vouloir supprimer les données avant de continuer : elles ne peuvent pas être annulées et **toutes les** Cloud Discovery données du système sont supprimées.

1. Cliquez sur le bouton **Supprimer**.

    ![supprimer des données](media/delete-data.png "supprimer des données")

    > [!NOTE]
    > Le processus de suppression peut prendre quelques minutes et il n’est pas immédiat.

## <a name="next-steps"></a>Étapes suivantes :

> [!div class="nextstepaction"]
> [Créer des rapports d’instantanés Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

> [!div class="nextstepaction"]
> [Configurer le chargement automatique des journaux pour des rapports continus](configure-automatic-log-upload-for-continuous-reports.md)

> [!div class="nextstepaction"]
> [Utilisation des données Cloud Discovery](working-with-cloud-discovery-data.md)
