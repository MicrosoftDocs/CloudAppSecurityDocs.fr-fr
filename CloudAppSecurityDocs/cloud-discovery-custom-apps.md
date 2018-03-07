---
title: "Ajouter des applications personnalisées à Cloud Discovery dans Cloud App Security | Microsoft Docs"
description: "Cette rubrique fournit des informations sur la façon d’ajouter des applications personnalisées à Cloud Discovery dans Cloud App Security pour surveiller le Shadow IT."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/27/2018
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 98b0d841-b33d-4ae9-b48b-d9ee77785eaa
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: d8ccd44e3c488b9adb0d4cd9df96b29b6bcc3e2d
ms.sourcegitcommit: 85d90d51e9e265d077f38b0188bcfdab2ce63ed1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2018
---
# <a name="add-custom-apps-to-cloud-discovery"></a>Ajouter des applications personnalisées à Cloud Discovery
    
Cloud Discovery analyse vos journaux de trafic en s’appuyant sur le catalogue d’applications cloud Microsoft Cloud App Security, qui contient plus de 15 000 applications cloud. Le catalogue contient uniquement des applications cloud disponibles publiquement et pour lesquelles Cloud App Security fournit des informations sur la visibilité et les risques.

Pour gagner en visibilité dans les applications cloud exclues du catalogue d’applications cloud, Cloud App Security vous permet de découvrir l’utilisation d’applications cloud personnalisées (applications métier) qui ont été développées ou affectées spécifiquement pour votre organisation.

En ajoutant une nouvelle application cloud personnalisée, Cloud App Security peut faire correspondre à l’application les messages du journal sur le trafic du pare-feu et du proxy chargés, et vous offrir ainsi une visibilité sur l’utilisation de cette application dans votre organisation dans les pages Cloud Discovery, par exemple le nombre de personnes qui utilisent l’application, le nombre d’adresses IP sources uniques qui utilisent l’application, ainsi que le volume de trafic transmis vers et depuis cette application. 

Pour ajouter une nouvelle application cloud personnalisée :

1.  Dans le portail Cloud App Security, cliquez sur **Découvrir**, puis sur **Tableau de bord Cloud Discovery**. 
  
 ![menu du tableau de bord Cloud Discovery](./media/cloud-discovery-dashboard-menu.png)

2.  Dans l’angle supérieur droit, cliquez sur les 3 points, puis sélectionnez **Ajouter une nouvelle application personnalisée**. 

 ![menu ajouter une nouvelle application personnalisée](./media/add-custom-app-menu.png)

3.  Renseignez les champs pour définir le nouvel enregistrement d’application qui apparaîtra dans le catalogue d’applications cloud et Cloud Discovery, une fois qu’il est découvert dans les journaux de votre pare-feu.

  ![application personnalisée](./media/add-custom-app.png)

4. Sous **Domaines**, renseignez les domaines uniques utilisés lors de l’accès à l’application personnalisée. Ces domaines servent à faire correspondre des messages du journal de trafic avec cette application. Si la source de données que vous utilisez ne contient pas d’informations sur l’URL de l’application, veillez à renseigner les champs d’adresse **IPv4** et **IPv6**.
4.  Il est recommandé d’ajouter des notes pour faciliter le suivi des modifications apportées à cet enregistrement.

Une fois créée, l’application est disponible dans le catalogue d’applications cloud.

Vous pouvez à tout moment cliquer sur les 3 points à la fin de la ligne pour modifier ou supprimer une application personnalisée.

>[!NOTE]
> - Les applications personnalisées affichent automatiquement une balise **Application personnalisée** lorsque vous les ajoutez. Cette balise d’application ne peut pas être supprimée.
Pour afficher toutes vos applications personnalisées, définissez le filtre **Balise d’application** sur « Application personnalisée ». 
> - Par défaut, les applications personnalisées affichent un score de risque de 10, mais vous pouvez utiliser l’action **Remplacer le score de l’application** pour modifier à tout moment cette valeur.

  
## <a name="see-also"></a>Voir aussi  
[Stratégies d’activité utilisateur](user-activity-policies.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  