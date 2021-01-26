---
title: Déployer Cloud App Security contrôle d’application par accès conditionnel pour toute application Web à l’aide de PingOne
description: Cet article fournit des informations sur le déploiement du contrôle d’application par accès conditionnel Microsoft Cloud App Security pour toute application Web à l’aide du fournisseur d’identité PingOne.
ms.date: 09/29/2020
ms.topic: how-to
ms.openlocfilehash: df0ab81e2dcb6140f939caff436d18868daad496
ms.sourcegitcommit: f56a2060b99ab087b8637606a1fb66e5577aded8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98795067"
---
# <a name="onboard-and-deploy-conditional-access-app-control-for-any-web-app-using-pingone-as-the-identity-provider-idp"></a>Intégrer et déployer des contrôle d’application par accès conditionnel pour n’importe quelle application Web à l’aide de PingOne comme fournisseur d’identité (IdP)

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Vous pouvez configurer des contrôles de session dans Microsoft Cloud App Security pour fonctionner avec n’importe quelle application Web et n’importe quel fournisseur tiers. Cet article explique comment acheminer des sessions d’application à partir de PingOne vers Cloud App Security pour les contrôles de session en temps réel.

Pour cet article, nous allons utiliser l’application Salesforce comme exemple d’application Web configurée pour utiliser des contrôles de session Cloud App Security.

## <a name="prerequisites"></a>Prérequis

- Votre organisation doit disposer des licences suivantes pour utiliser contrôle d’application par accès conditionnel :

  - Une licence PingOne appropriée (requise pour l’authentification unique)
  - Microsoft Cloud App Security

- Une configuration d’authentification unique PingOne existante pour l’application à l’aide du protocole d’authentification SAML 2,0

## <a name="to-configure-session-controls-for-your-app-using-pingone-as-the-idp"></a>Pour configurer des contrôles de session pour votre application à l’aide de PingOne comme IdP

