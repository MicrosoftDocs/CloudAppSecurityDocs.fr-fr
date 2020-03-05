---
title: Comment Cloud App Security aide à protéger votre environnement de jours ouvrés
description: Cet article fournit des informations sur les avantages de la connexion de votre application de jour de travail à Cloud App Security à l’aide du connecteur d’API pour la visibilité et le contrôle de l’utilisation.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: article
ms.date: 12/04/2019
ms.collection: M365-security-compliance
ms.openlocfilehash: 9ee405188d0f338bfe43ca9a08730baa6054a844
ms.sourcegitcommit: 582779b75be41e57fb1d773d1cf01f6b8598521e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78274641"
---
# <a name="how-cloud-app-security-helps-protect-your-workday-environment"></a>Comment Cloud App Security aide à protéger votre environnement de jours ouvrés

*S’applique à : Microsoft Cloud App Security*

En tant que solution HCM majeure, la journée de travail contient certaines des informations les plus sensibles de votre organisation, telles que les données personnelles des employés, les contrats, les détails des fournisseurs, etc. La prévention de l’exposition de ces données nécessite une surveillance continue pour empêcher les acteurs malveillants ou les Insiders de sécurité de dévoiler les informations sensibles.

La connexion de la journée de travail à Cloud App Security vous permet d’obtenir des informations plus détaillées sur les activités de vos utilisateurs et de détecter les menaces pour un comportement anormal.

## <a name="main-threats"></a>Menaces principales

- Comptes compromis et menaces internes
- Fuite de données
- Sensibilisation à la sécurité insuffisante
- BYOD (Bring Your Own Device) non géré

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Comment Cloud App Security aide à protéger votre environnement

- [Détectez les menaces du Cloud, les comptes compromis et les Insiders malveillants](best-practices.md#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Utiliser la piste d’audit des activités pour des investigations d’investigation](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)

## <a name="control-workday-with-built-in-policies-and-policy-templates"></a>Contrôle de la journée de travail avec des stratégies intégrées et des modèles de stratégie

Vous pouvez utiliser les modèles de stratégie intégrés suivants pour détecter et vous avertir des menaces potentielles :

| Type | Nom |
| ---- | ---- |
| Stratégie de détection des anomalies intégrée | [Activité à partir d’adresses IP anonymes](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses)<br />[Activité à partir d’un pays peu fréquent](anomaly-detection-policy.md#activity-from-infrequent-country)<br />[Activité à partir d’adresses IP suspectes](anomaly-detection-policy.md#activity-from-suspicious-ip-addresses)<br />[Voyage impossible](anomaly-detection-policy.md#impossible-travel) |
| Modèle de stratégie d’activité | Connexion à partir d’une adresse IP à risque |

Pour plus d’informations sur la création de stratégies, consultez [créer une stratégie](control-cloud-apps-with-policies.md#create-a-policy).

## <a name="automate-governance-controls"></a>Automatiser les contrôles de gouvernance

Actuellement, il n’existe aucun contrôle de gouvernance disponible pour les jours ouvrés. Si vous souhaitez avoir des actions de gouvernance pour ce connecteur, vous pouvez [Envoyer les commentaires de l’équipe Cloud App Security](support-and-ts.md#feedback) avec les détails des actions que vous souhaitez.

Pour plus d’informations sur la correction des menaces à partir des applications, consultez la rubrique relative aux [applications connectées](governance-actions.md).

## <a name="protect-workday-in-real-time"></a>Protéger la journée de travail en temps réel

Passez en revue nos meilleures pratiques en matière de [sécurisation et de collaboration avec les utilisateurs externes](best-practices.md#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) , [bloquant et protégeant le téléchargement de données sensibles sur des appareils non gérés ou risqués](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## <a name="next-steps"></a>Étapes suivantes :

> [!div class="nextstepaction"]
> [Connexion de la journée de travail à Microsoft Cloud App Security](connect-workday-to-microsoft-cloud-app-security.md)
