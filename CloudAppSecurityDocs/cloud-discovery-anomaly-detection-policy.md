---
title: Créer une stratégie de détection des anomalies Cloud Discovery dans Cloud App Security
description: Cette rubrique fournit des informations sur l’utilisation des stratégies de détection des anomalies Cloud Discovery.
ms.date: 12/10/2018
ms.topic: how-to
ms.openlocfilehash: 371f7b53de7f77d4743df39f1957bb1c411ad14c
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96313421"
---
# <a name="cloud-discovery-anomaly-detection-policy"></a>Stratégie de détection des anomalies Cloud Discovery

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Cet article vous fournit des détails de référence sur les stratégies. Les explications relatives à chaque type de stratégie et aux champs que vous pouvez configurer pour chaque stratégie sont listées.

## <a name="cloud-discovery-anomaly-detection-policy-reference"></a>Informations de référence sur les stratégies de détection d’anomalies de Cloud Discovery

Une stratégie de détection d’anomalie de Cloud Discovery vous permet de configurer une surveillance permanente des augmentations inhabituelles de l’utilisation des applications cloud. Les augmentations du nombre de données téléchargées, du nombre de données chargées, du nombre de transactions et du nombre d’utilisateurs sont prises en compte pour chaque application cloud. Chaque augmentation est comparée au modèle d’utilisation normale de l’application déterminé à partir de son utilisation antérieure. Les augmentations les plus extrêmes déclenchent des alertes de sécurité.

Pour chaque stratégie, vous définissez des filtres qui vous permettent de superviser de manière sélective l’utilisation des applications. Les filtres incluent un filtre d’application, des vues de données sélectionnées et une date de début sélectionnée. Vous pouvez aussi définir la sensibilité, qui vous permet de définir le nombre d’alertes que la stratégie doit déclencher.

Pour chaque stratégie, définissez les paramètres suivants :

1. Déterminez si vous souhaitez baser la stratégie sur un modèle. Le modèle **Comportement anormal dans les utilisateurs découverts** est un modèle de stratégie pertinent. Il donne l’alerte quand un comportement anormal est détecté pour des utilisateurs et des applications découverts, par exemple quand de grandes quantités de données sont chargées par rapport à d’autres utilisateurs ou quand un grand nombre de transactions utilisateur sont effectuées par rapport à l’historique de l’utilisateur. Vous pouvez également sélectionner le modèle **Comportement anormal des adresses IP découvertes**. Ce modèle donne l’alerte quand un comportement anormal est détecté dans des adresses IP et des applications découvertes, par exemple quand de grandes quantités de données sont chargées par rapport à d’autres adresses IP ou quand un grand nombre de transactions d’application sont effectuées par rapport à l’historique de l’adresse IP.

2. Spécifiez un **Nom de stratégie** et une **Description**.

3. Créez un filtre pour les applications que vous voulez surveiller en cliquant sur **Ajouter un filtre**.
   Vous pouvez sélectionner une application spécifique, une **catégorie** d’application ou filtrer par **nom**, * * domaine et **facteur de risque**, puis cliquer sur **Enregistrer**.

4. Sous **Appliquer à**, définissez comment vous voulez que l’utilisation soit filtrée. L’utilisation en cours de surveillance peut être filtrée de deux manières différentes :

    - **Rapports continus** : indiquez si vous souhaitez surveiller **tous les rapports continus** (par défaut) ou choisir **des rapports continus spécifiques** à surveiller.

        - Quand vous sélectionnez **Tous les rapports continus**, chaque accroissement de l’utilisation est comparé au modèle d’utilisation normale, telle qu’elle est déterminée à partir de toutes les vues de données.
        - Quand vous sélectionnez **Rapports continus spécifiques**, chaque augmentation de l’utilisation est comparée au modèle d’utilisation normale. Le modèle est déterminé à partir de la même vue de données que celle dans laquelle l’augmentation a été observée.

    - **Utilisateurs et adresses IP** - Chaque utilisation d’application cloud est associée à un utilisateur, à une adresse IP ou aux deux.

        - La sélection de l’option **Utilisateurs** permet d’ignorer l’association de l’utilisation d’application à des adresses IP.

        - La sélection de l’option **Adresses IP** permet d’ignorer l’association de l’utilisation d’application à des utilisateurs.

        - La sélection de l’option **Utilisateurs et adresses IP** (part défaut) prend en compte les deux associations, mais elle peut produire des alertes en doublon quand une correspondance étroite existe entre les utilisateurs et les adresses IP.

    - **Déclencher des alertes uniquement pour les activités suspectes qui se produisent après la date** : toute augmentation de l’utilisation de l’application avant la date sélectionnée est ignorée. Toutefois, les activités avant la date sélectionnée sont prises en compte pour établir le modèle d’utilisation normale.

5. Sous **alertes**, vous pouvez définir la sensibilité des alertes. Il existe plusieurs façons de contrôler le nombre d’alertes déclenchées par la stratégie :

    - Curseur **Sélectionnez la sensibilité de la détection d’anomalies** : déclenche des alertes pour les X activités anormales les plus fréquentes par 1 000 utilisateurs par semaine. Les alertes sont déclenchées pour les activités dont le risque est le plus élevé.

    - **Limite d’alerte quotidienne** : limitez le nombre d’alertes générées sur une même journée. Vous pouvez choisir s’il faut **Envoyer l’alerte par e-mail**, **Envoyer l’alerte par SMS** ou les deux. Les messages envoyés par SMS sont limités à 10 par jour pour le fuseau horaire UTC, ce qui signifie que la limite de 10 messages est réinitialisée à minuit dans le fuseau horaire UTC.

    - Vous pouvez également sélectionner l’option pour **Utiliser les paramètres par défaut de votre organisation**. Cette option permet d’affecter des valeurs aux paramètres de **Limite d’alerte quotidienne**, d’e-mail et de SMS à partir des paramètres par défaut de votre organisation. Pour définir la valeur par défaut, complétez la **Configuration des alertes**, puis cliquez sur **Enregistrer ces paramètres d’alerte comme valeurs par défaut pour votre organisation**.

6. Cliquez sur **Créer**.

7. Comme avec toutes les stratégies, vous pouvez **Modifier**, **Désactiver** et **Activer** la stratégie en cliquant sur les trois points à la fin de la ligne dans la page **Stratégies**. Par défaut, quand vous créez une stratégie, celle-ci est activée.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
