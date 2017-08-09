---
title: Utilisation du proxy Cloud App Security | Microsoft Docs
description: Cette rubrique fournit des informations sur le fonctionnement du proxy Cloud App Security.
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/31/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 28317b70-1851-4610-b1d6-863bc5994bb6
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 82e1ee0b5161dce88db815dc8eea06340bdbc532
ms.sourcegitcommit: f9851779aa15b11f559e56ac818f1333f027c000
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2017
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

### <a name="access-control"></a>Contrôle d’accès
<more information about what is access control including examples> Le contrôle d’accès du proxy vous permet de créer des stratégies d’accès puissantes pour vos applications cloud et vous fournit les fonctionnalités suivantes :

Pour utiliser le contrôle d’accès dans Cloud App Security, déployez le proxy en apportant quelques modifications à la configuration de votre fournisseur d’identité existant et définissez une stratégie pour contrôler vos applications cloud. 

> [!NOTE]
> -  Il est inutile de modifier les stratégies existantes du fournisseur d’identité.

#### <a name="supported-apps-and-identity-providers"></a>Applications et fournisseurs d’identité pris en charge

Le contrôle d’accès du proxy est conçu pour prendre en charge tous les fournisseurs d’identité et applications prenant en charge les protocoles SAML ou WS-Federation. L’équipe Cloud App Security teste les principaux fournisseurs d’identité et applications avec les fonctionnalités de contrôle d’accès. Toutefois, en raison du grand nombre de fournisseurs d’identité et d’applications cloud, toutes les combinaisons de fournisseurs d’identité et applications ne sont pas testées. Nous vous recommandons de tester le processus d’authentification unique avec votre fournisseur d’identité et votre application dans environnement de bac à sable ou de test avant de le déployer dans un environnement de production.

### <a name="session-control"></a>Contrôle de session

Le contrôle de session est une couche supplémentaire de contrôle fournie par le proxy. Il permet un contrôle en temps réel plus granulaire de vos applications cloud. Au lieu de définir une stratégie globale pour autoriser ou bloquer l’accès à une application donnée, vous pouvez autoriser l’accès, puis, en surveillant chaque session utilisateur dans l’application, limiter l’accès de différentes manières. Par exemple, vous pouvez décider que pour certains appareils ou pour les sessions provenant d’emplacements spécifiques, vous voulez autoriser l’utilisateur à accéder à l’application, mais limiter le téléchargement des fichiers sensibles.

#### <a name="supported-apps-and-flows"></a>Applications et flux pris en charge

Actuellement, le contrôle de session permet de bloquer le téléchargement de fichiers et l’exportation de rapports dans Salesforce.com. Vous pouvez créer des stratégies en fonction de l’utilisateur, de l’emplacement et de l’appareil, de même qu’en fonction du contenu que vous voulez télécharger.

Par ailleurs, cette version prend en charge les sessions limitées pour les utilisateurs qui se connectent à partir d’un navigateur. Par exemple, si vous voulez limiter l’accès pour les sessions provenant d’applications natives, vous devez définir une stratégie d’accès pour bloquer ces accès quand le filtre **Étiquette agent utilisateur** est égal à **Client natif**.

Salesforce est testé sur tous les flux normaux. Toutefois, comme Salesforce propose de nombreuses applications tierces, certaines de ces applications tierces peuvent ne pas avoir été testées et ne pas fonctionner avec le contrôle de session ou même entraîner le blocage de certaines pages. Pour vérifier qu’il s’agit effectivement d’un problème d’application tierce, supprimez toutes les applications tierces et testez l’application avec le contrôle de session. Si tout fonctionne correctement, ajoutez les applications tierces une par une jusqu'à ce que vous identifiez l’application problématique. 

## <a name="device-management"></a>Gestion des appareils

