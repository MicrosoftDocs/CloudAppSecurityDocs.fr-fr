---
title: API d’extraction d’arborescence d’entités
description: Cet article décrit la demande d’extraction d’arborescence d’entités dans l’API des entités de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: f3dad3e2e868af0399153b2b6995dcdb104be166
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505178"
---
# <a name="fetch-entity-tree---entities-api"></a>API d’extraction d’arborescence d’entités

*S’applique à : Microsoft Cloud App Security*

> [!NOTE]
> Cette demande n’est pas disponible pour Office 365 Cloud App Security.

Exécutez la requête d’obtention pour extraire toutes les entités associées à l’entité correspondant à la clé primaire spécifiée. Si l’entité est un utilisateur, extrait tous les comptes associés à l’utilisateur. Si l’entité est un compte, extrait le parent et les frères de l’entité.

## <a name="http-request"></a>Demande HTTP

```rest
GET /api/v1/entities/<pk>/retrieve_tree/
```

## <a name="request-url-parameters"></a>Paramètres d’URL de la requête

| Paramètre | Description |
| --- | --- |
| pk | ID de l’entité |

## <a name="example"></a>Exemple

### <a name="request"></a>Requête

Voici un exemple de la requête.

```rest
curl -XPOST -H "Authorization:<your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/entities/<pk>/retrieve_tree/"
```

### <a name="response"></a>response

Retourne l’arborescence d’entités spécifiée au format JSON.

```json
{
  // entity tree record
}
```

[!INCLUDE [Open support ticket](includes/support.md)]
