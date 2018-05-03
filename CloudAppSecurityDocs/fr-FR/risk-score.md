---
title: Utilisation du score de risque | Microsoft Docs
description: Cette rubrique fournit des instructions sur l’utilisation et la personnalisation du score de risque Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 9cb3594e-5007-48be-9b4f-e1d23355d86e
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 863801bab42b957af98541da326d9b7ec6c69ccc
ms.sourcegitcommit: 45311f2cafef79483e40d971a4c61c7673834d96
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2018
---
*S’applique à : Microsoft Cloud App Security*


# <a name="working-with-the-risk-score"></a>Utilisation du score de risque  

## <a name="the-cloud-app-catalog"></a>Catalogue d’applications cloud

Le catalogue d’applications cloud vous donne une vue d’ensemble complète des éléments identifiés par Cloud Discovery. Cloud Discovery analyse les journaux de votre trafic en se basant sur le catalogue d’applications cloud de Microsoft Cloud App Security, qui contient plus de 15 000 applications cloud classées et évaluées selon plus de 60 facteurs de risque, afin de vous offrir une visibilité en continu de l’utilisation du cloud, du Shadow IT et du risque qu’il représente pour votre organisation.
Le **catalogue d’applications cloud** évalue les risques pour vos applications cloud selon les certifications réglementaires, les normes du secteur et les bonnes pratiques. Quatre processus complémentaires s’exécutent dans le catalogue d’applications cloud pour le tenir à jour :
1.  Extraction de données automatisée directement à partir de l’application cloud (pour les attributs tels que la conformité SOC 2, les termes du contrat de service, l’URL d’ouverture de session, la politique de confidentialité et l’emplacement du siège social).
2.  Extraction de données avancée automatisée pour les données par les algorithmes de Cloud App Security (pour les attributs tels que les en-têtes de sécurité HTTP).
3.  Analyse en continu par l’équipe d’analystes cloud Cloud App Security (pour les attributs tels que le chiffrement au repos).
4.  Demandes de révisions basées sur le client, en fonction des demandes de soumissions du client des modifications à apporter au catalogue d’applications cloud. Toutes les demandes sont examinées par notre équipe d’analystes cloud et mises à jour en fonction de leurs conclusions.
  
![Catalogue d’applications cloud](./media/cloud-app-catalog.png)  

Les divisions sont de plus en plus à la recherche d’applications cloud pour répondre à leurs besoins changeants. Le catalogue d’applications cloud vous permet de choisir judicieusement les applications compatibles avec les critères de sécurité de votre organisation et vous permet de vous tenir informé des dernières normes de sécurité, vulnérabilités et violations. Par exemple, si vous voulez comparer des applications CRM et vérifier qu’elles sont suffisamment sécurisées, vous pouvez utiliser la page du catalogue d’applications cloud pour filtrer les applications appropriées de votre choix : dans la page **Catalogue d’applications cloud**, sous **Parcourir par catégorie**, sélectionnez les deux **CRM**. 

Ensuite, utilisez les filtres **Avancés** et définissez **Facteur de risque de conformité** > **SOC 2** égal à **True** ; **Facteur de risque de conformité** > **ISO 27001** égal à **True** ; **Facteur de risque de sécurité** > **Chiffrement de données au repos** égal à **True** ; **Facteur de risque de sécurité** > **Chiffrement de données au repos** égal à **True** ; **Facteur de risque de sécurité** > **Suivi d’audit administratif** égal à **True** et **Facteur de risque de sécurité** > **Suivi d’audit d’utilisateur** égal à **True**.

![Filtres du catalogue d’applications cloud](./media/cloud-app-catalog-filters.png)

Une fois que les résultats sont filtrés, vous pouvez passer en revue les applications qui vous intéressent et rechercher celle qui répond le mieux à vos besoins.

## <a name="cloud-app-catalog-filters"></a>Filtres du catalogue d’applications cloud

Le catalogue d’applications cloud contient des filtres de base et avancés. Pour obtenir un filtre complexe, utilisez l’option avancée qui inclut tous les éléments suivants :

