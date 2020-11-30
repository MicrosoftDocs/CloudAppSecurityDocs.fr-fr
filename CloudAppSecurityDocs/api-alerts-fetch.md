---
title: API FETCH-Alerts
description: Cet article décrit la requête d’extraction dans l’API des alertes de Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: 8332805803dc05d991ef153b8402afb39b7b0cc1
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314611"
---
# <a name="fetch---alerts-api"></a>API FETCH-Alerts

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Exécutez la requête d’obtention pour extraire l’alerte correspondant à la clé primaire spécifiée.

## <a name="http-request"></a>Demande HTTP

```rest
GET /api/v1/alerts/<pk>/
```

## <a name="request-url-parameters"></a>Paramètres d’URL de la requête

| Paramètre | Description |
| --- | --- |
| pk | ID de l’alerte |

## <a name="example"></a> Exemple

### <a name="request"></a>Requête

Voici un exemple de la requête.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/alerts/<pk>/"
```

### <a name="response"></a>response

Retourne l’alerte spécifiée au format JSON.

```json
{
  // alert record
}
```

[!INCLUDE [Open support ticket](includes/support.md)]
