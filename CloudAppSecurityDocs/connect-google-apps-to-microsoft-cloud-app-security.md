---
title: "Connecter G Suite à Cloud App Security pour la visibilité et le contrôle d’utilisation | Microsoft Docs"
description: "Cette rubrique fournit des informations sur la connexion de votre application G Suite à Cloud App Security à l’aide du connecteur API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/28/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: b938e1e0-356d-4cc6-ba4a-862c0c59d709
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 29a52d474fdc09052506e88c8b871e611c3a5b27
ms.sourcegitcommit: 661f4ce41262e8462c90fd2a4f1232e2154d5113
translationtype: HT
---
# <a name="connect-g-suite-to-microsoft-cloud-app-security"></a>Connecter G Suite à Microsoft Cloud App Security
Cette section fournit des instructions pour connecter Cloud App Security à votre compte G Suite existant à l’aide des API du connecteur.

  
  
## <a name="configure-g-suite"></a>Configurer G Suite  
  
1.  En tant que super administrateur G Suite, connectez-vous à [https://cloud.google.com/console/project](https://cloud.google.com/console/project).  
  
2.  Cliquez sur **Créer un projet** pour démarrer un nouveau projet.  
  
     ![google1](./media/google1.png "google1")  
  
3.  Dans l’écran **Nouveau projet**, nommez votre projet comme suit :</br>
    **Cloud App Security pour Google** et cliquez sur **Créer**.  
           ![google2](./media/google2.png "google2")  
  
4.  Une fois que le projet est créé, dans la barre d’outils, en regard de Google Cloud Platform, sélectionnez le projet puis, sous **API**, cliquez sur **Go to APIs overview** (Accéder à la vue d’ensemble des API).  
  
     ![google3](./media/google3.png "google3")  
  
5.  Sous **API**, désactivez toutes les API répertoriées.  
      
6.  Cliquez sur **Bibliothèque** et activez les API suivantes (utilisez la ligne de recherche si l’API n’est pas répertoriée dans la liste **Popular APIs** (API populaires)) :  
  
     ![api google](./media/google4.png "google4")  
  
    > [!NOTE]  
    >  Ignorez l’avertissement sur les **informations d’identification** pour l’instant.  
  
    -   Admin SDK  
  
    -   Audit API  
  
    -   API Google Drive  
  
    -   Google Apps Marketplace SDK  
  
    -   Gmail API  
            
7.  Vous devez avoir 5 **API activées** :  
  
     ![google, api activées](./media/google5.png "google5")  
  
8.  Cliquez sur **Credentials** (Informations d’identification), puis sur **OAuth consent screen** (Écran de consentement OAuth)  
  
    -   Dans **Product name shown to users (Nom de produit présenté aux utilisateurs)**, tapez **Cloud App Security pour Google**.  
  
    -   Tous les autres champs sont facultatifs.  
  
    -   Cliquez sur **Enregistrer**.  
  
     ![google, nom de produit](./media/google6.png "google6")  
  
9. Dans l’écran **API Credentials** (Informations d’identification de l’API), cliquez sur la flèche en regard de **Create credentials** (Créer des informations d’identification).  
  
     ![google, informations d’identification](./media/google7.png "google7")  

10. Sélectionnez **Service account key** (Clé de compte de service).

     ![google, clé de compte de service](./media/google8.png "google8")  
  
11. Sous **Create service account key** (Créer une clé de compte de service), choisissez **New service account** (Nouveau compte de service) et tapez un nom, par exemple **Compte de service 1**, sous **Rôle** choisissez **Projet** et **Éditeur**, puis sous **Key type** (Type de clé), choisissez **P12** et cliquez sur **Créer**.  
  
     ![google, créer une clé de compte de service](./media/google9.png "google9")  
  
12.  Un fichier de certificat P12 est enregistré sur votre ordinateur. Une fenêtre contextuelle vous indique le **mot de passe pour la clé privée**. VEILLEZ À L’ENREGISTRER pour l’utiliser plus tard.  
        
12. Dans l’écran **Credentials** (Informations d’identification), cliquez sur **Manage service accounts** (Gérer les comptes de service) à l’extrême droite.  
       ![Compte de service des informations d’identification G Suite](./media/google10.png "G Suite credentials service account")  
  
13. Cliquez sur les 3 points à droite du compte de service que vous avez créé et sélectionnez **Edit (Modifier)**.  
  
     ![google, modifier](./media/google11.png "google, modifier")  
  
14. Cochez la case **Enable G Suite Domain-wide Delegation** (Activer la délégation à l’échelle du domaine G Suite) et cliquez sur **Enregistrer**.  
  
     ![google, à l’échelle du domaine](./media/google12.png "google, à l’échelle du domaine")  
  
15. Copiez l’**ID de compte de service** attribué à votre service, car vous en aurez besoin.  
  
     ![google, ID de compte de service](./media/google13.png "google13")  
  
16. Ouvrez le menu Google en cliquant sur les trois lignes horizontales en regard de Google Cloud Platform dans la barre de titre, puis sélectionnez **API manager** (Gestionnaire d’API) et **Dashboard** (Tableau de bord).  
    
17. Accédez à la liste des API activées et cliquez sur l’icône des paramètres en regard d’**API Google Drive**.   
       ![Google Drive, sélectionner](./media/google14.png "google14")  

18. Renseignez les éléments suivants :

    -   **Application Name (Nom de l’application)** : Cloud App Security pour Google.  
  
    -   **Short Description & Long Description** (Description courte et description longue) (facultatif) : Microsoft Cloud App Security offre une visibilité sur les applications cloud, ce qui vous permet de contrôler, d’examiner et de régir l’utilisation de ces applications cloud, de sécuriser les données d’entreprise et de détecter les activités suspectes liées aux applications cloud.  
  
    -   Google vous demande de charger au moins une icône d’application. Accédez à [https://portal.cloudappsecurity.com/cas/static/files/MSLogos.zip](https://portal.cloudappsecurity.com/cas/static/files/MSLogos.zip) pour télécharger un fichier zip contenant les icônes Cloud App Security. Ensuite, sous **Application icon** (Icône de l’application), effectuez un glisser-déplacer des images 128 x 128 et 32 x 32.  
  
    -   Sous **Drive Integration** (Intégration du lecteur), tapez le code suivant sous **Open URL:** (Ouvrir l’URL :)  
  
         https://portal.cloudappsecurity.com/#/services/11770?tab=files  
  
    -   Cliquez sur **Save Changes (Enregistrer les modifications)**.  
  
         ![google, configuration du lecteur](./media/google15.png "googledriveconfig")  
  
19. Dans la liste **Enabled APIs** (API activées), cliquez sur l’icône des paramètres en regard de **Google Apps Marketplace SDK**. 
         ![google, configurer marketplace SDK](./media/google16.png "googledriveconfig")  
20. Sélectionnez l’onglet **Configuration**.  
  
    -   Copiez la valeur **Project number (App ID)** (Numéro de projet (ID d’application)) qui apparaît en haut à des fins d’utilisation ultérieure.  
  
    -   **Application Name** (Nom de l’application) doit indiquer **Cloud App Security pour Google**.
  
         Renseignez le champ **Application description (Description de l’application)** par : « Microsoft Cloud App Security donne de la visibilité sur les applications cloud, ce qui vous permet de contrôler, examiner et régir l’utilisation de ces applications cloud, de sécuriser les données d’entreprise et de détecter les activités suspectes liées aux applications cloud. »  
  
    -   Décochez la case **Enable individual install** (Activer l’installation individuelle).  
  
    -   Configurez les 4 images obligatoires sous **Application icons (Icônes de l’application)**.  
  
         Ces images se trouvent à l’adresse : [https://portal.cloudappsecurity.com/cas/static/files/MSLogos.zip](https://portal.cloudappsecurity.com/cas/static/files/MSLogos.zip)  
  
         ![google, configurer marketplace sdk](./media/google17.png "google17")  
  
    -   Renseignez les valeurs **Support URLs (URL d’assistance)** suivantes :  
  
        -   **URL des termes du contrat de service** : http://go.microsoft.com/fwlink/?LinkID=733268  
  
        -   **URL de la politique de confidentialité** : http://go.microsoft.com/fwlink/?LinkId=512132  
  
    -   Sous **OAuth 2.0 scopes** (Étendues OAuth 2.0), copiez et collez les éléments suivants. Vous devez les copier un par un et appuyer sur Entrer à chaque fois :  
  
           https://www.googleapis.com/auth/admin.reports.audit.readonly  
  
           https://www.googleapis.com/auth/admin.reports.usage.readonly  
  
           https://www.googleapis.com/auth/drive  
  
           https://www.googleapis.com/auth/drive.appdata  
  
           https://www.googleapis.com/auth/drive.apps.readonly  
  
           https://www.googleapis.com/auth/drive.file  
  
           https://www.googleapis.com/auth/drive.metadata.readonly  
  
           https://www.googleapis.com/auth/drive.readonly  
  
           https://www.googleapis.com/auth/drive.scripts  
  
           https://www.googleapis.com/auth/admin.directory.user.readonly  
  
           https://www.googleapis.com/auth/admin.directory.user.security  
  
           https://www.googleapis.com/auth/admin.directory.user.alias  
  
           https://www.googleapis.com/auth/admin.directory.orgunit  
  
           https://www.googleapis.com/auth/admin.directory.notifications  
  
           https://www.googleapis.com/auth/admin.directory.group.member  
  
           https://www.googleapis.com/auth/admin.directory.group  
  
           https://www.googleapis.com/auth/admin.directory.device.mobile.action  
  
           https://www.googleapis.com/auth/admin.directory.device.mobile  
  
           https://www.googleapis.com/auth/admin.directory.user  
  
    -   Cliquez sur **Save Changes (Enregistrer les modifications)**.  
  
18. Accédez à [admin.google.com](https://admin.google.com/), puis choisissez **Sécurité**. 
       ![google, sécurité](./media/googlesecurity.png "google8")  
 
19. Choisissez **API reference (Informations de référence sur les API)**.  
       ![google, activer l’api](./media/googleapi.png "google8")  
      
20. Sélectionnez **Enable API Access (Activer l’accès aux API)** et cliquez sur **Save changes (Enregistrer les modifications)**.  
  
    ![google, référence à l’api](./media/googleapiref.png "google8")  

  
## <a name="configure-cloud-app-security"></a>Configurer Cloud App Security  
  
1.  Dans le portail Cloud App Security, cliquez sur **Examiner**, puis sur **Applications connectées**.  
  
2.  Dans la page **Applications connectées**, cliquez sur le signe plus (+) et sélectionnez **G Suite**.  
       
  
3.  Dans la fenêtre contextuelle, renseignez les éléments suivants :  
  
     ![Configuration de G Suite dans Cloud App Security](./media/gsuite-config-cas.png "Configuration de G Suite dans Cloud App Security")  
  
    1.  **Adresse e-mail du compte de service** que vous avez copiée à l’étape 16.  
  
    2.  **Numéro de projet (ID d’application)** que vous avez copié à l’étape 21.  
  
    3.  Chargez le **certificat** P12 que vous avez enregistré à l’étape 12. Pour ce faire, vous aurez besoin du mot de passe que vous avez enregistré.  
  
    4.  Entrez un **e-mail du compte d’administrateur** de votre administrateur G Suite.  
  
    5.  Si vous avez un compte G Suite Unlimited, cochez cette case. Pour plus d’informations sur les fonctionnalités disponibles dans Cloud App Security pour G Suite Unlimited, consultez [Activer la visibilité, la protection et des actions de gouvernance instantanées pour vos applications](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).  
  
    6.  Cliquez sur **Enregistrer les paramètres**.  
  
    7.  **Suivez le lien** pour vous connecter à G Suite. G Suite s’ouvre et vous devez autoriser l’accès à Cloud App Security.  
         
    8.  Vérifiez la connexion en cliquant sur **Tester maintenant**.  
  
         Le test peut prendre quelques minutes.  
  
         Après avoir reçu une notification de réussite, cliquez sur **Terminé** et fermez la page G Suite.  
  
  
Après avoir connecté G Suite, vous recevrez les événements des 60 jours précédant la connexion.
  
Après la connexion de G Suite, Cloud App Security effectue une analyse complète. Selon le nombre de fichiers et d’utilisateurs, l’exécution de l’analyse complète peut prendre du temps. Pour permettre une analyse en temps quasi réel, les fichiers sur lesquels une activité est détectée sont déplacés vers le début de la file d’attente d’analyse, par exemple un fichier qui est modifié, mis à jour ou partagé est analysé immédiatement et n’attend pas d’être traité par le processus d’analyse standard. Cela ne s’applique pas aux fichiers qui ne sont pas intrinsèquement modifiés, par exemple les fichiers qui sont affichés, prévisualisés, imprimés ou exportés.
  
  
## <a name="see-also"></a>Voir aussi  
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  