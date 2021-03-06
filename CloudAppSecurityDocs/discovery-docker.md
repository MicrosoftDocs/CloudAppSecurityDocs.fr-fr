---
title: Configurer le chargement automatique des journaux pour des rapports continus dans Cloud App Security
description: Cet article décrit la procédure de configuration du chargement automatique des journaux pour des rapports continus dans Cloud App Security.
ms.date: 7/22/2019
ms.topic: how-to
ms.openlocfilehash: f627ae6c1174e84958a09c1d0dfe0645c63d8dda
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96311568"
---
# <a name="configure-automatic-log-upload-for-continuous-reports"></a>Configurer le chargement automatique des journaux pour des rapports continus

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Les collecteurs de journaux vous permettent d’automatiser facilement le chargement manuel des journaux de votre réseau. Le collecteur de journaux s’exécute sur votre réseau et reçoit les journaux par le biais de Syslog ou FTP. Chaque journal est automatiquement traité, compressé et transmis au portail. Les journaux FTP sont chargés sur Microsoft Cloud App Security une fois que le fichier a terminé le transfert FTP vers le collecteur de journaux. Pour Syslog, le collecteur de journaux écrit les journaux reçus sur le disque. Le collecteur de journaux charge ensuite le fichier sur Cloud App Security quand la taille du fichier est supérieure à 40 Ko.

Une fois qu’un journal est chargé dans Cloud App Security, il est déplacé dans un répertoire de sauvegarde. Le répertoire de sauvegarde stocke les 20 derniers journaux. Quand de nouveaux journaux arrivent, les anciens sont supprimés. Chaque fois que l’espace disque du collecteur de journaux est plein, le collecteur de journaux supprime les nouveaux journaux tant qu’il ne dispose pas de davantage d’espace disque libre. Dans ce cas, vous voyez s’afficher un avertissement sous l’onglet **Collecteurs de journaux** des paramètres **Charger les journaux automatiquement**.

Avant de configurer la collecte automatique de fichiers journaux, vérifiez que votre journal correspond au type de journal attendu. Vous souhaitez vérifier que cloud App Security peut analyser votre fichier spécifique. Pour plus d’informations, consultez [Utiliser les journaux de trafic pour Cloud Discovery](create-snapshot-cloud-discovery-reports.md#log-format).

> [!NOTE]
>
> * Cloud App Security prend en charge le transfert des journaux de votre serveur SIEM au collecteur de journaux en partant du principe que les journaux sont transférés sous leur format d’origine. Cependant, nous vous recommandons fortement d’intégrer le collecteur de journaux directement à votre pare-feu et/ou proxy.
> * Le collecteur de journaux compresse les données avant qu’elles ne soient chargées. Le trafic sortant du collecteur de journaux a un volume égal à 10 % de celui des journaux de trafic reçus.
> * Si le collecteur de journaux rencontre des problèmes, vous recevrez une alerte si aucune donnée n’a été reçue pendant 48 heures.

## <a name="deployment-modes"></a>Modes de déploiement

Le collecteur de journaux prend en charge deux modes de déploiement :

* **Conteneur**: s’exécute en tant qu’image de l’arrimeur sur [Windows](discovery-docker-windows.md), [Ubuntu localement](discovery-docker-ubuntu.md), [Ubuntu dans Azure](discovery-docker-ubuntu-azure.md), [RHEL localement](discovery-docker-ubuntu.md) ou CentOS.

* **Appliance virtuelle**: s’exécute en tant qu’image sur l’hyperviseur Hyper-V ou VMware (déconseillé)

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Utilisation des données Cloud Discovery](working-with-cloud-discovery-data.md)
