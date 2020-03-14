---
title: Créer des stratégies de session dans Cloud App Security
description: Cet article décrit la procédure de configuration d’une Cloud App Security contrôle d’application par accès conditionnel stratégie de session obtient une visibilité détaillée des activités de session utilisateur et des téléchargements de bloc à l’aide des fonctionnalités de proxy inverse.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/14/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 06a9b0fc0a732f745d370fe28541b0a753bfe0cc
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285723"
---
# <a name="session-policies"></a>Stratégies de session

*S’applique à : Microsoft Cloud App Security*

Microsoft Cloud App Security stratégies de session activent la surveillance en temps réel au niveau de la session, ce qui vous offre une visibilité granulaire des applications Cloud et la possibilité d’effectuer des actions différentes en fonction de la stratégie que vous définissez pour une session utilisateur. Au lieu d’autoriser [ou de bloquer complètement l’accès](access-policy-aad.md), avec le contrôle de session, vous pouvez autoriser l’accès pendant la surveillance de la session et/ou limiter les activités de session spécifiques à l’aide des fonctionnalités de proxy inverse de contrôle d’application par accès conditionnel.

Par exemple, vous pouvez décider qu’à partir d’appareils non gérés ou pour les sessions provenant d’emplacements spécifiques, vous voulez autoriser l’utilisateur à accéder à l’application, mais aussi limiter le téléchargement de fichiers sensibles ou exiger que certains documents soient protégés lors du téléchargement. Les stratégies de session vous permettent de définir ces contrôles de session utilisateur et d’autoriser l’accès et vous permettent d’effectuer les opérations suivantes :

