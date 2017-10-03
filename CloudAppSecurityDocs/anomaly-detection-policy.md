---
title: "Créer une stratégie de détection des anomalies dans Cloud App Security | Microsoft Docs"
description: "Cette rubrique fournit une description des stratégies de détection des anomalies ainsi que des informations de référence sur les composantes d’une stratégie de détection des anomalies."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 9/24/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: ab9bc377-d2f5-4f4c-a419-f1728a15d1c7
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 5ffc6d748e8a4050a40cfadc81d5b2267eae934d
ms.sourcegitcommit: 8759541301241e03784c5ac87b56986f22bd0561
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2017
---
# <a name="anomaly-detection-policy"></a>Stratégie de détection d’anomalie
Cet article fournit des informations de référence sur les stratégies, donne une explication de chaque type de stratégie et décrit les champs que vous pouvez configurer pour chacune d’elle.  

Une fois votre organisation protégée par Cloud App Security, toute l’activité cloud est évaluée en fonction de différents facteurs de risque prédéfinis. Cloud App Security examine chaque session utilisateur sur votre cloud, puis prend en considération les facteurs de risque que vous définissez ici afin d’être averti en cas d’événement anormal par rapport aux activités de référence ou habituelles de votre organisation ou de l’utilisateur. La page Stratégie de détection d’anomalie vous permet de configurer et de personnaliser les familles de facteurs de risque à prendre en compte dans le processus d’évaluation des risques. Vous pouvez adapter la stratégie en fonction de l’utilisateur, de l’emplacement ou du secteur de l’organisation. Par exemple, vous pouvez créer une stratégie qui vous avertit quand des membres de votre équipe informatique sont actifs en dehors de vos bureaux.  

Cloud App Security passe par une période d’apprentissage initiale de sept jours au cours de laquelle il ne signale pas les nouveaux utilisateurs, activités, appareils ni emplacements comme anormaux. Après cela, chaque session est comparée aux activités (activité des utilisateurs, adresses IP, appareils, etc.) détectées au cours du mois passé et à l’indice de risque de ces activités. Utilisez le curseur de sensibilité de la stratégie pour définir l’indice de risque minimal à partir duquel les alertes sont déclenchées. Quand vous créez une stratégie de détection d’anomalie, il est recommandé d’utiliser le seuil de sensibilité par défaut pendant une semaine avant de le modifier selon le nombre d’alertes reçues ; Cloud App Security vous envoie plus ou moins d’alertes pour les différents indices de risque quand vous modifiez le niveau de sensibilité.
  
![curseur de sensibilité](./media/sensitivity-slider.png)

Pour configurer une stratégie de détection d’anomalie :  
  
1.  Dans la console, cliquez sur **Contrôle**, puis sur **Stratégies**.  
  
2.  Cliquez sur **Créer une stratégie** et sélectionnez **Stratégie de détection d’anomalie**.  
  
     ![menu Stratégie de détection d’anomalie](./media/anomaly-detection-policy-menu.png "menu Stratégie de détection d’anomalie")  
  
3.  Indiquez le nom et la description de la stratégie et passez au champ **Filtres d’activité** où vous pouvez choisir l’activité pour laquelle vous souhaitez appliquer la stratégie.  
  
4.  Donnez à votre stratégie un nom et une description. Si vous le souhaitez, vous pouvez la baser sur un modèle ; pour plus d’informations sur les modèles de stratégie, consultez [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md).  
  
5.  Pour appliquer la stratégie à toutes les activités dans votre environnement cloud, sélectionnez **Toutes les activités surveillées**. Pour limiter la stratégie à des types d’activités spécifiques, choisissez **Activité sélectionnée**. Cliquez sur **Ajouter des filtres** et définissez les paramètres appropriés en fonction desquels filtrer l’activité. Par exemple, pour appliquer la stratégie uniquement sur une activité effectuée par les administrateurs Salesforce, vous choisissez l’étiquette utilisateur correspondante.  
  
6.  En dessous de ce champ, définissez les **Facteurs de risque**. Vous pouvez choisir les familles de risques à prendre en compte pour le calcul de l’indice de risque. À droite de la ligne, vous pouvez utiliser le bouton Activer/Désactiver pour activer ou désactiver les différents risques. En outre, pour plus de précision, vous pouvez choisir l’activité sur laquelle activer chaque famille de risques particulière.  
  
     Les facteurs de risque sont les suivants :  
  
    -   **Échecs de connexion** : Des utilisateurs se connectent-ils sans succès plusieurs fois pendant une courte période ?  
  
    -   **Activité administrative** : Des administrateurs utilisent-ils leurs comptes privilégiés pour se connecter à partir des emplacements inhabituels ou à des heures inhabituelles ?  
  
    -   **Comptes inactifs** : Existe-t-il une activité soudaine sur un compte qui n’a pas été utilisé pendant un certain temps ?  
  
    -   **Lieu** : Y a-t-il une activité dans un emplacement inhabituel, suspect ou nouveau ?  
  
    -   **Voyage impossible** : Un utilisateur se connecte-t-il depuis Denver, puis 10 minutes plus tard depuis Paris ?  
  
    -   **Agent Appareil et utilisateur** : Existe-t-il une activité à partir d’un appareil non reconnu ou non géré ?  

    -   **Taux d’activité** : L’activité augmente-t-elle soudainement sur une application donnée ? Constatez-vous des téléchargements ou suppressions conséquents, un grand nombre de fichiers partagés ou de nombreuses activités d’administration inattendues ?
  
     Vous pouvez utiliser ces paramètres pour définir des scénarios complexes, par exemple, pour exclure la plage d’adresses IP de votre bureau des facteurs de risque pris en compte pour la détection d’anomalies ou pour créer une étiquette « Plage IP du bureau » spécifique et exclure la plage des paramètres pris en compte. Pour exclure la plage ainsi créée de la détection d’anomalie dans l’activité administrative, procédez comme suit :  
  
    -   Dans **Type de risque**, recherchez **Activité administrative**.  
  
    -   Définissez **Appliquer à** sur **Activité sélectionnée**.  
  
    -   Sous **Filtres d’activité**, définissez **Appliquer à** sur **Activité sélectionnée** et sous **Activités remplissant toutes les conditions suivantes**, choisissez **Activité administrative** est **Vrai**.  
  
    -   Cliquez sur l’icône **+** et sélectionnez **Étiquette IP n’est pas égal à** et sélectionnez la balise Plage IP du bureau.  
  
