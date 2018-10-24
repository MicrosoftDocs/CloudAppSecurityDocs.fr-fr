---
title: Intégrer Azure Information Protection à Cloud App Security | Microsoft Docs
description: Cet article fournit des informations sur la façon de tirer parti de vos balises Azure Information Protection dans Cloud App Security afin de renforcer le contrôle de l’utilisation des applications cloud de votre organisation.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/08/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 8168319a-199f-4e6c-ad68-e0f236480803
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: c68426af8eb0f12bc0157c3b24841e381dd119ce
ms.sourcegitcommit: c80c584c444b12dc8c788208cf973b46192b0cf0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/10/2018
ms.locfileid: "49072869"
---
*S’applique à : Microsoft Cloud App Security*


# <a name="azure-information-protection-integration"></a>Intégration d’Azure Information Protection

Microsoft Cloud App Security vous permet d’appliquer des étiquettes de classification Azure Information Protection automatiquement, avec ou sans protection, à des fichiers, en tant qu’action de gouvernance de stratégie de fichier. Vous pouvez également rechercher des fichiers en filtrant sur l’étiquette de classification appliquée dans le portail Cloud App Security. Ceci accroît la visibilité et le contrôle de vos données sensibles dans le cloud. Pour intégrer Azure Information Protection à Cloud App Security, il suffit de cocher une seule case. 

En intégrant Azure Information Protection à Cloud App Security, vous pouvez utiliser toute la puissance des services et des fichiers sécurisés dans votre cloud, notamment :
- La possibilité d’appliquer des étiquettes de classification en tant qu’action de gouvernance aux fichiers qui correspondent à des stratégies spécifiques
- La possibilité de voir tous les fichiers classifiés à un emplacement centralisé.
- La possibilité d’investiguer en fonction du niveau de classification et de quantifier l’exposition des données sensibles sur vos applications cloud.
- La possibilité de créer des stratégies pour que les fichiers classifiés soient gérés correctement.


> [!NOTE] 
> Pour activer cette fonctionnalité, vous avez besoin d’une licence Cloud App Security et d’une licence pour Azure Information Protection Premium P1. Dès que ces deux licences sont en place, Cloud App Security synchronise les étiquettes des organisations à partir du service Azure Information Protection.


## <a name="prerequisites"></a>Prérequis

- Pour utiliser l’intégration à Azure Information Protection, vous devez activer le [connecteur d’applications pour Office 365](connect-office-365-to-microsoft-cloud-app-security.md).

Cloud App Security prend actuellement en charge l’application d’étiquettes de classification Azure Information Protection pour les types de fichiers suivants :

- Word : docm, docx, dotm, dotx
- Excel : xlam, xlsm, xlsx, xltx
- PowerPoint : potm, potx, ppsx, ppsm, pptm, pptx
- Les fichiers PDF seront disponibles dans des versions ultérieures 

Cette fonctionnalité est actuellement disponible pour les fichiers stockés dans Box, G Suite, SharePoint Online et OneDrive Entreprise. D’autres applications cloud seront prises en charge dans les prochaines versions.

Les fichiers qui ont été étiquetés avec la protection en dehors de Cloud App Security ne peuvent pas être analysés ou modifiés par Cloud App Security pour l’instant. Les fichiers qui ont été étiquetés (sans protection) en dehors de Cloud App Security peuvent être analysés, et Cloud App Security peut appliquer une autre étiquette (avec ou sans protection) telle qu’elle est définie dans les stratégies Cloud App Security.


