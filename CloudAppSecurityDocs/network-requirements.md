---
title: "Configuration requise du réseau Cloud App Security | Microsoft Docs"
description: "Cette rubrique décrit les adresses IP et les ports à ouvrir pour fonctionner avec Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 9/17/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 4de606f2-a09e-4e48-a578-e223de8b5e69
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 82bdda2ab26fa1c954edb5186eeb37d909d65e64
ms.sourcegitcommit: d012fc1a099773bd9e9dc61906faab68dae0e996
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2017
---
# <a name="network-requirements"></a>Configuration requise pour le réseau

Cette rubrique fournit une liste de ports et d’adresses IP que vous devez autoriser et ajouter à la liste verte pour qu’ils fonctionnent avec Cloud App Security. 

Pour savoir à quel centre de données Cloud App Security vous êtes connecté, consultez [Jetons d’API](api-tokens.md)



## <a name="portal-access-siem-agent-authentication-gateway-and-log-collector"></a>Accès au portail, agent SIEM, passerelle d’authentification et collecteur de journaux

Si vous voulez accéder au portail et à la passerelle d’authentification, autoriser Cloud App Security à se connecter à votre agent SIEM et permettre au collecteur de journaux Cloud App Security de s’exécuter, il est nécessaire d’ajouter le **port 443 sortant** pour les adresses IP suivantes à la liste verte de votre pare-feu :  


> [!div class="mx-tableFixed"]
|Centre de données|Adresses IP|  
|----|----|
|US1|13.91.91.243<br></br>52.183.75.62|
|EU1|52.174.56.180<br></br>13.80.125.22|

## <a name="app-connector-access-and-external-dlp-integration"></a>Accès au connecteur d’application et intégration DLP externe

Pour se connecter à des applications tierces et intégrer des solutions DLP externes, autorisez Cloud App Security à se connecter à ces adresses IP :


> [!div class="mx-tableFixed"]
|Centre de données|Adresses IP|  
|----|----|
|US1|104.209.35.177<br></br>13.91.98.185<br></br>40.118.211.172<br></br>13.93.216.68<br></br>13.91.61.249<br></br>13.93.233.42<br></br>13.64.196.27<br></br>13.64.198.97<br></br>13.64.199.41<br></br>13.64.198.19|
|EU1|13.80.22.71<br></br>13.95.29.177<br></br>13.95.30.46|


### <a name="app-connector"></a>Connecteur d’applications
Pour que Cloud App Security puisse accéder à certaines applications tierces, vous devez utiliser ces adresses IP pour permettre à Cloud App Security de collecter les journaux et de fournir un accès pour la console Cloud App Security. 

> [!NOTE]
>Vous verrez peut-être ces adresses IP dans les journaux d’activité du fournisseur, car Cloud App Security effectue des actions de gouvernance et des analyses à partir de ces adresses IP. 
  

### <a name="dlp-integration"></a>Intégration DLP

Pour que Cloud App Security envoie des données via votre stunnel à votre serveur ICAP, ouvrez votre pare-feu DMZ à ces adresses IP avec un numéro de port source dynamique. 

1.  Adresses sources : elles doivent figurer sur la liste verte, comme ci-dessus pour les applications tierces du connecteur d’API
2.  Port TCP source : dynamique
3.  Adresse(s) de destination : une ou deux adresses IP du stunnel connecté au serveur ICAP externe
4.  Port TCP de destination : comme défini dans votre réseau

> [!NOTE] 
> Par défaut, le numéro de port du stunnel a la valeur 11344. Vous pouvez le remplacer par un autre port si nécessaire, mais n’oubliez pas de noter le nouveau numéro de port.


    



  
## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  

   