---
title: Définir les préférences de notification par e-mail | Microsoft Docs
description: Cet article fournit des informations sur la procédure de personnalisation des notifications par e-mail envoyées par Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/27/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 8402cdc9-4969-4150-b567-ccc9d75e5370
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 6b9ec2fca122bfdfdea4e6ad298a689dd79bcaf6
ms.sourcegitcommit: 0d73d21f961dc883f01a329bcf16dcaf070dca2a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2018
ms.locfileid: "34558887"
---
*S’applique à : Microsoft Cloud App Security*


##  <a name="mailsettings"></a> Définir les préférences de notification par e-mail  

Pour définir les paramètres des e-mails de notification envoyés par Microsoft Cloud App Security aux administrateurs demandant l’envoi des alertes et des notifications aux utilisateurs finaux concernant les violations dans lesquelles ils sont impliqués, suivez cette procédure. Pour plus d’informations sur l’adresse IP du serveur de messagerie Microsoft Cloud App Security à ajouter à la liste verte de votre service antispam, consultez [Configuration requise pour le réseau](network-requirements.md). 


1. Dans la barre de menus, cliquez sur la roue dentée des paramètres ![icône des paramètres](./media/settings-icon.png "icône des paramètres") et sélectionnez **Paramètres**, puis sélectionnez l’onglet **Paramètres de messagerie**.  

 ![Paramètres de messagerie](./media/mail-settings-config.png)

2. Sous **Identité de l’expéditeur de l’e-mail** : si vous envisagez d’utiliser les paramètres de messagerie par défaut, vous n’avez pas besoin de modifier quoi que ce soit dans cette section. Si vous souhaitez personnaliser l’identité de l’expéditeur de l’e-mail, vous pouvez définir le **Nom complet de l’expéditeur**, **l’Adresse de messagerie de l'expéditeur** et **l’Adresse e-mail de réponse**. Microsoft Cloud App Security effectue cela pour vous à l’aide d’un service de messagerie tiers appelé MailChimp®. Veillez à lire et à accepter les Conditions d’utilisation et la Déclaration de confidentialité de MailChimp pour pouvoir activer cette option, sinon Microsoft Cloud App Security enverra les notifications à l’aide des paramètres par défaut.
   
   > [!NOTE]
   > Seuls les caractères Unicode sont pris en charge dans le nom complet et l’adresse e-mail conformément à la [norme rfc822](http://www.rfc-editor.org/rfc/rfc822.txt).

  
3. Pour la **Conception de l’e-mail**, vous pouvez utiliser un fichier html pour personnaliser et créer les e-mails envoyés par le système. Le fichier html utilisé pour votre modèle doit inclure les éléments suivants :  
  
   -   Tous les fichiers CSS du modèle doivent être insérés dans celui-ci.  
  
   -   Le modèle doit avoir trois espaces réservés non modifiables :  
  
        %%logo%% : URL vers le logo de votre société chargée par le biais de la page Paramètres généraux  
  
        %%title%% : espace réservé pour le titre de l’e-mail, tel que défini par la stratégie  

        %%content%% : espace réservé pour le contenu à inclure pour les utilisateurs finaux, tel que défini par la stratégie  
     
4. Cliquez sur **Charger un modèle...** et sélectionnez le fichier que vous avez créé. 

5. Ensuite, cliquez sur **Envoyer un e-mail test** pour vous envoyer un e-mail test afin de voir un exemple du modèle que vous avez créé. L’e-mail est envoyé au compte que vous avez utilisé pour vous connecter au portail. L’e-mail test comprend les champs de métadonnées, le modèle, l’objet de l’e-mail, le titre dans le corps de l’e-mail et le contenu.  Voici un exemple de modèle d’e-mail : 



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

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  