---
title: Intégrer Microsoft Defender for Identity avec Cloud App Security
description: Cet article fournit des informations sur l’utilisation de Microsoft Defender pour Identity Insights dans Cloud App Security pour la détection hybride des risques.
ms.date: 12/27/2020
ms.topic: how-to
ms.openlocfilehash: f1639d51b4d3bc82fe6002b96bdc62c983fe87d2
ms.sourcegitcommit: cfa59a538167bd126d64dbd05f04a1957bc035c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/27/2020
ms.locfileid: "97792668"
---
# <a name="microsoft-defender-for-identity-integration"></a>Intégration de Microsoft Defender pour Identity

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Microsoft Cloud App Security s’intègre à Microsoft Defender for Identity pour fournir l’analyse comportementale des entités utilisateur (UEBA) dans un environnement hybride (à la fois l’application Cloud et localement). pour plus d’informations, consultez [Didacticiel : étudier les utilisateurs à risque](tutorial-ueba.md). Pour plus d’informations sur le Machine Learning et l’analyse comportementale fournis par Defender pour l’identité, consultez [qu’est-ce que Defender pour l’identité ?](/defender-for-identity/what-is)

> [!NOTE]
> Cloud App Security n’envoie pas de notifications par courrier électronique à Defender pour les alertes d’identité. Toutefois, vous pouvez configurer des notifications par courrier électronique pour eux dans le portail d’identités Defender.

## <a name="prerequisites"></a>Prérequis

Pour procéder à un examen complet d’un utilisateur dans un environnement hybride, les éléments suivants sont nécessaires :

- Une licence valide pour Microsoft Defender pour l’identité connectée à votre instance Active Directory
- Vous devez être un administrateur général Azure Active Directory pour permettre l’intégration entre Defender pour l’identité et Cloud App Security

> [!NOTE]
>
> - Si vous n’avez pas d’abonnement pour Microsoft Cloud App Security, vous serez toujours en mesure d’utiliser Cloud App Security pour obtenir Defender pour Identity Insights.
> - Defender pour les administrateurs d’identité peut nécessiter de nouvelles autorisations pour accéder à Cloud App Security. Pour savoir comment attribuer des autorisations à Cloud App Security, consultez [Gérer l’accès administrateur](manage-admins.md).

## <a name="enable-defender-for-identity"></a>Activer Defender pour l’identité

Pour activer l’intégration d’Cloud App Security à Defender pour l’identité :

1. Dans Cloud App Security, sous l’roue dentée paramètres, sélectionnez **paramètres**.

    ![menu Paramètres](media/azip-system-settings.png)

1. Sous **protection contre les menaces**, sélectionnez **Microsoft Defender pour l’identité**.

    ![activer Azure-protection avancée contre les menaces](media/mdi-integration.png)

1. Sélectionnez **activer Microsoft Defender pour l’intégration des données d’identité** , puis cliquez sur **Enregistrer**.

> [!NOTE]
> Cela peut prendre jusqu’à 12 heures jusqu’à ce que l’intégration prenne effet.

Après avoir activé Defender pour l’intégration des identités, vous pouvez voir les activités locales pour tous les utilisateurs de votre organisation. Vous obtiendrez également des Insights avancés sur vos utilisateurs qui combinent des alertes et des activités suspectes dans vos environnements Cloud et locaux. En outre, les stratégies de Defender pour l’identité s’affichent sur la page stratégies de Cloud App Security. Pour obtenir la liste des stratégies de protection des identités, consultez [alertes de sécurité](/defender-for-identity/suspicious-activity-guide). Pour modifier ces stratégies, consultez [exclusion d’entités des détections](/defender-for-identity/excluding-entities-from-detections).

Vous devez également utiliser les liens de **configuration Defender for Identity** pour configurer Defender pour les paramètres d’identité qui sont pertinents pour Cloud App Security. Utilisez les informations suivantes pour en savoir plus sur ces paramètres :

- [Configurer Microsoft Defender pour les capteurs d’identité](/defender-for-identity/install-step5)
- [Configurer des comptes de service d’annuaire](/defender-for-identity/install-step2)
- [Configurer la gestion de comptes RADIUS pour VPN](/defender-for-identity/install-step6-vpn)
- [Accéder à Microsoft Defender pour Identity Health Center](/defender-for-identity/health-center)

## <a name="disable-defender-for-identity"></a>Désactiver Defender pour l’identité

Pour désactiver l’intégration de Cloud App Security à Defender pour l’identité :

1. Dans Cloud App Security, sous l’roue dentée paramètres, sélectionnez **paramètres**.

1. Sous **protection contre les menaces**, sélectionnez **Microsoft Defender pour l’identité**.

1. Désactivez **activer l’intégration des données d’identité dans Microsoft Defender** , puis cliquez sur **Enregistrer**.

> [!NOTE]
> Lorsque l’intégration est désactivée, l’application Defender existante pour les données d’identité est conservée conformément aux stratégies de rétention de Cloud App Security, mais la section d’évaluation de l’état de la sécurité des identités est supprimée.

## <a name="known-issues"></a>Problèmes connus

### <a name="missing-siem-alert-updates"></a>Mises à jour des alertes SIEM manquantes

Ce problème affecte plusieurs alertes déclenchées plusieurs fois. La première instance de l’alerte est envoyée à SIEM, mais les déclencheurs suivants de la même alerte ne sont pas envoyés.

#### <a name="resolution"></a>Résolution

Aucune solution connue.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]