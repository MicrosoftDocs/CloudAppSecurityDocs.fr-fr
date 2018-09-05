---
title: Intégrer Cloud App Security à Zscaler pour une expérience Cloud Discovery fluide et un bloc automatisé d’applications approuvées | Microsoft Docs
description: Intégrer Cloud App Security à Zscaler pour une expérience Cloud Discovery fluide et un bloc automatisé d’applications approuvées.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/28/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 8abeab8e-3b7a-46a7-bbec-9aaf26f778a8
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: a36a678b455442226e4520df0ff771087b3f93dd
ms.sourcegitcommit: 1744ef45b9c5ac8e08b3489bb9b73fc1347587ac
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2018
ms.locfileid: "43115707"
---
*S’applique à : Microsoft Cloud App Security*

# <a name="integrate-cloud-app-security-with-zscaler"></a>Intégrer Cloud App Security à Zscaler

Si vous travaillez avec Cloud App Security et Zscaler, vous pouvez intégrer les deux produits pour améliorer la sécurité de votre expérience Cloud Discovery. Zscaler, en tant que proxy cloud autonome, surveille le trafic de votre organisation, ce qui vous permet de définir des stratégies pour le blocage des transactions. Ensemble, Cloud App Security et Zscaler fournissent les fonctionnalités suivantes :

- Déploiement fluide de Cloud Discovery : le fait d’utiliser Zscaler comme proxy de votre trafic avant de l’envoyer à Cloud App Security élimine la nécessité d’installer des collecteurs de journaux sur vos points de terminaison réseau pour activer Cloud Discovery.
- Les fonctionnalités de blocage de Zscaler sont automatiquement appliquées sur les applications que vous définissez comme non approuvées dans Cloud App Security.
- Améliorez votre portail Zscaler avec l’évaluation du risque de Cloud App Security pour 200 applications cloud de pointe qui peuvent être affichées directement dans le portail Zscaler.
    

## <a name="prerequisites"></a>Prérequis

- Licence valide pour Microsoft Cloud App Security
- Licence valide pour Zscaler Cloud 5.6
- Abonnement à Zscaler NSS actif 

## <a name="deployment"></a>Déploiement

1. Dans le portail Zscaler, effectuez les étapes nécessaires pour terminer [l’intégration du partenaire Zscaler avec Microsoft Cloud App Security](https://help.zscaler.com/zia/configuring-mcas-integration).
2. Dans le portail Cloud App Security, effectuez les étapes d’intégration suivantes :
    1. Cliquez sur la roue dentée des paramètres et sélectionnez **Paramètres Cloud Discovery**. 
    2. Cliquez sur l’onglet **Chargement automatique des journaux**, puis cliquez sur **Ajouter une source de données**.
    3. Dans la page **Ajouter une source de données**, entrez les paramètres suivants :
        - Nom = NSS
        - Source = Zscaler QRadar LEEF
        - Type de récepteur = Syslog - UDP

          ![source de données zscaler](./media/data-source-zscaler.png)

    4. Cliquez sur **Afficher un exemple du fichier journal attendu**. Puis cliquez sur **Télécharger l’exemple de journal** pour afficher un exemple de journal Discovery et vous assurer qu’il correspond à vos journaux.<br>
    
3. Examinez les applications cloud découvertes sur votre réseau, consultez [Utilisation de Cloud Discovery](working-with-cloud-discovery-data.md) pour obtenir plus d’informations et connaître les étapes d’investigation.
 
4. Toute application que vous définissez comme non approuvée dans Cloud App Security est soumise à un test Ping par Zscaler toutes les deux heures, puis bloquée automatiquement par Zscaler. Pour plus d’informations sur la non-approbation des applications, consultez [Approbation/non-approbation d’une application](governance-discovery.md#govern-discovered-apps).
    
    
    
    
    

 
## <a name="see-also"></a>Voir aussi  
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  