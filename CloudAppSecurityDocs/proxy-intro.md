---
title: Utilisation du proxy Cloud App Security | Microsoft Docs
description: Cette rubrique fournit des informations sur le fonctionnement du proxy Cloud App Security.
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/9/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 28317b70-1851-4610-b1d6-863bc5994bb6
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: d4b01d92f705566bac36d764a7aede0eaa8defcc
ms.sourcegitcommit: 4cf65f627f2d370ee4a4decae1acbb9658874056
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2017
---
# <a name="working-with-the-cloud-app-security-proxy"></a>Utilisation du proxy Cloud App Security

Dans l’espace de travail actuel, souvent il ne suffit pas de savoir ce qui se passe dans votre environnement cloud après coup, vous devez pouvoir stopper les violations de sécurité et les fuites en temps réel, avant que les employés exposent par inadvertance ou intentionnellement vos données et votre organisation. Vous devez pouvoir autoriser les utilisateurs de votre organisation à accéder à la plupart des services et outils dans des applications cloud, et à apporter leurs propres appareils au travail. En même temps, vous avez besoin d’outils pour protéger votre organisation contre les fuites de données, les attaques de ransomware et le vol massif de données. 

## <a name="introducing-the-cloud-app-security-proxy"></a>Présentation du proxy Cloud App Security
Le proxy de Cloud App Security vous offre les outils nécessaires pour surveiller en temps réel votre environnement cloud et en contrôler l’accès, ainsi que les activités qu’il héberge.
Avec le proxy Cloud App Security, vous pouvez protéger votre organisation de la manière suivante :
- Éviter les fuites de données en bloquant les téléchargements avant qu’ils se produisent
- Limiter votre exposition aux ransomware en gérant et bloquant l’accès à votre réseau pour les appareils non gérés susceptibles de ne pas être protégés par mot de passe ou de ne pas avoir de logiciel antivirus installé
- Définir des règles qui forcent le chiffrement des données stockées dans le cloud et téléchargées à partir du cloud
- Obtenir une visibilité sur les points de terminaison non protégés afin de surveiller les opérations réalisées sur les appareils non gérés
- Contrôler l’accès à partir d’adresses IP risquées et de fournisseurs d’identité hérités

Pour activer ces fonctionnalités uniques, utilisez les deux niveaux de contrôle fournis par le proxy : le contrôle d’accès et le contrôle de session. Ces deux types de contrôle utilisent les informations utilisateur, les informations d’emplacement et les informations de l’appareil (utilisées pour identifier les appareils gérés et non gérés) afin de prendre des décisions en matière de stratégie pour chaque application.

## <a name="access-control"></a>Contrôle d’accès
Le contrôle d’accès vous donne la possibilité d’analyser, d’auditer et de bloquer l’accès en fonction de l’appareil, l’application, l’utilisateur et l’emplacement. De cette façon, vous pouvez contrôler l’accès à vos applications cloud en temps réel.

Le contrôle d’accès vous permet de créer des stratégies puissantes, de type :
 - Bloquer l’accès à toutes les applications cloud sur des appareils non gérés
 - Bloquer l’accès à des applications cloud spécifiques pour des utilisateurs spécifiques
 - Surveiller l’accès à des applications cloud spécifiques à partir d’emplacements spécifiques
 - Limiter l’accès aux applications cloud pour des groupes d’utilisateurs et des emplacements spécifiques

Pour utiliser le contrôle d’accès dans Cloud App Security, déployez le proxy en apportant quelques modifications à la configuration de votre fournisseur d’identité existant, puis définissez une stratégie pour contrôler vos applications cloud. 

> [!NOTE]
> -  Il est inutile de modifier les stratégies existantes du fournisseur d’identité.

### <a name="how-access-control-works"></a>Fonctionnement du contrôle d’accès

Dans le cadre du déploiement du proxy, vous modifiez la configuration de l’application et du fournisseur d’identité pour rediriger les demandes de connexion vers le proxy. 

Ensuite, tous les événements de connexion sont routés via le proxy qui peut décider d’autoriser l’accès à l’application, de refuser l’accès ou de surveiller l’accès.

### <a name="supported-apps-and-identity-providers"></a>Applications et fournisseurs d’identité pris en charge

Le contrôle d’accès prend en charge tous les fournisseurs d’identité et applications prenant en charge les protocoles SAML ou WS-Federation. L’équipe Cloud App Security a testé les principaux fournisseurs d’identité et applications avec les fonctionnalités de contrôle d’accès. Toutefois, en raison du nombre élevé de fournisseurs d’identité et d’applications, nous vous recommandons de tester le processus d’authentification unique avec votre fournisseur d’identité et votre application dans environnement de bac à sable ou de test avant de le déployer dans un environnement de production.

## <a name="session-control"></a>Contrôle de session

Le contrôle de session fournit une couche supplémentaire de contrôle en fournissant des insights sur chaque activité dans chaque session utilisateur. Le contrôle de session permet une surveillance en profondeur au niveau de la session, qui vous offre une visibilité granulaire des applications cloud similaire à celle des proxys en ligne pour les applications locales. Au lieu d’autoriser ou de bloquer complètement l’accès, le contrôle de session vous permet de limiter des activités de session spécifiques. 

