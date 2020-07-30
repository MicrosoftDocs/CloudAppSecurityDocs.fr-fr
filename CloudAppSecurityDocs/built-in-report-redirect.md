---
title: Rechercher des rapports intégrés dépréciés dans Cloud App Security | Microsoft Docs
description: Cet article fournit des instructions pour générer des rapports dépréciés dans Cloud App Security.
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
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 0c5cb9d6604fead5090c68ae74d9919d4ab0b3e4
ms.sourcegitcommit: cc283f0ecf8124953f1f71181655603de6846d8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87254616"
---
# <a name="how-to-find-built-in-deprecating-reports"></a>Guide pratique pour rechercher des rapports intégrés dépréciés

*S’applique à : Microsoft Cloud App Security*

Nous mettons à jour la fonctionnalité de rapports intégrés en l’incorporant à d’autres parties du portail. La mise à jour de cette fonctionnalité est en cours afin d’améliorer les rapports de Microsoft Cloud App Security.

## <a name="deprecating-reports"></a>Rapports dépréciés

Ce tableau vous permet de voir les informations que fournissaient les rapports dépréciés en utilisant d’autres fonctionnalités de Cloud App Security :

| Type de rapport | Nom du rapport intégré | Description | Nouvel emplacement des données |
|----|----|----|----|
| Sécurité | Activité | Ce rapport vous permet d’afficher la liste des pays/régions à partir desquels l’activité provient de vos applications Cloud. Le rapport affiche différents paramètres révélant le volume d’activité de chaque pays/région, comme le nombre d’événements, le nombre d’utilisateurs, etc. Il permet d’obtenir une vue d’ensemble de la distribution géographique de vos utilisateurs. | Ces informations sont disponibles pour des applications, utilisateurs et adresses IP spécifiques. Pour chaque application, cliquez sur l’application. À partir de là, vous pouvez voir la carte des activités avec tous les emplacements. Pour chaque utilisateur, cliquez sur l’utilisateur, puis sur son tiroir d’insight. Vous pouvez y voir les emplacements récemment utilisés et le nombre d’adresses IP et d’ISP utilisés. Pour chaque adresse IP, cliquez sur l’adresse IP spécifique. Dans le tiroir de l’adresse IP, vous pouvez voir combien d’utilisateurs et d’administrateurs l’ont utilisée. |
| Sécurité | Utilisation du navigateur | Les attaques par navigateur font partie des vecteurs d’attaque les plus courants. Les fournisseurs investissent des ressources énormes dans la sécurisation des logiciels de navigation, créant un mécanisme de mise à jour efficace pour publier les mises à jour vers les points de terminaison. L’utilisation de navigateurs dépréciés longtemps après leur dernière mise à jour en fait des cibles de choix pour les entités malveillantes qui recourent à des kits d’attaque. Cette fonctionnalité permet d’obtenir la liste des navigateurs obsolètes utilisés au cours des sept derniers jours par les utilisateurs qui accèdent à vos applications cloud. Il vous permet également de savoir si l’utilisation du navigateur obsolète a été effectuée par un robot. | Accédez au **journal d’activité**, puis ouvrez **Filtres avancés**. Ensuite, définissez le filtre **Étiquette agent utilisateur** est égal à **Navigateur obsolète** et **Système d’exploitation obsolète** pour voir la liste de tous les navigateurs et systèmes d’exploitation obsolètes en cours d’utilisation. |
| Sécurité | Adresses IP - comptes disposant de privilèges| Ce rapport répertorie les adresses IP utilisées par les appareils ayant effectué des activités administratives au cours des sept derniers jours dans votre environnement cloud protégé par Cloud App Security. La date se base sur les journaux d’audit accumulés par Cloud App Security. Les adresses IP sont associées à un emplacement géographique et à une organisation source. Ces information vous permettent d’identifier les adresses IP suspectes qui se connectent à vos applications protégées. Vous pouvez afficher les journaux d’audit propres à une adresse IP en cliquant sur celle-ci. | Cliquez sur un utilisateur spécifique. Ensuite, dans le tiroir d’insight de l’utilisateur, vous pouvez voir les emplacements récemment utilisés et le nombre d’adresses IP et d’ISP utilisés. |
| Gestion des utilisateurs | Comptes inactifs | Les comptes inactifs sont des comptes qui ont accès à votre instance cloud, mais qui ne sont à l’origine d’aucun événement au cours des 60 derniers jours. L’absence d’action suggère que ces comptes ne sont plus actifs et qu’ils doivent être suspendus afin d’empêcher tout accès ultérieur par des entités malveillantes ou des employés sur le départ. Le respect de cette bonne pratique non seulement améliore votre posture de sécurité, mais permet également de réduire les coûts d’exploitation. | Accédez à la page **Utilisateurs et comptes** et utilisez le filtre **Dernière consultation** pour générer la liste de tous les utilisateurs qui n’ont pas effectué d’activités récemment. |
| Gestion des utilisateurs | Utilisateurs disposant de privilèges | Ce rapport liste les utilisateurs qui ont eu des privilèges élevés dans les applications de l’entreprise, comme les administrateurs, au cours des 7 derniers jours. Les comptes disposant de privilèges de ce type sont un vecteur d’attaque de choix pour les entités malveillantes, car ils peuvent leur permettre d’accéder largement à la configuration réseau et aux informations de l’entreprise. Si des comptes disposant de privilèges n’ont pas été utilisés récemment, cela peut indiquer un manque de sensibilisation à la sécurité informatique dans les entreprises, pouvant favoriser une vague de violations des données. Vous pouvez examiner l’utilisation des privilèges utilisateur élevés par le biais du journal d’audit et envisager la révocation des privilèges superflus. | Accédez à la page **Utilisateurs et comptes**, utilisez le filtre **Groupes** pour générer la liste des utilisateurs privilégiés qui appartiennent au groupe Administrateurs. |
| Gestion des utilisateurs | Comptes spéciaux disposant de privilèges | Salesforce a plusieurs types de comptes disposant de privilèges, tels que la modification de toutes les données, l’affichage de toutes les données et la gestion de tous les utilisateurs. Étant donné que les comptes privilégiés comme ceux-ci sont un vecteur d’attaque de choix pour les personnes malveillantes, car ils peuvent leur permettre d’accéder largement aux configurations et informations de l’entreprise, dresser la liste des comptes privilégiés se révèle très utile. | Accédez à Salesforce. Cliquez sur l’onglet **Comptes spéciaux disposant de privilèges**. |
| Gestion des données | Vue d’ensemble du partage de données | Ce rapport répertorie le nombre de fichiers stockés dans vos applications cloud, par autorisation d’accès. Le partage est devenu facile avec les applications cloud en raison de la facilité d’accès et de l’omniprésence. Un fichier qui n’est partagé avec personne d’autre que son propriétaire est appelé fichier privé. Si le fichier est partagé, Cloud App Security distingue quatre types d’états : <br /> - Un fichier (web) partagé publiquement est un fichier accessible sans aucune authentification, même par le biais d’un résultat de moteur de recherche.<br /> - Un fichier partagé publiquement est un fichier accessible sans aucune authentification, au moyen d’un lien.<br /> - Un fichier partagé en externe est un fichier auquel peuvent accéder des personnes n’appartenant pas à l’organisation une fois qu’elles se sont authentifiées auprès de l’application cloud.<br /> - Un fichier partagé en interne est un fichier accessible à la totalité ou à une partie des utilisateurs de votre organisation.|Accédez à **Fichiers**. Dans le coin supérieur droit, cliquez sur les trois points et, sous **Rapports de gestion des données**, sélectionnez **Vue d’ensemble du partage de données**. |
| Gestion des données | Partage sortant par domaine | Ce rapport répertorie les domaines avec lesquels des fichiers d’entreprise sont partagés par vos employés. Pour chaque domaine, le rapport détaille les utilisateurs de l’entreprise qui partagent des fichiers avec ce domaine, les fichiers effectivement partagés et les collaborateurs avec lesquels ces fichiers sont partagés. Nous vous recommandons de gérer le partage avec ces domaines par le biais de l’onglet Fichiers dans la page de chaque application concernée. | Accédez à **Fichiers**. Dans le coin supérieur droit, cliquez sur les trois points et, sous **Rapports de gestion des données**, sélectionnez **Partage sortant par domaine**. |
| Gestion des données | Propriétaires de fichiers partagés | Ce rapport répertorie les utilisateurs qui partagent des fichiers d’entreprise avec le monde extérieur. Les fichiers partagés en externe sont partagés avec des collaborateurs externes spécifiques. Les fichiers partagés publiquement sont accessibles sur Internet à toute personne par le biais d’un lien privé auquel cette personne est explicitement exposée. Les fichiers partagés publiquement (Internet) sont accessibles à toute personne sur Internet, y compris par le biais d’un résultat de moteur de recherche. Si vous constatez que des utilisateurs partagent un nombre excessif de fichiers, nous vous recommandons d’examiner la nature des autorisations correspondantes à l’aide de l’onglet Fichiers et de contacter ces utilisateurs pour mieux comprendre la façon dont ils recourent au partage externe. | Accédez à **Fichiers**. Dans le coin supérieur droit, cliquez sur les trois points et, sous **Rapports de gestion des données**, sélectionnez **Propriétaires de fichiers partagés**. |

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôle](control.md)

[!INCLUDE [Open support ticket](includes/support.md)]
