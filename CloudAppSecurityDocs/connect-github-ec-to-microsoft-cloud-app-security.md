---
title: Connecter GitHub Enterprise Cloud à Cloud App Security
description: Cet article fournit des informations sur la connexion de votre application Cloud GitHub Enterprise à Cloud App Security à l’aide du connecteur API pour la visibilité et le contrôle de l’utilisation.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/10/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ROBOTS: NOINDEX
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 774fd931210f5e3303b94e5903a724811583e61e
ms.sourcegitcommit: 98f1b892294beb74157cb3452aa5d489e78bbef4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94424518"
---
# <a name="connect-github-enterprise-cloud-to-microsoft-cloud-app-security"></a>Connecter GitHub Enterprise Cloud à Microsoft Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Cet article fournit des instructions pour connecter Microsoft Cloud App Security à votre organisation Cloud GitHub Enterprise existante à l’aide des API du connecteur d’applications. Cette connexion vous donne une visibilité et un contrôle sur l’utilisation du Cloud d’entreprise GitHub de votre organisation. Pour plus d’informations sur la façon dont Cloud App Security protège le Cloud GitHub Enterprise, consultez [protéger GitHub Enterprise](protect-github.md).

## <a name="prerequisites"></a>Prérequis

- Votre organisation doit disposer d’une licence Cloud GitHub Enterprise.
- Le compte GitHub utilisé pour la connexion à Cloud App Security doit disposer des autorisations de *propriétaire* pour votre organisation.
- Pour vérifier les propriétaires de votre organisation, accédez à la page de votre organisation, sélectionnez **personnes** , puis filtrez par *propriétaire*.

## <a name="how-to-connect-github-enterprise-cloud-to-cloud-app-security"></a>Comment connecter GitHub Enterprise Cloud à Cloud App Security

### <a name="verify-your-github-domains"></a>Vérifier vos domaines GitHub

La vérification de vos domaines est facultative. Toutefois, nous vous recommandons vivement de vérifier vos domaines afin que les Cloud App Security puissent faire correspondre les e-mails des membres de votre organisation GitHub à leur Azure Active Directory utilisateur correspondant.

