---
title: "Utilisation des applications découvertes dans Cloud App Security | Microsoft Docs"
description: "Cette rubrique décrit le processus d’identification et de correction des applications Cloud Discovery à risque dans Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 9/26/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 645fd8c7-06d0-4f93-a85c-2976e7b3766d
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: d349488692f006908426fd8f33eb6ae654350958
ms.sourcegitcommit: 8759541301241e03784c5ac87b56986f22bd0561
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2017
---
# <a name="working-with-discovered-apps"></a>Utilisation des applications découvertes

## <a name="review-the-cloud-discovery-dashboard"></a>Consulter le tableau de bord Cloud Discovery

Le tableau de bord Cloud Discovery est conçu pour vous donner plus d’informations sur l’utilisation des applications cloud dans votre organisation. Il fournit une vue d’ensemble en un clin d’œil des types d’applications utilisés, des alertes ouvertes et des niveaux de risque des applications dans votre organisation. Il vous montre également les principaux utilisateurs des applications et fournit un plan du lieu du siège social d’une application. Le tableau de bord Cloud Discovery présente de nombreuses options pour filtrer les données et vous permettre ainsi de générer des vues spécifiques selon ce qui vous intéresse le plus, et des graphiques faciles à comprendre pour vous donner une vision globale en un clin d’œil.

![tableau de bord Cloud Discovery](./media/cloud-discovery-dashboard.png)

La première chose à faire pour obtenir une vue d’ensemble de vos applications Cloud Discovery consiste à examiner le tableau de bord Cloud Discovery et à passer en revue les éléments suivants :
 
1. Examinez d’abord l’utilisation générale des applications cloud dans votre organisation dans la **Vue d’ensemble de l’utilisation générale**.

2. Approfondissez ensuite cet examen pour identifier les **principales catégories** utilisées dans votre organisation pour chacun des différents paramètres d’utilisation, ainsi que la part utilisée par les applications approuvées.

3. Allez encore plus loin et affichez toutes les applications dans une catégorie spécifique dans le widget **Applications découvertes**.

4. Vous pouvez voir les **principaux utilisateurs et adresses IP sources** pour identifier les utilisateurs qui emploient le plus les applications cloud dans votre organisation.
5. Vérifiez comment les applications découvertes sont réparties en fonction de l’emplacement géographique (d’après le siège social) dans le **Plan des sièges sociaux des applications**.

6. Enfin, n’oubliez pas de consulter le score de risque de l’application découverte dans la **Vue d’ensemble des risques des applications** et de vérifier **l’état des alertes de découverte** pour afficher le nombre d’alertes ouvertes à examiner.

## <a name="deep-dive-into-discovered-apps"></a>Examen approfondi des applications découvertes
Si vous voulez examiner en détail les données fournies par Cloud Discovery, utilisez les filtres pour vérifier les applications qui sont à risque et celles qui sont couramment utilisées.


Par exemple, si vous voulez identifier les applications de collaboration et de stockage cloud à risque couramment utilisées, vous pouvez utiliser la page Applications découvertes pour rechercher les applications souhaitées. Vous pouvez par la suite [ne pas approuver ou bloquer](governance-discovery.md) ces applications, comme suit :

Dans la page **Applications découvertes**, sous **Parcourir par catégorie**, sélectionnez **Stockage cloud** et **Collaboration**. Ensuite, utilisez les filtres avancés et définissez **Facteur de risque de conformité** sur **SOC 2** égal à **False** ; **Utilisation** > **Utilisateurs** sur supérieure à 50 utilisateurs ; et **Utilisation** > **Transactions** sur supérieure à 100 ; **Facteur de risque de sécurité** > **Chiffrement de données au repos** égal à **False**, puis définissez **Score de risque** égal à moins de 6.

![Filtres d’application découverte](./media/discovered-app-filters.png)

Une fois que les résultats sont filtrés, vous pouvez [ne pas approuver et bloquer](governance-discovery.md) ces applications en cochant la case d’action en bloc pour ne pas les approuver toutes en une seule action. Une fois qu’elles sont non approuvées, vous pouvez utiliser un script de blocage pour empêcher leur utilisation dans votre environnement.

Cloud Discovery vous permet d’analyser de manière encore plus approfondie l’utilisation du cloud au sein de votre organisation, et d’identifier les instances spécifiques qui sont en cours d’utilisation en étudiant les sous-domaines de découverte.

Vous pouvez par exemple effectuer la distinction entre différents sites SharePoint.

