---
title: Résolution des erreurs d’inspection du contenu – Cloud App Security | Microsoft Docs
description: Cet article fournit la liste des états d’inspection du contenu et leur signification.
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
ms.openlocfilehash: be3c76516217e9cc36a06c85d778a717609ba254
ms.sourcegitcommit: 6eff466c7a6817b14a60d8c3b2c201c7ae4c2e2c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74721141"
---
# <a name="troubleshooting-content-inspection"></a>Résolution des problèmes d’inspection du contenu

*S’applique à : Microsoft Cloud App Security*

Cet article fournit la liste des états d’inspection du contenu et leur signification.

## <a name="content-inspection-status"></a>État de l’inspection du contenu

Le tableau liste les états d’inspection du contenu et leur description.

|État de l’inspection du contenu|Description|
|----|----|
|Completed|L’inspection du contenu s’est terminée correctement.|
|Not applicable|L’inspection du contenu n’était pas applicable pour ce fichier. Cet état peut apparaître si aucune stratégie ne nécessite l’inspection du contenu de ce fichier ou si le type de fichier n’est pas pris en charge.|
|Pending|Le fichier est actuellement dans la file d’attente de l’inspection du contenu.|
|Échec : erreur de téléchargement|Microsoft Cloud App Security n’a pas pu télécharger le fichier pour l’inspection.|
|Échec : le fichier est chiffré|Le fichier n’a pas pu être déchiffré.|
|Échec : le fichier est endommagé|Le fichier est endommagé et ne peut pas être inspecté.|
|Échec : erreur interne|Un problème non identifié est survenu lors de la tentative d’inspection du fichier.|
|Échec : erreur de la DLP externe|Un problème est survenu dans votre DLP externe et est à l’origine de l’échec de Cloud App Security lors de l’inspection du contenu.|
|Failed: File size exceeded (Échec : taille maximale de fichier dépassée)|La limite de fichier varie selon la taille du fichier et le nombre de caractères.|
|Échec : accès au fichier refusé|Le fichier est externe à votre cloud et n’est pas accessible par Cloud App Security.|
|Échec : le fichier a été supprimé|Le fichier n’existe plus dans votre cloud et ne peut pas être inspecté.|
|Échec : type de fichier non pris en charge|Cloud App Security ne peut pas effectuer d’inspection du contenu sur ce type de fichier. Cet état peut apparaître si le type de fichier n’est pas pris en charge ou si le fichier n’est pas réellement au format du type attendu.|

> [!NOTE]
> Si vous voyez un tiret dans l’état d’analyse, cela signifie que le fichier ne figure pas dans une file d’attente en vue d’être analysé. Pour plus d’informations sur la définition de stratégies d’inspection du contenu, consultez [Stratégies de fichier](data-protection-policies.md).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
