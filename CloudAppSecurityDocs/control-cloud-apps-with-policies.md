---
title: Contrôler l’utilisation des applications Cloud en créant des stratégies-Cloud App Security | Microsoft Docs
description: Cet article fournit des informations sur l’utilisation et la configuration des stratégies pour contrôler l’utilisation des applications Cloud.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 09/26/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: e4675430b45e92579cd4c692247c5a481bad233e
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285613"
---
# <a name="control-cloud-apps-with-policies"></a>Contrôler les applications cloud avec des stratégies

*S’applique à : Microsoft Cloud App Security*

Les stratégies vous permettent de définir la façon dont vous souhaitez que vos utilisateurs se comportent dans le Cloud. Elles vous permettent de détecter les comportements risqués, les violations, les points de données et les activités suspects dans votre environnement Cloud. Si nécessaire, vous pouvez intégrer des flux de travail de correction pour réaliser une atténuation des risques complète. Il existe plusieurs types de stratégies en corrélation avec les différents types d’informations que vous souhaitez collecter sur votre environnement Cloud et les types d’actions correctives que vous pouvez entreprendre.

Par exemple, si vous souhaitez mettre en quarantaine une menace de violation de données, vous avez besoin d’un autre type de stratégie en place que si vous souhaitez empêcher une application Cloud risquée d’être utilisée par votre organisation.

## <a name="policy-types"></a>Types de stratégie

Lorsque vous examinez la page **stratégie** , les différentes stratégies et les différents modèles peuvent être distingués par type et par icône pour voir quelles stratégies sont disponibles. Les stratégies disponibles dépendent de la source de données et de ce que vous avez activé dans Cloud App Security pour votre organisation. Par exemple, si vous avez chargé Cloud Discovery journaux, les stratégies relatives à Cloud Discovery sont affichées.

Vous pouvez créer les types de stratégies suivants :

|Icône type de stratégie|Type de stratégie|Utilisez|
|-----|-----------------|---------|
|![icône de stratégie d’accès](media/proxy-policy.png)|Stratégie d’accès|Les stratégies d’accès vous offrent une surveillance et un contrôle en temps réel des connexions utilisateur à vos applications Cloud.|
|![icône stratégie d’activité](media/activity_policy.png)|Stratégie d’activité|Les stratégies d’activité vous permettent d’appliquer une large gamme de processus automatisés à l’aide des API du fournisseur d’applications. Ces stratégies vous permettent de surveiller des activités spécifiques effectuées par différents utilisateurs ou de suivre les taux inattendus d’un certain type d’activité.|
|![icône de stratégie de détection d’anomalies](media/anomaly_detection_policy.png)|Stratégie de détection des anomalies|Les stratégies de détection des anomalies vous permettent de rechercher des activités inhabituelles dans votre Cloud. La détection est basée sur les facteurs de risque que vous définissez pour vous avertir en cas de problème qui diffère de la ligne de base de votre organisation ou de l’activité ordinaire de l’utilisateur.|
|![icône de stratégie Cloud Discovery](media/discovery_policy.png)|Stratégie de découverte d’application|Les stratégies de détection d’application vous permettent de définir des alertes qui vous informent quand de nouvelles applications sont détectées au sein de votre organisation.|
|![icône de stratégie de détection d’anomalies](media/anomaly_detection_policy.png)|Stratégie de détection des anomalies Cloud Discovery|Cloud Discovery stratégies de détection des anomalies examinent les journaux que vous utilisez pour découvrir les applications Cloud et recherche des occurrences inhabituelles. Par exemple, lorsqu’un utilisateur qui n’a jamais utilisé Dropbox pour télécharger 600 Go sur Dropbox, ou quand il y a beaucoup plus de transactions que d’habitude sur une application particulière.|
|![icône de stratégie de fichier](media/file_policy.png)|Stratégie de fichier|Les stratégies de fichier vous permettent d’analyser vos applications Cloud à la recherche de fichiers ou de types de fichiers spécifiés (partagés, partagés avec des domaines externes), de données (informations propriétaires, données personnelles, informations de carte de crédit et autres types de données) et d’appliquer des actions de gouvernance aux fichiers ( les actions de gouvernance sont spécifiques à l’application Cloud).|
|![icône de stratégie de session](media/proxy-policy.png)|Stratégie de session|Les stratégies de session vous permettent de surveiller et de contrôler en temps réel l’activité des utilisateurs dans vos applications Cloud.|

