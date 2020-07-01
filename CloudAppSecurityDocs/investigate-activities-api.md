---
title: Examiner les activités à l’aide de l’API-Cloud App Security
description: Cet article fournit des informations sur l’utilisation de l’API pour examiner l’activité des utilisateurs dans Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/26/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: b85675f31e6e306ae6f62b2c8f3b50053f3adeb0
ms.sourcegitcommit: b15034dd50142afd8e95de22a9232f711b1eae6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85624515"
---
# <a name="investigate-activities-using-the-api"></a>Examiner les activités à l’aide de l’API

*S’applique à : Microsoft Cloud App Security*

Microsoft Cloud App Security vous fournit une API REST entièrement prise en charge pour vous permettre d’interagir par programmation avec le service.

Vous pouvez utiliser les API Microsoft Cloud App Security pour analyser les activités effectuées par vos utilisateurs dans les applications Cloud connectées.

Le mode API des activités de Cloud App Security est optimisé pour l’analyse et la récupération de grandes quantités de données (plus de 5 000 activités). L’analyse des API interroge les données d’activité à plusieurs reprises jusqu’à ce que tous les résultats aient été analysés.

> [!NOTE]
> Pour les grandes quantités d’activités et les déploiements à grande échelle, nous vous recommandons d’utiliser l' [agent Siem](siem.md) pour l’analyse des activités.

**Pour utiliser l’API d’analyse des activités :**

1. Exécutez la requête sur vos données.
1. S’il y a plus d’enregistrements qu’il n’est possible de répertorier dans une seule analyse, vous recevrez une commande de retour avec `nextQueryFilters` que vous devez exécuter. Vous obtiendrez cette commande chaque fois que vous analyserez jusqu’à ce que la requête retournait tous les résultats.

**Paramètres du corps**de la demande :

- « filters » : filtrez les objets avec tous les filtres de recherche de la demande. pour plus d’informations, consultez [filtres d’activité](activity-filters.md) . Pour éviter que vos demandes ne soient limitées, veillez à inclure une limitation sur votre requête, par exemple, à interroger les activités du dernier jour ou à filtrer une application particulière.
- « isScan » : valeur booléenne. Active le mode d’analyse.
- "sortDirection" : le sens de tri, les valeurs possibles sont "ASC" et "desc"
- « sortField » : champs utilisés pour trier les activités. Les valeurs possibles sont les suivantes :
  - Date : date à laquelle l’activité s’est produite (valeur par défaut).
  - created : horodatage de l’enregistrement de l’activité.
- « Limit » : entier. En mode d’analyse, entre 500 et 5000 (la valeur par défaut est 500). Contrôle le nombre d’itérations utilisées pour l’analyse de toutes les données.

**Paramètres de réponse**:

- « Data » : données retournées. Va contenir jusqu’à « Limit » le nombre d’enregistrements de chaque itération. S’il y a plus d’enregistrements à extraire (hasNext = true), les derniers enregistrements seront supprimés pour s’assurer que toutes les données ne sont répertoriées qu’une seule fois.
- « hasNext » : valeur booléenne. Indique si une autre itération sur les données est nécessaire.
- « nextQueryFilters » : si une autre itération est nécessaire, elle contient la requête JSON consécutive à exécuter. Utilisez-le comme paramètre « Filters » dans la requête suivante.

L’exemple Python suivant obtient toutes les activités du jour précédent à partir d’Exchange Online.

``` python
import requests
import json
ACTIVITIES_URL = 'https://<your_tenant>.portal.cloudappsecurity.com/api/v1/activities/'

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
