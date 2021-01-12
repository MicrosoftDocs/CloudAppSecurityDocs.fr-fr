---
title: Intégrer Microsoft Power automate avec Microsoft Cloud App Security pour recevoir une automatisation des alertes personnalisée
description: Cet article fournit des informations sur la façon d’obtenir une automatisation des alertes personnalisée en intégrant Microsoft Power Automated avec Cloud App Security.
ms.date: 01/05/2021
ms.topic: how-to
ms.openlocfilehash: 8b2575764470bb444c2bb7a36e37cf80dc6251ce
ms.sourcegitcommit: 0768aa1992819e2651a14a731f79e178fdececc5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98114732"
---
# <a name="integrate-with-microsoft-power-automate-for-custom-alert-automation"></a>Intégration avec Microsoft Power automate pour l’automatisation des alertes personnalisée

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Cloud App Security s’intègre à [Microsoft Power automate](/flow/getting-started) pour fournir une automatisation des alertes personnalisée et des règles d’orchestration. À l’aide [de l’écosystème de connecteurs](/connectors/) disponibles dans Power automate, vous pouvez automatiser le déclenchement des règles lorsque Cloud App Security génère des alertes. Vous pouvez par exemple créer automatiquement un problème dans un système de gestion de tickets à l’aide du [connecteur ServiceNow](/connectors/service-now/) ou envoyer un e-mail d’approbation pour exécuter une action de gouvernance personnalisée quand une alerte est déclenchée dans Cloud App Security.

## <a name="prerequisites"></a>Prérequis

- Vous devez disposer d’un [plan Microsoft Power Automate](https://flow.microsoft.com/pricing) valide.

## <a name="how-it-works"></a>Fonctionnement

En soi, Cloud App Security fournit des options de gouvernance prédéfinies, telles que la suspension d’un utilisateur ou la création d’un fichier privé lors de la définition de stratégies. En créant un manuel dans Power automatiser à l’aide du connecteur Cloud App Security, vous pouvez créer des flux de travail pour activer des options de gouvernance personnalisées pour vos stratégies. Une fois le manuel créé dans Power automate, associez-le simplement à une stratégie dans Cloud App Security pour envoyer des alertes à Power automate. Microsoft Power automate offre plusieurs connecteurs et conditions pour créer un flux de travail personnalisé pour votre organisation.

Le [connecteur Cloud App Security](/connectors/cloudappsecurity/) dans Power automate prend en charge les déclencheurs et les actions automatisés. Power automate est déclenché automatiquement quand Cloud App Security génère une alerte. Les actions incluent le changement de l’état de l’alerte dans Cloud App Security.

## <a name="how-to-create-playbooks-with-power-automate"></a>Comment créer des règles avec Power automate

1. [Créez un jeton d’API](api-authentication.md) dans Cloud App Security.

2. Accédez au [portail Power automate](https://flow.microsoft.com), sélectionnez **mes flux**, sélectionnez **nouveau**, puis dans la liste déroulante, sélectionnez **automatisé-à partir de vide**.

    ![Power automate créer un nouveau Flow](media/flow-create-new.png)

3. Fournissez un nom pour le Flow, puis dans **choisir le déclencheur de votre Flow**, tapez **Cloud App Security** et sélectionnez le **moment où une alerte est générée**.

    ![Power automate quand une alerte est générée](media/flow-when-alert.png)

4. Sous **Paramètres d’authentification**, collez le jeton d’API créé à l’étape 1.

5. Définissez le workflow à déclencher quand une stratégie dans Cloud App Security génère une alerte. Ajoutez une action, une condition logique, des boucles ou des conditions switch case, puis enregistrez le playbook.

    ![Power automatiser le flux de travail](media/flow-workflow.png)

6. Dans le portail Cloud App Security, accédez à **stratégies** , puis dans la ligne de la stratégie dont vous souhaitez transférer les alertes vers Power automate, cliquez sur les trois points et sélectionnez **paramètres**.
7. Sous **alertes**, sélectionnez **Envoyer des alertes à Power automate** , puis choisissez le nom du manuel dans le menu déroulant.

    ![Activer Power automate dans Cloud App Security portail](media/flow-mcas-config.png)

8. Cloud App Security les règles que vous avez créées ou auxquelles vous avez accès peuvent être consultées dans l’écran **extensions de sécurité** .

    ![afficher des playbooks dans Cloud App Security](media/flow-extensions.png)

## <a name="related-videos"></a>Vidéos associées

> [!div class="nextstepaction"]
> [Automatisation et intégration avec Power automate webinaire](webinars.md#on-demand-webinars)

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
