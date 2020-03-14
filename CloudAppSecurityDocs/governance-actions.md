---
title: Actions de gouvernance pour contrôler les applications connectées-Cloud App Security | Microsoft Docs
description: Cet article répertorie et décrit toutes les actions de gouvernance qui peuvent être effectuées dans Cloud App Security et les messages de journal qui les suivent.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/03/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 5ae82c1acddf3bbf1ee711a108234d6b69cd8ee4
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285333"
---
# <a name="governing-connected-apps"></a>Gouvernance des applications connectées

*S’applique à : Microsoft Cloud App Security*

La gouvernance vous permet de contrôler en temps réel les actions des utilisateurs dans les applications. Pour les applications connectées, vous pouvez appliquer des actions de gouvernance aux fichiers ou aux activités. Les actions de gouvernance sont des actions intégrées que vous pouvez exécuter sur des fichiers ou des activités directement à partir de Microsoft Cloud App Security. Les actions de gouvernance contrôlent ce que les utilisateurs font, en temps réel, entre les applications connectées.

> [!NOTE]
> Lorsque Microsoft Cloud App Security tente d’exécuter une action de gouvernance sur un fichier, mais échoue parce que le fichier est verrouillé, il retente automatiquement l’action de gouvernance.

## <a name="file-governance-actions"></a>Actions de gouvernance sur des fichiers

Vous pouvez effectuer les actions de gouvernance suivantes sur un fichier ou un utilisateur spécifique, ou à partir d’une stratégie donnée.

- **Fonctionnalité**

  - **Alertes** : les alertes peuvent être déclenchées dans le système et propagées par courrier électronique et par message texte, en fonction du niveau de gravité.

  - **Notification par e-mail** de l’utilisateur : les e-mails peuvent être personnalisés et envoyés à tous les propriétaires de fichiers en violation.

  - **Notifier des utilisateurs spécifiques** : liste spécifique d’adresses e-mail qui recevront ces notifications.

  - **Notifier le dernier éditeur de fichier** : envoie des notifications à la dernière personne qui a modifié le fichier.

- **Actions de gouvernance dans les applications** : les actions granulaires peuvent être appliquées par application, et les actions spécifiques varient selon la terminologie de l’application.

  - **L’étiquetage**
    - **Apply label** -capacité à ajouter une étiquette de classification Azure information protection.
    - **Supprimer l’étiquette** -possibilité de supprimer une étiquette de classification Azure information protection.
  - **Modifier le partage**

    - **Supprimer le partage public** : autoriser l’accès uniquement aux collaborateurs nommés, par exemple : supprimer l’accès public pour G suite et supprimer le lien partagé direct pour Box.

    - **Supprimer les utilisateurs externes** : autorisez l’accès uniquement aux utilisateurs de l’entreprise.

    - **Rendre privé** : seuls les administrateurs de site peuvent accéder au fichier, tous les partages sont supprimés.

    - **Supprimer un collaborateur** : supprimez un collaborateur spécifique du fichier.

    - **Réduire l’accès public** : définissez les fichiers disponibles publiquement pour qu’ils soient disponibles uniquement avec un lien partagé. Google

    - Faire **expirer le lien partagé** : capacité à définir une date de experation pour un lien partagé après laquelle il n’est plus actif. Boîte

    - **Modifier le niveau d’accès au lien de partage** -possibilité de modifier le niveau d’accès du lien partagé entre la société uniquement, les collaborateurs uniquement et le public. Boîte

  - **Quarantaine**

    - **Mettre en quarantaine utilisateur** : autoriser le libre-service en déplaçant le fichier vers un dossier de quarantaine contrôlé par l’utilisateur

    - **Mettre en quarantaine administrateur** : le fichier est déplacé vers la quarantaine dans le lecteur d’administration, et l’administrateur doit l’approuver.

  - **Hériter des autorisations du parent** : cette action de gouvernance vous permet de supprimer des autorisations spécifiques définies pour un fichier ou un dossier dans Office 365. Revenez ensuite aux autorisations définies pour le dossier parent.

  - **Corbeille** : déplacez le fichier vers le dossier Corbeille. (Box, Dropbox, Google Drive, OneDrive, SharePoint)

   ![alertes de policy_create](media/policy_create-alerts.png "alertes de policy_create")

