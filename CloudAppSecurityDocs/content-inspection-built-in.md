---
title: Comment Cloud App Security effectue l’inspection du contenu
description: Cet article décrit le processus Cloud App Security suit lorsque vous effectuez l’inspection du contenu DLP sur les données de votre Cloud.
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
ms.openlocfilehash: 543631f5ffaa6716d8686e86e1386b55c081158b
ms.sourcegitcommit: 288c279a0d2dd62a8ad8d7425c3e9e98857bf5f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2020
ms.locfileid: "80666474"
---
# <a name="built-in-content-inspection"></a>Inspection du contenu intégré

*S’applique à : Microsoft Cloud App Security*

Cet article décrit le processus Microsoft Cloud App Security suit lors de l’exécution de l’inspection intégrée du contenu DLP sur les données de votre Cloud.

Cloud App Security l’inspection du contenu fonctionne comme suit :

1. Tout d’abord, Cloud App Security effectue une analyse en temps quasi-réel (Diagnostics proactifs NRT) des lecteurs et des événements qui sont détectés comme nouveaux ou modifiés.
2. Une fois l’analyse terminée, Cloud App Security effectue une analyse continue de tous les fichiers pertinents dans tous les lecteurs.

Les fichiers de l’analyse Diagnostics proactifs NRT et l’analyse continue sont ajoutés à la file d’attente à des fins d’inspection. L’ordre des fichiers dans la file d’attente d’analyse est défini par activité sur les fichiers et à l’analyse de vos lecteurs. Les fichiers sont analysés uniquement si les métadonnées du fichier indiquent qu’il s’agit d’un type MIME pris en charge. Cette analyse concerne les fichiers qui sont pertinents pour l’analyse des données (documents, images, présentations, feuilles de calcul, texte et fichiers zip/d’archivage).

Après l’analyse d’un fichier, les actions suivantes se produisent :

1. Cloud App Security applique toutes vos stratégies personnalisées relatives aux métadonnées et non au contenu lui-même. Par exemple, une stratégie qui vous avertit lorsque des fichiers sont supérieurs à 20 Mo ou une stratégie qui vous avertit lorsque des fichiers docx sont enregistrés sur OneDrive.

2. Si une stratégie requiert une inspection du contenu et que le fichier est qualifié pour l’inspection du contenu, le contenu est mis en file d’attente à des fins d’inspection. La longueur de la file d’attente dépend de la taille du locataire et du nombre de fichiers qui nécessitent une analyse.

3. À ce stade, vous pouvez afficher l’état de l’inspection du contenu en accédant à **examiner** > **fichiers** et en cliquant sur un fichier. Dans le tiroir de fichier qui s’ouvre avec les détails du fichier, l’état de l' **inspection du contenu** s’affiche : **terminé**, **en attente**, **non applicable** (si le type de fichier n’est pas pris en charge) ou un message d’échec. Pour plus d’informations sur les messages d’échec de l’analyse du contenu, consultez [résolution des problèmes d’inspection du contenu](troubleshooting-content-inspection.md).

> [!NOTE]
> Si vous voyez un tiret dans l’état de l’analyse, cela signifie que le fichier n’est pas mis en file d’attente pour être analysé. Pour plus d’informations sur la définition des stratégies d’inspection du contenu, consultez [stratégies de fichier](data-protection-policies.md) .

Les stratégies d’analyse de l’inspection du contenu intégrées peuvent rechercher les éléments suivants :

- Adresses de messagerie
- Numéros de carte de crédit
  - Toutes les sociétés de carte de crédit (Visa, MasterCard, American Express, Diners Club, Discover, JCB, Dankort, UnionPay)
  - Délimiteurs-espace, point ou tiret
  - Cette analyse comprend également la validation Luhn
- Codes SWIFT
- Numéros de passeport internationaux
- Numéros de licence des pilotes
- Dates
- Numéros de transit de routage ABA de la Banque
- Codes des identificateurs bancaires
- Numéros de demande d’assurance maladie HICN HIPAA
- Numéros des identificateurs de fournisseurs nationaux NPI HIPAA
- Dates de naissance et de nom complet de PHI
- ID de Californie ou numéros de licence des pilotes
- Numéros de licence des pilotes
- Adresses personnelles
- Cartes Passport
- Numéros de sécurité sociale

## <a name="supported-languages"></a>Langues prises en charge

Le moteur d’inspection du contenu Cloud App Security :

- Prend en charge tous les caractères Unicode
- Couvre plus de 100 types de fichiers
- Plusieurs langues sont prises en charge, en particulier les fichiers qui utilisent des jeux de caractères Unicode. Veillez à définir vos stratégies pour prendre en compte ces langues. Par exemple, si vous recherchez des mots clés, vous devez placer les mots clés dans les langues que vous avez l’intention d’utiliser.
- Dans les types de fichiers basés sur du texte qui utilisent l’encodage non-Unicode, par exemple chinois GB2312, la comparaison avec les mots clés Unicode chinois ne fonctionnera pas comme prévu.
- Pour les types de fichiers qui reposent sur des bibliothèques tierces, les chaînes et les mots correspondants peuvent ne pas toujours fonctionner comme prévu. Cela est le plus courant dans les fichiers (tels que les types de fichiers binaires) dans lesquels l’inspection du contenu s’appuie sur des bibliothèques tierces qui retournent des chaînes Java pour la langue et les jeux de caractères.

## <a name="next-steps"></a>Étapes suivantes :

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
