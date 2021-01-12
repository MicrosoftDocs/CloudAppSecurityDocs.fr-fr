---
title: Ligne de base de sécurité Azure pour Microsoft Cloud App Security
description: Le Microsoft Cloud App Security la ligne de base de sécurité fournit des instructions et des ressources pour la mise en œuvre des recommandations de sécurité spécifiées dans le test de sécurité Azure.
author: msmbaldwin
ms.service: cloud-app-security
ms.topic: conceptual
ms.date: 12/03/2020
ms.author: mbaldwin
ms.custom: subject-security-benchmark
ms.openlocfilehash: 0c659e0682cef4239bb5fe6d07b1cea84247b1a5
ms.sourcegitcommit: 0768aa1992819e2651a14a731f79e178fdececc5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98114681"
---
# <a name="azure-security-baseline-for-microsoft-cloud-app-security"></a>Ligne de base de sécurité Azure pour Microsoft Cloud App Security

Cette ligne de base de sécurité applique des instructions du [test de sécurité Azure version 2,0](/azure/security/benchmarks/overview) à Microsoft Cloud App Security. Le benchmark de sécurité Azure fournit des recommandations sur la façon dont vous pouvez sécuriser vos solutions cloud sur Azure. Le contenu est regroupé en fonction des **contrôles de sécurité** définis par le test de sécurité Azure et des conseils associés à Microsoft Cloud App Security. Les **contrôles** non applicables aux Microsoft Cloud App Security ont été exclus.

