---
title: Différences entre les fonctionnalités de découverte de Cloud App Security et d’Azure AD
description: Cet article décrit les différences entre les fonctionnalités de découverte de Microsoft Cloud App Security et d’Azure AD.
ms.date: 02/22/2021
ms.topic: overview
ms.openlocfilehash: 4df6d4c918267866083253c1a4154e58aab8b6d9
ms.sourcegitcommit: db520402e669ac6c140eb3a67bdc8c9306ed4145
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/09/2021
ms.locfileid: "102512497"
---
# <a name="what-are-the-differences-in-discovery-capabilities-for-azure-active-directory-and-microsoft-cloud-app-security"></a>Différences entre les fonctionnalités de découverte d’Azure Active Directory et de Microsoft Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Cet article décrit les différences qui existent entre les fonctionnalités de découverte de Microsoft Cloud App Security et celles d’Azure Active Directory (Azure AD).

Pour plus d’informations sur les licences, consultez la fiche [Licences Microsoft Cloud App Security](https://aka.ms/mcaslicensing).

## <a name="microsoft-cloud-app-security"></a>Microsoft Cloud App Security

Microsoft Cloud App Security est une solution complète multi-SaaS qui offre à vos applications cloud une meilleure visibilité, des contrôles de données puissants et une protection améliorée contre les menaces. Cloud Discovery est une fonctionnalité Cloud App Security qui vous permet de mieux détecter le « Shadow IT » en découvrant les applications cloud qui sont en cours d’utilisation.

## <a name="enhanced-cloud-app-discovery-in-azure-active-directory"></a>Cloud App Discovery améliorée dans Azure Active Directory

[Azure Active Directory Cloud App Discovery](./set-up-cloud-discovery.md) est fourni gratuitement avec Azure Active Directory Premium P1. Cette fonctionnalité est basée sur celles de Microsoft Cloud App Security Cloud Discovery, qui offrent une meilleure visibilité des applications cloud utilisées dans votre organisation. [Effectuez une mise à niveau vers Microsoft Cloud App Security](https://www.microsoft.com/cloud-platform/cloud-app-security) pour bénéficier de la suite complète des fonctionnalités Cloud App Security Broker (CASB) proposées par Microsoft Cloud App Security.

### <a name="feature-comparison"></a>Comparaison des fonctionnalités

Le tableau suivant compare les fonctionnalités de découverte de Microsoft Cloud App Security à celles d’Azure AD.

|Fonctionnalité|Composant|Microsoft Cloud App Security|Azure AD Cloud App Discovery|
|----|----|----|----|
|Cloud Discovery|Applications découvertes|> 16 000 applications cloud|> 16 000 applications cloud|
||Déploiement pour l’analyse de la découverte|Chargement manuel et automatique des journaux|Chargement manuel et automatique des journaux. [En savoir plus sur la configuration de Cloud Discovery](set-up-cloud-discovery.md)|
||Anonymisation des journaux pour la protection des données personnelles des utilisateurs|Oui|Oui|
||Accès à l’ensemble du catalogue d’applications cloud|Oui|Oui|
||Analyse de risque des applications cloud|Oui|Oui|
||Analyse de l’utilisation du cloud selon les applications, les utilisateurs et les adresses IP|Oui|Oui|
||Analytique et rapports suivis|Oui|Oui|
||Détection d’anomalie pour les applications découvertes|Oui||
|Protection des informations|Prise en charge de la protection contre la perte de données (DLP)|Contrôle du partage de données et DLP inter-SaaS||
||Permissions d’application et possibilité de révoquer l’accès (applications OAuth)|Oui||
||Paramètre de stratégie et application|Oui||
||Intégration avec Azure Information Protection |Oui||
||Intégration avec des solutions DLP tierces|Oui||
|Détection des menaces|Détection d’anomalie et analyse comportementale|Pour les applications multi-SaaS||
||Correction manuelle et automatique des alertes|Oui||
||Connecteur SIEM|Oui. Alertes et journaux d’activité pour les applications inter-SaaS||
||Intégration à Microsoft Intelligent Security Graph|Oui||
||Stratégies des activités|Oui||

## <a name="next-steps"></a>Étapes suivantes

- Découvrez les concepts de base dans [Bien démarrer avec Cloud App Security](getting-started-with-cloud-app-security.md).

[!INCLUDE [Open support ticket](includes/support.md)].