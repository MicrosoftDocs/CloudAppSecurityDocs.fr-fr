---
title: Lancer le chargement de fichiers-API Cloud Discovery
description: Cet article décrit la demande de upload_url dans l’API Cloud Discovery de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: a4b86ef7bdda32e66744960dd3902aaef7e3034a
ms.sourcegitcommit: 6e47d0348283d105614d81db4e7737fc837ed20b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88657773"
---
# <a name="initiate-file-upload---cloud-discovery-api"></a>Lancer le chargement de fichiers-API Cloud Discovery

*S’applique à : Microsoft Cloud App Security*

Exécutez la requête d’extraction pour initier le processus de chargement. Cet appel, le premier des trois, retourne une URL qui sera utilisée ultérieurement pour effectuer la demande de chargement (PUT).

## <a name="http-request"></a>Demande HTTP

```rest
GET /api/v1/discovery/upload_url/
```

## <a name="request-url-parameters"></a>Paramètres d’URL de la requête

| Paramètre | Description |
| --- |--- |
| filename | Nom du fichier que vous souhaitez charger dans Cloud Discovery traitement |
| source | Type de Cloud Discovery fichier journal en cours de téléchargement |

Les types de sources suivants sont actuellement pris en charge :

- BARRACUDA
- BLUECOAT
- CHECKPOINT
- CHECKPOINT_CEF_SYSLOG
- CHECKPOINT_SMART_VIEW_TRACKER
- CHECKPOINT_XML
- CISCO_ASA
- CISCO_ASA_FIREPOWER
- CISCO_FIREPOWER_V6_SYSLOG
- CISCO_FWSM
- CISCO_IRONPORT_PROXY
- CISCO_IRONPORT_WSA_II
- CISCO_SCAN_SAFE
- CLAVISTER
- CORRATA
- FORCEPOINT
- FORCEPOINT_LEEF
- FORTIGATE
- GENERIC_CEF
- GENERIC_LEEF
- GENERIC_W3C
- I_FILTER
- IBOSS
- JUNIPER_SRX
- JUNIPER_SRX_SD
- JUNIPER_SRX_WELF
- JUNIPER_SSG
- MACHINE_ZONE_MERAKI
- MCAFEE_SWG
- MICROSOFT_ISA_W3C
- PALO_ALTO
- PALO_ALTO_LEEF
- SONICWALL_SYSLOG
- SOPHOS_CYBEROAM
- SOPHOS_SG
- SOPHOS_XG
- Cornet
- SQUID_NATIVE
- STORMSHIELD
- WEBSENSE_SIEM_CEF
- WEBSENSE_V7_5
- ZSCALER
- ZSCALER_CEF
- ZSCALER_QRADAR

> [!NOTE]
> Si vous ne trouvez pas votre format de fichier, effectuez un téléchargement manuel à l’aide du portail.

## <a name="response-parameters"></a>Paramètres de réponse

| Paramètre | Description |
| --- | --- |
| url | URL cible qui effectuera votre chargement de Cloud Discovery. |
| provider | « Azure » ou « AWS », indication précisant si le chargement est ciblé vers le stockage Windows Azure et le stockage de l’AWS à l’autre. |

## <a name="example"></a>Exemple

### <a name="request"></a>Requête

Voici un exemple de la requête.

```rest
curl -XGET -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/discovery/upload_url/?filename=my_discovery_file.txt&source=LOG_3COM"
```

### <a name="response"></a>response

Voici un exemple de réponse JSON.

```json
{
  "url": "https://<initiate_file_upload_response_url>",
  "provider": "azure"
}
```

[!INCLUDE [Open support ticket](includes/support.md)]
