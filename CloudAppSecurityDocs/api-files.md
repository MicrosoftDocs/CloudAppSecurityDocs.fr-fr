---
title: API des fichiers Cloud App Security
description: Cet article fournit des informations sur l’utilisation de l’API de fichiers.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 6ad05db0010fd9a050a13cfddf19071204ef1977
ms.sourcegitcommit: 288f3011c0ce0e5f2d8cbaa9057a63be044465f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94375061"
---
# <a name="files-api"></a>API de fichiers

[!INCLUDE [Banner for top of topics](includes/banner.md)]

> [!NOTE]
>
> - Cette API sera bientôt dépréciée. Microsoft Cloud App Security développe une nouvelle solution pour identifier et agir sur des fichiers qui violent les stratégies.
> - Cette API n’est pas disponible pour Office 365 Cloud App Security.

L’API Files vous fournit des métadonnées sur les fichiers et dossiers stockés dans vos applications Cloud, telles que la date de la dernière modification, la propriété, etc.

La liste suivante répertorie les requêtes prises en charge :

- [Répertorier les fichiers](api-files-list.md)
- [Fichier d’extraction](api-files-fetch.md)

## <a name="filters"></a>Filtres

Pour plus d’informations sur le fonctionnement des filtres, consultez [filtres](api-introduction.md#filters).

Le tableau suivant décrit les filtres pris en charge :

| Filtrer | Type | Opérateurs | Description |
| --- | --- | --- | --- |
| service | entier | EQ, NEQ | Filtrer les fichiers à partir de l’appID d’application spécifié, par exemple : 11770 |
| instance | entier | EQ, NEQ | Filtrer les fichiers à partir des instances spécifiées |
| fileType | entier | EQ, NEQ | Filtrez les fichiers avec le type de fichier spécifié. Les valeurs possibles incluent :<br /><br />**0** : autres<br />**1** : document<br />**2** : feuille de calcul<br />**3** : présentation<br />**4** : texte<br />**5** : image<br />**6** : dossier |
| allowDeleted | boolean | eq | Les valeurs possibles incluent :<br /><br />**true** : retourne les fichiers supprimés<br />**false** ou not set : retourne les fichiers non supprimés (y compris les fichiers supprimés). Ce sera remplacé par l’opérateur poubelle |
| policy | string | cabinetmatchedrulesequals, NEQ, isset, isnotset | Filtrer les activités liées aux stratégies spécifiées |
| filename | string | eq | Filtrer les fichiers par nom de fichier |
| modifiedDate | timestamp | ETL, GTE, plage, lte_ndays, gte_ndays | Filtrer les fichiers à la date de leur dernière modification |
| createdDate | timestamp | ETL, GTE, plage | Filtrer les fichiers à la date de leur création |
| collaborateurs. Entity | CP d’entité | EQ, NEQ | Filtrer les fichiers partagés avec les entités spécifiées. Exemple : `[{ "id": "entity-id", "saas": 11161, "inst": 0 }]` |
| collaborateurs. domaines | string | EQ, NEQ | Filtrer les fichiers partagés avec les domaines spécifiés |
| collaborateurs. Groups | string | EQ, NEQ | Filtrer les fichiers partagés avec les groupes spécifiés |
| collaborateurs. withDomain | string | EQ, NEQ, DEQ | Filtrer les fichiers partagés avec les domaines spécifiés |
| propriétaire. entité | CP d’entité | EQ, NEQ | Filtrer les fichiers appartenant à des entités spécifiées. Exemple : `[{ "id": "entity-id", "saas": 11161, "inst": 0 }]` |
| propriétaire. unité | string | EQ, NEQ | Filtrer les fichiers avec des propriétaires à partir d’unités d’organisation spécifiées |
| partager | entier | EQ, NEQ | Filtrer les fichiers avec les niveaux de partage spécifiés. Les valeurs possibles incluent :<br /><br />**4** : public (Internet)<br />**3** : public<br />**2** : externe<br />**1** : interne<br />**0** : privé |
| fileId | string | EQ, NEQ | Filtrer les fichiers par ID de fichier |
| fileLabels | string | EQ, NEQ, isset, isnotset | Filtrer les fichiers contenant les identificateurs d’étiquette de fichier (balises) spécifiés |
| fileScanLabels | string | EQ, NEQ, isset, isnotset | Filtrer les fichiers contenant les ID d’avertissements d’inspection de contenu (balises) spécifiés |
| extension | string | EQ, NEQ | Filtrer les fichiers par une extension de fichier donnée |
| mimeType | string | EQ, NEQ | Filtrer les fichiers selon un type MIME donné, doit être une chaîne unique |
| Corbeille | boolean | eq | Les valeurs possibles incluent :<br /><br />**true** : retourne uniquement les fichiers supprimés<br />**false** : retourne les fichiers non supprimés |
| parentFolder | dossier | EQ, NEQ | Filtrer les fichiers contenus dans les dossiers spécifiés |
| dossier | boolean | eq | Les valeurs possibles incluent :<br /><br />**true** : retourne uniquement les dossiers<br >**false** : retourne uniquement les fichiers |
| mis en quarantaine | boolean | eq | Les valeurs possibles incluent :<br /><br />**true** : retourne uniquement les fichiers en quarantaine<br />**false** : retourne uniquement les fichiers non mis en quarantaine |
| snapshotLastModifiedDate | timestamp | ETL, GTE, plage | Filtrer les fichiers en fonction de la date de la dernière modification de leur instantané |

[!INCLUDE [Open support ticket](includes/support.md)]
