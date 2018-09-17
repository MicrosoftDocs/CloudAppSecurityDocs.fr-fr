---
title: Nouveautés de Cloud App Security | Microsoft Docs
description: Cette rubrique est mise à jour fréquemment pour vous informer des nouveautés de la dernière version de Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 9/3/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: d418ef3d-76ee-45d5-b5ae-21346e5239a3
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: b4f96e969a4276e6f2456659dfcae7243a791232
ms.sourcegitcommit: bb44de2ebaf2526cc04e08c3737f77f73f219310
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45561199"
---
*S’applique à : Microsoft Cloud App Security*


# <a name="whats-new-with-microsoft-cloud-app-security"></a>Nouveautés de Microsoft Cloud App Security


## <a name="cloud-app-security-release-131"></a>Cloud App Security version 131

Publication : 2 septembre 2018

- **Révoquer automatiquement des autorisations sur les applications OAuth à risque**<br>
Vous pouvez désormais contrôler à quelles applications OAuth vos utilisateurs ont accès, en révoquant l’autorisation d’application pour les applications OAuth sur Office, Google ou Salesforce. Lorsque vous créez une **stratégie d’autorisation d’application**, vous pouvez maintenant définir la stratégie pour révoquer l’autorisation d’une application. 

- **Analyseur intégré supplémentaire Cloud Discovery pris en charge**<br>Cloud Discovery prend désormais en charge le format de journal Forcepoint Web Security Cloud.

 
## <a name="cloud-app-security-release-130"></a>Cloud App Security version 130

Publication : 22 août 2018


- **Nouvelle barre de menus**<br>
Pour fournir une expérience d’administration plus cohérente entre les produits Microsoft 365 et vous permettre de naviguer plus facilement entre les solutions de sécurité Microsoft, la barre de menus du portail Cloud App Security a été déplacée vers le côté gauche de l’écran. Cette expérience de navigation cohérente vous aide à vous orienter lorsque vous passez d’un portail de sécurité Microsoft à l’autre.

- **Impact sur le score de l’application OAuth**<br>
Vous pouvez désormais envoyer des commentaires à l’équipe Cloud App Security pour nous indiquer s’il existe une application OAuth découverte dans votre organisation qui semble malveillante. Cette nouvelle fonctionnalité vous permet de faire partie de notre communauté de sécurité et d’améliorer l’analyse et le score de risque de l’application OAuth. Pour plus d’informations, consultez [Gérer les autorisations d’applications](manage-app-permissions.md).

- **Nouveaux analyseurs Cloud Discovery**<br>
Les analyseurs Cloud Discovery prennent désormais en charge iboss Secure Cloud Gateway et Sophos XG.


## <a name="cloud-app-security-release-129"></a>Cloud App Security version 129

Publication : 5 août 2018

- **Nouvelles stratégies de détection des anomalies : règles concernant les e-mails suspects**<br>De nouvelles stratégies de détection des anomalies ont été ajoutées pour détecter les règles de transfert des e-mails suspects, par exemple, si un utilisateur a créé une règle de boîte de réception assurant le transfert d’une copie de tous les e-mails à une adresse externe. 
- Cette version inclut des correctifs et améliorations ciblant plusieurs problèmes. 

## <a name="cloud-app-security-release-128"></a>Cloud App Security version 128

Publication : 22 juillet 2018

