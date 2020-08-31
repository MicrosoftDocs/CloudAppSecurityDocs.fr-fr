---
title: Gérer l’accès administrateur au portail Cloud App Security
description: Cet article explique comment définir l’accès au portail Cloud App Security pour vos administrateurs.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 06/07/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 1818697f5d5ad26d13cc2bf37e35cecc20f70fdb
ms.sourcegitcommit: c174a7ada5c6a14f0fea9870672898c54e5e3b52
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89150109"
---
# <a name="manage-admin-access"></a>Gérer l’accès administrateur

*S’applique à : Microsoft Cloud App Security*

Microsoft Cloud App Security prend en charge le contrôle d’accès basé sur les rôles. Cet article explique comment définir l’accès au portail Cloud App Security pour vos administrateurs. Pour plus d’informations sur l’attribution de rôles d’administrateur, consultez les Articles relatifs à [Azure Active Directory](/azure/active-directory/active-directory-assign-admin-roles) et [Microsoft 365](/office365/admin/add-users/assign-admin-roles).

## <a name="microsoft-365-and-azure-ad-roles-with-access-to-cloud-app-security"></a>Microsoft 365 et Azure AD rôles ayant accès à Cloud App Security

Par défaut, les rôles d’administrateur Microsoft 365 et [Azure Active Directory (Azure AD)](/azure/active-directory/users-groups-roles/directory-assign-admin-roles) suivants ont accès aux Cloud App Security :

- **Administrateur général et Administrateur de la sécurité :** les administrateurs avec un **Accès total** disposent d’autorisations complètes dans Cloud App Security. Ils peuvent ajouter des administrateurs, ajouter des stratégies et des paramètres, charger des journaux et effectuer des actions de gouvernance.

- **Administrateur de conformité** : dispose d’autorisations en lecture seule et peut gérer les alertes. Impossible d’accéder aux recommandations de sécurité pour les plateformes Cloud. Peut créer et modifier des stratégies de fichier, autoriser des actions de gouvernance de fichier et afficher tous les rapports intégrés sous Gestion des données.

- **Administrateur des données de conformité :** Possède des autorisations en lecture seule, peut créer et modifier des stratégies de fichier, autoriser des actions de gouvernance de fichiers et afficher tous les rapports de découverte. Impossible d’accéder aux recommandations de sécurité pour les plateformes Cloud.

- **Opérateur de sécurité :** Possède des autorisations en lecture seule et peut gérer les alertes.

- **Lecteur Sécurité** : dispose d’autorisations en lecture seule et peut gérer les alertes. Le Lecteur Sécurité ne peut pas effectuer les actions suivantes :

  - Créer des stratégies ou modifier et changer des stratégies existantes
  - Effectuer des actions de gouvernance
  - Charger des journaux de découverte
  - Interdire ou approuver des applications tierces
  - Accéder à la page de paramètres de la plage d’adresses IP
  - Accéder aux pages contenant des paramètres
  - Accéder aux paramètres de découverte
  - Accéder à la page de connecteurs d’application
  - Accéder au journal de gouvernance
  - Accéder à la page Gérer des rapports d’instantanés
  - Accès et modification de l’agent SIEM

- **Lecteur global :** Dispose d’un accès complet en lecture seule à tous les aspects de Microsoft Cloud App Security. Impossible de modifier des paramètres ou d’effectuer des actions.

> [!NOTE]
> Les rôles Microsoft 365 et Azure AD ne sont pas répertoriés dans la page **gérer l’accès administrateur** .

En outre, les Cloud App Security rôles d’administrateur spécifiques suivants peuvent être configurés dans le portail Cloud App Security :

