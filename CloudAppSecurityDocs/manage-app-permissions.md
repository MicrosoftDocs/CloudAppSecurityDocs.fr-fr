---
title: Contrôler quelles applications cloud tierces obtiennent des autorisations | Microsoft Docs
description: Cet article fournit des informations sur la manière dont vous pouvez contrôler, bloquer et accepter les autorisations d’applications tierces.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 137e0630-5440-4c49-bfe4-48bbc64575e2
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: bc91dadaacc00accdc95f6e6cabe65e4508eccf9
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44144021"
---
*S’applique à : Microsoft Cloud App Security*


# <a name="manage-app-permissions"></a>Gérer les autorisations d’applications
Les applications de productivité tierces installées par des utilisateurs professionnels dans votre organisation ont souvent besoin d’une autorisation pour pouvoir accéder aux informations et données utilisateur, et se connecter au nom de l’utilisateur à d’autres applications cloud, comme Office 365, G Suite et Salesforce.  Lorsque les utilisateurs installent ces applications, ils cliquent souvent sur Accepter sans examiner attentivement les détails du message d’invite, notamment concernant l’octroi d’autorisations à l’application.  Ce problème est d’autant plus complexe que le service informatique ne dispose pas toujours d’informations suffisantes pour mettre en balance le risque de sécurité d’une application et les avantages qu’elle offre en termes de productivité. Dans la mesure où l’acceptation des autorisations d’applications tierces représente un risque de sécurité potentiel pour votre organisation, la surveillance des autorisations d’applications accordées par vos utilisateurs, vous donne la visibilité et le contrôle nécessaires pour protéger vos utilisateurs et vos applications. Les autorisations d’applications Microsoft Cloud App Security vous permettent de savoir quelles applications installées par les utilisateurs ont accès aux données Office 365, G Suite et Salesforce, de quelles autorisations disposent ces applications et quels utilisateurs ont accordé à ces applications l’accès à leur compte Office 365, G Suite et Salesforce. Avec les autorisations d’applications vous décidez à quelles applications vous autorisez les utilisateurs à accéder et quelles autres vous voulez exclure.


## <a name="working-with-the-app-permissions-page"></a>Utilisation de la page des autorisations d’applications

La page **Autorisations d’applications** affiche des informations sur les autorisations d’applications dans vos applications connectées.

Pour accéder à l’onglet Autorisations d’applications :

Dans le portail Cloud App Security, cliquez sur **Examiner**, puis sur **Autorisations d’applications**.


 ![autorisations d’applications](./media/app-permissions.png)

La page Autorisations d’applications fournit les informations suivantes sur chaque application tierce à laquelle des autorisations ont été accordées :

|Élément|Signification|S’applique à|
|-------|-------|-------|
|Icône De base dans la barre de requête d’application  |Sélectionnez cette icône pour basculer vers l’interrogation dans la vue de base.|Office 365, G Suite, Salesforce|
|Icône Avancé dans la barre de requête d’application  |Sélectionnez cette icône pour basculer vers l’interrogation dans la vue avancée.|Office 365, G Suite, Salesforce|
|Icône d’ouverture ou de fermeture de tous les détails dans la liste des applications  |Sélectionnez cette icône pour afficher plus ou moins d’informations sur chaque application.|
|Icône d’exportation dans la liste des applications  |Sélectionnez cette icône pour exporter un fichier CSV contenant une liste d’applications, le nombre d’utilisateurs pour chaque application, les autorisations associées à l’application, le niveau d’autorisation, l’état de l’application et le niveau d’utilisation communautaire.|Office 365, G Suite, Salesforce|
|Application|Nom de l’application. Sélectionnez le nom pour afficher plus d’informations, notamment la description, l’éditeur (pour Office 365), le site web de l’application et son ID.|Office 365, G Suite, Salesforce|
|Autorisé par|Le nombre d’utilisateurs ayant autorisé cette application à accéder à leur compte d’application et ayant accordé les autorisations d’applications. Sélectionnez le nombre pour afficher des informations supplémentaires, notamment une liste d’e-mails utilisateurs ou une mention indiquant si un administrateur a ou non précédemment autorisé l’application.|Office 365, G Suite, Salesforce|
|Niveau d’autorisation  |Icône de niveau d’autorisation et texte indiquant Élevé, Moyen ou Bas. Le niveau indique le degré d’accès de cette application aux données d’application. Par exemple, Faible peut indiquer que l’application a uniquement accès au nom et au profil utilisateur. Sélectionnez le niveau pour afficher des informations supplémentaires, notamment les autorisations accordées à l’application, l’utilisation communautaire ou l’activité associée dans [Journal de gouvernance](governance-actions.md).|Office 365, G Suite|
|État de l’application|Un administrateur peut marquer une application comme approuvée, exclue ou laisser le statut non défini.|Office 365, G Suite, Salesforce|
|Utilisation communautaire|Sélectionnez cette option si vous souhaitez connaître la cote de popularité de l’application parmi tous vos utilisateurs (utilisation courante, peu courante, rare)|Office 365, G Suite, Salesforce|
|Dernière autorisation|Date la plus récente à laquelle un utilisateur a accordé des autorisations pour cette application.|Office 365, Salesforce|
|Éditeur|Nom du fournisseur qui fournit l’application.|Office 365|
|Dernière utilisation|Date la plus récente à laquelle cette application a été utilisée par une personne de votre organisation.|Salesforce|