## <a name="identifying-risk"></a>Identification des risques

Cloud App Security vous aide à atténuer les différents risques dans le Cloud. Vous pouvez configurer toute stratégie et alerte à associer à l’un des risques suivants :

- **Contrôle d’accès :** Qui accède à quoi ?

    Surveillez le comportement et détectez les activités anormales, y compris les attaques externes et internes à haut risque, et appliquez une stratégie d’alerte, de blocage ou de vérification d’identité pour toute application ou action spécifique au sein d’une application. Active les stratégies de contrôle d’accès mobile et local en fonction de l’utilisateur, de l’appareil et de la géographie avec blocage grossiste et vue granulaire, modification et bloc. Détecte les événements de connexion suspects, notamment les échecs d’authentification multifacteur, les échecs de connexion aux comptes désactivés et les événements d’emprunt d’identité.

- **Conformité :** Vos exigences en matière de conformité sont-elles enfreintes ?

    Cataloguez et identifiez les données sensibles ou réglementées, y compris les autorisations de partage pour chaque fichier, stockées dans les services de synchronisation de fichiers pour garantir la conformité avec les réglementations telles que PCI, SOX et HIPAA.

- **Contrôle de configuration :** Des modifications non autorisées sont-elles apportées à votre configuration ?

    Surveiller les modifications de configuration, notamment la manipulation de configuration à distance.

- **Cloud Discovery :** Les nouvelles applications sont-elles utilisées dans votre organisation ? Avez-vous un problème d’utilisation d’applications informatiques fictives que vous ne connaissez pas ?

    Évaluez le risque global pour chaque application Cloud en fonction des certifications et des pratiques recommandées. Vous permet de surveiller le nombre d’utilisateurs, les activités, le volume de trafic et les heures d’utilisation typiques pour chaque application Cloud.

- **DLP :** Des fichiers propriétaires sont-ils partagés publiquement ? Avez-vous besoin de mettre en quarantaine les fichiers ?

    L’intégration DLP locale assure l’intégration et la correction de la boucle fermée avec les solutions DLP locales existantes.

- **Comptes privilégiés :** Avez-vous besoin de surveiller les comptes d’administrateur ?

    Surveillance de l’activité en temps réel et création de rapports d’utilisateurs et d’administrateurs privilégiés.

- **Contrôle de partage :** Comment les données sont-elles partagées dans votre environnement cloud ?

    Inspectez le contenu des fichiers et du contenu dans le Cloud et appliquez des stratégies de partage interne et externe. Surveillez la collaboration et appliquez des stratégies de partage, telles que le partage de fichiers en dehors de votre organisation.

- **Détection des menaces :** Y a-t-il des activités suspectes menaçant votre environnement cloud ?

    Recevoir des notifications en temps réel pour toute violation de stratégie ou seuil d’activité via un message texte ou un e-mail. En appliquant Machine Learning algorithmes, Cloud App Security vous permet de détecter un comportement qui peut indiquer qu’un utilisateur utilise des données de manière inutilisée.

## <a name="how-to-control-risk"></a>Comment contrôler les risques

Suivez ce processus pour contrôler les risques liés aux stratégies :

1. Créer une stratégie à partir d’un modèle ou d’une requête.

1. Ajustez la stratégie pour obtenir les résultats attendus.

1. Ajoutez des actions automatisées pour répondre et corriger automatiquement les risques.

### <a name="create-a-policy"></a>Créer une stratégie

Vous pouvez utiliser les modèles de stratégie d’Cloud App Security comme base pour toutes vos stratégies ou créer des stratégies à partir d’une requête.

