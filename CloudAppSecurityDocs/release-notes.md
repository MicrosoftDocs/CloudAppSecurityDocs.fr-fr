---
title: Notes de publication et versions de Cloud App Security | Microsoft Docs
description: "Cette rubrique est mise à jour fréquemment pour vous informer des nouveautés de la dernière version de Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/7/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: d418ef3d-76ee-45d5-b5ae-21346e5239a3
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 4d65fec131538981f36660d2b5ec668fa11be86e
ms.sourcegitcommit: 945cb3c047ae1bfc05be20cc7798c43005b27c9b
ms.translationtype: HT
ms.contentlocale: fr-FR
---
# <a name="release-notes"></a>Notes de publication


## <a name="cloud-app-security-release-96"></a>Cloud App Security version 96
Publication : 8 mai 2017

Nouvelles fonctionnalités :
-    Lancement progressif de l’autorisation Lecteur Sécurité. Celle-ci vous permet de gérer les autorisations que vous accordez à vos administrateurs dans la console Cloud App Security. Par défaut, tous les administrateurs généraux Azure Active Directory et Office 365 et tous les administrateurs de sécurité disposent d’autorisations complètes dans le portail, tandis que tous les lecteurs Sécurité dans Azure Active Directory et Office 365 disposent d’un accès en lecture seule dans Cloud App Security. Pour plus d’informations, consultez [Gestion des autorisations d’administration](manage-admins.md).
-    Lancement terminé de la prise en charge de Cloud Discovery pour les analyseurs de journaux définis par l’utilisateur pour les journaux CSV. Cloud App Security propose des outils de délimitation pour mettre en corrélation les colonnes à des données spécifiques, ce qui vous permet de configurer un analyseur pour vos appareils précédemment non pris en charge. Pour plus d’informations, consultez [Analyseur de journaux personnalisés](custom-log-parser.md).
Améliorations :
-    Cloud Discovery prend désormais en charge les appareils Juniper SSG.
-    Amélioration de la prise en charge de des journaux Cisco ASA dans Cloud Discovery pour une meilleure visibilité.
-    Agrandissement de la page pour faciliter l’exécution des actions en bloc et la sélection de plusieurs enregistrements dans les tables du portail Cloud App Security.
-    Vous pouvez désormais exécuter les rapports intégrés **Partage sortant par domaine** et **Propriétaires de fichiers partagés** pour les données Salesforce.
-    Nous avons commencé à lancer d’autres activités Salesforce pour vous permettre de suivre les informations pertinentes extraites des données d’activité. Ces activités comprennent l’affichage et la modification des comptes, des prospects, des opportunités ainsi que d’autres objets Salesforce intéressants.
-    De nouvelles activités Exchange ont été ajoutées pour vous permettre de surveiller les autorisations accordées pour les boîtes aux lettres d’utilisateurs ou les dossiers de boîtes aux lettres. Parmi ces activités, citons les suivantes :
    -    Ajouter des autorisations à des destinataires
    -    Supprimer les autorisations de destinataires
    -    Ajouter des autorisations à des dossiers de boîtes aux lettres
    -    Supprimer les autorisations de dossiers de boîtes aux lettres
    -    Définir des autorisations pour des dossiers de boîtes aux lettres

    Par exemple, vous pouvez désormais surveiller les utilisateurs qui disposent d’autorisations **SendAs** sur les boîtes aux lettres d’autres utilisateurs et qui peuvent donc envoyer des e-mails en leur nom.


## <a name="cloud-app-security-release-95-in-roll-out"></a>Cloud App Security version 95 (déploiement)
Publication : 24 avril 2017

**Mises à jour**
- La page **Comptes** a été mise à jour avec des améliorations qui simplifient la détection des risques. Vous pouvez maintenant filtrer plus facilement les comptes internes et externes, voir en un coup d’œil si un utilisateur dispose d’autorisations d’administrateur et savoir si vous pouvez effectuer des actions sur chaque compte simplement par application (telles que supprimer les autorisations, supprimer les collaborations de l’utilisateur, suspendre l’utilisateur). En outre, les [groupes d’utilisateurs](user-groups.md) importés pour chaque compte s’affichent. 

