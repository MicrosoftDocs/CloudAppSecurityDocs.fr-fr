---
title: Examiner | Documentation Microsoft
description: "Cette rubrique présente le processus d’examen des alertes, des problèmes et des activités suspectes à l’aide de Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: a9b00c2a-2f71-499e-8f57-67e560daedc1
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: 186643ab8efa7391b06a09dd2cddbb22ba583e71


---

# <a name="investigate"></a>Étudier
Une fois que Cloud App Security s’exécute dans votre environnement cloud, vous avez besoin d’une phase de formation et d’étude avec des outils de Cloud App Security pour mieux comprendre ce qui se passe dans votre environnement cloud. Ensuite, selon votre environnement particulier et la façon dont vous l’utilisez, vous pouvez identifier les conditions requises pour protéger votre organisation contre les risques.  
  
Cette section décrit comment effectuer cette étude approfondie pour mieux comprendre ce qui se passe dans votre environnement cloud.  
  
## <a name="dashboards"></a>Tableaux de bord  
Les tableaux de bord suivants sont disponibles pour vous aider à étudier ce qui se passe avec les applications de votre environnement cloud :  
  
|Tableau de bord|Description|  
|---------------|-----------------|  
|Tableau de bord principal|Vue d’ensemble de l’état du cloud (utilisateurs, fichiers, activités) ainsi que des actions obligatoires (alertes, violations d’activité et violations de contenu)|  
|Tableau de bord Application - global|Vue d’ensemble de l’utilisation de l’application par emplacement, graphiques d’utilisation par nombre d’utilisateurs|  
|Tableau de bord Application – informations|Analyse des données stockées dans l’application, ventilées par type de fichier et niveau de partage de fichiers|  
|Tableau de bord Application – fichiers|Exploration des fichiers au niveau du détail, possibilité de filtrer en fonction du propriétaire, niveau de partage, etc. et d’effectuer des actions de gouvernance (telles que la mise en quarantaine)|  
|Tableau de bord Application – applications tierces|Exploration au niveau du détail des applications tierces actuellement déployées, comme Google Apps et définition de leurs stratégies|  
|Tableau de bord Utilisateur|Vue d’ensemble complète du profil utilisateur dans le cloud, notamment des groupes, emplacements, activités récentes, alertes associées et navigateurs utilisés|  
  
##  <a name="a-namesanctionappa-sanction-or-unsanction-apps"></a> Approuver ou ne pas approuver des applications  
La première étape pour comprendre votre cloud consiste à approuver des applications. Une fois que vous avez approuvé une application, vous pouvez filtrer les applications qui ne sont pas approuvées et lancer une migration vers des applications approuvées du même type.  
  
-   Dans la console Cloud App Security, cliquez sur **Découvrir**, puis sur **Tableau de bord de découverte**.  
  
-   Dans la liste des applications découvertes, sur la ligne dans laquelle l’application que vous souhaitez approuver apparaît, cliquez sur les trois points à la fin de la ligne ![Sanction three dots](./media/sanction-three-dots.png "Sanction three dots") (Approuver trois points) et sélectionnez **Marqué comme approuvé**.  
  
     ![marqué comme approuvé](./media/mark-as-sanctioned.png "mark as sanctioned")  
  
> [!NOTE]  
>  Pour chaque application à surveiller avec l’intégration de l’API Cloud App Security, nous vous recommandons de créer un compte de service d’administration dédié à Cloud App Security.  
  
## <a name="use-the-investigation-tools"></a>Utiliser les outils d’examen  
  
1.  Dans le portail Cloud App Security, accédez à **Examiner**, puis consultez le **journal d’activité** et filtrez sur une application spécifique. Vérifiez les points suivants :  
  
    -   Qui accède à votre environnement cloud ?  
  
    -   À partir de quelles plages d’adresses IP ?  
  
    -   Quelle est l’activité administrative ?  
  
    -   À partir de quels emplacements les administrateurs se connectent-ils ?  
  
    -   Des appareils obsolètes se connectent-ils à votre environnement cloud ?  
  
    -   Les échecs de connexion proviennent-ils d’adresses IP attendues ?  
  
2.  Accédez à **Examiner**, puis **Fichiers** et vérifiez les points suivants :  
  
    -   Combien de fichiers sont partagés publiquement pour permettre à toute personne d’y accéder sans aucun lien ?  
  
    -   Avec quels partenaires partagez-vous des fichiers ? (partage sortant)  
  
    -   Certains fichiers contiennent-ils un nom sensible ?  
  
    -   Certains fichiers partagés le sont-ils avec le compte personnel de quelqu’un ?  
  
3.  Accédez à **Examiner**, puis **Comptes** et vérifiez les points suivants :  
  
    -   Certains comptes n’ont-ils pas été actifs dans un service particulier pendant une longue période ? Peut-être pouvez-vous révoquer la licence de cet utilisateur pour ce service ?  
  
    -   Voulez-vous connaître les utilisateurs qui remplissent un rôle spécifique ?  
  
    -   Certaines personnes qui ont été licenciées ont-elles toujours accès à une application, lequel accès pourrait leur permettre de dérober des informations ?  
  
    -   Voulez-vous révoquer l’autorisation d’un utilisateur sur une application spécifique ou exiger d’un utilisateur spécifique qu’il effectue une authentification multifacteur ?  
  
