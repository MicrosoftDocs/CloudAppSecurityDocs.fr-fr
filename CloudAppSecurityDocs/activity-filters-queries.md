---
title: Utilisation des filtres et des requêtes d’activité Cloud App Security
description: Cet article fournit une liste de Cloud App Security les filtres d’activité et les requêtes et explique comment les utiliser.
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
ms.openlocfilehash: f37fab4f9d611577deecb4884838431144f1647d
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285273"
---
# <a name="activity-filters-and-queries"></a>Filtres et requêtes des activités

*S’applique à : Microsoft Cloud App Security*

Cet article fournit des descriptions et des instructions pour Cloud App Security les filtres et les requêtes d’activité.

## <a name="activity-filters"></a>Filtres d’activité

Vous trouverez ci-dessous une liste des filtres d’activité qui peuvent être appliqués. La plupart des filtres prennent en charge plusieurs valeurs et ne vous fournissent pas un outil puissant pour la création de stratégies.

- ID activité : Recherchez uniquement des activités spécifiques par leur ID. Ce filtre est utile lorsque vous vous connectez Microsoft Cloud App Security à votre SIEM (à l’aide de l’agent SIEM) et que vous souhaitez approfondir vos recherches sur les alertes dans le portail Cloud App Security.

- Objets d’activité : recherchez les objets sur lesquels l’activité a été effectuée. Ce filtre s’applique aux objets fichier, dossier, utilisateur ou application.
  - ID de l’objet d’activité : ID de l’objet (fichier, dossier, utilisateur ou ID d’application).
  <!-- - File, folder or site URL - Enables you to select files, folders and URLs that start with a specific string.-->
  <!-- - Target object (file/folder) - Enables you to select a specific file or folder. -->
  - Élément : vous permet de rechercher par nom ou par ID d’objet d’activité (par exemple des noms d’utilisateur, des fichiers, des paramètres, des sites). Pour le filtre **élément d’objet d’activité** , vous pouvez choisir de filtrer les éléments qui **contiennent**, sont **égaux**ou qui **commencent par** l’élément spécifique.

- Type d’activité : Recherchez l’activité de l’application.

- Activité administrative : Recherchez uniquement les activités administratives.

- ID d’alerte - Recherchez par ID d’alerte.

- Application : Recherchez uniquement des activités au sein d’applications spécifiques.

- Action appliquée : Recherchez par action de gouvernance appliquée (Bloqué, Proxy de contournement, Déchiffré, Chiffré, Échec du chiffrement, Aucune action).

- Date : Date à laquelle l’activité s’est produite. Le filtre prend en charge les dates avant/après et une plage de dates.

<!--- Description – Specific keyword in the activity description, for example, all activities that include the string **user** in their description.  -->

- Balise de l’appareil : Recherchez par appareil conforme, géré ou vérifié.

- Type d’appareil : recherchez uniquement les activités qui ont été effectuées à l’aide d’un type d’appareil spécifique. Par exemple, recherchez toutes les activités à partir d’appareils mobiles, de PC ou de tablettes.

- Fichiers et dossiers : recherchez les fichiers et les dossiers sur lesquels l’activité a été effectuée.
  - ID de fichier : vous permet d’effectuer une recherche en fonction de l’ID de fichier sur lequel l’activité a été effectuée.
  - Nom : filtre le nom des fichiers ou des dossiers. Vous pouvez choisir si le nom **se termine par**, **est égal**à ou **commence par** votre valeur de recherche.
  - Fichiers ou dossiers spécifiques : vous permet d’inclure ou d’exclure des fichiers ou des dossiers spécifiques. Lorsque vous sélectionnez des fichiers ou des dossiers, vous pouvez filtrer la liste par **application**, **propriétaire**ou **nom de fichier**partiel.