7.  Sous **Sensibilité**, sélectionnez la fréquence à laquelle vous souhaitez recevoir les alertes.  
  
     La valeur de la sensibilité détermine le nombre d’alertes hebdomadaires déclenchées en moyenne par tranche de 1 000 utilisateurs.  
  
     ![adresses IP de détection des anomalies](./media/anomaly-detection-ips.png "adresses IP de détection des anomalies")  
  
8.  Cliquez sur **Créer**.  
 

## <a name="anomaly-detection-policy-reference"></a>Informations de référence sur les stratégies de détection d’anomalie  
Une stratégie de détection d’anomalie vous permet d’installer et de configurer une surveillance continue de l’activité des utilisateurs afin de détecter d’éventuelles anomalies de comportement. Ces anomalies sont détectées en analysant l’activité des utilisateurs. Le risque est évalué en examinant plus de 30 indicateurs de risque différents, regroupés en 6 facteurs de risque. Selon les résultats de la stratégie, des alertes de sécurité sont déclenchées.   
Chaque stratégie comprend les éléments suivants :  
  
-   Filtres d’activité : Vous permettent d’analyser de manière sélective uniquement l’activité filtrée des utilisateurs afin de détecter d’éventuelles anomalies.  
  
-   Facteurs de risque : Vous permettent de choisir les facteurs de risque à inclure lors de l’évaluation des risques.  
  
-   Sensibilité : Vous permet de définir le nombre d’alertes que la stratégie doit déclencher.  
  
### <a name="activity-filters"></a>Filtres d’activité  
Pour obtenir une liste des filtres d’activité, voir [entrer la description du lien ici](activity-filters.md).  
  
### <a name="risk-factors"></a>Facteurs de risque  
Voici la liste des facteurs de risque pris en compte lors de l’évaluation du risque lié à l’activité des utilisateurs. Chaque facteur de risque peut être activé ou désactivé. Pour chaque facteur de risque, il existe deux options sous le champ **Appliquer à**, qui déterminent leur inclusion ou exclusion lors de l’évaluation du risque lié à l’activité des utilisateurs :  
  
-   Toutes les activités surveillées : Incluez le facteur de risque pour toutes les activités des utilisateurs qui passent le filtre d’activité de stratégie.  
  
-   Activité sélectionnée : Incluez le facteur de risque pour les activités des utilisateurs qui passent à la fois les filtres d’activité de stratégie et les filtres d’activité qui s’affichent sous ce facteur de risque. Lorsque cette option est sélectionnée, un sélecteur de filtre d’activité apparaît sous le facteur de risque, lequel fonctionne exactement comme le filtre d’activité de stratégie.  
  
Chaque facteur de risque, s’il est inclus dans l’évaluation des risques, a ses propres déclencheurs qui entraînent une augmentation du risque évalué lié à l’activité des utilisateurs :  
  
-   Échecs de connexion : Nombre élevé d’échecs de connexion ou activité entièrement composée d’échecs de connexion.  
  
-   Activité administrative : Activité administrative effectuée par un utilisateur inattendu, ou à partir d’une adresse IP, d’un fournisseur de services Internet ou d’un emplacement qui sont nouveaux ou non utilisés par d’autres utilisateurs de l’organisation.  
  
-   Comptes inactifs : Activité effectuée par un utilisateur qui n’a pas été actif depuis un long moment.  
  
-   Emplacement : Activité effectuée à partir d’une adresse IP, d’un fournisseur de services Internet ou d’un emplacement qui n’ont jamais été utilisés par un autre utilisateur, jamais été utilisés par cet utilisateur particulier, jamais été utilisés du tout ou utilisés uniquement pour des échecs de connexion par le passé.  
  
-   Voyage impossible : Activité à partir d’emplacements distants pendant un laps de temps court.  
  
-   Agent Appareil et utilisateur : Activité effectuée par un utilisateur à l’aide d’un agent utilisateur ou d’un appareil qui n’a jamais été utilisé par un autre utilisateur, jamais été utilisé par cet utilisateur particulier ou jamais été utilisé du tout.  
  
-   Taux d’activité : activités répétées effectuées par un utilisateur sur une courte période. 

### <a name="sensitivity"></a>Sensibilité  
Il existe deux façons de contrôler le nombre d’alertes déclenchées par la stratégie :  
  
-   Curseur Sensibilité : Choisissez le nombre d’alertes à déclencher pour 1 000 utilisateurs par semaine. Les alertes sont déclenchées pour les activités dont le risque est le plus élevé.  
  
-   Limite d’alerte quotidienne : Restreignez le nombre d’alertes générées sur une journée.  
  
## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   
[Pour obtenir du support technique, consultez la page Support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  
