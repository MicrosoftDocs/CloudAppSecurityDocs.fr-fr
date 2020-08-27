---
title: Intégrer Azure-protection avancée contre les menaces avec Cloud App Security
description: Cet article fournit des informations sur la façon d’exploiter Azure Advanced Threat Protection Insights dans Cloud App Security pour la détection hybride des risques.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/24/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 33ccea97fd5b41802d7f8b12fe7413c5bd76d8a6
ms.sourcegitcommit: 870ca47381a36b4bc04e1ccb9b2a522944431fed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88963588"
---
# <a name="azure-advanced-threat-protection-integration"></a>Intégration d’Azure-protection avancée contre les menaces

*S’applique à : Microsoft Cloud App Security*

Microsoft Cloud App Security s’intègre à Azure-protection avancée contre les menaces (Azure ATP) pour fournir une analyse comportementale des entités utilisateur (UEBA) dans un environnement hybride (à la fois dans l’application Cloud et localement). pour plus d’informations, consultez [Didacticiel : étudier les utilisateurs à risque](tutorial-ueba.md). Pour plus d’informations sur les Machine Learning et l’analyse comportementale fournis par Azure ATP, consultez [qu’est-ce que Azure ATP ?](/azure-advanced-threat-protection/what-is-atp)

## <a name="prerequisites"></a>Prérequis

Pour procéder à un examen complet d’un utilisateur dans un environnement hybride, les éléments suivants sont nécessaires :

- Licence valide pour Azure ATP connectée à votre instance Active Directory
- Vous devez être un administrateur général Azure Active Directory pour permettre l’intégration entre Azure ATP et Cloud App Security

> [!NOTE]
>
> - Si vous n’avez pas d’abonnement pour Microsoft Cloud App Security, vous serez toujours en mesure d’utiliser Cloud App Security pour obtenir Azure ATP Insights.
> - Les administrateurs Azure ATP peuvent avoir besoin de nouvelles autorisations pour accéder à Cloud App Security. Pour savoir comment attribuer des autorisations à Cloud App Security, consultez [Gérer l’accès administrateur](manage-admins.md).

## <a name="enable-azure-atp"></a>Activer Azure ATP

Pour activer l’intégration de Cloud App Security avec Azure ATP :

1. Dans Cloud App Security, sous l’roue dentée paramètres, sélectionnez **paramètres**.

    ![menu Paramètres](media/azip-system-settings.png)

1. Sous **protection contre les menaces**, sélectionnez **Azure ATP**.

    ![activer Azure-protection avancée contre les menaces](media/aatp-integration.png)

1. Sélectionnez **activer l’intégration des données Azure ATP** , puis cliquez sur **Enregistrer**.

> [!NOTE]
> Cela peut prendre jusqu’à 12 heures jusqu’à ce que l’intégration prenne effet.

Après l’activation de l’intégration de Azure ATP, vous pouvez voir les activités locales pour tous les utilisateurs de votre organisation. Vous obtiendrez également des Insights avancés sur vos utilisateurs qui combinent des alertes et des activités suspectes dans vos environnements Cloud et locaux. En outre, les stratégies de Azure ATP s’affichent sur la page stratégies Cloud App Security. Pour obtenir la liste des stratégies de Azure ATP, consultez [alertes de sécurité](/azure-advanced-threat-protection/suspicious-activity-guide).

Vous devez également utiliser les liens de **configuration Azure ATP** pour configurer les paramètres Azure ATP qui sont pertinents pour Cloud App Security. Utilisez les informations suivantes pour en savoir plus sur ces paramètres :

- [Configurer des capteurs Azure ATP](/azure-advanced-threat-protection/install-atp-step5)
- [Configurer des comptes de service d’annuaire](/azure-advanced-threat-protection/install-atp-step2)
- [Configurer la gestion de comptes RADIUS pour VPN](/azure-advanced-threat-protection/install-atp-step6-vpn)
- [Centre d’intégrité des Azure ATP d’accès](/azure-advanced-threat-protection/atp-health-center)

## <a name="disable-azure-atp"></a>Désactiver les Azure ATP

Pour désactiver l’intégration Cloud App Security avec Azure ATP :

1. Dans Cloud App Security, sous l’roue dentée paramètres, sélectionnez **paramètres**.

1. Sous **protection contre les menaces**, sélectionnez **Azure ATP**.

1. Désactivez **activer l’intégration des données Azure ATP** , puis cliquez sur **Enregistrer**.

> [!NOTE]
> Lorsque l’intégration est désactivée, les données Azure ATP existantes sont conservées conformément aux stratégies de rétention de Cloud App Security, mais la section d’évaluation de l’état de la sécurité des identités est supprimée.

## <a name="known-issues"></a>Problèmes connus

### <a name="missing-siem-alert-updates"></a>Mises à jour des alertes SIEM manquantes

Ce problème affecte plusieurs alertes déclenchées plusieurs fois. La première instance de l’alerte est envoyée à SIEM, mais les déclencheurs suivants de la même alerte ne sont pas envoyés.

#### <a name="resolution"></a>Solution

Aucune solution connue.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]