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
ms.openlocfilehash: 61a8c7edb0533d4b7c6cf2228ef7a83c54541bd7
ms.sourcegitcommit: 6e47d0348283d105614d81db4e7737fc837ed20b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88657843"
---
# <a name="mark-as-read---alerts-api"></a>Marquer en tant qu’API lecture-alertes

*S’applique à : Microsoft Cloud App Security*

Exécutez la demande de publication pour marquer l’alerte correspondant à la clé primaire spécifiée comme lue.

## <a name="http-request"></a>Demande HTTP

```rest
POST /api/v1/alerts/<pk>/read/
```

## <a name="request-url-parameters"></a>Paramètres d’URL de la requête

| Paramètre | Description |
| --- | --- |
| pk | ID de l’alerte |

## <a name="example"></a>Exemple

### <a name="request"></a>Requête

Voici un exemple de la requête.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/alerts/<pk>/read/"
```

[!INCLUDE [Open support ticket](includes/support.md)]
