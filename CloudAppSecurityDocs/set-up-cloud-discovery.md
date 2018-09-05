---
title: Déployer Cloud Discovery avec Microsoft Cloud App Security | Microsoft Docs
description: Cette rubrique décrit la procédure de configuration pour rendre Cloud Discovery opérationnel.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/15/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: a9b5bd8d-305b-4e93-9a4c-a4683ea09080
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 6d96dea5cfd7fd50c0730c59b13e5abb4121cdca
ms.sourcegitcommit: b439f29dc1d0aa8eec783ba45e3d517722a5ebe0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43016840"
---
*S’applique à : Microsoft Cloud App Security*


# <a name="set-up-cloud-discovery"></a>Configurer Cloud Discovery
Cloud Discovery analyse vos journaux de trafic en se basant sur le catalogue d’applications cloud de Microsoft Cloud App Security, qui contient plus de 16 000 applications cloud classées et évaluées selon plus de 70 facteurs de risque, afin de vous offrir une visibilité en continu de l’utilisation du cloud, du Shadow IT et du risque qu’il représente pour votre organisation.

## <a name="snapshot-and-continuous-risk-assessment-reports"></a>Rapports d’instantanés et continus d’évaluation des risques 

Il existe deux types de rapports que vous pouvez générer : 
- Les **rapports d’instantanés** fournissent une visibilité ad hoc sur un ensemble de journaux de trafic que vous chargez manuellement à partir de vos pare-feu et proxys.

- Les **rapports continus** analysent tous les journaux qui sont transférés à partir de votre réseau à l’aide du collecteur de journaux de Cloud App Security. Ils offrent une meilleure visibilité sur toutes les données et identifient automatiquement toute utilisation anormale à l’aide du moteur de détection des anomalies Machine Learning ou des stratégies personnalisées que vous définissez.

## <a name="log-process-flow-from-raw-data-to-risk-assessment"></a>Flux du processus de journalisation : des données brutes à l’évaluation des risques  
Le processus de génération d’une évaluation des risques comporte les étapes suivantes et nécessite entre quelques minutes et plusieurs heures selon la quantité de données traitée.  

-   **Chargement** : Les journaux de trafic web de votre réseau sont chargés vers le portail.  

-   **Extraction** : Cloud App Security analyse et extrait les données de trafic depuis les journaux de trafic à l’aide d’un analyseur dédié pour chaque source de données.  

-   **Analyse** : Les données de trafic sont analysées par rapport au catalogue d’applications cloud dans le but d’identifier plus de 16 000 applications cloud et d’évaluer leur score de risque. Les utilisateurs et adresses IP actifs sont également identifiés dans le cadre de l’analyse.  

-   **Générer un rapport** : Un rapport d’évaluation des risques sur les données extraites des fichiers journaux est généré.   


>[!NOTE]
>- Les données des rapports continus sont analysées deux fois par jour.
>- Le collecteur de journaux compresse les données avant leur chargement. Le trafic sortant du collecteur de journaux a un volume égal à 10 % de celui des journaux de trafic reçus. 

## <a name="using-traffic-logs-for-cloud-discovery"></a>Utiliser les journaux de trafic pour Cloud Discovery
Cloud Discovery utilise les données dans vos journaux de trafic. Plus le journal est détaillé, meilleure est la visibilité. Cloud Discovery nécessite des données de trafic web avec les attributs suivants :
- Date de la transaction
- Adresse IP source
- Utilisateur source (vivement recommandé)
- Adresse IP de destination
- URL de destination **recommandée** (les URL assurent une meilleure précision pour la détection d’applications cloud que les adresses IP)
- Quantité totale de données (les informations de données sont extrêmement précieuses)
- Quantité de données chargées ou téléchargées (fournit des informations sur les modèles d’utilisation des applications cloud)
- Action effectuée (autorisation/blocage)

Cloud Discovery ne peut pas afficher ni analyser des attributs qui ne sont pas inclus dans vos journaux.
Par exemple, le format de journal standard **Pare-feu Cisco ASA** ne contient pas le **nombre d’octets chargés par transaction** ni le **nom d’utilisateur**, et ne contient pas l’**URL cible** (mais uniquement l’adresse IP cible).
Par conséquent, ces attributs ne sont pas affichés dans les données Cloud Discovery pour ces journaux et la visibilité sur les applications cloud est limitée. Pour les pare-feu Cisco ASA, il est nécessaire de définir le niveau d’informations 6. 


Pour générer correctement un rapport Cloud Discovery, vos journaux de trafic doivent respecter les conditions suivantes :
1.  La source de données est prise en charge (voir la liste ci-dessous).
2.  Le format de journal correspond au format standard attendu (cela sera vérifié au moment du chargement par l’outil Log).
3.  Les événements ne datent pas de plus de 90 jours.
4.  Le fichier journal est valide et comprend des informations sur le trafic sortant.



