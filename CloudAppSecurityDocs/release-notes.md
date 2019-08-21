---
title: Nouveautés de Cloud App Security
description: Cet article est mis à jour fréquemment pour vous informer des nouveautés de la dernière version de Cloud App Security.
author: ShlomoSagir-MS
ms.author: shsagir
manager: ShlomoSagir-MS
ms.date: 8/18/2019
ms.topic: overview
ms.service: cloud-app-security
ms.collection: M365-security-compliance
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 92caf80bb63f3285cfff3761e274ee6eb76b1041
ms.sourcegitcommit: 850bf268bcb9fef0fe4870daa7341211d02776ad
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69577141"
---
# <a name="whats-new-with-microsoft-cloud-app-security"></a>Nouveautés de Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

Cet article est mis à jour fréquemment pour vous informer des nouveautés de la dernière version de Cloud App Security.

Flux RSS : Recevez une notification quand cette page est mise à jour en copiant et collant l’URL suivante dans votre lecteur de flux : `https://docs.microsoft.com/api/search/rss?search=%22This+article+is+updated+frequently+to+let+you+know+what%27s+new+in+the+latest+release+of+Cloud+App+Security%22&locale=en-us`

## <a name="cloud-app-security-release-156"></a>Cloud App Security version 156

Publication : 18 août 2019

- **Nouveaux analyseurs de journal Cloud Discovery**<br>
Cloud App Security Cloud Discovery analyse une large gamme de journaux de trafic pour classer et noter les applications. Cloud Discovery intègre désormais un analyseur de journaux intégré pour prendre en charge les formats de journaux Stormshield et Forcepoint LEEF.

- **Améliorations du journal d’activité**<br>
Cloud App Security offre désormais une meilleure visibilité des activités non classifiées effectuées par les applications dans votre environnement. Ces activités sont disponibles dans le journal d’activité ainsi que dans les stratégies d’activité. Pour voir les activités non classifiées, dans le filtre **Type**, sélectionnez **Non spécifié**. Pour plus d’informations sur les filtres d’activité, consultez [Filtres d’activité et requêtes](activity-filters-queries.md).

