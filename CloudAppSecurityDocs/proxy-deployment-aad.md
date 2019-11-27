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
[Étape suivante : intégration et déploiement de contrôle d’application par accès conditionnel pour une application»](proxy-deployment-any-app.md)

Les contrôles de session dans Microsoft Cloud App Security fonctionner avec les applications proposées. Pour obtenir la liste des applications qui sont proposées par Cloud App Security pour un travail prêt à l’emploi, consultez [protéger les applications avec Microsoft Cloud App Security contrôle d’application par accès conditionnel](proxy-intro-aad.md#featured-apps).

## <a name="prerequisites"></a>Conditions préalables requises

Pour déployer le contrôle d’application par accès conditionnel pour des applications Azure AD, vous avez besoin d’une [licence valide pour Azure AD Premium P1](https://docs.microsoft.com/azure/active-directory/license-users-groups), ainsi que d’une licence Cloud App Security.

## <a name="to-deploy-featured-apps"></a>Pour déployer des applications proposées

Procédez comme suit pour configurer les applications proposées pour qu’elles soient contrôlées par Microsoft Cloud App Security contrôle d’application par accès conditionnel.

**Étape 1 : [accéder au portail Azure ad et créer une stratégie d’accès conditionnel pour les applications et Router la session vers Cloud App Security](#add-azure-ad)**

**Étape 2 : [se connecter à chaque application à l’aide d’un utilisateur dont l’étendue est limitée à la stratégie](#sign-in-scoped)**

**Étape 3 : [vérifier que les applications sont configurées pour utiliser les contrôles d’accès et de session](#portal)**

**Étape 4 : [tester le déploiement](#test)**

## Étape 1 : créer une stratégie de test d’accès conditionnel Azure AD<a name="add-azure-ad"></a>

1. Dans Azure Active Directory, sous **sécurité**, cliquez sur **accès conditionnel**.

1. Cliquez sur **Nouvelle stratégie** et créez une stratégie.

1. Dans la stratégie TEST, sous **Utilisateurs**, attribuez un utilisateur de test ou un utilisateur pouvant servir à une ouverture de session initiale et à la vérification.

1. Dans la stratégie TEST, sous **Application cloud**, assignez les applications que vous voulez contrôler avec le Contrôle d’accès conditionnel aux applications.

1. Sous **Session**, définissez la stratégie pour qu’elle utilise l’une des stratégies intégrées, **Surveiller uniquement** ou **Bloquer les téléchargements**. Ou sélectionnez **Utiliser stratégie personnalisée** pour définir une stratégie avancée dans le portail Cloud App Security.

1. Ajoutez des **Conditions d’affectation** ou des **Contrôles d’octroi** (facultatif).

   ![Accès conditionnel Azure AD](./media/azure-ad-caac-policy.png)

1. Cliquez sur **activer** et **Enregistrer**.

## Étape 2 : se connecter à chaque application à l’aide d’un utilisateur dont l’étendue est limitée à la stratégie<a name="sign-in-scoped"></a>

> [!NOTE]
> Avant de continuer, veillez à vous déconnecter des sessions existantes.

Une fois que vous avez créé la stratégie, connectez-vous à chaque application configurée dans cette stratégie. Veillez à vous connecter à l’aide d’un utilisateur configuré dans la stratégie.

Cloud App Security synchronisera vos détails de stratégie sur ses serveurs pour chaque nouvelle application à laquelle vous vous connectez. Cette opération peut prendre jusqu’à une minute.

## Étape 3 : vérifier que les applications sont configurées pour utiliser les contrôles d’accès et de session<a name="portal"></a>

Les instructions ci-dessus vous ont aidé à créer une stratégie Cloud App Security intégrée pour les applications proposées directement dans Azure AD. Dans cette étape, vérifiez que les contrôles d’accès et de session sont configurés pour ces applications.

1. Dans le portail Cloud App Security, cliquez sur l’icône Paramètres roue dentée ![paramètres](./media/settings-icon.png "icône des paramètres"), puis sélectionnez **contrôle d’application par accès conditionnel**.

1. Dans le tableau contrôle d’application par accès conditionnel Apps, examinez la colonne **contrôles disponibles** et vérifiez que le contrôle d' **accès** et **le contrôle de session** apparaissent pour vos applications.

   > [!NOTE]
   > Si le contrôle de session n’apparaît pas pour une application, il n’est pas encore disponible pour cette application spécifique. Vous pouvez l’ajouter immédiatement en tant qu' [application personnalisée](proxy-deployment-any-app.md), ou vous pouvez ouvrir une demande pour l’ajouter en tant qu’application proposée en cliquant sur **demander un contrôle de session**.
    >
    >![Demande du Contrôle d’application par accès conditionnel](media/caac-request.png)

## Étape 4 : tester le déploiement<a name="test"></a>

1. Tout d’abord, déconnectez-vous de toutes les sessions existantes. Ensuite, essayez de vous connecter à chaque application qui a été déployée avec succès. Connectez-vous sous un utilisateur qui correspond à la stratégie configurée dans Azure AD.

1. Dans le portail Cloud App Security, sous **Examiner**, sélectionnez **Journal d’activité** et vérifiez que les activités de connexion sont capturées pour chaque application.

1. Vous pouvez filtrer en cliquant sur **Avancé**, puis en filtrant avec **Source est égale à Contrôle d’accès**.

    ![Filtrer à l’aide de l’accès conditionnel Azure AD](./media/sso-logon.png)

1. Nous vous recommandons de vous connecter aux applications mobiles et de bureau à partir d’appareils gérés et non gérés, afin de vous assurer que les activités sont correctement capturées dans le journal d’activité.<br>
Pour vérifier que les activités sont correctement capturées, cliquez sur une activité de connexion avec authentification unique afin d’ouvrir le tiroir Activité. Vérifiez que l’**Étiquette agent utilisateur** indique correctement si l’appareil est un client natif (à savoir, une application mobile ou de bureau) ou un appareil géré (conforme, joint à un domaine ou avec certificat client valide).

> [!NOTE]
> Après son déploiement, vous ne pouvez pas supprimer une application à partir de la page Contrôle d’application par accès conditionnel. Tant que vous ne définissez pas une stratégie d’accès ou de session sur l’application, le contrôle d’application par accès conditionnel ne change pas le comportement de l’application.

>[!div class="step-by-step"]
[« Précédent : Introduction au Contrôle d’accès conditionnel aux applications](proxy-intro-aad.md)<br>[Étape suivante : intégration et déploiement de contrôle d’application par accès conditionnel pour une application»](proxy-deployment-any-app.md)

## <a name="next-steps"></a>Étapes suivantes

[Utilisation de Cloud App Security contrôle d’application par accès conditionnel](proxy-intro-aad.md)

[!INCLUDE [Open support ticket](includes/support.md)]
