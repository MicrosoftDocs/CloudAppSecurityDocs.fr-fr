---
title: Créer des rapports d’instantané de l’utilisation des applications cloud Cloud Discovery | Microsoft Docs
description: Cet article fournit des informations sur le chargement manuel de journaux pour créer un rapport d’instantané de vos applications Cloud Discovery.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: ecc1949d-c861-4636-952a-c3a260719bb5
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 734975276a148ce541b84c4a68751b2bdb5666fb
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44143647"
---
*S’applique à : Microsoft Cloud App Security*


# <a name="create-snapshot-cloud-discovery-reports"></a>Créer des rapports d’instantanés Cloud Discovery
Il est important de charger un journal manuellement et de laisser Microsoft Cloud App Security l’analyser avant de tenter d’utiliser le collecteur de journaux automatique.
Si vous n’avez pas encore de journal et que vous aimeriez voir à quoi il doit ressembler, suivez la procédure ci-dessous pour télécharger un exemple de fichier journal.


Pour créer un rapport d’instantané :
  
1. Collectez les fichiers journaux de votre pare-feu et de votre proxy, via lesquels les utilisateurs de votre organisation accèdent à Internet. Veillez à collecter les journaux pendant les heures de pointe représentatives de toute l’activité utilisateur dans votre organisation.  
  
2. Dans le portail Cloud App Security, cliquez sur **Découvrir**, puis sur **Créer un rapport de capture instantanée**.  
  
   ![Créer un rapport de capture instantanée](./media/create-new-snapshot-report.png)
     
3. Renseignez **Nom du rapport** et **Description**
  
    ![Nouveau rapport d’instantané](./media/new-snapshot-report.png) 

4. Sélectionnez la **source de données** à partir de laquelle vous voulez charger les fichiers journaux.  
  
5. Examinez le format de votre journal pour vérifier qu’il convient à l’exemple à télécharger. Cliquez sur **Afficher et vérifier**, puis sur **Télécharger un exemple de journal**. Comparez ensuite votre journal à l’exemple fourni pour vérifier qu’il est compatible. 

   ![Vérifier le format de votre journal](./media/cloud-discovery-snapshot-verify.png)  

   > [!NOTE]
   > L’exemple de format FTP est pris en charge dans les captures instantanées et le chargement automatique alors que syslog est pris en charge dans le chargement automatique uniquement.<br></br>
   Le téléchargement d’un exemple de journal télécharge un exemple de journal FTP.


6. **Choisissez les journaux de trafic** à charger. Vous pouvez charger jusqu’à 20 fichiers à la fois. Les fichiers compressés et zippés sont également pris en charge.  
  
7. Cliquez sur **Créer**.  

8. Une fois le chargement terminé, un message d’état s’affiche dans le coin supérieur droit de votre écran pour vous informer que le journal a correctement été chargé.  
  
9. Une fois que vos fichiers journaux sont chargés, un certain temps est nécessaire pour leur extraction et leur analyse.  
   Après le traitement de vos fichiers journaux, vous recevrez un e-mail pour vous avertir que l’opération est terminée. 
  
10. Une bannière de notification s’affiche dans la barre d’état en haut du portail pour vous informer de l’état de traitement de vos fichiers journaux.  
    ![barre de menus de traitement des fichiers journaux](./media/processing-log-file-menu-bar.png) 
   
11. Une fois les journaux téléchargés, une notification vous informant que le traitement du fichier journal s’est terminé correctement doit s’afficher. À ce stade, vous pouvez afficher le rapport en cliquant sur le lien dans la barre d’état, ou en accédant à la dent Paramètres et en sélectionnant **Paramètres Cloud Discovery**.   
  
     ![onglet Paramètres Cloud Discovery](./media/discovery-settings-tab.png)
12. Sélectionnez ensuite **Rapports d’instantanés**, puis votre rapport d’instantané.
 
![gestion des rapports d’instantanés](./media/snapshot-report-managment.png)

  
      
## <a name="see-also"></a>Voir aussi  
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
    
      
  