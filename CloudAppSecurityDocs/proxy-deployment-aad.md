---
title: Déployer le contrôle d’application par accès conditionnel Cloud App Security pour les applications Azure AD
description: Cet article fournit des informations sur le déploiement du proxy inversé du Contrôle d’application par accès conditionnel Microsoft Cloud App Security pour les applications Azure AD.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/31/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: b2cc376ee93d4f052227cbc3a0e8e8f04e564ae3
ms.sourcegitcommit: ecb1835d1cd880de38f32ce7a7031b0015f3cae5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81241340"
---
# <a name="deploy-conditional-access-app-control-for-featured-apps"></a>Déployer le contrôle d’application par accès conditionnel pour les applications à la une

*S’applique à : Microsoft Cloud App Security*

Les contrôles de session dans Microsoft Cloud App Security fonctionner avec les applications proposées. Pour obtenir la liste des applications qui sont proposées par Cloud App Security pour un travail prêt à l’emploi, consultez [protéger les applications avec Cloud App Security contrôle d’application par accès conditionnel](proxy-intro-aad.md#featured-apps).

## <a name="prerequisites"></a>Prérequis

- Votre organisation doit disposer des licences suivantes pour utiliser contrôle d’application par accès conditionnel :

  - [Azure Active Directory (Azure AD) Premium P1](https://docs.microsoft.com/azure/active-directory/license-users-groups) ou supérieure, ou la licence requise par votre solution IDP (Identity Provider)
  - Microsoft Cloud App Security

- Les applications doivent être configurées avec l’authentification unique
- Les applications doivent utiliser l’un des protocoles d’authentification suivants :

    |Fournisseur d’identité (IdP)|Protocoles|
    |---|---|
    |Azure AD|SAML 2,0 ou OpenID Connect|
    |Autres|SAML 2.0|

## <a name="to-deploy-featured-apps"></a>Pour déployer des applications proposées

Procédez comme suit pour configurer les applications proposées pour qu’elles soient contrôlées par Microsoft Cloud App Security contrôle d’application par accès conditionnel.

**Étape 1 : [configurer votre IDP pour qu’il fonctionne avec Cloud App Security](#conf-idp)**

**Étape 2 : [se connecter à chaque application à l’aide d’un utilisateur dont l’étendue est limitée à la stratégie](#sign-in-scoped)**

**Étape 3 : [vérifier que les applications sont configurées pour utiliser les contrôles d’accès et de session](#portal)**

**Étape 4 : [tester le déploiement](#test)**

## <a name="step-1--configure-your-idp-to-work-with-cloud-app-security"></a>Étape 1 : configurer votre IdP pour qu’il fonctionne avec Cloud App Security<a name="conf-idp"></a><a name="add-azure-ad"></a>

### <a name="configure-integration-with-azure-ad"></a>Configurer l’intégration avec Azure AD

Utilisez les étapes suivantes pour créer une stratégie d’accès conditionnel Azure AD qui achemine les sessions d’application vers Cloud App Security. Pour d’autres solutions IdP, consultez [configurer l’intégration avec d’autres solutions IDP](#configure-integration-with-other-idp-solutions).

1. Dans Azure ad, accédez à **sécurité** > **accès conditionnel**.

1. Dans le volet **accès conditionnel** , dans la barre d’outils située en haut, cliquez sur **nouvelle stratégie**.

1. Dans le volet **nouveau** , dans la zone de texte **nom** , entrez le nom de la stratégie.

1. Sous **affectations**, cliquez sur **utilisateurs et groupes**, affectez à l’application les utilisateurs qui seront intégrés (authentification initiale et vérification), puis cliquez sur **terminé**.

1. Sous **affectations**, cliquez sur **applications Cloud**, affectez les applications que vous souhaitez contrôler avec contrôle d’application par accès conditionnel, puis cliquez sur **terminé**.

1. Sous **contrôles d’accès**, cliquez sur **session**, sélectionnez **utiliser contrôle d’application par accès conditionnel** et choisissez des stratégies intégrées (**surveiller uniquement** ou **bloquer les téléchargements**) ou **Utilisez une stratégie personnalisée** pour définir une stratégie avancée dans Cloud App Security, puis cliquez sur **Sélectionner**.

    ![Accès conditionnel Azure AD](media/azure-ad-caac-policy.png)

1. Si vous le souhaitez, ajoutez des conditions et accordez des contrôles en fonction des besoins.

1. Affectez à **activer la stratégie** la valeur **activé** , puis cliquez sur **créer**.

### <a name="configure-integration-with-other-idp-solutions"></a>Configurer l’intégration à d’autres solutions IdP

Suivez les étapes ci-dessous pour acheminer des sessions d’application d’autres solutions IdP vers Cloud App Security. Pour Azure AD, consultez [configurer l’intégration avec Azure ad](#configure-integration-with-azure-ad).

1. Dans > Cloud App Security, accédez à **examiner** > **applications connectées****contrôle d’application par accès conditionnel applications**.

1. Cliquez sur le signe plus, puis dans la fenêtre contextuelle, sélectionnez l’application que vous souhaitez déployer, puis cliquez sur **Démarrer l’Assistant**.
1. Sur la page informations sur l' **application** , remplissez le formulaire à l’aide des informations de la page Configuration de l’authentification unique de votre application, puis cliquez sur **suivant**.
    - Si votre IdP fournit un fichier de métadonnées d’authentification unique pour l’application sélectionnée, sélectionnez **charger le fichier de métadonnées à partir de l’application** et téléchargez le fichier de métadonnées.
    - Ou sélectionnez **remplir les données manuellement** et fournissez les informations suivantes :
        - **URL du service consommateur d’assertion**
        - Si votre application fournit un certificat SAML, sélectionnez **utiliser <app_name> certificat SAML** et chargez le fichier de certificat.

    ![Capture d’écran montrant la page d’informations de l’application](media/proxy-deploy-add-idp-app-info.png)

1. Dans la page **fournisseur d’identité** , utilisez les étapes fournies pour configurer une nouvelle application dans le portail de votre IDP, puis cliquez sur **suivant**.
    1. Accédez au portail de votre IdP et créez une nouvelle application SAML personnalisée.
    1. Copiez la configuration de l’authentification unique de l' `<app_name>` application existante dans la nouvelle application personnalisée.
    1. Affecter des utilisateurs à la nouvelle application personnalisée.
    1. Copiez la configuration de l’authentification unique de l’application inf’rmation. vous en aurez besoin à l’étape suivante.

    ![Capture d’écran de la page rassembler les informations du fournisseur d’identité](media/proxy-deploy-add-idp-get-conf.png)

    > [!NOTE]
    > Ces étapes peuvent varier légèrement en fonction de votre fournisseur d’identité. Cette étape est recommandée pour les raisons suivantes :
    >
    > - Certains fournisseurs d’identité ne vous permettent pas de modifier les attributs SAML ou les propriétés URL d’une application de la Galerie
    > - La configuration d’une application personnalisée vous permet de tester cette application avec des contrôles d’accès et de session sans modifier le comportement existant pour votre organisation.

1. Sur la page suivante, remplissez le formulaire à l’aide des informations de la page de configuration de l’authentification unique de votre application, puis cliquez sur **suivant**.
    - Si votre IdP fournit un fichier de métadonnées d’authentification unique pour l’application sélectionnée, sélectionnez **charger le fichier de métadonnées à partir de l’application** et téléchargez le fichier de métadonnées.
    - Ou sélectionnez **remplir les données manuellement** et fournissez les informations suivantes :
        - **URL du service consommateur d’assertion**
        - Si votre application fournit un certificat SAML, sélectionnez **utiliser <app_name> certificat SAML** et chargez le fichier de certificat.

    ![Capture d’écran de la page entrer les informations du fournisseur d’identité](media/proxy-deploy-add-idp-enter-conf.png)

1. Sur la page suivante, copiez les informations suivantes, puis cliquez sur **suivant**. Vous aurez besoin des informations de l’étape suivante.

    - URL d’authentification unique
    - Attributs et valeurs

    ![Capture d’écran de la page rassembler les informations SAML des fournisseurs d’identité](media/proxy-deploy-add-idp-ext-conf.png)

1. Dans le portail de votre IdP, procédez comme suit :
    > [!NOTE]
    > Les paramètres se trouvent généralement dans la page Paramètres de l’application personnalisée du portail IdP.

    1. Dans le champ URL d’authentification unique, entrez l’URL d’authentification unique que vous avez notée précédemment.
        > [!NOTE]
        > Certains fournisseurs peuvent faire référence à l’URL de l’authentification unique en tant qu' *URL de réponse*.
    1. Ajoutez les attributs et les valeurs que vous avez notés précédemment aux propriétés des applications.
        > [!NOTE]
        > Certains fournisseurs peuvent y faire référence en tant qu' *attributs utilisateur* ou *revendications*.
    1. Vérifiez que l’identificateur de nom est au format d’adresse de messagerie.
    1. Enregistrez vos paramètres.
1. Sur la page modifications de l' **application** , procédez comme suit, puis cliquez sur **suivant**. Vous aurez besoin des informations de l’étape suivante.

    - Copier l’URL d’authentification unique
    - Télécharger le certificat SAML Cloud App Security

    ![Capture d’écran montrant la page de rassemblement Cloud App Security informations SAML](media/proxy-deploy-add-idp-app-changes.png)

1. Dans le portail de votre application, sur les paramètres d’authentification unique, procédez comme suit :
    1. Recommandations Créez une sauvegarde de vos paramètres actuels.
    1. Dans le champ URL d’authentification unique, entrez l’URL d’authentification unique que vous avez notée précédemment.
    1. Téléchargez le certificat Cloud App Security SAML que vous avez noté précédemment.
    > [!NOTE]
    > Une fois vos paramètres enregistrés, toutes les demandes de connexion associées à cette application sont acheminées via contrôle d’application par accès conditionnel.

## <a name="step-2-sign-in-to-each-app-using-a-user-scoped-to-the-policy"></a>Étape 2 : se connecter à chaque application à l’aide d’un utilisateur dont l’étendue est limitée à la stratégie<a name="sign-in-scoped"></a>

> [!NOTE]
> Avant de continuer, veillez à vous déconnecter des sessions existantes.

Une fois que vous avez créé la stratégie, connectez-vous à chaque application configurée dans cette stratégie. Veillez à vous connecter à l’aide d’un utilisateur configuré dans la stratégie.

Cloud App Security synchronisera vos détails de stratégie sur ses serveurs pour chaque nouvelle application à laquelle vous vous connectez. Cette opération peut prendre jusqu’à une minute.

## <a name="step-3-verify-the-apps-are-configured-to-use-access-and-session-controls"></a>Étape 3 : vérifier que les applications sont configurées pour utiliser les contrôles d’accès et de session<a name="portal"></a>

Les instructions ci-dessus vous ont aidé à créer une stratégie Cloud App Security intégrée pour les applications proposées directement dans Azure AD. Dans cette étape, vérifiez que les contrôles d’accès et de session sont configurés pour ces applications.

1. Dans le portail Cloud App Security, cliquez sur l’icône Paramètres roue dentée ![paramètres](media/settings-icon.png "icône des paramètres"), puis sélectionnez **contrôle d’application par accès conditionnel**.

1. Dans le tableau contrôle d’application par accès conditionnel Apps, examinez la colonne **contrôles disponibles** et vérifiez que le **contrôle d’accès** ou l' **accès conditionnel Azure ad**, et que le **contrôle de session** s’affiche pour vos applications.

    > [!NOTE]
    > Si le contrôle de session n’apparaît pas pour une application, il n’est pas encore disponible pour cette application spécifique. Vous pouvez l’ajouter immédiatement en tant qu' [application personnalisée](proxy-deployment-any-app.md), ou vous pouvez ouvrir une demande pour l’ajouter en tant qu’application proposée en cliquant sur **demander un contrôle de session**.
    >
    >![Demande du Contrôle d’application par accès conditionnel](media/caac-request.png)

## <a name="step-4-test-the-deployment"></a>Étape 4 : tester le déploiement<a name="test"></a>

1. Tout d’abord, déconnectez-vous de toutes les sessions existantes. Ensuite, essayez de vous connecter à chaque application qui a été déployée avec succès. Connectez-vous à l’aide d’un utilisateur qui correspond à la stratégie configurée dans Azure AD ou pour une application SAML configurée avec votre fournisseur d’identité.

1. Dans le portail Cloud App Security, sous **Examiner**, sélectionnez **Journal d’activité** et vérifiez que les activités de connexion sont capturées pour chaque application.

1. Vous pouvez filtrer en cliquant sur **Avancé**, puis en filtrant avec **Source est égale à Contrôle d’accès**.

    ![Filtrer à l’aide de l’accès conditionnel Azure AD](media/sso-logon.png)

1. Nous vous recommandons de vous connecter aux applications mobiles et de bureau à partir d’appareils gérés et non gérés, afin de vous assurer que les activités sont correctement capturées dans le journal d’activité.  
Pour vérifier que l’activité est correctement capturée, cliquez sur une activité de connexion d’authentification unique afin qu’elle ouvre le tiroir d’activité. Vérifiez que l’**Étiquette agent utilisateur** indique correctement si l’appareil est un client natif (à savoir, une application mobile ou de bureau) ou un appareil géré (conforme, joint à un domaine ou avec certificat client valide).

> [!NOTE]
> Après son déploiement, vous ne pouvez pas supprimer une application à partir de la page Contrôle d’application par accès conditionnel. Tant que vous ne définissez pas une stratégie d’accès ou de session sur l’application, le contrôle d’application par accès conditionnel ne change pas le comportement de l’application.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [«PRÉCÉDENT : introduction à contrôle d’application par accès conditionnel](proxy-intro-aad.md)

> [!div class="nextstepaction"]
> [Étape suivante : intégration et déploiement de contrôle d’application par accès conditionnel pour une application»](proxy-deployment-any-app.md)

[!INCLUDE [Open support ticket](includes/support.md)]
