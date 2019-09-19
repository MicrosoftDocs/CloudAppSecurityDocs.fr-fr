---
title: Créer des stratégies pour contrôler les applications OAuth dans Cloud App Security
description: Cet article fournit des instructions sur la création et l’utilisation de stratégies d’autorisation d’application dans Microsoft Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 7/25/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 9f68302c-bb3d-450c-bbf5-f8130cb163e3
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 2046536e45f6ecd7f1ede6249c69b0c7f09b6f57
ms.sourcegitcommit: 8a49c166424fea83853b0a6895212367526abe78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083851"
---
# <a name="oauth-app-policies"></a>Stratégies d’application OAuth

*S’applique à : Microsoft Cloud App Security*

En plus de l’[investigation existante des applications OAuth](manage-app-permissions.md) connectées à votre environnement, vous pouvez définir des stratégies d’autorisation pour recevoir des notifications automatisées quand une application OAuth répond à certains critères. Par exemple, vous pouvez être automatiquement alerté quand des applications exigent un niveau d’autorisation élevé et que plus de 50 utilisateurs l’ont accordé. 

Les stratégies d’application OAuth vous permettent de rechercher les autorisations exigées par chaque application ainsi que les utilisateurs qui les ont accordées pour Office 365, G Suite et Salesforce. Vous pouvez également marquer ces autorisations comme approuvées ou interdites. Le fait de les marquer comme interdites révoque les autorisations de chaque application pour chaque utilisateur qui les a accordées. 

## <a name="create-a-new-oauth-app-policy"></a>Créer une stratégie d’application OAuth

Il existe deux façons de créer une stratégie d’application OAuth. La première se trouve sous **Examiner**, tandis que la seconde se trouve sous **Contrôler**. 

Pour créer une stratégie d’application OAuth :

1. Sous **Examiner**, sélectionnez **OAuth app** (Application OAuth).
2. Filtrez les applications selon vos besoins, par exemple, vous pouvez afficher toutes les applications qui demandent une **Autorisation** pour **Modifier les calendriers dans votre boîte aux lettres**.
3. Cliquez sur le bouton **Nouvelle stratégie à partir de la recherche**. 
    ![nouvelle stratégie à partir de la recherche](./media/app-permissions-filter.png)
4. Vous pouvez utiliser le filtre **Utilisation communautaire** pour savoir si l’octroi d’autorisation à cette application est courant, peu courant ou rare. Ce filtre peut être utile si vous avez une application rare qui exige une autorisation avec un haut niveau de gravité ou qui exige une autorisation auprès de nombreux utilisateurs. 
5. Vous pouvez définir la stratégie en fonction du groupe auquel appartiennent les utilisateurs qui ont autorisé les applications. Par exemple, un administrateur peut décider de définir une stratégie qui révoque les applications rares si celles-ci nécessitent des autorisations élevées, uniquement si l’utilisateur qui a accordé les autorisations est un membre du groupe Administrateurs.

Sinon, vous pouvez aussi créer la stratégie en cliquant sur **Contrôler** suivi de **Stratégies**. Cliquez ensuite sur **Créer une stratégie** suivi de **OAuth app policy** (Stratégie d’application OAuth).

   ![Nouvelle stratégie d’application OAuth](./media/app-permissions-policy.png)

## <a name="oauth-app-anomaly-detection-policies"></a>Stratégies de détection des anomalies d’application OAuth

En plus des stratégies d’application OAuth que vous pouvez créer, les stratégies de détection des anomalies prêtes à l’emploi suivantes permettent de profiler les métadonnées des applications OAuth pour identifier celles qui sont potentiellement malveillantes :

| Nom de la stratégie | Description de la stratégie |
| --- | --- |
| Nom d’application OAuth trompeur | Analyse les applications OAuth connectées à votre environnement et déclenche une alerte lorsqu’une application avec un nom trompeur est détectée. Les noms trompeurs, tels que les lettres étrangères ressemblant à des lettres latines, peuvent indiquer une tentative de déguisage d’une application malveillante en tant qu’application connue et approuvée. |
| Nom d’application OAuth suspect | Analyse les applications OAuth connectées à votre environnement et déclenche une alerte lorsqu’une application avec un nom suspect est détectée. Les noms suspects, tels que les noms des applications connues publiées par des serveurs de publication inconnus, peuvent indiquer une tentative de déguisage d’une application malveillante en tant qu’application connue et approuvée. |
| Une URL de redirection non sécurisée est utilisée par une application OAuth | Analyse les applications OAuth connectées à votre environnement et déclenche une alerte lorsqu’une application utilise une URL de redirection non sécurisée (par exemple, n’utilise pas le protocole HTTPs), qui expose des données sensibles pour l’interception. |
| Nom du serveur de publication trompeur pour une application OAuth | Analyse les applications OAuth connectées à votre environnement et déclenche une alerte lorsqu’une application avec un nom d’éditeur trompeur est détectée. Les noms de serveur de publication trompeurs, tels que les lettres étrangères ressemblant à des lettres latines, peuvent indiquer une tentative de déguisement d’application malveillante en tant qu’application provenant d’un éditeur connu et approuvé. |

> [!NOTE]
> Les stratégies de détection des anomalies sont uniquement disponibles pour les applications OAuth autorisées dans votre Azure Active Directory.

  ## <a name="next-steps"></a>Étapes suivantes 
  [Stratégies de protection des données](data-protection-policies.md)

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)