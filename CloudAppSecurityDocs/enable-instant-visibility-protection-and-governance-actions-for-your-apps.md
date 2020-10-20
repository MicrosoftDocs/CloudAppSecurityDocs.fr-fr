---
title: Connectez les applications pour bénéficier d’une visibilité et d’un contrôle Cloud App Security
description: Cet article décrit le processus de connexion d’applications à des applications dans le cloud de votre organisation avec des connecteurs d’API.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 07/14/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 729dec5de9bb349927e3cd60f331f61b31b65864
ms.sourcegitcommit: 812cb1e24ec18de2c4818970f3042ac06acea14c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92211998"
---
# <a name="connect-apps"></a>Connecter des applications

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Les connecteurs d’applications utilisent les API de fournisseurs d’applications pour que Microsoft Cloud App Security bénéficie d’une plus grande visibilité et d’un plus grand contrôle sur les applications auxquelles vous vous connectez.

Microsoft Cloud App Security tire profit des API proposées par le fournisseur de cloud. L’infrastructure et les API propres à chaque service ont des limitations, notamment en matière de bande passante, de limites d’API, de fenêtres d’API de décalage temporel dynamique, etc. Microsoft Cloud App Security utilise les services pour optimiser l’utilisation des API et fournir un niveau de performance optimal. Compte tenu des différentes limitations que les services imposent aux API, les moteurs Cloud App Security utilisent la capacité autorisée. Certaines opérations, par exemple l’analyse de tous les fichiers du locataire, nécessitent de nombreuses API et sont donc réparties sur une période plus longue. Il est normal que certaines stratégies s’exécutent pendant plusieurs heures ou jours.

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

- Visibilité de la **piste d’audit** pour les activités de l’utilisateur, les activités d’administration et les activités de connexion.

- **Analyse de données** - Analyse des données non structurées à l’aide de deux processus : analyse périodique (toutes les 12 heures) et analyse en temps réel (déclenchée chaque fois qu’un changement est détecté).

- **Autorisations d’applications** - Visibilité des jetons émis et de leurs autorisations.

- **Gouvernance des comptes** - Suspension des utilisateurs, révocation des mots de passe, etc.

- **Gouvernance des données** - Mise en quarantaine des fichiers, notamment les fichiers de la corbeille, et replacement des fichiers.

- **Gouvernance des autorisations d’applications** - Suppression de jetons.

Le tableau suivant répertorie, par application cloud, les fonctionnalités prises en charge avec les connecteurs d’applications :

| | AWS | Box | Dropbox | GCP | G Suite | Office 365 | Okta | ServiceNow | Salesforce | Webex | Workday |
|-|-|-|-|-|-|-|-|-|-|-|-|
| **Énumérer les comptes** | ✔ | ✔ | ✔ | Connexion de l’objet G suite | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
| **Liste des groupes** | ✔ | ✔ | ✔ | Connexion de l’objet G suite | ✔ | ✔ | ✔ | ✔ | ✔ | | Non prise en charge par le fournisseur |
| **Liste des privilèges** | | ✔ | ✔ | Connexion de l’objet G suite | ✔ | ✔ | Non prise en charge par le fournisseur | ✔ | ✔ | ✔ | Non prise en charge par le fournisseur |
| **Gouvernance des utilisateurs** | | ✔ | Bientôt disponible | Connexion de l’objet G suite | ✔ | ✔ | | Bientôt disponible | ✔ | Bientôt disponible | Non prise en charge par le fournisseur |
| **Activité de connexion** | ✔ | ✔ | ✔ | Connexion de l’objet G suite | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
| **Activité de l’utilisateur** | Non applicable | ✔ | ✔ | ✔ | ✔ - nécessite Google Business ou Entreprises | ✔ | ✔ | Partial | Prise en charge avec Salesforce Shield | ✔ | ✔ |
| **Activité d’administration** | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | Partial | ✔ | ✔ | Non prise en charge par le fournisseur |
| **DLP-analyse périodique** | | ✔ | ✔ | Non applicable | ✔ | ✔ | Non applicable | ✔ | ✔ | ✔ | Non prise en charge par le fournisseur |
| **DLP : analyse en temps quasi réel** | | ✔ | | Non applicable | ✔-nécessite Google Business Enterprise | ✔ | Non applicable | | | ✔ | Non prise en charge par le fournisseur |
| **Contrôle partagé** | ✔ | ✔ | ✔ | Non applicable | ✔ | ✔ | Non applicable | Non applicable | | ✔ | Non prise en charge par le fournisseur |
| **Gouvernance des fichiers** | ✔ | ✔ | ✔ | Non applicable | ✔ | ✔ | Non applicable | | ✔ | | Non prise en charge par le fournisseur |
| **Voir les autorisations d’application** | Non applicable | Non prise en charge par le fournisseur | En provenance | Non applicable | ✔ | ✔ | Non applicable | | ✔ | Non applicable | Non applicable |
| **Révoquer les autorisations d’application** | Non applicable | Non prise en charge par le fournisseur | Ming bientôt | Non applicable | ✔ | ✔ | Non applicable | | ✔ | Non applicable | Non applicable |
| **Appliquer des étiquettes Azure Information Protection** | Non applicable | ✔ | | Non applicable | ✔ | ✔ | Non applicable | | | Non applicable | Non applicable |

