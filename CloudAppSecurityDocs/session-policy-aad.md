---
title: "Créer des stratégies de session pour obtenir une meilleure visibilité des activités de session utilisateur et bloquer les téléchargements | Microsoft Docs"
description: "Cette rubrique décrit la procédure de configuration d’une stratégie de session du proxy Cloud App Security pour améliorer la visibilité des activités de session utilisateur et bloquer les téléchargements."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 745df28a-654c-4abf-9c90-203841169f90
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 97ebb7db49fcf5ed524a05943557d616487294f8
ms.sourcegitcommit: 3bc510959e66a29d474cbef412deac0daefa8a24
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="session-policies"></a>Stratégies de session 

> [!NOTE]
> Le lancement de la fonctionnalité de proxy Microsoft Cloud App Security est en cours.

Les stratégies de session Cloud App Security permettent la surveillance en temps réel au niveau de la session, vous offrant une visibilité plus précise dans les applications cloud et la possibilité de prendre des mesures différentes selon la stratégie que vous définissez pour une session utilisateur. Au lieu d’autoriser ou de bloquer complètement l’accès, vous pouvez utiliser le contrôle de session, lequel vous permet d’autoriser l’accès pendant la surveillance de la session et/ou de limiter des activités de session particulières. 

Par exemple, vous pouvez décider que pour les appareils non gérés ou pour les sessions provenant d’emplacements spécifiques, vous voulez autoriser l’utilisateur à accéder à l’application, mais aussi limiter le téléchargement des fichiers sensibles ou exiger que certains documents soient protégés lors de leur téléchargement. Les stratégies de session vous permettent de définir ces contrôles de session utilisateur. 

## <a name="prerequisites-to-using-session-policies"></a>Prérequis à l’utilisation de stratégies de session

- Licence Azure AD Premium P2.
- Les applications appropriées doivent être [déployées avec un proxy](proxy-deployment-aad.md).
- Une [stratégie d’accès conditionnel Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) doit être en place pour rediriger les utilisateurs vers le proxy Cloud App Security, comme décrit ci-dessous.


## <a name="create-an-azure-ad-conditional-access-policy"></a>Créer une stratégie d’accès conditionnel Azure AD

Les stratégies d’accès conditionnel Azure Active Directory et les stratégies de session Cloud App Security travaillent conjointement pour examiner chaque session utilisateur et prendre des décisions stratégiques pour chaque application. Pour configurer une stratégie d’accès conditionnel dans Azure AD, procédez comme suit :

1. Configurez une [stratégie d’accès conditionnel Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) avec des affectations pour l’utilisateur ou le groupe d’utilisateurs et l’application SAML à contrôler avec le proxy Cloud App Security. 

  > [!NOTE]
  > Seules les applications [déployées avec le proxy](proxy-deployment-aad.md) sont concernées par cette stratégie.

2. Acheminez les utilisateurs vers le proxy Cloud App Security en sélectionnant **Utiliser les restrictions appliquées par le proxy** dans le panneau **Session**.

 ![Restrictions du proxy pour l’accès conditionnel Azure AD](./media/proxy-deploy-restrictions-aad.png)

## <a name="create-a-cloud-app-security-session-policy"></a>Créer une stratégie de session Cloud App Security 

Pour créer une stratégie de session, suivez cette procédure :

1. Dans le portail, sélectionnez **Contrôle**, puis **Stratégies**.
3. Dans la page **Stratégies**, cliquez sur **Créer une stratégie** et sélectionnez **Stratégie de session**.  

 ![Créer une stratégie de session](./media/create-session-policy.png)

4. Dans la fenêtre **Stratégie de session**, donnez un nom à votre stratégie, comme *Bloquer le téléchargement des documents sensibles dans Box pour les utilisateurs du service marketing*.

 ![Nouvelle stratégie de session](./media/new-session-policy.png)

5. Dans le champ **Type de contrôle de session** : 

    1. Sélectionnez **Surveiller toutes les activités** pour surveiller uniquement les activités des utilisateurs.

    2. Sélectionnez **Surveiller toutes les activités et contrôler le téléchargement de fichiers** pour surveiller les activités des utilisateurs et prendre des mesures supplémentaires, comme le blocage ou la protection des téléchargements pour les utilisateurs.

    ![type de contrôle de stratégie de session](./media/session-policy-control-type.png)

