---
title: Comment Cloud App Security aide à protéger votre environnement Office 365
description: Découvrez les avantages de la connexion de votre application Office 365 à Cloud App Security à l’aide du connecteur API pour la visibilité et le contrôle de l’utilisation.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: article
ms.date: 12/04/2019
ms.collection: M365-security-compliance
ms.openlocfilehash: e640fbd96b91bb19fa0f9b70ce4eff603d48308a
ms.sourcegitcommit: 98c8dd439d1183af3d8598c676c8ff041a88bd88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89667119"
---
# <a name="how-cloud-app-security-helps-protect-your-office-365-environment"></a>Comment Cloud App Security aide à protéger votre environnement Office 365

*S’applique à : Microsoft Cloud App Security*

En tant que suite de productivité majeure fournissant un stockage de fichiers Cloud, des outils de collaboration, DÉCISIONNELs et CRM, Office 365 permet à vos utilisateurs de partager leurs documents au sein de votre organisation et de vos partenaires de manière rationalisée et efficace. L’utilisation d’Office 365 peut exposer vos données sensibles non seulement en interne, mais également aux collaborateurs externes, ou encore pire les rendre accessibles au public via un lien partagé. De tels incidents peuvent se produire en raison d’un acteur malveillant ou d’un employé ne connaissant pas. Office 365 fournit également un grand système d’écosystème d’applications tiers pour améliorer la productivité. L’utilisation de ces applications peut exposer votre organisation au risque d’applications malveillantes ou d’utilisation d’applications avec des autorisations excessives.

La connexion d’Office 365 à Cloud App Security vous permet d’améliorer l’analyse des activités de vos utilisateurs, de détecter les menaces à l’aide de détections d’anomalies basées sur Machine Learning, de détections de protection des informations (telles que la détection du partage d’informations externes), d’activer des contrôles de correction automatisée et de détecter les menaces des applications tierces activées dans votre organisation.

L’utilisation du connecteur Office 365 fournit une protection pour les produits suivants :

- Dynamics 365 CRM
- Exchange
- Office 365
- OneDrive
- Power Automate
- Power BI
- SharePoint
- Skype Entreprise
- Teams
- Yammer

> [!NOTE]
> Cloud App Security s’intègre directement avec les [journaux d’audit d’Office 365](/microsoft-365/compliance/detailed-properties-in-the-office-365-audit-log?view=o365-worldwide&preserve-view=true) et reçoit tous les événements audités de **tous les services pris en charge**, tels que powerapps, Forms, Sway et Stream.

## <a name="main-threats"></a>Menaces principales

- Comptes compromis et menaces internes
- Fuite de données
- Sensibilisation à la sécurité insuffisante
- Applications tierces malveillantes
- Programme malveillant
- Hameçonnage
- Ransomware
- BYOD (Bring Your Own Device) non géré

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Comment Cloud App Security aide à protéger votre environnement

