---
title: API d’enrichissement des données Cloud App Security
description: Cet article fournit des informations sur l’utilisation de l’API d’enrichissement des données.
ms.date: 12/13/2020
ms.topic: reference
ms.openlocfilehash: d2050afec68bc29b0f401188b60c3dbb631a4a1b
ms.sourcegitcommit: 0768aa1992819e2651a14a731f79e178fdececc5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98114749"
---
# <a name="data-enrichment-api"></a>API d’enrichissement des données

[!INCLUDE [Banner for top of topics](includes/banner.md)]

L’API enrichissement de données vous permet de gérer des plages d’adresses IP identifiables, telles que les adresses IP physiques de votre bureau. Les plages d’adresses IP vous permettent de baliser, classer et personnaliser la façon dont les journaux et les alertes sont affichés et examinés. Pour plus d’informations, consultez [utilisation de plages d’adresses IP et de balises](ip-tags.md).

La liste suivante répertorie les requêtes prises en charge :

- [Liste des plages d’adresses IP](api-data-enrichment-list.md)
- [Créer une plage d’adresses IP](api-data-enrichment-create.md)
- [Mettre à jour une plage d’adresses IP](api-data-enrichment-update.md)
- [Supprimer une plage d’adresses IP](api-data-enrichment-delete.md)

## <a name="properties"></a>Propriétés

L’objet Response définit les propriétés suivantes.

| Propriété | Type | Description |
| --- | --- | --- |
| total | int | Nombre total d’enregistrements |
| hasNext | bool | Indique s’il existe des enregistrements supplémentaires |
| data | list | Liste des enregistrements existants |
| _id | string | ID unique de la plage d’adresses IP |
| name | string | Nom unique de la plage |
| Sous-réseaux | list | Tableau de masques, d’adresses IP (IPv4/IPv6) et de chaînes d’origine |
| location | string | Objet incluant le nom de l’emplacement, la latitude, la longitude, le code du pays et le nom du pays |
| organization | string | Fournisseur de services Internet inscrit |
| tags| list | Tableau d’objets nouveaux ou existants, y compris le nom de la balise, l’ID, la description, le modèle de nom et l’ID de locataire. |
| catégorie | int | Catégorie de la plage d’adresses IP. La fourniture d’une catégorie vous permet de reconnaître facilement les activités à partir d’adresses IP intéressantes. Les valeurs possibles incluent :<br /><br />**1**: entreprise<br />**2**: administration<br />**3**: risqué<br />**4**: VPN<br />**5**: fournisseur de Cloud<br />**6**: autres |
| lastModified | long | Horodateur de la dernière règle modifiée |

## <a name="filters"></a>Filtres

Pour plus d’informations sur le fonctionnement des filtres, consultez [filtres](api-introduction.md#filters).

Le tableau suivant décrit les filtres pris en charge :

| Filtrer | Type | Opérateurs | Description |
| --- | --- | --- | --- |
| catégorie | entier | EQ, NEQ | Filtrez les plages d’adresses IP par catégorie. Les valeurs possibles incluent :<br /><br />**1**: entreprise<br />**2**: administration<br />**3**: risqué<br />**4**: VPN<br />**5**: fournisseur de Cloud<br />**6**: autres |
| tags | string | EQ, NEQ | Filtrer les plages d’adresses IP par ID de balise |
| builtIn | bool | eq | Filtrez les plages d’adresses IP par type. Les valeurs possibles sont les suivantes : **true** (intégré) ou **false** (personnalisé) |

[!INCLUDE [Open support ticket](includes/support.md)]
