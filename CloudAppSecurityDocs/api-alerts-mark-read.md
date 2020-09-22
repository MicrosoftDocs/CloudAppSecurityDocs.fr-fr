---
title: Marquer en tant qu’API lecture-alertes
description: Cet article décrit la case à cocher en tant que requête de lecture dans l’API des alertes de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: d3469f45ed36ea2089ef659e9181fef1857454b2
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90880684"
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
