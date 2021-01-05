---
title: Gérer les plages d’adresses IP à l’aide de l’API
description: Cet article fournit des informations sur l’utilisation de l’API pour gérer des plages d’adresses IP dans Cloud App Security.
ms.date: 01/04/2021
ms.topic: how-to
ms.openlocfilehash: 4351649e023128cbb7635c366e3ab5449956c144
ms.sourcegitcommit: 90df07ce9cd64fd9c46fb6563f0249079204e174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97859200"
---
# <a name="manage-ip-address-ranges-using-the-api"></a>Gérer les plages d’adresses IP à l’aide de l’API

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Vous pouvez utiliser les API d’enrichissement des données pour gérer les plages d’adresses IP.

## <a name="to-use-the-manage-ip-address-ranges-script"></a>Pour utiliser le script de gestion des plages d’adresses IP

1. Créez un fichier CSV avec les champs attendus suivants : nom, IP_Address_Ranges, catégorie, étiquette (ID) et Override_ISP_Name.

1. Mettez à jour les valeurs des variables de script suivantes : **OPTION_DELETE_ENABLED**, **IP_RANGES_BASE_URL**, **CSV_ABSOLUTE_PATH**, **YOUR_TOKEN**

    > [!IMPORTANT]
    > Si vous affectez à **OPTION_DELETE_ENABLED** la **valeur true**, toutes les plages d’adresses IP définies dans votre locataire mais qui n’existent pas dans les fichiers CSV seront supprimées du locataire par le script. Si vous utilisez cette option, assurez-vous que le fichier CSV définit toutes les plages d’adresses IP que vous souhaitez dans votre locataire.

1. Exécutez le script pour créer des enregistrements et mettre à jour les règles existantes avec le nom correspondant.

## <a name="request-body-parameters"></a>Paramètres du corps de la demande

- « filters » : filtrez les objets avec tous les filtres de recherche de la demande. pour plus d’informations, consultez [filtres d’enrichissement des données](api-data-enrichment.md#filters) . Pour éviter que vos demandes soient limitées, veillez à inclure une limitation sur votre requête.
- « Limit » : entier. En mode d’analyse, entre 500 et 5000 (la valeur par défaut est 500). Contrôle le nombre d’itérations utilisées pour l’analyse de toutes les données.

## <a name="response-parameters"></a>Paramètres de réponse

- « Data » : données retournées. Va contenir jusqu’à « Limit » le nombre d’enregistrements de chaque itération. S’il y a plus d’enregistrements à extraire (hasNext = true), les derniers enregistrements seront supprimés pour s’assurer que toutes les données ne sont répertoriées qu’une seule fois.
- « hasNext » : valeur booléenne. Indique si une autre itération sur les données est nécessaire.
- « nextQueryFilters » : si une autre itération est nécessaire, elle contient la requête JSON consécutive à exécuter. Utilisez-le comme paramètre « Filters » dans la requête suivante.

L’exemple Python suivant utilise le contenu d’un fichier CSV pour gérer (créer, mettre à jour ou supprimer) des plages d’adresses IP dans votre environnement de Cloud App Security.

```python
import csv
import requests
import json

OPTION_DELETE_ENABLED = False
IP_RANGES_BASE_URL = 'https://<tenant_id>.<tenant_region>.contoso.com/api/v1/subnet/'
IP_RANGES_UPDATE_SUFFIX = 'update_rule/'
IP_RANGES_CREATE_SUFFIX = 'create_rule/'
CSV_ABSOLUTE_PATH = 'rules.csv'
YOUR_TOKEN = '<your_token>'
HEADERS = {
  'Authorization': 'Token {}'.format(YOUR_TOKEN),
}

# Get all records.
def get_records():
  list_request_data = {
    # Optionally, edit to match your filters
    'filters': {},
    "skip": 0,
    "limit": 20
  }
  records = []
  has_next = True
  while has_next:
    content = json.loads(requests.post(IP_RANGES_BASE_URL, json=list_request_data, headers=HEADERS).content)
    response_data = content.get('data', [])
    records += response_data
    has_next = content.get('hasNext', False)
    list_request_data["skip"] += len(response_data)
  return records

# Rule fields are compared to the CSV row.
def rule_matching(record, ip_address_ranges, category, tag, isp_name, ):
  rule_exists_conditions = [sorted([subnet.get('originalString', False) for subnet in record.get('subnets', [])]) !=
                            sorted(ip_address_ranges.split(' ')),
                            str(record.get('category', False)) != category,
                            len(record.get('tags', [])) != len(tag.split(' ')) and
                            (len(record.get('tags', [])) != 0 and len(tag) == 1),
                            bool(record.get('organization', False)) != bool(isp_name) or
                            (record.get('organization', False) is not None and not isp_name)]
  if any(rule_exists_conditions):
    return False
  for tag in record.get('tags', []):
    tag_id = tag.get('id')
    if tag_id and tag_id not in tag.split(' '):
      return False
  return True

def create_update_rule(name, ip_address_ranges, category, tag, isp_name, records, request_data):
  for record in records:
    # Records are compared by name(unique).
    # This can be changed to id (to update the name), it will include adding id to the CSV and changing row shape.
    if record["name"] == name:
      # request_data["_tid"] = record["_tid"]
      if not rule_matching(record, ip_address_ranges, category, tag, isp_name):
        # Update existing rule
        json.loads(
          requests.post(f"{IP_RANGES_BASE_URL}{record['_id']}/{IP_RANGES_UPDATE_SUFFIX}", json=request_data, headers=HEADERS).content)
        return record
      else:
        # The exact same rule exists. no need for change.
        return record
  # Create new rule.
  requests.post(f"{IP_RANGES_BASE_URL}{IP_RANGES_CREATE_SUFFIX}", json=request_data, headers=HEADERS)

# Request data creation.
def create_request_data(name, ip_address_ranges, category, tag, isp_name):
  request_data = {"name": name, "subnets": ip_address_ranges.split(' '), "category": category,
                  "tags": tag.split(' ') if tag else ''}
  if isp_name:
    request_data["overrideOrganization"] = True
    request_data["organization"] = isp_name
  return request_data

def main():
  # CSV fields are: Name,IP_Address_Ranges,Category,Tag(id),Override_ISP_Name
  # Multiple values (eg: multiple subnets) will be space-separated. (eg: value1 value2)
  records = get_records()
  with open(CSV_ABSOLUTE_PATH, newline='\n') as your_file:
    reader = csv.reader(your_file, delimiter=',')
    for row in reader:
      name, ip_address_ranges, category, tag, isp_name = row
      request_data = create_request_data(name, ip_address_ranges, category, tag, isp_name)
      if records:
        # Existing records were retrieved from your tenant
        record = create_update_rule(name, ip_address_ranges, category, tag, isp_name, records, request_data)
        record_id = record['_id']
      else:
        # No existing records were retrieved from your tenant
        record_id = json.loads(requests.post(f"{IP_RANGES_BASE_URL}{IP_RANGES_CREATE_SUFFIX}", json=request_data, headers=HEADERS).content)
      if OPTION_DELETE_ENABLED:
        # Remove CSV file record from tenant records.
        if record_id:
          for record in records:
            if record['_id'] == record_id:
              records.remove(record)
  if OPTION_DELETE_ENABLED:
    # Delete remaining tenant records, i.e. records that aren't in the CSV file.
    for record in records:
      requests.delete(f"{IP_RANGES_BASE_URL}{record['_id']}/", headers=HEADERS)
  
if __name__ == '__main__':
  main()
```

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
