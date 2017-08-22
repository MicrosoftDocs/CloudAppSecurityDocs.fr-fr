---
title: "Intégrer Azure Information Protection à Cloud App Security | Microsoft Docs"
description: "Cet article fournit des informations sur la façon de tirer parti de vos balises Azure Information Protection dans Cloud App Security afin de renforcer le contrôle de l’utilisation des applications cloud de votre organisation."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/20/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 8168319a-199f-4e6c-ad68-e0f236480803
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 003c56d1d05c35adac55c568d72beab18243519f
ms.sourcegitcommit: 9111960557afb30ea2d6c155afd4885a7ca1b278
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2017
---
# <a name="azure-information-protection-integration"></a>Intégration d’Azure Information Protection

Cloud App Security vous permet d’examiner des fichiers et de définir des stratégies en fonction des étiquettes de classification d’Azure Information Protection, permettant une plus grande visibilité et un contrôle accru de vos données sensibles dans le cloud. Pour intégrer Azure Information Protection à Cloud App Security, il suffit de cocher une seule case. 

En intégrant Azure Information Protection dans Cloud App Security, vous pouvez tirer parti de toute la puissance des services et des fichiers sécurisés dans le cloud, notamment :
- La possibilité de voir tous les fichiers classifiés à un emplacement centralisé.
- La possibilité d’investiguer en fonction du niveau de classification et de quantifier l’exposition des données sensibles sur vos applications cloud.
- La possibilité de créer des stratégies pour que les fichiers classifiés soient gérés correctement.

> [!NOTE] 
> Pour activer cette fonctionnalité, vous avez besoin d’une licence Cloud App Security et d’une licence pour Azure Information Protection Premium P1 ou P2. Dès que ces deux licences sont en place, Cloud App Security synchronise les étiquettes des organisations à partir du service Azure Information Protection.