Cloud App Security vous permet d’identifier et de créer des stratégies proxy en fonction de l’état de l’appareil. Pour déterminer si un appareil est géré ou non, Cloud App Security utilise le mécanisme des certificats clients, selon lequel des certificats clients sont déployés sur les appareils gérés de votre organisation. Quand les utilisateurs se connectent à une application, ils doivent fournir le certificat client installé sur leur appareil. Si un certificat client est fourni, Cloud App Security considère que l’appareil est géré. 
> [!NOTE]
>  L’utilisateur peut choisir de refuser d’envoyer les certificats clients et, dans ce cas, l’appareil est considéré comme étant non géré.
<OK, donc, vous savez s’il est géré ou non - qu’est-ce que vous en faites ?>

### <a name="supported-browsers-and-native-apps"></a>Applications natives et navigateurs pris en charge

Le proxy Cloud App Security vous permet de... à partir de certificats clients...

Les certificats clients sont un mécanisme bien connu que les développeurs de navigateurs et les développeurs d’applications natives peuvent décider d’implémenter ou non. La plupart des navigateurs sur la plupart des plateformes les prennent en charge, mais en ce qui concerne les applications natives, c’est plus compliqué.

La prise en charge des certificats clients dans les applications natives, c’est-à-dire les applications de bureau et les applications mobiles, peut varier selon la plateforme et même selon l’état de l’appareil. Par exemple, dans Salesforce1, l’application mobile de Salesforce, les certificats clients fonctionnent uniquement si une gestion des appareils mobiles est déployée sur l’appareil et que Salesforce1 est configuré pour envoyer des certificats clients.

Les certificats clients ont été testés avec succès sur Internet Explorer, Edge, Chrome, Safari et Firefox sur les dernières versions de Windows, OSX, Android et iOS (chacun avec les navigateurs appropriés).

> [!NOTE]
> Dans iOS, seul le navigateur Safari fonctionne avec des certificats clients.

Même dans les cas où les navigateurs ou les applications natives prennent en charge les certificats clients, il peut arriver que les utilisateurs rencontrent des problèmes pour fournir le certificat, par exemple, si un utilisateur refuse d’envoyer un certificat client une fois, le navigateur ou l’application native peut mémoriser ce choix et ne plus l’inviter à fournir de certificat. Pour résoudre ces problèmes, nous vous recommandons de fermer toutes les instances ouvertes du navigateur et d’en ouvrir de nouvelles, ou de supprimer tous les cookies et de réessayer.

D’autre part, certains navigateurs et applications natives prennent en charge l’option qui permet de supprimer la fenêtre contextuelle demandant les certificats clients et les envoie automatiquement à la place.

En général, nous vous recommandons de tester les demandes de certificat client des utilisateurs sans appliquer de stratégies, mais en mode de surveillance uniquement. Vous pouvez le faire en créant une stratégie **Journaliser uniquement** pour identifier les appareils gérés.

## <a name="architecture"></a>Architecture

Le proxy est intégré à votre fournisseur d’identité et à l’application, et les deux doivent être configurés pour rediriger les demandes de connexion au proxy.

Par ailleurs, pour identifier les appareils gérés, le proxy peut demander des certificats clients aux appareils gérés. Une fois qu’un certificat client est reçu par le proxy, l’appareil est considéré comme étant géré et les stratégies sur les appareils gérés et non gérés sont appliquées.

Pour plus d'informations sur le processus de déploiement, consultez la section Déploiement.

![Architecture du proxy Cloud App Security](./media/proxy-architecture.png)

## <a name="user-login-flow"></a>Flux de connexion de l’utilisateur

Le schéma ci-dessus décrit une connexion qui démarre à partir du fournisseur d’identité, connue aussi sous le nom de *Connexion lancée par le fournisseur d’identité*. Si l’utilisateur commence à partir de l’application, on parle de *Connexion lancée par le fournisseur de service*, il est dirigé vers le proxy Cloud App Security qui le dirige ensuite vers le fournisseur d’identité. Le reste du processus de connexion est semblable au flux de la *Connexion lancée par le fournisseur d’identité*.

