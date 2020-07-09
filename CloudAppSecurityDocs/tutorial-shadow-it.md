---
title: Découvrir et gérer le Shadow IT
description: Ce tutoriel décrit le processus d’application automatique d’étiquettes de classification Azure Information Protection dans Microsoft Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 06/29/2020
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: dannyk
ms.suite: ems
ms.openlocfilehash: 2a9ef4658cb363e98397341faffc69d6c961808f
ms.sourcegitcommit: b15034dd50142afd8e95de22a9232f711b1eae6e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85624928"
---
# <a name="tutorial-discover-and-manage-shadow-it-in-your-network"></a>Tutoriel : Découvrir et gérer le Shadow IT

*S’applique à : Microsoft Cloud App Security*

À la question « Combien d’applications cloud vos employés utilisent-ils ? », les administrateurs informatiques avancent en moyenne le nombre de 30 ou 40. Or, dans la réalité, ce sont plus de 1 000 applications distinctes qui sont utilisées par les employés d’une grande entreprise. Le Shadow IT vous aide à identifier les applications qui sont utilisées ainsi que le niveau de risque associé. 80 % des employés utilisent des applications non approuvées qui n’ont fait l’objet d’aucun examen et qui peuvent ne pas être conformes à vos stratégies de sécurité et de conformité. Et sachant que vos employés peuvent accéder à vos ressources et applications en dehors de votre réseau d’entreprise, il ne suffit plus de définir des règles et des stratégies sur vos pare-feu.

Ce tutoriel explique comment utiliser Cloud Discovery pour découvrir les applications utilisées, explorer les risques liés à ces applications, configurer des stratégies permettant d’identifier les nouvelles applications à risque parmi celles utilisées et désapprouver ces applications de façon à les bloquer en mode natif à partir de votre appliance de proxy ou de pare-feu.

> [!div class="checklist"]
>
> * Découvrir et identifier Shadow IT
> * Évaluer et analyser
> * Gérer vos applications
> * Génération de rapports Shadow IT Discovery avancés
> * Contrôler les applications approuvées

## <a name="how-to-discover-and-manage-shadow-it-in-your-network"></a>Comment découvrir et gérer le Shadow IT dans votre réseau

Utilisez ce processus pour déployer le Shadow IT Cloud Discovery dans votre organisation.

![Cycle de vie du Shadow IT](media/shadow-it-lifecycle.png)

### <a name="phase-1-discover-and-identify-shadow-it"></a>Phase 1 : Découvrir et identifier Shadow IT

1. **Découvrir le Shadow IT** : Déterminez quelle est la situation de votre organisation sur le plan de la sécurité en exécutant Cloud Discovery dans votre organisation et voyez ce qu’il se passe réellement dans votre réseau. Pour plus d’informations, voir [Configurer Cloud Discovery](set-up-cloud-discovery.md). Pour cela, utilisez l’une des méthodes suivantes :

    * Soyez opérationnel rapidement avec Cloud Discovery en l’intégrant à [Microsoft Defender ATP](wdatp-integration.md). Cette intégration native vous permet de commencer immédiatement à collecter des données sur le trafic cloud pour l’ensemble de vos appareils Windows 10, à l’intérieur et à l’extérieur de votre réseau.

    * Pour englober tous les appareils connectés à votre réseau, il est important de déployer le [collecteur de journaux Cloud App Security](discovery-docker.md) sur vos pare-feu et autres proxys pour collecter les données de vos points de terminaison et les envoyer à Cloud App Security à des fins d’analyse.

    * Intégrez Cloud App Security à votre proxy. Cloud App Security s’intègre en mode natif à certains proxys tiers, notamment [Zscaler](zscaler-integration.md).

