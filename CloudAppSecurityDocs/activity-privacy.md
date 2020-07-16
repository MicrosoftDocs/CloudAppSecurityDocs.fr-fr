---
title: Confidentialité de l’activité
description: Cet article fournit des informations sur la façon de configurer votre analyse d’activité pour qu’elle soit conforme à votre politique de confidentialité des utilisateurs.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 05/27/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 6de413cc6067ea43f5c2d677e421c09ffddcd94d
ms.sourcegitcommit: 3464ce8ed73d1bfaf02e4e78007766ea18350d9f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86402666"
---
# <a name="activity-privacy"></a>Confidentialité de l’activité

*S’applique à : Microsoft Cloud App Security*

Microsoft Cloud App Security offre aux entreprises la possibilité de déterminer de façon précise les utilisateurs qu’ils souhaitent surveiller en fonction de l’appartenance à un groupe. La confidentialité des activités ajoute la possibilité de suivre les réglementations de conformité de votre organisation sans compromettre la confidentialité des utilisateurs. Cela est possible en vous permettant de surveiller les utilisateurs tout en conservant leur confidentialité en masquant leurs activités dans le journal d’activité. Seuls les administrateurs autorisés ont la possibilité de choisir d’afficher ces activités privées, chaque instance étant auditée dans le journal de gouvernance.

## <a name="configure-activity-privacy-user-groups"></a>Configurer des groupes d’utilisateurs pour la confidentialité des activités

Vous pouvez avoir des utilisateurs dans Cloud App Security que vous souhaitez analyser, mais en raison des réglementations de conformité, vous devez limiter les personnes qui peuvent le faire. La confidentialité des activités vous permet de définir un groupe d’utilisateurs pour lequel les activités sont masquées par défaut.

Pour configurer vos groupes de confidentialité d’utilisateur, vous devez d’abord [importer des groupes d’utilisateurs](user-groups.md) vers Cloud App Security. Par défaut, vous voyez les groupes suivants :

- Groupe d’utilisateurs **Application** : un groupe intégré qui vous permet de voir les activités effectuées par les applications Office 365 et Azure AD.

- Groupe d' **utilisateurs externes** -tous les utilisateurs qui ne sont pas membres de l’un des domaines gérés que vous avez configurés pour votre organisation.

1. Dans la barre de menus, cliquez sur les paramètres roue dentée et sélectionnez **déploiement étendu et confidentialité**.

    ![Icône des paramètres](media/settings-icon.png)

1. Pour définir des groupes spécifiques qui doivent être analysés par Cloud App Security, dans l’onglet confidentialité de l' **activité** , cliquez sur l’icône plus.
    ![icon](media/plus-icon.png)

1. Dans la boîte de dialogue **Ajouter des groupes d’utilisateurs** , sous sélectionner des groupes d' **utilisateurs**, sélectionnez tous les groupes que vous souhaitez rendre privés dans Cloud App Security, puis cliquez sur **Ajouter**.

    ![Capture d’écran montrant la boîte de dialogue Ajouter des groupes d’utilisateurs](media/activity-privacy-add-user-groups.png)

    > [!NOTE]
    > Une fois qu’un groupe d’utilisateurs est ajouté, toutes les activités effectuées par les utilisateurs du groupe sont rendues privées à partir de ce dernier. Les activités existantes ne sont pas affectées.

## <a name="assign-admins-permission-to-view-private-activities"></a>Autoriser les administrateurs à afficher les activités privées

1. Dans la barre de menus, cliquez sur les paramètres roue dentée et sélectionnez **gérer l’accès administrateur**.

    ![Icône des paramètres](media/settings-icon.png)

1. Pour accorder à des administrateurs spécifiques l’autorisation d’afficher les activités privées, sous l’onglet **autorisations de confidentialité** de l’activité, cliquez sur l’icône plus.
    ![icon](media/plus-icon.png)

1. Dans la boîte de dialogue **Ajouter une autorisation d’administrateur** , entrez l’adresse de messagerie ou l’UPN de l’administrateur, puis cliquez sur Ajouter une **autorisation**.

    ![Capture d’écran montrant la boîte de dialogue Ajouter une autorisation d’administrateur](media/activity-privacy-add-admin-permission.png)

    > [!NOTE]
    > Seuls les administrateurs peuvent se voir attribuer l’autorisation d’afficher les activités privées.

## <a name="viewing-private-activities"></a>Affichage des activités privées

Une fois qu’un administrateur a reçu l’autorisation appropriée pour afficher les activités privées, il a la possibilité de choisir d’afficher ces activités dans le journal d’activité.

### <a name="to-view-private-activities"></a>Pour afficher les activités privées

1. Dans la page **Journal d’activité** , à droite de la table activité, cliquez sur l’icône des paramètres, puis sélectionnez Afficher les **activités privées**.

    ![Capture d’écran montrant l’icône des paramètres du journal d’activité](media/activity-privacy-view-settings-icon.png)

1. Dans la boîte de dialogue **afficher les activités privées** , cliquez sur **OK** pour confirmer que vous comprenez que l’action est en cours d’audit. Une fois la confirmation effectuée, les activités privées sont affichées dans le journal d’activité et l’action est enregistrée dans le journal de gouvernance.

[!INCLUDE [Open support ticket](includes/support.md)]
