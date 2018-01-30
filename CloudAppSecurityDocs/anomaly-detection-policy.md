---
title: "Créer une stratégie de détection des anomalies dans Cloud App Security | Microsoft Docs"
description: "Cette rubrique fournit une description des stratégies de détection des anomalies ainsi que des informations de référence sur les composantes d’une stratégie de détection des anomalies."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/21/2018
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: ab9bc377-d2f5-4f4c-a419-f1728a15d1c7
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 9d93cf34908a357a80d5f98ec5c6ebe401789845
ms.sourcegitcommit: 4fdf9ae2e2b189d4efa6a6588898c8d46d0dda70
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2018
---
# <a name="anomaly-detection-policy"></a>Stratégie de détection d’anomalie
Cet article fournit des informations de référence sur les stratégies, donne une explication de chaque type de stratégie et décrit les champs que vous pouvez configurer pour chacune d’elle.  

Une fois votre organisation protégée par Cloud App Security, toute l’activité cloud est évaluée en fonction de différents facteurs de risque prédéfinis. Cloud App Security examine chaque session utilisateur sur votre cloud, puis prend en considération les facteurs de risque que vous définissez ici afin d’être averti en cas d’événement anormal par rapport aux activités de référence ou habituelles de votre organisation ou de l’utilisateur. Vous pouvez adapter la stratégie en fonction de l’utilisateur, de l’emplacement ou du secteur de l’organisation. Par exemple, vous pouvez créer une stratégie qui vous avertit quand des membres de votre équipe informatique sont actifs en dehors de vos bureaux.  

Cloud App Security passe par une période d’apprentissage initiale de sept jours au cours de laquelle il ne signale pas les nouveaux utilisateurs, activités, appareils ni emplacements comme anormaux. Après cela, chaque session est comparée aux activités (activité des utilisateurs, adresses IP, appareils, etc.) détectées au cours du mois passé et à l’indice de risque de ces activités. 


Les stratégies de détection d’anomalie suivantes sont disponibles :

**Voyage impossible**
- Cette détection fait partie du moteur de détection des anomalies global qui profile votre environnement et déclenche des alertes suivant une base de référence qui a été définie par rapport à l’activité de votre organisation. Elle identifie deux activités de l’utilisateur (dans une ou plusieurs sessions) provenant d’emplacements éloignés sur une durée plus courte que la durée nécessaire à l’utilisateur pour aller du premier emplacement au second, ce qui indique qu’un autre utilisateur utilise les mêmes informations d’identification. Cette détection s’appuie sur un algorithme d’apprentissage automatique qui ignore les « faux positifs » évidents contribuant à la condition de voyage impossible, comme les réseaux privés virtuels et les emplacements régulièrement utilisés par d’autres utilisateurs de l’organisation. La détection a une période d’apprentissage initiale de 7 jours au cours de laquelle elle apprend le modèle d’activité d’un nouvel utilisateur.


**Activité à partir de pays peu fréquents**
- Cette détection fait partie du moteur de détection des anomalies global qui profile votre environnement et déclenche des alertes suivant une base de référence qui a été définie par rapport à l’activité de votre organisation. Cette détection prend en compte les emplacements d’activité précédents pour identifier les emplacements nouveaux et peu fréquentés. Le moteur de détection des anomalies stocke les informations sur les emplacements précédents employés par les utilisateurs de l’organisation. Une alerte est déclenchée quand une activité se produit à partir d’un emplacement qui n’a pas été récemment visité ou qui ne l’a jamais été par l’utilisateur ou par aucun utilisateur de l’organisation. La détection a une période d’apprentissage initiale de 7 jours au cours de laquelle elle n’envoie aucune alerte sur aucun emplacement nouveau.


**Activité depuis des adresses IP anonymes**
- Cette détection fait partie du moteur de détection des anomalies global qui profile votre environnement et déclenche des alertes suivant une base de référence qui a été définie par rapport à l’activité de votre organisation. Cette détection identifie que des utilisateurs étaient actifs à partir d’une adresse IP qui a été identifiée comme adresse IP proxy anonyme. Ces proxys sont utilisés par des personnes qui veulent masquer l’adresse IP de leur appareil dans un but qui peut être malveillant. Cette détection s’appuie sur un algorithme d’apprentissage automatique qui réduit les « faux positifs », comme les adresses IP mal balisées qui sont couramment utilisées par les utilisateurs de l’organisation.

**Activité à partir d’adresses IP suspectes**
- Cette détection fait partie du moteur de détection des anomalies global qui profile votre environnement et déclenche des alertes suivant une base de référence qui a été définie par rapport à l’activité de votre organisation. Cette détection identifie que des utilisateurs étaient actifs à partir d’une adresse IP qui a été identifiée comme à risque par Microsoft Threat Intelligence. Ces IP sont impliqués dans des activités malveillantes, comme Botnet C&C, et peuvent être le signe de compte compromis. Cette détection s’appuie sur un algorithme d’apprentissage automatique qui réduit les « faux positifs », comme les adresses IP mal balisées qui sont couramment utilisées par les utilisateurs de l’organisation.


**Activité X inhabituelle (par utilisateur)**
- Cette détection fait partie du moteur de détection des anomalies global qui profile votre environnement et déclenche des alertes suivant une base de référence qui a été définie par rapport à l’activité de votre organisation. Cette détection identifie des utilisateurs qui effectuent plusieurs activités X dans une seule session en prenant en compte la base de référence apprise, ce qui peut indiquer une tentative de violation. Cette détection s’appuie sur un algorithme d’apprentissage automatique qui profile le modèle de connexion des utilisateurs et réduit les « faux positifs ».


**Plusieurs tentatives de connexion infructueuses**
- Cette détection fait partie du moteur de détection des anomalies global qui profile votre environnement et déclenche des alertes suivant une base de référence qui a été définie par rapport à l’activité de votre organisation. Cette détection identifie des utilisateurs qui tentent de se connecter plusieurs fois sans succès dans une seule session en prenant en compte la base de référence apprise, ce qui peut indiquer une tentative de violation. Cette détection s’appuie sur un algorithme d’apprentissage automatique qui profile le modèle de connexion des utilisateurs et réduit les « faux positifs ».

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
Pour contrôler le nombre d’alertes déclenchées par la stratégie, définissez la **limite d’alerte quotidienne** et limitez le nombre d’alertes déclenchées par jour.  
  
## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  
