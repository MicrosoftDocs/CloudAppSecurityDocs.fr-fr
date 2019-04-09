---
title: Gérer l’accès administrateur au portail Cloud App Security
description: Cet article explique comment définir l’accès au portail Cloud App Security pour vos administrateurs.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 04/04/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: b718edad-350c-4d90-b045-92529d701dc5
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 83e2adb5d0890c926843403a6bdf1d0087abb007
ms.sourcegitcommit: 28b3ab878b1fc403d2c3b617e989f711320530d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59233545"
---
# <a name="manage-admin-access"></a>Gérer l’accès administrateur

*S’applique à : Microsoft Cloud App Security*

Microsoft Cloud App Security prend en charge le contrôle d’accès basé sur les rôles. Cet article explique comment définir l’accès au portail Cloud App Security pour vos administrateurs. Pour plus d’informations sur l’affectation des rôles d’administrateur, consultez les articles pour [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles) et [Office 365](https://docs.microsoft.com/office365/admin/add-users/assign-admin-roles).

## <a name="office-365-and-azure-ad-roles-with-access-to-cloud-app-security"></a>Rôles Office 365 et Azure AD avec accès à Cloud App Security

Par défaut, les rôles d’administrateur Office 365 et [Azure Active Directory (Azure AD)](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles) suivants ont accès à Microsoft Cloud App Security :

- **Administrateur général et administrateur de sécurité :** Les administrateurs avec **Accès complet** disposent d’autorisations complètes dans Cloud App Security. Ils peuvent ajouter des administrateurs, ajouter des stratégies et des paramètres, charger des journaux et effectuer des actions de gouvernance.

- **Administrateur de conformité :** Dispose d’autorisations en lecture seule et peut gérer les alertes. Peut créer et modifier des stratégies de fichier, autoriser des actions de gouvernance de fichier et afficher tous les rapports intégrés sous Gestion des données. 

- **Lecteur Sécurité** : Dispose d’autorisations en lecture seule et peut gérer les alertes. Le Lecteur Sécurité ne peut pas effectuer les actions suivantes :

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

- **Administrateur d’application/d’instance :** Dispose des autorisations pour toutes les données dans Microsoft Cloud App Security qui portent exclusivement sur l’application spécifique ou l’instance d’une application sélectionnée. Par exemple, vous accordez à un utilisateur l’autorisation d’administrateur sur votre instance de Box European. L’administrateur verra uniquement les données qui sont liées à l’instance de Box European, qu’il s’agisse de fichiers, d’activités, de stratégies ou d’alertes :

  - Page des activités : seules les activités concernant l’application spécifique
  - Alertes : seules les alertes relatives à l’application spécifique
  - Stratégies : peut afficher toutes les stratégies et modifier ou créer uniquement les stratégies qui traitent exclusivement de l’application/instance
  - Page Comptes : seuls les comptes de l’application/instance spécifique
  - Autorisations d’application : seules les autorisations pour l’application/instance spécifique
  - Page des fichiers : seuls les fichiers de l’application/instance spécifique
  - Contrôle d’accès conditionnel aux applications : aucune autorisation
  - Activité Cloud Discovery : aucune autorisation
  - Extensions de sécurité : autorisations uniquement pour un jeton d’API avec des autorisations utilisateur
  - Actions de gouvernance : uniquement pour l’application/instance spécifique 

- **Administrateur de groupe utilisateur :** Dispose des autorisations pour toutes les données dans Microsoft Cloud App Security qui portent exclusivement sur le groupe spécifique sélectionné ici. Par exemple, si vous accordez à un utilisateur l’autorisation d’administrateur sur le groupe « Allemagne - tous les utilisateurs », l’administrateur peut visualiser et modifier les informations dans Microsoft Cloud App Security uniquement pour ce groupe d’utilisateurs :

  - Page des activités : seules les activités concernant les utilisateurs dans le groupe
  - Alertes : seules les alertes relatives aux utilisateurs dans le groupe
  - Stratégies : peut afficher toutes les stratégies et modifier ou créer uniquement les stratégies qui traitent exclusivement des utilisateurs dans le groupe
  - Page Comptes : seuls les comptes pour les utilisateurs spécifiques dans le groupe
  - Autorisations d’application : aucune autorisation
  - Page Fichiers : aucune autorisation
  - Contrôle d’accès conditionnel aux applications : aucune autorisation
  - Activité Cloud Discovery : aucune autorisation
  - Extensions de sécurité : autorisations uniquement pour un jeton d’API avec les utilisateurs dans le groupe
  - Actions de gouvernance : uniquement pour les utilisateurs spécifiques dans le groupe

- **Administrateur général de cloud Discovery :**  A l’autorisation d’afficher et de modifier l’ensemble des données et paramètres Cloud Discovery. L’administrateur Global Discovery a accès comme suit :

  - Paramètres - 
     -  Paramètres du système - Affichage uniquement
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

- **Administrateur de rapports cloud Discovery :** Dispose des autorisations pour afficher toutes les données dans Microsoft Cloud App Security qui concerne exclusivement les rapports Cloud Discovery spécifiques sélectionné. Par exemple, vous pouvez autoriser un utilisateur admin pour le rapport continu à partir de Windows Defender ATP. L’administrateur de découverte s’affiche uniquement les données de découverte du Cloud est lié à la source de données et au catalogue d’applications.
Cet administrateur n’a pas accès à la **activités** ou **fichiers** pages et un accès limité aux stratégies.

- **Lecteur global :** A un accès complet en lecture seule à tous les aspects de Microsoft Cloud App Security. Impossible de modifier des paramètres ou de prendre toutes les actions.
 
## <a name="override-admin-permissions"></a>Remplacer les autorisations d’administrateur

Si vous souhaitez remplacer une autorisation d’administrateur dans Azure Active Directory ou Office 365, vous pouvez le faire manuellement en ajoutant l’utilisateur à Cloud App Security et en lui affectant des autorisations.
Par exemple, pour affecter à Stéphanie, qui est titulaire du rôle Lecteur Sécurité dans Azure Active Directory, un **accès total** à Cloud App Security, vous pouvez l’ajouter manuellement à Cloud App Security et lui accorder un **accès total**. Son rôle est ainsi remplacé, et elle dispose des autorisations nécessaires dans Cloud App Security. 

## <a name="add-additional-admins"></a>Ajouter des administrateurs supplémentaires

Vous pouvez ajouter des administrateurs à Cloud App Security sans ajouter d’utilisateurs aux rôles administratifs Azure Active Directory. Pour ajouter des administrateurs, procédez comme suit :

   >[!IMPORTANT]
   > Seuls les administrateurs généraux ou de sécurité peuvent accorder l’accès à Cloud App Security à d’autres utilisateurs.


1. Cliquez sur l’icône des paramètres ![icône des paramètres](./media/settings-icon.png "icône des paramètres"), puis sur **Gérer l’accès administrateur**. 

2. Cliquez sur le signe plus pour ajouter les administrateurs qui doivent avoir accès à Cloud App Security. Vous pouvez taper une adresse e-mail interne ou externe pour permettre aux administrateurs de votre organisation ou aux fournisseurs MSSP (Managed Security Service Provider) externes d’administrer vos alertes de sécurité.
  
   ![ajouter des administrateurs](./media/add-admin.png)

3. Ensuite, cliquez sur la liste déroulante pour définir le type de rôle de l’administrateur, **Administrateur général**, **Lecteur Sécurité**, **Administrateur de la conformité** ou **Administrateur de l’application/instance**. Si vous sélectionnez **Administrateur de l’application/instance**, sélectionnez l’application et l’instance pour lesquelles l’administrateur doit avoir des autorisations.

     >[!NOTE]
      >Tout administrateur dont l’accès est limité et qui tente d’accéder à une page restreinte ou d’effectuer une action restreinte reçoit une erreur indiquant qu’il ne dispose pas des autorisations nécessaires pour accéder à la page ou effectuer l’action.

4. Cliquez sur **Ajouter un administrateur**.  

## <a name="invite-external-admins"></a>Inviter des administrateurs externes

Microsoft Cloud App Security vous permet d’inviter des fournisseurs MSSP (Managed Security Service Provider) comme administrateurs de votre portail Microsoft Cloud App Security. Les utilisateurs externes peuvent maintenant être configurés en tant qu’administrateurs et se voir attribuer les rôles disponibles dans Microsoft Cloud App Security. De plus, pour autoriser les fournisseurs MSSP à offrir des services sur plusieurs locataires de clients, les administrateurs disposant des droits d’accès sur plus d’un locataire peuvent facilement passer d’un locataire à l’autre au sein du portail. 

Une fois que vous avez les autorisations sur plusieurs locataires, cliquez sur l’icône utilisateur pour passer d’un locataire à l’autre. Vous verrez la liste des locataires pour lesquels vous avez des autorisations. Sélectionnez le locataire que vous voulez gérer.

![choisir le locataire](./media/choose-tenant.png "choisir le locataire")

## <a name="next-steps"></a>Étapes suivantes  
[Configurer Cloud Discovery](set-up-cloud-discovery.md)   
  
  
  
