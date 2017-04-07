---
title: "Gérer les alertes déclenchées dans le portail Cloud App Security | Microsoft Docs"
description: "Cet article explique comment utiliser les alertes déclenchées dans le portail Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/26/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 1b1dbcc6-472f-43ea-af59-2aa926e3e5a9
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 33f549807b37414aad8ac1eb71b3bba354a19e9e
ms.sourcegitcommit: cda4a69f9ad9c6eb66fbdb98610f54d79585b84b
translationtype: HT
---
## <a name="manage-your-alerts"></a>Gérer vos alertes  
Les alertes constituent un bon point de départ pour comprendre votre environnement cloud de façon plus approfondie. Vous pouvez créer des stratégies selon ce que vous trouvez. Par exemple, vous pouvez voir un administrateur qui se connecte depuis le Groenland, alors que personne dans votre organisation ne s’est jamais connecté à partir de là auparavant. Vous pouvez créer une stratégie qui suspend automatiquement un compte d’administrateur quand celui-ci est utilisé pour se connecter depuis cet emplacement.  

Il est judicieux d’examiner toutes vos alertes et de vous en servir pour modifier vos stratégies. Si des événements sans incidence sont considérés comme des violations de stratégies existantes, affinez vos stratégies afin de recevoir moins d’alertes inutiles.  

1.   Sous **Alertes ouvertes**, cliquez sur **Afficher toutes les alertes**.  

     Cette section du tableau de bord fournit une visibilité totale de toute activité suspecte ou des violations de vos stratégies établies. Elle vous aide à préserver le plan de sécurité que vous avez défini pour votre environnement cloud.  

     ![Alertes](./media/alerts.png "alertes")  

2.   Pour chaque alerte, vous devez examiner et déterminer la nature de la violation et la réponse requise.  

     Vous pouvez filtrer les alertes par type d’alerte ou par gravité de façon à traiter d’abord les plus importantes.  

     Sélectionnez une alerte spécifique. Selon le type d’alerte dont il s’agit, vous voyez différentes actions que vous pouvez entreprendre avant de résoudre l’alerte.  

     Il existe trois types de violations que vous devez traiter quand vous examinez les alertes :  

    #### <a name="serious-violations"></a>Violations graves
     Les violations graves nécessitent une réponse immédiate.

         Examples:  

         For a suspicious activity alert, you might want to suspend the account until the user changes their password.  

         For a data leak you might want to restrict permissions or quarantine the file.  

         If a new app is discovered, you might want to block access to the service on your proxy or firewall.  

    #### <a name="questionable-violations"></a>Violations contestables
    Les violations contestables nécessitent un examen plus approfondi.  

         You can contact the  user or the user's manager about the nature of the activity.  

         Leave the activity open until you have more information.  

 #### <a name="authorized-violations-or-anomalous-behavior"></a>Violations autorisées ou comportements anormaux
 Les violations autorisées ou les comportements anormaux peuvent provenir d’une utilisation légitime.  

         Dismiss the alert.  

3.   Quand vous avez terminé ce processus, marquez l’alerte comme résolue.  

Le tableau suivant contient une liste des types d’alertes qui peuvent être déclenchées et les méthodes recommandées pour y remédier.  

