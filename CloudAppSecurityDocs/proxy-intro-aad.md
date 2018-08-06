---
title: Protéger avec le Contrôle d’accès conditionnel aux applications Microsoft Cloud App Security | Microsoft Docs
description: Cette rubrique fournit des informations sur le fonctionnement du proxy inversé du Contrôle d’accès conditionnel aux applications de Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/5/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 35a43120-bf67-4cf9-9b48-ebe157dbbd18
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 94b44acb3335df4c1dceaa59308faa9fba20806e
ms.sourcegitcommit: b4bc20170a97e4fedc47cf67906a13aa0b70bcb6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2018
ms.locfileid: "39518157"
---
*S’applique à : Microsoft Cloud App Security*


# <a name="protect-apps-with-microsoft-cloud-app-security-conditional-access-app-control"></a>Protéger les applications avec le Contrôle d’accès conditionnel aux applications Microsoft Cloud App Security

>[!div class="step-by-step"]
[Suivant : Déployer le Contrôle d’accès conditionnel aux applications »](proxy-deployment-aad.md)


Dans l’espace de travail actuel, souvent il ne suffit pas de savoir ce qui se passe dans votre environnement cloud après coup, vous devez pouvoir stopper les violations de sécurité et les fuites en temps réel, avant que les employés exposent par inadvertance ou intentionnellement vos données et votre organisation. Il est important d’autoriser les utilisateurs de votre organisation à accéder à la plupart des services et outils des applications cloud, et de les laisser apporter leurs propres appareils au travail. En même temps, vous avez besoin d’outils pour protéger votre organisation contre les fuites et le vol de données, en temps réel. Avec Azure Active Directory, Microsoft Cloud App Security offre ces fonctionnalités dans une expérience globale et intégrée avec le Contrôle d’accès conditionnel aux applications.

## <a name="how-it-works"></a>Fonctionnement

Le Contrôle d’accès conditionnel aux applications utilise une architecture de proxy inversé et est intégré de manière unique avec un accès conditionnel Azure AD. L’accès conditionnel Azure AD vous permet d’appliquer des contrôles d’accès sur les applications de votre organisation en fonction de certaines conditions. Ces conditions définissent à *quelles personnes* (par exemple, un utilisateur ou un groupe d’utilisateurs), à *quelles applications* (applications cloud) et à *quels endroits* (emplacements et réseaux) une stratégie d’accès conditionnel est appliquée. Une fois que vous avez déterminé les conditions, vous pouvez acheminer les utilisateurs vers Microsoft Cloud App Security, où vous pouvez protéger des données avec le Contrôle d’accès conditionnel aux applications en appliquant des contrôles d’accès et de session.

Le Contrôle d’accès conditionnel aux applications active l’accès aux applications des utilisateurs et les sessions à surveiller et à contrôler en temps réel, en fonction des stratégies d’accès et de session. Les stratégies d’accès et de session sont utilisées dans le portail Cloud App Security pour affiner les filtres et définir les actions à effectuer sur un utilisateur. Avec les stratégies d’accès et de session, vous pouvez :

-   **Bloquer en cas de téléchargement** : vous pouvez bloquer le téléchargement de documents sensibles. Par exemple, sur les appareils non gérés.

-   **Protéger en cas de téléchargement** : au lieu de bloquer le téléchargement des documents sensibles, vous pouvez exiger que les documents soient protégés par chiffrement lors de leur téléchargement. Ainsi, vous êtes sûr que le document est protégé et que l’accès utilisateur est authentifié, si les données sont téléchargées sur un appareil non approuvé. 

-   **Surveiller les sessions utilisateur de confiance basse** : les utilisateurs à risque sont surveillés quand ils se connectent à des applications et leurs actions sont journalisées depuis la session. Vous pouvez examiner et analyser le comportement des utilisateurs pour comprendre où et dans quelles conditions les stratégies de session devront être appliquées à l’avenir. 

- **Bloquer l’accès** : vous pouvez bloquer complètement l’accès à des applications spécifiques pour les utilisateurs provenant d’appareils non gérés ou de réseaux qui ne sont pas des réseaux de l’entreprise.

- **Créer un mode Lecture seule** : en surveillant et en bloquant des activités personnalisées dans l’application, vous pouvez créer un mode Lecture seule pour certaines applications et certains utilisateurs.  

- **Limiter les sessions utilisateur à partir des réseaux hors entreprise** : les utilisateurs accédant à une application protégée à partir d’un emplacement qui ne fait pas partie de votre réseau d’entreprise se voient attribuer un accès restreint et le téléchargement de documents sensibles est bloqué ou protégé.

### <a name="how-session-control-works"></a>Fonctionnement du contrôle de session

