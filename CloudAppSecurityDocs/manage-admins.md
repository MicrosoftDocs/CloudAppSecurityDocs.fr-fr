---
title: Gérer l’accès administrateur au portail Cloud App Security
description: Cet article explique comment définir l’accès au portail Cloud App Security pour vos administrateurs.
ms.date: 01/11/2021
ms.topic: how-to
ms.openlocfilehash: a9ab36e788d74493059187bc043d701283b1969f
ms.sourcegitcommit: 7fc4d916a43d188b1aa4e3cee2e8bd1de230d135
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98206505"
---
# <a name="manage-admin-access"></a>Gérer l’accès administrateur

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Microsoft Cloud App Security prend en charge le contrôle d’accès basé sur les rôles. Cet article explique comment définir l’accès au portail Cloud App Security pour vos administrateurs. Pour plus d’informations sur l’attribution de rôles d’administrateur, consultez les articles pour [Azure Active Directory](/azure/active-directory/active-directory-assign-admin-roles) et [Office 365](/office365/admin/add-users/assign-admin-roles).

## <a name="office-365-and-azure-ad-roles-with-access-to-cloud-app-security"></a>Rôles Office 365 et Azure AD avec accès à Cloud App Security

Par défaut, les rôles d’administrateur Office 365 et [Azure Active Directory (Azure AD)](/azure/active-directory/users-groups-roles/directory-assign-admin-roles) suivants ont accès aux Cloud App Security :

- Administrateur **général et administrateur de sécurité**: les administrateurs disposant d’un **accès complet** disposent d’autorisations complètes dans Cloud App Security. Ils peuvent ajouter des administrateurs, ajouter des stratégies et des paramètres, charger des journaux et effectuer des actions de gouvernance.

- **Administrateur de conformité**: dispose d’autorisations en lecture seule et peut gérer les alertes. Impossible d’accéder aux recommandations de sécurité pour les plateformes Cloud. Peut créer et modifier des stratégies de fichier, autoriser des actions de gouvernance de fichier et afficher tous les rapports intégrés sous Gestion des données.

- **Administrateur des données de conformité**: dispose d’autorisations en lecture seule, peut créer et modifier des stratégies de fichier, autoriser des actions de gouvernance de fichiers et afficher tous les rapports de découverte. Impossible d’accéder aux recommandations de sécurité pour les plateformes Cloud.

- **Opérateur de sécurité et lecteur de sécurité**: disposent d’autorisations en lecture seule et peuvent gérer les alertes. Ces administrateurs ne sont pas autorisés à exécuter les actions suivantes :

  - Créer des stratégies ou modifier et changer des stratégies existantes
  - Effectuer des actions de gouvernance
  - Charger des journaux de découverte
  - Interdire ou approuver des applications tierces
  - Accéder à la page de paramètres de la plage d’adresses IP
  - Accès et affichage des pages de paramètres système
  - Accéder aux paramètres de découverte
  - Accéder à la page de connecteurs d’application
  - Accéder au journal de gouvernance
  - Accéder à la page Gérer des rapports d’instantanés
  - Accès et modification de l’agent SIEM

- **Lecteur global**: dispose d’un accès complet en lecture seule à tous les aspects de Cloud App Security. Impossible de modifier des paramètres ou d’effectuer des actions.

> [!NOTE]
> Les rôles Office 365 et Azure AD ne sont pas répertoriés dans la page **gérer l’accès administrateur** .

## <a name="built-in-cloud-app-security-admin-roles"></a>Rôles d’administrateur Cloud App Security intégrés

Les Cloud App Security rôles d’administrateur spécifiques suivants peuvent être configurés dans le portail Cloud App Security :

- **Administrateur d’application/d’instance**: dispose d’autorisations complètes ou en lecture seule pour toutes les données de Cloud App Security qui traitent exclusivement de l’application ou de l’instance spécifique d’une application sélectionnée. Par exemple, vous accordez à un utilisateur l’autorisation d’administrateur sur votre instance de Box European. L’administrateur verra uniquement les données qui sont liées à l’instance de Box European, qu’il s’agisse de fichiers, d’activités, de stratégies ou d’alertes :

  - Page des activités : seules les activités concernant l’application spécifique
  - Alertes : seules les alertes relatives à l’application spécifique
  - Stratégies : peut afficher toutes les stratégies et, si des autorisations complètes sont attribuées, modifier ou créer uniquement les stratégies qui traitent exclusivement avec l’application/l’instance
  - Page Comptes : seuls les comptes de l’application/instance spécifique
  - Autorisations d’application : seules les autorisations pour l’application/instance spécifique
  - Page des fichiers : seuls les fichiers de l’application/instance spécifique
  - Contrôle d’accès conditionnel aux applications : aucune autorisation
  - Activité Cloud Discovery : aucune autorisation
  - Extensions de sécurité : autorisations uniquement pour le jeton d’API avec des autorisations utilisateur
  - Actions de gouvernance : uniquement pour l’application/instance spécifique
  - Recommandations de sécurité pour les plateformes Cloud-aucune autorisation

