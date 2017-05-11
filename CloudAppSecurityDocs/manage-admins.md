---
title: "Gérer l’accès administrateur au portail Cloud App Security | Microsoft Docs"
description: "Cette rubrique explique comment définir l’accès au portail Cloud App Security pour vos administrateurs."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/7/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: b718edad-350c-4d90-b045-92529d701dc5
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: ce7a3bb3951e16efeaeafa3e2fc463a3ac5d9dbc
ms.sourcegitcommit: 945cb3c047ae1bfc05be20cc7798c43005b27c9b
ms.translationtype: HT
ms.contentlocale: fr-FR
---
## <a name="managing-admin-access"></a>Gestion de l’accès d’administrateur

Cloud App Security prend en charge les rôles d’administrateur suivants :

- Administrateur général : les administrateurs généraux ont un **accès total**, c’est-à-dire qu’ils disposent d’autorisations complètes dans Cloud App Security pour ajouter des administrateurs, ajouter des stratégies et des paramètres, charger des journaux et effectuer des actions de gouvernance.
- Administrateur de la sécurité : les administrateurs de la sécurité ont un **accès total**, c’est-à-dire qu’ils disposent d’autorisations complètes dans Cloud App Security pour ajouter des administrateurs, ajouter des stratégies et des paramètres, charger des journaux et effectuer des actions de gouvernance.
- Lecteur Sécurité : le Lecteur Sécurité dispose d’autorisations en lecture seule et peut gérer les alertes. Le Lecteur Sécurité ne peut pas effectuer les actions suivantes :
      - Créer des stratégies ou modifier et changer des stratégies existantes 
      - Effectuer des actions de gouvernance 
      - Charger des journaux de découverte
      - Interdire ou approuver des applications tierces
      - Accéder à la page de paramètres de la plage d’adresses IP
      - Accéder aux pages contenant des paramètres 
      - Accéder aux paramètres de découverte 
      - Accéder à la page de connecteurs d’application
      - Accéder au journal de gouvernance 
      - Accéder à la page Gérer des rapports d’instantanés 

Les administrateurs titulaires de ces rôles dans Azure Active Directory ou Office 365 ont les mêmes rôles dans Cloud App Security. Pour plus d’informations sur les rôles d’administrateur, consultez [Affectation des rôles d’administrateur dans Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-assign-admin-roles).

Pour ajouter des administrateurs à Cloud App Security :

1. Cliquez sur l’icône des paramètres ![icône des paramètres](./media/settings-icon.png "icône des paramètres"), puis sur **Gérer l’accès administrateur**. 

2. Ajoutez les administrateurs qui doivent avoir accès à Cloud App Security.
  
      
3. Ensuite, cliquez sur la liste déroulante pour définir le type d’accès accordé à l’administrateur : **Accès total** ou **Lecteur Sécurité**.

     >[!NOTE]
      >Tout **Lecteur Sécurité** qui tente d’accéder à une page restreinte ou d’effectuer une action restreinte reçoit une erreur indiquant qu’il ne dispose pas des autorisations nécessaires pour accéder à la page ou effectuer l’action.

4. Cliquez sur **Fermer**.  

   >[!NOTE]
    >Tout utilisateur non invité (avec son propre rôle, comme un administrateur général, de mise en conformité ou de la sécurité) peut inviter d’autres utilisateurs dans Cloud App Security.
  
 ![gérer l’accès administrateur](./media/manage-admin-access.png "gérer l’accès administrateur")  

**Pour remplacer les autorisations d’administrateur :**

Si vous souhaitez remplacer une autorisation d’administrateur dans Azure Active Directory ou Office 365, vous pouvez le faire manuellement en ajoutant l’utilisateur à Cloud App Security et en lui affectant un rôle.
Par exemple, pour affecter à Stéphanie, qui est titulaire du rôle Lecteur Sécurité dans Azure Active Directory, un accès total à Cloud App Security, vous pouvez l’ajouter manuellement à Cloud App Security et lui accorder un accès total. Son rôle est ainsi remplacé, et elle dispose des autorisations désirées dans Cloud App Security. 


