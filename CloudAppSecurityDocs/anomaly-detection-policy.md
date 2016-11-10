---
title: "Stratégie de détection des anomalies | Documentation Microsoft"
description: "Cette rubrique fournit une description des stratégies de détection des anomalies ainsi que des informations de référence sur les blocs de construction d’une stratégie de détection des anomalies."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/6/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: ab9bc377-d2f5-4f4c-a419-f1728a15d1c7
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: bd612cfcecae2eb9c5a81d59250585fb9f4adb01


---

# <a name="anomaly-detection-policy"></a>Stratégie de détection d’anomalie
Cet article fournit des informations de référence sur les stratégies, donne une explication de chaque type de stratégie et décrit les champs que vous pouvez configurer pour chacune d’elle.  
 
Cloud App Security passe par une période d’apprentissage initiale de 7 jours au cours de laquelle il ne signale pas les nouveaux utilisateurs, activités, appareils ni emplacements comme anormaux. Après cela, chaque session est comparée aux activités (activité des utilisateurs, adresses IP, appareils, etc.) détectées au cours du mois passé et à l’indice de risque de ces activités. Utilisez le curseur de sensibilité de la stratégie pour définir l’indice de risque minimal à partir duquel les alertes seront déclenchées. Quand vous créez une stratégie de détection d’anomalie, il est recommandé d’utiliser le seuil de sensibilité par défaut pendant une semaine avant de le modifier selon le nombre d’alertes reçues ; Cloud App Security vous envoie plus ou moins d’alertes pour les différents indices de risque quand vous modifiez le niveau de sensibilité.
  
![curseur de sensibilité](./media/sensitivity-slider.png)
## <a name="anomaly-detection-policy-reference"></a>Informations de référence sur les stratégies de détection d’anomalie  
Une stratégie de détection d’anomalie vous permet d’installer et de configurer une surveillance continue de l’activité des utilisateurs afin de détecter d’éventuelles anomalies de comportement. Ces anomalies sont détectées en analysant l’activité des utilisateurs. Le risque est évalué en examinant plus de 30 indicateurs de risque différents, regroupés en 6 facteurs de risque. Selon les résultats de la stratégie, des alertes de sécurité sont déclenchées.   
Chaque stratégie comprend les éléments suivants :  
  
-   Filtres d’activité : Vous permettent d’analyser de manière sélective uniquement l’activité filtrée des utilisateurs afin de détecter d’éventuelles anomalies.  
  
-   Facteurs de risque : Vous permettent de choisir les facteurs de risque à inclure lors de l’évaluation des risques.  
  
-   Sensibilité : Vous permet de définir le nombre d’alertes que la stratégie doit déclencher.  
  
### <a name="activity-filters"></a>Filtres d’activité  
Pour obtenir une liste des filtres d’activité, voir [enter link description here](activity-filters.md) (Entrer la description du lien ici).  
  
### <a name="risk-factors"></a>Facteurs de risque  
Voici la liste des facteurs de risque pris en compte lors de l’évaluation du risque lié à l’activité des utilisateurs. Chaque facteur de risque peut être activé ou désactivé. Pour chaque facteur de risque, il existe deux options sous le champ **Appliquer à**, qui déterminent leur inclusion ou exclusion lors de l’évaluation du risque lié à l’activité des utilisateurs :  
  
-   Toutes les activités surveillées : Incluez le facteur de risque pour toutes les activités des utilisateurs qui passent le filtre d’activité de stratégie.  
  
-   Activité sélectionnée : Incluez le facteur de risque pour les activités des utilisateurs qui passent à la fois les filtres d’activité de stratégie et les filtres d’activité qui s’affichent sous ce facteur de risque. Lorsque cette option est sélectionnée, un sélecteur de filtre d’activité apparaît sous le facteur de risque, lequel fonctionne exactement comme le filtre d’activité de stratégie.  
  
Chaque facteur de risque, s’il est inclus dans l’évaluation des risques, a ses propres déclencheurs qui entraînent une augmentation du risque évalué lié à l’activité des utilisateurs :  
  
-   Échecs de connexion : Nombre élevé d’échecs de connexion ou activité entièrement composée d’échecs de connexion.  
  
-   Activité administrative : Activité administrative effectuée par un utilisateur inattendu, ou à partir d’une adresse IP, d’un fournisseur de services Internet ou d’un emplacement qui sont nouveaux ou non utilisés par d’autres utilisateurs de l’organisation.  
  
-   Comptes inactifs : Activité effectuée par un utilisateur qui n’a pas été actif depuis un long moment.  
  
-   Emplacement : Activité effectuée à partir d’une adresse IP, d’un fournisseur de services Internet ou d’un emplacement qui n’ont jamais été utilisés par un autre utilisateur, jamais été utilisés par cet utilisateur particulier, jamais été utilisés du tout ou utilisés uniquement pour des échecs de connexion par le passé.  
  
-   Voyage impossible : Activité à partir d’emplacements distants pendant un laps de temps court.  
  
-   Agent Appareil et utilisateur : Activité effectuée par un utilisateur à l’aide d’un agent utilisateur ou d’un appareil qui n’ont jamais été utilisés par un autre utilisateur, jamais été utilisés par cet utilisateur particulier ou jamais été utilisés du tout.  
  
### <a name="sensitivity"></a>Sensibilité  
Il existe deux façons de contrôler le nombre d’alertes déclenchées par la stratégie :  
  
-   Curseur Sensibilité : Choisissez le nombre d’alertes à déclencher pour 1 000 utilisateurs par semaine. Les alertes liées aux activités dont le risque est le plus élevé sont déclenchées.  
  
-   Limite d’alerte quotidienne : Restreignez le nombre d’alertes générées sur une journée.  
  
## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  



<!--HONumber=Oct16_HO4-->


