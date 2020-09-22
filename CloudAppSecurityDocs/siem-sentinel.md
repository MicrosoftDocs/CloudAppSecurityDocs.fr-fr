---
title: Intégration d’Azure Sentinel à Cloud App Security
description: Cet article fournit des informations sur l’intégration d’Azure Sentinel avec Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 08/23/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 154cb0eda5a223c31813e1753b9dc0bcb8836436
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90878713"
---
# <a name="azure-sentinel-integration-preview"></a>Intégration d’Azure Sentinel (version préliminaire)

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Vous pouvez intégrer des Microsoft Cloud App Security avec Azure Sentinel (une SIEM et une dépassement en base de la base Cloud et de la décoller) pour permettre une surveillance centralisée des alertes et des données de découverte. L’intégration avec Azure Sentinel vous permet de mieux protéger vos applications Cloud tout en conservant votre flux de travail de sécurité habituel, en automatisant les procédures de sécurité et en mettant en corrélation les événements Cloud et locaux.

Les avantages de l’utilisation d’Azure Sentinel sont les suivants :

* Rétention des données plus longue fournie par Log Analytics.
* Visualisations prêtes à l’emploi.
* Utilisez des outils tels que Microsoft Power BI ou des classeurs Azure Sentinel pour créer vos propres visualisations de données de découverte adaptées aux besoins de votre organisation.

Les solutions d’intégration supplémentaires sont les suivantes :

