---
title: Connectez Google Cloud Platform à Cloud App Security
description: Cet article fournit des informations sur la façon de connecter votre Google Cloud Platform à Cloud App Security à l’aide du connecteur API pour la visibilité et le contrôle de l’utilisation.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/16/2019
ms.topic: conceptual
ms.service: cloud-app-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 65237f7be2218dad16c09f3940ca53c478d022bc
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74461207"
---
# <a name="connect-google-cloud-platform-to-microsoft-cloud-app-security-preview"></a>Se connecter Google Cloud Platform à Microsoft Cloud App Security (version préliminaire)

*S’applique à : Microsoft Cloud App Security*

Cet article fournit des instructions pour connecter Microsoft Cloud App Security à votre compte Google Cloud Platform existant (GCP) à l’aide des API du connecteur. Cette connexion vous donne une visibilité et un contrôle sur l’utilisation de GCP.

> [!NOTE]
> Les instructions pour connecter votre environnement GCP suivent les [recommandations de Google pour la](https://cloud.google.com/blog/products/gcp/best-practices-for-working-with-google-cloud-audit-logging) consommation des journaux agrégés. L’intégration s’appuie sur Google StackDriver et consomme des ressources supplémentaires susceptibles d’avoir un impact sur votre facturation. Les ressources consommées sont les suivantes :
>
> * [Récepteur d’exportation agrégé – niveau de l’Organisation](https://cloud.google.com/logging/docs/export/aggregated_exports#concept)
> * [Publication/sous-rubrique – niveau de projet GCP](https://cloud.google.com/logging/docs/export/using_exported_logs#pubsub-overview)
> * [Abonnement Pub/Sub – niveau de projet GCP](https://cloud.google.com/logging/docs/export/using_exported_logs#pubsub-overview)
>
> Actuellement, Cloud App Security importe uniquement les journaux d’audit de l’activité admin ; Les journaux d’audit des événements système et d’accès aux données ne sont pas importés. Pour plus d’informations sur les journaux GCP, consultez [journaux d’audit Cloud](https://go.microsoft.com/fwlink/?linkid=2109230).

Nous vous recommandons d’utiliser un projet dédié pour l’intégration et de restreindre l’accès au projet pour maintenir une intégration stable et empêcher les suppressions/modifications du processus d’installation. En outre, si votre instance GCP fait partie d’une instance G suite déjà connectée à Cloud App Security, nous vous recommandons de suivre le **pour une instance GCP qui fait partie d’une procédure d’organisation g suite connectée** lorsque vous ajoutez les détails de connexion GCP.

## <a name="prerequisites"></a>Conditions préalables requises

L’utilisateur GCP d’intégration doit disposer des autorisations suivantes :

* **IAM et modification administrateur** – niveau organisation
* **Création et modification d’un projet**

## <a name="configure-google-cloud-platform"></a>Configurer Google Cloud Platform

* Connectez-vous à votre portail GCP à l’aide de votre compte d’utilisateur intégré GCP.

### <a name="create-a-dedicated-project"></a>Créer un projet dédié

Créer un projet dédié dans GCP dans le cadre de votre organisation pour permettre l’isolation et la stabilité de l’intégration

1. Cliquez sur **créer un projet** pour démarrer un nouveau.
1. Dans l’écran **nouveau projet** , nommez votre projet et cliquez sur **créer**.

    ![Capture d’écran montrant la boîte de dialogue de création de projet GCP](media/connect-gcp-create-project.png)

### <a name="enable-the-pubsub-api"></a>Activer l’API Pub/Sub

1. Basculez vers le projet dédié.
1. Accédez à l’onglet Pub/Sub. Un message d’activation de service doit s’afficher.

### <a name="create-a-dedicated-service-account-for-the-integration"></a>Créer un compte de service dédié pour l’intégration

1. Sous **IAM & admin**, cliquez sur **comptes de service**.
1. Cliquez sur **créer un compte de service** pour créer un compte de service dédié.
1. Entrez un nom de compte, puis cliquez sur **créer**.
1. Spécifiez le **rôle** en tant que **Pub/Sub admin** , puis cliquez sur **Enregistrer**.

    ![Capture d’écran montrant GCP ajouter un rôle IAM](media/connect-gcp-iam-role.PNG)

1. Copiez la valeur de l' **e-mail** . vous en aurez besoin plus tard.

    ![Capture d’écran montrant la boîte de dialogue compte de service GCP](media/connect-gcp-create-service-account.png)

1. Sous **iam & admin**, cliquez sur **IAM**.

    1. Basculez vers le niveau de l’organisation.
    1. Cliquez sur **Ajouter**.
    1. Dans la zone **nouveaux membres** , collez la valeur de l' **e-mail** que vous avez copiée précédemment.
    1. Spécifiez le **rôle** en tant que **writer de configuration des journaux** , puis cliquez sur **Enregistrer**.

        ![Capture d’écran montrant la boîte de dialogue Ajouter un membre](media/connect-gcp-add-member.png)

### <a name="create-a-private-key-for-the-dedicated-service-account"></a>Créer une clé privée pour le compte de service dédié

1. Passez au niveau du projet.
1. Sous **IAM & admin**, cliquez sur **comptes de service**.
1. Ouvrez le compte de service dédié, puis cliquez sur **modifier**.
1. Cliquez sur **créer une clé**.
1. Dans l’écran **créer une clé privée** , sélectionnez **JSON**, puis cliquez sur **créer**.

    ![Capture d’écran montrant la boîte de dialogue créer une clé privée](media/connect-gcp-create-private-key.png)

    > [!NOTE]
    > Vous aurez besoin du fichier JSON téléchargé sur votre ordinateur ultérieurement.

### <a name="retrieve-your-organization-id"></a>Récupérer votre ID d’organisation

Prenez note de votre **ID d’organisation**. vous en aurez besoin plus tard. Pour plus d’informations, consultez [obtention de votre ID d’organisation](https://cloud.google.com/resource-manager/docs/creating-managing-organization#retrieving_your_organization_id).
    Capture d’écran ![montrant la boîte de dialogue ID d’organisation](media/connect-gcp-org-id.png)

## <a name="configure-cloud-app-security"></a>Configurer Cloud App Security

* Dans le portail Cloud App Security, cliquez sur **Examiner**, puis sur **Applications connectées**.

### <a name="add-the-gcp-connection-details"></a>Ajouter les détails de la connexion GCP

Pour fournir les détails de connexion GCP, sous **connecteurs d’applications**, effectuez l’une des opérations suivantes :

**Pour une instance GCP qui ne fait pas partie d’une organisation G suite connectée**

1. Cliquez sur le signe plus, puis sur **Google Cloud Platform**.

    ![Capture d’écran montrant le menu Ajouter un GCP](media/connect-gcp-add.png)

1. Dans la fenêtre contextuelle, fournissez un nom pour le connecteur, puis cliquez sur **se connecter Google Cloud Platform**.

1. Dans la page Google Cloud Platform, procédez comme suit :
    1. Dans la zone ID de l' **organisation** , entrez l’organisation que vous avez notée précédemment.
    1. Dans la zone **fichier de clé privée** , accédez au fichier JSON que vous avez téléchargé précédemment.
    1. Cliquez sur **se connecter Google Cloud Platform**.

    > [!NOTE]
    > Nous vous recommandons de connecter votre instance G suite pour bénéficier d’une gestion et d’une gouvernance des utilisateurs unifiées. Il s’agit de l’option recommandée même si vous n’utilisez pas de produits G suite et que les utilisateurs GCP sont gérés par le biais du système de gestion des utilisateurs G suite.

**Pour une instance de GCP qui fait partie d’une organisation G suite connectée**

1. Dans la liste des instances connectées, à la fin de la ligne dans laquelle le connecteur G suite s’affiche, cliquez sur les trois points, puis cliquez sur **ajouter Google Cloud Platform**.

1. Dans la page Google Cloud Platform, procédez comme suit :
    1. Dans la zone ID de l' **organisation** , entrez l’organisation que vous avez notée précédemment.
    1. Dans la zone **fichier de clé privée** , accédez au fichier JSON que vous avez téléchargé précédemment.
    1. Cliquez sur **se connecter Google Cloud Platform**.

    > [!NOTE]
    > Cela permet une gestion et une gouvernance des utilisateurs unifiées via le domaine de l’identité de l’utilisateur G suite.

### <a name="test-the-connection"></a>Tester la connexion

Vérifiez la connexion en cliquant sur **Test API** (Tester l’API).

Le test peut prendre quelques minutes. Quand il est terminé, vous recevez une notification de réussite ou d’échec. Une fois que vous avez reçu une notification de réussite, cliquez sur **Terminé**.

## <a name="aggregated-export-sink"></a>Récepteur d’exportation agrégé

La désactivation du récepteur d’exportation agrégé est actuellement possible uniquement via Google Cloud Shell.

### <a name="to-disable-aggregated-export-sink"></a>Pour désactiver le récepteur d’exportation agrégé

| Étape | Script | Pour plus d'informations |
|-|-|-|
| 1. Démarrez une session Google Cloud Shell. | | [Utilisation de Cloud Shell](https://cloud.google.com/shell/docs/using-cloud-shell) |
| 2. Définissez le projet actif. | `gcloud config set project {PROJECT_ID}` | [jeu de configuration gcloud](https://cloud.google.com/sdk/gcloud/reference/config/set) |
| 3. répertoriez les récepteurs au niveau de l’organisation. | `gcloud logging sinks list --organization={ORGANIZATION_ID}` | [Liste des récepteurs de journalisation gcloud](https://cloud.google.com/sdk/gcloud/reference/logging/sinks/list) |
| 4. Supprimez le récepteur approprié. | `gcloud logging sinks delete {SINK_NAME} --organization={ORGANIZATION_ID}` | [suppression des récepteurs de journalisation gcloud](https://cloud.google.com/sdk/gcloud/reference/logging/sinks/delete) |

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
