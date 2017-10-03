---
title: "Connecter Box à Cloud App Security pour la visibilité et le contrôle d’utilisation | Microsoft Docs"
description: "Cette rubrique fournit des informations sur la connexion de votre application Box à Cloud App Security à l’aide du connecteur API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 9/25/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: b3e4713e-986f-4a5e-9fcc-f8de94dd0df7
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 6c8b27ac5d148980463b68feded3667e1ebb19e1
ms.sourcegitcommit: 8759541301241e03784c5ac87b56986f22bd0561
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2017
---
# <a name="connect-box-to-microsoft-cloud-app-security"></a>Connecter Box à Microsoft Cloud App Security
Cette section fournit des instructions pour connecter Cloud App Security à votre compte Box existant à l’aide des API du connecteur d’applications.  
  
## <a name="how-to-connect-box-to-cloud-app-security"></a>Comment connecter Box à Cloud App Security  
  
> [!NOTE]  
>  Le déploiement avec un compte qui n’est pas un compte d’administrateur entraîne un échec du test de l’API et n’autorise pas Cloud App Security à analyser tous les fichiers inclus dans Box. S’il s’agit d’un problème pour vous, vous pouvez effectuer le déploiement avec un coadministrateur qui a tous les privilèges cochés, mais le test de l’API continuera d’échouer et les fichiers appartenant aux autres administrateurs dans Box ne seront pas analysés.  
  
1.  Si vous restreignez l’accès aux autorisations des applications, suivez cette étape. Sinon, passez à l’étape 2.  
  
    -   Dans la console d’administration Box, cliquez sur l’icône des paramètres suivie de **Business settings (Paramètres d’entreprise)**.  
  
         ![box, paramètres d’entreprise](./media/box-business-settings.png "box, paramètres d’entreprise")  
  
    -   Cliquez sur l’onglet **Applications**.  
  
         ![box, applications](./media/box-apps.png "box, applications")  
  
    -   Si l’option **Unpublished Applications** (Applications non publiées) est sélectionnée, dans la zone de texte **Except for** (À l’exception de), ajoutez le numéro de série de l’application Cloud App Security :<br></br>Centre de données US1 : `nduj1o3yavu30dii7e03c3n7p49cj2qh` <br></br>Centre de données EU1 : `me9cm6n7kr4mfz135yt0ab9f5k4ze8qp`<br></br>Cliquez ensuite sur **Enregistrer**. Pour savoir à quel centre de données Cloud App Security vous êtes connecté, consultez [Jetons d’API](api-tokens.md). 
  
         ![paramètres box, except for (à l’exception de)](./media/box-settings-except-for.png "paramètres box, except for (à l’exception de)")  
  
    > [!NOTE]  
    >  Si vous êtes un client Adallom existant et que votre URL de console concerne Adallom et non Cloud App Security, utilisez ce numéro de série d’application : bwahmilhdlpbqy2ongkl119o3lrkoshc.  
  
2.  Dans le portail Cloud App Security, cliquez sur **Examiner**, puis sur **Applications connectées**.  
  
3.  Dans la page **Connecteurs d’application**, cliquez sur le bouton plus (+), puis sélectionnez **Box**.  
  
     ![connecter box](./media/connect-box.png "connecter box")  
  
4.  Dans la fenêtre contextuelle **Paramètres Box**, cliquez sur **Suivez ce lien**.  
  
5.  La page de connexion à Box s’ouvre. Entrez vos informations d’identification pour autoriser Cloud App Security à accéder à l’application Box de votre équipe.  
  
6.  Box vous demande si vous voulez autoriser Cloud App Security à accéder aux informations de votre équipe, au journal d’activité et à effectuer des activités en tant que membre de l’équipe. Pour continuer, cliquez sur **Autoriser**.  
  
7.  De retour dans le portail Cloud App Security, vous devez recevoir un message indiquant que Box a été correctement connecté.  
  
8.  Vérifiez la connexion en cliquant sur **Test API** (Tester l’API).  
  
     Le test peut prendre quelques minutes. Une fois averti que la connexion a réussi, cliquez sur **Fermer**.  
  
Box est maintenant connecté à Cloud App Security.  
 
Après avoir connecté Box, vous recevrez les événements des 60 jours précédant la connexion.
  
Après la connexion de Box, Cloud App Security effectue une analyse complète. Selon le nombre de fichiers et d’utilisateurs, l’exécution de l’analyse complète peut prendre du temps. Pour activer l’analyse en quasi temps réel, les fichiers sur lesquels des activités sont détectées sont déplacés au début de la file d’attente d’analyse. Par exemple, un fichier qui est modifié, mis à jour ou partagé est analysé immédiatement au lieu d’attendre le processus d’analyse régulier. L’analyse en quasi temps réel ne s’applique pas aux fichiers qui ne sont pas modifiés de manière intrinsèque. Par exemple, les fichiers qui sont affichés, prévisualisés, imprimés ou exportés sont analysés dans le cadre de l’analyse planifiée régulièrement.
  
## <a name="see-also"></a>Voir aussi  
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   
[Pour obtenir du support technique, consultez la page Support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  