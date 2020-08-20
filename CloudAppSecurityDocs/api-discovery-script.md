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
ms.openlocfilehash: 55a5d50f8dbe0dbbe1a34fcca913bc25d3292e42
ms.sourcegitcommit: 6e47d0348283d105614d81db4e7737fc837ed20b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88657756"
---
# <a name="generate-block-script---cloud-discovery-api"></a>Générer un script de bloc-API Cloud Discovery

*S’applique à : Microsoft Cloud App Security*

> [!NOTE]
> Cette demande n’est pas disponible pour Office 365 Cloud App Security.

Exécutez la requête d’extraction pour obtenir un script de blocage pour votre appliance réseau.

## <a name="http-request"></a>Demande HTTP

```rest
GET /api/discovery/discovery_block_scripts/
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

## <a name="example"></a>Exemple

### <a name="request"></a>Requête

Voici un exemple de la requête.

```rest
curl -XGET -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/discovery/discovery_block_scripts/?format=102&type=banned"
```

### <a name="response"></a>response

```text
url.domain=application.com deny
url.domain=application.be deny
url.domain=application.co deny
```

[!INCLUDE [Open support ticket](includes/support.md)]