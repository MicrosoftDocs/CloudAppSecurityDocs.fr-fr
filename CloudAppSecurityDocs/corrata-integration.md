---
title: Intégrer Cloud App Security avec Corrata
description: Cet article explique comment intégrer Microsoft Cloud App Security avec Corrata pour une Cloud Discovery transparente et un bloc automatisé d’applications non approuvées.
ms.date: 05/17/2020
ms.topic: how-to
ms.openlocfilehash: b9ec2e83bd99db8c4e884e371edfa5be689813a0
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96312367"
---
# <a name="integrate-cloud-app-security-with-corrata"></a>Intégrer Cloud App Security avec Corrata

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Si vous travaillez avec Cloud App Security et Corrata, vous pouvez intégrer les deux produits pour améliorer votre expérience de Cloud Discovery de sécurité pour l’utilisation des applications mobiles. Corrata, en tant que passerelle mobile locale, surveille le trafic de votre organisation à partir d’appareils mobiles, ce qui vous permet de définir des stratégies pour bloquer les transactions. Ensemble, Cloud App Security et Corrata offrent les fonctionnalités suivantes :

- Un déploiement sans heurts de Cloud Discovery à utiliser Corrata pour collecter le trafic des appareils mobiles et les envoyer à Cloud App Security. Cela vous évite d’avoir à installer des collecteurs de journaux sur vos points de terminaison réseau pour activer Cloud Discovery.
- Les fonctionnalités de bloc de Corrata sont appliquées automatiquement sur les applications que vous définissez comme non approuvées dans Cloud App Security.
- Améliorez votre portail Corrata avec l’évaluation des risques de Cloud App Security pour les applications Cloud de pointe, que vous pouvez consulter directement dans le portail Corrata.

## <a name="prerequisites"></a>Prérequis

- Une licence valide pour Microsoft Cloud App Security
- Une licence valide pour Corrata Cloud

## <a name="deployment"></a>Déploiement

1. Dans le portail Corrata, procédez comme suit pour effectuer l' [intégration des partenaires Corrata avec Microsoft Cloud App Security](https://corrata.com/microsoft-mcas-onboarding).
2. Dans le portail Cloud App Security, effectuez les étapes d’intégration suivantes :
    1. Cliquez sur paramètres roue dentée, puis sélectionnez **paramètres de Cloud Discovery**.
    2. Cliquez sur l’onglet **Chargement automatique des journaux**, puis cliquez sur **Ajouter une source de données**.
    3. Dans la page **Ajouter une source de données**, entrez les paramètres suivants :

        - Nom = Corrata
        - Source = Corrata
        - Type de récepteur = FTP

        ![Corrata de la source de données](media/data-source-corrata.png)

    4. Cliquez sur **Afficher un exemple du fichier journal attendu**. Puis cliquez sur **Télécharger l’exemple de journal** pour afficher un exemple de journal Discovery et vous assurer qu’il correspond à vos journaux.

3. Examinez les applications cloud découvertes sur votre réseau. Pour plus d’informations et de méthodes d’examen, consultez la page [Utilisation de Cloud Discovery](working-with-cloud-discovery-data.md).

4. Toutes les applications que vous définissez comme non approuvées dans Cloud App Security sont interrogées par Corrata, puis automatiquement bloquées par Corrata. Pour plus d’informations sur la non-approbation des applications, consultez [Approbation/non-approbation d’une application](governance-discovery.md#BKMK_SanctionApp).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
