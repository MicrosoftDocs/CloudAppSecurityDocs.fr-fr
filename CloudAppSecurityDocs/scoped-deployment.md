---
title: Définir l’étendue d’un déploiement Microsoft Cloud App Security
description: Cet article donne des informations sur la marche à suivre pour définir l’étendue d’un déploiement Cloud App Security, en incluant et en excluant certains utilisateurs ou certains groupes.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: fe2ce27b-1020-45e9-ad72-fad93d197169
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: e3ca7c6bf16eec51f684e42c8964628ee5aa7ad0
ms.sourcegitcommit: 8ef0438fa35916c48625ff750cb85e9628d202f2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56281773"
---
# Déploiement étendu <a name="scoped-deployment"></a> 

*S’applique à : Microsoft Cloud App Security*

Microsoft Cloud App Security vous permet de délimiter votre déploiement. La délimitation vous permet de sélectionner certains groupes d’utilisateurs à surveiller pour des applications ou à exclure de la surveillance.

## <a name="include-or-exclude-user-groups"></a>Inclure ou exclure des groupes d’utilisateurs

Il est envisageable, dans certains cas, de ne pas utiliser Microsoft Cloud App Security pour tous les utilisateurs de l’organisation. La délimitation est particulièrement utile quand vous voulez limiter votre déploiement en raison de restrictions des licences. Une limitation peut aussi être nécessaire en raison de réglementations de conformité vous imposant de ne pas surveiller les utilisateurs de certains pays. Par exemple, utilisez des déploiements délimités pour surveiller seulement les employés basés aux États-Unis. À l’inverse, vous pouvez éviter de montrer les activités pour vos utilisateurs basés en Allemagne.

- Pour définir l’étendue de votre déploiement, vous devez commencer par [importer les groupes d’utilisateurs](user-groups.md) dans Microsoft Cloud App Security. Par défaut, vous voyez les groupes suivants :
    - Groupe d’utilisateurs **Application** : un groupe intégré qui vous permet de voir les activités effectuées par les applications Office 365 et Azure AD.
    - Groupe **Utilisateurs externes** : tous les utilisateurs qui ne sont pas dans les [plages d’adresses IP](ip-tags.md) que vous définissez pour votre organisation.
- La définition d’une règle d’inclusion a pour effet d’exclure automatiquement tous les groupes qui ne font pas partie du groupe inclus. Par exemple, si vous définissez une règle pour inclure tous les membres des groupes « Bureaux USA », les groupes qui n’en font pas partie ne sont pas surveillés.
- Les groupes d’utilisateurs exclus écrasent les groupes d’utilisateurs inclus. Cela signifie que si vous incluez le groupe d’utilisateurs « Employés GB » mais que vous excluez « Marketing », les membres du service marketing au Royaume-Uni ne sont pas surveillés, alors qu’ils sont membres du groupe **Employés GB**.

1. Dans la barre de menus, cliquez sur l’engrenage représentant les paramètres, puis sélectionnez **Déploiement étendu**.  

    ![icône des paramètres](./media/settings-icon.png "icône des paramètres")

2. Pour délimiter votre déploiement en incluant ou en excluant des groupes spécifiques, vous devez d’abord [importer les groupes d’utilisateurs](user-groups.md) dans Microsoft Cloud App Security. 

3. Pour définir des groupes spécifiques à surveiller par Microsoft Cloud App Security, sous l’onglet **Inclure**, cliquez sur l’icône avec le signe Plus (+). 
    ![icône](./media/plus-icon.png)

4. Dans la boîte de dialogue **Créer une règle d’inclusion**, effectuez les étapes suivantes :

    1. Sous **Taper le nom de la règle**, donnez un nom descriptif à la règle.
    2. Sous **Sélectionner des groupes d’utilisateurs**, sélectionnez tous les groupes pour lesquels vous souhaitez effectuer un monitoring avec Cloud App Security.
    3. Indiquez si vous souhaitez appliquer cette règle à toutes les applications connectées, ou seulement à **Certaines applications**. Si vous sélectionnez **Certaines applications**, la règle n’affectera que le monitoring des applications sélectionnées. Par exemple, si vous sélectionnez le groupe **Utilisateurs de l’équipe IU** et **Box**, Cloud App Security surveille seulement l’activité Box pour les utilisateurs de votre groupe « Utilisateurs de l’équipe IU » et, pour toutes les autres applications, il surveille toutes les activités de tous les utilisateurs.
     
        ![règle d’inclusion](./media/include-rule.png)

5. Pour définir des groupes à exclure de la surveillance, sous l’onglet **Exclure**, cliquez sur l’icône Plus (+). 
    
   ![icône](./media/plus-icon.png)

6. Dans la boîte de dialogue **Créer une règle d’exclusion**, définissez les paramètres suivants :

    1. Sous **Taper le nom de la règle**, donnez un nom descriptif à la règle.
    Sous **Sélectionner des groupes d’utilisateurs**, sélectionnez tous les groupes qui ne doivent pas être surveillés par Cloud App Security.
    2. Indiquez si vous souhaitez appliquer cette règle à toutes les applications connectées, ou seulement à **Certaines applications**. Si vous sélectionnez **Certaines applications**, Cloud App Security ne cessera le monitoring du groupe sélectionné que pour les applications sélectionnées. Cela signifie que si vous sélectionnez le groupe **Utilisateurs de l’équipe IU** et **Active Directory**, Cloud App Security surveille toutes les activités des utilisateurs à l’exception des activités Active Directory effectuées par les utilisateurs de l’équipe IU.
    
       ![règle d’exclusion](./media/exclude-rule.png)

## <a name="example-results-for-include-and-exclude-rules"></a>Exemples de résultats pour des règles d’inclusion et d’exclusion

Les règles d’inclusion et d’exclusion créées fonctionnent conjointement pour définir l’étendue du monitoring global effectué par Microsoft Cloud App Security. Voici un exemple de règles d’inclusion et d’exclusion possibles, et le résultat final du monitoring effectué par Microsoft Cloud App Security une fois ces règles appliquées.

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

## <a name="next-steps"></a>Étapes suivantes  
[Configurer Cloud Discovery](set-up-cloud-discovery.md)   

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)  
  
  
