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

## <a name="recover-missing-activity-events-in-mcas-siem-agent"></a>Récupérer les événements d’activité manquants dans MCAS SIEM agent 

Si vous avez reçu une alerte système concernant un problème de remise d’activité par le biais de l’agent SIEM, suivez les étapes ci-dessous pour récupérer les événements d’activité dans le laps de temps du problème. Ces étapes vous guident dans la configuration d’un nouvel agent SIEM de récupération qui s’exécute en parallèle et renvoient les événements d’activité à votre serveur SIEM.

>[!NOTE]
>Le processus de récupération renverra tous les événements d’activité dans le laps de temps décrit dans l’alerte système. Si votre SIEM contient déjà des événements d’activité à partir de ce laps de temps, vous rencontrerez des événements en double après cette récupération. 

### <a name="step-1--configure-a-new-siem-agent-in-parallel-to-your-existing-agent"></a>Étape 1 : configurer un nouvel agent SIEM en parallèle à votre agent existant 
1. Dans le portail Cloud App Security, accédez à la page extensions de sécurité.  
2. Dans l’onglet agents SIEM, cliquez sur [Ajouter un nouvel agent Siem](siem.md)et utilisez l’Assistant pour configurer les détails de connexion à votre serveur Siem. 

    >[!NOTE]
    >Cet agent doit s’exécuter en parallèle avec le nom existant. la configuration du réseau peut donc ne pas être identique. 

1. Dans l’Assistant, configurez les types de données pour inclure **uniquement les activités** et appliquez le même filtre d’activité que celui utilisé dans votre agent Siem d’origine (s’il existe). 
2. Activez le **mode de récupération** en activant la case à cocher mode de récupération. Cette action configure automatiquement l’agent SIEM pour envoyer uniquement les activités manquantes en raison du problème et arrêter l’envoi d’activités une fois que toutes les activités ont été entièrement récupérées.
3. Enregistrez les paramètres.
4. Exécutez le nouvel agent à l’aide du jeton généré.


### <a name="step-2--validate-the-successful-data-delivery-to-your-siem"></a>Étape 2 : valider la réussite de la remise des données à votre serveur SIEM 
1. Connectez-vous à votre serveur SIEM et vérifiez que de nouvelles données sont reçues du nouvel agent SIEM que vous avez configuré. 
2. L’agent enverra uniquement des activités à partir de la période du problème sur lequel vous avez été alerté. 

### <a name="step-3--remove-the-recovery-siem-agent"></a>Étape 3 : supprimer l’agent SIEM de récupération 
1. L’agent SIEM de récupération arrête automatiquement l’envoi des données et est désactivé une fois qu’il a atteint la date de fin.
2. Vérifiez dans votre SIEM qu’aucune nouvelle donnée n’est envoyée par l’agent SIEM de récupération. 
3. Arrêtez l’exécution de l’agent sur votre ordinateur. 
4. Dans le portail, accédez à la page de l’agent SIEM, puis supprimez l’agent SIEM de récupération. 
5. Vérifiez que votre agent SIEM d’origine est toujours en cours d’exécution correctement. 

## <a name="general-troubleshooting"></a>Résolution des problèmes généraux

Vérifiez que l’agent SIEM n’affiche pas l’état **Erreur de connexion** ou **Déconnecté** dans le portail Microsoft Cloud App Security et qu’il ne fait pas l’objet de notifications. Si la connexion est interrompue pendant plus de deux heures, l’état affiché est le suivant : **Erreur de connexion**. Si la connexion est interrompue depuis plus de 12 heures, l’état passe à **Déconnecté**.

Si vous voyez une des erreurs suivantes dans l’invite de commandes lors de l’exécution de l’agent, procédez comme suit pour corriger le problème :

|Error|Description|Résolution :|
|----|----|----|
|Erreur générale pendant l’amorçage|Erreur inattendue pendant le démarrage de l’agent.|Contactez le support technique.|
|Trop d’erreurs critiques|Trop d’erreurs critiques se sont produites lors de la connexion de la console. Arrêt.|Contactez le support technique.|
|Jeton non valide|Le jeton fourni n’est pas valide.|Vérifiez que vous avez copié le jeton approprié. Vous pouvez utiliser le processus ci-dessus pour régénérer le jeton.|
|Erreur de proxy non valide|L’adresse de proxy fournie n’est pas valide.|Vérifiez que vous avez entré le proxy et le port appropriés.|


Après avoir créé l’agent, consultez la page de l’agent SIEM dans le portail Cloud App Security. Si vous voyez l’une des **Notifications de l’agent** suivantes, procédez comme suit pour corriger le problème :

|Error|Description|Résolution :|
|----|----|----|
|**Erreur interne**|Quelque chose d’inconnu s’est produit avec votre agent SIEM.|Contactez le support technique.|
|**Erreur d’envoi du serveur de données**|Vous pouvez recevoir cette erreur si vous travaillez avec un serveur Syslog sur TCP. L’agent SIEM ne peut pas se connecter à votre serveur Syslog.  Si vous recevez cette erreur, l’agent cesse d’extraire de nouvelles activités tant qu’elle n’est pas résolue. Veillez à suivre les étapes de correction jusqu’à ce que l’erreur n’apparaisse plus.|1. Assurez-vous que vous avez correctement défini votre serveur Syslog : dans l’interface utilisateur Cloud App Security, modifiez votre agent SIEM comme décrit ci-dessus. Vérifiez que vous avez écrit correctement le nom du serveur et défini le port approprié. </br>2. Vérifiez la connectivité à votre serveur Syslog : Assurez-vous que votre pare-feu ne bloque pas les communications.| 
|**Erreur de connexion du serveur de données**| Vous pouvez recevoir cette erreur si vous travaillez avec un serveur Syslog sur TCP. L’agent SIEM ne peut pas se connecter à votre serveur Syslog.  Si vous recevez cette erreur, l’agent cesse d’extraire de nouvelles activités tant qu’elle n’est pas résolue. Veillez à suivre les étapes de correction jusqu’à ce que l’erreur n’apparaisse plus.|1. Assurez-vous que vous avez correctement défini votre serveur Syslog : dans l’interface utilisateur Cloud App Security, modifiez votre agent SIEM comme décrit ci-dessus. Vérifiez que vous avez écrit correctement le nom du serveur et défini le port approprié. </br>2. Vérifiez la connectivité à votre serveur Syslog : Assurez-vous que votre pare-feu ne bloque pas les communications.|
|**Erreur de l’agent SIEM**|L’agent SIEM est déconnecté depuis plus de X heures|Vérifiez que vous n’avez pas modifié la configuration de l’agent SIEM dans le portail Cloud App Security. Sinon, cette erreur peut signaler un problème de connectivité entre Cloud App Security et l’ordinateur sur lequel vous exécutez l’agent SIEM.|
|**Erreur de notification de l’agent SIEM**|Des erreurs de transfert de notification de l’agent SIEM ont été reçues d’un agent SIEM.|Cette erreur indique que vous avez reçu des erreurs concernant la connexion entre l’agent SIEM et votre serveur SIEM. Vérifiez qu’aucun pare-feu ne bloque votre serveur SIEM ou l’ordinateur sur lequel vous exécutez l’agent SIEM. Vérifiez aussi que l’adresse IP du serveur SIEM n’a pas changé.|


## <a name="next-steps"></a>Étapes suivantes
  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   

[!INCLUDE [Open support ticket](includes/support.md)]  
  
