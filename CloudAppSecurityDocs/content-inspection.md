---
title: Inspection du contenu | Documentation Microsoft
description: "Cet article décrit le processus suivi par Cloud App Security lors de l’exécution de l’inspection du contenu DLP sur les données de votre cloud."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/27/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 2401adbc-0011-4938-9e3a-a4c719a2f619
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 52f2245779568abbf41d47c4b45cdcced302529b
ms.openlocfilehash: 19d5b0624233da2af64cf35bd2e7ef8ca118c638


---

# <a name="content-inspection"></a>Inspection du contenu
Cet article décrit le processus suivi par Cloud App Security lors de l’exécution de l’inspection du contenu DLP sur les données de votre cloud. 


L’inspection du contenu Cloud App Security fonctionne comme suit :
1. Cloud App Security effectue une analyse en quasi temps réel des lecteurs et événements qui sont détectés comme étant nouveaux ou modifiés.
2. Une fois cette opération terminée, Cloud App Security effectue une analyse continue de tous les fichiers pertinents dans tous les lecteurs.  

Les fichiers de l’analyse en quasi temps réel et les fichiers de l’analyse continue sont ajoutés à la file d’attente pour l’inspection. L’ordre des fichiers dans la file d’attente d’analyse est défini selon l’activité sur les fichiers et l’analyse de vos lecteurs. Les fichiers sont analysés uniquement si les métadonnées de fichiers indiquent qu’il s’agit d’un type MIME pris en charge. Cette analyse concerne les fichiers qui sont appropriés pour l’analyse de données (documents, images, présentations, feuilles de calcul, fichiers texte et compressés/d’archive).  

Une fois qu’un fichier est analysé, les événements suivants se produisent :

1. Cloud App Security applique toutes vos stratégies personnalisées qui sont liées aux métadonnées et non au contenu proprement dit, par exemple une stratégie qui vous avertit quand la taille des fichiers dépasse 20 Mo ou lorsque des fichiers docx sont enregistrés dans OneDrive. 

2. Si une stratégie nécessite une inspection du contenu et que le fichier répond aux exigences d’inspection du contenu, le contenu est mis en file d’attente pour l’inspection. La longueur de la file d’attente dépend de la taille du client et du nombre de fichiers qui nécessitent une analyse. 

3. À ce stade, vous pouvez afficher l’état de l’inspection du contenu en accédant à **Examiner** > **Fichiers** et en cliquant sur un fichier. Dans le tiroir de fichier qui s’ouvre avec les détails du fichier, l’**état d’inspection du contenu** indique **Terminé**, **En attente**, **Non applicable** (si le type de fichier n’est pas pris en charge) ou un message d’échec. Pour plus d’informations sur les messages d’échec relatifs à l’analyse du contenu, consultez [Résolution des problèmes d’inspection du contenu](troubleshooting-content-inspection.md).

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



## <a name="see-also"></a>Voir aussi  
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  


<!--HONumber=Nov16_HO5-->


