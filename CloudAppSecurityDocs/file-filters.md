---
title: Présentation des données et des filtres de fichiers disponibles dans Cloud App Security
description: Cet article de référence fournit des informations sur les types de fichier et les filtres de fichiers utilisés par Cloud App Security.
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: ShlomoSagir-MSn
ms.date: 7/7/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: cadcd6db-05b2-4974-91fe-cfac3d57aecd
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 82332b70c58f81e5084b3d26394430e429490b54
ms.sourcegitcommit: 0249f6e4a51240e6e37bc67430304e5a261e340a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610897"
---
# <a name="files"></a>Fichiers

*S’applique à : Microsoft Cloud App Security*

Pour garantir la protection des données, Microsoft Cloud App Security vous permet de visualiser tous les fichiers de vos applications connectées. Une fois connecté à une application à l’aide du connecteur d’applications, Microsoft Cloud App Security analyse tous les fichiers, par exemple tous les fichiers stockés dans OneDrive et Salesforce. Cloud App Security analyse ensuite chaque fichier dès qu’une modification est apportée (à son contenu, à ses métadonnées ou à ses autorisations de partage). Les durées des analyses varient en fonction du nombre de fichiers stockés dans votre application. Vous pouvez également utiliser la page **Fichiers** pour filtrer les fichiers et examiner le genre des données enregistrées dans vos applications cloud.

## <a name="file-filter-examples"></a>Exemples de filtres de fichiers

Par exemple, utilisez la page **Fichiers** pour sécuriser les fichiers en partage externe étiquetés comme **confidentiels** comme suit : Une fois que vous avez connecté une application à Cloud App Security, intégrez à Azure Information Protection. Ensuite, dans la page **Fichiers**, filtrez les fichiers étiquetés comme **confidentiels**, puis excluez votre domaine dans le filtre **Collaborateurs**. Si vous voyez qu’il existe des fichiers confidentiels partagés en dehors de votre organisation, vous pouvez créer une stratégie de fichier pour les détecter. Vous pouvez appliquer des actions de gouvernance automatiques à ces fichiers, par exemple **Supprimer des collaborateurs externes** et **Envoyer le résumé des correspondances de stratégie au propriétaire du fichier** pour éviter toute perte de données dans votre organisation.

 ![Filtre de fichiers confidentiels](media/file-filter-confidential.png)

Voici un autre exemple d’utilisation de la page **Fichiers**. Faites en sorte que personne dans votre organisation ne partage publiquement ou de manière externe des fichiers qui n’ont pas été modifiés au cours des six derniers mois : Connectez une application à Cloud App Security, puis accédez à la page **Fichiers**. Filtrez les fichiers dont le niveau d’accès est **Externe** ou **Public**, et définissez la date de **Dernière modification** à six mois auparavant. Créez une stratégie de fichier qui détecte ces fichiers publics périmés en cliquant sur **Nouvelle stratégie à partir de la recherche**. Appliquez-leur des actions de gouvernance automatique, par exemple **Supprimer les utilisateurs externes**, pour éviter toute perte de données à votre organisation.

 ![Filtre de fichiers périmés externes](media/file-example-stale-external.png)

Le filtre de base fournit des outils efficaces pour démarrer le filtrage de vos fichiers.

 ![filtre de journal de fichiers de base](media/file-log-filter-basic-1.png)

Pour explorer des fichiers plus spécifiques, vous pouvez développer le filtre de base en cliquant sur Avancé.

 ![filtre de journal de fichiers avancé](media/file-log-filter-advanced-1.png)
 
## <a name="Filefilters"></a> Filtres de fichiers
 
Cloud App Security peut surveiller n’importe quel type de fichier en fonction de plus de 20 filtres de métadonnées (par exemple, niveau d’accès, type de fichier). 
 
Les moteurs DLP (protection contre la perte de données) intégrés de Cloud App Security effectuent une inspection du contenu en extrayant le texte des types de fichier courants. Certains types de fichier inclus sont des fichiers PDF, Office, RTF, HTML ainsi que des fichiers de code.

