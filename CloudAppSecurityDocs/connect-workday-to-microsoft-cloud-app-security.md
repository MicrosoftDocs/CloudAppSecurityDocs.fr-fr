---
title: Connecter un jour ouvré à Cloud App Security (version préliminaire)
description: Cet article fournit des informations sur la connexion de votre application de jour de travail à Cloud App Security à l’aide du connecteur API pour la visibilité et le contrôle de l’utilisation.
ms.date: 02/09/2021
ms.topic: how-to
ms.openlocfilehash: 482b606f5d21e53f4fe514ced0ebdee509146a93
ms.sourcegitcommit: 91cd536019579c022b877ab7f0687cef8fb8209d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/10/2021
ms.locfileid: "100105376"
---
# <a name="connect-workday-to-microsoft-cloud-app-security"></a>Connecter un jour ouvré à Microsoft Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Cet article fournit des instructions pour connecter Microsoft Cloud App Security à votre compte de jour de travail existant à l’aide de l’API du connecteur d’applications. Cette connexion vous donne une visibilité et un contrôle sur l’utilisation des jours de travail. Pour plus d’informations sur la façon dont Cloud App Security protège la journée de travail, consultez [protéger la journée de travail](protect-workday.md).

## <a name="quick-start"></a>Démarrage rapide

Regardez notre vidéo de démarrage rapide qui montre comment configurer les composants requis et effectuer les étapes de la journée de travail. Une fois que vous avez terminé les étapes de la vidéo, vous pouvez [Ajouter le connecteur de la journée de travail](#add-connector).

> [!NOTE]
> La vidéo n’indique pas l’étape requise pour la configuration du groupe de sécurité **configuré : client setup-permission System** . Assurez-vous également de le configurer.

<br />

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4n1ZO]

## <a name="prerequisites"></a>Prérequis

Le compte de jour de travail utilisé pour la connexion à Cloud App Security doit être membre d’un groupe de sécurité (nouveau ou existant). Nous vous recommandons d’utiliser un utilisateur système d’intégration de jours ouvrables. Les autorisations suivantes doivent être sélectionnées pour le groupe de sécurité pour les stratégies de sécurité de domaine suivantes :

| Zone fonctionnelle | Stratégie de sécurité du domaine | Stratégie de sécurité des sous-domaines | Autorisations de rapport/tâche | Autorisations d'intégration |
| --- | --- | --- | --- | --- |
| Système | Configuration : configuration du locataire – général | Configuration : configuration du client – sécurité | Afficher, modifier | Acquérir, put |
| Système | Configuration : configuration du locataire – général | Configuration : configuration du client – système | Modifier | Aucun |
| Système | Administration de la sécurité | | Afficher, modifier | Acquérir, put |
| Système | Audit du système | | Affichage | Obtenir |
| Effectifs | Données de travail : personnel | Worker Data: Public Worker Reports | Affichage | Obtenir |

> [!NOTE]
>
> * Le compte utilisé pour configurer les autorisations pour le groupe de sécurité doit être un administrateur de jours de travail.
> * Pour définir des autorisations, recherchez « stratégies de sécurité de domaine pour la zone fonctionnelle », puis recherchez chaque zone fonctionnelle (« système »/« personnel ») et accordez les autorisations indiquées dans le tableau.
> * Une fois que toutes les autorisations ont été définies, recherchez « activer les modifications de stratégie de sécurité en attente » et approuvez les modifications.

Pour plus d’informations sur la configuration des utilisateurs d’intégration des jours de travail, des groupes de sécurité et des autorisations, consultez les étapes 1 à 4 du Guide d' [intégration ou d’accès du point de terminaison externe au jour](https://go.microsoft.com/fwlink/?linkid=2103212) ouvrable (accessible avec la documentation des jours de travail/informations d’identification de la Communauté).

## <a name="how-to-connect-workday-to-cloud-app-security-using-oauth"></a>Connexion de la journée de travail à Cloud App Security à l’aide d’OAuth

1. Connectez-vous à la journée de travail à l’aide d’un compte membre du groupe de sécurité mentionné dans les conditions préalables.

1. Recherchez « modifier le paramétrage du locataire – système », puis, sous **Journal d’activité utilisateur**, sélectionnez **activer la journalisation** de l’activité des utilisateurs.

    ![Capture d’écran de l’autorisation de la journalisation des activités des utilisateurs](media/connect-workday-enable-logging.png)

1. Recherchez « modifier le paramétrage du locataire – sécurité », puis sous **paramètres oauth 2,0**, sélectionnez **clients OAuth 2,0 activés**.

1. Recherchez « Register API client » et sélectionnez **Register API client-Task**.

1. Dans la page **inscrire le client** de l’API, renseignez les informations suivantes, puis cliquez sur **OK**.

    | Nom du champ | Valeur |
    | ---- | ---- |
    | Nom du client | Microsoft Cloud App Security |
    | Type d’octroi client | Octroi de code d’autorisation |
    | Type de jeton d’accès | Porteur |
    | URI de redirection | `https://portal.cloudappsecurity.com/api/oauth/connect`<br /><br />**Remarque**: pour les clients du gouvernement des États-Unis, entrez la valeur suivante : `https://portal.cloudappsecurity.us/api/oauth/connect` |
    | Jetons d’actualisation sans expiration | Oui |
    | Étendues OAuth2 | **Personnel** et **système** |
    | Étendue (zones fonctionnelles) | **Personnel** et **système** |

    ![Capture d’écran de l’inscription du client API](media/connect-workday-register-api-client.png)

1. Une fois inscrit, prenez note des paramètres suivants, puis cliquez sur **terminé**.

    * ID client
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

1. Dans la journée de travail, une fenêtre contextuelle s’affiche pour vous demander si vous souhaitez autoriser Cloud App Security accès à votre compte de jours ouvrés. Pour continuer, cliquez sur **Autoriser**.

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
