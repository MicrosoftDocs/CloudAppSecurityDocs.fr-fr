---
title: Comprendre les champs dans les rapports prédéfinis de Cloud App Security | Microsoft Docs
description: Cette rubrique fournit une liste des rapports intégrés et leurs utilisations.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/15/2018
ms.topic: article
ms.prod: ''
ms.app: cloud-app-security
ms.technology: ''
ms.assetid: 588b3639-f748-45a6-bc4b-a6ee47c1865e
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 8793c7f60b3c18b2330552f9d300b557c1347e6d
ms.sourcegitcommit: 0fb77b0b4e9b2f5480758e9fb6ec609d5b3eb879
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2018
---
# <a name="built-in-report-reference"></a>Informations de référence sur les rapports intégrés

CAS propose une liste complète de rapports intégrés prêts à l’emploi à l’aide desquels vous pouvez recueillir des insights et surveiller l’utilisation du cloud. Vous pouvez utiliser les filtres pour personnaliser les rapports et les exporter par souci pratique.


Le tableau suivant dresse la liste des rapports intégrés et indique les types d’événements que vous pouvez surveiller avec ces rapports.  
  
## <a name="built-in-report-list"></a>Liste des rapports intégrés  
  
|Type de rapport|Nom du rapport intégré|Description|  
|-----------------|---------------------------|-----------------|  
|Sécurité|Activité par lieu|Ce rapport répertorie les pays d’où provient une activité dans vos applications cloud et différents paramètres représentant le volume d’activité dans chaque pays, tels que le nombre d’événements, le nombre d’utilisateurs, etc. Utilisez-le pour obtenir une vue d’ensemble de la distribution géographique de vos utilisateurs.|  
|Sécurité|Utilisation du navigateur|Les attaques par navigateur font partie des vecteurs d’attaque les plus courants. Les fournisseurs investissent des ressources énormes dans la sécurisation des logiciels de navigation, créant un mécanisme de mise à jour efficace pour diffuser les mises à jour vers les points de terminaison. L’utilisation de navigateurs déconseillés longtemps après leur dernière mise à jour en fait des cibles de choix pour les entités malveillantes qui recourent à des kits d’attaque. Ce rapport répertorie les navigateurs périmés utilisés au cours des 7 derniers jours par les utilisateurs qui accèdent à vos applications cloud. Le rapport vous permet également de savoir si l’utilisation du navigateur obsolète a été effectuée par un robot.|  
|Sécurité|Adresses IP - comptes disposant de privilèges|Ce rapport répertorie les adresses IP utilisées par les appareils pour effectuer des activités administratives au cours des 7 derniers jours dans votre environnement cloud protégé par Cloud App Security. Ce rapport est basé sur les journaux d’audit accumulés par Cloud App Security. Les adresses IP sont associées à un emplacement géographique et à une organisation source. Utilisez ce rapport pour identifier les adresses IP suspectes qui se connectent à vos applications protégées. Vous pouvez afficher les journaux d’audit propres à une adresse IP en cliquant sur celle-ci.|  
|Gestion des utilisateurs|Comptes inactifs|Les comptes inactifs sont des comptes qui ont accès à votre instance cloud, mais qui ne sont à l’origine d’aucun événement au cours des 60 derniers jours. Il est possible que ces comptes ne soient plus actifs et qu’ils doivent être suspendus pour empêcher tout accès de la part d’entités malveillantes ou d’employés sur le départ. Le respect de cette bonne pratique non seulement améliore votre posture de sécurité, mais permet également de réduire les coûts d’exploitation.|  
|Gestion des utilisateurs|Utilisateurs disposant de privilèges|Ce rapport liste les utilisateurs qui ont eu des privilèges élevés dans les applications de l’entreprise, comme les administrateurs, au cours des 7 derniers jours. Les comptes disposant de privilèges de ce type sont un vecteur d’attaque de choix pour les entités malveillantes, car ils peuvent leur permettre d’accéder largement à la configuration réseau et aux informations de l’entreprise. Si des comptes disposant de privilèges n’ont pas été utilisés récemment, cela peut indiquer un manque de sensibilisation à la sécurité informatique dans les entreprises, pouvant favoriser une vague de violations des données. Vous pouvez examiner l’utilisation des privilèges utilisateur élevés par le biais du journal d’audit et envisager la révocation des privilèges superflus.|  
|Gestion des utilisateurs|Comptes spéciaux disposant de privilèges|Salesforce a plusieurs types de comptes disposant de privilèges, tels que la modification de toutes les données, l’affichage de toutes les données et la gestion de tous les utilisateurs. Les comptes disposant de privilèges de ce type sont un vecteur d’attaque de choix pour les entités malveillantes, car ils peuvent leur permettre d’accéder largement aux configurations et informations de l’entreprise.|  
|Gestion des données|Vue d’ensemble du partage de données|Ce rapport répertorie le nombre de fichiers stockés dans vos applications cloud, par autorisation d’accès. Le partage est devenu facile avec les applications cloud en raison de la facilité d’accès et de l’omniprésence.<br /><br /> Un fichier qui n’est partagé avec personne d’autre que son propriétaire est appelé fichier privé. Si le fichier est partagé, Cloud App Security distingue quatre types d’états :<br /><br /> Un fichier (web) partagé publiquement est un fichier accessible sans aucune authentification, même par le biais d’un résultat de moteur de recherche.<br /><br /> Un fichier partagé publiquement est un fichier accessible sans aucune authentification, au moyen d’un lien.<br /><br /> Un fichier partagé en externe est un fichier auquel peuvent accéder des personnes n’appartenant pas à l’organisation une fois qu’elles se sont authentifiées auprès de l’application cloud.<br /><br /> Un fichier partagé en interne est un fichier accessible à la totalité ou à une partie des utilisateurs de votre organisation.|  
|Gestion des données|Partage sortant par domaine|Ce rapport répertorie les domaines avec lesquels des fichiers d’entreprise sont partagés par vos employés. Pour chaque domaine, le rapport détaille les utilisateurs de l’entreprise qui partagent des fichiers avec ce domaine, les fichiers effectivement partagés et les collaborateurs avec lesquels ces fichiers sont partagés. Nous vous recommandons de gérer le partage avec ces domaines par le biais de l’onglet Fichiers dans la page de chaque application concernée.|  
|Gestion des données|Propriétaires de fichiers partagés|Ce rapport répertorie les utilisateurs qui partagent des fichiers d’entreprise avec le monde extérieur. Les fichiers partagés en externe sont partagés avec des collaborateurs externes spécifiques. Les fichiers partagés publiquement sont accessibles sur Internet à toute personne par le biais d’une liaison privée à laquelle cette personne est explicitement exposée. Les fichiers partagés publiquement (Internet) sont accessibles à toute personne sur Internet, y compris par le biais d’un résultat de moteur de recherche.  Si vous constatez que des utilisateurs partagent un nombre excessif de fichiers, nous vous recommandons d’examiner la nature des autorisations correspondantes à l’aide de l’onglet Fichiers et de contacter ces utilisateurs pour mieux comprendre la façon dont ils recourent au partage externe.|  
  
## <a name="see-also"></a>Voir aussi  
[Contrôler](control.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  