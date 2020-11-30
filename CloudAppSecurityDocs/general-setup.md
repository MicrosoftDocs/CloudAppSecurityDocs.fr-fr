---
title: Configurez les paramètres de votre organisation dans Cloud App Security
description: Cet article explique comment fournir des informations sur votre organisation dans Cloud App Security.
ms.date: 11/08/2020
ms.topic: how-to
ms.openlocfilehash: d070b45db464c5789446dc87c4216b1e4e3370c8
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314900"
---
# <a name="basic-setup-for-cloud-app-security"></a>Configuration de base pour Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

La procédure suivante contient des instructions pour personnaliser le portail Microsoft Cloud App Security.

## <a name="prerequisites"></a>Prérequis

Pour l’accès au portail, il est nécessaire d’ajouter les adresses IP suivantes à la liste verte de votre pare-feu pour fournir l’accès au portail Cloud App Security :

* 104.42.231.28

Pour les clients du gouvernement des États-Unis, il est également nécessaire d’ajouter les adresses IP suivantes à la liste verte de votre pare-feu pour fournir l’accès au portail Cloud App Security GCC High :

* 52.227.143.223
* 13.72.19.4

> [!NOTE]
> Pour obtenir des mises à jour quand des URL et des adresses IP ont changé, abonnez-vous au flux RSS comme expliqué dans [URL et plages d’adresses IP Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).

## <a name="set-up-the-portal"></a>Configurer le portail

1. Dans le portail Cloud App Security, dans la barre de menus, cliquez sur l' ![icône](media/settings-icon.png "Icône des paramètres") paramètres roue dentée paramètres, puis sélectionnez **paramètres** pour configurer les détails de votre organisation.

1. Sous **Détails de l’organisation**, vous devez absolument fournir un **Nom d’affichage de l’organisation** pour votre organisation. Il apparaît dans les e-mails et les pages web envoyés par le système.

1. Fournissez un **Nom de l’environnement** (client). Ces informations sont particulièrement importantes si vous gérez plusieurs locataires.

1. Vous pouvez également fournir un **Logo** qui apparaît dans les e-mails de notification et les pages web envoyées par le système. Le logo doit être un fichier png avec une taille maximale de 150 x 50 pixels sur un arrière-plan transparent.

1. Veillez à ajouter une liste de vos **domaines gérés** pour identifier les utilisateurs internes. L’ajout de domaines managés est une étape essentielle. Cloud App Security utilise les domaines managés pour déterminer quels sont les utilisateurs internes, les utilisateurs externes ainsi que les emplacements auxquels les fichiers doivent ou non être partagés. Ces informations sont utilisées pour les rapports et les alertes.

    * Les utilisateurs dans des domaines qui ne sont pas configurés comme internes sont marqués comme externes. Aucune recherche d’activités ou de fichiers n’est exécutée sur les utilisateurs externes.

1. Sous **déconnexion automatique**, spécifiez la durée pendant laquelle une session peut rester inactive avant que la session ne soit déconnectée automatiquement.

1. En cas d’intégration à Azure Information Protection, consultez [Intégration d’Azure Information Protection](azip-integration.md) pour obtenir des informations.

    * Pour utiliser l’intégration à Azure Information Protection, vous devez activer le [connecteur d’applications pour Office 365](connect-office-365-to-microsoft-cloud-app-security.md).

1. Si vous effectuez l’intégration à Microsoft Defender pour l’intégration des identités, consultez [Microsoft Defender for Identity Integration](azip-integration.md) pour plus d’informations.

1. Grâce à cet écran, vous pouvez à tout moment sauvegarder vos paramètres de portail. Cliquez sur **Exporter les paramètres du portail** pour créer un fichier JSON de tous vos paramètres de portail, y compris les règles de stratégie, les groupes d’utilisateurs et les plages d’adresses IP.

> [!NOTE]
> Si vous utilisez ExpressRoute, Cloud App Security est déployé dans Azure et entièrement intégré à [ExpressRoute](/azure/expressroute/expressroute-introduction). Toutes les interactions avec les applications Cloud App Security et le trafic envoyé à Cloud App Security, y compris le chargement des journaux de découverte, sont acheminés via l' **homologation publique** ExpressRoute pour améliorer la latence, les performances et la sécurité. Aucune étape de configuration n’est nécessaire côté client.
>
> Pour plus d’informations sur le peering public, consultez [Circuits ExpressRoute et domaines de routage](/azure/expressroute/expressroute-circuit-peerings).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Configurer Cloud Discovery](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]