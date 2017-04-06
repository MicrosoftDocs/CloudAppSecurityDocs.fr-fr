---
title: Utilisation du score de risque | Microsoft Docs
description: "Cette rubrique fournit des instructions sur l’utilisation et la personnalisation du score de risque Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/2/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 9cb3594e-5007-48be-9b4f-e1d23355d86e
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 2fcc085cc53d2d7580640022029b1a528bea416a
ms.sourcegitcommit: 661f4ce41262e8462c90fd2a4f1232e2154d5113
translationtype: HT
---
# <a name="working-with-the-risk-score"></a>Utilisation du score de risque  

## <a name="the-cloud-app-catalog"></a>Catalogue d’applications cloud

Pour mieux comprendre les applications cloud pouvant être découvertes par la fonction Cloud Discovery de Cloud App Security, utilisez le catalogue d’applications cloud.

Ce catalogue répertorie plus de 14 000 applications SaaS qui peuvent être affichées (filtrées) par nom, domaine, indice de risque, catégorie ou fonctionnalités de sécurité disponibles.

![accéder au catalogue d’applications cloud](./media/risk-cac-dropdown.png)

## <a name="discovery-requests"></a>Requêtes de découverte

Les informations et les indices de risque du catalogue d’applications cloud s’appuient sur de nombreuses sources. Microsoft s’efforce de maintenir à jour ces informations, mais n’offre aucune garantie quant à l’exactitude de toutes les sources de données. 

Veuillez nous contacter si vous pensez que les informations relatives à une application sont obsolètes.

-    Demandez une mise à jour des indices (si vous souhaitez que notre équipe réévalue une application cloud).
-    Signalez de nouvelles données générales ou spécifiques (si vous pensez que les informations relatives à une application sont obsolètes).

![mettre à jour des données de risque](./media/risk-cac-feedback.png)

En outre, nous vous encourageons à demander l’ajout de toutes les applications cloud que votre organisation utilise et qui ne sont actuellement pas détectables par la fonction Cloud Discovery.

![suggérer de nouvelles applications](./media/risk-suggest-app.png)


## <a name="customizing-the-risk-score"></a>Personnalisation de l’indice de risque

Cloud Discovery vous fournit des données importantes sur la crédibilité et la fiabilité des applications cloud qui sont utilisées au sein de l’environnement. Dans le portail, chaque application découverte est présentée avec un score total, qui représente l’évaluation par Cloud App Security du niveau de maturité de l’utilisation par les entreprises de cette application particulière. Le score total d’une application donnée est une moyenne pondérée de trois sous-scores liés à trois sous-catégories que Cloud App Security prend en compte pour évaluer la fiabilité :  
  
-   **Général** : Cette catégorie fait référence à des informations basiques sur la société qui produit l’application, notamment son domaine, l’année de sa fondation et sa popularité. Ces champs ont vocation à illustrer la stabilité de la société au niveau le plus simple.  
  
-   **Sécurité** : La catégorie Sécurité tient compte de toutes les normes liées à la sécurité physique des données utilisées par l’application découverte. Sont inclus des champs tels que l’authentification multifacteur, le chiffrement, la classification des données et la propriété des données.  
  
-   **Conformité** : Cette catégorie présente les normes de conformité issues des bonnes pratiques en usage que la société qui produit l’application respecte. La liste des spécifications inclut des normes telles que HIPAA, CSA et PCI-DSS.  
  
Chacune de ces catégories comprend de nombreuses propriétés spécifiques. Selon notre algorithme de calcul de score, chaque propriété reçoit un score préliminaire compris entre 0 et 10, selon sa valeur. Les valeurs True/False reçoivent 10 ou 0 en conséquence, tandis que les propriétés continues telles que l’âge du domaine reçoivent une certaine valeur comprise dans le spectre. Le score de chaque propriété est pondéré par rapport à tous les autres champs existants dans la catégorie, pour créer le sous-score de la catégorie. Si vous rencontrez une application sans score, cela indique généralement que les propriétés de cette application sont inconnues et qu’elle n’a donc pas de score.  
  
Prenez le temps de passer en revue et modifier les pondérations par défaut données à la configuration du score Cloud Discovery. Par défaut, tous les différents paramètres évalués reçoivent une pondération identique. Si certains paramètres sont plus ou moins importants pour votre organisation, il est important de les modifier comme suit :  
  
1.  Dans le portail, sous l’icône Paramètres, sélectionnez **Paramètres Cloud Discovery**.  
  
2.  Sous **Configurer la métrique du score**, faites glisser le curseur **Importance** pour modifier la pondération du champ ou la catégorie de risque. Vous avez le choix entre les options **Ignoré**, **Bas**, **Moyen**, **Élevé** ou **Très élevé**.  
  
3.  De plus, vous pouvez déterminer si certaines valeurs sont soit non disponibles, soit non applicables dans le calcul du score. Quand elles sont incluses, les valeurs N/A contribuent négativement au score calculé.  
  
     ![score](./media/score.png "score")  

Toutes les informations nécessaires pour comprendre le fonctionnement de nos indices de risque et leur empilement sont disponibles dans le portail Cloud App Security.
Pour mieux comprendre le poids d’un facteur de risque dans une catégorie donnée, utilisez le bouton « i » à droite d’un nom de champ dans le profil de l’application. Il fournit des informations sur la façon dont Cloud App Security note précisément un facteur de risque. Ce score correspond à la valeur du facteur de risque sur une échelle de 1 à 10 et à son poids dans la catégorie de risque :

![calcul du risque](./media/cac-weight.png)
  
Pour comprendre le poids d’une catégorie de risque dans le score total d’une application, déplacez le curseur sur le score de catégorie de risque :

![poids de la catégorie de risque](./media/risk-category-weight.png)


 
## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  