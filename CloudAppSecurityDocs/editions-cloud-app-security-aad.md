---
title: Différences de fonctionnalités de découverte pour Cloud App Security et Azure AD
description: Cet article décrit les différences qui existent entre les fonctionnalités de découverte de Microsoft Cloud App Security et celles d’Azure AD.
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
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74461041"
---
# <a name="what-are-the-differences-in-discovery-capabilities-for-azure-active-directory-and-microsoft-cloud-app-security"></a>Quelles sont les différences qui existent entre les fonctionnalités de découverte d’Azure Active Directory et celles de Microsoft Cloud App Security ?

*S’applique à : Microsoft Cloud App Security*

Cet article décrit les différences qui existent entre les fonctionnalités de découverte de Microsoft Cloud App Security et celles d’Azure Active Directory (Azure AD).

Pour plus d’informations sur les licences, consultez la [fiche technique sur les licences Microsoft Cloud App Security](https://aka.ms/mcaslicensing).

## <a name="microsoft-cloud-app-security"></a>Microsoft Cloud App Security

Microsoft Cloud App Security est une solution complète multi-SaaS qui offre à vos applications cloud une meilleure visibilité, des contrôles de données puissants et une protection améliorée contre les menaces. Cloud Discovery est une fonctionnalité Cloud App Security qui vous permet de mieux détecter le « Shadow IT » en découvrant les applications cloud qui sont en cours d’utilisation.

## <a name="enhanced-cloud-app-discovery-in-azure-active-directory"></a>Cloud App Discovery améliorée dans Azure Active Directory

[Azure Active Directory Cloud App Discovery](https://aka.ms/caddocsnew) est fourni gratuitement avec Azure Active Directory Premium P1. Cette fonctionnalité est basée sur celles de Microsoft Cloud App Security Cloud Discovery, qui offrent une meilleure visibilité des applications cloud utilisées dans votre organisation. [Effectuez une mise à niveau vers Microsoft Cloud App Security](https://www.microsoft.com/cloud-platform/cloud-app-security) pour bénéficier de la suite complète des fonctionnalités Cloud App Security Broker (CASB) proposées par Microsoft Cloud App Security.

### <a name="feature-comparison"></a>Comparaison des fonctionnalités

Le tableau suivant compare les fonctionnalités de découverte de Microsoft Cloud App Security à celles d’Azure AD.

|Fonctionnalité|Fonctionnalité|Microsoft Cloud App Security|Azure AD Cloud App Discovery|
|----|----|----|----|
|Cloud Discovery|Applications découvertes|Plus de 16 000 applications cloud|Plus de 16 000 applications cloud|
||Déploiement de l’analyse de découverte|Chargement de journaux manuel et automatique|Chargement de journaux manuel et automatique|
||Anonymat des journaux pour la confidentialité de l’utilisateur|Oui|Oui|
||Accès au catalogue d’applications cloud complet|Oui|Oui|
||Évaluation des risques des applications cloud|Oui|Oui|
||Analytique de l’utilisation du cloud par application, utilisateur, adresse IP|Oui|Oui|
||Analytique et création de rapports en continu|Oui|Oui|
||Détection d’anomalie pour les applications découvertes|Oui||
|Protection des informations|Prise en charge de la protection contre la perte de données (DLP)|DLP multi-SaaS et contrôle du partage des données||
||Autorisations d’application et possibilité de révoquer l’accès|Oui||
||Paramètre et application de stratégies|Oui||
||Intégration à Azure Information Protection |Oui||
||Intégration à des solutions DLP tierces|Oui||
|Détection des menaces|Détection d’anomalies et analytique comportementale|Pour les applications multi-SaaS||
||Correction d’alerte automatique et manuelle|Oui||
||Connecteur SIEM|Oui. Alertes et journaux d’activité pour les applications multi-SaaS.||
||Intégration à Microsoft Intelligent Security Graph|Oui||
||Stratégies d’activité|Oui||

## <a name="next-steps"></a>Étapes suivantes

Découvrez les concepts de base dans [Bien démarrer avec Cloud App Security](getting-started-with-cloud-app-security.md).

[!INCLUDE [Open support ticket](includes/support.md)].
