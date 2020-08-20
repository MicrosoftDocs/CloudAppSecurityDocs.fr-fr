---
title: Marquer comme non lu-API alertes
description: Cet article décrit la demande Mark As non Read dans l’API des alertes de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 262163c5063e856957477166c6989a9bc5ae8e72
ms.sourcegitcommit: 6e47d0348283d105614d81db4e7737fc837ed20b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88657807"
---
# <a name="mark-as-unread---alerts-api"></a>Marquer comme non lu-API alertes

*S’applique à : Microsoft Cloud App Security*

Exécutez la demande de publication pour marquer l’alerte correspondant à la clé primaire spécifiée comme non lue.

## <a name="http-request"></a>Demande HTTP

```rest
POST /api/v1/alerts/<pk>/unread/
```

## <a name="request-url-parameters"></a>Paramètres d’URL de la requête

| Paramètre | Description |
| --- | --- |
| pk | ID de l’alerte |

## <a name="example"></a>Exemple

### <a name="request"></a>Requête

Voici un exemple de la requête.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/alerts/<pk>/unread/"
```

[!INCLUDE [Open support ticket](includes/support.md)]
