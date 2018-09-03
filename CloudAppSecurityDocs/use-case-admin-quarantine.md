---
title: Cas d’utilisation permettant d’examiner et de corriger les violations de fichier à l’aide de la mise en quarantaine administrateur | Microsoft Docs
description: Cette rubrique décrit le scénario d’utilisation de la mise en quarantaine administrateur pour contrôler les violations de données.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 3fc04cfb-ad4c-4ac2-980a-ee9f4c740d88
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 38faca2d4d8da2802ca0043bf53564d840645523
ms.sourcegitcommit: 1744ef45b9c5ac8e08b3489bb9b73fc1347587ac
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2018
ms.locfileid: "31773091"
---
*S’applique à : Microsoft Cloud App Security*


# <a name="protecting-your-files-with-admin-quarantine"></a>Protection de vos fichiers avec la mise en quarantaine administrateur

> [!NOTE]
> Il s’agit d’une fonctionnalité en préversion.

Les [stratégies de fichier](data-protection-policies.md) sont un excellent outil pour rechercher les menaces dans le cadre de vos stratégies de protection des informations, par exemple, rechercher les emplacements où les utilisateurs ont stocké des informations sensibles, des numéros de carte de crédit et des fichiers ICAP tiers dans votre cloud. Avec Microsoft Cloud App Security, non seulement vous pouvez détecter ces fichiers indésirables stockés dans votre cloud qui vous rendent vulnérable, mais vous pouvez aussi prendre des mesures immédiates pour les arrêter dans leur action et verrouiller les fichiers qui représentent une menace. La **Mise en quarantaine administrateur** vous permet de protéger vos fichiers dans le cloud et de corriger les problèmes, ainsi que d’éviter que des fuites se produisent à l’avenir. 

>[!NOTE] 
> Pour obtenir la liste des applications qui prennent en charge la mise en quarantaine administrateur, consultez la liste des [actions de gouvernance](governance-actions.md).
 
## <a name="how-quarantine-works"></a>Comment fonctionne la mise en quarantaine 

1. Quand un fichier correspond à une stratégie, l’option **Mise en quarantaine administrateur** est disponible pour le fichier.

2. Effectuez l’une des opérations suivantes pour mettre en quarantaine le fichier :
   - Appliquez manuellement l’option **Mise en quarantaine administrateur** :
     
     ![action de mise en quarantaine](./media/quarantine-action.png)

   - Définissez-la comme une action de mise en quarantaine automatique dans la stratégie : 

     ![mettre en quarantaine automatiquement](./media/quarantine-automated.png)

3. Quand l’option **Mise en quarantaine administrateur** est appliquée, les opérations suivantes se produisent en arrière-plan :

   1. Le fichier d’origine est déplacé vers le dossier de quarantaine administrateur que vous définissez.
   2. Le fichier d'origine est supprimé.
   3. Un fichier résiduel est chargé dans l’emplacement du fichier d’origine.

      ![fichier résiduel mis en quarantaine](./media/quarantine-tombstone.png)

   4. L’utilisateur a accès uniquement au fichier résiduel, où se trouvent les instructions personnalisées fournies par le service informatique et l’ID de corrélation permettant de contacter le service informatique pour libérer le fichier.

4. Quand vous recevez l’alerte qu’un fichier a été mis en quarantaine, recherchez le fichier dans la page **Alertes** de Cloud App Security :

   ![alertes de mise en quarantaine](./media/quarantine-alerts.png)
 
5. Ainsi que dans le **Rapport de stratégie** sous l’onglet **Mis en quarantaine** :

   ![rapport de mise en quarantaine](./media/quarantine-report.png)
    
6. Une fois qu’un fichier est en quarantaine, utilisez le processus suivant pour corriger la situation de menace :
       
    1. Examinez le fichier dans le dossier de quarantaine sur SharePoint Online.
    3. Vous pouvez également consulter les journaux d’audit pour un examen approfondi des propriétés du fichier.
    4. Si le fichier va à l’encontre de la stratégie d’entreprise, exécutez le processus de réponse aux incidents applicable dans l’organisation.
    5. Si le fichier est inoffensif, vous pouvez le restaurer à partir du dossier de quarantaine, ce qui entraîne la libération du fichier d’origine. Autrement dit, il est copié dans l’emplacement d’origine, le fichier résiduel est supprimé et l’utilisateur peut accéder au fichier.
       ![restauration après quarantaine](./media/quarantine-restore.png)
7. Une fois que vous avez validé que la stratégie s’exécute correctement, vous pouvez utiliser les actions de gouvernance automatiques de la stratégie pour éviter d’autres fuites et appliquer automatiquement la mise en quarantaine administrateur quand la stratégie trouve une correspondance.

> [!NOTE]
> Quand vous restaurez un fichier :
> - Les partages d’origine ne sont pas restaurés, l’héritage de dossier par défaut est appliqué.
> - Le fichier restauré contient uniquement la version la plus récente.
> 
> 
> [!NOTE]
> La gestion de l’accès au site du dossier de quarantaine est la responsabilité du client.

#### <a name="how-to-set-up-admin-quarantine"></a>Comment configurer la mise en quarantaine administrateur

1. Définissez des stratégies de fichier qui détectent les violations, comme une stratégie de métadonnées uniquement (par exemple, une étiquette de classification dans SharePoint Online), une stratégie DLP native (par exemple, une stratégie qui recherche des numéros de carte de crédit) ou une stratégie ICAP tierce (par exemple, une stratégie qui recherche Vontu).

2. Définir un emplacement de mise en quarantaine :
   1. Pour Office 365 SharePoint ou OneDrive Entreprise, avant de configurer la mise en quarantaine administrateur, vous ne pouvez pas mettre de fichiers en quarantaine administrateur dans le cadre d’une stratégie : ![paramètres de mise en quarantaine](./media/quarantine-warning.png)

      Pour définir des paramètres de mise en quarantaine, dans le menu des paramètres (roue dentée), accédez à **Paramètres généraux** et indiquez un emplacement pour les fichiers en quarantaine ainsi qu’une notification à l’utilisateur lui indiquant que son fichier est mis en quarantaine. 
      ![paramètres de mise en quarantaine](./media/quarantine-settings.png)

   2. Pour Box, l’emplacement du dossier de mise en quarantaine et le message à l’utilisateur ne peuvent pas être personnalisés. L’emplacement du dossier est le lecteur de l’administrateur qui a connecté Box à Cloud App Security et le message à l’utilisateur est : Ce fichier a été mis en quarantaine sur le lecteur de l’administrateur, car il est susceptible de violer les stratégies de conformité et de sécurité de votre société. Contactez votre administrateur informatique pour obtenir de l’aide.



## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  