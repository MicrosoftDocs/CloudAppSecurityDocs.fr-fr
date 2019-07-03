---
title: Résoudre les problèmes de contrôle d’accès conditionnel
description: Cet article fournit une liste des problèmes de contrôle d’accès conditionnel possibles et fournit des résolutions possibles.
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: ShlomoSagir-MS
ms.date: 6/30/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: e051d00c118b8e41142f8c0d9cc726675dcea27d
ms.sourcegitcommit: ee00e0033bf45a5f795bfd3e1d71fa1f70f97acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67515040"
---
# <a name="troubleshooting-conditional-access-app-control"></a>Résolution des problèmes de contrôle d’accès conditionnel

*S’applique à : Microsoft Cloud App Security*

Cet article de prohvides une liste de possible de contrôle d’accès conditionnel émet et fournit des résolutions possibles.

## <a name="troubleshooting-onboarded-apps"></a>Résolution des problèmes d’intégration des applications

### <a name="the-sign-in-to-the-app-is-not-working"></a>Connectez-vous à l’application ne fonctionne pas

1. Dans Cloud App Security, dans la barre de menus, cliquez sur la roue dentée des paramètres ![icône des paramètres](./media/settings-icon.png "icône des paramètres") et sélectionnez **contrôle d’accès conditionnel**.
1. Dans la liste des applications, sur la ligne dans laquelle l’application que vous configurez s’affiche, choisissez les points de suspension à la fin de la ligne, puis **modifier application**.
1. Cliquez sur **gestion Nonce** pour développer la section, puis sélectionnez **permettent un traitement nonce**.

    ![Capture d’écran de l’option de gestion de la valeur à usage unique.](media/troubleshooing-nonce-handling.png)

    > [!NOTE]
    > Si vous rencontrez le problème de navigation vers les pages d’application autre que la page d’accueil, consultez [visites suivantes de résolution des problèmes à l’application ne passent pas à la page attendue](#unexpected-page)

### Des visites ultérieures à l’application ne passent pas à la page attendue<a name="unexpected-page"></a>

Les étapes suivantes sont basées sur l’utilisation de Fiddler comme outil de journalisation du trafic. L’expérience peut être différent pour d’autres outils. Pour plus d’informations sur l’utilisation de Fiddler, consultez [moyen aisé de recueillir les journaux de fiddler](https://blogs.msdn.microsoft.com/maheshk/2016/05/03/easy-way-to-collect-fiddler-log-fiddlercap/).

1. Copiez l’URL de page dans l’application n’accède pas à la page attendue : vous en avez besoin plus tard.

    > [!NOTE]
    > Assurez-vous que le domaine n’inclut pas le suffixe d’URL de sécurité d’application Cloud (par exemple, *. us2.cas.ms*)

1. Utiliser un outil de journalisation de trafic tel que Fiddler pour analyser la page.
1. Accédez à l’URL que vous avez copié précédemment et vous authentifier si nécessaire.
1. Dans l’outil de journalisation du trafic, recherchez la demande correspondant au domaine et le chemin d’accès basé sur le protocole que vous utilisez.

    | Protocol | Domaine | Chemin | Nom du champ État |
    | --- | --- | --- | --- |
    | OIDC | `https://login.microsoftonline.com` | /common/oauth2/authorize | state |
    | SAML 2.0 | `https://login.microsoftonline.com` | /*id*/saml2 | RelayState |

1. Sélectionnez la demande, puis, dans le **inspecteurs** onglet, sélectionnez **WebForms**.
1. Créer une chaîne d’expression régulière basée sur le 

## <a name="next-steps"></a>Étapes suivantes

[Déployer Cloud Discovery](set-up-cloud-discovery.md)

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier](https://premier.microsoft.com/)