Ces étapes peuvent être effectuées indépendamment de la procédure [configure GitHub Enterprise Cloud](#configure-github-enterprise-cloud) et peuvent être ignorées si vous avez déjà vérifié vos domaines.

1. Mettez à niveau votre organisation vers les [conditions de service de l’entreprise](https://help.github.com/en/github/setting-up-and-managing-organizations-and-teams/upgrading-to-the-corporate-terms-of-service).
1. Vérifiez [les domaines de votre organisation](https://help.github.com/en/github/setting-up-and-managing-organizations-and-teams/verifying-your-organizations-domain).

    > [!NOTE]
    > Veillez à vérifier chacun des domaines gérés figurant dans votre portail Cloud App Security. Pour afficher vos domaines gérés, dans Cloud App Security, accédez à **paramètres**  >  **organisation détails**  >  **domaines gérés**.

### <a name="configure-github-enterprise-cloud"></a>Configurer GitHub Enterprise Cloud

1. **Rechercher le nom de connexion de votre organisation**  
Dans GitHub, accédez à la page de votre organisation et, à partir de l’URL, prenez note du nom de connexion de votre organisation, vous en aurez besoin plus tard.

    > [!NOTE]
    > La page aura une URL telle que `https://github.com/<your-organization>` . Par exemple, si la page de votre organisation est `https://github.com/sample-organization` , le nom de connexion de l’organisation est *Sample-Organization*.

    ![Capture d’écran montrant l’obtention du nom de connexion de l’Organisation](media/connect-github-org-login-name.png)

1. **Créez une application OAuth pour Cloud App Security pour connecter votre organisation GitHub.**  
Répétez cette étape pour chaque organisation connectée supplémentaire.

    1. Accédez à **paramètres**  >  **paramètres du développeur** , sélectionnez **applications OAuth** , puis cliquez sur **inscrire une application**. Sinon, si vous avez des applications OAuth existantes, cliquez sur **nouvelle application OAuth**.

        ![Capture d’écran montrant la création d’une application OAuth](media/connect-github-create-oauth-app.png)

    1. Remplissez les détails **inscrire une nouvelle application OAuth** , puis cliquez sur **inscrire l’application**.
        - Dans la zone nom de l' **application** , entrez un nom pour l’application.
        - Dans la zone URL de la **page d’accueil** , entrez l’URL de la page d’accueil de l’application.
        - Dans la zone **URL de rappel d’autorisation** , entrez la valeur suivante : `https://portal.cloudappsecurity.com/api/oauth/connect` .

            > [!NOTE]
            > Pour les clients du gouvernement des États-Unis, entrez la valeur suivante : `https://portal.cloudappsecurity.us/api/oauth/connect`

        ![Capture d’écran montrant l’inscription d’une application OAuth](media/connect-github-register-oauth-app.png)

    > [!NOTE]
    >
    > - Par défaut, l’accès aux applications OAuth est limité pour les organisations. Pour activer l’accès, accédez à **paramètres**  >  **accès tiers** , cliquez sur **Supprimer les restrictions** , puis cliquez sur **Oui, supprimer les restrictions d’application**.
    > - Les applications appartenant à une organisation ont accès aux applications de l’organisation. Pour plus d’informations, consultez [à propos des restrictions d’accès aux applications OAuth](https://help.github.com/en/github/setting-up-and-managing-organizations-and-teams/about-oauth-app-access-restrictions).

1. Accédez à **paramètres**  >  **applications OAuth** , sélectionnez l’application OAuth que vous venez de créer et notez son **ID client** et sa **clé secrète client**.

    ![Capture d’écran montrant les détails d’une application OAuth](media/connect-github-oauth-app-details.png)

### <a name="configure-cloud-app-security"></a>Configurer Cloud App Security

1. Dans le portail Cloud App Security, cliquez sur **Examiner** , puis sur **Applications connectées**.

1. Dans la page **connecteurs d’application** , cliquez sur le bouton plus (+), puis sur **GitHub**.

1. Dans la fenêtre contextuelle, renseignez l' **ID client** , la **clé secrète client** et le **nom de connexion** de l’organisation que vous avez notés précédemment, puis cliquez sur **se connecter dans GitHub**.

    ![Capture d’écran montrant l’API Connect GitHub](media/connect-github-connect-app.png)

    La page de connexion GitHub s’ouvre. Si nécessaire, entrez vos informations d’identification d’administrateur GitHub pour autoriser Cloud App Security accès à l’instance de Cloud d’entreprise GitHub de votre équipe.

1. Autorisez l’application à fournir Cloud App Security pour accéder à votre organisation GitHub.

    > [!NOTE]
    > Cloud App Security requiert les étendues OAuth suivantes :
    >
    > - **admin :** organisation obligatoire pour la synchronisation du journal d’audit de votre organisation
    > - **lecture : utilisateur** et **utilisateur : e-mail** -requis pour la synchronisation des membres de votre organisation
    > - **référentiel : Status :** requis pour la synchronisation des événements liés au référentiel dans le journal d’audit. pour plus d’informations sur les étendues OAuth, consultez [Présentation des étendues pour les applications OAuth](https://developer.github.com/apps/building-oauth-apps/understanding-scopes-for-oauth-apps/).

    ![Capture d’écran montrant l’autorisation GitHub OAuth](media/connect-github-authorize-app.png)

1. De retour dans la console Cloud App Security, vous devez recevoir un message indiquant que GitHub a été correctement connecté.

1. Vérifiez que la connexion a réussi en cliquant sur **Tester l’API**.

    Le test peut prendre quelques minutes. Une fois que vous êtes averti que la connexion a réussi, cliquez sur **Fermer**.

Après avoir connecté GitHub Enterprise Cloud, vous recevrez des événements pendant 7 jours avant la connexion.

Si vous rencontrez des problèmes lors de la connexion de l’application, consultez [résolution des problèmes liés aux connecteurs d’application](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
