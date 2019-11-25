---
title: Gestion des jetons d’API dans Cloud App Security
description: Cet article fournit des informations sur la génération de jetons d’API pour Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 4f5e6b1e-6b2c-4358-98f0-945e2993d5fe
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: bcb98ccaad997a0d98df6d7ecb6eee876c64622e
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74461290"
---
# <a name="api-tokens"></a>Jetons d’API

*S’applique à : Microsoft Cloud App Security*

L’API Microsoft Cloud App Security fournit l’accès par programmation à Cloud App Security par le biais de points de terminaison API REST. Les applications peuvent utiliser l’API pour effectuer des opérations de lecture et de mise à jour sur les objets et les données Cloud App Security. Par exemple, l’API Cloud App Security prend en charge les opérations courantes suivantes pour un objet utilisateur :

- Charger des fichiers journaux pour Cloud Discovery
- Générer un script de blocage
- Répertorier des activités, des alertes et des rapports de stratégie
- Ignorer ou résoudre les alertes

Pour consulter la documentation complète de l’API, dans le portail Cloud App Security, accédez à Aide > **Documentation de l’API**.

Pour accéder à l’API, vous devez créer un jeton d’API et l’utiliser dans votre logiciel pour vous connecter à l’API Cloud App Security.

L’onglet Jetons d’API vous aide à gérer tous les jetons d’API de votre locataire. 

## <a name="generate-a-token"></a>Générer un jeton

1. Dans le menu **Paramètres**, sélectionnez **Extensions de sécurité**, puis **Jetons d’API**.

2. Cliquez sur l’icône plus, **Générer un nouveau jeton** et indiquez un nom pour identifier le jeton plus tard, puis cliquez sur **Suivant**.
   ![Cloud App Security génère un jeton d’API](./media/api-token-gen.png)

3. Copiez la valeur du jeton et enregistrez-la quelque part pour pouvoir la récupérer (si vous la perdez, vous devez regénérer le jeton). Le jeton hérite des privilèges de l’utilisateur qui l’émet. Par exemple, un lecteur Sécurité ne peut pas émettre de jeton pouvant modifier des données.

4. Vous pouvez filtrer les jetons par état : Actif, Inactif ou Généré. 

   - L’état Généré désigne les jetons qui n’ont jamais été utilisés. 
   - Les jetons actifs sont ceux qui ont été générés et utilisés au cours des sept derniers jours. 
   - Les jetons inactifs sont ceux qui ont été utilisés, mais n’ont pas eu d’activité au cours des sept derniers jours.
5. Après avoir généré un nouveau jeton, vous recevez une nouvelle URL à utiliser pour accéder au portail Cloud App Security. 

   ![Jeton d’API Cloud App Security](./media/generate-api-token.png)

    L’URL du portail générique continue de fonctionner, mais est beaucoup plus lente que l’URL personnalisée fournie avec votre jeton. Si vous oubliez l’URL, vous pouvez la voir en accédant à l’icône **?** du menu et en sélectionnant **À propos de**.

> [!NOTE]
> If you are using Azure Active Directory Privileged Identity Management role activation, your API token will only be effective once the role is activated. For more information, see [Activate my Azure AD roles in PIM](https://docs.microsoft.com/azure/active-directory/privileged-identity-management/pim-how-to-activate-role).

## <a name="api-token-management"></a>Gestion des jetons d’API

La page Jeton d’API comprend un tableau de tous les jetons d’API qui ont été générés.

Les administrateurs avec des droits complets peuvent voir tous les jetons générés pour le locataire. Les autres utilisateurs voient uniquement les jetons qu’ils ont générés eux-mêmes.

Le tableau fournit des détails sur la date à laquelle le jeton a été généré et celle de sa dernière utilisation, et vous permet de révoquer le jeton. 

Une fois qu’un jeton est révoqué, il est supprimé du tableau, et le logiciel qui l’utilisait ne peut plus appeler l’API tant qu’un nouveau jeton n’est pas fourni. 

> [!NOTE]
> Les collecteurs de journaux et les connecteurs SIEM utilisent également des jetons d’API. Ces jetons doivent être gérés à partir des sections des collecteurs de journaux et de l’agent SIEM, et n’apparaissent pas dans ce tableau. 





## <a name="next-steps"></a>Étapes suivantes
[Résolution des problèmes d’intégration de SIEM](troubleshooting-siem.md)   

[!INCLUDE [Open support ticket](includes/support.md)]  

## <a name="check-out-this-video"></a>Regardez cette vidéo !
[Microsoft Cloud App Security – API REST et jetons](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security--REST-APIs-and-Tokens)  
