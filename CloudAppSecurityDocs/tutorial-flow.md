---
title: Étendre la gouvernance à la correction des points de terminaison
description: Ce tutoriel décrit le processus de configuration des alertes de stratégie Microsoft Cloud App Security pour déclencher des workflows Microsoft Power Automate en vue d’exécuter des actions correctives Microsoft Defender Advanced Threat Protection.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: tutorial
ms.date: 04/27/2020
ms.openlocfilehash: 2f06ed5a9eb5b029367b1ff05231b5a35fcc6d19
ms.sourcegitcommit: b15034dd50142afd8e95de22a9232f711b1eae6e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85625008"
---
# <a name="tutorial-extend-governance-to-endpoint-remediation"></a>Tutoriel : Étendre la gouvernance à la correction des points de terminaison

Cloud App Security fournit des options de gouvernance prédéfinies pour les stratégies. Il permet notamment de suspendre un utilisateur ou de rendre un fichier privé. À l’aide de l’intégration native à Microsoft Power Automate, vous pouvez utiliser un large écosystème de connecteurs SaaS pour générer des workflows en vue d’automatiser les processus, dont la correction.

Par exemple, lors de la détection d’une menace de programme malveillant possible, vous pouvez utiliser des workflows pour lancer des actions correctives Microsoft Defender Advanced Threat Protection (ATP), telles que l’exécution d’une analyse antivirus ou l’isolement d’un point de terminaison.

Dans ce tutoriel, vous allez apprendre à configurer une action de gouvernance de stratégie pour utiliser un workflow afin d’exécuter une analyse antivirus sur un point de terminaison où un utilisateur montre des signes de comportement suspect.