La création d’une stratégie de session avec le Contrôle d’accès conditionnel aux applications vous permet de contrôler des sessions utilisateur en redirigeant l’utilisateur via un proxy inversé plutôt que directement vers l’application. Dès lors, les requêtes et réponses de l’utilisateur passent par Microsoft Cloud App Security plutôt que directement par l’application.

Pour garder l’utilisateur dans la session, les URL, scripts Java et cookies appropriés dans la session de l’application sont remplacés par des URL Microsoft Cloud App Security. Par exemple, si l’application retourne une page avec des liens dont les domaines se terminent par myapp.com, le lien est remplacé par des domaines se terminant par quelque chose comme : myapp.com.us.cas.ms 

Cette méthode ne vous oblige pas à installer quoi que ce soit sur l’appareil. Cette approche est idéale pour surveiller des sessions à partir d’appareils non gérés. 

Une fois qu’une session est redirigée via Microsoft Cloud App Security, les actions suivantes peuvent être effectuées :
1. Inspecter le trafic à la recherche des activités des utilisateurs
2. Afficher les activités identifiées dans le journal d’activité de Microsoft Cloud App Security
3. Enregistrer les journaux de trafic et les analyser
4. Permettre à l’administrateur d’exporter les journaux de trafic
5. Appliquer des stratégies sur la session

## <a name="managed-device-identification"></a>Identification des appareils gérés

Le Contrôle d’accès conditionnel aux applications vous permet de créer des stratégies qui déterminent si un appareil est géré ou non. Pour déterminer si un appareil est géré ou non, la fonction se sert de ce qui suit :

-   Appareils conformes 
-   Appareils joints à un domaine 
-   Déploiement de certificats clients
 
 
### <a name="compliant-and-domain-joined-devices"></a>Appareils conformes et joints à un domaine
L’accès conditionnel Azure AD permet aux informations sur les appareils conformes et joints à un domaine d’être directement transmises à Microsoft Cloud App Security. À partir de là, vous pouvez développer une stratégie d’accès ou de session qui utilise l’état de l’appareil comme filtre.
Pour plus d’informations, consultez [Présentation de la gestion des appareils dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-introduction). 

### <a name="client-certificate-authenticated-devices"></a>Appareils authentifiés par certificat client

Le mécanisme d’identification des appareils peut exiger une authentification desdits appareils à l’aide de certificats clients. Cela vous permet soit d’exploiter les certificats clients existants déjà déployés dans votre organisation, soit de déployer de nouveaux certificats clients sur les appareils gérés, puis d’utiliser la présence de ces certificats pour définir des stratégies d’accès et de session. Pour plus d’informations sur la façon de déployer des certificats clients, consultez [Déployer un Contrôle d’accès conditionnel aux applications pour les applications Azure AD](proxy-deployment-aad.md).
 
## <a name="supported-apps-and-clients"></a>Applications et clients pris en charge

Le Contrôle d’accès conditionnel aux applications prend actuellement en charge des applications configurées avec l’authentification unique SAML dans Azure AD. 

> [!NOTE]
> - Le contrôle d’application par accès conditionnel prend également en charge des applications qui sont configurées avec des fournisseurs d’identité non-Azure AD. Pour plus d'informations sur ce scénario, envoyez un e-mail à mcaspreview@microsoft.com.
> - Les applications Office 365 ne sont pas configurées avec le format SAML si bien qu’elles ne sont pour le moment pas prises en charge.

Le contrôle de session est disponible pour tous les navigateurs de toutes les principales plateformes (les applications de bureau et les applications mobiles peuvent aussi être bloquées ou autorisées). Avec l’intégration en mode natif à Azure AD, toutes les applications qui sont configurées avec l’authentification unique SAML dans Azure AD peuvent être prises en charge, notamment les applications proposées suivantes :

-   Salesforce

-   Box

-   G Suite

-   Workday

-   Slack

-   Workplace by Facebook

-   ServiceNow

-   JIRA/Confluence

-   AWS

-   Workiva

-   CornerStone on Demand

-   DocuSign

-   HighQ 

-   Concur

-   Tableau

-  Dropbox

-  Egnyte

-  GitHub

De nouvelles applications sont intégrées au contrôle de session en continu. Si vous êtes intéressé par une application spécifique qui n’est pas mentionnée ici, [envoyez-nous des détails sur l’application](mailto:casfeedback@microsoft.com) et le cas d’utilisation qui vous intéresse et nous l’intégrerons.



>[!div class="step-by-step"]
[Suivant : Déployer le Contrôle d’accès conditionnel aux applications »](proxy-deployment-aad.md)


## <a name="see-also"></a>Voir aussi  
[Déployer le Contrôle d’applications par accès conditionnel pour les applications Azure AD](proxy-deployment-aad.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  


