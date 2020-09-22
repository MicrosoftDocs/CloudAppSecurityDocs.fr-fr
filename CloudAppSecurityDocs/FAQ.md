---
title: Forum aux questions (FAQ)-Cloud App Security
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
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: f9e226f117de70c98125708b93ea1badf67aa06d
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90880177"
---
# <a name="frequently-asked-questions"></a>Forum aux questions

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Cet article fournit les réponses aux questions fréquentes sur Cloud App Security.

## <a name="what-kind-of-permissions-do-i-need-to-access-cloud-app-security"></a>Quels sont les genres d’autorisation nécessaires pour accéder à Cloud App Security ?

Vous devez être administrateur général, administrateur de conformité ou administrateur de la sécurité dans Azure Active Directory. Ces rôles ne sont pas suffisants dans le Centre de sécurité et de conformité Office 365. Vous pouvez utiliser PowerShell pour définir un utilisateur en tant qu’administrateur général, administrateur de conformité ou administrateur de la sécurité dans Azure Active Directory. Exécutez les applets de commande ci-dessous :

```powershell

 $cred = Get-Credential
 Connect-MsolService -credential $cred
 Add-MsolRoleMember -RoleName "Compliance Administrator" -RoleMemberEmailAddress "XX@XX.XX"
```

 OR

```powershell
 Add-MsolRoleMember -RoleName "Security Administrator" -RoleMemberEmailAddress “XX@XX.XX”
```

## <a name="next-steps"></a>Étapes suivantes

Pour apprendre à configurer et utiliser les stratégies de contrôle des applications cloud, consultez [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md).

[!INCLUDE [Open support ticket](includes/support.md)]
