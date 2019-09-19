---
title: Protéger avec le contrôle d’application par accès conditionnel Microsoft Cloud App Security
description: Cet article fournit des informations sur le fonctionnement du proxy inverse du contrôle d’application par accès conditionnel de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 8/25/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 10f17632f5b611b86b1555ff50be5237c103ea88
ms.sourcegitcommit: 8a49c166424fea83853b0a6895212367526abe78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71085032"
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

- **Empêcher l’exfiltration de données**: Vous pouvez bloquer le téléchargement, couper, copier et imprimer des documents sensibles, par exemple des appareils non gérés.

- **Protéger en cas de téléchargement** : Au lieu de bloquer le téléchargement de documents sensibles, vous pouvez demander l’étiquetage et la protection des documents avec Azure Information Protection. Cette action garantit que le document est protégé et que l’accès utilisateur est limité dans une session potentiellement risquée.

- **Empêcher le téléchargement de fichiers sans étiquette**: Avant qu’un fichier sensible ne soit téléchargé, distribué et utilisé par d’autres utilisateurs, il est important de s’assurer que le fichier possède l’étiquette et la protection appropriées. Vous pouvez vous assurer que les fichiers sans étiquette avec du contenu sensible ne peuvent pas être téléchargés tant que l’utilisateur n’a pas classé le contenu.

- **Surveiller la conformité des sessions utilisateur**: Les utilisateurs à risque sont surveillés lorsqu’ils se connectent à des applications et leurs actions sont journalisées depuis la session. Vous pouvez examiner et analyser le comportement des utilisateurs pour comprendre où et dans quelles conditions les stratégies de session devront être appliquées à l’avenir.

- **Bloquer l’accès** : Vous pouvez bloquer de façon granulaire l’accès pour des applications et des utilisateurs spécifiques en fonction de plusieurs facteurs de risque. Par exemple, vous pouvez les bloquer s’ils utilisent des certificats clients comme forme de gestion des périphériques.

- **Bloquer les activités personnalisées**: Certaines applications ont des scénarios uniques qui comportent un risque, par exemple, l’envoi de messages avec du contenu sensible dans des applications telles que Microsoft teams ou la marge. Dans ce type de scénario, vous pouvez analyser les messages pour rechercher du contenu sensible et les bloquer en temps réel.

### <a name="how-session-control-works"></a>Fonctionnement du contrôle de session

La création d’une stratégie de session avec le Contrôle d’accès conditionnel aux applications vous permet de contrôler des sessions utilisateur en redirigeant l’utilisateur via un proxy inversé plutôt que directement vers l’application. À partir de là, les demandes et les réponses de l’utilisateur passent par Cloud App Security plutôt que directement à l’application.

Quand une session est protégée par proxy, toutes les URL et cookies appropriés sont remplacés par Cloud App Security. Par exemple, si l’application retourne une page avec des liens dont les domaines se terminent par myapp.com, le lien est remplacé par des domaines se terminant par quelque chose comme : myapp.com.us.cas.ms

Cette méthode ne vous oblige à installer quoi que ce soit sur l’appareil, ce qui la rend idéale lors de l’analyse ou du contrôle des sessions à partir d’appareils non gérés ou d’utilisateurs partenaires.

> [!NOTE]
> Cloud App Security tire parti des centres de données Azure dans le monde entier pour offrir des performances optimisées grâce à la géolocalisation. Cela signifie que la session d’un utilisateur peut être hébergée en dehors d’une région particulière, en fonction des modèles de trafic et de leur emplacement. Toutefois, pour protéger votre confidentialité, aucune donnée de session n’est stockée dans ces centres de données.

## <a name="managed-device-identification"></a>Identification des appareils gérés

Le Contrôle d’accès conditionnel aux applications vous permet de créer des stratégies qui déterminent si un appareil est géré ou non. Pour déterminer si un appareil est géré ou non, la fonctionnalité utilise ce qui suit :

- Appareils conformes
- Appareils joints à un domaine
- Déploiement de certificats clients

### <a name="compliant-and-domain-joined-devices"></a>Appareils conformes et joints à un domaine

L’accès conditionnel Azure AD permet aux informations sur les appareils conformes et joints à un domaine d’être directement transmises à Microsoft Cloud App Security. À partir de là, vous pouvez développer une stratégie d’accès ou de session qui utilise l’état de l’appareil comme filtre. Pour plus d’informations, consultez [Présentation de la gestion des appareils dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-introduction).

