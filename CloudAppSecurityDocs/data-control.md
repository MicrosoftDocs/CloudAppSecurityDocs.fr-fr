---
title: "Vue d’ensemble du scénario de contrôle des données | Microsoft Docs"
description: "Cette rubrique décrit le scénario de contrôle des données dans votre environnement cloud."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/2/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 57927618-cb66-4c7f-afd7-c96926460816
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: e7e735519caa7da514f06db13afc737cf6ef1806
ms.sourcegitcommit: 661f4ce41262e8462c90fd2a4f1232e2154d5113
translationtype: HT
---
# <a name="controlling-and-protecting-your-files"></a>Contrôler et protéger vos fichiers  

Dans le monde professionnel d’aujourd’hui, dans lequel les données et les appareils prolifèrent, il est parfois difficile de suivre vos données à la trace et de savoir où elles sont et qui y a accès. Cloud App Security vous permet de prendre le contrôle de vos données en activant une protection des fichiers dans le cloud. Cloud App Security vous fournit les outils nécessaires pour créer des stratégies autour de ce que vous voulez ou non autoriser dans votre cloud d’entreprise. Cette solution vous offre un large éventail de processus automatisés : analyses continues de conformité, tâches d’eDiscovery légales, stratégies DLP pour le contenu sensible stocké dans le cloud ou partagé publiquement ou en externe, et bien d’autres cas d’usage encore.  
Cloud App Security peut surveiller n’importe quel type de fichier en fonction de plus de 20 filtres de métadonnées (par exemple, niveau d’accès, type de fichier). Pour plus d’informations, voir [Fichiers](file-filters.md). Voici deux exemples de menaces pesant sur les données auxquelles sont confrontées toutes les organisations, ainsi que la façon de protéger vos fichiers dans le cloud.
 
## <a name="files-that-contain-sensitive-data-are-being-shared-externally"></a>Des fichiers contenant des données sensibles sont partagés en externe 

Ce cas de figure s’applique à Office 365, G Suite, Box, Dropbox et Salesforce.

### <a name="the-threat"></a>LA MENACE
Les employés partagent en dehors de l’organisation des fichiers d’entreprise contenant des données sensibles. Cela peut occasionner des fuites de données, celles-ci échappant à toute surveillance. Il peut s’agir de fuites sans gravité qui n’enfreignent pas les stratégies de votre entreprise. Néanmoins, même dans ce cas, il est important de surveiller ce qui est partagé afin de toujours savoir comment votre réseau est utilisé et quelles données sont partagées en externe.

### <a name="the-solution"></a>LA SOLUTION
Obtenez une réelle visibilité sur le partage des fichiers dans votre réseau et mettez en place des actions de gouvernance. Pour cela, déployez Cloud App Security.

#### <a name="prerequisites"></a>Conditions préalables

[Connectez](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) au moins une application cloud à Cloud App Security.

#### <a name="setting-up-monitoring"></a>Configurer la surveillance

1.    Contrôler vos fichiers en créant une stratégie

    1. Sur la page **Stratégies**, cliquez sur [ **Créer une stratégie de fichier**](data-protection-policies.md). 
    ![créer une stratégie de fichier](./media/create-file-policy.png)

    2. Dans le champ [ **Modèle de stratégie** ](policy-template-reference.md), choisissez **Fichier contenant des informations d’identification personnelle (PII) détecté dans le cloud (moteur intégré de protection contre la perte de données (DLP))** et cliquez sur **Appliquer le modèle**. 
    ![modèle de stratégie de fichier](./media/file-policy-template.png)
    3. Pour surveiller le partage inapproprié de ces fichiers qui contiennent des informations confidentielles, ajoutez un filtre avec le niveau d’accès que vous voulez empêcher, par exemple, **Niveau d’accès est égal à Externe, Public, Public (Internet)**. 
     ![filtre de stratégie de fichier](./media/file-policy-filter.png)

