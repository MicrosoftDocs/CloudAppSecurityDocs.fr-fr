---
title: Connecter Office 365 à Cloud App Security pour la visibilité et le contrôle d’utilisation | Microsoft Docs
description: Cette rubrique fournit des informations sur la connexion d’Office 365 à Cloud App Security à l’aide du connecteur API.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/30/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: a79bf393-0d2c-44b6-8dab-86c740fd7333
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 1960d9801ad24b880bd2f4eaad3947b26d87437e
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44144463"
---
*S’applique à : Microsoft Cloud App Security*



# <a name="connect-office-365-to-microsoft-cloud-app-security"></a>Connecter Office 365 à Microsoft Cloud App Security
Cette section fournit des instructions pour connecter Microsoft Cloud App Security à votre compte Microsoft Office 365 existant à l’aide de l’API du connecteur d’applications.  
  
Cloud App Security prend en charge la plateforme dédiée Office 365 héritée, ainsi que les dernières offres de services Office 365 (communément appelés la famille de mises en production vNext d’Office 365).  Cloud App Security ne prend pas en charge la suite héritée Microsoft Business Productivity Online Standard Suite. 

> [!NOTE]
> Dans certains cas, une mise en production de service vNext diffère légèrement de l’offre Office 365 standard sur les plans de l’administration et de la gestion.

Cloud App Security prend en charge les applications Office 365 suivantes :

- Office 365
- SharePoint
- OneDrive
- Teams (apparaît uniquement une fois que des activités Teams sont détectées dans le portail)
- Power BI (apparaît uniquement une fois que des activités Power BI sont détectées dans le portail et nécessite l’activation de l’audit)
- Exchange (apparaît uniquement une fois que des activités Exchange sont détectées dans le portail et nécessite l’activation de l’audit)

 
## <a name="how-to-connect-office-365-to-cloud-app-security"></a>Comment connecter Office 365 à Cloud App Security  
  
> [!NOTE]
>- Vous devez disposer d’au moins une licence Office 365 pour connecter Office 365 à Cloud App Security.
>-  La journalisation d’audit de l’administrateur Exchange, qui est activée par défaut dans Office 365, consigne un événement dans le journal d’audit Office 365 quand un administrateur (ou un utilisateur qui a reçu des privilèges d’administrateur) apporte une modification dans votre organisation Exchange Online. Les modifications apportées en utilisant le Centre d’administration Exchange ou en exécutant une applet de commande dans Windows PowerShell sont enregistrées dans le journal d’audit d’administrateur Exchange. Pour plus d’informations sur la journalisation d’audit de l’administrateur dans Exchange, voir [Gestion de la journalisation d’audit de l’administrateur](http://go.microsoft.com/fwlink/p/?LinkID=619225).
>- L’enregistrement d’audit pour les boîtes aux lettres Exchange doit être activé pour chaque boîte aux lettres utilisateur avant de consigner toute activité de l’utilisateur dans Exchange Online ; voir [Activités de la boîte aux lettres Exchange](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c).
>- Si des applications Office sont activées, les groupes qui font partie d’Office 365 sont aussi importés dans Cloud App Security à partir d’applications Office spécifiques : par exemple, si SharePoint est activé, les groupes Office 365 sont importés également comme groupes SharePoint.
>- Vous devez [activer l’audit dans Power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-auditing/) pour obtenir les journaux. Une fois l’audit activé, Cloud App Security commence à obtenir les journaux (avec un délai de 24 à 72 heures).
> Si votre Azure Active Directory est défini pour se synchroniser automatiquement avec les utilisateurs de votre environnement local Active Directory, les paramètres de l’environnement local remplacent les paramètres Azure AD et l’utilisation de l’action de gouvernance **Interrompre la synchronisation de l’utilisateur** est rétablie. 
 
1.  Dans la page **Applications connectées**, cliquez sur le bouton plus (+) et sélectionnez **Office 365**.  

      ![connecter 0365](./media/connect-0365.png) 

2.  Dans la fenêtre contextuelle Office 365, cliquez sur **Connecter Office 365**.

      ![connecter 0365](./media/office-connect.png) 
 
3.   Une fois Office 365 affiché comme correctement connecté, cliquez sur **Fermer**.
  
> [!NOTE] 
> Après la connexion d’Office 365, des données qui remontent à une semaine s’affichent, dont les applications tierces connectées à Office 365 qui extraient des API. Pour les applications tierces qui n’extrayaient pas d’API avant la connexion, vous voyez les événements à partir du moment où vous avez connecté Office 365, car Cloud App Security active toutes les API désactivées par défaut.

## <a name="see-also"></a>Voir aussi  
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  