---
title: Déployer le contrôle d’application par accès conditionnel Cloud App Security pour les applications Azure AD
description: Cet article fournit des informations sur le déploiement du proxy inversé du Contrôle d’application par accès conditionnel Microsoft Cloud App Security pour les applications Azure AD.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 9/23/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 14209e0b394571ee0d71784cb4c50683226a7a2e
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74460621"
---
# <a name="deploy-conditional-access-app-control-for-featured-apps"></a>Déployer le contrôle d’application par accès conditionnel pour les applications à la une

*S’applique à : Microsoft Cloud App Security*

>[!div class="step-by-step"]
[« Précédent : Introduction au Contrôle d’accès conditionnel aux applications](proxy-intro-aad.md)<br>
[Next: Onboard and deploy Conditional Access App Control for any app »](proxy-deployment-any-app.md)

Session controls in Microsoft Cloud App Security work with the featured apps. For a list of apps that are featured by Cloud App Security to work out-of-the-box, see [Protect apps with Microsoft Cloud App Security Conditional Access App Control](proxy-intro-aad.md#featured-apps).

## <a name="prerequisites"></a>Conditions préalables

Pour déployer le contrôle d’application par accès conditionnel pour des applications Azure AD, vous avez besoin d’une [licence valide pour Azure AD Premium P1](https://docs.microsoft.com/azure/active-directory/license-users-groups), ainsi que d’une licence Cloud App Security.

## <a name="to-deploy-featured-apps"></a>To deploy featured apps

Follow these steps to configure featured apps to be controlled by Microsoft Cloud App Security Conditional Access App Control.

**Step 1: [Go to the Azure AD portal and create a conditional access policy for the apps and route the session to Cloud App Security](#add-azure-ad)**

**Step 2: [Sign in to each app using a user scoped to the policy](#sign-in-scoped)**

**Step 3: [Verify the apps are configured to use access and session controls](#portal)**

**Step 4: [Test the deployment](#test)**

## Step 1: Create an Azure AD conditional access test policy <a name="add-azure-ad"></a>

1. In Azure Active Directory, under **Security**, click **Conditional Access**.

1. Cliquez sur **Nouvelle stratégie** et créez une stratégie.

1. Dans la stratégie TEST, sous **Utilisateurs**, attribuez un utilisateur de test ou un utilisateur pouvant servir à une ouverture de session initiale et à la vérification.

1. Dans la stratégie TEST, sous **Application cloud**, assignez les applications que vous voulez contrôler avec le Contrôle d'application par accès conditionnel.

1. Sous **Session**, définissez la stratégie pour qu’elle utilise l’une des stratégies intégrées, **Surveiller uniquement** ou **Bloquer les téléchargements**. Ou sélectionnez **Utiliser stratégie personnalisée** pour définir une stratégie avancée dans le portail Cloud App Security.

1. Ajoutez des **Conditions d’affectation** ou des **Contrôles d’octroi** (facultatif).

   ![Accès conditionnel Azure AD](./media/azure-ad-caac-policy.png)

1. Click **Enable** and **Save**.

## Step 2: Sign in to each app using a user scoped to the policy<a name="sign-in-scoped"></a>

> [!NOTE]
> Before proceeding, make sure to first sign out of existing sessions.

Une fois que vous avez créé la stratégie, connectez-vous à chaque application configurée dans cette stratégie. Veillez à vous connecter à l’aide d’un utilisateur configuré dans la stratégie.

Cloud App Security will sync your policy details to its servers for each new app you sign in to. Cette opération peut prendre jusqu’à une minute.

## Step 3: Verify the apps are configured to use access and session controls<a name="portal"></a>

Les instructions ci-dessus vous ont aidé à créer une stratégie Cloud App Security intégrée pour les applications proposées directement dans Azure AD. In this step, verify that the access and session controls are configured for these apps.

1. In the Cloud App Security portal, click the settings cog ![settings icon](./media/settings-icon.png "icône des paramètres"), and then select **Conditional Access App Control**.

1. In the Conditional Access App Control apps table, look at the **Available controls** column and verify that both **Access control** and **Session control** appear for your apps.

   > [!NOTE]
   > If session control doesn't appear for an app, it's not yet available for that specific app. You can either add it immediately as a [custom app](proxy-deployment-any-app.md), or you can open a request to add it as a featured app by clicking **Request session control**.
    >
    >![Demande du Contrôle d’application par accès conditionnel](media/caac-request.png)

## Step 4: Test the deployment<a name="test"></a>

1. Tout d’abord, déconnectez-vous de toutes les sessions existantes. Ensuite, essayez de vous connecter à chaque application qui a été déployée avec succès. Connectez-vous sous un utilisateur qui correspond à la stratégie configurée dans Azure AD.

1. Dans le portail Cloud App Security, sous **Examiner**, sélectionnez **Journal d’activité** et vérifiez que les activités de connexion sont capturées pour chaque application.

1. Vous pouvez filtrer en cliquant sur **Avancé**, puis en filtrant avec **Source est égale à Contrôle d’accès**.

    ![Filtrer à l’aide de l’accès conditionnel Azure AD](./media/sso-logon.png)

1. Nous vous recommandons de vous connecter aux applications mobiles et de bureau à partir d’appareils gérés et non gérés, afin de vous assurer que les activités sont correctement capturées dans le journal d’activité.<br>
Pour vérifier que les activités sont correctement capturées, cliquez sur une activité de connexion avec authentification unique afin d’ouvrir le tiroir Activité. Vérifiez que l’**Étiquette agent utilisateur** indique correctement si l’appareil est un client natif (à savoir, une application mobile ou de bureau) ou un appareil géré (conforme, joint à un domaine ou avec certificat client valide).

> [!NOTE]
> Après son déploiement, vous ne pouvez pas supprimer une application à partir de la page Contrôle d’application par accès conditionnel. Tant que vous ne définissez pas une stratégie d’accès ou de session sur l’application, le contrôle d’application par accès conditionnel ne change pas le comportement de l’application.

>[!div class="step-by-step"]
[« Précédent : Introduction au Contrôle d’accès conditionnel aux applications](proxy-intro-aad.md)<br>[Next: Onboard and deploy Conditional Access App Control for any app »](proxy-deployment-any-app.md)

## <a name="next-steps"></a>Étapes suivantes

[Working with Cloud App Security Conditional Access App Control](proxy-intro-aad.md)

[!INCLUDE [Open support ticket](includes/support.md)]