- [Détectez les menaces du Cloud, les comptes compromis et les Insiders malveillants](best-practices.md#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Découvrir, classifier, étiqueter et protéger des données réglementées et sensibles stockées dans le cloud](best-practices.md#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)
- [Détecter et gérer les applications OAuth qui ont accès à votre environnement](manage-app-permissions.md)
- [Appliquer des stratégies de conformité et DLP aux données stockées dans le cloud](best-practices.md#enforce-dlp-and-compliance-policies-for-data-stored-in-the-cloud)
- [Limiter l’exposition des données partagées et appliquer des stratégies de collaboration](best-practices.md#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
- [Utiliser la piste d’audit des activités pour des investigations forensiques](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)

## <a name="control-office-365-with-built-in-policies-and-policy-templates"></a>Contrôler Office 365 avec des stratégies intégrées et des modèles de stratégie

Vous pouvez utiliser les modèles de stratégie intégrés suivants pour détecter et vous avertir des menaces potentielles :

| Type | Nom |
| ---- | ---- |
| Stratégie de détection des anomalies intégrée | [Activité depuis des adresses IP anonymes](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses)<br />[Activité à partir de pays peu fréquents](anomaly-detection-policy.md#activity-from-infrequent-country)<br />[Activité à partir d'adresses IP suspectes](anomaly-detection-policy.md#activity-from-suspicious-ip-addresses)<br />[Voyage impossible](anomaly-detection-policy.md#impossible-travel)<br />[Activité effectuée par l’utilisateur terminé](anomaly-detection-policy.md#activity-performed-by-terminated-user) (nécessite Azure AD comme IDP)<br />[Détection de logiciel malveillant](anomaly-detection-policy.md#malware-detection)<br />[Plusieurs tentatives de connexion infructueuses](anomaly-detection-policy.md#multiple-failed-login-attempts)<br />[Détection de ransomware](anomaly-detection-policy.md#ransomware-activity)<br />[Activité suspecte de suppression d’e-mails (préversion)](anomaly-detection-policy.md#suspicious-email-deletion-activity-preview)<br />[Boîte de réception suspecte transférant](anomaly-detection-policy.md#suspicious-inbox-forwarding)des[activités de suppression de fichiers inhabituels](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Activités inhabituelles de partage de fichiers](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Activités inhabituelles de téléchargement de plusieurs fichiers](anomaly-detection-policy.md#unusual-activities-by-user) |
| Modèle de stratégie d’activité | Connexion à partir d’une adresse IP à risques<br />Téléchargement massif par un même utilisateur<br />Activité de ransomware potentielle<br />Modification du niveau d’accès (équipes)<br />Utilisateur externe ajouté (équipes)<br />Suppression en masse (équipes) |
| Modèle de stratégie de fichier | Détecter un fichier partagé avec un domaine non autorisé<br />Détecter un fichier partagé avec des adresses de messagerie personnelles<br />Détecter les fichiers avec PII/PCI/PHI |
| Stratégie de détection des anomalies d’application OAuth | [Nom d’application OAuth trompeur](app-permission-policy.md#oauth-app-anomaly-detection-policies)<br />[Nom du serveur de publication trompeur pour une application OAuth](app-permission-policy.md#oauth-app-anomaly-detection-policies)<br />[Consentement de l’application OAuth malveillante](app-permission-policy.md#oauth-app-anomaly-detection-policies) |

Pour plus d’informations sur la création de stratégies, consultez [créer une stratégie](control-cloud-apps-with-policies.md#create-a-policy).

## <a name="automate-governance-controls"></a>Automatiser les contrôles de gouvernance

Outre la surveillance des menaces potentielles, vous pouvez appliquer et automatiser les actions de gouvernance Office 365 suivantes pour corriger les menaces détectées :

| Type | Action |
| ---- | ---- |
| Gouvernance des données | **Espace**<br /> -Hériter des autorisations du dossier parent<br /> -Rendre privé le fichier/dossier<br /> -Placer le fichier/dossier dans la quarantaine administrateur<br /> -Placer le fichier/dossier en quarantaine utilisateur<br /> -Fichier/dossier de la corbeille<br /> -Supprimer un collaborateur spécifique<br /> -Supprimer les collaborateurs externes du fichier/dossier<br /> -Appliquer l’étiquette de classification Azure Information Protection<br /> -Supprimer Azure Information Protection étiquette de classification<br /> **SharePoint**<br /> -Hériter des autorisations du dossier parent<br /> -Rendre privé le fichier/dossier<br /> -Placer le fichier/dossier dans la quarantaine administrateur<br /> -Placer le fichier/dossier en quarantaine utilisateur<br /> -Placer le fichier/dossier en quarantaine utilisateur et ajouter des autorisations de propriétaire<br /> -Fichier/dossier de la corbeille<br /> -Supprimer les collaborateurs externes du fichier/dossier<br /> -Supprimer un collaborateur spécifique<br /> -Appliquer l’étiquette de classification Azure Information Protection<br /> -Supprimer Azure Information Protection étiquette de classification |
| Gouvernance des utilisateurs | -Notifier l’utilisateur en cas d’alerte (via Azure AD)<br /> -Exiger que l’utilisateur se connecte à nouveau (via Azure AD)<br /> -Suspendre l’utilisateur (via Azure AD) |
| Gouvernance des applications OAuth | -Revoke-révoquer l’autorisation d’application OAuth |

Pour plus d’informations sur la correction des menaces à partir des applications, consultez la rubrique relative aux [applications connectées](governance-actions.md).

## <a name="protect-office-365-in-real-time"></a>Protégez Office 365 en temps réel

Passez en revue nos meilleures pratiques en matière de [sécurisation et de collaboration avec les utilisateurs externes](best-practices.md#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) , [bloquant et protégeant le téléchargement de données sensibles sur des appareils non gérés ou risqués](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Comment connecter Office 365 à Microsoft Cloud App Security](connect-office-365-to-microsoft-cloud-app-security.md)