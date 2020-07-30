---
title: Connecter Azure à Cloud App Security
description: Cet article vous explique comment connecter Azure à Cloud App Security à l’aide du connecteur d’API, afin de bénéficier de plus de contrôle et de visibilité lors de l’utilisation.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: c12e2d09d9ef9adff32907795c37a86183ded964
ms.sourcegitcommit: 5cf263c4094f5ac91210b03d085ca3dbca50f32d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87388658"
---
# <a name="connect-azure-to-microsoft-cloud-app-security"></a>Connecter Azure à Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

Cet article fournit des instructions pour connecter Microsoft Cloud App Security à un compte Azure existant à l’aide de l’API de connecteur d’applications. Cette connexion vous permet de bénéficier de plus de visibilité et de contrôle lors de l’utilisation d’Azure. Pour plus d’informations sur la façon dont Cloud App Security protège Azure, consultez [protéger Azure](protect-azure.md).

## <a name="how-to-connect-azure-to-cloud-app-security"></a>Comment connecter Azure à Cloud App Security

> [!NOTE]
>
> - L’utilisateur doit être un administrateur global ou de sécurité dans Azure AD pour connecter Azure à Microsoft Cloud App Security.
> - Cloud App Security affiche les activités de **tous** les abonnements.
> - Actuellement, Cloud App Security surveille uniquement les activités ARM.

1. Dans la page **Applications connectées**, cliquez sur le bouton plus (+) et sélectionnez **Microsoft Azure**.

    ![connecter Azure](media/connect-azure-menu.png)

2. Dans la fenêtre contextuelle Azure, cliquez sur **Connecter Microsoft Azure**.

    ![connecter Azure](media/connect-azure.png)

> [!NOTE]
> Une fois Azure connecté, les données sont tirées (pull). À partir de maintenant, vous pouvez voir les données.

Si vous rencontrez des problèmes lors de la connexion de l’application, consultez [résolution des problèmes liés aux connecteurs d’application](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
