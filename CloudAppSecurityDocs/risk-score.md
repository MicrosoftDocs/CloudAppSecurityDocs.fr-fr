---
title: Utiliser l’indice de risque – Cloud App Security | Microsoft Docs
description: Cet article fournit des instructions sur l’utilisation et la personnalisation de l’indice de risque Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 9cb3594e-5007-48be-9b4f-e1d23355d86e
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 8427aa87af9b986b482901cf3671e54a6aa6fac3
ms.sourcegitcommit: b86c3afd1093fbc825fec5ba4103e3a95f65758e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53177434"
---
# <a name="working-with-the-risk-score"></a>Utilisation du score de risque

*S’applique à : Microsoft Cloud App Security*

Le catalogue d’applications cloud vous donne une vue d’ensemble complète des éléments identifiés par Cloud Discovery. Cloud Discovery analyse vos journaux de trafic en s’appuyant sur le catalogue d’applications cloud Microsoft Cloud App Security, qui contient plus de 16 000 applications cloud. Les applications sont classées et évaluées selon plus de 70 facteurs de risque, afin de vous offrir une visibilité en continu de l’utilisation du cloud, du « Shadow IT » et du risque que celui-ci représente pour votre organisation. Cet article fournit des instructions sur l’utilisation et la personnalisation de l’indice de risque Cloud App Security.

## <a name="the-cloud-app-catalog"></a>Catalogue d’applications cloud

Le **catalogue d’applications cloud** évalue les risques pour vos applications cloud selon les certifications réglementaires, les normes du secteur et les bonnes pratiques. Quatre processus complémentaires s’exécutent dans le catalogue d’applications cloud pour le tenir à jour :
1. Extraction de données automatisée directement à partir de l’application cloud. L’extraction est utilisée pour les attributs tels que la conformité SOC 2, les conditions d’utilisation du service, l’URL de connexion, la politique de confidentialité et l’emplacement du siège social.
2. Extraction de données avancée automatisée pour les données par les algorithmes de Cloud App Security (pour les attributs tels que les en-têtes de sécurité HTTP).
3. Analyse en continu par l’équipe d’analystes cloud Cloud App Security (pour les attributs tels que le chiffrement au repos).
4. Demandes de révisions basées sur le client, en fonction des demandes de soumissions du client des modifications à apporter au catalogue d’applications cloud. Toutes les demandes sont examinées par notre équipe d’analystes cloud et mises à jour en fonction de leurs conclusions.
  
![Catalogue d’applications cloud](./media/cloud-app-catalog.png)  

Les divisions sont de plus en plus à la recherche d’applications cloud pour répondre à leurs besoins changeants. Le catalogue d’applications cloud vous permet de choisir judicieusement les applications qui répondent le mieux aux exigences de sécurité de votre organisation. Le catalogue vous tient informé des dernières normes de sécurité, vulnérabilités et violations.

Supposons, par exemple, que vous souhaitiez comparer des applications CRM dans le but de vérifier qu’elles sont suffisamment sécurisées. Vous pouvez utiliser la page du catalogue d’applications cloud pour afficher uniquement les applications que vous souhaitez :

1. Dans la page **Catalogue d’applications cloud**, sous **Parcourir par catégorie**, sélectionnez **CRM**. 
2. Dans les filtres **Avancés**, définissez le **Facteur de risque de conformité** de **SOC 2** sur **True**.
3. Définissez le **Facteur de risque de conformité** de **ISO 27001** sur **True**.
4. Sélectionnez **Facteur de risque de sécurité** pour que le **Chiffrement des données au repos** ne soit pas égal à **Non pris en charge** ou à **N/A**.
5. Définissez le **Facteur de risque de sécurité** du **Suivi d’audit administratif** sur **True**.
6. Définissez le **Facteur de risque de sécurité** du **Suivi d’audit d’utilisateur** sur **True**.

![Filtres du catalogue d’applications cloud](./media/cloud-app-catalog-filters.png)

Une fois que les résultats sont filtrés, vous pouvez passer en revue les applications qui vous intéressent et rechercher celle qui répond le mieux à vos besoins.

## <a name="cloud-app-catalog-filters"></a>Filtres du catalogue d’applications cloud

Le catalogue d’applications cloud contient des filtres de base et avancés. Pour créer un filtre complexe, utilisez l’option avancée qui inclut tous les filtres suivants :

