---
title: Fermer l’API des alertes positives vraies
description: Cet article décrit la demande de fermeture en bloc d’une alerte en tant que vrai positif dans l’API des alertes de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/20/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 1da36127115b2b3204d33a467b01bc7544838936
ms.sourcegitcommit: ee40375712d2cc4090bd4e9cb58df486ec02aa62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92327028"
---
# <a name="close-true-positive---alerts-api"></a>Fermer l’API des alertes positives vraies

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Exécutez la demande de publication pour fermer plusieurs alertes correspondant aux filtres spécifiés comme vrai positif (une alerte sur une activité malveillante confirmée).

## <a name="http-request"></a>Demande HTTP

```rest
POST /api/v1/alerts/close_true_positive/
```

## <a name="request-body-parameters"></a>Paramètres du corps de la demande

| Paramètre | Description |
| --- | --- |
| filtres | Filtrer les objets avec tous les filtres de recherche pour la demande, consultez [filtres d’alerte](api-alerts.md#filters) pour plus d’informations |
| comment | Commentaire expliquant pourquoi les alertes sont rejetées |
| sendFeedback | Valeur booléenne indiquant que les commentaires sur cette alerte sont fournis. Valeur par défaut : false |
| feedbackText | Texte des commentaires |
| allowContact | Valeur booléenne indiquant que le consentement de contacter l’utilisateur est fourni. Valeur par défaut : false |
| contactEmail | Adresse e-mail de l’utilisateur |

## <a name="example"></a> Exemple

### <a name="request"></a>Requête

Voici un exemple de la requête.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/alerts/close_true_positive" -d '{
  "filters": {
    "id": {
      "eq": [
        "55af7415f8a0a7a29eef2e1f",
        "55af741cf8a0a7a29eef2e20",
        "5f8d70bfc1ffb25b0a541c7d"
      ]
    }
  },
  "comment": "Irrelevant",
  "sendFeedback": true,
  "feedbackText": "Feedback text",
  "allowContact": true,
  "contactEmail": " user@contoso.com"
}'
```

[!INCLUDE [Open support ticket](includes/support.md)]
