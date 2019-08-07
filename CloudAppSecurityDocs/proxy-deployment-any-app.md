---
title: Déployer des contrôle d’application par accès conditionnel Cloud App Security pour toutes les applications
description: Cet article fournit des informations sur le déploiement de la Microsoft Cloud App Security contrôle d’application par accès conditionnel les fonctionnalités de proxy inverse pour toutes les applications.
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: ShlomoSagir-MS
ms.date: 7/18/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.suite: ems
ms.openlocfilehash: 7b86bc5f344f097c4c4e45c9d25123c5b361ebb2
ms.sourcegitcommit: e9c93f69f280a929b2802619d24f59ea830b783f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68782878"
---
# <a name="onboard-and-deploy-conditional-access-app-control-for-any-app"></a>Intégration et déploiement de contrôle d’application par accès conditionnel pour n’importe quelle application

*S’applique à : Microsoft Cloud App Security*

>[!div class="step-by-step"]
[« Précédent : Déployer des contrôle d’application par accès conditionnel pour les applications proposées](proxy-deployment-aad.md)<br>
[Suivant : Guide pratique pour créer une stratégie de session »](session-policy-aad.md)

Les contrôles de session dans Microsoft Cloud App Security peuvent être configurés pour fonctionner avec n’importe quelle application Web. Cet article explique comment intégrer et déployer des applications métier personnalisées, des applications SaaS non proposées et des applications locales hébergées via le proxy d’application Azure Active Directory (Azure AD) avec des contrôles de session.

Pour obtenir la liste des applications qui sont proposées par Cloud App Security pour un travail prêt à l’emploi, consultez [protéger les applications avec Microsoft Cloud App Security contrôle d’application par accès conditionnel](proxy-intro-aad.md).

## <a name="prerequisites"></a>Prérequis

- Votre organisation doit disposer des licences suivantes pour utiliser contrôle d’application par accès conditionnel:

  - Azure Active Directory Premium P1 ou version ultérieure
  - Microsoft Cloud App Security

- Les applications doivent être configurées avec l’authentification unique dans Azure AD
- Les applications doivent utiliser des protocoles SAML ou Open ID Connect 2,0

## <a name="to-deploy-any-app"></a>Pour déployer une application

Procédez comme suit pour configurer une application devant être contrôlée par Cloud App Security contrôle d’application par accès conditionnel.

