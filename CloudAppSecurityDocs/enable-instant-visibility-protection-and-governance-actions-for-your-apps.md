---
title: Connectez les applications pour bénéficier d’une visibilité et d’un contrôle Cloud App Security | Microsoft Docs
description: Cet article décrit le processus de connexion des applications avec des connecteurs d’API à des applications dans le Cloud de votre organisation.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/12/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 0aa55a99017a1768bf58fd2c2a40688c1a5c95e6
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285343"
---
# <a name="connect-apps"></a>Connecter des applications

*S’applique à : Microsoft Cloud App Security*

Les connecteurs d’application utilisent les API des fournisseurs d’applications pour permettre une meilleure visibilité et un meilleur contrôle des Microsoft Cloud App Security sur les applications auxquelles vous vous connectez.

Microsoft Cloud App Security tire parti des API fournies par le fournisseur de Cloud. Chaque service a ses propres infrastructure et limitations d’API, telles que la limitation, les limites d’API, les fenêtres d’API de décalage temporel dynamique, etc. Microsoft Cloud App Security collaboré avec les services pour optimiser l’utilisation des API et offrir des performances optimales. Compte tenu des différents services de limitations imposés aux API, les moteurs Cloud App Security utilisent la capacité autorisée. Certaines opérations, telles que l’analyse de tous les fichiers du locataire, nécessitent de nombreuses API pour qu’elles soient réparties sur une période plus longue. Il est normal que certaines stratégies s’exécutent pendant plusieurs heures ou jours.

## <a name="multi-instance-support"></a>Prise en charge de plusieurs instances

Cloud App Security prend en charge plusieurs instances de la même application connectée. Par exemple, si vous avez plusieurs instances de Salesforce (une pour les ventes, une pour le marketing), vous pouvez connecter les deux à Cloud App Security. Vous pouvez gérer les différentes instances à partir de la même console pour créer des stratégies granulaires et des investigations plus approfondies. Cette prise en charge s’applique uniquement aux applications connectées à l’API, pas aux applications Cloud découvertes ou aux applications connectées au proxy.

> [!NOTE]
> Multi-instance n’est pas pris en charge pour Office 365 et Azure.

## <a name="how-it-works"></a>Fonctionnement

Cloud App Security est déployé avec des privilèges d’administrateur système qui autorisent un accès complet à tous les objets de votre environnement.

Le flux de connecteur d’applications est le suivant :

1. Cloud App Security analyse et enregistre les autorisations d’authentification.
2. Cloud App Security demande la liste d’utilisateurs. La première fois que la demande est effectuée, l’analyse peut prendre un certain temps. Une fois l’analyse des utilisateurs terminée, Cloud App Security passe aux activités et aux fichiers. Dès que l’analyse démarre, certaines activités sont disponibles dans Cloud App Security.
3. À la fin de la demande de l’utilisateur, Cloud App Security analyse périodiquement les utilisateurs, les groupes, les activités et les fichiers. Toutes les activités sont disponibles après la première analyse complète.

Cette connexion peut prendre un certain temps en fonction de la taille du locataire, du nombre d’utilisateurs et de la taille et du nombre de fichiers qui doivent être analysés.

Selon l’application à laquelle vous vous connectez, la connexion d’API active les éléments suivants :

- **Informations de compte** : visibilité des utilisateurs, des comptes, des informations de profil, des groupes d’État (suspendus, actifs, désactivés) et des privilèges.

- Visibilité de la **piste d’audit** pour les activités de l’utilisateur, les activités d’administration, l’activité de connexion.

- **Analyse des données** : analyse des données non structurées à l’aide de deux processus : périodiquement (toutes les 12 heures) et dans une analyse en temps réel (déclenché chaque fois qu’une modification est détectée).

- **Autorisations d’application** : visibilité des jetons émis et de leurs autorisations.

- **Gouvernance des comptes** : possibilité de suspendre les utilisateurs, de révoquer des mots de passe, etc.

- **Gouvernance des données** : possibilité de mettre en quarantaine les fichiers, y compris les fichiers dans la corbeille, et de remplacer les fichiers.

- **Gouvernance des autorisations d’application** : possibilité de supprimer des jetons.

Le tableau suivant répertorie, par application cloud, les fonctionnalités prises en charge avec les connecteurs d’applications :

