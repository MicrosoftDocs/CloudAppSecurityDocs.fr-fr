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
ms.openlocfilehash: 6e2464988eb075e3dd3bd345716b5ec71dec8ba6
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74460844"
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

 OU

```powershell
 Add-MsolRoleMember -RoleName "Security Administrator" -RoleMemberEmailAddress “XX@XX.XX”
```

## <a name="next-steps"></a>Étapes suivantes  
Pour apprendre à configurer et utiliser les stratégies de contrôle des applications cloud, consultez [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md).   

[!INCLUDE [Open support ticket](includes/support.md)]  
