---
title: Résolution des problèmes d’intégration de SIEM – Cloud App Security | Microsoft Docs
description: Cet article liste les problèmes qui peuvent se produire lors de la connexion de votre SIEM à Cloud App Security et propose des solutions pour chacun d’eux.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 08/30/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: de64d9ca-eaed-4243-bcf7-adca5aff18c8
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: a5ab44813959db6ad7b1f437ba88b47223ce5e41
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74459959"
---
# <a name="troubleshooting-the-siem-agent"></a>Résolution des problèmes de l’agent SIEM

*S’applique à : Microsoft Cloud App Security*

Cet article liste les problèmes qui peuvent se produire lors de la connexion de votre SIEM à Cloud App Security et propose des solutions possibles.

## <a name="recover-missing-activity-events-in-mcas-siem-agent"></a>Recover missing activity events in MCAS SIEM Agent 

If you received a system alert regarding an issue with activity delivery through the SIEM agent, follow the steps below to recover the activity events in the timeframe of the issue. These steps will guide you through setting up a new Recovery SIEM agent that will run in parallel and resend the activity events to your SIEM.

>[!NOTE]
>The recovery process will resend all activity events in the timeframe described in the system alert. If your SIEM already contains activity events from this timeframe, you will experience duplicated events after this recovery. 

### <a name="step-1--configure-a-new-siem-agent-in-parallel-to-your-existing-agent"></a>Step 1 – Configure a new SIEM Agent in parallel to your existing agent 
1. In the Cloud App Security portal, go to Security Extensions page.  
2. In the SIEM Agents tab, click on [add a new SIEM agent](siem.md), and use the wizard to configure the connection details to your SIEM. 

    >[!NOTE]
    >This agent should run in parallel to the existing one, so network configuration might not be identical. 

1. In the wizard, configure the Data Types to include **only Activities** and apply the same activity filter that was used in your original SIEM agent (if it exists). 
2. Turn on **Recovery mode** by checking the Recovery mode checkbox. This action will automatically configure the SIEM Agent to send only the missing activities due to the issue and stop sending activities once all activities are fully recovered.
3. Enregistrez les paramètres.
4. Run the new agent using the generated token.


### <a name="step-2--validate-the-successful-data-delivery-to-your-siem"></a>Step 2 – Validate the successful data delivery to your SIEM 
1. Connect to your SIEM and validate that new data is received from the new SIEM Agent that you configured. 
2. The agent will only send activities from the timeframe of the issue, which you were alerted on. 

### <a name="step-3--remove-the-recovery-siem-agent"></a>Step 3 – Remove the Recovery SIEM agent 
1. The recovery SIEM agent will automatically stop sending data and be disabled once it reaches the end date.
2. Validate in your SIEM that no new data is sent by the recovery SIEM agent. 
3. Stop the execution of the agent on your machine. 
4. In the portal, go to SIEM Agent page, and remove the Recovery SIEM Agent. 
5. Make sure your original SIEM Agent is still running properly. 

## <a name="general-troubleshooting"></a>General troubleshooting

Vérifiez que l’agent SIEM n’affiche pas l’état **Erreur de connexion** ou **Déconnecté** dans le portail Microsoft Cloud App Security et qu’il ne fait pas l’objet de notifications. Si la connexion est interrompue pendant plus de deux heures, l’état affiché est le suivant : **Erreur de connexion**. Si la connexion est interrompue depuis plus de 12 heures, l’état passe à **Déconnecté**.

Si vous voyez une des erreurs suivantes dans l’invite de commandes lors de l’exécution de l’agent, procédez comme suit pour corriger le problème :

|Erreur|Description|Solution|
|----|----|----|
|Erreur générale pendant l’amorçage|Erreur inattendue pendant le démarrage de l’agent.|Contactez le support technique.|
|Trop d’erreurs critiques|Trop d’erreurs critiques se sont produites lors de la connexion de la console. Arrêt.|Contactez le support technique.|
|Jeton non valide|Le jeton fourni n’est pas valide.|Vérifiez que vous avez copié le jeton approprié. Vous pouvez utiliser le processus ci-dessus pour régénérer le jeton.|
|Erreur de proxy non valide|L’adresse de proxy fournie n’est pas valide.|Vérifiez que vous avez entré le proxy et le port appropriés.|


Après avoir créé l’agent, consultez la page de l’agent SIEM dans le portail Cloud App Security. Si vous voyez l’une des **Notifications de l’agent** suivantes, procédez comme suit pour corriger le problème :

|Erreur|Description|Solution|
|----|----|----|
|**Erreur interne**|Quelque chose d’inconnu s’est produit avec votre agent SIEM.|Contactez le support technique.|
|**Erreur d’envoi du serveur de données**|Vous pouvez recevoir cette erreur si vous travaillez avec un serveur Syslog sur TCP. L’agent SIEM ne peut pas se connecter à votre serveur Syslog.  Si vous recevez cette erreur, l’agent cesse d’extraire de nouvelles activités tant qu’elle n’est pas résolue. Veillez à suivre les étapes de correction jusqu’à ce que l’erreur n’apparaisse plus.|1. Make sure you properly defined your Syslog server: In the Cloud App Security UI, edit your SIEM agent as described above. Vérifiez que vous avez écrit correctement le nom du serveur et défini le port approprié. </br>2. Check connectivity to your Syslog server: Make sure your firewall isn't blocking communication.| 
|**Erreur de connexion du serveur de données**| Vous pouvez recevoir cette erreur si vous travaillez avec un serveur Syslog sur TCP. L’agent SIEM ne peut pas se connecter à votre serveur Syslog.  Si vous recevez cette erreur, l’agent cesse d’extraire de nouvelles activités tant qu’elle n’est pas résolue. Veillez à suivre les étapes de correction jusqu’à ce que l’erreur n’apparaisse plus.|1. Make sure you properly defined your Syslog server: In the Cloud App Security UI, edit your SIEM agent as described above. Vérifiez que vous avez écrit correctement le nom du serveur et défini le port approprié. </br>2. Check connectivity to your Syslog server: Make sure your firewall isn't blocking communication.|
|**Erreur de l’agent SIEM**|L’agent SIEM est déconnecté depuis plus de X heures|Vérifiez que vous n’avez pas modifié la configuration de l’agent SIEM dans le portail Cloud App Security. Sinon, cette erreur peut signaler un problème de connectivité entre Cloud App Security et l’ordinateur sur lequel vous exécutez l’agent SIEM.|
|**Erreur de notification de l’agent SIEM**|Des erreurs de transfert de notification de l’agent SIEM ont été reçues d’un agent SIEM.|Cette erreur indique que vous avez reçu des erreurs concernant la connexion entre l’agent SIEM et votre serveur SIEM. Vérifiez qu’aucun pare-feu ne bloque votre serveur SIEM ou l’ordinateur sur lequel vous exécutez l’agent SIEM. Vérifiez aussi que l’adresse IP du serveur SIEM n’a pas changé.|


## <a name="next-steps"></a>Étapes suivantes
  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   

[!INCLUDE [Open support ticket](includes/support.md)]  
  
