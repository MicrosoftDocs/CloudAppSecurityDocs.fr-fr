---
title: Utilisation des filtres et des requêtes d’applications découvertes de Cloud App Security | Microsoft Docs
description: Cet article fournit une liste de filtres et de requêtes d’applications découvertes de Cloud App Security, et explique comment les utiliser.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/9/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 1a2d3aeb-4e28-4c73-804b-95e862b08e43
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: e62fca426ddd1d3a6ec1adde6ccbdb5f2d0bf0f8
ms.sourcegitcommit: c497253a7ab63973bb806607e5f15dece91640be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53123854"
---
# <a name="discovered-app-filters-and-queries"></a>Filtres et requêtes d’applications découvertes

*S’applique à : Microsoft Cloud App Security*

Quand vous avez un grand nombre d’applications découvertes, il est pratique de les filtrer et de leur appliquer des requêtes. Cet article décrit les filtres disponibles et comment faire des requêtes sur vos applications découvertes.  

## <a name="discovered-app-filters"></a>Filtres d’application découverte

Il existe des filtres d’application découverte de base et avancés. Pour obtenir un filtre complexe (comme dans l’exemple ci-dessus), utilisez l’option avancée qui inclut tous les filtres suivants :

![Applications découvertes](./media/discovered-apps.png)  


- **Balise d’application** : Indiquez si l’application a été approuvée, non approuvée ou non marquée. Par ailleurs, vous pouvez créer une balise personnalisée pour votre application, puis l’utiliser pour filtrer des types spécifiques d’applications. 
- **Applications et domaines** : Permet de rechercher des applications spécifiques ou des applications utilisées dans des domaines spécifiques. 
- **Catégories** : Le filtre de catégories, qui se trouve à gauche de la page, vous permet de rechercher des types d’applications selon des catégories d’applications. Voici des exemples de catégories : applications de réseaux sociaux, applications de stockage cloud et services d’hébergement. Vous pouvez sélectionner plusieurs catégories à la fois ou une seule catégorie, puis leur appliquer des filtres de base et des filtres avancés.
- **Facteur de risque de conformité** : permet de rechercher un standard, une certification et une conformité spécifiques auxquels l’application doit être conforme (HIPAA, ISO 27001, SOC 2, PCI-DSS, etc.).
- **Facteur de risque général** : permet de rechercher des facteurs de risque généraux, comme la popularité auprès des consommateurs, les paramètres régionaux du centre de données, etc.
- **Score de risque** : permet de filtrer les applications par score de risque, et donc par exemple de se concentrer uniquement sur les applications très risquées. Vous pouvez également remplacer le score de risque défini par Cloud App Security. Pour plus d’informations, consultez [Utilisation du score de risque](risk-score.md).
- **Facteur de risque de sécurité** : Permet de filtrer en fonction de mesures de sécurité spécifiques (comme le chiffrement au repos, l’authentification multifacteur, etc.).
- **Utilisation** : permet de filtrer selon les statistiques d’utilisation de cette application. Il peut s’agir d’applications avec un nombre de **chargements de données** ou **d’utilisateurs** supérieur ou inférieur à une quantité spécifiée.
- **Facteur de risque légal** : permet de filtrer selon l’ensemble des réglementations et des stratégies qui sont en place pour garantir la protection et la confidentialité des données des utilisateurs de l’application. Il peut s’agir par exemple des applications cloud prêtes pour le RGPD, de DMCA et de la stratégie de conservation des données.

### <a name="creating-and-managing-custom-app-tags"></a>Création et gestion des balises d’application personnalisées

Vous pouvez créer une balise d’application personnalisée. Ces balises peuvent ensuite servir de filtres pour rechercher plus précisément des types spécifiques d’applications que vous voulez examiner. Par exemple, une liste de suivi personnalisée, l’attribution à une division spécifique ou des approbations personnalisées, comme « approuvé par le service juridique ».

Pour créer une balise d’application personnalisée :

1. À partir de l’icône d’engrenage **Paramètres**, sélectionnez **Paramètres Cloud Discovery**, puis l’onglet **Balises d’application**. Cliquez sur l’icône Plus (+). ![Icône « Plus »](./media/plus-icon.png)

   ![créer une balise d’application personnalisée](./media/create-app-tag.png)

2. Vous pouvez utiliser le tableau **Balises d’application** pour voir les applications qui sont actuellement marquées avec chaque balise d’application, et vous pouvez supprimer les balises d’application inutilisées.

3. Pour appliquer une balise d’application, sous l’onglet **Applications découvertes**, cliquez sur les points de suspension tout à droite du nom de l’application. Sélectionnez la balise d’application à appliquer. 

