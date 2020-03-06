---
title: Intégrer Microsoft Defender ATP avec Cloud App Security
description: Cet article explique comment intégrer Microsoft Defender-protection avancée contre les menaces avec Cloud App Security pour une meilleure visibilité de la gestion des risques et de l’informatique cachée.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/24/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: d45711d5dfd5f0a7a3ae30df1e5e90425ff631ff
ms.sourcegitcommit: be2c558eee71de02ec29632fc58256d49de0f86f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78304880"
---
# <a name="microsoft-defender-advanced-threat-protection-integration-with-microsoft-cloud-app-security"></a>Intégration de Microsoft Defender-protection avancée contre les menaces avec Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

Microsoft Cloud App Security s’intègre à Microsoft Defender-protection avancée contre les menaces (ATP) en mode natif. L’intégration simplifie le déploiement de Cloud Discovery, étend les fonctionnalités Cloud Discovery au-delà de votre réseau d’entreprise et permet l’investigation basée sur l’ordinateur. [Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) est une plateforme de sécurité pour la protection, la détection, l’investigation et la réponse intelligentes. Microsoft Defender ATP protège les points de terminaison contre les menaces informatiques, détecte les attaques avancées et les violations de données, automatise les incidents de sécurité et améliore la sécurité.

Cloud App Security utilise les informations de trafic collectées par Microsoft Defender ATP sur les applications Cloud et les services accessibles à partir d’ordinateurs Windows 10 gérés par le service informatique. L’intégration native vous permet d’exécuter des Cloud Discovery sur n’importe quel ordinateur du réseau d’entreprise, à l’aide du Wi-Fi public, de l’itinérance et de l’accès à distance. Il permet également une investigation basée sur l’ordinateur.

L’intégration ne nécessite pas de déploiement supplémentaire et est prête à l’emploi. Vous n’avez pas besoin d’acheminer ou de mettre en miroir le trafic à partir de vos points de terminaison ou d’effectuer des étapes d’intégration complexes. Les journaux de vos points de terminaison envoyés à Cloud App Security fournissent des informations sur l’utilisateur pour les activités de trafic. L’activité réseau Microsoft Defender ATP fournit le contexte de périphérique. Le fait de coupler le contexte de périphérique au nom d’utilisateur fournit une image complète sur votre réseau, ce qui vous permet de déterminer l’utilisateur qui a effectué l’activité à partir de quelle machine.

En outre, lorsque vous identifiez un utilisateur à risque, vous pouvez vérifier tous les ordinateurs auxquels l’utilisateur a accédé pour détecter les risques potentiels. Si vous identifiez un ordinateur à risque, cochez tous les utilisateurs qui l’ont utilisé pour détecter d’autres risques potentiels.

Une fois les informations de trafic collectées, vous êtes prêt à approfondir l' [utilisation des applications Cloud](discovered-apps.md#deep-dive-into-discovered-apps) dans votre organisation. Cloud App Security tire parti des fonctionnalités de protection réseau de Microsoft Defender ATP pour bloquer l’accès des appareils de point de terminaison aux applications Cloud. Vous pouvez bloquer les applications en les [marquant comme non ](governance-discovery.md#BKMK_SanctionApp) approuvées dans le portail. En fonction de l’utilisation complète et de l’évaluation des risques de chaque application non approuvée, les domaines de l’application sont utilisés pour créer des [indicateurs de domaine](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/manage-indicators#create-indicators-for-ips-and-urlsdomains-preview) dans le portail Microsoft Defender ATP. L’antivirus Windows Defender, exécuté sur des appareils de point de terminaison, utilise les indicateurs de domaine pour bloquer l’accès à ces applications.

> [!NOTE]
> Vous souhaitez découvrir Microsoft Defender ATP ? [Inscrivez-vous pour obtenir une version d’évaluation gratuite](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-assignaccess-abovefoldlink).

## <a name="prerequisites"></a>Composants requis

- Licence Microsoft Cloud App Security
- Licence Microsoft Defender ATP
- Windows 10 version 1709 (version du système d’exploitation 16299,1085 avec KB4493441), Windows 10 version 1803 (version du système d’exploitation 17134,704 avec KB4493464), Windows 10 version 1809 (système d’exploitation version 17763,379 avec KB4489899) ou versions ultérieures de Windows 10
- Antivirus Windows Defender
  - [protection en temps réel activée](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/configure-real-time-protection-windows-defender-antivirus)
  - [protection fournie par le Cloud activée](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/enable-cloud-protection-windows-defender-antivirus)
  - [Protection réseau activée et configurée pour bloquer le mode](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/enable-network-protection)

## <a name="how-it-works"></a>Fonctionnement