## <a name="how-it-works"></a>Fonctionnement
Vous connaissez probablement déjà les étiquettes de classification des fichiers dans [Azure Information Protection](https://docs.microsoft.com/information-protection/). Vous pouvez voir les étiquettes de classification d’Azure Information Protection dans Cloud App Security. Dès que vous intégrez Cloud App Security à Azure Information Protection, Cloud App Security analyse les fichiers comme suit :
1. Cloud App Security récupère la liste de toutes les étiquettes de classification utilisées dans votre locataire (tenant). Cette opération est effectuée toutes les heures pour maintenir la liste à jour.
2. Cloud App Security recherche ensuite les étiquettes de classification pour les fichiers, comme suit : a. Si vous avez activé l’analyse automatique (voir ci-dessous), tous les fichiers nouveaux ou modifiés sont ajoutés à la file d’attente d’analyse.
    b. Si vous définissez une stratégie de fichier (voir ci-dessous) pour rechercher les étiquettes de classification, ces fichiers sont ajoutés à la file d’attente d’analyse pour les étiquettes de classification.
3. Comme indiqué ci-dessus, ces analyses concernent les étiquettes de classification découvertes lors de l’analyse initiale que Cloud App Security réalise pour déterminer les étiquettes de classification utilisées dans votre locataire. Les étiquettes externes, qui sont des étiquettes de classification définies par une personne externe à votre locataire, sont ajoutées à la liste des étiquettes de classification. Si vous ne voulez pas effectuer d’analyse pour ces étiquettes, cochez la case **Analyser uniquement les fichiers pour les étiquettes de classification Azure Information Protection de ce locataire** (voir ci-dessous).
4. Une fois que vous avez activé Azure Information Protection sur Cloud App Security, les étiquettes de classification sont également recherchées dans tous les nouveaux fichiers ajoutés à Office 365.

## <a name="how-to-integrate-azure-information-protection-with-cloud-app-security"></a>Comment intégrer Azure Information Protection à Cloud App Security
  
### <a name="enable-azure-information-protection"></a>Activer Azure Information Protection

Voici tout ce que vous avez à faire pour intégrer Azure Information Protection à Cloud App Security : activer l’analyse automatique pour permettre la recherche des étiquettes de classification Azure Information Protection sur vos fichiers Office 365 sans avoir à créer une stratégie. Après avoir activé cette option, si des fichiers de votre environnement cloud sont étiquetés avec des étiquettes de classification Azure Information Protection, vous les voyez dans Cloud App Security.

Pour permettre à Cloud App Security d’analyser des fichiers quand l’inspection du contenu est activée pour les étiquettes de classification :

1. Dans Cloud App Security, sous l’icône de roue dentée des paramètres, sélectionnez la page **Paramètres généraux**.
2. Sous Azure Information Protection, sélectionnez **Détecter automatiquement les étiquettes de classification Azure Information Protection dans les fichiers**. 

Après avoir activé Azure Information Protection, vous pouvez voir les fichiers qui ont des étiquettes de classification et les filtrer par étiquette dans Cloud App Security.

 ![activer azure information protection](./media/enable-azip.png)

> [!NOTE] 
> L’analyse automatique ne retraite les fichiers existants que s’ils sont modifiés. Si vous voulez analyser les fichiers existants pour les étiquettes de classification Azure Information Protection, vous devez avoir au moins une **stratégie Fichier d’inspection de contenu**. Si vous n’en avez aucune, créez une **stratégie Fichier**, supprimez tous les filtres prédéfinis et sélectionnez l’option **Inspection de contenu**. Ensuite, sous **Inspection de contenu**, cliquez sur **Inclure les fichiers qui correspondent à une expression prédéfinie**, sélectionnez une valeur prédéfinie et enregistrez la stratégie. Cette opération permet d’activer l’inspection de contenu qui détectera automatiquement les étiquettes de classification Azure Information Protection.

### <a name="set-internal-and-external-tags"></a>Définir des étiquettes internes et externes
Par défaut, Cloud App Security analyse les étiquettes de classification qui ont été définies dans votre organisation, ainsi que les étiquettes externes qui ont été définies par d’autres organisations. 

Pour les ignorer l’ensemble des étiquettes de classification externes à votre organisation, dans le portail Cloud App Security, sous **Paramètres généraux**, sous **Paramètres de sécurité Azure**, sélectionnez **Ignorer les étiquettes de classification Azure Information Protection des autres locataires**.
 
![ignorer les étiquettes](./media/azip-ignore.png)

### <a name="control-file-exposure"></a>Contrôler l’exposition des fichiers
- Si ceci est le document que vous avez étiqueté avec une étiquette de classification Azure Information Protection :

![exemple d’écran azip](./media/azip-screen.png)

- Vous pouvez voir ce fichier dans Cloud App Security, dans la page **Fichiers**, en filtrant sur l’étiquette de classification :

![cas comparé à azip](./media/cas-compared-azip.png)

- Vous pouvez obtenir plus d’informations sur ces fichiers et leurs étiquettes de classification dans le tiroir des fichiers.

- Dans la page **Fichiers**, cliquez sur le fichier approprié pour voir s’il a des étiquettes de classification :

![tiroir du fichier](./media/azip-file-drawer.png)

- Vous pouvez cliquer sur l’étiquette de classification pour afficher plus d’informations ou pour voir la liste complète des étiquettes de classification :
 
![liste de balises](./media/azip-tags-list.png)

- Vous pouvez ensuite créer des stratégies de fichiers dans Cloud App Security pour contrôler les fichiers qui sont partagés de façon inappropriée, et pour rechercher les fichiers étiquetés qui ont été modifiés récemment.
- En outre, vous pouvez déclencher des alertes sur des activités liées à des fichiers classifiés.

![balises azure information protection dans cloud app security](./media/azip-tags-in-cas.png)

> [!Note]
> Quand les étiquettes Azure Identity Protection sont désactivées sur un fichier, elles apparaissent désactivées dans Cloud App Security. Les étiquettes supprimées ne sont pas affichées.


**Stratégie n°1 - données confidentielles partagées en externe sur Box :**

1.  Créez une stratégie de fichier.
2.  Définissez le nom, la gravité et la catégorie de la stratégie.
3.  Ajoutez les filtres suivants pour rechercher toutes les données confidentielles qui sont partagées en externe sur Box :

![stratégie confidentialité](./media/azip-confidentiality-policy.png) 

**Stratégie n°2 : données restreintes qui ont été modifiées récemment en dehors du dossier Finance sur SharePoint :**

1.  Créez une stratégie de fichier.
2.  Définissez le nom, la gravité et la catégorie de la stratégie.
3.  Ajoutez les filtres suivants pour rechercher toutes les données restreintes qui ont été modifiées récemment et ajouter le dossier Finance dans l’option de sélection de dossier : 
 
![stratégie données restreintes](./media/azip-restricted-data-policy.png) 

Vous pouvez également définir des alertes ou une notification utilisateur ou encore prendre des mesures immédiates pour ces stratégies.
En savoir plus sur les [actions de gouvernance](governance-actions.md).

En savoir plus sur [Azure Information Protection](https://docs.microsoft.com/en-us/information-protection/understand-explore/what-is-information-protection) et suivre le [didacticiel de démarrage rapide](https://docs.microsoft.com/en-us/information-protection/get-started/infoprotect-quick-start-tutorial) pour Azure Information Protection.


## <a name="integration-with-azure-rights-management"></a>Intégration à Azure Rights Management

Votre organisation doit posséder une licence Azure Rights Management et l’avoir activée pour faciliter l’intégration entre Cloud App Security et Azure RMS.  Vous trouverez ces deux étapes distinctes dans [Activation d’Azure Rights Management](https://docs.microsoft.com/information-protection/deploy-use/activate-service).

Cloud App Security prend actuellement en charge la protection native des fichiers Office (2016 et supérieur). Les fichiers PDF et image seront disponibles dans les prochaines versions. 

Cette fonctionnalité est actuellement disponible pour les fichiers stockés dans SharePoint Online et OneDrive Entreprise. D’autres applications cloud seront prises en charge dans les prochaines versions.

Une fois Cloud App Security connecté à votre service Office 365, vous êtes en mesure d’utiliser les fonctionnalités d’intégration RMS de Cloud App Security. Ces dernières vous permettent de protéger vos documents avec RMS, directement dans le portail Cloud App Security, et ce, de la manière suivante :

1. À partir de la page **ichiers**, sélectionnez le fichier que vous souhaitez protéger, cliquez sur les trois points à la fin de la ligne du fichier, puis choisissez **Protéger**. 
![protéger l’application](./media/protect-app.png)
2. Vous êtes invité à choisir une étiquette de classification de votre organisation pour protéger le fichier. Cliquez ensuite sur **Protéger**. 
![étiquette de classification de protection](./media/protect-template.png)
3. Une fois que vous avez choisi une étiquette de classification et cliqué sur Protéger, Cloud App Security applique l’étiquette de classification et protège le fichier d’origine. T
> [!NOTE]
>   Nous vous recommandons d’appliquer aux fichiers les étiquettes de classification RMS dans toute l’entreprise, pour que tous les utilisateurs puissent accéder à ces fichiers, y compris le propriétaire d’origine du fichier. À partir du moment où le fichier est protégé, le propriétaire du fichier, la stratégie de partage du fichier et la liste des utilisateurs qui y ont déjà accès restent inchangés.

4. Si les utilisateurs souhaitent accéder au fichier protégé, leur appareil doit être équipé de l’application de partage RMS. Pour plus d’informations, voir l’article [Présentation technique de l’application de partage Microsoft Rights Management et détails sur la protection](https://docs.microsoft.com/information-protection/rms-client/sharing-app-admin-guide-technical).

5. Vous pouvez annuler cette action à tout moment dans le **journal de gouvernance**. Pour cela, cliquez sur le bouton **Rétablir** à la fin de la ligne de l’action Protéger précédemment entreprise. 


Pour plus d’informations sur l’interaction entre Cloud App Security et Azure Information Protection, consultez [Protéger les données contre les erreurs des utilisateurs](https://docs.microsoft.com/enterprise-mobility-security/solutions/protect-data-user-mistake).

 
## <a name="related-videos"></a>Vidéos connexes  
[Intégrations de Cloud App Security + Azure Information Protection](https://channel9.msdn.com/Shows/Microsoft-Security/MCAS--AIP-Integrations)  

## <a name="see-also"></a>Voir aussi  
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
