---
title: Différences entre Cloud App Security et la Sécurité des applications cloud Office 365
description: Cet article décrit les différences entre Cloud App Security et la Sécurité des applications cloud Office 365.
ms.date: 02/22/2021
ms.topic: overview
ms.openlocfilehash: 60ceb6a9d2415b66b371d24089f487163552750f
ms.sourcegitcommit: db520402e669ac6c140eb3a67bdc8c9306ed4145
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/09/2021
ms.locfileid: "102512378"
---
# <a name="what-are-the-differences-between-microsoft-cloud-app-security-and-office-365-cloud-app-security"></a>Différences entre Microsoft Cloud App Security et la Sécurité des applications cloud Office 365

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Cet article décrit les différences entre Cloud App Security et la Sécurité des applications cloud Office 365. Pour plus d’informations sur la Sécurité des applications cloud Office 365, consultez [Bien démarrer avec la Sécurité des applications cloud Office 365](https://support.office.com/article/Get-started-with-Advanced-Management-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a).

Pour plus d’informations sur les licences, consultez la fiche [Licences Microsoft Cloud App Security](https://aka.ms/mcaslicensing).

## <a name="microsoft-cloud-app-security"></a>Microsoft Cloud App Security

Microsoft Cloud App Security est une solution inter-SaaS complète qui offre une visibilité approfondie, des contrôles de données renforcés et une protection améliorée contre les menaces pour les applications cloud. Ce service permet de mieux visualiser l’informatique fantôme en détectant les applications cloud en cours d’utilisation. Vous pouvez contrôler et protéger les données des applications une fois celles-ci approuvées dans le service.

## <a name="office-365-cloud-app-security"></a>Sécurité des applications cloud Office 365

La Sécurité des applications cloud Office 365 est un sous-ensemble de Microsoft Cloud App Security qui assure une visibilité et un contrôle accrus pour Office 365. Office 365 Cloud App Security comprend la détection des menaces basée sur les journaux d’activité des utilisateurs, la découverte de l’informatique fantôme pour les applications qui ont des fonctionnalités similaires aux produits Office 365, le contrôle des autorisations d’applications dans Office 365 ainsi que des contrôles d’application d’accès et de session.

### <a name="feature-support"></a>Prise en charge des fonctionnalités

|Fonctionnalité|Composant|Microsoft Cloud App Security|Sécurité des applications cloud Office 365|
|----|----|----|----|
|Cloud Discovery|Applications découvertes |> 16 000 applications cloud  |> 750 applications cloud avec des fonctionnalités similaires à Office 365|
||Déploiement pour l’analyse de la découverte|Chargement manuel et automatique des journaux|Chargement manuel des journaux|
||Anonymisation des journaux pour la protection des données personnelles des utilisateurs|Oui||
||Accès à l’ensemble du catalogue d’applications cloud|Oui||
||Analyse de risque des applications cloud|Oui||
||Analyse de l’utilisation du cloud selon les applications, les utilisateurs et les adresses IP|Oui||
||Analytique et rapports suivis|Oui||
||Détection d’anomalie pour les applications découvertes|Oui||
|Protection des informations|Prise en charge de la protection contre la perte de données (DLP)|Contrôle du partage de données et DLP inter-SaaS|Utilisation de la fonctionnalité DLP existante d’Office (disponible dans Office E3 et les versions ultérieures)|
||Permissions d’application et possibilité de révoquer l’accès|Oui|Oui|
||Paramètre de stratégie et application|Oui||
||Intégration avec Azure Information Protection |Oui||
||Intégration avec des solutions DLP tierces|Oui||
|Détection des menaces|Détection d’anomalie et analyse comportementale|Pour les applications inter-SaaS, y compris Office 365|Pour les applications Office 365 |
||Correction manuelle et automatique des alertes|Oui|Oui|
||Connecteur SIEM|Oui. Alertes et journaux d’activité pour les applications inter-SaaS|Pour les alertes Office 365 uniquement|
||Intégration à Microsoft Intelligent Security Graph|Oui|Oui|
||Stratégies des activités|Oui|Oui|
|Contrôle d’application par accès conditionnel|Surveillance et contrôle des sessions en temps réel|Toute application cloud ou locale|Pour les applications Office 365|
|Sécurité des plateformes cloud|Configurations de la sécurité|Pour Azure, AWS et GCP|Pour Azure|

## <a name="next-steps"></a>Étapes suivantes

- Découvrez les concepts de base dans [Bien démarrer avec Cloud App Security](getting-started-with-cloud-app-security.md).

[!INCLUDE [Open support ticket](includes/support.md)].
