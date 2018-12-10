---
title: Déployer Cloud Discovery avec Microsoft Cloud App Security | Microsoft Docs
description: Cet article décrit la procédure de configuration pour rendre Cloud Discovery opérationnel.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/30/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: a9b5bd8d-305b-4e93-9a4c-a4683ea09080
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 3918d5595f5f4c18279c02ef896616e436d12636
ms.sourcegitcommit: cae782d508db9d1a7c0c362e9a23e83f74d48b21
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2018
ms.locfileid: "52743622"
---
# <a name="set-up-cloud-discovery"></a>Configurer Cloud Discovery

*S’applique à : Microsoft Cloud App Security*

Cloud Discovery analyse vos journaux de trafic en s’appuyant sur le catalogue d’applications cloud Microsoft Cloud App Security, qui contient plus de 16 000 applications cloud. Les applications sont classées et évaluées selon plus de 70 facteurs de risque, afin de vous offrir une visibilité en continu de l’utilisation du cloud, de l’informatique fantôme et du risque que cette dernière représente pour votre organisation.

## <a name="snapshot-and-continuous-risk-assessment-reports"></a>Rapports d’instantanés et continus d’évaluation des risques 

Il existe deux types de rapports que vous pouvez générer : 

- **Rapports d’instantanés** : ils fournissent une visibilité ad hoc sur un ensemble de journaux de trafic que vous chargez manuellement à partir de vos pare-feu et proxys.

- **Rapports continus** : ils analysent tous les journaux qui sont transférés à partir de votre réseau à l’aide de Cloud App Security. Ils offrent une meilleure visibilité sur toutes les données et identifient automatiquement toute utilisation anormale à l’aide du moteur de détection des anomalies Machine Learning ou des stratégies personnalisées que vous définissez. Ces rapports peuvent être créés en vous connectant des façons suivantes :

  - [Intégration de Windows Defender ATP](wdatp-integration.md) : Cloud App Security s’intègre au module Windows Defender - Protection avancée contre les menaces (ATP) en mode natif pour simplifier le déploiement de Cloud Discovery, étendre les fonctionnalités de Cloud Discovery au-delà de votre réseau d’entreprise et activer l’examen basé sur l’ordinateur.
  - [Collecteur de journaux](discovery-docker.md) : les collecteurs de journaux vous permettent d’automatiser facilement le chargement manuel des journaux de votre réseau. Le collecteur de journaux s’exécute sur votre réseau et reçoit les journaux par le biais de Syslog ou FTP.
  - [Intégration Zscaler](zscaler-integration.md) : si vous travaillez avec Cloud App Security et Zscaler, vous pouvez intégrer les deux produits pour améliorer la sécurité de votre expérience Cloud Discovery. Ensemble, Cloud App Security et Zscaler offrent un déploiement fluide de Cloud Discovery, le blocage automatique des applications non approuvées et l’évaluation des risques directement dans le portail de Zscaler.

## <a name="log-process-flow-from-raw-data-to-risk-assessment"></a>Flux du processus de journalisation : des données brutes à l’évaluation des risques

Le processus de génération d’une évaluation des risques se compose des étapes suivantes. Le processus dure de quelques minutes à plusieurs heures en fonction de la quantité de données traitées.  

- **Chargement** : Les journaux de trafic web de votre réseau sont chargés vers le portail.  

- **Extraction** : Cloud App Security analyse et extrait les données de trafic depuis les journaux de trafic à l’aide d’un analyseur dédié pour chaque source de données.  

- **Analyse** : Les données de trafic sont analysées par rapport au catalogue d’applications cloud dans le but d’identifier plus de 16 000 applications cloud et d’évaluer leur score de risque. Les utilisateurs et adresses IP actifs sont également identifiés dans le cadre de l’analyse.  

- **Générer un rapport** : Un rapport d’évaluation des risques sur les données extraites des fichiers journaux est généré.


>[!NOTE]
> Les données des rapports continus sont analysées deux fois par jour.


## <a name="next-steps"></a>Étapes suivantes

[Créer des rapports d’instantanés Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Configurer le chargement automatique des journaux pour des rapports continus](configure-automatic-log-upload-for-continuous-reports.md)

[Utilisation des données Cloud Discovery](working-with-cloud-discovery-data.md)