---
title: Déployer Cloud Discovery - Cloud App Security | Microsoft Docs
description: Cet article décrit la procédure de configuration pour rendre Cloud Discovery opérationnel.
author: ShlomoSagir-MS
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: conceptual
ms.date: 8/15/2019
ms.collection: M365-security-compliance
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 296abe6a227d6ab6c72e09cc993d8cf413770cec
ms.sourcegitcommit: 7eecf2f863c410abe0ba6eafd65777973de011cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2019
ms.locfileid: "69573037"
---
# <a name="set-up-cloud-discovery"></a>Configurer Cloud Discovery

*S’applique à : Microsoft Cloud App Security*

Cloud Discovery analyse vos journaux de trafic en s’appuyant sur le catalogue d’applications cloud Microsoft Cloud App Security, qui contient plus de 16 000 applications cloud. Les applications sont classées et évaluées en fonction de plus de 80 facteurs de risque afin de vous offrir une visibilité permanente de l’utilisation du Cloud, de l’occulter et de l’ombre des risques qu’il représente dans votre organisation.

## <a name="snapshot-and-continuous-risk-assessment-reports"></a>Rapports d’instantanés et continus d’évaluation des risques

Il existe deux types de rapports que vous pouvez générer :

- **Rapports d’instantanés** : ils fournissent une visibilité ad hoc sur un ensemble de journaux de trafic que vous chargez manuellement à partir de vos pare-feu et proxys.

- **Rapports continus** : ils analysent tous les journaux qui sont transférés à partir de votre réseau à l’aide de Cloud App Security. Ils offrent une meilleure visibilité sur toutes les données et identifient automatiquement toute utilisation anormale à l’aide du moteur de détection des anomalies Machine Learning ou des stratégies personnalisées que vous définissez. Ces rapports peuvent être créés en vous connectant des façons suivantes :

     - [Intégration de Microsoft Defender ATP](wdatp-integration.md): Cloud App Security s’intègre à Microsoft Defender-protection avancée contre les menaces (ATP) en mode natif, afin de simplifier le déploiement des Cloud Discovery, d’étendre les fonctionnalités Cloud Discovery au-delà de votre réseau d’entreprise et d’activer l’investigation basée sur les machines.
     - [Collecteur de journaux](discovery-docker.md) : Les collecteurs de journaux vous permettent d’automatiser facilement le chargement manuel des journaux de votre réseau. Le collecteur de journaux s’exécute sur votre réseau et reçoit les journaux par le biais de Syslog ou FTP.
     - [Intégration de Zscaler](zscaler-integration.md) : Si vous travaillez avec Cloud App Security et Zscaler, vous pouvez intégrer les deux produits pour améliorer la sécurité de votre expérience Cloud Discovery. Ensemble, Cloud App Security et Zscaler offrent un déploiement fluide de Cloud Discovery, le blocage automatique des applications non approuvées et l’évaluation des risques directement dans le portail de Zscaler.
     - [intégration de iboss](iboss-integration.md): Si vous utilisez Cloud App Security et iboss, vous pouvez intégrer ces deux produits pour rendre votre expérience Cloud Discovery encore plus sûre. Ensemble, Cloud App Security et iboss fournissent un déploiement transparent de Cloud Discovery, le blocage automatique des applications non approuvées et l’évaluation des risques directement dans le portail iboss.

## <a name="log-process-flow-from-raw-data-to-risk-assessment"></a>Flux du processus de journalisation : Des données brutes à l’évaluation des risques

Le processus de génération d’une évaluation des risques se compose des étapes suivantes. Le processus dure de quelques minutes à plusieurs heures en fonction de la quantité de données traitées.

- **Chargement** : Les journaux de trafic web de votre réseau sont chargés vers le portail.

- **Extraction** : Cloud App Security analyse et extrait les données de trafic depuis les journaux de trafic à l’aide d’un analyseur dédié pour chaque source de données.

- **Analyse** : Les données de trafic sont analysées par rapport au catalogue d’applications cloud dans le but d’identifier plus de 16 000 applications cloud et d’évaluer leur score de risque. Les utilisateurs et adresses IP actifs sont également identifiés dans le cadre de l’analyse.

- **Générer un rapport** : Un rapport d’évaluation des risques sur les données extraites des fichiers journaux est généré.

>[!NOTE]
> Les données des rapports continus sont analysées deux fois par jour.

## Pare-feu et proxys pris en charge <a name="supported-firewalls-and-proxies"></a>

