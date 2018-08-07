---
title: Utilisation des filtres et des requêtes d’applications découvertes de Cloud App Security | Microsoft Docs
description: Cette rubrique fournit une liste de filtres et de requêtes d’applications découvertes de Cloud App Security, et explique comment les utiliser.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/6/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 1a2d3aeb-4e28-4c73-804b-95e862b08e43
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 2032d5fbfc78e734abd747dc6f6f84fca1f95f95
ms.sourcegitcommit: a97e6d93124433547149fd8a642fcb77e02a75f2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39519004"
---
*S’applique à : Microsoft Cloud App Security*

# <a name="discovered-app-filters-and-queries"></a>Filtres et requêtes d’applications découvertes

## <a name="discovered-app-filters"></a>Filtres d’application découverte

Il existe des filtres d’application découverte de base et avancés. Pour obtenir un filtre complexe (comme dans l’exemple ci-dessus), utilisez l’option avancée qui inclut tous les filtres suivants :

![Applications découvertes](./media/discovered-apps.png)  


- **Balise d’application** : Indiquez si l’application a été approuvée, non approuvée ou non marquée. Par ailleurs, vous pouvez créer une balise personnalisée pour votre application et l’utiliser pour filtrer des types spécifiques d’applications. 
- **Applications et domaines** : Permet de rechercher des applications spécifiques ou des applications utilisées dans des domaines spécifiques. 
- **Catégories** : Le filtre de catégories, qui se trouve à gauche de la page, vous permet de rechercher des types d’applications selon des catégories d’applications, par exemple, des applications de réseau social, des applications de stockage cloud, etc. Vous pouvez sélectionner plusieurs catégories à la fois, ou une seule catégorie, puis leur appliquer des filtres de base et avancés.
- **Facteur de risque de conformité** : Permet de rechercher une norme, une certification et une conformité spécifique auxquelles l’application doit se conformer (HIPAA, ISO 27001, SOC 2, PCI-DSS, etc.).
- **Facteur de risque général** : Permet de rechercher des facteurs de risque général comme la popularité auprès des consommateurs, les paramètres régionaux du centre de données, etc.
- **Score de risque** : Permet de filtrer les applications par score de risque pour que vous puissiez vous concentrer uniquement sur les applications très risquées, par exemple. Vous pouvez également remplacer le score de risque défini par Cloud App Security. Pour plus d’informations, consultez [Utilisation du score de risque](risk-score.md).
- **Facteur de risque de sécurité** : Permet de filtrer en fonction de mesures de sécurité spécifiques (comme le chiffrement au repos, l’authentification multifacteur, etc.).
- **Utilisation** : Permet de filtrer en fonction des statistiques d’utilisation de cette application, comme les applications avec un nombre supérieur ou inférieur de **chargements de données** que la quantité spécifiée, les applications avec un nombre supérieur ou inférieur **d’utilisateurs** que le nombre spécifié.
- **Légal** : vous permet de filtrer selon l’ensemble des réglementations et des stratégies qui sont en place pour garantir la protection et la confidentialité des données des utilisateurs de l’application, comme la stratégie de conservation des données, le RGPD et le DMCA.

### <a name="creating-and-managing-custom-app-tags"></a>Création et gestion des balises d’application personnalisées

Vous pouvez créer une balise d’application personnalisée. Ces balises peuvent ensuite servir de filtres pour rechercher plus précisément des types spécifiques d’applications que vous voulez examiner. Par exemple, une liste de suivi personnalisée, l’attribution à une division spécifique ou des approbations personnalisées, comme « approuvé par le service juridique ».

Pour créer une balise d’application personnalisée :

1. Dans le menu **Paramètres** (roue dentée), sélectionnez **Cloud Discovery** et sous l’onglet **Gérer les balises d’application**, cliquez sur l’icône ![plus](./media/plus-icon.png). 

![créer une balise d’application personnalisée](./media/create-app-tag.png)

2. Vous pouvez utiliser le tableau **Gérer les balises d’application** pour consulter les applications qui sont actuellement marquées avec chaque balise d’application et vous pouvez supprimer les balises d’application inutilisées.

3. Pour appliquer une balise d’application, sous l’onglet **Applications découvertes**, cliquez sur les points de suspension complètement à droite du tableau et sélectionnez la balise d’application à appliquer. 