- **Administrateur du groupe d’utilisateurs**: dispose d’autorisations complètes ou en lecture seule pour toutes les données de Cloud App Security qui traitent exclusivement des groupes spécifiques qui leur sont affectés. Par exemple, si vous attribuez des autorisations d’administrateur d’utilisateur au groupe « Germany-tous les utilisateurs », l’administrateur peut afficher et modifier les informations dans Cloud App Security uniquement pour ce groupe d’utilisateurs. L’administrateur du groupe d’utilisateurs a l’accès suivant :

  - Page des activités : seules les activités concernant les utilisateurs dans le groupe
  - Alertes : seules les alertes relatives aux utilisateurs dans le groupe
  - Stratégies : peut afficher toutes les stratégies et, si des autorisations complètes sont attribuées, modifier ou créer uniquement les stratégies qui concernent exclusivement les utilisateurs du groupe.
  - Page Comptes : seuls les comptes pour les utilisateurs spécifiques dans le groupe
  - Autorisations d’application : aucune autorisation
  - Page Fichiers : aucune autorisation
  - Contrôle d’accès conditionnel aux applications : aucune autorisation
  - Activité Cloud Discovery : aucune autorisation
  - Extensions de sécurité : autorisations uniquement pour le jeton d’API avec les utilisateurs du groupe
  - Actions de gouvernance : uniquement pour les utilisateurs spécifiques dans le groupe
  - Recommandations de sécurité pour les plateformes Cloud-aucune autorisation

    > [!NOTE]
    >
    > - Pour affecter des groupes aux administrateurs de groupe d’utilisateurs, vous devez d’abord [importer des groupes d’utilisateurs](user-groups.md) à partir d’applications connectées.
    > - Vous pouvez uniquement affecter des autorisations Admins du groupe d’utilisateurs aux groupes de Azure AD importés.

- **Cloud Discovery administrateur général**: a l’autorisation d’afficher et de modifier tous les paramètres et données Cloud Discovery. L’administrateur de la découverte globale a l’accès suivant :

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
  - Extensions de sécurité-création et suppression de leurs propres jetons d’API
  - Actions liées à la gouvernance - Cloud Discovery uniquement
  - Recommandations de sécurité pour les plateformes Cloud-aucune autorisation

- **Cloud Discovery administrateur de rapports**: dispose des autorisations pour afficher toutes les données dans Cloud App Security qui traitent exclusivement des rapports d’Cloud Discovery spécifiques sélectionnés. Par exemple, vous pouvez accorder à quelqu’un d’administrateur le rapport continu à partir de Microsoft Defender pour point de terminaison. L’administrateur de la découverte verra uniquement les données de Cloud Discovery relatives à cette source de données et au catalogue d’applications. Cet administrateur n’aura pas accès aux pages des **activités**, des **fichiers** ou des **recommandations de sécurité** et un accès limité aux stratégies.

> [!NOTE]
> Les rôles d’administrateur de Cloud App Security intégrés fournissent uniquement des autorisations d’accès à Cloud App Security.

## <a name="override-admin-permissions"></a>Remplacer les autorisations d’administrateur

Si vous souhaitez remplacer une autorisation d’administrateur dans Azure Active Directory ou Office 365, vous pouvez le faire manuellement en ajoutant l’utilisateur à Cloud App Security et en lui affectant des autorisations. Par exemple, pour affecter à Stéphanie, qui est titulaire du rôle Lecteur Sécurité dans Azure Active Directory, un **accès total** à Cloud App Security, vous pouvez l’ajouter manuellement à Cloud App Security et lui accorder un **accès total**. Son rôle est ainsi remplacé, et elle dispose des autorisations nécessaires dans Cloud App Security.

## <a name="add-additional-admins"></a>Ajouter des administrateurs supplémentaires

Vous pouvez ajouter des administrateurs à Cloud App Security sans ajouter d’utilisateurs aux rôles administratifs Azure Active Directory. Pour ajouter des administrateurs, procédez comme suit :

> [!IMPORTANT]
> Seuls les administrateurs généraux ou de sécurité peuvent accorder l’accès à Cloud App Security à d’autres utilisateurs.

1. Cliquez sur l’icône Paramètres roue dentée ![paramètres](media/settings-icon.png "Icône des paramètres") , puis sur **gérer l’accès administrateur**.

2. Cliquez sur le signe plus pour ajouter les administrateurs qui doivent avoir accès à Cloud App Security. Vous pouvez taper une adresse e-mail interne ou externe pour permettre aux administrateurs de votre organisation ou aux fournisseurs MSSP (Managed Security Service Provider) externes d’administrer vos alertes de sécurité.

    ![ajouter des administrateurs](media/add-admin.png)

3. Ensuite, cliquez sur la liste déroulante pour définir le type de rôle de l’administrateur, l' **administrateur général**, le **lecteur de sécurité**, l’administrateur de la **conformité**, l’administrateur de l' **application/** de l’instance, l’administrateur du **groupe d’utilisateurs**, l’administrateur général de l' **Cloud Discovery** ou l’administrateur du **rapport Cloud Discovery**. Si vous sélectionnez **administrateur d’application/d’instance**, sélectionnez l’application et l’instance de pour l’administrateur pour lesquelles des autorisations doivent être définies.

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
> [Configuration de Cloud Discovery](set-up-cloud-discovery.md)
