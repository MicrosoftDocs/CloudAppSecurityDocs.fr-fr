---
title: Résoudre les messages d’erreur des connecteurs d’application | Microsoft Docs
description: Cet article fournit la liste des messages d’erreur relatifs aux connecteurs d’application API ainsi que les solutions recommandées pour chacun d’eux.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 89c0c08ceeda2e9bcc8d541e060f593a4d357540
ms.sourcegitcommit: 7c93b6f93d2699d466b172590710ed01697bbdad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74720945"
---
# <a name="troubleshooting-app-connectors-using-error-messages"></a>Résolution des problèmes des connecteurs d’application à l’aide de messages d’erreur

*S’applique à : Microsoft Cloud App Security*

Cet article fournit la liste des messages d’erreur relatifs aux connecteurs d’application API ainsi que les solutions recommandées pour chacun d’eux.

## <a name="troubleshooting"></a>Résolution des problèmes

Quand vous tentez de connecter une application cloud à l’aide du connecteur d’application API, la boîte de dialogue du connecteur d’application peut afficher des erreurs.

> [!div class="mx-tableFixed"]
> 
> |Message d'erreur|Application correspondante|Description|Solution|
> |----|----|----|------------|
> |HttpRequestFailure: 400 Requête incorrecte retourné par le serveur : {"error":{"code":"AF20012","message":"L’ID de client spécifié (emplacement de Tenant_ID) est configuré de façon incorrecte dans le système."|Office 365 |Aucune licence Office 365 attribuée n’a été trouvée. |Attribuez au moins une licence Office 365 à votre client.| 
> |AuthFatalFailureException: com.box.boxjavalibv2.exceptions.BoxServerException: {"error":"invalid_grant","error_description":"Jeton d’actualisation non valide"}|Zone|Le jeton d’actualisation Box n’est pas valide|Suivez le processus pour reconnecter Box à Cloud App Security.|
> |BoxRestException: Échec de l’analyse de la réponse.|Zone|Erreur interne|Cliquez à nouveau sur le lien Tester maintenant pour tester la connexion à Box.|
> |ContextManagerServiceException: com.adallom.adalib.httputils.exceptions.TokenRefreshException: {"error":"invalid_grant","error_description":"Jeton d’actualisation non valide"}'|Zone|Le jeton d’actualisation Box n’est pas valide|Suivez le processus pour reconnecter Box à Cloud App Security.|
> |BoxServerException: L’utilisateur ne peut pas accéder à cette fonctionnalité sans avoir une entreprise|Zone|Le compte Box n’est pas un compte d’entreprise.|Mettez à niveau votre licence Box vers la version d’entreprise de Box, puis suivez le processus pour reconnecter Box à Cloud App Security.|
> |BoxServerException: Non autorisé - Autorisation impossible avec ce service|Zone|L’administrateur Box a supprimé l’application Cloud App Security dans Box.|Suivez le processus pour reconnecter Box à Cloud App Security.|
> |HttpRequestFailure: 401 Non autorisé retourné par le serveur|Okta|Le jeton Okta n’est pas valide.|Suivez le processus pour reconnecter Okta à Cloud App Security.|
> |IOException:|Okta|Erreur interne|Contactez le support technique|
> |HttpRequestFailure: 404 Non trouvé retourné par le serveur|Okta|Erreur interne|Contactez le support technique|
> |SocketTimeoutException: Expiration du délai d’attente de lecture|Salesforce|Erreur interne|Cliquez à nouveau sur le lien Tester maintenant pour tester la connexion à Salesforce.|
> |HttpRequestFailure: 400 Requête incorrecte retourné par le serveur|Salesforce|La connexion à Salesforce n’a pas été établie ou a expiré.|Suivez le processus pour reconnecter Salesforce à Cloud App Security.|
> |HttpRequestFailure: 401 Non autorisé retourné par le serveur|Office 365|Problème interne|Cliquez à nouveau sur le lien Tester maintenant|
> |TokenRefreshException: {"error":"invalid_grant","error_description":"AADSTS70002: Erreur de validation des informations d’identification. AADSTS70008: Le jeton d’actualisation ou le code d’autorisation fourni a expiré. Envoyez une nouvelle demande d’autorisation interactive pour cet utilisateur et cette ressource.|Office 365|Jeton expiré|Suivez le processus pour reconnecter Office 365 à Cloud App Security.|
> |SocketTimeoutException: Expiration du délai d’attente de lecture|Office 365|Erreur interne|Cliquez à nouveau sur le lien Tester maintenant|
> |NullPointerException|Office 365|Erreur interne|Contactez le support technique|
> |IgniteException|Office 365|Le domaine ou l’utilisateur ne sont pas valides|Réinitialisez vos paramètres et suivez le processus pour reconnecter Office 365 à Cloud App Security.|
> |ContextManagerServiceException: com.adallom.adalib.httputils.exceptions.TokenRefreshException: {"error":"invalid_grant","error_description":"AADSTS70002: Erreur de validation des informations d’identification. AADSTS70008: Le jeton d’actualisation ou le code d’autorisation fourni a expiré. Envoyez une nouvelle demande d’autorisation interactive pour cet utilisateur et cette ressource.|Office 365|Le domaine ou l’utilisateur ne sont pas valides|Réinitialisez vos paramètres et suivez le processus pour reconnecter Office 365 à Cloud App Security.|
> |HttpRequestFailure: 400 Requête incorrecte retourné par le serveur|Office 365|Erreur interne|Cliquez à nouveau sur le lien Tester maintenant dans quelques minutes et, s’il ne fonctionne pas, suivez le processus pour reconnecter Office 365 à Cloud App Security.|
> |GoogleJsonResponseException: 401 Non autorisé|G Suite|Accès refusé. Vous n’êtes pas autorisé à lire les enregistrements d’activité. L’utilisateur avec lequel vous vous connectez à G Suite doit être un utilisateur administrateur.|Suivez le processus pour reconnecter G Suite à Cloud App Security à l’aide d’un compte d’administrateur.|
> |GoogleJsonResponseException: 403 Interdit|G Suite|Problème d’exécution de l’API G Suite.|Si vous venez de déployer le connecteur d’applications Cloud App Security pour G Suite, vérifiez les éléments suivants : si vous avez cliqué sur Illimité, assurez-vous que votre compte G Suite est vraiment illimité. Dans le cas contraire, réexécutez le connecteur d’applications et désélectionnez l’option pour un compte illimité. Vérifiez que les étendues que vous avez définies lors de l’installation sont correctes. S’il ne s’agit pas d’un nouveau déploiement et que cette erreur s’affiche, vous avez peut-être atteint la limite d’API pour aujourd’hui et les événements G Suite seront renouvelés demain.|
> |TokenResponseException: 400 Requête incorrecte|G Suite|La connexion à G Suite n’a pas été établie ou a expiré.|Suivez le processus pour reconnecter G Suite à Cloud App Security.|
> |RuntimeException: com.adallom.adalib.httputils.exceptions.HttpRequestFailure: 403 Interdit retourné par le serveur|ServiceNow|Les autorisations sont incorrectes|Suivez le processus pour reconnecter ServiceNow à Cloud App Security à l’aide d’un compte d’administrateur.|
> |HttpRequestFailure: 401 Non autorisé retourné par le serveur|Exchange Online|L’utilisateur ou le mot de passe sont incorrects|Vérifiez que le nom d’utilisateur et le mot de passe sont corrects, et suivez le processus pour reconnecter Exchange Online à Cloud App Security.|
> |HttpRequestFailure: 404 Non trouvé retourné par le serveur|Exchange Online|L’utilisateur que vous utilisez pour vous connecter à Exchange Online ne dispose pas d’une boîte aux lettres principale dans Exchange Online (par exemple, un utilisateur qui n’existe pas dans Azure AD ou un utilisateur qui existe dans Azure AD, mais ne dispose pas d’une licence Exchange Online).|Suivez le processus pour reconnecter Exchange Online à Cloud App Security à l’aide d’un nouveau compte d’administrateur.|
> |NullPointerException|AWS|Erreur interne|Contactez le support technique|
> |HttpRequestFailure: 500 Erreur interne au serveur retourné par le serveur|Toutes les applications|Une erreur s’est produite dans l’application.|Vérifiez l’état de l’application|
> |Le service a expiré|Toutes les applications|Un délai d’attente a été détecté dans la connexion entre Cloud App Security et l’application. Un problème au niveau de l’application peut en être la cause.|Réessayez plus tard.|

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   

[!INCLUDE [Open support ticket](includes/support.md)]  