- **Administrateur d’application/d’instance :** Dispose d’autorisations complètes ou en lecture seule pour toutes les données de Microsoft Cloud App Security qui traitent exclusivement de l’application ou de l’instance spécifique d’une application sélectionnée. Par exemple, vous accordez à un utilisateur l’autorisation d’administrateur sur votre instance de Box European. L’administrateur verra uniquement les données qui sont liées à l’instance de Box European, qu’il s’agisse de fichiers, d’activités, de stratégies ou d’alertes :

  - Page des activités : seules les activités concernant l’application spécifique
  - Alertes : seules les alertes relatives à l’application spécifique
  - Stratégies : peut afficher toutes les stratégies et, si des autorisations complètes sont attribuées, modifier ou créer uniquement les stratégies qui traitent exclusivement avec l’application/l’instance
  - Page Comptes : seuls les comptes de l’application/instance spécifique
  - Autorisations d’application : seules les autorisations pour l’application/instance spécifique
  - Page des fichiers : seuls les fichiers de l’application/instance spécifique
  - Contrôle d’accès conditionnel aux applications : aucune autorisation
  - Activité Cloud Discovery : aucune autorisation
  - Extensions de sécurité : autorisations uniquement pour un jeton d’API avec des autorisations utilisateur
  - Actions de gouvernance : uniquement pour l’application/instance spécifique
  - Recommandations de sécurité pour les plateformes Cloud-aucune autorisation

- **Administrateur du groupe d’utilisateurs :** Dispose d’autorisations complètes ou en lecture seule pour toutes les données de Microsoft Cloud App Security qui traitent exclusivement du groupe spécifique sélectionné ici. Par exemple, si vous accordez à un utilisateur l’autorisation d’administrateur sur le groupe « Allemagne - tous les utilisateurs », l’administrateur peut visualiser et modifier les informations dans Microsoft Cloud App Security uniquement pour ce groupe d’utilisateurs :

  - Page des activités : seules les activités concernant les utilisateurs dans le groupe
  - Alertes : seules les alertes relatives aux utilisateurs dans le groupe
  - Stratégies : peut afficher toutes les stratégies et, si des autorisations complètes sont attribuées, modifier ou créer uniquement les stratégies qui concernent exclusivement les utilisateurs du groupe.
  - Page Comptes : seuls les comptes pour les utilisateurs spécifiques dans le groupe
  - Autorisations d’application : aucune autorisation
  - Page Fichiers : aucune autorisation
  - Contrôle d’accès conditionnel aux applications : aucune autorisation
  - Activité Cloud Discovery : aucune autorisation
  - Extensions de sécurité : autorisations uniquement pour un jeton d’API avec les utilisateurs dans le groupe
  - Actions de gouvernance : uniquement pour les utilisateurs spécifiques dans le groupe
  - Recommandations de sécurité pour les plateformes Cloud-aucune autorisation

- **Cloud Discovery administrateur général :**  A l’autorisation d’afficher et de modifier tous les paramètres et données de Cloud Discovery. L’administrateur Global Discovery a accès comme suit :

  - Paramètres
    - Paramètres du système - Affichage uniquement
    - Paramètres Cloud Discovery - Tout afficher et modifier (les autorisations d’anonymisation dépendent de l’autorisation de celle-ci lors de l’attribution de rôle)
  - Activité Cloud Discovery - Autorisations complètes
  - Alertes - Seules les alertes liées aux données Cloud Discovery
  - Stratégies - Peut afficher toutes les stratégies et peut modifier ou créer uniquement des stratégies Cloud Discovery
  - Page Activités - Aucune autorisation
  - Page Comptes - Aucune autorisation
  - Autorisations d’application : aucune autorisation
  - Page Fichiers : aucune autorisation
  - Contrôle d’accès conditionnel aux applications : aucune autorisation
  - Extensions de sécurité - Aucune autorisation
  - Actions liées à la gouvernance - Cloud Discovery uniquement
  - Recommandations de sécurité pour les plateformes Cloud-aucune autorisation

- **Cloud Discovery l’administrateur du rapport :** Dispose des autorisations pour afficher toutes les données dans Cloud App Security qui traitent exclusivement des rapports Cloud Discovery spécifiques sélectionnés. Par exemple, vous pouvez accorder une autorisation d’administrateur à un rapport continu à partir de Microsoft Defender ATP. L’administrateur de la découverte verra uniquement les données de Cloud Discovery relatives à cette source de données et au catalogue d’applications. Cet administrateur n’aura pas accès aux pages des **activités**, des **fichiers**ou des **recommandations de sécurité** et un accès limité aux stratégies.

## <a name="override-admin-permissions"></a>Remplacer les autorisations d’administrateur

