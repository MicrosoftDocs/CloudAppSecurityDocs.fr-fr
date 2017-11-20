---
title: "Protéger avec le proxy Microsoft Cloud App Security | Microsoft Docs"
description: Cette rubrique fournit des informations sur le fonctionnement du proxy Cloud App Security.
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/13/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 35a43120-bf67-4cf9-9b48-ebe157dbbd18
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 6174cfe5fc0c5ba1bbde2b1f68234f727c7db223
ms.sourcegitcommit: eb4e70b6fa15cfff01932a711cecee38f67bc058
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2017
---
# <a name="protect-apps-with-microsoft-cloud-app-security-proxy"></a>Protéger des applications avec le proxy Microsoft Cloud App Security

> [!NOTE]
> Il s’agit d’une fonctionnalité en préversion.


Dans l’espace de travail actuel, souvent il ne suffit pas de savoir ce qui se passe dans votre environnement cloud après coup, vous devez pouvoir stopper les violations de sécurité et les fuites en temps réel, avant que les employés exposent par inadvertance ou intentionnellement vos données et votre organisation. Il est important d’autoriser les utilisateurs de votre organisation à accéder à la plupart des services et outils des applications cloud, et de les laisser apporter leurs propres appareils au travail. En même temps, vous avez besoin d’outils pour protéger votre organisation contre les fuites et le vol de données, en temps réel. Avec Azure Active Directory, le proxy Cloud App Security offre ces fonctionnalités dans une expérience globale et intégrée.

## <a name="how-it-works"></a>Fonctionnement

Le proxy Cloud App Security est intégré à l’accès conditionnel Azure AD. L’accès conditionnel Azure AD vous permet d’appliquer des contrôles d’accès sur les applications de votre organisation en fonction de certaines conditions. Ces conditions définissent à *quelles personnes* (par exemple, un utilisateur ou un groupe d’utilisateurs), à *quelles applications* (applications cloud) et à *quels endroits* (emplacements et réseaux) une stratégie d’accès conditionnel est appliquée. Une fois que vous avez déterminé les conditions, vous pouvez diriger les utilisateurs vers le proxy Cloud App Security où vous pouvez appliquer un contrôle de session.

Une fois que l’utilisateur est dirigé vers le proxy Cloud App Security, ses sessions d’application peuvent être surveillées et contrôlées en temps réel selon des stratégies de session. Les stratégies de session sont utilisées au sein du portail Cloud App Security pour affiner les filtres de session et définir les actions à effectuer sur un utilisateur. Avec les stratégies de session, vous pouvez :

-   **Bloquer en cas de téléchargement** : vous pouvez bloquer le téléchargement de documents sensibles. Par exemple, sur les appareils non gérés.

-   **Protéger en cas de téléchargement** : au lieu de bloquer le téléchargement des documents sensibles, vous pouvez exiger que les documents soient protégés par chiffrement lors de leur téléchargement. Ainsi, vous êtes sûr que le document est protégé et que l’accès utilisateur est authentifié, si les données sont téléchargées sur un appareil non approuvé. 

-   **Limiter les sessions utilisateur à partir des réseaux hors entreprise** : les utilisateurs accédant à une application protégée à partir d’un emplacement qui ne fait pas partie de votre réseau d’entreprise se voient attribuer un accès restreint et le téléchargement de documents sensibles est bloqué ou protégé.

-   **Surveiller les sessions utilisateur de confiance basse** : les utilisateurs à risque sont surveillés quand ils se connectent à des applications et leurs actions sont journalisées depuis la session. Vous pouvez examiner et analyser le comportement des utilisateurs pour comprendre où et dans quelles conditions les stratégies de session devront être appliquées à l’avenir. 

### <a name="how-session-control-works"></a>Fonctionnement du contrôle de session

Le contrôle de session du proxy repose sur l’accès conditionnel. Une fois que vous contrôlez l’accès à une application, vous pouvez rediriger les sessions utilisateur vers le contrôle de session du proxy au lieu de les rediriger directement vers l’application. Dès lors, les demandes de l’utilisateur et les réponses passent par le proxy au lieu de passer directement par l’application.

Pour garder l’utilisateur dans la session, le proxy remplace tous les scripts Java, URL et cookies appropriés dans la session de l’application par des URL de proxy. Par exemple, si l’application retourne une page avec des liens dont les domaines se terminent par myapp.com, le proxy remplace ces liens par des domaines se terminant par quelque chose comme : myapp.com.us.cas.ms. 

Cette méthode ne vous oblige pas à installer quoi que ce soit sur l’appareil. Cette approche est idéale pour surveiller des sessions à partir d’appareils non gérés. 

Une fois qu’une session passe par le proxy, celui-ci peut effectuer les opérations suivantes :
1. Inspecter le trafic à la recherche des activités des utilisateurs
3. Afficher les activités identifiées dans le portail du proxy Cloud App Security
2. Enregistrer les journaux de trafic et les analyser
3. Permettre à l’administrateur d’exporter les journaux de trafic
4. Appliquer des stratégies sur la session

## <a name="managed-device-identification"></a>Identification des appareils gérés

Le proxy vous permet de créer des stratégies qui déterminent si un appareil est géré ou non et qui en tiennent compte. Pour déterminer si un appareil est géré ou non, le proxy se sert de ce qui suit :

-   Appareils conformes 
-   Appareils joints à un domaine 
-   Déploiement de certificats clients
 
 
### <a name="compliant-and-domain-joined-devices"></a>Appareils conformes et joints à un domaine
L’accès conditionnel Azure AD permet aux informations sur les appareils conformes et joints à un domaine d’être directement transmises au proxy Cloud App Security. À partir de là, vous pouvez développer une stratégie de session qui utilise l’état de l’appareil en tant que filtre.
Pour plus d’informations, consultez [Présentation de la gestion des appareils dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-introduction). 

### <a name="client-certificate-authenticated-devices"></a>Appareils authentifiés par certificat client

Le mécanisme d’identification des appareils par le proxy peut exiger une authentification desdits appareils à l’aide de certificats clients. Cela vous permet soit d’exploiter les certificats clients existants déjà déployés dans votre organisation, soit de déployer de nouveaux certificats clients sur les appareils gérés, puis d’utiliser la présence de ces certificats pour définir des stratégies d’accès et de session. Pour plus d’informations sur la façon de déployer des certificats clients, consultez [Déployer un proxy pour les applications Azure AD](proxy-deployment-aad.md).
 
## <a name="supported-apps-and-clients"></a>Applications et clients pris en charge

Le proxy prend actuellement en charge les applications configurées avec l’authentification unique SAML dans Azure AD. De plus, le contrôle de session n’est pas automatiquement disponible pour toutes les applications. L’équipe Cloud App Security a testé de nombreuses applications populaires avec le contrôle de session. D’autres applications peuvent nécessiter un processus d’intégration effectué avec le client.
En termes de clients, le contrôle de session est disponible sur tous les navigateurs de toutes les plateformes majeures. Toutefois, les applications mobiles et les applications de bureau ne sont pas prises en charge. 

> [!NOTE]
> Les applications Office 365 ne sont pas configurées avec le format SAML si bien qu’elles ne sont pour le moment pas prises en charge.


## <a name="see-also"></a>Voir aussi  
[Déployer le proxy Cloud App Security](proxy-deployment-aad.md)   
[Pour obtenir du support technique, consultez la page Support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  

