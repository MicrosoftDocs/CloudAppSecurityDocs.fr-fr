---
title: Qu’est-ce que Cloud App Security ?
description: Cet article décrit Microsoft Cloud App Security et son fonctionnement.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 8/15/2019
ms.topic: overview
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: d46756b1-7dd8-4190-9799-3a97688f1266
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 49ecd0d844dd30c4816095686a353c301df4fa49
ms.sourcegitcommit: 0b929f7c8feed7dfb40d5294179fd5c6fc079614
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "74720455"
---
# <a name="microsoft-cloud-app-security-overview"></a>Vue d’ensemble de Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

> [!NOTE]
> Pour plus d’informations sur la Sécurité des applications cloud Office 365, consultez [Bien démarrer avec la Sécurité des applications cloud Office 365](https://support.office.com/article/Get-started-with-Advanced-Management-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a).

Le passage au cloud donne plus de flexibilité aux employés et aux équipes informatiques. Toutefois, il apporte également de nouvelles problématiques et rend plus difficile d’assurer la sécurité de l’organisation. Pour tirer profit des applications cloud et des services, l’équipe informatique doit trouver le juste équilibre entre la prise en charge des accès et la conservation du contrôle pour protéger les données critiques.

Microsoft Cloud App Security est un répartiteur de sécurité d’accès cloud (CASB) qui prend en charge différents modes de déploiement, y compris la collecte de journaux, les connecteurs API et un proxy inverse. Il offre une grande visibilité, un contrôle des déplacements des données, et des analyses sophistiquées pour identifier et combattre les cybermenaces sur l'ensemble de vos services cloud Microsoft et tiers.

Microsoft Cloud App Security s’intègre en mode natif aux principales solutions Microsoft, et il a été conçu en tenant compte des besoins des professionnels de la sécurité. Il fournit un déploiement simple, une gestion centralisée et des capacités d’automatisation innovantes.

Pour plus d’informations sur les licences, consultez la fiche [Licences Microsoft Cloud App Security](https://aka.ms/mcaslicensing).

## <a name="the-cloud-app-security-framework"></a>L’infrastructure de Cloud App Security

- **Découvrir et contrôler l’utilisation de l’informatique fantôme**: Identifier les applications cloud, IaaS, et les services PaaS utilisés par votre organisation. Examiner les modèles d’utilisation, évaluer les risques et le niveau de préparation de plus de 16 000 applications SaaS face à plus de 80 risques. Commencez à gérer ces éléments pour garantir la sécurité et la conformité.

- **Protection de vos informations sensibles, où qu’elles se trouvent dans le cloud** : Comprenez, classifiez et protégez l’exposition des informations sensibles au repos. Tirez parti des stratégies et des processus automatisés fournis par défaut pour appliquer des contrôles en temps réel dans toutes vos applications cloud.

- **Protection contre les cybermenaces et les anomalies** : Détectez tout comportement inhabituel dans les applications cloud pour identifier les ransomware, les utilisateurs compromis ou les applications non autorisées, analysez l’utilisation à haut risque et corrigez automatiquement les erreurs afin d’en limiter les risques pour votre organisation.

- **Évaluation de la compatibilité de vos applications cloud** : Évaluez si vos applications cloud répondent aux exigences de conformité appropriées, notamment la conformité aux réglementations et normes du secteur. Empêchez les fuites de données pour les applications non conformes, et limitez l’accès aux données réglementées.

## <a name="architecture"></a>Architecture

Cloud App Security intègre la visibilité à votre cloud de différentes manières :

- Il utilise Cloud Discovery pour mapper et identifier votre environnement cloud et les applications cloud utilisées par votre organisation.
- Il approuve (ou non) des applications dans votre cloud.
- Il utilise des connecteurs d’applications faciles à déployer qui exploitent les API du fournisseur, pour assurer la visibilité et la gouvernance des applications auxquelles vous vous connectez.
- Il utilise la protection du contrôle d’application par accès conditionnel pour offrir une visibilité et un contrôle en temps réel de l’accès et des activités de vos applications cloud.
- Il aide à bénéficier d’un contrôle continu en définissant les stratégies, puis en les ajustant en permanence.

![Diagramme de l’architecture Cloud App Security](media/proxy-architecture.png)

### <a name="data-retention--compliance"></a>Conservation des données et conformité

Pour plus d’informations sur la conservation des données et la conformité Microsoft Cloud App Security, consultez [Sécurité et confidentialité des données Microsoft Cloud App Security](cas-compliance-trust.md).

### <a name="cloud-discovery"></a>Cloud Discovery

Cloud Discovery utilise vos journaux de trafic pour découvrir et analyser dynamiquement les applications cloud utilisés par votre organisation. Pour créer un rapport d’instantané de l’usage du cloud de votre organisation, vous pouvez charger manuellement les fichiers journaux à partir de vos pare-feu ou proxys afin qu’ils soient analysés. Si vous souhaitez configurer des rapports continus, utilisez les collecteurs de journaux Cloud App Security pour transférer régulièrement vos journaux.

Pour plus d’informations, consultez [Configuration de Cloud Discovery](set-up-cloud-discovery.md).

### <a name="sanctioning-and-unsanctioning-an-app"></a>Approbation (ou non) des applications

Vous pouvez utiliser Cloud App Security pour approuver (ou non) des applications dans votre organisation avec le *Catalogue d’applications cloud*. Il s’agit d’un catalogue complet et continuellement alimenté de plus de 16 000 applications cloud classées et évaluées selon les normes du secteur, proposé par l’équipe d’analystes Microsoft. Vous pouvez vous en servir pour évaluer les risques de vos applications cloud en fonction des certifications réglementaires, des normes du secteur et des meilleures pratiques. Ensuite, personnalisez les scores et les pondérations de différents paramètres selon les besoins de votre organisation. En fonction de ces scores, Cloud App Security vous permet de connaître le niveau de risque d’une application. Le scoring est basé sur plus de 80 facteurs de risque susceptibles d’affecter votre environnement.

### <a name="app-connectors"></a>Connecteurs d’applications

Les connecteurs d’applications utilisent les API des fournisseurs d’applications cloud pour intégrer le cloud Cloud App Security avec d’autres applications cloud. Ils étendent le contrôle et la protection. Ils offrent également un accès direct à différentes informations à partir des applications cloud, pour l’analyse Cloud App Security.

Pour connecter une application et étendre la protection, l’administrateur d’application autorise Cloud App Security à accéder à l’application. Ensuite, Cloud App Security interroge l’application pour obtenir les journaux d’activité et analyse les données, les comptes et le contenu cloud. Il peut appliquer des stratégies, détecter les menaces et proposer des actions de gouvernance pour résoudre les problèmes.

Cloud App Security utilise les API fournies par le fournisseur de cloud. Chaque application a sa propre infrastructure et ses propres limitations d’API. Cloud App Security s’efforce d’optimiser l’utilisation des API conjointement avec les fournisseurs d’applications pour garantir des performances optimales. Compte tenu des différentes limitations qu’imposent les applications aux API (par exemple, les limites d’API et les fenêtres d’API de décalage temporel dynamique), les moteurs Cloud App Security exploitent la capacité autorisée. Certaines opérations, comme l’analyse de tous les fichiers dans le client, nécessitent un grand nombre d’API et sont donc réparties sur une longue période. Il est normal que certaines stratégies s’exécutent pendant plusieurs heures ou jours.

### <a name="conditional-access-app-control-protection"></a>Protection du contrôle d’application par accès conditionnel

Grâce à son architecture de proxy inverse, le contrôle d’application par accès conditionnel Microsoft Cloud App Security fournit les outils nécessaires pour bénéficier d’une visibilité et d’un contrôle en temps réel de l’accès et des activités effectuées dans l’environnement cloud. Il vous permet de protéger votre organisation :

- Évitez les fuites de données avant qu’elles ne se produisent en bloquant les téléchargements.
- Définissez des règles qui exigent une protection par chiffrement des données stockées dans le cloud et téléchargées à partir du cloud.
- Détectez plus facilement les points de terminaison non protégés pour pouvoir surveiller les opérations effectuées sur les appareils non gérés.
- Contrôlez les accès provenant de réseaux extérieurs à l’entreprise ou d’adresses IP à risque.

### <a name="policy-control"></a>Contrôle de stratégie

Vous pouvez utiliser des stratégies pour définir le comportement de vos utilisateurs dans le cloud, pour détecter les comportements risqués, les violations ainsi que les activités et points de données suspects dans votre environnement cloud ou, si nécessaire, pour intégrer des processus de correction permettant d’effectuer une atténuation des risques complète. Les types de stratégies correspondent aux différents types d’informations que vous pouvez collecter sur votre environnement cloud et aux types d’actions de correction possibles.

## <a name="related-videos"></a>Vidéos associées

- [Rejoindre la communauté de sécurité](https://channel9.msdn.com/Shows/Microsoft-Security/Join-the-Security-Community)

## <a name="next-steps"></a>Étapes suivantes

Découvrez les concepts de base dans [Bien démarrer avec Cloud App Security](getting-started-with-cloud-app-security.md).

[!INCLUDE [Open support ticket](includes/support.md)].