- **Balises d’application** : Les balises vous permettent de personnaliser le catalogue d’applications cloud. 
  Vous avez le choix entre **Approuvée**, **Non approuvée** ou vous pouvez créer des balises personnalisées pour les applications. Ces balises peuvent ensuite servir de filtres pour rechercher plus précisément des types spécifiques d’applications que vous voulez examiner. 
- **Applications et domaines** : Permet de rechercher des applications spécifiques ou des applications utilisées dans des domaines spécifiques. 
- **Catégories** : Le filtre de catégories, qui se trouve à gauche de la page, vous permet de rechercher des types d’applications selon des catégories d’applications, par exemple, des applications de réseau social, des applications de stockage cloud, etc. Vous pouvez sélectionner plusieurs catégories à la fois, ou une seule catégorie, puis leur appliquer des filtres de base et avancés.
- **Facteur de risque de conformité** : Permet de rechercher des normes, certifications et conformités spécifiques auxquelles l’application doit se conformer (HIPAA, ISO 27001, SOC 2, PCI-DSS, etc.).
- **Facteur de risque général** : Permet de rechercher des facteurs de risque général comme la popularité auprès des consommateurs, les paramètres régionaux du centre de données, etc.
- **Score de risque** : Permet de filtrer les applications par score de risque pour que vous puissiez vous concentrer uniquement sur les applications très risquées, par exemple.
- **Facteur de risque de sécurité** : Permet de filtrer en fonction de mesures de sécurité spécifiques (comme le chiffrement au repos, l’authentification multifacteur, etc.).

## <a name="suggesting-a-change"></a>Proposition de changement

Si vous trouvez une nouvelle application dans votre environnement qui n’a pas été évaluée par Cloud App Security, un nouveau facteur de risque, une mise à jour de score ou des données d’application obsolètes, vous pouvez demander une révision de l’application :

**Pour suggérer une nouvelle application :**
1. En haut de la page **Applications découvertes**, cliquez sur les points de suspension, puis sélectionnez **Suggérer une nouvelle application**. 

   ![Suggérer une application à Cloud App Security](./media/suggest-new-app.png)

2. Dans la fenêtre contextuelle **Suggérer une nouvelle application cloud**, renseignez les détails sur la nouvelle application, notamment le nom et le domaine de l’application. 

   ![Fenêtre contextuelle Suggérer une application à Cloud App Security](./media/suggest-new-app-popup.png)

3. Nous vous recommandons de cocher la case qui permet aux analystes Cloud App Security de vous contacter au cas où des informations supplémentaires sur l’application seraient nécessaires, et pour que vous soyez tenu informé à la fin de l’analyse.

**Pour mettre à jour un facteur de risque, un score ou des données d’application :**

1. Dans la page **Catalogue d’applications cloud**, sur la ligne de l’application que vous voulez mettre à jour, cliquez sur les points de suspension à la fin de la ligne et sélectionnez **Demander une mise à jour du score**.

   ![Demander une mise à jour du score](./media/request-score-update.png)

2. Dans la fenêtre contextuelle **Suggérer une amélioration**, indiquez si vous voulez demander une mise à jour de score, suggérer un nouveau facteur de risque ou mettre à jour des données d’application.

   ![suggérer une amélioration à Cloud App Security](./media/suggest-improvement-popup.png)

3. Nous vous recommandons de cocher la case qui permet aux analystes Cloud App Security de vous contacter au cas où des informations supplémentaires sur l’application seraient nécessaires, et pour que vous soyez tenu informé à la fin de l’analyse.
 


## <a name="customizing-the-risk-score"></a>Personnalisation de l’indice de risque

Cloud Discovery vous fournit des données importantes sur la crédibilité et la fiabilité des applications cloud qui sont utilisées au sein de l’environnement. Dans le portail, chaque application découverte est présentée avec un score total, qui représente l’évaluation par Cloud App Security du niveau de maturité de l’utilisation par les entreprises de cette application particulière. Le score total d’une application donnée est une moyenne pondérée de trois sous-scores liés à trois sous-catégories que Cloud App Security prend en compte pour évaluer la fiabilité :  
  
