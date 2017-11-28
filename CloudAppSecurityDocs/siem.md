---
title: "Intégration de SIEM à Cloud App Security | Microsoft Docs"
description: "Cette rubrique fournit des informations sur l’intégration de votre serveur SIEM à Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/22/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 4649423b-9289-49b7-8b60-04b61eca1364
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 298358657f775ec3a53a52112ee05af5db13ca16
ms.sourcegitcommit: 6e4eac42e553fd288da7de9c67eb79f11a420245
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2017
---
# <a name="siem-integration"></a>Intégration à SIEM
    
Vous pouvez maintenant intégrer Cloud App Security à votre serveur SIEM pour permettre la surveillance centralisée des alertes et des activités Office 365. Lorsque des activités et des événements nouveaux sont pris en charge par Office 365, leur visibilité est ensuite transférée dans Cloud App Security. L’intégration à un service SIEM vous permet de mieux protéger vos applications cloud tout en conservant votre flux de travail de sécurité habituel, en automatisant les procédures de sécurité et en établissant une corrélation entre les événements cloud et locaux. L’agent SIEM de Cloud App Security s’exécute sur votre serveur, extrait les alertes et les activités de Cloud App Security et les envoie sous forme de flux continu au serveur SIEM.

Quand vous intégrez pour la première fois votre serveur SIEM à Cloud App Security, les activités et les alertes des deux derniers jours sont transférées vers le serveur SIEM, ainsi que toutes les activités et alertes (en fonction du filtre que vous sélectionnez) à partir de ce moment-là. En outre, si vous désactivez cette fonctionnalité pour une période prolongée, quand vous la réactivez, elle transfère les deux derniers jours d’alertes et d’activités, et puis toutes les alertes et activités à partir de ce moment-là.

## <a name="siem-integration-architecture"></a>Architecture d'intégration SIEM

L’agent SIEM est déployé dans le réseau de votre organisation. Quand il est déployé et configuré, il extrait les types de données qui ont été configurés (alertes et activités) à l’aide des API RESTful de Cloud App Security.
Le trafic est ensuite envoyé via un canal HTTPS chiffré sur le port 443.

Une fois que l’agent SIEM extrait les données à partir de Cloud App Security, il envoie les messages Syslog à votre SIEM local en utilisant les configurations réseau que vous avez fournies lors de l’installation (TCP ou UDP avec un port personnalisé). 

