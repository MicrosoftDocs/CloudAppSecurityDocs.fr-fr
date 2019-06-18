---
title: Stratégies cloud Discovery - Cloud App Security | Microsoft Docs
description: Cet article décrit les étapes pour configurer de nombreuses stratégies Cloud Discovery dans Cloud App Security.
author: ShlomoSagir-MS
ms.author: ShlomoSagir-MS
ms.date: 06/13/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.assetid: 570da960-771d-484f-932d-b086f2ec2978
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: f301e5796fe408b9c1fb00b859c848bf4b62ba5f
ms.sourcegitcommit: 5c6d41aae2d9ac461917338f4a423f7a2683aca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/16/2019
ms.locfileid: "67149536"
---
# <a name="cloud-discovery-policies"></a>Stratégies Cloud Discovery

*S’applique à : Microsoft Cloud App Security*

Cet article fournit une vue d’ensemble de la prise en main à l’aide de Cloud App Security de gagner en visibilité au sein de votre organisation Shadow It à l’aide de Cloud Discovery.

Cloud App Security vous permet de découvrir et d’analyser les applications cloud qui sont en cours d’utilisation dans l’environnement de votre organisation. Le tableau de bord Cloud Discovery affiche toutes les applications de cloud en cours d’exécution dans l’environnement et les classe par la disponibilité de la fonction et d’entreprise. Pour chaque application, Découvrez les utilisateurs associés, IP adresses machines, transactions et évaluation des risques effectue sans avoir à installer un agent sur vos appareils de point de terminaison.

## Détecter l’utilisation d’application volumineux ou large nouveau <a name= "detect-volume"></a>

Détecter les nouvelles applications fréquemment utilisées, en termes de nombre d’utilisateurs ou de la quantité de trafic de votre organisation.

### <a name="prerequisites"></a>Prérequis

Rapports de chargement automatique des journaux de configurer pour continus Cloud Discovery, comme décrit dans [chargement automatique des journaux de configuration pour des rapports continus](configure-automatic-log-upload-for-continuous-reports.md).

### <a name="steps"></a>Étapes

1.  Sur le **stratégies** page, créez une nouvelle **stratégie de découverte d’application**

2.  Dans le **modèle de stratégie** champ, sélectionnez **nouvelle application avec volume élevé** ou **nouvelle application populaire** et appliquer le modèle.

3.  Personnaliser les filtres de stratégie pour répondre aux besoins de votre organisation.

4.  Configurer les actions à prendre lorsqu’une alerte est déclenchée.

> [!NOTE]
>  Une alerte est générée une fois pour chaque nouvelle application qui n’est pas détectée au cours des 90 derniers jours.

## <a name="detect-new-risky-or-non-compliant-app-use"></a>Détecter la nouvelle utilisation de l’application à risque ou non conforme

Détecter les risques d’exposition de votre organisation dans les applications de cloud qui ne répondent pas à vos normes de sécurité.

### <a name="prerequisites"></a>Prérequis

Rapports de chargement automatique des journaux de configurer pour continus Cloud Discovery, comme décrit dans [chargement automatique des journaux de configuration pour des rapports continus](configure-automatic-log-upload-for-continuous-reports.md).

### <a name="steps"></a>Étapes

1.  Sur le **stratégies** page, créez une nouvelle **stratégie de découverte d’application.**

2.  Dans le **modèle de stratégie** champ, sélectionnez le **nouvelle application à risques** modèle et appliquer le modèle.

3.  Sous **application remplissant toutes les conditions suivantes** définir le [Score de risque](risk-score.md) slider et le facteur de risque de conformité pour personnaliser vous sont le niveau de risque que vous souhaitez déclencher une alerte, puis définissez les filtres de stratégie pour répondre aux exigences de sécurité de votre organisation.

    1.  Facultatif : Pour obtenir des détections plus explicites, personnaliser la quantité de trafic qui déclenchera une alerte.

        1.  Vérifier le **déclencher une correspondance de stratégie si tous les éléments suivants se produisent sur le même jour** case à cocher.

        2.  Sélectionnez **trafic quotidien** supérieure à 2 000 Go (ou autre).

4.  Configurer des actions de gouvernance à entreprendre lorsqu’une alerte est déclenchée. Sous **gouvernance**, sélectionnez **baliser l’application comme non approuvées.**<br>Accès à l’application est bloqué automatiquement lorsque la stratégie trouve une correspondance.

5.  Facultatif : Tirez parti [intégrations natives Cloud App Security](set-up-cloud-discovery.md) avec des passerelles de Web sécurisé pour bloquer l’accès de l’application.

## <a name="detect-use-of-unsanctioned-business-apps"></a>Détecter l’utilisation des applications métier non approuvées

Vous pouvez détecter lorsque vos employés continuent d’utiliser des applications non approuvées en remplacement pour les applications d’entreprise approuvées.

### <a name="prerequisites"></a>Prérequis

-   Rapports de chargement automatique des journaux de configurer pour continus Cloud Discovery, comme décrit dans [chargement automatique des journaux de configuration pour des rapports continus](configure-automatic-log-upload-for-continuous-reports.md).

