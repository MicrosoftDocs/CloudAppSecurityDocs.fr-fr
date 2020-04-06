---
title: Comment Cloud App Security effectue l’inspection du contenu
description: Cet article décrit le processus Cloud App Security suit lorsque vous effectuez l’inspection du contenu DLP sur les données de votre Cloud.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 1/6/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 82d157bbe887f70194cbb55708635759e48433b1
ms.sourcegitcommit: 288c279a0d2dd62a8ad8d7425c3e9e98857bf5f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2020
ms.locfileid: "80666441"
---
# <a name="content-inspection"></a>Inspection du contenu

*S’applique à : Microsoft Cloud App Security*

Si vous activez l’inspection du contenu, vous pouvez choisir d’utiliser des expressions prédéfinies ou de rechercher d’autres expressions personnalisées.

Vous pouvez spécifier une expression régulière pour exclure un fichier des résultats. Cette option est très utile si vous avez un mot clé de classification interne standard que vous souhaitez exclure de la stratégie.

Vous pouvez décider de définir le nombre minimal de violations de contenu que vous souhaitez faire correspondre avant que le fichier ne soit considéré comme une violation. Par exemple, vous pouvez choisir 10 si vous souhaitez être alerté sur des fichiers contenant au moins 10 numéros de carte de crédit trouvés dans son contenu.

Lorsque le contenu est mis en correspondance avec l’expression sélectionnée, le texte de la violation est remplacé par des caractères « X ». Par défaut, les violations sont masquées et affichées dans leur contexte affichant 100 caractères avant et après la violation. Les nombres dans le contexte de l’expression sont remplacés par des caractères « # » et ne sont jamais stockés dans Cloud App Security. Vous pouvez sélectionner l’option pour afficher les **quatre derniers caractères d’une violation** afin de démasquer les quatre derniers caractères de la violation elle-même. Il est nécessaire de définir les types de données que l’expression régulière recherche : contenu, métadonnées et/ou nom de fichier. Par défaut, elle recherche le contenu et les métadonnées.

## <a name="content-inspection-for-protected-files"></a>Inspection du contenu pour les fichiers protégés

Cloud App Security permet aux administrateurs d’accorder à Cloud App Security l’autorisation de déchiffrer des fichiers chiffrés et de rechercher les violations de leur contenu.

Pour accorder à Cloud App Security les autorisations nécessaires :

1. Accédez à **paramètres** , puis **Azure information protection**.
2. Activez **inspecter les fichiers protégés.**
3. Suivez l’invite pour autoriser les autorisations requises dans Azure Active Directory.
4. Vous pouvez configurer les paramètres par stratégie de fichier pour déterminer quelles stratégies vont analyser les fichiers protégés.

## <a name="next-steps"></a>Étapes suivantes :

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
