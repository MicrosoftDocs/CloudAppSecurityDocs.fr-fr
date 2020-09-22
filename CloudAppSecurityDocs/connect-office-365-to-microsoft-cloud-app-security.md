---
title: Connecter Office 365 à Cloud App Security
description: Cet article vous explique comment connecter votre application Office 365 à Cloud App Security à l’aide du connecteur d’API, afin de bénéficier de plus de contrôle et de visibilité lors de l’utilisation.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 08/17/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: d50d185ce75b5ca301dd55681c11fbca8039491e
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90881337"
---
# <a name="connect-office-365-to-microsoft-cloud-app-security"></a>Connecter Office 365 à Microsoft Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Cet article fournit des instructions pour connecter Microsoft Cloud App Security à votre compte Office 365 existant à l’aide de l’API du connecteur d’applications. Cette connexion vous permet de bénéficier de plus de visibilité et de contrôle lors de l’utilisation d’Office 365. Pour plus d’informations sur la façon dont Cloud App Security protège Office 365, consultez [protéger office 365](protect-office-365.md).
  
Cloud App Security prend en charge la plateforme dédiée Office 365 héritée, ainsi que les dernières offres de services Office 365 (communément appelés la famille de mises en production vNext d’Office 365).  Cloud App Security ne prend pas en charge la suite héritée Microsoft Business Productivity Online Standard Suite (BPOS).

> [!NOTE]
> Dans certains cas, une mise en production de service vNext diffère légèrement de l’offre Office 365 standard sur les plans de l’administration et de la gestion.

Cloud App Security prend en charge les applications Office 365 suivantes :

- Dynamics 365 CRM
- Exchange (apparaît uniquement une fois que des activités Exchange sont détectées dans le portail et nécessite l’activation de l’audit)
- Office
- OneDrive Entreprise
- Power Automate
- Power BI (apparaît seulement une fois que des activités Power BI sont détectées dans le portail, et nécessite l’activation de l’audit)
- SharePoint
- Skype Entreprise
- Teams (apparaît uniquement une fois que des activités Teams sont détectées dans le portail)
- Yammer

> [!NOTE]
> Cloud App Security s’intègre directement avec les [journaux d’audit d’Office 365](/microsoft-365/compliance/detailed-properties-in-the-office-365-audit-log?view=o365-worldwide&preserve-view=true) et reçoit tous les événements audités de **tous les services pris en charge**, tels que powerapps, Forms, Sway et Stream.

## <a name="how-to-connect-office-365-to-cloud-app-security"></a>Comment connecter Office 365 à Cloud App Security  

> [!NOTE]
>
>- Vous devez disposer d’au moins une licence Office 365 pour connecter Office 365 à Cloud App Security.
>- Pour activer l’analyse des activités Office 365 dans Cloud App Security, vous devez activer l’audit dans le [Centre de sécurité et conformité Office](https://support.microsoft.com/help/4026501/office-auditing-in-office-365-for-admins).
>- La journalisation d’audit de l’administrateur Exchange, qui est activée par défaut dans Office 365, consigne un événement dans le journal d’audit Office 365 quand un administrateur (ou un utilisateur qui a reçu des privilèges d’administrateur) apporte une modification dans votre organisation Exchange Online. Les modifications apportées en utilisant le Centre d’administration Exchange ou en exécutant une applet de commande dans Windows PowerShell sont enregistrées dans le journal d’audit d’administrateur Exchange. Pour plus d’informations sur la journalisation d’audit de l’administrateur dans Exchange, voir [Gestion de la journalisation d’audit de l’administrateur](/exchange/security-and-compliance/exchange-auditing-reports/view-administrator-audit-log).
>- L’enregistrement d’audit pour les boîtes aux lettres Exchange doit être activé pour chaque boîte aux lettres utilisateur avant de consigner toute activité de l’utilisateur dans Exchange Online ; voir [Activités de la boîte aux lettres Exchange](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c).
>- Si des applications Office sont activées, les groupes qui font partie d’Office 365 sont aussi importés dans Cloud App Security à partir d’applications Office spécifiques : par exemple, si SharePoint est activé, les groupes Office 365 sont importés également comme groupes SharePoint.
>- Vous devez [activer l’audit dans Power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-auditing/) pour obtenir les journaux. Une fois l’audit activé, Cloud App Security commence à obtenir les journaux (avec un délai de 24 à 72 heures).
>- Vous devez [activer l’audit dans Dynamics 365](/dynamics365/customer-engagement/admin/enable-use-comprehensive-auditing#enable-auditing) pour récupérer les journaux à partir de là. Une fois l’audit activé, Cloud App Security commence à obtenir les journaux (avec un délai de 24 à 72 heures).
>- Si votre Azure Active Directory est défini pour se synchroniser automatiquement avec les utilisateurs de votre environnement local Active Directory, les paramètres de l’environnement local remplacent les paramètres Azure AD et l’utilisation de l’action de gouvernance **Interrompre la synchronisation de l’utilisateur** est rétablie.
>- Pour les activités de connexion Azure AD, Cloud App Security ne couvre que les activités de connexion interactives et les activités de connexion à partir de protocoles hérités tels qu’ActiveSync. Les activités de connexion non interactives peuvent être affichées dans le journal d’audit Azure AD.
> - Les [déploiements multigéographiques](/office365/enterprise/office-365-multi-geo) sont uniquement pris en charge pour OneDrive

1. Dans la page **Applications connectées**, cliquez sur le bouton plus (+) et sélectionnez **Office 365**.

    ![option de menu Connect O365](media/connect-o365.png)

1. Dans la fenêtre contextuelle Office 365, cliquez sur **Connecter Office 365**.

    ![ouvrir la fenêtre contextuelle O365](media/office-connect.png)

1. Dans la page composants Office 365, sélectionnez les options dont vous avez besoin, puis cliquez sur **se connecter**.

    > [!NOTE]
    >
    > - Pour une protection optimale, nous vous recommandons de sélectionner tous les composants Office 365.
    > - Le composant **Office 365 Files** requiert le composant **Office 365 Activities** et l’analyse de fichiers Cloud App Security (les fichiers de**paramètres**  >  **Files**  >  **permettent l’analyse des fichiers**).

    ![connecter les composants O365](media/connect-o365-components.png)

1. Une fois Office 365 affiché comme correctement connecté, cliquez sur **Fermer**.

> [!NOTE]
> Après la connexion d’Office 365, des données qui remontent à une semaine s’affichent, dont les applications tierces connectées à Office 365 qui extraient des API. Pour les applications tierces qui n’extrayaient pas d’API avant la connexion, vous voyez des événements à partir du moment où vous connectez Office 365, car Cloud App Security active les API qui étaient désactivées par défaut.

Si vous rencontrez des problèmes lors de la connexion de l’application, consultez [résolution des problèmes liés aux connecteurs d’application](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
