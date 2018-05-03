---
title: Utilisation du moteur RegEx pour les stratégies d’inspection du contenu | Microsoft Docs
description: Cette rubrique fournit des instructions d’utilisation du moteur RegEx pour la correspondance au modèle dans les stratégies Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: dc8b87e5-e6c1-4a65-ab8c-067fb527fce4
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 2e7c8f640a054ba8e5bc2ad999bd73a6604eb4d0
ms.sourcegitcommit: 45311f2cafef79483e40d971a4c61c7673834d96
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2018
---
*S’applique à : Microsoft Cloud App Security*


# <a name="working-with-the-regex-engine"></a>En utilisant l’inspection du contenu
 
Les stratégies d’inspection du contenu de Microsoft Cloud App Security tirent parti de RegEx pour la correspondance au modèle. L’inspection du contenu peut être appliquée dans le cadre des stratégies de fichier. Pour tester des expressions régulières, vous pouvez utiliser les sites web suivants :  
  
-   [http://regexpal.com/](http://regexpal.com/)  
  
     Veillez à sélectionner **Casse non prise en compte**.  
  
-   [https://regex101.com/](https://regex101.com/)  
  
     Fournit une analyse détaillée de RegEx.  
  
Les limitations suivantes sont imposées sur les expressions régulières personnalisées :  
  
-   Le non-respect de la casse est toujours appliqué à la recherche  
   
-   Quantificateurs autorisés : {n,m} où n, m < 10  
  
-   Tous les groupes doivent être sans capture, par exemple : (?:xxx)  
  
     Au lieu de (groupe), utilisez (?:groupe)  
  
-   Quantificateurs non autorisés : *, +, {n,}  
  
     Au lieu de *, utilisez {0,9}  
  
     Au lieu de +, utilisez {1,9}  
  
-   Références arrière non autorisées : \\<nombre\> ou \k\<nom>  
  
Exemples d’expressions  
  

|                                                               |                                                               |                                    |
|---------------------------------------------------------------|---------------------------------------------------------------|------------------------------------|
|              <strong>Expression régulière</strong>              |                     <strong>Données</strong>                     |      <strong>Correspondances</strong>      |
|            Colou?r (?:black&#124;blue&#124;white)             |   Noir<br /><br /> Blanc<br /><br /> Rouge   | Oui<br /><br /> Oui<br /><br /> Non |
|           [a-z0-9]{1,9}@[a-z0-9]{1,9}\\.[a-z]{2,3}            | Some1@abc.com<br /><br /> user@host.org<br /><br /> @bad.com  | Oui<br /><br /> Oui<br /><br /> Non |
| 20\d{2}-(?:0[1-9]&#124;1[0-2])-(?:[0-2][0-9]&#124;30&#124;31) |   2015-12-31<br /><br /> 2015-01-09<br /><br /> 1999-12-31    | Oui<br /><br /> Oui<br /><br /> Non |
|                       d.n't\s{0,10}c.r.                       | Don’t     care<br /><br /> D!n'tcor0<br /><br /> Doesn’t care | Oui<br /><br /> Oui<br /><br /> Non |

## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  

## <a name="check-out-this-video"></a>Regardez cette vidéo !
[Utilisation du moteur RegEx](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security-Working-with-the-Regex-Engine)    