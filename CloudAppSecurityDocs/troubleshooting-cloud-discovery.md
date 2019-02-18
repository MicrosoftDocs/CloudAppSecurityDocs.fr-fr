---
title: Résolution des erreurs Cloud Discovery – Cloud App Security | Microsoft Docs
description: Cet article fournit la liste des erreurs fréquentes relatives à Cloud Discovery ainsi que des solutions recommandées pour chacune.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 76dfaebb-d477-4bdb-b3d7-04cc3fe6431d
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 966cefac08c84c92a4cdd60cb9d75c6f3af5525d
ms.sourcegitcommit: 8ef0438fa35916c48625ff750cb85e9628d202f2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56281502"
---
# <a name="troubleshooting-cloud-discovery"></a>Dépannage de Cloud Discovery

*S’applique à : Microsoft Cloud App Security*

Cet article fournit la liste des erreurs relatives à Cloud Discovery ainsi que des solutions recommandées pour chacune.

## <a name="log-parsing-errors"></a>Erreurs d’analyse du journal

Vous pouvez suivre le traitement des journaux Cloud Discovery à l’aide du journal de gouvernance. Cet article fournit des actions de résolution à entreprendre pour chaque erreur qui peut s’afficher ici.

### <a name="governance-log-errors"></a>Erreurs du journal de gouvernance

|Erreur|Description|Solution|
|----|----|----|
|Type de fichier non pris en charge|Le fichier chargé n’est pas un fichier journal valide (par exemple, un fichier image).|Chargez un fichier **texte**, **zip ou **gzip** exporté directement à partir de votre pare-feu ou proxy.|
|Le format de journal ne correspond pas|Le format de journal que vous avez chargé ne correspond pas au format attendu pour cette source de données.|1. Vérifiez que le journal n’est pas endommagé. <br /> 2. Comparez et associez votre journal à l’exemple de format illustré dans la page de chargement.|
|Les transaction datent de plus de 90 jours|Toutes les transactions datent de plus de 90 jours et sont ignorées.|Exportez un nouveau journal avec des événements récents et rechargez-le.|
|Aucune transaction pour les applications cloud cataloguées|Aucune transaction pour les applications cloud reconnues ne figure dans le journal.|Vérifiez que le journal contient des informations sur le trafic sortant.|
|Type de journal non pris en charge|Quand vous sélectionnez **Data source = Other (unsupported)** [Source de données = autre (non prise en charge)], le journal n’est pas analysé. Au lieu de cela, il est envoyé à l’équipe technique Cloud App Security pour examen.|L’équipe technique Cloud App Security génère un analyseur dédié par source de données. Les sources de données les plus utilisées sont [déjà prises en charge](set-up-cloud-discovery.md). Chaque chargement d’une source de données non prise en charge est examiné et ajouté au pipeline pour les nouveaux analyseurs de sources de données. Les notifications des nouveaux analyseurs sont publiées dans le cadre des [notes de publication](release-notes.md) Cloud App Security.|

## <a name="log-collector-errors"></a>Erreurs du collecteur de journaux

|PROBLÈME | RÉSOLUTION |
|--------|--|
|Connexion impossible au collecteur de journaux via FTP| 1. Vérifiez que vous utilisez des informations d’identification FTP et non des informations d’identification SSH. <br />2. Vérifiez que le client FTP que vous utilisez n’est pas défini sur SFTP.  |
|Échec de la mise à jour de la configuration du collecteur | 1. Vérifiez que vous avez entré le dernier jeton d’accès. <br />2. Dans votre pare-feu, vérifiez que le collecteur de journaux est autorisé à lancer le trafic sortant sur le port 443.|
|Les journaux envoyés au collecteur n’apparaissent pas dans le portail | 1.  Vérifiez si des tâches d’analyse ont échoué dans le journal de gouvernance.  <br />  &nbsp;&nbsp;&nbsp;&nbsp;Si tel est le cas, corrigez l’erreur avec le tableau des erreurs d’analyse du journal ci-dessus.<br /> 2. Si ce n’est pas le cas, vérifiez la configuration des sources de données et du collecteur de journaux dans le portail. <br /> &nbsp;&nbsp;&nbsp;&nbsp;a. Dans la page des sources de données, vérifiez que la source de données que vous utilisez est correctement configurée. <br />&nbsp;&nbsp;&nbsp;&nbsp;b. Dans la page des collecteurs de journaux, vérifiez que la source de données est liée au collecteur de journaux approprié. <br /> 3. Vérifiez la configuration locale de l’ordinateur du collecteur de journaux local.  <br />&nbsp;&nbsp;&nbsp;&nbsp;a. Connectez-vous au collecteur de journaux via SSH et exécutez l’utilitaire collector_config.<br/>&nbsp;&nbsp;&nbsp;&nbsp;b. Vérifiez que votre pare-feu ou proxy envoie des journaux au collecteur de journaux en utilisant le protocole que vous avez défini (Syslog/TCP, Syslog/UDP ou FTP) et qu’il les envoie au port et au répertoire corrects.<br /> &nbsp;&nbsp;&nbsp;&nbsp;c. Exécutez netstat sur l’ordinateur et vérifiez qu’il reçoit les connexions entrantes à partir de votre pare-feu ou proxy <br /> 4.   Vérifiez que le collecteur de journaux est autorisé à lancer le trafic sortant sur le port 443. |
|État du collecteur de journaux : Créé le | Le déploiement du collecteur de journaux n’a pas été effectué. Effectuez les étapes de déploiement local conformément au guide de déploiement.|
|État du collecteur de journaux : Disconnected | Aucune donnée n’a été reçue au cours des dernières 24 heures à partir des sources de données liées. |


## <a name="discovery-dashboard-errors"></a>Erreurs du tableau de bord de découverte

|Problème|Solution|
|----|----|
|Les données de découverte ont été chargées et analysées correctement, mais le tableau de bord Cloud Discovery semble vide|Le tableau de bord est peut-être filtré sur des données qui ne sont pas présentes dans vos journaux. Dans ce cas, il n’y a aucune donnée à afficher. Essayez de changer les filtres du tableau de bord Cloud Discovery pour afficher différents types de données afin de voir les résultats.|

## <a name="next-steps"></a>Étapes suivantes
  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)  

