---
title: Intégrer Cloud App Security avec la sécurité Menlo
description: Cet article explique comment intégrer Microsoft Cloud App Security avec la sécurité Menlo pour une Cloud Discovery transparente et un bloc automatisé d’applications non approuvées.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/09/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 79d4e986632e33475be75a808244dc6a61226df5
ms.sourcegitcommit: 288f3011c0ce0e5f2d8cbaa9057a63be044465f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94377746"
---
# <a name="integrate-cloud-app-security-with-menlo-security"></a>Intégrer Cloud App Security avec la sécurité Menlo

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Si vous travaillez avec la sécurité Cloud App Security et Menlo, vous pouvez intégrer les deux produits pour améliorer votre expérience de Cloud Discovery de sécurité. La sécurité Menlo, en tant que passerelle Web sécurisée autonome, surveille le trafic de votre organisation, ce qui vous permet de définir des stratégies pour bloquer les transactions. Ensemble, Cloud App Security et la sécurité Menlo offrent les fonctionnalités suivantes :

- Le déploiement sans heurts de Cloud Discovery la sécurité Menlo pour transmettre votre trafic par proxy et l’envoyer à Cloud App Security. Cela vous évite d’avoir à installer des collecteurs de journaux sur vos points de terminaison réseau pour activer Cloud Discovery.
- Les fonctionnalités de bloc de sécurité Menlo sont appliquées automatiquement sur les applications que vous définissez comme non approuvées dans Cloud App Security.

## <a name="prerequisites"></a>Prérequis

- Une licence valide pour Microsoft Cloud App Security ou une licence valide pour Azure Active Directory Premium P1
- Une licence valide pour la sécurité Menlo

## <a name="deployment"></a>Déploiement

1. Connectez-vous à votre portail d’administration Menlo et utilisez l’intégration de la [sécurité Menlo avec Microsoft Cloud Guide d’installation](https://admin.menlosecurity.com/docs/guides/web_admin_settings_casb.html?highlight=microsoft) de la sécurité d’accès pour intégrer les produits.

1. Examinez les applications cloud découvertes sur votre réseau. Pour plus d’informations et de méthodes d’examen, consultez la page [Utilisation de Cloud Discovery](working-with-cloud-discovery-data.md).
1. Toutes les applications que vous définissez comme non approuvées dans Cloud App Security sont interrogées par la sécurité Menlo toutes les deux heures, puis bloquées automatiquement par Menlo Security. Pour plus d’informations sur la non-approbation des applications, consultez [Approbation/non-approbation d’une application](governance-discovery.md#BKMK_SanctionApp).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
