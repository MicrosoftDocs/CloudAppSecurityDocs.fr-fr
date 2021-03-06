---
title: Créer des stratégies sur les applications Cloud Discovery
description: Cet article fournit des informations sur l’utilisation des stratégies Cloud Discovery.
ms.date: 01/05/2021
ms.topic: how-to
ms.openlocfilehash: 9c892eed6b1200fb658a9ea03a77eeb0a98078f8
ms.sourcegitcommit: ee66e70f711aa11501e308e53b1a4b46f2175e4e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97894703"
---
# <a name="create-cloud-discovery-policies"></a>Créer des stratégies de Cloud Discovery

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Vous pouvez créer des stratégies de découverte d’applications afin d’être averti lorsque de nouvelles applications sont détectées. Cloud App Security examine également tous les journaux de votre environnement Cloud Discovery pour déterminer s’ils contiennent des anomalies.

## <a name="creating-an-app-discovery-policy"></a>Création d’une stratégie de découverte d’application

Grâce aux stratégies de découverte, vous pouvez définir des alertes qui vous informent quand de nouvelles applications sont détectées au sein de votre organisation.

1. Accédez à **Control**  >  **Policies**  >  **Shadow IT**.

1. Cliquez sur **créer une stratégie** et sélectionnez stratégie de découverte d' **application**.

    ![Créer une stratégie de Cloud Discovery](media/create-policy-from-shadow-it-tab.png)

1. Attribuez un nom et une description à votre stratégie. Si vous le souhaitez, vous pouvez baser votre stratégie sur un modèle. Pour plus d’informations sur les modèles de stratégies, consultez [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md).

1. Définissez la **Gravité** de la stratégie.

1. Pour définir les applications découvertes qui doivent déclencher cette stratégie, ajoutez des filtres.

1. Vous pouvez définir un seuil pour la sensibilité de la stratégie. Activez l’option **Déclencher une correspondance de stratégie si tous les éléments suivants se produisent le même jour**. Vous pouvez définir les critères que l’application doit remplir quotidiennement pour respecter la stratégie. Sélectionnez l’un des critères suivants :
    - Trafic quotidien
    - Données téléchargées
    - Nombre d’adresses IP
    - Nombre de transactions
    - Nombre d’utilisateurs
    - Données chargées

1. Définissez une **Limite d’alerte quotidienne** sous **Alertes**. Choisissez si l’alerte doit être envoyée par e-mail, par SMS, ou les deux. Ensuite, entrez les numéros de téléphone et les adresses e-mail des destinataires.
    - Si vous cliquez sur **Enregistrer ces paramètres d’alerte en tant que paramètres par défaut pour votre organisation**, les prochaines stratégies qui seront définies utiliseront ces paramètres.
    - Si vous avez déjà configuré des paramètres par défaut, vous pouvez sélectionner **Utiliser les paramètres par défaut de votre organisation**.

1. Sélectionnez les actions de **gouvernance** à appliquer quand une application remplit tous les critères de cette stratégie. Vous pouvez étiqueter les stratégies comme étant **Approuvées** ou **Non approuvées**, ou bien utiliser une étiquette personnalisée.

1. Cliquez sur **Créer**.

> [!NOTE]
>
> - Les stratégies de découverte nouvellement créées (ou les stratégies avec des rapports continus mis à jour) déclenchent une alerte une fois dans 90 jours par application par rapport continu, qu’il existe des alertes pour la même application ou non. Ainsi, par exemple, si vous créez une stratégie pour découvrir de nouvelles applications populaires, elle peut déclencher des alertes supplémentaires pour les applications qui ont déjà été découvertes et alerté.
> - Les données des **rapports d’instantané** ne déclenchent pas d’alertes dans les stratégies de détection d’application.

Par exemple, pour découvrir les applications d’hébergement à risque qui ont été détectées dans votre environnement cloud, définissez votre stratégie de la façon suivante :

