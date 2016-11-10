---
title: "Stratégie de détection des anomalies Cloud Discovery | Documentation Microsoft"
description: "Cette rubrique fournit des informations sur l’utilisation des stratégies de détection des anomalies Cloud Discovery."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: eaf73af0-7610-4903-b656-8d90b1d2b18c
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: 481ca3d68e5e7aea006eeff443ec521a374e6e11


---

# <a name="cloud-discovery-anomaly-detection-policy"></a>Stratégie de détection des anomalies de Cloud Discovery
Cet article fournit des informations de référence sur les stratégies, donne une explication de chaque type de stratégie et décrit les champs que vous pouvez configurer pour chacune d’elle.  
  
## <a name="cloud-discovery-anomaly-detection-policy-reference"></a>Informations de référence sur les stratégies de détection d’anomalies de Cloud Discovery  
Une stratégie de détection d’anomalie de Cloud Discovery vous permet de configurer une surveillance permanente des augmentations inhabituelles de l’utilisation des applications cloud. Pour chaque application cloud sont considérées les augmentations de données téléchargées, de données chargées, du nombre de transactions et du nombre d’utilisateurs. Chaque augmentation est comparée au modèle d’utilisation normale de l’application déterminé à partir de son utilisation antérieure. Les augmentations les plus extrêmes déclenchent des alertes de sécurité.  
  
Chaque stratégie comprend les éléments suivants :  
  
-   Filtres : Vous permettent de surveiller de manière sélective l’utilisation des applications, selon un filtre d’application, des vues de données sélectionnées et une date de début sélectionnée.  
  
-   Sensibilité : Vous permet de définir le nombre d’alertes que la stratégie doit déclencher.  
  
### <a name="activity-filters"></a>Filtres d’activité  
Pour obtenir la liste des filtres d’activité, consultez [Filtres d’activité](activity-filters.md).  
  
### <a name="apply-to"></a>Appliquer à  
L’utilisation en cours de surveillance peut être filtrée de deux manières différentes :  
  
-   Vues de données : Indiquez si vous voulez surveiller toutes les vues de données (par défaut) ou choisir des vues de données spécifiques à surveiller.  
  
    -   Quand vous sélectionnez **Toutes les vues de données**, chaque augmentation d’utilisation est comparée au modèle d’utilisation normale déterminé à partir de toutes les vues de données.  
  
    -   Quand vous sélectionnez des vues de données spécifiques, chaque augmentation d’utilisation est comparée au modèle d’utilisation normale déterminé à partir de la même vue de données que celle dans laquelle l’augmentation a été observée.  
  
-   Utilisateurs et adresses IP : Chaque utilisation d’application cloud est associée à un utilisateur, une adresse IP ou les deux.  
  
    -   La sélection de l’option **Utilisateurs** permet d’ignorer l’association de l’utilisation d’application à des adresses IP, le cas échéant.  
  
    -   La sélection de l’option **Adresses IP** permet d’ignorer l’association de l’utilisation d’application aux utilisateurs, le cas échéant.  
  
    -   La sélection de l’option **Utilisateurs et adresses IP** permet de tenir compte des deux associations, mais peut produire des alertes en double quand une correspondance étroite existe entre les utilisateurs et les adresses IP.  
  
Générer des alertes uniquement en cas d’activités suspectes après la date : Toute augmentation d’utilisation d’application est ignorée avant la date sélectionnée. Toutefois, les activités avant la date sélectionnée sont prises en compte pour établir le modèle d’utilisation normale.  
  
### <a name="sensitivity"></a>Sensibilité  
Il existe deux façons de contrôler le nombre d’alertes déclenchées par la stratégie :  
  
-   Curseur Sensibilité : Choisissez le nombre d’alertes à déclencher pour 1 000 utilisateurs par semaine. Les alertes liées aux activités dont le risque est le plus élevé sont déclenchées.  
  
-   Limite d’alerte quotidienne : Restreignez le nombre d’alertes générées sur une journée.  
  
## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO4-->


