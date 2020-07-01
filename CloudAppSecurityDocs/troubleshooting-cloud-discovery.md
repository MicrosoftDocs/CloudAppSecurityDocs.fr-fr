---
title: Dépannage des erreurs de Cloud Discovery-Cloud App Security
description: Cet article fournit la liste des erreurs fréquentes relatives à Cloud Discovery ainsi que des solutions recommandées pour chacune.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 04/19/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 5d4bff251e40954e6505c9f1633a927366d78df6
ms.sourcegitcommit: b15034dd50142afd8e95de22a9232f711b1eae6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85624826"
---
# <a name="troubleshooting-cloud-discovery"></a>Résolution des problèmes de Cloud Discovery

*S’applique à : Microsoft Cloud App Security*

Cet article fournit la liste des erreurs relatives à Cloud Discovery ainsi que des solutions recommandées pour chacune.

## <a name="microsoft-defender-atp-integration"></a>Intégration de Microsoft Defender ATP

Si vous avez intégré Microsoft Defender ATP avec Cloud App Security, et que vous ne voyez pas les résultats de l’intégration.

|Problème|Résolution|
|----|----|
|Les rapports **utilisateurs du point de terminaison Win10** n’apparaissent pas dans la liste|Assurez-vous que les machines auxquelles vous vous connectez sont Windows 10 version 1809 ou ultérieure, et que vous avez attendu les deux heures nécessaires pour que vos données soient accessibles.|
|Les rapports de découverte sont vides|Si l’appareil de point de terminaison se trouve derrière un proxy direct, vous pouvez envoyer des journaux à partir de votre proxy direct à l’aide d’un collecteur de journaux|

## <a name="log-parsing-errors"></a>Erreurs d’analyse du journal

Vous pouvez suivre le traitement des journaux Cloud Discovery à l’aide du journal de gouvernance. Cet article fournit des actions de résolution à entreprendre pour chaque erreur qui peut s’afficher ici.

### <a name="governance-log-errors"></a>Erreurs du journal de gouvernance

|Error|Description|Résolution|
|----|----|----|
|Type de fichier non pris en charge|Le fichier chargé n’est pas un fichier journal valide (par exemple, un fichier image).|Chargez un fichier **texte**, **zip ou **gzip** exporté directement à partir de votre pare-feu ou proxy.|
|Le format de journal ne correspond pas|Le format de journal que vous avez chargé ne correspond pas au format attendu pour cette source de données.|1. Vérifiez que le journal n’est pas endommagé. <br /> 2. Comparez et associez votre journal à l’exemple de format affiché dans la page de chargement.|
|Les transaction datent de plus de 90 jours|Toutes les transactions datent de plus de 90 jours et sont ignorées.|Exportez un nouveau journal avec des événements récents et rechargez-le.|
|Aucune transaction pour les applications cloud cataloguées|Aucune transaction pour les applications cloud reconnues ne figure dans le journal.|Vérifiez que le journal contient des informations sur le trafic sortant.|
|Type de journal non pris en charge|Quand vous sélectionnez **Data source = Other (unsupported)** [Source de données = autre (non prise en charge)], le journal n’est pas analysé. Au lieu de cela, il est envoyé à l’équipe technique Cloud App Security pour examen.|L’équipe technique Cloud App Security génère un analyseur dédié par source de données. Les sources de données les plus utilisées sont [déjà prises en charge](set-up-cloud-discovery.md). Chaque chargement d’une source de données non prise en charge est examiné et ajouté au pipeline pour les nouveaux analyseurs de sources de données. Les notifications des nouveaux analyseurs sont publiées dans le cadre des [notes de publication](release-notes.md) Cloud App Security.|

## <a name="log-collector-errors"></a>Erreurs du collecteur de journaux

|Problème|Résolution|
|----|----|
|Connexion impossible au collecteur de journaux via FTP| 1. Vérifiez que vous utilisez des informations d’identification FTP et non des informations d’identification SSH. <br />2. Vérifiez que le client FTP que vous utilisez n’est pas défini sur SFTP.  |
|Échec de la mise à jour de la configuration du collecteur | 1. Vérifiez que vous avez entré le dernier jeton d’accès. <br />2. Vérifiez dans votre pare-feu que le collecteur de journaux est autorisé à initier le trafic sortant sur le port 443.|
|Les journaux envoyés au collecteur n’apparaissent pas dans le portail | 1. Vérifiez si des tâches d’analyse ont échoué dans le journal de gouvernance.  <br />  &nbsp;&nbsp;&nbsp;&nbsp;Si tel est le cas, corrigez l’erreur avec le tableau des erreurs d’analyse du journal ci-dessus.<br /> 2. si ce n’est pas le cas, vérifiez la configuration des sources de données et du collecteur de journaux dans le portail. <br /> &nbsp;&nbsp;&nbsp;&nbsp;a. Dans la page des sources de données, vérifiez que la source de données que vous utilisez est correctement configurée. <br />&nbsp;&nbsp;&nbsp;&nbsp;b. Dans la page des collecteurs de journaux, vérifiez que la source de données est liée au collecteur de journaux approprié. <br /> 3. Vérifiez la configuration locale de l’ordinateur du collecteur de journaux local.  <br />&nbsp;&nbsp;&nbsp;&nbsp;a. Connectez-vous au collecteur de journaux via SSH et exécutez l’utilitaire collector_config.<br/>&nbsp;&nbsp;&nbsp;&nbsp;b. Vérifiez que votre pare-feu ou proxy envoie des journaux au collecteur de journaux en utilisant le protocole que vous avez défini (Syslog/TCP, Syslog/UDP ou FTP) et qu’il les envoie au port et au répertoire corrects.<br /> &nbsp;&nbsp;&nbsp;&nbsp;c. Exécutez netstat sur l’ordinateur et vérifiez qu’il reçoit les connexions entrantes à partir de votre pare-feu ou proxy <br /> 4. Vérifiez que le collecteur de journaux est autorisé à initier le trafic sortant sur le port 443. |
|État du collecteur de journaux : Créé | Le déploiement du collecteur de journaux n’a pas été effectué. Effectuez les étapes de déploiement local conformément au guide de déploiement.|
|État du collecteur de journaux : Déconnecté | Aucune donnée n’a été reçue au cours des dernières 24 heures à partir des sources de données liées. |
|Échec de l’extraction de la dernière image du collecteur| Si vous recevez cette erreur pendant le déploiement de l’amarrage, cela peut être que vous n’avez pas suffisamment de mémoire sur l’ordinateur hôte. Pour vérifier cela, exécutez la commande suivante sur l’hôte : `docker pull microsoft/caslogcollector` . Si elle retourne cette erreur, `failed to register layer: Error processing tar file(exist status 1): write /opt/jdk/jdk1.8.0_152/src.zip: no space left on device` Contactez l’administrateur de votre ordinateur hôte pour fournir davantage d’espace.|

## <a name="discovery-dashboard-errors"></a>Erreurs du tableau de bord de découverte

|Problème|Résolution|
|----|----|
|Les données de découverte ont été chargées et analysées correctement, mais le tableau de bord Cloud Discovery semble vide|Le tableau de bord est peut-être filtré sur des données qui ne sont pas présentes dans vos journaux. Dans ce cas, il n’y a aucune donnée à afficher. Essayez de changer les filtres du tableau de bord Cloud Discovery pour afficher différents types de données afin de voir les résultats.|

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
