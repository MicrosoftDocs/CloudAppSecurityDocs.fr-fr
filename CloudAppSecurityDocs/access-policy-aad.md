---
title: Créer des stratégies d’accès Cloud App Security pour autoriser et bloquer l’accès
description: Cet article décrit la procédure de configuration d’une stratégie d’accès Cloud App Security avec contrôle d’application par accès conditionnel pour autoriser et bloquer l’accès aux applications connectées via Azure AD, à l’aide de fonctionnalités de proxy.
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
ms.assetid: 9095cff1-f8b0-44a7-b1df-a83e674abbc6
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 081ecac67dac14443a85bc103294974607e3e106
ms.sourcegitcommit: c342abeec95359ddabdabcc3a081a0f91d52407c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72335445"
---
# <a name="access-policies"></a>Stratégies d’accès

*S’applique à : Microsoft Cloud App Security*

>[!div class="step-by-step"]
[« PRÉCÉDENT : Guide pratique pour créer une stratégie de session](session-policy-aad.md)<br>
[SUIVANT : Explorer les cas d’usage courants »](use-case-proxy-block-session-aad.md)

Les stratégies d’accès Microsoft Cloud App Security permettent la surveillance et la supervision en temps réel de l’accès à des applications cloud, en fonction de l’utilisateur, de l’emplacement, de l’appareil et de l’application. Vous pouvez créer des stratégies d’accès pour n’importe quel appareil, notamment les appareils qui ne sont pas joints à un domaine et qui ne sont pas gérés par Windows Intune, en déployant des certificats clients sur des appareils gérés ou en utilisant des certificats existants, par exemple des certificats MDM tiers. Par exemple, vous pouvez déployer des certificats clients sur des appareils gérés, puis bloquer l’accès à partir des appareils sans certificat. 

> [!NOTE]
> Au lieu d’autoriser ou de bloquer complètement l’accès, vous pouvez utiliser des [stratégies de session](session-policy-aad.md), qui vous permettent d’autoriser l’accès pendant la surveillance de la session et/ou de limiter des activités de session particulières. 

## <a name="prerequisites-to-using-access-policies"></a>Prérequis à l’utilisation des stratégies d’accès

- Licence Azure AD Premium P1
- Les applications appropriées doivent être [déployées avec le Contrôle d’accès conditionnel aux applications](proxy-deployment-aad.md)
- Une [stratégie d’accès conditionnel Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) doit être en place pour rediriger les utilisateurs vers le Microsoft Cloud App Security, comme décrit ci-dessous.

> [!NOTE]
> - Les stratégies d’accès prennent également en charge les applications qui sont configurées avec des fournisseurs d’identité non-Azure AD. Pour plus d’informations, envoyez un e-mail à mcaspreview@microsoft.com.

## <a name="create-an-azure-ad-conditional-access-policy"></a>Créer une stratégie d’accès conditionnel Azure AD

Les stratégies d’accès conditionnel Azure Active Directory et les stratégies de session Cloud App Security travaillent conjointement pour examiner chaque session utilisateur et prendre des décisions stratégiques pour chaque application. Pour configurer une stratégie d’accès conditionnel dans Azure AD, procédez comme suit :

1. Configurez une [stratégie d’accès conditionnel Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) avec des attributions pour l’utilisateur ou le groupe d’utilisateurs et l’application que vous souhaitez contrôler avec le contrôle d’application par accès conditionnel. 

   > [!NOTE]
   > Seules les applications [déployées avec le Contrôle d’accès conditionnel aux applications](proxy-deployment-aad.md) sont concernées par cette stratégie. 

2. Routez les utilisateurs vers Microsoft Cloud App Security en sélectionnant **Utiliser le contrôle d’application par accès conditionnel** sous **Session**.
 
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

    - **Autoriser** : Définissez cette action pour autoriser explicitement l’accès en fonction des filtres de stratégie que vous définissez.

    - **Bloquer** : Définissez cette action pour bloquer explicitement l’accès en fonction des filtres de stratégie que vous définissez. 

6. Vous pouvez **Créer une alerte pour chaque événement correspondant avec le niveau de gravité de la stratégie** et définissez une limite d’alerte, puis déterminez si vous voulez que l’alerte prenne la forme d’un e-mail, d’un SMS ou des deux.



>[!div class="step-by-step"]
[« PRÉCÉDENT : Guide pratique pour créer une stratégie de session](session-policy-aad.md)<br>
[SUIVANT : Explorer les cas d’usage courants »](use-case-proxy-block-session-aad.md)

 
## <a name="next-steps"></a>Étapes suivantes  
[Blocage des téléchargements sur des appareils non gérés à l’aide des fonctionnalités du Contrôle d’accès conditionnel aux applications Azure AD](use-case-proxy-block-session-aad.md)   

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)  
  
  
