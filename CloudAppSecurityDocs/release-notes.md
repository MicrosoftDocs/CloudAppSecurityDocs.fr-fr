---
title: Notes de publication | Documentation Microsoft
description: "Cette rubrique est mise à jour fréquemment pour vous informer des nouveautés de la dernière version de Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 4949ab4f-22c3-4371-b2dc-c8422a097dfe
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: 6f204a955d3186013691fe876e185286a55dd8af


---

# <a name="release-notes"></a>Notes de publication

## <a name="cloud-app-security-release-82"></a>Cloud App Security version 82
Publication : 9 octobre 2016

**Améliorations**

- Les activités **Change email** (Modifier l’e-mail) et **Modifier le mot de passe** sont maintenant indépendantes de l’activité générique **Manage users** (Gérer les utilisateurs) dans Salesforce.
- Ajout d’une clarification concernant la limite d’alerte quotidienne par SMS. 10 messages au maximum sont envoyés par numéro de téléphone par jour (UTC).
- Un nouveau certificat a été ajouté aux attributs Cloud Discovery pour le bouclier de protection des données qui a remplacé la mesure Safe Harbor (fournisseurs aux États-Unis uniquement).
- La résolution des problèmes a été ajoutée aux messages d’erreur concernant les connecteurs API pour faciliter les actions correctives.
- Amélioration de la fréquence des mises à jour de l’analyse des applications tierces Office 365.
- Améliorations apportées au tableau de bord Cloud Discovery.
- L’analyseur Syslog de point de contrôle a été amélioré.
- Améliorations apportées au journal de gouvernance pour l’exclusion et l’annulation de l’exclusion des applications tierces.
 
**Résolutions de bogues**
 
- Processus amélioré pour le chargement d’un logo.
 
## <a name="cloud-app-security-release-81"></a>Cloud App Security version 81
Publication : 18 septembre 2016

**Améliorations**
- Cloud App Security est maintenant une application interne dans Office 365 ! Vous pouvez désormais connecter Office 365 à Cloud App Security en un seul clic.

- Nouveau look pour le journal de gouvernance : il présente maintenant le même aspect clair et utile que le tableau des fichiers et du journal d’activité. Les nouveaux filtres permettent de trouver facilement ce dont vous avez besoin et de surveiller vos actions de gouvernance. 
- Des améliorations ont été apportées au moteur de détection des anomalies en cas de plusieurs échecs de connexion et d’autres facteurs de risque.
- Des améliorations ont été apportées aux rapports d’instantanés Cloud Discovery.
- Des améliorations ont été apportées aux activités administratives dans le journal d’activité ; Modifier le mot de passe, Mettre à jour un utilisateur, Réinitialiser le mot de passe indiquent désormais si l’activité a été effectuée en tant qu’activité administrative.
- Les filtres d’alerte pour les alertes système ont été améliorés. 
- L’étiquette pour une stratégie au sein d’une alerte permet maintenant de revenir au rapport de stratégie.
- Si aucun propriétaire n’est spécifié pour un fichier Dropbox, les e-mails de notification sont envoyés au destinataire que vous définissez. 
- Cloud App Security prend en charge 24 langues supplémentaires, ce qui étend la prise en charge à un total de 41 langues.  


## <a name="cloud-app-security-release-80"></a>Cloud App Security version 80
Publication : 4 septembre 2016 

