---
title: Importer des groupes d’utilisateurs à partir d’applications connectées | Microsoft Docs
description: Cette rubrique fournit des instructions sur l’importation de vos groupes d’utilisateurs dans Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/9/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 87b831ef-5977-4df8-bed3-3ee54a8adbb5
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: d952746375c18730b92f7629ac4978c61ebfbfa9
ms.sourcegitcommit: c497253a7ab63973bb806607e5f15dece91640be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53123786"
---
*S’applique à : Microsoft Cloud App Security*
   
# <a name="import-user-groups"></a>Importer des groupes d’utilisateurs

Quand vous connectez des applications à l’aide de connecteurs API, Microsoft Cloud App Security vous permet d’importer des groupes d’utilisateurs, par exemple à partir d’Office 365 et d’Azure Active Directory.
Il existe deux types de groupes d’utilisateurs : 
- Groupes automatiques </br>Les groupes automatiques sont créés par défaut par Microsoft Cloud App Security. Par exemple, il existe un groupe d’utilisateurs automatique appelé **Externe** qui combine tous les utilisateurs de toutes les applications qui sont externes à votre organisation et ont accès aux fichiers ou participaient aux activités des utilisateurs dans votre client.
 Les groupes automatiques suivants existent dans Cloud App Security :
  - External
  - Administrateur Dropbox
  - Administrateur Office 365
  - Administrateur G Suite
  - Administrateur Box
  - Tous les profils standard et personnalisés Salesforce, par exemple Administrateur système Salesforce. Consultez la liste complète [ici](https://help.salesforce.com/articleView?id=standard_profiles.htm&language=en&type=0).

- Groupes importés</br>Vous pouvez importer n’importe quel groupe à partir de vos applications connectées. Par exemple, vous pouvez importer des groupes d’utilisateurs d’Office 365 (Active Directory) et d’autres applications connectées. Cela vous permet de rechercher les menaces dans votre organisation en examinant un groupe spécifique et non l’intégralité de l’organisation ou un utilisateur spécifique. 

L’importation de groupes d’utilisateurs peut être utile dans les scénarios suivants : vous pouvez identifier les documents qui sont consultés par le service des Ressources Humaines, ou vérifier si quelque chose d’inhabituel s’est produit dans le groupe des dirigeants ou si un membre du groupe des administrateurs a effectué une activité en dehors de France. Pour importer des groupes d’utilisateurs :

1. Dans la barre de menus, cliquez sur l’icône des paramètres ![icône des paramètres](./media/settings-icon.png "icône des paramètres") et sélectionnez **Groupes d’utilisateurs**.
2. Cliquez sur **Importer le groupe d’utilisateurs**.

   ![Importer des groupes d’utilisateurs](./media/user-groups-add.png)

3. Sélectionnez l’application à partir de laquelle importer le groupe d’utilisateurs. La liste des applications dépend des connecteurs d’application que vous avez déployés.
4. Sélectionnez le groupe à importer. La liste des groupes disponibles est une liste de tous les groupes d’utilisateurs existants dans l’application elle-même. Si vous souhaitez ajouter un nouveau groupe, vous devez le faire directement dans l’application elle-même, puis le sélectionner quand il apparaît ici.
5. Selon la taille du groupe, l’importation peut durer jusqu’à une heure. Vous pouvez sélectionner l’option pour être averti par e-mail quand le processus d’importation est terminé.
6. Cliquez sur **Importer**. Après l’importation d’un groupe, Cloud App Security synchronise automatiquement les membres du groupe, comme Active Directory Connect.
7. Une fois l’importation terminée, vous pouvez cliquer sur un groupe spécifique dans la page **Groupes d’utilisateurs** pour afficher la liste de tous les membres du groupe. Vous pouvez également cliquer sur n’importe quel membre du groupe pour examiner de plus près les détails d’un compte spécifique et afficher les applications utilisées ainsi qu’un résumé du compte, dont les graphiques de l’utilisateur et de son activité.

L’importation de groupes vous permet de sélectionner ces groupes comme filtres quand vous examinez le **journal d’activité** et créez des stratégies. 

> [!NOTE]
> - Seules les activités effectuées après l’importation d’un groupe d’utilisateurs sont marquées comme ayant été effectuées par un membre du groupe d’utilisateurs.
> - Après la synchronisation initiale, les groupes sont mis à jour toutes les heures.

Pour plus d’informations sur l’utilisation des filtres Groupe d’utilisateurs, consultez la page [Activités](activity-filters.md).


    
## <a name="see-also"></a>Voir aussi  
[Configurer Cloud Discovery](set-up-cloud-discovery.md)   

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)  
  
  