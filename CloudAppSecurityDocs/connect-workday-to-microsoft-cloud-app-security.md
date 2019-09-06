---
title: Connecter un jour ouvré à Cloud App Security
description: Cet article fournit des informations sur la connexion de votre application de jour de travail à Cloud App Security à l’aide du connecteur API pour la visibilité et le contrôle de l’utilisation.
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: ShlomoSagir-MS
ms.date: 9/5/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: fefff041971b65d27e4a3409034af0569894dc04
ms.sourcegitcommit: 24c0dd16c7e8212f614fb6fd66c9f18ce75c0b45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2019
ms.locfileid: "70373124"
---
# <a name="connect-workday-to-microsoft-cloud-app-security"></a>Connecter un jour ouvré à Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

Cet article fournit des instructions pour connecter Microsoft Cloud App Security à votre compte de jour de travail existant à l’aide de l’API du connecteur d’applications. Cette connexion vous donne une visibilité et un contrôle sur l’utilisation des jours de travail.

## <a name="prerequisites"></a>Prérequis

- Le compte de jour de travail utilisé pour la connexion à Cloud App Security doit être membre d’un groupe de sécurité pour lequel les domaines suivants sont activés :

  - Administration de la sécurité du système
  - Audit système
  - Personnel-données de travail : Public Worker Reports

  Nous vous recommandons d’utiliser un utilisateur système d’intégration de jours ouvrables.

- Si votre déploiement de jours de travail gère des plages d’adresses IP, vous devez autoriser toutes les adresses IP de Cloud App Security. Pour obtenir la liste des adresses IP, consultez [Configuration réseau requise-connecteur d’applications](network-requirements.md#app-connector).

## <a name="how-to-connect-workday-to-cloud-app-security-using-oauth"></a>Connexion de la journée de travail à Cloud App Security à l’aide d’OAuth

1. Connectez-vous avec un compte d’administrateur à votre compte de jours ouvrés.

1. Recherchez « modifier le paramétrage du locataire – système », puis, sous **Journal d’activité utilisateur**, sélectionnez **activer la journalisation**de l’activité des utilisateurs.

    ![Capture d’écran de l’autorisation de la journalisation des activités des utilisateurs](media/connect-workday-enable-logging.png)

1. Recherchez « modifier le paramétrage du locataire – sécurité », puis sous **paramètres oauth 2,0**, sélectionnez **clients OAuth 2,0 activés**.

1. Recherchez « Register API client » et sélectionnez **Register API client-Task**.

1. Dans la page **inscrire le client** de l’API, renseignez les informations suivantes, puis cliquez sur **OK**.

    | Nom du champ | Valeur |
    | ---- | ---- |
    | Nom du client | Microsoft Cloud App Security |
    | Type d’octroi client | Octroi de code d’autorisation |
    | Type de jeton d’accès | Porteur |
    | URI de redirection | `https://portal.cloudappsecurity.com/api/oauth/connect` |
    | Étendues OAuth2 | **Personnel** et **système** |
    | Étendue (zones fonctionnelles) | **Personnel** et **système** |

    ![Capture d’écran de l’inscription du client API](media/connect-workday-register-api-client.png)

1. Une fois inscrit, prenez note des paramètres suivants, puis cliquez sur **terminé**.

    - ID client
    - Clé secrète client
    - Point de terminaison de l’API REST de travail
    - Point de terminaison de jeton
    - Point de terminaison d’autorisation

    ![Capture d’écran de confirmation de l’inscription de l’API client](media/connect-workday-register-api-client-confirm.png)

1. Dans le portail Cloud App Security, cliquez sur **examiner** , puis sur **applications connectées**.

1. Dans la page **connecteurs d’application** , cliquez sur le bouton plus, puis sur jour de **travail**.

    ![Capture d’écran de l’ajout d’un connecteur d’application](media/connect-workday-add-app.png)

1. Dans la fenêtre contextuelle, ajoutez le nom de votre instance, puis cliquez sur **connecter un jour ouvré**.

    ![Capture d’écran de l’ajout d’un nom d’instance](media/connect-workday-add-app-connect.png)

1. Sur la page suivante, renseignez les détails avec les informations que vous avez notées précédemment, puis cliquez sur **se connecter dans les jours ouvrés**.

    ![Capture d’écran de remplissage des détails de l’application](media/connect-workday-add-app-connect-details.png)

1. Dans la journée de travail, une fenêtre contextuelle vous demande si vous souhaitez autoriser Cloud App Security accès à votre compte de jours ouvrés. Pour continuer, cliquez sur **Autoriser**.

    ![Capture d’écran de l’autorisation d’accès à l’application](media/connect-workday-add-app-allow.png)

1. De retour dans le portail Cloud App Security, vous devriez voir un message indiquant que la journée de travail a été correctement connectée. Vérifiez la connexion en cliquant sur **Test API** (Tester l’API).

    Le test peut prendre quelques minutes. Une fois averti que la connexion a réussi, cliquez sur **Fermer**.

> [!NOTE]
> Après la connexion de la journée de travail, vous recevrez des événements pendant sept jours avant la connexion.

## <a name="next-steps"></a>Étapes suivantes

[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)
