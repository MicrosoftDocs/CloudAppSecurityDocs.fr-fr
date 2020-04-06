---
title: Surveiller et protéger des fichiers dans des applications Cloud-Cloud App Security | Microsoft Docs
description: Cet article décrit la procédure de configuration d’une stratégie de données pour surveiller et contrôler les données et les fichiers de l’utilisation des applications Cloud de votre organisation.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/7/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 7c309455b6c7c5a1d46421316eb589038f162726
ms.sourcegitcommit: 288c279a0d2dd62a8ad8d7425c3e9e98857bf5f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2020
ms.locfileid: "80666488"
---
# <a name="file-policies"></a>Stratégies de fichier

*S’applique à : Microsoft Cloud App Security*

Les stratégies de fichier vous permettent d’appliquer un large éventail de processus automatisés à l’aide des API du fournisseur de Cloud. Les stratégies peuvent être définies pour fournir des analyses de conformité continue, des tâches eDiscovery légales, DLP pour le contenu sensible partagé publiquement et bien d’autres cas d’utilisation. Cloud App Security pouvez surveiller n’importe quel type de fichier en fonction de plus de 20 filtres de métadonnées (par exemple, le niveau d’accès, le type de fichier).

## <a name="supported-file-types"></a>Types de fichiers pris en charge

Les moteurs DLP intégrés d’Cloud App Security effectuent l’inspection du contenu en extrayant le texte de tous les types de fichiers courants (plus de 100), y compris Office, Open Office, les fichiers compressés, différents formats de texte enrichi, XML, HTML et bien plus encore.

## <a name="policies"></a>Stratégies

Le moteur combine trois aspects sous chaque stratégie :

* Analyse du contenu basée sur des modèles prédéfinis ou des expressions personnalisées.

* Filtres de contexte incluant des rôles d’utilisateur, des métadonnées de fichier, un niveau de partage, une intégration de groupe organisationnel, un contexte de collaboration et des attributs personnalisables supplémentaires.

* Actions automatisées pour la gouvernance et la correction. Pour plus d’informations, consultez [contrôle](control.md).
    > [!NOTE]
    > Seule l’action de gouvernance de la première stratégie déclenchée est garantie d’être appliquée. Par exemple, si une stratégie de fichier a déjà appliqué une étiquette AIP à un fichier, une deuxième stratégie de fichier ne peut pas lui appliquer une autre étiquette AIP.

Une fois activée, la stratégie analyse en permanence votre environnement Cloud et identifie les fichiers qui correspondent aux filtres de contenu et de contexte, puis applique les actions automatisées demandées. Ces stratégies détectent et corrigent toutes les violations pour les informations au repos ou lors de la création du contenu. Les stratégies peuvent être surveillées à l’aide d’alertes en temps réel ou de rapports générés par la console.

Voici des exemples de stratégies de fichier qui peuvent être créées :

* **Fichiers partagés publiquement** : recevez une alerte sur tous les fichiers de votre Cloud qui sont partagés publiquement en sélectionnant tous les fichiers dont le niveau de partage est public.

* **Le nom de fichier publiquement partagé contient le nom de l’organisation** : recevez une alerte sur tout fichier qui contient le nom de votre organisation et qui est partagé publiquement. Sélectionnez les fichiers dont le nom contient le nom de votre organisation et qui sont partagés publiquement.

* **Partage avec des domaines externes** : recevez une alerte concernant tout fichier partagé avec des comptes appartenant à des domaines externes spécifiques. Par exemple, les fichiers partagés avec le domaine d’un concurrent. Sélectionnez le domaine externe avec lequel vous voulez limiter le partage.

* **Mettre en quarantaine les fichiers partagés non modifiés au cours de la dernière période** : recevez une alerte sur les fichiers partagés qui n’ont pas été modifiés récemment, pour les mettre en quarantaine ou choisissez d’activer une action automatisée. Excluez tous les fichiers privés qui n’ont pas été modifiés pendant une plage de dates spécifiée. Sur G suite, vous pouvez choisir de mettre en quarantaine ces fichiers à l’aide de la case à cocher « fichier en quarantaine » dans la page de création de la stratégie.

* **Partage avec des utilisateurs non autorisés** : recevez une alerte sur les fichiers partagés avec un groupe non autorisé d’utilisateurs dans votre organisation. Sélectionnez les utilisateurs pour qui le partage n’est pas autorisé.

* **Extension de fichier sensible** : recevez une alerte sur les fichiers avec des extensions spécifiques potentiellement très exposées. Sélectionnez l’extension spécifique (par exemple, CRT pour les certificats) ou nom de fichier et excluez ces fichiers avec un niveau de partage privé.

