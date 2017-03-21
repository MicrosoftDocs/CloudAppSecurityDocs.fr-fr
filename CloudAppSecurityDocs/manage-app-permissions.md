---
title: "Contrôler quelles applications cloud tierces obtiennent des autorisations | Microsoft Docs"
description: "Cet article fournit des informations sur la manière dont vous pouvez contrôler, bloquer et accepter les autorisations d’applications tierces."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/23/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 137e0630-5440-4c49-bfe4-48bbc64575e2
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 3866ae5606fd2add90338ac58a49edf646aa87c5
ms.sourcegitcommit: 355226ee21981563066d637e7db0bff0d53c2da6
translationtype: HT
---
# <a name="manage-app-permissions"></a>Gérer les autorisations d’applications
Les applications de productivité tierces installées par des utilisateurs professionnels dans votre organisation ont souvent besoin d’une autorisation pour pouvoir accéder aux informations et données utilisateur et se connecter au nom de l’utilisateur à d’autres applications cloud, comme Office 365.  Lorsque les utilisateurs installent ces applications, ils cliquent souvent sur Accepter sans examiner attentivement les détails du message d’invite, notamment concernant l’octroi d’autorisations à l’application.  Ce problème est d’autant plus complexe que le service informatique ne dispose pas toujours d’informations suffisantes pour mettre en balance le risque de sécurité d’une application et les avantages qu’elle offre en termes de productivité. Dans la mesure où l’acceptation des autorisations d’applications tierces représente un risque de sécurité potentiel pour votre organisation, le fait que vous puissiez contrôler les autorisations d’applications accordées par vos utilisateurs, vous donne la visibilité et le contrôle nécessaires pour protéger vos utilisateurs et vos applications. Les autorisations d’applications Cloud App Security vous permettent de savoir quelles applications installées par les utilisateurs ont accès aux données Office 365, de quelles autorisations disposent ces applications et quels utilisateurs ont accordé à ces applications l’accès à leur compte Office 365. Avec les autorisations d’applications vous décidez à quelles applications vous autorisez les utilisateurs à accéder et quelles autres vous voulez exclure.


## <a name="working-with-the-app-permissions-page"></a>Utilisation de la page des autorisations d’applications

L’onglet **Autorisations d’applications** affiche des informations sur les autorisations d’applications dans votre client Office 365.

Pour accéder à l’onglet Autorisations d’applications :

1. Dans le portail Cloud App Security, cliquez sur **Examiner**, puis sous **Applications connectées**, sélectionnez **Office 365**. 
> [!Note]
> Vous devez commencer par connecter Cloud App Security à Office 365 avant de pouvoir travailler avec les autorisations d’applications.

2. Ensuite, dans le tableau de bord Office 365, cliquez sur l’onglet **Autorisations d’applications**.


 ![autorisations d’applications](./media/app-permissions.png)

La page Autorisations d’applications fournit les informations suivantes sur chaque application tierce à laquelle des autorisations ont été accordées :

|Élément|Signification|
|-------|----------------|
|Icône De base dans la barre de requête d’application  |Sélectionnez cette icône pour basculer vers l’interrogation dans la vue de base.|
|Icône Avancé dans la barre de requête d’application  |Sélectionnez cette icône pour basculer vers l’interrogation dans la vue avancée.|
|Icône d’ouverture ou de fermeture de tous les détails dans la liste des applications  |Sélectionnez cette icône pour afficher plus ou moins d’informations sur chaque application.|
|Icône d’exportation dans la liste des applications  |Sélectionnez cette icône pour exporter un fichier CSV contenant une liste d’applications, le nombre d’utilisateurs pour chaque application, les autorisations associées à l’application, le niveau d’autorisation, l’état de l’application et le niveau d’utilisation communautaire.|
|Application|Nom de l’application. Sélectionnez le nom pour afficher des informations supplémentaires, notamment la description, l’éditeur, le site web de l’application et son ID.|
|Autorisé par|Le nombre d’utilisateurs ayant autorisé cette application à accéder à leur compte Office 365 et ayant accordé les autorisations d’applications. Sélectionnez le nombre pour afficher des informations supplémentaires, notamment une liste d’e-mails utilisateurs ou une mention indiquant si un administrateur a ou non précédemment autorisé l’application.|
|Niveau d’autorisation  |Icône de niveau d’autorisation et texte indiquant Élevé, Moyen ou Bas. Le niveau indique le degré d’accès de cette applications aux données Office 365. Par exemple, Faible peut indiquer que l’application a uniquement accès au nom et au profil utilisateur. Sélectionnez le niveau pour afficher des informations supplémentaires, notamment les autorisations accordées à l’application, l’utilisation communautaire ou l’activité associée dans [Journal de gouvernance](governance-actions.md).|
|État de l’application (Exclu, Approuvé ou Non défini).  |Un administrateur peut marquer une application comme approuvée, exclue ou laisser le statut non défini.|


