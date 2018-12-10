---
title: Connecter AWS à Cloud App Security pour la visibilité et le contrôle d’utilisation | Microsoft Docs
description: Cet article fournit des informations sur la connexion de votre application AWS à Cloud App Security à l’aide du connecteur d’API.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/13/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: a6b4c745-cd5c-4458-819c-80cbe8b25f29
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 3a8936a8a3f9a9e2198edbdec3111f1cccad0c90
ms.sourcegitcommit: 77850c6777504c2478611cb71a387e7fcc5f2551
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51597157"
---
# <a name="connect-aws-to-microsoft-cloud-app-security"></a>Connecter AWS à Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

Cet article fournit des instructions pour connecter Microsoft Cloud App Security à votre compte Amazon Web Services existant à l’aide des API de connecteur.  
  
## <a name="how-to-connect-amazon-web-services-to-cloud-app-security"></a>Comment connecter Amazon Web Services à Cloud App Security  
  
1.  Dans la [console Amazon Web Services](https://console.aws.amazon.com/), sous **Security, Identity & Compliance** (Sécurité, identité et conformité), cliquez sur **IAM**.  
  
     ![AWS, identité et accès](./media/aws-identity-and-access.png "AWS, identité et accès")  
  
2.  Cliquez sur l’onglet **Users** (Utilisateurs), puis sur **Add user** (Ajouter un utilisateur).  
  
     ![AWS, utilisateurs](./media/aws-users.png "AWS, utilisateurs")      
  
4.  À l’étape **Details** (Détails), indiquez un nouveau nom d’utilisateur pour Cloud App Security. Sous **Access type** (Type d’accès), veillez à sélectionner **Programmatic access** (Accès par programme) et cliquez sur **Next Permissions** (Autorisations suivantes).  

     ![créer un utilisateur dans AWS](./media/aws-create-user.png "Créer un utilisateur dans AWS")

5. Cliquez sur l’onglet JSON :

     ![AWS JSON](./media/aws-json.png "Onglet AWS JSON")

6. Collez le script suivant dans la zone fournie :

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
            "iam:Get*",
            "s3:ListAllMyBuckets",
            "s3:PutBucketAcl",
            "s3:GetBucketAcl",
            "s3:GetBucketLocation"
          ],  
          "Effect" : "Allow",  
          "Resource" : "*"  
        }  
      ]  
     }  
  
    ```  

     ![Code AWS](./media/aws-code.png "Code AWS")
    
6. Cliquez sur **Vérifier la stratégie**.

7. Spécifiez un **Nom** et cliquez sur **Créer une stratégie**.

     ![Nom de la stratégie AWS](./media/aws-create-policy.png "AWS : créer une stratégie")

9. De retour à l’écran **Add user** (Ajouter un utilisateur), actualisez la liste si nécessaire et sélectionnez l’utilisateur que vous avez créé, puis cliquez sur **Next Review** (Prochaine vérification).

   ![Vérifier la stratégie d’utilisateur dans AWS](./media/aws-review-user.png "Vérifier un utilisateur dans AWS")

10. Si tous les détails sont corrects, cliquez sur **Create user** (Créer un utilisateur).

    ![Autorisations des utilisateurs dans AWS](./media/aws-user-permissions.png "Vérifier les autorisations des utilisateurs dans AWS")

11. Quand vous obtenez le message de réussite, cliquez sur **Download .csv** (Télécharger .csv) pour enregistrer une copie des informations d’identification du nouvel utilisateur, car vous en aurez besoin ultérieurement.  

    ![Télécharger csv dans AWS](./media/aws-download-csv.png "Télécharger csv dans AWS")
  
10. Dans la console AWS, cliquez sur **Services** puis, sous **Management Tools** (Outils de gestion), cliquez sur **CloudTrail**.  
  
     ![AWS CloudTrail](./media/aws-cloudtrail.png "AWS CloudTrail")  
  
    Si vous n’avez pas encore utilisé CloudTrail, cliquez sur **Get Started** (Commencer) et configurez-le en indiquant un nom et en sélectionnant le compartiment S3 approprié, puis cliquez sur **Turn On** (Activer). Pour vérifier que vous disposez d’une couverture complète, affectez à **Apply to all regions** (Appliquer à toutes les régions) la valeur **Oui**.
  
       ![Activer CloudTrail dans AWS](./media/aws-turnon-cloudtrail.png "Activer CloudTrail dans AWS")
  
    Vous devez voir le nouveau nom CloudTrail dans la liste **Trails** (Pistes).
    
      ![Liste CloudTrail dans AWS](./media/aws-cloudtrail-list.png "Liste CloudTrail dans AWS")
  
11. Dans le portail Cloud App Security, cliquez sur **Examiner**, puis sur **Applications connectées**.  
  
12. Dans la page **Connecteurs d’application**, cliquez sur le signe plus (+), puis sur **Amazon Web Services**.  
  
     ![connecter AWS](./media/connect-aws.png "connecter AWS")  
  
13. Dans la fenêtre contextuelle, collez la **clé d’accès** et la **clé secrète** issues du fichier csv dans les champs appropriés, puis cliquez sur **Connect** (Connecter).  
   ![Connecter une application AWS](./media/aws-connect-app.png "Connecter une application AWS") 
  
14. Vérifiez la connexion en cliquant sur **Test API** (Tester l’API).  
  
     Le test peut prendre quelques minutes. Quand il est terminé, vous recevez une notification de réussite ou d’échec. Une fois que vous avez reçu une notification de réussite, cliquez sur **Terminé**.  
  
Après avoir connecté AWS, vous recevez les événements des 7 jours précédant la connexion. Si vous venez d’activer CloudTrail, vous recevez les événements à partir du moment où vous avez activé CloudTrail.
  
## <a name="next-steps"></a>Étapes suivantes  
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  