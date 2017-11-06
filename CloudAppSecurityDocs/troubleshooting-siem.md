---
title: "Résolution des problèmes d’intégration de SIEM à Cloud App Security | Microsoft Docs"
description: "Cette rubrique répertorie les problèmes qui peuvent se produire lors de la connexion de votre SIEM à Cloud App Security et propose des solutions pour chacun d’eux."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/6/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: de64d9ca-eaed-4243-bcf7-adca5aff18c8
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 386f9d87ea477b75af03bc03d44f2a36657e2b6d
ms.sourcegitcommit: b729e881851cdd8dc3f105ddbf6b4b907b8588dd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2017
---
# <a name="troubleshooting-the-siem-agent"></a>Résolution des problèmes de l’agent SIEM

Vérifiez que l’agent SIEM n’affiche pas l’état **Erreur de connexion** ou **Déconnecté** dans le portail Cloud App Security et qu’il ne fait pas l’objet de notifications. L’agent affiche l’état **Erreur de connexion** si la connexion est interrompue depuis plus de deux heures, et l’état **Déconnecté** si la connexion est interrompue depuis plus de 12 heures.

Si vous voyez une des erreurs suivantes dans l’invite de commandes lors de l’exécution de l’agent, procédez comme suit pour corriger le problème :

|Erreur|Description|Solution|
|----|----|----|
|Erreur générale pendant l’amorçage|Erreur inattendue pendant le démarrage de l’agent.|Contactez le support technique.|
|Trop d’erreurs critiques|Trop d’erreurs critiques se sont produites lors de la connexion de la console. Arrêt.|Contactez le support technique.|
|Jeton non valide|Le jeton fourni n’est pas valide.|Vérifiez que vous avez copié le jeton approprié. Vous pouvez utiliser le processus ci-dessus pour régénérer le jeton.|
|Erreur de proxy non valide|L’adresse de proxy fournie n’est pas valide.|Vérifiez que vous avez entré le proxy et le port appropriés.|


Après avoir créé l’agent, si vous voyez une des **notifications d’agent** suivantes dans le portail Cloud App Security sur la page de l’agent SIEM, procédez comme suit pour corriger le problème :

|Erreur|Description|Solution|
|----|----|----|
|**Erreur interne**|Quelque chose d’inconnu s’est produit avec votre agent SIEM.|Contactez le support technique.|
|**Erreur d’envoi du serveur de données**|Vous pouvez recevoir cette erreur si vous travaillez avec un serveur Syslog sur TCP. L’agent SIEM ne peut pas se connecter à votre serveur Syslog.  Si vous recevez cette erreur, l’agent cesse d’extraire de nouvelles activités tant qu’elle n’est pas résolue : veillez donc à suivre les étapes de correction jusqu’à ce que l’erreur n’apparaisse plus.|1. Vérifiez que vous avez défini correctement votre serveur Syslog : dans l’interface utilisateur de Cloud App Security, modifiez votre agent SIEM comme décrit ci-dessus, puis vérifiez que vous avez écrit correctement le nom du serveur et défini le port approprié. </br>2. Vérifiez la connectivité à votre serveur Syslog : vérifiez que votre pare-feu ne bloque la communication.| 
|**Erreur de connexion du serveur de données**| Vous pouvez recevoir cette erreur si vous travaillez avec un serveur Syslog sur TCP. L’agent SIEM ne peut pas se connecter à votre serveur Syslog.  Si vous recevez cette erreur, l’agent cesse d’extraire de nouvelles activités tant qu’elle n’est pas résolue : veillez donc à suivre les étapes de correction jusqu’à ce que l’erreur n’apparaisse plus.|1. Vérifiez que vous avez défini correctement votre serveur Syslog : dans l’interface utilisateur de Cloud App Security, modifiez votre agent SIEM comme décrit ci-dessus, puis vérifiez que vous avez écrit correctement le nom du serveur et défini le port approprié. </br>2. Vérifiez la connectivité à votre serveur Syslog : vérifiez que votre pare-feu ne bloque la communication.|
|**Erreur de l’agent SIEM**|L’agent SIEM est déconnecté depuis plus de X heures|Vérifiez que vous n’avez pas modifié la configuration de l’agent SIEM dans le portail Cloud App Security. Sinon, cette erreur peut signaler un problème de connectivité entre Cloud App Security et l’ordinateur sur lequel vous exécutez l’agent SIEM.|
|**Erreur de notification de l’agent SIEM**|Des erreurs de transfert de notification de l’agent SIEM ont été reçues d’un agent SIEM.|Cela indique que vous avez reçu des erreurs de connexion entre l’agent SIEM et votre serveur SIEM. Assurez-vous qu’aucun pare-feu ne bloque votre serveur SIEM ou l’ordinateur sur lequel vous exécutez l’agent SIEM. Vérifiez aussi que l’adresse IP du serveur SIEM n’a pas été modifiée.|



## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  