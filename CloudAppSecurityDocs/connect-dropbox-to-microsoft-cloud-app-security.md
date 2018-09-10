---
title: Connecter Dropbox à Cloud App Security pour la visibilité et le contrôle d’utilisation | Microsoft Docs
description: Cette rubrique fournit des informations sur la connexion de votre application Dropbox à Cloud App Security à l’aide du connecteur API.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 4acd93f4-b885-4e1f-a385-43b5db02a3ee
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 347a0fe95fc27212e76f294047c408e2b6aaa36d
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44143698"
---
*S’applique à : Microsoft Cloud App Security*


# <a name="connect-dropbox-to-microsoft-cloud-app-security"></a>Connecter Dropbox à Microsoft Cloud App Security
Cette section fournit des instructions pour connecter Microsoft Cloud App Security à votre compte Dropbox existant à l’aide des API du connecteur.  
 
 
Étant donné que Dropbox permet d’accéder aux fichiers à partir de liens partagés sans connexion, Cloud App Security inscrit ces utilisateurs en tant qu’utilisateurs non authentifiés. Si vous voyez des utilisateurs Dropbox non authentifiés, il peut s’agir d’utilisateurs qui n’appartiennent pas à votre organisation ou d’utilisateurs reconnus de votre organisation qui ne se sont pas connectés.

## <a name="how-to-connect-dropbox-to-cloud-app-security"></a>Comment connecter Dropbox à Cloud App Security  
  
1.  Dans la console Cloud App Security, cliquez sur **Examiner**, puis sur **Applications connectées**.  
  
2.  Dans la page **Connecteurs d’application**, cliquez sur le bouton plus (+), puis sur **Dropbox**.  
  
     ![connecter dropbox](./media/connect-dropbox.png "connecter dropbox")  
  
3.  Dans la fenêtre contextuelle, entrez l’adresse e-mail du compte d’administrateur.  
  
4.  Cliquez sur **Générer un lien**.  
  
5.  Cliquez sur **suivez ce lien**.  
  
     La page de connexion à Dropbox s’ouvre. Entrez vos informations d’identification pour autoriser Cloud App Security à accéder à l’instance Dropbox votre équipe.  
  
6.  Dropbox vous demande si vous voulez autoriser Cloud App Security à accéder aux informations de votre équipe, au journal d’activité et à effectuer des activités en tant que membre de l’équipe. Pour continuer, cliquez sur **Autoriser**.  
  
7.  De retour dans la console Cloud App Security, vous devez recevoir un message indiquant que Dropbox a été correctement connecté.  
  
8.  Vérifiez la connexion en cliquant sur **Test API** (Tester l’API).  
  
     Le test peut prendre quelques minutes. Une fois averti que la connexion a réussi, cliquez sur **Fermer**.  
  
Après avoir connecté Dropbox, vous recevrez les événements des 60 jours précédant la connexion.

> [!NOTE] 
> Tout événement Dropbox pour l’ajout d’un fichier est affiché dans Cloud App Security en tant que fichier de chargement pour l’aligner sur toutes les autres applications connectées à Cloud App Security. 
 
## <a name="see-also"></a>Voir aussi  
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  