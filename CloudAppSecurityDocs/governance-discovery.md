---
title: "Blocage des applications découvertes | Microsoft Docs"
description: "Cette rubrique décrit la procédure d’exportation de scripts de blocage pour les applications découvertes."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/21/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: e451031e-4764-411a-b366-73a49d4f25df
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: ca4a10f64429c481f49c75740f651302b1c7d1ef
ms.sourcegitcommit: 7493d88e4fe7c827f870b81e2090ffcc77f1408a
translationtype: HT
---
# <a name="governing-discovered-apps"></a>Gouvernance des applications découvertes
Cloud App Security vous permet de bloquer l’accès aux applications non approuvées en optimisant vos appliances de sécurité locales existantes. Générez un script de blocage dédié et importez-le dans votre appliance.
Pour cette solution, vous n’avez pas besoin de rediriger tout le trafic web de l’organisation vers un proxy.


## <a name="export-a-block-script-to-govern-discovered-apps"></a>Exporter un script de blocage pour gouverner les applications découvertes

1. Dans le tableau de bord Cloud Discovery, marquez toutes les applications que vous souhaitez bloquer comme **Non approuvées**.

   ![Marquer comme non approuvées](./media/tag-as-unsanctioned.png)  

2. Dans la barre de titre, cliquez sur les trois points et sélectionnez **Générer un script de blocage...**. 

   ![Générer un script de blocage](./media/generate-block-script.png)  

3. Dans **Générer un script de blocage**, sélectionnez l’appliance pour laquelle vous souhaitez générer le script de blocage. 

   ![Générer la fenêtre pop-up du script de blocage](./media/generate-block-script-popup.png)  

4. Cliquez ensuite sur le bouton Générer un script. Cette action crée un script de blocage pour toutes vos applications non approuvées. Par défaut, le fichier est renommé avec la date à laquelle il a été exporté et le type d’appliance sélectionné, par exemple *2017-02-19_CAS_Fortigate_block_script.txt* 

   ![Bouton Générer un script de blocage](./media/generate-block-script-button.png)  

5. Importez le fichier créé dans votre appliance.



## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  