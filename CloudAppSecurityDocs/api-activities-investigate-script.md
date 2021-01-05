---
title: Examiner les activités à l’aide de l’API
description: Cet article fournit des informations sur l’utilisation de l’API pour examiner l’activité des utilisateurs dans Cloud App Security.
ms.date: 12/22/2020
ms.topic: how-to
ms.openlocfilehash: 799e248ed69626b301d9281c43c14053b6ff03cf
ms.sourcegitcommit: 90df07ce9cd64fd9c46fb6563f0249079204e174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97859195"
---
# <a name="investigate-activities-using-the-api"></a>Examiner les activités à l’aide de l’API

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Vous pouvez utiliser les API d’activités pour analyser les activités effectuées par vos utilisateurs dans les applications Cloud connectées.

Le mode API des activités est optimisé pour l’analyse et la récupération de grandes quantités de données (plus de 5 000 activités). L’analyse des API interroge les données d’activité à plusieurs reprises jusqu’à ce que tous les résultats aient été analysés.

> [!NOTE]
> Pour les grandes quantités d’activités et les déploiements à grande échelle, nous vous recommandons d’utiliser l' [agent Siem](siem.md) pour l’analyse des activités.

## <a name="to-use-the-activity-scan-script"></a>Pour utiliser le script d’analyse des activités

1. Exécutez la requête sur vos données.
1. S’il y a plus d’enregistrements qu’il n’est possible de répertorier dans une seule analyse, vous recevrez une commande de retour avec `nextQueryFilters` que vous devez exécuter. Vous obtiendrez cette commande chaque fois que vous analyserez jusqu’à ce que la requête retournait tous les résultats.

## <a name="request-body-parameters"></a>Paramètres du corps de la demande

- « filters » : filtrez les objets avec tous les filtres de recherche de la demande. pour plus d’informations, consultez [filtres d’activité](activity-filters-queries.md) . Pour éviter que vos demandes ne soient limitées, veillez à inclure une limitation sur votre requête, par exemple, à interroger les activités du dernier jour ou à filtrer une application particulière.
- « isScan » : valeur booléenne. Active le mode d’analyse.
- "sortDirection" : le sens de tri, les valeurs possibles sont "ASC" et "desc"
- « sortField » : champs utilisés pour trier les activités. Les valeurs possibles sont les suivantes :
  - Date : date à laquelle l’activité s’est produite (valeur par défaut).
  - created : horodatage de l’enregistrement de l’activité.
- « Limit » : entier. En mode d’analyse, entre 500 et 5000 (la valeur par défaut est 500). Contrôle le nombre d’itérations utilisées pour l’analyse de toutes les données.

## <a name="response-parameters"></a>Paramètres de réponse

- « Data » : données retournées. Va contenir jusqu’à « Limit » le nombre d’enregistrements de chaque itération. S’il y a plus d’enregistrements à extraire (hasNext = true), les derniers enregistrements seront supprimés pour s’assurer que toutes les données ne sont répertoriées qu’une seule fois.
- « hasNext » : valeur booléenne. Indique si une autre itération sur les données est nécessaire.
- « nextQueryFilters » : si une autre itération est nécessaire, elle contient la requête JSON consécutive à exécuter. Utilisez-le comme paramètre « Filters » dans la requête suivante.

L’exemple Python suivant obtient toutes les activités du jour précédent à partir d’Exchange Online.

``` python
import requests
import json
ACTIVITIES_URL = 'https://<your_tenant>.<tenant_region>.contoso.com/api/v1/activities/'

your_token = '<your_token>'
headers = {
'Authorization': 'Token {}'.format(your_token),
}

filters = {
  # optionally, edit to match your filters
  'date': {'gte_ndays': 1},
  'service': {'eq': [20893]}
}
request_data = {
  'filters': filters,
  'isScan': True
}

records = []
has_next = True
while has_next:
    content = json.loads(requests.post(ACTIVITIES_URL, json=request_data, headers=headers).content)
    response_data = content.get('data', [])
    records += response_data
    print('Got {} more records'.format(len(response_data)))
    has_next = content.get('hasNext', False)
    request_data['filters'] = content.get('nextQueryFilters')

print('Got {} records in total'.format(len(records)))
```

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
