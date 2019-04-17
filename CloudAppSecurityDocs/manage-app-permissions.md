---
title: Contrôler quelles applications cloud tierces OAuth obtiennent des autorisations - Cloud App Security | Microsoft Docs
description: Cet article fournit des informations sur la manière dont vous pouvez contrôler, bloquer et autoriser les applications OAuth tierces.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 04/15/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 137e0630-5440-4c49-bfe4-48bbc64575e2
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 445c8ac7d535e349ed3c8bee7af100062c76d184
ms.sourcegitcommit: ec7ae3cd7648fa62d7a7925f8693dcb99b0b0d26
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59622386"
---
# <a name="manage-oauth-apps"></a>Gérer les applications OAuth

*S’applique à : Microsoft Cloud App Security*

Les applications de productivité tierces installées par des utilisateurs professionnels dans votre organisation ont souvent besoin d’une autorisation pour pouvoir accéder aux informations et données utilisateur, et se connecter au nom de l’utilisateur à d’autres applications cloud, comme Office 365, G Suite et Salesforce. Lorsque les utilisateurs installent ces applications, ils cliquent souvent sur Accepter sans examiner attentivement les détails du message d’invite, notamment concernant l’octroi d’autorisations à l’application. Ce problème est d’autant plus complexe que le service informatique ne dispose pas toujours d’informations suffisantes pour mettre en balance le risque de sécurité d’une application et les avantages qu’elle offre en termes de productivité. Dans la mesure où l’acceptation des autorisations d’applications tierces représente un risque de sécurité potentiel pour votre organisation, la surveillance des autorisations d’applications accordées par vos utilisateurs, vous donne la visibilité et le contrôle nécessaires pour protéger vos utilisateurs et vos applications. Les autorisations d’applications Microsoft Cloud App Security vous permettent de savoir quelles applications OAuth installées par l’utilisateur ont accès aux données Office 365, G Suite et Salesforce. Cloud App Security vous indique de quelles autorisations les applications disposent, et quels utilisateurs ont accordé à ces applications l’accès à leurs comptes Office 365, G Suite et Salesforce. Avec les autorisations d’applications, vous décidez à quelles applications vous autorisez les utilisateurs à accéder, et quelles autres vous voulez exclure.

Pour plus d’informations sur l’examen des applications Oauth, consultez 

## <a name="working-with-the-oauth-apps-page"></a>Utilisation de la page Applications OAuth

La page **OAuth** affiche des informations sur les autorisations d’applications dans vos applications connectées.

Pour accéder à l’onglet OAuth

Dans le portail Cloud App Security, cliquez sur **Examiner**, puis sur **Applications OAuth**.


 ![autorisations d’applications](./media/app-permissions.png)

La page Applications OAuth fournit les informations suivantes sur chaque application OAuth à laquelle des autorisations ont été accordées :

|Élément|Signification|S’applique à|
|-------|-------|-------|
|Icône De base dans la barre de requête d’application  |Basculer vers la requête dans la vue de base.|Office 365, G Suite, Salesforce|
|Icône Avancé dans la barre de requête d’application  |Basculer vers la requête dans la vue avancée.|Office 365, G Suite, Salesforce|
|Icône d’ouverture ou de fermeture de tous les détails dans la liste des applications  |Afficher plus ou moins d’informations sur chaque application.|
|Icône d’exportation dans la liste des applications  |Exporter un fichier CSV contenant une liste d’applications, le nombre d’utilisateurs pour chaque application, les autorisations associées à l’application, le niveau d’autorisation, l’état de l’application et le niveau d’utilisation communautaire.|Office 365, G Suite, Salesforce|
|Application|Nom de l’application. Sélectionnez le nom pour afficher plus d’informations, notamment la description, l’éditeur (pour Office 365), le site web de l’application et son ID.|Office 365, G Suite, Salesforce|
|Autorisé par|Le nombre d’utilisateurs ayant autorisé cette application à accéder à leur compte d’application et ayant accordé les autorisations d’applications. Sélectionnez le nombre pour afficher des informations supplémentaires, notamment une liste d’e-mails d’utilisateurs ou une mention indiquant si un administrateur a précédemment autorisé l’application.|Office 365, G Suite, Salesforce|
|Niveau d’autorisation  |Icône de niveau d’autorisation et texte indiquant Élevé, Moyen ou Bas. Le niveau indique le degré d’accès de cette application aux données d’application. Par exemple, Faible peut indiquer que l’application a uniquement accès au nom et au profil utilisateur. Sélectionnez le niveau pour afficher des informations supplémentaires, notamment les autorisations accordées à l’application, l’utilisation communautaire ou l’activité associée dans [Journal de gouvernance](governance-actions.md).|Office 365, G Suite|
|État de l’application|Un administrateur peut marquer une application comme approuvée, exclue ou laisser le statut non défini.|Office 365, G Suite, Salesforce|
|Utilisation communautaire|Indique la cote de popularité de l’application parmi tous vos utilisateurs (utilisation courante, peu courante, rare)|Office 365, G Suite, Salesforce|
|Dernière autorisation|Date la plus récente à laquelle un utilisateur a accordé des autorisations pour cette application.|Office 365, Salesforce|
|Éditeur|Nom du fournisseur qui fournit l’application.|Office 365|
|Dernière utilisation|Date la plus récente à laquelle cette application a été utilisée par une personne de votre organisation.|Salesforce|


## <a name="ban-or-approve-an-app"></a>Exclure ou approuver une application

