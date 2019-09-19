---
title: Obtenir des recommandations en matière de configuration de la sécurité pour AWS-Cloud App Security | Microsoft Docs
description: Cet article fournit des informations sur la façon d’obtenir des recommandations en matière de configuration de la sécurité dans Cloud App Security en s’intégrant à Amazon Web Services.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 8/1/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: c6d8f8af-867b-43ab-adee-f06520577fe7
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 40d8d1f578f826f1782cfbf643f8b2db136f24d2
ms.sourcegitcommit: 8a49c166424fea83853b0a6895212367526abe78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71084999"
---
# <a name="security-configuration-for-aws"></a>Configuration de la sécurité pour AWS

*S’applique à : Microsoft Cloud App Security*

Microsoft Cloud App Security vous fournit une évaluation de la configuration de la sécurité de votre environnement Amazon Web Services. Cette évaluation fournit des recommandations de sécurité fondamentales basées sur le test de la sécurité du centre de sécurité Internet (CIS) pour AWS.

## <a name="prerequisites"></a>Prérequis

- Le concentrateur de sécurité AWS doit être configuré pour toutes les régions de votre compte AWS. Pour plus d’informations, consultez [configuration du concentrateur de sécurité AWS](https://go.microsoft.com/fwlink/?linkid=2100208).
    > [!NOTE]
    > Si c’est la première fois que vous activez le hub de sécurité, plusieurs heures peuvent être nécessaires pour que les données initiales deviennent disponibles.
- Votre Amazon Web Services doit être connectée à Cloud App Security. Pour plus d’informations, consultez [connecter AWS à Microsoft Cloud App Security](connect-aws-to-microsoft-cloud-app-security.md).

## <a name="how-to-view-aws-security-recommendation"></a>Comment afficher la recommandation de sécurité AWS

1. Dans Cloud App Security, accédez à **examiner** > la configuration de la**sécurité**, puis sélectionnez l’onglet **Amazon Web services** .
    - Microsoft Cloud App Security fournit des recommandations pour les 50 premiers abonnements uniquement.
    - Il peut prendre jusqu’à 15 minutes avant que vos changements prennent effet.

     ![menu de configuration de la sécurité](media/security-configuration-menu.png)

1. Vous pouvez filtrer les recommandations par type, par ressource et par compte. En outre, vous pouvez cliquer sur l’icône de configuration de la sécurité ![Icône de configuration de la sécurité](./media/asc-icon.png) pour ouvrir la recommandation dans Amazon Security Hub pour plus d’informations et pour approfondir la recommandation.

   ![Configuration de la sécurité](media/security-configuration-aws.png)

## <a name="next-steps"></a>Étapes suivantes 
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)  
  
