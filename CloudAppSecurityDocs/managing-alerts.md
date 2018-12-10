---
title: Gérer les alertes déclenchées dans le portail Cloud App Security | Microsoft Docs
description: Cet article explique comment utiliser les alertes déclenchées dans le portail Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 1b1dbcc6-472f-43ea-af59-2aa926e3e5a9
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 7da46fcd18ad80f0df975ba4ff6fa927cc8594c6
ms.sourcegitcommit: b0b3e6c6f150fff8c286185826ce099601a12679
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2018
ms.locfileid: "52280610"
---
# <a name="manage-alerts"></a>Gérer les alertes

*S’applique à : Microsoft Cloud App Security*

Cet article explique comment utiliser les alertes déclenchées dans le portail Cloud App Security.

## <a name="manage-your-alerts"></a>Gérer vos alertes

Les alertes constituent un bon point de départ pour comprendre votre environnement cloud de façon plus approfondie. Vous pouvez créer des stratégies selon ce que vous trouvez. Par exemple, vous pouvez voir un administrateur qui se connecte depuis le Groenland, alors que personne dans votre organisation ne s’est jamais connecté à partir de là auparavant. Vous pouvez créer une stratégie qui suspend automatiquement un compte d’administrateur quand il est utilisé pour se connecter à partir cet emplacement.  

Il est judicieux d’examiner toutes vos alertes et de vous en servir pour modifier vos stratégies. Si des événements sans incidence sont considérés comme des violations de stratégies existantes, affinez vos stratégies afin de recevoir moins d’alertes inutiles.  

1. Dans la page **Alertes**, sélectionnez **Ouvert** comme **État de résolution**.  

   Cette section du tableau de bord fournit une visibilité totale de toute activité suspecte ou des violations de vos stratégies établies. Elle peut vous aider à préserver le plan de sécurité que vous avez défini pour votre environnement cloud.  

   ![Alertes](./media/alerts.png "alertes")  

2. Pour chaque alerte, vous devez examiner et déterminer la nature de la violation et la réponse requise.  

   - Vous pouvez filtrer les alertes par type d’alerte ou par gravité afin de traiter d’abord les plus importantes.  

   - Sélectionnez une alerte spécifique. En fonction du type d’alerte dont il s’agit, vous voyez différentes actions que vous pouvez effectuer avant de résoudre l’alerte.  
   
   - Vous pouvez filtrer en fonction de l’application : les applications listées sont celles pour lesquelles des activités ont été détectées par Cloud App Security.

   - Il existe trois types de violations que vous devez traiter quand vous examinez les alertes :  

       - **Violations graves** : les violations graves nécessitent une réponse immédiate. <br>
     *Exemples :*
         - Pour une alerte d’activité suspecte, vous pouvez suspendre le compte jusqu’à ce que l’utilisateur change son mot de passe.  
         - Pour une fuite de données, vous voudrez probablement restreindre les autorisations ou mettre le fichier en quarantaine.  
         - Si une nouvelle application est découverte, vous voudrez probablement bloquer l’accès au service sur votre proxy ou pare-feu.  

       - **Violations contestables** : les violations contestables nécessitent un examen plus approfondi.  <br>
         - Vous pouvez contacter l’utilisateur ou le responsable de l’utilisateur pour lui demander la nature de l’activité.
         - Laissez l’activité ouverte jusqu’à ce que vous ayez plus d’informations.  

       - **Violations autorisées ou comportements anormaux** : les violations autorisées ou les comportements anormaux peuvent provenir d’une utilisation légitime.  

   - Supprimez l’alerte.  

3. Quand vous avez terminé ce processus, marquez l’alerte comme résolue.  

## <a name="alert-types"></a>Types d’alertes

Le tableau suivant contient une liste des types d’alertes qui peuvent être déclenchées et les méthodes recommandées pour y remédier.  

