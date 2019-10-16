---
title: Analyseur de journal personnalisé Cloud App Security pour les journaux qui ne sont pas pris en charge
description: Cet article fournit des informations sur l’utilisation de l’analyseur de journal personnalisé pour charger les journaux des appareils qui ne sont pas pris en charge dans Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: a612d87e-5471-4add-b4b1-dbbb530f2b61
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 3f1e38f31a125dcad562f321aa8eac87a0a0fd31
ms.sourcegitcommit: c342abeec95359ddabdabcc3a081a0f91d52407c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72335689"
---
# <a name="use-a-custom-log-parser"></a>Utiliser un analyseur de journal personnalisé

*S’applique à : Microsoft Cloud App Security*

Cloud App Security vous permet de configurer un analyseur personnalisé correspondant au format de vos journaux et de traiter le format de vos journaux pour qu’ils soient utilisables avec Cloud Discovery. En règle générale, vous utilisez un analyseur personnalisé si le pare-feu ou l’appareil n’est pas explicitement pris en charge par Cloud App Security. Il peut s’agir d’un analyseur CSV ou d’un analyseur Clé-Valeur personnalisé.

L’analyseur personnalisé vous permet d’utiliser les journaux de pare-feu non pris en charge. 


 
Pour configurer un analyseur personnalisé :
1. Dans le portail Cloud App Security, cliquez sur **Découvrir**, puis sur **Créer un rapport de capture instantanée**.  
  
   ![Créer un rapport de capture instantanée](./media/create-new-snapshot-report.png)
     
2. Renseignez **Nom du rapport** et **Description**
  
3. Sous **Source de données**, sélectionnez **Format de journal personnalisé**.  

    ![Nouveau rapport d’instantané](./media/custom-log-upload.png)   

4. Collectez les journaux de votre pare-feu et de votre proxy, par le biais desquels les utilisateurs de votre organisation accèdent à Internet. Veillez à collecter les journaux pendant les heures de pointe représentatives de toute l’activité utilisateur dans votre organisation. 

5. Ouvrez les journaux que vous voulez traiter dans un éditeur de texte. Examinez leur format pour vérifier que les noms des colonnes dans le journal correspondent aux champs de l’écran **Format de journal personnalisé**.

   ![analyseur de journal personnalisé](./media/log-data.png) 

6. Renseignez ensuite les champs en fonction de vos données pour définir les colonnes dans les données à mettre en corrélation avec des champs spécifiques dans Cloud App Security. Vous devrez peut-être modifier les noms des colonnes dans votre fichier journal pour effectuer correctement la corrélation.
  
   > [!NOTE]
    > Les champs respectent la casse. Vérifiez que les noms des colonnes sont identiques dans Cloud App Security et dans le fichier journal. Veillez également à ce que le format de date choisi soit le même.

   ![analyseur de journal personnalisé](./media/custom-log-parser.png) 


7. Cliquez sur **Save**. Le format de journal personnalisé que vous configurez est enregistré comme analyseur personnalisé par défaut. Vous pouvez le modifier à tout moment en cliquant sur **Modifier**.

8. Sous **Choisir les journaux de trafic**, sélectionnez le fichier journal que vous avez modifié et chargez-le. Vous pouvez charger jusqu’à 20 fichiers à la fois. Les fichiers compressés et zippés sont également pris en charge.  
  

9. Cliquez sur **Create (Créer)** .  

10. Une fois le chargement terminé, un message d’état s’affiche dans le coin supérieur droit de votre écran pour vous informer que le journal a correctement été chargé.  
  
11. Une fois que vos fichiers journaux sont chargés, un certain temps est nécessaire pour leur extraction et leur analyse.  
    Après le traitement de vos fichiers journaux, vous recevez un e-mail pour vous avertir que l’opération est terminée. 
  
12. Une bannière de notification apparaît dans la barre d’état en haut du **tableau de bord Cloud Discovery**. La bannière se met à jour avec l’état du traitement de vos fichiers journaux.  
    ![barre de menus du traitement des fichiers journaux](./media/processing-log-file-menu-bar.png) 
   
13. Une fois les journaux téléchargés, une notification vous informant que le traitement du fichier journal s’est terminé correctement doit s’afficher. À ce stade, vous pouvez afficher le rapport en cliquant sur le lien dans la barre d’état, ou en accédant à l’icône d’engrenage Paramètres et en sélectionnant **Paramètres Cloud Discovery**.   
  
     ![onglet Paramètres Cloud Discovery](./media/discovery-settings-tab.png)
14. Sélectionnez ensuite **Gérer des rapports d’instantanés** et votre rapport d’instantané.
 
    ![gestion des rapports d’instantanés](./media/snapshot-report-managment.png)

  
      




## <a name="next-steps"></a>Étapes suivantes
 
[Créer des rapports d’instantanés Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Configurer le chargement automatique des journaux pour des rapports continus](configure-automatic-log-upload-for-continuous-reports.md)

[Utilisation des données Cloud Discovery](working-with-cloud-discovery-data.md)

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)  
