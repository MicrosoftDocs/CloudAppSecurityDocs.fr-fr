---
title: "Création de stratégies pour contrôler l’utilisation des applications cloud avec le proxy Cloud App Security | Microsoft Docs"
description: "Cette rubrique fournit des informations sur la création de stratégies pour contrôler l’utilisation des applications cloud avec le proxy Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/16/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: b419aff0-3f50-4917-9ee2-9ecf7539a5d7
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 4544f5b48484f9341bb85d09d8fdc8d11fd4ba00
ms.sourcegitcommit: c5a0d07af558239976ce144c14ae56c81642191b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2017
---
# <a name="controlling-app-use-with-proxy-control"></a>Contrôle de l’utilisation des applications avec le contrôle du proxy

Après avoir déployé le proxy, vous pouvez contrôler l’accès et les sessions dans le cloud de votre organisation en créant des stratégies pour bloquer l’accès et les comportements indésirables.

## <a name="create-access-control-policies-in-cloud-app-security"></a>Créer des stratégies de contrôle d’accès dans Cloud App Security

Pour créer des stratégies de contrôle d’accès :

1.  Sous **Contrôle,** sélectionnez **Stratégies**.

2.  Sous **Créer une stratégie**, choisissez **Stratégie proxy**, puis pour le **Type d’activité**, sélectionnez **Connexion avec authentification unique**.

3.  Ensuite, choisissez l’application et les filtres appropriés, puis l’option d’atténuation de votre choix.

>[!NOTE]
> Dans les filtres, vous pouvez choisir **Étiquette de l’appareil** et la définir pour qu’elle soit égale ou différente à **Appareil géré**. Voir ci-dessous pour plus d’informations sur les [Appareils gérés](#_Managed_devices).

Par ailleurs, notez que dans les **Actions d’atténuation,** vous pouvez choisir de **Journaliser** ou de **Bloquer l’accès**, ou encore de **Router vers Cloud App Security**, ce qui vous permet de surveiller la session et de créer des stratégies sur cette dernière. Cette procédure est expliquée dans [Création de stratégies de contrôle de session dans Cloud App Security](#_Creating_session_control).

## <a name="create-session-control-policies-in-cloud-app-security"></a>Créer des stratégies de contrôle de session dans Cloud App Security 

Après avoir déployé le proxy, vous pouvez ajouter des fonctionnalités de contrôle de session en définissant des stratégies de session dans le portail Cloud App Security.

Nous vous recommandons de commencer par activer le contrôle de session pour un petit groupe d’utilisateurs avant de le déployer dans votre organisation. Par ailleurs, nous vous recommandons d’activer le contrôle de session pour toutes les sessions ou pour la majorité d’entre elles. Comme le contrôle de session est basé sur un déploiement sans agent qui a ses limites, il est conçu pour couvrir les cas dans lesquels vous avez peu ou pas de contrôle sur l’appareil et l’application.

Pour créer des stratégies de contrôle de session :

1.  Créez une [stratégie d’accès](#working-with-proxy-control-features) et, pour l’action d’atténuation, choisissez **Router vers Cloud App Security**.

2.  Sous **Contrôle**, accédez à **Stratégies** et sous **Créer une stratégie**, choisissez **Stratégie proxy.**

3.  Ensuite, pour le **Type d’activité,** choisissez **Télécharger le fichier** ou **Exporter le rapport**. Choisissez l’application et les filtres appropriés, puis l’option d’atténuation de votre choix.

## <a name="enabling-managedunmanaged-device-control"></a>Activation du contrôle des appareils gérés/non gérés

### <a name="step-1-deploy-certificates"></a>ÉTAPE 1 : Déployer des certificats

Pour que Cloud App Security identifie si les appareils qui se connectent à votre cloud sont gérés ou non gérés, vous devez déployer des certificats clients. Cette opération peut être effectuée de différentes manières, généralement en utilisant les certificats d’une solution de gestion des appareils mobiles existante ou à l’aide de stratégies de groupe Active Directory.

### <a name="step-2-upload-the-root-certificate-to-cloud-app-security"></a>ÉTAPE 2 : Charger le certificat racine dans Cloud App Security

Pour activer l’identification des appareils gérés dans le portail Cloud App Security, vous devez d’abord charger le certificat racine de l’autorité de certification :

1.  Cliquez sur la roue dentée des paramètres et choisissez **Appareils gérés.**

2.  Activez **Identification de l’appareil**.

3. Chargez le certificat racine.

![certificat d’appareil géré du proxy cloud app security](./media/managed-device-cert.png)

### <a name="step-3-create-managed-device-policies"></a>ÉTAPE 3 : Créer des stratégies d’appareil géré

Une fois le certificat racine chargé, utilisez le filtre **Étiquette de l’appareil** égal ou différent de **Appareil géré** pour créer des stratégies proxy ou pour rechercher des événements dans le journal d’activité.

Quand vous utilisez des certificats clients pour identifier les appareils gérés, nous vous recommandons de commencer en mode de surveillance avant de tenter de bloquer ou de surveiller la session. Cela signifie que vous définissez une stratégie d’accès avec un filtre **Appareil géré** dans lequel l’action d’atténuation est **Journaliser uniquement**. Une fois que vous avez un peu plus d’expérience avec vos utilisateurs, vous pouvez ajouter d’autres actions d’atténuation comme le blocage de l’accès ou la surveillance de la session.


## <a name="see-also"></a>Voir aussi  
[Utilisation du proxy Cloud App Security](proxy-intro.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  