Pour voir comment Microsoft Cloud App Security est entièrement mappé au test de sécurité Azure, consultez le fichier de mappage de la [ligne de base de sécurité Microsoft Cloud App Security complète](https://github.com/MicrosoftDocs/SecurityBenchmarks/tree/master/Azure%20Offer%20Security%20Baselines).

## <a name="network-security"></a>Sécurité réseau

*Pour plus d’informations, consultez [Benchmark de sécurité Azure : sécurité réseau](/azure/security/benchmarks/security-controls-v2-network-security).*

### <a name="ns-6-simplify-network-security-rules"></a>NS-6 : Simplifier les règles de sécurité réseau

**Aide**: utilisez les balises de service de réseau virtuel Azure pour définir les contrôles d’accès réseau sur les groupes de sécurité réseau ou le pare-feu Azure configuré pour vos ressources cloud App Security. Vous pouvez utiliser des balises de service à la place des adresses IP spécifiques lors de la création de règles de sécurité. En spécifiant le nom de balise de service (par exemple : « MicrosoftCloudAppSecurity ») dans le champ source ou de destination approprié d’une règle, vous pouvez autoriser ou refuser le trafic pour le service correspondant. Microsoft gère les préfixes d’adresse englobés par la balise de service et met à jour automatiquement la balise de service quand les adresses changent.

- [Présentation et usage des balises de service](/azure/virtual-network/service-tags-overview)

**Supervision d’Azure Security Center** : actuellement non disponible

**Responsabilité** : Customer

## <a name="identity-management"></a>Gestion des identités

*Pour plus d’informations, consultez [Benchmark de sécurité Azure : Gestion des identités](/azure/security/benchmarks/security-controls-v2-identity-management).*

### <a name="im-1-standardize-azure-active-directory-as-the-central-identity-and-authentication-system"></a>IM-1 : Normaliser Azure Active Directory comme système d’authentification et d’identité central

**Guide**: Cloud App Security utilise Azure Active Directory (Azure AD) comme service de gestion des identités et des accès par défaut. Vous devez normaliser Azure AD pour régir la gestion des identités et des accès de votre organisation dans :

- Les ressources cloud Microsoft, comme le portail Azure, le stockage Azure, les machines virtuelles Azure (Linux et Windows), les applications Azure Key Vault, PaaS et SaaS.

- Les ressources de votre organisation, comme les applications sur Azure ou les ressources réseau de votre entreprise.

La sécurisation d’Azure AD doit être d’une priorité élevée dans les pratiques de sécurité cloud de votre organisation. Azure AD fournit un score d'identité sécurisée pour vous aider à évaluer la sécurité des identités par rapport aux recommandations de Microsoft en matière de meilleures pratiques. Utilisez le score pour évaluer avec précision votre configuration par rapport aux meilleures pratiques recommandées et apporter des améliorations à votre posture de sécurité.

Remarque : Azure AD prend en charge l’identité externe, ce qui permet aux utilisateurs sans compte Microsoft de se connecter à leurs applications et ressources avec leur identité externe.

- [Locataires dans Azure Active Directory](/azure/active-directory/develop/single-and-multi-tenant-apps) 

- [Création et configuration d’une instance Azure AD](/azure/active-directory/fundamentals/active-directory-access-create-new-tenant) 

- [Utilisez des fournisseurs d'identité externes pour l’application](/azure/active-directory/b2b/identity-providers) 

- [Qu’est-ce que le degré de sécurisation Identity Secure Score dans Azure Active Directory](/azure/active-directory/fundamentals/identity-secure-score)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="im-3-use-azure-ad-single-sign-on-sso-for-application-access"></a>IM-3 : Utiliser l’authentification unique Azure AD pour l’accès aux applications

**Guide**: Cloud App Security utilise Azure Active Directory (Azure AD) pour assurer la gestion des identités et des accès aux ressources Azure, aux applications Cloud et aux applications locales. Cela inclut les identités d’entreprise, comme les employés, ainsi que les identités externes, comme les partenaires et les fournisseurs. Cela permet à l’authentification unique de gérer et sécuriser l’accès aux données et ressources de votre organisation localement et dans le cloud. Connectez tous vos utilisateurs, applications et appareils au Azure AD pour un accès transparent et sécurisé, ainsi qu’une visibilité et un contrôle accrus.

- [Comprendre l’authentification unique des applications avec Azure AD](/azure/active-directory/manage-apps/what-is-single-sign-on)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="im-4-use-strong-authentication-controls-for-all-azure-active-directory-based-access"></a>IM-4 : Utiliser des contrôles d’authentification renforcés pour tous les accès basés sur Azure Active Directory

**Guide**: Cloud App Security utilise Azure Active Directory (Azure AD) qui prend en charge des contrôles d’authentification forte grâce à l’authentification multifacteur et à l’authentification par mot de passe.

- Authentification multifacteur : activez Azure AD l’authentification multifacteur et suivez Azure Security Center recommandations de gestion des identités et des accès pour la configuration de l’authentification multifacteur. L’authentification multifacteur peut être appliquée à tous les utilisateurs, sélectionner des utilisateurs ou un niveau par utilisateur en fonction des conditions de connexion et des facteurs de risque.

- Authentification sans mot de passe – Trois options d’authentification sans mot de passe sont disponibles : Windows Hello Entreprise, l’application Microsoft Authenticator et les méthodes d’authentification locales, comme les cartes à puce.

Pour les utilisateurs administrateurs et privilégiés, assurez-vous que le niveau le plus élevé de méthode d’authentification forte est utilisé, puis déployez la stratégie d’authentification forte appropriée pour les autres utilisateurs.

- [Comment activer l’authentification multifacteur dans Azure](/azure/active-directory/authentication/howto-mfa-getstarted) 

- [Introduction aux options d’authentification sans mot de passe pour Azure Active Directory](/azure/active-directory/authentication/concept-authentication-passwordless) 

- [Stratégie de mot de passe par défaut d’Azure AD](/azure/active-directory/authentication/concept-sspr-policy#password-policies-that-only-apply-to-cloud-user-accounts) 

- [Éliminer les mauvais mots de passe à l’aide de Protection de mots de passe d’Azure AD](/azure/active-directory/authentication/concept-password-ban-bad)

**Supervision d’Azure Security Center** : Oui

**Responsabilité** : Customer

### <a name="im-6-restrict-azure-resource-access-based-on-conditions"></a>IM-6 : Restreindre l’accès aux ressources Azure en fonction des conditions

**Guide**: Cloud App Security prend en charge l’accès conditionnel Azure Active Directory (Azure AD) pour un contrôle d’accès plus granulaire en fonction des conditions définies par l’utilisateur, telles que les connexions utilisateur de certaines plages d’adresses IP doivent utiliser l’authentification multifacteur pour la connexion. Vous pouvez également utiliser des stratégies de gestion des sessions d’authentification granulaires pour différents cas d’usage.

- [Protection du Contrôle d’accès conditionnel aux applications](what-is-cloud-app-security.md#conditional-access-app-control-protection)

- [Présentation de l’accès conditionnel Azure](/azure/active-directory/conditional-access/overview) 

- [Stratégies d’accès conditionnel courantes](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) 

- [Configurer la gestion des sessions d’authentification avec l’accès conditionnel](/azure/active-directory/conditional-access/howto-conditional-access-session-lifetime)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

## <a name="privileged-access"></a>Accès privilégié

*Pour plus d’informations, consultez [Benchmark de sécurité Azure : Accès privilégié](/azure/security/benchmarks/security-controls-v2-privileged-access).*

### <a name="pa-1-protect-and-limit-highly-privileged-users"></a>PA-1 : Protéger et limiter les utilisateurs disposant de privilèges élevés

**Guide**: Cloud App Security possède les comptes à privilèges élevés suivants :

- Administrateur général et Administrateur de la sécurité : les administrateurs avec un Accès total disposent d’autorisations complètes dans Cloud App Security. Ils peuvent ajouter des administrateurs, ajouter des stratégies et des paramètres, charger des journaux et effectuer des actions de gouvernance.
- Administrateur de conformité : dispose d’autorisations en lecture seule et peut gérer les alertes. Impossible d’accéder aux recommandations de sécurité pour les plateformes Cloud. Peut créer et modifier des stratégies de fichier, autoriser des actions de gouvernance de fichier et afficher tous les rapports intégrés sous Gestion des données.
- Administrateur des données de conformité : dispose d’autorisations en lecture seule, peut créer et modifier des stratégies de fichier, autoriser des actions de gouvernance de fichiers et afficher tous les rapports de découverte. Impossible d’accéder aux recommandations de sécurité pour les plateformes Cloud.
- Opérateur de sécurité : dispose d’autorisations en lecture seule et peut gérer les alertes.
- Lecteur Sécurité : dispose d’autorisations en lecture seule et peut gérer les alertes. Le Lecteur Sécurité ne peut pas effectuer les actions suivantes :
  - Créer des stratégies ou modifier et changer des stratégies existantes
  - Effectuer des actions de gouvernance

  - Charger des journaux de découverte

  - Interdire ou approuver des applications tierces

  - Accéder à la page de paramètres de la plage d’adresses IP

  - Accès et affichage des pages de paramètres système

  - Accéder aux paramètres de découverte

  - Accéder à la page de connecteurs d’application

  - Accéder au journal de gouvernance

  - Accéder à la page Gérer des rapports d’instantanés

  - Accès et modification de l’agent SIEM

- Lecteur global : dispose d’un accès complet en lecture seule à tous les aspects de Cloud App Security. Impossible de modifier des paramètres ou d’effectuer des actions.

Limitez le nombre de comptes ou de rôles à privilèges élevés et protégez ces comptes à un niveau élevé, car les utilisateurs disposant de ce privilège peuvent lire et modifier directement ou indirectement chaque ressource dans votre environnement Azure.

Vous pouvez activer l’accès privilégié juste-à-temps (JAT) aux ressources Azure et Azure AD en utilisant Azure AD Privileged Identity Management (PIM). JAT accorde des autorisations temporaires pour effectuer des tâches privilégiées uniquement lorsque les utilisateurs en ont besoin. PIM peut également générer des alertes de sécurité en cas d’activité suspecte ou non sécurisée dans votre organisation Azure AD.

- [Gérer l’accès administrateur dans les Cloud App Security](manage-admins.md)

**Supervision d’Azure Security Center** : Oui

**Responsabilité** : Customer

### <a name="pa-2-restrict-administrative-access-to-business-critical-systems"></a>PA-2 : Limiter l’accès administratif aux systèmes critiques de l’entreprise

**Guide**: Cloud App Security offre un contrôle d’accès en fonction du rôle pour les administrateurs.

- [Gérer l’accès administrateur Cloud App Security](manage-admins.md)

**Supervision d’Azure Security Center** : Oui

**Responsabilité** : Customer

### <a name="pa-3-review-and-reconcile-user-access-regularly"></a>PA-3 : Examiner et rapprocher régulièrement les accès utilisateur

**Guide**: Cloud App Security utilise les comptes Azure Active Directory (Azure AD) pour gérer ses ressources, examiner les comptes d’utilisateur et accéder régulièrement aux affectations pour s’assurer que les comptes et leur accès sont valides. Vous pouvez utiliser les révisions d’accès Azure AD pour réviser les appartenances aux groupes, les accès aux applications d’entreprise et les attributions de rôles. Les rapports Azure AD peuvent fournir des journaux pour vous aider à découvrir les comptes obsolètes. Vous pouvez également utiliser Azure AD Privileged Identity Management pour créer un flux de travail de rapport de révision d’accès afin de faciliter le processus de révision.

En outre, Azure Privileged Identity Management peut être configuré pour déclencher des alertes lorsqu'un nombre excessif de comptes d'administrateur est créé, et pour identifier les comptes d'administrateur obsolètes ou mal configurés.

Remarque : Certains services Azure prennent en charge des utilisateurs et des rôles locaux qui ne sont pas gérés par le biais d’Azure AD. Vous devrez gérer ces utilisateurs séparément.

- [Créer une révision d’accès des rôles de ressources Azure dans Privileged Identity Management (PIM)](/azure/active-directory/privileged-identity-management/pim-resource-roles-start-access-review) 

- [Utilisation des révisions d’accès et des identités Azure AD](/azure/active-directory/governance/access-reviews-overvie)

**Supervision d’Azure Security Center** : Oui

**Responsabilité** : Customer

### <a name="pa-4-set-up-emergency-access-in-azure-ad"></a>PA-4 : Configurer l’accès d’urgence dans Azure AD

**Guide**: Cloud App Security utilise Azure Active Directory (Azure AD) pour gérer ses ressources. Pour empêcher le verrouillage accidentel de votre organisation Azure AD, configurez un compte d’accès d’urgence pour conserver un accès lorsque les comptes administratifs normaux ne peuvent pas être utilisés. Les comptes d’accès d’urgence sont généralement hautement privilégiés et ne doivent pas être attribués à des personnes spécifiques. Les comptes d’accès d’urgence sont limités à des cas d’urgence ou à des scénarios « de secours » où il est impossible d’utiliser des comptes d’administration normaux.

Vous devez vous assurer que les informations d’identification (telles que le mot de passe, le certificat ou la carte à puce) des comptes d’accès d’urgence restent sécurisées et connues uniquement des personnes autorisées à les utiliser en cas d’urgence.

- [Gérer des comptes d’accès d’urgence dans Azure AD](/azure/active-directory/users-groups-roles/directory-emergency-access)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="pa-5-automate-entitlement-management"></a>PA-5 : Automatiser la gestion des droits d'utilisation 

**Guide**: Cloud App Security est intégré à Azure Active Directory (Azure AD) pour gérer ses ressources. Utilisez les fonctionnalités de gestion des droits d’utilisation d’Azure AD pour automatiser les workflows de demandes d’accès, notamment les attributions, les révisions et l’expiration des accès. L’approbation en deux ou plusieurs étapes est également prise en charge.

- [Présentation des révisions d’accès Azure AD](/azure/active-directory/governance/access-reviews-overview) 

- [Présentation de la gestion des droits d’utilisation Azure AD](/azure/active-directory/governance/entitlement-management-overview)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="pa-7-follow-just-enough-administration-least-privilege-principle"></a>PA-7 : Suivre le principe Just Enough Administration (privilèges minimum) 

**Guide**: Cloud App Security est intégré au contrôle d’accès en fonction du rôle (RBAC) Azure pour gérer ses ressources. Azure RBAC vous permet de gérer l’accès aux ressources Azure via des attributions de rôles. Vous pouvez affecter ces rôles à des utilisateurs et regrouper des principaux de service et des identités managées. Les rôles intégrés prédéfinis pour certaines ressources peuvent être inventoriés ou interrogés par le biais d’outils tels qu’Azure CLI, Azure PowerShell ou le portail Azure. Les privilèges que vous affectez aux ressources via Azure RBAC doivent toujours être limités à ce qui est requis par les rôles. Ils complètent l’approche juste-à-temps (JIT) d’Azure AD Privileged Identity Management (PIM) et doivent être révisés régulièrement.

Utilisez les rôles intégrés pour allouer des autorisations et ne créez des rôles personnalisés que si nécessaire.

- [Rôles Office 365 et Azure AD avec accès à Cloud App Security](manage-admins.md)

Qu’est-ce que le contrôle d’accès en fonction du rôle Azure (Azure RBAC) ? https://docs.microsoft.com/azure/role-based-access-control/overview 

- [Configurer le contrôle d'accès en fonction du rôle dans Azure](/azure/role-based-access-control/role-assignments-portal) 

- [Utilisation des révisions d’accès et des identités Azure AD](/azure/active-directory/governance/access-reviews-overview)

**Supervision d’Azure Security Center** : Oui

**Responsabilité** : Customer

## <a name="data-protection"></a>Protection des données

*Pour plus d’informations, consultez [Benchmark de sécurité Azure : protection des données](/azure/security/benchmarks/security-controls-v2-data-protection).*

### <a name="dp-2-protect-sensitive-data"></a>DP-2 : Protection des données sensibles

**Guide**: Cloud App Security gère les données sensibles et utilise Azure ad rôles pour contrôler les autorisations pour différents types de données.

- [Azure AD des rôles ayant accès à Cloud App Security](manage-admins.md#office-365-and-azure-ad-roles-with-access-to-cloud-app-security)

**Supervision d’Azure Security Center** : Oui

**Responsabilité** : Customer

### <a name="dp-4-encrypt-sensitive-information-in-transit"></a>DP-4 : Chiffrement des informations sensibles en transit

**Guide**: Cloud App Security prend en charge le chiffrement des données en transit avec TLS v 1.2 ou version ultérieure.

C’est certes facultatif pour le trafic sur les réseaux privés, mais essentiel pour le trafic sur les réseaux externes et publics. Pour le trafic HTTP, vérifiez que les clients se connectant à vos ressources Azure peuvent négocier TLS v1.2 ou une version ultérieure. Pour la gestion à distance, utilisez SSH (pour Linux) ou RDP/TLS (pour Windows) plutôt qu’un protocole non chiffré. Les versions et les protocoles SSL, TLS et SSH obsolètes, ainsi que les chiffrements faibles, doivent être désactivés.

Par défaut, Azure assure le chiffrement des données en transit entre les centres de données Azure.

- [Sécurité et confidentialité des données Microsoft Cloud App Security](cas-compliance-trust.md#encryption)

- [Présentation du chiffrement en transit avec Azure](/azure/security/fundamentals/encryption-overview#encryption-of-data-in-transit) 

- [Informations sur la sécurité TLS](/security/engineering/solving-tls1-problem) 

- [Double chiffrement pour les données Azure en transit](/azure/security/fundamentals/double-encryption#data-in-transit)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Partagé

## <a name="asset-management"></a>Gestion des ressources

*Pour plus d’informations, consultez [Benchmark de sécurité Azure : Gestion des ressources](/azure/security/benchmarks/security-controls-v2-asset-management).*

### <a name="am-1-ensure-security-team-has-visibility-into-risks-for-assets"></a>AM-1 : S’assurer que l’équipe de sécurité a une visibilité sur les risques pour les ressources

**Conseils** : Assurez-vous que les équipes de sécurité reçoivent des autorisations de lecteur de sécurité dans votre locataire et vos abonnements Azure afin qu’elles puissent surveiller les risques de sécurité à l’aide d’Azure Security Center. 

Selon la façon dont les responsabilités de l’équipe de sécurité sont structurées, la surveillance des risques de sécurité peut être la responsabilité d’une équipe de sécurité centrale ou d’une équipe locale. Cela dit, les insights et les risques liés à la sécurité doivent toujours être agrégés de manière centralisée au sein d’une organisation. 

Les autorisations de lecteur de sécurité peuvent être appliquées globalement à un locataire entier (groupe d’administration racine) ou étendues à des groupes d’administration ou à des abonnements spécifiques. 

Remarque : Des autorisations supplémentaires peuvent être nécessaires pour obtenir une visibilité sur les charges de travail et services. 

- [Vue d’ensemble du rôle lecteur de sécurité](/azure/role-based-access-control/built-in-roles#security-reader)

- [Vue d'ensemble des groupes d'administration Azure](/azure/governance/management-groups/overview)

**Supervision Azure Security Center** : actuellement non disponible

**Responsabilité** : Customer

## <a name="logging-and-threat-detection"></a>Journalisation et détection des menaces

*Pour plus d’informations, consultez [Benchmark de sécurité Azure : Journalisation et détection des menaces](/azure/security/benchmarks/security-controls-v2-logging-threat-protection).*

### <a name="lt-1-enable-threat-detection-for-azure-resources"></a>LT-1 : Activer la détection des menaces pour les ressources Azure

**Guide**: transférer tous les journaux de Cloud App Security à votre serveur Siem qui peuvent être utilisés pour configurer des détections de menaces personnalisées. Veillez à surveiller les différents types de ressources Azure pour identifier les menaces et anomalies potentielles. Concentrez-vous sur l’obtention d’alertes de haute qualité afin de réduire les faux positifs que les analystes doivent trier. Les alertes peuvent provenir de données de journal, d’agents ou d’autres données.

- [Intégration d’Azure Sentinel](siem-sentinel.md)
- [Intégration de SIEM générique](siem.md)

- [Créer des règles d’analytique personnalisées pour détecter des menaces](/azure/sentinel/tutorial-detect-threats-custom) 

- [Renseignement sur les menaces informatiques dans Azure Sentinel](/azure/architecture/example-scenario/data/sentinel-threat-intelligence)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

## <a name="incident-response"></a>Réponse aux incidents

*Pour plus d’informations, consultez [Benchmark de sécurité Azure : réponse aux incidents](/azure/security/benchmarks/security-controls-v2-incident-response).*

### <a name="ir-1-preparation--update-incident-response-process-for-azure"></a>IR-1 : Préparation – mettre à jour le processus de réponse aux incidents pour Azure

**Conseils** : Assurez-vous que votre organisation dispose de processus pour répondre aux incidents de sécurité, qu’elle a mis à jour ces processus pour Azure et qu’elle les exerce régulièrement pour garantir la préparation.

- [Implémenter la sécurité dans l’environnement de l’entreprise](/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

- [Guide de référence sur les réponses aux incidents](/microsoft-365/downloads/IR-Reference-Guide.pdf)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="ir-2-preparation--setup-incident-notification"></a>IR-2 : Préparation – configurer la notification d’incident

**Conseils** : Configurez les coordonnées des personnes à contacter en cas d’incident de sécurité dans Azure Security Center. Microsoft utilisera ces coordonnées afin de vous contacter si le Microsoft Security Response Center (MSRC) découvre que vos données ont été consultées de manière illégale ou par un tiers non autorisé. Vous disposez également d’options pour personnaliser les alertes d’incident et les notifications dans différents services Azure en fonction de vos besoins en matière de réponse aux incidents. 

- [Comment définir le contact de sécurité d’Azure Security Center](/azure/security-center/security-center-provide-security-contact-details)

**Supervision d’Azure Security Center** : Oui

**Responsabilité** : Customer

### <a name="ir-3-detection-and-analysis--create-incidents-based-on-high-quality-alerts"></a>IR-3 : Détection et analyse – créer des incidents en fonction d’alertes de haute qualité

**Instructions** : Veillez à avoir un processus de création d’alertes de bonne qualité et de mesure de la qualité des alertes. Cela vous permet de tirer les leçons des incidents passés et de classer par ordre de priorité les alertes pour les analystes, afin qu’ils ne perdent pas de temps sur les faux positifs. 

Vous pouvez créer des alertes de bonne qualité en vous basant sur l’expérience des incidents passés, sur les sources validées par la communauté, et sur des outils conçus pour générer et nettoyer les alertes en fusionnant et en mettant en corrélation différentes sources de signaux. 

Azure Security Center (ASC) fournit des alertes de haute qualité sur de nombreuses ressources Azure. Vous pouvez utiliser le connecteur de données ASC pour diffuser en continu les alertes vers Azure Sentinel. Azure Sentinel vous permet de créer des règles d’alerte avancées pour générer automatiquement des incidents à des fins d’enquête. 

Exportez vos alertes et recommandations Azure Security Center en utilisant la fonctionnalité d’exportation pour identifier les risques pesant sur les ressources Azure. Exportez les alertes et les recommandations manuellement ou automatiquement de manière continue.

- [Procédure de configuration de l’exportation](/azure/security-center/continuous-export)

- [Comment envoyer des alertes à Azure Sentinel](/azure/sentinel/connect-azure-security-center)

**Supervision Azure Security Center** : actuellement non disponible

**Responsabilité** : Customer

### <a name="ir-4-detection-and-analysis--investigate-an-incident"></a>IR-4 : Détection et analyse – enquêter sur un incident

**Conseils** : Veiller à ce que les analystes puissent interroger et utiliser diverses sources de données lorsqu’ils enquêtent sur des incidents potentiels, afin d’obtenir une vision complète de ce qui s’est passé. Différents journaux doivent être collectés pour suivre les activités d’un attaquant potentiel tout au long de la chaîne de destruction afin d’éviter les angles morts.  Vous devez également vous assurer que les insights et les enseignements sont capturés pour d’autres analystes et pour une référence historique future.  

Les sources de données à des fins d’investigation incluent les sources de journalisation centralisées qui sont déjà collectées à partir des services dans l’étendue et des systèmes en cours d’exécution, mais elles peuvent également inclure les éléments suivants :

- Données réseau : utilisez les journaux de flux des groupes de sécurité réseau, Azure Network Watcher et Azure Monitor pour capturer des journaux de flux réseau et d’autres informations analytiques. 

- Captures instantanées des systèmes en fonctionnement : 

    - Utilisez la capacité de capture instantanée de la machine virtuelle Azure pour créer un instantané du disque du système en fonctionnement. 

    - Utilisez la capacité native de sauvegarde de la mémoire du système d’exploitation pour créer un instantané de la mémoire du système en fonctionnement.

    - Utilisez la capacité de capture instantanée des services Azure ou celle de votre logiciel pour créer des instantanés des systèmes en fonctionnement.

Azure Sentinel fournit des analyses de données approfondies sur pratiquement toutes les sources de journal et un portail de gestion des cas pour gérer le cycle de vie complet des incidents. Les renseignements obtenus au cours d’une enquête peuvent être associés à un incident à des fins de suivi et de rapport. 

- [Capture instantanée du disque d’un ordinateur Windows](/azure/virtual-machines/windows/snapshot-copy-managed-disk)

- [Capture instantanée du disque d’un ordinateur Linux](/azure/virtual-machines/linux/snapshot-copy-managed-disk)

- [Collecte de l’image mémoire et des informations de diagnostic par le support Microsoft Azure](https://azure.microsoft.com/support/legal/support-diagnostic-information-collection/) 

- [Examiner les incidents avec Azure Sentinel](/azure/sentinel/tutorial-investigate-cases)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="ir-5-detection-and-analysis--prioritize-incidents"></a>IR-5 : Détection et analyse – classer par ordre de priorité les incidents

**Conseils** : Donnez aux analystes le contexte sur lequel les incidents doivent se concentrer en premier lieu en fonction de la gravité de l’alerte et de la sensibilité des ressources. 

Azure Security Center attribue un niveau de gravité à chaque alerte pour vous aider à hiérarchiser celles devant être examinées en premier. La gravité dépend du niveau de confiance accordé par Security Center à la découverte ou à l’analytique ayant servi à émettre l’alerte, ainsi que du niveau de confiance quant à l’existence d’une intention malveillante sous-jacente dans l’activité à l’origine de l’alerte.

En outre, marquez les ressources à l’aide d’étiquettes et créez un système de nommage pour identifier et classer les ressources Azure, en particulier celles qui traitent des données sensibles.  Il vous incombe de hiérarchiser le traitement des alertes en fonction de la criticité des ressources et de l’environnement Azure où l’incident s’est produit.

- [Alertes de sécurité dans le Centre de sécurité Azure](/azure/security-center/security-center-alerts-overview)

- [Organisation des ressources Azure à l’aide de catégories](/azure/azure-resource-manager/resource-group-using-tags)

**Supervision Azure Security Center** : actuellement non disponible

**Responsabilité** : Customer

### <a name="ir-6-containment-eradication-and-recovery--automate-the-incident-handling"></a>IR-6 : Confinement, éradication et récupération – automatiser la gestion des incidents

**Conseils** : Automatisez les tâches manuelles répétitives pour accélérer le temps de réponse et réduire la charge de travail des analystes. Les tâches manuelles prennent plus de temps à s’exécuter, ralentissant chaque incident et réduisant le nombre d’incidents qu’un analyste peut gérer. Les tâches manuelles augmentent également la fatigue des analystes, ce qui accroît le risque d’erreur humaine entraînant des retards et dégrade la capacité des analystes à se concentrer efficacement sur des tâches complexes. Utilisez les fonctionnalités d’automatisation des workflows dans Azure Security Center et Azure Sentinel pour déclencher automatiquement des actions ou exécuter un playbook pour répondre aux alertes de sécurité entrantes. Le playbook prend des mesures, telles que l’envoi de notifications, la désactivation de comptes et l’isolement des réseaux problématiques. 

- [Configurer l’automatisation du workflow dans Security Center](/azure/security-center/workflow-automation)

- [Configurer des réponses automatisées aux menaces dans Azure Security Center](/azure/security-center/tutorial-security-incident#triage-security-alerts)

- [Configurer des réponses automatisées aux menaces dans Azure Sentinel](/azure/sentinel/tutorial-respond-threats-playbook)

**Supervision Azure Security Center** : actuellement non disponible

**Responsabilité** : Customer

## <a name="posture-and-vulnerability-management"></a>Gestion de la posture et des vulnérabilités

*Pour plus d’informations, consultez [Benchmark de sécurité Azure : Gestion de la posture et des vulnérabilités](/azure/security/benchmarks/security-controls-v2-vulnerability-management).*

### <a name="pv-8-conduct-regular-attack-simulation"></a>PV-8 : Effectuer une simulation d’attaque régulière

**Conseils** : Selon les besoins, effectuez un test d’intrusion ou des activités Red Team sur vos ressources Azure et résolvez tous les problèmes de sécurité critiques détectés.
Suivez les règles d’engagement de pénétration du cloud Microsoft pour vous assurer que vos tests d’intrusion sont conformes aux stratégies de Microsoft. Utilisez la stratégie et l’exécution de Red Teaming de Microsoft ainsi que les tests d’intrusion de site actif sur l’infrastructure cloud, les services et les applications gérés par Microsoft.

- [Test d’intrusion dans Azure](/azure/security/fundamentals/pen-testing)

- [Règles d’engagement des tests d’intrusion](https://www.microsoft.com/msrc/pentest-rules-of-engagement?rtc=1) 

- [Microsoft Cloud Red Teaming](https://gallery.technet.microsoft.com/Cloud-Red-Teaming-b837392e)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Partagé

## <a name="governance-and-strategy"></a>Gouvernance et stratégie

*Pour plus d’informations, consultez [Benchmark de sécurité Azure : Gouvernance et stratégie](/azure/security/benchmarks/security-controls-v2-governance-strategy).*

### <a name="gs-1-define-asset-management-and-data-protection-strategy"></a>GS-1 : Définir la stratégie de gestion des ressources et de protection des données 

**Conseils** : Veillez à documenter et à communiquer une stratégie claire pour la surveillance et la protection continues des systèmes et des données. Hiérarchisez la découverte, l’évaluation, la protection et la surveillance des données et systèmes critiques de l’entreprise. 

Cette stratégie doit inclure les recommandations, stratégies et normes documentées pour les éléments suivants : 

-   Norme de classification des données en fonction des risques pour l’entreprise

-   Visibilité de l’organisation de sécurité sur les risques et l’inventaire des actifs 

-   Approbation de l’organisation de sécurité pour les services Azure en vue de leur utilisation 

-   Sécurité des ressources tout au long de leur cycle de vie

-   Stratégie de contrôle d’accès requise conformément à la classification des données organisationnelles

-   Utilisation de fonctionnalités de protection des données natives et tierces Azure

-   Exigences de chiffrement des données pour les cas d’utilisation en transit et au repos

-   Normes de chiffrement appropriées

Pour plus d’informations, consultez les références suivantes :
- [Recommandation d’architecture de sécurité Azure - Stockage, données et chiffrement](/azure/architecture/framework/security/storage-data-encryption?amp;bc=%2fsecurity%2fcompass%2fbreadcrumb%2ftoc.json&toc=%2fsecurity%2fcompass%2ftoc.json)

- [Notions de base de la sécurité Azure - Sécurité, chiffrement et stockage des données Azure](/azure/security/fundamentals/encryption-overview)

- [Cloud Adoption Framework - Meilleures pratiques en matière de chiffrement et de sécurité des données Azure](/azure/security/fundamentals/data-encryption-best-practices?amp;bc=%2fazure%2fcloud-adoption-framework%2f_bread%2ftoc.json&toc=%2fazure%2fcloud-adoption-framework%2ftoc.json)

- [Benchmark de sécurité Azure - Gestion des ressources](/azure/security/benchmarks/security-benchmark-v2-asset-management)

- [Benchmark de sécurité Azure - Protection des données](/azure/security/benchmarks/security-benchmark-v2-data-protection)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="gs-2-define-enterprise-segmentation-strategy"></a>GS-2 : Définir la stratégie de segmentation d'entreprise 

**Conseils** : Établissez une stratégie à l'échelle de l'entreprise pour segmenter l'accès aux ressources à l'aide d'une combinaison de contrôles d'identité, de réseau, d'application, d'abonnement, de groupe de gestion et autres.

Trouvez le bon équilibre entre la nécessité de séparation sur le plan de la sécurité et la nécessité d'exécuter quotidiennement les systèmes qui doivent communiquer entre eux et accéder aux données.

Veillez à ce que la stratégie de segmentation soit implémentée de manière cohérente pour tous les types de contrôle, y compris pour les modèles d'identité, d'accès et de sécurité du réseau, les modèles d'autorisation/d'accès aux applications et les contrôles des processus humains.

- [Aide relative à la stratégie de segmentation dans Azure (vidéo)](/security/compass/microsoft-security-compass-introduction#azure-components-and-reference-model-2151)

- [Aide relative à la stratégie de segmentation dans Azure (document)](/security/compass/governance#enterprise-segmentation-strategy)

- [Aligner la segmentation du réseau avec la stratégie de segmentation d’entreprise](/security/compass/network-security-containment#align-network-segmentation-with-enterprise-segmentation-strategy)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="gs-3-define-security-posture-management-strategy"></a>GS-3 : Définir la stratégie de gestion de la posture de la sécurité

**Conseils** : Mesurez et atténuez en permanence les risques liés à vos ressources individuelles et à l’environnement dans lequel elles sont hébergées. Hiérarchisez les ressources à valeur élevée et les surfaces d’attaque hautement exposées, telles que les applications publiées, les points d’entrée et de sortie du réseau, les points de terminaison utilisateur et administrateur, etc.

- [Benchmark de sécurité Azure - Gestion de la posture et des vulnérabilités](/azure/security/benchmarks/security-benchmark-v2-posture-vulnerability-management)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="gs-4-align-organization-roles-responsibilities-and-accountabilities"></a>GS-4 : Aligner les rôles et les responsabilités de l’organisation

**Conseils** : Veillez à documenter et à communiquer une stratégie claire pour les rôles et les responsabilités de votre organisation de sécurité. Veillez à définir clairement les responsabilités pour les décisions relatives à la sécurité, à former tout le monde au modèle de responsabilité partagée et à former les équipes techniques à la technologie permettant de sécuriser le cloud.

- [Meilleures pratiques pour la sécurité Azure 1 – Personnes : Former les équipes pour le parcours vers la sécurité dans le cloud](/azure/cloud-adoption-framework/security/security-top-10#1-people-educate-teams-about-the-cloud-security-journey)

- [Meilleures pratiques pour la sécurité Azure 2 – Personnes : Former les équipes pour les technologies de sécurité dans le cloud](/azure/cloud-adoption-framework/security/security-top-10#2-people-educate-teams-on-cloud-security-technology)

- [Meilleures pratiques pour la sécurité Azure 3 – Processus : Affecter les responsabilités pour les décisions de sécurité dans le cloud](/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="gs-5-define-network-security-strategy"></a>GS-5 : Définir la stratégie de sécurité réseau

**Conseils** : Établissez une approche de sécurité réseau Azure dans le cadre de la stratégie de contrôle d’accès de sécurité globale de votre organisation.  

Cette stratégie doit inclure les recommandations, stratégies et normes documentées pour les éléments suivants : 

-   Responsabilité centralisée pour la gestion et la sécurité du réseau

-   Modèle de segmentation de réseau virtuel aligné avec la stratégie de segmentation de l’entreprise

-   Stratégie de correction dans différents scénarios de menaces et d’attaques

-   Stratégie de périphérie d’Internet et d’entrée et de sortie

-   Stratégie de cloud hybride et d’interconnexion locale

-   Artefacts de sécurité réseau à jour (par exemple diagrammes réseau, architecture de réseau de référence)

Pour plus d’informations, consultez les références suivantes :
- [Meilleures pratiques pour la sécurité Azure 11 – Architecture. Stratégie de sécurité unifiée unique](/azure/cloud-adoption-framework/security/security-top-10#11-architecture-establish-a-single-unified-security-strategy)

- [Benchmark de sécurité Azure – Sécurité réseau](/azure/security/benchmarks/security-benchmark-v2-network-security)

- [Vue d’ensemble de la sécurité réseau d’Azure](/azure/security/fundamentals/network-overview)

- [Stratégie d’architecture de réseau d’entreprise](/azure/cloud-adoption-framework/ready/enterprise-scale/architecture)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="gs-6-define-identity-and-privileged-access-strategy"></a>GS-6 : Définir une stratégie d’accès privilégié et d’identité

**Conseils** : Établissez une approche d’identité Azure et d’accès privilégié dans le cadre de la stratégie de contrôle d’accès de sécurité globale de votre organisation.  

Cette stratégie doit inclure les recommandations, stratégies et normes documentées pour les éléments suivants : 

-   Un système centralisé d’identité et d’authentification et son interconnexion avec d’autres systèmes d’identité internes et externes

-   Méthodes d’authentification fortes dans différents cas d’usage et différentes conditions

-   Protection des utilisateurs disposant de privilèges élevés

-   Surveillance et gestion des activités anormales des utilisateurs  

-   Vérification de l’identité et de l’accès des utilisateurs et processus de rapprochement

Pour plus d’informations, consultez les références suivantes :

- [Benchmark de sécurité Azure - Gestion des identités](/azure/security/benchmarks/security-benchmark-v2-identity-management)

- [Benchmark de sécurité Azure - Accès privilégié](/azure/security/benchmarks/security-benchmark-v2-privileged-access)

- [Meilleures pratiques pour la sécurité Azure 11 – Architecture. Stratégie de sécurité unifiée unique](/azure/cloud-adoption-framework/security/security-top-10#11-architecture-establish-a-single-unified-security-strategy)

- [Vue d’ensemble de la sécurité et de la gestion des identités Azure](/azure/security/fundamentals/identity-management-overview)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

### <a name="gs-7-define-logging-and-threat-response-strategy"></a>GS-7 : Définir la stratégie de journalisation et de réponse aux menaces

**Conseils** : Établissez une stratégie de journalisation et de réponse aux menaces pour détecter et corriger rapidement les menaces tout en répondant aux exigences de conformité. En priorité, fournissez aux analystes des alertes de bonne qualité et des expériences homogènes afin qu’ils puissent se concentrer sur les menaces plutôt que sur l’intégration et les étapes manuelles. 

Cette stratégie doit inclure les recommandations, stratégies et normes documentées pour les éléments suivants : 

-   Rôle et responsabilités de l’organisation d’opérations de sécurité (SecOP) 

-   Un processus de réponse aux incidents bien défini, aligné avec NIST ou autre cadre réglementaire du secteur 

-   Capture et rétention des journaux pour prendre en charge la détection des menaces, la réponse aux incidents et les besoins de conformité

-   Visibilité centralisée des informations de corrélation sur les menaces, avec SIEM, les fonctionnalités Azure natives et d’autres sources 

-   Plan de communication et de notification avec vos clients, fournisseurs et les parties publiques pertinentes

-   Utilisation de plateformes Azure natives et tierces pour la gestion des incidents, comme la journalisation et la détection des menaces, les investigations et la correction et l’éradication des attaques

-   Processus de gestion des incidents et des activités postérieures aux incidents, comme les leçons apprises et la rétention des preuves

Pour plus d’informations, consultez les références suivantes :

- [Benchmark de sécurité Azure - Journalisation et détection des menaces](/azure/security/benchmarks/security-benchmark-v2-logging-threat-detection)

- [Benchmark de sécurité Azure - Réponse aux incidents](/azure/security/benchmarks/security-benchmark-v2-incident-response)

- [Meilleures pratiques pour la sécurité Azure 4 - Processus. Mise à jour des processus de réponse aux incidents pour le cloud](/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

- [Guide pour le cadre d’adoption d’Azure, la journalisation et la prise de décision pour les rapports](/azure/cloud-adoption-framework/decision-guides/logging-and-reporting/)

- [Mise à l’échelle, gestion et surveillance d’entreprise Azure](/azure/cloud-adoption-framework/ready/enterprise-scale/management-and-monitoring)

**Supervision d’Azure Security Center** : Non applicable

**Responsabilité** : Customer

## <a name="next-steps"></a>Étapes suivantes

- Consultez [Vue d’ensemble d’Azure Security Benchmark V2](/azure/security/benchmarks/overview)
- En savoir plus sur les [bases de référence de la sécurité Azure](/azure/security/benchmarks/security-baselines-overview)
