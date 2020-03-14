---
title: Créer des stratégies sur des applications Cloud Discoveryes-Cloud App Security | Microsoft Docs
description: Cet article fournit des informations sur l’utilisation des stratégies de Cloud Discovery.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: d3b5b62664abc9e82ad726e60c5105ef29ae0b16
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285483"
---
# <a name="cloud-discovery-policies"></a>Stratégies Cloud Discovery

*S’applique à : Microsoft Cloud App Security*

Vous pouvez créer des stratégies de détection d’application pour vous avertir quand de nouvelles applications sont détectées. Cloud App Security recherche également les anomalies dans tous les journaux de votre Cloud Discovery.

## <a name="creating-an-app-discovery-policy"></a>Création d’une stratégie de découverte d’application

Les stratégies de détection vous permettent de définir des alertes qui vous informent quand de nouvelles applications sont détectées au sein de votre organisation.

1. Dans la console, cliquez sur **contrôle** , puis sur **stratégies**.

2. Cliquez sur **créer une stratégie** et sélectionnez stratégie de découverte d' **application**.

    ![menu stratégie de découverte d’application](media/app-discovery-policy-menu.png "menu stratégie de découverte d’application")

3. Donnez un nom et une description à votre stratégie. Si vous le souhaitez, vous pouvez le baser sur un modèle. Pour plus d’informations sur les modèles de stratégie, consultez [contrôler les applications Cloud avec des stratégies](control-cloud-apps-with-policies.md).

4. Définissez la **gravité** de la stratégie.

5. Pour définir les applications découvertes qui déclenchent cette stratégie, ajoutez des filtres.

6. Vous pouvez définir un seuil pour la sensibilité de la stratégie. Activez **déclencher une correspondance de stratégie si tous les éléments suivants se produisent le même jour**. Vous pouvez définir des critères que l’application doit dépasser quotidiennement pour correspondre à la stratégie. Sélectionnez l’un des critères suivants :
    - Trafic quotidien
    - Données téléchargées
    - Nombre d’adresses IP
    - Nombre de transactions
    - Nombre d'utilisateurs
    - Données téléchargées

7. Définissez une **limite d’alertes quotidienne** sous **alertes**. Indiquez si l’alerte doit être envoyée sous forme d’e-mail, de message texte ou les deux. Fournissez ensuite les numéros de téléphone et les adresses de messagerie nécessaires.
    - Cliquer sur **enregistrer les paramètres d’alerte comme valeur par défaut pour votre organisation** permet aux futures stratégies d’utiliser le paramètre.
    - Si vous avez un paramètre par défaut, vous pouvez sélectionner **utiliser les paramètres par défaut de votre organisation**.

8. Sélectionnez les actions de **gouvernance** à appliquer lorsqu’une application correspond à cette stratégie. Il peut baliser les **stratégies**comme approuvées **, non**approuvées ou comme une balise personnalisée.

9. Cliquez sur **Créer**.

Par exemple, si vous souhaitez découvrir des applications d’hébergement risquées qui se trouvent dans votre environnement Cloud, définissez votre stratégie comme suit :

Définissez les filtres de stratégie pour découvrir tous les services qui se trouvent dans la catégorie **services d’hébergement** et qui ont un score de risque de 1, indiquant qu’ils sont très risqués.

 Définissez les seuils qui doivent déclencher une alerte pour une application découverte donnée en bas. Par exemple, alerte uniquement si plus de 100 utilisateurs dans l’environnement ont utilisé l’application et s’ils ont téléchargé une certaine quantité de données à partir du service.
En outre, vous pouvez définir la limite des alertes quotidiennes que vous souhaitez recevoir.

![exemple de stratégie de découverte d’application](media/app-discovery-policy-example.png "exemple de stratégie de découverte d’application")

## <a name="cloud-discovery-anomaly-detection"></a>Détection des anomalies Cloud Discovery

Cloud App Security recherche les anomalies dans tous les journaux de votre Cloud Discovery. Par exemple, lorsqu’un utilisateur, qui n’a jamais utilisé Dropbox, en charge soudainement 600 Go, ou lorsqu’il y a beaucoup plus de transactions que d’habitude sur une application particulière. La stratégie de détection des anomalies est activée par défaut. Il n’est pas nécessaire de configurer une nouvelle stratégie pour qu’elle fonctionne. Toutefois, vous pouvez affiner les types d’anomalies pour lesquelles vous souhaitez recevoir des alertes dans la stratégie par défaut.

1. Dans la console, cliquez sur **contrôle** , puis sur **stratégies**.

2. Cliquez sur **créer une stratégie** et sélectionnez **Cloud Discovery stratégie de détection des anomalies**.

    ![menu de stratégie de détection des anomalies Cloud Discovery](media/cloud-discovery-anomaly-detection-policy-menu.png "menu de stratégie de détection des anomalies Cloud Discovery")

3. Donnez un nom et une description à votre stratégie. Si vous le souhaitez, vous pouvez le baser sur un modèle ; pour plus d’informations sur les modèles de stratégie, consultez [contrôler les applications Cloud avec des stratégies](control-cloud-apps-with-policies.md).

4. Pour définir les applications découvertes qui déclenchent cette stratégie, cliquez sur **Ajouter des filtres**.

    Les filtres sont choisis dans des listes déroulantes. Pour ajouter des filtres, cliquez sur le bouton plus. Pour supprimer un filtre, cliquez sur « X ».

5. Sous **appliquer** , indiquez si cette stratégie s’applique à **tous les rapports continus** ou à **des rapports continus spécifiques**. Indiquez si la stratégie s’applique aux **utilisateurs**, aux **adresses IP**ou aux deux.

6. Sélectionnez les dates auxquelles l’activité anormale s’est produite pour déclencher l’alerte sous **déclencher des alertes uniquement pour les activités suspectes qui se produisent après la date.**

7. Définissez une **limite d’alertes quotidienne** sous **alertes**. Indiquez si l’alerte doit être envoyée sous forme d’e-mail, de message texte ou les deux. Fournissez ensuite les numéros de téléphone et les adresses de messagerie nécessaires.
    - Cliquer sur **enregistrer les paramètres d’alerte comme valeur par défaut pour votre organisation** permet aux futures stratégies d’utiliser le paramètre.
    - Si vous avez un paramètre par défaut, vous pouvez sélectionner **utiliser les paramètres par défaut de votre organisation**.

8. Cliquez sur **Créer**.

![nouvelle stratégie d’anomalie de découverte](media/new-discovery-anomaly-policy.png "nouvelle stratégie d’anomalie de découverte")

## <a name="next-steps"></a>Étapes suivantes :

> [!div class="nextstepaction"]
> [Stratégies d’activité utilisateur](user-activity-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
