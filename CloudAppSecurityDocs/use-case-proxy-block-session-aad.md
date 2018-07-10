---
title: Comment bloquer les téléchargements de données sensibles sur des appareils non gérés à l’aide du Contrôle d’accès conditionnel aux applications de Cloud App Security | Microsoft Docs
description: Cette rubrique décrit le scénario permettant de protéger votre organisation contre les téléchargements de données sensibles sur des appareils non gérés en utilisant les fonctionnalités du proxy inversé Azure AD.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/18/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 06238ebc-2088-4372-9412-96cceaf3b145
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 69da592808750b9c20e3615f935f6a0570b6afd4
ms.sourcegitcommit: 9d2a34a2d4145b39d855dd6f596c0fc858b92f9b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37339986"
---
*S’applique à : Microsoft Cloud App Security*



# <a name="blocking-downloads-of-sensitive-information-using-microsoft-cloud-app-security-conditional-access-app-control"></a>Blocage des téléchargements d’informations sensibles avec le Contrôle d’accès conditionnel aux applications Microsoft Cloud App Security

>[!div class="step-by-step"]
[« PRÉCÉDENT : Guide pratique pour créer une stratégie d’accès](access-policy-aad.md)

Aujourd’hui, l’administration informatique est prise entre deux feux : d’un côté, vous avez besoin que vos employés soient productifs. Ce qui implique de les autoriser à accéder à des applications pour qu’ils puissent travailler à tout moment, depuis n’importe quel appareil. De l’autre, vous devez protéger les ressources de l’entreprise, notamment les informations propriétaires et privilégiées. Comment permettre à vos employés d’accéder à vos applications cloud tout en protégeant vos données ? **Ce cas d’usage vous permet de bloquer les téléchargements effectués par des utilisateurs qui ont accès à vos données sensibles dans des applications cloud d’entreprise depuis des appareils non gérés ou des emplacements réseau hors entreprise.**


## <a name="the-threat"></a>La menace
Un responsable de compte de votre organisation veut vérifier une information dans Salesforce de chez lui pendant le weekend, sur son ordinateur portable personnel. Les données Salesforce peuvent inclure des informations personnelles sur vos clients ou leurs numéros de carte de crédit. L’ordinateur personnel n’est pas géré, ce qui signifie que s’il télécharge des documents de Salesforce sur son ordinateur, il peut être infecté par un logiciel malveillant ou, si l’ordinateur est perdu ou volé et qu’il n’est pas protégé par mot de passe, n’importe qui en sa possession a accès à des informations sensibles. 

## <a name="the-solution"></a>La solution
Protégez votre organisation en surveillant et en contrôlant l’utilisation des applications cloud à l’aide de l’accès conditionnel Azure AD et du Contrôle d’accès conditionnel aux applications de Cloud App Security.  

## <a name="prerequisites"></a>Prérequis

- Une licence valide pour Azure AD Premium P1
- Configurer une application cloud pour l’authentification unique dans Azure AD  
- Vérifier que l’[application est déployée sur Cloud App Security](proxy-deployment-aad.md)

## <a name="create-a-block-download-policy-for-unmanaged-devices"></a>Créer une stratégie de blocage de téléchargement pour les appareils non gérés  

Les stratégies de session Cloud App Security vous permettent de restreindre davantage une session en fonction de l’état de l’appareil. Quand vous voulez contrôler une session en utilisant son appareil comme condition, vous devez créer à la fois une stratégie d’accès conditionnel ET une stratégie de session pour y parvenir.  

### <a name="step-1-create-an-azure-ad-conditional-access-policy"></a>Étape 1 : Créer une stratégie d’accès conditionnel Azure AD

1. Créez une stratégie d’accès conditionnel Azure AD avec des utilisateurs et une application affectés.
2. Sélectionnez **Utiliser les restrictions appliquées au Contrôle d’accès conditionnel aux applications** sous les contrôles de session dans la stratégie d’accès conditionnel.   

Une fois cette tâche terminée, accédez au portail Cloud App Security et créez une stratégie de session pour surveiller et contrôler les téléchargements de fichiers dans la session.

### <a name="step-2-create-a-session-policy"></a>Étape 2 : Créer une stratégie de session

1. Dans le portail Cloud App Security, sélectionnez **Contrôle**, puis **Stratégies**. 

2. Dans la page **Stratégies**, cliquez sur **Créer une stratégie**, puis sur **Stratégie de session**.
 
