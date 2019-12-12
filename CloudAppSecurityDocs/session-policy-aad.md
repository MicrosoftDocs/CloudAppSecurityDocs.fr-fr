---
title: Créer des stratégies de session dans Cloud App Security
description: Cet article décrit la procédure de configuration d’une stratégie de session du contrôle d'application par accès conditionnel de Cloud App Security pour améliorer la visibilité des activités de session utilisateur et bloquer les téléchargements à l’aide des fonctionnalités de proxy inverse.
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
ms.openlocfilehash: c1ef5c688c4bdee59d73a63fb4e67a898eb7d0a5
ms.sourcegitcommit: 6eff466c7a6817b14a60d8c3b2c201c7ae4c2e2c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74721119"
---
# <a name="session-policies"></a>Stratégies de session

*S’applique à : Microsoft Cloud App Security*

Les stratégies de session Microsoft Cloud App Security permettent une surveillance en temps réel au niveau de la session, qui vous offre une visibilité plus précise des applications cloud et la possibilité de prendre différentes mesures selon la stratégie que vous définissez pour une session utilisateur. Au lieu [d’autoriser ou de bloquer complètement l’accès](access-policy-aad.md), avec le contrôle de session, vous pouvez autoriser l’accès pendant la surveillance de la session et/ou limiter des activités de session particulières à l’aide des fonctionnalités du proxy inversé du Contrôle d’accès conditionnel aux applications.

Par exemple, vous pouvez décider que pour les appareils non gérés ou pour les sessions provenant d’emplacements spécifiques, vous voulez autoriser l’utilisateur à accéder à l’application, mais aussi limiter le téléchargement des fichiers sensibles ou exiger que certains documents soient protégés lors de leur téléchargement. Les stratégies de session vous permettent de définir ces contrôles de session utilisateur, d’autoriser l’accès et de :

