---
title: Connecter Dropbox à Cloud App Security
description: Cet article vous explique comment connecter votre application Dropbox à Cloud App Security à l’aide du connecteur d’API, afin de bénéficier de plus de contrôle et de visibilité lors de l’utilisation.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: a2cc37a22d339b721111948b277135382a2c7c8a
ms.sourcegitcommit: 29a8e66c665f51d831516924ae4d9d8047b39276
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88781087"
---
# <a name="connect-dropbox-to-microsoft-cloud-app-security"></a>Connecter Dropbox à Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

Cet article fournit des instructions pour connecter Microsoft Cloud App Security à un compte Dropbox existant à l’aide des API de connecteur. Cette connexion vous permet de bénéficier de plus de visibilité et de contrôle lors de l’utilisation de Dropbox. Pour plus d’informations sur la façon dont Cloud App Security protège Dropbox, consultez [protéger Dropbox](protect-dropbox.md).

Étant donné que Dropbox permet d’accéder aux fichiers à partir de liens partagés sans connexion, Cloud App Security inscrit ces utilisateurs en tant qu’utilisateurs non authentifiés. Si vous voyez des utilisateurs Dropbox non authentifiés, il peut s’agir d’utilisateurs qui n’appartiennent pas à votre organisation ou d’utilisateurs reconnus de votre organisation qui ne se sont pas connectés.

## <a name="how-to-connect-dropbox-to-cloud-app-security"></a>Comment connecter Dropbox à Cloud App Security

1. Dans la console Cloud App Security, cliquez sur **Examiner**, puis sur **Applications connectées**.

2. Dans la page **connecteurs d’application** , cliquez sur le bouton plus (+), puis sur **Dropbox**.

    ![connecter Dropbox](media/connect-dropbox.png "connecter dropbox")

3. Dans la fenêtre contextuelle, entrez l’adresse e-mail du compte d’administrateur.

4. Cliquez sur **Générer un lien**.

5. Cliquez sur **suivez ce lien**.

    La page de connexion à Dropbox s’ouvre. Entrez vos informations d’identification pour autoriser Cloud App Security à accéder à l’instance Dropbox votre équipe.

6. Dropbox vous demande si vous voulez autoriser Cloud App Security à accéder aux informations de votre équipe, au journal d’activité et à effectuer des activités en tant que membre de l’équipe. Pour continuer, cliquez sur **Autoriser**.

7. De retour dans la console Cloud App Security, vous devez recevoir un message indiquant que Dropbox a été correctement connecté.

8. Vérifiez que la connexion a réussi en cliquant sur **Tester l’API**.

    Le test peut prendre quelques minutes. Une fois que vous êtes averti que la connexion a réussi, cliquez sur **Fermer**.

Après avoir connecté Dropbox, vous recevez les événements des 60 jours précédant la connexion.

> [!NOTE]
> Tout événement Dropbox pour l’ajout d’un fichier est affiché dans Cloud App Security en tant que fichier de chargement pour l’aligner sur toutes les autres applications connectées à Cloud App Security.

Si vous rencontrez des problèmes lors de la connexion de l’application, consultez [résolution des problèmes liés aux connecteurs d’application](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