2. Étudier les correspondances
    
    1. Dans la page **Stratégies**, cliquez sur le nom de la stratégie pour atteindre le **Rapport de stratégie**, puis passez en revue les correspondances qui ont été déclenchées.

    2. Pour examiner une correspondance, cliquez sur celle-ci et ouvrez le tiroir de fichier. Dans le tiroir, vous pouvez voir les autres stratégies auxquelles ce fichier correspond et l’état d’analyse du contenu, et si vous cliquez, vous pouvez voir les correspondances de contenu. Cliquez sur **Collaborateurs** pour afficher la liste des collaborateurs et voir si le fichier comporte des étiquettes de classification. Vous pouvez également jeter un coup d’œil au **chemin d’accès** pour voir où le fichier est enregistré et ainsi obtenir davantage de contexte sur le fichier lui-même.
    
    3. Si vous trouvez des faux positifs, marquez-les d’une coche pour les exclure du rapport et des correspondances. Vous pouvez utiliser la fonction de commentaires pour informer l’équipe Cloud App Security des améliorations que vous souhaitez ajouter. 


#### <a name="validating-your-policy"></a>Valider votre stratégie

1. Créer un document Word avec le texte suivant : 078-05-1120.
2. Ensuite, enregistrez le fichier sous *test file.docx* et partagez-le avec quelqu’un en dehors de votre domaine ou qui possède une URL publique. 
3. Accédez au rapport de stratégie. Une correspondance de stratégie de fichier devrait apparaître sous peu. 
4. Cliquez sur la correspondance pour afficher le contexte du fichier. La correspondance elle-même est masquée pour protéger les données sensibles. 

#### <a name="removing-the-risk"></a>Supprimer le risque

Après avoir validé et affiné la stratégie pour vous assurer qu’elle fonctionne comme prévu, procédez comme suit : 
  1. Vous pouvez engager immédiatement des [actions de gouvernance](governance-actions.md) en cliquant sur les trois points à la fin de la ligne et en sélectionnant l’action de gouvernance appropriée, par exemple, **Put user in quarantine (Placer l’utilisateur en quarantaine)**.

 ![gouvernance automatique externe](./media/auto-gov-external.png)

   2. Une fois la validation effectuée, vous pouvez définir des actions de gouvernance automatiques. Par exemple, dans SharePoint et OneDrive, vous pouvez **supprimer des utilisateurs externes** ou **placer l’utilisateur en quarantaine**, et dans G Suite et Box, vous pouvez **supprimer des utilisateurs externes** et **supprimer l’accès public**.

  ![appliquer des actions de gouvernance automatiques](./media/apply-automatic-gov-actions.png)

## <a name="files-shared-publicly-and-labeled-as-confidential"></a>Fichiers partagés publiquement et étiquetés comme confidentiels

Ce cas de figure s’applique à Office 365, G Suite, Box, Dropbox et Salesforce.

Il tire parti de l’intégration entre Cloud App Security et Azure Information Protection. Si vous exécutez Azure Information Protection au sein de votre organisation et si vous avez pris le temps d’apposer sur vos fichiers des étiquettes Azure Information Protection, Cloud App Security vous permet de surveiller et de contrôler ce qui arrivent à ces fichiers une fois étiquetés.

## <a name="the-threat"></a>LA MENACE

Vous savez que vous avez besoin de protéger vos données. Vous vous êtes déjà donné la peine de classifier vos fichiers dans Azure Information Protection. Mais une fois que vous les avez classifiés, comment savoir où ils sont et qui les consulte ? 

## <a name="the-solution"></a>LA SOLUTION
 Vous pouvez surveiller ces fichiers classifiés lorsqu’ils sont dans le cloud à l’aide de Cloud App Security. Cela vous permet de vous assurer que les données classifiées comme étant **confidentielles** (ou autrement sensibles) ne sont pas partagées de manière inappropriée. Cloud App Security permet de surveiller et de gérer les fichiers que vous avez classifiés dans Azure Information Protection en déployant la stratégie suivante et en effectuant les actions de gouvernant ci-après.

