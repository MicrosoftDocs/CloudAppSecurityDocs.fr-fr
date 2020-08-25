---
title: Connecter G Suite à Cloud App Security
description: Cet article vous explique comment connecter votre application G Suite à Cloud App Security à l’aide du connecteur d’API, afin de bénéficier de plus de contrôle et de visibilité lors de l’utilisation.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/27/2019
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 707bdbe5e5be0ad506451257f7364197b77e5079
ms.sourcegitcommit: 29a8e66c665f51d831516924ae4d9d8047b39276
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88781189"
---
# <a name="connect-g-suite-to-microsoft-cloud-app-security"></a>Connecter G Suite à Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

Cet article fournit des instructions pour connecter Microsoft Cloud App Security à votre compte G Suite existant à l’aide des API du connecteur. Cette connexion vous permet de bénéficier de plus de visibilité et de contrôle lors de l’utilisation de G Suite. Pour plus d’informations sur la façon dont Cloud App Security protège G suite, consultez [protéger g suite](protect-gsuite.md).

## <a name="configure-g-suite"></a>Configurer G Suite

1. En tant que Super administrateur G suite, connectez-vous à <a href="https://cloud.google.com/console/project" target="_blank">https://cloud.google.com/console/project</a> .

1. Cliquez sur **Créer un projet** pour démarrer un nouveau projet.

    ![Google créer un projet](media/google1.png)

1. Dans l’écran **nouveau projet** , nommez votre projet comme suit : **Cloud App Security** , puis cliquez sur **créer**.

    ![Fenêtre contextuelle Google New Project](media/google2.png)

1. Une fois le projet créé, dans la barre d’outils, cliquez sur **Google Cloud Platform**. Vérifiez que le projet approprié est sélectionné dans la liste déroulante du haut.

    ![Cliquer sur Google Cloud Platform dans la barre d’outils](media/googleverify-project.png)

1. Sélectionnez Menu, accédez à **API & services**  >  **bibliothèque** et activez les API suivantes (utilisez la ligne de recherche si l’API n’est pas listée) :

    * Admin SDK

    * Audit API

    * API Google Drive

    * G Suite Marketplace SDK  
![API Google](media/google4.png)

    > [!NOTE]
    > Pour chaque API, cliquez sur Activer pour l' **activer** .
    >
    > ![Activer Google APPI](media/google-api.png)
    >
    > Ignorez l’avertissement sur les **informations d’identification** pour l’instant.

1. Sélectionnez Menu, accédez à **API &**  >  **tableau de bord**des services et assurez-vous que les API suivantes sont activées :

    ![API Google activé](media/google5.png)

1. Accédez à l’onglet de l' **écran de consentement OAuth** .

    * Dans **nom**de l’application, tapez **Microsoft Cloud App Security**.

    * Tous les autres champs sont facultatifs.

    * Cliquez sur **Enregistrer**.

    ![Consentement de Google OAuth](media/google-oauth-consent.png)

1. Dans l’écran **informations d’identification** , cliquez sur la flèche en regard de **créer des informations d’identification**, puis sélectionnez **clé de compte de service**.

    ![Informations d’identification Google](media/google7.png)

1. Pour **compte de service**, choisissez **nouveau compte de service**, puis entrez un nom pour le compte, par exemple compte de **service 1**. Sous **Role** (Rôle), choisissez **Project** (Projet), puis **Editor** (Éditeur). Sous **Key type (Type de clé)**, choisissez **P12** et cliquez sur **Create (Créer)**. Un fichier de certificat P12 est enregistré sur votre ordinateur.

    ![Créer une clé de compte de service dans Google](media/google9.png)

1. Dans l’écran **Credentials** (Informations d’identification), cliquez sur **Manage service accounts** (Gérer les comptes de service) à l’extrême droite. Copiez l' **e-mail** affecté à votre compte de service. vous en aurez besoin plus tard.

    ![Compte de service des informations d’identification G Suite](media/google10.png)

1. Cliquez sur les points de suspension à droite du compte de service que vous avez créé et sélectionnez **Edit (Modifier)**.

    ![modification Google](media/google11.png "modification Google")

