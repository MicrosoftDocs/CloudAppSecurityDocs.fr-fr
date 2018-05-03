---
title: Examiner les risques et les activités suspectes des applications cloud avec Cloud App Security | Microsoft Docs
description: Cette rubrique présente le processus d’examen des alertes, des problèmes et des activités suspectes en utilisant Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: a9b00c2a-2f71-499e-8f57-67e560daedc1
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 0187adc2115e835c246b31c8412a359a4d3e2bc3
ms.sourcegitcommit: 45311f2cafef79483e40d971a4c61c7673834d96
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2018
---
*S’applique à : Microsoft Cloud App Security*


# <a name="investigate"></a>Investiguer
Une fois que Microsoft Cloud App Security s’exécute dans votre environnement cloud, vous avez besoin d’une phase de formation et d’étude sur la façon d’utiliser les outils de Microsoft Cloud App Security pour mieux comprendre ce qui se passe dans votre environnement cloud. Ensuite, selon votre environnement particulier et la façon dont il est utilisé, vous pouvez identifier ce qui est nécessaire pour protéger votre organisation contre les risques.

Cette rubrique décrit comment effectuer une investigation pour mieux comprendre votre environnement cloud.  

## <a name="dashboards"></a>Tableaux de bord  
Les tableaux de bord suivants sont disponibles pour vous aider à étudier les applications de votre environnement cloud :  

|Tableau de bord|Description|  
|---------------|-----------------|  
|Tableau de bord principal|Vue d’ensemble de l’état du cloud (utilisateurs, fichiers, activités) et des actions nécessaires (alertes, violations d’activité et violations de contenu)|  
|Tableau de bord Application : global|Vue d’ensemble de l’utilisation de l’application par emplacement, graphiques d’utilisation par nombre d’utilisateurs|  
|Tableau de bord Application : informations|Analyse des données stockées dans l’application, ventilées par type de fichier et par niveau de partage de fichiers|  
|Tableau de bord Application : fichiers|Exploration des fichiers au niveau du détail, possibilité de filtrer en fonction du propriétaire, du niveau de partage, etc., et d’effectuer des actions de gouvernance (comme la mise en quarantaine)|  
|Tableau de bord Application : applications tierces|Exploration au niveau du détail des applications tierces actuellement déployées, comme G Suite et définition de stratégies pour celles-ci|  
|Tableau de bord Utilisateur|Vue d’ensemble complète du profil utilisateur dans le cloud, notamment les groupes, les emplacements, les activités récentes, les alertes associées et les navigateurs utilisés|  

##  <a name="sanctionapp"></a> Marquer les applications comme approuvées ou non  
Le marquage des applications comme approuvées ou non est une étape importante pour comprendre votre cloud. Une fois que vous avez approuvé une application, vous pouvez filtrer les applications qui ne sont pas approuvées et lancer une migration vers des applications approuvées du même type.  

-   Dans la console Cloud App Security, accédez au catalogue d’applications ou aux applications découvertes.  

-   Dans la liste des applications, sur la ligne contenant l’application à marquer comme approuvée, cliquez sur les trois points à la fin de la ligne ![Points pour marquer comme approuvé](./media/sanction-three-dots.png "Points pour marquer comme approuvé") et choisissez **Marquer comme approuvé**.  

     ![Marquer comme approuvé](./media/mark-as-sanctioned.png "marquer comme approuvé")  


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

    -   Avec quels partenaires partagez-vous des fichiers (partage sortant) ?  

    -   Des fichiers ont-ils un nom sensible ?  

    -   Certains fichiers partagés le sont-ils avec le compte personnel de quelqu’un ?  

