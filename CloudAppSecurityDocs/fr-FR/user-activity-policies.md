---
title: Création de stratégies pour contrôler les activités dans Cloud App Security | Microsoft Docs
description: Cette rubrique fournit des instructions sur la création et l’utilisation de stratégies d’activité.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 99d5fd37-d922-4269-b557-86d7f84180eb
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 87e05e1b28ef469b6f180fbd4479ac6727b22f3b
ms.sourcegitcommit: 45311f2cafef79483e40d971a4c61c7673834d96
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2018
---
*S’applique à : Microsoft Cloud App Security*


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
  
  
## <a name="activity-policy-reference"></a>Informations de référence sur les stratégies d’activité  
Cette section fournit des informations de référence sur les stratégies, donne une explication de chaque type de stratégie et décrit les champs que vous pouvez configurer pour chacune d’elles.  
  
Une **stratégie d’activité** est une stratégie basée sur une API qui vous permet de surveiller les activités de votre organisation dans le cloud, en prenant en considération plus de 20 filtres de métadonnées de fichiers (notamment le type et l’emplacement de l’appareil). Selon les résultats de la stratégie, des notifications peuvent être générées et des utilisateurs peuvent être exclus temporairement de l’application cloud.   
Chaque stratégie comprend les éléments suivants :  
  
- Filtres d’activité : Vous permettent de créer des conditions très précises en fonction de métadonnées.  
  
- Paramètres de correspondance de l’activité : Vous permettent de définir un seuil pour le nombre de fois qu’une activité se répète pour être considérée comme correspondant à la stratégie.  Spécifiez le nombre d’activités répétées nécessaires pour correspondre à la stratégie, par exemple en définissant une stratégie qui émet une alerte quand un utilisateur effectue sans succès 10 tentatives de connexion dans un délai de 2 minutes.  Par défaut, **Paramètres de correspondance de l’activité**, déclenche une correspondance pour chaque activité unique qui satisfait à tous les filtres d’activité.   
  À l’aide de l’option **Activité répétée**, vous pouvez définir le nombre d’activités répétées, la durée du délai d’exécution dans lequel les activités sont comptabilisées et même spécifier que toutes les activités doivent être effectuées par le même utilisateur et dans la même application cloud.  
  
  
- Actions : La stratégie fournit un ensemble d’actions de gouvernance automatiquement applicables en cas de violations détectées.  
  ## <a name="see-also"></a>Voir aussi  
  [Stratégies de protection des données](data-protection-policies.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  