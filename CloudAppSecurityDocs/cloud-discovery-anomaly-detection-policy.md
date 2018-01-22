---
title: "Créer une stratégie de détection des anomalies Cloud Discovery | Microsoft Docs"
description: "Cette rubrique fournit des informations sur l’utilisation des stratégies de détection des anomalies Cloud Discovery."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/15/2018
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: eaf73af0-7610-4903-b656-8d90b1d2b18c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 408b136764fd5e16f47772fb73ff6588d9b5bc8e
ms.sourcegitcommit: 458e936e1ac548eda37e9bf955b439199bbdd018
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2018
---
# <a name="cloud-discovery-anomaly-detection-policy"></a>Stratégie de détection des anomalies de Cloud Discovery
Cet article fournit des informations de référence sur les stratégies, donne une explication de chaque type de stratégie et décrit les champs que vous pouvez configurer pour chacune d’elle.  
  
## <a name="cloud-discovery-anomaly-detection-policy-reference"></a>Informations de référence sur les stratégies de détection d’anomalies de Cloud Discovery  
Une stratégie de détection d’anomalie de Cloud Discovery vous permet de configurer une surveillance permanente des augmentations inhabituelles de l’utilisation des applications cloud. Pour chaque application cloud sont considérées les augmentations de données téléchargées, de données chargées, du nombre de transactions et du nombre d’utilisateurs. Chaque augmentation est comparée au modèle d’utilisation normale de l’application déterminé à partir de son utilisation antérieure. Les augmentations les plus extrêmes déclenchent des alertes de sécurité.  
  
Pour chaque stratégie, vous pouvez définir des filtres qui vous permettent de surveiller de façon sélective l’utilisation des applications, selon un filtre d’application, des vues de données sélectionnées et une date de début sélectionnée. Vous pouvez aussi définir la sensibilité, qui vous permet de définir le nombre d’alertes que la stratégie doit déclencher.  

Pour chaque stratégie, définissez les paramètres suivants :

1. Décidez si vous voulez baser la stratégie sur un modèle. Le modèle de stratégie approprié est le modèle **Comportement anormal dans les utilisateurs découverts**, qui alerte quand un comportement anormal est détecté dans des utilisateurs et des applications découverts, comme de grandes quantités de données chargées par rapport à d’autres utilisateurs ou des transactions utilisateur importantes par rapport à l’historique de l’utilisateur. Vous pouvez également sélectionner le modèle **Comportement anormal des adresses IP découvertes**, qui alerte quand un comportement anormal est détecté dans les adresses IP et les applications détectées, comme de grandes quantités de données chargées par rapport à d’autres adresses IP ou des transactions d’application importantes par rapport à l’historique de l’adresse IP. 
 
2. Spécifiez un **Nom de stratégie** et une **Description**.  

3. Créez un filtre pour les applications que vous voulez surveiller en cliquant sur **Ajouter un filtre**. Vous pouvez sélectionner une application spécifique, une **Catégorie** d’applications ou filtrer par **Nom**, par **Domaine et par **Facteur de risque**, et cliquer sur **Enregistrer**.

4. Sous **Appliquer à**, définissez comment vous voulez que l’utilisation soit filtrée. L’utilisation en cours de surveillance peut être filtrée de deux manières différentes :  
  
    -   Rapports continus : choisissez si vous voulez surveiller **Tous les rapports continus** (par défaut) ou des **Rapports continus spécifiques**.  
  
        -   Quand vous sélectionnez **Tous les rapports continus**, chaque accroissement de l’utilisation est comparé au modèle d’utilisation normale, telle qu’elle est déterminée à partir de toutes les vues de données.  
  
        -   Quand vous sélectionnez des **Rapports continus spécifiques**, chaque accroissement de l’utilisation est comparé au modèle d’utilisation normale déterminé à partir de la même vue de données que celle où l’accroissement a été observé.  
  
    -   **Utilisateurs et adresses IP** : chaque utilisation d’application cloud est associée à un utilisateur, à une adresse IP ou aux deux.  
  
        -   La sélection de l’option **Utilisateurs** permet d’ignorer l’association de l’utilisation d’application à des adresses IP, le cas échéant.  
  
        -   La sélection de l’option **Adresses IP** permet d’ignorer l’association de l’utilisation d’application aux utilisateurs, le cas échéant.  
  
        -   La sélection de l’option **Utilisateurs et adresses IP** (part défaut) prend en compte les deux associations, mais elle peut produire des alertes en doublon quand une correspondance étroite existe entre les utilisateurs et les adresses IP.
    -   Déclencher des alertes seulement pour les activités suspectes après la date : tout accroissement de l’utilisation de l’application avant la date sélectionnée est ignorée. Toutefois, les activités avant la date sélectionnée sont prises en compte pour établir le modèle d’utilisation normale.  
  
5. Sous **Alertes**, vous pouvez définir la sensibilité des alertes. Il existe plusieurs façons de contrôler le nombre d’alertes déclenchées par la stratégie :  
  
    -   Curseur **Sélectionnez la sensibilité de la détection d’anomalies** : déclenche des alertes pour les X activités anormales les plus fréquentes par 1 000 utilisateurs par semaine. Les alertes sont déclenchées pour les activités dont le risque est le plus élevé.  
  
    -   **Limite d’alerte quotidienne** : limitez le nombre d’alertes générées sur une même journée. Vous pouvez choisir s’il faut **Envoyer l’alerte par e-mail**, **Envoyer l’alerte par SMS** ou les deux. Les messages envoyés par SMS sont limités à 10 par jour pour le fuseau horaire UTC, ce qui signifie que la limite de 10 messages est réinitialisée à minuit dans le fuseau horaire UTC.

    - Vous pouvez également choisir d’**Utiliser les paramètres par défaut de votre organisation**, qui affecte des valeurs aux paramètres de **Limite quotidienne d’alertes**, d’e-mail et de SMS à partir des paramètres par défaut de votre organisation. Pour définir la valeur par défaut, complétez la **Configuration des alertes**, puis cliquez sur **Enregistrer ces paramètres d’alerte comme valeurs par défaut pour votre organisation**.

6. Cliquez sur **Créer**.

7. Comme avec toutes les stratégies, vous pouvez **Modifier**, **Désactiver** et **Activer** la stratégie en cliquant sur les trois points à la fin de la ligne dans la page **Stratégies**. Par défaut, quand vous créez une stratégie, celle-ci est activée.

## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  