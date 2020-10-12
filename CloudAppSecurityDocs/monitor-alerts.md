---
title: Surveiller les alertes déclenchées dans Cloud App Security
description: Cet article fournit une liste et une description de toutes les alertes.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: e5effef1c69cf3a8ce44218a8838bbb4d0ef1614
ms.sourcegitcommit: b173d24dba412e81801c498cc0c3623ad9e31601
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2020
ms.locfileid: "91941567"
---
# <a name="monitor-alerts-in-cloud-app-security"></a>Surveiller les alertes dans Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Les alertes constituent un bon point de départ pour comprendre votre environnement cloud de façon plus approfondie. Cet article fournit une liste et une description de toutes les alertes.

## <a name="monitoring-your-alerts"></a>Surveillance de vos alertes

Nous vous incitons à examiner vos alertes. En comprenant le déclenchement des alertes, vous pouvez les utiliser en tant qu’outils pour modifier vos stratégies.

**Pour afficher les alertes :** Dans le portail Microsoft Cloud App Security, cliquez sur **alertes**.

![menu Alerte](media/alert-menu.png)

- **Ignorez** une alerte lorsque vous l’avez vue et que vous avez déterminé qu’elle était sans importance.
  - Entrez un **commentaire** pour expliquer pourquoi vous avez ignoré l’alerte.
  - **Envoyez-nous vos commentaires sur cette alerte**. Ils seront examinés par notre équipe de recherche de sécurité afin d’améliorer les alertes.

- **Résolvez** l’alerte si vous vous y intéressez et éliminez le risque.

  - L’alerte n’apparaîtra plus dans le tableau des alertes.
  - **Marquez l’alerte comme non lue** si vous avez commencé à vous y intéresser et que vous poursuivrez vos recherches plus tard.
  - **Ajustez la stratégie** correspondant à l’alerte pour améliorer les prochaines correspondances d’alerte.
  - La résolution d’une alerte vous donne la possibilité d’entrer un commentaire et d’**Envoyer des commentaires à l’équipe de Cloud App Security**.

## <a name="deployment-of-our-enhanced-alert-monitoring-and-management-experience"></a>Déploiement de notre expérience de gestion et de surveillance des alertes améliorée

Dans le cadre de nos améliorations constantes de la surveillance et de la gestion des alertes, la page Cloud App Security des alertes a été améliorée en fonction de vos commentaires. Dans l’expérience améliorée, les États **résolus** et **rejetés** sont remplacés par l’état **fermé** , et les alertes fermées ont l’un des types de résolution suivants :

- **Vrai positif**: une alerte sur une activité malveillante confirmée
- **Bénigne**: alerte sur une activité suspecte mais pas malveillante, comme un test de pénétration ou une autre action suspecte autorisée
- **Faux positif**: alerte sur une activité non malveillante

> [!NOTE]
> L’expérience améliorée s’applique uniquement aux nouvelles alertes et n’affecte pas l’état des alertes existantes (héritées) qui ont été **résolues** ou **ignorées**.

![Page alertes améliorées](media/monitor-alerts/enhanced-alerts.png)

### <a name="enhanced-alert-monitoring"></a>Analyse améliorée des alertes

Dans la page alertes améliorées, la colonne **État** indique si une alerte est ouverte ou fermée et que la colonne **type de résolution** affiche le type de résolution utilisé lors de la fermeture d’une alerte. Vous pouvez utiliser le filtre d' **État** pour vous aider à identifier les alertes ouvertes ou fermées, puis à utiliser le filtre **avancé** , vous pouvez examiner plus en détail les alertes fermées par **type de résolution** à l’aide des types de résolution améliorés et hérités.

![Page alertes améliorées avec filtre avancé](media/monitor-alerts/enhanced-alerts-advanced-filter.png)

### <a name="enhanced-alert-management"></a>Gestion améliorée des alertes

Lors de la fermeture des alertes, choisissez l’une des options de résolution suivantes :

- **Fermer comme vrai positif**: si l’activité est confirmée comme malveillante
- **Fermer comme Bénin**: si l’activité est suspecte, mais pas comme une activité malveillante, comme un test de pénétration ou une autre action suspecte autorisée
- **Fermer comme faux positif**: si l’activité est confirmée comme non malveillante

Dans la fenêtre contextuelle qui s’affiche, indiquez la raison de la fermeture de l’alerte et renseignez le reste des détails en fonction des besoins, puis cliquez sur **Fermer l’alerte**.

![Fenêtre contextuelle des alertes améliorées](media/monitor-alerts/enhanced-alerts-close-resolution.png)

## <a name="built-in-alerts"></a>Alertes intégrées

