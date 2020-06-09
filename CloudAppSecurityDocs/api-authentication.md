---
title: Gestion des jetons d’API dans Cloud App Security
description: Cet article fournit des informations sur la génération de jetons d’API pour Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 933c2beb8285f4f76f61406ab4981153b81913cc
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505418"
---
# <a name="managing-api-tokens"></a>Gestion des jetons d’API

*S’applique à : Microsoft Cloud App Security*

Pour accéder à l’API Cloud App Security, vous devez créer un jeton d’API et l’utiliser dans votre logiciel pour vous connecter à l’API. Ce jeton sera inclus dans l’en-tête lorsque Cloud App Security effectue des demandes d’API.

L’onglet Jetons d’API vous aide à gérer tous les jetons d’API de votre locataire.

## <a name="generate-a-token"></a>Générer un jeton

1. Dans le menu **Paramètres**, sélectionnez **Extensions de sécurité**, puis **Jetons d’API**.

2. Cliquez sur l’icône plus, **Générer un nouveau jeton** et indiquez un nom pour identifier le jeton plus tard, puis cliquez sur **Suivant**.

    ![Cloud App Security génère un jeton d’API](media/api-token-gen.png)

3. Copiez la valeur du jeton et enregistrez-la quelque part pour pouvoir la récupérer (si vous la perdez, vous devez regénérer le jeton). Le jeton hérite des privilèges de l’utilisateur qui l’émet. Par exemple, un lecteur Sécurité ne peut pas émettre de jeton pouvant modifier des données.

4. Vous pouvez filtrer les jetons par état : Actif, Inactif ou Généré.

    - **Généré :** Jetons qui n’ont jamais été utilisés.
    - **Actif :** Jetons générés et utilisés au cours des sept derniers jours.
    - **Inactif :** Jetons utilisés, mais il n’y avait aucune activité au cours des sept derniers jours.

5. Après avoir généré un nouveau jeton, vous recevez une nouvelle URL à utiliser pour accéder au portail Cloud App Security.

    ![Jeton d’API Cloud App Security](media/generate-api-token.png)

    L’URL du portail générique continue de fonctionner, mais est beaucoup plus lente que l’URL personnalisée fournie avec votre jeton. Si vous oubliez l’URL, vous pouvez la voir en accédant à l’icône **?** du menu et en sélectionnant **À propos de**.

> [!NOTE]
> Si vous utilisez Azure Active Directory Privileged Identity Management activation du rôle, votre jeton d’API ne sera effectif qu’une fois le rôle activé. Pour plus d’informations, consultez [activer mes Azure ad des rôles dans PIM](https://docs.microsoft.com/azure/active-directory/privileged-identity-management/pim-how-to-activate-role).

## <a name="api-token-management"></a>Gestion des jetons d’API

La page Jeton d’API comprend un tableau de tous les jetons d’API qui ont été générés.

Les administrateurs avec des droits complets peuvent voir tous les jetons générés pour le locataire. Les autres utilisateurs voient uniquement les jetons qu’ils ont générés eux-mêmes.

Le tableau fournit des détails sur la date à laquelle le jeton a été généré et celle de sa dernière utilisation, et vous permet de révoquer le jeton.

Une fois qu’un jeton est révoqué, il est supprimé du tableau, et le logiciel qui l’utilisait ne peut plus appeler l’API tant qu’un nouveau jeton n’est pas fourni.

> [!NOTE]
> Les collecteurs de journaux et les connecteurs SIEM utilisent également des jetons d’API. Ces jetons doivent être gérés à partir des sections des collecteurs de journaux et de l’agent SIEM, et n’apparaissent pas dans ce tableau.

[!INCLUDE [Open support ticket](includes/support.md)]

## <a name="check-out-this-video"></a>Regardez cette vidéo !

[Microsoft Cloud App Security – API REST et jetons](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security--REST-APIs-and-Tokens)
