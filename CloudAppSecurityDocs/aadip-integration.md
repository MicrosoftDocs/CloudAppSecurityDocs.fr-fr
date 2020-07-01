---
title: Intégrer Azure Active Directory Identity Protection avec Cloud App Security
description: Cet article fournit des informations sur la façon de tirer parti des alertes de protection des identités dans Cloud App Security pour la détection hybride des risques.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 06/28/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 5af7efa448e7d93902e9d8845dd97479b7c53df7
ms.sourcegitcommit: b15034dd50142afd8e95de22a9232f711b1eae6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85624389"
---
# <a name="azure-active-directory-identity-protection-integration"></a>Intégration de Azure Active Directory Identity Protection

*S’applique à : Microsoft Cloud App Security*

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
> Lorsque l’intégration est désactivée, les alertes de protection des identités existantes sont conservées conformément aux stratégies de rétention de Cloud App Security.

## <a name="configure-identity-protection-policies"></a>Configurer des stratégies de protection des identités

Les stratégies de protection des identités peuvent être ajustées aux besoins de votre organisation en utilisant le curseur gravité. Le curseur sensibilité vous permet de contrôler les alertes qui sont ingérées. De cette façon, vous pouvez adapter la détection en fonction de vos besoins de couverture et de vos cibles (SNR).

Les stratégies suivantes sont disponibles :

|Policy|Description|État par défaut|Gravité par défaut|
|---|---|---|---|
|Informations d'identification divulguées|Affiche les alertes des informations d’identification divulguées, les informations d’identification valides de l’utilisateur ont été divulguées|activé|Faible-recevoir toutes les alertes|
|Connexion risquée|Agrège plusieurs détections de connexion risquée, les connexions qui n’ont pas été effectuées par l’utilisateur|activé|Alertes haute réception uniquement de gravité élevée|

## <a name="remediating-risky-users"></a>Correction des utilisateurs à risque

Les stratégies de protection des identités peuvent être utilisées pour corriger automatiquement les utilisateurs risqués en définissant le niveau de risque de l’utilisateur sur élevé. Une fois qu’un utilisateur est défini sur élevé, l’algorithme d’analyse des risques de l’utilisateur avancé prend en compte le nouvel état de l’utilisateur, ainsi que l’état de *gestion des périphériques* de l’ordinateur. Cela entraîne l’application des actions de stratégie appropriées définies dans Azure AD, telles que la réinitialisation du mot de passe de l’utilisateur, la demande d’authentification MFA ou la force de l’utilisateur à utiliser un appareil géré. Pour plus d’informations, consultez [comment Azure ad utiliser mes](https://docs.microsoft.com/azure/active-directory/identity-protection/howto-identity-protection-risk-feedback#how-does-azure-ad-use-my-risk-feedback) actions de commentaires et de [gouvernance](accounts.md#governance-actions).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
