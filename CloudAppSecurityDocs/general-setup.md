---
title: "Configuration générale | Documentation Microsoft"
description: "Cette rubrique présente les premières étapes pour rendre Cloud App Security opérationnel."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 2e7e57b0-db54-4d75-896c-4700dd9abe48
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2d39b26629579905ea30f3f769ca2a16121d51d1
ms.openlocfilehash: b617a488dec97deb7c1e1d89cbaa62e496e18891


---

# <a name="general-setup"></a>Configuration générale
La procédure suivante fournit des instructions pour configurer [!INCLUDE[Adallom1](./includes/adallom1_md.md)] afin qu’il fonctionne dans votre environnement cloud.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Votre organisation doit détenir une licence Cloud App Security pour pouvoir utiliser le produit. Pour plus d’informations, consultez [How to buy Cloud App Security](https://www.microsoft.com/server-cloud/products/cloud-app-security/default.aspx) (Comment acheter Cloud App Security) et vérifiez les [ressources de gestion des licences](https://www.microsoft.com/server-cloud/products/cloud-app-security/default.aspx).  
  
     Pour la prise en charge de l’activation client, voir [Contacter le support Office 365 pour les entreprises - Aide de l’administrateur](https://support.office.com/article/Contact-Office-365-for-business-support-Admin-Help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b).  
  
> [!NOTE] 
> Aucune licence Office 365 n’est nécessaire pour Cloud App Security.  
  
-   Une fois que vous avez acheté une licence Cloud App Security, vous recevez un e-mail contenant des informations sur l’activation et un lien vers le portail Cloud App Security.  
  
-   Pour configurer Cloud App Security, vous devez être un administrateur général, un administrateur de mise en conformité ou un administrateur de la sécurité dans Azure Active Directory ou Office 365. Il est important de comprendre qu’un utilisateur auquel est affecté un rôle d’administrateur a les mêmes autorisations sur toutes les applications cloud auxquelles votre organisation s’est abonnée, que vous affectiez le rôle dans le portail Office 365, dans le portail Azure classique ou à l’aide du module Azure AD pour Windows PowerShell. Pour plus d’informations, consultez [Attribution de rôles d’administrateur dans Office 365](https://support.office.com/article/Assigning-admin-roles-in-Office-365-eac4d046-1afd-4f1a-85fc-8219c79e1504) et [Attribution de rôles d’administrateur dans Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-assign-admin-roles/).  
  
-   Pour exécuter le portail Cloud App Security, utilisez Internet Explorer 11, Microsoft Edge (dernière version), Google Chrome (dernière version), Mozilla Firefox (dernière version) ou Apple Safari (dernière version).  
  
## <a name="set-up-the-portal"></a>Configurer le portail  
  
1.  Pour accéder au portail Cloud App Security, accédez à [https://portal.cloudappsecurity.com](https://portal.cloudappsecurity.com).  
  
     Vous pouvez également accéder au portail par le biais du **Centre d’administration Office 365** en cliquant sur l’icône Centres d’administration ![icône Centres d’administration O365](./media/o365-admin-centers-icon.png "O365 admin centers icon"), puis sur **Cloud App Security**.  
  
     ![Accès à partir d’O365](./media/access-from-o365.png "Access from O365")  
  
2.  Dans le portail Cloud App Security, dans la barre de menus, cliquez sur l’icône des paramètres ![icône des paramètres](./media/settings-icon.png "settings icon") et sélectionnez **Paramètres généraux** pour configurer les éléments suivants :  
  
3.  **Détails de l’organisation**  
  
     Il est important que vous fournissiez un **Nom d’affichage de l’organisation** pour votre organisation. Il apparaît dans les e-mails et les pages web envoyés par le système.  
  
     Fournissez un **Nom de l’environnement** (client). Cela est particulièrement important si vous gérez plusieurs clients.  
  
     Ajoutez la liste de vos **Domaines gérés**. Grâce aux domaines gérés, Cloud App Security peut déterminer quels sont les utilisateurs internes, les utilisateurs externes, ainsi que les emplacements auxquels les fichiers doivent ou non être partagés. Ce dispositif est utilisé pour les rapports, ainsi que pour les alertes.  
> [!NOTE] 
> Les utilisateurs dans des domaines qui ne sont pas configurés comme internes seront marqués comme externes et aucune recherche d’activités ni de fichiers ne sera effectuée.
   
Vous pouvez également fournir un **Logo**, qui apparaît dans les notifications par courrier électronique et les pages web envoyées par le système. Le logo doit être un fichier png avec une taille maximale de 150 x 50 pixels sur un arrière-plan transparent.  
  
4.  **Paramètres de confidentialité d’e-mail du journal d’activité**  
  
     Quand des e-mails sont détectés à partir d’Exchange Online, il est possible de définir la façon dont ils sont affichés, afin de préserver la confidentialité. Plusieurs options sont disponibles pour l’affichage d’un e-mail : **Ligne Objet masquée**, **Ligne Objet entière** ou **Afficher l’ID d’e-mail uniquement**.  
  
     ![paramètres généraux](./media/general-settings.png "general settings")  
  
5.  **Paramètres linguistiques et régionaux**  
  
     Définissez la **Langue** à utiliser par défaut pour le portail. Pour modifier la langue pour un administrateur spécifique, accédez à **Paramètres utilisateur** > **Paramètres du compte**.  
  
     ![langue du fuseau horaire](./media/timezone-language.png "timezone language")  
  
     Définissez le **Fuseau horaire principal**. Cloud App Security analyse et rassemble vos données en continu. Par défaut, le fuseau horaire pour le portail Cloud App Security est défini sur UTC. Il est important de définir le fuseau horaire principal, afin que Cloud App Security puisse dater les incidents avec précision dans votre système. Par exemple, dans le graphique d’activité, les données sont organisées par date ; ces dates étant affectées par le fuseau horaire de votre système, si vous n’avez pas modifié le fuseau horaire par défaut, vos données sont organisées en journées de 24 heures selon le fuseau horaire UTC et peuvent se voir associer un horodatage plus ou moins décalé par rapport à la réalité.  
  
     ![fuseau horaire principal](./media/master-time-zone.png "master time zone")  
  
6.  Grâce à cet écran, vous pouvez à tout moment sauvegarder vos paramètres de portail. Cliquez sur Exporter les paramètres de portail pour créer un fichier json de tous vos paramètres de portail, y compris les règles de stratégie, les groupes d’utilisateurs et les plages d’adresses IP.  
  
     ![console de sauvegarde](./media/backup-console.png "backup console")  
  
7.  Pour ajouter d’autres administrateurs à Cloud App Security, cliquez sur la dent Paramètres ![icône des paramètres](./media/settings-icon.png "settings icon"), puis sur **Gérer l’accès administrateur**. Ajoutez les administrateurs qui doivent avoir accès à Cloud App Security, puis cliquez sur **Fermer**.  
>[!NOTE]
>Tout utilisateur non invité (avec son propre rôle, comme un administrateur général, de mise en conformité ou de la sécurité) peut inviter d’autres utilisateurs dans Cloud App Security.
  
![gérer l’accès administrateur](./media/manage-admin-access.png "manage admin access")  
  
##  <a name="a-nameadminsettingsa-customize-your-admin-settings"></a><a name="Adminsettings"></a> Personnaliser vos paramètres d’administration  
Pour définir vos préférences en tant qu’administrateur de Cloud App Security, cliquez sur votre nom dans la barre de menus du portail, puis sélectionnez **Paramètres utilisateur** pour définir les éléments suivants :  
  
1.  Cliquez sur **Paramètres du compte**. Vous pouvez ici personnaliser la langue que doit utiliser le portail. Vous pouvez définir la langue du portail sur la langue par défaut ou sur la langue de votre choix.  
  
     ![paramètres utilisateur personnalisés](./media/custom-user-settings.png "custom user settings")  
  
2.  Cliquez sur **Notifications** et définissez les préférences de notification par courrier électronique et SMS pour les e-mails reçus du système.  Vous pouvez définir le niveau de gravité des alertes et des violations à recevoir par e-mail ; le niveau de gravité étant défini par stratégie, quand des violations sont déclenchées, vous recevez une notification par courrier électronique en fonction du paramètre défini ici et du paramètre de gravité défini dans la stratégie qui a été enfreinte. Les e-mails sont envoyés à l’alias associé au compte d’utilisateur administrateur que vous utilisez pour vous connecter à Cloud App Security. Entrez un numéro de téléphone afin que Cloud App Security puisse vous envoyer des SMS quand des alertes et des notifications sont envoyées et définissez le niveau de gravité pour lequel vous souhaitez recevoir des notifications par SMS.  
  
> [!NOTE] 
> Le nombre maximal d’alertes envoyées via SMS est de 10 par numéro de téléphone par jour. Notez que le jour est calculé selon le fuseau horaire UTC. 
  
  ![paramètres de notification](./media/notification-settings.png "notification settings")  
  
  
3. Quand vous avez terminé, cliquez sur **Enregistrer**.  
  
##  <a name="a-nameiptagsandrangesa-organize-the-data-according-to-your-needs"></a><a name="IPtagsandRanges"></a> Organiser les données selon vos besoins  
Pour identifier facilement les adresses IP connues, telles que les adresses IP physiques de votre bureau, vous devez définir des plages d’adresses IP qui vous permettent de marquer et de classer les adresses de manière appropriée, ainsi que de personnaliser la façon dont les journaux et les alertes sont affichés et examinés.   
Chaque groupe de plages IP peut être classé selon une liste de catégories d’adresses IP prédéfinies ou marqué avec des étiquettes IP créées par vos soins. En outre, ce paramètre vous permet de remplacer les informations de géolocalisation publiques en fonction de votre connaissance du réseau interne.  
  
IPv4 et IPv6 sont pris en charge.  
  
Dans la barre de menus, cliquez sur l’icône des paramètres ![icône des paramètres](./media/settings-icon.png "settings icon") et sélectionnez **Plages d’adresses IP**. Cliquez sur **Ajouter une plage d’adresses IP** et définissez les éléments suivants :  
  
> [!NOTE]  
>  L’emplacement et l’ISP enregistré remplacent les valeurs par défaut.   
> Toutefois, les étiquettes IP sont ajoutées à l’activité sans remplacer les données.  
  
1.  Affectez un **Nom** à votre plage IP. Le nom n’apparaît pas dans le journal des activités ; il sert uniquement à gérer votre plage IP.  
  
     Pour inclure la plage IP dans une catégorie d’adresses IP, sélectionnez une catégorie dans le menu déroulant.  
  
2.  Entrez la **plage d’adresses IP** que vous souhaitez configurer, puis cliquez sur le bouton « + ». Vous pouvez ajouter autant d’adresses et de sous-réseaux IP que vous le souhaitez en utilisant la notation de préfixe réseau (également appelée notation CIDR), par exemple 192.168.1.0/32.  
  
3.  Dans les champs qui permettent de **remplacer l’emplacement** ou l’ISP de l’organisation associés à ces adresses, entrez la nouvelle valeur. Par exemple, si vous avez une adresse IP publiquement considérée en Irlande, alors qu’elle se trouve aux États-Unis, vous pouvez remplacer ce paramètre.  
  
4.  Entrez un **ISP enregistré**. Cette opération remplace les données dans vos activités.  
  
5.  Pour **étiqueter** les activités liées à ces adresses IP, entrez une étiquette. Il suffit d’entrer un mot dans la zone pour créer l’étiquette. Une fois l’étiquette configurée, vous pouvez l’ajouter facilement à des plages IP supplémentaires en la sélectionnant dans la liste. Vous pouvez ajouter autant d’étiquettes IP que vous le souhaitez pour chaque plage. Vous pouvez utiliser des étiquettes IP quand vous créez des stratégies.  
  
     Des **balises IP** Cloud App Security intégrées sont définies pour les adresses à risque et sont constamment mises à jour. Ces balises incluent les proxys anonymes, les fournisseurs satellites, les nœuds de sortie Tor et le réseau du proxy Cloud App Security. Ces balises intégrées ne sont pas visibles.  
  
6.  Les **catégories IP** permettent d’identifier facilement les activités liées aux adresses IP intéressantes. Les catégories sont disponibles dans le portail, mais nécessitent une configuration utilisateur pour déterminer les adresses IP à inclure dans chaque catégorie, à l’exception de la catégorie « Risqué » qui comprend deux balises IP : Proxy anonyme et Tor.  
  
     Les catégories IP suivantes sont disponibles :  
  
    -   **Administratif** : adresses IP de vos administrateurs  
  
    -   **Interne** : adresses IP de votre réseau interne, de vos succursales et adresses d’itinérance Wi-Fi.  
  
    -   **Risqué** : toutes les adresses IP que vous considérez comme risquées. Celles-ci peuvent inclure les adresses IP suspectes déjà constatées, les adresses IP appartenant aux réseaux de vos concurrents, etc.  
  
    -   **VPN** : toutes les adresses IP que vous utilisez pour les télétravailleurs  
  
    -   **Proxy du cloud** : adresse IP de votre proxy dans le cloud  
  
7.  Quand vous avez terminé, cliquez sur **Créer**.  
  
     ![plage de nouvelles adresses IP](./media/newipaddress-range.png "newipaddress range")  
  
##  <a name="a-nameadallommailsettingsa-personalize-your-experience"></a><a name="Adallom_mailsettings"></a>Personnaliser votre expérience  
Dans la barre de menus, cliquez sur l’icône des paramètres ![icône des paramètres](./media/settings-icon.png "settings icon") et sélectionnez **Paramètres de messagerie** pour définir les paramètres des notifications par courrier électronique envoyées par Cloud App Security aux administrateurs ; ce paramétrage définit l’envoi des alertes et des notifications aux utilisateurs finaux concernant les violations dans lesquelles ils sont impliqués.  
  
![menu des paramètres de messagerie](./media/mail-setting-menu.png "mail setting menu")  
  
Configurez ce qui suit :  
  
1.  **Adresse de l’expéditeur** : compte de messagerie à utiliser pour envoyer la notification.  
  
     **Nom complet de l’expéditeur** : nom à afficher dans le champ **De** de l’e-mail.  
  
     **Adresse e-mail de réponse** : compte e-mail à utiliser pour les réponses au message.  
  
     ![configuration des paramètres de messagerie](./media/mail-settings-config.png "mail settings config")  
  
2.  Vous pouvez utiliser un fichier html pour personnaliser et créer les e-mails envoyés par le système. Le fichier html utilisé pour votre modèle doit inclure les éléments suivants :  
  
    -   Tout le code CSS du modèle doit être inséré dans celui-ci.  
  
    -   Le modèle doit avoir trois espaces réservés non modifiables :  
  
         %%logo%% : URL vers le logo de votre société chargée par le biais de la page Paramètres généraux  
  
         %%title%% : espace réservé pour le titre de l’e-mail, tel que défini par la stratégie  
  
         %%content%% : espace réservé pour le contenu à inclure pour les utilisateurs finaux, tel que défini par la stratégie  
  
     Voici un exemple de modèle d’e-mail :  
  
    ```  
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
  
3.  Cliquez sur **Charger un modèle...** et sélectionnez le fichier que vous avez créé.  
  
     Ensuite, cliquez sur **Envoyer un e-mail test** pour vous envoyer un e-mail test afin de voir un exemple du modèle que vous avez créé.  
     L’e-mail est envoyé au compte que vous avez utilisé pour vous connecter au portail. L’e-mail test comprend les champs de métadonnées, le modèle, l’objet de l’e-mail, le titre dans le corps de l’e-mail et le contenu.  
  
## <a name="single-sign-on"></a>Authentification unique  
Cloud App Security est couplé à Azure Active Directory pour les activités d’authentification, de configuration et de gestion des licences. Pour plus d’informations sur la gestion de l’authentification unique, voir [Liste de compatibilité de fédération Azure Active Directory : fournisseurs d’identité tiers qui peuvent être utilisés pour implémenter l’authentification unique](https://msdn.microsoft.com/library/azure/jj679342.aspx).  


> [!NOTE] 
> Si vous utilisez ExpressRoute, Cloud App Security est déployé dans Azure et entièrement intégré à [ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/). Toutes les interactions avec les applications Cloud App Security et le trafic envoyé vers Cloud App Security, notamment le chargement des journaux de découverte, sont acheminés via l’**homologation publique** ExpressRoute pour améliorer la latence, les performances et la sécurité. Aucune étape de configuration n’est nécessaire côté client.  
    Pour plus d’informations sur l’homologation publique, consultez [Circuits ExpressRoute et domaines de routage](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/).  
    
## <a name="see-also"></a>Voir aussi  
[Configurer Cloud Discovery](set-up-cloud-discovery.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Nov16_HO2-->


