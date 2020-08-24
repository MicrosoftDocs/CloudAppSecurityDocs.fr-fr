---
title: Filtres et requêtes d’applications découvertes de Cloud App Security
description: Cet article fournit une liste de filtres et de requêtes d’applications découvertes de Cloud App Security, et explique comment les utiliser.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 07/07/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: f31b8937d1eeb9781b677da154880ab699ef131e
ms.sourcegitcommit: 29a8e66c665f51d831516924ae4d9d8047b39276
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88780305"
---
# <a name="discovered-app-filters-and-queries"></a>Filtres et requêtes des applications découvertes

*S’applique à : Microsoft Cloud App Security*

Quand vous avez un grand nombre d’applications découvertes, il est pratique de les filtrer et de leur appliquer des requêtes. Cet article décrit les filtres disponibles et comment faire des requêtes sur vos applications découvertes.

## <a name="discovered-app-filters"></a>Filtres d’application découverte

Il existe des filtres d’application découverte de base et avancés. Pour obtenir un filtre complexe (comme dans l’exemple ci-dessus), utilisez l’option avancée qui inclut tous les filtres suivants :

![Applications découvertes](media/discovered-apps.png)

- **Balise d’application** : Indiquez si l’application a été approuvée, non approuvée ou non marquée. Par ailleurs, vous pouvez créer une balise personnalisée pour votre application, puis l’utiliser pour filtrer des types spécifiques d’applications.
- **Applications et domaines** : Permet de rechercher des applications spécifiques ou des applications utilisées dans des domaines spécifiques.
- **Catégories** : Le filtre de catégories, qui se trouve à gauche de la page, vous permet de rechercher des types d’applications selon des catégories d’applications. Voici des exemples de catégories : applications de réseaux sociaux, applications de stockage cloud et services d’hébergement. Vous pouvez sélectionner plusieurs catégories à la fois ou une seule catégorie, puis leur appliquer des filtres de base et des filtres avancés.
- **Facteur de risque de conformité** : permet de rechercher un standard, une certification et une conformité spécifiques auxquels l’application doit être conforme (HIPAA, ISO 27001, SOC 2, PCI-DSS, etc.).
- **Facteur de risque général** : permet de rechercher des facteurs de risque généraux, comme la popularité auprès des consommateurs, les paramètres régionaux du centre de données, etc.
- **Score de risque** : permet de filtrer les applications par score de risque, et donc par exemple de se concentrer uniquement sur les applications très risquées. Vous pouvez également remplacer le score de risque défini par Cloud App Security. Pour plus d’informations, consultez [utilisation du score de risque](risk-score.md).
- **Facteur de risque de sécurité** : Permet de filtrer en fonction de mesures de sécurité spécifiques (comme le chiffrement au repos, l’authentification multifacteur, etc.).
- **Utilisation** : permet de filtrer selon les statistiques d’utilisation de cette application. Il peut s’agir d’applications avec un nombre de **chargements de données** ou **d’utilisateurs** supérieur ou inférieur à une quantité spécifiée.
- **Facteur de risque légal** : permet de filtrer selon l’ensemble des réglementations et des stratégies qui sont en place pour garantir la protection et la confidentialité des données des utilisateurs de l’application. Il peut s’agir par exemple des applications cloud prêtes pour le RGPD, de DMCA et de la stratégie de conservation des données.

### <a name="creating-and-managing-custom-app-tags"></a>Création et gestion des balises d’application personnalisées

Vous pouvez créer une balise d’application personnalisée. Ces balises peuvent ensuite servir de filtres pour rechercher plus précisément des types spécifiques d’applications que vous voulez examiner. Par exemple, une liste de suivi personnalisée, une attribution à une division spécifique ou des approbations personnalisées, telles que « approuvé par légal ». Les balises d’application peuvent également être utilisées dans des stratégies de détection d’application dans des filtres ou en appliquant des balises aux applications dans le cadre des actions de gouvernance des stratégies.

Pour créer une balise d’application personnalisée :

1. Dans la roue dentée **paramètres** , sélectionnez **paramètres Cloud Discovery**, puis l’onglet **balises d’application** . cliquez sur l’icône plus. ![Icône « Plus »](media/plus-icon.png)

   ![créer une balise d’application personnalisée](media/create-app-tag.png)

2. Vous pouvez utiliser le tableau **Balises d’application** pour voir les applications qui sont actuellement marquées avec chaque balise d’application, et vous pouvez supprimer les balises d’application inutilisées.

3. Pour appliquer une balise d’application, sous l’onglet **Applications découvertes**, cliquez sur les points de suspension tout à droite du nom de l’application. Sélectionnez la balise d’application à appliquer.

