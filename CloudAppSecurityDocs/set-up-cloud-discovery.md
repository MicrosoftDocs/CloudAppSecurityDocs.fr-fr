---
title: Déployer Cloud Discovery-Cloud App Security | Microsoft Docs
description: Cet article décrit la procédure de configuration pour l’obtention de Cloud Discovery.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: conceptual
ms.date: 8/15/2019
ms.collection: M365-security-compliance
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: fe21bbb39b52981d7aeba0839367d2fd54073983
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285683"
---
# <a name="set-up-cloud-discovery"></a>Configurer Cloud Discovery

*S’applique à : Microsoft Cloud App Security*

Cloud Discovery analyse vos journaux de trafic sur le catalogue d’applications Cloud de Microsoft Cloud App Security de plus de 16 000 applications Cloud. Les applications sont classées et évaluées en fonction de plus de 80 facteurs de risque afin de vous offrir une visibilité permanente de l’utilisation du Cloud, de l’occulter et de l’ombre des risques qu’il représente dans votre organisation.

## <a name="snapshot-and-continuous-risk-assessment-reports"></a>Rapports d’évaluation des risques et des instantanés

Il existe deux types de rapports que vous pouvez générer :

- **Rapports d’instantané** : fournit une visibilité ad hoc sur un ensemble de journaux de trafic que vous chargez manuellement à partir de vos pare-feu et proxys.

- **Rapports continus** : Analysez tous les journaux qui sont transférés à partir de votre réseau à l’aide de Cloud App Security. Ils offrent une meilleure visibilité sur toutes les données et identifient automatiquement l’utilisation anormale à l’aide du moteur de détection des anomalies Machine Learning ou à l’aide de stratégies personnalisées que vous définissez. Ces rapports peuvent être créés en se connectant des manières suivantes :

  - [Intégration de Microsoft Defender ATP](wdatp-integration.md): Cloud App Security s’intègre à Microsoft Defender-protection avancée contre les menaces (ATP) en mode natif, afin de simplifier le déploiement des Cloud Discovery, d’étendre les fonctionnalités de Cloud Discovery au-delà de votre réseau d’entreprise et d’activer l’investigation basée sur les machines.
  - [Collecteur](discovery-docker.md)de journaux : les collecteurs de journaux vous permettent d’automatiser facilement le chargement du journal à partir de votre réseau. Le collecteur de journaux s’exécute sur votre réseau et reçoit les journaux par le biais de Syslog ou FTP.
  - [Intégration de Zscaler](zscaler-integration.md): Si vous travaillez avec Cloud App Security et Zscaler, vous pouvez intégrer les deux produits pour améliorer votre expérience de Cloud Discovery de sécurité. Ensemble, Cloud App Security et Zscaler fournissent un déploiement transparent de Cloud Discovery, le blocage automatique des applications non approuvées et l’évaluation des risques directement dans le portail Zscaler.
  - [intégration de iboss](iboss-integration.md): Si vous travaillez avec Cloud App Security et iboss, vous pouvez intégrer les deux produits pour améliorer votre expérience de Cloud Discovery de sécurité. Ensemble, Cloud App Security et iboss fournissent un déploiement transparent de Cloud Discovery, le blocage automatique des applications non approuvées et l’évaluation des risques directement dans le portail iboss.

## <a name="log-process-flow-from-raw-data-to-risk-assessment"></a>Journalisation du processus de journalisation : des données brutes à l’évaluation des risques

Le processus de génération d’une évaluation des risques se compose des étapes suivantes. Le processus prend entre quelques minutes et plusieurs heures selon la quantité de données traitées.

- **Upload** : les journaux de trafic Web de votre réseau sont chargés sur le portail.

- **Parse** : Cloud App Security analyse et extrait les données de trafic à partir des journaux de trafic à l’aide d’un analyseur dédié pour chaque source de données.

- **Analyser** : les données de trafic sont analysées par rapport au catalogue d’applications Cloud afin d’identifier plus de 16 000 applications Cloud et d’évaluer leur score de risque. Les utilisateurs actifs et les adresses IP sont également identifiés dans le cadre de l’analyse.

