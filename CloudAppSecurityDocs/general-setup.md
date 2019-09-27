---
title: Configurez les paramètres de votre organisation dans Cloud App Security
description: Cet article explique comment fournir des informations sur votre organisation dans Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 6/24/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 2e7e57b0-db54-4d75-896c-4700dd9abe48
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 6ca87c02f9eed0bbba8383d46ebb621dc4be31b5
ms.sourcegitcommit: 8a49c166424fea83853b0a6895212367526abe78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71084460"
---
# <a name="basic-setup-for-cloud-app-security"></a>Configuration de base pour Cloud App Security

*S’applique à : Microsoft Cloud App Security*

La procédure suivante contient des instructions pour personnaliser le portail Microsoft Cloud App Security.

## <a name="prerequisites"></a>Prérequis 
Pour l’accès au portail, il est nécessaire d’ajouter les adresses IP suivantes à la liste verte de votre pare-feu pour fournir l’accès au portail Cloud App Security :  
  
- 104.42.231.28  
  
> [!NOTE]  
>  Pour obtenir des mises à jour quand des URL et des adresses IP ont changé, abonnez-vous au flux RSS comme expliqué dans : [URL et plages d’adresses IP Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).
  
## <a name="set-up-the-portal"></a>Configurer le portail  
  
1. Dans la barre de menus du portail Cloud App Security, cliquez sur la roue dentée des paramètres ![icône des paramètres](./media/settings-icon.png "icône des paramètres") et sélectionnez **Paramètres** pour configurer les éléments de votre organisation.     

1. Sous **Détails de l’organisation**, vous devez absolument fournir un **Nom d’affichage de l’organisation** pour votre organisation. Il apparaît dans les e-mails et les pages web envoyés par le système.  
  
1. Fournissez un **Nom de l’environnement** (client). Ces informations sont particulièrement importantes si vous gérez plusieurs locataires.  
  
1. Vous pouvez également fournir un **Logo** qui apparaît dans les e-mails de notification et les pages web envoyées par le système. Le logo doit être un fichier png avec une taille maximale de 150 x 50 pixels sur un arrière-plan transparent.  

1. Veillez à ajouter la liste de vos **Domaines gérés**. L’ajout de domaines managés est une étape essentielle. Cloud App Security utilise les domaines managés pour déterminer quels sont les utilisateurs internes, les utilisateurs externes ainsi que les emplacements auxquels les fichiers doivent ou non être partagés. Ces informations sont utilisées pour les rapports et les alertes.  

    - Les utilisateurs dans des domaines qui ne sont pas configurés comme internes sont marqués comme externes. Aucune recherche d’activités ou de fichiers n’est exécutée sur les utilisateurs externes.

1. Sous **déconnexion automatique**, spécifiez la durée pendant laquelle une session peut rester inactive avant que la session ne soit déconnectée automatiquement.

1. En cas d’intégration à Azure Information Protection, consultez [Intégration d’Azure Information Protection](azip-integration.md) pour obtenir des informations. 

    - Pour utiliser l’intégration à Azure Information Protection, vous devez activer le [connecteur d’applications pour Office 365](connect-office-365-to-microsoft-cloud-app-security.md).
  
1. Si vous effectuez l’intégration avec l’intégration d’Azure-protection avancée contre les menaces, consultez [intégration d’Azure-protection avancée contre les menaces](azip-integration.md) pour plus d’informations.

1. Grâce à cet écran, vous pouvez à tout moment sauvegarder vos paramètres de portail. Cliquez sur **Exporter les paramètres de portail** pour créer un fichier json de tous vos paramètres de portail, notamment les règles de stratégie, les groupes d’utilisateurs et les plages d’adresses IP.  
  
> [!NOTE]
> Si vous utilisez ExpressRoute, Cloud App Security est déployé dans Azure et entièrement intégré à [ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/). Toutes les interactions avec les applications Cloud App Security et le trafic envoyé vers Cloud App Security, notamment le chargement des journaux de découverte, sont acheminés via le **peering public** ExpressRoute pour améliorer la latence, les performances et la sécurité. Aucune étape de configuration n’est nécessaire côté client. <br></br>Pour plus d’informations sur le peering public, consultez [Circuits ExpressRoute et domaines de routage](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/).  

## <a name="next-steps"></a>Étapes suivantes  
[Configurer Cloud Discovery](set-up-cloud-discovery.md)   

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)  