1. Cliquez sur **afficher la délégation à l’ensemble du domaine**, sélectionnez Activer la **délégation à l’ensemble du domaine G suite**.

    ![ID client Google](media/google12.png "google12")

    1. Copiez l' **ID client** . vous en aurez besoin plus tard.
    ![gérer l’accès client des API](media/google12-2.png "google12-2")

    1. Cliquez sur **Enregistrer**

    1. Accédez à [admin.google.com](https://admin.google.com/), puis choisissez **Sécurité**.

    1. Développez **Paramètres avancés**, puis sous **authentification**, sélectionnez **gérer l’accès client aux API**.

    1. Dans la zone **nom du client** , entrez l' **ID client** que vous avez copié précédemment.  

    1. Dans la zone **une ou plusieurs étendues d’API** , entrez la liste suivante des étendues requises (copiez le texte et collez-le dans la zone) :  
`https://www.googleapis.com/auth/admin.reports.audit.readonly,https://www.googleapis.com/auth/admin.reports.usage.readonly,https://www.googleapis.com/auth/drive,https://www.googleapis.com/auth/drive.appdata,https://www.googleapis.com/auth/drive.apps.readonly,https://www.googleapis.com/auth/drive.file,https://www.googleapis.com/auth/drive.metadata.readonly,https://www.googleapis.com/auth/drive.readonly,https://www.googleapis.com/auth/drive.scripts,https://www.googleapis.com/auth/admin.directory.user.readonly,https://www.googleapis.com/auth/admin.directory.user.security,https://www.googleapis.com/auth/admin.directory.user.alias,https://www.googleapis.com/auth/admin.directory.orgunit,https://www.googleapis.com/auth/admin.directory.notifications,https://www.googleapis.com/auth/admin.directory.group.member,https://www.googleapis.com/auth/admin.directory.group,https://www.googleapis.com/auth/admin.directory.device.mobile.action,https://www.googleapis.com/auth/admin.directory.device.mobile,https://www.googleapis.com/auth/admin.directory.user`

    1. Cliquez sur **Autoriser**.

1. Dans le [Google Cloud Platform](https://console.cloud.google.com/), sélectionnez Menu et accédez au tableau de bord **API et services**  >  **Dashboard**.

1. Dans le tableau de bord, faites défiler jusqu’à la liste des API activées et cliquez sur **API Google Drive**.
    ![Sélectionner Google Drive](media/google14.png)

1. Cliquez sur l’onglet **Drive UI integration** (Intégration de l’interface utilisateur Drive) et fournissez les informations suivantes :

    * **Nom de l’application** : Microsoft Cloud App Security.

    * **Brève description & longue Description** (facultatif) : Microsoft Cloud App Security vous offre une visibilité sur les applications Cloud, ce qui vous permet de contrôler, d’examiner et de régir l’utilisation des applications Cloud. sécuriser les données d’entreprise ; et détectent les activités suspectes pour n’importe quelle application Cloud.

    * Google vous demande de charger au moins une icône d’application. Accédez à [https://go.microsoft.com/fwlink/?linkid=862826](https://go.microsoft.com/fwlink/?linkid=862826) pour télécharger un fichier zip contenant Cloud App Security icônes. Ensuite, sous l’icône de l' **application**, cliquez sur **Sélectionner** en regard de l’image 128 x 128 et faites-la glisser vers l’écran contextuel. Cliquez sur **Sélectionner** en regard de l’image 32x32, puis faites-la glisser vers l’écran contextuel.

    * Faites défiler vers le dessous, puis dans la section **intégration de lecteur** , tapez l’URL suivante sous **ouvrir l’URL :**
    `https://portal.cloudappsecurity.com/#/services/11770?tab=files`

    ![Modifier Google Drive](media/google15.png)

1. Cliquez sur **Envoyer**.

1. Revenez à la liste **Enabled APIs** (API activées). Cliquez sur **G Suite Marketplace SDK**.

1. Sélectionnez l’onglet **Configuration**.

    1. Copiez la valeur **Project number (App ID)** (Numéro de projet (ID d’application)) qui apparaît en haut à des fins d’utilisation ultérieure.

    1. Sous **Nom de l’application**, tapez **Microsoft Cloud App Security**.  
Dans **Application description** (Description de l’application), tapez « Microsoft Cloud App Security donne de la visibilité sur les applications cloud, ce qui vous permet de contrôler, examiner et régir l’utilisation de ces applications cloud, de sécuriser les données d’entreprise et de détecter les activités suspectes liées aux applications cloud. »

    1. Veillez à cliquer sur **Done** (Terminé) dans la fenêtre **New item** (Nouvel élément).

    ![Google-nouvel élément](media/google-new-item.png)

    * Désactivez la case à cocher **activer l’installation individuelle** .

    * Configurez les quatre images obligatoires sous **Application icons (Icônes de l’application)**.

    Les images se trouvent à l’adresse :  [https://go.microsoft.com/fwlink/?linkid=862826](https://go.microsoft.com/fwlink/?linkid=862826)

    * Renseignez les valeurs **Support URLs (URL d’assistance)** suivantes :

    * **URL des conditions d’accès**: https://go.microsoft.com/fwlink/?LinkID=733268

    * **URL**de la politique de confidentialité : https://go.microsoft.com/fwlink/?LinkId=512132

    * Sous **OAuth 2.0 scopes** (Étendues OAuth 2.0), copiez et collez les URL suivantes (copiez-les une à la fois et appuyez sur Entrée après chacune d’elles) :  
`https://www.googleapis.com/auth/admin.reports.audit.readonly`  
`https://www.googleapis.com/auth/admin.reports.usage.readonly`  
`https://www.googleapis.com/auth/drive`  
`https://www.googleapis.com/auth/drive.appdata`  
`https://www.googleapis.com/auth/drive.apps.readonly`  
`https://www.googleapis.com/auth/drive.file`  
`https://www.googleapis.com/auth/drive.metadata.readonly`  
`https://www.googleapis.com/auth/drive.readonly`  
`https://www.googleapis.com/auth/drive.scripts`  
`https://www.googleapis.com/auth/admin.directory.user.readonly`  
`https://www.googleapis.com/auth/admin.directory.user.security`  
`https://www.googleapis.com/auth/admin.directory.user.alias`  
`https://www.googleapis.com/auth/admin.directory.orgunit`  
`https://www.googleapis.com/auth/admin.directory.notifications`  
`https://www.googleapis.com/auth/admin.directory.group.member`  
`https://www.googleapis.com/auth/admin.directory.group`  
`https://www.googleapis.com/auth/admin.directory.device.mobile.action`  
`https://www.googleapis.com/auth/admin.directory.device.mobile`  
`https://www.googleapis.com/auth/admin.directory.user`

    * Sous **Visibilité**, sélectionnez **Mon domaine** (et non pas public).
    * Cliquez sur **Enregistrer les modifications**.
        ![Google Visibility](media/google-visibility.png)
1. Dans la console d’administration Google, accédez à [gérer l’application Access Control](https://admin.google.com/). Recherchez la ligne **administrateur G suite** et vérifiez qu’elle dispose d’un accès **illimité** .

    ![Google Security](media/googlesec.png)

## <a name="configure-cloud-app-security"></a>Configurer Cloud App Security

1. Dans le portail Cloud App Security, cliquez sur **Examiner**, puis sur **Applications connectées**.

1. Pour fournir les détails de connexion G suite, sous **connecteurs d’applications**, effectuez l’une des opérations suivantes :

    **Pour une organisation G suite qui possède déjà une instance GCP connectée**

    * Dans la liste des connecteurs, à la fin de la ligne où l’instance GCP s’affiche, cliquez sur les trois points, puis sur **Ajouter G suite**.

    **Pour une organisation G suite qui n’a pas encore d’instance GCP connectée**

    * Dans la page **Applications connectées**, cliquez sur le signe plus (+) et sélectionnez **G Suite**.

1. Dans la fenêtre contextuelle, renseignez les informations suivantes :

    ![Configuration G suite dans Cloud App Security](media/gsuite-config-cas.png "Configuration G suite dans Cloud App Security")

    1. Entrez l' **ID de compte de service**, l' **adresse de messagerie** que vous avez copiée précédemment.

    1. Entrez le **numéro de projet (ID d’application)** que vous avez copié précédemment.

    1. Téléchargez le fichier de **certificat** P12 que vous avez enregistré précédemment.

    1. Entrez un **e-mail du compte d’administrateur** de votre administrateur G Suite.

    1. Si vous avez un compte G Suite Business ou Enterprise, cochez cette case. Pour plus d’informations sur les fonctionnalités disponibles dans Cloud App Security pour G Suite Business ou Enterprise, consultez [Activer la visibilité, la protection et des actions de gouvernance instantanées pour vos applications](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

    1. Cliquez sur **Enregistrer les paramètres**.

    1. **Suivez le lien** pour vous connecter à G Suite. G Suite s’ouvre et vous devez autoriser l’accès pour Cloud App Security.

    1. Vérifiez la connexion en cliquant sur **Tester maintenant**.  
    Le test peut prendre quelques minutes.  
    Après avoir reçu une notification de réussite, cliquez sur **Terminé** et fermez la page G Suite.

Après avoir connecté G Suite, vous recevez les événements des 60 jours précédant la connexion.

Après la connexion de G Suite, Cloud App Security effectue une analyse complète. Selon le nombre de fichiers et d’utilisateurs, l’exécution de l’analyse complète peut prendre du temps. Pour activer l’analyse en quasi temps réel, les fichiers sur lesquels une activité est détectée sont déplacés au début de la file d’attente d’analyse. Par exemple, un fichier qui est modifié, mis à jour ou partagé est analysé immédiatement. Ceci ne s’applique pas aux fichiers qui ne sont pas modifiés de façon intrinsèque. Par exemple, les fichiers qui sont affichés, prévisualisés, imprimés ou exportés sont analysés dans le cadre de l’analyse régulière.

Si vous rencontrez des problèmes lors de la connexion de l’application, consultez [résolution des problèmes liés aux connecteurs d’application](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
