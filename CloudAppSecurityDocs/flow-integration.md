---
title: Intégrer Flow à Cloud App Security pour bénéficier de l’automatisation avec des alertes personnalisées
description: Cet article explique comment bénéficier de l’automatisation avec des alertes personnalisées en intégrant Flow à Cloud App Security.
keywords: ''
author: ShlomoSagir-MS
ms.author: ShlomoSagir-MS
manager: ShlomoSagir-MS
ms.date: 6/18/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 344f92e2-6b3b-46db-bfd0-3b1016e0bc34
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: a9bdc83e18f82f60719e4080aacecdf4eea0580e
ms.sourcegitcommit: 62778bfbc010b95cdef4c8aed23b0f195f382242
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67171537"
---
# <a name="integrate-with-flow-for-custom-alert-automation"></a>Intégrer avec Flow automatisation d’alerte personnalisée

*S’applique à : Microsoft Cloud App Security*

Vous pouvez intégrer Cloud App Security à [Microsoft Flow](https://docs.microsoft.com/flow/getting-started) pour assurer l’automatisation et fournir des playbooks d’orchestration à la suite d’alertes personnalisées. Grâce à l’[écosystème de connecteurs](https://docs.microsoft.com/connectors/) disponible dans Microsoft Flow, vous pouvez automatiser le déclenchement de playbooks quand Cloud App Security génère des alertes. Vous pouvez par exemple créer automatiquement un problème dans un système de gestion de tickets à l’aide du [connecteur ServiceNow](https://docs.microsoft.com/connectors/service-now/) ou envoyer un e-mail d’approbation pour exécuter une action de gouvernance personnalisée quand une alerte est déclenchée dans Cloud App Security.  

## <a name="prerequisites"></a>Prérequis 

 - Vous devez avoir un [plan Microsoft Flow](https://flow.microsoft.com/en-us/pricing) valide.

## <a name="how-it-works"></a>Fonctionnement

Seul, Cloud App Security fournit des options de gouvernance prédéfinies. Il permet notamment de suspendre un utilisateur ou de rendre un fichier privé lors de la définition de stratégies. En créant un playbook dans Microsoft Flow à l’aide du connecteur Cloud App Security, vous pouvez créer des workflows pour activer des options de gouvernance personnalisées pour vos stratégies. Une fois le playbook créé dans Flow, il vous suffit de l’associer à une stratégie dans Cloud App Security pour envoyer des alertes à Flow. Microsoft Flow propose plusieurs connecteurs et conditions pour créer un workflow personnalisé pour votre organisation. 

Le [connecteur de Cloud App Security](https://docs.microsoft.com/connectors/cloudappsecurity/) dans le flux prend en charge automatisée des déclencheurs et les actions. Flow est déclenché automatiquement quand Cloud App Security génère une alerte. Les actions incluent le changement de l’état de l’alerte dans Cloud App Security. 

## <a name="how-to-create-playbooks-with-microsoft-flow"></a>Comment créer des playbooks avec Microsoft Flow

1. [Créez un jeton d’API](api-tokens.md) dans Cloud App Security. 

2. Accédez au [portail Microsoft Flow](https://flow.microsoft.com) et choisissez [**Créer un flux à partir de zéro**](https://docs.microsoft.com/flow/get-started-logic-flow). 

3. Dans Rechercher parmi les connecteurs et les déclencheurs, tapez **Cloud App Security** et sélectionnez **Quand une alerte est générée**.

   ![Quand une alerte est générée (Flow)](./media/flow-when-alert.png)

4. Sous **Paramètres d’authentification**, collez le jeton d’API créé à l’étape 1. 

5. Définissez le workflow à déclencher quand une stratégie dans Cloud App Security génère une alerte. Ajoutez une action, une condition logique, des boucles ou des conditions switch case, puis enregistrez le playbook. 

   ![Workflow (Flow)](./media/flow-workflow.png)

6. Dans le portail Cloud App Security, accédez à **Stratégies**. Dans la ligne de la stratégie dont vous souhaitez transférer les alertes à Flow, cliquez sur les points de suspension et sélectionnez **Paramètres**. 
7. Sous **Alertes**, sélectionnez **Envoyer des alertes à Flow**, choisissez le nom du playbook dans le menu déroulant.  

   ![Activer Flow dans le portail Cloud App Security](./media/flow-mcas-config.png)

8. Les playbooks Cloud App Security que vous avez créés ou auxquels vous avez accès sont visibles dans l’écran **Extensions de sécurité**. 

  
   ![afficher des playbooks dans Cloud App Security](./media/flow-extensions.png)
 
 

## <a name="next-steps"></a>Étapes suivantes 
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)  
