---
title: Ignorer en bloc-API Alerts
description: Cet article décrit la demande de rejet en bloc dans l’API d’alertes de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 7caef6711d8e8dd526e0c684cdec72bce785db93
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505568"
---
# <a name="bulk-dismiss---alerts-api"></a>Ignorer en bloc-API Alerts

*S’applique à : Microsoft Cloud App Security*

Exécutez la demande de publication pour ignorer plusieurs alertes correspondant aux filtres spécifiés.

## <a name="http-request"></a>Demande HTTP

```rest
POST /api/v1/alerts/dismiss_bulk/
```

## <a name="request-body-parameters"></a>Paramètres du corps de la demande

| Paramètre | Description |
| --- | --- |
| filtres | Filtrer les objets avec tous les filtres de recherche pour la demande, consultez [filtres d’alerte](api-alerts.md#filters) pour plus d’informations |
| comment | Commentaire expliquant pourquoi les alertes sont rejetées |

## <a name="example"></a>Exemple

### <a name="request"></a>Requête

Voici un exemple de la requête.

```rest
curl -XPOST -H "Authorization:<your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/alerts/dismiss_bulk/" -d '{
  "comment": "Irrelevant",
  "filters": {
    "id": {
      "eq": [
        "55af7415f8a0a7a29eef2e1f",
        "55af741cf8a0a7a29eef2e20"
      ]
    }
  }
}'
```

[!INCLUDE [Open support ticket](includes/support.md)]
