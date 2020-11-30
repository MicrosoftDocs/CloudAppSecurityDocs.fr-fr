---
title: Marquer en tant qu’API lecture-alertes
description: Cet article décrit la case à cocher en tant que requête de lecture dans l’API des alertes de Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: ecf314300e59371fc6cddaeddc0ab4b78efbaaa0
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314589"
---
# <a name="mark-as-read---alerts-api"></a>Marquer en tant qu’API lecture-alertes

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Exécutez la demande de publication pour marquer l’alerte correspondant à la clé primaire spécifiée comme lue.

## <a name="http-request"></a>Demande HTTP

```rest
POST /api/v1/alerts/<pk>/read/
```

## <a name="request-url-parameters"></a>Paramètres d’URL de la requête

| Paramètre | Description |
| --- | --- |
| pk | ID de l’alerte |

## <a name="example"></a> Exemple

### <a name="request"></a>Requête

Voici un exemple de la requête.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/alerts/<pk>/read/"
```

[!INCLUDE [Open support ticket](includes/support.md)]