- Barracuda - Web Application Firewall (W3C)
- Blue Coat Proxy SG - Journal d’accès (W3C)
- Check Point
- Cisco ASA avec FirePOWER
- Pare-feu Cisco ASA (pour les pare-feu Cisco ASA, il est nécessaire de définir le niveau d’informations sur 6)
- Cisco Cloud Web Security
- Cisco FWSM
- Cisco IronPort WSA
- Cisco Meraki – Journal des URL
- Clavister NGFW (Syslog)
- Digital Arts i-FILTER
- Forcepoint
- Fortinet Fortigate
- iboss Secure Cloud Gateway
- Juniper SRX
- Juniper SSG
- McAfee Secure Web Gateway
- Microsoft Forefront Threat Management Gateway (W3C)
- Pare-feu de la série Palo Alto
- SonicWall (anciennement Dell)
- Sophos SG
- Sophos XG
- Sophos Cyberoam
- Squid (commun)
- Squid (natif)
- Stormshield
- Websense - Solutions de sécurité web - Rapport détaillé d’investigation (CSV)
- Websense - Solutions de sécurité web - Journal d’activité Internet (CEF)
- Zscaler

> [!NOTE]
> Cloud Discovery prend en charge les adresses IPv4 et IPv6.

Si votre journal n’est pas pris en charge, sélectionnez **Autre** comme **Source de données**, et spécifiez l’appliance et le journal que vous essayez de charger. Votre journal est examiné par l’équipe d’analystes cloud de Cloud App Security et vous êtes averti si la prise en charge de votre type de journal est ajoutée. Vous pouvez également définir un analyseur personnalisé qui correspond à votre format. Pour plus d’informations, consultez [Utiliser un analyseur de journaux personnalisé](custom-log-parser.md).

Attributs de données (selon la documentation du fournisseur) :

| Source de données | URL de l’application cible | Adresse IP de l’application cible | Nom d'utilisateur | Adresse IP d’origine | Total du trafic | Octets chargés |
|----------------------------------------------|----------------------|----------------------|----------------------|----------------------|----------------------|----------------------|
| Barracuda | **Oui** | **Oui** | **Oui** | **Oui** | Non | Non |
| Blue Coat | **Oui** | Non | **Oui** | **Oui** | **Oui** | **Oui** |
| Point de contrôle | Non | **Oui** | Non | **Oui** | Non | Non |
| Cisco ASA (Syslog) | Non | **Oui** | Non | **Oui** | **Oui** | Non |
| Cisco ASA avec FirePOWER | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** |
| Cisco Cloud Web Security |**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|
| Cisco FWSM | Non | **Oui** | Non | **Oui** | **Oui** | Non |
| Cisco Ironport WSA | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** |
| Cisco Meraki | **Oui** | **Oui** | Non | **Oui** | Non | Non |
| Clavister NGFW (Syslog) | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** |
| SonicWall (anciennement Dell) | **Oui** | **Oui** | Non | **Oui** | **Oui** | **Oui** |
| Digital Arts i-FILTER | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** |
| ForcePoint LEEF |**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|
| ForcePoint Web Security Cloud |**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|
| Fortigate | Non | **Oui** | Non | **Oui** | **Oui** | **Oui** |
| Fortinet FortiOS |**Oui**|**Oui**|Non|**Oui**|**Oui**|**Oui**|
| iboss |**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|
| Juniper SRX | Non | **Oui** | Non | **Oui** | **Oui** | **Oui** |
| Juniper SSG | Non | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** |
| McAfee SWG | **Oui** | Non | Non | **Oui** | **Oui** | **Oui** |
| MS TMG | **Oui** | Non | **Oui** | **Oui** | **Oui** | **Oui** |
| Palo Alto Networks | Non | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** |
| Sophos | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** | Non |
| Squid (commun) | **Oui** | Non | **Oui** | **Oui** | Non | **Oui** |
| Squid (natif) | **Oui** | Non | **Oui** | **Oui** | Non | **Oui** |
| Stormshield | Non | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** |
| Websense - Rapport d’examen détaillé (CSV) | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** |
| Websense - Journal d’activité Internet (CEF) | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** |
| Zscaler | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** |

## <a name="next-steps"></a>Étapes suivantes

[Créer des rapports d’instantanés Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Configurer le chargement automatique des journaux pour des rapports continus](configure-automatic-log-upload-for-continuous-reports.md)

[Utilisation des données Cloud Discovery](working-with-cloud-discovery-data.md)