### <a name="prerequisites"></a>Conditions préalables

- [Connectez](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) au moins une application cloud à Cloud App Security.
- Suivez les instructions d’intégration [d’Azure Information Protection](azip-integration.md) pour activer l’analyse automatique.

### <a name="setting-up-monitoring"></a>Configurer la surveillance

1. Contrôler vos données en créant une stratégie    
    
    1. Sur la page **Stratégies**, cliquez sur [ **Créer une stratégie de fichier**](data-protection-policies.md). 

    2.    Dans la section filtre, vous pouvez supprimer les filtres correspondant au **niveau d’accès** et à la **dernière modification** pour exécuter cette stratégie sur tous les fichiers de votre cloud. Ces filtres s’appliquent uniquement aux fichiers modifiés à partir de maintenant. Ajoutez le filtre **Étiquette de classification**, puis **est égal à** et sélectionnez l’étiquette de classification de votre organisation. 
    
    ![étiquette de classification de stratégie de fichier](./media/file-policy-class-label.png)

    3.    Pour surveiller le partage inapproprié de ces fichiers classifiés, ajoutez un filtre avec le niveau d’accès que vous voulez empêcher, par exemple, **Niveau d’accès est égal à Public, Public (Internet)**.  Une fois que vous démarrez la stratégie, il faut du temps pour que Cloud App Security puisse analyser les fichiers existants ainsi que les nouveaux fichiers que vous ajoutez. Selon la quantité de données dont vous disposez dans le cloud, l’analyse peut être plus ou moins longue.

    ![filtre de stratégie de fichier public](./media/file-policy-filter-public.png)

2. Étudier les correspondances

    1. Cliquez sur le nom de la stratégie pour accéder au **Rapport de stratégie**, puis passez en revue les correspondances déclenchées.
    
    2. Pour examiner une correspondance, cliquez sur celle-ci et ouvrez le tiroir de fichier. Dans le tiroir, vous pouvez voir les étiquettes de classification qui ont été définies sur ce fichier et d’autres stratégies lui correspondant. Cliquez sur **Collaborateurs** pour afficher la liste des collaborateurs. Vous pouvez également jeter un coup d’œil au **chemin d’accès** pour voir où le fichier est enregistré et ainsi obtenir davantage de contexte sur le fichier lui-même.
      
    3. Si vous trouvez des faux positifs, marquez-les d’une coche pour les exclure du rapport et des correspondances. Vous pouvez utiliser la fonction de commentaires pour informer l’équipe Cloud App Security des améliorations que vous souhaitez ajouter. 


### <a name="validating-your-policy"></a>Valider votre stratégie

1. Créez un document Word et utilisez la barre d’outils Azure Information Protection pour définir une étiquette de sensibilité, par exemple **Confidentiel**. 

2. Téléchargez le fichier dans votre application cloud, puis partagez-le avec une URL publique. 

3. Accédez au **Rapport de stratégie**. Une correspondance de stratégie de fichier devrait apparaître sous peu. 

4. Vous pouvez voir l’étiquette de classification en cliquant sur le fichier et en ouvrant le **tiroir de fichier**. 


#### <a name="removing-the-risk"></a>Supprimer le risque

Après avoir validé et affiné la stratégie pour vous assurer qu’elle fonctionne comme prévu, procédez comme suit : 

1. Vous pouvez engager immédiatement des [actions de gouvernance](governance-actions.md) en cliquant sur les trois points à la fin de la ligne et en sélectionnant l’action de gouvernance appropriée, par exemple, **Put user in quarantine (Placer l’utilisateur en quarantaine)**.
    
2. Une fois la validation effectuée, vous pouvez définir des actions de gouvernance automatiques. Par exemple, dans SharePoint et OneDrive, vous pouvez **placer l’utilisateur en quarantaine**, et dans G Suite et Box, vous pouvez **supprimer l’accès public**.
 
 ![action de gouvernance automatique supprimer accès public](./media/gov-action-public-access.png)

## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  