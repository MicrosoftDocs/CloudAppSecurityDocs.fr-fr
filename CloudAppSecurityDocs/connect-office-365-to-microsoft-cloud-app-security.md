---
title: Connectez Office 365 à Cloud App Security
description: Cet article fournit des informations sur la connexion de votre Office 365 à Cloud App Security à l’aide du connecteur API pour la visibilité et le contrôle de l’utilisation.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 7/30/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 74b03bd9db046a7637ea84d69914d1e87b47c2ae
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285493"
---
# <a name="connect-office-365-to-microsoft-cloud-app-security"></a>Connectez Office 365 à Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

Cet article fournit des instructions pour connecter Microsoft Cloud App Security à votre compte Microsoft Office 365 existant à l’aide de l’API du connecteur d’applications. Cette connexion vous offre une visibilité et un contrôle sur l’utilisation d’Office 365. Pour plus d’informations sur la façon dont Cloud App Security protège Office 365, consultez [protéger office 365](protect-office-365.md).
  
Cloud App Security prend en charge la plate-forme Office 365 dédiée héritée, ainsi que les dernières offres des services Office 365 (communément appelées la famille de versions vNext d’Office 365).  Cloud App Security ne prend pas en charge la suite Microsoft Business Productivity Online standard suite (BPOS).

> [!NOTE]
> Dans certains cas, une version de service vNext diffère légèrement aux niveaux d’administration et de gestion de l’offre Office 365 standard.

Cloud App Security prend en charge les applications Office 365 suivantes :

- Dynamics 365 CRM
- Exchange (apparaît uniquement après la détection des activités d’Exchange dans le portail et nécessite l’activation de l’audit)
- Office 365
- OneDrive
- Power automate
- Power BI (apparaît uniquement après la détection des activités de Power BI dans le portail et vous oblige à activer l’audit)
- SharePoint
- Skype Entreprise
- Équipes (apparaît uniquement après la détection des activités des équipes dans le portail)
- Yammer

> [!NOTE]
> Cloud App Security s’intègre directement avec les [journaux d’audit d’Office 365](https://docs.microsoft.com/microsoft-365/compliance/detailed-properties-in-the-office-365-audit-log?view=o365-worldwide) et reçoit tous les événements audités de **tous les services pris en charge**, tels que powerapps, Forms, Sway et Stream.

## <a name="how-to-connect-office-365-to-cloud-app-security"></a>Comment connecter Office 365 à Cloud App Security  

> [!NOTE]
>
>- Vous devez disposer d’au moins une licence Office 365 affectée pour connecter Office 365 à Cloud App Security.
>- Pour activer l’analyse des activités Office 365 dans Cloud App Security, vous devez activer l’audit dans le [Centre de sécurité et conformité Office](https://support.microsoft.com/help/4026501/office-auditing-in-office-365-for-admins).
>- La journalisation d’audit de l’administrateur Exchange, qui est activée par défaut dans Office 365, consigne un événement dans le journal d’audit Office 365 lorsqu’un administrateur (ou un utilisateur qui a reçu des privilèges d’administrateur) apporte une modification à votre organisation Exchange Online. Les modifications apportées à l’aide du centre d’administration Exchange ou en exécutant une applet de commande dans Windows PowerShell sont consignées dans le journal d’audit de l’administrateur Exchange. Pour plus d’informations sur la journalisation d’audit de l’administrateur dans Exchange, consultez [journalisation d’audit de l’administrateur](https://docs.microsoft.com/exchange/security-and-compliance/exchange-auditing-reports/view-administrator-audit-log).
>- La journalisation d’audit de la boîte aux lettres Exchange doit être activée pour chaque boîte aux lettres de l’utilisateur avant que l’activité de l’utilisateur dans Exchange Online soit enregistrée, consultez [activités de boîte aux lettres Exchange](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c).
>- Si les applications Office sont activées, les groupes qui font partie d’Office 365 sont également importés dans Cloud App Security à partir des applications Office spécifiques, par exemple, si SharePoint est activé, les groupes Office 365 sont également importés en tant que groupes SharePoint.
>- Vous devez [activer l’audit dans PowerBI](https://powerbi.microsoft.com/documentation/powerbi-admin-auditing/) pour y récupérer les journaux. Une fois l’audit activé, Cloud App Security commence à obtenir les journaux (avec un délai de 24-72 heures).
>- Vous devez [activer l’audit dans Dynamics 365](https://docs.microsoft.com/dynamics365/customer-engagement/admin/enable-use-comprehensive-auditing#enable-auditing) pour récupérer les journaux à partir de là. Une fois l’audit activé, Cloud App Security commence à obtenir les journaux (avec un délai de 24-72 heures).
>- Si votre Azure Active Directory est configurée pour se synchroniser automatiquement avec les utilisateurs de votre Active Directory environnement local, les paramètres de l’environnement local remplacent les paramètres d’Azure AD et l’utilisation de l’action de gouvernance **interrompre l’utilisateur** est annulée.
>- Pour les activités de connexion Azure AD, Cloud App Security ne couvre que les activités de connexion interactives et les activités de connexion à partir de protocoles hérités tels qu’ActiveSync. Les activités de connexion non interactives peuvent être affichées dans le journal d’audit Azure AD.

1. Dans la page **applications connectées** , cliquez sur le bouton plus et sélectionnez **Office 365**.

    ![connecter 0365](media/connect-0365.png)

2. Dans la fenêtre contextuelle Office 365, cliquez sur **connecter office 365**.

    ![connecter 0365](media/office-connect.png)

3. Une fois la connexion établie avec Office 365, cliquez sur **Fermer**.

> [!NOTE]
> Après avoir connecté Office 365, vous verrez les données d’une semaine, y compris toutes les applications tierces connectées à Office 365 qui tirent des API. Pour les applications tierces qui n’extrayaient pas d’API avant la connexion, les événements s’affichent au moment où vous connectez Office 365, car Cloud App Security active les API qui étaient désactivées par défaut.

Si vous rencontrez des problèmes lors de la connexion de l’application, consultez [résolution des problèmes liés aux connecteurs d’application](troubleshooting-api-connectors-using-error-messages.md).

## <a name="next-steps"></a>Étapes suivantes :

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
