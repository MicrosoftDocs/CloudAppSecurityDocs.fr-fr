---
title: Connecter AWS | Documentation Microsoft
description: "Cette rubrique fournit des informations sur la connexion de votre application AWS à Cloud App Security à l’aide du connecteur API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: a6b4c745-cd5c-4458-819c-80cbe8b25f29
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6beb9041b338406fb5b16f4bd045dbdc4592c6d9
ms.openlocfilehash: a56257b7c149c3ea054f200ef88df0ab41b7e25b


---

# <a name="connect-aws-to-microsoft-cloud-app-security"></a>Connecter AWS à Microsoft Cloud App Security
Cette section fournit des instructions pour connecter Cloud App Security à votre compte Amazon Web Services existant à l’aide des API du connecteur.  
  
## <a name="how-to-connect-amazon-web-services-to-cloud-app-security"></a>Comment connecter Amazon Web Services à Cloud App Security  
  
1.  Dans la console Amazon Web Services, cliquez sur **Identity & Access Management (Gestion de l’identité et de l’accès)**.  
  
     ![aws, identité et accès](./media/aws-identity-and-access.png "aws identity and access")  
  
2.  Cliquez sur l’onglet **Users (Utilisateurs)**.  
  
     ![aws, utilisateurs](./media/aws-users.png "aws users")  
  
3.  Cliquez sur **Create New Users (Créer de nouveaux utilisateurs)**.  
  
     ![AWS, créer un utilisateur](./media/aws-create-user.png "AWS create user")  
  
4.  Créez un utilisateur pour Cloud App Security et vérifiez que la case **Generate an access key for each user (Générer une clé d’accès pour chaque utilisateur)** est cochée.  
  
5.  Cliquez sur **Download Credentials (Télécharger des informations d’identification)**.  
  
     ![aws, télécharger des informations d’identification](./media/aws-dl-cred.png "aws dl cred")  
  
6.  Sous l’onglet **Autorisations**, cliquez sur **Attach Policy** (Joindre la stratégie).  
  
     ![aws, joindre la stratégie utilisateur](./media/aws-attach-user-policy.png "aws attach user policy")  
  
7.  L’écran **Review Policy** (Vérifier la stratégie) s’affiche.
 
     ![vérifier la stratégie](./media/aws-review-policy.png "aws review policy")  
  

8. Sous **Nom de la stratégie**, tapez « AdallomTrustPolicy ». 
10. Sous **Policy Document** (Document de stratégie), copiez et collez les éléments suivants :  
  
    ```     
    {  
      "Version" : "2012-10-17",  
      "Statement" : [{  
          "Action" : [  
            "cloudtrail:DescribeTrails",  
  
           "cloudtrail:LookupEvents",  
            "cloudtrail:GetTrailStatus",  
            "cloudwatch:Describe*",  
            "cloudwatch:Get*",  
            "cloudwatch:List*",  
            "iam:List*",  
            "iam:Get*"  
          ],  
          "Effect" : "Allow",  
          "Resource" : "*"  
        }  
      ]  
     }  
  
    ```  
  
9. Dans le fichier téléchargé `credentials.csv`, trouvez les informations d’identification du nouvel utilisateur. Vous devrez les copier ultérieurement.  
  
10. Revenez à la page principale de la console AWS et dans le coin supérieur droit, choisissez votre région principale dans la fenêtre déroulante, puis cliquez sur **CloudTrail** dans le menu principal.  
  
     ![aws, cloudtrail](./media/aws-cloudtrail.png "aws cloudtrail")  
  
    1.  Si vous n’avez pas encore utilisé CloudTrail pour cette région, cliquez sur le bouton **Get Started (Commencer)** et configurez-le en sélectionnant le compartiment S3 approprié.  
  
         Cliquez sur l’onglet **Configuration** dans le coin supérieur gauche de l’écran. Sous **Additional configuration (Configuration supplémentaire)**, cliquez sur l’icône de modification.  
  
         ![aws, configuration de cloudtrail](./media/aws-cloudtrail-config.png "aws cloudtrail config")  
  
    2.  Cliquez sur **Yes (Oui)** quand vous êtes invité à **inclure des services globaux** et cliquez sur **Save (Enregistrer)**. Cela s’applique uniquement à la région que vous avez choisie.  
  
         ![aws, inclure des services globaux](./media/aws-include-global-svc.png "aws include global svc")  
  
    3.  Répétez l’étape 11 pour toutes les régions, mais sans inclure de services globaux.  
  
11. Dans le portail Cloud App Security, cliquez sur **Examiner**, puis sur **Applications connectées**.  
  
12. Dans la page **Connecteurs d’application**, cliquez sur le signe plus (+), puis sur **AWS**.  
  
     ![connecter AWS](./media/connect-aws.png "connect AWS")  
  
13. Dans la fenêtre contextuelle, collez la **clé d’accès** et la **clé secrète** issues du fichier CSV dans les champs de la page de l’API, puis cliquez sur **Mettre à jour la clé d’accès**.  
  
14. Vérifiez la connexion en cliquant sur **Test API** (Tester l’API).  
  
     Le test peut prendre quelques minutes. Lorsqu’il est terminé, vous recevez une notification de réussite ou d’échec. Une fois que vous avez reçu une notification de réussite, cliquez sur **Terminé**.  
  
Après avoir connecté AWS, vous recevrez les événements des 7 jours précédant la connexion.
  
## <a name="see-also"></a>Voir aussi  
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Nov16_HO5-->


