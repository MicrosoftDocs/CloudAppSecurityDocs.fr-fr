---
title: "Appliquer automatiquement des étiquettes de classification Azure Information Protection | Microsoft Docs"
description: "Cette rubrique décrit le processus d’application automatique des étiquettes de classification Azure Information Protection dans Microsoft Cloud App Security."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/15/2018
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: eac0b192-98d7-4939-9a07-1d4a7f8c39c3
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: f9addebb97bc57b14c5c666b73a0d0d8e21a23ff
ms.sourcegitcommit: 458e936e1ac548eda37e9bf955b439199bbdd018
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2018
---
# <a name="automatically-apply-azure-information-protection-classification-labels"></a>Appliquer automatiquement des étiquettes de classification Azure Information Protection  

Dans un monde parfait, tous les employés comprennent l’importance de la protection des informations et respectent vos stratégies. Mais dans le monde réel, l’un de vos partenaires qui collabore avec la comptabilité peut facilement charger un document sur votre dépôt Box avec des autorisations incorrectes. Une semaine plus tard, vous vous rendez compte que des informations confidentielles de votre entreprise ont été exposées à votre concurrent. 

Microsoft Cloud App Security vous permet d’éviter ce genre de catastrophe avant qu’elle n’arrive.

En effet, Cloud App Security identifie la présence d’autorisations publiques dans un document enregistré dans votre compte Box, puis utilise un moteur de classification pour identifier la présence d’informations confidentielles dans le document partagé publiquement. Cloud App Security vous envoie alors une alerte pour vous informer de cet événement, puis applique automatiquement votre étiquette de classification Azure Information Protection **Confidentiel** pour renforcer le chiffrement du fichier. 

>[!NOTE]
> - L’application d’une étiquette Azure Information Protection est l’un des éléments figurant dans la longue liste [des actions de gouvernance](governance-actions.md) disponibles.
> - Cette fonctionnalité est disponible pour Box, SharePoint et OneDrive Entreprise.

### <a name="enhanced-data-level-encryption-protection"></a>Protection par chiffrement renforcé au niveau des données

L’intégration de Cloud App Security dans Azure Information Protection augmente le niveau de protection en chiffrant automatiquement les fichiers. Par exemple, pendant qu’Azure Information Protection chiffre le fichier, les applications qui prennent en charge Azure Information Protection (par exemple, Office 365) savent comment ouvrir les fichiers et respecter les autorisations définies dans les étiquettes de classification. Vous pouvez utiliser des étiquettes pour appliquer des règles de protection spécifiques. Par exemple, vous pouvez définir un fichier pour qu’il puisse être ouvert mais pas partagé, imprimé, transféré ni modifié. 

Ce niveau de protection élevé se déplace avec le fichier : si vous envoyez, copiez, stockez le fichier dans votre application de stockage en ligne, il reste protégé. Si un de vos employés perd une clé USB sur laquelle est enregistré un fichier confidentiel, celui-ci est verrouillé et si quelqu’un essaie de l’ouvrir, le propriétaire du fichier reçoit une alerte. Avec Cloud App Security, vous pouvez appliquer une protection automatiquement. Par exemple, vous pouvez définir une protection automatique pour tous les fichiers qui comprennent des numéros de carte bancaire ou qui ont été chargés par le service financier afin d’être partagés en externe, à l’aide d’une étiquette de classification. 

## <a name="the-threat"></a>La menace 
Un utilisateur de votre organisation enregistre des fichiers contenant des informations confidentielles sur vos clients dans Box et en définit le partage avec tous les utilisateurs de l’organisation. L’utilisateur ne réalise pas que, en plus de son équipe immédiate, tout le personnel du support a accès à ce compte Box, notamment les fournisseurs, les partenaires et les visiteurs qui viennent parfois au bureau. Toutes les personnes ayant accès au compte Box de votre organisation ont désormais accès à ces informations. Non seulement cela peut s’avérer dangereux pour votre organisation, mais aussi contraire aux réglementations PII de nombreux pays, ce qui peut entraîner des problèmes légaux.

