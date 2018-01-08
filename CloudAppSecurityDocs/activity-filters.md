---
title: "Visibilité sur les activités des applications cloud | Microsoft Docs"
description: "Cette rubrique fournit une liste des activités, filtres et paramètres de correspondance qui peuvent être appliqués aux stratégies d’activité."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/3/2018
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: f3af2d25-9286-4e9b-b2ad-35653bec72ff
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 9e69481693e961c759f6d3bfd09f2e70a345576f
ms.sourcegitcommit: bbf4a2715d1ea3fd21c1a1b87c7f5a2947d2ca68
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2018
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

 Vous pouvez aussi utiliser les icônes au sommet de l’onglet pour :
 - Afficher des activités du même type
 - Afficher toutes les activités du même utilisateur
 - Afficher les activités à partir de la même adresse IP
 - Afficher les activités à partir du même emplacement géographique
 - Afficher les activités dans la même période (48 heures)
 
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
[Pour obtenir du support technique, consultez la page Support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  