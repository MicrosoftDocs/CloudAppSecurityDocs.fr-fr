---
title: Utilisation des filtres et des requêtes d’activités de Cloud App Security | Microsoft Docs
description: Cet article fournit une liste de filtres et de requêtes d’activité de Cloud App Security, et explique comment les utiliser.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/13/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 9ba5c7d3-c733-4048-9b99-bf41a0f46695
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 25d173e873e8e8cd49b47559a58240a93cc030b1
ms.sourcegitcommit: 77850c6777504c2478611cb71a387e7fcc5f2551
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51597253"
---
# <a name="activity-filters-and-queries"></a>Filtres et requêtes d’activités

*S’applique à : Microsoft Cloud App Security*

Cet article fournit des descriptions et des instructions pour les filtres et les requêtes d’activité de Cloud App Security.

## <a name="activity-filters"></a>Filtres d’activité

Vous trouverez ci-dessous une liste des filtres d’activité qui peuvent être appliqués. La plupart des filtres prennent en charge plusieurs valeurs, ainsi que NOT, afin de vous fournir un outil puissant pour créer des stratégies.  
  
- ID activité : Recherchez uniquement des activités spécifiques par leur ID. Ce filtre est utile quand vous connectez Microsoft Cloud App Security à votre SIEM (à l’aide de l’agent SIEM) et que vous voulez examiner davantage les alertes dans le portail Cloud App Security.  
  
- Objets d’activité : Recherchez les objets sur lesquels l’activité a été effectuée. Ce filtre s’applique aux objets fichier, dossier, utilisateur ou application. 
  - ID de l’objet d’activité : ID de l’objet (ID de fichier, de dossier, d’utilisateur ou d’application).
  <!-- - File, folder or site URL - Enables you to select files, folders and URLs that start with a specific string.-->
  <!-- - Target object (file/folder) - Enables you to select a specific file or folder. -->
  - Élément : vous permet de rechercher par nom ou par ID d’objet d’activité (par exemple des noms d’utilisateur, des fichiers, des paramètres, des sites). Pour le filtre **Élément d’objet d’activité**, vous pouvez choisir de filtrer les éléments qui **contiennent**, **sont égaux** ou **commencent par** l’élément spécifique.
    
- Type d’activité : Recherchez l’activité de l’application.

- Activité administrative : Recherchez uniquement les activités administratives.  
  
- ID d’alerte - Recherchez par ID d’alerte.

- Application : Recherchez uniquement des activités au sein d’applications spécifiques.  
  
- Action appliquée : Recherchez par action de gouvernance appliquée (Bloqué, Proxy de contournement, Déchiffré, Chiffré, Échec du chiffrement, Aucune action).

- Date : Date à laquelle l’activité s’est produite. Le filtre prend en charge des dates antérieures/ultérieures et une plage de dates.  
  
<!--- Description – Specific keyword in the activity description, for example, all activities that include the string **user** in their description.  -->
  
- Balise de l’appareil : Recherchez par appareil conforme, géré ou vérifié.

- Type d’appareil : Recherchez uniquement les activités qui ont été effectuées à l’aide d’un type d’appareil spécifique. Par exemple, recherchez toutes les activités d’appareils mobiles, de PC ou de tablettes.  

- Fichiers et dossiers : recherchez les fichiers et les dossiers sur lesquels l’activité a été effectuée.
    - ID de fichier : vous permet d’effectuer des recherches par l’ID de fichier sur lequel l’activité a été effectuée. 
    - Nom : filtre sur le nom des fichiers ou des dossiers. Vous pouvez spécifier si le nom **se termine par**, **est égal à** ou **commence par** votre valeur de recherche.
    - Fichiers ou dossiers spécifiques : vous permet d’inclure ou d’exclure des fichiers ou des dossiers spécifiques. Lors de la sélection de fichiers ou de dossiers, vous pouvez filtrer la liste par **Application**, par **Propriétaire** ou par **Nom de fichier** partiel. 
  
