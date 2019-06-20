---
title: Examiner des utilisateurs à risque | Microsoft Docs
description: Ce tutoriel décrit le processus permettant d’examiner les utilisateurs à risque dans Microsoft Cloud App Security, dans des environnements hybrides, en utilisant une intégration à Azure ATP.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 06/11/2019
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: eac0b192-98d7-4939-9a07-1d4a7f8c39c3
ms.reviewer: dannyk
ms.suite: ems
ms.openlocfilehash: 80ef10622093523c92547de4bb52538b705ce168
ms.sourcegitcommit: 917d8cf85ac0b58a3b1788067c2ff92101eb3ccf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2019
ms.locfileid: "67237242"
---
# <a name="tutorial-investigate-risky-users"></a>Tutoriel : Examiner des utilisateurs à risque

*S’applique à : Microsoft Cloud App Security*

Microsoft Cloud App Security s’intègre à Azure Advanced Threat Protection pour fournir une analyse du comportement des entités et des utilisateurs (UEBA) et permettre un examen approfondi de votre environnement hybride, à la fois dans les applications cloud et les activités locales. 

Dans un même portail, Cloud App Security affiche désormais toutes les informations dont vous avez besoin pour prendre de meilleures décisions sur les risques au sein de votre organisation et corriger activement les menaces. En combinant les alertes et en analysant les données provenant de ces systèmes, Cloud App Security est le premier endroit où commencer à enquêter sur les utilisateurs afin d’obtenir des informations basées sur l’identité dans un environnement hybride :
- Microsoft Cloud App Security, qui identifie les attaques au sein d'une session cloud, couvrant non seulement les produits Microsoft mais aussi les applications tierces
- Azure Advanced Threat Protection, qui utilise l'analyse comportementale pour identifier les attaques sur votre réseau local
- Azure Active Directory Identity Protection, qui détecte et prévient de manière proactive les risques pouvant affecter les identités dans le cloud au niveau des utilisateurs et des connexions

Que vous commenciez à enquêter sur un utilisateur en fonction d’un risque affiché dans le tableau de bord Cloud App Security, ou un sur utilisateur dont l’intention n’a pas été identifiée par le système, commencez par le tableau de bord Cloud App Security pour examiner profondément ces utilisateurs à risque.  



Ce tutoriel fournit des instructions afin d’utiliser Cloud Discovery pour examiner des utilisateurs à risque.

> [!div class="checklist"]
> * Prérequis
> * Identifier les principaux utilisateurs à risque
> * Procéder à une investigation sur un utilisateur
> * Comprendre le risque de l’utilisateur
> * Protéger votre organisation


## <a name="prerequisites"></a>Prérequis

Pour procéder à un examen complet d’un utilisateur dans un environnement hybride, les éléments suivants sont nécessaires :

- Licence valide pour Microsoft Cloud App Security
- Licence valide pour Azure ATP connectée à votre instance Active Directory
- Activer Cloud App Security pour [l’intégration à votre environnement Azure ATP](aatp-integration.md) 

>[!NOTE]
>Si vous n’avez pas d'abonnement à Azure ATP, vous pourrez toujours utiliser le portail Cloud App Security pour examiner les utilisateurs, mais vous ne recevrez pas d’informations de votre environnement local. Vous pouvez également consulter les informations Azure ATP sur le portail Cloud App Security si vous possédez une licence Azure ATP mais que vous n'avez pas de licence pour Microsoft Cloud App Security.


## <a name="identify-top-risky-users"></a>Identifier les principaux utilisateurs à risque

Pour identifier vos utilisateurs présentant le plus de risques dans Cloud App Security :

1. Accédez au tableau de bord Cloud App Security et recherchez les personnes identifiées dans la mosaïque **Top users by investigation priority** (Principaux utilisateurs par priorité d’examen), puis examinez une à une la page de ces utilisateurs. <br>Le **numéro de priorité d’examen**, affiché en regard du nom d’utilisateur, correspond à la somme de toutes les activités à risque de l’utilisateur au cours de la semaine dernière. 

   ![Tableau de bord des principaux utilisateurs](./media/dashboard-top-users.png) 

2. Cliquez sur un utilisateur pour accéder à la page **Utilisateur**. 
   ![Page Utilisateur](./media/user-page.png) 

