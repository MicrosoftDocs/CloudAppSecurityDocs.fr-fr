---
title: Inspection du contenu par Cloud App Security à l'aide du service de classification des données Microsoft | Microsoft Docs
description: Cet article décrit le processus suivi par Cloud App Security lors de l’exécution de l’inspection du contenu DLP à l'aide du service de classification des données Microsoft.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/11/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: bf25d1e6-e5dc-449f-b50e-1cd4a21b6d3d
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: ebba40c8f04dd644711a172fcf150761db3e11cc
ms.sourcegitcommit: 3177ffcbdabbddc6c758e9a1994fb21fde939ffc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35259758"
---
*S’applique à : Microsoft Cloud App Security*



# <a name="microsoft-data-classification-services-integration"></a>Intégration du service de classification des données Microsoft

Microsoft Cloud App Security vous permet d’utiliser le service de classification des données Microsoft en mode natif pour classer les fichiers dans vos applications cloud.
Le service de classification des données de Microsoft fournit une expérience de protection unifiée sur Office 365, Azure Information Protection et Microsoft Cloud App Security. Il vous permet ainsi d'étendre vos efforts de classification des données aux applications cloud tierces protégées par Microsoft Cloud App Security, en s’appuyant sur les décisions que vous avez déjà prises et d'un nombre encore plus grand d'applications.

Sans aucune configuration supplémentaire, lors de la création d’une stratégie de prévention des fuites de données pour vos fichiers dans Microsoft Cloud App Security, vous aurez automatiquement la possibilité de définir la **méthode d’inspection** afin d’utiliser le **service de classification des données Microsoft**.

![définition du service de classification des données](./media/dcs-enable.png)

Pour activer l’inspection du contenu avec les services de classification des données :

1. Dans la page [Stratégie de fichier](data-protection-policies.md) sous **Méthode d’Inspection**, sélectionnez **Service de classification des données**.
2. Indiquez si la stratégie doit s’appliquer quand **un** ou **tous** les critères sont remplis.
3. Choisissez votre type d’inspection du contenu en sélectionnant les types d’informations sensibles.
 ![définition du service de classification des données](./media/dcs-sensitive-information-type.png)

5. Vous pouvez utiliser les [types d’informations sensibles par défaut](https://support.office.com/article/what-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b) et les [types d’informations sensibles personnalisés](https://support.office.com/article/create-a-custom-sensitive-information-type-82c382a5-b6db-44fd-995d-b333b3c7fc30) (prenant en charge des modèles complexes avec des expressions régulières, des mots clés et un dictionnaire volumineux) que vous avez créés dans Office 365 et les réutiliser pour définir ce qui se passe pour les fichiers protégés par Microsoft Cloud App Security.

6. Si vous le souhaitez, vous pouvez afficher les quatre derniers caractères d’une correspondance. Par défaut, les correspondances sont masquées et s’affichent dans leur contexte, avec 40 caractères avant et après la violation. Si vous activez cette case à cocher, les quatre derniers caractères de la correspondance elle-même seront affichés.

7. Vous pouvez également définir des alertes et des actions de gouvernance pour la stratégie. Pour plus d’informations, consultez les [stratégies de fichier](data-protection-policies.md) et les [actions de gouvernance](governance-actions.md).

La définition de ces stratégies dans Microsoft Cloud App Security vous permet d’étendre facilement la puissance des fonctionnalités DLP Office 365 à toutes vos autres applications cloud approuvées et de protéger les données qu’elles stockent, avec l’ensemble complet d’outils que vous fournit Microsoft Cloud App Security, notamment la capacité d’[appliquer automatiquement des étiquettes de classification Azure Information Protection](azip-integration.md) et de contrôler les autorisations de partage.



## <a name="see-also"></a>Voir aussi  
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  