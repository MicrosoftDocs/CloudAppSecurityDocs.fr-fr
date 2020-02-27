---
title: Nouveautés dans Cloud App Security
description: Cet article est mis à jour fréquemment pour vous informer des nouveautés de la dernière version de Cloud App Security.
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/08/2019
ms.topic: overview
ms.service: cloud-app-security
ms.collection: M365-security-compliance
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 7a2a4cffd2d69c606e5f00743b9bd544638e9bd9
ms.sourcegitcommit: 9fe879ce7f07933866191724de5f108f43e3f923
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2020
ms.locfileid: "77566918"
---
# <a name="whats-new-with-microsoft-cloud-app-security"></a>Nouveautés dans Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

Cet article est mis à jour fréquemment pour vous informer des nouveautés de la dernière version de Cloud App Security.

Flux RSS : Recevez une notification quand cette page est mise à jour en copiant et collant l’URL suivante dans votre lecteur de flux : `https://docs.microsoft.com/api/search/rss?search=%22This+article+is+updated+frequently+to+let+you+know+what%27s+new+in+the+latest+release+of+Cloud+App+Security%22&locale=en-us`

## <a name="cloud-app-security-release-165-166-167-and-168"></a>Cloud App Security versions 165, 166, 167 et 168

Date de publication : 16 février 2020

