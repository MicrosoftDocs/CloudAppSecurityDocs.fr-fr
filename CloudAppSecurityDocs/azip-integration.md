---
title: Intégrer Azure Information Protection avec Cloud App Security
description: Cet article fournit des informations sur la façon de tirer parti de vos balises Azure Information Protection dans Cloud App Security pour un contrôle supplémentaire de l’utilisation des applications Cloud de votre organisation.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/09/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: b32007479ece2828cc13376f88188bfdc08ade7c
ms.sourcegitcommit: 288c279a0d2dd62a8ad8d7425c3e9e98857bf5f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2020
ms.locfileid: "80666467"
---
# <a name="azure-information-protection-integration"></a>Intégration d’Azure Information Protection

*S’applique à : Microsoft Cloud App Security*

Microsoft Cloud App Security vous permet d’appliquer des étiquettes de classification Azure Information Protection automatiquement, avec ou sans protection, à des fichiers en tant qu’action de gouvernance de stratégie de fichier. Vous pouvez également examiner les fichiers en filtrant l’étiquette de classification appliquée dans le portail Cloud App Security. L’utilisation de classifications permet une meilleure visibilité et un meilleur contrôle de vos données sensibles dans le Cloud. L’intégration de Azure Information Protection avec Cloud App Security est aussi simple que la sélection d’une seule case à cocher.

> [!NOTE]
> Cet article s’applique également aux étiquettes de sensibilité unifiée d’Office 365 si vous avez déjà [migré vos étiquettes de classification pour le centre de sécurité et conformité office 365](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels). Si vous n’avez pas migré vos étiquettes de classification existantes et que vous commencez à créer de nouvelles étiquettes dans le centre de sécurité et conformité Office 365, Cloud App Security utilisera uniquement les étiquettes préexistantes configurées dans le portail Azure Information Protection.

En intégrant Azure Information Protection dans Cloud App Security, vous pouvez utiliser toute la puissance des services et sécuriser les fichiers dans votre Cloud, notamment :

- La possibilité d’appliquer des étiquettes de classification en tant qu’action de gouvernance à des fichiers qui correspondent à des stratégies spécifiques
- Possibilité d’afficher tous les fichiers classifiés dans un emplacement central
- La possibilité d’effectuer des recherches en fonction du niveau de classification et de quantifier l’exposition des données sensibles sur vos applications Cloud
- La possibilité de créer des stratégies pour s’assurer que les fichiers classifiés sont correctement gérés

> [!NOTE]
> Pour activer cette fonctionnalité, vous avez besoin d’une licence Cloud App Security et d’une licence pour Azure Information Protection Premium P1. Dès que les deux licences sont en place, Cloud App Security synchronise les étiquettes des organisations à partir du service Azure Information Protection.

## <a name="prerequisites"></a>Composants requis

- Pour utiliser l’intégration de Azure Information Protection, vous devez activer le [connecteur d’application pour Office 365](connect-office-365-to-microsoft-cloud-app-security.md).

Pour utiliser des étiquettes dans Cloud App Security, les étiquettes doivent être publiées dans le cadre de la stratégie. Si vous utilisez Azure Information Protection, les étiquettes doivent être publiées via le portail Azure Information Protection. Si vous avez migré vers des étiquettes unifiées, les étiquettes doivent être publiées via le centre de sécurité et conformité Office 365.

Cloud App Security prend actuellement en charge l’application d’étiquettes de classification Azure Information Protection pour les types de fichiers suivants :

- Word : docm, docx, dotm, dotx
- Excel : xlam, xlsm, xlsx, xltx
- PowerPoint : potm, potx, ppsx, PPSM, pptm, pptx
- PDF
  > [!NOTE]
  > Pour PDF, vous devez utiliser des étiquettes unifiées.

Cette fonctionnalité est actuellement disponible pour les fichiers stockés dans Box, G suite, SharePoint Online et OneDrive entreprise. D’autres applications Cloud seront prises en charge dans les versions ultérieures.

