---
title: Intégrer Cloud App Security à iboss
description: Cet article explique comment intégrer Microsoft Cloud App Security à la passerelle cloud sécurisée iboss pour offrir une expérience Cloud Discovery fluide et créer un bloc automatisé d’applications non approuvées.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 2/2/2019
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 69b70614bf62f91c6d0d9743e863239217542f1e
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90881049"
---
# <a name="integrate-cloud-app-security-with-iboss"></a>Intégrer Cloud App Security à iboss

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Si vous utilisez Cloud App Security et iboss, vous pouvez intégrer ces deux produits pour rendre votre expérience Cloud Discovery encore plus sûre. iboss est une passerelle cloud sécurisée autonome qui supervise le trafic de votre organisation et vous permet de définir des stratégies de blocage des transactions. Utilisés ensemble, Cloud App Security et iboss offrent les avantages suivants :

- Un déploiement transparent de Cloud Discovery. Utilisez iboss pour envoyer le trafic à Cloud App Security par le biais du proxy. Cela vous évite d’avoir à installer des collecteurs de journaux sur vos points de terminaison réseau pour activer Cloud Discovery.
- Les fonctionnalités de blocage d’iboss sont automatiquement activées pour les applications que vous définissez comme non approuvées dans Cloud App Security.
- Améliorez votre portail d’administration d’iboss en activant l’évaluation des risques de Cloud App Security pour les 100 applications cloud les plus utilisées dans votre organisation. Vous pouvez ainsi voir toutes ces applications directement dans le portail d’administration d’iboss.

## <a name="prerequisites"></a>Prérequis

- Une licence valide pour Microsoft Cloud App Security
- Licence valide pour la passerelle iboss Secure Cloud Gateway (version 9.1.100.0 ou ultérieure)

## <a name="deployment"></a>Déploiement

1. Dans le portail Cloud App Security, effectuez les étapes d’intégration suivantes :
    1. Cliquez sur la roue dentée des paramètres et sélectionnez **Paramètres Cloud Discovery**.
    2. Sélectionnez l’onglet **Chargement automatique des journaux**, puis sélectionnez **Ajouter une source de données**.
    3. Dans la page **Ajouter une source de données**, entrez les paramètres suivants :

        - Nom = iboss
        - source = iboss Secure Cloud Gateway
        - Type de récepteur = Syslog - UDP

        ![source de données iboss](media/iboss-integration.png)

    4. Cliquez sur **Afficher un exemple du fichier journal attendu**. Puis cliquez sur **Télécharger l’exemple de journal** pour afficher un exemple de journal Discovery et vous assurer qu’il correspond à vos journaux.<br />

1. Examinez les applications cloud découvertes sur votre réseau. Pour plus d’informations et de méthodes d’examen, consultez la page [Utilisation de Cloud Discovery](working-with-cloud-discovery-data.md).

1. Toute application que vous définissez comme non approuvée dans Cloud App Security est soumise à un test Ping par iboss toutes les dix minutes, avant d’être bloquée automatiquement par iboss. Pour plus d’informations sur la non-approbation des applications, consultez [Approbation/non-approbation d’une application](governance-discovery.md#BKMK_SanctionApp).

1. Pour configurer iboss afin qu’il envoie les journaux du trafic à Microsoft Cloud App Security, contactez le support iboss.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
