---
title: Fermer l’API fausses alertes positives
description: Cet article décrit la demande de fermeture en bloc d’une alerte en tant que faux positif dans l’API des alertes de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/20/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 2783c414a7df2832136fbbbcbd2e319c2ac5ef02
ms.sourcegitcommit: ee40375712d2cc4090bd4e9cb58df486ec02aa62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92327029"
---
# <a name="close-false-positive---alerts-api"></a>Fermer l’API fausses alertes positives

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Exécutez la demande de publication pour fermer plusieurs alertes correspondant aux filtres spécifiés en tant que faux positif (une alerte sur une activité non malveillante).

## <a name="http-request"></a>Demande HTTP

```rest
POST /api/v1/alerts/close_false_positive/
```

## <a name="request-body-parameters"></a>Paramètres du corps de la demande

| Paramètre | Description |
| --- | --- |
| filtres | Filtrer les objets avec tous les filtres de recherche pour la demande, consultez [filtres d’alerte](api-alerts.md#filters) pour plus d’informations |
| comment | Commentaire expliquant pourquoi les alertes sont rejetées |
| reasonId | Raison de la fermeture des alertes en tant que faux positif. Fournir une raison permet d’améliorer la précision de la détection dans le temps. Les valeurs possibles incluent :<br /><br />**0**: non intéressant<br />**1**: trop d’alertes similaires<br />**3**: l’alerte n’est pas exacte<br />**4**: autre |
| sendFeedback | Valeur booléenne indiquant que les commentaires sur cette alerte sont fournis. Valeur par défaut : false |
| feedbackText | Texte des commentaires |
| allowContact | Valeur booléenne indiquant que le consentement de contacter l’utilisateur est fourni. Valeur par défaut : false |
| contactEmail | Adresse e-mail de l’utilisateur |

## <a name="example"></a> Exemple

### <a name="request"></a>Requête

Voici un exemple de la requête.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/alerts/close_false_positive/" -d '{
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
  "reasonId": 0,
  "sendFeedback": true,
  "feedbackText": "Feedback text",
  "allowContact": true,
  "contactEmail": " user@contoso.com"
}'
```

[!INCLUDE [Open support ticket](includes/support.md)]
