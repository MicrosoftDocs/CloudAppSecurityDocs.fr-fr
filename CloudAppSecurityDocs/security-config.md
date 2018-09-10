---
title: Obtenir des recommandations sur la configuration de la sécurité dans Cloud App Security | Microsoft Docs
description: Cet article fournit des informations sur l’obtention de recommandations sur la configuration de la sécurité dans Cloud App Security avec l’intégration d’Azure Security Center.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/1/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: c6d8f8af-867b-43ab-adee-f06520577fe7
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 95611b155930836b50d6ac0b7bc395555e12451a
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44143664"
---
*S’applique à : Microsoft Cloud App Security*


# <a name="security-configuration"></a>Configuration de la sécurité

Microsoft Cloud App Security vous offre une évaluation de la configuration de la sécurité de votre environnement Azure et fournit des recommandations sur la configuration et la gestion de la sécurité avec l’aide d’Azure Security Center. 

Pour utiliser cette fonctionnalité, vous devez avoir les autorisations appropriées dans Azure AD et dans le portail Azure.
 
Par défaut, le rôle d’administrateur général Azure AD ne vous donne pas accès aux abonnements Azure. C’est pourquoi vous devez élever vos autorisations afin de pouvoir accorder à d’autres utilisateurs et à vous-même l’accès aux abonnements Azure. 

> [!NOTE]
> Nous vous recommandons de désactiver l’élévation après avoir terminé la procédure suivante.

Pour obtenir des recommandations sur la configuration de la sécurité dans Microsoft Cloud App Security :

1. <a href="https://docs.microsoft.com/azure/security-center/security-center-management-groups" target="_blank">Gagnez en visibilité au niveau locataire dans Azure Security Center</a>. Ce processus vous permet d’accorder à vous-même et à tous les autres administrateurs Microsoft Cloud App Security auxquels vous souhaitez accorder l’accès à cette page le rôle de Lecteur pour tous les abonnements, d’attribuer le rôle au groupe d’administration racine dans Azure Security Center et d’élever votre administrateur général Azure AD pour lui donner accès aux abonnements Azure. 

   > [!NOTE]
   > L’article décrit la procédure permettant de devenir administrateur de la sécurité. Pour que cette intégration fonctionne, les autorisations minimales nécessaires sont Lecteur.

2. Veillez à ouvrir <a href="https://ms.portal.azure.com/#blade/Microsoft_Azure_Security/SecurityMenuBlade/0" target="_blank">Azure Security Center</a> pour que les changements entrent en vigueur.

3. Dans le portail Microsoft Cloud App Security, accédez à **Examiner**, puis à **Configuration de la sécurité**. 

   ![menu de configuration de la sécurité](./media/security-configuration-menu.png)

   > [!NOTE]
   > Microsoft Cloud App Security fournit des recommandations pour les 50 premiers abonnements uniquement.
   > Il peut prendre jusqu’à 15 minutes avant que vos changements prennent effet.

5. Vous pouvez filtrer les recommandations par type, par ressource et par abonnement. Vous pouvez aussi cliquer sur l’icône de configuration de la sécurité ![icône ASC](./media/asc-icon.png) afin d’ouvrir la recommandation dans Azure Security Center pour en savoir plus et approfondir la recommandation. <br></br><br></br>Pour plus d’informations sur l’implémentation des recommandations de sécurité, consultez [Gestion des recommandations de sécurité dans Azure Security Center](https://docs.microsoft.com/azure/security-center/security-center-recommendations).

 
   ![Configuration de la sécurité](./media/security-configuration1.png)

 

## <a name="see-also"></a>Voir aussi  
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