|Type d’alerte|Description|Résolution recommandée|  
|----------------|-----------------|----------------------------|  
|Violation de stratégie d’activité|Ce type d’alerte est le résultat d’une stratégie que vous avez créée.|Pour utiliser en bloc ce type d’alerte, il est recommandé de travailler directement depuis le Centre de stratégie pour les limiter.<br /><br /> Ajustez la stratégie pour exclure les entités générant du bruit en ajoutant davantage de filtres et des contrôles plus granulaires.<br /><br /> Si la stratégie est précise, que l’alerte est justifiée et qu’il s’agit d’une violation que vous voulez arrêter immédiatement, ajoutez une correction automatique dans la stratégie.|  
|Violation de stratégie de fichier|Ce type d’alerte est le résultat d’une stratégie que vous avez créée.| Pour utiliser en bloc ce type d’alerte, il est recommandé de travailler directement depuis le Centre de stratégie pour les limiter.<br /><br /> Ajustez la stratégie pour exclure les entités générant du bruit en ajoutant davantage de filtres et des contrôles plus granulaires.<br /><br /> Si la stratégie est précise, que l’alerte est justifiée et qu’il s’agit d’une violation que vous voulez arrêter immédiatement, ajoutez une correction automatique dans la stratégie.|  
|Compte compromis|Ce type d’alerte se déclenche quand Cloud App Security identifie un compte qui a été compromis, ce qui signifie que la probabilité que le compte a été utilisé de façon non autorisée est très élevée.|Il est recommandé de suspendre le compte tant que vous n’avez pas contacté l’utilisateur et vérifié qu’il a changé son mot de passe.|  
|Compte inactif|Cette alerte se déclenche quand un compte n’est pas utilisé durant 60 jours dans l’une de vos applications cloud connectées.|Contactez l’utilisateur et le responsable de l’utilisateur pour déterminer si le compte est encore actif. Si ce n’est pas le cas, suspendez l’utilisateur et mettez un terme à sa licence pour l’application.|  
|Nouvel utilisateur administrateur|Cette alerte vous signale que des modifications ont été apportées dans vos comptes privilégiés pour des applications connectées.|Vérifiez que les nouvelles autorisations d’administration sont bien nécessaires pour l’utilisateur. Si ce n’est pas le cas, nous recommandons de révoquer les privilèges d’administrateur de façon à réduire l’exposition.|  
|Nouvel emplacement administrateur|Cette alerte vous signale que des modifications ont été apportées dans vos comptes privilégiés pour des applications connectées.|Vérifiez que la connexion depuis cet emplacement anormal était légitime. Si ce n’est pas le cas, nous recommandons de révoquer les autorisations d’administration ou de suspendre le compte de façon à réduire l’exposition.|  
|Nouvel emplacement|Il s’agit d’une alerte à titre d’information sur l’accès à une application connectée à partir d’un nouvel emplacement. Elle se déclenche une seule fois par pays.|Examinez les activités de l’utilisateur concerné.|  
|Nouveau service découvert|Il s’agit d’une alerte concernant l’informatique fantôme : une nouvelle application a été détectée par Cloud Discovery.|<ul><li>Évaluez le risque du service en fonction du catalogue d’applications.</li><li>Explorez l’activité au niveau du détail pour en comprendre les modèles d’utilisation et la fréquence.</li><li>Décidez d’approuver ou de ne pas approuver l’application.</li><br /></ul>Pour les applications non approuvées :<br /><br /><ul><li>Vous pouvez en bloquer l’utilisation dans votre pare-feu ou proxy.</li><li>Si vous avez une application non approuvée et une application approuvée dans la même catégorie, vous pouvez explorer une liste des utilisateurs de l’application non approuvée, puis les contacter pour les inviter à migrer vers l’application approuvée.</li></ul></li>|  
|Activité suspecte|Cette alerte vous indique qu’une activité anormale qui n’est pas conforme aux activités ou utilisateurs attendus de votre organisation a été détectée.|Examinez le comportement et vérifiez-le auprès de l’utilisateur.<br /><br /> Ce type d’alerte est l’élément idéal pour en savoir plus sur votre environnement et créer des stratégies avec ces alertes. Par exemple, si un utilisateur charge soudainement une grande quantité de données dans l’une de vos applications connectées, vous pouvez définir une règle pour gérer ce type de comportement anormal.|  
|Utilisation suspecte du cloud|Cette alerte vous indique qu’une activité anormale qui n’est pas conforme aux activités ou utilisateurs attendus de votre organisation a été détectée.|Examinez le comportement et vérifiez-le auprès de l’utilisateur.<br /><br /> Ce type d’alerte est l’élément idéal pour en savoir plus sur votre environnement et créer des stratégies avec ces alertes. Par exemple, si un utilisateur charge soudainement une grande quantité de données dans l’une de vos applications connectées, vous pouvez définir une règle pour gérer ce type de comportement anormal.|  
|Utilisation d’un compte personnel|Cette alerte vous informe qu’un nouveau compte personnel a accès aux ressources de vos applications connectées.|Supprimez les collaborations de l’utilisateur dans le compte externe.|  


## <a name="next-steps"></a>Étapes suivantes  
Pour plus d’informations sur l’examen des alertes, consultez [Investiguer](investigate.md).  
Pour obtenir du support technique, visitez la page du [support assisté de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
Les clients Premier peuvent également choisir Cloud App Security directement depuis le [portail Premier](https://premier.microsoft.com/).  
