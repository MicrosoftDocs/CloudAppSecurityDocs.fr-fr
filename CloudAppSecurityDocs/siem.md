---
title: "Intégration de SIEM à Cloud App Security | Microsoft Docs"
description: "Cette rubrique fournit des informations sur l’intégration de votre serveur SIEM à Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/10/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 4649423b-9289-49b7-8b60-04b61eca1364
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 2acabcc195b8496f0a9bda812cc11b289911b81a
ms.sourcegitcommit: 2e89f41bc2581859a24d55b700dcd89e70e730a5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2017
---
# <a name="siem-integration"></a>Intégration à SIEM
    
Vous pouvez maintenant intégrer Cloud App Security avec votre serveur SIEM pour bénéficier de la surveillance centralisée des alertes et des activités des applications connectées. Comme les nouveaux événements et nouvelles activités sont pris en charge par les applications connectées, leur visibilité est ensuite transférée dans Cloud App Security. L’intégration à un service SIEM vous permet de mieux protéger vos applications cloud tout en conservant votre flux de travail de sécurité habituel, en automatisant les procédures de sécurité et en établissant une corrélation entre les événements cloud et locaux. L’agent SIEM de Cloud App Security s’exécute sur votre serveur, extrait les alertes et les activités de Cloud App Security et les envoie sous forme de flux continu au serveur SIEM.

Quand vous intégrez pour la première fois votre serveur SIEM à Cloud App Security, les activités et les alertes des deux derniers jours sont transférées vers le serveur SIEM, ainsi que toutes les activités et alertes (en fonction du filtre que vous sélectionnez) à partir de ce moment-là. En outre, si vous désactivez cette fonctionnalité pour une période prolongée, quand vous la réactivez, elle transfère les deux derniers jours d’alertes et d’activités, et puis toutes les alertes et activités à partir de ce moment-là.

## <a name="siem-integration-architecture"></a>Architecture d'intégration SIEM

L’agent SIEM est déployé dans le réseau de votre organisation. Quand il est déployé et configuré, il extrait les types de données qui ont été configurés (alertes et activités) à l’aide des API RESTful de Cloud App Security.
Le trafic est ensuite envoyé via un canal HTTPS chiffré sur le port 443.

Une fois que l’agent SIEM extrait les données à partir de Cloud App Security, il envoie les messages Syslog à votre SIEM local en utilisant les configurations réseau que vous avez fournies lors de l’installation (TCP ou UDP avec un port personnalisé). 

