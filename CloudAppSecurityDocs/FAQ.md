---
title: Forum Aux Questions - Cloud App Security | Microsoft Docs
description: Cet article fournit les réponses aux questions fréquentes sur Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 081c2cf4-2750-4546-9490-4b65e87ae48c
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: f2d2fc6ef5753cbca977e785249ddf61a3664eb5
ms.sourcegitcommit: c342abeec95359ddabdabcc3a081a0f91d52407c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72334445"
---
# <a name="frequently-asked-questions"></a>Forum aux questions

*S’applique à : Microsoft Cloud App Security*

Cet article fournit les réponses aux questions fréquentes sur Cloud App Security.

## <a name="what-kind-of-permissions-do-i-need-to-access-cloud-app-security"></a>Quels sont les genres d’autorisation nécessaires pour accéder à Cloud App Security ?

Vous devez être administrateur général, administrateur de conformité ou administrateur de la sécurité dans Azure Active Directory. Ces rôles ne sont pas suffisants dans le Centre de sécurité et de conformité Office 365. Vous pouvez utiliser PowerShell pour définir un utilisateur en tant qu’administrateur général, administrateur de conformité ou administrateur de la sécurité dans Azure Active Directory. Exécutez les applets de commande ci-dessous :

```powershell

 $cred = Get-Credential
 Connect-MsolService -credential $cred
 Add-MsolRoleMember -RoleName "Compliance Administrator" -RoleMemberEmailAddress "XX@XX.XX"
```

 ou

```powershell
 Add-MsolRoleMember -RoleName "Security Administrator" -RoleMemberEmailAddress “XX@XX.XX”
```

## <a name="next-steps"></a>Étapes suivantes  
Pour apprendre à configurer et utiliser les stratégies de contrôle des applications cloud, consultez [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md).   

Les clients Premier peuvent également choisir Cloud App Security directement depuis le [portail Premier](https://premier.microsoft.com/).  
