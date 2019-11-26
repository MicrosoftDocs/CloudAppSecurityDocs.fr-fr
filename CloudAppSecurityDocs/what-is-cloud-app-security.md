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
ms.openlocfilehash: d96699387b302a30c1ffeffe7712f116d9ca3649
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74459349"
---
# <a name="microsoft-cloud-app-security-overview"></a>Présentation de Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

> [!NOTE]
> Pour plus d’informations sur Office 365 Cloud App Security, consultez [Bien démarrer avec Office 365 Cloud App Security](https://support.office.com/article/Get-started-with-Advanced-Management-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a).

Le passage au cloud donne plus de flexibilité aux employés et aux équipes informatiques. Toutefois, il apporte son lot de nouveaux défis et problématiques quant à la sécurisation de votre organisation. Pour tirer profit des applications cloud et des services, l’équipe informatique doit trouver le juste équilibre entre la prise en charge des accès et la conservation du contrôle pour protéger les données critiques.

Microsoft Cloud App Security est un répartiteur de sécurité d’accès cloud (CASB) qui prend en charge différents modes de déploiement, y compris la collecte de journaux, les connecteurs API et un proxy inverse. Il offre une grande visibilité, un contrôle des déplacements des données, et des analyses sophistiquées pour identifier et combattre les cybermenaces sur l'ensemble de vos services cloud Microsoft et tiers.

Microsoft Cloud App Security s’intègre en mode natif aux principales solutions Microsoft, et il a été conçu en tenant compte des besoins des professionnels de la sécurité. Il fournit un déploiement simple, une gestion centralisée et des capacités d’automatisation innovantes.

Pour plus d’informations sur les licences, consultez la [fiche technique sur les licences Microsoft Cloud App Security](https://aka.ms/mcaslicensing).

## <a name="the-cloud-app-security-framework"></a>Infrastructure de Cloud App Security  

- **Découvrir et contrôler l’utilisation de l’informatique fantôme**: Identifier les applications cloud, IaaS, et les services PaaS utilisés par votre organisation. Examiner les modèles d’utilisation, évaluer les risques et le niveau de préparation de plus de 16 000 applications SaaS face à plus de 80 risques. Commencez à gérer ces éléments pour garantir la sécurité et la conformité.

- **Protection de vos informations sensibles, où qu’elles se trouvent dans le cloud** : Comprenez, classifiez et protégez l’exposition des informations sensibles au repos. Tirez parti des stratégies et des processus automatisés fournis par défaut pour appliquer des contrôles en temps réel dans toutes vos applications cloud.

- **Protection contre les cybermenaces et les anomalies** : Détectez tout comportement inhabituel dans les applications cloud pour identifier les ransomware, les utilisateurs compromis ou les applications non autorisées, analysez l’utilisation à haut risque et corrigez automatiquement les erreurs afin d’en limiter les risques pour votre organisation.

- **Évaluation de la compatibilité de vos applications cloud** : Évaluez si vos applications cloud répondent aux exigences de conformité appropriées, notamment la conformité aux réglementations et normes du secteur. Empêchez les fuites de données pour les applications non conformes, et limitez l’accès aux données réglementées.

## <a name="architecture"></a>Architecture  

Cloud App Security intègre une visibilité à votre cloud :  

- En utilisant Cloud Discovery pour mapper et identifier votre environnement cloud et les applications cloud que votre organisation utilise.
- En approuvant ou non des applications de votre cloud.  
- En utilisant des connecteurs d’application faciles à déployer qui tirent parti des API du fournisseur, ce qui permet une visibilité et une gouvernance des applications auxquelles vous vous connectez.  
- En utilisant une protection du contrôle d’application par accès conditionnel pour obtenir une visibilité en temps réel et contrôler l’accès et les activités effectuées au sein de vos applications cloud.
- En vous offrant un contrôle continu via la définition et l’optimisation permanente de stratégies.  

![Schéma de l’architecture Cloud App Security](./media/proxy-architecture.png)  

### <a name="data-retention--compliance"></a>Conservation des données et conformité

Pour plus d’informations sur la conservation des données et la conformité de Microsoft Cloud App Security, consultez [Sécurité et confidentialité des données Microsoft Cloud App Security](cas-compliance-trust.md).

### <a name="cloud-discovery"></a>Cloud Discovery  

Cloud Discovery utilise vos journaux de trafic pour découvrir et analyser dynamiquement les applications cloud utilisées dans votre organisation. Pour créer un rapport d’instantané sur l’utilisation du cloud de votre organisation, vous pouvez charger manuellement les fichiers journaux à partir de vos pare-feu ou de vos proxys pour une analyse. Pour configurer des rapports en continu, utilisez les collecteurs de journaux de Cloud App Security pour transférer régulièrement vos journaux.  

Pour plus d’informations sur Cloud Discovery, voir [Configurer Cloud Discovery](set-up-cloud-discovery.md).

### <a name="sanctioning-and-unsanctioning-an-app"></a>Approbation et non-approbation d’une application  

Vous pouvez utiliser Cloud App Security pour approuver/ne pas approuver des applications dans votre organisation en utilisant le *catalogue d’applications cloud*. L’équipe d’analystes Microsoft a un catalogue fourni et en constante évolution de plus de 16 000 applications cloud, classées et évaluées selon les standards du secteur. Vous pouvez utiliser le catalogue d’applications cloud pour évaluer les risques pour vos applications cloud selon les certifications réglementaires, les normes du secteur et les bonnes pratiques. Vous pouvez ensuite personnaliser les scores et les pondérations des différents paramètres selon les besoins de votre organisation. En fonction de ces scores, Cloud App Security vous permet de connaître l’indice de risque d’une application. Le scoring est basé sur plus de 80 facteurs de risque susceptibles d’affecter votre environnement.  

### <a name="app-connectors"></a>Connecteurs d’application

Les connecteurs d’application utilisent les API des fournisseurs d’application cloud pour intégrer le cloud Cloud App Security à d’autres applications cloud. Les connecteurs d’application étendent le contrôle et la protection. Ils vous donnent aussi accès aux informations directement à partir des applications cloud, pour une analyse par Cloud App Security.  

Pour connecter une application et étendre la protection, l’administrateur de l’application autorise Cloud App Security à accéder à l’application. Ensuite, Cloud App Security récupère les journaux d’activité de l’application et analyse les données, les comptes et le contenu cloud. Cloud App Security peut appliquer des stratégies, détecter des menaces et appliquer des actions de gouvernance pour résoudre les problèmes.  

Cloud App Security utilise les API fournies par le fournisseur cloud. Chaque application a ses propres limitations de framework et d’API. Cloud App Security fonctionne avec les fournisseurs d’applications pour optimiser l’utilisation des API afin de garantir des performances optimales. Compte tenu des différentes limitations que les applications imposent sur les API (comme les limitations, les limites d’API et les fenêtres d’API de décalage temporel dynamique), les moteurs de Cloud App Security utilisent la capacité autorisée. Certaines opérations, comme l’analyse de tous les fichiers dans le locataire, nécessitent une grande quantité d’API et sont donc réparties sur une période plus longue. Il est normal que certaines stratégies s’exécutent pendant plusieurs heures ou jours.  

### <a name="conditional-access-app-control-protection"></a>Protection du Contrôle d’accès conditionnel aux applications

Le contrôle d’application par accès conditionnel de Microsoft Cloud App Security utilise une architecture de proxy inversée et vous propose les outils dont vous avez besoin pour obtenir une visibilité et un contrôle en temps réel de l’accès à votre environnement cloud et des activités qui y sont effectuées. Avec le Contrôle d’accès conditionnel aux applications, vous pouvez protéger votre organisation :

- Éviter les fuites de données en bloquant les téléchargements avant qu’ils se produisent
- Définir des règles qui forcent le chiffrement des données stockées dans le cloud et téléchargées à partir du cloud
- Obtenir une visibilité sur les points de terminaison non protégés afin de surveiller les opérations réalisées sur les appareils non gérés
- Contrôler l’accès depuis des réseaux hors entreprise ou des adresses IP à risque

### <a name="policy-control"></a>Contrôle de stratégie  

Vous pouvez utiliser des stratégies pour définir le comportement de vos utilisateurs dans le cloud. Utilisez des stratégies pour détecter des comportements à risques, des violations, ou des points de données et des activités suspectes dans votre environnement cloud. Si nécessaire, vous pouvez utiliser des stratégies pour intégrer des processus de correction de façon à réduire complètement les risques. Les types de stratégies sont en corrélation avec les différents types d’informations que vous voulez collecter sur votre environnement cloud et les types d’actions correctives que vous pouvez entreprendre.  

## <a name="related-videos"></a>Vidéos connexes

- [Rejoindre la communauté sur la sécurité](https://channel9.msdn.com/Shows/Microsoft-Security/Join-the-Security-Community)

## <a name="next-steps"></a>Étapes suivantes  

Découvrez les concepts de base dans [Bien démarrer avec Cloud App Security](getting-started-with-cloud-app-security.md).    

[!INCLUDE [Open support ticket](includes/support.md)].   
