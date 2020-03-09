---
title: Créer des stratégies d’accès Cloud App Security pour autoriser et bloquer l’accès
description: Cet article décrit la procédure de configuration d’une stratégie d’accès Cloud App Security contrôle d’application par accès conditionnel pour autoriser et bloquer l’accès aux applications connectées via Azure AD à l’aide des fonctionnalités de proxy inverse.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 5ab52bf417a6a0a6fea583fac9f64f70ea78e4a3
ms.sourcegitcommit: 3f6ef6b97a0953470135d115323a00cf11441ab7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2020
ms.locfileid: "78927748"
---
# <a name="access-policies"></a>Stratégies d'accès

*S’applique à : Microsoft Cloud App Security*

Les stratégies d’accès Microsoft Cloud App Security permettent une surveillance et un contrôle en temps réel de l’accès aux applications Cloud en fonction de l’utilisateur, de l’emplacement, de l’appareil et de l’application. Vous pouvez créer des stratégies d’accès pour n’importe quel appareil, notamment les appareils qui ne sont pas joints à un domaine, et qui ne sont pas gérés par Windows Intune en déployant des certificats clients sur des appareils gérés ou en utilisant des certificats existants, tels que des certificats MDM tiers. Par exemple, vous pouvez déployer des certificats clients sur des appareils gérés, puis bloquer l’accès à partir des appareils sans certificat.

> [!NOTE]
> Au lieu d’autoriser ou de bloquer complètement l’accès, avec les [stratégies de session](session-policy-aad.md) , vous pouvez autoriser l’accès pendant la surveillance de la session et/ou limiter les activités de session spécifiques.

## <a name="prerequisites-to-using-access-policies"></a>Conditions préalables à l’utilisation des stratégies d’accès

- Licence Azure AD Premium P1
- Les applications appropriées doivent être [déployées avec contrôle d’application par accès conditionnel](proxy-deployment-aad.md)
- Une [stratégie d’accès conditionnel Azure ad](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) doit être en place pour rediriger les utilisateurs vers Microsoft Cloud App Security, comme décrit ci-dessous.

> [!NOTE]
> - Les stratégies d’accès prennent également en charge les applications qui sont configurées avec des fournisseurs d’identité autres que Azure AD. Pour plus d’informations, envoyez un e-mail à mcaspreview@microsoft.com.

## <a name="create-an-azure-ad-conditional-access-policy"></a>Créer une stratégie d’accès conditionnel Azure AD

Azure Active Directory stratégies d’accès conditionnel et les stratégies de session de Cloud App Security fonctionnent en tandem pour examiner chaque session utilisateur et prendre des décisions de stratégie pour chaque application. Pour configurer une stratégie d’accès conditionnel dans Azure AD, procédez comme suit :

1. Configurez une [stratégie d’accès conditionnel Azure ad](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) avec des affectations pour l’utilisateur ou le groupe d’utilisateurs et l’application que vous souhaitez contrôler avec contrôle d’application par accès conditionnel.

    > [!NOTE]
    > Seules [les applications déployées avec contrôle d’application par accès conditionnel](proxy-deployment-aad.md) seront affectées par cette stratégie.

2. Acheminez les utilisateurs vers Microsoft Cloud App Security en sélectionnant l’option **utiliser contrôle d’application par accès conditionnel restrictions appliquées** sous **session**.

## <a name="create-a-cloud-app-security-access-policy"></a>Créer une stratégie d’accès Cloud App Security

Pour créer une nouvelle stratégie d’accès, procédez comme suit :

1. Dans le portail, sélectionnez **contrôle** , puis **stratégies**.
2. Dans la page **stratégies** , cliquez sur **créer une stratégie** et sélectionnez stratégie d' **accès**.

3. Dans la fenêtre **stratégie d’accès** , attribuez un nom à votre stratégie, par exemple *bloquer l’accès à partir des appareils non gérés*.

4. Dans les **activités correspondant à l’ensemble de la section suivante** , sous source de l' **activité**, sélectionnez des filtres d’activité supplémentaires à appliquer à la stratégie. Les filtres incluent les options suivantes :

    - **Balises d’appareils**: utilisez ce filtre pour identifier les appareils non gérés.

    - **Emplacement**: utilisez ce filtre pour identifier les emplacements inconnus (et par conséquent risqués).

    - **Adresse IP**: utilisez ce filtre pour filtrer par adresse IP ou pour utiliser des balises d’adresse IP précédemment attribuées.

    - **Étiquette de l’agent utilisateur**: utilisez ce filtre pour activer l’heuristique afin d’identifier les applications mobiles et de bureau. Ce filtre peut être défini sur est égal à ou n’est pas égal à. Les valeurs doivent être testées par rapport à vos applications mobiles et de bureau pour chaque application Cloud.

5. Sous **actions**, sélectionnez l’une des options suivantes :

    - **Test**: définissez cette action pour autoriser explicitement l’accès en fonction des filtres de stratégie que vous définissez.

    - **Bloquer**: définissez cette action pour bloquer explicitement l’accès en fonction des filtres de stratégie que vous définissez.

6. Vous pouvez **créer une alerte pour chaque événement correspondant avec le niveau de gravité de la stratégie** et définir une limite d’alerte et choisir si vous souhaitez que l’alerte soit envoyée par courrier électronique, message texte ou les deux.

## <a name="next-steps"></a>Étapes suivantes :

> [!div class="nextstepaction"]
> [«PRÉCÉDENT : comment créer une stratégie de session](session-policy-aad.md)

> [!div class="nextstepaction"]
> [ENSUITE : Explorez les cas d’utilisation populaires»](use-case-proxy-block-session-aad.md)

## <a name="see-also"></a>Voir aussi

> [!div class="nextstepaction"]
> [Blocage des téléchargements sur des appareils non gérés à l’aide de contrôles de session](use-case-proxy-block-session-aad.md)

[!INCLUDE [Open support ticket](includes/support.md)]
