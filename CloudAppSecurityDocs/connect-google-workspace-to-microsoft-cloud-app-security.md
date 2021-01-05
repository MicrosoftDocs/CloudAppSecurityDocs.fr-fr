---
title: Connexion de l’espace de travail Google à Cloud App Security
description: Cet article fournit des informations sur la connexion de votre espace de travail Google à Cloud App Security à l’aide du connecteur API pour la visibilité et le contrôle de l’utilisation.
ms.date: 11/27/2019
ms.topic: how-to
ms.openlocfilehash: 0d9d99d650ab0d68f8bd6dd129f6b01c78fb2cc5
ms.sourcegitcommit: 16a65ab2c8ca778d0b3cfa97b847af4c812363b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/03/2021
ms.locfileid: "97855572"
---
# <a name="connect-google-workspace-to-microsoft-cloud-app-security"></a>Connexion de l’espace de travail Google à Microsoft Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Cet article fournit des instructions pour connecter Microsoft Cloud App Security à votre compte Google Workspace existant à l’aide des API du connecteur. Cette connexion vous offre une visibilité et un contrôle sur l’utilisation de l’espace de travail Google. Pour plus d’informations sur la façon dont Cloud App Security protège l’espace de travail Google, consultez [protéger l’espace de travail Google](protect-google-workspace.md).

## <a name="configure-google-workspace"></a>Configurer l’espace de travail Google

1. En tant que Super administrateur Google Workspace, connectez-vous à <a href="https://cloud.google.com/console/project" target="_blank">https://cloud.google.com/console/project</a> .

1. Cliquez sur **Créer un projet** pour démarrer un nouveau projet.

    ![Google créer un projet](media/connect-google-workspace/google-workspace-create-new-project.png)

1. Dans la page **nouveau projet** , nommez votre projet comme suit : **Cloud App Security** , puis cliquez sur **créer**.

    ![Fenêtre contextuelle Google New Project](media/connect-google-workspace/google-workspace-create-new-project-popup.png)

1. Une fois le projet créé, dans la barre d’outils, cliquez sur **Google Cloud Platform**. Vérifiez que le projet approprié est sélectionné dans la liste déroulante du haut.

    ![Cliquer sur Google Cloud Platform dans la barre d’outils](media/connect-google-workspace/google-workspace-verify-project.png)

1. Sélectionnez Menu, accédez à **API & services**  >  **bibliothèque** et activez les API suivantes (utilisez la ligne de recherche si l’API n’est pas listée) :

    - API du kit de développement logiciel (SDK)

    - Audit API
    - API Google Drive
    - SDK Google Workspace Marketplace

    > [!NOTE]
    > Pour chaque API, cliquez sur Activer pour l' **activer** .
    >
    > ![Activer Google APPI](media/connect-google-workspace/google-workspace-api.png)
    >
    > Ignorez l’avertissement sur les **informations d’identification** pour l’instant.

1. Sélectionnez Menu, accédez à **API &**  >  **tableau de bord** des services et assurez-vous que les API suivantes sont activées :

    - API du kit de développement logiciel (SDK)

    - Audit API
    - API Google Drive
    - SDK Google Workspace Marketplace

1. Dans la page de la **page de consentement OAuth** , procédez comme suit :
    1. Sous **type d’utilisateur**, choisissez **externe**, puis cliquez sur **créer**.

        ![Type d’utilisateur de consentement OAuth Google](media/connect-google-workspace/google-workspace-oauth-consent-user-type.png)

    1. Renseignez les informations suivantes, puis cliquez sur **Enregistrer**.

        | Nom du champ | Valeur |
        | --- | --- |
        | Type d'application | Public |
        | Nom de l'application | Microsoft Cloud App Security |
        | E-mail de support | `<your_email_address>` |

        Tous les autres champs sont facultatifs.

        ![Type d’application de consentement OAuth Google](media/connect-google-workspace/google-workspace-oauth-consent-app-type.png)

1. Dans la page **informations d’identification** , procédez comme suit :
    1. Sélectionnez **créer des informations d’identification** , puis sélectionnez **compte de service**.
    1. Sous **Détails du compte de service**, indiquez un nom et une description, puis cliquez sur **créer**.
    1. Sous **accorder à ce compte de service l’accès au projet**, pour le **rôle** sélectionner un **projet**, sélectionnez **éditeur** , puis cliquez sur **terminé**.

    ![Compte de service Google Create](media/connect-google-workspace/google-workspace-create-service-account.png)

1. Dans la page **compte de service** , procédez comme suit :
    1. Sous **comptes de service**, recherchez et modifiez le compte de service que vous avez créé précédemment.

        ![Google modifier le compte de service](media/connect-google-workspace/google-workspace-edit-service-account.png)

    1. Effectuez une copie de l’adresse de messagerie. Vous en aurez besoin plus tard.
    1. Sous **clés**, dans le menu **Ajouter une clé** , sélectionnez créer une **nouvelle clé**, sélectionnez **P12**, puis cliquez sur **créer**. Enregistrez le fichier téléchargé, vous en aurez besoin plus tard.
    1. Sous **État du compte de service**, sélectionnez **activer la délégation à l’ensemble du domaine G suite**, puis cliquez sur **Enregistrer**.

    ![Compte de service de mise à jour Google](media/connect-google-workspace/google-workspace-update-service-account.png)