- **Générer un rapport** : un rapport d’évaluation des risques des données extraites des fichiers journaux est généré.

>[!NOTE]
> Les données de rapport continues sont analysées deux fois par jour.

## Pare-feu et proxys pris en charge<a name="supported-firewalls-and-proxies"></a>

- Barracuda-pare-feu d’applications Web (W3C)
- Proxy de couche bleue, SG-journal d’accès (W3C)
- Check Point
- Cisco ASA avec un niveau de puissance
- Pare-feu Cisco ASA (pour les pare-feu Cisco ASA, il est nécessaire de définir le niveau d’information sur 6)
- Cisco Cloud Web Security
- Cisco FWSM
- WSA Cisco IronPort
- Cisco Meraki – journal des URL
- Clavister pare-feu (syslog)
- ContentKeeper
- Digital Arts i-FILTER
- Forcepoint
- Fortinet FortiGate
- Passerelle Cloud sécurisée iboss
- Juniper SRX
- Juniper SSG
- Passerelle Web sécurisée McAfee
- Microsoft Forefront Threat Management Gateway (W3C)
- Pare-feu de la série Palo Alto
- SonicWALL (anciennement Dell)
- Sophos SG
- Sophos XG
- Sophos Cyberoam
- Squid (commun)
- Squid (natif)
- Stormshield
- Websense-solutions de sécurité Web-rapport détaillé d’investigation (CSV)
- Websense-solutions de sécurité Web-Journal d’activité Internet (CEF)
- Zscaler

> [!NOTE]
> Cloud Discovery prend en charge les adresses IPv4 et IPv6.

Si votre journal n’est pas pris en charge, sélectionnez **autre** comme **source de données** et spécifiez l’appliance et le journal que vous essayez de charger. Votre journal est examiné par l’équipe d’analystes du Cloud Cloud App Security et vous êtes averti si la prise en charge de votre type de journal est ajoutée. Vous pouvez également définir un analyseur personnalisé qui correspond à votre format. Pour plus d’informations, consultez [utiliser un analyseur de journal personnalisé](custom-log-parser.md).

Attributs de données (selon la documentation du fournisseur) :

| Source de données | URL de l’application cible | Adresse IP de l’application cible | Nom d'utilisateur | Adresse IP d’origine | Trafic total | Octets chargés |
|----------------------------------------------|----------------------|----------------------|----------------------|----------------------|----------------------|----------------------|
| Barracuda | **Oui** | **Oui** | **Oui** | **Oui** | Non | Non |
| Revêtement bleu | **Oui** | Non | **Oui** | **Oui** | **Oui** | **Oui** |
| Point de contrôle | Non | **Oui** | Non | **Oui** | Non | Non |
| Cisco ASA (syslog) | Non | **Oui** | Non | **Oui** | **Oui** | Non |
| Cisco ASA avec un niveau de puissance | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** |
| Cisco Cloud Web Security |**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|
| Cisco FWSM | Non | **Oui** | Non | **Oui** | **Oui** | Non |
| WSA Cisco IronPort | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** |
| Cisco Meraki | **Oui** | **Oui** | Non | **Oui** | Non | Non |
| Clavister pare-feu (syslog) | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** |
| ContentKeeper | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** |
| SonicWall (anciennement Dell) | **Oui** | **Oui** | Non | **Oui** | **Oui** | **Oui** |
| Digital Arts i-FILTER | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** |
| ForcePoint LEEF |**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|
| ForcePoint Web Security Cloud |**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|
| FortiGate | Non | **Oui** | Non | **Oui** | **Oui** | **Oui** |
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
| Websense-rapport détaillé d’investigation (CSV) | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** |
| Websense-journal d’activité Internet (CEF) | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** |
| Zscaler | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** |

## <a name="next-steps"></a>Étapes suivantes :

> [!div class="nextstepaction"]
> [Créer des rapports d’instantanés Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

> [!div class="nextstepaction"]
> [Configurer le chargement automatique des journaux pour des rapports continus](configure-automatic-log-upload-for-continuous-reports.md)

> [!div class="nextstepaction"]
> [Utilisation des données Cloud Discovery](working-with-cloud-discovery-data.md)
