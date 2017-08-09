---
title: "Déploiement du proxy Cloud App Security | Microsoft Docs"
description: "Cette rubrique fournit des informations sur le déploiement du proxy Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/31/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 75094bde-e135-47fb-b5c6-7e1168919771
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 245e44cdf56b15795f67340442babcb0f688ea9d
ms.sourcegitcommit: c5a0d07af558239976ce144c14ae56c81642191b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2017
---
# <a name="deploying-the-cloud-app-security-proxy"></a>Déploiement du proxy Cloud App Security

> [!NOTE]
> Il est fortement recommandé d’essayer l’installation dans un environnement de bac à sable ou de test avant de l’installer dans un environnement de production.

Les étapes décrites ci-dessous permettent de déployer le proxy Cloud App Security, et d’activer le contrôle d’accès et le contrôle de session.

## <a name="prerequisites"></a>Conditions préalables

-   Un environnement de travail dans lequel votre application cloud est configurée avec un fournisseur d’identité. Le processus d’installation implique des modifications de la configuration dans l’application et le fournisseur d’identité.
- Vérifiez que vous avez accès aux paramètres d’authentification unique dans votre fournisseur d’identité et l’application.

## <a name="deploy-the-proxy"></a>Déployer le proxy

Si vous installez le proxy dans un environnement de production, nous vous recommandons de le faire quand les utilisateurs sont le moins susceptibles d’utiliser l’application, par exemple, tard le soir ou pendant le week-end, et de les informer qu’un court temps d’arrêt de l’application peut se produire.

Avant de modifier la configuration, vérifiez que la configuration actuelle fonctionne. Ensuite, effectuez les étapes suivantes.

1.  Dans le portail Cloud App Security, accédez à la roue dentée des paramètres et choisissez **Proxy**.

2. En haut à droite, cliquez sur le signe plus.

3. Dans la fenêtre **Ajouter une application au proxy**, sélectionnez l’application que vous voulez ajouter, puis cliquez sur **Démarrer l’Assistant**. 

 ![ajouter une application au proxy Cloud App Security](./media/proxy-add-app.png)

4. Chargez le fichier de métadonnées d’authentification unique à partir des paramètres d’authentification unique de votre application. Si vous n’avez pas de fichier de métadonnées, cliquez sur **Renseigner les données manuellement** et fournissez les données demandées, conformément à l’Assistant. 

 ![ajouter un fichier de métadonnées d’authentification unique au proxy Cloud App Security](./media/proxy-w-add-app.png)


5. Dans le portail de votre fournisseur d’identité, effectuez les étapes suivantes. Dans la plupart des portails de fournisseur d’identité, cette opération est effectuée sous **Applications** :

    1. Créez une application SAML personnalisée. Vous devez créer une application personnalisée pour pouvoir par la suite changer les URL et ajouter des attributs SAML, ce qui n’est pas possible dans les applications de la galerie.
    
    2. Copiez dans la nouvelle application personnalisée la configuration d’authentification unique de l’application existante dans la liste du fournisseur d’identité. Vérifiez que **l’identificateur** (également appelé ID public ou d’entité) dans l’application personnalisée correspond à **l’identificateur** des paramètres d’authentification unique de l’application réelle. Si votre fournisseur d’identité ne vous permet pas d’utiliser le même **identificateur** pour deux applications différentes, copiez l’identificateur de l’application d’origine et changez-le.
    
    3. Attribuez tous les utilisateurs actuellement attribués à l’application d’origine à la nouvelle application personnalisée.
    
    ![ajouter un fichier de métadonnées d’authentification unique au proxy Cloud App Security](./media/proxy-w-add-external-config.png)

5. Chargez le fichier de métadonnées d’authentification unique de votre fournisseur d’identité. Si vous n’avez pas de fichier de métadonnées, cliquez sur **Renseigner les données manuellement** et fournissez les données demandées, conformément à l’Assistant.  

 ![ajouter un fichier de métadonnées d’authentification unique au proxy Cloud App Security](./media/proxy-w-identity-provider.png)

6. Appliquez les modifications de configuration externe suivantes dans le portail de votre fournisseur d’identité, puis, dans la nouvelle application personnalisée que vous avez créée, procédez comme suit :

    1. Copiez l’URL fournie dans l’Assistant. Ensuite, accédez au portail de votre fournisseur d’identité et collez-la comme URL d’authentification unique (ou URL de réponse) dans la nouvelle application SAML personnalisée que vous avez créée.
    
    2. Copiez les attributs et les valeurs fournis dans l’Assistant du proxy et ajoutez-les comme attributs personnalisés SAML.
    
    3. Vérifiez que les identificateurs de nom utilisés par votre application sont sous forme d’adresse e-mail (nécessaire pour permettre au proxy Cloud App Security d’appliquer des stratégies sur les utilisateurs).
    
    4. Enregistrez les paramètres de votre nouvelle application personnalisée et cliquez sur **Suivant** dans l’Assistant du proxy.
 ![mettre à jour les paramètres de fournisseur d’identité dans le proxy Cloud App Security](./media/proxy-w-ip-external2.png)

4.  Ensuite, dans la page des paramètres d’authentification unique de l’application, procédez comme suit :
    1. Sauvegardez vos paramètres d’application actuels.
    
    2. Copiez l’URL de l’Assistant du proxy dans l’URL d’authentification unique SAML de l’application.
    
    3. Téléchargez le certificat SAML de Cloud App Security pour l’application.
    
    4. Dans l’application personnalisée que vous avez créée, chargez ce certificat SAML à la place de celui d’origine et enregistrez vos paramètres.
   
    5. Dans l’Assistant du proxy, cliquez sur **Terminer**.


Au bout de quelques minutes, toutes les demandes de connexion à votre application sont routées via le proxy Cloud App Security. 



### <a name="test-the-configuration"></a>Tester la configuration

1.  Essayez de vous connecter à l’application. Si la connexion échoue, vérifiez que vous avez correctement effectué toutes les étapes de l’Assistant du proxy. 

2.  Dans le portail Cloud App Security, sous **Examiner**, sélectionnez **Journal d’activité** et vérifiez que des événements **Connexion avec authentification unique** sont capturés par le proxy.



## <a name="see-also"></a>Voir aussi  
[Utilisation du proxy Cloud App Security](proxy-intro.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  