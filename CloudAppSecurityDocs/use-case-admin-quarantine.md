---
title: Protéger les fichiers avec la mise en quarantaine administrateur Cloud App Security
description: Ce tutoriel décrit le scénario d’utilisation de la mise en quarantaine administrateur pour contrôler les violations de données.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 7/30/2019
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 2835a0f8bc66f937d8569c327c5fd61c0e6ebac9
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90881161"
---
# <a name="tutorial-protect-files-with-admin-quarantine"></a>Tutoriel : Protéger les fichiers avec la mise en quarantaine administrateur

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Les [stratégies de fichier](data-protection-policies.md) sont un excellent outil pour rechercher les menaces sur vos stratégies de protection des informations. Par exemple, créez des stratégies de fichier qui recherchent les emplacements où les utilisateurs ont stocké des informations sensibles, des numéros de carte de crédit et des fichiers ICAP tiers dans votre cloud.

Ce tutoriel vous aide à utiliser Microsoft Cloud App Security pour détecter les fichiers indésirables stockés dans votre cloud qui vous rendent vulnérable, et vous aider à prendre des mesures immédiates pour les arrêter et verrouiller les fichiers qui représentent une menace à l’aide de la **mise en quarantaine administrateur ** pour protéger vos fichiers dans le cloud, corriger les problèmes et empêcher les fuites futures.

> [!div class="checklist"]
>
> * Comprendre le fonctionnement de la mise en quarantaine
> * Configurer la mise en quarantaine administrateur

## <a name="understand-how-quarantine-works"></a>Comprendre le fonctionnement de la mise en quarantaine

>[!NOTE]
>
> * Pour obtenir la liste des applications qui prennent en charge la mise en quarantaine administrateur, consultez la liste des [actions de gouvernance](governance-actions.md).
> * Si un fichier dans SharePoint ou OneDrive est détecté comme étant un logiciel malveillant, il n'est pas mis en quarantaine dans le portail Cloud App Security.
> * Les fichiers avec des étiquettes ne peuvent pas être mis en quarantaine.

1. Quand un fichier correspond à une stratégie, l’option **Mise en quarantaine administrateur** est disponible pour le fichier.

2. Effectuez l’une des actions suivantes pour mettre en quarantaine le fichier :

    * Appliquez manuellement l’option **Mise en quarantaine administrateur** :

    ![action de mise en quarantaine](media/quarantine-action.png)

    * Définissez-la comme une action de mise en quarantaine automatique dans la stratégie :

    ![mettre en quarantaine automatiquement](media/quarantine-automated.png)

3. Lorsque l’option **Mise en quarantaine administrateur** est appliquée, les actions suivantes se produisent en arrière-plan :

    1. Le fichier d’origine est déplacé vers le dossier de quarantaine administrateur que vous définissez.
    2. Le fichier d'origine est supprimé.
    3. Un fichier résiduel est chargé dans l’emplacement du fichier d’origine.

    ![fichier résiduel mis en quarantaine](media/quarantine-tombstone.png)

    4. L’utilisateur a accès uniquement au fichier résiduel. Dans le fichier, il peut retrouver les instructions personnalisées fournies par le service informatique et l’ID de corrélation permettant au service informatique de libérer le fichier.

4. Quand vous recevez l’alerte qu’un fichier a été mis en quarantaine, recherchez le fichier dans la page **Alertes** de Cloud App Security :

    ![alertes de mise en quarantaine](media/quarantine-alerts.png)

5. Ainsi que dans le **Rapport de stratégie** sous l’onglet **Mis en quarantaine** :

    ![rapport de mise en quarantaine](media/quarantine-report.png)

6. Une fois qu’un fichier est en quarantaine, utilisez le processus suivant pour corriger la situation de menace :

    1. Examinez le fichier dans le dossier de quarantaine sur SharePoint Online.
    2. Vous pouvez également consulter les journaux d’audit pour un examen approfondi des propriétés du fichier.
    3. Si vous trouvez que le fichier va à l’encontre de la stratégie d’entreprise, exécutez le processus de réponse aux incidents de l’organisation.
    4. Si vous pensez que le fichier est inoffensif, vous pouvez le restaurer de la quarantaine. À ce stade, le fichier d’origine est libéré, ce qui signifie qu’il est recopié vers l’emplacement d’origine, que l’objet résiduel est supprimé et que l’utilisateur peut accéder au fichier.

      ![restauration après quarantaine](media/quarantine-restore.png)

7. Validez la bonne exécution de la stratégie. Vous pouvez ensuite utiliser les actions de gouvernance automatiques de la stratégie pour éviter d’autres fuites et appliquer automatiquement la mise en quarantaine administrateur lorsque la stratégie trouve une correspondance.

> [!NOTE]
> Quand vous restaurez un fichier :
>
> * Les partages d’origine ne sont pas restaurés, l’héritage de dossier par défaut est appliqué.
> * Le fichier restauré contient uniquement la version la plus récente.
> * La gestion de l’accès au site du dossier de quarantaine est la responsabilité du client.

## <a name="set-up-admin-quarantine"></a>Configurer la mise en quarantaine administrateur

1. Définissez des stratégies de fichier qui détectent les violations. Voici quelques exemples de ces types de stratégies :

    - Une stratégie de métadonnées uniquement comme une étiquette de classification dans SharePoint Online
    - Une stratégie DLP native comme une stratégie qui recherche des numéros de carte de crédit
    - Une stratégie de tiers ICAP comme une stratégie qui recherche Vontu

2. Définir un emplacement de mise en quarantaine :
   1. Pour Office 365 SharePoint ou OneDrive Entreprise, vous ne pouvez pas mettre de fichiers en quarantaine administrateur dans le cadre d’une stratégie tant que vous ne l’avez pas configurée : ![avertissement de mise en quarantaine](media/quarantine-warning.png)

      Pour définir des paramètres de mise en quarantaine, sous la roue dentée des paramètres, accédez à **Paramètres**. Indiquez un emplacement pour les fichiers en quarantaine ainsi qu’une notification à l’utilisateur lui indiquant que son fichier est mis en quarantaine.
      ![paramètres de mise en quarantaine](media/quarantine-settings.png)

   2. Pour Box, l’emplacement du dossier de mise en quarantaine et le message à l’utilisateur ne peuvent pas être personnalisés. L’emplacement du dossier est le lecteur de l’administrateur qui a connecté Box à Cloud App Security et le message à l’utilisateur est : Ce fichier a été mis en quarantaine sur le lecteur de l’administrateur, car il est susceptible de violer les stratégies de conformité et de sécurité de votre société. Contactez votre administrateur informatique pour obtenir de l’aide.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
