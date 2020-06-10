---
title: API REST Cloud App Security
description: Cet article explique comment interagir avec Cloud App Security via HTTPs.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: df70a9408b88692b9faf789a00b5f307c0af24ee
ms.sourcegitcommit: 3172d6bd5e9d7a08f5cd2aa2e36980ef21bf0235
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84563897"
---
# <a name="cloud-app-security-rest-api"></a>API REST Cloud App Security

*S’applique à : Microsoft Cloud App Security*

Cet article explique comment interagir avec Cloud App Security via HTTPs.

L’API Microsoft Cloud App Security fournit l’accès par programmation à Cloud App Security par le biais de points de terminaison API REST. Les applications peuvent utiliser l’API pour effectuer des opérations de lecture et de mise à jour sur les objets et les données Cloud App Security. Par exemple, l’API Cloud App Security prend en charge les opérations courantes suivantes pour un objet utilisateur :

- Charger des fichiers journaux pour Cloud Discovery
- Générer un script de blocage
- Répertorier les activités et les alertes
- Ignorer ou résoudre les alertes

## <a name="api-url-structure"></a>Structure de l’URL de l’API

Pour utiliser l’API Cloud App Security, vous devez d’abord obtenir l’URL de l’API à partir de votre locataire. L’URL de l’API utilise le format suivant : `https://<portal_url>/api/<endpoint>` .

Pour obtenir l’URL du portail Cloud App Security pour votre locataire, procédez comme suit :

1. Dans le portail Cloud App Security, cliquez sur l’**icône de point d’interrogation** dans la barre de menus. Ensuite, sélectionnez **À propos de**.

    ![cliquez sur À propos de](media/about-menu.png)

1. Dans l’écran Cloud App Security à propos de, vous pouvez voir l’URL du portail.

    ![Afficher votre centre de données](media/api-url.png)

Une fois que vous avez l’URL du portail, ajoutez `/api` -lui le suffixe pour obtenir votre URL d’API. Par exemple, si l’URL de votre portail est `https://mytenant.us2.contoso.com` , votre URL d’API est `https://mytenant.us2.contoso.com/api` .

## <a name="api-tokens"></a>Jetons d’API

Cloud App Security nécessite un jeton d’API dans l’en-tête de toutes les requêtes d’API sur le serveur, comme suit :

```http
Authorization: Token <your_token_key>
```

Où `<your_token_key>` est votre jeton d’API personnel.

Pour plus d’informations sur les jetons d’API, consultez [gestion des jetons d’API](api-authentication.md).

### <a name="example"></a>Exemple

```rest
curl -XGET -H "Authorization:<your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/example-endpoint"
```

## <a name="what-actions-are-supported"></a>Quelles sont les actions prises en charge ?

Le tableau suivant décrit les actions prises en charge :

|Ressource|Verbes HTTP|Itinéraires URI|
|---|---|---|
|découverte,|Obtient, publie ou PUT|/api/v1/discovery/|
|Enrichissement des données|POST|/api/subnet/|
|Activités|GET ou POST|/api/v1/activities/|
|Alertes|GET ou POST|/api/v1/alerts/|
|Entités|GET ou POST|/api/v1/entities/|
|Fichiers|GET ou POST|/api/v1/files/|

Où la **ressource** représente un groupe d’entités associées.

## <a name="what-field-types-are-supported"></a>Quels sont les types de champs pris en charge ?

Le tableau suivant décrit les types de champs pris en charge :

|Champ|Description|
|---|---|
|string|Chaîne textuelle|
|boolean|Valeur booléenne représentant true/false|
|entier|Entier 32 bits signé|
|timestamp|Millisecondes écoulées depuis l’époque|

## <a name="limits"></a>limites

Vous pouvez choisir de limiter vos demandes en fournissant un paramètre Limit dans la demande.

Les méthodes suivantes sont prises en charge pour fournir le paramètre Limit :

- Encodé URL (avec `Content-Type: application/x-www-form-urlencoded` en-tête)
- Données de formulaire
- Corps JSON (avec `Content-Type: multipart/form-data` et un en-tête de limite approprié)

