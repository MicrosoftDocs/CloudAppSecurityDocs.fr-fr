---
title: Intégration supplémentaire avec Cloud App Security
description: Cet article fournit des informations sur l’intégration de solutions tierces avec Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 06/28/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 3d7d005940b032cd6e9b9f4bb5f1f3be13ababcb
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90880707"
---
# <a name="additional-integrations-with-external-solutions"></a>Intégrations supplémentaires avec des solutions externes

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Vous pouvez intégrer Microsoft Cloud App Security à vos autres investissements en matière de sécurité pour tirer parti et améliorer un écosystème intégré de protection. Par exemple, vous pouvez intégrer des solutions de gestion des appareils mobiles externes, des solutions UEBA et des flux d’informations sur les menaces externes.

La plateforme robuste de Cloud App Security vous permet de procéder à une intégration avec un large éventail de solutions de sécurité externes, notamment :

- **Flux d’intelligence des menaces (TI)**  
    Vous pouvez utiliser l' [API de plage d’adresses ip](api-data-enrichment.md) Cloud App Security pour ajouter de nouvelles plages d’adresses IP risquées identifiées par des solutions TI tierces. Une fois définis, les plages d’adresses IP vous permettent d’étiqueter, de classer et de personnaliser la façon dont les journaux et les alertes sont affichés et examinés.

- **Solutions de gestion des appareils mobiles (MDM)/mobile Threat Defense (MTD)**  
    Cloud App Security fournit des contrôles de session granulaires en temps réel. L’un des facteurs clés de l’évaluation et de la protection des sessions est l’appareil utilisé par l’utilisateur, qui permet de créer une identité complète. L’état de gestion d’un appareil peut être identifié directement par le biais de l’état de gestion des périphériques dans [Azure Active Directory (Azure AD)](/azure/active-directory/conditional-access/overview), [Microsoft Intune](/intune/mobile-threat-defense)ou plus de manière générique via l’analyse des certificats clients qui permettent l’intégration à une variété de solutions MDM et MTD tierces.

    Cloud App Security pouvez tirer parti des signaux des solutions MDM et MTD externes pour appliquer des contrôles de session en fonction de [l’état de gestion d’un appareil](proxy-intro-aad.md#managed-device-identification).

- **Solutions UEBA**  
    Vous pouvez utiliser plusieurs solutions UEBA pour répondre à différentes charges de travail et scénarios, où chaque solution UEBA s’appuie sur plusieurs sources de données pour identifier le comportement des utilisateurs suspects et anormaux. Les solutions UEBA externes peuvent être intégrées à l’écosystème de sécurité de Microsoft par le biais de Azure AD Identity Protection.

    Une fois intégré, les stratégies peuvent être utilisées pour identifier les utilisateurs risqués, appliquer des contrôles adaptatifs et corriger automatiquement les utilisateurs à risque en définissant le niveau de risque élevé de l’utilisateur. Une fois qu’un utilisateur est défini sur élevé, les actions de stratégie pertinentes sont appliquées, telles que la réinitialisation du mot de passe d’un utilisateur, la nécessité d’une authentification MFA ou la force d’un utilisateur à utiliser un appareil géré.

    Cloud App Security permet aux équipes de sécurité de confirmer automatiquement ou manuellement un utilisateur comme compromis, afin de garantir une correction rapide des utilisateurs compromis.

    Pour plus d’informations, consultez [comment Azure ad utiliser mes](/azure/active-directory/identity-protection/howto-identity-protection-risk-feedback#how-does-azure-ad-use-my-risk-feedback) actions de commentaires et de [gouvernance](accounts.md#governance-actions).

[!INCLUDE [Open support ticket](includes/support.md)]
