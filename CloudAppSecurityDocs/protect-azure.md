---
title: Comment Cloud App Security aide à protéger votre environnement Azure
description: Cet article fournit des informations sur les avantages de la connexion de votre application Azure à Cloud App Security à l’aide du connecteur API pour la visibilité et le contrôle de l’utilisation.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: article
ms.date: 12/04/2019
ms.collection: M365-security-compliance
ms.openlocfilehash: f6638891b8a3dbd75fe103bac7042b572c647e1a
ms.sourcegitcommit: db5ec79d219dd6674939c872ace7cd2ca80860a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75190059"
---
# <a name="how-cloud-app-security-helps-protect-your-azure-environment"></a>Comment Cloud App Security aide à protéger votre environnement Azure

*S’applique à : Microsoft Cloud App Security*

Azure est un fournisseur IaaS qui permet à votre organisation d’héberger et de gérer leurs charges de travail entières dans le Cloud. Outre les avantages liés à l’utilisation de l’infrastructure dans le Cloud, les ressources les plus critiques de votre organisation peuvent être exposées aux menaces. Les ressources exposées incluent des instances de stockage avec des informations potentiellement sensibles, des ressources de calcul qui exploitent certaines de vos applications, ports et réseaux privés virtuels les plus critiques, qui permettent d’accéder à votre organisation.

La connexion d’Azure à Cloud App Security vous permet de sécuriser vos ressources et de détecter les menaces potentielles en surveillant les activités d’administration et de connexion, en notifiant les éventuelles attaques par force brute, l’utilisation malveillante d’un compte d’utilisateur privilégié et les suppressions inhabituelles de VMS.

## <a name="main-threats"></a>Menaces principales

- Abus des ressources du Cloud
- Comptes compromis et menaces internes
- Fuite de données
- Configuration insuffisante des ressources et contrôle d’accès insuffisant

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Comment Cloud App Security aide à protéger votre environnement

- [Détectez les menaces du Cloud, les comptes compromis et les Insiders malveillants](best-practices.md#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Limiter l’exposition des données partagées et appliquer des stratégies de collaboration](best-practices.md#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
- [Utiliser la piste d’audit des activités pour des investigations d’investigation](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)

## <a name="control-azure-with-built-in-policies-and-policy-templates"></a>Contrôler Azure avec des stratégies intégrées et des modèles de stratégie

Vous pouvez utiliser les modèles de stratégie intégrés suivants pour détecter et vous avertir des menaces potentielles :

| Type | Nom |
| ---- | ---- |
| Stratégie de détection des anomalies intégrée | [Activité depuis des adresses IP anonymes](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses)<br />[Activité à partir de pays peu fréquents](anomaly-detection-policy.md#activity-from-infrequent-country)<br />[Activité à partir d’adresses IP suspectes](anomaly-detection-policy.md#activity-from-suspicious-ip-addresses)<br />[Activité effectuée par l’utilisateur terminé](anomaly-detection-policy.md#activity-performed-by-terminated-user) (requiert AAD comme IDP)<br />[Plusieurs tentatives de connexion infructueuses](anomaly-detection-policy.md#multiple-failed-login-attempts)<br />[Activités administratives inhabituelles](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Activités de suppression de plusieurs stockages inhabituelles](anomaly-detection-policy.md#unusual-activities-by-user) (version préliminaire)<br />[Plusieurs activités de suppression de machine virtuelle](anomaly-detection-policy.md#multiple-delete-vm-activities)<br />[Activités de création de plusieurs machines virtuelles inhabituelles](anomaly-detection-policy.md#unusual-activities-by-user) (version préliminaire) |

Pour plus d’informations sur la création de stratégies, consultez [créer une stratégie](control-cloud-apps-with-policies.md#create-a-policy).

## <a name="automate-governance-controls"></a>Automatiser les contrôles de gouvernance

Outre la surveillance des menaces potentielles, vous pouvez appliquer et automatiser les actions de gouvernance Azure suivantes pour corriger les menaces détectées :

| Type | Action |
| ---- | ---- |
| Gouvernance des utilisateurs | -Notifier l’utilisateur en cas d’alerte (via Azure AD)<br />-Exiger que l’utilisateur se connecte à nouveau (via Azure AD)<br />-Suspendre l’utilisateur (via Azure AD) |

Pour plus d’informations sur la correction des menaces à partir des applications, consultez la rubrique relative aux [applications connectées](governance-actions.md).

## <a name="protect-azure-in-real-time"></a>Protéger Azure en temps réel

Passez en revue nos meilleures pratiques en matière de [sécurisation et de collaboration avec les utilisateurs externes](best-practices.md#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) , [bloquant et protégeant le téléchargement de données sensibles sur des appareils non gérés ou risqués](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Connexion d’Azure à Microsoft Cloud App Security](connect-azure-to-microsoft-cloud-app-security.md)
