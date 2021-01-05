---
title: Enrichir les données Cloud App Security Discovery avec des noms d’utilisateur Azure AD
description: Cet article fournit des informations sur la façon d’enrichir les données Cloud App Security Discovery avec des noms d’utilisateur Azure AD.
ms.date: 12/10/2018
ms.topic: how-to
ms.openlocfilehash: 88564fe5b0ee719d06557942da647dbe828a0713
ms.sourcegitcommit: 16a65ab2c8ca778d0b3cfa97b847af4c812363b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/03/2021
ms.locfileid: "97855725"
---
# <a name="cloud-discovery-enrichment"></a>Enrichissement de Cloud Discovery

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Les données Cloud Discovery peuvent maintenant être enrichies avec des données de nom d’utilisateur Azure Active Directory. Quand vous activez cette fonctionnalité, le nom d’utilisateur reçu dans les journaux de trafic de découverte est mis en correspondance et remplacé par le nom d’utilisateur Azure AD. Cloud Discovery enrichissement active les fonctionnalités suivantes :

- Vous pouvez examiner l’utilisation de l’informatique fantôme par l’utilisateur Azure Active Directory.
- Vous pouvez mettre en corrélation l’utilisation de l’application cloud découverte avec les activités collectées par l’API.
- Vous pouvez ensuite créer des journaux personnalisés basés sur des groupes d’utilisateurs Azure AD. Par exemple, un rapport d’informatique fantôme pour un service marketing spécifique.

## <a name="prerequisites"></a>Prérequis

- La source de données doit fournir les informations de nom d’utilisateur
- [Connecteur d’application Office 365](connect-office-365-to-microsoft-cloud-app-security.md) connecté

## <a name="enabling-user-data-enrichment"></a>Activation de l’enrichissement des données utilisateur

1. Sous l’roue dentée paramètres, sélectionnez **paramètres de Cloud Discovery**.

2. Sous l’onglet **Enrichissement de l’utilisateur**, sélectionnez **Enrichir les identificateurs d’utilisateurs découverts avec les noms d’utilisateurs Azure Active Directory**. Cette option permet à Cloud App Security d’utiliser les données Azure Active Directory pour enrichir les noms d’utilisateur par défaut.

3. Cliquez sur **Enregistrer**.

![Enrichir Cloud App Security Discovery avec des noms d’utilisateur Azure AD](media/discovery-enrichment.png)

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
