---
title: Liste-API d’enrichissement des données
description: Cet article décrit la requête de liste dans l’API d’enrichissement de données de Cloud App Security.
ms.date: 12/13/2020
ms.topic: reference
ms.openlocfilehash: a817431dc7788900294b8f6fde26beb326a21d87
ms.sourcegitcommit: 90df07ce9cd64fd9c46fb6563f0249079204e174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97859196"
---
# <a name="list---data-enrichment-api"></a>Liste-API d’enrichissement des données

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Exécutez la requête d’obtention ou de publication pour extraire une liste de plages d’adresses IP correspondant aux filtres spécifiés.

## <a name="http-request"></a>Demande HTTP

```rest
GET /api/v1/subnet/
```

```rest
POST /api/v1/subnet/
```

## <a name="request-body-parameters"></a>Paramètres du corps de la demande

| Paramètre | Description |
| --- | --- |
| filtres | Filtrer les objets avec tous les filtres de recherche pour la demande, consultez [filtres de plage d’adresses IP](api-data-enrichment.md#filters) pour plus d’informations |
| sortDirection | Sens du tri. Les valeurs possibles sont : `asc` et `desc` |
| sortField | Champs utilisés pour trier des plages d’adresses IP. Les valeurs possibles sont les suivantes :<br />- **catégorie**: catégorie de la plage d’adresses IP<br />- **Tags**: balises de la plage d’adresses IP<br />- **nom**: nom de la plage d’adresses IP |
| skip | Ignore le nombre spécifié d’enregistrements |
| limit | Nombre maximal d’enregistrements retournés par la requête |

## <a name="example"></a> Exemple

### <a name="request"></a>Requête

Voici un exemple de la requête.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/subnet/" -d '{
  "filters": {
    // some filters
  },
  "skip": 5,
  "limit": 10
  ...
}'
```

### <a name="response"></a>response

Retourne une liste de plages d’adresses IP au format JSON. Pour plus d’informations sur les champs de réponse, consultez [Propriétés](api-data-enrichment.md#properties).

```json
{
  "total": 1 // total number of records
  "hasNext": false // whether there is more data to show or not.
  "data": [
    {
      // returned records
      "_id": "5fd767259cd24bb563567d7c",
      "name": "range name",
      "subnets": [
        {
          "mask": 112,
          "address": "0000:0000:0000:0000:0000:ffff:c5c6:0000",
          "originalString": "197.198.192.20/16"
        }
      ],
      "location": {
        "name": "United States",
        "latitude": 39.5035514831543,
        "longitude": -99.01830291748047,
        "countryCode": "US",
        "countryName": "United States"
      },
      "organization": "isp name",
      "tags": [
        {
          "_id": "5ce2aaf42207ad108c76fa3a",
          "id": "000000290000000000000000",
          "target": 1,
          "type": 2,
          "name": "Contoso",
          "nameTemplate": {
            "template": "SAGE_BUILTIN_TAG_CONTOSO_NAME"
          },
          "description": "IP addresses used by Contoso",
          "descriptionTemplate": {
            "template": "SAGE_BUILTIN_TAG_CONTOSO_DESCRIPTION"
          },
          "visibility": 0,
          "status": 0,
          "_tid": 113348336
        }
      ],
      "category": 5,
      "lastModified": 1607952165309.8032,
      "_tid": 113348336
    }
  ]
}
```

[!INCLUDE [Open support ticket](includes/support.md)]
