---
title: Connecter Azure à Cloud App Security
description: Cet article vous explique comment connecter Azure à Cloud App Security à l’aide du connecteur d’API, afin de bénéficier de plus de contrôle et de visibilité lors de l’utilisation.
ms.date: 12/27/2020
ms.topic: how-to
ms.openlocfilehash: eb95630ac08763fa6b87a6fab410ec3629010ec8
ms.sourcegitcommit: 40d17309b8729eb914ea91ba5fa7017340231488
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/29/2020
ms.locfileid: "97808910"
---
# <a name="connect-azure-to-microsoft-cloud-app-security"></a>Connecter Azure à Microsoft Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Cet article fournit des instructions pour connecter Microsoft Cloud App Security à un compte Azure existant à l’aide de l’API de connecteur d’applications. Cette connexion vous permet de bénéficier de plus de visibilité et de contrôle lors de l’utilisation d’Azure. Pour plus d’informations sur la façon dont Cloud App Security protège Azure, consultez [protéger Azure](protect-azure.md).

## <a name="how-to-connect-azure-to-cloud-app-security"></a>Comment connecter Azure à Cloud App Security

> [!NOTE]
>
> - L’utilisateur doit être un administrateur global ou de sécurité dans Azure AD pour connecter Azure à Microsoft Cloud App Security.
> - Cloud App Security affiche les activités de **tous** les abonnements.
> - Les informations de compte d’utilisateur sont renseignées dans Cloud App Security lorsque les utilisateurs effectuent des activités dans Azure.
> - Actuellement, Cloud App Security surveille uniquement les activités ARM.

1. Dans la page **applications connectées** , cliquez sur le bouton plus, puis sélectionnez **Microsoft Azure**.

    ![connecter un élément de menu Azure](media/connect-azure-menu.png)

2. Dans la fenêtre contextuelle Azure, cliquez sur **Connecter Microsoft Azure**.

    ![connecter Azure](media/connect-azure.png)

> [!NOTE]
> Une fois Azure connecté, les données sont tirées (pull). À partir de maintenant, vous pouvez voir les données.

Si vous rencontrez des problèmes lors de la connexion de l’application, consultez [résolution des problèmes liés aux connecteurs d’application](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
