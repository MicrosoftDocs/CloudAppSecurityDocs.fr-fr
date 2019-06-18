---
title: Inspection du contenu par Cloud App Security à l’aide du service de classification des données Microsoft
description: Cet article décrit le processus suivi par Cloud App Security quand il effectue l’inspection du contenu DLP avec le service de classification des données Microsoft.
keywords: ''
author: ShlomoSagir-MS
ms.author: ShlomoSagir-MS
manager: ShlomoSagir-MS
ms.date: 06/13/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: bf25d1e6-e5dc-449f-b50e-1cd4a21b6d3d
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: b970a947475b449534ad1ac3d28db2dd1984fc15
ms.sourcegitcommit: 5c6d41aae2d9ac461917338f4a423f7a2683aca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/16/2019
ms.locfileid: "67149521"
---
# <a name="microsoft-data-classification-services-integration"></a>Intégration du service de classification des données Microsoft

*S’applique à : Microsoft Cloud App Security*

Microsoft Cloud App Security vous permet d’utiliser le service de classification des données Microsoft en mode natif pour classer les fichiers de vos applications cloud. Le service de classification des données Microsoft fournit une expérience unifiée de protection des informations via Office 365, Azure Information Protection et Microsoft Cloud App Security. Le service de classification vous permet d’étendre votre travail de classification des données aux applications cloud tierces protégées par Microsoft Cloud App Security, en appliquant les décisions que vous avez déjà prises à un plus grand nombre d’applications.

>[!NOTE]
> Cette fonctionnalité est actuellement disponible dans des États-Unis, Europe (à l’exception de la France), Australie, Inde, au Canada, Japon et Asie-Pacifique.


## <a name="enable-content-inspection-with-data-classification-services"></a>Activer l’inspection du contenu avec les services de classification des données

Vous avez la possibilité de définir la **méthode d’inspection** pour qu’elle utilise le **service de classification des données Microsoft** sans aucune configuration supplémentaire. Cette option est utile quand vous créez une stratégie de prévention de fuite de données pour vos fichiers dans Microsoft Cloud App Security.


1. Dans la page [Stratégie de fichier](data-protection-policies.md), sous **Méthode d’inspection**, sélectionnez **Service de classification des données**. Vous pouvez également définir le **méthode d’Inspection** dans le [stratégie de session](session-policy-aad.md) page avec **contrôler le téléchargement du fichier (avec DLP)** sélectionné.
     ![définition du service de classification des données](./media/dcs-enable.png)
2. Indiquez si la stratégie doit s’appliquer quand **un** ou **tous** les critères sont remplis.
3. **Choisissez un type d’inspection** en sélectionnant les **types d’informations sensibles**.
 ![définition du service de classification des données](./media/dcs-sensitive-information-type.png)

4. Vous pouvez utiliser les [types d’informations sensibles par défaut ](https://support.office.com/article/what-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b) pour définir ce qui se passe pour les fichiers protégés par Microsoft Cloud App Security. Vous pouvez également réutiliser vos [types d’informations sensibles personnalisés d’Office 365](https://support.office.com/article/create-a-custom-sensitive-information-type-82c382a5-b6db-44fd-995d-b333b3c7fc30).

5. Si vous le souhaitez, vous pouvez afficher les quatre derniers caractères d’une correspondance. Par défaut, les correspondances sont masquées et s’affichent dans leur contexte, avec 40 caractères avant et après la violation. Si vous activez cette case à cocher, les quatre derniers caractères de la correspondance elle-même seront affichés.

6. Tirant parti des stratégies de fichier, vous pouvez également définir des alertes et des actions de gouvernance pour la stratégie. Pour plus d’informations, consultez les [stratégies de fichier](data-protection-policies.md) et les [actions de gouvernance](governance-actions.md). En tirant parti des stratégies de session, vous pouvez également surveiller et contrôler des actions en temps réel lorsque un fichier correspond à un type de contrôleurs de domaine. Pour plus d’informations, consultez [stratégie de session](session-policy-aad.md).

La définition de ces stratégies vous permet d’étendre facilement la puissance des fonctionnalités DLP Office 365 à toutes vos autres applications cloud approuvées et de protéger les données qu’elles stockent, avec l’ensemble complet d’outils que vous fournit Microsoft Cloud App Security, notamment la capacité à [appliquer automatiquement des étiquettes de classification Azure Information Protection](azip-integration.md) et de contrôler les autorisations de partage.



## <a name="next-steps"></a>Étapes suivantes  
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)  
  
