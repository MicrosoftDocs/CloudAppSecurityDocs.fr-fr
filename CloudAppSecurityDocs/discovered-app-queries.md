---
title: Cloud App Security les filtres et les requêtes d’application détectés
description: Cet article fournit une liste de Cloud App Security filtres et requêtes d’application découverts et explique comment les utiliser.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: ba9848bf0f9cbcee326cdebfaed09b95f38fe267
ms.sourcegitcommit: 445a7c208455e6ce2c4e13b028c811f4c3486290
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78342282"
---
# <a name="discovered-app-filters-and-queries"></a>Filtres et requêtes des applications découvertes

*S’applique à : Microsoft Cloud App Security*

Lorsque vous avez un grand nombre d’applications découvertes, il est utile de les filtrer et de les interroger. Cet article décrit les filtres disponibles et comment interroger vos applications découvertes.

## <a name="discovered-app-filters"></a>Filtres d’application découverte

Il existe des filtres d’application découverte de base et avancés. Pour obtenir un filtre complexe (comme dans l’exemple ci-dessus), utilisez l’option avancé, qui comprend tous les filtres suivants :

![Applications découvertes](media/discovered-apps.png)

- **Balise d’application** : Indiquez si l’application a été approuvée, non approuvée ou non marquée. En outre, vous pouvez créer une balise personnalisée pour votre application, puis l’utiliser pour filtrer des types spécifiques d’applications.
- **Applications et domaines** : Permet de rechercher des applications spécifiques ou des applications utilisées dans des domaines spécifiques.
- **Catégories**: le filtre catégories, situé à gauche de la page, vous permet de rechercher des types d’applications en fonction des catégories d’applications. Parmi les exemples de catégories, citons les applications de réseau social, les applications de stockage cloud et les services d’hébergement. Vous pouvez sélectionner plusieurs catégories à la fois, ou une seule catégorie, puis appliquer les filtres de base et avancés en plus.
- **Facteur de risque de conformité**: vous permet de rechercher les normes, la certification et la conformité spécifiques auxquelles l’application peut se conformer (HIPAA, ISO 27001, SOC 2, PCI-DSS, etc.).
- **Facteur de risque général**: vous permet de rechercher des facteurs de risque généraux tels que la popularité des consommateurs, les paramètres régionaux du centre de données et bien plus encore.
- **Score de risque**: vous permet de filtrer les applications par score de risque pour que vous puissiez vous concentrer sur, par exemple, la consultation des applications à haut risque. Vous pouvez également remplacer le score de risque défini par Cloud App Security. Pour plus d’informations, consultez [utilisation du score de risque](risk-score.md).
- **Facteur de risque de sécurité** : Permet de filtrer en fonction de mesures de sécurité spécifiques (comme le chiffrement au repos, l’authentification multifacteur, etc.).
- **Utilisation**: vous permet de filtrer en fonction des statistiques d’utilisation de cette application. Utilisation, comme les applications, avec un nombre d’utilisateurs inférieur ou égal à un nombre spécifié de **chargements de données**, les applications avec plus ou moins qu’un nombre spécifié d' **utilisateurs**.
- **Facteur de risque légal**: vous permet de filtrer en fonction de toutes les réglementations et stratégies en place pour garantir la protection et la confidentialité des données des utilisateurs de l’application. Exemples : applications Cloud RGPD Ready, DMCA et stratégie de rétention des données.

### <a name="creating-and-managing-custom-app-tags"></a>Création et gestion des balises d’application personnalisées

Vous pouvez créer une balise d’application personnalisée.
Ces balises peuvent ensuite servir de filtres pour rechercher plus précisément des types spécifiques d’applications que vous voulez examiner. Par exemple, une liste de suivi personnalisée, l’attribution à une division spécifique ou des approbations personnalisées, comme « approuvé par le service juridique ».

Pour créer une balise d’application personnalisée :

1. Dans la roue dentée **paramètres** , sélectionnez **paramètres Cloud Discovery**, puis l’onglet **balises d’application** . cliquez sur l’icône plus. icône ![plus](media/plus-icon.png)

   ![créer une balise d’application personnalisée](media/create-app-tag.png)

2. Vous pouvez utiliser le tableau **balises d’application** pour afficher les applications qui sont actuellement marquées avec chaque balise d’application et vous pouvez supprimer les balises d’application inutilisées.

3. Pour appliquer une balise d’application, sous l’onglet **applications découvertes** , cliquez sur les trois points à l’extrême droite du nom de l’application. Sélectionnez la balise d’application à appliquer.

