---
title: Enrichir les données Cloud App Security Discovery avec des noms d’utilisateur Azure AD | Microsoft Docs
description: Cet article fournit des informations sur la façon d’enrichir les données Cloud App Security Discovery avec des noms d’utilisateur Azure AD.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 45295c2c-3e4d-4482-bf95-2e47072f9236
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 7778f1a2798975f5e292a4f013d07d2665f05536
ms.sourcegitcommit: 45311f2cafef79483e40d971a4c61c7673834d96
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2018
---
*S’applique à : Microsoft Cloud App Security*


# <a name="cloud-discovery-enrichment"></a>Enrichissement de Cloud Discovery

Les données Cloud Discovery peuvent maintenant être enrichies avec des données de nom d’utilisateur Azure Active Directory. Quand vous activez cette fonctionnalité, le nom d’utilisateur reçu dans les journaux de trafic de découverte est mis en correspondance et remplacé par le nom d’utilisateur Azure AD, ce qui active les fonctionnalités suivantes :
-   Vous pouvez examiner l’utilisation de l’informatique fantôme par l’utilisateur Azure Active Directory.
-   Vous pouvez mettre en corrélation l’utilisation de l’application cloud découverte avec les activités collectées par l’API.
-   Vous pouvez ensuite créer des journaux personnalisés basés sur des groupes d’utilisateurs Azure AD. Par exemple, un rapport d’informatique fantôme pour un service marketing spécifique.


## <a name="prerequisites"></a>Conditions préalables :
- La source de données doit fournir les informations de nom d’utilisateur
- Le connecteur d’applications Office 365 doit être connecté

## <a name="enabling-user-data-enrichment"></a>Activation de l’enrichissement des données utilisateur 
    
1. Sous l’icône Paramètres, sélectionnez **Paramètres Cloud Discovery**.
     
2. Sous l’onglet **Enrichissement d’utilisateur**, pour permettre à Cloud App Security d’utiliser les données Azure Active Directory pour enrichir les noms d’utilisateur par défaut, sélectionnez **Enrichir les identificateurs des utilisateurs découverts avec les noms d’utilisateur Azure Active Directory**.

3. Cliquez sur **Enregistrer**.
 
![Enrichir Cloud App Security Discovery avec des noms d’utilisateur Azure AD](./media/discovery-enrichment.png)
  

  
      
## <a name="see-also"></a>Voir aussi  
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
    
      
  