> [!div class="checklist"]
>
> * 1 : [Générer un jeton d’API Cloud App Security](#generate-token)
> * 2 : [Créer un flux pour exécuter une analyse antivirus](#create-flow)
> * 3 : [Configurer le flux](#configure-flow)
> * 4 : [Configurer une stratégie pour exécuter le flux](#configure-policy)

> [!NOTE]
> Ces workflows sont pertinents seulement pour les stratégies qui contiennent l’activité de l’utilisateur. Par exemple, vous ne pouvez pas utiliser ces workflows avec des stratégies de découverte ou OAuth.

Si vous n’avez pas de plan Power Automate, [inscrivez-vous pour obtenir un compte d’essai gratuit](https://flow.microsoft.com/pricing).

## <a name="prerequisites"></a>Prérequis

* Vous devez disposer d’un [plan Microsoft Power Automate](https://flow.microsoft.com/pricing) valide.
* Vous devez avoir un plan Microsoft Defender ATP valide
* L’environnement Power Automate doit être synchronisé avec Azure AD, supervisé par Defender ATP et joint au domaine.

## <a name="phase-1-generate-a-cloud-app-security-api-token"></a>Phase 1 : Générer un jeton d’API Cloud App Security<a name="generate-token"></a>

> [!NOTE]
> Si vous avez déjà créé un workflow en utilisant un connecteur Cloud App Security, Power Automate réutilisera automatiquement le jeton. Vous pouvez donc ignorer cette étape.

1. Dans Cloud App Security, dans la barre de menus, cliquez sur la roue dentée des paramètres ![Icône des paramètres](media/settings-icon.png "Icône des paramètres") et sélectionnez **Extensions de sécurité**.

1. Dans la page **Extensions de sécurité**, cliquez sur le bouton plus (+) pour générer un nouveau jeton d’API.
1. Dans la fenêtre contextuelle **Générer un nouveau jeton**, entrez le nom du jeton (par exemple « Flow-Token »), puis cliquez sur **Générer**.

    ![Capture d’écran de la fenêtre de jeton, montrant l’entrée du nom et le bouton Générer.](media/tutorial-flow-token-generate.png)
1. Une fois le jeton généré, cliquez sur l’icône de copie à droite du jeton généré, puis cliquez sur **Fermer**. Vous aurez besoin du jeton ultérieurement.

    ![Capture d’écran de la fenêtre de jeton, montrant le jeton et le processus de copie.](media/tutorial-flow-token-copy.png)

## <a name="phase-2-create-a-flow-to-run-an-antivirus-scan"></a>Phase 2 : Créer un flux pour exécuter une analyse antivirus<a name="create-flow"></a>

> [!NOTE]
> Si vous avez déjà créé un flux en utilisant un connecteur Defender ATP, Power Automate réutilisera automatiquement le connecteur. Vous pouvez donc ignorer l’étape de **connexion**.

1. Accédez au [portail Power Automate](https://flow.microsoft.com/), puis sélectionnez **Modèles**.

    ![Capture d’écran de la page principale de Power Automate, montrant la sélection de modèles.](media/tutorial-flow-templates.png)

1. Recherchez « Cloud App Security » et sélectionnez **Exécuter l’analyse antivirus avec Windows Defender sur une alerte Cloud App Security**.

    ![Capture d’écran de la page de modèles de Power Automate, montrant les résultats de la recherche.](media/tutorial-flow-templates-search.png)

1. Dans la liste des applications, sur la ligne où figure **Connecteur Microsoft Defender ATP**, cliquez sur **Se connecter**.

    ![Capture d’écran de la page de modèles de Power Automate, montrant le processus de connexion.](media/tutorial-flow-templates-signin.png)

## <a name="phase-3-configure-the-flow"></a>Phase 3 : Configurer le flux<a name="configure-flow"></a>

> [!NOTE]
> Si vous avez déjà créé un flux en utilisant un connecteur Azure AD, Power Automate réutilisera automatiquement le jeton. Vous pouvez donc ignorer cette étape.

1. Dans la liste des applications, sur la ligne où figure **Cloud App Security**, cliquez sur **Créer**.

    ![Capture d’écran de la page de modèles de Power Automate, montrant le bouton Créer pour Cloud App Security.](media/tutorial-flow-templates-create.png)

1. Dans la fenêtre contextuelle **Cloud App Security**, entrez le nom de la connexion (par exemple « Cloud App Security Token »), collez le jeton d’API que vous avez copié ,puis cliquez sur **Créer**.

    ![Capture d’écran de la fenêtre Cloud App Security, montrant l’entrée du nom et de la clé, et le bouton Créer.](media/tutorial-flow-templates-create-window.png)

1. Dans la liste des applications, sur la ligne où figure **HTTP avec Azure AD**, cliquez sur **Se connecter**.

1. Dans la fenêtre contextuelle **HTTP avec Azure AD**, pour les deux champs **URL de ressource de base** et **URI de la ressource Azure AD**, entrez `https://graph.microsoft.com`, puis cliquez sur **Se connecter** et entrez les informations d’identification d’administrateur que vous voulez utiliser avec le connecteur HTTP avec Azure AD.

    ![Capture d’écran de la fenêtre HTTP avec Azure AD, montrant les champs des ressources et le bouton de connexion.](media/tutorial-flow-templates-azure.png)

1. Cliquez sur **Continuer**.

    ![Capture d’écran de la fenêtre des modèles Power Automate, montrant les actions effectuées et le bouton Continuer.](media/tutorial-flow-templates-continue.png)

1. Une fois que tous les connecteurs sont connectés, dans la page du flux, sous **Appliquer à chaque machine**, vous pouvez si vous le souhaitez modifier le commentaire et le type d’analyse, puis cliquer sur **Enregistrer**.

    ![Capture d’écran de la page du flux, montrant la section des paramètres d’analyse.](media/tutorial-flow-templates-scan.png)

## <a name="phase-4-configure-a-policy-to-run-the-flow"></a>Phase 4 : Configurer une stratégie pour exécuter le flux<a name="configure-policy"></a>

1. Dans Cloud App Security, cliquez sur **Contrôle**, puis sur **Stratégies**.

1. Dans la liste des stratégies, sur la ligne où la stratégie appropriée s’affiche, choisissez les trois points à la fin de la ligne, puis **Modifier la stratégie**.

1. Sous **Alertes**, sélectionnez **Envoyer des alertes à Flow**, puis **Exécuter l’analyse antivirus avec Windows Defender sur une alerte Cloud App Security**.

    ![Capture d’écran de la page de stratégie, montrant la section des paramètres des alertes.](media/tutorial-flow-templates-alerts.png)

Désormais, toutes les alertes déclenchées pour cette stratégie lancent le flux permettant d’exécuter l’analyse antivirus.

Vous pouvez utiliser les étapes de ce tutoriel pour créer un large éventail d’actions basées sur les workflows afin d’étendre les fonctions correctives Cloud App Security, notamment d’autres actions Defender ATP. Pour afficher la liste des workflows Cloud App Security prédéfinis, dans Power Automate, [recherchez « Cloud App Security »](https://go.microsoft.com/fwlink/?linkid=2102574).

## <a name="see-also"></a>Voir aussi

> [!div class="nextstepaction"]
> [Intégration à Power Automate pour l’automatisation des alertes personnalisées](flow-integration.md)
