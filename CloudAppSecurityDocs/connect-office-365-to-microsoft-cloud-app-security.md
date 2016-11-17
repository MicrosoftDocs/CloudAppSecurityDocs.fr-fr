---
title: "Connecter Office 365 à Microsoft Cloud App Security | Documentation Microsoft"
description: "Cette rubrique fournit des informations sur la connexion d’Office 365 à Cloud App Security à l’aide du connecteur API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/26/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: b938e1e0-356d-4cc6-ba4a-862c0c59d709
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a413236b04726dddc69068e39967f6ad17218719
ms.openlocfilehash: 2f07956782fb266eaa2eab1b0b0459c2d57f69fc


---

# <a name="connect-office-365-to-microsoft-cloud-app-security"></a>Connecter Office 365 à Microsoft Cloud App Security
Cette section fournit des instructions pour connecter Cloud App Security à votre compte Microsoft Office 365 existant à l’aide de l’API du connecteur d’applications.  
  
  

## <a name="how-to-connect-office-365-to-cloud-app-security"></a>Comment connecter Office 365 à Cloud App Security  
  
> [!NOTE]
>- Vous devez disposer d’au moins une licence Office 365 pour connecter Office 365 à Cloud App Security.
>-  La journalisation d’audit de l’administrateur Exchange, qui est activée par défaut dans Office 365, consigne un événement dans le journal d’audit Office 365 quand un administrateur (ou un utilisateur qui a reçu des privilèges d’administrateur) apporte une modification dans votre organisation Exchange Online. Les modifications apportées en utilisant le Centre d’administration Exchange ou en exécutant une applet de commande dans Windows PowerShell sont enregistrées dans le journal d’audit d’administrateur Exchange. Pour plus d’informations sur la journalisation d’audit de l’administrateur dans Exchange, voir [Gestion de la journalisation d’audit de l’administrateur](http://go.microsoft.com/fwlink/p/?LinkID=619225).
>- L’enregistrement d’audit pour les boîtes aux lettres Exchange doit être activé pour chaque boîte aux lettres utilisateur avant de consigner toute activité de l’utilisateur dans Exchange Online ; voir [Activités de la boîte aux lettres Exchange](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c).
>- Si des applications Office sont activées, des groupes qui font partie d’Office 365 sont également créés dans les applications Office spécifiques : par exemple, si SharePoint est activé, des groupes Office 365 seront créés dans SharePoint.
 
1.  Dans la ligne Office 365, cliquez sur **Connect** (Connect) dans la colonne **App Connector status** (État du connecteur d’applications), ou cliquez sur le bouton **Connect an App** (Connecter une application), puis sélectionnez **Office 365**.  

2.  Dans la fenêtre contextuelle Office 365, cliquez sur Connecter Office 365.

      ![connecter 0365](./media/connect-0365.png) 
 
3.  Cliquez sur Tester maintenant pour tester la connexion à Office 365. Le test peut prendre quelques minutes.
  
    ![O365, tester la connexion](./media/o365-test-connection.png) 
 
4.   Une fois Office 365 affiché comme correctement connecté, cliquez sur **Fermer**.
  
     ![O365 connecté](./media/o365-connected.png) 

> [!NOTE] 
> Après la connexion d’Office 365, des données qui remontent à une semaine s’affichent, dont les applications tierces connectées à Office 365 qui extraient des API. Pour les applications tierces qui n’extrayaient pas d’API avant la connexion, vous verrez les événements à partir du moment où vous avez connecté Office 365, car Cloud App Security active toutes les API désactivées par défaut.

## <a name="see-also"></a>Voir aussi  
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO5-->