* **Siem génériques** : intégrez Cloud App Security à votre serveur Siem générique. Pour plus d’informations sur l’intégration à une SIEM générique, consultez [intégration Siem générique](siem.md).
* **API Microsoft Security Graph** : service intermédiaire (ou répartiteur) qui fournit une interface de programmation unique pour connecter plusieurs fournisseurs de sécurité. Pour plus d’informations, consultez [intégration de solutions de sécurité à l’aide de l’API Microsoft Graph Security](/graph/security-integration#list-of-connectors-from-microsoft).

## <a name="how-to-integrate"></a>Processus d’intégration

L’intégration à votre serveur SIEM s’effectue en deux étapes :

1. Configurez-le dans Cloud App Security.
1. Configurez-le dans Azure Sentinel.

> [!NOTE]
> L’option permettant d’ajouter Azure Sentinel n’est pas disponible si vous avez déjà effectué l’intégration.

### <a name="prerequisites"></a>Prérequis

Pour une intégration avec Azure Sentinel :

* Vous devez disposer d’une licence Azure Sentinel valide
* Vous devez être administrateur général ou administrateur de la sécurité dans votre locataire.

### <a name="integrating-with-azure-sentinel"></a>Intégration à Azure Sentinel

1. Dans le portail Cloud App Security, sous **paramètres** roue dentée, cliquez sur **extensions de sécurité**.

1. Dans l’onglet **agents Siem** , cliquez sur Ajouter ( **+** ), puis choisissez **Azure Sentinel**.

    ![Capture d’écran montrant le menu Ajouter une intégration SIEM](media/siem0.png)

1. Dans l’Assistant, sélectionnez les types de données que vous souhaitez transférer vers Azure Sentinel. Vous pouvez configurer l’intégration comme suit :
    1. **Alertes**: les alertes sont activées automatiquement une fois qu’Azure Sentinel est activé. <!--Use the **Apply to** drop-down to filter which alerts are sent to Azure Sentinel.-->
    1. **Journaux de découverte**: utilisez le curseur pour les activer et les désactiver. par défaut, tout est sélectionné, puis utilisez la liste déroulante **appliquer à** pour filtrer les journaux de découverte envoyés à Azure Sentinel.

    ![Capture d’écran montrant la page de démarrage de configurer l’intégration d’Azure Sentinel](media/siem-sentinel-configuration.png)

1. Cliquez sur **suivant**, puis passez à Azure Sentinel pour finaliser l’intégration. Pour plus d’informations sur la configuration d’Azure Sentinel, consultez [/Azure/Sentinel/Connect-Cloud-App-Security](/azure/sentinel/connect-cloud-app-security).

    ![Capture d’écran montrant la page terminer de configurer l’intégration d’Azure Sentinel](media/siem-sentinel-configuration-complete.png)

> [!NOTE]
> Les nouveaux journaux de découverte démarreront le transfert vers Azure Sentinel dans les 15 minutes qui vous permettront de les configurer dans le portail de Cloud App Security.

## <a name="alerts-and-discovery-logs-in-azure-sentinel"></a>Alertes et journaux de découverte dans Azure Sentinel

Une fois l’intégration terminée, vous pouvez afficher Cloud App Security les alertes et les journaux de découverte dans Azure Sentinel.

Dans Azure Sentinel, sous **journaux**, sous **Insights de sécurité**, vous trouverez les journaux des types de données Cloud App Security, comme suit :

| Type de données | Table de charge de travail |
| --- | --- |
| Journaux de découverte | McasShadowItReporting |
| Alertes | SecurityAlert |

Le tableau suivant décrit chaque champ dans le schéma **McasShadowItReporting** :

| Champ | Type | Description | Exemples |
| --- | --- | --- | --- |
| TenantId | String | ID de l’espace de travail | b459b4u5-912x-46d5-9cb1-p43069212nb4 |
| SourceSystem | String | Système source – valeur statique | Azure |
| TimeGenerated [UTC] | DateTime | Date des données de découverte | 2019-07-23T11:00:35.858 Z |
| StreamName | Chaîne | Nom du flux spécifique | Service marketing |
| TotalEvents | Entier | Nombre total d’événements par session | 122 |
| BlockedEvents | Entier | Nombre d’événements bloqués | 0 |
| UploadedBytes | Entier | Quantité de données chargées | 1 514 874 |
| TotalBytes | Entier | Quantité totale de données | 4 067 785 |
| DownloadedBytes | Entier | Quantité de données téléchargées | 2 552 911 |
| IpAddress | Chaîne | Adresse IP source | 127.0.0.0 |
| UserName | Chaîne | Nom d’utilisateur | `Raegan@contoso.com` |
| EnrichedUserName | Chaîne | Nom d’utilisateur enrichi avec Azure AD nom d’utilisateur | `Raegan@contoso.com` |
| AppName | Chaîne | Nom de l’application Cloud | Microsoft OneDrive Entreprise |
| AppId | Entier | Identificateur d’application Cloud | 15600 |
| AppCategory | Chaîne | Catégorie d’application Cloud | Stockage cloud |
| AppTags | Tableau de chaînes | Balises intégrées et personnalisées définies pour l’application | [« approuvé »] |
| AppScore | Entier | Le score de risque de l’application dans une échelle de 0-10, 10 étant un score pour une application non risquée | 10 |
| Type | String | Type de journaux – valeur statique | McasShadowItReporting |

## <a name="use-power-bi-with-cloud-app-security-data-in-azure-sentinel"></a>Utiliser Power BI avec les données Cloud App Security dans Azure Sentinel

Une fois l’intégration terminée, vous pouvez également utiliser les données de Cloud App Security stockées dans Azure Sentinel dans d’autres outils.

Cette section décrit comment vous pouvez utiliser Microsoft Power BI (Power BI) pour mettre en forme et combiner facilement des données pour créer des rapports et des tableaux de bord qui répondent aux besoins de votre organisation.

Vous pouvez commencer rapidement en procédant comme suit :

1. Dans Power BI, importez des requêtes à partir d’Azure Sentinel pour les données de Cloud App Security. Pour plus d’informations, consultez [importer des données de journal Azure Monitor dans Power bi](/azure/azure-monitor/platform/powerbi).
1. [Installez l’application Cloud App Security Shadow IT Discovery](https://aka.ms/MCASShadowITReporting) et [Connectez-](#connect-the-cloud-app-security-app) la à vos données de journal de découverte pour afficher le tableau de bord Shadow IT Discovery intégré.

    > [!NOTE]
    > Actuellement, l’application n’est pas publiée sur Microsoft AppSource. Par conséquent, vous devrez peut-être contacter votre administrateur Power BI pour obtenir les autorisations nécessaires pour installer l’application.

    ![Capture d’écran montrant le tableau de bord Shadow IT Discovery](media/siem-sentinel-configuration-powerbi-dashboard.png)

1. Si vous le souhaitez, créez des tableaux de bord personnalisés dans Power BI Desktop et ajustez-les en fonction des besoins d’analyse visuelle et de création de rapports de votre organisation.

### <a name="connect-the-cloud-app-security-app"></a>Connexion de l’application Cloud App Security

1. Dans Power BI, cliquez sur **applications**, puis sur l’application **Shadow IT Discovery** .

1. Sur la page **prise en main de votre nouvelle application** , cliquez sur **se connecter**.

    ![Capture d’écran montrant la page de connexion des données de l’application](media/siem-sentinel-powerbi-connect.png)

1. Dans la page ID de l’espace de travail, entrez votre ID d’espace de travail Azure Sentinel tel qu’il apparaît dans la page de présentation de log Analytics, puis cliquez sur **suivant**.

    ![Capture d’écran montrant la demande d’ID d’espace de travail](media/siem-sentinel-powerbi-workspace-id.png)

1. Sur la page authentification, spécifiez la méthode d’authentification et le niveau de confidentialité, puis cliquez sur **se connecter**.

    ![Capture d’écran montrant la page d’authentification](media/siem-sentinel-powerbi-authentication.png)

1. Une fois que vous avez connecté vos données, accédez à l’onglet **jeux** de données de l’espace de travail, puis cliquez sur **Actualiser**. Le rapport sera mis à jour avec vos propres données.

[!INCLUDE [Open support ticket](includes/support.md)]