---
title: Application automatique d’étiquettes de classification Azure Information Protection
description: Ce tutoriel explique comment appliquer automatiquement des étiquettes de classification Azure Information Protection dans Microsoft Cloud App Security.
ms.date: 3/5/2019
ms.topic: tutorial
ms.openlocfilehash: 997de343a151ccfc5e91f0935b63229a1afb389c
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96315750"
---
# <a name="tutorial-automatically-apply-azure-information-protection-classification-labels"></a>Tutoriel : Application automatique d’étiquettes de classification Azure Information Protection

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Dans un monde idéal, tous vos employés comprennent l’importance de la protection des données et respectent vos stratégies. Cependant, il est probable que dans la réalité un partenaire du service comptabilité charge un document dans votre référentiel Box avec des autorisations inappropriées. Une semaine plus tard, vous réalisez que les informations confidentielles de votre entreprise ont été divulguées à la concurrence. Microsoft Cloud App Security vous aide à éviter que ce type d’incident ne se produise. Cette fonctionnalité est disponible pour Box, SharePoint et OneDrive Entreprise. L’application d’une étiquette Azure Information Protection fait partie des très nombreuses [actions de gouvernance](governance-actions.md) disponibles.

Ce tutoriel vous aide à identifier les autorisations publiques définies sur un document enregistré dans votre stockage cloud, afin d’être averti en cas de violation. Par ailleurs, vous pouvez appliquer automatiquement votre étiquette de classification Azure Information Protection **Confidentiel** pour assurer un chiffrement supplémentaire des fichiers.

> [!div class="checklist"]
>
> * Configuration de la protection des données
> * Valider votre stratégie

## <a name="enhanced-data-level-encryption-protection"></a>Protection améliorée du chiffrement au niveau des données

L’intégration de Cloud App Security avec Azure Information Protection offre un niveau de protection supplémentaire en chiffrant automatiquement les fichiers. Lorsque Azure Information Protection chiffre les fichiers, les applications qui prennent en charge cette fonctionnalité, comme Office 365, savent comment ouvrir les fichiers en respectant les autorisations définies dans les étiquettes de classification. Utilisez des étiquettes pour appliquer des règles de protection spécifiques. Par exemple, définissez un fichier qui peut être ouvert mais ni partagé, ni imprimé, ni transféré, ni modifié.

Ce niveau élevé de protection suit le fichier, qui reste protégé en cas d’envoi, de copie ou d’enregistrement dans une application de stockage en ligne. Si l’un de vos employés perd une clé USB contenant le fichier, ce dernier sera verrouillé. Dans le cas où quelqu’un essaierait de le modifier, son propriétaire recevrait une alerte. Avec Cloud App Security, vous pouvez appliquer cette protection automatiquement. Par exemple, définissez une protection automatique avec une étiquette de classification pour tous les fichiers comportant des numéros de carte de crédit ou chargés par le service financier et partagés en externe.

## <a name="the-threat"></a>La menace

Un utilisateur de votre organisation enregistre des fichiers d’informations client confidentielles dans Box et définit des paramètres de partage avec tous les collaborateurs. Il ne se rend pas compte que non seulement sa propre équipe, mais aussi tout le personnel du support a accès à ce compte Box. Cet accès comprend les fournisseurs, les partenaires et les visiteurs qui se rendent occasionnellement au bureau. Toute personne ayant accès au compte Box de votre organisation a maintenant accès à ces informations. Cet accès est à la fois dangereux pour votre organisation et contraire aux réglementations relatives aux informations personnelles de multiples pays/régions, ce qui peut potentiellement causer des problèmes juridiques.

## <a name="the-solution"></a>La solution

Utilisez Cloud App Security avec Azure Information Protection pour intégrer des informations de classification et de protection permanente à vos données, afin qu’elles restent sécurisées, quel que soit l’emplacement où elles sont stockées et quelles que soient les personnes avec qui elles sont partagées : collègues, clients et partenaires. Définissez qui peut y accéder et quels sont les usages permis. Par exemple, autorisez les utilisateurs à afficher et à modifier des fichiers, mais pas à les imprimer ni à les transférer. Vous pouvez également ajouter aux fichiers d’autres [actions de gouvernance](governance-actions.md) prises en charge par Cloud App Security, comme supprimer des collaborateurs ou des capacités de partage.

