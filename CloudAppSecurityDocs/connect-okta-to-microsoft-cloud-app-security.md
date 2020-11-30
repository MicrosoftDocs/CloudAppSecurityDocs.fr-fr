---
title: Connecter Okta à Cloud App Security
description: Cet article vous explique comment connecter votre application Okta à Cloud App Security à l’aide du connecteur d’API, afin de bénéficier de plus de contrôle et de visibilité lors de l’utilisation.
ms.date: 9/1/2019
ms.topic: how-to
ms.openlocfilehash: 511988d7383ad58d7f572d6c0c3ff1319ed4c92b
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96312605"
---
# <a name="connect-okta-to-microsoft-cloud-app-security"></a>Connecter Okta à Microsoft Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Cet article fournit des instructions pour connecter Microsoft Cloud App Security à un compte Okta existant à l’aide des API de connecteur. Cette connexion vous permet de bénéficier de plus de visibilité et de contrôle lors de l’utilisation d’Okta. Pour plus d’informations sur la façon dont Cloud App Security protège les Okta, consultez [protéger Okta](protect-okta.md).

## <a name="how-to-connect-okta-to-cloud-app-security"></a>Comment connecter Okta à Cloud App Security

1. Nous vous recommandons de créer un compte de service d’administration dans Okta pour Cloud App Security.

    Veillez à utiliser un compte disposant des autorisations de super administrateur.

    Assurez-vous que votre compte Okta est vérifié.

1. Dans la console Okta, cliquez sur **Admin**.

    - Cliquez sur **Security** (Sécurité), puis sur **API**.

         ![API Okta](media/okta-api.png "API Okta")

    - Cliquez sur **créer un jeton**.

         ![Okta créer un jeton](media/okta-createtoken.jpg "Okta créer un jeton")

    - Dans la fenêtre contextuelle **Create Token** (Créer un jeton), nommez votre jeton Cloud App Security et cliquez sur **Create Token** (Créer un jeton).

         ![Fenêtre contextuelle de jeton Okta](media/okta-token-pop-up.png)

    - Dans la fenêtre contextuelle **Token created successfully** (Jeton créé), copiez le contenu de **Token value** (Valeur du jeton).

         ![Valeur du jeton Okta](media/okta-token-value.png "Valeur du jeton Okta")

1. Dans la console Cloud App Security, cliquez sur **Examiner**, puis sur **Applications connectées**.

1. Dans la page **Connecteurs d’application**, cliquez sur le bouton plus (+), puis sur **Okta**.

    ![connecter Okta](media/connect-okta.png "connecter Okta")

1. Dans la fenêtre contextuelle, dans le champ **domaine** , entrez votre domaine Okta et collez votre jeton dans le champ **jeton** .

1. Cliquez sur **Connect** (Connecter) pour créer le jeton pour Okta dans Cloud App Security.

1. Vérifiez que la connexion a réussi en cliquant sur **Tester l’API**.

    Le test peut prendre quelques minutes. Une fois averti que la connexion a réussi, cliquez sur **Fermer**.

Après avoir connecté Okta, vous recevez les événements des 60 jours précédant la connexion.

Si vous rencontrez des problèmes lors de la connexion de l’application, consultez [résolution des problèmes liés aux connecteurs d’application](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