Vous trouverez ci-dessous la liste des filtres de fichiers qui peuvent être appliqués. Pour vous permettre de disposer d’un outil puissant de création de stratégies, la plupart des filtres prennent en charge plusieurs valeurs ainsi que NOT.  
> [!NOTE]
> Quand vous utilisez des filtres de stratégie de fichier, le filtre **Contains (Contient)** recherche uniquement des **mots entiers** séparés par des virgules, points, espaces ou traits de soulignement. 
> - Les espaces entre les mots agissent comme l’opérateur OR. Par exemple, si vous recherchez **malware** **virus**, le filtre trouve tous les fichiers dont le nom contient malware ou virus. Il trouve donc malware-virus.exe et virus.exe.  
> - Si vous souhaitez rechercher une chaîne, placez les mots entre guillemets. Ceux-ci fonctionnent comme l’opérateur AND. Ainsi, si vous recherchez **"malware"** **"virus"** , le filtre trouve virus_malware_file.exe, mais pas malwarevirusfile.exe et malware.exe. Toutefois, il recherche la chaîne exacte. Si vous recherchez **"malware virus"** , il ne trouve ni **"virus"** ni **"virus_malware"** .
>
> **Equals (Est égal à)** recherche uniquement la chaîne complète ; par exemple, si vous recherchez **malware.exe**, il trouve malware.exe, mais pas malware.exe.txt. 

- **Niveau d’accès** - Niveau d’accès de partage, à savoir public, externe, interne ou privé.  Pour plus d’informations sur les fichiers externes, consultez [Configuration générale, configurer le portail](getting-started-with-cloud-app-security.md)

    - **Interne** - Les fichiers internes se trouvent dans les domaines internes que vous définissez dans [Configuration générale](General-setup.md). 
    - **Externe** - Les fichiers externes sont tous les fichiers enregistrés à des emplacements hors des domaines internes que vous définissez. 
    - **Partagé** - Fichiers dont le niveau de partage est supérieur au niveau privé. Partagé comprend :
        -  Partage interne - Fichiers partagés dans vos domaines internes.
        -  Partage externe - Fichiers partagés dans des domaines qui ne sont pas listés dans vos domaines internes.
        - Public avec un lien - Fichiers pouvant être partagés avec n’importe qui via un lien.
        -  Public - Fichiers pouvant être trouvés en effectuant une recherche sur Internet. 

      > [!NOTE]
      >  Les fichiers partagés dans vos applications de stockage connectées par des utilisateurs externes sont gérées comme suit par Cloud App Security :
      > - **OneDrive :** OneDrive attribue un utilisateur interne en tant que propriétaire de tout fichier placé dans votre OneDrive par un utilisateur externe. Étant donné que ces fichiers sont alors considérés comme appartenant à votre organisation, Cloud App Security les analyse et applique des stratégies comme à tout autre fichier dans OneDrive.
      > - **Google Drive :** Google Drive les considère comme appartenant à l’utilisateur externe et, en raison de restrictions légales sur les fichiers et données qui ne sont pas la propriété de votre organisation, Cloud App Security n’a pas accès à ces fichiers.
      > - **Box :** Étant donné que Box considère les fichiers appartenant à des sources externes comme des informations privées, ses administrateurs généraux ne peuvent pas afficher le contenu des fichiers. Pour cette raison, Cloud App Security n’a pas accès à ces fichiers. 
      > - **Dropbox :** Étant donné que Dropbox considère les fichiers appartenant à des sources externes comme des informations privées, ses administrateurs généraux ne peuvent pas afficher le contenu des fichiers. Pour cette raison, Cloud App Security n’a pas accès à ces fichiers.

- **Application** - Recherchez uniquement des fichiers au sein de ces applications.  
  
- **Collaborateurs** - Incluez/Excluez des groupes de collaborateurs spécifiques.  
  
    - **Tout membre du domaine** - Si un utilisateur de ce domaine a accès au fichier.  
  
    - **Domaine complet** - Si l’ensemble du domaine a accès au fichier.  
  
    - **Groupes** - Si un groupe spécifique a accès au fichier. Les groupes peuvent être importés à partir d’Active Directory ou d’applications cloud ou encore créés manuellement dans le service.  
  
    - **Utilisateurs** - Ensemble spécifique d’utilisateurs qui peuvent accéder au fichier.  
  
