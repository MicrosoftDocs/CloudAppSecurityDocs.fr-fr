---
title: Examiner les activités à l’aide de l’API - Cloud App Security | Microsoft Docs
description: Cet article fournit des informations sur l’utilisation de l’API pour examiner les activités utilisateur dans Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 3/17/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 0f2f971d-10e3-496d-8004-96d9fad71cae
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 233df1cf7f01266bbca6c122a6908811e4c6649b
ms.sourcegitcommit: 57bad4dc9b28326c93ee480d308d52ea23c42089
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58163870"
---
# <a name="investigate-activities-using-the-api"></a>Examiner les activités à l’aide de l’API

*S’applique à : Microsoft Cloud App Security*

Vous pouvez utiliser l’API Microsoft Cloud App Security pour examiner les activités effectuées par vos utilisateurs sur des applications cloud connectées. 

Le mode de API d’activités Cloud App Security est optimisé pour l’analyse et la récupération de grandes quantités de données (plus de 5 000 activités). L’API analyse les données d’activité des requêtes à plusieurs reprises jusqu'à ce que tous les résultats ont été analysés. 

> [!NOTE] 
> Pour grandes quantités d’activités et les déploiements à grande échelle, nous recommendedthat que vous utilisez le [agent SIEM](siem.md) pour l’analyse de l’activité.

**Pour utiliser l’analyse de l’activité API :**

1. Exécutez la requête sur vos données.
1. S’il y a plus d’enregistrements que peuvent apparaître dans une seule analyse, vous obtiendrez une commande retournée avec `nextQueryFilters` que vous devez exécuter. Vous obtiendrez cette commande chaque fois que vous scannez jusqu'à ce que la requête a retourné tous les résultats.
 
 
**Paramètres de corps de la demande**:
- « filtres » : Filtre des objets avec tous les filtres de recherche pour la demande, consultez [filtres d’activité](activity-filters.md) pour plus d’informations. Pour éviter que vos demandes limitées, veillez à inclure une limitation de votre requête, par exemple, les activités du dernier jour de la requête ou de filtre pour une application particulière.
- « isScan » : Valeur booléenne. Active le mode d’analyse.
- « sortDirection » : Le sens de tri, les valeurs possibles sont « asc » et « desc » 
- « sortField » : Champs utilisés pour trier des activités. Les valeurs possibles sont les suivantes : 
    - date : date lorsque puis l’activité s’est produite (il s’agit de la valeur par défaut).
    - a été créé : l’horodatage lorsque l’activité a été enregistrée.
- « limite » : Entier. En mode d’analyse, entre 500 et 5 000 (500 par défaut). Contrôle le nombre d’itérations utilisées pour l’analyse de toutes les données. 

**Paramètres de réponse**:
- « données » : les données retournées. Contient jusqu'à « limiter » le nombre d’enregistrements de chaque itération. S’il existe plusieurs enregistrements à collecter (hasNext = true), le dernier peu d’enregistrements est supprimés pour vous assurer que toutes les données est répertoriée une seule fois.
- « hasNext » : Valeur booléenne. Indique si une autre itération sur les données est nécessaire.
- “nextQueryFilters”: Si une autre itération est nécessaire, elle contient la requête JSON consécutif à exécuter. Utilisez-le en tant que le paramètre « filtres » dans la demande suivante.



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
        
 
## <a name="next-steps"></a>Étapes suivantes
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)  
  
