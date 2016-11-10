---
title: "Connecter ServiceNow à Microsoft Cloud App Security | Documentation Microsoft"
description: "Cette rubrique fournit des informations sur la connexion de votre application ServiceNow à Cloud App Security à l’aide du connecteur API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: c626d94d-2ffd-4daf-8fa4-4b6d308cf012
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: 30ddba23a0c481cb434e9239950cce90c52efc4f


---

# <a name="connect-servicenow-to-microsoft-cloud-app-security"></a>Connecter ServiceNow à Microsoft Cloud App Security
Cette section fournit des instructions pour connecter Cloud App Security à votre compte ServiceNow existant à l’aide de l’API du connecteur d’applications.  
  
## <a name="how-to-connect-servicenow-to-cloud-app-security"></a>La connexion de ServiceNow à Cloud App Security  
  
> [!NOTE]  
>  Cloud App Security prend en charge les versions ServiceNow d’Eureka et de Fiji. Pour connecter ServiceNow à Cloud App Security, vous devez avoir des autorisations de niveau administrateur et vérifier que l’instance ServiceNow prend en charge l’accès à l’API.  
  
1.  Connectez-vous avec un compte d’administrateur à votre compte ServiceNow.  
  
2.  Créez un compte de service pour Cloud App Security et attachez le rôle d’administrateur au compte nouvellement créé.  
  
3.  Vérifiez que le plug-in API REST est activé.  
  
     ![servicenow, compte](./media/servicenow-account.png "servicenow account")  
  
4.  Dans le portail Cloud App Security, cliquez sur **Examiner**, puis sur **Applications approuvées**.  
  
5.  Dans la ligne ServiceNow, cliquez sur **Connecter** dans la colonne **État du connecteur d’applications** ou cliquez sur le bouton **Connecter une application**, puis sur **ServiceNow**.  
  
     ![connecter servicenow](./media/connect-servicenow.png "connect servicenow")  
  
6.  Dans la page Paramètres ServiceNow, sous l’onglet API, ajoutez votre nom d’utilisateur, mot de passe et URL d’instance ServiceNow dans les zones appropriées.  
  
7.  Cliquez sur **Connexion**.  
  
     ![servicenow, mettre à jour le mot de passe](./media/servicenow-update-password.png "servicenow update password")  
  
8.  Vérifiez la connexion en cliquant sur **Test API** (Tester l’API).  
  
     Le test peut prendre quelques minutes. Une fois averti que la connexion a réussi, cliquez sur **Fermer**.  
  
Après avoir connecté ServiceNow, vous recevrez les événements des 60 jours précédant la connexion.
  
## <a name="see-also"></a>Voir aussi  
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO4-->


