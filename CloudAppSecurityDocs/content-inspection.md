---
title: Comment Cloud App Security réalise l’inspection du contenu
description: Cet article décrit le processus suivi par Cloud App Security lors de l’exécution de l’inspection du contenu DLP sur les données de votre cloud.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 1/6/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: c67a387f-8c88-4018-9e80-0fb1455cf768
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: b0fcd13550d62d5ff96462b7d3f9f4a7437c1a44
ms.sourcegitcommit: 9f0c562322394a3dfac7f1d84286e673276a28b1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65568055"
---
# <a name="content-inspection"></a>Inspection du contenu

*S’applique à : Microsoft Cloud App Security*


Une fois que l’inspection du contenu est activée, vous pouvez choisir d’utiliser des expressions prédéfinies ou de rechercher d’autres expressions personnalisées.  

Vous pouvez spécifier une expression régulière pour exclure un fichier des résultats. Cette option s’avère très utile si vous avez un standard interne de mots clés de classification à exclure de la stratégie.  
   
Vous pouvez décider de définir le nombre minimal de violations de contenu à atteindre avant que le fichier ne soit considéré comme une violation. Par exemple, vous pouvez choisir 10 si vous souhaitez être alerté pour les fichiers comportant au moins 10 numéros de carte de crédit détectés dans leur contenu.  

Quand du contenu correspond à l’expression sélectionnée, le texte de la violation est remplacé par des caractères « X ». Par défaut, les violations sont masquées. Seul leur contexte, 100 caractères avant et après la violation, est affiché. Les chiffres dans le contexte de l’expression sont remplacés par des caractères « # » et ne sont jamais stockés dans Cloud App Security. Vous pouvez sélectionner l’option **Montrer les quatre derniers caractères d’une violation** pour annuler le masquage des quatre derniers caractères de la violation elle-même. Il est nécessaire de définir les types de données que l’expression régulière recherche : contenu, métadonnées et/ou nom de fichier. Par défaut, elle recherche le contenu et les métadonnées. 


## <a name="content-inspection-for-protected-files"></a>Inspection du contenu pour les fichiers protégés

Cloud App Security permet aux administrateurs d’accorder l’autorisation à Cloud App Security de déchiffrer les fichiers chiffrés et d’analyser leur contenu à la recherche de violations.

Afin d’octroyer les autorisations nécessaires à Cloud App Security :

1.  Accédez à **Paramètres**, puis **Azure Information Protection**.
2.  Activez **Inspecter les fichiers protégés**.
3. Suivez les instructions pour accorder les autorisations requises dans Azure Active Directory.
4. Vous pouvez configurer les paramètres pour chaque stratégie de fichier afin de déterminer quelles stratégies analyseront les fichiers protégés.



## <a name="next-steps"></a>Étapes suivantes
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)  
  
