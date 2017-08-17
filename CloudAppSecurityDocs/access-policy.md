---
title: "Créer des stratégies d’accès pour surveiller et bloquer l’accès à vos applications cloud | Microsoft Docs"
description: "Cette rubrique décrit la procédure de configuration d’une stratégie d’accès pour surveiller et bloquer l’accès à vos applications cloud."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/8/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: ddeabd1d-f017-4756-94b2-194292e60c07
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: b070c4f6364f8beccd397102fa00642560414326
ms.sourcegitcommit: 4cf65f627f2d370ee4a4decae1acbb9658874056
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2017
---
# <a name="access-policies"></a>Stratégies d’accès  
Les stratégies d’accès vous permettent de surveiller et bloquer l’accès à des applications spécifiques en fonction de l’utilisateur, l’emplacement ou l’appareil.

Avant de pouvoir créer une stratégie d’accès, vous devez [déployer le proxy](proxy-deployment.md). Les stratégies d’accès vous permettent de définir des règles pour gérer et surveiller l’accès des utilisateurs à vos applications cloud.
Par exemple, vous pouvez définir une stratégie pour effectuer les actions suivantes :
- Bloquer l’accès à toutes les applications cloud à partir d’appareils non gérés.
- Bloquer l’accès à partir de pays spécifiques, comme tous les pays autres que l’Angleterre.
- Bloquer l’accès à tous les groupes d’utilisateurs autres que Sales, Admins et Salesforce.
- Autoriser l’accès, mais surveiller toutes les tentatives de connexion et alerter quand une personne qui n’appartient pas à un groupe d’utilisateurs spécifique tente de se connecter.

Pour créer une stratégie d’activité, suivez cette procédure :  
  
1.  Dans la console, cliquez sur **Contrôle**, puis sur **Stratégies**.  
  
2.  Cliquez sur **Créer une stratégie** et sélectionnez **Stratégie d’accès**.  
  
3.  Donnez à votre stratégie un nom et une description. Si vous le souhaitez, vous pouvez la baser sur un modèle ; pour plus d’informations sur les modèles de stratégie, consultez [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md).  
  
3. Définissez une **Gravité de la stratégie**. Si Cloud App Security est défini pour vous envoyer des notifications en cas de correspondances de stratégie pour un niveau de gravité de stratégie spécifique, votre sélection détermine si les correspondances de cette stratégie déclenchent une notification.

4.  Dans **Catégorie**, liez la stratégie au type de risque le plus approprié. Ce champ est à titre informatif uniquement et vous permet de rechercher ultérieurement des stratégies et alertes spécifiques, selon le type de risque.  Le risque est peut-être déjà présélectionné en fonction de la catégorie pour laquelle vous avez choisi de créer la stratégie. Par défaut, les stratégies d’accès sont définies sur **Contrôle d’accès**.  
  
5.  Pour définir les applications découvertes qui déclenchent cette stratégie, **Créer un filtre pour les fichiers sur lesquels cette stratégie s’appliquera**, 

 > [!NOTE] 
 > Quand vous utilisez des filtres de stratégie, le filtre **Contains (Contient)** recherche uniquement des mots entiers, séparés par des virgules, points, espaces ou traits de soulignement. Par exemple, si vous recherchez **malware** ou **virus**, il trouve virus_malware_file.exe, mais pas malwarevirusfile.exe. Si vous recherchez **malware.exe**, vous obtenez tous les fichiers exe dont le nom contient malware ou exe, tandis que si vous recherchez **"malware.exe"** (avec les guillemets), vous n’obtenez que les fichiers dont le nom contient exactement « malware.exe ». **Equals (Est égal à)** recherche uniquement la chaîne complète ; par exemple, si vous recherchez **malware.exe**, il trouve malware.exe, mais pas malware.exe.txt.  

6.   Sous **Source d’activité**, sélectionnez les applications auxquelles la stratégie doit être appliquée : toutes les applications ou des applications spécifiques.

