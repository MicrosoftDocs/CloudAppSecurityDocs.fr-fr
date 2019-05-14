---
title: Appliquer automatiquement des étiquettes de classification Azure Information Protection
description: Ce tutoriel explique comment appliquer automatiquement des étiquettes de classification Azure Information Protection dans Microsoft Cloud App Security.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 3/5/2019
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: eac0b192-98d7-4939-9a07-1d4a7f8c39c3
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: f3c3afbf03acca812b47388c956ab22dbffd5dd0
ms.sourcegitcommit: 9f0c562322394a3dfac7f1d84286e673276a28b1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65568728"
---
# <a name="tutorial-automatically-apply-azure-information-protection-classification-labels"></a>Tutoriel : Appliquer automatiquement des étiquettes de classification Azure Information Protection

*S’applique à : Microsoft Cloud App Security*

Dans un monde parfait, tous les employés comprennent l’importance de la protection des informations et respectent vos stratégies. Mais dans le monde réel, il est probable qu’un partenaire qui travaille avec la comptabilité charge un document dans votre référentiel Box avec des autorisations incorrectes. Une semaine plus tard, vous réalisez que des informations confidentielles de votre entreprise ont été exposées à vos concurrents. Microsoft Cloud App Security vous permet d’éviter ce genre de catastrophe avant qu’elle n’arrive. Cette fonctionnalité est disponible pour Box, SharePoint et OneDrive Entreprise. L’application d’une étiquette Azure Information Protection est l’un des éléments figurant dans la longue liste [des actions de gouvernance](governance-actions.md) disponibles.

Ce tutoriel vous aide à identifier les autorisations publiques définies sur un document enregistré dans votre stockage cloud, afin de vous avertir en cas de violation. En outre, vous pouvez appliquer automatiquement votre étiquette de classification Azure Information Protection **Confidentiel** pour renforcer le chiffrement des fichiers.

> [!div class="checklist"]
> * Configurer la protection des données 
> * Valider votre stratégie


## <a name="enhanced-data-level-encryption-protection"></a>Protection par chiffrement renforcé au niveau des données

L’intégration de Cloud App Security dans Azure Information Protection augmente le niveau de protection en chiffrant automatiquement les fichiers. Lorsqu’Azure Information Protection chiffre les fichiers, les applications qui prennent en charge Azure Information Protection (comme Office 365) savent comment ouvrir les fichiers et respecter les autorisations définies dans les étiquettes de classification. Utilisez des étiquettes pour appliquer des règles de protection spécifiques. Par exemple, définissez un fichier qui peut être ouvert mais pas partagé, imprimé, transféré ni modifié.

Ce niveau de protection élevé suit le fichier. Le fichier est toujours protégé si vous l’envoyez, le copiez ou le stockez dans votre application de stockage en ligne. Si l’un de vos employés perd une clé USB sur laquelle se trouve le fichier, le fichier est verrouillé. Si une personne tente d’ouvrir le fichier, le propriétaire du fichier reçoit une alerte. Avec Cloud App Security, vous pouvez appliquer une protection automatiquement. Par exemple, définissez une protection automatique pour tous les fichiers qui comprennent des numéros de carte de crédit ou qui ont été chargés par le service financier afin d’être partagés en externe, à l’aide d’une étiquette de classification.

## <a name="the-threat"></a>La menace

Un utilisateur de votre organisation enregistre des fichiers contenant des informations confidentielles sur vos clients dans Box et en définit le partage avec tous les utilisateurs de l’organisation. L’utilisateur ne se rend pas compte que non seulement son équipe, mais également l’ensemble du personnel de support a accès à ce compte Box. Cet accès inclut les fournisseurs, les partenaires et les visiteurs qui viennent parfois au bureau. Toutes les personnes ayant accès au compte Box de votre organisation ont désormais accès à ces informations. Non seulement cet accès peut s’avérer dangereux pour votre organisation, mais également contraire aux réglementations relatives aux informations personnelles de nombreux pays, ce qui peut entraîner des problèmes légaux.

## <a name="the-solution"></a>La solution

