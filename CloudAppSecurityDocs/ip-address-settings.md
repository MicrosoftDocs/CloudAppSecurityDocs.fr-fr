---
title: "Connecter des applications pour obtenir une visibilité et un contrôle complets avec Cloud App Security | Microsoft Docs"
description: "Cette rubrique décrit le processus de connexion d’applications à des applications dans le cloud de votre organisation avec des connecteurs d’API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/3/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 7e718d77-aae7-4a3a-8421-5ba7cee7d67c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: c8c9b63f4265876fc1de6a24c6576f917f9d2278
ms.sourcegitcommit: a0290ac2a662994f7771975ef6c20d0b47e9edd8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2017
---
Cloud App Security nécessite un accès comme suit pour se connecter à votre réseau. 

## <a name="cloud-app-security-system-ip-addresses"></a>Adresses IP système de Cloud App Security

Les adresses IP suivantes sont utilisées par Cloud App Security pour se connecter aux environnements clients. Cela est nécessaire lors de la connexion avec [ICAP](icap-stunnel.md) et lors de la connexion des connecteurs d’applications. Pour certaines applications, vous pouvez être amené à ajouter les adresses IP suivantes à la liste verte pour permettre à Cloud App Security de collecter les journaux et de fournir un accès pour la console Cloud App Security. Dans certaines applications, ces adresses IP peuvent également être utilisées pour identifier les activités Cloud App Security, comme dans les journaux d’audit du service. 
  
-   Pour les journaux :  
  
    104.209.35.177  
  
    13.91.98.185
 
    40.118.211.172

    13.93.216.68

    13.91.61.249

    13.93.233.42

    13.64.196.27

    13.64.198.97

    13.64.199.41

    13.64.198.19
  
  
## <a name="cas-portal-url-and-ip-addresses"></a>URL du portail Cloud App Security et adresses IP

L’URL de Cloud App Security, le port 443 et les adresses IP sont utilisés pour l’accès du client au portail, les connexions aux API Cloud App Security, le collecteur de journaux et l’agent SIEM. 
  
     104.42.231.28  

 
  
> [!NOTE]  
>  Pour obtenir des mises à jour quand des URL et des adresses IP ont changé, abonnez-vous au flux RSS comme expliqué dans [URL et plages d’adresses IP Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).  
  

  
## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  

   