* [Surveiller toutes les activités](#monitor-session)
* [Bloquer tous les téléchargements](#block-download)
* [Bloquer des activités spécifiques](#block-activities)
* [Protéger les fichiers lors du téléchargement](#protect-download)
* [Protéger les téléchargements de fichiers sensibles](#protect-upload)
* [Informer les utilisateurs de la protection des fichiers sensibles](#educate-protect)

## <a name="prerequisites-to-using-session-policies"></a>Conditions préalables à l’utilisation des stratégies de session

* Licence Azure AD Premium P1
* Les applications appropriées doivent être [déployées avec contrôle d’application par accès conditionnel](proxy-deployment-aad.md)
* Une [stratégie d’accès conditionnel Azure ad](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) doit être en place pour rediriger les utilisateurs vers Microsoft Cloud App Security, comme décrit ci-dessous.

> [!NOTE]
> Les stratégies de session prennent également en charge les applications qui sont configurées avec des fournisseurs d’identité autres que Azure AD. Pour plus d’informations sur ce scénario, envoyez un e-mail à mcaspreview@microsoft.com.

## <a name="create-an-azure-ad-conditional-access-policy"></a>Créer une stratégie d’accès conditionnel Azure AD

Azure Active Directory stratégies d’accès conditionnel et les stratégies de session de Cloud App Security fonctionnent en tandem pour examiner chaque session utilisateur et prendre des décisions de stratégie pour chaque application. Pour configurer une stratégie d’accès conditionnel dans Azure AD, procédez comme suit :

1. Configurez une [stratégie d’accès conditionnel Azure ad](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) avec des affectations pour un utilisateur ou un groupe d’utilisateurs et l’application que vous souhaitez contrôler avec le contrôle d’application par accès conditionnel.

    > [!NOTE]
    > Seules [les applications déployées avec contrôle d’application par accès conditionnel](proxy-deployment-aad.md) seront affectées par cette stratégie.

2. Acheminez les utilisateurs vers Microsoft Cloud App Security en sélectionnant la **contrôle d’application par accès conditionnel restrictions appliquées** dans la **session** .

## <a name="create-a-cloud-app-security-session-policy"></a>Créer une stratégie de session de Cloud App Security

Pour créer une stratégie de session, procédez comme suit :

1. Dans le portail, sélectionnez **contrôle** , puis **stratégies**.
1. Dans la page **stratégies** , cliquez sur **créer une stratégie** et sélectionnez stratégie de **session**.
1. Dans la fenêtre **stratégie de session** , attribuez un nom à votre stratégie, par exemple bloquer le *téléchargement de documents sensibles dans Box pour les utilisateurs du service marketing*.
1. Dans le champ **type de contrôle de session** :

    1. Sélectionnez **surveiller uniquement** si vous souhaitez uniquement surveiller les activités des utilisateurs. Cette sélection permet de créer une stratégie surveiller uniquement pour les applications que vous avez sélectionnées, où toutes les connexions, les téléchargements heuristiques et les types d’activités sont téléchargés.

    1. Sélectionnez **contrôler le téléchargement du fichier (avec DLP)** si vous souhaitez surveiller les activités des utilisateurs. Vous pouvez effectuer des actions supplémentaires comme bloquer ou protéger les téléchargements pour les utilisateurs.
    1. Sélectionnez **bloquer les activités** pour bloquer des activités spécifiques, que vous pouvez sélectionner à l’aide du filtre **type d’activité** . Toutes les activités des applications sélectionnées sont surveillées (et signalées dans le journal d’activité). Les activités spécifiques que vous sélectionnez sont bloquées si vous sélectionnez l’action **bloquer** . Les activités spécifiques que vous avez sélectionnées déclenchent des alertes si vous sélectionnez l’action de **test** et si les alertes sont activées.
1. Sous **source** de l’activité dans la section **activités répondant à toutes les conditions suivantes** , sélectionnez des filtres d’activité supplémentaires à appliquer à la stratégie. Ces filtres peuvent inclure les options suivantes :

    * **Balises d’appareils**: utilisez ce filtre pour identifier les appareils non gérés.

    * **Emplacement**: utilisez ce filtre pour identifier les emplacements inconnus (et par conséquent risqués).

    * **Adresse IP**: utilisez ce filtre pour filtrer par adresse IP ou pour utiliser des balises d’adresse IP précédemment attribuées.

    * **Étiquette de l’agent utilisateur**: utilisez ce filtre pour activer l’heuristique afin d’identifier les applications mobiles et de bureau. Ce filtre peut être défini sur est égal à ou n’est pas égal à **Native Client**. Ce filtre doit être testé par rapport à vos applications mobiles et de bureau pour chaque application Cloud.

    >[!NOTE]
    >Les stratégies de session ne prennent pas en charge les applications mobiles et de bureau. Les applications mobiles et les applications de bureau peuvent également être bloquées ou autorisées par la création d’une stratégie d’accès.

1. Si vous avez sélectionné l’option permettant de **contrôler le téléchargement de fichiers (avec DLP)** :

    1. Sous **source** de l’activité dans la section **fichiers correspondant à toutes les conditions suivantes** , sélectionnez les filtres de fichiers supplémentaires à appliquer à la stratégie. Ces filtres peuvent inclure les options suivantes :

        * **Étiquette de classification** : utilisez ce filtre si votre organisation utilise Azure information protection et que vos données ont été protégées par ses étiquettes de classification. Vous pouvez filtrer les fichiers en fonction de l’étiquette de classification que vous avez appliquée. Pour plus d’informations sur l’intégration à Azure Information Protection, consultez [Azure information protection Integration](azip-integration.md).

        * **Nom de fichier** : utilisez ce filtre pour appliquer la stratégie à des fichiers spécifiques.
        * **Type de fichier** : utilisez ce filtre pour appliquer la stratégie à des types de fichiers spécifiques, par exemple, bloquer le téléchargement pour tous les fichiers. xls.
    2. Dans la section **inspection du contenu** , indiquez si vous souhaitez activer le moteur DLP pour analyser les documents et le contenu des fichiers.

    3. Sous **actions**, sélectionnez l’un des éléments suivants :

        * **Test (surveiller toutes les activités)** : définissez cette action pour autoriser explicitement le téléchargement en fonction des filtres de stratégie que vous définissez.

        * **Bloquer (bloquer le téléchargement de fichiers et surveiller toutes les activités)** : définissez cette action pour bloquer explicitement le téléchargement en fonction des filtres de stratégie que vous définissez. Pour plus d’informations, consultez fonctionnement du [téléchargement de blocs](#block-download).

        * **Protéger (appliquer l’étiquette de classification pour télécharger et surveiller toutes les activités)** : cette option est disponible uniquement si vous avez sélectionné **contrôler le téléchargement du fichier (avec DLP)** sous **stratégie de session**. Si votre organisation utilise Azure Information Protection, vous pouvez définir une **action** pour appliquer un ensemble d’étiquettes de classification dans Azure information protection au fichier. Pour plus d’informations, consultez fonctionnement de [la protection du téléchargement](#protect-download).

1. Vous pouvez **créer une alerte pour chaque événement correspondant avec la gravité de la stratégie** et définir une limite d’alerte. Indiquez si vous souhaitez que l’alerte soit envoyée par courrier électronique, message texte ou les deux.

## <a name="monitor-session"></a>Surveiller toutes les activités

Lorsque vous créez une stratégie de session, chaque session utilisateur qui correspond à la stratégie est redirigée vers le contrôle de session plutôt que directement vers l’application. L’utilisateur verra un avis de surveillance pour lui signaler que ses sessions sont surveillées.

Si vous ne souhaitez pas avertir l’utilisateur qu’il est en cours d’analyse, vous pouvez désactiver le message de notification.

1. Sous l’roue dentée paramètres, sélectionnez **paramètres généraux**.

2. Ensuite, sous **contrôle d’application par accès conditionnel** sélectionnez **analyse utilisateur** et décochez la case **notifier les utilisateurs** .

Pour conserver l’utilisateur au sein de la session, contrôle d’application par accès conditionnel remplace toutes les URL, scripts Java et cookies appropriés dans la session de l’application par Microsoft Cloud App Security URL. Par exemple, si l’application retourne une page avec des liens dont les domaines se terminent par myapp.com, contrôle d’application par accès conditionnel remplace les liens par des domaines se terminant par un nom similaire à myapp.com.us.cas.ms. De cette façon, la session entière est analysée par Microsoft Cloud App Security.

Contrôle d’application par accès conditionnel enregistre les journaux de trafic de chaque session utilisateur qui est acheminée via celui-ci. Les journaux de trafic incluent l’heure, l’adresse IP, l’agent utilisateur, les URL visitées et le nombre d’octets chargés et téléchargés. Ces journaux sont analysés et un rapport continu, **Cloud App Security contrôle d’application par accès conditionnel**, est ajouté à la liste des rapports d’Cloud Discovery dans le tableau de bord Cloud Discovery.

Pour exporter ces journaux :

1. Accédez à paramètres roue dentée, puis cliquez sur **contrôle d’application par accès conditionnel**.
2. Sur le côté droit du tableau, cliquez sur le bouton Exporter.

    ![bouton Exporter](./media/export-button.png)
3. Sélectionnez la plage du rapport, puis cliquez sur **Exporter**. Ce processus peut prendre un certain temps.

Pour télécharger le journal exporté :

1. Une fois le rapport prêt, accédez à **paramètres** , puis **rapports exportés**.
2. Dans le tableau, sélectionnez le rapport approprié dans la liste des **journaux de trafic de contrôle d’application par accès conditionnel** , puis cliquez sur Télécharger.

    ![bouton Télécharger](./media/download-button.png)

## <a name="block-download"></a>Bloquer tous les téléchargements

Lorsque **bloquer** est défini en tant qu' **action** que vous souhaitez effectuer dans la stratégie de session Cloud App Security, contrôle d’application par accès conditionnel empêche un utilisateur de télécharger un fichier conformément aux filtres de fichiers de la stratégie. Un événement de téléchargement est reconnu par Microsoft Cloud App Security pour chaque application quand un utilisateur démarre un téléchargement. Contrôle d’application par accès conditionnel intervient en temps réel pour l’empêcher de s’exécuter. Lorsque le signal est reçu par un utilisateur, contrôle d’application par accès conditionnel renvoie un message de **Téléchargement restreint** à l’utilisateur et remplace le fichier téléchargé par un fichier texte. Le message du fichier texte à l’utilisateur peut être configuré et personnalisé à partir de la stratégie de session.

## <a name="block-activities"></a>Bloquer des activités spécifiques

Lorsque l’option **activités de bloc** est définie sur le **type d’activité**, vous pouvez sélectionner des activités spécifiques à bloquer dans des applications spécifiques. Toutes les activités des applications sélectionnées sont surveillées et signalées dans le journal d’activité. Les activités spécifiques que vous sélectionnez sont bloquées si vous sélectionnez l’action **bloquer** . Les activités spécifiques que vous avez sélectionnées déclenchent des alertes si vous sélectionnez l’action de **test** et si les alertes sont activées.

**Bloquer des activités spécifiques** et les appliquer à des groupes spécifiques pour créer un mode de lecture seule complet pour votre organisation.

## <a name="protect-download"></a>Protéger les fichiers lors du téléchargement

Sélectionnez **bloquer les activités** pour bloquer des activités spécifiques, que vous pouvez trouver à l’aide du filtre **type d’activité** . Toutes les activités des applications sélectionnées sont surveillées (et signalées dans le journal d’activité). Les activités spécifiques que vous sélectionnez sont bloquées si vous sélectionnez l’action **bloquer** . Les activités spécifiques que vous avez sélectionnées déclenchent des alertes si vous sélectionnez l’action de **test** et si les alertes sont activées.

Lorsque l’action **protéger** est définie en tant qu' **action** à effectuer dans la stratégie de session Cloud App Security, contrôle d’application par accès conditionnel applique l’étiquetage et la protection ultérieure d’un fichier en fonction des filtres de fichiers de la stratégie. Les étiquettes sont configurées dans la console Azure Information Protection et la **protection** doit être sélectionnée dans l’étiquette pour qu’elle apparaisse en tant qu’option dans la stratégie de Cloud App Security. Lorsqu’une étiquette est sélectionnée et qu’un fichier est téléchargé qui répond aux critères de la stratégie de Cloud App Security, l’étiquette et la protection correspondante (avec les autorisations) sont appliquées au fichier lors du téléchargement. Le fichier d’origine reste tel quel dans l’application Cloud, tandis que le fichier téléchargé est maintenant protégé. Les utilisateurs qui essaient d’accéder au fichier doivent remplir les conditions d’autorisation déterminées par la protection appliquée.

Cloud App Security prend actuellement en charge l’application d' [étiquettes de classification Azure information protection](azip-integration.md) pour les types de fichiers suivants :

* Word : docm, docx, dotm, dotx
* Excel : xlam, xlsm, xlsx, xltx
* PowerPoint : potm, potx, ppsx, PPSM, pptm, pptx
* PDF
  > [!NOTE]
  > Pour PDF, vous devez utiliser des étiquettes unifiées.

## <a name="protect-upload"></a>Protéger les téléchargements de fichiers sensibles

Lorsque l’opération **contrôler le téléchargement du fichier (avec DLP)** est définie en tant que **type de contrôle de session** dans la stratégie de session Cloud App Security, contrôle d’application par accès conditionnel empêche un utilisateur de télécharger un fichier en fonction des filtres de fichiers de la stratégie. Lorsqu’un événement de chargement est reconnu, contrôle d’application par accès conditionnel intervient en temps réel pour déterminer si le fichier est sensible et doit être protégé. Si le fichier contient des données sensibles et n’a pas d’étiquette appropriée, le téléchargement du fichier est bloqué.

Par exemple, vous pouvez créer une stratégie qui analyse le contenu d’un fichier pour déterminer si elle contient une correspondance de contenu sensible, telle qu’un numéro de sécurité sociale. S’il contient du contenu sensible et qu’il n’est pas étiqueté avec une étiquette confidentielle Azure Information Protection, le téléchargement du fichier est bloqué. Lorsque le fichier est bloqué, vous pouvez [afficher un message personnalisé destiné à l’utilisateur](#educate-protect) pour lui indiquer comment étiqueter le fichier afin de le télécharger. En procédant ainsi, vous vous assurez que les fichiers stockés dans vos applications Cloud sont conformes à vos stratégies.

## <a name="educate-protect"></a>Informer les utilisateurs de la protection des fichiers sensibles

Il est important d’informer les utilisateurs lorsqu’ils sont en violation d’une stratégie, afin qu’ils apprennent à se conformer aux stratégies de votre organisation. Étant donné que chaque entreprise a des besoins et des stratégies uniques, Cloud App Security vous permet de personnaliser les filtres d’une stratégie et le message qu’elle affiche à l’utilisateur lorsqu’une violation est détectée. Vous pouvez fournir des conseils spécifiques à vos utilisateurs, comme fournir des instructions sur l’étiquetage approprié d’un fichier, ou l’inscription d’un appareil non géré, pour s’assurer que les fichiers sont correctement téléchargés.

Par exemple, si un utilisateur charge un fichier sans étiquette Azure Information Protection, un message peut s’afficher, expliquant que le fichier contient du contenu sensible nécessitant une étiquette appropriée. De même, si un utilisateur tente de télécharger un document à partir d’un appareil non géré, un message contenant des instructions sur la façon d’inscrire ce périphérique ou un message fournissant une explication supplémentaire de la raison pour laquelle l’appareil doit être inscrit peut s’afficher.

## <a name="next-steps"></a>Étapes suivantes :

>[!div class="nextstepaction"]
> [« PRÉCÉDENT : intégration et déploiement contrôle d’application par accès conditionnel pour une application »](proxy-deployment-any-app.md)

>[!div class="nextstepaction"]
> [Étape suivante : comment créer une stratégie d’accès»](access-policy-aad.md)

## <a name="see-also"></a>Voir aussi

> [!div class="nextstepaction"]
> [Blocage des téléchargements sur des appareils non gérés à l’aide de Azure AD contrôle d’application par accès conditionnel](use-case-proxy-block-session-aad.md)

[!INCLUDE [Open support ticket](includes/support.md)]  
