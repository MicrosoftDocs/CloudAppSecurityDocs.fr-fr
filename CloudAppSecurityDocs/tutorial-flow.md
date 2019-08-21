---
title: Automatiser les alertes pour protéger les points de terminaison | Microsoft Docs
description: Ce tutoriel le processus de configuration des alertes Microsoft Cloud App Security pour utiliser Microsoft Flow pour exécuter des actions Microsoft Defender.
author: ShlomoSagir-MS
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: tutorial
ms.date: 8/15/2019
ms.openlocfilehash: bfec590f92172773bf263dbb5b84832329c63488
ms.sourcegitcommit: 12dfc4c0b8d72aad8cfae9c70f0014ca312b9e4e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037423"
---
# <a name="tutorial-automate-alerts-to-protect-endpoints"></a>Tutoriel : Automatiser les alertes pour protéger les points de terminaison

Seul, Cloud App Security fournit des options de gouvernance prédéfinies. Il permet notamment de suspendre un utilisateur ou de rendre un fichier privé lors de la définition de stratégies. En créant un playbook dans Microsoft Flow avec le connecteur Cloud App Security, vous pouvez créer des workflows permettant des actions de point de terminaison personnalisées pour vos stratégies avec Microsoft Defender Advanced Threat Protection (ATP). Une fois le playbook créé dans Flow, il vous suffit de l’associer à une stratégie dans Cloud App Security pour envoyer des alertes à Flow. Microsoft Flow propose plusieurs connecteurs et conditions pour créer un workflow personnalisé pour votre organisation.