- **Nouveau : bloquer les applications non approuvées avec Microsoft Defender ATP**  
Cloud App Security a étendu son intégration native à Microsoft Defender Advanced Threat Protection (ATP). Vous pouvez désormais bloquer l’accès aux applications marquées comme non approuvées à l’aide de la fonctionnalité de protection réseau de Microsoft Defender ATP. Pour plus d’informations, consultez [Bloquer l’accès aux applications cloud non approuvées](wdatp-integration.md#block-access-to-unsanctioned-cloud-apps).

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
Nous avons mis à jour la logique de détection pour un voyage impossible afin d’offrir une couverture améliorée et une meilleure précision. Dans le cadre de cette mise à jour, nous avons également mis à jour la logique de détection pour un [voyage impossible à partir de réseaux d’entreprise](anomaly-detection-policy.md#impossible-travel).

- **Nouveau seuil pour les stratégies d’activité**  
Nous avons ajouté un seuil pour les [stratégies d’activité](user-activity-policies.md) afin de vous aider à gérer le volume d’alertes. Les stratégies qui déclenchent un grand nombre de correspondances pendant plusieurs jours sont automatiquement désactivées. Si vous recevez une alerte système à ce sujet, vous devriez essayer d’affiner les stratégies en ajoutant des filtres ou, si vous utilisez des stratégies à des fins de création de rapports, envisager de les enregistrer en tant que requêtes à la place.

## <a name="cloud-app-security-release-162-163-and-164"></a>Cloud App Security versions 162, 163 et 164

Publication : 8 décembre 2019

- **Modification des activités et alertes SIEM au format CEF**  
Le [format de l’URL du portail (CS1)](siem.md#sample-cloud-app-security-alerts-in-cef-format) pour les informations sur l’activité et les alertes envoyées par Cloud App Security aux SIEM est passé à `https://<tenant_name>.portal.cloudappsecurity.com` et ne contient plus l’emplacement du centre de données. Les clients qui utilisent des critères spéciaux pour l’URL du portail doivent mettre à jour le modèle pour refléter cette modification.

## <a name="cloud-app-security-release-160-and-161"></a>Cloud App Security versions 160 et 161

Publication : 3 novembre 2019

- **Données de découverte dans Azure Sentinel (préversion)**  
Cloud App Security s’intègre maintenant à Azure Sentinel. Le partage des données d’alerte et de découverte avec Azure Sentinel offre les avantages suivants :

  - Permettre la corrélation des données de découverte avec d’autres sources de données pour une analyse plus poussée.

  - Afficher les données dans Power BI à l’aide de tableaux de bord prêts à l’emploi ou créez vos propres visualisations.

  - Profitez de périodes de rétention plus longues avec Log Analytics.

  Pour plus d’informations, consultez [Intégration Azure Sentinel](siem-sentinel.md).

- **Connecteur Google Cloud Platform (préversion)**  
Cloud App Security étend ses fonctionnalités de surveillance IaaS au-delà d’Amazon Web Services et d’Azure, et prend désormais en charge Google Cloud Platform. Cela vous permet de vous connecter rapidement et de surveiller toutes vos charges de travail GCP avec Cloud App Security. La connexion vous offre un ensemble puissant d’outils pour protéger votre environnement GCP, notamment :

  - Visibilité de toutes les activités effectuées via la console d’administration et les appels d’API.

  - Création de stratégies personnalisées et utilisation de modèles prédéfinis pour créer des alertes en cas d’événements à risque.

  - Toutes les activités GCP sont contrôlées par notre moteur de détection des anomalies, qui vous signale automatiquement tout comportement suspect, notamment les voyages impossibles, les activités de masse suspectes et les activités provenant d’un nouveau pays.

  Pour plus d’informations, consultez [Connecter Google Cloud Platform à Microsoft Cloud App Security](connect-google-gcp-to-microsoft-cloud-app-security.md).

- **Nouveaux modèles de stratégie**  
Cloud App Security intègre maintenant de nouveaux modèles de stratégies d’activité pour de meilleures pratiques de sécurité Google Cloud Platform.

- **Analyseur de journal Cloud Discovery amélioré**  
Cloud App Security Cloud Discovery analyse une large gamme de journaux de trafic pour classer et noter les applications. Désormais, l’analyseur de journal intégré à Cloud Discovery prend en charge le format de journal Ironport WSA 10.5.1.

- **Page d’accueil utilisateur personnalisable pour les contrôles de session**  
Nous avons lancé la possibilité pour les administrateurs de personnaliser la page d’accueil que vos utilisateurs voient lors de la navigation vers une application à laquelle une stratégie de session est appliquée. Vous pouvez maintenant afficher le logo de votre organisation et personnaliser le message affiché. Pour commencer la personnalisation, accédez à la page **Paramètres** et, sous **Contrôle d’application d’accès au cloud**, sélectionnez **Analyse utilisateur**.

- **Nouvelles détections**  

  - **Modifications suspectes du service de journalisation AWS (préversion)** : Vous avertit lorsqu’un utilisateur apporte des modifications au service de journalisation CloudTrail. Par exemple, les attaquants désactivent souvent l’audit dans CloudTrail pour masquer les empreintes de leur attaque.

  - **Multiples activités de création de machines virtuelles** : Vous alerte lorsqu'un utilisateur effectue un nombre inhabituel d'activités de création de machines virtuelles par rapport à la référence apprise. S’applique désormais à AWS.

## <a name="cloud-app-security-release-159"></a>Cloud App Security version 159

Publication : 6 octobre 2019

- **Nouvel analyseur de journal Cloud Discovery ContentKeeper**  
Cloud App Security Cloud Discovery analyse une large gamme de journaux de trafic pour classer et noter les applications. Cloud Discovery intègre désormais un analyseur de journal intégré pour prendre en charge les formats de journaux ContentKeeper. Consultez la liste des analyseurs de journal pris en charge dans [Pare-feu et proxys pris en charge](set-up-cloud-discovery.md#supported-firewalls-and-proxies).

- **Nouvelles détections**  
Les nouvelles stratégies de détection d'anomalies suivantes sont prêtes à l’emploi et automatiquement activées :

  - **Activité suspecte de suppression d’e-mails (préversion)**  
    Vous avertit lorsqu'un utilisateur effectue des activités inhabituelles de suppression d'e-mails. Cette stratégie peut vous aider à détecter les piratages de boîtes aux lettres d’utilisateurs par des vecteurs d'attaque potentiels comme les communications de commande et de contrôle (C&C/C2) par e-mail.

  - **Multiples partages de rapports Power BI (préversion)**  
    Vous alerte lorsqu'un utilisateur effectue un nombre inhabituel d'activités de partage de rapports Power BI par rapport à la référence apprise.

  - **Multiples activités de création de machines virtuelles (préversion)**  
    Vous alerte lorsqu'un utilisateur effectue un nombre inhabituel d'activités de création de machines virtuelles par rapport à la référence apprise. S’applique actuellement à Azure.

  - **Multiples activités de suppression de stockage (préversion)**  
    Vous alerte lorsqu'un utilisateur effectue un nombre inhabituel d'activités de suppression de stockage par rapport à la référence apprise. S’applique actuellement à Azure.

## <a name="cloud-app-security-release-158"></a>Cloud App Security version 158

Publication : 15 septembre 2019

- **Personnaliser un nom de rapport exécutif Cloud Discovery**  
Le rapport exécutif Cloud Discovery vous donne une vue d’ensemble de l’utilisation du Shadow IT dans votre organisation. Vous avez maintenant la possibilité de personnaliser le nom du rapport avant de le générer. Pour plus d’informations, consultez [Générer un rapport exécutif Cloud Discovery](discovered-apps.md#generate-cloud-discovery-executive-report).

- **Rapport de vue d’ensemble des nouvelles stratégies**  
Cloud App Security détecte les correspondances de stratégie et, le cas échéant, consigne les alertes que vous pouvez utiliser pour mieux comprendre votre environnement cloud. Vous pouvez maintenant exporter un rapport de vue d’ensemble des stratégies avec des métriques d’alerte agrégées par stratégie pour vous aider à surveiller, à comprendre et à personnaliser vos stratégies afin de mieux protéger votre organisation. Pour plus d’informations sur l’exportation du rapport, consultez [Rapport de vue d’ensemble des stratégies](control-cloud-apps-with-policies.md#policies-overview-report).

## <a name="cloud-app-security-release-157"></a>Cloud App Security version 157

Publication : 1er septembre 2019

- **Rappel : Fin de la prise en charge de TLS 1.0 et 1.1 le 8 septembre**  
Microsoft transfère tous ses services en ligne vers Transport Layer Security (TLS) 1.2+ pour fournir le meilleur chiffrement de sa catégorie. Par conséquent, à partir du 8 septembre 2019, Cloud App Security ne prendra plus en charge TLS 1.0/1.1 et les connexions utilisant ces protocoles. Pour plus d'informations sur l’impact de ce changement, lisez [notre billet de blog](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/End-of-support-for-TLS-1-0-and-1-1-in-Microsoft-Cloud-App/ba-p/770507).

- **Nouvelle détection – Partage Microsoft Power BI suspect (préversion)**  
La nouvelle stratégie de partage de rapport Power BI suspect est désormais prête à l’emploi et automatiquement activée pour vous avertir lorsqu’un rapport Power BI potentiellement sensible est partagé de façon suspecte en dehors de votre organisation.

- **Nouvelle fonctionnalité d’exportation pour l’audit d’application OAuth**  
Cloud App Security audite toutes les activités d’autorisation OAuth, vous permettant ainsi de superviser et d’analyser les activités effectuées de manière approfondie. Désormais, vous pouvez également exporter les détails des utilisateurs qui ont autorisé une application OAuth spécifique, qui vous fournissent des informations supplémentaires sur les utilisateurs que vous pouvez ensuite utiliser pour une analyse plus poussée.

- **Audit d’événement Okta amélioré**  
Cloud App Security prend désormais en charge la nouvelle API de journal système publiée par Okta. Pour plus d’informations sur la connexion Okta, consultez [Connecter Okta](connect-okta-to-microsoft-cloud-app-security.md).

- **Connecteur Workday (préversion)**  
Un nouveau connecteur d’applications est désormais disponible pour Workday. Vous pouvez maintenant connecter Workday à Cloud App Security pour superviser les activités ainsi que protéger ses utilisateurs et activités. Pour plus d’informations, consultez [Se connecter à Workday](connect-workday-to-microsoft-cloud-app-security.md).

- **Évaluation améliorée du facteur de risque « Stratégie de mot de passe »**  
Le catalogue d’applications cloud offre désormais une évaluation granulaire du facteur de risque **Stratégie de mot de passe**. En pointant sur son icône d’informations, vous pouvez voir une répartition des stratégies spécifiques appliquées par l’application.

## <a name="cloud-app-security-release-156"></a>Cloud App Security version 156

Publication : 18 août 2019

- **Nouveaux analyseurs de journal Cloud Discovery**  
Cloud App Security Cloud Discovery analyse une large gamme de journaux de trafic pour classer et noter les applications. Cloud Discovery intègre désormais un analyseur de journaux intégré pour prendre en charge les formats de journaux Stormshield et Forcepoint LEEF.

- **Améliorations du journal d’activité**  
Cloud App Security offre désormais une meilleure visibilité des activités non classifiées effectuées par les applications dans votre environnement. Ces activités sont disponibles dans le journal d’activité ainsi que dans les stratégies d’activité. Pour voir les activités non classifiées, dans le filtre **Type**, sélectionnez **Non spécifié**. Pour plus d’informations sur les filtres d’activité, consultez [Filtres d’activité et requêtes](activity-filters-queries.md).

- **Amélioration des investigations sur les utilisateurs à risque**  
Cloud App Security permet d’identifier les utilisateurs à risque dans la page **Utilisateurs et comptes** par groupes, applications et même rôles spécifiques. Vous pouvez désormais également examiner les utilisateurs de votre organisation en fonction de leur score **Priorité d’une enquête**. Pour plus d’informations, consultez [Comprendre le score de priorité d’examen](tutorial-ueba.md#risk-score).

- **Améliorations de la stratégie d’activité**  
Vous pouvez désormais créer des alertes de stratégie d’activité basées sur des objets d’activité. Par exemple, cette fonctionnalité vous permet de créer des alertes sur les modifications apportées aux rôles d’administration d’Azure Active Directory. Pour plus d’informations sur les objets d’activité, consultez [Filtres d’activité](activity-filters-queries.md#activity-filters).

## <a name="cloud-app-security-release-155"></a>Cloud App Security version 155

Publication : 4 août 2019

- **Nouveaux modèles de stratégie**  
Cloud App Security intègre maintenant de nouveaux modèles de stratégies d'activité pour de meilleures pratiques de sécurité AWS.

- **Avertissement : Fin de la prise en charge de TLS 1.0 et 1.1 le 8 septembre**  
Microsoft transfère tous ses services en ligne vers Transport Layer Security (TLS) 1.2+ pour fournir le meilleur chiffrement de sa catégorie. Par conséquent, à partir du 8 septembre 2019, Cloud App Security ne prendra plus en charge TLS 1.0/1.1 et les connexions utilisant ces protocoles. Pour plus d'informations sur l’impact de ce changement, lisez [notre billet de blog](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/End-of-support-for-TLS-1-0-and-1-1-in-Microsoft-Cloud-App/ba-p/770507).

- **Logique améliorée pour les activités de connexion interactives (déploiement graduel)**  
Nous déployons progressivement une nouvelle logique pour déterminer si une activité de connexion Azure Active Directory est interactive. La nouvelle logique améliore la capacité de Cloud App Security à signaler uniquement les activités de connexion qui sont lancées par un utilisateur.

## <a name="cloud-app-security-release-154"></a>Cloud App Security version 154

Publication : 21 juillet 2019

- **Intégrer et déployer le contrôle d’application par accès conditionnel pour tous les types d’applications maintenant en GA**  
Depuis que nous vous avons montré un aperçu du contrôle d’application par accès conditionnel pour toutes les applications le mois dernier, nous avons reçu un feedback incroyable et nous sommes donc très contents d’annoncer sa disponibilité générale. Cette nouvelle fonctionnalité vous permet de déployer n’importe quelle application web en vue d’utiliser des stratégies de session et d’accès, et de bénéficier de puissantes fonctionnalités de supervision et de contrôle en temps réel.

- **Évaluation de la configuration de la sécurité pour AWS**  
Cloud App Security met progressivement en place la possibilité d’obtenir une évaluation de la configuration de la sécurité de votre environnement Amazon Web Services à des fins de conformité CIS, et fournit des recommandations s’il manque des configurations et des contrôles de la sécurité. Cette fonctionnalité permet aux organisations de superviser l’état de conformité de tous les comptes AWS connectés à partir d’une seule vue.

- **Détections d’anomalies d’application OAuth**  
Nous avons étendu notre actuelle fonctionnalité de détection d’applications OAuth suspectes. Quatre nouvelles détections sont maintenant prêtes à l’emploi, qui profilent les métadonnées des applications OAuth autorisées dans votre organisation pour identifier celles qui sont potentiellement malveillantes.

## <a name="cloud-app-security-release-153"></a>Cloud App Security mise en production 153

Publication : 7 juillet 2019

- **Support Dropbox amélioré**  
Cloud App Security prend désormais en charge l’action de gouvernance **Corbeille** pour Dropbox : cette action de gouvernance peut être utilisée manuellement ou automatiquement en tant que partie d’une stratégie de fichier.
- **Nouvelles applications proposées pour le contrôle d’application par accès Cloud**  
Le contrôle d’application par accès conditionnel pour les applications proposées suivantes est généralement disponible :

    - OneDrive Entreprise
    - SharePoint Online
    - Azure DevOps
    - Exchange Online
    - Power BI

- **Autoriser les fichiers identifiés comme programme malveillant**  
Cloud App Security analyse les fichiers à partir de vos applications connectées pour rechercher l’exposition DLP et les programmes malveillants. Vous pouvez maintenant autoriser les fichiers identifiés comme programme malveillant mais confirmés sans échec après examen. Autoriser un fichier le supprime du rapport de détection des programmes malveillants et supprime les correspondances futures sur ce fichier. Pour plus d’informations sur la détection de programme malveillant, consultez [Détection d’anomalie Cloud App Security](anomaly-detection-policy.md).

## <a name="cloud-app-security-release-152"></a>Cloud App Security version 152

Publication : 23 juin 2019

- **Déployer le contrôle d’application par accès conditionnel pour tous les types d’applications (préversion)**  
Nous sommes heureux d’annoncer que nous avons étendu notre prise en charge du contrôle d’application par accès conditionnel à l’ensemble des applications web, en plus de la prise en charge que nous proposons déjà pour les [applications à la une](proxy-intro-aad.md). Cette nouvelle fonctionnalité vous permet de déployer n’importe quelle application web en vue d’utiliser des stratégies de session et d’accès, et de bénéficier de puissantes fonctionnalités de supervision et de contrôle en temps réel. Par exemple, vous pouvez protéger les téléchargements avec des étiquettes Azure Information Protection, bloquer le chargement des documents sensibles, effectuer des audits, et bien plus encore.
- **Audit des activités dans le portail**  
Cloud App Security audite toutes les activités d’administration du portail, vous permettant ainsi de superviser et d’analyser les activités de manière approfondie. À présent, vous pouvez également exporter jusqu’à 90 jours d’activités en vue de procéder à une analyse. Par exemple, vous pouvez auditer un administrateur qui analyse les activités d’un utilisateur ou qui affiche certaines alertes. Pour exporter le journal, accédez à la page de paramètres **Gérer l’accès administrateur**.
- **Déconnexion de session personnalisée à partir du portail Cloud App Security**  
Vous pouvez désormais configurer la déconnexion automatique des sessions administrateur du portail après une durée d’inactivité spécifiée.

## <a name="cloud-app-security-release-151"></a>Cloud App Security version 151

Publication : 9 juin 2019

- **UEBA hybride - Intégration native avec Azure ATP (préversion)**  
Cloud App Security s’intègre maintenant en mode natif dans Azure ATP pour fournir une vue unique des activités d’identité dans les applications cloud et votre réseau local. Pour plus d’informations, consultez [Intégration d’Azure Advanced Threat Protection](aatp-integration.md).
- **Améliorations apportées à UEBA**  
Pour vous aider à identifier les menaces qui échappent aux contrôles, Cloud App Security utilise désormais le profilage unique afin de fournir des indices de risque pour les alertes et activités individuelles. Les indices de risque peuvent être utilisés pour identifier des activités qui ne sont pas assez suspectes en elles-mêmes pour déclencher des alertes. Toutefois, en regroupant les indices de risque dans un **indice de priorité d’examen** pour l’utilisateur, Cloud App Security vous permet d’identifier des comportements à risques et de concentrer votre examen. Ces fonctionnalités sont désormais disponibles dans la nouvelle page utilisateur.
- **Nouveau facteur de risque ajouté au catalogue d’applications cloud**  
Le catalogue d’applications cloud inclut désormais le facteur de risque du plan de récupération d’urgence pour vous permettre d’évaluer les applications dans le catalogue d’applications cloud pour la prise en charge de la continuité des activités métier.
- **Connecteur Microsoft Flow GA**  
Après la préversion de la prise en charge de Microsoft Cloud App Security l’an dernier, le connecteur est maintenant généralement disponible.
- **Amélioration de gouvernance automatisées pour les stratégies de fichiers**  
Cloud App Security prend désormais en charge la configuration de l’action de gouvernance **Mettre à la corbeille** pour les stratégies de fichiers. Cette action de gouvernance vous permet de déplacer automatiquement des fichiers vers le dossier Corbeille.
- **Prise en charge améliorée de Google Drive**  
Cloud App Security prend désormais en charge l’action de gouvernance **Mettre à la corbeille** pour les stratégies de fichiers. Cette action de gouvernance vous permet de déplacer automatiquement des fichiers Google Drive vers le dossier Corbeille.
- **Nouvelle autorisation pour les rôles d’administrateur d’application et d’administrateur de groupe**  
Les rôles *Administrateur d’application/d’instance* et *Administrateur de groupe d’utilisateurs* prennent désormais en charge l’accès en lecture seule.
- **Activités de connexion d’authentification héritées (déploiement graduel)**  
Cloud App Security signale maintenant les activités de connexion Azure Active Directory qui utilisent des protocoles hérités comme ActiveSync. Ces activités de connexion peuvent être consultées dans le journal d’activité et peuvent être utilisées lors de la configuration des stratégies.

## <a name="cloud-app-security-release-150"></a>Cloud App Security version 150

Publication : le 26 mai 2019

- **Amélioration de l’exportation des alertes**  
Lorsque vous exportez des alertes au format CSV à partir de la page **Alertes**, les résultats incluront désormais la date de résolution ou de rejet de l'alerte.

## <a name="cloud-app-security-release-148-and-149"></a>Cloud App Security versions 148 et 149

Publication le 12 mai 2019

- **Connecteur d’applications Webex disponible**  
Un nouveau connecteur d’applications est maintenant disponible pour Cisco Webex Teams en préversion publique. Vous pouvez maintenant connecter Microsoft Cloud App Security à Cisco Webex Teams pour surveiller et protéger ses utilisateurs, activités et fichiers. Pour plus d’informations, consultez [Connecter Webex](connect-webex-to-microsoft-cloud-app-security.md)

- **Nouveaux sites du service de classification des données Microsoft**  
Le [service de classification des données Microsoft](dcs-inspection.md) est désormais disponible dans quatre nouveaux pays : Australie, Inde, Canada et Japon. Si votre locataire Office se trouve dans ces pays, vous pouvez maintenant utiliser le service de classification des données Microsoft comme méthode d’inspection du contenu dans les stratégies de fichier Microsoft Cloud App Security.

- **Découverte des clichés instantanés PaaS et IaaS**  
Microsoft Cloud App Security a étendu ses capacités Cloud Discovery et propose désormais également une fonctionnalité Shadow IT pour les ressources hébergées sur des solutions IaaS et PaaS comme Microsoft Azure, Amazon Web Services et Google Cloud Platform. Cloud Discovery fournit désormais une visibilité permettant à des applications personnalisées de s’exécuter par-dessus vos solutions IaaS et PaaS, comptes de stockage créés, et bien plus encore. Utilisez cette nouvelle fonctionnalité pour découvrir les ressources existantes, identifier les personnes qui accèdent à chacune d’elles, et le volume de trafic transmis.

- **Attestation d’application**  
L’évaluation de la conformité et du risque Microsoft Cloud App Security permet maintenant aux fournisseurs de cloud d’attester que leur application est mise à jour dans le catalogue d’applications cloud. Ce programme pilote permet aux fournisseurs de cloud de remplir un questionnaire à attestation automatique selon des attributs de risque du catalogue d’applications cloud pour s’assurer que leur évaluation du risque dans Cloud App Security est à jour. Les utilisateurs peuvent obtenir une indication des attributs de risque qui ont été attestés par le fournisseur (plutôt qu’évalués par l’équipe Cloud App Security) et la date à laquelle chaque attribut a été soumis par le fournisseur. Pour plus d’informations, consultez [Attester votre application](attest-your-app.md).

- **Granularité de la charge de travail Office 365**  
Lorsque vous connectez Office 365 à Microsoft Cloud App Security, vous pouvez maintenant choisir les charges de travail à connecter. Par exemple, les clients uniquement intéressés par la connexion d’Office 365 pour la surveillance de l’activité peuvent désormais le faire pendant le processus de connexion ou en modifiant un connecteur Office 365 existant. Dans le cadre de ce changement, OneDrive et SharePoint Online ne seront plus affichés en tant que connecteurs séparés mais seront inclus dans le connecteur Office 365 en tant que charge de travail des fichiers _Office 365_. Les clients disposant d’un connecteur Office 365 existant ne sont pas affectés par cette modification.

- **Prise en charge améliorée de Teams**  
Vous pouvez désormais surveiller et bloquer l’envoi de message dans l’application web Teams en temps réel, en configurant une stratégie de session basée sur du contenu sensible.

## <a name="cloud-app-security-release-147"></a>Cloud App Security version 147

Publication : 14 avril 2019

- **Nouvel analyseur de journal Cloud Discovery**  
Cloud App Security Cloud Discovery inclut désormais un analyseur de journal intégré pour prendre en charge le format de journal Palo Alto LEEF.

- **Mises à jour des stratégies de session**  
  - **Méthode d’inspection du contenu supplémentaire pour les stratégies de session** :  Lorsque vous définissez une stratégie de session, vous avez désormais la possibilité de choisir le Service de classification des données en tant que méthode d’inspection du contenu pour les fichiers. Le Service de classification des données offre à l’utilisateur un large éventail de types sensibles intégrés à utiliser pour identifier les informations sensibles.
  - **Contrôle amélioré des autorisations de fichier dans les stratégies de session** :  Lorsque vous créez une stratégie de session pour contrôler les téléchargements à l’aide de Cloud App Security, vous pouvez maintenant appliquer automatiquement les autorisations par utilisateur, comme la lecture seule, aux documents lors de leur téléchargement à partir de vos applications cloud. Cela fournit un niveau supérieur de flexibilité et la possibilité de protéger les informations au-delà de vos étiquettes d’entreprise préconfigurées.
  - **Contrôle du téléchargement de fichiers volumineux** :  Lorsque l’inspection du contenu est activée dans les stratégies de session, vous pouvez désormais contrôler ce qui se passe quand un utilisateur tente de télécharger un fichier très volumineux. Si le fichier est trop volumineux pour une analyse lors du téléchargement, vous pouvez choisir s’il sera bloqué ou autorisé.

## <a name="cloud-app-security-release-146"></a>Cloud App Security version 146

Date de publication : 31 mars 2019

- **Amélioration du voyage impossible**  
La détection d’un voyage impossible a été améliorée avec une prise en charge dédiée pour les pays voisins.
- **Prise en charge d’attributs supplémentaires pour l’analyseur CEF générique**  
La prise en charge de l’analyseur du journal Cloud Discovery pour le format CEF générique a été améliorée pour prendre en charge des attributs supplémentaires.
- **Accès étendu aux rapports Cloud Discovery**  
En plus du rôle Discovery Admin, vous pouvez maintenant étendre l’accès à des rapports Discovery spécifiques. Cette amélioration vous permet de configurer des privilèges d’accès aux données de sites et divisions spécifiques.
- **Nouvelle prise en charge de rôle : lecteur général**  
Microsoft Cloud App Security prend désormais en charge le rôle de lecteur général Azure AD. Le lecteur général dispose d’un accès complet en lecture seule à tous les aspects de Microsoft Cloud App Security, mais il ne peut ni modifier des paramètres ni prendre aucune mesure.

## <a name="cloud-app-security-release-145"></a>Cloud App Security version 145

Date de publication : 17 mars 2019

- **L’intégration de Microsoft Defender ATP est en disponibilité générale**  
L’année dernière, nous avons annoncé l’[intégration avec Windows Defender Advanced Threat Protection](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Cloud-App-Security-and-Windows-Defender-ATP-better/ba-p/263265), qui améliore la découverte du Shadow IT dans votre organisation et l’étend au-delà du réseau d’entreprise. Nous sommes heureux de vous annoncer que cette intégration unique, [Activée par simple clic](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RWtNmG), est désormais disponible en général.
- **Prise en charge de Dynamics 365 CRM**  
Cloud App Security a ajouté des fonctionnalités de supervision et de contrôle en temps réel pour Dynamics 365 CRM, afin de vous permettre de protéger vos applications métier et le contenu sensible stocké dans ces applications. Pour plus d'informations sur les possibilités offertes par Dynamics 365 CRM, lisez [cet article](proxy-intro-aad.md#how-it-works).

## <a name="cloud-app-security-release-144"></a>Cloud App Security version 144

Date de publication : 3 mars 2019

- **Investigation unifiée de SecOps pour les environnements hybrides**  
Étant donné que de nombreuses organisations ont des environnements hybrides, les attaques démarrent dans le cloud avant de basculer en local, ce qui signifie que les équipes SecOps doivent investiguer ces attaques depuis différents endroits. Grâce à la combinaison des signaux de sources cloud et locales, notamment Microsoft Cloud App Security, Azure ATP et Azure AD Identity Protection, Microsoft autonomise les analystes de sécurité en fournissant des informations sur l’identité unifiée et l’utilisateur dans une console unique pour mettre fin au basculement entre les solutions de sécurité. Vos équipes SecOP ont ainsi plus de temps et les bonnes informations pour prendre de meilleures décisions et remédier activement aux menaces et aux risques réels liés à l’identité. Pour plus d’informations, consultez [Investigation unifiée de SecOps pour les environnements hybrides](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Unified-SecOps-Investigation-for-Hybrid-Environments/ba-p/360850)

- **Fonctionnalités de sandboxing pour la détection de programmes malveillants** (déploiement progressif)  
Les fonctionnalités de détection de programmes malveillants de Cloud App Security sont en cours de développement afin d’inclure la possibilité d’identifier les logiciels malveillants zero-day par le biais d’une technologie de sandboxing avancée.  
Dans le cadre de cette fonctionnalité, Cloud App Security identifie automatiquement les fichiers suspects et les fait exploser pour rechercher un comportement suspect des fichiers et indique que le fichier a des intentions malveillantes (programme malveillant).
Dans le cadre de cette modification, les stratégies de détection de programmes malveillants incluent désormais un champ de type Détection qui vous permet de filtrer par renseignement sur les menaces ainsi que par sandboxing.

- **Mises à jour de l’accès conditionnel**  
Avec le contrôle d’application par accès conditionnel, vous avez maintenant la possibilité de superviser et de bloquer les activités suivantes :
  - Chargez des fichiers dans n’importe quelle application : activez des scénarios tels qu’empêcher le chargement d’extensions de programmes malveillants connus et garantir que les utilisateurs protègent les fichiers avec AIP avant le chargement.
  - Copiez et collez dans n’importe quelle application : renforcez les contrôles robustes de l’exfiltration des données, qui incluaient déjà le téléchargement, l’impression et les activités personnalisées telles que le partage.
  - Envoyez un message : assurez-vous que les données des informations d'identification personnelle telles que les mots de passe ne sont pas partagées dans des outils de collaboration populaires comme Slack, Salesforce et Workplace by Facebook.
  - Les stratégies des sessions incluent maintenant des modèles intégrés. Ils permettent à votre organisation d’activer sans effort une surveillance et un contrôle en temps réel populaires, tels que **Bloquer le chargement sur la base de l’inspection du contenu en temps réel**.

## <a name="cloud-app-security-release-143"></a>Cloud App Security version 143

Date de publication : 17 février 2019

- **Déploiement d’étendue pour les instances d’application**  
Le déploiement d’étendue peut désormais être configuré au niveau de l’instance de l’application, ce qui permet une plus grande granularité et un meilleur contrôle.
- **Améliorations des rôles**  
  - Les rôles Office 365 d’administration des données et d’opérateur de sécurité sont désormais pris en charge dans Cloud App Security. Le rôle d’administrateur de données permet aux utilisateurs de gérer tous les fichiers associés, ainsi que d’afficher les rapports Cloud Discovery. Les opérateurs de sécurité sont autorisés à gérer les alertes et à afficher la configuration de la stratégie.
  - Le rôle de lecteur de sécurité a maintenant la possibilité de configurer l’agent SIEM, ce qui permet une meilleure étendue d’autorisation.

- **Support Microsoft Flow**  
Cloud App Security analyse désormais les activités des utilisateurs dans Microsoft Flow. Les activités prises en charge sont les activités signalées par Flow dans le journal d’audit Office 365.

- **Regroupement d’entités d’alerte**  
La page **Alerte** regroupe désormais des entités associées qui ont été impliquées dans une alerte pour vous aider dans votre investigation.

## <a name="cloud-app-security-release-142"></a>Cloud App Security version 142

Date de publication : 3 février 2019

- **Configuration de la stratégie de session dans Azure AD**  
Vous pouvez désormais configurer des stratégies de session pour surveiller les utilisateurs ou bloquer les téléchargements en temps réel, directement dans l’accès conditionnel Azure AD. Vous pouvez toujours configurer des stratégies de session avancées directement dans Cloud App Security. Pour parcourir ce déploiement, consultez [Déployer un contrôle d’application par accès conditionnel pour les applications Azure AD](proxy-deployment-aad.md).

- **Requêtes suggérées et enregistrées pour les applications OAuth**  
Les requêtes suggérées ont été ajoutées à la page d’applications OAuth, qui fournissent des modèles d’investigation prêts à l’emploi pour filtrer vos applications OAuth. Les requêtes suggérées incluent des filtres personnalisés pour identifier les applications à risque, telles que les applications autorisées par les administrateurs. Les requêtes enregistrées vous permettent d’enregistrer des requêtes personnalisées pour une utilisation future, comme les requêtes enregistrées disponibles aujourd’hui dans le journal d’activité et les pages de découverte.

- **Configuration par défaut de l’audit Office 365**  
Si vous souhaitez activer la surveillance des activités d’Office 365 dans Cloud App Security, vous devez maintenant activer l’audit dans le [Centre de sécurité et de conformité Office](/office365/securitycompliance/turn-audit-log-search-on-or-off#turn-on-audit-log-search), ce qui résulte d’une [modification de d’audit Office 365](/office/office-365-management-api/office-365-management-activity-api-faq#what-happens-if-i-disable-auditing-for-my-office-365-organization-will-i-still-get-events-via-the-management-activity-api). Cette modification n’est nécessaire que si vous n’avez pas encore activé la surveillance des activités d’Office 365 dans Cloud App Security.

- **Prise en charge améliorée de Box**  
Cloud App Security prend désormais en charge deux nouvelles actions de gouvernance pour Box :

  - **Faire expirer le lien partagé** : cette action de gouvernance vous permet de définir une date d’expiration après laquelle un lien partagé ne sera plus actif.

  - **Modifier le niveau d’accès au lien de partage** : cette action de gouvernance vous permet de modifier le niveau d’accès au lien de partage uniquement dans la société, uniquement entre les collaborateurs et au niveau public.

- **Support de plusieurs emplacements dans OneDrive**  
Cloud App Security offre désormais une visibilité complète des fichiers OneDrive, même s’ils sont répartis sur plusieurs emplacements géographiques. La protection est désormais disponible pour les fichiers situés aux emplacements supplémentaires ainsi qu’à l’emplacement principal.

- **Amélioration de la navigation dans le portail**  
Le portail Cloud App Security a été amélioré pour offrir une meilleure navigation et mieux aligner Cloud App Security avec les autres services de sécurité de Microsoft, l’objectif étant de simplifier et de rationaliser son utilisation.

## <a name="cloud-app-security-release-141"></a>Cloud App Security version 141

Publiée le 20 janvier 2019

- **Améliorations de l’évaluation des risques dans le cloud**  
  - L’évaluation des risques du logiciel cloud a été améliorée avec deux nouvelles expériences.
    - Un nouvel attribut **Type de données** évalue le type de contenu que les utilisateurs peuvent charger vers l’application. Vous pouvez utiliser cet attribut pour évaluer une application en fonction de la sensibilité de chaque type de données dans votre organisation.
    - Pour obtenir une vue d’ensemble plus complète des risques d’une application, vous pouvez désormais facilement passer de l’évaluation des risques de l’application à l’évaluation des risques de la société d’hébergement en cliquant sur l’attribut **Société d’hébergement**.

- **Contexte de fichier amélioré pour l’investigation d’alerte de détection d’anomalie**  
  - L’investigation de détection d’anomalies a été améliorée pour vous permettre d’obtenir des insights supplémentaires associée aux fichiers impliqués dans une alerte. Lorsque des alertes sont déclenchées en cas d’activité inhabituelle liée à des fichiers (téléchargement, partage, suppression), ce zoom avant est disponible. Par exemple, si la plupart des fichiers affectés proviennent du même dossier ou partagent la même extension de fichier, vous verrez ces insights dans la section Risque supplémentaire de l’alerte.

- **Requêtes pour l’investigation des fichiers**  
  - La capacité de création et d’enregistrement de requêtes personnalisées de Cloud App Security a été étendue à la page **Fichiers**. Les requêtes de la page **Fichiers** vous permettent de créer des modèles de requêtes pouvant être réutilisés pour une investigation approfondie.

## <a name="cloud-app-security-release-139-140"></a>Cloud App Security versions 139, 140

Mise en production du 6 janvier 2019

- **Modification de la détection de fichiers**  
Les fichiers partagés avec tout le monde dans SharePoint et One Drive sont désormais considérés comme **internes** [en raison des modifications apportées à SharePoint et à One Drive](https://support.microsoft.com/help/4089534/how-to-grant-the-everyone-claim-to-external-users-in-office-365). Ainsi, si un fichier partagé avec tout le monde est détecté, il sera désormais traité comme un fichier interne, ce qui a un impact sur la façon dont le fichier est traité par les stratégies et affiché dans la page de fichiers.

- **Modification de la surveillance des fichiers**  
Le comportement de supervision de fichier par défaut a changé pour les clients nouveaux et inactifs. Vous devez maintenant activer la supervision des fichiers pour activer la fonctionnalité, par le biais de **Paramètres** > **Fichiers**. Les clients actifs existants ne seront pas affectés par cette modification.

- **Réglage avancé des stratégies de détection d'anomalie**  
Vous pouvez désormais agir sur le moteur de détection d'anomalie pour supprimer ou exposer des alertes en fonction de vos préférences.
  - Dans la stratégie de voyage impossible, vous pouvez définir le curseur de sensibilité afin de déterminer le niveau de comportement anormal nécessaire pour déclencher une alerte.
  - Vous pouvez également configurer si les alertes d’activité dans un pays peu fréquent, les adresses IP anonymes, les adresses IP suspectes et le voyage impossible doivent analyser les connexions ayant échoué et celles ayant réussi, ou uniquement les connexions ayant réussi.

- **Prise en charge de plusieurs chaînes d’approbation**  
Le contrôle d’application par accès conditionnel prend désormais en charge l’ajout et l’utilisation de plusieurs certificats intermédiaires ou racines de confiance en tant que méthode de gestion des appareils.

- **Nouveau rôle Cloud Discovery** (déploiement progressif)  
Cloud App Security fournit désormais un nouveau rôle administrateur pour les utilisateurs de Cloud Discovery. Ce rôle peut être utilisé pour limiter l’accès d’un utilisateur administrateur aux seuls paramètres et données Cloud Discovery dans le portail Cloud App Security.

- **Prise en charge des étiquettes unifiées Microsoft Information Protection** (déploiement progressif)  
Cloud App Security prend désormais en charge les étiquettes unifiées Microsoft Information Protection. Pour les clients qui ont déjà [migré leurs étiquettes de classification pour leur Centre de conformité et de sécurité Office 365](/azure/information-protection/configure-policy-migrate-labels), Cloud App Security identifie et utilise ces étiquettes, comme décrit dans [Intégration avec Azure Information Protection](azip-integration.md).

**Prise en charge de l’étiquetage de fichier PDF** (déploiement progressif)  
Pour les clients qui utilisent des étiquettes unifiées, Cloud App Security prend désormais en charge l’étiquetage automatique des fichiers PDF.

## <a name="cloud-app-security-release-138"></a>Cloud App Security version 138

Mise en production du 9 décembre 2018

- **Chargement automatique de journaux à l’aide de Docker sur Windows**  
Cloud App Security prend désormais en charge le chargement automatique de journaux pour Windows 10 (Fall Creators Update) et Windows Server (versions 1709 et ultérieures) à l’aide d’un Docker pour Windows. Pour obtenir plus d’informations et des instructions sur la configuration de cette fonctionnalité, consultez [Docker sur Windows en local](discovery-docker-windows.md).

- Cloud App Security est intégré dans [Microsoft Flow](/flow/getting-started) pour fournir une automatisation des alertes et des playbooks d’orchestration personnalisés. Pour plus d’informations et d’instructions d’intégration, consultez [Intégration dans Microsoft Flow](flow-integration.md).

## <a name="cloud-app-security-release-137"></a>Cloud App Security version 137

Publication : 25 novembre 2018

- **Ajout de la prise en charge de Dynamics**  
Cloud App Security prend maintenant en charge les activités Microsoft Dynamics qui sont prises en charge dans le journal d’audit d’Office 365.

- **Analyse du contenu chiffré (préversion)**  
Cloud App Security vous permet dorénavant d’analyser le contenu protégé par les étiquettes de protection Azure Information Protection. Ceci vous permettra de trouver du contenu sensible, y compris dans des fichiers déjà chiffrés par Azure Information Protection.

- **Attention, nouvelle terminologie !**  
Pour plus de clarté, le nom des capacités de permission d’application a été modifié. Elles s’appellent maintenant **Applications OAuth**.

## <a name="cloud-app-security-release-136"></a>Cloud App Security version 136

Publication : 11 novembre 2018

- **Mises à jour de Cloud Discovery**  
L’analyseur de journal personnalisé a été amélioré pour prendre en charge des formats de journaux d’activité de trafic web plus complexes. Dans le cadre de ces améliorations, les utilisateurs peuvent désormais entrer des en-têtes personnalisés pour les fichiers journaux CSV sans en-tête, utiliser des séparateurs spéciaux pour les fichiers clé-valeur et traiter le format de fichier Syslog, entre autres.

- **Nouvelles stratégies de détection des anomalies**  
Règles de manipulation de boîtes de réception suspectes : Cette stratégie profile votre environnement et déclenche des alertes lorsque des règles suspectes qui suppriment ou déplacent des messages ou des dossiers sont définies pour la boîte de réception d’un utilisateur. Cela peut indiquer que le compte de l’utilisateur est compromis, que des messages sont intentionnellement masqués et que la boîte aux lettres est utilisée pour distribuer du courrier indésirable ou des logiciels malveillants dans votre organisation.

- **Prise en charge de groupes dans les stratégie de permission d’application**  
Cloud App Security vous donne maintenant la possibilité de définir des stratégies de permission d’application de façon plus granulaire, en fonction de l’appartenance à des groupes des utilisateurs qui ont autorisé les applications. Par exemple, un administrateur ne peut décider de définir une stratégie de révocation des applications rares demandant des autorisations élevées que si l’utilisateur qui a donné les autorisations est membre du groupe administrateurs.

- **Le contrôle d’application par accès conditionnel s’intègre désormais à vos applications locales via le proxy d'application Azure Active Directory**  
  - Le [proxy d’application Azure AD](/azure/active-directory/manage-apps/application-proxy) fournit des services d’authentification unique et l’accès à distance sécurisé pour les applications web hébergées localement.
  - Ces applications web locales peuvent désormais être acheminées vers Microsoft Cloud App Security via l’accès conditionnel Azure AD pour fournir une analyse et des contrôles en temps réel par le biais de stratégies d’[accès](access-policy-aad.md) et de [session](session-policy-aad.md).

## <a name="cloud-app-security-release-133-134-135"></a>Cloud App Security versions 133, 134, 135

Publication : octobre 2018

- **Nouvelles stratégies de détection d’anomalies mises en place progressivement**  
  - La nouvelle exfiltration de données vers une stratégie d’applications non approuvées est activée automatiquement pour vous avertir lorsqu'un utilisateur ou une adresse IP utilise une application qui n'est pas approuvée dans le but d’effectuer une activité qui ressemble à une tentative d'exfiltrer des informations de votre organisation.
    - La nouvelle stratégie Plusieurs activités de suppression de machine virtuelle profile votre environnement et déclenche des alertes lorsque des utilisateurs suppriment plusieurs machines virtuelles lors d’une même session, en fonction de la ligne de base de votre organisation.

- **Service de classification des données disponible pour APAC**  
  - L’inspection du contenu du service de classification des données est désormais disponible pour les clients APAC. Pour voir une liste complète de la prise en charge régionale, consultez [Intégration des services de classification des données Microsoft](dcs-inspection.md).

- **Cloud Discovery prend en charge i-Filter**  
  - La fonctionnalité Cloud Discovery de Cloud App Security offre désormais une prise en charge améliorée de l’analyseur syslog i-Filter.

## <a name="cloud-app-security-release-132"></a>Cloud App Security version 132

Publication : 25 septembre 2018

- **Le contrôle d’application par accès conditionnel pour Office 365 est désormais en version préliminaire publique**  
  - Le contrôle d’application par accès conditionnel prend désormais également en charge Office 365 et toute application configurée avec Open ID Connect.
  - Fournir des commentaires à partir d’une session : Ce nouvel outil vous permet de fournir des commentaires sur les performances d’une application sous contrôle d’une session à l’équipe Cloud App Security directement à partir de la session.

- **Intégration native avec Microsoft Defender ATP pour Shadow IT Discovery au-delà de votre société**  
  - Microsoft Cloud App Security s’intègre désormais en mode natif dans Windows Defender Advanced Threat Protection (ATP) pour fournir des fonctionnalités de détection Shadow IT sans déploiement lors de l’utilisation du réseau d’entreprise en mode activé et désactivé par les applications Cloud.  Cela vous permet d’exécuter Cloud Discovery même sur des ordinateurs extérieurs à votre réseau d’entreprise. Ceci permet également une investigation basée sur l’ordinateur : après avoir identifié un utilisateur à risque, vous pouvez vérifier tous les ordinateurs auxquels il a accédé pour détecter les risques potentiels. Si vous identifiez un ordinateur à risque, vous pouvez vérifier tous les utilisateurs qui l’ont utilisé pour examiner les risques potentiels. Pour plus d’informations, consultez l’intégration de Windows Defender Advanced Threat Protection dans [Microsoft Cloud App Security](wdatp-integration.md).

- **Inspection du contenu des fichiers chiffrés**  
  - Cloud App Security prend désormais en charge l’inspection du contenu des fichiers protégés chiffrés qui ont été protégés à l’aide d’Azure Information Protection. Vous pouvez maintenant examiner ces fichiers chiffrés à des fins de reclassification et identifier d’autres violations de stratégies d’exposition et de sécurité DLP.

## <a name="cloud-app-security-release-131"></a>Cloud App Security version 131

Publication : 2 septembre 2018

- **Révoquer automatiquement les autorisations sur les applications OAuth à risque**  
Vous pouvez désormais contrôler les applications OAuth auxquelles vos utilisateurs ont accès en révoquant l’autorisation App pour les applications OAuth sur Office, Google ou Salesforce. Maintenant, lorsque vous créez une **stratégie de permission d'application**, vous pouvez définir la stratégie de révocation d’une permission d'application.

- **Analyseur intégré supplémentaire Cloud Discovery pris en charge**  
Cloud Discovery prend désormais en charge le format de journal Forcepoint Web Security Cloud.

## <a name="cloud-app-security-release-130"></a>Cloud App Security version 130

Publication : 22 août 2018

- **Nouvelle barre de menus**  
Pour fournir une expérience d’administration plus cohérente entre les produits Microsoft 365 et vous permettre de passer plus facilement d’une solution de sécurité Microsoft à une autre, la barre de menus du portail Cloud App Security se trouve maintenant sur le côté gauche de l’écran. Cette expérience de navigation cohérente vous aide à vous orienter lorsque vous passez d’un portail de sécurité Microsoft à un autre.

- **Impact sur le score de l’application OAuth**  
Vous pouvez désormais envoyer les commentaires de l’équipe Cloud App Security pour nous indiquer si une application OAuth détectée dans votre organisation semble malveillante. Cette nouvelle fonctionnalité vous permet de faire partie de notre communauté de sécurité ainsi que de contribuer à améliorer l’analyse et le score de risque des applications OAuth. Pour plus d’informations, consultez [Gérer les applications OAuth](manage-app-permissions.md).

- **Nouveaux analyseurs Cloud Discovery**  
Les analyseurs Cloud Discovery prennent désormais en charge iboss Secure Cloud Gateway et Sophos XG.

## <a name="cloud-app-security-release-129"></a>Cloud App Security version 129

Publication : 5 août 2018

- **Nouvelles stratégies de détection d’anomalies : règles relatives aux e-mails suspects**  
De nouvelles stratégies de détection des anomalies ont été ajoutées pour détecter les règles de transfert des e-mails suspects, par exemple, si un utilisateur a créé une règle de boîte de réception assurant le transfert d’une copie de tous les e-mails à une adresse externe.

- Cette version comprend des correctifs et des améliorations visant plusieurs problèmes.

## <a name="cloud-app-security-release-128"></a>Cloud App Security version 128

Publication : 22 juillet 2018

- **Actions des applications OAuth sur plusieurs applications**  
Pour les applications OAuth qui ont reçu des permissions d’applications, vous pouvez désormais interdire ou approuver plusieurs applications en une seule action. Par exemple, vous pouvez passer en revue toutes les applications qui ont reçu l’autorisation d’utilisateurs de votre organisation, sélectionner toutes les applications que vous souhaitez interdire, puis cliquer sur Exclure les applications pour révoquer tous les consentements accordés. Les utilisateurs ne seront alors plus autorisés à accorder des permissions à ces applications.  Pour plus d’informations, consultez [Gérer les applications OAuth](manage-app-permissions.md).

- **Prise en charge améliorée des applications Azure**  
Pour Azure, nous mettons maintenant progressivement en place la possibilité de détecter des applications en tant qu’activités comptes utilisateurs effectuées par les applications Azure (internes et externes). Ceci vous permet de créer des stratégies qui vous alerteront si une application a des activités inattendues et non autorisées. Pour plus d’informations, consultez [Connecter Azure à Microsoft Cloud App Security](connect-azure-to-microsoft-cloud-app-security.md).

- **Moteur de classification des données mis à jour avec de nouveaux types sensibles au RGPD**  
Le [service de classification de données Cloud App Security](dcs-inspection.md) ajouté de nouveaux types sensibles au RGPD à notre moteur de classification des données pour vous permettre de détecter le contenu lié au RGPD dans vos fichiers.

- **Mises à jour du catalogue d’applications cloud**  
Le catalogue d’applications cloud inclut désormais une catégorie de risque juridique (en plus des catégories Général, Sécurité et Conformité) pour vous aider à gérer la confidentialité et la conformité de propriété des données, notamment la préparation du RGPD.
Pour vous aider à évaluer la préparation de chaque application cloud pour le RGPD, la nouvelle catégorie de risque contient l’instruction de préparation pour le RGPD du service cloud et l’état de chaque contrôle de framework du RGPD.
Notez que dans le cadre de cette amélioration, les attributs de risque suivants ont été déplacés d’une autre catégorie de risque à la catégorie juridique :
  - DMCA
  - Propriété des données
  - Stratégie de conservation des données

  De plus, la nouvelle catégorie de risque est notée séparément, ce qui vous permet de configurer le score pondéré en fonction de vos préférences et de vos priorités. Pour plus d'informations, consultez [Score de risque](risk-score.md).

- **Nouvelle requête suggérée : prête pour le RGPD**  
Une nouvelle requête est suggérée pour vous permettre d’identifier les applications découvertes qui sont prêtes pour le RGPD. Étant donné que le RGPD est récemment devenu une priorité absolue pour les administrateurs de sécurité, cette requête vous aide à identifier facilement les applications conformes au RGPD et à atténuer les menaces en évaluant le risque de celles qui ne le sont pas.

## <a name="cloud-app-security-release-127"></a>Cloud App Security version 127

Publication : 8 juillet 2018

- Vous pouvez désormais voir les activités génériques pour Office 365. Dans le **Journal d’activité** et dans les **Stratégies d’activité**, vous pouvez maintenant filtrer les activités Office 365 ayant pour état **Non spécifié**. L’examen de ces activités vous permet d’examiner des informations sur les activités qui ne sont pas encore classifiées par type dans Cloud App Security, et vous pouvez vous baser sur ces activités pour envoyer des demandes à l’équipe Cloud App Security afin de créer des types d’activités.

## <a name="cloud-app-security-release-126"></a>Cloud App Security version 126

Publication : 24 juin 2018

- **Contrôle d’application par accès conditionnel (en disponibilité générale)**  
Le contrôle d’application par accès conditionnel de Microsoft Cloud App Security (proxy inverse) est maintenant en disponibilité générale pour toutes les applications SAML. Le contrôle d’application par accès conditionnel s’intègre directement à vos stratégies d’accès conditionnel Azure AD pour **surveiller et contrôler les sessions de vos utilisateurs en temps réel** tout en leur permettant d’être productifs. Depuis le premier aperçu de la fonctionnalité, de nombreuses fonctionnalités et améliorations ont été mises en place, notamment les suivantes :
  - La possibilité de créer une [stratégie d’accès](access-policy-aad.md) pour gérer l’accès aux mêmes applications à partir de clients natifs en plus de la création d’une stratégie de session pour le trafic du navigateur.
  - Le processus d’intégration d’applications a été rationalisé pour prendre en charge des applications SAML personnalisées dans votre organisation.
  - Dans le cadre du réseau mondial Azure, l’intégration et l’interface ont été améliorées pour offrir une expérience transparente aux utilisateurs, où qu’ils soient dans le monde.

- **Inspection du contenu avec le service de classification des données Microsoft (en disponibilité générale)**  
L’intégration de Microsoft Cloud App Security avec les services de classification des données Microsoft est maintenant en disponibilité générale. Cette intégration vous permet d’utiliser le service de classification des données Microsoft en mode natif pour classer les fichiers dans vos applications cloud. Pour plus d’informations, consultez [Intégration des services de classification des données Microsoft](dcs-inspection.md). Actuellement, cette fonctionnalité est disponible uniquement aux États-Unis et en Europe (à l’exception de la France).

- **Rapport exécutif Cloud Discovery**  
Microsoft Cloud App Security met progressivement en place la possibilité de générer un rapport exécutif Cloud Discovery au format PDF. Ce rapport fournit une vue d’ensemble de l’utilisation du Shadow IT qui a été identifié dans votre organisation et met en évidence les applications et utilisateurs les plus utilisés globalement et dans les principales catégories. Il se concentre sur le risque que le Shadow IT représentent dans votre organisation. Le rapport fournit également une liste de recommandations pour améliorer la visibilité et le contrôle du Shadow IT dans votre organisation. Utilisez ce rapport pour garantir que des risques et menaces potentiels sont supprimés et que votre utilisation reste sûre et sécurisée.

- **Détection de logiciel malveillant**  
La capacité de détection de programmes malveillants est progressivement mise en place. Elle permet de **détecter automatiquement les fichiers malveillants dans votre stockage cloud**, quel que soit le type de fichier. Microsoft Cloud App Security utilise le renseignement sur les menaces de Microsoft pour déterminer si certains fichiers sont associés à des attaques de programmes malveillants connus ou potentiellement malveillants. Pour plus d’informations, consultez [Stratégies de détection d'anomalies](anomaly-detection-policy.md).

- **Correction automatisée d’activités suspectes**  
Vous pouvez désormais définir des actions de correction automatique pour une session suspecte, qui sont déclenchées par les stratégies de détection d’anomalie. Cette amélioration vous permet d’être alerté instantanément en cas de violation et d’**appliquer automatiquement des actions de gouvernance**, telles que suspendre l’utilisateur. Pour plus d’informations, consultez [Stratégies de détection d'anomalies](anomaly-detection-policy.md#adp-automated-gov).

- **Évaluation de la configuration de la sécurité pour Azure**  
Microsoft Cloud App Security met progressivement en place la possibilité d’obtenir une évaluation de la configuration de la sécurité de votre environnement Azure et fait des recommandations relatives à l’absence de configuration et au contrôle de la sécurité. Par exemple, il vous indique s’il manque l’authentification MFA pour les utilisateurs administratifs. Pour plus d’informations, consultez [Intégration de la gestion de la posture de sécurité cloud](security-config.md).

- **Détection automatisée d’applications OAuth à risque**  
En plus de l’investigation existante des applications OAuth connectées à votre environnement, Microsoft Cloud App Security met désormais progressivement en place la possibilité de définir des notifications automatisées pour vous informer quand une application OAuth répond à certains critères. Par exemple, vous pouvez être alerté automatiquement quand des applications nécessitent un niveau d’autorisation élevé et ont été autorisées par plus de 50 utilisateurs. Pour plus d’informations, consultez [Stratégies de permission d'applications](app-permission-policy.md).

- **Prise en charge de la gestion du fournisseur de services de sécurité gérée (MSSP)**  
Microsoft Cloud App Security offre désormais une meilleure expérience de gestion pour les MSSP. Les utilisateurs externes peuvent maintenant être configurés en tant qu’administrateurs et affectés à l’un des [rôles actuellement disponibles dans Microsoft Cloud App Security](manage-admins.md). De plus, pour permettre aux MSSP de fournir des services à plusieurs locataires clients, les administrateurs disposant de droits d’accès à plusieurs locataires peuvent désormais facilement changer de locataires dans le portail. Pour plus d’informations sur la gestion des administrateurs, consultez [Gérer les administrateurs](manage-admins.md).

- **Intégration dans DLP externe (en disponibilité générale)**  
Microsoft Cloud App Security vous permet de [tirer parti des investissements existants dans les systèmes de classification tiers](icap-stunnel.md), comme les solutions DLP (Data Loss Prevention), et vous permet d’analyser le contenu d’applications cloud à l’aide de déploiements existants en cours d’exécution dans votre environnement. Pour plus d'informations, consultez [Intégration dans DLP externe](icap-stunnel.md).

## <a name="cloud-app-security-release-125"></a>Cloud App Security version 125

Publication : 10 juin 2018

- **Nouvelle fonctionnalité d’investigation pour les principaux utilisateurs :**  
Microsoft Cloud App Security a ajouté un nouveau widget d’investigation au tableau de bord qui affiche les principaux utilisateurs par nombre d’alertes de détection de menaces en attente. Ce widget d’investigation vous permet de concentrer vos investigations relatives aux menaces sur les utilisateurs ayant le plus grand nombre de sessions suspectes.

- **Prise en charge des compartiments AWS S3 :**  
Microsoft Cloud App Security peut désormais détecter les compartiments AWS S3 et leurs niveaux de partage. Cela fournit des alertes et une visibilité des compartiments AWS accessibles publiquement. Cela vous permet également de créer des stratégies basées sur des compartiments et d’appliquer la gouvernance automatique. Par ailleurs, un nouveau modèle de stratégie appelé **Compartiments S3 accessibles publiquement (AWS)** est disponible. Vous pouvez l’utiliser pour créer facilement une stratégie de gouvernance pour votre stockage AWS. Pour activer ces nouvelles fonctionnalités, veillez à mettre à jour vos applications connectées à AWS en ajoutant les nouvelles autorisations décrites dans [Connexion à AWS](connect-aws-to-microsoft-cloud-app-security.md).

- **Privilèges d’administrateur basés sur des groupes d’utilisateurs** :  
Vous pouvez maintenant définir des autorisations d’administration pour les administrateurs Microsoft Cloud App Security par groupe d’utilisateurs. Par exemple, vous pouvez définir un utilisateur spécifique comme administrateur pour les seuls utilisateurs en Allemagne. L’utilisateur peut ainsi afficher et modifier des informations dans Microsoft Cloud App Security uniquement pour le groupe d’utilisateurs « Allemagne – Tous les utilisateurs ». Pour plus d’informations, consultez [Gestion de l’accès administrateur](manage-admins.md).

## <a name="cloud-app-security-release-124"></a>Cloud App Security version 124

Publication : 27 mai 2018

- **Évaluation des risques du RGPD ajoutée au catalogue d’applications cloud**  
13 nouveaux facteurs de risque ont été ajoutés à Microsoft Cloud App Security. Ces facteurs de risque correspondent aux points de la liste de l’infrastructure du RGPD, pour vous permettre d’évaluer les applications dans le catalogue d’applications cloud conformément aux réglementations du RGPD.

- **Intégration dans le service de classification des données Microsoft**  
Microsoft Cloud App Security vous permet maintenant d’utiliser le service de classification des données Microsoft en mode natif pour classer les fichiers dans vos applications cloud.   
Le service de classification des données Microsoft offre une expérience unifiée de protection des informations sur Office 365, Azure Information Protection et Microsoft Cloud App Security. Il vous permet d’étendre la même infrastructure de classification des données aux applications cloud tierces protégées par Microsoft Cloud App Security, en tirant parti des décisions que vous avez déjà prises dans un nombre encore plus élevé d’applications.

- **Connexion à Microsoft Azure** (déploiement progressif)  
Microsoft Cloud App Security étend ses fonctionnalités de surveillance IaaS au-delà d’Amazon Web Services et prend désormais en charge Microsoft Azure. Cela vous permet de vous connecter rapidement et de surveiller tous vos abonnements Azure avec Cloud App Security. Cette connexion vous offre un ensemble puissant d’outils pour protéger votre environnement Azure, notamment :

  - Visibilité de toutes les activités effectuées via le portail

  - Possibilité de créer des stratégies personnalisées pour émettre des alertes en cas de comportement indésirable, ainsi possibilité de protéger automatiquement les utilisateurs à risque potentiels en les interrompant ou en les forçant à se reconnecter.

  - Toutes les activités Azure sont contrôlées par notre moteur de détection des anomalies, qui vous signale automatiquement tout comportement suspect dans le portail Azure, notamment les voyages impossibles, les activités de masse suspectes et les activités provenant d’un nouveau pays.  

  Pour plus d’informations, consultez [Connecter Azure à Microsoft Cloud App Security](connect-azure-to-microsoft-cloud-app-security.md).

- **Déploiements étendus** (déploiement progressif)  
Microsoft Cloud App Security permet aux entreprises de déterminer de façon granulaire quels utilisateurs ils souhaitent surveiller et protéger en fonction de l’appartenance à un groupe. Cette fonctionnalité vous permet de sélectionner des utilisateurs dont les activités ne s’afficheront pour aucune des applications protégées. La fonctionnalité de surveillance étendue est particulièrement utile dans les cas suivants :
  - Conformité : si vos réglementations de conformité vous imposent de ne pas surveiller les utilisateurs de certains pays en raison des réglementations locales.
  - Gestion des licences : si vous souhaitez surveiller moins d’utilisateurs pour rester dans les limites de vos licences Microsoft Cloud App Security.
  Pour plus d'informations, consultez [Déploiement étendu](scoped-deployment.md).

- **Alerte d’application transgressée pour les applications découvertes**  
 Nous disposons maintenant d’une alerte intégrée pour vous avertir lorsque l’une des applications découvertes d’un locataire est compromise. L’alerte fournit des informations sur l’heure et la date de la violation, les utilisateurs qui ont utilisé l’application et les liens vers les sources disponibles publiquement qui donnent des informations sur la violation.

- **Nouveau serveur de messagerie**  
 Le serveur de messagerie de Cloud App Security a changé et utilise des plages d’adresses IP différentes. Pour vous assurer que vous pouvez recevoir des notifications, ajoutez les nouvelles adresses IP à votre liste verte anti-courrier indésirable. Microsoft Cloud App Security permet aux utilisateurs de personnaliser leurs notifications avec MailChimp®, un service de messagerie tiers. Pour obtenir la liste des adresses IP du serveur de messagerie ainsi que des instructions sur l’activation de l’utilisation de MailChimp, consultez [Configuration réseau requise](network-requirements.md#mail-server) et [Paramètres de messagerie](mail-settings.md).

## <a name="cloud-app-security-release-123"></a>Cloud App Security version 123

Publication : 13 mai 2018

- **Étendue de la stratégie de détection des anomalies** :  
les stratégies de détection des anomalies peuvent désormais être étendues. Cela vous permet de définir chaque stratégie de détection d’anomalie pour inclure uniquement des utilisateurs ou des groupes spécifiques et exclure des utilisateurs ou des groupes spécifiques. Par exemple, sous Activité, vous pouvez définir la détection d’une région rare ou ignorer un utilisateur spécifique qui voyage fréquemment.

## <a name="cloud-app-security-release-122"></a>Cloud App Security version 122

Publication : 29 avril 2018

- Déploiement progressif : Vous pouvez maintenant **définir des autorisations d’administration pour les administrateurs Microsoft Cloud App Security par application**. Par exemple, vous pouvez définir un utilisateur spécifique comme administrateur pour G Suite seulement. L’utilisateur peut ainsi afficher et modifier des informations dans Microsoft Cloud App Security uniquement pour G Suite. Pour plus d’informations, consultez [Gestion de l’accès administrateur](manage-admins.md).

- Déploiement progressif : **Les rôles d’administrateur Okta sont désormais visibles** dans Microsoft Cloud App Security et disponibles pour chaque rôle sous la forme d’une balise sous **Paramètres** > **Groupes d’utilisateurs**.

## <a name="cloud-app-security-release-121"></a>Cloud App Security version 121

Publication : 22 avril 2018

- La préversion publique du **contrôle d’application par accès conditionnel (anciennement appelé proxy Cloud App Security)** a été améliorée grâce à des fonctionnalités qui offrent une meilleure visibilité et permettent de contrôler diverses applications. Vous pouvez maintenant créer une stratégie de session avec un filtre *Type d’activité* pour surveiller et bloquer une variété d’activités spécifiques à l’application. Ce nouveau filtre augmente les fonctionnalités existantes de contrôle de téléchargement de fichiers, pour un contrôle complet des applications de votre organisation. Il fonctionne conjointement avec l’accès conditionnel Azure Active Directory pour offrir une visibilité en temps réel et contrôler les sessions des utilisateurs à risque. Il peut s’agir de sessions avec des utilisateurs entretenant une collaboration B2B ou des utilisateurs dont l’appareil est non géré. Pour plus d’informations, consultez [Stratégies de session](session-policy-aad.md).

- Déploiement progressif : Concernant Cloud App Security, les **stratégies de détection d’anomalies ont été améliorées** pour inclure deux nouveaux types de détection des menaces : Activité de ransomware et activité d’utilisateurs supprimés. Cloud App Security a étendu ses fonctionnalités de détection de ransomware à la détection d’anomalies pour garantir une couverture plus complète contre les attaques par ransomware sophistiqué. Grâce à notre expertise en matière de recherche sur la sécurité pour identifier des modèles de comportement qui reflètent l’activité des ransomware, Cloud App Security garantit une protection holistique et robuste. L’activité des utilisateurs supprimés vous permet de surveiller les comptes des utilisateurs supprimés, qui ont peut-être été désapprovisionnés à partir d’applications d’entreprise, mais ont souvent toujours accès à certaines ressources d’entreprise. Pour plus d’informations, consultez [Obtenir instantanément des analyses comportementales et une détection d’anomalies](anomaly-detection-policy.md).

## <a name="cloud-app-security-release-120"></a>Cloud App Security version 120

Publication : 8 avril 2018

- Pour Office 365 et Azure AD, nous mettons maintenant progressivement en place la possibilité de détecter des applications internes en tant qu’activités comptes utilisateurs effectuées par les applications Office 365 et Azure AD (internes et externes). Ceci vous permet de créer des stratégies qui vous alerteront si une application a des activités inattendues et non autorisées.

- Lors de l’exportation d’une liste de permissions d'applications au format CSV, des champs supplémentaires tels que l’éditeur, le niveau d’autorisation et l’utilisation de la communauté sont inclus pour faciliter le processus de conformité et d’investigation.

- L’application connectée ServiceNow a été améliorée afin que les activités de service internes ne s’inscrivent plus comme ayant été effectuées par « Invité » et ne déclenchent plus d’alertes de faux positifs. Ces activités sont maintenant représentées en tant que N/A, comme toutes les autres applications connectées.

## <a name="cloud-app-security-release-119"></a>Cloud App Security version 119

Date de publication : 18 mars 2018

- La page des plages d’adresses IP contient des adresses IP intégrées qui sont découvertes par Cloud App Security. Ceci inclut des adresses IP des services cloud identifiés, tels qu’Azure et Office 365, ainsi que le flux de renseignements sur les menaces qui enrichit automatiquement les adresses IP avec des informations sur les adresses IP à risque connues.

- Lorsque Cloud App Security tente d’exécuter une action de gouvernance sur un fichier, mais échoue parce que le fichier est verrouillé, il fait automatiquement une nouvelle tentative.

## <a name="cloud-app-security-release-118"></a>Cloud App Security version 118

Publication : 4 mars 2018

- Vous pouvez désormais tirer parti des fonctionnalités de surveillance et de découverte du Shadow IT de Microsoft Cloud App Security pour vos propres applications propriétaires personnalisées. La nouvelle possibilité d’ajouter des applications personnalisées à Cloud Discovery vous permet de surveiller l’utilisation des applications et de recevoir des alertes si des modifications sont apportées au modèle d’utilisation. Pour plus d’informations, consultez [Protection de vos applications personnalisées](cloud-discovery-custom-apps.md). Cette fonctionnalité est déployée progressivement.

- Les pages **Paramètres** du portail Cloud App Security ont été remaniées. La nouvelle conception améliorée consolide toutes les pages de paramètres et fournit des fonctionnalités de recherche.

- Cloud Discovery prend désormais en charge les pare-feu de série F Barracuda et la diffusion en continu des journaux de la série F.

- La fonctionnalité de recherche dans les pages Utilisateur et Adresses IP permet désormais la saisie semi-automatique, ce qui vous aide à trouver ce que vous cherchez.

- Vous pouvez maintenant effectuer des actions en bloc dans les pages de paramètres Exclure des entités et Exclure une adresse IP. Cela vous permet de sélectionner plus facilement plusieurs utilisateurs et groupes ou adresses IP et de les exclure de la surveillance dans le cadre de Cloud Discovery de votre organisation.

## <a name="cloud-app-security-release-117"></a>Cloud App Security version 117

Date de publication : 20 février 2018

- L’intégration plus poussée de Cloud App Security avec Azure Information Protection vous permet désormais de protéger les fichiers dans G Suite. Cette fonctionnalité en préversion publique vous permet d’analyser et de classifier des fichiers dans G Suite, et d’appliquer automatiquement des étiquettes Azure Information Protection pour la protection. Pour plus d’informations, consultez [Intégration d’Azure Information Protection](azip-integration.md).

- Cloud Discovery prend désormais en charge [Digital Arts i-FILTER](https://www.daj.jp/en/products/if/).

- Le tableau des agents SIEM fournit désormais plus de détails pour faciliter la gestion.

## <a name="cloud-app-security-release-116"></a>Cloud App Security version 116

Date de publication : 4 février 2018

- La stratégie de détection d’anomalies de Cloud App Security a été améliorée grâce à de nouvelles **détections basées sur des scénarios**, notamment un voyage impossible, une activité à partir d’une adresse IP suspecte et plusieurs échecs de tentatives de connexion. Les nouvelles stratégies sont automatiquement activées, fournissant une détection des menaces prête à l’emploi dans votre environnement cloud. De plus, les nouvelles stratégies exposent davantage de données à partir du moteur de détection Cloud App Security pour vous aider à accélérer le processus d’investigation et à contenir des menaces continues. Pour plus d’informations, consultez [Obtenir instantanément des analyses comportementales et une détection d’anomalies](/cloud-app-security/anomaly-detection-policy).

- Déploiement progressif : Cloud App Security met désormais en corrélation les utilisateurs et leurs comptes dans les applications SaaS. Vous pouvez ainsi examiner facilement toutes les activités d’un utilisateur dans toutes ses applications SaaS corrélées, quels que soient l’application ou le compte utilisés.

- Déploiement progressif : Cloud App Security prend désormais en charge plusieurs instances de la même application connectée. Si vous avez plusieurs instances, par exemple de Salesforce (une pour les ventes, une pour le marketing), vous pourrez les connecter à Cloud App Security et les gérer à partir de la même console pour créer des stratégies granulaires et des investigations plus approfondies.

- Les analyseurs Cloud Discovery prennent désormais en charge deux formats de point de contrôle supplémentaires, à savoir XML et KPC.

## <a name="cloud-app-security-release-115"></a>Cloud App Security version 115

Publication : 21 janvier 2018

- Cette version offre une expérience améliorée lors de la sélection de dossiers spécifiques dans les stratégies de fichiers. Vous pouvez désormais facilement afficher et sélectionner plusieurs dossiers à inclure dans une stratégie.
- Dans la page **Applications découvertes** :
  - La fonctionnalité de balisage en bloc vous permet d’appliquer des balises personnalisées (en plus des balises approuvées et non approuvées).
  - Lorsque vous **générez un rapport sur les adresses IP** ou que vous **générez un rapport sur les utilisateurs**, les rapports exportés incluent désormais les informations indiquant si le trafic provient d’applications approuvées ou non approuvées.
- Vous pouvez désormais demander un nouveau connecteur d’application API à l’équipe Microsoft Cloud App Security directement dans le portail, à la page **Connecter une application**.

## <a name="cloud-app-security-release-114"></a>Cloud App Security version 114

Publication : 7 janvier 2018

- Depuis la version 114, nous déployons progressivement la possibilité de créer et d’enregistrer des requêtes personnalisées dans les pages Journal d’activité et Applications découvertes. Les requêtes personnalisées vous permettent de créer des modèles de filtres pouvant être réutilisés pour une investigation approfondie. De plus, les **Requêtes suggérées** ont été ajoutées pour fournir des modèles d’investigation prêts à l’emploi avec lesquels vous pourrez filtrer vos activités et vos applications découvertes. Les **requêtes suggérées** incluent des filtres personnalisés pour identifier les risques tels que les activités d’usurpation d’identité, les activités d’administrateurs, les applications de stockage cloud non conformes à risque, les applications d’entreprise avec un chiffrement faible et les risques de sécurité. Vous pouvez utiliser les **requêtes suggérées** comme point de départ, les modifier comme bon vous semble, puis les enregistrer en tant que nouvelle requête. Pour plus d’informations, consultez [Filtres d’activité et requêtes](activity-filters-queries.md) ainsi que [Filtres et requêtes d’applications découverts](discovered-app-queries.md).

- Vous pouvez maintenant vérifier l’état actuel du service Cloud App Security en accédant à [status.cloudappsecurity.com](https://status.cloudappsecurity.com) ou directement à partir du portail en cliquant sur **Aide**>**État du système**.

## <a name="see-also"></a>Voir aussi

Pour obtenir une description des versions antérieures à celles répertoriées ici, consultez [Versions antérieures de Microsoft Cloud App Security](release-note-archive.md).

[!INCLUDE [Open support ticket](includes/support.md)]
