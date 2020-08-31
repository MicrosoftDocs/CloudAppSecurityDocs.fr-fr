---
title: Intégrer Azure Information Protection à Cloud App Security
description: Cet article fournit des informations sur la façon de tirer parti de vos balises Azure Information Protection dans Cloud App Security afin de renforcer le contrôle de l’utilisation des applications cloud de votre organisation.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/09/2019
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 0759c218b1125fa6c383e861228f6c6606841072
ms.sourcegitcommit: c174a7ada5c6a14f0fea9870672898c54e5e3b52
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89149612"
---
# <a name="azure-information-protection-integration"></a>Intégration d’Azure Information Protection

*S’applique à : Microsoft Cloud App Security*

Microsoft Cloud App Security vous permet d’appliquer des étiquettes de classification Azure Information Protection automatiquement, avec ou sans protection, à des fichiers, en tant qu’action de gouvernance de stratégie de fichier. Vous pouvez également rechercher des fichiers en filtrant sur l’étiquette de classification appliquée dans le portail Cloud App Security. L’utilisation de classifications accroît la visibilité et le contrôle de vos données sensibles dans le cloud. Pour intégrer Azure Information Protection à Cloud App Security, il suffit de cocher une seule case.

> [!NOTE]
> Cet article s’applique également à Microsoft 365 des étiquettes de sensibilité unifiée si vous avez déjà [migré vos étiquettes de classification pour le centre de sécurité et conformité Office 365](/azure/information-protection/configure-policy-migrate-labels). Si vous n’avez pas migré vos étiquettes de classification existantes et que vous commencez à créer de nouvelles étiquettes dans le centre de sécurité et conformité Office 365, Cloud App Security utilisera uniquement les étiquettes préexistantes configurées dans le portail Azure Information Protection.

En intégrant Azure Information Protection à Cloud App Security, vous pouvez utiliser toute la puissance des services et des fichiers sécurisés dans votre cloud, notamment :

- La possibilité d’appliquer des étiquettes de classification en tant qu’action de gouvernance aux fichiers qui correspondent à des stratégies spécifiques
- La possibilité de voir tous les fichiers classifiés à un emplacement centralisé.
- La possibilité d’investiguer en fonction du niveau de classification et de quantifier l’exposition des données sensibles sur vos applications cloud.
- La possibilité de créer des stratégies pour que les fichiers classifiés soient gérés correctement.

> [!NOTE]
> Pour activer cette fonctionnalité, vous avez besoin d’une licence Cloud App Security et d’une licence pour Azure Information Protection Premium P1. Dès que ces deux licences sont en place, Cloud App Security synchronise les étiquettes des organisations à partir du service Azure Information Protection.

## <a name="prerequisites"></a>Prérequis

- Pour utiliser l’intégration de Azure Information Protection, vous devez activer le [connecteur d’application pour Microsoft 365](connect-office-365-to-microsoft-cloud-app-security.md).

Pour utiliser des étiquettes dans Cloud App Security, les étiquettes doivent être publiées dans le cadre de la stratégie. Si vous utilisez Azure Information Protection, les étiquettes doivent être publiées via le portail Azure Information Protection. Si vous avez migré vers des étiquettes unifiées, les étiquettes doivent être publiées via le centre de sécurité et conformité Office 365.

Cloud App Security prend actuellement en charge l’application d’étiquettes de classification Azure Information Protection pour les types de fichiers suivants :

- Word : docm, docx, dotm, dotx
- Excel : xlam, xlsm, xlsx, xltx
- PowerPoint : potm, potx, ppsx, ppsm, pptm, pptx
- PDF
  > [!NOTE]
  > Pour PDF, vous devez utiliser des étiquettes unifiées.

Cette fonctionnalité est actuellement disponible pour les fichiers stockés dans Box, G Suite, SharePoint Online et OneDrive Entreprise. D’autres applications cloud seront prises en charge dans les prochaines versions.

