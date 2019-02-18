---
title: Vue d’ensemble du scénario de protection contre les menaces – Cloud App Security | Microsoft Docs
description: Cette rubrique décrit le scénario de protection de votre organisation contre les menaces présentes dans l’environnement cloud.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 12/14/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 7a06a243-9ec2-4a11-8db2-bc065cdfef64
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 0cb5f3ef6e88a35e7c8c5e262e666fb3d4107159
ms.sourcegitcommit: 8ef0438fa35916c48625ff750cb85e9628d202f2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56282747"
---
# <a name="protecting-your-organization-from-ransomware"></a>Protection de votre organisation contre les ransomwares

*S’applique à : Microsoft Cloud App Security*

Dans la dernière attaque massive par un ransomware, WannaCry a fortement frappé le cybermonde en infectant un nombre estimé de 200 000 ordinateurs dans 150 pays. Avec l’augmentation des attaques de ransomwares ces dernières années, en moyenne 25 000 attaques par mois en 2015 et 56 000 en 2016, il devient nécessaire de mettre en place une cybersécurité proactive pour garantir que votre réseau et votre cloud ne sont pas exposés. Cet article explique comment vous pouvez utiliser Cloud App Security pour surveiller votre cloud, détecter et atténuer les menaces, et appliquer les meilleures pratiques pour protéger votre environnement contre les ransomwares.

## <a name="what-is-ransomware"></a>Qu’est-ce qu’un ransomware ?
Un ransomware est une cyberattaque dans laquelle l’attaquant vous envoie un fichier capable de vous empêcher d’accéder à votre ordinateur et de chiffrer vos fichiers personnels. Les fichiers sont parfois retenus contre une rançon et ne sont pas déchiffrés tant que vous ne payez pas l’attaquant pour qu’il restaure l’accès à votre ordinateur, vos fichiers ou vos applications métier critiques. Les attaques de ransomware peuvent affecter n’importe quel ordinateur, domicile, bureau, réseau ou serveur. En fait, parce que les grandes organisations emploient de nombreux utilisateurs susceptibles d’ouvrir par inadvertance un fichier qui libère un ransomware sur votre réseau, elles sont encore plus exposées au risque de devoir payer une rançon pour arrêter le ransomware et restaurer l’accès aux ordinateurs ou fichiers.

>[!NOTE]
> Ce cas d’utilisation s’applique à Office 365, G Suite, Box et Dropbox.

## <a name="the-threat"></a>LA MENACE
Un utilisateur de votre organisation est la cible d’une attaque de ransomware. L’utilisateur peut ouvrir involontairement un e-mail infecté et exécuter un ransomware qui infecte la totalité de ses fichiers, y compris les fichiers synchronisés dans le cloud.

## <a name="the-solution"></a>LA SOLUTION
Détectez les ransomwares potentiels dans votre environnement cloud en créant une stratégie qui vous alerte quand une activité suspecte est détectée, et configurez des actions automatiques pour empêcher les fichiers infectés par le ransomware d’être enregistrés dans votre cloud.

## <a name="out-of-the-box-protection"></a>Protection prête à l’emploi

[Connectez](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) au moins une application cloud (Office 365, G Suite, Box et Dropbox) à Cloud App Security.

1.  Par défaut, Cloud App Security analyse votre réseau pour établir une base de référence, où il découvre ce que font généralement les utilisateurs dans votre cloud et à quel moment. 

2. Les [stratégies de détection des menaces](anomaly-detection-policy.md) automatisées de Cloud App Security commencent à s’exécuter en arrière-plan à partir du moment où vous vous connectez. Une de ces stratégies permet de rechercher des activités de ransomware pour garantir une couverture complète contre des attaques de ransomware complexes. Fort de notre expertise en recherche dans la sécurité visant à identifier les modèles comportementaux qui reflètent des activités de ransomware, Cloud App Security assure une protection complète et solide. Si Cloud App Security identifie, par exemple, un taux élevé de chargements de fichiers ou d’activités de suppression de fichiers, cela peut représenter un processus de chiffrement indésirable. Ces données sont collectées dans les journaux reçus des API connectées, puis combinées avec des modèles comportementaux appris et des informations sur les menaces, par exemple, des extensions de ransomware. 




## <a name="next-steps"></a>Étapes suivantes 

[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)  
  
  
