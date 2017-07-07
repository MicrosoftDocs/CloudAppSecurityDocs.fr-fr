---
title: Protection de votre organisation contre les menaces | Microsoft Docs
description: "Cette rubrique décrit le scénario de protection de votre organisation contre les menaces présentes dans l’environnement cloud."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/27/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 0017be99-29c3-468e-a181-255e343ed4f5
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 7bad1e1ae6196b684ac35d063558fad22bc3689f
ms.sourcegitcommit: 2f4474084c7e07ac4853945ab5aa1ea78950675d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2017
---
# <a name="protecting-your-organization-against-threats"></a>Protection de votre organisation contre les menaces  

Identifiez les problèmes liés à une utilisation à haut risque et à la sécurité dans le cloud, détectez tout comportement anormal des utilisateurs et protégez vos applications cloud connectées contre les menaces. Bénéficiez d’une visibilité sur les activités des administrateurs et des utilisateurs, et définissez des stratégies pour générer automatiquement une alerte en cas de comportement suspect ou quand des activités spécifiques que vous considérez comme risquées se déroulent dans vos environnements approuvés. Exploitez la quantité considérable de données Microsoft relatives à l’intelligence des menaces et à la recherche sur la sécurité. Les stratégies de détection des menaces vous permettent de vous assurer que vos applications approuvées bénéficient de tous les contrôles de sécurité nécessaires et de bien les maîtriser.
 
## <a name="mass-download-by-a-single-user-data-exfiltration-by-an-insider"></a>Téléchargement en masse par un seul utilisateur (exfiltration de données par une personne interne)

Ce cas d’utilisation s’applique à Office 365, G Suite, Box, Dropbox, Salesforce.

### <a name="the-threat"></a>LA MENACE
Une personne interne malveillante peut exfiltrer des données d’Office 365 ou d’autres applications cloud en téléchargeant ou en consultant plusieurs fichiers sur une courte période de temps.

### <a name="the-solution"></a>LA SOLUTION
Détectez quand un utilisateur télécharge ou consulte un grand nombre de fichiers en peu de temps.

#### <a name="prerequisites"></a>Prérequis

[Connectez](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) au moins une application cloud à Cloud App Security.

#### <a name="setting-up-monitoring"></a>Configurer la surveillance

1.  Par défaut, Cloud App Security analyse votre réseau pour établir une base de référence, où il découvre ce que font généralement les utilisateurs dans votre cloud et à quel moment. 

2. Définissez une stratégie qui surveille vos applications cloud pour détecter les téléchargements en masse et vous alerte si une activité inhabituelle se produit :

    1. Dans la page **Stratégies**, cliquez sur [**Créer une stratégie d’activité**](user-activity-policies.md). 
   

    2. Dans le champ [**Modèle de stratégie**](policy-template-reference.md), choisissez **Téléchargement massif par un même utilisateur**.
    
    3. Vous pouvez aussi ajuster le filtre d’activité répétée.
    
    4. Cliquez sur **Créer**. 
   
     
2. Étudier les correspondances
    
    1. Dans la page **Stratégies**, cliquez sur le nom de la stratégie pour atteindre le **Rapport de stratégie**, puis passez en revue les correspondances qui ont été déclenchées.

    2. Pour examiner une correspondance, cliquez sur celle-ci et ouvrez le tiroir d’activité. Dans le tiroir, vous pouvez voir les autres stratégies correspondant à cette activité. 
    
    3. Vous pouvez vérifier les fichiers qui ont été téléchargés par l’utilisateur en cliquant sur les objets d’activité dans le **tiroir Activité**, puis sur le nom du fichier : vous accédez au fichier dans le tableau de fichiers. Dans ce tableau, vous pouvez voir si les fichiers sont détenus par l’utilisateur et avec qui ils sont partagés, et déterminer s’il s’agit de fichiers que l’utilisateur utilise habituellement ou s’ils proviennent d’une adresse IP interne et ne doivent pas être téléchargés.
     


#### <a name="validating-your-policy"></a>Valider votre stratégie

1. Pour simuler une alerte, téléchargez à partir de vos applications cloud connectées un nombre de documents supérieur au seuil que vous avez défini et sur une courte période, selon l’intervalle de temps que vous avez défini dans la stratégie (par exemple, 30 téléchargements en moins de 5 minutes).
3. Accédez au rapport de stratégie. Une correspondance de stratégie d’activité devrait apparaître sous peu. 
4. Vous pouvez cliquer sur la correspondance pour voir quels fichiers ont été téléchargés.  

#### <a name="removing-the-risk"></a>Supprimer le risque

