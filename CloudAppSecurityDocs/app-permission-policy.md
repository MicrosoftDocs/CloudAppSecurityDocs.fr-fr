---
title: Créer des stratégies pour contrôler les applications OAuth dans Cloud App Security | Microsoft Docs
description: Cet article fournit des instructions sur la création et l’utilisation de stratégies d’autorisation d’application dans Microsoft Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/2/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 9f68302c-bb3d-450c-bbf5-f8130cb163e3
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: d0b65fd50a75c7af045abd5cbbd890ecff4d33de
ms.sourcegitcommit: cae782d508db9d1a7c0c362e9a23e83f74d48b21
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2018
ms.locfileid: "52743537"
---
# <a name="oauth-app-policies"></a>Stratégies d’application OAuth

*S’applique à : Microsoft Cloud App Security*

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



  ## <a name="next-steps"></a>Étapes suivantes 
  [Stratégies de protection des données](data-protection-policies.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  