- Pour les comptes professionnels Microsoft (Office 365 et Azure Active Directory), Cloud App Security regroupe différents identificateurs d’utilisateurs tels que des adresses proxy, des alias, des SID, entre autres, sous un compte unique. Tous les alias associés à un compte s’affichent sous l’adresse e-mail principale. Selon la liste des identificateurs d’utilisateurs, pour les activités dont l’acteur est un identificateur d’utilisateur, l’acteur s’affiche sous le nom d’utilisateur principal (UPN, User Principal Name). En fonction de l’UPN, les groupes sont affectés et les stratégies appliquées. Cela améliore l’examen des activités et réunit toutes les activités associées dans la même session pour les anomalies et les stratégies basées sur des groupes. Cette fonctionnalité sera progressivement déployée au cours du mois suivant.

- La balise Robot a été ajoutée comme un facteur de risque possible dans le rapport intégré Utilisation du navigateur. Maintenant, en plus de l’utilisation du navigateur marquée comme obsolète, vous pouvez voir quand cette utilisation a été effectuée par un robot. En savoir plus sur les [rapports intégrés](built-in-report-reference.md).

- Quand vous créez une stratégie de fichier d’inspection du contenu, vous pouvez maintenant définir le filtre pour inclure uniquement les fichiers avec au moins 50 correspondances.



## <a name="cloud-app-security-release-94"></a>Cloud App Security version 94
Publication : 2 avril 2017

**Nouvelles fonctionnalités :**
-    Cloud App Security est maintenant intégré à Azure RMS. Vous pouvez protéger vos fichiers dans Office 365 OneDrive et Sharepoint Online avec Microsoft Rights Management, directement à partir du portail Cloud App Security. Pour y parvenir, accédez à la page **Fichiers**. Pour plus d’informations, voir [Intégration à Azure Information Protection](azip-integration.md). La prise en charge d’applications supplémentaires sera proposée dans les prochaines versions.
-    Jusqu’à présent, lorsqu’un robot ou un robot d’indexation intervenait sur votre réseau, il était tout particulièrement difficile à identifier. En effet, ces activités ne sont pas effectuées par un utilisateur. Ces robots peuvent exécuter des outils malveillants à votre insu sur les ordinateurs. Mais c’est sans compter Cloud App Security qui vous offre les outils nécessaires pour visualiser l’intervention de ces robots sur votre réseau. Vous pouvez utiliser la nouvelle balise de l’agent utilisateur pour filtrer les activités dans le journal d’activité. La balise de l’agent utilisateur vous permet de filtrer toutes les activités effectuées par les robots. Vous pouvez l’utiliser pour créer une stratégie qui vous alerte à chaque fois que ce type d’activité est détecté. Vous serez informé quand les prochaines versions intégreront cette activité à risque par le biais des alertes de détection d’anomalies. 
-    La nouvelle page unifiée des autorisations d’applications vous permet de rechercher plus facilement les autorisations que vos utilisateurs ont accordées à des applications tierces. En cliquant sur **Examiner** > **Autorisations d’applications**, vous pouvez désormais afficher une liste de toutes les autorisations que vos utilisateurs ont accordées à des applications tierces. Vous obtenez une page d’autorisations par application connectée ce qui vous aide à mieux comparer les différentes applications et les autorisations accordées.  Pour plus d’informations, voir [Gérer les autorisations d’applications](manage-app-permissions.md).
-    Pour faciliter les recherches, vous pouvez filtrer les données directement depuis le tiroir de table.
Dans **Journal d’activité**, les pages **Fichiers** et **Autorisations d’applications** sont maintenant étoffées avec de nouvelles actions contextuelles qui facilitent le processus de recherche. Nous avons également ajouté des liens rapides vers les pages de configuration et nous permettons de copier les données d’un seul clic. Pour plus d’informations, voir [Utilisation des tiroirs de fichier et d’activité](file-filters.md).
-    La prise en charge pour Microsoft Teams des journaux d’activité Office 365 et du déploiement des alertes est à présent terminée.
 



## <a name="cloud-app-security-release-93"></a>Cloud App Security version 93
Publication : 20 mars 2017