## <a name="activity-governance-actions"></a>Actions de gouvernance des activités

- **Fonctionnalité**

  - **Alertes** : les alertes peuvent être déclenchées dans le système et propagées par courrier électronique et par message texte, en fonction du niveau de gravité.

  - **Notification par e-mail** de l’utilisateur : les e-mails peuvent être personnalisés et envoyés à tous les propriétaires de fichiers en violation.

  - **Notifier d’autres utilisateurs** : liste spécifique d’adresses e-mail qui recevront ces notifications.

- **Actions de gouvernance dans les applications** : les actions granulaires peuvent être appliquées par application, et les actions spécifiques varient selon la terminologie de l’application.

  - **Suspendre l’utilisateur** : suspendez l’utilisateur de l’application.
    > [!NOTE]
    > Si votre Azure Active Directory (Azure AD) est configurée pour se synchroniser automatiquement avec les utilisateurs de votre Active Directory environnement local, les paramètres de l’environnement local remplacent les paramètres de Azure AD et cette action de gouvernance est rétablie.

  - **Demander à l’utilisateur de se connecter à nouveau** : déconnecte l’utilisateur et demande à ce qu’il se reconnecte.

  - **Confirmer** que l’utilisateur est compromis-définir le niveau de risque de l’utilisateur sur élevé. Cela entraîne l’application des actions de stratégie appropriées définies dans Azure AD. Pour plus d’informations sur le fonctionnement de Azure AD avec les niveaux de risque, consultez [comment Azure ad utiliser mes commentaires](https://docs.microsoft.com/azure/active-directory/identity-protection/howto-identity-protection-risk-feedback#how-does-azure-ad-use-my-risk-feedback)sur les risques.

  ![Cloud App Security les actions de gouvernance des stratégies d’activité](media/activity-policy-ref6.png "Ref6 de stratégie d’activité")

## <a name="governance-conflicts"></a>Conflits de gouvernance

Si vous créez plusieurs stratégies, il peut arriver que les actions de gouvernance se chevauchent. Dans ce cas, Cloud App Security traite les actions de gouvernance comme suit :

### <a name="conflicts-between-policies"></a>Conflits de stratégies

- Si deux stratégies contiennent des actions qui sont contenues dans l’une et l’autre (par exemple, l’action **Supprimer des partages externes** est incluse dans **Rendre privé**), Cloud App Security résout le conflit et l’action la plus forte est appliquée.
- Si les actions ne sont pas liées (par exemple, **notifier le propriétaire** et **rendre privé**). les deux actions ont lieu.
- Si les actions sont en conflit (par exemple, **changer le propriétaire en utilisateur A** et **changer le propriétaire en utilisateur B**), différents résultats peuvent être obtenus à partir de chaque correspondance. Il est important de modifier vos stratégies pour éviter les conflits, car elles peuvent entraîner des modifications indésirables dans le lecteur qui seront difficiles à détecter.

### <a name="conflicts-in-user-sync"></a>Conflits de synchronisation d’utilisateur

- Si votre Azure AD est configurée pour se synchroniser automatiquement avec les utilisateurs de votre Active Directory environnement local, les paramètres de l’environnement local remplacent les paramètres de Azure AD et cette action de gouvernance est rétablie.

## <a name="governance-log"></a>Journal de gouvernance

Le journal de gouvernance fournit un enregistrement de l’état de chaque tâche que Cloud App Security doit exécuter, dont les tâches manuelles et automatiques. Ces tâches incluent celles que vous définissez dans les stratégies, les actions de gouvernance que vous définissez sur les fichiers et les utilisateurs, ainsi que toute autre action que vous définissez Cloud App Security à prendre. Le journal de gouvernance fournit également des informations sur la réussite ou l’échec de ces actions. Vous pouvez choisir de retenter ou de rétablir certaines des actions de gouvernance à partir du journal de gouvernance.

Le tableau suivant présente la liste complète des actions que le portail Cloud App Security vous permet de prendre. Ces actions sont activées à différents emplacements dans la console, comme décrit dans la colonne **emplacement** . Chaque action de gouvernance effectuée est répertoriée dans le journal de gouvernance.
Pour plus d’informations sur la façon dont les actions de gouvernance sont traitées en cas de conflits de stratégies, consultez [Conflits de stratégies](control-cloud-apps-with-policies.md).

| Location | Type d’objet cible | Action de gouvernance |Description| Connecteurs associés|
|-------------------|---------|-----|--------|-------|
|Accounts |Fichier |Supprimer les collaborations de l’utilisateur | Supprime toutes les collaborations d’un utilisateur spécifique pour tous les fichiers - utile lorsque des personnes quittent l’entreprise. |Box, G Suite|
|Accounts | Account | Réhabiliter l’utilisateur |Réhabilite l’utilisateur |G Suite, Box, Office, Salesforce|
|Accounts | Account |Paramètres de compte | Vous permet d’accéder à la page de paramètres de compte dans une application donnée (par exemple, dans Salesforce). | Toutes les applications. Les paramètres de One Drive et SharePoint sont configurés dans Office. |
|Accounts |Fichier |Transférer la possession de tous les fichiers | Dans un compte, vous transférez les fichiers d’un utilisateur vers un nouveau propriétaire que vous sélectionnez. Le propriétaire précédent devient un éditeur et ne peut plus modifier les paramètres de partage. Le nouveau propriétaire reçoit une notification du transfert de possession par e-mail. | G Suite|
|Comptes, Stratégie d’activité | Account | Suspendre l’utilisateur| Définit l’utilisateur pour qu’il n’ait aucun accès et aucune possibilité de se connecter. Si elles sont connectées lorsque vous définissez cette action, elles sont immédiatement verrouillées. |G Suite, Box, Office, Salesforce|
|Stratégie d’activité, Comptes | Account |Demander à l’utilisateur de se connecter à nouveau|Révoque tous les jetons d’actualisation et les problèmes de cookies de session aux applications par l’utilisateur. Cette action empêchera l’accès aux données de l’organisation et forcera l’utilisateur à se reconnecter à toutes les applications.| G suite, Office|
|Stratégie d’activité, Comptes | Account |Confirmer que l’utilisateur a été compromis|Définissez le niveau de risque de l’utilisateur sur élevé. Cela entraîne l’application des actions de stratégie appropriées définies dans Azure AD. | Office |
|Stratégie d’activité, Comptes | Account | Révoquer les privilèges administratifs |Révoque les privilèges d’un compte d’administrateur. Par exemple, la définition d’une stratégie d’activité qui révoque les privilèges d’administrateur après 10 échecs de tentative de connexion. | G Suite|
|Tableau de bord de l’application > Autorisations d’applications |Autorisations|Application Unban| Dans Google et Salesforce : supprimez l’exclusion de l’application et autorisez les utilisateurs à accorder des autorisations à l’application tierce avec Google ou Salesforce. Dans Office 365 : restaure les autorisations de l’application tierce à Office. |G Suite, Salesforce, Office |
|Tableau de bord de l’application > Autorisations d’applications |Autorisations| Désactiver les autorisations d’application | Révoquez les autorisations d’une application tierce à Google, Salesforce ou Office. Il s’agit d’une action unique qui se produit sur toutes les autorisations existantes, mais qui n’empêchera pas les futures connexions.|G Suite, Salesforce, Office |
|Tableau de bord de l’application > Autorisations d’applications |Autorisations| Activer les autorisations d’application |Accordez des autorisations d’application tierce à Google, Salesforce ou Office. Il s’agit d’une action unique qui se produit sur toutes les autorisations existantes, mais qui n’empêchera pas les futures connexions.|G Suite, Salesforce, Office |
|Tableau de bord de l’application > Autorisations d’applications |Autorisations| Exclure l’application | Dans Google et Salesforce : révoquent les autorisations d’accès d’une application tierce à Google ou Salesforce et lui interdisent de recevoir des autorisations dans le futur. Dans Office 365 : n’autorise pas l’autorisation des applications tierces à accéder à Office, mais ne les révoque pas. |G Suite, Salesforce, Office |
|Tableau de bord de l’application > Autorisations d’applications |Autorisations|Révoquer l’application|Révoque les autorisations d’accès d’une application tierce à Google, Salesforce ou Office. Il s’agit d’une action unique qui se produit sur toutes les autorisations existantes, mais qui n’empêchera pas les futures connexions. | G Suite, Salesforce|
|Tableau de bord de l’application > Autorisations d’applications | Account | Révoquer l’utilisateur de cette application|Vous pouvez révoquer des utilisateurs spécifiques en cliquant sur le nombre sous Utilisateurs. L’écran affiche les utilisateurs spécifiques et vous pouvez utiliser le X pour supprimer des autorisations pour tous les utilisateurs.| G Suite, Salesforce|
|Découverte > Applications découvertes/Adresses IP/Utilisateurs| Cloud Discovery | Exporter les données de découverte | Crée un fichier CSV à partir de données de découverte. | Découverte |
|Stratégie de fichier|Fichier |Mettre à la corbeille|Déplace le fichier dans la corbeille de l’utilisateur.| Box, Dropbox, Google Drive, OneDrive, SharePoint |
|Stratégie de fichier|Fichier | Notifier le dernier éditeur du fichier |Envoie un e-mail pour notifier la dernière personne qui a modifié le fichier qu’il viole une stratégie. |G Suite, Box|
|Stratégie de fichier|Fichier |Notifier le propriétaire du fichier|Envoie un e-mail au propriétaire du fichier lorsqu’un fichier viole une stratégie. Dans Dropbox, si aucun propriétaire n’est associé à un fichier, la notification est envoyée à l’utilisateur spécifique que vous définissez. | Toutes les applications |
|Stratégie de fichier, Stratégie d’activité | Fichier, Activité | Notifier des utilisateurs spécifiques |Envoie un e-mail pour notifier des utilisateurs spécifiques qu’un fichier viole une stratégie.| Toutes les applications |
|Stratégie de fichier et Stratégie d’activité | Fichier, Activité |Notifier l’utilisateur|Envoie un e-mail aux utilisateurs pour les informer qu’une de leurs actions ou qu’un fichier qu’ils possèdent viole une stratégie. Vous pouvez ajouter une notification personnalisée lui indiquant la violation. |Tout |
|Stratégie de fichiers et fichiers|Fichier | Supprimer la capacité des éditeurs à partager|Dans Google Drive, les autorisations de l’éditeur par défaut d’un fichier permettent également le partage. Cette action de gouvernance restreint cette option et restreint le partage de fichiers au propriétaire.| G Suite|
|Stratégie de fichiers et fichiers|Fichier | [Mettre en quarantaine administrateur](use-case-admin-quarantine.md) |Supprime toutes les autorisations du fichier et déplace le fichier vers un dossier de quarantaine dans un emplacement pour l’administrateur. Cette action permet à l’administrateur de consulter le fichier et de le supprimer.| Office 365 SharePoint, OneDrive Entreprise, Box|
|Stratégie de fichiers et fichiers|Fichier | Appliquer l’étiquette de classification|Applique une étiquette de classification Azure Information Protection aux fichiers automatiquement en fonction des conditions définies dans la stratégie.| Box, un lecteur, G suite, SharePoint |
|Stratégie de fichiers et fichiers|Fichier | Supprimer l’étiquette de classification | Supprime automatiquement une étiquette de classification Azure Information Protection des fichiers en fonction des conditions définies dans la stratégie. Vous pouvez supprimer des étiquettes uniquement si elles n’incluent pas de protection, et si elles ont été appliquées à partir de Cloud App Security, et non les étiquettes appliquées directement dans Information Protection.| Box, un lecteur, G suite, SharePoint |
|Stratégie de fichier, Stratégie d’activité, Alertes | Application |Demander aux utilisateurs de se reconnecter| Vous pouvez demander aux utilisateurs de se reconnecter à toutes les applications Office 365 et Azure AD pour corriger de manière rapide et efficace les alertes d’activité suspecte de l’utilisateur et les comptes corrompus. La nouvelle gouvernance se trouve dans les paramètres de stratégie et les pages d’alerte, à côté de l’option Interrompre la synchronisation de l’utilisateur. | Office 365, Azure AD |
|Files |Fichier |Restaurer des fichiers mis en quarantaine utilisateur |Restaure un utilisateur mis en quarantaine. |Box |
|Files |Fichier | M’auto-attribuer des permissions de lecture| Vous accorde des permissions de lecture pour le fichier afin de vous permettre d’y accéder et de déterminer s’il y a eu violation ou non.| G Suite|
|Files |Fichier | Autoriser les éditeurs à partager | Dans Google Drive, l’autorisation par défaut de l’éditeur d’un fichier permet également le partage. Cette action de gouvernance est l’opposé de Supprimer la capacité des éditeurs à partager et permet à l’éditeur de partager le fichier. | G Suite|
|Files |Fichier | Protéger | Protégez un fichier avec Azure Information Protection en appliquant un modèle d’organisation. | Office 365 (SharePoint et OneDrive) |
|Files |Fichier | Révoquer les permissions de lecture pour moi-même | Révoque les permissions de lecture pour le fichier pour vous-même. Cette option est utile lorsque vous vous êtes attribué des permissions pour examiner si un fichier comprend une violation ou non.| G Suite|
|Fichiers, Stratégie de fichier|Fichier | Transférer la possession de fichier | Modifie le propriétaire (vous choisissez un propriétaire spécifique dans la stratégie). | G Suite|
|Fichiers, Stratégie de fichier|Fichier | Réduire l’accès public|Cette action vous permet de définir des fichiers accessibles au public afin qu’ils soient disponibles uniquement avec un lien partagé.| G Suite|
|Fichiers, Stratégie de fichier|Fichier | Supprimer un collaborateur | Supprime un collaborateur donné d’un fichier. | G Suite, Box, One Drive, SharePoint|
|Fichiers, Stratégie de fichier|Fichier | Rendre privé| Seuls les administrateurs de site peuvent accéder au fichier, tous les partages sont supprimés. | G Suite, One Drive, SharePoint |
|Fichiers, Stratégie de fichier|Fichier | Supprimer les utilisateurs externes | Supprime tous les collaborateurs externes - configurés comme internes dans les paramètres en dehors des domaines. |G Suite, Box, One Drive, SharePoint|
|Fichiers, Stratégie de fichier|Fichier |Attribuer une permission de lecture au domaine|Accorde une permission de lecture pour le fichier sur le domaine spécifié pour tout votre domaine ou un domaine spécifique. Cette action est utile si vous souhaitez supprimer l’accès public après avoir accordé l’accès au domaine des personnes qui doivent travailler dessus.| G Suite|
|Fichiers, Stratégie de fichier|Fichier | Mettre en quarantaine utilisateur | Supprime toutes les autorisations du fichier et déplace le fichier vers un dossier de quarantaine sur le lecteur racine de l’utilisateur. Cette action permet à l’utilisateur de passer en revue le fichier et de le déplacer. S’il est déplacé manuellement, le partage de fichiers n’est pas restauré. | Box, One Drive, SharePoint |
|Files|Fichier|Faire expirer le lien partagé| Définissez une date d’expiration pour un lien partagé après laquelle il ne sera plus actif.|Box|
|Files|Fichier|Modifier le niveau d’accès au lien de partage|Modifie le niveau d’accès du lien partagé entre la société uniquement, les collaborateurs uniquement et le public.| Box|
|Fichiers, Stratégie de fichier|Fichier | Supprimer l’accès public| Si vous êtes un fichier et que vous le placez dans un accès public, il devient accessible à toute autre personne disposant d’un accès au fichier (en fonction du type d’accès du fichier). | G Suite|
|Fichiers, Stratégie de fichier|Fichier |Supprimer le lien partagé direct| Supprime un lien créé pour le fichier qui est public, mais partagé uniquement avec des personnes spécifiques.|Box |
|Paramètres> Paramètres de Cloud Discovery| Cloud Discovery | Recalculer les scores de Cloud Discovery |Recalcule les scores dans le catalogue d’applications cloud après une modification d’une mesure de score.| Découverte |
|Paramètres> Paramètres de Cloud Discovery > Gérer les vues de données| Cloud Discovery | Créer une vue de données de filtre Cloud Discovery|Crée une nouvelle vue de données pour une vue plus détaillée des résultats de découverte. Par exemple, des plages d’adresses IP spécifiques. | Découverte |
|Paramètres> Paramètres de Cloud Discovery > Supprimer les données| Cloud Discovery | Supprimer les données Cloud Discovery |Supprime toutes les données collectées à partir de sources de découverte.| Découverte |
|Paramètres> Paramètres de Cloud Discovery > Charger les journaux manuellement/Charger les journaux automatiquement | Cloud Discovery | Analyser les données Cloud Discovery| Notification que toutes les données de journal ont été analysées. | Découverte |

## <a name="next-steps"></a>Étapes suivantes :

> [!div class="nextstepaction"]
> [Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
