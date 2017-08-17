---
title: "Guide pratique pour bloquer des téléchargements de données sensibles sur des appareils non gérés | Microsoft Docs"
description: "Cette rubrique décrit le scénario permettant de protéger votre organisation contre le téléchargement de données sensibles sur des appareils non gérés."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/15/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: d1861218-a16f-4058-bd0e-34cc4a9413d6
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 4936805c3777ce4ff82735637941cbe528315eb4
ms.sourcegitcommit: 84f358a5dd0ab7f362dd3a2cf9999a6184fba856
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2017
---
# <a name="blocking-downloads-on-unmanaged-devices"></a>Blocage des téléchargements sur les appareils non gérés

Les administrateurs informatiques d’aujourd’hui font face à un dilemme : d’un côté, les employés doivent être productifs, ce qui signifie qu’ils doivent avoir un accès en permanence et la possibilité de travailler sur n’importe quel appareil. De l’autre, vous devez protéger les ressources de l’entreprise, notamment les informations propriétaires et privilégiées. Comment permettre à vos employés d’accéder à vos applications cloud tout en protégeant vos données ? Le proxy Cloud App Security vous offre un contrôle général sur ce que vous autorisez et interdisez dans vos applications cloud. 

## <a name="how-does-cloud-app-security-detect-unmanaged-devices"></a>Comment Cloud App Security détecte les appareils non gérés ?
.

>[!NOTE]
> Ce cas de figure s’applique à .

## <a name="the-threat"></a>LA MENACE
Un responsable de compte de votre organisation veut vérifier une information dans Salesforce de chez lui pendant le weekend, sur son téléphone mobile personnel. Le compte comprend des informations susceptibles de contenir des informations de carte de crédit de clients ou des informations personnelles. Le téléphone n’est pas géré, ce qui signifie que s’il télécharge des documents de Salesforce sur son téléphone, il peut être infecté par un logiciel malveillant ou, si l’appareil est perdu ou volé et qu’il n’est pas protégé par mot de passe, n’importe qui en possession de l’appareil a accès à des informations sensibles.

## <a name="the-solution"></a>LA SOLUTION
Protégez votre organisation en surveillant l’utilisation des applications cloud dans Cloud App Security et en créant une stratégie proxy pour régir et bloquer les activités provenant d’appareils non gérés.

## <a name="prerequisites"></a>Prérequis

[Déployer](proxy-deployment.md) le proxy Cloud App Security pour Salesforce.

## <a name="set-up-unmanaged-device-detection"></a>Configurer la détection d’appareils non gérés


## <a name="create-a-session-policy"></a>Créer une stratégie de session
Les stratégies de session vous permettent de contrôler tout ce que fait l’utilisateur au sein d’une session et vous offrent des fonctionnalités de contrôle pour pouvoir bloquer et protéger le téléchargement de fichiers.


1.  Dans la console, cliquez sur **Contrôle**, puis sur **Stratégies**.  
  
2.  Cliquez sur **Créer une stratégie** et sélectionnez la **Stratégie de session**.  
  
3.  Donnez un nom et une description à votre stratégie, par exemple, **Bloquer les téléchargements SF sur les appareils non gérés**.  
  
3. Définissez une **Gravité de la stratégie**. Si Cloud App Security est défini pour vous envoyer des notifications en cas de correspondances de stratégie pour un niveau de gravité de stratégie spécifique, votre sélection détermine si les correspondances de cette stratégie déclenchent une notification.

4.  Vous pouvez laisser le paramètre **Catégorie** défini sur **DLP**.  
  
6. Sous **Type de contrôle de session**, sélectionnez **Surveiller toutes les activités et contrôler le téléchargement de fichiers**. Cela vous permet de surveiller tout ce que font vos utilisateurs dans une session Salesforce, et de bloquer et protéger les téléchargements en temps réel. Vous pouvez aussi filtrer le contenu du fichier à partir du DLP intégré à Cloud App Security ou d’un DLP externe.
 
