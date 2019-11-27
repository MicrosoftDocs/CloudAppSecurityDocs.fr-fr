---
title: Archivage des mises à jour précédentes dans Cloud App Security
description: Cet article est une archive qui décrit les mises à jour effectuées dans les versions précédentes de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 185c3a46-ede8-4d58-b232-111807845c8f
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: da7783c7ca1ee206de62be369df2b3059a35aa18
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74460505"
---
# <a name="past-release-archive-of-microsoft-cloud-app-security"></a>Archive des versions précédentes de Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

Cet article est une archive qui décrit les mises à jour effectuées dans les versions précédentes de Cloud App Security. Pour obtenir la dernière liste Nouveautés, consultez [Nouveautés dans Cloud App Security](release-notes.md).

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

- Les stratégies de découverte prennent désormais en charge les balises d’application en tant que condition et en tant qu’action de gouvernance. Cet ajout vous permet d’étiqueter automatiquement les applications nouvellement découvertes avec des étiquettes personnalisées comme **Applications tendancielles**. Vous pouvez également utiliser l’étiquette d’application comme filtre. Par exemple « M’alerter quand une application de la Watchlist a plus de 100 utilisateurs sur une même journée ».

- Le filtre **Heure** a été amélioré pour le rendre plus convivial.

- L’inspection de contenu vous permet désormais de faire la distinction entre le contenu, les métadonnées et le nom de fichier, pour vous permettre de sélectionner l’élément à inspecter.

- Une nouvelle action de gouvernance a été ajoutée pour G Suite. Vous pouvez désormais **Réduire l’accès public** aux fichiers partagés. Cette action vous permet de définir les fichiers publiquement disponibles comme étant accessibles uniquement avec un lien partagé.

- Toutes les activités de connexion OKTA à d’autres applications s’affichent désormais dans Cloud App Security comme provenant d’OKTA. Vous pouvez afficher et filtrer en fonction de l’application cible vers laquelle la connexion a été effectuée dans le champ **Objets d’activité** de l’activité.


### <a name="cloud-app-security-release-110"></a>Cloud App Security version 110

Publiée le 12 novembre 2017

- Désormais en disponibilité générale : nous avons commencé à développer un nouveau mode de déploiement pour le collecteur de journaux. En plus du déploiement actuel par appliance virtuelle, le nouveau collecteur de journaux, sur (conteneur) Docker, peut être installé sous forme de package sur les [machines Ubuntu](discovery-docker.md), à la fois en local et dans Azure. Quand vous utilisez le collecteur Docker, l’ordinateur hôte est détenu par le client, qui peut librement le corriger et le surveiller.

- Grâce au nouveau point d’interrogation bleu dans l’angle, vous avez maintenant accès à la page de documentation Cloud App Security correspondante sur docs.microsoft.com, sur les pages du portail. Chaque lien est contextuel : il vous redirige vers les informations dont vous avez besoin en fonction de la page sur laquelle vous vous trouvez.
- Vous pouvez maintenant envoyer des commentaires sur chaque page du portail Cloud App Security. Le feedback vous permet de signaler des bogues, de demander de nouvelles fonctionnalités et de partager votre expérience directement avec l’équipe Cloud App Security.
- Des améliorations ont été apportées à la capacité de la détection cloud à reconnaître les sous-domaines, afin de vous permettre de mener des examens approfondis sur l’utilisation du cloud de votre organisation. Pour plus d’informations, consultez la page [Utiliser les applications découvertes](discovered-apps.md).

### <a name="cloud-app-security-release-109"></a>Cloud App Security version 109

Publication : 29 octobre 2017 

- Le lancement de la fonctionnalité de proxy Microsoft Cloud App Security est en cours. Le proxy Microsoft Cloud App Security vous fournit les outils dont vous avez besoin pour obtenir une visibilité et un contrôle en temps réel de l’accès à votre environnement cloud et des activités qui y sont effectuées. Par exemple :

  - Évitez les fuites de données en bloquant les téléchargements avant qu’ils ne se produisent.
  - Définissez des règles qui forcent le chiffrement des données stockées dans le cloud et téléchargées à partir du cloud.
  - Obtenez une visibilité sur les points de terminaison non protégés afin de surveiller les opérations réalisées sur les appareils non gérés.
  - Contrôlez l’accès depuis des réseaux hors entreprise ou des adresses IP à risque.
  
  Pour plus d’informations, consultez [Protéger les applications avec le Contrôle d’accès conditionnel aux applications](proxy-intro-aad.md).