> [!NOTE]
> Certains navigateurs peuvent nécessiter une configuration supplémentaire telle que l’installation d’une extension. Pour plus d’informations, consultez [prise en charge du navigateur d’accès conditionnel](https://go.microsoft.com/fwlink/?linkid=2102732).

### <a name="client-certificate-authenticated-devices"></a>Appareils authentifiés par certificat client

Le mécanisme d’identification des appareils peut exiger une authentification desdits appareils à l’aide de certificats clients. Vous pouvez utiliser des certificats clients existants déjà déployés dans votre organisation ou déployer de nouveaux certificats clients sur des appareils gérés. Vous profitez ensuite de la présence de ces certificats pour définir des stratégies d’accès et de session.

Les certificats clients SSL sont vérifiés par le biais d’une chaîne d’approbation. Vous pouvez télécharger une racine X. 509 ou une autorité de certification intermédiaire au format de certificat PEM. Ces certificats doivent contenir la clé publique de l’autorité de certification, qui est ensuite utilisée pour signer les certificats clients présentés au cours d’une session.

Une fois le certificat téléchargé et une stratégie pertinente configurée, lorsqu’une session applicable parcourt contrôle d’application par accès conditionnel, le point de terminaison Cloud App Security demande au navigateur de présenter les certificats clients SSL. Le navigateur dessert les certificats clients SSL installés avec une clé privée. Cette combinaison de certificat et de clé privée s’effectue à l’aide du format de fichier PKCS #12, généralement. P12 ou. pfx.

Lorsqu’une vérification de certificat client est effectuée, Cloud App Security vérifie les conditions suivantes :

1. Le certificat client sélectionné est valide et se trouve sous l’autorité de certification racine ou intermédiaire appropriée.
1. Le certificat n’est pas révoqué (si la liste de révocation des certificats est activée).

> [!NOTE]
> La plupart des navigateurs principaux prennent en charge l’exécution d’une vérification de certificat client. Toutefois, les applications mobiles et de bureau utilisent souvent des navigateurs intégrés qui ne prennent peut-être pas en charge cette vérification et affectent donc l’authentification pour ces applications.

Pour plus d’informations sur la façon de déployer des certificats clients, consultez [Déployer un Contrôle d’accès conditionnel aux applications pour les applications Azure AD](proxy-deployment-aad.md).

## <a name="supported-apps-and-clients"></a>Applications et clients pris en charge

Le contrôle d’application par accès conditionnel prend en charge les applications SAML et Open ID Connect configurées avec l’authentification unique, ainsi que les applications web hébergées localement qui sont configurées avec le [proxy d’application Azure AD](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).
> [!NOTE]
> Le contrôle d’application par accès conditionnel prend également en charge des applications qui sont configurées avec des fournisseurs d’identité non-Azure AD. Pour plus d'informations sur ce scénario, envoyez un e-mail à mcaspreview@microsoft.com.

**Le contrôle de session est disponible sur tous les navigateurs de toutes les plateformes majeures, quel que soit le système d’exploitation**. Nous vous recommandons d’utiliser Internet Explorer 11, Microsoft Edge (dernière version), Google Chrome (dernière version), Mozilla Firefox (dernière version) ou Apple Safari (dernière version). L’accès aux applications mobiles et de bureau peut également être bloqué ou autorisé.

> [!NOTE]
> L’utilisation du filtre d' **application cliente** dans les stratégies d’accès peut entraîner le proxy de la session utilisateur résultante par Cloud App Security.

> [!NOTE]
> Cloud App Security s’appuie sur les protocoles TLS (Transport Layer Security) 1.2+ pour fournir un chiffrement de pointe. Les applications clientes natives et les navigateurs qui ne prennent pas en charge TLS 1.2+ ne sont pas accessibles lorsqu’ils sont configurés avec le contrôle de session. Toutefois, les applications SaaS qui utilisent TLS 1.1 ou une version antérieure apparaissent dans le navigateur comme utilisant TLS 1.2+ lorsqu’elles sont configurées avec Cloud App Security.

En intégrant en mode natif avec Azure AD, toute application configurée avec SAML ou Open ID Connect peut être intégrée automatiquement. En outre, les applications suivantes sont proposées par Cloud App Security et sont déjà intégrées et prêtes à être utilisées dans n’importe quel locataire :

- AWS
- DevOps Azure (Visual Studio Team Services)
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

Si vous êtes intéressé par une application spécifique, [envoyez-nous des informations sur l’application](mailto:casfeedback@microsoft.com). Envoyez-nous également le cas d’usage qui vous intéresse pour que nous puissions l’intégrer.

>[!div class="step-by-step"]
[SUIVANT : Déployer le contrôle d’application par accès conditionnel »](proxy-deployment-aad.md)

## <a name="next-steps"></a>Étapes suivantes

[Déployer le Contrôle d’applications par accès conditionnel pour les applications Azure AD](proxy-deployment-aad.md)

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)
