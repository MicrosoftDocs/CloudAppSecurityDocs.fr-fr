---
title: Intégrer le module Windows Defender - Protection avancée contre les menaces à Cloud App Security | Microsoft Docs
description: Cet article fournit des informations sur la façon d’intégrer Windows Defender ATP à l’intégration fluide de Cloud App Security et la visibilité améliorée de Shadow IT et de la gestion des risques.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/3/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: b35ca44c-da8e-49ec-89d1-c076d123c14f
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 114e4deeeca06c41132421a748fb95c5c7e7b34d
ms.sourcegitcommit: 53a1c990ff06674c26563a9ebcb1979818c3c063
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2018
ms.locfileid: "48881871"
---
*S’applique à : Microsoft Cloud App Security*


# <a name="windows-defender-advanced-threat-protection-integration-with-microsoft-cloud-app-security"></a>Intégration du module Windows Defender - Protection avancée contre les menaces à Microsoft Cloud App Security

Microsoft Cloud App Security s’intègre au module Windows Defender - Protection avancée contre les menaces (ATP) en mode natif pour simplifier le déploiement de Cloud Discovery, étendre les fonctionnalités de Cloud Discovery au-delà de votre réseau d’entreprise et activer l’examen basé sur l’ordinateur. 

[Windows Defender - Protection avancée contre les menaces (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) est une plateforme de sécurité pour une protection, une détection, un examen et une réponse intelligents. Windows Defender ATP protège les points de terminaison contre les cybermenaces, détecte les attaques avancées et les violations de données, automatise les incidents de sécurité et améliore le dispositif de sécurité.

Microsoft Cloud App Security s’appuie sur les informations de trafic collectées par Windows Defender ATP concernant les applications et les services cloud accessibles à partir d’ordinateurs Windows 10 gérés par le service informatique. Cela vous permet d’exécuter Cloud Discovery sur n’importe quel ordinateur du réseau d’entreprise à l’aide du Wi-Fi public, en cas d’itinérance et d’accès à distance. Cela permet également d’effectuer un examen basé sur l’ordinateur : après avoir identifié un utilisateur à risque, vous pouvez vérifier tous les ordinateurs auxquels l’utilisateur a accédé pour détecter les risques potentiels. Si vous identifiez un ordinateur à risque, vous pouvez vérifier tous les utilisateurs qui l’ont utilisé pour détecter des risques potentiels. Les journaux de vos points de terminaison routés vers Cloud App Security fournissent des informations utilisateur pour les activités de trafic. L’activité réseau de Windows Defender ATP fournit le contexte d’appareil, lequel peut être associé au nom d’utilisateur pour fournir une image complète de quel utilisateur a effectué quelle activité à partir de quel ordinateur sur votre réseau. Microsoft Cloud App Security s’appuie sur l’intégration native à Windows Defender ATP pour exploiter les données relatives au trafic des applications cloud et aux services des appareils Windows gérés. Cette intégration fluide ne nécessite pas de n’importe quel prêt à l’emploi et déploiement supplémentaires. Il n’est pas nécessaire de router ou de mettre en miroir le trafic en provenance de vos points de terminaison ou d’effectuer des étapes d’intégration complexes.

> [!NOTE]
> Vous voulez essayer Windows Defender ATP ? [Inscrivez-vous pour obtenir un essai gratuit](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-assignaccess-abovefoldlink).
>


## <a name="prerequisites"></a>Prérequis

- Licence Microsoft Cloud App Security
- Licence Windows Defender ATP
- Ordinateurs Windows 10 exécutant la version 1809 ou une version ultérieure


## <a name="how-it-works"></a>Fonctionnement

Seul, Cloud App Security collecte des journaux de vos points de terminaison en utilisant des [journaux que vous chargez](create-snapshot-cloud-discovery-reports.md) ou en [configurant le chargement automatique de journaux](discovery-docker.md). Cette intégration native vous permet d’exploiter au mieux les journaux que l’agent de Windows Defender ATP crée quand il s’exécute sur Windows et qu’il supervise les transactions réseau, et de les utiliser pour la découverte Shadow IT sur les machines Windows de votre réseau. 

Pour vous permettre d’effectuer la découverte Cloud Discovery sur d’autres plateformes, il est préférable d’utiliser à la fois le [collecteur de journaux](discovery-docker.md) Cloud App Security et l’intégration à Windows Defender ATP pour superviser vos machines Windows 10.


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

Une fois que vous avez intégré Windows Defender ATP à Cloud App Security, vous pouvez examiner des données d’ordinateur découvertes dans le tableau de bord Cloud Discovery.

1. Dans le portail Cloud App Security, cliquez sur **Cloud Discovery**, puis sur **Tableau de bord Cloud Discovery**.
2. Dans la barre de navigation supérieure, sous **Rapports continus**, sélectionnez **Utilisateurs de point de terminaison Win10**.
  ![Rapport WD ATP](./media/win10-dashboard-report.png)
4. Vous pouvez voir qu’en haut, le nombre de machines détectées a été ajouté après l’intégration.
5. Cliquez sur l’onglet **Ordinateurs**.
6. Vous pouvez explorer les détails de chaque ordinateur répertorié, puis utiliser les onglets pour afficher les données d’investigation et rechercher des corrélations entre les ordinateurs et les utilisateurs, les adresses IP et les applications qui ont été impliqués dans des incidents :
   - **Vue d’ensemble**
      - Transactions : vous fournit des informations sur le nombre de transactions qui ont eu lieu sur l’ordinateur pendant la période sélectionnée.
      - Trafic total : vous fournit des informations sur la quantité de trafic totale (en Mo) pour la période sélectionnée.
     - Chargements : vous fournit des informations sur la quantité de trafic totale (en Mo) chargée par l’ordinateur pendant la période sélectionnée.
     - Téléchargement : vous fournit des informations sur la quantité de trafic totale (en Mo) téléchargée par l’ordinateur pendant la période sélectionnée.
   - **Applications découvertes**<br>
  Répertorie toutes les applications découvertes qui ont fait l’objet d’un accès par l’ordinateur.
   - **Historique de l’utilisateur**<br>
    Répertorie tous les utilisateurs qui se sont connectés à l’ordinateur.
   - **Historique de l’adresse IP**<br>
    Répertorie toutes les adresses IP qui ont été attribuées à l’ordinateur.
 ![Vue d’ensemble des ordinateurs](./media/machines-overview.png)
 

Comme avec n’importe quelle autre source Cloud Discovery, vous pouvez exporter les données du rapport sur les utilisateurs de point de terminaison Win10 pour un examen plus approfondi. 


## <a name="related-videos"></a>Vidéos connexes  
[Shadow IT discovery beyond the corporate network with Windows Defender ATP and Cloud](https://www.youtube.com/watch?v=f8hbvbY1Hnc)  

## <a name="see-also"></a>Voir aussi  
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