> [!NOTE]
>Vous pouvez également créer une balise d’application directement dans le tableau **Applications découvertes** en cliquant sur **Créer une balise d’application** après avoir sélectionné les points de suspension à droite de n’importe quelle application sélectionnée. Quand vous créez la balise à partir de l’application découverte, vous pouvez l’appliquer à l’application. Vous pouvez également accéder à l’écran **Balises d’application** en cliquant sur le lien **Gérer les balises**.
> ![Créer une balise d’application personnalisée à partir de l’application](media/create-app-tag-from-app.png)

## <a name="discovered-app-queries"></a>Requêtes d’applications découvertes

Pour faciliter encore plus l’investigation, vous pouvez créer des requêtes personnalisées et les enregistrer pour une utilisation ultérieure.

1. Dans la page **Applications découvertes**, utilisez les filtres comme décrit ci-dessus pour explorer vos applications selon vos besoins.

2. Une fois que vous avez obtenu les résultats souhaités, cliquez sur le bouton **Enregistrer sous** en haut à droite des filtres.

3. Dans la fenêtre contextuelle **enregistrer la requête** , nommez votre requête.

    ![nouvelle requête](media/new-query.png)

4. Pour réutiliser cette requête plus tard, sous **Requêtes**, faites défiler jusqu’à **Requêtes enregistrées** et sélectionnez votre requête.

    ![ouvrir une requête](media/discovered-app-query.png)

Cloud App Security vous fournit également des **requêtes suggérées** et vous permet d’enregistrer des requêtes personnalisées que vous utilisez fréquemment. Les requêtes suggérées vous fournissent des zones de recherche recommandées qui filtrent vos applications découvertes en utilisant les requêtes suggérées facultatives suivantes :

- **Applications Cloud qui autorisent une utilisation anonyme** : filtre toutes vos applications découvertes pour afficher uniquement les applications qui présentent des risques de sécurité, car elles ne nécessitent pas d’authentification utilisateur et permettent aux utilisateurs de télécharger des données.

- **Applications Cloud certifiées CSA en étoile** -filtre toutes vos applications découvertes pour afficher uniquement les applications qui ont une certification CSA Star par le biais de l’auto-évaluation, de la certification, de l’attestation ou de la surveillance continue.

- **Applications Cloud compatibles FedRAMP** : filtre toutes vos applications découvertes pour afficher uniquement les applications dont le facteur de risque de conformité FedRAMP est élevé, moyen ou faible.

- **Applications de stockage et de collaboration cloud qui possèdent les données utilisateur** - Filtre toutes vos applications découvertes pour afficher uniquement les applications qui présentent un risque, car elles ne vous permettent pas d’être propriétaire de vos données alors qu’elles les conservent.

- **Applications de stockage cloud risquées et non conformes** : filtre toutes vos applications découvertes pour afficher uniquement les applications pour lesquelles elles ne sont pas compatibles avec SOC 2 ou HIPAA. elles ne prennent pas en charge la version PCI DSS et elles ont un score de risque inférieur ou supérieur à 5.

- **Applications Cloud d’entreprise avec une authentification faible** : filtre toutes vos applications découvertes pour afficher uniquement les applications qui ne prennent pas en charge SAML, n’ont pas de stratégie de mot de passe et n’activent pas l’authentification multifacteur.

- **Applications Cloud d’entreprise avec un chiffrement faible** : filtre toutes vos applications découvertes pour afficher uniquement les applications risquées, car elles ne chiffrent pas les données au repos et ne prennent pas en charge les protocoles de chiffrement.

- **Applications cloud prêtes pour le RGPD** - Filtre toutes vos applications découvertes pour afficher uniquement les applications qui sont prêtes pour le RGPD. Étant donné que la conformité RGPD est la priorité la plus haute, cette requête vous aide à identifier facilement les applications qui sont RGPD prêtes et à atténuer les menaces en évaluant le risque de ceux qui ne le sont pas.

![interroger les applications découvertes](media/queries-discovered-apps.png)

De plus, vous pouvez utiliser les requêtes suggérées comme point de départ d’une nouvelle requête. Sélectionnez d’abord une des requêtes suggérées. Ensuite, apportez les modifications nécessaires et cliquez sur **Enregistrer sous** pour créer une **requête enregistrée**.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Créer des rapports d’instantanés Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

> [!div class="nextstepaction"]
> [Configurer le chargement automatique des journaux pour des rapports continus](configure-automatic-log-upload-for-continuous-reports.md)

> [!div class="nextstepaction"]
> [Utilisation des données Cloud Discovery](working-with-cloud-discovery-data.md)
