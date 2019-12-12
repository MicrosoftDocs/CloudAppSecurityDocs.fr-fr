---
title: Stratégies de Cloud Discovery-Cloud App Security | Microsoft Docs
description: Cet article décrit les étapes permettant de configurer de nombreuses stratégies de Cloud Discovery dans Cloud App Security.
author: shsagir
ms.author: shsagir
ms.date: 06/13/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 58208567133bf9c8257e456a415c60ab3dacee0b
ms.sourcegitcommit: 6eff466c7a6817b14a60d8c3b2c201c7ae4c2e2c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74719199"
---
# <a name="cloud-discovery-policies"></a>Stratégies Cloud Discovery

*S’applique à : Microsoft Cloud App Security*

Cet article fournit une vue d’ensemble de la prise en main de l’utilisation de Cloud App Security pour obtenir une visibilité de l’ensemble de votre organisation en utilisant des Cloud Discovery.

Cloud App Security vous permet de détecter et d’analyser les applications Cloud en cours d’utilisation dans l’environnement de votre organisation. Le tableau de bord Cloud Discovery affiche toutes les applications Cloud en cours d’exécution dans l’environnement et les classe par fonction et préparation de l’entreprise. Pour chaque application, Découvrez les utilisateurs, les adresses IP, les machines, les transactions et l’évaluation des risques associés sans avoir à installer un agent sur vos appareils de point de terminaison.

## Détection d’une nouvelle utilisation d’applications volumineuses ou à grande quantité<a name= "detect-volume"></a>

Détectez les nouvelles applications qui sont fortement utilisées, en termes de nombre d’utilisateurs ou de volume de trafic dans votre organisation.

### <a name="prerequisites"></a>Conditions préalables

Configurez le chargement automatique des journaux pour les rapports de Cloud Discovery continus, comme décrit dans [configurer le chargement automatique des journaux pour les rapports continus](configure-automatic-log-upload-for-continuous-reports.md).

### <a name="steps"></a>Étapes

1. Dans la page **stratégies** , créez une **stratégie de découverte d’application** .

2. Dans le champ **modèle de stratégie** , sélectionnez **nouvelle application à volume élevé** ou **nouvelle application populaire** et appliquez le modèle.

3. Personnaliser les filtres de stratégie pour répondre aux besoins de votre organisation.

4. Configurez les actions à entreprendre lorsqu’une alerte est déclenchée.

> [!NOTE]
> Une alerte est générée une fois pour chaque nouvelle application qui n’a pas été découverte au cours des 90 derniers jours.

## <a name="detect-new-risky-or-non-compliant-app-use"></a>Détecter les nouvelles utilisation d’applications risquées ou non conformes

Détectez les risques potentiels de votre organisation dans les applications Cloud qui ne répondent pas à vos normes de sécurité.

### <a name="prerequisites"></a>Conditions préalables

Configurez le chargement automatique des journaux pour les rapports de Cloud Discovery continus, comme décrit dans [configurer le chargement automatique des journaux pour les rapports continus](configure-automatic-log-upload-for-continuous-reports.md).

### <a name="steps"></a>Étapes

1. Dans la page **stratégies** , créez une nouvelle **stratégie de découverte d’application.**

2. Dans le champ **modèle de stratégie** , sélectionnez le nouveau modèle d' **application risquée** et appliquez le modèle.

3. Sous **application correspondant à tous les éléments suivants** , définissez le curseur [score de risque](risk-score.md) et le facteur de risque de conformité pour personnaliser le niveau de risque auquel vous souhaitez déclencher une alerte et définissez les autres filtres de stratégie en fonction des exigences de sécurité de votre organisation.

    1. Facultatif : pour obtenir des détections plus explicites, personnalisez la quantité de trafic qui déclenchera une alerte.

    2. Cochez la case **déclencher une correspondance de stratégie si tous les éléments suivants se produisent le même jour** .

    3. Sélectionnez **le trafic quotidien** supérieur à 2000 Go (ou autre).

4. Configurez les actions de gouvernance à entreprendre lorsqu’une alerte est déclenchée. Sous **gouvernance**, sélectionnez **baliser l’application comme** non approuvée.<br />L’accès à l’application est automatiquement bloqué lorsque la stratégie est mise en correspondance.

5. Facultatif : Tirez parti de [Cloud App Security intégration native](set-up-cloud-discovery.md) avec des passerelles Web sécurisées pour bloquer l’accès aux applications.

## <a name="detect-use-of-unsanctioned-business-apps"></a>Détecter l’utilisation d’applications professionnelles non approuvées

Vous pouvez détecter quand vos employés continuent d’utiliser des applications non approuvées en remplacement des applications approuvées pour l’entreprise.

### <a name="prerequisites"></a>Conditions préalables

- Configurez le chargement automatique des journaux pour les rapports de Cloud Discovery continus, comme décrit dans [configurer le chargement automatique des journaux pour les rapports continus](configure-automatic-log-upload-for-continuous-reports.md).

