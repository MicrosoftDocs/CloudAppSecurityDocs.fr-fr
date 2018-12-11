---
title: Connecter des applications pour obtenir une visibilité et un contrôle complets avec Cloud App Security | Microsoft Docs
description: Cet article décrit le processus de connexion d’applications à des applications dans le cloud de votre organisation avec des connecteurs d’API.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/9/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 3b15ba46-ac9c-4b4f-aefc-137edc903bc1
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 1d6f5e998959abf670d282297b2d7ca61706610d
ms.sourcegitcommit: c497253a7ab63973bb806607e5f15dece91640be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53123990"
---
# <a name="connect-apps"></a>Connecter des applications 

*S’applique à : Microsoft Cloud App Security*

Les connecteurs d’applications utilisent les API des fournisseurs d’applications pour que Microsoft Cloud App Security bénéficie d’une plus grande visibilité et d’un plus grand contrôle sur les applications auxquelles vous vous connectez.  

Microsoft Cloud App Security tire profit des API proposées par le fournisseur de cloud. Chaque service a ses propres limitations de framework et d’API, par exemple la limitation de requêtes, les limites d’API, les fenêtres d’API de décalage temporel dynamique, etc. Microsoft Cloud App Security utilise les services pour optimiser l’utilisation des API et fournir un niveau de performance optimal. Compte tenu des différentes limitations que les services imposent aux API, les moteurs Cloud App Security utilisent la capacité autorisée. Certaines opérations, par exemple l’analyse de tous les fichiers du locataire, nécessitent de nombreuses API et sont donc réparties sur une période plus longue. Il est normal que certaines stratégies s’exécutent pendant plusieurs heures ou jours.  

## <a name="multi-instance-support"></a>Prise en charge de plusieurs instances

Cloud App Security prend en charge plusieurs instances de la même application connectée. Par exemple, si vous avez plusieurs instances de Salesforce (une pour les ventes, une pour le marketing), vous pouvez vous connecter à Cloud App Security. Vous pouvez gérer les différentes instances à partir de la même console pour créer des stratégies granulaires et mener une investigation plus approfondie. Cette prise en charge s’applique uniquement aux applications connectées à des API, pas aux applications découvertes dans le cloud ni aux applications connectées à des proxys.

## <a name="how-it-works"></a>Fonctionnement  
Cloud App Security est déployé avec des privilèges d’administrateur système qui autorisent un accès complet à tous les objets de votre environnement.  

Le flux de connecteur d’applications est le suivant :

1. Cloud App Security analyse et enregistre les autorisations d’authentification.
2. Cloud App Security demande la liste d’utilisateurs. La première fois que la demande est effectuée, l’analyse peut prendre un certain temps. Une fois l’analyse des utilisateurs terminée, Cloud App Security passe aux activités et aux fichiers. Dès que l’analyse démarre, certaines activités sont disponibles dans Cloud App Security.
3. Une fois la demande de liste d’utilisateurs effectuée, Cloud App Security analyse périodiquement les utilisateurs, les groupes, les activités et les fichiers. Toutes les activités sont disponibles après la première analyse complète.

Cette connexion peut prendre du temps, en fonction de la taille du locataire, du nombre d’utilisateurs ainsi que de la taille et du nombre de fichiers à analyser. 

Selon l’application à laquelle vous vous connectez, la connexion d’API active les éléments suivants :  

- **Informations sur le compte** - Visibilité des utilisateurs, des comptes, des informations de profil, de l’état (suspendu, actif, désactivé), des groupes et des privilèges.  

- **Piste d’audit** - Visibilité des activités des utilisateurs, des administrateurs et des connexions.  

- **Analyse de données** - Analyse des données non structurées à l’aide de deux processus : analyse périodique (toutes les 12 heures) et analyse en temps réel (déclenchée chaque fois qu’un changement est détecté).  

- **Autorisations d’applications** - Visibilité des jetons émis et de leurs autorisations.  

- **Gouvernance des comptes** - Suspension des utilisateurs, révocation des mots de passe, etc.  

- **Gouvernance des données** - Mise en quarantaine des fichiers, notamment les fichiers de la corbeille, et replacement des fichiers.  

- **Gouvernance des autorisations d’applications** - Suppression de jetons.  

Le tableau suivant répertorie, par application cloud, les fonctionnalités prises en charge avec les connecteurs d’applications :  

