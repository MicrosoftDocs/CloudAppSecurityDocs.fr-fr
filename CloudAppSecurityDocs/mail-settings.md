---
title: Définir les préférences de notification par e-mail-Cloud App Security
description: Cet article fournit des informations sur la procédure de personnalisation des notifications par e-mail envoyées par Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 2/4/2019
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 5313745b303e6ff4e8dee19f7fe496c059b15288
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90879305"
---
# <a name="email-notification-preferences"></a>Préférences de notification par e-mail

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Cet article fournit des informations sur la procédure de personnalisation des notifications par e-mail envoyées par Cloud App Security à vos utilisateurs quand une violation de la sécurité est détectée.

> [!NOTE]
> Cette personnalisation affecte uniquement les notifications envoyées à vos utilisateurs finaux, pas les notifications envoyées aux administrateurs Cloud App Security.

## <a name="set-email-notification-preferences"></a><a name="mailsettings"></a> Définir les préférences de notification par e-mail

 Microsoft Cloud App Security vous permet de personnaliser les notifications par e-mail envoyées aux utilisateurs finaux impliqués dans les violations. Pour définir les paramètres des notifications par e-mail, effectuez les étapes suivantes. Pour plus d’informations sur l’adresse IP du serveur de messagerie Microsoft Cloud App Security que vous devez autoriser dans votre service anti-courrier indésirable, consultez [Configuration réseau requise](network-requirements.md).

1. Dans la barre de menus, cliquez sur l’icône des paramètres (engrenage), sélectionnez **Paramètres**, puis sélectionnez l’onglet **Paramètres de messagerie**.

    ![Paramètres de messagerie](media/mail-settings-config.png)

2. Sous **Identité de l’expéditeur de l’e-mail** : si vous envisagez d’utiliser les paramètres de messagerie par défaut, vous n’avez pas besoin de modifier quoi que ce soit dans cette section. Si vous voulez personnaliser l’identité de l’expéditeur de l’e-mail, vous pouvez définir tous les paramètres ici pour personnaliser le champ à modifier. Vous pouvez changer tout ou partie des éléments suivants : **Nom complet de l’expéditeur**, **Adresse e-mail de l’expéditeur**, **Adresse e-mail de réponse**. Microsoft Cloud App Security effectue la personnalisation à l’aide d’un service de messagerie tiers appelé MailChimp &reg; . N’oubliez pas de consulter et d’accepter les termes du contrat de service et la déclaration de confidentialité de MailChimp avant d’activer la personnalisation. Si vous oubliez, Microsoft Cloud App Security enverra les notifications en utilisant les paramètres par défaut.

    > [!NOTE]
    > Seuls les caractères Unicode sont pris en charge dans le nom complet et l’adresse e-mail conformément à la [norme rfc822](https://www.rfc-editor.org/rfc/rfc822.txt).

3. Pour la **Conception de l’e-mail**, vous pouvez utiliser un fichier html pour personnaliser et créer les e-mails envoyés par le système. Le fichier html utilisé pour votre modèle doit inclure les éléments suivants :

    - Tous les fichiers CSS du modèle doivent être insérés dans celui-ci.

    - Le modèle doit avoir trois espaces réservés non modifiables :

        - **%%logo%%**  : URL vers le logo de votre société chargée par le biais de la page Paramètres généraux.

        - **%%title%%**  : espace réservé pour le titre de l’e-mail, tel que défini par la stratégie.

        - **%%content%%**  : espace réservé pour le contenu à inclure pour les utilisateurs finaux, tel que défini par la stratégie.

4. Cliquez sur **Charger un modèle...** et sélectionnez le fichier que vous avez créé.

5. Cliquez sur **Envoyer un e-mail test** pour vous envoyer un e-mail d’un exemple du modèle que vous avez créé. L’e-mail est envoyé au compte que vous avez utilisé pour vous connecter au portail. Dans l’e-mail de test, vous verrez et vérifierez les éléments suivants :
    - Les champs de métadonnées
    - Le modèle
    - L’objet de l’e-mail
    - Le titre dans le corps du message
    - Le contenu

## <a name="sample-email-template"></a>Exemple de modèle d’e-mail

Voici un exemple de modèle d’e-mail :

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "https://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
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

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Configuration de Cloud Discovery](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]
