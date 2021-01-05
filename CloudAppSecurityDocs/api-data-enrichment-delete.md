---
title: Supprimer la plage d’adresses IP-API d’enrichissement des données
description: Cet article décrit la demande de suppression de la plage d’adresses IP dans l’API d’enrichissement des données de Cloud App Security.
ms.date: 12/13/2020
ms.topic: reference
ms.openlocfilehash: 0cda04381501283526c77240debd7cfbe4f672fc
ms.sourcegitcommit: 90df07ce9cd64fd9c46fb6563f0249079204e174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97859203"
---
# <a name="delete-ip-address-range---data-enrichment-api"></a>Supprimer la plage d’adresses IP-API d’enrichissement des données

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Exécutez la requête de suppression pour supprimer une plage d’adresses IP.

## <a name="http-request"></a>Demande HTTP

```rest
DELETE /api/v1/subnet/<ip_range_id>/
```

## <a name="example"></a> Exemple

### <a name="request"></a>Requête

Voici un exemple de la requête.

```rest
curl -X DELETE -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/subnet/<ip_range_id>/"
```

[!INCLUDE [Open support ticket](includes/support.md)]
