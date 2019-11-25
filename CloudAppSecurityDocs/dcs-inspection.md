---
title: Inspection du contenu par Cloud App Security à l’aide du service de classification des données Microsoft
description: Cet article décrit le processus suivi par Cloud App Security quand il effectue l’inspection du contenu DLP avec le service de classification des données Microsoft.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 7/30/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: bf25d1e6-e5dc-449f-b50e-1cd4a21b6d3d
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: c4e00f152fcb09f2133805157b85b2a930ad3aca
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74461343"
---
# <a name="microsoft-data-classification-services-integration"></a>Intégration du service de classification des données Microsoft

*S’applique à : Microsoft Cloud App Security*

Microsoft Cloud App Security vous permet d’utiliser le service de classification des données Microsoft en mode natif pour classer les fichiers de vos applications cloud. Le service de classification des données Microsoft fournit une expérience unifiée de protection des informations via Office 365, Azure Information Protection et Microsoft Cloud App Security. Le service de classification vous permet d’étendre votre travail de classification des données aux applications cloud tierces protégées par Microsoft Cloud App Security, en appliquant les décisions que vous avez déjà prises à un plus grand nombre d’applications.

>[!NOTE]
> This feature is currently available in the US, Europe (except France), Australia, India, Canada, Japan, and APAC.

## <a name="enable-content-inspection-with-data-classification-services"></a>Activer l’inspection du contenu avec les services de classification des données

Vous avez la possibilité de définir la **méthode d’inspection** pour qu’elle utilise le **service de classification des données Microsoft** sans aucune configuration supplémentaire. Cette option est utile quand vous créez une stratégie de prévention de fuite de données pour vos fichiers dans Microsoft Cloud App Security.

1. Dans la page [Stratégie de fichier](data-protection-policies.md), sous **Méthode d’inspection**, sélectionnez **Service de classification des données**. You can also set the **Inspection method** in the [session policy](session-policy-aad.md) page with **Control file download (with DLP)** selected.
     ![définition du service de classification des données](./media/dcs-enable.png)
2. Indiquez si la stratégie doit s’appliquer quand **un** ou **tous** les critères sont remplis.
3. **Choisissez un type d’inspection** en sélectionnant les **types d’informations sensibles**.
 ![définition du service de classification des données](./media/dcs-sensitive-information-type.png)

4. Vous pouvez utiliser les [types d’informations sensibles par défaut ](https://support.office.com/article/what-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b) pour définir ce qui se passe pour les fichiers protégés par Microsoft Cloud App Security. Vous pouvez également réutiliser vos [types d’informations sensibles personnalisés d’Office 365](https://support.office.com/article/create-a-custom-sensitive-information-type-82c382a5-b6db-44fd-995d-b333b3c7fc30).
    > [!NOTE]
    > You can configure your policy to use advanced classification types such as Fingerprints and Exact Data Match.

5. Si vous le souhaitez, vous pouvez afficher les quatre derniers caractères d’une correspondance. Par défaut, les correspondances sont masquées et s’affichent dans leur contexte, avec 40 caractères avant et après la violation. Si vous activez cette case à cocher, les quatre derniers caractères de la correspondance elle-même seront affichés.

6. Leveraging file policies, you can also set alerts and governance actions for the policy. Pour plus d’informations, consultez les [stratégies de fichier](data-protection-policies.md) et les [actions de gouvernance](governance-actions.md). Leveraging session policies, you can also monitor and control actions in real-time when a file matches a DCS type. For more information, see [session policy](session-policy-aad.md).

La définition de ces stratégies vous permet d’étendre facilement la puissance des fonctionnalités DLP Office 365 à toutes vos autres applications cloud approuvées et de protéger les données qu’elles stockent, avec l’ensemble complet d’outils que vous fournit Microsoft Cloud App Security, notamment la capacité à [appliquer automatiquement des étiquettes de classification Azure Information Protection](azip-integration.md) et de contrôler les autorisations de partage.

## <a name="next-steps"></a>Étapes suivantes

[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]