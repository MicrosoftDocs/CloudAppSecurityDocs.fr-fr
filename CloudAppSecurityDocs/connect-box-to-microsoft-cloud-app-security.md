---
title: Connecter Box à Cloud App Security
description: Cet article vous explique comment connecter votre application Box à Cloud App Security à l’aide du connecteur d’API, afin de bénéficier de plus de contrôle et de visibilité lors de l’utilisation.
ms.date: 12/10/2018
ms.topic: how-to
ms.openlocfilehash: 775653ae7beacbba69fb55fd6934bae44d7e31f5
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96312996"
---
# <a name="connect-box-to-microsoft-cloud-app-security"></a>Connecter Box à Microsoft Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Cet article fournit des instructions pour connecter Microsoft Cloud App Security à votre compte Box existant à l’aide des API du connecteur d’applications. Cette connexion vous permet de bénéficier de plus de visibilité et de contrôle lors de l’utilisation de Box. Pour plus d’informations sur la façon dont Cloud App Security protège la boîte, consultez [protection Box](protect-box.md).

## <a name="how-to-connect-box-to-cloud-app-security"></a>Comment connecter Box à Cloud App Security

> [!NOTE]
> Le déploiement avec un compte qui n’est pas un compte d’administrateur entraîne un échec du test de l’API et n’autorise pas Cloud App Security à analyser tous les fichiers inclus dans Box. S’il s’agit d’un problème pour vous, vous pouvez effectuer le déploiement avec un coadministrateur qui a tous les privilèges cochés, mais le test de l’API continuera d’échouer et les fichiers appartenant aux autres administrateurs dans Box ne seront pas analysés.

1. Si vous restreignez l’accès aux autorisations des applications, suivez cette étape. Sinon, passez à l’étape 2.

    1. Connectez-vous avec un compte d’administrateur à votre compte Box.
    1. Cliquez sur les **Apps**  >  paramètres applications **personnalisées** des applications  >  **Settings**.

         ![box, applications](media/box-apps.png "box, applications")

    1. Si l’option **Désactiver les applications non publiées par défaut** est sélectionnée, dans la zone **de texte à l’exception de** , ajoutez la clé d’API Cloud App Security :

         |Centre de données|Clé API Cloud App Security|
         |----|----|
         |US1|`nduj1o3yavu30dii7e03c3n7p49cj2qh`|
         |US2|`w0ouf1apiii9z8o0r6kpr4nu1pvyec75`|
         |US3|`dmcyvu1s9284i2u6gw9r2kb0hhve4a0r`|
         |EU1|`me9cm6n7kr4mfz135yt0ab9f5k4ze8qp`|
         |EU2|`uwdy5r40t7jprdlzo85v8suw1l4cdsbf`|

        Ensuite, cliquez sur **Enregistrer**. Pour plus d’informations sur la façon de déterminer à quel Cloud App Security Centre de données auquel vous êtes connecté, consultez [afficher votre centre de données](network-requirements.md#view-your-data-center).

        ![paramètres box, except for (à l’exception de)](media/box-settings-except-for.png)

        > [!NOTE]
        > Si vous êtes un client Adallom existant et que votre URL de console concerne Adallom et non Cloud App Security, utilisez ce numéro de série d’application : `bwahmilhdlpbqy2ongkl119o3lrkoshc` .

2. Dans le portail Cloud App Security, cliquez sur **Examiner**, puis sur **Applications connectées**.

3. Dans la page **Connecteurs d’application**, cliquez sur le bouton plus (+), puis sélectionnez **Box**.

    ![zone de connexion](media/connect-box.png "connecter box")

4. Dans la fenêtre contextuelle **paramètres Box** , cliquez sur **suivre ce lien**.

5. La page de connexion à Box s’ouvre. Entrez vos informations d’identification pour autoriser Cloud App Security à accéder à l’application Box de votre équipe.

6. Box vous demande si vous voulez autoriser Cloud App Security à accéder aux informations de votre équipe, au journal d’activité et à effectuer des activités en tant que membre de l’équipe. Pour continuer, cliquez sur **Autoriser**.

7. De retour dans le portail Cloud App Security, vous devez recevoir un message indiquant que Box a été correctement connecté.

8. Vérifiez que la connexion a réussi en cliquant sur **Tester l’API**.

    Le test peut prendre quelques minutes. Une fois averti que la connexion a réussi, cliquez sur **Fermer**.

Box est maintenant connecté à Cloud App Security.

Après avoir connecté Box, vous recevez les événements des 60 jours précédant la connexion.

Après la connexion de Box, Cloud App Security effectue une analyse complète. Selon le nombre de fichiers et d’utilisateurs, l’exécution de l’analyse complète peut prendre du temps. Pour activer l’analyse en quasi temps réel, les fichiers sur lesquels des activités sont détectées sont déplacés au début de la file d’attente d’analyse. Par exemple, un fichier qui est modifié, mis à jour ou partagé est analysé immédiatement au lieu d’attendre le processus d’analyse régulier. L’analyse en quasi temps réel ne s’applique pas aux fichiers qui ne sont pas modifiés de façon intrinsèque. Par exemple, les fichiers qui sont affichés, prévisualisés, imprimés ou exportés sont analysés dans le cadre de l’analyse planifiée régulièrement.

Si vous rencontrez des problèmes lors de la connexion de l’application, consultez [résolution des problèmes liés aux connecteurs d’application](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
