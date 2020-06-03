---
title: Découvrir et protéger les informations sensibles dans votre organisation
description: Ce tutoriel décrit le processus de découverte et de protection des informations sensibles dans Microsoft Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 05/26/2020
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.suite: ems
ms.openlocfilehash: c0ba4e4271b39adf3fa574459c15641bce5b3c26
ms.sourcegitcommit: 7b6124e5ecb3fa8fc1176d89e06b052f2a53a310
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83856092"
---
# <a name="tutorial-discover-and-protect-sensitive-information-in-your-organization"></a>Tutoriel : Découvrir et protéger les informations sensibles dans votre organisation

*S’applique à : Microsoft Cloud App Security*

Dans un monde idéal, tous vos employés comprennent l’importance de la protection des données et respectent vos stratégies. Dans le monde réel, il est probable qu’un partenaire occupé qui travaille fréquemment avec des informations de comptabilité charge par inadvertance un document sensible sur votre référentiel Box avec des autorisations incorrectes. Une semaine plus tard, vous réalisez que les informations confidentielles de votre entreprise ont été divulguées à la concurrence.

Pour éviter ce problème, Microsoft Cloud App Security vous fournit une suite complète de fonctionnalités DLP qui couvrent les différents points de fuite de données qui existent dans les organisations.

Ce tutoriel vous fournit une vue d’ensemble et des instructions pour l’utilisation de Cloud App Security afin de découvrir des données sensibles potentiellement exposées et d’appliquer des contrôles pour empêcher leur exposition.

> [!div class="checklist"]
>
> * Découvrir vos données
> * Classer les informations sensibles
> * Protection de vos données
> * Surveiller vos données et créer des rapports

## <a name="how-to-discover-and-protect-sensitive-information-in-your-organization"></a>Guide pratique pour découvrir et protéger les informations sensibles dans votre organisation

Notre approche de la protection des informations peut être divisée selon les phases suivantes qui vous permettent de protéger vos données tout au long de leur cycle de vie, sur plusieurs emplacements et appareils.

![Cycle de vie du Shadow IT](media/tutorial-dlp-solution.png)

### <a name="phase-1-discover-your-data"></a>Phase 1 : Découvrir vos données

1. **Connecter des applications** : La première étape de la découverte des données utilisées dans votre organisation consiste à connecter les applications cloud utilisées dans votre organisation à Cloud App Security. Une fois connecté, Cloud App Security peut analyser les données, ajouter des classifications et appliquer des stratégies et des contrôles. La manière dont les applications sont connectées affecte le mode d’application des analyses et des contrôles, ainsi que leur chronologie. Vous pouvez connecter vos applications de l’une des manières suivantes :

    * **Utiliser un connecteur d’application** : Nos connecteurs d’applications utilisent les API fournies par les fournisseurs d’applications. Ils offrent une visibilité et un contrôle améliorés sur les applications utilisées dans votre organisation. Les analyses sont effectuées périodiquement (toutes les 12 heures) et en temps réel (déclenchées à chaque fois qu’une modification est détectée). Pour plus d’informations et pour obtenir des instructions sur l’ajout d’applications, consultez [Connexion d’applications](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).
    * **Utiliser le contrôle d’application par accès conditionnel** : Notre solution de contrôle d’application par accès conditionnel utilise une architecture de proxy inverse qui est intégrée de manière unique avec l’accès conditionnel Azure Active Directory (AD). Une fois configurés dans Azure AD, les utilisateurs sont acheminés vers Cloud App Security où les stratégies d’accès et de session sont appliquées pour protéger les données que les applications tentent d’utiliser. Cette méthode de connexion vous permet d’appliquer des contrôles à [n’importe quelle application](proxy-deployment-any-app.md). Pour plus d’informations, consultez [Protéger des applications avec le contrôle d’application par accès conditionnel Cloud App Security](proxy-intro-aad.md).

1. **Examiner** : Une fois qu’une application est connectée à Cloud App Security avec son connecteur d’API, Cloud App Security analyse tous les fichiers qu’elle utilise. Vous pouvez alors accéder à la page d’investigation du fichier (**Examiner** > **Fichiers**) pour obtenir une vue d’ensemble des fichiers partagés par vos applications cloud, leur accessibilité et leur état. Pour plus d’informations, consultez [Examiner des fichiers](file-filters.md).

### <a name="phase-2-classify-sensitive-information"></a>Phase 2 : Classer les informations sensibles

