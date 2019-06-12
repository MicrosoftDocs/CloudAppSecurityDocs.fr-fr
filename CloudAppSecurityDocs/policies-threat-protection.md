---
title: Stratégies de protection - Cloud App Security des menaces | Microsoft Docs
description: Cette rubrique décrit les étapes pour configurer de nombreuses stratégies de protection contre les menaces dans Cloud App Security.
author: rkarlin
ms.author: rkarlin
ms.date: 06/13/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.assetid: 7c8d5bfd-194e-40ba-b0b0-dfae80f45ecb
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 4cb65835bf2f03eb6bef2fc5973be3420cdedb3d
ms.sourcegitcommit: 9f671d5dd5e5da023d598425442d8736546ca183
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66837767"
---
# <a name="threat-protection-policies"></a>Stratégies de protection contre les menaces

*S’applique à : Microsoft Cloud App Security*


Cloud App Security vous permet de vous identifier les problèmes de sécurité cloud et d’utilisation à haut risque, détecter un comportement anormal des utilisateurs et empêcher les menaces dans vos applications cloud approuvées. Obtenez une visibilité sur les activités d’administration et de l’utilisateur et définir des stratégies pour générer automatiquement une alerte lors de la détection de comportement suspect ou des activités spécifiques que vous considérez comme risquées. Dessiner à partir de la vaste quantité de menaces de Microsoft et les données de recherche de sécurité afin de garantir que vos applications approuvées bénéficient de tous les contrôles de sécurité que vous avez besoin de placent et vous aider à maîtriser.

## <a name="detect-and-control-user-activity-from-unfamiliar-locations"></a>Détecter et contrôler l’activité des utilisateurs à partir d’emplacements non connus

Détection automatique de l’accès utilisateur ou de l’activité à partir d’emplacements non connus qui ont été visités jamais par quelqu'un d’autre dans votre organisation.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer d’au moins une application connectée à l’aide [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) ou intégré à l’aide de [contrôle d’accès conditionnel avec contrôles de session](proxy-deployment-aad.md).

### <a name="steps"></a>Étapes

Cette détection est automatiquement configuré out-of-the-box pour vous avertir en cas d’accès à partir de nouveaux emplacements. Il est inutile d’agir pour configurer cette stratégie. Pour plus d’informations, consultez [Stratégies de détection d’anomalie](anomaly-detection-policy.md).

## <a name="detect-compromised-account-by-impossible-location-impossible-travel"></a>Compte compromis par emplacement impossible de détecter (voyage impossible)

Détection automatique de l’accès utilisateur ou de l’activité à partir de 2 emplacements au sein d’une période de temps plus court que le temps que nécessaire pour être déplacée entre les deux.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer d’au moins une application connectée à l’aide [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) ou intégré à l’aide de [contrôle d’accès conditionnel avec contrôles de session](proxy-deployment-aad.md).
### <a name="steps"></a>Étapes

