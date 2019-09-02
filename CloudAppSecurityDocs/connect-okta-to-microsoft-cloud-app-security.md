---
title: Connecter Okta à Cloud App Security
description: Cet article vous explique comment connecter votre application Okta à Cloud App Security à l’aide du connecteur d’API, afin de bénéficier de plus de contrôle et de visibilité lors de l’utilisation.
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: shsagir
ms.date: 9/1/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 59798c191a90f9be252e42ff9a9d4582f7d2221e
ms.sourcegitcommit: 0b78b13bc163bfcd6f2ae13b1f57acee05e5b423
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2019
ms.locfileid: "70208811"
---
# <a name="connect-okta-to-microsoft-cloud-app-security"></a>Connecter Okta à Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

Cet article fournit des instructions pour connecter Microsoft Cloud App Security à un compte Okta existant à l’aide des API de connecteur. Cette connexion vous permet de bénéficier de plus de visibilité et de contrôle lors de l’utilisation d’Okta.

## <a name="how-to-connect-okta-to-cloud-app-security"></a>Comment connecter Okta à Cloud App Security

1. Nous vous recommandons de créer un compte de service d’administration dans Okta pour Cloud App Security.

    Veillez à utiliser un compte disposant des autorisations de super administrateur.

    Assurez-vous que votre compte Okta est vérifié.

1. Dans la console Okta, cliquez sur **Admin**.

    - Cliquez sur **Security** (Sécurité), puis sur **API**.

         ![Okta - API](./media/okta-api.png "Okta - API")

    - Cliquez sur **Create Token** (Créer un jeton).

         ![Okta - Créer un jeton](./media/okta-createtoken.jpg "Okta - Créer un jeton")

    - Dans la fenêtre contextuelle **Create Token** (Créer un jeton), nommez votre jeton Cloud App Security et cliquez sur **Create Token** (Créer un jeton).

         ![Okta - fenêtre contextuelle de jeton](./media/okta-token-popup.png "Okta - fenêtre contextuelle de jeton")

    - Dans la fenêtre contextuelle **Token created successfully** (Jeton créé), copiez le contenu de **Token value** (Valeur du jeton).

         ![Okta - valeur du jeton](./media/okta-token-value.png "Okta - valeur du jeton")

1. Dans la console Cloud App Security, cliquez sur **Examiner**, puis sur **Applications connectées**.

1. Dans la page **Connecteurs d’application**, cliquez sur le bouton plus (+), puis sur **Okta**.

    ![Okta - connexion](./media/connect-okta.png "Okta - connexion")

1. Dans la fenêtre contextuelle qui s’affiche, dans le champ **Domaine**, entrez votre domaine Okta et collez votre jeton dans le champ **Jeton**.

1. Cliquez sur **Connect** (Connecter) pour créer le jeton pour Okta dans Cloud App Security.

1. Vérifiez la connexion en cliquant sur **Test API** (Tester l’API).

    Le test peut prendre quelques minutes. Une fois averti que la connexion a réussi, cliquez sur **Fermer**.

Après avoir connecté Okta, vous recevez les événements des 60 jours précédant la connexion.

## <a name="next-steps"></a>Étapes suivantes

[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)
