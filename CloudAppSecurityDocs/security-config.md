---
title: Obtenir des recommandations en matière de configuration de la sécurité pour Azure-Cloud App Security | Microsoft Docs
description: Cet article fournit des informations sur l’obtention de recommandations sur la configuration de la sécurité dans Cloud App Security avec l’intégration d’Azure Security Center.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 8/1/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: c6d8f8af-867b-43ab-adee-f06520577fe7
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: c68cf2cb1df5c61a2f3685818320cd3ffd30eb15
ms.sourcegitcommit: 8a49c166424fea83853b0a6895212367526abe78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71084973"
---
# <a name="security-configuration-for-azure"></a>Configuration de la sécurité pour Azure

*S’applique à : Microsoft Cloud App Security*

Microsoft Cloud App Security vous permet d’évaluer la configuration de la sécurité de votre environnement Azure. L’évaluation, permise par Azure Security Center, fournit des recommandations concernant les configurations et les contrôles de sécurité manquants.

## <a name="enable-security-configuration-recommendations"></a>Activer les recommandations de configuration de la sécurité

Pour utiliser cette fonctionnalité, vous devez avoir les autorisations appropriées dans Azure AD et dans le portail Azure. Par défaut, le rôle d’administrateur général Azure AD ne vous donne pas accès aux abonnements Azure. Élevez vos autorisations dans le but d’accorder l’accès aux abonnements Azure à vous-même et aux autres utilisateurs.

> [!IMPORTANT]
> Nous vous recommandons de désactiver l’élévation après avoir terminé la procédure suivante.

Pour obtenir des recommandations sur la configuration de la sécurité dans Microsoft Cloud App Security :

1. <a href="https://docs.microsoft.com/azure/security-center/security-center-management-groups" target="_blank">Gagnez en visibilité au niveau locataire dans Azure Security Center</a>. Ce processus comprend :
   - L’attribution du rôle Lecteur à vous-même ainsi qu’à tous les administrateurs Microsoft Cloud App Security de votre choix, pour tous les abonnements
   - L’attribution du rôle au groupe d’administration racine dans Azure Security Center
   - L’élévation de votre administrateur général Azure AD pour accorder l’accès aux abonnements Azure
   - L’article décrit la procédure permettant de devenir administrateur de la sécurité. Pour que cette intégration fonctionne, les autorisations minimales nécessaires sont celles du niveau **Lecteur**.

2. Veillez à ouvrir <a href="https://ms.portal.azure.com/#blade/Microsoft_Azure_Security/SecurityMenuBlade/0" target="_blank">Azure Security Center</a> pour que les changements entrent en vigueur.

3. Dans Cloud App Security, accédez à **examiner** > la configuration de la**sécurité**, puis sélectionnez l’onglet **Azure** .
    - Microsoft Cloud App Security fournit des recommandations pour les 50 premiers abonnements uniquement.
    - Il peut prendre jusqu’à 15 minutes avant que vos changements prennent effet.

     ![menu de configuration de la sécurité](media/security-configuration-menu.png)

4. Vous pouvez filtrer les recommandations par type, par ressource et par abonnement. En outre, vous pouvez cliquer sur l’icône de configuration de la sécurité ![Icône de configuration de la sécurité](./media/asc-icon.png) pour ouvrir la recommandation dans Azure Security Center et l’analyser.

Pour plus d’informations sur l’implémentation des recommandations de sécurité, consultez [Gestion des recommandations de sécurité dans Azure Security Center](https://docs.microsoft.com/azure/security-center/security-center-recommendations).

   ![Configuration de la sécurité](media/security-configuration-azure.png)

## <a name="next-steps"></a>Étapes suivantes

[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)