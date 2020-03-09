---
title: Connecter la zone à Cloud App Security
description: Cet article fournit des informations sur la connexion de votre application Box à Cloud App Security à l’aide du connecteur API pour la visibilité et le contrôle de l’utilisation.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: e9a2a4ecc10506a992ba4e01ad4fac09eef37275
ms.sourcegitcommit: c303acdcb251c9b15930ab9ed701ab32dcaa6053
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2020
ms.locfileid: "78927956"
---
# <a name="connect-box-to-microsoft-cloud-app-security"></a>Connecter la zone à Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

Cet article fournit des instructions pour connecter Microsoft Cloud App Security à votre compte Box existant à l’aide des API du connecteur d’applications. Cette connexion vous donne une visibilité et un contrôle sur l’utilisation de Box. Pour plus d’informations sur la façon dont Cloud App Security protège la boîte, consultez [protection Box](protect-box.md).

## <a name="how-to-connect-box-to-cloud-app-security"></a>Comment connecter Box à Cloud App Security

> [!NOTE]
> Le déploiement avec un compte qui n’est pas un compte d’administrateur entraîne un échec dans le test de l’API et ne permet pas à Cloud App Security d’analyser tous les fichiers dans Box. S’il s’agit d’un problème pour vous, vous pouvez le déployer avec un coadministrateur dont tous les privilèges sont activés, mais le test de l’API continuera d’échouer et les fichiers appartenant aux autres administrateurs dans Box ne seront pas analysés.

1. Si vous restreignez l’accès aux autorisations des applications, suivez cette étape. Sinon, passez à l’étape 2.

    1. Connectez-vous avec un compte d’administrateur à votre compte Box.
    1. Cliquez sur **applications** > **applications personnalisées** > **paramètres**.

         ![applications Box](media/box-apps.png "applications Box")

    1. Si l’option **Désactiver les applications non publiées par défaut** est sélectionnée, dans la zone **de texte à l’exception de** , ajoutez la clé d’API Cloud App Security :

         |Centre de données|Clé API Cloud App Security|
         |----|----|
         |US1|`nduj1o3yavu30dii7e03c3n7p49cj2qh`|
         |Unis 2|`w0ouf1apiii9z8o0r6kpr4nu1pvyec75`|
         |US3|`dmcyvu1s9284i2u6gw9r2kb0hhve4a0r`|
         |EU1|`me9cm6n7kr4mfz135yt0ab9f5k4ze8qp`|
         |EU2|`uwdy5r40t7jprdlzo85v8suw1l4cdsbf`|

        Cliquez ensuite sur **Enregistrer**. Pour plus d’informations sur la façon de déterminer à quel Cloud App Security Centre de données auquel vous êtes connecté, consultez [afficher votre centre de données](network-requirements.md#view-your-data-center).

        ![paramètres Box à l’exception de](media/box-settings-except-for.png)

        > [!NOTE]
        > Si vous êtes un client Adallom existant et que votre URL de console concerne Adallom et non Cloud App Security, utilisez ce numéro de série d’application : `bwahmilhdlpbqy2ongkl119o3lrkoshc`.

2. Dans le portail Cloud App Security, cliquez sur **examiner** , puis sur **applications connectées**.

3. Dans la page **connecteurs d’application** , cliquez sur le bouton du signe plus et sélectionnez **Box**.

    ![zone de connexion](media/connect-box.png "zone de connexion")

4. Dans la fenêtre contextuelle **paramètres Box** , cliquez sur **suivre ce lien**.

5. La page de connexion à Box s’ouvre. Entrez vos informations d’identification pour autoriser Cloud App Security accès à l’application Box de votre équipe.

6. Box vous demande si vous souhaitez autoriser Cloud App Security accès aux informations de votre équipe, au Journal d’activité et à l’exécution des activités en tant que membre de l’équipe. Pour continuer, cliquez sur **Autoriser**.

7. De retour dans le portail Cloud App Security, vous devez recevoir un message indiquant que la boîte a été correctement connectée.

8. Vérifiez la connexion en cliquant sur **Test API** (Tester l’API).

    Le test peut prendre quelques minutes. Après avoir reçu un avis de réussite, cliquez sur **Fermer**.

Box est maintenant connecté à Cloud App Security.

Après la connexion, vous recevrez des événements pendant 60 jours avant la connexion.

Après la connexion Box, Cloud App Security effectue une analyse complète. Selon le nombre de fichiers et d’utilisateurs dont vous disposez, l’exécution de l’analyse complète peut prendre un certain temps. Pour activer l’analyse en quasi temps réel, les fichiers sur lesquels les activités sont détectées sont déplacés au début de la file d’attente d’analyse. Par exemple, un fichier qui est modifié, mis à jour ou partagé est analysé immédiatement au lieu d’attendre le processus d’analyse normal. L’analyse en quasi temps réel ne s’applique pas aux fichiers qui ne sont pas modifiés par nature. Par exemple, les fichiers qui sont affichés, prévisualisés, imprimés ou exportés sont analysés dans le cadre de l’analyse planifiée régulièrement.

Si vous rencontrez des problèmes lors de la connexion de l’application, consultez [résolution des problèmes liés aux connecteurs d’application](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Étapes suivantes :

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
