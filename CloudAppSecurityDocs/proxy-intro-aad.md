---
title: Protéger avec le contrôle d’application par accès conditionnel Microsoft Cloud App Security
description: Cet article fournit des informations sur le fonctionnement du proxy inverse du contrôle d’application par accès conditionnel de Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 9/23/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: d4b800afa927b8a9151837cfbff76478c98bf71f
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74460541"
---
# <a name="protect-apps-with-microsoft-cloud-app-security-conditional-access-app-control"></a>Protéger les applications avec le Contrôle d’accès conditionnel aux applications Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

>[!div class="step-by-step"]
[Suivant : Déployer le Contrôle d’accès conditionnel aux applications »](proxy-deployment-aad.md)

En entreprise, le fait de savoir ce qui s’est passé dans votre environnement cloud après coup n’est pas suffisant. En effet, vous devez pouvoir arrêter les violations et les fuites en temps réel, avant que les employés ne puissent, par inadvertance ou intentionnellement, compromettre vos données et votre organisation. Il est important d’autoriser les utilisateurs de votre organisation à accéder à la plupart des services et outils des applications cloud, et de leur permettre d’apporter leurs propres appareils au travail. En même temps, vous avez besoin d’outils pour protéger votre organisation contre les fuites et le vol de données, en temps réel. Avec Azure Active Directory, Microsoft Cloud App Security offre ces fonctionnalités dans une expérience globale et intégrée avec le Contrôle d’accès conditionnel aux applications.

