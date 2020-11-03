---
title: Comment Cloud App Security aide à protéger votre environnement d’équipes Cisco Webex
description: Cet article fournit des informations sur les avantages de la connexion de votre application Cisco Webex teams à Cloud App Security à l’aide du connecteur API pour la visibilité et le contrôle de l’utilisation.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: article
ms.date: 12/04/2019
ms.collection: M365-security-compliance
ms.openlocfilehash: 4061efcd3a0c03f8f57f8e9c0d36d7d1dfa5a678
ms.sourcegitcommit: 9391853beca4bd62e0f05bd457faac97e7dec646
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93278527"
---
# <a name="how-cloud-app-security-helps-protect-your-cisco-webex-teams-environment"></a>Comment Cloud App Security aide à protéger votre environnement d’équipes Cisco Webex

[!INCLUDE [Banner for top of topics](includes/banner.md)]

En tant que plateforme de communication et de collaboration, les équipes Cisco Webex permettent une communication et une collaboration rationalisées au sein de votre organisation. À l’aide de Cisco Webex pour vos données et de vos ressources, Exchange peut exposer vos informations d’organisation sensibles à des utilisateurs externes, par exemple dans les salles de conversation où ils peuvent également participer à une conversation avec vos employés.

La connexion des équipes Cisco Webex à Cloud App Security vous offre des informations améliorées sur les activités de vos utilisateurs, fournit des détections de protection des informations et active des contrôles de gouvernance automatisés.

## <a name="main-threats"></a>Menaces principales

- Comptes compromis et menaces internes
- Fuite de données
- Sensibilisation à la sécurité insuffisante
- Ransomware
- BYOD (Bring Your Own Device) non géré

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Comment Cloud App Security aide à protéger votre environnement

- [Appliquer des stratégies de conformité et DLP aux données stockées dans le cloud](best-practices.md#enforce-dlp-and-compliance-policies-for-data-stored-in-the-cloud)
- [Limiter l’exposition des données partagées et appliquer des stratégies de collaboration](best-practices.md#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
- [Utiliser la piste d’audit des activités pour des investigations forensiques](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)

## <a name="control-cisco-webex-teams-with-built-in-policies-and-policy-templates"></a>Contrôler les équipes Cisco Webex avec des stratégies intégrées et des modèles de stratégie

Vous pouvez utiliser les modèles de stratégie intégrés suivants pour détecter et vous avertir des menaces potentielles :

| Type | Nom |
| ---- | ---- |
| Stratégie de détection des anomalies intégrée | [Activité effectuée par l’utilisateur terminé](anomaly-detection-policy.md#activity-performed-by-terminated-user) (requiert AAD comme IDP)<br />[Plusieurs tentatives de connexion infructueuses](anomaly-detection-policy.md#multiple-failed-login-attempts)<br />[Détection de ransomware](anomaly-detection-policy.md#ransomware-activity)<br />[Activités inhabituelles de suppression de fichiers](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Activités inhabituelles de partage de fichiers](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Activités inhabituelles de téléchargement de plusieurs fichiers](anomaly-detection-policy.md#unusual-activities-by-user) |
| Modèle de stratégie de fichier | Détecter un fichier partagé avec un domaine non autorisé<br />Détecter un fichier partagé avec des adresses de messagerie personnelles<br />Détecter les fichiers avec PII/PCI/PHI |
| Modèle de stratégie d’activité | Téléchargement massif par un même utilisateur<br />Activité de ransomware potentielle |

Pour plus d’informations sur la création de stratégies, consultez [créer une stratégie](control-cloud-apps-with-policies.md#create-a-policy).

## <a name="automate-governance-controls"></a>Automatiser les contrôles de gouvernance

Outre la surveillance des menaces potentielles, vous pouvez appliquer et automatiser les actions de gouvernance des équipes Cisco Webex suivantes pour corriger les menaces détectées :

| Type | Action |
| ---- | ---- |
| Gouvernance des utilisateurs | -Notifier l’utilisateur en cas d’alerte (via Azure AD)<br />-Exiger que l’utilisateur se connecte à nouveau (via Azure AD)<br />-Suspendre l’utilisateur (via Azure AD) |
| Gouvernance des données | -Fichier Trash |

Pour plus d’informations sur la correction des menaces à partir des applications, consultez la rubrique relative aux [applications connectées](governance-actions.md).

## <a name="protect-cisco-webex-teams-in-real-time"></a>Protégez les équipes Cisco Webex en temps réel

Passez en revue nos meilleures pratiques en matière de [sécurisation et de collaboration avec les utilisateurs externes](best-practices.md#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) , [bloquant et protégeant le téléchargement de données sensibles sur des appareils non gérés ou risqués](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Comment connecter des équipes Cisco Webex à Microsoft Cloud App Security](connect-webex-to-microsoft-cloud-app-security.md)
