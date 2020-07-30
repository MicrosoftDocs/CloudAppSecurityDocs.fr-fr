---
title: Connectez Google Cloud Platform à Cloud App Security
description: Cet article fournit des informations sur la façon de connecter votre Google Cloud Platform à Cloud App Security à l’aide du connecteur API pour la visibilité et le contrôle de l’utilisation.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 06/28/2020
ms.topic: conceptual
ms.service: cloud-app-security
ms.collection: M365-security-compliance
ms.openlocfilehash: a792ae503fda51e69d162cec0b5e32cd3710780f
ms.sourcegitcommit: 84eafb4926bf0d4db27bed7df55dc83ca48f9192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87377862"
---
# <a name="connect-google-cloud-platform-to-microsoft-cloud-app-security"></a>Connectez Google Cloud Platform à Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

Cet article fournit des instructions pour connecter Microsoft Cloud App Security à votre compte Google Cloud Platform existant (GCP) à l’aide des API du connecteur. Cette connexion vous donne une visibilité et un contrôle sur l’utilisation de GCP. Pour plus d’informations sur la façon dont Cloud App Security protège les GCP, consultez [protéger GCP](protect-gcp.md).

Nous vous recommandons d’utiliser un projet dédié pour l’intégration et de restreindre l’accès au projet pour maintenir une intégration stable et empêcher les suppressions/modifications du processus d’installation. En outre, si votre instance GCP fait partie d’une instance G suite déjà connectée à Cloud App Security, nous vous recommandons de suivre le **pour une instance GCP qui fait partie d’une procédure d’organisation g suite connectée** lorsque vous ajoutez les détails de connexion GCP.

## <a name="prerequisites"></a>Prérequis

L’utilisateur GCP d’intégration doit disposer des autorisations suivantes :

- **IAM et modification administrateur** – niveau organisation
- **Création et modification d’un projet**

Vous pouvez connecter l’un des GCP suivants, ou les deux, aux connexions Cloud App Security :

- **Audit de sécurité**: cette connexion vous offre une visibilité et un contrôle de l’utilisation des applications GCP.
- **Configuration**de la sécurité : cette connexion vous donne des recommandations de sécurité fondamentales basées sur le benchmarking Center for Internet Security (CIS) pour GCP.

Dans la mesure où vous pouvez ajouter une connexion ou les deux, les étapes décrites dans cet article sont écrites en tant qu’instructions indépendantes. Si vous avez déjà ajouté une des connexions, le cas échéant, modifiez les configurations existantes.

## <a name="how-to-connect-gcp-security-auditing-to-cloud-app-security"></a>Comment connecter l’audit de sécurité GCP à Cloud App Security

La connexion de l’audit de sécurité GCP vous offre une visibilité et un contrôle sur l’utilisation des applications GCP.

Procédez comme suit pour connecter l’audit de sécurité AWS à Cloud App Security.

