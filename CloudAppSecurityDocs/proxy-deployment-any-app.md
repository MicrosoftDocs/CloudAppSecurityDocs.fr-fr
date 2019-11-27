---
title: Déployer des contrôle d’application par accès conditionnel Cloud App Security pour toutes les applications
description: Cet article fournit des informations sur le déploiement de la Microsoft Cloud App Security contrôle d’application par accès conditionnel les fonctionnalités de proxy inverse pour toutes les applications.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 9/23/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.suite: ems
ms.openlocfilehash: f6de75de67bc81b1f12da30cc7a54a6d6b95b324
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74460612"
---
# <a name="onboard-and-deploy-conditional-access-app-control-for-any-app"></a>Intégration et déploiement de contrôle d’application par accès conditionnel pour n’importe quelle application

*S’applique à : Microsoft Cloud App Security*

>[!div class="step-by-step"]
[«Précédent : déployer contrôle d’application par accès conditionnel pour les applications proposées](proxy-deployment-aad.md)<br>
[Suivant : Guide pratique pour créer une stratégie de session »](session-policy-aad.md)

Les contrôles de session dans Microsoft Cloud App Security peuvent être configurés pour fonctionner avec n’importe quelle application Web. Cet article explique comment intégrer et déployer des applications métier personnalisées, des applications SaaS non proposées et des applications locales hébergées via le proxy d’application Azure Active Directory (Azure AD) avec des contrôles de session.

