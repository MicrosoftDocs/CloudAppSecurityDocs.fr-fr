---
title: "Connecter Azure à Cloud App Security pour la visibilité et le contrôle d’utilisation | Microsoft Docs"
description: "Cette rubrique fournit des informations sur la connexion d’Azure à Cloud App Security à l’aide du connecteur API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/15/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 3a677bc7-c8b7-4c6a-aada-82c8b3778352
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: d2c5dff92c790a9ad27c872ebbd09769eef9898d
ms.sourcegitcommit: 27170447acfaeded585c264e425a46a485e7fb19
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2017
---
# <a name="connect-azure-to-microsoft-cloud-app-security"></a>Connecter Azure à Microsoft Cloud App Security

Cette section fournit des instructions pour connecter Cloud App Security à votre compte Azure existant à l’aide de l’API du connecteur d’applications.  
  
## <a name="setting-up-azure-for-connection-to-cloud-app-security"></a>Configuration d’Azure pour la connexion à Cloud App Security

Cloud App Security se connecte à Azure par le biais d’Event Hubs. Cette section fournit des instructions pour la diffusion de vos journaux d’activité sur un hub d’événements dans votre abonnement. 

### <a name="step-1-stream-your-azure-activity-logs-to-event-hubs"></a>Étape 1 : Diffuser vos journaux d’activité Azure dans Event Hubs

1.  Diffusez le journal d’activité Azure de votre abonnement Azure sur un hub d’événements. Suivez le guide officiel dans la documentation Azure : https://docs.microsoft.com/en-us/azure/monitoring-and-diagnostics/monitoring-stream-activity-logs-event-hubs

 > [!NOTE]
 > Si vous avez plusieurs abonnements Azure, répétez cette étape pour chaque abonnement, mais n’utilisez qu’un seul hub d’événements qui sera partagé entre vos abonnements.

 Une fois que vous avez suivi les instructions, un nouvel hub d’événements s’affiche dans l’espace de noms choisi.
 
 > [!NOTE]
 > Si vous obtenez une erreur après avoir essayé d’exporter les journaux d’activité, accédez au panneau **Fournisseurs de ressources** dans Azure et vérifiez que 'microsoft.insights' est inscrit.

### <a name="step-2-get-a-connection-string-to-your-event-hub"></a>Étape 2 : Obtenir une chaîne de connexion à votre hub d’événements

1.  Accédez au panneau **Event Hubs - Preview**.
  
   ![Panneau Event Hubs](media/azure-event-hubs.png "Event Hubs Azure")

2.  Sélectionnez votre espace de noms de hub d’événements.
  
    ![Espace de noms de hub d’événements](media/azure-namespace.png "Espace de noms Azure")

3.  Dans le menu, sous **Entités**, cliquez sur **Event Hubs**. 
  
    ![Entités de hub d’événements](media/azure-event-hubs-entities.png "Entités de hub d’événements Azure")

4.  Sélectionnez le nouvel hub d’événements créé par Azure Monitor. Il s’appelle **insights-operational-logs**.
  > [!NOTE]
  > La création du hub d’événements peut prendre quelques minutes.

   ![Journaux opérationnels Insights](media/azure-insight-operational-logs.png "Journaux opérationnels Insights Azure")
  
  
5. Créez une stratégie d’accès qui donne à Cloud App Security l’autorisation de lire à partir du hub d’événements, en cliquant sur **Stratégies d’accès partagé** et sur **Ajouter**.
  
    ![Stratégies d’accès partagé](media/azure-shared-access-policies.png "Stratégies d’accès partagé Azure")

6.  Entrez un nom pour la nouvelle stratégie et veillez à inclure au moins la **revendication Écouter**. Quand vous avez terminé, cliquez sur **Créer**.
  
    ![Nouvelle stratégie Azure](media/azure-new-policy.png "Créer une stratégie Azure")

7.  Sous **Paramètres**, puis **Stratégies d’accès partagé**, cliquez sur la stratégie d’accès que vous venez de créer.   
  
    ![Sélectionner une stratégie Azure](media/azure-select-policy.png "Sélectionner une stratégie Azure")

8. Dans la fenêtre Stratégie, copiez l’une des chaînes de connexion en cliquant sur le bouton suivant en regard de **Chaîne de connexion - Clé primaire** ou **Chaîne de connexion - Clé secondaire**.

### <a name="step-3-add-azure-to-cloud-app-security"></a>Étape 3 : Ajouter Azure à Cloud App Security
 
1.  Dans le portail Cloud App Security, cliquez sur **Examiner**, puis sur **Applications connectées**.  
  
3.  Dans la page **Connecteurs d’application**, cliquez sur le bouton plus (+), puis sélectionnez **Microsoft Azure**.  
  
     ![Connecter Azure à Cloud App Security](media/azure-connect-app.png "Connecter Azure")  
  
4.  Dans le champ **Chaîne de connexion**, collez la chaîne de connexion que vous avez copiée à l’étape précédente.  
  
5.  Dans le champ **Groupe de consommateurs**, tapez :   `$Default`
    
   >[!NOTE] 
   > Si vous avez créé un autre groupe de consommateurs à utiliser, utilisez ce nom de **Groupe de consommateurs**.
  
6.  Cliquez sur **Connexion**.
     La connexion sera testée et peut prendre quelques minutes. Une fois averti que la connexion a réussi, cliquez sur **Fermer**.  
  
## <a name="see-also"></a>Voir aussi  
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  