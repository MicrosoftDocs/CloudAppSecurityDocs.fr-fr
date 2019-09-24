---
title: Examiner des applications OAuth à risque – Cloud App Security | Microsoft Docs
description: Cet article fournit des informations sur la façon d’examiner des applications OAuth à risque dans Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 9/1/2019
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: adb9c8cceaab8158c194256ccd1e5cb0ecbaaa8a
ms.sourcegitcommit: 8a49c166424fea83853b0a6895212367526abe78
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71084354"
---
# <a name="tutorial-investigate-risky-oauth-apps"></a>Didacticiel : Examiner des applications OAuth à risque

*S’applique à : Microsoft Cloud App Security*

OAuth est un standard ouvert pour l’authentification basée sur un jeton et sur une autorisation. OAuth permet à des services tiers d’utiliser les informations de compte d’un utilisateur sans exposer le mot de passe d’utilisateur. OAuth fait Office d’intermédiaire pour le compte de l’utilisateur et fournit le service avec un jeton d’accès qui autorise le partage d’informations de compte spécifiques.

Par exemple, une application qui analyse le calendrier de l’utilisateur et lui donne des conseils sur la façon de devenir plus productif a besoin d’accéder au calendrier de l’utilisateur. Au lieu de fournir les informations d’identification de l’utilisateur, OAuth permet à l’application d’obtenir l’accès aux données avec uniquement un jeton, qui est généré lorsque l’utilisateur fournit son consentement sur une page, comme illustré dans l’image ci-dessous.

 ![Autorisation d’application OAuth](./media/oauth-permission.png)

Les applications tierces installées par des utilisateurs professionnels dans votre organisation ont souvent besoin d’une autorisation pour pouvoir accéder aux informations et données utilisateur et se connecter au nom de l’utilisateur à d’autres applications cloud. Lorsque les utilisateurs installent ces applications, ils cliquent souvent sur **Accepter** sans examiner attentivement les détails du message d’invite, notamment concernant l’octroi d’autorisations à l’application. Le fait d’accepter les autorisations d’applications tierces est un risque de sécurité potentiel pour votre organisation.

Par exemple, la page de consentement d’application OAuth suivante peut paraître légitime à l’utilisateur moyen, toutefois, « l’Explorateur d’API Google » ne devrait pas avoir besoin de demander des autorisations à Google. Par conséquent, cela indique que l’application peut être une tentative de hameçonnage, non liée à Google.

![Hameçonnage OAuth](./media/oauth-phishing.png)

En tant qu’administrateur de sécurité, vous avez besoin d’une visibilité et de contrôle sur les applications dans votre environnement et cela inclut leurs autorisations. Vous devez être en mesure d’empêcher l’utilisation d’applications qui demandent l’autorisation à des ressources que vous voulez révoquer. Par conséquent, Microsoft Cloud App Security vous offre la possibilité d’analyser et de surveiller les autorisations données à l’application par vos utilisateurs. Cet article vise à aider à examiner les applications OAuth dans votre organisation et à vous concentrer sur les applications plus susceptibles d’être suspectes.

Il est recommandé d’examiner les applications en utilisant les capacités et les informations fournies dans le portail Cloud App Security pour éliminer par filtrage les applications présentant un faible risque et de vous concentrer sur les applications suspectes.

## <a name="how-to-detect-risky-oauth-apps"></a>Comment détecter les applications OAuth à risque

La détection d’une application OAuth à risque peut se faire avec :

- **Alertes** : Réagissez à une alerte déclenchée par une stratégie existante.
- **Recherche** : Recherche d’une application à risque parmi toutes les applications disponibles, sans réelle suspicion de risque.

### <a name="detect-risky-apps-using-alerts"></a>Détecter des applications à risque à l’aide des alertes

Vous pouvez définir des stratégies pour vous envoyer automatiquement des notifications lorsqu’une application OAuth correspond à certains critères. Par exemple, vous pouvez définir une stratégie pour vous avertir automatiquement lorsqu’une application, demandant des autorisations élevées et qui a été autorisée par plus de 50 utilisateurs, est détectée. Pour plus d’informations sur la création de stratégies OAuth, consultez [Stratégies d’application OAuth](app-permission-policy.md).

### <a name="detect-risky-apps-by-hunting"></a>Détecter des applications à risque à l’aide de la recherche

