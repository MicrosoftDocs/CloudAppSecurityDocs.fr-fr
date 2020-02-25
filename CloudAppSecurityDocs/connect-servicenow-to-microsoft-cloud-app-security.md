---
title: Connecter ServiceNow à Cloud App Security
description: Cet article fournit des informations sur la connexion de votre application ServiceNow à Cloud App Security à l’aide du connecteur API pour la visibilité et le contrôle de l’utilisation.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 6/24/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: a1214e0067d5c83ff001ff6c0e8a27fb227bc7e9
ms.sourcegitcommit: 9fe879ce7f07933866191724de5f108f43e3f923
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2020
ms.locfileid: "77566833"
---
# <a name="connect-servicenow-to-microsoft-cloud-app-security"></a>Connecter ServiceNow à Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

Cet article fournit des instructions pour connecter Microsoft Cloud App Security à votre compte ServiceNow existant à l’aide de l’API du connecteur d’applications. Cette connexion vous donne une visibilité et un contrôle sur l’utilisation de ServiceNow. Pour plus d’informations sur la façon dont Cloud App Security protège les ServiceNow, consultez [protéger ServiceNow](protect-servicenow.md).

> [!NOTE]
> Nous vous recommandons de déployer ServiceNow à l’aide de jetons d’application OAuth, disponibles pour Fuji et versions ultérieures (consultez la [documentation ServiceNow](https://wiki.servicenow.com/index.php?title=OAuth_Applications#gsc.tab=0)correspondante.
> Pour les versions antérieures, un [mode de connexion hérité](#legacy-servicenow-connection) est disponible en fonction de l’utilisateur/mot de passe. Le nom d’utilisateur/mot de passe fourni sont uniquement utilisés pour la génération de jetons d’API et ne sont pas enregistrés après le processus de connexion initial.

> [!NOTE]
> Cloud App Security prend en charge les versions ServiceNow de Jakarta, Kingston, Eureka, Fidji, Geneva, Helsinki, Istanbul, London et Madrid. Pour connecter ServiceNow à Cloud App Security, vous devez disposer de l' **administrateur** de rôle et vérifier que l’instance ServiceNow prend en charge l’accès aux API.  Pour plus d’informations, consultez la [documentation du produit ServiceNow](https://wiki.servicenow.com/index.php?title=Base_System_Roles#gsc.tab=0).

## <a name="how-to-connect-servicenow-to-cloud-app-security-using-oauth"></a>Comment connecter ServiceNow à Cloud App Security à l’aide d’OAuth

1. Connectez-vous avec un compte d’administrateur à votre compte ServiceNow.

    > [!NOTE]
    > Le nom d’utilisateur/mot de passe fourni sont uniquement utilisés pour la génération de jetons d’API et ne sont pas enregistrés après le processus de connexion initial.

2. Dans la barre de recherche du **navigateur de filtres** , tapez **OAuth** et sélectionnez Registre de l' **application**.

3. Dans la barre de menus **registres des applications** , cliquez sur **nouveau** pour créer un nouveau profil OAuth.

    ![ServiceNow nouveau profil OAuth](media/servicenow-app-registry.png)

4. Sous **quel type d’application OAuth ?** , cliquez sur **créer un point de terminaison d’API OAuth pour les clients externes**.

    ![Type OAuth ServiceNow](media/servicenow-oauth-app-type.png)

5. Dans **registres des applications, nouvel enregistrement** , renseignez les champs suivants :

    - Champ **nom** , nommez le nouveau profil OAuth, par exemple, CloudAppSecurity.

    - L' **ID client** est généré automatiquement. Copiez cet ID, vous devez le coller dans Cloud App Security pour terminer la connexion.

    - Dans le champ **clé secrète client** , entrez une chaîne. S’il est laissé vide, un secret aléatoire est généré automatiquement. Copiez-le et enregistrez-le pour une version ultérieure.

    - Augmentez la durée de **vie du jeton d’accès** à au moins 3 600.

    - Cliquez sur **Submit**.

    ![ID de profil ServiceNow](media/servicenow-profile-ids.png)

6. Dans le portail Cloud App Security, cliquez sur **examiner** , puis sur **applications connectées**.

7. Dans la page **connecteurs d’application** , cliquez sur le bouton plus, puis sur **ServiceNow**.

    ![connecter ServiceNow](media/connect-servicenow.png "connecter ServiceNow")

8. Dans la fenêtre contextuelle, ajoutez vos ID d’utilisateur, mot de passe, URL d’instance, ID client et clé secrète client ServiceNow dans les zones appropriées. Pour trouver votre ID d’utilisateur ServiceNow, dans le portail ServiceNow, accédez à **utilisateurs** , puis recherchez votre nom dans le tableau.

    ![ID d’utilisateur ServiceNow](media/servicenow-userid.png)

9. Cliquez sur **Se connecter**.

    ![ServiceNow se connecter aux autorités de certification](media/servicenow-portal-connect.png "ServiceNow se connecter dans le portail")

10. Vérifiez que la connexion a réussi en cliquant sur **tester maintenant**.

    Le test peut prendre quelques minutes. Après avoir reçu un avis de réussite, cliquez sur **Fermer**.

Après avoir connecté ServiceNow, vous recevrez des événements pendant 7 jours avant la connexion.

## <a name="legacy-servicenow-connection"></a>Connexion ServiceNow héritée

Pour connecter ServiceNow avec Cloud App Security, vous devez disposer d’autorisations au niveau de l’administrateur et vous assurer que l’instance ServiceNow prend en charge l’accès aux API.

1. Connectez-vous avec un compte d’administrateur à votre compte ServiceNow.

2. Créez un compte de service pour Cloud App Security et associez le rôle d’administrateur au compte nouvellement créé.

3. Assurez-vous que le plug-in de l’API REST est activé.

    ![Compte ServiceNow](media/servicenow-account.png "Compte ServiceNow")

4. Dans le portail Cloud App Security, cliquez sur **examiner** , puis sur **applications**approuvées.

5. Sur la ligne ServiceNow, cliquez sur **se connecter** dans la colonne **État du connecteur d’applications** , ou cliquez sur le bouton **connecter une application** , puis sur **ServiceNow**.

   ![connecter ServiceNow](media/connect-servicenow.png "connecter ServiceNow")

6. Dans la page Paramètres ServiceNow, sous l’onglet API, ajoutez votre ID d’utilisateur, votre mot de passe et votre URL d’instance ServiceNow dans les zones appropriées.

7. Cliquez sur **Se connecter**.

    ![ServiceNow mettre à jour le mot de passe](media/servicenow-update-password.png "ServiceNow mettre à jour le mot de passe")

8. Vérifiez la connexion en cliquant sur **Test API** (Tester l’API).

    Le test peut prendre quelques minutes. Après avoir reçu un avis de réussite, cliquez sur **Fermer**.

Après avoir connecté ServiceNow, vous recevrez des événements pendant 7 jours avant la connexion.

Si vous rencontrez des problèmes lors de la connexion de l’application, consultez [résolution des problèmes liés aux connecteurs d’application](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Étapes suivantes :

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
