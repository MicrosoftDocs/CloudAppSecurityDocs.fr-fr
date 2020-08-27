---
title: Créer des stratégies de session dans Cloud App Security
description: Cet article décrit la procédure de configuration d’une stratégie de session du contrôle d'application par accès conditionnel de Cloud App Security pour améliorer la visibilité des activités de session utilisateur et bloquer les téléchargements à l’aide des fonctionnalités de proxy inverse.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/31/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 3fc036277fac599f3075cd3c9cf765a0623e79a9
ms.sourcegitcommit: 870ca47381a36b4bc04e1ccb9b2a522944431fed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88963928"
---
# <a name="session-policies"></a>Stratégies de session

*S’applique à : Microsoft Cloud App Security*

Les stratégies de session Microsoft Cloud App Security permettent une surveillance en temps réel au niveau de la session, qui vous offre une visibilité plus précise des applications cloud et la possibilité de prendre différentes mesures selon la stratégie que vous définissez pour une session utilisateur. Au lieu [d’autoriser ou de bloquer complètement l’accès](access-policy-aad.md), avec le contrôle de session, vous pouvez autoriser l’accès pendant la surveillance de la session et/ou limiter des activités de session particulières à l’aide des fonctionnalités du proxy inversé du Contrôle d’accès conditionnel aux applications.

Par exemple, vous pouvez décider que pour les appareils non gérés ou pour les sessions provenant d’emplacements spécifiques, vous voulez autoriser l’utilisateur à accéder à l’application, mais aussi limiter le téléchargement des fichiers sensibles ou exiger que certains documents soient protégés lors de leur téléchargement. Les stratégies de session vous permettent de définir ces contrôles de session utilisateur, d’autoriser l’accès et de :

