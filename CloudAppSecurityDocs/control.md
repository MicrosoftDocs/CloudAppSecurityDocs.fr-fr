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
ms.sourcegitcommit: 2f158e2f3643629d215eb23281b17a58ee7f78fc
ms.openlocfilehash: 5a051fc106661fc2266587ac5dbbb8bbdabd88bc


---

# <a name="control"></a>Control
Vous pouvez appliquer des actions de gouvernance aux fichiers des utilisateurs dans tout votre environnement cloud. Après avoir soigneusement examiné et étudié votre cloud, vous pouvez utiliser des actions de gouvernance pour protéger votre organisation.  

## <a name="apply-governance-actions"></a>Appliquer des actions de gouvernance  
Vous pouvez appliquer des actions de gouvernance depuis des stratégies, depuis des alertes et depuis le journal **Fichier**.  

À tout moment, vous pouvez consulter et afficher l’état de toutes les actions de gouvernance précédemment appliquées en accédant à la roue dentée **Paramètres** ![Icône Paramètres](./media/settings-icon.png "settings icon") et en cliquant sur **Journal de gouvernance**.  

Pour toute action de gouvernance ayant échoué, cliquez sur l’icône **Nouvelle tentative** ![Icône Nouvelle tentative](./media/retry-icon.png "retry icon") pour l’appliquer à nouveau.  

Selon le type de stratégie, violation et application, différentes actions de gouvernance sont disponibles.  

## <a name="move-from-detection-to-automatic-remediation"></a>Passer de la détection à la correction automatique  
Après avoir défini et personnalisé vos filtres de stratégie, vous pouvez sélectionner des actions de gouvernance automatisées qui sont déclenchées à chaque violation de votre stratégie.  
Étant donné que les actions de correction utilisent les API du fournisseur cloud, ces actions peuvent varier d’une application à l’autre.  

> [!NOTE]  
>  Soyez spécialement prudent quand vous définissez des actions de gouvernance. Elles peuvent entraîner une perte irréversible des autorisations d’accès à vos fichiers.  
> Il est recommandé d’affiner les filtres pour représenter exactement les fichiers sur lesquels vous voulez agir, en utilisant plusieurs champs de recherche. Plus les filtres sont précis, mieux c’est.  
>   
>  Pour obtenir des instructions, vous pouvez utiliser le bouton **Modifier et afficher un aperçu des résultats** dans la section **Filtres**.  

![Modification et aperçu des résultats des stratégies de fichiers](./media/file-policy-edit-and-preview-results.png "file policy edit and preview results")  

## <a name="migration"></a>Migration  
Cloud App Security vous permet d’introduire vos migrations en vous faisant savoir qui dans votre organisation utilise quelles applications et en vous donnant les outils nécessaires pour surveiller l’adoption de nouvelles applications. Ce composant peut également vous aider à déterminer quels types d’applications vous pouvez proposer dans votre organisation, en vous fournissant les outils nécessaires pour voir ce que tout le monde utilise déjà.  

### <a name="migrate-your-users-to-a-new-app"></a>Migrer vos utilisateurs vers une nouvelle application  
Imaginons le scénario suivant : vous venez d’acheter Office 365 et vous voulez que tous les utilisateurs de votre organisation arrêtent d’utiliser toutes les autres applications de stockage cloud pour commencer à utiliser OneDrive. Voici comment vous pouvez procéder :  

1.   Accédez à votre **tableau de bord Cloud Discovery** et sous **Catégories**, filtrez les applications par **Stockage cloud**. Ensuite, triez les résultats par **Utilisateurs** ou **Adresses IP** et déterminez quelle est l’application la plus populaire.  

2.   Vous pouvez voir quels utilisateurs utilisent d’autres applications. Vous pouvez également explorer ces applications de façon détaillée et avertir les utilisateurs que vous voulez qu’ils migrent vers OneDrive, comme suit :

    1.  Dans votre **tableau de bord Cloud Discovery**, choisissez **Dropbox**, puis choisissez l’onglet **Adresse IP** ou **Utilisateurs**.  

    2.  Choisissez la flèche ![Icône Flèche](./media/arrow-icon.png "arrow icon") et sélectionnez **Exporter**.  

### <a name="find-more-secure-alternatives"></a>Trouver des alternatives plus sécurisées  
Le catalogue de services Cloud App Security peut vous aider à trouver des alternatives satisfaisantes pour votre organisation et ainsi éviter les applications risquées auxquelles vos utilisateurs peuvent avoir recours.  

Imaginons le scénario suivant : vous envisagez d’acheter une application de productivité mais vous n’êtes pas sûr que vos utilisateurs s’en serviront.  

1.   Accédez au **tableau de bord Cloud Discovery**.  

2.   Sous **Catégories**, filtrez les applications par **Productivité**.  

3.   Pour chaque application utilisée, consultez le **Score** pour voir si elle est fiable et dans le cas contraire, pourquoi.  

4.   Si vous décidez que vous voulez acheter une licence d’entreprise pour toute l’organisation, vous pouvez examiner la colonne **Utilisateurs**. Vous pouvez voir ici ce qui est déjà le plus répandu parmi vos utilisateurs, si ces applications sont fiables et quelles sont leurs fonctionnalités de sécurité avant de prendre votre décision.  

## <a name="see-also"></a>Voir aussi  
Pour savoir comment utiliser et configurer des stratégies permettant de contrôler l’utilisation des applications cloud, consultez [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md).   
Pour obtenir du support technique, accédez à la page [Support assisté Cloud App Security](http://support.microsoft.com/oas/default.aspx?prid=16031).   
Les clients Premier peuvent également choisir Cloud App Security directement depuis le [portail Premier](https://premier.microsoft.com/).  



<!--HONumber=Nov16_HO5-->


