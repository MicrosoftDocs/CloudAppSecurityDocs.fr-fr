---
title: Intégrer Microsoft Defender for Endpoint à Cloud App Security
description: Cet article explique comment intégrer Microsoft Defender-protection avancée contre les menaces avec Cloud App Security pour une meilleure visibilité de la gestion des risques et de l’informatique cachée.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 09/02/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 118f0047640b3b062ba5cd66d5601fec99ea8477
ms.sourcegitcommit: b0ad9e8e6b5668849e1c292c43084480f229d981
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2020
ms.locfileid: "93147490"
---
# <a name="microsoft-defender-advanced-threat-protection-integration-with-microsoft-cloud-app-security"></a>Intégration de Microsoft Defender-protection avancée contre les menaces avec Microsoft Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Microsoft Cloud App Security s’intègre à Microsoft Defender for Endpoint en mode natif. L’intégration simplifie le lancement de Cloud Discovery, étend les fonctionnalités de Cloud Discovery au-delà de votre réseau d’entreprise et permet d’effectuer des recherches basées sur la machine. [Microsoft Defender for Endpoint](/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) est une plateforme de sécurité pour la protection, la détection, l’investigation et la réponse intelligentes. Microsoft Defender for Endpoint protège les points de terminaison contre les menaces informatiques, détecte les attaques avancées et les violations de données, automatise les incidents de sécurité et améliore la sécurité.

Cloud App Security utilise les informations de trafic collectées par Microsoft Defender for Endpoint sur les applications Cloud et les services accessibles à partir d’ordinateurs Windows 10 gérés par le service informatique. L’intégration native vous permet d’exécuter des Cloud Discovery sur n’importe quel ordinateur du réseau d’entreprise, à l’aide du Wi-Fi public, de l’itinérance et de l’accès à distance. Elle permet également d’effectuer des recherches basées sur la machine.

L’intégration est prête à l’emploi et ne nécessite pas de déploiement supplémentaire . Vous ne devez pas router ou mettre en miroir le trafic en provenance de vos points de terminaison ou effectuer des étapes d’intégration complexes. Les journaux de vos points de terminaison envoyés à Cloud App Security fournissent des informations sur l’utilisateur pour les activités de trafic. L’activité réseau Microsoft Defender pour le point de terminaison fournit un contexte de périphérique. Le fait de coupler le contexte de périphérique au nom d’utilisateur fournit une image complète sur votre réseau, ce qui vous permet de déterminer l’utilisateur qui a effectué l’activité à partir de quelle machine.

En outre, lorsque vous identifiez un utilisateur à risque, vous pouvez vérifier tous les ordinateurs auxquels l’utilisateur a accédé pour détecter les risques potentiels. Si vous identifiez un ordinateur à risque, cochez tous les utilisateurs qui l’ont utilisé pour détecter d’autres risques potentiels.

Une fois les informations de trafic collectées, vous êtes prêt à approfondir l' [utilisation des applications Cloud](discovered-apps.md#deep-dive-into-discovered-apps) dans votre organisation. Cloud App Security tire parti des fonctionnalités de protection réseau de Microsoft Defender pour les points de terminaison pour bloquer l’accès des appareils de point de terminaison aux applications Cloud. Vous pouvez bloquer les applications en les [marquant comme non **Unsanctioned**](governance-discovery.md#BKMK_SanctionApp) approuvées dans le portail. En fonction de l’utilisation complète et de l’évaluation des risques de chaque application non approuvée, les domaines de l’application sont utilisés pour créer des [indicateurs de domaine](/windows/security/threat-protection/microsoft-defender-atp/manage-indicators#create-indicators-for-ips-and-urlsdomains-preview) dans le portail Microsoft Defender pour les points de terminaison. L’antivirus Microsoft Defender, exécuté sur les appareils de point de terminaison, utilise les indicateurs de domaine pour bloquer l’accès à ces applications.

> [!NOTE]
> Vous souhaitez expérimenter Microsoft Defender for Endpoint ? [Inscrivez-vous pour un essai gratuit](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-assignaccess-abovefoldlink).

## <a name="prerequisites"></a>Prérequis

