---
title: Blocage des applications découvertes-Cloud App Security | Microsoft Docs
description: Cet article décrit la procédure d’exportation de scripts de blocage pour les applications découvertes.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/12/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: bc95cb2272d996752c60c49c7f7402550325b208
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285523"
---
# <a name="govern-discovered-apps"></a>Gouverner les applications découvertes

*S’applique à : Microsoft Cloud App Security*

Une fois que vous avez consulté la liste des applications découvertes dans votre environnement, vous pouvez sécuriser votre environnement en approuvant les applications sécurisées (approuvées) ou en interdisant les applications indésirables **(non**approuvées **) des**manières suivantes.

## <a name="BKMK_SanctionApp"></a>Approbation/non-approbation d’une application

Vous pouvez désapprouver une application à risque spécifique en cliquant sur les trois points à la fin de la ligne. **Sélectionnez ensuite**ne pas approuver. La non-approbation d’une application ne bloque pas l’utilisation, mais vous permet de surveiller plus facilement son utilisation avec les filtres de Cloud Discovery. Vous pouvez ensuite informer les utilisateurs de l’application non approuvée et suggérer une autre application sécurisée pour leur utilisation.

![Marquer comme non approuvé](media/tag-as-unsanctioned.png)

Si vous avez une liste d’applications que vous souhaitez approuver ou ne pas approuver, utilisez la case à cocher pour sélectionner les applications que vous souhaitez gérer, puis sélectionnez l’action.

Pour interroger une liste d’applications non approuvées, vous pouvez [générer un script de blocage à l’aide des api Cloud App Security](https://us.portal.cloudappsecurity.com/api-docs/#generate-block-script).

> [!NOTE]
> Si votre locataire utilise Microsoft Defender-protection avancée contre les menaces (ATP), Zscaler NSS ou iboss, toute application que vous marquez comme non approuvée est automatiquement bloquée par Cloud App Security, et les sections suivantes relatives à la création de scripts de blocage ne sont pas nécessaires. Pour plus d’informations, consultez [intégration à Microsoft Defender ATP](wdatp-integration.md), [intégration avec Zscaler](zscaler-integration.md)et [intégration avec iboss](iboss-integration.md) , respectivement.

## <a name="export-a-block-script-to-govern-discovered-apps"></a>Exporter un script de bloc pour régir les applications découvertes

Cloud App Security vous permet de bloquer l’accès aux applications non approuvées à l’aide de vos appliances de sécurité local existantes. Vous pouvez générer un script de bloc dédié et l’importer sur votre appliance. Cette solution ne requiert pas la redirection de tout le trafic Web de l’organisation vers un proxy.

1. Dans le tableau de bord Cloud Discovery, marquez toutes les **applications que vous souhaitez bloquer comme non**approuvées.

    ![Marquer comme non approuvé](media/tag-as-unsanctioned.png)

2. Dans la barre de titre, cliquez sur les trois points et sélectionnez **générer un script de bloc...** .

    ![Générer un script de bloc](media/generate-block-script.png)

3. Dans **générer un script de bloc**, sélectionnez l’appliance pour laquelle vous souhaitez générer le script de bloc.

    ![Générer une fenêtre contextuelle de blocage de script](media/generate-block-script-popup.png)

4. Ensuite, cliquez sur le bouton générer un script pour créer un script de blocage pour toutes vos applications non approuvées. Par défaut, le fichier est nommé avec la date à laquelle il a été exporté et le type d’appliance que vous avez sélectionné. *2017-02-19_CAS_Fortigate_block_script. txt* est un exemple de nom de fichier

   ![Bouton générer un script de bloc](media/generate-block-script-button.png)

5. Importez le fichier créé sur votre appliance.

## <a name="next-steps"></a>Étapes suivantes :

> [!div class="nextstepaction"]
> [Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
