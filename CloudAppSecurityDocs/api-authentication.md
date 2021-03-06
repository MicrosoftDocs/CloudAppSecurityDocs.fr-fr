---
title: Gestion des jetons d’API
description: Cet article fournit des informations sur la génération et la gestion des jetons d’API pour Cloud App Security.
ms.date: 03/27/2020
ms.topic: reference
ms.openlocfilehash: cd577565cb67b51dd93c649e69cd00a551736789
ms.sourcegitcommit: 421870fac566642809eff0a545ec1981be1c9165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2020
ms.locfileid: "97705880"
---
# <a name="managing-api-tokens"></a>Gestion des jetons d’API

[!INCLUDE [Banner for top of topics](includes/banner.md)]

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

## <a name="api-token-management"></a>Gestion des jetons d’API

La page Jeton d’API comprend un tableau de tous les jetons d’API qui ont été générés.

Les administrateurs avec des droits complets peuvent voir tous les jetons générés pour le locataire. Les autres utilisateurs voient uniquement les jetons qu’ils ont générés eux-mêmes.

Le tableau fournit des détails sur la date à laquelle le jeton a été généré et celle de sa dernière utilisation, et vous permet de révoquer le jeton.

Une fois qu’un jeton est révoqué, il est supprimé du tableau, et le logiciel qui l’utilisait ne peut plus appeler l’API tant qu’un nouveau jeton n’est pas fourni.

> [!NOTE]
>
> - Les collecteurs de journaux et les connecteurs SIEM utilisent également des jetons d’API. Ces jetons doivent être gérés à partir des sections des collecteurs de journaux et de l’agent SIEM, et n’apparaissent pas dans ce tableau.
> - Les jetons d’API d’annulation d’approvisionnement sont conservés dans Cloud App Security mais ne peuvent pas être utilisés. Toute tentative d’utilisation de ceux-ci entraînera une réponse de refus d’autorisation. Toutefois, nous vous recommandons de révoquer ces jetons sur la page **jetons d’API** .

[!INCLUDE [Open support ticket](includes/support.md)]

## <a name="check-out-this-video"></a>Regardez cette vidéo !

[Microsoft Cloud App Security – API REST et jetons](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security--REST-APIs-and-Tokens)
