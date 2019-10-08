---
title: Surveiller et protéger les fichiers dans les applications cloud - Cloud App Security | Microsoft Docs
description: Cet article décrit la procédure de configuration d’une stratégie de données pour superviser et contrôler les données ainsi que les fichiers durant l’usage des applications cloud de votre organisation.
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
ms.openlocfilehash: 7391832b1be0ed9b50d54f22ee324879fd588d38
ms.sourcegitcommit: 207543b3f7d0489b1275d20c3543964bc6525d1a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71995989"
---
# <a name="file-policies"></a>Stratégies de fichier

*S’applique à : Microsoft Cloud App Security*

Les stratégies de fichier vous permettent d’appliquer une large gamme de processus automatisés en utilisant les API du fournisseur de cloud. Vous pouvez définir des stratégies pour fournir des analyses de conformité en continu, des tâches eDiscovery réglementaires, une protection contre la perte de données (DLP, Data Loss Prevention) au contenu sensible partagé publiquement et de nombreux autres cas d’usage. Cloud App Security peut surveiller n’importe quel type de fichier en fonction de plus de 20 filtres de métadonnées (par exemple, niveau d’accès, type de fichier).

### <a name="supported-file-types"></a>Types de fichiers pris en charge

Les moteurs intégrés de protection contre la perte de données (DLP) de Cloud App Security effectuent l’inspection du contenu en extrayant le texte de tous les types de fichiers courants (plus de 100), dont Office, Open Office, les fichiers compressés, différents formats de texte enrichi, XML, HTML et bien plus encore.

## <a name="policies"></a>Stratégies

Le moteur combine trois aspects sous chaque stratégie :

* Analyse du contenu basé sur des modèles prédéfinis ou des expressions personnalisées.

* Filtres de contexte comprenant des rôles d’utilisateur, des métadonnées de fichiers, un niveau de partage, une intégration des groupes d’organisation, un contexte de collaboration et d’autres attributs personnalisables.

* Actions automatisées pour la gouvernance et la correction. Pour plus d’informations, consultez [Contrôle](control.md).
    > [!NOTE]
    > Une seule action de gouvernance peut être appliquée par fichier ; par conséquent, lorsqu’il existe plusieurs correspondances de stratégie de fichier pour un fichier, l’action de gouvernance de la première stratégie déclenchée est appliquée. Par exemple, si une stratégie de fichier a déjà appliqué une étiquette AIP à un fichier, une deuxième stratégie de fichier ne peut pas déplacer le fichier vers la quarantaine administrateur.

Une fois activée, la stratégie analyse en permanence votre environnement cloud et identifie les fichiers qui correspondent aux filtres de contenu et de contexte, puis applique les actions automatisées demandées. Ces stratégies détectent et corrigent toutes les violations concernant les informations au repos ou le contenu nouvellement créé. Les stratégies peuvent être surveillées avec des alertes en temps réel ou des rapports générés sur une console.

Voici quelques exemples de stratégies de fichier que vous pouvez créer :

* **Fichiers en partage public** - Recevez une alerte quand un fichier situé dans le cloud est partagé publiquement en sélectionnant tous les fichiers dont le niveau de partage est public.

* **Le nom du fichier en partage public contient le nom de l’organisation** - Recevez une alerte quand un fichier contient le nom de votre organisation et qu’il est en partage public. Sélectionnez les fichiers dont le nom contient celui de votre organisation et qui sont publiquement partagés.

* **Partage avec des domaines externes** - Recevez une alerte quand un fichier est partagé avec des comptes appartenant à des domaines externes spécifiques. par exemple des fichiers partagés avec le domaine d’un concurrent. Sélectionnez le domaine externe avec lequel vous voulez limiter le partage.

* **Mettez en quarantaine les fichiers partagés qui n’ont pas été modifiés pendant la dernière période** - Recevez une alerte sur les fichiers partagés que personne n’a modifié dernièrement, pour les mettre en quarantaine ou activer une action automatisée. Excluez tous les fichiers privés qui n’ont pas été modifiés pendant une plage de dates spécifiée. Sur G Suite, vous pouvez choisir de mettre en quarantaine ces fichiers, en cochant la case « Fichier en quarantaine » dans la page de création de stratégie.

* **Partage avec des utilisateurs non autorisés** - Recevez une alerte quand des fichiers sont partagés avec un groupe d’utilisateurs non autorisés dans votre organisation. Sélectionnez les utilisateurs pour lesquels le partage n’est pas autorisé.

* **Extension de fichier sensible** - Recevez une alerte quand des fichiers ayant des extensions spécifiques sont potentiellement très exposés. Sélectionnez l’extension (par exemple crt pour les certificats) ou le nom de fichier spécifique, et excluez les fichiers avec le niveau de partage privé.