Cette fonctionnalité est prise en charge uniquement dans les pare-feu et les proxys qui contiennent des données d’URL cibles. Consultez la liste des appliances prises en charge dans [Pare-feu et proxys pris en charge](set-up-cloud-discovery.md#supported-firewalls-and-proxies).

![informations sur les sous-domaines](./media/discovery-domains.png)  

## <a name="discovered-app-filters"></a>Filtres d’application découverte

Il existe des filtres d’application découverte de base et avancés. Pour obtenir un filtre complexe (comme dans l’exemple ci-dessus), utilisez l’option avancée qui inclut tous les éléments suivants :

![Applications découvertes](./media/discovered-apps.png)  


- **Balise d’application** : Indiquez si l’application a été approuvée, non approuvée ou non marquée. Par ailleurs, vous pouvez créer une balise personnalisée pour votre application et l’utiliser pour filtrer des types spécifiques d’applications. 
- **Applications et domaines** : Permet de rechercher des applications spécifiques ou des applications utilisées dans des domaines spécifiques. 
- **Catégories** : Le filtre de catégories, qui se trouve à gauche de la page, vous permet de rechercher des types d’applications selon des catégories d’applications, par exemple, des applications de réseau social, des applications de stockage cloud, etc. Vous pouvez sélectionner plusieurs catégories à la fois, ou une seule catégorie, puis leur appliquer des filtres de base et avancés.
- **Facteur de risque de conformité** : Permet de rechercher des normes, certifications et conformités spécifiques auxquelles l’application doit se conformer (HIPAA, ISO 27001, SOC 2, PCI-DSS, etc.).
- **Facteur de risque général** : Permet de rechercher des facteurs de risque général comme la popularité auprès des consommateurs, les paramètres régionaux du centre de données, etc.
- **Score de risque** : Permet de filtrer les applications par score de risque pour que vous puissiez vous concentrer uniquement sur les applications très risquées, par exemple. Vous pouvez également remplacer le score de risque défini par Cloud App Security. Pour plus d’informations, consultez [Utilisation du score de risque](risk-score.md).
- **Facteur de risque de sécurité** : Permet de filtrer en fonction de mesures de sécurité spécifiques (comme le chiffrement au repos, l’authentification multifacteur, etc.).
- **Utilisation** : Permet de filtrer en fonction des statistiques d’utilisation de cette application, comme les applications avec une quantité supérieure ou inférieure de **chargements de données** que la quantité spécifiée, les applications avec un nombre supérieur ou inférieur **d’utilisateurs** que le nombre spécifié.

## <a name="creating-and-managing-custom-app-tags"></a>Création et gestion des balises d’application personnalisées

Vous pouvez créer une balise d’application personnalisée. Ces balises peuvent ensuite servir de filtres pour rechercher plus précisément des types spécifiques d’applications que vous voulez examiner. Par exemple, une liste de suivi personnalisée, l’attribution à une division spécifique ou des approbations personnalisées, comme « approuvé par le service juridique ».

Pour créer une balise d’application personnalisée :

1. Dans le menu **Paramètres** (roue dentée), sélectionnez **Cloud Discovery** et sous l’onglet **Gérer les balises d’application**, cliquez sur l’icône ![plus](./media/plus-icon.png). 

![créer une balise d’application personnalisée](./media/create-app-tag.png)

2. Vous pouvez utiliser le tableau **Gérer les balises d’application** pour consulter les applications qui sont actuellement marquées avec chaque balise d’application et vous pouvez supprimer les balises d’application inutilisées.

3. Pour appliquer une balise d’application, sous l’onglet **Applications découvertes**, cliquez sur les points de suspension complètement à droite du tableau et sélectionnez la balise d’application à appliquer. 

> [!NOTE]
>Vous pouvez également créer une balise d’application directement dans le tableau **Applications découvertes** en cliquant sur **Créer une balise d’application** après avoir sélectionné les points de suspension à droite de n’importe quelle application sélectionnée. Vous pouvez également accéder à l’écran **Gérer les balises d’application** en cliquant sur le lien dans le coin de la fenêtre contextuelle **Créer une balise d’application**.

## <a name="exclude-entities"></a>Exclure des entités  
Si certains utilisateurs ou certaines adresses IP sont particulièrement bruyants et inintéressants ou si des applications ne sont pas pertinentes, vous pouvez exclure leurs données des données Cloud Discovery qui sont analysées. Par exemple, vous pouvez exclure toutes les informations provenant de 127.0.0.1 ou de l’hôte local.  
  
Pour créer une exclusion :  
  
1.  Dans le portail, sous l’icône Paramètres, sélectionnez **Paramètres Cloud Discovery**.  
  
2.  Cliquez sur l’onglet **Exclure des entités**.  
  
3.  Choisissez l’onglet **Utilisateurs exclus** ou **Adresses IP exclues**, puis cliquez sur le bouton **Ajouter un utilisateur** ou **Ajouter une adresse IP**.  
  
4.  Ajoutez une adresse IP ou un alias utilisateur. Nous vous recommandons d’ajouter des informations sur les raisons de l’exclusion de l’utilisateur ou de l’adresse IP.  
  
     ![exclure l’utilisateur](./media/exclude-user.png "exclure l’utilisateur")  
  
## <a name="manage-continuous-reports"></a>Gérer les rapports continus  
Les rapports continus personnalisés vous apportent une plus grande granularité lors de la surveillance des données de journaux Cloud Discovery de votre organisation. En créant des rapports personnalisés, vous pouvez filtrer sur des emplacements géographiques, des réseaux et sites ou des unités d’organisation spécifiques. Par défaut, seuls les rapports suivants apparaissent dans votre sélecteur de rapports Cloud Discovery :  
  
-  Le **rapport global** regroupe toutes les informations du portail provenant de toutes les sources de données que vous avez incluses dans vos journaux.  
  
- Le **rapport spécifique à la source de données** affiche uniquement les informations d’une source de données spécifique.  
  
Pour créer un rapport continu :  
  
1.  Dans le portail, sous l’icône Paramètres, sélectionnez **Paramètres Cloud Discovery**.  
  
2.  Cliquez sur l’onglet **Gérer un rapport continu**.  
  
3.  Cliquez sur le bouton **Créer un rapport**.  
  
4.  Entrez un nom de rapport.  
  
5.  Sélectionnez les sources de données à inclure (toutes ou certaines).  
  
6.  Définissez les filtres voulus sur les données, qui peuvent être **Unités d’organisation**, **Balises d’adresse IP** ou **Plages d’adresses IP**. Pour plus d’informations sur l’utilisation de balises d’adresse IP et de plages d’adresses IP, voir [Organiser les données selon vos besoins](ip-tags.md).  
  
    ![créer un rapport continu personnalisé](./media/create-custom-continuous-report.png) 

> [!NOTE]
> Tous les rapports personnalisés sont limitées à 1 Go de données maximum non compressées. En cas de dépassement, le premier 1 Go de données est exporté dans le rapport.


## <a name="deleting-cloud-discovery-data"></a>Suppression de données Cloud Discovery  
Plusieurs raisons peuvent vous amener à supprimer vos données Cloud Discovery. Nous vous recommandons de les supprimer dans les cas suivants :  
  
-   Vous avez chargé manuellement les fichiers journaux, vous avez attendu longtemps avant de mettre à jour le système avec de nouveaux fichiers journaux et vous ne voulez pas que les anciennes données affectent vos résultats.  
  
-   Vous définissez une nouvelle vue de données personnalisée qui s’applique uniquement aux nouvelles données à compter de moment-là, alors vous pouvez effacer les anciennes données, puis charger à nouveau vos fichiers journaux pour permettre à la vue de données personnalisée de sélectionner des événements dans les données de fichiers journaux.  
  
-   De nombreux utilisateurs ou adresses IP sont à nouveau actifs après une longue période hors connexion. Leur activité est identifiée comme étant anormale et vous risquez d’obtenir de nombreuses violations qui sont en fait des faux positifs.  
  
Pour supprimer des données Cloud Discovery :  
  
1.  Dans le portail, sous l’icône Paramètres, sélectionnez **Paramètres Cloud Discovery**.  
  
2.  Cliquez sur l’onglet **Supprimer les données**.  
  
     Il est important d’être sûr de vouloir supprimer les données avant de poursuivre : cette opération ne peut pas être annulée et **toutes** les données Cloud Discovery dans le système sont alors supprimées.  
  
3.  Cliquez sur le bouton **Supprimer**.  
  
     ![supprimer des données](./media/delete-data.png "supprimer des données")  
  
   > [!NOTE]  
   >  Le processus de suppression peut prendre quelques minutes et il n’est pas immédiat.  




## <a name="see-also"></a>Voir aussi
 
[Créer des rapports d’instantanés Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Configurer le chargement automatique des journaux pour des rapports continus](configure-automatic-log-upload-for-continuous-reports.md)

[Utilisation des données Cloud Discovery](working-with-cloud-discovery-data.md)

