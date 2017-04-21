---
title: "Personnaliser le portail Cloud App Security pour des résultats optimaux | Microsoft Docs"
description: "Cette rubrique présente les premières étapes de personnalisation du portail."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/19/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 2e7e57b0-db54-4d75-896c-4700dd9abe48
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: b55da41080d70a41382a94b9ff527d50046c61b2
ms.sourcegitcommit: 661f4ce41262e8462c90fd2a4f1232e2154d5113
translationtype: HT
---
# <a name="customize-the-portal"></a>Personnaliser le portail
La procédure suivante contient des instructions pour personnaliser le portail Cloud App Security.
  
## <a name="set-up-the-portal"></a>Configurer le portail  
  
1.  Dans la barre de menus du portail Cloud App Security, cliquez sur l’icône des paramètres ![icône des paramètres](./media/settings-icon.png "icône des paramètres") et sélectionnez **Paramètres généraux** pour configurer les éléments suivants :  
  
3.  **Détails de l’organisation**  
  
     Il est important que vous fournissiez un **Nom d’affichage de l’organisation** pour votre organisation. Il apparaît dans les e-mails et les pages web envoyés par le système.  
  
     Fournissez un **Nom de l’environnement** (client). Cela est particulièrement important si vous gérez plusieurs clients.  
  
4. Vous pouvez également fournir un **Logo**, qui apparaît dans les notifications par courrier électronique et les pages web envoyées par le système. Le logo doit être un fichier png avec une taille maximale de 150 x 50 pixels sur un arrière-plan transparent.  

4.  Ajoutez la liste de vos **Domaines gérés**. Grâce aux domaines gérés, Cloud App Security peut déterminer quels sont les utilisateurs internes, les utilisateurs externes, ainsi que les emplacements auxquels les fichiers doivent ou non être partagés. Ce dispositif est utilisé pour les rapports, ainsi que pour les alertes.  
> [!NOTE] 
> - Les utilisateurs dans des domaines qui ne sont pas configurés comme internes seront marqués comme externes et aucune recherche d’activités ni de fichiers ne sera effectuée.
> - En cas d’intégration à Azure Information Protection, consultez [Intégration d’Azure Information Protection](azip-integration.md) pour obtenir des informations. 
  
4.  **Paramètres de confidentialité d’e-mail du journal d’activité**  
  
     Quand des e-mails sont détectés à partir d’Exchange Online, il est possible de définir la façon dont ils sont affichés, afin de préserver la confidentialité. Plusieurs options sont disponibles pour l’affichage d’un e-mail : **Ligne Objet masquée**, **Ligne Objet entière** ou **Afficher l’ID d’e-mail uniquement**.  
  
     ![paramètres généraux](./media/general-settings.png "paramètres généraux")  
  
5.  **Paramètres linguistiques et régionaux**  
  
     Définissez la **Langue** à utiliser par défaut pour le portail. Pour modifier la langue pour un administrateur spécifique, accédez à **Paramètres utilisateur** > **Paramètres du compte**.  
  
     ![langue du fuseau horaire](./media/timezone-language.png "langue du fuseau horaire")  
  
     Définissez le **Fuseau horaire principal**. Cloud App Security analyse et rassemble vos données en continu. Par défaut, le fuseau horaire pour le portail Cloud App Security est défini sur UTC. Il est important de définir le fuseau horaire principal, afin que Cloud App Security puisse dater les incidents avec précision dans votre système. Par exemple, dans le graphique d’activité, les données sont organisées par date ; ces dates étant affectées par le fuseau horaire de votre système, si vous n’avez pas modifié le fuseau horaire par défaut, vos données sont organisées en journées de 24 heures selon le fuseau horaire UTC et peuvent se voir associer un horodatage plus ou moins décalé par rapport à la réalité.  
  
     ![fuseau horaire principal](./media/master-time-zone.png "fuseau horaire principal")  
  
6.  Grâce à cet écran, vous pouvez à tout moment sauvegarder vos paramètres de portail. Cliquez sur Exporter les paramètres de portail pour créer un fichier json de tous vos paramètres de portail, y compris les règles de stratégie, les groupes d’utilisateurs et les plages d’adresses IP.  
  
     ![console de sauvegarde](./media/backup-console.png "console de sauvegarde")  
  
7.  Pour ajouter d’autres administrateurs à Cloud App Security, cliquez sur l’icône des paramètres ![icône des paramètres](./media/settings-icon.png "icône des paramètres"), puis sur **Gérer l’accès administrateur**. Ajoutez les administrateurs qui doivent avoir accès à Cloud App Security, puis cliquez sur **Fermer**.  
>[!NOTE]
>Tout utilisateur non invité (avec son propre rôle, comme un administrateur général, de mise en conformité ou de la sécurité) peut inviter d’autres utilisateurs dans Cloud App Security.
  
![gérer l’accès administrateur](./media/manage-admin-access.png "gérer l’accès administrateur")  
  
##  <a name="Adminsettings"></a> Personnaliser vos paramètres d’administration  
Pour définir vos préférences en tant qu’administrateur de Cloud App Security, cliquez sur votre nom dans la barre de menus du portail, puis sélectionnez **Paramètres utilisateur** pour définir les éléments suivants :  
  
1.  Cliquez sur **Paramètres du compte**. Vous pouvez ici personnaliser la langue que doit utiliser le portail. Vous pouvez définir la langue du portail sur la langue par défaut ou sur la langue de votre choix.  
  
     ![paramètres utilisateur personnalisés](./media/custom-user-settings.png "paramètres utilisateur personnalisés")  
  
2.  Cliquez sur **Notifications** et définissez les préférences de notification par courrier électronique et SMS pour les e-mails reçus du système.  Vous pouvez définir le niveau de gravité des alertes et des violations à recevoir par e-mail ; le niveau de gravité étant défini par stratégie, quand des violations sont déclenchées, vous recevez une notification par courrier électronique en fonction du paramètre défini ici et du paramètre de gravité défini dans la stratégie qui a été enfreinte. Les e-mails sont envoyés à l’alias associé au compte d’utilisateur administrateur que vous utilisez pour vous connecter à Cloud App Security. Entrez un numéro de téléphone afin que Cloud App Security puisse vous envoyer des SMS quand des alertes et des notifications sont envoyées et définissez le niveau de gravité pour lequel vous souhaitez recevoir des notifications par SMS.  
  
> [!NOTE] 
> Le nombre maximal d’alertes envoyées via SMS est de 10 par numéro de téléphone par jour. Notez que le jour est calculé selon le fuseau horaire UTC. 
  
  ![paramètres de notification](./media/notification-settings.png "paramètres de notification")  
  
3. Quand vous avez terminé, cliquez sur **Enregistrer**.  
  
##  <a name="IPtagsandRanges"></a> Définir des plages d’adresses IP  
Pour identifier facilement les adresses IP connues, telles que les adresses IP physiques de votre bureau, vous devez définir des plages d’adresses IP qui vous permettent de marquer et de classer les adresses de manière appropriée, ainsi que de personnaliser la façon dont les journaux et les alertes sont affichés et examinés.   
Pour plus d’informations, consultez [Balises IP](ip-tags.md).
  
## <a name="import-user-groups"></a>Importer des groupes d’utilisateurs

Quand vous connectez des applications à l’aide de connecteurs API, Cloud App Security vous permet d’importer des groupes d’utilisateurs, par exemple à partir d’Office 365 et d’Azure Active Directory.

Pour plus d’informations, consultez [Groupes d’utilisateurs](user-groups.md).

##  <a name="Adallom_mailsettings"></a>Personnaliser votre expérience  
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
  
  