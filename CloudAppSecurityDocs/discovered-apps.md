---
title: Utilisation des applications découvertes dans Cloud App Security
description: Ce démarrage rapide décrit le processus d’identification et de correction des applications Cloud Discovery à risque dans Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/10/2019
ms.topic: quickstart
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 645fd8c7-06d0-4f93-a85c-2976e7b3766d
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 589f0d11d7fac47a4080926f6aa4f654c17deb34
ms.sourcegitcommit: 076705cc9684fe5fb35c33a51e3319ba2ccfd24e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2019
ms.locfileid: "54060171"
---
# <a name="quickstart-work-with-discovered-apps"></a>Démarrage rapide : Utiliser des applications découvertes

*S’applique à : Microsoft Cloud App Security*

Ce démarrage rapide vous fournit des informations de prise en main sur la façon de surveiller et de gérer des applications découvertes. Le tableau de bord Cloud Discovery est conçu pour vous donner plus d’informations sur l’utilisation des applications cloud dans votre organisation. Il fournit une vue d’ensemble en un clin d’œil des types d’applications utilisés, des alertes ouvertes et des niveaux de risque des applications dans votre organisation. Il vous montre également les principaux utilisateurs des applications et fournit un plan du lieu du siège social d’une application. Le tableau de bord Cloud Discovery a de nombreuses options pour filtrer les données. Le filtrage vous permet de générer des vues spécifiques selon ce qui vous intéresse le plus, avec des graphiques faciles à comprendre pour vous donner une vision globale en un clin d’œil.

![tableau de bord Cloud Discovery](./media/cloud-discovery-dashboard.png)

## <a name="review-the-cloud-discovery-dashboard"></a>Consulter le tableau de bord Cloud Discovery

La première chose à faire pour obtenir une vue d’ensemble de vos applications Cloud Discovery consiste à examiner les informations suivantes du tableau de bord Cloud Discovery :
 
1. Examinez d’abord l’utilisation globale des applications cloud dans votre organisation dans la **Vue d’ensemble de l’utilisation générale**.

2. Approfondissez ensuite cet examen pour identifier les **principales catégories** utilisées dans votre organisation pour chacun des différents paramètres d’utilisation. Vous pouvez voir la part d’utilisation des applications approuvées.

3. Allez encore plus loin et affichez toutes les applications d’une catégorie spécifique sous l’onglet **Applications découvertes**.

4. Vous pouvez voir les **principaux utilisateurs et adresses IP sources** pour identifier les utilisateurs qui emploient le plus les applications cloud dans votre organisation.
5. Vérifiez comment les applications découvertes sont réparties en fonction de l’emplacement géographique (d’après le siège social) dans le **Plan des sièges sociaux des applications**.

6. Enfin, n’oubliez pas de consulter le score de risque de l’application découverte dans la **vue d’ensemble des risques de l’application**. Vérifiez **l’état des alertes de découverte** pour voir le nombre d’alertes ouvertes à passer en revue.

## <a name="deep-dive-into-discovered-apps"></a>Examen approfondi des applications découvertes

Si vous voulez examiner en détail les données fournies par Cloud Discovery, utilisez les filtres pour vérifier les applications qui sont considérées comme étant à risque et celles qui sont couramment utilisées.


Par exemple, si vous voulez identifier les applications de collaboration et de stockage cloud à risque couramment utilisées, vous pouvez utiliser la page Applications découvertes pour rechercher les applications souhaitées. Vous pouvez par la suite [ne pas approuver ou bloquer](governance-discovery.md) ces applications, comme suit :

1. Dans la page **Applications découvertes**, sous **Parcourir par catégorie**, sélectionnez **Stockage cloud** et **Collaboration**.
2. Ensuite, utilisez les filtres avancés et définissez **Facteur de risque de conformité** sur **SOC 2** égal à **False**
3. Pour **Utilisation**, définissez **Utilisateurs** sur une valeur supérieure à 50 et **Utilisation** pour **Transactions** sur une valeur supérieure à 100.
4. Définissez le **Facteur de risque de sécurité** pour **Chiffrement des données au repos** sur **Non pris en charge**. Définissez ensuite **Score de risque** sur une valeur inférieure ou égale à 6.

