---
title: Intégrer Azure-protection avancée contre les menaces avec Cloud App Security
description: Cet article fournit des informations sur la façon d’exploiter Azure Advanced Threat Protection Insights dans Cloud App Security pour la détection hybride des risques.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/19/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: c38ccba7b6d9729ebdd80f005d9630270726d209
ms.sourcegitcommit: d493fc811a68387398615ff6288a300bb1f0fce7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75310393"
---
# <a name="azure-advanced-threat-protection-integration"></a>Intégration d’Azure-protection avancée contre les menaces

*S’applique à : Microsoft Cloud App Security* git Microsoft Cloud App Security s’intègre à Azure-protection avancée contre les menaces (Azure ATP) pour fournir l’analyse comportementale des entités utilisateur (UEBA) dans un environnement hybride (à la fois l’application Cloud et l’application locale). pour plus d’informations, consultez [Didacticiel : examiner les utilisateurs à risque](tutorial-ueba.md). Pour plus d’informations sur les Machine Learning et l’analyse comportementale fournis par Azure ATP, consultez [qu’est-ce que Azure ATP ?](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp)

## <a name="prerequisites"></a>Conditions préalables

Pour procéder à un examen complet d’un utilisateur dans un environnement hybride, les éléments suivants sont nécessaires :

- Licence valide pour Azure ATP connectée à votre instance Active Directory
- Vous devez être un administrateur général Azure Active Directory pour permettre l’intégration entre Azure ATP et Cloud App Security

> [!NOTE]
>
> - Si vous n’avez pas d’abonnement pour Microsoft Cloud App Security, vous serez toujours en mesure d’utiliser Cloud App Security pour obtenir Azure ATP Insights.
> - Azure ATP administrateurs peuvent avoir besoin de nouvelles autorisations pour accéder à Cloud App Security. Pour savoir comment assigner des autorisations à des Cloud App Security, consultez [gérer l’accès administrateur](manage-admins.md).

## <a name="enable-azure-atp"></a>Activer Azure ATP

Pour activer l’intégration de Cloud App Security avec Azure ATP :

1. Dans Cloud App Security, sous l’roue dentée paramètres, sélectionnez **paramètres**.

    ![Menu paramètres](media/azip-system-settings.png)

1. Sous **protection contre les menaces**, sélectionnez **Azure ATP**.

    ![activer Azure-protection avancée contre les menaces](media/aatp-integration.png)

1. Sélectionnez **se connecter Azure ATP données, notamment les alertes et les activités avec Cloud App Security** puis cliquez sur **Enregistrer**.

> [!NOTE]
> Cela peut prendre jusqu’à 12 heures jusqu’à ce que l’intégration prenne effet.

Après l’activation de l’intégration de Azure ATP, vous pouvez voir les activités locales pour tous les utilisateurs de votre organisation. Vous obtiendrez également des Insights avancés sur vos utilisateurs qui combinent des alertes et des activités suspectes dans vos environnements Cloud et locaux. En outre, les stratégies de Azure ATP s’affichent sur la page stratégies Cloud App Security. Pour obtenir la liste des stratégies de Azure ATP, consultez [alertes de sécurité](https://docs.microsoft.com/azure-advanced-threat-protection/suspicious-activity-guide).

## <a name="disable-azure-atp"></a>Désactiver les Azure ATP

Pour désactiver l’intégration Cloud App Security avec Azure ATP :

1. Dans Cloud App Security, sous l’roue dentée paramètres, sélectionnez **paramètres**.

1. Sous **protection contre les menaces**, sélectionnez **Azure ATP**.

1. Désactivez **connexion Azure ATP données, notamment les alertes et les activités avec Cloud App Security** puis cliquez sur **Enregistrer**.

> [!NOTE]
> Les données Azure ATP existantes sont conservées conformément aux stratégies de rétention de Cloud App Security, mais les évaluations de la sécurité des identités sont supprimées.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