Les modèles de stratégie vous aident à définir les filtres et configurations appropriés nécessaires à la détection des événements spécifiques qui vous intéressent dans votre environnement. Les modèles incluent des stratégies de tous types et peuvent s’appliquer à divers services.

Pour créer une stratégie à partir de **modèles de stratégie**, procédez comme suit :

1. Dans la console, cliquez sur **contrôle** , puis sur **modèles**.

    ![Créer la stratégie à partir d’un modèle](media/create-policy-from-template.png)

1. Cliquez sur l' **+** à l’extrême droite de la ligne du modèle que vous souhaitez utiliser. Une page créer une stratégie s’ouvre, avec la configuration prédéfinie du modèle.

1. Modifiez le modèle en fonction des besoins de votre stratégie personnalisée. Chaque propriété et champ de cette nouvelle stratégie basée sur un modèle peut être modifié en fonction de vos besoins.
   > [!NOTE]
   > Lorsque vous utilisez les filtres de stratégie, **contient** des recherches portant uniquement sur des mots entiers, séparés par des virgules, des points, des espaces ou des traits de soulignement. Par exemple, si vous recherchez un **programme malveillant** ou un **virus**, il trouve virus_malware_file. exe, mais il ne trouve pas malwarevirusfile. exe. Si vous recherchez *Malware. exe*, vous trouvez tous les fichiers avec programme malveillant ou exe dans leur nom de fichier, tandis que si vous recherchez **« Malware. exe »** (avec les guillemets), vous ne trouverez que les fichiers qui contiennent exactement « Malware. exe ».  
**Égal** à recherche uniquement la chaîne complète, par exemple si vous recherchez *Malware. exe* , il trouve Malware. exe, mais pas Malware. exe. txt.

1. Une fois que vous avez créé la nouvelle stratégie basée sur un modèle, un lien vers la nouvelle stratégie s’affiche dans la colonne **stratégies liées** de la table des modèles de stratégie, en regard du modèle à partir duquel la stratégie a été créée.
    Vous pouvez créer autant de stratégies que vous le souhaitez à partir de chaque modèle, et elles seront toutes liées au modèle d’origine. La liaison vous permet d’effectuer le suivi de toutes les stratégies générées à l’aide du même modèle.

Vous pouvez également **créer une stratégie au cours de l’investigation**. Si vous examinez le **Journal d’activité**, les **fichiers** ou les **comptes**, et que vous explorez pour rechercher un objet spécifique, vous pouvez à tout moment créer une nouvelle stratégie basée sur les résultats de votre investigation.

Par exemple, si vous examinez le **Journal d’activité**et que vous voyez une activité d’administration à partir de l’extérieur des adresses IP de votre bureau.

Pour créer une stratégie basée sur les résultats de l’investigation, procédez comme suit :

1. Dans la console, cliquez sur **examiner** , puis sur **Journal d’activité**, **fichiers**ou **comptes**.

1. Utilisez les filtres en haut de la page pour limiter les résultats de la recherche à la zone suspecte. Par exemple, dans la page Journal d’activité, cliquez sur **type d’activité** , puis sélectionnez **administrateurs d’écriture** sous opération Azure. Ensuite, sous **adresse IP**, sélectionnez **catégorie** et définissez la valeur sur ne pas inclure les catégories d’adresses IP que vous avez créées pour vos domaines reconnus, tels que les adresses IP de l’administrateur, de l’entreprise et du VPN.

    ![Créer un fichier à partir de l’investigation](media/create-file-from-investigation.png)

1. Dans le coin supérieur droit de la console, cliquez sur **nouvelle stratégie à partir de la recherche**.

    ![Nouvelle stratégie à partir du bouton de recherche](media/new-policy-from-search-button.png)

1. Une page de création de stratégie s’ouvre, contenant les filtres que vous avez utilisés dans votre investigation.

