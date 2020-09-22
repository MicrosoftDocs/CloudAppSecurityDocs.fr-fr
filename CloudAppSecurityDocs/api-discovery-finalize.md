---
title: Finaliser le chargement des fichiers-API Cloud Discovery
description: Cet article décrit la demande de done_upload dans l’API Cloud Discovery de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: a30fd3f257089d8d3aeda125f63ae2c695d6344c
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90880594"
---
# <a name="finalize-file-upload---cloud-discovery-api"></a>Finaliser le chargement des fichiers-API Cloud Discovery

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Une fois le téléchargement du contenu du fichier terminé, signalez-le afin de commencer le traitement du fichier.

## <a name="http-request"></a>Demande HTTP

```rest
POST /api/v1/discovery/done_upload/
```

## <a name="request-body-parameters"></a>Paramètres du corps de la demande

| Paramètre | Description |
| --- | --- |
| uploadUrl | URL retournée lors de l’appel initial demandant le chargement du fichier. |
| inputStreamName | Nom de la source de données à partir de laquelle les données sont envoyées (représente l’appareil). |
| uploadAsSnapshot | Téléchargez les données sous la forme d’un rapport d’instantané au lieu de les charger dans un rapport continu. Si ce paramètre est défini, le rapport est créé avec le nom spécifié dans inputStreamName. |

## <a name="example"></a> Exemple

### <a name="request"></a>Requête

Voici un exemple de la requête.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/discovery/done_upload/" -d "uploadUrl=<initiate_file_upload_response_url>"
```

[!INCLUDE [Open support ticket](includes/support.md)]
