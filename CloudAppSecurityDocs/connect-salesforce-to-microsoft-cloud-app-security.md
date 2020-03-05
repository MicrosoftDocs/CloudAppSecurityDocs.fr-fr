---
title: Connecter Salesforce à Cloud App Security
description: Cet article fournit des informations sur la façon de connecter votre Salesforce à Cloud App Security à l’aide du connecteur API pour la visibilité et le contrôle de l’utilisation.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/06/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: b47b17e74df346b1e1b1cdf01522d5b980360b78
ms.sourcegitcommit: 582779b75be41e57fb1d773d1cf01f6b8598521e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78274681"
---
# <a name="connect-salesforce-to-microsoft-cloud-app-security"></a>Connecter Salesforce à Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

Cet article fournit des instructions pour connecter Microsoft Cloud App Security à votre compte Salesforce existant à l’aide de l’API du connecteur d’applications. Cette connexion vous donne une visibilité et un contrôle sur l’utilisation de salesforce. Pour plus d’informations sur la façon dont Cloud App Security protège Salesforce, consultez [protéger Salesforce](protect-salesforce.md).

## <a name="how-to-connect-salesforce-to-cloud-app-security"></a>Comment connecter Salesforce à Cloud App Security

1. Il est recommandé d’avoir un compte d’administrateur de service dédié pour Cloud App Security.

1. Vérifiez que l’API REST est activée dans Salesforce.

    Votre compte Salesforce doit correspondre à l’une des éditions suivantes prenant en charge l’API REST :

    **Performance**, **Enterprise**, **Unlimited**ou **Developer**.

    L’édition **Professional** n’a pas d’API REST par défaut, mais elle peut être ajoutée à la demande.

    Vérifiez que l’API REST est disponible et activée dans votre édition, comme suit :

    * Connectez-vous à votre compte Salesforce et accédez à la page **d’installation** .

    * Sous **gérer les utilisateurs**, accédez à la page **profils utilisateur** .

        ![profils Salesforce gérer les utilisateurs](media/salesforce-manageusers-profiles.png "profils Salesforce gérer les utilisateurs")

    * Créez un nouveau profil en cliquant sur **nouveau**.
    * Choisissez le profil que vous venez de créer pour déployer Cloud App Security, puis cliquez sur **modifier**. Ce profil sera utilisé pour le compte de service Cloud App Security pour configurer le connecteur d’applications.

         ![Salesforce-modifier le profil](media/salesforce-edit-profile.png "Salesforce-modifier le profil")

    * Vérifiez que les cases suivantes sont cochées :
      * **API activée**
      * **Afficher toutes les données**
      * **Gérer le contenu Salesforce CRM**
      * **Gérer les utilisateurs**
      * **[Interroger tous les fichiers](https://go.microsoft.com/fwlink/?linkid=2106480)**

      Si ces cases à cocher ne sont pas sélectionnées, vous devrez peut-être contacter Salesforce pour les ajouter à votre compte.

1. Si **Salesforce CRM Content** (Contenu CRM Salesforce) est activé pour votre organisation, vérifiez que le compte administratif actuel est également activé.

    1. Accédez à votre page de configuration de Salesforce.

        ![configuration de Salesforce](media/salesforce-setup.png "configuration de Salesforce")

    1. Dans le menu latéral, sélectionnez **Manage Users** (Gérer les utilisateurs), puis cliquez sur **Utilisateurs**.

        ![utilisateurs du menu Salesforce](media/salesforce-menu-users.png "utilisateurs du menu Salesforce")

    1. Sélectionnez l’utilisateur administratif actuel pour votre utilisateur Cloud App Security dédié.

    1. Vérifiez que la case **Salesforce CRM Content User** (Utilisateur de contenu CRM Salesforce) est cochée.

        Si ce n’est pas le cas, cliquez sur **modifier** , puis activez la case à cocher.

        ![utilisateur de contenu CRM Salesforce](media/salesforce-crm-content-user.png "utilisateur de contenu CRM Salesforce")

    1. Cliquez sur **Enregistrer**.

1. Dans la console Cloud App Security, cliquez sur **Examiner**, puis sur **Applications connectées**.

1. Dans la page **Connecteurs d’application**, cliquez sur le bouton plus (+), puis sur **Salesforce**.

    ![connecter Salesforce](media/connect-salesforce.png "connecter Salesforce")

1. Dans la page des paramètres Salesforce, sous l’onglet API, cliquez sur **suivez ce lien**, en fonction de l’instance que vous souhaitez installer.

1. La page de connexion Salesforce s’ouvre. Entrez vos informations d’identification pour autoriser Cloud App Security à accéder à l’application Salesforce de votre équipe.

    ![connexion Salesforce](media/salesforce-logon.png "connexion Salesforce")

1. Salesforce vous demande si vous voulez autoriser Cloud App Security à accéder au journal d’informations et d’activité de votre équipe, et à effectuer toute activité en tant que membre de l’équipe. Pour continuer, cliquez sur **Autoriser**.

1. À ce stade, vous recevrez une notification de réussite ou d’échec pour le déploiement. Cloud App Security est désormais autorisé dans Salesforce.com.

1. De retour dans la console Cloud App Security, vous devez recevoir un message indiquant que Salesforce a été correctement connecté.

1. Vérifiez la connexion en cliquant sur **Test API** (Tester l’API).

    Le test peut prendre quelques minutes. Une fois que vous avez reçu une notification de réussite, cliquez sur **Terminé**.

Après avoir connecté Salesforce, vous recevrez des événements comme suit : les déclencheurs à partir du moment de la connexion, les événements de connexion et la piste d’audit du programme d’audit pour 60 jours avant la connexion, surveillance 30 jours, ou 1 jour, en fonction de votre surveillance Salesforce licence. L’API Cloud App Security communique directement avec les API disponibles dans Salesforce. Comme Salesforce limite le nombre d’appels d’API qu’il peut recevoir, Cloud App Security prend ce point en considération et respecte la limite. Les API Salesforce envoient chaque réponse avec un champ pour les compteurs d’API, notamment le total disponible et le total restant. Cloud App Security calcule en pourcentage et veille à toujours garder 10 % des appels d’API disponibles restants.

> [!NOTE]
> La limitation Cloud App Security est calculée uniquement à partir de ses propres appels d’API avec Salesforce, et non avec ceux des autres applications qui effectuent des appels d’API avec Salesforce.
> La restriction des appels d’API en raison de la limitation peut ralentir la vitesse à laquelle les données sont absorbées dans Cloud App Security, mais le retard est généralement comblé dans la nuit.

Les événements Salesforce sont traités par Cloud App Security de la façon suivante :

* Événements de connexion toutes les 15 minutes
* Configurer les pistes d’audit toutes les 15 minutes
* Journaux des événements toutes les heures. Pour plus d’informations sur les événements Salesforce, consultez [Utilisation de la surveillance des événements](https://developer.salesforce.com/docs/atlas.en-us.api_rest.meta/api_rest/using_resources_event_log_files.htm).

Si vous rencontrez des problèmes lors de la connexion de l’application, consultez [résolution des problèmes liés aux connecteurs d’application](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Étapes suivantes :

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
