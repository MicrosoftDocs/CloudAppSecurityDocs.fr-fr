---
title: API FETCH-Alerts
description: Cet article décrit la requête d’extraction dans l’API des alertes de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 78ef3b8d2982a6f5228344b35f5d67dca9a6aec1
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90879836"
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
