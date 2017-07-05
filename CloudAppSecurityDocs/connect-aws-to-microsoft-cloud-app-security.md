---
title: "Connecter AWS à Cloud App Security pour la visibilité et le contrôle d’utilisation | Microsoft Docs"
description: "Cette rubrique fournit des informations sur la connexion de votre application AWS à Cloud App Security à l’aide du connecteur API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/19/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: a6b4c745-cd5c-4458-819c-80cbe8b25f29
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 68d4c221626706ca641a5d3e1986da543771561a
ms.sourcegitcommit: 2f4474084c7e07ac4853945ab5aa1ea78950675d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2017
---
# <a name="connect-aws-to-microsoft-cloud-app-security"></a>Connecter AWS à Microsoft Cloud App Security
Cette section fournit des instructions pour connecter Cloud App Security à votre compte Amazon Web Services existant à l’aide des API du connecteur.  
  
## <a name="how-to-connect-amazon-web-services-to-cloud-app-security"></a>Comment connecter Amazon Web Services à Cloud App Security  
  
1.  Dans la [console Amazon Web Services](https://console.aws.amazon.com/), sous **Security, Identity & Compliance** (Sécurité, identité et conformité), cliquez sur **IAM**.  
  
     ![aws, identité et accès](./media/aws-identity-and-access.png "aws, identité et accès")  
  
2.  Cliquez sur l’onglet **Users** (Utilisateurs), puis sur **Add user** (Ajouter un utilisateur).  
  
     ![aws, utilisateurs](./media/aws-users.png "aws, utilisateurs")      
  
4.  Dans l’étape **Details** (Détails), indiquez un nouveau nom d’utilisateur pour Cloud App Security et, sous **Access type** (Type d’accès), veillez à sélectionner **Programmatic access** (Accès par programmation) et à cliquer sur **Next Permissions** (Autorisations suivantes).  

     ![AWS, créer un utilisateur](./media/aws-create-user.png "AWS, créer un utilisateur")

5. Dans l’étape **Permissions** (Autorisations), sélectionnez **Attach existing policies directly** (Attacher directement les stratégies existantes), puis cliquez sur **Create policy** (Créer une stratégie).

   ![AWS, attacher un utilisateur](./media/aws-attach-user-policy.png "AWS, attacher une stratégie existante")

6.  Sous **Create policy** (Créer une stratégie), sélectionnez **Create Your Own Policy** (Créer votre propre stratégie).
 
    ![AWS, créer votre propre stratégie](./media/aws-create-own-policy.png "AWS, créer une stratégie")
 
7.  Sous **Review Policy** (Vérifier la stratégie), fournissez un **Policy Name** (Nom de la stratégie), par exemple CloudAppSecurityPolicy.

    ![AWS, vérifier la stratégie](./media/aws-review-policy.png "AWS, vérifier la stratégie")

8. Collez ensuite le code suivant dans le champ **Policy Document** (Document de stratégie) et cliquez sur **Create policy** (Créer une stratégie) :
  
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
  
9. De retour à l’écran **Add user** (Ajouter un utilisateur), actualisez la liste si nécessaire et sélectionnez l’utilisateur que vous venez de créer, puis cliquez sur **Next Review** (Prochaine vérification).

   ![AWS, vérifier la stratégie de l’utilisateur](./media/aws-review-user.png "AWS, vérifier l’utilisateur")

10. Si tous les détails sont corrects, cliquez sur **Create user** (Créer un utilisateur).

    ![AWS, autorisations des utilisateurs](./media/aws-user-permissions.png "AWS, vérifier les autorisations des utilisateurs")

11. Quand vous obtenez le message de réussite, cliquez sur **Download .csv** (Télécharger .csv) pour enregistrer une copie des informations d’identification du nouvel utilisateur, car vous en aurez besoin ultérieurement.  

    ![AWS, télécharger csv](./media/aws-download-csv.png "AWS, télécharger csv")
  
10. Dans la console AWS, cliquez sur **Services** puis, sous **Management Tools** (Outils de gestion), cliquez sur **CloudTrail**.  
  
     ![aws, cloudtrail](./media/aws-cloudtrail.png "aws, cloudtrail")  
  
    Si vous n’avez pas encore utilisé CloudTrail, cliquez sur **Get Started** (Commencer) et configurez-le en indiquant un nom et en sélectionnant le compartiment S3 approprié, puis cliquez sur **Turn On** (Activer). Pour vérifier que vous disposez d’une couverture complète, affectez à **Apply to all regions** (Appliquer à toutes les régions) la valeur **Oui**.
  
       ![AWS, activer CloudTrail](./media/aws-turnon-cloudtrail.png "AWS, activer CloudTrail")
  
    Vous devez voir le nouveau nom CloudTrail dans la liste **Trails** (Pistes).
    
      ![AWS, liste CloudTrail](./media/aws-cloudtrail-list.png "AWS, liste CloudTrail")
  
11. Dans le portail Cloud App Security, cliquez sur **Examiner**, puis sur **Applications connectées**.  
  
12. Dans la page **Connecteurs d’application**, cliquez sur le signe plus (+), puis sur **AWS**.  
  
     ![connecter AWS](./media/connect-aws.png "connecter AWS")  
  
13. Dans la fenêtre contextuelle, collez la **clé d’accès** et la **clé secrète** issues du fichier csv dans les champs appropriés, puis cliquez sur **Connect** (Connecter).  
   ![AWS, connecter l’application](./media/aws-connect-app.png "AWS connect app") 
  
14. Vérifiez la connexion en cliquant sur **Test API** (Tester l’API).  
  
     Le test peut prendre quelques minutes. Lorsqu’il est terminé, vous recevez une notification de réussite ou d’échec. Une fois que vous avez reçu une notification de réussite, cliquez sur **Terminé**.  
  
Après avoir connecté AWS, vous recevrez les événements des 7 jours précédant la connexion, sauf si vous venez d’activer CloudTrail, auquel cas vous recevrez les événements à partir du moment où vous avez activé CloudTrail.
  
## <a name="see-also"></a>Voir aussi  
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  