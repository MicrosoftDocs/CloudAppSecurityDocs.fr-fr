---
title: Résoudre les problèmes de contrôle d’application par accès conditionnel
description: Cet article fournit une liste des problèmes contrôle d’application par accès conditionnel possibles et fournit des solutions possibles.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 6/30/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 6e43990b3ee3d3c5f33119643329381001707724
ms.sourcegitcommit: e8c40ab8901744314af19ede50e9017a92111721
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91205532"
---
# <a name="troubleshooting-conditional-access-app-control-issues"></a>Résolution des problèmes de contrôle d’application par accès conditionnel

*S’applique à : Microsoft Cloud App Security*

Cet article fournit une liste des problèmes contrôle d’application par accès conditionnel possibles et fournit des solutions possibles.

## <a name="our-system-flagged-a-new-dns-entry-or-generated-a-certificate-for-casms-but-we-dont-use-microsoft-cloud-app-security"></a>Notre système a marqué une nouvelle entrée DNS ou généré un certificat pour *. cas.ms, mais nous n’utilisons pas Microsoft Cloud App Security

Il s’agit d’un comportement normal et des résultats de Cloud App Security protégeant votre environnement. Même si votre organisation n’utilise pas Cloud App Security, lorsqu’un utilisateur visite votre site ou service à partir d’un environnement protégé par le contrôle d’application par accès conditionnel d’Cloud App Security, ses URL sont réécrites pour protéger leur accès.

Par exemple, lorsqu’un utilisateur de contoso, une entreprise protégée par Cloud App Security, consulte fabrikam.com, l’utilisateur est automatiquement redirigé vers fabrikam.com.us.cas.ms. Par conséquent, l’équipe de phishing de Fabrikam verra une nouvelle entrée DNS et un nouveau certificat pour fabrikam.com.us.cas.ms.

Dans cet exemple, vous pouvez voir que même si Fabrikam n’utilise pas réellement Cloud App Security, puisque contoso le fait, l’entrée DNS et le certificat sont créés.

**TBD [ALEX] :??? COMMENT RÉSOUDRE ? Contacter MS ? Ajouter des exceptions ????**

## <a name="i-see-casms-in-my-url-have-i-been-phished"></a>Je vois *. cas.ms dans mon URL. Ai-je été hameçon ?

Tout d’abord, vous n’avez pas été hameçon. Ce type d’URL est attendu et indique que votre organisation applique des contrôles de sécurité supplémentaires pour protéger les données critiques de l’entreprise.

Pour ce faire, vous devez...

Lorsque vous essayez d’accéder à des applications Cloud telles que Salesforce, SharePoint Online ou AWS, vous remarquerez que l’URL est suivie d’un suffixe `*.cas.ms` . Par exemple, lors de l’utilisation de l’application XYZ, l’URL que vous êtes en train de voir aura des modifications de `XYZ.com` à `XYZ.com.us.cas.ms` .

Si l’URL ne correspond pas exactement au modèle de remplacement (par exemple, la redirection de *. com vers *. com.*. cas.ms), ou si vous avez des questions supplémentaires, contactez votre service informatique.
