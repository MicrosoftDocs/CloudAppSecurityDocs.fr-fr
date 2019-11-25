---
title: Visibilité sur les comptes d’application cloud – Cloud App Security | Microsoft Docs
description: Cet article fournit des informations sur la vérification des comptes à partir de vos applications connectées.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 7811f23b-6100-427f-93b1-44f5f81f6c76
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: e6559c68b3b958eb9a989153d5f1e4ec011fea49
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74460948"
---
# <a name="accounts"></a>Comptes

*S’applique à : Microsoft Cloud App Security*

Microsoft Cloud App Security vous donne une visibilité sur les comptes de vos applications connectées. Une fois connecté à une application à l’aide du connecteur d’applications, Cloud App Security lit les informations sur le compte qui sont associées aux applications connectées. La page Comptes vous permet d’examiner ces comptes, les autorisations, les groupes dont ils sont membres, leurs alias et les applications qu’ils utilisent. De plus, quand Cloud App Security détecte un nouveau compte qui n’a pas déjà été vu dans l’une des applications connectées (par exemple dans les activités ou le partage de fichiers), le compte est ajouté à la liste des comptes de cette application. Cela vous permet d’avoir une visibilité sur l’activité des utilisateurs externes interagissant avec vos applications cloud.

Les administrateurs peuvent rechercher les métadonnées ou l’activité d’un utilisateur spécifique. The **Users and accounts** page provides you with comprehensive details about the entities that are pulled from connected cloud applications. Elle fournit également l’historique d’activité de l’utilisateur et les alertes de sécurité liées à l’utilisateur.

[!INCLUDE [Handle personal data](../includes/gdpr-intro-sentence.md)]


La page **Utilisateurs et comptes** peut être filtrée pour vous permettre de trouver des comptes spécifiques et d’étudier plus en détail différents types de comptes ; par exemple, vous pouvez filtrer tous les comptes externes qui n’ont pas été consultés depuis l’année dernière. 

La page **Utilisateurs et comptes** vous permet d’examiner facilement certains points dans vos comptes, notamment les problèmes suivants :  

-   Vérifiez si certains comptes ont été inactifs dans un service particulier pendant une longue période (peut-être devez-vous révoquer la licence de cet utilisateur pour ce service)  
-   Vous pouvez filtrer la liste des utilisateurs avec des autorisations d’administrateur  

-   Vous pouvez rechercher des utilisateurs qui ne font plus partie de votre organisation, mais peuvent toujours disposer de comptes actifs  

-   Vous pouvez engager des actions de gouvernance sur les comptes, comme la suspension d’une application, ou accéder à la page des paramètres de compte. Pour obtenir la liste complète des actions de gouvernance, consultez le [journal de gouvernance](governance-actions.md).
    
-   Vous pouvez voir les comptes qui sont inclus dans chaque groupe d’utilisateurs  

-   Vous pouvez voir les applications qui sont consultées par chaque compte et les applications qui sont supprimées pour des comptes spécifiques
    

![écran des comptes](./media/accounts-page.png)

## <a name="users-and-accounts-filters"></a>Filtres d’utilisateurs et de comptes
Vous trouverez ci-dessous une liste des filtres de comptes qui peuvent être appliqués. La plupart des filtres prennent en charge plusieurs valeurs, ainsi que NOT, afin de vous fournir un outil puissant pour créer des stratégies.  
  
<!--- **Account name**: The account name is the primary alias of the user, but other identifiers from other Microsoft accounts (Office 365 and Azure Active Directory) such as proxy addresses, aliases, SID are supported and consolidated beneath the primary alias. -->

- **Affiliation** : l’affiliation est **interne** ou **externe**. Pour définir les utilisateurs et les comptes qui sont internes, sous **Paramètres**, veillez à définir la **plage d’adresses IP** de votre organisation interne. Dans le cas où le compte dispose d’autorisations d’administrateur, l’icône dans la table Comptes s’affiche avec l’ajout de la cravate rouge. ![icône d’administration des comptes](./media/accounts-admin-icon.png)

- **Application** : vous pouvez filtrer n’importe quelle application connectée à l’API utilisée par les comptes de votre organisation.

- **Domaine** : vous permet de filtrer des utilisateurs dans des domaines spécifiques.

- **Groupes**: vous permet de filtrer les membres des groupes d’utilisateurs dans Cloud App Security, à la fois les groupes d’utilisateurs intégrés et les groupes d’utilisateurs importés.

- **Instance** : vous permet de filtrer les membres d’une instance d’application spécifique. 

- **Dernière consultation** : le filtre **Dernière consultation** vous permet de rechercher des comptes qui sont sans mouvement et dont les utilisateurs n’ont effectué aucune activité depuis un certain temps.

- **Organisation** : vous permet de filtrer les membres de groupes d’organisation spécifiques définis dans vos applications connectées.

- **Afficher uniquement les administrateurs** : filtres pour les comptes et les utilisateurs qui sont des administrateurs.

- **État** : filtre basé sur l’état de compte utilisateur N/A, intermédiaire, actif, suspendu ou supprimé.

- **Type** : vous permet de filtrer sur l’utilisateur ou sur le type de compte.

- **Nom d’utilisateur** : vous permet de filtrer sur des utilisateurs spécifiques. 


## <a name="next-steps"></a>Étapes suivantes  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   

[!INCLUDE [Open support ticket](includes/support.md)]  
  
  
