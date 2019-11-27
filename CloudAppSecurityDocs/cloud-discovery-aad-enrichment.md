---
title: Enrichir les données Cloud App Security Discovery avec des noms d’utilisateur Azure AD
description: Cet article fournit des informations sur la façon d’enrichir les données Cloud App Security Discovery avec des noms d’utilisateur Azure AD.
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
ms.assetid: 45295c2c-3e4d-4482-bf95-2e47072f9236
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: a49b5a068ae8a2292d4e98314676d8c5389b5520
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74461247"
---
# <a name="cloud-discovery-enrichment"></a>Enrichissement de Cloud Discovery

*S’applique à : Microsoft Cloud App Security*

Les données Cloud Discovery peuvent maintenant être enrichies avec des données de nom d’utilisateur Azure Active Directory. Quand vous activez cette fonctionnalité, le nom d’utilisateur reçu dans les journaux de trafic de découverte est mis en correspondance et remplacé par le nom d’utilisateur Azure AD. Avez l’enrichissement de Cloud Discovery, vous disposez des fonctionnalités suivantes :
- Vous pouvez examiner l’utilisation de l’informatique fantôme par l’utilisateur Azure Active Directory.
- Vous pouvez mettre en corrélation l’utilisation de l’application cloud découverte avec les activités collectées par l’API.
- Vous pouvez ensuite créer des journaux personnalisés basés sur des groupes d’utilisateurs Azure AD. Par exemple, un rapport d’informatique fantôme pour un service marketing spécifique.


## <a name="prerequisites"></a>Conditions préalables :
- La source de données doit fournir les informations de nom d’utilisateur
- Le connecteur d’applications Office 365 doit être connecté

## <a name="enabling-user-data-enrichment"></a>Activation de l’enrichissement des données utilisateur 
    
1. Sous l’icône Paramètres, sélectionnez **Paramètres Cloud Discovery**.
     
2. Sous l’onglet **Enrichissement de l’utilisateur**, sélectionnez **Enrichir les identificateurs d’utilisateurs découverts avec les noms d’utilisateurs Azure Active Directory**. Cette option permet à Cloud App Security d’utiliser les données Azure Active Directory pour enrichir les noms d’utilisateur par défaut.

3. Cliquez sur **Enregistrer**.
 
![Enrichir Cloud App Security Discovery avec des noms d’utilisateur Azure AD](./media/discovery-enrichment.png)
  

  
      
## <a name="next-steps"></a>Étapes suivantes
  
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   

[!INCLUDE [Open support ticket](includes/support.md)]  
    
      
  
