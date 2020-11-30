---
title: API FETCH-Entities
description: Cet article décrit la requête d’extraction dans l’API des entités de Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: 34db1003dd3ac23f7bc4d5f14100b6c1ff4f6a2e
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314271"
---
# <a name="fetch---entities-api"></a>API FETCH-Entities

[!INCLUDE [Banner for top of topics](includes/banner.md)]

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

## <a name="example"></a> Exemple

### <a name="request"></a>Requête

Voici un exemple de la requête.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/entities/<pk>/"
```

### <a name="response"></a>response

Retourne l’entité spécifiée au format JSON.

```json
{
  // entity record
}
```

[!INCLUDE [Open support ticket](includes/support.md)]
