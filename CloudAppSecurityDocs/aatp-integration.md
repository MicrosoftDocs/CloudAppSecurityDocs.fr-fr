---
title: Intégrer la Protection contre les menaces avancées Azure avec Cloud App Security
description: Cet article fournit des informations sur la façon de tirer parti des insights d’Azure-Protection avancée contre les menaces dans Cloud App Security pour la détection de risque hybride.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 6/17/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 63e82b47-bb08-4614-af55-f85d04edfc5a
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 1f920a6cb1ddcc00930527b9ba22264d4b4637a6
ms.sourcegitcommit: 62778bfbc010b95cdef4c8aed23b0f195f382242
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67171485"
---
# <a name="azure-advanced-threat-protection-integration"></a>Intégration d’Azure-Protection avancée contre les menaces

*S’applique à : Microsoft Cloud App Security*

Microsoft Cloud App Security s’intègre à Azure Advanced Threat Protection (ATP Azure) pour fournir l’analytique comportementale de l’entité d’utilisateur (UEBA) dans un environnement hybride - application cloud et locales. Pour plus d’informations sur l’apprentissage automatique et analytique comportementale fournies par Azure ATP, consultez [What ' s Azure ATP ?](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp).

En intégrant Azure ATP, votre portail Cloud App Security fournissent des alertes et des informations à partir de :
- Microsoft Cloud App Security, qui identifie les attaques au sein d'une session cloud, couvrant non seulement les produits Microsoft mais aussi les applications tierces
- Azure Advanced Threat Protection, qui utilise l’apprentissage automatique et analytique comportementale pour identifier les attaques de votre réseau local
- Azure Active Directory Identity Protection, qui détecte et prévient de manière proactive les risques pouvant affecter les identités dans le cloud au niveau des utilisateurs et des connexions


## <a name="prerequisites"></a>Prérequis

Pour procéder à un examen complet d’un utilisateur dans un environnement hybride, les éléments suivants sont nécessaires :

- Licence valide pour Microsoft Cloud App Security
- Licence valide pour Azure ATP connectée à votre instance Active Directory

>[!NOTE]
>Si vous n’avez pas d'abonnement à Azure ATP, vous pourrez toujours utiliser le portail Cloud App Security pour examiner les utilisateurs, mais vous ne recevrez pas d’informations de votre environnement local.


## <a name="enable-azure-advanced-threat-protection"></a>Activer la Protection contre les menaces avancées Azure

Il vous suffit pour intégrer Azure-Protection avancée contre les menaces avec Cloud App Security est cliquez sur une seule case à cocher. En activant l’intégration, vous autorisez le Cloud App Security accéder et analyser les activités suspectes locales vues par Azure ATP, les extraire dans le Cloud App Security et vous fournissez une image complète de votre environnement hybride et toutes les activités à risque effectuée par vos utilisateurs.

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
  