- Adresse IP : adresse IP brute, catégorie ou balise à partir de laquelle l’activité a été effectuée.
  - Adresse IP brute : vous permet de rechercher les activités qui ont été effectuées sur ou par des adresses IP brutes. Les adresses IP brutes peuvent être égales, ne pas être égales, commencer par ou ne pas commencer par une séquence particulière.
  - Catégorie IP : Catégorie de l’adresse IP à partir de laquelle l’activité a été réalisée, par exemple, toutes les activités de la plage d’adresses IP administratives. Les catégories doivent être configurées de manière à inclure les adresses IP appropriées, à l’exception de la catégorie « risquée », qui est préconfigurée et inclut deux balises IP : proxy anonyme et TDR. Pour découvrir comment configurer les catégories IP, consultez [Organiser les données selon vos besoins](ip-tags.md).
  - Balise IP : Balise de l’adresse IP à partir de laquelle l’activité a été exécutée, par exemple toutes les activités des adresses IP de proxy anonyme. Cloud App Security crée un ensemble de balises IP intégrées qui ne sont pas configurables. En outre, vous pouvez configurer vos propres balises IP. Pour plus d’informations sur la configuration de vos propres balises IP, consultez [Organiser les données selon vos besoins](ip-tags.md).
  Les balises IP prédéfinies sont les suivantes :
    - Applications Microsoft (14 applications)
    - Proxy anonyme
    - Botnet (vous verrez que l’activité a été effectuée par un botnet avec un lien pour en savoir plus sur le botnet spécifique)
    - Adresse IP d’analyse du darknet
    - Serveur de commande et contrôle de programmes malveillants
    - Analyseur de connectivité à distance
    - Fournisseurs par satellite
    - Proxy intelligent et proxy d’accès (délibérément omis)
    - Nœuds de sortie Tor
    - Zscaler

- Activité représentée : Recherchez uniquement les activités qui ont été effectuées au nom d’un autre utilisateur.

- Instance : instance de l’application dans laquelle l’activité a été exécutée ou non.

- Emplacement : Pays à partir duquel l’activité a été effectuée.

- Stratégie correspondante : Recherchez les activités qui correspondent à une stratégie spécifique qui a été définie dans le portail.

- ISP enregistré : Fournisseur de services Internet à partir duquel l’activité a été effectuée.

- Source : Effectuez la recherche en fonction de la source à partir de laquelle l’activité a été détectée. La source peut être l’un des éléments suivants :
  - Connecteur d’application : journaux provenant directement du connecteur d’API de l’application.
  - Analyse du connecteur d’application : enrichissements de Cloud App Security basés sur l’analyse des informations par le connecteur d’API.

- Utilisateur : utilisateur qui a effectué l’activité, qui peut être filtré en domaine, groupe, nom ou organisation. Pour filtrer les activités sans utilisateur spécifique, vous pouvez utiliser l’opérateur « n’est pas défini ».
  - Domaine de l’utilisateur : Recherchez un domaine utilisateur spécifique.
  - Organisation utilisateur : Unité d’organisation de l’utilisateur qui a effectué l’activité, par exemple toutes les activités effectuées par les utilisateurs EMEA_marketing. Cela s’applique uniquement aux instances G suite connectées qui utilisent des unités d’organisation.
  - Groupe d’utilisateurs : Groupes d’utilisateurs spécifiques que vous pouvez importer à partir d’applications connectées, par exemple, les administrateurs Office 365.
  - Nom d’utilisateur : Recherchez un nom d’utilisateur spécifique. Pour afficher la liste des utilisateurs membres d’un groupe d’utilisateurs spécifique, dans le **tiroir Activité**, cliquez sur le nom du groupe d’utilisateurs. Cliquer sur vous reconnectera à la page comptes qui répertorie tous les utilisateurs du groupe. À partir de là, vous pouvez examiner en détail les comptes d’utilisateurs spécifiques dans le groupe.
  - Vous pouvez affiner les filtres **Groupe d’utilisateurs** et **Nom d’utilisateur** en choisissant le filtre **En tant que**, puis en sélectionnant le rôle de l’utilisateur parmi les rôles suivants :
    - Objet d’activité uniquement : cela signifie que l’utilisateur ou le groupe d’utilisateurs sélectionné n’a pas effectué l’activité en question. il s’agit de l’objet de l’activité.
    - Acteur uniquement : cela signifie que l’utilisateur ou le groupe d’utilisateurs a effectué l’activité.
    - N’importe quel rôle, c’est-à-dire que l’utilisateur ou le groupe d’utilisateurs a participé à l’activité, soit en tant que personne qui a effectué l’activité, soit en tant qu’objet de l’activité.

