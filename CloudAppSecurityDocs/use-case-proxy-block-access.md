---
title: "Guide pratique pour bloquer l’accès aux applications cloud sur des appareils non gérés | Microsoft Docs"
description: "Cette rubrique décrit le scénario permettant de protéger votre organisation contre l’accès aux applications cloud sur des appareils non gérés."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/15/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 9aec9c6f-c9e2-4a4b-8b6a-2f8e4465ee3f
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: b12fabca53c6174fb674f9de260eadb2c1311775
ms.sourcegitcommit: 84f358a5dd0ab7f362dd3a2cf9999a6184fba856
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2017
---
# <a name="blocking-access-to-cloud-apps-from-unmanaged-devices"></a>Blocage de l’accès aux applications cloud sur des appareils non gérés

Dans le monde de l’entreprise, les scénarios BYOD sont très utiles pour les employés qui veulent utiliser leur téléphone personnel et leur tablette dans l’espace de travail. Toutefois, de nombreux administrateurs informatiques, conscients des menaces que cela engendre pour les données et le réseau de l’organisation, veulent pouvoir bloquer l’accès sur ces appareils non gérés à toutes les applications cloud de l’entreprise, ou seulement une partie. 

## <a name="how-does-cloud-app-security-detect-unmanaged-devices"></a>Comment Cloud App Security détecte les appareils non gérés ?
.

>[!NOTE]
> Ce cas de figure s’applique à .

## <a name="the-threat"></a>LA MENACE
Une responsable des ventes de votre organisation a un appareil géré qu’elle utilise régulièrement, mais elle veut parfois consulter un document dans Salesforce sur son téléphone mobile personnel. Le téléphone n’est pas géré par votre organisation, ce qui signifie qu’il peut être infecté par un virus ou un logiciel malveillant, ou qu’il n’est pas protégé par un mot de passe et que toute personne l’ayant en sa possession peut accéder à votre compte Salesforce.

## <a name="the-solution"></a>LA SOLUTION
Protégez votre organisation en surveillant l’utilisation des applications cloud dans Cloud App Security et en créant une stratégie d’accès pour régir et bloquer les activités provenant d’appareils non gérés.

## <a name="prerequisites"></a>Prérequis

[Déployer](proxy-deployment.md) le proxy Cloud App Security pour Salesforce.

## <a name="set-up-unmanaged-device-detection"></a>Configurer la détection d’appareils non gérés


## <a name="create-an-access-policy"></a>Créer une stratégie d’accès
Les stratégies d’accès vous permettent de surveiller les tentatives de connexion de vos utilisateurs à des applications cloud et, si nécessaire, de les empêcher d’accéder à ces applications.


1.  Dans la console, cliquez sur **Contrôle**, puis sur **Stratégies**.  
  
2.  Cliquez sur **Créer une stratégie** et sélectionnez **Stratégie d’accès**.  
  
3.  Donnez un nom et une description à votre stratégie, par exemple, **Bloquer l’accès à Salesforce à partir d’appareils non gérés**.  
  
3. Définissez une **Gravité de la stratégie**. Si Cloud App Security est défini pour vous envoyer des notifications en cas de correspondances de stratégie pour un niveau de gravité de stratégie spécifique, votre sélection détermine si les correspondances de cette stratégie déclenchent une notification.

4.  Vous pouvez laisser le paramètre **Catégorie** défini sur **Contrôle d’accès**.  
  
7. Sous **Source d’activité**, cliquez sur **Sélectionner des applications dans la liste ci-dessous** et sélectionnez **Salesforce**.

8. Dans la section des filtres d’activité, sélectionnez **Type d’appareil**, puis **différent de** et sélectionnez **Conforme**, **Joint à un domaine** et **Certificat client valide**.
  
10. À ce stade, sous **Actions** à effectuer quand la stratégie trouve une correspondance, sélectionnez :
    - Autoriser : Si vous sélectionnez Autoriser, les utilisateurs sont autorisés à télécharger les fichiers. 
    ou
    
 
 >[!WARNING]
 >Il est vivement recommandé de ne pas **Bloquer** les téléchargements avant la première exécution de la stratégie en mode **Autoriser** et de vérifier que les résultats sont conformes à ce que vous attendez. Une fois seulement après avoir déterminé que la stratégie ne bloque pas des personnes par erreur, vous pouvez la définir sur **Bloquer** les téléchargements.
 
 9. Définissez les alertes que vous voulez recevoir quand la stratégie trouve une correspondance. Vous pouvez définir une limite pour ne pas recevoir trop d’alertes et choisir de recevoir les alertes par e-mail ou SMS, ou les deux.

10. Pour afficher les correspondances de stratégie d’accès, cliquez sur **Contrôle**, puis sur **Stratégies**. Filtrez les résultats pour afficher uniquement les stratégies d’accès à l’aide du filtre **Type** en haut. Pour plus d’informations sur les correspondances pour chaque stratégie, cliquez sur une stratégie. Cliquez sur l’onglet **Historique** pour consulter un historique remontant jusqu’à 6 mois de correspondances de stratégie.     
  
## <a name="validate-your-policy"></a>Valider votre stratégie

1. Pour simuler une alerte, essayez de vous connecter à Salesforce sur un appareil non géré.
3. Accédez au rapport de stratégie. Une correspondance de stratégie d’accès doit apparaître rapidement. 
4. Vous pouvez cliquer sur la correspondance pour voir qui a tenté de se connecter dans Salesforce et à partir de quel appareil. 

## <a name="blocking-access"></a>Blocage de l’accès

Après avoir validé et affiné la stratégie, supprimez les faux positifs possibles qui peuvent avoir correspondu à votre stratégie. Effectuez ensuite les opérations suivantes : 

1. Quand une stratégie d’accès trouve une correspondance, vous pouvez y remédier en définissant des [actions de gouvernance](governance-actions.md) automatiques.

2. Pour ce faire, modifiez la stratégie créée ci-dessus et définissez les **Actions** sur **Bloquer** les téléchargements quand la stratégie trouve une correspondance. L’utilisateur n’est pas autorisé à accéder à Salesforce à partir d’un appareil non géré.
  
 
 ## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  