---
title: Déployer des contrôle d’application par accès conditionnel Cloud App Security pour les applications Azure AD
description: Cet article fournit des informations sur le déploiement du Microsoft Cloud App Security contrôle d’application par accès conditionnel les fonctionnalités du proxy inverse pour les applications Azure AD.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 9/23/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 0fc3f43aa76f64d1228a6e45d2fdc743a494a8e3
ms.sourcegitcommit: 3f6ef6b97a0953470135d115323a00cf11441ab7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2020
ms.locfileid: "78927778"
---
# <a name="deploy-conditional-access-app-control-for-featured-apps"></a>Déployer le contrôle d’application par accès conditionnel pour les applications à la une

*S’applique à : Microsoft Cloud App Security*

Les contrôles de session dans Microsoft Cloud App Security fonctionner avec les applications proposées. Pour obtenir la liste des applications qui sont proposées par Cloud App Security pour un travail prêt à l’emploi, consultez [protéger les applications avec Microsoft Cloud App Security contrôle d’application par accès conditionnel](proxy-intro-aad.md#featured-apps).

## <a name="prerequisites"></a>Composants requis

Pour déployer contrôle d’application par accès conditionnel pour les applications Azure AD, vous avez besoin d’une [licence valide pour Azure ad Premium P1](https://docs.microsoft.com/azure/active-directory/license-users-groups) , ainsi qu’une licence Cloud App Security.

## <a name="to-deploy-featured-apps"></a>Pour déployer des applications proposées

Procédez comme suit pour configurer les applications proposées pour qu’elles soient contrôlées par Microsoft Cloud App Security contrôle d’application par accès conditionnel.

**Étape 1 : [accéder au portail Azure ad et créer une stratégie d’accès conditionnel pour les applications et Router la session vers Cloud App Security](#add-azure-ad)**

**Étape 2 : [se connecter à chaque application à l’aide d’un utilisateur dont l’étendue est limitée à la stratégie](#sign-in-scoped)**

**Étape 3 : [vérifier que les applications sont configurées pour utiliser les contrôles d’accès et de session](#portal)**

**Étape 4 : [tester le déploiement](#test)**

## Étape 1 : créer une stratégie de test d’accès conditionnel Azure AD<a name="add-azure-ad"></a>

1. Dans Azure Active Directory, sous **sécurité**, cliquez sur **accès conditionnel**.

1. Cliquez sur **nouvelle stratégie** et créez une nouvelle stratégie.

1. Dans la stratégie TEST, sous **utilisateurs**, attribuez un utilisateur ou un utilisateur de test qui peut être utilisé pour une authentification initiale et une vérification.

1. Dans la stratégie TEST, sous **application Cloud**, affectez les applications que vous souhaitez contrôler avec contrôle d’application par accès conditionnel.

1. Sous **session**, définissez la stratégie pour utiliser l’une des stratégies intégrées, **surveiller uniquement** ou bloquer les **téléchargements**. Ou sélectionnez **utiliser une stratégie personnalisée** pour définir une stratégie avancée dans le portail Cloud App Security.

1. Ajoutez les **assignations de condition** applicables ou les **contrôles Grant** (facultatif).

    ![Accès conditionnel Azure AD](media/azure-ad-caac-policy.png)

1. Cliquez sur **activer** et **Enregistrer**.

## Étape 2 : se connecter à chaque application à l’aide d’un utilisateur dont l’étendue est limitée à la stratégie<a name="sign-in-scoped"></a>

> [!NOTE]
> Avant de continuer, veillez à vous déconnecter des sessions existantes.

Une fois que vous avez créé la stratégie, connectez-vous à chaque application configurée dans cette stratégie. Veillez à vous connecter à l’aide d’un utilisateur configuré dans la stratégie.

Cloud App Security synchronisera vos détails de stratégie sur ses serveurs pour chaque nouvelle application à laquelle vous vous connectez. Cette opération peut prendre jusqu’à une minute.

## Étape 3 : vérifier que les applications sont configurées pour utiliser les contrôles d’accès et de session<a name="portal"></a>

Les instructions ci-dessus vous ont aidé à créer une stratégie de Cloud App Security intégrée pour les applications proposées directement dans Azure AD. Dans cette étape, vérifiez que les contrôles d’accès et de session sont configurés pour ces applications.

1. Dans le portail Cloud App Security, cliquez sur l’icône Paramètres roue dentée ![paramètres](media/settings-icon.png "icône Paramètres"), puis sélectionnez **contrôle d’application par accès conditionnel**.

1. Dans le tableau contrôle d’application par accès conditionnel Apps, examinez la colonne **contrôles disponibles** et vérifiez que le contrôle d' **accès** et **le contrôle de session** apparaissent pour vos applications.

    > [!NOTE]
    > Si le contrôle de session n’apparaît pas pour une application, il n’est pas encore disponible pour cette application spécifique. Vous pouvez l’ajouter immédiatement en tant qu' [application personnalisée](proxy-deployment-any-app.md), ou vous pouvez ouvrir une demande pour l’ajouter en tant qu’application proposée en cliquant sur **demander un contrôle de session**.
    >
    >![Demande de contrôle d’accès conditionnel aux applications](media/caac-request.png)

## Étape 4 : tester le déploiement<a name="test"></a>

1. Tout d’abord, déconnectez-vous des sessions existantes. Ensuite, essayez de vous connecter à chaque application qui a été déployée avec succès. Connectez-vous à l’aide d’un utilisateur qui correspond à la stratégie configurée dans Azure AD.

1. Dans le portail Cloud App Security, sous **examiner**, sélectionnez **Journal d’activité**et assurez-vous que les activités de connexion sont capturées pour chaque application.

1. Vous pouvez filtrer en cliquant sur **avancé**, puis le filtrage à l’aide du **contrôle d’accès source est égal**à.

    ![Filtrer à l’aide d’Azure AD accès conditionnel](media/sso-logon.png)

1. Il est recommandé de vous connecter à des applications mobiles et de bureau à partir d’appareils gérés et non gérés. Cela permet de s’assurer que les activités sont correctement capturées dans le journal d’activité.<br />
Pour vérifier que l’activité est correctement capturée, cliquez sur une activité d’ouverture de session d’authentification unique afin qu’elle ouvre le tiroir d’activité. Assurez-vous que la **balise de l’agent utilisateur** reflète correctement si l’appareil est un client natif (c’est-à-dire une application mobile ou de bureau) ou si l’appareil est un appareil géré (conforme, joint à un domaine ou un certificat de client valide).

> [!NOTE]
> Après son déploiement, vous ne pouvez pas supprimer une application de la page contrôle d’application par accès conditionnel. Tant que vous ne définissez pas de session ou de stratégie d’accès sur l’application, le contrôle d’application par accès conditionnel ne modifiera aucun comportement pour l’application.

## <a name="next-steps"></a>Étapes suivantes :

> [!div class="nextstepaction"]
> [«PRÉCÉDENT : introduction à contrôle d’application par accès conditionnel](proxy-intro-aad.md)

> [!div class="nextstepaction"]
> [Étape suivante : intégration et déploiement de contrôle d’application par accès conditionnel pour une application»](proxy-deployment-any-app.md)

[!INCLUDE [Open support ticket](includes/support.md)]
