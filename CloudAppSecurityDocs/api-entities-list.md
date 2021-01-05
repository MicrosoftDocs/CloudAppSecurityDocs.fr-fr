---
title: API List-Entities
description: Cet article décrit la requête de liste dans l’API des entités de Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: a93fa00db40720d8b8bf31a8494ce949402bca0b
ms.sourcegitcommit: 90df07ce9cd64fd9c46fb6563f0249079204e174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97858967"
---
# <a name="list---entities-api"></a>API List-Entities

[!INCLUDE [Banner for top of topics](includes/banner.md)]

> [!NOTE]
> Cette demande n’est pas disponible pour Office 365 Cloud App Security.

Exécutez la requête d’obtention ou de publication pour extraire une liste d’entités correspondant aux filtres spécifiés.

## <a name="http-request"></a>Demande HTTP

```rest
GET /api/v1/entities/
```

```rest
POST /api/v1/entities/
```

## <a name="request-body-parameters"></a>Paramètres du corps de la demande

| Paramètre | Description |
| --- | --- |
| filtres | Filtrer les objets avec tous les filtres de recherche pour la demande, consultez [filtres d’entité](api-entities.md#filters) pour plus d’informations |
| sortDirection | Sens du tri. Les valeurs possibles sont : `asc` et `desc` |
| sortField | Champs utilisés pour trier les entités. Les valeurs possibles sont les suivantes :<br />- **Date**: date de création de l’entité<br />- **gravité**: gravité de l’entité |
| skip | Ignore le nombre spécifié d’enregistrements |
| limit | Nombre maximal d’enregistrements retournés par la requête |

## <a name="example"></a> Exemple

### <a name="request"></a>Requête

Voici un exemple de la requête.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/entities/" -d '{
  "filters": {
    // some filters
  },
  "skip": 5,
  "limit": 10
  ...
}'
```

### <a name="response"></a>response

Retourne une liste d’activités au format JSON.

```json
{
  "total": 5 // total number of records
  "hasNext": true // whether there is more data to show or not.
  "data": [
    // returned records
  ]
}
```

[!INCLUDE [Open support ticket](includes/support.md)]