## <a name="create-a-new-file-policy"></a>Créer une stratégie de fichier

Pour créer une stratégie de fichier, procédez comme suit :

1. Dans la console, cliquez sur **Contrôle**, puis sur **Stratégies**.

1. Cliquez sur **Créer une stratégie** et sélectionnez la stratégie **Fichier**.

1. Donnez à votre stratégie un nom et une description. Si vous le souhaitez, vous pouvez la baser sur un modèle ; pour plus d’informations sur les modèles de stratégie, consultez [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md).

1. Définissez une **Gravité de la stratégie**. Si Cloud App Security est défini pour vous envoyer des notifications en cas de correspondances de stratégie pour un niveau de gravité de stratégie spécifique, ce niveau est utilisé pour déterminer si les correspondances de cette stratégie déclenchent une notification.

1. Dans **Catégorie**, liez la stratégie au type de risque le plus approprié. Ce champ est à titre informatif uniquement et vous permet de rechercher ultérieurement des stratégies et alertes spécifiques, selon le type de risque.  Le risque est peut-être déjà présélectionné en fonction de la catégorie pour laquelle vous avez choisi de créer la stratégie. Par défaut, les stratégies de fichier ont la valeur DLP.

1. **Créez un filtre pour les fichiers sur lesquels cette stratégie s’appliquera** pour définir les applications découvertes qui déclenchent cette stratégie. Affinez les filtres de stratégie jusqu’à atteindre un ensemble précis de fichiers sur lesquels vous voulez agir. Soyez aussi restrictif que possible pour éviter les faux positifs. Par exemple, si vous voulez supprimer les autorisations publiques, n’oubliez pas d’ajouter le filtre **Public** ; si vous voulez supprimer un utilisateur externe, utilisez le filtre « Externe », etc.
   > [!NOTE]
   > Quand vous utilisez des filtres de stratégie, le filtre **Contains (Contient)** recherche uniquement des mots entiers, séparés par des virgules, points, espaces ou traits de soulignement. Par exemple, si vous recherchez **malware** ou **virus**, il trouve virus_malware_file.exe, mais pas malwarevirusfile.exe. Si vous recherchez **malware.exe**, vous obtenez TOUS les fichiers exe dont le nom contient malware ou exe, tandis que si vous recherchez **"malware.exe"** (avec les guillemets), vous n’obtenez que les fichiers dont le nom contient exactement « malware.exe ». **Equals (Est égal à)** recherche uniquement la chaîne complète ; par exemple, si vous recherchez **malware.exe**, il trouve malware.exe, mais pas malware.exe.txt.
1. Sous le premier filtre **Appliquer à**, sélectionnez **tous les fichiers excepté les dossiers sélectionnés** ou **dossiers sélectionnés** pour Box, SharePoint, Dropbox, OneDrive. Vous pouvez ainsi appliquer votre stratégie de fichiers à tous les fichiers de l’application ou à des dossiers spécifiques. Votre êtes redirigé pour vous connecter à l’application cloud. Ajoutez ensuite les dossiers appropriés.

1. Sous le deuxième filtre **Appliquer à**, sélectionnez **tous les propriétaires de fichiers**, **propriétaires de fichiers de groupes d’utilisateurs sélectionnés** ou **tous les propriétaires de fichiers à l’exception des groupes d’utilisateurs sélectionnés**. Sélectionnez ensuite les groupes d’utilisateurs appropriés pour déterminer les utilisateurs et les groupes à inclure dans la stratégie.

1. Sélectionnez la **Méthode d’inspection du contenu**. Vous pouvez sélectionner [**DLP intégré**](content-inspection-built-in.md) ou [**Services de classification des données**](content-inspection.md). Nous vous recommandons d’utiliser **Services de classification des données**.

    Une fois que l’inspection du contenu est activée, vous pouvez choisir d’utiliser des expressions prédéfinies ou de rechercher d’autres expressions personnalisées.

    De plus, vous pouvez spécifier une expression régulière pour exclure un fichier des résultats. Cette option s’avère très utile si vous avez un standard interne de mots clés de classification à exclure de la stratégie.

    Vous pouvez décider de définir le nombre minimal de violations de contenu à atteindre avant que le fichier ne soit considéré comme une violation. Par exemple, vous pouvez choisir 10 si vous souhaitez être alerté pour les fichiers comportant au moins 10 numéros de carte de crédit détectés dans leur contenu.

    Quand du contenu correspond à l’expression sélectionnée, le texte de la violation est remplacé par des caractères « X ». Par défaut, les violations sont masquées. Seul leur contexte, 100 caractères avant et après la violation, est affiché. Les chiffres dans le contexte de l’expression sont remplacés par des caractères « # » et ne sont jamais stockés dans Cloud App Security. Vous pouvez sélectionner l’option **Montrer les quatre derniers caractères d’une violation** pour annuler le masquage des quatre derniers caractères de la violation elle-même. Il est nécessaire de définir les types de données que l’expression régulière recherche : contenu, métadonnées et/ou nom de fichier. Par défaut, elle recherche le contenu et les métadonnées.