7. Utilisez les filtres pour sélectionner les utilisateurs, les applications et les appareils pour lesquels vous voulez déclencher une correspondance de stratégie. Pour obtenir la liste complète des filtres, consultez [Filtres de stratégie d’accès](#access-policy-filters).

8.  Choisissez les **Actions** que Cloud App Security doit exécuter quand une correspondance est détectée :
    - Autoriser et alerter : Si vous sélectionnez Autoriser, l’accès des applications est surveillé, mais pas bloqué. Par défaut, si **Autoriser** est sélectionné, les alertes sont automatiquement envoyées au portail Cloud App Security. 
    - Bloquer : Si vous sélectionnez **Bloquer**, quand les conditions de la stratégie sont remplies, l’utilisateur ou l’appareil ne peut pas accéder à l’application cloud. L’utilisateur reçoit un message qui lui indique qu’il n’a pas accès à l’application.
  
>[!WARNING]
>Il est vivement recommandé de créer d’abord la stratégie à l’aide de l’action **Autoriser** et de vérifier les résultats. Une fois seulement que vous avez déterminé que la stratégie ne bloque pas accidentellement des personnes, vous pouvez la définir sur **Bloquer** l’accès.
  
9. Définissez les alertes que vous voulez recevoir quand la stratégie trouve une correspondance. Vous pouvez définir une limite pour ne pas recevoir trop d’alertes et choisir de recevoir les alertes par e-mail ou SMS, ou les deux.

10. Pour afficher les correspondances de stratégie d’accès, cliquez sur **Contrôle**, puis sur **Stratégies**. Filtrez les résultats pour afficher uniquement les stratégies d’accès à l’aide du filtre **Type** en haut. Pour plus d’informations sur les correspondances pour chaque stratégie, cliquez sur une stratégie. Cliquez sur l’onglet **Historique** pour consulter un historique remontant jusqu’à 6 mois de correspondances de stratégie.     
  
## Informations de référence sur les stratégies d’accès  <a name="access-policy-filters"></a>

Cette section fournit des informations de référence sur les filtres de stratégie d’accès. 

- Balise de l’appareil : La balise de l’appareil vous permet de filtrer les appareils gérés en sélectionnant **Conforme**, **Joint à un domaine** et **Certificat client valide**.
- Type d’appareil : Aucune valeur, PC, Mobile, Tablette, Autres
-   Adresse IP : Adresse IP brute, catégorie IP ou balise IP à partir de laquelle l’activité a été réalisée.  
    - Adresse IP brute : Vous permet de rechercher des activités qui ont été réalisées sur ou par des adresses IP brutes qui sont égales à/ne sont pas égales à ou commencent par/ne commencent pas par une séquence particulière, ou des adresses IP brutes qui sont définies/ne sont pas définies. 
    - Catégorie IP : Catégorie de l’adresse IP à partir de laquelle l’activité a été réalisée, par exemple, toutes les activités de la plage d’adresses IP administratives. Les catégories doivent être configurées de façon à inclure les adresses IP appropriées, à l’exception de la catégorie « Risqué », qui est préconfigurée et inclut deux balises IP : Proxy anonyme et Tor. Pour découvrir comment configurer les catégories IP, consultez [Organiser les données selon vos besoins](ip-tags.md).  
    - Balise IP : Balise de l’adresse IP à partir de laquelle l’activité a été exécutée, par exemple toutes les activités des adresses IP de proxy anonyme. Cloud App Security crée un ensemble de balises IP prédéfinies qui ne sont pas configurables. Vous pouvez aussi configurer vos propres balises IP. Pour plus d’informations sur la configuration de vos propres balises IP, consultez [Organiser les données selon vos besoins](ip-tags.md).
   Les balises IP prédéfinies sont les suivantes :
    - Applications Microsoft (14 applications)
    - Proxy anonyme
    - Botnet (vous voyez que l’activité a été effectuée par un botnet avec un lien qui vous permet d’en savoir plus sur le botnet spécifique)
    - Adresse IP d’analyse du darknet
    - Serveur de commande et contrôle de programmes malveillants
    - Analyseur de connectivité à distance
    - Fournisseurs par satellite
    - Proxy intelligent et proxy d’accès (délibérément omis)
    - Nœuds de sortie Tor
    - Zscaler

-   Emplacement : Pays à partir duquel la demande d’accès a été effectuée.    

- ISP inscrit : 

-   Utilisateur : Utilisateur qui a exécuté l’activité, qui peut être filtré en domaine, groupe, nom ou organisation. Pour filtrer les activités sans utilisateur spécifique, vous pouvez utiliser l’opérateur « n’est pas défini ».  
    -   Organisation utilisateur : Unité d’organisation de l’utilisateur qui a effectué l’activité, par exemple toutes les activités effectuées par les utilisateurs EMEA_marketing.  
    -   Groupe d’utilisateurs : Groupes d’utilisateurs spécifiques que vous pouvez importer à partir d’applications connectées, par exemple, les administrateurs Office 365.  
    -   Nom d’utilisateur : Recherchez un nom d’utilisateur spécifique. Pour afficher la liste des utilisateurs membres d’un groupe d’utilisateurs spécifique, dans le **tiroir Activité**, cliquez sur le nom du groupe d’utilisateurs. Vous accédez alors à la page Comptes qui liste tous les utilisateurs figurant dans le groupe. À partir de cette page, vous pouvez explorer plus en détail les comptes d’utilisateurs spécifiques dans le groupe.
       -  Vous pouvez affiner les filtres **Groupe d’utilisateurs** et **Nom d’utilisateur** en choisissant le filtre **En tant que**, puis en sélectionnant le rôle de l’utilisateur parmi les rôles suivants :
            - Objet d’activité uniquement : cela signifie que l’utilisateur ou le groupe d’utilisateurs sélectionné n’a pas effectué l’activité en question, mais qu’il était l’objet de l’activité
            - Acteur uniquement : cela signifie que l’utilisateur ou le groupe d’utilisateurs a effectué l’activité
            - N’importe quel rôle : cela signifie que l’utilisateur ou le groupe d’utilisateurs a participé à l’activité, soit en effectuant l’activité, soit en étant l’objet de l’activité

-   Agent utilisateur : Agent utilisateur à partir duquel l’activité a été effectuée.  
  
-   Étiquette agent utilisateur : Balise d’agent utilisateur intégrée, par exemple toutes les activités d’un navigateur obsolète ou d’anciens systèmes d’exploitation.  
    
>[!NOTE]
> Si vous voulez effacer les filtres, vous pouvez le faire à tout moment en cliquant sur l’icône d’effacement des filtres ![icône d’effacement des filtres](./media/clear-filters.png).


## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  