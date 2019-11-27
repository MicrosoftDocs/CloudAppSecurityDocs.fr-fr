---
title: Connecter G Suite à Cloud App Security
description: Cet article vous explique comment connecter votre application G Suite à Cloud App Security à l’aide du connecteur d’API, afin de bénéficier de plus de contrôle et de visibilité lors de l’utilisation.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/17/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: b938e1e0-356d-4cc6-ba4a-862c0c59d709
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 2ee23589a2cefbba9189ba34dfe095f352b08383
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74461219"
---
# <a name="connect-g-suite-to-microsoft-cloud-app-security"></a>Connecter G Suite à Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

Cet article fournit des instructions pour connecter Microsoft Cloud App Security à votre compte G Suite existant à l’aide des API du connecteur. Cette connexion vous permet de bénéficier de plus de visibilité et de contrôle lors de l’utilisation de G Suite.

## <a name="configure-g-suite"></a>Configurer G Suite

1. En tant que super administrateur de G Suite, connectez-vous à <a href="https://cloud.google.com/console/project" target="_blank">https://cloud.google.com/console/project</a>.

1. Cliquez sur **Créer un projet** pour démarrer un nouveau projet.

    ![google1](media/google1.png)

1. Dans l’écran **Nouveau projet**, nommez votre projet comme suit :  
**Cloud App Security** puis cliquez sur **créer**.

    ![google2](media/google2.png)

1. Une fois que le projet est créé, dans la barre d’outils, cliquez sur **Google Cloud Platform**. Vérifiez que le projet approprié est sélectionné dans la liste déroulante du haut.

    ![projet Google](media/googleverify-project.png)

1. Sous **API**, cliquez sur **accéder à la vue d’ensemble de l’API**.

    ![google3](media/google3.png)