Pour obtenir la liste des applications qui sont proposées par Cloud App Security pour un travail prêt à l’emploi, consultez [protéger les applications avec Microsoft Cloud App Security contrôle d’application par accès conditionnel](proxy-intro-aad.md#featured-apps).

## <a name="prerequisites"></a>Conditions préalables requises

- Votre organisation doit disposer des licences suivantes pour utiliser contrôle d’application par accès conditionnel :

  - Azure Active Directory Premium P1 ou version ultérieure
  - Microsoft Cloud App Security

- Les applications doivent être configurées avec l’authentification unique dans Azure AD
- Les applications doivent utiliser des protocoles SAML ou Open ID Connect 2,0

## <a name="to-deploy-any-app"></a>Pour déployer une application

Procédez comme suit pour configurer une application devant être contrôlée par Cloud App Security contrôle d’application par accès conditionnel.

**Étape 1 : [configurer Azure ad stratégie d’accès conditionnel pour acheminer les applications pertinentes vers Cloud App Security](#conf-azure-ad)**

**Étape 2 : [configurer les utilisateurs qui déploieront l’application](#conf-users)**

**Étape 3 : [configurer l’application que vous déployez](#conf-app)**

**Étape 4 : [vérifier que l’application fonctionne correctement](#verify-app)**

**Étape 5 : [activer l’application en vue de son utilisation dans votre organisation](#enable-app)**

**Étape 6 : [mettre à jour la stratégie de Azure ad](#update-azure-ad)**

> [!NOTE]
> Pour déployer contrôle d’application par accès conditionnel pour les applications Azure AD, vous avez besoin d’une [licence valide pour Azure Active Directory Premium P1 ou version ultérieure](https://docs.microsoft.com/azure/active-directory/license-users-groups) , ainsi qu’une licence Cloud App Security.

## Étape 1 : configurer Azure AD stratégie d’accès conditionnel pour acheminer les applications pertinentes vers Cloud App Security<a name="conf-azure-ad"></a>  

1. Dans Azure AD, navigateur à **sécurité** > **accès conditionnel**.

1. Dans le panneau **accès conditionnel** , dans la barre d’outils située en haut, cliquez sur **nouvelle stratégie**.

1. Dans le panneau **nouveau** , dans la zone de texte **nom** , entrez le nom de la stratégie.

1. Sous **affectations**, cliquez sur **utilisateurs et groupes**, affectez à l’application les utilisateurs qui seront intégrés (authentification initiale et vérification), puis cliquez sur **terminé**.

1. Sous **affectations**, cliquez sur **applications Cloud**, affectez les applications que vous souhaitez contrôler avec contrôle d’application par accès conditionnel, puis cliquez sur **terminé**.

1. Sous **contrôles d’accès**, cliquez sur **session**, sélectionnez **utiliser contrôle d’application par accès conditionnel** et choisissez des stratégies intégrées (**surveiller uniquement** ou **bloquer les téléchargements**) ou **Utilisez une stratégie personnalisée** pour définir une stratégie avancée dans Cloud App Security, puis cliquez sur **Sélectionner**.

   ![Accès conditionnel Azure AD](./media/azure-ad-caac-policy.png)

1. Facultatif : ajoutez des conditions et accordez des contrôles en fonction des besoins.

1. Affectez à **activer la stratégie** la valeur **activé** , puis cliquez sur **créer**.

## Étape 2 : configurer les utilisateurs qui déploieront l’application<a name="conf-users"></a>

1. Dans Cloud App Security, dans la barre de menus, cliquez sur l' ![icône](./media/settings-icon.png "icône des paramètres") paramètres roue dentée paramètres, puis sélectionnez **paramètres**.

1. Sous **contrôle d’application par accès conditionnel**, sélectionnez **intégration/maintenance**de l’application.

1. Entrez le nom d’utilisateur principal ou l’adresse de messagerie des utilisateurs qui intégreront l’application, puis cliquez sur **Enregistrer**.

    ![Capture d’écran des paramètres d’intégration et de maintenance des applications.](media/app-onboarding-settings.png)

## Étape 3 : configurer l’application que vous déployez<a name="conf-app"></a>

Accédez à l’application que vous déployez. La page que vous voyez varie selon que l’application est reconnue ou non. Effectuez l’une des opérations suivantes :

| État de l’application | Description | Étapes |
| --- | --- | --- |
| Non reconnu | Une page application non reconnue s’affiche et vous invite à configurer votre application. | 1. [Ajoutez l’application à contrôle d’application par accès conditionnel](#add-app).<br> 2. [Ajoutez les domaines pour l’application](#add-domains), puis revenez à l’application et actualisez la page.<br> 3. [Installez les certificats pour l’application](#install-certs). |
| Reconnu | Une page d’intégration s’affiche pour vous inviter à poursuivre le processus de configuration de l’application. | - [installer les certificats pour l’application](#install-certs). <br><br> **Remarque :** Assurez-vous que l’application est configurée avec tous les domaines requis pour que l’application fonctionne correctement. Pour configurer des domaines supplémentaires, continuez à [Ajouter les domaines pour l’application](#add-domains), puis revenez à la page de l’application. |

### Pour ajouter une nouvelle application<a name="add-app"></a>

1. Dans la barre de menus, cliquez sur l' ![icône](./media/settings-icon.png "icône des paramètres")paramètres roue dentée paramètres, puis sélectionnez **contrôle d’application par accès conditionnel**.

1. Cliquez sur **Afficher les nouvelles applications**.

    ![Afficher les nouvelles applications du Contrôle d’application par accès conditionnel](media/caac-view-apps.png)

1. Dans l’écran qui s’ouvre, vous pouvez voir une liste de nouvelles applications. Pour chaque application que vous intégrez, cliquez sur le signe **+** , puis cliquez sur **Ajouter**.

   > [!NOTE]
   > Si une application n’apparaît pas dans le catalogue d’applications Cloud App Security, elle figure, dans la boîte de dialogue, sous les applications non identifiées, avec son URL de connexion. Lorsque vous cliquez sur le signe + pour ces applications, vous pouvez intégrer l’application en tant qu’application personnalisée.

    ![Applications Azure AD découvertes du Contrôle d’application par accès conditionnel](media/caac-discovered-aad-apps.png)

### Pour ajouter des domaines pour une application<a name="add-domains"></a>

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
1. Accédez à Cloud App Security, dans la barre de menus, cliquez sur l' ![icône](./media/settings-icon.png "icône des paramètres") paramètres roue dentée paramètres, puis sélectionnez **contrôle d’application par accès conditionnel**.
1. Dans la liste des applications, sur la ligne dans laquelle l’application que vous déployez s’affiche, choisissez les trois points à la fin de la ligne, puis sous **Détails**de l’application, choisissez **modifier**.
    > [!TIP]
    > Pour afficher la liste des domaines configurés dans l’application, cliquez sur **afficher les domaines d’application**.
1. Dans **domaines définis par l’utilisateur**, entrez tous les domaines que vous souhaitez associer à cette application, puis cliquez sur **Enregistrer**.
    > [!NOTE]
    > Vous pouvez utiliser le caractère générique * en tant qu’espace réservé pour n’importe quel caractère. Lorsque vous ajoutez des domaines, déterminez si vous souhaitez ajouter des domaines spécifiques (`sub1.contoso.com`,`sub2.contoso.com`) ou plusieurs domaines (`*.contoso.com`).

### Pour installer des certificats racines<a name="install-certs"></a>

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

## Étape 4 : vérifier que l’application fonctionne correctement<a name="verify-app"></a>

1. Vérifiez que le processus de connexion fonctionne correctement.
    <!--
    > [!NOTE]
    > Some apps issue a nonce hash during authentication that may break the sign-in process. If this happens, see the Troubleshooting Guide to resolve the issue.-->
1. Une fois que vous êtes dans l’application, effectuez les vérifications suivantes :
    1. Accédez à toutes les pages de l’application qui font partie du processus de travail des utilisateurs et vérifiez que les pages s’affichent correctement.
    1. Vérifiez que le comportement et les fonctionnalités de l’application ne sont pas affectés par l’exécution d’actions courantes telles que le téléchargement et le chargement de fichiers.
    1. Passez en revue la liste des domaines associés à l’application. Pour plus d’informations, consultez [Ajouter les domaines pour l’application](#add-domains).

## Étape 5 : activer l’application en vue de son utilisation dans votre organisation<a name="enable-app"></a>

Une fois que vous êtes prêt à activer l’application en vue de son utilisation dans l’environnement de production de votre organisation, procédez comme suit.

1. Dans Cloud App Security, cliquez sur l’icône Paramètres roue dentée ![paramètres](./media/settings-icon.png "icône des paramètres"), puis sélectionnez **contrôle d’application par accès conditionnel**.
1. Dans la liste des applications, sur la ligne dans laquelle l’application que vous déployez s’affiche, choisissez les trois points à la fin de la ligne, puis choisissez **modifier l’application**.
1. Sélectionnez **utiliser avec contrôle d’application par accès conditionnel** , puis cliquez sur **Enregistrer**.

## Étape 6 : mettre à jour la stratégie de Azure AD<a name="update-azure-ad"></a>

1. Dans Azure AD, sous **sécurité**, cliquez sur **accès conditionnel**.
1. Mettez à jour la stratégie que vous avez créée précédemment pour inclure les utilisateurs, les groupes et les contrôles appropriés dont vous avez besoin.
1. Sous **Session** > **utiliser contrôle d’application par accès conditionnel**, si vous avez sélectionné **utiliser une stratégie personnalisée**, accédez à Cloud App Security et créez une stratégie de session correspondante. Pour plus d’informations, consultez [Stratégies de session](session-policy-aad.md).

>[!div class="step-by-step"]
[«Précédent : déployer contrôle d’application par accès conditionnel pour les applications proposées](proxy-deployment-aad.md)<br>
[Suivant : Guide pratique pour créer une stratégie de session »](session-policy-aad.md)

## <a name="next-steps"></a>Étapes suivantes

[Utilisation avec le Contrôle d’accès conditionnel aux applications de Cloud App Security](proxy-intro-aad.md)

[!INCLUDE [Open support ticket](includes/support.md)]