> [!NOTE]
>Vous pouvez également créer une balise d’application directement dans le tableau **Applications découvertes** en cliquant sur **Créer une balise d’application** après avoir sélectionné les points de suspension à droite de n’importe quelle application sélectionnée. Vous pouvez également accéder à l’écran **Gérer les balises d’application** en cliquant sur le lien dans le coin de la fenêtre contextuelle **Créer une balise d’application**.

## <a name="discovered-app-queries"></a>Requêtes d’applications découvertes

Pour faciliter encore plus les recherches, vous pouvez désormais créer des requêtes personnalisées et les enregistrer pour les utiliser ultérieurement. 

1. Dans la page **Applications découvertes**, utilisez les filtres comme décrit ci-dessus pour explorer vos applications selon vos besoins. 

2. Une fois que vous avez atteint les résultats souhaités, cliquez sur le bouton **Enregistrer sous** en haut à droite des filtres. 

3. Dans la fenêtre contextuelle **Enregistrer la requête**, nommez votre requête.

   ![nouvelle requête](./media/new-query.png)

4. Pour réutiliser cette requête plus tard, sous **Requêtes**, faites défiler jusqu’à **Requêtes enregistrées** et sélectionnez votre requête. 

   ![ouvrir une requête](./media/discovered-app-query.png)


Cloud App Security vous fournit également des **requêtes suggérées** et vous permet d’enregistrer des requêtes personnalisées que vous utilisez fréquemment. Les requêtes suggérées vous fournissent des zones de recherche recommandées qui filtrent vos applications découvertes en utilisant les requêtes suggérées facultatives suivantes :

 - Applications cloud autorisant l’utilisation anonyme : filtre toutes vos applications découvertes pour afficher uniquement les applications représentant des risques de sécurité, car elles ne nécessitent pas l’authentification des utilisateurs et permettent aux utilisateurs de charger des données.

 - Applications cloud certifiées CSA STAR : filtre toutes vos applications découvertes pour afficher uniquement les applications qui ont une certification CSA STAR par auto-évaluation, par certification, par attestation ou par surveillance continue.

 - Applications cloud conformes à FedRAMP : filtre toutes vos applications découvertes pour afficher uniquement celles dont le facteur de risque de conformité FedRAMP est élevé, moyen ou faible. 

 - Applications de stockage et de collaboration cloud qui ont des filtres de données : filtre toutes vos applications découvertes pour afficher uniquement les applications qui présentent un risque, car elles ne vous permettent pas d’être propriétaire de vos données alors qu’elles les conservent.

 - Applications de stockage cloud risquées et non conformes : filtre toutes vos applications découvertes pour afficher uniquement les applications qui ne sont pas conformes à SOC 2 ou à HIPAA, qui ne prennent pas en charge la version de PCI DSS, et qui ont un score de risque inférieur ou égal à 5.

 - Applications cloud d’entreprise qui ont une authentification faible : filtre toutes vos applications découvertes pour afficher uniquement les applications qui ne prennent pas en charge SAML, qui n’ont pas de stratégie de mot de passe et qui ne permettent pas l’authentification multifacteur.

 - Applications cloud d’entreprise qui ont un chiffrement faible : filtre toutes vos applications découvertes pour afficher uniquement les applications qui sont risquées, car elles ne chiffrent pas les données au repos et ne prennent en charge aucun protocole de chiffrement.

- Prêt pour le RGPD : filtre toutes vos applications découvertes pour afficher uniquement les applications qui sont prêtes pour le RGPD. Étant donné que la conformité au RGPD est une priorité absolue, cette requête vous aide à identifier les applications qui sont prêtes pour le RGPD et à atténuer les menaces en évaluant le risque de celles qui ne le sont pas.
 
![interroger les applications découvertes](./media/queries-discovered-apps.png)

 
De plus, vous pouvez utiliser les requêtes suggérées comme point de départ d’une nouvelle requête. Sélectionnez d’abord une des requêtes suggérées. Ensuite, apportez les modifications nécessaires et cliquez sur **Enregistrer sous** pour créer une **requête enregistrée**.


## <a name="see-also"></a>Voir aussi
 
[Créer des rapports d’instantanés Cloud Discovery](create-snapshot-cloud-discovery-reports.md)

[Configurer le chargement automatique des journaux pour des rapports continus](configure-automatic-log-upload-for-continuous-reports.md)

[Utilisation des données Cloud Discovery](working-with-cloud-discovery-data.md)

