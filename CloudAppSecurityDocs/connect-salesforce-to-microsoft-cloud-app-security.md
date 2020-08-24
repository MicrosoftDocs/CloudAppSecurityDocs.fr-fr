---
title: Connecter Salesforce à Cloud App Security
description: Cet article vous explique comment connecter votre application Salesforce à Cloud App Security à l’aide du connecteur d’API, afin de bénéficier de plus de contrôle et de visibilité lors de l’utilisation.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/06/2019
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 81ad720b3230ab49a752671bcdc7d45cf789aad7
ms.sourcegitcommit: 29a8e66c665f51d831516924ae4d9d8047b39276
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88780883"
---
# <a name="connect-salesforce-to-microsoft-cloud-app-security"></a>Connecter Salesforce à Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

Cet article fournit des instructions pour connecter Microsoft Cloud App Security à un compte Salesforce existant à l’aide de l’API de connecteur d’applications. Cette connexion vous permet de bénéficier de plus de visibilité et de contrôle lors de l’utilisation de Salesforce. Pour plus d’informations sur la façon dont Cloud App Security protège Salesforce, consultez [protéger Salesforce](protect-salesforce.md).

## <a name="how-to-connect-salesforce-to-cloud-app-security"></a>Comment connecter Salesforce à Cloud App Security

1. Nous vous recommandons d’avoir un compte d’administrateur de service dédié pour Cloud App Security.

1. Vérifiez que l’API REST est activée dans Salesforce.

    Votre compte Salesforce doit correspondre à l’une des éditions suivantes prenant en charge l’API REST :

    **Performance**, **Enterprise**, **Unlimited**ou **Developer**.

    L’édition **Professional** ne comprend pas l’API REST par défaut, mais elle peut être ajoutée sur demande.

    Vérifiez que l’API REST est disponible et activée dans votre édition, comme suit :

    * Connectez-vous à votre compte Salesforce et accédez à la page **Setup** (Configuration).

    * Sous **Gérer les utilisateurs**, accédez à la page **Profils**.

        ![profils Salesforce gérer les utilisateurs](media/salesforce-manageusers-profiles.png "profils Salesforce gérer les utilisateurs")

    * Créez un profil en cliquant sur **Nouveau**.
    * Choisissez le profil que vous venez de créer pour déployer Cloud App Security, puis cliquez sur **Modifier**. Ce profil sera utilisé pour le compte de service Cloud App Security pour configurer le connecteur d’applications.

         ![salesforce, modifier le profil](media/salesforce-edit-profile.png "salesforce, modifier le profil")

    * Vérifiez que les cases suivantes sont cochées :
      * **API activée**
      * **Afficher toutes les données**
      * **Gérer le contenu Salesforce CRM**
      * **Gérer les utilisateurs**
      * **[Interroger tous les fichiers](https://go.microsoft.com/fwlink/?linkid=2106480)**

      Si ces cases ne sont pas cochées, il peut être nécessaire de contacter Salesforce pour les ajouter à votre compte.

1. Si **Salesforce CRM Content** (Contenu CRM Salesforce) est activé pour votre organisation, vérifiez que le compte administratif actuel est également activé.

    1. Accédez à votre page de configuration de Salesforce.

        ![configuration de Salesforce](media/salesforce-setup.png "salesforce, configuration")

    1. Dans le menu latéral, sélectionnez **Manage Users** (Gérer les utilisateurs), puis cliquez sur **Utilisateurs**.

        ![menu salesforce, utilisateurs](media/salesforce-menu-users.png "menu salesforce, utilisateurs")

    1. Sélectionnez l’utilisateur administratif actuel pour votre utilisateur Cloud App Security dédié.

    1. Vérifiez que la case **Salesforce CRM Content User** (Utilisateur de contenu CRM Salesforce) est cochée.

        Si ce n’est pas le cas, cliquez sur **Edit** (Modifier), puis cochez la case.

        ![salesforce, utilisateur de contenu crm](media/salesforce-crm-content-user.png "salesforce, utilisateur de contenu crm")

    1. Cliquez sur **Enregistrer**.

1. Dans la console Cloud App Security, cliquez sur **Examiner**, puis sur **Applications connectées**.

1. Dans la page **Connecteurs d’application**, cliquez sur le bouton plus (+), puis sur **Salesforce**.

    ![connecter Salesforce](media/connect-salesforce.png "connecter salesforce")

1. Dans la page des paramètres Salesforce, sous l’onglet API, cliquez sur **suivez ce lien**, en fonction de l’instance que vous souhaitez installer.

1. Ceci ouvre la page de connexion à Salesforce. Entrez vos informations d’identification pour autoriser Cloud App Security à accéder à l’application Salesforce de votre équipe.

    ![connexion Salesforce](media/salesforce-logon.png "salesforce, connexion")

1. Salesforce vous demande si vous voulez autoriser Cloud App Security à accéder au journal d’informations et d’activité de votre équipe, et à effectuer toute activité en tant que membre de l’équipe. Pour continuer, cliquez sur **Autoriser**.

1. À ce stade, vous recevez une notification de réussite ou d’échec du déploiement. Cloud App Security est désormais autorisé dans Salesforce.com.

1. De retour dans la console Cloud App Security, vous devez recevoir un message indiquant que Salesforce a été correctement connecté.

1. Vérifiez que la connexion a réussi en cliquant sur **Tester l’API**.

    Le test peut prendre quelques minutes. Une fois que vous avez reçu une notification de réussite, cliquez sur **Terminé**.

Après avoir connecté Salesforce, vous recevez les événements comme suit : déclencheurs à partir du moment de la connexion, événements de connexion et piste d’audit d’installation pour les 60 jours précédant la connexion, surveillance des événements remontant à 30 jours ou à 1 jour, en fonction de votre licence Salesforce EventMonitoring. L’API Cloud App Security communique directement avec les API disponibles dans Salesforce. Comme Salesforce limite le nombre d’appels d’API qu’il peut recevoir, Cloud App Security prend ce point en considération et respecte la limite. Les API Salesforce envoient chaque réponse avec un champ pour les compteurs d’API, notamment le total disponible et le total restant. Cloud App Security calcule en pourcentage et veille à toujours garder 10 % des appels d’API disponibles restants.

> [!NOTE]
> La limitation Cloud App Security est calculée uniquement à partir de ses propres appels d’API avec Salesforce, et non avec ceux des autres applications qui effectuent des appels d’API avec Salesforce.
> La restriction des appels d’API en raison de la limitation peut ralentir la vitesse à laquelle les données sont absorbées dans Cloud App Security, mais le retard est généralement comblé dans la nuit.

Les événements Salesforce sont traités par Cloud App Security de la façon suivante :

* Événements de connexion toutes les 15 minutes
* Piste d’audit d’installation toutes les 15 minutes
* Journaux des événements toutes les heures. Pour plus d’informations sur les événements Salesforce, consultez [Using Event Monitoring](https://developer.salesforce.com/docs/atlas.en-us.api_rest.meta/api_rest/using_resources_event_log_files.htm) (Utilisation de la surveillance des événements).

Si vous rencontrez des problèmes lors de la connexion de l’application, consultez [résolution des problèmes liés aux connecteurs d’application](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
