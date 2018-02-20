---
title: "Vue d’ensemble du scénario de protection contre les menaces | Microsoft Docs"
description: "Cette rubrique décrit le scénario de protection de votre organisation contre les menaces présentes dans l’environnement cloud."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/15/2018
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 7a06a243-9ec2-4a11-8db2-bc065cdfef64
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 4bb90d94fdab3725c853a772df1c484260a6c5ec
ms.sourcegitcommit: 458e936e1ac548eda37e9bf955b439199bbdd018
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2018
---
# <a name="protecting-your-organization-from-ransomware"></a>Protection de votre organisation contre les ransomwares

Dans la dernière attaque massive par un ransomware, WannaCry a fortement frappé le cybermonde en infectant un nombre estimé de 200 000 ordinateurs dans 150 pays. Avec l’augmentation des attaques de ransomwares ces dernières années, en moyenne 25 000 attaques par mois en 2015 et 56 000 en 2016, il devient nécessaire de mettre en place une cybersécurité proactive pour garantir que votre réseau et votre cloud ne sont pas exposés. Cet article explique comment vous pouvez utiliser Cloud App Security pour surveiller votre cloud, détecter et atténuer les menaces, et appliquer les bonnes pratiques pour protéger votre environnement contre les ransomwares.

## <a name="what-is-ransomware"></a>Qu’est-ce qu’un ransomware ?
Un ransomware est une cyberattaque dans laquelle l’attaquant vous envoie un fichier capable de vous empêcher d’accéder à votre ordinateur et de chiffrer vos fichiers personnels. Les fichiers sont parfois retenus contre une rançon et ne sont pas déchiffrés tant que vous ne payez pas l’attaquant pour qu’il restaure l’accès à votre ordinateur, vos fichiers ou vos applications métier critiques. Les attaques de ransomware peuvent affecter n’importe quel ordinateur, domicile, bureau, réseau ou serveur. En fait, parce que les grandes organisations emploient de nombreux utilisateurs susceptibles d’ouvrir par inadvertance un fichier qui libère un ransomware sur votre réseau, elles sont encore plus exposées au risque de devoir payer une rançon pour arrêter le ransomware et restaurer l’accès aux ordinateurs ou fichiers.

>[!NOTE]
> Ce cas d’utilisation s’applique à Office 365, G Suite, Box et Dropbox.

## <a name="the-threat"></a>LA MENACE
Un utilisateur de votre organisation est la cible d’une attaque de ransomware. L’utilisateur peut ouvrir involontairement un e-mail infecté et exécuter un ransomware qui infecte la totalité de ses fichiers, y compris les fichiers synchronisés dans le cloud.

## <a name="the-solution"></a>LA SOLUTION
Détectez les ransomwares potentiels dans votre environnement cloud en créant une stratégie qui vous alerte quand une activité suspecte est détectée, et configurez des actions automatiques pour empêcher les fichiers infectés par le ransomware d’être enregistrés dans votre cloud.

## <a name="prerequisites"></a>Prérequis

[Connectez](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) au moins une application cloud (Office 365, G Suite, Box et Dropbox) à Cloud App Security.

## <a name="setting-up-monitoring"></a>Configurer la surveillance

1.  Par défaut, Cloud App Security analyse votre réseau pour établir une base de référence, où il découvre ce que font généralement les utilisateurs dans votre cloud et à quel moment. 

2. Il est également important de commencer à surveiller vos applications cloud en configurant une stratégie qui détecte les téléchargements en masse et vous alerte si une activité inhabituelle se produit :

    1. Sous l’onglet **Contrôle**, cliquez sur [**Modèles**](policy-template-reference.md). 
   
    2. Dans la liste [**Modèle de stratégie**](policy-template-reference.md), choisissez **Activité de ransomware potentielle**. 
       ![modèle pour ransomware](./media/ransomware-template.png)
    3. Ce modèle est prêt à l’emploi pour rechercher des activités typiques d’attaques de ransomware, ainsi que les fichiers et dossiers associés aux ransomwares connus. Vous pouvez aussi définir le type d’alerte que vous recevez (e-mails et SMS) quand la stratégie trouve une correspondance.
        ![modèle pour ransomware](./media/ransomware-template-fields.png)
    4. Cliquez sur **Créer**. 
   
     
2. Étudier les correspondances
    
    1. Dans la page **Stratégies**, cliquez sur le nom de la stratégie pour atteindre le **Rapport de stratégie**, puis passez en revue les correspondances qui ont été déclenchées.

    2. Pour examiner une correspondance, cliquez sur celle-ci et ouvrez le tiroir d’activité. Dans le tiroir, vous pouvez voir les autres stratégies correspondant à cette activité. 
     
## <a name="validating-your-policy"></a>Valider votre stratégie

1. Pour simuler une alerte, remplacez l’extension de 30 fichiers par .wncry et chargez-les dans votre site SharePoint.
3. Accédez au rapport de stratégie. Une correspondance de stratégie d’activité devrait apparaître sous peu. 
4. Vous pouvez cliquer sur la correspondance pour voir quels fichiers ont été téléchargés. La correspondance elle-même est masquée pour protéger les données sensibles. 

## <a name="remediating-attacks-and-preventing-risk"></a>Correction des attaques et prévention des risques

Après avoir validé et affiné la stratégie, supprimez les faux positifs possibles qui peuvent avoir correspondu à votre stratégie. Effectuez ensuite les opérations suivantes : 
1. Quand une stratégie de ransomware trouve une correspondance, vous pouvez y remédier en définissant des [actions de gouvernance](governance-actions.md) automatiques.

2. Pour empêcher les attaques futures, définissez la stratégie pour effectuer des actions de gouvernance automatiques. Par exemple, dans SharePoint et OneDrive, vous pouvez définir la stratégie pour automatiquement **Interrompre la synchronisation de l’utilisateur**.

 ## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  