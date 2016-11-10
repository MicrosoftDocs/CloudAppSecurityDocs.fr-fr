---
title: "Stratégies de protection des données | Documentation Microsoft"
description: "Cette rubrique décrit la procédure de configuration d’une stratégie de données pour surveiller et contrôler les données et les fichiers lors de l’usage des applications cloud de votre organisation."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: ac53fbd6-4d31-4bce-b2bc-9dc65ad83b3e
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: b5887c21fe93262cd9982b0d99bf3301b4ef3f0f


---

# <a name="data-protection-policies"></a>Stratégies de protection des données
    
## <a name="file-policies"></a>Stratégies de fichier  
Les stratégies de fichier vous permettent d’appliquer une large gamme de processus automatisés en exploitant les API du fournisseur de cloud. Vous pouvez définir des stratégies pour fournir des analyses de conformité en continu, des tâches eDiscovery réglementaires, une protection contre la perte de données (DLP, Data Loss Prevention) au contenu sensible partagé publiquement et de nombreux autres cas d’usage.  
Cloud App Security peut surveiller n’importe quel type de fichier en fonction de plus de 20 filtres de métadonnées (par exemple, niveau d’accès, type de fichier). 
 
**Types de fichiers pris en charge** 

Les moteurs intégrés de protection contre la perte de données (DLP) de Cloud App Security effectuent l’inspection du contenu en extrayant le texte de tous les types de fichiers courants (plus de 100), dont Office, Open Office, les fichiers compressés, différents formats de texte enrichi, XML, HTML et bien plus encore.

Le moteur combine trois aspects sous chaque stratégie :  
  
-   Analyse du contenu basé sur des modèles prédéfinis ou des expressions personnalisées.  
  
-   Filtres de contexte comprenant des rôles d’utilisateur, des métadonnées de fichiers, un niveau de partage, une intégration des groupes d’organisation, un contexte de collaboration et d’autres attributs personnalisables.  
  
-   Actions automatisées pour la gouvernance et la correction. Pour plus d’informations, consultez [Contrôle](control.md).  
  
Une fois activée, la stratégie analyse en permanence votre environnement cloud et identifie les fichiers qui correspondent aux filtres de contenu et de contexte, puis applique les actions automatisées demandées. Ces stratégies détectent et corrigent toutes les violations concernant les informations au repos ou le contenu nouvellement créé. Les stratégies peuvent être surveillées à l’aide d’alertes en temps réel ou de rapports générés par une console.  
  
Voici quelques exemples de stratégies de fichier que vous pouvez créer :  
  
-   Fichiers partagés publiquement :  
    Recevez une alerte quand un fichier situé dans le cloud est publiquement partagé en sélectionnant tous les fichiers dont le niveau de partage est public.  
  
-   Le nom de fichier publiquement partagé contient le nom de l’organisation :  
    Recevez une alerte quand un fichier contient le nom de votre organisation et qu’il est publiquement partagé. Sélectionnez les fichiers dont le nom contient celui de votre organisation et qui sont publiquement partagés.  
  
-   Partage avec des domaines externes :  
    Recevez une alerte quand un fichier est partagé avec des comptes appartenant à des domaines externes spécifiques, par exemple, au domaine d’un concurrent. Sélectionnez le domaine externe avec lequel vous voulez limiter le partage.  
  
-   Mettez en quarantaine les fichiers partagés qui n’ont pas été modifiés pendant la dernière période :  
    Recevez une alerte sur les fichiers partagés que personne n’a modifié dernièrement, afin de les mettre en quarantaine ou d’activer une action automatisée. Excluez tous les fichiers privés qui n’ont pas été modifiés pendant une plage de dates spécifiée. Sur Google Apps, vous pouvez choisir de mettre en quarantaine ces fichiers, en cochant la case « Fichier en quarantaine » dans la page de création de stratégie.  
  
-   Partage avec des utilisateurs non autorisés :  
    Recevez une alerte quand des fichiers sont partagés avec un groupe non autorisé d’utilisateurs dans votre organisation. Sélectionnez les utilisateurs avec lesquels le partage n’est pas autorisé.  
  
-   Extension de fichier sensible :  
    Recevez une alerte quand des fichiers portant des extensions spécifiques sont potentiellement très exposés. Sélectionnez l’extension spécifique (par exemple, crt pour les certificats) ou le nom de fichier et excluez celles avec le niveau de partage privé.  
  
Pour créer une stratégie de fichier, procédez comme suit :  
  
1.  Dans la console, cliquez sur **Contrôle**, puis sur **Stratégies**.  
  
2.  Cliquez sur **Créer une stratégie** et sélectionnez la stratégie **Fichier**.  
  
3.  Donnez à votre stratégie un nom et une description. Si vous le souhaitez, vous pouvez la baser sur un modèle ; pour plus d’informations sur les modèles de stratégie, consultez [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md).  
  
4.  Dans **Type de risque**, liez la stratégie au type de risque le plus approprié. Ce champ est à titre informatif uniquement et vous permet de rechercher ultérieurement des stratégies et alertes spécifiques, selon le type de risque.  Le risque est peut-être déjà présélectionné en fonction de la catégorie pour laquelle vous avez choisi de créer la stratégie. Par défaut, les stratégies de fichier ont la valeur DLP.  
  
5.  Pour définir les applications découvertes qui déclenchent cette stratégie, **Créer un filtre pour les fichiers sur lesquels cette stratégie s’appliquera**, limitez les filtres de stratégie jusqu’à atteindre l’ensemble de fichiers le plus précis sur lequel vous voulez agir. Soyez aussi restrictif que possible afin d’éviter les faux positifs. Par exemple, si vous souhaitez supprimer les autorisations publiques, n’oubliez pas d’ajouter le filtre « Public », pour supprimer un utilisateur externe, utilisez le filtre « Externe », etc.  
  
