---
title: API Cloud App Security Alerts
description: Cet article fournit des informations sur l’utilisation de l’API alertes.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/20/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: f1176967bfcf67a458f55fe9421575df329aabe7
ms.sourcegitcommit: 6ae1c05025a49ad3c8e8cecd0c10dc05edcd9bf8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92929078"
---
# <a name="alerts-api"></a>API alertes

[!INCLUDE [Banner for top of topics](includes/banner.md)]

L’API Alerts vous fournit des informations sur les risques immédiats identifiés par Cloud App Security et nécessitant votre attention. Les alertes peuvent provenir de modèles d’utilisation suspects ou de fichiers contenant du contenu qui ne respecte pas la stratégie de l’entreprise.

La liste suivante répertorie les requêtes prises en charge :

- [Lister les alertes](api-alerts-list.md)
- [Fermer les alertes bénignes](api-alerts-close-benign.md)
- [Fermer les faux positifs](api-alerts-close-false-positive.md)
- [Fermer les vrais positifs](api-alerts-close-true-positive.md)
- [Récupérer l’alerte](api-alerts-fetch.md)
- [Marquer l’alerte comme lue](api-alerts-mark-read.md)
- [Marquer l’alerte comme non lue](api-alerts-mark-unread.md)

## <a name="deprecated-requests"></a>Demandes déconseillées

Le tableau suivant répertorie les requêtes déconseillées comme obsolètes et les requêtes qui les remplacent.

| Demande obsolète | Alternative |
| --- | --- |
| Ignorer en bloc | [Fermer les faux positifs](api-alerts-close-false-positive.md) |
| Résoudre en bloc | [Fermer les vrais positifs](api-alerts-close-true-positive.md) |
| Ignorer l’alerte | [Fermer les faux positifs](api-alerts-close-false-positive.md) |

> [!NOTE]
> Les demandes déconseillées ont été mappées à leurs alternatives afin d’éviter toute interruption. Toutefois, si vous utilisez des requêtes obsolètes dans votre environnement, nous vous recommandons de les mettre à jour vers leurs alternatives.

## <a name="filters"></a>Filtres

Pour plus d’informations sur le fonctionnement des filtres, consultez [filtres](api-introduction.md#filters).

Le tableau suivant décrit les filtres pris en charge :

| Filtrer | Type | Opérateurs | Description |
| --- | --- | --- | --- |
| entité. Entity | CP d’entité | EQ, NEQ | Filtrer les alertes liées aux entités spécifiées. Exemple : `[{ "id": "entity-id", "saas": 11161, "inst": 0 }]` |
| entité. IP | string | EQ, NEQ | Filtrer les alertes liées à des adresses IP spécifiées |
| entité. service | entier | EQ, NEQ | Filtrer les alertes liées à l’appId de service spécifié, par exemple : 11770 |
| entité. instance | entier | EQ, NEQ | Filtrer les alertes liées aux instances spécifiées, par exemple : 11770, 1059065 |
| entité. Policy | string | EQ, NEQ | Filtrer les alertes liées aux stratégies spécifiées |
| entité. fichier | string | EQ, NEQ | Filtrer les alertes liées au fichier spécifié |
| alertOpen | boolean | eq | Si la valeur est définie sur « true », retourne uniquement les alertes ouvertes, si la valeur est « false », retourne uniquement les alertes fermées |
| severity | entier | EQ, NEQ | Filtrez par gravité. Les valeurs possibles incluent :<br /><br />**0** : faible<br />**1** : moyenne<br/>**2** : élevé |
| resolutionStatus | entier | EQ, NEQ | Filtrer par État de résolution d’alerte, les valeurs possibles sont les suivantes :<br /><br />**0** : ouvrir <br />**1** : ignoré (État hérité)<br />**2** : résolu (État hérité)<br />**3** : fermé comme faux positif<br />**4** : fermé comme Bénin<br />**5** : fermé comme vrai positif |
| lire | boolean | eq | Si la valeur est définie sur « true », retourne uniquement les alertes de lecture, si la valeur est « false », retourne des alertes non lues |
| Date | timestamp | ETL, GTE, plage, lte_ndays, gte_ndays | Filtrer en fonction de l’heure à laquelle une alerte a été déclenchée |
| resolutionDate | timestamp | ETL, GTE, plage | Filtrer en fonction de l’heure à laquelle une alerte a été résolue |
| risquent | entier | EQ, NEQ | Filtrer par risque |
| alertType | entier | EQ, NEQ | Filtrer par type d’alerte |
| id | string | EQ, NEQ | Filtrer par ID d’alerte |
| source | string | eq | Origine de l’alerte, intégrée ou stratégie |

[!INCLUDE [Open support ticket](includes/support.md)]
