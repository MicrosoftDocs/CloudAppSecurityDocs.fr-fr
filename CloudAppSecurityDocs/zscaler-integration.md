---
title: Intégrer Cloud App Security avec Zscaler
description: Cet article explique comment intégrer Microsoft Cloud App Security avec Zscaler pour une Cloud Discovery transparente et un bloc automatisé d’applications non approuvées.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/03/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: bc418943f4825c7433401f271d710333066039cc
ms.sourcegitcommit: 5a0ea6fe5b90aafadb90da25854dabc4cf05d5fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78238377"
---
# <a name="integrate-cloud-app-security-with-zscaler"></a>Intégrer Cloud App Security avec Zscaler

*S’applique à : Microsoft Cloud App Security*

Si vous travaillez avec Cloud App Security et Zscaler, vous pouvez intégrer les deux produits pour améliorer votre expérience de Cloud Discovery de sécurité. Zscaler, en tant que proxy Cloud autonome, surveille le trafic de votre organisation, ce qui vous permet de définir des stratégies pour bloquer les transactions. Ensemble, Cloud App Security et Zscaler offrent les fonctionnalités suivantes :

- Le déploiement transparent de Cloud Discovery à l’aide de Zscaler pour effectuer un proxy de votre trafic et l’envoyer à Cloud App Security élimine la nécessité d’installer des collecteurs de journaux sur vos points de terminaison réseau pour activer Cloud Discovery.
- Les fonctionnalités de bloc de Zscaler sont appliquées automatiquement sur les applications que vous définissez comme non approuvées dans Cloud App Security.
- Améliorez votre portail Zscaler avec l’évaluation des risques de Cloud App Security pour les applications Cloud de 200 leaders, qui peuvent être consultées directement dans le portail Zscaler.

## <a name="prerequisites"></a>Composants requis

- Une licence valide pour Microsoft Cloud App Security
- Une licence valide pour Zscaler Cloud 5,6
- Un abonnement Zscaler NSS actif

## <a name="deployment"></a>Déploiement

1. Dans le portail Zscaler, procédez comme suit pour effectuer l' [intégration des partenaires Zscaler avec Microsoft Cloud App Security](https://help.zscaler.com/zia/configuring-mcas-integration).
2. Dans le portail Cloud App Security, procédez comme suit :
    1. Cliquez sur paramètres roue dentée, puis sélectionnez **paramètres de Cloud Discovery**.
    2. Cliquez sur l’onglet **chargement automatique des journaux** , puis sur **Ajouter une source de données**.
    3. Dans la page **Ajouter une source de données** , entrez les paramètres suivants :

        - Nom = NSS
        - Source = Zscaler QRadar LEEF
        - Type de récepteur = syslog-UDP

        ![Zscaler de la source de données](media/data-source-zscaler.png)

        > [!NOTE]
        > Assurez-vous que le nom de la source de données est identique au nom de flux utilisé lors de la création du flux NSS Cloud App Security. Pour plus d’informations, consultez [Ajout de Cloud App Security flux NSS](https://help.zscaler.com/zia/adding-mcas-nss-feeds).

    4. Cliquez sur **afficher l’exemple de fichier journal attendu**. Cliquez ensuite sur **Télécharger l’exemple de journal** pour afficher un exemple de journal de découverte et assurez-vous qu’il correspond à vos journaux.<br />

3. Examinez les applications Cloud découvertes sur votre réseau. Pour plus d’informations et pour connaître les étapes de l’investigation, consultez [utilisation de Cloud Discovery](working-with-cloud-discovery-data.md).

4. Toutes les applications que vous définissez comme non approuvées dans Cloud App Security sont interrogées par Zscaler toutes les deux heures, puis bloquées automatiquement par Zscaler. Pour plus d’informations sur la non-approbation d’applications, consultez approbation/désapprobation [d’une application](governance-discovery.md#BKMK_SanctionApp).

## <a name="next-steps"></a>Étapes suivantes :

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
