---
title: Comment Cloud App Security vous aide à protéger votre environnement Dropbox
description: Cet article fournit des informations sur les avantages de la connexion de votre application Dropbox à Cloud App Security à l’aide du connecteur API pour la visibilité et le contrôle de l’utilisation.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: article
ms.date: 12/04/2019
ms.collection: M365-security-compliance
ms.openlocfilehash: 090aed9021a1323b99cd254d9d857bc9894ca87f
ms.sourcegitcommit: db5ec79d219dd6674939c872ace7cd2ca80860a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75190069"
---
# <a name="how-cloud-app-security-helps-protect-your-dropbox-environment"></a>Comment Cloud App Security vous aide à protéger votre environnement Dropbox

*S’applique à : Microsoft Cloud App Security*

En tant qu’outil de collaboration et de stockage de fichiers Cloud, Dropbox permet à vos utilisateurs de partager leurs documents au sein de votre organisation et de vos partenaires de façon rationalisée et efficace. Dropbox peut exposer vos données sensibles non seulement en interne, mais également aux collaborateurs externes, ou encore pire les rendre accessibles au public via un lien partagé. De tels incidents peuvent être causés par des acteurs malveillants ou par des employés ne connaissant pas le problème.

La connexion de Dropbox à Cloud App Security vous permet d’obtenir des informations plus détaillées sur les activités de vos utilisateurs, de détecter les menaces à l’aide de détections d’anomalies basées sur Machine Learning, de détections de protection des informations telles que la détection du partage d’informations externes et activation des contrôles de correction automatisée.

## <a name="main-threats"></a>Menaces principales

- Comptes compromis et menaces internes
- Fuite de données
- Sensibilisation à la sécurité insuffisante
- Programme malveillant
- Ransomware
- BYOD (Bring Your Own Device) non géré

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Comment Cloud App Security aide à protéger votre environnement

- [Détectez les menaces du Cloud, les comptes compromis et les Insiders malveillants](best-practices.md#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Découverte, classification, étiquetage et protection des données réglementées et sensibles stockées dans le Cloud](best-practices.md#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)
- [Appliquer des stratégies de conformité et DLP pour les données stockées dans le Cloud](best-practices.md#enforce-dlp-and-compliance-policies-for-data-stored-in-the-cloud)
- [Limiter l’exposition des données partagées et appliquer des stratégies de collaboration](best-practices.md#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
- [Utiliser la piste d’audit des activités pour des investigations d’investigation](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)

## <a name="control-dropbox-with-built-in-policies-and-policy-templates"></a>Contrôler Dropbox avec des stratégies intégrées et des modèles de stratégie

Vous pouvez utiliser les modèles de stratégie intégrés suivants pour détecter et vous avertir des menaces potentielles :

| Type | Nom |
| ---- | ---- |
| Stratégie de détection des anomalies intégrée | [Activité depuis des adresses IP anonymes](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses)<br />[Activité à partir de pays peu fréquents](anomaly-detection-policy.md#activity-from-infrequent-country)<br />[Activité à partir d’adresses IP suspectes](anomaly-detection-policy.md#activity-from-suspicious-ip-addresses)<br />[Voyage impossible](anomaly-detection-policy.md#impossible-travel)<br />[Activité effectuée par l’utilisateur terminé](anomaly-detection-policy.md#activity-performed-by-terminated-user) (requiert AAD comme IDP)<br />[Détection de programme malveillant](anomaly-detection-policy.md#malware-detection)<br />[Plusieurs tentatives de connexion infructueuses](anomaly-detection-policy.md#multiple-failed-login-attempts)<br />[Détection de ransomware](anomaly-detection-policy.md#ransomware-activity)<br />[Activités de suppression de fichiers inhabituelles](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Activités de partage de fichiers inhabituelles](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Activités de téléchargement de plusieurs fichiers inhabituelles](anomaly-detection-policy.md#unusual-activities-by-user) |
| Modèle de stratégie d’activité | Connexion à partir d’une adresse IP à risques<br />Téléchargement massif par un même utilisateur<br />Activité de ransomware potentielle |
| Modèle de stratégie de fichier | Détecter un fichier partagé avec un domaine non autorisé<br />Détecter un fichier partagé avec des adresses de messagerie personnelles<br />Détecter les fichiers avec PII/PCI/PHI |

Pour plus d’informations sur la création de stratégies, consultez [créer une stratégie](control-cloud-apps-with-policies.md#create-a-policy).

## <a name="automate-governance-controls"></a>Automatiser les contrôles de gouvernance

Outre la surveillance des menaces potentielles, vous pouvez appliquer et automatiser les actions de gouvernance Dropbox suivantes pour corriger les menaces détectées :

| Type | Action |
| ---- | ---- |
| Gouvernance des données | -Supprimer le lien partagé direct<br />-Envoyer le résumé de violation DLP aux propriétaires de fichiers<br />-Fichier Trash |
| Gouvernance des utilisateurs | -Notifier l’utilisateur en cas d’alerte (via Azure AD)<br /> -Exiger que l’utilisateur se connecte à nouveau (via Azure AD)<br /> -Suspendre l’utilisateur (via Azure AD) |

Pour plus d’informations sur la correction des menaces à partir des applications, consultez la rubrique relative aux [applications connectées](governance-actions.md).

## <a name="protect-dropbox-in-real-time"></a>Protéger Dropbox en temps réel

Passez en revue nos meilleures pratiques en matière de [sécurisation et de collaboration avec les utilisateurs externes](best-practices.md#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) , [bloquant et protégeant le téléchargement de données sensibles sur des appareils non gérés ou risqués](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Comment connecter Dropbox à Microsoft Cloud App Security](connect-dropbox-to-microsoft-cloud-app-security.md)
