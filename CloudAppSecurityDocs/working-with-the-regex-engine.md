---
title: Utiliser le moteur RegEx dans Cloud App Security pour les stratégies d’inspection du contenu
description: Cet article fournit des instructions d’utilisation du moteur RegEx pour la correspondance au modèle dans les stratégies Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 12/14/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: dc8b87e5-e6c1-4a65-ab8c-067fb527fce4
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 07085a2c2e8a27e6e6ad35d9e088a95f8d543522
ms.sourcegitcommit: 8ef0438fa35916c48625ff750cb85e9628d202f2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56281115"
---
# <a name="working-with-the-regex-engine"></a>En utilisant l’inspection du contenu

*S’applique à : Microsoft Cloud App Security*
 
Cet article fournit des instructions d’utilisation du moteur RegEx pour la correspondance au modèle dans les stratégies Cloud App Security.

## <a name="regular-expressions-in-cloud-app-security"></a>Expressions régulières dans Cloud App Security

Les stratégies d’inspection du contenu de Microsoft Cloud App Security utilisent RegEx pour la correspondance au modèle. L’inspection du contenu peut être appliquée dans le cadre des stratégies de fichier.

### <a name="testing-regular-expressions"></a>Test des expressions régulières

Pour tester des expressions régulières, vous pouvez utiliser les sites web suivants :  
  
- [https://regexpal.com/](https://regexpal.com/) - Veillez à sélectionner **Casse non prise en compte**.  
  
- [https://regex101.com/](https://regex101.com/) - Fournit une analyse détaillée de RegEx.  

### <a name="limitations-of-regular-expressions-in-cloud-app-security"></a>Limitations des expressions régulières dans Cloud App Security

Les limitations suivantes sont imposées sur les expressions régulières personnalisées :  
  
- Le non-respect de la casse est toujours appliqué à la recherche  

- Quantificateurs autorisés : {n,m} où n, m < 10  
  
- Tous les groupes doivent être sans capture, par exemple : (?:xxx)  
  
     Au lieu de (groupe), utilisez (?:groupe)  
  
- Quantificateurs non autorisés : *, +, {n,}  
  
     Au lieu de *, utilisez {0,9}  
  
     Au lieu de +, utilisez {1,9}  
  
- Références arrière non autorisées : \\<nombre\> ou \k\<nom>  
  
### <a name="example-expressions"></a>Exemples d’expressions  

Le tableau suivant vous présente des exemples d’expressions et si elles correspondraient ou non.

|                                                               |                                                               |                                    |
|---------------------------------------------------------------|---------------------------------------------------------------|------------------------------------|
|              <strong>Expression régulière</strong>              |                     <strong>Données</strong>                     |      <strong>Correspondances</strong>      |
|            Colou?r (?:black&#124;blue&#124;white)             |   Noir<br /><br /> Blanc<br /><br /> Rouge   | Oui<br /><br /> Oui<br /><br /> Non |
|           [a-z0-9]{1,9}@[a-z0-9]{1,9}\\.[a-z]{2,3}            | Some1@abc.com<br /><br /> user@host.org<br /><br /> @bad.com  | Oui<br /><br /> Oui<br /><br /> Non |
| 20\d{2}-(?:0[1-9]&#124;1[0-2])-(?:[0-2][0-9]&#124;30&#124;31) |   2015-12-31<br /><br /> 2015-01-09<br /><br /> 1999-12-31    | Oui<br /><br /> Oui<br /><br /> Non |
|                       d.n't\s{0,10}c.r.                       | Don’t     care<br /><br /> D!n'tcor0<br /><br /> Doesn’t care | Oui<br /><br /> Oui<br /><br /> Non |

## <a name="check-out-this-video"></a>Regardez cette vidéo !

[Utilisation du moteur RegEx](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security-Working-with-the-Regex-Engine)

## <a name="next-steps"></a>Étapes suivantes

[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)  
  