> [!NOTE]
>
> - Si aucune limite n’est spécifiée, la valeur par défaut 100 est définie.
> - Les réponses pour toutes les requêtes effectuées avec le jeton d’API sont limitées à un maximum de 100 éléments.

## <a name="filters"></a>Filtres

Lorsque vous avez un grand nombre de résultats, il est utile d’affiner les demandes à l’aide de filtres. Cette section décrit la structure des opérateurs et, qui peuvent être utilisés avec les filtres.

### <a name="structure"></a>Structure

Certains de nos points de terminaison d’API prennent en charge les filtres lors de l’exécution de requêtes. Dans les sections correspondantes, vous trouverez une référence qui répertorie tous les champs filtrables disponibles et les opérateurs pris en charge pour cette ressource.

La plupart des filtres prennent en charge plusieurs valeurs pour vous fournir des requêtes puissantes. Lors de la combinaison des filtres et des opérateurs, nous utilisons et comme opérateur logique entre les filtres.

### <a name="example"></a>Exemple

```rest
curl -XGET -H "Authorization:<your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/example-endpoint" -d '{
  "filters": {
    "some.field": {
      "eq": ["value1", "value2"],
      "isset": true
    },
    "some.field2": {
      "gte": 5
    }
  },
  "skip": 5,
  "limit": 10
}'
```

### <a name="operators"></a>Opérateurs

> [!NOTE]
> Tous les opérateurs ne sont pas compatibles avec tous les filtres.

Le tableau suivant décrit les opérateurs pris en charge :

| Opérateur | Type de réponse | Description |
| --- | --- | --- |
| contient | Liste de chaînes | Retourne tous les enregistrements pertinents contenant l’une des chaînes fournies. |
| deq | liste de valeurs | Retourne tous les enregistrements qui contiennent une valeur qui n’est pas égale à l’une des valeurs fournies. |
| descendantof | liste de valeurs | Retourne tous les enregistrements pertinents correspondant aux valeurs ou descendants de ceux-ci |
| doesnotstartwith | Liste de chaînes | Retourne tous les enregistrements pertinents ne commençant pas par chacune des chaînes fournies |
| endswith | Liste de chaînes | Retourne tous les enregistrements pertinents se terminant par l’une des chaînes fournies. |
| eq | liste de valeurs | Retourne tous les enregistrements pertinents contenant l’une des valeurs fournies. |
| gt | valeur unique | Retourne tous les enregistrements dont la valeur est supérieure à la valeur fournie. |
| GTE | valeur unique | Retourne tous les enregistrements dont la valeur est supérieure ou égale à la valeur fournie. |
| gte_ndays | nombre | Retourne tous les enregistrements dont la date est postérieure à N jours |
| isnotset | boolean | Quand la valeur est définie sur « true », retourne tous les enregistrements pertinents qui n’ont pas de valeur dans le champ spécifié |
| isset | boolean | Quand la valeur est définie sur « true », retourne tous les enregistrements pertinents qui ont une valeur dans le champ spécifié |
| lt | valeur unique | Retourne tous les enregistrements dont la valeur est inférieure à la valeur fournie. |
| LTE | valeur unique | Retourne tous les enregistrements dont la valeur est inférieure ou égale à la valeur fournie. |
| lte_ndays | nombre | Retourne tous les enregistrements dont la date est antérieure à N jours |
| ncontains | Liste de chaînes | Retourne tous les enregistrements pertinents qui ne contiennent pas l’une des chaînes fournies. |
| ndescendantof | liste de valeurs | Retourne tous les enregistrements pertinents qui ne correspondent pas à des valeurs ou descendants de ceux-ci |
| NEQ | liste de valeurs | Retourne tous les enregistrements pertinents qui ne contiennent pas toutes les valeurs fournies. |
| range | liste d’objets contenant les champs « Start » et « end » | Retourne tous les enregistrements dans l’une des plages fournies |
| startswith | Liste de chaînes | Retourne tous les enregistrements pertinents commençant par l’une des chaînes fournies |
| startswithsingle | string | Retourne tous les enregistrements pertinents commençant par la chaîne fournie. |
| text | string | Effectue une recherche en texte intégral sur tous les enregistrements |

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Authentification de l’API](api-authentication.md)

[!INCLUDE [Open support ticket](includes/support.md)]
