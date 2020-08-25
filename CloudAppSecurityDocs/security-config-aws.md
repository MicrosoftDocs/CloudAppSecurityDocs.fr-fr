---
title: Obtenir des recommandations en matière de configuration de la sécurité pour AWS
description: Cet article fournit des informations sur la façon d’obtenir des recommandations en matière de configuration de la sécurité dans Cloud App Security en s’intégrant à Amazon Web Services.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 06/28/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 6e0f5f0d7f692dc254b334be9bd34d4b7ebe01a6
ms.sourcegitcommit: 29a8e66c665f51d831516924ae4d9d8047b39276
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88781580"
---
# <a name="security-configuration-for-aws"></a>Configuration de la sécurité pour AWS

*S’applique à : Microsoft Cloud App Security*

Microsoft Cloud App Security vous fournit une évaluation de la configuration de la sécurité de votre environnement Amazon Web Services. Cette évaluation fournit des recommandations de sécurité fondamentales basées sur le test de la sécurité du centre de sécurité Internet (CIS) pour AWS.

## <a name="prerequisites"></a>Prérequis

- Le concentrateur de sécurité AWS doit être configuré pour toutes les régions de votre compte AWS. Pour plus d’informations, consultez [configuration du concentrateur de sécurité AWS](https://go.microsoft.com/fwlink/?linkid=2100208).
    > [!NOTE]
    > Si c’est la première fois que vous activez le hub de sécurité, plusieurs heures peuvent être nécessaires pour que les données initiales deviennent disponibles.
- Votre Amazon Web Services doit être connectée à Cloud App Security. Pour plus d’informations, consultez [connecter AWS à Microsoft Cloud App Security](connect-aws-to-microsoft-cloud-app-security.md).

## <a name="how-to-view-aws-security-recommendations"></a>Comment afficher les recommandations de sécurité AWS

1. Dans Cloud App Security, accédez à **examiner**  >  la configuration de la**sécurité**, puis sélectionnez l’onglet **Amazon Web services** .

    > [!NOTE]
    > Il peut prendre jusqu’à 15 minutes avant que vos changements prennent effet.

    ![menu de configuration de la sécurité](media/security-configuration-menu.png)

1. Vous pouvez filtrer les recommandations par type, par ressource et par compte. En outre, vous pouvez cliquer sur l’icône de configuration de la sécurité ![Icône ASC](media/asc-icon.png) pour ouvrir la recommandation dans Amazon Security Hub pour plus d’informations et pour approfondir la recommandation.

    > [!NOTE]
    > Pour faciliter encore plus les recherches, vous pouvez créer des requêtes personnalisées et les enregistrer pour les utiliser ultérieurement. Une fois que vous avez terminé de générer votre requête, cliquez sur le bouton **Enregistrer sous** en haut à droite des filtres. Dans la fenêtre contextuelle **enregistrer la requête** , nommez votre requête.

    ![Configuration de la sécurité](media/security-configuration-aws.png)

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