> [!div class="mx-tableFixed"]
> 
> ||**Office 365**|**Box**|**Okta**|**G Suite**|**ServiceNow**|**Salesforce**|**Dropbox**|**AWS**|  
> |-|-|-|-|-|-|-|-|-|  
> |**Répertorier les comptes**|✔|✔|✔|✔|✔|✔|✔|✔|  
> |**Groupe**|✔|✔|✔|✔|✔|✔|✔|✔|  
> |**Privilèges**|✔|✔|Non prise en charge par le fournisseur|✔|✔|✔|✔||  
> |**Gouvernance des utilisateurs**|✔|✔||✔|Bientôt disponible|Bientôt disponible|Bientôt disponible||  
> |**Activité de connexion**|✔|✔|✔|✔|✔|✔|✔|✔|  
> |**Activité de l’utilisateur**|✔*|✔|✔|✔ - nécessite Google illimité|Partiel|Prise en charge avec Salesforce Shield|✔|Non applicable|  
> |**Activité d’administration**|✔|✔|✔|✔|Partiel|✔|✔|✔|  
> |**Analyse régulière des fichiers**|✔|✔|Non applicable|✔|✔|✔|✔|Non applicable|  
> |**Analyse des fichiers pratiquement en temps réel**|✔|✔|Non applicable|✔ - nécessite Google illimité|||Bientôt disponible||  
> |**Contrôle partagé**|✔|✔|Non applicable|✔|Non applicable||✔||  
> |**Quarantaine**|✔|✔|Non applicable|Bientôt disponible|||Bientôt disponible||  
> |**Voir les autorisations d’application**|✔|Non prise en charge par le fournisseur|Non applicable|✔||✔|Non prise en charge par le fournisseur||  
> |**Révoquer les autorisations d’application**|✔||Non applicable|✔||✔|Non applicable||  
> |**Appliquer des étiquettes Azure Information Protection**|✔|✔||✔|||||  

## <a name="prerequisites"></a>Prérequis  

- Pour certaines applications, vous pouvez être amené à ajouter des adresses IP à la liste verte pour permettre à Cloud App Security de collecter les journaux et de fournir un accès pour la console Cloud App Security. Pour plus d’informations, consultez [Configuration requise pour le réseau](network-requirements.md).

- Pour chaque application à connecter avec l’intégration de l’API Cloud App Security, nous recommandons de créer un compte de service d’administration dédié à Cloud App Security.  

> [!NOTE]  
>  Pour obtenir des mises à jour quand des URL et des adresses IP ont changé, abonnez-vous au flux RSS comme expliqué dans [URL et plages d’adresses IP Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).  

Pour utiliser des connecteurs d’applications, vous devez vérifier que vous avez les éléments suivants pour chaque application concernée :  

|Application|Type de licence|Utilisateur|  
|---------|------------------|----------|  
|Box|Enterprise|Il est fortement recommandé de vous connecter à Box en tant qu’administrateur. Une connexion en tant que coadministrateur entraîne une visibilité uniquement partielle des données. Si vous vous connectez en tant que coadministrateur, sélectionnez toutes les autorisations.|  
|G Suite|G Suite Unlimited de préférence<br /><br /> G Suite Enterprise (au minimum)|Super administrateur|  
|Office 365||Administrateur général|  
|AWS||Utilisateur récemment créé|  
|Dropbox|Business/Entreprises|Administrateur|  
|Okta|Enterprise (pas la version d’essai)|Administrateur|  
|Exchange||Administrateur général|  
|ServiceNow|Eureka et au-dessus|Administrateur + rôle RestAPI|  
|Salesforce||Administrateur|  


**ExpressRoute**

Cloud App Security est déployé dans Azure et entièrement intégré à [ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/). Toutes les interactions avec les applications Cloud App Security et le trafic envoyé vers Cloud App Security, notamment le chargement des journaux de découverte, sont acheminés via l’**homologation publique** ExpressRoute pour améliorer la latence, les performances et la sécurité. Aucune étape de configuration n’est nécessaire côté client.  
Pour plus d’informations sur l’homologation publique, consultez [Circuits ExpressRoute et domaines de routage](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/).  

## <a name="next-steps"></a>Étapes suivantes
 
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)  

## <a name="check-out-this-video"></a>Regardez cette vidéo !

[Microsoft Cloud App Security – API REST et jetons](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security--REST-APIs-and-Tokens)  