- [Surveiller toutes les activités](#monitor-session)
- [Bloquer tous les téléchargements](#block-download)
- [Bloquer des activités spécifiques](#block-activities)
- [Protéger des fichiers lors du téléchargement](#protect-download)

## <a name="prerequisites-to-using-session-policies"></a>Prérequis à l’utilisation de stratégies de session

- Licence Azure AD Premium P1
- Les applications appropriées doivent être [déployées avec le Contrôle d’accès conditionnel aux applications](proxy-deployment-aad.md)
- Une [stratégie d’accès conditionnel Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) doit être en place pour rediriger les utilisateurs vers le Microsoft Cloud App Security, comme décrit ci-dessous.

> [!NOTE]
> Les stratégies de session prennent également en charge les applications qui sont configurées avec des fournisseurs d’identité non-Azure AD. Pour plus d'informations sur ce scénario, envoyez un e-mail à mcaspreview@microsoft.com.

## <a name="create-an-azure-ad-conditional-access-policy"></a>Créer une stratégie d’accès conditionnel Azure AD

Les stratégies d’accès conditionnel Azure Active Directory et les stratégies de session Cloud App Security travaillent conjointement pour examiner chaque session utilisateur et prendre des décisions stratégiques pour chaque application. Pour configurer une stratégie d’accès conditionnel dans Azure AD, procédez comme suit :

1. Configurez une [stratégie d’accès conditionnel Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) avec des attributions pour l’utilisateur ou le groupe d’utilisateurs, et l’application que vous souhaitez contrôler avec le contrôle d’application par accès conditionnel.

    > [!NOTE]
    > Seules les applications [déployées avec le Contrôle d’accès conditionnel aux applications](proxy-deployment-aad.md) sont concernées par cette stratégie.

2. Routez les utilisateurs vers Microsoft Cloud App Security en sélectionnant **Utiliser le contrôle d’application par accès conditionnel** dans la page **Session**.

## <a name="create-a-cloud-app-security-session-policy"></a>Créer une stratégie de session Cloud App Security

Pour créer une stratégie de session, suivez cette procédure :

1. Dans le portail, sélectionnez **Contrôle**, puis **Stratégies**.
2. Dans la page **Stratégies**, cliquez sur **Créer une stratégie** et sélectionnez **Stratégie de session**.

3. Dans la fenêtre **Stratégie de session**, donnez un nom à votre stratégie, comme *Bloquer le téléchargement des documents sensibles dans Box pour les utilisateurs du service marketing*.

4. Dans le champ **Type de contrôle de session** :

    1. Sélectionnez **Surveiller uniquement** pour surveiller uniquement les activités des utilisateurs. De cette façon, vous créez une stratégie de type « Superviser uniquement », dans laquelle toutes les connexions, tous les téléchargements heuristiques et tous les types d’activités sont téléchargés pour les applications que vous avez sélectionnées.

    2. Si vous souhaitez superviser les activités de l’utilisateur, sélectionnez **Contrôler le téléchargement du fichier (avec DLP)** . Vous pouvez exécuter des actions supplémentaires, comme bloquer ou protéger les téléchargements pour les utilisateurs.

    3. Sélectionnez **Bloquer les activités** pour bloquer certaines activités, que vous pouvez sélectionner à l’aide du filtre **Type d’activité**. Toutes les activités des applications sélectionnées sont surveillées (et signalées dans le journal d’activité). Les activités que vous sélectionnez sont bloquées si vous sélectionnez l’action **Bloquer**. Les activités que vous avez sélectionnées déclencheront des alertes si vous sélectionnez l’action **Tester** et si vous activez les alertes.

5. Sous **Source de l’activité** dans la section **Activités remplissant toutes les conditions suivantes**, sélectionnez d’autres filtres d’activité à appliquer à la stratégie. Ces filtres peuvent inclure les options suivantes :

    - **Balise de l’appareil** : Utilisez ce filtre pour identifier les appareils non gérés.

    - **Emplacement** : Utilisez ce filtre pour identifier les emplacements inconnus (et par conséquent à risque).

    - **Adresse IP** : Utilisez ce filtre pour filtrer selon des adresses IP ou utiliser des balises d’adresse IP déjà attribuées.

    - **Étiquette agent utilisateur** : Utilisez ce filtre pour activer l’heuristique afin d’identifier les applications mobiles et de bureau. Ce filtre peut être défini de manière à être égal ou différent de **Client natif**. Ce filtre doit être testé sur vos applications mobiles et de bureau pour chacune des applications cloud.

    >[!NOTE]
    >Les stratégies de session ne prennent pas en charge les applications mobiles et de bureau. Les applications mobiles et les applications de bureau peuvent également être bloquées ou autorisées en créant une stratégie d’accès.

6. Si vous avez sélectionné l’option **Contrôler le téléchargement du fichier (avec DLP)**  :

   1. Sous **Source de l’activité** dans la section **Fichiers remplissant toutes les conditions suivantes**, sélectionnez d’autres filtres de fichiers à appliquer à la stratégie. Ces filtres peuvent inclure les options suivantes :

      - **Étiquette de classification** : Utilisez ce filtre si votre organisation utilise Azure Information Protection et que vos données ont été protégées par ses étiquettes de classification. Vous pouvez filtrer des fichiers en fonction de l’étiquette de classification que vous leur avez appliquée. Pour plus d’informations sur l’intégration à Azure Information Protection, consultez [Intégration à Azure Information Protection](azip-integration.md).

      - **Nom de fichier** : Utilisez ce filtre pour appliquer la stratégie à des fichiers spécifiques.

      - **Type de fichier** : Utilisez ce filtre pour appliquer la stratégie à des types de fichiers spécifiques, par exemple, pour bloquer le téléchargement de tous les fichiers .xls.

   2. Dans la section **Inspection du contenu**, indiquez si vous voulez activer le moteur DLP pour analyser les documents et le contenu des fichiers.

   3. Sous **Actions**, sélectionnez l’un des éléments suivants :

      - **Tester (Surveiller toutes les activités)**  : définissez cette action pour autoriser explicitement le téléchargement selon les filtres de stratégie que vous définissez.

      - **Bloquer (Bloquer le téléchargement de fichiers et surveiller toutes les activités)**  : définissez cette action pour bloquer explicitement le téléchargement selon les filtres de stratégie que vous définissez. Pour plus d’informations, consultez [Fonctionnement du blocage du téléchargement](#block-download).

      - **Protéger (Appliquer l’étiquette de classification pour télécharger et superviser toutes les activités)**  : cette option est uniquement disponible si vous avez sélectionné **Contrôler le téléchargement du fichier (avec DLP)** sous **Stratégie de session**. Si votre organisation utilise Azure Information Protection, vous pouvez définir une **action** pour appliquer une étiquette de classification définie dans Azure Information Protection sur le fichier. Pour plus d’informations, consultez [Fonctionnement de la protection du téléchargement](#protect-download).

7. Vous pouvez **Créer une alerte pour chaque événement correspondant avec le niveau de gravité de la stratégie** et définir un seuil d’alerte. Choisissez si l’alerte doit être envoyée par e-mail, par SMS, ou les deux.

## Surveiller toutes les activités <a name="monitor-session"></a>

Quand vous créez une stratégie de session, chaque session utilisateur qui correspond à la stratégie est redirigée vers le contrôle de session plutôt que directement vers l’application. L’utilisateur reçoit une notification de surveillance qui l’informe que ses sessions sont surveillées.

Si vous ne voulez pas en informer l’utilisateur, vous pouvez désactiver le message de notification.

1. Sous la roue dentée des paramètres, sélectionnez **Paramètres généraux**.

2. Puis, sous **Contrôle d’accès conditionnel aux applications**, sélectionnez **Suivi des utilisateurs** et décochez la case **Aviser les utilisateurs**.

Pour garder l’utilisateur dans la session, le Contrôle d’accès conditionnel aux applications remplace tous les URL, scripts de Java et cookies appropriés dans la session de l’application par des URL de Contrôle d’accès conditionnel aux applications. Par exemple, si l’application retourne une page avec des liens dont les domaines se terminent par myapp.com, le contrôle d’application par accès conditionnel remplace ces liens par des domaines se terminant par quelque chose comme myapp.com.us.cas.ms. Ainsi, la session entière est surveillée par Microsoft Cloud App Security.

Le Contrôle d’accès conditionnel aux applications enregistre les journaux de trafic de chaque session utilisateur acheminée vers lui. Les journaux de trafic incluent l’heure, l’adresse IP, l’agent utilisateur, les URL visitées et le nombre d’octets chargés et téléchargés. Ces journaux sont analysés et un rapport continu (**Contrôle d’application par accès conditionnel Cloud App Security**) est ajouté à la liste des rapports Cloud Discovery dans le tableau de bord Cloud Discovery.

Pour exporter ces journaux :

1. Accédez à la roue dentée des paramètres et cliquez sur **Contrôle d’accès conditionnel aux applications**.
2. Sur le côté droit du tableau, cliquez sur le bouton d’exportation.

   ![bouton d’exportation](media/export-button.png)
3. Sélectionnez la plage du rapport et cliquez sur **Exporter**. Ce processus peut prendre un certain temps.

Pour télécharger le journal exporté :

1. Une fois que le rapport est prêt, accédez à **Paramètres**, puis à **Rapports exportés**.
2. Dans le tableau, sélectionnez le rapport approprié dans la liste des **journaux du trafic du Contrôle d’application par accès conditionnel**, puis cliquez sur Télécharger.

    ![Bouton Télécharger](media/download-button.png)

## Bloquer tous les téléchargements <a name="block-download"></a>

Quand vous sélectionnez **Bloquer** sous **Action** dans la stratégie de session Cloud App Security, le contrôle d’application par accès conditionnel empêche l’utilisateur de télécharger un fichier, conformément aux filtres de fichiers de la stratégie. Un événement de téléchargement est reconnu par Microsoft Cloud App Security pour chaque application lorsqu’un utilisateur démarre un téléchargement. Le contrôle d’application par accès conditionnel intervient en temps réel pour en empêcher l’exécution. À la réception d’un signal de téléchargement par un utilisateur, le contrôle d’application par accès conditionnel retourne le message **Téléchargement restreint**, et remplace le fichier téléchargé par un fichier texte. Le message du fichier texte peut être configuré et personnalisé dans la stratégie de session.

## Bloquer des activités spécifiques <a name="block-activities"></a>

Quand l’option **Bloquer les activités** est définie pour le **Type d’activité**, vous pouvez sélectionner des activités spécifiques à bloquer dans des applications spécifiques. Toutes les activités des applications sélectionnées sont supervisées et signalées dans le journal d’activité. Les activités que vous sélectionnez sont bloquées si vous sélectionnez l’action **Bloquer**. Les activités que vous avez sélectionnées déclencheront des alertes si vous sélectionnez l’action **Tester** et si vous activez les alertes.

**Bloquez des activités** et appliquez ce blocage à certains groupes afin d’appliquer globalement un mode en lecture seule à l’échelle de votre organisation.

## Protéger des fichiers lors du téléchargement <a name="protect-download"></a>

Sélectionnez **Bloquer les activités** pour bloquer certaines activités, que vous pouvez sélectionner à l’aide du filtre **Type d’activité**. Toutes les activités des applications sélectionnées sont supervisées (et signalées dans le journal d’activité). Les activités que vous sélectionnez sont bloquées si vous sélectionnez l’action **Bloquer**. Les activités que vous avez sélectionnées déclencheront des alertes si vous sélectionnez l’action **Tester** et si vous activez les alertes.

Quand vous sélectionnez **Protéger** sous **Action** dans la stratégie de session Cloud App Security, le contrôle d’application par accès conditionnel applique l’étiquetage et la protection ultérieure d’un fichier, conformément aux filtres de fichiers de la stratégie. Les étiquettes sont configurées dans la console Azure Information Protection, et l’option **Protéger** doit être sélectionnée dans l’étiquette pour qu’elle apparaisse en tant qu’option dans la stratégie Cloud App Security. Quand une étiquette est sélectionnée et qu’un fichier correspondant aux critères de la stratégie Cloud App Security est téléchargé, l’étiquette et la protection correspondante (avec les autorisations) sont appliquées au fichier lors de son téléchargement. Le fichier original reste inchangé dans l’application cloud, tandis que le fichier téléchargé est désormais protégé. Les utilisateurs qui tentent d’accéder au fichier doivent respecter les exigences d’autorisation déterminées par la protection appliquée.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Blocage des téléchargements sur des appareils non gérés à l’aide de contrôles de session](use-case-proxy-block-session-aad.md)

## <a name="see-also"></a>Voir aussi

> [!div class="nextstepaction"]
> [Comment créer une stratégie d’accès](access-policy-aad.md)

> [!div class="nextstepaction"]
> [Déployer le contrôle d’application par accès conditionnel pour tous les types d’applications](proxy-deployment-any-app.md)

> [!div class="nextstepaction"]
> [Utilisation avec le Contrôle d’accès conditionnel aux applications de Cloud App Security](proxy-intro-aad.md)

[!INCLUDE [Open support ticket](includes/support.md)]
