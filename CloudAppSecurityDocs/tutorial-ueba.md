---
title: Examiner des utilisateurs à risque | Microsoft Docs
description: Ce tutoriel décrit le processus permettant d’examiner les utilisateurs à risque dans Microsoft Cloud App Security, dans des environnements hybrides, en utilisant une intégration à Azure ATP.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 06/27/2019
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: eac0b192-98d7-4939-9a07-1d4a7f8c39c3
ms.reviewer: dannyk
ms.suite: ems
ms.openlocfilehash: 654cc70f9e5322f608eedb55042f60d558d858a6
ms.sourcegitcommit: 3938edadc5f89f87cdeba607476cf3983b2413e8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67411940"
---
# <a name="tutorial-investigate-risky-users"></a>Tutoriel : Examiner des utilisateurs à risque

*S’applique à : Microsoft Cloud App Security*

Des équipes des opérations de sécurité sont mises au défi de surveiller l’activité de l’utilisateur, suspecte ou pas, dans toutes les dimensions de la surface d’attaque d’identité, à l’aide de plusieurs solutions de sécurité qui souvent ne sont pas connectées.

Afin de vous permettre de mieux vous concentrer sur l’identité de l’utilisateur, Microsoft Cloud App Security s’intègre avec Azure Advanced Threat Protection (ATP) à l’analyse comportementale des entités et utilisateurs fournie (UEBA).

Alors que de nombreuses sociétés ont maintenant des équipes de chasse pour identifier de façon proactive les menaces dans leurs environnements, le fait de connaître ce que vous recherchez dans la vaste quantité de données peut être un défi. Microsoft Cloud App Security simplifie désormais le problème en éliminant la nécessité de créer des règles de corrélation complexes et vous permet de détecter les attaques qui s’étendent sur votre cloud et réseau local.

Que vous commenciez à enquêter sur un utilisateur en fonction d’un risque affiché dans le tableau de bord Cloud App Security ou sur utilisateur dont l’intention n’a pas été identifiée par le système, commencez par le tableau de bord Cloud App Security pour examiner profondément ces utilisateurs à risque.  

Ce tutoriel fournit des instructions afin d’utiliser Cloud Discovery pour examiner des utilisateurs à risque.

> [!div class="checklist"]
> * Prérequis
> * Identifier les principaux utilisateurs à risque
> * Procéder à une investigation sur un utilisateur
> * Comprendre le risque de l’utilisateur
> * Protéger votre organisation


## <a name="prerequisites"></a>Prérequis

L’analyse comportementale des utilisateurs et des entités (UEBA) fonctionne sur le cloud et localement. Pour détecter les menaces locales, vous devez posséder une licence valide pour Azure ATP connectée à votre instance Active Directory et Cloud App Security doit être configuré pour [s’intégrer à votre environnement Azure ATP](aatp-integration.md).


## Comprendre le score de priorité d’examen <a name ="risk-score"></a>

Le score de priorité d’examen est fourni par Cloud App Security à chaque utilisateur pour vous permettre de savoir quel risque présente un utilisateur par rapport à d’autres utilisateurs de votre organisation.
    
Utilisez le **score de priorité d’examen** pour identifier les utilisateurs à examiner en premier. Cloud App Security crée des profils d'utilisateur pour chaque utilisateur en fonction de diverses analyses prenant en compte l’heure, les groupes homologues et l’activité attendue. Toute activité jugée anormale par rapport à la référence d'un utilisateur est évaluée et notée. Une fois le score évalué, les calculs homologues dynamiques propriétaires de Microsoft et l'apprentissage automatique sont exécutés sur les activités de l'utilisateur pour calculer la priorité d'examen pour chaque utilisateur. 

Le **score de priorité d'examen** vous permet de détecter à la fois les employés malveillants et les menaces externes qui se propagent latéralement dans votre organisation, sans avoir à vous fier aux détections déterministes standard.

En évaluant l'urgence de l'examen pour chaque utilisateur spécifique, le score de priorité d’examen est basé sur les alertes de sécurité, les activités anormales et l'impact potentiel sur les activités et les ressources de chaque utilisateur. 

Si vous cliquez sur le score d'une alerte ou d'une activité, vous pouvez voir les preuves sur lesquelles Cloud App Security s’est appuyé pour noter l'activité.

Chaque utilisateur Azure AD dispose d’un score de priorité d'examen dynamique, constamment mis à jour en fonction du comportement et de l'impact récents, calculé à partir des données évaluées par Azure ATP, Microsoft Cloud App Security et Azure AD Identity Protection. Vous pouvez maintenant identifier immédiatement les principaux utilisateurs à risque par **score de priorité d'examen**, puis vérifier directement leur impact sur l’entreprise et examiner toutes les activités connexes, qu'il s’agisse d’informations compromises, de données exfiltrées ou de menaces provenant des employés.

Cloud App Security utilise les fonctionnalités suivantes pour mesurer le risque : 

- **Score d’alerte**<br>Le score d'alerte représente l'impact potentiel d'une alerte spécifique sur chaque utilisateur. Le score d’alerte est basé sur la gravité, l'impact sur les utilisateurs ainsi que le niveau de propagation chez les autres utilisateurs et dans toutes les entités de l'organisation.

- **Score d’activité**<br> Le score d'activité détermine la probabilité qu'un utilisateur donné effectue une activité spécifique, en fonction de l'apprentissage comportemental de l'utilisateur et de ses collègues. Les activités identifiées comme étant les plus anormales reçoivent les scores les plus élevés. 

## <a name="identify-top-risky-users"></a>Identifier les principaux utilisateurs à risque

Pour identifier vos utilisateurs présentant le plus de risques dans Cloud App Security :

