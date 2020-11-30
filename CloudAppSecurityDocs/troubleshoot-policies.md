---
title: Résolution des problèmes des stratégies Cloud App Security
description: Cet article décrit la procédure de résolution des problèmes liés à la création de stratégies dans Cloud App Security.
ms.date: 12/10/2018
ms.topic: conceptual
ms.openlocfilehash: 80d7501dcc97c3697f0d4a98286ba72637cd051d
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96315971"
---
# <a name="troubleshooting-microsoft-cloud-app-security-policies"></a>Résolution des problèmes des stratégies Microsoft Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Cet article décrit la procédure de résolution des problèmes liés à la création de stratégies dans Cloud App Security.

## <a name="troubleshooting"></a>Dépannage

Le tableau suivant décrit les erreurs qui peuvent s’afficher pour des stratégies et propose des solutions.

|Error|Description|Résolution|
|----|----|----|
| **La stratégie <*nom*> a été automatiquement désactivée à cause d’une erreur de configuration**|Si vous obtenez cette erreur dans Microsoft Cloud App Security, cela signifie que vous devez corriger la configuration de la stratégie indiquée. Quand vous créez une stratégie Microsoft Cloud App Security, vous utilisez souvent d’autres objets créés dans Cloud App Security ou dans le Centre de sécurité et de conformité, comme des balises IP ou des types sensibles personnalisés. Si la balise IP ou le type sensible personnalisé que vous avez utilisé dans la stratégie est supprimé, la stratégie est automatiquement désactivée et vous recevez cette erreur. Ce message peut également indiquer une erreur de configuration plus générale comme un filtre trop complexe. |Pour restaurer la stratégie, modifiez-la et résolvez chaque erreur de configuration indiquée. Cette erreur signifie généralement que vous devez supprimer tous les objets supprimés dans les filtres de stratégie et enregistrer la stratégie.|

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
