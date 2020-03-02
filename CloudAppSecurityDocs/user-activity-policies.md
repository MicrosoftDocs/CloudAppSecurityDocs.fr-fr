---
title: Créer des stratégies pour contrôler les activités dans Cloud App Security
description: Cet article fournit des instructions sur la création et l’utilisation des stratégies d’activité.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: conceptual
ms.date: 03/01/2020
ms.collection: M365-security-compliance
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 87e25ce39cf7c3858db00af9dbe9d9141de2a48d
ms.sourcegitcommit: 828bbe923713b358fbd32f14e007bf7e5bccedbe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/01/2020
ms.locfileid: "78207901"
---
# <a name="activity-policies"></a>Stratégies des activités

*S’applique à : Microsoft Cloud App Security*

Les stratégies d’activité vous permettent d’appliquer une large gamme de processus automatisés à l’aide des API du fournisseur d’applications. Ces stratégies vous permettent de surveiller des activités spécifiques effectuées par différents utilisateurs ou de suivre les taux inattendus d’un certain type d’activité.

Une fois que vous avez défini une stratégie de détection d’activité, elle commence à générer des alertes-les alertes sont générées uniquement sur les activités qui se produisent après la création de la stratégie.

> [!NOTE]
> Les stratégies qui déclenchent plus de 50 000 correspondances par jour, pour 3 des 7 derniers jours, sont automatiquement désactivées. Vous pouvez essayer d’affiner les stratégies en ajoutant des filtres supplémentaires ou, si vous utilisez des stratégies à des fins de création de rapports, pensez à [les enregistrer en tant que requêtes](activity-filters-queries.md#activity-queries) à la place.

## <a name="custom-alerts"></a>Alertes personnalisées

Les stratégies d’activité permettent d’envoyer des alertes personnalisées ou d’effectuer des actions lorsque l’activité de l’utilisateur est détectée. Par exemple, vous souhaitez connaître à chaque fois :

- Un utilisateur tente de se connecter et échoue 70 fois en une minute
- Un utilisateur télécharge 7 000 fichiers
- Un utilisateur est connecté à partir de l’Afghanistan

Vous pouvez définir des alertes d’activité à envoyer à vous-même ou à l’utilisateur lorsque ces événements se produisent. Vous pouvez même suspendre l’utilisateur jusqu’à ce que vous ayez terminé d’examiner ce qui s’est passé.

Pour créer une stratégie d’activité, procédez comme suit :

1. Dans la console, cliquez sur **contrôle** , puis sur **stratégies**.

2. Cliquez sur **créer une stratégie** et sélectionnez stratégie d' **activité**.

     ![menu stratégie d’activité](media/activity-policy-menu.png)

3. Donnez un nom et une description à votre stratégie. Si vous le souhaitez, vous pouvez la baser sur un modèle. pour plus d’informations sur les modèles de stratégie, consultez [contrôler les applications Cloud avec des stratégies](control-cloud-apps-with-policies.md).

4. Pour définir les actions ou autres mesures qui déclencheront cette stratégie, utilisez les **filtres d’activité**.
    > [!NOTE]
    > Pour vous assurer que vous incluez uniquement les résultats où le champ de filtre spécifié a une valeur, nous vous recommandons d’ajouter à nouveau le même champ à l’aide de l' **ensemble** de tests. Par exemple, lorsque le filtrage par **emplacement** *n’est pas égal* à une liste de pays spécifiée, ajoutez également un filtre pour l' **emplacement** *est défini*. Vous pouvez également afficher un aperçu des résultats du filtre en sélectionnant **modifier et afficher un aperçu des résultats**.
    >
    > ![Capture d’écran des paramètres de filtre, indication du champ d’emplacement défini](media/activity-example-location-isset.png)

5. Sous **paramètres de correspondance**de l’activité, sélectionnez lorsqu’une violation de stratégie est déclenchée. Choisissez un déclenchement quand une seule activité correspond aux filtres ou uniquement lorsqu’un nombre spécifié d' **activités répétées** est détecté.
    - Si vous choisissez **activité répétée**, vous pouvez définir **dans une seule application**. Ce paramètre déclenche une correspondance de stratégie uniquement lorsque les activités répétées se produisent dans la même application. Par exemple, cinq téléchargements dans 30 minutes à partir de Box déclenchent une correspondance de stratégie.

6. Configurez les **actions** qui doivent être effectuées lorsqu’une correspondance est trouvée.

Jetez un coup d’œil à ces exemples :

- Plusieurs échecs de connexion

    Vous pouvez définir une stratégie pour recevoir une alerte lorsqu’un grand nombre de connexions ayant échoué dans un laps de temps réduit se produit. Pour configurer ce type de stratégie, choisissez le filtre d’activité approprié dans la page **nouvelle stratégie d’activité** .

    Sous le champ **filtres d’activité** , configurez les paramètres pour lesquels l’alerte doit être déclenchée.

    ![Exemple de stratégie pour plusieurs tentatives de connexion ayant échoué](media/multiple-failed-log-on-attempts-policy-example.png "exemple de stratégie de tentatives d’ouverture de session multiples ayant échoué")

- Taux de téléchargement élevé

    Vous pouvez définir votre stratégie afin de recevoir une alerte en cas de niveau inattendu ou non caractéristique de l’activité de téléchargement. Pour configurer ce type de stratégie, sous paramètres du **taux** , choisissez les paramètres pour déclencher l’alerte.

    ![exemple de taux de téléchargement élevé](media/high-download-rate-example.png "exemple de taux de téléchargement élevé")

## <a name="activity-policy-reference"></a>Référence de stratégie d’activité

Cette section contient des informations de référence sur les stratégies, des explications pour chaque type de stratégie et les champs qui peuvent être configurés pour chaque stratégie.

Une **stratégie d’activité** est une stratégie basée sur une API qui vous permet de surveiller les activités de votre organisation dans le Cloud. La stratégie prend en compte plus de 20 filtres de métadonnées de fichiers, notamment le type et l’emplacement de l’appareil. En fonction des résultats de la stratégie, des notifications peuvent être générées et les utilisateurs peuvent être suspendus à partir de l’application Cloud.
Chaque stratégie est composée des éléments suivants :

- Filtres d’activité : vous permettent de créer des conditions granulaires basées sur les métadonnées.

- Paramètres de correspondance de l’activité : vous permettent de définir un seuil pour le nombre de fois qu’une activité se répète pour être considérée comme correspondant à la stratégie.  Spécifiez le nombre d’activités répétées requises pour correspondre à la stratégie. Par exemple, définissez une stratégie pour alerter quand un utilisateur a 10 tentatives de connexion ayant échoué dans un laps de temps de 2 minutes. Par défaut, * * le paramètre de correspondance d’activité déclenche une correspondance pour chaque activité unique qui satisfait à tous les filtres d’activité.

  - À l’aide d’une **activité répétée** , vous pouvez définir le nombre d’activités répétées, la durée de l’intervalle de temps pendant lequel les activités sont comptées. Vous pouvez également spécifier que toutes les activités doivent être effectuées par le même utilisateur et dans la même application Cloud.

- Actions : la stratégie fournit un ensemble d’actions de gouvernance qui peuvent être appliquées automatiquement quand des violations sont détectées.

## <a name="next-steps"></a>Étapes suivantes :

> [!div class="nextstepaction"]
> [Stratégies de protection des données](data-protection-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
