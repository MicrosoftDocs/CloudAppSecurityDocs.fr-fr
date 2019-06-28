---
title: Intégrer la Protection contre les menaces avancées Azure avec Cloud App Security
description: Cet article fournit des informations sur la façon de tirer parti des insights d’Azure-Protection avancée contre les menaces dans Cloud App Security pour la détection de risque hybride.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
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
ms.openlocfilehash: 99c866a8b2571c9572e042572d0f5160d0ae56e5
ms.sourcegitcommit: 3938edadc5f89f87cdeba607476cf3983b2413e8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67411923"
---
# <a name="azure-advanced-threat-protection-integration"></a>Intégration d’Azure-Protection avancée contre les menaces

*S’applique à : Microsoft Cloud App Security*

Microsoft Cloud App Security s’intègre à Azure Advanced Threat Protection (ATP Azure) pour fournir l’analytique comportementale de l’entité d’utilisateur (UEBA) dans un environnement hybride - application cloud et localement, pour plus d’informations, consultez [didacticiel : Enquêter sur les utilisateurs à risque]() pour plus d’informations sur l’apprentissage automatique et analytique comportementale fournies par Azure ATP, consultez [What ' s Azure ATP ?](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp).

## <a name="prerequisites"></a>Prérequis

Pour procéder à un examen complet d’un utilisateur dans un environnement hybride, les éléments suivants sont nécessaires :

- Licence valide pour Azure ATP connectée à votre instance Active Directory
- Vous devez être administrateur général pour permettre une intégration entre Azure ATP et Microsoft Cloud App Security 
- Si ne pas avoir d’Azure ATP, essayez dès maintenant


>[!NOTE]
>Si vous n’avez pas un abonnement pour Microsoft Cloud App Security, vous serez toujours en mesure d’utiliser le portail Cloud App Security pour obtenir des informations d’Azure ATP.


## <a name="enable-azure-advanced-threat-protection"></a>Activer la Protection contre les menaces avancées Azure

Pour permettre à Cloud App Security à intégrer à Azure ATP :

1. Dans Cloud App Security, sous la roue dentée des paramètres, sélectionnez **paramètres**.
    
   ![Menu Paramètres](./media/azip-system-settings.png)

1. Sous **Protection contre les menaces**, sélectionnez **Azure ATP**.
   
    ![Activer la protection contre les menaces avancées azure](./media/aatp-integration.png)

3. Cochez la case pour **données connecter Azure ATP, y compris des alertes et des activités avec Cloud App Security**.


> [!NOTE]
> Il peut prendre jusqu'à 12 heures jusqu'à ce que l’intégration entre en vigueur.
 
Après avoir activé l’intégration Azure-Protection avancée contre les menaces, vous serez en mesure de voir les activités en local pour tous les utilisateurs de votre organisation. Vous serez également obtenir des avancées insights sur vos utilisateurs qui combinent des alertes et les activités suspectes dans vos environnements cloud et locales.



## <a name="next-steps"></a>Étapes suivantes 
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)  
  
