---
title: Déployer Cloud App Security
description: Ce démarrage rapide décrit le processus permettant d’opérationnaliser Cloud App Security afin que vous puissiez utiliser les applications cloud, les contrôler et obtenir des insights.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 04/15/2019
ms.topic: quickstart
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: cf040b18-93d1-41e8-a26a-647c56afb00f
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: adfd8b7371fae5dcc4c4ffdfe5d9be647a12b826
ms.sourcegitcommit: 9f0c562322394a3dfac7f1d84286e673276a28b1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65567782"
---
#  <a name="quickstart-get-started-with-microsoft-cloud-app-security"></a>Démarrage rapide : Bien démarrer avec Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

Ce démarrage rapide vous explique comment bien démarrer avec Cloud App Security. Microsoft Cloud App Security vous permet de tirer parti des avantages des applications cloud tout en conservant le contrôle des ressources d’entreprise. Il fonctionne en améliorant la visibilité de l’activité cloud et contribue à renforcer la protection des données d’entreprise. Dans cet article, nous vous guidons à travers les étapes à suivre pour configurer et utiliser Microsoft Cloud App Security.  

Votre organisation doit avoir une licence pour utiliser Cloud App Security. Pour plus d’informations, consultez la section [Comment acheter Cloud App Security](https://www.microsoft.com/cloud-platform/cloud-app-security) dans la page d’accueil de Cloud App Security.  

>[!NOTE]
>Vous n’avez pas besoin d’une licence Office 365 pour utiliser Cloud App Security.  

## <a name="prerequisites"></a>Prérequis  
  
- Votre organisation doit détenir une licence Cloud App Security pour pouvoir utiliser le produit. Pour plus d’informations, consultez la section [Comment acheter Cloud App Security](https://www.microsoft.com/cloud-platform/cloud-app-security) dans la page d’accueil de Cloud App Security.  
  
     Pour la prise en charge de l’activation client, consultez [Contacter le support Office 365 pour les entreprises - Aide de l’administrateur](https://support.office.com/article/Contact-Office-365-for-business-support-Admin-Help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b).  
- Une fois que vous avez une licence Cloud App Security, vous recevez un e-mail contenant des informations sur l’activation et un lien vers le portail Cloud App Security.  
  
- Pour configurer Cloud App Security, vous devez être Administrateur général, Administrateur de conformité ou Lecteur sécurité dans Azure Active Directory ou Office 365. Il est important de comprendre qu’un utilisateur auquel est attribué un rôle d’administrateur a les mêmes autorisations sur toutes les applications cloud auxquelles votre organisation s’est abonnée. Peu importe que vous attribuiez le rôle dans le centre d’administration Microsoft 365, dans le portail Azure Classic ou à l’aide du module Azure AD pour [Windows PowerShell](https://technet.microsoft.com/library/mt736914.aspx). Pour plus d’informations, consultez [Attribution de rôles d’administrateur dans Office 365](https://support.office.com/article/Assigning-admin-roles-in-Office-365-eac4d046-1afd-4f1a-85fc-8219c79e1504) et [Attribution de rôles d’administrateur dans Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-assign-admin-roles/).  
  
- Pour exécuter le portail Cloud App Security, utilisez Internet Explorer 11, Microsoft Edge (dernière version), Google Chrome (dernière version), Mozilla Firefox (dernière version) ou Apple Safari (dernière version).  

## <a name="to-access-the-portal"></a>Pour accéder au portail

Pour accéder au portail Cloud App Security, accédez à [https://portal.cloudappsecurity.com](https://portal.cloudappsecurity.com).  
Vous pouvez également accéder au portail via le **centre d’administration Microsoft 365** en cliquant sur l’icône Centres d’administration. ![Icône Centres d’administration O365](./media/o365-admin-centers-icon.png "Icône Centres d’administration O365"), puis sélectionnez **Cloud App Security**.  
  
![Accès à partir d’O365](./media/access-from-o365.png "Accès à partir d’O365")  
  



## <a name="step-1-set-instant-visibility-protection-and-governance-actions-for-your-appsenable-instant-visibility-protection-and-governance-actions-for-your-appsmd"></a>Étape 1. [Définissez une visibilité instantanée, une protection et des actions de gouvernance pour vos applications](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).
Tâche obligatoire : Connecter des applications

1. Dans la roue dentée des paramètres, sélectionnez **Connecteurs d’application**.
2. Cliquez sur le signe plus pour ajouter une application puis sélectionnez une application.
3. Suivez les étapes de configuration pour connecter l’application.

**Pourquoi connecter une application ?**
Après avoir connecté une application, vous pouvez obtenir une visibilité plus approfondie et ainsi examiner les activités, les fichiers et les comptes pour les applications de votre environnement cloud.


## <a name="step-2-control-cloud-apps-with-policiescontrol-cloud-apps-with-policiesmd"></a>Étape 2. [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md).
Tâche obligatoire : Créer des stratégies

**Pour créer des stratégies**

1. Accédez à **Contrôle** > **Modèles**.
2. Sélectionnez un modèle de stratégie dans la liste, puis choisissez (+) **Créer une stratégie**.
3. Personnalisez la stratégie (sélectionnez des filtres, des actions et d’autres paramètres), puis choisissez **Créer**.
4. Sous l’onglet **Stratégies**, choisissez la stratégie pour afficher les correspondances pertinentes (activités, fichiers, alertes).
 Conseil : Pour couvrir tous les scénarios de sécurité de votre environnement cloud, créez une stratégie pour chaque **catégorie de risque**.

**Comment les stratégies peuvent-elles aider votre organisation ?**
Vous pouvez utiliser des stratégies pour surveiller les tendances, identifier les menaces à la sécurité, et générer des alertes et des rapports personnalisés. Avec les stratégies, vous pouvez créer des actions de gouvernance, et définir une protection contre la perte de données et des contrôles sur les partages de fichiers.


## <a name="step-3-set-up-cloud-discoveryset-up-cloud-discoverymd"></a>Étape 3. [Configurer Cloud Discovery](set-up-cloud-discovery.md).

Tâche obligatoire : Activer Cloud App Security pour afficher votre utilisation d’applications cloud

1. [Effectuez une intégration à Microsoft Defender ATP](wdatp-integration.md) pour activer automatiquement Cloud App Security afin de superviser vos appareils Windows 10 à l’intérieur et à l’extérieur de votre entreprise.
2. Si vous utilisez [Zscaler, intégrez](zscaler-integration.md)-le à Cloud App Security.
3. Pour obtenir une couverture complète, créez un rapport Cloud Discovery continu.

   1. Dans la roue dentée des paramètres, sélectionnez **Paramètres Cloud Discovery**.
   2. Choisissez **Chargement automatique des journaux**.
   3. Sous l’onglet **Sources de données**, ajoutez vos sources.
   4. Sous l’onglet **Collecteurs de journaux**, configurez le collecteur de journaux.
 
**Pour créer un rapport d’instantané Cloud Discovery**

 Accédez à **Découvrir** > **Rapport d’instantané** et suivez les étapes indiquées.

**Pourquoi configurer les rapports Cloud Discovery ?**
Obtenir une visibilité sur l’informatique fantôme dans votre organisation est critique.
Une fois vos journaux analysés, vous pouvez facilement identifier les applications cloud utilisées, par quelles personnes et sur quels appareils.

## <a name="step-4-personalize-your-experiencemail-settingsmd"></a>Étape 4. [Personnaliser votre expérience](mail-settings.md).
Tâche recommandée : Ajouter les détails de votre organisation

**Pour entrer les paramètres d’e-mail**

1. Dans la roue dentée des paramètres, sélectionnez **Paramètres de messagerie**.
2. Sous **Identité de l’expéditeur de l’e-mail**, entrez vos adresses e-mail et votre nom d’affichage.
3. Sous **Conception de l’e-mail**, chargez le modèle d’e-mail de votre organisation.

**Pour définir des notifications d’administrateur**

1. Dans la barre de navigation, choisissez votre nom d’utilisateur, puis accédez à **Paramètres utilisateur**.
2. Sous **Notifications**, configurez les méthodes à définir pour les notifications système.
3. Choisissez **Enregistrer**.

**Pour personnaliser les métriques de score**

1. Dans la roue dentée des paramètres, sélectionnez **Paramètres Cloud Discovery**.
1. Dans la roue dentée des paramètres, sélectionnez **Paramètres Cloud Discovery**.
2. Sous **Métriques de score**, configurez l’importance des différentes valeurs de risque.
3. Choisissez **Enregistrer**.

Les scores de risque attribués aux applications découvertes sont maintenant configurés précisément selon les besoins et priorités de votre organisation.

**Pourquoi personnaliser votre environnement ?**
Certaines fonctionnalités sont plus efficaces quand elles sont adaptées à vos besoins. Offrez une meilleure expérience à vos utilisateurs avec vos propres modèles d’e-mail. Choisissez les notifications que vous recevez et personnalisez vos métriques de score de risque selon les préférences de votre organisation.


## <a name="step-5-organize-the-data-according-to-your-needsip-tagsmd"></a>Étape 5. [Organiser les données selon vos besoins](ip-tags.md).
Tâche recommandée : Configurer des paramètres importants

**Pour créer des étiquettes d’adresse IP**

1. Dans la roue dentée des paramètres, sélectionnez **Paramètres Cloud Discovery**.
1. Dans la roue dentée des paramètres, sélectionnez **Plages d’adresses IP**.
2. Cliquez sur le signe plus pour ajouter une plage d’adresses IP.
3. Entrez les **détails**, l’**emplacement**, les **étiquettes** et la **catégorie** de la plage d’adresses IP.
4. Choisissez **Créer**.

   Vous pouvez maintenant utiliser des étiquettes d’adresse IP quand vous créez des stratégies, et quand vous filtrez et créez des rapports continus.

**Pour créer des rapports continus**

1. Dans la roue dentée des paramètres, sélectionnez **Paramètres Cloud Discovery**.
2. Sous **Rapports continus**, choisissez **Créer un rapport**.
3. Suivez les étapes de configuration.
4. Choisissez **Créer**.

Vous pouvez maintenant afficher les données découvertes selon vos propres préférences, comme des divisions ou des plages d’adresses IP.

**Pour ajouter des domaines**

1. Dans la roue dentée des paramètres, sélectionnez **Paramètres**.
2. Sous **Détails de l’organisation**, ajoutez les domaines internes de votre organisation.
3. Choisissez **Enregistrer**.

**Pourquoi devez-vous configurer ces paramètres ?**
Ces paramètres permettent d’exercer un meilleur contrôle des fonctionnalités dans la console. Avec les étiquettes d’adresse IP, il est plus facile de créer des stratégies qui répondent à vos besoins, de filtrer avec précision les données, etc. Utilisez des vues de données pour regrouper vos données dans des catégories logiques.
  

## <a name="next-steps"></a>Étapes suivantes

Définir des stratégies [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md).    

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)   