- Agent utilisateur : Agent utilisateur à partir duquel l’activité a été effectuée.

- Étiquette agent utilisateur : Balise d’agent utilisateur intégrée, par exemple toutes les activités d’un navigateur obsolète ou d’anciens systèmes d’exploitation.

<!--
>[!NOTE]
> If at any point you want to clear the filters, you can do so by clicking the clear filters icon ![clear filters icon](media/clear-filters.png). -->

## <a name="activity-queries"></a>Requêtes d’activité

Pour faciliter encore plus l’investigation, vous pouvez désormais créer des requêtes personnalisées et les enregistrer pour une utilisation ultérieure.

1. Dans la page **Journal d’activité** , utilisez les filtres comme décrit ci-dessus pour analyser en détail vos applications en fonction des besoins.

2. Une fois que vous avez terminé de créer votre requête, cliquez sur le bouton **Enregistrer sous** dans le coin supérieur droit des filtres.

3. Dans la fenêtre contextuelle **enregistrer la requête** , nommez votre requête.

   ![nouvelle requête](media/new-activity-query.png)

4. Pour réutiliser cette requête ultérieurement, sous **requêtes**, faites défiler jusqu’à **requêtes enregistrées** et sélectionnez votre requête.

   ![ouvrir la requête](media/select-activity-query.png)

Cloud App Security fournit également des **requêtes suggérées**. Les requêtes suggérées vous fournissent des voies d’investigation recommandées qui filtrent vos activités. Vous pouvez modifier ces requêtes et les enregistrer en tant que requêtes personnalisées. Les requêtes suggérées facultatives sont les suivantes :

- Activités d’administration : filtre toutes vos activités pour afficher uniquement les activités qui ont impliqué les administrateurs.

- Télécharger des activités : filtre toutes vos activités pour afficher uniquement les activités qui ont été téléchargées, y compris Télécharger la liste des utilisateurs en tant que fichier. csv vile, en téléchargeant le contenu partagé et en téléchargeant un dossier.

- Échec de la connexion : filtre toutes vos activités pour afficher uniquement les échecs de journalisation et les échecs de connexion via SSO

- Activités de fichiers et de dossiers : filtre toutes vos activités pour afficher uniquement les activités qui ont impliqué des fichiers et des dossiers. Le filtre comprend le chargement, le téléchargement et l’accès aux dossiers, ainsi que la création, la suppression, le chargement, le téléchargement, la mise en quarantaine et l’accès aux fichiers, ainsi que le transfert de contenu.

- Activités d’emprunt d’identité : filtre toutes vos activités pour afficher uniquement les activités d’emprunt d’identité.

- Activités de boîte aux lettres : filtre toutes vos activités pour afficher uniquement les activités Microsoft Exchange Online, telles que créer un élément, purger les messages de la boîte aux lettres, mettre à jour le message et envoyer un message à l’aide des autorisations Envoyer en tant que (emprunt d’identité).

- Demandes de modification et de réinitialisation de mot de passe : filtre toutes vos activités pour afficher uniquement les activités qui impliquent la réinitialisation du mot de passe, modifier le mot de passe et forcer l’utilisateur à modifier le mot de passe lors de la prochaine connexion.

- Risques de sécurité : filtre toutes vos activités pour afficher uniquement les activités qui correspondent aux stratégies DLP.

- Partage des activités : filtre toutes vos activités pour afficher uniquement les activités qui impliquent le partage de dossiers et de fichiers, y compris la création d’un lien d’entreprise, la création d’un lien anonyme et l’octroi d’autorisations de lecture/écriture.

- Connexion réussie : filtre toutes vos activités pour afficher uniquement les activités qui impliquent des connexions réussies, y compris l’action d’emprunt d’identité, l’usurpation d’identité, l’authentification unique et l’ouverture de session à partir d’un nouvel appareil.

![activités de requête](media/queries-activity.png)

En outre, vous pouvez utiliser les requêtes suggérées comme point de départ pour une nouvelle requête. Tout d’abord, sélectionnez l’une des requêtes suggérées. Ensuite, apportez les modifications nécessaires et cliquez enfin sur **Enregistrer sous** pour créer une **requête enregistrée**.

## <a name="next-steps"></a>Étapes suivantes :

> [!div class="nextstepaction"]
> [Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)
