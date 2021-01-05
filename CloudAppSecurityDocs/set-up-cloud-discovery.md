---
title: Déployer Cloud Discovery
description: Cet article décrit la procédure de configuration pour rendre Cloud Discovery opérationnel.
ms.date: 08/09/2020
ms.topic: how-to
ms.openlocfilehash: e4ac4ce0e6148ca37c4c666b94da6779578ca77a
ms.sourcegitcommit: 16a65ab2c8ca778d0b3cfa97b847af4c812363b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/03/2021
ms.locfileid: "97855232"
---
# <a name="set-up-cloud-discovery"></a>Configurer Cloud Discovery

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Cloud Discovery analyse vos journaux de trafic en s’appuyant sur le catalogue d’applications cloud Microsoft Cloud App Security, qui contient plus de 16 000 applications cloud. Les applications sont classées et évaluées en fonction de plus de 80 facteurs de risque afin de vous offrir une visibilité permanente de l’utilisation du Cloud, de l’occulter et de l’ombre des risques qu’il représente dans votre organisation.

## <a name="snapshot-and-continuous-risk-assessment-reports"></a>Rapports d’instantanés et continus d’évaluation des risques

Vous pouvez générer les types de rapports suivants :

- **Rapports d’instantanés** : ils fournissent une visibilité ad hoc sur un ensemble de journaux de trafic que vous chargez manuellement à partir de vos pare-feu et proxys.

- **Rapports continus** : ils analysent tous les journaux qui sont transférés à partir de votre réseau à l’aide de Cloud App Security. Ils offrent une meilleure visibilité sur toutes les données et identifient automatiquement toute utilisation anormale à l’aide du moteur de détection des anomalies Machine Learning ou des stratégies personnalisées que vous définissez. Ces rapports peuvent être créés en vous connectant des façons suivantes :

  - [**Intégration de Microsoft Defender pour les points de terminaison**](mde-integration.md): Cloud App Security s’intègre à Defender pour le point de terminaison en mode natif, afin de simplifier le déploiement des Cloud Discovery, d’étendre les fonctionnalités Cloud Discovery au-delà de votre réseau d’entreprise et d’activer l’investigation basée sur les machines.
  - [**Collecteur**](discovery-docker.md)de journaux : les collecteurs de journaux vous permettent d’automatiser facilement le chargement du journal à partir de votre réseau. Le collecteur de journaux s’exécute sur votre réseau et reçoit les journaux par le biais de Syslog ou FTP.
  - **Secure Web Gateway (SWG)**: Si vous travaillez avec Cloud App Security et l’un des SWGs suivants, vous pouvez intégrer les produits pour améliorer votre expérience de Cloud Discovery de sécurité. Ensemble, Cloud App Security et SWGs offrent un déploiement transparent de Cloud Discovery, le blocage automatique des applications non approuvées et l’évaluation des risques directement sur le portail de SWG.
    - [Intégration de Zscaler](zscaler-integration.md)
    - [intégration de iboss](iboss-integration.md)
    - [Intégration de Corrata](corrata-integration.md)
    - [Intégration de la sécurité Menlo](menlo-integration.md)

- **[Api Cloud Discovery](api-discovery.md)** : utilisez l’API Cloud Discovery de Cloud App Security pour automatiser le chargement du journal du trafic et bénéficier d’une évaluation automatisée des Cloud Discovery et des rapports. Vous pouvez également utiliser l’API pour [générer des scripts de bloc](api-discovery-script.md) et rationaliser les contrôles d’application directement sur votre appliance réseau.

## <a name="log-process-flow-from-raw-data-to-risk-assessment"></a>Flux du processus de journalisation : des données brutes à l’évaluation des risques

Le processus de génération d’une évaluation des risques se compose des étapes suivantes. Le processus dure de quelques minutes à plusieurs heures en fonction de la quantité de données traitées.

- **Chargement** : Les journaux de trafic web de votre réseau sont chargés vers le portail.

- **Extraction** : Cloud App Security analyse et extrait les données de trafic depuis les journaux de trafic à l’aide d’un analyseur dédié pour chaque source de données.

- **Analyse** : Les données de trafic sont analysées par rapport au catalogue d’applications cloud dans le but d’identifier plus de 16 000 applications cloud et d’évaluer leur score de risque. Les adresses IP et les utilisateurs actifs sont également identifiés dans le cadre de l’analyse.

- **Générer un rapport** : Un rapport d’évaluation des risques sur les données extraites des fichiers journaux est généré.

>[!NOTE]
> Les données de rapport continues sont analysées quatre fois par jour.

## <a name="supported-firewalls-and-proxies"></a>Pare-feu et proxys pris en charge <a name="supported-firewalls-and-proxies"></a>

