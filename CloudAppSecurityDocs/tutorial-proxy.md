---
title: Protéger toutes les applications utilisées dans votre organisation en temps réel
description: Ce didacticiel fournit des instructions sur l’utilisation des contrôles d’accès et de session pour surveiller et contrôler l’accès aux applications et à leurs données.
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: tutorial
ms.date: 01/01/2020
ms.collection: M365-security-compliance
ms.openlocfilehash: bb0ae32a16d9ea9a8f36a0bd0ae0405b1d28b273
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90881204"
---
# <a name="tutorial-protect-any-apps-in-use-in-your-organization-in-real-time"></a>Tutoriel : Protéger toutes les applications utilisées dans votre organisation en temps réel

[!INCLUDE [Banner for top of topics](includes/banner.md)]

L’utilisation approuvée des applications par les employés, stockent souvent certaines de vos données d’entreprise et secrets les plus sensibles. Dans l’espace de travail moderne, les utilisateurs accèdent à ces applications dans de nombreuses situations risquées. Ces utilisateurs peuvent être des partenaires de votre organisation qui ne disposent que d’un peu de visibilité ou d’employés utilisant des appareils non gérés ou provenant d’adresses IP publiques. En raison de la diversité des risques dans ce paysage, une stratégie de confiance nulle doit être employée. Souvent, il n’y a pas assez de connaissance des violations et de la perte de données dans ces applications après le fait ; par conséquent, de nombreux scénarios de protection et contre les cybermenaces des informations doivent être traités ou bloqués en temps réel.

Ce didacticiel fournit des instructions sur l’utilisation des contrôles d’accès et de session pour surveiller et contrôler l’accès aux applications et à leurs données. La gestion adaptative de l’accès à vos données et l’atténuation des menaces permet à Cloud App Security de protéger vos ressources les plus sensibles. Plus précisément, nous aborderons les scénarios suivants :

> [!div class="checklist"]
>
> * Surveiller les activités des utilisateurs pour les anomalies
> * Protéger vos données lorsqu’elles sont exfiltrées
> * Empêcher le téléchargement de données non protégées vers vos applications

## <a name="how-to-protect-your-organization-from-any-app-in-real-time"></a>Comment protéger toutes les applications de votre organisation en temps réel

Utilisez ce processus pour déployer des contrôles en temps réel dans votre organisation.

### <a name="phase-1-monitor-user-activities-for-anomalies"></a>Phase 1 : Surveiller les activités des utilisateurs pour les anomalies

1. **Déployer vos applications** : Commencez par déployer les applications importantes que votre organisation utilise. Le déploiement est simplifié par notre intégration native avec l’accès conditionnel Azure Active Directory (Azure AD). Vous pouvez déployer des applications en procédant comme suit :

    * Commencez par [déployer des applications qui sont proposées](proxy-intro-aad.md) par Cloud App Security pour travailler prêtes à l’emploi. Pour obtenir la liste des applications disponibles, consultez [Applications et les clients pris en charge](proxy-intro-aad.md#supported-apps-and-clients).

    * Ensuite, pour les applications qui ne sont pas proposées par Cloud App Security, utilisez le processus suivant pour [intégrer et déployer n’importe quelle application](proxy-deployment-any-app.md).

    Une fois vos applications déployées, elles sont analysées en temps réel, qui vous donnent des informations immédiates sur leurs activités et leurs informations connexes. Vous pouvez utiliser ces informations pour identifier un comportement anormal.

1. **Analyser et examiner** : Dans Cloud App Security, utilisez le [Journal d’activité](activity-filters.md) pour surveiller et caractériser l’utilisation des applications dans votre environnement et comprendre leurs risques. Vous pouvez limiter l’étendue des activités présentées à l’aide de [la recherche, les filtres et les requêtes](activity-filters-queries.md) pour identifier rapidement les activités à risque.

### <a name="phase-2-protect-your-data-when-its-exfiltrated"></a>Phase 2 : Protéger vos données lorsqu’elles sont exfiltrées

Une préoccupation majeure pour de nombreuses organisations est de savoir comment empêcher l’exfiltration de données avant qu’elle ne se produise. Deux des plus grands risques sont les appareils non gérés (qui peuvent ne pas être protégés par un code confidentiel ou qui peuvent contenir des applications malveillantes) et les utilisateurs invités où votre service informatique a peu de visibilité et de contrôle.

Maintenant que vos applications sont déployées, vous pouvez facilement configurer des stratégies pour atténuer ces deux risques en tirant parti de nos intégrations natives avec Microsoft Intune pour la gestion des appareils, Azure AD pour les groupes d’utilisateurs et Azure Information Protection pour la protection des données.

* **Atténuer des appareils non gérés** : créer une [stratégie de session pour étiqueter](session-policy-aad.md#create-a-cloud-app-security-session-policy) et protéger les fichiers hautement confidentiels destinés aux utilisateurs de votre organisation uniquement.
* **Atténuer les utilisateurs invités** : créez une [stratégie de session pour appliquer des autorisations personnalisées](session-policy-aad.md#protect-download) à n’importe quel fichier téléchargé par des utilisateurs invités. Par exemple, vous pouvez définir des autorisations pour que les utilisateurs invités puissent accéder à un fichier protégé uniquement.

### <a name="phase-3-prevent-unprotected-data-from-being-uploaded-to-your-apps"></a>Phase 3 : Empêcher le téléchargement de données non protégées vers vos applications

En plus d’empêcher l’exfiltration des données, les organisations veulent souvent s’assurer que les données qui sont infiltrées vers les applications cloud sont également sécurisées. Un cas d’usage courant se présente lorsqu’un utilisateur tente de charger des fichiers qui ne sont pas étiquetés correctement.

Pour toutes les applications que vous avez configurées ci-dessus, vous pouvez configurer une stratégie de session pour empêcher le téléchargement de fichiers qui ne sont pas étiquetés correctement, comme suit :

1. Créez une stratégie de session pour [bloquer les téléchargements de fichiers dont l’étiquette est incorrecte](session-policy-aad.md#protect-upload).

1. Configurez une stratégie pour afficher un [message de bloc avec des instructions sur la façon de corriger l’étiquette et réessayez](session-policy-aad.md#educate-protect).

La protection des chargements de fichiers de cette façon garantit que les données enregistrées dans le cloud disposent des autorisations d’accès appropriées. En cas de perte ou de partage d’un fichier, les utilisateurs autorisés peuvent y accéder uniquement.
