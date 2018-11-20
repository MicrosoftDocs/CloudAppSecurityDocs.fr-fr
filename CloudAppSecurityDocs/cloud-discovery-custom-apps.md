---
title: Ajouter des applications personnalisées à Cloud Discovery dans Cloud App Security | Microsoft Docs
description: Cette rubrique fournit des informations sur la façon d’ajouter des applications personnalisées à Cloud Discovery dans Cloud App Security pour surveiller le Shadow IT.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/13/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 98b0d841-b33d-4ae9-b48b-d9ee77785eaa
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 4cbe1ab46596f55283b0aa86390674e048c45216
ms.sourcegitcommit: 77850c6777504c2478611cb71a387e7fcc5f2551
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51597389"
---
# <a name="add-custom-apps-to-cloud-discovery"></a>Ajouter des applications personnalisées à Cloud Discovery

*S’applique à : Microsoft Cloud App Security*
    
Cloud Discovery analyse vos journaux de trafic en s’appuyant sur le catalogue d’applications cloud Microsoft Cloud App Security. Ce catalogue comprend plus de 16 000 applications. Le catalogue contient uniquement des applications cloud disponibles publiquement et pour lesquelles Cloud App Security fournit des informations sur la visibilité et les risques.

Pour que vous puissiez connaître les applications cloud qui ne sont pas incluses dans le catalogue, Cloud App Security vous permet de découvrir les applications cloud personnalisées (ou applications métier) qui ont été développées ou affectées spécifiquement pour votre organisation.

En ajoutant une nouvelle application cloud personnalisée, Cloud App Security peut établir une correspondance entre l’application et les messages du journal sur le trafic du pare-feu et du proxy qui ont été chargés, et ainsi, vous offrir une visibilité sur l’utilisation de cette application dans votre organisation dans les pages Cloud Discovery (par exemple, le nombre de personnes qui utilisent l’application, le nombre d’adresses IP sources uniques qui utilisent l’application, ainsi que le volume de trafic transmis vers et à partir de cette application). 

## <a name="add-a-new-custom-cloud-app"></a>Ajouter une nouvelle application cloud personnalisée

1. Dans le portail Cloud App Security, cliquez sur **Découvrir**, puis sur **Tableau de bord Cloud Discovery**. 
  
   ![menu du tableau de bord Cloud Discovery](./media/cloud-discovery-dashboard-menu.png)

2. En haut à droite, cliquez sur les trois points, puis sélectionnez **Ajouter une nouvelle application personnalisée**. 

   ![menu ajouter une nouvelle application personnalisée](./media/add-custom-app-menu.png)

3. Renseignez les champs pour définir le nouvel enregistrement d’application qui figurera dans le catalogue d’applications cloud et dans Cloud Discovery, une fois qu’il aura été découvert dans les journaux de votre pare-feu.

   ![application personnalisée](./media/add-custom-app.png)

4. Sous **Domaines**, renseignez les domaines uniques utilisés lors de l’accès à l’application personnalisée. Ces domaines servent à faire correspondre des messages du journal de trafic avec cette application. Si la source de données que vous utilisez ne contient pas d’informations sur l’URL de l’application, renseignez les champs d’adresse **IPv4** et **IPv6**.
5. Renseignez les champs **Plateforme d’hébergement** et **ID d’abonnement Azure**. Si vous le souhaitez, spécifiez une **Unité commerciale** pour l’application. 
6. Attribuez un **Score** relatif au risque et ajoutez des informations dans **Notes de l’application** pour faciliter le suivi des modifications de cet enregistrement.
7. Cliquez sur **Créer**.

Une fois créée, l’application est disponible dans le catalogue d’applications cloud.

Vous pouvez à tout moment cliquer sur les trois points à la fin de la ligne pour modifier ou supprimer une application personnalisée.

>[!NOTE]
> Les applications personnalisées affichent automatiquement une balise **Application personnalisée** lorsque vous les ajoutez. Cette balise d’application ne peut pas être supprimée.
Pour afficher toutes vos applications personnalisées, définissez le filtre **Balise d’application** sur « Application personnalisée ». 
<!-- -  By default, custom apps have a risk score of 10, but you can use the **Override app score** action to change it at any time.-->

  
## <a name="next-steps"></a>Étapes suivantes 
[Stratégies d’activité utilisateur](user-activity-policies.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  