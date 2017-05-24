---
title: "Intégration de SIEM à Cloud App Security | Microsoft Docs"
description: "Cette rubrique fournit des informations sur l’intégration de votre serveur SIEM à Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/14/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 4649423b-9289-49b7-8b60-04b61eca1364
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 292b4c6408aa526184aefb57ee594b72b3262ce7
ms.sourcegitcommit: cb8238610222953751ff714b346a0b4cf73ac40c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2017
---
# <a name="siem-integration"></a>Intégration à SIEM
    
Vous pouvez maintenant intégrer Cloud App Security à votre serveur SIEM pour permettre la surveillance centralisée des alertes et des activités. L’intégration à un service SIEM vous permet de mieux protéger vos applications cloud tout en conservant votre flux de travail de sécurité habituel, en automatisant les procédures de sécurité et en établissant une corrélation entre les événements cloud et locaux. L’agent SIEM de Cloud App Security s’exécute sur votre serveur, extrait les alertes et les activités de Cloud App Security et les envoie sous forme de flux continu au serveur SIEM.

Quand vous intégrez pour la première fois votre serveur SIEM à Cloud App Security, les activités et les alertes des deux derniers jours sont transférées vers le serveur SIEM, ainsi que toutes les activités et alertes (en fonction du filtre que vous sélectionnez) à partir de ce moment-là. En outre, si vous désactivez cette fonctionnalité pour une période prolongée, quand vous la réactivez, elle transfère les deux derniers jours d’alertes et d’activités, et puis toutes les alertes et activités à partir de ce moment-là.

## <a name="siem-integration-architecture"></a>Architecture d'intégration SIEM

L’agent SIEM est déployé dans le réseau de votre organisation. Lorsqu’il est déployé et configuré, il interroge les types de données qui ont été configurés (alertes et activités) à l’aide d’API RESTful de Cloud App Security.
Le trafic est ensuite envoyé via un canal HTTPS chiffré sur le port 443.

Une fois que l’agent SIEM extrait les données à partir de Cloud App Security, il envoie les messages Syslog à votre SIEM local en utilisant les configurations réseau que vous avez fournies lors de l’installation (TCP ou UDP avec un port personnalisé). 

![Architecture d'intégration SIEM](./media/siem-architecture.png)

## <a name="sample-siem-logs"></a>Exemples de journaux SIEM

Les journaux fournis à votre serveur SIEM à partir de Cloud App Security sont de type CEF sur Syslog. Dans les exemples de journaux suivants, vous pouvez voir le type d’événement généralement envoyé par Cloud App Security à votre serveur SIEM. Dans ces exemples, vous pouvez voir quand l’alerte a été déclenchée, le **type d’événement**, la **stratégie** qui a été enfreinte, **l’utilisateur** qui a déclenché l’événement, **l’application** utilisée par l’utilisateur pour créer la violation de la sécurité et **l’URL** d’où provient l’alerte :

Exemple de journal d’activité : 
  
2017-05-12T13:15:32.131Z CEF:0|MCAS|SIEM_Agent|0.97.33|EVENT_CATEGORY_UPLOAD_FILE|**Charger un fichier**|0|externalId=AVv8zNojeXPEqTlM-j6M start=1494594932131 end=1494594932131 msg=**Charger un fichier : passwords.txt** **suser=admin@contoso.com** destination**ServiceName=Jive Software** dvc= requestClientApplication= cs1Label=**portalURL cs1=https://contoso.cloudappsecurity.com**/#/audits?activity.id\=eq(AVv8zNojeXPEqTlM-j6M,) cs2Label=uniqueServiceAppIds cs2=APPID_JIVE cs3Label=targetObjects cs3=test.txt c6a1Label="Adresse IPv6 de l’appareil" c6a1=



Exemple de journal d’alerte : 

2017-05-12T13:25:57.640Z CEF:0|MCAS|SIEM_Agent|0.97.33|ALERT_CABINET_EVENT_MATCH_AUDIT|asddsddas|3|externalId=5915b7e50d5d72daaf394da9 start=1494595557640 end=1494595557640 msg=**La stratégie d’activité 'connexions à Jive'** a été déclenchée par 'admin@contoso.com' **suser=admin@contoso.com** destination**ServiceName=Jive Software** cn1Label=riskScore cn1= cs1Label=portal**URL cs1=https://contoso.cloudappsecurity.com**/#/alerts/5915b7e50d5d72daaf394da9 cs2Label=uniqueServiceAppIds cs2=APPID_JIVE cs3Label=relatedAudits cs3=AVv81ljWeXPEqTlM-j-j


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

1. Dans le portail Cloud App Security, sous l’icône Paramètres, cliquez sur **Agents SIEM**.

2. Cliquez sur Ajouter un agent SIEM pour démarrer l’Assistant.
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

1. [Téléchargez le fichier .zip à partir du Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/?linkid=838596) et décompressez-le.

2. Extrayez le fichier .jar du fichier ZIP et exécutez-le sur votre serveur.
 Après avoir exécuté le fichier, exécutez la commande suivante :
    
      java -jar mcas-siemagent-0.87.20-signed.jar [--logsDirectory NOM_RÉPERTOIRE] [--proxy ADRESSE[:PORT]] --token JETON
> [!NOTE]
> - Le nom de fichier peut différer selon la version de l’agent SIEM.
> - Les paramètres entre crochets [] sont facultatifs et doivent être utilisés seulement si nécessaire.

Où les variables suivantes sont utilisées :
- NOM_RÉPERTOIRE est le chemin du répertoire à utiliser pour les journaux de débogage de l’agent local.
- ADRESSE[:PORT] est l’adresse et le port du serveur proxy que le serveur utilise pour se connecter à Internet.
- JETON est le jeton de l’agent SIEM que vous avez copié à l’étape précédente.

Vous pouvez taper -h à tout moment pour obtenir de l’aide.



### <a name="step-3-validate-that-the-siem-agent-is-working"></a>Étape 3 : Vérifiez que l’agent SIEM fonctionne

1. Vérifiez que l’agent SIEM n’affiche pas l’état **Erreur de connexion** ou **Déconnecté** dans le portail Cloud App Security et qu’il ne fait pas l’objet de notifications. L’agent affiche l’état **Erreur de connexion** si la connexion est interrompue depuis plus de deux heures, et l’état **Déconnecté** si la connexion est interrompue depuis plus de 12 heures.
 ![SIEM déconnecté](./media/siem-not-connected.png)
 
   Au lieu de cela, l’état doit être connecté, comme illustré ici :  ![SIEM connecté](./media/siem-connected.png)

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

## <a name="see-also"></a>Voir aussi  
[Résolution des problèmes d’intégration de SIEM](troubleshooting-siem.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  