1. **Définir les informations sensibles** : Avant de rechercher des informations sensibles dans vos fichiers, vous devez d’abord définir ce qui est sensible pour votre organisation. Dans le cadre de notre [service de classification des données](dcs-inspection.md), nous offrons plus de 100 types d’informations sensibles prêts à l’emploi, ou vous pouvez [créer vos propres types](/microsoft-365/compliance/create-a-custom-sensitive-information-type) pour les adapter à la stratégie de votre entreprise. **Cloud App Security est intégré en mode natif à Microsoft Information Protection** et les mêmes étiquettes et types sensibles sont disponibles dans les deux services. Ainsi, lorsque vous souhaitez définir des informations sensibles, accédez au portail Microsoft Information Protection pour les créer, et une fois définies, elles seront disponibles dans Cloud App Security. Vous pouvez également utiliser des types de classifications avancés, comme l’empreinte digitale ou la correspondance exacte des données (EDM).

    Pour ceux d’entre vous qui ont déjà effectué le travail difficile consistant à identifier les informations sensibles et à appliquer les étiquettes de sensibilité appropriées, vous pouvez utiliser ces étiquettes dans vos stratégies sans avoir à relancer l’analyse du contenu.
1. **Activer l’intégration Azure Information Protection**
    1. Dans Cloud App Security, sous la roue dentée Paramètres, sélectionnez la page **Paramètres** sous l’en-tête **Système**.
    1. Sous **Azure Information Protection**, sélectionnez **Analyser automatiquement les nouveaux fichiers pour détecter les étiquettes de classification Azure Information Protection**.

    Pour plus d’informations, consultez [Intégration d’Azure Information Protection](azip-integration.md).
1. **Créer des stratégies pour identifier les informations sensibles dans les fichiers** : Une fois que vous connaissez les types d’informations que vous souhaitez protéger, il est temps de créer des stratégies pour les détecter. Commencez par créer les stratégies suivantes :

    **Stratégie de fichier**  
    Utilisez ce type de stratégie pour analyser le contenu des fichiers stockés dans vos applications cloud connectées par API en temps quasi réel et les données au repos. Les fichiers sont analysés à l’aide de l’une de nos méthodes d’inspection prises en charge, notamment **Contenu chiffré Azure Information Protection** grâce à son **intégration native** avec Cloud App Security.

    1. Accédez à **Contrôle** > **Stratégies**, cliquez sur **Créer une stratégie**, puis sélectionnez **Stratégie de fichier**.
    1. Sous **Méthode d’inspection**, choisissez et configurez l’un des services de classification suivants :

        * **[Services de classification des données](dcs-inspection.md)** : Utilise les décisions de classification que vous avez prises dans Office 365, Azure Information Protection et Cloud App Security pour fournir une expérience d’étiquetage unifiée. Il s’agit de la méthode d’inspection de contenu par défaut, car elle offre une expérience cohérente et unifiée pour les produits Microsoft.
        * **[DLP intégré](content-inspection-built-in.md)** : Inspecte les fichiers pour obtenir des informations sensibles à l’aide de notre moteur d’inspection de contenu DLP intégré.
        * **[Intégration DLP externe](icap-stunnel.md)** : Pour les entreprises souhaitant utiliser leurs propres solutions DLP tierces, les stratégies de fichiers Cloud App Security peuvent diriger en toute sécurité les fichiers à inspecter vers votre solution DLP externe via un serveur ICAP.

    1. Pour les fichiers très sensibles, sélectionnez **Créer une alerte** et choisissez les alertes dont vous avez besoin pour être informé de la présence de fichiers contenant des informations sensibles non protégées dans votre organisation.
    1. Cliquez sur **Créer**.

    **Stratégie de session**  
    Utilisez ce type de stratégie pour analyser et protéger les fichiers en temps réel lors de l’accès à :

    * **Empêcher l’exfiltration de données** : Bloquer les opérations télécharger, couper, copier et imprimer sur les documents sensibles, par exemple sur les appareils non managés.
    * **Protéger les fichiers lors du téléchargement** : Exiger l’étiquetage et la protection des documents avec Azure Information Protection. Cette action garantit que le document est protégé et que l’accès utilisateur est limité dans une session potentiellement risquée.
    * **Empêcher le chargement de fichiers sans étiquette** : Exiger qu’un fichier dispose de l’étiquette et de la protection appropriées avant qu’un fichier sensible soit chargé, distribué et utilisé par d’autres personnes. Avec cette action, vous pouvez vous assurer que le chargement des fichiers sans étiquette avec du contenu sensible est bloqué jusqu’à ce que l’utilisateur puisse classifier le contenu.

    1. Accédez à **Contrôle** > **Stratégies**, cliquez sur **Créer une stratégie**, puis sélectionnez **Stratégie de session**.
    1. Sous **Type de contrôle de session**, choisissez l’une des options avec DLP.
    1. Sous **Méthode d’inspection**, choisissez et configurez l’un des services de classification suivants :

        * **[Services de classification des données](dcs-inspection.md)** : Utilise les décisions de classification que vous avez prises dans Office 365, Azure Information Protection et Cloud App Security pour fournir une expérience d’étiquetage unifiée. Il s’agit de la méthode d’inspection de contenu par défaut, car elle offre une expérience cohérente et unifiée pour les produits Microsoft.
        * **[DLP intégré](content-inspection-built-in.md)** : Inspecte les fichiers pour obtenir des informations sensibles à l’aide de notre moteur d’inspection de contenu DLP intégré.

    1. Pour les fichiers très sensibles, sélectionnez **Créer une alerte** et choisissez les alertes dont vous avez besoin pour être informé de la présence de fichiers contenant des informations sensibles non protégées dans votre organisation.
    1. Cliquez sur **Créer**.