> [!div class="mx-tableFixed"]
>
> | | AWS | Box | Dropbox | GCP | G Suite | Office 365 | Okta | ServiceNow | Salesforce | WebEx | Workday |
> |-|-|-|-|-|-|-|-|-|-|-|-|
> | **Répertorier les comptes** | ✔ | ✔ | ✔ | Connexion de l’objet G suite | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
> | **Liste des groupes** | ✔ | ✔ | ✔ | Connexion de l’objet G suite | ✔ | ✔ | ✔ | ✔ | ✔ | | Non prise en charge par le fournisseur |
> | **Liste des privilèges** | | ✔ | ✔ | Connexion de l’objet G suite | ✔ | ✔ | Non prise en charge par le fournisseur | ✔ | ✔ | ✔ | Non pported par le fournisseur |
> | **Gouvernance des utilisateurs** | | ✔ | Bientôt disponible | Connexion de l’objet G suite | ✔ | ✔ | | Bientôt disponible | ✔ | Bientôt disponible | t pris en charge par le fournisseur |
> | **Activité de connexion** | ✔ | ✔ | ✔ | Connexion de l’objet G suite | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
> | **Activité de l’utilisateur** | Not applicable | ✔ | ✔ | ✔ | ✔-nécessite Google Business ou Enterprise | ✔ | ✔ | Partiel | Pris en charge avec lesforce Shield | ✔ | ✔ |
> | **Activité d’administration** | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | Partiel | ✔ | ✔ | Non prise en charge par le fournisseur |
> | **DLP-analyse périodique** | | ✔ | Bientôt disponible | Not applicable | ✔ | ✔ | Not applicable | | | | Non pris en charge par ovider |
> | **Analyse DLP en temps quasi réel** | | ✔ | ✔ | Not applicable | ✔-nécessite Google Business Enterprise | ✔ | Not applicable | ✔ | ✔ | ✔ | Non prise en charge par le fournisseur |
> | **Contrôle partagé** | ✔ | ✔ | ✔ | Not applicable | ✔ | ✔ | Not applicable | Not applicable | | ✔ | Non pris en charge par ovider |
> | **Gouvernance des fichiers** | ✔ | ✔ | ✔ | Not applicable | ✔ | ✔ | Not applicable | | ✔ | | Non prise en charge par le fournisseur |
> | **Voir les autorisations d’application** | Not applicable | Non prise en charge par le fournisseur | En provenance | Not applicable | ✔ | ✔ | Not applicable | | ✔ | Not applicable | Not applicable |
> | **Révoquer les autorisations d’application** | Not applicable | Non prise en charge par le fournisseur | Ming bientôt | Not applicable | ✔ | ✔ | Not applicable | | ✔ | Not applicable | Not applicable |
> | **Appliquer des étiquettes de Azure Information Protection** | Not applicable | ✔ | | Not applicable | ✔ | ✔ | Not applicable | | | Not applicable | Not applicable |

## <a name="prerequisites"></a>Composants requis

- Pour certaines applications, il peut être nécessaire de répertorier les adresses IP de façon blanche pour permettre Cloud App Security de collecter des journaux et de fournir un accès pour la console Cloud App Security. Pour plus d’informations, consultez [Configuration réseau requise](network-requirements.md).

- Pour chaque application à connecter avec l’intégration de l’API Cloud App Security, nous recommandons de créer un compte de service d’administration dédié à Cloud App Security.

> [!NOTE]
> Pour obtenir des mises à jour quand des URL et des adresses IP ont changé, abonnez-vous au flux RSS comme expliqué dans [URL et plages d’adresses IP Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).

Pour utiliser des connecteurs d’application, vous devez vous assurer que vous disposez des éléments suivants pour chaque application spécifique :

| Application | Type de licence | Utilisateur |
|-----|--------------|------|
| Azure | | Administrateur général |
| AWS | | Utilisateur récemment créé |
| Box | Enterprise | Il est fortement recommandé de vous connecter à Box en tant qu’administrateur. La connexion en tant que coadministrateur entraînera uniquement une visibilité partielle des données. Si vous vous connectez en tant que coadministrateur, veillez à sélectionner toutes les autorisations. |
| Dropbox | Business/Entreprises | Admin |
| GCP | | Consultez les [conditions préalables Connect GCP](connect-google-gcp-to-microsoft-cloud-app-security.md#prerequisites) |
| G Suite | G suite Business ou Enterprise préféré<br /><br />G Suite Enterprise (au minimum) | Super administrateur |
| Office 365 | | Administrateur général |
| Okta | Enterprise (pas la version d’essai) | Admin |
| Salesforce | | Admin |
| ServiceNow | Eureka et au-dessus | Rôle admin + RestAPI |
| WebEx | | Admin + conformité administrateur |
| Workday | | Consultez les [conditions préalables Connect](connect-workday-to-microsoft-cloud-app-security.md#prerequisites) de la journée de travail |

### <a name="expressroute"></a>ExpressRoute

Cloud App Security est déployé dans Azure et entièrement intégré à [ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/). Toutes les interactions avec les applications Cloud App Security et le trafic envoyé à Cloud App Security, y compris le chargement des journaux de découverte, sont acheminés via l' **homologation publique** ExpressRoute pour améliorer la latence, les performances et la sécurité. Aucune étape de configuration n’est nécessaire côté client.
Pour plus d’informations sur le peering public, consultez [Circuits ExpressRoute et domaines de routage](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/).

## <a name="next-steps"></a>Étapes suivantes :

> [!div class="nextstepaction"]
> [Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

## <a name="check-out-this-video"></a>Regardez cette vidéo !

> [!div class="nextstepaction"]
> [Microsoft Cloud App Security – API REST et jetons](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security--REST-APIs-and-Tokens)