Utilisez Cloud App Security avec Azure Information Protection pour incorporer des informations de classification et de protection afin de mettre en place une protection permanente qui suit vos données. Elles restent ainsi protégées où qu’elles soient stockées et quelles que soient les personnes avec lesquelles vous les partagez. Cette protection vous permet de partager en toute sécurité des données avec vos collègues, clients et partenaires. Définissez qui peut accéder aux données et comment ils peuvent les utiliser. Par exemple, autorisez des utilisateurs à afficher et modifier des fichiers, mais pas à les imprimer ou les transférer. Vous pouvez également ajouter d’autres [actions de gouvernance](governance-actions.md) prises en charge par Cloud App Security aux fichiers telles que la suppression de collaborateurs et la suppression des fonctionnalités de partage.

## <a name="prerequisites"></a>Prérequis

- [Activez Cloud App Security et Azure Information Protection](azip-integration.md) pour votre locataire.
- [Connectez Box](connect-box-to-microsoft-cloud-app-security.md) à Cloud App Security.

## <a name="set-up-data-protection"></a>Configurer la protection des données

Définissons une stratégie qui recherche des numéros de carte de crédit dans des fichiers stockés dans votre compte Box. Lorsque des fichiers sont trouvés, appliquez automatiquement une étiquette Azure Information Protection et contrôlez les actions effectuées sur tous les fichiers portant cette étiquette.

1. Commencez à protéger les données que vous stockez dans Box en définissant une stratégie qui chiffre toutes les données sensibles stockées dans Box :

    1. Sous l’onglet **Contrôle**, cliquez sur [**Stratégies**](control-cloud-apps-with-policies.md). 

    2. Cliquez sur **Créer une stratégie** et sélectionnez **Stratégie de fichier**.

    3. Nommez la stratégie *Protection des données Box*.

    4. Sous **Créer un filtre pour les fichiers sur lesquels cette stratégie s’appliquera**, ciblez vos données sensibles et propriétaires.
        - Par exemple, sélectionnez **Dossier parent** est égal à **Données client** dans Box, puis **Propriétaire** est égal au service financier.

    5. Dans ce dossier, recherchez les fichiers contenant des informations de carte de crédit. Sous **Méthode d’inspection du contenu**, sélectionnez **DLP intégré**, sélectionnez **Inclure les fichiers correspondant à une expression prédéfinie**, puis **Tous les pays:Finance:Numéro de carte de crédit**.

    6. Sous **Gouvernance**, ouvrez la section **Box** et sélectionnez **Appliquer l’étiquette de classification**. Sélectionnez l’étiquette à appliquer.

    7. Étant donné que [Cloud App Security est intégré avec Azure Information Protection](azip-integration.md), vous pouvez effectuer une sélection dans votre liste d’étiquettes de classification que vous utiliserez pour protéger les données.

    8. Cliquez sur **Create (Créer)**. 

   ![Ajouter l’étiquette de classification à la stratégie](./media/aip-auto-policy.png)

2. Étudier les correspondances

    1. Dans la page **Stratégies**, cliquez sur le nom de la stratégie pour accéder au **rapport de stratégie**. Passez en revue les correspondances qui ont été déclenchées pour la stratégie.

    2. Pour examiner une correspondance, cliquez sur celle-ci et ouvrez le tiroir de fichier. Dans le tiroir, vous pouvez voir les autres stratégies correspondant à ce fichier.

## <a name="validate-your-policy"></a>Valider votre stratégie

1. Pour simuler une alerte, accédez à votre compte Box et tentez d’accéder à un fichier dans le dossier **Données client**.
2. Accédez au rapport de stratégie. Une correspondance de stratégie de fichier devrait apparaître sous peu. 
3. Vous pouvez cliquer sur la correspondance pour voir quels fichiers ont été protégés. La correspondance elle-même est masquée pour protéger les données sensibles.

>[!NOTE]
>
> - Cloud App Security prend actuellement en charge l’application automatique des étiquettes Azure Information Protection sur Box, GSuite, SharePoint et OneDrive Entreprise.
> - Lorsqu’un document est étiqueté en utilisant Cloud App Security, les marquages visuels ne sont pas appliqués immédiatement. Ils le sont quand le document est ouvert dans une application Office et qu’il est enregistré pour la première fois. Pour plus d’informations, consultez [Comment configurer les marquages visuels d’une étiquette pour Azure Information Protection](https://docs.microsoft.com/information-protection/deploy-use/configure-policy-markings#when-visual-markings-are-applied).

## <a name="next-steps"></a>Étapes suivantes

[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)  
  
  
