---
title: "Définir les préférences de notification par e-mail | Microsoft Docs"
description: "Cet article fournit des informations sur la procédure de personnalisation des notifications par e-mail envoyées par Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/10/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 8402cdc9-4969-4150-b567-ccc9d75e5370
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 49c2c444b0ae378584f3ddbccccf7c8b34bb50d3
ms.sourcegitcommit: 26ae7b0e1ee0ec3b2c7464a6424d4ebd1cd436ac
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2017
---
##  <a name="mailsettings"></a> Définir les préférences de notification par e-mail  
Dans la barre de menus, cliquez sur l’icône des paramètres ![icône des paramètres](./media/settings-icon.png "icône des paramètres") et sélectionnez **Paramètres de messagerie** pour définir les paramètres des notifications par e-mail envoyées par Cloud App Security aux administrateurs ; ce paramétrage définit l’envoi des alertes et des notifications aux utilisateurs finaux concernant les violations dans lesquelles ils sont impliqués.  
  
![menu des paramètres de messagerie](./media/mail-setting-menu.png "menu des paramètres de messagerie")  
  
Configurez ce qui suit :  
  
1.  **Adresse de l’expéditeur** : compte de messagerie à utiliser pour envoyer la notification.  
  
     **Nom complet de l’expéditeur** : nom à afficher dans le champ **De** de l’e-mail.  
  
     **Adresse e-mail de réponse** : compte e-mail à utiliser pour les réponses au message.  
  
     ![configuration des paramètres de messagerie](./media/mail-settings-config.png "configuration des paramètres de messagerie")  
  
2.  Pour la **Conception de l’e-mail**, vous pouvez utiliser un fichier html pour personnaliser et créer les e-mails envoyés par le système. Le fichier html utilisé pour votre modèle doit inclure les éléments suivants :  
  
    -   Tout le code CSS du modèle doit être inséré dans celui-ci.  
  
    -   Le modèle doit avoir trois espaces réservés non modifiables :  
  
         %%logo%% : URL vers le logo de votre société chargée par le biais de la page Paramètres généraux  
  
         %%title%% : espace réservé pour le titre de l’e-mail, tel que défini par la stratégie  

         %%content%% : espace réservé pour le contenu à inclure pour les utilisateurs finaux, tel que défini par la stratégie  
     
3.  Cliquez sur **Charger un modèle...** et sélectionnez le fichier que vous avez créé. 

4. Ensuite, cliquez sur **Envoyer un e-mail test** pour vous envoyer un e-mail test afin de voir un exemple du modèle que vous avez créé. L’e-mail est envoyé au compte que vous avez utilisé pour vous connecter au portail. L’e-mail test comprend les champs de métadonnées, le modèle, l’objet de l’e-mail, le titre dans le corps de l’e-mail et le contenu.  Voici un exemple de modèle d’e-mail : 



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
  

  
  

  
    
## <a name="see-also"></a>Voir aussi  
[Configurer Cloud Discovery](set-up-cloud-discovery.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  