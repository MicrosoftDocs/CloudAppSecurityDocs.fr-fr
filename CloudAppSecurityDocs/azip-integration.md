---
title: "Intégration d’Azure Information Protection | Documentation Microsoft"
description: "Cet article fournit des informations sur la façon de tirer parti de vos balises Azure Information Protection dans Cloud App Security afin de renforcer le contrôle de l’utilisation des applications cloud de votre organisation."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/23/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 8168319a-199f-4e6c-ad68-e0f236480803
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eceb326c4ab14852ecd284cfbaa0d2eb07149168
ms.openlocfilehash: bf3b2c9fcd374ee9a980d123890b9c78f6fb9e07


---

# <a name="azure-information-protection-integration"></a>Intégration d’Azure Information Protection

Cloud App Security vous permet d’examiner des fichiers et de définir des stratégies en fonction des étiquettes de fichiers Azure Information Protection pour une plus grande visibilité et un contrôle accru de vos données sensibles dans le cloud. Pour cela, dans Cloud App Security, vous devez définir une stratégie qui analyse les fichiers lorsque l’inspection du contenu est activée. En outre, vous pouvez déclencher des alertes sur des activités liées à des fichiers classifiés. Avec l’intégration d’Azure Information Protection, vous pouvez :
-   quantifier l’exposition des données sensibles dans vos applications cloud ;
-   créer des stratégies et déclencher des alertes en cas de téléchargement de données classifiées dans vos applications cloud connectées ou mettre en quarantaine/empêcher le partage en externe des données sensibles ;
-   examiner les pistes d’audit et corriger les fichiers qui vont à l’encontre de vos stratégies. 

> [!NOTE] 
> Par défaut, les étiquettes sont détectées dans les fichiers uniquement s’il existe une stratégie de fichier qui analyse les fichiers lorsque l’inspection du contenu est activée. Pour détecter les étiquettes dans tous les fichiers sans stratégie de fichier, activez l’analyse automatique.

## <a name="terminology-overview"></a>Vue d’ensemble de la terminologie
-   Étiquette de classification Azure Information Protection : attribut qui est ajouté aux fichiers dans votre organisation soit automatiquement sur la base d’une stratégie, soit manuellement par les utilisateurs finaux.
-   Externe : balise définie par une personne externe à votre organisation.
-   Balise de fichier : présentation de l’étiquette de classification dans Cloud App Security. Ce champ est affiché pour chaque fichier de la table de fichiers et peut être utilisé dans les filtres.
-   Stratégie de fichier : ensemble de règles reposant sur des filtres de fichiers qui vous permet d’appliquer une large gamme de processus automatisés tirant parti des API du fournisseur du cloud.

## <a name="license-and-tenant-creation"></a>Licence et création du client
Pour activer cette fonctionnalité, vous avez besoin d’une licence Cloud App Security et d’une licence pour Azure Information Protection Premium P1 ou P2. Dès que ces deux licences sont en place, Cloud App Security synchronise les étiquettes des organisations à partir du service Azure Information Protection :

![exemple d’écran azip](./media/azip-screen.png)

![cas comparé à azip](./media/cas-compared-azip.png)
     
En outre, par défaut, les fichiers qui subissent une inspection du contenu par une ou plusieurs stratégies de fichier sont également analysés afin de détecter les étiquettes de classification.

## <a name="gain-visibility"></a>Gain de visibilité

Les balises de fichier détectées dans chaque fichier sont visibles dans le tiroir du fichier.
Dans la page **Fichiers**, cliquez sur le fichier approprié afin de voir s’il contient des balises de fichier :

![tiroir du fichier](./media/azip-file-drawer.png)

Vous pouvez cliquer sur les balises pour afficher plus d’informations ou pour voir la liste complète des balises :
 
![liste de balises](./media/azip-tags-list.png)

Utilisez le filtre **Balises de fichier** pour rechercher les fichiers qui ont été marqués avec une balise spécifique :
 
![filtre des balises de fichier](./media/azip-file-tags-filter.png)

Ou, pour rechercher les fichiers qui ont été marqués avec n’importe quelle balise de fichier :

![filtres toutes les balises de fichier](./media/azip-file-tags-all-filter.png)