## <a name="how-it-works"></a>Fonctionnement
Vous connaissez probablement déjà les étiquettes de classification des fichiers dans [Azure Information Protection](https://docs.microsoft.com/azure/information-protection/what-is-information-protection). Vous pouvez voir les étiquettes de classification d’Azure Information Protection dans Cloud App Security. Dès que vous intégrez Cloud App Security à Azure Information Protection, Cloud App Security analyse les fichiers comme suit :

1. Cloud App Security récupère la liste de toutes les étiquettes de classification utilisées dans votre locataire (tenant). Cette opération est effectuée toutes les heures pour maintenir la liste à jour.

2. Cloud App Security recherche ensuite les étiquettes de classification pour les fichiers, comme suit :

   1. Si vous avez autorisé une analyse automatique (voir ci-dessous), tous les fichiers nouveaux ou modifiés sont ajoutés à la file d’attente de l’analyse tandis que tous les fichiers et référentiels existants sont analysés, classés et protégés.
   2. Si vous définissez une stratégie de fichier (voir ci-dessous) pour rechercher les étiquettes de classification, ces fichiers sont ajoutés à la file d’attente d’analyse pour les étiquettes de classification.

3. Comme indiqué ci-dessus, ces analyses concernent les étiquettes de classification découvertes lors de l’analyse initiale que Cloud App Security réalise pour déterminer les étiquettes de classification utilisées dans votre locataire. Les étiquettes externes, qui sont des étiquettes de classification définies par une personne externe à votre locataire, sont ajoutées à la liste des étiquettes de classification. Si vous ne voulez pas rechercher ces étiquettes, cochez la case **Analyser uniquement les fichiers pour les étiquettes de classification Azure Information Protection de ce locataire** (voir ci-dessous).

4. Une fois que vous avez activé Azure Information Protection sur Cloud App Security, les étiquettes de classification sont également recherchées dans tous les nouveaux fichiers ajoutés à Office 365.

5. Vous pouvez créer des stratégies dans Cloud App Security qui appliquent automatiquement vos étiquettes de classification.

## <a name="how-to-integrate-azure-information-protection-with-cloud-app-security"></a>Comment intégrer Azure Information Protection à Cloud App Security
  
### <a name="enable-azure-information-protection"></a>Activer Azure Information Protection

Il vous suffit de cocher une seule case pour intégrer Azure Information Protection à Cloud App Security. Le fait d’activer l’analyse automatique permet d’activer la recherche des étiquettes de classification Azure Information Protection dans vos fichiers Office 365 sans devoir créer de stratégie. Après avoir activé cette option, si des fichiers de votre environnement cloud sont étiquetés avec des étiquettes de classification Azure Information Protection, vous les voyez dans Cloud App Security.

Pour permettre à Cloud App Security d’analyser des fichiers quand l’inspection du contenu est activée pour les étiquettes de classification :

1. Dans Cloud App Security, sous l’icône de roue dentée des paramètres, sélectionnez la page **Paramètres généraux**.
2. Sous Azure Information Protection, sélectionnez **Détecter automatiquement les étiquettes de classification Azure Information Protection dans les fichiers**. 

Après avoir activé Azure Information Protection, vous pouvez voir les fichiers qui ont des étiquettes de classification et les filtrer par étiquette dans Cloud App Security. Une fois Cloud App Security connecté à l’application cloud, vous pouvez utiliser les fonctionnalités d’intégration Azure Information Protection de Cloud App Security qui vous permettent d’appliquer des étiquettes Azure Information Protection (avec ou sans protection) directement dans le portail Cloud App Security, en les ajoutant directement aux fichiers ou en configurant une stratégie de fichier pour appliquer automatiquement des étiquettes de classification en tant qu’action de gouvernance.


 ![activer azure information protection](./media/enable-azip.png)

> [!NOTE] 
> L’analyse automatique ne retraite les fichiers existants que s’ils sont modifiés. Si vous voulez analyser les fichiers existants pour les étiquettes de classification Azure Information Protection, vous devez avoir au moins une **stratégie Fichier d’inspection de contenu**. Si vous n’en avez aucune, créez une **stratégie Fichier**, supprimez tous les filtres prédéfinis et sélectionnez l’option **Inspection de contenu**. Ensuite, sous **Inspection de contenu**, cliquez sur **Inclure les fichiers qui correspondent à une expression prédéfinie**, sélectionnez une valeur prédéfinie et enregistrez la stratégie. Cette opération permet d’activer l’inspection de contenu qui détecte automatiquement les étiquettes de classification Azure Information Protection.

#### <a name="set-internal-and-external-tags"></a>Définir des étiquettes internes et externes
Par défaut, Cloud App Security analyse les étiquettes de classification qui ont été définies dans votre organisation, ainsi que les étiquettes externes qui ont été définies par d’autres organisations. 


Pour les ignorer l’ensemble des étiquettes de classification externes à votre organisation, dans le portail Cloud App Security, sous **Paramètres généraux**, sous **Paramètres de sécurité Azure**, sélectionnez **Ignorer les étiquettes de classification Azure Information Protection des autres locataires**.
 
![ignorer les étiquettes](./media/azip-ignore.png)

### <a name="apply-labels-directly-to-files"></a>Appliquer des étiquettes directement à des fichiers

1. Dans la page **Fichiers**, sélectionnez le fichier que vous voulez protéger, cliquez sur les trois points à la fin de la ligne correspondant au fichier, puis choisissez **Appliquer l’étiquette de classification**.

   ![protéger une application](./media/protect-app.png)
  
   >[!NOTE]
   > Cloud App Security peut appliquer Azure Information Protection sur des fichiers de 50 Mo maximum.  

2. Vous êtes invité à choisir une des étiquettes de classification de votre organisation à appliquer au fichier. Cliquez ensuite sur **Appliquer**. 
   ![étiquette de classification de protection](./media/protect-template.png)

3. Une fois que vous avez choisi une étiquette de classification et que vous avez cliqué sur Appliquer, Cloud App Security applique cette étiquette au fichier d’origine.

4. Vous pouvez également supprimer des étiquettes de classification en choisissant l’option **Supprimer l’étiquette de classement**. 


Pour plus d’informations sur l’interaction entre Cloud App Security et Azure Information Protection, consultez [Protéger les données contre les erreurs des utilisateurs](https://docs.microsoft.com/enterprise-mobility-security/solutions/protect-data-user-mistake).

### <a name="automatically-label-files"></a>Étiqueter automatiquement des fichiers

Vous pouvez appliquer automatiquement des étiquettes de classification à des fichiers en créant une stratégie de fichier et en définissant **Appliquer l’étiquette de classification** comme action de gouvernance.

Suivez ces instructions pour créer la stratégie de fichier :

1. Créez une stratégie de fichier.
2. Définissez la stratégie en incluant le type de fichier que vous voulez détecter, par exemple tous les fichiers où **Niveau d’accès** n’est pas égal à **Interne** et où **UO propriétaire** est égal à votre équipe Finance. 
3. Sous les actions de gouvernance pour l’application concernées, choisissez **Appliquer une étiquette de classification**, puis sélectionnez le type d’étiquette.

   ![Appliquer une étiquette](./media/aip-gov-action.png)

> [!NOTE]
> La possibilité d’appliquer automatiquement une étiquette Azure Information Protection via la stratégie de fichier est une puissante fonctionnalité. Pour protéger les clients contre toute application par erreur d’une étiquette à un grand nombre de fichiers, il existe, pour des raisons de sécurité, une limite quotidienne de 100 actions **Appliquer une étiquette** par application et le client. Une fois la limite quotidienne atteinte, l’action Appliquer une étiquette est temporairement interrompue, puis reprend automatiquement le jour suivant (après 12:00 UTC). Pour augmenter la limite de votre client, [contactez le support Cloud App Security](mailto:cascoresupport@microsoft.com).

### <a name="control-file-exposure"></a>Contrôler l’exposition des fichiers

- S’il s’agit du document que vous avez étiqueté avec une étiquette de classification Azure Information Protection :

   ![exemple d’écran Azure Information Protection](./media/azip-screen.png)

- Vous pouvez voir ce fichier dans Cloud App Security, dans la page **Fichiers**, en filtrant sur l’étiquette de classification :

   ![Comparaison de Cloud App Security et d’Azure Information Protection](./media/cas-compared-azip.png)

- Vous pouvez obtenir plus d’informations sur ces fichiers et leurs étiquettes de classification dans le tiroir de fichiers, en cliquant sur le fichier approprié dans la page **Fichiers** et en vérifiant s’il a une étiquette de classification :

   ![tiroir du fichier](./media/azip-file-drawer.png)

- Vous pouvez ensuite créer des stratégies de fichiers dans Cloud App Security pour contrôler les fichiers qui sont partagés de façon inappropriée, et pour rechercher les fichiers étiquetés qui ont été modifiés récemment.
- En outre, vous pouvez déclencher des alertes sur des activités liées à des fichiers classifiés.

  ![balises azure information protection dans cloud app security](./media/azip-tags-in-cas.png)

- Vous pouvez également créer une stratégie qui applique automatiquement une étiquette de classification à des fichiers spécifiques.


> [!Note]
> Quand les étiquettes Azure Information Protection sont désactivées sur un fichier, elles apparaissent désactivées dans Cloud App Security. Les étiquettes supprimées ne sont pas affichées.


**Exemple de stratégie : données confidentielles partagées en externe sur Box :**

1.  Créez une stratégie de fichier.
2.  Définissez le nom, la gravité et la catégorie de la stratégie.
3.  Ajoutez les filtres suivants pour rechercher toutes les données confidentielles qui sont partagées en externe sur Box :

![stratégie confidentialité](./media/azip-confidentiality-policy.png) 

**Exemple de stratégie : données restreintes qui ont été modifiées récemment en dehors du dossier Finance sur SharePoint :**

1.  Créez une stratégie de fichier.
2.  Définissez le nom, la gravité et la catégorie de la stratégie.
3.  Ajoutez les filtres suivants pour rechercher toutes les données restreintes qui ont été modifiées récemment et ajouter le dossier Finance dans l’option de sélection de dossier : 
 
![stratégie données restreintes](./media/azip-restricted-data-policy.png) 

Vous pouvez également définir des alertes ou une notification utilisateur ou encore prendre des mesures immédiates pour ces stratégies.
En savoir plus sur les [actions de gouvernance](governance-actions.md).

En savoir plus sur [Azure Information Protection](https://docs.microsoft.com/information-protection/understand-explore/what-is-information-protection) et suivre le [didacticiel de démarrage rapide](https://docs.microsoft.com/information-protection/get-started/infoprotect-quick-start-tutorial) pour Azure Information Protection.


 
## <a name="related-videos"></a>Vidéos connexes  
[Intégrations de Cloud App Security + Azure Information Protection](https://channel9.msdn.com/Shows/Microsoft-Security/MCAS--AIP-Integrations)  

## <a name="next-steps"></a>Étapes suivantes 
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