### <a name="steps"></a>Étapes

1. Dans le catalogue d’applications Cloud, recherchez vos applications professionnelles et marquez-les avec une [balise d’application personnalisée](discovered-app-queries.md#creating-and-managing-custom-app-tags).

2. Suivez les étapes de la section [détecter une utilisation élevée du volume ou de l’application étendue](#detect-volume).

3. Ajoutez un filtre d' **étiquette d’application** et choisissez les balises d’application que vous avez créées pour vos applications professionnelles.

4. Configurez les actions de gouvernance à entreprendre lorsqu’une alerte est déclenchée. Sous gouvernance, sélectionnez **baliser l’application comme**non approuvée.<br />L’accès à l’application est automatiquement bloqué lorsque la stratégie est mise en correspondance.

5. Facultatif : Tirez parti de [Cloud App Security intégration native](set-up-cloud-discovery.md) avec des passerelles Web sécurisées pour bloquer l’accès aux applications.

## <a name="detect-unusual-usage-patterns-on-your-network"></a>Détecter les modèles d’utilisation inhabituels sur votre réseau

Détectez les modèles d’utilisation du trafic anormal (chargements/téléchargements) dans vos applications Cloud, qui proviennent d’utilisateurs ou d’adresses IP au sein du réseau de votre organisation.

### <a name="prerequisites"></a>Conditions préalables

Configurez le chargement automatique des journaux pour les rapports de Cloud Discovery continus, comme décrit dans [configurer le chargement automatique des journaux pour les rapports continus](configure-automatic-log-upload-for-continuous-reports.md).

### <a name="steps"></a>Étapes

1. Dans la page **stratégies** , créez une **stratégie de détection des anomalies Cloud Discovery**.

2. Dans le champ **modèle de stratégie** , sélectionnez **comportement anormal dans les utilisateurs découverts** ou **comportement anormal dans les adresses IP découvertes**.

3. Personnalisez les filtres pour répondre aux besoins de votre organisation.

4. Si vous souhaitez être alerté uniquement lorsqu’il existe des anomalies impliquant des applications risquées, utilisez les filtres de **score de risque** et définissez la plage dans laquelle les applications sont considérées comme risquées.

5. Utilisez le curseur pour sélectionner la sensibilité de la **détection des anomalies**.

> [!NOTE]
> Une fois le chargement continu du journal établi, le moteur de détection des anomalies prend quelques jours jusqu’à ce qu’une ligne de base (période d’apprentissage) soit établie pour le comportement attendu de votre organisation. Après avoir établi une ligne de base, vous commencez à recevoir des alertes en fonction des différences par rapport au comportement de trafic attendu sur les applications Cloud effectuées par les utilisateurs ou à partir d’adresses IP.

## <a name="detect-data-exfiltration-to-unsanctioned-storage-apps"></a>Détecter l’exfiltration de données vers des applications de stockage non approuvées

Détection de l’exfiltration des données potentielles par un utilisateur vers une application de stockage cloud non approuvée.

### <a name="prerequisites"></a>Conditions préalables

Configurez le chargement automatique des journaux pour les rapports de Cloud Discovery continus, comme décrit dans [configurer le chargement automatique des journaux pour les rapports continus](configure-automatic-log-upload-for-continuous-reports.md).

### <a name="steps"></a>Étapes

1. Sur la page **stratégies** , modifiez l' **exfiltration des données**de stratégie intégrée en applications non approuvées.

2. Sélectionnez la catégorie de l' **application** de filtre est égale à **stockage cloud**.

3. Cochez la case pour **créer une alerte pour chaque événement correspondant avec la gravité de la stratégie**.

4. Configurez les actions à entreprendre lorsqu’une alerte est déclenchée.

## <a name="detect-risky-oauth-apps"></a>Détecter les applications OAuth risquées

Bénéficiez d’une visibilité et d’un contrôle sur les [applications OAuth](investigate-risky-oauth.md) installées dans des applications telles que G suite, Office 365 et Salesforce. Les applications OAuth qui demandent des autorisations élevées et qui ont une utilisation communautaire rare peuvent être considérées comme risquées.

### <a name="prerequisites"></a>Conditions préalables

L’application G suite, Office 365 ou Salesforce doit être connectée à l’aide de [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Étapes

1. Dans la page **stratégies** , créez une nouvelle **stratégie d’application OAuth**.

2. Sélectionnez l' **application** de filtre et définissez l’application que la stratégie doit couvrir, G suite, Office 365 ou Salesforce.

3. Sélectionnez le filtre de **niveau d’autorisation** est égal à **élevé** (disponible pour G suite et O365).

4. Ajoutez le filtre l’utilisation de la **communauté** est égale à **rare**.

5. Configurez les actions à entreprendre lorsqu’une alerte est déclenchée. Par exemple, pour Office 365, activez la case à cocher **révoquer l’application** pour les applications OAuth détectées par la stratégie.

> [!NOTE]
> Pris en charge pour les magasins d’applications G suite, Office 365 et Salesforce.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
