---
title: Utilisation des alertes dans Cloud App Security | Microsoft Docs
description: Cette rubrique fournit une liste et une description de toutes les alertes.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: f118a3bf-1663-46ba-884f-b1b03a84ab66
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: c542968b0946dad903d0e77e9f44c92d957cc8e1
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44143511"
---
*S’applique à : Microsoft Cloud App Security*

# <a name="alerts"></a>Alertes
Pour afficher les alertes :

Dans le portail Microsoft Cloud App Security, cliquez sur Alertes.


![menu Alerte](./media/alert-menu.png)

Si l’alerte que vous consultez n’est pas intéressante, vous pouvez la **Faire disparaître**. Vous pouvez entrer un commentaire pour expliquer la raison pour laquelle vous avez fait disparaître l’alerte et vous pouvez **Envoyer des commentaires à l’équipe de Cloud App Security**. Ces commentaires sont examinés par notre équipe de recherche de sécurité pour améliorer en permanence le mécanisme d’alerte. 

Si vous examinez l’alerte et éliminez le risque, vous pouvez **Résoudre** l’alerte. L’alerte n’apparaîtra plus dans le tableau des alertes. Si vous avez commencé à étudier le problème et que vous ne voulez pas oublier de continuer vos recherches, vous pouvez choisir l’option **Marquer comme non lue**. Vous pouvez également **Ajuster la stratégie** correspondant à l’alerte pour améliorer les prochaines correspondances d’alerte. La résolution d’une alerte vous donne également la possibilité d’entrer un commentaire et d’**Envoyer des commentaires à l’équipe de Cloud App Security**.



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

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  