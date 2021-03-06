---
title: Résoudre les messages d’erreur du connecteur d’applications
description: Cet article fournit la liste des messages d’erreur relatifs aux connecteurs d’application API ainsi que les solutions recommandées pour chacun d’eux.
ms.date: 01/29/2020
ms.topic: conceptual
ms.openlocfilehash: 5848e0286d6d99ed3699652e3a44ef5fe1cf359b
ms.sourcegitcommit: 40d17309b8729eb914ea91ba5fa7017340231488
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/29/2020
ms.locfileid: "97808995"
---
# <a name="troubleshooting-app-connectors-using-error-messages"></a>Résolution des problèmes des connecteurs d’application à l’aide de messages d’erreur

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Cet article fournit la liste des messages d’erreur relatifs aux connecteurs d’application API ainsi que les solutions recommandées pour chacun d’eux.

## <a name="troubleshooting"></a>Résolution des problèmes

Quand vous tentez de connecter une application cloud à l’aide du connecteur d’application API, la boîte de dialogue du connecteur d’application peut afficher des erreurs.

> [!div class="mx-tableFixed"]
>
> |Message d'erreur|Application correspondante|Description|Résolution|
> |----|----|----|------------|
> |HttpRequestFailure: 500 Erreur interne au serveur retourné par le serveur|Toutes les applications|Une erreur s’est produite dans l’application.|Vérifiez l’état de l’application|
> |Le service a expiré|Toutes les applications|Un délai d’attente a été détecté dans la connexion entre Cloud App Security et l’application. Un problème au niveau de l’application peut en être la cause.|Réessayez plus tard.|
> |NullPointerException|AWS|Erreur interne|Contacter le support technique|
> |AuthFatalFailureException: com.box.boxjavalibv2.exceptions.BoxServerException: {"error":"invalid_grant","error_description":"Jeton d’actualisation non valide"}|Box|Le jeton d’actualisation Box n’est pas valide|Suivez le processus pour reconnecter Box à Cloud App Security.|
> |BoxRestException: Échec de l’analyse de la réponse.|Box|Erreur interne|Cliquez à nouveau sur le lien Tester maintenant pour tester la connexion à Box.|
> |ContextManagerServiceException: com.adallom.adalib.httputils.exceptions.TokenRefreshException: {"error":"invalid_grant","error_description":"Jeton d’actualisation non valide"}'|Box|Le jeton d’actualisation Box n’est pas valide|Suivez le processus pour reconnecter Box à Cloud App Security.|
> |BoxServerException: L’utilisateur ne peut pas accéder à cette fonctionnalité sans avoir une entreprise|Box|Le compte Box n’est pas un compte d’entreprise.|Mettez à niveau votre licence Box vers la version d’entreprise de Box, puis suivez le processus pour reconnecter Box à Cloud App Security.|
> |BoxServerException: Non autorisé - Autorisation impossible avec ce service|Box|L’administrateur Box a supprimé l’application Cloud App Security dans Box.|Suivez le processus pour reconnecter Box à Cloud App Security.|
> |HttpRequestFailure: 401 Non autorisé retourné par le serveur|Exchange Online|L’utilisateur ou le mot de passe sont incorrects|Vérifiez que le nom d’utilisateur et le mot de passe sont corrects, et suivez le processus pour reconnecter Exchange Online à Cloud App Security.|
> |HttpRequestFailure: 404 Non trouvé retourné par le serveur|Exchange Online|L’utilisateur que vous utilisez pour vous connecter à Exchange Online ne dispose pas d’une boîte aux lettres principale dans Exchange Online (par exemple, un utilisateur qui n’existe pas dans Azure AD ou un utilisateur qui existe dans Azure AD, mais ne dispose pas d’une licence Exchange Online).|Suivez le processus pour reconnecter Exchange Online à Cloud App Security à l’aide d’un nouveau compte d’administrateur.|
> |GoogleJsonResponseException: 401 Non autorisé|Espace de travail Google|Accès refusé. Vous n’êtes pas autorisé à lire les enregistrements d’activité. L’utilisateur avec lequel vous vous connectez à Google Workspace doit être un utilisateur administrateur.|Suivez le processus pour reconnecter l’espace de travail Google à Cloud App Security à l’aide d’un compte d’administrateur.|
> |GoogleJsonResponseException: 403 Interdit|Espace de travail Google|Problème lors de l’exécution de l’API de l’espace de travail Google.|Si vous venez de déployer le connecteur d’application Cloud App Security pour l’espace de travail Google, vérifiez les points suivants : Si vous avez cliqué sur illimité, assurez-vous que votre compte Google Workspace est vraiment illimité. Dans le cas contraire, réexécutez le connecteur d’applications et désélectionnez l’option pour un compte illimité. Vérifiez que les étendues que vous avez définies lors de l’installation sont correctes. S’il ne s’agit pas d’un nouveau déploiement et que vous voyez cette erreur, vous avez peut-être atteint la limite d’API pour aujourd’hui et les événements Google Workspace seront renouvelés demain.|
> |TokenResponseException: 400 Requête incorrecte|Espace de travail Google|La connexion à Google Workspace ne s’est pas terminée ou a expiré.|Suivez le processus pour reconnecter l’espace de travail Google à Cloud App Security.|
> |HttpRequestFailure: 401 Non autorisé retourné par le serveur|Okta|Le jeton Okta n’est pas valide.|Suivez le processus pour reconnecter Okta à Cloud App Security.|
> |IOException:|Okta|Erreur interne|Contacter le support technique|
> |HttpRequestFailure: 404 Non trouvé retourné par le serveur|Okta|Erreur interne|Contacter le support technique|
> |HttpRequestFailure: 400 Requête incorrecte retourné par le serveur : {"error":{"code":"AF20012","message":"L’ID de client spécifié (emplacement de Tenant_ID) est configuré de façon incorrecte dans le système."|Office 365 |Aucune licence Office 365 attribuée n’a été trouvée. |Attribuez au moins une licence Office 365 à votre client.|
> |Microsoft. Office. Compliance. audit. DataServiceException : le locataire 998cea7e-35cd-46a5-ab3c-8ec88a45d7d5 n’existe pas ou {"Error" : "code" : "AF20023", "message" : "l’abonnement a été désactivé."|Office 365|La journalisation d’audit n’est pas activée dans Office 365|Activez la journalisation d’audit dans Office 365. [En savoir plus](connect-office-365-to-microsoft-cloud-app-security.md#how-to-connect-office-365-to-cloud-app-security)|
> |HttpRequestFailure: 401 Non autorisé retourné par le serveur|Office 365|Problème interne|Cliquez à nouveau sur le lien Tester maintenant|
> |TokenRefreshException: {"error":"invalid_grant","error_description":"AADSTS70002: Erreur de validation des informations d’identification. AADSTS70008: Le jeton d’actualisation ou le code d’autorisation fourni a expiré. Envoyez une nouvelle demande d’autorisation interactive pour cet utilisateur et cette ressource.|Office 365|Jeton expiré.|Suivez le processus pour reconnecter Office 365 à Cloud App Security.|
> |SocketTimeoutException: Expiration du délai d’attente de lecture|Office 365|Erreur interne|Cliquez à nouveau sur le lien Tester maintenant|
> |NullPointerException|Office 365|Erreur interne|Contacter le support technique|
> |IgniteException|Office 365|Le domaine ou l’utilisateur ne sont pas valides|Réinitialisez vos paramètres et suivez le processus pour reconnecter Office 365 à Cloud App Security.|
> |ContextManagerServiceException: com.adallom.adalib.httputils.exceptions.TokenRefreshException: {"error":"invalid_grant","error_description":"AADSTS70002: Erreur de validation des informations d’identification. AADSTS70008: Le jeton d’actualisation ou le code d’autorisation fourni a expiré. Envoyez une nouvelle demande d’autorisation interactive pour cet utilisateur et cette ressource.|Office 365|Le domaine ou l’utilisateur ne sont pas valides|Réinitialisez vos paramètres et suivez le processus pour reconnecter Office 365 à Cloud App Security.|
> |HttpRequestFailure: 400 Requête incorrecte retourné par le serveur|Office 365|Erreur interne|Cliquez à nouveau sur le lien Tester maintenant dans quelques minutes et, s’il ne fonctionne pas, suivez le processus pour reconnecter Office 365 à Cloud App Security.|
> |SocketTimeoutException: Expiration du délai d’attente de lecture|Salesforce|Erreur interne|Cliquez à nouveau sur le lien Tester maintenant pour tester la connexion à Salesforce.|
> |HttpRequestFailure: 400 Requête incorrecte retourné par le serveur|Salesforce|La connexion à Salesforce n’a pas été établie ou a expiré.|Suivez le processus pour reconnecter Salesforce à Cloud App Security.|
> |Autorisations d’extraction : NoHttpResponseException : `*******.salesforce.com:443` échec de la réponse|Salesforce|Restriction d’adresse IP sur le client ENV.|Dans le portail Salesforce, sous paramètres de session **d’installation**  >  , désactivez la case à cocher **verrouiller les sessions sur l’adresse IP à partir de laquelle elles proviennent** .|
> |RuntimeException: com.adallom.adalib.httputils.exceptions.HttpRequestFailure: 403 Interdit retourné par le serveur|ServiceNow|Les autorisations sont incorrectes|Suivez le processus pour reconnecter ServiceNow à Cloud App Security à l’aide d’un compte d’administrateur.|
> |Événements d’extraction : {"code" : 403, "serverResponse"<br />Obtient les utilisateurs : {"code" : 403, "serverResponse"<br />…<br />« Body » : « { » error» : « autorisation refusée »}»|Workday|Autorisations insuffisantes pour accéder aux journaux d’audit et/ou aux points de terminaison d’utilisateur|Vérifiez que toutes les autorisations sont en place. [En savoir plus](connect-workday-to-microsoft-cloud-app-security.md#prerequisites)|
> |"code" : 400, "serverResponse"<br />…<br />corps " :" {"Error" : "invalid_grant"}|Workday|Problème d’authentification|Le compte utilisé pour configurer l’instance est peut-être verrouillé ou désactivé. Pour vérifier, affichez le compte de jour ouvré et sélectionnez **afficher l’historique de connexion**. Vous pouvez voir un message d’échec d’authentification dans le rapport en spécifiant que le compte système est désactivé. [En savoir plus](connect-workday-to-microsoft-cloud-app-security.md#how-to-connect-workday-to-cloud-app-security-using-oauth)|
> |« Code » : 401, « serverResponse » :<br />…<br />corps " :" {"Error" : "invalid_client"} "|Workday|Problème de validité du jeton client|Jeton client de l’API REST OAuth 2,0 non valide. Le jeton a peut-être expiré ou est peut-être incorrect. Générez un autre jeton et affectez-le à l’instance connectée. [En savoir plus](connect-workday-to-microsoft-cloud-app-security.md#how-to-connect-workday-to-cloud-app-security-using-oauth)|

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
