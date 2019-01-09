---
title: Examiner les risques et les activités suspectes des applications cloud – Cloud App Security | Microsoft Docs
description: Cet article décrit le processus d’investigation des alertes, des problèmes et des activités suspectes à l’aide de Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: a9b00c2a-2f71-499e-8f57-67e560daedc1
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 12bb0604e776f9ff8df61c784d3d8597dc05ed32
ms.sourcegitcommit: b86c3afd1093fbc825fec5ba4103e3a95f65758e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53176635"
---
# <a name="investigate"></a>Investiguer

*S’applique à : Microsoft Cloud App Security*

Une fois que Microsoft Cloud App Security est exécuté dans votre environnement cloud, vous avez besoin d’une phase d’apprentissage et d’investigation. Apprenez à utiliser les outils Microsoft Cloud App Security pour mieux comprendre ce qui se passe dans votre environnement cloud. Selon les spécificités de votre environnement et la façon dont il est utilisé, vous pouvez identifier les exigences relatives à la protection de votre organisation. Cet article décrit comment effectuer une investigation pour mieux comprendre l’environnement cloud.  

## <a name="dashboards"></a>Tableaux de bord  
Les tableaux de bord suivants sont disponibles pour vous aider à étudier les applications de votre environnement cloud :  

|Tableau de bord|Description|  
|---------------|-----------------|  
|Tableau de bord principal|Vue d’ensemble de l’état du cloud (utilisateurs, fichiers, activités) et des actions nécessaires (alertes, violations d’activité et violations de contenu)|  
|Tableau de bord Application : global|Vue d’ensemble de l’utilisation de l’application par emplacement, graphiques d’utilisation par nombre d’utilisateurs|  
|Tableau de bord Application : informations|Analyse des données stockées dans l’application, ventilées par type de fichier et par niveau de partage de fichiers|  
|Tableau de bord Application : fichiers|Exploration des fichiers au niveau du détail, filtrage en fonction du propriétaire, du niveau de partage, etc., et exécution d’actions de gouvernance comme la mise en quarantaine.|  
|Tableau de bord Application : applications tierces|Exploration au niveau du détail des applications tierces déployées, par exemple G Suite, et définition de stratégies pour celles-ci|  
|Tableau de bord Utilisateur|Vue d’ensemble complète du profil utilisateur dans le cloud, notamment les groupes, les emplacements, les activités récentes, les alertes associées et les navigateurs utilisés|  

##  <a name="sanctionapp"></a> Marquer les applications comme approuvées ou non  
Le marquage des applications comme approuvées ou non est une étape importante pour comprendre votre cloud. Une fois que vous avez approuvé une application, vous pouvez filtrer les applications qui ne sont pas approuvées et lancer une migration vers des applications approuvées du même type.  

- Dans la console Cloud App Security, accédez au catalogue d’applications ou aux applications découvertes.  

- Dans la liste des applications, sur la ligne contenant l’application à marquer comme approuvée, cliquez sur les trois points à la fin de la ligne ![Points pour marquer comme approuvé](./media/sanction-three-dots.png "Points pour marquer comme approuvé") et choisissez **Marquer comme approuvé**.  

     ![Marquer comme approuvé](./media/mark-as-sanctioned.png "marquer comme approuvé")  


## <a name="use-the-investigation-tools"></a>Utiliser les outils d’examen  

1. Dans le portail Cloud App Security, accédez à **Examiner**, puis consultez le **journal d’activité** et filtrez sur une application spécifique. Vérifiez les points suivants :  

    - Qui accède à votre environnement cloud ?  

    - À partir de quelles plages d’adresses IP ?  

    - Quelle est l’activité administrative ?  

    - À partir de quels emplacements les administrateurs se connectent-ils ?  

    - Des appareils obsolètes se connectent-ils à votre environnement cloud ?  

    - Les échecs de connexion proviennent-ils d’adresses IP attendues ?  

2. Accédez à **Examiner**, **Fichiers**, puis vérifiez les points suivants :  

    - Combien de fichiers sont partagés publiquement pour permettre à toute personne d’y accéder sans aucun lien ?  

    - Avec quels partenaires partagez-vous des fichiers (partage sortant) ?  

    - Des fichiers ont-ils un nom sensible ?  

    - Certains fichiers partagés le sont-ils avec le compte personnel de quelqu’un ?  

