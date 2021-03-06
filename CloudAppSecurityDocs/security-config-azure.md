---
title: Obtenir des recommandations en matière de configuration de la sécurité pour Azure
description: Cet article fournit des informations sur la façon d’obtenir des recommandations en matière de configuration de la sécurité dans Cloud App Security en s’intégrant à Azure Security Center.
ms.date: 09/15/2020
ms.topic: how-to
ms.openlocfilehash: e34cd55f3e09b36c1bbb4641a7842e525f3c56d7
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96315512"
---
# <a name="security-configuration-for-azure"></a>Configuration de la sécurité pour Azure

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Microsoft Cloud App Security vous permet d’évaluer la configuration de la sécurité de votre environnement Azure. L’évaluation, optimisée par Azure Security Center, fournit des recommandations pour les contrôles de sécurité et de configuration manquants.

## <a name="prerequisites"></a>Prérequis

Votre organisation doit disposer de licences Azure Security Center pour tous les abonnements pour lesquels vous souhaitez fournir des évaluations de configuration de sécurité Azure.

## <a name="how-to-enable-azure-security-recommendations"></a>Comment activer les recommandations de sécurité Azure

Pour activer les recommandations de configuration de la sécurité dans Cloud App Security, activez votre abonnement Azure Security Center en accédant au <a href="https://ms.portal.azure.com/#blade/Microsoft_Azure_Security/SecurityMenuBlade/0" target="_blank">portail</a>.

## <a name="how-to-view-azure-security-recommendations"></a>Comment afficher les recommandations de sécurité Azure

1. Dans Cloud App Security, accédez à **examiner**  >  la configuration de la **sécurité**, puis sélectionnez l’onglet **Azure** .

    > [!NOTE]
    > Il peut prendre jusqu’à 15 minutes avant que vos changements prennent effet.

    ![menu de configuration de la sécurité](media/security-configuration-menu.png)

1. Vous pouvez filtrer les recommandations par type, par ressource et par abonnement. En outre, vous pouvez cliquer sur l’icône de configuration de la sécurité ![Icône ASC](media/asc-icon.png) pour ouvrir la recommandation dans Azure Security Center et l’analyser.

    > [!NOTE]
    > Pour faciliter encore plus les recherches, vous pouvez créer des requêtes personnalisées et les enregistrer pour les utiliser ultérieurement. Une fois que vous avez terminé de générer votre requête, cliquez sur le bouton **Enregistrer sous** en haut à droite des filtres.  Dans la fenêtre contextuelle **enregistrer la requête** , nommez votre requête.

    ![Configuration de la sécurité](media/security-configuration-azure.png)

Pour plus d’informations sur l’implémentation des recommandations de sécurité, consultez [Gestion des recommandations de sécurité dans Azure Security Center](/azure/security-center/security-center-recommendations).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]