---
title: Contrôler les applications OAuth Cloud tierces obtenant des autorisations-Cloud App Security
description: Cet article fournit des informations sur la manière dont vous pouvez contrôler, bloquer et autoriser les applications OAuth tierces.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 08/05/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 0f6aebe10c147a6be1250ce5f15a208570947edc
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90879264"
---
# <a name="manage-oauth-apps"></a>Gérer les applications OAuth

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Les applications de productivité tierces installées par des utilisateurs professionnels dans votre organisation ont souvent besoin d’une autorisation pour pouvoir accéder aux informations et données utilisateur, et se connecter au nom de l’utilisateur à d’autres applications cloud, comme Office 365, G Suite et Salesforce. Lorsque les utilisateurs installent ces applications, ils cliquent souvent sur Accepter sans examiner attentivement les détails du message d’invite, notamment concernant l’octroi d’autorisations à l’application. Ce problème est d’autant plus complexe que le service informatique ne dispose pas toujours d’informations suffisantes pour mettre en balance le risque de sécurité d’une application et les avantages qu’elle offre en termes de productivité. Dans la mesure où l’acceptation des autorisations d’applications tierces représente un risque de sécurité potentiel pour votre organisation, la surveillance des autorisations d’applications accordées par vos utilisateurs, vous donne la visibilité et le contrôle nécessaires pour protéger vos utilisateurs et vos applications. Les autorisations d’applications Microsoft Cloud App Security vous permettent de savoir quelles applications OAuth installées par l’utilisateur ont accès aux données Office 365, G Suite et Salesforce. Cloud App Security vous indique de quelles autorisations les applications disposent, et quels utilisateurs ont accordé à ces applications l’accès à leurs comptes Office 365, G Suite et Salesforce. Avec les autorisations d’applications, vous décidez à quelles applications vous autorisez les utilisateurs à accéder, et quelles autres vous voulez exclure.

Pour plus d’informations sur l’examen des applications OAuth, consultez [examiner les applications OAuth risquées](investigate-risky-oauth.md).

