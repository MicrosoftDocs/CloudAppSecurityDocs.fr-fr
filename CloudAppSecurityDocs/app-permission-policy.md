---
title: Créer des stratégies pour contrôler les applications OAuth dans Cloud App Security
description: Cet article fournit des instructions sur la création et l’utilisation des stratégies d’autorisation d’application dans Microsoft Cloud App Security.
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
ms.openlocfilehash: 9d007c4760ace7a4337e4738406016576fa04171
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285303"
---
# <a name="oauth-app-policies"></a>Stratégies d’application OAuth

*S’applique à : Microsoft Cloud App Security*

En plus de l' [investigation existante des applications OAuth](manage-app-permissions.md) connectées à votre environnement, vous pouvez définir des stratégies d’autorisation pour que vous obteniez des notifications automatisées quand une application OAuth répond à certains critères. Par exemple, vous pouvez être alerté automatiquement quand des applications nécessitent un niveau d’autorisation élevé et ont été autorisées par plus de 50 utilisateurs.

Les stratégies d’application OAuth vous permettent d’examiner les autorisations demandées par chaque application et les utilisateurs qui les ont autorisés pour Office 365, G suite et Salesforce. Vous pouvez également marquer ces autorisations comme approuvées ou interdites. Les marquer comme interdits révoquent les autorisations pour chaque application pour chaque utilisateur qui l’a autorisé.

## <a name="create-a-new-oauth-app-policy"></a>Créer une stratégie d’application OAuth

Il existe deux façons de créer une stratégie d’application OAuth. La première consiste à **examiner** et le second est sous **contrôle**.

Pour créer une stratégie d’application OAuth :

1. Sous **examiner** , sélectionnez **application OAuth**.

1. Filtrer les applications en fonction de vos besoins, par exemple, vous pouvez afficher toutes les applications qui demandent l' **autorisation** de **modifier des calendriers dans votre boîte aux lettres**.
1. Cliquez sur le bouton **Nouvelle stratégie à partir de la recherche**.
    ![de la nouvelle stratégie à partir de la recherche](media/app-permissions-filter.png)
1. Vous pouvez utiliser le filtre **Community use** pour savoir si l’autorisation d’accès à cette application est courante, peu courante ou rare. Ce filtre peut être utile si vous avez une application qui est rare et qui demande une autorisation ayant un niveau de gravité élevé ou qui demande une autorisation à de nombreux utilisateurs.
1. Vous pouvez définir la stratégie en fonction des appartenances aux groupes des utilisateurs qui ont autorisé les applications. Par exemple, un administrateur ne peut décider de définir une stratégie de révocation des applications rares demandant des autorisations élevées que si l’utilisateur qui a donné les autorisations est membre du groupe administrateurs.

Vous pouvez également créer la stratégie en cliquant sur **contrôle** , puis sur **stratégies**. Cliquez ensuite sur **créer une stratégie** , puis sur stratégie d' **application OAuth**.

   ![nouvelle stratégie d’application OAuth](media/app-permissions-policy.png)

## <a name="oauth-app-anomaly-detection-policies"></a>Stratégies de détection des anomalies d’application OAuth

En plus des stratégies d’application OAuth que vous pouvez créer, les stratégies de détection des anomalies prêtes à l’emploi suivantes permettent de profiler les métadonnées des applications OAuth pour identifier celles qui sont potentiellement malveillantes :

| Nom de la stratégie | Description de la stratégie |
| --- | --- |
| Nom d’application OAuth trompeur | Analyse les applications OAuth connectées à votre environnement et déclenche une alerte lorsqu’une application avec un nom trompeur est détectée. Les noms trompeurs, tels que les lettres étrangères ressemblant à des lettres latines, peuvent indiquer une tentative de déguisage d’une application malveillante en tant qu’application connue et approuvée. |
| Nom du serveur de publication trompeur pour une application OAuth | Analyse les applications OAuth connectées à votre environnement et déclenche une alerte lorsqu’une application avec un nom d’éditeur trompeur est détectée. Les noms de serveur de publication trompeurs, tels que les lettres étrangères ressemblant à des lettres latines, peuvent indiquer une tentative de déguisement d’application malveillante en tant qu’application provenant d’un éditeur connu et approuvé. |
| Consentement de l’application OAuth malveillante | Analyse les applications OAuth connectées à votre environnement et déclenche une alerte lorsqu’une application potentiellement malveillante est autorisée. Les applications OAuth malveillantes peuvent être utilisées dans le cadre d’une campagne de hameçonnage pour tenter de compromettre les utilisateurs. Cette détection tire parti de l’expertise en matière de recherche et de renseignement sur les menaces de Microsoft pour identifier les applications malveillantes. |

<!--| Suspicious OAuth app name | Scans OAuth apps connected to your environment and triggers an alert when an app with a suspicious name is detected. Suspicious names, such as names of known apps published by unknown publishers, could indicate an attempt to disguise a malicious app as a known and trusted app. |
| Non-secure redirect URL is used by an OAuth app | Scans OAuth apps connected to your environment and triggers an alert when an app uses a non-secure redirect URL (for example, does not use the HTTPS protocol), which exposes sensitive data to interception. |-->

> [!NOTE]
> Les stratégies de détection des anomalies sont uniquement disponibles pour les applications OAuth autorisées dans votre Azure Active Directory.

## <a name="next-steps"></a>Étapes suivantes :

> [!div class="nextstepaction"]
> [Stratégies de protection des données](data-protection-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