3. Cliquez sur le **score de priorité d'examen** pour afficher une liste de toutes les activités à risque effectuées au cours de la semaine dernière, dont la somme correspond au score affiché. 
4. Passez en revue les informations de la page **Utilisateur** pour obtenir une vue d’ensemble de l’utilisateur et vérifier s’il existe des cas où l'utilisateur a effectué des activités inhabituelles pour lui, ou effectuées à un moment inhabituel. Le **score de l’utilisateur par rapport à l’organisation** représente le centile de cet utilisateur dans le classement dans votre organisation, c’est-à-dire à quel niveau il figure sur la liste des utilisateurs que vous devriez examiner, par rapport aux autres utilisateurs de votre organisation. Le chiffre s’affiche en rouge si un utilisateur se situe dans ou au-dessus du 90e centile des utilisateurs à risque de votre organisation.<br>La page **Utilisateur** vous aide à répondre aux questions suivantes :
    1. Qui est l’utilisateur ?<br>Consultez le volet de gauche pour obtenir des informations sur l’identité de l’utilisateur et ce que l’on sait sur lui. Ce volet vous fournit des informations sur le rôle de l'utilisateur dans votre entreprise et son service. L'utilisateur est-il un ingénieur DevOps qui effectue souvent des activités inhabituelles dans le cadre de son travail ? L'utilisateur est-il un employé mécontent qui s’est vu refuser une promotion ?
    2. S’agit-il d’un utilisateur à risque ?<br>Consultez la partie supérieure du volet de droite pour savoir l’examen de cet utilisateur est justifié. Quel est le [score de risque](#risk-score) de l'employé ?
    3. Quel risque l’utilisateur présente-t-il pour votre organisation ?<br>Consultez la liste dans le volet inférieur, qui vous indique chaque activité et chaque alerte liées à l'utilisateur. Cette liste vous aide à comprendre quel type de risque l'utilisateur représente pour que vous puissiez commencer une enquête plus approfondie.

  >[!NOTE]
  >Remarque importante : même si la page **Utilisateur** fournit des informations sur les appareils, les ressources et les comptes pour toutes les activités, le score de priorité d'examen correspond à la somme de toutes les activités et alertes à risque identifiées au cours des 7 derniers jours.
 
 
## <a name="investigate-a-user"></a>Procéder à une investigation sur un utilisateur
Si quelque chose semble anormal ou que vous souhaitez enquêter sur un utilisateur, examinez les alertes de cet utilisateur. Isolées, certaines activités mineures ne semblent pas être un motif d’inquiétude, mais si Cloud App Security les regroupe avec d’autres activités, elles peuvent présenter un risque et nécessiter un examen de votre part.
 
Lorsque vous examinez un utilisateur, posez-vous ces questions sur les activités et les alertes affichées :
- Les activités s’inscrivent-elles dans le cadre de son travail ?
- Examinez la chronologie : les activités ont-elles été effectuées à des moments opportuns ?
- Pour chaque activité à laquelle vous avez répondu « non », examinez-la puis, dans le **journal d'activité**, cochez cette activité avec les autres activités du même utilisateur. Vous verrez si d’autres activités à risque se sont produites et à quel endroit l'utilisateur s'est connecté. Pour poursuivre l’enquête, il est très facile de basculer vers d’autres aspects, par exemple les dernières activités non anormales dans le cloud et sur site.


## Comprendre le risque de l’utilisateur <a name ="risk-score"></a>
    
Utilisez le **score de priorité d’examen** pour identifier les utilisateurs à examiner en premier. Cloud App Security crée des profils d'utilisateur pour chaque utilisateur en fonction de diverses analyses prenant en compte l’heure, les groupes homologues et l’activité attendue. Toute activité jugée anormale par rapport à la référence d'un utilisateur est évaluée et notée. Une fois le score évalué, les calculs homologues dynamiques propriétaires de Microsoft et l'apprentissage automatique sont exécutés sur les activités de l'utilisateur pour calculer la priorité d'examen pour chaque utilisateur. 

Le **score de priorité d'examen** vous permet de détecter à la fois les employés malveillants et les menaces externes qui se propagent latéralement dans votre organisation, sans avoir à vous fier aux détections déterministes standard.

En évaluant l'urgence de l'examen pour chaque utilisateur spécifique, le score de priorité d’examen est basé sur les alertes de sécurité, les activités anormales et l'impact potentiel sur les activités et les ressources de chaque utilisateur. 

Si vous cliquez sur le score d'une alerte ou d'une activité, vous pouvez voir les preuves sur lesquelles Cloud App Security s’est appuyé pour noter l'activité.

Chaque utilisateur Azure AD dispose d’un score de priorité d'examen dynamique, constamment mis à jour en fonction du comportement et de l'impact récents, calculé à partir des données évaluées par Azure ATP, Microsoft Cloud App Security et Azure AD Identity Protection. Vous pouvez maintenant identifier immédiatement les principales menaces réelles des utilisateurs par **score de priorité d'examen**, puis vérifier directement leur impact sur l’entreprise et examiner toutes les activités connexes, qu'il s’agisse d’informations compromises, de données exfiltrées ou de menaces provenant des employés.

Cloud App Security utilise les fonctionnalités suivantes pour mesurer le risque : 

- **Score d’alerte**<br>Le score d'alerte représente l'impact potentiel d'une alerte spécifique sur chaque utilisateur. Le score d’alerte est basé sur la gravité, l'impact sur les utilisateurs ainsi que le niveau de propagation chez les autres utilisateurs et dans toutes les entités de l'organisation.

- **Score d’activité**<br> Le score d'activité détermine la probabilité qu'un utilisateur donné effectue une activité spécifique, en fonction de l'apprentissage comportemental de l'utilisateur et de ses collègues. Les activités identifiées comme étant les plus anormales reçoivent les scores les plus élevés. 


## <a name="protect-your-organization"></a>Protéger votre organisation

Si vous constatez qu'un utilisateur a été victime d’une attaque ou que vous soupçonnez l'existence d'un problème, il est temps d'agir.
- Directement depuis le portail Cloud App Security, vous pouvez cliquer sur le bouton **Actions de l’utilisateur** et classer cet utilisateur comme un utilisateur à risque élevé ou le suspendre.
- Vous pouvez également réinitialiser le mot de passe de l'utilisateur pour bloquer son accès.
- Si vous examinez une alerte et estimez que l'activité n'aurait pas dû déclencher cette alerte, dans le [tiroir Activité](activity-filters.md), cliquez sur le lien **Envoyez-nous des commentaires** pour nous permettre d'ajuster notre système d'alerte en fonction de votre organisation.
- Une fois le problème résolu, fermez l’alerte.


## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  