1. Dans la page **Applications OAuth**, cliquez sur l’application pour ouvrir le **tiroir Application** et afficher plus d’informations sur l’application et les autorisations qui lui ont été accordées.
   
   - Cliquez sur le lien **Autorisations** pour afficher la liste complète des autorisations qui ont été accordées à l’application. 
   - Sous **Utilisation communautaire**, vous pouvez afficher la fréquence d’utilisation de cette application dans d’autres organisations.  
   - Cliquez sur le lien **Activité associée** pour afficher les activités qui sont listées dans le journal de gouvernance lié à cette application.

2. Pour exclure l’application, cliquez sur l’icône d’exclusion à l’extrémité de la ligne de l’application dans le tableau.
   
     ![icône d’exclusion de l’application](./media/ban-app-icon.png) 

    - Vous pouvez choisir de signaler aux utilisateurs que l’application qu’ils ont installée et autorisée a été interdite. La notification signale aux utilisateurs que l’application sera désactivée et qu’ils n’auront pas accès à l’application connectée. Si vous ne souhaitez pas les en informer, désélectionnez **Avertir les utilisateurs qui ont accordé l’accès à cette application interdite** dans la boîte de dialogue. 
    - Nous vous recommandons d’avertir les utilisateurs que leur application est sur le point d’être exclue.

      ![exclure l’application](./media/ban-app.png)

3. Tapez le message à envoyer aux utilisateurs de l’application dans la zone Entrez un message de notification personnalisé. Cliquez sur **Exclure l’application** pour envoyer l’e-mail et exclure l’application des utilisateurs de votre application connectée.


4. Pour approuver l’application, cliquez sur l’icône d’approbation à l’extrémité de la ligne dans le tableau. 

   ![approuver l’application](./media/approve-app.png) 

   - L’icône prend la couleur verte et l’application est approuvée pour tous les utilisateurs de votre application connectée.
   - Quand vous marquez une application comme approuvée, il n’y a aucune incidence sur l’utilisateur final. Ce changement de couleur vous aide simplement à identifier les applications que vous avez approuvées, pour les distinguer de celles que vous n’avez pas encore vérifiées.



## <a name="revoke-app-and-notify-user"></a>Révoquer l’application et avertir l’utilisateur

Pour G Suite et Salesforce, vous pouvez révoquer l’autorisation d’une application ou avertir l’utilisateur qu’il doit la changer. Lorsque vous révoquez l’autorisation, il supprime toutes les autorisations qui ont été accordées à l’application sous « Applications d’entreprise » dans Azure AD.

1. Dans la page **Applications OAuth**, cliquez sur les points de suspension à la fin de la ligne de l’application et sélectionnez **Notifier l’utilisateur**. Par défaut, l’utilisateur sera informé comme suit : *Vous avez autorisé l’application à accéder à votre compte G Suite. Cette application est en conflit avec la stratégie de sécurité de votre organisation. Vous devez fournir ou révoquer les autorisations que vous avez attribuées à cette application dans votre compte G Suite. Pour révoquer l’accès à l’application, accédez à : https://security.google.com/settings/security/permissions?hl=en&pli=1 Sélectionnez l’application et cliquez sur « Révoquer l’accès » dans la barre de menu de droite.* Vous pouvez personnaliser le message envoyé.
2. Vous pouvez également révoquer des autorisations d’utilisation de l’application pour l’utilisateur. Cliquez sur l’icône à la fin de la ligne de l’application dans le tableau et sélectionnez **Révoquer l’application**. 

   ![révoquer l’application](./media/revoke-app.png)

## <a name="query-oauth-apps"></a>Interroger des applications OAuth

Vous pouvez interroger des applications OAuth dans la vue **De base** ou la vue **Avancée**. Sélectionnez des valeurs dans une ou plusieurs listes déroulantes pour afficher les applications spécifiques dans la vue de base. Dans la vue avancée, utilisez la zone de liste déroulante **Sélectionner un filtre** pour affiner votre recherche. Ajoutez des opérateurs (est égal à ou n’est pas égal à une valeur sélectionnée) pour terminer votre requête.

- Cliquez sur l’icône **Ajouter un filtre** pour ajouter des filtres supplémentaires et affiner davantage votre requête. Les filtres sont appliqués automatiquement et la liste des applications est mise à jour.

- Cliquez sur l’icône **Supprimer un filtre** en regard d’un filtre pour le supprimer.

## <a name="send-feedback"></a>Envoyer des commentaires

Vous pouvez envoyer des commentaires à l’équipe Cloud App Security pour nous indiquer s’il existe une application OAuth découverte dans votre organisation qui semble malveillante. Cette fonctionnalité vous permet de faire partie de notre communauté de sécurité et d’améliorer l’analyse et le score de risque de l’application OAuth.
1. Dans la page **Applications OAuth**, cliquez sur les points de suspension à la fin de la ligne de l’application et sélectionnez **Signaler l’application**.  

   ![signaler l’application](./media/report-app.png)
2. Dans l’écran **Signaler cette application**, vous pouvez choisir de signaler l’application comme étant malveillante ou de signaler tout autre problème lié à la façon dont Cloud App Security perçoit l’application. Par exemple, vous pourriez utiliser **Éditeur incorrect**, **Autorisations incorrectes** ou **Autre**. Les données que vous envoyez permettent de mettre à jour le score de risque de l’application et d’autres données analytiques sur l’application.

## <a name="next-steps"></a>Étapes suivantes

[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)  
