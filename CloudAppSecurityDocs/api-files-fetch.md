---
title: API FETCH-Files
description: Cet article décrit la requête d’extraction dans l’API de fichiers de Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: 7d3faf9630edf3e277b481d5f8bcea87898e67cd
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314050"
---
# <a name="fetch---files-api"></a>API FETCH-Files

[!INCLUDE [Banner for top of topics](includes/banner.md)]

> [!NOTE]
>
> - Cette API sera bientôt dépréciée. Microsoft Cloud App Security développe une nouvelle solution pour identifier et agir sur des fichiers qui violent les stratégies.
> - Cette API n’est pas disponible pour Office 365 Cloud App Security.

Exécutez la requête d’obtention pour récupérer le fichier correspondant à la clé primaire spécifiée.

## <a name="http-request"></a>Demande HTTP

```rest
GET /api/v1/files/<pk>/
```

## <a name="request-url-parameters"></a>Paramètres d’URL de la requête

| Paramètre | Description |
| --- | --- |
| pk | ID du fichier |

## <a name="example"></a> Exemple

### <a name="request"></a>Requête

Voici un exemple de la requête.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/files/<pk>/"
```

### <a name="response"></a>response

Retourne le fichier spécifié.

[!INCLUDE [Open support ticket](includes/support.md)]
