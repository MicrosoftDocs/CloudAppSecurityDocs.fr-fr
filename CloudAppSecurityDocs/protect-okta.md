---
title: Comment Cloud App Security aide à protéger votre environnement Okta
description: Cet article fournit des informations sur les avantages de la connexion de votre application Okta à Cloud App Security à l’aide du connecteur API pour la visibilité et le contrôle de l’utilisation.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: article
ms.date: 12/04/2019
ms.collection: M365-security-compliance
ms.openlocfilehash: d62b7d9d91d5f627217caaccbec462aa20d2fcd2
ms.sourcegitcommit: db5ec79d219dd6674939c872ace7cd2ca80860a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75190089"
---
# <a name="how-cloud-app-security-helps-protect-your-okta-environment"></a>Comment Cloud App Security aide à protéger votre environnement Okta

*S’applique à : Microsoft Cloud App Security*

En tant que solution de gestion des identités et des accès, Okta contient les clés de la plupart des services critiques de votre organisation. Okta gère les processus d’authentification et d’autorisation pour vos utilisateurs et vos clients. Tout abus de Okta par un acteur malveillant ou toute erreur humaine peut exposer vos ressources et services les plus critiques à des attaques potentielles.

La connexion de Okta à Cloud App Security vous permet d’obtenir des informations améliorées sur vos activités d’administration Okta, les utilisateurs gérés et les compléments de Sigh des clients, et fournit une détection des menaces pour un comportement anormal.

## <a name="main-threats"></a>Menaces principales

- Comptes compromis et menaces internes

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Comment Cloud App Security aide à protéger votre environnement

- [Détectez les menaces du Cloud, les comptes compromis et les Insiders malveillants](best-practices.md#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Utiliser la piste d’audit des activités pour des investigations d’investigation](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)

## <a name="control-okta-with-built-in-policies-and-policy-templates"></a>Contrôler les Okta avec des stratégies intégrées et des modèles de stratégie

Vous pouvez utiliser les modèles de stratégie intégrés suivants pour détecter et vous avertir des menaces potentielles :

| Type | Nom |
| ---- | ---- |
| Stratégie de détection des anomalies intégrée | [Activité depuis des adresses IP anonymes](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses)<br />[Activité à partir de pays peu fréquents](anomaly-detection-policy.md#activity-from-infrequent-country)<br />[Activité à partir d’adresses IP suspectes](anomaly-detection-policy.md#activity-from-suspicious-ip-addresses)<br />[Voyage impossible](anomaly-detection-policy.md#impossible-travel)<br />[Plusieurs tentatives de connexion infructueuses](anomaly-detection-policy.md#multiple-failed-login-attempts)<br />[Détection de ransomware](anomaly-detection-policy.md#ransomware-activity)<br />[Activités administratives inhabituelles](anomaly-detection-policy.md#unusual-activities-by-user) |
| Modèle de stratégie d’activité | Connexion à partir d’une adresse IP à risques |

Pour plus d’informations sur la création de stratégies, consultez [créer une stratégie](control-cloud-apps-with-policies.md#create-a-policy).

## <a name="automate-governance-controls"></a>Automatiser les contrôles de gouvernance

Actuellement, il n’existe aucun contrôle de gouvernance disponible pour Okta. Si vous souhaitez avoir des actions de gouvernance pour ce connecteur, vous pouvez [Envoyer les commentaires de l’équipe Cloud App Security](support-and-ts.md#feedback) avec les détails des actions que vous souhaitez.

Pour plus d’informations sur la correction des menaces à partir des applications, consultez la rubrique relative aux [applications connectées](governance-actions.md).

## <a name="protect-okta-in-real-time"></a>Protéger Okta en temps réel

Passez en revue nos meilleures pratiques en matière de [sécurisation et de collaboration avec les utilisateurs externes](best-practices.md#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) , [bloquant et protégeant le téléchargement de données sensibles sur des appareils non gérés ou risqués](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Comment connecter Okta à Microsoft Cloud App Security](connect-okta-to-microsoft-cloud-app-security.md)
