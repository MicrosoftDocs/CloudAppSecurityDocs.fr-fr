---
title: Comment Cloud App Security effectue l’inspection du contenu DLP
description: Cet article décrit le processus suivi par Cloud App Security lors de l’exécution de l’inspection du contenu DLP sur les données de votre cloud.
ms.date: 1/6/2019
ms.topic: how-to
ms.openlocfilehash: 6dedfb8ff66ef1e6012238aa0fc993a0c3ddbbe8
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96312350"
---
# <a name="content-inspection"></a>Inspection du contenu

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Une fois que l’inspection du contenu est activée, vous pouvez choisir d’utiliser des expressions prédéfinies ou de rechercher d’autres expressions personnalisées.

Vous pouvez spécifier une expression régulière pour exclure un fichier des résultats. Cette option s’avère très utile si vous avez un standard interne de mots clés de classification à exclure de la stratégie.

Vous pouvez décider de définir le nombre minimal de violations de contenu à atteindre avant que le fichier ne soit considéré comme une violation. Par exemple, vous pouvez choisir 10 si vous souhaitez être alerté pour les fichiers comportant au moins 10 numéros de carte de crédit détectés dans leur contenu.

Quand du contenu correspond à l’expression sélectionnée, le texte de la violation est remplacé par des caractères « X ». Par défaut, les violations sont masquées. Seul leur contexte, 100 caractères avant et après la violation, est affiché. Les nombres dans le contexte de l’expression sont remplacés par des caractères « # » et ne sont jamais stockés dans Cloud App Security. Vous pouvez sélectionner l’option **Montrer les quatre derniers caractères d’une violation** pour annuler le masquage des quatre derniers caractères de la violation elle-même. Il est nécessaire de définir les types de données que l’expression régulière recherche : contenu, métadonnées et/ou nom de fichier. Par défaut, elle recherche le contenu et les métadonnées.

## <a name="content-inspection-for-protected-files"></a>Inspection du contenu pour les fichiers protégés

Cloud App Security permet aux administrateurs d’accorder l’autorisation à Cloud App Security de déchiffrer les fichiers chiffrés et d’analyser leur contenu à la recherche de violations.

Afin de fournir Cloud App Security autorisations nécessaires :

1. Accédez à **Paramètres**, puis **Azure Information Protection**.
2. Activez **Inspecter les fichiers protégés**.
3. Suivez les instructions pour accorder les autorisations requises dans Azure Active Directory.
4. Vous pouvez configurer les paramètres pour chaque stratégie de fichier afin de déterminer quelles stratégies analyseront les fichiers protégés.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