Une fois que vous avez validé et ajusté la stratégie, supprimez les faux positifs éventuels qui peuvent avoir été signalés par votre stratégie, comme des comptes de service qui synchronisent des fichiers, des dossiers d’images des événements de la société, etc. Effectuez ensuite les opérations suivantes : 
  1. Vous pouvez lancer des [actions de gouvernance](governance-actions.md) en ouvrant l’activité dans le tiroir d’activités, puis en cliquant sur le nom du fichier sous **Objets d’activité**.

  2. Contactez les utilisateurs pour leur demander pourquoi ils ont besoin de copier autant de fichiers d’entreprise sur leur ordinateur.

 
## <a name="admin-activity-from-outside-your-organizations-network"></a>Activité d’administration en dehors du réseau de votre organisation

Ce cas d’utilisation s’applique à Office 365, G Suite, Box, Dropbox, Salesforce et Okta.

### <a name="the-threat"></a>LA MENACE
Un compte d’administrateur a été corrompu par un attaquant externe. Les comptes d’administrateur sont les comptes les plus sensibles de votre organisation, car ils ont les privilèges les plus élevés et accèdent à toutes les informations de votre organisation. Généralement, une activité d’administration doit être effectuée en interne dans le cadre du travail de l’administrateur et non à partir d’emplacements distants ou d’appareils non reconnus.

### <a name="the-solution"></a>LA SOLUTION
Détectez quand des personnes se faisant passer pour des administrateurs se connectent à votre application cloud à partir d’adresses IP externes et effectuent une activité d’administration.

#### <a name="prerequisites"></a>Conditions préalables

- [Connectez](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) au moins une application cloud à Cloud App Security.

- Accédez à **Paramètres** > **Plages d’adresses IP** et ajoutez les plages d’adresses IP des deux sous-réseaux internes et leurs adresses IP publiques de sortie, puis marquez-les comme appartenant à l’**Entreprise**.

#### <a name="setting-up-monitoring"></a>Configurer la surveillance

1.  Commencez à surveiller vos applications cloud en configurant une stratégie pour détecter les activités d’administration en dehors de votre réseau et vous alerter si une activité inhabituelle se produit :

    1. Dans la page **Stratégies**, cliquez sur [**Créer une stratégie d’activité**](user-activity-policies.md). 
   

    2. Dans le champ [**Modèle de stratégie**](policy-template-reference.md), choisissez **Activité administrative à partir d’une adresse IP n’appartenant pas à l’entreprise**, puis définissez le **Type d’activité** sur **Ouvrir une session** et sélectionnez **Utilisateur**, **Du groupe** et sélectionnez le groupe auquel vos administrateurs appartiennent.
    
    3. Vous pouvez ajuster la stratégie pour définir le nombre d’activités répétées que vous voulez considérer comme suspect.
    
    4. Cliquez sur **Créer**. 
   
     
2. Étudier les correspondances
    
    1. Dans la page **Stratégies**, cliquez sur le nom de la stratégie pour atteindre le **Rapport de stratégie**, puis passez en revue les correspondances qui ont été déclenchées.

    2. Pour examiner une correspondance, cliquez sur celle-ci et ouvrez le tiroir d’activité. Dans le tiroir, vous pouvez voir les autres stratégies correspondant à cette activité. 
     
#### <a name="validating-your-policy"></a>Valider votre stratégie

1. Pour simuler une alerte, à partir d’un ordinateur avec une adresse IP qui ne fait pas partie de votre réseau d’entreprise, effectuer des activités d’administration, en vérifiant que le nombre d’activités que vous effectuez est supérieur au seuil défini, sur une courte période selon l’intervalle de temps que vous avez défini dans la stratégie (par exemple, 1 activité en moins de 5 minutes).
3. Accédez au rapport de stratégie. Une correspondance de stratégie d’activité devrait apparaître sous peu. 
4. Vous pouvez cliquer sur la correspondance pour voir les activités qui ont été effectuées. 

#### <a name="removing-the-risk"></a>Supprimer le risque

Après avoir validé et affiné la stratégie, supprimez les faux positifs possibles qui peuvent avoir correspondu à votre stratégie. Effectuez ensuite les opérations suivantes : 
  1. Vous pouvez lancer des [actions de gouvernance](governance-actions.md) en ouvrant l’activité dans le tiroir d’activités, puis en cliquant sur le nom de l’**Utilisateur**.

  2. Dans la page de l’utilisateur qui s’ouvre, vous pouvez voir un graphique d’activité de l’utilisateur sur le dernier mois et les emplacements où l’utilisateur a été actif sur le dernier mois, ainsi que les appartenances à un groupe, l’activité des applications et les comptes. 
  
  3. Si nécessaire, vous pouvez cliquer sur **Contacter** pour envoyer un e-mail à l’utilisateur et l’alerter que son compte est corrompu.

 ![gouvernance automatique externe](./media/auto-gov-external.png)

   2. Une fois la validation effectuée, vous pouvez définir des actions de gouvernance automatiques. Par exemple, vous pouvez **Interrompre la synchronisation de l’utilisateur** ou **Supprimer les collaborations de l’utilisateur**.


## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  