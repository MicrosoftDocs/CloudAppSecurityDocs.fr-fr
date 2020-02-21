---
title: Comment Cloud App Security aide à protéger votre environnement Salesforce
description: Cet article fournit des informations sur les avantages de la connexion de votre application Salesforce à Cloud App Security à l’aide du connecteur API pour la visibilité et le contrôle de l’utilisation.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: article
ms.date: 12/04/2019
ms.collection: M365-security-compliance
ms.openlocfilehash: 3f3aef39e134e34c46bc97a559bc3c19d4434f84
ms.sourcegitcommit: 6e266262b9b54e991acb8230a04e865628820557
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77495701"
---
# <a name="how-cloud-app-security-helps-protect-your-salesforce-environment"></a>Comment Cloud App Security aide à protéger votre environnement Salesforce

*S’applique à : Microsoft Cloud App Security*

En tant que fournisseur de Cloud CRM majeur, Salesforce intègre de grandes quantités d’informations sensibles sur les clients, des règles de tarification et des demandes majeures au sein de votre organisation. En tant qu’application critique pour l’entreprise, Salesforce est accessible et utilisé par des personnes au sein de votre organisation et par d’autres personnes en dehors de celui-ci (par exemple, des partenaires et des sous-traitants) à différentes fins. Dans de nombreux cas, une grande partie de vos utilisateurs qui accèdent à Salesforce n’ont pas conscience de la sécurité et peuvent mettre vos informations sensibles à risque en les partageant par inadvertance. Dans d’autres cas, les acteurs malveillants peuvent accéder à vos ressources les plus sensibles liées aux clients.

La connexion de Salesforce à Cloud App Security vous permet d’améliorer l’analyse des activités de vos utilisateurs, de détecter les menaces à l’aide de détections d’anomalies basées sur Machine Learning et de détections de protection des informations (telles que la détection d’informations externes). partage), active les contrôles de correction automatisée et détecte les menaces des applications tierces activées dans votre organisation.

## <a name="main-threats"></a>Menaces principales

- Comptes compromis et menaces internes
- Fuite de données
- Privilèges élevés
- Sensibilisation à la sécurité insuffisante
- Applications tierces malveillantes et modules complémentaires Google
- Ransomware
- BYOD (Bring Your Own Device) non géré

## <a name="how-cloud-app-security-helps-to-protect-your-environment"></a>Comment Cloud App Security aide à protéger votre environnement

- [Détectez les menaces du Cloud, les comptes compromis et les Insiders malveillants](best-practices.md#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Découverte, classification, étiquetage et protection des données réglementées et sensibles stockées dans le Cloud](best-practices.md#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)
- [Détecter et gérer les applications OAuth qui ont accès à votre environnement](manage-app-permissions.md)
- [Appliquer des stratégies de conformité et DLP pour les données stockées dans le Cloud](best-practices.md#enforce-dlp-and-compliance-policies-for-data-stored-in-the-cloud)
- [Limiter l’exposition des données partagées et appliquer des stratégies de collaboration](best-practices.md#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
- [Utiliser la piste d’audit des activités pour des investigations d’investigation](best-practices.md#use-the-audit-trail-of-activities-for-forensic-investigations)

## <a name="control-salesforce-with-built-in-policies-and-policy-templates"></a>Contrôler Salesforce avec des stratégies intégrées et des modèles de stratégie

Vous pouvez utiliser les modèles de stratégie intégrés suivants pour détecter et vous avertir des menaces potentielles :

| Type | Nom |
| ---- | ---- |
| Stratégie de détection des anomalies intégrée | [Activité à partir d’adresses IP anonymes](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses)<br />[Activité à partir d’un pays peu fréquent](anomaly-detection-policy.md#activity-from-infrequent-country)<br />[Activité à partir d’adresses IP suspectes](anomaly-detection-policy.md#activity-from-suspicious-ip-addresses)<br />[Voyage impossible](anomaly-detection-policy.md#impossible-travel)<br />[Activité effectuée par l’utilisateur terminé](anomaly-detection-policy.md#activity-performed-by-terminated-user) (requiert AAD comme IDP)<br />[Plusieurs tentatives de connexion ayant échoué](anomaly-detection-policy.md#multiple-failed-login-attempts)<br />[Détection de ransomware](anomaly-detection-policy.md#ransomware-activity)<br />[Activités administratives inhabituelles](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Activités de suppression de fichiers inhabituelles](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Activités de partage de fichiers inhabituelles](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Activités d’emprunt d’identité inhabituelles](anomaly-detection-policy.md#unusual-activities-by-user)<br />[Activités de téléchargement de plusieurs fichiers inhabituelles](anomaly-detection-policy.md#unusual-activities-by-user) |
| Modèle de stratégie d’activité | Connexion à partir d’une adresse IP à risque<br />Téléchargement en masse par un seul utilisateur<br />Activité potentielle de ransomware |
| Modèle de stratégie de fichier | Détecter un fichier partagé avec un domaine non autorisé<br />Détecter un fichier partagé avec des adresses de messagerie personnelles<br />Détecter les fichiers avec PII/PCI/PHI |

Pour plus d’informations sur la création de stratégies, consultez [créer une stratégie](control-cloud-apps-with-policies.md#create-a-policy).

## <a name="automate-governance-controls"></a>Automatiser les contrôles de gouvernance

Outre la surveillance des menaces potentielles, vous pouvez appliquer et automatiser les actions de gouvernance Salesforce suivantes pour corriger les menaces détectées :

| Type | Action |
| ---- | ---- |
| Gouvernance des utilisateurs | -Notifier les utilisateurs des alertes en attente<br />-Envoyer le résumé de violation DLP aux propriétaires de fichiers<br />-Suspendre l’utilisateur<br />-Notifier l’utilisateur en cas d’alerte (via Azure AD)<br />-Exiger que l’utilisateur se connecte à nouveau (via Azure AD)<br />-Suspendre l’utilisateur (via Azure AD) |
| Gouvernance des applications OAuth | -Révoquer l’application OAuth pour les utilisateurs |

Pour plus d’informations sur la correction des menaces à partir des applications, consultez la rubrique relative aux [applications connectées](governance-actions.md).

## <a name="protect-salesforce-in-real-time"></a>Protéger Salesforce en temps réel

Passez en revue nos meilleures pratiques en matière de [sécurisation et de collaboration avec les utilisateurs externes](best-practices.md#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) , [bloquant et protégeant le téléchargement de données sensibles sur des appareils non gérés ou risqués](best-practices.md#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## <a name="next-steps"></a>Étapes suivantes :

> [!div class="nextstepaction"]
> [Comment connecter Salesforce à Microsoft Cloud App Security](connect-salesforce-to-microsoft-cloud-app-security.md)
