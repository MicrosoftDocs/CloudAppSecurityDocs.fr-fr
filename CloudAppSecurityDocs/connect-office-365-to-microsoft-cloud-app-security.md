---
title: Connectez Microsoft 365 à Cloud App Security
description: Cet article fournit des informations sur la façon de connecter votre Microsoft 365 à Cloud App Security à l’aide du connecteur API pour la visibilité et le contrôle de l’utilisation.
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
ms.openlocfilehash: 797ff41831b886354583e3b21e1cf0981f84577e
ms.sourcegitcommit: c174a7ada5c6a14f0fea9870672898c54e5e3b52
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89150203"
---
# <a name="connect-microsoft-365-to-microsoft-cloud-app-security"></a>Connectez Microsoft 365 à Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

Cet article fournit des instructions pour connecter Microsoft Cloud App Security à votre compte Microsoft 365 existant à l’aide de l’API du connecteur d’applications. Cette connexion vous donne une visibilité et un contrôle sur Microsoft 365 utilisation. Pour plus d’informations sur la façon dont Cloud App Security protège Microsoft 365, consultez [protéger Microsoft 365](protect-office-365.md).
  
Cloud App Security prend en charge la plate-forme Office 365 dédiée héritée, ainsi que les dernières offres de services Microsoft 365 (communément appelées la famille de versions vNext de Microsoft 365).  Cloud App Security ne prend pas en charge la suite héritée Microsoft Business Productivity Online Standard Suite (BPOS).

> [!NOTE]
> Dans certains cas, une version de service vNext diffère légèrement aux niveaux d’administration et de gestion de l’offre de Microsoft 365 standard.

Cloud App Security prend en charge les applications de Microsoft 365 suivantes :

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
> Cloud App Security s’intègre directement avec les [journaux d’audit d’Microsoft 365](/microsoft-365/compliance/detailed-properties-in-the-office-365-audit-log?view=o365-worldwide) et reçoit tous les événements audités de **tous les services pris en charge**, tels que powerapps, Forms, Sway et Stream.

## <a name="how-to-connect-microsoft-365-to-cloud-app-security"></a>Comment connecter Microsoft 365 à Cloud App Security  

> [!NOTE]
>
>- Vous devez disposer d’au moins une licence Microsoft 365 attribuée pour vous connecter Microsoft 365 à Cloud App Security.
>- Pour activer l’analyse des activités de Microsoft 365 dans Cloud App Security, vous devez activer l’audit dans le [Centre de sécurité et conformité Office](https://support.microsoft.com/help/4026501/office-auditing-in-office-365-for-admins).
>- La journalisation d’audit de l’administrateur Exchange, qui est activée par défaut dans Microsoft 365, enregistre un événement dans le journal d’audit Microsoft 365 lorsqu’un administrateur (ou un utilisateur qui a reçu des privilèges d’administrateur) apporte une modification à votre organisation Exchange Online. Les modifications apportées en utilisant le Centre d’administration Exchange ou en exécutant une applet de commande dans Windows PowerShell sont enregistrées dans le journal d’audit d’administrateur Exchange. Pour plus d’informations sur la journalisation d’audit de l’administrateur dans Exchange, voir [Gestion de la journalisation d’audit de l’administrateur](/exchange/security-and-compliance/exchange-auditing-reports/view-administrator-audit-log).
>- L’enregistrement d’audit pour les boîtes aux lettres Exchange doit être activé pour chaque boîte aux lettres utilisateur avant de consigner toute activité de l’utilisateur dans Exchange Online ; voir [Activités de la boîte aux lettres Exchange](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c).
>- Si les applications Office sont activées, les groupes qui font partie de Microsoft 365 sont également importés dans Cloud App Security à partir des applications Office spécifiques, par exemple, si SharePoint est activé, les groupes Microsoft 365 sont également importés en tant que groupes SharePoint.
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

1. Une fois que Microsoft 365 s’affiche comme connecté avec succès, cliquez sur **Fermer**.

> [!NOTE]
> Après vous être connecté Microsoft 365, vous verrez les données d’une semaine, y compris toutes les applications tierces connectées à des Microsoft 365 qui tirent des API. Pour les applications tierces qui n’extrayaient pas d’API avant la connexion, les événements s’affichent au moment où vous vous connectez Microsoft 365, car Cloud App Security active les API qui étaient désactivées par défaut.

Si vous rencontrez des problèmes lors de la connexion de l’application, consultez [résolution des problèmes liés aux connecteurs d’application](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