## <a name="create-a-new-file-policy"></a>Créer une stratégie de fichier

Pour créer une stratégie de fichier, procédez comme suit :

1. Dans la console, cliquez sur **contrôle** , puis sur **stratégies**.

1. Cliquez sur **créer une stratégie** et sélectionnez stratégie de **fichier** .

1. Donnez un nom et une description à votre stratégie. Si vous le souhaitez, vous pouvez la baser sur un modèle. pour plus d’informations sur les modèles de stratégie, consultez [contrôler les applications Cloud avec des stratégies](control-cloud-apps-with-policies.md).

1. Donnez à votre stratégie un niveau de **gravité de stratégie**. Si vous avez défini Cloud App Security pour envoyer des notifications sur les correspondances de stratégie pour un niveau de gravité de stratégie spécifique, ce niveau est utilisé pour déterminer si les correspondances de la stratégie déclenchent une notification.

1. Dans **catégorie**, liez la stratégie au type de risque le plus approprié. Ce champ est informatif uniquement et vous permet de rechercher ultérieurement des stratégies et des alertes spécifiques, en fonction du type de risque.  Le risque peut être déjà présélectionné en fonction de la catégorie pour laquelle vous avez choisi de créer la stratégie. Par défaut, les stratégies de fichier ont la valeur DLP.

1. **Créez un filtre pour les fichiers sur lesquels cette stratégie doit agir** pour définir les applications découvertes qui déclenchent cette stratégie. Affinez les filtres de stratégie jusqu’à ce que vous atteigniez un ensemble précis de fichiers sur lesquels vous souhaitez agir. Soyez aussi restrictif que possible pour éviter les faux positifs. Par exemple, si vous souhaitez supprimer les autorisations publiques, n’oubliez pas d’ajouter le filtre **public** , si vous souhaitez supprimer un utilisateur externe, utilisez le filtre « externe », etc.
   > [!NOTE]
   > Lorsque vous utilisez les filtres de stratégie, **contient** des recherches portant uniquement sur des mots entiers, séparés par des virgules, des points, des espaces ou des traits de soulignement. Par exemple, si vous recherchez un **programme malveillant** ou un **virus**, il trouve virus_malware_file. exe, mais il ne trouve pas malwarevirusfile. exe. Si vous recherchez **Malware. exe**, vous trouvez tous les fichiers avec programme malveillant ou exe dans leur nom de fichier, tandis que si vous recherchez **« Malware. exe »** (avec les guillemets), vous ne trouvez que les fichiers qui contiennent exactement « Malware. exe ». **Égal** à recherche uniquement la chaîne complète, par exemple si vous recherchez **Malware. exe** , il trouve Malware. exe, mais pas Malware. exe. txt.
1. Sous le premier filtre **appliquer à** , sélectionnez **tous les fichiers à l’exception de dossiers sélectionnés** ou **dossiers sélectionnés** pour Box, SharePoint, Dropbox, OneDrive, où vous pouvez appliquer votre stratégie de fichier à tous les fichiers de l’application ou à des dossiers spécifiques. Vous êtes redirigé pour vous connecter à l’application Cloud, puis vous ajoutez les dossiers appropriés.

1. Sous le deuxième filtre **appliquer à** , sélectionnez **tous les propriétaires**de fichiers, **propriétaires de fichiers de groupes d’utilisateurs sélectionnés** ou **tous les propriétaires de fichiers à l’exception des groupes sélectionnés**. Sélectionnez ensuite les groupes d’utilisateurs appropriés pour déterminer quels utilisateurs et groupes doivent être inclus dans la stratégie.

1. Sélectionnez la **méthode d’inspection du contenu**. Vous pouvez sélectionner des [**services de classification de données**](content-inspection.md)ou [**DLP intégrés**](content-inspection-built-in.md) . Nous vous recommandons d’utiliser les **services de classification des données**.

    Une fois que l’inspection du contenu est activée, vous pouvez choisir d’utiliser des expressions prédéfinies ou de rechercher d’autres expressions personnalisées.

    En outre, vous pouvez spécifier une expression régulière pour exclure un fichier des résultats. Cette option est très utile si vous avez un mot clé de classification interne standard que vous souhaitez exclure de la stratégie.

    Vous pouvez décider de définir le nombre minimal de violations de contenu que vous souhaitez faire correspondre avant que le fichier ne soit considéré comme une violation. Par exemple, vous pouvez choisir 10 si vous souhaitez être alerté sur des fichiers contenant au moins 10 numéros de carte de crédit trouvés dans son contenu.

    Lorsque le contenu est mis en correspondance avec l’expression sélectionnée, le texte de la violation est remplacé par des caractères « X ». Par défaut, les violations sont masquées et affichées dans leur contexte affichant 100 caractères avant et après la violation. Les nombres dans le contexte de l’expression sont remplacés par des caractères « # » et ne sont jamais stockés dans Cloud App Security. Vous pouvez sélectionner l’option pour afficher les **quatre derniers caractères d’une violation** afin de démasquer les quatre derniers caractères de la violation elle-même. Il est nécessaire de définir les types de données que l’expression régulière recherche : contenu, métadonnées et/ou nom de fichier. Par défaut, elle recherche le contenu et les métadonnées.

