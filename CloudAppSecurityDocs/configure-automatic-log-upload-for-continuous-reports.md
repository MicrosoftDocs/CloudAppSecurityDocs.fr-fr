---
title: Configurer le chargement automatique des journaux pour des rapports continus dans Cloud App Security | Microsoft Docs
description: "Cette rubrique fournit des informations sur le chargement de journaux pour créer des rapports Cloud Discovery automatiques."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/15/2018
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: c4123272-4111-4445-b6bd-2a1efd3e0c5c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 56252b8d4bd7d69719b9ceb6fb05a9e8030f8ffd
ms.sourcegitcommit: 458e936e1ac548eda37e9bf955b439199bbdd018
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2018
---
# <a name="configure-automatic-log-upload-for-continuous-reports-on-a-virtual-appliance---deprecated"></a>Configurer le chargement automatique des journaux pour des rapports continus sur une appliance virtuelle - Déconseillé

> [!WARNING] 
> Il est fortement recommandé de configurer le chargement du journal avec [Docker](discovery-docker.md) pour un déploiement plus souple.

## <a name="technical-requirements"></a>Spécifications techniques
- Hyperviseur : HyperV ou VMware
- Espace disque : 250 Go
- Processeur : 2
- RAM : 4 Go 
- Configurez votre pare-feu, comme décrit dans [Configuration réseau requise](network-requirements#log-collector)


## <a name="log-collector-performance"></a>Performances du collecteur de journaux
Le collecteur de journaux peut gérer correctement une capacité allant jusqu’à 50 Go par heure.
Les principaux goulots d’étranglement dans le processus de collecte des journaux sont les suivants :
- Bande passante réseau : votre bande passante réseau détermine la vitesse de chargement des journaux.
- Performances d’E/S de la machine virtuelle allouées par votre service informatique : détermine la vitesse à laquelle les journaux sont écrits sur le disque du collecteur de journaux.
Le collecteur de journaux dispose d’un mécanisme de sécurité intégré qui surveille le débit auquel les journaux arrivent et le compare au débit de chargement. En cas de congestion, le collecteur de journaux commence à supprimer des fichiers journaux. Si votre configuration dépasse généralement 50 Go par heure, il est recommandé de diviser le trafic entre plusieurs collecteurs de journaux.

## <a name="set-up-and-configuration"></a>Installation et configuration  
  
### <a name="step-1--web-portal-configuration-define-data-sources-and-link-them-to-a-log-collector"></a>Étape 1 : configuration du portail web  - définir les sources de données et les lier à un collecteur de journaux  
  
1.  Accédez à la page des paramètres de chargement automatisé :  
    Dans le portail Cloud App Security, cliquez sur l’icône des paramètres ![icône des paramètres](./media/settings-icon.png "icône des paramètres"), puis sur **Collecteurs de journaux**.  
  
3.  Pour chaque pare-feu ou proxy à partir desquels vous voulez charger des journaux, créez une source de données correspondante :  
  
    a.  Cliquez sur **Ajouter une source de données**.  
  
    b.  **Nommez** votre proxy ou pare-feu.  
  
    c.  Sélectionnez l’appareil dans la liste **Source**. Si vous sélectionnez **Format de journal personnalisé** pour utiliser une appliance réseau qui n’est pas répertoriée, consultez [Utilisation de l’analyseur de journal personnalisé](custom-log-parser.md) pour obtenir des instructions de configuration.
  
    d.  Comparez votre journal à l’exemple de format de journal attendu. Si votre format de fichier journal ne correspond pas à cet exemple, vous devez ajouter votre source de données en tant qu’**Autre**.  
  
    e.  Affectez à l’option **Type de récepteur** la valeur **FTP** ou **Syslog**. Pour **Syslog**, choisissez **UDP** ou **TCP**.  
  
    f.  Répétez ce processus pour chaque pare-feu ou proxy dont les journaux peuvent être utilisés pour détecter le trafic sur votre réseau.  
  
4.  Accédez à l’onglet **Collecteurs de journaux** en haut.  
  
    a.  Cliquez sur **Ajouter un collecteur de journaux**.  
  
    b.  Donnez un **nom** au collecteur de journaux.  
  
    c.  Sélectionnez toutes les **sources de données** que vous voulez connecter au collecteur, puis cliquez sur **Mettre à jour** pour enregistrer la configuration et générer un jeton d’accès.  
![sources de données de découverte](./media/discovery-data-sources.png)
  
  > [!NOTE] 
  > - Un seul collecteur de journaux peut gérer plusieurs sources de données.
  > - Copiez le contenu de l’écran, car vous l’utiliserez lors de la configuration du collecteur de journaux pour communiquer avec Cloud App Security. Si vous avez sélectionné Syslog, ces informations incluent des informations sur le port utilisé par l’écouteur Syslog pour écouter.
4.  Si vous acceptez les [termes du contrat de licence logiciel](https://go.microsoft.com/fwlink/?linkid=862492), **téléchargez** une nouvelle machine virtuelle pour le collecteur de journaux en cliquant sur Hyper-V ou VMware. Ensuite, décompressez le fichier avec le mot de passe que vous avez reçu sur le portail.  
  
### <a name="step-2--on-premises-deployment-of-the-virtual-machine-and-network-configuration"></a>Étape 2 : déploiement local de la machine virtuelle et de la configuration réseau   

> [!NOTE] 
> La procédure suivante décrit le déploiement dans Hyper-V. La procédure de déploiement pour l’hyperviseur de machine virtuelle est légèrement différente.  

1.  Ouvrez le Gestionnaire Hyper-V.  
  
2.  Sélectionnez **Nouveau**, puis **Machine virtuelle** et cliquez sur **Suivant**.  
 ![Détection de machine virtuelle Hyper-V](./media/discovery-hyperv-virtual-machine.png "Détection de machine virtuelle Hyper-V")  
  
3.  Fournissez un **nom** à la nouvelle machine virtuelle, par exemple, CloudAppSecurityLogCollector01, puis cliquez sur **Suivant**.  
  
4.  Sélectionnez **Génération 1**, puis cliquez sur **Suivant**.  
  
5.  Affectez à la **mémoire de démarrage** la valeur **4 096 Mo**.  
        
6. Cochez **Utiliser la mémoire dynamique** pour cette machine virtuelle et cliquez sur **Suivant**.  
  
7.  Si disponible, choisissez la **connexion** réseau et cliquez sur **Suivant**.  
  
8.  Choisissez **Utiliser un disque dur virtuel existant** et sélectionnez le fichier **.vhd** qui était inclus dans le fichier Zip que vous avez téléchargé.  
  
9.  Cliquez sur **Suivant** , puis sur **Terminer**.  
    La machine est ajoutée à votre environnement Hyper-V.  
  
9. Cliquez sur la machine dans le tableau **Machines virtuelles** et cliquez sur **Démarrer**.   
  
10. Connectez-vous à la machine virtuelle du collecteur de journaux pour déterminer si une adresse DHCP lui a été attribuée : cliquez sur la machine virtuelle, puis sélectionnez **Connect** (Connecter). Vous devez voir l’invite de connexion. Si vous voyez une adresse IP, vous pouvez vous connecter à la machine virtuelle à l’aide d’un outil Terminal Server/SSH.  Si vous ne voyez pas une adresse IP, connectez-vous en utilisant les outils de connexion Hyper-V/VMWare avec les informations d’identification que vous avez copiées quand vous avez créé le collecteur de journaux précédemment. Vous pouvez modifier le mot de passe et configurer la machine virtuelle à l’aide de l’utilitaire de configuration réseau en exécutant la commande suivante :
```
sudo network_config
```
> [!NOTE]
> La machine virtuelle est préconfigurée pour obtenir une adresse IP d’un serveur DHCP. Si vous avez besoin de configurer une adresse IP statique, une passerelle par défaut, un nom d’hôte, des serveurs DNS et NTPS, vous pouvez utiliser l’utilitaire **network_config** ou effectuer les modifications manuellement.


À ce stade, votre collecteur de journaux doit être connecté à votre réseau et en mesure d’atteindre le portail Cloud App Security.  

### <a name="step-3--on-premises-configuration-of-the-log-collection"></a>Étape 3 : configuration locale de la collecte de journaux 
La première fois que vous vous connectez au collecteur de journaux et importez sa configuration à partir du portail, procédez comme suit. 

1.  Connectez-vous au collecteur de journaux via SSH, à l’aide des informations d’identification d’administrateur interactives qui vous ont été fournies dans le portail. (S’il s’agit de votre première connexion à la console, vous devrez modifier le mot de passe et vous reconnecter après la modification. Si vous utilisez une session Terminal Server, vous devrez peut-être la redémarrer. )
2.  Exécutez l’utilitaire de configuration de collecteur avec le jeton d’accès fourni quand vous avez créé le collecteur de journaux.```sudo collector_config <access token> ```
3. Entrez le domaine de la console, par exemple : ```contoso.portal.cloudappsecurity.com```. Celui-ci est disponible à partir de l’URL qui s’affiche après la connexion au portail Cloud App Security. 

4. Entrez le nom du collecteur de journaux que vous souhaitez configurer, par exemple : **CloudAppSecurityLogCollector01** ou **NewYork** à partir de l’image précédente.

5.  Importez la configuration du collecteur de journaux à partir du portail, comme suit :  
  
      a.  Connectez-vous au collecteur de journaux via SSH, à l’aide des informations d’identification d’administrateur interactives qui vous ont été fournies dans le portail.  
  
      b.  Exécutez l’utilitaire de configuration de collecteur avec le jeton d’accès fourni dans la commande ```sudo collector_config \<access token>```.  
     
      c.  Entrez le domaine de la console, par exemple : ``` contoso.portal.cloudappsecurity.com ```
  
      d. Entrez le nom du collecteur de journaux à configurer, par exemple : ``` CloudAppSecurityLogCollector01  ```

### <a name="step-4---on-premises-configuration-of-your-network-appliances"></a>Étape 4 : configuration locale de vos équipements de réseau

Configurez vos pare-feu réseau et proxys pour exporter régulièrement les journaux vers le port Syslog dédié du répertoire FTP selon les instructions données dans la boîte de dialogue, par exemple :  
  
     `London Zscaler - Destination path: 614`  
  
     BlueCoat_HQ - Destination path: \<<machine_name>>\BlueCoat_HQ\  
  
### <a name="step-5---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>Étape 5 : vérifier la réussite du déploiement dans le portail Cloud App Security

Consultez l’état du collecteur dans le tableau **Collecteur de journaux** et vérifiez que l’état est **Connecté**. Si l’état est **Créé**, il est possible que la connexion du collecteur de journaux et l’analyse ne soient pas effectuées.

![état du collecteur de journaux](./media/log-collector-status.png)

Accédez au journal de gouvernance et vérifiez que les journaux sont régulièrement chargés sur le portail.  
  
Si vous rencontrez des problèmes lors du déploiement, consultez [Dépannage de Cloud Discovery](troubleshooting-cloud-discovery.md).

### <a name="optional---create-custom-continuous-reports"></a>Facultatif : Créer des rapports continus personnalisés

Après avoir vérifié que les journaux sont en cours de chargement dans Cloud App Security et que les rapports sont générés, vous pouvez créer des rapports personnalisés. Vous pouvez maintenant créer des rapports de découverte personnalisés basés sur les groupes d’utilisateurs Azure Active Directory. Par exemple, si vous voulez afficher l’utilisation cloud de votre service marketing, vous pouvez importer le groupe marketing à l’aide de la fonctionnalité d’importation des groupes d’utilisateurs, puis créer un rapport personnalisé pour ce groupe. Vous pouvez également personnaliser un rapport en fonction d’une balise d’adresse IP ou de plages d’adresses IP.

1. Dans le portail Cloud App Security, dans les Paramètres (roue crantée), sélectionnez **Paramètres Cloud Discovery**, puis **Gérer les rapports continus**. 
2. Cliquez sur le bouton **Créer un rapport** et renseignez les champs.
3. Sous **Filtres**, vous pouvez filtrer les données par source de données, par [groupe d’utilisateurs importé](user-groups.md) ou par [balises et plages d’adresses IP](ip-tags.md). 

> [!NOTE]
> Tous les rapports personnalisés sont limitées à 1 Go de données maximum non compressées. En cas de dépassement, le premier 1 Go de données est exporté dans le rapport.

![Rapport continu personnalisé](./media/custom-continuous-report.png)

## <a name="see-also"></a>Voir aussi  
[Utilisation des données Cloud Discovery](working-with-cloud-discovery-data.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
    
      
  