Dans la mesure où les stratégies varient en fonction des groupes d’utilisateurs, des régions et des groupes de l’entreprise, vous pouvez créer un rapport Shadow IT dédié pour chacune de ces unités. Pour plus d’informations, consultez [Docker sur Windows en local](discovery-docker-windows.md#continuous-reports).

Maintenant que Cloud Discovery s’exécute sur votre réseau, examinez les rapports générés en continu et consultez le [tableau de bord Cloud Discovery](working-with-cloud-discovery-data.md) pour obtenir une vision globale des applications qui sont actuellement utilisées dans votre organisation. Il est judicieux de les examiner par catégorie, car vous constaterez souvent que les applications non approuvées sont utilisées à bon escient dans le cadre du travail et qu’aucune application approuvée ne répondait à ce besoin.

1. **Identifier le niveau de risque de vos applications** : Utilisez le catalogue des applications cloud de Cloud App Security pour analyser dans le détail les risques qu’implique chaque application découverte. Le catalogue des risques de Cloud App Security inclut plus de 16 000 applications, qui sont évaluées selon plus de 80 facteurs de risque. Pour commencer, les informations générales sur l’application (origine géographique de l’application, nom de l’éditeur) peuvent donner des indications sur les risques, tout comme les mesures et les contrôles de sécurité (prise en charge du chiffrement au repos, présence d’un journal d’audit de l’activité des utilisateurs). Pour plus d’informations, consultez [Utilisation des scores de risque d’application](risk-score.md).

    * Sur le portail Cloud App Security, sous **Découvrir**, cliquez sur **Applications découvertes**. Filtrez la liste des applications découvertes dans votre organisation selon les facteurs de risque qui vous intéressent. Par exemple, vous pouvez utiliser les filtres avancés pour rechercher toutes les applications dont le score de risque est inférieur à 8.

    * Vous pouvez explorer une application pour mieux évaluer sa conformité en cliquant sur le nom de l’application, puis sur l’onglet **Infos** pour afficher des détails sur les facteurs de risque de sécurité de l’application.

### <a name="phase-2-evaluate-and-analyze"></a>Phase 2 : Évaluer et analyser

1. **Évaluer la conformité** : Vérifiez si les applications sont certifiées conformes aux standards de votre organisation, comme HIPAA, SOC2, RGPD.

    * Sur le portail Cloud App Security, sous **Découvrir**, cliquez sur **Applications découvertes**. Filtrez la liste des applications découvertes dans votre organisation selon les facteurs de risque de conformité qui vous intéressent. Par exemple, utilisez la requête suggérée pour filtrer les applications non conformes.

    * Vous pouvez explorer une application pour en savoir plus sur sa conformité en cliquant sur le nom de l’application, puis sur l’onglet **Infos** pour afficher les détails sur les facteurs de risque de conformité de l’application.

    > [!TIP]
    > Recevez une notification lorsqu’une application découverte est associée à une violation de sécurité récemment publiée à l’aide de l’alerte intégrée **Violation de la sécurité de l’application découverte**. Investiguez tous les utilisateurs, les adresses IP et les appareils qui accèdent à l’application violée au cours des 90 derniers jours, puis appliquez les contrôles appropriés.

1. **Analyser l’utilisation** : Maintenant que vous êtes décidé à autoriser l’utilisation de l’application dans votre organisation, vous devez déterminer qui l’utilise et de quelle façon. Si une utilisation limitée dans votre organisation n’est pas de nature à vous inquiéter, peut-être souhaiterez-vous être notifié d’une utilisation croissante de l’application de façon à la bloquer, le cas échéant.

    * Sur le portail Cloud App Security, sous **Découvrir**, cliquez sur **Applications découvertes**, puis explorez l’application qui vous intéresse en cliquant sur son nom. L’onglet **Utilisation** vous permet de déterminer le nombre d’utilisateurs actifs de l’application ainsi que la quantité de trafic qu’elle génère. Vous pouvez ainsi déjà vous faire une idée assez précise de l’activité liée à l’application. Ensuite, si vous voulez savoir précisément qui utilise l’application, vous pouvez faire une exploration plus poussée en cliquant sur **Nombre total d’utilisateurs actifs**. Cette étape importante peut vous livrer des informations intéressantes. Par exemple, si vous découvrez que les utilisateurs d’une même application font tous partie du service Marketing, vous pourrez en déduire qu’elle correspond à un besoin, et si elle présente un risque, vous pourrez leur proposer une solution alternative avant de bloquer l’application.

    * Explorez encore plus en détail lors de l’examen de l’utilisation des applications découvertes. Affichez les sous-domaines et les ressources pour en savoir plus sur les activités spécifiques, l’accès aux données et l’utilisation des ressources dans vos services cloud. Pour plus d’informations, consultez [Examen approfondi des applications découvertes](discovered-apps.md#deep-dive-into-discovered-apps) et [Découvrir les ressources et les applications personnalisées](discovered-apps.md#discover-resources-and-custom-apps).

1. **Identifier les autres applications** : Utilisez le catalogue d’applications cloud et filtrez les applications qui appartiennent à la même catégorie d’applications. À l’aide des filtres avancés, identifiez les solutions conformes aux différents contrôles de sécurité requis pour respecter la stratégie de votre organisation.

### <a name="phase-3-manage-your-apps"></a>Phase 3 : Gérer vos applications

* **Gérer les applications cloud** : Cloud App Security vous aide à gérer l’utilisation des applications dans votre organisation. Une fois que vous aurez identifié les différentes caractéristiques et les différents comportements qui ont cours dans votre organisation, vous pourrez créer de nouvelles balises d’application personnalisées afin de classifier chaque application en fonction de son statut ou de sa justification métier. Ces balises pourront ensuite être utilisées à des fins de supervision spécifiques, par exemple, pour identifier un trafic important à destination d’applications marquées comme étant des applications de stockage cloud risquées. Les balises d’application peuvent être gérées sous **Paramètres de Cloud Discovery** > **Balises d’application**. Ces balises peuvent servir par la suite à filtrer les pages Cloud Discovery et à créer des stratégies à partir de celles-ci.

* **Gérer les applications découvertes à l’aide de la galerie Azure Active Directory (Azure AD)** <a name ="gallery-apps"></a> : Cloud App Security tire également parti de son intégration native avec Azure AD pour vous permettre de gérer vos applications découvertes dans la galerie Azure AD. Pour les applications qui figurent déjà dans la galerie Azure AD, vous pouvez appliquer l’authentification unique et gérer l’application avec Azure AD. Pour ce faire, sur la ligne où l’application appropriée s’affiche, choisissez les trois points à la fin de la ligne, puis **Gérer l’application avec Azure AD**.

    ![Cycle de vie du Shadow IT](media/manage-app-in-azure-ad-gallery.png)

* **Supervision continue** : Après avoir mené une enquête minutieuse sur les applications, vous pouvez souhaiter définir des stratégies en vue de superviser ces applications et en assurer le contrôle, si nécessaire.

Le moment est venu de créer des stratégies qui vous alerteront automatiquement dès que des événements préoccupants se produiront. Par exemple, vous pouvez souhaiter créer une **stratégie de découverte d’application** qui vous informe qu’un pic de téléchargements ou de trafic a été atteint par une application dont vous vous souciez. Pour cela, vous devez activer les fonctions **Comportement anormal par des utilisateurs découverts**, **Vérification de conformité des applications de stockage cloud** et **Nouvelle application à risques**. Vous devez également définir la stratégie pour être averti par e-mail ou SMS. Pour plus d’informations, voir la [référence de modèle de stratégie](policy-template-reference.md), les informations complémentaires sur les [stratégies Cloud Discovery](cloud-discovery-policies.md), et configurer les [Stratégies Cloud Discovery](cloud-discovery-policies.md).

Accédez à la page d’alertes et utilisez le filtre **Type de stratégie** pour examiner les alertes de découverte d’application. Pour les applications qui ont été trouvées par vos stratégies de découverte d’application, il est recommandé d’effectuer une analyse approfondie pour en savoir plus sur les raisons professionnelles qui justifient l’utilisation de l’application, par exemple en contactant les utilisateurs de l’application. Répétez ensuite les étapes de la Phase 2 pour évaluer le risque de l’application. Décidez ensuite des prochaines étapes concernant l’application, que vous approuviez son utilisation future ou que vous décidiez de la bloquer la prochaine fois qu’un utilisateur y accédera. Auquel cas, vous devrez la marquer comme étant non approuvée pour qu’elle puisse être bloquée par le pare-feu, le proxy ou la passerelle web sécurisée de votre organisation. Pour plus d’informations, consultez [Intégrer avec Microsoft Defender ATP](wdatp-integration.md#block-access-to-unsanctioned-cloud-apps), [Intégrer avec Zscaler](zscaler-integration.md), [Intégrer à iboss](iboss-integration.md)et [Exporter un script de blocage pour gouverner les applications découvertes](governance-discovery.md#export-a-block-script-to-govern-discovered-apps).

### <a name="phase-4-advanced-shadow-it-discovery-reporting"></a>Phase 4 : Génération de rapports Shadow IT Discovery avancés

En plus des options de création de rapports disponibles dans Cloud App Security, vous pouvez intégrer des journaux Cloud Discovery dans Azure Sentinel pour approfondir l’enquête et l’analyse. Une fois les données dans Azure Sentinel, vous pouvez les afficher dans des tableaux de bord, exécuter des requêtes à l’aide du langage de requête Kusto, exporter des requêtes vers Microsoft Power BI, les intégrer à d’autres sources et créer des alertes personnalisées. Pour plus d’informations, consultez [Intégration Azure Sentinel](siem-sentinel.md).

### <a name="phase-5-control-sanctioned-apps"></a>Phase 5 : Contrôler les applications approuvées

1. Pour activer le contrôle d’application via des API, [connectez les applications via l’API](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) pour la surveillance continue.

2. Protégez les applications à l’aide du [contrôle d’application par accès conditionnel](proxy-intro-aad.md).

Du fait de leur nature, les applications sont mises à jour quotidiennement et de nouvelles applications se font jour en permanence. De ce fait, les employés utilisent constamment de nouvelles applications et il est important de suivre, examiner et mettre à jour les stratégies, en étant attentif aux applications dont se servent vos utilisateurs ainsi qu’à leurs modèles d’utilisation et de comportement. Vous pouvez toujours accéder au tableau de bord Cloud Discovery pour identifier les nouvelles applications utilisées et suivre les instructions fournies dans cet article encore une fois pour veiller à la protection de votre organisation et de vos données.

## <a name="see-also"></a>Voir aussi

> [!div class="nextstepaction"]
> [Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]  
