---
title: Fermer l’API bénigne-Alerts
description: Cet article décrit la tentative de fermeture en bloc d’une alerte en tant que demande bénigne dans l’API des alertes de Cloud App Security.
ms.date: 10/20/2020
ms.topic: reference
ms.openlocfilehash: cf137f0476b588e66493fabde7bfae354cf41f15
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314662"
---
# <a name="close-benign---alerts-api"></a>Fermer l’API bénigne-Alerts

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Exécutez la demande de publication pour fermer les alertes multiples correspondant aux filtres spécifiés comme sans gravité (une alerte sur une activité suspecte, mais pas malveillante, comme un test de pénétration ou une autre action suspecte autorisée).

## <a name="http-request"></a>Demande HTTP

```rest
POST /api/v1/alerts/close_benign/
```

## <a name="request-body-parameters"></a>Paramètres du corps de la demande

| Paramètre | Description |
| --- | --- |
| filtres | Filtrer les objets avec tous les filtres de recherche pour la demande, consultez [filtres d’alerte](api-alerts.md#filters) pour plus d’informations |
| comment | Commentaire expliquant pourquoi les alertes sont rejetées |
| reasonId | Raison de la fermeture des alertes comme bénignes. Fournir une raison permet d’améliorer la précision de la détection dans le temps. Les valeurs possibles incluent :<br /><br />**2**: la gravité réelle est inférieure<br />**4**: autre<br />**5**: confirmé avec l’utilisateur final<br />**6**: déclenché par test |
| sendFeedback | Valeur booléenne indiquant que les commentaires sur cette alerte sont fournis. Valeur par défaut : false |
| feedbackText | Texte des commentaires |
| allowContact | Valeur booléenne indiquant que le consentement de contacter l’utilisateur est fourni. Valeur par défaut : false |
| contactEmail | Adresse e-mail de l’utilisateur |

## <a name="example"></a> Exemple

### <a name="request"></a>Requête

Voici un exemple de la requête.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/alerts/close_benign/" -d '{
  "filters": {
    "id": {
      "eq": [
        "55af7415f8a0a7a29eef2e1f",
        "55af741cf8a0a7a29eef2e20"
        "5f8d70bfc1ffb25b0a541c7d"
      ]
    }
  },
  "comment": "Irrelevant",
  "reasonId": 5,
  "sendFeedback": true,
  "feedbackText": "Feedback text",
  "allowContact": true,
  "contactEmail": " user@contoso.com"
}'
```

[!INCLUDE [Open support ticket](includes/support.md)]
