---
title: Inspection du contenu par Cloud App Security à l’aide du service de classification des données Microsoft
description: Cet article décrit le processus suivi par Cloud App Security quand il effectue l’inspection du contenu DLP avec le service de classification des données Microsoft.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 04/16/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 353cff79b3e76c3f63380194ea055a92f13c0ce8
ms.sourcegitcommit: 826d2ec022647bce6c3135c115a41ee894ff8ecd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/16/2020
ms.locfileid: "84800773"
---
# <a name="microsoft-data-classification-services-integration"></a>Intégration du service de classification des données Microsoft

*S’applique à : Microsoft Cloud App Security*

Microsoft Cloud App Security vous permet d’utiliser le service de classification des données Microsoft en mode natif pour classer les fichiers de vos applications cloud. Le service de classification des données Microsoft fournit une expérience unifiée de protection des informations via Office 365, Azure Information Protection et Microsoft Cloud App Security. Le service de classification vous permet d’étendre votre travail de classification des données aux applications cloud tierces protégées par Microsoft Cloud App Security, en appliquant les décisions que vous avez déjà prises à un plus grand nombre d’applications.

>[!NOTE]
> Cette fonctionnalité est actuellement disponible aux États-Unis, en Europe, en Australie, en Inde, au Canada, au Japon et à l’Asie-Pacifique.

## <a name="enable-content-inspection-with-data-classification-services"></a>Activer l’inspection du contenu avec les services de classification des données

Vous avez la possibilité de définir la **méthode d’inspection** pour qu’elle utilise le **service de classification des données Microsoft** sans aucune configuration supplémentaire. Cette option est utile quand vous créez une stratégie de prévention de fuite de données pour vos fichiers dans Microsoft Cloud App Security.

1. Dans la page [Stratégie de fichier](data-protection-policies.md), sous **Méthode d’inspection**, sélectionnez **Service de classification des données**. Vous pouvez également définir la **méthode d’inspection** dans la page [stratégie de session](session-policy-aad.md) avec l’option **contrôler le téléchargement du fichier (avec inspection)** sélectionnée.

    ![définition du service de classification des données](media/dcs-enable.png)
2. Indiquez si la stratégie doit s’appliquer quand **un** ou **tous** les critères sont remplis.
3. **Choisissez un type d’inspection** en sélectionnant les **types d’informations sensibles**.

    ![définition du service de classification des données](media/dcs-sensitive-information-type.png)

4. Vous pouvez utiliser les [types d’informations sensibles par défaut ](https://support.office.com/article/what-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b) pour définir ce qui se passe pour les fichiers protégés par Microsoft Cloud App Security. Vous pouvez également réutiliser vos [types d’informations sensibles personnalisés d’Office 365](https://support.office.com/article/create-a-custom-sensitive-information-type-82c382a5-b6db-44fd-995d-b333b3c7fc30).
    > [!NOTE]
    > Vous pouvez configurer votre stratégie pour utiliser des types de classification avancés tels que les empreintes digitales et la correspondance exacte des données.

5. Si vous le souhaitez, vous pouvez afficher les quatre derniers caractères d’une correspondance. Par défaut, les correspondances sont masquées et s’affichent dans leur contexte, avec 40 caractères avant et après la violation. Si vous activez cette case à cocher, les quatre derniers caractères de la correspondance elle-même seront affichés.

6. En tirant parti des stratégies de fichiers, vous pouvez également définir des alertes et des actions de gouvernance pour la stratégie. Pour plus d’informations, consultez les [stratégies de fichier](data-protection-policies.md) et les [actions de gouvernance](governance-actions.md). En tirant parti des stratégies de session, vous pouvez également surveiller et contrôler les actions en temps réel lorsqu’un fichier correspond à un type de contrôleur de contrôle d’accès. Pour plus d’informations, consultez [stratégie de session](session-policy-aad.md).

La définition de ces stratégies vous permet d’étendre facilement la puissance des fonctionnalités DLP Office 365 à toutes vos autres applications cloud approuvées et de protéger les données qu’elles stockent, avec l’ensemble complet d’outils que vous fournit Microsoft Cloud App Security, notamment la capacité à [appliquer automatiquement des étiquettes de classification Azure Information Protection](azip-integration.md) et de contrôler les autorisations de partage.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
