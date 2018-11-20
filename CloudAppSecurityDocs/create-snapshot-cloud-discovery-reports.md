---
title: Créer des rapports d’instantané de l’utilisation des applications cloud Cloud Discovery | Microsoft Docs
description: Cet article fournit des informations sur le chargement manuel de journaux pour créer un rapport d’instantané de vos applications Cloud Discovery.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/13/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: ecc1949d-c861-4636-952a-c3a260719bb5
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: ff22c10cdbb1736fde90922c7dc36b81f26558cc
ms.sourcegitcommit: 77850c6777504c2478611cb71a387e7fcc5f2551
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51597440"
---
# <a name="create-snapshot-cloud-discovery-reports"></a>Créer des rapports d’instantanés Cloud Discovery

*S’applique à : Microsoft Cloud App Security*

Il est important de charger un journal manuellement et de laisser Microsoft Cloud App Security l’analyser avant d’essayer d’utiliser le collecteur de journaux automatique. Pour plus d’informations sur le fonctionnement du collecteur de journaux et le format de journal attendu, consultez [Utilisation de journaux de trafic pour Cloud Discovery](#log-format).

Si vous n’avez pas encore de journal et que vous voulez voir à quoi ressemble un journal, téléchargez un exemple de fichier journal. Suivez la procédure ci-dessous pour voir à quoi doit ressembler votre journal.


Pour créer un rapport d’instantané :
  
1. Collectez les fichiers journaux de votre pare-feu et de votre proxy, via lesquels les utilisateurs de votre organisation accèdent à Internet. Veillez à collecter les journaux pendant les heures de pointe représentatives de toute l’activité utilisateur dans votre organisation.  
  
2. Dans le portail Cloud App Security, cliquez sur **Découvrir**, puis sur **Créer un rapport d’instantané**.  
  
   ![Créer un rapport de capture instantanée](./media/create-new-snapshot-report.png)
     
3. Renseignez **Nom du rapport** et **Description**
  
    ![Nouveau rapport d’instantané](./media/new-snapshot-report.png) 

4. Sélectionnez la **source de données** à partir de laquelle vous voulez charger les fichiers journaux.  
  
5. Examinez le format de votre journal pour vérifier qu’il est mis en forme correctement en vous basant sur l’exemple de journal que vous pouvez télécharger. Cliquez sur **Afficher et vérifier**, puis sur **Télécharger l’exemple de journal**. Comparez votre journal à l’exemple fourni pour vérifier qu’il est compatible. 

   ![Vérifier le format de votre journal](./media/cloud-discovery-snapshot-verify.png)  

   > [!NOTE]
   > L’exemple de format FTP est pris en charge dans les captures instantanées et le chargement automatique alors que syslog est pris en charge dans le chargement automatique uniquement.<br></br>
   Le téléchargement d’un exemple de journal télécharge un exemple de journal FTP.


6. **Choisissez les journaux de trafic** à charger. Vous pouvez charger jusqu’à 20 fichiers à la fois. Les fichiers compressés et zippés sont également pris en charge.  
  
7. Cliquez sur **Créer**.  

8. Une fois le chargement terminé, un message d’état s’affiche dans le coin supérieur droit de votre écran pour vous informer que le journal a correctement été chargé.  
  
9. Une fois que vos fichiers journaux sont chargés, un certain temps est nécessaire pour leur extraction et leur analyse.  
   Après le traitement de vos fichiers journaux, vous recevez un e-mail pour vous avertir que l’opération est terminée. 
  
10. Une bannière de notification apparaît dans la barre d’état en haut du **tableau de bord Cloud Discovery**. La bannière se met à jour avec l’état du traitement de vos fichiers journaux.  
    ![barre de menus du traitement des fichiers journaux](./media/processing-log-file-menu-bar.png) 
   
11. Une fois les journaux téléchargés, une notification vous informant que le traitement du fichier journal s’est terminé correctement doit s’afficher. À ce stade, vous pouvez afficher le rapport en cliquant sur le lien dans la barre d’état, ou en accédant à l’icône d’engrenage Paramètres et en sélectionnant **Paramètres Cloud Discovery**.   
  
     ![onglet Paramètres Cloud Discovery](./media/discovery-settings-tab.png)
12. Sélectionnez ensuite **Rapports d’instantanés**, puis votre rapport d’instantané.
 
     ![gestion des rapports d’instantanés](./media/snapshot-report-managment.png)

  
## Utilisation de journaux de trafic pour Cloud Discovery <a name="log-format"></a>
Cloud Discovery utilise les données de vos journaux de trafic. Plus le journal est détaillé, meilleure est la visibilité. Cloud Discovery nécessite des données de trafic web avec les attributs suivants :
- Date de la transaction
- Adresse IP source
- Utilisateur source (vivement recommandé)
- Adresse IP de destination
- URL de destination **recommandée** (les URL assurent une meilleure précision pour la détection d’applications cloud que les adresses IP)
- Quantité totale de données (les informations de données sont extrêmement précieuses)
- Quantité de données chargées ou téléchargées (fournit des informations sur les modèles d’utilisation des applications cloud)
- Action effectuée (autorisation/blocage)

Cloud Discovery ne peut pas afficher ni analyser des attributs qui ne se trouvent pas dans vos journaux.
Par exemple, le format de journal standard **Pare-feu Cisco ASA** ne contient pas le **nombre d’octets chargés par transaction**, le **nom d’utilisateur** et **l’URL cible** (il contient seulement l’adresse IP cible).
Par conséquent, ces attributs ne sont pas affichés dans les données Cloud Discovery pour ces journaux et la visibilité sur les applications cloud est limitée. Pour les pare-feu Cisco ASA, il est nécessaire de définir le niveau d’informations 6. 


Pour générer correctement un rapport Cloud Discovery, vos journaux de trafic doivent respecter les conditions suivantes :
1. La source de données est prise en charge (voir la liste ci-dessous).
2. Le format de journal correspond au format standard attendu (le format est vérifié lors du chargement par l’outil Log).
3. Les événements ne datent pas de plus de 90 jours.
4. Le fichier journal est valide et comprend des informations sur le trafic sortant.



## Pare-feu et proxys pris en charge <a name="supported-firewalls-and-proxies"></a>

- Barracuda - Web Application Firewall (W3C)
- Blue Coat Proxy SG - Journal d’accès (W3C)
- Check Point
- Pare-feu Cisco ASA (pour les pare-feu Cisco ASA, il est nécessaire de définir le niveau d’informations sur 6)
- Cisco ASA avec FirePOWER
- Cisco IronPort WSA
- Cisco ScanSafe
- Cisco Meraki – Journal des URL
- Clavister NGFW (Syslog)
- Digital Arts i-FILTER
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
- Websense - Solutions de sécurité web - Rapport détaillé d’investigation (CSV)
- Websense - Solutions de sécurité web - Journal d’activité Internet (CEF)
- Zscaler

> [!NOTE]
> Cloud Discovery prend en charge les adresses IPv4 et IPv6.

Si votre journal n’est pas pris en charge, sélectionnez **Autre** comme **Source de données**, et spécifiez l’appliance et le journal que vous essayez de charger. Votre journal est examiné par l’équipe d’analystes cloud de Cloud App Security et vous êtes averti si la prise en charge de votre type de journal est ajoutée. Vous pouvez également définir un analyseur personnalisé qui correspond à votre format. Pour plus d’informations, consultez [Utiliser un analyseur de journaux personnalisé](custom-log-parser.md).


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
|                SonicWall (anciennement Dell)                | <strong>Oui</strong> | <strong>Oui</strong> |          Non          | <strong>Oui</strong> | <strong>Oui</strong> | <strong>Oui</strong> |
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
     
 
## <a name="next-steps"></a>Étapes suivantes  
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
    
      
  