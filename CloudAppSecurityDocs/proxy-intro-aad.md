---
title: Protéger avec le contrôle d’application par accès conditionnel Microsoft Cloud App Security
description: Cet article fournit des informations sur le fonctionnement du proxy inverse du contrôle d’application par accès conditionnel de Cloud App Security.
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
ms.assetid: 35a43120-bf67-4cf9-9b48-ebe157dbbd18
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: fca34e1bb6a9f83928ef3a4eaf388090468ce06a
ms.sourcegitcommit: ee00e0033bf45a5f795bfd3e1d71fa1f70f97acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67511368"
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

- **Empêcher l’exfiltration de données**: Vous pouvez bloquer la téléchargement, couper, copier et imprimer des documents sensibles sur, par exemple, les appareils non gérés.

- **Protéger en cas de téléchargement** : Au lieu de bloquer le téléchargement des documents sensibles, vous pouvez exiger des documents d’être étiquetés et protégés avec Azure Information Protection. Cette action garantit que le document est protégé et l’accès utilisateur est limité dans une session potentiellement dangereuse.

- **Empêcher le téléchargement de fichiers sans étiquette**: Avant d’un fichier sensible est chargé, distribué utilisé par d’autres, il est important de s’assurer que le fichier comporte la bonne étiquette et la protection. Vous pouvez vous assurer que les fichiers sans étiquette contenant des données sensibles sont bloqués à partir d’en cours de téléchargement jusqu'à ce que l’utilisateur classifie le contenu.

- **Analyser les sessions utilisateur pour la conformité**: Les utilisateurs à risque sont surveillés lorsqu’ils se connectent à des applications et leurs actions sont journalisées depuis la session. Vous pouvez examiner et analyser le comportement des utilisateurs pour comprendre où et dans quelles conditions les stratégies de session devront être appliquées à l’avenir.

- **Bloquer l’accès** : Vous pouvez définir de façon précise bloquer l’accès pour des applications spécifiques et des utilisateurs en fonction de plusieurs facteurs de risque. Par exemple, vous pouvez les bloquer si elles sont à l’aide de certificats de client comme une forme de gestion des appareils.

- **Bloquer les activités personnalisées**: Certaines applications possèdent des scénarios uniques qui comportent le risque, par exemple, l’envoi de messages contenant des données sensibles dans des applications telles que Microsoft Teams ou Slack. Dans ces types de scénarios, vous pouvez analyser les messages pour le contenu sensible et les bloquer en temps réel.

### <a name="how-session-control-works"></a>Fonctionnement du contrôle de session

La création d’une stratégie de session avec le Contrôle d’accès conditionnel aux applications vous permet de contrôler des sessions utilisateur en redirigeant l’utilisateur via un proxy inversé plutôt que directement vers l’application. Dès lors, les requêtes utilisateur et les réponses passent par Cloud App Security plutôt que directement à l’application.

Quand une session est protégée par un proxy, toutes les URL pertinentes et les cookies sont remplacés par Cloud App Security. Par exemple, si l’application retourne une page avec des liens dont les domaines se terminent par myapp.com, le lien est remplacé par des domaines se terminant par quelque chose comme : myapp.com.us.cas.ms

Cette méthode ne vous oblige à installer quoi que ce soit sur l’appareil idéale lors de la surveillance ou le contrôle de sessions à partir d’appareils non gérés ou les utilisateurs partenaires.

## <a name="managed-device-identification"></a>Identification des appareils gérés

Le Contrôle d’accès conditionnel aux applications vous permet de créer des stratégies qui déterminent si un appareil est géré ou non. Pour déterminer si un appareil est géré ou non, la fonctionnalité utilise ce qui suit :

- Appareils conformes
- Appareils joints à un domaine
- Déploiement de certificats clients
 
### <a name="compliant-and-domain-joined-devices"></a>Appareils conformes et joints à un domaine

L’accès conditionnel Azure AD permet aux informations sur les appareils conformes et joints à un domaine d’être directement transmises à Microsoft Cloud App Security. À partir de là, vous pouvez développer une stratégie d’accès ou de session qui utilise l’état de l’appareil comme filtre.
Pour plus d’informations, consultez [Présentation de la gestion des appareils dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-introduction). 

