---
title: API Cloud App Security Cloud Discovery
description: Cet article fournit des informations sur l’utilisation de l’API Cloud Discovery.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 647570edd98fd1fd4977a9096fcf475f3ee09a8e
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505248"
---
# <a name="cloud-discovery-api"></a>API Cloud Discovery

*S’applique à : Microsoft Cloud App Security*

Cloud Discovery analyse les journaux système fournis par l’utilisateur pour détecter les applications nouvelles et inconnues dans votre environnement Cloud. Utilisez l’API Cloud Discovery pour automatiser le chargement des fichiers journaux de découverte de votre entreprise. Le processus de téléchargement de fichier se compose de 3 appels d’API qui doivent être appelés de façon consécutive.

En outre, Cloud App Security vous permet de bloquer l’accès aux applications non approuvées à l’aide de vos appliances de sécurité locales existantes. Utilisez l’appel de génération de script de bloc pour obtenir un script de bloc dédié et l’importer sur votre appliance.

La liste suivante répertorie les requêtes prises en charge :

- [Lancer le chargement de fichier](api-discovery-initiate.md)
- [Effectuer un chargement de fichier](api-discovery-perform.md)
- [Finaliser le chargement du fichier](api-discovery-finalize.md)
- [Générer un script de blocage](api-discovery-script.md)

[!INCLUDE [Open support ticket](includes/support.md)]
