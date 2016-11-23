---
title: "Bien démarrer avec Cloud App Security | Documentation Microsoft"
description: "Cette rubrique décrit le processus pour rendre Cloud App Security opérationnel."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: cf040b18-93d1-41e8-a26a-647c56afb00f
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 224c7039ecb7200ad951774ac5fb76202543a35c
ms.openlocfilehash: 2e9307b5166566efa65f4766c0331c6aa15118e9


---

# <a name="getting-started-with-cloud-app-security"></a>Bien démarrer avec Cloud App Security
Cloud App Security vous permet de tirer parti des avantages des applications cloud, mais aussi de conserver le contrôle des ressources d’entreprise. Il fonctionne en améliorant la visibilité de l’activité cloud et contribue à renforcer la protection des données d’entreprise. Dans cette rubrique, nous vous guidons à travers les étapes permettant de configurer et d’utiliser Cloud App Security.  

Votre organisation doit avoir une licence pour utiliser Cloud App Security. Pour plus d’informations, consultez la section des ressources concernant les licences dans [Comment acheter Cloud App Security](https://www.microsoft.com/en-us/cloud-platform/cloud-app-security).  

>[!NOTE]
>Vous n’avez pas besoin d’une licence Office 365 pour utiliser Cloud App Security.  

## <a name="get-started-quickly-with-cloud-app-security"></a>Prendre rapidement en main Cloud App Security  

|Ce que vous devez faire|Tâche|Obligatoire ?|Procédure|Description|  
|-------------------------|----------|---------------|-------------|-----------------|  
|Étape 1. [Configurer Cloud Discovery](set-up-cloud-discovery.md).|Charger les journaux de trafic|Obligatoire|**Pour créer un rapport Cloud Discovery continu**<br /><br /> 1. Accédez à **Paramètres** > **Paramètres Cloud Discovery**.<br /><br /> 2. Choisissez **Charger les journaux automatiquement**.<br /><br /> 3. Sous l’onglet **Sources de données**, ajoutez vos sources.<br /><br /> 4. Sous l’onglet **Collecteurs de journaux**, configurez le collecteur de journaux.<br /><br /> **Pour créer un rapport d’instantané Cloud Discovery**<br /><br /> 1. Accédez à **Découvrir** > **Créer un rapport d’instantané** et suivez les étapes indiquées.|**Pourquoi configurer les rapports Cloud Discovery ?**<br /> Obtenir une visibilité sur l’informatique fantôme dans votre organisation est critique. <br />Une fois vos journaux analysés, vous pouvez facilement découvrir quelles applications cloud sont utilisées, par qui et sur quels appareils.|
|Étape 2. [Définissez une visibilité instantanée, une protection et des actions de gouvernance pour vos applications](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).|Connecter des applications|Obligatoire|1. Accédez à **Paramètres** > **Applications approuvées**.<br /><br /> 2. Choisissez **Connecter l’application** et sélectionnez une application.<br /><br /> 3. Suivez les étapes de configuration pour connecter l’application.|**Pourquoi connecter une application ?**<br />Après avoir connecté une application, vous pouvez obtenir une visibilité plus approfondie et ainsi examiner les activités, les fichiers et les comptes pour les applications de votre environnement cloud.|
|Étape 3. [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md).|Créer des stratégies|Obligatoire|**Pour créer des stratégies**<br /><br /> 1. Accédez à **Contrôle** > **Modèles**.<br /><br /> 2. Sélectionnez un modèle de stratégie dans la liste, puis choisissez (+) **Créer une stratégie**.<br /><br /> 3. Personnalisez la stratégie (sélectionnez des filtres, des actions et d’autres paramètres), puis choisissez **Créer**.<br /><br /> 4. Sous l’onglet **Stratégies**, choisissez la stratégie pour afficher les correspondances pertinentes (activités, fichiers, alertes).<br /><br /> Conseil : Pour couvrir tous les scénarios de sécurité de votre environnement cloud, créez une stratégie pour chaque **catégorie de risque**.|**Comment les stratégies peuvent-elles aider votre organisation ?**<br />Vous pouvez utiliser des stratégies pour surveiller les tendances, identifier les menaces à la sécurité, et générer des alertes et des rapports personnalisés. Avec les stratégies, vous pouvez créer des actions de gouvernance, et définir une protection contre la perte de données et des contrôles sur les partages de fichiers.|
|Étape 4. [Personnaliser votre expérience](general-setup.md#Adallom_mailsettings).|Ajouter les détails de votre organisation|Recommandé|**Pour entrer les paramètres d’e-mail**<br /><br /> 1. Accédez à **Paramètres** > **Paramètres de messagerie**.<br /><br /> 2. Sous **Identité de l’expéditeur de l’e-mail**, entrez vos adresses e-mail et votre nom d’affichage.<br /><br /> 3. Sous **Conception de l’e-mail**, chargez le modèle d’e-mail de votre organisation.<br /><br /> **Pour définir des notifications d’administrateur**<br /><br /> 1. Dans la barre de navigation, choisissez votre nom d’utilisateur, puis accédez à **Paramètres utilisateur**.<br /><br /> 2. Sous **Notifications**, configurez les méthodes à définir pour les notifications système.<br /><br /> 3. Choisissez **Enregistrer**.<br /><br /> **Pour personnaliser les métriques de score**<br /><br /> 1. Accédez à **Paramètres** > **Paramètres Cloud Discovery**.<br /><br /> 2. Sous **Configurer la métrique du score**, configurez l’importance des différentes valeurs de risque.<br /><br /> 3. Choisissez **Enregistrer**.<br /><br /> Les scores de risque attribués aux applications découvertes sont maintenant configurés précisément selon les besoins et priorités de votre organisation.|**Pourquoi personnaliser votre environnement ?**<br />Certaines fonctionnalités fonctionnent mieux quand elles sont adaptées à vos besoins. <br />Améliorez l’expérience de vos utilisateurs avec vos propres modèles de message électronique, choisissez les notifications que vous recevez et personnalisez vos métriques de score de risque selon les préférences de votre organisation.|
|Étape 5. [Organiser les données selon vos besoins](general-setup.md#IPtagsandRanges).|Configurer des paramètres importants|Recommandé|**Pour créer des étiquettes d’adresse IP**<br /><br /> 1. Accédez à **Paramètres** > **Balises d’adresse IP**.<br /><br /> 2. Choisissez (+) **Ajouter une plage d’adresses IP**.<br /><br /> 3. Entrez les **détails**, l’**emplacement**, les **étiquettes** et la **catégorie** de la plage d’adresses IP.<br /><br /> 4. Choisissez **Créer**.<br /><br /> Vous pouvez maintenant utiliser des étiquettes d’adresse IP quand vous créez des stratégies, et quand vous filtrez et créez des vues de données.<br /><br /> **Pour créer des vues**<br /><br /> 1. Accédez à **Paramètres** > **Paramètres Cloud Discovery**.<br /><br /> 2. Sous **Vues de données**, cliquez sur (+) **Ajouter une vue de données**.<br /><br /> 3. Suivez les étapes de configuration.<br /><br /> 4. Choisissez **Créer**.<br /><br /> Vous pouvez maintenant afficher les données découvertes selon vos propres préférences, comme des divisions ou des plages d’adresses IP.<br /><br /> **Pour ajouter des domaines**<br /><br /> 1. Accédez à **Paramètres** > **Paramètres généraux**.<br /><br /> 2. Sous **Détails de l’organisation**, ajoutez les domaines internes de votre organisation.<br /><br /> 3. Choisissez **Enregistrer**.|**Pourquoi devez-vous configurer ces paramètres ?**<br />Ces paramètres permettent d’exercer un meilleur contrôle des fonctionnalités dans la console. Avec les étiquettes d’adresse IP, il est plus facile de créer des stratégies qui répondent à vos besoins, de filtrer avec précision les données, etc. Utilisez des vues de données pour regrouper vos données dans des catégories logiques.|  

## <a name="see-also"></a>Voir aussi

Découvrez les concepts de base dans [Bien démarrer avec Cloud App Security](getting-started-with-cloud-app-security.md).    
Pour obtenir du support technique, accédez à la page [Support assisté Cloud App Security](http://support.microsoft.com/oas/default.aspx?prid=16031).   
Les clients Premier peuvent également choisir Cloud App Security directement depuis le [portail Premier](https://premier.microsoft.com/).   



<!--HONumber=Nov16_HO3-->