-   **Actions d’autorisations d’application sur plusieurs applications**<br>
Pour les applications qui ont reçu des autorisations d’application, vous pouvez maintenant en interdire ou en approuver plusieurs en une seule action. Par exemple, vous pouvez consulter toutes les applications qui ont reçu une autorisation par les utilisateurs de votre organisation, sélectionner toutes les applications que vous voulez interdire et cliquer sur Interdire des applications pour révoquer tous les consentements accordés et cesser d’autoriser les utilisateurs à accorder des autorisations à ces applications.  Pour plus d’informations, consultez [Gérer une autorisation d’application](manage-app-permissions.md).
-   **Prise en charge avancée des applications Azure**<br>
Pour Azure, nous offrons progressivement la possibilité de détecter les applications en tant qu’activités de compte d’utilisateur effectuées par les applications Azure (internes et externes). Cela vous permet de créer des stratégies qui vous avertissent si une application effectue des activités inattendues et non autorisées. Pour plus d’informations, consultez [Connecter Azure à Microsoft Cloud App Security](connect-azure-to-microsoft-cloud-app-security.md).
-   **Moteur de classification des données mis à jour avec de nouveaux types de contenu sensible du RGPD**<br>
Le [Service de classification des données Cloud App Security](dcs-inspection.md) a ajouté de nouveaux types de contenu sensible à notre moteur de classification des données pour vous permettre de détecter du contenu relatif au RGPD dans vos fichiers.
-   **Mises à jour du catalogue des applications cloud**<br>
Le catalogue d’applications cloud comprend maintenant une catégorie de risque Légal (en plus de Général, Sécurité et Conformité) pour vous aider à gérer la conformité à la confidentialité et à la propriété des données, notamment la préparation au RGPD.
Pour vous permettre d’évaluer la préparation au RGPD de chaque application cloud, la nouvelle catégorie de risque contient l’instruction de préparation au RGPD du service cloud et l’état de chaque contrôle de structure du RGPD.
Notez que, dans le cadre de cette amélioration, les attributs de risque suivants ont été déplacés de l’autre catégorie de risque à la catégorie Légal :
     - DMCA
     - Propriété des données
     - Stratégie de conservation des données

     De plus, la nouvelle catégorie de risque est évaluée séparément pour vous permettre de configurer la pondération du score en fonction de vos préférences et de vos priorités. Pour plus d’informations, consultez [Score du risque](risk-score.md).

-   **Nouvelle requête proposée : prête pour le RGPD** <br>
Il existe une nouvelle proposition de requête qui vous permet d’identifier les applications découvertes qui sont prêtes pour le RGPD. Étant donné que le RGPD est récemment devenu une priorité absolue pour les administrateurs de sécurité, cette requête vous aide à identifier les applications qui sont prêtes pour le RGPD et à atténuer les menaces en évaluant le risque de celles qui ne le sont pas.


## <a name="cloud-app-security-release-127"></a>Cloud App Security version 127

Publication : 8 juillet 2018

- Vous pouvez désormais voir les activités génériques pour Office 365 dans le **Journal d’activité** et filtrer les activités Office 365 ayant pour état **Non spécifié** dans les **Stratégies d’activité**. Vous pouvez examiner ces activités pour rechercher des informations sur les activités effectuées non encore classées par type dans Cloud App Security, et vous pouvez utiliser ces activités pour envoyer des demandes à l’équipe Cloud App Security afin de créer des types d’activités en fonction de ces activités. 

## <a name="cloud-app-security-release-126"></a>Cloud App Security version 126

Publication : 24 juin 2018

-   **Contrôle d’application par accès conditionnel en disponibilité générale**<br>Le contrôle d’application par accès conditionnel Microsoft Cloud App Security (proxy inverse) est maintenant en disponibilité générale pour toutes les applications SAML. Le contrôle d’application par accès conditionnel s’intègre directement à vos stratégies d’accès conditionnel Azure AD pour **surveiller et contrôler les sessions de vos utilisateurs en temps réel**, tout en leur permettant d’être productifs. Depuis la première préversion de la fonctionnalité, de nombreuses fonctions et améliorations ont été apportées, notamment : 
    -   La possibilité de créer une [stratégie d’accès](access-policy-aad.md) pour gérer l’accès aux mêmes applications à partir des clients natifs, en plus de créer une stratégie de session pour le trafic du navigateur.
    -   Le processus d’intégration des applications a été simplifié pour prendre en charge les applications SAML personnalisées de votre organisation.
    -   Dans le cadre du réseau mondial Azure, l’intégration et l’interface ont été améliorées pour que les utilisateurs bénéficient d’une expérience fluide, où qu’ils se trouvent.
 

-   **Inspection du contenu avec les services de classification des données Microsoft en disponibilité générale**<br>L’intégration de Microsoft Cloud App Security avec les services de classification des données Microsoft est maintenant en disponibilité générale. Cette intégration vous permet d’utiliser le service de classification des données Microsoft en mode natif pour classer les fichiers dans vos applications cloud. Pour plus d’informations, consultez [Intégration des services de classification des données Microsoft](dcs-inspection.md). Cette fonctionnalité est actuellement uniquement disponible aux États-Unis et en Europe (à l’exclusion de la France).