1. Modifiez le modèle en fonction des besoins de votre stratégie personnalisée. Chaque propriété et champ de cette nouvelle stratégie basée sur l’investigation peut être modifié en fonction de vos besoins.

    > [!NOTE]
    > Lorsque vous utilisez les filtres de stratégie, **contient** des recherches portant uniquement sur des mots entiers, séparés par des virgules, des points, des espaces ou des traits de soulignement. Par exemple, si vous recherchez un **programme malveillant** ou un **virus**, il trouve virus_malware_file. exe, mais il ne trouve pas malwarevirusfile. exe.  
**Égal** à recherche uniquement la chaîne complète, par exemple si vous recherchez **Malware. exe** , il trouve Malware. exe, mais pas Malware. exe. txt.

    ![créer une stratégie d’activité à partir de l’investigation](media/create-activity-policy-from-investigation.png)

    > [!NOTE]
    > Pour plus d’informations sur la définition des champs de stratégie, consultez la documentation de stratégie correspondante :
    >
    > [Stratégies d’activité utilisateur](user-activity-policies.md)
    >
    > [Stratégies de protection des données](data-protection-policies.md)
    >
    > [Stratégies Cloud Discovery](cloud-discovery-policies.md)

### <a name="add-automated-actions-to-respond-and-remediate-risks-automatically"></a>Ajouter des actions automatisées pour répondre et corriger automatiquement les risques

Pour obtenir la liste des actions de gouvernance disponibles par application, consultez la rubrique relative aux [applications connectées](governance-actions.md).

Vous pouvez également définir la stratégie pour qu’elle vous envoie une alerte par courrier électronique ou par message texte lorsque des correspondances sont détectées.

Pour définir vos préférences de notification, vous avez réussi à [personnaliser le portail](general-setup.md)

> [!NOTE]
> Le nombre maximal d’alertes envoyées via SMS est de 10 par numéro de téléphone par jour. Le jour est calculé en fonction du fuseau horaire UTC.

## <a name="enable-and-disable-policies"></a>Activer et désactiver des stratégies

Une fois que vous avez créé une stratégie, vous pouvez l’activer ou la désactiver. Si vous désactivez cette opération, vous n’avez plus besoin de supprimer une stratégie après l’avoir créée afin de l’arrêter. Au lieu de cela, si vous souhaitez arrêter la stratégie pour une raison quelconque, désactivez-la jusqu’à ce que vous choisissiez de la réactiver.

- Pour activer une stratégie, dans la page **stratégie** , cliquez sur les trois points à la fin de la ligne de la stratégie que vous souhaitez activer. Sélectionnez **activer**.

    ![Activer la stratégie](media/enable-policy.png)

- Pour désactiver une stratégie, dans la page **stratégie** , cliquez sur les trois points à la fin de la ligne de la stratégie que vous souhaitez désactiver. Sélectionnez **Désactiver**.

    ![Désactiver la stratégie](media/disable-policy.png)

Par défaut, après avoir créé une nouvelle stratégie, elle est activée.

## <a name="policies-overview-report"></a>Rapport vue d’ensemble des stratégies

Cloud App Security vous permet d’exporter un rapport vue d’ensemble des stratégies présentant des métriques d’alerte agrégées par stratégie pour vous aider à surveiller, à comprendre et à personnaliser vos stratégies afin de mieux protéger votre organisation.

Pour exporter un journal, procédez comme suit :

1. Dans la page **stratégies** , cliquez sur le bouton **Exporter** .

1. Spécifiez l’intervalle de temps requis.

1. Cliquez sur **Exporter**. Ce processus peut prendre un certain temps.

Pour télécharger le rapport exporté :

1. Une fois le rapport prêt, accédez à **paramètres** , puis **rapports exportés**.

1. Dans le tableau, sélectionnez le rapport approprié dans le **rapport vue d’ensemble** de la liste des stratégies, puis cliquez sur Télécharger.

    ![bouton Télécharger](media/download-button.png)

## <a name="next-steps"></a>Étapes suivantes :

> [!div class="nextstepaction"]
> [Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
