---
title: "Contrôler | Documentation Microsoft"
description: "Cet article fournit des informations sur les actions de gouvernance à entreprendre dans Cloud App Security pour contrôler l’usage des applications cloud de votre organisation."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: bc11bbfe-ec6c-458c-8302-8112c383199d
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: 9dc74c35f32c9a3dff251d6e0ac6b35a3591f4b9


---

# <a name="control"></a>Control
Les actions de gouvernance sont applicables aux fichiers des utilisateurs dans tout votre environnement cloud. Après avoir soigneusement examiné et étudié votre cloud, vous pouvez utiliser des actions de gouvernance pour protéger votre organisation.  
  
## <a name="applying-governance-actions"></a>Application d’actions de gouvernance  
Les actions de gouvernance sont applicables depuis les stratégies, depuis les alertes et depuis le journal **Fichier**.  
  
À tout moment, vous pouvez consulter et afficher l’état de toutes les actions de gouvernance précédemment appliquées en accédant à la dent **Paramètres** ![icône des paramètres](./media/settings-icon.png "settings icon") et en cliquant sur **Journal de gouvernance**.  
  
Pour toute action de gouvernance qui a échoué, cliquez sur l’icône de nouvelle tentative ![icône de nouvelle tentative](./media/retry-icon.png "retry icon") pour l’appliquer à nouveau.  
  
Selon le type de stratégie, violation et application, différentes actions de gouvernance sont disponibles.  
  
## <a name="moving-from-detection-to-automatic-remediation"></a>Passage de la détection à la correction automatique  
Après avoir défini et personnalisé vos filtres de stratégie, vous pouvez sélectionner les actions de gouvernance automatisées qui sont mises en place à chaque violation de votre stratégie.  
Étant donné que les actions de correction exploitent les API du fournisseur de cloud, ces actions peuvent varier d’une application à l’autre.  
  
> [!NOTE]  
>  Soyez vigilant quand vous définissez des actions de gouvernance. Elles peuvent entraîner une perte irréversible des autorisations d’accès à vos fichiers.  
> Il est recommandé d’affiner les filtres pour représenter exactement les fichiers sur lesquels vous voulez agir, en utilisant plusieurs champs de recherche. Plus les filtres sont précis, mieux c’est.  
>   
>  Pour obtenir des instructions, vous pouvez utiliser le bouton **Modifier et afficher un aperçu des résultats** dans la section Filtres.  
  
![stratégie de fichier, modifier et afficher un aperçu des résultats](./media/file-policy-edit-and-preview-results.png "file policy edit and preview results")  
  
## <a name="migration"></a>Migration  
Cloud App Security vous permet d’introduire vos migrations en vous faisant savoir qui dans votre organisation utilise quelles applications et en vous donnant les outils nécessaires pour surveiller l’adoption de nouvelles applications. Ce composant peut également vous aider à déterminer quels types d’applications vous pouvez proposer dans votre organisation, en vous fournissant les outils nécessaires pour voir ce que tout le monde utilise déjà.  
  
### <a name="how-to-migrate-your-users-to-a-new-app"></a>Comment faire migrer vos utilisateurs vers une nouvelle application  
Imaginons le scénario suivant : vous venez d’acheter Office 365 et vous voulez que tous les utilisateurs de votre organisation arrêtent d’utiliser toutes les autres applications de stockage cloud pour commencer à utiliser OneDrive. Voici comment vous pouvez procéder :  
  
-   Accédez à votre **tableau de bord Cloud Discovery** et sous **Catégories**, filtrez les applications par **Stockage cloud**. Ensuite, triez les résultats par **Utilisateurs** ou **Adresses IP** et déterminez quelle est l’application la plus populaire.  
  
-   Vous pouvez voir quels utilisateurs utilisent d’autres applications.  
  
     Vous pouvez également explorer ces applications au niveau du détail et avertir leurs utilisateurs que vous voulez qu’ils migrent vers OneDrive, comme suit :  
  
    1.  Dans votre **tableau de bord Cloud Discovery**, cliquez sur Dropbox, puis sur l’onglet **Adresse IP** ou **Utilisateurs**.  
  
    2.  Cliquez sur la flèche ![icône de flèche](./media/arrow-icon.png "arrow icon") et sélectionnez **Exporter**.  
  
### <a name="find-more-secure-alternatives"></a>Trouver des alternatives plus sécurisées  
Le catalogue de services Cloud App Security peut vous aider à trouver des alternatives satisfaisantes pour votre organisation et ainsi éviter les applications risquées auxquelles ont éventuellement recours certains de vos utilisateurs.  
  
Imaginons le scénario suivant : vous envisagez également d’acheter une application de productivité mais vous n’êtes pas sûr que vos utilisateurs s’en serviront.  
  
-   Accédez au **tableau de bord Cloud Discovery**.  
  
-   Sous **Catégories**, filtrez les applications par **Productivité**.  
  
-   Pour chaque application en cours d’utilisation, consultez le **Score** pour voir si elle est fiable et dans le cas contraire, pourquoi.  
  
-   Si vous décidez d’acheter une licence d’entreprise pour toute l’organisation, n’hésitez pas à consulter la colonne **Utilisateurs** pour voir ce qui est déjà le plus adopté par vos utilisateurs, pour voir si l’application en question est approuvée et pour connaître ses fonctionnalités de sécurité avant de prendre votre décision.  
  
## <a name="see-also"></a>Voir aussi  
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO4-->