- **Rapport exécutif Cloud Discovery**<br>Microsoft Cloud App Security met progressivement en place la possibilité de générer un rapport exécutif Cloud Discovery au format PDF. Ce rapport fournit une vue d’ensemble de l’utilisation du Shadow IT qui a été identifiée dans votre organisation, en mettant en avant les principaux utilisateurs et principales applications utilisées en général et dans les catégories dominantes, et se concentre sur le risque que pose le Shadow IT dans votre organisation. De plus, le rapport fournit une liste de recommandations pour améliorer la visibilité et le contrôle du Shadow IT dans votre organisation. Utilisez ce rapport pour vous assurer que les menaces et risques potentiels sont supprimés et que votre organisation reste sûr et sécurisé.

-   **Détection de programme malveillant**<br>La détection de programme malveillant, progressivement mise en place, **détecte automatiquement les fichiers malveillants dans votre stockage cloud**, quel que soit le type de fichier. Microsoft Cloud App Security utilise la Threat Intelligence de Microsoft pour savoir si certains fichiers sont associés à des attaques par programme malveillant connues ou s’ils sont potentiellement dangereux. Pour plus d’informations, consultez [Stratégies de détection d’anomalie](anomaly-detection-policy.md).
 
-   **Correction automatisée des activités suspectes**<br>Vous pouvez désormais définir des actions de correction automatique pour une session suspecte, qui sont déclenchées par les stratégies de détection d’anomalie. Cette amélioration vous permet d’être alerté instantanément lorsqu’une violation se produit et d’**appliquer automatiquement des actions de gouvernance**, comme suspendre l’utilisateur. Pour plus d’informations, consultez [Stratégies de détection d’anomalie](anomaly-detection-policy.md#adp-automated-gov). 
 
-   **Évaluation de la configuration de la sécurité pour Azure**<br>Microsoft Cloud App Security met progressivement en place la possibilité d’obtenir une évaluation de la configuration de la sécurité de votre environnement Azure et fournit des recommandations s’il manque une configuration et un contrôle de la sécurité. Par exemple, vous êtes averti s’il manque MFA pour les utilisateurs administratifs. Pour plus d’informations, consultez [Intégration de la gestion de la posture de sécurité cloud](security-config.md).  
  
-   **Détection automatisée des applications OAuth à risque**<br>En plus d’investiguer les applications OAuth connectées à votre environnement, Microsoft Cloud App Security met progressivement en place la possibilité de définir des notifications automatisées pour vous informer quand une application OAuth répond à certains critères. Par exemple, vous pouvez être automatiquement alerté quand des applications exigent un niveau d’autorisation élevé et que plus de 50 utilisateurs l’ont accordé. Pour plus d’informations, consultez [Stratégies d’autorisation d’application](app-permission-policy.md).
 
-   **Prise en charge de la gestion des fournisseurs MSSP (Managed Security Service Provider)**<br>Microsoft Cloud App Security fournit désormais une meilleure expérience de gestion pour les fournisseurs MSSP. Les utilisateurs externes peuvent maintenant être configurés en tant qu’administrateurs et se voir attribuer [les rôles actuellement disponibles dans Microsoft Cloud App Security](manage-admins.md). De plus, pour autoriser les fournisseurs MSSP à offrir des services sur plusieurs locataires de clients, les administrateurs disposant des droits d’accès sur plus d’un locataire peuvent facilement passer d’un locataire à l’autre au sein du portail. Pour plus d’informations sur la gestion des administrateurs, consultez [Gérer les administrateurs](manage-admins.md).
  
-   **Intégration avec la protection DLP externe en disponibilité générale**<br>Microsoft Cloud App Security vous permet de [tirer parti des investissements existants dans les systèmes de classification tiers](icap-stunnel.md), comme les solutions DLP (Data Loss Prevention), et d’analyser le contenu des applications cloud à l’aide de déploiements existants exécutés dans votre environnement. Pour plus d’informations, consultez [Intégration de la protection DLP externe](icap-stunnel.md).


## <a name="cloud-app-security-release-125"></a>Cloud App Security version 125

Publication : 10 juin 2018


- **Nouvelle fonctionnalité d’investigation basée sur les utilisateurs avec le plus de sessions suspectes :**<br>
Microsoft Cloud App Security a ajouté un nouveau widget d’enquête au tableau de bord qui affiche les principaux utilisateurs en fonction du nombre d’alertes de détection de menace ouvertes. Ce widget d’enquête vous permet de concentrer votre recherche de menace sur les utilisateurs avec le plus grand nombre de sessions suspectes.

- **Prise en charge des compartiments AWS S3 :**<br>
Microsoft Cloud App Security peut désormais détecter les compartiments AWS S3 et leurs niveaux de partage. Vous obtenez ainsi des alertes et une visibilité des compartiments AWS accessibles publiquement. Cela vous permet également de créer des stratégies basées sur les compartiments et d’appliquer la gouvernance automatique. En outre, il existe un nouveau modèle de stratégie disponible appelé **Compartiments S3 (AWS) accessibles publiquement** que vous pouvez utiliser pour créer facilement une stratégie régissant votre stockage AWS. Pour activer ces nouvelles fonctionnalités, assurez-vous de mettre à jour vos applications connectées à AWS en ajoutant les nouvelles autorisations décrites dans [Connecter AWS](connect-aws-to-microsoft-cloud-app-security.md).

- **Privilèges Administrateur sur les groupes d’utilisateurs** : Vous pouvez maintenant définir des privilèges Administrateur pour les administrateurs Microsoft Cloud App Security par groupe d’utilisateurs. Par exemple, vous pouvez définir un utilisateur spécifique en tant qu’administrateur des utilisateurs en Allemagne uniquement. Cela permet à l’utilisateur d’afficher et de modifier les informations de Microsoft Cloud App Security uniquement pour le groupe d’utilisateurs « Allemagne - tous les utilisateurs ». Pour plus d’informations, consultez [Gestion des accès d’administration](manage-admins.md).


## <a name="cloud-app-security-release-124"></a>Cloud App Security version 124

Publication : 27 mai 2018

-   **Évaluation des risques RGPD ajoutée au catalogue d’applications cloud**<br>
13 nouveaux facteurs de risque ont été ajoutés à Microsoft Cloud App Security. Ces facteurs de risque suivent la checklist RGPD pour vous permettre d’évaluer les applications du catalogue d’applications cloud conformément à la réglementation RGPD.

-   **Intégrer le service de classification des données Microsoft**<br>
Microsoft Cloud App Security vous permet désormais d’utiliser le service de classification des données de Microsoft en mode natif pour classer les fichiers dans vos applications cloud. <br>
Le service de classification des données de Microsoft fournit une expérience de protection unifiée sur Office 365, Azure Information Protection et Microsoft Cloud App Security. Il vous permet d’étendre la même infrastructure de classification des données aux applications cloud tierces protégées par Microsoft Cloud App Security, en appliquant les décisions que vous déjà prises à un plus grand nombre d’applications. 

-   **Se connecter à Microsoft Azure** (déploiement progressif)<br>
Microsoft Cloud App Security étend ses fonctionnalités de surveillance IaaS au-delà d’Amazon Web Services et prend désormais en charge Microsoft Azure. Cela vous permet de vous connecter rapidement et de surveiller tous vos abonnements Azure avec Cloud App Security. Cette connexion vous offre un ensemble puissant d’outils pour protéger votre environnement Azure, notamment : 

       -    Visibilité de toutes les activités effectuées via le portail

       -    Possibilité de créer des stratégies personnalisées pour signaler un comportement non désiré, de protéger automatiquement les utilisateurs présentant des risques en les suspendant ou en les forçant à se reconnecter.

       -    Toutes les activités Azure sont contrôlées par notre moteur de détection des anomalies, qui vous signale automatiquement tout comportement suspect dans le portail Azure, notamment les voyages impossibles, les activités de masse suspectes et les activités provenant d’un nouveau pays.<br>

  Pour plus d’informations, consultez [Connecter Azure à Microsoft Cloud App Security](connect-azure-to-microsoft-cloud-app-security.md).
 
-   **Déploiements étendus** (déploiement progressif) <br>
Microsoft Cloud App Security offre aux entreprises la possibilité d’identifier de façon granulaire les utilisateurs à surveiller et à protéger en fonction de l’appartenance à un groupe. Cette fonctionnalité vous permet de sélectionner les utilisateurs dont les activités n’apparaîtront pas pour les applications protégées. La fonctionnalité de surveillance étendue est particulièrement dans les cas suivants : 

    -   Conformité : si vos réglementations de conformité vous interdisent de surveiller les utilisateurs de certains pays en raison de réglementations locales.

       -    Gestion des licences : si vous souhaitez surveiller un nombre restreint d’utilisateurs afin de rester dans les limites de vos licences Microsoft Cloud App Security.
   Pour plus d'informations, consultez [Déploiement étendu](scoped-deployment.md).

-   **Alerte de violation d’application pour les applications découvertes**<br>
 Nous proposons désormais une alerte intégrée qui vous avertit en cas de violation d’une des applications découvertes du client. L’alerte précise la date et l’heure de la violation ainsi que les utilisateurs qui ont ouvert l’application, puis vous dirige vers des sources publiques contenant des informations sur cette violation.

-   **Nouveau serveur de messagerie**<br>
 Le serveur de messagerie de Cloud App Security a été modifié et utilise d’autres plages d’adresses IP. Pour être certain de recevoir les notifications, ajoutez les nouvelles adresses IP à votre liste verte anti-spam. Pour les utilisateurs qui souhaitent personnaliser leurs notifications, Microsoft Cloud App Security permet de le faire automatiquement à l’aide de MailChimp®, un service de messagerie tiers. Pour obtenir la liste des adresses IP du serveur de messagerie et des instructions sur l’utilisation de MailChimp, consultez les rubriques [Configuration requise pour le réseau](https://docs.microsoft.com/cloud-app-security/network-requirements#email-server) et [Paramètres de messagerie](mail-settings.md).


## <a name="cloud-app-security-release-123"></a>Cloud App Security version 123

Publication : 13 mai 2018

- **Délimitation des stratégies de détection d’anomalie** :<br>
Les stratégies de détection d’anomalie peuvent désormais être délimitées. Cela vous permet, pour chaque stratégie de détection d’anomalie, d’inclure ou d’exclure certains utilisateurs ou groupes. Par exemple, vous pouvez configurer l’option Activité à partir de pays peu fréquents de manière à ignorer un utilisateur qui voyage fréquemment. 


## <a name="cloud-app-security-release-122"></a>Cloud App Security version 122
Publication : 29 avril 2018

-   Lancement progressif : vous pouvez maintenant **définir des autorisations administratives pour les administrateurs Microsoft Cloud App Security pour chaque application**. Par exemple, vous pouvez définir un utilisateur spécifique en tant qu’administrateur de la Suite G uniquement. Cela permet à l’utilisateur d’afficher et de modifier les informations de Microsoft Cloud App Security uniquement lorsqu’il se rapporte exclusivement à la Suite G. Pour plus d’informations, consultez [Gestion des accès d’administration](manage-admins.md).
- Lancement progressif : les **rôles d’administrateur Okta sont désormais visibles** dans Microsoft Cloud App Security et sont disponibles pour chaque rôle en tant que balise sous **Paramètres** > **Groupes d’utilisateurs**.


## <a name="cloud-app-security-release-121"></a>Cloud App Security version 121
Publication : 22 avril 2018

-   La préversion publique du **contrôle d’application d’accès conditionnel (anciennement appelé Proxy Cloud App Security)** a été enrichie de fonctionnalités qui approfondissent la visibilité et le contrôle de diverses applications. Vous pouvez à présent créer une stratégie de session avec un filtre *Type d’activité*, pour surveiller et bloquer un éventail d’activités propres à l’application. Ce nouveau filtre augmente les fonctionnalités existantes de contrôle de téléchargement de fichiers pour vous fournir un contrôle total sur les applications de votre organisation. Il fonctionne avec l’accès conditionnel Azure Active Directory pour offrir une visibilité en temps réel et un contrôle des sessions utilisateur présentant un risque (par exemple, les sessions avec des collaborateurs B2B ou des utilisateurs d’appareils non gérés). Pour plus d’informations, consultez [Stratégies de session](session-policy-aad.md).
-   Lancement progressif : les **stratégies de détection d’anomalie de Cloud App Security ont été améliorées** de sorte à inclure deux nouveaux types de détection des menaces : l’activité de ransomware et l’activité des utilisateurs en fin de contrat. Cloud App Security a étendu ses capacités de détection de ransomware à la détection d’anomalie pour garantir une couverture plus complète contre les attaques de ransomware complexes. Fort de notre expertise en recherche dans la sécurité visant à identifier les modèles comportementaux qui reflètent des activités de ransomware, Cloud App Security assure une protection complète et solide. L’activité des utilisateurs en fin de contrat vous permet de surveiller les comptes des utilisateurs en fin de contrat, qui ont été peut-être été déprovisionnés des applications d’entreprise, mais qui, dans de nombreux cas, conservent toujours l’accès à certaines ressources de l’entreprise. Pour plus d’informations, consultez [Obtenir instantanément une détection des anomalies et une analytique comportementale](anomaly-detection-policy.md).


## <a name="cloud-app-security-release-120"></a>Cloud App Security version 120
Publication : 8 avril 2018

-   Pour Office 365 et Azure AD, nous développons progressivement la possibilité de détecter les applications internes en tant qu’activités de compte d’utilisateur effectuées par les applications Office 365 et Azure AD (internes et externes). Cela vous permet de créer des stratégies qui vous avertissent si une application effectue des activités inattendues et non autorisées. 
-   Lors de l’exportation d’une liste d’autorisations d’application au format csv, des champs supplémentaires, comme l’éditeur, le niveau d’autorisation et l’utilisation de la Communauté, sont ajoutés pour vous aider dans le processus d’investigation et de conformité.
-   L’application connectée ServiceNow a été améliorée pour que les activités de service interne ne soient plus enregistrées comme ayant été effectuées par « Invité » et ne déclenchent plus d’alertes fausses positives. Ces activités sont maintenant représentées par N/A comme toutes les autres applications connectées.


## <a name="cloud-app-security-release-119"></a>Cloud App Security version 119
Date de publication : 18 mars 2018

-   La page des plages d’adresses IP contient les adresses IP intégrées qui sont découvertes par Cloud App Security. Cela inclut les adresses IP des services cloud identifiés, comme Azure et Office 365, ainsi que le flux de Threat Intelligence qui enrichit automatiquement les adresses IP avec des informations sur les adresses IP risquées connues. 
-   Lorsque Cloud App Security tente d’exécuter une action de gouvernance sur un fichier, mais échoue parce que le fichier est verrouillé, il retente automatiquement l’action de gouvernance. 

## <a name="cloud-app-security-release-118"></a>Cloud App Security version 118
Date de publication : 4 mars 2018

- Vous pouvez désormais tirer parti de la découverte du Shadow IT de Microsoft Cloud App Security et des fonctions de surveillance de vos propres applications personnalisées propriétaires. La nouvelle possibilité d’ajouter des applications personnalisées à Cloud Discovery vous permet de surveiller l’utilisation des applications et d’être averti des modifications apportées au modèle d’utilisation. Pour plus d’informations, consultez [Protection de vos applications personnalisées](cloud-discovery-custom-apps.md). Cette fonctionnalité est déployée progressivement.

- Les pages **Paramètres** du portail Cloud App Security ont été repensées. La nouvelle conception consolide toutes les pages de paramètres et intègre une fonctionnalité de recherche et un design amélioré. 

- Cloud Discovery prend désormais en charge les pare-feu Barracuda F-Series et Barracuda F-Series Firewall Web Log Streaming.

- La fonctionnalité de recherche dans les pages Utilisateur et Adresse IP permet maintenant la saisie semi-automatique, ce qui facilite vos recherches.

- Vous pouvez désormais effectuer des actions en bloc dans les pages Exclure des entités et Exclure une adresse IP. Vous pouvez ainsi sélectionner plus facilement plusieurs utilisateurs, groupes ou adresses IP, et les exclure de l’analyse dans le cadre de la solution Cloud Discovery de votre organisation. 

## <a name="cloud-app-security-release-117"></a>Cloud App Security version 117
Date de publication : 20 février 2018

-   L’intégration approfondie de Cloud App Security avec Azure Information Protection vous permet désormais de protéger des fichiers dans G Suite. Cette fonctionnalité en préversion publique vous permet d’analyser et de classifier des fichiers dans G Suite, et d’appliquer automatiquement des étiquettes Azure Information Protection pour la protection. Pour plus d’informations, consultez [Intégration d’Azure Information Protection](azip-integration.md).

-   Cloud Discovery prend désormais en charge [Digital Arts i-FILTER](http://www.daj.jp/en/products/if/).

-   Le tableau des agents SIEM inclut désormais plus de détails pour faciliter la gestion.

## <a name="cloud-app-security-release-116"></a>Cloud App Security version 116
Date de publication : 4 février 2018
- La stratégie de détection d’anomalie de Cloud App Security a été améliorée grâce à de nouvelles **détections basées sur des scénarios**, notamment les activités de type Voyage impossible, les échecs de tentatives de connexion multiples et les activités provenant d’adresses IP suspectes. Les nouvelles stratégies sont automatiquement activées et fournissent une solution de détection des menaces prête à l’emploi pour votre environnement cloud. En outre, les nouvelles stratégies exposent davantage de données à partir du moteur de détection de Cloud App Security afin d’accélérer le processus d’investigation, et contiennent des menaces permanentes. Pour plus d’informations, consultez [Obtenir instantanément une détection des anomalies et une analytique comportementale](https://docs.microsoft.com/cloud-app-security/anomaly-detection-policy).

- Déploiement progressif : Cloud App Security met désormais en corrélation les utilisateurs et leurs comptes dans les applications SaaS. Cela vous permet d’examiner facilement toutes les activités d’un utilisateur, dans toutes ses différentes applications SaaS corrélées, peu importe l’application ou le compte qu’il a utilisé.  

-   Déploiement progressif : Cloud App Security prend désormais en charge plusieurs instances de la même application connectée. Si vous utilisez plusieurs instances, par exemple, Salesforce (une pour le service commercial et une autre pour le département marketing), vous pourrez les connecter à la fois à Cloud App Security et les gérer à partir de la même console pour créer des stratégies granulaires et obtenir une investigation plus approfondie. 

- Les analyseurs de Cloud Discovery prennent désormais en charge deux formats de point de contrôle supplémentaires, XML et KPC.



## <a name="cloud-app-security-release-115"></a>Cloud App Security version 115
Publiée le 21 janvier 2018

- Cette version offre une meilleure expérience lors de la sélection de dossiers spécifiques dans les stratégies de fichier. Vous pouvez désormais facilement afficher et sélectionner plusieurs dossiers à inclure dans une stratégie. 
- Dans la page **Applications découvertes** : 
  - La fonctionnalité de balisage en bloc vous permet d’appliquer des balises personnalisées (en plus des balises approuvées et non approuvées). 
  - Lorsque vous **générez un rapport d’adresses IP** ou **générez un rapport d’utilisateurs**, les rapports exportés incluent désormais les informations sur le trafic provenant d’applications approuvées non approuvées. 
- Vous pouvez maintenant demander à l’équipe Microsoft Cloud App Security un nouveau connecteur d’application API directement depuis le portail, dans la page **Connecter une application**. 


## <a name="cloud-app-security-release-114"></a>Cloud App Security version 114
Publiée le 7 janvier 2018

- À compter de la version 114, nous allons progressivement déployer la possibilité de créer et d’enregistrer des requêtes personnalisées dans les pages du journal d’activité et des applications découvertes. Les requêtes personnalisées vous permettent de créer des modèles de filtre qui peuvent être réutilisés pour des examens approfondis. De plus, des **requêtes suggérées** ont été ajoutées pour fournir des modèles d’examen prédéfinis permettant de filtrer vos activités et vos applications découvertes. Les **requêtes suggérées** incluent des filtres personnalisés pour identifier les risques comme les activités d’emprunt d’identité, les activités d’administrateur, les applications de stockage cloud non conformes présentant des risques, les applications d’entreprise avec un chiffrement faible et les risques de sécurité. Vous pouvez utiliser les **requêtes suggérées** comme point de départ, les modifier comme vous le souhaitez, puis les enregistrer en tant que nouvelle requête. Pour plus d’informations, consultez [Filtres d’activité et requêtes](activity-filters-queries.md) et [Filtres d’application découverte](discovered-app-queries.md).
 
- Vous pouvez désormais vérifier l’état actuel du service Cloud App Security en accédant à [status.cloudappsecurity.com](https://status.cloudappsecurity.com) ou directement à partir du portail en cliquant sur **Aide**>**État du système**. 
 


## <a name="see-also"></a>Voir aussi  

Pour obtenir une description des versions antérieures à celles répertoriées ici, consultez [Versions précédentes de Microsoft Cloud App Security](release-note-archive.md).

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  
