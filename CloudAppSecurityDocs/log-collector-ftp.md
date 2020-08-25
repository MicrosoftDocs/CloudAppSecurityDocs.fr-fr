---
title: Configuration FTP du collecteur de journaux
description: Cet article décrit la procédure de modification de la configuration du docker Cloud Discovery Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 8/7/2019
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 53eaa7b96a22c7574a63b6051dce64076fafaa39
ms.sourcegitcommit: 29a8e66c665f51d831516924ae4d9d8047b39276
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88781665"
---
# <a name="log-collector-ftp-configuration"></a>Configuration FTP du collecteur de journaux

*S’applique à : Microsoft Cloud App Security*

Cet article décrit comment modifier la configuration du docker Cloud Discovery Cloud App Security.

## <a name="docker-deployment"></a>Déploiement de Docker

Il peut être nécessaire de modifier la configuration du docker Cloud Discovery Cloud App Security.

### <a name="changing-the-ftp-password"></a>Modification du mot de passe FTP

1. Connectez-vous à l’hôte du collecteur de journaux.

2. Exécutez `docker exec -it <collector name> pure-pw passwd <ftp user>`

    1. Saisissez le nouveau mot de passe.
    2. Saisissez à nouveau le nouveau mot de passe pour le confirmer.

3. Exécutez `docker exec -it <collector name> pure-pw mkdb` pour appliquer la modification.

    ![modifier le mot de passe FTP](media/ftp-connect.png)

### <a name="customize-certificate-files"></a>Personnaliser les fichiers de certificats

Suivez cette procédure pour personnaliser les fichiers de certificats que vous utilisez pour obtenir des connexions sécurisées au docker Cloud Discovery.

1. Ouvrez un client FTP et connectez-vous au collecteur de journaux.

    ![Se connecter au client FTP](media/ftp-connect.png)

2. Accédez au répertoire `ssl_update`.
3. Chargez les nouveaux fichiers de certificats dans le répertoire `ssl_update` (les noms sont obligatoires).

    ![Charger les fichiers de certificat](media/new-certs.png)

    - **Pour FTP :** un seul fichier est nécessaire. Le fichier a la clé et les données de certificat, dans cet ordre, et est nommé **pure-ftpd.pem**.
    - **Pour Syslog :** trois fichiers sont nécessaires (**ca.pem**, **server-key.pem et **server-cert.pem**). Si l’un des fichiers est absent, la mise à jour n’a pas lieu.

4. Sur un terminal, exécutez : `docker exec -t <collector name> update_certs`. La commande doit produire une sortie semblable à celle illustrée dans la capture d’écran suivante.

    ![Mettre à jour les fichiers de certificat](media/update-certs.png)

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Déployer Cloud Discovery](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]
