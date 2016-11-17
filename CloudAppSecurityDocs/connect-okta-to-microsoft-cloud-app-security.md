---
title: "Connecter Okta à Microsoft Cloud App Security | Documentation Microsoft"
description: "Cette rubrique fournit des informations sur la connexion de votre application Okta à Cloud App Security à l’aide du connecteur API."
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
ms.openlocfilehash: c11e133f78c3973006c3e70dd1ccd719f7b639aa


---

# <a name="connect-okta-to-microsoft-cloud-app-security"></a>Connecter Okta à Microsoft Cloud App Security
Cette section fournit des instructions pour connecter Cloud App Security à votre compte Okta existant à l’aide des API du connecteur.  
  
## <a name="how-to-connect-okta-to-cloud-app-security"></a>Comment connecter Okta à Cloud App Security  
  
1.  Nous vous recommandons de créer un compte de service d’administration dans Okta pour Cloud App Security.  
  
     Veillez à utiliser un compte disposant des autorisations de super administrateur.  
  
     Assurez-vous que votre compte Okta est vérifié.  
  
2.  Dans la console Okta, cliquez sur **Admin**.  
  
    -   Cliquez sur **Security** (Sécurité), puis sur **API**.  
  
         ![okta, api](./media/okta-api.png "okta api")  
  
    -   Cliquez sur **Create Token** (Créer un jeton).  
  
         ![okta, créer un jeton](./media/okta-createtoken.jpg "okta createtoken")  
  
    -   Dans la fenêtre contextuelle **Create Token** (Créer un jeton), nommez votre jeton Cloud App Security et cliquez sur **Create Token** (Créer un jeton).  
  
         ![okta, fenêtre contextuelle de jeton](./media/okta-token-popup.png "okta token popup")  
  
    -   Dans la fenêtre contextuelle **Token created successfully** (Jeton créé avec succès), copiez le contenu de **Token value** (Valeur du jeton).  
  
         ![okta, valeur du jeton](./media/okta-token-value.png "okta token value")  
  
3.  Dans la console Cloud App Security, cliquez sur **Examiner**, puis sur **Applications approuvées**.  
  
4.  Dans la ligne Okta, cliquez sur **Connect** (Connecter) dans la colonne **App Connector status** (État du connecteur d’applications), ou cliquez sur le bouton **Connect an app** (Connecter une application), puis sur **Okta**.  
  
     ![connecter okta](./media/connect-okta.png "connect okta")  
  
5.  Dans la page de l’API, dans le champ **Domain** (Domaine), entrez votre domaine Okta et collez votre jeton dans le champ **Token** (Jeton).  
  
6.  Cliquez sur **Connect** (Connecter) pour créer le jeton pour Okta dans Cloud App Security.  
  
7.  Vérifiez la connexion en cliquant sur **Test API** (Tester l’API).  
  
     Le test peut prendre quelques minutes. Une fois averti que la connexion a réussi, cliquez sur **Fermer**.  
  
Après avoir connecté Okta, vous recevrez les événements des 60 jours précédant la connexion.
  
## <a name="see-also"></a>Voir aussi  
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO5-->


