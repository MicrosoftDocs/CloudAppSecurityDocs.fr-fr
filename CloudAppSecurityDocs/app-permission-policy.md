---
title: Créer des stratégies pour contrôler les applications OAuth dans Cloud App Security
description: Cet article fournit des instructions sur la création et l’utilisation de stratégies d’autorisation d’application dans Microsoft Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/27/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: c67e950b2d3227e8c0e261d346dcd1eec5f22d89
ms.sourcegitcommit: 97563af6076ccbad0d994ac69a85a998a625d06a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87296705"
---
# <a name="oauth-app-policies"></a>Stratégies d’application OAuth

*S’applique à : Microsoft Cloud App Security*

En plus de l’[investigation existante des applications OAuth](manage-app-permissions.md) connectées à votre environnement, vous pouvez définir des stratégies d’autorisation pour recevoir des notifications automatisées quand une application OAuth répond à certains critères. Par exemple, vous pouvez être alerté automatiquement quand des applications nécessitent un niveau d’autorisation élevé et ont été autorisées par plus de 50 utilisateurs.

Les stratégies d’application OAuth vous permettent de rechercher les autorisations exigées par chaque application ainsi que les utilisateurs qui les ont accordées pour Office 365, G Suite et Salesforce. Vous pouvez également marquer ces autorisations comme approuvées ou interdites. Le fait de les marquer comme interdites révoque les autorisations de chaque application pour chaque utilisateur qui les a accordées.

## <a name="create-a-new-oauth-app-policy"></a>Créer une stratégie d’application OAuth

Il existe deux façons de créer une stratégie d’application OAuth. La première se trouve sous **Examiner**, tandis que la seconde se trouve sous **Contrôler**.

Pour créer une stratégie d’application OAuth :

1. Sous **Examiner**, sélectionnez **OAuth app** (Application OAuth).

1. Filtrez les applications selon vos besoins, par exemple, vous pouvez afficher toutes les applications qui demandent une **Autorisation** pour **Modifier les calendriers dans votre boîte aux lettres**.
1. Cliquez sur le bouton **Nouvelle stratégie à partir de la recherche**.
    ![nouvelle stratégie à partir de la recherche](media/app-permissions-filter.png)
1. Vous pouvez utiliser le filtre **Utilisation communautaire** pour savoir si l’octroi d’autorisation à cette application est courant, peu courant ou rare. Ce filtre peut être utile si vous avez une application rare qui exige une autorisation avec un haut niveau de gravité ou qui exige une autorisation auprès de nombreux utilisateurs.
1. Vous pouvez définir la stratégie en fonction du groupe auquel appartiennent les utilisateurs qui ont autorisé les applications. Par exemple, un administrateur ne peut décider de définir une stratégie de révocation des applications rares demandant des autorisations élevées que si l’utilisateur qui a donné les autorisations est membre du groupe administrateurs.

Sinon, vous pouvez aussi créer la stratégie en cliquant sur **Contrôler** suivi de **Stratégies**. Cliquez ensuite sur **Créer une stratégie** suivi de **OAuth app policy** (Stratégie d’application OAuth).

   ![Nouvelle stratégie d’application OAuth](media/app-permissions-policy.png)

## <a name="oauth-app-anomaly-detection-policies"></a>Stratégies de détection des anomalies d’application OAuth

En plus des stratégies d’application OAuth que vous pouvez créer, les stratégies de détection des anomalies prêtes à l’emploi suivantes permettent de profiler les métadonnées des applications OAuth pour identifier celles qui sont potentiellement malveillantes :

| Nom de stratégie | Description de stratégie |
| --- | --- |
| Nom d’application OAuth trompeur | Analyse les applications OAuth connectées à votre environnement et déclenche une alerte lorsqu’une application avec un nom trompeur est détectée. Les noms trompeurs, tels que les lettres étrangères ressemblant à des lettres latines, peuvent indiquer une tentative de déguisage d’une application malveillante en tant qu’application connue et approuvée. |
| Nom du serveur de publication trompeur pour une application OAuth | Analyse les applications OAuth connectées à votre environnement et déclenche une alerte lorsqu’une application avec un nom d’éditeur trompeur est détectée. Les noms de serveur de publication trompeurs, tels que les lettres étrangères ressemblant à des lettres latines, peuvent indiquer une tentative de déguisement d’application malveillante en tant qu’application provenant d’un éditeur connu et approuvé. |
| Consentement de l’application OAuth malveillante | Analyse les applications OAuth connectées à votre environnement et déclenche une alerte lorsqu’une application potentiellement malveillante est autorisée. Les applications OAuth malveillantes peuvent être utilisées dans le cadre d’une campagne de hameçonnage pour tenter de compromettre les utilisateurs. Cette détection tire parti de l’expertise en matière de recherche et de renseignement sur les menaces de Microsoft pour identifier les applications malveillantes. |
| Activités suspectes de téléchargement de fichiers d’application OAuth | Voir [stratégies de détection des anomalies](anomaly-detection-policy.md#suspicious-oauth-app-file-download-activities) |

<!--
| OAuth apps authorized by external users | Scans OAuth apps connected to your environment and triggers an alert when an app was authorized by an external user. |
| OAuth apps with high permissions and rare community use – Google | Scans OAuth apps connected to your environment and triggers an alert for apps with high permissions and rare community use in Google. |
| OAuth apps with high permissions and rare community use – Office | Scans OAuth apps connected to your environment and triggers an alert for apps with high permissions and rare community use in Office. |
| OAuth apps with rare community use - Salesforce | Scans OAuth apps connected to your environment and triggers an alert for apps with rare community use in Salesforce. |
-->

> [!NOTE]
> Les stratégies de détection des anomalies sont uniquement disponibles pour les applications OAuth autorisées dans votre Azure Active Directory.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Stratégies de protection des données](data-protection-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
