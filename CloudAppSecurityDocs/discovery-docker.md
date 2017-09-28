---
title: Configurer le chargement automatique des journaux pour des rapports continus | Documentation Microsoft
description: "Cette rubrique décrit la procédure de configuration du chargement automatique des journaux pour des rapports continus dans Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 9/24/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: c75ba963-ad5a-48e6-8d5d-610fc6e0b990
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: f0f6f0de46e8833b4f4ffb6bd31c7c46eeacac9a
ms.sourcegitcommit: 13148ac82e496e8d4e0d10851e5d6e4f231229e4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2017
---
# <a name="configure-automatic-log-upload-for-continuous-reports"></a>Configurer le chargement automatique des journaux pour des rapports continus


Les collecteurs de journaux vous permettent d’automatiser facilement le chargement manuel des journaux de votre réseau. Le collecteur de journaux s’exécute sur votre réseau et reçoit les journaux par le biais de Syslog ou FTP. Chaque journal est automatiquement traité, compressé et transmis au portail. Les journaux FTP sont chargés sur Cloud App Security une fois que le fichier a terminé le transfert FTP vers le collecteur de journaux.  Pour Syslog, le collecteur de journaux écrit les journaux reçus sur le disque et charge le fichier sur Cloud App Security quand la taille du fichier est supérieure à 40 Ko.

Une fois qu’un journal est chargé dans Cloud App Security, il est déplacé dans un répertoire de sauvegarde qui stocke les 20 derniers journaux à un moment donné. Quand de nouveaux journaux arrivent, les anciens sont supprimés. Quand l’espace disque du collecteur de journaux est plein, le collecteur de journaux supprime les nouveaux journaux tant qu’il ne dispose pas de davantage d’espace disque libre. Dans ce cas, un avertissement s’affiche sous l’onglet **Collecteurs de journaux** des paramètres **Charger les journaux automatiquement**.

Avant de configurer la collecte de fichiers journaux automatique, vérifiez que votre journal correspond au type attendu de journal pour vous assurer que Cloud App Security peut analyser votre fichier spécifique.

> [!NOTE]
>-  Cloud App Security prend en charge le transfert des journaux de votre serveur SIEM au collecteur de journaux en partant du principe que les journaux sont transférés sous leur format d’origine. Cependant, nous vous recommandons fortement d’intégrer le collecteur de journaux directement à votre pare-feu et/ou proxy.
>- Le collecteur de journaux compresse les données avant leur chargement. Le trafic sortant du collecteur de journaux a un volume égal à 10 % de celui des journaux de trafic reçus. 

## <a name="deployment-modes"></a>Modes de déploiement

Le collecteur de journaux prend en charge deux modes de déploiement :

-   **Conteneur** (*préversion*) : s’exécute en tant qu’image Docker sur [Windows](discovery-docker-windows.md) et [Ubuntu](discovery-docker-ubuntu.md), soit localement, soit sur Azure. 



-   **Appliance virtuelle**: [s’exécute en tant qu’image sur l’hyperviseur Hyper-V ou VMware](configure-automatic-log-upload-for-continuous-reports.md)




## <a name="see-also"></a>Voir aussi
 
[Créer des rapports d’instantanés Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Utilisation des données Cloud Discovery](working-with-cloud-discovery-data.md)

