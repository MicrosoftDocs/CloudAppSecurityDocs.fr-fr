---
title: Connecter Salesforce | Documentation Microsoft
description: "Cette rubrique fournit des informations sur la connexion de Salesforce à Cloud App Security à l’aide du connecteur API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/26/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 776d7589-acdb-4cb6-99a0-3be2f7b6aab2
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 129181e4768f068a0e30f6ef3a2d3f7fc6d47024
ms.openlocfilehash: 0932c6bc696e7b050eae543fbea7d847dfa42b4b


---


# <a name="connect-salesforce-to-microsoft-cloud-app-security"></a>Connecter Salesforce à Microsoft Cloud App Security
Cette section fournit des instructions pour connecter Cloud App Security à votre compte Salesforce existant à l’aide de l’API du connecteur d’applications.  
  
## <a name="how-to-connect-salesforce-to-cloud-app-security"></a>Comment connecter Salesforce à Cloud App Security  
  
1.  Nous vous recommandons d’avoir un compte d’administrateur de service dédié pour Cloud App Security.  
  
2.  Vérifiez que l’API REST est activée dans Salesforce.  
  
     Votre compte Salesforce doit correspondre à l’une des éditions suivantes prenant en charge l’API REST :  
  
     **Performance**, **Enterprise**, **Unlimited** ou **Developer**.  
  
     L’édition **Professional** n’a pas l’API REST par défaut, mais elle peut être ajoutée sur demande.  
  
     Vérifiez que l’API REST est disponible et activée dans votre édition, comme suit :  
  
    -   Connectez-vous à votre compte Salesforce et accédez à la page **Setup** (Configuration).  
  
    -   Sous **Manage Users** (Gérer les utilisateurs), accédez à la page **Profiles** (Profils).  
  
         ![salesforce, gérer les profils des utilisateurs](./media/salesforce-manageusers-profiles.png "salesforce, gérer les profils des utilisateurs")  
  
    -   Choisissez le profil que vous utilisez pour déployer Cloud App Security, puis cliquez sur **Modifier**. Il s’agit du profil à utiliser pour le compte de service Cloud App Security pour configurer le connecteur d’applications.  
  
         ![salesforce, modifier le profil](./media/salesforce-edit-profile.png "salesforce, modifier le profil")  
  
    -   Vérifiez que la case **API Enabled** (API activée) est cochée. Si ce n’est pas le cas, vous devez peut-être contacter Salesforce pour l’ajouter à votre compte.  
  
         ![salesforce, api activée](./media/salesforce-api-enabled.png "salesforce, api activée")  
  
3.  Si **Salesforce CRM Content** (Contenu CRM Salesforce) est activé pour votre organisation, vérifiez que le compte administratif actuel est également activé.  
  
    1.  Accédez à votre page de configuration de Salesforce.  
  
         ![salesforce, configuration](./media/salesforce-setup.png "salesforce, configuration")  
  
    2.  Dans le menu latéral, sélectionnez **Manage Users** (Gérer les utilisateurs), puis cliquez sur **Utilisateurs**.  
  
         ![menu salesforce, utilisateurs](./media/salesforce-menu-users.png "menu salesforce, utilisateurs")  
  
    3.  Sélectionnez l’utilisateur administratif actuel pour votre utilisateur Cloud App Security dédié.  
  
    4.  Vérifiez que la case **Salesforce CRM Content User** (Utilisateur de contenu CRM Salesforce) est cochée.  
  
         Si ce n’est pas le cas, cliquez sur **Edit** (Modifier), puis cochez la case.  
  
         ![salesforce, utilisateur de contenu crm](./media/salesforce-crm-content-user.png "salesforce, utilisateur de contenu crm")  
  
    5.  Cliquez sur **Save**.  
  
4.  Dans la console Cloud App Security, cliquez sur **Examiner**, puis sur **Applications connectées**.  
  
5.  Dans la page **Connecteurs d’application**, cliquez sur le bouton plus (+), puis sur **Salesforce**.  
  
     ![connecter salesforce](./media/connect-salesforce.png "connecter salesforce")  
  
6.  Dans la page des paramètres Salesforce, sous l’onglet API, cliquez sur **suivez ce lien**, en fonction de l’instance que vous souhaitez installer.  
  
7.  Cette opération ouvre la page de connexion de Salesforce. Entrez vos informations d’identification pour autoriser Cloud App Security à accéder à l’application Salesforce de votre équipe.  
  
     ![salesforce, connexion](./media/salesforce-logon.png "salesforce, connexion")  
  
8.  Salesforce vous demande si vous voulez autoriser Cloud App Security à accéder au journal d’informations et d’activité de votre équipe, et à effectuer toute activité en tant que membre de l’équipe. Pour continuer, cliquez sur **Autoriser**.  
  
9. À ce stade, vous recevez une notification de réussite ou d’échec concernant le déploiement. Cloud App Security est désormais autorisé dans Salesforce.com.  
  
10. De retour dans la console Cloud App Security, vous devez recevoir un message indiquant que Salesforce a été correctement connecté.  
  
11. Vérifiez la connexion en cliquant sur **Test API** (Tester l’API).  
  
     Le test peut prendre quelques minutes. Une fois que vous avez reçu une notification de réussite, cliquez sur **Terminé**.  
  
  
Après avoir connecté Salesforce, vous recevrez les événements comme suit : déclencheurs à partir du moment de connexion, événements de connexion et piste d’audit d’installation des 60 jours précédant la connexion, surveillance des événements remontant à 30 jours ou 1 jour, en fonction de votre licence de surveillance des événements Salesforce.
  
## <a name="see-also"></a>Voir aussi  
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Dec16_HO2-->


