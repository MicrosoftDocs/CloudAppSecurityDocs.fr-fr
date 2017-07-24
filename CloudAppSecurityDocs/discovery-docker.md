---
title: Configurer le chargement automatique des journaux pour des rapports continus | Documentation Microsoft
description: "Cette rubrique aborde le processus de configuration du chargement automatique des journaux pour une création continue de rapports dans Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/9/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: c75ba963-ad5a-48e6-8d5d-610fc6e0b990
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 9f17366c62b202432d8b0c750290b4915f64c929
ms.sourcegitcommit: b2e3af9d0a62dcb6410cc3992183c2888bdf6a2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2017
---
# <a name="configure-automatic-log-upload-for-continuous-reports"></a>Configurer le chargement automatique des journaux pour des rapports continus


Les collecteurs de journaux vous permettent d’automatiser facilement le chargement manuel des journaux de votre réseau. Le collecteur de journaux s’exécute sur votre réseau et reçoit les journaux par le biais de Syslog ou FTP. Chaque journal est automatiquement traité, compressé et transmis au portail. Les journaux FTP sont chargés dans Cloud App Security une fois terminé le transfert FTP du fichier vers le collecteur de journaux.  Pour Syslog, le collecteur de journaux écrit les journaux reçus sur le disque et charge le fichier dans Cloud App Security si sa taille est supérieure à 40 Ko.

Une fois qu’un journal est chargé dans Cloud App Security, il est déplacé dans un répertoire de sauvegarde qui stocke les 20 derniers journaux à un moment donné. Quand de nouveaux journaux arrivent, les anciens sont supprimés. Quand l’espace disque du collecteur de journaux est plein, le collecteur de journaux supprime les nouveaux journaux tant qu’il ne dispose pas de davantage d’espace disque libre.

Avant de configurer la collecte de fichiers journaux automatique, vérifiez que votre journal correspond au type attendu de journal pour vous assurer que Cloud App Security peut analyser votre fichier spécifique.

> [!NOTE]
> Cloud App Security prend en charge le transfert des journaux de votre serveur SIEM au collecteur de journaux en partant du principe que les journaux sont transférés sous leur format d’origine. Cependant, il est fortement recommandé d’intégrer le collecteur de journaux directement à votre pare-feu et/ou proxy.

## <a name="deployment-modes"></a>Modes de déploiement

Le collecteur de journaux prend en charge deux modes de déploiement :

-   **Mode Conteneur** (*basé sur Docker CE*) : s’exécute comme une image Docker sur [Windows](discovery-docker-windows.md) et [Ubuntu](discovery-docker-ubuntu.md), soit en local, soit dans Azure.

-   **Mode Appliance virtuelle** (*déconseillé*) : [s’exécute en tant qu’image sur l’hyperviseur Hyper-V ou VMware](configure-automatic-log-upload-for-continuous-reports.md)




## <a name="see-also"></a>Voir aussi
 
[Créer des rapports d’instantanés Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Utilisation des données Cloud Discovery](working-with-cloud-discovery-data.md)
