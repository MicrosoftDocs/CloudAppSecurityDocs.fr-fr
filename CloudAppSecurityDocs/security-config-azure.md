---
title: Obtenir des recommandations en matière de configuration de la sécurité pour Azure
description: Cet article fournit des informations sur la façon d’obtenir des recommandations en matière de configuration de la sécurité dans Cloud App Security en s’intégrant à Azure Security Center.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 06/29/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 0d821e574dc241097d70814cf854c46e4db2664b
ms.sourcegitcommit: 29a8e66c665f51d831516924ae4d9d8047b39276
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88781546"
---
# <a name="security-configuration-for-azure"></a>Configuration de la sécurité pour Azure

*S’applique à : Microsoft Cloud App Security*

Microsoft Cloud App Security vous permet d’évaluer la configuration de la sécurité de votre environnement Azure. L’évaluation, permise par Azure Security Center, fournit des recommandations concernant les configurations et les contrôles de sécurité manquants.

## <a name="enable-security-configuration-recommendations"></a>Activer les recommandations de configuration de la sécurité

Pour utiliser cette fonctionnalité, vous devez avoir les autorisations appropriées dans Azure AD et dans le portail Azure. Par défaut, le rôle d’administrateur général Azure AD ne vous donne pas accès aux abonnements Azure. Élevez vos autorisations dans le but d’accorder l’accès aux abonnements Azure à vous-même et aux autres utilisateurs.

> [!IMPORTANT]
> Nous vous recommandons de désactiver l’élévation après avoir terminé la procédure suivante.

## <a name="how-to-enable-azure-security-recommendations"></a>Comment activer les recommandations de sécurité Azure

Pour obtenir des recommandations sur la configuration de la sécurité dans Microsoft Cloud App Security :

1. <a href="https://docs.microsoft.com/azure/security-center/security-center-management-groups" target="_blank">Bénéficiez d’une visibilité à l’niveau du locataire pour Azure Security Center</a>. Ce processus comprend :

    - L’attribution du rôle Lecteur à vous-même ainsi qu’à tous les administrateurs Microsoft Cloud App Security de votre choix, pour tous les abonnements
    - L’attribution du rôle au groupe d’administration racine dans Azure Security Center
    - L’élévation de votre administrateur général Azure AD pour accorder l’accès aux abonnements Azure
    - L’article décrit la procédure permettant de devenir administrateur de la sécurité. Pour que cette intégration fonctionne, les autorisations minimales dont vous avez besoin sont **Reader**.

1. Veillez à ouvrir <a href="https://ms.portal.azure.com/#blade/Microsoft_Azure_Security/SecurityMenuBlade/0" target="_blank">Azure Security Center</a> pour que les changements entrent en vigueur.

## <a name="how-to-view-azure-security-recommendations"></a>Comment afficher les recommandations de sécurité Azure

1. Dans Cloud App Security, accédez à **examiner**  >  la configuration de la**sécurité**, puis sélectionnez l’onglet **Azure** .

    > [!NOTE]
    > Il peut prendre jusqu’à 15 minutes avant que vos changements prennent effet.

    ![menu de configuration de la sécurité](media/security-configuration-menu.png)

1. Vous pouvez filtrer les recommandations par type, par ressource et par abonnement. En outre, vous pouvez cliquer sur l’icône de configuration de la sécurité ![Icône ASC](media/asc-icon.png) pour ouvrir la recommandation dans Azure Security Center et l’analyser.

    > [!NOTE]
    > Pour faciliter encore plus les recherches, vous pouvez créer des requêtes personnalisées et les enregistrer pour les utiliser ultérieurement. Une fois que vous avez terminé de générer votre requête, cliquez sur le bouton **Enregistrer sous** en haut à droite des filtres.  Dans la fenêtre contextuelle **enregistrer la requête** , nommez votre requête.

    ![Configuration de la sécurité](media/security-configuration-azure.png)

Pour plus d’informations sur l’implémentation des recommandations de sécurité, consultez [Gestion des recommandations de sécurité dans Azure Security Center](https://docs.microsoft.com/azure/security-center/security-center-recommendations).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
