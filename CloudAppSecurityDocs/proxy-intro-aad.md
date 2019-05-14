---
title: Protéger avec le contrôle d’application par accès conditionnel Microsoft Cloud App Security
description: Cet article fournit des informations sur le fonctionnement du proxy inverse du contrôle d’application par accès conditionnel de Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 1/29/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 35a43120-bf67-4cf9-9b48-ebe157dbbd18
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: c3da25124129097a0433dc5e8f312de9d73f9440
ms.sourcegitcommit: 9f0c562322394a3dfac7f1d84286e673276a28b1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65568968"
---
# <a name="protect-apps-with-microsoft-cloud-app-security-conditional-access-app-control"></a>Protéger les applications avec le Contrôle d’accès conditionnel aux applications Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

>[!div class="step-by-step"]
[SUIVANT : Déployer le contrôle d’application par accès conditionnel »](proxy-deployment-aad.md)


En entreprise, le fait de savoir ce qui s’est passé dans votre environnement cloud après coup n’est pas suffisant. En effet, vous devez pouvoir arrêter les violations et les fuites en temps réel, avant que les employés ne puissent, par inadvertance ou intentionnellement, compromettre vos données et votre organisation. Il est important d’autoriser les utilisateurs de votre organisation à accéder à la plupart des services et outils des applications cloud, et de leur permettre d’apporter leurs propres appareils au travail. En même temps, vous avez besoin d’outils pour protéger votre organisation contre les fuites et le vol de données, en temps réel. Avec Azure Active Directory, Microsoft Cloud App Security offre ces fonctionnalités dans une expérience globale et intégrée avec le Contrôle d’accès conditionnel aux applications.

