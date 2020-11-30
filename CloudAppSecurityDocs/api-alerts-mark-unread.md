---
title: Marquer comme non lu-API alertes
description: Cet article décrit la demande Mark As non Read dans l’API des alertes de Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: 5fb1a23183d0077a945fdfb1cb8637151921e509
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314560"
---
# <a name="mark-as-unread---alerts-api"></a>Marquer comme non lu-API alertes

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Exécutez la demande de publication pour marquer l’alerte correspondant à la clé primaire spécifiée comme non lue.

## <a name="http-request"></a>Demande HTTP

```rest
POST /api/v1/alerts/<pk>/unread/
```

## <a name="request-url-parameters"></a>Paramètres d’URL de la requête

| Paramètre | Description |
| --- | --- |
| pk | ID de l’alerte |

## <a name="example"></a> Exemple

### <a name="request"></a>Requête

Voici un exemple de la requête.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/alerts/<pk>/unread/"
```

[!INCLUDE [Open support ticket](includes/support.md)]