## <a name="ban-or-approve-an-app"></a>Exclure ou approuver une application
1. Dans la page Autorisations d’applications, cliquez sur l’application pour ouvrir le tiroir Application et afficher plus d’informations sur l’application et les autorisations qui lui ont été accordées. Vous pouvez cliquer sur le lien Autorisations pour afficher la liste complète des autorisations qui ont été accordées à l’application. Sous Utilisation communautaire, vous pouvez afficher la fréquence d’utilisation de cette application dans d’autres organisations. Vous pouvez également cliquer sur le lien Activité associée pour afficher les activités qui sont répertoriées dans le journal de gouvernance lié à cette application.
2. Pour exclure l’application, cliquez sur l’icône d’exclusion à l’extrémité de la ligne de l’application dans le tableau. <br></br>
 ![icône d’exclusion de l’application](./media/ban-app-icon.png) <br></br>
Lorsque vous excluez une application, vous pouvez choisir si vous souhaitez informer les utilisateurs que l’application qu’ils ont précédemment installée et autorisée a été exclue et sera par conséquent désactivée et n’aura pas accès à Office 365. Si vous ne souhaitez pas les en informer, désélectionnez Avertir les utilisateurs qui ont accordé l'accès à cette application interdite dans la boîte de dialogue Exclure l’application.

    ![exclure l’application](./media/ban-app.png)
> [!Note]
> Il est recommandé d’informer les utilisateurs que leur application est sur le point d’être exclue.

3. Pour approuver l’application, cliquez sur l’icône d’approbation à l’extrémité de la ligne dans le tableau. <br></br>
 ![approuver l’application](./media/approve-app.png) <br></br>
L’icône prend la couleur verte et l’application est approuvée pour tous vos utilisateurs Office 365.
> [!Note]
> Lorsque vous marquez une application comme approuvée, il n’y a aucune incidence sur l’utilisateur final. Cela permet simplement de marquer visuellement les applications que vous avez approuvées pour les distinguer de celles que vous n’avez pas encore vérifiées.

3. Tapez le message à envoyer aux utilisateurs de l’application dans la zone Entrez un message de notification personnalisé, puis mettez si nécessaire à jour l’adresse de réponse de l’e-mail de notification. 
 Cliquez sur **Exclure l’application** pour envoyer l’e-mail et exclure l’application de vos utilisateurs Office 365.


## <a name="query-app-permissions"></a>Interroger les autorisations d’applications

### <a name="query-in-the-advanced-view"></a>Interroger dans la vue Avancée 
1. Dans la vue avancée, utilisez la zone de liste déroulante **Sélectionner un filtre** pour affiner votre recherche. Ajoutez des opérateurs (est égal à ou n’est pas égal à une valeur sélectionnée) pour terminer votre requête.
2. Cliquez sur l’icône **Ajouter un filtre** pour ajouter des filtres supplémentaires et affiner davantage votre requête. Les filtres sont appliqués automatiquement et la liste des applications est mise à jour en conséquence.
3. Cliquez sur l’icône **Supprimer un filtre** en regard d’un filtre pour le supprimer.
Les filtres suivants sont disponibles :
- Application Afficher la ou les applications tierces portant les noms sélectionnés auxquelles a été accordé l’accès à Office 365.

- Utilisateur Afficher les applications que ce ou ces utilisateurs ont autorisées.

- Autorisations Afficher les applications qui ont besoin des autorisations sélectionnées.

- État de l’application Afficher les applications en fonction de leur état (approuvé, exclu ou non défini).

- Niveau d’autorisation Afficher les applications en fonction du ou des niveaux d’autorisation sélectionnés.

- Utilisation communautaire Afficher les applications en fonction du niveau d’utilisation communautaire (rare, non courant, courant).

### <a name="query-in-the-basic-view"></a>Interrogation dans la vue de base 
Dans la vue de base, sélectionnez des valeurs dans une ou plusieurs listes déroulantes pour afficher les applications spécifiques. Vous pouvez sélectionner plusieurs valeurs dans les listes déroulantes. Vous pouvez utiliser les menus déroulants suivants pour l’interrogation : 
- Application Afficher la ou les applications tierces portant les noms sélectionnés auxquelles a été accordé l’accès à Office 365.

- Utilisateur Afficher les applications que ce ou ces utilisateurs ont autorisées.

- Autorisations Afficher les applications qui ont besoin des autorisations sélectionnées.

- État de l’application Afficher les applications en fonction de leur état (approuvé, exclu ou non défini).

- Niveau d’autorisation Afficher les applications en fonction du ou des niveaux d’autorisation sélectionnés.

- Utilisation communautaire Afficher les applications en fonction du niveau d’utilisation communautaire (rare, non courant, courant).
Les filtres sont appliqués automatiquement et la liste des applications est mise à jour en conséquence. 

## <a name="see-also"></a>Voir aussi  
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  