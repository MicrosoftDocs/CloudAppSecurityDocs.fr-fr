---
title: Résolution des problèmes de contrôle d’accès et de session
description: Cet article fournit aux administrateurs des conseils sur la façon d’examiner et de résoudre les contrôles d’accès et de session courants.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 07/15/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: c473128c22f0369725260077b642d75ac50f559f
ms.sourcegitcommit: 1dec09a56cc44148393f103c96fc24c59adc2f8f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86402348"
---
# <a name="troubleshooting-access-and-session-controls"></a>Résolution des problèmes de contrôle d’accès et de session

Cet article fournit aux administrateurs des conseils sur la façon d’examiner et de résoudre les problèmes courants d’accès et de contrôle de session tels qu’ils sont rencontrés par les [administrateurs](#issues-experienced-by-admins) et [les utilisateurs finaux](#issues-experienced-by-end-users).

Avant de continuer, assurez-vous que votre environnement répond aux conditions générales minimales suivantes pour les contrôles d’accès et de session.

- **Licence**: Vérifiez que vous disposez d’une [licence](https://aka.ms/mcaslicensing)valide.
- Authentification **unique (SSO)**: les applications doivent être configurées avec l’une des solutions SSO prises en charge.
  - Azure Active Directory (Azure AD) à l’aide de SAML 2,0 ou OpenID Connect 2,0
  - IdP tiers utilisant SAML 2,0
- **Prise en charge des navigateurs**: les contrôles de session sont disponibles pour les sessions basées sur un navigateur sur les navigateurs pris en charge suivants : Microsoft Edge (dernière version), Google Chrome (dernière version), Mozilla Firefox (dernière version) ou Apple Safari (dernière version)
- **Temps d’arrêt**: Cloud App Security vous permet de définir le comportement par défaut à appliquer en cas d’interruption de service, par exemple un composant qui ne fonctionne pas correctement. Vous pouvez choisir de renforcer (bloquer) ou de contourner (autoriser) les utilisateurs à prendre des mesures sur du contenu potentiellement sensible quand les contrôles de stratégie normaux ne peuvent pas être appliqués. Ce comportement par défaut pendant les temps d’arrêt du système peut être configuré dans le portail Cloud App Security, comme suit : **paramètres**  >  **contrôle d’application par accès conditionnel**  >  **comportement par défaut**  >  **autoriser** ou **bloquer** l’accès.

## <a name="issues-experienced-by-admins"></a>Problèmes rencontrés par les administrateurs

Cette section est destinée aux administrateurs qui configurent les contrôles d’accès et de session avec Cloud App Security et aide à identifier les situations courantes qui peuvent se produire dans les domaines suivants :

|Section|Problèmes|
|---|---|
|[Conditions réseau](#network-conditions)|- [Erreurs réseau lors de la navigation vers une page de navigateur](#network-errors-when-navigating-to-a-browser-page)<br />- [Connexion lente](#slow-login)<br />- [Considérations supplémentaires](#network-conditions-additional-considerations)|
|[Identification de l’appareil](#device-identification)|- [Appareils conformes à Intune non identifiés ou Azure AD Hybride joints](#misidentified-intune-compliant-or-hybrid-azure-ad-joined-devices)<br />- [Les certificats clients ne s’affichent pas quand ils sont attendus](#client-certificates-are-not-prompting-when-expected)<br />- [Les certificats clients demandent à chaque connexion](#client-certificates-are-prompting-at-every-login)<br />- [Considérations supplémentaires](#device-identification-additional-considerations)|
|[Intégration d’une application](#onboarding-an-app)|- [L’application n’apparaît pas sur la page **contrôle d’application par accès conditionnel Apps**](#app-does-not-appear-on-the-conditional-access-app-control-apps-page)<br />- [État de l’application : continuer l’installation](#app-status-continue-setup)<br />- [Impossible de configurer des contrôles pour les applications natives](#cannot-configure-controls-for-native-apps)<br />- [La page **application non reconnue** s’affiche](#something-went-wrong-page-appears)<br />- [L’option de **contrôle de session de demande** s’affiche](#request-session-control-option-appears)<br />- [Considérations supplémentaires](#onboarding-apps-additional-considerations)|
|[Création de stratégies d’accès et de session](#creating-access-and-session-policies)|- [Dans les stratégies d’accès conditionnel, vous ne voyez pas l’option **contrôle d’application par accès conditionnel**](#in-conditional-access-policies-you-cannot-see-the-conditional-access-app-control-option)<br />- [Message d’erreur lors de la création d’une stratégie : aucune application n’est déployée avec contrôle d’application par accès conditionnel](#error-message-when-creating-a-policy-you-dont-have-any-apps-deployed-with-conditional-access-app-control)<br />- [Impossible de créer des stratégies de session pour une application](#cannot-create-session-policies-for-an-app)<br />- [Impossible de choisir la **méthode d’inspection**: service de **classification des données**](#cannot-choose-inspection-method-data-classification-service)<br />- [Impossible de choisir l' **action**: **protéger**](#cannot-choose-action-protect)<br />- [Considérations supplémentaires](#policies-additional-considerations)|

### <a name="network-conditions"></a>Conditions réseau

Les problèmes courants de condition réseau que vous pouvez rencontrer sont les suivants :

- [Erreurs réseau lors de la navigation vers une page de navigateur](#network-errors-when-navigating-to-a-browser-page)
- [Connexion lente](#slow-login)
- [Considérations supplémentaires](#network-conditions-additional-considerations)

#### <a name="network-errors-when-navigating-to-a-browser-page"></a>Erreurs réseau lors de la navigation vers une page de navigateur

Quand vous configurez en premier lieu des contrôles d’accès et de session Cloud App Security pour une application, les erreurs réseau courantes qui peuvent se produire sont notamment les suivantes : « ce site n’est pas sécurisé » et « aucune connexion Internet ». Ces messages peuvent indiquer une erreur de configuration générale du réseau.

**Étapes recommandées**

1. Configurez votre pare-feu pour qu’il fonctionne avec Cloud App Security à l’aide des adresses IP Azure et des noms DNS pertinents pour votre environnement.
    1. Ajoutez le **port de sortie 443** pour les adresses IP et les noms DNS suivants pour votre [Centre de données de Cloud App Security](network-requirements.md#access-and-session-controls).
    1. Redémarrer votre ordinateur et votre session de navigateur
    1. Vérifier que la connexion fonctionne comme prévu
1. Activez TLS 1,2 dans les options Internet de votre navigateur.

    > [!NOTE]
    >
    > - Cloud App Security exploite les protocoles TLS (Transport Layer Security) 1.2 + pour fournir un chiffrement optimal. Les applications clientes natives et les navigateurs qui ne prennent pas en charge TLS 1.2 + ne sont pas accessibles lorsqu’ils sont configurés avec le contrôle de session. Toutefois, les applications SaaS qui utilisent TLS 1.1 ou une version antérieure apparaissent dans le navigateur comme utilisant TLS 1.2+ lorsqu’elles sont configurées avec Cloud App Security.
    > - Alors que les contrôles de session sont créés pour fonctionner avec n’importe quel navigateur sur n’importe quelle plateforme principale sur tout système d’exploitation, nous prenons en charge Microsoft Edge (dernière version), Google Chrome (dernière version), Mozilla Firefox (dernière version) ou Apple Safari (dernière version). L’accès aux applications mobiles et de bureau peut également être bloqué ou autorisé.

    | Navigateur | Étapes |
    |---|---|
    | Microsoft Internet Explorer | 1. Ouvrez Internet Explorer<br />2. Sélectionnez **Outils**  >  **Options Internet**  >  onglet**avancé**<br />3. sous **sécurité**, sélectionnez **TLS 1,2**<br />4. Sélectionnez **appliquer**, puis cliquez sur **OK** .<br />5. Redémarrez votre navigateur et vérifiez que vous pouvez accéder à l’application |
    | Chrome Microsoft Edge/Edge | 1. Ouvrez la recherche à partir de la barre des tâches et recherchez « Options Internet »<br />2. sélectionner les **Options Internet**<br />3. sous **sécurité**, sélectionnez **TLS 1,2**<br />4. Sélectionnez **appliquer**, puis cliquez sur **OK** .<br />5. Redémarrez votre navigateur et vérifiez que vous pouvez accéder à l’application |
    | Google Chrome | 1. Ouvrez Google Chrome<br />2. en haut à droite, cliquez sur **plus** (3 points verticaux) > **paramètres**<br />3. en bas, cliquez sur **avancé** .<br />4. sous **système**, cliquez sur **ouvrir les paramètres de proxy** .<br />5. sous l’onglet **avancé** , sous **sécurité**, sélectionnez **TLS 1,2**<br />6. cliquez sur **OK**<br />7. Redémarrez votre navigateur et vérifiez que vous êtes en mesure d’accéder à l’application |
    | Mozilla Firefox | 1. Ouvrez Mozilla Firefox<br />2. dans la barre d’adresses et recherchez « about : config »<br />3. dans la zone de recherche, recherchez « TLS ».<br />4. double-cliquez sur l’entrée correspondant à **Security. TLS. version. min**<br />5. Définissez la valeur entière sur 3 pour forcer TLS 1,2 comme version minimale requise<br />6. cliquez sur **Enregistrer** (cochez la case à droite de la zone valeur).<br />7. Redémarrez votre navigateur et vérifiez que vous êtes en mesure d’accéder à l’application |
    | Safari | Si vous utilisez Safari version 7 ou ultérieure, TLS 1,2 est automatiquement activé |

#### <a name="slow-login"></a>Connexion lente

Le chaînage de proxy et la gestion à usage unique sont certains des problèmes courants qui peuvent entraîner une lenteur des performances de connexion.

**Étapes recommandées**

1. Configurez votre environnement pour supprimer le pare-feu et le chaînage de proxy direct, en connectant au moins deux serveurs proxy pour accéder à la page prévue, et d’autres facteurs externes pouvant entraîner une lenteur du processus de connexion.
    1. Déterminer si le chaînage de proxy s’est produit dans votre environnement
    1. Supprimer les proxys de transfert supplémentaires dans la mesure du possible
1. Désactivez la gestion des nonce pour vos applications qui n’utilisent pas de valeur à usage unique.

    > [!NOTE]
    > Certaines applications utilisent un hachage de valeur à usage unique pendant l’authentification pour empêcher les attaques par relecture. Par défaut, Cloud App Security suppose qu’une application utilise une valeur à usage unique. Si l’application que vous utilisez n’utilise pas de valeur à usage unique, vous pouvez désactiver la gestion de la valeur à usage unique pour cette application dans Cloud App Security.

    1. Dans Cloud App Security, dans la barre de menus, cliquez sur paramètres roue dentée, puis sélectionnez **contrôle d’application par accès conditionnel**.
    1. Dans la liste des applications, sur la ligne dans laquelle l’application que vous configurez s’affiche, choisissez les trois points à la fin de la ligne, puis choisissez **modifier** l’application.
    1. Cliquez sur la gestion à usage **unique** pour développer la section, puis désactivez l’activation de la **gestion des nonce**.
    1. Déconnectez-vous de l’application et fermez toutes les sessions de navigateur.
    1. Redémarrez votre navigateur et connectez-vous à l’application et vérifiez que la connexion fonctionne comme prévu.

<a name="network-conditions-additional-considerations"></a>

#### <a name="additional-considerations"></a>Considérations supplémentaires

Lors de la résolution des problèmes de réseau, il existe des éléments supplémentaires à prendre en compte concernant le proxy Cloud App Security.

- **La session est acheminée vers un autre centre de données**

    Cloud App Security tire parti des centres de données Azure dans le monde entier pour optimiser les performances grâce à la géolocalisation. Cela signifie que la session d’un utilisateur peut être hébergée en dehors d’une région, en fonction des modèles de trafic et de leur emplacement. Toutefois, pour protéger votre confidentialité, aucune donnée de session n’est stockée dans ces centres de données.

- **Performances du proxy**

    La dérivation d’une ligne de base des performances dépend de nombreux facteurs en dehors du proxy de Cloud App Security, par exemple :

    - Quels sont les autres proxys ou passerelles qui se trouvent en série avec ce proxy
    - Provenance de l’utilisateur
    - Emplacement de la ressource ciblée
    - Demandes spécifiques sur la page

    En général, n’importe quel proxy ajoute la latence. Les avantages du Cloud App Security proxy sont les suivants :

    - Tirant parti de la disponibilité globale des contrôleurs de domaine Azure pour géolocaliser les utilisateurs sur le nœud le plus proche et réduire leur distance d’aller-retour, sur une échelle que quelques services du monde entier ont.
    - Tirer parti de l’intégration avec Azure AD accès conditionnel pour router uniquement les sessions que vous souhaitez envoyer au service à partir de notre service, plutôt que tous les utilisateurs dans toutes les situations.

### <a name="device-identification"></a>Identification de l’appareil

Cloud App Security fournit les options suivantes pour identifier l’état de gestion d’un appareil.

1. Conformité Microsoft Intune
1. Azure AD Hybride joint au domaine
1. Certificats clients

Pour plus d’informations sur l’identification des appareils, consultez [identification des appareils gérés](proxy-intro-aad.md#managed-device-identification).

Les problèmes courants d’identification des appareils que vous pouvez rencontrer sont les suivants :

- [Appareils conformes à Intune non identifiés ou Azure AD Hybride joints](#misidentified-intune-compliant-or-hybrid-azure-ad-joined-devices)
- [Les certificats clients ne s’affichent pas quand ils sont attendus](#client-certificates-are-not-prompting-when-expected)
- [Les certificats clients demandent à chaque connexion](#client-certificates-are-prompting-at-every-login)
- [Considérations supplémentaires](#device-identification-additional-considerations)

#### <a name="misidentified-intune-compliant-or-hybrid-azure-ad-joined-devices"></a>Appareils conformes à Intune non identifiés ou Azure AD Hybride joints

Azure AD l’accès conditionnel permet de transmettre directement les informations d’appareil jointes et conformes à Intune et Azure AD Hybride à Cloud App Security, où l’état de l’appareil peut être utilisé comme filtre pour les stratégies d’accès ou de session. Pour plus d’informations, consultez [Présentation de la gestion des appareils dans Azure Active Directory](/azure/active-directory/devices/overview).

**Étapes recommandées**

1. Dans Cloud App Security, dans la barre de menus, cliquez sur paramètres roue dentée, puis sélectionnez **paramètres**.
1. Sous **contrôle d’application par accès conditionnel**, sélectionnez **identification**de l’appareil. Cette page affiche les options d’identification des appareils disponibles dans Cloud App Security.
1. Pour **identification de l’appareil conforme à Intune** et **Azure ad hybride identification jointe** , cliquez sur **afficher la configuration** et vérifiez que les services sont configurés.

    > [!NOTE]
    > Celles-ci sont automatiquement synchronisées à partir de Azure AD et d’Intune, respectivement.
1. Créez une stratégie d’accès ou de session avec le filtre de **balise d’appareil** égal à **Azure ad hybride joint**, **compatible avec Intune**, ou les deux.
1. Dans un navigateur, connectez-vous à un appareil qui est Azure AD Hybride joint ou Intune conforme en fonction de votre filtre de stratégie.
1. Vérifiez que les activités de ces appareils remplissent le journal. Dans Cloud App Security, dans la page **Journal d’activité** , [filtrez](activity-filters.md) sur la **balise de périphérique** égale à **Azure ad hybride jointe**, **conforme à Intune**ou les deux en fonction de vos filtres de stratégie.
1. Si les activités ne sont pas renseignées dans le journal d’activité Cloud App Security, accédez à Azure AD et procédez comme suit :
    1. Sous **surveillance**des  >  **connexions**, vérifiez qu’il existe des activités de connexion dans les journaux.
    1. Sélectionnez l’entrée de journal appropriée pour l’appareil auquel vous vous êtes connecté.
    1. Dans le volet d' **informations** , sous l’onglet informations sur l' **appareil** , vérifiez que l’appareil est **géré** (Azure ad hybride joint) ou **conforme** (conforme à Intune). Si vous ne pouvez pas vérifier l’un des deux États, essayez une autre entrée du journal ou assurez-vous que les données de votre appareil sont correctement configurées dans Azure AD.
    1. Pour l’accès conditionnel, certains navigateurs peuvent nécessiter une configuration supplémentaire telle que l’installation d’une extension. Utilisez les informations du Guide de [prise en charge du navigateur d’accès conditionnel](/azure/active-directory/conditional-access/concept-conditional-access-conditions#supported-browsers) pour configurer votre navigateur.
    1. Si vous ne voyez toujours pas les informations sur l’appareil dans la page **connexions** , ouvrez un ticket de support pour Azure ad.

#### <a name="client-certificates-are-not-prompting-when-expected"></a>Les certificats clients ne s’affichent pas quand ils sont attendus

Le mécanisme d’identification des appareils peut exiger une authentification desdits appareils à l’aide de certificats clients. Vous pouvez télécharger une racine X. 509 ou une autorité de certification intermédiaire au format de certificat PEM. Ces certificats doivent contenir la clé publique de l’autorité de certification, qui est ensuite utilisée pour signer les certificats clients présentés au cours d’une session. Pour plus d’informations sur les certificats clients, consultez la page [périphériques authentifiés par le certificat client](proxy-intro-aad.md#client-certificate-authenticated-devices).

**Étapes recommandées**

1. Dans Cloud App Security, dans la barre de menus, cliquez sur paramètres roue dentée, puis sélectionnez **paramètres**.
1. Sous **contrôle d’application par accès conditionnel**, sélectionnez **identification**de l’appareil. Cette page affiche les options d’identification des appareils disponibles dans Cloud App Security.
1. Vérifiez que vous avez chargé une autorité de certification racine ou intermédiaire X. 509. Vous devez charger l’autorité de certification utilisée pour signer votre autorité de certification appropriée.
1. Créez une stratégie d’accès ou de session avec le filtre de **balise d’appareil** égal au **certificat client valide**.
1. Assurez-vous que votre certificat client est :
    - déployé à l’aide du format de fichier #12 PKCS, en général une extension de fichier. P12 ou. pfx
    - installé dans le magasin de l’utilisateur, et non dans le magasin de l’appareil, de l’ordinateur que vous utilisez pour le test
1. Redémarrez votre session de navigateur
1. Lors de la connexion à l’application protégée
    - Vérifiez que vous êtes redirigé vers l’URL`<https://*.managed.access-control.cas.ms/aad_login>`
    - Si vous utilisez iOS, vérifiez que vous utilisez le navigateur Safari
    - Si vous utilisez Firefox, vous devez également ajouter le certificat au magasin de certificats de Firefox. Tous les autres navigateurs utilisent le même magasin de certificats par défaut. Découvrez [comment ajouter un certificat au magasin de certificats Firefox](http://www.jscape.com/blog/firefox-client-certificate).
1. Vérifiez que le certificat client est demandé dans votre navigateur.
    - S’il n’apparaît pas, essayez un autre navigateur. La plupart des navigateurs principaux prennent en charge l’exécution d’une vérification de certificat client. Toutefois, les applications mobiles et de bureau utilisent souvent des navigateurs intégrés qui ne prennent peut-être pas en charge cette vérification et affectent donc l’authentification pour ces applications.
1. Vérifiez que les activités de ces appareils remplissent le journal. Dans Cloud App Security, dans la **page Journal d’activité** , [filtrez](activity-filters.md) sur l' **indicateur de périphérique** égal à **certificat client valide**.
1. Si vous ne voyez toujours pas l’invite, ouvrez un [ticket de support](support-and-ts.md) et incluez les informations suivantes :
    - Détails du navigateur ou de l’application native dans laquelle vous avez rencontré le problème
    - Version du système d’exploitation (par exemple, iOS/Android/Windows 10)
    - Indiquez si l’invite fonctionne sur le chrome Edge

#### <a name="client-certificates-are-prompting-at-every-login"></a>Les certificats clients demandent à chaque connexion

Si vous rencontrez le certificat client qui s’ouvre après l’ouverture d’un nouvel onglet, cela peut être dû à des paramètres masqués dans les **Options Internet**.

| Navigateur | Étapes |
|---|---|
| Microsoft Internet Explorer | 1. Ouvrez Internet Explorer<br />2. Sélectionnez **Outils**  >  **Options Internet**  >  onglet**avancé**<br />3. sous **sécurité**, sélectionnez **ne pas demander la sélection d’un certificat client lorsqu’il n’existe qu’un seul certificat**<br />4. Sélectionnez **appliquer**, puis cliquez sur **OK** .<br />5. Redémarrez votre navigateur et vérifiez que vous pouvez accéder à l’application sans les invites supplémentaires |
| Chrome Microsoft Edge/Edge | 1. Ouvrez la recherche à partir de la barre des tâches et recherchez « Options Internet »<br />2. sélectionner les **Options Internet**<br />3. sous **sécurité**, sélectionnez **ne pas demander la sélection d’un certificat client lorsqu’il n’existe qu’un seul certificat**<br />4. Sélectionnez **appliquer**, puis cliquez sur **OK** .<br />5. Redémarrez votre navigateur et vérifiez que vous pouvez accéder à l’application sans les invites supplémentaires |

<a name="device-identification-additional-considerations"></a>

#### <a name="additional-considerations"></a>Considérations supplémentaires

Lors du dépannage de l’identification des appareils, vous devez prendre en compte certains éléments supplémentaires.

- **Protocole de révocation de certificat client**

    Vous pouvez exiger la révocation de certificats pour les certificats clients. Les certificats qui ont été révoqués par l’autorité de certification ne sont plus approuvés. Si vous sélectionnez cette option, tous les certificats doivent être transmis au protocole de liste de révocation de certificats. Si votre certificat client ne contient pas de point de terminaison de liste de révocation de certificats, vous ne pourrez pas vous connecter à partir de l’appareil géré.

### <a name="onboarding-an-app"></a>Intégration d’une application

Vous pouvez intégrer les types d’applications suivants pour les contrôles d’accès et de session :

- Applications à la une : applications fournies avec des contrôles de session prêts à l’emploi, comme indiqué par l’étiquette de **contrôle de session**

- Toutes les applications (personnalisées) : les applications métier (LOB) ou locales personnalisées peuvent être intégrées aux contrôles de session par un administrateur

![Liste de proxy présentant les applications proposées et toutes (personnalisées)](media/troubleshooting-onboarding.png)

Lors de l’intégration d’une application, il est essentiel de veiller à suivre chaque étape des guides de déploiement de proxy :

1. [Déployer des applications proposées avec des contrôles de session](proxy-deployment-aad.md)
1. [Déployer des applications métier personnalisées, des applications SaaS non proposées et des applications locales hébergées via le proxy d’application Azure AD avec des contrôles de session](proxy-deployment-any-app.md)

Les scénarios courants que vous pouvez rencontrer lors de l’intégration d’une application sont les suivants :

- [L’application n’apparaît pas sur la page **contrôle d’application par accès conditionnel Apps**](#app-does-not-appear-on-the-conditional-access-app-control-apps-page)
- [État de l’application : continuer l’installation](#app-status-continue-setup)
- [Impossible de configurer des contrôles pour les applications natives](#cannot-configure-controls-for-native-apps)
- [La page **application non reconnue** s’affiche](#something-went-wrong-page-appears)
- [L’option de **contrôle de session de demande** s’affiche](#request-session-control-option-appears)
- [Considérations supplémentaires](#onboarding-apps-additional-considerations)

#### <a name="app-does-not-appear-on-the-conditional-access-app-control-apps-page"></a>L’application n’apparaît pas sur la page contrôle d’application par accès conditionnel apps

Lors de l’intégration d’une application à contrôle d’application par accès conditionnel, la dernière étape des guides de déploiement consiste à faire en sorte que l’utilisateur final accède à l’application. Les recommandations répertoriées ci-dessous sont des étapes qui peuvent être effectuées si l’application ne s’affiche pas après avoir parcouru les guides.

**Étapes recommandées**

1. Assurez-vous que votre application répond aux conditions préalables de l’application d’accès conditionnel

| Fournisseur d’identité | Validations |
|---|---|
| Azure AD | 1. Assurez-vous que vous disposez d’une licence valide pour Azure AD Premium P1 en plus d’une licence Cloud App Security<br />2. Assurez-vous que l’application utilise le protocole SAML 2,0 ou OpenID Connect.<br />3. Assurez-vous que l’authentification unique de l’application dans Azure AD |
| Tiers | 1. Vérifiez que vous disposez d’une licence Cloud App Security valide.<br />2. créer une application dupliquée<br />3. Assurez-vous que l’application utilise le protocole SAML.<br />4. Vérifiez que vous avez entièrement intégré l’application et que l’état de l’application est **connecté** |

1. Dans votre stratégie de Azure AD, sous la **session**, assurez-vous que la session est forcée à acheminer vers Cloud App Security, ce qui permettra à l’application d’apparaître dans la page **contrôle d’application par accès conditionnel Apps** , comme suit :
    1. contrôle d’application par accès conditionnel est sélectionné
    1. Dans la liste déroulante stratégies intégrées, vérifiez que l’option **analyser uniquement** est sélectionnée.
1. Veillez à accéder à l’application dans une nouvelle session de navigateur à l’aide d’un nouveau mode Incognito ou en vous reconnectant.

#### <a name="app-status-continue-setup"></a>État de l’application : continuer l’installation

L’état d’une application peut varier entre les activités **continuer l’installation**, **connecté**et **aucune**.

Pour les applications connectées via des fournisseurs d’identité (IdP) tiers, si l’installation n’est pas terminée, lorsque vous accédez à l’application, une page s’affiche avec l’état **continuer l’installation**. Procédez comme suit pour terminer l’installation.

**Étapes recommandées**

1. Cliquez sur **continuer l’installation**.
1. Suivez le [Guide de déploiement](proxy-deployment-any-app.md#conf-app) et vérifiez que vous avez effectué toutes les étapes. Portez une attention particulière à ce qui suit :
    1. Veillez à créer une application SAML personnalisée. Vous en avez besoin pour modifier les URL et les attributs SAML qui peuvent ne pas être disponibles dans les applications de la Galerie.
    1. Si votre fournisseur d’identité n’autorise pas la réutilisation du même identificateur (également appelé ID d’entité ou audience), modifiez l’identificateur de l’application d’origine.

#### <a name="cannot-configure-controls-for-native-apps"></a>Impossible de configurer des contrôles pour les applications natives

Les applications natives peuvent être détectées de façon heuristique et vous pouvez utiliser des stratégies d’accès pour les surveiller ou les bloquer. Utilisez les étapes suivantes pour configurer des contrôles pour les applications natives.

**Étapes recommandées**

1. Dans une stratégie d’accès, ajoutez un filtre d' **application cliente** et affectez-lui la valeur **mobile et Desktop**.
1. Sous actions, sélectionnez **bloquer**.
1. Si vous le souhaitez, vous pouvez personnaliser le message de blocage que vos utilisateurs obtiennent lorsqu’ils ne peuvent pas télécharger de fichiers, par exemple « vous devez utiliser un navigateur Web pour accéder à cette application ».
1. Testez et vérifiez que le contrôle fonctionne comme prévu.

#### <a name="app-is-not-recognized-page-appears"></a>La page application non reconnue s’affiche

Cloud App Security pouvez reconnaître plus de 16 000 applications par le biais du catalogue d’applications Cloud (**découvrir**le  ->  **catalogue d’applications Cloud**). Si vous utilisez une application personnalisée configurée Azure AD via l’authentification unique (SSO) qui ne fait pas partie des 16 000 applications, vous allez rencontrer une page **non reconnue** . Pour résoudre le problème, vous devez configurer l’application sur le contrôle d’application par accès conditionnel.

**Étapes recommandées**

1. Dans Cloud App Security, dans la barre de menus, cliquez sur paramètres roue dentée, puis sélectionnez **contrôle d’application par accès conditionnel**.
1. Dans la bannière, cliquez sur **afficher les nouvelles applications**.
1. Dans la liste des nouvelles applications, recherchez l’application que vous intégrez, cliquez sur le **+** signe, puis cliquez sur **Ajouter**.
    1. Indiquez si l’application est une application **personnalisée** ou **standard** .
    1. Suivez les étapes de l’Assistant, assurez-vous que les **domaines définis par l’utilisateur** spécifiés sont corrects pour l’application que vous configurez.
1. Vérifiez que l’application s’affiche dans la page **contrôle d’application par accès conditionnel Apps** .

#### <a name="request-session-control-option-appears"></a>L’option de contrôle de session de demande s’affiche

Après avoir ajouté une application, vous pouvez voir l’option de **contrôle de session de demande** . Cela se produit parce que seules les applications proposées possèdent des contrôles de session prêts à l’emploi. Pour toute autre application, vous devez passer par un processus d’intégration automatique.

**Étapes recommandées**

1. Dans Cloud App Security, dans la barre de menus, cliquez sur paramètres roue dentée, puis sélectionnez **paramètres**.
1. Sous **contrôle d’application par accès conditionnel**, sélectionnez **intégration/maintenance**de l’application.
1. Entrez le nom d’utilisateur principal ou l’adresse de messagerie des utilisateurs qui intégreront l’application, puis cliquez sur **Enregistrer**.
1. Accédez à l’application que vous déployez. La page que vous voyez varie selon que l’application est reconnue ou non. Effectuez l’une des actions suivantes :

    | État de l’application | Description | Étapes |
    | --- | --- | --- |
    | Non reconnu | Une page application non reconnue s’affiche et vous invite à configurer votre application. | 1. [Ajoutez l’application à contrôle d’application par accès conditionnel](proxy-deployment-any-app.md#add-app).<br /> 2. [Ajoutez les domaines pour l’application](proxy-deployment-any-app.md#add-domains), puis revenez à l’application et actualisez la page.<br /> 3. [Installez les certificats pour l’application](proxy-deployment-any-app.md#install-certs). |
    | Reconnu | Une page d’intégration s’affiche pour vous inviter à poursuivre le processus de configuration de l’application. | - [Installez les certificats pour l’application](proxy-deployment-any-app.md#install-certs). <br /><br /> **Remarque :** Assurez-vous que l’application est configurée avec tous les domaines requis pour que l’application fonctionne correctement. Pour configurer des domaines supplémentaires, continuez à [Ajouter les domaines pour l’application](proxy-deployment-any-app.md#add-domains), puis revenez à la page de l’application. |

<a name="onboarding-apps-additional-considerations"></a>

#### <a name="additional-considerations"></a>Considérations supplémentaires

Lors du dépannage des applications d’intégration, vous devez prendre en compte certains éléments supplémentaires.

- **Les applications de contrôle d’application par accès conditionnel ne s’alignent pas avec les applications Azure AD**

    Les noms des applications dans Azure AD et Cloud App Security peuvent varier en fonction de la façon dont les produits identifient les applications. Cloud App Security identifie les applications à l’aide des domaines de l’application et les ajoute au catalogue d’applications [Cloud](risk-score.md#the-cloud-app-catalog), où nous avons plus de 16 000 applications. Dans chaque application, vous pouvez afficher ou ajouter au sous-ensemble de domaines. En revanche, Azure AD identifie les applications à l’aide de principaux de service. Pour plus d’informations, consultez [objets du principal du service et de l’application dans Azure ad](/azure/active-directory/develop/app-objects-and-service-principals).

    Dans la pratique, cela signifie que la sélection de **SharePoint Online** dans Azure ad équivaut à sélectionner des applications, telles que Word Online et Teams, dans Cloud App Security, car les applications utilisent le `sharepoint.com` domaine.

### <a name="creating-access-and-session-policies"></a>Création de stratégies d’accès et de session

Cloud App Security fournit les stratégies configurables suivantes :

1. [Stratégies d’accès](access-policy-aad.md): pour surveiller ou bloquer l’accès aux applications de navigateur, mobiles et/ou de bureau
1. [Stratégies de session](session-policy-aad.md). Pour surveiller, bloquer et effectuer des actions spécifiques pour empêcher les scénarios d’infiltration et d’exfiltration de données dans le navigateur

Pour utiliser ces stratégies dans Cloud App Security, vous devez d’abord configurer une stratégie dans Azure AD un accès conditionnel pour étendre les contrôles de session, comme suit : dans la stratégie de Azure AD, sous **contrôles d’accès**, cliquez sur **session**, sélectionnez **utiliser contrôle d’application par accès conditionnel** , puis choisissez une stratégie intégrée (**surveiller uniquement** ou **bloquer les téléchargements**) ou **utiliser une stratégie personnalisée** pour définir une stratégie avancée dans Cloud App Security, puis cliquez sur **Sélectionner**.

Les scénarios courants que vous pouvez rencontrer lors de la configuration de ces stratégies sont les suivants :

- [Dans les stratégies d’accès conditionnel, vous ne voyez pas l’option **contrôle d’application par accès conditionnel**](#in-conditional-access-policies-you-cannot-see-the-conditional-access-app-control-option)
- [Message d’erreur lors de la création d’une stratégie : aucune application n’est déployée avec contrôle d’application par accès conditionnel](#error-message-when-creating-a-policy-you-dont-have-any-apps-deployed-with-conditional-access-app-control)
- [Impossible de créer des stratégies de session pour une application](#cannot-create-session-policies-for-an-app)
- [Impossible de choisir la **méthode d’inspection**: service de **classification des données**](#cannot-choose-inspection-method-data-classification-service)
- [Impossible de choisir l' **action**: **protéger**](#cannot-choose-action-protect)
- [Considérations supplémentaires](#policies-additional-considerations)

#### <a name="in-conditional-access-policies-you-cannot-see-the-conditional-access-app-control-option"></a>Dans les stratégies d’accès conditionnel, vous ne voyez pas l’option contrôle d’application par accès conditionnel

Pour acheminer des sessions vers Cloud App Security, Azure AD stratégies d’accès conditionnel doivent être configurées pour inclure des contrôles de session de contrôle d’application par accès conditionnel.

**Étapes recommandées**

- Si vous ne voyez pas l’option **contrôle d’application par accès conditionnel** dans votre stratégie d’accès conditionnel, vérifiez que vous disposez d’une licence valide pour Azure ad Premium P1, ainsi qu’une licence Cloud App Security valide.

#### <a name="error-message-when-creating-a-policy-you-dont-have-any-apps-deployed-with-conditional-access-app-control"></a>Message d’erreur lors de la création d’une stratégie : aucune application n’est déployée avec contrôle d’application par accès conditionnel

Lors de la création d’une stratégie d’accès ou de session, le message d’erreur suivant peut s’afficher : « aucune application n’est déployée avec contrôle d’application par accès conditionnel ». Cette erreur indique que l’application n’a pas été déployée.

**Étapes recommandées**

1. Dans Cloud App Security, dans la barre de menus, cliquez sur paramètres roue dentée, puis sélectionnez **contrôle d’application par accès conditionnel**.
1. Si vous voyez le message **aucune application connectée**, utilisez le guide suivant pour déployer des applications :

    - [Déployer les applications proposées pour lesquelles le contrôle de session est activé](proxy-deployment-aad.md)
    - [Déployez des applications métier personnalisées, des applications SaaS non proposées et des applications locales](proxy-deployment-any-app.md) hébergées via le proxy d’application Azure Active Directory (Azure AD) avec des contrôles de session
1. Si vous rencontrez des problèmes lors du déploiement de l’application, consultez [intégration d’une application](#onboarding-an-app).

#### <a name="cannot-create-session-policies-for-an-app"></a>Impossible de créer des stratégies de session pour une application

Après avoir ajouté une application personnalisée, dans la page **contrôle d’application par accès conditionnel Apps** , vous pouvez voir l’option : **demander un contrôle de session**.

> [!NOTE]
> [Applications à la une](proxy-intro-aad.md#session-controls) disposez de contrôles de session prêts à l’emploi. Pour toutes les autres applications, vous devez passer par un processus d’intégration automatique.

**Étapes recommandées**

1. Utilisez le Guide d’auto-intégration suivant pour déployer n’importe quelle application dans le contrôle de session : déployer des applications [métier personnalisées, des applications SaaS non proposées et des applications locales](proxy-deployment-any-app.md) hébergées via le proxy d’application Azure Active Directory (Azure AD) avec des contrôles de session.
1. Créez une stratégie de session, sélectionnez le filtre d' **application** , assurez-vous que votre application est maintenant répertoriée dans la liste déroulante.

#### <a name="cannot-choose-inspection-method-data-classification-service"></a>Impossible de choisir la **méthode d’inspection**: service de **classification des données**

Dans les stratégies de session, lors de l’utilisation du type de contrôle de session de **Téléchargement du fichier de contrôle (avec inspection)** , vous pouvez utiliser la méthode d’inspection du **service de classification des données** pour analyser vos fichiers en temps réel et détecter le contenu sensible qui correspond à l’un des critères que vous avez configurés. Si la méthode d’inspection du **service de classification des données** n’est pas disponible, procédez comme suit pour examiner le problème.

**Étapes recommandées**

1. Vérifiez que le **type de contrôle de session** est défini sur **contrôler le téléchargement de fichiers (avec inspection)**.

    > [!NOTE]
    > La méthode d’inspection du **service de classification des données** est disponible uniquement pour l’option contrôler le téléchargement du **fichier (avec inspection)** .

1. Déterminez si la fonctionnalité **service de classification des données** est disponible dans votre [région](dcs-inspection.md).
    1. Si la fonctionnalité n’est pas disponible dans votre région, utilisez la méthode **d’inspection DLP intégrée** .
    1. Si la fonctionnalité est disponible dans votre région, mais que vous ne voyez toujours pas la méthode d’inspection du **service de classification des données** , ouvrez un ticket de [support](support-and-ts.md).

#### <a name="cannot-choose-action-protect"></a>Impossible de choisir l’action : protéger

Dans les stratégies de session, lors de l’utilisation du type de contrôle de session de **Téléchargement du fichier de contrôle (avec inspection)** , en plus des actions d' **analyse** et de **blocage** , vous pouvez spécifier l’action de **protection** . Cette action vous permet d’autoriser les téléchargements de fichiers avec l’option de chiffrement ou d’application des autorisations sur le fichier en fonction des conditions, de l’inspection du contenu ou des deux. Si l’action de **protection** n’est pas disponible, procédez comme suit pour examiner le problème.

**Étapes recommandées**

1. Si l’action de **protection** n’est pas disponible ou est grisée, vérifiez que vous disposez de la licence Premium P1 de l’Azure information protection (AIP). Pour plus d’informations, consultez [Azure Information Protection integration](azip-integration.md) (Intégration d’Azure Information Protection).
1. Si l’action de **protection** est disponible, mais ne voit pas les étiquettes appropriées.
    1. Dans Cloud App Security, dans la barre de menus, cliquez sur paramètres roue dentée, sélectionnez **Azure information protection**, puis vérifiez que l’intégration aip est activée.
    1. Pour les étiquettes Office, dans le portail AIP, assurez-vous que l' **étiquetage unifié** est sélectionné.

<a name="policies-additional-considerations"></a>

#### <a name="additional-considerations"></a>Considérations supplémentaires

Lors du dépannage des applications d’intégration, vous devez prendre en compte certains éléments supplémentaires.

- **Comprendre la différence entre les paramètres de stratégie d’accès conditionnel Azure AD : « surveiller uniquement », « bloquer les téléchargements » et « utiliser une stratégie personnalisée »**

    Dans Azure AD des stratégies d’accès conditionnel, vous pouvez configurer les contrôles de Cloud App Security intégrés suivants : **surveiller uniquement** et **bloquer les téléchargements**. Cela s’applique et applique la fonctionnalité de proxy Cloud App Security pour les applications Cloud et les conditions configurées dans Azure AD. Pour les stratégies plus complexes, sélectionnez **utiliser une stratégie personnalisée**, qui vous permet de configurer les stratégies d’accès et de session dans Cloud App Security.

- **Fonctionnement de l’option de filtre d’application cliente « mobile et bureau » dans les stratégies d’accès**

    Dans Cloud App Security les stratégies d’accès, sauf si le filtre d' **application cliente** est spécifiquement défini sur **mobile et Desktop**, la stratégie d’accès résultante s’appliquera uniquement aux sessions de navigateur. La raison en est d’empêcher le proxy par inadvertance des sessions utilisateur, qui peut être un sous-utilisateur de l’utilisation de ce filtre.

## <a name="issues-experienced-by-end-users"></a>Problèmes rencontrés par les utilisateurs finaux

Cette section est destinée aux utilisateurs finaux qui utilisent des applications protégées par Cloud App Security et permet d’identifier les situations courantes qui peuvent se produire dans les domaines suivants :

- [La page d’analyse utilisateur n’apparaît pas](#user-monitoring-page-is-not-appearing)
- [Impossible d’accéder à l’application à partir d’un fournisseur d’identité tiers](#not-able-to-access-app-from-a-third-party-identity-provider)
- [**Une page incorrecte** s’affiche](#something-went-wrong-page-appears)
- [Les actions du presse-papiers ou les contrôles de fichier ne sont pas bloqués](#clipboard-actions-or-file-controls-are-not-being-blocked)
- [Les téléchargements ne sont pas protégés](#downloads-are-not-being-protected)
- [Considérations supplémentaires](#app-additional-considerations)

### <a name="user-monitoring-page-is-not-appearing"></a>La page d’analyse utilisateur n’apparaît pas

Lors du routage d’un utilisateur via l’Cloud App Security, vous pouvez informer l’utilisateur que sa session sera analysée. Par défaut, la page surveillance de l’utilisateur est activée.

**Étapes recommandées**

1. Dans Cloud App Security, dans la barre de menus, cliquez sur paramètres roue dentée, puis sélectionnez **paramètres**.
1. Sous **contrôle d’application par accès conditionnel**, sélectionnez **analyse utilisateur**. Cette page affiche les options d’analyse utilisateur disponibles dans Cloud App Security.

    ![Capture d’écran montrant les options d’analyse utilisateur](media/proxy-user-monitoring.png)

1. Vérifiez que l’option **notifier les utilisateurs que leur activité est analysée** est sélectionnée.
1. Indiquez si vous souhaitez utiliser le message par défaut ou fournir un message personnalisé.

    | type de message | Détails |
    | --- | --- |
    | Default | **En-tête**:<br />L’accès à [nom de l’application s’affiche ici] est analysé<br />**Corps du message**:<br />Pour améliorer la sécurité, votre organisation autorise l’accès à [le nom de l’application s’affiche ici] en mode analyse. L’accès est disponible uniquement à partir d’un navigateur Web. |
    | Custom | **En-tête**:<br />Utilisez cette zone pour fournir un titre personnalisé pour informer les utilisateurs qu’ils sont surveillés.<br />**Corps du message**:<br />Utilisez cette zone pour ajouter des informations personnalisées supplémentaires à l’utilisateur, telles que les personnes à contacter avec les questions, et prend en charge les entrées suivantes : texte brut, texte enrichi, liens hypertexte. |
1. Cliquez sur **Aperçu** pour vérifier la page surveillance de l’utilisateur qui s’affiche avant d’accéder à une application.
1. Cliquez sur **Enregistrer**.

### <a name="not-able-to-access-app-from-a-third-party-identity-provider"></a>Impossible d’accéder à l’application à partir d’un fournisseur d’identité tiers

Si un utilisateur final reçoit une défaillance générale après s’être connecté à une application à partir d’un fournisseur d’identité tiers, validez la configuration IdP tierce.

**Étapes recommandées**

1. Dans Cloud App Security, dans la barre de menus, cliquez sur paramètres roue dentée, puis sélectionnez **contrôle d’application par accès conditionnel**.
1. Dans la liste des applications, sur la ligne dans laquelle l’application à laquelle vous n’êtes pas en mesure d’accéder apparaît, choisissez les trois points à la fin de la ligne, puis choisissez **modifier** l’application.
    1. Vérifier que le certificat SAML téléchargé est correct
    1. Vérifier que les URL SSO valides ont été fournies dans la configuration de l’application
    1. Vérifiez que les attributs et les valeurs de l’application personnalisée sont reflétés dans la capture d’écran des paramètres du fournisseur d’identité ![ indiquant rassembler les fournisseurs d’identité SAML information page](media/proxy-deploy-add-idp-ext-conf.png)
1. Si vous ne pouvez toujours pas accéder à l’application, ouvrez un [ticket de support](support-and-ts.md).

### <a name="something-went-wrong-page-appears"></a>Une page incorrecte s’affiche

Parfois, une page **incorrecte** peut apparaître au cours d’une session de proxy. Ceci peut se produire quand :

1. Un utilisateur se connecte après une période d’inactivité pendant un certain temps
1. L’actualisation du navigateur et le chargement de la page prennent plus de temps que prévu
1. L’application IdP tierce n’est pas configurée correctement

**Étapes recommandées**

1. Si l’utilisateur final tente d’accéder à une application configurée à l’aide d’un fournisseur d’identité tiers, consultez Impossible d’accéder à l' [application à partir d’un IDP tiers](#not-able-to-access-app-from-a-third-party-identity-provider) et état de l' [application : continuer l’installation](#app-status-continue-setup).
1. Si l’utilisateur final a atteint cette page de manière inattendue, procédez comme suit :
    1. Redémarrez votre session de navigateur
    1. Effacer l’historique, les cookies et le cache à partir du navigateur

### <a name="clipboard-actions-or-file-controls-are-not-being-blocked"></a>Les actions du presse-papiers ou les contrôles de fichier ne sont pas bloqués

La possibilité de bloquer des actions du presse-papiers, telles que couper, copier, coller et des contrôles de fichiers tels que le téléchargement, le téléchargement et l’impression, est nécessaire pour éviter les scénarios d’infiltration et d’infiltration de données. Cette capacité permet aux entreprises d’équilibrer la sécurité et la productivité des utilisateurs finaux. Si vous rencontrez des problèmes avec ces fonctionnalités, procédez comme suit pour examiner le problème.

**Étapes recommandées**

Si la session est en cours de proxy, procédez comme suit pour vérifier la stratégie :

1. Dans Cloud App Security, sous **examiner**, sélectionnez **Journal d’activité**.
1. Utilisez le filtre avancé, sélectionnez **action appliquée** et définissez sa valeur sur **bloqué**.
1. Vérifiez que des activités de fichiers sont bloquées.
    1. S’il existe une activité, développez le tiroir activité en cliquant sur l’activité.
    1. Dans l’onglet **général** de la caisse de l’activité, cliquez sur le lien stratégies correspondantes pour vérifier que la stratégie que vous avez appliquée est présente.
    1. Si vous ne voyez pas votre stratégie, consultez [création de stratégies d’accès et de session](#creating-access-and-session-policies).
    1. Si vous voyez **accès bloqué/autorisé en raison du comportement par défaut**, cela indique que le système est inactif et que le comportement par défaut a été appliqué.
        1. Pour modifier le comportement par défaut, dans Cloud App Security, dans la barre de menus, cliquez sur paramètres roue dentée et sélectionnez **paramètres**. Ensuite, sous **contrôle d’application par accès conditionnel**, sélectionnez **comportement par défaut**et définissez le comportement par défaut sur **autoriser** ou **bloquer** l’accès.
        1. Accédez à `https://status.cloudappsecurity.com/` et surveillez les notifications sur les temps d’arrêt du système.
1. Si vous ne parvenez toujours pas à voir l’activité bloquée, ouvrez un [ticket de support](support-and-ts.md).

### <a name="downloads-are-not-being-protected"></a>Les téléchargements ne sont pas protégés

En tant qu’utilisateur final, il peut être nécessaire de télécharger des données sensibles sur un appareil non géré. Dans ces scénarios, vous pouvez protéger des documents avec Azure Information Protection. Si l’utilisateur final n’a pas pu chiffrer le document, suivez les étapes ci-dessous pour examiner le problème.

**Étapes recommandées**

1. Dans Cloud App Security, sous **examiner**, sélectionnez **Journal d’activité**.
1. Utilisez le filtre avancé, sélectionnez **action appliquée** et définissez sa valeur sur **protégé**.
1. Vérifiez que des activités de fichiers sont bloquées.
    1. S’il existe une activité, développez le tiroir activité en cliquant sur l’activité.
    1. Dans l’onglet **général** de la caisse de l’activité, cliquez sur le lien stratégies correspondantes pour vérifier que la stratégie que vous avez appliquée est présente.
    1. Si vous ne voyez pas votre stratégie, consultez [création de stratégies d’accès et de session](#creating-access-and-session-policies).
    1. Si vous voyez **accès bloqué/autorisé en raison du comportement par défaut**, cela indique que le système est inactif et que le comportement par défaut a été appliqué.
        1. Pour modifier le comportement par défaut, dans Cloud App Security, dans la barre de menus, cliquez sur paramètres roue dentée, puis sélectionnez **paramètres**. Ensuite, sous **contrôle d’application par accès conditionnel**, sélectionnez **comportement par défaut**et définissez le comportement par défaut sur **autoriser** ou **bloquer** l’accès.
        1. Accédez à `https://status.cloudappsecurity.com/` et surveillez les notifications sur les temps d’arrêt du système.
    1. Si vous protégez le fichier avec une étiquette AIP ou des autorisations personnalisées, dans la description de l' **activité**, assurez-vous que l’extension de fichier est l’un des types de fichiers pris en charge suivants :
        - Word : docm, docx, dotm, dotx
        - Excel : xlam, xlsm, xlsx, xltx
        - PowerPoint : potm, potx, ppsx, ppsm, pptm, pptx
        - PDF * Si l’étiquetage unifié est activé
    - Si le type de fichier n’est pas pris en charge, dans la stratégie de session, vous pouvez sélectionner **bloquer le téléchargement de tout fichier qui n’est pas pris en charge par la protection native ou lorsque la protection native est infructueuse**.
1. Si vous ne parvenez toujours pas à voir l’activité bloquée, ouvrez un [ticket de support](support-and-ts.md).

<a name="app-additional-considerations"></a>

### <a name="additional-considerations"></a>Considérations supplémentaires

Lors de la résolution des problèmes d’applications, il existe des éléments supplémentaires à prendre en compte.

- **Prise en charge des contrôles de session pour les navigateurs modernes**

    Les contrôles de session Cloud App Security incluent désormais la prise en charge du nouveau navigateur Microsoft Edge basé sur Chromium. Alors que nous continuerons à prendre en charge les versions les plus récentes d’Internet Explorer et de la version héritée de Microsoft Edge, la prise en charge sera limitée et nous vous recommandons d’utiliser le nouveau navigateur Microsoft Edge.

- **Double connexion**

    Une double connexion se produit en raison de l’utilisation présumée d’une valeur à usage unique, un jeton de chiffrement utilisé par les applications pour empêcher les attaques par relecture. Par défaut, Cloud App Security suppose qu’une application utilise une valeur à usage unique. Si vous êtes certain que l’application n’utilise pas de valeur à usage unique, vous pouvez désactiver ce mode en modifiant l’application dans Cloud App Security et le problème sera résolu. Pour connaître la procédure de désactivation de la valeur à usage unique, consultez [connexion lente](#slow-login).

    Si l’application utilise une valeur à usage unique et que cette fonctionnalité ne peut pas être désactivée, la deuxième connexion peut être transparente pour les utilisateurs, ou elle peut être invitée à se reconnecter.

- **L’aperçu ou l’impression des fichiers PDF peut être bloqué**

    Il s’agit d’un comportement normal lorsque vous avez une stratégie configurée pour bloquer les téléchargements. Parfois, lors de l’affichage de l’aperçu ou de l’impression des fichiers PDF, les applications lancent un téléchargement du fichier provoquant l’intervention d’Cloud App Security pour s’assurer que le téléchargement est bloqué et que les données ne sont pas divulguées à partir de votre environnement.

    Si vous souhaitez autoriser les téléchargements de fichiers PDF, vous pouvez exclure des fichiers PDF en fonction de leur extension de fichier dans la stratégie de session appropriée.
