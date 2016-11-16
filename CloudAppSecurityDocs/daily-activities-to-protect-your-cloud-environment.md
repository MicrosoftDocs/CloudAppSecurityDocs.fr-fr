---
title: "Activités quotidiennes pour protéger votre environnement cloud | Documentation Microsoft"
description: "Cet article fournit une base pour la procédure à suivre régulièrement dans Cloud App Security pour utiliser Cloud App Security afin de surveiller l’usage des applications cloud dans votre organisation."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: a835fa24-15c5-4bbb-a25a-688444040f1f
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: cc6a6e4b41b6660462c9c873469a1e8c9af97c4e


---

# <a name="daily-activities-to-protect-your-cloud-environment"></a>Activités quotidiennes pour protéger votre environnement cloud
Une fois que vous avez rendu Cloud App Security opérationnel et configuré des flux de données, approuvé toutes les applications que vos utilisateurs doivent pouvoir utiliser et défini des stratégies pour surveiller votre environnement cloud, le moment est venu d’utiliser Cloud App Security pour contrôler et protéger votre cloud, et gérer les risques.  
  
Cette rubrique décrit la procédure à suivre au quotidien.  
  
## <a name="check-the-dashboard"></a>Consulter le tableau de bord  
Quand vous ouvrez le portail Cloud App Security, vous voyez une vue d’ensemble des alertes ouvertes, des violations d’activité, des violations de contenu, une carte d’activités qui indique les emplacements géographiques desquels provient l’activité utilisateur, ainsi que des tendances d’utilisation des applications connectées dans votre environnement cloud.  
  
Il est recommandé de consulter le tableau de bord tous les jours pour voir quelles nouvelles alertes ont été déclenchées afin de les gérer. Le tableau de bord est aussi l’endroit idéal pour garder un œil sur l’intégrité de votre environnement cloud car il vous donne un aperçu de ce qui se passe, de façon précise, au sein de tout votre environnement cloud.  
  
![tableau de bord](./media/dashboard.png "dashboard")  
  
## <a name="handle-your-alerts"></a>Gérer vos alertes  
Les alertes constituent un bon point de départ pour comprendre votre environnement cloud de façon plus approfondie. Vous pouvez créer des stratégies selon ce que vous trouvez. Par exemple, vous pouvez observer qu’un administrateur se connecte depuis le Groenland et décider qu’à l’avenir vous allez créer une stratégie qui suspend automatiquement un compte d’administrateur quand il est utilisé pour se connecter depuis le Groenland.  
  
Il est judicieux de consulter toutes vos alertes et de les utiliser comme un outil pour modifier vos stratégies. Si des événements sans incidence sont considérés comme des violations par des stratégies existantes, vous devez affiner vos stratégies afin de recevoir moins d’alertes inutiles.  
  
-   Sous **Alertes ouvertes**, cliquez sur **Afficher toutes les alertes**.  
  
     Cette opération donne une visibilité complète à toute activité ou violation suspecte de vos stratégies établies, ce qui vous permet de protéger le cadre de sécurité que vous avez défini pour votre environnement cloud.  
  
     ![alertes](./media/alerts.png "alerts")  
  
-   Pour chaque alerte, vous devez examiner et déterminer la nature de la violation et la réponse requise.  
  
     Vous pouvez filtrer les alertes par **type d’alerte** ou par **gravité** afin de traiter d’abord les plus importantes.  
  
     Cliquez sur une alerte spécifique. Selon le type d’alerte dont il s’agit, vous recevez diverses actions pouvant être effectuées avant de résoudre l’alerte.  
  
     Il existe trois types de violations que vous devez traiter quand vous examinez les alertes :  
  
    -   Les **violations graves** qui nécessitent une réponse immédiate  
  
         Exemples :  
  
         Pour une alerte d’activité suspecte, vous pouvez suspendre le compte jusqu’à ce que l’utilisateur modifie son mot de passe.  
  
         Pour une fuite de données, vous pouvez restreindre les autorisations ou mettre le fichier en quarantaine.  
  
         Si un nouveau service non approuvé est découvert, vous pouvez bloquer l’accès au service sur votre proxy ou pare-feu.  
  
    -   Les **violations discutables** qui requièrent un examen plus approfondi  
  
         Vous pouvez contacter l’utilisateur ou le responsable de l’utilisateur pour lui demander la nature de l’activité.  
  
         Laissez l’activité ouverte jusqu’à ce que vous ayez plus d’informations.  
  
    -   Les **violations autorisées ou un comportement anormal** résultant d’une utilisation légitime  
  
         Supprimez l’alerte.  
  