- Barracuda - Pare-feu d’application web (W3C)
- Blue Coat Proxy SG - Journal d’accès (W3C)
- Check Point
- Cisco ASA avec FirePOWER
- Pare-feu Cisco ASA (pour les pare-feu Cisco ASA, il est nécessaire de définir le niveau d’informations sur 6)
- Cisco Cloud Web Security
- Cisco FWSM
- Cisco IronPort WSA
- Cisco Meraki – journal des URL
- Clavister NGFW (Syslog)
- ContentKeeper
- Corrata
- Digital Arts i-FILTER
- Forcepoint
- Fortinet Fortigate
- iboss Secure Cloud Gateway
- Juniper SRX
- Juniper SSG
- McAfee Secure Web Gateway
- Sécurité Menlo (CEF)
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
- WatchGuard
- Zscaler

> [!NOTE]
> Cloud Discovery prend en charge les adresses IPv4 et IPv6.

Si votre journal n’est pas pris en charge, ou si vous utilisez un format de journal nouvellement publié à partir de l’une des sources de données prises en charge et que le téléchargement échoue, sélectionnez **autre** comme **source de données** et spécifiez l’appliance et le journal que vous essayez de charger. Votre journal est examiné par l’équipe d’analystes cloud de Cloud App Security et vous êtes averti si la prise en charge de votre type de journal est ajoutée. Vous pouvez également définir un analyseur personnalisé qui correspond à votre format. Pour plus d’informations, consultez [Utiliser un analyseur de journaux personnalisé](custom-log-parser.md).

> [!NOTE]
> La liste suivante d’appliances prises en charge peut ne pas fonctionner avec les formats de journal récemment publiés. Si vous utilisez un format récemment publié et que le téléchargement échoue, [Utilisez un analyseur de journal personnalisé](custom-log-parser.md) et, si nécessaire, ouvrez un dossier de support.

Attributs de données (selon la documentation du fournisseur) :

| Source de données | URL de l’application cible | Adresse IP de l’application cible | Nom d’utilisateur | Adresse IP d’origine | Total du trafic | Octets chargés |
|----------------------------------------------|----------------------|----------------------|----------------------|----------------------|----------------------|----------------------|
| Barracuda | **Oui** | **Oui** | **Oui** | **Oui** | Non | Non |
| Blue Coat | **Oui** | Non | **Oui** | **Oui** | **Oui** | **Oui** |
| Check Point | Non | **Oui** | Non | **Oui** | Non | Non |
| Cisco ASA (Syslog) | Non | **Oui** | Non | **Oui** | **Oui** | Non |
| Cisco ASA avec FirePOWER | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** |
| Cisco Cloud Web Security |**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|
| Cisco FWSM | Non | **Oui** | Non | **Oui** | **Oui** | Non |
| Cisco Ironport WSA | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** |
| Cisco Meraki | **Oui** | **Oui** | Non | **Oui** | Non | Non |
| Clavister NGFW (Syslog) | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** |
| ContentKeeper | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** |
| Corrata | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** |
| SonicWall (anciennement Dell) | **Oui** | **Oui** | Non | **Oui** | **Oui** | **Oui** |
| Digital Arts i-FILTER | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** |
| ForcePoint LEEF |**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|
| ForcePoint Web Security Cloud\* |**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|
| Fortigate | Non | **Oui** | Non | **Oui** | **Oui** | **Oui** |
| Fortinet FortiOS |**Oui**|**Oui**|Non|**Oui**|**Oui**|**Oui**|
| iboss |**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|
| Juniper SRX | Non | **Oui** | Non | **Oui** | **Oui** | **Oui** |
| Juniper SSG | Non | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** |
| McAfee SWG | **Oui** | Non | Non | **Oui** | **Oui** | **Oui** |
| Sécurité Menlo (CEF) | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** |
| MS TMG | **Oui** | Non | **Oui** | **Oui** | **Oui** | **Oui** |
| Palo Alto Networks | Non | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** |
| Sophos | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** | Non |
| Squid (commun) | **Oui** | Non | **Oui** | **Oui** | **Oui** | Non |
| Squid (natif) | **Oui** | Non | **Oui** | **Oui** | Non | Non |
| Stormshield | Non | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** |
| Websense - Rapport d’examen détaillé (CSV) | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** |
| Websense - Journal d’activité Internet (CEF) | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** |
| WatchGuard | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** |
| Zscaler | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** | **Oui** |

\* Les versions 8,5 et ultérieures du Cloud de sécurité Web Forcepoint ne sont pas prises en charge

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Créer des rapports d’instantanés Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

> [!div class="nextstepaction"]
> [Configurer le chargement automatique des journaux pour des rapports continus](discovery-docker.md)

> [!div class="nextstepaction"]
> [Utilisation des données Cloud Discovery](working-with-cloud-discovery-data.md)