![Architecture d'intégration SIEM](./media/siem-architecture.png)

## <a name="supported-siems"></a>SIEM pris en charge

Actuellement, Cloud App Security prend en charge HP ArcSight et le format CEF générique.

## <a name="how-to-integrate"></a>Procédure d’intégration

L’intégration à votre serveur SIEM s’effectue en trois étapes :
1. Configurez-le dans le portail Cloud App Security. 
2. Téléchargez le fichier JAR et exécutez-le sur votre serveur.
3. Vérifiez que l’agent SIEM fonctionne.

### <a name="prerequisites"></a>Conditions préalables

- Un serveur Windows ou Linux standard (il peut s’agir d’une machine virtuelle).
- Le serveur doit exécuter Java 8 ; les versions antérieures ne sont pas prises en charge.

## <a name="integrating-with-your-siem"></a>Intégration à votre serveur SIEM

### <a name="step-1-set-it-up-in-the-cloud-app-security-portal"></a>Étape 1 : Configurez-le dans le portail Cloud App Security

1. Dans le portail Cloud App Security, dans Paramètres (roue dentée), cliquez sur **Extensions de sécurité**, puis sur l’onglet **Agents SIEM**.

2. Cliquez sur l’icône plus pour démarrer l’Assistant **Ajouter un agent SIEM**.
3. Dans l’Assistant, cliquez sur **Ajouter un agent SIEM**. 
4. Dans l’Assistant, entrez un nom, **sélectionner votre format SIEM** et définissez les **paramètres avancés** appropriés pour ce format. Cliquez sur **Suivant**.

   ![Paramètres SIEM généraux](./media/siem1.png)

5. Entrez l’adresse IP ou le nom d’hôte de **l’hôte Syslog distant** et le **numéro de port Syslog**. Sélectionnez TCP ou UDP comme protocole Syslog distant.
Vous pouvez travailler avec votre administrateur de la sécurité pour obtenir ces informations si vous n’en disposez pas.
Cliquez sur **Suivant**.

  ![Paramètres Syslog distants](./media/siem2.png)

6. Sélectionnez les types de données, les **Alertes** et les **Activités** que vous voulez exporter vers votre serveur SIEM. Utilisez le curseur pour les activer et les désactiver. Par défaut, tout est sélectionné. Vous pouvez utiliser la liste déroulante **Appliquer à** pour définir des filtres pour envoyer seulement des alertes et des activités spécifiques à votre serveur SIEM.
Vous pouvez cliquer sur **Modifier et afficher un aperçu des résultats** pour vérifier que le filtre fonctionne comme prévu. Cliquez sur **Suivant**. 

  ![Paramètres des types de données](./media/siem3.png)

7. Copiez le jeton et enregistrez-le pour l’utiliser ultérieurement. Une fois que vous avez cliqué sur Terminer et que vous avez quitté l’Assistant, dans la page SIEM, vous pouvez voir l’agent SIEM que vous avez ajouté dans le tableau. Il indique qu’il est **créé** jusqu’à ce qu’il soit connecté.

### <a name="step-2-download-the-jar-file-and-run-it-on-your-server"></a>Étape 2 : Téléchargez le fichier JAR et exécutez-le sur votre serveur

1. Dans le [Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/?linkid=838596), après avoir accepté les [termes du contrat de licence logiciel](https://go.microsoft.com/fwlink/?linkid=862491), téléchargez le fichier zip et décompressez-le.

2. Extrayez le fichier .jar du fichier ZIP et exécutez-le sur votre serveur.
 Après avoir exécuté le fichier, exécutez la commande suivante :
    
        java -jar mcas-siemagent-0.87.20-signed.jar [--logsDirectory DIRNAME] [--proxy ADDRESS[:PORT]] --token TOKEN

> [!NOTE]
> - Le nom de fichier peut différer selon la version de l’agent SIEM.
> - Les paramètres entre crochets [ ] sont facultatifs et doivent être utilisés seulement si nécessaire.
> - Il est recommandé d’exécuter le fichier JAR lors du démarrage du serveur.
>   - Windows : Exécutez en tant que tâche planifiée et vérifiez que vous configurez la tâche pour qu’elle **s’exécute si l’utilisateur est connecté ou non** et que la case **Arrêter la tâche si elle s’exécute plus de** est décochée.
>   - Linux : Ajoutez la commande d’exécution avec un **&** au fichier rc.local. Par exemple : `java -jar mcas-siemagent-0.87.20-signed.jar [--logsDirectory DIRNAME] [--proxy ADDRESS[:PORT]] --token TOKEN &`

Où les variables suivantes sont utilisées :
- NOM_RÉPERTOIRE est le chemin du répertoire à utiliser pour les journaux de débogage de l’agent local.
- ADRESSE[:PORT] est l’adresse et le port du serveur proxy que le serveur utilise pour se connecter à Internet.
- JETON est le jeton de l’agent SIEM que vous avez copié à l’étape précédente.

Vous pouvez taper -h à tout moment pour obtenir de l’aide.

Voici des exemples de journaux d’activité envoyés à votre serveur SIEM :
```
    2017-07-11T19:14:55.895Z CEF:0|MCAS|SIEM_Agent|0.102.17|EVENT_CATEGORY_LOGIN|Log on|0|externalId=1499800495894_e453bc33-a7c1-48f7-8397-8ae8e2758183 start=1499800495895 end=1499800495895 msg=Log on suser=admin@contoso.com destinationServiceName=Microsoft Exchange Online dvc=13.82.149.151 requestClientApplication=Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/59.0.3071.115 Safari/537.36 machine_id_149980022970038514 cs1Label=portalURL cs1=https://cloud-app-security.com/#/audits?activity.id\=eq(1499800495894_e453bc33-a7c1-48f7-8397-8ae8e2758183,) cs2Label=uniqueServiceAppIds cs2=APPID_OUTLOOK cs3Label=targetObjects cs3=admin@contoso.com c6a1Label="Device IPv6 Address" c6a1=
    2017-07-11T19:14:56.781Z CEF:0|MCAS|SIEM_Agent|0.102.17|EVENT_CATEGORY_DOWNLOAD_FILE|Download file|0|externalId=1499800496781_2e50118e-dee7-40d7-b912-b81a10feed28 start=1499800496781 end=1499800496781 msg=Download file: file name50280117yyct6t.xlsx suser=roy@adallom.com.test destinationServiceName=Salesforce dvc=13.82.149.151 requestClientApplication=Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/59.0.3071.115 Safari/537.36 machine_id_149979855250880034 cs1Label=portalURL cs1=https://cloud-app-security/#/audits?activity.id\=eq(1499800496781_2e50118e-dee7-40d7-b912-b81a10feed28,) cs2Label=uniqueServiceAppIds cs2=APPID_SALESFORCE cs3Label=targetObjects cs3=name50280117yyct6t.xlsx c6a1Label="Device IPv6 Address" c6a1=
    2017-07-11T19:16:04.666Z CEF:0|MCAS|SIEM_Agent|0.102.17|EVENT_CATEGORY_SSO_LOGIN|Single sign-on log on|0|externalId=1499800564666_06496600-edde-4d81-a995-7632e70fb24f start=1499800564666 end=1499800564666 msg=Single sign-on log on suser=admin@contoso.com destinationServiceName=Microsoft Online Services dvc=13.82.149.151 requestClientApplication=Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/59.0.3071.115 Safari/537.36 machine_id_149980039637481908 cs1Label=portalURL cs1=https://cloud-app-security.com/#/audits?activity.id\=eq(1499800564666_06496600-edde-4d81-a995-7632e70fb24f,) cs2Label=uniqueServiceAppIds cs2=APPID_11394 cs3Label=targetObjects cs3=admin@contoso.com c6a1Label="Device IPv6 Address" c6a1=
    2017-07-12T13:28:29.067Z CEF:0|MCAS|SIEM_Agent|0.102.17|EVENT_CATEGORY_DOWNLOAD_FILE|Download file|0|externalId=1499866109067_8e3fae2c-ca5b-4163-84b6-fb9a03c4d052 start=1499866109067 end=1499866109067 msg=Download file: file CC004.txt suser=admin@box-contoso.com destinationServiceName=Box dvc=194.69.102.134 requestClientApplication=Mozilla/5.0 (Linux; Android 7.0; SAMSUNG SM-G930F Build/NRD90M) AppleWebKit/537.36 (KHTML, like Gecko) SamsungBrowser/5.0 Chrome/51.0.2704.106 Mobile Safari/537.36 cs1Label=portalURL cs1=https://cloud-app-security.com/#/audits?activity.id\=eq(1499866109067_8e3fae2c-ca5b-4163-84b6-fb9a03c4d052,) cs2Label=uniqueServiceAppIds cs2=APPID_BOX cs3Label=targetObjects cs3=CC004.txt c6a1Label="Device IPv6 Address" c6a1=
    2017-07-12T14:15:33.901Z CEF:0|MCAS|SIEM_Agent|0.102.17|EVENT_CATEGORY_UPLOAD_FILE|Upload file|0|externalId=1499868933901_72c21ebe-c206-4d8c-a41b-224035868d09 start=1499868933901 end=1499868933901 msg=Upload file: file response.txt suser=user1@test15-adallom.com destinationServiceName=Google Drive dvc=194.69.102.134 requestClientApplication=Mozilla/5.0 (Windows NT 10.0; WOW64; Trident/7.0; Touch; rv:11.0) like Gecko cs1Label=portalURL cs1=https://cloud-app-security.com/#/audits?activity.id\=eq(1499868933901_72c21ebe-c206-4d8c-a41b-224035868d09,) cs2Label=uniqueServiceAppIds cs2=APPID_26069 cs3Label=targetObjects cs3=response.txt c6a1Label="Device IPv6 Address" c6a1=
    2017-07-12T18:53:16.519Z CEF:0|MCAS|SIEM_Agent|0.102.17|EVENT_CATEGORY_LOGIN|Log on|0|externalId=1499885596519_ed261269-9b07-4418-9ded-8cad464d677f start=1499885596519 end=1499885596519 msg=Log on suser=admin@contoso.com destinationServiceName=Office 365 dvc=13.82.149.151 requestClientApplication=Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/59.0.3071.115 Safari/537.36 machine_id_149988543613557447 cs1Label=portalURL cs1=https://cloud-app-security.com/#/audits?activity.id\=eq(1499885596519_ed261269-9b07-4418-9ded-8cad464d677f,) cs2Label=uniqueServiceAppIds cs2=APPID_O365 cs3Label=targetObjects cs3=admin@contoso.com c6a1Label="Device IPv6 Address" c6a1=
```
Ainsi que l’exemple de fichier journal d’alertes suivant :
```
  2017-07-15T20:42:30.531Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|myPolicy|3|externalId=596a7e360c204203a335a3fb start=1500151350531 end=1500151350531 msg=Activity policy ''myPolicy'' was triggered by ''admin@box-contoso.com'' suser=admin@box-contoso.com destinationServiceName=Box cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596a7e360c204203a335a3fb cs2Label=uniqueServiceAppIds cs2=APPID_BOX cs3Label=relatedAudits cs3=1500151288183_acc891bf-33e1-424b-a021-0d4370789660
  2017-07-16T09:36:26.550Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|test-activity-policy|3|externalId=596b339b0c204203a33a51ae start=1500197786550 end=1500197786550 msg=Activity policy ''test-activity-policy'' was triggered by ''user@contoso.com'' suser=user@contoso.com destinationServiceName=Salesforce cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596b339b0c204203a33a51ae cs2Label=uniqueServiceAppIds cs2=APPID_SALESFORCE cs3Label=relatedAudits cs3=1500197720691_b7f6317c-b8de-476a-bc8f-dfa570e00349
  2017-07-16T09:17:03.361Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|test-activity-policy3|3|externalId=596b2fd70c204203a33a3eeb start=1500196623361 end=1500196623361 msg=Activity policy ''test-activity-policy3'' was triggered by ''admin@contoso.com'' suser=admin@contoso.com destinationServiceName=Office 365 cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596b2fd70c204203a33a3eeb cs2Label=uniqueServiceAppIds cs2=APPID_O365 cs3Label=relatedAudits cs3=1500196549157_a0e01f8a-e29a-43ae-8599-783c1c11597d
  2017-07-16T09:17:15.426Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|test-activity-policy|3|externalId=596b2fd70c204203a33a3eec start=1500196635426 end=1500196635426 msg=Activity policy ''test-activity-policy'' was triggered by ''admin@contoso.com'' suser=admin@contoso.com destinationServiceName=Microsoft Office 365 admin center cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596b2fd70c204203a33a3eec cs2Label=uniqueServiceAppIds cs2=APPID_O365_PORTAL cs3Label=relatedAudits cs3=1500196557398_3e102b20-d9fa-4f66-b550-8c7a403bb4d8
  2017-07-16T09:17:46.290Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|test-activity-policy4|3|externalId=596b30200c204203a33a4765 start=1500196666290 end=1500196666290 msg=Activity policy ''test-activity-policy4'' was triggered by ''admin@contoso.com'' suser=admin@contoso.com destinationServiceName=Microsoft Exchange Online cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596b30200c204203a33a4765 cs2Label=uniqueServiceAppIds cs2=APPID_OUTLOOK cs3Label=relatedAudits cs3=1500196587034_a8673602-7e95-46d6-a1fe-c156c4709c5d
  2017-07-16T09:41:04.369Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|test-activity-policy2|3|externalId=596b34b10c204203a33a5240 start=1500198064369 end=1500198064369 msg=Activity policy ''test-activity-policy2'' was triggered by ''user2@test15-adallom.com'' suser=user2@test15-adallom.com destinationServiceName=Google cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596b34b10c204203a33a5240 cs2Label=uniqueServiceAppIds cs2=APPID_33626 cs3Label=relatedAudits cs3=1500197996117_fd71f265-1e46-4f04-b372-2e32ec874cd3
```
#### <a name="sample-cloud-app-security-alerts-in-cef-format"></a>Exemples d’alertes Cloud App Security au format CEF


##### <a name="activity-logs"></a>Journaux d’activité

-   EVENT_CATEGORY_* - Catégorie générale de l’activité

-   <ACTION> - Type d’activité, tel qu’il apparaît dans le portail

-   externalId – ID d’événement

-   start – Horodatage de l’alerte

-   end – Horodatage de l’alerte

-   rt – Horodatage de l’alerte

-   msg – description de l’événement comme illustré dans le portail

-   suser – Utilisateur de l’activité

-   destinationServiceName – Application à l’origine de l’activité, par exemple Office 365, Sharepoint, Box.

-   dvc – IP de l’appareil client

-   requestClientApplication – Agent utilisateur de l’appareil client

-   cs<X>Label – Chaque étiquette a une signification différente, mais l’étiquette elle-même l’explique, par exemple targetObjects.

-   cs<X> - Informations correspondant à l’étiquette (utilisateur cible de l’activité ou de l’alerte, selon l’exemple d’étiquette).

##### <a name="alerts"></a>Alertes

-   <alert type> - Par exemple “ALERT_CABINET_EVENT_MATCH_AUDIT”

-   <name> - Nom de la stratégie correspondante

-   externalId – ID d’alerte

-   start – Horodatage de l’alerte

-   end – Horodatage de l’alerte

-   rt – Horodatage de l’alerte

-   msg – Description de l’alerte comme illustré dans le portail

-   suser – Utilisateur de l’objet de l’alerte

-   destinationServiceName – Application à l’origine de l’alerte, par exemple Office 365, Sharepoint, Box

-   cs<X>Label – Chaque étiquette a une signification différente, mais l’étiquette elle-même l’explique, par exemple targetObjects.

-   cs<X> - Informations correspondant à l’étiquette (utilisateur cible de l’activité ou de l’alerte, selon l’exemple d’étiquette).


### <a name="step-3-validate-that-the-siem-agent-is-working"></a>Étape 3 : Vérifiez que l’agent SIEM fonctionne

1. Vérifiez que l’agent SIEM n’affiche pas l’état **Erreur de connexion** ou **Déconnecté** dans le portail Cloud App Security et qu’il ne fait pas l’objet de notifications. L’agent affiche l’état **Erreur de connexion** si la connexion est interrompue depuis plus de deux heures, et l’état **Déconnecté** si la connexion est interrompue depuis plus de 12 heures.
 ![SIEM déconnecté](./media/siem-not-connected.png)
 
   Au lieu de cela, l’état doit être connecté, comme illustré ici : ![SIEM connecté](./media/siem-connected.png)

2. Dans votre serveur Syslog/SIEM, vérifiez que vous voyez des activités et des alertes provenant de Cloud App Security.


## <a name="regenerating-your-token"></a>Régénération de votre jeton
Si vous perdez le jeton, vous pouvez toujours le restaurer en cliquant sur les trois points à la fin de la ligne pour l’agent SIEM dans le tableau et en sélectionnant **Régénérer le jeton**.

 ![SIEM - Régénérer le jeton](./media/siem-regenerate-token.png)

## <a name="editing-your-siem-agent"></a>Modification de votre agent SIEM 
Si vous devez modifier l’agent SIEM à l’avenir, vous pouvez cliquer sur trois points à la fin de la ligne pour l’agent SIEM dans le tableau et sélectionner **Modifier**. Si vous modifiez l’agent SIEM, vous n’avez pas besoin de réexécuter le fichier .jar car il se met à jour automatiquement.

![SIEM - Modifier](./media/siem-edit.png)

## <a name="deleting-your-siem-agent"></a>Suppression de votre agent SIEM
Si vous devez supprimer l’agent SIEM à l’avenir, vous pouvez cliquer sur trois points à la fin de la ligne pour l’agent SIEM dans le tableau et sélectionner **Supprimer**.

![SIEM - Supprimer](./media/siem-delete.png)

> [!NOTE]
> Cette fonctionnalité est disponible dans la préversion publique.

## <a name="high-availability-options"></a>Options de haute disponibilité

L’agent SIEM est un point de terminaison unique qui prend en charge la récupération d’un temps d’arrêt allant jusqu'à deux jours. Le fait de disposer d’un équilibreur de charge en tant que point de terminaison client constitue une mesure supplémentaire pour la haute disponibilité.

## <a name="see-also"></a>Voir aussi  
[Résolution des problèmes d’intégration de SIEM](troubleshooting-siem.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  