7. Sous **Source d’activité**, cliquez sur **Sélectionner des applications dans la liste ci-dessous** et sélectionnez **Salesforce**.

8. Dans la section des filtres d’activité, sélectionnez **Type d’appareil**, puis **différent de** et sélectionnez **Conforme**, **Joint à un domaine** et **Certificat client valide**.
  
8. Définissez Cloud App Security pour reconnaître les fichiers et données que vous considérez comme privés :

    - Dans la section des filtres de fichier, sélectionnez vos fichiers confidentiels. Si vous utilisez Azure Information Protection, vous pouvez sélectionner **Étiquette de classification**, puis les étiquettes que vous utilisez pour les fichiers classifiés.
    
    -  Activez **Inspection du contenu** pour permettre au Cloud App Security interne de rechercher dans vos fichiers du contenu classifié, par exemple, vous pouvez sélectionner **Inclure les fichiers qui correspondent à une expression prédéfinie**, puis **Tous les pays : Finance : numéro de carte de crédit**.

10. À ce stade, sous **Actions** à effectuer quand la stratégie trouve une correspondance, sélectionnez :
    - Autoriser : Si vous sélectionnez Autoriser, les utilisateurs sont autorisés à télécharger les fichiers. 
    ou
    - Protéger : Si vous sélectionnez **Protéger**, l’utilisateur peut télécharger les fichiers, mais ils sont chiffrés avec Azure RMS. Vous pouvez également définir une action par défaut à effectuer si le chiffrement échoue (bloquer ou autoriser le téléchargement).
 
 >[!WARNING]
 >Il est vivement recommandé de ne pas **Bloquer** les téléchargements avant la première exécution de la stratégie en mode **Autoriser** et de vérifier que les résultats sont conformes à ce que vous attendez. Une fois seulement après avoir déterminé que la stratégie ne bloque pas des personnes par erreur, vous pouvez la définir sur **Bloquer** les téléchargements.
 
 9. Définissez les alertes que vous voulez recevoir quand la stratégie trouve une correspondance. Vous pouvez définir une limite pour ne pas recevoir trop d’alertes et choisir de recevoir les alertes par e-mail ou SMS, ou les deux.

10. Pour afficher les correspondances de stratégie de session, cliquez sur **Contrôle**, puis sur **Stratégies**. Filtrez les résultats pour afficher uniquement les stratégies de session à l’aide du filtre **Type** en haut. Pour plus d’informations sur les correspondances pour chaque stratégie, cliquez sur une stratégie. Cliquez sur l’onglet **Historique** pour consulter un historique remontant jusqu’à 6 mois de correspondances de stratégie.     
  
## <a name="validate-your-policy"></a>Valider votre stratégie

1. Pour simuler une alerte, connectez-vous à Salesforce à partir d’un appareil non géré et essayez de télécharger un fichier.
3. Accédez au rapport de stratégie. Une correspondance de stratégie de session doit apparaître rapidement. 
4. Vous pouvez cliquer sur la correspondance pour voir quels fichiers ont été téléchargés. La correspondance elle-même est masquée pour protéger les données sensibles. 

## <a name="blocking-and-protecting-your-sensitive-information"></a>Blocage et protection de vos informations sensibles

Après avoir validé et affiné la stratégie, supprimez les faux positifs possibles qui peuvent avoir correspondu à votre stratégie. Effectuez ensuite les opérations suivantes : 

1. Quand une stratégie de session trouve une correspondance, vous pouvez y remédier en définissant des [actions de gouvernance](governance-actions.md) automatiques.

2. Pour ce faire, modifiez la stratégie créée ci-dessus et définissez les **Actions** sur **Bloquer** les téléchargements quand la stratégie trouve une correspondance. L’utilisateur ne peut pas télécharger les fichiers et reçoit un message indiquant qu’il n’a pas l’autorisation de télécharger les fichiers.
  
 
 ## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  