### <a name="client-certificate-authenticated-devices"></a>Appareils authentifiés par certificat client

Le mécanisme d’identification des appareils peut exiger une authentification desdits appareils à l’aide de certificats clients. Vous pouvez utiliser des certificats clients existants déjà déployés dans votre organisation ou déployer de nouveaux certificats clients sur des appareils gérés. Vous profitez ensuite de la présence de ces certificats pour définir des stratégies d’accès et de session.

Les certificats clients SSL sont vérifiés via une chaîne d’approbation. Vous pouvez télécharger une racine X.509 ou une autorité de certification intermédiaire (CA) mis en forme dans le format du certificat PEM. Ces certificats doivent contenir la clé publique de l’autorité de certification, qui est ensuite utilisée pour signer les certificats de client présentés pendant une session.

Une fois que le certificat est chargé et une stratégie appropriée est configurée, lorsqu’une session applicable traverse le contrôle d’accès conditionnel, le point de terminaison Cloud App Security demande le navigateur pour présenter des certificats client SSL. Le navigateur fait Office de client SSL certificats qui sont installés avec une clé privée. Cette combinaison de certificat et la clé privée est effectuée en utilisant le PKCS #12 format de fichier, généralement .p12 ou .pfx.

Lorsqu’une vérification de certificat client est effectuée, Cloud App Security vérifie les conditions suivantes :

1. Le certificat client sélectionné est valide et trouve sous la racine appropriée ou l’autorité de certification intermédiaire.
1. Le certificat n’est pas révoqué (si la CRL est activée).

Pour plus d’informations sur la façon de déployer des certificats clients, consultez [Déployer un Contrôle d’accès conditionnel aux applications pour les applications Azure AD](proxy-deployment-aad.md).

## <a name="supported-apps-and-clients"></a>Applications et clients pris en charge

Le contrôle d’application par accès conditionnel prend en charge les applications SAML et Open ID Connect configurées avec l’authentification unique, ainsi que les applications web hébergées localement qui sont configurées avec le [proxy d’application Azure AD](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).
> [!NOTE]
> Le contrôle d’application par accès conditionnel prend également en charge des applications qui sont configurées avec des fournisseurs d’identité non-Azure AD. Pour plus d'informations sur ce scénario, envoyez un e-mail à mcaspreview@microsoft.com.

**Le contrôle de session est disponible sur tous les navigateurs de toutes les plateformes majeures, quel que soit le système d’exploitation**. Nous vous recommandons d’utiliser Internet Explorer 11, Microsoft Edge (dernière version), Google Chrome (dernière version), Mozilla Firefox (dernière version) ou Apple Safari (dernière version). Les applications mobiles et les applications de bureau peuvent également être bloquées ou autorisées. En intégrant en mode natif avec Azure AD, n’importe quelle application qui est configurée avec SAML ou Open ID Connect peut être self-intégrée. En outre, les applications suivantes sont proposées par Cloud App Security et déjà intégré et prêt à utiliser dans n’importe quel client :

- AWS
- Azure DevOps (Visual Studio Team Services)
- Portail Azure (préversion)
- Box
- Concur
- CornerStone on Demand
- DocuSign
- Dropbox
- Dynamics 365 CRM (version préliminaire)
- Egnyte
- Exchange Online
- G Suite
- GitHub
- HighQ
- JIRA/Confluence
- OneDrive Entreprise
- LinkedIn Learning
- Power BI
- Salesforce
- ServiceNow
- SharePoint Online
- Slack
- Tableau
- Microsoft Teams (préversion)
- Workday
- Workiva
- Workplace by Facebook
- Yammer (préversion)

Si vous êtes intéressé par une application spécifique en cours proposée, [envoyez-nous des détails sur l’application](mailto:casfeedback@microsoft.com). Envoyez-nous également le cas d’usage qui vous intéresse pour que nous puissions l’intégrer.

>[!div class="step-by-step"]
[SUIVANT : Déployer le contrôle d’application par accès conditionnel »](proxy-deployment-aad.md)

## <a name="next-steps"></a>Étapes suivantes
[Déployer le Contrôle d’applications par accès conditionnel pour les applications Azure AD](proxy-deployment-aad.md)

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)