> [!NOTE]
> Cloud App Security identifie uniquement les applications qui demandent des autorisations « déléguées ». Pour plus d’informations, consultez [autorisations des applications clientes](/azure/active-directory/develop/developer-glossary#permissions).

## <a name="working-with-the-oauth-apps-page"></a>Utilisation de la page Applications OAuth

La page **OAuth** affiche des informations sur les autorisations d’applications dans vos applications connectées.

Pour accéder à l’onglet OAuth

Dans le portail Cloud App Security, cliquez sur **Examiner**, puis sur **Applications OAuth**.

![autorisations d’applications](media/app-permissions.png)

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
|Serveur de publication|Nom du fournisseur qui fournit l’application.|Office 365|
|Dernière utilisation|Date la plus récente à laquelle cette application a été utilisée par une personne de votre organisation.|Salesforce|

## <a name="ban-or-approve-an-app"></a>Exclure ou approuver une application

1. Dans la page **Applications OAuth**, cliquez sur l’application pour ouvrir le **tiroir Application** et afficher plus d’informations sur l’application et les autorisations qui lui ont été accordées.

    - Cliquez sur **autorisations** pour afficher la liste complète des autorisations qui ont été accordées à l’application.
    - Dans la **communauté**, vous pouvez voir la façon dont l’application se trouve dans d’autres organisations.
    - Cliquez sur **activité associée** pour afficher les activités répertoriées dans le journal d’activité associé à cette application.

2. Pour exclure l’application, cliquez sur l’icône d’exclusion à l’extrémité de la ligne de l’application dans le tableau.

    ![icône d’exclusion de l’application](media/ban-app-icon.png)

    - Vous pouvez choisir de signaler aux utilisateurs que l’application qu’ils ont installée et autorisée a été interdite. La notification signale aux utilisateurs que l’application sera désactivée et qu’ils n’auront pas accès à l’application connectée. Si vous ne souhaitez pas les en informer, désélectionnez **Avertir les utilisateurs qui ont accordé l’accès à cette application interdite** dans la boîte de dialogue.
    - Nous vous recommandons d’avertir les utilisateurs que leur application est sur le point d’être exclue.

    ![exclure l’application](media/ban-app.png)

3. Tapez le message à envoyer aux utilisateurs de l’application dans la zone Entrez un message de notification personnalisé. Cliquez sur **Exclure l’application** pour envoyer l’e-mail et exclure l’application des utilisateurs de votre application connectée.

4. Pour approuver l’application, cliquez sur l’icône d’approbation à l’extrémité de la ligne dans le tableau.

    ![approuver l’application](media/approve-app.png)

    - L’icône prend la couleur verte et l’application est approuvée pour tous les utilisateurs de votre application connectée.
    - Quand vous marquez une application comme approuvée, il n’y a aucune incidence sur l’utilisateur final. Ce changement de couleur vous aide simplement à identifier les applications que vous avez approuvées, pour les distinguer de celles que vous n’avez pas encore vérifiées.

## <a name="revoke-app-and-notify-user"></a>Révoquer l’application et avertir l’utilisateur

Pour G Suite et Salesforce, vous pouvez révoquer l’autorisation d’une application ou avertir l’utilisateur qu’il doit la changer. Quand vous révoquez l’autorisation, elle supprime toutes les autorisations qui ont été accordées à l’application sous « applications d’entreprise » dans Azure AD.

1. Dans la page **Applications OAuth**, cliquez sur les points de suspension à la fin de la ligne de l’application et sélectionnez **Notifier l’utilisateur**. Par défaut, l’utilisateur est averti comme suit : *vous avez autorisé l’application à accéder à votre compte G suite. Cette application est en conflit avec la stratégie de sécurité de votre organisation. Réessayez d’attribuer ou de révoquer les autorisations que vous avez attribuées à cette application dans votre compte G suite. Pour révoquer l’accès aux applications, accédez à : https://security.google.com/settings/security/permissions?hl=en&pli=1  Sélectionnez l’application et cliquez sur « révoquer l’accès » dans la barre de menus de droite.* Vous pouvez personnaliser le message envoyé.
2. Vous pouvez également révoquer des autorisations d’utilisation de l’application pour l’utilisateur. Cliquez sur l’icône à la fin de la ligne de l’application dans le tableau et sélectionnez **Révoquer l’application**.

    ![révoquer l’application](media/revoke-app.png)

## <a name="query-oauth-apps"></a>Interroger des applications OAuth

Vous pouvez interroger des applications OAuth dans la vue **De base** ou la vue **Avancée**. Sélectionnez des valeurs dans une ou plusieurs listes déroulantes pour afficher les applications spécifiques dans la vue de base. Dans la vue avancée, utilisez la zone de liste déroulante **Sélectionner un filtre** pour affiner votre recherche. Ajoutez des opérateurs (est égal à ou n’est pas égal à une valeur sélectionnée) pour terminer votre requête.

- Choisissez l’icône **Ajouter un filtre** pour ajouter des filtres supplémentaires afin d’affiner davantage votre requête. Les filtres sont appliqués automatiquement et la liste des applications est mise à jour.

- Cliquez sur l’icône **Supprimer un filtre** en regard d’un filtre pour le supprimer.

## <a name="oauth-app-auditing"></a>Audit d’application OAuth

Cloud App Security audite toutes les activités d’autorisation OAuth, vous permettant ainsi de superviser et d’analyser les activités effectuées de manière approfondie. Vous pouvez également exporter les détails des utilisateurs qui ont autorisé une application OAuth spécifique, en fournissant des informations supplémentaires sur les utilisateurs, que vous pouvez ensuite utiliser pour une analyse plus poussée.

Pour exporter le journal, procédez comme suit :

1. Sur la page **applications OAuth** , sur la ligne où l’application correspondante s’affiche, sous **autorisé par**, cliquez sur le lien indiquant le nombre d’utilisateurs qui ont autorisé l’application.

1. Dans la fenêtre contextuelle, cliquez sur **Exporter**.

    ![Capture d’écran montrant l’exportation de l’audit d’application OAuth](media/oauth-export-users.png)

## <a name="send-feedback"></a>Envoyer des commentaires

Si une application OAuth détectée dans votre organisation semble malveillante, vous pouvez envoyer les commentaires de l’équipe Cloud App Security pour nous le faire savoir. Cette fonctionnalité vous permet de faire partie de notre communauté de sécurité et d’améliorer l’analyse et le score de risque de l’application OAuth.

1. Dans la page **Applications OAuth**, cliquez sur les points de suspension à la fin de la ligne de l’application et sélectionnez **Signaler l’application**.

    ![signaler l’application](media/report-app.png)
2. Dans l’écran **Signaler cette application**, vous pouvez choisir de signaler l’application comme étant malveillante ou de signaler tout autre problème lié à la façon dont Cloud App Security perçoit l’application. Par exemple, vous pourriez utiliser **Éditeur incorrect**, **Autorisations incorrectes** ou **Autre**. Les données que vous envoyez permettent de mettre à jour le score de risque de l’application et d’autres données analytiques sur l’application.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