Par exemple, vous pouvez décider que pour les appareils non gérés ou pour les sessions provenant d’emplacements spécifiques, vous voulez autoriser l’utilisateur à accéder à l’application, mais limiter le téléchargement des fichiers sensibles. 

### <a name="how-session-control-works"></a>Fonctionnement du contrôle de session

Le contrôle de session du proxy repose sur le contrôle d’accès. Une fois que vous contrôlez l’accès à une application, vous pouvez définir des stratégies de session qui redirigent les sessions utilisateur vers le contrôle de session du proxy. Dès lors, les demandes de l’utilisateur et les réponses passent par le proxy au lieu de passer par l’application directement.

Pour garder l’utilisateur dans la session, le proxy remplace tous les scripts Java, URL et cookies appropriés dans l’application par des pages dupliquées dans le proxy. Par exemple : si l’application retourne une page avec des liens qui se terminent par *myapp.com*, le proxy les remplace par des pages qui se terminent par quelque chose comme *myapp.com.cas.ms*.

Quand une session est dirigée vers le proxy, ce dernier peut inspecter le trafic, afficher les événements qu’il identifie dans le portail Cloud App Security et appliquer des stratégies sur la session.

## <a name="device-identification"></a>Identification de l’appareil

Cloud App Security vous permet d’identifier et de créer des stratégies proxy en fonction de l’état de l’appareil. Pour déterminer si un appareil est géré ou non, Cloud App Security utilise les éléments suivants :
 - Appareils Intune conformes* 
 - Appareils joints à un domaine Azure AD* 
 - Déploiement de certificats clients (pour toutes les applications)

* Disponible uniquement pour les applications Azure AD où l’accès conditionnel est disponible

## <a name="architecture"></a>Architecture

L’intégration aux fonctionnalités du proxy est simplifiée avec Azure Active Directory. Vous pouvez également utiliser des appareils joints à un domaine Azure AD et des appareils Intune conformes pour identifier facilement les appareils pendant la création de stratégie. 

Pour définir d’autres fournisseurs d’identité et applications qui fonctionnent avec le proxy, ils doivent être configurés afin de rediriger les demandes de connexion vers le proxy.

Par ailleurs, pour identifier les appareils gérés, le proxy peut demander des certificats clients aux appareils gérés. Une fois qu’un certificat client est reçu par le proxy, l’appareil est considéré comme étant géré et les stratégies sur les appareils gérés et non gérés sont appliquées.

Pour plus d'informations sur le processus de déploiement, consultez [Déploiement du proxy](proxy-deployment.md).

![Architecture du proxy Cloud App Security](./media/proxy-architecture.png)

## <a name="user-login-flow"></a>Flux de connexion de l’utilisateur

1. L’utilisateur envoie une demande au fournisseur d’identité et fournit des informations d’identification.
2.  Si l’accès est autorisé, le fournisseur d’identité redirige l’utilisateur vers le proxy Cloud App Security.
3.  Si l’utilisateur a installé un certificat client et qu’une stratégie appropriée détermine si les appareils sont gérés ou non, l’utilisateur est invité à fournir des certificats clients. Dans les deux cas, une stratégie d’accès est évaluée.
4.   À ce stade, il existe 3 options possibles :
    -   L’utilisateur est autorisé à accéder à l’application
    -   L’utilisateur ne peut pas accéder à l’application
    -   L’utilisateur est autorisé à accéder à l’application, mais en mode surveillé
        -   Dans ce cas, l’utilisateur est redirigé à nouveau vers le proxy Cloud App Security, qui surveille l’intégralité de la session entre l’utilisateur et l’application. Pendant la surveillance, le proxy évalue les stratégies de session et peut effectuer des actions de blocage en conséquence.

>[!NOTE]
> Le diagramme ci-dessus représente une *Connexion lancée par le fournisseur d’identité*. Si l’utilisateur commence à partir de l’application, c’est-à-dire une *Connexion lancée par le fournisseur de service*, il est dirigé vers le proxy Cloud App Security, puis vers le fournisseur d’identité, avant de suivre le flux de la *Connexion lancée par le fournisseur d’identité*.

## <a name="managed-devices-flow"></a>Flux des appareils gérés

Pour identifier les appareils gérés et non gérés par Azure AD, le proxy utilise le mécanisme des certificats clients. Ce mécanisme fonctionne de la façon suivante :

1   Si l’utilisateur a installé un certificat client sur son appareil et qu’une stratégie appropriée détermine si les appareils sont gérés ou non.
   -   Quand l’utilisateur arrive dans la page du proxy pendant la phase de connexion, le proxy demande un certificat client à l’appareil de l’utilisateur.

   -   L’appareil de l’utilisateur est invité à fournir le certificat client et si ce dernier est approuvé, il est envoyé au proxy.

   -   Ensuite, le proxy authentifie le certificat client par rapport au certificat racine fourni par l’administrateur.

   -   Si le certificat client fourni par l’appareil est correctement authentifié avec le certificat racine, l’appareil est considéré comme étant géré.

-   Si l’une des phases précédentes n’est pas effectuée, l’appareil est considéré étant non géré.



## <a name="see-also"></a>Voir aussi  
[Déploiement du proxy](proxy-deployment.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  