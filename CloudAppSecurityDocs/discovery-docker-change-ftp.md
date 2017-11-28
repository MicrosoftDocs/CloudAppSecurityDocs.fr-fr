---
title: Modification du mot de passe FTP pour le docker Cloud Discovery | Microsoft Docs
description: "Cette rubrique décrit le processus de modification du mot de passe FTP de Cloud Discovery."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 26/11/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 776e834f-3c20-4d5f-9fab-4c5b975edb06
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 91411653b36cc5119b1c8e85ceac79c34386482f
ms.sourcegitcommit: 473d96a6383a6e4d01ef03ed31f2e773cea82cab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2017
---
# <a name="changing-the-ftp-password"></a>Modification du mot de passe FTP


1. Connectez-vous à l’hôte du collecteur de journaux.

2.  Exécutez `docker exec -it <collector name> pure-pw passwd <ftp user>`

    1. Saisissez le nouveau mot de passe.
    2. Saisissez à nouveau le nouveau mot de passe pour le confirmer.
 
3.  Exécutez `docker exec -it <collector name> pure-pw mkdb` pour appliquer la modification.


  ![modifier le mot de passe FTP](./media/ftp-connect.png)

## <a name="see-also"></a>Voir aussi
[Utilisation des données Cloud Discovery](working-with-cloud-discovery-data.md)  
[Pour obtenir un support technique, visitez la page de support assisté de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)  
[Les clients Premier peuvent également choisir Cloud App Security directement dans le portail Premier.](https://premier.microsoft.com/)