Si vous souhaitez remplacer l’autorisation d’un administrateur de Azure Active Directory ou Microsoft 365, vous pouvez le faire en ajoutant manuellement l’utilisateur à Cloud App Security et en attribuant les autorisations utilisateur. Par exemple, pour affecter à Stéphanie, qui est titulaire du rôle Lecteur Sécurité dans Azure Active Directory, un **accès total** à Cloud App Security, vous pouvez l’ajouter manuellement à Cloud App Security et lui accorder un **accès total**. Son rôle est ainsi remplacé, et elle dispose des autorisations nécessaires dans Cloud App Security.

## <a name="add-additional-admins"></a>Ajouter des administrateurs supplémentaires

Vous pouvez ajouter des administrateurs à Cloud App Security sans ajouter d’utilisateurs aux rôles administratifs Azure Active Directory. Pour ajouter des administrateurs, procédez comme suit :

> [!IMPORTANT]
> Seuls les administrateurs généraux ou de sécurité peuvent accorder l’accès à Cloud App Security à d’autres utilisateurs.

1. Cliquez sur l’icône Paramètres roue dentée ![paramètres](media/settings-icon.png "Icône des paramètres") , puis sur **gérer l’accès administrateur**.

2. Cliquez sur le signe plus pour ajouter les administrateurs qui doivent avoir accès à Cloud App Security. Vous pouvez taper une adresse e-mail interne ou externe pour permettre aux administrateurs de votre organisation ou aux fournisseurs MSSP (Managed Security Service Provider) externes d’administrer vos alertes de sécurité.

    ![ajouter des administrateurs](media/add-admin.png)

3. Ensuite, cliquez sur la liste déroulante pour définir le type de rôle de l’administrateur, l' **administrateur général**, le **lecteur de sécurité**, l’administrateur de la **conformité**, l’administrateur de l' **application/** de l’instance, l’administrateur du **groupe d’utilisateurs**, l’administrateur général de l' **Cloud Discovery**ou l’administrateur du **rapport Cloud Discovery**. Si vous sélectionnez **administrateur d’application/d’instance**, sélectionnez l’application et l’instance de pour l’administrateur pour lesquelles des autorisations doivent être définies.

    >[!NOTE]
    > Tout administrateur dont l’accès est limité et qui tente d’accéder à une page restreinte ou d’effectuer une action restreinte reçoit une erreur indiquant qu’il ne dispose pas des autorisations nécessaires pour accéder à la page ou effectuer l’action.

4. Cliquez sur **Ajouter un administrateur**.

## <a name="admin-activity-auditing"></a>Audit des activités d’administration

Cloud App Security vous permet d’exporter un journal des activités de connexion administrateur et un audit des affichages d’un utilisateur spécifique ou des alertes effectuées dans le cadre d’une investigation.

Pour exporter un journal, procédez comme suit :

1. Dans la page **gérer l’accès aux administrateurs** , sélectionnez **Exporter les activités d’administration**.

1. Spécifiez l’intervalle de temps requis.

1. Cliquez sur **Exporter**.

## <a name="invite-external-admins"></a>Inviter des administrateurs externes

Cloud App Security vous permet d’inviter des fournisseurs de services de sécurité managés externes (MSSPs) en tant qu’administrateurs de votre portail Cloud App Security. Les utilisateurs externes peuvent maintenant être configurés en tant qu’administrateurs et être affectés à l’un des rôles disponibles dans Cloud App Security. Pour ajouter des utilisateurs externes, assurez-vous que Cloud App Security est activé sur le locataire source, puis fournissez une adresse de messagerie externe dans les étapes de la section [Ajouter des administrateurs supplémentaires](#add-additional-admins).

De plus, pour autoriser les fournisseurs MSSP à offrir des services sur plusieurs locataires de clients, les administrateurs disposant des droits d’accès sur plus d’un locataire peuvent facilement passer d’un locataire à l’autre au sein du portail. Une fois que vous avez les autorisations sur plusieurs locataires, cliquez sur l’icône utilisateur pour passer d’un locataire à l’autre. Vous verrez la liste des locataires pour lesquels vous avez des autorisations. Sélectionnez le locataire que vous voulez gérer.

![choisir un locataire](media/choose-tenant.png "choisir un locataire")

## <a name="next-steps"></a>Étapes suivantes  

> [!div class="nextstepaction"]
> [Configurer Cloud Discovery](set-up-cloud-discovery.md)
