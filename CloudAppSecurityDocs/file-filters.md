---
title: "Présentation des données et des filtres de fichiers disponibles dans Cloud App Security | Microsoft Docs"
description: "Cette rubrique de référence fournit des informations sur les types de fichiers et les filtres de fichiers utilisés par Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/3/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: cadcd6db-05b2-4974-91fe-cfac3d57aecd
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: a93e9ac3c98dbbe2fef09419afe58c158ec96337
ms.sourcegitcommit: 34cd68651b5a1be9bc460d7175bc2711efa103b2
ms.translationtype: HT
ms.contentlocale: fr-FR
---
# <a name="files"></a>Fichiers


Pour garantir la protection des données, Cloud App Security vous permet de visualiser tous les fichiers de vos applications connectées. Une fois connecté à une application à l’aide du connecteur d’applications, Cloud App Security analyse tous les fichiers, par exemple tous les fichiers stockés dans OneDrive et Salesforce. Cloud App Security analyse ensuite chaque fichier dès qu’une modification est apportée (à son contenu, à ses métadonnées ou à ses autorisations de partage). Les durées des analyses varient en fonction du nombre de fichiers stockés dans votre application. Vous pouvez également utiliser la page **Fichiers** pour filtrer les fichiers et examiner le genre des données enregistrées dans vos applications cloud. 

Par exemple, si vous voulez utiliser la page **Fichiers** pour sécuriser des fichiers partagés en externe et étiquetés comme **confidentiels**, procédez comme suit : après avoir connecté une application à Cloud App Security, vous pouvez procéder à l’intégration à Azure Information Protection. Ensuite, dans la page **Fichiers**, filtrez les fichiers étiquetés comme **confidentiels**. Si vous constatez que des fichiers **confidentiels** sont partagés à l’extérieur de votre organisation en excluant votre domaine via le filtre **Collaborateurs**, vous pouvez créer une stratégie de fichier qui détecte les fichiers **confidentiels** avec des niveaux d’accès incorrects et appliquer des actions de gouvernance automatiques, comme **Supprimer des collaborateurs externes** et **Envoyer une synthèse de correspondance de stratégie au propriétaire du fichier** pour éviter la perte de données à votre organisation.

 ![Filtre de fichiers confidentiels](media/file-filter-confidential.png)

Voici un autre exemple de la façon dont vous pouvez utiliser la page **Fichiers**. Pour faire en sorte que personne dans votre organisation ne partage publiquement ou en externe des fichiers qui n’ont pas été modifiés au cours des 6 derniers mois : après avoir connecté une application à Cloud App Security, dans la page **Fichiers**, filtrez les fichiers dont le niveau d’accès est **Externe** ou **Public** et définissez la **Date de dernière modification** à 6 mois auparavant. Vous pouvez créer une stratégie de fichier qui détecte les fichiers publics périmés en cliquant sur **Nouvelle stratégie à partir de la recherche** et appliquer des actions de gouvernance automatique, comme **Supprimer des utilisateurs externes**, pour éviter une perte de données à votre organisation.

 ![Filtre de fichiers périmés externes](media/file-example-stale-external.png)

Le filtre de base fournit des outils efficaces pour démarrer le filtrage de vos fichiers.

 ![filtre de journal de fichiers de base](media/file-log-filter-basic.png)

Pour explorer des fichiers plus spécifiques, vous pouvez développer le filtre de base en cliquant sur Avancé.

 ![filtre de journal de fichiers avancé](media/file-log-filter-advanced.png)
 
###  <a name="Filefilters"></a> Filtres de fichiers 
 
Cloud App Security peut surveiller n’importe quel type de fichier en fonction de plus de 20 filtres de métadonnées (par exemple, niveau d’accès, type de fichier). 
 
Les moteurs intégrés de protection contre la perte de données (DLP) de Cloud App Security effectuent l’inspection du contenu en extrayant le texte des types de fichiers courants (PDF, fichiers Office, RTF, HTML, fichiers de code, etc.).