Les types d’alertes suivants sont affichés.

|Nom de l’alerte|ID d’alerte|Description|
|----|----|----|
|Nouvel emplacement|ALERT_GEOLOCATION_NEW_COUNTRY|Un nouvel emplacement a été détecté depuis le début de l’analyse (jusqu’à 6 mois). Cette alerte ne s’affiche qu’une seule fois pour chaque pays/région de l’ensemble de votre organisation. |
|Nouvel utilisateur administrateur|ALERT_ADMIN_USER|Un nouvel administrateur a été détecté pour une application spécifique. Il se peut que cette personne soit l’administrateur d’une application et maintenant l’administrateur d’une autre application. Cette alerte concernant le type d’administrateur spécifique, elle s’affiche chaque fois que le type de l’administrateur est modifié. Si un utilisateur perd, puis récupère des privilèges d’administrateur, cette alerte s’affiche.|
|Compte inactif|ALERT_ZOMBIE_USER|Si un utilisateur est inactif pendant 60 jours par application, par exemple si une personne est active dans Box, mais n’a pas utilisé G Suite pendant 60 jours, l’utilisateur est considéré comme inactif dans G Suite. Une balise est ajoutée à ces utilisateurs pour que vous puissiez rechercher les comptes inactifs.|
|Emplacement de l’administrateur inattendu|ALERT_NEW_ADMIN_LOCATION|Un nouvel emplacement a été détecté pour les administrateurs depuis le début de l’analyse (jusqu’à 6 mois). Cette alerte ne s’affiche qu’une seule fois pour chaque pays/région de l’administrateur de votre organisation. |
|Compte compromis|ALERT_COMPROMISED_ACCOUNT|Si une violation s’est produite dans une application et que la liste des comptes affectés est publiée, Cloud App Security télécharge la liste et la compare à votre liste d’utilisateurs. La liste d’utilisateurs comprend notamment les utilisateurs internes, les utilisateurs externes et les comptes personnels. |

## <a name="custom-alerts"></a>Alertes personnalisées

Les types d’alertes suivants sont affichés.

|Nom de l’alerte|ID d’alerte|Description|
|----|----|----|
|Alerte d’activité suspecte|ALERT_SUSPICIOUS_ACTIVITY|Les activités suspectes sont évaluées en fonction du degré de suspicion de l’activité anormale (Un compte inactif est-il impliqué ? S’agit-il d’un nouvel emplacement ?) Ces critères sont tous calculés ensemble pour fournir un score de risque en fonction des facteurs de risque suivants : <br />L’utilisateur est administrateur <br />Utilisateur strictement à distance<br />Proxy anonyme<br /> Toute la session ne compte que des échecs de connexion<br />Nombreux échecs de connexion<br />Nouveau (administrateur)<br />IP/ISP/pays/agent utilisateur pour utilisateur/client<br /> IP/ISP/pays/agent utilisateur utilisé uniquement par utilisateur (administrateur)<br />Première activité utilisateur (administrateur) depuis un certain temps<br />Première fois que cette activité administrative particulière est exécutée depuis un certain temps<br />Cette activité administrative particulière n’est pas courante/n’a jamais été exécutée auparavant<br />Cette adresse IP ne présentait que des échecs de connexion dans le passé<br />Voyage impossible|
|Alerte d’utilisation suspecte du cloud|ALERT_DISCOVERY_ANOMALY_DETECTION|La détection des anomalies Cloud Discovery vérifie le modèle du comportement normal et recherche des utilisateurs ou des applications qui sont utilisés de façon inhabituelle. |
|Violation de stratégie d’activité|ALERT_CABINET_EVENT_MATCH_AUDIT|Cette alerte vous informe quand une correspondance de stratégie a été détectée.|
|Violation de stratégie de fichier|ALERT_CABINET_EVENT_MATCH_FILE|Cette alerte vous informe quand une correspondance de stratégie a été détectée.|
|Violation de stratégie de proxy|ALERT_CABINET_INLINE_EVENT_MATCH|Cette alerte vous informe quand une correspondance de stratégie a été détectée.|
|Violation de stratégie de champ|ALERT_CABINET_EVENT_MATCH_OBJECT|Cette alerte vous informe quand une correspondance de stratégie a été détectée.|
|Nouveau service découvert|ALERT_CABINET_DISCOVERY_NEW_SERVICE|Une nouvelle application a été découverte.|
|Utilisation d’un compte personnel|ALERT_PERSONAL_USER_SAGE|Selon les partages de fichiers et les noms d’utilisateur, le moteur de détection recherche des comptes personnels. |

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
