---
title: API Cloud App Security des activités
description: Cet article fournit des informations sur l’utilisation de l’API des activités.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 9ba5e83c10406308a1faf6e323fcfb9837da4b12
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90880037"
---
# <a name="activities-api"></a>API d’activités

[!INCLUDE [Banner for top of topics](includes/banner.md)]

L’API d’activité vous donne une visibilité sur toutes les actions effectuées dans vos applications Cloud. Les données de cette API peuvent fournir des informations sur les personnes qui se connectent à quelle application et quand, quels fichiers sont téléchargés à partir d’emplacements suspects, et ainsi de suite.

La liste suivante répertorie les requêtes prises en charge :

- [Lister les activités](api-activities-list.md)
- [Récupérer l’activité](api-activities-fetch.md)
- [Commentaires sur l’activité](api-activities-feedback.md)

## <a name="filters"></a>Filtres

Pour plus d’informations sur le fonctionnement des filtres, consultez [filtres](api-introduction.md#filters).

Le tableau suivant décrit les filtres pris en charge :

| Filtrer | Type | Opérateurs | Description |
| --- | --- | --- | --- |
| service | entier | EQ, NEQ | Filtrer les activités liées à l’appID de service spécifié, par exemple : 11770 |
| instance | entier | EQ, NEQ | Filtrer les activités à partir d’instances spécifiées |
| User. unité | string | EQ, NEQ, isset, isnotset | Filtrer les activités par l’unité d’organisation de l’utilisateur effectuant l’opération |
| Activity. eventType | string | EQ, NEQ | Filtrer les activités par type d’événement |
| activity.id | string | eq | Rechercher une activité par ID |
| Activity. emprunté | boolean | eq | Si la valeur est définie sur « true », retourne uniquement les événements empruntés, si la valeur est « false », retourne les événements qui ne sont pas empruntés. |
| Activity. type | boolean | eq | Si la valeur est « true », retourne uniquement les événements d’administration, si la valeur est « false », retourne des événements réguliers. |
| Activity. takenAction | string | EQ, NEQ | Filtrer les activités en fonction des actions effectuées sur celles-ci. Les valeurs possibles incluent :<br /><br />**bloquer**: bloqué<br />**proxy**: redirigé vers le contrôle de session<br />**BypassProxy**: ignorer le contrôle de session<br />**chiffrer**: chiffré<br />**déchiffrer**: déchiffré<br />**vérifié**: vérifié<br />**encryptionFailed**: échec du chiffrement<br />**protéger**: protégé<br />**vérification**: exiger une authentification de pas à pas<br />**null**: aucune action |
| Device. type | string | EQ, NEQ | Filtrer les activités par type d’appareil. Les valeurs possibles incluent :<br /><br />**Bureau**: PC<br />**Mobile**: mobile<br />**Tablette**: tablette<br />**Autre**: autre<br />**null**: aucune valeur |
| Device. Tags | string | EQ, NEQ | Filtrer les activités par ID de balise d’appareil |
| userAgent. userAgent | string | Contains, ncontains | Filtrer les activités qui ne contiennent pas les chaînes données dans l’agent utilisateur |
| userAgent. balises | string | EQ, NEQ | Filtrer les activités contenant les ID de balise de l’agent utilisateur spécifiés |
| Location. Country | string | EQ, NEQ, isset, isnotset | Filtrer les activités provenant du code de pays/région spécifié |
| emplacement. organisations | string | EQ, NEQ, isset, isnotset, Contains | Filtrer les activités provenant de l’organisation spécifiée |
| IP. adresse | string | EQ, StartsWith, doesnotstartwith, isset, isnotset, NEQ | Filtrer les activités provenant de l’adresse IP donnée |
| fileSelector | fichier | EQ, NEQ | Filtrer les activités contenant le fichier/dossier spécifié |
| office365url | string | StartsWith, EQ, EndsWith | Filtrer les activités par URL Office 365 |
| fileId | string | eq | Rechercher un fichier par ID |
| IP. Category | entier | EQ, NEQ | Filtrer les activités avec les catégories de sous-réseau spécifiées. Les valeurs possibles incluent :<br /><br />**1**: entreprise<br />**2**: administration<br />**3**: risqué<br />**4**: VPN<br />**5**: fournisseur de Cloud<br />**6**: autres |
| IP. Tags | string | EQ, NEQ | Filtrer les activités par ID de balise IP |
| text | string | EQ, startswithsingle, texte | Filtrer les activités en effectuant une recherche en texte libre |
| Date | timestamp | ETL, GTE, plage, lte_ndays, gte_ndays | Filtrer les activités qui se sont produites dans l’intervalle de temps spécifié |
| policy | string | EQ, NEQ, isset, isnotset | Filtrer les activités liées aux stratégies spécifiées |
| source | string | EQ, NEQ | Filtrez toutes les activités par type de source ou ID de flux. Exemple : les `[{ "s:stream-id", "t:source-type" }]` valeurs de type de source possibles sont les suivantes :<br /><br />**0**: contrôle d’accès<br />**1**: contrôle de session<br />**2**: connecteur d’application<br />**3**: analyse du connecteur d’applications<br />**5**: découverte<br />**6**: MDATP |
| Activity. alertiesd | string | eq | Filtrer toutes les activités relatives à un ID d’alerte |
| activityObject | string | EQ, NEQ | Filtrer les activités contenant l’ID spécifié |
| fileLabels | string | EQ, NEQ | Filtrer les fichiers contenant les identificateurs d’étiquette de fichier (balises) spécifiés |
| created || ETL, GTE, plage, gt, LT, EQ | Filtrer les activités qui ont été créées dans l’intervalle de temps spécifié |
| entité | CP d’entité | EQ, NEQ, isset, isnotset, StartsWith | Filtrer les activités par l’entité qui a effectué l’activité. Exemple : `[{ "id": "entity-id", "saas": 11161, "inst": 0 }]` |
| User. UserName | string | EQ, NEQ, isset, isnotset, StartsWith | Filtrer les activités par l’utilisateur qui a effectué l’activité |
| User. Tags | string | EQ, NEQ, isset, isnotset, StartsWith | Filtrer les activités par balises appartenant à l’utilisateur en cours d’exécution. Requiert des ID de groupe |
| User. Domain | string | EQ, NEQ, isset, isnotset | Filtrer les activités en effectuant le domaine de l’utilisateur |

[!INCLUDE [Open support ticket](includes/support.md)]