- **Balises d’application** : Les balises vous permettent de personnaliser le catalogue d’applications cloud. 
  Vous avez le choix entre **Approuvée**, **Non approuvée** ou créer vos propres étiquettes personnalisées pour les applications. Ces étiquettes peuvent ensuite servir de filtres. Les filtres permettent de rechercher plus précisément les types d’applications que vous voulez étudier. 
- **Applications et domaines** : Ils vous permettent de rechercher des applications spécifiques ou des applications utilisées dans des domaines spécifiques. 
- **Catégories** : Le filtre de catégories, qui se trouve à gauche de la page, vous permet de rechercher des types d’applications selon des catégories d’applications. Par exemple, les applications de réseaux sociaux, les applications de stockage cloud, etc. Vous pouvez sélectionner plusieurs catégories à la fois. Ensuite, appliquez les filtres de base ou avancés aux catégories.
- **Facteur de risque de conformité** : Il vous permet de rechercher une norme, une certification ou une conformité auxquelles l’application doit se conformer. Par exemple, les normes HIPAA, ISO 27001, SOC 2 ou PCI-DSS.
- **Facteur de risque général** : Il vous permet de rechercher des facteurs de risque généraux, comme la popularité auprès des consommateurs, les paramètres régionaux du centre de données, etc.
- **Facteur de risque juridique** : Il vous permet de filtrer les réglementations et les stratégies qui sont en place. L’utilisation des facteurs de risque juridique permet de garantir la protection et la confidentialité des données des utilisateurs de l’application (par exemple, le RGPD, le DMCA ou la stratégie de conservation des données).
- **Indice de risque** : Il vous permet de filtrer les applications selon l’indice de risque qui leur est associé. Par exemple, vous pouvez examiner uniquement les applications à risque.
- **Facteur de risque de sécurité** : Il vous permet de filtrer les applications en fonction des mesures de sécurité qui leur sont appliquées. Il peut s’agir du chiffrement des données au repos, de l’authentification multifacteur, etc.

## <a name="suggesting-a-change"></a>Proposition de changement

Si vous trouvez une nouvelle application dans votre environnement qui n’a pas été évaluée par Cloud App Security, vous pouvez demander une révision de cette application. Vous pouvez également demander une révision en cas de nouveau facteur de risque, de mise à jour de l’indice de risque ou de données d’application obsolètes.

**Pour suggérer une nouvelle application :**

1. En haut de la page **Applications découvertes**, cliquez sur les points de suspension, puis sélectionnez **Suggérer une nouvelle application**.

   ![Suggérer une application à Cloud App Security](./media/suggest-new-app.png)

2. Dans la fenêtre contextuelle **Suggérer une nouvelle application cloud**, entrez les informations concernant la nouvelle application. Mentionnez le nom et le domaine de l’application.

   ![Fenêtre contextuelle Suggérer une application à Cloud App Security](./media/suggest-new-app-popup.png)

3. Nous vous recommandons de cocher la case qui permet aux analystes Cloud App Security de vous contacter au cas où des informations supplémentaires seraient nécessaires. Renseignez également vos coordonnées pour que nous puissions vous informer lorsque l’analyse sera terminée.

**Pour mettre à jour un facteur de risque, un score ou des données d’application :**

1. Dans la page **Catalogue d’applications cloud**, sur la ligne de l’application que vous voulez mettre à jour, cliquez sur les points de suspension à la fin de la ligne et sélectionnez **Demander une mise à jour du score**.

   ![Demander une mise à jour du score](./media/request-score-update.png)

2. Dans la fenêtre contextuelle **Suggérer une amélioration**, indiquez si vous voulez demander une mise à jour de score, suggérer un nouveau facteur de risque ou mettre à jour des données d’application.

   ![suggérer une amélioration à Cloud App Security](./media/suggest-improvement-popup.png)

3. Nous vous recommandons de cocher la case qui permet aux analystes Cloud App Security de vous contacter au cas où des informations supplémentaires seraient nécessaires. Renseignez également vos coordonnées pour que nous puissions vous informer lorsque l’analyse sera terminée.
 
## <a name="customizing-the-risk-score"></a>Personnalisation de l’indice de risque

Cloud Discovery vous fournit des données importantes sur la crédibilité et la fiabilité des applications cloud qui sont utilisées au sein de l’environnement. Dans le portail, chaque application découverte est présentée avec un score total. Ce score représente le niveau de maturité qui a été obtenu par cette application après son évaluation par Cloud App Security, en vue de son utilisation en entreprise. Le score total d’une application donnée est une moyenne pondérée de trois sous-scores liés à trois sous-catégories que Cloud App Security prend en compte pour évaluer la fiabilité :  
  