> [!NOTE]
>Vous pouvez également créer une balise d’application directement dans le tableau **Applications découvertes** en cliquant sur **Créer une balise d’application** après avoir sélectionné les points de suspension à droite de n’importe quelle application sélectionnée. Quand vous créez la balise à partir de l’application découverte, vous pouvez l’appliquer à l’application. Vous pouvez également accéder à l’écran **Balises d’application** en cliquant sur le lien **Gérer les balises**.
> ![Créer une balise d’application personnalisée à partir de l’application](./media/create-app-tag-from-app.png)

## <a name="discovered-app-queries"></a>Requêtes d’applications découvertes

Pour faciliter encore plus les recherches, vous pouvez créer des requêtes personnalisées et les enregistrer pour les utiliser ultérieurement. 

1. Dans la page **Applications découvertes**, utilisez les filtres comme décrit ci-dessus pour explorer vos applications selon vos besoins. 

2. Une fois que vous avez obtenu les résultats souhaités, cliquez sur le bouton **Enregistrer sous** en haut à droite des filtres. 

3. Dans la fenêtre contextuelle **Enregistrer la requête**, nommez votre requête.

   ![nouvelle requête](./media/new-query.png)

4. Pour réutiliser cette requête plus tard, sous **Requêtes**, faites défiler jusqu’à **Requêtes enregistrées** et sélectionnez votre requête. 

   ![ouvrir une requête](./media/discovered-app-query.png)


Cloud App Security vous fournit également des **requêtes suggérées** et vous permet d’enregistrer des requêtes personnalisées que vous utilisez fréquemment. Les requêtes suggérées vous fournissent des zones de recherche recommandées qui filtrent vos applications découvertes en utilisant les requêtes suggérées facultatives suivantes :

 - **Applications cloud autorisant l’utilisation anonyme** - Filtre toutes vos applications découvertes pour afficher uniquement les applications représentant des risques de sécurité, car elles ne nécessitent pas l’authentification des utilisateurs et permettent à ces derniers de charger des données.

 - **Applications cloud certifiées CSA STAR** - Filtre toutes vos applications découvertes pour afficher uniquement les applications qui ont une certification CSA STAR par autoévaluation, par certification, par attestation ou par supervision continue.

 - **Applications cloud conformes à FedRAMP** - Filtre toutes vos applications découvertes pour afficher uniquement celles dont le facteur de risque de conformité FedRAMP est élevé, moyen ou faible. 

 - **Applications de stockage et de collaboration cloud qui possèdent les données utilisateur** - Filtre toutes vos applications découvertes pour afficher uniquement les applications qui présentent un risque, car elles ne vous permettent pas d’être propriétaire de vos données alors qu’elles les conservent.

 - **Applications de stockage cloud risquées et non conformes** - Filtre toutes vos applications découvertes pour afficher uniquement les applications qui ne sont pas conformes à SOC 2 ou à HIPAA, qui ne prennent pas en charge la version PCI DSS et qui ont un score de risque inférieur ou égal à 5.

 - **Applications cloud d’entreprise avec une authentification faible** - Filtre toutes vos applications découvertes pour afficher uniquement les applications qui ne prennent pas en charge SAML, qui n’ont pas de stratégie de mot de passe et qui ne permettent pas l’utilisation de MFA.

 - **Applications cloud d’entreprise avec un chiffrement faible** - Filtre toutes vos applications découvertes pour afficher uniquement les applications qui présentent des risques, car elles ne chiffrent pas les données au repos et ne prennent en charge aucun protocole de chiffrement.

- **Applications cloud prêtes pour le RGPD** - Filtre toutes vos applications découvertes pour afficher uniquement les applications qui sont prêtes pour le RGPD. Étant donné que la conformité au RGPD est une priorité absolue, cette requête vous aide à identifier les applications qui sont prêtes pour le RGPD et à atténuer les menaces en évaluant le risque de celles qui ne le sont pas.
 
![interroger les applications découvertes](./media/queries-discovered-apps.png)

 
De plus, vous pouvez utiliser les requêtes suggérées comme point de départ d’une nouvelle requête. Sélectionnez d’abord une des requêtes suggérées. Ensuite, apportez les modifications nécessaires et cliquez sur **Enregistrer sous** pour créer une **requête enregistrée**.


## <a name="next-steps"></a>Étapes suivantes
 
[Créer des rapports d’instantanés Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Configurer le chargement automatique des journaux pour des rapports continus](configure-automatic-log-upload-for-continuous-reports.md)

[Utilisation des données Cloud Discovery](working-with-cloud-discovery-data.md)

