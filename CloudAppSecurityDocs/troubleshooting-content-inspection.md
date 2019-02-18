---
title: Résolution des erreurs d’inspection du contenu – Cloud App Security | Microsoft Docs
description: Cet article fournit la liste des états d’inspection du contenu et leur signification.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 359eb77f-e719-4c50-9b62-6ef64149a5a5
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: b3e3866b8cef8ae5b711145ffa104de88aed419e
ms.sourcegitcommit: 8ef0438fa35916c48625ff750cb85e9628d202f2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56281370"
---
# <a name="troubleshooting-content-inspection"></a>Résolution des problèmes d’inspection du contenu

*S’applique à : Microsoft Cloud App Security*

Cet article fournit la liste des états d’inspection du contenu et leur signification.

## <a name="content-inspection-status"></a>État de l’inspection du contenu

Le tableau liste les états d’inspection du contenu et leur description.

|État de l’inspection du contenu|Description|
|----|----|
|Completed|L’inspection du contenu s’est terminée correctement.|
|Non applicable|L’inspection du contenu n’était pas applicable pour ce fichier. Cet état peut apparaître si aucune stratégie ne nécessite l’inspection du contenu de ce fichier ou si le type de fichier n’est pas pris en charge.|
|Pending|Le fichier est actuellement dans la file d’attente de l’inspection du contenu.|
|Échec : Erreur de téléchargement|Microsoft Cloud App Security n’a pas pu télécharger le fichier pour l’inspection.|
|Échec : Le fichier est chiffré|Le fichier n’a pas pu être déchiffré.|
|Échec : Le fichier est endommagé|Le fichier est endommagé et ne peut pas être inspecté.|
|Échec : Erreur interne|Un problème non identifié est survenu lors de la tentative d’inspection du fichier.|
|Échec : Erreur de la DLP externe|Un problème est survenu dans votre DLP externe et est à l’origine de l’échec de Cloud App Security lors de l’inspection du contenu.|
|Échec : Taille maximale de fichier dépassée|La limite de fichier varie selon la taille du fichier et le nombre de caractères.|
|Échec : Accès au fichier refusé|Le fichier est externe à votre cloud et n’est pas accessible par Cloud App Security.|
|Échec : Le fichier a été supprimé|Le fichier n’existe plus dans votre cloud et ne peut pas être inspecté.|
|Échec : Type de fichier non pris en charge|Cloud App Security ne peut pas effectuer d’inspection du contenu sur ce type de fichier. Cet état peut apparaître si le type de fichier n’est pas pris en charge ou si le fichier n’est pas réellement au format du type attendu.|

> [!NOTE]
> Si vous voyez un tiret dans l’état d’analyse, cela signifie que le fichier ne figure pas dans une file d’attente en vue d’être analysé. Pour plus d’informations sur la définition de stratégies d’inspection du contenu, consultez [Stratégies de fichier](data-protection-policies.md).

## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)  

## <a name="next-steps"></a>Étapes suivantes
 
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