3. Dans la page **Créer une stratégie de session**, donnez à votre stratégie un nom et une description. Par exemple, **Bloquer les téléchargements depuis Salesforce pour les appareils non gérés**.

4. Affectez une **gravité de la stratégie** et une **catégorie**.

5. Sous **Type de contrôle de session**, sélectionnez **Contrôler le téléchargement du fichier (avec DLP)**. Cela vous permet de surveiller tout ce que font vos utilisateurs dans une session Salesforce, et de bloquer et protéger les téléchargements en temps réel.

6. Sous **Source de l’activité** dans la section **Activités remplissant toutes les conditions suivantes**, sélectionnez les filtres : 
    
   - **Balise de l’appareil** : Sélectionnez **Est différent de**, puis sélectionnez **Conforme**, **Joint à un domaine** ou **Certificat client valide**, en fonction de la méthode utilisée dans votre organisation pour identifier les appareils gérés. 
    
   - **Application** : Sélectionnez l’application à contrôler.  

   - **Utilisateurs** : Sélectionnez les utilisateurs à surveiller.  
    
7. Autrement, si vous voulez bloquer les téléchargements pour les emplacements qui ne font pas partie de votre réseau d’entreprise, sous **Source de l’activité** dans la section **Activités remplissant toutes les conditions suivantes**, définissez les filtres suivants : 

   - **Adresse IP** ou **Emplacement** : Vous pouvez utiliser l’un ou l’autre de ces deux paramètres pour identifier les emplacements hors entreprise ou inconnus, à partir desquels un utilisateur peut essayer d’accéder à des données sensibles.

     > [!NOTE]
     > Si vous voulez bloquer les téléchargements depuis À LA FOIS les appareils non gérés et les emplacements hors entreprise, vous devez créer deux stratégies de session, une qui définit la **source de l’activité** à l’aide de l’emplacement et une qui définit la **source de l’activité** sur les appareils non gérés.
 
   - **Application** : Sélectionnez l’application à contrôler.    
   
   - **Utilisateurs** : Sélectionnez les utilisateurs à surveiller.  

8. Sous **Source de l’activité** dans la section **Fichiers remplissant toutes les conditions suivantes**, sélectionnez les filtres suivants : 
   
   - **Étiquettes de classification** : pour utiliser des étiquettes de classification Azure Information Protection et filtrer les fichiers selon une étiquette de classification Azure Information Protection spécifique.
   
   - Sélectionnez **Nom de fichier** ou **Type de fichier** pour appliquer des restrictions en fonction de celles-ci.
9. Activez l’option **Inspection du contenu** pour permettre à la protection contre la perte de données (DLP) interne d’analyser vos fichiers pour en détecter le contenu sensible. 

10. Sous **Actions**, sélectionnez **Bloquer**. Personnalisez le message de blocage que vos utilisateurs reçoivent quand ils ne parviennent pas à télécharger des fichiers.  

11. Définissez les alertes que vous voulez recevoir quand la stratégie trouve une correspondance. Vous pouvez définir une limite pour ne pas recevoir trop d’alertes et choisir de recevoir les alertes par e-mail, par SMS, ou les deux.

12. Cliquez sur **Créer**.  
 

## <a name="validate-your-policy"></a>Valider votre stratégie 

1. Pour simuler le blocage du téléchargement de fichiers, depuis un appareil non géré ou un emplacement réseau hors entreprise, connectez-vous à l’application et essayez de télécharger un fichier. 

2. Ce fichier doit être bloqué et vous devez recevoir le message que vous avez défini sous **Personnaliser les messages de blocage**. 

3. Dans le portail Cloud App Security, cliquez sur **Contrôle**, puis sur **Stratégies** et cliquez sur la stratégie que vous avez créée pour afficher le rapport de stratégie. Une correspondance de stratégie de session doit apparaître rapidement. 

4. Dans le rapport de stratégie, vous pouvez voir quelles connexions ont été redirigées vers Microsoft Cloud App Security à des fins de contrôle de session et quels fichiers ont été téléchargés ou bloqués depuis les sessions surveillées.


>[!div class="step-by-step"]
[« PRÉCÉDENT : Guide pratique pour créer une stratégie d’accès](access-policy-aad.md)



## <a name="see-also"></a>Voir aussi  
[Créer une stratégie de session](session-policy-aad.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  