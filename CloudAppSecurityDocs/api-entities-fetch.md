---
title: API FETCH-Entities
description: Cet article décrit la requête d’extraction dans l’API des entités de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 0ff0a93866652a0a4cc2e927593a2a56800c64de
ms.sourcegitcommit: cc283f0ecf8124953f1f71181655603de6846d8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87254660"
---
# <a name="fetch---entities-api"></a>API FETCH-Entities

*S’applique à : Microsoft Cloud App Security*

> [!NOTE]
> Cette demande n’est pas disponible pour Office 365 Cloud App Security.

Exécutez la requête d’obtention pour extraire l’entité correspondant à la clé primaire spécifiée.

## <a name="http-request"></a>Demande HTTP

```rest
GET /api/v1/entities/<pk>/
```

## <a name="request-url-parameters"></a>Paramètres d’URL de la requête

| Paramètre | Description |
| --- | --- |
| pk | Dictionnaire avec les détails de l’ID d’entité, du SaaS et de l’instance encodés sous la forme d’une chaîne base64. Par exemple : `{"id":"3fa9f28b-eb0e-463a-ba7b-8089fe9991e2","saas":11161,"inst":0}` encodée sous forme de chaîne base64. |

## <a name="example"></a>Exemple

### <a name="request"></a>Requête

Voici un exemple de la requête.

```rest
curl -XPOST -H "Authorization:<your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/entities/<pk>/"
```

### <a name="response"></a>response

Retourne l’entité spécifiée au format JSON.

```json
{
  // entity record
}
```

[!INCLUDE [Open support ticket](includes/support.md)]