## <a name="ban-or-approve-an-app"></a>Exclure ou approuver une application
1. Dans la page Autorisations d’applications, cliquez sur l’application pour ouvrir le tiroir Application, et afficher plus d’informations sur l’application et les autorisations qui lui ont été accordées. Vous pouvez cliquer sur le lien Autorisations pour afficher la liste complète des autorisations qui ont été accordées à l’application. Sous Utilisation communautaire, vous pouvez afficher la fréquence d’utilisation de cette application dans d’autres organisations. Vous pouvez également cliquer sur le lien Activité associée pour afficher les activités qui sont répertoriées dans le journal de gouvernance lié à cette application.
2. Pour exclure l’application, cliquez sur l’icône d’exclusion à l’extrémité de la ligne de l’application dans le tableau. <br></br>
   ![icône d’exclusion de l’application](./media/ban-app-icon.png) <br></br>
   Quand vous excluez une application, vous pouvez choisir d’informer les utilisateurs que l’application qu’ils ont déjà installée et autorisée a été exclue, sera par conséquent désactivée et n’aura pas accès à l’application connectée. Si vous ne souhaitez pas les en informer, désélectionnez Avertir les utilisateurs qui ont accordé l'accès à cette application interdite dans la boîte de dialogue Exclure l’application.

    ![exclure l’application](./media/ban-app.png)
   > [!Note]
   > Il est recommandé d’informer les utilisateurs que leur application est sur le point d’être exclue.

3. Pour approuver l’application, cliquez sur l’icône d’approbation à l’extrémité de la ligne dans le tableau. <br></br>
   ![approuver l’application](./media/approve-app.png) <br></br>
   L’icône prend la couleur verte et l’application est approuvée pour tous les utilisateurs de votre application connectée.
   > [!Note]
   > Lorsque vous marquez une application comme approuvée, il n’y a aucune incidence sur l’utilisateur final. Cela permet simplement de marquer visuellement les applications que vous avez approuvées pour les distinguer de celles que vous n’avez pas encore vérifiées.

4. Tapez le message à envoyer aux utilisateurs de l’application dans la zone Entrez un message de notification personnalisé, puis mettez si nécessaire à jour l’adresse de réponse de l’e-mail de notification. 
   Cliquez sur **Exclure l’application** pour envoyer l’e-mail et exclure l’application des utilisateurs de votre application connectée.

## <a name="revoke-app-and-notify-user"></a>Révoquer l’application et avertir l’utilisateur

Pour G Suite et Salesforce, vous pouvez révoquer l’autorisation d’une application ou avertir l’utilisateur qu’une autorisation doit être révoquée. 

1. Dans la page **Autorisations d’applications**, cliquez sur les points de suspension à la fin de la ligne de l’application et sélectionnez **Notifier l’utilisateur**. Par défaut, l’utilisateur est averti de la façon suivante : *Vous avez autorisé l’application Adallom Google Protector à accéder à votre compte G Suite. Cette application est en conflit avec la stratégie de sécurité de votre organisation. Vous devez fournir ou révoquer les autorisations que vous avez attribuées à cette application dans votre compte G Suite. Pour révoquer l’accès à l’application, accédez à : https://security.google.com/settings/security/permissions?hl=en&pli=1 Sélectionnez l’application et cliquez sur « Révoquer l’accès » dans la barre de menu de droite.* Vous pouvez personnaliser le message envoyé.
2. Vous pouvez également révoquer l’autorisation d’utilisation de l’application pour l’utilisateur en cliquant sur l’icône située à la fin de la ligne de l’application dans le tableau et en sélectionnant **Révoquer l’application**. 

   ![révoquer l’application](./media/revoke-app.png)

## <a name="query-app-permissions"></a>Interroger les autorisations d’applications

Vous pouvez interroger les autorisations d’applications dans la vue **de base** ou la vue **avancée**. Dans la vue de base, sélectionnez des valeurs dans une ou plusieurs listes déroulantes pour afficher les applications spécifiques. Dans la vue avancée, utilisez la zone de liste déroulante **Sélectionner un filtre** pour affiner votre recherche. Ajoutez des opérateurs (est égal à ou n’est pas égal à une valeur sélectionnée) pour terminer votre requête.

- Cliquez sur l’icône **Ajouter un filtre** pour ajouter des filtres supplémentaires et affiner davantage votre requête. Les filtres sont appliqués automatiquement et la liste des applications est mise à jour en conséquence.

- Cliquez sur l’icône **Supprimer un filtre** en regard d’un filtre pour le supprimer.

## <a name="send-feedback"></a>Envoyer des commentaires

Vous pouvez envoyer des commentaires à l’équipe Cloud App Security pour nous indiquer s’il existe une application OAuth découverte dans votre organisation qui semble malveillante. Cette nouvelle fonctionnalité vous permet de faire partie de notre communauté de sécurité et d’améliorer l’analyse et le score de risque de l’application OAuth.
1. Dans la page **Autorisations d’applications**, cliquez sur les points de suspension à la fin de la ligne de l’application et sélectionnez **Signaler l’application**.  

   ![signaler l’application](./media/report-app.png)
2. Dans l’écran **Signaler cette application**, vous pouvez choisir de signaler l’application comme étant malveillante ou de signaler tout autre problème avec la façon dont Cloud App Security perçoit l’application, par exemple, **Éditeur incorrect** ou **Autorisations incorrectes**. Les données que vous envoyez permettent de mettre à jour le score de risque de l’application, ainsi que d’autres données analytiques sur l’application.

 
## <a name="see-also"></a>Voir aussi  
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  