6.  Pour Box, SharePoint, Dropbox et OneDrive, vous pouvez appliquer votre stratégie de fichier à tous les fichiers de l’application ou à des dossiers spécifiques. Sous **Appliquer à**, sélectionnez **dossiers sélectionnés** ou **tous les fichiers excepté les dossiers sélectionnés**. Vous êtes alors redirigé pour vous connecter à l’application cloud, puis vous ajoutez les dossiers appropriés.  
  
7.  Sélectionnez la **Méthode d’inspection du contenu**. La protection contre la perte de données (DLP) intégrée vous permet de filtrer les fichiers par leur contenu. Pour analyser le contenu des fichiers, sélectionnez ensuite **DLP intégré**. Une fois que l’inspection du contenu est activée, vous pouvez choisir d’utiliser des expressions prédéfinies ou de rechercher d’autres expressions personnalisées, sous forme de sous-chaîne ou d’expression régulière de votre choix.  
    De plus, vous pouvez spécifier une expression régulière pour exclure un fichier des résultats. Cette possibilité s’avère très utile si vous avez des mots clés de classification interne standard à exclure de la stratégie.  
    De plus, vous pouvez déterminer le nombre minimal de violations de contenu à atteindre avant que le fichier ne soit considéré comme une violation. Par exemple, vous pouvez choisir 10 si vous souhaitez être alerté pour les fichiers comportant au moins 10 numéros de carte de crédit détectés dans leur contenu.  
    Quand le contenu est mis en correspondance avec l’expression sélectionnée, vous pouvez choisir de masquer la correspondance elle-même dans la notification de violation et les journaux. Une fois vérifié, le texte en violation est remplacé par des caractères « X ». N’oubliez pas que les numéros sont remplacés par des caractères « # » et qu’ils ne sont jamais stockés dans Cloud App Security.  
  
8.  Choisissez les actions de **gouvernance** que Cloud App Security doit exécuter quand une correspondance est détectée.  
  
9. Une fois que vous avez créé votre stratégie, vous pouvez l’afficher sous l’onglet **Stratégie de fichier**. Vous pouvez toujours modifier une stratégie, ajuster ses filtres ou modifier les actions automatisées. La stratégie est automatiquement activée lors de la création et démarre immédiatement l’analyse de vos fichiers cloud.  
  
> [!NOTE]  
>  Soyez vigilant quand vous définissez des actions de gouvernance. Elles peuvent entraîner une perte irréversible des autorisations d’accès à vos fichiers.  
> Il est recommandé d’affiner les filtres pour représenter exactement les fichiers sur lesquels vous voulez agir, en utilisant plusieurs champs de recherche. Plus les filtres sont précis, mieux c’est.  
>   
>  Pour obtenir des instructions, vous pouvez utiliser le bouton **Modifier et afficher un aperçu des résultats** dans la section Filtres.  
  
![stratégie de fichier, modifier et afficher un aperçu des résultats](./media/file-policy-edit-and-preview-results.png "file policy edit and preview results")  
  
10. Pour afficher les correspondances de stratégie de fichier, les fichiers qui sont suspectés d’enfreindre la stratégie, cliquez sur **Contrôle**, puis sur **Stratégies**. Filtrez les résultats pour afficher uniquement les stratégies de fichier avec le filtre **Type** en haut. Pour plus d’informations sur les correspondances pour chaque stratégie, cliquez sur une stratégie. Vous affichez ainsi les fichiers Mise en correspondance maintenant pour la stratégie. Cliquez sur l’onglet **Historique** pour consulter un historique remontant jusqu’à 6 mois de fichiers correspondant à la stratégie.     
  
## <a name="file-policy-reference"></a>Informations de référence sur les stratégies de fichier  
Cette section fournit des informations de référence sur les stratégies, donne une explication de chaque type de stratégie et décrit les champs que vous pouvez configurer pour chacune d’elles. 
  
Une **stratégie de fichier** est une stratégie basée sur une API qui vous permet de contrôler le contenu de votre organisation dans le cloud, en tenant compte de plus de 20 filtres de métadonnées de fichiers (dont le propriétaire et le niveau de partage), ainsi que des résultats de l’inspection du contenu. Les résultats de la stratégie déterminent les actions de gouvernance applicables. Le moteur d’inspection du contenu peut être étendu par le biais de moteurs DLP tiers, ainsi que de solutions anti-programme malveillant.  
  
Chaque stratégie comprend les éléments suivants :  
  
-   Filtres de fichiers : Vous permettent de créer des conditions très précises en fonction de métadonnées.  
  
-   Inspection du contenu : Vous permet de limiter la stratégie, en fonction de résultats de moteur DLP.  
  
-   Actions : La stratégie fournit un ensemble d’actions de gouvernance automatiquement applicables en cas de violations.  Ces actions sont réparties en actions de collaboration, actions de sécurité et actions d’examen.

![liste déroulante de gouvernance de fichiers](./media/file-governance-drop-down.png)
  
-   Extensions  
  
    > [!NOTE]  
    >  Les extensions sont uniquement disponibles avec la version d’évaluation technique Cloud App Security.  
  
    -   L’inspection du contenu peut être effectuée via des moteurs tiers pour améliorer les fonctionnalités DLP ou anti-programme malveillant.  
  
    -   Les actions de gouvernance peuvent être effectuées par le biais de moteurs tiers pour mettre en œuvre un contrôle de chiffrement personnalisé ou d’autres types de traitement de fichiers (par exemple, un filigrane personnalisé).  
  
## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO4-->


