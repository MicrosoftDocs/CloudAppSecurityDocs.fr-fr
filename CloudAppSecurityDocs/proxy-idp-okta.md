---
title: Déployer Cloud App Security contrôle d’application par accès conditionnel pour toute application Web à l’aide de Okta
description: Cet article fournit des informations sur le déploiement du contrôle d’application par accès conditionnel Microsoft Cloud App Security pour toute application Web à l’aide de Okta comme fournisseur d’identité.
ms.date: 02/18/2021
ms.topic: how-to
ms.openlocfilehash: 8d431689e69c88c31f30fd5d58d718e929eb9a2f
ms.sourcegitcommit: 859594eee0b0bdfab86930f91c994ce609f8debe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2021
ms.locfileid: "101873386"
---
# <a name="onboard-and-deploy-conditional-access-app-control-for-any-web-app-using-okta-as-the-identity-provider-idp"></a>Intégrer et déployer des contrôle d’application par accès conditionnel pour n’importe quelle application Web à l’aide de Okta comme fournisseur d’identité (IdP)

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Vous pouvez configurer des contrôles de session dans Microsoft Cloud App Security pour fonctionner avec n’importe quelle application Web et n’importe quel fournisseur tiers. Cet article explique comment acheminer des sessions d’application à partir de Okta vers Cloud App Security pour les contrôles de session en temps réel.

Pour cet article, nous allons utiliser l’application Salesforce comme exemple d’application Web configurée pour utiliser des contrôles de session Cloud App Security.

## <a name="prerequisites"></a>Prérequis

- Votre organisation doit disposer des licences suivantes pour utiliser contrôle d’application par accès conditionnel :

  - Un locataire Okta préconfiguré.
  - Microsoft Cloud App Security

- Une configuration d’authentification unique Okta existante pour l’application à l’aide du protocole d’authentification SAML 2,0

## <a name="to-configure-session-controls-for-your-app-using-okta-as-the-idp"></a>Pour configurer des contrôles de session pour votre application à l’aide de Okta comme IdP