- Adresse IP : adresse IP brute, catégorie IP ou balise IP à partir de laquelle l’activité a été réalisée.  
  - Adresse IP brute : vous permet de rechercher des activités qui ont été réalisées sur ou par des adresses IP brutes. Les adresses IP brutes peuvent être égales à, ne pas être égales à, commencer par ou ne pas commencer par une séquence spécifique. 
  - Catégorie IP : Catégorie de l’adresse IP à partir de laquelle l’activité a été réalisée, par exemple, toutes les activités de la plage d’adresses IP administratives. Les catégories doivent être configurées de façon à inclure les adresses IP appropriées, à l’exception de la catégorie « Risqué », qui est préconfigurée et qui inclut deux balises IP : Proxy anonyme et Tor. Pour découvrir comment configurer les catégories IP, consultez [Organiser les données selon vos besoins](ip-tags.md).  
  - Balise IP : Balise de l’adresse IP à partir de laquelle l’activité a été exécutée, par exemple toutes les activités des adresses IP de proxy anonyme. Cloud App Security crée un ensemble de balises IP prédéfinies qui ne sont pas configurables. Vous pouvez également configurer vos propres balises IP. Pour plus d’informations sur la configuration de vos propres balises IP, consultez [Organiser les données selon vos besoins](ip-tags.md).
  Les balises IP prédéfinies sont les suivantes :
  - Applications Microsoft (14 applications)
  - Proxy anonyme
  - Botnet (vous verrez que l’activité a été effectuée par un botnet avec un lien qui vous permet d’en savoir plus sur le botnet spécifique)
  - Adresse IP d’analyse du darknet
  - Serveur de commande et contrôle de programmes malveillants
  - Analyseur de connectivité à distance
  - Fournisseurs par satellite
  - Proxy intelligent et proxy d’accès (délibérément omis)
  - Nœuds de sortie Tor
  - Zscaler


- Activité représentée : Recherchez uniquement les activités qui ont été effectuées au nom d’un autre utilisateur.  

- Instance : instance d’application où l’activité a été ou n’a pas été effectuée.

- Emplacement : Pays à partir duquel l’activité a été effectuée.  

- Stratégie correspondante : Recherchez les activités qui correspondent à une stratégie spécifique qui a été définie dans le portail.  

- ISP enregistré : Fournisseur de services Internet à partir duquel l’activité a été effectuée.

- Source : Effectuez la recherche en fonction de la source à partir de laquelle l’activité a été détectée. La source peut être l’un des éléments suivants :
  - Connecteur d’application : journaux provenant directement du connecteur d’API de l’application.
  - Analyse du connecteur d’application : enrichissements de Cloud App Security basés sur l’analyse des informations par le connecteur d’API.
  

- Utilisateur : utilisateur qui a exécuté l’activité, qui peut être filtré en domaine, groupe, nom ou organisation. Pour filtrer les activités sans utilisateur spécifique, vous pouvez utiliser l’opérateur « n’est pas défini ».  
  - Domaine de l’utilisateur : Recherchez un domaine utilisateur spécifique.
  - Organisation utilisateur : Unité d’organisation de l’utilisateur qui a effectué l’activité, par exemple toutes les activités effectuées par les utilisateurs EMEA_marketing.  
  - Groupe d’utilisateurs : Groupes d’utilisateurs spécifiques que vous pouvez importer à partir d’applications connectées, par exemple, les administrateurs Office 365.  
  - Nom d’utilisateur : Recherchez un nom d’utilisateur spécifique. Pour afficher la liste des utilisateurs membres d’un groupe d’utilisateurs spécifique, dans le **tiroir Activité**, cliquez sur le nom du groupe d’utilisateurs. Le fait de cliquer vous permet d’accéder à la page Comptes qui répertorie tous les utilisateurs figurant dans le groupe. À partir de cette page, vous pouvez explorer plus en détail les comptes d’utilisateurs spécifiques dans le groupe.
    -  Vous pouvez affiner les filtres **Groupe d’utilisateurs** et **Nom d’utilisateur** en choisissant le filtre **En tant que**, puis en sélectionnant le rôle de l’utilisateur parmi les rôles suivants :
        - Objet d’activité uniquement : signifie que l’utilisateur ou le groupe d’utilisateurs sélectionné n’a pas effectué l’activité en question, mais qu’il était l’objet de l’activité.
        - Acteur uniquement : signifie que l’utilisateur ou le groupe d’utilisateurs a effectué l’activité.
        - N’importe quel rôle : signifie que l’utilisateur ou le groupe d’utilisateurs a participé à l’activité, soit en effectuant l’activité, soit en étant l’objet de l’activité.