**Améliorations**
- Quand l’analyse de protection contre la perte de données (DLP) échoue, vous recevez maintenant une explication des raisons pour lesquelles Cloud App Security n’a pas pu analyser le fichier. Pour plus d’informations, voir [Inspection du contenu](https://aka.ms/aka.ms/cas-contentinspection).
- Des améliorations ont été apportées aux moteurs de détection des anomalies, notamment pour les alertes de voyage impossible.
- Des améliorations ont été apportées pour les situations où vous voulez ignorer les alertes ; vous pouvez également ajouter des commentaires afin d’indiquer à l’équipe Cloud App Security si et pourquoi l’alerte était intéressante afin que ces commentaires permettent d’améliorer les détections Cloud App Security.
- Les analyseurs Cloud Discovery Cisco ASA ont été améliorés.
- Vous recevez maintenant une notification par e-mail quand le chargement manuel de votre journal Cloud Discovery est terminé.
   



## <a name="cloud-app-security-release-79"></a>Cloud App Security version 79
Publication : 21 août 2016 

**Nouvelles fonctionnalités**

- **Nouveau tableau de bord Cloud Discovery**  
Un tout nouveau tableau de bord Cloud Discovery est disponible, conçu pour vous donner plus d’informations sur l’utilisation des applications cloud dans votre organisation. Il fournit une vue d’ensemble en un clin d’œil des types d’applications utilisés, des alertes ouvertes et des niveaux de risque des applications dans votre organisation. Il vous permet également de connaître les principaux utilisateurs des applications dans votre organisation et fournit un plan du lieu du siège social d’une application.
Le nouveau tableau de bord présente davantage d’options pour filtrer les données et vous permettre ainsi de générer des vues spécifiques selon ce qui vous intéresse le plus, et des graphiques faciles à comprendre pour vous donner une vision globale en un clin d’œil.

- **Nouveaux rapports Cloud Discovery** Pour afficher les résultats de Cloud Discovery, vous pouvez maintenant générer deux types de rapports, les rapports d’instantanés et les rapports continus.
Les rapports d’instantanés fournissent une visibilité ad hoc sur un ensemble de journaux de trafic que vous chargez manuellement à partir de vos pare-feu et proxys. Les rapports continus présentent les résultats de tous les journaux qui sont transférés à partir de votre réseau à l’aide des collecteurs de journaux de Cloud App Security. Ces nouveaux rapports offrent une meilleure visibilité sur toutes les données, l’identification automatique d’une utilisation anormale identifiée par le moteur de détection des anomalies Machine Learning Cloud App Security ainsi que l’identification d’une utilisation anormale telle que vous l’avez définie avec le moteur de stratégie fiable et granulaire. Pour plus d’informations, voir [Configurer Cloud Discovery](set-up-cloud-discovery.md).
 
**Améliorations**
- Facilité d’utilisation globale améliorée dans les pages suivantes : pages de stratégies, paramètres généraux, paramètres de messagerie.
- Dans la table des alertes, il est maintenant plus facile de faire la distinction entre les alertes lues et non lues. Les alertes lues affichent une ligne bleue sur la gauche et apparaissent grisées pour indiquer que vous les avez déjà lues.
- Les paramètres de la stratégie d’activité **Activité répétée** ont été mis à jour. 
- Dans la page des comptes, une colonne **Type** pour l’utilisateur a été ajoutée et vous pouvez maintenant voir le type de compte d’utilisateur de chaque utilisateur. Les types d’utilisateurs sont spécifiques à l’application. 
- Une prise en charge en temps quasi réel a été ajoutée pour les activités liées aux fichiers dans OneDrive et SharePoint. Quand un fichier est modifié, Cloud App Security déclenche une analyse presque immédiatement.


## <a name="cloud-app-security-release-78"></a>Cloud App Security version 78
Publication : 7 août 2016

**Améliorations**
- À partir d’un fichier spécifique, vous pouvez désormais cliquer avec le bouton droit et **Rechercher des éléments associés**. À partir du journal d’activité, vous pouvez utiliser le filtre d’objet cible et sélectionner le fichier spécifique.

- Des analyseurs de fichiers journaux Cloud Discovery optimisés, avec l’ajout de Juniper et Cisco ASA.
- Cloud App Security vous permet désormais de fournir des commentaires relatifs à l’amélioration des alertes quand vous ignorez l’une d’elles. Vous pouvez aider à améliorer la qualité de la fonctionnalité d’alerte Cloud App Security en nous indiquant pourquoi vous ignorez l’alerte, par exemple parce qu’elle n’est pas intéressante, vous avez reçu un trop grand nombre d’alertes similaires, la gravité réelle doit être inférieure, l’alerte n’est pas exacte.
- Dans la vue de stratégie de fichier, ou quand vous affichez un fichier, quand vous ouvrez le tiroir de fichiers, le nouveau lien vers Stratégies correspondantes a été ajouté. Quand vous cliquez dessus, vous pouvez afficher toutes les correspondances et vous pouvez désormais toutes les ignorer. 
- L’unité d’organisation à laquelle appartient un utilisateur est maintenant ajoutée à toutes les alertes pertinentes.
- Une notification par e-mail est maintenant envoyée pour vous avertir de la fin du traitement de vos journaux chargés manuellement.


## <a name="cloud-app-security-release-77"></a>Cloud App Security version 77
Publication : 24 juillet 2016

**Améliorations :**
- L’icône du bouton Exporter Cloud Discovery a été améliorée pour la facilité d’utilisation.
- Quand vous examinez une activité, si l’agent utilisateur n’a pas été analysé, vous pouvez maintenant voir les données brutes.
- Deux nouveaux facteurs de risque ont été ajoutés au moteur de détection des anomalies : 
    - Cloud App Security utilise désormais les balises d’adresse IP qui sont associées à un botnet et les adresses IP anonymes dans le cadre du calcul de risque. 
    - L’activité Office 365 est maintenant surveillée pour les taux de téléchargements élevés. Si le taux de téléchargement Office 365 est plus important que le taux de téléchargement standard de votre organisation ou d’un utilisateur spécifique, une alerte de détection d’anomalie est déclenchée. 
- Cloud App Security est désormais compatible avec la nouvelle API de [fonctionnalité de partage sécurisé](https://blogs.dropbox.com/dropbox/2016/06/new-dropbox-productivity-tools/) Dropbox. 
- Des améliorations ont été apportées pour ajouter des détails aux erreurs d’analyse du journal Cloud Discovery, notamment : transactions non liées au cloud, tous les événements sont obsolètes, fichier endommagé, pas de correspondance du format de journal.
- Le filtre de date du journal d’activité a été amélioré ; il inclut désormais la possibilité de filtrer par heure.
- La page des plages d’adresses IP a été améliorée pour la facilité d’utilisation.
- Cloud App Security inclut désormais la prise en charge de Microsoft Azure Information Protection (préversion). Vous pouvez filtrer vos fichiers et définir des stratégies de fichier à l’aide de la classification sécurisée des balises, puis définir le niveau de l’étiquette de classification que vous souhaitez afficher. Les étiquettes indiquent également si la classification a été définie par une personne de votre organisation ou d’un autre client (externe). 



## <a name="cloud-app-security-release-76"></a>Cloud App Security version 76
Publication : 10 juillet 2016

**Améliorations :**

- Les listes d’utilisateurs dans les rapports intégrés peuvent maintenant être exportées.
- Facilité d’utilisation améliorée pour la stratégie d’activité agrégée.
- Prise en charge améliorée pour l’analyseur des messages du journal de pare-feu TMG W3C.
- Facilité d’utilisation améliorée pour la liste déroulante des actions de gouvernance des fichiers, qui est désormais répartie en actions de collaboration, actions de sécurité et actions d’examen.
- Détection de voyage impossible améliorée pour l’activité Exchange Online : Envoyer un message.
- Une nouvelle liste de titres (barres de navigation) a été ajoutée en haut des pages d’alertes et de stratégies pour faciliter la navigation.

**Résolutions de bogues :**
- L’expression prédéfinie pour Carte de crédit dans le paramètre DLP pour les stratégies de fichier a été remplacée par Tout : Finance : Carte de crédit.


## <a name="cloud-app-security-release-75"></a>Cloud App Security version 75
Publication : 27 juin 2016


**Nouvelles fonctionnalités :**
* De nouveaux ajouts ont été effectués dans notre liste croissante d’événements Salesforce pris en charge, dont les événements qui fournissent des informations sur les rapports, des liens partagés, la distribution de contenu, une connexion avec emprunt d’identité et bien plus encore.
* Les icônes des applications connectées sur le tableau de bord Cloud App Security ont été alignées sur l’état des applications affichées sur le tableau de bord pour refléter les 30 derniers jours.
* Prise en charge des écrans en pleine largeur.


**Résolutions de bogues :**
* Les numéros de téléphone des alertes par SMS sont maintenant validés lors de l’insertion.

## <a name="cloud-app-security-release-74"></a>Cloud App Security version 74
Publication : 13 juin 2016
* L’écran Alerte a été mis à jour pour vous fournir plus d’informations en un clin d’œil, notamment la possibilité de voir immédiatement toutes les activités de l’utilisateur, une carte des activités, des journaux de gouvernance utilisateur connexes, une description du motif du déclenchement de l’alerte et des graphiques et cartes supplémentaires dans la page de l’utilisateur. 
* Les événements générés par Cloud App Security incluent désormais le type d’événement, le format, les groupes de stratégies, les objets connexes et une description.
* De nouvelles étiquettes d’adresses IP ont été ajoutées pour Office 365 ProPlus, OneNote, Office Online et Exchange Online Protection.
* Vous pouvez désormais charger les journaux à partir du menu de découverte principal.
* Le filtre Catégorie d’adresse IP a été amélioré. La catégorie d’adresse IP null est désormais appelée « non catégorisée » et une nouvelle catégorie appelée « Aucune valeur » a été ajoutée pour regrouper toutes les activités dépourvues de données d’adresse IP.
* Les groupes de sécurité dans Cloud App Security sont maintenant appelées « groupes d’utilisateurs » pour éviter toute confusion avec les groupes de sécurité Active Directory.
* Vous pouvez désormais filtrer par adresse IP et exclure les événements dépourvus d’adresse IP. 
* Des modifications ont été apportées aux paramètres des e-mails de notification qui sont envoyés quand des correspondances sont détectées dans les stratégies d’activité et de fichier. Vous pouvez maintenant ajouter les adresses de messagerie des destinataires auxquels vous souhaitez envoyer une copie (CC) de la notification.


## <a name="cloud-app-security-release-73"></a>Cloud App Security version 73
Publication : 29 mai 2016

* Mise à jour des fonctions d’alerte : vous pouvez maintenant définir des alertes par stratégie à envoyer par e-mail ou SMS.
* Page d’alertes : conception optimisée pour une meilleure gestion des incidents et des options de résolution avancées.
* Ajustement de la stratégie : les alertes vous permettent maintenant de passer des options de résolution d’alerte directement à la page des paramètres de stratégie pour un réglage en fonction des alertes plus facile.
* Améliorations apportées à la détection des anomalies et au calcul du score de risque et réduction du nombre de faux positifs sur la base des commentaires des clients.
* L’exportation du journal d’activité inclut désormais les ID d’événement, la catégorie d’événement et le nom du type d’événement.
* Apparence et convivialité optimisées pour les actions de gouvernance de création de stratégies.
* Examen et contrôle simplifiés pour Office 365 : Office 365 sélectionne automatiquement toutes les applications qui font partie d’une Suite Office 365.
* Les notifications sont désormais envoyées à l’adresse e-mail configurée dans l’application connectée. 
* En cas d’erreur de connexion, une description détaillée de l’erreur est désormais fournie par l’application cloud.
* Lorsqu’un fichier correspond à une stratégie, une URL d’accès au fichier est désormais fournie dans le tiroir de fichiers.
* Lorsqu’une alerte est déclenchée par une stratégie d’activité ou une stratégie de détection des anomalies, une nouvelle notification détaillée est envoyée. Cette dernière fournit des informations sur le résultat. 
* Une alerte système automatique est déclenchée lorsqu’un connecteur d’application est déconnecté.
* Vous pouvez maintenant ignorer et résoudre une alerte ou une sélection en bloc d’alertes à partir de la page des alertes.

## <a name="cloud-app-security-release-72"></a>Cloud App Security version 72
Publication : 15 mai 2016

*  Améliorations de l’apparence générale et de l’infrastructure, notamment :
    * Nouveau diagramme pour une meilleure assistance pour le processus de chargement manuel du manuel Cloud Discovery.
    * Processus optimisé de mise à jour des fichiers journaux non reconnus (« Autre »), notamment une fenêtre contextuelle qui vous indique que le fichier nécessite une révision supplémentaire et que vous serez notifié lorsque les données seront disponibles.
    * Plus de violations d’activités et de fichiers sont signalées lors de l’examen d’un journal d’activité et de fichier en cas de navigateurs et de systèmes d’exploitation obsolètes.
* Des analyseurs de fichiers journaux Cloud Discovery optimisés, avec notamment l’ajout de Cisco ASA, Cisco FWSM, Cisco Meraki et W3C.
* Résolution de problèmes connus avec Cloud Discovery.
* De nouveaux filtres d’activité ont été ajoutés au domaine du propriétaire et à l’affiliation interne/externe.
* Un nouveau filtre a été ajouté pour rechercher tout objet Office 365 (fichiers, dossiers, URL).
* La possibilité de configurer un score de risque minimal pour les stratégies de détection d’anomalie a été ajoutée.
* Lorsque vous définissez l’envoi d’une alerte en cas de violation d’une stratégie, vous pouvez maintenant définir un niveau de gravité minimal à partir duquel vous souhaitez être alerté. Vous pouvez choisir d’utiliser pour cela les paramètres par défaut de votre organisation et définir un paramètre d’alerte spécifique comme valeur par défaut pour votre organisation.

## <a name="see-also"></a>Voir aussi  
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO4-->