### <a name="steps"></a>Étapes

1.  Dans le catalogue d’applications Cloud, recherchez vos applications d’entreprise et les marquer avec un [balise d’application personnalisée](discovered-app-queries.md#creating-and-managing-custom-app-tags).

2.  Suivez les étapes de [détecter le nouveau volume élevé ou l’utilisation des applications large](#detect-volume).

3.  Ajouter un **balise d’application** de filtrer et les balises d’application que vous avez créé pour vos applications d’entreprise.

4.  Configurer des actions de gouvernance à entreprendre lorsqu’une alerte est déclenchée. Sous la gouvernance, sélectionnez **baliser l’application comme non approuvées**.<br>Accès à l’application est bloqué automatiquement lorsque la stratégie trouve une correspondance.

5.  Facultatif : Tirez parti [intégrations natives Cloud App Security](set-up-cloud-discovery.md) avec des passerelles de Web sécurisé pour bloquer l’accès de l’application.

## <a name="detect-unusual-usage-patterns-on-your-network"></a>Détecter les modèles d’utilisation inhabituelles sur votre réseau

Détecter les modèles d’utilisation de trafic anormaux (chargements/téléchargements) dans vos applications cloud, qui proviennent d’utilisateurs ou adresses IP à l’intérieur du réseau de votre organisation.

### <a name="prerequisites"></a>Prérequis

Rapports de chargement automatique des journaux de configurer pour continus Cloud Discovery, comme décrit dans [chargement automatique des journaux de configuration pour des rapports continus](configure-automatic-log-upload-for-continuous-reports.md).

### <a name="steps"></a>Étapes

1.  Sur le **stratégies** page, créez une nouvelle **stratégie de détection des anomalies Cloud Discovery**.

2.  Dans le **modèle de stratégie** champ, sélectionnez **un comportement anormal dans les utilisateurs découverts** ou **un comportement anormal dans les adresses IP découvertes**.

3.  Personnaliser les filtres pour répondre aux besoins de votre organisation.

4. Si vous voulez être alerté uniquement en cas d’anomalies impliquant des applications à risque, utilisez le **score de risque** filtre et définir la plage dans laquelle les applications sont considérées comme risquées.

4.  Utilisez le curseur pour **sélectionner la sensibilité de détection d’anomalie**.

> [!NOTE]
>  Une fois le chargement des journaux en continu est établi, le moteur de détection des anomalies prend quelques jours jusqu'à une ligne de base (période d’apprentissage), est établi pour le comportement attendu dans votre organisation. Après l’établie d’une ligne de base, commencer à recevoir des alertes basées sur les différences du comportement attendu le trafic entre les applications cloud effectuées par les utilisateurs ou à partir d’adresses IP.

## <a name="detect-data-exfiltration-to-unsanctioned-storage-apps"></a>Détecter l’exfiltration des données pour les applications de stockage non approuvées

Détecter l’exfiltration de données potentielle par un utilisateur à une application de stockage cloud non approuvées.

### <a name="prerequisites"></a>Prérequis

Rapports de chargement automatique des journaux de configurer pour continus Cloud Discovery, comme décrit dans [chargement automatique des journaux de configuration pour des rapports continus](configure-automatic-log-upload-for-continuous-reports.md).

### <a name="steps"></a>Étapes

1.  Sur le **stratégies** page, de modifier la stratégie intégrée **exfiltration des données aux applications non approuvées**.

2.  Sélectionnez le filtre **catégorie d’application** est égal à **stockage Cloud**.

3.  Cochez la case pour **créer une alerte pour chaque événement correspondant avec le niveau de gravité de la stratégie**.

4.  Configurer les actions à entreprendre lorsqu’une alerte est déclenchée.

## <a name="detect-risky-oauth-apps"></a>Détecter les applications OAuth à risque

Bénéficiez d’une visibilité et contrôle accrus de [applications OAuth](investigate-risky-oauth.md) qui sont installés à l’intérieur d’applications comme G Suite, Office 365 et Salesforce. Les applications OAuth qui demandent des autorisations élevées et ont Communauté rares à utiliser peuvent être considérées comme risquées.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer de l’application G Suite, Office 365 ou Salesforce connectée à l’aide de [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Étapes

1.  Sur le **stratégies** page, créez une nouvelle **stratégie d’application OAuth**.

2.  Sélectionnez le filtre **application** et définir l’application de la stratégie doit couvrir, G Suite, Office 365 ou Salesforce.

3.  Sélectionnez **niveau d’autorisation** filtrer equals **haute** (disponible pour G Suite et Office 365).

4.  Ajoutez le filtre **utilisation communautaire** est égal à **rares**.

4.  Configurer les actions à entreprendre lorsqu’une alerte est déclenchée. Par exemple, pour Office 365, consultez **révoquer l’application** pour les applications OAuth détectées par la stratégie.

> [!NOTE]
>  Prise en charge pour les magasins d’applications de G Suite, Office 365 et Salesforce.

## <a name="next-steps"></a>Étapes suivantes 

[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)  
  
  
