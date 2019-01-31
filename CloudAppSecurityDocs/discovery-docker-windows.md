---
title: Lancer des rapports continus pour Cloud App Security à l’aide d’un Docker sur Windows | Microsoft Docs
description: Cet article décrit la procédure de configuration du chargement automatique des journaux pour des rapports continus dans Cloud App Security à l’aide d’un Docker sur Windows dans une serveur local.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/29/2019
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: ff73a393-da43-4954-8b02-38d2a48d39b3
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 9e645becc555c73dc7403dc3075095f903e760f9
ms.sourcegitcommit: c24732bc40350c3cf416640b7d15f3c6f7be371d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2019
ms.locfileid: "55086105"
---
# <a name="docker-on-windows-on-premises"></a>Docker sur Windows en local

*S’applique à : Microsoft Cloud App Security*

Vous pouvez configurer le chargement automatique des journaux pour des rapports continus dans Cloud App Security à l’aide d’un Docker sur Windows.

## <a name="technical-requirements"></a>Spécifications techniques

- Système d’exploitation : **Windows 10** (Fall Creators Update) et Windows Server **version 1709+**

- Espace disque : 250 Go

- UC : 2

- RAM : 4 Go

- Configurez votre pare-feu, comme décrit dans [Configuration réseau requise](network-requirements.md#log-collector)

- La virtualisation du système d’exploitation doit être activée avec Hyper-V

## <a name="log-collector-performance"></a>Performances du collecteur de journaux

Le collecteur de journaux peut gérer correctement une capacité allant jusqu’à 50 Go par heure. Les principaux goulots d’étranglement dans le processus de collecte des journaux sont les suivants :

- Bande passante réseau - Votre bande passante réseau détermine la vitesse de chargement des journaux.

- Performances d’E/S de la machine virtuelle - Détermine la vitesse à laquelle les journaux sont écrits sur le disque du collecteur de journaux. Le collecteur de journaux dispose d’un mécanisme de sécurité intégré qui surveille le débit auquel les journaux arrivent et le compare au débit de chargement. En cas de congestion, le collecteur de journaux commence à supprimer des fichiers journaux. Si votre configuration dépasse généralement 50 Go par heure, nous vous recommandons de diviser le trafic entre plusieurs collecteurs de journaux.

## <a name="set-up-and-configuration"></a>Installation et configuration  

### <a name="step-1--web-portal-configuration-define-data-sources-and-link-them-to-a-log-collector"></a>Étape 1 – Configuration du portail web : Définir les sources de données et les lier à un collecteur de journaux

1. Accédez à la page de paramètres **Chargement automatique de journal**. 

     a. Dans le portail Cloud App Security, cliquez sur l’icône des paramètres, puis sur **Collecteurs de journaux**.

      ![icône des paramètres](./media/settings-icon.png)

2. Pour chaque pare-feu ou proxy à partir duquel vous souhaitez charger des journaux, créez une source de données correspondante.

     a. Cliquez sur **Ajouter une source de données**.

      ![Ajouter une source de données](./media/add-data-source.png)
          
     b. **Nommez** votre proxy ou pare-feu.
      
      ![ubuntu1](./media/ubuntu1.png)

     c. Sélectionnez l’appareil dans la liste **Source**. Si vous sélectionnez **Format de journal personnalisé** pour utiliser une appliance réseau qui n’est pas listée, consultez [Utilisation de l’analyseur de journal personnalisé](custom-log-parser.md) pour obtenir des instructions de configuration.

     d. Comparez votre journal à l’exemple de format de journal attendu. Si le format de votre fichier journal ne correspond pas à cet exemple, vous devez ajouter votre source de données en sélectionnant **Autre**.

     e. Définissez le **Type de récepteur** sur **FTP**, **FTPS**, **Syslog – UDP** ou **Syslog – TCP** ou **Syslog – TLS**.
     
     >[!NOTE]
     >L’intégration à des protocoles de transfert sécurisés (FTPS et Syslog – TLS) nécessite souvent un paramètre supplémentaire ou votre pare-feu/proxy.

      f. Répétez ce processus pour chaque pare-feu ou proxy dont les journaux peuvent être utilisés pour détecter le trafic sur votre réseau. Nous vous recommandons de configurer une source de données dédiée par appareil réseau pour vous permettre de :
     - Superviser l’état de chaque appareil séparément à des fins d’investigation
     - Explorer le Shadow IT Discovery par appareil, si chaque appareil est utilisé par un segment d’utilisateur différent

3. Accédez à l’onglet **Collecteurs de journaux** en haut.

   a. Cliquez sur **Ajouter un collecteur de journaux**.

   b. Donnez un **nom** au collecteur de journaux.

   c. Entrez l’**adresse IP de l’hôte** de la machine sur laquelle sera déployé le Docker. L’adresse IP de l’hôte peut être remplacée par le nom de l’ordinateur s’il existe un serveur DNS (ou un équivalent) qui résout le nom d’hôte.

   d. Sélectionnez toutes les **Sources de données** que vous voulez connecter au collecteur, puis cliquez sur **Mettre à jour** pour enregistrer la configuration et consulter les étapes suivantes du déploiement.

   ![ubuntu2](./media/ubuntu2.png)

   > [!NOTE]
   > - Un seul collecteur de journaux peut gérer plusieurs sources de données.
   > - Copiez le contenu de l’écran, car vous aurez besoin des informations lors de la configuration du collecteur de journaux pour communiquer avec Cloud App Security. Si vous avez sélectionné Syslog, ces informations vont inclure des informations sur le port utilisé par l’écouteur Syslog pour écouter.

4. Des informations supplémentaires sur le déploiement s’affichent. **Copiez** la commande d’exécution à partir de la boîte de dialogue. Vous pouvez utiliser l’icône de copie dans le Presse-papiers. ![icône de copie dans le Presse-papiers](./media/copy-icon.png) Vous en aurez besoin plus tard.

5. **Exportez** la configuration de sources de données attendue. Cette configuration décrit comment définir l’exportation du journal dans vos appliances.

   ![Créer le collecteur de journaux](./media/windows7.png)

### <a name="step-2--on-premises-deployment-of-your-machine"></a>Étape 2 : Déploiement local de votre ordinateur
La procédure suivante décrit le déploiement dans Windows. Les étapes de déploiement pour d’autres plateformes sont légèrement différentes.

1. Ouvrez un terminal PowerShell en tant qu’administrateur sur votre ordinateur Windows.

2. Utilisez la commande suivante pour télécharger le programme d’installation de Docker pour Windows :<br>
 `Invoke-WebRequest https://adaprodconsole.blob.core.windows.net/public-files/LogCollectorInstaller.ps1 -OutFile (Join-Path $Env:Temp LogCollectorInstaller.ps1)`
<br>Si vous souhaitez vérifier que le programme d’installation est signé par Microsoft, consultez [Valider la signature du programme d’installation](#validate-signature).

3. Pour activer l’exécution du script PowerShell, exécutez `Set-ExecutionPolicy RemoteSigned`.

4. Exécutez la commande suivante : `& (Join-Path $Env:Temp LogCollectorInstaller.ps1)`<br>
Cette commande installe le client Docker sur votre ordinateur. L’installation du conteneur de collecteur de journaux redémarre deux fois l’ordinateur et vous oblige à vous reconnecter.

5. Après chaque redémarrage, réexécutez la commande suivante à partir du répertoire où vous avez enregistré le programme d’installation : `& (Join-Path $Env:Temp LogCollectorInstaller.ps1)`<br>  

6. Avant la fin de l’installation, vous devez coller la commande d’exécution copiée précédemment.

7. Déployez l’image du collecteur sur la machine hôte en important la configuration du collecteur. Importez la configuration en copiant la commande d’exécution générée dans le portail. Si vous devez configurer un proxy, ajoutez l’adresse IP et le numéro de port du proxy. Par exemple, si les détails de votre proxy sont 192.168.10.1:8080, votre commande d’exécution mise à jour est :

           (echo db3a7c73eb7e91a0db53566c50bab7ed3a755607d90bb348c875825a7d1b2fce) | docker run --name MyLogCollector -p 21:21 -p 20000-20099:20000-20099 -e "PUBLICIP='192.168.1.1'" -e "PROXY=192.168.10.1:8080" -e "CONSOLE=mod244533.us.portal.cloudappsecurity.com" -e "COLLECTOR=MyLogCollector" --security-opt apparmor:unconfined --cap-add=SYS_ADMIN --restart unless-stopped -a stdin -i microsoft/caslogcollector starter

   ![Créer le collecteur de journaux](./media/windows7.png)
8. Vérifiez que le collecteur s’exécute correctement à l’aide de la commande suivante : `docker logs <collector_name>`

Vous devez recevoir le message suivant : **Opération correctement terminée.**

  ![ubuntu8](./media/ubuntu8.png)

### <a name="step-3---on-premises-configuration-of-your-network-appliances"></a>Étape 3 : Configuration locale de vos appliances réseau

Configurez vos pare-feu et proxys réseau pour exporter régulièrement les journaux vers le port Syslog dédié du répertoire FTP conformément aux instructions données dans la boîte de dialogue. Par exemple :

    BlueCoat_HQ - Destination path: \<<machine_name>>\BlueCoat_HQ\

### <a name="step-4---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>Étape 4 : Vérifier la réussite du déploiement dans le portail Cloud App Security

Consultez l’état du collecteur dans le tableau  **Collecteur de journaux**  et vérifiez que l’état est  **Connecté**. Si l’état est  **Créé**, il est possible que la connexion du collecteur de journaux et l’analyse n’aient pas été effectuées.

 ![ubuntu9](./media/ubuntu9.png)

Vous pouvez aussi accéder au **journal de gouvernance** et vérifier que les journaux sont régulièrement chargés sur le portail.

Si vous rencontrez des problèmes durant le déploiement, consultez  [Dépannage de Cloud Discovery](troubleshooting-cloud-discovery.md).

### Facultatif : Créer des rapports continus personnalisés <a name="continuous-reports"></a>

Vérifiez que les journaux sont chargés sur Cloud App Security et que les rapports sont générés. Après vérification, créez des rapports personnalisés. Vous pouvez créer des rapports de découverte personnalisés basés sur les groupes d’utilisateurs Azure Active Directory. Par exemple, pour voir l’utilisation cloud de votre service marketing, importez le groupe marketing à l’aide de la fonctionnalité d’importation des groupes d’utilisateurs. Créez ensuite un rapport personnalisé pour ce groupe. Vous pouvez également personnaliser un rapport en fonction d’une balise d’adresse IP ou de plages d’adresses IP.

1. Dans le portail Cloud App Security, dans les Paramètres (icône d’engrenage), sélectionnez Paramètres Cloud Discovery, puis **Rapports continus**. 
2. Cliquez sur le bouton **Créer un rapport** et renseignez les champs.
3. Sous **Filtres**, vous pouvez filtrer les données par source de données, par [groupe d’utilisateurs importé](user-groups.md) ou par [balises et plages d’adresses IP](ip-tags.md). 

![Rapport continu personnalisé](./media/custom-continuous-report.png)

### Facultatif : Valider la signature du programme d’installation <a name="validate-signature"></a>

Pour vérifier que le programme d’installation de Docker est signé par Microsoft :
1. Cliquez avec le bouton droit sur le fichier et sélectionnez **Propriétés**.
2. Cliquez sur **Signatures numériques** et vérifiez la présence du message **Cette signature numérique est valide**.  
3. Vérifiez que l’option **Microsoft Corporation** figure en tant qu’entrée unique sous **Nom du signataire**.  

![Signature numérique valide](./media/digital-signature-successful.png)

Si la signature numérique n’est pas valide, vous recevez le message **Cette signature numérique n’est pas valide** :

![La signature numérique n’est pas valide](./media/digital-signature-unsuccessful.png)

## <a name="next-steps"></a>Étapes suivantes

[Résolution des problèmes du déploiement docker Cloud Discovery](troubleshoot-docker.md)

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)

