---
title: Contrôler les applications OAuth Cloud tierces obtenant des autorisations-Cloud App Security | Microsoft Docs
description: Cet article fournit des informations sur la façon dont vous pouvez contrôler, interdire et autoriser des applications OAuth tierces.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 9/1/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 37b4f17539b0d160e8650f5478741f0941e50648
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285283"
---
# <a name="manage-oauth-apps"></a>Gérer les applications OAuth

*S’applique à : Microsoft Cloud App Security*

De nombreuses applications de productivité tierces qui peuvent être installées par les utilisateurs de votre organisation demandent l’autorisation d’accéder aux informations et données utilisateur et de se connecter au nom de l’utilisateur dans d’autres applications Cloud, comme Office 365, G suite et Salesforce. Quand les utilisateurs installent ces applications, ils cliquent souvent sur accepter sans examiner attentivement les détails dans l’invite, y compris l’octroi d’autorisations à l’application. Ce problème est aggravé par le fait qu’il n’a peut-être pas suffisamment d’indications pour peser le risque de sécurité d’une application par rapport aux avantages de productivité qu’elle offre. Étant donné que l’acceptation des autorisations d’applications tierces constitue un risque potentiel pour la sécurité de votre organisation, la surveillance des autorisations de l’application que vos utilisateurs octroient vous donne la visibilité et le contrôle nécessaires pour protéger vos utilisateurs et vos applications. Les autorisations de l’application Microsoft Cloud App Security vous permettent de voir quelles applications OAuth installées par l’utilisateur ont accès aux données Office 365, aux données G suite et aux données Salesforce. Cloud App Security indique les autorisations dont disposent les applications et les utilisateurs qui ont accordé à ces applications l’accès à leurs comptes Office 365, G suite et Salesforce. Les autorisations d’application vous permettent de décider quelles applications vous autorisez à accéder à vos utilisateurs et celles que vous souhaitez interdire.

Pour plus d’informations sur l’examen des applications OAuth, consultez [examiner les applications OAuth risquées](investigate-risky-oauth.md).

## <a name="working-with-the-oauth-apps-page"></a>Utilisation de la page applications OAuth

La page **OAuth** affiche des informations sur les autorisations d’application dans vos applications connectées.

Pour accéder à l’onglet OAuth :

Dans le portail Cloud App Security, cliquez sur **examiner**, puis sur **applications OAuth**.

![autorisations de l’application](media/app-permissions.png)

La page applications OAuth fournit les informations suivantes sur chaque application OAuth à laquelle des autorisations ont été accordées :

|Élément|Signification|Application|
|-------|-------|-------|
|Icône de base dans la barre de requête de l’application  |Basculez vers la requête dans la vue de base.|Office 365, G suite, Salesforce|
|Icône avancé dans la barre de requête de l’application  |Basculez vers la requête dans la vue avancée.|Office 365, G suite, Salesforce|
|Icône ouvrir ou fermer tous les détails dans la liste des applications  |Affichez plus ou moins de détails sur chaque application.|
|Icône d’exportation dans la liste des applications  |Exportez un fichier CSV qui contient une liste d’applications, le nombre d’utilisateurs pour chaque application, les autorisations associées à l’application, le niveau d’autorisation, l’état de l’application et le niveau d’utilisation de la communauté.|Office 365, G suite, Salesforce|
|Application|Nom de l’application. Sélectionnez le nom pour afficher plus d’informations, y compris la description, l’éditeur (pour Office 365), le site Web de l’application et l’ID.|Office 365, G suite, Salesforce|
|Autorisé par|Nombre d’utilisateurs ayant autorisé cette application à accéder au compte de son application et ayant accordé les autorisations d’application. Sélectionnez le nombre pour afficher plus d’informations, notamment une liste des e-mails utilisateur et si un administrateur a accepté l’application précédemment.|Office 365, G suite, Salesforce|
|Niveau d’autorisation  |L’icône et le texte du niveau d’autorisation indiquent la valeur haute, moyenne ou faible. Le niveau indique le degré d’accès de cette application aux données de l’application. Par exemple, Low peut indiquer que l’application accède uniquement au profil utilisateur et au nom. Sélectionnez le niveau pour afficher plus d’informations, y compris les autorisations accordées à l’application, à l’utilisation de la communauté ou à l’activité associée dans le [Journal de gouvernance](governance-actions.md).|Office 365, G suite|
|État de l’application|Un administrateur peut marquer une application comme approuvée, interdite ou laissée comme non déterminée.|Office 365, G suite, Salesforce|
|Utilisation de la communauté|Montre le degré de popularité de l’application pour l’ensemble de vos utilisateurs (commun, rare, rare)|Office 365, G suite, Salesforce|
|Dernière autorisation|Date la plus récente à laquelle un utilisateur a accordé des autorisations à cette application.|Office 365, Salesforce|
|Éditeur|Nom du fournisseur qui fournit l’application.|Office 365|
|Dernière utilisation|Date la plus récente à laquelle cette application a été utilisée par toute personne de votre organisation.|Salesforce|

## <a name="ban-or-approve-an-app"></a>Interdire ou approuver une application

1. Dans la page **applications OAuth** , cliquez sur l’application pour ouvrir le **tiroir d’application** et afficher plus d’informations sur l’application et les autorisations qui lui ont été accordées.

    - Cliquez sur le lien **autorisations** pour afficher la liste complète des autorisations qui ont été accordées à l’application.
    - Dans la **communauté**, vous pouvez voir la façon dont l’application se trouve dans d’autres organisations.
    - Cliquez sur le lien **activité associée** pour afficher les activités répertoriées dans le journal de gouvernance relatives à cette application.

