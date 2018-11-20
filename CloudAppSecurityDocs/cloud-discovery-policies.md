---
title: Créer des stratégies sur des applications Cloud Discovery dans Cloud App Security | Microsoft Docs
description: Cette rubrique fournit des informations sur l’utilisation des stratégies Cloud Discovery.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/13/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 45446111-ed1a-4699-9df5-840cc6664a6b
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 01b08ae0246dbae89a71794bca170d757725c3c8
ms.sourcegitcommit: 77850c6777504c2478611cb71a387e7fcc5f2551
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51597195"
---
# <a name="cloud-discovery-policies"></a>Stratégies Cloud Discovery

*S’applique à : Microsoft Cloud App Security*

Vous pouvez créer des stratégies de découverte d’applications afin d’être averti lorsque de nouvelles applications sont détectées. Cloud App Security examine également tous les journaux de votre environnement Cloud Discovery pour déterminer s’ils contiennent des anomalies. 

## <a name="creating-an-app-discovery-policy"></a>Création d’une stratégie de découverte d’application  
Grâce aux stratégies de découverte, vous pouvez définir des alertes qui vous informent quand de nouvelles applications sont détectées au sein de votre organisation.  
  
1. Dans la console, cliquez sur **Contrôle**, puis sur **Stratégies**.  
  
2. Cliquez sur **Créer une stratégie** et sélectionnez **Stratégie de découverte d’application**.  
  
     ![menu Stratégie de découverte d’application](./media/app-discovery-policy-menu.png "menu Stratégie de découverte d’application")  
  
3. Attribuez un nom et une description à votre stratégie. Si vous le souhaitez, vous pouvez baser votre stratégie sur un modèle. Pour plus d’informations sur les modèles de stratégies, consultez [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md).  
  
4. Définissez la **Gravité** de la stratégie.

5. Pour définir les applications découvertes qui doivent déclencher cette stratégie, ajoutez des filtres.  
  
6. Vous pouvez définir un seuil pour la sensibilité de la stratégie. Activez l’option **Déclencher une correspondance de stratégie si tous les éléments suivants se produisent le même jour**. Vous pouvez définir les critères que l’application doit remplir quotidiennement pour respecter la stratégie. Sélectionnez l’un des critères suivants : 
     - Trafic quotidien
     - Données téléchargées
     - Nombre d’adresses IP
     - Nombre de transactions
     - Nombre d’utilisateurs
     - Données chargées

  
7. Définissez une **Limite d’alerte quotidienne** sous **Alertes**. Choisissez si l’alerte doit être envoyée par e-mail, par SMS, ou les deux. Ensuite, entrez les numéros de téléphone et les adresses e-mail des destinataires.
     - Si vous cliquez sur **Enregistrer ces paramètres d’alerte en tant que paramètres par défaut pour votre organisation**, les prochaines stratégies qui seront définies utiliseront ces paramètres.
     - Si vous avez déjà configuré des paramètres par défaut, vous pouvez sélectionner **Utiliser les paramètres par défaut de votre organisation**.
  
8. Sélectionnez les actions de **gouvernance** à appliquer quand une application remplit tous les critères de cette stratégie. Vous pouvez étiqueter les stratégies comme étant **Approuvées** ou **Non approuvées**, ou bien utiliser une étiquette personnalisée. 

9. Cliquez sur **Créer**.  
  
Par exemple, pour découvrir les applications d’hébergement à risque qui ont été détectées dans votre environnement cloud, définissez votre stratégie de la façon suivante :  
  
Définissez des filtres de stratégie afin de découvrir les services appartenant à la catégorie **Services d’hébergement** dont l’indice de risque est égal à 1, ce qui correspond à un risque élevé.

 Définissez les seuils qui doivent déclencher une alerte en cas de découverte d’une application donnée. Par exemple, déclenchez une alerte uniquement si plus de 100 utilisateurs de l’environnement ont utilisé l’application et s’ils ont téléchargé une certaine quantité de données à partir du service.
En outre, vous pouvez définir la limite des alertes quotidiennes à recevoir.  
  
![exemple de stratégie de découverte d’application](./media/app-discovery-policy-example.png "exemple de stratégie de découverte d’application")  
  
## <a name="cloud-discovery-anomaly-detection"></a>Détection d’anomalie de Cloud Discovery

Cloud App Security examine tous les journaux de votre environnement Cloud Discovery pour déterminer s’ils contiennent des anomalies. À titre d’exemple, citons un utilisateur qui n’a jamais utilisé Dropbox et qui y charge soudainement 600 Go de données ou une application qui fait l’objet de transactions dans des proportions inhabituelles. La stratégie de détection des anomalies est activée par défaut. Il n’est pas nécessaire de configurer une nouvelle stratégie pour que la détection fonctionne. Toutefois, dans la stratégie par défaut, vous pouvez choisir les types d’anomalies pour lesquels vous souhaitez être averti.  
  
1. Dans la console, cliquez sur **Contrôle**, puis sur **Stratégies**.  
  
2. Cliquez sur **Créer une stratégie** et sélectionnez **Créer une stratégie de détection des anomalies de Cloud Discovery**.  
  
     ![menu Stratégie de détection des anomalies de Cloud Discovery](./media/cloud-discovery-anomaly-detection-policy-menu.png "menu Stratégie de détection des anomalies de Cloud Discovery")  
  
3. Attribuez un nom et une description à votre stratégie. Si vous le souhaitez, vous pouvez baser la stratégie sur un modèle. Pour plus d’informations sur les modèles de stratégie, consultez [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md).  
  
4. Pour définir les applications découvertes qui doivent déclencher cette stratégie, cliquez sur **Ajouter des filtres**.  
  
     Les filtres peuvent être sélectionnés dans des listes déroulantes. Pour ajouter des filtres, cliquez sur le bouton plus (+). Pour supprimer un filtre, cliquez sur le « X » en regard de celui-ci. 
  
5. Sous **Appliquer à**, choisissez si cette stratégie doit s’appliquer à **Tous les rapports continus** ou à des **Rapports continus spécifiques**. Indiquez si la stratégie s’applique à des **Utilisateurs**, à des **Adresses IP**, ou aux deux.  
  
6. Sous **Générer des alertes uniquement en cas d’activités suspectes après la date**, sélectionnez les dates pendant lesquelles l’occurrence d’une activité anormale doit déclencher une alerte.  
  
7. Définissez une **Limite d’alerte quotidienne** sous **Alertes**. Choisissez si l’alerte doit être envoyée par e-mail, par SMS, ou les deux. Ensuite, entrez les numéros de téléphone et les adresses e-mail des destinataires.
     - Si vous cliquez sur **Enregistrer ces paramètres d’alerte en tant que paramètres par défaut pour votre organisation**, les prochaines stratégies qui seront définies utiliseront ces paramètres.
     - Si vous avez déjà configuré des paramètres par défaut, vous pouvez sélectionner **Utiliser les paramètres par défaut de votre organisation**.
  
8. Cliquez sur **Créer**.  
  
![nouvelle stratégie de détection d’anomalie](./media/new-discovery-anomaly-policy.png "nouvelle stratégie de détection d’anomalie")  
  
## <a name="next-steps"></a>Étapes suivantes 
[Stratégies d’activité utilisateur](user-activity-policies.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  