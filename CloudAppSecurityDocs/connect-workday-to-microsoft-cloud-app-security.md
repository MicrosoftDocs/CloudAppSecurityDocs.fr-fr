---
title: Connecter un jour ouvré à Cloud App Security (version préliminaire)
description: Cet article fournit des informations sur la connexion de votre application de jour de travail à Cloud App Security à l’aide du connecteur API pour la visibilité et le contrôle de l’utilisation.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/31/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 032ed68260e178c176c631b41eb7dc64e869cbd3
ms.sourcegitcommit: 00599ac6c64a4c62ed9ebdda3edb58f90f92c24d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912195"
---
# <a name="connect-workday-to-microsoft-cloud-app-security-preview"></a>Connecter un jour ouvré à Microsoft Cloud App Security (version préliminaire)

*S’applique à : Microsoft Cloud App Security*

Cet article fournit des instructions pour connecter Microsoft Cloud App Security à votre compte de jour de travail existant à l’aide de l’API du connecteur d’applications. Cette connexion vous donne une visibilité et un contrôle sur l’utilisation des jours de travail. Pour plus d’informations sur la façon dont Cloud App Security protège la journée de travail, consultez [protéger la journée de travail](protect-workday.md).

## <a name="quick-start"></a>Démarrage rapide

Regardez notre vidéo de démarrage rapide qui montre comment configurer les composants requis et effectuer les étapes de la journée de travail. Une fois que vous avez terminé les étapes de la vidéo, vous pouvez [Ajouter le connecteur de la journée de travail](#add-connector).

<br />

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4n1ZO]

## <a name="prerequisites"></a>Prerequisites

Le compte de jour de travail utilisé pour la connexion à Cloud App Security doit être membre d’un groupe de sécurité (nouveau ou existant). Nous vous recommandons d’utiliser un utilisateur système d’intégration de jours ouvrables. Les autorisations suivantes doivent être sélectionnées pour le groupe de sécurité pour les stratégies de sécurité de domaine suivantes :

| Zone fonctionnelle | Stratégie de sécurité du domaine | Stratégie de sécurité des sous-domaines | Autorisations de rapport/tâche | Autorisations d'intégration |
| --- | --- | --- | --- | --- |
| System | Configuration : configuration du locataire – général | Configuration : configuration du client – sécurité | Afficher, modifier | Acquérir, put |
| System | Administration de la sécurité | | Afficher, modifier | Acquérir, put |
| System | Audit du système | | Affichez | Obtenir |
| Effectifs | Données de travail : personnel | Données de travail : rapports de travail public | Affichez | Obtenir |

> [!NOTE]
>
> * Le compte utilisé pour configurer les autorisations pour le groupe de sécurité doit être un administrateur de jours de travail.
> * Pour définir des autorisations, recherchez « stratégies de sécurité de domaine pour la zone fonctionnelle », puis recherchez chaque zone fonctionnelle (« système »/« personnel ») et accordez les autorisations indiquées dans le tableau.
> * Une fois que toutes les autorisations ont été définies, recherchez « activer les modifications de stratégie de sécurité en attente » et approuvez les modifications.

Pour plus d’informations sur la configuration des utilisateurs d’intégration des jours de travail, des groupes de sécurité et des autorisations, consultez les étapes 1 à 4 du Guide d' [intégration ou d’accès du point de terminaison externe au jour](https://go.microsoft.com/fwlink/?linkid=2103212) ouvrable (accessible avec la documentation des jours de travail/informations d’identification de la Communauté).

## <a name="how-to-connect-workday-to-cloud-app-security-using-oauth"></a>Connexion de la journée de travail à Cloud App Security à l’aide d’OAuth

1. Connectez-vous à la journée de travail à l’aide d’un compte membre du groupe de sécurité mentionné dans les conditions préalables.

1. Recherchez « modifier le paramétrage du locataire – système », puis, sous **Journal d’activité utilisateur**, sélectionnez **activer la journalisation**de l’activité des utilisateurs.

    ![Capture d’écran de l’autorisation de la journalisation des activités des utilisateurs](media/connect-workday-enable-logging.png)

1. Recherchez « modifier le paramétrage du locataire – sécurité », puis sous **paramètres oauth 2,0**, sélectionnez **clients OAuth 2,0 activés**.

1. Recherchez « Register API client » et sélectionnez **Register API client-Task**.

1. Dans la page **inscrire le client** de l’API, renseignez les informations suivantes, puis cliquez sur **OK**.

    | Nom de champ | valeur |
    | ---- | ---- |
    | Nom du client | Microsoft Cloud App Security |
    | Type d’octroi client | Octroi de code d’autorisation |
    | Type de jeton d’accès | Porteur |
    | URI de redirection | `https://portal.cloudappsecurity.com/api/oauth/connect` |
    | Étendues OAuth2 | **Personnel** et **système** |
    | Étendue (zones fonctionnelles) | **Personnel** et **système** |

    ![Capture d’écran de l’inscription du client API](media/connect-workday-register-api-client.png)

1. Une fois inscrit, prenez note des paramètres suivants, puis cliquez sur **terminé**.

    * ID de client
    * Clé secrète client
    * Point de terminaison de l’API REST de travail
    * Point de terminaison de jeton
    * Point de terminaison d’autorisation

    ![Capture d’écran de confirmation de l’inscription de l’API client](media/connect-workday-register-api-client-confirm.png)

1. <a name="add-connector"></a>Dans le portail Cloud App Security, cliquez sur **examiner** , puis sur **applications connectées**.

1. Dans la page **connecteurs d’application** , cliquez sur le bouton plus, puis sur jour de **travail**.

    ![Capture d’écran de l’ajout d’un connecteur d’application](media/connect-workday-add-app.png)

1. Dans la fenêtre contextuelle, ajoutez le nom de votre instance, puis cliquez sur **connecter un jour ouvré**.

    ![Capture d’écran de l’ajout d’un nom d’instance](media/connect-workday-add-app-connect.png)

1. Sur la page suivante, renseignez les détails avec les informations que vous avez notées précédemment, puis cliquez sur **se connecter dans les jours ouvrés**.

    ![Capture d’écran de remplissage des détails de l’application](media/connect-workday-add-app-connect-details.png)

1. Dans la journée de travail, une fenêtre contextuelle vous demande si vous souhaitez autoriser Cloud App Security accès à votre compte de jours ouvrés. Pour continuer, cliquez sur **Autoriser**.

    ![Capture d’écran de l’autorisation d’accès à l’application](media/connect-workday-add-app-allow.png)

1. De retour dans le portail Cloud App Security, vous devriez voir un message indiquant que la journée de travail a été correctement connectée. Vérifiez que la connexion a réussi en cliquant sur **Tester l’API**.

    Le test peut prendre quelques minutes. Une fois averti que la connexion a réussi, cliquez sur **Fermer**.

> [!NOTE]
> Après la connexion de la journée de travail, vous recevrez des événements pendant sept jours avant la connexion.

Si vous rencontrez des problèmes lors de la connexion de l’application, consultez [résolution des problèmes liés aux connecteurs d’application](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
