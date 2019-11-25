---
title: Get security configuration recommendations for AWS - Cloud App Security | Microsoft Docs
description: This article provides information about how to Get security configuration recommendations in Cloud App Security by integrating with Amazon Web Services.
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
ms.openlocfilehash: 9e41902fd34f113412b02fb7c4377b226cd18fc0
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74460456"
---
# <a name="security-configuration-for-aws"></a>Configuration de la sécurité pour AWS

*S’applique à : Microsoft Cloud App Security*

Microsoft Cloud App Security provides you with a security configuration assessment of your Amazon Web Services environment. This assessment provides fundamental security recommendations based on the Center for Internet Security (CIS) benchmark for AWS.

## <a name="prerequisites"></a>Conditions préalables

- AWS Security Hub must be set up for all your AWS account regions. For more information, see [Setting Up AWS Security Hub](https://go.microsoft.com/fwlink/?linkid=2100208).
    > [!NOTE]
    > If this is the first time you’re enabling Security Hub, it can take several hours for the initial data to become available.
- Your Amazon Web Services must be connected to Cloud App Security. For more information, see [Connect AWS to Microsoft Cloud App Security](connect-aws-to-microsoft-cloud-app-security.md).

## <a name="how-to-view-aws-security-recommendation"></a>How to view AWS security recommendation

1. In Cloud App Security, browse to **Investigate** > **Security configuration**, and then select the **Amazon Web Services** tab.
    - Microsoft Cloud App Security fournit des recommandations pour les 50 premiers abonnements uniquement.
    - Il peut prendre jusqu’à 15 minutes avant que vos changements prennent effet.

     ![menu de configuration de la sécurité](media/security-configuration-menu.png)

1. You can filter the recommendations by type, by resource, and by accounts. En outre, vous pouvez cliquer sur l’icône de configuration de la sécurité ![Icône de configuration de la sécurité](./media/asc-icon.png) to open the recommendation in Amazon Security Hub for more information and to deep dive into the recommendation.

   ![Configuration de la sécurité](media/security-configuration-aws.png)

## <a name="next-steps"></a>Étapes suivantes 
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]  
  