## Pare-feu et proxys pris en charge <a name="supported-firewalls-and-proxies"></a>

- Barracuda - Web Application Firewall (W3C)
- Blue Coat Proxy SG - Journal d’accès (W3C)
- Check Point
- Pare-feu Cisco ASA (pour les pare-feu Cisco ASA, il est nécessaire de définir le niveau d’informations 6)
- Cisco ASA avec FirePOWER
- Cisco IronPort WSA
- Cisco ScanSafe
- Cisco Meraki – Journal des URL
- Clavister NGFW (Syslog)
- Dell Sonicwall
- Digital Arts i-FILTER
- Fortinet Fortigate
- iboss Secure Cloud Gateway
- Juniper SRX
- Juniper SSG
- McAfee Secure Web Gateway
- Microsoft Forefront Threat Management Gateway (W3C)
- Pare-feu de la série Palo Alto
- Sophos SG
- Sophos XG
- Sophos Cyberoam
- Squid (commun)
- Squid (natif)
- Websense - Solutions de sécurité web - Rapport détaillé d’investigation (CSV)
- Websense - Solutions de sécurité web - Journal d’activité Internet (CEF)
- Zscaler

> [!NOTE]
> Cloud Discovery prend en charge les adresses IPv4 et IPv6.

Si votre journal n’est pas pris en charge, sélectionnez **Autre** comme **Source de données** et spécifiez l’appareil et le journal que vous essayez de charger. Votre journal est examiné par l’équipe d’analystes cloud Cloud App Security et vous êtes averti si la prise en charge de votre type de journal est ajoutée. Vous pouvez également définir un analyseur personnalisé qui correspond à votre format. Pour plus d’informations, consultez [Utiliser un analyseur de journaux personnalisé](custom-log-parser.md).


Attributs de données (selon la documentation du fournisseur) :


|                 Source de données                  |    URL de l’application cible    |    Adresse IP de l’application cible     |       Nom d'utilisateur       |      Adresse IP d’origine       |    Total du trafic     |    Octets chargés    |
|----------------------------------------------|----------------------|----------------------|----------------------|----------------------|----------------------|----------------------|
|                  Barracuda                   | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> |          Non          |          Non          |
|                  Blue Coat                   | <strong>Oui</strong> |          Non          | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> |
|                  Point de contrôle                  |          Non          | <strong>Oui</strong> |          Non          | <strong>Oui</strong> |          Non          |          Non          |
|              Cisco ASA (Syslog)              |          Non          | <strong>Oui</strong> |          Non          | <strong>Oui</strong> | <strong>Oui</strong> |          Non          |
|           Cisco ASA avec FirePOWER           | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> |
|                  Cisco FWSM                  |          Non          | <strong>Oui</strong> |          Non          | <strong>Oui</strong> | <strong>Oui</strong> |          Non          |
|              Cisco Ironport WSA              | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> |
|                 Cisco Meraki                 | <strong>Oui</strong> | <strong>Oui</strong> |          Non          | <strong>Oui</strong> |          Non          |          Non          |
|           Clavister NGFW (Syslog)            | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> |
|                Dell SonicWall                | <strong>Oui</strong> | <strong>Oui</strong> |          Non          | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> |
|            Digital Arts i-FILTER             | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> |
|                  Fortigate                   |          Non          | <strong>Oui</strong> |          Non          | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> |
|                 Juniper SRX                  |          Non          | <strong>Oui</strong> |          Non          | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> |
|                 Juniper SSG                  |          Non          | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> |
|                  McAfee SWG                  | <strong>Oui</strong> |          Non          |          Non          | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> |
|                    MS TMG                    | <strong>Oui</strong> |          Non          | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> |
|              Palo Alto Networks              |          Non          | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> |
|                    Sophos                    | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> |          Non          |
|                Squid (commun)                | <strong>Oui</strong> |          Non          | <strong>Oui</strong> | <strong>Oui</strong> |          Non          | <strong>Oui</strong> |
|                Squid (natif)                | <strong>Oui</strong> |          Non          | <strong>Oui</strong> | <strong>Oui</strong> |          Non          | <strong>Oui</strong> |
| Websense - Rapport d’examen détaillé (CSV) | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> |
|    Websense - Journal d’activité Internet (CEF)    | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> |
|                   Zscaler                    | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> |

## <a name="see-also"></a>Voir aussi

[Créer des rapports d’instantanés Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Configurer le chargement automatique des journaux pour des rapports continus](configure-automatic-log-upload-for-continuous-reports.md)

[Utilisation des données Cloud Discovery](working-with-cloud-discovery-data.md)