---
title: Déployer Cloud App Security contrôle d’application par accès conditionnel pour toute application Web à l’aide de AD FS
description: Cet article fournit des informations sur le déploiement du contrôle d’application par accès conditionnel Microsoft Cloud App Security pour toute application Web à l’aide de AD FS en tant que fournisseur d’identité.
ms.date: 01/26/2021
ms.topic: how-to
ms.openlocfilehash: 74a454332125162dbec74f076d150ffe1b9d9b45
ms.sourcegitcommit: f56a2060b99ab087b8637606a1fb66e5577aded8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98795066"
---
# <a name="onboard-and-deploy-conditional-access-app-control-for-any-web-app-using-active-directory-federation-services-ad-fs-as-the-identity-provider-idp"></a>Intégrer et déployer des contrôle d’application par accès conditionnel pour n’importe quelle application Web utilisant services de fédération Active Directory (AD FS) (AD FS) en tant que fournisseur d’identité (IdP)

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Vous pouvez configurer des contrôles de session dans Microsoft Cloud App Security pour fonctionner avec n’importe quelle application Web et n’importe quel fournisseur tiers. Cet article explique comment acheminer des sessions d’application à partir de AD FS vers Cloud App Security pour les contrôles de session en temps réel.

Pour cet article, nous allons utiliser l’application Salesforce comme exemple d’application Web configurée pour utiliser des contrôles de session Cloud App Security.

## <a name="prerequisites"></a>Prérequis

- Votre organisation doit disposer des licences suivantes pour utiliser contrôle d’application par accès conditionnel :

  - Un environnement préconfiguré AD FS
  - Microsoft Cloud App Security

- Une configuration d’authentification unique AD FS existante pour l’application à l’aide du protocole d’authentification SAML 2,0

## <a name="to-configure-session-controls-for-your-app-using-ad-fs-as-the-idp"></a>Pour configurer des contrôles de session pour votre application à l’aide de AD FS comme IdP

