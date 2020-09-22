---
title: Générer un script de bloc-API Cloud Discovery
description: Cet article décrit la demande de discovery_block_scripts dans l’API Cloud Discovery de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 542f4a010aa5ca5051dedb5bc3ca8f97913c4a4e
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90879817"
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
