---
title: "Déployer Cloud Discovery | Microsoft Docs"
description: "Cette rubrique décrit la procédure de configuration pour rendre Cloud Discovery opérationnel."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/26/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: a9b5bd8d-305b-4e93-9a4c-a4683ea09080
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 99ad61811b68b47ac62b4bac83b611e535d4a6be
ms.openlocfilehash: 2070adb26a6b23cd0d699f3c4b9241819e24928d


---

# <a name="set-up-cloud-discovery"></a>Configurer Cloud Discovery
Cloud Discovery analyse vos journaux de trafic par rapport au catalogue de plus de 13 000 applications cloud de Cloud App Security qui sont classées et évaluées selon plus de 50 attributs pour que vous bénéficiiez d’une visibilité permanente sur l’utilisation du cloud, l’informatique fantôme et le risque que ce dernier représente pour votre organisation.
Le **catalogue d’applications cloud** évalue les risques pour vos applications cloud selon les certifications réglementaires, les normes du secteur et les bonnes pratiques. Quatre processus complémentaires s’exécutent dans le catalogue d’applications cloud pour le tenir à jour :
1.  Extraction de données automatisée directement à partir de l’application cloud (pour les attributs tels que la conformité SOC 2).
2.  Extraction de données avancée automatisée pour les données par les algorithmes de Cloud App Security (pour les attributs tels que les en-têtes de sécurité HTTP).
3.  Analyse en continu par l’équipe d’analystes cloud Cloud App Security (pour les attributs tels que le chiffrement au repos).
4.  Demandes de révisions basées sur le client, en fonction des demandes de soumissions du client des modifications à apporter au catalogue d’applications cloud. Toutes les demandes sont examinées par notre équipe d’analystes cloud et mises à jour en fonction de leurs conclusions.
  
## <a name="cloud-discovery-data-anonymization"></a>Anonymisation des données Cloud Discovery

L’anonymisation de données Cloud Discovery vous permet de protéger la confidentialité des utilisateurs. Une fois que le journal des données est téléchargé sur le portail Cloud App Security, il est purgé et toutes les informations des noms d’utilisateur sont remplacées par des noms d’utilisateur chiffrés. De cette façon, toutes les activités cloud restent anonymes. Pour plus d’informations, consultez [Anonymisation de Cloud Discovery](cloud-discovery-anonymizer.md).

## <a name="snapshot-and-continuous-risk-assessment-reports"></a>Rapports d’instantanés et continus d’évaluation des risques 

Il existe deux types de rapports que vous pouvez générer : 
- Les **rapports d’instantanés** fournissent une visibilité ad hoc sur un ensemble de journaux de trafic que vous chargez manuellement à partir de vos pare-feu et proxys.
 
- Les **rapports continus** analysent tous les journaux qui sont transférés à partir de votre réseau à l’aide du collecteur de journaux de Cloud App Security. Ils offrent une meilleure visibilité sur toutes les données et identifient automatiquement toute utilisation anormale à l’aide du moteur de détection des anomalies Machine Learning ou des stratégies personnalisées que vous définissez.
 
## <a name="log-process-flow-from-raw-data-to-risk-assessment"></a>Flux du processus de journalisation : des données brutes à l’évaluation des risques  
Le processus de génération d’une évaluation des risques comporte les étapes suivantes et nécessite entre quelques minutes et plusieurs heures selon la quantité de données traitée.  
  
-   **Chargement** : Les journaux de trafic web de votre réseau sont chargés vers le portail.  
  
-   **Extraction** : Cloud App Security analyse et extrait les données de trafic depuis les journaux de trafic à l’aide d’un analyseur dédié pour chaque source de données.  
  
-   **Analyse** : Les données de trafic sont analysées par rapport au catalogue d’applications cloud dans le but d’identifier plus de 13 000 applications cloud et d’évaluer leur score de risque. Les utilisateurs et adresses IP actifs sont également identifiés dans le cadre de l’analyse.  
  
-   **Générer un rapport** : Un rapport d’évaluation des risques sur les données extraites des fichiers journaux est généré.   
 
 
>[!NOTE]
>Les données des rapports continus sont analysées deux fois par jour.
 