1. Accédez au tableau de bord Cloud App Security et recherchez les personnes identifiées dans la mosaïque **Top users by investigation priority** (Principaux utilisateurs par priorité d’examen), puis examinez une à une la page de ces utilisateurs. <br>Le **numéro de priorité d’examen**, affiché en regard du nom d’utilisateur, correspond à la somme de toutes les activités à risque de l’utilisateur au cours de la semaine dernière. 

   ![Tableau de bord des principaux utilisateurs](./media/dashboard-top-users.png) 

2. Cliquez sur un utilisateur pour accéder à la page **Utilisateur**. 
   ![Page Utilisateur](./media/user-page.png) 

4. Passez en revue les informations de la page **Utilisateur** pour obtenir une vue d’ensemble de l’utilisateur et vérifier s’il existe des cas où l'utilisateur a effectué des activités inhabituelles pour lui, ou effectuées à un moment inhabituel. Le **score de l’utilisateur par rapport à l’organisation** représente le centile de cet utilisateur dans le classement dans votre organisation, c’est-à-dire à quel niveau il figure sur la liste des utilisateurs que vous devriez examiner, par rapport aux autres utilisateurs de votre organisation. Le chiffre s’affiche en rouge si un utilisateur se situe dans ou au-dessus du 90e centile des utilisateurs à risque de votre organisation.<br>La page **Utilisateur** vous aide à répondre aux questions suivantes :
    - Qui est l’utilisateur ?<br>Consultez le volet de gauche pour obtenir des informations sur l’identité de l’utilisateur et ce que l’on sait sur lui. Ce volet vous fournit des informations sur le rôle de l'utilisateur dans votre entreprise et son service. L'utilisateur est-il un ingénieur DevOps qui effectue souvent des activités inhabituelles dans le cadre de son travail ? L'utilisateur est-il un employé mécontent qui s’est vu refuser une promotion ?
      
   - S’agit-il d’un utilisateur à risque ?<br>Consultez la partie supérieure du volet de droite pour savoir l’examen de cet utilisateur est justifié. Quel est le [score de risque](#risk-score) de l'employé ?
    
   - Quel risque l’utilisateur présente-t-il pour votre organisation ?<br>Consultez la liste dans le volet inférieur, qui vous indique chaque activité et chaque alerte liées à l'utilisateur. Cette liste vous aide à comprendre quel type de risque l'utilisateur représente. Dans la chronologie, cliquez sur chaque ligne afin de descendre encore plus dans la hiérarchie de l’activité ou de l’alerte elle-même. Vous pouvez cliquer également sur le numéro en regard de l’activité afin que vous puissiez comprendre la preuve qui influence le score lui-même.

  >[!NOTE]
  >Remarque importante : même si la page **Utilisateur** fournit des informations sur les appareils, les ressources et les comptes pour toutes les activités, le score de priorité d'examen correspond à la somme de toutes les activités et alertes à risque identifiées au cours des 7 derniers jours.
 
 
## <a name="investigate-a-user"></a>Procéder à une investigation sur un utilisateur

Lorsque vous examinez un utilisateur en fonction d’une alerte ou si vous avez vu une alerte dans un système externe, il peut y avoir des activités qui peuvent ne pas être la cause d’une alerte seules, mais lorsque Cloud App Security les agrège avec d’autres activités, l’alerte peut indiquer un événement suspect.
 
Lorsque vous examinez un utilisateur, posez-vous ces questions sur les activités et les alertes affichées :
- Y a-t-il une justification métier pour que cet employé effectue ces activités ? Par exemple, si une personne du Marketing accède à la base de code ou une personne du Développement accède à une base de données Finance, vous devez suivre l’employé pour vous assurer qu’il s’agissait d’une activité intentionnelle et justifiée.

- Accédez au **journal d’activité** pour comprendre pourquoi cette activité a reçu un score élevé, tandis que d’autres n’ont pas reçu ce score. Vous pouvez définir la **Priorité d’examen** sur **Est défini** pour comprendre quelles activités sont suspectes. Par exemple, vous pouvez filtrer selon la Priorité d’examen pour toutes les activités qui se sont produites en Ukraine. Vous verrez alors si d’autres activités à risque se sont produites et à quel endroit l'utilisateur s'est connecté. Pour poursuivre l’examen, il est très facile de basculer vers d’autres aspects, par exemple les dernières activités non anormales dans le cloud et localement.




## <a name="protect-your-organization"></a>Protéger votre organisation

Si vous constatez qu'un utilisateur a été victime d’une attaque ou que vous soupçonnez l'existence d'un problème, il est temps d'agir.

Une fois l’examen terminé, vous pouvez contacter l’utilisateur : les informations de contact de tous les utilisateurs à partir d’Azure Active Directory sont ajoutées au Cloud App Security afin que vous puissiez voir qui a effectué chaque activité. Assurez-vous que l’utilisateur est familiarisé avec les activités.


- Directement depuis le portail Cloud App Security, vous pouvez cliquer sur le bouton **Actions de l’utilisateur** et classer cet utilisateur comme un utilisateur à risque élevé ou le suspendre.
- Dans le cas d’une identité compromise, vous pouvez demander à l’utilisateur de réinitialiser son mot de passe et vous assurer que le mot de passe est suffisamment complexe pour être plus difficile à pirater.
- Si vous examinez une alerte et estimez que l'activité n'aurait pas dû déclencher cette alerte, dans le [tiroir Activité](activity-filters.md), cliquez sur le lien **Envoyez-nous des commentaires** pour nous permettre d'ajuster notre système d'alerte en fonction de votre organisation.
- Une fois le problème résolu, fermez l’alerte.


## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  
