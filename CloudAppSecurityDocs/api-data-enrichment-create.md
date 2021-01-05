---
title: Créer une plage d’adresses IP-API d’enrichissement des données
description: Cet article décrit la demande de création d’une plage d’adresses IP dans l’API d’enrichissement des données de Cloud App Security.
ms.date: 12/13/2020
ms.topic: reference
ms.openlocfilehash: 39cb7fc47146aec690b9418da28a2caa636749d0
ms.sourcegitcommit: 90df07ce9cd64fd9c46fb6563f0249079204e174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97859190"
---
# <a name="create-ip-address-range---data-enrichment-api"></a>Créer une plage d’adresses IP-API d’enrichissement des données

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Exécutez la demande de publication pour ajouter une nouvelle plage d’adresses IP.

## <a name="http-request"></a>Demande HTTP

```rest
POST /api/v1/subnet/create_rule/
```

## <a name="request-body-parameters"></a>Paramètres du corps de la demande

| Paramètre | Description |
| --- | --- |
| name | Nom unique de la plage |
| catégorie | ID de la catégorie de plage. La fourniture d’une catégorie vous permet de reconnaître facilement les activités à partir d’adresses IP intéressantes. Les valeurs possibles incluent :<br /><br />**1**: entreprise<br />**2**: administration<br />**3**: risqué<br />**4**: VPN<br />**5**: fournisseur de Cloud<br />**6**: autres |
| Sous-réseaux | Tableau de masques sous forme de chaînes (IPv4/IPv6) |
| Organisation (facultatif) | Fournisseur de services Internet inscrit |
| balises (facultatif) | Tableau d’objets nouveaux ou existants, y compris le nom de la balise, l’ID, la description, le modèle de nom et l’ID de locataire. |

## <a name="example"></a> Exemple

### <a name="request"></a>Requête

Voici un exemple de la requête.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/subnet/create_rule/" -d '{
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
