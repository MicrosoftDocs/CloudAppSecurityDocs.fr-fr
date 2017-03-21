---
title: "Informations de référence sur les modèles de stratégie dans Cloud App Security | Microsoft Docs"
description: "Cette rubrique fournit des informations sur la façon dont les stratégies sont utilisées et configurées pour contrôler l’usage des applications cloud."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/23/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: a6658937-57a2-484a-85cb-5a4cdbeeb002
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: a8565105b128f4109ceab7a93714cadf96defa4d
ms.sourcegitcommit: 355226ee21981563066d637e7db0bff0d53c2da6
translationtype: HT
---
# <a name="policy-templates"></a>Modèles de stratégie

Voici une liste de tous les modèles de stratégie qui existent dans Cloud App Security. Il est recommandé de commencer avec une stratégie créée à partir d’un modèle existant pour une utilisation plus facile.

|Nom du modèle|Description|
|----|----|
|Nouvelle application appréciée|Alerte quand de nouvelles applications utilisées par plus de 500 utilisateurs sont découvertes.|
|Fichier partagé avec un domaine non autorisé|Alerte quand un fichier est partagé avec un domaine non autorisé (par exemple votre concurrent).|
|Plusieurs tentatives de connexion à une application ayant échoué pour un utilisateur|Alerte quand un utilisateur tente de se connecter à une même application et y échoue plus de 10 fois en 5 minutes.|
|Comportement anormal par des utilisateurs découverts|Alerte quand un comportement anormal est détecté pour des utilisateurs et des applications découverts, comme de grandes quantités de données chargées en comparaison d’autres utilisateurs ou des transactions utilisateur importantes par rapport à l’historique de l’utilisateur.|
|Vérification de la conformité d’applications CRM|Alerte quand de nouvelles applications CRM non conformes à SOC2, SSAE 16, ISAE 3402, ISO 27001 et HIPAA et utilisées par plus de 50 utilisateurs avec une utilisation quotidienne totale de plus de 50 Mo sont découvertes.|
|Détection d’anomalie générale|Alerte quand une session anormale est détectée dans une des applications approuvées, comme voyage impossible, modèle de connexion, compte inactif.|
|Nouvelle application avec volume de chargement élevé|Alerte quand de nouvelles applications dont le trafic de chargement quotidien total est supérieur à 500 Mo sont découvertes.|
|Téléchargement massif par un même utilisateur|Alerte quand un même utilisateur effectue plus de 30 téléchargements en 5 minutes.|
|Nouvelle application avec volume élevé|Alerte quand de nouvelles applications qui ont un trafic quotidien total de plus de 500 Mo sont découvertes.|
|Vérification de conformité des applications de stockage cloud|Alerte quand de nouvelles applications de stockage cloud non conformes à SOC2, SSAE 16, ISAE 3402 et PCI DSS, et utilisées par plus de 50 utilisateurs avec une utilisation quotidienne totale de plus de 50 Mo, sont découvertes.|
|Nouvelle application à risques|Alerte quand de nouvelles applications dont le score de risque est inférieur à 6 sont utilisées par plus de 50 utilisateurs avec une utilisation quotidienne totale de plus de 50 Mo sont découvertes.|
|Vérification de la conformité d’applications de collaboration|Alerte quand de nouvelles applications de collaboration non conformes à SOC2 et SSAE 16 et utilisées par plus de 50 utilisateurs avec une utilisation quotidienne totale de plus de 50 Mo sont découvertes.|
|Connexion à partir d’une adresse IP à risques|Alerte quand un utilisateur se connecte à vos applications approuvées à partir d’une adresse IP à risques. Par défaut, la catégorie Adresses IP à risques contient les adresses qui ont des balises d’adresse IP Proxy anonyme, TOR ou Botnet. Vous pouvez ajouter d’autres adresses IP à cette catégorie dans la page des paramètres de plages d’adresses IP.|
|Activités d’administration à partir d’une adresse IP non-administrateur|Alerte quand un utilisateur administrateur effectue une activité d’administration à partir d’une adresse IP qui n’est pas incluse dans une catégorie de plage d’adresses IP spécifique. Vous pouvez définir d’autres adresses IP à risques en accédant à la page Paramètres et en sélectionnant des plages d’adresses IP.|
|Ouverture de session utilisateur à partir d’une adresse IP sans catégorie|Alerte quand un utilisateur ouvre une session à partir d’une adresse IP qui n’est pas incluse dans une catégorie de plage d’adresses IP spécifique. Vous pouvez catégoriser d’autres adresses IP à risques en accédant à la page Paramètres et en sélectionnant des plages d’adresses IP.|
|Fichier contenant des informations d’identification personnelle détecté dans le cloud (moteur DLP intégré)|Alerte quand un fichier contenant des informations d’identification personnelle est détecté par notre moteur de protection contre la perte de données intégré dans une application cloud approuvée.|
|Nouvelle application de gestion des ressources humaines|Alerte quand de nouvelles applications de gestion des ressources humaines utilisées par plus de 50 utilisateurs avec une utilisation quotidienne totale de plus de 50 Mo sont découvertes.|
|Fichier contenant des informations de carte de paiement détecté dans le cloud (moteur DLP intégré)|Alerte quand un fichier contenant des informations de carte de paiement est détecté par notre moteur de protection contre la perte de données intégré dans une application cloud approuvée.|
|Nouvelle application d’hébergement de code|Alerte quand de nouvelles applications d’hébergement de code utilisées par plus de 50 utilisateurs avec une utilisation quotidienne totale de plus de 50 Mo sont découvertes.|
|Nouvelle application de collaboration|Alerte quand de nouvelles applications de collaboration utilisées par plus de 50 utilisateurs avec une utilisation quotidienne totale de plus de 50 Mo sont découvertes.|
|Nouvelles applications de système de gestion des fournisseurs|Alerte quand de nouvelles applications de système de gestion des fournisseurs utilisées par plus de 50 utilisateurs avec une utilisation quotidienne totale de plus de 50 Mo sont découvertes.|
|Nouvelle application de réunion en ligne|Alerte quand de nouvelles applications de réunion en ligne utilisées par plus de 50 utilisateurs avec une utilisation quotidienne totale de plus de 50 Mo sont découvertes.|
|Comportement anormal d’adresses IP découvertes|Alerte quand un comportement anormal est détecté dans des adresses IP et des applications découvertes, comme de grandes quantités de données chargées par rapport à d’autres adresses IP ou des transactions d’application importantes par rapport à l’historique de l’adresse IP.|
|Nouvelle application de ventes|Alerte quand de nouvelles applications de ventes utilisées par plus de 50 utilisateurs avec une utilisation quotidienne totale de plus de 50 Mo sont découvertes.|
|Nouvelle application de stockage cloud|Alerte quand de nouvelles applications de stockage cloud utilisées par plus de 50 utilisateurs avec une utilisation quotidienne totale de plus de 50 Mo sont découvertes.|
|Code source partagé en externe|Alerte quand un fichier contenant du code source est partagé en dehors de votre organisation.|
|Nouvelle application CRM|Alerte quand de nouvelles applications CRM utilisées par plus de 50 utilisateurs avec une utilisation quotidienne totale de plus de 50 Mo sont découvertes.|
|Fichier contenant des informations médicales protégées détecté dans le cloud (moteur DLP intégré)|Alerte quand un fichier contenant des informations médicales protégées est détecté par notre moteur de protection contre la perte de données intégré dans une application cloud approuvée.|
|Fichier partagé avec des adresses e-mail personnelles|Alerte quand un fichier est partagé avec une adresse e-mail personnelle d’un utilisateur.|
|Certificats numériques partagés (extensions de fichier)|Alerte quand un fichier contenant des certificats numériques est partagé publiquement.|
|Fichiers obsolètes partagés en externe|Recherche les fichiers partagés en externe qui n’ont pas été ouverts ou modifiés au cours des 6 derniers mois et les supprime de votre lecteur.|



## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  