- **Amélioration des investigations sur les utilisateurs à risque**<br>
Cloud App Security permet d’identifier les utilisateurs à risque dans la page **Utilisateurs et comptes** par groupes, applications et même rôles spécifiques. Vous pouvez désormais également examiner les utilisateurs de votre organisation en fonction de leur score **Priorité d’une enquête**. Pour plus d’informations, consultez [Comprendre le score de priorité d’examen](tutorial-ueba.md#risk-score).

- **Améliorations de la stratégie d’activité**<br>
Vous pouvez désormais créer des alertes de stratégie d’activité basées sur des objets d’activité. Par exemple, cette fonctionnalité vous permet de créer des alertes sur les modifications apportées aux rôles d’administration d’Azure Active Directory. Pour plus d’informations sur les objets d’activité, consultez [Filtres d’activité](activity-filters-queries.md#activity-filters).

<!-- **Workday app connector available (Preview)**<br>
A new app connector is now available for Workday. You can now connect Microsoft Cloud App Security to Workday to monitor activities and protect its users. For more information, see [Connect Workday](connect-workday-to-microsoft-cloud-app-security.md).-->

## <a name="cloud-app-security-release-155"></a>Cloud App Security version 155

Publication : 4 août 2019

- **Nouveaux modèles de stratégie**<br>
Cloud App Security intègre maintenant de nouveaux modèles de stratégies d'activité pour de meilleures pratiques de sécurité AWS.

- **Avertissement : Fin de la prise en charge de TLS 1.0 et 1.1 le 8 septembre**<br>
Microsoft transfère tous ses services en ligne vers Transport Layer Security (TLS) 1.2+ pour fournir le meilleur chiffrement de sa catégorie. Par conséquent, à partir du 8 septembre 2019, Cloud App Security ne prendra plus en charge TLS 1.0/1.1 et les connexions utilisant ces protocoles. Pour plus d'informations sur l’impact de ce changement, lisez [notre billet de blog](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/End-of-support-for-TLS-1-0-and-1-1-in-Microsoft-Cloud-App/ba-p/770507).

## <a name="cloud-app-security-release-154"></a>Cloud App Security version 154

Publication : 21 juillet 2019

- **Intégrer et déployer le contrôle d’application par accès conditionnel pour tous les types d’applications maintenant en GA**<br>
Depuis que nous vous avons montré un aperçu du contrôle d’application par accès conditionnel pour toutes les applications le mois dernier, nous avons reçu un feedback incroyable et nous sommes donc très contents d’annoncer sa disponibilité générale. Cette nouvelle fonctionnalité vous permet de déployer n’importe quelle application web en vue d’utiliser des stratégies de session et d’accès, et de bénéficier de puissantes fonctionnalités de supervision et de contrôle en temps réel.

- **Évaluation de la configuration de la sécurité pour AWS**<br>
Cloud App Security met progressivement en place la possibilité d’obtenir une évaluation de la configuration de la sécurité de votre environnement Amazon Web Services à des fins de conformité CIS, et fournit des recommandations s’il manque des configurations et des contrôles de la sécurité. Cette fonctionnalité permet aux organisations de superviser l’état de conformité de tous les comptes AWS connectés à partir d’une seule vue.

- **Détections d’anomalies d’application OAuth**<br>
Nous avons étendu notre actuelle fonctionnalité de détection d’applications OAuth suspectes. Quatre nouvelles détections sont maintenant prêtes à l’emploi, qui profilent les métadonnées des applications OAuth autorisées dans votre organisation pour identifier celles qui sont potentiellement malveillantes.

## <a name="cloud-app-security-release-153"></a>Cloud App Security mise en production 153

Publication : 7 juillet 2019

- **Support Dropbox amélioré**<br>
Cloud App Security prend désormais en charge l’action de gouvernance **Corbeille** pour Dropbox : cette action de gouvernance peut être utilisée manuellement ou automatiquement en tant que partie d’une stratégie de fichier.
- **Nouvelles applications proposées pour le contrôle d’application par accès Cloud**<br>
Le contrôle d’application par accès conditionnel pour les applications proposées suivantes est généralement disponible :

    - OneDrive Entreprise
    - SharePoint Online
    - Azure DevOps
    - Exchange Online
    - Power BI

- **Autoriser les fichiers identifiés comme programme malveillant**<br>
Cloud App Security analyse les fichiers à partir de vos applications connectées pour rechercher l’exposition DLP et les programmes malveillants. Vous pouvez maintenant autoriser les fichiers identifiés comme programme malveillant mais confirmés sans échec après examen. Autoriser un fichier le supprime du rapport de détection des programmes malveillants et supprime les correspondances futures sur ce fichier. Pour plus d’informations sur la détection de programme malveillant, consultez [Détection d’anomalie Cloud App Security](anomaly-detection-policy.md).

## <a name="cloud-app-security-release-152"></a>Cloud App Security version 152

Publication : 23 juin 2019

- **Déployer le contrôle d’application par accès conditionnel pour tous les types d’applications (préversion)**<br>
Nous sommes heureux d’annoncer que nous avons étendu notre prise en charge du contrôle d’application par accès conditionnel à l’ensemble des applications web, en plus de la prise en charge que nous proposons déjà pour les [applications à la une](proxy-intro-aad.md). Cette nouvelle fonctionnalité vous permet de déployer n’importe quelle application web en vue d’utiliser des stratégies de session et d’accès, et de bénéficier de puissantes fonctionnalités de supervision et de contrôle en temps réel. Par exemple, vous pouvez protéger les téléchargements avec des étiquettes Azure Information Protection, bloquer le chargement des documents sensibles, effectuer des audits, et bien plus encore.
- **Audit des activités dans le portail**<br>
Cloud App Security audite toutes les activités d’administration du portail, vous permettant ainsi de superviser et d’analyser les activités de manière approfondie. À présent, vous pouvez également exporter jusqu’à 90 jours d’activités en vue de procéder à une analyse. Par exemple, vous pouvez auditer un administrateur qui analyse les activités d’un utilisateur ou qui affiche certaines alertes. Pour exporter le journal, accédez à la page de paramètres **Gérer l’accès administrateur**.
- **Déconnexion de session personnalisée à partir du portail Cloud App Security**<br>
Vous pouvez désormais configurer la déconnexion automatique des sessions administrateur du portail après une durée d’inactivité spécifiée.

## <a name="cloud-app-security-release-151"></a>Cloud App Security version 151

Publication : 9 juin 2019

- **UEBA hybride - Intégration native avec Azure ATP (préversion)**<br>
Cloud App Security s’intègre maintenant en mode natif dans Azure ATP pour fournir une vue unique des activités d’identité dans les applications cloud et votre réseau local. Pour plus d’informations, consultez [Intégration d’Azure Advanced Threat Protection](aatp-integration.md).
- **Améliorations apportées à UEBA**<br>
Pour vous aider à identifier les menaces qui échappent aux contrôles, Cloud App Security utilise désormais le profilage unique afin de fournir des indices de risque pour les alertes et activités individuelles. Les indices de risque peuvent être utilisés pour identifier des activités qui ne sont pas assez suspectes en elles-mêmes pour déclencher des alertes. Toutefois, en regroupant les indices de risque dans un **indice de priorité d’examen** pour l’utilisateur, Cloud App Security vous permet d’identifier des comportements à risques et de concentrer votre examen. Ces fonctionnalités sont désormais disponibles dans la nouvelle page utilisateur.
- **Nouveau facteur de risque ajouté au catalogue d’applications cloud**<br>
Le catalogue d’applications cloud inclut désormais le facteur de risque du plan de récupération d’urgence pour vous permettre d’évaluer les applications dans le catalogue d’applications cloud pour la prise en charge de la continuité des activités métier.
- **Connecteur Microsoft Flow GA**<br>
Après la préversion de la prise en charge de Microsoft Cloud App Security l’an dernier, le connecteur est maintenant généralement disponible.
- **Amélioration de gouvernance automatisées pour les stratégies de fichiers**<br>
Cloud App Security prend désormais en charge la configuration de l’action de gouvernance **Mettre à la corbeille** pour les stratégies de fichiers. Cette action de gouvernance vous permet de déplacer automatiquement des fichiers vers le dossier Corbeille.
- **Prise en charge améliorée de Google Drive**<br>
Cloud App Security prend désormais en charge l’action de gouvernance **Mettre à la corbeille** pour les stratégies de fichiers. Cette action de gouvernance vous permet de déplacer automatiquement des fichiers Google Drive vers le dossier Corbeille.
- **Nouvelle autorisation pour les rôles d’administrateur d’application et d’administrateur de groupe**<br>
Les rôles *Administrateur d’application/d’instance* et *Administrateur de groupe d’utilisateurs* prennent désormais en charge l’accès en lecture seule.

## <a name="cloud-app-security-release-150"></a>Cloud App Security version 150

Publication : le 26 mai 2019

- **Amélioration de l’exportation des alertes**<br>
Lorsque vous exportez des alertes au format CSV à partir de la page **Alertes**, les résultats incluront désormais la date de résolution ou de rejet de l'alerte.

## <a name="cloud-app-security-release-148-and-149"></a>Cloud App Security versions 148 et 149

Publication le 12 mai 2019

- **Connecteur d’applications WebEx disponible**<br>Un nouveau connecteur d’applications est maintenant disponible pour Cisco WebEx Teams en préversion publique. Vous pouvez maintenant connecter Microsoft Cloud App Security à Cisco WebEx Teams pour surveiller et protéger ses utilisateurs, activités et fichiers. Pour plus d’informations, consultez [Connecter WebEx](connect-webex-to-microsoft-cloud-app-security.md)

- **Nouveaux sites du service de classification des données Microsoft**<br>Le [service de classification des données Microsoft](dcs-inspection.md) est désormais disponible dans 4 nouveaux pays : Australie, Inde, Canada et Japon. Si votre locataire Office se trouve dans ces pays, vous pouvez maintenant utiliser le service de classification des données Microsoft comme méthode d’inspection du contenu dans les stratégies de fichier Microsoft Cloud App Security.

- **Découverte des clichés instantanés PaaS et IaaS**<br> Microsoft Cloud App Security a étendu ses capacités Cloud Discovery et propose désormais également une fonctionnalité Shadow IT pour les ressources hébergées sur des solutions IaaS et PaaS comme Microsoft Azure, Amazon Web Services et Google Cloud Platform. Cloud Discovery fournit désormais une visibilité permettant à des applications personnalisées de s’exécuter par-dessus vos solutions IaaS et PaaS, comptes de stockage créés, et bien plus encore. Utilisez cette nouvelle fonctionnalité pour découvrir les ressources existantes, identifier les personnes qui accèdent à chacune d’elles, et le volume de trafic transmis.

- **Attestation d’application**<br>L’évaluation de la conformité et du risque Microsoft Cloud App Security permet maintenant aux fournisseurs de cloud d’attester que leur application est mise à jour dans le catalogue d’applications cloud. Ce programme pilote permet aux fournisseurs de cloud de remplir un questionnaire à attestation automatique selon des attributs de risque du catalogue d’applications cloud pour s’assurer que leur évaluation du risque dans Cloud App Security est à jour. Les utilisateurs peuvent obtenir une indication des attributs de risque qui ont été attestés par le fournisseur (plutôt qu’évalués par l’équipe Cloud App Security) et la date à laquelle chaque attribut a été soumis par le fournisseur. Pour plus d’informations, consultez [Attester votre application](attest-your-app.md).

- **Granularité de la charge de travail Office 365**<br>Lorsque vous connectez Office 365 à Microsoft Cloud App Security, vous pouvez maintenant choisir les charges de travail à connecter. Par exemple, les clients uniquement intéressés par la connexion d’Office 365 pour la surveillance de l’activité peuvent désormais le faire pendant le processus de connexion ou en modifiant un connecteur Office 365 existant. Dans le cadre de ce changement, OneDrive et SharePoint Online ne seront plus affichés en tant que connecteurs séparés mais seront inclus dans le connecteur Office 365 en tant que charge de travail des fichiers _Office 365_. Les clients disposant d’un connecteur Office 365 existant ne sont pas affectés par cette modification.

- **Prise en charge améliorée de Teams**<br>Vous pouvez désormais surveiller et bloquer l’envoi de message dans l’application web Teams en temps réel, en configurant une stratégie de session basée sur du contenu sensible.

## <a name="cloud-app-security-release-147"></a>Cloud App Security version 147

Publication : 14 avril 2019

- **Nouvel analyseur de journal Cloud Discovery**<br>Cloud App Security Cloud Discovery inclut désormais un analyseur de journal intégré pour prendre en charge le format de journal Palo Alto LEEF.

- **Mises à jour des stratégies de session**
    - **Méthode d’inspection du contenu supplémentaire pour les stratégies de session** :<br>Lorsque vous définissez une stratégie de session, vous avez désormais la possibilité de choisir le Service de classification des données en tant que méthode d’inspection du contenu pour les fichiers. Le Service de classification des données offre à l’utilisateur un large éventail de types sensibles intégrés à utiliser pour identifier les informations sensibles.
    - **Contrôle amélioré des autorisations de fichier dans les stratégies de session** :<br>Lorsque vous créez une stratégie de session pour contrôler les téléchargements à l’aide de Cloud App Security, vous pouvez maintenant appliquer automatiquement les autorisations par utilisateur, comme la lecture seule, aux documents lors de leur téléchargement à partir de vos applications cloud. Cela fournit un niveau supérieur de flexibilité et la possibilité de protéger les informations au-delà de vos étiquettes d’entreprise préconfigurées.
    - **Contrôle du téléchargement de fichiers volumineux** :<br>Lorsque l’inspection du contenu est activée dans les stratégies de session, vous pouvez désormais contrôler ce qui se passe quand un utilisateur tente de télécharger un fichier très volumineux. Si le fichier est trop volumineux pour une analyse lors du téléchargement, vous pouvez choisir s’il sera bloqué ou autorisé.

## <a name="cloud-app-security-release-146"></a>Cloud App Security version 146

Date de publication : 31 mars 2019

- **Amélioration du voyage impossible**<br>
La détection d’un voyage impossible a été améliorée avec une prise en charge dédiée pour les pays voisins.
- **Prise en charge d’attributs supplémentaires pour l’analyseur CEF générique**<br>
La prise en charge de l’analyseur du journal Cloud Discovery pour le format CEF générique a été améliorée pour prendre en charge des attributs supplémentaires.
- **Accès étendu aux rapports Cloud Discovery**<br>
En plus du rôle Discovery Admin, vous pouvez maintenant étendre l’accès à des rapports Discovery spécifiques. Cette amélioration vous permet de configurer des privilèges d’accès aux données de sites et divisions spécifiques.
- **Nouvelle prise en charge de rôle : lecteur général**<br>
Microsoft Cloud App Security prend désormais en charge le rôle de lecteur général Azure AD. Le lecteur général dispose d’un accès complet en lecture seule à tous les aspects de Microsoft Cloud App Security, mais il ne peut ni modifier des paramètres ni prendre aucune mesure.

## <a name="cloud-app-security-release-145"></a>Cloud App Security version 145

Date de publication : 17 mars 2019

- **L’intégration de Microsoft Defender ATP est en disponibilité générale** <br>
L’année dernière, nous avons annoncé l’[intégration à Windows Defender Advanced Threat Protection](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Cloud-App-Security-and-Windows-Defender-ATP-better/ba-p/263265) qui améliore la découverte de Shadow IT dans votre organisation et l’étend au-delà du réseau d’entreprise. [Activée en un seul clic](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RWtNmG), nous sommes heureux d’annoncer que cette intégration unique est maintenant en disponibilité générale.
- **Prise en charge de Dynamics 365 CRM**<br>
Cloud App Security a ajouté des fonctionnalités de supervision et de contrôle en temps réel pour Dynamics 365 CRM, afin de vous permettre de protéger vos applications métier et le contenu sensible stocké dans ces applications. Pour plus d'informations sur les possibilités offertes par Dynamics 365 CRM, lisez [cet article](proxy-intro-aad.md#how-it-works).

## <a name="cloud-app-security-release-144"></a>Cloud App Security version 144

Date de publication : 3 mars 2019

- **Investigation unifiée de SecOps pour les environnements hybrides**<br> Étant donné que de nombreuses organisations ont des environnements hybrides, les attaques démarrent dans le cloud avant de basculer en local, ce qui signifie que les équipes SecOps doivent investiguer ces attaques depuis différents endroits. En combinant les signaux provenant de sources cloud et locales, dont Microsoft Cloud App Security, Azure ATP et Azure AD Identity Protection, Microsoft donne une plus grande autonomie aux analystes de sécurité en fournissant des informations unifiées sur les identités et les utilisateurs dans une console unique, ce qui élimine le besoin de basculer entre les solutions de sécurité. Vos équipes SecOps disposent ainsi de plus de temps et des bonnes informations pour prendre de meilleures décisions et pallier activement les véritables risques et menaces relatives à l’identité. Pour plus d’informations, consultez [Unified SecOps Investigation for Hybrid Environments](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Unified-SecOps-Investigation-for-Hybrid-Environments/ba-p/360850)

- **Fonctionnalités de sandboxing pour la détection de programmes malveillants** (lancement progressif)<br>
Les fonctionnalités de détection de programmes malveillants de Cloud App Security sont développées pour inclure la capacité à identifier les logiciels malveillants à effet immédiat via une technologie de sandboxing avancée.<br>
Dans le cadre de cette fonctionnalité, Cloud App Security identifie automatiquement les fichiers suspects et les détone pour rechercher un comportement de fichier suspect et des indicateurs que le fichier a un but malveillant (programme malveillant). <br>
Dans le cadre de ce changement, les stratégies de détection de programmes malveillants incluent désormais un champ de type de détection qui vous permet de filtrer par Threat Intelligence ainsi que par sandboxing.
- **Mises à jour de l’accès conditionnel**<br> Avec le contrôle d’application par accès conditionnel, vous avez maintenant la possibilité de superviser et de bloquer les activités suivantes :
    - Chargements de fichiers dans les applications : permet des scénarios tels que l’interdiction du chargement des extensions de logiciels malveillants connus et la garantie que les utilisateurs protègent les fichiers avec AIP avant le chargement.
    - Fonction copier-coller dans les applications : complète les contrôles fiables d’exfiltration de données qui comprenaient déjà le contrôle des activités de téléchargement, d’impression et personnalisées telles que le partage.
    - Envoyer un message : garantie que les données PII comme les mots de passe ne sont pas partagées dans les outils de collaboration populaires tels que Slack, Salesforce et Workplace by Facebook.
- Les stratégies de session incluent désormais des modèles intégrés pour permettre à votre organisation d’activer sans effort une supervision et un contrôle en temps réel de vos applications approuvées, comme **Bloquer le chargement en fonction de l’inspection du contenu en temps réel**.

## <a name="cloud-app-security-release-143"></a>Cloud App Security mise en production 143

Date de publication : 17 février 2019

- **Déploiement étendu pour les instances d’applications** Le déploiement étendu peut maintenant être configuré au niveau de l’instance de l’application, permettant ainsi davantage de granularité et de contrôle.
- **Améliorations des rôles**
    - Les rôles d’administrateur de données et d’opérateur de sécurité pour Office 365 sont désormais pris en charge dans Cloud App Security. Le rôle d’administrateur de données permet aux utilisateurs de gérer tout ce qui est lié aux fichiers ainsi que d’afficher les rapports Cloud Discovery. Les opérateurs de sécurité sont autorisés à gérer les alertes et à afficher la configuration de la stratégie.
    - Le rôle de lecteur de sécurité a maintenant la possibilité de configurer l’agent SIEM, ce qui permet une meilleure étendue des autorisations.
- **Prise en charge de Microsoft Flow** Cloud App Security analyse désormais les activités des utilisateurs dans Microsoft Flow. Les activités prises en charge sont les activités signalées par Flow au journal d’audit Office 365.
- **Regroupement des entités d’alerte** La page **Alerte** regroupe désormais des entités associées qui ont été impliquées dans une alerte pour vous aider dans votre investigation.

## <a name="cloud-app-security-release-142"></a>Cloud App Security mise en production 142

Date de publication : 3 février 2019

- **Configuration de stratégies de session dans Azure AD**<br>
Vous pouvez maintenant configurer des stratégies de session pour superviser les utilisateurs ou bloquer les téléchargements en temps réel, directement dans l’accès conditionnel Azure AD. Vous pouvez toujours configurer des stratégies de session avancées directement dans Cloud App Security. Pour connaître la procédure pas à pas de ce déploiement, consultez [Déployer le contrôle d’application par accès conditionnel pour les applications Azure AD](proxy-deployment-aad.md).

- **Requêtes suggérées et enregistrées pour les applications OAuth** <br>
Les requêtes suggérées ont été ajoutées à la page des applications OAuth. Elles fournissent des modèles d’examen prédéfinis qui vous permettent de filtrer vos applications OAuth. Les requêtes suggérées incluent des filtres personnalisés qui identifient les applications à risque telles que les applications autorisées par les administrateurs. Les requêtes enregistrées permettent d’enregistrer des requêtes personnalisées pour une utilisation ultérieure, de manière similaire aux requêtes enregistrées déjà disponibles dans les pages Découverte et Journal d’activité.

- **Configuration par défaut de l’audit Office 365**<br>
Si vous souhaitez activer la supervision des activités Office 365 dans Cloud App Security, vous devez maintenant activer l’audit dans le [Centre de sécurité et conformité Office 365](https://docs.microsoft.com/office365/securitycompliance/turn-audit-log-search-on-or-off#turn-on-audit-log-search). Cela est dû à un [changement apporté à l’audit Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-faq#what-happens-if-i-disable-auditing-for-my-office-365-organization-will-i-still-get-events-via-the-management-activity-api). Ce changement est nécessaire uniquement si vous n’avez pas encore activé la supervision des activités Office 365 dans Cloud App Security.

- **Prise en charge améliorée de Box**<br>
Cloud App Security prend en charge deux nouvelles actions de gouvernance pour Box :

   - **Faire expirer le lien partagé** – Cette action de gouvernance vous permet de définir la date d’expiration d’un lien partagé, date après laquelle ce lien ne sera plus actif.

   - **Modifier le niveau d’accès du lien de partage** – Cette action de gouvernance vous permet de modifier le niveau d’accès du lien partagé (entreprise uniquement, collaborateurs uniquement ou public).

- **Prise en charge des emplacements multiples dans OneDrive**<br>
Avec Cloud App Security, vous voyez désormais l’intégralité des fichiers dans OneDrive, même s’ils sont répartis entre plusieurs emplacements géographiques. La protection est maintenant disponible pour les fichiers situés aux emplacements supplémentaires ainsi qu’à l’emplacement principal.

- **Amélioration de la navigation dans le portail**<br>
Le portail Cloud App Security a été amélioré pour fluidifier la navigation et mieux aligner Cloud App Security avec les autres services de sécurité de Microsoft, pour une plus grande simplicité d’utilisation.

## <a name="cloud-app-security-release-141"></a>Cloud App Security version 141

Publiée le 20 janvier 2019

- **Améliorations apportées à l’analyse de risque cloud**
    - L’analyse de risque des applications cloud a été enrichie de deux nouvelles expériences.
        - Un nouvel attribut **Type de données** évalue le type de contenu que les utilisateurs peuvent charger sur l’application. Vous pouvez l’utiliser pour analyser une application en fonction de la sensibilité des différents types de données de votre organisation.
        - Pour profiter d’une vue d’ensemble plus complète du risque d’une application, vous pouvez maintenant facilement basculer de l’analyse de risque de l’application à celle de la société d’hébergement en cliquant sur l’attribut **Société d’hébergement**.

- **Amélioration du contexte de fichier à des fins d’examen des alertes de détection d’anomalie**
    - L’examen de la détection d’anomalie a été amélioré de façon à donner des informations supplémentaires sur les fichiers impliqués dans l’alerte. Lorsque des alertes sont déclenchées en cas d’activité inhabituelle liée à des fichiers (téléchargement, partage, suppression), ce zoom avant est disponible. Par exemple, si la plupart des fichiers affectés proviennent du même dossier ou partagent la même extension, ces informations apparaissent dans la section Risque supplémentaire de l’alerte.

- **Demandes d’examen de fichier**
    - La capacité de Cloud App Security à créer et à enregistrer des requêtes personnalisées a été étendue à la page **Fichiers**. Les requêtes de la page **Fichier** permettent de créer des modèles de requête réutilisables à des fins d’examen approfondi.

## <a name="cloud-app-security-release-139-140"></a>Cloud App Security versions 139, 140

Publiée le 6 janvier 2019

- **Modification dans la détection de fichier**<br>
Les fichiers partagés avec tout le monde dans SharePoint et One Drive sont désormais considérés comme **internes** [en raison des modifications apportées à SharePoint et One Drive](https://support.microsoft.com/help/4089534/how-to-grant-the-everyone-claim-to-external-users-in-office-365). Donc, si un fichier qui est partagé avec tout le monde est détecté, il est désormais considéré comme un fichier interne. Cela affecte la façon dont le fichier est géré par les stratégies et affiché dans la page des fichiers.

- **Modification dans la supervision de fichier**<br>
Le comportement de supervision par défaut a été modifié pour les clients nouveaux et inactifs. Vous devrez maintenant activer la surveillance de fichier pour activer la fonctionnalité, via **Paramètres** > **Fichiers**. Les clients actifs existants ne sont pas affectés par cette modification.

- **Paramétrage avancé pour les stratégies de détection d’anomalie**<br>
Vous pouvez désormais configurer le moteur de détection d’anomalie pour supprimer ou déclencher des alertes en fonction de vos préférences.
    - Dans la stratégie Voyage impossible, vous pouvez définir le curseur de sensibilité pour déterminer le niveau d’un comportement anormal nécessaire avant qu’une alerte ne soit déclenchée.
    - Vous pouvez également configurer si les alertes pour Activité à partir de pays peu fréquents, d’adresses IP anonymes, d’adresses IP suspectes et Voyage impossible doivent analyser les échecs et les réussites de connexion ou juste les réussites de connexion.

- **Prise en charge de plusieurs chaînes d’approbation** Le contrôle d’application par accès conditionnel prend désormais en charge l’ajout et l’utilisation de plusieurs certificats intermédiaires ou racines de confiance en tant que méthode de gestion des appareils.

- **Nouveau rôle Cloud Discovery** (déploiement progressif) Cloud App Security fournit désormais un nouveau rôle administrateur pour les utilisateurs de Cloud Discovery. Ce rôle peut être utilisé afin de limiter l’accès d’un utilisateur administrateur uniquement aux données et paramètres Cloud Discovery dans le portail Cloud App Security.

- **Prise en charge des étiquettes unifiées Microsoft Information Protection** (déploiement progressif) Cloud App Security prend désormais en charge les étiquettes unifiées Microsoft Information Protection. Pour les clients qui ont déjà [migré leurs étiquettes de classification pour leur Centre de conformité et de sécurité Office 365](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels), Cloud App Security identifie et utilise ces étiquettes, comme décrit dans [Intégration avec Azure Information Protection](azip-integration.md).

**Prise en charge de l’étiquetage de fichier PDF** (déploiement progressif) Pour les clients qui utilisent des étiquettes unifiées, Cloud App Security prend désormais en charge l’étiquetage automatique des fichiers PDF.

## <a name="cloud-app-security-release-138"></a>Cloud App Security version 138

Date de publication : 9 décembre 2018

- **Chargement automatique de journal à l’aide de Docker sur Windows**<br>Cloud App Security prend désormais en charge le chargement automatique de journal pour Windows 10 (Fall Creators Update) et Windows Server (version 1709 et ultérieure) à l’aide d’un Docker pour Windows.
Pour obtenir plus d’informations et des instructions sur la configuration de cette fonctionnalité, consultez [Docker sur Windows en local](discovery-docker-windows.md).
- Vous pouvez intégrer Cloud App Security à [Microsoft Flow](https://docs.microsoft.com/flow/getting-started) pour assurer l’automatisation et fournir des playbooks d’orchestration à la suite d’alertes personnalisées. Pour obtenir plus d’informations et des instructions sur l’intégration, consultez [Intégration à Microsoft Flow](flow-integration.md).

## <a name="cloud-app-security-release-137"></a>Cloud App Security version 137

Publiée le 25 novembre 2018

- **Ajout de la prise en charge de Dynamics**<br>
Cloud App Security prend maintenant en charge les activités Microsoft Dynamics qui sont prises en charge dans le journal d’audit d’Office 365.
- **Analyse du contenu chiffré (en préversion)**<br>
Cloud App Security vous permet désormais d’analyser le contenu qui est protégé par des étiquettes de protection Azure Information Protection. Vous pouvez ainsi trouver du contenu sensible, même dans les fichiers qui ont déjà été chiffrés par Azure Information Protection.
- **Attention : nouvelle terminologie !**<br>
Le nom des fonctionnalités d’autorisations d’application a été modifié pour plus de clarté : on parle désormais d’**applications OAuth**.

## <a name="cloud-app-security-release-136"></a>Cloud App Security version 136

Publiée le 11 novembre 2018

- **Mises à jour de Cloud Discovery**<br>
L’analyseur de journal personnalisé a été amélioré pour prendre en charge davantage de formats de journaux de trafic web, dont certains plus complexes. Dans le cadre de ces améliorations, les utilisateurs peuvent désormais entrer des en-têtes personnalisés dans les fichiers de journaux CSV sans en-tête, utiliser des délimiteurs spéciaux pour les fichiers clé-valeur, traiter le format de fichier Syslog, et bien plus encore.
- **Nouvelles stratégies de détection des anomalies**<br>
Règles de manipulation de boîte de réception suspecte : Cette stratégie profile votre environnement et déclenche des alertes lorsque des règles de boîte de réception suspectes qui suppriment ou déplacent des messages ou des dossiers sont définies sur la boîte de réception d’un utilisateur. Cela peut indiquer que le compte de l’utilisateur est compromis, que des messages sont masqués intentionnellement, et que la boîte aux lettres est utilisée pour distribuer du courrier indésirable ou des programmes malveillants dans votre organisation.
- **Prise en charge des groupes dans les stratégies d’autorisation d’application**<br>
Cloud App Security permet désormais de définir des stratégies d’autorisation d’application plus granulaires, en fonction du groupe auquel appartiennent les utilisateurs qui ont autorisé les applications. Par exemple, un administrateur peut décider de définir une stratégie qui révoque les applications rares si celles-ci nécessitent des autorisations élevées, uniquement si l’utilisateur qui a accordé les autorisations est un membre du groupe Administrateurs.
- **Le contrôle d’application par accès conditionnel s’intègre désormais à vos applications locales via le proxy d’application Azure Active Directory**
  - Le [proxy d’application Azure AD](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy) fournit l’authentification unique et un accès distant sécurisé aux applications web hébergées localement.
  - Ces applications web locales peuvent désormais être routées vers Microsoft Cloud App Security via l’accès conditionnel Azure AD dans le but de fournir un contrôle et une supervision en temps réel, par le biais des stratégies [Accès](access-policy-aad.md) et [Session](session-policy-aad.md).

## <a name="cloud-app-security-release-133-134-135"></a>Cloud App Security version 133, 134, 135

Publication : octobre 2018

- **Nouvelles stratégies de détection des anomalies progressivement déployées**
    - La nouvelle stratégie Exfiltration de données vers une application non approuvée est activée automatiquement pour vous avertir quand un utilisateur ou une adresse IP utilise une application qui n’est pas approuvée pour effectuer une activité qui ressemble à une tentative d’exfiltration des informations en dehors de votre organisation.
    - La nouvelle stratégie Plusieurs activités de suppression de machine virtuelle profile votre environnement et déclenche des alertes quand des utilisateurs suppriment plusieurs machines virtuelles dans une même session, relativement à la base de référence de votre organisation.

- **Service de classification des données disponible pour la région Asie-Pacifique**
    - Le service de classification des données est désormais disponible pour les clients de la région Asie-Pacifique. Pour obtenir la liste complète de la prise en charge par région, consultez [Intégration des services de classification des données Microsoft](dcs-inspection.md).

- **Prise en charge d’i-Filter par Cloud Discovery**
    - La fonctionnalité Cloud Discovery de Cloud App Security intègre désormais une prise en charge améliorée de l’analyseur syslog i-Filter.

## <a name="cloud-app-security-release-132"></a>Cloud App Security version 132

Publication : 25 septembre 2018

- **Le Contrôle d’application par accès conditionnel pour Office 365 est désormais disponible en préversion publique**
    - Désormais, le Contrôle d’application par accès conditionnel prend également en charge Office 365 et toute application configurée avec Open ID Connect.
    - Fournir des commentaires à partir d’une session : Ce nouvel outil vous permet de fournir des commentaires à l’équipe Cloud App Security concernant les performances d’une application sous contrôle de session, directement à partir de la session.

- **Intégration native avec Microsoft Defender ATP pour Shadow IT Discovery au-delà de votre société**
    - Microsoft Cloud App Security s’intègre désormais en mode natif à au module Windows Defender - Protection avancée contre les menaces (ATP) pour fournir des fonctionnalités de découverte Shadow IT sans déploiement pour activer et désactiver l’utilisation de réseau d’entreprise par des applications cloud.  Cela vous permet d’effectuer une découverte Cloud Discovery sur les ordinateurs, même quand ils ne se trouvent pas sur votre réseau d’entreprise. Cela permet également d’effectuer un examen basé sur l’ordinateur : après avoir identifié un utilisateur à risque, vous pouvez vérifier tous les ordinateurs auxquels l’utilisateur a accédé pour détecter les risques potentiels. Si vous identifiez un ordinateur à risque, vous pouvez vérifier tous les utilisateurs qui l’ont utilisé pour rechercher les risques potentiels. Pour plus d’informations, consultez la rubrique relative à l’intégration du module Windows Defender - Protection avancée contre les menaces à [Microsoft Cloud App Security](wdatp-integration.md).
- **Inspection du contenu pour les fichiers chiffrés**
    - Cloud App Security prend désormais en charge l’inspection de contenu des fichiers protégés qui sont chiffrés et qui ont été protégés à l’aide d’Azure Information Protection. Vous pouvez maintenant examiner ces fichiers chiffrés à des fins de reclassification et identifier d’autres violations de stratégies d’exposition et de sécurité DLP.

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
Vous pouvez désormais envoyer des commentaires à l’équipe Cloud App Security pour nous indiquer s’il existe une application OAuth découverte dans votre organisation qui semble malveillante. Cette nouvelle fonctionnalité vous permet de faire partie de notre communauté de sécurité et d’améliorer l’analyse et le score de risque de l’application OAuth. Pour plus d’informations, consultez [Gérer les applications OAuth](manage-app-permissions.md).

- **Nouveaux analyseurs Cloud Discovery**<br>
Les analyseurs Cloud Discovery prennent désormais en charge iboss Secure Cloud Gateway et Sophos XG.

## <a name="cloud-app-security-release-129"></a>Cloud App Security version 129

Publication : 5 août 2018

- **Nouvelles stratégies de détection des anomalies : règles concernant les e-mails suspects**<br>De nouvelles stratégies de détection des anomalies ont été ajoutées pour détecter les règles de transfert des e-mails suspects, par exemple, si un utilisateur a créé une règle de boîte de réception assurant le transfert d’une copie de tous les e-mails à une adresse externe.
- Cette version inclut des correctifs et améliorations ciblant plusieurs problèmes.

## <a name="cloud-app-security-release-128"></a>Cloud App Security version 128

Publication : 22 juillet 2018

- **Actions possibles sur plusieurs applications OAuth**<br>
Pour les applications OAuth qui ont reçu des autorisations d’application, vous pouvez désormais en interdire ou en approuver plusieurs en une seule action. Par exemple, vous pouvez consulter toutes les applications qui ont reçu une autorisation par les utilisateurs de votre organisation, sélectionner toutes les applications que vous voulez interdire et cliquer sur Interdire des applications pour révoquer tous les consentements accordés et cesser d’autoriser les utilisateurs à accorder des autorisations à ces applications.  Pour plus d’informations, consultez [Gérer les applications OAuth](manage-app-permissions.md).
- **Prise en charge avancée des applications Azure**<br>
Pour Azure, nous offrons progressivement la possibilité de détecter les applications en tant qu’activités de compte d’utilisateur effectuées par les applications Azure (internes et externes). Cela vous permet de créer des stratégies qui vous avertissent si une application effectue des activités inattendues et non autorisées. Pour plus d’informations, consultez [Connecter Azure à Microsoft Cloud App Security](connect-azure-to-microsoft-cloud-app-security.md).
- **Moteur de classification des données mis à jour avec de nouveaux types de contenu sensible du RGPD**<br>
Le [Service de classification des données Cloud App Security](dcs-inspection.md) a ajouté de nouveaux types de contenu sensible à notre moteur de classification des données pour vous permettre de détecter du contenu relatif au RGPD dans vos fichiers.
- **Mises à jour du catalogue des applications cloud**<br>
Le catalogue d’applications cloud comprend maintenant une catégorie de risque Légal (en plus de Général, Sécurité et Conformité) pour vous aider à gérer la conformité à la confidentialité et à la propriété des données, notamment la préparation au RGPD.
Pour vous permettre d’évaluer la préparation au RGPD de chaque application cloud, la nouvelle catégorie de risque contient l’instruction de préparation au RGPD du service cloud et l’état de chaque contrôle de structure du RGPD.
Notez que, dans le cadre de cette amélioration, les attributs de risque suivants ont été déplacés de l’autre catégorie de risque à la catégorie Légal :
     - DMCA
     - Propriété des données
     - Stratégie de conservation des données

     De plus, la nouvelle catégorie de risque est évaluée séparément pour vous permettre de configurer la pondération du score en fonction de vos préférences et de vos priorités. Pour plus d’informations, consultez [Score du risque](risk-score.md).

- **Nouvelle requête proposée : prête pour le RGPD** <br>
Il existe une nouvelle proposition de requête qui vous permet d’identifier les applications découvertes qui sont prêtes pour le RGPD. Étant donné que le RGPD est récemment devenu une priorité absolue pour les administrateurs de sécurité, cette requête vous aide à identifier les applications qui sont prêtes pour le RGPD et à atténuer les menaces en évaluant le risque de celles qui ne le sont pas.

## <a name="cloud-app-security-release-127"></a>Cloud App Security version 127

Publication : 8 juillet 2018

- Vous pouvez désormais voir les activités génériques pour Office 365 dans le **Journal d’activité** et filtrer les activités Office 365 ayant pour état **Non spécifié** dans les **Stratégies d’activité**. Vous pouvez examiner ces activités pour rechercher des informations sur les activités effectuées non encore classées par type dans Cloud App Security, et vous pouvez utiliser ces activités pour envoyer des demandes à l’équipe Cloud App Security afin de créer des types d’activités en fonction de ces activités.

## <a name="cloud-app-security-release-126"></a>Cloud App Security version 126

Publication : 24 juin 2018

- **Contrôle d’application par accès conditionnel en disponibilité générale**<br>Le contrôle d’application par accès conditionnel Microsoft Cloud App Security (proxy inverse) est maintenant en disponibilité générale pour toutes les applications SAML. Le contrôle d’application par accès conditionnel s’intègre directement à vos stratégies d’accès conditionnel Azure AD pour **surveiller et contrôler les sessions de vos utilisateurs en temps réel**, tout en leur permettant d’être productifs. Depuis la première préversion de la fonctionnalité, de nombreuses fonctions et améliorations ont été apportées, notamment :
    - La possibilité de créer une [stratégie d’accès](access-policy-aad.md) pour gérer l’accès aux mêmes applications à partir des clients natifs, en plus de créer une stratégie de session pour le trafic du navigateur.
    - Le processus d’intégration des applications a été simplifié pour prendre en charge les applications SAML personnalisées de votre organisation.
    - Dans le cadre du réseau mondial Azure, l’intégration et l’interface ont été améliorées pour que les utilisateurs bénéficient d’une expérience fluide, où qu’ils se trouvent.

- **Inspection du contenu avec les services de classification des données Microsoft en disponibilité générale**<br>L’intégration de Microsoft Cloud App Security avec les services de classification des données Microsoft est maintenant en disponibilité générale. Cette intégration vous permet d’utiliser le service de classification des données Microsoft en mode natif pour classer les fichiers dans vos applications cloud. Pour plus d’informations, consultez [Intégration des services de classification des données Microsoft](dcs-inspection.md). Cette fonctionnalité est actuellement uniquement disponible aux États-Unis et en Europe (à l’exclusion de la France).

- **Rapport exécutif Cloud Discovery**<br>Microsoft Cloud App Security met progressivement en place la possibilité de générer un rapport exécutif Cloud Discovery au format PDF. Ce rapport fournit une vue d’ensemble de l’utilisation du Shadow IT qui a été identifiée dans votre organisation, en mettant en avant les principaux utilisateurs et principales applications utilisées en général et dans les catégories dominantes, et se concentre sur le risque que pose le Shadow IT dans votre organisation. De plus, le rapport fournit une liste de recommandations pour améliorer la visibilité et le contrôle du Shadow IT dans votre organisation. Utilisez ce rapport pour vous assurer que les menaces et risques potentiels sont supprimés et que votre organisation reste sûr et sécurisé.

- **Détection de programme malveillant**<br>La détection de programme malveillant, progressivement mise en place, **détecte automatiquement les fichiers malveillants dans votre stockage cloud**, quel que soit le type de fichier. Microsoft Cloud App Security utilise la Threat Intelligence de Microsoft pour savoir si certains fichiers sont associés à des attaques par programme malveillant connues ou s’ils sont potentiellement dangereux. Pour plus d’informations, consultez [Stratégies de détection d’anomalie](anomaly-detection-policy.md).

- **Correction automatisée des activités suspectes**<br>Vous pouvez désormais définir des actions de correction automatique pour une session suspecte, qui sont déclenchées par les stratégies de détection d’anomalie. Cette amélioration vous permet d’être alerté instantanément lorsqu’une violation se produit et d’**appliquer automatiquement des actions de gouvernance**, comme suspendre l’utilisateur. Pour plus d’informations, consultez [Stratégies de détection d’anomalie](anomaly-detection-policy.md#adp-automated-gov).

- **Évaluation de la configuration de la sécurité pour Azure**<br>Microsoft Cloud App Security met progressivement en place la possibilité d’obtenir une évaluation de la configuration de la sécurité de votre environnement Azure et fournit des recommandations s’il manque une configuration et un contrôle de la sécurité. Par exemple, vous êtes averti s’il manque MFA pour les utilisateurs administratifs. Pour plus d’informations, consultez [Intégration de la gestion de la posture de sécurité cloud](security-config.md).

- **Détection automatisée des applications OAuth à risque**<br>En plus d’investiguer les applications OAuth connectées à votre environnement, Microsoft Cloud App Security met progressivement en place la possibilité de définir des notifications automatisées pour vous informer quand une application OAuth répond à certains critères. Par exemple, vous pouvez être automatiquement alerté quand des applications exigent un niveau d’autorisation élevé et que plus de 50 utilisateurs l’ont accordé. Pour plus d’informations, consultez [Stratégies d’autorisation d’application](app-permission-policy.md).

- **Prise en charge de la gestion des fournisseurs MSSP (Managed Security Service Provider)**<br>Microsoft Cloud App Security fournit désormais une meilleure expérience de gestion pour les fournisseurs MSSP. Les utilisateurs externes peuvent maintenant être configurés en tant qu’administrateurs et se voir attribuer [les rôles actuellement disponibles dans Microsoft Cloud App Security](manage-admins.md). De plus, pour autoriser les fournisseurs MSSP à offrir des services sur plusieurs locataires de clients, les administrateurs disposant des droits d’accès sur plus d’un locataire peuvent facilement passer d’un locataire à l’autre au sein du portail. Pour plus d’informations sur la gestion des administrateurs, consultez [Gérer les administrateurs](manage-admins.md).

- **Intégration avec la protection DLP externe en disponibilité générale**<br>Microsoft Cloud App Security vous permet de [tirer parti des investissements existants dans les systèmes de classification tiers](icap-stunnel.md), comme les solutions DLP (Data Loss Prevention), et d’analyser le contenu des applications cloud à l’aide de déploiements existants exécutés dans votre environnement. Pour plus d’informations, consultez [Intégration de la protection DLP externe](icap-stunnel.md).

## <a name="cloud-app-security-release-125"></a>Cloud App Security version 125

Publication : 10 juin 2018

- **Nouvelle fonctionnalité d’investigation basée sur les utilisateurs avec le plus de sessions suspectes :**<br>
Microsoft Cloud App Security a ajouté un nouveau widget d’enquête au tableau de bord qui affiche les principaux utilisateurs en fonction du nombre d’alertes de détection de menace ouvertes. Ce widget d’enquête vous permet de concentrer votre recherche de menace sur les utilisateurs avec le plus grand nombre de sessions suspectes.

- **Prise en charge des compartiments AWS S3 :**<br>
Microsoft Cloud App Security peut désormais détecter les compartiments AWS S3 et leurs niveaux de partage. Vous obtenez ainsi des alertes et une visibilité des compartiments AWS accessibles publiquement. Cela vous permet également de créer des stratégies basées sur les compartiments et d’appliquer la gouvernance automatique. En outre, il existe un nouveau modèle de stratégie disponible appelé **Compartiments S3 (AWS) accessibles publiquement** que vous pouvez utiliser pour créer facilement une stratégie régissant votre stockage AWS. Pour activer ces nouvelles fonctionnalités, assurez-vous de mettre à jour vos applications connectées à AWS en ajoutant les nouvelles autorisations décrites dans [Connecter AWS](connect-aws-to-microsoft-cloud-app-security.md).

- **Privilèges Administrateur basés sur des groupes d’utilisateurs** : Vous pouvez maintenant définir des privilèges Administrateur pour les administrateurs Microsoft Cloud App Security par groupe d’utilisateurs. Par exemple, vous pouvez définir un utilisateur spécifique en tant qu’administrateur des utilisateurs en Allemagne uniquement. Cela permet à l’utilisateur d’afficher et de modifier les informations de Microsoft Cloud App Security uniquement pour le groupe d’utilisateurs « Allemagne - tous les utilisateurs ». Pour plus d’informations, consultez [Gestion des accès d’administration](manage-admins.md).

## <a name="cloud-app-security-release-124"></a>Cloud App Security version 124

Publication : 27 mai 2018

- **Évaluation des risques RGPD ajoutée au catalogue d’applications cloud**<br>
13 nouveaux facteurs de risque ont été ajoutés à Microsoft Cloud App Security. Ces facteurs de risque suivent la checklist RGPD pour vous permettre d’évaluer les applications du catalogue d’applications cloud conformément à la réglementation RGPD.

- **Intégrer le service de classification des données Microsoft**<br>
Microsoft Cloud App Security vous permet désormais d’utiliser le service de classification des données de Microsoft en mode natif pour classer les fichiers dans vos applications cloud. <br>
Le service de classification des données de Microsoft fournit une expérience de protection unifiée sur Office 365, Azure Information Protection et Microsoft Cloud App Security. Il vous permet d’étendre la même infrastructure de classification des données aux applications cloud tierces protégées par Microsoft Cloud App Security, en appliquant les décisions que vous déjà prises à un plus grand nombre d’applications.

- **Se connecter à Microsoft Azure** (déploiement progressif)<br>
Microsoft Cloud App Security étend ses fonctionnalités de surveillance IaaS au-delà d’Amazon Web Services et prend désormais en charge Microsoft Azure. Cela vous permet de vous connecter rapidement et de surveiller tous vos abonnements Azure avec Cloud App Security. Cette connexion vous offre un ensemble puissant d’outils pour protéger votre environnement Azure, notamment :

    - Visibilité de toutes les activités effectuées via le portail

    - Possibilité de créer des stratégies personnalisées pour signaler un comportement non désiré, de protéger automatiquement les utilisateurs présentant des risques en les suspendant ou en les forçant à se reconnecter.

    - Toutes les activités Azure sont contrôlées par notre moteur de détection des anomalies, qui vous signale automatiquement tout comportement suspect dans le portail Azure, notamment les voyages impossibles, les activités de masse suspectes et les activités provenant d’un nouveau pays.<br>

  Pour plus d’informations, consultez [Connecter Azure à Microsoft Cloud App Security](connect-azure-to-microsoft-cloud-app-security.md).

- **Déploiements étendus** (déploiement progressif) <br>
Microsoft Cloud App Security offre aux entreprises la possibilité d’identifier de façon granulaire les utilisateurs à surveiller et à protéger en fonction de l’appartenance à un groupe. Cette fonctionnalité vous permet de sélectionner les utilisateurs dont les activités n’apparaîtront pas pour les applications protégées. La fonctionnalité de surveillance étendue est particulièrement dans les cas suivants :

    - Conformité : si vos réglementations de conformité vous interdisent de surveiller les utilisateurs de certains pays en raison de réglementations locales.

    - Gestion des licences : si vous souhaitez surveiller un nombre restreint d’utilisateurs afin de rester dans les limites de vos licences Microsoft Cloud App Security.
   Pour plus d'informations, consultez [Déploiement étendu](scoped-deployment.md).

- **Alerte de violation d’application pour les applications découvertes**<br>
 Nous proposons désormais une alerte intégrée qui vous avertit en cas de violation d’une des applications découvertes du client. L’alerte précise la date et l’heure de la violation ainsi que les utilisateurs qui ont ouvert l’application, puis vous dirige vers des sources publiques contenant des informations sur cette violation.

- **Nouveau serveur de messagerie**<br>
 Le serveur de messagerie de Cloud App Security a été modifié et utilise d’autres plages d’adresses IP. Pour être certain de recevoir les notifications, ajoutez les nouvelles adresses IP à votre liste verte anti-spam. Pour les utilisateurs qui souhaitent personnaliser leurs notifications, Microsoft Cloud App Security permet de le faire automatiquement à l’aide de MailChimp®, un service de messagerie tiers. Pour obtenir la liste des adresses IP du serveur de messagerie et des instructions sur l’utilisation de MailChimp, consultez les rubriques [Configuration requise pour le réseau](network-requirements.md#mail-server) et [Paramètres de messagerie](mail-settings.md).

## <a name="cloud-app-security-release-123"></a>Cloud App Security version 123

Publication : 13 mai 2018

- **Délimitation des stratégies de détection d’anomalie** :<br>
Les stratégies de détection d’anomalie peuvent désormais être délimitées. Cela vous permet, pour chaque stratégie de détection d’anomalie, d’inclure ou d’exclure certains utilisateurs ou groupes. Par exemple, vous pouvez configurer l’option Activité à partir de pays peu fréquents de manière à ignorer un utilisateur qui voyage fréquemment.

## <a name="cloud-app-security-release-122"></a>Cloud App Security version 122

Publication : 29 avril 2018

- Lancement progressif : Vous pouvez maintenant **définir des privilèges Administrateur pour les administrateurs Microsoft Cloud App Security par application**. Par exemple, vous pouvez définir un utilisateur spécifique en tant qu’administrateur de la Suite G uniquement. Cela permet à l’utilisateur d’afficher et de modifier les informations de Microsoft Cloud App Security uniquement lorsqu’il se rapporte exclusivement à la Suite G. Pour plus d’informations, consultez [Gestion des accès d’administration](manage-admins.md).
- Lancement progressif : Les **rôles d’administrateur Okta sont désormais visibles** dans Microsoft Cloud App Security et sont disponibles pour chaque rôle en tant que balise sous **Paramètres** > **Groupes d’utilisateurs**.

## <a name="cloud-app-security-release-121"></a>Cloud App Security version 121

Publication : 22 avril 2018

- La préversion publique du **contrôle d’application d’accès conditionnel (anciennement appelé Proxy Cloud App Security)** a été enrichie de fonctionnalités qui approfondissent la visibilité et le contrôle de diverses applications. Vous pouvez à présent créer une stratégie de session avec un filtre *Type d’activité*, pour surveiller et bloquer un éventail d’activités propres à l’application. Ce nouveau filtre augmente les fonctionnalités existantes de contrôle de téléchargement de fichiers pour vous fournir un contrôle total sur les applications de votre organisation. Il fonctionne avec l’accès conditionnel Azure Active Directory pour offrir une visibilité en temps réel et un contrôle des sessions utilisateur présentant un risque (par exemple, les sessions avec des collaborateurs B2B ou des utilisateurs d’appareils non gérés). Pour plus d’informations, consultez [Stratégies de session](session-policy-aad.md).
- Lancement progressif : Les **stratégies de détection d’anomalie de Cloud App Security ont été améliorées** de sorte à inclure deux nouveaux types de détection des menaces : l’activité de ransomware et l’activité des utilisateurs en fin de contrat. Cloud App Security a étendu ses capacités de détection de ransomware à la détection d’anomalie pour garantir une couverture plus complète contre les attaques de ransomware complexes. Fort de notre expertise en recherche dans la sécurité visant à identifier les modèles comportementaux qui reflètent des activités de ransomware, Cloud App Security assure une protection complète et solide. L’activité des utilisateurs en fin de contrat vous permet de surveiller les comptes des utilisateurs en fin de contrat, qui ont été peut-être été déprovisionnés des applications d’entreprise, mais qui, dans de nombreux cas, conservent toujours l’accès à certaines ressources de l’entreprise. Pour plus d’informations, consultez [Obtenir instantanément une détection des anomalies et une analytique comportementale](anomaly-detection-policy.md).

## <a name="cloud-app-security-release-120"></a>Cloud App Security version 120

Publication : 8 avril 2018

- Pour Office 365 et Azure AD, nous développons progressivement la possibilité de détecter les applications internes en tant qu’activités de compte d’utilisateur effectuées par les applications Office 365 et Azure AD (internes et externes). Cela vous permet de créer des stratégies qui vous avertissent si une application effectue des activités inattendues et non autorisées.
- Lors de l’exportation d’une liste d’autorisations d’application au format csv, des champs supplémentaires, comme l’éditeur, le niveau d’autorisation et l’utilisation de la Communauté, sont ajoutés pour vous aider dans le processus d’investigation et de conformité.
- L’application connectée ServiceNow a été améliorée pour que les activités de service interne ne soient plus enregistrées comme ayant été effectuées par « Invité » et ne déclenchent plus d’alertes fausses positives. Ces activités sont maintenant représentées par N/A comme toutes les autres applications connectées.

## <a name="cloud-app-security-release-119"></a>Cloud App Security version 119

Date de publication : 18 mars 2018

- La page des plages d’adresses IP contient les adresses IP intégrées qui sont découvertes par Cloud App Security. Cela inclut les adresses IP des services cloud identifiés, comme Azure et Office 365, ainsi que le flux de Threat Intelligence qui enrichit automatiquement les adresses IP avec des informations sur les adresses IP risquées connues.
- Lorsque Cloud App Security tente d’exécuter une action de gouvernance sur un fichier, mais échoue parce que le fichier est verrouillé, il retente automatiquement l’action de gouvernance.

## <a name="cloud-app-security-release-118"></a>Cloud App Security version 118

Date de publication : 4 mars 2018

- Vous pouvez désormais tirer parti de la découverte du Shadow IT de Microsoft Cloud App Security et des fonctions de surveillance de vos propres applications personnalisées propriétaires. La nouvelle possibilité d’ajouter des applications personnalisées à Cloud Discovery vous permet de surveiller l’utilisation des applications et d’être averti des modifications apportées au modèle d’utilisation. Pour plus d’informations, consultez [Protection de vos applications personnalisées](cloud-discovery-custom-apps.md). Cette fonctionnalité est déployée progressivement.

- Les pages **Paramètres** du portail Cloud App Security ont été repensées. La nouvelle conception consolide toutes les pages de paramètres et intègre une fonctionnalité de recherche et un design amélioré.

- Cloud Discovery prend désormais en charge les pare-feu Barracuda F-Series et Barracuda F-Series Firewall Web Log Streaming.

- La fonctionnalité de recherche dans les pages Utilisateur et Adresse IP permet maintenant la saisie semi-automatique, ce qui facilite vos recherches.

- Vous pouvez désormais effectuer des actions en bloc dans les pages Exclure des entités et Exclure une adresse IP. Vous pouvez ainsi sélectionner plus facilement plusieurs utilisateurs, groupes ou adresses IP, et les exclure de l’analyse dans le cadre de la solution Cloud Discovery de votre organisation.

## <a name="cloud-app-security-release-117"></a>Cloud App Security version 117

Date de publication : 20 février 2018

- L’intégration plus poussée de Cloud App Security avec Azure Information Protection vous permet désormais de protéger les fichiers dans G Suite. Cette fonctionnalité en préversion publique vous permet d’analyser et de classifier des fichiers dans G Suite, et d’appliquer automatiquement des étiquettes Azure Information Protection pour la protection. Pour plus d’informations, consultez [Intégration d’Azure Information Protection](azip-integration.md).

- Cloud Discovery prend désormais en charge [Digital Arts i-FILTER](https://www.daj.jp/en/products/if/).

- Le tableau des agents SIEM inclut désormais plus de détails pour faciliter la gestion.

## <a name="cloud-app-security-release-116"></a>Cloud App Security version 116

Date de publication : 4 février 2018
- La stratégie de détection d’anomalie de Cloud App Security a été améliorée grâce à de nouvelles **détections basées sur des scénarios**, notamment les activités de type Voyage impossible, les échecs de tentatives de connexion multiples et les activités provenant d’adresses IP suspectes. Les nouvelles stratégies sont automatiquement activées et fournissent une solution de détection des menaces prête à l’emploi pour votre environnement cloud. En outre, les nouvelles stratégies exposent davantage de données à partir du moteur de détection de Cloud App Security afin d’accélérer le processus d’investigation, et contiennent des menaces permanentes. Pour plus d’informations, consultez [Obtenir instantanément une détection des anomalies et une analytique comportementale](https://docs.microsoft.com/cloud-app-security/anomaly-detection-policy).

- Lancement progressif : Cloud App Security met désormais en corrélation les utilisateurs et leurs comptes dans les applications SaaS. Cela vous permet d’examiner facilement toutes les activités d’un utilisateur, dans toutes ses différentes applications SaaS corrélées, peu importe l’application ou le compte qu’il a utilisé.

- Lancement progressif : Cloud App Security prend désormais en charge plusieurs instances de la même application connectée. Si vous utilisez plusieurs instances, par exemple, Salesforce (une pour le service commercial et une autre pour le département marketing), vous pourrez les connecter à la fois à Cloud App Security et les gérer à partir de la même console pour créer des stratégies granulaires et obtenir une investigation plus approfondie.

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

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)