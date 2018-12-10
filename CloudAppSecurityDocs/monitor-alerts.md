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
ms.openlocfilehash: 0385cef903263b680f4fdd5915bd150a3cca17dc
ms.sourcegitcommit: cae782d508db9d1a7c0c362e9a23e83f74d48b21
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2018
ms.locfileid: "52743401"
---
*S’applique à : Microsoft Cloud App Security*


## <a name="manage-your-alerts"></a>Gérer vos alertes  
Les alertes constituent un bon point de départ pour comprendre votre environnement cloud de façon plus approfondie. Vous pouvez créer des stratégies selon ce que vous trouvez. Par exemple, vous pouvez voir un administrateur qui se connecte depuis le Groenland, alors que personne dans votre organisation ne s’est jamais connecté à partir de là auparavant. Vous pouvez créer une stratégie qui suspend automatiquement un compte d’administrateur quand celui-ci est utilisé pour se connecter depuis cet emplacement.  

Il est judicieux d’examiner toutes vos alertes et de vous en servir pour modifier vos stratégies. Si des événements sans incidence sont considérés comme des violations de stratégies existantes, affinez vos stratégies afin de recevoir moins d’alertes inutiles.  

1. Sous **Alertes ouvertes**, cliquez sur **Afficher toutes les alertes**.  

   Cette section du tableau de bord fournit une visibilité totale de toute activité suspecte ou des violations de vos stratégies établies. Elle vous aide à préserver le plan de sécurité que vous avez défini pour votre environnement cloud.  

   ![Alertes](./media/alerts.png "alertes")  

2. Pour chaque alerte, vous devez examiner et déterminer la nature de la violation et la réponse requise.  

   Vous pouvez filtrer les alertes par type d’alerte ou par gravité de façon à traiter d’abord les plus importantes.  

   Sélectionnez une alerte spécifique. Selon le type d’alerte dont il s’agit, vous voyez différentes actions que vous pouvez entreprendre avant de résoudre l’alerte.  
   
   Vous pouvez filtrer en fonction de l’application : les applications répertoriées sont celles pour lesquelles des activités ont été détectées par Cloud App Security.

   Il existe trois types de violations que vous devez traiter quand vous examinez les alertes :  

   - **Violations graves**<br>
     Les violations graves nécessitent une réponse immédiate. <br>
     Exemples :<br>
     Pour une alerte d’activité suspecte, vous pouvez suspendre le compte jusqu’à ce que l’utilisateur change son mot de passe.  

     Pour une fuite de données, vous voudrez probablement restreindre les autorisations ou mettre le fichier en quarantaine.  

     Si une nouvelle application est découverte, vous voudrez probablement bloquer l’accès au service sur votre proxy ou pare-feu.  

   - **Violations contestables**<br>
     Les violations contestables nécessitent un examen plus approfondi.  <br>
     Vous pouvez contacter l’utilisateur ou le responsable de l’utilisateur pour lui demander la nature de l’activité. <br>  
     Laissez l’activité ouverte jusqu’à ce que vous ayez plus d’informations.  

   - **Violations autorisées ou comportements anormaux**<br>
     Les violations autorisées ou les comportements anormaux peuvent provenir d’une utilisation légitime.  

     Vous pouvez ignorer l’alerte.  

3. Chaque fois que vous ignorez une alerte, il est important d’envoyer un feedback sur la raison pour laquelle vous l’ignorez. L’équipe Cloud App Security utilise ce feedback comme indication de l’exactitude de l’alerte : il est ensuite utilisé pour affiner nos modèles Machine Learning pour les alertes futures. Vous pouvez suivre ces instructions pour décider comment catégoriser l’alerte :
 - Si une utilisation légitime a déclenché l’alerte et que ce n’est pas un problème de sécurité, il peut s’agir de : 
    - Un positif sans gravité : l’alerte est exacte, mais l’activité est légitime. Il est recommandé d’ignorer l’alerte, et de définir la raison sur **La gravité réelle est inférieure** ou sur **Sans intérêt**.
    -   Faux positif : l’alerte est inexacte. Ignorez l’alerte et définissez la raison sur **L’alerte n’est pas exacte**.
 - S’il y a trop de bruit pour déterminer la légitimité et l’exactitude d’une alerte, ignorez-la et définissez la raison sur **Trop d’alertes similaires**.
 - Vrai positif : si l’alerte concerne un événement à risques réel qui a été commis à des fins malveillantes ou involontairement par un utilisateur interne ou externe, il est recommandé de définir l’événement sur **Résolution** après que toutes les actions appropriées ont été effectuées pour remédier à l’événement.
 

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
|Nouveau service découvert|Il s’agit d’une alerte concernant le Shadow IT. Une nouvelle application a été détectée par Cloud Discovery.|<ul><li>Évaluez le risque du service en fonction du catalogue d’applications.</li><li>Explorez l’activité au niveau du détail pour en comprendre les modèles d’utilisation et la fréquence.</li><li>Décidez d’approuver ou de ne pas approuver l’application.</li><br /></ul>Pour les applications non approuvées :<br /><br /><ul><li>Vous pouvez en bloquer l’utilisation dans votre pare-feu ou proxy.</li><li>Si vous avez une application non approuvée et une application approuvée dans la même catégorie, vous pouvez explorer une liste des utilisateurs de l’application non approuvée, puis les contacter pour les inviter à migrer vers l’application approuvée.</li></ul></li>|  
|Activité suspecte|Cette alerte vous indique qu’une activité anormale qui n’est pas conforme aux activités ou utilisateurs attendus de votre organisation a été détectée.|Examinez le comportement et vérifiez-le auprès de l’utilisateur.<br /><br /> Ce type d’alerte est l’élément idéal pour en savoir plus sur votre environnement et créer des stratégies avec ces alertes. Par exemple, si un utilisateur charge soudainement une grande quantité de données dans l’une de vos applications connectées, vous pouvez définir une règle pour gérer ce type de comportement anormal.|  
|Utilisation suspecte du cloud|Cette alerte vous indique qu’une activité anormale qui n’est pas conforme aux activités ou utilisateurs attendus de votre organisation a été détectée.|Examinez le comportement et vérifiez-le auprès de l’utilisateur.<br /><br /> Ce type d’alerte est l’élément idéal pour en savoir plus sur votre environnement et créer des stratégies avec ces alertes. Par exemple, si un utilisateur charge soudainement une grande quantité de données dans l’une de vos applications connectées, vous pouvez définir une règle pour gérer ce type de comportement anormal.|  
|Utilisation d’un compte personnel|Cette alerte vous informe qu’un nouveau compte personnel a accès aux ressources de vos applications connectées.|Supprimez les collaborations de l’utilisateur dans le compte externe.|  


## <a name="next-steps"></a>Étapes suivantes  
Pour plus d’informations sur l’examen des alertes, consultez [Investiguer](investigate.md).  

Les clients Premier peuvent également choisir Cloud App Security directement depuis le [portail Premier](https://premier.microsoft.com/).  