1. Dans le portail, accédez à **Investigate**, puis **Applications OAuth**. Utilisez les filtres et les requêtes pour passer en revue ce qui se passe dans votre environnement :

    - Définissez le filtre sur **Niveau d’autorisation de gravité élevée** et **Utilisation communautaire pas courante**. Ce filtre vous aide à vous concentrer sur les applications à risque potentiel très élevé pour lesquelles les utilisateurs peuvent avoir sous-estimé le risque.
    - Sous **Autorisations** sélectionnez toutes les options qui sont particulièrement risquées dans un contexte spécifique. Par exemple, vous pouvez sélectionner tous les filtres qui donnent l’autorisation d’accès aux e-mails, comme **Accès complet à toutes les boîtes aux lettres** puis passez en revue la liste des applications pour vous assurer qu’elles ont toutes besoin d’un accès relatif à la messagerie. Cela peut faciliter l’investigation dans un contexte spécifique et la recherche d’applications qui semblent légitimes, mais contiennent des autorisations inutiles. Ces applications sont plus susceptibles de présenter des risques.

            ![OAuth phishing](./media/oauth-filters.png)

    - Sélectionnez la requête enregistrée **Applications autorisées par des utilisateurs externes**. Ce filtre vous aide à identifier les applications qui peuvent ne pas être conformes aux normes de sécurité de votre entreprise.
1. Après les avoir examinées, vous pouvez vous concentrer sur les applications dans les requêtes qui semblent légitimes, mais peuvent en réalité présenter des risques. Utilisez les filtres pour les rechercher :
    - Filtres pour les applications qui sont **Autorisées par un petit nombre d’utilisateurs**. Si vous vous concentrez sur ces applications, vous pouvez rechercher les applications à risque qui ont été autorisées par un utilisateur compromis.
    - Applications avec des autorisations qui ne répondent pas à l’objectif de l’application, par exemple une application d’horloge avec un accès complet à toutes les boîtes aux lettres.
1. Cliquez sur chaque application pour ouvrir le tiroir des applications et vérifier si l’application a un nom, un éditeur ou un site web suspect.
1. Examinez la liste des applications et ciblez celles qui ont une date sous **Dernière autorisation** qui n’est pas récente. Ces applications peuvent ne plus être nécessaires.

    ![Tiroir d’application OAuth](./media/oauth-drawer.png)

## <a name="how-to-investigate"></a>Procédure d’examen

Après avoir déterminé qu’une application est suspecte et que vous souhaitez l’examiner, nous vous recommandons les principes clés suivants pour une investigation efficace :

- Plus une application est courante et utilisée, par votre organisation ou en ligne, plus elle est probablement sécurisée.
- Une application ne doit exiger que les autorisations qui sont liées à son objectif. Si tel n’est pas le cas, l’application peut être risquée.
- Les applications qui demandent des privilèges élevés ou le consentement de l’administrateur sont plus susceptibles de s’avérer dangereuses.

1. Cliquez sur l’application pour ouvrir le tiroir des applications et sur le lien situé sous **Activités associées**. Cette opération ouvre la page Journal d’activité, filtrée pour les activités effectuées par l’application. N’oubliez pas que certaines applications effectuent des activités qui sont inscrites comme ayant été effectuées par un utilisateur. Ces activités sont automatiquement filtrées dans les résultats dans le journal d’activité. Pour une investigation poussée avec le journal d’activité, consultez [Journal d’activité](activity-filters.md).
1. Si une application semble suspecte, nous vous recommandons d’examiner son nom et son éditeur dans les différents App Stores. Concentrez-vous sur les applications suivantes, qui peuvent être suspectes :
    - Applications avec un faible nombre de téléchargements.
    - Applications avec une évaluation médiocre, un faible score ou des commentaires négatifs.
    - Applications avec un éditeur ou un site web suspect.
    - Applications avec une date de dernière mise à jour ancienne. Cela peut indiquer une application qui n’est plus prise en charge.
    - Applications avec des autorisations sans intérêt. Cela peut indiquer qu’une application est à risque.
1. Si l’application est toujours suspecte, vous pouvez rechercher son nom, son éditeur et son URL en ligne.
1. Vous pouvez exporter l’audit d’application OAuth pour approfondir l’analyse des utilisateurs qui ont autorisé une application. Pour plus d’informations, consultez [Audit d’application OAuth](manage-app-permissions.md#oauth-app-auditing).

## <a name="how-to-remediate"></a>Comment corriger

Après avoir déterminé qu’une application OAuth est risquée, Cloud App Security fournit les options de correction suivantes :

- **Correction manuelle** : Vous pouvez facilement [interdire ou révoquer une application à partir de la page des applications OAuth](manage-app-permissions.md#ban-or-approve-an-app)

- **Correction automatique** : Vous pouvez créer une stratégie qui [révoque automatiquement une application ou qui révoque un utilisateur spécifique d’une application](app-permission-policy.md).

## <a name="next-steps"></a>Étapes suivantes

[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)
