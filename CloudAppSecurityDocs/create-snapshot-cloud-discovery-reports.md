---
title: "Créer des rapports d’instantanés Cloud Discovery | Documentation Microsoft"
description: "Cet article fournit des informations sur le chargement manuel de journaux pour créer un rapport d’instantané de vos applications Cloud Discovery."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/29/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: ecc1949d-c861-4636-952a-c3a260719bb5
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 851617bc68618b177600523a4d4432b3e557f394
ms.openlocfilehash: abd134c9ff3b000170bce474e8ecebb71b762b98


---

# <a name="create-snapshot-cloud-discovery-reports"></a>Créer des rapports d’instantanés Cloud Discovery
Il est important de charger un journal manuellement et de laisser Cloud App Security l’analyser avant de tenter d’utiliser le collecteur de journaux automatique.

Pour créer un rapport d’instantané :
  
1.  Collectez les fichiers journaux de votre pare-feu et de votre proxy, via lesquels les utilisateurs de votre organisation accèdent à Internet. Veillez à collecter les journaux pendant les heures de pointe représentatives de toute l’activité utilisateur dans votre organisation.  
  
2.  Dans le portail Cloud App Security, cliquez sur **Découvrir**, puis sur **Créer un rapport de capture instantanée**.  
  
     ![Créer un rapport de capture instantanée](./media/create-new-snapshot-report.png)
     
      
3.  Renseignez **Nom du rapport** et **Description**
  
4.  Sélectionnez la **source de données** à partir de laquelle vous voulez charger les fichiers journaux.  
  
5.  **Choisissez les journaux de trafic** à charger. Vous pouvez charger jusqu’à 20 fichiers à la fois. Les fichiers compressés et zippés sont également pris en charge.  
  
6.  Cliquez sur **Create (Créer)**.  
  
     ![Nouveau rapport d’instantané](./media/new-snapshot-report.png) 
  
7.  Une fois le chargement terminé, un message d’état s’affiche dans le coin supérieur droit de votre écran pour vous informer que le journal a correctement été chargé.  
  
8.  Une fois que vos fichiers journaux sont chargés, un certain temps est nécessaire pour leur extraction et leur analyse.  
Après le traitement de vos fichiers journaux, vous recevrez un e-mail pour vous avertir que l’opération est terminée. 
  
9. Une bannière de notification s’affiche dans la barre d’état en haut du portail pour vous informer de l’état de traitement de vos fichiers journaux.  
![barre de menus de traitement des fichiers journaux](./media/processing-log-file-menu-bar.png) 
   
10. Une fois les journaux téléchargés, une notification vous informant que le traitement du fichier journal s’est terminé correctement doit s’afficher. À ce stade, vous pouvez afficher le rapport en cliquant sur le lien dans la barre d’état, ou en accédant à la dent Paramètres et en sélectionnant **Paramètres Cloud Discovery**.   
  
     ![onglet Paramètres Cloud Discovery](./media/discovery-settings-tab.png)
11. Sélectionnez ensuite **Gérer des rapports d’instantanés** et votre rapport d’instantané.
 
![gestion des rapports d’instantanés](./media/snapshot-report-managment.png)

  
      
## <a name="see-also"></a>Voir aussi  
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
    
      
  


<!--HONumber=Nov16_HO5-->


