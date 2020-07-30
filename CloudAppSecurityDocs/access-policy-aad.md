---
title: Créer des stratégies d’accès Cloud App Security pour autoriser et bloquer l’accès
description: Cet article décrit la procédure de configuration d’une stratégie d’accès Cloud App Security avec contrôle d’application par accès conditionnel pour autoriser et bloquer l’accès aux applications connectées via Azure AD, à l’aide de fonctionnalités de proxy.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/31/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 88a86e60e632f781428f307c4e1cf6653f87836b
ms.sourcegitcommit: 97563af6076ccbad0d994ac69a85a998a625d06a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87296774"
---
# <a name="access-policies"></a>Stratégies d’accès

*S’applique à : Microsoft Cloud App Security*

Les stratégies d’accès Microsoft Cloud App Security permettent la surveillance et la supervision en temps réel de l’accès à des applications cloud, en fonction de l’utilisateur, de l’emplacement, de l’appareil et de l’application. Vous pouvez créer des stratégies d’accès pour n’importe quel appareil, notamment les appareils qui ne sont pas jonction Azure AD Hybride et non gérés par Microsoft Intune en déployant des certificats clients sur des appareils gérés ou à l’aide de certificats existants, tels que des certificats MDM tiers. Par exemple, vous pouvez déployer des certificats clients sur des appareils gérés, puis bloquer l’accès à partir des appareils sans certificat.

> [!NOTE]
> Au lieu d’autoriser ou de bloquer complètement l’accès, vous pouvez utiliser des [stratégies de session](session-policy-aad.md), qui vous permettent d’autoriser l’accès pendant la surveillance de la session et/ou de limiter des activités de session particulières.

## <a name="prerequisites-to-using-access-policies"></a>Prérequis à l’utilisation des stratégies d’accès

- Azure AD Premium licence P1 ou la licence requise par votre solution de fournisseur d’identité (IdP)
- Les applications appropriées doivent être [déployées avec le Contrôle d’accès conditionnel aux applications](proxy-deployment-aad.md)
- Configurez votre solution de fournisseur d’identité pour qu’elle fonctionne avec Cloud App Security :
  - Pour [l’accès conditionnel Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal), consultez [Configuration de l’intégration avec Azure AD](proxy-deployment-aad.md#configure-integration-with-azure-ad).
  - Pour les autres solutions de fournisseur d’identité, consultez [Configuration de l’intégration avec d’autres solutions de fournisseur d’identité](proxy-deployment-aad.md#configure-integration-with-other-idp-solutions).

## <a name="create-a-cloud-app-security-access-policy"></a>Créer une stratégie d’accès Cloud App Security

Pour créer une stratégie d’activité, suivez cette procédure :

1. Dans le portail, sélectionnez **Contrôle**, puis **Stratégies**.
2. Dans la page **Stratégies**, cliquez sur **Créer une stratégie** et sélectionnez **Stratégie d’accès**.

3. Dans la fenêtre **Stratégie d’accès**, affectez un nom à votre stratégie, comme *Bloquer l’accès à partir des appareils non gérés*.

4. Dans la section **Activités remplissant toutes les conditions suivantes**, sous **Source de l’activité**, sélectionnez des filtres d’activité supplémentaires à appliquer à la stratégie. Les filtres incluent les options suivantes :

    - **Balise de l’appareil** : Utilisez ce filtre pour identifier les appareils non gérés.

    - **Emplacement** : Utilisez ce filtre pour identifier les emplacements inconnus (et par conséquent à risque).

    - **Adresse IP** : Utilisez ce filtre pour filtrer selon des adresses IP ou utiliser des balises d’adresse IP déjà attribuées.

    - **Étiquette agent utilisateur** : Utilisez ce filtre pour activer l’heuristique afin d’identifier les applications mobiles et de bureau. Ce filtre peut avoir la valeur est égal à ou n’est pas égal à. Vous devez tester ces valeurs par rapport à vos applications mobiles et vos applications de bureau pour chaque application cloud.

5. Sous **Actions**, sélectionnez l’une des options suivantes :

    - **Test**: définissez cette action pour autoriser explicitement l’accès en fonction des filtres de stratégie que vous définissez.

    - **Bloquer** : Définissez cette action pour bloquer explicitement l’accès en fonction des filtres de stratégie que vous définissez.

6. Vous pouvez **Créer une alerte pour chaque événement correspondant avec le niveau de gravité de la stratégie** et définissez une limite d’alerte, puis déterminez si vous voulez que l’alerte prenne la forme d’un e-mail, d’un SMS ou des deux.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [« PRÉCÉDENT : Guide pratique pour créer une stratégie de session](session-policy-aad.md)

> [!div class="nextstepaction"]
> [SUIVANT : Explorer les cas d’usage courants »](use-case-proxy-block-session-aad.md)

## <a name="see-also"></a>Voir aussi

> [!div class="nextstepaction"]
> [Blocage des téléchargements sur des appareils non gérés à l’aide de contrôles de session](use-case-proxy-block-session-aad.md)

> [!div class="nextstepaction"]
> [Résolution des problèmes de contrôles d’accès et de session](troubleshooting-proxy.md)

[!INCLUDE [Open support ticket](includes/support.md)]
