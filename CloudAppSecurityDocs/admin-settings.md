---
title: Définir les préférences d’administration-Cloud App Security
description: Cet article fournit des instructions sur la définition des préférences d’administration dans Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 04/19/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 5114b50577d75d2301fae189e1c61275444fe2ca
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90880149"
---
# <a name="admin-user-settings"></a>Paramètres utilisateur administrateur

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Microsoft Cloud App Security vous permet de personnaliser vos paramètres utilisateur administrateur. Les paramètres de notification permettent aux administrateurs de spécifier s’ils souhaitent recevoir des notifications par e-mail ou par SMS pour les alertes.

## <a name="customize-your-admin-settings"></a><a name="Adminsettings"></a>Personnaliser vos paramètres d’administration

Pour définir vos préférences en tant qu’administrateur de Microsoft Cloud App Security, cliquez sur votre nom dans la barre de menus du portail, puis sélectionnez **Paramètres utilisateur** pour définir les paramètres suivants :

1. Cliquez sur **langue**. Ici, vous pouvez choisir la langue à utiliser dans le portail Cloud App Security.

    ![paramètres utilisateur personnalisés](media/custom-language-settings.png)

2. Cliquez sur **Notifications** et définissez les préférences de notification par courrier électronique et SMS pour les e-mails reçus du système. Vous pouvez définir le niveau de gravité des alertes et des violations à recevoir par e-mail. Le niveau de gravité est défini par stratégie. Quand des violations sont déclenchées, vous recevez une notification par e-mail en fonction du paramètre défini ici et du paramètre de gravité défini dans la stratégie qui a été enfreinte. Les e-mails sont envoyés à l’alias associé au compte d’utilisateur administrateur que vous avez utilisé pour vous connecter à Cloud App Security. Entrez un numéro de téléphone afin que Cloud App Security puisse vous envoyer des SMS quand des alertes et des notifications sont envoyées et définissez le niveau de gravité pour lequel vous souhaitez recevoir des notifications par SMS.

    > [!NOTE]
    >
    > - Le nombre maximal d’alertes envoyées via SMS est de 10 par numéro de téléphone par jour. Le jour est calculé selon le fuseau horaire UTC.
    > - Les notifications ne sont pas envoyées pour les événements de Azure Active Directory IPC.

    ![paramètres de notification](media/notification-settings.png)

3. Quand vous avez terminé, cliquez sur **Enregistrer**.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Configuration de Cloud Discovery](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]
