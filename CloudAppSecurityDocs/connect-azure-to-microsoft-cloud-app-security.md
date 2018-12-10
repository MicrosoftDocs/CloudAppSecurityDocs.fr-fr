---
title: Connecter Azure à Cloud App Security pour la visibilité et le contrôle d’utilisation | Microsoft Docs
description: Cet article fournit des informations sur la connexion d’Azure à Cloud App Security à l’aide du connecteur d’API.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/13/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 3a677bc7-c8b7-4c6a-aada-82c8b3778352
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 9466a9afa157bad350bb94b63ba633bf0d80bac2
ms.sourcegitcommit: 77850c6777504c2478611cb71a387e7fcc5f2551
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51597176"
---
# <a name="connect-azure-to-microsoft-cloud-app-security"></a>Connecter Azure à Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

Cet article fournit des instructions pour connecter Microsoft Cloud App Security à un compte Azure existant à l’aide de l’API de connecteur d’applications.  
  
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
  
  