Les fichiers qui ont été étiquetés avec une protection en dehors de Cloud App Security ne peuvent pas être modifiés par Cloud App Security. Toutefois, vous pouvez analyser ces fichiers en accordant des autorisations pour [inspecter le contenu des fichiers protégés](content-inspection.md#content-inspection-for-protected-files).

## <a name="how-it-works"></a>Fonctionnement

Vous connaissez probablement déjà les étiquettes de classification des fichiers dans [Azure Information Protection](/azure/information-protection/what-is-information-protection). Vous pouvez voir les étiquettes de classification d’Azure Information Protection dans Cloud App Security. Dès que vous intégrez Cloud App Security à Azure Information Protection, Cloud App Security analyse les fichiers comme suit :

1. Cloud App Security récupère la liste de toutes les étiquettes de classification utilisées dans votre locataire (tenant). Cette action est effectuée toutes les heures pour maintenir la liste à jour.

2. Cloud App Security recherche ensuite les étiquettes de classification pour les fichiers, comme suit :

    - Si vous avez activé l’analyse automatique, tous les fichiers nouveaux ou modifiés sont ajoutés à la file d’attente d’analyse, et tous les fichiers et dépôts existants sont analysés.
    - Si vous définissez une stratégie de fichier pour rechercher les étiquettes de classification, ces fichiers sont ajoutés à la file d’attente d’analyse pour les étiquettes de classification.

3. Comme indiqué ci-dessus, ces analyses concernent les étiquettes de classification découvertes lors de l’analyse initiale que Cloud App Security réalise pour déterminer les étiquettes de classification utilisées dans votre locataire. Les étiquettes externes, qui sont des étiquettes de classification définies par une personne externe à votre locataire, sont ajoutées à la liste des étiquettes de classification. Si vous ne voulez pas effectuer d’analyse pour ces étiquettes, cochez la case **Analyser uniquement les fichiers pour les étiquettes de classification Azure Information Protection de ce locataire**.

4. Une fois que vous avez activé Azure Information Protection sur Cloud App Security, tous les nouveaux fichiers ajoutés à vos applications Cloud connectées sont analysés pour rechercher les étiquettes de classification.

5. Vous pouvez créer des stratégies dans Cloud App Security qui appliquent automatiquement vos étiquettes de classification.

## <a name="how-to-integrate-azure-information-protection-with-cloud-app-security"></a>Comment intégrer Azure Information Protection à Cloud App Security

### <a name="enable-azure-information-protection"></a>Activer Azure Information Protection

Il vous suffit de cocher une seule case pour intégrer Azure Information Protection à Cloud App Security. En activant l’analyse automatique, vous activez la recherche de Azure Information Protection étiquettes de classification sur vos fichiers de Microsoft 365 sans avoir besoin de créer une stratégie. Après avoir activé cette option, si des fichiers de votre environnement cloud sont étiquetés avec des étiquettes de classification Azure Information Protection, vous les voyez dans Cloud App Security.

Pour permettre à Cloud App Security d’analyser des fichiers quand l’inspection du contenu est activée pour les étiquettes de classification :

1. Dans Cloud App Security, sous la roue dentée Paramètres, sélectionnez la page **Paramètres** sous l’en-tête **Système**.

    ![menu Paramètres](media/azip-system-settings.png)
1. Sous **Azure Information Protection**, sélectionnez **Analyser automatiquement les nouveaux fichiers pour détecter les étiquettes de classification Azure Information Protection**.

    ![activer azure information protection](media/enable-azip.png)

Après avoir activé Azure Information Protection, vous pouvez voir les fichiers qui ont des étiquettes de classification et les filtrer par étiquette dans Cloud App Security. Une fois Cloud App Security connecté à l’application cloud, vous pouvez utiliser les fonctionnalités d’intégration Azure Information Protection pour appliquer des étiquettes de classification Azure Information Protection (avec ou sans protection) dans le portail Cloud App Security, en les ajoutant directement aux fichiers ou en configurant une stratégie de fichier pour appliquer automatiquement des étiquettes de classification en tant qu’action de gouvernance.

> [!NOTE]
> L’analyse automatique ne retraite les fichiers existants que s’ils sont modifiés. Pour analyser les fichiers existants en vue d’Azure Information Protection étiquettes de classification, vous devez avoir au moins une **stratégie de fichier** qui comprend l’inspection du contenu. Si vous n’en avez pas, créez une nouvelle **stratégie de fichier**, supprimez tous les filtres prédéfinis, sous **méthode d’inspection** , sélectionnez **DLP intégré**. Dans le champ **inspection du contenu** , sélectionnez inclure les **fichiers qui correspondent à une expression prédéfinie** et sélectionnez une valeur prédéfinie, puis enregistrez la stratégie. Cette opération permet d’activer l’inspection de contenu qui détecte automatiquement les étiquettes de classification Azure Information Protection.

#### <a name="set-internal-and-external-tags"></a>Définir des étiquettes internes et externes

Par défaut, Cloud App Security analyse les étiquettes de classification qui ont été définies dans votre organisation, ainsi que les étiquettes externes définies par d’autres organisations.

Pour ignorer les étiquettes de classification définies en externe à votre organisation, dans le portail Cloud App Security, accédez à **Paramètres** et **Azure Information Protection**. Sélectionnez **Analyser les fichiers uniquement pour détecter les étiquettes de classification Azure Information Protection et les avertissements émis suite à l'inspection du contenu de ce locataire**.

![ignorer les étiquettes](media/azip-ignore.png)

### <a name="apply-labels-directly-to-files"></a>Appliquer des étiquettes directement à des fichiers

1. Sur la page **Fichiers** sous **Investiguer**, sélectionnez le fichier que vous souhaitez protéger. Cliquez sur les points de suspension à la fin de la ligne du fichier, puis choisissez **Appliquer l’étiquette de classification**.

    ![protéger une application](media/protect-app.png)

    >[!NOTE]
    > Cloud App Security peut appliquer Azure Information Protection sur des fichiers de 50 Mo maximum.

2. Vous êtes invité à choisir une des étiquettes de classification de votre organisation à appliquer au fichier. Cliquez ensuite sur **Appliquer**.

    ![étiquette de classification de protection](media/protect-template.png)

3. Une fois que vous avez choisi une étiquette de classification et que vous avez cliqué sur Appliquer, Cloud App Security applique cette étiquette au fichier d’origine.

4. Vous pouvez également supprimer des étiquettes de classification en choisissant l’option **Supprimer l’étiquette de classement**.

> [!NOTE]
> Seules sont supprimables les étiquettes qui ne comportent pas de protection et ont été appliquées dans Cloud App Security, et non celles qui ont été appliquées directement dans Information Protection.

Pour plus d’informations sur la façon dont Cloud App Security et Azure Information Protection fonctionnent ensemble, consultez [appliquer automatiquement des étiquettes de classification Azure information protection](use-case-information-protection.md).

### <a name="automatically-label-files"></a>Étiqueter automatiquement des fichiers

Vous pouvez appliquer automatiquement des étiquettes de classification à des fichiers en créant une stratégie de fichier et en définissant **Appliquer l’étiquette de classification** comme action de gouvernance.

Suivez ces instructions pour créer la stratégie de fichier :

1. Créez une stratégie de fichier.
2. Définissez la stratégie en incluant le type de fichier que vous voulez détecter. Par exemple, sélectionnez tous les fichiers où **Niveau d’accès** n’est pas égal à **Interne** et où **UO propriétaire** est égal à votre équipe Finance.
3. Sous les actions de gouvernance pour l’application concernée, cliquez sur **Appliquer une étiquette de classification**, puis sélectionnez le type d’étiquette.

    ![Appliquer une étiquette](media/aip-gov-action.png)

> [!NOTE]
> La possibilité d’appliquer automatiquement une étiquette Azure Information Protection via la stratégie de fichier est une puissante fonctionnalité. Pour protéger les clients contre toute application par erreur d’une étiquette à un grand nombre de fichiers, il existe, pour des raisons de sécurité, une limite quotidienne de 100 actions **Appliquer une étiquette** par application et le client. Une fois la limite quotidienne atteinte, l’action Appliquer une étiquette est temporairement interrompue, puis reprend automatiquement le jour suivant (après 12:00 UTC). Pour augmenter la limite pour votre locataire, ouvrez un ticket de support.

### <a name="control-file-exposure"></a>Contrôler l’exposition des fichiers

- Par exemple, si ce qui suit est un document que vous avez étiqueté avec une étiquette de classification Azure Information Protection :

    ![exemple d’écran Azure Information Protection](media/azip-screen.png)

- Vous pouvez voir ce document dans Cloud App Security en filtrant sur l’étiquette de classification pour Azure Information Protection dans la page **Fichiers**.

    ![Comparaison de Cloud App Security et d’Azure Information Protection](media/cas-compared-azip.png)

- Vous pouvez obtenir plus d’informations sur ces fichiers et leurs étiquettes de classification dans le tiroir des fichiers. Il vous suffit de cliquer sur le fichier approprié dans la page **Fichiers** pour voir s’il a une étiquette de classification.

    ![tiroir du fichier](media/azip-file-drawer.png)

- Vous pouvez ensuite créer des stratégies de fichiers dans Cloud App Security pour contrôler les fichiers qui sont partagés de façon inappropriée, et pour rechercher les fichiers étiquetés qui ont été modifiés récemment.

- Vous pouvez créer une stratégie qui applique automatiquement une étiquette de classification à des fichiers spécifiques.
- Vous pouvez aussi déclencher des alertes sur des activités liées à la classification des fichiers.

> [!Note]
> Quand les étiquettes Azure Information Protection sont désactivées sur un fichier, elles apparaissent désactivées dans Cloud App Security. Les étiquettes supprimées ne sont pas affichées.

**Exemple de stratégie : données confidentielles partagées en externe sur Box :**

1. Créez une stratégie de fichier.
2. Définissez le nom, la gravité et la catégorie de la stratégie.
3. Ajoutez les filtres suivants pour rechercher toutes les données confidentielles qui sont partagées en externe sur Box :

    ![stratégie confidentialité](media/azip-confidentiality-policy.png)

**Exemple de stratégie : données restreintes qui ont été modifiées récemment en dehors du dossier Finance sur SharePoint :**

1. Créez une stratégie de fichier.
2. Définissez le nom, la gravité et la catégorie de la stratégie.
3. Ajoutez les filtres suivants pour rechercher tous les fichiers restreints qui ont été modifiés récemment tout en excluant le dossier Finance dans l’option de sélection de dossier :

    ![stratégie données restreintes](media/azip-restricted-data-policy.png)

Vous pouvez également définir des alertes ou une notification utilisateur ou encore prendre des mesures immédiates pour ces stratégies.
En savoir plus sur les [actions de gouvernance](governance-actions.md).

En savoir plus sur [Azure Information Protection](/information-protection/understand-explore/what-is-information-protection) et suivre le [didacticiel de démarrage rapide](/information-protection/get-started/infoprotect-quick-start-tutorial) pour Azure Information Protection.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

## <a name="related-videos"></a>Vidéos associées

> [!div class="nextstepaction"]
> [Intégrations de Cloud App Security + Azure Information Protection](https://channel9.msdn.com/Shows/Microsoft-Security/MCAS--AIP-Integrations)

[!INCLUDE [Open support ticket](includes/support.md)]
