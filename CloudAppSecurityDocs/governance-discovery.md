---
title: Blocage des applications découvertes | Microsoft Docs
description: Cette rubrique décrit la procédure d’exportation de scripts de blocage pour les applications découvertes.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: e451031e-4764-411a-b366-73a49d4f25df
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: e6976c39a644fe96f1d9ec431df08c9737026ffd
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44143037"
---
*S’applique à : Microsoft Cloud App Security*


## <a name="govern-discovered-apps"></a>Gouverner les applications découvertes

Une fois que vous avez consulté la liste des applications découvertes dans votre environnement, vous pouvez sécuriser de plusieurs façons l’environnement contre l’utilisation d’applications indésirables.


### <a name="sanctioningunsanctioning-an-app"></a>Approbation/non-approbation d’une application 

Pour ne pas approuver une application présentant un risque spécifique, cliquez sur les points de suspension à la fin de la ligne et sélectionnez **Ne pas approuver**.
Vous avez toujours la possibilité d’utiliser une application non approuvée, mais grâce aux filtres Cloud Discovery vous surveillez plus facilement son utilisation. Vous pouvez alors informer les utilisateurs de l’application qu’elle n’est pas approuvée et leur suggérer d’utiliser une autre application sécurisée.

![Marquer comme non approuvées](./media/tag-as-unsanctioned.png)  

Si vous voulez approuver/ne pas approuver une liste d’applications, cochez les cases des applications que vous voulez gérer, puis sélectionnez l’action appropriée.

Pour interroger une liste d’applications non approuvées, vous pouvez [générer un script de bloc en utilisant les API Cloud App Security](https://mod636914.us.portal.cloudappsecurity.com/api-docs/#generate-block-script).

> [!NOTE]
> Si votre locataire utilise Zscaler NSS, n’importe quelle application que vous marquez comme non approuvée est automatiquement bloquée par Cloud App Security et les sections suivantes concernant la création de scripts de blocage ne sont pas nécessaires. Pour plus d’informations, consultez [Intégration avec Zscaler](zscaler-integration.md).

## <a name="export-a-block-script-to-govern-discovered-apps"></a>Exporter un script de blocage pour gouverner les applications découvertes

Cloud App Security vous permet de bloquer l’accès aux applications non approuvées en optimisant vos appliances de sécurité locales existantes. Générez un script de blocage dédié et importez-le dans votre appliance.
Pour cette solution, vous n’avez pas besoin de rediriger tout le trafic web de l’organisation vers un proxy.

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

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  