## <a name="how-it-works"></a>Fonctionnement
Dès que vous connectez Cloud App Security à Azure Information Protection, Cloud App Security analyse les fichiers comme suit :
1. Récupère la liste de toutes les étiquettes de classification utilisées dans votre client. Cette opération est effectuée toutes les heures pour maintenir la liste à jour.
2. Analyse les fichiers à la recherche d’étiquettes de classification. Cela peut se produire de deux manières : a. Les fichiers dont le contenu est analysé dans le cadre d’une stratégie de fichier sont également ajoutés à la file d’attente d’analyse pour rechercher des étiquettes de classification.
    b. Pour ajouter tous vos fichiers à la file d’attente d’analyse sans avoir besoin de définir une stratégie de fichier, activez l’analyse automatique pour analyser les nouveaux fichiers ou les fichiers modifiés (voir ci-dessous).
3. Les étiquettes externes ne sont ajoutées à la liste des étiquettes de classification que si elles sont visibles sur un fichier spécifique, sauf si vous cochez la case **Ignorer les étiquettes de classification Azure Information Protection d’autres clients** (voir ci-dessous).

## <a name="enable-automatic-scan"></a>Activer l’analyse automatique
Pour activer l’analyse automatique en vue de détecter les balises de fichier pour les nouveaux fichiers dans Office 365 :

1. Dans Office 365, accédez à la page **Paramètres généraux**.
2. Sous Paramètres de sécurité Azure, sélectionnez **Détecter automatiquement les étiquettes de classification Azure Information Protection dans les fichiers**. Par la suite, tous les nouveaux fichiers ajoutés à Office 365 (et pas seulement ceux dont le contenu est analysé par une stratégie de fichier) sont analysés pour détecter les balises de fichier.

![activer azure information protection](./media/enable-azip.png)
 

## <a name="internal-and-external-tags"></a>Étiquettes internes et externes
Par défaut, Cloud App Security analyse les étiquettes de classification qui ont été définies dans votre organisation, ainsi que les étiquettes externes qui ont été définies par d’autres organisations. 

Pour les ignorer, sous **Paramètres de sécurité Azure**, sélectionnez **Ignorer les étiquettes de classification Azure Information Protection des autres clients**.
 
![ignorer les étiquettes](./media/azip-ignore.png)

> [!Note]
> Si vous travaillez dans un client de test, vous ne souhaiterez probablement pas ignorer les étiquettes de classification externes afin de pouvoir tester les fichiers que vous recevez d’autres clients.

![balises azure information protection dans cloud app security](./media/azip-tags-in-cas.png)

## <a name="use-azure-information-protection-tags-to-apply-control"></a>Utiliser les balises Azure Information Protection pour appliquer un contrôle
Créez des stratégies de fichier dans Cloud App Security afin de rechercher les fichiers qui sont partagés de façon inappropriée et rechercher les fichiers qui portent une étiquette et qui ont été récemment modifiés. 

**Stratégie n°1 - données confidentielles partagées en externe sur Box :**

1.  Créez une stratégie de fichier.
2.  Définissez le nom, la gravité et la catégorie de la stratégie.
3.  Ajoutez les filtres suivants pour rechercher toutes les données confidentielles qui sont partagées en externe sur Box :

![stratégie confidentialité](./media/azip-confidentiality-policy.png) 

**Stratégie n°2 : données restreintes qui ont été modifiées récemment en dehors du dossier Finance sur SharePoint :**

1.  Créez une stratégie de fichier.
2.  Définissez le nom, la gravité et la catégorie de la stratégie.
3.  Ajoutez les filtres suivants pour rechercher toutes les données restreintes qui ont été modifiées récemment et ajouter le dossier Finance dans l’option de sélection de dossier : 
 
![stratégie données restreintes](./media/azip-restricted-data-policy.png) 

Vous pouvez également définir des alertes ou une notification utilisateur ou encore prendre des mesures immédiates pour ces stratégies.
En savoir plus sur les [actions de gouvernance](governance-actions.md).

En savoir plus sur [Azure Information Protection](https://docs.microsoft.com/en-us/information-protection/understand-explore/what-is-information-protection) et suivre le [didacticiel de démarrage rapide](https://docs.microsoft.com/en-us/information-protection/get-started/infoprotect-quick-start-tutorial) pour Azure Information Protection.

  

## <a name="see-also"></a>Voir aussi  
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  



<!--HONumber=Nov16_HO5-->


