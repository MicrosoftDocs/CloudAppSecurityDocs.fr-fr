---
title: "Activer la visibilité, la protection et des actions de gouvernance instantanées pour vos applications | Documentation Microsoft"
description: "Cette rubrique décrit le processus d’activation des connecteurs API sur les applications dans le cloud de votre organisation."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 3b15ba46-ac9c-4b4f-aefc-137edc903bc1
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 14de5a6b28c6593250a1a7827905fb0f8a6482b5
ms.openlocfilehash: 3ea2fbe78b943513a1b6ce483bc50ed5d79ae7c5


---

# <a name="enable-instant-visibility-protection-and-governance-actions-for-your-apps"></a>Voir, protéger et contrôler instantanément vos applications
Les connecteurs d’applications utilisent les API des fournisseurs d’applications pour que Cloud App Security bénéficie d’une plus grande visibilité et d’un plus grand contrôle sur les applications auxquelles vous vous connectez.  
  
Cloud App Security s’appuie sur les API données par le fournisseur de cloud, et chaque service a ses propres infrastructure et limitations d’API. Cloud App Security utilise les services pour optimiser l’utilisation des API et pour garantir des performances optimales. Compte tenu des différentes limitations qu’imposent les services aux API (telles que les limites d’API et les fenêtres d’API de décalage temporel dynamique), les moteurs Cloud App Security tirent parti de la capacité autorisée. Certaines opérations, comme l’analyse de tous les fichiers dans le client, nécessitent une grande quantité d’API et sont donc réparties sur une longue période. Il est normal que certaines stratégies s’exécutent pendant plusieurs heures ou jours.  
  
## <a name="how-it-works"></a>Fonctionnement  
Cloud App Security est déployé avec des privilèges d’administrateur système qui autorisent un accès complet à tous les objets de votre environnement.  
  
Le flux de connecteur d’applications est le suivant :
1. Cloud App Security analyse et enregistre les autorisations d’authentification.
2.  Cloud App Security demande la liste d’utilisateurs. La première fois que cette opération est effectuée, l’analyse peut prendre un certain temps. Une fois l’analyse des utilisateurs terminée, Cloud App Security passe aux activités et aux fichiers. Dès que l’analyse démarre, certaines activités sont disponibles dans Cloud App Security. 
4. Une fois la demande de liste d’utilisateurs effectuée, Cloud App Security analyse périodiquement les utilisateurs, les groupes, les activités et les fichiers. Toutes les activités sont disponibles après la première analyse complète. 
 
Cette analyse peut prendre du temps, en fonction de la taille du client, du nombre d’utilisateurs, et de la taille et du nombre de fichiers qui doivent être analysés. 
 
Selon l’application à laquelle vous vous connectez (voir le tableau ci-dessous), la connexion d’API présente les caractéristiques suivantes :  
  
-   **Informations de compte :**  
  
     Visibilité des utilisateurs, des comptes, des informations de profil, de l’état (suspendu, actif, désactivé), des groupes et des privilèges.  
  
-   **Piste d’audit :**  
  
     Visibilité des activités des utilisateurs, des administrateurs et des connexions.  
  
-   **Analyse de données :**  
  
     Analyse des données non structurées à l’aide de deux processus : analyse régulière (toutes les 12 heures) et analyse en temps réel (chaque fois qu’une modification est détectée).  
  
-   **Autorisations d’application :**  
  
     Visibilité des jetons émis et de leurs autorisations.  
  
-   **Gouvernance des comptes :**  
  
     Possibilité de suspendre les utilisateurs, de révoquer des mots de passe, etc.  
  
-   **Gouvernance des données :**  
  
     Possibilité de mettre des fichiers en quarantaine, y compris les fichiers dans la corbeille, et d’écraser des fichiers.  
  
-   **Gouvernance des autorisations d’application :**  
  
     Possibilité de supprimer des jetons.  
  
Le tableau suivant répertorie, par application cloud, les fonctionnalités prises en charge avec les connecteurs d’applications :  

||**Office 365**|**Box**|**Okta**|**Google Apps**|**ServiceNow**|**Salesforce**|**Dropbox**|**AWS**|  
|-|-|-|-|-|-|-|-|-|  
|**Répertorier les comptes**|✔|✔|✔|✔|✔|✔|✔|✔|  
|**Groupe**|✔|✔|✔|✔|✔|✔|✔|✔|  
|**Privilèges**|✔|✔|Non prise en charge par le fournisseur|✔|✔|✔|✔||  
|**Gouvernance des utilisateurs**|✔|✔||✔|Bientôt disponible|Bientôt disponible|Bientôt disponible||  
|**Activité de connexion**|✔|✔|✔|✔|✔|✔|✔|✔|  
|**Activité de l’utilisateur**|✔*|✔|✔|✔ - nécessite Google illimité|Partiel|Prise en charge avec Salesforce Shield|✔|Non applicable|  
|**Activité d’administration**|✔|✔|✔|✔|Partiel|✔|✔|✔|  
|**Analyse régulière des fichiers**|✔|✔|Non applicable|✔|✔|✔|✔|Bientôt disponible|  
|**Analyse des fichiers pratiquement en temps réel**|Bientôt disponible|✔|Non applicable|✔ - nécessite Google illimité|||Bientôt disponible||  
|**Contrôle partagé**|✔|✔|Non applicable|✔|Non applicable||✔||  
|**Quarantaine**|✔|✔|Non applicable|Bientôt disponible|||Bientôt disponible||  
|**Voir les autorisations d’application**|✔|Non prise en charge par le fournisseur|Non applicable|✔||✔|Non prise en charge par le fournisseur||  
|**Révoquer les autorisations d’application**|✔||Non applicable|✔||✔|Non applicable||  
  
\* Le connecteur d’applications Office 365 inclut une activité d’administration pour Exchange Online. Pour ajouter l’activité utilisateur pour Exchange Online, vous devez déployer le connecteur Exchange Online séparément.  
  
## <a name="prerequisites"></a>Conditions préalables  
Pour certaines applications, vous pouvez être amené à ajouter les adresses IP suivantes à la liste approuvée pour permettre à Cloud App Security de collecter les journaux et de fournir un accès pour la console Cloud App Security :  
  
-   Pour les journaux :  
  
     104.209.35.177  
  
     13.91.98.185  
  
-   Pour la console :  
  
     104.42.231.28  
  
> [!NOTE]  
>  Pour obtenir des mises à jour quand des URL et des adresses IP ont changé, abonnez-vous au flux RSS comme expliqué dans [URL et plages d’adresses IP Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).  
  
Pour utiliser des connecteurs d’applications, vous devez vérifier que vous avez les éléments suivants pour chaque application concernée :  
  
|Application|Type de licence|Utilisateur|  
|---------|------------------|----------|  
|Box|Enterprise|Il est fortement recommandé de vous connecter à Box en tant qu’administrateur. Une connexion en tant que coadministrateur entraînera une visibilité des données partielle seulement. Si vous vous connectez en tant que coadministrateur, veillez à sélectionner toutes les autorisations.|  
|Google Apps|Google Apps Unlimited de préférence<br /><br /> Google Apps Enterprise (au minimum)|Super administrateur|  
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
  
## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
   


<!--HONumber=Nov16_HO2-->