**Nouvelles fonctionnalités :**
-   Vous pouvez maintenant appliquer des stratégies pour inclure ou exclure des groupes d’utilisateurs importés. 
-    L’anonymisation de Cloud App Security vous permet désormais de configurer une clé de chiffrement personnalisée. Pour plus d’informations, consultez [Anonymisation de Cloud Discovery](cloud-discovery-anonymizer.md).
-    Pour un contrôle plus étendu sur l’administration des utilisateurs et des comptes, vous disposez maintenant d’un accès direct aux paramètres des comptes Azure AD pour chaque utilisateur et chaque compte depuis la page **Compte** en cliquant sur la roue dentée à côté de chaque utilisateur. Vous pouvez ainsi accéder plus facilement à l’administration avancée des utilisateurs, à l’administration des groupes de fonctionnalités, à la configuration de l’authentification multifacteur, aux informations détaillées sur les connexions de l’utilisateur et à la possibilité de bloquer les connexions. 
-    À partir de maintenant, vous pouvez exporter un script de blocage pour les applications non autorisées via l’API Cloud App Security. Pour plus d’informations sur nos API dans le portail Cloud App Security, cliquez sur le point d’interrogation dans la barre de menus et sur **Documentation des API**.
-    Le connecteur d’applications Cloud App Security pour ServiceNow a été étendu pour prendre en charge les jetons OAuth (nouveauté pour Genève, Helsinki, Istanbul). Cela renforce la connexion d’API à ServiceNow, qui ne repose pas sur l’utilisateur du déploiement. Pour plus d’informations, consultez [Connecter ServiceNow à Microsoft Cloud App Security](connect-servicenow-to-microsoft-cloud-app-security.md). Les clients existants peuvent mettre à jour leurs paramètres dans la page du connecteur d’applications ServiceNow.
-    Si vous avez configuré d’autres analyseurs DLP tiers, l’état d’analyse DLP affiche individuellement l’état de chaque connecteur de façon à améliorer la visibilité.
-    Cloud App Security prend maintenant en charge les activités Microsoft Teams qui sont prises en charge dans le journal d’audit d’Office 365. Cette fonctionnalité est déployée progressivement.
-    Pour les événements d’emprunt d’identité Exchange Online, vous pouvez maintenant filtrer par niveau d’autorisation utilisé : délégué, administrateur ou administrateur délégué. Vous pouvez rechercher des événements affichant le niveau d’emprunt d’identité qui vous intéresse dans le **Journal d’activité** en recherchant des **Objets d’activité** > **Élément**.
-    Dans le tiroir des applications sous l’onglet Autorisations des applications, vous pouvez désormais voir **l’Éditeur** de chaque application. Vous pouvez également utiliser l’éditeur comme filtre pour rechercher les autres applications du même éditeur.
-    Les adresses IP à risques apparaissent maintenant comme facteur de risque indépendant et non plus pondéré, sous le facteur de risque général **Emplacement**. 
-    Quand les étiquettes Azure Information Protection sont désactivées sur un fichier, elles apparaissent désactivées dans Cloud App Security. Les étiquettes supprimées ne sont pas affichées.
 
**Prise en charge supplémentaire de Salesforce :**
-    Maintenant, vous pouvez suspendre et rétablir des utilisateurs Salesforce dans Cloud App Security. Vous pouvez effectuer ces opérations dans l’onglet **Comptes** du connecteur Salesforce en cliquant sur la roue dentée à la fin de la ligne d’un utilisateur spécifique, et en sélectionnant **Suspendre** ou **Rétablir**. Vous pouvez également l’appliquer comme action de gouvernance dans le cadre d’une stratégie. Toutes les activités Suspendre et Rétablir effectuées dans Cloud App Security sont consignées dans le [journal de gouvernance](governance-actions.md). 
-    Visibilité améliorée sur le partage de contenu Salesforce : maintenant, vous pouvez voir quels fichiers ont été partagés et avec qui, notamment les fichiers partagés publiquement, les fichiers partagés avec des groupes et les fichiers partagés avec l’ensemble du domaine Salesforce. Cette meilleure visibilité sera déployée rétroactivement sur les applications Salesforce connectées nouvelles et actuelles : la première mise à jour peut nécessiter un certain temps.
-    Nous avons amélioré la couverture des événements Salesforce suivants et nous les avons séparés de l’activité **Gérer les utilisateurs** : 
    - Modifier les autorisations
    - Créer un utilisateur
    - Changer de rôle
    - Réinitialiser le mot de passe

