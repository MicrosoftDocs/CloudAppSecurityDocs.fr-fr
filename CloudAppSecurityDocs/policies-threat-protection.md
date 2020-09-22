---
title: Stratégies de protection contre les menaces-Cloud App Security
description: Cette rubrique décrit les étapes permettant de configurer de nombreuses stratégies de protection contre les menaces dans Cloud App Security.
author: shsagir
ms.author: shsagir
ms.date: 06/13/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 4860dc37a2d0ad8fab903ec852e5e21074672a81
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90877825"
---
# <a name="threat-protection-policies"></a>Stratégies de protection contre les menaces

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Cloud App Security vous permet d’identifier les problèmes d’utilisation et de sécurité du Cloud à haut risque, de détecter un comportement anormal des utilisateurs et d’éviter les menaces dans vos applications Cloud approuvées. Bénéficiez d’une visibilité sur les activités des utilisateurs et des administrateurs et définissez des stratégies pour alerter automatiquement lorsque des comportements suspects ou des activités spécifiques que vous considérez comme risquées sont détectés. Sortez de la grande quantité de données de Microsoft Threat Intelligence et de la recherche de sécurité pour vous assurer que vos applications approuvées disposent de tous les contrôles de sécurité dont vous avez besoin et que vous pouvez en garder le contrôle.

> [!NOTE]
> Lors de l’intégration d’Cloud App Security avec Azure-protection avancée contre les menaces (Azure ATP), les stratégies de Azure ATP s’affichent également dans la page stratégies. Pour obtenir la liste des stratégies de Azure ATP, consultez [alertes de sécurité](/azure-advanced-threat-protection/suspicious-activity-guide).

## <a name="detect-and-control-user-activity-from-unfamiliar-locations"></a>Détecter et contrôler l’activité des utilisateurs à partir d’emplacements inconnus

Détection automatique de l’accès ou de l’activité des utilisateurs à partir d’emplacements inconnus qui n’ont jamais été visités par une autre personne de votre organisation.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer d’au moins une application connectée à l’aide de [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) ou intégrée à l’aide du [contrôle d’accès conditionnel aux applications avec des contrôles de session](proxy-deployment-aad.md).

### <a name="steps"></a>Étapes