3. Accédez à **Examiner**, **Utilisateurs et comptes**, puis vérifiez les points suivants :  

    - Des comptes ont-ils été inactifs dans un service particulier pendant une longue période de temps ? Pouvez-vous révoquer la licence de cet utilisateur pour ce service ?  

    - Voulez-vous connaître les utilisateurs qui remplissent un rôle spécifique ?  

    - Certaines personnes qui ont été licenciées ont-elles toujours accès à une application, lequel accès pourrait leur permettre de dérober des informations ?  

    - Voulez-vous révoquer l’autorisation d’un utilisateur pour une application spécifique ou obliger un utilisateur spécifique à effectuer une authentification multifacteur ?  

    - Vous pouvez explorer le compte de l’utilisateur en cliquant sur les trois points à la fin de la ligne du compte de l’utilisateur, et en sélectionnant une action à effectuer. Vous pouvez **Suspendre l’utilisateur** ou **Supprimer les collaborations de l’utilisateur**. Si l’utilisateur a été importé depuis Azure Active Directory, vous pouvez également cliquer sur **Paramètres du compte Azure AD** pour accéder facilement aux fonctionnalités d’administration avancée de l’utilisateur. Exemples de fonctionnalités d’administration : administration de groupes, MFA, détails relatifs aux connexions de l’utilisateur et blocage de la connexion.

4. Accédez à **Investiguer**, **Applications connectées**, puis sélectionnez une application. Le tableau de bord Application s’ouvre et vous donne des informations. Vous pouvez utiliser les onglets en haut pour vérifier :  

    - Quels types d’appareils vos utilisateurs utilisent-ils pour se connecter à l’application ?  

    - Quels types de fichiers enregistrent-ils dans le cloud ?  

    - Quelle activité se produit dans l’application en ce moment même ?  

    - Des applications tierces sont-elles connectées à votre environnement ?  

    - Connaissez-vous ces applications ?  

    - Sont-elles autorisées pour le niveau d’accès auquel elles correspondent ?  

    - Combien d’utilisateurs les ont déployées ? Quelle est la fréquence de ces applications en général ?  
 
    ![Tableau de bord des applications](./media/investigate-app.png "examiner l’application")  

5. Accédez au **tableau de bord Cloud Discovery** et vérifiez les points suivants :  

    - Quelles sont les applications cloud utilisées, dans quelle mesure et par quels utilisateurs ?  

    - À quelles fins sont-elles utilisées ?  

    - Quelle quantité de données est chargée vers ces applications cloud ?  

    - Dans quelles catégories avez-vous des applications cloud approuvées, alors que les utilisateurs utilisent plutôt des solutions alternatives ?  

    - Pour les solutions alternatives, voulez-vous rendre non approuvées des applications cloud dans votre organisation ?  

    - Certaines applications cloud sont-elles utilisées, alors qu’elles ne sont pas conformes à la stratégie de votre organisation ?  

## <a name="sample-investigation"></a>Exemple d’examen
  
Partons du principe que vous pensez ne pas avoir d’accès à votre environnement cloud via des adresses IP présentant un risque. Prenons l’exemple de Tor. Vous créez cependant une stratégie pour les adresses IP à risques simplement pour vous en assurer :  

1. Dans le portail, accédez à **Contrôle**, puis choisissez **Modèles**.  

2. Choisissez la **stratégie d’activité** correspondant au **Type**.  

3. À la fin de la ligne **Connexion depuis une adresse IP à risque**, choisissez le signe plus (**+**) pour créer une stratégie.  

4. Changez le nom de la stratégie pour pouvoir l’identifier.  

5. Sous **Activités remplissant toutes les conditions suivantes**, choisissez **+** pour ajouter un filtre. Faites défiler jusqu’à **Balises IP**, puis choisissez **Tor**.  

     ![Exemple de stratégie pour les adresses IP avec risques](./media/example-policy-risky-ips.png "exemple de stratégie pour les adresses IP avec risques")  

Maintenant que la stratégie est en place, vous vous étonnez de voir que vous recevez une alerte indiquant que la stratégie a été violée.  

1. Accédez à la page **Alertes** et affichez l’alerte relative à la violation de la stratégie.  

2. Si vous constatez qu’il semble s’agir d’une réelle violation, vous pouvez contenir le risque ou le corriger.  

     Pour contenir le risque, vous pouvez envoyer à l’utilisateur une notification l’invitant à préciser si la violation était délibérée et s’il en avait conscience.  

     Vous pouvez également explorer l’alerte au niveau du détail et suspendre l’utilisateur jusqu’à ce que vous décidiez des mesures à prendre.  

3. S’il s’agit d’un événement autorisé qui a peu de chances de se reproduire, vous pouvez rejeter l’alerte.  

     S’il est autorisé et que vous pensez qu’il va se reproduire, vous pouvez modifier la stratégie pour éviter que ce type d’événement soit considéré comme une violation à l’avenir.  

## <a name="next-steps"></a>Étapes suivantes
 
Pour découvrir comment contrôler l’application cloud de votre organisation, consultez [Contrôle](control.md).   

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)  