> [!div class="checklist"]
>
> - [Configurer Google Cloud Platform](#configure-google-cloud-platform)
> - [Connectez Google Cloud Platform audit à Cloud App Security](#connect-google-cloud-platform-auditing-to-cloud-app-security)
> - [Récepteur d’exportation agrégé](#aggregated-export-sink)

### <a name="configure-google-cloud-platform"></a>Configurer Google Cloud Platform

> [!NOTE]
> Les instructions pour connecter votre environnement GCP à des fins d’audit suivent les [recommandations de Google pour la](https://cloud.google.com/blog/products/gcp/best-practices-for-working-with-google-cloud-audit-logging) consommation des journaux agrégés. L’intégration s’appuie sur Google StackDriver et consomme des ressources supplémentaires susceptibles d’avoir un impact sur votre facturation. Les ressources consommées sont les suivantes :
>
> - [Récepteur d’exportation agrégé – niveau de l’Organisation](https://cloud.google.com/logging/docs/export/aggregated_exports#concept)
> - [Publication/sous-rubrique – niveau de projet GCP](https://cloud.google.com/logging/docs/export/using_exported_logs#pubsub-overview)
> - [Abonnement Pub/Sub – niveau de projet GCP](https://cloud.google.com/logging/docs/export/using_exported_logs#pubsub-overview)
>
> La connexion d’audit Cloud App Security importe uniquement les journaux d’audit des activités d’administration ; Les journaux d’audit des événements système et d’accès aux données ne sont pas importés. Pour plus d’informations sur les journaux GCP, consultez [journaux d’audit Cloud](https://go.microsoft.com/fwlink/?linkid=2109230).

#### <a name="create-a-dedicated-project"></a>Créer un projet dédié

Créer un projet dédié dans GCP dans le cadre de votre organisation pour permettre l’isolation et la stabilité de l’intégration

1. Connectez-vous à votre portail GCP à l’aide de votre compte d’utilisateur intégré GCP.
1. Cliquez sur **créer un projet** pour démarrer un nouveau.
1. Dans l’écran **nouveau projet** , nommez votre projet et cliquez sur **créer**.

    ![Capture d’écran montrant la boîte de dialogue de création de projet GCP](media/connect-gcp-create-project.png)

#### <a name="enable-required-apis"></a>Activer les API requises

1. Basculez vers le projet dédié.
1. Accédez à l’onglet **bibliothèque** .
1. Recherchez et sélectionnez **API de journalisation Cloud**, puis dans la page API, cliquez sur **activer**.
1. Recherchez et sélectionnez l' **API Cloud Pub/Sub**, puis dans la page API, cliquez sur **activer**.

    > [!NOTE]
    > Veillez à ne pas sélectionner l' **API Pub/Sub Lite**.

#### <a name="create-a-dedicated-service-account-for-the-security-auditing-integration"></a>Créer un compte de service dédié pour l’intégration de l’audit de sécurité

1. Sous **IAM & admin**, cliquez sur **comptes de service**.
1. Cliquez sur **créer un compte de service** pour créer un compte de service dédié.
1. Entrez un nom de compte, puis cliquez sur **créer**.
1. Spécifiez le **rôle** en tant que **Pub/Sub admin** , puis cliquez sur **Enregistrer**.

    ![Capture d’écran montrant GCP ajouter un rôle IAM](media/connect-gcp-iam-role.PNG)

1. Copiez la valeur de l' **e-mail** . vous en aurez besoin plus tard.

    ![Capture d’écran montrant la boîte de dialogue compte de service GCP](media/connect-gcp-create-service-account.png)

1. Sous **iam & admin**, cliquez sur **IAM**.

    1. Basculez vers le niveau de l’organisation.
    1. Cliquez sur **AJOUTER**.
    1. Dans la zone **nouveaux membres** , collez la valeur de l' **e-mail** que vous avez copiée précédemment.
    1. Spécifiez le **rôle** en tant que **writer de configuration des journaux** , puis cliquez sur **Enregistrer**.

        ![Capture d’écran montrant la boîte de dialogue Ajouter un membre](media/connect-gcp-add-member.png)

#### <a name="create-a-private-key-for-the-dedicated-service-account"></a>Créer une clé privée pour le compte de service dédié

1. Passez au niveau du projet.
1. Sous **IAM & admin**, cliquez sur **comptes de service**.
1. Ouvrez le compte de service dédié, puis cliquez sur **modifier**.
1. Cliquez sur **créer une clé**.
1. Dans l’écran **créer une clé privée** , sélectionnez **JSON**, puis cliquez sur **créer**.

    ![Capture d’écran montrant la boîte de dialogue créer une clé privée](media/connect-gcp-create-private-key.png)

    > [!NOTE]
    > Vous aurez besoin du fichier JSON téléchargé sur votre ordinateur ultérieurement.

#### <a name="retrieve-your-organization-id"></a>Récupérer votre ID d’organisation

Prenez note de votre **ID d’organisation**. vous en aurez besoin plus tard. Pour plus d’informations, consultez [obtention de votre ID d’organisation](https://cloud.google.com/resource-manager/docs/creating-managing-organization#retrieving_your_organization_id).

![Capture d’écran montrant la boîte de dialogue ID d’organisation](media/connect-gcp-org-id.png)

### <a name="connect-google-cloud-platform-auditing-to-cloud-app-security"></a>Connectez Google Cloud Platform audit à Cloud App Security

#### <a name="add-the-gcp-connection-details"></a>Ajouter les détails de la connexion GCP

1. Dans le portail Cloud App Security, cliquez sur **Examiner**, puis sur **Applications connectées**.

1. Dans la page **connecteurs d’application** , pour fournir les informations d’identification du connecteur AWS, effectuez l’une des opérations suivantes :

    > [!NOTE]
    > Nous vous recommandons de connecter votre instance G suite pour bénéficier d’une gestion et d’une gouvernance des utilisateurs unifiées. Il s’agit de l’option recommandée même si vous n’utilisez pas de produits G suite et que les utilisateurs GCP sont gérés par le biais du système de gestion des utilisateurs G suite.

    **Pour un nouveau connecteur**

    1. Cliquez sur le signe plus, puis sur **Google Cloud Platform**.

        ![connecter GCP](media/connect-gcp-add.png)

    1. Dans la fenêtre contextuelle, fournissez un nom pour le connecteur, puis cliquez sur **se connecter Google Cloud Platform**.

        ![Nom du connecteur GCP](media/connect-gcp-name.png)

    1. Dans la page **Détails du projet** , effectuez les opérations suivantes, puis cliquez sur **se connecter Google Cloud Platform**.
        1. Dans la zone ID de l' **organisation** , entrez l’organisation que vous avez notée précédemment.
        1. Dans la zone **fichier de clé privée** , accédez au fichier JSON que vous avez téléchargé précédemment.

        ![Connecter l’audit de sécurité de l’application GCP](media/connect-gcp-app-audit.png)

    **Pour un connecteur existant**

    1. Dans la liste des connecteurs, sur la ligne dans laquelle le connecteur AWS s’affiche, cliquez sur **connecter l’audit de sécurité**.

        ![Capture d’écran de la page applications connectées, montrant le lien modifier l’audit de sécurité](media/connect-gcp-app-edit-audit.png)

    1. Dans la page **Détails du projet** , effectuez les opérations suivantes, puis cliquez sur **se connecter Google Cloud Platform**.
        1. Dans la zone ID de l' **organisation** , entrez l’organisation que vous avez notée précédemment.
        1. Dans la zone **fichier de clé privée** , accédez au fichier JSON que vous avez téléchargé précédemment.

        ![Connecter l’audit de sécurité de l’application GCP](media/connect-gcp-app-edit-audit-creds.png)

1. Cliquez sur **tester l’API** pour vérifier que la connexion a réussi.

    Le test peut prendre quelques minutes. Une fois l’opération terminée, vous recevez une notification de réussite ou d’échec. Une fois que vous avez reçu une notification de réussite, cliquez sur **Terminé**.

Si vous rencontrez des problèmes lors de la connexion de l’application, consultez [résolution des problèmes liés aux connecteurs d’application](troubleshooting-api-connectors-using-error-messages.md).

### <a name="aggregated-export-sink"></a>Récepteur d’exportation agrégé

La désactivation du récepteur d’exportation agrégé est actuellement possible uniquement via Google Cloud Shell.

#### <a name="to-disable-aggregated-export-sink"></a>Pour désactiver le récepteur d’exportation agrégé

| Étape | Script | Informations supplémentaires |
|-|-|-|
| 1. Démarrez une session Google Cloud Shell. | | [Utilisation de Cloud Shell](https://cloud.google.com/shell/docs/using-cloud-shell) |
| 2. Définissez le projet actif. | `gcloud config set project {PROJECT_ID}` | [jeu de configuration gcloud](https://cloud.google.com/sdk/gcloud/reference/config/set) |
| 3. répertoriez les récepteurs au niveau de l’organisation. | `gcloud logging sinks list --organization={ORGANIZATION_ID}` | [Liste des récepteurs de journalisation gcloud](https://cloud.google.com/sdk/gcloud/reference/logging/sinks/list) |
| 4. Supprimez le récepteur approprié. | `gcloud logging sinks delete {SINK_NAME} --organization={ORGANIZATION_ID}` | [suppression des récepteurs de journalisation gcloud](https://cloud.google.com/sdk/gcloud/reference/logging/sinks/delete) |

## <a name="how-to-connect-gcp-security-configuration-to-cloud-app-security"></a>Comment connecter la configuration de sécurité GCP à Cloud App Security

La connexion de la configuration de sécurité GCP vous donne des informations sur les recommandations de sécurité fondamentales basées sur le test de référence de la sécurité Internet (CIS) de Center pour GCP.

Procédez comme suit pour connecter la configuration de sécurité GCP à Cloud App Security.

> [!div class="checklist"]
>
> - [Configurer le centre de commandes de sécurité GCP avec l’analyse d’intégrité de la sécurité](#set-up-gcp-security-command-center-with-security-health-analytics)
> - [Activer l’API du centre de commandes de sécurité](#enable-security-command-center-api)
> - [Créer un compte de service dédié pour l’intégration de la configuration de la sécurité](#create-a-dedicated-service-account-for-the-security-configuration-integration)
> - [Connectez-vous Google Cloud Platform Configuration de sécurité à Cloud App Security](#connect-google-cloud-platform-security-configuration-to-cloud-app-security)

### <a name="set-up-gcp-security-command-center-with-security-health-analytics"></a>Configurer le centre de commandes de sécurité GCP avec l’analyse d’intégrité de la sécurité

1. Configurez le [Centre de commandes de sécurité](https://cloud.google.com/security-command-center/docs/quickstart-security-command-center).
1. [Activez GCP Security Health Analytics](https://cloud.google.com/security-command-center/docs/how-to-use-security-health-analytics).
1. Vérifiez que les données sont transmises au centre de commandes de sécurité.

    > [!NOTE]
    >
    > - Les instructions de connexion de votre environnement GCP pour la configuration de sécurité suivent les [recommandations de Google pour l'](https://cloud.google.com/security-command-center/docs/how-to-notifications#enable-scc-api) utilisation des recommandations de configuration de sécurité. L’intégration s’appuie sur le centre de commandes de sécurité de Google et consomme des ressources supplémentaires susceptibles d’avoir un impact sur votre facturation.
    > - Lorsque vous activez pour la première fois l’analyse de l’intégrité de la sécurité, plusieurs heures peuvent être nécessaires pour que les données soient disponibles.

### <a name="enable-security-command-center-api"></a>Activer l’API du centre de commandes de sécurité

1. Dans Bibliothèque de l’API de la console Cloud, sélectionnez le projet auquel vous souhaitez vous connecter Cloud App Security.
1. Dans la bibliothèque d’API, recherchez et sélectionnez l’API Centre de commandes de sécurité.
1. Dans la page API, cliquez sur **activer**.

### <a name="create-a-dedicated-service-account-for-the-security-configuration-integration"></a>Créer un compte de service dédié pour l’intégration de la configuration de la sécurité

1. Dans le centre de commandes de sécurité GCP, sélectionnez le projet auquel vous souhaitez vous connecter Cloud App Security.
1. Sous **IAM & admin**, cliquez sur **comptes de service**.
1. Cliquez sur **créer un compte de service** pour créer un compte de service dédié.
1. Entrez un nom de compte, puis cliquez sur **créer**.
1. Spécifiez **Role** le rôle **Security Center la visionneuse d’administration** , puis cliquez sur **Enregistrer**.

    ![Capture d’écran montrant le menu Ajouter un GCP](media/connect-gcp-security-configuration-1.png)

1. Copiez la valeur de l' **e-mail** . vous en aurez besoin plus tard.

    ![Capture d’écran montrant la boîte de dialogue compte de service GCP](media/connect-gcp-security-configuration-2.png)

1. Sous **iam & admin**, cliquez sur **IAM**.

    1. Basculez vers le niveau de l’organisation.
    1. Cliquez sur **AJOUTER**.
    1. Dans la zone **nouveaux membres** , collez la valeur de l' **e-mail** que vous avez copiée précédemment.
    1. Spécifiez **Role** le rôle **Security Center la visionneuse d’administration** , puis cliquez sur **Enregistrer**.

        ![Capture d’écran montrant la boîte de dialogue Ajouter un membre](media/connect-gcp-security-configuration-3.png)

#### <a name="create-a-private-key-for-the-dedicated-service-account"></a>Créer une clé privée pour le compte de service dédié

1. Passez au niveau du projet.
1. Sous **IAM & admin**, cliquez sur **comptes de service**.
1. Ouvrez le compte de service dédié, puis cliquez sur **modifier**.
1. Cliquez sur **créer une clé**.
1. Dans l’écran **créer une clé privée** , sélectionnez **JSON**, puis cliquez sur **créer**.

    ![Capture d’écran montrant la boîte de dialogue créer une clé privée](media/connect-gcp-security-configuration-4.png)

    > [!NOTE]
    > Vous aurez besoin du fichier JSON téléchargé sur votre ordinateur ultérieurement.

#### <a name="retrieve-your-organization-id"></a>Récupérer votre ID d’organisation

Prenez note de votre **ID d’organisation**. vous en aurez besoin plus tard. Pour plus d’informations, consultez [obtention de votre ID d’organisation](https://cloud.google.com/resource-manager/docs/creating-managing-organization#retrieving_your_organization_id).
    ![Capture d’écran montrant la boîte de dialogue ID d’organisation](media/connect-gcp-org-id.png)

### <a name="connect-google-cloud-platform-security-configuration-to-cloud-app-security"></a>Connectez-vous Google Cloud Platform Configuration de sécurité à Cloud App Security

1. Dans Cloud App Security, cliquez sur **examiner**, puis sélectionnez **applications connectées**.

1. Dans l’onglet **applications de configuration** de la sécurité, cliquez sur le bouton plus, puis sélectionnez **Google Cloud Platform**.

    ![Capture d’écran montrant le menu Ajouter un GCP](media/connect-gcp-security-configuration-5.png)

1. Dans la page nom de l' **instance** , choisissez le type d’instance, puis cliquez sur **suivant**.

    - Pour un connecteur existant, choisissez l’instance appropriée.

        ![Sélection de l’instance GCP](media/connect-gcp-existing-instance.png)

    - Pour un nouveau connecteur, fournissez un nom pour l’instance.

        ![Nom du connecteur GCP](media/connect-gcp-new-instance.png)

1. Dans la page **Détails du projet** , effectuez les opérations suivantes, puis cliquez sur **suivant**.
    1. Dans la zone ID de l' **organisation** , entrez l’organisation que vous avez notée précédemment.
    1. Dans la zone **fichier de clé privée** , accédez au fichier JSON que vous avez téléchargé précédemment.

    ![Ajouter les détails du projet GCP](media/connect-gcp-security-configuration-6.png)

1. Dans la page **terminé** , assurez-vous que la connexion a réussi, puis cliquez sur **terminé**.

Si vous rencontrez des problèmes lors de la connexion de l’application, consultez [résolution des problèmes liés aux connecteurs d’application](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
