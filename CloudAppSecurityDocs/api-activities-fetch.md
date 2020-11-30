---
title: API FETCH-Activities
description: Cet article décrit la requête d’extraction dans l’API des activités de Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: dc26c22748aa2a03e7a59208b691c6a3a92527d6
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314713"
---
# <a name="fetch---activities-api"></a>API FETCH-Activities

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Exécutez la requête d’obtention pour extraire l’activité correspondant à la clé primaire spécifiée.

## <a name="http-request"></a>Demande HTTP

```rest
GET /api/v1/activities/<pk>/
```

## <a name="request-url-parameters"></a>Paramètres d’URL de la requête

| Paramètre | Description |
| --- | --- |
| pk | ID de l’activité |

## <a name="example"></a> Exemple

### <a name="request"></a>Requête

Voici un exemple de la requête.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/activities/<pk>/"
```

### <a name="response"></a>response

Retourne l’activité spécifiée au format JSON.

```json
{
  // activity record
}
```

[!INCLUDE [Open support ticket](includes/support.md)]
