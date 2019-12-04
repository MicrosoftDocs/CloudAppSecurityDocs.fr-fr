---
title: Définir les préférences d’administration – Cloud App Security | Microsoft Docs
description: Cet article fournit des instructions sur la définition des préférences d’administration dans Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 9f687be6ba51bf7d1fb64803aaabd8397de02db7
ms.sourcegitcommit: 7c93b6f93d2699d466b172590710ed01697bbdad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74720823"
---
# <a name="admin-user-settings"></a>Paramètres utilisateur administrateur

*S’applique à : Microsoft Cloud App Security*

Microsoft Cloud App Security vous permet de personnaliser vos paramètres utilisateur administrateur. Les paramètres de notification permettent aux administrateurs de spécifier s’ils souhaitent recevoir des notifications par e-mail ou par SMS pour les alertes.

## <a name="Adminsettings"></a>Personnaliser vos paramètres d’administration

Pour définir vos préférences en tant qu’administrateur de Microsoft Cloud App Security, cliquez sur votre nom dans la barre de menus du portail, puis sélectionnez **Paramètres utilisateur** pour définir les paramètres suivants :

1. Cliquez sur **Paramètres du compte**. Ici, vous pouvez définir et renouveler votre mot de passe pour accéder au portail Cloud App Security.

    ![paramètres utilisateur personnalisés](media/custom-user-settings.png "paramètres utilisateur personnalisés")

2. Cliquez sur **Notifications** et définissez les préférences de notification par courrier électronique et SMS pour les e-mails reçus du système.  Vous pouvez définir le niveau de gravité des alertes et des violations à recevoir par e-mail. Le niveau de gravité est défini par stratégie. Quand des violations sont déclenchées, vous recevez une notification par e-mail en fonction du paramètre défini ici et du paramètre de gravité défini dans la stratégie qui a été enfreinte. Les e-mails sont envoyés à l’alias associé au compte d’utilisateur administrateur que vous avez utilisé pour vous connecter à Cloud App Security. Entrez un numéro de téléphone afin que Cloud App Security puisse vous envoyer des SMS quand des alertes et des notifications sont envoyées et définissez le niveau de gravité pour lequel vous souhaitez recevoir des notifications par SMS.

    > [!NOTE]
    > Le nombre maximal d’alertes envoyées via SMS est de 10 par numéro de téléphone par jour. Le jour est calculé selon le fuseau horaire UTC.

    ![paramètres de notification](media/notification-settings.png "paramètres de notification")

3. Quand vous avez terminé, cliquez sur **Enregistrer**.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Configurer Cloud Discovery](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]
