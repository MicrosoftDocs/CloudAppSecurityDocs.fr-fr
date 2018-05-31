---
title: Résolution des problèmes des stratégies Cloud App Security | Microsoft Docs
description: Cette rubrique décrit la procédure de dépannage de la création de stratégies dans Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/22/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 828cc94a-248b-44f6-a1ba-c28c0a135f8c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: cfc1d9442c50153ce06a358ccdd88b4ab316a88d
ms.sourcegitcommit: 592478b77531328e23bedd6e8964c07321e6b1a9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2018
ms.locfileid: "34445333"
---
*S’applique à : Microsoft Cloud App Security*


# <a name="troubleshooting-microsoft-cloud-app-security-policies"></a>Résolution des problèmes des stratégies Microsoft Cloud App Security

|Erreur|Description|Solution|
|----|----|----|
| **La stratégie <policy name> a été automatiquement désactivée à cause d’une erreur de configuration**|Si vous obtenez cette erreur dans Microsoft Cloud App Security, cela signifie que vous devez corriger la configuration de la stratégie indiquée. Quand vous créez une stratégie Microsoft Cloud App Security, vous utilisez souvent d’autres objets que vous avez créés dans Cloud App Security ou dans le Centre de sécurité et de conformité, comme des balises IP ou des types sensibles personnalisés. Si la balise IP ou le type sensible personnalisé que vous avez utilisé dans la stratégie est supprimé, la stratégie est automatiquement désactivée et vous recevez cette erreur. Cela peut également indiquer une erreur de configuration plus générale comme un filtre trop complexe. |Pour restaurer la stratégie, modifiez-la et résolvez chaque erreur de configuration indiquée. Cela signifie généralement que vous devez supprimer tous les objets supprimés dans les filtres de stratégie et enregistrer la stratégie.|



## <a name="see-also"></a>Voir aussi
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[Les clients Premier peuvent également choisir Cloud App Security directement dans le portail Premier.](https://premier.microsoft.com/)