- Nous lançons progressivement la possibilité de filtrer en fonction de noms d’activité de service spécifiques. Ce nouveau filtre de type d’activité est plus précis pour vous permettre de surveiller des activités d’application spécifiques, plutôt que des types d’activité plus généraux. Par exemple, vous pouviez filtrer la commande **Exécuter**, mais maintenant, vous pouvez aussi filtrer des applets de commande EXO spécifiques. Le nom de l’activité peut également être vu dans le tiroir Activité sous **Type (dans l’application)** . À terme, cette fonctionnalité va remplacer le filtre de type d’activité.  

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
- Pour vous aider à vous préparer à la mise en conformité au RGPD, nous avons rassemblé les déclarations associées à partir des applications cloud du catalogue. Cela n’affecte pas encore le score de risque des applications, mais fournit un lien vers la page de préparation au RGPD de l’éditeur d’applications, le cas échéant. Microsoft n’a pas vérifié ce contenu et n’est pas responsable de sa validité.

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

- Parce que les informations d’adresse IP sont essentielles pour la quasi-totalité des examens, vous pouvez maintenant afficher les informations détaillées des adresses IP dans le tiroir Activité. Depuis une activité spécifique, vous pouvez désormais cliquer sur l’onglet Adresse IP pour voir des données consolidées sur l’adresse IP. Les données incluent le nombre d’alertes ouvertes pour l’adresse IP spécifique, un graphique de tendance de l’activité récente et une carte des emplacements. Cette fonctionnalité permet une exploration détaillée facile. Par exemple, quand vous recherchez la cause d’alertes Voyage impossible, vous pouvez facilement déterminer où l’adresse IP a été utilisée, et si elle a été ou non impliquée dans des activités suspectes. Vous pouvez effectuer des actions directement dans le tiroir Adresse IP, où vous pouvez marquer une adresse IP comme étant risquée, VPN ou d’entreprise pour faciliter par la suite l’examen et la création de stratégie. Pour plus d’informations, consultez [Insights sur l’adresse IP](activity-filters.md#ip-address-insights)

- Dans Cloud Discovery, vous pouvez désormais utiliser des [formats de fichiers journaux personnalisés](custom-log-parser.md) pour [le chargement automatique des journaux](discovery-docker.md). Ces formats de journaux personnalisés vous permettent d’automatiser facilement le chargement des journaux depuis vos serveurs SIEM (par exemple des serveurs Splunk) ou de tout autre format non pris en charge.

- Les nouvelles actions d’examen d’utilisateur donnent accès à un niveau supplémentaire d’exploration. Dans les pages **Examen**, vous pouvez désormais cliquer avec le bouton droit sur une activité, un utilisateur ou un compte, et appliquer un des nouveaux filtres pour un examen et un filtrage avancés : **Afficher les activités associées**, **Afficher la gouvernance relative**, **Afficher les alertes associées**, **Afficher les fichiers possédés**, **Afficher les fichiers partagés avec cet utilisateur**.

- Le catalogue d’applications cloud contient désormais un nouveau champ de rétention des données après l’arrêt du compte. Ce facteur de risque vous permet de vérifier que vos données sont totalement supprimées après l’arrêt d’un compte dans une application cloud.

- Cloud App Security permet désormais une visibilité améliorée des activités relatives aux objets Salesforce. Les objets incluent les prospects, les comptes, les campagnes, les opportunités, les profils et les incidents. Par exemple, la visibilité de l’accès aux pages de compte vous permet de configurer une stratégie qui vous alerte si un utilisateur affiche un nombre exceptionnellement élevé de pages de compte. Cette fonctionnalité est disponible dans le connecteur d’applications Salesforce, une fois que vous avez activé la surveillance des événements Salesforce dans Salesforce (intégrée à Salesforce Shield).

- La fonctionnalité Ne pas me suivre est désormais disponible pour les clients de la préversion limitée ! Vous pouvez maintenant contrôler les données d’activité de l’utilisateur qui sont à traiter. Cette fonctionnalité vous permet de définir des groupes spécifiques dans Cloud App Security avec « Ne pas me suivre ». Par exemple, vous pouvez désormais décidez de ne traiter aucune donnée d’activité pour les utilisateurs situés en Allemagne ou dans un pays non soumis à une loi de conformité spécifique. Cette fonctionnalité peut être implémentée pour toutes les applications dans Cloud App Security, pour une application spécifique ou même pour une sous-application spécifique. Par ailleurs, cette fonctionnalité peut être utilisée pour faciliter le déploiement progressif de Cloud App Security. Pour plus d’informations ou pour participer à la préversion limitée de cette fonctionnalité, contactez le support ou votre responsable de compte. 

### <a name="cloud-app-security-release-100"></a>Cloud App Security version 100

Publication : 3 juillet 2017

**Nouvelles fonctionnalités**

- **Extensions de sécurité :** Extensions de sécurité est un nouveau tableau de bord pour la gestion centralisée de toutes les extensions de sécurité de Cloud App Security.  Les extensions incluent la gestion des jetons d’API, les agents SIEM et les connecteurs DLP externes. Le nouveau tableau de bord est disponible dans Cloud App Security sous « Paramètres ». 

    - Jetons d’API : Générez et gérez vos propres [Jetons d’API](api-tokens.md) pour intégrer Cloud App Security à des logiciels tiers à l’aide de nos API RESTful. 
    - Agents SIEM : [L’Intégration SIEM](siem.md) était précédemment située directement sous « Paramètres », elle est maintenant disponible sous forme d’onglet dans Extensions de sécurité.
    - DLP externe (préversion) : Cloud App Security vous permet de [tirer parti des investissements existants dans les systèmes de classification tiers](icap-stunnel.md), comme les solutions DLP (Data Loss Prevention), et vous permet d’analyser le contenu d’applications cloud à l’aide de déploiements existants en cours d’exécution dans votre environnement. Contactez votre responsable de compte pour participer à la préversion.

- **Automatiquement approuver/ne pas approuver :** Les nouvelles stratégies de détection d’application permettent à Cloud Discovery de définir automatiquement les applications avec l’étiquette Approuvée/Non approuvée. Cela vous permet d’identifier automatiquement les applications qui sont en violation de la politique et des réglementations de votre organisation, et de les ajouter au script de blocage généré.
- **Étiquettes de fichier Cloud App Security :** Vous pouvez maintenant appliquer des étiquettes de fichier Cloud App Security pour fournir davantage d’insights sur les fichiers analysés. Pour chaque fichier analysé par Cloud App Security DLP, vous pouvez maintenant savoir si les fichiers n’ont pas pu être inspectés parce qu’ils ont été chiffrés ou corrompus. Par exemple, vous pouvez configurer des stratégies pour vous alerter et mettre en quarantaine les fichiers protégés par mot de passe qui sont partagés en externe. Cette fonctionnalité est disponible pour les fichiers analysés après le 3 juillet 2017.

    Vous pouvez filtrer ces fichiers à l’aide du filtre **Étiquettes de classification** > **Cloud App Security** : 

  - **Chiffré par Azure RMS** : les fichiers dont le contenu n’a pas été inspecté, car le chiffrement Azure RMS défini pour ceux-ci.
  - **Chiffré par mot de passe** : les fichiers dont le contenu n’a pas été inspecté, car ils sont protégés par un mot de passe de l’utilisateur.
  - **Fichier corrompu** : les fichiers dont le contenu n’a pas été inspecté, car il n’a pas pu être lu.

- **Insights utilisateur** : L’expérience d’investigation a été mise à niveau pour activer des insights prêts à l’emploi sur l’utilisateur responsable de l’action. En un seul clic, vous pouvez maintenant obtenir, dans le tiroir Activité, une vue d’ensemble complète des utilisateurs, notamment l’endroit à partir duquel ils sont connectés, le nombre d’alertes ouvertes dans lesquelles ils sont impliqués et leurs informations de métadonnées.
- **Insights des connecteurs d’applications :** sous **Connecteurs d’applications**, chaque application connectée inclut désormais un tiroir d’application dans le tableau, qui permet d’explorer plus facilement son état. Les détails fournis indiquent notamment la date de connexion du connecteur d’applications et le dernier contrôle d’intégrité du connecteur. Vous pouvez également surveiller l’état de l’analyse DLP sur chaque application : le nombre total de fichiers inspectés par DLP ainsi que l’état des analyses en temps réel (analyses demandées par rapport aux analyses réelles). Vous pouvez savoir si le taux de fichiers analysés par Cloud App Security en temps réel est inférieur au nombre demandé, et si votre locataire risque de dépasser sa capacité et d’obtenir les résultats DLP avec du retard.

- **Personnalisation du catalogue d’applications cloud :**

  - **Balises d’application** : Vous pouvez désormais créer des balises personnalisées pour les applications. Ces étiquettes peuvent ensuite servir de filtres pour rechercher plus précisément des types spécifiques d’applications que vous voulez examiner. Par exemple, une liste de suivi personnalisée, l’attribution à une division spécifique ou des approbations personnalisées, comme « approuvé par le service juridique ».
  - **Notes personnalisées** : Quand vous passez en revue et évaluez les différentes applications qui ont été découvertes dans votre environnement, vous pouvez maintenant enregistrer votre conclusions et insights dans les Notes.
  - **Score de risque personnalisé** : Vous pouvez désormais remplacer le score de risque d’une application. Par exemple, si le score de risque d’une application est de 8 et qu’il s’agit d’une application approuvée dans votre organisation, vous pouvez changer ce score de risque en 10 pour votre organisation. Vous pouvez également ajouter des notes pour clarifier la justification du changement quand une personne examine l’application.

- **Nouveau mode de déploiement du collecteur de journaux :** nous commençons à lancer un nouveau mode de déploiement qui est désormais disponible pour le collecteur de journaux. En plus du déploiement actuel basé sur l’appliance virtuelle, le nouveau collecteur de journaux basé sur Docker (conteneur) peut être installé comme un package sur les ordinateurs Windows et Ubuntu à la fois localement et dans Azure. Quand vous utilisez le collecteur Docker, l’ordinateur hôte est détenu par le client, qui peut librement le corriger et le surveiller.

**Annonces :**

- Le catalogue d’applications cloud prend désormais en charge plus de 15 000 applications détectables
- Conformité : Cloud App Security est officiellement certifié SOC1/2/3 par Azure. Pour obtenir la liste complète des certifications, consultez les [offres de conformité](https://www.microsoft.com/trustcenter/compliance/complianceofferings) et recherchez Cloud App Security.

**Autres améliorations :** 

- **Amélioration de l’analyse :** Des améliorations ont été apportées au mécanisme d’analyse du journal Cloud Discovery. Les erreurs internes sont beaucoup moins susceptibles de se produire.
- **Formats de journaux attendus :** Le format de journal attendu pour les journaux Cloud Discovery fournit désormais des exemples pour les formats Syslog et FTP.
- **État de chargement du collecteur de journaux :** Vous pouvez maintenant afficher l’état du collecteur de journaux dans le portail et résoudre les problèmes plus rapidement à l’aide des notifications d’état du portail et des alertes système.

### <a name="cloud-app-security-release-99"></a>Cloud App Security version 99

Publication : 18 juin 2017

**Nouvelles fonctionnalités**

- Vous pouvez désormais demander aux utilisateurs de se reconnecter à toutes les applications Office 365 et Azure AD. Demandez cette reconnexion pour corriger de façon rapide et efficace les alertes d’activités suspectes des utilisateurs et les comptes compromis. La nouvelle gouvernance se trouve dans les paramètres de stratégie et les pages d’alerte, à côté de l’option Interrompre la synchronisation de l’utilisateur.
- Vous pouvez désormais rechercher les activités **Ajouter l’attribution de rôle d’emprunt d’identité** dans le journal d’activité. Cette activité vous permet de détecter quand un administrateur a accordé un rôle **Emprunt d’identité de l’application** à un utilisateur ou compte système, à l’aide de l’applet de commande **New-ManagementRoleAssignment**. Ce rôle permet au représentant d’effectuer des opérations en utilisant les autorisations associées au compte d’emprunt d’identité, au lieu des autorisations associées au compte du représentant.
  
**Améliorations de Cloud Discovery :**

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

- Déploiement terminé du RBAC pour les lecteurs de sécurité. Cette fonctionnalité vous permet de gérer les autorisations que vous accordez à vos administrateurs à l’intérieur de la console Cloud App Security. Par défaut, tous les administrateurs Azure Active Directory, les administrateurs généraux Office 365 et les administrateurs de sécurité disposent des autorisations complètes dans le portail. Tous les lecteurs Sécurité dans Azure Active Directory et Office 365 ont un accès en lecture seule dans Cloud App Security. Vous pouvez ajouter des administrateurs ou remplacer des autorisations à l’aide de l’option « Gérer l’accès ». Pour plus d’informations, consultez [Gestion des autorisations d’administration](manage-admins.md).
- Nous déployons maintenant des rapports détaillés d’intelligence des menaces pour les adresses IP à risque détectées par Microsoft Intelligent Security Graph. Quand une activité est effectuée par un botnet, vous voyez le nom du botnet (s’il est disponible) avec un lien vers un rapport détaillé sur ce botnet.
 
### <a name="cloud-app-security-release-97"></a>Cloud App Security version 97

Publication : 24 mai 2017

**Nouvelles fonctionnalités :**

- Examen des fichiers et des violations de stratégie : Vous pouvez maintenant consulter toutes les correspondances de stratégie dans la page Fichiers. En outre, la page Alerte de fichier a été améliorée et inclut désormais un onglet distinct pour l’historique du fichier concerné. L’amélioration vous permet d’explorer l’historique des violations de toutes les stratégies pour ce fichier spécifique. Chaque événement d’historique inclut une capture instantanée du fichier au moment de l’alerte. Il est indiqué si le fichier a été supprimé ou mis en quarantaine.
- L’option [Mise en quarantaine administrateur](use-case-admin-quarantine.md) est désormais disponible en préversion privée pour les fichiers Office 365 SharePoint et OneDrive Entreprise. Cette fonctionnalité vous permet de mettre en quarantaine les fichiers qui correspondent à des stratégies ou de définir une action automatique pour les mettre en quarantaine. La mise en quarantaine supprime les fichiers du répertoire SharePoint de l’utilisateur et copie les originaux à l’emplacement de mise en quarantaine administrateur que vous choisissez.

**Améliorations de Cloud Discovery :**

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

- Poursuite du lancement progressif de l’autorisation Lecteur Sécurité, qui vous permet de gérer les autorisations que vous accordez à vos administrateurs dans la console Cloud App Security. Par défaut, tous les administrateurs généraux Azure Active Directory et Office 365, et les administrateurs de sécurité, disposent des autorisations complètes dans le portail. Tous les lecteurs Sécurité dans Azure Active Directory et Office 365 ont un accès en lecture seule dans Cloud App Security. Pour plus d’informations, consultez [Gestion des autorisations d’administration](manage-admins.md).
- Lancement terminé de la prise en charge de Cloud Discovery pour les analyseurs de journaux définis par l’utilisateur pour les journaux CSV. Cloud App Security propose des outils de délimitation pour mettre en corrélation les colonnes à des données spécifiques, ce qui vous permet de configurer un analyseur pour vos appareils précédemment non pris en charge. Pour plus d’informations, consultez [Analyseur de journaux personnalisés](custom-log-parser.md).

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

   Par exemple, vous pouvez désormais surveiller les utilisateurs qui disposent d’autorisations **SendAs** sur les boîtes aux lettres d’autres utilisateurs et qui peuvent donc envoyer des e-mails en leur nom.


### <a name="cloud-app-security-release-95"></a>Cloud App Security version 95

Publication : 24 avril 2017

**Mises à jour :**

- La page **Comptes** a été mise à jour avec des améliorations qui simplifient la détection des risques. Vous pouvez désormais filtrer plus facilement pour les comptes internes et externes. Voyez en un coup d’œil si un utilisateur dispose des autorisations d’administrateur. Vous pouvez effectuer des actions sur chaque compte pour une application, comme supprimer des autorisations, supprimer des collaborations de l’utilisateur et suspendre l’utilisateur. En outre, les [groupes d’utilisateurs](user-groups.md) importés pour chaque compte sont affichés. 

- Pour les comptes professionnels Microsoft (Office 365 et Azure Active Directory), Cloud App Security regroupe différents identificateurs d’utilisateurs, comme des adresses de proxy, des alias, des SID et d’autres informations sous un même compte. Tous les alias associés à un compte s’affichent sous l’adresse e-mail principale. Selon la liste des identificateurs d’utilisateurs, pour les activités dont l’acteur est un identificateur d’utilisateur, l’acteur s’affiche sous le nom d’utilisateur principal (UPN, User Principal Name). En fonction de l’UPN, les groupes sont affectés et les stratégies appliquées. Cette modification améliore l’examen des activités et réunit toutes les activités associées dans la même session pour les anomalies et les stratégies basées sur des groupes. Cette fonctionnalité sera progressivement déployée au cours du mois suivant.

- La balise Robot a été ajoutée comme un facteur de risque possible dans le rapport intégré Utilisation du navigateur. Maintenant, en plus de l’utilisation du navigateur marquée comme obsolète, vous pouvez voir quand cette utilisation a été effectuée par un robot. 
- Quand vous créez une stratégie de fichier d’inspection du contenu, vous pouvez maintenant définir le filtre pour inclure uniquement les fichiers avec au moins 50 correspondances.

### <a name="cloud-app-security-release-94"></a>Cloud App Security version 94

Publication : 2 avril 2017

**Nouvelles fonctionnalités :**

- Cloud App Security est maintenant intégré à Azure RMS. Vous pouvez protéger vos fichiers dans Office 365 OneDrive et Sharepoint Online avec Microsoft Rights Management, directement à partir du portail Cloud App Security. Vous pouvez activer cette protection dans la page **Fichiers**. Pour plus d’informations, consultez [Intégration à Azure Information Protection](azip-integration.md). La prise en charge d’applications supplémentaires sera proposée dans les prochaines versions.
- Jusqu’à présent, lorsqu’un robot ou un robot d’indexation intervenait sur votre réseau, il était tout particulièrement difficile à identifier. En effet, ces activités ne sont pas effectuées par un utilisateur. Ces robots peuvent exécuter des outils malveillants à votre insu sur les ordinateurs. Mais c’est sans compter Cloud App Security qui vous offre les outils nécessaires pour visualiser l’intervention de ces robots sur votre réseau. Vous pouvez utiliser la nouvelle balise de l’agent utilisateur pour filtrer les activités dans le journal d’activité. La balise de l’agent utilisateur vous permet de filtrer toutes les activités effectuées par les robots. Vous pouvez l’utiliser pour créer une stratégie qui vous alerte à chaque fois que ce type d’activité est détecté. Vous serez informé quand les prochaines versions intégreront cette activité à risque via les alertes de détection d’anomalies. 
- La nouvelle page unifiée des autorisations d’applications vous permet d’examiner plus facilement les autorisations que vos utilisateurs ont accordées à des applications tierces. En cliquant sur **Examiner** > **Autorisations d’applications**, vous pouvez désormais voir une liste de toutes les autorisations que vos utilisateurs ont accordées à des applications tierces. Une page des autorisations d’application par application connectée vous permet de mieux comparer les différentes applications et les autorisations accordées. Pour plus d’informations, voir [Gérer les autorisations d’applications](manage-app-permissions.md).
- Pour faciliter les recherches, vous pouvez filtrer les données directement depuis le tiroir de table.
Dans **Journal d’activité**, les pages **Fichiers** et **Autorisations d’applications** sont maintenant étoffées avec de nouvelles actions contextuelles qui facilitent le processus de recherche. Nous avons également ajouté des liens rapides vers les pages de configuration et nous permettons de copier les données d’un seul clic. Pour plus d’informations, consultez [Utilisation des tiroirs de fichier et d’activité](file-filters.md).
- La prise en charge par Microsoft Teams du déploiement des journaux et des alertes d’activité Office 365 est à présent complète.

### <a name="cloud-app-security-release-93"></a>Cloud App Security version 93

Publication : 20 mars 2017

**Nouvelles fonctionnalités :**

- Vous pouvez maintenant appliquer des stratégies pour inclure ou exclure des groupes d’utilisateurs importés. 
- L’anonymisation de Cloud App Security vous permet désormais de configurer une clé de chiffrement personnalisée. Pour plus d’informations, consultez [Anonymisation de Cloud Discovery](cloud-discovery-anonymizer.md).
- Pour un contrôle plus étendu sur l’administration des utilisateurs et des comptes, vous disposez désormais d’un accès direct aux paramètres des comptes Azure AD pour chaque utilisateur et chaque compte depuis la page **Compte**. Cliquez simplement sur l’engrenage en regard de chaque utilisateur. Cette modification vous permet d’accéder plus facilement à l’administration avancée des utilisateurs, à l’administration des groupes de fonctionnalités, à la configuration de l’authentification multifacteur, aux informations détaillées sur les connexions des utilisateurs et à la possibilité de bloquer les connexions. 
- À partir de maintenant, vous pouvez exporter un script de blocage pour les applications non autorisées via l’API Cloud App Security. Pour plus d’informations sur nos API dans le portail Cloud App Security, cliquez sur le point d’interrogation dans la barre de menus, puis sur **Documentation des API**.
- Le connecteur d’applications Cloud App Security pour ServiceNow a été étendu pour prendre en charge les jetons OAuth (nouveauté pour Genève, Helsinki, Istanbul). Cette modification fournit une connexion d’API plus robuste à ServiceNow, qui ne s’appuie pas sur l’utilisateur du déploiement. Pour plus d’informations, consultez [Connecter ServiceNow à Microsoft Cloud App Security](connect-servicenow-to-microsoft-cloud-app-security.md). Les clients existants peuvent mettre à jour leurs paramètres dans la page du connecteur d’applications ServiceNow.
- Si vous avez configuré d’autres analyseurs DLP tiers, l’état d’analyse DLP affiche individuellement l’état de chaque connecteur de façon à améliorer la visibilité.
- Cloud App Security prend maintenant en charge les activités Microsoft Teams qui sont prises en charge dans le journal d’audit d’Office 365. Cette fonctionnalité est déployée progressivement.
- Pour les événements d’emprunt d’identité Exchange Online, vous pouvez désormais filtrer en fonction du niveau d’autorisation utilisé : délégué, administrateur ou administrateur délégué. Vous pouvez rechercher des événements affichant le niveau d’emprunt d’identité qui vous intéresse dans le **Journal d’activité** en recherchant des objets d' **activité** > **élément**.
- Dans le tiroir des applications sous l’onglet **Autorisations des applications** des applications Office 365, vous pouvez désormais voir l’**Éditeur** de chaque application. Vous pouvez également utiliser l’éditeur comme filtre pour rechercher les autres applications du même éditeur.
- Les adresses IP à risques apparaissent maintenant comme facteur de risque indépendant et non plus pondéré, sous le facteur de risque général **Emplacement**. 
- Quand les étiquettes Azure Information Protection sont désactivées sur un fichier, elles apparaissent désactivées dans Cloud App Security. Les étiquettes supprimées ne sont pas affichées.
 
**Prise en charge supplémentaire de Salesforce :**

- Maintenant, vous pouvez suspendre et rétablir des utilisateurs Salesforce dans Cloud App Security. Cette action peut être effectuée sous l’onglet **Comptes** du connecteur Salesforce. Cliquez sur l’engrenage à la fin de la ligne d’un utilisateur spécifique et sélectionnez**Suspendre** ou **Annuler la suspension**. Vous pouvez également appliquer Suspendre et Annuler la suspension comme action de gouvernance dans le cadre d’une stratégie. Toutes les activités Suspendre et Rétablir effectuées dans Cloud App Security sont consignées dans le [journal de gouvernance](governance-actions.md). 
- Visibilité améliorée sur le partage de contenu Salesforce : vous pouvez désormais voir quels fichiers ont été partagés et avec qui, notamment les fichiers partagés publiquement, les fichiers partagés avec des groupes et les fichiers partagés avec l’ensemble du domaine Salesforce. Cette meilleure visibilité sera déployée rétroactivement sur les applications Salesforce connectées nouvelles et actuelles : la première mise à jour peut nécessiter un certain temps.
- Nous avons amélioré la couverture des événements Salesforce suivants et nous les avons séparés de l’activité **Gérer les utilisateurs** : 
  - Modifier les autorisations
  - Créer un utilisateur
  - Changer de rôle
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

- Le système Cloud App Security envoie maintenant des alertes pour les erreurs de connectivité de l’agent SIEM. Pour plus d’informations, consultez [Intégration de SIEM](siem.md).

- Cloud App Security prend maintenant en charge les activités suivantes :

  - **Office 365, SharePoint/OneDrive** : Mettre à jour la configuration de l’application, Supprimer le propriétaire du groupe, Supprimer le site, Créer un dossier

  - **Dropbox** : Ajouter un membre au groupe, Supprimer un membre dans le groupe, Créer un groupe, Renommer un groupe, Renommer un membre du groupe

  - **Box** : Supprimer un élément dans le groupe, Mettre à jour le partage d’élément, Ajouter un utilisateur au groupe, Supprimer un utilisateur dans le groupe

### <a name="cloud-app-security-release-89"></a>Cloud App Security version 89

Publiée le 22 janvier 2017

**Nouvelles fonctionnalités :**

- Nous commençons à déployer la possibilité de voir les événements DLP du Centre de sécurité et de conformité Office 365 dans Cloud App Security. Si vous avez configuré des stratégies DLP dans le Centre de sécurité et de conformité Office 365, vous pouvez voir les correspondances de stratégie dans le journal des activités de Cloud App Security quand elles sont détectées. Les informations contenues dans le journal des activités comprennent le fichier ou l’e-mail qui a déclenché la correspondance, ainsi que la stratégie ou l’alerte correspondante. L’activité **Événement de sécurité** vous permet de voir les correspondances de stratégie DLP d’Office 365 dans le journal des activités de Cloud App Security. Avec cette fonctionnalité, vous pouvez :
  - Voir toutes les correspondances DLP provenant du moteur DLP d’Office 365.
  - Alerter sur des correspondances de stratégie DLP d’Office 365 pour un fichier, un site SharePoint ou une stratégie spécifique.
  - Examiner les correspondances DLP avec un contexte plus large, par exemple étendu aux utilisateurs externes qui ont accédé à ou téléchargé un fichier qui a déclenché une correspondance de stratégie DLP.

- Les descriptions des activités ont été améliorées pour plus de clarté et de cohérence. Chaque activité comporte désormais un bouton de feedback. Si vous ne comprenez pas quelque chose ou que vous avez une question, vous pouvez nous le faire savoir.
 
**Améliorations :**

- Une nouvelle action de gouvernance a été ajoutée pour Office 365, qui vous permet de supprimer tous les utilisateurs externes d’un fichier. Par exemple, cette action vous permet d’implémenter des stratégies qui **suppriment les partages externes des fichiers avec une classification exclusivement interne**.
- Amélioration de l’identification des utilisateurs externes dans SharePoint Online. Lors du filtrage du groupe « utilisateurs externes », le compte système app@"sharepoint" n’apparaît pas.


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
- Une nouvelle action de gouvernance de fichier a été ajoutée, qui vous permet de forcer un fichier à hériter des autorisations du parent, supprimant toutes les autorisations individuelles qui ont été définies pour le fichier ou le dossier. Cette action de gouvernance de fichier vous permet de changer les autorisations de votre fichier ou dossier qui doivent être héritées du dossier parent. 
- Un nouveau groupe d’utilisateurs nommé Externe a été ajouté. Il s’agit d’un groupe d’utilisateurs par défaut qui est préconfiguré par Cloud App Security de façon à inclure tous les utilisateurs qui ne font pas partie de vos domaines internes. Vous pouvez utiliser ce groupe d’utilisateurs comme filtre. Par exemple, vous pouvez rechercher les activités effectuées par des utilisateurs externes.
- La fonctionnalité Cloud Discovery prend maintenant en charge les appliances Sophos Cyberoam.
 
**Résolutions de bogues :**

- Les fichiers SharePoint Online et OneDrive Entreprise apparaissaient dans le rapport Stratégie de fichier et dans la page Fichiers comme internes au lieu de privés. Ce bogue a été corrigé.

### <a name="cloud-app-security-release-86"></a>Cloud App Security version 86

Publication le 13 décembre 2016

**Nouvelles fonctionnalités :**

- Toutes les licences autonomes Cloud App Security vous permettent d’activer les analyses Azure Information Protection à partir des paramètres généraux (sans qu’il soit nécessaire de créer une stratégie). 
 
**Améliorations :**

- Vous pouvez maintenant utiliser « ou » dans le filtre de fichiers pour le nom de fichier et le filtre de type MIME pour les fichiers et les stratégies. Cette modification permet des scénarios comme la saisie du mot « passeport » OU « pilote » lors de la création d’une stratégie pour les données personnelles. Le filtre établit une correspondance avec tout fichier ayant « passeport » ou « pilote » dans son nom.
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

- Quand l’analyse DLP échoue, vous recevez maintenant une explication des raisons pour lesquelles Cloud App Security n’a pas pu analyser le fichier. Pour plus d’informations, voir [Inspection du contenu](https://aka.ms/aka.ms/cas-contentinspection).
- Des améliorations ont été apportées aux moteurs de détection des anomalies, notamment pour les alertes de voyage impossible.
- Des améliorations ont été apportées à l’expérience qui permet d’ignorer les alertes. Vous pouvez également ajouter un feedback qui permet à l’équipe Cloud App Security de savoir si l’alerte était intéressante et pourquoi. Votre feedback est utilisé pour améliorer les détections de Cloud App Security.
- Les analyseurs Cloud Discovery Cisco ASA ont été améliorés.
- Vous recevez maintenant une notification par e-mail quand le chargement manuel de votre journal Cloud Discovery est terminé.

### <a name="cloud-app-security-release-79"></a>Cloud App Security version 79

Publication : 21 août 2016 

**Nouvelles fonctionnalités :**

- **Nouveau tableau de bord Cloud Discovery**  : un tout nouveau tableau de bord Cloud Discovery est disponible, conçu pour vous donner plus d’informations sur l’utilisation des applications cloud dans votre organisation. Il fournit une vue d’ensemble en un clin d’œil des types d’applications utilisés, des alertes ouvertes et des niveaux de risque des applications dans votre organisation. Il vous permet également de connaître les principaux utilisateurs des applications dans votre organisation et fournit un plan du lieu du siège social d’une application. Le nouveau tableau de bord présente davantage d’options pour filtrer les données et vous permettre ainsi de générer des vues spécifiques selon ce qui vous intéresse le plus, et des graphiques faciles à comprendre pour vous donner une vision globale en un clin d’œil.

- **Nouveaux rapports Cloud Discovery** : pour voir les résultats de Cloud Discovery, vous pouvez désormais générer deux types de rapports : les rapports d’instantanés et les rapports continus. Les rapports d’instantanés fournissent une visibilité ad hoc sur un ensemble de journaux de trafic que vous chargez manuellement à partir de vos pare-feu et proxys. Les rapports continus présentent les résultats de tous les journaux qui sont transférés à partir de votre réseau à l’aide des collecteurs de journaux de Cloud App Security. Ces nouveaux rapports offrent une meilleure visibilité sur toutes les données, l’identification automatique d’une utilisation anormale par le moteur de détection des anomalies Machine Learning de Cloud App Security ainsi que l’identification d’une utilisation anormale, telle que vous l’avez définie avec le moteur de stratégie robuste et granulaire. Pour plus d’informations, consultez [Configurer Cloud Discovery](set-up-cloud-discovery.md).
 
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
- De nouvelles étiquettes d’adresses IP ont été ajoutées pour Office 365 ProPlus, OneNote, Office Online et Exchange Online Protection.
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

-  Améliorations de l’apparence générale et de l’infrastructure, notamment :

   - Nouveau diagramme pour une meilleure assistance pour le processus de chargement manuel du manuel Cloud Discovery.
   - Amélioration du processus de mise à jour des fichiers journaux non reconnus (« Autres »). Ce processus inclut une fenêtre contextuelle qui vous permet de savoir que le fichier nécessite une révision supplémentaire. Vous êtes averti quand les données sont disponibles.
   - Plus de violations d’activités et de fichiers sont signalées lors de l’examen d’un journal d’activité et de fichier en cas de navigateurs et de systèmes d’exploitation obsolètes.

- Des analyseurs de fichiers journaux Cloud Discovery optimisés, avec notamment l’ajout de Cisco ASA, Cisco FWSM, Cisco Meraki et W3C.
- Résolution de problèmes connus avec Cloud Discovery.
- De nouveaux filtres d’activité ont été ajoutés au domaine du propriétaire et à l’affiliation interne/externe.
- Un nouveau filtre a été ajouté pour rechercher tout objet Office 365 (fichiers, dossiers, URL).
- La possibilité de configurer un score de risque minimal pour les stratégies de détection d’anomalie a été ajoutée.
- Lorsque vous définissez l’envoi d’une alerte en cas de violation d’une stratégie, vous pouvez maintenant définir un niveau de gravité minimal à partir duquel vous souhaitez être alerté. Vous pouvez choisir d’utiliser pour cela les paramètres par défaut de votre organisation et définir un paramètre d’alerte spécifique comme valeur par défaut pour votre organisation.

### <a name="next-steps"></a>Étapes suivantes 

[!INCLUDE [Open support ticket](includes/support.md)]  
  
  