Vous trouverez ci-dessous la liste des filtres de fichiers qui peuvent être appliqués. La plupart des filtres prennent en charge plusieurs valeurs, ainsi que NOT, afin de vous fournir un outil très puissant pour créer des stratégies.  
> [!NOTE] 
> Quand vous utilisez des filtres de stratégie de fichier, le filtre **Contains (Contient)** recherche uniquement des **mots entiers** séparés par des virgules, points, espaces ou traits de soulignement. 
> - Les espaces entre les mots agissent comme l’opérateur OR. Par exemple, si vous recherchez **malware** **virus**, le filtre trouve tous les fichiers dont le nom contient malware ou virus. Il trouve donc malware-virus.exe et virus.exe.  
> - Si vous souhaitez rechercher une chaîne, placez les mots entre guillemets. Ceux-ci fonctionnent comme l’opérateur AND. Ainsi, si vous recherchez **"malware"** **"virus"**, le filtre trouve virus_malware_file.exe, mais pas malwarevirusfile.exe et malware.exe. Toutefois, il recherche la chaîne exacte. Si vous recherchez **"malware virus"**, il ne trouve ni **"virus"** ni **"virus_malware"**.

>**Equals (Est égal à)** recherche uniquement la chaîne complète ; par exemple, si vous recherchez **malware.exe**, il trouve malware.exe, mais pas malware.exe.txt. 

-   Niveau d’accès : Niveau d’accès de partage, à savoir public, externe, interne ou privé.  Pour plus d’informations sur les fichiers externes, voir [Configuration générale, Configurer le portail](getting-started-with-cloud-app-security.md). Les fichiers internes sont tous les fichiers dans les domaines internes que vous définissez dans [Configuration générale](General-setup.md). Les fichiers externes sont tous les fichiers enregistrés à des emplacements hors des domaines internes que vous définissez. Les fichiers partagés ont un niveau de partage au-dessus du niveau privé, ce qui inclut le partage interne (fichiers partagés au sein de vos domaines internes), le partage externe (fichiers partagés dans des domaines qui ne figurent pas dans vos domaines internes), les fichiers publics avec un lien (fichiers qui peuvent être partagés avec tout le monde via un lien) et les fichiers publics (fichiers accessibles via une recherche sur Internet). 

> [!NOTE]
>  Les fichiers partagés dans vos applications de stockage connectées par des utilisateurs externes sont gérées comme suit par Cloud App Security :
> - **OneDrive :** OneDrive attribue un utilisateur interne en tant que propriétaire de tout fichier placé dans votre OneDrive par un utilisateur externe. Étant donné que ces fichiers sont alors considérés comme appartenant à votre organisation, Cloud App Security les analyse et applique des stratégies comme à tout autre fichier dans OneDrive.
> - **Google Drive :** Google Drive les considère comme appartenant à l’utilisateur externe et, en raison de restrictions légales sur les fichiers et données qui ne sont pas la propriété de votre organisation, Cloud App Security n’a pas accès à ces fichiers.
> - **Box :** étant donné que Box considère les fichiers appartenant à des sources externes comme des informations privées, ses administrateurs généraux ne peuvent pas afficher le contenu des fichiers. Pour cette raison, Cloud App Security n’a pas accès à ces fichiers. 
> - **Dropbox :** étant donné que Dropbox considère les fichiers appartenant à des sources externes comme des informations privées, ses administrateurs généraux ne peuvent pas afficher le contenu des fichiers. Pour cette raison, Cloud App Security n’a pas accès à ces fichiers.

-   Application : Recherchez uniquement des fichiers au sein de ces applications.  
  
-   Collaborateurs : Incluez/Excluez des groupes de collaborateurs spécifiques.  
  
    -   Un du domaine : Si un utilisateur de ce domaine a accès au fichier.  
  
    -   Domaine complet : Si l’ensemble du domaine a accès au fichier.  
  
    -   Groupes : Si un groupe spécifique a accès au fichier. Les groupes peuvent être importés à partir d’Active Directory ou d’applications cloud ou encore créés manuellement dans le service.  
  
    -   Utilisateurs : Un certain ensemble d’utilisateurs qui peuvent accéder au fichier.  
  
-   Date de création : Date de création du fichier. Le filtre prend en charge des dates antérieures/ultérieures ainsi qu’une plage de dates.  
  
-   Extension : Concentrez-vous sur des extensions de fichier spécifiques, par exemple tous les fichiers exécutables (exe).  
  
-   ID de fichier : Recherchez des ID de fichier spécifiques. Il s’agit d’une fonctionnalité avancée qui vous permet d’effectuer le suivi de certains fichiers de valeur sans dépendre de leur propriétaire/emplacement/nom.  
  
-   Nom de fichier : Nom de fichier ou sous-chaîne du nom comme défini dans l’application cloud, par exemple, Tous les fichiers avec un mot de passe dans leur nom.   
  
-   Étiquette de classification : rechercher des fichiers avec des balises spécifiques définies par Azure Information Protection. Une intégration à Azure Information Protection est alors nécessaire.

