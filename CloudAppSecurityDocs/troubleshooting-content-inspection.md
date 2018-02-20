---
title: "Résolution des erreurs d’inspection du contenu dans Cloud App Security | Microsoft Docs"
description: "Cette rubrique fournit une liste des états d’inspection du contenu et leur signification."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/15/2018
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 359eb77f-e719-4c50-9b62-6ef64149a5a5
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: be49af4df563d4aa2a05dd4830d2dd8835fa90d3
ms.sourcegitcommit: 458e936e1ac548eda37e9bf955b439199bbdd018
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2018
---
# <a name="troubleshooting-content-inspection"></a>Résolution des problèmes d’inspection du contenu
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

> [!NOTE]
> Si vous voyez un tiret dans l’état d’analyse, cela signifie que le fichier ne figure pas dans une file d’attente en vue d’être analysé. Pour plus d’informations sur la définition de stratégies d’inspection du contenu, consultez [Stratégies de fichier](data-protection-policies.md).

## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  