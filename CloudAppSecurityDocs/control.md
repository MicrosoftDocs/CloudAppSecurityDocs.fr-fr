---
title: Comment utiliser des actions de gouvernance dans Cloud App Security
description: Cet article fournit des informations sur les actions de gouvernance à entreprendre dans Cloud App Security pour contrôler l’usage des applications cloud de votre organisation.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 7143b8a8b98e95dffdd5e27cc56ba9e9b6c6ded5
ms.sourcegitcommit: c174a7ada5c6a14f0fea9870672898c54e5e3b52
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89149822"
---
# <a name="control"></a>Control

*S’applique à : Microsoft Cloud App Security*

Vous pouvez appliquer des actions de gouvernance aux fichiers des utilisateurs dans tout votre environnement cloud. Après avoir soigneusement examiné et étudié votre cloud, vous pouvez utiliser des actions de gouvernance pour protéger votre organisation.

## <a name="use-policies-to-assess-risk"></a>Utiliser des stratégies pour évaluer les risques

Quand vous examinez vos alertes ouvertes, accédez au Centre de stratégie pour passer en revue les violations de stratégie qui n’ont pas déclenché d’alertes.

- Dans le tableau de bord Cloud App Security, cliquez sur **Contrôle**, puis sur **Stratégies**.

- Sélectionnez une stratégie spécifique pour afficher la liste **Mise en correspondance maintenant** des correspondances de stratégie qui n’ont pas déclenché d’alertes.

- Cliquez sur les violations une à une, puis décidez ce qu’il faut faire pour chacune d’elles. Pour plus d’informations sur les actions de gouvernance, consultez les figures suivantes.

    Si votre stratégie est définie pour rechercher des violations de conformité et qu’une personne enregistre des numéros de carte de crédit dans des fichiers sur OneDrive, vous obtenez une correspondance dans la stratégie.

    ![Correspondances PCI](media/pci-matches.png "correspondances pci")

- Sélectionnez la correspondance pour afficher les fichiers qui ont enfreint la stratégie.

    ![Correspondances de contenu PCI](media/pci-content-matches.png "pci, correspondances de contenu")

    Vous pouvez sélectionner le fichier lui-même pour obtenir des informations sur les fichiers.

    Vous pouvez cliquer sur **Collaborateurs** pour voir qui a accès à ce fichier.

    Vous pouvez cliquer sur **Correspondances** pour voir les numéros de carte de crédit.

    ![Le contenu correspond aux numéros de carte de crédit](media/content-matches-ccn.png "le contenu correspond aux numéros de carte de crédit")

## <a name="apply-governance-actions"></a>Appliquer des actions de gouvernance

Vous pouvez appliquer des actions de gouvernance depuis des stratégies, depuis des alertes et depuis le journal **Fichier**.

À tout moment, vous pouvez passer en revue et voir l’état de toutes les actions de gouvernance appliquées en accédant à l’icône **Paramètres** (symbolisée par un engrenage) et en choisissant **Journal de gouvernance**. ![Icône des paramètres](media/settings-icon.png "Icône des paramètres")

En cas d’échec d’une action de gouvernance, choisissez l’icône **Nouvelle tentative** pour l’appliquer à nouveau. ![Icône de nouvelle tentative](media/retry-icon.png "icône de nouvelle tentative")

Selon le type de stratégie, violation et application, différentes actions de gouvernance sont disponibles.

## <a name="move-from-detection-to-automatic-remediation"></a>Passer de la détection à la correction automatique

Après avoir défini et personnalisé vos filtres de stratégie, vous pouvez sélectionner des actions de gouvernance automatisées qui sont déclenchées à chaque violation de votre stratégie.
Étant donné que les actions de correction utilisent les API du fournisseur cloud, ces actions peuvent varier d’une application à l’autre.

> [!NOTE]
> Soyez spécialement prudent quand vous définissez des actions de gouvernance. Elles peuvent entraîner une perte irréversible des autorisations d’accès à vos fichiers.
> Il est recommandé d’affiner les filtres pour représenter exactement les fichiers sur lesquels vous voulez agir, en utilisant plusieurs champs de recherche. Plus les filtres sont précis, mieux c’est.
>
> Pour obtenir des instructions, vous pouvez utiliser le bouton **Modifier et afficher un aperçu des résultats** dans la section **Filtres**.

![Modification et aperçu des résultats des stratégies de fichiers](media/file-policy-edit-and-preview-results.png "stratégie de fichier, modifier et afficher un aperçu des résultats")

## <a name="migration"></a>Migration

Cloud App Security vous permet d’introduire vos migrations en vous faisant savoir qui dans votre organisation utilise quelles applications et en vous donnant les outils nécessaires pour surveiller l’adoption de nouvelles applications. Ce composant peut également vous aider à déterminer quels types d’applications vous pouvez proposer dans votre organisation, en vous fournissant les outils nécessaires pour voir ce que tout le monde utilise déjà.

### <a name="migrate-your-users-to-a-new-app"></a>Migrer vos utilisateurs vers une nouvelle application

Imaginez ce scénario : vous avez récemment acheté Microsoft 365, et vous souhaitez que tous les utilisateurs de votre organisation arrêtent d’utiliser toutes les autres applications de stockage cloud et commencent à utiliser OneDrive. Voici comment vous pouvez procéder :

1. Accédez à votre **tableau de bord Cloud Discovery** et, sous **Catégories**, filtrez les applications par **Stockage cloud**. Triez les résultats par **Utilisateurs** ou par **Adresses IP**, et déterminez quelle est l’application la plus populaire.

2. Vous pouvez voir quels utilisateurs utilisent d’autres applications. Vous pouvez également explorer ces applications de façon détaillée et avertir les utilisateurs que vous voulez qu’ils migrent vers OneDrive, comme suit :

    1. Dans votre **tableau de bord Cloud Discovery**, choisissez **Dropbox**, puis choisissez l’onglet **Adresse IP** ou **Utilisateurs**.

    2. Choisissez l’icône de flèche **Exporter**, puis choisissez vos options d’exportation. ![Icône en forme de flèche](media/arrow-icon.png "Icône en forme de flèche")

### <a name="find-more-secure-alternatives"></a>Trouver des alternatives plus sécurisées

Le catalogue de services Cloud App Security peut vous aider à trouver des alternatives satisfaisantes pour votre organisation et ainsi éviter les applications risquées auxquelles vos utilisateurs peuvent avoir recours.

Imaginons le scénario suivant : vous envisagez d’acheter une application de productivité mais vous n’êtes pas sûr que vos utilisateurs s’en serviront.

1. Accédez au **tableau de bord Cloud Discovery**.

2. Sous **Catégories**, filtrez les applications par **Productivité**.

3. Pour chaque application utilisée, consultez le **Score** pour voir si elle est fiable et, dans le cas contraire, pourquoi.

4. Si vous décidez que vous voulez acheter une licence d’entreprise pour toute l’organisation, vous pouvez examiner la colonne **Utilisateurs**. Vous pouvez voir ici ce qui est déjà le plus répandu parmi vos utilisateurs, si ces applications sont fiables et quelles sont leurs fonctionnalités de sécurité avant de prendre votre décision.

## <a name="next-steps"></a>Étapes suivantes

Pour savoir comment utiliser et configurer des stratégies permettant de contrôler l’utilisation des applications cloud, consultez [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md).

[!INCLUDE [Open support ticket](includes/support.md)]
