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
ms.openlocfilehash: 83bb7ac4d1b75a98f426f97f09d6019befc221ad
ms.sourcegitcommit: 0b929f7c8feed7dfb40d5294179fd5c6fc079614
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "80666430"
---
# <a name="tutorial-protect-files-with-admin-quarantine"></a>Tutoriel : Protéger les fichiers avec la mise en quarantaine administrateur

*S’applique à : Microsoft Cloud App Security*

Les [stratégies de fichier](data-protection-policies.md) sont un excellent outil pour identifier les menaces pesant sur vos stratégies de protection des informations. Par exemple, créez des stratégies de fichier qui recherchent les emplacements où les utilisateurs stockent des informations sensibles, des numéros de carte de crédit et des fichiers ICAP tiers dans votre cloud.

Ce tutoriel vous aide à utiliser Microsoft Cloud App Security pour détecter les fichiers indésirables stockés dans votre cloud qui vous rendent vulnérable, et prendre des mesures immédiates pour bloquer et verrouiller les fichiers qui constituent une menace en utilisant la **mise en quarantaine administrateur** pour protéger vos fichiers dans le cloud, corriger les problèmes et empêcher l’apparition de fuites futures.

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

1. Lorsqu’un fichier correspond à une stratégie, l’option **Mise en quarantaine administrateur** est disponible pour le fichier.

2. Effectuez l’une des actions suivantes pour mettre en quarantaine le fichier :

    * Appliquez manuellement l’action de **mise en quarantaine administrateur** :

    ![action de mise en quarantaine](media/quarantine-action.png)

    * Définissez-la en tant qu’action de mise en quarantaine automatisée dans la stratégie :

    ![mettre en quarantaine automatiquement](media/quarantine-automated.png)

3. Lorsque la **Mise en quarantaine administrateur** est appliqué, les événements suivants se produisent en arrière-plan :

    1. Le fichier d’origine est déplacé vers le dossier de quarantaine administrateur que vous définissez.
    2. Le fichier d’origine est supprimé.
    3. Un fichier tombstone est chargé vers l’emplacement du fichier d’origine.

    ![mise en quarantaine, tombstone](media/quarantine-tombstone.png)

    4. L’utilisateur peut uniquement accéder au fichier tombstone. Dans le fichier, il peut lire les instructions personnalisées fournies par le service informatique et l’ID de corrélation à communiquer au service informatique pour libérer le fichier.

4. Quand vous recevez l’alerte indiquant qu’un fichier a été mis en quarantaine, examinez le fichier dans la page **Alertes** de Cloud App Security :

    ![alertes de mise en quarantaine](media/quarantine-alerts.png)

5. Et aussi dans le **Rapport de stratégie** sous l’onglet **Mis en quarantaine** :

    ![mise en quarantaine, rapport](media/quarantine-report.png)

6. Une fois qu’un fichier est mis en quarantaine, utilisez le processus suivant pour corriger la situation de la menace :

    1. Inspectez le fichier dans le dossier en quarantaine sur SharePoint Online.
    2. Vous pouvez également consulter les journaux d’audit pour explorer en détail les propriétés du fichier.
    3. Si vous trouvez que le fichier va à l’encontre de la stratégie d’entreprise, exécutez le processus de réponse aux incidents de l’organisation.
    4. Si vous constatez que le fichier est inoffensif, vous pouvez le restaurer à partir de la mise en quarantaine. À ce stade, le fichier d’origine est libéré, ce qui signifie qu’il est copié dans l’emplacement d’origine, que l’objet tombstone est supprimé et que l’utilisateur peut accéder au fichier.

      ![mise en quarantaine, restaurer](media/quarantine-restore.png)

7. Vérifiez que la stratégie s’exécute correctement. Ensuite, vous pouvez utiliser les actions de gouvernance automatiques dans la stratégie pour éviter d’autres fuites et appliquer automatiquement une mise en quarantaine administrateur lorsque la stratégie est mise en correspondance.

> [!NOTE]
> Lorsque vous restaurez un fichier :
>
> * Les partages d’origine ne sont pas restaurés, l’héritage de dossier par défaut est appliqué.
> * Le fichier restauré contient uniquement la version la plus récente.
> * La gestion de l’accès au site du dossier de quarantaine est la responsabilité du client.

## <a name="set-up-admin-quarantine"></a>Configurer la mise en quarantaine administrateur

1. Définissez des stratégies de fichier qui détectent les violations. Voici quelques exemples de ces stratégies :

    - Stratégie de métadonnées uniquement, telle qu’une étiquette de classification dans SharePoint Online
    - Stratégie DLP native, telle qu’une stratégie qui recherche des numéros de carte de crédit
    - Une stratégie de tiers ICAP comme une stratégie qui recherche Vontu

2. Définissez un emplacement de quarantaine :
   1. Pour Office 365 SharePoint ou OneDrive Entreprise, vous ne pouvez pas mettre de fichiers en quarantaine administrateur dans le cadre d’une stratégie tant que vous ne l’avez pas configurée : ![paramètres de mise en quarantaine](media/quarantine-warning.png)

      Pour définir les paramètres de mise en quarantaine administrateur, sous la roue dentée des paramètres, accédez à **Paramètres**. Indiquez un emplacement pour les fichiers mis en quarantaine et une notification utilisateur que votre utilisateur recevra lorsque son fichier sera mis en quarantaine.
      ![paramètres de quarantaine](media/quarantine-settings.png)

   2. Pour Box, l’emplacement du dossier de quarantaine et le message à l’utilisateur ne peuvent pas être personnalisés. L’emplacement du dossier est le lecteur de l’administrateur qui a connecté Box à Cloud App Security et le message utilisateur est le suivant : Ce fichier a été mis en quarantaine dans votre lecteur administrateur, car il peut violer les politiques de sécurité et de conformité de votre entreprise. Contactez votre administrateur informatique pour obtenir de l’aide.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
