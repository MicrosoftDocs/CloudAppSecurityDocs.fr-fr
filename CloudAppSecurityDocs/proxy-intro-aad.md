---
title: Protéger avec le contrôle d’application par accès conditionnel Microsoft Cloud App Security
description: Cet article fournit des informations sur le fonctionnement du proxy inverse du contrôle d’application par accès conditionnel de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 01/15/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: b3517591eba70dde048041c7b55a57679e7cc829
ms.sourcegitcommit: dabfa885ebb82db25a92127d87e8d1283340e834
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2020
ms.locfileid: "76020767"
---
# <a name="protect-apps-with-microsoft-cloud-app-security-conditional-access-app-control"></a>Protéger les applications avec le Contrôle d’accès conditionnel aux applications Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

En entreprise, le fait de savoir ce qui s’est passé dans votre environnement cloud après coup n’est pas suffisant. En effet, vous devez pouvoir arrêter les violations et les fuites en temps réel, avant que les employés ne puissent, par inadvertance ou intentionnellement, compromettre vos données et votre organisation. Il est important d’autoriser les utilisateurs de votre organisation à accéder à la plupart des services et outils des applications cloud, et de leur permettre d’apporter leurs propres appareils au travail. En même temps, vous avez besoin d’outils pour protéger votre organisation contre les fuites et le vol de données, en temps réel. Avec Azure Active Directory (Azure AD), Microsoft Cloud App Security offre ces fonctionnalités dans une expérience globale et intégrée avec contrôle d’application par accès conditionnel.

