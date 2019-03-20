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
ms.openlocfilehash: 77b33d524e3a88d49c4dd2bcd71bc31c0fa26250
ms.sourcegitcommit: 57bad4dc9b28326c93ee480d308d52ea23c42089
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58163652"
---
# <a name="investigate-risky-oauth-apps"></a>Examiner des applications OAuth à risque

*S’applique à : Microsoft Cloud App Security*

OAuth est un standard ouvert pour l’authentification basée sur un jeton et sur une autorisation. OAuth permet à des services tiers d’utiliser les informations de compte d’un utilisateur sans exposer le mot de passe d’utilisateur. OAuth fait Office d’intermédiaire pour le compte de l’utilisateur et fournit le service avec un jeton d’accès qui autorise le partage d’informations de compte spécifiques.

Les applications tierces installées par des utilisateurs professionnels dans votre organisation ont souvent besoin d’une autorisation pour pouvoir accéder aux informations et données utilisateur et se connecter au nom de l’utilisateur à d’autres applications cloud. Lorsque les utilisateurs installent ces applications, ils cliquent souvent sur **Accepter** sans examiner attentivement les détails du message d’invite, notamment concernant l’octroi d’autorisations à l’application.

Accepter les autorisations application tierce est un risque de sécurité potentiel pour votre organisation. Par conséquent, Microsoft Cloud App Security vous offre la possibilité d’analyser et de surveiller les autorisations données à l’application par vos utilisateurs. Cet article vise à aider à examiner les applications OAuth dans votre organisation et à vous concentrer sur les applications plus susceptibles d’être suspectes. 

Il est recommandé d’examiner les applications en utilisant les capacités et les informations fournies dans le portail Cloud App Security pour éliminer par filtrage les applications présentant un faible risque et de vous concentrer sur les applications suspectes. 

## <a name="how-to-investigate"></a>Procédure d’examen 

1.  Toutes les requêtes d’applications OAuth connectées à l’aide des filtres du portail. Les requêtes et les filtres recommandés sont les suivants : 
    1. Niveau d’autorisation élevé et utilisation communautaire pas courante. Ce filtre vous aide à vous concentrer sur une application à risque potentiel élevé pour laquelle l’utilisateur a probablement mal compris le risque. 
    2. Autorisations à risque spécifiques liées à un type spécifique d’applications (par exemple, les applications avec un accès complet à toutes les boîtes aux lettres). Ce filtre vous aide à examiner dans un contexte spécifique et, par là, à rechercher des applications qui semblent légitimes, mais contiennent des autorisations non pertinentes. Ces applications sont plus susceptibles d’être malveillantes. 
    3. Applications autorisées par des utilisateurs externes. Ce filtre vous aide à identifier les applications qui peuvent ne pas être conformes aux standards de sécurité de votre entreprise. 
2.  Concentrez-vous sur les applications suivantes, qui peuvent être suspectes : 
    1. Applications avec un faible nombre de « Autorisée par ». Vous concentrer sur ces applications peut vous aider à identifier des applications malveillantes qui ont été autorisées par un utilisateur compromis. 
    2. Applications avec des autorisations qui ne répondent pas à l’objectif de l’application (par exemple, une application d’horloge avec un accès complet à toutes les boîtes aux lettres). Vous concentrer sur ces applications peut vous aider à identifier des applications qui semblent légitimes, mais sont en fait malveillantes. 
    3. Applications avec un nom, un serveur de publication ou un site web suspects. Vous concentrer sur ces applications peut vous aider à identifier rapidement des applications suspectes. 
    4. Applications avec une « dernière autorisation » ancienne. Vous concentrer sur ces applications peut vous aider à identifier des applications qui ne sont plus nécessaires. 
3. Utilisez le lien des activités connexes et affichez à la page du journal d'activité les activités effectuées par l’application. Notez qu’un filtre des activités pour lesquelles l’utilisateur correspond au nom de l’application sera automatiquement créé. Toutefois, certaines applications peuvent effectuer des activités en tant qu’un des utilisateurs. Ces événements sont accessibles dans le journal d’activité, mais peuvent être éliminés par filtrage. 
4. Si une application semble suspecte, il est recommandé de vérifier son nom et son serveur de publication dans les différents App Stores. Concentrez-vous sur les applications suivantes, qui peuvent être suspectes : 
    1. Application avec un faible nombre de téléchargements.
    2. Application avec un faible score ou des commentaires négatifs.
    3. Application avec un serveur de publication ou un site web suspects.
    4. Application avec une date de dernière mise à jour ancienne, peut indiquer une application qui n’est plus prise en charge. 
    5. Les applications qui ne correspondent pas à leurs autorisations peuvent indiquer que ces applications sont malveillantes. 
5. Si l’application est toujours suspecte, vous pouvez rechercher son serveur de publication et son URL en ligne. 

## <a name="example"></a>Exemple 

Choisissez l’option « Applications OAuth » sous l’icône de l’examen
 
Utilisez les options de filtre pour filtrer les applications (correspond à l’étape 1)
 

Examinez une application suspecte à l’aide des informations disponibles dans le portail (correspond à l’étape 2)
 

Utilisez le journal d'activité (correspond à l’étape 3)
 

Références https://searchmicroservices.techtarget.com/definition/OAuth https://docs.microsoft.com/cloud-app-security/manage-app-permissions


 
## <a name="next-steps"></a>Étapes suivantes
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md) 

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/) 
 
