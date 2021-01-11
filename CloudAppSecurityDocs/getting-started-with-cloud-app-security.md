---
title: Déploiement de Cloud App Security
description: Ce guide de démarrage rapide décrit le processus de mise en route de Cloud App Security, qui permet d’utiliser les applications cloud, de les contrôler et d’obtenir des insights les concernant.
ms.date: 06/07/2020
ms.topic: quickstart
ms.openlocfilehash: f17608329facabe6f48ae20938c44f3e8ef1b05a
ms.sourcegitcommit: 16a65ab2c8ca778d0b3cfa97b847af4c812363b2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/03/2021
ms.locfileid: "97855536"
---
# <a name="quickstart-get-started-with-microsoft-cloud-app-security"></a>Démarrage rapide : Bien démarrer avec Microsoft Cloud App Security

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Ce guide de démarrage rapide présente la procédure de mise en route de Cloud App Security. Microsoft Cloud App Security vous permet de tirer parti des avantages des applications cloud tout en conservant le contrôle de vos ressources d’entreprise. Sa fonction est d’améliorer la visibilité de l’activité cloud et de contribuer à accroître la protection des données d’entreprise. Cet article présente la procédure à suivre pour configurer et utiliser Microsoft Cloud App Security.

Votre organisation doit disposer d’une licence permettant d’utiliser Cloud App Security. Pour plus d’informations sur les tarifs, consultez la [fiche technique sur les licences Cloud App Security](https://aka.ms/mcaslicensing).

>[!NOTE]
>Cloud App Security ne nécessite pas de licence Office 365.

## <a name="prerequisites"></a>Prérequis

- Votre organisation doit disposer d’une licence permettant d’utiliser Cloud App Security. Pour plus d’informations sur les tarifs, consultez la [fiche technique sur les licences Cloud App Security](https://aka.ms/mcaslicensing).

    Pour la prise en charge de l’activation du locataire, consultez [Comment contacter le support relatif aux produits d’entreprises - Aide de l’administrateur](https://support.office.com/article/Contact-Office-365-for-business-support-Admin-Help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b).
- Après avoir acquis une licence Cloud App Security, vous recevrez un e-mail contenant les informations d’activation et le lien du portail Cloud App Security.

- Pour configurer Cloud App Security, vous devez être un administrateur général, de mise en conformité ou de la sécurité dans Azure Active Directory ou Office 365. Il est important de comprendre qu’un utilisateur possédant un rôle d’administrateur aura les mêmes autorisations sur toutes les applications cloud auxquelles votre organisation s’est abonnée, que ce rôle ait été attribué dans le Centre d’administration Microsoft 365, sur le Portail Azure Classic ou à l’aide du module Azure AD pour [Windows PowerShell](/microsoft-365/enterprise/assign-roles-to-user-accounts-with-microsoft-365-powershell?view=o365-worldwide&preserve-view=true). Pour plus d’informations, consultez [Attribuer des rôles d’administrateur](https://support.office.com/article/Assigning-admin-roles-in-Office-365-eac4d046-1afd-4f1a-85fc-8219c79e1504) et [Attribution des rôles d’administrateur dans Azure Active Directory](/azure/active-directory/users-groups-roles/directory-assign-admin-roles).

- Pour exécuter le portail Cloud App Security, utilisez Internet Explorer 11, Microsoft Edge (dernière version), Google Chrome (dernière version), Mozilla Firefox (dernière version) ou Apple Safari (dernière version).

## <a name="to-access-the-portal"></a>Accès au portail

Pour accéder au portail Cloud App Security, suivez le lien [https://portal.cloudappsecurity.com](https://portal.cloudappsecurity.com). Vous pouvez également accéder au portail via le **[Centre d’administration Microsoft 365](https://security.microsoft.com)** de la façon suivante :

1. Dans le menu latéral du Centre d’administration Microsoft 365, cliquez sur **Tout afficher**, puis sélectionnez **Sécurité**.

    ![Accès à partir du centre d’administration Microsoft 365](media/access-from-o365.png)

1. Dans la page sécurité de Microsoft 365, cliquez sur **Plus de ressources**, puis sélectionnez **Cloud App Security**.

    ![Sélectionner Cloud App Security](media/access-from-o365-s2.png)

## <a name="step-1-set-instant-visibility-protection-and-governance-actions-for-your-apps"></a>Étape 1. [Définir une visibilité instantanée, une protection et des actions de gouvernance pour vos applications](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)

Tâche obligatoire : Connecter des applications

1. Dans la roue dentée des paramètres, sélectionnez **Connecteurs d’application**.
1. Cliquez sur le signe plus ( **+** ) pour ajouter une application et sélectionnez une application.
1. Suivez la procédure de configuration pour connecter l’application.

**Pourquoi connecter une application ?**
Une fois les applications de votre environnement cloud connectées, vous bénéficierez d’une meilleure visibilité et pourrez ainsi examiner les activités, les fichiers et les comptes associés.

## <a name="step-2-control-cloud-apps-with-policies"></a>Étape 2. [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

Tâche obligatoire : Créer des stratégies

### <a name="to-create-policies"></a>Création de stratégies

1. Accédez à **Contrôle** > **Modèles**.
1. Sélectionnez un modèle de stratégie dans la liste, puis choisissez (+) **Créer une stratégie**.
1. Personnalisez la stratégie (sélectionnez des filtres, des actions et d’autres paramètres), puis choisissez **Créer**.
1. Dans l’onglet **Stratégies**, choisissez la stratégie pour afficher les correspondances pertinentes (activités, fichiers, alertes).
 Conseil : Pour couvrir tous les scénarios de sécurité de votre environnement cloud, créez une stratégie pour chaque **catégorie de risque**.

### <a name="how-can-policies-help-your-organization"></a>Comment les stratégies peuvent-elles aider votre organisation ?

Vous pouvez utiliser des stratégies pour surveiller les tendances, voir les menaces de sécurité et générer des rapports et des alertes personnalisés. Elles permettent également de créer des actions de gouvernance et de définir des contrôles de protection contre la perte de données et de partage de fichiers.

## <a name="step-3-set-up-cloud-discovery"></a>Étape 3. [Configuration de Cloud Discovery](set-up-cloud-discovery.md)

Tâche obligatoire : Activer Cloud App Security pour voir l’utilisation de l’application cloud

1. [Effectuez une intégration à Microsoft Defender ATP](mde-integration.md) pour activer automatiquement Cloud App Security afin de superviser vos appareils Windows 10 à l’intérieur et à l’extérieur de votre entreprise.
1. Si vous utilisez [Zscaler](zscaler-integration.md), intégrez-le avec Cloud App Security.
1. Pour obtenir une couverture complète, créez un rapport Cloud Discovery continu :

    1. Dans la roue dentée Paramètres, sélectionnez **Paramètres de Cloud Discovery**.
    1. Choisissez **Chargement automatique des journaux**.
    1. Dans l’onglet **Sources de données**, ajoutez vos sources.
    1. Dans l’onglet **Collecteurs de journaux**, configurez le collecteur de journaux.

### <a name="to-create-a-snapshot-cloud-discovery-report"></a>Pour créer un rapport d’instantané Cloud Discovery

 Accédez à **Découvrir** > **Rapport d’instantané** et suivez la procédure indiquée.

### <a name="why-should-you-configure-cloud-discovery-reports"></a>Pourquoi configurer les rapports Cloud Discovery ?

Il est essentiel de bénéficier d’une visibilité sur l’informatique fantôme dans l’organisation.
Une fois vos journaux analysés, vous pourrez facilement identifier les applications cloud utilisées, les utilisateurs ainsi que les appareils dont ils se sont servis.

## <a name="step-4-personalize-your-experience"></a>Étape 4. [Personnaliser votre expérience](mail-settings.md)

Tâche recommandée : Ajouter les détails de l’organisation

### <a name="to-enter-email-settings"></a>Pour entrer les paramètres d’e-mail

1. Dans la roue dentée des paramètres, sélectionnez **Paramètres de courrier**.
1. Sous **Identité de l’expéditeur des e-mails**, entrez vos adresses e-mail et votre nom complet.
1. Sous **Conception des e-mails**, téléchargez le modèle d’e-mail de votre organisation.

### <a name="to-set-admin-notifications"></a>Pour définir des notifications d’administrateur

1. Dans la barre de navigation, choisissez votre nom d’utilisateur, puis accédez à **Paramètres utilisateur**.
1. Sous **Notifications**, configurez les méthodes que vous souhaitez définir pour les notifications système.
1. Choisissez **Enregistrer**.

### <a name="to-customize-the-score-metrics"></a>Pour personnaliser les métriques de score

1. Dans la roue dentée Paramètres, sélectionnez **Paramètres de Cloud Discovery**.
1. Dans la roue dentée Paramètres, sélectionnez **Paramètres de Cloud Discovery**.
1. Sous **Métriques de score**, configurez l’importance des différentes valeurs de risque.
1. Choisissez **Enregistrer**.

Les scores de risque attribués aux applications découvertes sont maintenant configurés précisément selon les besoins et les priorités de votre organisation.

### <a name="why-personalize-your-environment"></a>Pourquoi personnaliser votre environnement ?

Certaines fonctionnalités fonctionnent mieux quand elles sont adaptées à vos besoins.
Offrez une meilleure expérience utilisateur avec vos propres modèles d’e-mail. Choisissez les notifications à recevoir, et personnalisez votre métrique de score de risque selon les préférences de votre organisation.

## <a name="step-5-organize-the-data-according-to-your-needs"></a>Étape 5. [Organiser les données selon vos besoins](ip-tags.md)

Tâche recommandée : Configurer les paramètres importants

### <a name="to-create-ip-address-tags"></a>Pour créer des étiquettes d’adresse IP

1. Dans la roue dentée Paramètres, sélectionnez **Paramètres de Cloud Discovery**.
1. Dans la roue dentée des paramètres, sélectionnez **Plages d’adresses IP**.
1. Cliquez sur le signe plus ( **+** ) pour ajouter une plage d’adresses IP.
1. Entrez les **détails**, **l’emplacement**, les **étiquettes** et la **catégorie** de la plage d’adresses IP.
1. Choisissez **Créer**.

    Vous pouvez maintenant utiliser des balises IP lorsque vous créez des stratégies, et quand vous filtrez et créez des rapports continus.

### <a name="to-create-continuous-reports"></a>Pour créer des rapports continus

1. Dans la roue dentée Paramètres, sélectionnez **Paramètres de Cloud Discovery**.
1. Sous **Rapports continus**, choisissez **Créer un rapport**.
1. Suivez la procédure de configuration.
1. Choisissez **Créer**.

Vous pouvez maintenant afficher les données découvertes en fonction de vos propres préférences (par exemple, divisions ou plages d’adresses IP).

### <a name="to-add-domains"></a>Pour ajouter des domaines

1. Dans la roue dentée des paramètres, sélectionnez **Paramètres**.
1. Sous **Informations sur l’organisation**, ajoutez les domaines internes de votre organisation.
1. Choisissez **Enregistrer**.

### <a name="why-should-you-configure-these-settings"></a>Pourquoi devez-vous configurer ces paramètres ?

Ces paramètres permettent de mieux contrôler les fonctionnalités de la console. Avec les balises IP, il est plus facile de créer des stratégies qui répondent à vos besoins, de filtrer avec précision les données, etc. Utilisez les Vues de données pour grouper vos données dans différentes catégories logiques.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôle des applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)].