En soi, Cloud App Security collecte les journaux à partir de vos points de terminaison à l’aide des [journaux que vous téléchargez](create-snapshot-cloud-discovery-reports.md) ou en [configurant le chargement automatique des journaux](discovery-docker.md). L’intégration native vous permet de tirer parti des journaux créés par l’agent Microsoft Defender ATP lorsqu’il s’exécute sur Windows et surveille les transactions réseau. Utilisez ces informations pour la découverte Shadow IT sur les ordinateurs Windows de votre réseau.

Pour vous permettre d’effectuer des Cloud Discovery sur d’autres plateformes, il est préférable d’utiliser le [collecteur de journaux](discovery-docker.md)Cloud App Security, ainsi que l’intégration de Microsoft Defender ATP pour surveiller vos ordinateurs Windows 10.

## <a name="how-to-integrate-microsoft-defender-atp-with-cloud-app-security"></a>Intégration de Microsoft Defender ATP à Cloud App Security

Pour activer l’intégration de Microsoft Defender ATP avec Cloud App Security :

1. Dans le portail Microsoft Defender ATP, dans le volet de navigation, sélectionnez **préférences configuration**.
2. Dans le menu **paramètres** , sous **général**, sélectionnez **fonctionnalités avancées**.
3. Activez la **Microsoft Cloud App Security** **.**
4. Cliquez sur **enregistrer les préférences**.

>[!NOTE]
> Cela prend jusqu’à deux heures après que vous avez activé l’intégration pour que les données s’affichent dans Cloud App Security.
>

![Paramètres WD ATP](media/wdatp-settings.png)

## <a name="investigate-machines-in-cloud-app-security"></a>Examiner les machines dans Cloud App Security

Une fois que vous avez intégré Microsoft Defender ATP à Cloud App Security, vous pouvez examiner les données d’ordinateur découvertes dans le tableau de bord Cloud Discovery.

1. Dans le portail Cloud App Security, cliquez sur **Cloud Discovery** puis **Cloud Discovery tableau de bord**.
2. Dans la barre de navigation supérieure, sous **rapports continus**, sélectionnez **utilisateurs du point de terminaison Win10**.
  rapport ![WD ATP](media/win10-dashboard-report.png)
3. Dans la partie supérieure, vous verrez le nombre de machines découvertes ajoutées après l’intégration.
4. Cliquez sur l’onglet **ordinateurs** .
5. Vous pouvez descendre dans la liste de chaque ordinateur qui est listé et utiliser les onglets pour afficher les données d’investigation. Recherchez les corrélations entre les machines, les utilisateurs, les adresses IP et les applications impliquées dans les incidents :

    - **Vue d’ensemble**
        - Transactions : informations sur le nombre de transactions qui ont eu lieu sur l’ordinateur pendant la période sélectionnée.
        - Trafic total : informations sur la quantité totale de trafic (en Mo) sur la période sélectionnée.
        - Charge : informations sur la quantité totale de trafic (en Mo) téléchargée par l’ordinateur sur la période sélectionnée.
        - Téléchargements : informations sur la quantité totale de trafic (en Mo) téléchargée par l’ordinateur sur la période sélectionnée.
    - **Applications découvertes**  
  Répertorie toutes les applications découvertes qui ont été consultées par l’ordinateur.
    - **Historique de l’utilisateur**  
    Répertorie tous les utilisateurs qui se sont connectés à l’ordinateur.
    - **Historique des adresses IP**  
    Répertorie toutes les adresses IP qui ont été affectées à la machine.
 vue d’ensemble des ordinateurs ![](media/machines-overview.png)

Comme pour toute autre source de Cloud Discovery, vous pouvez exporter les données du rapport des utilisateurs de point de terminaison Win10 pour approfondir l’investigation.

