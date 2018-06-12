---
title: Gérer l’accès administrateur au portail Cloud App Security | Microsoft Docs
description: Cette rubrique explique comment définir l’accès au portail Cloud App Security pour vos administrateurs.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/10/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: b718edad-350c-4d90-b045-92529d701dc5
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 6e9a2f9466352296caea57ee3219fa6a5151f1c8
ms.sourcegitcommit: 41fbc8e235befd240ad7a1eed52339cfafb5d906
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2018
ms.locfileid: "35251767"
---
*S’applique à : Microsoft Cloud App Security*


## <a name="managing-admin-access"></a>Gestion de l’accès d’administrateur

Microsoft Cloud App Security prend en charge le contrôle d’accès basé sur les rôles. Par défaut, les rôles d’administrateur Office 365 et Azure AD suivants ont accès à Microsoft Cloud App Security :

- Administrateur général et administrateur de sécurité : les administrateurs avec un **accès total** disposent d’autorisations complètes dans Cloud App Security pour ajouter des administrateurs, ajouter des stratégies et des paramètres, charger des journaux et effectuer des actions de gouvernance.

- Administrateur de conformité : dispose d’autorisations en lecture seule et peut gérer les alertes. Peut créer et modifier des stratégies de fichier, autoriser des actions de gouvernance de fichier et afficher tous les rapports intégrés sous Gestion des données. 

- Lecteur Sécurité : dispose d’autorisations en lecture seule et peut gérer les alertes. Le Lecteur Sécurité ne peut pas effectuer les actions suivantes :

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

- Administrateur d’application/d’instance : dispose des autorisations pour toutes les données dans Microsoft Cloud App Security qui portent exclusivement sur l’instance ou l’application spécifique d’une application sélectionnée ici. Par exemple, si vous accordez une autorisation d’administrateur utilisateur à votre instance encadré Européen, l’administrateur sera en mesure d’afficher uniquement les données relatives à cette instance d’application, qu’il s’agisse de fichiers, d’activités, de stratégies ou d’alertes, comme suit :

  - Page des activités : seules les activités concernant l’application spécifique
  - Alertes : seules les alertes relatives à l’application spécifique
  - Stratégies : peut afficher toutes les stratégies et modifier ou créer uniquement les stratégies qui traitent exclusivement de l’application/instance
  - Compte : seuls les comptes de l’application/instance spécifique
  - Autorisations d’application : seules les autorisations pour l’application/instance spécifique
  - Page des fichiers : seuls les fichiers à partir de l’application/instance spécifique
  - Contrôle d’accès conditionnel aux applications : aucune autorisation
  - Activité Cloud Discovery : aucune autorisation
  - Extensions de sécurité : autorisations uniquement pour un jeton d’API avec des autorisations utilisateur
  - Actions de gouvernance : uniquement pour l’application/instance spécifique 

- Administrateur de groupe : dispose des autorisations pour toutes les données dans Microsoft Cloud App Security qui portent exclusivement sur le groupe spécifique sélectionné ici. Par exemple, si vous donnez à un administrateur utilisateur l’autorisation sur le groupe « Allemagne - tous les utilisateurs », l’administrateur sera en mesure de visualiser et de modifier les informations dans Microsoft Cloud App Security uniquement pour ce groupe d’utilisateurs, comme suit :

  - Page des activités : seules les activités concernant les utilisateurs dans le groupe
  -     Alertes : seules les alertes relatives aux utilisateurs dans le groupe
  -     Stratégies : peut afficher toutes les stratégies et modifier ou créer uniquement les stratégies qui traitent exclusivement des utilisateurs dans le groupe
  -     Compte : seuls les comptes pour les utilisateurs spécifiques dans le groupe
  -     Autorisations d’application : aucune autorisation
  -     Page Fichiers : aucune autorisation
  -     Contrôle d’accès conditionnel aux applications : aucune autorisation
  -     Activité Cloud Discovery : aucune autorisation
  -     Extensions de sécurité : autorisations uniquement pour un jeton d’API avec les utilisateurs dans le groupe
  -     Actions de gouvernance : uniquement pour les utilisateurs spécifiques dans le groupe



Pour plus d’informations, consultez [Affectation des rôles d’administrateur dans Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-assign-admin-roles).

Vous pouvez également ajouter des administrateurs à Cloud App Security, sans ajouter d’utilisateurs aux rôles administratifs Azure Active Directory, en effectuant les étapes suivantes :

1. Cliquez sur la roue dentée des paramètres ![icône des paramètres](./media/settings-icon.png "icône des paramètres"), puis sur **Gérer les administrateurs**. 

2. Cliquez sur le signe plus pour ajouter les administrateurs qui doivent avoir accès à Cloud App Security.
  
  ![ajouter des administrateurs](./media/add-admin.png)
    
3. Ensuite, cliquez sur la liste déroulante pour définir le type de rôle de l’administrateur, **Administrateur général**, **Lecteur Sécurité**, **Administrateur de la conformité** ou **Administrateur de l’application/instance**. Si vous sélectionnez **Administrateur de l’application/instance**, sélectionnez l’application et l’instance pour lesquelles l’administrateur doit avoir des autorisations.

     >[!NOTE]
      >Tout administrateur dont l’accès est limité et qui tente d’accéder à une page restreinte ou d’effectuer une action restreinte reçoit une erreur indiquant qu’il ne dispose pas des autorisations nécessaires pour accéder à la page ou effectuer l’action.
4. Cliquez sur **Ajouter un administrateur**.  

   >[!NOTE]
    >Seuls les administrateurs généraux ou de sécurité peuvent accorder l’accès à Cloud App Security à d’autres utilisateurs.
  
**Pour remplacer les autorisations d’administrateur :**

Si vous souhaitez remplacer une autorisation d’administrateur dans Azure Active Directory ou Office 365, vous pouvez le faire manuellement en ajoutant l’utilisateur à Cloud App Security et en lui affectant des autorisations.
Par exemple, pour affecter à Stéphanie, qui est titulaire du rôle Lecteur Sécurité dans Azure Active Directory, un **accès total** à Cloud App Security, vous pouvez l’ajouter manuellement à Cloud App Security et lui accorder un **accès total**. Son rôle est ainsi remplacé, et elle dispose des autorisations désirées dans Cloud App Security. 


Pour ajouter des administrateurs à Cloud App Security :
1. Cliquez sur l’icône des paramètres ![icône des paramètres](./media/settings-icon.png "icône des paramètres"), puis sur **Gérer l’accès administrateur**. 

2. Ajoutez les administrateurs qui doivent avoir accès à Cloud App Security. Sélectionnez leur niveau d’accès et cliquez sur **Fermer**.

## <a name="see-also"></a>Voir aussi  
[Configurer Cloud Discovery](set-up-cloud-discovery.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  