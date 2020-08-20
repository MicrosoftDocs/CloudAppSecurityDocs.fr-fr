---
title: API FETCH-Activities
description: Cet article décrit la requête d’extraction dans l’API des activités de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 151edb2f763f55fa21f10b8b869703a31406dffb
ms.sourcegitcommit: 6e47d0348283d105614d81db4e7737fc837ed20b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88657667"
---
# <a name="fetch---activities-api"></a>API FETCH-Activities

*S’applique à : Microsoft Cloud App Security*

Exécutez la requête d’obtention pour extraire l’activité correspondant à la clé primaire spécifiée.

## <a name="http-request"></a>Demande HTTP

```rest
GET /api/v1/activities/<pk>/
```

## <a name="request-url-parameters"></a>Paramètres d’URL de la requête

| Paramètre | Description |
| --- | --- |
| pk | ID de l’activité |

## <a name="example"></a>Exemple

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