## <a name="using-traffic-logs-for--cloud-discovery"></a>Utilisation de journaux de trafic pour Cloud Discovery
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
Par exemple, le format de journal standard **Pare-feu Cisco ASA** ne contient pas la **quantité d’octets chargés par transaction** ni le **nom d’utilisateur**, et ne contient pas l’**URL cible** (mais uniquement l’adresse IP cible).
Par conséquent, ces attributs sont affichés dans les données Cloud Discovery pour ces journaux et la visibilité sur les applications cloud est limitée. Pour les pare-feu Cisco ASA, il est nécessaire de définir le niveau d’informations 6. 
 

Pour générer correctement un rapport Cloud Discovery, vos journaux de trafic doivent respecter les conditions suivantes :
1.  La source de données est prise en charge (voir la liste ci-dessous).
2.  Le format de journal correspond au format standard attendu (cela sera vérifié au moment du chargement par l’outil Log).
3.  Les événements ne datent pas de plus de 90 jours.
4.  Le fichier journal est valide et comprend des informations sur le trafic sortant.
 
## <a name="supported-firewalls-and-proxies"></a>Pare-feu et proxys pris en charge
- Blue Coat Proxy SG - Journal d’accès (W3C)
- Check Point
- Pare-feu Cisco ASA (pour les pare-feu Cisco ASA, il est nécessaire de définir le niveau d’informations 6)
- Cisco IronPort WSA
- Cisco ScanSafe
- Cisco Merkai – Journal des URL
- Dell Sonicwall
- Fortiner Fortigate
- Juniper SRX
- McAfee Secure Web Gateway
- Microsoft Forefront Threat Management Gateway (W3C)
- Pare-feu de la série Palo Alto
- Sophos SG
- Sophos Cyberoam
- Squid (commun)
- Squid (natif)
- Websense - Solutions de sécurité web - Rapport détaillé d’investigation (CSV)
- Websense - Solutions de sécurité web - Journal d’activité Internet (CEF)
- Zscaler


Si votre journal n’est pas pris en charge, sélectionnez **Autre** comme **Source de données** et spécifiez l’appareil et le journal que vous essayez de charger. Votre journal est examiné par l’équipe d’analystes cloud Cloud App Security et vous êtes averti si la prise en charge de votre type de journal est ajoutée. 


Attributs de données (selon la documentation du fournisseur) :

|Source de données|URL de l’application cible|Adresse IP de l’application cible|Nom d'utilisateur|Adresse IP d’origine|Total du trafic|Octets chargés|
|----|----|----|-----|----|----|----|
|Blue Coat|**Oui**|Non|**Oui**|**Oui**|**Oui**|**Oui**|
|Point de contrôle|Non|**Oui**|Non|**Oui**|Non|Non|
|Cisco ASA|Non|**Oui**|Non|**Oui**|**Oui**|Non|
|Cisco FWSM|Non|**Oui**|Non|**Oui**|**Oui**|Non|
|Cisco Ironport WSA|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|
|Cisco Scansfe|**Oui**|Non|**Oui**|**Oui**|**Oui**|**Oui**|
|Dell SonicWall|**Oui**|**Oui**|Non|**Oui**|**Oui**|**Oui**|
|Fortigate|Non|**Oui**|Non|**Oui**|**Oui**|**Oui**|
|Juniper SRX|Non|**Oui**|Non|**Oui**|**Oui**|**Oui**|
|McAfee SWG|**Oui**|Non|Non|**Oui**|**Oui**|**Oui**|
|Meraki|**Oui**|**Oui**|Non|**Oui**|Non|Non|
|MS TMG|**Oui**|Non|**Oui**|**Oui**|**Oui**|**Oui**|
|PAN|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|
|Sophos|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|Non|
|Websense - Rapport d’examen détaillé (CSV)|**Oui**|Non|Non|**Oui**|Non|Non|
|Websense - Journal d’activité Internet (CEF)|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|
|Zscaler|**Oui**|Non|**Oui**|Non|**Oui**|Non|


## <a name="see-also"></a>Voir aussi
 
[Créer des rapports d’instantanés Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Configurer le chargement automatique des journaux pour des rapports continus](configure-automatic-log-upload-for-continuous-reports.md)

[Utilisation des données Cloud Discovery](working-with-cloud-discovery-data.md)
  
  


<!--HONumber=Dec16_HO4-->


