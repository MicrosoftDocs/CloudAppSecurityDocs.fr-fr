---
title: Fichiers | Documentation Microsoft
description: "Cette rubrique de référence fournit des informations sur les types de fichiers et les filtres de fichiers utilisés par Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/26/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: cadcd6db-05b2-4974-91fe-cfac3d57aecd
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3c342e019dfca316ee89f68de60886d848abdb17
ms.openlocfilehash: f65d64b240eb26f13a70143f5fb84a4f84f4cb6d


---

# <a name="files"></a>Fichiers

Le journal des fichiers peut être filtré pour vous permettre de trouver des fichiers spécifiques. Le filtre de base fournit des outils efficaces pour démarrer le filtrage de vos fichiers.

 ![filtre de journal de fichiers de base](media/file-log-filter-basic.png)

Pour explorer des fichiers plus spécifiques, vous pouvez développer le filtre de base en cliquant sur Avancé.

 ![filtre de journal de fichiers avancé](media/file-log-filter-advanced.png)
 
###  <a name="a-namefilefiltersa-file-filters"></a><a name="Filefilters"></a> Filtres de fichiers 
 
Cloud App Security peut surveiller n’importe quel type de fichier en fonction de plus de 20 filtres de métadonnées (par exemple, niveau d’accès, type de fichier). 
 
Les moteurs intégrés de protection contre la perte de données (DLP) de Cloud App Security effectuent l’inspection du contenu en extrayant le texte des types de fichiers courants (PDF, fichiers Office, RTF, HTML, fichiers de code, etc.).

Vous trouverez ci-dessous la liste des filtres de fichiers qui peuvent être appliqués. La plupart des filtres prennent en charge plusieurs valeurs, ainsi que NOT, afin de vous fournir un outil très puissant pour créer des stratégies.  
> [!NOTE] 
> Quand vous utilisez des filtres de stratégie, le filtre **Contains (Contient)** recherche uniquement des mots entiers, séparés par des virgules, points, espaces ou traits de soulignement. Par exemple, si vous recherchez **malware** ou **virus**, il trouve virus_malware_file.exe, mais pas malwarevirusfile.exe. Si vous recherchez **malware.exe**, vous obtenez tous les fichiers exe dont le nom contient malware ou exe, tandis que si vous recherchez **"malware.exe"** (avec les guillemets), vous n’obtenez que les fichiers dont le nom contient exactement « malware.exe ».  **Equals (Est égal à)** recherche uniquement la chaîne complète ; par exemple, si vous recherchez **malware.exe**, il trouve malware.exe, mais pas malware.exe.txt. 

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
  
-   Balise de fichier : rechercher des fichiers avec des balises spécifiques définies par Azure Information Protection. Une intégration à Azure Information Protection est alors nécessaire.

-   Type de fichier : Cloud App Security accepte le type MIME reçu du service et analyse le fichier pour déterminer le type de fichier réel. Notez que cette analyse concerne les fichiers qui sont appropriés pour l’analyse de données (documents, images, présentations, feuilles de calcul, fichiers texte et compressés/d’archive). Le filtre fonctionne selon le type de fichier/dossier, par exemple Tous les dossiers qui... ou Tous les fichiers de feuille de calcul qui...


 ![mettre à la corbeille des filtres policy_file](./media/policy_file-filters-trash.png "policy_file filters trash")  

  
-   Dans la Corbeille : Excluez/Incluez des fichiers dans le dossier Corbeille. Ces fichiers peuvent quand même être partagés et représentent un risque.  
  
-   Dernière modification : Date de modification du fichier. Le filtre prend en charge des dates antérieures/ultérieures, une plage de dates et des expressions temporelles relatives comme Tous les fichiers qui n’ont pas été modifiés au cours des 6 derniers mois.  

-   Stratégie de mise en correspondance : fichiers qui sont mis en correspondance par une stratégie Cloud App Security active.

-   Type MIME : Vérification du type MIME de fichier, accepte le texte libre.  
  
-   Propriétaire : Incluez/Excluez des propriétaires de fichiers spécifiques, par exemple Suivre tous les fichiers partagés par employé_non autorisé_#100.  
  
-   UO propriétaire : Incluez/Excluez les propriétaires de fichiers qui appartiennent à certains groupes d’organisation, par exemple Tous les fichiers publics à l’exception de ceux partagés par EMEA_marketing.  
  
-   Dossier parent : Incluez/Excluez selon le dossier parent, par exemple Tous les fichiers partagés publiquement à l’exception des fichiers contenus dans ce dossier.  
  
-   En quarantaine : Le fichier est-il en mis quarantaine par le service ? Par exemple, Afficher tous les fichiers mis en quarantaine.  
  
Vous pouvez également définir la stratégie pour qu’elle s’exécute sur des fichiers spécifiques en définissant le filtre **Appliquer à** sur Tous les fichiers, Dossiers sélectionnés ou Tous les fichiers excepté les dossiers sélectionnés, puis sélectionnez les fichiers ou dossiers concernés.  
  
![filtre Appliquer à](./media/apply-to-filter.png "apply to filter")  
  

## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Nov16_HO4-->


