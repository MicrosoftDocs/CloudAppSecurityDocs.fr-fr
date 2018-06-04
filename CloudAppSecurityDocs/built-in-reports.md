---
title: Guide pratique pour générer des rapports dans Microsoft Cloud App Security | Microsoft Docs
description: Cette rubrique fournit des instructions pour générer des rapports de gestion de données dans Microsoft Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/30/2018
ms.topic: article
ms.prod: ''
ms.app: cloud-app-security
ms.technology: ''
ms.assetid: 0dcc3c35-f787-4822-84c6-d4dff897dd6c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 4eca209bb4ec71e519439704a7dbb33e48107c9b
ms.sourcegitcommit: af8fad9709171b200699ca1ed513e2831826ed7e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34568696"
---
*S’applique à : Microsoft Cloud App Security*



# <a name="generate-data-management-reports"></a>Générer des rapports de gestion de données

Microsoft Cloud App Security vous permet de générer des rapports qui fournissent une vue d’ensemble des fichiers dans vos applications cloud.

Pour générer ces rapports

1. Accédez à **Fichiers**. 
2. En haut à droite, cliquez sur les trois points et sous **Rapports de gestion de données**, sélectionnez un des rapports suivants.

   ![rapports](./media/reports.png) I
## <a name="data-sharing-overview"></a>Vue d’ensemble du partage de données 

Ce rapport répertorie le nombre de fichiers stockés dans vos applications cloud, par autorisation d’accès. Le partage est devenu facile avec les applications cloud en raison de la facilité d’accès et de l’omniprésence. Un fichier qui n’est partagé avec personne d’autre que son propriétaire est appelé fichier privé. Si le fichier est partagé, Cloud App Security distingue quatre types d’états : <br> - Un fichier (web) partagé publiquement est un fichier accessible sans aucune authentification, même par le biais d’un résultat de moteur de recherche.<br> - Un fichier partagé publiquement est un fichier accessible sans aucune authentification, au moyen d’un lien.<br> - Un fichier partagé en externe est un fichier auquel peuvent accéder des personnes n’appartenant pas à l’organisation une fois qu’elles se sont authentifiées auprès de l’application cloud.<br> - Un fichier partagé en interne est un fichier accessible à la totalité ou à une partie des utilisateurs de votre organisation.

## <a name="outbound-sharing-by-domain"></a>Partage sortant par domaine

Ce rapport répertorie les domaines avec lesquels des fichiers d’entreprise sont partagés par vos employés. Pour chaque domaine, le rapport détaille les utilisateurs de l’entreprise qui partagent des fichiers avec ce domaine, les fichiers effectivement partagés et les collaborateurs avec lesquels ces fichiers sont partagés. Nous vous recommandons de gérer le partage avec ces domaines par le biais de l’onglet Fichiers dans la page de chaque application concernée.

## <a name="owners-of-shared-files"></a>Propriétaires de fichiers partagés

Ce rapport répertorie les utilisateurs qui partagent des fichiers d’entreprise avec le monde extérieur. Les fichiers partagés en externe sont partagés avec des collaborateurs externes spécifiques. Les fichiers partagés publiquement sont accessibles sur Internet à toute personne par le biais d’une liaison privée à laquelle cette personne est explicitement exposée. Les fichiers partagés publiquement (Internet) sont accessibles à toute personne sur Internet, y compris par le biais d’un résultat de moteur de recherche. Si vous constatez que des utilisateurs partagent un nombre excessif de fichiers, nous vous recommandons d’examiner la nature des autorisations correspondantes à l’aide de l’onglet Fichiers et de contacter ces utilisateurs pour mieux comprendre la façon dont ils recourent au partage externe.


  
## <a name="see-also"></a>Voir aussi 
[Contrôler](control.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  