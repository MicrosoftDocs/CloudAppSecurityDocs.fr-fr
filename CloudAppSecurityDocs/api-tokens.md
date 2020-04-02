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
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: fcde5b08363a790cf18cf873c0dfde183ec6ddcd
ms.sourcegitcommit: 9165220189564860d74a255a5c0be1ed362ba152
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80522558"
---
# <a name="api-tokens"></a>Jetons d’API

*S’applique à : Microsoft Cloud App Security*

L’API Microsoft Cloud App Security fournit un accès par programme aux Cloud App Security par le biais de points de terminaison d’API REST. Les applications peuvent utiliser l’API pour effectuer des opérations de lecture et de mise à jour sur Cloud App Security données et des objets. Par exemple, l’API Cloud App Security prend en charge les opérations courantes suivantes pour un objet utilisateur :

- Charger les fichiers journaux de Cloud Discovery
- Générer des scripts de bloc
- Répertorier les activités, les alertes et les rapports de stratégie
- Ignorer ou résoudre les alertes

Pour afficher la documentation complète de l’API, dans le portail Cloud App Security, accédez à aide > la documentation de l' **API**.

Pour accéder à l’API, vous devez créer un jeton d’API et l’utiliser dans votre logiciel pour vous connecter à l’API Cloud App Security.

L’onglet jetons d’API vous permet de gérer tous les jetons d’API de votre locataire.

## <a name="generate-a-token"></a>Générer un jeton

1. Dans le menu **paramètres** , sélectionnez **extensions de sécurité** , puis **jetons d’API**.

2. Cliquez sur l’icône plus, **générer un nouveau jeton** et indiquez un nom pour identifier le jeton à l’avenir, puis cliquez sur **suivant**.
  ![Cloud App Security génère un jeton d’API](media/api-token-gen.png)

3. Copiez la valeur du jeton et enregistrez-la quelque part pour la récupération. Si vous la perdez, vous devez régénérer le jeton. Le jeton a les privilèges de l’utilisateur qui l’a émis. Par exemple, un lecteur de sécurité ne peut pas émettre un jeton qui peut modifier des données.

4. Vous pouvez filtrer les jetons par État : actif, inactif ou généré.

    - Les générés sont des jetons qui n’ont jamais été utilisés.
    - Active sont des jetons qui ont été générés et utilisés au cours des sept derniers jours.
    - Inactif a été utilisé, mais il n’y a pas eu d’activité au cours des sept derniers jours.

5. Une fois que vous avez généré un nouveau jeton, vous disposez d’une nouvelle URL à utiliser pour accéder au portail Cloud App Security.

    ![Cloud App Security jeton d’API](media/generate-api-token.png)

    L’URL du portail générique continue de fonctionner, mais elle est beaucoup plus lente que l’URL personnalisée fournie avec votre jeton. Si vous oubliez l’URL à tout moment, vous pouvez l’afficher en accédant à l' **?** dans le menu, puis en sélectionnant **à propos**de.

> [!NOTE]
> Si vous utilisez Azure Active Directory Privileged Identity Management activation du rôle, votre jeton d’API ne sera effectif qu’une fois le rôle activé. Pour plus d’informations, consultez [activer mes Azure ad des rôles dans PIM](https://docs.microsoft.com/azure/active-directory/privileged-identity-management/pim-how-to-activate-role).

## <a name="api-token-management"></a>Gestion des jetons d’API

La page jeton d’API comprend un tableau de tous les jetons d’API qui ont été générés.

Les administrateurs complets voient tous les jetons générés pour ce locataire. Les autres utilisateurs voient uniquement les jetons qu’ils ont générés eux-mêmes.

Le tableau fournit des détails sur le moment où le jeton a été généré et le moment où il a été utilisé pour la dernière fois, et vous permet de révoquer le jeton.

Une fois qu’un jeton est révoqué, il est supprimé de la table, et le logiciel qui l’utilisait ne parvient pas à effectuer des appels d’API tant qu’un nouveau jeton n’est pas fourni.

> [!NOTE]
>
> - Les connecteurs SIEM et les collecteurs de journaux utilisent également des jetons d’API. Ces jetons doivent être gérés à partir des sections collecteurs de journaux et agent SIEM et n’apparaissent pas dans ce tableau.
> - Les jetons d’API d’annulation d’approvisionnement sont conservés dans Cloud App Security mais ne peuvent pas être utilisés. Toute tentative d’utilisation de ceux-ci entraînera une réponse de refus d’autorisation. Toutefois, nous vous recommandons de révoquer ces jetons sur la page **jetons d’API** .

## <a name="next-steps"></a>Étapes suivantes :

> [!div class="nextstepaction"]
> [Résolution des problèmes d’intégration de SIEM](troubleshooting-siem.md)

[!INCLUDE [Open support ticket](includes/support.md)]

## <a name="check-out-this-video"></a>Regardez cette vidéo !

[Microsoft Cloud App Security – API REST et jetons](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security--REST-APIs-and-Tokens)