Suivez les étapes ci-dessous pour acheminer vos sessions d’application Web de PingOne vers Cloud App Security. Pour Azure AD étapes de configuration, consultez [configurer l’intégration avec Azure ad](proxy-deployment-any-app.md#configure-integration-with-azure-ad).

> [!NOTE]
> Vous pouvez configurer les informations d’authentification unique SAML de l’application fournies par PingOne à l’aide de l’une des méthodes suivantes :
>
> - **Option 1**: chargement du fichier de métadonnées SAML de l’application.
> - **Option 2**: fourniture manuelle des données SAML de l’application.
>
> Dans les étapes suivantes, nous allons utiliser l’option 2.

**Étape 1 : [obtenir les paramètres d’authentification unique SAML de votre application](#idp1-get-your-app-saml-sso-info)**

**Étape 2 : [configurer Cloud App Security avec les informations SAML de votre application](#idp1-conf-cas-with-your-app-saml-info)**

**Étape 3 : [créer une application personnalisée dans PingOne](#idp1-create-custom-app-pingone)**

**Étape 4 : [configurer Cloud App Security avec les informations de l’application PingOne](#idp1-conf-cas-with-pingone-app-info)**

**Étape 5 : [terminer l’application personnalisée dans PingOne](#idp1-complete-custom-app-in-pingone)**

**Étape 6 : [obtenir les modifications apportées à l’application dans Cloud App Security](#idp1-get-app-changes-in-cas)**

**Étape 7 : [terminer les modifications de l’application](#idp1-complete-app-changes)**

**Étape 8 : [terminer la configuration dans Cloud App Security](#idp1-complete-conf-in-cas)**

<a name="idp1-get-your-app-saml-sso-info"></a>

## <a name="step-1-get-your-apps-saml-single-sign-on-settings"></a>Étape 1 : obtenir les paramètres d’authentification unique SAML de votre application

1. Dans Salesforce, **accédez à**  >  **paramètres paramètres**  >  **identité**  >  **unique Sign-On paramètres**.

1. Sous **paramètres d' Sign-On unique**, cliquez sur le nom de votre configuration SAML 2,0 existante.

    ![Sélectionner les paramètres d’authentification unique Salesforce](media/proxy-idp-pingone/idp-pingone-sf-select-sso-settings.png)

1. Sur la page du **paramètre de Sign-On unique SAML** , notez l’URL de **connexion** Salesforce. Vous en aurez besoin plus tard.

    > [!NOTE]
    > Si votre application fournit un certificat SAML, téléchargez le fichier de certificat.

    ![Sélectionner l’URL de connexion d’authentification unique Salesforce](media/proxy-idp-pingone/idp-pingone-sf-copy-saml-sso-login-url.png)

<a name="idp1-conf-cas-with-your-app-saml-info"></a>

## <a name="step-2-configure-cloud-app-security-with-your-apps-saml-information"></a>Étape 2 : configurer Cloud App Security avec les informations SAML de votre application

1. Dans Cloud App Security, accédez à **examiner**  >  **applications connectées**  >  **contrôle d’application par accès conditionnel applications**.

1. Cliquez sur le signe plus ( **+** ), puis dans la fenêtre contextuelle, sélectionnez l’application que vous souhaitez déployer, puis cliquez sur **Démarrer l’Assistant**.
1. Dans la page **informations** sur l’application, sélectionnez **remplir les données manuellement**, dans l’URL du **service consommateur d’assertion** , entrez l’URL de **connexion** Salesforce que vous avez notée précédemment, puis cliquez sur **suivant**.

    > [!NOTE]
    > Si votre application fournit un certificat SAML, sélectionnez **utiliser <app_name> certificat SAML** et chargez le fichier de certificat.

    ![Renseignez manuellement les informations SAML Salesforce](media/proxy-idp-pingone/idp-pingone-cas-sf-app-info.png)

<a name="idp1-create-custom-app-pingone"></a>

## <a name="step-3-create-a-custom-app-in-pingone"></a>Étape 3 : créer une application personnalisée dans PingOne

Avant de continuer, procédez comme suit pour récupérer des informations à partir de votre application Salesforce existante.

1. Dans PingOne, modifiez votre application Salesforce existante.

1. Dans la page **mappage des attributs SSO** , notez l’attribut et la valeur SAML_SUBJECT, puis téléchargez le certificat de **signature** et les fichiers de **métadonnées SAML** .

    ![Notez les attributs de l’application Salesforce existante](media/proxy-idp-pingone/idp-pingone-sf-app-copy-saml-sso-attributes.png)

1. Ouvrez le fichier de métadonnées SAML et prenez note de l' **emplacement PingOne connexion**. Vous en aurez besoin plus tard.

    ![Notez l’emplacement du service SSO de l’application Salesforce existante](media/proxy-idp-pingone/idp-pingone-sf-app-copy-saml-sso-service-location.png)

1. Sur la page **accès au groupe** , prenez note des groupes affectés.

    ![Notez les groupes attribués de l’application Salesforce existante](media/proxy-idp-pingone/idp-pingone-sf-app-copy-saml-sso-user-groups.png)

Utilisez ensuite les instructions de la page **Ajouter une application SAML avec votre fournisseur d’identité** pour configurer une application personnalisée dans le portail de votre IDP.

![Ajouter une application SAML avec votre fournisseur d’identité](media/proxy-deploy-add-idp-get-conf.png)

> [!NOTE]
> La configuration d’une application personnalisée vous permet de tester l’application existante avec les contrôles d’accès et de session sans modifier le comportement actuel de votre organisation.

1. Créez une **nouvelle application SAML**.

    ![Dans PingOne, créer une application Salesforce personnalisée](media/proxy-idp-pingone/idp-pingone-sf-custom-app-new.png)

1. Dans la page Détails de l' **application** , remplissez le formulaire, puis cliquez sur **passer à l’étape suivante**.

    > [!TIP]
    > Utilisez un nom d’application qui vous permettra de faire la différence entre l’application personnalisée et l’application Salesforce existante.

    ![Renseignez les détails de l’application personnalisée](media/proxy-idp-pingone/idp-pingone-sf-custom-app-details.png)

1. Dans la page Configuration de l' **application** , procédez comme suit, puis cliquez sur **passer à l’étape suivante**.
    - Dans le champ **URL du service Sigh unique** , entrez l’URL de **connexion** Salesforce que vous avez notée précédemment.
    - Dans le champ **ID d’entité** , entrez un ID unique à partir de *https://*. Assurez-vous qu’il est différent de la configuration de l’application PingOne de salesforce.
    - Prenez note de l' **ID d’entité**. Vous en aurez besoin plus tard.

    ![Configurer une application personnalisée avec les détails SAML Salesforce](media/proxy-idp-pingone/idp-pingone-sf-custom-app-set-saml-sso-properties.png)

1. Dans la page **mappage des attributs SSO** , ajoutez l’attribut **SAML_SUBJECT** de l’application Salesforce existante et la valeur que vous avez notée précédemment, puis cliquez sur **passer à l’étape suivante**.

    ![Ajouter des attributs à l’application Salesforce personnalisée](media/proxy-idp-pingone/idp-pingone-sf-custom-app-set-saml-sso-attributes.png)

1. Sur la page **accès au groupe** , ajoutez les groupes de l’application Salesforce existante que vous avez notés précédemment, puis terminez la configuration.

    ![Affecter des groupes à l’application Salesforce personnalisée](media/proxy-idp-pingone/idp-pingone-sf-custom-app-set-saml-sso-user-groups.png)

<a name="idp1-conf-cas-with-pingone-app-info"></a>

## <a name="step-4-configure-cloud-app-security-with-the-pingone-apps-information"></a>Étape 4 : configurer Cloud App Security avec les informations de l’application PingOne

1. De retour dans la page Cloud App Security **fournisseur d’identité** , cliquez sur **suivant** pour continuer.

1. Sur la page suivante, sélectionnez **remplir les données manuellement**, effectuez les opérations suivantes, puis cliquez sur **suivant**.
    - Pour l' **URL du service consommateur d’assertion**, entrez l' **URL de connexion** Salesforce que vous avez notée précédemment.
    - Sélectionnez **Télécharger le certificat SAML du fournisseur d’identité** et téléchargez le fichier de certificat que vous avez téléchargé précédemment.

    ![Ajouter l’URL du service SSO et le certificat SAML](media/proxy-idp-pingone/idp-pingone-cas-sf-app-idp-info.png)

1. Sur la page suivante, prenez note des informations suivantes, puis cliquez sur **suivant**. Vous aurez besoin des informations ultérieurement.

    - URL d’authentification unique Cloud App Security
    - Attributs et valeurs de Cloud App Security

    ![Dans Cloud App Security, notez les attributs et URL SSO](media/proxy-idp-pingone/idp-pingone-cas-get-sf-app-external-config.png)

<a name="idp1-complete-custom-app-in-pingone"></a>

## <a name="step-5-complete-the-custom-app-in-pingone"></a>Étape 5 : terminer l’application personnalisée dans PingOne

1. Dans PingOne, localisez et modifiez l’application Salesforce personnalisée.

    ![Localiser et modifier une application Salesforce personnalisée](media/proxy-idp-pingone/idp-pingone-sf-custom-app-edit.png)

1. Dans le champ **service consommateur d’assertion (ACS)** , remplacez l’URL par la Cloud App Security URL d’authentification unique que vous avez notée précédemment, puis cliquez sur **suivant**.

    ![Remplacer ACS dans l’application Salesforce personnalisée](media/proxy-idp-pingone/idp-pingone-sf-custom-app-replace-saml-sso-properties.png)

1. Ajoutez les attributs et valeurs de Cloud App Security que vous avez notés précédemment dans les propriétés de l’application.

    ![Ajouter des attributs de Cloud App Security à l’application Salesforce personnalisée](media/proxy-idp-pingone/idp-pingone-sf-custom-app-replace-saml-sso-attributes.png)

1. Enregistrez vos paramètres.

<a name="idp1-get-app-changes-in-cas"></a>

## <a name="step-6-get-the-app-changes-in-cloud-app-security"></a>Étape 6 : obtenir les modifications apportées à l’application dans Cloud App Security

De retour dans la page modifications de l' **application** Cloud App Security, procédez comme suit, mais **ne cliquez pas sur Terminer**. Vous aurez besoin des informations ultérieurement.

- Copier l’URL d’authentification unique SAML Cloud App Security
- Télécharger le certificat SAML Cloud App Security

![Notez le Cloud App Security URL SSO SAML et téléchargez le certificat](media/proxy-idp-pingone/idp-pingone-cas-sf-app-changes.png)

<a name="idp1-complete-app-changes"></a>

## <a name="step-7-complete-the-app-changes"></a>Étape 7 : terminer les modifications de l’application

Dans Salesforce, **accédez à**  >  **paramètres paramètres**  >  **identité**  >  **unique Sign-On paramètres**, puis procédez comme suit :

1. Recommandé : créez une sauvegarde de vos paramètres actuels.
1. Remplacez la valeur du champ **URL de connexion du fournisseur d’identité** par la Cloud App Security URL d’authentification unique SAML que vous avez notée précédemment.
1. Téléchargez le certificat SAML Cloud App Security que vous avez téléchargé précédemment.
1. Remplacez la valeur du champ **ID d’entité** par l’ID d’entité d’application personnalisée PingOne que vous avez noté précédemment.
1. Cliquez sur **Enregistrer**.

    > [!NOTE]
    > Le certificat SAML Cloud App Security est valide pendant un an. Après son expiration, un nouveau certificat doit être généré.

    ![Mettre à jour l’application Salesforce personnalisée avec Cloud App Security détails SAML](media/proxy-idp-pingone/idp-pingone-sf-custom-app-changes.png)

<a name="idp1-complete-conf-in-cas"></a>

## <a name="step-8-complete-the-configuration-in-cloud-app-security"></a>Étape 8 : terminer la configuration dans Cloud App Security

- De retour dans la page modifications de l' **application** Cloud App Security, cliquez sur **Terminer**. Une fois l’Assistant terminé, toutes les demandes de connexion associées à cette application sont acheminées via contrôle d’application par accès conditionnel.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [«PRÉCÉDENT : déployer contrôle d’application par accès conditionnel pour toutes les applications](proxy-deployment-any-app.md)

## <a name="see-also"></a>Voir aussi

> [!div class="nextstepaction"]
> [Présentation de contrôle d’application par accès conditionnel](proxy-intro-aad.md)

> [!div class="nextstepaction"]
> [Résolution des problèmes de contrôles d’accès et de session](troubleshooting-proxy.md)

[!INCLUDE [Open support ticket](includes/support.md)]