- **Date de création** - Date de création du fichier. Le filtre prend en charge les dates antérieures/postérieures et une plage de dates.  
  
- **Extension** - Concentrez-vous sur des extensions de fichier spécifiques. Par exemple, tous les fichiers qui sont des exécutables (exe).  
  
- **ID de fichier** - Il s’agit d’une fonctionnalité avancée qui vous permet d’effectuer le suivi de certains fichiers de valeur indépendamment de leur propriétaire, leur emplacement ou leur nom.  
  
- **Nom de fichier** - Nom de fichier ou sous-chaîne du nom comme défini dans l’application cloud, par exemple tous les fichiers avec un mot de passe dans leur nom.   
  
- **Étiquette de classification** - Recherchez des fichiers avec des étiquettes spécifiques définies. Il peut s’agir des étiquettes suivantes :
    - **Étiquettes Azure Information Protection** - Nécessite l’intégration avec Azure Information Protection.
    - **Étiquettes Cloud App Security** - Fournit un meilleur insight des fichiers analysés. Pour chaque fichier analysé par Cloud App Security DLP, vous pouvez savoir si l’inspection a été bloquée en raison du chiffrement ou de l’altération du fichier. Par exemple, vous pouvez configurer des stratégies pour vous alerter et mettre en quarantaine les fichiers protégés par mot de passe qui sont partagés en externe.
        - **Chiffré par Azure RMS** - Fichiers dont le contenu n’a pas été inspecté, car ils ont un chiffrement Azure RMS défini.
        - **Chiffré par mot de passe** - Fichiers dont le contenu n’a pas été inspecté, car ils sont protégés par un mot de passe de l’utilisateur.
        - **Fichier endommagé** - Fichiers dont le contenu n’a pas été inspecté, car il n’a pas pu être lu.

- **Type de fichier** - Cloud App Security accepte le type MIME reçu de la part du service et analyse le fichier pour déterminer le type de fichier réel. Cette analyse concerne les fichiers appropriés pour l’analyse des données (documents, images, présentations, feuilles de calcul, fichiers texte et fichiers compressés/archives). Le filtre fonctionne par type de fichier/dossier. Par exemple, Tous les dossiers qui... ou Tous les fichiers de feuille de calcul qui...


   ![mettre à la corbeille des filtres policy_file](./media/policy_file-filters-trash.png "mettre à la corbeille des filtres policy_file")  

  
- **Dans la corbeille** - Excluez/Incluez des fichiers dans le dossier de corbeille. Ces fichiers peuvent quand même être partagés et représentent un risque.  
  
- **Dernière modification** - Date de modification du fichier. Le filtre prend en charge les dates antérieures et postérieures, une plage de dates et les expressions temporelles relatives. Par exemple, tous les fichiers qui n’ont pas été modifiés au cours des six derniers mois.  

- **Stratégie correspondante** - Fichiers mis en correspondance par une stratégie Cloud App Security active.

- **Type MIME** - Vérification du type MIME de fichier, accepte le texte libre.  
  
- **Propriétaire** - Incluez/Excluez des propriétaires de fichiers spécifiques. Par exemple, effectuez le suivi tous les fichiers partagés par employé_non autorisé_#100.  
  
- **UO propriétaire** - Incluez ou excluez les propriétaires de fichiers qui appartiennent à certains groupes d’organisation. Par exemple, tous les fichiers publics à l’exception de ceux partagés par EMEA_marketing. S’applique uniquement aux fichiers stockés dans Google Drive.
  
- **Dossier parent** - Incluez ou excluez des éléments en fonction du dossier parent. Par exemple, tous les fichiers partagés publiquement à l’exception des fichiers contenus dans ce dossier.  
  
- **Mis en quarantaine** - Le fichier est-il en mis quarantaine par le service ? Par exemple, afficher tous les fichiers mis en quarantaine.  
  