* [Analyser toutes les activités](#monitor-session)
* [Bloquer tous les téléchargements](#block-download)
* [Bloquer des activités spécifiques](#block-activities)
* [Protéger les fichiers lors du téléchargement](#protect-download)
* [Protéger les téléchargements de fichiers sensibles](#protect-upload)
* [Bloquer les logiciels malveillants lors du téléchargement](#block-malware-on-upload)
* [Informer les utilisateurs de la protection des fichiers sensibles](#educate-protect)

## <a name="prerequisites-to-using-session-policies"></a>Prérequis à l’utilisation de stratégies de session

* Azure AD Premium licence P1 ou la licence requise par votre solution de fournisseur d’identité (IdP)
* Les applications appropriées doivent être [déployées avec le Contrôle d’accès conditionnel aux applications](proxy-deployment-aad.md)
* Configurez votre solution de fournisseur d’identité pour qu’elle fonctionne avec Cloud App Security :
  * Pour [l’accès conditionnel Azure AD](/azure/active-directory/active-directory-conditional-access-azure-portal), consultez [Configuration de l’intégration avec Azure AD](proxy-deployment-aad.md#configure-integration-with-azure-ad).
  * Pour les autres solutions de fournisseur d’identité, consultez [Configuration de l’intégration avec d’autres solutions de fournisseur d’identité](proxy-deployment-aad.md#configure-integration-with-other-idp-solutions).

## <a name="create-a-cloud-app-security-session-policy"></a>Créer une stratégie de session Cloud App Security

Pour créer une stratégie de session, suivez cette procédure :

1. Dans le portail, sélectionnez **Contrôle**, puis **Stratégies**.
1. Dans la page **Stratégies**, cliquez sur **Créer une stratégie** et sélectionnez **Stratégie de session**.
1. Dans la fenêtre **Stratégie de session**, donnez un nom à votre stratégie, comme *Bloquer le téléchargement des documents sensibles dans Box pour les utilisateurs du service marketing*.
1. Dans le champ **Type de contrôle de session** :

    1. Sélectionnez **Surveiller uniquement** pour surveiller uniquement les activités des utilisateurs. De cette façon, vous créez une stratégie de type « Superviser uniquement », dans laquelle toutes les connexions, tous les téléchargements heuristiques et tous les types d’activités sont téléchargés pour les applications que vous avez sélectionnées.

    1. Sélectionnez **contrôler le téléchargement du fichier (avec inspection)** si vous souhaitez surveiller les activités des utilisateurs. Vous pouvez exécuter des actions supplémentaires, comme bloquer ou protéger les téléchargements pour les utilisateurs.
    1. Sélectionnez **Bloquer les activités** pour bloquer certaines activités, que vous pouvez sélectionner à l’aide du filtre **Type d’activité**. Toutes les activités des applications sélectionnées sont surveillées (et signalées dans le journal d’activité). Les activités que vous sélectionnez sont bloquées si vous sélectionnez l’action **Bloquer**. Les activités que vous avez sélectionnées déclencheront des alertes si vous sélectionnez l’action **Tester** et si vous activez les alertes.
1. Sous **Source de l’activité** dans la section **Activités remplissant toutes les conditions suivantes**, sélectionnez d’autres filtres d’activité à appliquer à la stratégie. Ces filtres peuvent inclure les options suivantes :

    * **Balise de l’appareil** : Utilisez ce filtre pour identifier les appareils non gérés.

    * **Emplacement** : Utilisez ce filtre pour identifier les emplacements inconnus (et par conséquent à risque).

    * **Adresse IP** : Utilisez ce filtre pour filtrer selon des adresses IP ou utiliser des balises d’adresse IP déjà attribuées.

    * **Étiquette agent utilisateur** : Utilisez ce filtre pour activer l’heuristique afin d’identifier les applications mobiles et de bureau. Ce filtre peut être défini de manière à être égal ou différent de **Client natif**. Ce filtre doit être testé sur vos applications mobiles et de bureau pour chacune des applications cloud.

    >[!NOTE]
    >Les stratégies de session ne prennent pas en charge les applications mobiles et de bureau. Les applications mobiles et les applications de bureau peuvent également être bloquées ou autorisées en créant une stratégie d’accès.

1. Si vous avez sélectionné l’option permettant de **contrôler le téléchargement de fichiers (avec inspection)**:

    1. Sous **Source de l’activité** dans la section **Fichiers remplissant toutes les conditions suivantes**, sélectionnez d’autres filtres de fichiers à appliquer à la stratégie. Ces filtres peuvent inclure les options suivantes :

        * **Étiquette de classification** : utilisez ce filtre si votre organisation utilise Azure information protection et que vos données ont été protégées par ses étiquettes de classification. Vous pouvez filtrer des fichiers en fonction de l’étiquette de classification que vous leur avez appliquée. Pour plus d’informations sur l’intégration à Azure Information Protection, consultez [Intégration à Azure Information Protection](azip-integration.md).

        * **Nom de fichier** : Utilisez ce filtre pour appliquer la stratégie à des fichiers spécifiques.
        * **Type de fichier** : Utilisez ce filtre pour appliquer la stratégie à des types de fichiers spécifiques, par exemple, pour bloquer le téléchargement de tous les fichiers .xls.
    2. Dans la section **Inspection du contenu**, indiquez si vous voulez activer le moteur DLP pour analyser les documents et le contenu des fichiers.

    3. Sous **Actions**, sélectionnez l’un des éléments suivants :

        * **Tester (Surveiller toutes les activités)**  : définissez cette action pour autoriser explicitement le téléchargement selon les filtres de stratégie que vous définissez.

        * **Bloquer (Bloquer le téléchargement de fichiers et surveiller toutes les activités)**  : définissez cette action pour bloquer explicitement le téléchargement selon les filtres de stratégie que vous définissez. Pour plus d’informations, consultez [Fonctionnement du blocage du téléchargement](#block-download).

        * **Protéger (appliquer l’étiquette de classification pour télécharger et surveiller toutes les activités)**: cette option est disponible uniquement si vous avez sélectionné **contrôler le téléchargement de fichiers (avec inspection)** sous **stratégie de session**. Si votre organisation utilise Azure Information Protection, vous pouvez définir une **action** pour appliquer une étiquette de classification définie dans Azure Information Protection sur le fichier. Pour plus d’informations, consultez [Fonctionnement de la protection du téléchargement](#protect-download).

1. Vous pouvez **Créer une alerte pour chaque événement correspondant avec le niveau de gravité de la stratégie** et définir un seuil d’alerte. Choisissez si l’alerte doit être envoyée par e-mail, par SMS, ou les deux.

## <a name="monitor-all-activities"></a><a name="monitor-session"></a>Analyser toutes les activités

Quand vous créez une stratégie de session, chaque session utilisateur qui correspond à la stratégie est redirigée vers le contrôle de session plutôt que directement vers l’application. L’utilisateur reçoit une notification de surveillance qui l’informe que ses sessions sont surveillées.

Si vous ne voulez pas en informer l’utilisateur, vous pouvez désactiver le message de notification.

1. Sous la roue dentée des paramètres, sélectionnez **Paramètres généraux**.

2. Puis, sous **Contrôle d’accès conditionnel aux applications**, sélectionnez **Suivi des utilisateurs** et décochez la case **Aviser les utilisateurs**.

Pour garder l’utilisateur dans la session, le Contrôle d’accès conditionnel aux applications remplace tous les URL, scripts de Java et cookies appropriés dans la session de l’application par des URL de Contrôle d’accès conditionnel aux applications. Par exemple, si l’application retourne une page avec des liens dont les domaines se terminent par myapp.com, contrôle d’application par accès conditionnel remplace les liens par des domaines se terminant par un nom similaire à `myapp.com.mcas.ms` . Ainsi, la session entière est surveillée par Microsoft Cloud App Security.

Le Contrôle d’accès conditionnel aux applications enregistre les journaux de trafic de chaque session utilisateur acheminée vers lui. Les journaux de trafic incluent l’heure, l’adresse IP, l’agent utilisateur, les URL visitées et le nombre d’octets chargés et téléchargés. Ces journaux sont analysés et un rapport continu (**Contrôle d’application par accès conditionnel Cloud App Security**) est ajouté à la liste des rapports Cloud Discovery dans le tableau de bord Cloud Discovery.

Pour exporter ces journaux :

1. Accédez à la roue dentée des paramètres et cliquez sur **Contrôle d’accès conditionnel aux applications**.
2. Sur le côté droit du tableau, cliquez sur le bouton d’exportation.

    ![bouton exporter](media/export-button.png)
3. Sélectionnez la plage du rapport et cliquez sur **Exporter**. Ce processus peut prendre un certain temps.

Pour télécharger le journal exporté :

1. Une fois que le rapport est prêt, accédez à **Paramètres**, puis à **Rapports exportés**.
2. Dans le tableau, sélectionnez le rapport approprié dans la liste des **journaux du trafic du Contrôle d’application par accès conditionnel**, puis cliquez sur Télécharger.

    ![bouton de téléchargement](media/download-button.png)

## <a name="block-all-downloads"></a><a name="block-download"></a>Bloquer tous les téléchargements

Lorsque **bloquer** est défini en tant qu' **action** que vous souhaitez effectuer dans la stratégie de session Cloud App Security, contrôle d’application par accès conditionnel empêche un utilisateur de télécharger un fichier conformément aux filtres de fichiers de la stratégie. Un événement de téléchargement est reconnu par Microsoft Cloud App Security pour chaque application lorsqu’un utilisateur démarre un téléchargement. Le contrôle d’application par accès conditionnel intervient en temps réel pour en empêcher l’exécution. À la réception d’un signal de téléchargement par un utilisateur, le contrôle d’application par accès conditionnel retourne le message **Téléchargement restreint**, et remplace le fichier téléchargé par un fichier texte. Le message du fichier texte peut être configuré et personnalisé dans la stratégie de session.

## <a name="block-specific-activities"></a><a name="block-activities"></a>Bloquer des activités spécifiques

Quand l’option **Bloquer les activités** est définie pour le **Type d’activité**, vous pouvez sélectionner des activités spécifiques à bloquer dans des applications spécifiques. Toutes les activités des applications sélectionnées sont supervisées et signalées dans le journal d’activité. Les activités que vous sélectionnez sont bloquées si vous sélectionnez l’action **Bloquer**. Les activités que vous avez sélectionnées déclencheront des alertes si vous sélectionnez l’action **Tester** et si vous activez les alertes.

**Bloquez des activités** et appliquez ce blocage à certains groupes afin d’appliquer globalement un mode en lecture seule à l’échelle de votre organisation.

## <a name="protect-files-on-download"></a><a name="protect-download"></a>Protéger les fichiers lors du téléchargement

Sélectionnez **Bloquer les activités** pour bloquer certaines activités, que vous pouvez sélectionner à l’aide du filtre **Type d’activité**. Toutes les activités des applications sélectionnées sont supervisées (et signalées dans le journal d’activité). Les activités que vous sélectionnez sont bloquées si vous sélectionnez l’action **Bloquer**. Les activités que vous avez sélectionnées déclencheront des alertes si vous sélectionnez l’action **Tester** et si vous activez les alertes.

Lorsque l’action **protéger** est définie en tant qu' **action** à effectuer dans la stratégie de session Cloud App Security, contrôle d’application par accès conditionnel applique l’étiquetage et la protection ultérieure d’un fichier en fonction des filtres de fichiers de la stratégie. Les étiquettes sont configurées dans la console Azure Information Protection, et l’option **Protéger** doit être sélectionnée dans l’étiquette pour qu’elle apparaisse en tant qu’option dans la stratégie Cloud App Security. Quand une étiquette est sélectionnée et qu’un fichier correspondant aux critères de la stratégie Cloud App Security est téléchargé, l’étiquette et la protection correspondante (avec les autorisations) sont appliquées au fichier lors de son téléchargement. Le fichier original reste inchangé dans l’application cloud, tandis que le fichier téléchargé est désormais protégé. Les utilisateurs qui tentent d’accéder au fichier doivent respecter les exigences d’autorisation déterminées par la protection appliquée.

Cloud App Security prend actuellement en charge l’application d' [étiquettes de classification Azure information protection](azip-integration.md) pour les types de fichiers suivants :

* Word : docm, docx, dotm, dotx
* Excel : xlam, xlsm, xlsx, xltx
* PowerPoint : potm, potx, ppsx, ppsm, pptm, pptx
* PDF
  > [!NOTE]
  > Pour PDF, vous devez utiliser des étiquettes unifiées.

## <a name="protect-uploads-of-sensitive-files"></a><a name="protect-upload"></a>Protéger les téléchargements de fichiers sensibles

Lorsque le **chargement du fichier de contrôle (avec inspection)** est défini en tant que **type de contrôle de session** dans la stratégie de session Cloud App Security, contrôle d’application par accès conditionnel empêche un utilisateur de télécharger un fichier en fonction des filtres de fichiers de la stratégie. Lorsqu’un événement de chargement est reconnu, contrôle d’application par accès conditionnel intervient en temps réel pour déterminer si le fichier est sensible et doit être protégé. Si le fichier contient des données sensibles et n’a pas d’étiquette appropriée, le téléchargement du fichier est bloqué.

Par exemple, vous pouvez créer une stratégie qui analyse le contenu d’un fichier pour déterminer si elle contient une correspondance de contenu sensible, telle qu’un numéro de sécurité sociale. S’il contient du contenu sensible et qu’il n’est pas étiqueté avec une étiquette confidentielle Azure Information Protection, le téléchargement du fichier est bloqué. Lorsque le fichier est bloqué, vous pouvez [afficher un message personnalisé destiné à l’utilisateur](#educate-protect) pour lui indiquer comment étiqueter le fichier afin de le télécharger. En procédant ainsi, vous vous assurez que les fichiers stockés dans vos applications Cloud sont conformes à vos stratégies.

## <a name="block-malware-on-upload"></a>Bloquer les logiciels malveillants lors du téléchargement

Lorsque le **contrôle de téléchargement de fichier (avec inspection)**   est défini comme **type de contrôle de session** et que la détection de **programmes malveillants** est définie comme **méthode d’inspection** dans la stratégie de session de Cloud App Security, contrôle d’application par accès conditionnel empêche un utilisateur de charger un fichier en temps réel si un logiciel malveillant est détecté. Les fichiers sont analysés à l’aide du moteur Microsoft Threat Intelligence.

Vous pouvez afficher les fichiers signalés comme programmes malveillants potentiels à l’aide du filtre **potentiellement malveillant détecté** dans le journal d’activité.

Vous pouvez également configurer des stratégies de session pour bloquer les logiciels malveillants au téléchargement.

## <a name="educate-users-to-protect-sensitive-files"></a><a name="educate-protect"></a>Informer les utilisateurs de la protection des fichiers sensibles

Il est important d’informer les utilisateurs lorsqu’ils sont en violation d’une stratégie, afin qu’ils apprennent à se conformer aux stratégies de votre organisation. Étant donné que chaque entreprise a des besoins et des stratégies uniques, Cloud App Security vous permet de personnaliser les filtres d’une stratégie et le message qu’elle affiche à l’utilisateur lorsqu’une violation est détectée. Vous pouvez fournir des conseils spécifiques à vos utilisateurs, comme fournir des instructions sur l’étiquetage approprié d’un fichier, ou l’inscription d’un appareil non géré, pour s’assurer que les fichiers sont correctement téléchargés.

Par exemple, si un utilisateur charge un fichier sans étiquette Azure Information Protection, un message peut s’afficher, expliquant que le fichier contient du contenu sensible nécessitant une étiquette appropriée. De même, si un utilisateur tente de télécharger un document à partir d’un appareil non géré, un message contenant des instructions sur la façon d’inscrire ce périphérique ou un message fournissant une explication supplémentaire de la raison pour laquelle l’appareil doit être inscrit peut s’afficher.

## <a name="next-steps"></a>Étapes suivantes

>[!div class="nextstepaction"]
> [« PRÉCÉDENT : intégration et déploiement contrôle d’application par accès conditionnel pour une application »](proxy-deployment-any-app.md)

>[!div class="nextstepaction"]
> [SUIVANT : Guide pratique pour créer une stratégie d’accès »](access-policy-aad.md)

> [!div class="nextstepaction"]
> [Résolution des problèmes de contrôles d’accès et de session](troubleshooting-proxy.md)

## <a name="see-also"></a>Voir aussi

> [!div class="nextstepaction"]
> [Blocage des téléchargements sur des appareils non gérés à l’aide de Azure AD contrôle d’application par accès conditionnel](use-case-proxy-block-session-aad.md)

[!INCLUDE [Open support ticket](includes/support.md)]