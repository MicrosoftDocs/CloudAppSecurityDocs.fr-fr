---
title: Déployer le Contrôle d’application par accès conditionnel Microsoft Cloud App Security pour les applications Azure AD | Microsoft Docs
description: Cet article fournit des informations sur le déploiement du proxy inversé du Contrôle d’application par accès conditionnel Microsoft Cloud App Security pour les applications Azure AD.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 2490c5e5-e723-4fc2-a5e0-d0a3a7d01fc2
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: ef834c9b73af6a1bed34530b29bec4fd3581cc1e
ms.sourcegitcommit: b0b3e6c6f150fff8c286185826ce099601a12679
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2018
ms.locfileid: "52280559"
---
# <a name="deploy-conditional-access-app-control-for-azure-ad-apps"></a>Déployer le Contrôle d’application par accès conditionnel Azure AD

*S’applique à : Microsoft Cloud App Security*

>[!div class="step-by-step"]
[« Précédent : Introduction au Contrôle d’accès conditionnel aux applications](proxy-intro-aad.md)<br>
[Suivant : Guide pratique pour créer une stratégie de session »](session-policy-aad.md)


Suivez ces étapes pour configurer des applications Azure AD à contrôler par le Contrôle d’application par accès conditionnel Microsoft Cloud App Security.

