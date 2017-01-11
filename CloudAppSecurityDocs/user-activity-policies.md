---
title: "Stratégies d’activité | Microsoft Docs"
description: "Cette rubrique fournit des instructions sur la création et l’utilisation de stratégies d’activité."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 99d5fd37-d922-4269-b557-86d7f84180eb
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2997a79f2e0fd730302be2602b6aee6ec56999db
ms.openlocfilehash: 46ab0f13a8d0839f77525c334e75c840c9bfc73f


---

# <a name="activity-policies"></a>Stratégies d’activité
Grâce aux stratégies d’activité, vous pouvez appliquer une large gamme de processus automatisés en exploitant les API du fournisseur d’application. Ces stratégies vous permettent de surveiller des activités spécifiques effectuées par différents utilisateurs ou de suivre les taux anormalement élevés d’un certain type d’activité.  
  
Après avoir défini une stratégie de détection d’activité, elle commence à générer des alertes ; les alertes sont générées uniquement sur les activités qui se produisent après avoir créé la stratégie.
  
  
## <a name="custom-alerts"></a>Alertes personnalisées  
Grâce aux stratégies d’activité, vous pouvez définir des alertes personnalisées à envoyer ou des actions à entreprendre en cas de détection d’une activité utilisateur. Par exemple, si vous souhaitez être systématiquement averti qu’un utilisateur a tenté sans succès de se connecter à 70 reprises en une minute, qu’il télécharge 7 000 fichiers ou qu’il est connecté depuis l’Afghanistan, vous pouvez définir des alertes d’activité à envoyer à vous-même ou à l’utilisateur quand ces événements se produisent. Vous pouvez même suspendre l’utilisateur jusqu’à ce que vous ayez examiné ce qui est arrivé.  
  
Pour créer une stratégie d’activité, procédez comme suit :  
  
1.  Dans la console, cliquez sur **Contrôle**, puis sur **Stratégies**.  
  
2.  Cliquez sur **Créer une stratégie** et sélectionnez **Stratégie d’activité**.  
  
     ![menu Stratégie d’activité](./media/activity-policy-menu.png "menu Stratégie d’activité")  
  
3.  Donnez à votre stratégie un nom et une description. Si vous le souhaitez, vous pouvez la baser sur un modèle ; pour plus d’informations sur les modèles de stratégie, consultez [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md).  
  
4.  Pour définir les actions ou autres mesures susceptibles de déclencher cette stratégie, utilisez les **Filtres d’activité**.  
  
5.  Sous **Paramètres de correspondance de l’activité**, indiquez si une violation de stratégie est déclenchée quand une seule activité satisfait aux filtres ou si une violation est détectée uniquement quand un **Nombre d’activités répétées** spécifié est constaté.  
    Si vous choisissez **Activité répétée**, vous pouvez définir **Grouper les activités correspondantes par application**. Cela déclenche une correspondance de stratégie uniquement lorsque les activités répétées se produisent dans la même application (par exemple, 5 téléchargements depuis Box).  
  
6.  Configurez les **Actions** à effectuer quand une correspondance est trouvée.  
  
Jetez un œil aux exemples suivants :  
  
-   Plusieurs échecs de connexion  
  
     Vous pouvez définir votre stratégie afin de recevoir une alerte quand un grand nombre de tentatives de connexion ont échoué pendant une période relativement courte. Pour configurer une stratégie de ce type, choisissez le filtre d’activité approprié dans la page **Nouvelle stratégie d’activité**.  
  
     Sous le champ **Filtres d’activité**, configurez les paramètres pour lesquels l’alerte doit être déclenchée.  
  
     ![exemple de stratégie, échec de plusieurs tentatives de connexion](./media/multiple-failed-log-on-attempts-policy-example.png "exemple de stratégie, échec de plusieurs tentatives de connexion")  
  
-   Taux de téléchargement élevé  
  
     Vous pouvez définir votre stratégie afin de recevoir une alerte en cas de niveau d’activité de téléchargement anormal ou inhabituel. Pour configurer une stratégie de ce type, sous les paramètres **Taux**, choisissez les paramètres devant déclencher l’alerte.  
  
     ![exemple de taux de téléchargement élevé](./media/high-download-rate-example.png "exemple de taux de téléchargement élevé")  
  
