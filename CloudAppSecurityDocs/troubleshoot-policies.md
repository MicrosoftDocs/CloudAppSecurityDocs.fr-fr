---
title: Résolution des problèmes des stratégies Cloud App Security
description: Cet article décrit la procédure de résolution des problèmes liés à la création de stratégies dans Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 828cc94a-248b-44f6-a1ba-c28c0a135f8c
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: cd309d6997486dcd84c072c28aedba1ef75d4284
ms.sourcegitcommit: b86c3afd1093fbc825fec5ba4103e3a95f65758e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53175717"
---
# <a name="troubleshooting-microsoft-cloud-app-security-policies"></a>Résolution des problèmes des stratégies Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

Cet article décrit la procédure de résolution des problèmes liés à la création de stratégies dans Cloud App Security.

## <a name="troubleshooting"></a>Résolution des problèmes

Le tableau suivant décrit les erreurs qui peuvent s’afficher pour des stratégies et propose des solutions.

|Erreur|Description|Solution|
|----|----|----|
| **La stratégie <*nom*> a été automatiquement désactivée à cause d’une erreur de configuration**|Si vous obtenez cette erreur dans Microsoft Cloud App Security, cela signifie que vous devez corriger la configuration de la stratégie indiquée. Quand vous créez une stratégie Microsoft Cloud App Security, vous utilisez souvent d’autres objets créés dans Cloud App Security ou dans le Centre de sécurité et de conformité, comme des balises IP ou des types sensibles personnalisés. Si la balise IP ou le type sensible personnalisé que vous avez utilisé dans la stratégie est supprimé, la stratégie est automatiquement désactivée et vous recevez cette erreur. Ce message peut également indiquer une erreur de configuration plus générale comme un filtre trop complexe. |Pour restaurer la stratégie, modifiez-la et résolvez chaque erreur de configuration indiquée. Cette erreur signifie généralement que vous devez supprimer tous les objets supprimés dans les filtres de stratégie et enregistrer la stratégie.|

## <a name="next-steps"></a>Étapes suivantes

[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[Les clients Premier peuvent également choisir Cloud App Security directement dans le portail Premier.](https://premier.microsoft.com/)

