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
ms.openlocfilehash: 1822ce576b71a196917a3f8d2b94122b88eac163
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74461139"
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

## <a name="oauth-app-anomaly-detection-policies"></a>OAuth app anomaly detection policies

In addition to OAuth app policies you can create, there are the following out-of-the-box anomaly detection policies that profile metadata of OAuth apps to identify ones that are potentially malicious:

| Nom de la stratégie | Description de la stratégie |
| --- | --- |
| Misleading OAuth app name | Scans OAuth apps connected to your environment and triggers an alert when an app with a misleading name is detected. Misleading names, such as foreign letters that resemble Latin letters, could indicate an attempt to disguise a malicious app as a known and trusted app. |
| Suspicious OAuth app name | Scans OAuth apps connected to your environment and triggers an alert when an app with a suspicious name is detected. Suspicious names, such as names of known apps published by unknown publishers, could indicate an attempt to disguise a malicious app as a known and trusted app. |
| Non-secure redirect URL is used by an OAuth app | Scans OAuth apps connected to your environment and triggers an alert when an app uses a non-secure redirect URL (for example, does not use the HTTPS protocol), which exposes sensitive data to interception. |
| Misleading publisher name for an OAuth app | Scans OAuth apps connected to your environment and triggers an alert when an app with a misleading publisher name is detected. Misleading publisher names, such as foreign letters that resemble Latin letters, could indicate an attempt to disguise a malicious app as an app coming from a known and trusted publisher. |

> [!NOTE]
> Anomaly detection policies are only available for OAuth apps that are authorized in your Azure Active Directory.

  ## <a name="next-steps"></a>Étapes suivantes 
  [Stratégies de protection des données](data-protection-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]