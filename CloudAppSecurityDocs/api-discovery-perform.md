---
title: Effectuer le chargement de fichiers-API Cloud Discovery
description: Cet article décrit la demande d’exécution de chargement de fichier dans l’API Cloud Discovery de Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: 551a8a0434c916f1df7b591638908970712e9d28
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314424"
---
# <a name="perform-file-upload---cloud-discovery-api"></a>Effectuer le chargement de fichiers-API Cloud Discovery

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Chargez le contenu du fichier en effectuant une requête HTTP PUT. Vous devez utiliser l’URL renvoyée par la demande de [chargement de fichier](api-discovery-initiate.md) .

Azure et AWS ont des en-têtes et des limitations différents lors du chargement de fichiers sur l’URL cible.

> [!NOTE]
>
> - Vous pouvez télécharger des fichiers individuels d’une valeur pouvant atteindre 5 Go. Si vous devez charger des fichiers plus volumineux, scindez les données Cloud Discovery en plusieurs segments.
> - Si vous ne connaissez pas l’environnement que vous exécutez, consultez la demande de [lancement de chargement de fichier](api-discovery-initiate.md) qui renvoie ces informations.

## <a name="http-request"></a>Demande HTTP

```rest
PUT https://<initiate_file_upload_response_url>
```

> [!NOTE]
>
> Pour Azure :
> - Si votre fichier se trouve sous 64 Mo, ajoutez l’en-tête « x-ms-blob-type : BlockBlob » à votre demande.
> - Si la taille de votre fichier est supérieure à 64 Mo, téléchargez-le en bloc. le moyen le plus simple de procéder consiste à utiliser le [Kit de développement logiciel (SDK) Azure](https://azure.microsoft.com/downloads/).

## <a name="example"></a> Exemple

### <a name="request"></a>Requête

Voici un exemple de demande pour Azure.

```rest
curl --request PUT --upload-file <file_to_upload> -H "x-ms-blob-type: BlockBlob" "https://<initiate_file_upload_response_url>"
```

Voici un exemple de la demande pour le kit de développement logiciel (SDK) Azure Java.

```java
File fileReference = new File("file.name");
// Create a blob using the URI that contains the shared access signature.
CloudBlockBlob sasBlob = new CloudBlockBlob(uri);

// Upload the file to the blob.
sasBlob.upload(new FileInputStream(fileReference), fileReference.length());
```

[!INCLUDE [Open support ticket](includes/support.md)]
