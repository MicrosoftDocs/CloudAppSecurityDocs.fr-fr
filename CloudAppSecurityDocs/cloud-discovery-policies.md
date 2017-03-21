---
title: "Créer des stratégies sur des applications Cloud Discovery dans Cloud App Security | Microsoft Docs"
description: "Cette rubrique fournit des informations sur l’utilisation des stratégies Cloud Discovery."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/23/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 45446111-ed1a-4699-9df5-840cc6664a6b
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: f90d44fba89e06e160c0161e1cec7b7f95d3e00c
ms.sourcegitcommit: 355226ee21981563066d637e7db0bff0d53c2da6
translationtype: HT
---
# <a name="cloud-discovery-policies"></a>Stratégies Cloud Discovery
    
## <a name="creating-an-app-discovery-policy"></a>Création d’une stratégie de découverte d’application  
Grâce aux stratégies de découverte, vous pouvez définir des alertes qui vous informent quand de nouvelles applications sont détectées au sein de votre organisation.  
  
1.  Dans la console, cliquez sur **Contrôle**, puis sur **Stratégies**.  
  
2.  Cliquez sur **Créer une stratégie** et sélectionnez **Stratégie de découverte d’application**.  
  
     ![menu Stratégie de découverte d’application](./media/app-discovery-policy-menu.png "menu Stratégie de découverte d’application")  
  
3.  Donnez à votre stratégie un nom et une description. Si vous le souhaitez, vous pouvez la baser sur un modèle ; pour plus d’informations sur les modèles de stratégie, consultez [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md).  
  
4.  Pour définir les applications découvertes qui doivent déclencher cette stratégie, cliquez sur **Ajouter des filtres**.  
  
     Vous pouvez choisir les filtres dans la partie gauche de la page de la fenêtre contextuelle des filtres. Vous pouvez filtrer par **Nom de l’application**, **Domaine**, **Facteur de risque**, **Indice de risque** et **Catégorie**. Le côté droit de la page affiche les résultats des filtres choisis à partir du catalogue de services actuel. Après avoir choisi les filtres, enregistrez votre configuration et vérifiez que les étiquettes appropriées apparaissent dans la zone des filtres.  
  
5.  Sous **Appliquer à**, choisissez **Utilisateurs**, **Adresses IP** ou les deux.  
  
6.  Définissez le seuil **Utilisation quotidienne** que l’application doit respecter vis-à-vis de la stratégie.  
  
7.  Définissez une **Limite d’alerte quotidienne**, indiquez si l’alerte doit être envoyée sous forme d’e-mail et/ou de SMS et fournissez les détails nécessaires. Vous pouvez cliquer sur Enregistrer les paramètres d’alerte en tant que paramètres par défaut pour que les stratégies futures puissent enregistrer ces paramètres d’alerte, y compris les adresses de messagerie et le numéro de téléphone, en tant que paramètres par défaut.  
  
8.  Cliquez sur **Create (Créer)**.  
  
Par exemple, pour découvrir les applications d’hébergement à risque détectées dans votre environnement cloud, définissez votre stratégie comme suit :  
  
Définissez les filtres de stratégie pour découvrir tout service figurant dans la catégorie **Services d’hébergement** et ayant un indice faible, donc présentant un risque.   
Définissez la **Gravité** de la stratégie sur **Moyenne**.   
En bas, définissez les seuils qui doivent déclencher une alerte pour une application découverte donnée : uniquement si plus de 100 utilisateurs dans l’environnement ont utilisé l’application, et seulement s’ils ont téléchargé une certaine quantité de données à partir du service.   
En outre, vous pouvez définir la limite des alertes quotidiennes à recevoir.  
  
![exemple de stratégie de découverte d’application](./media/app-discovery-policy-example.png "exemple de stratégie de découverte d’application")  
  
## <a name="cloud-discovery-anomaly-detection"></a>Détection d’anomalie de Cloud Discovery  
Cloud App Security examine tous les journaux de votre environnement Cloud Discovery pour déterminer s’ils contiennent des anomalies. À titre d’exemple, citons un utilisateur qui n’a jamais utilisé Dropbox et qui y charge soudainement 600 Go de données ou une application qui fait l’objet de transactions dans des proportions inhabituelles. Par défaut, la stratégie de détection des anomalies est activée ; ainsi, vous n’avez pas besoin de configurer une nouvelle stratégie pour qu’elle fonctionne, mais vous pouvez affiner les types d’anomalies dont vous souhaitez être averti dans la stratégie par défaut.  
  
1.  Dans la console, cliquez sur **Contrôle**, puis sur **Stratégies**.  
  
2.  Cliquez sur **Créer une stratégie** et sélectionnez **Créer une stratégie de détection des anomalies de Cloud Discovery**.  
  
     ![menu Stratégie de détection des anomalies de Cloud Discovery](./media/cloud-discovery-anomaly-detection-policy-menu.png "menu Stratégie de détection des anomalies de Cloud Discovery")  
  
3.  Donnez à votre stratégie un nom et une description. Si vous le souhaitez, vous pouvez la baser sur un modèle ; pour plus d’informations sur les modèles de stratégie, consultez [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md).  
  
4.  Pour définir les applications découvertes qui doivent déclencher cette stratégie, cliquez sur **Ajouter des filtres**.  
  
     Vous pouvez choisir les filtres dans la partie gauche de la page de la fenêtre contextuelle des filtres. Vous pouvez filtrer par nom de service, domaine, facteur de risque, indice de risque et catégorie. Le côté droit de la page affiche les résultats des filtres choisis à partir du catalogue de services actuel. Après avoir choisi les filtres, enregistrez votre configuration et vérifiez que les étiquettes appropriées apparaissent dans la zone des filtres.  
  
5.  Sous **Appliquer à**, choisissez d’une part **Toutes les vues de données** ou **Vues de données spécifiques**, d’autre part **Utilisateurs** et/ou **Adresses IP**.  
  
6.  Sous **Générer des alertes uniquement en cas d’activités suspectes après la date**, sélectionnez les dates pendant lesquelles l’occurrence d’une activité anormale doit déclencher une alerte.  
  
7.  Sous **Alertes**, vous pouvez définir le niveau de sensibilité de la détection d’anomalies (de faible à élevé) pour configurer la fréquence des alertes à recevoir.  
Définissez une **Limite d’alerte quotidienne**, indiquez si l’alerte doit être envoyée sous forme d’e-mail et/ou de SMS et fournissez les détails nécessaires. Vous pouvez cliquer sur Enregistrer les paramètres d’alerte en tant que paramètres par défaut pour que les stratégies futures puissent enregistrer ces paramètres d’alerte, y compris les adresses de messagerie et le numéro de téléphone, en tant que paramètres par défaut. Vous pouvez également cliquer sur **Utiliser les paramètres par défaut de l’organisation** pour définir ces paramètres en fonction de la configuration par défaut de votre organisation.  
  
9. Cliquez sur **Create (Créer)**.  
  
![nouvelle stratégie de détection d’anomalie](./media/new-discovery-anomaly-policy.png "nouvelle stratégie de détection d’anomalie")  
  
## <a name="see-also"></a>Voir aussi  
[Stratégies d’activité utilisateur](user-activity-policies.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  