Le [connecteur Cloud App Security](https://docs.microsoft.com/connectors/cloudappsecurity/) dans Flow prend en charge les actions et les déclencheurs automatisés. Flow est déclenché automatiquement quand Cloud App Security génère une alerte. Les actions incluent le changement de l’état de l’alerte dans Cloud App Security.

Dans ce tutoriel, vous découvrez comment automatiser les alertes pour :

> [!div class="checklist"]
> * Exécuter une analyse antivirus en utilisant Microsoft Defender ATP
> * Isoler une machine en utilisant Microsoft Defender ATP

Dans le cadre de ce didacticiel, la procédure décrit comment automatiser les alertes pour exécuter une analyse antivirus avec Microsoft Defender ATP. Pour automatiser les alertes afin d’isoler une machine, suivez les mêmes étapes en remplaçant le flux « antivirus » par le flux « isolation ».

> [!NOTE]
> Ces flux sont pertinents seulement pour les stratégies qui contiennent l’activité de l’utilisateur. Par exemple, vous ne pouvez pas utiliser ces flux avec des stratégies de découverte ou OAuth.

Si vous n’avez pas de plan Flow, [inscrivez-vous pour un compte d’essai gratuit](https://flow.microsoft.com/pricing).

## <a name="prerequisites"></a>Prérequis

* Vous devez avoir un [plan Microsoft Flow](https://flow.microsoft.com/pricing) valide.
* L’environnement Flow doit être synchronisé avec Azure AD, supervisé par Defender ATP et joint au domaine

## <a name="run-an-antivirus-scan-using-microsoft-defender-atp"></a>Exécuter une analyse antivirus en utilisant Microsoft Defender ATP

Les étapes suivantes vous guident dans la création d’un flux qui effectue une analyse antivirus et l’ajoute à une stratégie qui détecte un comportement suspect. Quand une alerte pour un comportement suspect est déclenchée pour un utilisateur, elle déclenche le flux qui exécute une analyse antivirus sur l’ordinateur utilisé par l’utilisateur suspecté d’être compromis.

### <a name="step-1-create-a-flow-to-run-an-antivirus-scan"></a>Étape 1 : Créer un flux pour exécuter une analyse antivirus

> [!NOTE]
> Si vous avez déjà créé un flux en utilisant un connecteur Defender ATP, Flow réutilise automatiquement le connecteur et vous pouvez ignorer l’étape **Se connecter**.

1. Accédez au [portail Microsoft Flow](https://flow.microsoft.com/)et sélectionnez Modèles.
    ![Capture d’écran de la page principale de Flow, montrant la sélection de modèles.](media/tutorial-flow-templates.png)
1. Recherchez « Cloud App Security » et sélectionnez **Exécuter l’analyse antivirus avec Windows Defender sur une alerte Cloud App Security**.
    ![Capture d’écran de la page principale de Flow, montrant les résultats de la recherche.](media/tutorial-flow-templates-search.png)
1. Cliquez sur **Se connecter** et entrez les informations d’identification d’administrateur que vous voulez utiliser avec le connecteur Microsoft Defender ATP.
    ![Capture d’écran de la page principale de Flow, montrant le processus de connexion.](media/tutorial-flow-templates-signin.png)

> [!TIP]
> Conservez cette page ouverte, vous en aurez besoin plus tard.

### <a name="step-2-create-a-cloud-app-security-connector"></a>Étape 2 : Créer un connecteur Cloud App Security

> [!NOTE]
> Si vous avez déjà créé un flux en utilisant un connecteur Cloud App Security, Flow réutilise automatiquement le jeton et vous pouvez ignorer cette étape.

1. Dans Cloud App Security, dans la barre de menus, cliquez sur la roue dentée des paramètres ![Icône des paramètres](./media/settings-icon.png "Icône des paramètres") et sélectionnez **Extensions de sécurité**.
1. Dans la page **Extensions de sécurité**, cliquez sur le bouton plus (+) pour générer un nouveau jeton d’API.
1. Dans la fenêtre contextuelle **Générer un nouveau jeton**, entrez le nom du jeton (par exemple « Flow-Token »), puis cliquez sur **Générer**.
    ![Capture d’écran de la fenêtre de jeton, montrant l’entrée du nom et le bouton Générer.](media/tutorial-flow-token-generate.png)
1. Une fois le jeton généré, cliquez sur l’icône de copie à droite du jeton généré, puis cliquez sur **Fermer**. Vous aurez besoin du jeton ultérieurement.
    ![Capture d’écran de la fenêtre de jeton, montrant le jeton et le processus de copie.](media/tutorial-flow-token-copy.png)

### <a name="step-3-configure-the-flow"></a>Étape 3 : Configurer le flux

> [!NOTE]
> Si vous avez déjà créé un flux en utilisant un connecteur Azure AD, Flow réutilise automatiquement le jeton et vous pouvez ignorer cette étape.

1. De retour dans le portail Microsoft Flow, cliquez sur **Créer**.
    ![Capture d’écran de la page principale de Flow, montrant le processus de création.](media/tutorial-flow-templates-create.png)
1. Dans la fenêtre contextuelle **Cloud App Security**, entrez le nom de la connexion (par exemple « Cloud App Security Token »), collez le jeton d’API que vous avez copié ,puis cliquez sur **Créer**.
    ![Capture d’écran de la fenêtre de Cloud App Security, montrant l’entrée du nom et de la clé, et le bouton Créer.](media/tutorial-flow-token-generate.png)
1. Dans la liste des applications, sur la ligne où apparaît **HTTP avec Azure AD**, choisissez les trois points à la fin de la ligne, puis cliquez sur **Ajouter une nouvelle connexion**.
1. Dans la fenêtre contextuelle **HTTP avec Azure AD**, pour les deux champs **URL de ressource de base** et **URI de la ressource Azure AD**, entrez `https://graph.microsoft.com`, puis cliquez sur **Se connecter** et entrez les informations d’identification d’administrateur que vous voulez utiliser avec le connecteur HTTP avec Azure AD.
    ![Capture d’écran de la fenêtre HTTP avec Azure AD, montrant les champs des ressources et le bouton de connexion.](media/tutorial-flow-templates-azure.png)
1. Cliquez sur **Continue** (Continuer).
    ![Capture d’écran de la fenêtre des modèles Flow, montrant les actions effectuées et le bouton Continuer.](media/tutorial-flow-templates-continue.png)
1. Une fois que tous les connecteurs sont connectés, dans la page du flux, sous **Appliquer à chaque machine**, vous pouvez si vous le souhaitez modifier le commentaire et le type d’analyse, puis cliquer sur **Enregistrer**.
    ![Capture d’écran de la page du flux, montrant la section des paramètres d’analyse.](media/tutorial-flow-templates-scan.png)

### <a name="step-4-apply-the-flow-to-a-policy"></a>Étape 4 : Appliquer le flux à une stratégie

1. Dans Cloud App Security, modifiez la stratégie où vous voulez ajouter le flux « antivirus » puis, sous **Alertes**, sélectionnez **Envoyer des alertes à Flow**, puis sélectionnez **Exécuter l’analyse antivirus avec Windows Defender sur une alerte Cloud App Security**.
    ![Capture d’écran de la page de stratégie, montrant la section des alertes de sécurité.](media/tutorial-flow-templates-alerts.png)

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
[S’intégrer à Flow pour l’automatisation des alertes personnalisées](flow-integration.md)