Cette détection est automatiquement configurée pour vous avertir en cas d’accès à partir de nouveaux emplacements. Vous n’avez aucune action à effectuer pour configurer cette stratégie. Pour plus d’informations, consultez [Stratégies de détection d'anomalies](anomaly-detection-policy.md).

## <a name="detect-compromised-account-by-impossible-location-impossible-travel"></a>Détection du compte compromis par emplacement impossible (voyage impossible)

Détection automatique de l’accès ou de l’activité des utilisateurs à partir de 2 emplacements différents au cours d’une période de temps qui est plus rapide que le temps nécessaire pour se déplacer entre les deux.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer d’au moins une application connectée à l’aide de [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) ou intégrée à l’aide du [contrôle d’accès conditionnel aux applications avec des contrôles de session](proxy-deployment-aad.md).
### <a name="steps"></a>Étapes

1. Cette détection est automatiquement configurée pour vous avertir en cas d’accès à partir d’emplacements impossibles. Vous n’avez aucune action à effectuer pour configurer cette stratégie. Pour plus d’informations, consultez [Stratégies de détection d'anomalies](anomaly-detection-policy.md).
2. Facultatif : vous pouvez [personnaliser les stratégies de détection des anomalies](anomaly-detection-policy.md#scope-anomaly-detection-policies):

    - Personnaliser l’étendue de détection en termes d’utilisateurs et de groupes

    - Choisir les types de connexions à prendre en compte

    - Définir vos préférences de sensibilité pour les alertes

3. Créez la stratégie de détection des anomalies.

## <a name="detect-suspicious-activity-from-an-on-leave-employee"></a>Détection d’une activité suspecte à partir d’un employé « à la sortie »

Détectez quand un utilisateur, qui est en congé non payé et ne doit pas être actif sur une ressource de l’organisation, accède à l’une des ressources de Cloud de votre organisation.

### <a name="prerequisites"></a>Prérequis

- Vous devez disposer d’au moins une application connectée à l’aide de [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

- Créez un groupe de sécurité dans Azure Active Directory pour les utilisateurs en congé sans paiement et ajoutez tous les utilisateurs que vous souhaitez analyser.

### <a name="steps"></a>Étapes

1. Dans l’écran [groupes d’utilisateurs](user-groups.md) , cliquez sur créer un groupe d' **utilisateurs** et importez le groupe de Azure ad approprié.

2. Dans la page **stratégies** , créez une nouvelle **stratégie d’activité**.

3. Définissez le **groupe d’utilisateurs** de filtre sur le nom des groupes d’utilisateurs que vous avez créés dans Azure AD pour les utilisateurs de congé sans paiement.

4. Facultatif : définissez les actions de **gouvernance** à effectuer sur les fichiers lorsqu’une violation est détectée. Les actions de gouvernance disponibles varient d’un service à l’autre. Vous pouvez choisir **suspendre l’utilisateur**.

5. Créez la stratégie de fichier.

## <a name="detect-and-notify-when-outdated-browser-os-is-used"></a>Détecter et notifier quand un système d’exploitation de navigateur obsolète est utilisé

Détecte quand un utilisateur utilise un navigateur avec une version obsolète du client qui peut poser des problèmes de conformité ou de sécurité à votre organisation.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer d’au moins une application connectée à l’aide de [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) ou intégrée à l’aide du [contrôle d’accès conditionnel aux applications avec des contrôles de session](proxy-deployment-aad.md).

### <a name="steps"></a>Étapes

1. Dans la page **stratégies** , créez une nouvelle **stratégie d’activité**.

2. Définissez la **balise filtre agent utilisateur** sur égal à **navigateur obsolète** et **système d’exploitation obsolète**.

3. Définissez les actions de **gouvernance** à effectuer sur les fichiers lorsqu’une violation est détectée. Les actions de gouvernance disponibles varient d’un service à l’autre. Sous **toutes les applications**, sélectionnez **notifier l’utilisateur**pour que vos utilisateurs puissent agir sur l’alerte et mettre à jour les composants nécessaires.

4. Créez la stratégie d’activité.

## <a name="detect-and-alert-when-admin-activity-is-detected-on-risky-ip-addresses"></a>Détecter et alerter quand une activité d’administration est détectée sur des adresses IP à risque

Détectez les activités d’administration effectuées à partir de et de l’adresse IP considérée comme une adresse IP à risque et avertissez l’administrateur système pour une investigation plus poussée ou définissez une action de gouvernance sur le compte de l’administrateur.

### <a name="prerequisites"></a>Prérequis

- Vous devez disposer d’au moins une application connectée à l’aide de [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

- Dans la roue dentée paramètres, sélectionnez **plages d’adresses IP** , puis cliquez sur le signe + pour ajouter des plages d’adresses IP pour vos sous-réseaux internes et leurs adresses IP publiques de sortie. Définissez la **catégorie** sur **interne**.

### <a name="steps"></a>Étapes

1. Dans la page **stratégies** , créez une nouvelle **stratégie d’activité**.

2. Affectez à **agir sur** **une seule activité**.

3. Définir le filtre **adresse IP** sur **catégorie** est égal à **risqué**

4. Définir l' **activité d’administration** de filtre sur **true**

5. Définissez les actions de **gouvernance** à effectuer sur les fichiers lorsqu’une violation est détectée. Les actions de gouvernance disponibles varient d’un service à l’autre. Sous **toutes les applications**, sélectionnez **notifier l’utilisateur**pour que vos utilisateurs puissent agir sur l’alerte et mettre à jour les composants nécessaires en **copient le responsable de l’utilisateur**.

6. Créez la stratégie d’activité.

## <a name="detect-activities-by-service-account-from-external-ip-addresses"></a>Détecter les activités par compte de service à partir d’adresses IP externes

Détecter les activités de compte de service provenant d’une adresse IP non interne. Cela peut indiquer un comportement suspect ou un compte compromis.

### <a name="prerequisites"></a>Prérequis

- Vous devez disposer d’au moins une application connectée à l’aide de [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).
- Dans la roue dentée paramètres, sélectionnez **plages d’adresses IP** , puis cliquez sur le signe + pour ajouter des plages d’adresses IP pour vos sous-réseaux internes et leurs adresses IP publiques de sortie. Définissez la **catégorie** sur **interne**.

- Standardisez les conventions d’affectation de noms pour les comptes de service dans votre environnement, par exemple, définissez tous les noms de comptes sur Démarrer avec « SVC ».

### <a name="steps"></a>Étapes

1. Dans la page **stratégies** , créez une nouvelle **stratégie d’activité**.

2. Définissez l' **utilisateur** du filtre sur **Name** , puis **commencez par** et entrez votre convention d’affectation de noms, par exemple SVC.

3. Définissez l' **adresse IP** de filtre **sur catégorie** n’est pas égale à **autre** et **entreprise**.

4. Définissez les actions de **gouvernance** à effectuer sur les fichiers lorsqu’une violation est détectée. Les actions de gouvernance disponibles varient d’un service à l’autre.

5. Créez la stratégie.

## <a name="detect-mass-download-data-exfiltration"></a>Détecter le téléchargement en masse (exfiltration des données)

Détectez le moment où un utilisateur accède à un grand nombre de fichiers ou le télécharge sur une brève période.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer d’au moins une application connectée à l’aide de [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) ou intégrée à l’aide du [contrôle d’accès conditionnel aux applications avec des contrôles de session](proxy-deployment-aad.md).

### <a name="steps"></a>Étapes

1. Dans la page **stratégies** , créez une nouvelle **stratégie d’activité**.

2. Définissez la **balise** les **adresses IP** de filtre sur n’est pas égale **Microsoft Azure**. Cela exclut les activités non interactives basées sur l’ordinateur.

3. Définissez les **types d’activité** de filtre sur, puis sélectionnez toutes les activités de téléchargement pertinentes.

4. Définissez les actions de **gouvernance** à effectuer sur les fichiers lorsqu’une violation est détectée. Les actions de gouvernance disponibles varient d’un service à l’autre.
5. Créez la stratégie.

## <a name="detect-potential-ransomware-activity"></a>Détecter l’activité de ransomware potentielle

Détection automatique de l’activité de ransomware potentiel.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer d’au moins une application connectée à l’aide de [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Étapes

1. Cette détection est automatiquement configurée pour vous avertir en cas de détection d’un risque de ransomware potentiel. Vous n’avez aucune action à effectuer pour configurer cette stratégie. Pour plus d’informations, consultez [Stratégies de détection d'anomalies](anomaly-detection-policy.md).

2. Il est possible de configurer l' **étendue** de la détection et de personnaliser les actions de gouvernance à entreprendre lorsqu’une alerte est déclenchée. Pour plus d’informations sur la façon dont Cloud App Security identifie le ransomware, consultez [protection de votre organisation contre les ransomware](use-case-ransomware.md).

> [!NOTE]
> Cela s’applique à Office 365, G suite, Box et Dropbox.

## <a name="detect-malware-in-the-cloud"></a>Détecter les logiciels malveillants dans le Cloud

Détectez les fichiers contenant des programmes malveillants dans vos environnements Cloud en utilisant l’intégration de Cloud App Security avec le moteur Threat Intelligence de Microsoft.

### <a name="prerequisites"></a>Prérequis

- Pour la détection de programmes malveillants Office 365, vous devez disposer d’une licence valide pour Office 365-protection avancée contre les menaces P1.
- Vous devez disposer d’au moins une application connectée à l’aide de [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Étapes

- Cette détection est automatiquement configurée pour vous avertir lorsqu’un fichier peut contenir un programme malveillant. Vous n’avez aucune action à effectuer pour configurer cette stratégie. Pour plus d’informations, consultez [Stratégies de détection d'anomalies](anomaly-detection-policy.md).

## <a name="detect-rogue-admin-takeover"></a>Détecter la prise en charge des administrateurs non autorisés

Détectez les activités d’administration répétées qui peuvent indiquer des intentions malveillantes.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer d’au moins une application connectée à l’aide de [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Étapes

1. Dans la page **stratégies** , créez une nouvelle **stratégie d’activité**.

2. Définissez **agir sur** une **activité répétée** et personnalisez les **activités répétitives minimales** et définissez une **plage** de temps pour la conformité à la stratégie de votre organisation.

3. Affectez à l' **utilisateur** du filtre la valeur **à partir du groupe** égal et sélectionnez tout le groupe d’administration associé en tant qu' **acteur uniquement**.

4. Définissez le **type d’activité** de filtre sur toutes les activités en rapport avec les mises à jour de mot de passe, les modifications et les réinitialisations.

5. Définissez les actions de **gouvernance** à effectuer sur les fichiers lorsqu’une violation est détectée. Les actions de gouvernance disponibles varient d’un service à l’autre.
6. Créez la stratégie.

## <a name="detect-suspicious-inbox-manipulation-rules"></a>Détecter les règles de manipulation de boîtes de réception suspectes

Si une règle de boîte de réception suspecte a été définie sur la boîte de réception d’un utilisateur, cela peut signifier que le compte d’utilisateur est compromis et que la boîte aux lettres est utilisée pour distribuer le courrier indésirable et les logiciels malveillants dans votre organisation.

### <a name="prerequisites"></a>Prérequis

- Utilisation de Microsoft Exchange pour la messagerie électronique.

### <a name="steps"></a>Étapes

- Cette détection est automatiquement configurée pour vous avertir lorsqu’il existe un ensemble de règles de boîte de réception suspectes. Vous n’avez aucune action à effectuer pour configurer cette stratégie. Pour plus d’informations, consultez [Stratégies de détection d'anomalies](anomaly-detection-policy.md).

## <a name="detect-leaked-credentials"></a>Détecter les informations d’identification divulguées

Lorsque les cybercriminels compromettent les mots de passe valides des utilisateurs légitimes, ils partagent souvent ces informations d’identification. En général, les mots de passe volés sont publiés sur le « dark web », ou bien ils sont échangés ou vendus sur le marché noir.

Cloud App Security utilise l’intelligence des menaces de Microsoft pour faire correspondre ces informations d’identification à celles utilisées au sein de votre organisation.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer d’au moins une application connectée à l’aide de [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Étapes

Cette détection est automatiquement configurée pour vous avertir en cas de détection d’une fuite d’informations d’identification. Vous n’avez aucune action à effectuer pour configurer cette stratégie. Pour plus d’informations, consultez [Stratégies de détection d'anomalies](anomaly-detection-policy.md).

## <a name="detect-anomalous-file-downloads"></a>Détecter les téléchargements de fichiers anormaux

Détecte quand les utilisateurs effectuent plusieurs activités de téléchargement de fichiers dans une seule session, par rapport à la ligne de base apprise. Cela peut indiquer une tentative de violation.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer d’au moins une application connectée à l’aide de [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) ou intégrée à l’aide du [contrôle d’accès conditionnel aux applications avec des contrôles de session](proxy-deployment-aad.md).

### <a name="steps"></a>Étapes

1. Cette détection est automatiquement configurée pour vous avertir quand un téléchargement anormal se produit. Vous n’avez aucune action à effectuer pour configurer cette stratégie. Pour plus d’informations, consultez [Stratégies de détection d'anomalies](anomaly-detection-policy.md).

2. Il est possible de configurer l’étendue de la détection et de personnaliser l’action à entreprendre lorsqu’une alerte est déclenchée.

## <a name="detect-anomalous-file-shares-by-a-user"></a>Détecter les partages de fichiers anormaux par un utilisateur

Détectez le moment où les utilisateurs effectuent plusieurs activités de partage de fichiers dans une seule session en ce qui concerne la ligne de base apprise, ce qui peut indiquer une tentative de violation.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer d’au moins une application connectée à l’aide de [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) ou intégrée à l’aide du [contrôle d’accès conditionnel aux applications avec des contrôles de session](proxy-deployment-aad.md).

### <a name="steps"></a>Étapes

1. Cette détection est automatiquement configurée pour vous avertir lorsque les utilisateurs effectuent un partage de fichiers multiple. Vous n’avez aucune action à effectuer pour configurer cette stratégie. Pour plus d’informations, consultez [Stratégies de détection d'anomalies](anomaly-detection-policy.md).

2. Il est possible de configurer l’étendue de la détection et de personnaliser l’action à entreprendre lorsqu’une alerte est déclenchée.

## <a name="detect-anomalous-activities-from-infrequent-country"></a>Détecter les activités anormales d’un pays peu fréquent

Détectez les activités à partir d’un emplacement qui n’a pas été récemment visité ou qui n’a jamais été visité par l’utilisateur ou par un utilisateur de votre organisation.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer d’au moins une application connectée à l’aide de [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) ou intégrée à l’aide du [contrôle d’accès conditionnel aux applications avec des contrôles de session](proxy-deployment-aad.md).

### <a name="steps"></a>Étapes

1. Cette détection est automatiquement configurée pour vous avertir quand une activité anormale se produit dans un pays/une région peu fréquents. Vous n’avez aucune action à effectuer pour configurer cette stratégie. Pour plus d’informations, consultez [Stratégies de détection d'anomalies](anomaly-detection-policy.md).

2. Il est possible de configurer l’étendue de la détection et de personnaliser l’action à entreprendre lorsqu’une alerte est déclenchée.

> [!NOTE]
> La détection des emplacements anormaux nécessite une période d’apprentissage initiale de 7 jours. Pendant la période d’apprentissage, Cloud App Security ne génère pas d’alertes pour les nouveaux emplacements.

## <a name="detect-activity-performed-by-a-terminated-user"></a>Détecter l’activité effectuée par un utilisateur terminé

Détecte quand un utilisateur qui n’est plus un employé de votre organisation effectue une activité dans une application approuvée. Cela peut indiquer une activité malveillante par un employé qui a terminé l’accès aux ressources de l’entreprise.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer d’au moins une application connectée à l’aide de [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Étapes

1. Cette détection est automatiquement configurée pour vous avertir lorsqu’une activité est effectuée par un employé terminé. Vous n’avez aucune action à effectuer pour configurer cette stratégie. Pour plus d’informations, consultez [Stratégies de détection d'anomalies](anomaly-detection-policy.md).

2. Il est possible de configurer l’étendue de la détection et de personnaliser l’action à entreprendre lorsqu’une alerte est déclenchée.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]