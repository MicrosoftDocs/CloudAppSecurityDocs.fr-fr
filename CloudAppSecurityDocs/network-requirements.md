---
title: "Configuration requise du réseau Cloud App Security | Microsoft Docs"
description: "Cette rubrique décrit les adresses IP et les ports à ouvrir pour fonctionner avec Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/30/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 4de606f2-a09e-4e48-a578-e223de8b5e69
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: f67e363f9b6cdb866124960037ecb81e07756d8a
ms.sourcegitcommit: 9eb5c9c43629329a081f970b480956975e424ecb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2017
---
# <a name="network-requirements"></a>Configuration requise pour le réseau

Cette rubrique fournit une liste de ports et d’adresses IP que vous devez autoriser et ajouter à la liste verte pour qu’ils fonctionnent avec Cloud App Security. 


## <a name="view-your-data-center"></a>Afficher votre centre de données

Certaines exigences stipulées ci-dessous varient selon le centre de données auquel vous êtes connecté. 

Pour déterminer à quel centre de données vous vous connectez :

1. Dans le portail Cloud App Security, cliquez sur **?** dans la barre de menus et sélectionnez **À propos de**. 

    ![cliquez sur À propos de](./media/about-menu.png)

2. Dans l’écran de la version Cloud App Security, vous pouvez voir la région et le centre de données.

    ![Afficher votre centre de données](./media/data-center.png)

## <a name="portal-access"></a>Accès au portail

Pour accéder au portail Cloud App Security, ajoutez le **port sortant 443** pour les adresses IP suivantes à la liste verte de votre pare-feu :  


> [!div class="mx-tableFixed"]
|Centre de données|Adresses IP|  
|----|----|
|US1|13.80.125.22<br></br>52.183.75.62<br></br>13.91.91.243|
|EU1|13.80.125.22<br></br>52.183.75.62<br></br>52.174.56.180|

## <a name="siem-agent-connection"></a>Connexion de l’agent SIEM

Pour permettre à Cloud App Security de se connecter à votre SIEM, ajoutez le **port sortant 443** pour les adresses IP suivantes à la liste verte de votre pare-feu :  


> [!div class="mx-tableFixed"]
|Centre de données|Adresses IP|  
|----|----|
|US1|13.91.91.243|
|EU1|52.174.56.180|

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

## <a name="email-server"></a>Serveur de courrier

L’adresse IP de courrier dédiée à Cloud App Security est la suivante : 

198.2.134.139 (mail1.cloudappsecurity.com)

N’oubliez pas d’ajouter cette adresse IP à la liste verte de votre service anti-courrier indésirable pour activer les notifications à envoyer.
    
## <a name="log-collector"></a>Collecteur de journaux 

Pour activer les fonctionnalités Cloud Discovery à l’aide d’un collecteur de journaux et détecter Shadow IT dans votre organisation, il est nécessaire d’ouvrir les éléments suivants :

- Autorisez le collecteur de journaux à recevoir le trafic FTP et Syslog entrant.
- Autorisez le collecteur de journaux à lancer le trafic sortant sur le portail (par exemple, contoso.cloudappsecurity.com) sur le port 443.
- Autorisez le collecteur de journaux à initier le trafic sortant vers le stockage Blob Azure (https://adaprodconsole.blob.core.windows.net/) sur les ports 80 et 443.

> [!NOTE]
> Si votre pare-feu exige une liste d’accès à une adresse IP statique et ne prend pas en charge la mise sur liste verte en fonction de l’URL, autorisez le collecteur de journaux à initier le trafic sortant vers les plages IP du centre de données Microsoft Azure sur le port 443.




## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  

   