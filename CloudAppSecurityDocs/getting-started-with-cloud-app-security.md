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
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: 8b454edde557c408b644c9bff6f7bf6136ba9819


---

# <a name="getting-started-with-cloud-app-security"></a>Bien démarrer avec Cloud App Security
Cloud App Security permet aux clients de tirer parti des avantages des applications cloud tout en conservant le contrôle grâce à une meilleure visibilité de l’activité et une protection accrue des données d’entreprise critiques.  Cette documentation vous présente progressivement les étapes suivantes pour vous permettre d’utiliser Cloud App Security.  
  
Votre organisation doit détenir une licence Cloud App Security pour pouvoir utiliser le produit. Pour plus d’informations, consultez [Comment acheter Cloud App Security](https://www.microsoft.com/server-cloud/products/cloud-app-security/default.aspx) et vérifiez les [ressources de gestion des licences](https://www.microsoft.com/server-cloud/products/cloud-app-security/default.aspx).  
  
>[!NOTE]
>Aucune licence Office 365 n’est nécessaire pour Cloud App Security.  
  
## <a name="get-started-quickly-with-cloud-app-security"></a>Prendre rapidement en main Cloud App Security  
  
|Ce que vous devez faire :|Tâche|Obligatoire ?|Procédure :|Description|  
|-------------------------|----------|---------------|-------------|-----------------|  
|ÉTAPE 1. [Configurer Cloud Discovery](set-up-cloud-discovery.md).|Charger les journaux de trafic|Obligatoire|**Créer un rapport Cloud Discovery continu**<br /><br /> 1.   Accédez à **Paramètres** -> **Paramètres Cloud Discovery**.<br /><br /> 2.    Cliquez sur **Upload log automatically (Charger automatiquement les journaux)**.<br /><br /> 3.   Ajoutez vos sources de données sous l’onglet **Sources de données**.<br /><br /> 4.    Configurez le collecteur de journaux sous l’onglet **Collecteurs de journaux**.<br /><br /> Créer un rapport d’instantané Cloud Discovery<br /><br /> 1.    Accédez à **Découvrir** -> **Créer un rapport de capture instantanée** et suivez les étapes|**Pourquoi configurer les rapports Cloud Discovery ?** Il est essentiel de rendre visible le Shadow IT pour votre organisation.  <br />Une fois que vos journaux sont analysés, vous pouvez facilement découvrir quelles applications cloud sont utilisées par quelles personnes, sur quels appareils.|  
|ÉTAPE 2. [Voir, protéger et contrôler instantanément vos applications](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).|Connecter des applications|Obligatoire|1.   Accédez à **Paramètres** -> **Applications approuvées**.<br /><br /> 2. Cliquez sur **Connecter l’application** et choisissez une application.<br /><br /> 3. Suivez les étapes de configuration pour connecter l’application.|**Pourquoi connecter une application ?**<br /><br /> La visibilité sera accrue uniquement après avoir connecté une application. Vous pourrez alors examiner les activités, les fichiers et les comptes dans votre environnement cloud pour vos applications cloud.|  
|ÉTAPE 3. [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md).|Créer des stratégies|Obligatoire|**Créer des stratégies**<br /><br /> 1.  Accédez à **Contrôle** -> **Modèles**.<br /><br /> 2.    Sélectionnez un modèle de stratégie dans la liste et cliquez sur (+) **Créer une stratégie**.<br /><br /> 3.  Personnalisez la stratégie selon vos besoins (sélectionnez les filtres, actions et autres configurations), puis cliquez sur **Créer**.<br /><br /> 4.    Sous l’onglet **Stratégies**, cliquez sur la stratégie que vous avez créée pour afficher les correspondances pertinentes (activités, fichiers, alertes, etc.).<br /><br /> Conseil : Créez une stratégie pour chaque **catégorie de risque** afin de couvrir tous les scénarios de sécurité de votre environnement cloud.|**Comment les stratégies peuvent-elles aider votre organisation ?**<br /><br /> Les stratégies vous fournissent les outils nécessaires pour analyser les tendances, identifier les menaces à la sécurité et générer des alertes et rapports personnalisés. Avec les stratégies, vous pouvez créer des actions de gouvernance, de protection contre la perte de données (DLP, Data Loss Prevention) et de contrôle des partages de fichiers.|  
|ÉTAPE 4. [Personnaliser votre expérience](general-setup.md#Adallom_mailsettings).|Ajouter les détails de votre organisation|Recommandé|**Entrer les paramètres de messagerie**<br /><br /> 1. Accédez à **Paramètres** -> **Paramètres de messagerie**.<br /><br /> 2.   Sous **Identité de l’expéditeur de l’e-mail**, entrez vos adresses de messagerie et votre nom d’affichage.<br /><br /> 3. Sous **Conception de l’e-mail**, chargez le modèle de message électronique de votre organisation.<br /><br /> **Définir des notifications d’administrateur**<br /><br /> 1.    Cliquez sur votre nom d’utilisateur dans la barre de navigation et accédez à **Paramètres utilisateur**.<br /><br /> 2.    Sous **Notifications**, configurez les méthodes à définir pour les notifications système.<br /><br /> 3.  Cliquez sur **Save**.<br /><br /> **Personnaliser les métriques de score**<br /><br /> 1.  Accédez à **Paramètres** -> **Paramètres Cloud Discovery**.<br /><br /> 2.    Sous **Configuration de la métrique du score**, configurez l’importance des diverses valeurs de risque.<br /><br /> 3.    Cliquez sur **Save**.<br /><br /> Les scores de risque attribués aux applications découvertes sont maintenant configurés précisément selon les besoins et priorités de votre organisation.|**Pourquoi personnaliser votre environnement ?**<br /><br /> Certaines fonctionnalités fonctionnent mieux quand elles sont adaptées à vos besoins.  <br />Améliorez l’expérience de vos utilisateurs avec vos propres modèles de message électronique, choisissez les notifications que vous recevez et personnalisez vos métriques de score de risque selon les préférences de votre organisation.|  
|ÉTAPE 5. [Organiser les données selon vos besoins](general-setup.md#IPtagsandRanges).|Configurer des paramètres importants|Recommandé|**Créer des balises d’adresse IP**<br /><br /> 1.   Accédez à **Paramètres** -> **Balises d’adresse IP**.<br /><br /> 2. Cliquez sur (+) **Ajouter une plage d’adresses IP**.<br /><br /> 3.    Entrez les **détails**, l’**emplacement**, les **balises** et la **catégorie** de la plage d’adresses IP.<br /><br /> 4. Cliquez sur **Create (Créer)**.<br /><br /> Vous pouvez désormais utiliser des balises IP lors de la création de stratégies, lors du filtrage et lors de la création de vues de données.<br /><br /> **Créer des vues**<br /><br /> 1.  Accédez à **Paramètres** -> **Paramètres Cloud Discovery**.<br /><br /> 2.    Sous **Data views** (Vues de données), cliquez sur (+) **Add data view** (Ajouter une vue de données).<br /><br /> 3.  Suivez les étapes de configuration.<br /><br /> 4.  Cliquez sur **Créer**.<br /><br /> Vous pouvez à présent afficher les données découvertes selon vos propres préférences telles que des unités commerciales ou des plages d’adresses IP.<br /><br /> **Ajouter des domaines**<br /><br /> 1.    Accédez à **Paramètres** -> **Paramètres généraux**.<br /><br /> 2.    Sous **Détails de l’organisation**, ajoutez les domaines internes de votre organisation.<br /><br /> 3. Cliquez sur **Save**.|**Pourquoi devez-vous configurer ces paramètres ?**<br /><br /> Ces paramètres améliorent et facilitent le contrôle de diverses fonctionnalités dans la console. Avec les balises d’adresse IP, il est plus facile de créer des stratégies qui répondent à vos besoins, de filtrer avec précision les données, etc. Utilisez des vues de données pour regrouper vos données dans des catégories logiques.|  
  
## <a name="see-also"></a>Voir aussi  
[Configuration générale](general-setup.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO4-->