## <a name="prerequisites"></a>Prérequis

- Pour certaines applications, il peut être nécessaire d’autoriser les adresses IP de liste pour permettre à Cloud App Security de collecter des journaux et de fournir un accès pour la console Cloud App Security. Pour plus d’informations, consultez [Configuration exigée pour le réseau](network-requirements.md).

- Pour chaque application à connecter avec l’intégration de l’API Cloud App Security, nous recommandons de créer un compte de service d’administration dédié à Cloud App Security.

> [!NOTE]
> Pour obtenir des mises à jour quand des URL et des adresses IP ont changé, abonnez-vous au flux RSS comme expliqué dans [URL et plages d’adresses IP Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).

Pour utiliser des connecteurs d’applications, vous devez vérifier que vous avez les éléments suivants pour chaque application concernée :

| Application | Type de licence | Utilisateur |
|-----|--------------|------|
| Azure | | Administrateur général |
| AWS | | Utilisateur récemment créé |
| Box | Entreprise | Il est fortement recommandé de vous connecter à Box en tant qu’administrateur. Si vous vous connectez en tant que coadministrateur, vous obtiendrez uniquement une visibilité partielle des données. Si vous vous connectez en tant que coadministrateur, sélectionnez toutes les autorisations. |
| Dropbox | Business/Entreprises | Admin |
| GitHub | GitHub Enterprise Cloud | Propriétaire |
| GCP | | Consultez les [conditions préalables Connect GCP](connect-google-gcp-to-microsoft-cloud-app-security.md#prerequisites) |
| G Suite | Compte G Suite Business ou Entreprise<br /><br />G Suite Enterprise (au minimum) | Super administrateur |
| Office 365 | | Administrateur général |
| Okta | Enterprise (pas la version d’essai) | Admin |
| Salesforce | | Admin |
| ServiceNow | Eureka et au-dessus | Rôle admin + RestAPI |
| Webex | | Admin + conformité administrateur |
| Workday | | Consultez les [conditions préalables Connect](connect-workday-to-microsoft-cloud-app-security.md#prerequisites) de la journée de travail |

### <a name="expressroute"></a>ExpressRoute

Cloud App Security est déployé dans Azure et entièrement intégré à [ExpressRoute](/azure/expressroute/expressroute-introduction). Toutes les interactions avec les applications Cloud App Security et le trafic envoyé à Cloud App Security, y compris le chargement des journaux de découverte, sont acheminés via l' **homologation publique** ExpressRoute pour améliorer la latence, les performances et la sécurité. Aucune étape de configuration n’est nécessaire côté client.
Pour plus d’informations sur le peering public, consultez [Circuits ExpressRoute et domaines de routage](/azure/expressroute/expressroute-circuit-peerings).

## <a name="disable-app-connectors"></a>Désactiver les connecteurs d’application

> [!NOTE]
>
> - Avant de désactiver un connecteur d’applications, assurez-vous que les détails de connexion sont disponibles, car vous en aurez besoin si vous souhaitez réactiver le connecteur.
> - Ces étapes ne peuvent pas être utilisées pour désactiver le connecteur Azure.
> - Ces étapes ne peuvent pas être utilisées pour désactiver les applications de contrôle d’application par accès conditionnel et les applications de configuration de sécurité.

Pour désactiver les applications connectées :

1. Dans la page **applications connectées** , dans la ligne appropriée, cliquez sur les trois points et sélectionnez **désactiver le connecteur d’applications**.
1. Dans la fenêtre contextuelle, cliquez sur **désactiver l’instance App Connector** pour confirmer l’action.

Une fois désactivée, l’instance de connecteur cesse de consommer les données du connecteur.

## <a name="re-enable-app-connectors"></a>Réactiver les connecteurs d’application

Pour réactiver les applications connectées :

1. Dans la page **applications connectées** , dans la ligne appropriée, cliquez sur les trois points et sélectionnez **modifier l’application**. Cela démarre le processus pour ajouter un connecteur.
1. Ajoutez le connecteur à l’aide des étapes décrites dans le Guide du connecteur d’API approprié. Par exemple, si vous réactivez GitHub, suivez les étapes décrites dans [Connect GitHub Enterprise Cloud to Cloud App Security](connect-github-ec-to-microsoft-cloud-app-security.md).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]

## <a name="check-out-this-video"></a>Regardez cette vidéo !

> [!div class="nextstepaction"]
> [Microsoft Cloud App Security – API REST et jetons](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security--REST-APIs-and-Tokens)