1. Dans la page **informations d’identification** , sous **id client OAuth 2,0**, copiez l' **ID client** affecté à votre compte de service. vous en aurez besoin ultérieurement.

    ![Compte de service des informations d’identification Google Workspace](media/connect-google-workspace/google-workspace-copy-service-account-client-id.png)

1. Accédez à [admin.google.com](https://admin.google.com/) et accédez à **sécurité**  >  **API contrôles**  >  **gérer la délégation** à l’ensemble du domaine, cliquez sur **Ajouter nouveau**, puis procédez comme suit :

    1. Dans la zone **ID client** , entrez l' **ID client** que vous avez copié précédemment.
    1. Dans la zone **étendues OAuth** , entrez la liste suivante des étendues requises (copiez le texte et collez-le dans la zone) :  
    `https://www.googleapis.com/auth/admin.reports.audit.readonly,https://www.googleapis.com/auth/admin.reports.usage.readonly,https://www.googleapis.com/auth/drive,https://www.googleapis.com/auth/drive.appdata,https://www.googleapis.com/auth/drive.apps.readonly,https://www.googleapis.com/auth/drive.file,https://www.googleapis.com/auth/drive.metadata.readonly,https://www.googleapis.com/auth/drive.readonly,https://www.googleapis.com/auth/drive.scripts,https://www.googleapis.com/auth/admin.directory.user.readonly,https://www.googleapis.com/auth/admin.directory.user.security,https://www.googleapis.com/auth/admin.directory.user.alias,https://www.googleapis.com/auth/admin.directory.orgunit,https://www.googleapis.com/auth/admin.directory.notifications,https://www.googleapis.com/auth/admin.directory.group.member,https://www.googleapis.com/auth/admin.directory.group,https://www.googleapis.com/auth/admin.directory.device.mobile.action,https://www.googleapis.com/auth/admin.directory.device.mobile,https://www.googleapis.com/auth/admin.directory.user`

    1. Cliquez sur **autoriser**.

    ![Ajouter un nouvel ID client à Google Workspace](media/connect-google-workspace/google-workspace-add-new-client-id.png)

## <a name="configure-cloud-app-security"></a>Configurer Cloud App Security

1. Dans le portail Cloud App Security, cliquez sur **Examiner**, puis sur **Applications connectées**.

1. Pour fournir les détails de connexion à Google Workspace, sous **connecteurs d’applications**, effectuez l’une des opérations suivantes :

    **Pour une organisation de l’espace de travail Google qui possède déjà une instance GCP connectée**

    - Dans la liste des connecteurs, à la fin de la ligne où l’instance GCP s’affiche, cliquez sur les trois points, puis cliquez sur **Ajouter un espace de travail Google**.

    **Pour une organisation de l’espace de travail Google qui n’a pas encore d’instance GCP connectée**

    - Dans la page **applications connectées** , cliquez sur le signe plus ( **+** ), puis sélectionnez **espace de travail Google**.

1. Dans la fenêtre contextuelle, renseignez les informations suivantes :

    ![Configuration de l’espace de travail Google dans Cloud App Security](media/connect-google-workspace/cas-config-google-workspace.png "Configuration de l’espace de travail Google dans Cloud App Security")

    1. Entrez l' **ID de compte de service**, l' **adresse de messagerie** que vous avez copiée précédemment.

    1. Entrez le **numéro de projet (ID d’application)** que vous avez copié précédemment.

    1. Téléchargez le fichier de **certificat** P12 que vous avez enregistré précédemment.

    1. Entrez un **e-mail de compte d’administrateur** de votre administrateur Google Workspace.

    1. Si vous disposez d’un compte d’entreprise ou d’entreprise Google Workspace, cochez cette case. Pour plus d’informations sur les fonctionnalités disponibles dans Cloud App Security pour Google Workspace Business ou Enterprise, consultez [activer la visibilité, la protection et les actions de gouvernance instantanées pour vos applications](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

    1. Cliquez sur **Enregistrer les paramètres**.

    1. **Suivez le lien** pour vous connecter à Google Workspace. L’espace de travail Google s’ouvre et vous êtes invité à autoriser l’accès à Cloud App Security.

    1. Vérifiez la connexion en cliquant sur **Tester maintenant**.  
    Le test peut prendre quelques minutes.  
    Après avoir reçu une notification de réussite, cliquez sur **terminé** et fermez la page de l’espace de travail Google.

Une fois que vous êtes connecté à Google Workspace, vous recevrez des événements pendant 60 jours avant la connexion.

Une fois la connexion à Google Workspace effectuée, Cloud App Security effectue une analyse complète. Selon le nombre de fichiers et d’utilisateurs, l’exécution de l’analyse complète peut prendre du temps. Pour activer l’analyse en quasi temps réel, les fichiers sur lesquels une activité est détectée sont déplacés au début de la file d’attente d’analyse. Par exemple, un fichier qui est modifié, mis à jour ou partagé est analysé immédiatement. Ceci ne s’applique pas aux fichiers qui ne sont pas modifiés de façon intrinsèque. Par exemple, les fichiers qui sont affichés, prévisualisés, imprimés ou exportés sont analysés dans le cadre de l’analyse régulière.

Si vous rencontrez des problèmes lors de la connexion de l’application, consultez [résolution des problèmes liés aux connecteurs d’application](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