**Étape 1 : [accédez au portail Azure AD, créez une stratégie d’accès conditionnel pour les applications et acheminez la session vers Cloud App Security](#add-azure-ad).**

**Étape 2 : [connectez-vous avec un utilisateur inclus dans l’étendue de la stratégie dans les applications](#sign-in-scoped).**

**Étape 3 :[retournez au portail Cloud App Security et sélectionnez la notification de bannière pour ajouter les applications](#banner-notification).**

**Étape 4 : [créez une stratégie d’accès](access-policy-aad.md) ou [ une stratégie de session](session-policy-aad.md) pour les applications dans Cloud App Security.**


> [!NOTE]
> Pour déployer le contrôle d’application par accès conditionnel pour des applications Azure AD, vous avez besoin d’une [licence valide pour Azure AD Premium P1](https://docs.microsoft.com/azure/active-directory/license-users-groups).

## Étape 1 : ajoutez des applications Azure AD dans Cloud App Security.<a name="add-azure-ad"></a>  

1. Créez une stratégie TEST d’accès conditionnel Azure AD.

   1. Dans Azure Active Directory, sous **Sécurité**, cliquez sur **Accès conditionnel**.

      ![Accès conditionnel Azure AD](./media/aad-conditional-access.png)

   2. Cliquez sur **Nouvelle stratégie** et créez une stratégie. Sous **Session**, veillez à sélectionner **Utiliser les restrictions appliquées au Contrôle d’application par accès conditionnel**.

      ![Accès conditionnel Azure AD](./media/proxy-deploy-restrictions-aad.png)

   3. Dans la stratégie TEST, sous **Utilisateurs**, attribuez un utilisateur de test ou un utilisateur pouvant servir à une ouverture de session initiale.
    
   4. Dans la stratégie TEST, sous **Application cloud**, assignez les applications que vous voulez contrôler avec le Contrôle d'application par accès conditionnel. 

      > [!NOTE]
      >Veillez à choisir des applications prises en charge par le Contrôle d’accès conditionnel aux applications. Le Contrôle d'application par accès conditionnel prend en charge des applications configurées avec des applications SAML et Open ID Connect avec l’authentification unique dans Azure AD. 

## Étape 2 : connectez-vous avec un utilisateur inclus dans l’étendue de la stratégie dans les applications <a name="sign-in-scoped"></a>

Une fois que vous avez créé la stratégie, connectez-vous à chaque application configurée dans cette stratégie. Veillez à vous connecter à l’aide d’un utilisateur configuré dans la stratégie. Veillez tout d’abord à vous déconnecter des sessions existantes.

## Étape 3 : revenez au portail Cloud App Security et sélectionnez la notification de bannière pour ajouter les applications <a name="banner-notification"></a>

1. Dans le portail Cloud App Security, accédez à la roue dentée des paramètres et choisissez **Contrôle d'application par accès conditionnel**. 
    
     ![menu du proxy](./media/proxy-menu.png)

2. Un message doit vous informer que de nouvelles applications Azure AD ont été découvertes par le Contrôle d'application par accès conditionnel. Cliquez sur le lien **Afficher les nouvelles applications**.

   ![Nouvelles applications d’affichage du Contrôle d'application par accès conditionnel](./media/proxy-view-new-apps.png)

3. Dans la boîte de dialogue qui s’ouvre, vous pouvez voir toutes les applications auxquelles vous vous êtes connecté à l’étape précédente. Pour chaque application, cliquez sur le signe + et cliquez sur **Ajouter**.

   ![Nouvelles applications du Contrôle d'application par accès conditionnel](./media/proxy-new-app.png)

   > [!NOTE]
   > Si une application n’apparaît pas dans le catalogue d’applications Cloud App Security, elle figure, dans la boîte de dialogue, sous les applications non identifiées, avec son URL de connexion. Lorsque vous cliquez sur le signe + de telles applications, vous pouvez suggérer de les ajouter au catalogue. Une fois que l’application figure dans le catalogue, reprenez les étapes pour la déployer. 

4. Dans la table des applications de Contrôle d'application par accès conditionnel, examinez la colonne **Contrôles disponibles** et vérifiez que l’accès conditionnel Azure AD et le contrôle de session apparaissent. <br></br>Si le contrôle de session n’apparaît pas pour une application, cela signifie qu’il n’est pas encore disponible pour cette application spécifique. Le lien **Demander le contrôle de la session** sera affiché à la place. Cliquez dessus pour ouvrir une boîte de dialogue et demander l’intégration de l’application au contrôle de session. Dans ce scénario, le processus d’intégration sera effectué par l’équipe Microsoft Cloud App Security et avec vous.
  
   ![demander le contrôle de la session](./media/proxy-view-new-apps.png)

5. Facultatif - Identifier les appareils qui utilisent des certificats clients :

   1. Accédez à la roue dentée des paramètres et choisissez **Identification de périphérique**.

   2. Chargez un certificat racine.

      ![Identification de l’appareil](./media/device-identification.png)
 
      Une fois le certificat chargé, vous pouvez créer des stratégies d’accès et des stratégies de session basées sur une **balise d’appareil** et un **certification client valide**.
 
      > [!NOTE]
      >Un certificat est uniquement demandé à un utilisateur si la session correspond à une stratégie qui utilise le filtre du certificat client valide. 

## <a name="test-the-deployment"></a>Tester le déploiement

1. Tout d’abord, déconnectez-vous de toutes les sessions existantes. Ensuite, essayez de vous connecter à chaque application qui a été déployée avec succès. Connectez-vous sous un utilisateur qui correspond à la stratégie configurée dans Azure AD. 

2. Dans le portail Cloud App Security, sous **Examiner**, sélectionnez **Journal d’activité** et vérifiez que les activités de connexion sont capturées pour chaque application.

3. Vous pouvez filtrer en cliquant sur **Avancé**, puis en filtrant avec **Source est égale à Accès conditionnel Azure Active Directory**.

    ![Filtrer à l’aide de l’accès conditionnel Azure AD](./media/sso-logon.png)

4. Nous vous recommandons de vous connecter aux applications mobiles et de bureau à partir d’appareils gérés et non gérés, afin de vous assurer que les activités sont correctement capturées dans le journal d’activité.<br></br>
   Pour vérifier que les activités sont correctement capturées, cliquez sur une activité de connexion avec authentification unique afin d’ouvrir le tiroir Activité. Vérifiez que l’**Étiquette agent utilisateur** indique correctement si l’appareil est un client natif (à savoir, une application mobile ou de bureau) ou un appareil géré (conforme, joint à un domaine ou avec certificat client valide).
 
   ![étiquette de l’agent utilisateur de test](./media/domain-joined.png)


Vous êtes maintenant prêt à créer des [stratégies d’accès](access-policy-aad.md) et des [stratégies de session](session-policy-aad.md) pour contrôler vos applications de Contrôle d’application par accès conditionnel.


>[!div class="step-by-step"]
[« Précédent : Introduction au Contrôle d’accès conditionnel aux applications](proxy-intro-aad.md)<br>
[Suivant : Guide pratique pour créer une stratégie de session »](session-policy-aad.md)


## <a name="next-steps"></a>Étapes suivantes 
[Utilisation avec le Contrôle d’accès conditionnel aux applications de Cloud App Security](proxy-intro-aad.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  