---
title: "Gérer l’accès administrateur au portail Cloud App Security | Microsoft Docs"
description: "Cette rubrique explique comment définir l’accès au portail Cloud App Security pour vos administrateurs."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/10/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: b718edad-350c-4d90-b045-92529d701dc5
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: f4d336b48dc7f3655a60d64ec4fe7e066db7f438
ms.sourcegitcommit: 2f4474084c7e07ac4853945ab5aa1ea78950675d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2017
---
## <a name="managing-admin-access"></a>Gestion de l’accès d’administrateur

Cloud App Security prend en charge le contrôle d’accès basé sur les rôles. Par défaut, les rôles d’administrateur Office 365 et Azure AD suivants ont accès à Cloud App Security :

- Administrateur général et administrateur de sécurité : les administrateurs ont un **accès total**, c’est-à-dire qu’ils disposent d’autorisations complètes dans Cloud App Security pour ajouter des administrateurs, ajouter des stratégies et des paramètres, charger des journaux et effectuer des actions de gouvernance.

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

Pour plus d’informations, consultez [Affectation des rôles d’administrateur dans Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-assign-admin-roles).

Vous pouvez également ajouter des administrateurs à Cloud App Security, sans ajouter d’utilisateurs aux rôles administratifs Azure Active Directory, en effectuant les opérations suivantes :

1. Cliquez sur l’icône des paramètres ![icône des paramètres](./media/settings-icon.png "icône des paramètres"), puis sur **Gérer l’accès administrateur**. 

2. Ajoutez les administrateurs qui doivent avoir accès à Cloud App Security.
  
      
3. Ensuite, cliquez sur la liste déroulante pour définir le type d’accès accordé à l’administrateur : **Accès total** ou **Lecture seule et gestion des alertes**.

     >[!NOTE]
      >Tout administrateur dont l’accès est limité à **Lecture seule et gestion des alertes** qui tente d’accéder à une page restreinte ou d’effectuer une action restreinte reçoit une erreur indiquant qu’il ne dispose pas des autorisations nécessaires pour accéder à la page ou effectuer l’action.

   ![gérer l’accès administrateur](./media/manage-admin-access.png "gérer l’accès administrateur")  

4. Cliquez sur **Fermer**.  

   >[!NOTE]
    >Seuls les administrateurs généraux ou de sécurité peuvent accorder l’accès à Cloud App Security à d’autres utilisateurs.
  
**Pour remplacer les autorisations d’administrateur :**

Si vous souhaitez remplacer une autorisation d’administrateur dans Azure Active Directory ou Office 365, vous pouvez le faire manuellement en ajoutant l’utilisateur à Cloud App Security et en lui affectant des autorisations.
Par exemple, pour affecter à Stéphanie, qui est titulaire du rôle Lecteur Sécurité dans Azure Active Directory, un **accès total** à Cloud App Security, vous pouvez l’ajouter manuellement à Cloud App Security et lui accorder un **accès total**. Son rôle est ainsi remplacé, et elle dispose des autorisations désirées dans Cloud App Security. 


Pour ajouter des administrateurs à Cloud App Security :
1. Cliquez sur l’icône des paramètres ![icône des paramètres](./media/settings-icon.png "icône des paramètres"), puis sur **Gérer l’accès administrateur**. 

2. Ajoutez les administrateurs qui doivent avoir accès à Cloud App Security, sélectionnez leur niveau d’accès, puis cliquez sur **Fermer**.



## <a name="see-also"></a>Voir aussi  
[Configurer Cloud Discovery](set-up-cloud-discovery.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  