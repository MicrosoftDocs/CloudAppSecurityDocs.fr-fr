---
title: Protéger avec le contrôle d’application par accès conditionnel Microsoft Cloud App Security
description: Cet article fournit des informations sur le fonctionnement du proxy inverse du contrôle d’application par accès conditionnel de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 04/27/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 0ba00548c014126414319fb5860d2c7fab9fb26d
ms.sourcegitcommit: 9a35b4e96db80ac85a4c0244ef6abd468d5774a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853981"
---
# <a name="protect-apps-with-microsoft-cloud-app-security-conditional-access-app-control"></a>Protéger les applications avec le Contrôle d’accès conditionnel aux applications Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

Dans le lieu de travail actuel, il est souvent difficile de savoir ce qui se passe dans votre environnement Cloud après le fait. En effet, vous devez pouvoir arrêter les violations et les fuites en temps réel, avant que les employés ne puissent, par inadvertance ou intentionnellement, compromettre vos données et votre organisation. Il est important de permettre aux utilisateurs de votre organisation de tirer le meilleur parti des services et outils disponibles dans les applications Cloud et de leur permettre de faire fonctionner leurs propres appareils. En même temps, vous avez besoin d’outils pour protéger votre organisation contre les fuites et le vol de données, en temps réel. Microsoft Cloud App Security s’intègre à n’importe quel fournisseur d’identité (IdP) pour fournir ces fonctionnalités avec des contrôles d’accès et de session. Si vous utilisez Azure Active Directory (Azure AD) comme IdP, ces contrôles sont intégrés et rationalisés pour un déploiement plus simple et plus personnalisé, basé sur l' [outil d’accès conditionnel](/azure/active-directory/conditional-access/overview)de Azure ad.

