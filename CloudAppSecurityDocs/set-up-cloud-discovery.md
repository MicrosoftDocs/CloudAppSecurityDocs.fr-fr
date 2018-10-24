---
title: Déployer Cloud Discovery avec Microsoft Cloud App Security | Microsoft Docs
description: Cette rubrique décrit la procédure de configuration pour rendre Cloud Discovery opérationnel.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/7/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: a9b5bd8d-305b-4e93-9a4c-a4683ea09080
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: cbc8999419f9c316323227c515fe111310231a9a
ms.sourcegitcommit: 53a1c990ff06674c26563a9ebcb1979818c3c063
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2018
ms.locfileid: "48881803"
---
*S’applique à : Microsoft Cloud App Security*


# <a name="set-up-cloud-discovery"></a>Configurer Cloud Discovery
Cloud Discovery analyse vos journaux de trafic en se basant sur le catalogue d’applications cloud de Microsoft Cloud App Security, qui contient plus de 16 000 applications cloud classées et évaluées selon plus de 70 facteurs de risque, afin de vous offrir une visibilité en continu de l’utilisation du cloud, du Shadow IT et du risque qu’il représente pour votre organisation.

## <a name="snapshot-and-continuous-risk-assessment-reports"></a>Rapports d’instantanés et continus d’évaluation des risques 

Il existe deux types de rapports que vous pouvez générer : 
- Les **rapports d’instantanés** fournissent une visibilité ad hoc sur un ensemble de journaux de trafic que vous chargez manuellement à partir de vos pare-feu et proxys.

- Les **rapports continus** analysent tous les journaux qui sont transférés à partir de votre réseau à l’aide de Cloud App Security. Ils offrent une meilleure visibilité sur toutes les données et identifient automatiquement toute utilisation anormale à l’aide du moteur de détection des anomalies Machine Learning ou des stratégies personnalisées que vous définissez. Ces rapports peuvent être créés en vous connectant des façons suivantes :
  - [Intégration de Windows Defender ATP](wdatp-integration.md) : Cloud App Security s’intègre au module Windows Defender - Protection avancée contre les menaces (ATP) en mode natif pour simplifier le déploiement de Cloud Discovery, étendre les fonctionnalités de Cloud Discovery au-delà de votre réseau d’entreprise et activer l’examen basé sur l’ordinateur.
  - [Collecteur de journaux]( ) :
  - [Intégration de Zscaler](zscaler-integration.md) : 

## <a name="log-process-flow-from-raw-data-to-risk-assessment"></a>Flux du processus de journalisation : des données brutes à l’évaluation des risques  
Le processus de génération d’une évaluation des risques comporte les étapes suivantes et nécessite entre quelques minutes et plusieurs heures selon la quantité de données traitée.  

-   **Chargement** : Les journaux de trafic web de votre réseau sont chargés vers le portail.  

-   **Extraction** : Cloud App Security analyse et extrait les données de trafic depuis les journaux de trafic à l’aide d’un analyseur dédié pour chaque source de données.  

-   **Analyse** : Les données de trafic sont analysées par rapport au catalogue d’applications cloud dans le but d’identifier plus de 16 000 applications cloud et d’évaluer leur score de risque. Les utilisateurs et adresses IP actifs sont également identifiés dans le cadre de l’analyse.  

-   **Générer un rapport** : Un rapport d’évaluation des risques sur les données extraites des fichiers journaux est généré.   


>[!NOTE]
>- Les données des rapports continus sont analysées deux fois par jour.
> 


## <a name="see-also"></a>Voir aussi

[Créer des rapports d’instantanés Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Configurer le chargement automatique des journaux pour des rapports continus](configure-automatic-log-upload-for-continuous-reports.md)

[Utilisation des données Cloud Discovery](working-with-cloud-discovery-data.md)