> [!NOTE]
> To use Cloud App Security Conditional Access App Control, you need an [Azure Active Directory P1 license](https://azure.microsoft.com/pricing/details/active-directory/), and an active Microsoft Cloud App Security subscription or Office 365 E5 license. For a list of featured apps included with Office 365 E5, see [Office 365 featured apps](#O365-apps).

Office 365 E5 license. For a list of apps included with supported Office 365 E5, see Office 365 featured apps

## <a name="how-it-works"></a>Fonctionnement

Le contrôle d’application par accès conditionnel utilise une architecture de proxy inverse. En outre, il est intégré de manière unique à l’accès conditionnel Azure AD. L’accès conditionnel Azure AD vous permet d’appliquer des contrôles d’accès sur les applications de votre organisation en fonction de certaines conditions. Ces conditions définissent à *quelles personnes* (utilisateur ou groupe d’utilisateurs), à *quelles applications* (applications cloud) et à *quels endroits* (emplacements et réseaux) une stratégie d’accès conditionnel est appliquée. Une fois que vous avez déterminé les conditions, vous pouvez router les utilisateurs vers Microsoft Cloud App Security, ce qui vous permet de protéger des données avec le contrôle d’application par accès conditionnel en appliquant des contrôles d’accès et de session.

Le Contrôle d’accès conditionnel aux applications active l’accès aux applications des utilisateurs et les sessions à surveiller et à contrôler en temps réel, en fonction des stratégies d’accès et de session. Les stratégies d’accès et de session sont utilisées dans le portail Cloud App Security pour affiner les filtres et définir les actions à effectuer sur un utilisateur. Avec les stratégies d’accès et de session, vous pouvez :

- **Prevent data exfiltration**: You can block the download, cut, copy, and print of sensitive documents on, for example, unmanaged devices.

- **Protect on download**: Instead of blocking the download of sensitive documents, you can require documents to be labeled and protected with Azure Information Protection. This action ensures the document is protected and user access is restricted in a potentially risky session.

- **Prevent upload of unlabeled files**: Before a sensitive file is uploaded, distributed, and used by others, it’s important to make sure that the file has the right label and protection. You can ensure that unlabeled files with sensitive content are blocked from being uploaded until the user classifies the content.

- **Monitor user sessions for compliance**: Risky users are monitored when they sign into apps and their actions are logged from within the session. Vous pouvez examiner et analyser le comportement des utilisateurs pour comprendre où et dans quelles conditions les stratégies de session devront être appliquées à l’avenir.

- **Block access**: You can granularly block access for specific apps and users depending on several risk factors. For example, you can block them if they are using client certificates as a form of device management.

- **Block custom activities**: Some applications have unique scenarios that carry risk, for example, sending messages with sensitive content in applications like Microsoft Teams or Slack. In these kinds of scenarios, you can scan messages for sensitive content and block them in real time.

### <a name="how-session-control-works"></a>Fonctionnement du contrôle de session

La création d’une stratégie de session avec le Contrôle d’accès conditionnel aux applications vous permet de contrôler des sessions utilisateur en redirigeant l’utilisateur via un proxy inversé plutôt que directement vers l’application. From then on, user requests and responses go through Cloud App Security rather than directly to the app.

When a session is protected by proxy, all the relevant URLs and cookies are replaced by Cloud App Security. Par exemple, si l’application retourne une page avec des liens dont les domaines se terminent par myapp.com, le lien est remplacé par des domaines se terminant par quelque chose comme : myapp.com.us.cas.ms

This method doesn't require you to install anything on the device making it ideal when monitoring or controlling sessions from unmanaged devices or partner users.

> [!NOTE]
> Cloud App Security tire parti des centres de données Azure dans le monde entier pour offrir des performances optimisées grâce à la géolocalisation. Cela signifie que la session d’un utilisateur peut être hébergée en dehors d’une région particulière, en fonction des modèles de trafic et de leur emplacement. Toutefois, pour protéger votre confidentialité, aucune donnée de session n’est stockée dans ces centres de données.

## <a name="managed-device-identification"></a>Identification des appareils gérés

Le Contrôle d’accès conditionnel aux applications vous permet de créer des stratégies qui déterminent si un appareil est géré ou non. Pour déterminer si un appareil est géré ou non, la fonctionnalité utilise ce qui suit :

- Appareils conformes
- Appareils joints à un domaine
- Déploiement de certificats clients

To configure a policy to leverage device management via client certificates:

1. Accédez à la roue dentée des paramètres et choisissez **Identification de périphérique**.
1. Charger un ou plusieurs certificats intermédiaires ou racines.
1. After the certificate is uploaded, you can create [access policies](access-policy-aad.md) and [session policies](session-policy-aad.md) based on **Device tag** and **Valid client certificate**.

    ![ID d’appareil du Contrôle d’application par accès conditionnel](./media/caac-device-id.png)

> [!NOTE]
> Un certificat est uniquement demandé à un utilisateur si la session correspond à une stratégie qui utilise le filtre du certificat client valide.

### <a name="compliant-and-domain-joined-devices"></a>Appareils conformes et joints à un domaine

L’accès conditionnel Azure AD permet aux informations sur les appareils conformes et joints à un domaine d’être directement transmises à Microsoft Cloud App Security. À partir de là, vous pouvez développer une stratégie d’accès ou de session qui utilise l’état de l’appareil comme filtre. Pour plus d’informations, consultez [Présentation de la gestion des appareils dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-introduction).

> [!NOTE]
> Some browsers may require additional configuration such as installing an extension. For more information, see [Conditional Access browser support](https://go.microsoft.com/fwlink/?linkid=2102732).

### <a name="client-certificate-authenticated-devices"></a>Appareils authentifiés par certificat client

Le mécanisme d’identification des appareils peut exiger une authentification desdits appareils à l’aide de certificats clients. Vous pouvez utiliser des certificats clients existants déjà déployés dans votre organisation ou déployer de nouveaux certificats clients sur des appareils gérés. Vous profitez ensuite de la présence de ces certificats pour définir des stratégies d’accès et de session.

SSL client certificates are verified via a trust chain. You can upload an X.509 root or intermediate certificate authority (CA) formatted in the PEM certificate format. These certificates must contain the public key of the CA, which is then used to sign the client certificates presented during a session.

Once the certificate is uploaded and a relevant policy is configured, when an applicable session traverses Conditional Access App Control, the Cloud App Security endpoint requests the browser to present the SSL client certificates. The browser serves the SSL client certificates that are installed with a private key. This combination of certificate and private key is done by using the PKCS #12 file format, typically .p12 or .pfx.

When a client certificate check is performed, Cloud App Security checks for the following conditions:

1. The selected client certificate is valid and is under the correct root or intermediate CA.
1. The certificate is not revoked (if CRL is enabled).

> [!NOTE]
> Most major browsers support performing a client certificate check. However, mobile and desktop apps often leverage built-in browsers that may not support this check and therefore affect authentication for these apps.

Pour plus d’informations sur la façon de déployer des certificats clients, consultez [Déployer un Contrôle d’accès conditionnel aux applications pour les applications Azure AD](proxy-deployment-aad.md).

## <a name="supported-apps-and-clients"></a>Applications et clients pris en charge

Conditional Access App Control currently supports SAML and Open ID Connect apps configured with single sign-on, along with web apps hosted on-premises configured with the [Azure AD App Proxy](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).
> [!NOTE]
> Le contrôle d’application par accès conditionnel prend également en charge des applications qui sont configurées avec des fournisseurs d’identité non-Azure AD. Pour plus d'informations sur ce scénario, envoyez un e-mail à mcaspreview@microsoft.com.

**Le contrôle de session est disponible sur tous les navigateurs de toutes les plateformes majeures, quel que soit le système d’exploitation**. We recommend using Internet Explorer 11, Microsoft Edge (latest), Google Chrome (latest), Mozilla Firefox (latest), or Apple Safari (latest). Access to mobile and desktop apps can also be blocked or allowed.

> [!NOTE]
> Using the **Client app** filter in access policies can cause the resulting user session to be proxied by Cloud App Security.
>
> In access policies, when using the **Client app** filter it defaults to **Mobile and desktop**. This can cause the resulting user session to be proxied by Cloud App Security. To void this behavior, set the value to **Browser**.
>
> By default, evaluating whether an app is mobile or desktop can cause the resulting user session to be proxied by Cloud App Security. To avoid this behavior, set the Client App filter in your Access policies to be equal to **Browser**.

> [!NOTE]
> Cloud App Security s’appuie sur les protocoles TLS (Transport Layer Security) 1.2+ pour fournir un chiffrement de pointe. Les applications clientes natives et les navigateurs qui ne prennent pas en charge TLS 1.2+ ne sont pas accessibles lorsqu’ils sont configurés avec le contrôle de session. Toutefois, les applications SaaS qui utilisent TLS 1.1 ou une version antérieure apparaissent dans le navigateur comme utilisant TLS 1.2+ lorsqu’elles sont configurées avec Cloud App Security.

<a name="featured-apps"></a>By natively integrating with Azure AD, any app that is configured with SAML or Open ID Connect you can onboard any app yourself. In addition, the following apps are featured by Cloud App Security and are already onboarded and ready to use in any tenant:

- AWS
- Azure DevOps (Visual Studio Team Services)
- Portail Azure (préversion)
- Zone
- Concur
- CornerStone on Demand
- DocuSign
- Dropbox
- Dynamics 365 CRM (preview)
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

### <a name="a-ido365-apps-office-365-featured-apps"></a><a id="O365-apps" />Office 365 featured apps

The following is a list of featured apps that are supported in Office 365 Cloud App Security:

- Exchange Online
- OneDrive Entreprise
- Power BI
- SharePodanst Onldanse
- Microsoft Teams (préversion)
- Yammer (préversion)

If you're interested in a specific app being featured, [send us details about the app](mailto:casfeedback@microsoft.com). Envoyez-nous également le cas d’usage qui vous intéresse pour que nous puissions l’intégrer.

> [!div class="step-by-step"]
> [Suivant : Déployer le Contrôle d’accès conditionnel aux applications »](proxy-deployment-aad.md)

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Déployer le Contrôle d’applications par accès conditionnel pour les applications Azure AD](proxy-deployment-aad.md)

[!INCLUDE [Open support ticket](includes/support.md)]