- **Général** : Cette catégorie fait référence à des informations basiques sur la société qui produit l’application, notamment son domaine, l’année de sa fondation et sa popularité. Ces champs ont vocation à illustrer la stabilité de la société au niveau le plus simple.  
  
- **Sécurité** : la catégorie Sécurité tient compte de toutes les normes liées à la sécurité physique des données utilisées par l’application découverte. Cette catégorie comprend des champs tels que l’authentification multifacteur, le chiffrement, la classification des données et la propriété des données.  
  
- **Conformité** : Cette catégorie présente les normes de conformité issues des bonnes pratiques en usage que la société qui produit l’application respecte. La liste des spécifications inclut des normes telles que HIPAA, CSA et PCI-DSS.  

- **Légal** : Cette catégorie représente les applications avec des réglementations et des stratégies en place pour garantir la protection et la confidentialité des données des utilisateurs de l’application, comme la stratégie de conservation des données, le RGPD et le DMCA.
  
Chacune de ces catégories comprend de nombreuses propriétés spécifiques. Selon notre algorithme de scoring Cloud App Security, chaque propriété reçoit un score préliminaire compris entre 0 et 10, selon sa valeur. Les valeurs True/False reçoivent 10 ou 0. Cependant, les propriétés continues, telles que l’âge du domaine, reçoivent une valeur comprise dans le spectre. Le score de chaque propriété est pondéré par rapport à tous les autres champs existants dans la catégorie, afin de créer le sous-score de la catégorie. Si vous rencontrez une application sans score, cela indique généralement que les propriétés de cette application sont inconnues et qu’elle n’a donc pas de score.  
  
Prenez le temps de passer en revue et d’éventuellement modifier les pondérations qui ont été attribuées par défaut à la configuration du score Cloud Discovery. Par défaut, tous les différents paramètres évalués reçoivent une pondération identique. Si certains paramètres sont plus ou moins importants pour votre organisation, il est important de les modifier comme suit :  
  
1. Dans le portail, sous l’icône Paramètres, sélectionnez **Paramètres Cloud Discovery**.  
  
2. Sous **Métrique du score**, faites glisser le curseur **Importance** pour modifier la pondération du champ ou la catégorie de risque. L’importance peut être définie sur **Ignoré**, **Bas**, **Moyen**, **Élevé** ou **Très élevé**.  
  
3. De plus, vous pouvez déterminer si certaines valeurs sont soit non disponibles, soit non applicables dans le calcul du score. Quand elles sont incluses, les valeurs N/A contribuent négativement au score calculé.  
  
   ![score](./media/score.png "métriques de score")  

Toutes les informations nécessaires pour comprendre le fonctionnement des indices de risque Cloud App Security et leur empilement sont disponibles dans le portail Cloud App Security. Pour mieux comprendre la pondération d’un facteur de risque dans une catégorie donnée, utilisez le bouton « i » à droite d’un nom de champ, dans le profil de l’application. Il fournit des informations sur la façon dont Cloud App Security note précisément un facteur de risque. Ce score correspond à la valeur du facteur de risque sur une échelle de 1 à 10 et à son poids dans la catégorie de risque :

![calcul du risque](./media/cac-weight.png)
  
Pour comprendre la pondération d’une catégorie de risque dans le score total d’une application, déplacez le curseur sur le score de catégorie de risque :

![poids de la catégorie de risque](./media/risk-category-weight.png)

## <a name="overriding-the-risk-score"></a>Remplacement du score de risque


Pour remplacer l’indice de risque, dans le tableau **Applications découvertes** ou dans le **Catalogue d’applications cloud**, cliquez sur les points de suspension à droite d’une application, puis sélectionnez **Remplacer le score de l’application**.
Vous pouvez remplacer l’indice de risque d’une application sans changer la façon dont elle est pondérée, afin d’obtenir des résultats immédiats pour votre organisation. Mettons, par exemple, que l’indice de risque d’une application métier que vous utilisez soit de 8. Pourtant, l’application est approuvée par votre organisation, qui encourage même son utilisation. Dans ce cas, il est souhaitable d’attribuer un indice de risque de 10 à votre application métier.
![Remplacer l’indice de risque d’une application dans Cloud App Security](./media/override-risk-score.png)

Une fois que vous avez mis à jour le score, vous pouvez ajouter des notes d’application pour justifier le changement du score de l’application aux autres administrateurs. 

Vous pouvez également ajouter des notes pour clarifier la justification du changement quand une personne examine l’application.


 
## <a name="next-steps"></a>Étapes suivantes
 
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)  
  
  