---
title: Utilisation des alertes dans Cloud App Security | Microsoft Docs
description: Cette rubrique fournit une liste et une description de toutes les alertes.
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/18/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: f118a3bf-1663-46ba-884f-b1b03a84ab66
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: b5027699862a6cfe4b8dd8037f26d569b788a412
ms.sourcegitcommit: 27170447acfaeded585c264e425a46a485e7fb19
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2017
---
# <a name="alerts"></a>Alertes
Pour afficher les alertes :

Dans le portail Cloud App Security, cliquez sur Alertes.


![menu Alerte](./media/alert-menu.png)

Pour gérer chaque alerte, cliquez sur l’alerte dans la table et sélectionnez l’une des options suivantes :
- **Résoudre l’alerte** : Après avoir examiné l’alerte et pris des mesures pour la solutionner, cliquez sur **résoudre l’alerte**. Vous pouvez entrer un commentaire pour garder une trace des actions prises, mais également **envoyer des commentaires à l’équipe de Cloud App Security** concernant l’alerte. Lorsqu’une alerte est résolue, elle n’apparaît plus dans la table des alertes.
- Résoudre l’alerte et **Marquer comme lu** : Vous pouvez laisser l’alerte ouverte, mais la marquer comme lue.
- Résoudre l’alerte et **Ajuster la stratégie** : Vous pouvez modifier la stratégie de mise en correspondance de l’alerte en réponse à l’alerte.
- **Masquer** : Vous pouvez masquer l’alerte pour qu’elle n’apparaisse plus dans la table, mais elle ne n’affichera pas comme résolue. Cette option est plus susceptible d’être utilisée lorsque l’alerte est un faux positif ou bénigne.

Les types d’alertes suivants sont affichés. 

## <a name="built-in-alerts"></a>Alertes intégrées

|Nom d'alerte|ID d’alerte|Description|
|----|----|----|
|Nouvel emplacement|ALERT_GEOLOCATION_NEW_COUNTRY|Un nouvel emplacement a été détecté depuis le début de l’analyse (jusqu’à 6 mois). Cette alerte ne s’affiche qu’une fois pour chaque pays pour toute votre organisation. |
|Nouvel utilisateur administrateur|ALERT_ADMIN_USER|Un nouvel administrateur a été détecté pour une application spécifique : il peut s’agir d’une personne qui est l’administrateur d’une application et maintenant l’administrateur d’une autre application. Cette alerte concernant le type d’administrateur spécifique, elle s’affiche chaque fois que le type de l’administrateur est modifié. Si un utilisateur perd, puis récupère des privilèges d’administrateur, cette alerte s’affiche.|
|Compte inactif|ALERT_ZOMBIE_USER|Si un utilisateur est inactif pendant 60 jours par application, par exemple si une personne est active dans Box, mais n’a pas utilisé G Suite pendant 60 jours, l’utilisateur est considéré comme inactif dans G Suite. Une balise est ajoutée à ces utilisateurs pour que vous puissiez rechercher les comptes inactifs.|
|Emplacement de l’administrateur inattendu|ALERT_NEW_ADMIN_LOCATION|Un nouvel emplacement a été détecté pour les administrateurs depuis le début de l’analyse (jusqu’à 6 mois). Cette alerte ne s’affiche qu’une fois pour chaque pays et pour tout administrateur de votre organisation. |
|Compte compromis|ALERT_COMPROMISED_ACCOUNT|Si une violation s’est produite dans une application et que la liste des comptes affectés est publiée, Cloud App Security télécharge la liste et la compare à votre liste d’utilisateurs, notamment les utilisateurs internes, les utilisateurs externes et les comptes personnels. |

## <a name="custom-alerts"></a>Alertes personnalisées

|Nom d'alerte|ID d’alerte|Description|
|----|----|----|
|Alerte d’activité suspecte|ALERT_SUSPICIOUS_ACTIVITY|Les activités suspectes sont évaluées en fonction du degré de suspicion de l’activité anormale (Un compte inactif est-il impliqué ? À partir d’un nouvel emplacement ?) Ces critères sont tous calculés ensemble pour fournir un indice de risque selon les facteurs de risque suivants : <br>L’utilisateur est administrateur <br>Utilisateur strictement à distance<br>Proxy anonyme<br> Toute la session ne compte que des échecs de connexion<br>Nombreux échecs de connexion<br>Nouveau (administrateur)<br>IP/ISP/pays/agent utilisateur pour utilisateur/client<br> IP/ISP/pays/agent utilisateur utilisé uniquement par utilisateur (administrateur)<br>Première activité utilisateur (administrateur) depuis un certain temps<br>Première fois que cette activité administrative particulière est exécutée depuis un certain temps<br>Cette activité administrative particulière n’est pas courante / n’a jamais été exécutée auparavant<br>Cette adresse IP ne présentait que des échecs de connexion dans le passé<br>Voyage impossible|
|Alerte d’utilisation suspecte du cloud|ALERT_DISCOVERY_ANOMALY_DETECTION|La détection des anomalies Cloud Discovery vérifie le modèle du comportement normal et recherche des utilisateurs ou des applications qui sont utilisés de façon inhabituelle. |
|Violation de stratégie d’activité|ALERT_CABINET_EVENT_MATCH_AUDIT|Cette alerte vous informe quand une correspondance de stratégie a été détectée.|
|Violation de stratégie de fichier|ALERT_CABINET_EVENT_MATCH_FILE|Cette alerte vous informe quand une correspondance de stratégie a été détectée.|
|Violation de stratégie de proxy|ALERT_CABINET_INLINE_EVENT_MATCH|Cette alerte vous informe quand une correspondance de stratégie a été détectée.|
|Violation de stratégie de champ|ALERT_CABINET_EVENT_MATCH_OBJECT|Cette alerte vous informe quand une correspondance de stratégie a été détectée.|
|Nouveau service découvert|ALERT_CABINET_DISCOVERY_NEW_SERVICE|Une nouvelle application a été découverte.|
|Utilisation d’un compte personnel|ALERT_PERSONAL_USER_SAGE|Selon les partages de fichiers et les noms d’utilisateur, le moteur de détection recherche des comptes personnels. |

## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  