-   Quand vous avez terminé ce processus, marquez l’alerte comme résolue.  
  
Le tableau suivant fournit la liste des types d’alertes qui peuvent être déclenchés et les méthodes recommandées pour y remédier.  
  
|Type d’alerte|Description|Résolution recommandée|  
|----------------|-----------------|----------------------------|  
|Violation de stratégie d’activité|Ce type d’alerte est le résultat d’une stratégie que vous avez créée.|- Pour utiliser ce type d’alerte en bloc, il est recommandé de travailler directement depuis le Centre de stratégie pour les atténuer.<br />- Ajustez la stratégie pour exclure les entités bruyantes en ajoutant davantage de filtres et de contrôles plus granulaires.<br />- Si la stratégie est très précise, que l’alerte était justifiée et qu’il s’agit d’une violation que vous voulez arrêter immédiatement, envisagez de passer à une réponse automatisée, en ajoutant la correction automatique à la stratégie.|  
|Violation de stratégie de fichier|Ce type d’alerte est le résultat d’une stratégie que vous avez créée.|- Pour utiliser ce type d’alerte en bloc, il est recommandé de travailler directement depuis le Centre de stratégie pour les atténuer.<br />- Ajustez la stratégie pour exclure les entités bruyantes en ajoutant davantage de filtres et de contrôles plus granulaires.<br />- Si la stratégie est très précise, que l’alerte était justifiée et qu’il s’agit d’une violation que vous voulez arrêter immédiatement, envisagez de passer à une réponse automatisée, en ajoutant la correction automatique à la stratégie.|  
|Compte compromis|Ce type d’alerte se déclenche quand Cloud App Security identifie un compte qui a été compromis (la probabilité que le compte ait été utilisé de façon non autorisée est très élevée).|Il est recommandé de suspendre le compte jusqu’à ce que vous puissiez contacter l’utilisateur et vous assurer qu’il a modifié son mot de passe.|  
|Compte inactif|Cette alerte se déclenche quand un compte n’est plus utilisé dans l’une de vos applications cloud connectées.|Contactez l’utilisateur et le responsable de l’utilisateur pour déterminer si le compte est encore actif. Si ce n’est pas le cas, suspendez l’utilisateur et mettez un terme à sa licence pour l’application.|  
|Nouvel utilisateur administrateur|Cette alerte vous signale que des modifications ont été apportées dans vos comptes privilégiés pour des applications connectées.|Vérifiez que les nouvelles autorisations administratives sont effectivement nécessaires à l’utilisateur, et dans le cas contraire, n’hésitez pas à révoquer les privilèges d’administrateur pour réduire l’exposition à des risques.|  
|Nouvel emplacement administrateur|Cette alerte vous signale que des modifications ont été apportées dans vos comptes privilégiés pour des applications connectées.|Vérifiez que la connexion depuis cet emplacement anormal était légitime, et dans le cas contraire, n’hésitez pas à révoquer les autorisations administratives ou à suspendre le compte pour réduire l’exposition à des risques.|  
|Nouvel emplacement|Il s’agit d’une alerte à titre d’information sur l’accès à une application connectée à partir d’un nouvel emplacement. Elle se déclenche une seule fois par pays.|Examinez les activités de l’utilisateur concerné.|  
|Nouveau service découvert|Il s’agit d’une alerte concernant l’informatique fantôme : une nouvelle application a été détectée par Cloud Discovery.|<ul><li>Évaluez le risque du service en fonction du catalogue d’applications.</li><li>Explorez l’activité au niveau du détail pour en comprendre les modèles d’utilisation et la fréquence.</li><li>Décidez d’approuver ou de ne pas approuver l’application.<br /><br />     Pour les applications non approuvées :<br /><br /> <ul><li>Vous pouvez en bloquer l’utilisation dans votre pare-feu ou proxy.</li><li>Si l’application est non approuvée et que vous avez une application approuvée de la même catégorie, vous pouvez explorer l’alerte au niveau du détail et exporter la liste des utilisateurs de l’application non approuvée, pour ensuite les contacter afin de les inviter à migrer vers l’application approuvée.</li></ul></li></ul>|  
|Activité suspecte|Cette alerte vous indique qu’une activité anormale qui n’est pas conforme aux activités ou utilisateurs attendus de votre organisation a été détectée.|Examinez le comportement et vérifiez-le auprès de l’utilisateur.<br /><br /> Ce type d’alerte est l’élément idéal pour en savoir plus sur votre environnement et créer des stratégies. Par exemple, si un utilisateur charge soudainement une grande quantité de données dans l’une de vos applications connectées, vous pouvez définir une règle pour gérer ce type de comportement anormal.|  
|Utilisation suspecte du cloud|Cette alerte vous indique qu’une activité anormale qui n’est pas conforme aux activités ou utilisateurs attendus de votre organisation a été détectée.|Examinez le comportement et vérifiez-le auprès de l’utilisateur.<br /><br /> Ce type d’alerte est l’élément idéal pour en savoir plus sur votre environnement et créer des stratégies. Par exemple, si un utilisateur charge soudainement une grande quantité de données dans l’une de vos applications connectées, vous pouvez définir une règle pour gérer ce type de comportement anormal.|  
|Utilisation d’un compte personnel|Cette alerte vous informe qu’un nouveau compte personnel a accès aux ressources de vos applications connectées.|Dans le compte externe, supprimez les collaborations de l’utilisateur.|  
  