## <a name="prerequisites"></a>Prérequis

* [Activez Cloud App Security et Azure Information Protection](azip-integration.md) pour votre locataire.
* [Connectez Box](connect-box-to-microsoft-cloud-app-security.md) à Cloud App Security.

## <a name="set-up-data-protection"></a>Configuration de la protection des données

Configurons une stratégie qui recherche des numéros de carte de crédit au sein des fichiers stockés dans votre compte Box. Lorsque des fichiers sont trouvés, une étiquette Azure Information Protection est automatiquement appliquée ; il sera ainsi possible de contrôler tous les fichiers auxquels elle est attribuée.

1. Commencez à protéger les données stockées dans Box en configurant une stratégie qui chiffrera toutes les données sensibles stockées dans Box :

    1. Dans l’onglet **Contrôle**, cliquez sur [**Stratégies**](control-cloud-apps-with-policies.md).

    2. Cliquez sur **Créer une stratégie**, puis sélectionnez **Stratégie de fichier**.

    3. Appelez la stratégie *Protection des données Box*.

    4. Sous **Créer un filtre pour les fichiers sur lesquels porte cette stratégie**, ciblez vos données protégées et sensibles.
        * Par exemple, sélectionnez **Données client** comme **Dossier parent** dans Box et le service financier comme **Propriétaire**.

    5. Dans ce dossier, recherchez les fichiers contenant des informations de carte de crédit. Sous **Méthode d’inspection du contenu**, sélectionnez **DLP intégré**, **Inclure les fichiers qui correspondent à une expression prédéfinie**, puis **tous les pays:Finance:Numéro de carte de crédit**.

    6. Sous **Gouvernance**, ouvrez la section **Box**, puis sélectionnez **Appliquer une étiquette de classification**. Sélectionnez l’étiquette que vous voulez appliquer.

    7. [Cloud App Security offre une intégration avec Azure Information Protection](azip-integration.md), ce qui permet de sélectionner une étiquette de classification dans la liste d’étiquettes existantes pour protéger les données.

    8. Cliquez sur **Créer**.

   ![Ajout d’une étiquette de classification à une stratégie](media/aip-auto-policy.png)

2. Examinez vos correspondances :

    1. Sur la page **Stratégies**, cliquez sur le nom de la stratégie pour accéder au **Rapport de stratégie**. Examinez les correspondances déclenchées pour cette stratégie.

    2. Pour examiner les correspondances, vous pouvez cliquer sur l’une d’elles afin d’ouvrir le tiroir des fichiers. Dans le tiroir figurent les autres stratégies avec lesquelles ce fichier présente une correspondance.

## <a name="validate-your-policy"></a>Valider votre stratégie

1. Pour simuler une alerte, accédez à votre compte Box et essayez d’accéder à un fichier du dossier **Données client**.
2. Accédez au rapport de la stratégie. Une correspondance avec une stratégie de fichier devrait apparaître rapidement.
3. Vous pouvez cliquer sur la correspondance pour voir quels fichiers ont été protégés. La correspondance elle-même est masquée pour protéger les données sensibles.

>[!NOTE]
>
> *- Cloud App Security prend actuellement en charge l’application automatique des étiquettes Azure Information Protection sur Box, GSuite, SharePoint et OneDrive Entreprise.
> *- Lorsqu’un document est étiqueté en utilisant Cloud App Security, les marquages visuels ne sont pas appliqués immédiatement. Ils le sont quand le document est ouvert dans une application Office et qu’il est enregistré pour la première fois. Pour plus d’informations, consultez [Guide pratique pour configurer les marquages visuels d’une étiquette pour Azure Information Protection](/information-protection/deploy-use/configure-policy-markings#when-visual-markings-are-applied).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]