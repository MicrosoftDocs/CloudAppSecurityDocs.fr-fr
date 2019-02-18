---
title: Découvrir et gérer l’informatique fantôme | Microsoft Docs
description: Ce didacticiel décrit le processus d’application automatique des étiquettes de classification Azure Information Protection dans Microsoft Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 1/28/2019
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: eac0b192-98d7-4939-9a07-1d4a7f8c39c3
ms.reviewer: dannyk
ms.suite: ems
ms.openlocfilehash: 748d4daa5f3ca47b652888ee382bc22eff0f340c
ms.sourcegitcommit: 8ef0438fa35916c48625ff750cb85e9628d202f2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56281772"
---
*S’applique à : Microsoft Cloud App Security*


# <a name="tutorial-discover-and-manage-shadow-it-in-your-network"></a>Didacticiel : Découvrir et gérer l’informatique fantôme sur votre réseau

Lorsque les administrateurs informatiques doivent dire combien d’applications cloud ils pensent que leurs employés utilisent en moyenne, leur réponse est généralement 30 ou 40, alors qu’en réalité, la moyenne est de plus de 1 000 applications distinctes utilisées par les employés de votre organisation. L’informatique fantôme vous aide à savoir quelles applications sont utilisées et à les identifier, mais aussi à connaître votre niveau de risque. 80 % des employés utilisent des applications non approuvées que personne n’a analysées et qui ne sont peut-être pas conformes à vos stratégies de sécurité et de conformité. Étant donné que vos employés sont en mesure d’accéder à vos ressources et applications en dehors de votre réseau d’entreprise, il n’est plus suffisant de mettre en place des règles et stratégies sur vos pare-feu. 

Ce didacticiel fournit des instructions sur l’utilisation de Cloud Discovery pour découvrir les applications utilisées, analyser le risque qu’elles représentent, configurer des stratégies pour identifier les nouvelles applications à risque qui sont exécutées et empêcher l’approbation de ces applications, afin de les bloquer en mode natif à l’aide de votre appliance de pare-feu ou de proxy.

> [!div class="checklist"]
> * Découvrir et identifier l’informatique fantôme
> * Évaluer et analyser
> * Gérer vos applications
> * Contrôler les applications approuvées
 
## <a name="how-to-discover-and-manage-shadow-it-in-your-network"></a>Comment découvrir et gérer l’informatique fantôme sur votre réseau

Utilisez ce processus pour déployer la solution Cloud Discovery pour l’informatique fantôme dans votre organisation.

![cycle de vie de l’informatique fantôme](./media/shadow-it-lifecycle.png)

### <a name="phase-1-discover-and-identify-shadow-it"></a>Phase 1 : Découvrir et identifier l’informatique fantôme
    
1. **Découvrir l’informatique fantôme** : Identifiez la position de votre organisation en matière de sécurité en exécutant Cloud Discovery dans votre organisation pour voir ce qui se passe réellement sur votre réseau. Pour plus d’informations, voir [Configurer Cloud Discovery](set-up-cloud-discovery.md). Pour ce faire, utilisez l’une des méthodes suivantes :
   
    - Soyez opérationnel rapidement avec Cloud Discovery en l’intégrant à [Windows Defender ATP](wdatp-integration.md). Cette intégration native vous permet de commencer immédiatement à collecter des données sur le trafic cloud sur vos appareils Windows 10, sur votre réseau et en dehors.
   
    - Pour couvrir tous les appareils connectés à votre réseau, il est important de déployer le [collecteur de journaux Cloud App Security](discovery-docker.md) sur vos pare-feu et autres proxies, afin de collecter des données à partir de vos points de terminaison et de les envoyer à Cloud App Security pour analyse.

   - Intégrez Cloud App Security à votre proxy. Cloud App Security s’intègre en mode natif avec certains proxies tiers, y compris [Zscaler](zscaler-integration.md).
   
 
