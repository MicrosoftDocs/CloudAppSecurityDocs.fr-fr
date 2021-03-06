---
title: Connectez les équipes WebEx à Cloud App Security
description: Cet article fournit des informations sur la connexion de votre application WebEx apps à Cloud App Security à l’aide du connecteur API pour la visibilité et le contrôle de l’utilisation.
ms.date: 12/27/2020
ms.topic: how-to
ms.openlocfilehash: 7cc58ee71f57c82aae87332d292fad8cf08894d4
ms.sourcegitcommit: cfa59a538167bd126d64dbd05f04a1957bc035c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/27/2020
ms.locfileid: "97792690"
---
# <a name="connect-cisco-webex-teams-to-microsoft-cloud-app-security"></a>Connectez les équipes Cisco Webex à Microsoft Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Cet article fournit des instructions pour connecter Microsoft Cloud App Security à votre compte Cisco Webex existant à l’aide des API du connecteur. Cette connexion vous offre une visibilité et un contrôle sur les utilisateurs, les activités et les fichiers de WebEx. Pour plus d’informations sur la façon dont Cloud App Security protège les équipes Cisco Webex, consultez [protéger les équipes Cisco Webex](protect-webex.md).

## <a name="prerequisites"></a>Prérequis

- Nous vous suggérons de créer un compte de service dédié pour la connexion. Cela vous permet de voir que les actions de gouvernance effectuées dans WebEx sont effectuées à partir de ce compte, telles que supprimer les messages envoyés dans WebEx. Dans le cas contraire, le nom de l’administrateur qui s’est connecté Cloud App Security à WebEx apparaîtra en tant qu’utilisateur qui a effectué les actions.
- Vous devez disposer des rôles administrateur complet **et** responsable de la conformité dans WebEx (sous rôles **et**  >  **rôles Administrateur** de sécurité).

    ![Rôles WebEx requis](media/connect-webex-roles.png)

## <a name="how-to-connect-webex-to-cloud-app-security"></a>Comment connecter WebEx à Cloud App Security

1. Dans la console Cloud App Security, cliquez sur **Examiner**, puis sur **Applications connectées**.

1. Dans la page **connecteurs d’application** , cliquez sur le bouton plus (+), puis sur **Cisco Webex**.

    ![connecter WebEx](media/cisco-webex.png)

1. Dans la fenêtre contextuelle, entrez le nom de l’instance de ce connecteur.

1. Cliquez sur **connecter Cisco Webex**. La page de connexion WebEx s’ouvre. Entrez vos informations d’identification pour autoriser Cloud App Security accès à l’instance WebEx de votre équipe.

1. WebEx vous demande si vous souhaitez autoriser Cloud App Security accès aux informations de votre équipe, au Journal d’activité et à l’exécution des activités en tant que membre de l’équipe. Pour continuer, cliquez sur **Autoriser**.

1. De retour dans la console Cloud App Security, vous devez recevoir un message indiquant que WebEx a été correctement connecté.

1. Vérifiez que la connexion a réussi en cliquant sur **Tester l’API**.

    Le test peut prendre quelques minutes. Une fois que vous êtes averti que la connexion a réussi, cliquez sur **Fermer**.

Une fois que vous avez connecté WebEx, vous recevrez des événements pendant 7 jours avant la connexion. Cloud App Security analyse les événements au cours des trois derniers mois. Pour augmenter cela, vous devez disposer d’une licence Cisco Webex Pro et ouvrir un ticket avec Cloud App Security Support.

Si vous rencontrez des problèmes lors de la connexion de l’application, consultez [résolution des problèmes liés aux connecteurs d’application](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
