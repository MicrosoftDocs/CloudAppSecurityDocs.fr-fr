---
title: API d’extraction d’arborescence d’entités
description: Cet article décrit la demande d’extraction d’arborescence d’entités dans l’API des entités de Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: 70e01ffa31ddfe13434c0a1705f2af98b43de6b5
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314288"
---
# <a name="fetch-entity-tree---entities-api"></a>API d’extraction d’arborescence d’entités

[!INCLUDE [Banner for top of topics](includes/banner.md)]

> [!NOTE]
> Cette demande n’est pas disponible pour Office 365 Cloud App Security.

Exécutez la requête d’obtention pour extraire toutes les entités associées à l’entité correspondant à la clé primaire spécifiée. Si l’entité est un utilisateur, extrait tous les comptes associés à l’utilisateur. Si l’entité est un compte, extrait le parent et les frères de l’entité.

## <a name="http-request"></a>Demande HTTP

```rest
GET /api/v1/entities/<pk>/retrieve_tree/
```

## <a name="request-url-parameters"></a>Paramètres d’URL de la requête

| Paramètre | Description |
| --- | --- |
| pk | ID de l’entité |

## <a name="example"></a> Exemple

### <a name="request"></a>Requête

Voici un exemple de la requête.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/entities/<pk>/retrieve_tree/"
```

### <a name="response"></a>response

Retourne l’arborescence d’entités spécifiée au format JSON.

```json
{
  // entity tree record
}
```

[!INCLUDE [Open support ticket](includes/support.md)]