1.  Cette détection est automatiquement configuré out-of-the-box pour vous avertir en cas d’accès à partir d’emplacements impossibles. Il est inutile d’agir pour configurer cette stratégie. Pour plus d’informations, consultez [Stratégies de détection d’anomalie](anomaly-detection-policy.md).
2. Facultatif : vous pouvez [personnaliser les stratégies de détection d’anomalie](anomaly-detection-policy.md#scope-anomaly-detection-policies): 
    - Personnaliser l’étendue de détection en termes d’utilisateurs et groupes

    - Choisir les types de connexions à prendre en compte

    - Définir vos préférences de sensibilité pour l’alerte

3.  Créez la stratégie de détection des anomalies.

## <a name="detect-suspicious-activity-from-an-on-leave-employee"></a>Détecter les activités suspectes à partir d’un employé « leave »

Détecter quand un utilisateur, ce qui est en congé et ne doit pas être active sur les ressources organisationnelles, accède à des ressources de cloud de votre organisation.

### <a name="prerequisites"></a>Prérequis

- Vous devez disposer d’au moins une application connectée à l’aide [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

- Créer un groupe de sécurité dans Azure Active Directory pour les utilisateurs en congé et ajouter tous les utilisateurs que vous souhaitez analyser.

### <a name="steps"></a>Étapes

1.  Sur le [groupes d’utilisateurs](user-groups.md) , cliquez sur **créer un groupe utilisateur** et le groupe d’importation Azure AD appropriée.

2.  Sur le **stratégies** page, créez une nouvelle **stratégie d’activité**.

3.  Définissez le filtre **groupe d’utilisateurs** égal au nom des groupes d’utilisateurs que vous avez créé dans Azure AD pour la fraction laissez les utilisateurs.

4.  Facultatif : Définir le **gouvernance** actions à entreprendre sur les fichiers lorsqu’une violation est détectée. Les actions de gouvernance disponibles varient entre les services. Vous pouvez choisir **suspendre l’utilisateur**.

6.  Créer la stratégie de fichier.

## <a name="detect-and-notify-when-outdated-browser-os-is-used"></a>Détecter et en informer lorsque obsolète navigateur du système d’exploitation est utilisé.

Détecter quand un utilisateur utilise un navigateur avec une version obsolète de client qui peut poser conformité ou les risques de sécurité à votre organisation.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer d’au moins une application connectée à l’aide [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) ou intégré à l’aide de [contrôle d’accès conditionnel avec contrôles de session](proxy-deployment-aad.md).

### <a name="steps"></a>Étapes

1.  Sur le **stratégies** page, créez une nouvelle **stratégie d’activité**.

2.  Définissez le filtre **étiquette agent utilisateur** est égal à **navigateur obsolète** et **système d’exploitation obsolète**.

3. Définir le **gouvernance** actions à entreprendre sur les fichiers lorsqu’une violation est détectée. Les actions de gouvernance disponibles varient entre les services. Sous **toutes les applications**, sélectionnez **notifier l’utilisateur**, afin que vos utilisateurs puissent agir sur l’alerte et mettre à jour les composants nécessaires.

5.  Créer la stratégie d’activité.

## <a name="detect-and-alert-when-admin-activity-is-detected-on-risky-ip-addresses"></a>Détecter et traite de l’alerte en cas d’activité d’administration est détectée sur l’adresse IP risquée

Détecter les activités administratives effectuées à partir d’et l’adresse IP qui est considéré comme une adresse IP à risques, et informer l’administrateur système pour un examen approfondi ou une action de gouvernance sur le compte de l’administrateur.

### <a name="prerequisites"></a>Prérequis

- Vous devez disposer d’au moins une application connectée à l’aide [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).
 
- Dans la roue dentée des paramètres, sélectionnez **plages d’adresses IP** et cliquez sur le + pour ajouter des plages d’adresses IP pour vos sous-réseaux internes et leurs adresses IP publiques de sortie. Définir le **catégorie** à **interne**.

### <a name="steps"></a>Étapes

1.  Sur le **stratégies** page, créez une nouvelle **stratégie d’activité**.

2.  Définissez **agir sur** à **activité unique**.

3.  Définissez le filtre **adresse IP** à **catégorie** est égal à **risqué**

4.  Définissez le filtre **activité Administrative** à **True**

5.  Définir le **gouvernance** actions à entreprendre sur les fichiers lorsqu’une violation est détectée. Les actions de gouvernance disponibles varient entre les services. Sous **toutes les applications**, sélectionnez **notifier l’utilisateur**, afin que vos utilisateurs puissent agir sur l’alerte et mettre à jour les composants nécessaires **CC responsable de l’utilisateur**.

7.  Créer la stratégie d’activité.

## <a name="detect-activities-by-service-account-from-external-ip-addresses"></a>Détecter les activités par compte de service à partir d’adresses IP externes

Détecter les activités de compte de service provenant d’une adresse IP non interne adresses. Cela peut indiquer un comportement suspect ou un compte compromis.

### <a name="prerequisites"></a>Prérequis

- Vous devez disposer d’au moins une application connectée à l’aide [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).
- Dans la roue dentée des paramètres, sélectionnez **plages d’adresses IP** et cliquez sur le + pour ajouter des plages d’adresses IP pour vos sous-réseaux internes et leurs adresses IP publiques de sortie. Définir le **catégorie** à **interne**.

- Normaliser un conventions d’affectation de noms pour les comptes de service dans votre environnement, par exemple, définissez tous les noms de compte à commencer par « svc ».

### <a name="steps"></a>Étapes

1.  Sur le **stratégies** page, créez une nouvelle **stratégie d’activité**.

2.  Définissez le filtre **utilisateur** à **nom** , puis **commence par** et entrez votre convention d’affectation de noms, tels que svc.

3.  Définissez le filtre **adresse IP** à **catégorie** n’est pas égal **autres** et **Corporate**.

4.  Définir le **gouvernance** actions à entreprendre sur les fichiers lorsqu’une violation est détectée. Les actions de gouvernance disponibles varient entre les services.

5.  Créer la stratégie.

## <a name="detect-mass-download-data-exfiltration"></a>Détecter le téléchargement en masse (exfiltration de données)

Détecter lorsqu’un utilisateur donné accède à ou télécharge un grand nombre de fichiers sur une courte période de temps.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer d’au moins une application connectée à l’aide [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) ou intégré à l’aide de [contrôle d’accès conditionnel avec contrôles de session](proxy-deployment-aad.md).

### <a name="steps"></a>Étapes

1.  Sur le **stratégies** page, créez une nouvelle **stratégie d’activité**.

2.  Définissez le filtre **adresses IP** à **balise** n’est pas égal **Microsoft Azure**. Cela exclut des activités sur l’ordinateur non interactif.

3.  Définissez le filtre **types d’activités** est égal à, puis sélectionnez toutes les activités de téléchargement approprié.

4. Définir le **gouvernance** actions à entreprendre sur les fichiers lorsqu’une violation est détectée. Les actions de gouvernance disponibles varient entre les services.
5.  Créer la stratégie.

## <a name="detect-potential-ransomware-activity"></a>Détecter l’activité de Ransomware potentielle

Détection automatique de l’activité de Ransomware potentielle.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer d’au moins une application connectée à l’aide [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Étapes

- Cette détection est automatiquement configuré out-of-the-box pour vous avertir lorsqu’il existe un risque potentiel de ransomware détecté. Il est inutile d’agir pour configurer cette stratégie. Pour plus d’informations, consultez [Stratégies de détection d’anomalie](anomaly-detection-policy.md).  

- Il est possible de configurer le **étendue** de la détection et de personnaliser les actions de gouvernance à entreprendre lorsqu’une alerte est déclenchée. Pour plus d’informations sur la façon dont Cloud App Security identifie Ransomware, consultez [protéger votre organisation contre les ransomware](use-case-ransomware.md).

> [!NOTE]
> Cela s’applique à Office 365, G Suite, Box et Dropbox.

## <a name="detect-malware-in-the-cloud"></a>Détecter les logiciels malveillants dans le cloud

Détecter les fichiers contenant des programmes malveillants dans vos environnements de cloud à l’aide de l’intégration de Cloud App Security avec le moteur de Microsoft Threat Intelligence.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer d’au moins une application connectée à l’aide [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Étapes

- Cette détection est automatiquement configuré out-of-the-box pour vous avertir lorsqu’il existe un fichier qui peut contenir des logiciels malveillants. Il est inutile d’agir pour configurer cette stratégie. Pour plus d’informations, consultez [Stratégies de détection d’anomalie](anomaly-detection-policy.md).  

## <a name="detect-rogue-admin-takeover"></a>Détecter la prise en charge d’administrateur non autorisé

Détecter les activités d’administration répétées pouvant indiquer des intentions malveillantes.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer d’au moins une application connectée à l’aide [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Étapes

1.  Sur le **stratégies** page, créez une nouvelle **stratégie d’activité**.

2.  Définir **agir sur** à **activité répétée** et personnaliser le **au Minimum les activités répétées** et définir un **laps de temps** pour se conformer à votre stratégie de l’organisation...

3.  Définissez le filtre **utilisateur** à **groupe** equals et sélectionnez tous les l’administrateur associé de groupe en tant que **acteur uniquement**.

4.  Définissez le filtre **type d’activité** est égal à toutes les activités qui se rapportent à des mises à jour du mot de passe, les modifications et réinitialisations.

5. Définir le **gouvernance** actions à entreprendre sur les fichiers lorsqu’une violation est détectée. Les actions de gouvernance disponibles varient entre les services.
6.  Créer la stratégie.

## <a name="detect-suspicious-inbox-manipulation-rules"></a>Détecter les règles de manipulation de boîte de réception suspecte

Si une règle de la boîte de réception suspecte a été définie sur la boîte de réception d’un utilisateur, cela peut indiquer que le compte d’utilisateur est compromis, et que la boîte aux lettres est utilisé pour distribuer le spam et les logiciels malveillants dans votre organisation.

### <a name="prerequisites"></a>Prérequis

- Utilisation de Microsoft Exchange pour le courrier électronique.

### <a name="steps"></a>Étapes

- Cette détection est automatiquement configuré out-of-the-box pour vous avertir lorsqu’il existe un ensemble de règles suspecte de boîte de réception. Il est inutile d’agir pour configurer cette stratégie. Pour plus d’informations, consultez [Stratégies de détection d’anomalie](anomaly-detection-policy.md).  


## <a name="detect-leaked-credentials"></a>Détecter les informations d’identification volées
  
Lorsque les cybercriminels compromettent les mots de passe valides d’utilisateurs légitimes, ils partagent souvent ces informations d’identification. Cela est généralement effectuée par leur validation publiquement sur les sites web ou de coller sombres ou échangés ou vendus sur le marché noir.

Cloud App Security utilise Microsoft Threat intelligence pour faire correspondre ces informations d’identification à celles utilisées au sein de votre organisation.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer d’au moins une application connectée à l’aide [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Étapes

Cette détection est automatiquement configuré out-of-the-box pour vous avertir lorsqu’une fuite d’informations d’identification possibles est détectée. Il est inutile d’agir pour configurer cette stratégie. Pour plus d’informations, consultez [Stratégies de détection d’anomalie](anomaly-detection-policy.md).  


## <a name="detect-anomalous-file-downloads"></a>Détecter les téléchargements de fichiers anormales

Détecter lorsque les utilisateurs effectuent plusieurs activités de téléchargement de fichier dans une session unique, par rapport à la ligne de base apprise. Cela peut indiquer une tentative de violation.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer d’au moins une application connectée à l’aide [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) ou intégré à l’aide de [contrôle d’accès conditionnel avec contrôles de session](proxy-deployment-aad.md).

### <a name="steps"></a>Étapes

- Cette détection est automatiquement configuré out-of-the-box pour vous avertir lorsqu’un téléchargement anormal se produit. Il est inutile d’agir pour configurer cette stratégie. Pour plus d’informations, consultez [Stratégies de détection d’anomalie](anomaly-detection-policy.md).  
- Il est possible de configurer l’étendue de la détection et à personnaliser l’action à entreprendre lorsqu’une alerte est déclenchée.

## <a name="detect-anomalous-file-shares-by-a-user"></a>Détecter les partages de fichiers anormales par un utilisateur

Détecter lorsque les utilisateurs effectuent plusieurs activités de partage de fichiers dans une seule session par rapport à la ligne de base apprise, ce qui peut indiquer une tentative de violation.

### <a name="prerequisites"></a>Prérequis
Vous devez disposer d’au moins une application connectée à l’aide [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) ou intégré à l’aide de [contrôle d’accès conditionnel avec contrôles de session](proxy-deployment-aad.md).
### <a name="steps"></a>Étapes

- Cette détection est automatiquement configuré out-of-the-box pour vous avertir lorsque les utilisateurs effectuent plusieurs partage de fichiers. Il est inutile d’agir pour configurer cette stratégie. Pour plus d’informations, consultez [Stratégies de détection d’anomalie](anomaly-detection-policy.md).  
- Il est possible de configurer l’étendue de la détection et à personnaliser l’action à entreprendre lorsqu’une alerte est déclenchée.

## <a name="detect-anomalous-activities-from-infrequent-country"></a>Détecter les activités anormales à partir de pays peu fréquents

Détecter les activités à partir d’un emplacement qui a récemment été pas ou n’a jamais été consultée par l’utilisateur ou par un utilisateur dans votre organisation.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer d’au moins une application connectée à l’aide [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) ou intégré à l’aide de [contrôle d’accès conditionnel avec contrôles de session](proxy-deployment-aad.md).

### <a name="steps"></a>Étapes

- Cette détection est automatiquement configuré out-of-the-box pour vous avertir lorsqu’une activité anormale se produit à partir d’un pays peu fréquents. Il est inutile d’agir pour configurer cette stratégie. Pour plus d’informations, consultez [Stratégies de détection d’anomalie](anomaly-detection-policy.md).  
- Il est possible de configurer l’étendue de la détection et à personnaliser l’action à entreprendre lorsqu’une alerte est déclenchée.

> [!NOTE]
> Détection d’emplacements anormaux nécessite une période d’apprentissage initiale de 7 jours. Pendant la période d’apprentissage, Cloud App Security ne génère pas d’alertes pour les nouveaux emplacements.

## <a name="detect-activity-performed-by-a-terminated-user"></a>Détecter les activités effectuées par un utilisateur se terminant par

Détecter lorsqu’un utilisateur qui n’est plus un employé de votre organisation effectue une activité dans une application approuvée. Cela peut indiquer des activités malveillantes par un employé congédié qui a toujours accès aux ressources d’entreprise.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer d’au moins une application connectée à l’aide [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Étapes

- Cette détection est automatiquement configuré out-of-the-box pour vous avertir lorsqu’une activité est effectuée par un employé congédié. Il est inutile d’agir pour configurer cette stratégie. Pour plus d’informations, consultez [Stratégies de détection d’anomalie](anomaly-detection-policy.md).  
- Il est possible de configurer l’étendue de la détection et à personnaliser l’action à entreprendre lorsqu’une alerte est déclenchée.


## <a name="next-steps"></a>Étapes suivantes 

[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)  
  
  