1. Choisissez les actions de **gouvernance** que vous souhaitez Cloud App Security prendre lorsqu’une correspondance est détectée.

1. Une fois que vous avez créé votre stratégie, vous pouvez l’afficher sous l’onglet **stratégie de fichier** . Vous pouvez toujours modifier une stratégie, étalonner ses filtres ou modifier les actions automatisées. La stratégie est automatiquement activée lors de la création et démarre immédiatement l’analyse de vos fichiers Cloud.  Soyez particulièrement vigilant lorsque vous définissez des actions de gouvernance. elles peuvent entraîner une perte irréversible des autorisations d’accès à vos fichiers. Il est recommandé de limiter les filtres pour représenter exactement les fichiers sur lesquels vous souhaitez agir, en utilisant plusieurs champs de recherche. Plus les filtres sont étroits, mieux c’est. Pour obtenir de l’aide, vous pouvez utiliser le bouton **modifier et afficher un aperçu des résultats** dans la section filtres.

    ![modifier la stratégie de fichier et afficher un aperçu des résultats](media/file-policy-edit-and-preview-results.png)

1. Pour afficher les correspondances de stratégie de fichier, les fichiers suspects de violer la stratégie, cliquez sur **contrôle** , puis sur **stratégies**. Filtrez les résultats pour afficher uniquement les stratégies de fichiers à l’aide du filtre **type** en haut. Pour plus d’informations sur les correspondances pour chaque stratégie, cliquez sur une stratégie. Les fichiers « match Now » s’affichent pour la stratégie. Cliquez sur l’onglet **historique** pour afficher un historique jusqu’à six mois de fichiers correspondant à la stratégie.

## <a name="file-policy-reference"></a>Référence de stratégie de fichier

Cette section fournit des informations de référence sur les stratégies, ainsi que des explications pour chaque type de stratégie et les champs qui peuvent être configurés pour chaque stratégie.

Une **stratégie de fichier** est une stratégie basée sur une API qui vous permet de contrôler le contenu de votre organisation dans le Cloud, en prenant en compte plus de 20 filtres de métadonnées de fichiers (y compris le niveau de propriétaire et de partage) et les résultats d’inspection du contenu. En fonction des résultats de la stratégie, les actions de gouvernance peuvent être appliquées. Le moteur d’inspection du contenu peut être étendu par le biais de moteurs DLP tiers, ainsi que de solutions anti-programme malveillant.

Chaque stratégie est composée des éléments suivants :

* **Filtres de fichiers** : vous permettent de créer des conditions granulaires basées sur les métadonnées.

* **Inspection du contenu** : vous permet de limiter la stratégie, en fonction des résultats du moteur DLP. Vous pouvez inclure une expression personnalisée ou une expression prédéfinie. Les exclusions peuvent être définies et vous pouvez choisir le nombre de correspondances. Vous pouvez également utiliser l’anonymisation pour masquer le nom d’utilisateur.

* **Actions** : la stratégie fournit un ensemble d’actions de gouvernance qui peuvent être appliquées automatiquement quand des violations sont détectées.  Ces actions sont divisées en actions de collaboration, actions de sécurité et actions d’investigation.

* **Extensions** : l’inspection du contenu peut être effectuée via des moteurs tiers pour améliorer les fonctionnalités DLP ou anti-programme malveillant.

## <a name="file-queries"></a>Requêtes de fichier

Pour faciliter encore plus l’investigation, vous pouvez désormais créer des requêtes personnalisées et les enregistrer pour une utilisation ultérieure.

1. Dans la page **fichier** , utilisez les filtres comme décrit ci-dessus pour accéder à vos applications en fonction des besoins.

1. Une fois que vous avez terminé de créer votre requête, cliquez sur le bouton **Enregistrer sous** dans le coin supérieur droit des filtres.

1. Dans la fenêtre contextuelle **enregistrer la requête** , nommez votre requête.

1. Pour réutiliser cette requête ultérieurement, sous **requêtes**, faites défiler jusqu’à **requêtes enregistrées** et sélectionnez votre requête.

## <a name="next-steps"></a>Étapes suivantes :

> [!div class="nextstepaction"]
> [Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
