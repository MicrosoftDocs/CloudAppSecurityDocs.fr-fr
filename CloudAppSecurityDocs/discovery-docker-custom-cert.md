---
title: Personnalisation des certificats pour le docker Cloud Discovery | Microsoft Docs
description: "Cette rubrique décrit le processus de personnalisation des certificats pour le docker Cloud Discovery."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 26/11/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 0e9c15d3-902b-4b8f-8dec-31953b4451e0
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 6052e5b7b3db9e3f69f86fbbfe9930432ce2a30c
ms.sourcegitcommit: 473d96a6383a6e4d01ef03ed31f2e773cea82cab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2017
---
# <a name="customize-certificate-files"></a>Personnaliser les fichiers de certificats

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
[Utilisation des données Cloud Discovery](working-with-cloud-discovery-data.md)  
[Pour obtenir un support technique, visitez la page de support assisté de Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)  
[Les clients Premier peuvent également choisir Cloud App Security directement dans le portail Premier.](https://premier.microsoft.com/)