**Étape 1 : [Configurez Azure AD stratégie d’accès conditionnel pour acheminer les applications pertinentes vers Cloud App Security](#conf-azure-ad)**

**Étape 2 : [Configurer les utilisateurs qui déploieront l’application](#conf-users)**

**Étape 3 : [Configuration de l’application que vous déployez](#conf-app)**

**Étape 4 : [Ajouter les domaines pour l’application](#add-domains)**

**Étape 5 : [Vérifier que l’application fonctionne correctement](#verify-app)**

**Étape 6 : [Activer l’application pour l’utiliser dans votre organisation](#enable-app)**

**Étape 7 : [Mettre à jour la stratégie de Azure AD](#update-azure-ad)**

> [!NOTE]
> Pour déployer contrôle d’application par accès conditionnel pour les applications Azure AD, vous avez besoin d’une [licence valide pour Azure Active Directory Premium P1 ou version ultérieure](https://docs.microsoft.com/azure/active-directory/license-users-groups) , ainsi qu’une licence Cloud App Security.

## Étape 1 : Configurez Azure AD stratégie d’accès conditionnel pour acheminer les applications pertinentes vers Cloud App Security<a name="conf-azure-ad"></a>  

1. Dans Azure ad, accédez au navigateur pour accéder à la **sécurité** > de**l’accès conditionnel**.

1. Dans le panneau **accès conditionnel** , dans la barre d’outils située en haut, cliquez sur **nouvelle stratégie**.

1. Dans le panneau **nouveau** , dans la zone de texte **nom** , entrez le nom de la stratégie.

1. Sous **affectations**, cliquez sur **utilisateurs et groupes**, affectez à l’application les utilisateurs qui seront intégrés (authentification initiale et vérification), puis cliquez sur **terminé**.

1. Sous **affectations**, cliquez sur **applications Cloud**, affectez les applications que vous souhaitez contrôler avec contrôle d’application par accès conditionnel, puis cliquez sur **terminé**.

1. Sous **contrôles d’accès**, cliquez sur **session**, sélectionnez **utiliser contrôle d’application par accès conditionnel** et choisissez des stratégies intégrées (**surveiller uniquement** ou **bloquer les téléchargements**) ou **utiliser une stratégie personnalisée** pour définir une stratégie avancée dans le Cloud Sécurité de l’application, puis cliquez sur **Sélectionner**.

   ![Accès conditionnel Azure AD](./media/azure-ad-caac-policy.png)

1. Facultatif : Ajoutez des conditions et accordez des contrôles en fonction des besoins.

1. Affectez à **activer la stratégie** la valeur **activé** , puis cliquez sur **créer**.

## Étape 2 : Configurer les utilisateurs qui déploieront l’application<a name="conf-users"></a>

1. Dans Cloud App Security, dans la barre de menus, cliquez sur l’icône Paramètres roue dentée icône paramètres ![icône](./media/settings-icon.png "paramètres") , puis sélectionnez **paramètres**.

1. Sous **contrôle d’application par accès conditionnel**, sélectionnez **intégration/maintenance**de l’application.

1. Entrez le nom d’utilisateur principal ou l’adresse de messagerie des utilisateurs qui intégreront l’application, puis cliquez sur **Enregistrer**.

    ![Capture d’écran des paramètres d’intégration et de maintenance des applications.](media/app-onboarding-settings.png)

## Étape 3 : Configuration de l’application que vous déployez<a name="conf-app"></a>

1. Accédez à l’application que vous déployez. Si votre domaine d’application est reconnu, vous êtes invité à poursuivre le processus de configuration de l’application. Si votre domaine d’application n’est pas reconnu, vous êtes invité à configurer le (s) domaine (s) de votre application. Cliquez sur **configurer l’application** et passez à [Ajouter les domaines pour l’application](#add-domains).

    > [!NOTE]
    > Pour les domaines d’application reconnus, assurez-vous que l’application est configurée avec tous les domaines requis pour que l’application fonctionne correctement. Pour configurer des domaines supplémentaires, continuez à [Ajouter les domaines pour l’application](#add-domains).

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

## Étape 4 : Ajouter les domaines pour l’application<a name="add-domains"></a>

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
1. Accédez à Cloud App Security, dans la barre de menus, cliquez sur l’icône Paramètres roue dentée icône paramètres ![icône](./media/settings-icon.png "paramètres") , puis sélectionnez **contrôle d’application par accès conditionnel**.
1. Dans la liste des applications, sur la ligne dans laquelle l’application que vous déployez s’affiche, choisissez les trois points à la fin de la ligne, puis sous **Détails**de l’application, choisissez **modifier**.
    > [!TIP]
    > Pour afficher la liste des domaines configurés dans l’application, cliquez sur **afficher les domaines d’application**.
1. Dans **domaines définis par l’utilisateur**, entrez tous les domaines que vous souhaitez associer à cette application, puis cliquez sur **Enregistrer**.
    > [!NOTE]
    > Vous pouvez utiliser le caractère générique * en tant qu’espace réservé pour n’importe quel caractère. Lorsque vous ajoutez des domaines, déterminez si vous souhaitez ajouter des`sub1.contoso.com`domaines`sub2.contoso.com`spécifiques (,) ou`*.contoso.com`plusieurs domaines ().

## Étape 5 : Vérifier que l’application fonctionne correctement<a name="verify-app"></a>

1. Vérifiez que le Flow de connexion fonctionne correctement.
    <!--
    > [!NOTE]
    > Some apps issue a nonce hash during authentication that may break the sign-in process. If this happens, see the Troubleshooting Guide to resolve the issue.-->
1. Une fois que vous êtes dans l’application, effectuez les vérifications suivantes:
    1. Accédez à toutes les pages de l’application qui font partie du processus de travail des utilisateurs et vérifiez que les pages s’affichent correctement.
    1. Vérifiez que le comportement et les fonctionnalités de l’application ne sont pas affectés par l’exécution d’actions courantes telles que le téléchargement et le chargement de fichiers.
    1. Passez en revue la liste des domaines associés à l’application. Pour plus d’informations, consultez [Ajouter les domaines pour l’application](#add-domains).

## Étape 6 : Activer l’application pour l’utiliser dans votre organisation<a name="enable-app"></a>

Une fois que vous êtes prêt à activer l’application en vue de son utilisation dans l’environnement de production de votre organisation, procédez comme suit.

1. Dans Cloud App Security, dans la barre de menus, cliquez sur l’icône Paramètres roue dentée icône paramètres ![icône](./media/settings-icon.png "paramètres") , puis sélectionnez **contrôle d’application par accès conditionnel**.
1. Dans la liste des applications, sur la ligne dans laquelle l’application que vous déployez s’affiche, choisissez les trois points à la fin de la ligne, puis choisissez **modifier l’application**.
1. Sélectionnez **utiliser avec contrôle d’application par accès conditionnel** , puis cliquez sur **Enregistrer**.

## Étape 7 : Mettre à jour la stratégie de Azure AD<a name="update-azure-ad"></a>

1. Dans Azure AD, sous **sécurité**, cliquez sur **accès conditionnel**.
1. Mettez à jour la stratégie que vous avez créée précédemment pour inclure les utilisateurs, les groupes et les contrôles appropriés dont vous avez besoin.
1. Sous **session** > **utiliser contrôle d’application par accès conditionnel**, si vous avez sélectionné **utiliser une stratégie personnalisée**, accédez à Cloud App Security et créez une stratégie de session correspondante. Pour plus d’informations, consultez [Stratégies de session](session-policy-aad.md).

>[!div class="step-by-step"]
[« Précédent : Déployer des contrôle d’application par accès conditionnel pour les applications proposées](proxy-deployment-aad.md)<br>
[Suivant : Guide pratique pour créer une stratégie de session »](session-policy-aad.md)

## <a name="next-steps"></a>Étapes suivantes 
[Utilisation avec le Contrôle d’accès conditionnel aux applications de Cloud App Security](proxy-intro-aad.md)

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)