- Licence Microsoft Cloud App Security
- Licence Microsoft Defender for Endpoint
- Windows 10 version 1709 (version du système d’exploitation 16299,1085 avec KB4493441), Windows 10 version 1803 (version du système d’exploitation 17134,704 avec KB4493464), Windows 10 version 1809 (système d’exploitation version 17763,379 avec KB4489899) ou versions ultérieures de Windows 10
- Antivirus Microsoft Defender
  - [protection en temps réel activée](/windows/security/threat-protection/windows-defender-antivirus/configure-real-time-protection-windows-defender-antivirus)
  - [protection fournie par le Cloud activée](/windows/security/threat-protection/windows-defender-antivirus/enable-cloud-protection-windows-defender-antivirus)
  - [Protection réseau activée et configurée pour bloquer le mode](/windows/security/threat-protection/microsoft-defender-atp/enable-network-protection)

## <a name="how-it-works"></a>Fonctionnement

Seul, Cloud App Security collecte des journaux de vos points de terminaison en utilisant des [journaux que vous chargez](create-snapshot-cloud-discovery-reports.md) ou en [configurant le chargement automatique de journaux](discovery-docker.md). L’intégration native vous permet de tirer parti des journaux créés par l’agent Microsoft Defender pour les points de terminaison lorsqu’il s’exécute sur Windows et surveille les transactions réseau. Utilisez ces informations pour la découverte Shadow IT sur les machines Windows de votre réseau.

Pour vous permettre d’effectuer des Cloud Discovery sur d’autres plateformes, il est préférable d’utiliser le [collecteur de journaux](discovery-docker.md)Cloud App Security, ainsi que l’intégration de Microsoft Defender for Endpoint pour surveiller vos ordinateurs Windows 10.

