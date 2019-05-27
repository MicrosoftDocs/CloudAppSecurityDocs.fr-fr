---
title: Intégrer Microsoft Defender ATP à Cloud App Security
description: Cet article décrit comment intégrer Microsoft Defender Advanced Threat Protection Cloud App Security pour améliorant la visibilité dans l’informatique fantôme et gestion des risques.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 12/14/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: b35ca44c-da8e-49ec-89d1-c076d123c14f
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: b49ab77b33548d6fd188eadde97294ceb6c62ca5
ms.sourcegitcommit: 235b7d5f1f49075c199b154abc38e51326c0493e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66173520"
---
# <a name="microsoft-defender-advanced-threat-protection-integration-with-microsoft-cloud-app-security"></a>Intégration de Microsoft Defender Advanced Threat Protection avec Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

Microsoft Cloud App Security s’intègre avec le module Microsoft Defender Advanced Threat Protection (ATP) en mode natif. L’intégration simplifie le lancement de Cloud Discovery, étend les fonctionnalités de Cloud Discovery au-delà de votre réseau d’entreprise et permet d’effectuer des recherches basées sur la machine. [Microsoft Defender Advanced Threat Protection (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) est une plateforme de sécurité pour une protection intelligente, détection, investigation et de réponse. Microsoft Defender ATP protège les points de terminaison contre les cybermenaces détecte avancées violations les attaques et les données, automatise les incidents de sécurité et améliore la posture de sécurité.

Microsoft Cloud App Security utilise les informations de trafic collectées par Microsoft Defender ATP sur les applications et services cloud est accessibles à partir de l’informatique Windows 10 machines. L’intégration vous permet d’exécuter Cloud Discovery sur n’importe quelle machine du réseau d’entreprise à l’aide du Wi-Fi public, en cas d’itinérance et d’accès à distance. Elle permet également d’effectuer des recherches basées sur la machine.

Après avoir identifié un utilisateur à risque, vous pouvez vérifier toutes les machines auxquelles l’utilisateur a accédé pour détecter des risques potentiels. Si vous identifiez une machine à risque, vérifiez tous les utilisateurs qui l’ont utilisée pour détecter des risques potentiels. Les journaux de vos points de terminaison routés vers Cloud App Security fournissent des informations utilisateur pour les activités de trafic. Activité du réseau Microsoft Defender ATP fournit le contexte de périphérique. Associez le contexte d’appareil au nom d’utilisateur pour disposer d’une image complète de votre réseau indiquant quel utilisateur a effectué quelle activité et à partir de quelle machine.

Microsoft Cloud App Security utilise l’intégration native avec Microsoft Defender ATP à exploiter les données relatives à cloud app service du trafic et les appareils Windows gérés. L’intégration est prête à l’emploi et ne nécessite pas de déploiement supplémentaire . Vous ne devez pas router ou mettre en miroir le trafic en provenance de vos points de terminaison ou effectuer des étapes d’intégration complexes.

> [!NOTE]
> Vous voulez découvrir Microsoft Defender ATP ? [Inscrivez-vous pour obtenir un essai gratuit](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-assignaccess-abovefoldlink).
>


## <a name="prerequisites"></a>Prérequis

- Licence Microsoft Cloud App Security
- Licence de Microsoft Defender ATP
- Ordinateurs Windows 10 exécutant la version 1809 ou une version ultérieure
- Activer/désactiver **Fonctionnalités d’évaluation** pour activer cette fonctionnalité dans Cloud App Security

## <a name="how-it-works"></a>Fonctionnement

Seul, Cloud App Security collecte des journaux de vos points de terminaison en utilisant des [journaux que vous chargez](create-snapshot-cloud-discovery-reports.md) ou en [configurant le chargement automatique de journaux](discovery-docker.md). Intégration native vous permet de tirer parti des journaux d’agent de Microsoft Defender ATP crée lorsqu’elle s’exécute sur Windows et surveille les transactions réseau. Utilisez ces informations pour la découverte Shadow IT sur les machines Windows de votre réseau.

Pour vous permettre d’effectuer la découverte de Cloud sur d’autres plateformes, il est préférable d’utiliser Cloud App Security [collecteur de journaux](discovery-docker.md), ainsi que de l’intégration de Microsoft Defender ATP pour surveiller vos machines Windows 10.

## <a name="how-to-integrate-microsoft-defender-atp-with-cloud-app-security"></a>Apprendre à intégrer Microsoft Defender ATP à Cloud App Security

Pour activer l’intégration à Cloud App Security à partir de Microsoft Defender ATP :

1. Dans le portail Microsoft Defender ATP, dans le volet de navigation, sélectionnez **le programme d’installation de préférences**.
2. Dans le menu **Paramètres**, sous **Général**, sélectionnez **Fonctionnalités avancées**.
3. Basculez **Microsoft Cloud App Security** sur **Activé**.
4. Cliquez sur **Enregistrer les préférences**.

>[!NOTE]
> Il faut jusqu’à deux heures après l’activation de l’intégration pour que les données s’affichent dans Cloud App Security.
>

   ![Paramètres WD ATP](./media/wdatp-settings.png)

## <a name="investigate-machines-in-cloud-app-security"></a>Examiner des ordinateurs dans Cloud App Security

Une fois que vous intégrez Microsoft Defender ATP avec Cloud App Security, vous pouvez examiner les données d’ordinateur découvert dans le tableau de bord Cloud Discovery.

1. Dans le portail Cloud App Security, cliquez sur **Cloud Discovery**, puis sur **Tableau de bord Cloud Discovery**.
2. Dans la barre de navigation supérieure, sous **Rapports continus**, sélectionnez **Utilisateurs de point de terminaison Win10**.
  ![Rapport WD ATP](./media/win10-dashboard-report.png)
3. En haut, vous voyez le nombre de machines détectées ajoutées après l’intégration.
4. Cliquez sur l’onglet **Ordinateurs**.
5. Vous pouvez explorer chaque machine répertoriée et utiliser les onglets pour afficher les données de la recherche. Recherchez des corrélations entre les machines, les utilisateurs, les adresses IP et les applications qui ont été impliqués dans des incidents :
   - **Vue d’ensemble**
      - Transactions : Informations sur le nombre de transactions qui ont eu lieu sur la machine pendant la période sélectionnée.
      - Trafic total : Informations sur la quantité de trafic totale (en Mo) pour la période sélectionnée.
     - Chargements : Informations sur la quantité de trafic totale (en Mo) chargée par la machine pendant la période sélectionnée.
     - Téléchargements : Informations sur la quantité de trafic totale (en Mo) téléchargée par la machine pendant la période sélectionnée.
   - **Applications découvertes**<br>
  Répertorie toutes les applications découvertes qui ont fait l’objet d’un accès par l’ordinateur.
   - **Historique de l’utilisateur**<br>
    Répertorie tous les utilisateurs qui se sont connectés à l’ordinateur.
   - **Historique de l’adresse IP**<br>
    Répertorie toutes les adresses IP qui ont été attribuées à l’ordinateur.
 ![Vue d’ensemble des ordinateurs](./media/machines-overview.png)
 
Comme avec n’importe quelle autre source Cloud Discovery, vous pouvez exporter les données du rapport sur les utilisateurs de point de terminaison Win10 pour un examen plus approfondi. 

> [!NOTE]
> - Defender ATP transfère les données à Cloud App Security en segments d’environ 4 Mo (transactions de point de terminaison de 4 000)
> - Si la limite de 4 Mo n’est pas atteinte dans l’heure, rapports Defender ATP toutes les transactions effectuées sur la dernière heure.

## <a name="related-videos"></a>Vidéos connexes

[Clichés instantanés IT discovery au-delà du réseau d’entreprise avec Microsoft Defender ATP et Cloud App Security](https://www.youtube.com/watch?v=f8hbvbY1Hnc)  

## <a name="next-steps"></a>Étapes suivantes 
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md) 

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)  
  
