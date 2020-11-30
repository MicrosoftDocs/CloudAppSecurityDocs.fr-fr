---
title: Obtenir des recommandations en matière de configuration de la sécurité pour GCP
description: Cet article fournit des informations sur la façon d’obtenir des recommandations en matière de configuration de la sécurité dans Cloud App Security en s’intégrant à Google Cloud Platform.
ms.date: 06/28/2020
ms.topic: how-to
ms.openlocfilehash: 15242c8a89aee5a9aa3edd1bf7a881f81734680a
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96315495"
---
# <a name="security-configuration-for-google-cloud-platform"></a>Configuration de la sécurité pour Google Cloud Platform

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Microsoft Cloud App Security vous fournit une évaluation de la configuration de la sécurité de votre environnement Google Cloud Platform (GCP). Cette évaluation fournit des recommandations de sécurité fondamentales basées sur le [Benchmark Center for Internet Security (CIS) pour GCP](https://www.cisecurity.org/benchmark/google_cloud_computing_platform/), version 1.1.0.

Cette évaluation fournit une vue d’ensemble de la configuration de la sécurité de tous les projets GCP et permet aux administrateurs de la sécurité d’examiner les lacunes de la configuration de la sécurité et de lancer une mise à jour par les propriétaires des ressources.

## <a name="prerequisites"></a>Prérequis

- Vous devez configurer le centre de commandes de sécurité GCP avec l’analyse d’intégrité de la sécurité pour tous vos projets GCP dans votre organisation. Pour plus d’informations, consultez [configuration du centre de commandes de sécurité GCP](https://cloud.google.com/security-command-center/docs/quickstart-scc-setup) et activer l’analyse de l’intégrité de la [sécurité](https://cloud.google.com/security-command-center/docs/how-to-use-security-health-analytics).
- Vos projets GCP doivent être connectés à Cloud App Security. Pour plus d’informations, consultez [connecter GCP à Microsoft Cloud App Security](connect-google-gcp-to-microsoft-cloud-app-security.md).

## <a name="how-to-view-gcp-security-recommendations"></a>Comment afficher les recommandations de sécurité GCP

1. Dans Cloud App Security, accédez à **examiner**  >  la configuration de la **sécurité**, puis sélectionnez l’onglet **Google Cloud Platform** .

    > [!NOTE]
    > Il peut prendre jusqu’à 15 minutes avant que vos changements prennent effet.

    ![menu de configuration de la sécurité](media/security-configuration-menu.png)

1. Vous pouvez filtrer les recommandations par type, par ressource et par abonnement. En outre, vous pouvez cliquer sur l’icône de configuration de la sécurité ![Icône ASC](media/asc-icon.png) pour ouvrir la recommandation dans le centre de commandes de sécurité GCP pour plus d’informations et pour approfondir la recommandation.

    > [!NOTE]
    > Pour faciliter encore plus les recherches, vous pouvez créer des requêtes personnalisées et les enregistrer pour les utiliser ultérieurement. Une fois que vous avez terminé de générer votre requête, cliquez sur le bouton **Enregistrer sous** en haut à droite des filtres. Dans la fenêtre contextuelle **enregistrer la requête** , nommez votre requête.

    ![Configuration de la sécurité](media/security-configuration-gcp.png)

1. Sélectionnez une recommandation pour afficher des informations supplémentaires sur la recommandation, notamment une description et des instructions de correction détaillées.

    ![recommandation de configuration de la sécurité](media/security-configuration-gcp-details.png)

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
