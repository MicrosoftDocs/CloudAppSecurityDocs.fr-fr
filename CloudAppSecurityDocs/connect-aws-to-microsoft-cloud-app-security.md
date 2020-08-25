---
title: Se connecter Amazon Web Services avec Cloud App Security
description: Cet article vous explique comment connecter votre application AWS à Cloud App Security à l’aide du connecteur d’API, afin de bénéficier de plus de contrôle et de visibilité lors de l’utilisation.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 06/24/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: dff661d7db60a01cb9d66fc131add97db7598e04
ms.sourcegitcommit: 29a8e66c665f51d831516924ae4d9d8047b39276
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88781257"
---
# <a name="connect-aws-to-microsoft-cloud-app-security"></a>Connecter AWS à Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

Cet article fournit des instructions pour connecter votre compte Amazon Web Services (AWS) existant à Microsoft Cloud App Security à l’aide des API du connecteur. Pour plus d’informations sur la façon dont Cloud App Security protège AWS, consultez [protéger AWS](protect-aws.md).

Vous pouvez connecter l’un des deux AWS suivants au Cloud App Security connexions suivantes :

- **Audit de sécurité**: cette connexion vous offre une visibilité et un contrôle sur l’utilisation des applications AWS.
- **Configuration**de la sécurité : cette connexion vous donne des recommandations de sécurité fondamentales basées sur le benchmark Center for Internet Security (CIS) pour AWS.

Dans la mesure où vous pouvez ajouter une connexion ou les deux, les étapes décrites dans cet article sont écrites en tant qu’instructions indépendantes. Si vous avez déjà ajouté une des connexions, le cas échéant, modifiez les configurations existantes.

## <a name="how-to-connect-aws-security-auditing-to-cloud-app-security"></a>Comment connecter l’audit de sécurité AWS à Cloud App Security

Procédez comme suit pour configurer votre audit AWS, puis connectez-le à Cloud App Security.

### <a name="step-1-configure-amazon-web-services-auditing"></a>Étape 1 : configurer Amazon Web Services l’audit

