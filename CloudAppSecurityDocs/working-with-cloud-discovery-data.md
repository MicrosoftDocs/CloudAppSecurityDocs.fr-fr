---
title: Utiliser les données Cloud Discovery pour détecter les comportements à risques - Cloud App Security | Microsoft Docs
description: Cette rubrique fournit des instructions pour l’utilisation des données Cloud Discovery, notamment l’utilisation de l’indice de risque de l’application.
keywords: ''
author: shsagir
ms.author: shsagir
manager: angrobe
ms.date: 05/06/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: cf94b290-b7ef-4fee-854e-c8ff8d11dea9
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 5e289a3eea5bbc3306bfe6fa07c5a9084145e6d1
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74459254"
---
# <a name="working-with-discovery-data"></a>Utilisation des données de découverte

*S’applique à : Microsoft Cloud App Security*

Le tableau de bord Cloud Discovery est conçu pour vous donner plus d’informations sur l’utilisation des applications cloud dans votre organisation. Il fournit une vue d’ensemble en un clin d’œil des types d’applications utilisés, des alertes ouvertes et des niveaux de risque des applications dans votre organisation. Il vous montre également les principaux utilisateurs des applications et fournit un plan du lieu du siège social d’une application. Le tableau de bord Cloud Discovery a de nombreuses options pour filtrer les données. Le filtrage vous permet de générer des vues spécifiques selon ce qui vous intéresse le plus, avec des graphiques faciles à comprendre pour vous donner une vision globale en un clin d’œil.

![tableau de bord Cloud Discovery](./media/cloud-discovery-dashboard.png)

## <a name="review-the-cloud-discovery-dashboard"></a>Consulter le tableau de bord Cloud Discovery

La première chose à faire pour obtenir une vue d’ensemble de vos applications Cloud Discovery consiste à examiner les informations suivantes du tableau de bord Cloud Discovery :
 
1. Examinez d’abord l’utilisation globale des applications cloud dans votre organisation dans la **Vue d’ensemble de l’utilisation générale**.

2. Approfondissez ensuite cet examen pour identifier les **principales catégories** utilisées dans votre organisation pour chacun des différents paramètres d’utilisation. Vous pouvez voir la part d’utilisation des applications approuvées.

3. Allez encore plus loin et affichez toutes les applications d’une catégorie spécifique sous l’onglet **Applications découvertes**.

4. Vous pouvez voir les **principaux utilisateurs et adresses IP sources** pour identifier les utilisateurs qui emploient le plus les applications cloud dans votre organisation.
5. Vérifiez comment les applications découvertes sont réparties en fonction de l’emplacement géographique (d’après le siège social) dans le **Plan des sièges sociaux des applications**.

6. Enfin, n’oubliez pas de consulter le score de risque de l’application découverte dans la **vue d’ensemble des risques de l’application**. Vérifiez **l’état des alertes de découverte** pour voir le nombre d’alertes ouvertes à passer en revue.

## <a name="exclude-entities"></a>Exclure des entités

Si des utilisateurs, des adresses IP ou des machines génèrent du bruit mais ne sont pas intéressants, ou si des applications ne sont pas pertinentes, vous pouvez exclure leurs données des données Cloud Discovery qui sont analysées. Par exemple, vous pouvez exclure toutes les informations provenant de 127.0.0.1 ou de l’hôte local.  
  
Pour créer une exclusion :  
  
1. Dans le portail, sous l’icône Paramètres, sélectionnez **Paramètres Cloud Discovery**.  
2. Cliquez sur l’onglet **Exclure des entités**.  
3. Choisissez l’onglet **Utilisateurs exclus**, **Adresses IP exclues** ou **Machines exclues**, puis cliquez sur le bouton + pour ajouter votre exclusion.
4. Ajoutez un alias utilisateur, une adresse IP ou un nom de machine. Nous vous recommandons d’ajouter des informations sur les raisons de l’exclusion.
  
     ![exclure un utilisateur](./media/exclude-user.png "exclure l’utilisateur")  

## <a name="manage-continuous-reports"></a>Gérer les rapports continus

Les rapports continus personnalisés vous apportent une plus grande granularité lors de la surveillance des données de journaux Cloud Discovery de votre organisation. En créant des rapports personnalisés, vous pouvez filtrer sur des emplacements géographiques, des réseaux, des sites ou des unités d’organisation spécifiques. Par défaut, seuls les rapports suivants apparaissent dans votre sélecteur de rapports Cloud Discovery :  
  
- Le **rapport global** regroupe toutes les informations du portail provenant de toutes les sources de données que vous avez incluses dans vos journaux.  Le rapport global n’inclut pas de données de Microsoft Defender ATP.
  
- Le **rapport spécifique à la source de données** affiche uniquement les informations d’une source de données spécifique.  
  
Pour créer un rapport continu :  
  
1. Dans le portail, sous l’icône Paramètres, sélectionnez **Paramètres Cloud Discovery**.  
  
2. Cliquez sur l’onglet **Rapport continu**.  
  
3. Cliquez sur le bouton **Créer un rapport**.  
  
4. Entrez un nom de rapport.  
  
5. Sélectionnez les sources de données à inclure (toutes ou certaines).  
  
6. Définissez les filtres souhaités sur les données. Ces filtres peuvent être **Groupes d’utilisateurs**, **Balises d’adresse IP** ou **Plages d’adresses IP**. Pour plus d’informations sur l’utilisation de balises d’adresse IP et de plages d’adresses IP, voir [Organiser les données selon vos besoins](ip-tags.md).  
  
    ![créer un rapport continu personnalisé](./media/create-custom-continuous-report.png) 

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
  
    ![supprimer des données](./media/delete-data.png "supprimer des données")  
  
   > [!NOTE]  
   >  Le processus de suppression peut prendre quelques minutes et il n’est pas immédiat.


 
## <a name="next-steps"></a>Étapes suivantes

[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   

[!INCLUDE [Open support ticket](includes/support.md)]  
  
  
