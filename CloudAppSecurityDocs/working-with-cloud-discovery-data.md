---
title: "Utiliser les données Cloud Discovery pour détecter les comportements à risques | Microsoft Docs"
description: "Cette rubrique fournit des instructions pour l’utilisation des données Cloud Discovery, notamment l’utilisation de l’indice de risque de l’application."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/19/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: cf94b290-b7ef-4fee-854e-c8ff8d11dea9
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 872c5839a3fbf54e4e4d07ef9ac0629aef29aaad
ms.sourcegitcommit: 1a01ac2d5b4ff92e46e1bc4fd4318330f6ff41dd
translationtype: HT
---
# <a name="working-with-cloud-discovery"></a>Utilisation de Cloud Discovery
## <a name="review-the-cloud-discovery-dashboard"></a>Consulter le tableau de bord Cloud Discovery

Le tableau de bord Cloud Discovery est conçu pour vous donner plus d’informations sur l’utilisation des applications cloud dans votre organisation. Il fournit une vue d’ensemble en un clin d’œil des types d’applications utilisés, des alertes ouvertes et des niveaux de risque des applications dans votre organisation. Il vous montre également les principaux utilisateurs des applications et fournit un plan du lieu du siège social d’une application. Le tableau de bord Cloud Discovery présente de nombreuses options pour filtrer les données et vous permettre ainsi de générer des vues spécifiques selon ce qui vous intéresse le plus, et des graphiques faciles à comprendre pour vous donner une vision globale en un clin d’œil.

![tableau de bord Cloud Discovery](./media/cloud-discovery-dashboard.png)

La première chose à faire pour obtenir une vue d’ensemble de vos applications Cloud Discovery consiste à examiner le tableau de bord Cloud Discovery et à passer en revue les éléments suivants :
 
1. Examinez d’abord l’usage global des applications cloud dans votre organisation dans la vue d’ensemble de l’utilisation générale.

2. Approfondissez ensuite cet examen pour identifier les principales catégories utilisées dans votre organisation pour chacun des différents paramètres d’utilisation, dont la part utilisée par les applications approuvées.

3. Allez encore plus loin et affichez toutes les applications dans une catégorie spécifique dans le widget Applications découvertes.

4. Vous pouvez voir les principaux utilisateurs et les adresses IP sources pour identifier les utilisateurs qui emploient le plus les applications cloud dans votre organisation.
5. Vérifiez comment les applications découvertes sont réparties en fonction de l’emplacement géographique (selon leur siège social) dans le plan des sièges sociaux des applications.

6. Enfin, n’oubliez pas de consulter l’indice de risque de l’application découverte dans la vue d’ensemble des risques des applications et de vérifier l’état des alertes de détection pour afficher le nombre d’alertes ouvertes à examiner.


## <a name="customize-the-risk-score"></a>Personnaliser le score de risque  
Cloud Discovery vous fournit des données importantes sur la crédibilité et la fiabilité des applications cloud qui sont utilisées au sein de l’environnement. Dans le portail, chaque application découverte est présentée avec un score total, qui représente l’évaluation par Cloud App Security du niveau de maturité de l’utilisation par les entreprises de cette application particulière. Le score total d’une application donnée est une moyenne pondérée de trois sous-scores liés à trois sous-catégories que Cloud App Security prend en compte pour évaluer la fiabilité :  
  
-   **Général** : Cette catégorie fait référence à des informations basiques sur la société qui produit l’application, notamment son domaine, l’année de sa fondation et sa popularité. Ces champs ont vocation à illustrer la stabilité de la société au niveau le plus simple.  
  
-   **Sécurité** : La catégorie Sécurité tient compte de toutes les normes liées à la sécurité physique des données utilisées par l’application découverte. Sont inclus des champs tels que l’authentification multifacteur, le chiffrement, la classification des données et la propriété des données.  
  
-   **Conformité** : Cette catégorie présente les normes de conformité issues des bonnes pratiques en usage que la société qui produit l’application respecte. La liste des spécifications inclut des normes telles que HIPAA, CSA et PCI-DSS.  
  
Chacune de ces catégories comprend de nombreuses propriétés spécifiques. Selon notre algorithme de calcul de score, chaque propriété reçoit un score préliminaire compris entre 0 et 10, selon sa valeur. Les valeurs True/False reçoivent 10 ou 0 en conséquence, tandis que les propriétés continues telles que l’âge du domaine reçoivent une certaine valeur comprise dans le spectre. Le score de chaque propriété est pondéré par rapport à tous les autres champs existants dans la catégorie, pour créer le sous-score de la catégorie. Si vous rencontrez une application sans score, cela indique généralement que les propriétés de cette application sont inconnues et qu’elle n’a donc pas de score.  
  
Prenez le temps de passer en revue et modifier les pondérations par défaut données à la configuration du score Cloud Discovery. Par défaut, tous les différents paramètres évalués reçoivent une pondération identique. Si certains paramètres sont plus ou moins importants pour votre organisation, il est important de les modifier comme suit :  
  
1.  Dans le portail, sous l’icône Paramètres, sélectionnez **Paramètres Cloud Discovery**.  
  
2.  Sous **Configuration de la métrique du score**, faites glisser le curseur **Importance** pour choisir la pondération du champ parmi les options **Ignoré**, **Bas**, **Moyen**, **Élevé** ou **Très élevé**.  
  
3.  De plus, vous pouvez déterminer si certaines valeurs sont soit non disponibles, soit non applicables dans le calcul du score. Quand elles sont incluses, les valeurs N/A contribuent négativement au score calculé.  
  
     ![score](./media/score.png "score")  
  
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
  
6.  Définissez les filtres voulus sur les données, qui peuvent être **Unités d’organisation**, **Balises d’adresse IP** ou **Plages d’adresses IP**. Pour plus d’informations sur l’utilisation de balises d’adresse IP et de plages d’adresses IP, voir [Organiser les données selon vos besoins](general-setup.md#IPtagsandRanges).  
  
    ![créer un rapport continu personnalisé](./media/create-custom-continuous-report.png) 
  
## <a name="exclude-entities"></a>Exclure des entités  
Si certains utilisateurs ou certaines adresses IP sont particulièrement bruyants et inintéressants ou si des applications ne sont pas pertinentes, vous pouvez exclure leurs données des données Cloud Discovery qui sont analysées. Par exemple, vous pouvez exclure toutes les informations provenant de 127.0.0.1 ou de l’hôte local.  
  
Pour créer une exclusion :  
  
1.  Dans le portail, sous l’icône Paramètres, sélectionnez **Paramètres Cloud Discovery**.  
  
2.  Cliquez sur l’onglet **Exclure des entités**.  
  
3.  Choisissez l’onglet **Utilisateurs exclus** ou **Adresses IP exclues**, puis cliquez sur le bouton **Ajouter un utilisateur** ou **Ajouter une adresse IP**.  
  
4.  Ajoutez une adresse IP ou un alias utilisateur. Nous vous recommandons d’ajouter des informations sur les raisons de l’exclusion de l’utilisateur ou de l’adresse IP.  
  
     ![exclure l’utilisateur](./media/exclude-user.png "exclure l’utilisateur")  
  
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
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  