## <a name="the-solution"></a>La solution
Utilisez Cloud App Security avec Azure Information Protection pour incorporer des informations de classification et de protection afin de mettre en place une protection permanente qui suit vos données (et ainsi s’assurer que les données restent protégées, où qu’elles soient stockées et quelles que soient les personnes avec lesquelles vous les partagez). Cette pratique vous permet également de partager en toute sécurité des données avec vos collègues, mais aussi vos clients et partenaires. Définissez qui peut accéder aux données et ce que ces personnes peuvent en faire, notamment autoriser des utilisateurs à afficher et modifier des fichiers, mais pas à les imprimer ni les transférer, ceci en plus des autres [actions de gouvernance](governance-actions.md) prises en charge par Cloud App Security, comme retirer des collaborateurs et les possibilités de partage.

## <a name="prerequisites"></a>Prérequis

- [Activez Cloud App Security et Azure Information Protection](azip-integration.md) pour votre locataire.
- [Connectez Box](connect-box-to-microsoft-cloud-app-security.md) à Cloud App Security.

## <a name="setting-up-data-protection"></a>Configuration de la protection des données

Définissons une stratégie qui recherche des numéros de carte de crédit dans les fichiers stockés dans votre compte Box et qui, quand ils sont trouvés, applique automatiquement une étiquette Azure Information Protection, puis contrôle ce qui se passe pour tous les fichiers ayant cette étiquette.

1. Commencez à protéger les données que vous stockez dans Box en définissant une stratégie qui chiffre toutes les données sensibles stockées dans Box :

    1. Sous l’onglet **Contrôle**, cliquez sur [**Stratégies**](control-cloud-apps-with-policies.md). 
    
    2. Cliquez sur **Créer une stratégie** et sélectionnez **Stratégie de fichier**.
    
    3. Nommez la stratégie *Protection des données Box*.
    
    4. Sous **Créer un filtre pour les fichiers sur lesquels cette stratégie s’appliquera**, ciblez vos données sensibles et propriétaires.<br></br>
    Par exemple, sélectionnez **Dossier parent** est égal à **Données client** dans Box, puis **Propriétaire** est égal à et sélectionnez le service financier.
    
    4. Dans ce dossier, recherchez les fichiers qui contiennent des informations de carte de crédit comme suit : sous **Méthode d’inspection du contenu**, sélectionnez **DLP intégré**, puis **Inclure les fichiers correspondant à une expression prédéfinie** et sélectionnez **Tous les pays:Finance:Numéro de carte de crédit**.
    
    5. Sous **Gouvernance**, ouvrez la section **Box** et sélectionnez **Appliquer l’étiquette de classification**, puis sélectionnez l’étiquette à appliquer.
    
    6. Étant donné que [Cloud App Security est intégré avec Azure Information Protection](azip-integration.md), vous pouvez effectuer une sélection dans votre liste d’étiquettes de classification que vous utiliserez pour protéger les données.
 
    7. Cliquez sur **Créer**. 
   
   ![Ajouter l’étiquette de classification à la stratégie](./media/aip-auto-policy.png)
     
2. Étudier les correspondances
    
    1. Dans la page **Stratégies**, cliquez sur le nom de la stratégie pour atteindre le **Rapport de stratégie**, puis passez en revue les correspondances qui ont été déclenchées.

    2. Pour examiner une correspondance, cliquez sur celle-ci et ouvrez le tiroir de fichier. Dans le tiroir, vous pouvez voir les autres stratégies correspondant à ce fichier. 
     
## <a name="validating-your-policy"></a>Valider votre stratégie

1. Pour simuler une alerte, accédez à votre compte Box et tentez d’accéder à un fichier dans le dossier **Données client**.
3. Accédez au rapport de stratégie. Une correspondance de stratégie de fichier devrait apparaître sous peu. 
4. Vous pouvez cliquer sur la correspondance pour voir quels fichiers ont été protégés. La correspondance elle-même est masquée pour protéger les données sensibles. 

>[!NOTE]
>Cloud App Security prend actuellement en charge l’application automatique des étiquettes Azure Information Protection sur Box, SharePoint et OneDrive Entreprise.


 ## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  