Vous devez créer autant de stratégies que nécessaire pour détecter les données sensibles en conformité avec la stratégie de votre entreprise.

### <a name="phase-3-protect-your-data"></a>Phase 3 : Protection de vos données

Désormais, vous pouvez détecter des fichiers contenant des informations sensibles, mais ce que vous voulez vraiment c’est protéger ces informations contre les menaces potentielles. Une fois que vous avez pris connaissance d’un incident, vous pouvez corriger manuellement la situation ou vous pouvez utiliser l’une des actions de gouvernance automatiques fournies par Cloud App Security pour sécuriser vos fichiers. Les actions incluent, sans s’y limiter, les contrôles natifs Azure Information Protection, les actions fournies par l’API et l’analyse en temps réel. Le type de gouvernance que vous pouvez appliquer dépend du type de stratégie que vous configurez, comme suit :

1. **[Actions de gouvernance de stratégie de](governance-actions.md#file-governance-actions) fichier** : Utilise l’API du fournisseur d’applications cloud et nos intégrations natives pour sécuriser les fichiers, notamment :
    * Déclencher des alertes et envoyer des notifications par e-mail sur l’incident
    * Gérer les étiquettes appliquées à un fichier pour appliquer les contrôles Azure Information Protection natifs
    * Modifier l’accès en partage à un fichier
    * Mettre un fichier en quarantaine
    * Supprimer des autorisations de fichier ou de dossier spécifiques dans Office 365
    * Déplacer un fichier vers le dossier Corbeille

1. **Contrôles de stratégie de session** : Utilise des fonctionnalités de proxy inverse pour protéger les fichiers, notamment :
    * Déclencher des alertes et envoyer des notifications par e-mail sur l’incident
    * [Surveiller toutes les activités](session-policy-aad.md#monitor-session) : Autorise explicitement le téléchargement ou le chargement de fichiers et surveille toutes les activités associées.
    * [Bloquer](session-policy-aad.md#block-download) : Bloque explicitement le téléchargement ou le chargement de fichiers. Utilisez cette option pour protéger les fichiers sensibles de votre organisation contre les exfiltrations ou les infiltrations de n’importe quel appareil, notamment les appareils non managés.
    * [Protéger](session-policy-aad.md#protect-download) : Applique automatiquement une étiquette de classification aux fichiers qui correspondent aux filtres du fichier de la stratégie. Utilisez cette option pour protéger le téléchargement de fichiers sensibles.

### <a name="phase-4-monitor-and-report-on-your-data"></a>Phase 4 : Surveiller vos données et créer des rapports

Vos stratégies sont toutes en place pour inspecter et protéger vos données. À présent, vous souhaitez [vérifier votre tableau de bord](daily-activities-to-protect-your-cloud-environment.md#check-the-dashboard) quotidiennement pour voir quelles nouvelles alertes ont été déclenchées. C’est un bon endroit pour garder un œil sur l’intégrité de votre environnement cloud. Votre tableau de bord vous permet de vous faire une idée de ce qui se passe et, si nécessaire, de lancer une [investigation](investigate.md).

L’une des méthodes les plus efficaces pour analyser les incidents de fichiers sensibles consiste à passer à la page **Stratégies** et à vérifier les correspondances pour les stratégies que vous avez configurées. En outre, si vous avez configuré des alertes, vous devez également envisager de surveiller régulièrement les alertes de fichier en accédant à la page **Alertes**, en spécifiant la catégorie comme **DLP** et en vérifiant les stratégies liées aux fichiers qui sont déclenchées. L’examen de ces incidents peut vous aider à affiner vos stratégies afin de vous concentrer sur les menaces qui présentent un intérêt pour votre organisation.

En conclusion, la gestion des informations sensibles de cette façon garantit que les données enregistrées dans le cloud bénéficient d’une protection maximale contre les exfiltrations et les infiltrations malveillantes. En outre, en cas de perte ou de partage d’un fichier, seuls les utilisateurs autorisés peuvent y accéder.

## <a name="see-also"></a>Voir aussi

> [!div class="nextstepaction"]
> [Fonctionnement des filtres et des données de fichier](file-filters.md)

> [!div class="nextstepaction"]
> [Stratégies de fichier](data-protection-policies.md)

> [!div class="nextstepaction"]
> [Inspection du contenu](content-inspection.md)

> [!div class="nextstepaction"]
> [Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]  