1. Choisissez les actions de **gouvernance** que Cloud App Security doit exécuter quand une correspondance est détectée.

1. Une fois que vous avez créé votre stratégie, vous pouvez l’afficher sous l’onglet **Stratégie de fichier**. Vous pouvez toujours modifier une stratégie, ajuster ses filtres ou modifier les actions automatisées. La stratégie est automatiquement activée lors de la création et démarre immédiatement l’analyse de vos fichiers cloud.  Soyez vigilant quand vous définissez des actions de gouvernance. Elles peuvent entraîner une perte irréversible des autorisations d’accès à vos fichiers. Il est recommandé d’affiner les filtres pour représenter exactement les fichiers sur lesquels vous voulez agir, en utilisant plusieurs champs de recherche. Plus les filtres sont précis, mieux c’est. Pour obtenir des instructions, vous pouvez utiliser le bouton **Modifier et afficher un aperçu des résultats** dans la section Filtres.

    ![stratégie de fichier, modifier et afficher un aperçu des résultats](./media/file-policy-edit-and-preview-results.png)

1. Pour afficher les correspondances de stratégie de fichier, les fichiers qui sont suspectés d’enfreindre la stratégie, cliquez sur **Contrôle**, puis sur **Stratégies**. Filtrez les résultats pour afficher uniquement les stratégies de fichier avec le filtre **Type** en haut. Pour plus d’informations sur les correspondances pour chaque stratégie, cliquez sur une stratégie. Ceci affiche les fichiers « Mise en correspondance maintenant » pour la stratégie. Cliquez sur l’onglet **Historique** pour consulter un historique remontant jusqu’à six mois de fichiers correspondant à la stratégie.

## <a name="file-policy-reference"></a>Informations de référence sur les stratégies de fichier

Cette section fournit des informations de référence sur les stratégies, donne une explication de chaque type de stratégie et décrit les champs que vous pouvez configurer pour chacune d’elles.

Une **stratégie de fichier** est une stratégie basée sur une API qui vous permet de contrôler le contenu de votre organisation dans le cloud, en tenant compte de plus de 20 filtres de métadonnées de fichiers (dont le propriétaire et le niveau de partage), ainsi que les résultats de l’inspection du contenu. Les résultats de la stratégie déterminent les actions de gouvernance applicables. Le moteur d’inspection du contenu peut être étendu par le biais de moteurs DLP tiers, ainsi que de solutions anti-programme malveillant.

Chaque stratégie comprend les éléments suivants :

* **Filtres de fichiers** - Vous permettent de créer des conditions précises en fonction des métadonnées.

* **Inspection du contenu** - Vous permet de limiter la stratégie, en fonction des résultats du moteur DLP. Vous pouvez inclure une expression personnalisée ou prédéfinie. Vous pouvez définir des exclusions et choisir le nombre de correspondances. Vous pouvez aussi utiliser l’anonymisation pour masquer le nom de l’utilisateur.

* **Actions** - La stratégie fournit un ensemble d’actions de gouvernance automatiquement applicables en cas de violations.  Ces actions sont réparties en actions de collaboration, de sécurité et d’examen.

* **Extensions** - L’inspection du contenu peut être effectuée via des moteurs tiers pour améliorer les fonctionnalités DLP ou antiprogramme malveillant.

## <a name="file-queries"></a>Requêtes de fichier

Pour faciliter encore plus les recherches, vous pouvez désormais créer des requêtes personnalisées et les enregistrer pour les utiliser ultérieurement.

1. Dans la page **fichier** , utilisez les filtres comme décrit ci-dessus pour accéder à vos applications en fonction des besoins.

1. Une fois que vous avez terminé de générer votre requête, cliquez sur le bouton **Enregistrer sous** en haut à droite des filtres.

1. Dans la fenêtre contextuelle **Enregistrer la requête**, nommez votre requête.

1. Pour réutiliser cette requête plus tard, sous **Requêtes**, faites défiler jusqu’à **Requêtes enregistrées** et sélectionnez votre requête.

## <a name="next-steps"></a>Étapes suivantes

[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)
