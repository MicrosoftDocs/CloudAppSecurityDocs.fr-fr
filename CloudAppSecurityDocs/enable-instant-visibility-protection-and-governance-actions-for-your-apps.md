---
title: Connecter des applications pour obtenir visibilité et contrôle – Cloud App Security | Microsoft Docs
description: Cet article décrit le processus de connexion d’applications à des applications dans le cloud de votre organisation avec des connecteurs d’API.
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: ShlomoSagir-MS
ms.date: 8/26/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 5d6b659fd25e17e2c3e4ac22749057a9e2ec70ac
ms.sourcegitcommit: 4179e4ad0fbabf08a24a176bbe21cad1f8cc35da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2019
ms.locfileid: "70019480"
---
# <a name="connect-apps"></a>Connecter des applications

*S’applique à : Microsoft Cloud App Security*

Les connecteurs d’applications utilisent les API des fournisseurs d’applications pour que Microsoft Cloud App Security bénéficie d’une plus grande visibilité et d’un plus grand contrôle sur les applications auxquelles vous vous connectez.

Microsoft Cloud App Security tire profit des API proposées par le fournisseur de cloud. Chaque service a ses propres limitations de framework et d’API, par exemple la limitation de requêtes, les limites d’API, les fenêtres d’API de décalage temporel dynamique, etc. Microsoft Cloud App Security utilise les services pour optimiser l’utilisation des API et fournir un niveau de performance optimal. Compte tenu des différentes limitations que les services imposent aux API, les moteurs Cloud App Security utilisent la capacité autorisée. Certaines opérations, par exemple l’analyse de tous les fichiers du locataire, nécessitent de nombreuses API et sont donc réparties sur une période plus longue. Il est normal que certaines stratégies s’exécutent pendant plusieurs heures ou jours.

## <a name="multi-instance-support"></a>Prise en charge de plusieurs instances

Cloud App Security prend en charge plusieurs instances de la même application connectée. Par exemple, si vous avez plusieurs instances de Salesforce (une pour les ventes, une pour le marketing), vous pouvez vous connecter à Cloud App Security. Vous pouvez gérer les différentes instances à partir de la même console pour créer des stratégies granulaires et mener une investigation plus approfondie. Cette prise en charge s’applique uniquement aux applications connectées à des API, pas aux applications découvertes dans le cloud ni aux applications connectées à des proxys.

> [!NOTE]
> Multi-instance n’est pas pris en charge pour Office 365 et Azure.

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
> ||**Office 365**|**Box**|**Okta**|**G Suite**|**ServiceNow**|**Salesforce**|**Dropbox**|**AWS**|**WebEx**|**Workday**|
> |-|-|-|-|-|-|-|-|-|-|-|
> |**Répertorier les comptes**|✔|✔|✔|✔|✔|✔|✔|✔|✔|✔|
> |**Groupe**|✔|✔|✔|✔|✔|✔|✔|✔|Non applicable|Non applicable|
> |**Privilèges**|✔|✔|Non prise en charge par le fournisseur|✔|✔|✔|✔||✔|Non applicable|
> |**Gouvernance des utilisateurs**|✔|✔||✔|Bientôt disponible|Bientôt disponible|Bientôt disponible||Bientôt disponible|Bientôt disponible|
> |**Activité de connexion**|✔|✔|✔|✔|✔|✔|✔|✔|✔|✔|
> |**Activité de l’utilisateur**|✔*|✔|✔|✔ - nécessite Google Business ou Entreprises|Partielle|Prise en charge avec Salesforce Shield|✔|Non applicable|✔|✔|
> |**Activité d’administration**|✔|✔|✔|✔|Partiel|✔|✔|✔|✔|✔|
> |**Analyse régulière des fichiers**|✔|✔|Non applicable|✔|✔|✔|✔|Non applicable|||
> |**Analyse des fichiers pratiquement en temps réel**|✔|✔|Non applicable|✔ - nécessite Google Business ou Entreprises|||Bientôt disponible||✔||
> |**Contrôle partagé**|✔|✔|Non applicable|✔|Non applicable||✔||✔||
> |**Quarantaine**|✔|✔|Non applicable|Bientôt disponible|||Bientôt disponible||Non applicable|Non applicable|
> |**Voir les autorisations d’application**|✔|Non prise en charge par le fournisseur|Non applicable|✔||✔|Non prise en charge par le fournisseur||Non applicable|Non applicable|
> |**Révoquer les autorisations d’application**|✔||Non applicable|✔||✔|Non applicable||Non applicable|Non applicable|
> |**Appliquer des étiquettes Azure Information Protection**|✔|✔||✔|||||Non applicable|Non applicable|

## <a name="prerequisites"></a>Prérequis

- Pour certaines applications, vous pouvez être amené à ajouter des adresses IP à la liste verte pour permettre à Cloud App Security de collecter les journaux et de fournir un accès pour la console Cloud App Security. Pour plus d’informations, consultez [Configuration requise pour le réseau](network-requirements.md).

- Pour chaque application à connecter avec l’intégration de l’API Cloud App Security, nous recommandons de créer un compte de service d’administration dédié à Cloud App Security.

> [!NOTE]
> Pour obtenir des mises à jour quand des URL et des adresses IP ont changé, abonnez-vous au flux RSS comme expliqué dans [URL et plages d’adresses IP Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).

Pour utiliser des connecteurs d’applications, vous devez vérifier que vous avez les éléments suivants pour chaque application concernée :

| Application | Type de licence | Utilisateur |
|-----|--------------|------|
| Azure | | Administrateur général |
| AWS | | Utilisateur récemment créé |
| Box | Enterprise | Il est fortement recommandé de vous connecter à Box en tant qu’administrateur. Une connexion en tant que coadministrateur entraîne une visibilité uniquement partielle des données. Si vous vous connectez en tant que coadministrateur, sélectionnez toutes les autorisations. |
| Dropbox | Business/Entreprises | Admin |
| G Suite | Compte G Suite Business ou Entreprise<br /><br /> G Suite Enterprise (au minimum) | Super administrateur |
| Office 365 | | Administrateur général |
| Okta | Enterprise (pas la version d’essai) | Admin |
| Salesforce | | Admin |
| ServiceNow | Eureka et au-dessus | Rôle admin + RestAPI |
| WebEx | | Admin + conformité administrateur |

<!--| Workday | | Admin |-->

### <a name="expressroute"></a>ExpressRoute

Cloud App Security est déployé dans Azure et entièrement intégré à [ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/). Toutes les interactions avec les applications Cloud App Security et le trafic envoyé vers Cloud App Security, notamment le chargement des journaux de découverte, sont acheminés via l’**homologation publique** ExpressRoute pour améliorer la latence, les performances et la sécurité. Aucune étape de configuration n’est nécessaire côté client.
Pour plus d’informations sur l’homologation publique, consultez [Circuits ExpressRoute et domaines de routage](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/).

## <a name="next-steps"></a>Étapes suivantes

[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)

## <a name="check-out-this-video"></a>Regardez cette vidéo !

[Microsoft Cloud App Security – API REST et jetons](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security--REST-APIs-and-Tokens)