4.  Accédez à **Examiner**, puis sélectionnez une application. Vous accédez au tableau de bord Application qui vous fournit des informations. Vous pouvez alors utiliser les onglets situés en haut pour vérifier les points suivants :  
  
     ![examiner l’application](./media/investigate-app.png "investigate app")  
  
    -   Quels types d’appareils vos utilisateurs utilisent-ils pour se connecter à l’application ?  
  
    -   Quels types de fichiers enregistrent-ils dans le cloud ?  
  
    -   Quelle activité se produit dans l’application en ce moment même ?  
  
    -   Des applications tierces sont-elles connectées à votre environnement ?  
  
    -   Connaissez-vous ces applications ?  
  
    -   Sont-elles autorisées pour le niveau d’accès auquel elles correspondent ?  
  
    -   Combien d’utilisateurs les ont déployées ? Quelle est la fréquence de ces applications en général ?  
  
5.  Accédez au **tableau de bord Cloud Discovery** et vérifiez les points suivants :  
  
    -   Quelles sont les applications cloud utilisées, dans quelle mesure et par qui ?  
  
    -   À quelles fins sont-elles utilisées ?  
  
    -   Quelle quantité de données est chargée vers ces applications cloud ?  
  
    -   Dans quelles catégories avez-vous des applications cloud approuvées, alors que les utilisateurs utilisent plutôt des solutions alternatives ?  
  
    -   Pour les solutions alternatives, existe-t-il des applications cloud que vous ne voulez pas approuver dans votre organisation ?  
  
    -   Certaines applications cloud sont-elles utilisées, alors qu’elles ne sont pas conformes à la stratégie de votre organisation ?  
  
## <a name="how-to-use-reports-to-investigate-risk"></a>Comment utiliser des rapports pour examiner les risques  
Quand vous vous attelez à mieux contrôler votre environnement cloud, vous avancez certaines hypothèses selon ce que vous vous attendez à trouver : vous ne connaissez pas encore vraiment votre cloud. Selon ces hypothèses, vous créez des stratégies. Ensuite, une fois que Cloud App Security s’exécute dans votre environnement cloud, vous pouvez utiliser les rapports intégrés (ainsi que des rapports personnalisés) pour voir ce qui se passe vraiment dans votre cloud et, en fonction de cela, vous ajustez vos stratégies pour inclure des exceptions, afin que votre stratégie intercepte finalement très peu de faux positifs.  
  
Les rapports intégrés vous offrent des vues agrégées à examiner.  
  
Pour utiliser les rapports intégrés, accédez à **Examiner**, puis **Rapports intégrés**. Pour plus d’informations sur les différents rapports intégrés, voir les [informations de référence sur les rapports intégrés](built-in-report-reference.md).  
  
## <a name="sample-investigation"></a>Exemple d’examen  
Partons du principe que vous pensez ne pas avoir d’accès à votre environnement cloud par des adresses IP risquées (par exemple, des proxys anonymes et Tor). Mais vous créez une stratégie Adresse IP risquée simplement pour vous en assurer :  
  
1.  Dans le portail, accédez à **Contrôle** et sélectionnez **Stratégies**.  
  
2.  Dans le **Centre de stratégie**, cliquez sur l’onglet **Modèles**.  
  
3.  À la fin de la ligne **Connexion utilisateur depuis une adresse IP non catégorisée**, cliquez sur le signe **+** pour créer une stratégie.  
  
4.  Modifiez le nom de la stratégie pour pouvoir l’identifier facilement.  
  
5.  Sous **Filtres d’activité**, cliquez sur le signe **+** pour ajouter un filtre. Faites défiler jusqu’à **Étiquette IP**, puis sélectionnez **Anonyme** et **Tor**.  
  
     ![exemple de stratégie, adresses IP risquées](./media/example-policy-risky-ips.png "example policy risky ips")  
  
Maintenant que la stratégie est en place, vous vous étonnez de voir que vous recevez une alerte indiquant que la stratégie a été violée.  
  
1.  Accédez à la page **Alertes** et affichez l’alerte relative à la violation de la stratégie.  
  
2.  Si vous constatez qu’il semble s’agir d’une réelle violation, vous voudrez contenir le risque ou y remédier.  
  
     Pour contenir le risque, vous pouvez envoyer à l’utilisateur une notification l’invitant à préciser si la violation était délibérée et s’il en avait conscience.  
  
     Vous pouvez également explorer l’alerte au niveau du détail et suspendre l’utilisateur jusqu’à ce que vous décidiez des mesures à prendre.  
  
3.  S’il s’agit d’un événement autorisé qui a peu de chances de se reproduire, vous pouvez rejeter l’alerte.  
  
     S’il est autorisé et que vous pensez qu’il va se reproduire, vous pouvez modifier la stratégie pour éviter que ce type d’événement soit considéré comme une violation à l’avenir.  
  
## <a name="see-also"></a>Voir aussi  
[Contrôler](control.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO4-->


