---
title: Se connecter WebEx à Cloud App Security
description: Cet article fournit des informations sur comment connecter votre application WebEx à Cloud App Security à l’aide du connecteur API pour la visibilité et contrôle d’utilisation.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 04/16/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: c43271fd-9a61-4727-9945-de1c6ea5422c
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: be23b571e25ba283bd661f647cf38d462b37882b
ms.sourcegitcommit: 9f0c562322394a3dfac7f1d84286e673276a28b1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65568172"
---
# <a name="connect-cisco-webex-to-microsoft-cloud-app-security"></a>Connecter Cisco WebEx à Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

Cet article fournit des instructions pour connecter Microsoft Cloud App Security à votre compte de Cisco WebEx existant à l’aide des API du connecteur. Cette connexion donne vous visibilité et contrôle sur les utilisateurs, les activités et les fichiers WebEx. 
 
## <a name="prerequisites"></a>Prérequis

- Nous vous suggérons de créer un compte de service dédié pour la connexion. Cela vous permet de voir que les actions de gouvernance effectuées dans WebEx comme en cours d’exécution à partir de ce compte, telles que suppriment les messages envoyés dans WebEx. Sinon, le nom de l’administrateur qui se sont connectés de Cloud App Security à WebEx apparaîtra en tant que l’utilisateur qui a effectué les actions.  
- Vous devez disposer d’administrateur complet **et** autorisations d’administrateur de conformité dans WebEx.


## <a name="how-to-connect-webex-to-cloud-app-security"></a>Comment se connecter WebEx à Cloud App Security  
  
1.  Dans la console Cloud App Security, cliquez sur **Examiner**, puis sur **Applications connectées**.  
  
2.  Dans le **connecteurs d’application** , cliquez sur le bouton plus (+) puis **Cisco WebEx**.  
  
     ![se connecter WebEx](./media/cisco-webex.png "connecter WebEx")  
  
3.  Dans la fenêtre contextuelle, entrez le nom de l’instance de ce connecteur.  
  
4.  Cliquez sur **se connecter à Cisco Webex**. La page de connexion WebEx s’ouvre. Entrez vos informations d’identification pour autoriser Cloud App Security à accéder à l’instance de WebEx de votre équipe.  
  
6.  WebEx vous demande si vous voulez autoriser Cloud App Security à accéder aux informations de votre équipe, journal d’activité et à effectuer des activités en tant que membre de l’équipe. Pour continuer, cliquez sur **Autoriser**.  
  
7.  Dans la console Cloud App Security, vous devez recevoir un message indiquant que WebEx a été correctement connecté.  
  
8.  Vérifiez la connexion en cliquant sur **Test API** (Tester l’API).  
  
     Le test peut prendre quelques minutes. Une fois que vous êtes averti que la connexion a réussi, cliquez sur **Fermer**.  
  
Après avoir connecté WebEx, vous recevrez les événements des 7 derniers jours précédant la connexion. Cloud App Security analyse les événements sur les trois derniers mois. Pour augmenter de cela, vous devez posséder une licence pro Cisco WebEx et ouvrez un ticket avec prise en charge de Cloud App Security.

 
## <a name="next-steps"></a>Étapes suivantes 
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)  
  
  
