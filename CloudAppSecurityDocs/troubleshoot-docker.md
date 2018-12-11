---
title: Résolution des problèmes du déploiement du docker Cloud Discovery | Microsoft Docs
description: Cet article décrit la procédure de modification de la configuration du docker Cloud Discovery Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/9/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 776e834f-3c20-4d5f-9fab-4c5b975edb06
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 69ff240426b86a254128e241c66c59fff1a10c36
ms.sourcegitcommit: c497253a7ab63973bb806607e5f15dece91640be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53122993"
---
# <a name="troubleshooting-the-microsoft-cloud-app-security-cloud-discovery-deployment"></a>Résolution des problèmes liés au déploiement Cloud Discovery de Microsoft Cloud App Security

*S’applique à : Microsoft Cloud App Security*

Cet article décrit comment modifier la configuration du docker Cloud Discovery Cloud App Security.

## <a name="windows-defender-atp-integration"></a>Intégration de Windows Defender ATP

Si vous avez intégré Windows Defender ATP à Cloud App Security et que vous ne voyez pas les résultats de cette intégration (aucun rapport **Utilisateurs de point de terminaison Win10**), vérifiez que les ordinateurs auxquels vous vous connectez disposent de Windows 10 version 1809 ou ultérieure et que vous avez attendu les deux heures nécessaires pour que vos données soient accessibles.

## <a name="docker-deployment"></a>Déploiement de Docker

Il peut être nécessaire de modifier la configuration du docker Cloud Discovery Cloud App Security. 

### <a name="changing-the-ftp-password"></a>Modification du mot de passe FTP

1. Connectez-vous à l’hôte du collecteur de journaux.

2. Exécutez `docker exec -it <collector name> pure-pw passwd <ftp user>`

    1. Saisissez le nouveau mot de passe.
    2. Saisissez à nouveau le nouveau mot de passe pour le confirmer.
 
3. Exécutez `docker exec -it <collector name> pure-pw mkdb` pour appliquer la modification.

  ![modifier le mot de passe FTP](./media/ftp-connect.png)

### <a name="customize-certificate-files"></a>Personnaliser les fichiers de certificats

Suivez cette procédure pour personnaliser les fichiers de certificats que vous utilisez pour obtenir des connexions sécurisées au docker Cloud Discovery.

1. Ouvrez un client FTP et connectez-vous au collecteur de journaux.

   ![Se connecter au client FTP](./media/ftp-connect.png)

2. Accédez au répertoire `ssl_update`.
3. Chargez les nouveaux fichiers de certificats dans le répertoire `ssl_update` (les noms sont obligatoires).

   ![Modifier le mot de passe FTP](./media/new-certs.png)

    - **Pour FTP :** un seul fichier est nécessaire. Le fichier a la clé et les données de certificat, dans cet ordre, et est nommé **pure-ftpd.pem**.
    - **Pour Syslog :** trois fichiers sont nécessaires (**ca.pem**, **server-key.pem et **server-cert.pem**). Si l’un des fichiers est absent, la mise à jour n’a pas lieu.

4. Sur un terminal, exécutez : `docker exec -t <collector name> update_certs`. La commande doit produire une sortie semblable à celle illustrée dans la capture d’écran suivante.

   ![Modifier le mot de passe FTP](./media/update-certs.png)

## <a name="next-steps"></a>Étapes suivantes

[Déployer Cloud Discovery](set-up-cloud-discovery.md)

[Les clients Premier peuvent également choisir Cloud App Security directement dans le portail Premier.](https://premier.microsoft.com/)
