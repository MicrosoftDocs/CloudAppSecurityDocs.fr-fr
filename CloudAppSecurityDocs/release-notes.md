---
title: Nouveautés dans Cloud App Security
description: Cet article est mis à jour fréquemment pour vous informer des nouveautés de la dernière version de Cloud App Security.
ms.date: 10/25/2020
ms.topic: overview
ms.openlocfilehash: a98d6305b20b7cca12754edc8804781d20dd0f4e
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96315478"
---
# <a name="whats-new-with-microsoft-cloud-app-security"></a>Nouveautés dans Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

Cet article est mis à jour fréquemment pour vous informer des nouveautés de la dernière version de Cloud App Security.

Flux RSS : Recevez une notification quand cette page est mise à jour en copiant et collant l’URL suivante dans votre lecteur de flux : `https://docs.microsoft.com/api/search/rss?search=%22This+article+is+updated+frequently+to+let+you+know+what%27s+new+in+the+latest+release+of+Cloud+App+Security%22&locale=en-us`

> [!IMPORTANT]
>
> Les noms des produits Microsoft de protection contre les menaces changent. Vous trouverez [ici](https://www.microsoft.com/security/blog/?p=91813) plus d’informations sur ce sujet et sur les autres mises à jour. Nous utiliserons les nouveaux noms dans les prochaines versions.

## <a name="cloud-app-security-release-187-and-188"></a>Cloud App Security versions 187 et 188

Publication : 22 novembre 2020

- **Nouvelle intégration de Shadow IT à Menlo Security**  
Nous avons ajouté une intégration native à Menlo Security, ce qui vous fournit la visibilité Shadow IT de l’utilisation des applications et le contrôle de l’accès aux applications. Pour plus d’informations, consultez [Intégrer Cloud App Security à Menlo Security](menlo-integration.md).

- **Nouvel analyseur de journal WatchGuard Cloud Discovery**  
Cloud App Security Cloud Discovery analyse une large gamme de journaux de trafic pour classer et noter les applications. Cloud Discovery comprend désormais un analyseur de journal intégré pour prendre en charge le format WatchGuard. Consultez la liste des analyseurs de journal pris en charge dans [Pare-feu et proxys pris en charge](set-up-cloud-discovery.md#supported-firewalls-and-proxies).

- **Nouvelle autorisation pour rôle d’administrateur général Cloud Discovery**  
Cloud App Security permet désormais aux utilisateurs avec le rôle d’administrateur général Cloud Discovery de créer des jetons d’API et d’utiliser toutes les API Cloud Discovery associées. Pour plus d’informations sur le rôle, consultez [Rôles d’administrateurs Cloud App Security intégrés](manage-admins.md#built-in-cloud-app-security-admin-roles).

- **Curseur de sensibilité amélioré : voyage impossible**  
Nous avons mis à jour le curseur de sensibilité pour un voyage impossible afin de configurer différents niveaux de sensibilité pour différentes étendues utilisateur, ce qui permet un contrôle accru sur la fidélité des alertes pour les étendues utilisateur. Par exemple, vous pouvez définir un niveau de sensibilité plus élevé pour les administrateurs que pour les autres utilisateurs de l’organisation. Pour plus d’informations sur cette stratégie de détection des anomalies, consultez [Voyage impossible](anomaly-detection-policy.md#impossible-travel).

- **Suffixe d’URL de proxy amélioré pour les contrôles de session (déploiement progressif)**  
Le 7 juin 2020, nous avons commencé à déployer progressivement nos contrôles de session de proxy améliorés en vue d’utiliser un suffixe unifié qui n’inclut pas de régions nommées. Par exemple, les utilisateurs verront le suffixe `<AppName>.mcas.ms` au lieu de `<AppName>.<Region>.cas.ms`. Si vous bloquez régulièrement des domaines dans vos passerelles ou appliances réseau, veillez à mettre sur la liste verte tous les domaines qui figurent sous [Contrôles d’accès et de session](network-requirements.md#access-and-session-controls).

## <a name="cloud-app-security-release-184-185-and-186"></a>Cloud App Security versions 184, 185 et 186

Publication : 25 octobre 2020

- **Nouvelle expérience améliorée de supervision et de gestion des alertes**  
Dans le cadre de l’amélioration continue de la supervision et de la gestion des alertes, la page Alertes de Cloud App Security a été optimisée sur la base de vos commentaires. Dans l’expérience améliorée, les états **Résolu** et **Ignoré** sont remplacés par l’état **Fermé**, accompagné d’un type de résolution. [En savoir plus](monitor-alerts.md#deployment-of-our-enhanced-alert-monitoring-and-management-experience)

- **Nouveau paramètre de gravité globale des signaux envoyés à 	Microsoft Defender pour point de terminaison**  
Nous avons ajouté la possibilité de définir le paramètre de gravité globale des signaux envoyés à Microsoft Defender pour point de terminaison. Pour plus d’informations, consultez [Comment intégrer Microsoft Defender pour point de terminaison à Cloud App Security](mde-integration.md#how-to-integrate-microsoft-defender-for-endpoint-with-cloud-app-security).

- **Nouveau rapport sur les recommandations de sécurité**  
Cloud App Security effectue des évaluations de la configuration de la sécurité des environnements Azure, Amazon Web Services (AWS) et Google Cloud Platform (GCP). Il offre ainsi des insights sur les lacunes de la configuration de la sécurité dans un environnement multicloud. Vous pouvez à présent exporter des rapports détaillés sur les recommandations de sécurité pour superviser, comprendre et personnaliser vos environnements cloud, et ainsi mieux protéger votre organisation. Pour plus d’informations sur l’exportation du rapport, consultez [Rapport sur les recommandations de sécurité](security-config.md#security-recommendations-report).

- **Suffixe d’URL de proxy amélioré pour les contrôles de session (déploiement progressif)**  
Le 7 juin 2020, nous avons commencé à déployer progressivement nos contrôles de session de proxy améliorés en vue d’utiliser un suffixe unifié qui n’inclut pas de régions nommées. Par exemple, les utilisateurs verront le suffixe `<AppName>.mcas.ms` au lieu de `<AppName>.<Region>.cas.ms`. Si vous bloquez régulièrement des domaines dans vos passerelles ou appliances réseau, veillez à mettre sur la liste verte tous les domaines qui figurent sous [Contrôles d’accès et de session](network-requirements.md#access-and-session-controls).

- **Mises à jour du catalogue d’applications cloud**  
Nous avons apporté les mises à jour suivantes à notre catalogue d’applications cloud :

  - Le Centre d’administration Teams est devenu une application autonome.
  - Le Centre d’administration Microsoft Office 365 a été renommé Portail Office.

- **Mise à jour terminologique**  
Nous avons remplacé le terme **machine** par le terme **appareil** dans le cadre de l’effort général de Microsoft d’harmoniser la terminologie entre les produits.

## <a name="cloud-app-security-release-182-and-183"></a>Cloud App Security versions 182 et 183

Publication : 6 septembre 2020

- **Contrôles d’accès et de session pour le portail Azure GA**  
Le contrôle d’application par accès conditionnel pour le portail Azure est maintenant en disponibilité générale. Pour plus d’informations sur la configuration de ces contrôles, consultez le [Guide de déploiement](proxy-deployment-aad.md).

## <a name="cloud-app-security-release-181"></a>Cloud App Security version 181

Publication : 9 août 2020

- **Nouvel analyseur de journal Menlo Security Cloud Discovery**  
Cloud App Security Cloud Discovery analyse une large gamme de journaux de trafic pour classer et noter les applications. Cloud Discovery comprend désormais un analyseur de journal intégré pour prendre en charge le format CEF Menlo Security. Consultez la liste des analyseurs de journal pris en charge dans [Pare-feu et proxys pris en charge](set-up-cloud-discovery.md#supported-firewalls-and-proxies).

- **Le nom Azure Active Directory (AD) Cloud App Discovery s’affiche dans le portail**  
Pour les licences Azure AD P1 et P2, nous avons remplacé le nom du produit par **Cloud App Discovery** dans le portail. En savoir plus sur [Cloud App Discovery](editions-cloud-app-security-aad.md).

## <a name="cloud-app-security-release-179-and-180"></a>Cloud App Security versions 179 et 180

Publication le 26 juillet 2020

- **Nouvelle détection d’anomalie : Activités suspectes de téléchargement de fichier d’application OAuth**  
Nous avons étendu nos détections d’anomalies pour inclure des activités de téléchargement suspectes par une application OAuth. La nouvelle détection est maintenant prête à l’emploi et automatiquement activée pour vous alerter quand une application OAuth télécharge plusieurs fichiers à partir de Microsoft SharePoint ou Microsoft OneDrive d’une manière inhabituelle pour l’utilisateur.

- **Améliorations des performances à l’aide de la mise en cache de proxy pour les contrôles de session (déploiement progressif)**  
Nous avons apporté d’autre améliorations de performances à nos contrôles de session, en améliorant nos mécanismes de mise en cache de contenu. Le service amélioré est encore plus rationalisé et fournit une réactivité accrue lors de l’utilisation de contrôles de session. Notez que les contrôles de session ne mettent pas en cache le contenu privé, respectant ainsi les standards appropriés selon lesquels seul le contenu partagé (public) est mis en cache. Pour plus d’informations, consultez [Fonctionnement du contrôle de session](proxy-intro-aad.md#how-session-control-works).

- **Nouvelle fonctionnalité : Enregistrement des requêtes de configuration de la sécurité**  
Nous avons ajouté la possibilité d’enregistrer des requêtes pour nos filtres de tableau de bord de configuration de sécurité pour Azure, Amazon Web Services (AWS) et Google Cloud Platform (GCP). Cela peut faciliter encore plus les futures investigations en réutilisant les requêtes courantes. Apprenez-en davantage sur nos [Recommandations de configuration de la sécurité](security-config.md).

- **Amélioration des alertes de détection d’anomalie**  
Nous avons étendu les informations que nous fournissons pour les alertes de détection d’anomalie afin d’inclure un mappage vers la tactique MITRE ATT\&CK correspondante. Ce mappage vous aidera à comprendre la phase et l’impact de l’attaque et à mener vos investigations. Découvrez plus en détail comment [Investiguer les alertes de détection d’anomalie](investigate-anomaly-alerts.md).

- **Logique de détection améliorée : Activité ransomware**  
Nous avons mis à jour la logique de détection pour l’activité ransomware afin d’offrir une meilleure précision et un volume d’alertes réduit. Pour plus d’informations sur cette stratégie de détection des anomalies, consultez [Activité ransomware](anomaly-detection-policy.md#ransomware-activity).

- **Rapports de posture de sécurité des identités : Visibilité des étiquettes**  
Nous avons ajouté des étiquettes d’entité aux rapports de posture de sécurité des identités pour fournir des insights supplémentaires sur les entités. Par exemple, l’étiquette **Sensible** peut vous aider à identifier les utilisateurs à risque et à classer par ordre de priorité vos investigations. Découvrez plus en détail l’[Investigation des utilisateurs à risque](tutorial-ueba.md).

## <a name="cloud-app-security-release-178"></a>Cloud App Security version 178

Publication : 28 juin 2020

- **Nouvelles configurations de sécurité pour Google Cloud Platform (déploiement graduel)**  
Nous avons étendu nos configurations de sécurité multicloud afin de fournir des recommandations de sécurité pour Google Cloud Platform, basées sur le benchmark GCP CIS. Avec cette nouvelle fonctionnalité, Cloud App Security offre aux organisations une seule et même vue pour surveiller l’état de conformité sur toutes les plateformes cloud, notamment les [abonnements Azure](security-config-azure.md), les [comptes AWS](security-config-aws.md) et maintenant les [projets GCP](security-config-gcp.md).

- **Nouveaux connecteurs d’application en GA**  
Nous avons ajouté les connecteurs d’application suivants à notre portefeuille de connecteurs d’API en disponibilité générale pour vous donner plus de visibilité et de contrôle sur la façon dont vos applications sont utilisées dans votre organisation :
  - [GitHub Enterprise Cloud](protect-github.md)
  - [Google Cloud Platform](protect-gcp.md)
  - [Workday](protect-workday.md)

- **Nouvelle détection de programmes malveillants en temps réel en GA**  
Nous avons étendu nos contrôles de session afin de détecter les logiciels malveillants potentiels à l’aide de Microsoft Threat Intelligence lors du chargement ou du téléchargement de fichiers. La nouvelle détection est en disponibilité générale et peut être configurée pour bloquer automatiquement les fichiers identifiés comme des programmes malveillants potentiels. Pour plus d’informations, consultez [Bloquer les logiciels malveillants lors du chargement](session-policy-aad.md#block-malware-on-upload).

- **Amélioration des contrôles d’accès et de session avec n’importe quel IdP en GA**  
La prise en charge des contrôles d’accès et de session pour les applications SAML configurées avec n’importe quel fournisseur d’identité est maintenant en disponibilité générale. Pour plus d’informations sur la configuration de ces contrôles, consultez le [Guide de déploiement](proxy-deployment-aad.md).

- **Amélioration des investigations sur les ordinateurs à risque**  
Cloud App Security permet d’identifier les ordinateurs à risque dans le cadre de votre investigation de découverte du Shadow IT. Nous avons ajouté le **Niveau de risque des ordinateurs** Microsoft Defender Advanced Threat Protection dans la page **Ordinateurs** pour donner aux analystes plus de contexte lors de l’investigation des ordinateurs de votre organisation. Pour plus d’informations, consultez [Examen des appareils dans Cloud App Security](mde-integration.md#investigate-devices-in-cloud-app-security).

- **Nouvelle fonctionnalité : Désactivation en libre-service des connecteurs d’application (déploiement progressif)**  
Nous avons ajouté la possibilité de désactiver les connecteurs d’application directement dans Cloud App Security. Pour plus d’informations, consultez [Désactiver les connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md#disable-app-connectors).

## <a name="cloud-app-security-release-177"></a>Cloud App Security version 177

Publication : 14 juin 2020

- **Nouvelle détection de programmes malveillants en temps réel (préversion, déploiement progressif)**  
Nous avons étendu nos contrôles de session afin de détecter les logiciels malveillants potentiels à l’aide de Microsoft Threat Intelligence lors du chargement ou du téléchargement de fichiers. La nouvelle détection est prête à l’emploi et peut être configurée pour bloquer automatiquement les fichiers identifiés comme des programmes malveillants potentiels. Pour plus d’informations, consultez [Bloquer les logiciels malveillants lors du chargement](session-policy-aad.md#block-malware-on-upload).

- **Nouvelle prise en charge des jetons d’accès pour les contrôles d’accès et de session**  
Nous avons ajouté la possibilité de traiter les demandes de jeton d’accès et de code en tant que connexions lors de l’intégration d’applications aux contrôles d’accès et de session. Pour utiliser des jetons, cliquez sur l’icône Paramètres représentée par une roue dentée, sélectionnez **Contrôle d’application par accès conditionnel**, modifiez l’application appropriée (cliquez sur le menu à trois points > **Modifier l’application**), sélectionnez **Traiter les demandes de jeton d’accès et de code en tant que connexions à l’application**, puis cliquez sur **Enregistrer**. Pour plus d’informations sur l’intégration des applications, consultez [Intégrer et déployer une application](proxy-deployment-any-app.md) et [Déployer des applications proposées](proxy-deployment-aad.md).

- **Suffixe d’URL de proxy amélioré pour les contrôles de session (déploiement progressif)**  
Le 7 juin 2020, nous avons commencé à déployer progressivement nos contrôles de session de proxy améliorés en vue d’utiliser un suffixe unifié qui n’inclut pas de régions nommées. Par exemple, les utilisateurs verront le suffixe `<AppName>.mcas.ms` au lieu de `<AppName>.<Region>.cas.ms`. Si vous bloquez régulièrement des domaines dans vos passerelles ou appliances réseau, veillez à mettre sur la liste verte tous les domaines qui figurent sous [Contrôles d’accès et de session](network-requirements.md#access-and-session-controls).

- **Nouvelle documentation**  
Le contenu suivant a été ajouté à la documentation Cloud App Security :

  - **[Utilisation de l’API REST Cloud App Security](api-introduction.md)**  : Découvrez nos fonctionnalités API et commencez à intégrer vos applications à Cloud App Security.
  - **[Investiguer les alertes de détection d’anomalie](investigate-anomaly-alerts.md)**  : Familiarisez-vous avec les alertes UEBA disponibles, notamment avec leur signification, les risques qu’elles présentent, l’ampleur de la violation et l’action que vous pouvez entreprendre pour résoudre le problème.

## <a name="cloud-app-security-release-176"></a>Cloud App Security version 176

Publication : 31 mai 2020

- **Nouvelle fonctionnalité de confidentialité de l’activité**  
Nous avons amélioré votre capacité à déterminer de manière granulaire les utilisateurs que vous souhaitez surveiller avec la possibilité de rendre les activités privées. Cette nouvelle fonctionnalité vous permet de spécifier des utilisateurs en fonction de l’appartenance à un groupe dont les activités seront masquées par défaut. Seuls les administrateurs autorisés ont la possibilité de choisir d’afficher ces activités privées, chaque instance étant auditée dans le journal de gouvernance. Pour plus d’informations, consultez [Confidentialité de l’activité](activity-privacy.md).

- **Nouvelle intégration avec la galerie Azure Active Directory (Azure AD)**  
Nous avons exploité notre intégration native avec Azure AD pour vous permettre d’accéder directement à une application depuis le catalogue d’applications cloud à son application de la galerie Azure AD correspondante, et de la gérer dans la galerie. Pour plus d’informations, consultez [Gérer des applications avec la galerie Azure AD](tutorial-shadow-it.md#gallery-apps).

- **Nouvelle option de commentaires disponible dans les stratégies sélectionnées**  
Nous souhaitons recevoir vos commentaires et découvrir comment nous pouvons vous aider. Désormais, une nouvelle boîte de dialogue de commentaires vous donne la possibilité de contribuer à améliorer Cloud App Security, lors de la création, de la modification ou de la suppression d’un fichier, de la détection d’anomalies ou d’une stratégie de session.

- **Suffixe d’URL de proxy amélioré pour les contrôles de session (déploiement progressif)**  
À partir du 7 juin 2020, nous déployons progressivement nos contrôles de session de proxy améliorés pour utiliser un suffixe unifié qui n’inclut pas de régions nommées. Par exemple, les utilisateurs verront le suffixe `<AppName>.mcas.ms` au lieu de `<AppName>.<Region>.cas.ms`. Si vous mettez régulièrement des domaines sur la liste rouge dans vos passerelles ou appliances réseau, veillez à mettre tous les domaines listés sous [Contrôles d’accès et de session](network-requirements.md#access-and-session-controls) sur la liste verte.

- **Améliorations des performances pour les contrôles de session (déploiement progressif)**  
Nous avons amélioré de manière significative les performances réseau de notre service proxy. Le service amélioré est encore plus rationalisé et fournit une réactivité accrue lors de l’utilisation de contrôles de session.

- **Nouvelle détection d’activité à risque : échec de connexion inhabituel**  
Nous avons étendu notre fonctionnalité actuelle pour détecter les comportements à risque. La nouvelle détection est désormais prête à l’emploi et automatiquement activée pour vous avertir en cas d’échec inhabituel d’une tentative de connexion. Les échecs inhabituels de tentatives de connexion peuvent indiquer une attaque par force brute potentielle de type *password-spray* (vaporisation) (également appelée méthode *low and slow*). Cette détection a un impact sur le [score de priorité d’investigation](tutorial-ueba.md) global de l’utilisateur.

- **Expérience de tableau améliorée**  
Nous avons ajouté la possibilité de redimensionner les largeurs de colonne de tableau, afin de pouvoir élargir ou réduire les colonnes, de personnaliser et d’améliorer la façon dont vous consultez les tableaux. Vous avez également la possibilité de restaurer la disposition d’origine en sélectionnant le menu Paramètres du tableau et en choisissant **Largeur par défaut**.

## <a name="cloud-app-security-release-175"></a>Cloud App Security version 175

Publication : 17 mai 2020

- **Nouvelle intégration de Shadow IT Discovery à Corrata (préversion)**  
Nous avons ajouté une intégration native à Corrata, ce qui vous fournit la visibilité Shadow IT de l’utilisation des applications et le contrôle de l’accès aux applications. Pour plus d’informations, consultez [Intégrer Cloud App Security à Corrata](corrata-integration.md).

- **Nouveaux analyseurs de journal Cloud Discovery**  
Cloud App Security Cloud Discovery analyse une large gamme de journaux de trafic pour classer et noter les applications. Cloud Discovery comprend désormais un analyseur de journal intégré pour prendre en charge Corrata et Cisco ASA avec les formats de journaux FirePOWER 6.4. Consultez la liste des analyseurs de journal pris en charge dans [Pare-feu et proxys pris en charge](set-up-cloud-discovery.md#supported-firewalls-and-proxies).

- **Tableau de bord amélioré (lancement progressif)** Dans le cadre de nos améliorations continues de la conception du portail, nous déployons maintenant progressivement le tableau de bord Cloud App Security amélioré. Le tableau de bord, qui a été modernisé sur la base de vos commentaires, offre une expérience utilisateur améliorée avec du contenu et des données mis à jour. Pour plus d’informations, consultez [Déploiement progressif de notre tableau de bord amélioré](daily-activities-to-protect-your-cloud-environment.md).

- **Gouvernance améliorée : Confirmer que l’utilisateur est compromis pour les détections d’anomalies**  
Nous avons étendu nos actions de gouvernance actuelles pour les stratégies de détection des anomalies afin d’inclure **Confirmer que l’utilisateur est compromis** vous permettant de protéger de manière proactive votre environnement contre toute activité suspecte des utilisateurs. Pour plus d’informations, consultez [Actions de gouvernance des activités](governance-actions.md#activity-governance-actions).

## <a name="cloud-app-security-release-173-and-174"></a>Cloud App Security versions 173 et 174

Publication : 26 avril 2020

- **Nouveau format CEF de l’agent SIEM pour les alertes**  
Dans le cadre de notre effort pour enrichir les informations d’alerte fournies dans les fichiers CEF utilisés par les serveurs SIEM génériques, nous avons étendu le format pour inclure les champs client suivants :
  - Adresse IPv4
  - Adresse IPv6
  - Emplacement d’adresse IP

    Pour plus d’informations, voir [Format de fichier CEF](siem.md#sample-cloud-app-security-alerts-in-cef-format).
- **Logique de détection améliorée : voyage impossible**  
Nous avons mis à jour la logique de détection de Voyage impossible afin d’offrir une exactitude améliorée et un volume d’alertes réduit. Pour plus d’informations sur cette stratégie de détection des anomalies, consultez [Voyage impossible](anomaly-detection-policy.md#impossible-travel).

## <a name="cloud-app-security-release-172"></a>Cloud App Security version 172

Publication : 5 avril 2020

- **Amélioration des contrôles d’accès et de session avec n’importe quel IdP (préversion)**  
Les contrôles d’accès et de session prennent désormais en charge les applications SAML configurées avec n’importe quel fournisseur d’identité. La préversion publique de cette nouvelle fonctionnalité est désormais progressivement déployée. Pour configurer ces contrôles, consultez le [Guide de déploiement](proxy-deployment-aad.md).

- **Nouvelle désanonymisation en bloc des utilisateurs et des ordinateurs**  
Nous avons étendu et simplifié le processus de désanonymisation d’un ou plusieurs utilisateurs et ordinateurs en cours d’investigation. Pour plus d’informations sur la désanonymisation en bloc, consultez [Fonctionnement de l’anonymisation des données](cloud-discovery-anonymizer.md#how-data-anonymization-works).

## <a name="cloud-app-security-release-170-and-171"></a>Cloud App Security versions 170 et 171

Date de publication : 22 mars 2020

- **Nouvelle détection d’anomalie : région inhabituelle pour la ressource cloud (préversion)**  
Nous avons étendu notre fonctionnalité actuelle de détection de comportement anormal pour AWS. La nouvelle détection, maintenant disponible clé en main, est automatiquement activée pour vous avertir quand une ressource est créée dans une région AWS où l’activité n’est normalement pas réalisée. Les attaquants exploitent souvent les crédits AWS d’une organisation pour effectuer des activités malveillantes comme le minage de cryptomonnaie. La détection de ce type de comportement anormal peut aider à atténuer l’attaque.

- **Nouveaux modèles de stratégie d’activité pour Microsoft Teams**  
Cloud App Security fournit maintenant les nouveaux modèles de stratégie d’activité suivants, qui permettent de détecter des activités potentiellement suspectes dans Microsoft Teams :
  - **Changement de niveau d’accès (Teams) :** avertit lorsque le niveau d’accès d’une équipe passe de privé à public.
  - **Ajout d’un utilisateur externe (Teams) :** avertit lorsqu’un utilisateur externe est ajouté à une équipe.
  - **Suppression en masse (Teams) :** avertit lorsqu’un utilisateur supprime un grand nombre d’équipes.

- **Intégration d’Azure Active Directory (Azure AD) Identity Protection**  
Il est maintenant possible de contrôler la gravité des alertes Azure AD Identity Protection qui sont ingérées dans Cloud App Security. Par ailleurs, si ce n’est pas déjà fait, la détection **Connexion risquée Azure AD** est automatiquement activée de façon à ingérer les alertes de niveau de gravité élevé. Pour plus d’informations, consultez [Intégration d’Azure Active Directory Identity Protection](aadip-integration.md).

## <a name="cloud-app-security-release-169"></a>Cloud App Security version 169

Date de publication : 1er mars 2020

- **Nouvelle détection pour Workday**  
Nous avons étendu nos alertes actuelles sur les comportements anormaux pour Workday. Les nouvelles alertes incluent les détections de géolocalisation d’utilisateur suivantes :
  - [Activité depuis des adresses IP anonymes](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses)
  - [Activité à partir de pays peu fréquents](anomaly-detection-policy.md#activity-from-infrequent-country)
  - [Activité à partir d'adresses IP suspectes](anomaly-detection-policy.md#activity-from-suspicious-ip-addresses)
  - [Voyage impossible](anomaly-detection-policy.md#impossible-travel)

- **Collecte améliorée des journaux Salesforce**  
Cloud App Security prend désormais en charge le journal des événements horaires de Salesforce. Les journaux des événements horaires vous offrent une surveillance accélérée et en quasi temps réel des activités des utilisateurs. Pour plus d’informations, consultez [Connecter Salesforce](connect-salesforce-to-microsoft-cloud-app-security.md).

- **Prise en charge de la configuration de sécurité AWS à l’aide d’un compte principal**  
Cloud App Security prend désormais en charge l’utilisation d’un compte principal. La connexion de votre compte principal vous permet de recevoir des recommandations de sécurité pour tous les comptes membres dans toutes les régions. Pour plus d’informations sur la connexion à un compte principal, consultez [Connexion d’une configuration AWS Security à Cloud App Security](connect-aws-to-microsoft-cloud-app-security.md#how-to-connect-aws-security-configuration-to-cloud-app-security).

- **Prise en charge des contrôles de session pour les navigateurs modernes**  
Les contrôles de session Cloud App Security incluent désormais la prise en charge du nouveau navigateur Microsoft Edge basé sur Chromium. Alors que nous continuerons à prendre en charge les versions les plus récentes d’Internet Explorer et de la version héritée de Microsoft Edge, la prise en charge sera limitée et nous vous recommandons d’utiliser le nouveau navigateur Microsoft Edge.

## <a name="cloud-app-security-release-165-166-167-and-168"></a>Cloud App Security versions 165, 166, 167 et 168

Date de publication : 16 février 2020

- **Nouveau : bloquer les applications non approuvées avec Microsoft Defender ATP**  
Cloud App Security a étendu son intégration native à Microsoft Defender Advanced Threat Protection (ATP). Il est maintenant possible de bloquer l’accès aux applications marquées comme non approuvées avec la fonctionnalité de protection réseau de Microsoft Defender ATP. Pour plus d’informations, consultez [Bloquer l’accès aux applications cloud non approuvées](mde-integration.md#block-access-to-unsanctioned-cloud-apps).

- **Nouveau : détection d’anomalies dans l’application OAuth**  
Nous avons étendu notre capacité actuelle pour détecter un consentement de l’application OAuth malveillante. La nouvelle détection est désormais disponible prête à l’emploi et automatiquement activée pour vous avertir lorsqu’une application OAuth potentiellement malveillante est autorisée dans votre environnement. Cette détection tire parti de l’expertise en matière de recherche et de renseignement sur les menaces de Microsoft pour identifier les applications malveillantes.

- **Mises à jour du collecteur de journaux**  
Le collecteur de journaux basé sur Docker a été amélioré avec les mises à jour importantes suivantes :

  - Mise à niveau de la version du système d’exploitation du conteneur

  - Correctifs des vulnérabilités de sécurité Java

  - Mise à niveau du service Syslog

  - Améliorations de la stabilité et des performances

    Nous vous recommandons vivement de mettre à niveau votre environnement vers cette nouvelle version. Pour plus d’informations, consultez [Modes de déploiement du collecteur de journaux](discovery-docker.md#deployment-modes).

- **Prise en charge de ServiceNow New York**  
Cloud App Security prend désormais en charge la version la plus récente (New York) de ServiceNow. Pour en savoir plus sur la sécurisation de ServiceNow, consultez [Connecter ServiceNow à Microsoft Cloud App Security](connect-servicenow-to-microsoft-cloud-app-security.md).

- **Logique de détection améliorée : voyage impossible**  
Nous avons mis à jour la logique de détection de Voyage impossible afin d’offrir une couverture améliorée et une plus grande exactitude. Dans le cadre de cette mise à jour, nous avons également mis à jour la logique de détection pour un [voyage impossible à partir de réseaux d’entreprise](anomaly-detection-policy.md#impossible-travel).

- **Nouveau seuil pour les stratégies d’activité**  
Nous avons ajouté un seuil pour les [stratégies d’activité](user-activity-policies.md) afin de vous aider à gérer le volume d’alertes. Les stratégies qui déclenchent un grand nombre de correspondances pendant plusieurs jours sont automatiquement désactivées. Si vous recevez une alerte système à ce sujet, vous devriez essayer d’affiner les stratégies en ajoutant des filtres ou, si vous utilisez des stratégies à des fins de création de rapports, envisager de les enregistrer en tant que requêtes à la place.

## <a name="see-also"></a>Voir aussi

Pour obtenir une description des versions antérieures à celles répertoriées ici, consultez [Versions antérieures de Microsoft Cloud App Security](release-note-archive.md).

[!INCLUDE [Open support ticket](includes/support.md)]