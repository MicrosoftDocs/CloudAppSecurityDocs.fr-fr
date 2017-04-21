---
title: "Connecter ServiceNow à Cloud App Security pour la visibilité et le contrôle d’utilisation | Microsoft Docs"
description: "Cette rubrique fournit des informations sur la connexion de votre application ServiceNow à Cloud App Security à l’aide du connecteur API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: c626d94d-2ffd-4daf-8fa4-4b6d308cf012
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 1f4fd428f762bcbe1fb2a26bf44268cf985fbd4f
ms.sourcegitcommit: c79c405a1277c5fcebbc245fa12ff8feb53248d5
translationtype: HT
---
# <a name="connect-servicenow-to-microsoft-cloud-app-security"></a>Connecter ServiceNow à Microsoft Cloud App Security
Cette section fournit des instructions pour connecter Cloud App Security à votre compte ServiceNow existant à l’aide de l’API du connecteur d’applications.  
  
## <a name="how-to-connect-servicenow-to-cloud-app-security"></a>La connexion de ServiceNow à Cloud App Security  
  
> [!NOTE]  
>  Cloud App Security prend en charge les versions Eureka, Fiji, Geneva, Helsinki et Istanbul de ServiceNow. Pour connecter ServiceNow à Cloud App Security, vous devez avoir le rôle **Administrateur** et vérifier que l’instance ServiceNow prend en charge l’accès à l’API.  Pour plus d’informations, reportez-vous à la [documentation du produit ServiceNow](http://wiki.servicenow.com/index.php?title=Base_System_Roles#gsc.tab=0).
  
1.  Connectez-vous avec un compte d’administrateur à votre compte ServiceNow.  
  
2.  Dans le volet de recherche **Filter navigator** (Navigateur de filtres), tapez **OAuth** et sélectionnez **Application Registry** (Registre d’application).

3. Dans la barre de menus **Application Registries** (Registres d’applications), cliquez sur **Nouveau** pour créer un profil OAuth.

   ![Nouveau profil OAuth ServiceNow](./media/servicenow-app-registry.png)

4. Sous **What kind of OAuth application?** (Quel type d’application OAuth ?), cliquez sur **Create an OAuth API endpoint for external clients** (Créer un point de terminaison d’API OAuth pour les clients externes).

   ![Type OAuth ServiceNow](./media/servicenow-oauth-app-type.png)

5. Sous **Application Registries New record** (Nouvel enregistrement des registres d’applications), renseignez les champs suivants :
    
    - Dans le champ **Nom**, nommez le nouveau profil OAuth, par exemple CloudAppSecurity. 
    
    - L’**ID de client** va être généré automatiquement. Copiez cet ID, vous devrez le coller dans Cloud App Security pour établir la connexion.
    
    - Dans le champ **Secret client**, entrez une chaîne. Si ce champ reste vide, un secret aléatoire est généré automatiquement. Copiez la clé et enregistrez-la pour l’utiliser ultérieurement. 
    
    - Augmentez la valeur du champ **Access Token Lifespan** (Durée de vie du jeton d’accès) jusqu’à au moins 3 600.
    
    - Cliquez sur **Envoyer**.

   ![ID des profils ServiceNow](./media/servicenow-profile-ids.png)

6.  Dans le portail Cloud App Security, cliquez sur **Examiner**, puis sur **Applications connectées**.  
  
7.  Dans la page **Connecteurs d’application**, cliquez sur le bouton plus (+), puis sur **ServiceNow**.  
  
     ![connecter servicenow](./media/connect-servicenow.png "connecter servicenow")  
  
8.  Dans la fenêtre contextuelle, ajoutez vos nom d’utilisateur, mot de passe, URL d’instance, ID de client et secret client ServiceNow dans les zones appropriées.  
  
9.  Cliquez sur **Connexion**.  
  
     ![servicenow, connexion à CAS](./media/servicenow-portal-connect.png "servicenow, connexion dans le portail")  
  
10.  Vérifiez la connexion en cliquant sur **Tester maintenant**.  
  
     Le test peut prendre quelques minutes. Une fois averti que la connexion a réussi, cliquez sur **Fermer**.  
  
Après avoir connecté ServiceNow, vous recevrez les événements des 60 jours précédant la connexion.
  
## <a name="see-also"></a>Voir aussi  
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
