---
title: "Visibilité sur les activités des applications cloud | Microsoft Docs"
description: "Cette rubrique fournit une liste des activités, filtres et paramètres de correspondance qui peuvent être appliqués aux stratégies d’activité."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/30/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: f3af2d25-9286-4e9b-b2ad-35653bec72ff
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 7d74bb482f44e2845d348dd18777d72910b7e18b
ms.sourcegitcommit: c5a0d07af558239976ce144c14ae56c81642191b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2017
---
# <a name="activities"></a>Activités
Cloud App Security vous donne une visibilité sur toutes les activités de vos applications connectées. Une fois connecté à une application à l’aide du connecteur d’applications, Cloud App Security analyse toutes les activités passées (la période d’analyse rétroactive varie par application). Cloud App Security est ensuite mis à jour en continu avec les nouvelles activités. 

> [!NOTE] 
> Pour obtenir une liste complète des activités Office 365 surveillées par Cloud App Security, voir [Rechercher le journal d’audit dans le Centre de sécurité et conformité Office 365](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c?ui=en-US&rs=en-US&ad=US#ID0EABAAA=Audited_activities).

Le **journal d’activité** peut être filtré pour vous permettre de trouver des activités spécifiques. Vous pouvez créer des stratégies basées sur les activités, puis définir ce dont voulez être alerté pour y réagir. Vous pouvez également rechercher des activités effectuées sur certains fichiers. Les types d’activités et les informations que nous obtenons pour chaque activité varient selon l’application et le genre de données que l’application peut fournir. 

Par exemple, vous pouvez utiliser le **journal d’activité** pour trouver les utilisateurs de votre organisation qui utilisent des systèmes d’exploitation ou des navigateurs obsolètes. Pour cela, procédez comme suit : après avoir connecté une application à Cloud App Security dans la page **Journal d’activité**, utilisez le filtre avancé et sélectionnez l’**étiquette Agent utilisateur**. Sélectionnez ensuite **Navigateur obsolète** ou **Système d’exploitation obsolète**.

 ![Exemple de navigateur obsolète dans une activité](media/activity-example-outdated.png)

Si vous voulez vérifier s’il y a des accès à des fichiers **confidentiels** depuis l’extérieur de votre organisation, définissez le filtre **Objet d’activité** pour rechercher **Étiquette de classification** et sélectionnez l’étiquette **Confidentiel**. Définissez le filtre **Adresse IP** pour une rechercher sur **Catégorie** et excluez les adresses IP de votre bureau (les catégories d’adresses IP peuvent être configurées dans le menu **Paramètres**. Vous pouvez cliquer sur **Nouvelle stratégie à partir de la recherche** pour créer une stratégie d’activité en fonction des filtres que vous avez définis et pour notifier automatiquement les utilisateurs.

 ![Exemple d’activité Fichiers confidentiels externes](media/activity-example-ip.png)

 
Le filtre de base fournit des outils efficaces pour démarrer vos activités de filtrage.

 ![filtre de base du journal d’activité](media/activity-log-filter-basic.png)

Pour explorer des activités plus spécifiques, vous pouvez développer le filtre de base en cliquant sur Avancé.

 ![filtre avancé du journal d’activité](media/activity-log-filter-advanced.png)

## <a name="activity-filters"></a>Filtres d’activité
Vous trouverez ci-dessous une liste des filtres d’activité qui peuvent être appliqués. La plupart des filtres prennent en charge plusieurs valeurs, ainsi que NOT, afin de vous fournir un outil très puissant pour créer des stratégies.  
  
-   ID activité : Recherchez uniquement des activités spécifiques par leur ID. Ce filtre est très utile quand vous connectez Cloud App Security à votre SIEM (à l’aide de l’agent SIEM) et que vous voulez examiner davantage les alertes dans le portail Cloud App Security.  
  
-   Objets d’activité : Recherchez les objets sur lesquels l’activité a été effectuée. Ce filtre s’applique aux objets fichier, dossier, utilisateur ou application. 
    - ID de l’objet d’activité : ID de l’objet (fichier, dossier, utilisateur ou application).
    - Fichier, dossier ou site URL : Vous permet de sélectionner des fichiers, des dossiers et des URL qui commencent par une chaîne spécifique.
    - Objet cible (fichier/dossier) : Vous permet de sélectionner un fichier ou un dossier spécifique. 
    - Élément : vous permet de rechercher par nom ou par ID d’objet d’activité (par exemple des noms d’utilisateur, des fichiers, des paramètres, des sites). Pour le filtre **Élément d’objet d’activité**, vous pouvez choisir de filtrer les éléments qui **contiennent**, **sont égaux** ou **commencent par** l’élément spécifique.
    
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
    - Catégorie IP : Catégorie de l’adresse IP à partir de laquelle l’activité a été réalisée, par exemple, toutes les activités de la plage d’adresses IP administratives. Les catégories doivent être configurées de façon à inclure les adresses IP appropriées, à l’exception de la catégorie « Risqué », qui est préconfigurée et inclut deux balises IP : Proxy anonyme et Tor. Pour découvrir comment configurer les catégories IP, consultez [Organiser les données selon vos besoins](ip-tags.md).  
    - Balise IP : Balise de l’adresse IP à partir de laquelle l’activité a été exécutée, par exemple toutes les activités des adresses IP de proxy anonyme. Cloud App Security crée un ensemble de balises IP prédéfinies qui ne sont pas configurables. Vous pouvez aussi configurer vos propres balises IP. Pour plus d’informations sur la configuration de vos propres balises IP, consultez [Organiser les données selon vos besoins](ip-tags.md).
   Les balises IP prédéfinies sont les suivantes :
    - Applications Microsoft (14 applications)
    - Proxy anonyme
    - Botnet (vous voyez que l’activité a été effectuée par un botnet avec un lien qui vous permet d’en savoir plus sur le botnet spécifique)
    - Adresse IP d’analyse du darknet
    - Serveur de commande et contrôle de programmes malveillants
    - Analyseur de connectivité à distance
    - Fournisseurs par satellite
    - Proxy intelligent et proxy d’accès (délibérément omis)
    - Nœuds de sortie Tor
    - Zscaler


-   Activité représentée : Recherchez uniquement les activités qui ont été effectuées au nom d’un autre utilisateur.  

-   Emplacement : Pays à partir duquel l’activité a été effectuée.  

-   Stratégie correspondante : Recherchez les activités qui correspondent à une stratégie spécifique qui a été définie dans le portail.  

-   ISP enregistré : Fournisseur de services Internet à partir duquel l’activité a été effectuée.   

-  Source : Effectuez la recherche en fonction de la source à partir de laquelle l’activité a été détectée. La source peut être l’un des éléments suivants :
  - Connecteur d’application : journaux provenant directement du connecteur d’API de l’application.
  - Analyse du connecteur d’application : enrichissements de Cloud App Security basés sur l’analyse des informations par le connecteur d’API.
  

-   Utilisateur : Utilisateur qui a exécuté l’activité, qui peut être filtré en domaine, groupe, nom ou organisation. Pour filtrer les activités sans utilisateur spécifique, vous pouvez utiliser l’opérateur « n’est pas défini ».  
    -   Domaine de l’utilisateur : Recherchez un domaine utilisateur spécifique.
    -   Organisation utilisateur : Unité d’organisation de l’utilisateur qui a effectué l’activité, par exemple toutes les activités effectuées par les utilisateurs EMEA_marketing.  
    -   Groupe d’utilisateurs : Groupes d’utilisateurs spécifiques que vous pouvez importer à partir d’applications connectées, par exemple, les administrateurs Office 365.  
    -   Nom d’utilisateur : Recherchez un nom d’utilisateur spécifique. Pour afficher la liste des utilisateurs membres d’un groupe d’utilisateurs spécifique, dans le **tiroir Activité**, cliquez sur le nom du groupe d’utilisateurs. Vous accédez alors à la page Comptes qui liste tous les utilisateurs figurant dans le groupe. À partir de cette page, vous pouvez explorer plus en détail les comptes d’utilisateurs spécifiques dans le groupe.
       -  Vous pouvez affiner les filtres **Groupe d’utilisateurs** et **Nom d’utilisateur** en choisissant le filtre **En tant que**, puis en sélectionnant le rôle de l’utilisateur parmi les rôles suivants :
            - Objet d’activité uniquement : cela signifie que l’utilisateur ou le groupe d’utilisateurs sélectionné n’a pas effectué l’activité en question, mais qu’il était l’objet de l’activité
            - Acteur uniquement : cela signifie que l’utilisateur ou le groupe d’utilisateurs a effectué l’activité
            - N’importe quel rôle : cela signifie que l’utilisateur ou le groupe d’utilisateurs a participé à l’activité, soit en effectuant l’activité, soit en étant l’objet de l’activité

-   Agent utilisateur : Agent utilisateur à partir duquel l’activité a été effectuée.  
  
-   Étiquette agent utilisateur : Balise d’agent utilisateur intégrée, par exemple toutes les activités d’un navigateur obsolète ou d’anciens systèmes d’exploitation.  
    
>[!NOTE]
> Si vous voulez effacer les filtres, vous pouvez le faire à tout moment en cliquant sur l’icône d’effacement des filtres ![icône d’effacement des filtres](./media/clear-filters.png).

## <a name="the-activity-drawer"></a>Tiroir Activité

### <a name="working-with-the-activity-drawer"></a>Travailler avec le tiroir Activité

Vous pouvez afficher plus d’informations supplémentaires sur chaque activité en cliquant sur l’activité elle-même dans le journal d’activité. Cette opération ouvre le tiroir Activité qui contient les actions et insights supplémentaires suivants pour chaque activité :
    - Stratégies correspondantes : Cliquez sur le lien Stratégies correspondantes pour afficher la liste des stratégies que cette activité a mises en correspondance.
    - Afficher les données brutes : Cliquez sur Afficher les données brutes pour afficher les données réelles reçues de l’application.
    - Utilisateur : Cliquez sur l’utilisateur pour afficher la page utilisateur de l’utilisateur ayant réalisé l’activité. 
    - Type d’appareil : Cliquez sur le type d’appareil pour afficher les données d’agent utilisateur brutes. 
    - Emplacement : Cliquez sur l’emplacement pour afficher l’emplacement dans des cartes Bing.
    - Catégorie d’adresse IP et balises : Cliquez sur la balise IP pour afficher la liste des balises IP trouvées dans cette activité. Vous pouvez ensuite filtrer selon toutes les activités correspondant à cette balise.    

 Les champs du tiroir d’activité fournissent des liens contextuels vers des fichiers supplémentaires et permettent d’effectuer un zoom avant, directement dans le tiroir. Par exemple, si vous déplacez votre curseur à côté de la catégorie d’adresse IP, vous pouvez utiliser l’icône ajouter au filtre ![ajouter au filtre](./media/add-to-filter-icon.png) pour ajouter l’adresse IP immédiatement au filtre de la page actuelle. Vous pouvez également utiliser l’icône de roue dentée paramètres ![icône paramètres](./media/contextual-settings-icon.png) qui s’affiche pour accéder directement à la page des paramètres nécessaire pour modifier la configuration de l’un des champs, par exemple les **groupes d’utilisateurs**.


![tiroir activité](./media/activity-drawer.png "tiroir activité")  
  
Pour obtenir la liste des actions de gouvernance disponibles, consultez [Actions de gouvernance des activités](governance-actions.md#activity-governance-actions).

#### <a name="user-insights"></a>Insights utilisateur

L’expérience d’investigation comprend des insights prêts à l’emploi sur l’utilisateur responsable de l’action. En un seul clic, vous pouvez obtenir une vue d’ensemble complète de l’utilisateur, notamment l’endroit à partir duquel il s’est connecté, le nombre d’alertes ouvertes qui le concernent et ses informations de métadonnées.

Pour afficher les insights utilisateur :

1. Cliquez sur l’activité elle-même dans le **Journal d’activité**.

2. Ensuite, cliquez sur l’onglet **Utilisateur**. <br></br> Cette opération ouvre l’onglet **Utilisateur** du tiroir Activité qui fournit les insights suivants sur l’utilisateur :
    - **Alertes ouvertes** : Nombre d’alertes ouvertes concernant l’utilisateur.
    - **Violation de fichiers** : Nombre de violations des fichiers appartenant à l’utilisateur.
    - **Activités** : Nombre d’activités effectuées par l’utilisateur au cours des 30 derniers jours.
    - **Pays** : Nombre de pays à partir desquels l’utilisateur s’est connecté au cours des 30 derniers jours.
    - **ISP** : Nombre d’ISP à partir desquels l’utilisateur s’est connecté au cours des 30 derniers jours.
    - **Adresses IP** : Nombre d’adresses IP à partir desquelles l’utilisateur s’est connecté au cours des 30 derniers jours.

![insights sur l’utilisateur dans Cloud App Security](./media/user-insights.png)

#### <a name="ip-address-insights"></a>Insights sur l’adresse IP

Parce que les informations d’adresse IP sont essentielles dans la quasi-totalité des examens, vous pouvez afficher les informations détaillées des adresses IP dans le tiroir Activité. Dans une activité spécifique, vous pouvez cliquer sur l’onglet Adresse IP pour afficher des données consolidées concernant l’adresse IP, y compris le nombre d’alertes actives pour l’adresse IP spécifique, un graphique de tendance de l’activité récente et une carte d’emplacement. Cela vous permet de faire des examens approfondis, par exemple, quand vous recherchez la cause d’alertes Voyage impossible, vous pouvez facilement déterminer où a été utilisée l’adresse IP et si elle a été impliquée ou non dans des activités suspectes. Vous pouvez également effectuer des actions directement dans le tiroir Adresse IP, où vous pouvez marquer une adresse IP comme étant risquée, VPN ou d’entreprise pour faciliter par la suite l’examen et la création de stratégie.

Pour afficher les insights sur l’adresse IP :

1. Cliquez sur l’activité elle-même dans le **Journal d’activité**.

2. Ensuite, cliquez sur l’onglet **Adresse IP**. <br></br> Cette opération ouvre l’onglet **Adresse IP** du tiroir Activité qui fournit les insights suivants sur l’adresse IP :
    - **Alertes ouvertes** : Nombre d’alertes ouvertes concernant l’adresse IP.
    - **Activités** : Nombre d’activités effectuées par l’adresse IP au cours des 30 derniers jours.
    - **Emplacement IP** : Emplacements géographiques à partir desquels l’adresse IP s’est connectée au cours des 30 derniers jours.
    - **Activités** : Nombre d’activités effectuées à partir de l’adresse IP au cours des 30 derniers jours.
    - **Activités administratives**  : Nombre d’activités administratives effectuées à partir de l’adresse IP au cours des 30 derniers jours.
    - Vous pouvez effectuer les actions d’adresse IP suivantes :
        - Marquer comme adresse IP risquée 
        - Marquer comme adresse IP VPN
        - Marquer comme adresse IP risquée et l’ajouter à un groupe bloqué

![Insights sur l’adresse IP dans Cloud App Security](./media/ip-address-insights.png)


## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  