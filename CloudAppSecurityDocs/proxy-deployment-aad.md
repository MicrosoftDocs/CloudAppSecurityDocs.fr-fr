---
title: "Déploiement du proxy Cloud App Security pour Azure AD | Microsoft Docs"
description: "Cette rubrique fournit des informations sur le déploiement du proxy Cloud App Security pour les applications Azure AD."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/10/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 2490c5e5-e723-4fc2-a5e0-d0a3a7d01fc2
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 58b309ddcc893d47a8adc89e9b286eff97ec99ed
ms.sourcegitcommit: 4cf65f627f2d370ee4a4decae1acbb9658874056
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2017
---
# <a name="deploying-the-cloud-app-security-proxy-for-azure-ad"></a>Déploiement du proxy Cloud App Security pour Azure AD

> [!NOTE]
> Il est fortement recommandé d’essayer l’installation dans un environnement de bac à sable ou de test avant de l’installer dans un environnement de production.

Les étapes décrites ci-dessous permettent de déployer le proxy Cloud App Security, et d’activer le contrôle d’accès et le contrôle de session.


## <a name="step-1-create-an-azure-ad-conditional-access-policy"></a>Étape 1 : Créer une stratégie d’accès conditionnel Azure AD

1. Dans Azure Active Directory, sous **Sécurité**, cliquez sur **Accès conditionnel**.

 ![Accès conditionnel Azure AD](./media/conditional-access.png)

2. Cliquez sur **Nouvelle stratégie** et créez une stratégie en vérifiant que sous **Session**, vous sélectionnez **Utiliser les restrictions appliquées par le proxy**.

## <a name="step-2-log-on-to-each-app"></a>Étape 2 : Se connecter à chaque application

Utilisez vos informations d’identification pour vous connecter à chaque application que vous voulez contrôler avec le proxy.

## <a name="step-3-add-the-apps-in-cloud-app-security"></a>Étape 3 : Ajouter les applications dans Cloud App Security

1.  Dans le portail Cloud App Security, accédez à la roue dentée des paramètres et choisissez **Proxy**.

2. Les applications auxquelles vous vous connectez s’affichent maintenant dans la table. 

3. Pour chaque application, cliquez sur les points de suspension dans le coin droit de la ligne de table, puis sur **Poursuivre l’installation**.

4. Dans l’Assistant du proxy, cliquez sur **Terminer**.


Au bout de quelques minutes, toutes les demandes de connexion à votre application sont routées via le proxy Cloud App Security. 

## <a name="test-the-configuration"></a>Tester la configuration

1.  Essayez de vous connecter à l’application. Si la connexion échoue, vérifiez que vous avez correctement effectué toutes les étapes de l’Assistant du proxy. 

2.  Dans le portail Cloud App Security, sous **Examiner**, sélectionnez **Journal d’activité** et vérifiez que des événements **Connexion avec authentification unique** sont capturés par le proxy.



## <a name="see-also"></a>Voir aussi  
[Utilisation du proxy Cloud App Security](proxy-intro.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  