-   Type de fichier : Cloud App Security accepte le type MIME reçu du service et analyse le fichier pour déterminer le type de fichier réel. Notez que cette analyse concerne les fichiers qui sont appropriés pour l’analyse de données (documents, images, présentations, feuilles de calcul, fichiers texte et compressés/d’archive). Le filtre fonctionne selon le type de fichier/dossier, par exemple Tous les dossiers qui... ou Tous les fichiers de feuille de calcul qui...


 ![mettre à la corbeille des filtres policy_file](./media/policy_file-filters-trash.png "mettre à la corbeille des filtres policy_file")  

  
-   Dans la Corbeille : Excluez/Incluez des fichiers dans le dossier Corbeille. Ces fichiers peuvent quand même être partagés et représentent un risque.  
  
-   Dernière modification : Date de modification du fichier. Le filtre prend en charge des dates antérieures/ultérieures, une plage de dates et des expressions temporelles relatives comme Tous les fichiers qui n’ont pas été modifiés au cours des 6 derniers mois.  

-   Stratégie de mise en correspondance : fichiers qui sont mis en correspondance par une stratégie Cloud App Security active.

-   Type MIME : Vérification du type MIME de fichier, accepte le texte libre.  
  
-   Propriétaire : Incluez/Excluez des propriétaires de fichiers spécifiques, par exemple Suivre tous les fichiers partagés par employé_non autorisé_#100.  
  
-   UO propriétaire : Incluez/Excluez les propriétaires de fichiers qui appartiennent à certains groupes d’organisation, par exemple Tous les fichiers publics à l’exception de ceux partagés par EMEA_marketing.  
  
-   Dossier parent : Incluez/Excluez selon le dossier parent, par exemple Tous les fichiers partagés publiquement à l’exception des fichiers contenus dans ce dossier.  
  
-   En quarantaine : Le fichier est-il en mis quarantaine par le service ? Par exemple, Afficher tous les fichiers mis en quarantaine.  
  
Vous pouvez également définir la stratégie pour qu’elle s’exécute sur des fichiers spécifiques en définissant le filtre **Appliquer à** sur Tous les fichiers, Dossiers sélectionnés ou Tous les fichiers excepté les dossiers sélectionnés, puis sélectionnez les fichiers ou dossiers concernés.  
  
![filtre Appliquer à](./media/apply-to-filter.png "filtre Appliquer à")  
  
## <a name="working-with-the-file-drawer"></a>Utilisation du tiroir de fichier

Vous pouvez afficher plus d’informations sur chaque fichier en cliquant sur le fichier lui-même dans le journal des fichiers. Cette opération ouvre le tiroir de fichier qui contient les actions supplémentaires suivantes que vous pouvez réaliser sur le fichier :

- URL : Pointe vers l’emplacement du fichier.
- Identificateurs de fichier : Cliquez sur les identificateurs de fichier pour ouvrir une fenêtre contextuelle avec des détails en données brutes sur le fichier, notamment l’ID du fichier et les clés de chiffrement.
- Propriétaire : Cliquez sur le propriétaire pour afficher la page de l’utilisateur pour le propriétaire de ce fichier.
- Stratégies correspondantes : Cliquez sur le lien Stratégies correspondantes pour afficher la liste des stratégies correspondant à ce fichier.
- Étiquette de classification : cliquez sur l’étiquette de Classification pour afficher la liste des étiquettes de classification Azure Information Protection trouvées dans ce fichier. Vous pouvez ensuite appliquer un filtre selon tous les fichiers correspondant à cette étiquette.    

Les champs du tiroir de fichier fournissent des liens contextuels vers des fichiers supplémentaires et permettent d’effectuer un zoom avant, directement dans le tiroir. Par exemple, si vous déplacez votre curseur à côté du champ **Propriétaire**, vous pouvez utiliser l’icône ajouter au filtre ![ajouter au filtre](./media/add-to-filter-icon.png) pour ajouter le propriétaire immédiatement au filtre de la page actuelle. Vous pouvez également utiliser l’icône de roue dentée paramètres ![icône paramètres](./media/contextual-settings-icon.png) qui s’affiche pour accéder directement à la page des paramètres nécessaire pour modifier la configuration de l’un des champs, par exemple les **étiquettes de classification**.


![tiroir de fichier](./media/file-drawer.png "tiroir de fichier")  
  
Pour obtenir la liste des actions de gouvernance disponibles, consultez [Actions de gouvernance sur des fichiers](governance-actions.md#file-governance-actions).

## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  
