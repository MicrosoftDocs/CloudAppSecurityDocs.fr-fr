---
title: Connecter ServiceNow à Cloud App Security pour la visibilité et le contrôle d’utilisation | Microsoft Docs
description: Cette rubrique fournit des informations sur la connexion de votre application ServiceNow à Cloud App Security à l’aide du connecteur API.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/29/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: c626d94d-2ffd-4daf-8fa4-4b6d308cf012
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 75e22bb5ff151ea71ea2a48e5aef45f22fc4b5f8
ms.sourcegitcommit: bb010d8dd0a6eff39df31e33c2cc9c37ec321b46
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50217320"
---
*S’applique à : Microsoft Cloud App Security*

# <a name="connect-servicenow-to-microsoft-cloud-app-security"></a>Connecter ServiceNow à Microsoft Cloud App Security

Cette section fournit des instructions pour connecter Microsoft Cloud App Security à votre compte ServiceNow existant à l’aide de l’API du connecteur d’applications. 

> [!NOTE]
>  Nous vous recommandons de déployer ServiceNow à l’aide de jetons d’application OAuth, disponibles pour Fuji et versions ultérieures (consultez la [documentation ServiceNow](http://wiki.servicenow.com/index.php?title=OAuth_Applications#gsc.tab=0) appropriée). Pour les versions antérieures, un [mode de connexion hérité](#legacy-servicenow-connection) est disponible en fonction de l’utilisateur/du mot de passe. Le nom d’utilisateur et le mot de passe fournis sont utilisés uniquement pour générer les jetons API, et ils ne sont pas enregistrés après le processus initial de connexion.
> 
> [!NOTE]
>  Cloud App Security prend en charge les versions Eureka, Fiji, Geneva, Helsinki et Istanbul de ServiceNow. Pour connecter ServiceNow à Cloud App Security, vous devez avoir le rôle **Administrateur** et vérifier que l’instance ServiceNow prend en charge l’accès à l’API.  Pour plus d’informations, consultez la [documentation du produit ServiceNow](http://wiki.servicenow.com/index.php?title=Base_System_Roles#gsc.tab=0).
  
## <a name="how-to-connect-servicenow-to-cloud-app-security-using-oauth"></a>Comment connecter ServiceNow à Cloud App Security avec OAuth
  
  
1. Connectez-vous avec un compte d’administrateur à votre compte ServiceNow.  
 
   > [!NOTE]
   >  Le nom d’utilisateur et le mot de passe fournis sont utilisés uniquement pour générer les jetons API, et ils ne sont pas enregistrés après le processus initial de connexion.

2. Dans le volet de recherche **Filter navigator** (Navigateur de filtres), tapez **OAuth** et sélectionnez **Application Registry** (Registre d’application).

3. Dans la barre de menus **Application Registries** (Registres d’applications), cliquez sur **Nouveau** pour créer un profil OAuth.

   ![Nouveau profil OAuth ServiceNow](./media/servicenow-app-registry.png)

4. Sous **What kind of OAuth application?** (Quel type d’application OAuth ?), cliquez sur **Create an OAuth API endpoint for external clients** (Créer un point de terminaison d’API OAuth pour les clients externes).

   ![Type OAuth ServiceNow](./media/servicenow-oauth-app-type.png)

5. Sous **Application Registries New record** (Nouvel enregistrement des registres d’applications), renseignez les champs suivants :
    
    - Dans le champ **Nom**, nommez le nouveau profil OAuth, par exemple CloudAppSecurity. 
    
    - L’**ID de client** est généré automatiquement. Copiez cet ID et collez-le dans Cloud App Security pour établir la connexion.
    
    - Dans le champ **Secret client**, entrez une chaîne. Si ce champ reste vide, un secret aléatoire est généré automatiquement. Copiez la clé et enregistrez-la pour l’utiliser ultérieurement. 
    
    - Augmentez la valeur du champ **Access Token Lifespan** (Durée de vie du jeton d’accès) jusqu’à au moins 3 600.
    
    - Cliquez sur **Envoyer**.

   ![ID des profils ServiceNow](./media/servicenow-profile-ids.png)

6. Dans le portail Cloud App Security, cliquez sur **Examiner**, puis sur **Applications connectées**.  
  
7. Dans la page **Connecteurs d’application**, cliquez sur le bouton plus (+), puis sur **ServiceNow**.  
  
    ![connecter ServiceNow](./media/connect-servicenow.png "connecter ServiceNow")  
  
8. Dans la fenêtre contextuelle, ajoutez vos ID d’utilisateur, mot de passe, URL d’instance, ID de client et secret client ServiceNow dans les zones appropriées. Pour trouver votre ID d’utilisateur ServiceNow, dans le portail ServiceNow, accédez à **Utilisateurs**, puis recherchez votre nom dans le tableau.

   ![ID d’utilisateur ServiceNow](./media/servicenow-userid.png)
  
9. Cliquez sur **Connexion**.  
  
    ![ServiceNow - connexion à CAS](./media/servicenow-portal-connect.png "ServiceNow - connexion dans le portail")  
  
10. Vérifiez la connexion en cliquant sur **Tester maintenant**.  
  
    Le test peut prendre quelques minutes. Une fois averti que la connexion a réussi, cliquez sur **Fermer**.  
  
Après avoir connecté ServiceNow, vous recevez les événements des 60 jours précédant la connexion.
  
## <a name="legacy-servicenow-connection"></a>Connexion ServiceNow héritée

Pour connecter ServiceNow à Cloud App Security, vous devez avoir des autorisations de niveau administrateur et vérifier que l’instance ServiceNow prend en charge l’accès à l’API.   

1. Connectez-vous avec un compte d’administrateur à votre compte ServiceNow.   

2. Créez un compte de service pour Cloud App Security et attachez le rôle d’administrateur au compte nouvellement créé.   

3. Vérifiez que le plug-in API REST est activé.   

   ![compte ServiceNow](./media/servicenow-account.png "compte ServiceNow")   

4. Dans le portail Cloud App Security, cliquez sur **Examiner**, puis sur **Applications approuvées**.   

5. Dans la ligne ServiceNow, cliquez sur **Connecter** dans la colonne **État du connecteur d’applications** ou cliquez sur le bouton **Connecter une application**, puis sur **ServiceNow**.   

   ![connecter ServiceNow](./media/connect-servicenow.png "connecter ServiceNow")   

6. Dans la page Paramètres ServiceNow, sous l’onglet API, ajoutez vos ID d’utilisateur, mot de passe et URL d’instance ServiceNow dans les zones appropriées.   

7. Cliquez sur **Connexion**.   

   ![ServiceNow - mise à jour du mot de passe](./media/servicenow-update-password.png "ServiceNow - mise à jour du mot de passe")   

8. Vérifiez la connexion en cliquant sur **Test API** (Tester l’API).   
  
   Le test peut prendre quelques minutes. Une fois averti que la connexion a réussi, cliquez sur **Fermer**.    
   Après avoir connecté ServiceNow, vous recevrez les événements des 60 jours précédant la connexion. 


## <a name="next-steps"></a>Étapes suivantes 
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
