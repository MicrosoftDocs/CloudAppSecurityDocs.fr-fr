---
title: Se connecter Amazon Web Services avec Cloud App Security
description: Cet article vous explique comment connecter votre application AWS à Cloud App Security à l’aide du connecteur d’API, afin de bénéficier de plus de contrôle et de visibilité lors de l’utilisation.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 8/13/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: a6b4c745-cd5c-4458-819c-80cbe8b25f29
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 34e1c361d5b1a49093f927dfde1ae2391570b958
ms.sourcegitcommit: 8a49c166424fea83853b0a6895212367526abe78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083827"
---
# <a name="connect-aws-to-microsoft-cloud-app-security"></a>Connecter AWS à Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

Cet article fournit des instructions pour connecter votre compte Amazon Web Services (AWS) existant à Microsoft Cloud App Security à l’aide des API du connecteur.

Vous pouvez connecter l’un des deux AWS suivants au Cloud App Security connexions suivantes :

- **Audit de sécurité**: Cette connexion vous permet de bénéficier de plus de visibilité et de contrôle lors de l’utilisation de l’application AWS.
- **Configuration**de la sécurité : Cette connexion vous donne des recommandations de sécurité fondamentales basées sur la référence de la sécurité Internet (CIS) du Centre pour AWS.

Dans la mesure où vous pouvez ajouter une connexion ou les deux, les étapes décrites dans cet article sont écrites en tant qu’instructions indépendantes. Si vous avez déjà ajouté une des connexions, le cas échéant, modifiez les configurations existantes.

## <a name="how-to-connect-aws-security-auditing-to-cloud-app-security"></a>Comment connecter l’audit de sécurité AWS à Cloud App Security

