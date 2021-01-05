---
title: API List-Activities
description: Cet article décrit la requête de liste dans l’API des activités de Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: 277dfc0a42b258072a35c14d544ef9fbac4cdb7b
ms.sourcegitcommit: 90df07ce9cd64fd9c46fb6563f0249079204e174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97859006"
---
# <a name="list---activities-api"></a>API List-Activities

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Exécutez la requête d’obtention ou de publication pour extraire une liste d’activités correspondant aux filtres spécifiés.

## <a name="http-request"></a>Demande HTTP

```rest
GET /api/v1/activities/
```

```rest
POST /api/v1/activities/
```

## <a name="request-body-parameters"></a>Paramètres du corps de la demande

| Paramètre | Description |
| --- | --- |
| filtres | Filtrer les objets avec tous les filtres de recherche pour la demande, consultez [filtres d’activité](api-activities.md#filters) pour plus d’informations |
| sortDirection | Sens du tri. Les valeurs possibles sont : `asc` et `desc` |
| sortField | Champs utilisés pour trier les activités. Les valeurs possibles sont les suivantes :<br />- **Date**: date à laquelle l’activité s’est produite<br />- **créé**: horodatage de l’enregistrement de l’activité |
| skip | Ignore le nombre spécifié d’enregistrements |
| limit | Nombre maximal d’enregistrements retournés par la requête |

## <a name="example"></a> Exemple

### <a name="request"></a>Requête

Voici un exemple de la requête.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/activities/" -d '{
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