Voici le flux de la *Connexion lancée par le fournisseur d’identité* :
-   L’utilisateur envoie une demande au fournisseur d’identité et fournit des informations d’identification

-   Si l’accès est autorisé, le fournisseur d’identité redirige l’utilisateur vers le proxy Cloud App Security

-   Si l’utilisateur a installé un certificat client et qu’une stratégie appropriée détermine si les appareils sont gérés ou non, l’utilisateur est invité à fournir des certificats clients. Dans les deux cas, une stratégie d’accès est évaluée

-   À ce stade, il existe 3 options possibles :

    -   L’utilisateur est autorisé à accéder à l’application

    -   L’utilisateur ne peut pas accéder à l’application

    -   L’utilisateur est autorisé à accéder à l’application, mais en mode surveillé

        -   Dans ce cas, l’utilisateur est redirigé à nouveau vers le proxy Cloud App Security, qui surveille l’intégralité de la session entre l’utilisateur et l’application

        -   Pendant la surveillance, le proxy évalue les stratégies de session et peut effectuer des actions de blocage en conséquence

## <a name="how-access-control-works"></a>Fonctionnement du contrôle d’accès

Dans le cadre du déploiement du proxy, vous devez modifier les configurations du fournisseur d’identité et de l’application que vous voulez contrôler. Cela inclut des changements d’URL pour que le fournisseur d’identité et l’application redirigent les demandes de connexion vers le proxy. Par ailleurs et si cela est nécessaire, les certificats sont également remplacés.

Une fois ces étapes terminées, tous les événements de connexion passent par le proxy et ce dernier peut décider s’ils sont autorisés à accéder à l’application, si l’accès est refusé ou si l’accès est autorisé en mode surveillé. Notez qu’à ce stade, le proxy peut demander des certificats clients à l’appareil et utiliser l’état de l’appareil pour prendre des décisions en matière de stratégie.

## <a name="how-session-control-works"></a>Fonctionnement du contrôle de session

Le contrôle de session du proxy repose sur le contrôle d’accès. Une fois que vous contrôlez l’accès à une application, vous pouvez décider, en fonction des stratégies d’accès, de surveiller la session en redirigeant ses sessions vers le contrôle de session du proxy. Dès lors, les demandes de l’utilisateur et les réponses passent par le proxy au lieu de passer par l’application directement.

Pour garder l’utilisateur dans la session, le proxy remplace tous les scripts Java, URL et cookies appropriés dans l’application par des pages dupliquées dans le proxy. Par exemple : si l’application retourne une page avec des liens qui se terminent par *myapp.com*, le proxy les remplace par des pages qui se terminent par quelque chose comme *myapp.com.cas.ms*.

Quand une session est dirigée vers le proxy, ce dernier peut inspecter le trafic, afficher les événements qu’il identifie dans le portail Cloud App Security et appliquer des stratégies sur la session.

## <a name="how-identifying-managed-devices-works"></a>Fonctionnement de l’identification des appareils gérés

Pour identifier les appareils gérés, le proxy utilise le mécanisme des certificats clients. Ce mécanisme fonctionne de la façon suivante :

-   Si l’utilisateur a installé un certificat client sur son appareil et qu’une stratégie appropriée détermine si les appareils sont gérés ou non.

    -   Quand l’utilisateur arrive dans la page du proxy pendant la phase de connexion, le proxy demande un certificat client à l’appareil de l’utilisateur.

    -   L’appareil de l’utilisateur est invité à fournir le certificat client et si ce dernier est approuvé, il est envoyé au proxy.

    -   Ensuite, le proxy authentifie le certificat client par rapport au certificat racine fourni par l’administrateur.

    -   Si le certificat client fourni par l’appareil est correctement authentifié avec le certificat racine, l’appareil est considéré comme étant géré.

-   Si l’une des phases précédentes n’est pas effectuée, l’appareil est considéré étant non géré.



## <a name="see-also"></a>Voir aussi  
[Déploiement du proxy](proxy-deployment.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  