---
title: Créer des stratégies pour contrôler les autorisations d’application dans Cloud App Security | Microsoft Docs
description: Cette rubrique fournit des instructions pour créer et utiliser des stratégies d’autorisation d’application dans Microsoft Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/24/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 9f68302c-bb3d-450c-bbf5-f8130cb163e3
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 02af6d6c109812156f8b8a3cf38a6f0599f2fec4
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44143154"
---
*S’applique à : Microsoft Cloud App Security*


# <a name="app-permission-policies"></a>Stratégies d’autorisation d’application

En plus de l’[investigation existante des applications OAuth](manage-app-permissions.md) connectées à votre environnement, vous pouvez définir des stratégies d’autorisation pour recevoir des notifications automatisées quand une application OAuth répond à certains critères. Par exemple, vous pouvez être automatiquement alerté quand des applications exigent un niveau d’autorisation élevé et que plus de 50 utilisateurs l’ont accordé. 

Les stratégies d’autorisation d’application vous permettent de savoir, pour Office 365, G Suite et Salesforce, les autorisations qu’a exigées chaque application et les utilisateurs qui les ont accordées. Vous pouvez également marquer ces autorisations comme approuvées ou interdites. Le fait de les marquer comme interdites révoque les autorisations de chaque application pour chaque utilisateur qui les a accordées. 

Pour créer une stratégie d’autorisation d’application :
1. Sous **Examiner**, sélectionnez **Autorisations d’application**.
2. Filtrez les applications selon vos besoins, par exemple, vous pouvez afficher toutes les applications qui demandent une **Autorisation** pour **Modifier les calendriers dans votre boîte aux lettres**.
3. Cliquez sur le bouton **Nouvelle stratégie à partir de la recherche**. 
    ![nouvelle stratégie à partir de la recherche](./media/app-permissions-filter.png)
4. Vous pouvez utiliser le filtre **Utilisation communautaire** pour savoir si l’octroi d’autorisation à cette application est courant, peu courant ou rare. Cela peut être utile si vous avez une application qui exige rarement une autorisation, qui a un haut niveau de gravité ou qui exige une autorisation auprès de nombreux utilisateurs. 

Sinon, vous pouvez aussi créer la stratégie en cliquant sur **Contrôler** suivi de **Stratégies**. Cliquez ensuite sur **Créer une stratégie** suivi de **Stratégie d’autorisation d’application**.

  
   ![nouvelle stratégie d’autorisation d’application](./media/app-permissions-policy.png)



  ## <a name="see-also"></a>Voir aussi  
  [Stratégies de protection des données](data-protection-policies.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  