---
title: Blocage des applications découvertes – Cloud App Security | Microsoft Docs
description: Cet article décrit la procédure d’exportation de scripts de blocage pour les applications découvertes.
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
ms.assetid: e451031e-4764-411a-b366-73a49d4f25df
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: ab6a8d276cdd3ce1963be2e5a0c28b42bc8eeaa6
ms.sourcegitcommit: c342abeec95359ddabdabcc3a081a0f91d52407c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72335797"
---
# <a name="govern-discovered-apps"></a>Gouverner les applications découvertes

*S’applique à : Microsoft Cloud App Security*

Une fois que vous avez consulté la liste des applications découvertes dans votre environnement, vous pouvez sécuriser de plusieurs façons l’environnement contre l’utilisation d’applications indésirables.


## <a name="BKMK_SanctionApp"></a> Approbation/non-approbation d’une application 

Pour ne pas approuver une application présentant un risque spécifique, cliquez sur les points de suspension à la fin de la ligne. Ensuite, sélectionnez **Ne pas approuver**. Vous avez toujours la possibilité d’utiliser une application non approuvée, mais grâce aux filtres Cloud Discovery vous surveillez plus facilement son utilisation. Vous pouvez alors informer les utilisateurs de l’application non approuvée et leur suggérer d’utiliser une autre application sécurisée.

![Marquer comme non approuvées](./media/tag-as-unsanctioned.png)  

Si vous voulez approuver/ne pas approuver une liste d’applications, cochez les cases des applications que vous voulez gérer, puis sélectionnez l’action appropriée.

Pour interroger une liste d’applications non approuvées, vous pouvez [générer un script de bloc en utilisant les API Cloud App Security](https://us.portal.cloudappsecurity.com/api-docs/#generate-block-script).

> [!NOTE]
> Si votre locataire utilise Zscaler NSS, n’importe quelle application que vous marquez comme non approuvée est automatiquement bloquée par Cloud App Security et les sections suivantes concernant la création de scripts de blocage ne sont pas nécessaires. Pour plus d’informations, consultez [Intégration avec Zscaler](zscaler-integration.md).

## <a name="export-a-block-script-to-govern-discovered-apps"></a>Exporter un script de blocage pour gouverner les applications découvertes

Cloud App Security vous permet de bloquer l’accès aux applications non approuvées en utilisant vos appliances de sécurité locales existantes. Vous pouvez générer un script de blocage dédié et l’importer dans votre appliance. Pour cette solution, vous n’avez pas besoin de rediriger tout le trafic web de l’organisation vers un proxy.

1. Dans le tableau de bord Cloud Discovery, marquez toutes les applications que vous souhaitez bloquer comme **Non approuvées**.

   ![Marquer comme non approuvées](./media/tag-as-unsanctioned.png)  

2. Dans la barre de titre, cliquez sur les trois points et sélectionnez **Générer un script de blocage...** . 

   ![Générer un script de blocage](./media/generate-block-script.png)  

3. Dans **Générer un script de blocage**, sélectionnez l’appliance pour laquelle vous souhaitez générer le script de blocage. 

   ![Générer la fenêtre pop-up du script de blocage](./media/generate-block-script-popup.png)  

4. Ensuite, cliquez sur le bouton Générer un script afin de créer un script de blocage pour toutes vos applications non approuvées. Par défaut, le fichier est renommé avec la date à laquelle il a été exporté et le type d’appliance sélectionné. *2017-02-19_CAS_Fortigate_block_script.txt* serait un exemple de nom de fichier. 

   ![Bouton Générer un script de blocage](./media/generate-block-script-button.png)  

5. Importez le fichier créé dans votre appliance.



## <a name="next-steps"></a>Étapes suivantes  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)  
  
  