3.  Accédez à **Examiner**, puis **Comptes** et vérifiez les points suivants :  

    -   Des comptes ont-ils été inactifs dans un service particulier pendant une longue période de temps ? (Vous pouvez peut-être révoquer la licence de cet utilisateur pour ce service ?)  

    -   Voulez-vous connaître les utilisateurs qui remplissent un rôle spécifique ?  

    -   Certaines personnes qui ont été licenciées ont-elles toujours accès à une application, lequel accès pourrait leur permettre de dérober des informations ?  

    -   Voulez-vous révoquer l’autorisation d’un utilisateur sur une application spécifique ou exiger d’un utilisateur spécifique qu’il effectue une authentification multifacteur ?  
    
    -   Vous pouvez également explorer le compte de l’utilisateur en cliquant sur la roue dentée à la fin de la ligne du compte de l’utilisateur et en sélectionnant une action à effectuer, comme **Suspendre l’utilisateur** ou **Supprimer les collaborations d’utilisateur**. Si l’utilisateur a été importé depuis Azure Active Directory, vous pouvez également cliquer sur **Paramètres du compte Azure AD** pour accéder facilement aux fonctionnalités d’administration avancée de l’utilisateur, comme l’administration du groupe, l’authentification multifacteur, l’obtention d’informations sur les connexions de l’utilisateur et la possibilité de bloquer la connexion.

4.  Accédez à **Examiner**, puis sélectionnez une application. Le tableau de bord Application s’ouvre et vous donne des informations. Vous pouvez utiliser les onglets en haut pour vérifier les éléments suivants :  

     ![Tableau de bord des applications](./media/investigate-app.png "examiner l’application")  

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

    -   Pour les solutions alternatives, voulez-vous rendre non approuvées des applications cloud dans votre organisation ?  

    -   Certaines applications cloud sont-elles utilisées, alors qu’elles ne sont pas conformes à la stratégie de votre organisation ?  

## <a name="sample-investigation"></a>Exemple d’examen  
Partons du principe que vous pensez ne pas avoir d’accès à votre environnement cloud via des adresses IP risquées (par exemple des proxys anonymes et Tor). Vous créez cependant une stratégie pour les adresses IP à risques simplement pour vous en assurer :  

1.  Dans le portail, accédez à **Contrôle** et choisissez **Stratégies**.  

2.  Dans le **Centre de stratégie**, choisissez l’onglet **Modèles**.  

3.  À la fin de la ligne **Connexion utilisateur depuis une adresse IP non catégorisée**, choisissez le signe **+** pour créer une stratégie.  

4.  Modifiez le nom de la stratégie pour pouvoir l’identifier facilement.  

5.  Sous **Filtres d’activité**, cliquez sur le signe **+** pour ajouter un filtre. Faites défiler jusqu’à **Étiquette IP**, puis choisissez **Anonyme** et **Tor**.  

     ![Exemple de stratégie pour les adresses IP avec risques](./media/example-policy-risky-ips.png "exemple de stratégie pour les adresses IP avec risques")  

Maintenant que la stratégie est en place, vous vous étonnez de voir que vous recevez une alerte indiquant que la stratégie a été violée.  

1.  Accédez à la page **Alertes** et affichez l’alerte relative à la violation de la stratégie.  

2.  Si vous constatez qu’il semble s’agir d’une réelle violation, vous voudrez contenir le risque ou y remédier.  

     Pour contenir le risque, vous pouvez envoyer à l’utilisateur une notification l’invitant à préciser si la violation était délibérée et s’il en avait conscience.  

     Vous pouvez également explorer l’alerte au niveau du détail et suspendre l’utilisateur jusqu’à ce que vous décidiez des mesures à prendre.  

3.  S’il s’agit d’un événement autorisé qui a peu de chances de se reproduire, vous pouvez rejeter l’alerte.  

     S’il est autorisé et que vous pensez qu’il va se reproduire, vous pouvez modifier la stratégie pour éviter que ce type d’événement soit considéré comme une violation à l’avenir.  

## <a name="see-also"></a>Voir aussi  
Pour découvrir comment contrôler l’application cloud de votre organisation, consultez [Contrôle](control.md).   

Les clients Premier peuvent également choisir Cloud App Security directement depuis le [portail Premier](https://premier.microsoft.com/).  
