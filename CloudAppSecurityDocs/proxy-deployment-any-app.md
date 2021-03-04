---
title: Déployer des contrôle d’application par accès conditionnel Cloud App Security pour toutes les applications
description: Cet article fournit des informations sur le déploiement de la Microsoft Cloud App Security contrôle d’application par accès conditionnel les fonctionnalités de proxy inverse pour toutes les applications.
ms.date: 02/18/2021
ms.topic: how-to
ms.openlocfilehash: 2657bb5226ca0a0b33620a2d036535b42f1d8e09
ms.sourcegitcommit: 859594eee0b0bdfab86930f91c994ce609f8debe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2021
ms.locfileid: "101829872"
---
# <a name="onboard-and-deploy-conditional-access-app-control-for-any-app"></a>Intégrer et déployer le Contrôle d’application par accès conditionnel pour tous les types d’applications

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Les contrôles de session dans Microsoft Cloud App Security peuvent être configurés pour fonctionner avec n’importe quelle application Web. Cet article explique comment intégrer et déployer des applications métier personnalisées, des applications SaaS non proposées et des applications locales hébergées via le proxy d’application Azure Active Directory (Azure AD) avec des contrôles de session.

Pour obtenir la liste des applications qui sont proposées par Cloud App Security pour un travail prêt à l’emploi, consultez [protéger les applications avec Cloud App Security contrôle d’application par accès conditionnel](proxy-intro-aad.md#featured-apps).

## <a name="prerequisites"></a>Prérequis

- Votre organisation doit disposer des licences suivantes pour utiliser contrôle d’application par accès conditionnel :

  - [Azure Active Directory (Azure AD) Premium P1](/azure/active-directory/license-users-groups) ou supérieure, ou la licence requise par votre solution IDP (Identity Provider)
  - Microsoft Cloud App Security

- Les applications doivent être configurées avec l’authentification unique
- Les applications doivent utiliser l’un des protocoles d’authentification suivants :

    |Fournisseur d’identité|Protocoles|
    |---|---|
    |Azure AD|SAML 2.0 ou OpenID Connect|
    |Autre|SAML 2.0|

## <a name="to-deploy-any-app"></a>Pour déployer une application

Procédez comme suit pour configurer une application devant être contrôlée par Cloud App Security contrôle d’application par accès conditionnel.

**Étape 1 : [configurer votre IDP pour qu’il fonctionne avec Cloud App Security](#conf-idp)**

**Étape 2 : [configurer les utilisateurs qui déploieront l’application](#conf-users)**

**Étape 3 : [configurer l’application que vous déployez](#conf-app)**

**Étape 4 : [vérifier que l’application fonctionne correctement](#verify-app)**

**Étape 5 : [activer l’application en vue de son utilisation dans votre organisation](#enable-app)**

**Étape 6 : [mettre à jour la stratégie de Azure ad](#update-azure-ad)**

> [!NOTE]
> Pour déployer contrôle d’application par accès conditionnel pour les applications Azure AD, vous avez besoin d’une [licence valide pour Azure Active Directory Premium P1 ou version ultérieure](/azure/active-directory/license-users-groups) , ainsi qu’une licence Cloud App Security.

## <a name="step-1--configure-your-idp-to-work-with-cloud-app-security"></a>Étape 1 : configurer votre IdP pour qu’il fonctionne avec Cloud App Security<a name="conf-idp"></a><a name="conf-azure-ad"></a>

### <a name="configure-integration-with-azure-ad"></a>Configurer l’intégration avec Azure AD

Utilisez les étapes suivantes pour créer une stratégie d’accès conditionnel Azure AD qui achemine les sessions d’application vers Cloud App Security. Pour d’autres solutions IdP, consultez [configurer l’intégration avec d’autres solutions IDP](#configure-integration-with-other-idp-solutions).

1. Dans Azure ad, accédez à **sécurité**  >  **accès conditionnel**.

1. Dans le volet **accès conditionnel** , dans la barre d’outils située en haut, cliquez sur **nouvelle stratégie**.

1. Dans le volet **nouveau** , dans la zone de texte **nom** , entrez le nom de la stratégie.

1. Sous **affectations**, cliquez sur **utilisateurs et groupes**, affectez à l’application les utilisateurs qui seront intégrés (authentification initiale et vérification), puis cliquez sur **terminé**.

1. Sous **affectations**, cliquez sur **applications Cloud**, affectez les applications que vous souhaitez contrôler avec contrôle d’application par accès conditionnel, puis cliquez sur **terminé**.

1. Sous **contrôles d’accès**, cliquez sur **session**, sélectionnez **utiliser contrôle d’application par accès conditionnel** et choisissez une stratégie intégrée (**surveiller uniquement** ou **bloquer les téléchargements**) ou **Utilisez une stratégie personnalisée** pour définir une stratégie avancée dans Cloud App Security, puis cliquez sur **Sélectionner**.

    ![Accès conditionnel Azure AD](media/azure-ad-caac-policy.png)

1. Si vous le souhaitez, ajoutez des conditions et accordez des contrôles en fonction des besoins.

1. Affectez à **activer la stratégie** la valeur **activé** , puis cliquez sur **créer**.

### <a name="configure-integration-with-other-idp-solutions"></a>Configurer l’intégration à d’autres solutions IdP

Suivez les étapes ci-dessous pour acheminer des sessions d’application d’autres solutions IdP vers Cloud App Security. Pour Azure AD, consultez [configurer l’intégration avec Azure ad](#configure-integration-with-azure-ad).

> [!NOTE]
> Pour obtenir des exemples de configuration des solutions IdP, consultez :
>
> - [Configurer votre IdP PingOne](proxy-idp-pingone.md)
> - [Configurer votre AD FS IdP](proxy-idp-adfs.md)
> - [Configurer votre IdP Okta](proxy-idp-okta.md)

1. Dans Cloud App Security, accédez à **examiner**  >  **applications connectées**  >  **contrôle d’application par accès conditionnel applications**.

1. Cliquez sur le signe plus ( **+** ), puis dans la fenêtre contextuelle, sélectionnez l’application que vous souhaitez déployer, puis cliquez sur **Démarrer l’Assistant**.
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
    1. Copiez les informations de configuration de l’authentification unique des applications. vous en aurez besoin à l’étape suivante.

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

    1. Recommandations Créez une sauvegarde de vos paramètres actuels.
    1. Remplacez la valeur du champ URL d’authentification unique par le Cloud App Security URL d’authentification unique SAML que vous avez notée précédemment.
        > [!NOTE]
        > Certains fournisseurs peuvent faire référence à l’URL de l’authentification unique en tant qu' *URL de réponse*.
    1. Ajoutez les attributs et les valeurs que vous avez notés précédemment aux propriétés de l’application.
        > [!NOTE]
        >
        > - Certains fournisseurs peuvent y faire référence en tant qu' *attributs utilisateur* ou *revendications*.
        > - Lors de la création d’une nouvelle application SAML, le fournisseur d’identité Okta limite les attributs à 1024 caractères. Pour atténuer cette limitation, commencez par créer l’application sans les attributs appropriés. Après avoir créé l’application, modifiez-la, puis ajoutez les attributs appropriés.

    1. Vérifiez que l’identificateur de nom est au format d’adresse de messagerie.
    1. Enregistrez vos paramètres.
1. Sur la page modifications de l' **application** , procédez comme suit, puis cliquez sur **suivant**. Vous aurez besoin des informations de l’étape suivante.

    - Copier l’URL d’authentification unique
    - Télécharger le certificat SAML Cloud App Security

    ![Capture d’écran montrant la page de rassemblement Cloud App Security informations SAML](media/proxy-deploy-add-idp-app-changes.png)

1. Dans le portail de votre application, sur les paramètres d’authentification unique, procédez comme suit :
    1. Recommandations Créez une sauvegarde de vos paramètres actuels.
    1. Dans le champ URL d’authentification unique, entrez l’Cloud App Security URL d’authentification unique que vous avez notée précédemment.
    1. Téléchargez le certificat SAML Cloud App Security que vous avez téléchargé précédemment.
    > [!NOTE]
    >
    > - Une fois vos paramètres enregistrés, toutes les demandes de connexion associées à cette application sont acheminées via contrôle d’application par accès conditionnel.
    > - Le certificat SAML Cloud App Security est valide pendant un an. Après son expiration, un nouveau certificat doit être généré.

## <a name="step-2-configure-the-users-that-will-deploy-the-app"></a>Étape 2 : configurer les utilisateurs qui déploieront l’application<a name="conf-users"></a>

1. Dans Cloud App Security, dans la barre de menus, cliquez sur l' ![icône](media/settings-icon.png "Icône des paramètres") paramètres roue dentée paramètres, puis sélectionnez **paramètres**.

1. Sous **contrôle d’application par accès conditionnel**, sélectionnez **intégration/maintenance** de l’application.

1. Entrez le nom d’utilisateur principal ou l’adresse de messagerie des utilisateurs qui intégreront l’application, puis cliquez sur **Enregistrer**.

    ![Capture d’écran des paramètres d’intégration et de maintenance des applications.](media/app-onboarding-settings.png)

## <a name="step-3-configure-the-app-that-you-are-deploying"></a>Étape 3 : configurer l’application que vous déployez<a name="conf-app"></a>

Accédez à l’application que vous déployez. La page que vous voyez varie selon que l’application est reconnue ou non. Effectuez l’une des opérations suivantes :

| État de l’application | Description | Étapes |
| --- | --- | --- |
| Non reconnu | Une page application non reconnue s’affiche et vous invite à configurer votre application. | 1. [Ajoutez l’application à contrôle d’application par accès conditionnel](#add-app).<br /> 2. [Ajoutez les domaines pour l’application](#add-domains), puis revenez à l’application et actualisez la page.<br /> 3. [Installez les certificats pour l’application](#install-certs). |
| Reconnu | Une page d’intégration s’affiche pour vous inviter à poursuivre le processus de configuration de l’application. | - [Installez les certificats pour l’application](#install-certs). <br /><br /> **Remarque :** Assurez-vous que l’application est configurée avec tous les domaines requis pour que l’application fonctionne correctement. Pour configurer des domaines supplémentaires, continuez à [Ajouter les domaines pour l’application](#add-domains), puis revenez à la page de l’application. |

### <a name="to-add-a-new-app"></a>Pour ajouter une nouvelle application<a name="add-app"></a>

1. Dans la barre de menus, cliquez sur l' ![icône](media/settings-icon.png "Icône des paramètres")paramètres roue dentée paramètres, puis sélectionnez **contrôle d’application par accès conditionnel**.

1. Dans la bannière, cliquez sur **afficher les nouvelles applications**.

    ![Afficher les nouvelles applications du Contrôle d’application par accès conditionnel](media/caac-view-apps.png)

1. Dans la liste des nouvelles applications, pour chaque application que vous intégrez, cliquez sur le **+** signe, puis sur **Ajouter**.

    > [!NOTE]
    > Si une application n’apparaît pas dans le catalogue d’applications Cloud App Security, elle figure, dans la boîte de dialogue, sous les applications non identifiées, avec son URL de connexion. Lorsque vous cliquez sur le signe + pour ces applications, vous pouvez intégrer l’application en tant qu’application personnalisée.

    ![Applications Azure AD découvertes du Contrôle d’application par accès conditionnel](media/caac-discovered-aad-apps.png)

### <a name="to-add-domains-for-an-app"></a>Pour ajouter des domaines pour une application<a name="add-domains"></a>

L’Association des domaines appropriés à une application permet à Cloud App Security d’appliquer des stratégies et des activités d’audit.

Par exemple, si vous avez configuré une stratégie qui bloque le téléchargement de fichiers pour un domaine associé, les téléchargements de fichiers par l’application à partir de ce domaine seront bloqués. Toutefois, les téléchargements de fichiers par l’application à partir de domaines non associés à l’application ne seront pas bloqués et l’action ne sera pas auditée dans le journal d’activité.
> [!NOTE]
> Cloud App Security ajoute toujours un suffixe aux domaines non associés à l’application pour garantir une expérience utilisateur transparente.

1. À partir de l’application, dans la barre d’outils d’administration de Cloud App Security, cliquez sur **domaines découverts**.
    > [!NOTE]
    > La barre d’outils d’administration n’est visible que pour les utilisateurs disposant d’autorisations d’intégration ou de maintenance d’applications.
1. Dans le volet domaines découverts, prenez note des noms de domaine ou exportez la liste sous forme de fichier. csv.
    > [!NOTE]
    > Le volet affiche la liste des domaines détectés qui ne sont pas associés à l’application. Les noms de domaine sont qualifiés complets.
1. Accédez à Cloud App Security, dans la barre de menus, cliquez sur l' ![icône](media/settings-icon.png "Icône des paramètres") paramètres roue dentée paramètres, puis sélectionnez **contrôle d’application par accès conditionnel**.
1. Dans la liste des applications, sur la ligne dans laquelle l’application que vous déployez s’affiche, choisissez les trois points à la fin de la ligne, puis sous **Détails** de l’application, choisissez **modifier**.
    > [!TIP]
    > Pour afficher la liste des domaines configurés dans l’application, cliquez sur **afficher les domaines d’application**.
1. Dans **domaines définis par l’utilisateur**, entrez tous les domaines que vous souhaitez associer à cette application, puis cliquez sur **Enregistrer**.
    > [!NOTE]
    > Vous pouvez utiliser le caractère générique * en tant qu’espace réservé pour n’importe quel caractère. Lorsque vous ajoutez des domaines, déterminez si vous souhaitez ajouter des domaines spécifiques ( `sub1.contoso.com` , `sub2.contoso.com` ) ou plusieurs domaines ( `*.contoso.com` ).

### <a name="to-install-root-certificates"></a>Pour installer des certificats racines<a name="install-certs"></a>

1. Répétez les étapes suivantes pour installer l' **autorité de certification actuelle** et les certificats racines auto-signés suivants de l' **autorité de certification** .
    1. Sélectionnez le certificat.
    1. Cliquez sur **ouvrir**, puis lorsque vous y êtes invité, cliquez à nouveau sur **ouvrir** .
    1. Cliquez sur **installer le certificat**.
    1. Choisissez l' **utilisateur actuel** ou l' **ordinateur local**.
    1. Sélectionnez **Placer tous les certificats dans le magasin suivant** , puis cliquez sur **Parcourir**.
    1. Sélectionnez **autorités de certification racines de confiance** , puis cliquez sur **OK**.
    1. Cliquez sur **Terminer**.

    > [!NOTE]
    > Pour que les certificats soient reconnus, une fois que vous avez installé le certificat, vous devez redémarrer le navigateur et accéder à la même page.<!-- You'll see a check-mark by the certificates links confirmation they are installed.-->

1. Cliquez sur **Continuer**.

## <a name="step-4-verify-that-the-app-is-working-correctly"></a>Étape 4 : vérifier que l’application fonctionne correctement<a name="verify-app"></a>

1. Vérifiez que le processus de connexion fonctionne correctement.
    <!--
    > [!NOTE]
    > Some apps issue a nonce hash during authentication that may break the sign-in process. If this happens, see the Troubleshooting Guide to resolve the issue.-->
1. Une fois que vous êtes dans l’application, effectuez les vérifications suivantes :
    1. Accédez à toutes les pages de l’application qui font partie du processus de travail des utilisateurs et vérifiez que les pages s’affichent correctement.
    1. Vérifiez que le comportement et les fonctionnalités de l’application ne sont pas affectés par l’exécution d’actions courantes telles que le téléchargement et le chargement de fichiers.
    1. Passez en revue la liste des domaines associés à l’application. Pour plus d’informations, consultez [Ajouter les domaines pour l’application](#add-domains).

## <a name="step-5-enable-the-app-for-use-in-your-organization"></a>Étape 5 : activer l’application en vue de son utilisation dans votre organisation<a name="enable-app"></a>

Une fois que vous êtes prêt à activer l’application en vue de son utilisation dans l’environnement de production de votre organisation, procédez comme suit.

1. Dans Cloud App Security, cliquez sur l’icône Paramètres roue dentée ![ paramètres ](media/settings-icon.png) , puis sélectionnez **contrôle d’application par accès conditionnel**.
1. Dans la liste des applications, sur la ligne dans laquelle l’application que vous déployez s’affiche, choisissez les trois points à la fin de la ligne, puis choisissez **modifier l’application**.
1. Sélectionnez **utiliser avec contrôle d’application par accès conditionnel** , puis cliquez sur **Enregistrer**.

    ![Activer le menu contextuel des contrôles de session](media/edit-app-enable-session-controls.png)

## <a name="step-6-update-the-azure-ad-policy-azure-ad-only"></a>Étape 6 : mettre à jour la stratégie de Azure AD (Azure AD uniquement)<a name="update-azure-ad"></a>

1. Dans Azure AD, sous **sécurité**, cliquez sur **accès conditionnel**.
1. Mettez à jour la stratégie que vous avez créée précédemment pour inclure les utilisateurs, les groupes et les contrôles appropriés dont vous avez besoin.
1. Sous **session**  >  **utiliser contrôle d’application par accès conditionnel**, si vous avez sélectionné **utiliser une stratégie personnalisée**, accédez à Cloud App Security et créez une stratégie de session correspondante. Pour plus d’informations, consultez [Stratégies de session](session-policy-aad.md).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [«PRÉCÉDENT : déployer contrôle d’application par accès conditionnel pour les applications proposées](proxy-deployment-aad.md)

> [!div class="nextstepaction"]
> [Étape suivante : comment créer une stratégie de session»](session-policy-aad.md)

## <a name="see-also"></a>Voir aussi

> [!div class="nextstepaction"]
> [Présentation de contrôle d’application par accès conditionnel](proxy-intro-aad.md)

> [!div class="nextstepaction"]
> [Résolution des problèmes de contrôles d’accès et de session](troubleshooting-proxy.md)

[!INCLUDE [Open support ticket](includes/support.md)]