> [!NOTE]
> Pour utiliser la fonctionnalité Contrôle d’application par accès conditionnel de Cloud App Security, vous devez disposer d’une [licence Azure Active Directory P1](https://azure.microsoft.com/pricing/details/active-directory/) et d’un abonnement Microsoft Cloud App Security actif.
>

## <a name="how-it-works"></a>Fonctionnement

Le contrôle d’application par accès conditionnel utilise une architecture de proxy inverse. En outre, il est intégré de manière unique à l’accès conditionnel Azure AD. L’accès conditionnel Azure AD vous permet d’appliquer des contrôles d’accès sur les applications de votre organisation en fonction de certaines conditions. Ces conditions définissent à *quelles personnes* (utilisateur ou groupe d’utilisateurs), à *quelles applications* (applications cloud) et à *quels endroits* (emplacements et réseaux) une stratégie d’accès conditionnel est appliquée. Une fois que vous avez déterminé les conditions, vous pouvez router les utilisateurs vers Microsoft Cloud App Security, ce qui vous permet de protéger des données avec le contrôle d’application par accès conditionnel en appliquant des contrôles d’accès et de session.

Le Contrôle d’accès conditionnel aux applications active l’accès aux applications des utilisateurs et les sessions à surveiller et à contrôler en temps réel, en fonction des stratégies d’accès et de session. Les stratégies d’accès et de session sont utilisées dans le portail Cloud App Security pour affiner les filtres et définir les actions à effectuer sur un utilisateur. Avec les stratégies d’accès et de session, vous pouvez :

- **Bloquer en cas de téléchargement** : Vous pouvez bloquer le téléchargement de documents sensibles. Par exemple, sur les appareils non gérés.

- **Protéger en cas de téléchargement** : Au lieu de bloquer le téléchargement des documents sensibles, vous pouvez exiger que les documents soient protégés par chiffrement lors de leur téléchargement. Ce chiffrement garantit que le document est protégé et que l’accès utilisateur est authentifié, si les données sont téléchargées sur un appareil non approuvé. 

- **Surveiller les sessions utilisateur de confiance basse** : Les utilisateurs à risque sont surveillés lorsqu’ils se connectent à des applications et leurs actions sont journalisées depuis la session. Vous pouvez examiner et analyser le comportement des utilisateurs pour comprendre où et dans quelles conditions les stratégies de session devront être appliquées à l’avenir. 

- **Bloquer l’accès** : Vous pouvez bloquer complètement l’accès à des applications spécifiques pour les utilisateurs provenant d’appareils non gérés ou de réseaux qui ne sont pas des réseaux de l’entreprise.

- **Créer un mode Lecture seule** : En supervisant et en bloquant des activités personnalisées dans l’application, vous pouvez créer un mode Lecture seule pour certaines applications et certains utilisateurs.  

- **Limiter les sessions utilisateur à partir des réseaux hors entreprise** : Les utilisateurs accédant à une application protégée à partir d’un emplacement qui ne fait pas partie de votre réseau d’entreprise se voient attribuer un accès restreint. Le téléchargement des documents sensibles est bloqué ou protégé.

### <a name="how-session-control-works"></a>Fonctionnement du contrôle de session

La création d’une stratégie de session avec le Contrôle d’accès conditionnel aux applications vous permet de contrôler des sessions utilisateur en redirigeant l’utilisateur via un proxy inversé plutôt que directement vers l’application. Dès lors, les requêtes et réponses de l’utilisateur passent par Microsoft Cloud App Security plutôt que directement par l’application.

Pour garder l’utilisateur dans la session, les URL, scripts Java et cookies appropriés dans la session de l’application sont remplacés par des URL Microsoft Cloud App Security. Par exemple, si l’application retourne une page avec des liens dont les domaines se terminent par myapp.com, le lien est remplacé par des domaines se terminant par quelque chose comme : myapp.com.us.cas.ms 

Cette méthode ne vous oblige pas à installer un programme sur l’appareil. Elle est idéale pour superviser les sessions sur les appareils non gérés. 

Une fois qu’une session est redirigée via Microsoft Cloud App Security, les actions suivantes peuvent être effectuées :

1. Inspecter le trafic à la recherche des activités des utilisateurs
2. Afficher les activités identifiées dans le journal d’activité de Microsoft Cloud App Security
3. Enregistrer les journaux de trafic et les analyser
4. Permettre à l’administrateur d’exporter les journaux de trafic
5. Appliquer des stratégies sur la session

## <a name="managed-device-identification"></a>Identification des appareils gérés

Le Contrôle d’accès conditionnel aux applications vous permet de créer des stratégies qui déterminent si un appareil est géré ou non. Pour déterminer si un appareil est géré ou non, la fonctionnalité utilise ce qui suit :

- Appareils conformes
- Appareils joints à un domaine
- Déploiement de certificats clients
 
### <a name="compliant-and-domain-joined-devices"></a>Appareils conformes et joints à un domaine

L’accès conditionnel Azure AD permet aux informations sur les appareils conformes et joints à un domaine d’être directement transmises à Microsoft Cloud App Security. À partir de là, vous pouvez développer une stratégie d’accès ou de session qui utilise l’état de l’appareil comme filtre.
Pour plus d’informations, consultez [Présentation de la gestion des appareils dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-introduction). 

### <a name="client-certificate-authenticated-devices"></a>Appareils authentifiés par certificat client

Le mécanisme d’identification des appareils peut exiger une authentification desdits appareils à l’aide de certificats clients. Vous pouvez utiliser des certificats clients existants déjà déployés dans votre organisation ou déployer de nouveaux certificats clients sur des appareils gérés. Vous profitez ensuite de la présence de ces certificats pour définir des stratégies d’accès et de session. Pour plus d’informations sur la façon de déployer des certificats clients, consultez [Déployer un Contrôle d’accès conditionnel aux applications pour les applications Azure AD](proxy-deployment-aad.md).
 
## <a name="supported-apps-and-clients"></a>Applications et clients pris en charge

Le contrôle d’application par accès conditionnel prend en charge les applications SAML et Open ID Connect configurées avec l’authentification unique, ainsi que les applications web hébergées localement qui sont configurées avec le [proxy d’application Azure AD](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).
> [!NOTE]
> Le contrôle d’application par accès conditionnel prend également en charge des applications qui sont configurées avec des fournisseurs d’identité non-Azure AD. Pour plus d'informations sur ce scénario, envoyez un e-mail à mcaspreview@microsoft.com.

**Le contrôle de session est disponible sur tous les navigateurs de toutes les plateformes majeures, quel que soit le système d’exploitation**. Les applications mobiles et les applications de bureau peuvent également être bloquées ou autorisées. Avec l’intégration en mode natif à Azure AD, toutes les applications qui sont configurées avec des applications SAML ou Open ID Connect avec l’authentification unique dans Azure AD peuvent être prises en charge, notamment les applications proposées suivantes :

- AWS
- Azure DevOps (Visual Studio Team Services) (préversion)
- Portail Azure (préversion)
- Box
- Concur
- CornerStone on Demand
- DocuSign
- Dropbox
- Egnyte
- Exchange Online (préversion)
- G Suite
- GitHub
- HighQ
- JIRA/Confluence
- OneDrive Entreprise (préversion)
- LinkedIn Learning
- Power BI (préversion)
- Salesforce
- ServiceNow
- SharePoint Online (préversion)
- Slack
- Tableau
- Microsoft Teams (préversion)
- Workday
- Workiva
- Workplace by Facebook
- Yammer (préversion)




De nouvelles applications sont intégrées au contrôle de session en continu. Si vous souhaitez en savoir plus sur une application qui n’est pas mentionnée ici, [envoyez-nous des informations sur cette application](mailto:casfeedback@microsoft.com). Envoyez-nous également le cas d’usage qui vous intéresse pour que nous puissions l’intégrer.



>[!div class="step-by-step"]
[SUIVANT : Déployer le contrôle d’application par accès conditionnel »](proxy-deployment-aad.md)


## <a name="next-steps"></a>Étapes suivantes
[Déployer le Contrôle d’applications par accès conditionnel pour les applications Azure AD](proxy-deployment-aad.md)   

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)  
  