[Regardez nos vidéos](#related-videos) présentant les avantages de l’utilisation de Microsoft Defender for Endpoint avec Cloud App Security.

## <a name="how-to-integrate-microsoft-defender-for-endpoint-with-cloud-app-security"></a>Comment intégrer Microsoft Defender for Endpoint avec Cloud App Security

Pour activer l’intégration de Microsoft Defender for Endpoint avec Cloud App Security :

1. Dans le portail Microsoft Defender pour les points de terminaison, dans le volet de navigation, sélectionnez **préférences configuration** .
2. Dans le menu **Paramètres** , sous **Général** , sélectionnez **Fonctionnalités avancées** .
3. Basculez **Microsoft Cloud App Security** sur **Activé** .
4. Cliquez sur **Enregistrer les préférences** .

>[!NOTE]
> Il faut jusqu’à deux heures après l’activation de l’intégration pour que les données s’affichent dans Cloud App Security.
>

![Paramètres Microsoft Defender pour point de terminaison](media/wdatp-settings.png)

## <a name="investigate-machines-in-cloud-app-security"></a>Examiner des ordinateurs dans Cloud App Security

Une fois que vous avez intégré Microsoft Defender for Endpoint à Cloud App Security, vous pouvez examiner les données d’ordinateur découvertes dans le tableau de bord Cloud Discovery.

1. Dans Cloud App Security, cliquez sur **Cloud Discovery** puis **Cloud Discovery tableau de bord** .
2. Dans la barre de navigation supérieure, sous **Rapports continus** , sélectionnez **Utilisateurs de point de terminaison Win10** .
  ![Rapport WD ATP](media/win10-dashboard-report.png)
3. En haut, vous voyez le nombre de machines détectées ajoutées après l’intégration.
4. Cliquez sur l’onglet **Ordinateurs** .
5. Vous pouvez explorer chaque machine répertoriée et utiliser les onglets pour afficher les données de la recherche. Recherchez des corrélations entre les machines, les utilisateurs, les adresses IP et les applications qui ont été impliqués dans des incidents :

    - **Vue d'ensemble**
        - **Niveau de risque** de l’ordinateur : indique le risque que le profil de l’ordinateur soit relatif à d’autres ordinateurs de votre organisation, comme indiqué par la gravité (haute, moyenne, faible, informations). Cloud App Security utilise les profils d’ordinateur de Microsoft Defender for Endpoint pour chaque ordinateur basé sur l’analytique avancée. L’activité qui est anormale pour la ligne de base d’une machine est évaluée et détermine le niveau de risque de la machine. Utilisez le niveau de risque de l’ordinateur pour déterminer les machines à examiner en premier.
        - **Transactions** : informations sur le nombre de transactions qui ont eu lieu sur l’ordinateur pendant la période sélectionnée.
        - **Trafic total** : informations sur la quantité totale de trafic (en Mo) sur la période sélectionnée.
        - Charge : informations sur la quantité totale de trafic (en Mo) téléchargée par l’ordinateur sur la période sélectionnée.
        - **Téléchargements** : informations sur la quantité totale de trafic (en Mo) téléchargée par l’ordinateur sur la période sélectionnée.
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
> - Microsoft Defender pour le point de terminaison transfère les données à Cloud App Security dans des segments de environ 4 Mo (environ 4000 transactions de point de terminaison)
> - Si la limite de 4 Mo n’est pas atteinte dans un délai de 1 heure, Microsoft Defender for Endpoint signale toutes les transactions effectuées au cours de la dernière heure.
> - Nous vous recommandons de router les journaux du proxy direct vers Cloud App Security à l’aide du **chargement automatisé des journaux** afin d’obtenir une visibilité complète. Pour obtenir un autre moyen d’afficher ce trafic et d’examiner les URL accessibles par les appareils qui se trouvent derrière le proxy de transfert, consultez surveillance de la [connexion réseau derrière le proxy direct](https://techcommunity.microsoft.com/t5/Microsoft-Defender-ATP/MDATP-Monitoring-network-connection-behind-forward-proxy-Public/ba-p/758274).

## <a name="investigate-device-network-events-in-microsoft-defender-for-endpoint"></a>Examiner les événements réseau de l’appareil dans Microsoft Defender pour le point de terminaison

Utilisez les étapes suivantes pour obtenir une visibilité plus granulaire de l’activité réseau de l’appareil dans Microsoft Defender pour le point de terminaison :

1. Dans Cloud App Security, sous **détection** , puis sélectionnez **ordinateurs** .
1. Sélectionnez l’ordinateur que vous souhaitez examiner, puis dans le coin supérieur droit, cliquez sur **affichage dans Microsoft Defender pour point de terminaison** .
1. Dans Microsoft Defender Security Center, sous **appareils** > {appareil sélectionné}, sélectionnez **chronologie** .
1. Sous **filtres** , sélectionnez **événements réseau** .
1. Examinez les événements réseau de l’appareil en fonction des besoins.

![Capture d’écran montrant la chronologie de l’appareil dans Microsoft Defender Security Center](media/mdatp-selected-device.png)

## <a name="investigate-app-usage-in-microsoft-defender-for-endpoint-with-advanced-hunting"></a>Examiner l’utilisation des applications dans Microsoft Defender pour les points de terminaison avec la chasse avancée

Utilisez les étapes suivantes pour obtenir une visibilité plus granulaire sur les événements réseau liés à l’application dans Microsoft Defender pour le point de terminaison :

1. Dans Cloud App Security, sous **détection** , puis sélectionnez **découvert** .
1. Cliquez sur l’application que vous souhaitez examiner pour ouvrir son tiroir.
1. Cliquez sur la liste **domaine** de l’application, puis copiez la liste des domaines.
1. Dans Microsoft Defender Security Center, sous **appareils** , sélectionnez sélection **avancée** .
1. Collez la requête suivante et remplacez `<DOMAIN_LIST>` par la liste des domaines que vous avez copiés précédemment.

    ```kusto
    DeviceNetworkEvents
    | where RemoteUrl in ("<DOMAIN_LIST>")
    | order by Timestamp desc
    ```

1. Exécutez la requête et examinez les événements réseau pour cette application.

![Capture d’écran montrant Microsoft Defender Security Center la chasse avancée](media/mdatp-advanced-hunting.png)

## <a name="block-access-to-unsanctioned-cloud-apps"></a>Bloquer l’accès aux applications Cloud non approuvées

Cloud App Security utilise la balise d' [**application non**](governance-discovery.md#BKMK_SanctionApp) approuvée intégrée pour marquer les applications Cloud comme étant interdites en vue de leur utilisation, disponible dans les pages du catalogue d’applications Cloud Discovery et Cloud. En activant l’intégration à Microsoft Defender for Endpoint, vous pouvez bloquer en toute transparence l’accès aux applications non approuvées en un seul clic dans le portail Cloud App Security.

### <a name="how-blocking-works"></a>Fonctionnement du blocage

Les applications marquées comme non approuvées dans Cloud App Security sont synchronisées automatiquement avec Microsoft Defender pour le point de terminaison, **généralement en quelques** minutes. Plus précisément, les domaines utilisés par ces applications non approuvées sont propagés aux appareils de point de terminaison pour être bloqués par l’antivirus Microsoft Defender dans le contrat SLA de protection réseau.

### <a name="how-to-enable-cloud-app-blocking-with-microsoft-defender-for-endpoint"></a>Comment activer le blocage d’applications Cloud avec Microsoft Defender pour point de terminaison

Pour activer le contrôle d’accès pour les applications Cloud, procédez comme suit :

1. Dans Cloud App Security, sous l’roue dentée paramètres, sélectionnez **paramètres** , sous **Cloud Discovery** sélectionnez **Microsoft Defender pour point de terminaison** , puis sélectionnez **bloquer les applications** non approuvées.

    ![Capture d’écran montrant comment activer le blocage avec Microsoft Defender pour le point de terminaison](media/defender-atp-integration.png)

1. Dans Microsoft Defender Security Center, accédez à **paramètres**  >  **fonctionnalités avancées** , puis sélectionnez indicateurs de **réseau personnalisés** . Pour plus d’informations sur les indicateurs réseau, consultez [créer des indicateurs pour les adresses IP et les URL/domaines](/windows/security/threat-protection/microsoft-defender-atp/manage-indicators#create-indicators-for-ips-and-urlsdomains-preview).

    Cela vous permet de tirer parti des fonctionnalités de protection réseau antivirus de Microsoft Defender pour bloquer l’accès à un ensemble prédéfini d’URL à l’aide de Cloud App Security, soit en attribuant manuellement des [balises d’application](governance-discovery.md#BKMK_SanctionApp) à des applications spécifiques, soit en utilisant automatiquement une [stratégie de découverte d’application](cloud-discovery-policies.md#creating-an-app-discovery-policy).

    ![Capture d’écran montrant comment activer des indicateurs de réseau personnalisés dans Microsoft Defender pour le point de terminaison](media/defender-atp-custom-network-indicators.png)

## <a name="investigate-unsanctioned-apps-in-microsoft-defender-security-center"></a>Examiner les applications non approuvées dans Microsoft Defender Security Center

Chaque tentative d’accès à une application non approuvée déclenche une alerte dans Microsoft Defender Security Center avec des détails détaillés sur l’ensemble de la session. Cela vous permet d’effectuer des investigations plus approfondies dans les tentatives d’accès aux applications non approuvées, ainsi que de fournir des informations pertinentes supplémentaires pour une utilisation dans l’investigation des appareils de point de terminaison.

Parfois, l’accès à une application non approuvée n’est pas bloqué, soit parce que l’appareil de point de terminaison n’est pas configuré correctement, soit parce que la stratégie de mise en application n’a pas encore été propagée vers le point de terminaison. Dans ce cas, Microsoft Defender pour les administrateurs de point de terminaison reçoit une alerte dans Microsoft Defender Security Center que l’application non approuvée n’a pas été bloquée.

![Capture d’écran montrant l’alerte de l’application non approuvée de Microsoft Defender pour le point de terminaison](media/defender-atp-unsanctioned-app-alert.png)

> [!NOTE]
>
> - La propagation d’une application **à des appareils** de point de terminaison peut prendre jusqu’à deux heures.
> - Par défaut, les applications et les domaines marqués comme non **approuvés** dans Cloud App Security sont bloqués pour tous les appareils de point de terminaison de l’organisation.
> - Actuellement, les URL complètes ne sont pas prises en charge pour les applications non approuvées. Par conséquent, lors de la non-approbation d’applications configurées avec des URL complètes, elles ne sont pas propagées à Microsoft Defender pour le point de terminaison et ne seront pas bloquées. Par exemple, `google.com/drive` n’est pas pris en charge, tandis que `drive.google.com` est pris en charge.
> - Les notifications dans le navigateur peuvent varier d’un navigateur à l’autre.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

## <a name="related-videos"></a>Vidéos associées

> [!div class="nextstepaction"]
> [Découvrir et bloquer Shadow IT à l’aide de Microsoft Defender for Endpoint](https://www.youtube.com/watch?v=MsHkTOoqSQo)

> [!div class="nextstepaction"]
> [Découverte de l’informatique fantôme au-delà du réseau d’entreprise](https://www.youtube.com/watch?v=f8hbvbY1Hnc)

[!INCLUDE [Open support ticket](includes/support.md)]