1. Cliquez sur **Bibliothèque** et activez les API suivantes (utilisez la ligne de recherche si l’API ne figure pas dans la liste **Popular APIs** (API populaires)) :

    * Admin SDK

    * Audit API

    * API Google Drive

    * G Suite Marketplace SDK

    ! [API Google] (Media/google4. png

    > [!NOTE]
    > Ignorez l’avertissement sur les **informations d’identification** pour l’instant.

1. Cliquez sur Activer pour chaque API.
    ![Activer Google APPI](media/google-api.png)
1. Vérifiez que les API suivantes sont activées :

    ![API Google activé](media/google5.png)

1. Cliquez sur **Credentials** (Informations d’identification)et sélectionnez l’onglet de l’**écran de consentement OAuth**.

    * Dans **Nom de produit présenté aux utilisateurs**, tapez **Microsoft Cloud App Security**.

    * Tous les autres champs sont facultatifs.

    * Cliquez sur **Enregistrer**.

    ![Consentement de Google OAuth](media/google-oauth-consent.png)

1. Sous l’onglet **Credentials** (Informations d’identification), cliquez sur la flèche en regard de **Create credentials** (Créer des informations d’identification).

    ![Informations d’identification Google](media/google7.png)

1. Sélectionnez **Service account key** (Clé de compte de service).

    ![Clé de compte de service Google](media/google8.png)

1. Sous **Create service account key (Créer une clé de compte de service)** , choisissez **New service account (Nouveau compte de service)** et tapez un nom, par exemple, **Compte de service 1**. Sous **Role** (Rôle), choisissez **Project** (Projet), puis **Editor** (Éditeur). Sous **Key type (Type de clé)** , choisissez **P12** et cliquez sur **Create (Créer)** . Un fichier de certificat P12 est enregistré sur votre ordinateur.

    ![Créer une clé de compte de service dans Google](media/google9.png)

1. Copiez **l’ID de compte de service** attribué à votre service, car vous en aurez besoin.

1. Dans l’écran **Credentials** (Informations d’identification), cliquez sur **Manage service accounts** (Gérer les comptes de service) à l’extrême droite.

    ![Compte de service des informations d’identification G Suite](media/google10.png "Compte de service des informations d’identification G suite")

1. Cliquez sur les points de suspension à droite du compte de service que vous avez créé et sélectionnez **Edit (Modifier)** .

    ![modification Google](media/google11.png "modification Google")

1. Cliquez sur **afficher l’ID client de délégation**à l’ensemble du domaine.

    ![ID client Google](media/google12.png "google12")

    * Copiez l' **ID client** . vous en aurez besoin plus tard.

    * Accédez à [admin.google.com](https://admin.google.com/), puis choisissez **Sécurité**.

    * Sélectionnez **afficher plus** , puis choisissez **Paramètres avancés**.

    * Dans la section **authentification** , sélectionnez **gérer l’accès client**de l’API.

    * Dans la zone **nom du client** , entrez l' **ID client** que vous avez copié précédemment.

    ![gérer l’accès client des API](media/google12-2.png "google12-2")

    * Dans la zone **une ou plusieurs étendues d’API** , entrez la liste suivante des étendues requises (copiez le texte et collez-le dans la zone) :

            `https://www.googleapis.com/auth/admin.reports.audit.readonly,https://www.googleapis.com/auth/admin.reports.usage.readonly,https://www.googleapis.com/auth/drive,https://www.googleapis.com/auth/drive.appdata,https://www.googleapis.com/auth/drive.apps.readonly,https://www.googleapis.com/auth/drive.file,https://www.googleapis.com/auth/drive.metadata.readonly,https://www.googleapis.com/auth/drive.readonly,https://www.googleapis.com/auth/drive.scripts,https://www.googleapis.com/auth/admin.directory.user.readonly,https://www.googleapis.com/auth/admin.directory.user.security,https://www.googleapis.com/auth/admin.directory.user.alias,https://www.googleapis.com/auth/admin.directory.orgunit,https://www.googleapis.com/auth/admin.directory.notifications,https://www.googleapis.com/auth/admin.directory.group.member,https://www.googleapis.com/auth/admin.directory.group,https://www.googleapis.com/auth/admin.directory.device.mobile.action,https://www.googleapis.com/auth/admin.directory.device.mobile,https://www.googleapis.com/auth/admin.directory.user`

    * Cliquez sur **autoriser**.

1. Ouvrez le menu Google en cliquant sur les trois lignes horizontales en regard de Google Cloud Platform dans la barre de titre. Cliquez sur **Google Cloud Platform**, puis sur l’onglet **APIs and services** (API et services) dans le menu de gauche.

1. Dans le tableau de bord qui s’ouvre, faites défiler la liste des API activées et cliquez sur **Google Drive API**.
    ! [Sélectionner Google Drive] (Media/google14. png

1. Cliquez sur l’onglet **Drive UI integration** (Intégration de l’interface utilisateur Drive) et fournissez les informations suivantes :

    * **Nom de l’application** : Microsoft Cloud App Security.

    * **Short Description & Long Description** (Description courte et description longue) (facultatif) : Microsoft Cloud App Security offre une visibilité sur les applications cloud, ce qui vous permet de contrôler, d’examiner et de régir l’utilisation de ces applications cloud, de sécuriser les données d’entreprise et de détecter les activités suspectes liées aux applications cloud.

    * Google vous demande de charger au moins une icône d’application. Accédez à [ https://go.microsoft.com/fwlink/?linkid=862826 ](https://go.microsoft.com/fwlink/?linkid=862826) pour télécharger un fichier zip contenant les icônes de Cloud App Security. Ensuite, sous **Icône de l’application**, cliquez sur **Sélectionner** en regard de l’image 128 x 128 et faites-la glisser jusqu’à la fenêtre contextuelle. Cliquez sur **Sélectionner** en regard de l’image 32 x 32 et faites-la glisser jusqu’à la fenêtre contextuelle.

    * Faites défiler et dans la section **Drive Integration** (Intégration de Drive), tapez l’URL suivante sous **Open URL:** (Ouvrir l’URL :)  
    `https://portal.cloudappsecurity.com/#/services/11770?tab=files`

    ![Modifier Google Drive](media/google15.png)

1. Cliquez sur **Save Changes (Enregistrer les modifications)** .

1. Revenez à la liste **Enabled APIs** (API activées). Cliquez sur **G Suite Marketplace SDK**.

1. Sélectionnez l’onglet **Configuration**.

    * Copiez la valeur **Project number (App ID)** (Numéro de projet (ID d’application)) qui apparaît en haut à des fins d’utilisation ultérieure.

    * Sous **Nom de l’application**, tapez **Microsoft Cloud App Security**.

         Dans **Application description** (Description de l’application), tapez « Microsoft Cloud App Security donne de la visibilité sur les applications cloud, ce qui vous permet de contrôler, examiner et régir l’utilisation de ces applications cloud, de sécuriser les données d’entreprise et de détecter les activités suspectes liées aux applications cloud. »

    * Veillez à cliquer sur **Done** (Terminé) dans la fenêtre **New item** (Nouvel élément).

    ![Google-nouvel élément](media/google-new-item.png)

    * Désactivez la case à cocher **activer l’installation individuelle** .

    * Configurez les quatre images obligatoires sous **Application icons (Icônes de l’application)** .

    Vous trouverez les images sur :  [https://go.microsoft.com/fwlink/?linkid=862826](https://go.microsoft.com/fwlink/?linkid=862826)

    * Renseignez les valeurs **Support URLs (URL d’assistance)** suivantes :

    * **Terms of service URL** : https://go.microsoft.com/fwlink/?LinkID=733268 (URL des conditions générales du service)

    * **Privacy policy URL** : https://go.microsoft.com/fwlink/?LinkId=512132 (URL de la politique de confidentialité)

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
    * Cliquez sur **Save Changes (Enregistrer les modifications)** .
        ![Google Visibility](media/google-visibility.png)
1. Accédez à [admin.google.com](https://admin.google.com/), puis choisissez **Sécurité**.

    ![Google Security](media/googlesec.png)

1. Choisissez **API reference (Informations de référence sur les API)** .

    ![activation de l’API Google](media/googleapi.png)

1. Sélectionnez **Enable API Access (Activer l’accès aux API)** et cliquez sur **Save changes (Enregistrer les modifications)** .

    ![informations de référence sur l’API Google](media/googleapiref.png)

## <a name="configure-cloud-app-security"></a>Configurer Cloud App Security

1. Dans le portail Cloud App Security, cliquez sur **Examiner**, puis sur **Applications connectées**.

1. Pour fournir les détails de connexion G suite, sous **connecteurs d’applications**, effectuez l’une des opérations suivantes :

    **Pour une organisation G suite qui possède déjà une instance GCP connectée**

    * Dans la liste des connecteurs, à la fin de la ligne où l’instance GCP s’affiche, cliquez sur les trois points, puis sur **Ajouter G suite**.

    **Pour une organisation G suite qui n’a pas encore d’instance GCP connectée**

    * Dans la page **Applications connectées**, cliquez sur le signe plus (+) et sélectionnez **G Suite**.

3. Dans la fenêtre contextuelle, renseignez les informations suivantes :

    ![Configuration G suite dans Cloud App Security](media/gsuite-config-cas.png "Configuration G suite dans Cloud App Security")

    1. **ID de compte de service** que vous avez copié à l’étape 13.

    1. **Numéro de projet (ID d’application)** que vous avez copié à l’étape 22.

    1. Chargez le **certificat** P12 que vous avez enregistré à l’étape 12. Pour ce faire, vous avez besoin du mot de passe que vous avez enregistré.

    1. Entrez un **e-mail du compte d’administrateur** de votre administrateur G Suite.

    1. Si vous avez un compte G Suite Business ou Enterprise, cochez cette case. Pour plus d’informations sur les fonctionnalités disponibles dans Cloud App Security pour G Suite Business ou Enterprise, consultez [Activer la visibilité, la protection et des actions de gouvernance instantanées pour vos applications](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

    1. Cliquez sur **Enregistrer les paramètres**.

    1. **Suivez le lien** pour vous connecter à G Suite. G Suite s’ouvre et vous devez autoriser l’accès pour Cloud App Security.

    1. Vérifiez la connexion en cliquant sur **Tester maintenant**.

            Testing may take a couple of minutes.
    
            After receiving a success notice, click **Done** and close the G Suite page.

Après avoir connecté G Suite, vous recevez les événements des 60 jours précédant la connexion.

Après la connexion de G Suite, Cloud App Security effectue une analyse complète. Selon le nombre de fichiers et d’utilisateurs, l’exécution de l’analyse complète peut prendre du temps. Pour activer l’analyse en quasi temps réel, les fichiers sur lesquels une activité est détectée sont déplacés au début de la file d’attente d’analyse. Par exemple, un fichier qui est modifié, mis à jour ou partagé est analysé immédiatement. Ceci ne s’applique pas aux fichiers qui ne sont pas modifiés de façon intrinsèque. Par exemple, les fichiers qui sont affichés, prévisualisés, imprimés ou exportés sont analysés dans le cadre de l’analyse régulière.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
