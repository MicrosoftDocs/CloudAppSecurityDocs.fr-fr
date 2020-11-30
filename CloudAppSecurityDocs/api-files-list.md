---
title: API List-Files
description: Cet article décrit la requête de liste dans l’API de fichiers de Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: 644bfea227212e5b988eebc7e05aca8694a49f92
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96313999"
---
# <a name="list---files-api"></a>API List-Files

[!INCLUDE [Banner for top of topics](includes/banner.md)]

> [!NOTE]
>
> - Cette API sera bientôt dépréciée. Microsoft Cloud App Security développe une nouvelle solution pour identifier et agir sur des fichiers qui violent les stratégies.
> - Ce point de terminaison peut expirer lors du filtrage et de la pagination des collections volumineuses.
> - Cette API n’est pas disponible pour Office 365 Cloud App Security.

Exécutez la requête d’obtention ou de publication pour extraire une liste des fichiers correspondant aux filtres spécifiés.

## <a name="http-request"></a>Demande HTTP

```rest
GET /api/v1/files/
```

```rest
POST /api/v1/files/
```

## <a name="request-body-parameters"></a>Paramètres du corps de la demande

| Paramètre | Description |
| --- | --- |
| filtres | Filtrer les objets avec tous les filtres de recherche pour la demande, consultez [filtres de fichiers](api-files.md#filters) pour plus d’informations |
| skip | Ignore le nombre spécifié d’enregistrements |
| limit | Nombre maximal d’enregistrements retournés par la requête |

## <a name="example"></a> Exemple

### <a name="request"></a>Requête

Voici un exemple de la requête.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/files/" -d '{
  "filters": {
    // some filters
  },
  "skip": 5,
  "limit": 10
  ...
}'
```

### <a name="response"></a>response

Retourne une liste de fichiers au format JSON.

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
