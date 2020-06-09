---
title: Créer une plage d’adresses IP-API d’enrichissement des données
description: Cet article décrit la demande de création d’une plage d’adresses IP dans l’API d’enrichissement des données de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 790389f16409b5554fe44e0b20d2f584b0fd0fe5
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505408"
---
# <a name="create-ip-address-range---data-enrichment-api"></a>Créer une plage d’adresses IP-API d’enrichissement des données

*S’applique à : Microsoft Cloud App Security*

Exécutez la demande de publication pour ajouter une nouvelle plage d’adresses IP.

## <a name="http-request"></a>Demande HTTP

```rest
POST /cas/api/subnet/
```

## <a name="request-body-parameters"></a>Paramètres du corps de la demande

| Paramètre | Description |
| --- | --- |
| catégorie | ID de la catégorie de plage |
| subnetMasks | Tableau de masques sous forme de chaînes (IPv4/IPv6) |
| Organisation (facultatif) | Fournisseur de services Internet inscrit |
| balises (facultatif) | Tableau de balises (objets dont la propriété « Text » est définie avec le nom de la balise)-New ou Existing |

Les catégories suivantes sont actuellement prises en charge :

| Category | Id |
| --- | -- |
| Entreprise | 1 |
| Administratif | 2 |
| Déconseillé | 3 |
| VPN | 4 |
| Fournisseur de Cloud | 5 |
| Autres | 6 |

## <a name="example"></a>Exemple

### <a name="request"></a>Requête

Voici un exemple de la requête.

```rest
curl -XPOST -H "Authorization:<your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/cas/api/subnet/create_rule/" -d '{
  "name":"range name",
  "category":5,
  "organization":"Microsoft",
  "subnets":[
    "192.168.1.0/24",
    "192.168.2.0/16"
  ],
  "tags":[
    "existing tag"
  ]
}'
```

### <a name="response"></a>response

Retourne l’ID de la nouvelle plage sous la forme d’une chaîne.

[!INCLUDE [Open support ticket](includes/support.md)]
