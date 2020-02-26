---
title: Gérer l’accès administrateur au portail Cloud App Security
description: Cet article fournit des instructions sur la configuration de l’accès au portail Cloud App Security pour vos administrateurs.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 02/25/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: f36b3e09abdc8f10a1e3fa5b59b32101f13f1065
ms.sourcegitcommit: c5d288898630c949bab6538f59ae196ff9bbb909
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77599748"
---
# <a name="manage-admin-access"></a>Gérer l’accès administrateur

*S’applique à : Microsoft Cloud App Security*

Microsoft Cloud App Security prend en charge le contrôle d’accès basé sur les rôles. Cet article fournit des instructions sur la configuration de l’accès au portail Cloud App Security pour vos administrateurs. Pour plus d’informations sur l’attribution de rôles d’administrateur, consultez les articles pour [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles) et [Office 365](https://docs.microsoft.com/office365/admin/add-users/assign-admin-roles).

## <a name="office-365-and-azure-ad-roles-with-access-to-cloud-app-security"></a>Rôles Office 365 et Azure AD avec accès à Cloud App Security

Par défaut, les rôles d’administrateur Office 365 et [Azure Active Directory (Azure AD)](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles) suivants ont accès aux Cloud App Security :

- Administrateur **général et administrateur de sécurité :** Les administrateurs disposant d’un **accès total** disposent d’autorisations complètes dans Cloud App Security. Ils peuvent ajouter des administrateurs, ajouter des stratégies et des paramètres, charger des journaux et effectuer des actions de gouvernance.

- **Administrateur de conformité :** Possède des autorisations en lecture seule et peut gérer les alertes. Peut créer et modifier des stratégies de fichier, autoriser des actions de gouvernance de fichiers et afficher tous les rapports intégrés sous Gestion des données.

- **Administrateur des données de conformité :** Possède des autorisations en lecture seule, peut créer et modifier des stratégies de fichier, autoriser des actions de gouvernance de fichiers et afficher tous les rapports de découverte.

- **Opérateur de sécurité :** Possède des autorisations en lecture seule et peut gérer les alertes.

- **Lecteur de sécurité :** Possède des autorisations en lecture seule et peut gérer les alertes. Le lecteur de sécurité ne peut pas exécuter les actions suivantes :

  - Créer des stratégies ou modifier et changer des stratégies existantes
  - Effectuer des actions de gouvernance
  - Charger des journaux de découverte
  - Interdire ou approuver des applications tierces
  - Accéder à la page de paramètres de la plage d’adresses IP
  - Accéder aux pages contenant des paramètres
  - Accès et affichage des paramètres de découverte
  - Accès et affichage de la page connecteurs d’application
  - Accéder au journal de gouvernance
  - Accéder à la page Gérer des rapports d’instantanés
  - Accès et modification de l’agent SIEM

- **Lecteur global :** Dispose d’un accès complet en lecture seule à tous les aspects de Microsoft Cloud App Security. Impossible de modifier des paramètres ou d’effectuer des actions.

En outre, les Cloud App Security rôles d’administrateur spécifiques suivants peuvent être configurés dans le portail Cloud App Security :

- **Administrateur d’application/d’instance :** Dispose d’autorisations complètes ou en lecture seule pour toutes les données de Microsoft Cloud App Security qui traitent exclusivement de l’application ou de l’instance spécifique d’une application sélectionnée. Par exemple, vous accordez à l’utilisateur une autorisation d’administrateur sur votre instance de zone européenne. L’Administrateur verra uniquement les données relatives à l’instance Box Europe, qu’il s’agisse de fichiers, d’activités, de stratégies ou d’alertes :

  - Page activités-uniquement les activités relatives à l’application spécifique
  - Alertes : seules les alertes relatives à l’application spécifique
  - Stratégies : peut afficher toutes les stratégies et, si des autorisations complètes sont attribuées, modifier ou créer uniquement les stratégies qui traitent exclusivement avec l’application/l’instance
  - Comptes page uniquement comptes pour l’application/instance spécifique
  - Autorisations de l’application : autorisations uniquement pour l’application/instance spécifique
  - Fichiers page uniquement fichiers de l’application/instance spécifique
  - Contrôle d’application par accès conditionnel-aucune autorisation
  - Activité Cloud Discovery-aucune autorisation
  - Extensions de sécurité-autorisations uniquement pour le jeton d’API avec des autorisations utilisateur
  - Actions de gouvernance-uniquement pour l’application/instance spécifique

- **Administrateur du groupe d’utilisateurs :** Dispose d’autorisations complètes ou en lecture seule pour toutes les données de Microsoft Cloud App Security qui traitent exclusivement du groupe spécifique sélectionné ici. Par exemple, si vous accordez une autorisation d’administrateur d’utilisateur au groupe « Germany-tous les utilisateurs », l’administrateur peut afficher et modifier les informations dans Microsoft Cloud App Security uniquement pour ce groupe d’utilisateurs :

  - Page activités-uniquement les activités relatives aux utilisateurs du groupe
  - Alertes : seules les alertes relatives aux utilisateurs du groupe
  - Stratégies : peut afficher toutes les stratégies et, si des autorisations complètes sont attribuées, modifier ou créer uniquement les stratégies qui concernent exclusivement les utilisateurs du groupe.
  - Comptes de la page comptes uniquement pour les utilisateurs spécifiques dans le groupe
  - Autorisations d’application – aucune autorisation
  - Page fichiers-aucune autorisation
  - Contrôle d’application par accès conditionnel-aucune autorisation
  - Activité Cloud Discovery-aucune autorisation
  - Extensions de sécurité : autorisations uniquement pour le jeton d’API avec les utilisateurs du groupe
  - Actions de gouvernance : uniquement pour les utilisateurs spécifiques du groupe

- **Cloud Discovery administrateur général :**  A l’autorisation d’afficher et de modifier tous les paramètres et données de Cloud Discovery. L’administrateur de la découverte globale a accès comme suit :

  - Paramètres
    - Paramètres système-vue uniquement
    - Paramètres de Cloud Discovery-afficher et modifier tout (les autorisations d’anonymisation varient selon qu’elles ont été autorisées ou non lors de l’attribution de rôle)
  - Activité Cloud Discovery-autorisations complètes
  - Alertes-uniquement les alertes relatives aux données de Cloud Discovery
  - Stratégies : peut afficher toutes les stratégies et peut modifier ou créer uniquement des stratégies de Cloud Discovery
  - Page activités-aucune autorisation
  - Page comptes-aucune autorisation
  - Autorisations d’application – aucune autorisation
  - Page fichiers-aucune autorisation
  - Contrôle d’application par accès conditionnel-aucune autorisation
  - Extensions de sécurité-aucune autorisation
  - Actions de gouvernance : seules Cloud Discovery actions associées

- **Cloud Discovery l’administrateur du rapport :** Dispose des autorisations pour afficher toutes les données dans Microsoft Cloud App Security qui traitent exclusivement des rapports Cloud Discovery spécifiques sélectionnés. Par exemple, vous pouvez accorder une autorisation d’administrateur à un rapport continu à partir de Microsoft Defender ATP. L’administrateur de la découverte verra uniquement les données de Cloud Discovery relatives à cette source de données et au catalogue d’applications.
Cet administrateur n’aura pas accès aux pages des **activités** ou des **fichiers** et à un accès limité aux stratégies.

## <a name="override-admin-permissions"></a>Remplacer les autorisations d’administrateur

Si vous souhaitez remplacer l’autorisation d’un administrateur de Azure Active Directory ou Office 365, vous pouvez le faire en ajoutant manuellement l’utilisateur à Cloud App Security et en affectant les autorisations de l’utilisateur.
Par exemple, si vous souhaitez affecter à Stéphanie, qui est un lecteur de sécurité dans Azure Active Directory pour avoir un **accès total** dans Cloud App Security, vous pouvez l’ajouter manuellement à Cloud App Security et lui affecter un **accès complet** pour remplacer son rôle et lui accorder les autorisations nécessaires dans Cloud App Security.

## <a name="add-additional-admins"></a>Ajouter des administrateurs supplémentaires

Vous pouvez ajouter des administrateurs supplémentaires à Cloud App Security sans ajouter d’utilisateurs aux rôles d’administration Azure Active Directory. Pour ajouter des administrateurs supplémentaires, procédez comme suit :

> [!IMPORTANT]
> Seuls les administrateurs généraux ou les administrateurs de la sécurité peuvent accorder à d’autres utilisateurs l’accès à Cloud App Security.

1. Cliquez sur l’icône Paramètres roue dentée ![paramètres](media/settings-icon.png "icône Paramètres") , puis sur **gérer l’accès administrateur**.

2. Cliquez sur le signe plus pour ajouter les administrateurs qui doivent avoir accès à Cloud App Security. Vous pouvez entrer une adresse de messagerie interne ou externe pour permettre aux administrateurs de l’intérieur de votre organisation ou à des fournisseurs de services de sécurité managés (MSSPs) externes d’administrer vos alertes de sécurité.

    ![Ajouter des administrateurs](media/add-admin.png)

3. Ensuite, cliquez sur la liste déroulante pour définir le type de rôle de l’administrateur, **administrateur général**, **lecteur de sécurité**, **administrateur de conformité**ou **administrateur d’application/d’instance**. Si vous sélectionnez **administrateur d’application/d’instance**, sélectionnez l’application et l’instance de pour l’administrateur pour lesquelles des autorisations doivent être définies.

    >[!NOTE]
    >Tout administrateur dont l’accès est limité, qui tente d’accéder à une page restreinte ou d’effectuer une action restreinte, recevra une erreur indiquant qu’il n’a pas l’autorisation d’accéder à la page ou d’exécuter l’action.

4. Cliquez sur **Ajouter un administrateur**.

## <a name="admin-activity-auditing"></a>Audit des activités d’administration

Cloud App Security vous permet d’exporter un journal de toutes les activités d’administration, y compris l’audit d’un administrateur qui examine un utilisateur spécifique ou affiche des alertes spécifiques.

Pour exporter un journal, procédez comme suit :

1. Dans la page **gérer l’accès aux administrateurs** , sélectionnez **Exporter les activités d’administration**.

1. Spécifiez l’intervalle de temps requis.

1. Cliquez sur **Exporter**.

## <a name="invite-external-admins"></a>Inviter des administrateurs externes

Cloud App Security vous permet d’inviter des fournisseurs de services de sécurité managés externes (MSSPs) en tant qu’administrateurs de votre portail Cloud App Security. Les utilisateurs externes peuvent maintenant être configurés en tant qu’administrateurs et être affectés à l’un des rôles disponibles dans Cloud App Security. En outre, pour permettre à MSSPs de fournir des services à plusieurs locataires clients, les administrateurs disposant de droits d’accès à plusieurs locataires peuvent désormais facilement changer de locataires dans le portail.

Pour basculer entre les locataires, une fois que vous disposez des autorisations pour plusieurs locataires, cliquez sur l’icône utilisateur. Vous verrez une liste des locataires pour lesquels vous disposez d’autorisations. Sélectionnez le locataire que vous souhaitez gérer.

![choisir un locataire](media/choose-tenant.png "choisir un locataire")

## <a name="next-steps"></a>Étapes suivantes :  

> [!div class="nextstepaction"]
> [Configurer Cloud Discovery](set-up-cloud-discovery.md)