1. Dans la [console Amazon Web services](https://console.aws.amazon.com/), sous **sécurité, identité & conformité**, cliquez sur **IAM**.

    ![Identité AWS et accès](media/aws-identity-and-access.png "Identité AWS et accès")

1. Sélectionnez **utilisateurs** , puis cliquez sur **Ajouter un utilisateur**.

    ![Utilisateurs AWS](media/aws-users.png "Utilisateurs AWS")

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

1. Click **Review policy** (Vérifier la stratégie).

1. Spécifiez un **Nom** et cliquez sur **Créer une stratégie**.

    ![Fournir le nom de la stratégie AWS](media/aws-create-policy.png "Fournir le nom de la stratégie AWS")

1. De retour à l’écran **Add user** (Ajouter un utilisateur), actualisez la liste si nécessaire et sélectionnez l’utilisateur que vous avez créé, puis cliquez sur **Next Review** (Prochaine vérification).

    ![Attacher une stratégie existante dans AWS](media/aws-attach-policy.png "Attacher une stratégie existante dans AWS")

1. Si tous les détails sont corrects, cliquez sur **Create user** (Créer un utilisateur).

    ![Autorisations utilisateur dans AWS](media/aws-user-permissions.png "Examiner les autorisations utilisateur dans AWS")

1. Quand vous obtenez le message de réussite, cliquez sur **Download .csv** (Télécharger .csv) pour enregistrer une copie des informations d’identification du nouvel utilisateur, car vous en aurez besoin ultérieurement.

    ![Télécharger CSV dans AWS](media/aws-download-csv.png "Télécharger CSV dans AWS")

1. Dans la console AWS, cliquez sur **Services** puis, sous **Management Tools** (Outils de gestion), cliquez sur **CloudTrail**.

    ![AWS CloudTrail](media/aws-cloudtrail.png "AWS CloudTrail")

    Si vous n’avez pas encore utilisé CloudTrail, cliquez sur **Get Started** (Commencer) et configurez-le en indiquant un nom et en sélectionnant le compartiment S3 approprié, puis cliquez sur **Turn On** (Activer). Pour vérifier que vous disposez d’une couverture complète, affectez à **Apply to all regions** (Appliquer à toutes les régions) la valeur **Oui**.

    ![Activer CloudTrail dans AWS](media/aws-turnon-cloudtrail.png "Activer CloudTrail dans AWS")

    Vous devez voir le nouveau nom CloudTrail dans la liste **Trails** (Pistes).

    ![Liste CloudTrail dans AWS](media/aws-cloudtrail-list.png "Liste CloudTrail dans AWS")

    > [!NOTE]
    > Après avoir connecté AWS, vous recevez les événements des 7 jours précédant la connexion. Si vous venez d’activer CloudTrail, vous recevrez des événements à partir du moment où vous avez activé CloudTrail.

### <a name="step-2-connect-amazon-web-services-auditing-to-cloud-app-security"></a>Étape 2 : se connecter Amazon Web Services l’audit à Cloud App Security

1. Dans le portail Cloud App Security, cliquez sur **Examiner**, puis sur **Applications connectées**.

1. Dans la page **connecteurs d’application** , pour fournir les informations d’identification du connecteur AWS, effectuez l’une des opérations suivantes :

    **Pour un nouveau connecteur**

    1. Cliquez sur le signe plus, puis sur **Amazon Web services**.

        ![connecter l’audit AWS](media/connect-aws.png "connecter AWS")

    1. Dans la fenêtre contextuelle, fournissez un nom pour le connecteur, puis cliquez sur **se connecter Amazon Web services**.

        ![Nom du connecteur d’audit AWS](media/connect-aws-name.png)

    1. Dans la page connecter Amazon Web services, sélectionnez **audit de sécurité**, collez **la clé d’accès** et la **clé secrète** du fichier. csv dans les champs appropriés, puis cliquez sur **se connecter**.

        ![Connecter l’audit de sécurité de l’application AWS pour le nouveau connecteur](media/aws-connect-app-audit.png "Connecter l’audit de sécurité des applications AWS")

    **Pour un connecteur existant**

    1. Dans la liste des connecteurs, sur la ligne dans laquelle le connecteur AWS s’affiche, cliquez sur **connecter l’audit de sécurité**.

        ![Capture d’écran de la page applications connectées, montrant le lien modifier l’audit de sécurité](media/aws-connect-app-edit-audit.png)

    1. Sur la page se connecter Amazon Web Services, collez la **clé d’accès** et la **clé secrète** du fichier. csv dans les champs appropriés, puis cliquez sur **se connecter**.

        ![Connecter l’audit de sécurité des applications AWS pour un connecteur existant](media/aws-connect-app-edit-audit-creds.png "Connecter l’audit de sécurité des applications AWS")

1. Cliquez sur **tester l’API** pour vérifier que la connexion a réussi.

    Le test peut prendre quelques minutes. Une fois l’opération terminée, vous recevez une notification de réussite ou d’échec. Une fois que vous avez reçu une notification de réussite, cliquez sur **Terminé**.

## <a name="how-to-connect-aws-security-configuration-to-cloud-app-security"></a>Comment connecter la configuration de sécurité AWS à Cloud App Security

La connexion de la configuration de sécurité AWS vous donne des informations sur les recommandations de sécurité fondamentales basées sur le test de sécurité Center for Internet Security (CIS) pour AWS.

Procédez comme suit pour connecter la configuration de sécurité AWS à Cloud App Security.

> [!div class="checklist"]
>
> - [Configurer le concentrateur de sécurité AWS](#set-up-aws-security-hub)
> - [Connexion de la configuration de sécurité AWS à Cloud App Security](#connect-aws-security-configuration-to-cloud-app-security)

### <a name="set-up-aws-security-hub"></a>Configurer le concentrateur de sécurité AWS

Pour afficher les recommandations de sécurité pour plusieurs régions, répétez les étapes suivantes pour chaque région pertinente.

> [!NOTE]
> Si vous utilisez un compte principal, répétez ces étapes pour configurer le compte principal et tous les comptes des membres connectés dans toutes les régions pertinentes.

1. Activez la [configuration AWS](https://docs.aws.amazon.com/config/latest/developerguide/gs-console.html).
1. Activez le [concentrateur de sécurité AWS](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-settingup.html).
1. Vérifiez que les données sont transmises au hub de sécurité.

    > [!NOTE]
    > Lorsque vous activez pour la première fois Security Hub, plusieurs heures peuvent être nécessaires pour que les données soient disponibles.

### <a name="connect-aws-security-configuration-to-cloud-app-security"></a>Connexion de la configuration de sécurité AWS à Cloud App Security

Avant de pouvoir vous connecter à la configuration de la sécurité AWS, assurez-vous que vous avez [configuré votre environnement AWS](#set-up-aws-security-hub) pour collecter des recommandations fondamentales sur la sécurité et la conformité.

> [!NOTE]
> Si vous utilisez un [compte maître AWS](https://aws.amazon.com/security-hub/faqs/), procédez comme suit pour vous connecter au compte principal. La connexion de votre compte principal vous permet de recevoir des recommandations pour tous les comptes membres dans toutes les régions.

### <a name="step-1-configure-amazon-web-services-security-configuration"></a>Étape 1 : configurer la configuration de la sécurité Amazon Web Services

1. Suivez les étapes *de connexion de l’audit de sécurité AWS* pour accéder à la page [autorisations](#set-permissions) .

1. Sur la page autorisations, cliquez sur **attacher les stratégies existantes directement**, appliquez les stratégies **AWSSecurityHubReadOnlyAccess** et **SecurityAudit** , puis cliquez sur **balises suivantes**.

    ![Attacher une stratégie existante dans AWS](media/aws-attach-policy.png "Attacher une stratégie existante dans AWS")

1. Facultatif : ajoutez des balises à l’utilisateur.

    ![Ajouter des balises à l’utilisateur dans AWS](media/aws-add-tags.png)

    > [!NOTE]
    > L’ajout de balises à l’utilisateur n’affecte pas la connexion.

1. Cliquez sur **révision suivante**.

1. Si tous les détails sont corrects, cliquez sur **Create user** (Créer un utilisateur).

    ![Autorisations utilisateur dans AWS](media/aws-user-permissions.png "Examiner les autorisations utilisateur dans AWS")

1. Lorsque vous recevez le message de réussite, cliquez sur **download. csv** pour enregistrer une copie de l’ID de la **clé d’accès** et de la **clé d’accès secrète**. vous en aurez besoin plus tard.

    ![Télécharger CSV dans AWS](media/aws-download-csv.png "Télécharger CSV dans AWS")

### <a name="step-2-connect-amazon-web-services-security-configuration-to-cloud-app-security"></a>Étape 2 : se connecter Amazon Web Services configuration de sécurité à Cloud App Security

1. Dans Cloud App Security, cliquez sur **examiner**, puis sélectionnez **applications connectées**.

1. Dans l’onglet **applications de configuration** de la sécurité, cliquez sur le bouton plus, puis sélectionnez **Amazon Web services**.

    ![connexion à la configuration de sécurité AWS](media/connect-aws-security-configuration.png)

1. Dans la page nom de l' **instance** , choisissez le type d’instance, puis cliquez sur **suivant**.

    - Pour un connecteur existant, choisissez l’instance appropriée.

        ![Sélection de l’instance AWS](media/connect-aws-existing-instance.png)

    - Pour un nouveau connecteur, fournissez un nom pour l’instance.

        ![Nom du connecteur de configuration de sécurité AWS](media/aws-connect-name.png)

1. Dans la page **Détails du compte** , collez la clé d' **accès** et la **clé secrète** du fichier. csv dans les champs appropriés, puis cliquez sur **suivant**.

    ![Connecter les détails du compte AWS](media/aws-connect-account-details.png)

1. Dans la page **terminé** , assurez-vous que la connexion a réussi, puis cliquez sur **terminé**.

Si vous rencontrez des problèmes lors de la connexion de l’application, consultez [résolution des problèmes liés aux connecteurs d’application](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
