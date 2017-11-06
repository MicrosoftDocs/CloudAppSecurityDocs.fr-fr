---
title: Forum Aux Questions sur Cloud App Security | Microsoft Docs
description: "Cet article fournit les réponses aux questions fréquentes sur Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/6/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 081c2cf4-2750-4546-9490-4b65e87ae48c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 618f5817abc29ee3d46230f0af94e4e819242e6f
ms.sourcegitcommit: b729e881851cdd8dc3f105ddbf6b4b907b8588dd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2017
---
# <a name="frequently-asked-questions"></a>Forum aux questions

## <a name="what-kind-of-permissions-do-i-need-to-have-in-order-to-access-cloud-app-security"></a>Quels types d’autorisations dois-je avoir pour accéder à Cloud App Security ?

Vous devez être administrateur global, administrateur de mise en conformité ou administrateur de sécurité dans Azure Active Directory. Ces rôles ne sont pas suffisants dans le Centre de sécurité et conformité Office 365.
Pour définir un utilisateur comme administrateur global, administrateur de mise en conformité ou administrateur de sécurité dans Azure Active Directory, exécutez la commande suivante dans Windows PowerShell :

        $cred = Get-Credential
        Connect-MsolService -credential $cred
        Add-MsolRoleMember -RoleName "Compliance Administrator" -RoleMemberEmailAddress "XX@XX.XX"
 OR Add-MsolRoleMember -RoleName "Security Administrator" -RoleMemberEmailAddress “XX@XX.XX”

## <a name="see-also"></a>Voir aussi  
Pour savoir comment utiliser et configurer des stratégies permettant de contrôler l’utilisation des applications cloud, consultez [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md).   
Pour obtenir du support technique, accédez à la page [Support assisté Cloud App Security](http://support.microsoft.com/oas/default.aspx?prid=16031).   
Les clients Premier peuvent également choisir Cloud App Security directement depuis le [portail Premier](https://premier.microsoft.com/).  
