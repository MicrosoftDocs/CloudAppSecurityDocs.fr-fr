---
title: Archivage des mises à jour précédentes dans Cloud App Security
description: Cet article est une archive qui décrit les mises à jour effectuées dans les versions précédentes de Cloud App Security.
ms.date: 11/25/2020
ms.topic: conceptual
ms.openlocfilehash: 50f8bc735743d1506ac9ad18e6b10b659de7ab6e
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96315546"
---
# <a name="past-release-archive-of-microsoft-cloud-app-security"></a>Archive des versions précédentes de Microsoft Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Cet article est une archive qui décrit les mises à jour effectuées dans les versions précédentes de Cloud App Security. Pour obtenir la dernière liste Nouveautés, consultez [Nouveautés dans Cloud App Security](release-notes.md).

## <a name="updates-made-in-2019"></a>Mises à jour effectuées dans 2019

### <a name="cloud-app-security-release-162-163-and-164"></a>Cloud App Security versions 162, 163 et 164

Publication : 8 décembre 2019

- **Modification des activités et alertes SIEM au format CEF**  
Le [format de l’URL du portail (CS1)](siem.md#sample-cloud-app-security-alerts-in-cef-format) pour les informations sur l’activité et les alertes envoyées par Cloud App Security aux SIEM est passé à `https://<tenant_name>.portal.cloudappsecurity.com` et ne contient plus l’emplacement du centre de données. Les clients qui utilisent des critères spéciaux pour l’URL du portail doivent mettre à jour le modèle pour refléter cette modification.

### <a name="cloud-app-security-release-160-and-161"></a>Cloud App Security versions 160 et 161

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
Cloud App Security Cloud Discovery analyse une large gamme de journaux de trafic pour classer et noter les applications. L’analyseur de journal intégré à Cloud Discovery prend maintenant en charge le format de journal Ironport WSA 10.5.1.

- **Page d’accueil utilisateur personnalisable pour les contrôles de session**  
Nous avons lancé la possibilité pour les administrateurs de personnaliser la page d’accueil que vos utilisateurs voient lors de la navigation vers une application à laquelle une stratégie de session est appliquée. Vous pouvez maintenant afficher le logo de votre organisation et personnaliser le message affiché. Pour commencer la personnalisation, accédez à la page **Paramètres** et, sous **Contrôle d’application d’accès au cloud**, sélectionnez **Analyse utilisateur**.

- **Nouvelles détections**  

  - **Modifications suspectes du service de journalisation AWS (préversion)**  : Vous avertit lorsqu’un utilisateur apporte des modifications au service de journalisation CloudTrail. Par exemple, les attaquants désactivent souvent l’audit dans CloudTrail pour masquer les empreintes de leur attaque.

  - **Multiples activités de création de machines virtuelles** : Vous alerte lorsqu'un utilisateur effectue un nombre inhabituel d'activités de création de machines virtuelles par rapport à la référence apprise. S’applique désormais à AWS.

### <a name="cloud-app-security-release-159"></a>Cloud App Security version 159

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

### <a name="cloud-app-security-release-158"></a>Cloud App Security version 158

Publication : 15 septembre 2019

- **Personnaliser un nom de rapport exécutif Cloud Discovery**  
Le rapport exécutif Cloud Discovery vous donne une vue d’ensemble de l’utilisation du Shadow IT dans votre organisation. Vous avez maintenant la possibilité de personnaliser le nom du rapport avant de le générer. Pour plus d’informations, consultez [Générer un rapport exécutif Cloud Discovery](discovered-apps.md#generate-cloud-discovery-executive-report).

- **Rapport de vue d’ensemble des nouvelles stratégies**  
Cloud App Security détecte les correspondances de stratégie et, le cas échéant, consigne les alertes que vous pouvez utiliser pour mieux comprendre votre environnement cloud. Vous pouvez maintenant exporter un rapport de vue d’ensemble des stratégies avec des métriques d’alerte agrégées par stratégie pour vous aider à surveiller, à comprendre et à personnaliser vos stratégies afin de mieux protéger votre organisation. Pour plus d’informations sur l’exportation du rapport, consultez [Rapport de vue d’ensemble des stratégies](control-cloud-apps-with-policies.md#policies-overview-report).

### <a name="cloud-app-security-release-157"></a>Cloud App Security version 157

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

### <a name="cloud-app-security-release-156"></a>Cloud App Security version 156

Publication : 18 août 2019

- **Nouveaux analyseurs de journal Cloud Discovery**  
Cloud App Security Cloud Discovery analyse une large gamme de journaux de trafic pour classer et noter les applications. Cloud Discovery intègre désormais un analyseur de journaux intégré pour prendre en charge les formats de journaux Stormshield et Forcepoint LEEF.

- **Améliorations du journal d’activité**  
Cloud App Security offre désormais une meilleure visibilité des activités non classifiées effectuées par les applications dans votre environnement. Ces activités sont disponibles dans le journal d’activité ainsi que dans les stratégies d’activité. Pour voir les activités non classifiées, dans le filtre **Type**, sélectionnez **Non spécifié**. Pour plus d’informations sur les filtres d’activité, consultez [Filtres d’activité et requêtes](activity-filters-queries.md).

- **Amélioration des investigations sur les utilisateurs à risque**  
Cloud App Security permet d’identifier les utilisateurs à risque dans la page **Utilisateurs et comptes** par groupes, applications et même rôles spécifiques. Vous pouvez désormais également examiner les utilisateurs de votre organisation en fonction de leur score **Priorité d’une enquête**. Pour plus d’informations, consultez [Comprendre le score de priorité d’examen](tutorial-ueba.md#risk-score).

- **Améliorations de la stratégie d’activité**  
Vous pouvez désormais créer des alertes de stratégie d’activité basées sur des objets d’activité. Par exemple, cette fonctionnalité vous permet de créer des alertes sur les modifications apportées aux rôles d’administration d’Azure Active Directory. Pour plus d’informations sur les objets d’activité, consultez [Filtres d’activité](activity-filters-queries.md#activity-filters).

### <a name="cloud-app-security-release-155"></a>Cloud App Security version 155

Publication : 4 août 2019

- **Nouveaux modèles de stratégie**  
Cloud App Security intègre maintenant de nouveaux modèles de stratégies d'activité pour de meilleures pratiques de sécurité AWS.

- **Avertissement : Fin de la prise en charge de TLS 1.0 et 1.1 le 8 septembre**  
Microsoft transfère tous ses services en ligne vers Transport Layer Security (TLS) 1.2+ pour fournir le meilleur chiffrement de sa catégorie. Par conséquent, à partir du 8 septembre 2019, Cloud App Security ne prendra plus en charge TLS 1.0/1.1 et les connexions utilisant ces protocoles. Pour plus d'informations sur l’impact de ce changement, lisez [notre billet de blog](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/End-of-support-for-TLS-1-0-and-1-1-in-Microsoft-Cloud-App/ba-p/770507).

- **Logique améliorée pour les activités de connexion interactives (déploiement graduel)**  
Nous déployons progressivement une nouvelle logique pour déterminer si une activité de connexion Azure Active Directory est interactive. La nouvelle logique améliore la capacité de Cloud App Security à signaler uniquement les activités de connexion qui sont lancées par un utilisateur.

### <a name="cloud-app-security-release-154"></a>Cloud App Security version 154

Publication : 21 juillet 2019

- **Intégrer et déployer le contrôle d’application par accès conditionnel pour tous les types d’applications maintenant en GA**  
Depuis que nous vous avons montré un aperçu du contrôle d’application par accès conditionnel pour toutes les applications le mois dernier, nous avons reçu un feedback incroyable et nous sommes donc très contents d’annoncer sa disponibilité générale. Cette nouvelle fonctionnalité vous permet de déployer n’importe quelle application web en vue d’utiliser des stratégies de session et d’accès, et de bénéficier de puissantes fonctionnalités de supervision et de contrôle en temps réel.

- **Évaluation de la configuration de la sécurité pour AWS**  
Cloud App Security met progressivement en place la possibilité d’obtenir une évaluation de la configuration de la sécurité de votre environnement Amazon Web Services à des fins de conformité CIS, et fournit des recommandations s’il manque des configurations et des contrôles de la sécurité. Cette fonctionnalité permet aux organisations de superviser l’état de conformité de tous les comptes AWS connectés à partir d’une seule vue.

- **Détections d’anomalies d’application OAuth**  
Nous avons étendu notre actuelle fonctionnalité de détection d’applications OAuth suspectes. Quatre nouvelles détections sont maintenant prêtes à l’emploi, qui profilent les métadonnées des applications OAuth autorisées dans votre organisation pour identifier celles qui sont potentiellement malveillantes.

### <a name="cloud-app-security-release-153"></a>Cloud App Security mise en production 153

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

### <a name="cloud-app-security-release-152"></a>Cloud App Security version 152

Publication : 23 juin 2019

- **Déployer le contrôle d’application par accès conditionnel pour tous les types d’applications (préversion)**  
Nous sommes heureux d’annoncer que nous avons étendu notre prise en charge du contrôle d’application par accès conditionnel à l’ensemble des applications web, en plus de la prise en charge que nous proposons déjà pour les [applications à la une](proxy-intro-aad.md). Cette nouvelle fonctionnalité vous permet de déployer n’importe quelle application web en vue d’utiliser des stratégies de session et d’accès, et de bénéficier de puissantes fonctionnalités de supervision et de contrôle en temps réel. Par exemple, vous pouvez protéger les téléchargements avec des étiquettes Azure Information Protection, bloquer le chargement des documents sensibles, effectuer des audits, et bien plus encore.
- **Audit des activités dans le portail**  
Cloud App Security audite toutes les activités d’administration du portail, vous permettant ainsi de superviser et d’analyser les activités de manière approfondie. À présent, vous pouvez également exporter jusqu’à 90 jours d’activités en vue de procéder à une analyse. Par exemple, vous pouvez auditer un administrateur qui analyse les activités d’un utilisateur ou qui affiche certaines alertes. Pour exporter le journal, accédez à la page de paramètres **Gérer l’accès administrateur**.
- **Déconnexion de session personnalisée à partir du portail Cloud App Security**  
Vous pouvez désormais configurer la déconnexion automatique des sessions administrateur du portail après une durée d’inactivité spécifiée.

### <a name="cloud-app-security-release-151"></a>Cloud App Security version 151

Publication : 9 juin 2019

- **UEBA hybride - Intégration native avec Azure ATP (préversion)**  
Cloud App Security s’intègre maintenant en mode natif dans Azure ATP pour fournir une vue unique des activités d’identité dans les applications cloud et votre réseau local. Pour plus d’informations, consultez [Intégration d’Azure Advanced Threat Protection](mdi-integration.md).
- **Améliorations apportées à UEBA**  
Pour vous aider à identifier les menaces qui échappent aux contrôles, Cloud App Security utilise désormais le profilage unique afin de fournir des indices de risque pour les alertes et activités individuelles. Les scores de risque peuvent être utilisés pour identifier des activités qui ne sont pas assez suspectes en elles-mêmes pour déclencher des alertes. Toutefois, en regroupant les indices de risque dans un **indice de priorité d’examen** pour l’utilisateur, Cloud App Security vous permet d’identifier des comportements à risques et de concentrer votre examen. Ces fonctionnalités sont désormais disponibles dans la nouvelle page utilisateur.
- **Nouveau facteur de risque ajouté au catalogue d’applications cloud**  
Le catalogue d’applications cloud inclut désormais le facteur de risque du plan de récupération d’urgence pour vous permettre d’évaluer les applications dans le catalogue d’applications cloud pour la prise en charge de la continuité des activités métier.
- **Connecteur Microsoft Flow GA**  
Après la préversion de sa prise en charge par Microsoft Cloud App Security l’an dernier, le connecteur Microsoft Flow est maintenant en disponibilité générale.
- **Amélioration de gouvernance automatisées pour les stratégies de fichiers**  
Cloud App Security prend désormais en charge la configuration de l’action de gouvernance **Mettre à la corbeille** pour les stratégies de fichiers. Cette action de gouvernance vous permet de déplacer automatiquement des fichiers vers le dossier Corbeille.
- **Prise en charge améliorée de Google Drive**  
Cloud App Security prend désormais en charge l’action de gouvernance **Mettre à la corbeille** pour les stratégies de fichiers. Cette action de gouvernance vous permet de déplacer automatiquement des fichiers Google Drive vers le dossier Corbeille.
- **Nouvelle autorisation pour les rôles d’administrateur d’application et d’administrateur de groupe**  
Les rôles *Administrateur d’application/d’instance* et *Administrateur de groupe d’utilisateurs* prennent désormais en charge l’accès en lecture seule.
- **Activités de connexion d’authentification héritées (déploiement graduel)**  
Cloud App Security signale maintenant les activités de connexion Azure Active Directory qui utilisent des protocoles hérités comme ActiveSync. Ces activités de connexion peuvent être consultées dans le journal d’activité et peuvent être utilisées lors de la configuration des stratégies.

### <a name="cloud-app-security-release-150"></a>Cloud App Security version 150

Publication : le 26 mai 2019

- **Amélioration de l’exportation des alertes**  
Lorsque vous exportez des alertes au format CSV à partir de la page **Alertes**, les résultats incluront désormais la date de résolution ou de rejet de l'alerte.

### <a name="cloud-app-security-release-148-and-149"></a>Cloud App Security versions 148 et 149

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
Lorsque vous connectez Office 365 à Microsoft Cloud App Security, vous pouvez maintenant choisir les charges de travail à connecter. Par exemple, les clients uniquement intéressés par la connexion d’Office 365 pour la surveillance de l’activité peuvent désormais le faire pendant le processus de connexion ou en modifiant un connecteur Office 365 existant. Dans le cadre de ce changement, OneDrive et SharePoint ne seront plus affichés en tant que connecteurs séparés mais seront inclus dans le connecteur Office 365 en tant que charge de travail des fichiers _Office 365_. Les clients disposant d’un connecteur Office 365 existant ne sont pas affectés par cette modification.

- **Prise en charge améliorée de Teams**  
Vous pouvez désormais surveiller et bloquer l’envoi de message dans l’application web Teams en temps réel, en configurant une stratégie de session basée sur du contenu sensible.

### <a name="cloud-app-security-release-147"></a>Cloud App Security version 147

Publication : 14 avril 2019

- **Nouvel analyseur de journal Cloud Discovery**  
Cloud App Security Cloud Discovery inclut désormais un analyseur de journal intégré pour prendre en charge le format de journal Palo Alto LEEF.

- **Mises à jour des stratégies de session**  
  - **Méthode d’inspection du contenu supplémentaire pour les stratégies de session** :  Lorsque vous définissez une stratégie de session, vous avez désormais la possibilité de choisir le Service de classification des données en tant que méthode d’inspection du contenu pour les fichiers. Le Service de classification des données offre à l’utilisateur un large éventail de types sensibles intégrés à utiliser pour identifier les informations sensibles.
  - **Contrôle amélioré des autorisations de fichier dans les stratégies de session** :  Lorsque vous créez une stratégie de session pour contrôler les téléchargements à l’aide de Cloud App Security, vous pouvez maintenant appliquer automatiquement les autorisations utilisateur par utilisateur aux documents, comme la lecture seule, lors de leur téléchargement à partir de vos applications cloud. Cela fournit un niveau supérieur de flexibilité et la possibilité de protéger les informations au-delà de vos étiquettes d’entreprise préconfigurées.
  - **Contrôle du téléchargement de fichiers volumineux** :  Lorsque l’inspection du contenu est activée dans les stratégies de session, vous pouvez désormais contrôler ce qui se passe quand un utilisateur tente de télécharger un fichier très volumineux. Si le fichier est trop volumineux pour une analyse lors du téléchargement, vous pouvez choisir s’il sera bloqué ou autorisé.

### <a name="cloud-app-security-release-146"></a>Cloud App Security version 146

Date de publication : 31 mars 2019

- **Amélioration du voyage impossible**  
La détection d’un voyage impossible a été améliorée avec une prise en charge dédiée pour les pays/régions voisin(e)s.
- **Prise en charge d’attributs supplémentaires pour l’analyseur CEF générique**  
La prise en charge de l’analyseur du journal Cloud Discovery pour le format CEF générique a été améliorée pour prendre en charge des attributs supplémentaires.
- **Accès étendu aux rapports Cloud Discovery**  
En plus du rôle Discovery Admin, vous pouvez maintenant étendre l’accès à des rapports Discovery spécifiques. Cette amélioration vous permet de configurer des privilèges d’accès aux données de sites et divisions spécifiques.
- **Nouvelle prise en charge de rôle : lecteur général**  
Microsoft Cloud App Security prend désormais en charge le rôle de lecteur général Azure AD. Le lecteur général dispose d’un accès complet en lecture seule à tous les aspects de Microsoft Cloud App Security, mais il ne peut ni modifier des paramètres ni prendre aucune mesure.

### <a name="cloud-app-security-release-145"></a>Cloud App Security version 145

Date de publication : 17 mars 2019

- **L’intégration de Microsoft Defender ATP est en disponibilité générale**  
L’année dernière, nous avons annoncé l’[intégration avec Windows Defender Advanced Threat Protection](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Cloud-App-Security-and-Windows-Defender-ATP-better/ba-p/263265), qui améliore la découverte du Shadow IT dans votre organisation et l’étend au-delà du réseau d’entreprise. Nous sommes heureux de vous annoncer que cette intégration unique, [Activée par simple clic](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RWtNmG), est désormais disponible en général.
- **Prise en charge de Dynamics 365 CRM**  
Cloud App Security a ajouté des fonctionnalités de supervision et de contrôle en temps réel pour Dynamics 365 CRM, afin de vous permettre de protéger vos applications métier et le contenu sensible stocké dans ces applications. Pour plus d'informations sur les possibilités offertes par Dynamics 365 CRM, lisez [cet article](proxy-intro-aad.md#how-it-works).

### <a name="cloud-app-security-release-144"></a>Cloud App Security version 144

Date de publication : 3 mars 2019

- **Investigation unifiée de SecOps pour les environnements hybrides**  
Étant donné que de nombreuses organisations ont des environnements hybrides, les attaques démarrent dans le cloud avant de basculer en local, ce qui signifie que les équipes SecOps doivent investiguer ces attaques depuis différents endroits. Grâce à la combinaison des signaux de sources cloud et locales, notamment Microsoft Cloud App Security, Azure ATP et Azure AD Identity Protection, Microsoft autonomise les analystes de sécurité en fournissant des informations sur l’identité unifiée et l’utilisateur dans une console unique pour mettre fin au basculement entre les solutions de sécurité. Vos équipes SecOP ont ainsi plus de temps et les bonnes informations pour prendre de meilleures décisions et remédier activement aux menaces et aux risques réels liés à l’identité. Pour plus d’informations, consultez [Investigation unifiée de SecOps pour les environnements hybrides](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Unified-SecOps-Investigation-for-Hybrid-Environments/ba-p/360850)

- **Fonctionnalités de sandboxing pour la détection de programmes malveillants** (déploiement progressif)  
Les fonctionnalités de détection de programmes malveillants de Cloud App Security sont en cours de développement afin d’inclure la possibilité d’identifier les programmes malveillants zero-day par le biais d’une technologie de sandboxing avancée.  
Dans le cadre de cette fonctionnalité, Cloud App Security identifie automatiquement les fichiers suspects et les fait exploser pour rechercher un comportement suspect des fichiers et indique que le fichier a des intentions malveillantes (programme malveillant).
Dans le cadre de cette modification, les stratégies de détection de programmes malveillants incluent désormais un champ de type Détection qui vous permet de filtrer par renseignement sur les menaces ainsi que par sandboxing.

- **Mises à jour de l’accès conditionnel**  
Avec le contrôle d’application par accès conditionnel, vous avez maintenant la possibilité de superviser et de bloquer les activités suivantes :
  - Chargez des fichiers dans n’importe quelle application : activez des scénarios tels qu’empêcher le chargement d’extensions de programmes malveillants connus et garantir que les utilisateurs protègent les fichiers avec Azure Information Protection avant le chargement.
  - Copiez et collez dans n’importe quelle application : renforcez les contrôles robustes de l’exfiltration des données, qui incluaient déjà le téléchargement, l’impression et les activités personnalisées telles que le partage.
  - Envoyez un message : vérifiez que les données personnelles, telles que les mots de passe, ne sont pas partagées dans des outils de collaboration populaires comme Slack, Salesforce ou Workplace by Facebook.
  - Les stratégies des sessions incluent maintenant des modèles intégrés. Ils permettent à votre organisation d’activer sans effort une surveillance et un contrôle en temps réel populaires, tels que **Bloquer le chargement sur la base de l’inspection du contenu en temps réel**.

### <a name="cloud-app-security-release-143"></a>Cloud App Security version 143

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

### <a name="cloud-app-security-release-142"></a>Cloud App Security version 142

Date de publication : 3 février 2019

- **Configuration de la stratégie de session dans Azure AD**  
Vous pouvez désormais configurer des stratégies de session pour surveiller les utilisateurs ou bloquer les téléchargements en temps réel, directement dans l’accès conditionnel Azure AD. Vous pouvez toujours configurer des stratégies de session avancées directement dans Cloud App Security. Pour parcourir ce déploiement, consultez [Déployer un contrôle d’application par accès conditionnel pour les applications Azure AD](proxy-deployment-aad.md).

- **Requêtes suggérées et enregistrées pour les applications OAuth**  
Les requêtes suggérées ont été ajoutées à la page d’applications OAuth, qui fournissent des modèles d’investigation prêts à l’emploi pour filtrer vos applications OAuth. Les requêtes suggérées incluent des filtres personnalisés pour identifier les applications à risque, telles que les applications autorisées par les administrateurs. Les requêtes enregistrées vous permettent d’enregistrer des requêtes personnalisées pour une utilisation future, comme les requêtes enregistrées disponibles aujourd’hui dans le journal d’activité et les pages de découverte.

- **Configuration par défaut de l’audit Office 365**  
Si vous souhaitez activer la surveillance des activités d’Office 365 dans Cloud App Security, vous devez maintenant activer l’audit dans le [Centre de sécurité et de conformité Office](/office365/securitycompliance/turn-audit-log-search-on-or-off#turn-on-audit-log-search), ce qui résulte d’une [modification de d’audit Office 365](/office/office-365-management-api/office-365-management-activity-api-faq#what-happens-if-i-disable-auditing-for-my-office-365-organization-will-i-still-get-events-via-the-management-activity-api). Cette modification n’est nécessaire que si vous n’avez pas déjà activé le monitoring des activités d’Office 365 dans Cloud App Security.

- **Prise en charge améliorée de Box**  
Cloud App Security prend désormais en charge deux nouvelles actions de gouvernance pour Box :

  - **Faire expirer le lien partagé** : cette action de gouvernance vous permet de définir une date d’expiration après laquelle un lien partagé ne sera plus actif.

  - **Modifier le niveau d’accès au lien de partage** : cette action de gouvernance vous permet de modifier le niveau d’accès au lien de partage uniquement dans la société, uniquement entre les collaborateurs et au niveau public.

- **Support de plusieurs emplacements dans OneDrive**  
Cloud App Security offre désormais une visibilité complète des fichiers OneDrive, même s’ils sont répartis sur plusieurs emplacements géographiques. La protection est désormais disponible pour les fichiers situés aux emplacements supplémentaires ainsi qu’à l’emplacement principal.

- **Amélioration de la navigation dans le portail**  
Le portail Cloud App Security a été amélioré pour offrir une meilleure navigation et mieux aligner Cloud App Security sur les autres services de sécurité de Microsoft, l’objectif étant de simplifier et de rationaliser son utilisation.

### <a name="cloud-app-security-release-141"></a>Cloud App Security version 141

Publiée le 20 janvier 2019

- **Améliorations de l’évaluation des risques dans le cloud**  
  - L’évaluation des risques du logiciel cloud a été améliorée avec deux nouvelles expériences.
    - Un nouvel attribut **Type de données** évalue le type de contenu que les utilisateurs peuvent charger vers l’application. Vous pouvez utiliser cet attribut pour évaluer une application en fonction de la sensibilité de chaque type de données dans votre organisation.
    - Pour obtenir une vue d’ensemble plus complète des risques d’une application, vous pouvez désormais facilement passer de l’évaluation des risques de l’application à l’évaluation des risques de la société d’hébergement en cliquant sur l’attribut **Société d’hébergement**.

- **Contexte de fichier amélioré pour l’investigation d’alerte de détection d’anomalie**  
  - L’investigation de détection d’anomalies a été améliorée pour vous permettre d’obtenir des insights supplémentaires associée aux fichiers impliqués dans une alerte. Lorsque des alertes sont déclenchées en cas d’activité inhabituelle liée à des fichiers (téléchargement, partage, suppression), ce zoom avant est disponible. Par exemple, si la plupart des fichiers affectés proviennent du même dossier ou partagent la même extension de fichier, vous verrez ces insights dans la section Risque supplémentaire de l’alerte.

- **Requêtes pour l’investigation des fichiers**  
  - La capacité de création et d’enregistrement de requêtes personnalisées de Cloud App Security a été étendue à la page **Fichiers**. Les requêtes de la page **Fichiers** vous permettent de créer des modèles de requêtes pouvant être réutilisés pour une investigation approfondie.

### <a name="cloud-app-security-release-139-140"></a>Cloud App Security versions 139, 140

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

## <a name="updates-made-in-2018"></a>Mises à jour effectuées dans 2018

### <a name="cloud-app-security-release-138"></a>Cloud App Security version 138

Mise en production du 9 décembre 2018

- **Chargement automatique de journaux à l’aide de Docker sur Windows**  
Cloud App Security prend désormais en charge le chargement automatique de journaux pour Windows 10 (Fall Creators Update) et Windows Server (versions 1709 et ultérieures) à l’aide d’un Docker pour Windows. Pour obtenir plus d’informations et des instructions sur la configuration de cette fonctionnalité, consultez [Docker sur Windows en local](discovery-docker-windows.md).

- Cloud App Security est intégré dans [Microsoft Flow](/flow/getting-started) pour fournir une automatisation des alertes et des playbooks d’orchestration personnalisés. Pour plus d’informations et d’instructions d’intégration, consultez [Intégration dans Microsoft Flow](flow-integration.md).

### <a name="cloud-app-security-release-137"></a>Cloud App Security version 137

Publication : 25 novembre 2018

- **Ajout de la prise en charge de Dynamics**  
Cloud App Security prend maintenant en charge les activités Microsoft Dynamics qui sont prises en charge dans le journal d’audit d’Office 365.

- **Analyse du contenu chiffré (préversion)**  
Cloud App Security vous permet dorénavant d’analyser le contenu protégé par les étiquettes de protection Azure Information Protection. Ceci vous permettra de trouver du contenu sensible, y compris dans des fichiers déjà chiffrés par Azure Information Protection.

- **Attention, nouvelle terminologie !**  
Pour plus de clarté, le nom des capacités de permission d’application a été modifié. Elles s’appellent maintenant **Applications OAuth**.

### <a name="cloud-app-security-release-136"></a>Cloud App Security version 136

Publication : 11 novembre 2018

- **Mises à jour de Cloud Discovery**  
L’analyseur de journal personnalisé a été amélioré pour prendre en charge des formats de journaux d’activité de trafic web plus complexes. Dans le cadre de ces améliorations, les utilisateurs peuvent désormais entrer des en-têtes personnalisés pour les fichiers journaux CSV sans en-tête, utiliser des séparateurs spéciaux pour les fichiers clé-valeur et traiter le format de fichier Syslog, entre autres.

- **Nouvelles stratégies de détection des anomalies**  
Règles de manipulation de boîtes de réception suspectes : Cette stratégie profile votre environnement et déclenche des alertes lorsque des règles suspectes qui suppriment ou déplacent des messages ou des dossiers sont définies pour la boîte de réception d’un utilisateur. Cela peut indiquer que le compte de l’utilisateur est compromis, que des messages sont intentionnellement masqués et que la boîte aux lettres est utilisée pour distribuer du courrier indésirable ou des programmes malveillants dans votre organisation.

- **Prise en charge de groupes dans les stratégie de permission d’application**  
Cloud App Security vous donne maintenant la possibilité de définir des stratégies de permission d’application de façon plus granulaire, en fonction de l’appartenance à des groupes des utilisateurs qui ont autorisé les applications. Par exemple, un administrateur ne peut décider de définir une stratégie de révocation des applications rares demandant des autorisations élevées que si l’utilisateur qui a donné les autorisations est membre du groupe administrateurs.

- **Le contrôle d’application par accès conditionnel s’intègre désormais à vos applications locales via le proxy d'application Azure Active Directory**  
  - Le [proxy d’application Azure AD](/azure/active-directory/manage-apps/application-proxy) fournit des services d’authentification unique et l’accès à distance sécurisé pour les applications web hébergées localement.
  - Ces applications web locales peuvent désormais être acheminées vers Microsoft Cloud App Security via l’accès conditionnel Azure AD pour fournir une analyse et des contrôles en temps réel par le biais de stratégies d’[accès](access-policy-aad.md) et de [session](session-policy-aad.md).

### <a name="cloud-app-security-release-133-134-135"></a>Cloud App Security versions 133, 134, 135

Publication : octobre 2018

- **Nouvelles stratégies de détection d’anomalies mises en place progressivement**  
  - La nouvelle exfiltration de données vers une stratégie d’applications non approuvées est activée automatiquement pour vous avertir lorsqu'un utilisateur ou une adresse IP utilise une application qui n'est pas approuvée dans le but d’effectuer une activité qui ressemble à une tentative d'exfiltrer des informations de votre organisation.
    - La nouvelle stratégie Plusieurs activités de suppression de machine virtuelle profile votre environnement et déclenche des alertes lorsque des utilisateurs suppriment plusieurs machines virtuelles lors d’une même session, en fonction de la ligne de base de votre organisation.

- **Service de classification des données disponible pour APAC**  
  - L’inspection du contenu du service de classification des données est désormais disponible pour les clients APAC. Pour voir une liste complète de la prise en charge régionale, consultez [Intégration des services de classification des données Microsoft](dcs-inspection.md).

- **Cloud Discovery prend en charge i-Filter**  
  - La fonctionnalité Cloud Discovery de Cloud App Security offre désormais une prise en charge améliorée de l’analyseur syslog i-Filter.

### <a name="cloud-app-security-release-132"></a>Cloud App Security version 132

Publication : 25 septembre 2018

- **Le contrôle d’application par accès conditionnel pour Office 365 est désormais en version préliminaire publique**  
  - Le contrôle d’application par accès conditionnel prend désormais également en charge Office 365 et toute application configurée avec Open ID Connect.
  - Fournir des commentaires à partir d’une session : Ce nouvel outil vous permet de fournir des commentaires sur les performances d’une application sous contrôle d’une session à l’équipe Cloud App Security directement à partir de la session.

- **Intégration native avec Microsoft Defender ATP pour Shadow IT Discovery au-delà de votre société**  
  - Microsoft Cloud App Security s’intègre désormais en mode natif dans Windows Defender Advanced Threat Protection (ATP) pour fournir des fonctionnalités de détection Shadow IT sans déploiement lors de l’utilisation du réseau d’entreprise en mode activé et désactivé par les applications Cloud.  Cela vous permet d’exécuter Cloud Discovery même sur des ordinateurs extérieurs à votre réseau d’entreprise. Ceci permet également une investigation basée sur l’ordinateur : après avoir identifié un utilisateur à risque, vous pouvez vérifier tous les ordinateurs auxquels il a accédé pour détecter les risques potentiels. Si vous identifiez un ordinateur à risque, vous pouvez vérifier tous les utilisateurs qui l’ont utilisé pour examiner les risques potentiels. Pour plus d’informations, consultez l’intégration de Windows Defender Advanced Threat Protection dans [Microsoft Cloud App Security](mde-integration.md).

- **Inspection du contenu des fichiers chiffrés**  
  - Cloud App Security prend désormais en charge l’inspection du contenu des fichiers protégés chiffrés qui ont été protégés à l’aide d’Azure Information Protection. Vous pouvez maintenant examiner ces fichiers chiffrés à des fins de reclassification et identifier d’autres violations de stratégies d’exposition et de sécurité DLP.

### <a name="cloud-app-security-release-131"></a>Cloud App Security version 131

Publication : 2 septembre 2018

- **Révoquer automatiquement les autorisations sur les applications OAuth à risque**  
Vous pouvez désormais contrôler les applications OAuth auxquelles vos utilisateurs ont accès en révoquant l’autorisation App pour les applications OAuth sur Office, Google ou Salesforce. Lorsque vous créez une **stratégie de permission d’application**, vous pouvez maintenant la définir la révocation associée.

- **Analyseur intégré supplémentaire Cloud Discovery pris en charge**  
Cloud Discovery prend désormais en charge le format de journal Forcepoint Web Security Cloud.

### <a name="cloud-app-security-release-130"></a>Cloud App Security version 130

Publication : 22 août 2018

- **Nouvelle barre de menus**  
Pour fournir une expérience d’administration plus cohérente entre les produits Office 365 et vous permettre de passer plus facilement d’une solution de sécurité Microsoft à une autre, la barre de menus du portail Cloud App Security se trouve maintenant sur le côté gauche de l’écran. Cette expérience de navigation cohérente vous aide à vous orienter lorsque vous passez d’un portail de sécurité Microsoft à un autre.

- **Impact sur le score de l’application OAuth**  
Vous pouvez maintenant envoyer des commentaires à l’équipe Cloud App Security pour indiquer si une application OAuth qui semble malveillante a été découverte dans votre organisation. Cette nouvelle fonctionnalité vous permet de faire partie de notre communauté de sécurité ainsi que de contribuer à améliorer l’analyse et le score de risque des applications OAuth. Pour plus d’informations, consultez [Gérer les applications OAuth](manage-app-permissions.md).

- **Nouveaux analyseurs Cloud Discovery**  
Les analyseurs Cloud Discovery prennent désormais en charge iboss Secure Cloud Gateway et Sophos XG.

### <a name="cloud-app-security-release-129"></a>Cloud App Security version 129

Publication : 5 août 2018

- **Nouvelles stratégies de détection d’anomalies : règles relatives aux e-mails suspects**  
De nouvelles stratégies de détection des anomalies ont été ajoutées pour détecter les règles de transfert des e-mails suspects, par exemple, si un utilisateur a créé une règle de boîte de réception assurant le transfert d’une copie de tous les e-mails à une adresse externe.

- Cette version comprend des correctifs et des améliorations visant plusieurs problèmes.

### <a name="cloud-app-security-release-128"></a>Cloud App Security version 128

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
Une nouvelle requête est suggérée pour vous permettre d’identifier les applications découvertes qui sont prêtes pour le RGPD. Étant donné que le RGPD est récemment devenu une priorité absolue pour les administrateurs de la sécurité, cette requête vous permet d’identifier facilement les applications conformes au RGPD et d’atténuer les menaces en évaluant le risque de celles qui ne le sont pas.

### <a name="cloud-app-security-release-127"></a>Cloud App Security version 127

Publication : 8 juillet 2018

- Vous pouvez désormais voir les activités génériques pour Office 365. Dans le **Journal d’activité** et dans les **Stratégies d’activité**, vous pouvez maintenant filtrer les activités Office 365 ayant pour état **Non spécifié**. L’examen de ces activités vous permet d’examiner des informations sur les activités qui ne sont pas encore classifiées par type dans Cloud App Security, et vous pouvez vous baser sur ces activités pour envoyer des demandes à l’équipe Cloud App Security afin de créer des types d’activités.

### <a name="cloud-app-security-release-126"></a>Cloud App Security version 126

Publication : 24 juin 2018

- **Contrôle d’application par accès conditionnel (en disponibilité générale)**  
Le contrôle d’application par accès conditionnel de Microsoft Cloud App Security (proxy inverse) est maintenant en disponibilité générale pour toutes les applications SAML. Il s’intègre directement à vos stratégies d’accès conditionnel Azure AD pour **contrôler et effectuer le monitoring des sessions de vos utilisateurs en temps réel** tout en leur permettant d’être productifs. Depuis le premier aperçu de la fonctionnalité, de nombreuses fonctionnalités et améliorations ont été mises en place, notamment les suivantes :
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

### <a name="cloud-app-security-release-125"></a>Cloud App Security version 125

Publication : 10 juin 2018

- **Nouvelle fonctionnalité d’investigation pour les principaux utilisateurs :**  
Microsoft Cloud App Security a ajouté un nouveau widget d’investigation au tableau de bord qui affiche les principaux utilisateurs par nombre d’alertes de détection de menaces en attente. Ce widget d’investigation vous permet de concentrer vos investigations relatives aux menaces sur les utilisateurs ayant le plus grand nombre de sessions suspectes.

- **Prise en charge des compartiments AWS S3 :**  
Microsoft Cloud App Security peut désormais détecter les compartiments AWS S3 et leurs niveaux de partage. Cela fournit des alertes et une visibilité des compartiments AWS accessibles publiquement. Cela vous permet également de créer des stratégies basées sur des compartiments et d’appliquer la gouvernance automatique. Par ailleurs, un nouveau modèle de stratégie appelé **Compartiments S3 accessibles publiquement (AWS)** est disponible. Vous pouvez l’utiliser pour créer facilement une stratégie de gouvernance pour votre stockage AWS. Pour activer ces nouvelles fonctionnalités, veillez à mettre à jour vos applications connectées à AWS en ajoutant les nouvelles autorisations décrites dans [Connexion à AWS](connect-aws-to-microsoft-cloud-app-security.md).

- **Privilèges d’administrateur basés sur des groupes d’utilisateurs** :  
Vous pouvez maintenant définir des autorisations d’administration pour les administrateurs Microsoft Cloud App Security par groupe d’utilisateurs. Par exemple, vous pouvez définir un utilisateur spécifique comme administrateur pour les seuls utilisateurs en Allemagne. Il peut ainsi afficher et modifier des informations dans Microsoft Cloud App Security uniquement pour le groupe d’utilisateurs « Allemagne – Tous les utilisateurs ». Pour plus d’informations, consultez [Gestion de l’accès administrateur](manage-admins.md).

### <a name="cloud-app-security-release-124"></a>Cloud App Security version 124

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
  - Conformité : si vos réglementations de conformité vous imposent de ne pas surveiller les utilisateurs de certains pays ou certaines régions en raison des réglementations locales.
  - Gestion des licences : si vous souhaitez surveiller moins d’utilisateurs pour rester dans les limites de vos licences Microsoft Cloud App Security.
  Pour plus d'informations, consultez [Déploiement étendu](scoped-deployment.md).

- **Alerte d’application transgressée pour les applications découvertes**  
 Il existe maintenant une alerte intégrée qui vous avertit lorsque l’une des applications découvertes d’un locataire est compromise. L’alerte fournit des informations sur l’heure et la date de la violation, les utilisateurs qui ont utilisé l’application et les liens vers les sources disponibles publiquement qui donnent des informations sur la violation.

- **Nouveau serveur de messagerie**  
 Le serveur de courrier de Cloud App Security a changé et utilise d’autres plages d’adresses IP. Pour être sûr de recevoir des notifications, ajoutez les nouvelles adresses IP à votre liste verte anti-courrier indésirable. Microsoft Cloud App Security permet aux utilisateurs de personnaliser leurs notifications avec MailChimp&reg;, un service d’hébergement de courrier tiers. Pour obtenir la liste des adresses IP du serveur de messagerie ainsi que des instructions sur l’activation de l’utilisation de MailChimp, consultez [Configuration réseau requise](network-requirements.md#mail-server) et [Paramètres de messagerie](mail-settings.md).

### <a name="cloud-app-security-release-123"></a>Cloud App Security version 123

Publication : 13 mai 2018

- **Étendue de la stratégie de détection des anomalies** :  
les stratégies de détection des anomalies peuvent désormais être étendues. Cela vous permet de définir chaque stratégie de détection d’anomalie pour inclure uniquement des utilisateurs ou des groupes spécifiques et exclure des utilisateurs ou des groupes spécifiques. Par exemple, sous Activité, vous pouvez définir la détection d’une région rare ou ignorer un utilisateur spécifique qui voyage fréquemment.

### <a name="cloud-app-security-release-122"></a>Cloud App Security version 122

Publication : 29 avril 2018

- Déploiement progressif : Vous pouvez maintenant **définir des autorisations d’administration pour les administrateurs Microsoft Cloud App Security par application**. Par exemple, vous pouvez définir un utilisateur spécifique comme administrateur pour G Suite seulement. L’utilisateur peut ainsi afficher et modifier des informations dans Microsoft Cloud App Security uniquement pour G Suite. Pour plus d’informations, consultez [Gestion de l’accès administrateur](manage-admins.md).

- Déploiement progressif : **Les rôles d’administrateur Okta sont désormais visibles** dans Microsoft Cloud App Security et disponibles pour chaque rôle sous la forme d’une balise sous **Paramètres** > **Groupes d’utilisateurs**.

### <a name="cloud-app-security-release-121"></a>Cloud App Security version 121

Publication : 22 avril 2018

- La préversion publique du **contrôle d’application par accès conditionnel (anciennement appelé proxy Cloud App Security)** a été améliorée grâce à des fonctionnalités qui offrent une meilleure visibilité et permettent de contrôler diverses applications. Vous pouvez maintenant créer une stratégie de session avec un filtre *Type d’activité* pour surveiller et bloquer une variété d’activités spécifiques à l’application. Ce nouveau filtre augmente les fonctionnalités existantes de contrôle de téléchargement de fichiers, pour un contrôle complet des applications de votre organisation. Il fonctionne conjointement avec l’accès conditionnel Azure Active Directory pour offrir une visibilité en temps réel et contrôler les sessions des utilisateurs à risque. Il peut s’agir de sessions avec des utilisateurs entretenant une collaboration B2B ou des utilisateurs dont l’appareil est non géré. Pour plus d’informations, consultez [Stratégies de session](session-policy-aad.md).

- Déploiement progressif : Concernant Cloud App Security, les **stratégies de détection d’anomalies ont été améliorées** pour inclure deux nouveaux types de détection des menaces : Activité de ransomware et activité d’utilisateurs supprimés. Cloud App Security a étendu ses fonctionnalités de détection de ransomware à la détection d’anomalies pour garantir une couverture plus complète contre les attaques par ransomware sophistiqué. Grâce à notre expertise en matière de recherche sur la sécurité pour identifier des modèles de comportement qui reflètent l’activité des ransomware, Cloud App Security garantit une protection holistique et robuste. L’activité des utilisateurs supprimés vous permet de surveiller les comptes des utilisateurs supprimés, qui ont peut-être été désapprovisionnés à partir d’applications d’entreprise, mais ont souvent toujours accès à certaines ressources d’entreprise. Pour plus d’informations, consultez [Obtenir instantanément des analyses comportementales et une détection d’anomalies](anomaly-detection-policy.md).

### <a name="cloud-app-security-release-120"></a>Cloud App Security version 120

Publication : 8 avril 2018

- Pour Office 365 et Azure AD, nous mettons maintenant progressivement en place la possibilité de détecter des applications internes en tant qu’activités comptes utilisateurs effectuées par les applications Office 365 et Azure AD (internes et externes). Ceci vous permet de créer des stratégies qui vous alerteront si une application a des activités inattendues et non autorisées.

- Lors de l’exportation d’une liste de permissions d'applications au format CSV, des champs supplémentaires tels que l’éditeur, le niveau d’autorisation et l’utilisation de la communauté sont inclus pour faciliter le processus de conformité et d’investigation.

- L’application connectée ServiceNow a été améliorée de sorte que les activités de service internes ne s’inscrivent plus comme ayant été effectuées par « Invité » et ne déclenchent plus d’alertes de faux positifs. Ces activités sont maintenant représentées en tant que N/A, comme toutes les autres applications connectées.

### <a name="cloud-app-security-release-119"></a>Cloud App Security version 119

Date de publication : 18 mars 2018

- La page des plages d’adresses IP contient des adresses IP intégrées qui sont découvertes par Cloud App Security. Ceci inclut des adresses IP des services cloud identifiés, tels qu’Azure et Office 365, ainsi que le flux de renseignements sur les menaces qui enrichit automatiquement les adresses IP avec des informations sur les adresses IP à risque connues.

- Lorsque Cloud App Security tente d’exécuter une action de gouvernance sur un fichier, mais échoue parce que le fichier est verrouillé, il fait automatiquement une nouvelle tentative.

### <a name="cloud-app-security-release-118"></a>Cloud App Security version 118

Publication : 4 mars 2018

- Vous pouvez maintenant tirer parti des fonctionnalités de monitoring et de découverte de l’informatique fantôme de Microsoft Cloud App Security pour vos propres applications personnalisées privées. La nouvelle possibilité d’ajouter des applications personnalisées à Cloud Discovery vous permet de surveiller l’utilisation des applications et de recevoir des alertes si des modifications sont apportées au modèle d’utilisation. Pour plus d’informations, consultez [Protection de vos applications personnalisées](cloud-discovery-custom-apps.md). Cette fonctionnalité est déployée progressivement.

- Les pages **Paramètres** du portail Cloud App Security ont été remaniées. La nouvelle conception améliorée consolide toutes les pages de paramètres et fournit des fonctionnalités de recherche.

- Cloud Discovery prend désormais en charge les pare-feu de série F Barracuda et la diffusion en continu des journaux de la série F.

- La fonctionnalité de recherche des pages Utilisateur et Adresses IP permet maintenant l’autocomplétion, ce qui vous aide à trouver ce que vous cherchez.

- Vous pouvez maintenant effectuer des actions en bloc dans les pages de paramètres Exclure des entités et Exclure une adresse IP. Cela vous permet de sélectionner facilement plusieurs utilisateurs ou adresses IP, et de les exclure de la supervision Cloud Discovery de votre organisation.

### <a name="cloud-app-security-release-117"></a>Cloud App Security version 117

Date de publication : 20 février 2018

- L’intégration plus poussée de Cloud App Security avec Azure Information Protection vous permet désormais de protéger les fichiers dans G Suite. Cette fonctionnalité en préversion publique vous permet d’analyser et de classifier des fichiers dans G Suite, et d’appliquer automatiquement des étiquettes Azure Information Protection pour la protection. Pour plus d’informations, consultez [Intégration d’Azure Information Protection](azip-integration.md).

- Cloud Discovery prend désormais en charge [Digital Arts i-FILTER](https://www.daj.jp/en/products/if/).

- Le tableau des agents SIEM fournit désormais plus de détails pour faciliter la gestion.

### <a name="cloud-app-security-release-116"></a>Cloud App Security version 116

Date de publication : 4 février 2018

- La stratégie de détection d’anomalies de Cloud App Security a été améliorée grâce à de nouvelles **détections basées sur des scénarios**, notamment un voyage impossible, une activité à partir d’une adresse IP suspecte et plusieurs échecs de tentatives de connexion. Les nouvelles stratégies sont automatiquement activées, fournissant une détection des menaces prête à l’emploi dans votre environnement cloud. De plus, les nouvelles stratégies exposent davantage de données à partir du moteur de détection Cloud App Security pour vous aider à accélérer le processus d’investigation et à contenir des menaces continues. Pour plus d’informations, consultez [Obtenir instantanément des analyses comportementales et une détection d’anomalies](anomaly-detection-policy.md).

- Déploiement progressif : Cloud App Security met désormais en corrélation les utilisateurs et leurs comptes dans les applications SaaS. Vous pouvez ainsi examiner facilement toutes les activités d’un utilisateur dans toutes ses applications SaaS corrélées, quels que soient l’application ou le compte utilisés.

- Déploiement progressif : Cloud App Security prend désormais en charge plusieurs instances de la même application connectée. Si vous avez plusieurs instances, par exemple de Salesforce (une pour les ventes, une pour le marketing), vous pourrez les connecter à Cloud App Security et les gérer à partir de la même console pour créer des stratégies granulaires et des investigations plus approfondies.

- Les analyseurs Cloud Discovery prennent désormais en charge deux formats de point de contrôle supplémentaires, à savoir XML et KPC.

### <a name="cloud-app-security-release-115"></a>Cloud App Security version 115

Publication : 21 janvier 2018

- Cette version offre une expérience améliorée lors de la sélection de dossiers spécifiques dans les stratégies de fichiers. Vous pouvez désormais facilement afficher et sélectionner plusieurs dossiers à inclure dans une stratégie.
- Dans la page **Applications découvertes** :
  - La fonctionnalité de balisage en bloc vous permet d’appliquer des balises personnalisées (en plus des balises approuvées et non approuvées).
  - Lorsque vous **générez un rapport sur les adresses IP** ou que vous **générez un rapport sur les utilisateurs**, les rapports exportés incluent désormais les informations indiquant si le trafic provient d’applications approuvées ou non approuvées.
- Vous pouvez désormais demander un nouveau connecteur d’application API à l’équipe Microsoft Cloud App Security directement dans le portail, à la page **Connecter une application**.

### <a name="cloud-app-security-release-114"></a>Cloud App Security version 114

Publication : 7 janvier 2018

- Depuis la version 114, nous déployons progressivement la possibilité de créer et d’enregistrer des requêtes personnalisées dans les pages Journal d’activité et Applications découvertes. Les requêtes personnalisées vous permettent de créer des modèles de filtres pouvant être réutilisés pour une investigation approfondie. De plus, les **Requêtes suggérées** ont été ajoutées pour fournir des modèles d’investigation prêts à l’emploi avec lesquels vous pourrez filtrer vos activités et vos applications découvertes. Les **requêtes suggérées** incluent des filtres personnalisés pour identifier les risques tels que les activités d’usurpation d’identité, les activités d’administrateurs, les applications de stockage cloud non conformes à risque, les applications d’entreprise avec un chiffrement faible et les risques de sécurité. Vous pouvez utiliser les **requêtes suggérées** comme point de départ, les modifier comme bon vous semble, puis les enregistrer en tant que nouvelle requête. Pour plus d’informations, consultez [Filtres d’activité et requêtes](activity-filters-queries.md) ainsi que [Filtres et requêtes d’applications découverts](discovered-app-queries.md).

- Vous pouvez maintenant vérifier l’état actuel du service Cloud App Security en accédant à [status.cloudappsecurity.com](https://status.cloudappsecurity.com) ou directement à partir du portail en cliquant sur **Aide**>**État du système**.

## <a name="updates-made-in-2017"></a>Mises à jour effectuées en 2017

### <a name="cloud-app-security-release-113"></a>Cloud App Security version 113

Publiée le 25 décembre 2017

- Nous sommes heureux d’annoncer que Cloud App Security prend désormais en charge une intégration plus poussée avec Azure Information Protection. Cette fonctionnalité en préversion publique vous permet d’analyser et de classifier des fichiers dans les applications cloud, et d’appliquer automatiquement des étiquettes Azure Information Protection pour la protection. Cette fonctionnalité est disponible pour Box, SharePoint et OneDrive. Pour plus d’informations, consultez [Intégration d’Azure Information Protection](azip-integration.md).

- Les analyseurs de journaux Cloud Discovery prennent désormais en charge les formats génériques LEEF, CEF et W3C.

### <a name="cloud-app-security-release-112"></a>Cloud App Security version 112

Publication le 10 décembre 2017

- Vous pouvez désormais accéder au tiroir d’insight pertinent en cliquant sur un nom d’utilisateur ou une adresse IP Dans le journal des activités.
- Quand vous examinez des activités, vous pouvez désormais afficher facilement toutes les activités durant la même période à partir du tiroir d’insights en cliquant sur l’icône d’horloge. Cette icône vous permet d’afficher toutes les activités effectuées dans les 48 heures de l’activité actuellement affichée.
- Des améliorations ont été apportées à l’analyseur de journal Cloud Discovery pour Juniper SRX.
- Pour les activités surveillées par le proxy, **l’objet Activité** a été étendu de façon à inclure des informations concernant les analyses DLP. Les stratégies correspondantes ont été étendues de façon à inclure les violations DLP si elles existent.

### <a name="cloud-app-security-release-111"></a>Cloud App Security version 111

Publiée le 26 novembre 2017

- Les stratégies de découverte prennent désormais en charge les balises d’application en tant que condition et en tant qu’action de gouvernance. Cet ajout vous permet d’étiqueter automatiquement les applications nouvellement découvertes avec des étiquettes personnalisées comme **Applications tendancielles**. Vous pouvez également utiliser l’étiquette d’application comme filtre. Par exemple, « m’avertir quand une application dans le «Watchlist » a plus de 100 utilisateurs en une seule journée».

- Le filtre **Heure** a été amélioré pour le rendre plus convivial.

- L’inspection de contenu vous permet désormais de faire la distinction entre le contenu, les métadonnées et le nom de fichier, pour vous permettre de sélectionner l’élément à inspecter.

- Une nouvelle action de gouvernance a été ajoutée pour G Suite. Vous pouvez désormais **Réduire l’accès public** aux fichiers partagés. Cette action vous permet de définir les fichiers disponibles publiquement comme étant accessibles uniquement avec un lien partagé.

- Toutes les activités de connexion OKTA à d’autres applications s’affichent désormais dans Cloud App Security comme provenant d’OKTA. Vous pouvez afficher et filtrer en fonction de l’application cible dans laquelle la connexion a été effectuée dans le champ **objets d’activité** de l’activité.

### <a name="cloud-app-security-release-110"></a>Cloud App Security version 110

Publiée le 12 novembre 2017

- Désormais en disponibilité générale : nous avons commencé à développer un nouveau mode de déploiement pour le collecteur de journaux. En plus du déploiement actuel par appliance virtuelle, le nouveau collecteur de journaux, sur (conteneur) Docker, peut être installé sous forme de package sur les [machines Ubuntu](discovery-docker.md), à la fois en local et dans Azure. Quand vous utilisez le collecteur Docker, l’ordinateur hôte est détenu par le client, qui peut librement le corriger et le surveiller.

- Grâce au nouveau point d’interrogation bleu dans l’angle, vous avez maintenant accès à la page de documentation Cloud App Security correspondante sur docs.microsoft.com, sur les pages du portail. Chaque lien est sensible au contexte et vous permet d’accéder aux informations dont vous avez besoin en fonction de la page sur laquelle vous vous connectez.
- Vous pouvez maintenant envoyer des commentaires sur chaque page du portail Cloud App Security. Le feedback vous permet de signaler des bogues, de demander de nouvelles fonctionnalités et de partager votre expérience directement avec l’équipe Cloud App Security.
- Des améliorations ont été apportées à la capacité Cloud Discovery à reconnaître des sous-domaines pour des investigations approfondies dans l’utilisation du Cloud de votre organisation. Pour plus d’informations, consultez la page [Utiliser les applications découvertes](discovered-apps.md).

### <a name="cloud-app-security-release-109"></a>Cloud App Security version 109

Publication : 29 octobre 2017

- Le lancement de la fonctionnalité de proxy Microsoft Cloud App Security est en cours. Le proxy Microsoft Cloud App Security vous fournit les outils dont vous avez besoin pour obtenir une visibilité et un contrôle en temps réel de l’accès à votre environnement cloud et des activités qui y sont effectuées. Par exemple :

  - Évitez les fuites de données en bloquant les téléchargements avant qu’ils ne se produisent.
  - Définissez des règles qui forcent le chiffrement des données stockées dans le cloud et téléchargées à partir du cloud.
  - Obtenez une visibilité sur les points de terminaison non protégés afin de surveiller les opérations réalisées sur les appareils non gérés.
  - Contrôlez l’accès depuis des réseaux hors entreprise ou des adresses IP à risque.

  Pour plus d’informations, consultez [Protéger les applications avec le Contrôle d’accès conditionnel aux applications](proxy-intro-aad.md).

- Nous lançons progressivement la possibilité de filtrer en fonction de noms d’activité de service spécifiques. Ce nouveau filtre de type d’activité est plus précis pour vous permettre de surveiller des activités d’application spécifiques, plutôt que des types d’activité plus généraux. Par exemple, vous pouviez filtrer la commande **Exécuter**, mais maintenant, vous pouvez aussi filtrer des applets de commande EXO spécifiques. Le nom de l’activité peut également être vu dans le tiroir Activité sous **Type (dans l’application)**. À terme, cette fonctionnalité va remplacer le filtre de type d’activité.

- Cloud Discovery prend désormais en charge Cisco ASA avec FirePOWER.

- Des améliorations des performances ont été apportées aux pages des utilisateurs et adresses IP de Cloud Discovery afin d’améliorer l’expérience utilisateur.

### <a name="cloud-app-security-releases-105-106-107-108"></a>Cloud App Security versions 105, 106, 107, 108

Publication : septembre/octobre 2017

- Cloud App Security compte désormais un centre de données situé dans l’Union européenne. En complément de notre centre de données aux États-Unis, le centre de données de l’Union européenne permettra aux clients Cloud App Security de se mettre en totale conformité avec les certifications et normes européennes nouvelles et à venir.
- De nouveaux filtres ont été ajoutés à la page **Connecteurs d’application** qui vous propose un filtrage plus simple et d’autres informations.
- La découverte cloud sur les fichiers journaux qui contiennent seulement des informations sur les adresses IP de destination a été améliorée.

### <a name="cloud-app-security-release-104"></a>Cloud App Security version 104

Publication : 27 août 2017

- Vous pouvez désormais ajouter des plages d’adresses IP en bloc en créant un script à l’aide de l’**API des plages d’adresses IP**. Vous trouverez l’API dans la barre de menus du portail Cloud App Security en cliquant sur le point d’interrogation, puis sur **Documentation sur les API**.
- Cloud Discovery fournit une meilleure visibilité des transactions bloquées en présentant à la fois la totalité des transactions et les transactions bloquées.
- Vous pouvez désormais filtrer les applications cloud selon qu’elles sont ou non certifiées **ISO 27017**. Ce nouveau facteur de risque du catalogue d’applications cloud détermine si le fournisseur de l’application a cette certification. ISO 27017 établit des contrôles et des consignes communément admis pour traiter et protéger les informations utilisateur dans un environnement de cloud computing public.
- Pour vous aider à vous préparer à la mise en conformité au RGPD, nous avons rassemblé les déclarations associées à partir des applications cloud du catalogue. Il n’affecte pas encore le score de risque de l’application, mais fournit un lien vers la page de préparation RGPD de l’éditeur d’applications, lorsqu’il est fourni. Microsoft n’a pas vérifié ce contenu et n’est pas responsable de sa validité.

### <a name="cloud-app-security-release-103"></a>Cloud App Security version 103

Publication : 13 août 2017

- Ajout dans Cloud App Security de la prise en charge de la protection native Azure Information Protection pour les fichiers Office suivants : .docm, .docx, .dotm, .dotx, .xlam, .xlsb, .xlsm, .xlsx, .xltx, .xps, .potm, .potx, .ppsx, .ppsm, .pptm, .pptx, .thmx, .vsdx, .vsdm, .vssx, .vssm, .vstx, .vstm (au lieu d’une protection générique).

- Tous les administrateurs de conformité Azure Active Directory reçoivent automatiquement des autorisations similaires dans Cloud App Security. Les autorisations incluent la possibilité de lecture seule et de gestion des alertes, la création et la modification des stratégies de fichiers, la possibilité d’autoriser des actions de gouvernance de fichiers et la visualisation de tous les rapports intégrés sous Gestion des données.

- Nous avons étendu le contexte de violation DLP de 40 à 100 caractères pour en améliorer la compréhension.

- Ajout de messages d’erreur détaillés au chargeur de journal personnalisé Cloud Discovery pour vous permettre de résoudre facilement les erreurs de chargement de journaux.

- Le script de bloc Cloud Discovery a été étendu pour prendre en charge le format Zscaler.

- Nouveau facteur de risque du catalogue d’applications cloud : rétention des données après l’arrêt du compte. Cela vous permet de vérifier que vos données sont totalement supprimées après l’arrêt d’un compte dans une application cloud.

### <a name="cloud-app-security-release-102"></a>Cloud App Security version 102

Publication : 30 juillet 2017

- Parce que les informations d’adresse IP sont essentielles pour la quasi-totalité des examens, vous pouvez maintenant afficher les informations détaillées des adresses IP dans le tiroir Activité. Depuis une activité spécifique, vous pouvez désormais cliquer sur l’onglet Adresse IP pour voir des données consolidées sur l’adresse IP. Les données incluent le nombre d’alertes ouvertes pour l’adresse IP spécifique, un graphique de tendance de l’activité récente et une carte des emplacements. Cette fonctionnalité permet une exploration détaillée facile. Par exemple, quand vous recherchez la cause d’alertes Voyage impossible, vous pouvez facilement déterminer où l’adresse IP a été utilisée, et si elle a été ou non impliquée dans des activités suspectes. Vous pouvez effectuer des actions directement dans le tiroir Adresse IP, où vous pouvez marquer une adresse IP comme étant risquée, VPN ou d’entreprise pour faciliter par la suite l’examen et la création de stratégie. Pour plus d’informations, consultez [IP address Insights](activity-filters.md#ip-address-insights) .

- Dans Cloud Discovery, vous pouvez désormais utiliser des [formats de fichiers journaux personnalisés](custom-log-parser.md) pour [le chargement automatique des journaux](discovery-docker.md). Ces formats de journaux personnalisés vous permettent d’automatiser facilement le chargement des journaux depuis vos serveurs SIEM (par exemple des serveurs Splunk) ou de tout autre format non pris en charge.

- Les nouvelles actions d’examen d’utilisateur donnent accès à un niveau supplémentaire d’exploration. Dans les pages **Examen**, vous pouvez désormais cliquer avec le bouton droit sur une activité, un utilisateur ou un compte, et appliquer un des nouveaux filtres pour un examen et un filtrage avancés : **Afficher les activités associées**, **Afficher la gouvernance relative**, **Afficher les alertes associées**, **Afficher les fichiers possédés**, **Afficher les fichiers partagés avec cet utilisateur**.

- Le catalogue d’applications cloud contient désormais un nouveau champ de rétention des données après l’arrêt du compte. Ce facteur de risque vous permet de vérifier que vos données sont totalement supprimées après l’arrêt d’un compte dans une application cloud.

- Cloud App Security permet désormais une visibilité améliorée des activités relatives aux objets Salesforce. Les objets incluent les prospects, les comptes, les campagnes, les opportunités, les profils et les incidents. Par exemple, la visibilité de l’accès aux pages de compte vous permet de configurer une stratégie qui vous alerte si un utilisateur affiche un nombre exceptionnellement élevé de pages de compte. Cette fonctionnalité est disponible dans le connecteur d’applications Salesforce, une fois que vous avez activé la surveillance des événements Salesforce dans Salesforce (intégrée à Salesforce Shield).

- La fonctionnalité Ne pas me suivre est désormais disponible pour les clients de la préversion limitée ! Vous pouvez maintenant contrôler les données d’activité des utilisateurs qui sont traitées. Cette fonctionnalité vous permet de définir des groupes spécifiques dans Cloud App Security en tant que « ne pas suivre ». Par exemple, vous pouvez désormais décidez de ne traiter aucune donnée d’activité pour les utilisateurs situés en Allemagne ou dans un pays non soumis à une loi de conformité spécifique. Cette fonctionnalité peut être implémentée pour toutes les applications dans Cloud App Security, pour une application spécifique ou même pour une sous-application spécifique. Par ailleurs, cette fonctionnalité peut être utilisée pour faciliter le déploiement progressif de Cloud App Security. Pour plus d’informations ou pour participer à la préversion limitée de cette fonctionnalité, contactez le support ou votre responsable de compte.

### <a name="cloud-app-security-release-100"></a>Cloud App Security version 100

Publication : 3 juillet 2017

**Nouvelles fonctionnalités**

- **Extensions de sécurité :** Extensions de sécurité est un nouveau tableau de bord pour la gestion centralisée de toutes les extensions de sécurité de Cloud App Security.  Les extensions incluent la gestion des jetons d’API, les agents SIEM et les connecteurs DLP externes. Le nouveau tableau de bord est disponible dans Cloud App Security sous « paramètres ».

  - Jetons d’API : Générez et gérez vos propres [Jetons d’API](api-tokens.md) pour intégrer Cloud App Security à des logiciels tiers à l’aide de nos API RESTful.
  - Agents SIEM : l' [intégration Siem](siem.md) était précédemment située directement sous « paramètres », maintenant disponible sous forme d’onglet dans extensions de sécurité.
  - DLP externe (préversion) : Cloud App Security vous permet de [tirer parti des investissements existants dans les systèmes de classification tiers](icap-stunnel.md), comme les solutions DLP (Data Loss Prevention), et vous permet d’analyser le contenu d’applications cloud à l’aide de déploiements existants en cours d’exécution dans votre environnement. Contactez votre responsable de compte pour participer à la préversion.

- **Automatiquement approuver/ne pas approuver :** Les nouvelles stratégies de détection d’application permettent à Cloud Discovery de définir automatiquement les applications avec l’étiquette Approuvée/Non approuvée. Cela vous donne la possibilité d’identifier automatiquement les applications qui sont en violation de la stratégie et des réglementations de votre organisation et de les ajouter au script de blocage généré.
- **Étiquettes de fichier Cloud App Security :** Vous pouvez maintenant appliquer des étiquettes de fichier Cloud App Security pour fournir davantage d’insights sur les fichiers analysés. Pour chaque fichier analysé par Cloud App Security DLP, vous pouvez maintenant savoir si les fichiers n’ont pas pu être inspectés parce qu’ils ont été chiffrés ou corrompus. Par exemple, vous pouvez configurer des stratégies pour vous alerter et mettre en quarantaine les fichiers protégés par mot de passe qui sont partagés en externe. Cette fonctionnalité est disponible pour les fichiers analysés après le 3 juillet 2017.

    Vous pouvez filtrer ces fichiers à l’aide des **étiquettes de classification** des filtres  >  **Cloud App Security**:

  - **Chiffré par Azure RMS** : les fichiers dont le contenu n’a pas été inspecté, car le chiffrement Azure RMS défini pour ceux-ci.
  - **Chiffrement de mot de passe** : les fichiers dont le contenu n’a pas été inspecté parce qu’ils sont protégés par un mot de passe par l’utilisateur.
  - **Fichier corrompu** : les fichiers dont le contenu n’a pas été inspecté, car il n’a pas pu être lu.

- **Insights utilisateur** : L’expérience d’investigation a été mise à niveau pour activer des insights prêts à l’emploi sur l’utilisateur responsable de l’action. En un seul clic, vous pouvez maintenant obtenir, dans le tiroir Activité, une vue d’ensemble complète des utilisateurs, notamment l’endroit à partir duquel ils sont connectés, le nombre d’alertes ouvertes dans lesquelles ils sont impliqués et leurs informations de métadonnées.
- **Insights des connecteurs d’applications :** sous **Connecteurs d’applications**, chaque application connectée inclut désormais un tiroir d’application dans le tableau, qui permet d’explorer plus facilement son état. Les détails fournis indiquent notamment la date de connexion du connecteur d’applications et le dernier contrôle d’intégrité du connecteur. Vous pouvez également surveiller l’état de l’analyse DLP sur chaque application : le nombre total de fichiers inspectés par DLP ainsi que l’état des analyses en temps réel (analyses demandées par rapport aux analyses réelles). Vous pouvez savoir si le taux de fichiers analysés par Cloud App Security en temps réel est inférieur au nombre demandé, et si votre locataire risque de dépasser sa capacité et d’obtenir les résultats DLP avec du retard.

- **Personnalisation du catalogue d’applications cloud :**

  - **Balises d’application** : Vous pouvez désormais créer des balises personnalisées pour les applications. Ces étiquettes peuvent ensuite servir de filtres pour rechercher plus précisément des types spécifiques d’applications que vous voulez examiner. Par exemple, une liste de suivi personnalisée, une attribution à une division spécifique ou des approbations personnalisées, telles que « approuvé par légal ».
  - **Notes personnalisées** : Quand vous passez en revue et évaluez les différentes applications qui ont été découvertes dans votre environnement, vous pouvez maintenant enregistrer votre conclusions et insights dans les Notes.
  - **Score de risque personnalisé** : Vous pouvez désormais remplacer le score de risque d’une application. Par exemple, si le score de risque d’une application est de 8 et qu’il s’agit d’une application approuvée dans votre organisation, vous pouvez changer ce score de risque en 10 pour votre organisation. Vous pouvez également ajouter des notes pour clarifier la justification du changement quand une personne examine l’application.

- **Nouveau mode de déploiement du collecteur de journaux :** nous commençons à lancer un nouveau mode de déploiement qui est désormais disponible pour le collecteur de journaux. En plus du déploiement actuel basé sur l’appliance virtuelle, le nouveau collecteur de journaux basé sur Docker (conteneur) peut être installé comme un package sur les ordinateurs Windows et Ubuntu à la fois localement et dans Azure. Quand vous utilisez le collecteur Docker, l’ordinateur hôte est détenu par le client, qui peut librement le corriger et le surveiller.

**Relatives**

- Le catalogue d’applications cloud prend désormais en charge plus de 15 000 applications détectables
- Conformité : Cloud App Security est officiellement certifié SOC1/2/3 par Azure. Pour obtenir la liste complète des certifications, consultez les [offres de conformité](https://www.microsoft.com/trustcenter/compliance/complianceofferings) et filtrez les résultats pour Cloud App Security.

**Autres améliorations :**

- **Amélioration de l’analyse :** Des améliorations ont été apportées au mécanisme d’analyse du journal Cloud Discovery. Les erreurs internes sont beaucoup moins susceptibles de se produire.
- **Formats de journaux attendus :** Le format de journal attendu pour les journaux Cloud Discovery fournit désormais des exemples pour les formats Syslog et FTP.
- **État de chargement du collecteur de journaux :** Vous pouvez maintenant afficher l’état du collecteur de journaux dans le portail et résoudre les problèmes plus rapidement à l’aide des notifications d’état du portail et des alertes système.

### <a name="cloud-app-security-release-99"></a>Cloud App Security version 99

Publication : 18 juin 2017

**Nouvelles fonctionnalités**

- Vous pouvez désormais demander aux utilisateurs de se reconnecter à toutes les applications Office 365 et Azure AD. Demandez cette reconnexion pour corriger de façon rapide et efficace les alertes d’activités suspectes des utilisateurs et les comptes compromis. La nouvelle gouvernance se trouve dans les paramètres de stratégie et les pages d’alerte, à côté de l’option Interrompre la synchronisation de l’utilisateur.
- Vous pouvez désormais rechercher les activités **Ajouter l’attribution de rôle d’emprunt d’identité** dans le journal d’activité. Cette activité vous permet de détecter quand un administrateur a accordé un rôle **Emprunt d’identité de l’application** à un utilisateur ou compte système, à l’aide de l’applet de commande **New-ManagementRoleAssignment**. Ce rôle permet à l’emprunteur d’effectuer des opérations à l’aide des autorisations associées au compte emprunté, au lieu des autorisations associées au compte de l’emprunteur.

**Améliorations de Cloud Discovery :**

- Les données Cloud Discovery peuvent maintenant être enrichies avec des données de nom d’utilisateur Azure Active Directory. Quand vous activez cette fonctionnalité, le nom d’utilisateur reçu dans les journaux de trafic de découverte est mis en correspondance et remplacé par le nom d’utilisateur Azure AD. Ces améliorations permettent les nouvelles fonctionnalités suivantes :
  - Vous pouvez examiner l’utilisation de l’informatique fantôme par l’utilisateur Azure Active Directory.
  - Vous pouvez mettre en corrélation l’utilisation de l’application cloud découverte avec les activités collectées par l’API.
  - Vous pouvez ensuite créer des journaux personnalisés basés sur des groupes d’utilisateurs Azure AD. Par exemple, un rapport d’informatique fantôme pour un service marketing spécifique.
- Améliorations apportées à l’analyseur de syslog Juniper. Il prend désormais en charge les formats welf et sd-syslog.
- Améliorations apportées à l’analyseur Palo Alto pour une meilleure découverte des applications.
- Pour vérifier que les journaux sont chargés correctement, vous pouvez maintenant afficher l’état de vos collecteurs de journaux dans le portail Cloud App Security.

**Améliorations générales :**

- Les balises d’adresse IP intégrées et les balises d’adresse IP personnalisées sont désormais considérées de manière hiérarchique, les balises d’adresse IP personnalisées étant prioritaires sur les balises d’adresse IP intégrées. Par exemple, si une adresse IP est marquée comme étant **Risquée** en fonction de l’intelligence des menaces, mais qu’il existe une étiquette d’adresse IP personnalisée qui l’identifie comme étant **Entreprise**, la catégorie et les étiquettes personnalisées sont prioritaires.

### <a name="cloud-app-security-release-98"></a>Cloud App Security version 98

Publication : 4 juin 2017

**Mises à jour de Cloud Discovery :**

- Les utilisateurs peuvent désormais effectuer un filtrage avancé sur les applications découvertes. Le filtrage vous permet d’effectuer des examens approfondis. C’est le cas par exemple du filtrage basé sur l’utilisation des applications. Quelle est la quantité de trafic de chargement provenant d’applications découvertes de certains types ? Combien d’utilisateurs ont utilisé certaines catégories d’applications découvertes ? Vous pouvez également effectuer plusieurs sélections dans le volet gauche pour sélectionner plusieurs catégories.
- Lancement de nouveaux modèles pour Cloud Discovery basés sur les recherches fréquentes, comme « application de stockage cloud non conforme ». Ces filtres de base peuvent être utilisés comme modèles pour effectuer une analyse sur vos applications découvertes.
- Pour faciliter l’utilisation, vous pouvez désormais effectuer des actions, comme approuver et ne pas approuver plusieurs applications, en une seule action.
- Nous déployons maintenant la possibilité de créer des rapports de découverte personnalisés basés sur les groupes d’utilisateurs Azure Active Directory. Par exemple, si vous voulez voir l’utilisation cloud de votre service marketing, vous pouvez importer le groupe marketing avec la fonctionnalité d’importation des groupes d’utilisateurs, puis créer un rapport personnalisé pour ce groupe.

**Nouvelles fonctionnalités :**

- Déploiement terminé du RBAC pour les lecteurs de sécurité. Cette fonctionnalité vous permet de gérer les autorisations que vous accordez à vos administrateurs à l’intérieur de la console Cloud App Security. Par défaut, tous les administrateurs Azure Active Directory, les administrateurs généraux Office 365 et les administrateurs de sécurité disposent des autorisations complètes dans le portail. Tous les lecteurs Sécurité dans Azure Active Directory et Office 365 ont un accès en lecture seule dans Cloud App Security. Vous pouvez ajouter des administrateurs ou remplacer des autorisations à l’aide de l’option « gérer l’accès ». Pour plus d’informations, consultez [gestion des autorisations d’administrateur](manage-admins.md).
- Nous déployons maintenant des rapports détaillés d’intelligence des menaces pour les adresses IP à risque détectées par Microsoft Intelligent Security Graph. Quand une activité est effectuée par un botnet, vous voyez le nom du botnet (s’il est disponible) avec un lien vers un rapport détaillé sur ce botnet.

### <a name="cloud-app-security-release-97"></a>Cloud App Security version 97

Publication : 24 mai 2017

**Nouvelles fonctionnalités :**

- Examen des fichiers et des violations de stratégie : Vous pouvez maintenant consulter toutes les correspondances de stratégie dans la page Fichiers. En outre, la page Alerte de fichier a été améliorée et inclut désormais un onglet distinct pour l’historique du fichier concerné. L’amélioration vous permet d’explorer l’historique des violations de toutes les stratégies pour ce fichier spécifique. Chaque événement d’historique inclut une capture instantanée du fichier au moment de l’alerte. Il est indiqué si le fichier a été supprimé ou mis en quarantaine.
- L’option [Mise en quarantaine administrateur](use-case-admin-quarantine.md) est désormais disponible en préversion privée pour les fichiers Office 365 SharePoint et OneDrive Entreprise. Cette fonctionnalité vous permet de mettre en quarantaine les fichiers qui correspondent à des stratégies ou de définir une action automatique pour les mettre en quarantaine. La mise en quarantaine supprime les fichiers du répertoire SharePoint de l’utilisateur et copie les originaux à l’emplacement de mise en quarantaine administrateur de votre choix.

**Améliorations de la Cloud Discovery :**

- La prise en charge des journaux Cisco Meraki dans Cloud Discovery a été améliorée.
- L’option permettant de suggérer une amélioration de Cloud Discovery vous permet désormais de suggérer un nouveau facteur de risque.
- L’analyseur de journal personnalisé a été amélioré pour prendre en charge les formats de journaux en séparant le paramètre de date et d’heure et en vous donnant la possibilité de définir l’horodatage.
- Nous commençons à déployer la possibilité de créer des rapports de découverte personnalisés basés sur les groupes d’utilisateurs Azure Active Directory. Par exemple, si vous voulez voir l’utilisation cloud de votre département marketing, importez le groupe Marketing avec la fonctionnalité d’importation des groupes d’utilisateurs, puis créez un rapport personnalisé pour ce groupe.

**Autres mises à jour :**

- Cloud App Security prend maintenant en charge les activités Microsoft Power BI qui sont prises en charge dans le journal d’audit d’Office 365. Cette fonctionnalité est déployée progressivement. Vous devez activer [cette fonctionnalité dans le portail Power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-auditing/).
- Dans les stratégies d’activité, vous pouvez maintenant définir des actions de notification et de suspension concernant l’utilisateur dans toutes les applications connectées. Par exemple, vous pouvez définir une stratégie pour toujours informer le responsable de l’utilisateur et suspendre immédiatement l’utilisateur quand il accumule plusieurs échecs de connexion dans n’importe quelle application connectée.

### <a name="oob-release"></a>Version OOB

- Pour réagir rapidement au ransomware qui a parcouru le monde, ce dimanche, l’équipe Cloud App Security a ajouté un nouveau modèle de [stratégie de détection d’activité de ransomware potentielle](use-case-ransomware.md) dans le portail qui inclut l’extension de signature de WannaCrypt. Nous vous recommandons de définir cette stratégie aujourd'hui.

### <a name="cloud-app-security-release-96"></a>Cloud App Security version 96

Publication : 8 mai 2017

**Nouvelles fonctionnalités :**

- Poursuite du lancement progressif de l’autorisation Lecteur Sécurité, qui vous permet de gérer les autorisations que vous accordez à vos administrateurs dans la console Cloud App Security. Par défaut, tous les administrateurs généraux Azure Active Directory et Office 365, et les administrateurs de sécurité, disposent des autorisations complètes dans le portail. Tous les lecteurs Sécurité dans Azure Active Directory et Office 365 ont un accès en lecture seule dans Cloud App Security. Pour plus d’informations, consultez [gestion des autorisations d’administrateur](manage-admins.md).
- Lancement terminé de la prise en charge de Cloud Discovery pour les analyseurs de journaux définis par l’utilisateur pour les journaux CSV. Cloud App Security propose des outils de délimitation pour mettre en corrélation les colonnes à des données spécifiques, ce qui vous permet de configurer un analyseur pour vos appareils précédemment non pris en charge. Pour plus d’informations, consultez [Analyseur de journal personnalisé](custom-log-parser.md).

**Améliorations :**

- Cloud Discovery prend désormais en charge les appareils Juniper SSG.
- Amélioration de la prise en charge de des journaux Cisco ASA dans Cloud Discovery pour une meilleure visibilité.
- Agrandissement de la page pour faciliter l’exécution des actions en bloc et la sélection de plusieurs enregistrements dans les tables du portail Cloud App Security.
- Vous pouvez désormais exécuter les rapports intégrés **Partage sortant par domaine** et **Propriétaires de fichiers partagés** pour les données Salesforce.
- Nous commençons à lancer d’autres activités Salesforce pour vous permettre de suivre les informations pertinentes extraites des données des activités. Ces activités comprennent l’affichage et la modification des comptes, des prospects, des opportunités et d’autres objets Salesforce intéressants.
- De nouvelles activités Exchange ont été ajoutées pour vous permettre de surveiller les autorisations accordées pour les boîtes aux lettres d’utilisateurs ou les dossiers de boîtes aux lettres. Parmi ces activités, citons les suivantes :
  - Ajouter des autorisations à des destinataires
  - Supprimer les autorisations de destinataires
  - Ajouter des autorisations à des dossiers de boîtes aux lettres
  - Supprimer les autorisations de dossiers de boîtes aux lettres
  - Définir des autorisations pour des dossiers de boîtes aux lettres

   Par exemple, vous pouvez désormais surveiller les utilisateurs qui disposent d’autorisations **SendAs** sur les boîtes aux lettres d’autres utilisateurs. par conséquent, ils peuvent désormais envoyer des courriers électroniques dans leur nom.

### <a name="cloud-app-security-release-95"></a>Cloud App Security version 95

Publication : 24 avril 2017

**Mises à jour**

- La page **Comptes** a été mise à jour avec des améliorations qui simplifient la détection des risques. Vous pouvez désormais filtrer plus facilement pour les comptes internes et externes. Voyez en un coup d’œil si un utilisateur dispose des autorisations d’administrateur. Vous pouvez effectuer des actions sur chaque compte par application, par exemple supprimer les autorisations, supprimer les collaborations de l’utilisateur, suspendre l’utilisateur. En outre, les [groupes d’utilisateurs](user-groups.md) importés pour chaque compte sont affichés.

- Pour les comptes professionnels Microsoft (Office 365 et Azure Active Directory), Cloud App Security regroupe différents identificateurs d’utilisateurs, comme des adresses de proxy, des alias, des SID et d’autres informations sous un même compte. Tous les alias associés à un compte s’affichent sous l’adresse e-mail principale. Selon la liste des identificateurs d’utilisateurs, pour les activités dont l’acteur est un identificateur d’utilisateur, l’acteur s’affiche sous le nom d’utilisateur principal (UPN, User Principal Name). En fonction de l’UPN, les groupes sont affectés et les stratégies appliquées. Cette modification améliore l’examen des activités et réunit toutes les activités associées dans la même session pour les anomalies et les stratégies basées sur des groupes. Cette fonctionnalité sera progressivement déployée au cours du mois suivant.

- La balise Robot a été ajoutée comme un facteur de risque possible dans le rapport intégré Utilisation du navigateur. Maintenant, en plus de l’utilisation du navigateur marquée comme obsolète, vous pouvez voir quand cette utilisation a été effectuée par un robot.
- Quand vous créez une stratégie de fichier d’inspection du contenu, vous pouvez maintenant définir le filtre pour inclure uniquement les fichiers avec au moins 50 correspondances.

### <a name="cloud-app-security-release-94"></a>Cloud App Security version 94

Publication : 2 avril 2017

**Nouvelles fonctionnalités :**

- Cloud App Security est maintenant intégré à Azure RMS. Vous pouvez protéger vos fichiers dans Office 365 OneDrive et Sharepoint Online avec Microsoft Rights Management, directement à partir du portail Cloud App Security. Vous pouvez activer cette protection dans la page **Fichiers**. Pour plus d’informations, consultez [intégration avec Azure information protection](azip-integration.md). La prise en charge d’applications supplémentaires sera proposée dans les prochaines versions.
- Jusqu’à présent, lorsqu’un robot ou un robot d’indexation intervenait sur votre réseau, il était tout particulièrement difficile à identifier. En effet, ces activités ne sont pas effectuées par un utilisateur. Ces robots peuvent exécuter des outils malveillants à votre insu sur les ordinateurs. Mais c’est sans compter Cloud App Security qui vous offre les outils nécessaires pour visualiser l’intervention de ces robots sur votre réseau. Vous pouvez utiliser la nouvelle balise de l’agent utilisateur pour filtrer les activités dans le journal d’activité. La balise de l’agent utilisateur vous permet de filtrer toutes les activités effectuées par les robots. Vous pouvez l’utiliser pour créer une stratégie qui vous alerte à chaque fois que ce type d’activité est détecté. Vous serez informé quand les prochaines versions intégreront cette activité à risque via les alertes de détection d’anomalies.
- La nouvelle page unifiée des autorisations d’applications vous permet d’examiner plus facilement les autorisations que vos utilisateurs ont accordées à des applications tierces. En cliquant sur **examiner**  >  les autorisations de l'**application**, vous pouvez désormais afficher une liste de toutes les autorisations que vos utilisateurs ont accordées à des applications tierces. Une page des autorisations d’application par application connectée vous permet de mieux comparer les différentes applications et les autorisations accordées. Pour plus d’informations, voir [Gérer les autorisations d’applications](manage-app-permissions.md).
- Pour faciliter les recherches, vous pouvez filtrer les données directement depuis le tiroir de table.
Dans **Journal d’activité**, les pages **Fichiers** et **Autorisations d’applications** sont maintenant étoffées avec de nouvelles actions contextuelles qui facilitent le processus de recherche. Nous avons également ajouté des liens rapides vers les pages de configuration et nous permettons de copier les données d’un seul clic. Pour plus d’informations, consultez les informations relatives à [l’utilisation des tiroirs de fichier et d’activité](file-filters.md).
- La prise en charge par Microsoft Teams du déploiement des journaux et des alertes d’activité Office 365 est à présent complète.

### <a name="cloud-app-security-release-93"></a>Cloud App Security version 93

Publication : 20 mars 2017

**Nouvelles fonctionnalités :**

- Vous pouvez maintenant appliquer des stratégies pour inclure ou exclure des groupes d’utilisateurs importés.
- L’anonymisation de Cloud App Security vous permet désormais de configurer une clé de chiffrement personnalisée. Pour plus d’informations, consultez [anonymisation Cloud Discovery](cloud-discovery-anonymizer.md).
- Pour un contrôle plus étendu sur l’administration des utilisateurs et des comptes, vous disposez désormais d’un accès direct aux paramètres des comptes Azure AD pour chaque utilisateur et chaque compte depuis la page **Compte**. Cliquez simplement sur l’engrenage en regard de chaque utilisateur. Cette modification vous permet d’accéder plus facilement à l’administration avancée des utilisateurs, à l’administration des groupes de fonctionnalités, à la configuration de l’authentification multifacteur, aux informations détaillées sur les connexions des utilisateurs et à la possibilité de bloquer les connexions.
- À partir de maintenant, vous pouvez exporter un script de blocage pour les applications non autorisées via l’API Cloud App Security. Pour plus d’informations sur nos API dans le portail Cloud App Security, cliquez sur le point d’interrogation dans la barre de menus, puis sur **Documentation des API**.
- Le connecteur d’applications Cloud App Security pour ServiceNow a été étendu pour prendre en charge les jetons OAuth (nouveauté pour Genève, Helsinki, Istanbul). Cette modification fournit une connexion d’API plus robuste à ServiceNow, qui ne s’appuie pas sur l’utilisateur du déploiement. Pour plus d’informations, consultez [connecter ServiceNow à Microsoft Cloud App Security](connect-servicenow-to-microsoft-cloud-app-security.md). Les clients existants peuvent mettre à jour leurs paramètres dans la page du connecteur d’applications ServiceNow.
- Si vous avez configuré d’autres analyseurs DLP tiers, l’état d’analyse DLP affiche individuellement l’état de chaque connecteur de façon à améliorer la visibilité.
- Cloud App Security prend maintenant en charge les activités Microsoft Teams qui sont prises en charge dans le journal d’audit d’Office 365. Cette fonctionnalité est déployée progressivement.
- Pour les événements d’emprunt d’identité Exchange Online, vous pouvez désormais filtrer en fonction du niveau d’autorisation utilisé : délégué, administrateur ou administrateur délégué. Vous pouvez rechercher des événements affichant le niveau d’emprunt d’identité qui vous intéresse dans le **Journal d’activité** en recherchant des objets d' **activité**  >  **élément**.
- Dans le tiroir des applications sous l’onglet **Autorisations des applications** des applications Office 365, vous pouvez désormais voir l’**Éditeur** de chaque application. Vous pouvez également utiliser l’éditeur comme filtre pour rechercher les autres applications du même éditeur.
- Les adresses IP à risques apparaissent maintenant comme facteur de risque indépendant et non plus pondéré, sous le facteur de risque général **Emplacement**.
- Quand les étiquettes Azure Information Protection sont désactivées sur un fichier, elles apparaissent désactivées dans Cloud App Security. Les étiquettes supprimées ne sont pas affichées.

**Prise en charge supplémentaire de Salesforce :**

- Maintenant, vous pouvez suspendre et rétablir des utilisateurs Salesforce dans Cloud App Security. Cette action peut être effectuée sous l’onglet **Comptes** du connecteur Salesforce. Cliquez sur l’engrenage à la fin de la ligne d’un utilisateur spécifique et sélectionnez **Suspendre** ou **Annuler la suspension**. Vous pouvez également appliquer Suspendre et Annuler la suspension comme action de gouvernance dans le cadre d’une stratégie. Toutes les activités Suspendre et Rétablir effectuées dans Cloud App Security sont consignées dans le [journal de gouvernance](governance-actions.md).
- Visibilité améliorée sur le partage de contenu Salesforce : vous pouvez désormais voir quels fichiers ont été partagés et avec qui, notamment les fichiers partagés publiquement, les fichiers partagés avec des groupes et les fichiers partagés avec l’ensemble du domaine Salesforce. Cette meilleure visibilité sera déployée rétroactivement sur les applications Salesforce connectées nouvelles et actuelles : la première mise à jour peut nécessiter un certain temps.
- Nous avons amélioré la couverture des événements Salesforce suivants et nous les avons séparés de l’activité **Gérer les utilisateurs** :
  - Modifier les autorisations
  - Créer un utilisateur
  - Modifier le rôle
  - Réinitialiser le mot de passe

### <a name="cloud-app-security-release-90-91-92"></a>Cloud App Security version 90, 91, 92

Date de publication : février 2017

**Annonce spéciale :**

Cloud App Security est maintenant officiellement certifié conforme à ISO, HIPAA, CSA STAR, aux clauses contractuelles types de l’Union européenne et plus encore. Pour consulter la liste complète des certifications, accédez à l’article [Offres de conformité Microsoft](https://www.microsoft.com/trustcenter/compliance/complianceofferings) et sélectionnez Cloud App Security.

**Nouvelles fonctionnalités :**

- **Importer des groupes d’utilisateurs (préversion)** Quand vous connectez des applications à l’aide de connecteurs d’API, Cloud App Security vous permet maintenant d’importer des groupes d’utilisateurs à partir d’Office 365 et d’Azure Active Directory. L’importation de groupes d’utilisateurs peut être utile dans les scénarios suivants : vous souhaitez connaître quels documents sont consultés par le service des Ressources Humaines, ou vous voulez vérifier si quelque chose d’inhabituel s’est produit dans le groupe des dirigeants ou si un membre du groupe des administrateurs a effectué une activité en dehors de France. Pour plus d’informations et obtenir des instructions, consultez [Importation de groupes d’utilisateurs](user-groups.md).

- Dans le journal d’activité, vous pouvez maintenant filtrer les utilisateurs et les utilisateurs dans les groupes pour afficher les activités qui ont été effectuées par un utilisateur donné et celles qui ont été effectuées sur un utilisateur donné. Par exemple, vous pouvez examiner les activités ayant été effectuées par un utilisateur au nom d’autres utilisateurs, et les activités effectuées par d’autres utilisateurs au nom de cet utilisateur. Pour plus d’informations, consultez [Activités](activity-filters.md).

- Quand vous examinez un fichier dans la page **Fichiers**, si vous explorez le fichier spécifique **Collaborateurs**, vous pouvez maintenant voir plus d’informations sur les collaborateurs. Ces informations indiquent s’ils sont internes ou externes, auteurs ou lecteurs (autorisations de fichiers) et, quand un fichier est partagé avec un groupe, vous pouvez maintenant voir tous les utilisateurs qui sont membres du groupe. Le fait de voir tous les utilisateurs vous permet de savoir si les membres du groupe sont des utilisateurs externes.

- La prise en charge IPv6 est désormais disponible pour tous les appareils.

- Cloud Discovery prend désormais en charge les appareils Barracuda.

- Le système Cloud App Security envoie maintenant des alertes pour les erreurs de connectivité de l’agent SIEM. Pour plus d’informations, consultez [SIEM integration](siem.md) (Intégration de SIEM).

- Cloud App Security prend maintenant en charge les activités suivantes :

  - **Office 365, SharePoint/OneDrive** : Mettre à jour la configuration de l’application, Supprimer le propriétaire du groupe, Supprimer le site, Créer un dossier

  - **Dropbox** : Ajouter un membre au groupe, Supprimer un membre dans le groupe, Créer un groupe, Renommer un groupe, Renommer un membre du groupe

  - **Box** : Supprimer un élément dans le groupe, Mettre à jour le partage d’élément, Ajouter un utilisateur au groupe, Supprimer un utilisateur dans le groupe

### <a name="cloud-app-security-release-89"></a>Cloud App Security version 89

Publiée le 22 janvier 2017

**Nouvelles fonctionnalités :**

- Nous commençons à déployer la possibilité de voir les événements DLP du Centre de sécurité et de conformité Office 365 dans Cloud App Security. Si vous avez configuré des stratégies DLP dans le Centre de sécurité et de conformité Office 365, vous pouvez voir les correspondances de stratégie dans le journal des activités de Cloud App Security quand elles sont détectées. Les informations contenues dans le journal des activités comprennent le fichier ou l’e-mail qui a déclenché la correspondance, ainsi que la stratégie ou l’alerte correspondante. L’activité **Événement de sécurité** vous permet de voir les correspondances de stratégie DLP d’Office 365 dans le journal des activités de Cloud App Security. À l’aide de cette fonctionnalité, vous pouvez :
  - Voir toutes les correspondances DLP provenant du moteur DLP d’Office 365.
  - Alerter sur des correspondances de stratégie DLP d’Office 365 pour un fichier, un site SharePoint ou une stratégie spécifique.
  - Examiner les correspondances DLP avec un contexte plus large, par exemple étendu aux utilisateurs externes qui ont accédé à ou téléchargé un fichier qui a déclenché une correspondance de stratégie DLP.

- Les descriptions des activités ont été améliorées pour plus de clarté et de cohérence. Chaque activité comporte désormais un bouton de feedback. Si vous ne comprenez pas certaines choses ou si vous avez une question, vous pouvez nous en faire part.

**Améliorations :**

- Une nouvelle action de gouvernance a été ajoutée pour Office 365, qui vous permet de supprimer tous les utilisateurs externes d’un fichier. Par exemple, cette action vous permet d’implémenter des stratégies qui **suppriment les partages externes des fichiers avec une classification exclusivement interne**.
- Amélioration de l’identification des utilisateurs externes dans SharePoint Online. Lors du filtrage du groupe « utilisateurs externes », le @"sharepoint" compte système de l’application n’apparaît pas.

### <a name="cloud-app-security-release-88"></a>Cloud App Security version 88

Publiée le 8 janvier 2017

**Nouvelles fonctionnalités :**

- Connectez votre serveur SIEM à Cloud App Security. Vous pourrez désormais envoyer des alertes et des activités automatiquement au serveur SIEM de votre choix en configurant des agents SIEM. Désormais disponible en préversion publique.  Pour une documentation complète et plus d’informations, consultez Intégration à SIEM.
- Cloud Discovery prend désormais en charge IPv6. Nous avons déployé la prise en charge pour Palo Alto et Juniper, et d’autres appareils seront déployés dans les versions ultérieures.

**Améliorations :**

- Il existe un nouveau facteur de risque dans le catalogue d’applications cloud. Vous pouvez désormais évaluer une application selon qu’elle nécessite ou non l’authentification utilisateur. Les applications qui exigent l’authentification et qui n’autorisent pas l’utilisation anonyme reçoivent un score de risque correspondant à un état plus sain.
- Nous déployons de nouvelles descriptions d’activités plus utilisables et plus cohérentes, qui n’affectent pas la recherche des activités.
- Nous avons inclus une meilleure identification utilisateur-appareil, qui permet à Cloud App Security de documenter un plus grand nombre d’événements avec des informations sur les appareils.

## <a name="updates-made-in-2016"></a>Mises à jour effectuées en 2016

### <a name="cloud-app-security-release-87"></a>Cloud App Security version 87

Publication le 25 décembre 2016

**Nouvelles fonctionnalités :**

- Nous sommes en train de déployer l’[anonymisation des données](cloud-discovery-anonymizer.md), pour vous permettre de bénéficier de Cloud Discovery tout en protégeant la vie privée des utilisateurs. L’anonymisation de données est effectuée en chiffrant les informations des noms d’utilisateur.
- Nous allons bientôt permettre d’exporter un script de blocage depuis Cloud App Security sur des appliances supplémentaires. Le script vous permet de réduire facilement l’informatique fantôme en bloquant le trafic pour des applications non approuvées. Cette option est maintenant disponible pour :
  - BlueCoat ProxySG
  - Cisco ASA
  - Fortinet
  - Juniper SRX
  - Palo Alto
  - Websense
- Une nouvelle action de gouvernance de fichier a été ajoutée, qui vous permet de forcer un fichier à hériter des autorisations du parent, supprimant toutes les autorisations individuelles qui ont été définies pour le fichier ou le dossier. Cette action de gouvernance de fichier vous permet de modifier les autorisations de votre fichier ou dossier pour qu’elles soient héritées du dossier parent.
- Un nouveau groupe d’utilisateurs nommé Externe a été ajouté. Il s’agit d’un groupe d’utilisateurs par défaut qui est préconfiguré par Cloud App Security de façon à inclure tous les utilisateurs qui ne font pas partie de vos domaines internes. Vous pouvez utiliser ce groupe d’utilisateurs comme filtre. Par exemple, vous pouvez rechercher les activités effectuées par des utilisateurs externes.
- La fonctionnalité Cloud Discovery prend maintenant en charge les appliances Sophos Cyberoam.

**Résolutions de bogues :**

- Les fichiers SharePoint Online et OneDrive Entreprise apparaissaient dans le rapport Stratégie de fichier et dans la page Fichiers comme internes au lieu de privés. Ce bogue a été corrigé.

### <a name="cloud-app-security-release-86"></a>Cloud App Security version 86

Publication le 13 décembre 2016

**Nouvelles fonctionnalités :**

- Toutes les licences autonomes Cloud App Security vous permettent d’activer les analyses Azure Information Protection à partir des paramètres généraux (sans qu’il soit nécessaire de créer une stratégie).

**Améliorations :**

- Vous pouvez maintenant utiliser « ou » dans le filtre de fichiers pour le nom de fichier et dans le filtre de type MIME pour les fichiers et les stratégies. Cette modification permet des scénarios tels que l’entrée du mot « Passport » ou « Driver » lors de la création d’une stratégie pour les données personnelles. Le filtre correspond à n’importe quel fichier ayant « Passport » ou « Driver » dans le nom de fichier.
- Par défaut, quand une stratégie d’inspection DLP s’exécute, les données des violations qui en résultent sont masquées. Vous pouvez maintenant afficher les 4 derniers caractères de la violation.

**Améliorations mineures :**

- Nouveaux événements liés à la boîte aux lettres d’Office 365 (Exchange) en relation avec des règles de transfert, et ajout et suppression d’autorisations de boîtes aux lettres déléguées.
- Nouvel événement qui audite l’octroi d’un consentement à de nouvelles applications dans Azure Active Directory.

### <a name="cloud-app-security-release-85"></a>Cloud App Security version 85

Publiée le 27 novembre 2016

**Nouvelles fonctionnalités :**

- Une distinction a été établie entre les applications approuvées et les applications connectées. Vous pouvez désormais appliquer une balise aux applications découvertes et à toutes les applications du catalogue d’applications pour les marquer comme approuvées ou non. Les applications connectées sont des applications que vous avez connectées à l’aide du connecteur d’API pour une meilleure visibilité et un plus grand contrôle. Vous pouvez désormais soit marquer les applications comme approuvées ou non, soit les connecter à l’aide du connecteur d’application, le cas échéant.
- Compte tenu de cette modification, la page des applications approuvées a été remplacée par une nouvelle page **Applications connectées** qui externalise les données d’état sur les connecteurs.
- Les collecteurs de journal sont plus facilement accessibles dans leur propre ligne dans le menu **Paramètres** sous **Sources**.
- Quand vous créez un filtre de stratégie d’activité, vous pouvez réduire les faux positifs en choisissant d’ignorer les activités répétées quand elles sont exécutées sur le même objet cible par le même utilisateur. Par exemple, une alerte n’est pas déclenchée si la même personne tente plusieurs fois de télécharger le même fichier.
- Des améliorations ont été apportées au tiroir d’activité. À présent, quand vous cliquez sur un objet d’activité dans le tiroir d’activité, vous pouvez descendre dans la hiérarchie pour obtenir plus d’informations.

**Améliorations :**

- Des améliorations ont été apportées au moteur de détection des anomalies, notamment au niveau des alertes de déplacement impossible. Des informations sur l’adresse IP sont désormais disponibles dans la description de l’alerte.
- Des améliorations ont été apportées aux filtres complexes : vous pouvez ainsi ajouter plusieurs fois le même filtre pour affiner les résultats filtrés.
- Les activités liées aux fichiers et aux dossiers dans Dropbox ont été séparées pour une meilleure visibilité.

**Résolutions de bogues :**

- Un bogue à l’origine de faux positifs a été résolu dans le mécanisme de déclenchement des alertes système.

### <a name="cloud-app-security-release-84"></a>Cloud App Security version 84

Publiée le 13 novembre 2016

**Nouvelles fonctionnalités :**

- Cloud App Security prend désormais en charge Microsoft Azure Information Protection, avec notamment une intégration améliorée et le provisionnement automatique. Vous pouvez filtrer vos fichiers et définir des stratégies de fichier à l’aide de la classification sécurisée des étiquettes, puis définir l’étiquette de classification que vous voulez afficher. Les étiquettes indiquent également si la classification a été définie par une personne de votre organisation ou d’un autre locataire (externe). Vous pouvez également définir des stratégies d’activité basées sur les étiquettes de classification d’Azure Information Protection et activer l’analyse automatique des étiquettes de classification dans Office 365. Pour plus d’informations sur la façon de tirer parti de cette nouvelle fonctionnalité intéressante, consultez [Intégration à Azure Information Protection](azip-integration.md).

**Améliorations :**

- Des améliorations ont été apportées au journal d’activité de Cloud App Security :
  - Les événements Office 365 provenant du Centre de sécurité et conformité sont désormais intégrés à Cloud App Security et sont visibles dans le **journal d’activité**.
  - Toute l’activité de Cloud App Security est enregistrée dans le journal d’activité Cloud App Security comme activité d’administration.
- Pour vous permettre d’examiner les alertes relatives aux fichiers, dans chaque résultant d’une stratégie de fichier, vous pouvez désormais afficher la liste des activités qui ont été effectuées sur le fichier correspondant.
- L’algorithme de voyage impossible dans le moteur de détection d’anomalie a été amélioré pour fournir une meilleure prise en charge pour les petits locataires.

**Améliorations mineures :**

- La **limite d’exportation d’activités** a été portée à 10 000.
- Quand vous créez un **rapport d’instantané** dans le processus de chargement manuel du journal Cloud Discovery, vous recevez désormais une estimation précise de la durée de traitement du journal.
- Dans une stratégie de fichier, l’action de gouvernance **Supprimer le collaborateur** fonctionne désormais sur les groupes.
- Des améliorations mineures ont été apportées dans la page **Autorisations d’applications**.
- Quand plus de 10 000 utilisateurs avaient des autorisations pour une application qui se connecte à Office 365, la liste se chargeait lentement. Cette lenteur a été corrigée.
- Des attributs supplémentaires ont été ajoutés au **Catalogue d’applications** en ce qui concerne le secteur des cartes de paiement.

### <a name="cloud-app-security-release-83"></a>Cloud App Security version 83

Publication : 30 octobre 2016

**Nouvelles fonctionnalités :**

- Pour simplifier le filtrage dans le [journal d’activité](activity-filters.md) et le [journal de fichier](file-filters.md), les filtres similaires ont été regroupés. Utilisez les filtres d’activité : Objet d’activité, Adresse IP et Utilisateur. Utilisez le filtre de fichier Collaborateurs pour trouver ce dont vous avez besoin.
- À partir du tiroir Journal d’activité, sous **Source**, vous pouvez cliquer sur le lien pour **Afficher les données brutes**. Cette action télécharge les données brutes utilisées pour générer le journal d’activité pour explorer plus en détail les événements de l’application.
- Prise en charge d’activités de connexion supplémentaires dans Okta. [Private preview]
- Prise en charge d’activités de connexion supplémentaires dans Salesforce.

**Améliorations :**

- Plus grande facilité d’utilisation des rapports d’instantané Cloud Discovery et de la résolution des problèmes.
- Meilleure visibilité des alertes portant sur plusieurs applications dans la liste des alertes.
- Plus grande facilité d’utilisation lors de la création de nouveaux rapports continus Cloud Discovery.
- Plus grande facilité d’utilisation dans le journal de gouvernance.

### <a name="cloud-app-security-release-82"></a>Cloud App Security version 82

Publication : 9 octobre 2016

**Améliorations :**

- Les activités **Change email** (Modifier l’e-mail) et **Modifier le mot de passe** sont maintenant indépendantes de l’activité générique **Manage users** (Gérer les utilisateurs) dans Salesforce.
- Ajout d’une clarification concernant la limite d’alerte quotidienne par SMS. 10 messages au maximum sont envoyés par numéro de téléphone par jour (UTC).
- Un nouveau certificat a été ajouté aux attributs Cloud Discovery pour le bouclier de protection des données qui a remplacé Safe Harbor (fournisseurs aux États-Unis uniquement).
- La résolution des problèmes a été ajoutée aux messages d’erreur concernant les connecteurs API pour faciliter les actions correctives.
- Amélioration de la fréquence des mises à jour de l’analyse des applications tierces Office 365.
- Améliorations apportées au tableau de bord Cloud Discovery.
- L’analyseur Syslog de point de contrôle a été amélioré.
- Améliorations apportées au journal de gouvernance pour l’exclusion et l’annulation de l’exclusion des applications tierces.

**Résolutions de bogues :**

- Processus amélioré pour le chargement d’un logo.

### <a name="cloud-app-security-release-81"></a>Cloud App Security version 81

Publication : 18 septembre 2016

**Améliorations :**

- Cloud App Security est maintenant une application interne dans Office 365 ! Vous pouvez désormais connecter Office 365 à Cloud App Security en un seul clic.

- Nouveau look pour le journal de gouvernance : il présente maintenant le même aspect clair et utile que le tableau des fichiers et du journal d’activité. Les nouveaux filtres permettent de trouver facilement ce dont vous avez besoin et de surveiller vos actions de gouvernance.
- Des améliorations ont été apportées au moteur de détection des anomalies en cas de plusieurs échecs de connexion et d’autres facteurs de risque.
- Des améliorations ont été apportées aux rapports d’instantanés Cloud Discovery.
- Des améliorations ont été apportées aux activités administratives dans le journal d’activité ; Modifier le mot de passe, Mettre à jour un utilisateur, Réinitialiser le mot de passe indiquent désormais si l’activité a été effectuée en tant qu’activité administrative.
- Les filtres d’alerte pour les alertes système ont été améliorés.
- L’étiquette pour une stratégie au sein d’une alerte permet maintenant de revenir au rapport de stratégie.
- Si aucun propriétaire n’est spécifié pour un fichier Dropbox, les e-mails de notification sont envoyés au destinataire que vous définissez.
- Cloud App Security prend en charge 24 langues supplémentaires, ce qui étend la prise en charge à un total de 41 langues.

### <a name="cloud-app-security-release-80"></a>Cloud App Security version 80

Publication : 4 septembre 2016

**Améliorations :**

- Quand l’analyse DLP échoue, vous recevez maintenant une explication des raisons pour lesquelles Cloud App Security n’a pas pu analyser le fichier. Pour plus d’informations, voir [Inspection du contenu](./content-inspection.md).
- Des améliorations ont été apportées aux moteurs de détection des anomalies, notamment pour les alertes de voyage impossible.
- Des améliorations ont été apportées à l’expérience qui permet d’ignorer les alertes. Vous pouvez également ajouter un feedback qui permet à l’équipe Cloud App Security de savoir si l’alerte était intéressante et pourquoi. Votre feedback est utilisé pour améliorer les détections de Cloud App Security.
- Les analyseurs Cloud Discovery Cisco ASA ont été améliorés.
- Vous recevez maintenant une notification par e-mail quand le chargement manuel de votre journal Cloud Discovery est terminé.

### <a name="cloud-app-security-release-79"></a>Cloud App Security version 79

Publication : 21 août 2016

**Nouvelles fonctionnalités :**

- **Nouveau tableau de bord Cloud Discovery** : un tout nouveau tableau de bord Cloud Discovery est disponible, conçu pour vous donner plus d’informations sur l’utilisation des applications cloud dans votre organisation. Il fournit une vue d’ensemble en un clin d’œil des types d’applications utilisés, des alertes ouvertes et des niveaux de risque des applications dans votre organisation. Il vous permet également de connaître les principaux utilisateurs des applications dans votre organisation et fournit un plan du lieu du siège social d’une application. Le nouveau tableau de bord présente davantage d’options pour filtrer les données et vous permettre ainsi de générer des vues spécifiques selon ce qui vous intéresse le plus, et des graphiques faciles à comprendre pour vous donner une vision globale en un clin d’œil.

- **Nouveaux rapports Cloud Discovery** : pour voir les résultats de Cloud Discovery, vous pouvez désormais générer deux types de rapports : les rapports d’instantanés et les rapports continus. Les rapports d’instantanés fournissent une visibilité ad hoc sur un ensemble de journaux de trafic que vous chargez manuellement à partir de vos pare-feu et proxys. Les rapports continus affichent les résultats de tous les journaux qui sont transférés à partir de votre réseau à l’aide des collecteurs de journaux de Cloud App Security. Ces nouveaux rapports offrent une meilleure visibilité sur toutes les données, l’identification automatique d’une utilisation anormale par le moteur de détection des anomalies Machine Learning de Cloud App Security ainsi que l’identification d’une utilisation anormale, telle que vous l’avez définie avec le moteur de stratégie robuste et granulaire. Pour plus d’informations, consultez [configurer des Cloud Discovery](set-up-cloud-discovery.md).

**Améliorations :**

- Facilité d’utilisation globale améliorée dans les pages suivantes : pages de stratégies, paramètres généraux, paramètres de messagerie.
- Dans la table des alertes, il est désormais plus facile de faire la distinction entre les alertes lues et les alertes non lues. Les alertes lues affichent une ligne bleue sur la gauche et apparaissent grisées pour indiquer que vous les avez déjà lues.
- Les paramètres de la stratégie d’activité **Activité répétée** ont été mis à jour.
- Dans la page des comptes, une colonne **Type** pour l’utilisateur a été ajoutée et vous pouvez maintenant voir le type de compte d’utilisateur de chaque utilisateur. Les types d’utilisateurs sont spécifiques à l’application.
- Une prise en charge en temps quasi réel a été ajoutée pour les activités liées aux fichiers dans OneDrive et SharePoint. Quand un fichier est modifié, Cloud App Security déclenche une analyse presque immédiatement.

### <a name="cloud-app-security-release-78"></a>Cloud App Security version 78

Publication : 7 août 2016

**Améliorations :**

- À partir d’un fichier spécifique, vous pouvez désormais cliquer avec le bouton droit et **Rechercher des éléments associés**. À partir du journal d’activité, vous pouvez utiliser le filtre d’objet cible et sélectionner le fichier spécifique.

- Des analyseurs de fichiers journaux Cloud Discovery optimisés, avec l’ajout de Juniper et Cisco ASA.
- Cloud App Security vous permet désormais de fournir des commentaires relatifs à l’amélioration des alertes quand vous ignorez l’une d’elles. Vous pouvez aider à améliorer la qualité de la fonctionnalité d’alerte de Cloud App Security en nous indiquant pourquoi vous ignorez l’alerte. Par exemple : elle n’est pas intéressante, vous avez reçu trop d’alertes similaires, la gravité réelle doit être inférieure, l’alerte n’est pas exacte.
- Dans la vue Stratégie de fichier, ou quand vous visualisez un fichier, quand vous ouvrez le tiroir Fichiers, le nouveau lien vers Stratégies correspondantes a été ajouté. Quand vous cliquez sur celui-ci, vous pouvez voir toutes les correspondances et vous pouvez désormais toutes les ignorer.
- L’unité d’organisation à laquelle appartient un utilisateur est maintenant ajoutée à toutes les alertes pertinentes.
- Une notification par e-mail est maintenant envoyée pour vous avertir de la fin du traitement de vos journaux chargés manuellement.

### <a name="cloud-app-security-release-77"></a>Cloud App Security version 77

Publication : 24 juillet 2016

**Améliorations :**

- L’icône du bouton Exporter Cloud Discovery a été améliorée pour la facilité d’utilisation.
- Quand vous examinez une activité, si l’agent utilisateur n’a pas été analysé, vous pouvez désormais voir les données brutes.
- Deux nouveaux facteurs de risque ont été ajoutés au moteur de détection des anomalies :
  - Cloud App Security utilise désormais les balises d’adresse IP qui sont associées à un botnet et les adresses IP anonymes dans le cadre du calcul de risque.
  - L’activité Office 365 est maintenant surveillée pour les taux de téléchargements élevés. Si le taux de téléchargement Office 365 est plus important que le taux de téléchargement standard de votre organisation ou d’un utilisateur spécifique, une alerte de détection d’anomalie est déclenchée.
- Cloud App Security est désormais compatible avec la nouvelle API de [fonctionnalité de partage sécurisé](https://blogs.dropbox.com/dropbox/2016/06/new-dropbox-productivity-tools/) Dropbox.
- Des améliorations ont été apportées pour ajouter des détails aux erreurs d’analyse des journaux Cloud Discovery, notamment : Pas de transactions liées au cloud, Tous les événements sont obsolètes, Fichier endommagé, Le format de journal ne correspond pas.
- Le filtre de date du journal d’activité a été amélioré ; il inclut désormais la possibilité de filtrer par heure.
- La page des plages d’adresses IP a été améliorée pour la facilité d’utilisation.
- Cloud App Security inclut désormais la prise en charge de Microsoft Azure Information Protection (préversion). Vous pouvez filtrer vos fichiers et définir des stratégies de fichier avec la classification sécurisée des étiquettes. Ensuite, définissez le niveau de l’étiquette de classification que vous voulez voir. Les étiquettes indiquent également si la classification a été définie par une personne de votre organisation ou d’un autre locataire (externe).

### <a name="cloud-app-security-release-76"></a>Cloud App Security version 76

Publication : 10 juillet 2016

**Améliorations :**

- Les listes d’utilisateurs dans les rapports intégrés peuvent maintenant être exportées.
- Facilité d’utilisation améliorée pour la stratégie d’activité agrégée.
- Prise en charge améliorée pour l’analyseur des messages du journal de pare-feu TMG W3C.
- Facilité d’utilisation améliorée pour la liste déroulante des actions de gouvernance des fichiers, qui est désormais séparée en actions de collaboration, de sécurité et d’examen.
- Détection de voyage impossible améliorée pour l’activité Exchange Online : Envoyer un message.
- Une nouvelle liste de titres (barres de navigation) a été ajoutée en haut des pages d’alertes et de stratégies pour faciliter la navigation.

**Résolutions de bogues :**

- L’expression prédéfinie pour Carte de crédit dans le paramètre DLP pour les stratégies de fichier a été remplacée par Tout : Finance : Carte de crédit.

### <a name="cloud-app-security-release-75"></a>Cloud App Security version 75

Publication : 27 juin 2016

**Nouvelles fonctionnalités :**

- De nouveaux ajouts ont été faits à notre liste croissante des événements Salesforce pris en charge.  Les événements incluent la fourniture d’insights dans les rapports, des liens partagés, de la distribution de contenu, la connexion avec emprunt d’identité, etc.
- Les icônes des applications connectées sur le tableau de bord Cloud App Security ont été alignées sur l’état des applications affichées sur le tableau de bord pour refléter les 30 derniers jours.
- Prise en charge des écrans en pleine largeur.

**Résolutions de bogues :**

- Les numéros de téléphone des alertes par SMS sont maintenant validés lors de l’insertion.

### <a name="cloud-app-security-release-74"></a>Cloud App Security version 74

Publication : 13 juin 2016

- L’écran Alerte a été mis à jour de façon à fournir plus d’informations en un coup d’œil. Les mises à jour incluent la possibilité de voir immédiatement toutes les activités de l’utilisateur, une carte des activités, des journaux de gouvernance des utilisateurs associés, une description de la raison du déclenchement de l’alerte, et des graphiques et des cartes supplémentaires dans la page de l’utilisateur.
- Les événements générés par Cloud App Security incluent désormais le type d’événement, le format, les groupes de stratégies, les objets associés et une description.
- De nouvelles étiquettes d’adresses IP ont été ajoutées pour les applications Office 365 pour Enterprise, OneNote, Office Online et Exchange Online Protection.
- Vous pouvez désormais charger les journaux à partir du menu de découverte principal.
- Le filtre Catégorie d’adresse IP a été amélioré. La catégorie d’adresse IP « Null » est désormais appelée « Sans catégorie ». Une nouvelle catégorie appelée « Aucune valeur » a été ajoutée pour inclure toutes les activités dépourvues de données d’adresse IP.
- Les groupes de sécurité dans Cloud App Security sont maintenant appelées « groupes d’utilisateurs » pour éviter toute confusion avec les groupes de sécurité Active Directory.
- Vous pouvez désormais filtrer par adresse IP et exclure les événements dépourvus d’adresse IP.
- Des modifications ont été apportées aux paramètres des e-mails de notification qui sont envoyés quand des correspondances sont détectées dans les stratégies d’activité et de fichier. Vous pouvez maintenant ajouter les adresses de messagerie des destinataires auxquels vous souhaitez envoyer une copie (CC) de la notification.

### <a name="cloud-app-security-release-73"></a>Cloud App Security version 73

Publication : 29 mai 2016

- Mise à jour des fonctions d’alerte : vous pouvez maintenant définir des alertes par stratégie à envoyer par e-mail ou SMS.
- Page d’alertes : conception optimisée pour une meilleure gestion des incidents et des options de résolution avancées.
- Ajustement de la stratégie : les alertes vous permettent maintenant de passer des options de résolution d’alerte directement à la page des paramètres de stratégie pour un réglage en fonction des alertes plus facile.
- Améliorations apportées à la détection des anomalies et au calcul du score de risque et réduction du nombre de faux positifs sur la base des commentaires des clients.
- L’exportation du journal d’activité inclut désormais les ID d’événement, la catégorie d’événement et le nom du type d’événement.
- Apparence et convivialité optimisées pour les actions de gouvernance de création de stratégies.
- Examen et contrôle simplifiés pour Office 365 : Office 365 sélectionne automatiquement toutes les applications qui font partie d’une Suite Office 365.
- Les notifications sont désormais envoyées à l’adresse e-mail configurée dans l’application connectée.
- En cas d’erreur de connexion, une description détaillée de l’erreur est désormais fournie par l’application cloud.
- Lorsqu’un fichier correspond à une stratégie, une URL d’accès au fichier est désormais fournie dans le tiroir de fichiers.
- Lorsqu’une alerte est déclenchée par une stratégie d’activité ou une stratégie de détection des anomalies, une nouvelle notification détaillée est envoyée. Cette dernière fournit des informations sur le résultat.
- Une alerte système automatique est déclenchée lorsqu’un connecteur d’application est déconnecté.
- Vous pouvez maintenant ignorer et résoudre une alerte ou une sélection en bloc d’alertes à partir de la page des alertes.

### <a name="cloud-app-security-release-72"></a>Cloud App Security version 72

Publication : 15 mai 2016

- Améliorations de l’apparence générale et de l’infrastructure, notamment :

  - Nouveau diagramme pour une meilleure assistance pour le processus de chargement manuel du manuel Cloud Discovery.
  - Amélioration du processus de mise à jour des fichiers journaux non reconnus (« Autres »). Ce processus inclut une fenêtre contextuelle qui vous permet de savoir que le fichier nécessite une révision supplémentaire. Vous êtes averti quand les données sont disponibles.
  - Plus de violations d’activités et de fichiers sont signalées lors de l’examen d’un journal d’activité et de fichier en cas de navigateurs et de systèmes d’exploitation obsolètes.

- Des analyseurs de fichiers journaux Cloud Discovery optimisés, avec notamment l’ajout de Cisco ASA, Cisco FWSM, Cisco Meraki et W3C.
- Résolution de problèmes connus avec Cloud Discovery.
- De nouveaux filtres d’activité ont été ajoutés au domaine du propriétaire et à l’affiliation interne/externe.
- Un nouveau filtre a été ajouté pour rechercher tout objet Office 365 (fichiers, dossiers, URL).
- La possibilité de configurer un score de risque minimal pour les stratégies de détection d’anomalie a été ajoutée.
- Lorsque vous définissez l’envoi d’une alerte en cas de violation d’une stratégie, vous pouvez maintenant définir un niveau de gravité minimal à partir duquel vous souhaitez être alerté. Vous pouvez choisir d’utiliser pour cela les paramètres par défaut de votre organisation et définir un paramètre d’alerte spécifique comme valeur par défaut pour votre organisation.

[!INCLUDE [Open support ticket](includes/support.md)]