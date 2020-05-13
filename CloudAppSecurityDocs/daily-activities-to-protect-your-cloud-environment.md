---
title: Utilisation du tableau de bord Cloud App Security
description: Cet article fournit des informations de base sur l’utilisation du tableau de bord Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 05/06/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 367778c25f0a56dd0db8f6457b884b02d382da6c
ms.sourcegitcommit: e0c2a8fbdce9cc0fd0d6b85c92e112fd306ad950
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83203009"
---
# <a name="working-with-the-dashboard"></a>Utilisation du tableau de bord

*S’applique à : Microsoft Cloud App Security*

Cet article décrit la procédure à suivre au quotidien avec Cloud App Security.  Une fois que Microsoft Cloud App Security est opérationnel, vous devez :

- Configurer les flux de données
- Approuver les applications que vous voulez autoriser les utilisateurs à utiliser
- Configurer des stratégies pour surveiller votre environnement cloud.

Vous pouvez ensuite utiliser Cloud App Security pour contrôler et protéger votre cloud, et pour gérer les risques.

## <a name="check-the-dashboard"></a>Consulter le tableau de bord

![Tableau de bord Cloud App Security](media/dashboard.png "dashboard")

Le tableau de bord Cloud App Security donne une vue d’ensemble des activités et des fonctionnalités, notamment :

- Alertes ouvertes
- Violations d’activité
- Violations de contenu
- Carte des activités qui représente l’origine de l’activité des utilisateurs
- Tendances de l’utilisation des applications connectées dans votre environnement cloud
- Utilisateurs principaux par détection de menace

Nous vous recommandons de vérifier le tableau de bord tous les jours pour voir les nouvelles alertes déclenchées. C’est un bon endroit pour surveiller l’intégrité de votre environnement cloud. Le tableau de bord vous permet de vous faire une idée de ce qui se passe.

## <a name="gradual-deployment-of-our-enhanced-dashboard"></a>Déploiement progressif de notre tableau de bord amélioré

Dans le cadre de nos améliorations constantes de la conception du portail, le tableau de bord Cloud App Security a été amélioré en fonction de vos commentaires. Le tableau de bord offre une expérience utilisateur améliorée avec le contenu et les données mis à jour.

Les informations présentées dans le tableau de bord sont une vue d’ensemble de toutes les informations les plus importantes concernant votre organisation. Chaque carte d’informations fournit des liens vers une investigation plus approfondie des informations présentées. Vous pouvez également choisir d’afficher les informations de tableau de bord pour une application spécifique à l’aide du filtre fourni.

![Tableau de bord Cloud App Security](media/dashboard-enhanced.png)

### <a name="what-can-you-expect-to-see-in-the-dashboard"></a>Que pouvez-vous vous attendre à voir dans le tableau de bord ?

- **Alertes ouvertes**  
Affiche le nombre d’alertes ouvertes, un graphique de la distribution de l’état des alertes et les alertes récentes

- **Applications découvertes**  
Affiche le nombre d’applications découvertes, un graphique de la distribution des risques d’application et les principales catégories d’applications par trafic.
- **Principaux utilisateurs à examiner**  
Affiche le nombre d’utilisateurs à examiner et les utilisateurs ayant la priorité d’investigation la plus élevée.
- **Contrôle d’application par accès conditionnel**  
Affiche le nombre d’applications protégées par contrôle d’application par accès conditionnel, ainsi que le nombre de sessions et d’actions protégées au cours des 30 derniers jours.
- **État des connecteurs d’application**  
Affiche le nombre d’instances d’applications connectées à l’API et leur état.
- **Fichiers infectés par un programme malveillant**  
Affiche le nombre de fichiers infectés par un programme malveillant.
- **Applications OAuth Office 365 privilégiées**  
Affiche le nombre d’applications OAuth rarement utilisées accordées à des autorisations hautement privilégiées.
- **Configuration de la sécurité Azure**  
Affiche le nombre et la gravité des recommandations de configuration de la sécurité Azure.
- **Configuration de la sécurité AWS**  
Affiche le nombre et la gravité des recommandations relatives à la configuration de la sécurité AWS.
- **Alertes DLP**  
Affiche un graphique des alertes DLP au cours des 30 derniers jours.
<!-- - **Activity map**  
Shows the global spread of activities performed by users over the last 30 days. -->

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Examiner les alertes](investigate.md)

[!INCLUDE [Open support ticket](includes/support.md)]