> [!NOTE]
>Vous pouvez également créer une balise d’application directement dans le tableau **Applications découvertes** en cliquant sur **Créer une balise d’application** après avoir sélectionné les points de suspension à droite de n’importe quelle application sélectionnée. Lorsque vous créez la balise à partir de l’application découverte, vous pouvez l’appliquer à l’application. Vous pouvez également accéder à l’écran **balises d’application** en cliquant sur le lien **gérer les balises** dans l’angle.
> ![créer une balise d’application personnalisée à partir de l’application](media/create-app-tag-from-app.png)

## <a name="discovered-app-queries"></a>Requêtes d’application découvertes

Pour faciliter encore plus l’investigation, vous pouvez créer des requêtes personnalisées et les enregistrer pour une utilisation ultérieure.

1. Dans la page **applications découvertes** , utilisez les filtres comme décrit ci-dessus pour analyser en détail vos applications en fonction des besoins.

2. Une fois que vous avez obtenu les résultats souhaités, cliquez sur le bouton **Enregistrer sous** dans le coin supérieur droit des filtres.

3. Dans la fenêtre contextuelle **enregistrer la requête** , nommez votre requête.

    ![nouvelle requête](media/new-query.png)

4. Pour réutiliser cette requête ultérieurement, sous **requêtes**, faites défiler jusqu’à **requêtes enregistrées** et sélectionnez votre requête.

    ![ouvrir la requête](media/discovered-app-query.png)

Cloud App Security vous fournit également des **suggestions de requêtes** et vous permet d’enregistrer des requêtes personnalisées que vous utilisez fréquemment. Les requêtes suggérées vous fournissent des voies d’investigation recommandées qui filtrent vos applications découvertes en utilisant les requêtes suggérées facultatives suivantes :

- **Applications Cloud qui autorisent une utilisation anonyme** : filtre toutes vos applications découvertes pour afficher uniquement les applications qui présentent des risques de sécurité, car elles ne nécessitent pas d’authentification utilisateur et permettent aux utilisateurs de télécharger des données.

- **Applications Cloud certifiées CSA en étoile** -filtre toutes vos applications découvertes pour afficher uniquement les applications qui ont une certification CSA Star par le biais de l’auto-évaluation, de la certification, de l’attestation ou de la surveillance continue.

- **Applications Cloud compatibles FedRAMP** : filtre toutes vos applications découvertes pour afficher uniquement les applications dont le facteur de risque de conformité FedRAMP est élevé, moyen ou faible.

- **Applications de stockage et de collaboration Cloud qui possèdent des données utilisateur** : filtre toutes vos applications découvertes pour afficher uniquement les applications risquées, car elles ne vous permettent pas de vous approprier vos données, mais elles conservent vos données.

- **Applications de stockage cloud risquées et non conformes** : filtre toutes vos applications découvertes pour afficher uniquement les applications pour lesquelles elles ne sont pas compatibles avec SOC 2 ou HIPAA. elles ne prennent pas en charge la version PCI DSS et elles ont un score de risque inférieur ou supérieur à 5.

- **Applications Cloud d’entreprise avec une authentification faible** : filtre toutes vos applications découvertes pour afficher uniquement les applications qui ne prennent pas en charge SAML, n’ont pas de stratégie de mot de passe et n’activent pas l’authentification multifacteur.

- **Applications Cloud d’entreprise avec un chiffrement faible** : filtre toutes vos applications découvertes pour afficher uniquement les applications risquées, car elles ne chiffrent pas les données au repos et ne prennent pas en charge les protocoles de chiffrement.

- **Applications Cloud RGPD Ready** : filtre toutes vos applications découvertes pour afficher uniquement les applications qui sont RGPD prêtes. Étant donné que la conformité RGPD est la priorité la plus haute, cette requête vous aide à identifier facilement les applications qui sont RGPD prêtes et à atténuer les menaces en évaluant le risque de ceux qui ne le sont pas.

![interroger les applications découvertes](media/queries-discovered-apps.png)

En outre, vous pouvez utiliser les requêtes suggérées comme point de départ pour une nouvelle requête. Tout d’abord, sélectionnez l’une des requêtes suggérées. Ensuite, apportez les modifications nécessaires et cliquez enfin sur **Enregistrer sous** pour créer une **requête enregistrée**.

## <a name="next-steps"></a>Étapes suivantes :

> [!div class="nextstepaction"]
> [Créer des rapports d’instantanés Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

> [!div class="nextstepaction"]
> [Configurer le chargement automatique des journaux pour des rapports continus](configure-automatic-log-upload-for-continuous-reports.md)

> [!div class="nextstepaction"]
> [Utilisation des données Cloud Discovery](working-with-cloud-discovery-data.md)
