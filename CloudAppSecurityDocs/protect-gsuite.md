---
title: Comment Cloud App Security aide à protéger votre environnement G suite
description: Cet article fournit des informations sur les avantages de la connexion de votre application G suite à Cloud App Security à l’aide du connecteur d’API pour la visibilité et le contrôle de l’utilisation.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: article
ms.date: 12/04/2019
ms.collection: M365-security-compliance
ms.openlocfilehash: 7eb22c2cb6ee0839f41bca963ec0e8c29a1a4905
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90877156"
---
# <a name="how-cloud-app-security-helps-protect-your-g-suite-environment"></a>Comment Cloud App Security aide à protéger votre environnement G suite

[!INCLUDE [Banner for top of topics](includes/banner.md)]

En tant qu’outil de collaboration et de stockage de fichiers Cloud, G suite permet à vos utilisateurs de partager leurs documents au sein de votre organisation et de vos partenaires de façon rationalisée et efficace. L’utilisation de G suite peut exposer vos données sensibles non seulement en interne, mais également aux collaborateurs externes, ou encore pire les rendre accessibles au public via un lien partagé. De tels incidents peuvent être causés par des acteurs malveillants ou par des employés ne connaissant pas le problème. G suite fournit également un grand système d’écosystème d’applications tiers pour améliorer la productivité. L’utilisation de ces applications peut exposer votre organisation au risque d’applications malveillantes ou d’utilisation d’applications avec des autorisations excessives.

La connexion de G suite à Cloud App Security vous permet d’améliorer l’analyse des activités de vos utilisateurs, de détecter les menaces à l’aide de détections d’anomalies basées sur Machine Learning, de détections de protection des informations (telles que la détection du partage d’informations externes), d’activer les contrôles de correction automatisée et de détecter les menaces des applications tierces activées dans votre organisation.

## <a name="main-threats"></a>Menaces principales

- Comptes compromis et menaces internes
- Fuite de données
- Sensibilisation à la sécurité insuffisante
- Applications tierces malveillantes et modules complémentaires Google
- Programme malveillant
- Ransomware
- BYOD (Bring Your Own Device) non géré

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Comment Cloud App Security aide à protéger votre environnement

- [Détectez les menaces du Cloud, les comptes compromis et les Insiders malveillants](best-practices.md#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Découvrir, classifier, étiqueter et protéger des données réglementées et sensibles stockées dans le cloud](best-practices.md#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)
- [Détecter et gérer les applications OAuth qui ont accès à votre environnement](manage-app-permissions.md)
- [Appliquer des stratégies de conformité et DLP aux données stockées dans le cloud](best-practices.md#enforce-dlp-and-compliance-policies-for-data-stored-in-the-cloud)
- [Limiter l’exposition des données partagées et appliquer des stratégies de collaboration](best-practices.md#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
- [Utiliser la piste d’audit des activités pour des investigations forensiques](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)

## <a name="control-g-suite-with-built-in-policies-and-policy-templates"></a>Contrôle G suite avec des stratégies intégrées et des modèles de stratégie

Vous pouvez utiliser les modèles de stratégie intégrés suivants pour détecter et vous avertir des menaces potentielles :

| Type | Nom |
| ---- | ---- |
| Stratégie de détection des anomalies intégrée | [Activité depuis des adresses IP anonymes](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses)<br />[Activité à partir de pays peu fréquents](anomaly-detection-policy.md#activity-from-infrequent-country)<br />[Activité à partir d'adresses IP suspectes](anomaly-detection-policy.md#activity-from-suspicious-ip-addresses)<br />[Voyage impossible](anomaly-detection-policy.md#impossible-travel)<br />[Activité effectuée par l’utilisateur terminé](anomaly-detection-policy.md#activity-performed-by-terminated-user) (requiert AAD comme IDP)<br />[Détection de logiciel malveillant](anomaly-detection-policy.md#malware-detection)<br />[Plusieurs tentatives de connexion infructueuses](anomaly-detection-policy.md#multiple-failed-login-attempts)<br />[Détection de ransomware](anomaly-detection-policy.md#ransomware-activity)<br />[Activités administratives inhabituelles](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Activités inhabituelles de suppression de fichiers](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Activités inhabituelles de partage de fichiers](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Activités inhabituelles de téléchargement de plusieurs fichiers](anomaly-detection-policy.md#unusual-activities-by-user) |
| Modèle de stratégie d’activité | Connexion à partir d’une adresse IP à risques<br />Téléchargement massif par un même utilisateur<br />Activité de ransomware potentielle |
| Modèle de stratégie de fichier | Détecter un fichier partagé avec un domaine non autorisé<br />Détecter un fichier partagé avec des adresses de messagerie personnelles<br />Détecter les fichiers avec PII/PCI/PHI |

Pour plus d’informations sur la création de stratégies, consultez [créer une stratégie](control-cloud-apps-with-policies.md#create-a-policy).

## <a name="automate-governance-controls"></a>Automatiser les contrôles de gouvernance

Outre la surveillance des menaces potentielles, vous pouvez appliquer et automatiser les actions de gouvernance G suite suivantes pour corriger les menaces détectées :

| Type | Action |
| ---- | ---- |
| Gouvernance des données | -Appliquer l’étiquette de classification Azure Information Protection<br />-Accorder l’autorisation de lecture au domaine<br />-Créer un fichier/dossier dans Google Drive privé<br />-Réduire l’accès public au fichier/dossier<br />-Supprimer un collaborateur d’un fichier<br />-Supprimer Azure Information Protection étiquette de classification<br />-Supprimer les collaborateurs externes du fichier/dossier<br />-Supprimer la capacité de l’éditeur de fichiers à partager<br />-Supprimer l’accès public au fichier/dossier<br />-Demander à l’utilisateur de réinitialiser le mot de passe sur Google<br />-Envoyer le résumé de violation DLP aux propriétaires de fichiers<br />-Envoyer une violation DLP au dernier éditeur de fichiers<br />-Transférer la propriété du fichier<br />-Fichier Trash |
| Gouvernance des utilisateurs | -Suspendre l’utilisateur<br />-Notifier l’utilisateur en cas d’alerte (via Azure AD)<br />-Exiger que l’utilisateur se connecte à nouveau (via Azure AD)<br />-Suspendre l’utilisateur (via Azure AD) |
| Gouvernance des applications OAuth | -Revoke-révoquer l’autorisation d’application OAuth |

Pour plus d’informations sur la correction des menaces à partir des applications, consultez la rubrique relative aux [applications connectées](governance-actions.md).

## <a name="protect-g-suite-in-real-time"></a>Protéger G suite en temps réel

Passez en revue nos meilleures pratiques en matière de [sécurisation et de collaboration avec les utilisateurs externes](best-practices.md#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) , [bloquant et protégeant le téléchargement de données sensibles sur des appareils non gérés ou risqués](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Comment connecter G suite à Microsoft Cloud App Security](connect-google-apps-to-microsoft-cloud-app-security.md)
