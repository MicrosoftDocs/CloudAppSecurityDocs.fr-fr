---
title: Connecter Azure à Cloud App Security pour la visibilité et le contrôle d’utilisation | Microsoft Docs
description: Cette rubrique fournit des informations sur la connexion d’Azure à Cloud App Security à l’aide du connecteur API.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/29/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 3a677bc7-c8b7-4c6a-aada-82c8b3778352
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 0bb637129c852e284aad5b27bba9ed13a5111cf5
ms.sourcegitcommit: bb010d8dd0a6eff39df31e33c2cc9c37ec321b46
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50217150"
---
*S’applique à : Microsoft Cloud App Security*


# <a name="connect-azure-to-microsoft-cloud-app-security"></a>Connecter Azure à Microsoft Cloud App Security

Cette section fournit des instructions pour connecter Microsoft Cloud App Security à votre compte Azure existant à l’aide de l’API du connecteur d’applications.  
  
## <a name="how-to-connect-azure-to-cloud-app-security"></a>Comment connecter Azure à Cloud App Security  
  
> [!NOTE]
> - L’utilisateur doit être administrateur général dans Azure AD pour connecter Azure à Microsoft Cloud App Security. 
> - Cloud App Security affiche les activités de **tous** les abonnements.
>-  Actuellement, Cloud App Security surveille uniquement les activités ARM. 
 
1.  Dans la page **Applications connectées**, cliquez sur le bouton plus (+) et sélectionnez **Microsoft Azure**.  
  
     ![connecter Azure](./media/connect-azure-menu.png) 

2.  Dans la fenêtre contextuelle Azure, cliquez sur **Connecter Microsoft Azure**.

      ![connecter Azure](./media/connect-azure.png) 
 
> [!NOTE] 
> Une fois Azure connecté, les données sont tirées (pull). À partir de maintenant, vous pouvez voir les données.


## <a name="next-steps"></a>Étapes suivantes 
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  