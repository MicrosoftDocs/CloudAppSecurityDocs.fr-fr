---
title: Résolution des problèmes-qu’est-ce que cas.ms, mcas.ms ou mcas-gov.us ?
description: Cet article fournit des informations sur le suffixe d’URL cas.ms, mcas.ms ou mcas-gov.us utilisé par contrôle d’application par accès conditionnel.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/18/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 77a93d0b514b928af733be240357257f3573341b
ms.sourcegitcommit: 7a217c4b127aa874de5bb5e44bd3b7291530cde0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79525499"
---
# <a name="troubleshooting---what-is-casms-mcasms-or-mcas-govus"></a>Résolution des problèmes-qu’est-ce que `cas.ms`, `mcas.ms`ou `mcas-gov.us`?

*S’applique à : Microsoft Cloud App Security*

Cet article fournit des informations sur les suffixes d’URL `cas.ms`, `mcas.ms`et `mcas-gov.us` utilisés par contrôle d’application par accès conditionnel.

## <a name="our-system-flagged-a-new-dns-entry-or-generated-certificate-for-casms-mcasms-or-mcas-govus-but-we-dont-use-cloud-app-security"></a>Notre système a marqué une nouvelle entrée DNS ou un certificat généré pour `*.cas.ms`, `*.mcas.ms`ou `*.mcas-gov.us`, mais nous n’utilisons pas Cloud App Security

Il s’agit d’un comportement normal et des résultats de Cloud App Security protégeant votre environnement. Même si votre organisation n’utilise pas Cloud App Security, lorsqu’un utilisateur visite votre site ou service à partir d’un environnement qui le fait, ses URL sont réécrites pour protéger son accès.

Par exemple, contoso protège son environnement à l’aide des contrôle d’application par accès conditionnel fournis par Cloud App Security. Quand un utilisateur contoso visite `fabrikam.com`, il est automatiquement redirigé vers `fabrikam.com.<region>.cas.ms`. Par conséquent, l’équipe de phishing de Fabrikam verra une nouvelle entrée et un nouveau certificat DNS pour `fabrikam.com.<region>.cas.ms`.

Donc, même si Fabrikam n’utilise pas Cloud App Security, il voit l’entrée DNS ou le certificat, car contoso en fait.

## <a name="heres-why-you-see-casms-mcasms-or-mcas-govus-in-your-url"></a>Voici pourquoi vous pouvez voir `*.cas.ms`, `*.mcas.ms`ou `*.mcas-gov.us` dans votre URL

Tout d’abord, vous n’avez pas été hameçon. Ce type d’URL est attendu et indique que votre organisation applique des contrôles de sécurité supplémentaires pour protéger les données critiques de l’entreprise.

Pour ce faire, ils utilisent Cloud App Security, une solution pour la protection de l’environnement Cloud de votre organisation, afin de remplacer toutes les URL et cookies pertinents relatifs aux applications Cloud que vous utilisez.

Ainsi, lorsque vous essayez d’accéder à une application Cloud telle que Salesforce, SharePoint Online ou AWS, vous remarquerez que son URL est suivie d’un suffixe `<region>.cas.ms`, `<region>.mcas.ms`ou `<region>.mcas-gov.us`. Par exemple, lors de l’utilisation de l’application XYZ, l’URL que vous avez utilisée pour voir les modifications de `XYZ.com` à `XYZ.com.<region>.cas.ms`.

Si l’URL ne correspond pas exactement à l’un des modèles de remplacement (par exemple, `<app_site>.com` n’est pas remplacé par `<app_site>.com.<region>.cas.ms`), ou si vous avez des problèmes supplémentaires, contactez votre service informatique.