Les fichiers qui ont été étiquetés avec une protection en dehors de Cloud App Security ne peuvent pas être modifiés par Cloud App Security. Toutefois, vous pouvez analyser ces fichiers en accordant des autorisations pour [inspecter le contenu des fichiers protégés](content-inspection.md#content-inspection-for-protected-files).

## <a name="how-it-works"></a>Fonctionnement

Vous êtes probablement familiarisé avec les étiquettes de classification des fichiers dans [Azure information protection](https://docs.microsoft.com/azure/information-protection/what-is-information-protection). Vous pouvez voir les balises de classification Azure Information Protection dans Cloud App Security. Dès que vous intégrez Cloud App Security à Azure Information Protection, Cloud App Security analyse les fichiers comme suit :

1. Cloud App Security récupère la liste de toutes les étiquettes de classification utilisées dans votre locataire. Cette action est effectuée toutes les heures pour maintenir la liste à jour.

2. Cloud App Security analyse ensuite les fichiers à la recherche d’étiquettes de classification, comme suit :

    - Si vous avez activé l’analyse automatique, tous les fichiers nouveaux ou modifiés sont ajoutés à la file d’attente d’analyse, et tous les fichiers et dépôts existants sont analysés.
    - Si vous définissez une stratégie de fichier pour rechercher des étiquettes de classification, ces fichiers sont ajoutés à la file d’attente d’analyse pour les étiquettes de classification.

3. Comme indiqué ci-dessus, ces analyses sont destinées aux étiquettes de classification découvertes lors de l’analyse initiale Cloud App Security pour voir les étiquettes de classification utilisées dans votre locataire. Les étiquettes externes, les étiquettes de classification définies par une personne externe à votre locataire, sont ajoutées à la liste des étiquettes de classification. Si vous ne souhaitez pas les Rechercher, activez la case à cocher **analyser uniquement les fichiers pour les étiquettes de classification de Azure information protection de ce locataire** .

4. Une fois que vous avez activé Azure Information Protection sur Cloud App Security, tous les nouveaux fichiers ajoutés à vos applications Cloud connectées sont analysés pour rechercher les étiquettes de classification.

5. Vous pouvez créer des stratégies dans Cloud App Security qui appliquent automatiquement vos étiquettes de classification.

## <a name="how-to-integrate-azure-information-protection-with-cloud-app-security"></a>Intégration de Azure Information Protection à Cloud App Security
  
### <a name="enable-azure-information-protection"></a>Activer Azure Information Protection

Pour intégrer Azure Information Protection avec Cloud App Security, il suffit de cliquer sur une seule case. En activant l’analyse automatique, vous activez la recherche de Azure Information Protection étiquettes de classification sur vos fichiers Office 365 sans avoir besoin de créer une stratégie. Après l’avoir activé, si des fichiers de votre environnement Cloud sont étiquetés avec des étiquettes de classification Azure Information Protection, vous les verrez dans Cloud App Security.

Pour permettre à Cloud App Security d’analyser les fichiers dont l’inspection du contenu est activée pour les étiquettes de classification :

1. Dans Cloud App Security, sous l’roue dentée paramètres, sélectionnez la page **paramètres** sous l’en-tête **système** .

    ![Menu paramètres](media/azip-system-settings.png)
1. Sous **Azure information protection**, sélectionnez **analyser automatiquement les fichiers pour Azure information protection étiquettes de classification**.

    ![activer Azure information protection](media/enable-azip.png)

Après avoir activé Azure Information Protection, vous pouvez voir les fichiers qui ont des étiquettes de classification et les filtrer par étiquette dans Cloud App Security. Une fois que Cloud App Security est connectée à l’application Cloud, vous pouvez utiliser les fonctionnalités d’intégration Azure Information Protection pour appliquer Azure Information Protection étiquettes de classification (avec ou sans protection) dans le portail de Cloud App Security, en les ajoutant directement aux fichiers ou en configurant une stratégie de fichier pour appliquer automatiquement des étiquettes de classification en tant qu’action de gouvernance.

> [!NOTE]
> L’analyse automatique n’analyse pas les fichiers existants tant qu’ils ne sont pas de nouveau modifiés. Pour analyser les fichiers existants en vue d’Azure Information Protection étiquettes de classification, vous devez avoir au moins une **stratégie de fichier** qui comprend l’inspection du contenu. Si vous n’en avez pas, créez une nouvelle **stratégie de fichier**, supprimez tous les filtres prédéfinis, sous **méthode d’inspection** , sélectionnez **DLP intégré**. Dans le champ **inspection du contenu** , sélectionnez inclure les **fichiers qui correspondent à une expression prédéfinie** et sélectionnez une valeur prédéfinie, puis enregistrez la stratégie. Cela permet l’inspection du contenu, qui détecte automatiquement Azure Information Protection étiquettes de classification.

#### <a name="set-internal-and-external-tags"></a>Définir des balises internes et externes

Par défaut, Cloud App Security analyse les étiquettes de classification qui ont été définies dans votre organisation, ainsi que celles externes définies par d’autres organisations. 

Pour ignorer les étiquettes de classification définies en dehors de votre organisation, dans le portail Cloud App Security, accédez à **paramètres** et **Azure information protection**. Sélectionnez **analyser uniquement les fichiers pour les Azure information protection les étiquettes de classification et les avertissements d’inspection du contenu de ce locataire**.

![ignorer les étiquettes](media/azip-ignore.png)

### <a name="apply-labels-directly-to-files"></a>Appliquer des étiquettes directement aux fichiers

1. Dans la page **fichiers** , sous **examiner**, sélectionnez le fichier que vous souhaitez protéger. Cliquez sur les trois points à la fin de la ligne du fichier, puis choisissez **appliquer l’étiquette de classification**.  

    ![protéger l’application](media/protect-app.png)
  
    >[!NOTE]
    > Cloud App Security pouvez appliquer des Azure Information Protection sur des fichiers qui ont jusqu’à 50 Mo.

2. Vous êtes invité à choisir l’une des étiquettes de classification de votre organisation à appliquer au fichier, puis à cliquer sur **appliquer**.

    ![étiquette de classification de la protection](media/protect-template.png)

3. Une fois que vous avez choisi une étiquette de classification et cliqué sur appliquer, Cloud App Security applique l’étiquette de classification au fichier d’origine.

4. Vous pouvez également supprimer des étiquettes de classification en choisissant l’option **Supprimer l’étiquette de classification** .

> [!NOTE]
> Vous pouvez supprimer des étiquettes uniquement si elles n’incluent pas de protection, et si elles ont été appliquées à partir de Cloud App Security, et non les étiquettes appliquées directement dans Information Protection.

Pour plus d’informations sur la façon dont Cloud App Security et Azure Information Protection fonctionnent ensemble, consultez [protéger les données contre les erreurs des utilisateurs](https://docs.microsoft.com/enterprise-mobility-security/solutions/protect-data-user-mistake).

### <a name="automatically-label-files"></a>Étiqueter automatiquement les fichiers

Vous pouvez appliquer automatiquement des étiquettes de classification aux fichiers en créant une stratégie de fichier et en définissant **appliquer l’étiquette de classification** en tant qu’action de gouvernance.

Suivez ces instructions pour créer la stratégie de fichier :

1. Créer une stratégie de fichier.
2. Définissez la stratégie pour inclure le type de fichier que vous souhaitez détecter. Par exemple, sélectionnez tous les fichiers pour lesquels le **niveau d’accès** n’est pas égal à **interne** et où l' **unité d’organisation propriétaire** est égale à votre équipe finance.
3. Sous actions de gouvernance pour l’application appropriée, cliquez sur **appliquer une étiquette de classification** , puis sélectionnez le type d’étiquette.

    ![Appliquer l’étiquette](media/aip-gov-action.png)

> [!NOTE]
> La possibilité d’appliquer automatiquement une étiquette Azure Information Protection via une stratégie de fichier est une puissante fonctionnalité. Pour protéger les clients contre l’application par erreur d’une étiquette à un grand nombre de fichiers, il existe, pour des raisons de sécurité, une limite quotidienne de 100 actions **Appliquer une étiquette** par application et par client. Une fois cette limite quotidienne atteinte, l’action Appliquer une étiquette s’interrompt temporairement et reprend automatiquement le jour suivant (après 12:00 UTC). Pour augmenter la limite pour votre locataire, ouvrez un ticket de support.

### <a name="control-file-exposure"></a>Contrôler l’exposition des fichiers

- Par exemple, si Voici un document que vous avez étiqueté avec une étiquette de classification Azure Information Protection :

    ![écran d’Azure Information Protection de l’exemple](media/azip-screen.png)

- Vous pouvez consulter ce document dans Cloud App Security en filtrant sur l’étiquette de classification pour Azure Information Protection dans la page **fichiers** .

    ![Cloud App Security comparé à Azure Information Protection](media/cas-compared-azip.png)

- Vous pouvez obtenir plus d’informations sur ces fichiers et leurs étiquettes de classification dans le tiroir de fichier. Il vous suffit de cliquer sur le fichier approprié dans la page **fichiers** et de vérifier s’il possède une étiquette de classification.

    ![tiroir de fichier](media/azip-file-drawer.png)

- Ensuite, vous pouvez créer des stratégies de fichiers dans Cloud App Security pour contrôler les fichiers qui sont partagés de façon inappropriée et rechercher les fichiers étiquetés et récemment modifiés.

- Vous pouvez créer une stratégie qui applique automatiquement une étiquette de classification à des fichiers spécifiques.
- Vous pouvez également déclencher des alertes sur les activités liées à la classification des fichiers.

> [!Note]
> Lorsque Azure Information Protection étiquettes sont désactivées sur un fichier, les étiquettes désactivées apparaissent comme étant désactivées dans Cloud App Security. Les étiquettes supprimées ne sont pas affichées.

**Exemple de stratégie-données confidentielles partagées en externe sur Box :**

1. Créer une stratégie de fichier.
2. Définissez le nom, la gravité et la catégorie de la stratégie.
3. Ajoutez les filtres suivants pour rechercher toutes les données confidentielles partagées en externe sur Box :

    ![stratégie de confidentialité](media/azip-confidentiality-policy.png)

**Exemple de stratégie : données restreintes récemment modifiées en dehors du dossier Finance sur SharePoint :**

1. Créer une stratégie de fichier.
2. Définissez le nom, la gravité et la catégorie de la stratégie.
3. Ajoutez les filtres suivants pour rechercher tous les fichiers restreints récemment modifiés tout en excluant le dossier Finance dans l’option de sélection de dossier :

    ![stratégie de données restreinte](media/azip-restricted-data-policy.png)

Vous pouvez également choisir de définir des alertes, une notification utilisateur ou d’effectuer une action immédiate pour ces stratégies.
En savoir plus sur les [actions de gouvernance](governance-actions.md).

Pour en savoir plus sur [Azure information protection](https://docs.microsoft.com/information-protection/understand-explore/what-is-information-protection) , consultez le [didacticiel de démarrage rapide](https://docs.microsoft.com/information-protection/get-started/infoprotect-quick-start-tutorial)Azure information protection.

## <a name="next-steps"></a>Étapes suivantes :

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

## <a name="related-videos"></a>Vidéos associées

> [!div class="nextstepaction"]
> [Intégrations de Cloud App Security + Azure Information Protection](https://channel9.msdn.com/Shows/Microsoft-Security/MCAS--AIP-Integrations)  

[!INCLUDE [Open support ticket](includes/support.md)]