> [!NOTE]
>
> - Microsoft Defender ATP transfère les données à Cloud App Security dans des segments de environ 4 Mo (environ 4000 transactions de point de terminaison)
> - Si la limite de 4 Mo n’est pas atteinte dans un délai de 1 heure, Microsoft Defender ATP signale toutes les transactions effectuées au cours de la dernière heure.
> - Si l’appareil de point de terminaison se trouve derrière un proxy direct, le volume de trafic n’est pas visible par Microsoft Defender ATP et ne sera donc pas inclus dans les rapports Cloud Discovery. Pour plus d’informations, consultez surveillance de la [connexion réseau derrière le proxy direct](https://techcommunity.microsoft.com/t5/Microsoft-Defender-ATP/MDATP-Monitoring-network-connection-behind-forward-proxy-Public/ba-p/758274).

## <a name="block-access-to-unsanctioned-cloud-apps"></a>Bloquer l’accès aux applications Cloud non approuvées

Cloud App Security utilise la balise d' [**application non**](governance-discovery.md#BKMK_SanctionApp) approuvée intégrée pour marquer les applications Cloud comme étant interdites en vue de leur utilisation, disponible dans les pages du catalogue d’applications Cloud Discovery et Cloud. En activant l’intégration à Microsoft Defender ATP, vous pouvez bloquer en toute transparence l’accès aux applications non approuvées en un seul clic dans le portail Cloud App Security.

### <a name="how-it-works"></a>Fonctionnement

Les applications marquées comme non approuvées dans Cloud App Security sont synchronisées automatiquement avec Microsoft Defender ATP, **généralement en quelques** minutes. Plus précisément, les domaines utilisés par ces applications non approuvées sont propagés aux appareils de point de terminaison pour être bloqués par l’antivirus Windows Defender dans le contrat SLA de protection réseau.

### <a name="how-to-enable-cloud-app-blocking-with-microsoft-defender-atp"></a>Comment activer le blocage d’applications Cloud avec Microsoft Defender ATP

Pour activer le contrôle d’accès pour les applications Cloud, procédez comme suit :

1. Dans Cloud App Security, sous l’roue dentée paramètres, sélectionnez **paramètres**, sous **Cloud Discovery** sélectionnez **Microsoft Defender ATP**, puis sélectionnez bloquer les **applications**non approuvées.

    ![Capture d’écran montrant comment activer le blocage avec Microsoft Defender ATP](media/defender-atp-integration.png)

1. Dans Microsoft Defender Security Center, accédez à **paramètres** > **fonctionnalités avancées**, puis sélectionnez **indicateurs réseau personnalisés**. Pour plus d’informations sur les indicateurs réseau, consultez [créer des indicateurs pour les adresses IP et les URL/domaines](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/manage-indicators#create-indicators-for-ips-and-urlsdomains-preview).

    Cela vous permet de tirer parti des fonctionnalités de protection réseau de l’antivirus Windows Defender pour bloquer l’accès à un ensemble prédéfini d’URL à l’aide de Cloud App Security, soit en attribuant manuellement des [balises d’application](governance-discovery.md#BKMK_SanctionApp) à des applications spécifiques, soit en utilisant automatiquement une [stratégie de découverte d’application](cloud-discovery-policies.md#creating-an-app-discovery-policy).

    ![Capture d’écran montrant comment activer les indicateurs de réseau personnalisés dans Microsoft Defender ATP](media/defender-atp-custom-network-indicators.png)

## <a name="investigate-unsanctioned-apps-in-microsoft-defender-security-center"></a>Examiner les applications non approuvées dans Microsoft Defender Security Center

Chaque tentative d’accès à une application non approuvée déclenche une alerte dans Microsoft Defender Security Center avec des détails détaillés sur l’ensemble de la session. Cela vous permet d’effectuer des investigations plus approfondies dans les tentatives d’accès aux applications non approuvées, ainsi que de fournir des informations pertinentes supplémentaires pour une utilisation dans l’investigation des appareils de point de terminaison.

Parfois, l’accès à une application non approuvée n’est pas bloqué, soit parce que l’appareil de point de terminaison n’est pas configuré correctement, soit parce que la stratégie de mise en application n’a pas encore été propagée vers le point de terminaison. Dans ce cas, les administrateurs de Microsoft Defender ATP reçoivent une alerte dans Microsoft Defender Security Center que l’application non approuvée n’a pas été bloquée.

![Capture d’écran montrant l’alerte de l’application non approuvée de Microsoft Defender ATP](media/defender-atp-unsanctioned-app-alert.png)

> [!NOTE]
>
> - La propagation d’une application **à des appareils** de point de terminaison peut prendre jusqu’à deux heures.
> - Par défaut, les applications et les domaines marqués comme non **approuvés** dans Cloud App Security sont bloqués pour tous les appareils de point de terminaison de l’organisation.
> - Actuellement, les URL complètes ne sont pas prises en charge pour les applications non approuvées. Par conséquent, lors de la non-approbation d’applications configurées avec des URL complètes, elles ne sont pas propagées à Microsoft Defender ATP et ne sont pas bloquées. Par exemple, `google.com/drive` n’est pas pris en charge, tandis que `drive.google.com` est pris en charge.
> - Les notifications dans le navigateur peuvent varier d’un navigateur à l’autre.

## <a name="next-steps"></a>Étapes suivantes :

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

## <a name="related-videos"></a>Vidéos associées

> [!div class="nextstepaction"]
> [Découverte de l’informatique cachée au-delà du réseau d’entreprise](https://www.youtube.com/watch?v=f8hbvbY1Hnc)

[!INCLUDE [Open support ticket](includes/support.md)]