## <a name="cloud-app-security-release-90-91-92"></a>Cloud App Security version 90, 91, 92
Date de publication : février 2017

**Annonce spéciale**

Cloud App Security est maintenant officiellement certifié conforme à ISO, HIPAA, CSA STAR, aux clauses contractuelles types de l’Union européenne et plus encore. Pour consulter la liste complète des certifications, accédez à la page des [offres de conformité Microsoft](https://www.microsoft.com/trustcenter/compliance/complianceofferings) et sélectionnez Cloud App Security.

**Nouvelles fonctionnalités**

-  **Importer des groupes d’utilisateurs (préversion)** Quand vous connectez des applications à l’aide de connecteurs d’API, Cloud App Security vous permet maintenant d’importer des groupes d’utilisateurs à partir d’Office 365 et d’Azure Active Directory. L’importation de groupes d’utilisateurs peut être utile dans les scénarios suivants : vous souhaitez connaître quels documents sont consultés par le service des Ressources Humaines, ou vous voulez vérifier si quelque chose d’inhabituel s’est produit dans le groupe des dirigeants ou si un membre du groupe des administrateurs a effectué une activité en dehors de France. Pour plus d’informations et obtenir des instructions, consultez [Importation de groupes d’utilisateurs](user-groups.md).

-  Dans le journal d’activité, vous pouvez maintenant filtrer les utilisateurs et les utilisateurs dans les groupes pour afficher les activités qui ont été effectuées par un utilisateur donné et celles qui ont été effectuées sur un utilisateur donné. Par exemple, vous pouvez examiner les activités ayant été effectuées par un utilisateur au nom d’autres utilisateurs, et les activités effectuées par d’autres utilisateurs au nom de cet utilisateur. Pour plus d’informations, consultez [Activités](activity-filters.md).

- Quand vous examinez un fichier dans la page **Fichiers** et que vous explorez plus en détail la section **Collaborateurs** du fichier, vous avez maintenant accès à davantage d’informations sur les collaborateurs, notamment s’ils ont le statut Interne ou Externe et s’ils ont les autorisations de fichiers Auteurs ou Lecteurs. De plus, si le fichier est partagé avec un groupe, vous pouvez maintenant afficher tous les utilisateurs qui sont membres du groupe. Cela vous permet de savoir si les membres du groupe sont des utilisateurs externes.

-  La prise en charge IPv6 est désormais disponible pour tous les appareils.

-    Le service Cloud Discovery prend maintenant en charge les appareils Baracuda.

-    Le système Cloud App Security envoie maintenant des alertes pour les erreurs de connectivité de l’agent SIEM. Pour plus d’informations, consultez [Intégration de SIEM](siem.md).

-    Cloud App Security prend maintenant en charge les activités suivantes :

     **Office 365, SharePoint/OneDrive** : Mettre à jour la configuration de l’application, Supprimer le propriétaire du groupe, Supprimer le site, Créer un dossier

     **Dropbox** : Ajouter un membre au groupe, Supprimer un membre dans le groupe, Créer un groupe, Renommer un groupe, Renommer un membre du groupe

     **Box** : Supprimer un élément dans le groupe, Mettre à jour le partage d’élément, Ajouter un utilisateur au groupe, Supprimer un utilisateur dans le groupe


## <a name="cloud-app-security-release-89"></a>Cloud App Security version 89
Publiée le 22 janvier 2017

**Nouvelles fonctionnalités**
-    Nous avons commencé à déployer l’affichage des événements DLP du Centre de sécurité et conformité Office 365 dans Cloud App Security. Si vous avez configuré des stratégies DLP dans le Centre de sécurité et conformité Office 365, vous pouvez voir les correspondances de stratégie dans le journal des activités de Cloud App Security quand elles sont détectées. Les informations contenues dans le journal des activités comprennent le fichier ou l’e-mail qui a déclenché la correspondance, ainsi que la stratégie ou l’alerte correspondante. L’activité **Événement de sécurité** vous permet de voir les correspondances de stratégie DLP d’Office 365 dans le journal des activités de Cloud App Security. Avec cette fonctionnalité, vous pouvez :
    -    Voir toutes les correspondances DLP provenant du moteur DLP d’Office 365.
    -    Alerter sur des correspondances de stratégie DLP d’Office 365 pour un fichier, un site SharePoint ou une stratégie spécifique.
    -    Examiner les correspondances DLP avec un contexte plus large, par exemple étendu aux utilisateurs externes qui ont accédé à ou téléchargé un fichier qui a déclenché une correspondance de stratégie DLP.
 
-    Les descriptions des activités ont été améliorées pour plus de clarté et de cohérence. Chaque activité comprend désormais un bouton Commentaires : si vous ne comprenez pas certaines d’entre elles ou si vous avez des questions sur celles-ci, vous pouvez nous le faire savoir. 
 
**Améliorations**  
-    Une nouvelle action de gouvernance a été ajoutée pour Office 365, qui vous permet de supprimer tous les utilisateurs externes d’un fichier. Par exemple, elle vous permet d’implémenter des stratégies qui **suppriment les partages externes des fichiers avec une classification exclusivement interne**.
-    Amélioration de l’identification des utilisateurs externes dans SharePoint Online. Lors du filtrage du groupe « utilisateurs externes », le compte système app@sharepoint n’apparaît pas.



## <a name="cloud-app-security-release-88"></a>Cloud App Security version 88
Publiée le 8 janvier 2017
 
**Nouvelles fonctionnalités**
- Connectez votre serveur SIEM à Cloud App Security. Vous pourrez désormais envoyer des alertes et des activités automatiquement au serveur SIEM de votre choix en configurant des agents SIEM. Désormais disponible en préversion publique.  Pour une documentation complète et plus d’informations, consultez Intégration à SIEM.
- Cloud Discovery prend désormais en charge IPv6. Nous avons déployé la prise en charge pour Palo Alto et Juniper, et d’autres appareils seront déployés dans les versions ultérieures.
 
**Améliorations**
- Il existe un nouveau facteur de risque dans le catalogue d’applications cloud. Vous pouvez désormais évaluer une application selon qu’elle nécessite ou non l’authentification utilisateur. Les applications qui exigent l’authentification et qui n’autorisent pas l’utilisation anonyme reçoivent un score de risque correspondant à un état plus sain.
- Nous déployons de nouvelles descriptions d’activités plus utilisables et plus cohérentes, qui n’affectent pas la recherche des activités.
- Nous avons inclus une meilleure identification utilisateur-appareil, qui permet à Cloud App Security de documenter un plus grand nombre d’événements avec des informations sur les appareils.
 
## <a name="cloud-app-security-release-87"></a>Cloud App Security version 87
Publication le 25 décembre 2016

**Nouvelles fonctionnalités**
-    Nous sommes en train de mettre à disposition l’[anonymisation des données](cloud-discovery-anonymizer.md) pour vous permettre de bénéficier de Cloud Discovery tout en protégeant la vie privée des utilisateurs. L’anonymisation de données est effectuée en chiffrant les informations des noms d’utilisateur.
-    Nous allons bientôt permettre d’exporter un script de blocage depuis Cloud App Security sur des appliances supplémentaires. Le script vous permet de réduire facilement l’informatique fantôme en bloquant le trafic pour des applications non approuvées. Cette option est maintenant disponible pour : 
    -    BlueCoat ProxySG
    -    Cisco ASA
    -    Fortinet
    -    Juniper SRX
    -    Palo Alto
    -    Websense
-    Une nouvelle action de gouvernance de fichier a été ajoutée, qui vous permet de forcer un fichier à hériter des autorisations du parent, supprimant toutes les autorisations individuelles qui ont été définies pour le fichier ou le dossier. Cette action de gouvernance de fichier vous permet de changer les autorisations de votre fichier ou dossier qui doivent être héritées du dossier parent. 
-    Un nouveau groupe d’utilisateurs nommé Externe a été ajouté. Il s’agit d’un groupe d’utilisateurs par défaut qui est préconfiguré par Cloud App Security de façon à inclure tous les utilisateurs qui ne font pas partie de vos domaines internes. Vous pouvez utiliser ce groupe d’utilisateurs comme filtre : par exemple, vous pouvez rechercher les activités effectuées par des utilisateurs externes.
-    La fonctionnalité Cloud Discovery prend maintenant en charge les appliances Sophos Cyberoam.
 
**Résolutions de bogues**
-    Les fichiers SharePoint Online et OneDrive Entreprise apparaissaient dans le rapport Stratégie de fichier et dans la page Fichiers comme internes au lieu de privés. Ce problème a été corrigé.
 


## <a name="cloud-app-security-release-86"></a>Cloud App Security version 86
Publication le 13 décembre 2016

**Nouvelles fonctionnalités**
- Toutes les licences autonomes Cloud App Security vous permettent d’activer les analyses Azure Information Protection à partir des paramètres généraux (sans qu’il soit nécessaire de créer une stratégie). 
 
**Améliorations**
- Vous pouvez maintenant utiliser « ou » dans le filtre de fichiers pour le nom de fichier et le filtre de type MIME pour les fichiers et les stratégies. Ceci permet des scénarios comme la saisie du mot « passeport » ou « pilote » lors de la création d’une stratégie avec des informations d’identification personnelles, qui mettra en correspondance tout fichier ayant « passeport » ou « pilote » dans son nom de fichier. 
- Par défaut, quand une stratégie d’inspection DLP s’exécute, les données des violations qui en résultent sont masquées. Vous pouvez maintenant afficher les 4 derniers caractères de la violation. 

**Améliorations mineures**
- Nouveaux événements liés à la boîte aux lettres d’Office 365 (Exchange) en relation avec des règles de transfert, et ajout et suppression de boîtes aux lettres déléguées.
- Nouvel événement qui audite l’octroi d’un consentement à de nouvelles applications dans Azure Active Directory. 




## <a name="cloud-app-security-release-85"></a>Cloud App Security version 85
Publiée le 27 novembre 2016

**Nouvelles fonctionnalités**
- Une distinction a été établie entre les applications approuvées et les applications connectées. Vous pouvez désormais appliquer une balise aux applications découvertes et à toutes les applications du catalogue d’applications pour les marquer comme approuvées ou non. Les applications connectées sont des applications que vous avez connectées à l’aide du connecteur d’API pour une meilleure visibilité et un plus grand contrôle. Vous pouvez désormais soit marquer les applications comme approuvées ou non, soit les connecter à l’aide du connecteur d’application, le cas échéant. 
 
- Compte tenu de cette modification, la page des applications approuvées a été remplacée par une nouvelle page **Applications connectées** qui externalise les données d’état sur les connecteurs. 
 
- Les collecteurs de journal sont plus facilement accessibles dans leur propre ligne dans le menu **Paramètres** sous **Sources**. 
- Quand vous créez un filtre de stratégie d’activité, vous pouvez réduire les faux positifs en choisissant d’ignorer les activités répétées quand elles sont exécutées sur le même objet cible par le même utilisateur. Une alerte n’est donc pas déclenchée si la même personne tente plusieurs fois de télécharger le même fichier. 
- Des améliorations ont été apportées au tiroir d’activité. À présent, quand vous cliquez sur un objet d’activité dans le tiroir d’activité, vous pouvez descendre dans la hiérarchie pour obtenir plus d’informations.

**Améliorations**
- Des améliorations ont été apportées au moteur de détection des anomalies, notamment au niveau des alertes de déplacement impossible. Des informations sur l’adresse IP sont désormais disponibles dans la description de l’alerte.
- Des améliorations ont été apportées aux filtres complexes. Vous pouvez ainsi ajouter plusieurs fois le même filtre pour ajuster les résultats filtrés. 
- Les activités liées aux fichiers et aux dossiers dans Dropbox ont été séparées pour une meilleure visibilité. 
  
**Résolutions de bogues**
- Un bogue à l’origine de faux positifs a été résolu dans le mécanisme de déclenchement des alertes système.

## <a name="cloud-app-security-release-84"></a>Cloud App Security version 84
Publiée le 13 novembre 2016

**Nouvelles fonctionnalités**
-    Cloud App Security prend désormais en charge Microsoft Azure Information Protection, notamment une intégration améliorée et l’approvisionnement automatique. Vous pouvez filtrer vos fichiers et définir des stratégies de fichier à l’aide de la classification sécurisée des étiquettes, puis définir l’étiquette de classification que vous voulez afficher. Les étiquettes indiquent également si la classification a été définie par une personne de votre organisation ou d’un autre locataire (externe). Vous pouvez également définir des stratégies d’activité basées sur les étiquettes de classification d’Azure Information Protection et activer l’analyse automatique des étiquettes de classification dans Office 365. Pour plus d’informations sur la façon de tirer parti de cette nouvelle fonctionnalité intéressante, consultez [Intégration à Azure Information Protection](azip-integration.md).
 
**Améliorations**
-    Des améliorations ont été apportées au journal d’activité de Cloud App Security : 
   -    Les événements Office 365 provenant du Centre de sécurité et conformité sont désormais intégrés à Cloud App Security et sont visibles dans le **journal d’activité**.
   -    Toute l’activité de Cloud App Security est enregistrée dans le journal d’activité Cloud App Security comme activité d’administration.
-    Pour vous permettre d’examiner les alertes relatives aux fichiers, dans chaque résultant d’une stratégie de fichier, vous pouvez désormais afficher la liste des activités qui ont été effectuées sur le fichier correspondant.
-    L’algorithme de voyage impossible dans le moteur de détection d’anomalie a été amélioré pour fournir une meilleure prise en charge pour les petits locataires. 
 
**Améliorations mineures**
-    La **limite d’exportation d’activités** a été portée à 10 000. 
-    Quand vous créez un **rapport d’instantané** dans le processus de chargement manuel du journal Cloud Discovery, vous recevez désormais une estimation précise de la durée de traitement du journal. 
-    Dans une stratégie de fichier, l’action de gouvernance **Supprimer le collaborateur** fonctionne désormais sur les groupes.
-    Des améliorations mineures ont été apportées dans la page **Autorisations d’applications**. 
-    Quand plus de 10 000 utilisateurs avaient des autorisations pour une application qui se connecte à Office 365, la liste se chargeait lentement. Ce problème a été résolu.
-    Des attributs supplémentaires ont été ajoutés au **Catalogue d’applications** en ce qui concerne le secteur des cartes de paiement.


## <a name="cloud-app-security-release-83"></a>Cloud App Security version 83
Publication : 30 octobre 2016

**Nouvelles fonctionnalités**
-    Pour simplifier le filtrage dans le [journal d’activité](activity-filters.md) et le [journal de fichier](file-filters.md), les filtres similaires ont été regroupés. Utilisez les filtres d’activité : objet d’activité, adresse IP et utilisateur. Utilisez le filtre de fichier Collaborateurs pour trouver ce dont vous avez besoin.
-    Dans le tiroir du journal d’activité, sous **Source**, vous pouvez cliquer sur le lien **Afficher les données brutes** afin de télécharger les données brutes utilisées pour générer le journal d’activité et ainsi accéder aux événements de l’application. 
-    Prise en charge d’activités de connexion supplémentaires dans Okta. [Private preview]
-    Prise en charge d’activités de connexion supplémentaires dans Salesforce. 

**Améliorations**
-    Plus grande facilité d’utilisation des rapports d’instantané Cloud Discovery et de la résolution des problèmes.
-    Meilleure visibilité des alertes portant sur plusieurs applications dans la liste des alertes.
-    Plus grande facilité d’utilisation lors de la création de nouveaux rapports continus Cloud Discovery.
-    Plus grande facilité d’utilisation dans le journal de gouvernance.



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
-Dans la vue de stratégie de fichier, ou quand vous affichez un fichier, quand vous ouvrez le tiroir de fichiers, le nouveau lien vers Stratégies correspondantes a été ajouté. Quand vous cliquez dessus, vous pouvez afficher toutes les correspondances et vous pouvez désormais toutes les ignorer. 
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
  
  