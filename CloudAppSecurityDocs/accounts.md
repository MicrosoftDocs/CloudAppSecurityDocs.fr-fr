---
title: "Visibilité sur les comptes d’application cloud | Microsoft Docs"
description: Dans cette rubrique
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/23/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 7811f23b-6100-427f-93b1-44f5f81f6c76
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 5d5ccc55fe0d9c3fea93446daebfcbd5bbed8c8d
ms.sourcegitcommit: fd3b6c04cec30f7c9300cc02d29d562d17bf43ea
translationtype: HT
---
# <a name="accounts"></a>Comptes
Cloud App Security vous donne une visibilité sur tous les comptes de vos applications connectées. Une fois connecté à une application à l’aide du connecteur d’applications, Cloud App Security analyse tous les comptes associés aux applications. La page Comptes vous permet d’examiner ces comptes, les groupes dont ils sont membres, leurs alias et les applications qu’ils utilisent. 


Le journal **Comptes** peut être filtré pour vous permettre de trouver des comptes spécifiques et d’étudier plus en détail différents types de comptes ; par exemple, vous pouvez filtrer tous les comptes externes qui n’ont pas été consultés depuis l’année dernière. Vous pouvez créer des stratégies basées sur les comptes, puis définir les alertes que vous souhaitez recevoir pour y réagir. 

La page **Comptes** vous permet d’examiner facilement certains points dans vos comptes, notamment les suivants :  

-   Vérifiez si certains comptes ont été inactifs dans un service particulier pendant une longue période (peut-être devez-vous révoquer la licence de cet utilisateur pour ce service)  
-   Vous pouvez filtrer la liste des utilisateurs avec des autorisations d’administrateur  

-   Vous pouvez afficher les comptes qui sont actifs mais appartiennent à des utilisateurs qui ne font plus partie de votre organisation  

-   Vous pouvez révoquer l’autorisation d’un utilisateur sur une application spécifique (en fonction de l’application) ou exiger d’un utilisateur spécifique qu’il effectue une authentification Multi-Factor Authentication
    
-   Vous pouvez voir les comptes qui sont inclus dans chaque groupe d’utilisateurs  

-   Vous pouvez voir les applications qui sont consultées par chaque compte et les applications qui sont supprimées pour des comptes spécifiques
    
-   Vous pouvez également analyser plus en détail le compte de l’utilisateur et sélectionner les actions de gouvernance pertinentes, telles que **Suspendre l’utilisateur** ou **Supprimer les collaborations de l’utilisateur**. Si l’utilisateur a été importé depuis Azure Active Directory, vous pouvez également cliquer sur **Paramètres du compte Azure AD** pour accéder facilement aux fonctionnalités d’administration avancée de l’utilisateur, comme l’administration du groupe, Multi-Factor Authentication, l’obtention d’informations sur les connexions de l’utilisateur et la possibilité de bloquer la connexion.

![écran des comptes](./media/accounts-page.png)

## <a name="account-filters"></a>Filtres de comptes
Vous trouverez ci-dessous une liste des filtres de comptes qui peuvent être appliqués. La plupart des filtres prennent en charge plusieurs valeurs, ainsi que NOT, afin de vous fournir un outil très puissant pour créer des stratégies.  
  
- **Nom du compte** : le nom du compte est l’alias principal de l’utilisateur, mais les autres identificateurs d’autres comptes Microsoft (Office 365 et Azure Active Directory) tels que des adresses proxy, des alias, des SID, sont pris en charge et consolidés sous l’alias principal.

- **Affiliation** : l’affiliation est **interne** ou **externe**. Pour définir les utilisateurs et les comptes qui sont internes, sous **Paramètres**, veillez à définir la **plage d’adresses IP** de votre organisation interne. Dans le cas où le compte dispose d’autorisations d’administrateur, l’icône dans la table Comptes s’affiche avec l’ajout de la cravate rouge ![icône d’administration des comptes](./media/accounts-admin-icon.png).

- **Application** : vous pouvez filtrer n’importe quelle application connectée à l’API utilisée par les comptes de votre organisation.

- **Domaine** : vous permet de filtrer des utilisateurs dans des domaines spécifiques.

- **Dernière consultation** : le filtre **Dernière consultation** vous permet de rechercher des comptes qui sont sans mouvement et dont les utilisateurs n’ont effectué aucune activité depuis un certain temps.

- **Organisation/Service** : vous permet de filtrer les membres de certains groupes d’organisation Azure Active Directory ou Office 365.

- **Groupe d’utilisateurs** : vous permet de filtrer les membres des groupes d’utilisateurs dans Cloud App Security, à la fois les groupes d’utilisateurs intégrés et les groupes d’utilisateurs importés.


## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  