6. Sous **Source de l’activité** dans la section **Activités remplissant toutes les conditions suivantes**, sélectionnez d’autres filtres d’activité à appliquer à la stratégie. Ceux-ci peuvent inclure les options suivantes : 

     - **Balise de l’appareil** : Utilisez ce filtre pour identifier les appareils non gérés.

     - **Emplacement** : Utilisez ce filtre pour identifier les emplacements inconnus (et par conséquent à risque). 

     - **Adresse IP** : Utilisez ce filtre pour filtrer selon des adresses IP ou utiliser des balises d’adresse IP déjà attribuées. 

     - **Étiquette agent utilisateur** : Utilisez ce filtre pour activer l’heuristique afin d’identifier les applications mobiles et de bureau. Vous devez définir ce filtre comme étant égal à ou différent du **client natif** et le tester sur vos applications mobiles et de bureau pour chaque application cloud.
         
         ![prise en charge du client natif](./media/user-agent-tag.png)

       >[!NOTE]
       >Les stratégies de session ne prennent pas en charge les applications mobiles et de bureau. Veillez à tester les stratégies de session pour vérifier qu’elles n’interfèrent pas avec les fonctionnalités des applications mobiles et de bureau. Si nécessaire, excluez les applications mobiles et de bureau des stratégies de session.

     ![source de l’activité de la stratégie de session](./media/session-policy-activity-filters.png)

