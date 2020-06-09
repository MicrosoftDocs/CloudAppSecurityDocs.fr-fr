---
title: API Cloud App Security Alerts
description: Cet article fournit des informations sur l’utilisation de l’API alertes.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 0363d275c764d1e92d8d3f295de82e0c5bd2143a
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505438"
---
# <a name="alerts-api"></a>API alertes

*S’applique à : Microsoft Cloud App Security*

L’API Alerts vous fournit des informations sur les risques immédiats identifiés par Cloud App Security et nécessitant votre attention. Les alertes peuvent provenir de modèles d’utilisation suspects ou de fichiers contenant du contenu qui ne respecte pas la stratégie de l’entreprise.

La liste suivante répertorie les requêtes prises en charge :

- [Répertorier les alertes](api-alerts-list.md)
- [Ignorer en bloc](api-alerts-bulk-dismiss.md)
- [Résolution en bloc](api-alerts-bulk-resolve.md)
- [Extraire une alerte](api-alerts-fetch.md)
- [Ignorer l’alerte](api-alerts-dismiss.md)
- [Marquer l’alerte comme lue](api-alerts-mark-read.md)
- [Marquer l’alerte comme non lue](api-alerts-mark-unread.md)

## <a name="filters"></a>Filtres

Pour plus d’informations sur le fonctionnement des filtres, consultez [filtres](api-introduction.md#filters).

Le tableau suivant décrit les filtres pris en charge :

| Filtrer | Type | Opérateurs | Description |
| --- | --- | --- | --- |
| entité. Entity | CP d’entité | EQ, NEQ | Filtrer les alertes liées aux entités spécifiées. Exemple : `[{ "id": "entity-id", "saas": 11161, "inst": 0 }]` |
| entité. IP | string | EQ, NEQ | Filtrer les alertes liées à des adresses IP spécifiées |
| entité. service | entier | EQ, NEQ | Filtrer les alertes liées à l’appId de service spécifié, par exemple : 11770 |
| entité. instance | entier | EQ, NEQ | Filtrer les alertes liées aux instances spécifiées, par exemple : 11770, 1059065 |
| entité. Policy | string | EQ, NEQ | Filtrer les alertes liées aux stratégies spécifiées |
| entité. fichier | string | EQ, NEQ | Filtrer les alertes liées au fichier spécifié |
| severity | entier | EQ, NEQ | Filtrez par gravité. Les valeurs possibles incluent :<br /><br />**0**: faible<br />**1**: moyenne<br/>**2**: élevé |
| resolutionStatus | entier | EQ, NEQ | Filtrer par État de résolution d’alerte, les valeurs possibles sont les suivantes :<br /><br />**0**: ouvrir<br />**1**: ignoré<br />**2**: résolu |
| read | boolean | eq | Si la valeur est définie sur « true », retourne uniquement les alertes de lecture, si la valeur est « false », retourne des alertes non lues |
| Date | timestamp | ETL, GTE, plage, lte_ndays, gte_ndays | Filtrer en fonction de l’heure à laquelle une alerte a été déclenchée |
| resolutionDate | timestamp | ETL, GTE, plage | Filtrer en fonction de l’heure à laquelle une alerte a été résolue |
| risquent | entier | EQ, NEQ | Filtrer par risque |
| alertType | entier | EQ, NEQ | Filtrer par type d’alerte |
| id | string | EQ, NEQ | Filtrer par ID d’alerte |
| source | string | eq | Origine de l’alerte, intégrée ou stratégie |

[!INCLUDE [Open support ticket](includes/support.md)]