## <a name="anomaly-detection"></a>Détection d’anomalie  
Une fois votre organisation protégée par Cloud App Security, toute l’activité cloud est évaluée en fonction de différents facteurs de risque prédéfinis. Cloud App Security examine chaque session utilisateur sur votre cloud, puis prend en considération les facteurs de risque que vous définissez ici afin d’être averti en cas d’événement anormal par rapport aux activités de référence ou habituelles de votre organisation ou de l’utilisateur. La page Stratégie de détection d’anomalie vous permet de configurer et de personnaliser les familles de facteurs de risque à prendre en compte dans le processus d’évaluation des risques. Vous pouvez adapter la stratégie en fonction de l’utilisateur, de l’emplacement ou du secteur de l’organisation. Par exemple, vous pouvez créer une stratégie qui vous avertit quand des membres de votre équipe informatique sont actifs en dehors de vos bureaux.  
  
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
  
    -   **Voyage impossible** : Un utilisateur se connecte-t-il depuis Denver, puis dix minutes plus tard depuis Paris ?  
  
    -   **Agent Appareil et utilisateur** : Existe-t-il une activité à partir d’un appareil non reconnu ou non géré ?  
  
     Vous pouvez utiliser ces paramètres pour définir des scénarios complexes, par exemple, pour exclure la plage d’adresses IP de votre bureau des facteurs de risque pris en compte pour la détection d’anomalies ou pour créer une étiquette « Plage IP du bureau » spécifique et exclure la plage des paramètres pris en compte. Pour exclure la plage ainsi créée de la détection d’anomalie dans l’activité administrative, procédez comme suit :  
  
    -   Dans **Type de risque**, recherchez **Activité administrative**.  
  
    -   Définissez **Appliquer à** sur **Activité sélectionnée**.  
  
    -   Sous **Filtres d’activité**, définissez **Appliquer à** sur **Activité sélectionnée** et sous **Activities matching all of the following** (Les activités satisfont à toutes les conditions suivantes), choisissez **Activité administrative** est **Vrai**.  
  
    -   Cliquez sur l’icône **+** et sélectionnez **Étiquette IP n’est pas égal à** et sélectionnez la balise Plage IP du bureau.  
  
7.  Sous **Sensibilité**, sélectionnez la fréquence à laquelle vous souhaitez recevoir les alertes.  
  
     La valeur de la sensibilité détermine le nombre d’alertes hebdomadaires déclenchées en moyenne par tranche de 1 000 utilisateurs.  
  
     ![adresses IP de détection des anomalies](./media/anomaly-detection-ips.png "adresses IP de détection des anomalies")  
  
8.  Cliquez sur **Create (Créer)**.  
 
  
## <a name="activity-policy-reference"></a>Informations de référence sur les stratégies d’activité  
Cette section fournit des informations de référence sur les stratégies, donne une explication de chaque type de stratégie et décrit les champs que vous pouvez configurer pour chacune d’elles.  
  
Une **stratégie d’activité** est une stratégie basée sur une API qui vous permet de surveiller les activités de votre organisation dans le cloud, en prenant en considération plus de 20 filtres de métadonnées de fichiers (notamment le type et l’emplacement de l’appareil). Selon les résultats de la stratégie, des notifications peuvent être générées et des utilisateurs peuvent être exclus temporairement de l’application cloud.   
Chaque stratégie comprend les éléments suivants :  
  
-   Filtres d’activité : Vous permettent de créer des conditions très précises en fonction de métadonnées.  
  
-   Paramètres de correspondance de l’activité : Vous permettent de définir un seuil pour le nombre de fois qu’une activité se répète pour être considérée comme correspondant à la stratégie.  Spécifiez le nombre d’activités répétées nécessaires pour correspondre à la stratégie, par exemple en définissant une stratégie qui émet une alerte quand un utilisateur effectue sans succès 10 tentatives de connexion dans un délai de 2 minutes.  Par défaut, **Paramètres de correspondance de l’activité**, déclenche une correspondance pour chaque activité unique qui satisfait à tous les filtres d’activité.   
À l’aide de l’option **Activité répétée**, vous pouvez définir le nombre d’activités répétées, la durée du délai d’exécution dans lequel les activités sont comptabilisées et même spécifier que toutes les activités doivent être effectuées par le même utilisateur et dans la même application cloud.  
  
  
-   Actions : La stratégie fournit un ensemble d’actions de gouvernance automatiquement applicables en cas de violations détectées.  
## <a name="see-also"></a>Voir aussi  
[Stratégies de protection des données](data-protection-policies.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Dec16_HO3-->


