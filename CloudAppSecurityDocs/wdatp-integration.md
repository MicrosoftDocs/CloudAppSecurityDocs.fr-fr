---
title: Intégrer Microsoft Defender ATP avec Cloud App Security
description: Cet article explique comment intégrer Microsoft Defender-protection avancée contre les menaces avec Cloud App Security pour une meilleure visibilité de la gestion des risques et de l’informatique cachée.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 7/11/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 90efa85fccd71e488f80db290b09b1636013304b
ms.sourcegitcommit: 6eff466c7a6817b14a60d8c3b2c201c7ae4c2e2c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74720388"
---
# <a name="microsoft-defender-advanced-threat-protection-integration-with-microsoft-cloud-app-security"></a>Intégration de Microsoft Defender-protection avancée contre les menaces avec Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

Microsoft Cloud App Security s’intègre à Microsoft Defender-protection avancée contre les menaces (ATP) en mode natif. L’intégration simplifie le lancement de Cloud Discovery, étend les fonctionnalités de Cloud Discovery au-delà de votre réseau d’entreprise et permet d’effectuer des recherches basées sur la machine. [Microsoft Defender-protection avancée contre les menaces (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) est une plateforme de sécurité pour la protection, la détection, l’investigation et la réponse intelligentes. Microsoft Defender ATP protège les points de terminaison contre les menaces informatiques, détecte les attaques avancées et les violations de données, automatise les incidents de sécurité et améliore la sécurité.

Microsoft Cloud App Security utilise les informations de trafic collectées par Microsoft Defender ATP sur les applications Cloud et les services accessibles à partir d’ordinateurs Windows 10 gérés par le service informatique. L’intégration vous permet d’exécuter Cloud Discovery sur n’importe quelle machine du réseau d’entreprise à l’aide du Wi-Fi public, en cas d’itinérance et d’accès à distance. Elle permet également d’effectuer des recherches basées sur la machine.

Après avoir identifié un utilisateur à risque, vous pouvez vérifier toutes les machines auxquelles l’utilisateur a accédé pour détecter des risques potentiels. Si vous identifiez une machine à risque, vérifiez tous les utilisateurs qui l’ont utilisée pour détecter des risques potentiels. Les journaux de vos points de terminaison routés vers Cloud App Security fournissent des informations utilisateur pour les activités de trafic. L’activité réseau Microsoft Defender ATP fournit le contexte de périphérique. Associez le contexte d’appareil au nom d’utilisateur pour disposer d’une image complète de votre réseau indiquant quel utilisateur a effectué quelle activité et à partir de quelle machine.

Microsoft Cloud App Security utilise l’intégration native avec Microsoft Defender ATP pour exploiter les données sur l’application Cloud et le trafic de service à partir d’appareils Windows gérés. L’intégration est prête à l’emploi et ne nécessite pas de déploiement supplémentaire . Vous ne devez pas router ou mettre en miroir le trafic en provenance de vos points de terminaison ou effectuer des étapes d’intégration complexes.

> [!NOTE]
> Vous souhaitez découvrir Microsoft Defender ATP ? [Inscrivez-vous pour obtenir un essai gratuit](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-assignaccess-abovefoldlink).

## <a name="prerequisites"></a>Conditions préalables

- Licence Microsoft Cloud App Security
- Licence Microsoft Defender ATP
- Windows 10 version 1709 (version du système d’exploitation 16299,1085 avec KB4493441), Windows 10 version 1803 (version du système d’exploitation 17134,704 avec KB4493464), Windows 10 version 1809 (système d’exploitation version 17763,379 avec KB4489899) ou versions ultérieures de Windows 10
- Activer/désactiver **Fonctionnalités d’évaluation** pour activer cette fonctionnalité dans Cloud App Security

## <a name="how-it-works"></a>Fonctionnement

Seul, Cloud App Security collecte des journaux de vos points de terminaison en utilisant des [journaux que vous chargez](create-snapshot-cloud-discovery-reports.md) ou en [configurant le chargement automatique de journaux](discovery-docker.md). L’intégration native vous permet de tirer parti des journaux créés par l’agent Microsoft Defender ATP lorsqu’il s’exécute sur Windows et surveille les transactions réseau. Utilisez ces informations pour la découverte Shadow IT sur les machines Windows de votre réseau.

Pour vous permettre d’effectuer des Cloud Discovery sur d’autres plateformes, il est préférable d’utiliser le [collecteur de journaux](discovery-docker.md)Cloud App Security, ainsi que l’intégration de Microsoft Defender ATP pour surveiller vos ordinateurs Windows 10.

## <a name="how-to-integrate-microsoft-defender-atp-with-cloud-app-security"></a>Intégration de Microsoft Defender ATP à Cloud App Security

Pour activer l’intégration à Cloud App Security à partir de Microsoft Defender ATP :

1. Dans le portail Microsoft Defender ATP, dans le volet de navigation, sélectionnez **préférences configuration**.
2. Dans le menu **Paramètres**, sous **Général**, sélectionnez **Fonctionnalités avancées**.
3. Basculez **Microsoft Cloud App Security** sur **Activé**.
4. Cliquez sur **Enregistrer les préférences**.

>[!NOTE]
> Il faut jusqu’à deux heures après l’activation de l’intégration pour que les données s’affichent dans Cloud App Security.
>

![Paramètres WD ATP](media/wdatp-settings.png)

## <a name="investigate-machines-in-cloud-app-security"></a>Examiner des ordinateurs dans Cloud App Security

Une fois que vous avez intégré Microsoft Defender ATP à Cloud App Security, vous pouvez examiner les données d’ordinateur découvertes dans le tableau de bord Cloud Discovery.

1. Dans le portail Cloud App Security, cliquez sur **Cloud Discovery**, puis sur **Tableau de bord Cloud Discovery**.
2. Dans la barre de navigation supérieure, sous **Rapports continus**, sélectionnez **Utilisateurs de point de terminaison Win10**.
  ![Rapport WD ATP](media/win10-dashboard-report.png)
3. En haut, vous voyez le nombre de machines détectées ajoutées après l’intégration.
4. Cliquez sur l’onglet **Ordinateurs**.
5. Vous pouvez explorer chaque machine répertoriée et utiliser les onglets pour afficher les données de la recherche. Recherchez des corrélations entre les machines, les utilisateurs, les adresses IP et les applications qui ont été impliqués dans des incidents :

    - **Vue d’ensemble**
        - Transactions : informations sur le nombre de transactions qui ont eu lieu sur l’ordinateur pendant la période sélectionnée.
        - Trafic total : informations sur la quantité totale de trafic (en Mo) sur la période sélectionnée.
        - Charge : informations sur la quantité totale de trafic (en Mo) téléchargée par l’ordinateur sur la période sélectionnée.
        - Téléchargements : informations sur la quantité totale de trafic (en Mo) téléchargée par l’ordinateur sur la période sélectionnée.
    - **Applications découvertes**  
  Répertorie toutes les applications découvertes qui ont fait l’objet d’un accès par l’ordinateur.
    - **Historique de l’utilisateur**  
    Répertorie tous les utilisateurs qui se sont connectés à l’ordinateur.
    - **Historique de l’adresse IP**  
    Répertorie toutes les adresses IP qui ont été attribuées à l’ordinateur.
 ![Vue d’ensemble des ordinateurs](media/machines-overview.png)

Comme avec n’importe quelle autre source Cloud Discovery, vous pouvez exporter les données du rapport sur les utilisateurs de point de terminaison Win10 pour un examen plus approfondi.

> [!NOTE]
>
> - Defender ATP transfère les données à Cloud App Security dans des segments de environ 4 Mo (environ 4000 transactions de point de terminaison)
> - Si la limite de 4 Mo n’est pas atteinte dans un délai de 1 heure, Defender ATP signale toutes les transactions effectuées au cours de la dernière heure.
> - Si l’appareil de point de terminaison se trouve derrière un proxy direct, le volume de trafic n’est pas visible par Microsoft Defender ATP et ne sera donc pas inclus dans les rapports Cloud Discovery. Pour plus d’informations, consultez surveillance de la [connexion réseau derrière le proxy direct](https://techcommunity.microsoft.com/t5/Microsoft-Defender-ATP/MDATP-Monitoring-network-connection-behind-forward-proxy-Public/ba-p/758274).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

## <a name="related-videos"></a>Vidéos associées

> [!div class="nextstepaction"]
> [Découverte de l’informatique cachée au-delà du réseau d’entreprise](https://www.youtube.com/watch?v=f8hbvbY1Hnc)

[!INCLUDE [Open support ticket](includes/support.md)]