Étant donné que les stratégies diffèrent en fonction du groupe d’utilisateurs, de la région et du groupe d’entreprise, vous souhaiterez peut-être créer un rapport dédié sur l’informatique fantôme et ce, pour chacune de ces unités. Pour plus d’informations, voir [Docker sur Windows en local](discovery-docker-windows.md#continuous-reports).


Maintenant que Cloud Discovery est en cours d’exécution sur votre réseau, examinez les rapports continus générés et étudiez le [tableau de bord Cloud Discovery](working-with-cloud-discovery-data.md) pour bénéficier d’un aperçu complet des applications utilisées dans votre organisation. Il est judicieux de les examiner par catégorie : vous constaterez souvent que les applications non approuvées sont utilisées à des fins professionnelles légitimes qui ne sont pas couvertes par les applications approuvées. 

2. **Identifier les niveaux de risque de vos applications** : Utilisez le catalogue des applications cloud de Cloud App Security pour analyser dans le détail les risques qu’implique chaque application découverte. Le catalogue des risques de Cloud App Security inclut plus de 16 000 applications, qui sont évaluées selon plus de 70 facteurs de risque. Les facteurs de risque vont des informations générales sur l’application (où se trouve le siège social de l’application, qui en est l’éditeur) aux mesures de sécurité et aux contrôles (prise en charge du chiffrement au repos, existence d’un journal d’audit sur l’activité des utilisateurs). Pour plus d’informations, voir [Utilisation du score de risque](risk-score.md).
    
   - Dans le portail Cloud App Security, sous **Découvrir**, cliquez sur **Applications découvertes**. Filtrez la liste des applications découvertes en cours d’utilisation dans votre organisation selon les facteurs de risque qui vous intéressent. Par exemple, vous pouvez utiliser les filtres avancés pour trouver toutes les applications avec un score de risque inférieur à 8. 

   - Vous pouvez explorer une application pour en savoir plus sur sa conformité en cliquant sur le nom de l’application, puis sur l’onglet **Infos** pour afficher les détails sur les facteurs de risque de sécurité de l’application.
    
### <a name="phase-2-evaluate-and-analyze"></a>Phase 2 : Évaluer et analyser

1. **Évaluer la conformité** : Vérifiez si les applications sont certifiées conformes aux standards de votre organisation, tels que HIPAA, SOC2, RGPD.
   - Dans le portail Cloud App Security, sous **Découvrir**, cliquez sur **Applications découvertes**. Filtrez la liste des applications découvertes dans votre organisation selon les facteurs de risque de conformité qui vous intéressent. Par exemple, utilisez la requête suggérée pour filtrer les applications non conformes.
   - Vous pouvez explorer une application pour en savoir plus sur sa conformité en cliquant sur le nom de l’application, puis sur l’onglet **Infos** pour afficher les détails sur les facteurs de risque de conformité de l’application.

2. **Analyser l’utilisation** : Maintenant que vous savez si vous voulez que l’application soit ou non utilisée dans votre organisation, vous désirez savoir comment elle est utilisée et par qui. Si elle est uniquement utilisée de manière limitée dans votre organisation, ce n’est peut-être pas grave, mais si son utilisation s’étend, vous souhaiterez peut-être en être averti afin de décider si vous voulez la bloquer.
    - Dans le portail Cloud App Security, sous **Découvrir**, cliquez sur **Applications découvertes** et descendez dans la hiérarchie en cliquant sur l’application qui vous intéresse. L’onglet **Utilisation** vous permet de savoir combien d’utilisateurs actifs se servent de l’application et la quantité de trafic qu’elle génère. Vous aurez ainsi un premier aperçu assez clair de ce qui se passe avec cette application. Ensuite, si vous souhaitez voir qui, en particulier, utilise l’application, vous pouvez aller plus loin en cliquant sur **Total Active Users (Nombre total d’utilisateurs actifs)**. Cette étape importante peut vous fournir des informations pertinentes. Par exemple, si vous découvrez que tous les utilisateurs d’une application donnée font partie du service Marketing, il est possible qu’il existe un besoin métier pour cette application, et si l’application présente des risques, il peut être judicieux de discuter avec les employés d’une alternative avant de bloquer l’application.

4. Utilisez le catalogue d’applications cloud et filtrez les applications qui appartiennent à la même catégorie d’applications. À l’aide des filtres avancés, identifiez la solution conforme aux différents contrôles de sécurité requis pour respecter la stratégie de votre organisation.


### <a name="phase-3-manage-your-apps"></a>Phase 3 : Gérer vos applications
    
- **Gérer les applications cloud** : Cloud App Security vous aide à gérer l’utilisation des applications dans votre organisation. Une fois que vous avez identifié les différents modèles et comportements utilisés dans votre organisation, vous pouvez créer de nouvelles balises d’application personnalisées afin de classer chaque application en fonction de son état professionnel ou des besoins auxquels elle répond.
Ces balises peuvent ensuite servir à une surveillance particulière, par exemple pour identifier un trafic élevé vers les applications qui sont marquées comme applications de stockage cloud à risque. Les balises d’application peuvent être gérées sous **Cloud Discovery settings (Paramètres Cloud Discovery)** > **Balises d’application**. Ces balises peuvent ensuite être utilisées pour filtrer le contenu des pages Cloud Discovery et créer des stratégies.

- **Supervision continue** : Maintenant que vous avez examiné soigneusement les applications, vous souhaiterez peut-être définir des stratégies qui les surveillent et offrent des fonctionnalités de contrôle lorsque cela est nécessaire.

Il est maintenant temps de créer des stratégies afin que vous soyez automatiquement alerté en cas d’événement pertinent pour vous. Par exemple, vous pouvez créer une **stratégie de découverte d’application** qui vous préviendra si un pic survient dans les téléchargements ou le trafic en provenance d’une application donnée. Vous pouvez définir la stratégie pour être averti par e-mail ou SMS. Pour plus d’informations, voir la [référence de modèle de stratégie](policy-template-reference.md) et les informations complémentaires sur les [stratégies Cloud Discovery](cloud-discovery-policies.md).


Configurez les [**stratégies de découverte des applications**](cloud-discovery-policies.md). Par exemple, vous devez activer les fonctions **Comportement anormal par des utilisateurs découverts**, **Vérification de conformité des applications de stockage cloud** et **Nouvelle application à risques**.


Consultez la page des alertes et utilisez le filtre du **type de stratégie** pour afficher les alertes de découverte d’application. Pour les applications qui ont été trouvées par vos stratégies de découverte d’application, il est recommandé d’effectuer une analyse approfondie pour en savoir plus sur les raisons professionnelles qui justifient l’utilisation de l’application, par exemple en contactant les utilisateurs des applications. Répétez ensuite les étapes de la phase 2 pour évaluer le risque que représente l’application. Déterminez les étapes suivantes pour l’application, que vous en approuviez l’utilisation ou que vous souhaitiez la bloquer la prochaine fois qu’un utilisateur y accède, auquel cas vous devez la marquer comme non approuvée afin qu’elle puisse être bloquée par votre pare-feu, votre proxy ou la passerelle web sécurisée. 


### <a name="phase-4-control-sanctioned-apps"></a>Phase 4 : Contrôler les applications approuvées

1. Pour activer le contrôle d’application via des API, [connectez des applications via une API](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) (enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) pour la surveillance continue.

2. Protégez les applications à l’aide du [contrôle d’application par accès conditionnel](proxy-intro-aad.md).


La nature des applications cloud implique qu’elles sont mises à jour quotidiennement et que de nouvelles applications apparaissent tout le temps. Pour cette raison, les employés utilisent en permanence de nouvelles applications et il est important de sans cesse surveiller, réviser et mettre à jour vos stratégies, en vérifiant les applications exploitées par vos utilisateurs, ainsi que leurs modèles d’utilisation et de comportement. Vous pouvez toujours accéder au tableau de bord Cloud Discovery et voir les nouvelles applications utilisées. Suivez alors de nouveau les instructions de cet article pour vous assurer que votre organisation et vos données sont protégées.


## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  