##  <a name="Adminsettings"></a> Personnaliser vos paramètres d’administration  
Pour définir vos préférences en tant qu’administrateur de Cloud App Security, cliquez sur votre nom dans la barre de menus du portail, puis sélectionnez **Paramètres utilisateur** pour définir les éléments suivants :  
  
1.  Cliquez sur **Paramètres du compte**. Vous pouvez ici personnaliser la langue que doit utiliser le portail. Vous pouvez définir la langue du portail sur la langue par défaut ou sur la langue de votre choix.  
  
     ![paramètres utilisateur personnalisés](./media/custom-user-settings.png "paramètres utilisateur personnalisés")  
  
2.  Cliquez sur **Notifications** et définissez les préférences de notification par courrier électronique et SMS pour les e-mails reçus du système.  Vous pouvez définir le niveau de gravité des alertes et des violations à recevoir par e-mail ; le niveau de gravité étant défini par stratégie, quand des violations sont déclenchées, vous recevez une notification par courrier électronique en fonction du paramètre défini ici et du paramètre de gravité défini dans la stratégie qui a été enfreinte. Les e-mails sont envoyés à l’alias associé au compte d’utilisateur administrateur que vous utilisez pour vous connecter à Cloud App Security. Entrez un numéro de téléphone afin que Cloud App Security puisse vous envoyer des SMS quand des alertes et des notifications sont envoyées et définissez le niveau de gravité pour lequel vous souhaitez recevoir des notifications par SMS.  
  
   > [!NOTE] 
   > Le nombre maximal d’alertes envoyées via SMS est de 10 par numéro de téléphone par jour. Notez que le jour est calculé selon le fuseau horaire UTC. 
  
  ![paramètres de notification](./media/notification-settings.png "paramètres de notification")  
  
3. Quand vous avez terminé, cliquez sur **Enregistrer**.  


## <a name="region-and-language-settings"></a>Paramètres linguistiques et régionaux  
  
1. Définissez la **Langue** à utiliser par défaut pour le portail. Pour modifier la langue pour un administrateur spécifique, accédez à **Paramètres utilisateur** > **Paramètres du compte**.  
  
   ![langue du fuseau horaire](./media/timezone-language.png "langue du fuseau horaire")  
  
2. Définissez le **Fuseau horaire principal**. Cloud App Security analyse et rassemble vos données en continu. Par défaut, le fuseau horaire pour le portail Cloud App Security est défini sur UTC. Il est important de définir le fuseau horaire principal, afin que Cloud App Security puisse dater les incidents avec précision dans votre système. Par exemple, dans le graphique d’activité, les données sont organisées par date ; ces dates étant affectées par le fuseau horaire de votre système, si vous n’avez pas modifié le fuseau horaire par défaut, vos données sont organisées en journées de 24 heures selon le fuseau horaire UTC et peuvent se voir associer un horodatage plus ou moins décalé par rapport à la réalité.  
  
     ![fuseau horaire principal](./media/master-time-zone.png "fuseau horaire principal")  
  
## <a name="back-up-portal-settings"></a>Sauvegarder les paramètres du portail

Grâce à cet écran, vous pouvez à tout moment sauvegarder vos paramètres de portail. Cliquez sur Exporter les paramètres de portail pour créer un fichier json de tous vos paramètres de portail, y compris les règles de stratégie, les groupes d’utilisateurs et les plages d’adresses IP.  
  
![console de sauvegarde](./media/backup-console.png "console de sauvegarde")  
  
##  <a name="mailsettings"></a>Personnaliser votre expérience  
Dans la barre de menus, cliquez sur l’icône des paramètres ![icône des paramètres](./media/settings-icon.png "icône des paramètres") et sélectionnez **Paramètres de messagerie** pour définir les paramètres des notifications par e-mail envoyées par Cloud App Security aux administrateurs ; ce paramétrage définit l’envoi des alertes et des notifications aux utilisateurs finaux concernant les violations dans lesquelles ils sont impliqués.  
  
![menu des paramètres de messagerie](./media/mail-setting-menu.png "menu des paramètres de messagerie")  
  
Configurez ce qui suit :  
  
