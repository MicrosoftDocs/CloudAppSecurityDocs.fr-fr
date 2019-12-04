---
title: Importer des groupes d’utilisateurs à partir d’applications connectées dans Cloud App Security
description: Cet article fournit des instructions sur l’importation de groupes d’utilisateurs issus d’applications connectées vers Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/17/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 777e672436220642df6ea739c0f2e381487dd9ee
ms.sourcegitcommit: 7c93b6f93d2699d466b172590710ed01697bbdad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74720367"
---
# <a name="importing-user-groups-from-connected-apps"></a>Importation de groupes d’utilisateurs à partir d’applications connectées

*S’applique à : Microsoft Cloud App Security*

Quand vous connectez des applications à l’aide de connecteurs API, Microsoft Cloud App Security vous permet d’importer des groupes d’utilisateurs, par exemple à partir d’Office 365 et d’Azure Active Directory. Il existe deux types de groupes d’utilisateurs :

- Groupes automatiques  
Les groupes automatiques sont créés par défaut par Microsoft Cloud App Security. Par exemple, il existe un groupe d’utilisateurs automatique appelé **Externe** qui combine tous les utilisateurs de toutes les applications qui sont externes à votre organisation. Ces utilisateurs ont accès aux fichiers ou participaient aux activités dans votre client. Les groupes automatiques suivants existent dans Cloud App Security :

  - External
  - Administrateur Dropbox
  - Administrateur Office 365
  - Administrateur G Suite
  - Administrateur Box
  - Tous les profils standard et personnalisés Salesforce, par exemple Administrateur système Salesforce. Consultez la liste complète [ici](https://help.salesforce.com/articleView?id=standard_profiles.htm&language=en&type=0).

- Groupes importés  
Vous pouvez importer n’importe quel groupe à partir de vos applications connectées. Par exemple, vous pouvez importer des groupes d’utilisateurs d’Office 365 (Active Directory) et d’autres applications connectées. Ces groupes vous permettent de rechercher les menaces dans votre organisation en examinant un groupe spécifique et non l’intégralité de l’organisation ou un utilisateur spécifique.

  Voici des scénarios classiques qui font usage de groupes d’utilisateurs importés :

  - Connaître les documents que les membres des ressources humaines consultent
  - Vérifier si quelque chose d’inhabituel s’est produit dans le groupe de dirigeants
  - Savoir si un membre du groupe d’administration a effectué une activité hors des États-Unis

## <a name="how-to-import-user-groups"></a>Importer des groupes d’utilisateurs

1. Dans la barre de menus, cliquez sur l' ![icône](media/settings-icon.png "icône des paramètres") des paramètres icône des paramètres et sélectionnez **groupes d’utilisateurs**.
1. Cliquez sur **Importer le groupe d’utilisateurs**.

    ![Importer des groupes d’utilisateurs](media/user-groups-add.png)

1. Sélectionnez l’application à partir de laquelle importer le groupe d’utilisateurs. La liste des applications dépend des connecteurs d’application que vous avez déployés.
1. Sélectionnez le groupe à importer. La liste des groupes disponibles est une liste de tous les groupes d’utilisateurs existants dans l’application elle-même. Vous devez ajouter un nouveau groupe directement dans l’application elle-même. Ensuite, lorsque le groupe apparaît dans la liste, vous pouvez le sélectionner.
1. Selon la taille du groupe, l’importation peut durer jusqu’à une heure. Vous pouvez sélectionner l’option pour être averti par e-mail quand le processus d’importation est terminé.
1. Cliquez sur **Importer**. Après l’importation d’un groupe, Cloud App Security synchronise automatiquement les membres du groupe, comme Active Directory Connect.
1. Une fois l’importation terminée, vous pouvez cliquer sur un groupe spécifique dans la page **Groupes d’utilisateurs** pour afficher la liste de tous les membres du groupe. Cliquez sur un membre du groupe pour explorer plus en détail les informations d’un compte spécifique. Vous pouvez connaître les applications utilisées et consulter un récapitulatif du compte qui inclut des graphiques sur l’utilisateur et son activité.

L’importation de groupes vous permet de sélectionner ces groupes comme filtres quand vous examinez le **journal d’activité** et créez des stratégies.

> [!NOTE]
>
> - Il peut y avoir un bref délai jusqu’à ce que les groupes d’utilisateurs importés soient disponibles dans les filtres.
> - Seules les activités effectuées après l’importation d’un groupe d’utilisateurs sont marquées comme ayant été effectuées par un membre du groupe d’utilisateurs.
> - Après la synchronisation initiale, les groupes sont mis à jour toutes les heures.

Pour plus d’informations sur l’utilisation des filtres Groupe d’utilisateurs, consultez la page [Activités](activity-filters.md).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Configurer Cloud Discovery](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]
