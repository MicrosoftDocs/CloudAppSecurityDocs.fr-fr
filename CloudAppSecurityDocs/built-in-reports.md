---
title: Guide pratique pour générer des rapports dans Microsoft Cloud App Security | Microsoft Docs
description: Cette rubrique fournit des instructions pour générer des rapports de gestion de données dans Microsoft Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/11/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 0dcc3c35-f787-4822-84c6-d4dff897dd6c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 7684e6e3172076d8f7e8a4d69b1ddd70d322a200
ms.sourcegitcommit: 82052a88acbc33893f7b9e0d10cc2e8c652ef003
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49349506"
---
*S’applique à : Microsoft Cloud App Security*



# <a name="generate-data-management-reports"></a>Générer des rapports de gestion de données

Microsoft Cloud App Security vous permet de générer des rapports qui fournissent une vue d’ensemble des fichiers dans vos applications cloud.

Pour générer ces rapports

1. Accédez à **Fichiers**. 
2. En haut à droite, cliquez sur les trois points et sous **Rapports de gestion de données**, sélectionnez un des rapports suivants.

 ![rapports](./media/reports.png)

## <a name="data-sharing-overview"></a>Vue d’ensemble du partage de données 

Ce rapport liste le nombre de fichiers, par autorisation d’accès, qui sont stockés dans vos applications cloud. Le partage de fichiers est devenu facile avec les applications cloud en raison de la facilité d’accès et de l’omniprésence. Un **fichier privé** n’est partagé avec personne d’autre que son propriétaire. Si le fichier est partagé, Cloud App Security distingue quatre types d’états :
- Un fichier en **Partage public (Internet)** est un fichier accessible sans aucune authentification, même par le biais d’un résultat de moteur de recherche.
 - Un fichier en **Partage public** est un fichier accessible sans aucune authentification, au moyen d’un lien.
 - Un fichier en **Partage externe** est un fichier auquel peuvent accéder des personnes n’appartenant pas à l’organisation une fois qu’elles se sont authentifiées auprès de l’application cloud.
- Un fichier en **Partage interne** est un fichier accessible à la totalité ou à une partie des utilisateurs de votre organisation.

## <a name="outbound-sharing-by-domain"></a>Partage sortant par domaine

Ce rapport répertorie les domaines avec lesquels des fichiers d’entreprise sont partagés par vos employés. Pour chaque domaine, le rapport affiche les utilisateurs qui partagent des fichiers avec ce domaine. Le rapport affiche également les fichiers qui sont partagés et avec qui les fichiers de collaborateur sont partagés. Il est recommandé de gérer le partage avec ces domaines. Vous pouvez gérer le partage sous l’onglet Fichiers de la page de chaque application concernée.

## <a name="owners-of-shared-files"></a>Propriétaires de fichiers partagés

Ce rapport répertorie les utilisateurs qui partagent des fichiers d’entreprise avec le monde extérieur. Les fichiers en partage externe sont des fichiers partagés avec des collaborateurs externes spécifiques. Les fichiers en partage public sont accessibles à toute personne sur Internet, via une lien privé. Ces fichiers sont uniquement accessibles par des personnes qui ont explicitement le lien. Les fichiers en partage public (Internet) sont accessibles à toute personne sur Internet, notamment dans un résultat de moteur de recherche. Si vous trouvez des utilisateurs qui partagent un nombre excessif de fichiers, il est recommandé d’en rechercher la raison. Vous pouvez regarder dans l’onglet Fichiers, puis contacter ces utilisateurs pour mieux comprendre leur utilisation du partage externe.


  
## <a name="next-steps"></a>Étapes suivantes 
[Contrôler](control.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  