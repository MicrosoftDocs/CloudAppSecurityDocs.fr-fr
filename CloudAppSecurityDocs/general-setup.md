---
title: "Indiquer les paramètres de votre organisation dans le portail Cloud App Security pour obtenir de meilleurs résultats | Microsoft Docs"
description: Cet article explique comment fournir des informations sur votre organisation dans Cloud App Security.
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/10/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 2e7e57b0-db54-4d75-896c-4700dd9abe48
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: cb2b4b26ee9a5f0340409090318fcbe1421b90d5
ms.sourcegitcommit: 50fac1cec86dfb8170ba9c63a8f58a4bf24e3c5b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2017
---
# <a name="basic-set-up"></a>Configuration de base
La procédure suivante contient des instructions pour personnaliser le portail Cloud App Security.
  
## <a name="set-up-the-portal"></a>Configurer le portail  
  
1.  Dans la barre de menus du portail Cloud App Security, cliquez sur l’icône des paramètres ![icône des paramètres](./media/settings-icon.png "icône des paramètres") et sélectionnez **Paramètres généraux** pour configurer les éléments suivants :  
     
     ![paramètres généraux](./media/general-settings.png "paramètres généraux")  
  
3.  Sous **Détails de l’organisation**, il est important que vous fournissiez un **Nom d’affichage de l’organisation** pour votre organisation. Il apparaît dans les e-mails et les pages web envoyés par le système.  
  
4. Fournissez un **Nom de l’environnement** (client). Cela est particulièrement important si vous gérez plusieurs clients.  
  
4. Vous pouvez également fournir un **Logo**, qui apparaît dans les notifications par courrier électronique et les pages web envoyées par le système. Le logo doit être un fichier png avec une taille maximale de 150 x 50 pixels sur un arrière-plan transparent.  

4.  Veillez à ajouter la liste de vos **Domaines gérés**. Cette étape est essentielle, car Cloud App Security utilise les domaines gérés pour déterminer quels sont les utilisateurs internes, les utilisateurs externes, ainsi que les emplacements auxquels les fichiers doivent ou non être partagés. Ce dispositif est utilisé pour les rapports, ainsi que pour les alertes.  
> [!NOTE] 
> - Les utilisateurs dans des domaines qui ne sont pas configurés comme internes seront marqués comme externes et aucune recherche d’activités ni de fichiers ne sera effectuée.

5. En cas d’intégration à Azure Information Protection, consultez [Intégration d’Azure Information Protection](azip-integration.md) pour obtenir des informations. 
  
  
6.  Grâce à cet écran, vous pouvez à tout moment sauvegarder vos paramètres de portail. Cliquez sur **Exporter les paramètres de portail** pour créer un fichier json de tous vos paramètres de portail, notamment les règles de stratégie, les groupes d’utilisateurs et les plages d’adresses IP.  
  
       



> [!NOTE] 
> Si vous utilisez ExpressRoute, Cloud App Security est déployé dans Azure et entièrement intégré à [ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/). Toutes les interactions avec les applications Cloud App Security et le trafic envoyé vers Cloud App Security, notamment le chargement des journaux de découverte, sont acheminés via l’**homologation publique** ExpressRoute pour améliorer la latence, les performances et la sécurité. Aucune étape de configuration n’est nécessaire côté client.  
    Pour plus d’informations sur l’homologation publique, consultez [Circuits ExpressRoute et domaines de routage](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/).  
    
## <a name="see-also"></a>Voir aussi  
[Configurer Cloud Discovery](set-up-cloud-discovery.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  