> [!NOTE]
>
> - Pour utiliser Cloud App Security contrôle d’application par accès conditionnel, vous avez besoin d’une [licence Azure Active Directory P1](https://azure.microsoft.com/pricing/details/active-directory/)ou de la licence requise par votre solution IDP, ainsi que d’une licence Cloud App Security.

## <a name="how-it-works"></a>Fonctionnement

Contrôle d’application par accès conditionnel utilise une architecture de proxy inverse et s’intègre à votre IdP. Lors de l’intégration avec Azure AD accès conditionnel, vous pouvez configurer des applications pour qu’elles fonctionnent avec contrôle d’application par accès conditionnel en quelques clics, ce qui vous permet d’appliquer facilement et de manière sélective des contrôles d’accès et de session sur les applications de votre organisation en fonction des conditions de l’accès conditionnel. Les conditions définissent *qui* (utilisateur ou groupe d’utilisateurs) et *Quelles* (applications Cloud) et *où* (emplacements et réseaux) une stratégie d’accès conditionnel est appliquée. Une fois que vous avez déterminé les conditions, vous pouvez acheminer les utilisateurs vers Cloud App Security où vous pouvez protéger les données avec contrôle d’application par accès conditionnel en appliquant des contrôles d’accès et de session.

Le contrôle d’application par accès conditionnel permet de superviser et de contrôler en temps réel les sessions et accès utilisateur aux applications en fonction des stratégies d’accès et de session. Les stratégies d’accès et de session s’utilisent dans le portail Cloud App Security pour affiner davantage les filtres et définir les actions à effectuer sur un utilisateur. Avec les stratégies d’accès et de session, vous pouvez :

- **Empêcher l’exfiltration de données**: vous pouvez bloquer le téléchargement, couper, copier et imprimer des documents sensibles sur, par exemple les appareils non gérés.

- **Protéger au téléchargement**: au lieu de bloquer le téléchargement de documents sensibles, vous pouvez exiger que les documents soient étiquetés et protégés par Azure information protection. Cette action garantit que les documents sont protégés et que l’accès utilisateur est limité dans une session potentiellement à risque.

- **Empêcher le téléchargement de fichiers sans étiquette**: avant qu’un fichier sensible ne soit téléchargé, distribué et utilisé par d’autres utilisateurs, il est important de s’assurer que le fichier a l’étiquette et la protection appropriées. Vous pouvez bloquer le chargement des fichiers sans étiquette qui ont du contenu sensible tant que l’utilisateur n’a pas classifié leur contenu.

- **Bloquer les logiciels malveillants potentiels**: vous pouvez protéger votre environnement contre les logiciels malveillants en bloquant le chargement de fichiers potentiellement malveillants. Tout fichier téléchargé ou téléchargé peut être analysé par rapport à Microsoft Threat Intelligence et bloqué instantanément.

- **Surveiller les sessions utilisateur pour la conformité**: les utilisateurs risqués sont analysés lorsqu’ils se connectent à des applications et que leurs actions sont journalisées depuis la session. Vous pouvez examiner et analyser le comportement des utilisateurs pour comprendre où et dans quelles conditions les stratégies de session doivent être appliquées à l’avenir.

- **Bloquer l’accès**: vous pouvez bloquer l’accès de façon granulaire pour des applications et des utilisateurs spécifiques en fonction de plusieurs facteurs de risque. Par exemple, vous pouvez les bloquer s’ils utilisent des certificats clients comme moyen de gérer les appareils.

- **Bloquer les activités personnalisées**: certaines applications ont des scénarios uniques qui comportent un risque, par exemple, l’envoi de messages avec du contenu sensible dans des applications telles que Microsoft teams ou la marge. Dans ce genre de scénarios, vous pouvez analyser les messages pour rechercher la présence de contenu sensible et les bloquer en temps réel.

### <a name="how-session-control-works"></a>Fonctionnement du contrôle de session

La création d’une stratégie de session avec le Contrôle d’accès conditionnel aux applications vous permet de contrôler des sessions utilisateur en redirigeant l’utilisateur via un proxy inversé plutôt que directement vers l’application. À partir de là, les demandes et les réponses de l’utilisateur passent par Cloud App Security plutôt que directement à l’application.

Quand une session est protégée par proxy, toutes les URL et cookies appropriés sont remplacés par Cloud App Security. Par exemple, si l’application retourne une page avec des liens dont les domaines se terminent par `myapp.com` , le domaine du lien est suivi d’un suffixe similaire à ce qui `*.mcas.ms` suit :

|URL de l’application|URL remplacée|
|---|---|
|`myapp.com`|`myapp.com.mcas.ms`|

Cette méthode ne vous oblige à installer quoi que ce soit sur l’appareil, ce qui la rend idéale lors de l’analyse ou du contrôle des sessions à partir d’appareils non gérés ou d’utilisateurs partenaires.

> [!NOTE]
>
> - Notre technologie utilise des heuristiques brevetées de meilleure qualité pour identifier et contrôler les activités effectuées par l’utilisateur dans l’application cible. Nos heuristiques sont conçues pour optimiser et équilibrer la sécurité grâce à la facilité d’utilisation. Dans certains scénarios rares, lorsque les activités bloquantes côté serveur rendent l’application inutilisable, nous sécurisons ces activités uniquement côté client, ce qui les rend potentiellement susceptibles d’être exploitées par des personnes malveillantes.
> - Cloud App Security tire parti des centres de données Azure dans le monde entier pour offrir des performances optimisées grâce à la géolocalisation. Cela signifie que la session d’un utilisateur peut être hébergée en dehors d’une région particulière, en fonction des modèles de trafic et de leur emplacement. Toutefois, pour protéger votre confidentialité, aucune donnée de session n’est stockée dans ces centres de données.

## <a name="managed-device-identification"></a>Identification des appareils gérés

Le Contrôle d’accès conditionnel aux applications vous permet de créer des stratégies qui déterminent si un appareil est géré ou non. Pour identifier l’état d’un appareil, vous pouvez configurer des stratégies d’accès et de session pour vérifier les éléments suivants :

- Appareils conformes à Microsoft Intune [disponible uniquement avec Azure AD]
- Azure AD Hybride des appareils joints [disponible uniquement avec Azure AD]
- Présence de certificats clients dans une chaîne approuvée

### <a name="intune-compliant-and-hybrid-azure-ad-joined-devices"></a>Appareils conformes à Intune et Azure AD Hybride joints

Azure AD l’accès conditionnel permet de transmettre directement les informations d’appareil jointes et conformes à Intune et Azure AD Hybride à Cloud App Security. À partir de là, vous pouvez développer une stratégie d’accès ou de session qui utilise l’état de l’appareil comme filtre. Pour plus d’informations, consultez la [Présentation de la gestion des appareils dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-introduction).

> [!NOTE]
> Certains navigateurs peuvent nécessiter une configuration supplémentaire telle que l’installation d’une extension. Pour plus d’informations, consultez [prise en charge du navigateur d’accès conditionnel](https://go.microsoft.com/fwlink/?linkid=2102732).

### <a name="client-certificate-authenticated-devices"></a>Appareils authentifiés par certificat client

Le mécanisme d’identification des appareils peut exiger une authentification desdits appareils à l’aide de certificats clients. Vous pouvez utiliser des certificats clients existants déjà déployés dans votre organisation ou déployer de nouveaux certificats clients sur des appareils gérés. Assurez-vous que le certificat client est installé dans le magasin de l’utilisateur et non dans le magasin de l’ordinateur. Vous profitez ensuite de la présence de ces certificats pour définir des stratégies d’accès et de session.

Les certificats clients SSL sont vérifiés par le biais d’une chaîne d’approbation. Vous pouvez télécharger une racine X. 509 ou une autorité de certification intermédiaire au format de certificat PEM. Ces certificats doivent contenir la clé publique de l’autorité de certification, qui est ensuite utilisée pour signer les certificats clients présentés au cours d’une session.

Une fois le certificat téléchargé et une stratégie pertinente configurée, lorsqu’une session applicable parcourt contrôle d’application par accès conditionnel, le point de terminaison Cloud App Security demande au navigateur de présenter les certificats clients SSL. Le navigateur dessert les certificats clients SSL installés avec une clé privée. Cette combinaison de certificat et de clé privée s’effectue à l’aide du format de fichier PKCS #12, généralement. P12 ou. pfx.

Lorsqu’une vérification de certificat client est effectuée, Cloud App Security vérifie les conditions suivantes :

1. Le certificat client sélectionné est valide et se trouve sous l’autorité de certification racine ou intermédiaire appropriée.
1. Le certificat n’est pas révoqué (si la liste de révocation des certificats est activée).

> [!NOTE]
>
> La plupart des navigateurs principaux prennent en charge l’exécution d’une vérification de certificat client. Toutefois, les applications mobiles et de bureau utilisent souvent des navigateurs intégrés qui ne prennent peut-être pas en charge cette vérification et affectent donc l’authentification pour ces applications.

Pour configurer une stratégie pour tirer parti de la gestion des appareils via des certificats clients :

1. Dans Cloud App Security, dans la barre de menus, cliquez sur l' ![icône](media/settings-icon.png "Icône des paramètres") paramètres roue dentée paramètres, puis sélectionnez **paramètres**.

1. Sélectionnez l’onglet Identification de l' **appareil** .
1. Chargez autant de certificats racine ou intermédiaires que vous le souhaitez.

Une fois les certificats téléchargés, vous pouvez créer des stratégies d’accès et de session basées sur une **balise d’appareil** et un **certificat client valide**.

## <a name="supported-apps-and-clients"></a>Applications et clients pris en charge

Les contrôles de session et d’accès peuvent être appliqués à n’importe quelle authentification unique interactive, en utilisant le protocole d’authentification SAML 2,0 ou, si vous utilisez Azure AD, le protocole d’authentification Open ID Connect. En outre, si vos applications sont configurées avec Azure AD, vous pouvez également appliquer ces contrôles aux applications hébergées localement configurées avec le [Proxy Azure ad App](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy). En outre, les contrôles d’accès peuvent être appliqués aux applications clientes natives et de bureau.

Cloud App Security identifie les applications à l’aide des informations disponibles dans son catalogue d’applications Cloud. Certaines organisations et utilisateurs personnalisent des applications en ajoutant des plug-ins. Toutefois, pour que les contrôles de session fonctionnent correctement avec ces plug-ins, les domaines personnalisés associés doivent être ajoutés à l’application correspondante dans le catalogue.

> [!NOTE]
> L’application Authenticator, parmi d’autres flux de connexion d’application cliente native, utilise un flux de connexion non interactif et ne peut pas être utilisée avec les contrôles d’accès.

### <a name="access-controls"></a>Contrôles d’accès

De nombreuses organisations qui choisissent d’utiliser des contrôles de session pour les applications Cloud pour contrôler les activités en session, appliquent également des contrôles d’accès pour bloquer le même ensemble d’applications clientes mobiles et de bureau natives, offrant ainsi une sécurité complète pour les applications.

Vous pouvez bloquer l’accès aux applications clientes mobiles natives et de bureau à l’aide de stratégies d’accès, en définissant le filtre d' **application client** sur **mobile et Desktop**. Certaines applications clientes natives peuvent être reconnues individuellement, tandis que d’autres qui font partie d’une suite d’applications ne peuvent être identifiées qu’en tant qu’application de niveau supérieur. Par exemple, les applications telles que SharePoint Online peuvent uniquement être reconnues en créant une stratégie d’accès appliquée aux applications Office 365.

> [!NOTE]
> À moins que le filtre d' **application cliente** ne soit spécifiquement défini sur **mobile et Desktop**, la stratégie d’accès résultante s’appliquera uniquement aux sessions de navigateur. Cela a pour but d’empêcher le proxy par inadvertance des sessions utilisateur, qui peut être un sous-utilisateur de l’utilisation de ce filtre. Tandis que la plupart des principaux navigateurs prennent en charge l’exécution d’une vérification de certificat client, certaines applications mobiles et de bureau utilisent des navigateurs intégrés qui peuvent ne pas prendre en charge cette vérification. Par conséquent, l’utilisation de ce filtre peut affecter l’authentification pour ces applications.

### <a name="session-controls"></a>Contrôles de session

Alors que les contrôles de session sont créés pour fonctionner avec n’importe quel navigateur sur n’importe quelle plateforme principale sur tout système d’exploitation, nous prenons en charge [Microsoft Edge](https://www.microsoft.com/edge) (dernière version), Google Chrome (dernière version), Mozilla Firefox (dernière version) ou Apple Safari (dernière version). L’accès aux applications mobiles et de bureau peut également être bloqué ou autorisé.

> [!NOTE]
>
> - Cloud App Security s’appuie sur les protocoles TLS (Transport Layer Security) 1.2 + pour offrir un chiffrement optimal. Les applications clientes natives et les navigateurs qui ne prennent pas en charge TLS 1.2 + ne sont pas accessibles lorsqu’ils sont configurés avec le contrôle de session. Toutefois, les applications SaaS qui utilisent TLS 1.1 ou une version antérieure apparaissent dans le navigateur comme utilisant TLS 1.2+ lorsqu’elles sont configurées avec Cloud App Security.
> - Pour appliquer des contrôles de session à portal.office.com, vous devez intégrer le centre d’administration Microsoft Office 365. Pour plus d’informations sur l’intégration des applications, consultez [intégration et déploiement de contrôle d’application par accès conditionnel pour n’importe quelle application](proxy-deployment-any-app.md).

<a name="featured-apps"></a>Toute application Web configurée à l’aide des [protocoles d’authentification mentionnés précédemment](#supported-apps-and-clients) peut être intégrée pour fonctionner avec les contrôles d’accès et de session. En outre, les applications suivantes sont proposées par Cloud App Security et sont déjà intégrées et prêtes à être utilisées dans n’importe quel locataire :

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

### <a name="office-365-featured-apps"></a><a name="O365-apps"></a>Applications Office 365 proposées

La liste suivante répertorie les applications proposées qui sont prises en charge dans Office 365 Cloud App Security. Pour utiliser ces applications avec Cloud App Security, vous devez disposer d’une licence Office 365 E5.

- Exchange Online
- OneDrive Entreprise
- Power BI
- SharePoint Online
- Microsoft Teams (préversion)
- Yammer (préversion)

Si vous êtes intéressé par une application spécifique, [envoyez-nous des informations sur l’application](mailto:casfeedback@microsoft.com). Veillez à envoyer le cas d’usage qui vous intéresse pour l’intégration.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Déployer le contrôle d’application par accès conditionnel pour les applications proposées](proxy-deployment-aad.md)

> [!div class="nextstepaction"]
> [Déployer le contrôle d’application par accès conditionnel pour tous les types d’applications](proxy-deployment-any-app.md)

[!INCLUDE [Open support ticket](includes/support.md)]