1. Dans la [console Amazon Web services](https://console.aws.amazon.com/), sous **sécurité, identité & conformité**, cliquez sur **IAM**.

    ![AWS, identité et accès](media/aws-identity-and-access.png "AWS, identité et accès")

1. Sélectionnez **utilisateurs** , puis cliquez sur **Ajouter un utilisateur**.

    ![AWS, utilisateurs](media/aws-users.png "AWS, utilisateurs")

1. À l’étape **Details** (Détails), indiquez un nouveau nom d’utilisateur pour Cloud App Security. Assurez-vous que sous **type d’accès** , sélectionnez **accès par programme** , puis cliquez sur **autorisations suivantes**.<a name="set-permissions"></a>

    ![Créer un utilisateur dans AWS](media/aws-create-user.png "Créer un utilisateur dans AWS")

1. Cliquez sur l’onglet **JSON** :

    ![Onglet JSON AWS](media/aws-json.png "Onglet JSON AWS")

1. Collez le script suivant dans la zone fournie :

    ```json
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

     ![Code AWS](media/aws-code.png "Code AWS")

1. Cliquez sur **Vérifier la stratégie**.

1. Spécifiez un **Nom** et cliquez sur **Créer une stratégie**.

    ![Fournir le nom de la stratégie AWS](media/aws-create-policy.png "Fournir le nom de la stratégie AWS")

1. De retour à l’écran **Add user** (Ajouter un utilisateur), actualisez la liste si nécessaire et sélectionnez l’utilisateur que vous avez créé, puis cliquez sur **Next Review** (Prochaine vérification).

    ![Attacher une stratégie existante dans AWS](media/aws-attach-policy.png "Attacher une stratégie existante dans AWS")

1. Si tous les détails sont corrects, cliquez sur **Create user** (Créer un utilisateur).

    ![Autorisations des utilisateurs dans AWS](media/aws-user-permissions.png "Vérifier les autorisations des utilisateurs dans AWS")

1. Quand vous obtenez le message de réussite, cliquez sur **Download .csv** (Télécharger .csv) pour enregistrer une copie des informations d’identification du nouvel utilisateur, car vous en aurez besoin ultérieurement.

    ![Télécharger csv dans AWS](media/aws-download-csv.png "Télécharger csv dans AWS")

1. Dans la console AWS, cliquez sur **Services** puis, sous **Management Tools** (Outils de gestion), cliquez sur **CloudTrail**.

    ![AWS CloudTrail](media/aws-cloudtrail.png "AWS CloudTrail")

    Si vous n’avez pas encore utilisé CloudTrail, cliquez sur **Get Started** (Commencer) et configurez-le en indiquant un nom et en sélectionnant le compartiment S3 approprié, puis cliquez sur **Turn On** (Activer). Pour vérifier que vous disposez d’une couverture complète, affectez à **Apply to all regions** (Appliquer à toutes les régions) la valeur **Oui**.

    ![Activer CloudTrail dans AWS](media/aws-turnon-cloudtrail.png "Activer CloudTrail dans AWS")

    Vous devez voir le nouveau nom CloudTrail dans la liste **Trails** (Pistes).

    ![Liste CloudTrail dans AWS](media/aws-cloudtrail-list.png "Liste CloudTrail dans AWS")

    > [!NOTE]
    > Après avoir connecté AWS, vous recevez les événements des 7 jours précédant la connexion. Si vous venez d’activer CloudTrail, vous recevrez des événements à partir du moment où vous avez activé CloudTrail.

1. Dans le portail Cloud App Security, cliquez sur **Examiner**, puis sur **Applications connectées**.

1. Dans la page **connecteurs d’application** , pour fournir les informations d’identification du connecteur AWS, effectuez l’une des opérations suivantes :

    **Pour un nouveau connecteur**

    1. Cliquez sur le signe plus, puis sur **Amazon Web services**.

        ![connecter AWS](media/connect-aws.png "connecter AWS")

    1. Dans la fenêtre contextuelle, fournissez un nom pour le connecteur, puis cliquez sur **se connecter Amazon Web services**.

        ![Nom du connecteur AWS](media/aws-connect-name.png)

    1. Dans la page connecter Amazon Web services, sélectionnez **audit de sécurité**, collez **la clé d’accès** et la **clé secrète** du fichier. csv dans les champs appropriés, puis cliquez sur **se connecter**.

        ![Connecter l’audit de sécurité des applications AWS](media/aws-connect-app-audit.png "Connecter l’audit de sécurité des applications AWS")

    **Pour un connecteur existant**

    1. Dans la liste des connecteurs, sur la ligne dans laquelle le connecteur AWS s’affiche, cliquez sur **connecter l’audit de sécurité**.

        ![Capture d’écran de la page applications connectées, montrant le lien modifier l’audit de sécurité](media/aws-connect-app-edit-audit.png)

    1. Sur la page se connecter Amazon Web Services, collez la **clé d’accès** et la **clé secrète** du fichier. csv dans les champs appropriés, puis cliquez sur **se connecter**.

        ![Connecter l’audit de sécurité des applications AWS](media/aws-connect-app-edit-audit-creds.png "Connecter l’audit de sécurité des applications AWS")

1. Vérifiez la connexion en cliquant sur **Test API** (Tester l’API).  

    Le test peut prendre quelques minutes. Quand il est terminé, vous recevez une notification de réussite ou d’échec. Une fois que vous avez reçu une notification de réussite, cliquez sur **Terminé**.

## <a name="how-to-connect-aws-security-configuration-to-cloud-app-security"></a>Comment connecter la configuration de sécurité AWS à Cloud App Security

Suivez les étapes [de connexion de l’audit de sécurité AWS](#how-to-connect-aws-security-auditing-to-cloud-app-security) pour accéder à la page [autorisations](#set-permissions) .

1. Sur la page autorisations, cliquez sur **attacher les stratégies existantes directement**, appliquez les stratégies **AWSSecurityHubReadOnlyAccess** et **SecurityAudit** , puis cliquez sur **balises suivantes**.

    ![Attacher une stratégie existante dans AWS](media/aws-attach-policy.png "Attacher une stratégie existante dans AWS")

1. Facultatif : Ajoutez des balises à l’utilisateur.

    ![Ajouter des balises à l’utilisateur dans AWS](media/aws-add-tags.png)

    > [!NOTE]
    > L’ajout de balises à l’utilisateur n’affecte pas la connexion.

1. Cliquez sur **révision suivante**.

1. Si tous les détails sont corrects, cliquez sur **Create user** (Créer un utilisateur).

    ![Autorisations des utilisateurs dans AWS](media/aws-user-permissions.png "Vérifier les autorisations des utilisateurs dans AWS")

1. Lorsque vous recevez le message de réussite, cliquez sur **download. csv** pour enregistrer une copie de l’ID de la **clé d’accès** et de la **clé d’accès secrète**. vous en aurez besoin plus tard.

    ![Télécharger csv dans AWS](media/aws-download-csv.png "Télécharger csv dans AWS")

1. Dans le portail Cloud App Security, cliquez sur **Examiner**, puis sur **Applications connectées**.

1. Dans la page **connecteurs d’application** , pour fournir les informations d’identification du connecteur AWS, effectuez l’une des opérations suivantes :

    **Pour un nouveau connecteur**
    1. Cliquez sur le signe plus, puis sur **Amazon Web services**.<br>

        ![connecter AWS](media/connect-aws.png "connecter AWS")

    1. Dans la fenêtre contextuelle, fournissez un nom pour le connecteur, puis cliquez sur **se connecter Amazon Web services**.

        ![Nom du connecteur AWS](media/aws-connect-name.png)

    1. Dans la page connecter Amazon Web services, sélectionnez **configuration**de la sécurité, collez la **clé d’accès** et la **clé secrète** du fichier. csv dans les champs appropriés, puis cliquez sur **se connecter**.

        Connexion de la configuration de sécurité de l' ![application AWS] Connexion de la configuration de sécurité de l' (media/aws-connect-app-config.png "application AWS")

    **Pour un connecteur existant**
    1. Dans la liste des connecteurs, sur la ligne dans laquelle le connecteur AWS s’affiche, cliquez sur **connecter la configuration**de la sécurité.

        ![Capture d’écran de la page applications connectées, montrant le lien modifier la configuration de la sécurité](media/aws-connect-app-edit-config.png)

    1. Sur la page se connecter Amazon Web Services, collez la **clé d’accès** et la **clé secrète** du fichier. csv dans les champs appropriés, puis cliquez sur **se connecter**.

        Connexion de la configuration de sécurité de l' ![application AWS] Connexion de la configuration de sécurité de l' (media/aws-connect-app-edit-config-creds.png "application AWS")

1. Vérifiez la connexion en cliquant sur **Test API** (Tester l’API).  

    Le test peut prendre quelques minutes. Quand il est terminé, vous recevez une notification de réussite ou d’échec. Une fois que vous avez reçu une notification de réussite, cliquez sur **Terminé**.

## <a name="next-steps"></a>Étapes suivantes

[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)