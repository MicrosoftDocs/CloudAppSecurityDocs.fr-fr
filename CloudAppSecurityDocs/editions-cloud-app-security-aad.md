---
title: Différences entre les fonctionnalités de découverte de Cloud App Security et d’Azure AD
description: Cet article décrit les différences entre les fonctionnalités de découverte de Microsoft Cloud App Security et d’Azure AD.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 8/29/2019
ms.topic: overview
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 825a8532588cc479bcc37e5373bff23ccc841d8d
ms.sourcegitcommit: 0b929f7c8feed7dfb40d5294179fd5c6fc079614
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "74461041"
---
# <a name="what-are-the-differences-in-discovery-capabilities-for-azure-active-directory-and-microsoft-cloud-app-security"></a>Différences entre les fonctionnalités de découverte d’Azure Active Directory et de Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

Cet article décrit les différences entre les fonctionnalités de découverte de Microsoft Cloud App Security et d’Azure Active Directory (Azure AD).

Pour plus d’informations sur les licences, consultez la fiche [Licences Microsoft Cloud App Security](https://aka.ms/mcaslicensing).

## <a name="microsoft-cloud-app-security"></a>Microsoft Cloud App Security

Microsoft Cloud App Security est une solution inter-SaaS complète qui offre une visibilité approfondie, des contrôles de données renforcés et une protection améliorée contre les menaces pour les applications cloud. Cloud Discovery, l’une des fonctionnalités de Cloud App Security, permet de mieux visualiser l’informatique fantôme en détectant les applications cloud en cours d’utilisation.

## <a name="enhanced-cloud-app-discovery-in-azure-active-directory"></a>Version améliorée de Cloud App Discovery dans Azure Active Directory

Azure Active Directory Premium P1 comprend [Azure Active Directory Cloud App Discovery](https://aka.ms/caddocsnew) sans coût supplémentaire. Cette fonctionnalité s’appuie sur les fonctionnalités Cloud Discovery de Microsoft Cloud App Security, qui offrent une visibilité approfondie de l’utilisation des applications cloud dans les organisations. [Passez à Microsoft Cloud App Security](https://www.microsoft.com/cloud-platform/cloud-app-security) pour recevoir la suite complète de fonctionnalités Cloud Access Security Broker (CASB) proposées par Microsoft Cloud App Security.

### <a name="feature-comparison"></a>Comparaison des fonctionnalités

Le tableau suivant compare les fonctionnalités de découverte de Microsoft Cloud App Security et d’Azure AD.

|Fonctionnalité|Composant|Microsoft Cloud App Security|Azure AD Cloud App Discovery|
|----|----|----|----|
|Cloud Discovery|Applications découvertes|> 16 000 applications cloud|> 16 000 applications cloud|
||Déploiement pour l’analyse de la découverte|Chargement manuel et automatique des journaux|Chargement manuel et automatique des journaux|
||Anonymisation des journaux pour la protection des données personnelles des utilisateurs|Oui|Oui|
||Accès à l’ensemble du catalogue d’applications cloud|Oui|Oui|
||Analyse de risque des applications cloud|Oui|Oui|
||Analyse de l’utilisation du cloud selon les applications, les utilisateurs et les adresses IP|Oui|Oui|
||Analytique et rapports suivis|Oui|Oui|
||Détection d’anomalie pour les applications découvertes|Oui||
|Protection des informations|Prise en charge de la protection contre la perte de données (DLP)|Contrôle du partage de données et DLP inter-SaaS||
||Permissions d’application et possibilité de révoquer l’accès|Oui||
||Paramètre de stratégie et application|Oui||
||Intégration avec Azure Information Protection |Oui||
||Intégration avec des solutions DLP tierces|Oui||
|Détection des menaces|Détection d’anomalie et analyse comportementale|Pour les applications multi-SaaS||
||Correction manuelle et automatique des alertes|Oui||
||Connecteur SIEM|Oui. Alertes et journaux d’activité pour les applications inter-SaaS||
||Intégration à Microsoft Intelligent Security Graph|Oui||
||Stratégies des activités|Oui||

## <a name="next-steps"></a>Étapes suivantes

Découvrez les concepts de base dans [Bien démarrer avec Cloud App Security](getting-started-with-cloud-app-security.md).

[!INCLUDE [Open support ticket](includes/support.md)].
