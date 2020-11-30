---
title: Générer un script de bloc-API Cloud Discovery
description: Cet article décrit la demande de discovery_block_scripts dans l’API Cloud Discovery de Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: e4969772f2a1ae371753cddbd8e618b16b877e46
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314339"
---
# <a name="generate-block-script---cloud-discovery-api"></a>Générer un script de bloc-API Cloud Discovery

[!INCLUDE [Banner for top of topics](includes/banner.md)]

> [!NOTE]
> Cette demande n’est pas disponible pour Office 365 Cloud App Security.

Exécutez la requête d’extraction pour obtenir un script de blocage pour votre appliance réseau.

## <a name="http-request"></a>Demande HTTP

```rest
GET /api/discovery_block_scripts/
```

## <a name="request-url-parameters"></a>Paramètres d’URL de la requête

| Paramètre | Description |
| --- | --- |
| format | Format du dispositif réseau. |

Les formats suivants sont actuellement pris en charge :

| Appliance | Format |
| --- | --- |
| BlueCoat ProxySG | 102 |
| Cisco ASA | 104 |
| Fortinet FortiGate | 108 |
| Juniper SRX | 129 |
| Palo Alto | 112 |
| Websense | 135 |
| Zscaler | 120 |

> [!NOTE]
> Si vous ne trouvez pas votre appliance, générez un script de blocage manuellement à l’aide du portail.

## <a name="response"></a>response

Cette requête renvoie le script de bloc sous forme de texte.

## <a name="example"></a> Exemple

### <a name="request"></a>Requête

Voici un exemple de la requête.

```rest
curl -XGET -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/discovery_block_scripts/?format=102&type=banned"
```

### <a name="response"></a>response

```text
url.domain=application.com deny
url.domain=application.be deny
url.domain=application.co deny
```

[!INCLUDE [Open support ticket](includes/support.md)]
