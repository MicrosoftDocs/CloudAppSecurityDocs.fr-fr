---
title: Connecter Salesforce à Cloud App Security pour la visibilité et le contrôle d’utilisation | Microsoft Docs
description: Cet article fournit des informations sur la connexion de Salesforce à Cloud App Security à l’aide du connecteur d’API.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/13/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 776d7589-acdb-4cb6-99a0-3be2f7b6aab2
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: acac9a56ec2ecd55206c7e3cd6ccb743c3c1a65b
ms.sourcegitcommit: 77850c6777504c2478611cb71a387e7fcc5f2551
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51597032"
---
# <a name="connect-salesforce-to-microsoft-cloud-app-security"></a>Connecter Salesforce à Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

Cet article fournit des instructions pour connecter Microsoft Cloud App Security à un compte Salesforce existant à l’aide de l’API de connecteur d’applications.  
  
## <a name="how-to-connect-salesforce-to-cloud-app-security"></a>Comment connecter Salesforce à Cloud App Security  
  
1.  Nous vous recommandons d’avoir un compte d’administrateur de service dédié pour Cloud App Security.  
  
2.  Vérifiez que l’API REST est activée dans Salesforce.  
  
     Votre compte Salesforce doit correspondre à l’une des éditions suivantes prenant en charge l’API REST :  
  
     **Performance**, **Enterprise**, **Unlimited** ou **Developer**.  
  
     L’édition **Professional** ne comprend pas l’API REST par défaut, mais elle peut être ajoutée sur demande.  
  
     Vérifiez que l’API REST est disponible et activée dans votre édition, comme suit :  
  
    -   Connectez-vous à votre compte Salesforce et accédez à la page **Setup** (Configuration).  
  
    -   Sous **Gérer les utilisateurs**, accédez à la page **Profils**.  
  
         ![Salesforce - gérer les profils des utilisateurs](./media/salesforce-manageusers-profiles.png "Salesforce - gérer les profils des utilisateurs")  
  
    -   Créez un profil en cliquant sur **Nouveau**. 
    - Choisissez le profil que vous venez de créer pour déployer Cloud App Security, puis cliquez sur **Modifier**.  Il s’agit du profil à utiliser pour le compte de service Cloud App Security pour configurer le connecteur d’applications.  
  
         ![salesforce, modifier le profil](./media/salesforce-edit-profile.png "salesforce, modifier le profil")  
  
    -   Vérifiez que les cases suivantes sont cochées :   
        - **API activée**
        - **Afficher toutes les données** 
        - **Gérer le contenu Salesforce CRM**
        - **Gérer les utilisateurs**
        
        Si ces cases ne sont pas cochées, il peut être nécessaire de contacter Salesforce pour les ajouter à votre compte.  
             
3.  Si **Salesforce CRM Content** (Contenu CRM Salesforce) est activé pour votre organisation, vérifiez que le compte administratif actuel est également activé.  
  
    1.  Accédez à votre page de configuration de Salesforce.  
  
         ![salesforce, configuration](./media/salesforce-setup.png "salesforce, configuration")  
  
    2.  Dans le menu latéral, sélectionnez **Manage Users** (Gérer les utilisateurs), puis cliquez sur **Utilisateurs**.  
  
         ![menu salesforce, utilisateurs](./media/salesforce-menu-users.png "menu salesforce, utilisateurs")  
  
    3.  Sélectionnez l’utilisateur administratif actuel pour votre utilisateur Cloud App Security dédié.  
  
    4.  Vérifiez que la case **Salesforce CRM Content User** (Utilisateur de contenu CRM Salesforce) est cochée.  
  
         Si ce n’est pas le cas, cliquez sur **Edit** (Modifier), puis cochez la case.  
  
         ![salesforce, utilisateur de contenu crm](./media/salesforce-crm-content-user.png "salesforce, utilisateur de contenu crm")  
  
    5.  Cliquez sur **Enregistrer**.  
  
4.  Dans la console Cloud App Security, cliquez sur **Examiner**, puis sur **Applications connectées**.  
  
5.  Dans la page **Connecteurs d’application**, cliquez sur le bouton plus (+), puis sur **Salesforce**.  
  
     ![connecter salesforce](./media/connect-salesforce.png "connecter salesforce")  
  
6.  Dans la page des paramètres Salesforce, sous l’onglet API, cliquez sur **suivez ce lien**, en fonction de l’instance que vous souhaitez installer.  
  
7.  Ceci ouvre la page de connexion à Salesforce. Entrez vos informations d’identification pour autoriser Cloud App Security à accéder à l’application Salesforce de votre équipe.  
  
     ![Salesforce - connexion](./media/salesforce-logon.png "Salesforce - connexion")  
  
8.  Salesforce vous demande si vous voulez autoriser Cloud App Security à accéder au journal d’informations et d’activité de votre équipe, et à effectuer toute activité en tant que membre de l’équipe. Pour continuer, cliquez sur **Autoriser**.  
  
9. À ce stade, vous recevez une notification de réussite ou d’échec du déploiement. Cloud App Security est désormais autorisé dans Salesforce.com.  
  
10. De retour dans la console Cloud App Security, vous devez recevoir un message indiquant que Salesforce a été correctement connecté.  
  
11. Vérifiez la connexion en cliquant sur **Test API** (Tester l’API).  
  
     Le test peut prendre quelques minutes. Une fois que vous avez reçu une notification de réussite, cliquez sur **Terminé**.  
  
  
Après avoir connecté Salesforce, vous recevez les événements comme suit : déclencheurs à partir du moment de la connexion, événements de connexion et piste d’audit d’installation pour les 60 jours précédant la connexion, surveillance des événements remontant à 30 jours ou à 1 jour, en fonction de votre licence Salesforce EventMonitoring. L’API Cloud App Security communique directement avec les API disponibles dans Salesforce. Comme Salesforce limite le nombre d’appels d’API qu’il peut recevoir, Cloud App Security prend ce point en considération et respecte la limite. Les API Salesforce envoient chaque réponse avec un champ pour les compteurs d’API, notamment le total disponible et le total restant. Cloud App Security calcule en pourcentage et veille à toujours garder 10 % des appels d’API disponibles restants. 

> [!NOTE]
> La limitation Cloud App Security est calculée uniquement à partir de ses propres appels d’API avec Salesforce, et non avec ceux des autres applications qui effectuent des appels d’API avec Salesforce.
> La restriction des appels d’API en raison de la limitation peut ralentir la vitesse à laquelle les données sont absorbées dans Cloud App Security, mais le retard est généralement comblé dans la nuit.


Les événements Salesforce sont traités par Cloud App Security de la façon suivante : 
  
- Événements de connexion toutes les 15 minutes
- Piste d’audit d’installation toutes les 15 minutes
- Les journaux de Salesforce suivent l’activité d’utilisation sur une période de 24 heures, de 00:00 à 23:59 heure UTC. Les événements dans Salesforce génèrent des données de journal en temps réel. Toutefois, les fichiers journaux sont générés par Salesforce le lendemain d’un événement, pendant les heures creuses. Par conséquent, les données du fichier journal ne sont disponibles qu’au moins un jour après l’événement. Pour plus d’informations sur les événements Salesforce, consultez [Using Event Monitoring](https://developer.salesforce.com/docs/atlas.en-us.api_rest.meta/api_rest/using_resources_event_log_files.htm) (Utilisation de la surveillance des événements).


## <a name="next-steps"></a>Étapes suivantes  
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  