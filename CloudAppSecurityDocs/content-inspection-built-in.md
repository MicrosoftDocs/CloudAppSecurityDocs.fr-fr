---
title: Comment Cloud App Security réalise l’inspection du contenu
description: Cet article décrit le processus suivi par Cloud App Security lors de l’exécution de l’inspection du contenu DLP sur les données de votre cloud.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 194187117a64db4a3267291c75bd68f694d655f7
ms.sourcegitcommit: 6eff466c7a6817b14a60d8c3b2c201c7ae4c2e2c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74719736"
---
# <a name="built-in-content-inspection"></a>Inspection du contenu intégré

*S’applique à : Microsoft Cloud App Security*

Cet article décrit le processus suivi par Microsoft Cloud App Security lors de l’exécution de l’inspection du contenu DLP intégrée sur les données de votre cloud.

L’inspection du contenu Cloud App Security fonctionne comme suit :

1. Cloud App Security effectue une analyse en quasi temps réel des lecteurs et événements qui sont détectés comme étant nouveaux ou modifiés.
2. Une fois cette analyse terminée, Cloud App Security effectue une analyse continue de tous les fichiers pertinents dans tous les lecteurs.

Les fichiers de l’analyse en quasi temps réel et les fichiers de l’analyse continue sont ajoutés à la file d’attente pour l’inspection. L’ordre des fichiers dans la file d’attente d’analyse est défini selon l’activité sur les fichiers et l’analyse de vos lecteurs. Les fichiers sont analysés seulement si les métadonnées des fichiers indiquent qu’il s’agit d’un type MIME pris en charge. Cette analyse concerne les fichiers appropriés pour l’analyse des données (documents, images, présentations, feuilles de calcul, fichiers texte et compressés/archives).

Une fois qu’un fichier est analysé, les actions suivantes se produisent :

1. Cloud App Security applique toutes vos stratégies personnalisées qui sont liées aux métadonnées et non au contenu proprement dit, par exemple une stratégie qui vous avertit quand la taille des fichiers dépasse 20 Mo ou lorsque des fichiers docx sont enregistrés dans OneDrive.

2. Si une stratégie nécessite une inspection du contenu et que le fichier répond aux critères d’inspection du contenu, le contenu est mis en file d’attente pour inspection. La longueur de la file d’attente dépend de la taille du client et du nombre de fichiers qui nécessitent une analyse.

3. À ce stade, vous pouvez afficher l’état de l’inspection du contenu en accédant à **Examiner** > **Fichiers** et en cliquant sur un fichier. Dans le tiroir de fichier qui s’ouvre avec les détails du fichier, **l’état d’inspection du contenu** indique **Terminé**, **En attente**, **Non applicable** (si le type de fichier n’est pas pris en charge) ou un message d’échec. Pour plus d’informations sur les messages d’échec relatifs à l’analyse du contenu, consultez [Résolution des problèmes d’inspection du contenu](troubleshooting-content-inspection.md).

> [!NOTE]
> Si vous voyez un tiret dans l’état d’analyse, cela signifie que le fichier ne figure pas dans une file d’attente en vue d’être analysé. Pour plus d’informations sur la définition de stratégies d’inspection du contenu, consultez [Stratégies de fichier](data-protection-policies.md).

Les stratégies d’analyse d’inspection du contenu intégrées peuvent rechercher les éléments suivants :

- Adresses e-mail
- Numéros de carte de crédit
  - Toutes les sociétés émettrices de cartes de crédit (Visa, MasterCard, American Express, Diners Club, Discover, JCB, Dankort, UnionPay)
  - Délimiteurs (espace, point ou tiret)
  - Cette analyse inclut également la validation de Luhn
- Codes SWIFT
- Numéros de passeports internationaux
- Numéros de permis de conduire
- Dates
- Numéros d’acheminement bancaire ABA
- Codes d’identification bancaire
- Numéros de demande d’assurance-maladie (HICN) HIPAA
- Numéros d’identification de prestataire national (NPI) HIPAA
- Dates de naissance et noms complets dans le cadre des informations de santé protégées (PHI)
- Numéros de permis de conduire et d’identité de l’État de Californie
- Numéros de permis de conduire
- Adresses personnelles
- Passeports au format carte
- Numéros de sécurité sociale

## <a name="supported-languages"></a>Langues prises en charge

Le moteur d’inspection du contenu Cloud App Security :

- Prend en charge tous les caractères Unicode
- Couvre plus de 1 000 types de fichiers
- Plusieurs langues sont prises en charge, tout particulièrement dans les fichiers qui utilisent des jeux de caractères Unicode. Veillez à définir vos stratégies de façon à prendre en compte ces langues. Par exemple, si vous recherchez des mots clés, vous devez entrer les mots clés pour les langues que vous prévoyez d’utiliser.
- Dans les types de fichiers texte qui utilisent un codage non-Unicode, par exemple le codage chinois GB2312, la comparaison avec les mots clés chinois Unicode ne fonctionnera pas comme attendu.
- Pour les types de fichiers qui s’appuient sur des bibliothèques tierces, la mise en correspondance des chaînes et des mots ne fonctionnera peut-être pas toujours comme prévu. C’est ce qui arrive fréquemment avec les fichiers (par exemple, les fichiers binaires) dans lesquels l’inspection du contenu s’appuie sur des bibliothèques tierces qui renvoient des chaînes en Java pour les jeux de caractères et de langues.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