Suivez les étapes ci-dessous pour acheminer vos sessions d’application Web de Okta vers Cloud App Security. Pour Azure AD étapes de configuration, consultez [configurer l’intégration avec Azure ad](proxy-deployment-any-app.md#configure-integration-with-azure-ad).

> [!NOTE]
> Vous pouvez configurer les informations d’authentification unique SAML de l’application fournies par Okta à l’aide de l’une des méthodes suivantes :
>
> - **Option 1**: chargement du fichier de métadonnées SAML de l’application.
> - **Option 2**: fourniture manuelle des données SAML de l’application.
>
> Dans les étapes suivantes, nous allons utiliser l’option 2.

**Étape 1 : [obtenir les paramètres d’authentification unique SAML de votre application](#idp1-get-your-app-saml-sso-info)**

**Étape 2 : [configurer Cloud App Security avec les informations SAML de votre application](#idp1-conf-cas-with-your-app-saml-info)**

**Étape 3 : [créer une application personnalisée Okta et une configuration de Sign-On unique](#idp1-create-custom-app-okta) de l’application**

**Étape 4 : [configurer Cloud App Security avec les informations de l’application Okta](#idp1-conf-cas-with-okta-app-info)**

**Étape 5 : [terminer la configuration de l’application personnalisée Okta](#idp1-complete-custom-app-in-okta)**

**Étape 6 : [obtenir les modifications apportées à l’application dans Cloud App Security](#idp1-get-app-changes-in-cas)**

**Étape 7 : [terminer les modifications de l’application](#idp1-complete-app-changes)**

**Étape 8 : [terminer la configuration dans Cloud App Security](#idp1-complete-conf-in-cas)**

<a name="idp1-get-your-app-saml-sso-info"></a>

## <a name="step-1-get-your-apps-saml-single-sign-on-settings"></a>Étape 1 : obtenir les paramètres d’authentification unique SAML de votre application

1. Dans Salesforce, **accédez à**  >  **paramètres paramètres**  >  **identité**  >  **unique Sign-On paramètres**.

1. Sous **paramètres d' Sign-On unique**, cliquez sur le nom de votre configuration Okta existante.

    ![Sélectionner les paramètres d’authentification unique Salesforce](media/proxy-idp-okta/idp-okta-sf-select-sso-settings.png)

1. Sur la page du **paramètre de Sign-On unique SAML** , notez l’URL de **connexion** Salesforce. Vous en aurez besoin plus tard lors de la configuration de Cloud App Security.

    > [!NOTE]
    > Si votre application fournit un certificat SAML, téléchargez le fichier de certificat.

    ![Sélectionner l’URL de connexion d’authentification unique Salesforce](media/proxy-idp-okta/idp-okta-sf-copy-saml-sso-login-url.png)

<a name="idp1-conf-cas-with-your-app-saml-info"></a>

## <a name="step-2-configure-cloud-app-security-with-your-apps-saml-information"></a>Étape 2 : configurer Cloud App Security avec les informations SAML de votre application

1. Dans Cloud App Security, accédez à **examiner**  >  **applications connectées**  >  **contrôle d’application par accès conditionnel applications**.

1. Cliquez sur le signe plus, puis dans la fenêtre contextuelle, sélectionnez l’application que vous souhaitez déployer, puis cliquez sur **Démarrer l’Assistant**.
1. Dans la page **informations** sur l’application, sélectionnez **remplir les données manuellement**, dans l’URL du **service consommateur d’assertion** , entrez l’URL de **connexion** Salesforce que vous avez notée précédemment, puis cliquez sur **suivant**.

    > [!NOTE]
    > Si votre application fournit un certificat SAML, sélectionnez **utiliser <app_name> certificat SAML** et chargez le fichier de certificat.

    ![Renseignez manuellement les informations SAML Salesforce](media/proxy-idp-okta/idp-okta-cas-sf-app-info.png)

<a name="idp1-create-custom-app-okta"></a>

## <a name="step-3-create-a-new-okta-custom-application-and-app-single-sign-on-configuration"></a>Étape 3 : créer une application personnalisée Okta et une configuration de Sign-On unique de l’application

> [!NOTE]
> Pour limiter les temps d’arrêt de l’utilisateur final et conserver votre configuration existante connue, nous vous recommandons de créer une nouvelle **application personnalisée** et une **seule configuration de Sign-On**. Si ce n’est pas possible, ignorez les étapes pertinentes. Par exemple, si l’application que vous configurez ne prend pas en charge la création de plusieurs **configurations de Sign-On unique**, ignorez l’étape créer une nouvelle authentification unique.

1. Dans la console d' **administration Okta** , sous **applications**, affichez les propriétés de votre configuration existante pour votre application et prenez note des paramètres.

1. Cliquez sur **Ajouter une application**, puis sur créer une **nouvelle** application. En dehors de la valeur de l' **URI d’audience (ID d’entité SP)** qui doit être un nom unique, configurez la nouvelle application à l’aide des paramètres que vous avez notés précédemment. Vous aurez besoin de cette application ultérieurement lors de la configuration de Cloud App Security.
1. Accédez à **applications**, affichez votre configuration Okta existante, puis dans l’onglet **authentification** , sélectionnez **afficher les instructions d’installation**.

    ![Notez l’emplacement du service SSO de l’application Salesforce existante](media/proxy-idp-okta/idp-okta-sf-view-setup-instructions.png)

1. Prenez note de l' **URL d' Sign-On unique du fournisseur d’identité** et téléchargez le certificat de signature du fournisseur d’identité (X. 509). Vous en aurez besoin plus tard.

1. De retour dans Salesforce, dans la page des paramètres d’authentification unique Okta, prenez note de tous les paramètres.
1. Créez une nouvelle configuration de l’authentification unique SAML. En dehors de la valeur d' **ID d’entité** qui doit correspondre à l’URI d’audience de l’application personnalisée **(ID d’entité SP)**, configurez l’authentification unique à l’aide des paramètres que vous avez notés précédemment. Vous en aurez besoin plus tard lors de la configuration de Cloud App Security.
1. Après avoir enregistré votre nouvelle application, accédez à la page **affectations** et affectez les **personnes** ou les **groupes** qui requièrent l’accès à l’application.

<a name="idp1-conf-cas-with-okta-app-info"></a>ׂ

## <a name="step-4-configure-cloud-app-security-with-the-okta-apps-information"></a>Étape 4 : configurer Cloud App Security avec les informations de l’application Okta

1. De retour dans la page Cloud App Security **fournisseur d’identité** , cliquez sur **suivant** pour continuer.

1. Sur la page suivante, sélectionnez **remplir les données manuellement**, effectuez les opérations suivantes, puis cliquez sur **suivant**.
    - Pour l' **URL du service d’authentification unique**, entrez l' **URL de connexion** Salesforce que vous avez notée précédemment.
    - Sélectionnez **Télécharger le certificat SAML du fournisseur d’identité** et téléchargez le fichier de certificat que vous avez téléchargé précédemment.

    ![Ajouter l’URL du service SSO et le certificat SAML](media/proxy-idp-okta/idp-okta-cas-sf-app-idp-info.png)

1. Sur la page suivante, prenez note des informations suivantes, puis cliquez sur **suivant**. Vous aurez besoin des informations ultérieurement.

    - URL d’authentification unique Cloud App Security
    - Attributs et valeurs de Cloud App Security

    > [!NOTE]
    > Si vous voyez une option permettant de télécharger le **certificat SAML Cloud App Security pour le fournisseur d’identité**, cliquez sur le Cliquer pour télécharger le fichier de certificat. Vous en aurez besoin plus tard.

    ![Dans Cloud App Security, notez les attributs et URL SSO](media/proxy-idp-okta/idp-okta-cas-get-sf-app-external-config.png)

<a name="idp1-complete-custom-app-in-okta"></a>

## <a name="step-5-complete-the-configuration-of-the-okta-custom-application"></a>Étape 5 : terminer la configuration de l’application personnalisée Okta

1. De retour dans la console d' **administration Okta** , sous **applications**, sélectionnez l’application personnalisée que vous avez créée précédemment, puis sous   >  **paramètres SAML** généraux, cliquez sur **modifier**.

    ![Localiser et modifier les paramètres SAML](media/proxy-idp-okta/idp-okta-sf-saml-settings-edit.png)

1. Dans le champ **URL d’authentification unique** , remplacez l’URL par la Cloud App Security URL d’authentification unique que vous avez notée précédemment, puis enregistrez vos paramètres.

1. Sous **répertoire**, sélectionnez **éditeur de profil**, sélectionnez l’application personnalisée que vous avez créée précédemment, puis cliquez sur **Profil**. Ajoutez des attributs à l’aide des informations suivantes.

    | Nom complet | Nom de la variable | Type de données | Type d'attribut |
    | --- | --- | --- | --- |
    | McasSigningCert | McasSigningCert | string | Custom |
    | McasAppId | McasAppId | string | Custom |

    ![Ajouter des attributs de profil](media/proxy-idp-okta/idp-okta-sf-add-profile-attributes-edit.png)

1. De retour dans la page de l' **éditeur de profil** , sélectionnez l’application personnalisée que vous avez créée précédemment, cliquez sur **mappages**, puis sélectionnez **utilisateur Okta sur {custom_app_name}**. Mappez les attributs **McasSigningCert** et **McasAppId** aux valeurs d’attribut Cloud App Security que vous avez notées précédemment.

    > [!NOTE]
    >
    > - Veillez à placer les valeurs entre guillemets doubles (")
    > - Okta limite les attributs à 1024 caractères. Pour atténuer cette limitation, ajoutez les attributs à l’aide de l' **éditeur de profil** comme décrit.

    ![Mapper les attributs de profil](media/proxy-idp-okta/idp-okta-sf-map-profile-attributes-edit.png)

1. Enregistrez vos paramètres.

<a name="idp1-get-app-changes-in-cas"></a>

## <a name="step-6-get-the-app-changes-in-cloud-app-security"></a>Étape 6 : obtenir les modifications apportées à l’application dans Cloud App Security

De retour dans la page modifications de l' **application** Cloud App Security, procédez comme suit, mais **ne cliquez pas sur Terminer**. Vous aurez besoin des informations ultérieurement.

- Copier l’URL d’authentification unique SAML Cloud App Security
- Télécharger le certificat SAML Cloud App Security

![Notez le Cloud App Security URL SSO SAML et téléchargez le certificat](media/proxy-idp-okta/idp-okta-cas-sf-app-changes.png)

<a name="idp1-complete-app-changes"></a>

## <a name="step-7-complete-the-app-changes"></a>Étape 7 : terminer les modifications de l’application

Dans Salesforce, **accédez à**  >  **paramètres paramètres**  >  **identité**  >  **unique Sign-On paramètres**, puis procédez comme suit :

1. Recommandations Créez une sauvegarde de vos paramètres actuels.
1. Remplacez la valeur du champ **URL de connexion du fournisseur d’identité** par la Cloud App Security URL d’authentification unique SAML que vous avez notée précédemment.
1. Téléchargez le certificat SAML Cloud App Security que vous avez téléchargé précédemment.
1. Cliquez sur **Enregistrer**.

    > [!NOTE]
    >
    > - Une fois vos paramètres enregistrés, toutes les demandes de connexion associées à cette application sont acheminées via contrôle d’application par accès conditionnel.
    > - Le certificat SAML Cloud App Security est valide pendant un an. Après son expiration, un nouveau certificat doit être généré.

    ![Mettre à jour les paramètres SSO](media/proxy-idp-okta/idp-okta-sf-update-sso-settings.png)

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
