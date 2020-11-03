---
title: Meilleures pratiques pour la protection de votre organisation - Cloud App Security
description: Cet article fournit un ensemble de meilleures pratiques pour la protection de votre organisation.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: quickstart
ms.date: 10/24/2019
ms.collection: M365-security-compliance
ms.openlocfilehash: a7c2dc834173dc212d783ba5853dff6186410e34
ms.sourcegitcommit: e711727f2f00ee3b54e08337a5040449e352ca46
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93185765"
---
# <a name="cloud-app-security-best-practices"></a>Meilleures pratiques pour Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Cet article présente les meilleures pratiques pour la protection de votre organisation à l’aide de Microsoft Cloud App Security. Ces meilleures pratiques sont issues de notre expérience avec Cloud App Security et des expériences de clients comme vous.

Les meilleures pratiques décrites dans cet article sont les suivantes :

> [!div class="checklist"]
> * [Découvrir et évaluer des applications cloud](#discover-and-assess-cloud-apps)
> * [Appliquer des stratégies de gouvernance cloud](#apply-cloud-governance-policies)
> * [Limiter l’exposition des données partagées et appliquer des stratégies de collaboration](#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
> * [Découvrir, classifier, étiqueter et protéger des données réglementées et sensibles stockées dans le cloud](#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)
> * [Appliquer des stratégies de conformité et DLP aux données stockées dans le cloud](#enforce-dlp-and-compliance-policies-for-data-stored-in-the-cloud)
> * [Bloquer et protéger le téléchargement de données sensibles sur des appareils non gérés ou à risque](#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices)
> * [Sécuriser votre collaboration avec les utilisateurs externes en appliquant des contrôles de session en temps réel](#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls)
> * [Détecter les menaces cloud, les comptes compromis, les insiders malveillants et les ransomware](#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
> * [Utiliser la piste d’audit des activités pour des investigations forensiques](#use-the-audit-trail-of-activities-for-forensic-investigations)
> * [Sécuriser les services IaaS et les applications personnalisées](#secure-iaas-services-and-custom-apps)

## <a name="discover-and-assess-cloud-apps"></a>Découvrir et évaluer des applications cloud

L’intégration de Cloud App Security avec Microsoft Defender - Protection avancée contre les menaces (Microsoft Defender ATP) vous donne la possibilité d’utiliser Cloud Discovery au-delà de votre réseau d’entreprise ou de passerelles web sécurisées. Avec les informations de l’utilisateur et de l’appareil combinées, vous pouvez identifier les utilisateurs et les appareils à risque, voir les applications qu’ils utilisent et approfondir vos recherches sur le portail Microsoft Defender ATP.

**Meilleure pratique**  : Activer Shadow IT Discovery à l’aide de Microsoft Defender ATP  
**Détail**  : Cloud Discovery analyse les journaux de trafic collectés par Microsoft Defender ATP et évalue les applications identifiées par rapport au catalogue d’applications cloud pour fournir des informations sur la conformité et la sécurité. En configurant Cloud Discovery, vous bénéficiez d’une visibilité sur l’utilisation du cloud, le Shadow IT et la surveillance continue des applications non approuvées utilisées par vos utilisateurs.  
**Pour plus d’informations**  :

* [Intégration de Microsoft Defender ATP à Cloud App Security](mde-integration.md)
* [Configurer Cloud Discovery](set-up-cloud-discovery.md)
* [Découvrir et gérer le Shadow IT dans votre réseau](tutorial-shadow-it.md)

---

**Meilleure pratique**  : Configurer des stratégies App Discovery pour identifier de manière proactive les applications risquées, non conformes et à la mode  
**Détails**  : Les stratégies App Discovery facilitent le suivi des applications significatives découvertes dans votre organisation pour vous aider à les gérer efficacement. Créez des stratégies pour recevoir des alertes lors de la détection de nouvelles applications identifiées comme risquées, non conformes, à la mode ou ayant un volume élevé.  
**Pour plus d’informations**  :

* [Stratégies Cloud Discovery](cloud-discovery-policies.md)
* [Stratégie de détection des anomalies Cloud Discovery](cloud-discovery-anomaly-detection-policy.md)
* [Obtenir instantanément une détection des anomalies et une analytique comportementale](anomaly-detection-policy.md)

---

**Meilleure pratique**  : Gérer les applications OAuth autorisées par vos utilisateurs  
**Détail**  : De nombreux utilisateurs accordent de manière occasionnelle des autorisations OAuth à des applications tierces pour accéder à leurs informations de compte et, par ce biais, ils donnent également accès à leurs données dans d’autres applications cloud par inadvertance. En règle générale, le service informatique n’a aucune visibilité sur ces applications, ce qui complique la pondération du risque de sécurité d’une application par rapport aux avantages de productivité qu’elle offre.

Cloud App Security vous offre la possibilité d’analyser et de surveiller les autorisations données à l’application par vos utilisateurs. Vous pouvez utiliser ces informations pour identifier une application potentiellement suspecte et, si vous déterminez qu’elle est risquée, vous pouvez y interdire l’accès.  
**Pour plus d’informations**  :

* [Gérer les applications OAuth](manage-app-permissions.md)
* [Stratégies d’application OAuth](app-permission-policy.md)

---
---
---
---

## <a name="apply-cloud-governance-policies"></a>Appliquer des stratégies de gouvernance cloud

**Meilleure pratique**  : Étiqueter des applications et exporter des scripts de blocage  
**Détail**  : Une fois que vous avez consulté la liste des applications découvertes dans votre organisation, vous pouvez sécuriser votre environnement contre toute utilisation d’application indésirable. Vous pouvez appliquer l’étiquette **Approuvée** aux applications approuvées par votre organisation et l’étiquette **Non approuvée** aux applications qui ne le sont pas. Vous pouvez surveiller les applications non approuvées à l’aide de filtres de découverte ou exporter un script pour bloquer les applications non approuvées à l’aide de vos appliances de sécurité locales. L’utilisation d’étiquettes et de scripts d’exportation vous permet d’organiser vos applications et de protéger votre environnement en n’autorisant l’accès qu’aux applications sécurisées.  
**Pour plus d’informations**  :

* [Gouverner les applications découvertes](governance-discovery.md)

---
---
---
---

## <a name="limit-exposure-of-shared-data-and-enforce-collaboration-policies"></a>Limiter l’exposition des données partagées et appliquer des stratégies de collaboration

**Meilleure pratique**  : Connecter Office 365  
**Détail**  : La connexion d’Office 365 à Cloud App Security vous offre une visibilité immédiate des activités de vos utilisateurs, des fichiers auxquels ils accèdent et fournit des actions de gouvernance pour Office 365, SharePoint, OneDrive, Teams, Power BI, Exchange et Dynamics.  
**Pour plus d’informations**  :

* [Connecter des applications](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)
* [Connecter Office 365 à Microsoft Cloud App Security](connect-office-365-to-microsoft-cloud-app-security.md)

---

**Meilleure pratique**  : Connecter des applications tierces  
**Détail**  : La connexion d’applications tierces à Cloud App Security vous offre des insights améliorés sur les activités des utilisateurs, la détection des menaces et les fonctionnalités de gouvernance. Les API d’applications tierces suivantes sont prises en charge : [Amazon Web Services (AWS)](connect-aws-to-microsoft-cloud-app-security.md), [Box](connect-box-to-microsoft-cloud-app-security.md), [Dropbox](connect-dropbox-to-microsoft-cloud-app-security.md), [G Suite](connect-google-apps-to-microsoft-cloud-app-security.md), [Okta](connect-okta-to-microsoft-cloud-app-security.md), [Salesforce](connect-salesforce-to-microsoft-cloud-app-security.md), [ServiceNow](connect-servicenow-to-microsoft-cloud-app-security.md), [WebEx](connect-webex-to-microsoft-cloud-app-security.md) et [Workday](connect-workday-to-microsoft-cloud-app-security.md).  
**Pour plus d’informations**  :

* [Connecter des applications](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)

---

**Meilleure pratique**  : Examiner l’exposition des données de votre organisation  
**Détail**  : Utilisez les rapports sur l’exposition des fichiers pour mieux comprendre comment vos utilisateurs partagent des fichiers avec des applications cloud. Les rapports suivants sont disponibles et peuvent être exportés pour une analyse plus poussée dans des outils tels que Microsoft Power BI :

* **Vue d’ensemble du partage des données**  : Répertorie, par autorisations d’accès, les fichiers stockés dans chacune de vos applications cloud
* **Partage sortant par domaine**  : Répertorie les domaines avec lesquels les fichiers d’entreprise sont partagés par vos employés
* **Propriétaires de fichiers partagés**  : Répertorie les utilisateurs qui partagent des fichiers d’entreprise avec le monde extérieur  
**Pour plus d’informations**  :

* [Générer des rapports de gestion des données](built-in-reports.md)

---

**Meilleure pratique**  : Créer des stratégies pour supprimer le partage avec des comptes personnels  
**Détail**  : La connexion d’Office 365 à Cloud App Security vous offre une visibilité immédiate des activités de vos utilisateurs, des fichiers auxquels ils accèdent et fournit des actions de gouvernance pour Office 365, SharePoint, OneDrive, Teams, Power BI, Exchange et Dynamics.  
**Pour plus d’informations**  :

* [Gouvernance des applications connectées](governance-actions.md)

---
---
---
---

## <a name="discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud"></a>Découvrir, classifier, étiqueter et protéger des données réglementées et sensibles stockées dans le cloud

**Meilleure pratique**  : Intégrer à Azure Information Protection  
**Détail**  : L’intégration à Azure Information Protection vous donne la possibilité d’appliquer automatiquement des étiquettes de classification et d’ajouter éventuellement une protection avec le chiffrement. Une fois l’intégration activée, vous pouvez appliquer des étiquettes en tant qu’action de gouvernance, afficher les fichiers par classification, analyser les fichiers par niveau de classification et créer des stratégies granulaires pour vous assurer que les fichiers classifiés sont correctement gérés. Si vous n’activez pas l’intégration, vous ne pouvez pas tirer parti de la possibilité d’analyser, d’étiqueter et de chiffrer automatiquement les fichiers dans le cloud.  
**Pour plus d’informations**  :

* [Intégration d’Azure Information Protection](azip-integration.md)
* [Tutoriel : Application automatique d’étiquettes de classification Azure Information Protection](use-case-information-protection.md)

---

**Meilleure pratique**  : Créer des stratégies d’exposition des données  
**Détail**  : Utilisez des stratégies de fichiers pour détecter le partage d’informations et rechercher des informations confidentielles dans vos applications cloud. Créez les stratégies de fichiers suivantes pour recevoir une alerte lorsque des expositions de données sont détectées :

* Fichiers contenant des données sensibles partagés en externe
* Fichiers dotés de l’étiquette **Confidentiel** partagés en externe
* Fichiers partagés avec des domaines non autorisés
* Protéger les fichiers sensibles sur des applications SaaS

**Pour plus d’informations**  :

* [Inspection du contenu](content-inspection.md)
* [Stratégies de fichier](data-protection-policies.md)
* [Stratégies de protection des informations](policies-information-protection.md)

---

**Meilleure pratique**  : Consulter les rapports dans la page **Fichiers**  
**Détail**  : Une fois que vous avez connecté plusieurs applications SaaS à l’aide de connecteurs d’application, Cloud App Security analyse les fichiers stockés par ces applications. En outre, chaque fois qu’un fichier est modifié, il est à nouveau analysé. Vous pouvez utiliser la page **Fichiers** pour comprendre et examiner les types de données stockées dans vos applications cloud. Pour vous aider, vous pouvez filtrer par domaines, groupes, utilisateurs, date de création, extension, nom et type de fichier, ID de fichier, étiquette de classification, et bien plus encore. L’utilisation de ces filtres vous permet de contrôler la façon dont vous choisissez d’examiner les fichiers pour vous assurer qu’aucune de vos données n’est menacée. Une fois que vous avez une meilleure compréhension de la façon dont vos données sont utilisées, vous pouvez créer des stratégies pour rechercher du contenu sensible dans ces fichiers.  
**Pour plus d’informations**  :

* [Connecter des applications](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)
* [Filtres de fichiers](file-filters.md)
* [Inspection du contenu](content-inspection.md)

---
---
---
---

## <a name="enforce-dlp-and-compliance-policies-for-data-stored-in-the-cloud"></a>Appliquer des stratégies de conformité et DLP aux données stockées dans le cloud

**Meilleure pratique**  : Protéger les données confidentielles contre le partage avec des utilisateurs externes  
**Détail**  : Créez une stratégie de fichier qui détecte quand un utilisateur tente de partager un fichier doté de l’étiquette de classification **Confidentiel** avec une personne externe à votre organisation, et configurez son action de gouvernance pour supprimer les utilisateurs externes. Cette stratégie garantit que vos données confidentielles ne sortent pas votre organisation et que les utilisateurs externes ne peuvent pas y accéder.  
**Pour plus d’informations**  :

* [Gouvernance des applications connectées](governance-actions.md)

---
---
---
---

## <a name="block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices"></a>Bloquer et protéger le téléchargement de données sensibles sur des appareils non gérés ou à risque

**Meilleure pratique**  : Gérer et contrôler l’accès aux appareils à haut risque  
**Détail**  : Utilisez le Contrôle d’application par accès conditionnel pour définir des contrôles sur vos applications SaaS. Vous pouvez créer des stratégies de session pour surveiller les sessions à haut risque et faible niveau de confiance. De même, vous pouvez créer des stratégies de session pour bloquer et protéger les téléchargements effectués par des utilisateurs qui essaient d’accéder à des données sensibles à partir d’appareils risqués ou non gérés. Si vous ne créez pas de stratégies de session pour surveiller les sessions à haut risque, vous perdez la possibilité de bloquer et de protéger les téléchargements dans le client web, ainsi que la possibilité de surveiller les sessions à faible niveau de confiance dans les applications Microsoft et tierces.  
**Pour plus d’informations**  :

* [Protéger les applications avec le contrôle d’application par accès conditionnel de Microsoft Cloud App Security](proxy-intro-aad.md)
* [Stratégies de session](session-policy-aad.md)

---
---
---
---

## <a name="secure-collaboration-with-external-users-by-enforcing-real-time-session-controls"></a>Sécuriser votre collaboration avec les utilisateurs externes en appliquant des contrôles de session en temps réel

**Meilleure pratique**  : Surveiller les sessions avec des utilisateurs externes à l’aide du Contrôle d’application par accès conditionnel  
**Détail**  : Pour sécuriser la collaboration dans votre environnement, vous pouvez créer une stratégie de session pour surveiller les sessions entre vos utilisateurs internes et externes. Cela vous permet non seulement de surveiller la session entre vos utilisateurs (et de les informer que leurs activités de session sont surveillées), mais également de limiter les activités spécifiques. Lorsque vous créez des stratégies de session pour surveiller l’activité, vous pouvez choisir les applications et les utilisateurs à surveiller.  
**Pour plus d’informations**  :

* [Protéger les applications avec le contrôle d’application par accès conditionnel de Microsoft Cloud App Security](proxy-intro-aad.md)
* [Stratégies de session](session-policy-aad.md)

---
---
---
---

## <a name="detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware"></a>Détecter les menaces cloud, les comptes compromis, les insiders malveillants et les ransomware

**Meilleure pratique**  : Paramétrer les stratégies d’anomalies, définir des plages d’adresses IP, envoyer des commentaires pour les alertes  
**Détail**  : Les stratégies de détection d’anomalie offrent des fonctionnalités d’analytique comportementale des utilisateurs et des entités (UEBA) et de Machine Learning (ML) prêtes à l’emploi, afin que vous puissiez exécuter immédiatement la détection avancée des menaces dans votre environnement cloud.

Les stratégies de détection d’anomalie sont déclenchées lorsque des activités inhabituelles sont effectuées par les utilisateurs dans votre environnement. Cloud App Security surveille en continu les activités de vos utilisateurs et utilise les fonctionnalités UEBA et ML pour apprendre et comprendre le comportement *normal* de vos utilisateurs. Vous pouvez paramétrer les paramètres de la stratégie selon les besoins de votre organisation. Par exemple, vous pouvez définir la sensibilité d’une stratégie et l’étendre à un groupe spécifique.

* **Paramétrage et étendue des stratégies de détection d’anomalie**  : Par exemple, pour réduire le nombre de faux positifs dans l’alerte de voyage impossible, vous pouvez définir le curseur de sensibilité de la stratégie sur faible. Si des utilisateurs au sein de votre organisation voyagent souvent pour leur travail, vous pouvez les ajouter à un groupe d’utilisateurs et sélectionner ce groupe dans l’étendue de la stratégie.

* **Définir des plages d’adresses IP**  : Cloud App Security peut identifier les adresses IP connues une fois que les plages d’adresses IP sont définies. Avec les plages d’adresses IP configurées, vous pouvez étiqueter, classer et personnaliser la manière dont les journaux et les alertes sont affichés et examinés. L’ajout de plages d’adresses IP permet de réduire les détections de faux positifs et d’améliorer la précision des alertes. Si vous choisissez de ne pas ajouter vos adresses IP, il est possible que le nombre de faux positifs et d’alertes à examiner augmente.

* **Envoyer des commentaires pour les alertes**

    Lorsque vous ignorez ou résolvez des alertes, veillez à envoyer des commentaires incluant la raison pour laquelle vous avez ignoré l’alerte ou la manière dont l’alerte a été résolue. Ces informations aident Cloud App Security à améliorer les alertes et à réduire les faux positifs.

**Pour plus d’informations**  :

* [Obtenir instantanément une détection des anomalies et une analytique comportementale](anomaly-detection-policy.md)
* [Utilisation des plages d’adresses IP et des étiquettes](ip-tags.md)
* [Surveiller les alertes dans Cloud App Security](monitor-alerts.md)

---

**Meilleure pratique**  : Détecter l’activité à partir d’emplacements ou de pays inattendus  
**Détail**  : Créez une stratégie d’activité pour recevoir une alerte quand des utilisateurs se connectent à partir d’emplacements ou de pays/régions inattendus. Ces notifications peuvent vous avertir de sessions potentiellement compromises dans votre environnement afin que vous puissiez détecter et corriger les menaces avant qu’elles ne se produisent.  
**Pour plus d’informations**  :

* [Stratégies de protection contre les menaces](policies-threat-protection.md)

---

**Meilleure pratique**  : Créer des stratégies d’application OAuth  
**Détail**  : Créez une stratégie d’application OAuth pour recevoir une alerte quand une application OAuth répond à certains critères. Par exemple, vous pouvez choisir de recevoir une alerte lorsque plus de 100 utilisateurs ont accédé à une application spécifique nécessitant un niveau d’autorisation élevé.  
**Pour plus d’informations**  :

* [Stratégies d’application OAuth](app-permission-policy.md)

---
---
---
---

## <a name="use-the-audit-trail-of-activities-for-forensic-investigations"></a>Utiliser la piste d’audit des activités pour des investigations forensiques

**Meilleure pratique**  : Utiliser la piste d’audit des activités lors de l’examen des alertes  
**Détail**  : Les alertes sont déclenchées lorsque les activités de l’utilisateur, de l’administrateur ou de connexion ne sont pas conformes à vos stratégies. Il est important d’examiner les alertes pour déterminer s’il existe une menace possible dans votre environnement.

Vous pouvez examiner une alerte en la sélectionnant dans la page **Alertes** et en examinant la piste d’audit des activités associée à cette alerte. La piste d’audit vous donne une vue d’ensemble des activités du même type, même utilisateur, même adresse IP et emplacement, afin de vous fournir l’histoire générale d’une alerte. Si une alerte justifie une investigation supplémentaire, créez un plan pour résoudre ces alertes dans votre organisation.

Lorsque vous ignorez des alertes, il est important d’examiner et de comprendre pourquoi elles ne sont pas importantes ou s’il s’agit de faux positifs. Si le volume de ces activités est élevé, vous pouvez également envisager d’examiner et de paramétrer la stratégie déclenchant l’alerte.  
**Pour plus d’informations**  :

* [Activités](activity-filters.md)

---
---
---
---

## <a name="secure-iaas-services-and-custom-apps"></a>Sécuriser les services IaaS et les applications personnalisées

**Meilleure pratique**  : Connecter Azure, AWS et GCP  
**Détail**  : La connexion de chacune de ces plateformes cloud à Cloud App Security vous aide à améliorer vos fonctionnalités de détection des menaces. En surveillant les activités d’administration et de connexion pour ces services, vous pouvez détecter et être informé des éventuelles attaques par force brute, de l’utilisation malveillante d’un compte d’utilisateur privilégié et d’autres menaces dans votre environnement. Par exemple, vous pouvez identifier les risques comme les suppressions inhabituelles de machines virtuelles ou même les activités d’emprunt d’identité dans ces applications.  
**Pour plus d’informations**  :

* [Connecter Azure à Microsoft Cloud App Security](connect-azure-to-microsoft-cloud-app-security.md)
* [Connecter AWS à Microsoft Cloud App Security](connect-aws-to-microsoft-cloud-app-security.md)
* [Connecter GCP à Microsoft Cloud App Security (préversion)](connect-google-gcp-to-microsoft-cloud-app-security.md)

---

**Meilleure pratique**  : Examiner les évaluations de la configuration de la sécurité pour Azure, AWS et GCP  
**Détail**  : L’intégration à Azure Security Center vous offre une évaluation de la configuration de la sécurité de votre environnement Azure. L’évaluation fournit des recommandations pour la configuration et le contrôle de sécurité manquants. L’examen de ces recommandations vous aide à identifier les anomalies et les vulnérabilités potentielles dans votre environnement, et à accéder directement à l’emplacement approprié dans le portail Azure Security pour les résoudre.

AWS et GCP vous donnent la possibilité d’obtenir une visibilité de vos recommandations en matière de configurations de la sécurité sur la façon d’améliorer la sécurité du cloud.

Utilisez ces recommandations pour surveiller l’état de la conformité et la posture de sécurité de toute votre organisation, notamment les abonnements Azure, les comptes AWS et les projets GCP.  
**Pour plus d’informations**  :

* [Configuration de la sécurité pour Azure](security-config.md)
* [Configuration de la sécurité pour AWS](security-config-aws.md)
* [Configuration de la sécurité pour GCP](security-config-gcp.md)

---

**Meilleure pratique**  : Intégrer des applications personnalisées  
**Détail**  : Pour obtenir une visibilité supplémentaire des activités de vos applications métier, vous pouvez intégrer des applications personnalisées à Cloud App Security. Une fois les applications personnalisées configurées, des informations sur les personnes qui les utilisent, les adresses IP à partir desquelles elles sont utilisées et la quantité de trafic entrant et sortant de l’application s’affichent.

En outre, vous pouvez intégrer une application personnalisée en tant qu’application de Contrôle d’application par accès conditionnel pour surveiller les sessions à faible niveau de confiance.  
**Pour plus d’informations**  :

* [Ajouter des applications personnalisées à Cloud Discovery](cloud-discovery-custom-apps.md)
* [Intégrer et déployer le Contrôle d’application par accès conditionnel pour tous les types d’applications](proxy-deployment-any-app.md)
