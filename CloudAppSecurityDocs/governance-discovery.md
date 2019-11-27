---
title: Blocage des applications découvertes – Cloud App Security | Microsoft Docs
description: Cet article décrit la procédure d’exportation de scripts de blocage pour les applications découvertes.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/06/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 8464851432d8fce81baa624738c6f73da1d68413
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74461359"
---
# <a name="govern-discovered-apps"></a>Gouverner les applications découvertes

*S’applique à : Microsoft Cloud App Security*

Une fois que vous avez consulté la liste des applications découvertes dans votre environnement, vous pouvez sécuriser votre environnement en approuvant les applications sécurisées (approuvées) ou en interdisant les applications indésirables **(non**approuvées **) des**manières suivantes.

## <a name="BKMK_SanctionApp"></a> Approbation/non-approbation d’une application

Pour ne pas approuver une application présentant un risque spécifique, cliquez sur les points de suspension à la fin de la ligne. Ensuite, sélectionnez **Ne pas approuver**. Vous avez toujours la possibilité d’utiliser une application non approuvée, mais grâce aux filtres Cloud Discovery vous surveillez plus facilement son utilisation. Vous pouvez alors informer les utilisateurs de l’application non approuvée et leur suggérer d’utiliser une autre application sécurisée.

![Marquer comme non approuvées](./media/tag-as-unsanctioned.png)

Si vous voulez approuver/ne pas approuver une liste d’applications, cochez les cases des applications que vous voulez gérer, puis sélectionnez l’action appropriée.

Pour interroger une liste d’applications non approuvées, vous pouvez [générer un script de bloc en utilisant les API Cloud App Security](https://us.portal.cloudappsecurity.com/api-docs/#generate-block-script).

> [!NOTE]
> Si votre locataire utilise Zscaler NSS ou iboss, toute application que vous marquez comme non approuvée est automatiquement bloquée par Cloud App Security, et les sections suivantes relatives à la création de scripts de blocage ne sont pas nécessaires. Pour plus d’informations, consultez [intégration de avec Zscaler](zscaler-integration.md) et [intégration de Cloud App Security avec iboss](iboss-integration.md) , respectivement.

## <a name="export-a-block-script-to-govern-discovered-apps"></a>Exporter un script de blocage pour gouverner les applications découvertes

Cloud App Security vous permet de bloquer l’accès aux applications non approuvées en utilisant vos appliances de sécurité locales existantes. Vous pouvez générer un script de blocage dédié et l’importer dans votre appliance. Pour cette solution, vous n’avez pas besoin de rediriger tout le trafic web de l’organisation vers un proxy.

1. Dans le tableau de bord Cloud Discovery, marquez toutes les applications que vous souhaitez bloquer comme **Non approuvées**.

    ![Marquer comme non approuvées](./media/tag-as-unsanctioned.png)

2. Dans la barre de titre, cliquez sur les trois points et sélectionnez **Générer un script de blocage...** .

    ![Générer un script de blocage](./media/generate-block-script.png)

3. Dans **Générer un script de blocage**, sélectionnez l’appliance pour laquelle vous souhaitez générer le script de blocage.

    ![Générer la fenêtre pop-up du script de blocage](./media/generate-block-script-popup.png)

4. Ensuite, cliquez sur le bouton Générer un script afin de créer un script de blocage pour toutes vos applications non approuvées. Par défaut, le fichier est renommé avec la date à laquelle il a été exporté et le type d’appliance sélectionné. *2017-02-19_CAS_Fortigate_block_script.txt* serait un exemple de nom de fichier.

   ![Bouton Générer un script de blocage](./media/generate-block-script-button.png)

5. Importez le fichier créé dans votre appliance.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
