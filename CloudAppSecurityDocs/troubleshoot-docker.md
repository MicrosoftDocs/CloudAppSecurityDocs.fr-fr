---
title: "Résolution des problèmes du déploiement du docker Cloud Discovery | Microsoft Docs"
description: "Cette rubrique décrit la procédure de modification de la configuration du docker Cloud Discovery Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 29/11/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 776e834f-3c20-4d5f-9fab-4c5b975edb06
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: e40eae71a84f3e2cc0ca2814c4a8f16b25a6b380
ms.sourcegitcommit: f4ec7f2cb81c9d83bb7f406ddcca91ab07790a98
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="troubleshooting-the-cloud-app-security-cloud-discovery-docker"></a>Résolution des problèmes du déploiement du docker Cloud Discovery

## <a name="changing-the-ftp-password"></a>Modification du mot de passe FTP


1. Connectez-vous à l’hôte du collecteur de journaux.

2.  Exécutez `docker exec -it <collector name> pure-pw passwd <ftp user>`

    1. Saisissez le nouveau mot de passe.
    2. Saisissez à nouveau le nouveau mot de passe pour le confirmer.
 
3.  Exécutez `docker exec -it <collector name> pure-pw mkdb` pour appliquer la modification.


  ![modifier le mot de passe FTP](./media/ftp-connect.png)

## <a name="customize-certificate-files"></a>Personnaliser les fichiers de certificats

Suivez cette procédure pour personnaliser les fichiers de certificats que vous utilisez pour obtenir des connexions sécurisées au docker Cloud Discovery.

1.  Ouvrez un client FTP et connectez-vous au collecteur de journaux.

  ![Se connecter au client FTP](./media/ftp-connect.png)

2.  Accédez au répertoire `ssl_update`.
3.  Chargez les nouveaux fichiers de certificats dans le répertoire `ssl_update` (les noms sont obligatoires).

    ![Modifier le mot de passe FTP](./media/new-certs.png)

    1.  Pour FTP : un seul fichier est nécessaire, il doit contenir la clé et les données du certificat, dans cet ordre, et être nommé **pure-ftpd.pem**.
    
    2.  Pour Syslog : trois fichiers sont nécessaires : **ca.pem**, **server-key.pem** et **server-cert.pem**. Si l’un des fichiers est absent, la mise à jour n’aura pas lieu.

4.  Sur un terminal, exécutez : `docker exec -t <collector name> update_certs`. Vous devez obtenir une sortie semblable à celle illustrée dans l’écran ci-dessous.

    ![Modifier le mot de passe FTP](./media/update-certs.png)

## <a name="see-also"></a>Voir aussi
[Déployer Cloud Discovery](set-up-cloud-discovery.md)
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)  
[Les clients Premier peuvent également choisir Cloud App Security directement dans le portail Premier.](https://premier.microsoft.com/)