-   **Général** : Cette catégorie fait référence à des informations basiques sur la société qui produit l’application, notamment son domaine, l’année de sa fondation et sa popularité. Ces champs ont vocation à illustrer la stabilité de la société au niveau le plus simple.  
  
-   **Sécurité** : La catégorie Sécurité tient compte de toutes les normes liées à la sécurité physique des données utilisées par l’application découverte. Sont inclus des champs tels que l’authentification multifacteur, le chiffrement, la classification des données et la propriété des données.  
  
-   **Conformité** : Cette catégorie présente les normes de conformité issues des bonnes pratiques en usage que la société qui produit l’application respecte. La liste des spécifications inclut des normes telles que HIPAA, CSA et PCI-DSS.  
  
Chacune de ces catégories comprend de nombreuses propriétés spécifiques. Selon notre algorithme de scoring Cloud App Security, chaque propriété reçoit un score préliminaire compris entre 0 et 10, selon sa valeur. Les valeurs True/False reçoivent 10 ou 0 en conséquence, tandis que les propriétés continues telles que l’âge du domaine reçoivent une certaine valeur comprise dans le spectre. Le score de chaque propriété est pondéré par rapport à tous les autres champs existants dans la catégorie, pour créer le sous-score de la catégorie. Si vous rencontrez une application sans score, cela indique généralement que les propriétés de cette application sont inconnues et qu’elle n’a donc pas de score.  
  
Prenez le temps de passer en revue et modifier les pondérations par défaut données à la configuration du score Cloud Discovery. Par défaut, tous les différents paramètres évalués reçoivent une pondération identique. Si certains paramètres sont plus ou moins importants pour votre organisation, il est important de les modifier comme suit :  
  
1. Dans le portail, sous l’icône Paramètres, sélectionnez **Paramètres Cloud Discovery**.  
  
2. Sous **Configurer la métrique du score**, faites glisser le curseur **Importance** pour modifier la pondération du champ ou la catégorie de risque. Vous avez le choix entre les options **Ignoré**, **Bas**, **Moyen**, **Élevé** ou **Très élevé**.  
  
3. De plus, vous pouvez déterminer si certaines valeurs sont soit non disponibles, soit non applicables dans le calcul du score. Quand elles sont incluses, les valeurs N/A contribuent négativement au score calculé.  
  
   ![score](./media/score.png "score")  

Toutes les informations nécessaires pour comprendre le fonctionnement des indices de risque Cloud App Security et leur empilement sont disponibles dans le portail Cloud App Security.
Pour mieux comprendre le poids d’un facteur de risque dans une catégorie donnée, utilisez le bouton « i » à droite d’un nom de champ dans le profil de l’application. Il fournit des informations sur la façon dont Cloud App Security note précisément un facteur de risque. Ce score correspond à la valeur du facteur de risque sur une échelle de 1 à 10 et à son poids dans la catégorie de risque :

![calcul du risque](./media/cac-weight.png)
  
Pour comprendre le poids d’une catégorie de risque dans le score total d’une application, déplacez le curseur sur le score de catégorie de risque :

![poids de la catégorie de risque](./media/risk-category-weight.png)

## <a name="overriding-the-risk-score"></a>Remplacement du score de risque
Vous pouvez remplacer le score de risque d’une application sans changer la façon dont elle est pondérée afin d’obtenir des résultats immédiats pour votre organisation. Par exemple, si le score de risque d’une application métier que vous utilisez est 8 et qu’elle est approuvée et proposée par votre organisation, vous pouvez remplacer le score de risque par 10. 

Pour remplacer le score de risque, dans le tableau **Applications découvertes** ou dans le **Catalogue d’applications cloud**, cliquez sur les points de suspension à droite d’une application et sélectionnez **Remplacer le score de risque**.

![remplacer le score de risque d’une application découverte dans cloud app security](./media/override-risk-score.png)

Une fois que vous avez mis à jour le score, vous pouvez ajouter des notes d’application pour justifier le changement du score de l’application aux autres administrateurs. 

Vous pouvez également ajouter des notes pour clarifier la justification du changement quand une personne examine l’application.


 
## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  