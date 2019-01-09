---
title: Créer des stratégies pour contrôler les activités dans Cloud App Security
description: Cet article fournit des instructions sur la création et l’utilisation de stratégies d’activité.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/14/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 99d5fd37-d922-4269-b557-86d7f84180eb
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: c98b01083b964901d3ff2823fff35c9702ddcd17
ms.sourcegitcommit: 420a0119513e3f4a8651f6a9e66c56fe442a31c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53347301"
---
# <a name="activity-policies"></a>Stratégies d’activité

*S’applique à : Microsoft Cloud App Security*

Avec les stratégies d’activité, vous pouvez appliquer une large gamme de processus automatisés en utilisant les API du fournisseur d’application. Ces stratégies vous permettent de surveiller des activités spécifiques effectuées par différents utilisateurs ou de suivre les taux anormalement élevés d’un certain type d’activité.  
  
Après avoir défini une stratégie de détection d’activité, elle commence à générer des alertes ; les alertes sont générées uniquement sur les activités qui se produisent après avoir créé la stratégie.
  
  
## <a name="custom-alerts"></a>Alertes personnalisées  

Grâce aux stratégies d’activité, vous pouvez envoyer des alertes personnalisées ou entreprendre des actions en cas de détection d’une activité utilisateur. Par exemple, vous souhaitez être informé dans les cas suivants :

- Un utilisateur tente de se connecter et échoue à 70 reprises en une minute
- Un utilisateur télécharge 7 000 fichiers
- Un utilisateur est connecté depuis l’Afghanistan

Lorsque ces événements se produisent, vous pouvez choisir de recevoir vous-même ces alertes d’activité ou les envoyer à l’utilisateur. Vous pouvez même suspendre l’utilisateur jusqu’à ce que vous ayez examiné ce qui est arrivé.  
  
Pour créer une stratégie d’activité, procédez comme suit :  
  
1. Dans la console, cliquez sur **Contrôle**, puis sur **Stratégies**.  
  
2. Cliquez sur **Créer une stratégie** et sélectionnez **Stratégie d’activité**.  
  
     ![menu Stratégie d’activité](./media/activity-policy-menu.png "menu Stratégie d’activité")  
  
3. Donnez à votre stratégie un nom et une description. Si vous le souhaitez, vous pouvez la baser sur un modèle ; pour plus d’informations sur les modèles de stratégie, consultez [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md).  
  
4. Pour définir les actions ou autres mesures susceptibles de déclencher cette stratégie, utilisez les **Filtres d’activité**.  
  
5. Sous **Paramètres de correspondance de l’activité**, sélectionnez le moment auquel la violation de stratégie est déclenchée. Vous pouvez choisir de déclencher l’action lorsqu’une seule activité correspond aux filtres, ou lorsqu’un certain nombre d’**activités répétées** sont détectées.  
    - Si vous choisissez **Activité répétée**, vous pouvez également définir **Dans une seule application**. Ce paramètre déclenchera une correspondance de stratégie uniquement lorsque les activités répétées se produisent dans la même application. Par exemple, 5 téléchargements depuis Box en 30 minutes déclenchent une correspondance de stratégie.  
  
6. Configurez les **Actions** à effectuer quand une correspondance est trouvée.  
  
Jetez un œil aux exemples suivants :  
  
- Plusieurs échecs de connexion  
  
     Vous pouvez définir la stratégie de sorte à recevoir une alerte lorsqu’un grand nombre d’échecs de connexion se produisent sur une courte durée. Pour configurer ce type de stratégie, choisissez le filtre d’activité approprié dans la page **Nouvelle stratégie d’activité**.  
  
     Sous le champ **Filtres d’activité**, configurez les paramètres pour lesquels l’alerte doit être déclenchée.  
  
     ![Exemple de stratégie en cas d’échec de plusieurs tentatives de connexion](./media/multiple-failed-log-on-attempts-policy-example.png "exemple de stratégie en cas d’échec de plusieurs tentatives d’ouverture de session")  
  
- Taux de téléchargement élevé  
  
     Vous pouvez définir votre stratégie afin de recevoir une alerte en cas de niveau d’activité de téléchargement anormal ou inhabituel. Pour configurer ce type de stratégie, sous les paramètres **Taux**, choisissez les paramètres devant déclencher l’alerte.  
  
     ![exemple de taux de téléchargement élevé](./media/high-download-rate-example.png "exemple de taux de téléchargement élevé")  
  
  
## <a name="activity-policy-reference"></a>Informations de référence sur les stratégies d’activité  

Cette section offre des informations de référence sur les stratégies, explique chaque type de stratégie et décrit les champs que vous pouvez configurer pour chacune d’elles.  
  
Une **Stratégie d’activité** constitue une stratégie basée sur API qui vous permet de surveiller les activités de votre organisation dans le cloud. La stratégie prend en compte plus de 20 filtres de métadonnées de fichiers, notamment l’emplacement et le type d’appareil. Selon les résultats de la stratégie, des notifications peuvent être générées et des utilisateurs peuvent être exclus temporairement de l’application cloud.
Chaque stratégie comprend les éléments suivants :  
  
- Filtres d’activité : Vous permettent de créer des conditions précises en fonction des métadonnées.  
  
- Paramètres de correspondance de l’activité : Vous permettent de définir un seuil pour le nombre de fois qu’une activité se répète pour être considérée comme correspondant à la stratégie.  Spécifiez le nombre d’activités répétées nécessaires pour correspondre à la stratégie. Par exemple, définissez une stratégie pour vous informer lorsqu’un utilisateur atteint 10 tentatives de connexion échouées en 2 minutes ou moins. Par défaut, le **Paramètre de correspondance de l’activité déclenche une correspondance pour chaque activité unique qui satisfait à tous les filtres d’activité.

  - À l’aide du paramètre **Activité répétée**, vous pouvez définir le nombre d’activités répétées et la durée de l’intervalle pendant lequel elles sont comptabilisées. Vous pouvez également spécifier que toutes les activités doivent être effectuées par le même utilisateur et dans la même application cloud.  
  
  
- Actions : La stratégie fournit un ensemble d’actions de gouvernance automatiquement applicables en cas de violations détectées.  
  
## <a name="next-steps"></a>Étapes suivantes
  
[Stratégies de protection des données](data-protection-policies.md)

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)  
  