Suivez les étapes ci-dessous pour acheminer vos sessions d’application Web de AD FS vers Cloud App Security. Pour Azure AD étapes de configuration, consultez [configurer l’intégration avec Azure ad](proxy-deployment-any-app.md#configure-integration-with-azure-ad).

> [!NOTE]
> Vous pouvez configurer les informations d’authentification unique SAML de l’application fournies par AD FS à l’aide de l’une des méthodes suivantes :
>
> - **Option 1**: chargement du fichier de métadonnées SAML de l’application.
> - **Option 2**: fourniture manuelle des données SAML de l’application.
>
> Dans les étapes suivantes, nous allons utiliser l’option 2.

**Étape 1 : [obtenir les paramètres d’authentification unique SAML de votre application](#idp1-get-your-app-saml-sso-info)**

**Étape 2 : [configurer Cloud App Security avec les informations SAML de votre application](#idp1-conf-cas-with-your-app-saml-info)**

**Étape 3 : [créer une nouvelle AD FS approbation de partie de confiance et une configuration d’application Sign-On unique](#idp1-create-custom-app-adfs)**

**Étape 4 : [configurer Cloud App Security avec les informations de l’application AD FS](#idp1-conf-cas-with-adfs-app-info)**

**Étape 5 : [terminer la configuration de l’approbation de la partie de confiance AD FS](#idp1-complete-custom-app-in-adfs)**

**Étape 6 : [obtenir les modifications apportées à l’application dans Cloud App Security](#idp1-get-app-changes-in-cas)**

**Étape 7 : [terminer les modifications de l’application](#idp1-complete-app-changes)**

**Étape 8 : [terminer la configuration dans Cloud App Security](#idp1-complete-conf-in-cas)**

<a name="idp1-get-your-app-saml-sso-info"></a>

## <a name="step-1-get-your-apps-saml-single-sign-on-settings"></a>Étape 1 : obtenir les paramètres d’authentification unique SAML de votre application

1. Dans Salesforce, **accédez à**  >  **paramètres paramètres**  >  **identité**  >  **unique Sign-On paramètres**.

1. Sous **paramètres d' Sign-On unique**, cliquez sur le nom de votre configuration de AD FS existante.

    ![Sélectionner les paramètres d’authentification unique Salesforce](media/proxy-idp-adfs/idp-adfs-sf-select-sso-settings.png)

1. Sur la page du **paramètre de Sign-On unique SAML** , notez l’URL de **connexion** Salesforce. Vous en aurez besoin plus tard lors de la configuration de Cloud App Security.

    > [!NOTE]
    > Si votre application fournit un certificat SAML, téléchargez le fichier de certificat.

    ![Sélectionner l’URL de connexion d’authentification unique Salesforce](media/proxy-idp-adfs/idp-adfs-sf-copy-saml-sso-login-url.png)

<a name="idp1-conf-cas-with-your-app-saml-info"></a>

## <a name="step-2-configure-cloud-app-security-with-your-apps-saml-information"></a>Étape 2 : configurer Cloud App Security avec les informations SAML de votre application

1. Dans Cloud App Security, accédez à **examiner**  >  **applications connectées**  >  **contrôle d’application par accès conditionnel applications**.

1. Cliquez sur le signe plus, puis dans la fenêtre contextuelle, sélectionnez l’application que vous souhaitez déployer, puis cliquez sur **Démarrer l’Assistant**.
1. Dans la page **informations** sur l’application, sélectionnez **remplir les données manuellement**, dans l’URL du **service consommateur d’assertion** , entrez l’URL de **connexion** Salesforce que vous avez notée précédemment, puis cliquez sur **suivant**.

    > [!NOTE]
    > Si votre application fournit un certificat SAML, sélectionnez **utiliser <app_name> certificat SAML** et chargez le fichier de certificat.

    ![Renseignez manuellement les informations SAML Salesforce](media/proxy-idp-adfs/idp-adfs-cas-sf-app-info.png)

<a name="idp1-create-custom-app-adfs"></a>

## <a name="step-3-create-a-new-ad-fs-relying-party-trust-and-app-single-sign-on-configuration"></a>Étape 3 : créer une nouvelle AD FS approbation de partie de confiance et une configuration d’application Sign-On unique

> [!NOTE]
> Pour limiter les temps d’arrêt de l’utilisateur final et conserver votre configuration existante connue, nous vous recommandons de créer une nouvelle **approbation de partie de confiance** et une **seule configuration de Sign-On**. Si ce n’est pas possible, ignorez les étapes pertinentes. Par exemple, si l’application que vous configurez ne prend pas en charge la création de plusieurs **configurations de Sign-On unique**, ignorez l’étape créer une nouvelle authentification unique.

1. Dans la console de **gestion AD FS** , sous **approbations de partie de confiance**, affichez les propriétés de votre approbation de partie de confiance existante pour votre application et notez les paramètres.

1. Sous **actions**, cliquez sur **Ajouter une approbation de partie de confiance**. En dehors de la valeur d' **identificateur** qui doit être un nom unique, configurez la nouvelle approbation à l’aide des paramètres que vous avez notés précédemment. Vous aurez besoin de cette approbation plus tard lors de la configuration de Cloud App Security.
1. Ouvrez le fichier de métadonnées de Fédération et prenez note de l’emplacement de l’AD FS **connexion**. Vous en aurez besoin plus tard.

    > [!NOTE]
    > Vous pouvez utiliser le point de terminaison suivant pour accéder à votre fichier de métadonnées de Fédération : `https://<Your_Domain>/federationmetadata/2007-06/federationmetadata.xml`

    ![Notez l’emplacement du service SSO de l’application Salesforce existante](media/proxy-idp-adfs/idp-adfs-sf-app-copy-saml-sso-service-location.png)

1. Téléchargez le certificat de signature du fournisseur d’identité. Vous en aurez besoin plus tard.
    1. Sous   >  **certificats** de services, cliquez avec le bouton droit sur le certificat de signature AD FS, puis sélectionnez **afficher le certificat**.

        ![Afficher les propriétés du certificat de signature IdP](media/proxy-idp-adfs/idp-adfs-view-signing-cert-props.png)

    1. Dans l’onglet Détails du certificat, cliquez sur **copier dans un fichier** et suivez les étapes de l' **Assistant exportation de certificat** pour exporter votre certificat sous la forme d’un *X. 509 encodé en base 64 (. CER)* .

        ![Enregistrer le fichier de certificat de signature IdP](media/proxy-idp-adfs/idp-adfs-save-signing-cert-file.png)

1. De retour dans Salesforce, dans la page AD FS des paramètres d’authentification unique existants, prenez note de tous les paramètres.
1. Créez une nouvelle configuration de l’authentification unique SAML. En dehors de la valeur d' **ID d’entité** qui doit correspondre à l' **identificateur** d’approbation de la partie de confiance, configurez l’authentification unique à l’aide des paramètres que vous avez notés précédemment. Vous en aurez besoin plus tard lors de la configuration de Cloud App Security.

<a name="idp1-conf-cas-with-adfs-app-info"></a>

## <a name="step-4-configure-cloud-app-security-with-the-ad-fs-apps-information"></a>Étape 4 : configurer Cloud App Security avec les informations de l’application AD FS

1. De retour dans la page Cloud App Security **fournisseur d’identité** , cliquez sur **suivant** pour continuer.

1. Sur la page suivante, sélectionnez **remplir les données manuellement**, effectuez les opérations suivantes, puis cliquez sur **suivant**.
    - Pour l' **URL du service d’authentification unique**, entrez l' **URL de connexion** Salesforce que vous avez notée précédemment.
    - Sélectionnez **Télécharger le certificat SAML du fournisseur d’identité** et téléchargez le fichier de certificat que vous avez téléchargé précédemment.

    ![Ajouter l’URL du service SSO et le certificat SAML](media/proxy-idp-adfs/idp-adfs-cas-sf-app-idp-info.png)

1. Sur la page suivante, prenez note des informations suivantes, puis cliquez sur **suivant**. Vous aurez besoin des informations ultérieurement.

    - URL d’authentification unique Cloud App Security
    - Attributs et valeurs de Cloud App Security

    > [!NOTE]
    > Si vous voyez une option permettant de télécharger le **certificat SAML Cloud App Security pour le fournisseur d’identité**, cliquez sur le lien pour télécharger le fichier de certificat. Vous en aurez besoin plus tard.

    ![Dans Cloud App Security, notez les attributs et URL SSO](media/proxy-idp-adfs/idp-adfs-cas-get-sf-app-external-config.png)

<a name="idp1-complete-custom-app-in-adfs"></a>

## <a name="step-5-complete-the-configuration-of-the-ad-fs-relying-party-trust"></a>Étape 5 : terminer la configuration de l’approbation de la partie de confiance AD FS

1. Dans la console de **gestion de AD FS** , cliquez avec le bouton droit sur l’approbation de la partie de confiance que vous avez créée précédemment, puis sélectionnez Modifier la stratégie d’émission de **revendication**.

    ![Rechercher et modifier l’émission de la revendication d’approbation de confiance](media/proxy-idp-adfs/idp-adfs-sf-relying-trust-edit.png)

1. Dans la boîte de dialogue **modifier la stratégie d’émission de revendication** , sous règles de transformation d' **émission**, utilisez les informations fournies dans le tableau suivant pour effectuer les étapes de création de règles personnalisées.

    | Nom de la règle de revendication | Règle personnalisée |
    | --- | --- |
    | McasSigningCert | `=> issue(type="McasSigningCert", value="<value>");` où `<value>` est la valeur **McasSigningCert** de l’Assistant Cloud App Security que vous avez notée précédemment |
    | McasAppId | `=> issue(type="McasAppId", value="<value>");` est la valeur **McasAppId** de l’Assistant Cloud App Security que vous avez notée précédemment |

    1. Cliquez **sur Ajouter une règle**, sous modèle de règle de **revendication** , sélectionnez Envoyer des **revendications à l’aide d’une règle personnalisée**, puis cliquez sur **suivant**.
    1. Dans la page **configurer la règle** , entrez le **nom** de la règle de revendication respective et la **règle personnalisée** fournie.

    > [!NOTE]
    > Ces règles s’ajoutent aux règles de revendication ou aux attributs requis par l’application que vous configurez.

1. De retour sur la page approbation de la **partie de confiance** , cliquez avec le bouton droit sur l’approbation de la partie de confiance que vous avez créée précédemment, puis sélectionnez **Propriétés**.
1. Sous l’onglet **points de terminaison** , sélectionnez point de **terminaison consommateur d’assertion SAML**, cliquez sur **modifier** et remplacez l' **URL approuvée** par la Cloud App Security URL d’authentification unique que vous avez notée précédemment, puis cliquez sur **OK**.

    ![Mettre à jour les propriétés du point de terminaison d’approbation de confiance URL approuvée](media/proxy-idp-adfs/idp-adfs-sf-relying-trust-endpoint-properties.png)

1. Si vous avez téléchargé un **certificat SAML Cloud App Security pour le fournisseur d’identité**, sous l’onglet **signature** , cliquez sur **Ajouter** et chargez le fichier de certificat, puis cliquez sur **OK**.

    ![Mettre à jour les propriétés de la signature d’approbation de confiance certificat SAML](media/proxy-idp-adfs/idp-adfs-sf-relying-trust-signature-properties.png)

1. Enregistrez vos paramètres.

<a name="idp1-get-app-changes-in-cas"></a>

## <a name="step-6-get-the-app-changes-in-cloud-app-security"></a>Étape 6 : obtenir les modifications apportées à l’application dans Cloud App Security

De retour dans la page modifications de l' **application** Cloud App Security, procédez comme suit, mais **ne cliquez pas sur Terminer**. Vous aurez besoin des informations ultérieurement.

- Copier l’URL d’authentification unique SAML Cloud App Security
- Télécharger le certificat SAML Cloud App Security

![Notez le Cloud App Security URL SSO SAML et téléchargez le certificat](media/proxy-idp-adfs/idp-adfs-cas-sf-app-changes.png)

<a name="idp1-complete-app-changes"></a>

## <a name="step-7-complete-the-app-changes"></a>Étape 7 : terminer les modifications de l’application

Dans Salesforce, **accédez à**  >  **paramètres paramètres**  >  **identité**  >  **unique Sign-On paramètres**, puis procédez comme suit :

1. Recommandé : créez une sauvegarde de vos paramètres actuels.
1. Remplacez la valeur du champ **URL de connexion du fournisseur d’identité** par la Cloud App Security URL d’authentification unique SAML que vous avez notée précédemment.
1. Téléchargez le certificat SAML Cloud App Security que vous avez téléchargé précédemment.
1. Cliquez sur **Enregistrer**.

    > [!NOTE]
    > Le certificat SAML Cloud App Security est valide pendant un an. Après son expiration, un nouveau certificat doit être généré.

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
