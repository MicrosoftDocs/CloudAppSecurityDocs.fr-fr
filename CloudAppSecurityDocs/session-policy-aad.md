---
title: Créer des stratégies de session pour obtenir une meilleure visibilité des activités de session utilisateur et bloquer les téléchargements | Microsoft Docs
description: Cette rubrique décrit la procédure de configuration d’une stratégie de session du Contrôle d’accès conditionnel aux applications de Cloud App Security pour améliorer la visibilité des activités de session utilisateur et bloquer les téléchargements à l’aide des fonctionnalités du proxy.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/9/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 745df28a-654c-4abf-9c90-203841169f90
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: cf13b7439baafa11a94aa8420ec050781fde88fc
ms.sourcegitcommit: 5d549d7e2d15f36452fe3c3d143493a7014b457b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2018
---
*S’applique à : Microsoft Cloud App Security*

# <a name="session-policies"></a>Stratégies de session 

> [!NOTE]
> Il s’agit d’une fonctionnalité en préversion.


>[!div class="step-by-step"]
[« Précédent : Déployer le Contrôle d’accès conditionnel aux applications](proxy-deployment-aad.md)
[Suivant : Stratégies d’accès »](access-policy-aad.md)


Les stratégies de session Microsoft Cloud App Security permettent une surveillance en temps réel au niveau de la session, qui vous offre une visibilité plus précise des applications cloud et la possibilité de prendre différentes mesures selon la stratégie que vous définissez pour une session utilisateur. Au lieu [d’autoriser ou de bloquer complètement l’accès](access-policy-aad.md), avec le contrôle de session, vous pouvez autoriser l’accès pendant la surveillance de la session et/ou limiter des activités de session particulières à l’aide des fonctionnalités du proxy inversé du Contrôle d’accès conditionnel aux applications. 

Par exemple, vous pouvez décider que pour les appareils non gérés ou pour les sessions provenant d’emplacements spécifiques, vous voulez autoriser l’utilisateur à accéder à l’application, mais aussi limiter le téléchargement des fichiers sensibles ou exiger que certains documents soient protégés lors de leur téléchargement. Les stratégies de session vous permettent de définir ces contrôles de session utilisateur, d’autoriser l’accès et de :