Définissez des filtres de stratégie afin de découvrir les services appartenant à la catégorie **Services d’hébergement** dont l’indice de risque est égal à 1, ce qui correspond à un risque élevé.

Définissez les seuils qui doivent déclencher une alerte en cas de découverte d’une application donnée. Par exemple, déclenchez une alerte uniquement si plus de 100 utilisateurs de l’environnement ont utilisé l’application et s’ils ont téléchargé une certaine quantité de données à partir du service. En outre, vous pouvez définir la limite des alertes quotidiennes à recevoir.

![exemple de stratégie de découverte d’application](media/app-discovery-policy-example.png "exemple de stratégie de découverte d’application")

## <a name="cloud-discovery-anomaly-detection"></a>Détection d’anomalie Cloud Discovery

Cloud App Security examine tous les journaux de votre environnement Cloud Discovery pour déterminer s’ils contiennent des anomalies. À titre d’exemple, citons un utilisateur qui n’a jamais utilisé Dropbox et qui y charge soudainement 600 Go de données ou une application qui fait l’objet de transactions dans des proportions inhabituelles. La stratégie de détection des anomalies est activée par défaut. Il n’est pas nécessaire de configurer une nouvelle stratégie pour que la détection fonctionne. Toutefois, dans la stratégie par défaut, vous pouvez choisir les types d’anomalies pour lesquels vous souhaitez être averti.

1. Dans la console, cliquez sur **Contrôle**, puis sur **Stratégies**.

1. Cliquez sur **Créer une stratégie** et sélectionnez **Créer une stratégie de détection des anomalies de Cloud Discovery**.

    ![menu de stratégie de détection des anomalies cloud discovery](media/cloud-discovery-anomaly-detection-policy-menu.png "menu de stratégie de détection des anomalies cloud discovery")

1. Attribuez un nom et une description à votre stratégie. Si vous le souhaitez, vous pouvez baser la stratégie sur un modèle. Pour plus d’informations sur les modèles de stratégie, consultez [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md).

1. Pour définir les applications découvertes qui doivent déclencher cette stratégie, cliquez sur **Ajouter des filtres**.

    Les filtres peuvent être sélectionnés dans des listes déroulantes. Pour ajouter des filtres, cliquez sur le bouton plus (+). Pour supprimer un filtre, cliquez sur le « X » en regard de celui-ci.

1. Sous **Appliquer à**, choisissez si cette stratégie doit s’appliquer à **Tous les rapports continus** ou à des **Rapports continus spécifiques**. Indiquez si la stratégie s’applique à des **Utilisateurs**, à des **Adresses IP**, ou aux deux.

1. Sous **Générer des alertes uniquement en cas d’activités suspectes après la date**, sélectionnez les dates pendant lesquelles l’occurrence d’une activité anormale doit déclencher une alerte.

1. Définissez une **Limite d’alerte quotidienne** sous **Alertes**. Choisissez si l’alerte doit être envoyée par e-mail, par SMS, ou les deux. Ensuite, entrez les numéros de téléphone et les adresses e-mail des destinataires.
    - Si vous cliquez sur **Enregistrer ces paramètres d’alerte en tant que paramètres par défaut pour votre organisation**, les prochaines stratégies qui seront définies utiliseront ces paramètres.
    - Si vous avez déjà configuré des paramètres par défaut, vous pouvez sélectionner **Utiliser les paramètres par défaut de votre organisation**.

1. Cliquez sur **Créer**.

    ![nouvelle stratégie de détection d’anomalie](media/new-discovery-anomaly-policy.png "nouvelle stratégie de détection d’anomalie")

## <a name="related-videos"></a>Vidéos associées

> [!div class="nextstepaction"]
> [Webinaire sur la configuration de la découverte d’application et du collecteur de journaux](webinars.md#on-demand-webinars)

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Stratégies d’activité utilisateur](user-activity-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