7. Si vous avez sélectionné l’option **Surveiller toutes les activités et contrôler le téléchargement de fichiers** :

    1. Sous **Source de l’activité** dans la section **Fichiers remplissant toutes les conditions suivantes**, sélectionnez d’autres filtres de fichiers à appliquer à la stratégie. Ceux-ci peuvent inclure les options suivantes :

        - **Étiquette de classification** : Utilisez ce filtre si votre organisation utilise Azure Information Protection et que vos données ont été protégées par ses étiquettes de classification. Vous pouvez alors filtrer des fichiers en fonction de l’étiquette de classification que vous leur avez appliquée. Pour plus d’informations sur l’intégration entre Cloud App Security et Azure Information Protection, consultez [Intégration d’Azure Information Protection](azip-integration.md).

        - **Nom de fichier** : Utilisez ce filtre pour appliquer la stratégie à des fichiers spécifiques.

        - **Type de fichier** : Utilisez ce filtre pour appliquer la stratégie à des types de fichiers spécifiques, par exemple, pour bloquer le téléchargement de tous les fichiers .xls.

         ![filtres de fichiers de la stratégie de session](./media/session-policy-file-filters.png)

        
    2. Dans la section **Inspection du contenu**, indiquez si vous voulez activer le moteur DLP pour analyser les documents et le contenu des fichiers.
 
     ![inspection du contenu dans la stratégie de session](./media/session-policy-content-inspection.png)

    3. Sous **Actions**, sélectionnez une des options suivantes : 

        - **Autoriser** : Définissez cette action pour autoriser explicitement le téléchargement selon les filtres de stratégie que vous définissez.

        - **Bloquer** : Définissez cette action pour bloquer explicitement le téléchargement selon les filtres de stratégie que vous définissez. Pour plus d’informations, consultez [Fonctionnement du blocage du téléchargement](#block-download).

        - **Protéger** : Si votre organisation utilise Azure Information Protection, vous pouvez définir une **action** pour appliquer une étiquette de classification définie dans Azure Information Protection sur le fichier. Pour plus d’informations, consultez [Fonctionnement de la protection du téléchargement](#protect-download).

         ![actions de stratégie de session](./media/session-policy-actions.png)

10. Vous pouvez **Créer une alerte pour chaque événement correspondant avec le niveau de gravité de la stratégie** et définissez une limite d’alerte, puis déterminez si vous voulez que l’alerte prenne la forme d’un e-mail, d’un SMS ou des deux.

    ![alerte de stratégie de session](./media/session-policy-alert.png)


## <a name="how-session-monitoring-works"></a>Fonctionnement de la surveillance des sessions

Quand vous créez une stratégie de session, chaque session utilisateur qui correspond à la stratégie est redirigée vers le contrôle de session du proxy plutôt que directement vers l’application. L’utilisateur reçoit une notification de surveillance qui l’informe que ses sessions sont surveillées.

   ![notification de surveillance de session](./media/session-monitoring-notice.png)

Si vous ne voulez pas informer l’utilisateur de cette surveillance, vous pouvez désactiver le message de notification.

1. Sous la roue dentée des paramètres, sélectionnez **Paramètres généraux**. 

2. Ensuite, dans les paramètres du proxy Cloud App Security, décochez la case **Notifier les utilisateurs**.

    ![désactiver la notification de surveillance de session](./media/disable-session-monitoring-notice.png)

Pour garder l’utilisateur dans la session, le proxy remplace tous les scripts Java, URL et cookies appropriés dans la session de l’application par des URL de proxy. Par exemple, si l’application renvoie une page avec des liens dont les domaines se terminent par myapp.com, le proxy remplace ces liens par des domaines se terminant par quelque chose comme : myapp.com.us.cas.ms. Ainsi, la session entière est surveillée par le proxy.

Le proxy enregistre les journaux de trafic de chaque session utilisateur acheminée vers lui. Les journaux de trafic incluent l’heure, l’adresse IP, l’agent utilisateur, les URL visitées et le nombre d’octets chargés et téléchargés. Ces journaux sont analysés et un rapport continu appelé **Cloud App Security Proxy** est ajouté à la liste des rapports Cloud Discovery dans le tableau de bord Cloud Discovery.

![rapport de proxy](./media/proxy-report.png)


Pour exporter ces journaux :

1. Accédez à la roue dentée des paramètres et cliquez sur **Proxy**.
2. Sur le côté droit du tableau, cliquez sur le bouton d’exportation ![bouton d’exportation](./media/export-button.png). 
3. Sélectionnez la plage du rapport et cliquez sur **Exporter**. Ce processus peut prendre un certain temps.

Pour télécharger le journal exporté :

1. Une fois que le rapport est prêt, accédez à **Examiner**, puis à **Rapports personnalisés**.
2. Dans le tableau, sélectionnez le rapport approprié dans la liste des **journaux du trafic proxy** et cliquez sur Télécharger ![bouton Télécharger](./media/download-button.png). 


## Fonctionnement du blocage du téléchargement <a name="block-download"></a>

Quand la valeur **Bloquer** est affectée à l’**action** à effectuer dans la stratégie de session du proxy Cloud App Security, le proxy empêche l’utilisateur de télécharger un fichier conformément aux filtres de fichiers de la stratégie. Un événement de téléchargement est reconnu par le proxy pour chaque application SAML et lorsqu’un utilisateur lance cet événement, le proxy intervient en temps réel pour l’empêcher de s’exécuter. À la réception d’un signal de téléchargement par un utilisateur, le proxy renvoie un message **Téléchargement restreint** à l’utilisateur et remplace le fichier téléchargé par un fichier texte qui contient un message personnalisable adressé à l’utilisateur, que vous pouvez configurer à partir de la stratégie de session du proxy.  

## Fonctionnement de la protection du téléchargement <a name="protect-download"></a>

Quand la valeur **Protéger** est affectée à l’**action** à effectuer dans la stratégie de session du proxy Cloud App Security, le proxy applique l’étiquetage et la protection ultérieure d’un fichier conformément aux filtres de fichiers de la stratégie. Les étiquettes sont configurées dans la console Azure Information Protection dans Azure et l’option **Protéger** doit être sélectionnée dans l’étiquette pour qu’elle apparaisse en tant qu’option dans la stratégie Cloud App Security. Quand une étiquette est sélectionnée et qu’un fichier correspondant aux critères de la stratégie Cloud App Security est téléchargé, l’étiquette et la protection correspondante (avec les autorisations) sont appliquées au fichier lors de son téléchargement. Le fichier original reste inchangé dans l’application cloud, tandis que le fichier téléchargé est désormais protégé. Les utilisateurs qui essaient d’accéder au fichier doivent respecter les exigences d’autorisation déterminées par la protection appliquée.  
 
  
## <a name="see-also"></a>Voir aussi  
[Blocage des téléchargements sur des appareils non gérés à l’aide des fonctionnalités de proxy Azure AD](use-case-proxy-block-session-aad.md)   
[Pour obtenir du support technique, consultez la page Support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  