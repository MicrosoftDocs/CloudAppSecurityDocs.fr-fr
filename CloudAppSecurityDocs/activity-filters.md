---
title: "Activités | Documentation Microsoft"
description: "Cette rubrique fournit une liste des activités, filtres et paramètres de correspondance qui peuvent être appliqués aux stratégies d’activité."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/26/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: f3af2d25-9286-4e9b-b2ad-35653bec72ff
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 52f2245779568abbf41d47c4b45cdcced302529b
ms.openlocfilehash: 40fd28f568aa9af32f9e2399435f48372ea62413


---
# <a name="activities"></a>Activités
Le journal d’activité peut être filtré pour vous permettre de trouver des activités spécifiques. Le filtre de base fournit des outils efficaces pour démarrer vos activités de filtrage.

 ![filtre de base du journal d’activité](media/activity-log-filter-basic.png)

Pour explorer des activités plus spécifiques, vous pouvez développer le filtre de base en cliquant sur Avancé.

 ![filtre avancé du journal d’activité](media/activity-log-filter-advanced.png)

## <a name="activity-filters"></a>Filtres d’activité
Vous trouverez ci-dessous une liste des filtres d’activité qui peuvent être appliqués. La plupart des filtres prennent en charge plusieurs valeurs, ainsi que NOT, afin de vous fournir un outil très puissant pour créer des stratégies.  
  
-   ID activité : Recherchez uniquement des activités spécifiques par leur ID. Ce filtre s’avère très utile quand vous connectez MCAS à votre SIEM (à l’aide de l’agent SIEM) et que vous voulez examiner davantage les alertes au sein du portail MCAS.  
  
-   Objets d’activité : Recherchez des fichiers, des dossiers ou des URL de site, ou encore des objets cibles (fichier/dossier).
    - Fichier, dossier ou site URL : Vous permet de sélectionner des fichiers, des dossiers et des URL qui commencent par une chaîne spécifique.
    - Objet cible (fichier/dossier) : Vous permet de sélectionner un fichier ou un dossier spécifique. 
    
-   Type d’activité : Recherchez l’activité de l’application.

-   Activité administrative : Recherchez uniquement les activités administratives.  
  
-   ID d’alerte - Recherchez par ID d’alerte.

-   Application : Recherchez uniquement des activités au sein d’applications spécifiques.  
  
-   Action appliquée : Recherchez par action de gouvernance appliquée (Bloqué, Proxy de contournement, Déchiffré, Chiffré, Échec du chiffrement, Aucune action).

-   Date : Date à laquelle l’activité s’est produite. Le filtre prend en charge des dates antérieures/ultérieures ainsi qu’une plage de dates.  
  
-   Description : Mot clé spécifique dans la description de l’activité, par exemple, toutes les activités qui contiennent la chaîne **utilisateur** dans leur description.  
  
-   Balise de l’appareil : Recherchez par appareil conforme, géré ou vérifié.

-   Type d’appareil : Recherchez uniquement les activités qui ont été effectuées à l’aide d’un type d’appareil spécifique, par exemple toutes les activités des appareils mobiles, PC ou tablettes.  
  
-   Adresse IP : Adresse IP brute, catégorie IP ou balise IP à partir de laquelle l’activité a été réalisée.  
    - Adresse IP brute : Vous permet de rechercher des activités qui ont été réalisées sur ou par des adresses IP brutes qui sont égales à/ne sont pas égales à ou commencent par/ne commencent pas par une séquence particulière, ou des adresses IP brutes qui sont définies/ne sont pas définies. 
    - Catégorie IP : Catégorie de l’adresse IP à partir de laquelle l’activité a été réalisée, par exemple, toutes les activités de la plage d’adresses IP administratives. Pour plus d’informations sur les catégories d’adresses IP, consultez [Organiser les données selon vos besoins](general-setup.md#IPtagsandRanges).  
    - Balise IP : Balise de l’adresse IP à partir de laquelle l’activité a été exécutée, par exemple toutes les activités des adresses IP de proxy anonyme. Pour plus d’informations sur les balises IP, consultez [Organiser les données selon vos besoins](general-setup.md#IPtagsandRanges).
  
-   Activité représentée : Recherchez uniquement les activités qui ont été effectuées au nom d’un autre utilisateur.  

-   Emplacement : Pays à partir duquel l’activité a été effectuée.  

-   Stratégie correspondante : Recherchez les activités qui correspondent à une stratégie spécifique qui a été définie dans le portail.  

-   ISP enregistré : Fournisseur de services Internet à partir duquel l’activité a été effectuée.   

-  Source : Effectuez la recherche en fonction de la source à partir de laquelle l’activité a été détectée. La source peut être l’un des éléments suivants :
  - Connecteur d’application : journaux provenant directement du connecteur d’API de l’application.
  - Analyse du connecteur d’application : enrichissements de Cloud App Security basés sur l’analyse des informations par le connecteur d’API.
  

-   Utilisateur : Utilisateur qui a exécuté l’activité, qui peut être filtré en domaine, groupe, nom ou organisation. Pour filtrer les activités sans utilisateur spécifique, vous pouvez utiliser l’opérateur « n’est pas défini ».  
    -   Domaine de l’utilisateur : Recherchez un domaine utilisateur spécifique.
    -   Groupe d’utilisateurs : Groupes d’utilisateurs spécifiques importés automatiquement par Cloud App Security à partir de l’application cloud, par exemple, toutes les activités réalisées par les administrateurs Office 365.
    -   Nom d’utilisateur : Recherchez un nom d’utilisateur spécifique.
    -   Organisation utilisateur : Unité d’organisation de l’utilisateur qui a effectué l’activité, par exemple toutes les activités effectuées par les utilisateurs EMEA_marketing.  

-   Agent utilisateur : Agent utilisateur à partir duquel l’activité a été effectuée.  
  
-   Étiquette agent utilisateur : Balise d’agent utilisateur intégrée, par exemple toutes les activités d’un navigateur obsolète ou d’anciens systèmes d’exploitation.  
    
  
## <a name="working-with-the-activity-drawer"></a>Travailler avec le tiroir Activité

Vous pouvez afficher des informations supplémentaires sur chaque activité en cliquant sur l’activité elle-même dans le journal d’activité. Cela ouvre le tiroir Activité qui contient les actions supplémentaires suivantes que vous pouvez réaliser sur le fichier :

- Stratégies correspondantes : Cliquez sur le lien Stratégies correspondantes pour afficher la liste des stratégies que cette activité a mises en correspondance.
- Afficher les données brutes : Cliquez sur Afficher les données brutes pour afficher les données réelles reçues de l’application.
- Utilisateur : Cliquez sur l’utilisateur pour afficher la page utilisateur de l’utilisateur ayant réalisé l’activité. 
- Type d’appareil : Cliquez sur le type d’appareil pour afficher les données d’agent utilisateur brutes. 
- Emplacement : Cliquez sur l’emplacement pour afficher l’emplacement dans des cartes Bing.
- Catégorie d’adresse IP et balises : Cliquez sur la balise IP pour afficher la liste des balises IP trouvées dans cette activité. Vous pouvez ensuite filtrer selon toutes les activités correspondant à cette balise.    

![tiroir activité](./media/activity-drawer.png "activity drawer")  
  
Pour obtenir la liste des actions de gouvernance disponibles, consultez [Paramètres de correspondance de l’activité](governance-actions.md#activity-match-parameters).


## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Dec16_HO1-->


