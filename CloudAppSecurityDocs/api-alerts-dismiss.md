---
title: Faire disparaître-API Alerts
description: Cet article décrit la demande de rejet dans l’API des alertes de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: cebdc20f52b295106a2147f9438990504819e857
ms.sourcegitcommit: 4450119e1c7e2c54357dca955621327f9c343422
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2020
ms.locfileid: "88027021"
---
# <a name="dismiss---alerts-api"></a>Faire disparaître-API Alerts

*S’applique à : Microsoft Cloud App Security*

Exécutez la demande de publication pour faire disparaître l’alerte correspondant à la clé primaire spécifiée.

## <a name="http-request"></a>Demande HTTP

```rest
POST /api/v1/alerts/<pk>/dismiss/
```

## <a name="request-url-parameters"></a>Paramètres d’URL de la requête

| Paramètre | Description |
| --- | --- |
| pk | ID de l’alerte |

## <a name="request-body-parameters"></a>Paramètres du corps de la demande

| Paramètre | Description |
| --- | --- |
| comment | Commentaire expliquant pourquoi l’alerte a été rejetée |

## <a name="example"></a>Exemple

### <a name="request"></a>Requête

Voici un exemple de la requête.

```rest
curl -XPOST -H "Authorization:<your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/alerts/<pk>/dismiss/" -d '{
  "comment": "Irrelevant"
}'
```

[!INCLUDE [Open support ticket](includes/support.md)]
