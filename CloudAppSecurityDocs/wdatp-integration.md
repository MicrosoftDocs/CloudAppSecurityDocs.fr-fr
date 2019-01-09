---
title: Intégrer Windows Defender ATP à Cloud App Security
description: Cet article explique comment intégrer Windows Defender Advanced Threat Protection à Cloud App Security pour une visibilité améliorée de Shadow IT et de la gestion des risques.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/14/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: b35ca44c-da8e-49ec-89d1-c076d123c14f
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 1741b209e1e76da18297e075dff26d97fb3adcd4
ms.sourcegitcommit: 475dc75456f4683336e3e4875e3155677e4fb827
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2018
ms.locfileid: "53450560"
---
# <a name="windows-defender-advanced-threat-protection-integration-with-microsoft-cloud-app-security"></a>Intégration du module Windows Defender - Protection avancée contre les menaces à Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

Microsoft Cloud App Security s’intègre de manière native à Windows Defender Advanced Threat Protection (ATP). L’intégration simplifie le lancement de Cloud Discovery, étend les fonctionnalités de Cloud Discovery au-delà de votre réseau d’entreprise et permet d’effectuer des recherches basées sur la machine. [Windows Defender - Protection avancée contre les menaces (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) est une plateforme de sécurité pour une protection, une détection, un examen et une réponse intelligents. Windows Defender ATP protège les points de terminaison contre les cybermenaces, détecte les attaques avancées et les violations de données, automatise les incidents de sécurité et améliore le dispositif de sécurité.

Microsoft Cloud App Security utilise les informations de trafic collectées par Windows Defender ATP concernant les applications et les services cloud accessibles à partir de machines Windows 10 gérées par le service informatique. L’intégration vous permet d’exécuter Cloud Discovery sur n’importe quelle machine du réseau d’entreprise à l’aide du Wi-Fi public, en cas d’itinérance et d’accès à distance. Elle permet également d’effectuer des recherches basées sur la machine.

Après avoir identifié un utilisateur à risque, vous pouvez vérifier toutes les machines auxquelles l’utilisateur a accédé pour détecter des risques potentiels. Si vous identifiez une machine à risque, vérifiez tous les utilisateurs qui l’ont utilisée pour détecter des risques potentiels. Les journaux de vos points de terminaison routés vers Cloud App Security fournissent des informations utilisateur pour les activités de trafic. L’activité réseau de Windows Defender ATP fournit le contexte d’appareil. Associez le contexte d’appareil au nom d’utilisateur pour disposer d’une image complète de votre réseau indiquant quel utilisateur a effectué quelle activité et à partir de quelle machine.

Microsoft Cloud App Security utilise l’intégration native à Windows Defender ATP pour exploiter les données relatives au trafic des applications cloud et aux services des appareils Windows gérés. L’intégration est prête à l’emploi et ne nécessite pas de déploiement supplémentaire . Vous ne devez pas router ou mettre en miroir le trafic en provenance de vos points de terminaison ou effectuer des étapes d’intégration complexes.

> [!NOTE]
> Vous voulez essayer Windows Defender ATP ? [Inscrivez-vous pour obtenir un essai gratuit](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-assignaccess-abovefoldlink).
>


## <a name="prerequisites"></a>Prérequis

- Licence Microsoft Cloud App Security
- Licence Windows Defender ATP
- Ordinateurs Windows 10 exécutant la version 1809 ou une version ultérieure


## <a name="how-it-works"></a>Fonctionnement

Seul, Cloud App Security collecte des journaux de vos points de terminaison en utilisant des [journaux que vous chargez](create-snapshot-cloud-discovery-reports.md) ou en [configurant le chargement automatique de journaux](discovery-docker.md). L’intégration native vous permet d’exploiter au mieux les journaux que l’agent de Windows Defender ATP crée lorsqu’il s’exécute sur Windows et supervise les transactions réseau. Utilisez ces informations pour la découverte Shadow IT sur les machines Windows de votre réseau.

Pour vous permettre d’effectuer la découverte Cloud Discovery sur d’autres plateformes, il est préférable d’utiliser le [collecteur de journaux](discovery-docker.md) Cloud App Security avec l’intégration à Windows Defender ATP pour superviser vos machines Windows 10.

## <a name="how-to-integrate-windows-defender-atp-with-cloud-app-security"></a>Guide pratique pour intégrer Windows Defender ATP à Cloud App Security

Pour activer l’intégration à Cloud App Security à partir de Windows Defender ATP :

1. Dans le volet de navigation du portail Windows Defender ATP, sélectionnez **Configuration des préférences**.
2. Dans le menu **Paramètres**, sous **Général**, sélectionnez **Fonctionnalités avancées**.
3. Basculez **Microsoft Cloud App Security** sur **Activé**.
4. Cliquez sur **Enregistrer les préférences**.

>[!NOTE]
> Il faut jusqu’à deux heures après l’activation de l’intégration pour que les données s’affichent dans Cloud App Security.
>

   ![Paramètres WD ATP](./media/wdatp-settings.png)

## <a name="investigate-machines-in-cloud-app-security"></a>Examiner des ordinateurs dans Cloud App Security

Une fois que vous avez intégré Windows Defender ATP à Cloud App Security, vous pouvez examiner des données de machine découvertes dans le tableau de bord Cloud Discovery.

1. Dans le portail Cloud App Security, cliquez sur **Cloud Discovery**, puis sur **Tableau de bord Cloud Discovery**.
2. Dans la barre de navigation supérieure, sous **Rapports continus**, sélectionnez **Utilisateurs de point de terminaison Win10**.
  ![Rapport WD ATP](./media/win10-dashboard-report.png)
3. En haut, vous voyez le nombre de machines détectées ajoutées après l’intégration.
4. Cliquez sur l’onglet **Ordinateurs**.
5. Vous pouvez explorer chaque machine répertoriée et utiliser les onglets pour afficher les données de la recherche. Recherchez des corrélations entre les machines, les utilisateurs, les adresses IP et les applications qui ont été impliqués dans des incidents :
   - **Vue d’ensemble**
      - Transactions : Informations sur le nombre de transactions qui ont eu lieu sur la machine pendant la période sélectionnée.
      - Trafic total : Informations sur la quantité de trafic totale (en Mo) pour la période sélectionnée.
     - Chargements : Informations sur la quantité de trafic totale (en Mo) chargée par la machine pendant la période sélectionnée.
     - Téléchargements : Informations sur la quantité de trafic totale (en Mo) téléchargée par la machine pendant la période sélectionnée.
   - **Applications découvertes**<br>
  Répertorie toutes les applications découvertes qui ont fait l’objet d’un accès par l’ordinateur.
   - **Historique de l’utilisateur**<br>
    Répertorie tous les utilisateurs qui se sont connectés à l’ordinateur.
   - **Historique de l’adresse IP**<br>
    Répertorie toutes les adresses IP qui ont été attribuées à l’ordinateur.
 ![Vue d’ensemble des ordinateurs](./media/machines-overview.png)
 
Comme avec n’importe quelle autre source Cloud Discovery, vous pouvez exporter les données du rapport sur les utilisateurs de point de terminaison Win10 pour un examen plus approfondi. 


## <a name="related-videos"></a>Vidéos connexes

[Shadow IT discovery beyond the corporate network with Windows Defender ATP and Cloud App Security](https://www.youtube.com/watch?v=f8hbvbY1Hnc) (Découverte Shadow IT au-delà du réseau d’entreprise avec Windows Defender ATP et Cloud App Security)  

## <a name="next-steps"></a>Étapes suivantes 
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md) 

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)  
  
