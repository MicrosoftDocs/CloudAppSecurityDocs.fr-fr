---
title: Résoudre les contrôle d’application par accès conditionnel
description: Cet article fournit une liste des problèmes contrôle d’application par accès conditionnel possibles et fournit des solutions possibles.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 6/30/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 71126072096d9a2ba156c6c3e6b3c17dc0d619b3
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74460108"
---
# <a name="troubleshooting-conditional-access-app-control"></a>Résolution des problèmes contrôle d’application par accès conditionnel

*S’applique à : Microsoft Cloud App Security*

Cet article prohvides une liste des problèmes contrôle d’application par accès conditionnel possibles et fournit des solutions possibles.

## <a name="troubleshooting-onboarded-apps"></a>Dépannage des applications intégrées

### <a name="the-sign-in-to-the-app-is-not-working"></a>La connexion à l’application ne fonctionne pas

1. Dans Cloud App Security, dans la barre de menus, cliquez sur l' ![icône](./media/settings-icon.png "icône des paramètres") paramètres roue dentée paramètres, puis sélectionnez **contrôle d’application par accès conditionnel**.
1. Dans la liste des applications, sur la ligne dans laquelle l’application que vous configurez s’affiche, choisissez les trois points à la fin de la ligne, puis choisissez **modifier l’application**.
1. Cliquez sur la gestion à usage **unique** pour développer la section, puis sélectionnez **activer la gestion des nonce**.

    ![Capture d’écran de l’option de gestion de la valeur à usage unique.](media/troubleshooing-nonce-handling.png)

    > [!NOTE]
    > Si vous rencontrez des problèmes lors de la navigation vers des pages d’application autres que la page d’hébergement, consultez [la page résolution des problèmes de visites ultérieures à l’application ne pas accéder à la page attendue](#unexpected-page)

### Les visites suivantes de l’application n’accèdent pas à la page attendue<a name="unexpected-page"></a>

Les étapes suivantes sont basées sur l’utilisation de Fiddler comme outil de journalisation du trafic. L’expérience peut être différente pour d’autres outils. Pour plus d’informations sur l’utilisation de Fiddler, consultez [méthode simple pour collecter le journal Fiddler](https://blogs.msdn.microsoft.com/maheshk/2016/05/03/easy-way-to-collect-fiddler-log-fiddlercap/).

1. Copiez l’URL de la page de l’application qui n’atteint pas la page attendue : vous en aurez besoin plus tard.

    > [!NOTE]
    > Assurez-vous que le domaine n’inclut pas le suffixe d’URL Cloud App Security (par exemple, *. US2.cas.ms*)

1. Utilisez un outil de journalisation du trafic tel que Fiddler pour surveiller la page.
1. Accédez à l’URL que vous avez copiée précédemment et authentifiez-vous si nécessaire.
1. Dans l’outil de journalisation du trafic, recherchez la demande correspondant au domaine et au chemin d’accès en fonction du protocole que vous utilisez.

    | Protocol | domaine. | Path | Nom du champ d’État |
    | --- | --- | --- | --- |
    | OIDC | `https://login.microsoftonline.com` | /common/oauth2/authorize | state |
    | SAML 2.0 | `https://login.microsoftonline.com` | *ID*de //Saml2 | RelayState |

1. Sélectionnez la demande, puis sous l’onglet **inspecteurs** , sélectionnez **WebForms**.
1. Créer une chaîne Regex basée sur 

## <a name="next-steps"></a>Étapes suivantes

[Déployer Cloud Discovery](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]
