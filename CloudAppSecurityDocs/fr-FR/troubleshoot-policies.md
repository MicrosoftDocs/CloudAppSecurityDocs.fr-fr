---
title: Résolution des problèmes des stratégies Cloud App Security | Microsoft Docs
description: Cette rubrique décrit la procédure de dépannage de la création de stratégies dans Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 828cc94a-248b-44f6-a1ba-c28c0a135f8c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 9bfc880cdaa0bf87abfd2b3b34cdf647a4aa1aaf
ms.sourcegitcommit: 45311f2cafef79483e40d971a4c61c7673834d96
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2018
---
*S’applique à : Microsoft Cloud App Security*


# <a name="troubleshooting-microsoft-cloud-app-security-policies"></a>Résolution des problèmes des stratégies Microsoft Cloud App Security

|Erreur|Description|Solution|
|----|----|----|
| **La stratégie <policy name> a été automatiquement désactivée à cause d’une erreur de configuration.**|Si vous obtenez cette erreur dans Microsoft Cloud App Security, cela signifie que vous devez corriger la configuration de la stratégie nommée. Quand vous créez une stratégie Microsoft Cloud App Security, vous utilisez souvent d’autres objets que vous avez créés dans Cloud App Security, comme des balises IP ou des filtres de plage d’adresses IP. Si la plage ou la balise IP que vous avez utilisée dans la stratégie est supprimée, la stratégie est automatiquement désactivée et vous recevez cette erreur. |Pour restaurer la stratégie, modifiez-la et effacez tous les objets supprimés de ses filtres, puis enregistrez-la.|



## <a name="see-also"></a>Voir aussi
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[Les clients Premier peuvent également choisir Cloud App Security directement dans le portail Premier.](https://premier.microsoft.com/)

