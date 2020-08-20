---
title: API d’extraction d’arborescence d’entités
description: Cet article décrit la demande d’extraction d’arborescence d’entités dans l’API des entités de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 2f39f0541569b4f4c127c3c1d9602e097b56a82b
ms.sourcegitcommit: 6e47d0348283d105614d81db4e7737fc837ed20b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88657739"
---
# <a name="fetch-entity-tree---entities-api"></a>API d’extraction d’arborescence d’entités

*S’applique à : Microsoft Cloud App Security*

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

## <a name="example"></a>Exemple

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
