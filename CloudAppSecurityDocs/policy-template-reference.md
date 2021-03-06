---
title: Informations de référence sur les modèles de stratégie pour Cloud App Security
description: Cet article fournit des informations sur les modèles de stratégie inclus dans Microsoft Cloud App Security.
ms.date: 12/1/2019
ms.topic: how-to
ms.openlocfilehash: 6ae6eec80234a858e1d854db004cc5a2615d1c79
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96310922"
---
# <a name="policy-template-reference"></a>Référence sur les modèles de stratégie

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Cet article fournit des informations sur les modèles de stratégie inclus dans Microsoft Cloud App Security.

## <a name="policy-templates"></a>Modèles de stratégie

Il est recommandé de commencer avec une stratégie créée à partir d’un modèle existant pour une utilisation plus facile. Ce tableau liste les modèles de stratégie qui existent dans Microsoft Cloud App Security.

|Catégorie de risque|Nom du modèle|Description|
|-----|----|----|
|Cloud Discovery|Comportement anormal par des utilisateurs découverts|Alerte quand un comportement anormal est détecté pour des utilisateurs et des applications découverts, comme de grandes quantités de données chargées en comparaison d’autres utilisateurs ou des transactions utilisateur importantes par rapport à l’historique de l’utilisateur.|
|Cloud Discovery|Comportement anormal d’adresses IP découvertes|Alerte quand un comportement anormal est détecté dans des adresses IP et des applications découvertes, comme de grandes quantités de données chargées par rapport à d’autres adresses IP ou des transactions d’application importantes par rapport à l’historique de l’adresse IP.|
|Cloud Discovery|Vérification de la conformité d’applications de collaboration|Alerte quand de nouvelles applications de collaboration non conformes à SOC2 et SSAE 16 et utilisées par plus de 50 utilisateurs avec une utilisation quotidienne totale de plus de 50 Mo sont découvertes.|
|Cloud Discovery|Vérification de conformité des applications de stockage cloud|Alerte quand de nouvelles applications de stockage cloud non conformes à SOC2, SSAE 16, ISAE 3402 et PCI DSS, et utilisées par plus de 50 utilisateurs avec une utilisation quotidienne totale de plus de 50 Mo sont découvertes.|
|Cloud Discovery|Vérification de la conformité d’applications CRM|Alerte quand de nouvelles applications CRM non conformes à SOC2, SSAE 16, ISAE 3402, ISO 27001 et HIPAA et utilisées par plus de 50 utilisateurs avec une utilisation quotidienne totale de plus de 50 Mo sont découvertes.|
|Cloud Discovery|Nouvelle application de stockage cloud|Alerte quand de nouvelles applications de stockage cloud utilisées par plus de 50 utilisateurs avec une utilisation quotidienne totale de plus de 50 Mo sont découvertes.|
|Cloud Discovery|Nouvelle application d’hébergement de code|Alerte quand de nouvelles applications d’hébergement de code utilisées par plus de 50 utilisateurs avec une utilisation quotidienne totale de plus de 50 Mo sont découvertes.|
|Cloud Discovery|Nouvelle application de collaboration|Alerte quand de nouvelles applications de collaboration utilisées par plus de 50 utilisateurs avec une utilisation quotidienne totale de plus de 50 Mo sont découvertes.|
|Cloud Discovery|Nouvelle application CRM|Alerte quand de nouvelles applications CRM découvertes sont utilisées par plus de 50 utilisateurs avec une utilisation quotidienne totale de plus de 50 Mo.|
|Cloud Discovery|Nouvelle application avec volume élevé|Alerte quand de nouvelles applications qui ont un trafic quotidien total de plus de 500 Mo sont découvertes.|
|Cloud Discovery|Nouvelle application avec volume de chargement élevé|Alerte quand de nouvelles applications dont le trafic de chargement quotidien total est supérieur à 500 Mo sont découvertes.|
|Cloud Discovery|Nouvelle application de gestion des ressources humaines|Alerte quand de nouvelles applications de gestion des ressources humaines utilisées par plus de 50 utilisateurs avec une utilisation quotidienne totale de plus de 50 Mo sont découvertes.|
|Cloud Discovery|Nouvelle application de réunion en ligne|Alerte quand de nouvelles applications de réunion en ligne utilisées par plus de 50 utilisateurs avec une utilisation quotidienne totale de plus de 50 Mo sont découvertes.|
|Cloud Discovery|Nouvelle application appréciée|Alerte quand de nouvelles applications utilisées par plus de 500 utilisateurs sont découvertes.|
|Cloud Discovery|Nouvelle application à risques|Alerte quand de nouvelles applications dont le score de risque est inférieur à 6 sont utilisées par plus de 50 utilisateurs avec une utilisation quotidienne totale de plus de 50 Mo sont découvertes.|
|Cloud Discovery|Nouvelle application de ventes|Alerte quand de nouvelles applications de ventes utilisées par plus de 50 utilisateurs avec une utilisation quotidienne totale de plus de 50 Mo sont découvertes.|
|Cloud Discovery|Nouvelles applications de système de gestion des fournisseurs|Alerte quand de nouvelles applications de système de gestion des fournisseurs utilisées par plus de 50 utilisateurs avec une utilisation quotidienne totale de plus de 50 Mo sont découvertes.|
|DLP|Code source partagé en externe|Alerte quand un fichier contenant du code source est partagé en dehors de votre organisation.|
|DLP|Fichier contenant des informations de carte de paiement détecté dans le cloud (moteur DLP intégré)|Alerte quand un fichier contenant des informations de carte de paiement est détecté par le moteur de protection contre la perte de données intégré à Microsoft Cloud App Security dans une application cloud approuvée.|
|DLP|Fichier contenant des informations médicales protégées détecté dans le cloud (moteur DLP intégré)|Alerte quand un fichier contenant des informations médicales protégées est détecté par le moteur de protection contre la perte de données intégré à Microsoft Cloud App Security dans une application cloud approuvée.|
|DLP|Fichier contenant des informations privées détecté dans le cloud (moteur DLP intégré)|Alerte quand un fichier contenant des données personnelles est détecté par le moteur de protection contre la perte de données intégré à Microsoft Cloud App Security dans une application cloud approuvée.|
|Détection de menaces|Activités d’administration à partir d’une adresse IP externe à l’entreprise|Alerte quand un utilisateur administrateur effectue une activité d’administration à partir d’une adresse IP qui n’est pas incluse dans la catégorie de plage d’adresses IP de l’entreprise. Commencez par configurer vos adresses IP d’entreprise en accédant à la page Paramètres et en définissant **Plages d’adresses IP**.|
|Détection de menaces|Connexion à partir d’une adresse IP à risques|Alerte quand un utilisateur se connecte à vos applications approuvées à partir d’une adresse IP à risque. Par défaut, la catégorie Adresses IP à risques contient les adresses qui ont des balises d’adresse IP Proxy anonyme, TOR ou Botnet. Vous pouvez ajouter d’autres adresses IP à cette catégorie dans la page des paramètres de plages d’adresses IP.|
|Détection de menaces|Téléchargement massif par un même utilisateur|Alerte quand un même utilisateur effectue plus de 50 téléchargements en 1 minutes.|
|Détection de menaces|Plusieurs tentatives de connexion utilisateur à une application ayant échoué|Alerte quand un utilisateur tente de se connecter à une application et y échoue plus de 10 fois en cinq minutes.|
|Détection de menaces|Activité de ransomware potentielle|Alerte quand un utilisateur charge des fichiers dans le cloud susceptibles d’être infectés par un ransomware.|
|Contrôle partagé|Fichier partagé avec des adresses e-mail personnelles|Alerte quand un fichier est partagé avec l’adresse de messagerie personnelle d’un utilisateur.|
|Contrôle partagé|Fichier partagé avec un domaine non autorisé|Alerte quand un fichier est partagé avec un domaine non autorisé (par exemple votre concurrent).|
|Contrôle partagé|Certificats numériques partagés (extensions de fichier)|Alerte quand un fichier contenant des certificats numériques est partagé publiquement. Utilisez ce modèle afin de régir votre stockage AWS.|
|Contrôle partagé|Compartiments S3 accessibles publiquement (AWS)|Alerte quand un compartiment AWS S3 est publiquement partagé.|
|Contrôle partagé|Fichiers obsolètes partagés en externe|Alerte lorsque des fichiers partagés en externe n’ont pas été modifiés depuis au moins 6 mois.|

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