1.  **Adresse de l’expéditeur** : compte de messagerie à utiliser pour envoyer la notification.  
  
     **Nom complet de l’expéditeur** : nom à afficher dans le champ **De** de l’e-mail.  
  
     **Adresse e-mail de réponse** : compte e-mail à utiliser pour les réponses au message.  
  
     ![configuration des paramètres de messagerie](./media/mail-settings-config.png "configuration des paramètres de messagerie")  
  
2.  Vous pouvez utiliser un fichier html pour personnaliser et créer les e-mails envoyés par le système. Le fichier html utilisé pour votre modèle doit inclure les éléments suivants :  
  
    -   Tout le code CSS du modèle doit être inséré dans celui-ci.  
  
    -   Le modèle doit avoir trois espaces réservés non modifiables :  
  
         %%logo%% : URL vers le logo de votre société chargée par le biais de la page Paramètres généraux  
  
         %%title%% : espace réservé pour le titre de l’e-mail, tel que défini par la stratégie  
  
         %%content%% : espace réservé pour le contenu à inclure pour les utilisateurs finaux, tel que défini par la stratégie  
  
     Voici un exemple de modèle d’e-mail : 
```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
  <html>  
       <head>  
            <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"/>  
            <meta name="viewport" content="width=device-width, initial-scale=1.0"/>  
          </head>  
          <body class="end-user">  
          <table border="0" cellpadding="20%" cellspacing="0" width="100%" id="background-table">  
            <tr>  
              <td align="center">  
                <!--[if (gte mso 9)|(IE)]>  
                <table width="600" align="center" cellpadding="0" cellspacing="0" border="0">  
                  <tr>  
                    <td>  
                <![endif]-->  
                <table bgcolor="#ffffff" align="center" border="0" cellpadding="0" cellspacing="0" style="padding-bottom: 40px;" id="container-table">  
                  <tr>  
                    <td align="right" id="header-table-cell">  
                      <img src="%%logo%%" alt="Microsoft Cloud App Security" id="org-logo" />  
                    </td>  
                  </tr>  
                  <tr>  
                    <td style="padding-top: 58px;" align="center" valign="top">  
                      <table width="100%" cellpadding="12">  
                        <tr>  
                          <td align="center" class="round-title">  
                            %%title%%  
                          </td>  
                        </tr>  
                      </table>  
                    </td>  
                  </tr>  
                  <tr>  
                    <td style="padding: 0 40px 79px 40px;" class="content-table-cell" align="left" valign="top">  
                        %%content%%  
                    </td>  
                  </tr>  
                  <tr>  
                    <td class="last-row"></td>  
                  </tr>  
                </table>  
                <!--[if (gte mso 9)|(IE)]>  
                </td>  
                </tr>  
                </table>  
                  <![endif]-->  
              </td>  
              </tr>  
          </table>  
            </body>  
          </html>  
    ```

  
3.  Click **Upload a template...** and select the file you created.  
  
     Then, click **Send a test email** to send yourself a test email to see an example of the template you created.  
     The email will be sent to the account you used to log into the portal. In the test email you will be able to see the metadata fields, the template, the email subject, the title in the email body and the content.  
  
## Single sign-on  
Cloud App Security is coupled with Azure Active Directory for authentication, provisioning, and licensing related activities. For information on how to manage single sign-on, see [Azure Active Directory federation compatibility list: third-party identity providers that can be used to implement single sign-on](https://msdn.microsoft.com/library/azure/jj679342.aspx).  


> [!NOTE] 
> If you use ExpressRoute, Cloud App Security is deployed in Azure and fully integrated with [ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/). All interactions with the Cloud App Security apps and traffic sent to Cloud App Security, including upload of discovery logs, is routed via ExpressRoute **public peering** for improved latency, performance and security. There are no configuration steps required from the customer side.  
    For more information about  Public Peering, see [ExpressRoute circuits and routing domains](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/).  
    
## See Also  
[Set up Cloud Discovery](set-up-cloud-discovery.md)   
[For technical support, please visit the Cloud App Security assisted support page.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier customers can also choose Cloud App Security directly from the Premier Portal.](https://premier.microsoft.com/)  
  
  