- Agent utilisateur : Agent utilisateur à partir duquel l’activité a été effectuée.  
  
- Étiquette agent utilisateur : Balise d’agent utilisateur intégrée, par exemple toutes les activités d’un navigateur obsolète ou d’anciens systèmes d’exploitation.  

<!--
>[!NOTE]
> If at any point you want to clear the filters, you can do so by clicking the clear filters icon ![clear filters icon](./media/clear-filters.png). -->


## <a name="activity-queries"></a>Requêtes d’activités

Pour faciliter encore plus les recherches, vous pouvez désormais créer des requêtes personnalisées et les enregistrer pour les utiliser ultérieurement. 

1. Dans la page **Journal d’activité**, utilisez les filtres comme décrit ci-dessus pour explorer vos applications selon vos besoins. 

2. Une fois que vous avez terminé de générer votre requête, cliquez sur le bouton **Enregistrer sous** en haut à droite des filtres. 

3. Dans la fenêtre contextuelle **Enregistrer la requête**, nommez votre requête.

   ![nouvelle requête](./media/new-activity-query.png)

4. Pour réutiliser cette requête plus tard, sous **Requêtes**, faites défiler jusqu’à **Requêtes enregistrées** et sélectionnez votre requête. 

   ![ouvrir une requête](./media/select-activity-query.png)


Cloud App Security vous fournit également des **requêtes suggérées**. Les requêtes suggérées vous fournissent des zones de recherche recommandées qui filtrent vos activités. Vous pouvez modifier ces requêtes et les enregistrer en tant que requêtes personnalisées. Les requêtes suggérées suivantes sont facultatives :

 - Activités d’administration : filtre toutes vos activités pour afficher uniquement les activités ayant impliqué des administrateurs.

 - Activités de téléchargement : filtre toutes vos activités pour afficher uniquement les activités de téléchargement, notamment le téléchargement de la liste des utilisateurs sous forme de fichier .csv, le téléchargement de contenu partagé et le téléchargement d’un dossier.

 - Connexion ayant échoué : filtre toutes vos activités pour afficher uniquement les ouvertures de session et les connexions en échec via l’authentification unique 

 - Activités liées au fichier et au dossier : filtre toutes vos activités pour afficher uniquement les activités liées à des fichiers et des dossiers. Le filtre inclut le chargement, le téléchargement et l’accès aux dossiers, ainsi que la création, la suppression, le chargement, le téléchargement, la mise en quarantaine, l’accès aux fichiers et le transfert de contenu. 

 - Activités d’emprunt d’identité : filtre toutes vos activités pour afficher uniquement les activités d’emprunt d’identité.

 - Activités de boîte aux lettres : filtre toutes vos activités pour afficher uniquement les activités en ligne de Microsoft Exchange Online, comme créer un élément, vider les messages d’une boîte aux lettres, mettre à jour un message et envoyer un message en utilisant des autorisations Envoyer en tant que (emprunt d’identité).

 - Modifications du mot de passe et requêtes réinitialisées : filtre toutes vos activités pour afficher uniquement celles impliquant la réinitialisation de mot de passe, le changement de mot de passe et l’obligation faite à l’utilisateur de changer le mot de passe à la prochaine connexion.

 - Risques de sécurité : filtre toutes vos activités pour afficher uniquement les activités correspondant aux stratégies DLP.

 - Activités de partage : filtre toutes vos activités pour afficher uniquement les activités qui impliquent le partage de dossiers et de fichiers, notamment la création d’un lien d’entreprise, la création d’un lien anonyme et l’octroi d’autorisations de lecture/écriture.

 - Connexion réussie : filtre toutes vos activités pour afficher uniquement les activités impliquant des connexions réussies, notamment une action avec emprunt d’identité, une ouverture de session avec emprunt d’identité, une ouverture de session avec authentification unique et l’ouverture de session à partir d’un nouvel appareil.

![activités de requête](./media/queries-activity.png)
 
De plus, vous pouvez utiliser les requêtes suggérées comme point de départ d’une nouvelle requête. Sélectionnez d’abord une des requêtes suggérées. Ensuite, apportez les modifications nécessaires et cliquez sur **Enregistrer sous** pour créer une **requête enregistrée**.


## <a name="next-steps"></a>Étapes suivantes 
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  