Vous pouvez également configurer la stratégie pour qu’elle s’exécute sur des fichiers spécifiques en définissant le filtre **Appliquer à**. Appliquez le filtre **tous les fichiers**, **les dossiers sélectionnés** ou **tous les fichiers exceptés les dossiers sélectionnés**. Sélectionnez ensuite les fichiers ou dossiers appropriés.  
  
![filtre Appliquer à](./media/apply-to-filter.png "filtre Appliquer à")  
<!-- 
>[!NOTE]
> If at any point you want to clear the filters, you can do so by clicking the clear filters icon ![clear filters icon](./media/clear-filters.png).
-->

## <a name="authorizing-files"></a>Autorisation de fichiers

Une fois que Cloud App Security a identifié des fichiers comme présentant un risque DLP ou un programme malveillant, nous vous recommandons de rechercher les fichiers. Si vous déterminez que les fichiers sont sécurisés, vous pouvez les autoriser. Autoriser un fichier supprime de l’état de détection de programmes malveillants et supprime les correspondances futures sur ce fichier.

### <a name="to-authorize-files"></a>Pour autoriser les fichiers

1. Dans Cloud App Security, cliquez sur **contrôle** , puis **stratégies**.
1. Dans la liste des stratégies, sur la ligne dans laquelle la stratégie qui a déclenché l’investigation s’affiche, dans le **nombre** colonne, cliquez sur Lier les correspondances.
    > [!TIP]
    > Vous pouvez filtrer la liste des stratégies par type. Le tableau suivant répertorie, par type de risque, lequel filtrer le type à utiliser :
    >
    > | Type de risque | Type de filtre |
    > | --- | --- |
    > | DLP | Stratégie de fichier |
    > | Programme malveillant | Stratégie de détection des programmes malveillants |
1. Dans la liste des fichiers de mise en correspondance, sur la ligne dans laquelle le fichier sous investigation s’affiche, cliquez sur **Authorize**.

## <a name="working-with-the-file-drawer"></a>Utilisation du tiroir de fichier

Vous pouvez afficher plus d’informations sur chaque fichier en cliquant sur le fichier lui-même dans le journal des fichiers. Cliquant sur le **tiroir de fichier** qui fournit les actions supplémentaires suivantes, vous pouvez effectuer sur le fichier :

- **URL** - Pointe vers l’emplacement du fichier.
- **Identificateurs de fichier** - Ouvre une fenêtre contextuelle avec des détails en données brutes sur le fichier, notamment l’ID du fichier et les clés de chiffrement.
- **Propriétaire** - Permet d’afficher la page utilisateur du propriétaire de ce fichier.
- **Stratégies correspondantes** - Permet de voir une liste des stratégies correspondant au fichier.
- **Étiquette de classification** - Permet d’afficher la liste des étiquettes de classification Azure Information Protection trouvées dans ce fichier. Vous pouvez ensuite appliquer un filtre selon tous les fichiers correspondant à cette étiquette.

Les champs du tiroir de fichier fournissent des liens contextuels vers des fichiers supplémentaires et permettent d’effectuer un zoom avant, directement dans le tiroir. Par exemple, si vous déplacez votre curseur à côté du champ **Propriétaire**, vous pouvez utiliser l’icône « ajouter au filtre » ![ajouter au filtre](./media/add-to-filter-icon.png) pour ajouter le propriétaire immédiatement au filtre de la page active. Vous pouvez également utiliser l’icône de roue dentée paramètres ![icône paramètres](./media/contextual-settings-icon.png) qui s’affiche pour accéder directement à la page des paramètres nécessaire pour modifier la configuration de l’un des champs, par exemple les **étiquettes de classification**.

![tiroir de fichier](./media/file-drawer.png "tiroir de fichier")  
  
Pour obtenir la liste des actions de gouvernance disponibles, consultez [Actions de gouvernance sur des fichiers](governance-actions.md#file-governance-actions).

## <a name="next-steps"></a>Étapes suivantes
  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)