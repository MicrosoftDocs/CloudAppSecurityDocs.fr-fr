---
title: Effectuer le chargement de fichiers-API Cloud Discovery
description: Cet article décrit la demande d’exécution de chargement de fichier dans l’API Cloud Discovery de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: a943bf41934a6f90bd8d23b1b6bb358d673f35e7
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90880565"
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
