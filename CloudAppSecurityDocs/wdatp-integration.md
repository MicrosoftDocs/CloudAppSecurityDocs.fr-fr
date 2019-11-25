---
title: Integrate Microsoft Defender ATP with Cloud App Security
description: This article describes how to integrate Microsoft Defender Advanced Threat Protection with Cloud App Security for enhanced visibility into Shadow IT and risk management.
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
ms.assetid: b35ca44c-da8e-49ec-89d1-c076d123c14f
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: aeddfb56542309b0ee6b1f0d4cdec85bb36a120e
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74459432"
---
# <a name="microsoft-defender-advanced-threat-protection-integration-with-microsoft-cloud-app-security"></a>Microsoft Defender Advanced Threat Protection integration with Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

Microsoft Cloud App Security integrates with Microsoft Defender Advanced Threat Protection (ATP) natively. L’intégration simplifie le lancement de Cloud Discovery, étend les fonctionnalités de Cloud Discovery au-delà de votre réseau d’entreprise et permet d’effectuer des recherches basées sur la machine. [Microsoft Defender Advanced Threat Protection (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) is a security platform for intelligent protection, detection, investigation, and response. Microsoft Defender ATP protects endpoints from cyber threats, detects advanced attacks and data breaches, automates security incidents, and improves security posture.

Microsoft Cloud App Security uses the traffic information collected by Microsoft Defender ATP about the cloud apps and services being accessed from IT-managed Windows 10 machines. L’intégration vous permet d’exécuter Cloud Discovery sur n’importe quelle machine du réseau d’entreprise à l’aide du Wi-Fi public, en cas d’itinérance et d’accès à distance. Elle permet également d’effectuer des recherches basées sur la machine.

Après avoir identifié un utilisateur à risque, vous pouvez vérifier toutes les machines auxquelles l’utilisateur a accédé pour détecter des risques potentiels. Si vous identifiez une machine à risque, vérifiez tous les utilisateurs qui l’ont utilisée pour détecter des risques potentiels. Les journaux de vos points de terminaison routés vers Cloud App Security fournissent des informations utilisateur pour les activités de trafic. Microsoft Defender ATP network activity provides device context. Associez le contexte d’appareil au nom d’utilisateur pour disposer d’une image complète de votre réseau indiquant quel utilisateur a effectué quelle activité et à partir de quelle machine.

Microsoft Cloud App Security uses the native integration with Microsoft Defender ATP to tap into data about cloud app and service traffic from managed Windows devices. L’intégration est prête à l’emploi et ne nécessite pas de déploiement supplémentaire . Vous ne devez pas router ou mettre en miroir le trafic en provenance de vos points de terminaison ou effectuer des étapes d’intégration complexes.

> [!NOTE]
> Want to experience Microsoft Defender ATP? [Inscrivez-vous pour obtenir un essai gratuit](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-assignaccess-abovefoldlink).
>


## <a name="prerequisites"></a>Conditions préalables

- Licence Microsoft Cloud App Security
- Microsoft Defender ATP license
- Windows 10 version 1709 (OS Build 16299.1085 with KB4493441), Windows 10 version 1803 (OS Build 17134.704 with KB4493464), Windows 10 version 1809 (OS Build 17763.379 with KB4489899) or later Windows 10 versions
- Activer/désactiver **Fonctionnalités d’évaluation** pour activer cette fonctionnalité dans Cloud App Security

## <a name="how-it-works"></a>Fonctionnement

Seul, Cloud App Security collecte des journaux de vos points de terminaison en utilisant des [journaux que vous chargez](create-snapshot-cloud-discovery-reports.md) ou en [configurant le chargement automatique de journaux](discovery-docker.md). Native integration enables you to take advantage of the logs Microsoft Defender ATP's agent creates when it runs on Windows and monitors network transactions. Utilisez ces informations pour la découverte Shadow IT sur les machines Windows de votre réseau.

To enable you to perform Cloud Discovery across other platforms, it's best to use both the Cloud App Security [log collector](discovery-docker.md), along with Microsoft Defender ATP integration to monitor your Windows 10 machines.

## <a name="how-to-integrate-microsoft-defender-atp-with-cloud-app-security"></a>How to integrate Microsoft Defender ATP with Cloud App Security

To enable integration with Cloud App Security from Microsoft Defender ATP:

1. In the Microsoft Defender ATP portal, from the navigation pane, select **Preferences setup**.
2. Dans le menu **Paramètres**, sous **Général**, sélectionnez **Fonctionnalités avancées**.
3. Basculez **Microsoft Cloud App Security** sur **Activé**.
4. Cliquez sur **Enregistrer les préférences**.

>[!NOTE]
> Il faut jusqu’à deux heures après l’activation de l’intégration pour que les données s’affichent dans Cloud App Security.
>

   ![Paramètres WD ATP](./media/wdatp-settings.png)

## <a name="investigate-machines-in-cloud-app-security"></a>Examiner des ordinateurs dans Cloud App Security

After you integrate Microsoft Defender ATP with Cloud App Security, you can investigate discovered machine data in the Cloud Discovery dashboard.

1. Dans le portail Cloud App Security, cliquez sur **Cloud Discovery**, puis sur **Tableau de bord Cloud Discovery**.
2. Dans la barre de navigation supérieure, sous **Rapports continus**, sélectionnez **Utilisateurs de point de terminaison Win10**.
  ![Rapport WD ATP](./media/win10-dashboard-report.png)
3. En haut, vous voyez le nombre de machines détectées ajoutées après l’intégration.
4. Cliquez sur l’onglet **Ordinateurs**.
5. Vous pouvez explorer chaque machine répertoriée et utiliser les onglets pour afficher les données de la recherche. Recherchez des corrélations entre les machines, les utilisateurs, les adresses IP et les applications qui ont été impliqués dans des incidents :
   - **Vue d’ensemble**
      - Transactions: Information about the number of transactions that took place on the machine over the selected period of time.
      - Total traffic: Information about the total amount of traffic (in MB) over the selected period of time.
     - Uploads: Information about the total amount of traffic (in MB) uploaded by the machine over the selected period of time.
     - Downloads: Information about the total amount of traffic (in MB) downloaded by the machine over the selected period of time.
   - **Applications découvertes**<br>
  Répertorie toutes les applications découvertes qui ont fait l’objet d’un accès par l’ordinateur.
   - **Historique de l’utilisateur**<br>
    Répertorie tous les utilisateurs qui se sont connectés à l’ordinateur.
   - **Historique de l’adresse IP**<br>
    Répertorie toutes les adresses IP qui ont été attribuées à l’ordinateur.
 ![Vue d’ensemble des ordinateurs](./media/machines-overview.png)
 
Comme avec n’importe quelle autre source Cloud Discovery, vous pouvez exporter les données du rapport sur les utilisateurs de point de terminaison Win10 pour un examen plus approfondi. 

> [!NOTE]
> - Defender ATP forwards data to Cloud App Security in chunks of ~4 MB (~4000 endpoint transactions)
> - If the 4 MB limit isn't reached within 1 hour, Defender ATP reports all the transactions performed over the last hour.

## <a name="related-videos"></a>Vidéos connexes

[Shadow IT discovery beyond the corporate network with Microsoft Defender ATP and Cloud App Security](https://www.youtube.com/watch?v=f8hbvbY1Hnc)  

## <a name="next-steps"></a>Étapes suivantes 
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md) 

[!INCLUDE [Open support ticket](includes/support.md)]  
  
