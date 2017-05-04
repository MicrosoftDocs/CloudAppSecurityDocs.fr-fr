---
title: "Vue d’ensemble du scénario de protection contre les menaces | Microsoft Docs"
description: "Cette rubrique décrit le scénario de protection de votre organisation contre les menaces présentes dans l’environnement cloud."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/30/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 0017be99-29c3-468e-a181-255e343ed4f5
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: fcc793f0fea71ef0666a7c99034185c5cd5fd894
ms.sourcegitcommit: 7e9ae94cb4f90fbccaa84f19bdebb4652a425e45
translationtype: HT
---
# <a name="controlling-and-protecting-your-files"></a>Contrôler et protéger vos fichiers  

Identifiez les problèmes liés à une utilisation à haut risque et à la sécurité dans le cloud, détectez tout comportement utilisateur anormal et protégez-vous des menaces dans vos applications cloud approuvées. Bénéficiez d’une visibilité sur les activités des administrateurs et des utilisateurs, et définissez des stratégies pour générer automatiquement une alerte en cas de comportement suspect ou quand des activités spécifiques que vous considérez comme risquées se déroulent dans vos environnements approuvés. Exploitez la quantité considérable de données Microsoft relatives à l’intelligence des menaces et à la recherche sur la sécurité. Les stratégies de détection des menaces vous permettent de vous assurer que vos applications approuvées bénéficient de tous les contrôles de sécurité nécessaires et de bien les maîtriser.
 
## <a name="massive-quantities-of-files-are-being-downloaded-insider-data-exfiltration"></a>Des quantités énormes de fichiers sont téléchargées (exfiltration de données en interne)

Ce cas de figure s’applique à Office 365, Google Apps, Box, Dropbox, Salesforce.

### <a name="the-threat"></a>LA MENACE
Un attaquant avec un compte compromis peut exfiltrer des données à partir d’Office 365 ou d’autres applications cloud en téléchargeant ou en consultant plusieurs fichiers.

### <a name="the-solution"></a>LA SOLUTION
Détectez quand un utilisateur télécharge ou consulte un grand nombre de fichiers en peu de temps.

#### <a name="prerequisites"></a>Prérequis

[Connectez](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) au moins une application cloud à Cloud App Security.

#### <a name="setting-up-monitoring"></a>Configurer la surveillance

1.    Par défaut, Cloud App Security analyse votre réseau pour établir une base de référence, où il découvre ce que font généralement les utilisateurs dans votre cloud et à quel moment. 

2. Il est également important de commencer à surveiller vos applications cloud en définissant une stratégie qui les examine à la recherche de téléchargements massifs et vous alerte si un événement inhabituel se produit :

    1. Dans la page **Stratégies**, cliquez sur [**Créer une stratégie d’activité**](user-activity-policies.md). 
    ![créer une stratégie d’activité](./media/create-activity-policy.png)

    2. Dans le champ [**Modèle de stratégie**](policy-template-reference.md), choisissez **Téléchargement massif par un même utilisateur**.
    
    3. Si vous le souhaitez, vous pouvez affiner le filtre d’activité répétée.
    
    4. Cliquez sur **Appliquer le modèle**. 
    ![modèle de stratégie d’activité](./media/activity-policy-template.png)
     
2. Étudier les correspondances
    
    1. Dans la page **Stratégies**, cliquez sur le nom de la stratégie pour atteindre le **Rapport de stratégie**, puis passez en revue les correspondances qui ont été déclenchées.

    2. Pour examiner une correspondance, cliquez sur celle-ci et ouvrez le tiroir d’activité. Dans le tiroir, vous pouvez voir les autres stratégies correspondant à cette activité. 
     


#### <a name="validating-your-policy"></a>Valider votre stratégie

1. Pour simuler une alerte, téléchargez plusieurs documents à partir de vos applications cloud connectées plusieurs fois sur une courte période comme défini dans la configuration de votre stratégie (par exemple, 10 fois en moins de 30 minutes).
3. Accédez au rapport de stratégie. Une correspondance de stratégie d’activité devrait apparaître sous peu. 
4. Vous pouvez cliquer sur la correspondance pour voir quels fichiers ont été téléchargés. La correspondance elle-même est masquée pour protéger les données sensibles. 

#### <a name="removing-the-risk"></a>Supprimer le risque

Après avoir validé et affiné la stratégie, supprimez les faux positifs possibles qui peuvent avoir correspondu à votre stratégie. Effectuez ensuite les opérations suivantes : 
  1. Vous pouvez engager immédiatement des [actions de gouvernance](governance-actions.md) en cliquant sur les trois points à la fin de la ligne et en sélectionnant l’action de gouvernance appropriée, par exemple, **Put user in quarantine (Placer l’utilisateur en quarantaine)**.

 ![gouvernance automatique externe](./media/auto-gov-external.png)

   2. Une fois la validation effectuée, vous pouvez définir des actions de gouvernance automatiques. Par exemple, dans SharePoint et OneDrive, vous pouvez **supprimer des utilisateurs externes** ou **placer l’utilisateur en quarantaine**, et dans G Suite et Box, vous pouvez **supprimer des utilisateurs externes** et **supprimer l’accès public**.

  ![appliquer des actions de gouvernance automatiques](./media/apply-automatic-gov-actions.png)



## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  