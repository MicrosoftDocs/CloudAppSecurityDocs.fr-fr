---
title: "Connecter Google Apps à Microsoft Cloud App Security | Documentation Microsoft"
description: "Cette rubrique fournit des informations sur la connexion de votre application Google Apps à Cloud App Security à l’aide du connecteur API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: b938e1e0-356d-4cc6-ba4a-862c0c59d709
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: 0f38f61be8a0db4a28d3c7df614807ace69bb38e


---

# <a name="connect-google-apps-to-microsoft-cloud-app-security"></a>Connecter Google Apps à Microsoft Cloud App Security
Cette section fournit des instructions pour connecter Cloud App Security à votre compte Google Apps existant à l’aide des API du connecteur.  
  
## <a name="configure-google-apps"></a>Configurer Google Apps  
  
1.  En tant que super administrateur Google Apps, connectez-vous à [https://cloud.google.com/console/project](https://cloud.google.com/console/project).  
  
2.  Cliquez sur **Create an empty project (Créer un projet vide)** pour démarrer un nouveau projet.  
  
     ![google1](./media/google1.png "google1")  
  
3.  Dans l’écran **New project (Nouveau projet)** :  
  
    1.  Nommez votre projet **Cloud App Security pour Google**.  
  
    2.  Indiquez si vous voulez vous abonner aux mises à jour.  
  
    3.  Consultez et acceptez les termes du contrat de service.  
  
    4.  Cliquez sur **Create (Créer)**.  
  
         ![google2](./media/google2.png "google2")  
  
4.  Une fois le projet créé, cliquez sur **Enable and manage APIs (Activer et gérer les API)**.  
  
     ![google3](./media/google3.png "google3")  
  
5.  Cliquez sur l’onglet **Enabled API (API activées)** et désactivez toutes les API répertoriées.  
  
     ![google5](./media/google5.png "google5")  
  
6.  Cliquez sur l’onglet **Google APIs** (API Google) et activez les API suivantes (utilisez la ligne de recherche si l’API n’est pas répertoriée dans la liste **Popular APIs** (API populaires)) :  
  
     ![google8](./media/google8.png "google8")  
  
    > [!NOTE]  
    >  Ignorez l’avertissement sur les **informations d’identification** pour l’instant.  
  
    -   Admin SDK  
  
    -   Audit API  
  
    -   Drive API  
  
    -   Google Apps Marketplace SDK  
  
    -   Gmail API  
  
         ![google11, avertissement](./media/google11-warning.png "google11 warning")  
  
7.  Vous devez avoir 5 **API activées** :  
  
     ![google15](./media/google15.png "google15")  
  
8.  Cliquez sur **Credentials (Informations d’identification)** puis sur **OAuth consent (Consentement OAuth)**.  
  
    -   Dans **Product name shown to users (Nom de produit présenté aux utilisateurs)**, tapez **Cloud App Security pour Google**.  
  
    -   Tous les autres champs sont facultatifs.  
  
    -   Cliquez sur **Save**.  
  
     ![google16](./media/google16.png "google16")  
  
9. Sous l’onglet **Credentials (Informations d’identification)**, cliquez sur la flèche en regard de **Create credentials (Créer des informations d’identification)** et sélectionnez **Service account key (Clé de compte de service)**.  
  
     ![google17](./media/google17.png "google17")  
  
10. Dans **Service account (Compte de service)**, choisissez **New service account (Nouveau compte de service)** et tapez un nom, par exemple, **Compte de service 1**.  
  
     ![google19](./media/google19.png "google19")  
  
     Sous **Key type (Type de clé)**, choisissez **P12** et cliquez sur **Create (Créer)**.  
  
     Un fichier de certificat P12 est téléchargé. Enregistrez le certificat à des fins d’utilisation ultérieure.  
  
     ![google20](./media/google20.png "google20")  
  
11. Sous l’onglet **Credentials (Informations d’identification)**, cliquez sur **Manage service accounts (Gérer les comptes de service)** à l’extrême droite.  
  
     ![informations d’identification google apps, compte de service](./media/google-apps-credentials-service-account.png "google apps credentials service account")  
  
12. Cliquez sur les 3 points à droite du compte de service que vous avez créé et sélectionnez **Edit (Modifier)**.  
  
     ![google22](./media/google22.png "google22")  
  
13. Cochez la case **Enable Google Apps Domain-wide Delegation** (Activer la délégation à l’échelle du domaine Google Apps) et cliquez sur **Enregistrer**.  
  
     ![google24](./media/google24.png "google24")  
  
14. Copiez l’**adresse e-mail** attribuée à votre service : vous en aurez besoin ultérieurement.  
  
     ![google25](./media/google25.png "google25")  
  
15. Ouvrez le menu Google en cliquant sur les trois lignes horizontales en regard de Google Cloud Platform, puis sélectionnez **API manager (Gestionnaire d’API)**.  
  
     ![google, menu](./media/google-menu.png "google menu")  
  
     Sélectionnez **Enabled APIs (API activées)**.  
  
     ![google27](./media/google27.png "google27")  
  
16. Cliquez sur l’icône Paramètres (symbolisée par une roue dentée) en regard de **Drive API** et sous **Drive UI Integration (Intégration de l’interface utilisateur de Drive)**, renseignez les valeurs suivantes :  
  
    -   **Application Name (Nom de l’application)** : Cloud App Security pour Google.  
  
    -   **Short Description & Long Description (Description courte et description longue)** : Microsoft Cloud App Security donne de la visibilité sur les applications cloud, ce qui vous permet de contrôler, examiner et régir l’utilisation de ces applications cloud, de sécuriser les données d’entreprise et de détecter les activités suspectes liées aux applications cloud.  
  
    -   Sous **Application icon (Icône de l’application)**, chargez les images 128 x 128 et 32 x 32.  
  
         Ces images se trouvent à l’adresse : [https://portal.cloudappsecurity.com/cas/static/files/MSLogos.zip](https://portal.cloudappsecurity.com/cas/static/files/MSLogos.zip)  
  
    -   Tapez la valeur suivante sous **Open URL (URL ouverte) :**  
  
         https://portal.cloudappsecurity.com/#/services/11770?tab=files  
  
    -   Cliquez sur **Save Changes (Enregistrer les modifications)**.  
  
         ![google29](./media/google29.png "google29")  
  
17. Dans la liste **Enabled API (API activées)**, cliquez sur l’icône Paramètres (symbolisée par une roue dentée) en regard de **Google Apps Marketplace SDK** et sélectionnez l’onglet **Configuration**.  
  
    -   Copiez la valeur **Project number (App ID)** (Numéro de projet (ID d’application)) qui apparaît en haut à des fins d’utilisation ultérieure.  
  
    -   **Application Name (Nom de l’application)** : Cloud App Security pour Google.  
  
         Renseignez le champ **Application description (Description de l’application)** par : « Microsoft Cloud App Security donne de la visibilité sur les applications cloud, ce qui vous permet de contrôler, examiner et régir l’utilisation de ces applications cloud, de sécuriser les données d’entreprise et de détecter les activités suspectes liées aux applications cloud. »  
  
    -   Décochez la case **Enable individual install (Activer l’installation individuelle)**.  
  
    -   Configurez les 4 images obligatoires sous **Application icons (Icônes de l’application)**.  
  
         Ces images se trouvent à l’adresse : [https://portal.cloudappsecurity.com/cas/static/files/MSLogos.zip](https://portal.cloudappsecurity.com/cas/static/files/MSLogos.zip)  
  
         ![google31](./media/google31.png "google31")  
  
    -   Renseignez les valeurs **Support URLs (URL d’assistance)** suivantes :  
  
        -   **URL des termes du contrat de service** : http://go.microsoft.com/fwlink/?LinkID=733268  
  
        -   **URL de la politique de confidentialité** : http://go.microsoft.com/fwlink/?LinkId=512132  
  
    -   Sous **OAuth 2.0 scopes** (Étendues OAuth 2.0), tapez les valeurs suivantes (1 par ligne. Appuyez sur Entrée pour confirmer) :  
  
        -   https://www.googleapis.com/auth/admin.reports.audit.readonly  
  
        -   https://www.googleapis.com/auth/admin.reports.usage.readonly  
  
        -   https://www.googleapis.com/auth/drive  
  
        -   https://www.googleapis.com/auth/drive.appdata  
  
        -   https://www.googleapis.com/auth/drive.apps.readonly  
  
        -   https://www.googleapis.com/auth/drive.file  
  
        -   https://www.googleapis.com/auth/drive.metadata.readonly  
  
        -   https://www.googleapis.com/auth/drive.readonly  
  
        -   https://www.googleapis.com/auth/drive.scripts  
  
        -   https://www.googleapis.com/auth/admin.directory.user.readonly  
  
        -   https://www.googleapis.com/auth/admin.directory.user.security  
  
        -   https://www.googleapis.com/auth/admin.directory.user.alias  
  
        -   https://www.googleapis.com/auth/admin.directory.orgunit  
  
        -   https://www.googleapis.com/auth/admin.directory.notifications  
  
        -   https://www.googleapis.com/auth/admin.directory.group.member  
  
        -   https://www.googleapis.com/auth/admin.directory.group  
  
        -   https://www.googleapis.com/auth/admin.directory.device.mobile.action  
  
        -   https://www.googleapis.com/auth/admin.directory.device.mobile  
  
        -   https://www.googleapis.com/auth/admin.directory.user  
  
    -   Cliquez sur **Save Changes (Enregistrer les modifications)**.  
  
18. Sélectionnez **Security (Sécurité)** dans la liste des contrôles. Si cette option n’apparaît pas, sélectionnez More controls (Autres contrôles) dans la barre grise située en bas de la page, puis sélectionnez **Security (Sécurité)**.  
  
     ![google apps, sécurité](./media/google-apps-security.png "google apps security")  
  
19. Choisissez **API reference (Informations de référence sur les API)**.  
  
     ![google, référence sur les api](./media/google-api-ref.png "google api ref")  
  
20. Sélectionnez **Enable API Access (Activer l’accès aux API)** et cliquez sur **Save changes (Enregistrer les modifications)**.  
  
     ![google, accès aux api](./media/google-api-access.png "google api access")  
  
## <a name="configure-cloud-app-security"></a>Configurer Cloud App Security  
  
1.  Dans le portail Cloud App Security, cliquez sur **Examiner**, puis sur **Applications approuvées**.  
  
2.  Dans la ligne Google Apps, cliquez sur **Connecter** dans la colonne **État du connecteur d’applications** ou cliquez sur **Connecter une application** et sélectionnez **Google Apps**.  
  
     ![connecter google apps](./media/connect-google-apps.png "connect google apps")  
  
3.  Dans la page des paramètres de Google Apps, renseignez les valeurs suivantes :  
  
     ![Configuration de Google Apps dans Cloud App Security](./media/google-apps-configuration-in-cloud-app-security.png "Google Apps Configuration in Cloud App Security")  
  
    1.  **Adresse e-mail du compte de service Google** que vous avez copiée à l’étape 14.  
  
    2.  **Numéro de projet Google (ID d’application)** que vous avez copié à l’étape 17.  
  
    3.  Chargez le **certificat Google** P12 que vous avez enregistré à l’étape 10.  
  
    4.  Entrez une seule **adresse e-mail d’administrateur** pour votre administrateur Google Apps.  
  
    5.  Si vous avez un compte Google Apps illimité, cochez cette case. Pour plus d’informations sur les fonctionnalités disponibles dans Cloud App Security pour Google Apps illimité, voir [Activer la visibilité, la protection et des actions de gouvernance instantanées pour vos applications](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).  
  
    6.  Cliquez sur **Enregistrer les paramètres**.  
  
    7.  **Suivez le lien** pour vous connecter à Google Apps. Google Apps s’ouvre et vous devez autoriser l’accès à Cloud App Security.  
  
         ![Demande d’autorisation Google Apps](./media/google-apps-authorization-request.png "Google Apps authorization request")  
  
    8.  Vérifiez la connexion en cliquant sur **Test API** (Tester l’API).  
  
         Le test peut prendre quelques minutes.  
  
         Après avoir reçu une notification de réussite, cliquez sur **Terminé** et fermez la page Google Apps.  
  
  
Après avoir connecté Google Apps, vous recevrez les événements des 60 jours précédant la connexion.
  
Après la connexion de Google Apps, Cloud App Security effectue une analyse complète. Selon le nombre de fichiers et d’utilisateurs, l’exécution de l’analyse complète peut prendre du temps. Pour permettre une analyse en temps quasi réel, les fichiers sur lesquels une activité est détectée sont déplacés vers le début de la file d’attente d’analyse, par exemple un fichier qui est modifié, mis à jour ou partagé est analysé immédiatement et n’attend pas d’être traité par le processus d’analyse standard. Cela ne s’applique pas aux fichiers qui ne sont pas intrinsèquement modifiés, par exemple les fichiers qui sont affichés, prévisualisés, imprimés ou exportés.
  
  
## <a name="see-also"></a>Voir aussi  
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO4-->