2. Pour interdire l’application, cliquez sur l’icône d’interdiction à la fin de la ligne de l’application dans le tableau.

    ![icône d’interdiction d’application](media/ban-app-icon.png)

    - Vous pouvez choisir si vous souhaitez informer les utilisateurs que l’application qu’ils ont installée et autorisée a été exclue. La notification permet aux utilisateurs de savoir que l’application est désactivée et qu’ils n’ont pas accès à l’application connectée. Si vous ne souhaitez pas qu’ils le sachent, désélectionnez **notifier les utilisateurs qui ont accordé l’accès à cette application interdite** dans la boîte de dialogue.
    - Il est recommandé que les utilisateurs de l’application sachent que leur application doit être exclue de l’utilisation.

    ![bloquer l’application](media/ban-app.png)

3. Tapez le message que vous voulez envoyer aux utilisateurs de l’application dans la zone Entrez un message de notification personnalisé. Cliquez sur **Bun App** pour envoyer le courrier et exclure l’application des utilisateurs de votre application connectée.

4. Pour approuver l’application, cliquez sur l’icône approuver à la fin de la ligne dans la table.

    ![approuver l’application](media/approve-app.png)

    - L’icône devient verte et l’application est approuvée pour tous les utilisateurs de votre application connectée.
    - Lorsque vous marquez une application comme approuvée, il n’y a aucun effet sur l’utilisateur final. Ce changement de couleur est destiné à vous aider à voir les applications que vous avez approuvées pour les séparer de celles que vous n’avez pas encore revues.

## <a name="revoke-app-and-notify-user"></a>Révoquer l’application et avertir l’utilisateur

Pour G suite et Salesforce, il est possible de révoquer l’autorisation sur une application ou d’informer l’utilisateur qu’il doit modifier l’autorisation. Quand vous révoquez l’autorisation, elle supprime toutes les autorisations qui ont été accordées à l’application sous « applications d’entreprise » dans Azure AD.

1. Dans la page **applications OAuth** , cliquez sur trois points à la fin de la ligne de l’application, puis sélectionnez **notifier l’utilisateur**. Par défaut, l’utilisateur est averti comme suit : *vous avez autorisé l’application à accéder à votre compte G suite. Cette application est en conflit avec la stratégie de sécurité de votre organisation. Réessayez d’attribuer ou de révoquer les autorisations que vous avez attribuées à cette application dans votre compte G suite. Pour révoquer l’accès à l’application, accédez à : https://security.google.com/settings/security/permissions?hl=en&pli=1 sélectionnez l’application et cliquez sur « révoquer l’accès » dans la barre de menus de droite.* Vous pouvez personnaliser le message envoyé.
2. Vous pouvez également révoquer les autorisations pour utiliser l’application pour l’utilisateur. Cliquez sur l’icône à la fin de la ligne de l’application dans le tableau et sélectionnez **révoquer l’application**.

    ![révoquer l’application](media/revoke-app.png)

## <a name="query-oauth-apps"></a>Interroger des applications OAuth

Vous pouvez interroger des applications OAuth en mode de **base** ou **avancé** . Sélectionnez des valeurs dans une ou plusieurs listes déroulantes pour afficher les applications spécifiques dans la vue de base. Dans la vue avancée, utilisez la liste déroulante **Sélectionner un filtre** pour affiner votre recherche. Ajoutez des opérateurs, est égal à ou n’est pas égal à une valeur sélectionnée pour terminer votre requête.

- Choisissez l’icône **Ajouter un filtre** pour ajouter des filtres supplémentaires afin d’affiner davantage votre requête. Les filtres sont appliqués automatiquement et la liste des applications est mise à jour.

- Choisissez l’icône **supprimer un filtre** en regard du filtre pour supprimer les filtres.

## <a name="oauth-app-auditing"></a>Audit d’application OAuth

Cloud App Security audite toutes les activités d’autorisation OAuth, vous permettant ainsi de superviser et d’analyser les activités effectuées de manière approfondie. Vous pouvez également exporter les détails des utilisateurs qui ont autorisé une application OAuth spécifique, en fournissant des informations supplémentaires sur les utilisateurs, que vous pouvez ensuite utiliser pour une analyse plus poussée.

Pour exporter le journal, procédez comme suit :

1. Sur la page **applications OAuth** , sur la ligne où l’application correspondante s’affiche, sous **autorisé par**, cliquez sur le lien indiquant le nombre d’utilisateurs qui ont autorisé l’application.

1. Dans la fenêtre contextuelle, cliquez sur **Exporter**.

    ![Capture d’écran montrant l’exportation de l’audit d’application OAuth](media/oauth-export-users.png)

## <a name="send-feedback"></a>Envoyer des commentaires

Si une application OAuth détectée dans votre organisation semble malveillante, vous pouvez envoyer les commentaires de l’équipe Cloud App Security pour nous le faire savoir. Cette fonctionnalité vous permet de faire partie de notre communauté de sécurité et d’améliorer l’analyse et le score de risque des applications OAuth.

1. Dans la page **applications OAuth** , cliquez sur trois points à la fin de la ligne de l’application et sélectionnez **application de rapport**.

    ![application de rapport](media/report-app.png)
2. Dans l’écran **signaler cette application** , vous pouvez choisir de signaler l’application comme malveillante ou de signaler un autre problème lié à la façon dont Cloud App Security perçoit l’application. Par exemple, vous pouvez utiliser un **éditeur incorrect**, des **autorisations incorrectes**ou d' **autres types**. Les données que vous envoyez seront utilisées pour mettre à jour le score de risque de l’application et d’autres analyses sur l’application.

## <a name="next-steps"></a>Étapes suivantes :

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