## <a name="use-policies-to-assess-risk"></a>Utiliser des stratégies pour évaluer les risques  
Quand vous examinez vos alertes ouvertes, accédez au **Centre de stratégie** pour passer en revue les violations de stratégie qui n’ont pas déclenché d’alertes.  
  
-   Dans le portail Cloud App Security, cliquez sur **Contrôle**, puis sur **Stratégies**.  
  
-   Cliquez sur une stratégie spécifique pour afficher la liste **Violation maintenant** des correspondances de stratégie qui n’ont pas déclenché d’alertes.  
  
-   Cliquez sur les violations, une par une, puis déterminez ce que vous devez faire pour chacune. Pour plus d’informations sur les actions de gouvernance, voir ci-dessous.  
  
     Par exemple, si votre stratégie est définie pour rechercher des violations de conformité et que quelqu’un enregistre des numéros de carte de crédit dans des fichiers sur OneDrive, vous obtenez une correspondance dans la stratégie.  
  
     ![correspondances pci](./media/pci-matches.png "pci matches")  
  
-   Cliquez sur la correspondance pour afficher les fichiers réels qui ont enfreint la stratégie.  
  
     ![pci, correspondances de contenu](./media/pci-content-matches.png "pci content matches")  
  
     Vous pouvez cliquer sur le fichier lui-même pour obtenir des informations sur les fichiers.  
  
     Vous pouvez cliquer sur **Collaborateurs** pour voir qui a accès à ce fichier.  
  
     Vous pouvez cliquer sur les **Correspondances** pour voir les numéros de carte de crédit réels.  
  
     ![correspondances de contenu ccn](./media/content-matches-ccn.png "content matches ccn")  
  
## <a name="see-also"></a>Voir aussi  
[Examiner](investigate.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO4-->


