---
title: Examiner des applications OAuth à risque – Cloud App Security | Microsoft Docs
description: Cet article fournit des informations sur la façon d’examiner des applications OAuth à risque dans Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 3/17/2019
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 4118681e-362f-4b10-aa08-39691aa7800a
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 664e2ea3e6ce0414d3d55ca18a89e9bf9d889d94
ms.sourcegitcommit: fe4cd2174f6dc83811a2d484f079e8dfbac5d082
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58476967"
---
# <a name="investigate-risky-oauth-apps"></a>Examiner des applications OAuth à risque

*S’applique à : Microsoft Cloud App Security*

OAuth est un standard ouvert pour l’authentification basée sur un jeton et sur une autorisation. OAuth permet à des services tiers d’utiliser les informations de compte d’un utilisateur sans exposer le mot de passe d’utilisateur. OAuth fait Office d’intermédiaire pour le compte de l’utilisateur et fournit le service avec un jeton d’accès qui autorise le partage d’informations de compte spécifiques.

Les applications tierces installées par des utilisateurs professionnels dans votre organisation ont souvent besoin d’une autorisation pour pouvoir accéder aux informations et données utilisateur et se connecter au nom de l’utilisateur à d’autres applications cloud. Lorsque les utilisateurs installent ces applications, ils cliquent souvent sur **Accepter** sans examiner attentivement les détails du message d’invite, notamment concernant l’octroi d’autorisations à l’application. Accepter les autorisations application tierce est un risque de sécurité potentiel pour votre organisation. Par conséquent, Microsoft Cloud App Security vous offre la possibilité d’analyser et de surveiller les autorisations données à l’application par vos utilisateurs. Cet article vise à aider à examiner les applications OAuth dans votre organisation et à vous concentrer sur les applications plus susceptibles d’être suspectes. 

Il est recommandé d’examiner les applications en utilisant les capacités et les informations fournies dans le portail Cloud App Security pour éliminer par filtrage les applications présentant un faible risque et de vous concentrer sur les applications suspectes. 

## <a name="how-to-investigate"></a>Procédure d’examen 

1.  Dans le portail, accédez à **Investigate**, puis **Applications OAuth**. Nous vous recommandons d’effectuer une requête à l’aide de l’un des filtres suivants : 
    - Sélectionnez un **niveau d’autorisation** de gravité élevée et une **utilisation communautaire** pas courante. Ce filtre vous aide à vous concentrer sur les applications à risque potentiel élevé pour lesquelles les utilisateurs peuvent avoir sous-estimé le risque. 
    - Sous **Autorisations**, sélectionnez toutes les options qui présentent particulièrement des risques dans un contexte spécifique. Vous pouvez notamment sélectionner tous les filtres qui fournissent des autorisations d’accès aux e-mails, par exemple **Accès total à toutes les boîtes aux lettres**, puis passer en revue la liste des applications pour vérifier qu’il s’agit bien d’applications qui ont vraiment besoin d’un accès aux e-mails. Cela peut faciliter l’investigation dans un contexte spécifique et la recherche d’applications qui semblent légitimes, mais contiennent des autorisations inutiles. Ces applications sont plus susceptibles de présenter des risques. 
    ![Application OAuth à risque](./media/risky-oauth1.png) 
    - Utilisez la **requête** qui vous permet de voir les **applications autorisées par des utilisateurs externes**. Ce filtre vous aide à identifier les applications qui peuvent ne pas être conformes aux normes de sécurité de votre entreprise. 
2.  Après les avoir filtrées, vous pouvez vous concentrer sur les applications dans les requêtes qui semblent légitimes, mais peuvent en réalité présenter des risques, notamment : 
    - Applications avec un faible nombre d’**Autorisée par**. Si vous vous concentrez sur ces applications, vous pouvez rechercher les applications à risque qui ont été autorisées par un utilisateur compromis. 
    - Applications avec des autorisations qui ne répondent pas à l’objectif de l’application, par exemple une application d’horloge avec un accès complet à toutes les boîtes aux lettres. 
    - Cliquez sur chaque application pour ouvrir le tiroir des applications et vérifier si l’application a un nom, un éditeur ou un site web suspect.  
    - Examinez la liste des applications et ciblez celles qui ont une date sous **Dernière autorisation** qui n’est pas récente. Ces applications peuvent ne plus être nécessaires. 
    ![Application OAuth à risque](./media/risky-oauth2.png) 
 
3. Cliquez sur l’application pour ouvrir le tiroir des applications et sur le lien situé sous **Activités associées**. Cette opération ouvre la page Journal d’activité, filtrée pour les activités effectuées par l’application. N’oubliez pas que certaines applications effectuent des activités qui sont inscrites comme ayant été effectuées par un utilisateur. Ces activités sont automatiquement filtrées dans les résultats dans le journal d’activité. Pour une investigation poussée avec le journal d’activité, consultez [Journal d’activité](activity-filters.md). 
4. Si une application semble suspecte, nous vous recommandons d’investiguer son nom et son éditeur dans les différents App Stores. Concentrez-vous sur les applications suivantes, qui peuvent être suspectes : 
    - Applications avec un faible nombre de téléchargements.
    - Applications avec une évaluation médiocre, un faible score ou des commentaires négatifs.
    - Applications avec un éditeur ou un site web suspect.
    - Applications avec une date de dernière mise à jour ancienne. Cela peut indiquer une application qui n’est plus prise en charge. 
    - Applications avec des autorisations sans intérêt. Cela peut indiquer qu’une application est à risque. 
5. Si l’application est toujours suspecte, vous pouvez rechercher son nom, son éditeur et son URL en ligne. 


 
## <a name="next-steps"></a>Étapes suivantes
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md) 

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/) 
 
