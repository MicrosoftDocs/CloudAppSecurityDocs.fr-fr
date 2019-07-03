---
title: Déployer le contrôle l’accès conditionnel Cloud App Security pour les applications
description: Cet article fournit des informations sur la façon de déployer les fonctionnalités de proxy inverse de Microsoft Cloud App Security contrôle d’accès conditionnel pour les applications.
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: ShlomoSagir-MS
ms.date: 7/2/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.suite: ems
ms.openlocfilehash: 6d96e788c741de31242a075bf65f80344d0c54ed
ms.sourcegitcommit: ee00e0033bf45a5f795bfd3e1d71fa1f70f97acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67515070"
---
# <a name="onboard-and-deploy-conditional-access-app-control-for-any-app"></a>Intégrer et déployer le contrôle d’accès conditionnel pour n’importe quelle application

*S’applique à : Microsoft Cloud App Security*

>[!div class="step-by-step"]
[« Précédent : Introduction au contrôle d’application par accès conditionnel](proxy-intro-aad.md)<br>
[Suivant : Guide pratique pour créer une stratégie de session »](session-policy-aad.md)

Contrôles de session dans Microsoft Cloud App Security peuvent être configurés pour fonctionner avec toutes les applications web. Cet article décrit comment intégrer et déployer des applications line of business personnalisées, non complet des applications SaaS et hébergées par le biais du Proxy d’Application Azure AD avec les contrôles de Session des applications sur site.

Pour obtenir la liste des applications qui sont disponibles par Cloud App Security fonctionne out-of-the-box, consultez [protéger des applications avec Microsoft Cloud App Security contrôle d’accès conditionnel](proxy-intro-aad.md).

## <a name="prerequisites"></a>Prérequis

- Votre organisation doit disposer des licences suivantes à utiliser le contrôle d’accès conditionnel :

  - Édition Azure Active Directory Premium
  - Sécurité des applications de cloud

- Les applications doivent être configurées avec l’authentification unique dans Azure AD
- Les applications doivent utiliser les protocoles SAML ou Open ID connexion 2.0

## <a name="to-deploy-a-any-app"></a>Pour déployer une n’importe quelle application

Suivez ces étapes pour configurer n’importe quelle application pour être contrôlé par Cloud App Security contrôle d’accès conditionnel.