![Architecture d'intégration SIEM](./media/siem-architecture.png)

## <a name="supported-siems"></a>SIEM pris en charge

Actuellement, Cloud App Security prend en charge Micro Focus ArcSight et le format CEF générique.

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
3. Dans l’Assistant, cliquez sur **Démarrer l’Assistant**.   
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

2. Exécutez le fichier extrait sur votre serveur :
    
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
2017-11-22T17:50:04.000Z CEF:0|MCAS|SIEM_Agent|0.111.85|EVENT_CATEGORY_LOGOUT|Log out|0|externalId=1511373015679_167ae3eb-ed33-454a-b548-c2ed6cea6ef0 rt=1511373004000 start=1511373004000 end=1511373004000 msg=Log out suser=admin@contoso.com destinationServiceName=ServiceNow dvc=13.82.149.151 requestClientApplication= cs1Label=portalURL cs1=https://contoso.portal.cloudappsecurity.com/#/audits?activity.id\=eq(1511373015679_167ae3eb-ed33-454a-b548-c2ed6cea6ef0,) cs2Label=uniqueServiceAppIds cs2=APPID_SERVICENOW cs3Label=targetObjects cs3=admin@contoso.com,admin@contoso.com,admin@contoso.com cs4Label=policyIDs cs4= c6a1Label="Device IPv6 Address" c6a1=

2017-11-28T19:40:15.000Z CEF:0|MCAS|SIEM_Agent|0.112.68|EVENT_CATEGORY_VIEW_REPORT|View report|0|externalId=1511898027370_e272cd5f-31a3-48e3-8a6a-0490c042950a rt=1511898015000 start=1511898015000 end=1511898015000 msg=View report: ServiceNow Report 23 suser=admin@contoso.com destinationServiceName=ServiceNow dvc= requestClientApplication= cs1Label=portalURL cs1=https://contoso.portal.cloudappsecurity.com/#/audits?activity.id\=eq(1511898027370_e272cd5f-31a3-48e3-8a6a-0490c042950a,) cs2Label=uniqueServiceAppIds cs2=APPID_SERVICENOW cs3Label=targetObjects cs3=23,sys_report,admin@contoso.com,admin@contoso.com,admin@contoso.com cs4Label=policyIDs cs4= c6a1Label="Device IPv6 Address" c6a1=

2017-11-28T19:25:34.000Z CEF:0|MCAS|SIEM_Agent|0.112.68|EVENT_CATEGORY_DELETE_OBJECT|Delete object|0|externalId=1511897141625_7558b33f-218c-40ff-be5d-47d2bdd6b798 rt=1511897134000 start=1511897134000 end=1511897134000 msg=Delete object: ServiceNow Object f5122008db360300906ff34ebf96198a suser=admin@contoso.com destinationServiceName=ServiceNow dvc= requestClientApplication= cs1Label=portalURL cs1=https://contoso.portal.cloudappsecurity.com/#/audits?activity.id\=eq(1511897141625_7558b33f-218c-40ff-be5d-47d2bdd6b798,) cs2Label=uniqueServiceAppIds cs2=APPID_SERVICENOW cs3Label=targetObjects cs3=,,admin@contoso.com,admin@contoso.com,admin@contoso.com cs4Label=policyIDs cs4= c6a1Label="Device IPv6 Address" c6a1=

2017-11-27T20:40:14.000Z CEF:0|MCAS|SIEM_Agent|0.112.49|EVENT_CATEGORY_CREATE_USER|Create user|0|externalId=1511815215873_824f8f8d-2ecd-439b-98b1-99a1adf7ba1c rt=1511815214000 start=1511815214000 end=1511815214000 msg=Create user: user 747518c0db360300906ff34ebf96197c suser=admin@contoso.com destinationServiceName=ServiceNow dvc= requestClientApplication= cs1Label=portalURL cs1=https://contoso.portal.cloudappsecurity.com/#/audits?activity.id\=eq(1511815215873_824f8f8d-2ecd-439b-98b1-99a1adf7ba1c,) cs2Label=uniqueServiceAppIds cs2=APPID_SERVICENOW cs3Label=targetObjects cs3=,747518c0db360300906ff34ebf96197c,sys_user,admin@contoso.com,admin@contoso.com,admin@contoso.com cs4Label=policyIDs cs4= c6a1Label="Device IPv6 Address" c6a1=

2017-11-27T20:41:20.000Z CEF:0|MCAS|SIEM_Agent|0.112.49|EVENT_CATEGORY_DELETE_USER|Delete user|0|externalId=1511815287798_bcf60601-ecef-4207-beda-3d2b8d87d383 rt=1511815280000 start=1511815280000 end=1511815280000 msg=Delete user: user 233490c0db360300906ff34ebf9619ef suser=admin@contoso.com destinationServiceName=ServiceNow dvc= requestClientApplication= cs1Label=portalURL cs1=https://contoso.portal.cloudappsecurity.com/#/audits?activity.id\=eq(1511815287798_bcf60601-ecef-4207-beda-3d2b8d87d383,) cs2Label=uniqueServiceAppIds cs2=APPID_SERVICENOW cs3Label=targetObjects cs3=,233490c0db360300906ff34ebf9619ef,,admin@contoso.com,admin@contoso.com,admin@contoso.com cs4Label=policyIDs cs4= c6a1Label="Device IPv6 Address" c6a1=

2017-11-28T19:24:55.000Z LAB-EUW-ARCTEST CEF:0|MCAS|SIEM_Agent|0.112.68|EVENT_CATEGORY_DELETE_OBJECT|Delete object|0|externalId=1511897117617_5be018ee-f676-4473-a9b5-5982527409be rt=1511897095000 start=1511897095000 end=1511897095000 msg=Delete object: ServiceNow Object b1709c40db360300906ff34ebf961923 suser=admin@contoso.com destinationServiceName=ServiceNow dvc= requestClientApplication= cs1Label=portalURL cs1=https://contoso.portal.cloudappsecurity.com/#/audits?activity.id\=eq(1511897117617_5be018ee-f676-4473-a9b5-5982527409be,) cs2Label=uniqueServiceAppIds cs2=APPID_SERVICENOW cs3Label=targetObjects cs3=,,admin@contoso.com,admin@contoso.com,admin@contoso.com cs4Label=policyIDs cs4= c6a1Label="Device IPv6 Address" c6a1=

```
Ainsi que l’exemple de fichier journal d’alertes suivant :
```
2017-07-15T20:42:30.531Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|myPolicy|3|externalId=596a7e360c204203a335a3fb start=1500151350531 end=1500151350531 msg=Activity policy ''myPolicy'' was triggered by ''admin@box-contoso.com'' suser=admin@box-contoso.com destinationServiceName=Box cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596a7e360c204203a335a3fb cs2Label=uniqueServiceAppIds cs2=APPID_BOX cs3Label=relatedAudits cs3=1500151288183_acc891bf-33e1-424b-a021-0d4370789660 cs4Label=policyIDs cs4=59f0ab82f797fa0681e9b1c7

2017-07-16T09:36:26.550Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|test-activity-policy|3|externalId=596b339b0c204203a33a51ae start=1500197786550 end=1500197786550 msg=Activity policy ''test-activity-policy'' was triggered by ''user@contoso.com'' suser=user@contoso.com destinationServiceName=Salesforce cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596b339b0c204203a33a51ae cs2Label=uniqueServiceAppIds cs2=APPID_SALESFORCE cs3Label=relatedAudits cs3=1500197720691_b7f6317c-b8de-476a-bc8f-dfa570e00349 cs4Label=policyIDs cs4=

2017-07-16T09:17:03.361Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|test-activity-policy3|3|externalId=596b2fd70c204203a33a3eeb start=1500196623361 end=1500196623361 msg=Activity policy ''test-activity-policy3'' was triggered by ''admin@contoso.com'' suser=admin@contoso.com destinationServiceName=Office 365 cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596b2fd70c204203a33a3eeb cs2Label=uniqueServiceAppIds cs2=APPID_O365 cs3Label=relatedAudits cs3=1500196549157_a0e01f8a-e29a-43ae-8599-783c1c11597d cs4Label=policyIDs cs4=

2017-07-16T09:17:15.426Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|test-activity-policy|3|externalId=596b2fd70c204203a33a3eec start=1500196635426 end=1500196635426 msg=Activity policy ''test-activity-policy'' was triggered by ''admin@contoso.com'' suser=admin@contoso.com destinationServiceName=Microsoft Office 365 admin center cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596b2fd70c204203a33a3eec cs2Label=uniqueServiceAppIds cs2=APPID_O365_PORTAL cs3Label=relatedAudits cs3=1500196557398_3e102b20-d9fa-4f66-b550-8c7a403bb4d8 cs4Label=policyIDs cs4=59f0ab35f797fa9811e9b1c7

2017-07-16T09:17:46.290Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|test-activity-policy4|3|externalId=596b30200c204203a33a4765 start=1500196666290 end=1500196666290 msg=Activity policy ''test-activity-policy4'' was triggered by ''admin@contoso.com'' suser=admin@contoso.com destinationServiceName=Microsoft Exchange Online cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596b30200c204203a33a4765 cs2Label=uniqueServiceAppIds cs2=APPID_OUTLOOK cs3Label=relatedAudits cs3=1500196587034_a8673602-7e95-46d6-a1fe-c156c4709c5d cs4Label=policyIDs cs4=

2017-07-16T09:41:04.369Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|test-activity-policy2|3|externalId=596b34b10c204203a33a5240 start=1500198064369 end=1500198064369 msg=Activity policy ''test-activity-policy2'' was triggered by ''user2@test15-adallom.com'' suser=user2@test15-adallom.com destinationServiceName=Google cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596b34b10c204203a33a5240 cs2Label=uniqueServiceAppIds cs2=APPID_33626 cs3Label=relatedAudits cs3=1500197996117_fd71f265-1e46-4f04-b372-2e32ec874cd3 cs4Label=policyIDs cs4=

```
#### <a name="sample-cloud-app-security-alerts-in-cef-format"></a>Exemples d’alertes Cloud App Security au format CEF


##### <a name="activity-logs"></a>Journaux d’activité

-   EVENT_CATEGORY_* - Catégorie générale de l’activité

-   <ACTION> - Type d’activité, tel qu’il apparaît dans le portail

-   externalId – ID d’événement

-   start – Horodatage d’activité

-   end – Horodatage d’activité

-   rt - Horodatage d’activité

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
  
  