> [!NOTE]
>
> - Pour utiliser Cloud App Security contrôle d’application par accès conditionnel, vous avez besoin d’une [licence Azure Active Directory P1](https://azure.microsoft.com/pricing/details/active-directory/)et d’un abonnement actif Microsoft Cloud App Security ou d’une licence Office 365 E5. Pour obtenir la liste des applications proposées incluses avec Office 365 E5, consultez [applications proposées par office 365](#O365-apps).
> - Les contrôles d’accès et de session prennent également en charge les applications qui sont configurées avec des fournisseurs d’identité autres que Azure AD. Pour plus d'informations sur ce scénario, envoyez un e-mail à mcaspreview@microsoft.com.

## <a name="how-it-works"></a>Fonctionnement

Contrôle d’application par accès conditionnel utilise une architecture de proxy inverse et est intégrée de manière unique avec Azure AD accès conditionnel. Azure AD l’accès conditionnel vous permet d’appliquer des contrôles d’accès sur les applications de votre organisation en fonction de certaines conditions. Les conditions définissent *qui* (utilisateur ou groupe d’utilisateurs) et *Quelles* (applications Cloud) et *où* (emplacements et réseaux) une stratégie d’accès conditionnel est appliquée. Une fois que vous avez déterminé les conditions, vous pouvez router les utilisateurs vers Microsoft Cloud App Security, ce qui vous permet de protéger des données avec le contrôle d’application par accès conditionnel en appliquant des contrôles d’accès et de session.

Le Contrôle d’accès conditionnel aux applications active l’accès aux applications des utilisateurs et les sessions à surveiller et à contrôler en temps réel, en fonction des stratégies d’accès et de session. Les stratégies d’accès et de session sont utilisées dans le portail Cloud App Security pour affiner les filtres et définir les actions à effectuer sur un utilisateur. Avec les stratégies d’accès et de session, vous pouvez :

- **Empêcher l’exfiltration de données**: vous pouvez bloquer le téléchargement, couper, copier et imprimer des documents sensibles sur, par exemple les appareils non gérés.

- **Protéger au téléchargement**: au lieu de bloquer le téléchargement de documents sensibles, vous pouvez exiger que les documents soient étiquetés et protégés par Azure information protection. Cette action garantit que le document est protégé et que l’accès utilisateur est limité dans une session potentiellement risquée.

- **Empêcher le téléchargement de fichiers sans étiquette**: avant qu’un fichier sensible ne soit téléchargé, distribué et utilisé par d’autres utilisateurs, il est important de s’assurer que le fichier a l’étiquette et la protection appropriées. Vous pouvez vous assurer que les fichiers sans étiquette avec du contenu sensible ne peuvent pas être téléchargés tant que l’utilisateur n’a pas classé le contenu.

- **Surveiller les sessions utilisateur pour la conformité**: les utilisateurs risqués sont analysés lorsqu’ils se connectent à des applications et que leurs actions sont journalisées depuis la session. Vous pouvez examiner et analyser le comportement des utilisateurs pour comprendre où et dans quelles conditions les stratégies de session devront être appliquées à l’avenir.

- **Bloquer l’accès**: vous pouvez bloquer l’accès de façon granulaire pour des applications et des utilisateurs spécifiques en fonction de plusieurs facteurs de risque. Par exemple, vous pouvez les bloquer s’ils utilisent des certificats clients comme forme de gestion des périphériques.

- **Bloquer les activités personnalisées**: certaines applications ont des scénarios uniques qui comportent un risque, par exemple, l’envoi de messages avec du contenu sensible dans des applications telles que Microsoft teams ou la marge. Dans ce type de scénario, vous pouvez analyser les messages pour rechercher du contenu sensible et les bloquer en temps réel.

### <a name="how-session-control-works"></a>Fonctionnement du contrôle de session

La création d’une stratégie de session avec le Contrôle d’accès conditionnel aux applications vous permet de contrôler des sessions utilisateur en redirigeant l’utilisateur via un proxy inversé plutôt que directement vers l’application. À partir de là, les demandes et les réponses de l’utilisateur passent par Cloud App Security plutôt que directement à l’application.

Quand une session est protégée par proxy, toutes les URL et cookies appropriés sont remplacés par Cloud App Security. Par exemple, si l’application retourne une page avec des liens dont les domaines se terminent par myapp.com, le lien est remplacé par des domaines se terminant par quelque chose comme : myapp.com.us.cas.ms

Cette méthode ne vous oblige à installer quoi que ce soit sur l’appareil, ce qui la rend idéale lors de l’analyse ou du contrôle des sessions à partir d’appareils non gérés ou d’utilisateurs partenaires.

> [!NOTE]
> Cloud App Security tire parti des centres de données Azure dans le monde entier pour offrir des performances optimisées grâce à la géolocalisation. Cela signifie que la session d’un utilisateur peut être hébergée en dehors d’une région particulière, en fonction des modèles de trafic et de leur emplacement. Toutefois, pour protéger votre confidentialité, aucune donnée de session n’est stockée dans ces centres de données.

## <a name="managed-device-identification"></a>Identification des appareils gérés

Le Contrôle d’accès conditionnel aux applications vous permet de créer des stratégies qui déterminent si un appareil est géré ou non. Pour identifier l’état d’un appareil, vous pouvez configurer des stratégies d’accès et de session pour vérifier les éléments suivants :

- Appareils conformes à Microsoft Intune (Intune)
- Appareils joints à Azure AD hybride
- Présence de certificats clients dans une chaîne approuvée

### <a name="intune-compliant-and-hybrid-azure-ad-joined-devices"></a>Appareils conformes et hybrides Azure AD associés à Intune

Azure AD l’accès conditionnel permet de transmettre directement les informations d’appareil jointes conformes et hybrides à Microsoft Cloud App Security. À partir de là, vous pouvez développer une stratégie d’accès ou de session qui utilise l’état de l’appareil comme filtre. Pour plus d’informations, consultez [Présentation de la gestion des appareils dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-introduction).

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

Pour configurer une stratégie pour tirer parti de la gestion des appareils via des certificats clients :

1. Dans Cloud App Security, dans la barre de menus, cliquez sur l' ![icône](media/settings-icon.png "icône des paramètres") paramètres roue dentée paramètres, puis sélectionnez **paramètres**.

1. Sélectionnez l’onglet Identification de l' **appareil** .
1. Chargez autant de certificats racine ou intermédiaires que nécessaire.

Une fois les certificats téléchargés, vous pouvez créer des stratégies d’accès et de session basées sur une **balise d’appareil** et un **certificat client valide**.

## <a name="supported-apps-and-clients"></a>Applications et clients pris en charge

Les contrôles de session et d’accès peuvent être appliqués à n’importe quelle authentification unique interactive, à l’aide des protocoles d’authentification SAML 2,0 ou Open ID Connect. Vous pouvez également appliquer ces contrôles à des applications hébergées localement et configurées avec le [Proxy Azure ad App](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy). En outre, les contrôles d’accès peuvent être appliqués aux applications clientes natives et de bureau.

Cloud App Security identifie les applications à l’aide des informations disponibles dans son catalogue d’applications Cloud. Certaines organisations et utilisateurs personnalisent des applications en ajoutant des plug-ins. Toutefois, pour que les contrôles de session fonctionnent correctement avec ces plug-ins, les domaines personnalisés associés doivent être ajoutés à l’application correspondante dans le catalogue.

> [!NOTE]
> L’application Authenticator, parmi d’autres flux de connexion d’application cliente native, utilise un flux de connexion non interactif et ne peut pas être utilisée avec les contrôles d’accès.

### <a name="access-controls"></a>Contrôles d’accès

De nombreuses organisations qui choisissent d’utiliser des contrôles de session pour les applications Cloud pour contrôler les activités en session, appliquent également des contrôles d’accès pour bloquer le même ensemble d’applications clientes mobiles et de bureau natives, offrant ainsi une sécurité complète pour les applications.

Vous pouvez bloquer l’accès aux applications clientes mobiles natives et de bureau à l’aide de stratégies d’accès, en définissant le filtre d' **application client** sur **mobile et Desktop**. Certaines applications clientes natives peuvent être reconnues individuellement, tandis que d’autres qui font partie d’une suite d’applications ne peuvent être identifiées qu’en tant qu’application de niveau supérieur. Par exemple, les applications telles que SharePoint Online peuvent uniquement être reconnues en créant une stratégie d’accès appliquée aux applications Office 365.

> [!NOTE]
> À moins que le filtre d' **application cliente** ne soit spécifiquement défini sur **mobile et Desktop**, la stratégie d’accès résultante s’appliquera uniquement aux sessions de navigateur. Cela a pour but d’empêcher le proxy par inadvertance des sessions utilisateur, qui peut être un sous-utilisateur de l’utilisation de ce filtre. Tandis que la plupart des principaux navigateurs prennent en charge l’exécution d’une vérification de certificat client, certaines applications mobiles et de bureau utilisent des navigateurs intégrés qui peuvent ne pas prendre en charge cette vérification. Par conséquent, l’utilisation de ce filtre peut affecter l’authentification pour ces applications.

### <a name="session-controls"></a>Contrôles de session

**Le contrôle de session est disponible sur tous les navigateurs de toutes les plateformes majeures, quel que soit le système d’exploitation**. Nous vous recommandons d’utiliser Internet Explorer 11, Microsoft Edge (dernière version), Google Chrome (dernière version), Mozilla Firefox (dernière version) ou Apple Safari (dernière version). L’accès aux applications mobiles et de bureau peut également être bloqué ou autorisé.

> [!NOTE]
> Cloud App Security s’appuie sur les protocoles TLS (Transport Layer Security) 1.2+ pour fournir un chiffrement de pointe. Les applications clientes natives et les navigateurs qui ne prennent pas en charge TLS 1.2 + ne sont pas accessibles lorsqu’ils sont configurés avec le contrôle de session. Toutefois, les applications SaaS qui utilisent TLS 1.1 ou une version antérieure apparaissent dans le navigateur comme utilisant TLS 1.2+ lorsqu’elles sont configurées avec Cloud App Security.

<a name="featured-apps"></a>En intégrant en mode natif avec Azure AD, toute application configurée avec SAML ou Open ID Connect vous permet d’intégrer n’importe quelle application vous-même. En outre, les applications suivantes sont proposées par Cloud App Security et sont déjà intégrées et prêtes à être utilisées dans n’importe quel locataire :

- AWS
- DevOps Azure (Visual Studio Team Services)
- Portail Azure (préversion)
- Zone
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
- OneDrive Entreprise
- LinkedIn Learning
- Power BI
- Salesforce
- ServiceNow
- SharePodanst Onldanse
- Slack
- Tableau
- Microsoft Teams (préversion)
- Workday
- Workiva
- Workplace by Facebook
- Yammer (préversion)

### <a name="a-ido365-apps-office-365-featured-apps"></a><a id="O365-apps" />les applications Office 365 proposées

La liste suivante répertorie les applications proposées qui sont prises en charge dans Office 365 Cloud App Security :

- Exchange Online
- OneDrive Entreprise
- Power BI
- SharePodanst Onldanse
- Microsoft Teams (préversion)
- Yammer (préversion)

Si vous êtes intéressé par une application spécifique, [envoyez-nous des informations sur l’application](mailto:casfeedback@microsoft.com). Envoyez-nous également le cas d’usage qui vous intéresse pour que nous puissions l’intégrer.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Déployer le contrôle d’application par accès conditionnel pour les applications proposées](proxy-deployment-aad.md)

> [!div class="nextstepaction"]
> [Déployer le contrôle d’application par accès conditionnel pour tous les types d’applications](proxy-deployment-any-app.md)

[!INCLUDE [Open support ticket](includes/support.md)]
