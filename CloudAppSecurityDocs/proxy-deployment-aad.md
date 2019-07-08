---
title: Déployer le contrôle d’application par accès conditionnel Cloud App Security pour les applications Azure AD
description: Cet article fournit des informations sur le déploiement du proxy inversé du Contrôle d’application par accès conditionnel Microsoft Cloud App Security pour les applications Azure AD.
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
ms.assetid: 2490c5e5-e723-4fc2-a5e0-d0a3a7d01fc2
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 511512c6d615f1e0fe09640bb7b02b2df694c6de
ms.sourcegitcommit: 8fd13c10c2f66a553a8a8fc413555ca837fc9c56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610747"
---
# <a name="deploy-conditional-access-app-control-for-featured-apps"></a>Déployer le contrôle d’application par accès conditionnel pour les applications à la une

*S’applique à : Microsoft Cloud App Security*

>[!div class="step-by-step"]
[« Précédent : Introduction au contrôle d’application par accès conditionnel](proxy-intro-aad.md)<br>
[Suivant : Guide pratique pour créer une stratégie de session »](session-policy-aad.md)

Suivez ces étapes pour configurer des applications proposées contrôlés par Microsoft Cloud App Security contrôle d’accès conditionnel.

**Étape 1 : [Accédez au portail Azure AD, créez une stratégie d’accès conditionnel pour les applications et acheminez la session vers Cloud App Security](#add-azure-ad).**

**Étape 2 : [Connectez-vous à chaque application à l’aide d’un utilisateur limité à la stratégie](#sign-in-scoped).**

**Étape 3 : Si vous n’avez pas sélectionné une stratégie de Cloud App Security intégrée dans Azure AD ou si vous souhaitez appliquer la stratégie à une n’importe quelle application, [accédez au portail Cloud App Security](#portal)**

[**Étape 4 : Testez le déploiement**](#test)

> [!NOTE]
> Pour déployer le contrôle d’application par accès conditionnel pour des applications Azure AD, vous avez besoin d’une [licence valide pour Azure AD Premium P1](https://docs.microsoft.com/azure/active-directory/license-users-groups), ainsi que d’une licence Cloud App Security.

## Étape 1 : Créez une stratégie de test d’accès conditionnel Azure AD <a name="add-azure-ad"></a>  

1. Dans Azure Active Directory, sous **sécurité**, cliquez sur **accès conditionnel**.

2. Cliquez sur **Nouvelle stratégie** et créez une stratégie.

3. Dans la stratégie TEST, sous **Utilisateurs**, attribuez un utilisateur de test ou un utilisateur pouvant servir à une ouverture de session initiale et à la vérification.

4. Dans la stratégie TEST, sous **Application cloud**, assignez les applications que vous voulez contrôler avec le Contrôle d'application par accès conditionnel. 

5. Sous **Session**, définissez la stratégie pour qu’elle utilise l’une des stratégies intégrées, **Surveiller uniquement** ou **Bloquer les téléchargements**. Ou sélectionnez **Utiliser stratégie personnalisée** pour définir une stratégie avancée dans le portail Cloud App Security. 

6. Ajoutez des **Conditions d’affectation** ou des **Contrôles d’octroi** (facultatif).

   ![Accès conditionnel Azure AD](./media/azure-ad-caac-policy.png)

      > [!NOTE]
      >Le Contrôle d'application par accès conditionnel prend en charge toute application SAML ou Open ID Connect configurée avec l’authentification unique dans Azure AD, notamment ces applications proposées. Les applications non proposées peuvent être configurées avec le contrôle d’accès dans le portail Cloud App Security en effectuant une demande pour les intégrer avec le contrôle de session. 

7. Cliquez sur **activer** et **enregistrer**.

## Étape 2 : Connectez-vous à chaque application à l’aide d’un utilisateur limité à la stratégie<a name="sign-in-scoped"></a>

Une fois que vous avez créé la stratégie, connectez-vous à chaque application configurée dans cette stratégie. Veillez à vous connecter à l’aide d’un utilisateur configuré dans la stratégie. Veillez tout d’abord à vous déconnecter des sessions existantes.

Cloud App Security synchronise vos détails de la stratégie à ses serveurs pour chaque nouvelle application que vous êtes connecté à.  Cette opération peut prendre jusqu’à une minute.

## Étape 3 : Configurer des contrôles avancés et toutes les applications dans le portail Cloud App Security<a name="portal"></a>

Les instructions ci-dessus vous ont aidé à créer une stratégie Cloud App Security intégrée pour les applications proposées directement dans Azure AD.

Pour configurer une stratégie avancée, créez un [stratégie d’accès](access-policy-aad.md) ou un [stratégie de session](session-policy-aad.md) dans Cloud App Security.

Pour appliquer la stratégie à une n’importe quelle application, suivez les instructions pour [self-intégrer une n’importe quelle application pour une utilisation avec le contrôle d’accès conditionnel](proxy-deployment-any-app.md).

Pour demander la prise en charge pour une n’importe quelle application :

1. Dans le portail Cloud App Security, accédez à la roue dentée des paramètres et choisissez **Contrôle d'application par accès conditionnel**. Un message doit vous informer que de nouvelles applications Azure AD ont été découvertes par le Contrôle d'application par accès conditionnel.

    ![Menu du contrôle d’application par accès conditionnel](./media/caac-menu.png)

2. Cliquez sur **Afficher les nouvelles applications**.

    ![Afficher les nouvelles applications du Contrôle d’application par accès conditionnel](./media/caac-view-apps.png)

3. Dans l’écran qui s’ouvre, vous pouvez voir toutes les applications auxquelles vous vous êtes connecté à l’étape précédente. Pour chaque application, cliquez sur le signe + et cliquez sur **Ajouter**.

   > [!NOTE]
   > Si une application n’apparaît pas dans le catalogue d’applications Cloud App Security, elle figure, dans la boîte de dialogue, sous les applications non identifiées, avec son URL de connexion. Lorsque vous cliquez sur le signe + pour ces applications, vous pouvez intégrer l’application en tant qu’application personnalisée.

   ![Applications Azure AD découvertes du Contrôle d’application par accès conditionnel](./media/caac-discovered-aad-apps.png)

4. Dans la table des applications de Contrôle d’application par accès conditionnel, examinez la colonne **Contrôles disponibles** et vérifiez que **l’accès conditionnel Azure AD** et le **contrôle de session** apparaissent.

   > [!NOTE]
   > Si le contrôle de session n’apparaît pas pour une application, cela signifie qu’il n’est pas encore disponible pour cette application spécifique. Le lien **Demander le contrôle de la session** sera affiché à la place.

     ![Demande du Contrôle d’application par accès conditionnel](./media/caac-request.png)

5. Cliquez sur **Demander le contrôle de session** pour demander que l’application soit intégrée au contrôle de session. Le processus d’intégration est effectué par l’équipe Microsoft Cloud App Security et avec vous.

6. Pour configurer une stratégie pour tirer parti de gestion des appareils via des certificats de client :
    1. Accédez à la roue dentée des paramètres et choisissez **Identification de périphérique**.
    2. Charger un ou plusieurs certificats intermédiaires ou racines.
    3. Une fois le certificat chargé, vous pouvez créer des stratégies d’accès et des stratégies de session basées sur une **balise d’appareil** et un **certification client valide**.

       ![ID d’appareil du Contrôle d’application par accès conditionnel](./media/caac-device-id.png)

> [!NOTE]
> Un certificat est uniquement demandé à un utilisateur si la session correspond à une stratégie qui utilise le filtre du certificat client valide.

## Étape 4 : Testez le déploiement<a name="test"></a>

1. Tout d’abord, déconnectez-vous de toutes les sessions existantes. Ensuite, essayez de vous connecter à chaque application qui a été déployée avec succès. Connectez-vous sous un utilisateur qui correspond à la stratégie configurée dans Azure AD.

2. Dans le portail Cloud App Security, sous **Examiner**, sélectionnez **Journal d’activité** et vérifiez que les activités de connexion sont capturées pour chaque application.

3. Vous pouvez filtrer en cliquant sur **Avancé**, puis en filtrant avec **Source est égale à Contrôle d’accès**.

    ![Filtrer à l’aide de l’accès conditionnel Azure AD](./media/sso-logon.png)

4. Nous vous recommandons de vous connecter aux applications mobiles et de bureau à partir d’appareils gérés et non gérés, afin de vous assurer que les activités sont correctement capturées dans le journal d’activité.<br>
Pour vérifier que les activités sont correctement capturées, cliquez sur une activité de connexion avec authentification unique afin d’ouvrir le tiroir Activité. Vérifiez que l’**Étiquette agent utilisateur** indique correctement si l’appareil est un client natif (à savoir, une application mobile ou de bureau) ou un appareil géré (conforme, joint à un domaine ou avec certificat client valide).

> [!NOTE]
> Après son déploiement, vous ne pouvez pas supprimer une application à partir de la page Contrôle d’application par accès conditionnel. Tant que vous ne définissez pas une stratégie d’accès ou de session sur l’application, le contrôle d’application par accès conditionnel ne change pas le comportement de l’application.

>[!div class="step-by-step"]
[« Précédent : Introduction au contrôle d’application par accès conditionnel](proxy-intro-aad.md)<br>[Suivant : Intégrer et déployer le contrôle d’accès conditionnel pour n’importe quelle application »](proxy-deployment-any-app.md)

## <a name="next-steps"></a>Étapes suivantes 
[Utilisation de contrôle d’accès conditionnel Cloud App Security](proxy-intro-aad.md)

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)