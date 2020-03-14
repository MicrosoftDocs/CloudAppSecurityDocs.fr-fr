---
title: Visibilité des activités de l’application Cloud-Cloud App Security | Microsoft Docs
description: Cet article fournit une liste des activités, des filtres et des paramètres de correspondance qui peuvent être appliqués aux stratégies d’activité.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/16/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 33837f543282dbc7d40dc7c1961e687b4334794e
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285293"
---
# <a name="activities"></a>Activités

*S’applique à : Microsoft Cloud App Security*

Microsoft Cloud App Security vous donne une visibilité sur toutes les activités de vos applications connectées. Une fois que vous avez connecté Cloud App Security à une application à l’aide du connecteur d’application, Cloud App Security analyse toutes les activités qui se sont produites : la période d’analyse rétroactive diffère selon l’application, puis elle est mise à jour en permanence avec les nouvelles activités.

> [!NOTE]
> Pour obtenir une liste complète des activités Office 365 surveillées par Cloud App Security, voir [Rechercher le journal d’audit dans le Centre de sécurité et conformité Office 365](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c?ui=en-US&rs=en-US&ad=US#ID0EABAAA=Audited_activities).

Le **journal d’activité** peut être filtré pour vous permettre de trouver des activités spécifiques. Vous créez des stratégies en fonction des activités, puis vous définissez ce à quoi vous souhaitez être alerté et comment agir. Vous pouvez rechercher des activités effectuées sur certains fichiers. Les types d’activités et les informations que nous obtenons pour chaque activité varient selon l’application et le genre de données que l’application peut fournir.

Par exemple, vous pouvez utiliser le **journal d’activité** pour trouver les utilisateurs de votre organisation qui utilisent des systèmes d’exploitation ou des navigateurs obsolètes. Pour cela, procédez comme suit : après avoir connecté une application à Cloud App Security dans la page **Journal d’activité**, utilisez le filtre avancé et sélectionnez l’**étiquette Agent utilisateur**. Sélectionnez ensuite **Navigateur obsolète** ou **Système d’exploitation obsolète**.

![Exemple de navigateur obsolète dans une activité](media/activity-example-outdated.png)

Le filtre de base fournit des outils efficaces pour démarrer vos activités de filtrage.

![filtre de base du journal d’activité](media/activity-log-filter-basic.png)

Pour accéder à des activités plus spécifiques, vous pouvez développer le filtre de base en cliquant sur **avancé**.

![filtre avancé du journal d’activité](media/activity-log-filter-advanced.png)

> [!NOTE]
> La balise héritée est ajoutée à toute stratégie d’activité qui utilise l’ancien filtre « utilisateur ». Ce filtre continuera à fonctionner normalement. Si vous souhaitez supprimer la balise héritée, vous pouvez supprimer le filtre et rajouter le filtre à l’aide du nouveau filtre de **nom d’utilisateur** .

## <a name="the-activity-drawer"></a>Tiroir Activité

### <a name="working-with-the-activity-drawer"></a>Travailler avec le tiroir Activité

Vous pouvez afficher plus d’informations supplémentaires sur chaque activité en cliquant sur l’activité elle-même dans le journal d’activité. Cela ouvre le tiroir activité qui fournit les actions et Insights supplémentaires suivants pour chaque activité :
- Stratégies correspondantes : Cliquez sur le lien Stratégies correspondantes pour afficher la liste des stratégies que cette activité a mises en correspondance.

- Afficher les données brutes : Cliquez sur Afficher les données brutes pour afficher les données réelles reçues de l’application.

- Utilisateur : Cliquez sur l’utilisateur pour afficher la page utilisateur de l’utilisateur ayant réalisé l’activité.

- Type d’appareil : Cliquez sur le type d’appareil pour afficher les données d’agent utilisateur brutes.

- Emplacement : Cliquez sur l’emplacement pour afficher l’emplacement dans des cartes Bing.

- Catégorie d’adresse IP et balises : Cliquez sur la balise IP pour afficher la liste des balises IP trouvées dans cette activité. Vous pouvez ensuite filtrer selon toutes les activités correspondant à cette balise.

Les champs du tiroir d’activité fournissent des liens contextuels vers des fichiers supplémentaires et permettent d’effectuer un zoom avant, directement dans le tiroir. Par exemple, si vous déplacez votre curseur à côté de la catégorie d’adresse IP, vous pouvez utiliser l’icône ajouter au filtre ![ajouter au filtre](media/add-to-filter-icon.png) pour ajouter l’adresse IP immédiatement au filtre de la page actuelle. Vous pouvez également utiliser l’icône de roue dentée paramètres ![icône paramètres](media/contextual-settings-icon.png) qui s’affiche pour accéder directement à la page des paramètres nécessaire pour modifier la configuration de l’un des champs, par exemple les **groupes d’utilisateurs**.

Vous pouvez également utiliser les icônes en haut de l’onglet pour effectuer les opérations suivantes :
- Afficher les activités du même type
- Afficher toutes les activités du même utilisateur
- Afficher les activités à partir de la même adresse IP
- Afficher les activités à partir du même emplacement géographique
- Afficher les activités à partir de la même période (48 heures)

![tiroir activité](media/activity-drawer.png "tiroir activité")

Pour obtenir la liste des actions de gouvernance disponibles, consultez [Actions de gouvernance des activités](governance-actions.md#activity-governance-actions).

#### <a name="user-insights"></a>Insights utilisateur

L’expérience d’investigation comprend des Insights sur l’utilisateur en action. En un seul clic, vous pouvez obtenir une vue d’ensemble complète de l’utilisateur, notamment l’emplacement à partir duquel il s’est connecté, le nombre d’alertes ouvertes impliquées et leurs informations de métadonnées.

Pour afficher les insights utilisateur :

1. Cliquez sur l’activité elle-même dans le **Journal d’activité**.

2. Ensuite, cliquez sur l’onglet **Utilisateur**.  
Cliquer sur ouvre l’onglet **utilisateur** du tiroir activité qui fournit les Insights suivants sur l’utilisateur :
    - **Alertes ouvertes** : Nombre d’alertes ouvertes concernant l’utilisateur.
    - **Correspond**: nombre de correspondances de stratégie pour les fichiers appartenant à l’utilisateur.
    - **Activités** : Nombre d’activités effectuées par l’utilisateur au cours des 30 derniers jours.
    - **Pays** : Nombre de pays à partir desquels l’utilisateur s’est connecté au cours des 30 derniers jours.
    - **ISP** : Nombre d’ISP à partir desquels l’utilisateur s’est connecté au cours des 30 derniers jours.
    - **Adresses IP** : Nombre d’adresses IP à partir desquelles l’utilisateur s’est connecté au cours des 30 derniers jours.

![Insights utilisateur dans Cloud App Security](media/user-insights.png)

#### <a name="ip-address-insights"></a>Insights d’adresse IP

Étant donné que les informations d’adresse IP sont essentielles pour la quasi-totalité des investigations, vous pouvez afficher des informations détaillées sur les adresses IP dans le tiroir activité. Dans une activité spécifique, vous pouvez cliquer sur l’onglet adresse IP pour afficher les données consolidées relatives à l’adresse IP, y compris le nombre d’alertes ouvertes pour l’adresse IP spécifique, un graphique de tendance de l’activité récente et une carte d’emplacement. Cela vous permet d’accéder facilement aux alertes de voyage, par exemple. Vous pouvez facilement comprendre où l’adresse IP a été utilisée et si elle a été impliquée dans des activités suspectes ou non. Vous pouvez également effectuer des actions directement dans le tiroir d’adresse IP, qui vous permettent de marquer une adresse IP comme étant risquée, VPN ou d’entreprise pour faciliter l’investigation future et la création de stratégies.

Pour afficher les informations sur l’adresse IP :

1. Cliquez sur l’activité elle-même dans le **Journal d’activité**.

2. Cliquez ensuite sur l’onglet **adresse IP** .  
Cela ouvre l’onglet **adresse IP** du tiroir activité qui fournit les Insights suivants sur l’adresse IP :
    - **Alertes ouvertes**: nombre d’alertes ouvertes qui impliquaient l’adresse IP.
    - **Activités**: nombre d’activités effectuées par l’adresse IP au cours des 30 derniers jours.
    - **Emplacement IP**: emplacements géographiques à partir desquels l’adresse IP est connectée au cours des 30 derniers jours.
    - **Activités**: nombre d’activités effectuées à partir de cette adresse IP au cours des 30 derniers jours.
    - **Activités d’administration**: nombre d’activités administratives effectuées à partir de cette adresse IP au cours des 30 derniers jours.
    - Vous pouvez effectuer les actions d’adresse IP suivantes :
        - Baliser en tant qu’adresse IP d’entreprise et ajouter à la liste autorisée
        - Baliser en tant qu’adresse IP VPN et ajouter à la liste autorisée
        - Marquer comme adresse IP risquée et ajouter à la liste bloquée

   >[!NOTE]
   > Quand une adresse IP est marquée comme entreprise, elle est reflétée dans le portail, et les adresses IP sont exclues du déclenchement de détections spécifiques (par exemple, voyage impossible), car ces adresses IP sont considérées comme approuvées.

![Informations sur l’adresse IP dans Cloud App Security](media/ip-address-insights.png)

## Exporter des activités<a name="export"></a>

Vous pouvez exporter toutes les activités des utilisateurs vers un fichier CSV.

Dans le **Journal d’activité**, dans le coin supérieur droit, cliquez sur le bouton **Exporter** .

![bouton Exporter](media/export-button.png)

[!INCLUDE [Handle personal data](../includes/gdpr-intro-sentence.md)]

## <a name="next-steps"></a>Étapes suivantes :

> [!div class="nextstepaction"]
> [Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
