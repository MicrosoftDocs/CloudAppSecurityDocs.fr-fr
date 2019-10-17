---
title: Intégrer Azure-protection avancée contre les menaces avec Cloud App Security
description: Cet article fournit des informations sur la façon d’exploiter Azure Advanced Threat Protection Insights dans Cloud App Security pour la détection hybride des risques.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 6/27/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 63e82b47-bb08-4614-af55-f85d04edfc5a
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: cd52e120f20e6b8ebaeacdd5a30a7c98d883fec9
ms.sourcegitcommit: c342abeec95359ddabdabcc3a081a0f91d52407c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72334880"
---
# <a name="azure-advanced-threat-protection-integration"></a>Intégration d’Azure-protection avancée contre les menaces

*S’applique à : Microsoft Cloud App Security*

Microsoft Cloud App Security s’intègre à Azure-protection avancée contre les menaces (Azure ATP) pour fournir une analyse comportementale des entités utilisateur (UEBA) dans un environnement hybride (à la fois une application Cloud et une application en local). pour plus d’informations, consultez [Didacticiel : examiner les risques Pour plus](tutorial-ueba.md) d’informations sur les machine learning et l’analyse comportementale fournis par Azure ATP, consultez [qu’est-ce que Azure ATP ?](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp).

## <a name="prerequisites"></a>Conditions préalables

Pour procéder à un examen complet d’un utilisateur dans un environnement hybride, les éléments suivants sont nécessaires :

- Licence valide pour Azure ATP connectée à votre instance Active Directory
- Vous devez être administrateur général pour activer l’intégration entre Azure ATP et Microsoft Cloud App Security 
- Si vous n’avez pas Azure ATP, essayez-le maintenant


>[!NOTE]
>Si vous n’avez pas d’abonnement pour Microsoft Cloud App Security, vous pouvez toujours utiliser le portail Cloud App Security pour obtenir Azure ATP Insights.


## <a name="enable-azure-advanced-threat-protection"></a>Activer Azure-protection avancée contre les menaces

Pour permettre l’intégration de Cloud App Security avec Azure ATP :

1. Dans Cloud App Security, sous l’roue dentée paramètres, sélectionnez **paramètres**.
    
   ![Menu paramètres](./media/azip-system-settings.png)

1. Sous **protection contre les menaces**, sélectionnez **Azure ATP**.
   
    ![activer Azure-protection avancée contre les menaces](./media/aatp-integration.png)

3. Cochez la case pour **vous connecter Azure ATP données, notamment les alertes et les activités avec Cloud App Security**.


> [!NOTE]
> Cela peut prendre jusqu’à 12 heures jusqu’à ce que l’intégration prenne effet.
 
Après l’activation de l’intégration d’Azure-protection avancée contre les menaces, vous pouvez voir les activités locales pour tous les utilisateurs de votre organisation. Vous obtiendrez également des Insights avancés sur vos utilisateurs qui combinent des alertes et des activités suspectes dans vos environnements Cloud et local.



## <a name="next-steps"></a>Étapes suivantes 
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)  
  
