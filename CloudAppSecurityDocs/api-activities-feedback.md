---
title: API de commentaires-activités
description: Cet article décrit la demande de commentaires dans l’API des activités de Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: f21dbee6d43236710f6a5846962c8444c52cddc7
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314730"
---
# <a name="feedback-on-activity---activities-api"></a>Commentaires sur l’API activité-activités

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Exécutez la demande de publication pour envoyer des commentaires sur l’activité correspondant à la clé primaire spécifiée.

## <a name="http-request"></a>Demande HTTP

```rest
POST /api/v1/activities/<pk>/feedback
```

## <a name="request-url-parameters"></a>Paramètres d’URL de la requête

| Paramètre | Description |
| --- | --- |
| pk | ID de l’activité |

## <a name="request-body-parameters"></a>Paramètres du corps de la demande

| Paramètre | Description |
| --- | --- |
| feedback | Commentaires pour l’activité |

## <a name="example"></a> Exemple

### <a name="request"></a>Requête

Voici un exemple de la requête.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/activities/<pk>/feedback" -d '{
  "feedbackValue": "0",
  "feedbackText": "Irrelevant",
  "allowContact": false,
  "contactEmail": "some.contact.address"
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
