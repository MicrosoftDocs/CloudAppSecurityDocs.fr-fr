---
title: Utiliser Cloud Discovery données pour détecter un comportement risqué
description: Cette rubrique fournit des instructions pour l’utilisation des données Cloud Discovery, notamment l’utilisation de l’indice de risque de l’application.
ms.date: 05/06/2019
ms.topic: conceptual
ms.openlocfilehash: 0ae744dcdc777ab806654abb7862ec27730be143
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96315597"
---
# <a name="working-with-discovery-data"></a>Utilisation des données de découverte

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Le tableau de bord Cloud Discovery est conçu pour vous donner plus d’informations sur l’utilisation des applications cloud dans votre organisation. Il fournit une vue d’ensemble en un clin d’œil des types d’applications utilisés, des alertes ouvertes et des niveaux de risque des applications dans votre organisation. Il vous montre également les principaux utilisateurs des applications et fournit un plan du lieu du siège social d’une application. Le tableau de bord Cloud Discovery a de nombreuses options pour filtrer les données. Le filtrage vous permet de générer des vues spécifiques selon ce qui vous intéresse le plus, avec des graphiques faciles à comprendre pour vous donner une vision globale en un clin d’œil.

![tableau de bord Cloud Discovery](media/cloud-discovery-dashboard.png)

## <a name="review-the-cloud-discovery-dashboard"></a>Consulter le tableau de bord Cloud Discovery

La première chose à faire pour obtenir une vue d’ensemble de vos applications Cloud Discovery consiste à examiner les informations suivantes du tableau de bord Cloud Discovery :

1. Examinez d’abord l’utilisation globale des applications cloud dans votre organisation dans la **Vue d’ensemble de l’utilisation générale**.

2. Approfondissez ensuite cet examen pour identifier les **principales catégories** utilisées dans votre organisation pour chacun des différents paramètres d’utilisation. Vous pouvez voir la part d’utilisation des applications approuvées.

3. Allez encore plus loin et affichez toutes les applications d’une catégorie spécifique sous l’onglet **Applications découvertes**.

4. Vous pouvez voir les **principaux utilisateurs et adresses IP sources** pour identifier les utilisateurs qui emploient le plus les applications cloud dans votre organisation.
5. Vérifiez comment les applications découvertes sont réparties en fonction de l’emplacement géographique (d’après le siège social) dans le **Plan des sièges sociaux des applications**.

6. Enfin, n’oubliez pas de consulter le score de risque de l’application découverte dans la **vue d’ensemble des risques des applications**. Vérifiez **l’état des alertes de découverte** pour voir le nombre d’alertes ouvertes à passer en revue.

## <a name="exclude-entities"></a>Exclure des entités

Si vous avez des utilisateurs système, des adresses IP ou des appareils bruyants, mais non intéressants, ou des applications qui ne sont pas pertinents, vous souhaiterez peut-être exclure leurs données des données Cloud Discovery qui sont analysées. Par exemple, vous pouvez exclure toutes les informations provenant de 127.0.0.1 ou de l’hôte local.

Pour créer une exclusion :

1. Dans le portail, sous l’icône Paramètres, sélectionnez **Paramètres Cloud Discovery**.
2. Cliquez sur l’onglet **Exclure des entités**.
3. Choisissez l’onglet **utilisateurs exclus**, **adresses IP exclues** ou **périphérique exclu** , puis cliquez sur le bouton + pour ajouter votre exclusion.
4. Ajoutez un alias d’utilisateur, une adresse IP ou un nom de périphérique. Nous vous recommandons d’ajouter des informations sur les raisons de l’exclusion.

    ![exclure l’utilisateur](media/exclude-user.png "exclure l’utilisateur")

## <a name="manage-continuous-reports"></a>Gérer les rapports continus

Les rapports continus personnalisés vous apportent une plus grande granularité lors de la surveillance des données de journaux Cloud Discovery de votre organisation. En créant des rapports personnalisés, vous pouvez filtrer sur des emplacements géographiques, des réseaux, des sites ou des unités d’organisation spécifiques. Par défaut, seuls les rapports suivants apparaissent dans votre sélecteur de rapports Cloud Discovery :

- Le **rapport global** regroupe toutes les informations du portail provenant de toutes les sources de données que vous avez incluses dans vos journaux.  Le rapport global n’inclut pas les données de Microsoft Defender ATP.

- Le **rapport spécifique à la source de données** affiche uniquement les informations d’une source de données spécifique.

Pour créer un rapport continu :

1. Dans le portail, sous l’icône Paramètres, sélectionnez **Paramètres Cloud Discovery**.

2. Cliquez sur l’onglet **Rapport continu**.

3. Cliquez sur le bouton **Créer un rapport**.

4. Entrez un nom de rapport.

5. Sélectionnez les sources de données à inclure (toutes ou certaines).

6. Définissez les filtres souhaités sur les données. Ces filtres peuvent être des **groupes d’utilisateurs**, des **balises d’adresse IP** ou des **plages d’adresses IP**. Pour plus d’informations sur l’utilisation de balises d’adresse IP et de plages d’adresses IP, voir [Organiser les données selon vos besoins](ip-tags.md).

    ![créer un rapport continu personnalisé](media/create-custom-continuous-report.png)

> [!NOTE]
> Tous les rapports personnalisés sont limitées à 1 Go de données maximum non compressées. En cas de dépassement, le premier 1 Go de données est exporté dans le rapport.

## <a name="deleting-cloud-discovery-data"></a>Suppression de données Cloud Discovery

Plusieurs raisons peuvent vous amener à supprimer vos données Cloud Discovery. Nous vous recommandons de les supprimer dans les cas suivants :

- Vous avez chargé manuellement les fichiers journaux, vous avez attendu longtemps avant de mettre à jour le système avec de nouveaux fichiers journaux et vous ne voulez pas que les anciennes données affectent vos résultats.

- Quand vous définissez une nouvelle vue de données personnalisée, elle s’applique seulement aux nouvelles données à partir de ce moment. Vous pouvez ainsi effacer les anciennes données, puis recharger vos fichiers journaux pour permettre à la vue de données personnalisée de sélectionner des événements dans les données des fichiers journaux.

- Si de nombreux utilisateurs ou adresses IP sont à nouveau actifs après une longue période hors connexion, leur activité est identifiée comme étant anormale et vous risquez d’obtenir de nombreuses violations qui sont en fait des faux positifs.

Pour supprimer des données Cloud Discovery :

1. Dans le portail, sous l’icône Paramètres, sélectionnez **Paramètres Cloud Discovery**.

2. Cliquez sur l’onglet **Supprimer les données**.

    Il est important d’être sûr de vouloir supprimer les données avant de poursuivre : cette opération ne peut pas être annulée et **toutes** les données Cloud Discovery dans le système sont alors supprimées.

3. Cliquez sur le bouton **Supprimer**.

    ![supprimer des données](media/delete-data.png "supprimer des données")

    > [!NOTE]
    >  Le processus de suppression peut prendre quelques minutes et il n’est pas immédiat.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
