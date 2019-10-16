---
title: Anonymisation des données d’utilisateur dans Cloud App Security
description: Cet article fournit des informations sur la façon de protéger la confidentialité des utilisateurs en anonymisant les noms d’utilisateur dans vos données Cloud Discovery.
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
ms.assetid: eb250ede-fede-4699-a08b-b8ea4b232f07
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: b83aa653074e0b441634c8560821fc4cf4d71373
ms.sourcegitcommit: c342abeec95359ddabdabcc3a081a0f91d52407c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72335493"
---
# <a name="cloud-discovery-data-anonymization"></a>Anonymisation des données Cloud Discovery

*S’applique à : Microsoft Cloud App Security*

L’anonymisation de données Cloud Discovery vous permet de protéger la confidentialité des utilisateurs. Une fois que le journal des données est téléchargé sur le portail Microsoft Cloud App Security, il est purgé et toutes les informations des noms d’utilisateur sont remplacées par des noms d’utilisateur chiffrés. De cette façon, toutes les activités cloud restent anonymes. Quand c’est nécessaire, pour une enquête de sécurité spécifique (par exemple une violation de la sécurité ou une activité utilisateur suspecte), les administrateurs peuvent résoudre le nom d’utilisateur réel. Si un administrateur a une raison de suspecter un utilisateur spécifique, il peut également rechercher le nom d’utilisateur chiffré d’un nom d’utilisateur connu, puis commencer son investigation avec le nom d’utilisateur chiffré. La conversion de chaque nom d’utilisateur est auditée dans le **journal de gouvernance** du portail.

Points clés :
-   Aucune information privée n’est stockée ou affichée. Seulement des informations chiffrées.
-   Les données privées sont chiffrées en utilisant AES-128 avec une clé dédiée par client.
-   La résolution des noms d’utilisateur est correctement effectuée, par nom d’utilisateur en déchiffrant un nom d’utilisateur chiffré donné.


## <a name="how-data-anonymization-works"></a>Fonctionnement de l’anonymisation des données

1. Il existe trois façons d’appliquer l’anonymisation des données : 
    
   - Vous pouvez anonymiser les données d’un fichier journal spécifique en [créant un rapport de capture instantanée](create-snapshot-cloud-discovery-reports.md) et en sélectionnant **Anonymiser les informations privées**.

     ![Anonymiser les données de capture instantanée](./media/anonymize-log.png)

   - Vous pouvez anonymiser les données d’un [chargement automatisé d’une nouvelle source de données](configure-automatic-log-upload-for-continuous-reports.md) en sélectionnant **Anonymiser les informations privées** quand vous ajoutez la nouvelle source de données.  
  
     ![Anonymiser les données des journaux](./media/anonymize-autolog.png)

   - Vous pouvez définir le comportement par défaut dans Cloud App Security pour anonymiser toutes les données des rapports de capture instantanée des fichiers journaux chargés et celles des rapports continus du collecteur de journaux comme suit :
     
     1. Sous l’icône Paramètres, sélectionnez **Paramètres Cloud Discovery**.
     
     2. Dans l’onglet Anonymisation, pour anonymiser les noms d’utilisateur par défaut, sélectionnez **Anonymiser les informations privées par défaut dans les nouveaux rapports et les nouvelles sources de données**. Vous pouvez aussi sélectionner **Anonymiser les informations de l'ordinateur par défaut dans le rapport « Utilisateurs du point de terminaison Win10 »** .

     3. Sous Clé de chiffrement, choisissez si vous voulez **Utiliser la clé dédiée générée pour votre portail** ou **Utiliser une clé personnalisée**. Si vous voulez **Utiliser une clé personnalisée**, entrez une clé de chiffrement UTF8 de 16 octets.
     4. Cliquez sur **Save**.
 
        ![Anonymisation](./media/anonymizer1.png)
  

2. Quand l’anonymisation est sélectionnée, Cloud App Security analyse le journal du trafic et extrait les attributs de données spécifiques.
3. Cloud App Security remplace le nom d’utilisateur par un nom d’utilisateur chiffré.
4. Il analyse ensuite les données d’utilisation cloud et génère des rapports Cloud Discovery basés sur les données anonymisées.
 
   ![Anonymiser le tableau de bord Cloud Discovery](./media/anonymize-dashboard.png)
 
5. Pour des investigations spécifiques, comme pour une alerte d’utilisation anormale, vous pouvez résoudre le nom d’utilisateur spécifique dans le portail et spécifier une justification liée à l’activité de l’entreprise. 
   Cette page peut également être utilisée pour rechercher le nom d’utilisateur chiffré d’un nom d’utilisateur connu. 

   1. Sous l’icône Paramètres, sélectionnez **Paramètres Cloud Discovery**.
   2. Sous l’onglet **Anonymisation**, sous **Anonymiser et résoudre les noms d’utilisateur**, entrez une justification expliquant pourquoi vous effectuez la résolution.
   3. Sous **Entrer le nom d’utilisateur à résoudre**, sélectionnez **À partir du nom anonymisé** et entrez le nom d’utilisateur anonymisé, ou sélectionnez **À anonymiser** et entrez le nom d’utilisateur d’origine à résoudre. Cliquez sur **Résoudre**. 

   ![Anonymisation](./media/anonymizer.png)

6. L’action est auditée dans le **journal de gouvernance** du portail. 

    ![Anonymisation](./media/anonymize-gov-log.png)




  
      
## <a name="next-steps"></a>Étapes suivantes 
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)  
    
      
  
