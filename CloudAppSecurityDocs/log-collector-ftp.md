---
title: Configuration FTP du collecteur de journaux
description: Cet article décrit la procédure de modification de la configuration du docker Cloud Discovery Cloud App Security.
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: ShlomoSagir-MS
ms.date: 8/7/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 776e834f-3c20-4d5f-9fab-4c5b975edb06
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: ab97993b283df9a6669fcb475bc60d6030accbae
ms.sourcegitcommit: 39faa183e7d781660d475c79c827adbb4cc635fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68878826"
---
# <a name="log-collector-ftp-configuration"></a>Configuration FTP du collecteur de journaux

*S’applique à : Microsoft Cloud App Security*

Cet article décrit comment modifier la configuration du docker Cloud Discovery Cloud App Security.

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

    - **Pour FTP :** Un seul fichier est nécessaire. Le fichier a la clé et les données de certificat, dans cet ordre, et est nommé **pure-ftpd.pem**.
    - **Pour Syslog :** Trois fichiers sont nécessaires (**ca.pem**, **server-key.pem et **server-cert.pem**). Si l’un des fichiers est absent, la mise à jour n’a pas lieu.

4. Sur un terminal, exécutez : `docker exec -t <collector name> update_certs`. La commande doit produire une sortie semblable à celle illustrée dans la capture d’écran suivante.

    ![Modifier le mot de passe FTP](./media/update-certs.png)

## <a name="next-steps"></a>Étapes suivantes

[Déployer Cloud Discovery](set-up-cloud-discovery.md)

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier](https://premier.microsoft.com/)