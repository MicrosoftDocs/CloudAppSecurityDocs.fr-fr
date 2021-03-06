---
title: Intégrer Azure Active Directory Identity Protection avec Cloud App Security
description: Cet article fournit des informations sur la façon de tirer parti des alertes de protection des identités dans Cloud App Security pour la détection hybride des risques.
ms.date: 12/27/2020
ms.topic: how-to
ms.openlocfilehash: f71e73dfd3ca8be7d6ed5e03847ac6e11e290818
ms.sourcegitcommit: 4900168878f42e9fa79873df4b7c2d81991b5b27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97857952"
---
# <a name="azure-active-directory-identity-protection-integration"></a>Intégration de Azure Active Directory Identity Protection

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Microsoft Cloud App Security s’intègre à Azure Active Directory Identity Protection (identity protection) pour fournir une analytique UEBA (Behavior-action Analytics) d’entité utilisateur dans un environnement hybride. Pour plus d’informations sur les Machine Learning et l’analyse comportementale fournis par Identity Protection, consultez [qu’est-ce qu’Identity Protection ?](/azure/active-directory/identity-protection/overview-identity-protection).

## <a name="prerequisites"></a>Prérequis

- Un compte d’administrateur Cloud App Security pour permettre l’intégration entre la protection des identités et les Cloud App Security.

## <a name="enable-identity-protection"></a>Activer Identity Protection

> [!NOTE]
> La fonctionnalité de protection d’identité est activée par défaut. Toutefois, si la fonctionnalité a été désactivée, vous pouvez utiliser ces étapes pour l’activer.

Pour activer l’intégration de Cloud App Security avec Identity Protection :

1. Dans Cloud App Security, sous l’roue dentée paramètres, sélectionnez **paramètres**.

    ![menu Paramètres](media/azip-system-settings.png)

1. Sous **protection contre les menaces**, sélectionnez **Azure ad Identity Protection**.

    ![activer Azure-protection avancée contre les menaces](media/aadip-integration.png)

1. Sélectionnez **activer Azure ad Identity Protection l’intégration des alertes** , puis cliquez sur **Enregistrer**.

Après l’activation de l’intégration de la protection des identités, vous pouvez afficher les alertes de tous les utilisateurs de votre organisation.

## <a name="disable-identity-protection"></a>Désactiver Identity Protection

Pour désactiver l’intégration de Cloud App Security avec Identity Protection :

1. Dans Cloud App Security, sous l’roue dentée paramètres, sélectionnez **paramètres**.

1. Sous **protection contre les menaces**, sélectionnez **Azure ad Identity Protection**.

1. Désactivez la case à **coAzure AD Identity Protection activer l’intégration des alertes** , puis cliquez sur **Enregistrer**.

> [!NOTE]
>
> - Lorsque l’intégration est désactivée, les alertes de protection des identités existantes sont conservées conformément aux stratégies de rétention de Cloud App Security.
> - Étant donné que Cloud App Security consomme uniquement des connexions interactives à partir de Azure AD, certaines alertes risquent de ne pas afficher les activités associées. Vous pouvez examiner ces activités dans le portail Azure AD.

## <a name="configure-identity-protection-policies"></a>Configurer des stratégies de protection des identités

Les stratégies de protection des identités peuvent être ajustées aux besoins de votre organisation en utilisant le curseur gravité. Le curseur sensibilité vous permet de contrôler les alertes qui sont ingérées. De cette façon, vous pouvez adapter la détection en fonction de vos besoins de couverture et de vos cibles (SNR).

Les stratégies suivantes sont disponibles :

|Stratégie|Description|État par défaut|Gravité par défaut|
|---|---|---|---|
|Informations d'identification divulguées|Affiche les alertes des informations d’identification divulguées, les informations d’identification valides de l’utilisateur ont été divulguées|activé|Faible-recevoir toutes les alertes|
|Connexion risquée|Agrège plusieurs détections de connexion risquée, les connexions qui n’ont pas été effectuées par l’utilisateur|activé|Alertes haute réception uniquement de gravité élevée|

> [!NOTE]
> Cloud App Security n’envoie pas de notifications par courrier électronique pour les alertes de protection d’identité. Toutefois, vous pouvez configurer des notifications par courrier électronique pour eux dans le portail identity protection.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