**Étape 1 : [Configurer la fonctionnalité de stratégie d’accès conditionnel d’Azure Active Directory pour acheminer les applications appropriées à Cloud App Security](#conf-azure-ad).**

**Étape 2 : [Configurer les utilisateurs qui déploiement l’application](#conf-users).**

**Étape 3 : [Configurer l’application que vous déployez](#conf-app)**

**Étape 4 : [Vérifiez que l’application fonctionne correctement](#verify-app)**

**Étape 5 : [Permettre à l’application pour une utilisation dans votre organisation](#enable-app)**

**Étape 6 : [Mise à jour la stratégie Azure AD](#update-azure-ad)**

> [!NOTE]
> Pour déployer le contrôle d’application par accès conditionnel pour des applications Azure AD, vous avez besoin d’une [licence valide pour Azure AD Premium P1](https://docs.microsoft.com/azure/active-directory/license-users-groups), ainsi que d’une licence Cloud App Security.

## Étape 1 : Configurer la fonctionnalité de stratégie d’accès conditionnel d’Azure Active Directory pour acheminer les applications appropriées à Cloud App Security<a name="conf-azure-ad"></a>  

1. Dans Azure Active Directory, sous **sécurité**, cliquez sur **accès conditionnel**.

1. Sur le **accès conditionnel** page, dans la barre d’outils en haut, cliquez sur **nouvelle stratégie**.

1. Sur le **New** page, dans le **nom** zone de texte, tapez **TEST**.

1. Sur le **utilisateurs et groupes** page, affectez les utilisateurs de test pertinentes qui seront l’intégration les applications.

1. Sur le **applications Cloud** page, affecter les applications souhaitées au contrôle avec le contrôle d’accès conditionnel.

1. Sous **Session**, sélectionnez **contrôle d’accès conditionnel utilisation** , puis sélectionnez **surveiller uniquement**.

   ![Accès conditionnel Azure AD](./media/azure-ad-caac-policy.png)

1. Cliquez sur **activer** et **enregistrer**.

## Étape 2 : Configurer les utilisateurs qui déploiement l’application<a name="conf-users"></a>

1. Dans Cloud App Security, dans la barre de menus, cliquez sur la roue dentée des paramètres ![icône des paramètres](./media/settings-icon.png "icône des paramètres") et sélectionnez **paramètres**.

1. Sous **contrôle d’accès conditionnel**, sélectionnez **d’intégration d’application/maintenance**.

1. Entrez le nom d’utilisateur principal ou par e-mail pour les utilisateurs qui seront l’intégration de l’application, puis cliquez sur **enregistrer**.

    ![Capture d’écran de paramètres pour l’intégration d’application et la maintenance.](media/app-onboarding-settings.png)

## Étape 3 : Configurer l’application que vous déployez<a name="conf-app"></a>

1. Accédez à l’application que vous déployez. Si votre domaine d’application est reconnu, vous devrez continuer le processus de configuration d’application. Si votre domaine d’application n’est pas reconnu, vous devrez configurer les domaines de votre application. Cliquez sur **configurer application** pour continuer le processus de configuration.

    > [!NOTE]
    > Pour les domaines d’application reconnue, assurez-vous que l’application est configurée avec tous les domaines requis pour l’application de fonctionner correctement.

1. Répétez les étapes suivantes pour installer le **autorité de certification actuel** et **autorité de certification suivant** les certificats racine auto-signés.
    1. Sélectionnez le certificat.
    1. Cliquez sur **Open**, puis à l’invite cliquez sur **Open** à nouveau.
    1. Cliquez sur **installer le certificat**.
    1. Choisissez **utilisateur actuel** ou **ordinateur Local**.
    1. Sélectionnez **placer tous les certificats dans le magasin suivant** puis cliquez sur **Parcourir**.
    1. Sélectionnez **autorités de certification racine de confiance** puis cliquez sur **OK**.
    1. Cliquez sur **Terminer**.

    > [!NOTE]
    > Pour les certificats d’être reconnue, une fois que vous avez installé le certificat, vous devez redémarrer le navigateur et accédez à la même page. Vous verrez une coche par la confirmation des liens de certificats qu’ils sont installés.

1. Cliquez sur **Continue** (Continuer).

## Étape 4 : Vérifiez que l’application fonctionne correctement<a name="verify-app"></a>

1. Vérifiez que le flux de connexion fonctionne correctement.
    > [!NOTE]
    > Certaines applications émettre un hachage nonce lors de l’authentification qui peut-être arrêter le processus de connexion. Si cela se produit, consultez le Guide de dépannage pour résoudre le problème.
1. Une fois que vous êtes dans l’application, effectuez les vérifications suivantes :
    1. Visitez toutes les pages au sein de l’application qui font partie du processus de travail d’un utilisateur et vérifier que les pages s’affichent correctement.
    1. Vérifiez que le comportement et les fonctionnalités de l’application ne soient pas affectées en effectuant des actions courantes telles que le téléchargement de fichiers.

## Étape 5 : Permettre à l’application pour une utilisation dans votre organisation<a name="enable-app"></a>

Une fois que vous êtes prêt à activer l’application à utiliser dans votre environnement de production, procédez comme suit.

1. Dans Cloud App Security, dans la barre de menus, cliquez sur la roue dentée des paramètres ![icône des paramètres](./media/settings-icon.png "icône des paramètres") et sélectionnez **contrôle d’accès conditionnel**.
1. Dans la liste des applications, sur la ligne dans laquelle l’application que vous déployez s’affiche, choisissez les points de suspension à la fin de la ligne, puis **modifier application**.
1. Sélectionnez **utiliser avec le contrôle d’accès conditionnel** puis cliquez sur **enregistrer**.

## Étape 6 : Mise à jour la stratégie Azure AD<a name="update-azure-ad"></a>

1. Dans Azure Active Directory, sous **sécurité**, cliquez sur **accès conditionnel**.
1. Mettre à jour de la stratégie que vous avez créé dans [étape 1](#conf-azure-ad) pour inclure les utilisateurs concernés, des groupes et des contrôles que vous avez besoin.
1. Sous **Session** > **contrôle d’accès conditionnel utilisation**, si vous avez sélectionné **utiliser une stratégie personnalisée**, accédez à Cloud App Security et créer un correspondant stratégie de session. Pour plus d’informations, consultez [Stratégies de session](session-policy-aad.md).

>[!div class="step-by-step"]
[« Précédent : Déployer le contrôle d’accès conditionnel aux applications Azure AD](proxy-deployment-aad.md)<br>
[Suivant : Guide pratique pour créer une stratégie de session »](session-policy-aad.md)

## <a name="next-steps"></a>Étapes suivantes 
[Utilisation avec le Contrôle d’accès conditionnel aux applications de Cloud App Security](proxy-intro-aad.md)

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)