![Filtres d’application découverte](./media/discovered-app-filters.png)

Une fois que les résultats sont filtrés, vous pouvez [ne pas approuver et bloquer](governance-discovery.md) ces applications en cochant la case d’action en bloc pour ne pas les approuver toutes en une seule action. Une fois qu’elles sont non approuvées, vous pouvez utiliser un script de blocage pour empêcher leur utilisation dans votre environnement.

Cloud Discovery vous permet de voir de façon encore plus approfondie l’utilisation du cloud de votre organisation. Vous pouvez identifier des instances spécifiques qui sont utilisées en examinant les sous-domaines découverts.
     
Vous pouvez par exemple effectuer la distinction entre différents sites SharePoint.

Cette fonctionnalité est prise en charge uniquement dans les pare-feu et les proxys qui contiennent des données d’URL cibles. Pour plus d’informations, consultez la liste des appliances prises en charge dans [Pare-feux et proxys pris en charge](create-snapshot-cloud-discovery-reports.md#supported-firewalls-and-proxies).

 ![informations sur les sous-domaines](./media/discovery-domains.png) 

## <a name="generate-cloud-discovery-executive-report"></a>Générer un rapport exécutif Cloud Discovery

La meilleure façon d’obtenir une vue d’ensemble de l’utilisation du Shadow IT dans votre organisation est de générer un rapport exécutif Cloud Discovery. Ce rapport identifie les principaux risques potentiels et vous permet de planifier un flux de travail pour atténuer et gérer les risques jusqu’à leur résolution.

Pour générer un rapport Cloud Discovery efficace : 

Dans le **tableau de bord Cloud Discovery**, cliquez sur les trois points en haut à droite du menu et sélectionnez **Générer un rapport exécutif Cloud Discovery**.

## <a name="exclude-entities"></a>Exclure des entités

Si des utilisateurs, des adresses IP ou des machines génèrent du bruit mais ne sont pas intéressants, ou si des applications ne sont pas pertinentes, vous pouvez exclure leurs données des données Cloud Discovery qui sont analysées. Par exemple, vous pouvez exclure toutes les informations provenant de 127.0.0.1 ou de l’hôte local.  
  
Pour créer une exclusion :  
  
1. Dans le portail, sous l’icône Paramètres, sélectionnez **Paramètres Cloud Discovery**.  
2. Cliquez sur l’onglet **Exclure des entités**.  
3. Choisissez l’onglet **Utilisateurs exclus**, **Adresses IP exclues** ou **Machines exclues**, puis cliquez sur le bouton + pour ajouter votre exclusion.
4. Ajoutez un alias utilisateur, une adresse IP ou un nom de machine. Nous vous recommandons d’ajouter des informations sur les raisons de l’exclusion.
  
     ![exclure l’utilisateur](./media/exclude-user.png "exclure l’utilisateur")  
  
## <a name="manage-continuous-reports"></a>Gérer les rapports continus

Les rapports continus personnalisés vous apportent une plus grande granularité lors de la surveillance des données de journaux Cloud Discovery de votre organisation. En créant des rapports personnalisés, vous pouvez filtrer sur des emplacements géographiques, des réseaux, des sites ou des unités d’organisation spécifiques. Par défaut, seuls les rapports suivants apparaissent dans votre sélecteur de rapports Cloud Discovery :  
  
- Le **rapport global** regroupe toutes les informations du portail provenant de toutes les sources de données que vous avez incluses dans vos journaux.  
  
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
 
[Créer des rapports d’instantanés Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Configurer le chargement automatique des journaux pour des rapports continus](configure-automatic-log-upload-for-continuous-reports.md)

[Utilisation des données Cloud Discovery](working-with-cloud-discovery-data.md)

