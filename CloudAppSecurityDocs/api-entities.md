---
title: API Cloud App Security Entities
description: Cet article fournit des informations sur l’utilisation de l’API Entities.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: ac5135136dac13af2ebbfc47e786804094cecd59
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314067"
---
# <a name="entities-api"></a>API Entités

[!INCLUDE [Banner for top of topics](includes/banner.md)]

> [!NOTE]
> Cette API n’est pas disponible pour Office 365 Cloud App Security.

L’API Entities fournit des informations de base sur les utilisateurs et les comptes à l’aide des applications Cloud de votre organisation, ce qui vous permet de comprendre les modèles d’utilisation des services.

La liste suivante répertorie les requêtes prises en charge :

- [Répertorier des entités](api-entities-list.md)
- [Récupérer l’entité](api-entities-fetch.md)
- [Récupérer l’arborescence des entités](api-entities-fetch-tree.md)

## <a name="filters"></a>Filtres

Pour plus d’informations sur le fonctionnement des filtres, consultez [filtres](api-introduction.md#filters).

Le tableau suivant décrit les filtres pris en charge :

| Filtrer | Type | Opérateurs | Description |
| --- | --- | --- | --- |
| type| string | EQ, NEQ | Filtrer les entités en fonction de leur type |
| isAdmin | string | eq | Filtrer les entités qui sont des administrateurs |
| entité | CP d’entité | EQ, NEQ | Filtrer les entités avec des entités spécifiques clés primaires. Si un utilisateur est sélectionné, renverra également tous ses comptes. Exemple : `[{ "id": "entity-id", "saas": 11161, "inst": 0 }]` |
| userGroups |string | EQ, NEQ | Filtrer les entités en fonction de leur ID de groupe associé |
| app | entier | EQ, NEQ | Filtrer les entités en utilisant des services avec l’ID SaaS spécifié, par exemple : 11770 |
| instance | entier | EQ, NEQ | Filtrer les entités en utilisant des services avec les Appstances spécifiés (ID SaaS et ID d’instance), par exemple : 11770, 1059065 |
| isExternal | boolean | eq | Affiliation de l’entité. Les valeurs possibles incluent :<br /><br />**true**: externe<br />**false**: interne<br />**null**: aucune valeur |
| domaine | string | EQ, NEQ, isset, isnotset | Domaine associé de l’entité |
| organization | string | EQ, NEQ, isset, isnotset | Filtrer les entités avec l’unité d’organisation spécifiée |
| lastSeen | timestamp | ETL, GTE, | les entités de filtre de plage ont été consultées pour la dernière fois entre les dates données |
| status | string | EQ, NEQ | Filtrer les entités par État. Les valeurs possibles incluent :<br /><br />**0**: N/A<br />**1**: intermédiaire<br />**2**: actif<br />**3**: suspendu<br />**4**: supprimé |
| score | entier | lt, gt, isset, isnotset | Filtrer les entités en fonction de leur score de priorité d’investigation |

[!INCLUDE [Open support ticket](includes/support.md)]
