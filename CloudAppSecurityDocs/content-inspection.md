---
title: Inspection du contenu | Documentation Microsoft
description: "Cet article décrit le processus suivi par Cloud App Security lors de l’exécution de l’inspection du contenu DLP sur les données de votre cloud."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 2401adbc-0011-4938-9e3a-a4c719a2f619
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: ea1854d6bf32e01afe6183409b68ded32ee37dd1


---

# <a name="content-inspection"></a>Inspection du contenu
Cet article décrit le processus suivi par Cloud App Security lors de l’exécution de l’inspection du contenu DLP sur les données de votre cloud. 


L’inspection du contenu Cloud App Security fonctionne comme suit :
1. Cloud App Security effectue une analyse continue de tous les fichiers pertinents dans tous les lecteurs. 
2. Cloud App Security effectue une analyse en temps quasi réel des lecteurs et événements qui sont détectés comme étant nouveaux ou modifiés. 

Les fichiers de l’analyse continue et les fichiers de l’analyse en temps quasi réel sont ajoutés à la file d’attente pour l’inspection. L’ordre des fichiers dans la file d’attente d’analyse est défini selon l’activité sur les fichiers et l’analyse de vos lecteurs. Les fichiers sont analysés uniquement si les métadonnées de fichiers indiquent qu’il s’agit d’un type MIME pris en charge. Cette analyse concerne les fichiers qui sont appropriés pour l’analyse de données (documents, images, présentations, feuilles de calcul, fichiers texte et compressés/d’archive).  

Une fois qu’un fichier est analysé, les événements suivants se produisent :

1. Cloud App Security applique toutes vos stratégies personnalisées qui sont liées aux métadonnées et non au contenu proprement dit, par exemple une stratégie qui vous avertit quand la taille des fichiers dépasse 20 Mo ou lorsque des fichiers docx sont enregistrés dans OneDrive. 

2. Si une stratégie nécessite une inspection du contenu et que le fichier répond aux exigences d’inspection du contenu, le contenu est mis en file d’attente pour l’inspection. La longueur de la file d’attente dépend de la taille du client et du nombre de fichiers qui nécessitent une analyse. 

3. À ce stade, vous pouvez afficher l’état de l’inspection du contenu en accédant à **Examiner** > **Fichiers** et en cliquant sur un fichier. Dans le tiroir de fichiers qui s’ouvre avec les détails du fichier, la colonne **État de l’inspection du contenu** affiche l’un des messages suivants : 

|État de l’inspection du contenu|Description|
|----|----|
|Completed|L’inspection du contenu s’est terminée correctement.|
|Non applicable|L’inspection du contenu n’était pas applicable pour ce fichier. Cela peut être dû au fait qu’aucune stratégie ne nécessite d’inspection du contenu de ce fichier ou que le type de fichier n’est pas pris en charge.|
|Pending|Le fichier est actuellement dans la file d’attente de l’inspection du contenu.|
|Échec : erreur de téléchargement|Cloud App Security n’a pas pu télécharger le fichier pour l’inspection.|
|Échec : le fichier est chiffré|Le fichier n’a pas pu être déchiffré.|
|Échec : le fichier est endommagé|Le fichier est endommagé et ne peut pas être inspecté.|
|Échec : erreur interne|Un problème non identifié est survenu lors de la tentative d’inspection du fichier.|
|Échec : erreur de la DLP externe|Un problème est survenu dans votre DLP externe et est à l’origine de l’échec de Cloud App Security lors de l’inspection du contenu.|
|Failed: File size exceeded (Échec : taille maximale de fichier dépassée)|La limite de fichier varie selon la taille du fichier et le nombre de caractères.|
|Échec : accès au fichier refusé|Le fichier est externe à votre cloud et n’est pas accessible par Cloud App Security.|
|Échec : le fichier a été supprimé|Le fichier n’existe plus dans votre cloud et ne peut pas être inspecté.|
|Échec : type de fichier non pris en charge|Cloud App Security ne peut pas effectuer d’inspection du contenu sur ce type de fichier. Cela peut être dû au fait que le type de fichier n’est pas pris en charge ou que le fichier n’est pas réellement au format du type attendu.|

## <a name="see-also"></a>Voir aussi  
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  


<!--HONumber=Oct16_HO4-->