- [Surveiller toutes les activités](#monitor-session)
- [Bloquer tous les téléchargements](#block-download)
- [Bloquer des activités spécifiques](#block-activities)
- [Protéger des fichiers lors du téléchargement](#protect-download)
 

## <a name="prerequisites-to-using-session-policies"></a>Prérequis à l’utilisation de stratégies de session

- Licence Azure AD Premium P2.
- Les applications appropriées doivent être [déployées avec le Contrôle d’accès conditionnel aux applications](proxy-deployment-aad.md)
- Une [stratégie d’accès conditionnel Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) doit être en place pour rediriger les utilisateurs vers le Microsoft Cloud App Security, comme décrit ci-dessous.

> [!NOTE]
> - En préversion privée, les stratégies de session prennent également en charge les applications qui sont configurées avec des fournisseurs d’identité autres qu’Azure AD. Pour plus d’informations sur la préversion privée, envoyez un e-mail à mcaspreview@microsoft.com.

## <a name="create-an-azure-ad-conditional-access-policy"></a>Créer une stratégie d’accès conditionnel Azure AD

Les stratégies d’accès conditionnel Azure Active Directory et les stratégies de session Cloud App Security travaillent conjointement pour examiner chaque session utilisateur et prendre des décisions stratégiques pour chaque application. Pour configurer une stratégie d’accès conditionnel dans Azure AD, procédez comme suit :

1. Configurez une [stratégie d’accès conditionnel Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) avec des attributions pour l’utilisateur ou le groupe d’utilisateurs et l’application SAML que vous souhaitez contrôler avec le Contrôle d’accès conditionnel aux applications. 

   > [!NOTE]
   > Seules les applications [déployées avec le Contrôle d’accès conditionnel aux applications](proxy-deployment-aad.md) sont concernées par cette stratégie.

2. Acheminez les utilisateurs vers Microsoft Cloud App Security en sélectionnant **Utiliser les restrictions appliquées au Contrôle d’accès conditionnel aux applications** dans le panneau **Session**.

   ![Accès conditionnel Azure AD aux restrictions du Contrôle d’accès conditionnel aux applications](./media/proxy-deploy-restrictions-aad.png)

## <a name="create-a-cloud-app-security-session-policy"></a>Créer une stratégie de session Cloud App Security 

Pour créer une stratégie de session, suivez cette procédure :

1. Dans le portail, sélectionnez **Contrôle**, puis **Stratégies**.
2. Dans la page **Stratégies**, cliquez sur **Créer une stratégie** et sélectionnez **Stratégie de session**.  

   ![Créer une stratégie de session](./media/create-session-policy.png)

3. Dans la fenêtre **Stratégie de session**, donnez un nom à votre stratégie, comme *Bloquer le téléchargement des documents sensibles dans Box pour les utilisateurs du service marketing*.

   ![Nouvelle stratégie de session](./media/new-session-policy.png)

4. Dans le champ **Type de contrôle de session** : 

   1. Sélectionnez **Surveiller uniquement** pour surveiller uniquement les activités des utilisateurs. Cette opération crée une stratégie de surveillance uniquement dans laquelle toutes les connexions, tous les téléchargements heuristiques et tous les types d’activités sont téléchargés, pour les applications que vous avez sélectionnées.

   2. Sélectionnez **Contrôler le téléchargement du fichier (avec DLP)** pour surveiller les activités des utilisateurs et prendre des mesures supplémentaires, comme le blocage ou la protection des téléchargements pour les utilisateurs.

      ![type de contrôle de stratégie de session](./media/session-policy-control-type.png)
   
   3. Sélectionnez **Bloquer les activités** pour bloquer des activités spécifiques que vous pouvez sélectionner à l’aide du filtre **Type d’activité**. Toutes les activités des applications sélectionnées sont surveillées (et signalées dans le journal d’activité). Les activités spécifiques que vous sélectionnez sont bloquées si vous sélectionnez l’action **Bloquer** et déclenchent des alertes si vous sélectionnez l’action **Tester** et que les alertes sont activées.

1. Sous **Source de l’activité** dans la section **Activités remplissant toutes les conditions suivantes**, sélectionnez d’autres filtres d’activité à appliquer à la stratégie. Ceux-ci peuvent inclure les options suivantes : 

   - **Balise de l’appareil** : Utilisez ce filtre pour identifier les appareils non gérés.

   - **Emplacement** : Utilisez ce filtre pour identifier les emplacements inconnus (et par conséquent à risque). 

   - **Adresse IP** : Utilisez ce filtre pour filtrer selon des adresses IP ou utiliser des balises d’adresse IP déjà attribuées. 

   - **Étiquette agent utilisateur** : Utilisez ce filtre pour activer l’heuristique afin d’identifier les applications mobiles et de bureau. Vous devez définir ce filtre comme étant égal à ou différent du **client natif** et le tester sur vos applications mobiles et de bureau pour chaque application cloud.
         
       ![prise en charge du client natif](./media/user-agent-tag.png)

     >[!NOTE]
     >Les stratégies de session ne prennent pas en charge les applications mobiles et de bureau. Veillez à tester les stratégies de session pour vérifier qu’elles n’interfèrent pas avec les fonctionnalités des applications mobiles et de bureau. Si nécessaire, excluez les applications mobiles et de bureau des stratégies de session.

     ![source de l’activité de la stratégie de session](./media/session-policy-activity-filters.png)

6. Si vous avez sélectionné l’option **Contrôler le téléchargement du fichier (avec DLP)**  :

   1. Sous **Source de l’activité** dans la section **Fichiers remplissant toutes les conditions suivantes**, sélectionnez d’autres filtres de fichiers à appliquer à la stratégie. Ceux-ci peuvent inclure les options suivantes :

      - **Étiquette de classification** : Utilisez ce filtre si votre organisation utilise Azure Information Protection et que vos données ont été protégées par ses étiquettes de classification. Vous pouvez alors filtrer des fichiers en fonction de l’étiquette de classification que vous leur avez appliquée. Pour plus d’informations sur l’intégration entre Cloud App Security et Azure Information Protection, consultez [Intégration d’Azure Information Protection](azip-integration.md).

      - **Nom de fichier** : Utilisez ce filtre pour appliquer la stratégie à des fichiers spécifiques.

      - **Type de fichier** : Utilisez ce filtre pour appliquer la stratégie à des types de fichiers spécifiques, par exemple, pour bloquer le téléchargement de tous les fichiers .xls.

        ![filtres de fichiers de la stratégie de session](./media/session-policy-file-filters.png)

        
   2. Dans la section **Inspection du contenu**, indiquez si vous voulez activer le moteur DLP pour analyser les documents et le contenu des fichiers.
 
      ![inspection du contenu dans la stratégie de session](./media/session-policy-content-inspection.png)

   3. Sous **Actions**, sélectionnez une des options suivantes : 

      - **Tester (Surveiller toutes les activités)**  : définissez cette action pour autoriser explicitement le téléchargement selon les filtres de stratégie que vous définissez.

      - **Bloquer (Bloquer le téléchargement de fichiers et surveiller toutes les activités)**  : définissez cette action pour bloquer explicitement le téléchargement selon les filtres de stratégie que vous définissez. Pour plus d’informations, consultez [Fonctionnement du blocage du téléchargement](#block-download).

      - **Protéger (Appliquer l’étiquette de classification pour télécharger et surveiller toutes les activités)**  : cette action est uniquement disponible si vous avez sélectionné **Contrôler le téléchargement du fichier (avec DLP)** sous **Stratégie de session**. Si votre organisation utilise Azure Information Protection, vous pouvez définir une **action** pour appliquer une étiquette de classification définie dans Azure Information Protection sur le fichier. Pour plus d’informations, consultez [Fonctionnement de la protection du téléchargement](#protect-download).

        ![actions de stratégie de session](./media/session-policy-actions.png)

7. Vous pouvez **Créer une alerte pour chaque événement correspondant avec le niveau de gravité de la stratégie** et définissez une limite d’alerte, puis déterminez si vous voulez que l’alerte prenne la forme d’un e-mail, d’un SMS ou des deux.

   ![alerte de stratégie de session](./media/session-policy-alert.png)


## Surveiller toutes les activités <a name="monitor-session"></a>

Quand vous créez une stratégie de session, chaque session utilisateur qui correspond à la stratégie est redirigée vers le contrôle de session plutôt que directement vers l’application. L’utilisateur reçoit une notification de surveillance qui l’informe que ses sessions sont surveillées.

   ![notification de surveillance de session](./media/session-monitoring-notice.png)

Si vous ne voulez pas informer l’utilisateur de cette surveillance, vous pouvez désactiver le message de notification.

1. Sous la roue dentée des paramètres, sélectionnez **Paramètres généraux**. 

2. Puis, sous les paramètres du Contrôle d’accès conditionnel aux applications, décochez la case **Aviser les utilisateurs**.

    ![désactiver la notification de surveillance de session](./media/disable-session-monitoring-notice.png)

Pour garder l’utilisateur dans la session, le Contrôle d’accès conditionnel aux applications remplace tous les URL, scripts de Java et cookies appropriés dans la session de l’application par des URL de Contrôle d’accès conditionnel aux applications. Par exemple, si l’application renvoie une page avec des liens dont les domaines se terminent par myapp.com, le Contrôle d’accès conditionnel aux applications remplace ces liens par des domaines se terminant par quelque chose comme : myapp.com.us.cas.ms. Ainsi, la session entière est surveillée par Microsoft Cloud App Security.

Le Contrôle d’accès conditionnel aux applications enregistre les journaux de trafic de chaque session utilisateur acheminée vers lui. Les journaux de trafic incluent l’heure, l’adresse IP, l’agent utilisateur, les URL visitées et le nombre d’octets chargés et téléchargés. Ces journaux sont analysés et un rapport continu appelé **Contrôle d’accès conditionnel aux applications de Cloud App Security** est ajouté à la liste des rapports Cloud Discovery dans le tableau de bord Cloud Discovery.

![Rapport du Contrôle d’accès conditionnel aux applications](./media/proxy-report.png)


Pour exporter ces journaux :

1. Accédez à la roue dentée des paramètres et cliquez sur **Contrôle d’accès conditionnel aux applications**.
2. Sur le côté droit du tableau, cliquez sur le bouton d’exportation ![bouton d’exportation](./media/export-button.png). 
3. Sélectionnez la plage du rapport et cliquez sur **Exporter**. Ce processus peut prendre un certain temps.

Pour télécharger le journal exporté :

1. Une fois que le rapport est prêt, accédez à **Examiner**, puis à **Rapports personnalisés**.
2. Dans la table, sélectionnez le rapport approprié dans la liste des **journaux du trafic du Contrôle d’accès conditionnel aux applications** et cliquez sur le ![bouton Télécharger](./media/download-button.png). 


## Bloquer tous les téléchargements <a name="block-download"></a>

Quand la valeur **Bloquer** est définie sur **Action** à prendre dans la stratégie de session de Cloud App Security, le Contrôle d’accès conditionnel aux applications empêche un utilisateur de télécharger un fichier conformément aux filtres de fichiers de la stratégie. Un événement de téléchargement est reconnu par Microsoft Cloud App Security pour chaque application SAML et lorsqu’un utilisateur lance cet événement, le Contrôle d’accès conditionnel aux applications intervient en temps réel pour l’empêcher de s’exécuter. À la réception d’un signal de téléchargement par un utilisateur, le Contrôle d’accès conditionnel aux applications renvoie un message **Téléchargement restreint** à l’utilisateur et remplace le fichier téléchargé par un fichier texte qui contient un message personnalisable adressé à l’utilisateur, que vous pouvez configurer à partir de la stratégie de session.  

## Bloquer des activités spécifiques <a name="block-activities"></a>

Quand l’option **Bloquer les activités** est définie pour le **Type d’activité**, vous pouvez sélectionner des activités spécifiques à bloquer dans des applications spécifiques. Toutes les activités des applications sélectionnées sont surveillées (et signalées dans le journal d’activité) et les actions spécifiques que vous sélectionnez sont bloquées si vous sélectionnez l’action **Bloquer** et déclenchent des alertes si vous sélectionnez l’action **Tester** et que les alertes sont activées.

## Protéger des fichiers lors du téléchargement <a name="protect-download"></a>
Sélectionnez **Bloquer les activités** pour bloquer des activités spécifiques que vous pouvez sélectionner à l’aide du filtre **Type d’activité**. Toutes les activités des applications sélectionnées sont surveillées (et signalées dans le journal d’activité). Les activités spécifiques que vous sélectionnez sont bloquées si vous sélectionnez l’action **Bloquer** et déclenchent des alertes si vous sélectionnez l’action **Tester** et que les alertes sont activées.
Quand la valeur **Protéger** est définie sur **Action** à prendre dans la stratégie de session de Cloud App Security, le Contrôle d’accès conditionnel aux applications applique l’étiquetage et la protection ultérieure d’un fichier conformément aux filtres de fichiers de la stratégie. Les étiquettes sont configurées dans la console Azure Information Protection dans Azure et l’option **Protéger** doit être sélectionnée dans l’étiquette pour qu’elle apparaisse en tant qu’option dans la stratégie Cloud App Security. Quand une étiquette est sélectionnée et qu’un fichier correspondant aux critères de la stratégie Cloud App Security est téléchargé, l’étiquette et la protection correspondante (avec les autorisations) sont appliquées au fichier lors de son téléchargement. Le fichier original reste inchangé dans l’application cloud, tandis que le fichier téléchargé est désormais protégé. Les utilisateurs qui essaient d’accéder au fichier doivent respecter les exigences d’autorisation déterminées par la protection appliquée.  
 
>[!div class="step-by-step"]
[« Précédent : Déployer le Contrôle d’accès conditionnel aux applications](proxy-deployment-aad.md)
[Suivant : Stratégies d’accès »](access-policy-aad.md)

 
## <a name="see-also"></a>Voir aussi  
[Blocage des téléchargements sur des appareils non gérés à l’aide des fonctionnalités du Contrôle d’accès conditionnel aux applications Azure AD](use-case-proxy-block-session-aad.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  