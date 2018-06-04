---
title: Définir l’étendue d’un déploiement Microsoft Cloud App Security | Microsoft Docs
description: Cet article donne des informations sur la marche à suivre pour définir l’étendue d’un déploiement Cloud App Security, en incluant et en excluant certains utilisateurs ou certains groupes.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/30/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: fe2ce27b-1020-45e9-ad72-fad93d197169
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: d7148854286218172fdbeb7c9e651a49cb721980
ms.sourcegitcommit: af8fad9709171b200699ca1ed513e2831826ed7e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34568660"
---
*S’applique à : Microsoft Cloud App Security*


# Déploiement étendu <a name="scoped-deployment"></a> 

Microsoft Cloud App Security permet de définir l’étendue d’un déploiement afin de limiter le monitoring à certains groupes d’utilisateurs ou d’en exclure d’autres.

Il est envisageable, dans certains cas, de ne pas utiliser Microsoft Cloud App Security pour tous les utilisateurs de l’organisation. C’est particulièrement utile pour limiter le déploiement en raison de restrictions de licence ou parce que des réglementations de conformité interdisent le monitoring des utilisateurs de certains pays. Le déploiement étendu permet par exemple, de restreindre le monitoring aux employés résidant aux États-Unis ou bien d’éviter d’afficher des activités pour les utilisateurs allemands. 

- Pour définir l’étendue de votre déploiement, vous devez commencer par [importer les groupes d’utilisateurs](user-groups.md) dans Microsoft Cloud App Security. Par défaut apparaîtra le groupe d’utilisateurs **Application**, un groupe intégré qui permet de voir les activités effectuées par les applications Office 365 et Azure AD, et le groupe **Utilisateurs externes**, qui regroupe tous les utilisateurs ne figurant pas dans les [plages d’adresses IP](ip-tags.md) que vous avez définies pour votre organisation.
- La définition d’une règle d’inclusion a pour effet d’exclure automatiquement tous les groupes qui ne font pas partie du groupe inclus. Par exemple, si vous définissez une règle qui inclut tous les membres des groupes US-office, les groupes qui n’en font pas partie ne feront pas l’objet d’un monitoring.
- Les groupes d’utilisateurs exclus écrasent les groupes d’utilisateurs inclus. Par exemple, si vous incluez le groupe d’utilisateurs « UK-employees » (« Employés du Royaume-Uni ») mais excluez « Marketing », les membres du service marketing au Royaume-Uni ne feront pas l’objet d’un monitoring alors qu’ils sont membres du groupe **UK-employees**.

1. Dans la barre de menus, cliquez sur la roue dentée des paramètres ![icône des paramètres](./media/settings-icon.png "icône des paramètres") et sélectionnez **Déploiement étendu**.  

2. Pour pouvoir définir l’étendue de votre déploiement en incluant ou en excluant des groupes spécifiques, vous devez commencer par [importer les groupes d’utilisateurs](user-groups.md) dans Microsoft Cloud App Security. 

3. Pour définir les groupes qui devront faire l’objet d’un monitoring par Microsoft Cloud App Security, cliquez sur ![l’icône](./media/plus-icon.png) plus dans l’onglet **Inclure**. <br>Dans la boîte de dialogue **Créer une règle d’inclusion**, suivez les étapes ci-dessous :

    1. Sous **Taper le nom de la règle**, donnez un nom descriptif à la règle.
    2. Sous **Sélectionner des groupes d’utilisateurs**, sélectionnez tous les groupes pour lesquels vous souhaitez effectuer un monitoring avec Cloud App Security.
    3. Indiquez si vous souhaitez appliquer cette règle à toutes les applications connectées, ou seulement à **Certaines applications**. Si vous sélectionnez **Certaines applications**, la règle n’affectera que le monitoring des applications sélectionnées. Par exemple, si vous sélectionnez le groupe **UK-users** (« Utilisateurs du Royaume-Uni ») et **Box**, Cloud App Security n’effectuera un monitoring de l’activité Box que pour les utilisateurs du Royaume-Uni ; pour toutes les autres applications, toutes les activités de tous les utilisateurs feront l’objet d’un monitoring.
     
     ![règle d’inclusion](./media/include-rule.png)

4. Pour définir des groupes à exclure du monitoring, cliquez sur ![l’icône](./media/plus-icon.png) plus sous l’onglet **Exclure**. <br>Dans la boîte de dialogue **Créer une règle d’inclusion**, définissez les paramètres suivants :

    1. Sous **Taper le nom de la règle**, donnez un nom descriptif à la règle.
    Sous **Sélectionner des groupes d’utilisateurs**, sélectionnez tous les groupes pour lesquels vous ne souhaitez pas effectuer un monitoring avec Cloud App Security.
    2. Indiquez si vous souhaitez appliquer cette règle à toutes les applications connectées, ou seulement à **Certaines applications**. Si vous sélectionnez **Certaines applications**, Cloud App Security ne cessera le monitoring du groupe sélectionné que pour les applications sélectionnées. Par exemple, si vous sélectionnez le groupe **Germany-users** (« Utilisateurs d’Allemagne ») et **Active Directory**, Cloud App Security effectue le monitoring de toutes les activités des utilisateurs à l’exception des activités Active Directory effectuées par des utilisateurs en Allemagne.
    
    ![règle d’exclusion](./media/exclude-rule.png)

Les règles d’inclusion et d’exclusion créées fonctionnent conjointement pour définir l’étendue du monitoring global effectué par Microsoft Cloud App Security.

Voici un exemple de règles d’inclusion et d’exclusion possibles, et le résultat final du monitoring effectué par Microsoft Cloud App Security une fois ces règles appliquées.

Si l’on crée les règles suivantes :

- Exclure le groupe d’utilisateurs « Germany all users » (« Tous les utilisateurs d’Allemagne »)
- Pour le groupe d’utilisateurs « Global sales » (« Ventes à l’international »), inclure seulement les activités Office 365
- Pour le groupe d’utilisateurs « Sales managers » (« Directeurs commerciaux »), inclure seulement les activités Power BI
- Salesforce est connecté à Microsoft Cloud App Security et aucune règle n’est définie pour celui-ci

Les activités suivantes des utilisateurs font l’objet d’un monitoring :

|Utilisateur|Appartenance aux groupes|Activités faisant l’objet d’un monitoring|
|----|----|----|
|Adriana|Germany all users<br>Global sales<br>Sales managers|Aucune|
|Alain|Global sales|Office 365 et toutes les sous-applications à l’exception de Power BI|
|Cornel|Global sales<br>Sales managers|Office 365 et toutes les sous-applications|
|Raymond|Sales managers|Power BI uniquement|

> [!NOTE] 
> Les autres applications ne sont pas affectées par l’étendue de groupe dans ces règles.
> Dans l’exemple, pour Salesforce, toutes les activités sont surveillées sur tous les groupes d’utilisateurs.

  
    
## <a name="see-also"></a>Voir aussi  
[Configurer Cloud Discovery](set-up-cloud-discovery.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  