|Type d’alerte|Description|Résolution recommandée|  
|----------------|-----------------|----------------------------|  
|Violation de stratégie d’activité|Ce type d’alerte est le résultat d’une stratégie que vous avez créée.|Pour utiliser en bloc ce type d’alerte, il est recommandé de travailler directement depuis le Centre de stratégie pour les limiter.<br /><br /> Ajustez la stratégie pour exclure les entités générant du bruit en ajoutant davantage de filtres et des contrôles plus granulaires.<br /><br /> Si la stratégie est précise, que l’alerte est justifiée et qu’il s’agit d’une violation que vous voulez arrêter immédiatement, ajoutez une correction automatique dans la stratégie.|  
|Violation de stratégie de fichier|Ce type d’alerte est le résultat d’une stratégie que vous avez créée.| Pour utiliser en bloc ce type d’alerte, il est recommandé de travailler directement depuis le Centre de stratégie pour les limiter.<br /><br /> Ajustez la stratégie pour exclure les entités générant du bruit en ajoutant davantage de filtres et des contrôles plus granulaires.<br /><br /> Si la stratégie est précise, que l’alerte est justifiée et qu’il s’agit d’une violation que vous voulez arrêter immédiatement, ajoutez une correction automatique dans la stratégie.|  
|Compte compromis|Ce type d’alerte est déclenché quand Cloud App Security identifie un compte qui a été compromis. Cela signifie qu’il est fort probable que le compte ait été utilisé de façon non autorisée.|Il est recommandé de suspendre le compte tant que vous n’avez pas contacté l’utilisateur et vérifié qu’il a changé son mot de passe.|  
|Compte inactif|Cette alerte se déclenche quand un compte n’a pas été utilisé depuis 60 jours dans l’une de vos applications cloud connectées.|Contactez l’utilisateur et le responsable de l’utilisateur pour déterminer si le compte est encore actif. Si ce n’est pas le cas, suspendez l’utilisateur et mettez un terme à sa licence pour l’application.|  
|Nouvel utilisateur administrateur|Vous signale que des modifications ont été apportées dans vos comptes privilégiés pour des applications connectées.|Vérifiez que les nouvelles autorisations d’administration sont bien nécessaires pour l’utilisateur. Si ce n’est pas le cas, nous recommandons de révoquer les privilèges d’administrateur de façon à réduire l’exposition.|  
|Nouvel emplacement administrateur|Vous signale que des modifications ont été apportées dans vos comptes privilégiés pour des applications connectées.|Vérifiez que la connexion à partir de cet emplacement anormal était légitime. Si ce n’est pas le cas, nous recommandons de révoquer les autorisations d’administration ou de suspendre le compte de façon à réduire l’exposition.|  
|Nouvel emplacement|Alerte à titre d’information sur l’accès à une application connectée à partir d’un nouvel emplacement. Elle se déclenche une seule fois par pays.|Examinez les activités de l’utilisateur concerné.|  
|Nouveau service découvert|Cet alerte concerne l’informatique fantôme. Une nouvelle application a été détectée par Cloud Discovery.|<ul><li>Évaluez le risque du service en fonction du catalogue d’applications.</li><li>Explorez l’activité au niveau du détail pour en comprendre les modèles d’utilisation et la fréquence.</li><li>Décidez d’approuver ou de ne pas approuver l’application.</li><br /></ul>Pour les applications non approuvées :<br /><br /><ul><li>Vous pouvez en bloquer l’utilisation dans votre pare-feu ou proxy.</li><li>Si vous avez une application non approuvée et une application approuvée dans la même catégorie, vous pouvez exporter une liste des utilisateurs de l’application non approuvée. Ensuite, contactez-les pour les inviter à migrer vers l’application approuvée.</li></ul></li>|  
|Activité suspecte|Cette alerte vous indique qu’une activité anormale qui n’est pas conforme aux activités ou utilisateurs attendus de votre organisation a été détectée.|Examinez le comportement et vérifiez-le auprès de l’utilisateur.<br /><br /> Ce type d’alerte est l’élément idéal pour en savoir plus sur votre environnement et créer des stratégies avec ces alertes. Par exemple, si un utilisateur charge soudainement une grande quantité de données dans l’une de vos applications connectées, vous pouvez définir une règle pour gérer ce type de comportement anormal.|  
|Utilisation suspecte du cloud|Cette alerte vous indique qu’une activité anormale qui n’est pas conforme aux activités ou utilisateurs attendus de votre organisation a été détectée.|Examinez le comportement et vérifiez-le auprès de l’utilisateur.<br /><br /> Ce type d’alerte est l’élément idéal pour en savoir plus sur votre environnement et créer des stratégies avec ces alertes. Par exemple, si un utilisateur charge soudainement une grande quantité de données dans l’une de vos applications connectées, vous pouvez définir une règle pour gérer ce type de comportement anormal.|  
|Utilisation d’un compte personnel|Cette alerte vous informe qu’un nouveau compte personnel a accès aux ressources de vos applications connectées.|Supprimez les collaborations de l’utilisateur dans le compte externe.|  


## <a name="next-steps"></a>Étapes suivantes  
Pour plus d’informations sur l’examen des alertes, consultez [Investiguer](investigate.md).  

Les clients Premier peuvent également choisir Cloud App Security directement depuis le [portail Premier](https://premier.microsoft.com/).  
