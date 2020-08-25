---
title: Cloud App Security Guide d’enquête sur les alertes de détection d’anomalie
description: Cet article explique comment analyser les Cloud App Security alertes de détection d’anomalies émises lorsque des attaques sont détectées contre votre organisation.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 06/08/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: itfalcon
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: f117092ebdae230eae473bf4bbfd2d53b05fa3eb
ms.sourcegitcommit: 29a8e66c665f51d831516924ae4d9d8047b39276
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88781376"
---
# <a name="how-to-investigate-anomaly-detection-alerts"></a>Comment examiner les alertes de détection d’anomalies

*S’applique à : Microsoft Cloud App Security*

Microsoft Cloud App Security fournit des détections et des alertes de sécurité pour les activités malveillantes. L’objectif de ce guide est de vous fournir des informations générales et pratiques sur chaque alerte, afin de faciliter vos investigations et vos tâches de correction. Ce guide contient des informations générales sur les conditions de déclenchement d’alertes. Toutefois, il est important de noter que dans la mesure où les détections d’anomalies ne sont pas déterministes par nature, elles ne sont déclenchées que lorsqu’il y a un comportement qui dévie de la norme. Enfin, certaines alertes peuvent être en préversion. consultez régulièrement la documentation officielle pour obtenir l’état des alertes mises à jour.

## <a name="mitre-attck"></a>MITRE ATT \& CK

Pour expliquer et faciliter le mappage de la relation entre Cloud App Security alertes et la matrice familière MITRE ATT \& CK, nous avons catégorisé les alertes en fonction de la mitre att \& CK correspondante. Grâce à cette référence supplémentaire, il est plus facile de comprendre la technique des attaques suspectes qui peut être utilisée lorsqu’une alerte Cloud App Security est déclenchée.

Ce guide fournit des informations sur l’examen et la correction des Cloud App Security les alertes dans les catégories suivantes.

> [!div class="checklist"]
>
> - [Accès initial](#initial-access-alerts)
> - [Exécution](#execution-alerts)
> - [Persistance](#persistence-alerts)
> - [Escalade de privilèges](#privilege-escalation-alerts)
> - [Accès aux informations d’identification](#credential-access-alerts)
> - [Collection](#collection-alerts)
> - [Exfiltration](#exfiltration-alerts)
> - [Impact](#impact-alerts)

## <a name="security-alert-classifications"></a>Classifications des alertes de sécurité

Après une investigation appropriée, toutes les alertes de Cloud App Security peuvent être classées comme l’un des types d’activité suivants :

- **Vrai positif (TP)**: alerte sur une activité malveillante confirmée.
- **Vrai positif sans gravité (B-TP)**: alerte signalant une activité suspecte, mais pas malveillante, comme un test de pénétration ou une autre action suspecte autorisée.
- **Faux positif (FP)**: alerte sur une activité non malveillante.

## <a name="general-investigation-steps"></a>Étapes générales de l’investigation

Vous devez suivre les instructions générales suivantes lorsque vous examinez un type d’alerte pour mieux comprendre la menace potentielle avant d’appliquer l’action recommandée.

- Examinez le [score de priorité d’investigation](tutorial-ueba.md#understand-the-investigation-priority-score) de l’utilisateur et comparez-le au reste de l’organisation. Cela vous permettra d’identifier les utilisateurs de votre organisation qui présentent le plus grand risque.
- Si vous identifiez un **TP**, passez en revue toutes les activités de l’utilisateur pour mieux comprendre l’impact.
- Examinez toutes les activités des utilisateurs pour d’autres indicateurs de compromission et explorez la source et l’étendue de l’impact. Par exemple, passez en revue les informations suivantes sur l’appareil utilisateur et comparez-les aux informations d’appareil connues :
  - Système d’exploitation et version
  - Navigateur et version
  - Adresse IP et emplacement

## <a name="initial-access-alerts"></a>Alertes d’accès initiales

Cette section décrit les alertes indiquant qu’un acteur malveillant peut tenter d’obtenir un point de départ dans votre organisation.

### <a name="activity-from-anonymous-ip-address"></a>Activité à partir d’une adresse IP anonyme

**Description**

Activité à partir d’une adresse IP qui a été identifiée comme adresse IP de proxy anonyme par Microsoft Threat Intelligence ou par votre organisation. Ces proxies peuvent être utilisés pour masquer l’adresse IP d’un appareil et peuvent être utilisés pour les activités malveillantes.

**TP**, **B-TP**ou **FP**?

Cette détection utilise un algorithme de Machine Learning qui réduit les incidents de type **« B-TP** », tels que les adresses IP mal identifiées qui sont largement utilisées par les utilisateurs de l’organisation.

1. **TP**: Si vous êtes en mesure de vérifier que l’activité a été effectuée à partir d’une adresse IP anonyme ou TDR.

    **Action recommandée**: suspendre l’utilisateur, marquer l’utilisateur comme compromis et réinitialiser son mot de passe.
1. **B-TP**: si un utilisateur est connu pour utiliser des adresses IP anonymes dans le cadre de ses tâches. Par exemple, lorsqu’un analyste de la sécurité effectue des tests de sécurité ou d’intrusion pour le compte de l’organisation.

    **Action recommandée**: ignorez l’alerte.

**Comprendre l’étendue de la violation**

- Passez en revue toutes les alertes et l’activité des utilisateurs pour obtenir des indicateurs supplémentaires de compromission. Par exemple, si l’alerte a été suivie d’une autre alerte suspecte, telle qu’un [téléchargement de fichiers inhabituel (par l’utilisateur)](#unusual-file-download-by-user) ou une alerte de [transfert de boîte de réception suspecte](#suspicious-inbox-forwarding) , qui indique souvent qu’une personne malveillante tente d’exfiltrer des données.

### <a name="activity-from-infrequent-country"></a>Activité à partir de pays peu fréquents

Activité à partir d’un pays ou d’une région qui peut indiquer une activité malveillante. Cette stratégie Profile votre environnement et déclenche des alertes lorsque l’activité est détectée à partir d’un emplacement qui n’a pas été récemment ou n’a jamais été visité par un utilisateur de l’organisation.

Par défaut, la stratégie est configurée pour inclure uniquement les activités de connexion réussies, mais peut être configurée de manière à inclure toutes les activités de connexion. La stratégie peut être étendue à un sous-ensemble d’utilisateurs ou peut exclure des utilisateurs connus pour se déplacer vers des emplacements distants.

**Période d’apprentissage**

La détection des emplacements anormaux nécessite une période d’apprentissage initiale de sept jours pendant laquelle les alertes ne sont pas déclenchées pour les nouveaux emplacements.

**TP**, **B-TP**ou **FP**?

1. **TP**: Si vous êtes en mesure de vérifier que l’activité n’a pas été effectuée par un utilisateur légitime.

    **Action recommandée**:
    1. Interrompez l’utilisateur, réinitialisez son mot de passe et identifiez le moment opportun pour réactiver le compte en toute sécurité.
    1. Facultatif : créer un manuel à l’aide de Power automate pour contacter les utilisateurs détectés comme se connectant à des emplacements peu fréquents, ainsi que leurs responsables, pour vérifier leur activité.
1. **B-TP**: si un utilisateur est connu pour être à cet emplacement. Par exemple, lorsqu’un utilisateur voyage fréquemment et se trouve actuellement dans l’emplacement spécifié.

    **Action recommandée**:
    1. Ignorez l’alerte et modifiez la stratégie pour exclure l’utilisateur.
    1. Créez un groupe d’utilisateurs pour les voyageurs fréquents, importez le groupe dans Cloud App Security et excluez les utilisateurs de cette alerte.
    1. Facultatif : créer un manuel à l’aide de Power automate pour contacter les utilisateurs détectés comme se connectant à des emplacements peu fréquents, ainsi que leurs responsables, pour vérifier leur activité.

**Comprendre l’étendue de la violation**

- Passez en revue les ressources qui ont été compromises, telles que les téléchargements de données potentiels.

### <a name="activity-from-suspicious-ip-addresses"></a>Activité à partir d'adresses IP suspectes

Activité à partir d’une adresse IP qui a été identifiée comme dangereuse par Microsoft Threat Intelligence ou par votre organisation. Ces adresses IP ont été identifiées comme étant impliquées dans des activités malveillantes, telles que la commande et le contrôle du botnet (C&C) et peuvent indiquer un compte compromis.

**TP**, **B-TP**ou **FP**?

1. **TP**: Si vous êtes en mesure de vérifier que l’activité n’a pas été effectuée par un utilisateur légitime.

    **Action recommandée**: suspendre l’utilisateur, marquer l’utilisateur comme compromis et réinitialiser son mot de passe.
1. **B-TP**: si un utilisateur est connu pour utiliser l’adresse IP dans le cadre de ses tâches. Par exemple, lorsqu’un analyste de la sécurité effectue des tests de sécurité ou d’intrusion pour le compte de l’organisation.

    **Action recommandée**: ignorez l’alerte.

**Comprendre l’étendue de la violation**

1. Examinez le journal d’activité et recherchez les activités à partir de la même adresse IP.
1. Passez en revue les ressources qui ont été compromises, telles que les téléchargements de données potentiels ou les modifications administratives.
1. Créez un groupe pour que les analystes de la sécurité déclenchent volontairement ces alertes et les excluent de la stratégie.

### <a name="impossible-travel"></a>Voyage impossible

Activité du même utilisateur dans différents emplacements au cours d’une période qui est plus petite que le temps de trajet attendu entre les deux emplacements. Cela peut indiquer une violation des informations d’identification. Toutefois, il est également possible que l’emplacement réel de l’utilisateur soit masqué, par exemple, à l’aide d’un VPN.

Pour améliorer la précision et l’alerte uniquement lorsqu’il existe une forte indication d’une violation, Cloud App Security établit une ligne de base pour chaque utilisateur de l’organisation et alerte uniquement en cas de détection d’un comportement inhabituel. La stratégie de voyage impossible peut être ajustée à vos besoins.

**Période d’apprentissage**

L’établissement du modèle d’activité d’un nouvel utilisateur nécessite une période d’apprentissage initiale de sept jours pendant laquelle les alertes ne sont pas déclenchées pour les nouveaux emplacements.

**TP**, **B-TP**ou **FP**?

Cette détection utilise un algorithme de Machine Learning qui ignore les conditions de **TP (B-TP** ) évidentes, par exemple lorsque les adresses IP des deux côtés du trajet sont considérées comme sûres, que le voyage est approuvé et exclu du déclenchement de la détection de voyage impossible. Par exemple, les deux côtés sont considérés comme sécurisés s’ils sont [marqués comme entreprise](ip-tags.md). Toutefois, si l’adresse IP d’un seul côté du trajet est considérée comme sécurisée, la détection est déclenchée normalement.

1. **TP**: Si vous êtes en mesure de vérifier que l’emplacement dans l’alerte de voyage impossible est improbable pour l’utilisateur.

    **Action recommandée**: suspendre l’utilisateur, marquer l’utilisateur comme compromis et réinitialiser son mot de passe.
1. **FP** (voyages utilisateur non détectés) : Si vous êtes en mesure de vérifier que l’utilisateur a récemment réussi à accéder à la destination indiquée dans l’alerte. Par exemple, si le téléphone d’un utilisateur en mode avion reste connecté à des services tels qu’Exchange Online sur votre réseau d’entreprise tout en se déplaçant vers un autre emplacement. Lorsque l’utilisateur arrive au nouvel emplacement, le téléphone se connecte à Exchange Online pour déclencher l’alerte de voyage impossible.

    **Action recommandée**: ignorez l’alerte.
1. **FP** (sans balise VPN) : Si vous êtes en mesure de vérifier que la plage d’adresses IP provient d’un VPN approuvé.

    **Action recommandée**: ignorez l’alerte et [Ajoutez la plage d’adresses IP du VPN](ip-tags.md#create-an-ip-address-range) à Cloud App Security puis utilisez-la pour baliser la plage d’adresses IP du VPN.

**Comprendre l’étendue de la violation**

1. Examinez le journal d’activité pour mieux comprendre les activités similaires dans le même emplacement et la même adresse IP.
1. Si vous constatez que l’utilisateur a effectué d’autres activités risquées, telles que le téléchargement d’un grand volume de fichiers à partir d’un nouvel emplacement, il s’agit d’une indication forte d’une possible compromission.
1. Ajoutez les plages d’adresses IP et du VPN d’entreprise.
1. Créez un manuel à l’aide de Power automate et contactez le responsable de l’utilisateur pour voir si l’utilisateur est en déplacement légitime.
1. Envisagez de créer une base de données voyageur connue jusqu’à la minute pour la création de rapports de voyages organisationnels et utilisez-la pour faire référence aux activités de déplacement.

### <a name="misleading-oauth-app-name"></a>Nom d’application OAuth trompeur

Le nom d’application OAuth trompeur identifie les applications avec des caractères, tels que des lettres étrangères, qui ressemblent à des lettres latines. Cela peut indiquer une tentative de déguisement d’une application malveillante en tant qu’application connue et approuvée afin que les attaquants puissent tromper les utilisateurs pour qu’ils téléchargent leur application malveillante.

**TP**, **B-TP**ou **FP**?

1. **TP**: Si vous êtes en mesure de vérifier que l’application a un nom trompeur.

    **Action recommandée**: passez en revue le niveau d’autorisation demandé par cette application et les utilisateurs qui ont accordé l’accès. En fonction de votre investigation, vous pouvez choisir d’interdire l’accès à cette application.

Pour interdire l’accès à l’application, dans la page **applications OAuth** , sur la ligne dans laquelle l’application que vous souhaitez interdire s’affiche, cliquez sur l’icône d’interdiction.
    - Vous pouvez choisir de signaler aux utilisateurs que l’application qu’ils ont installée et autorisée a été interdite. La notification signale aux utilisateurs que l’application sera désactivée et qu’ils n’auront pas accès à l’application connectée. Si vous ne souhaitez pas les en informer, désélectionnez **Avertir les utilisateurs qui ont accordé l’accès à cette application interdite** dans la boîte de dialogue.
    - Nous vous recommandons d’avertir les utilisateurs que leur application est sur le point d’être exclue.

1. **FP**: Si vous devez confirmer que l’application a un nom trompeur, mais qu’elle a une utilisation professionnelle légitime dans l’organisation.

    **Action recommandée**: ignorez l’alerte.

**Comprendre l’étendue de la violation**

- Suivez le didacticiel sur la façon d' [examiner les applications OAuth risquées](investigate-risky-oauth.md).

### <a name="misleading-publisher-name-for-an-oauth-app"></a>Nom du serveur de publication trompeur pour une application OAuth

Le nom de l’éditeur OAuth trompeur pour une application OAuth identifie les applications avec des caractères, tels que des lettres étrangères, qui ressemblent à des lettres latines. Cela peut indiquer une tentative de déguisement d’une application malveillante en tant qu’application connue et approuvée afin que les attaquants puissent tromper les utilisateurs pour qu’ils téléchargent leur application malveillante.

**TP**, **B-TP**ou **FP**?

1. **TP**: Si vous êtes en mesure de vérifier que l’application a un nom d’éditeur trompeur.

    **Action recommandée**: passez en revue le niveau d’autorisation demandé par cette application et les utilisateurs qui ont accordé l’accès. En fonction de votre investigation, vous pouvez choisir d’interdire l’accès à cette application.
1. **FP**: Si vous devez confirmer que l’application a un nom d’éditeur trompeur, mais qu’il s’agit d’un éditeur légitime.

    **Action recommandée**: ignorez l’alerte.

**Comprendre l’étendue de la violation**

1. Dans la page **applications OAuth** , cliquez sur l’application pour ouvrir le **tiroir**de l’application, puis cliquez sur **activité associée**. Cela ouvre la page **Journal d’activité** filtrée pour les activités effectuées par l’application. N’oubliez pas que certaines applications effectuent des activités qui sont enregistrées comme ayant été effectuées par un utilisateur. Ces activités sont automatiquement filtrées en dehors des résultats dans le journal d’activité. Pour plus d’informations sur l’utilisation du journal d’activité, consultez [Journal d’activité](activity-filters.md).
1. Si vous soupçonnez qu’une application est suspecte, nous vous recommandons d’examiner le nom et le serveur de publication de l’application dans différents magasins d’applications. Lorsque vous vérifiez les magasins d’applications, vous vous concentrez sur les types d’applications suivants :
    - Applications avec un faible nombre de téléchargements.
    - Applications avec une évaluation faible, un faible score ou de mauvais commentaires.
    - Applications avec un éditeur ou un site web suspect.
    - Applications qui n’ont pas été mises à jour récemment. Cela peut indiquer une application qui n’est plus prise en charge.
    - Applications avec des autorisations inadaptées. Cela peut indiquer qu’une application est à risque.
1. Si vous pensez toujours qu’une application est suspecte, vous pouvez rechercher le nom de l’application, l’éditeur et l’URL en ligne.

## <a name="execution-alerts"></a>Alertes d’exécution

Cette section décrit les alertes indiquant qu’un acteur malveillant peut tenter d’exécuter du code malveillant dans votre organisation.

### <a name="multiple-storage-deletion-activities"></a>Activités de suppression de plusieurs stockages

Activités dans une session unique indiquant qu’un utilisateur a effectué un nombre inhabituel de suppressions de bases de données ou de stockage cloud à partir de ressources telles que des objets BLOB Azure, des compartiments de AWS S3 ou des Cosmos DB par rapport à la ligne de base apprise. Cela peut indiquer une tentative de violation de votre organisation.

**Période d’apprentissage**

L’établissement du modèle d’activité d’un nouvel utilisateur nécessite une période d’apprentissage initiale de sept jours pendant laquelle les alertes ne sont pas déclenchées pour les nouveaux emplacements.

**TP**, **B-TP**ou **FP**?

1. **TP**: Si vous devez confirmer que les suppressions n’ont pas été autorisées.

    **Action recommandée**: suspendre l’utilisateur, réinitialiser son mot de passe et analyser tous les appareils à la recherche de menaces malveillantes. Examinez toutes les activités des utilisateurs pour d’autres indicateurs de compromission et explorez l’étendue de l’impact.
1. **FP**: si, après votre investigation, vous êtes en mesure de vérifier que l’administrateur a été autorisé à effectuer ces activités de suppression.

    **Action recommandée**: ignorez l’alerte.

**Comprendre l’étendue de la violation**

1. Contactez l’utilisateur et confirmez l’activité.
1. Examinez le journal d’activité pour rechercher d’autres indicateurs de compromission et Voir qui a apporté la modification.
1. Passez en revue les activités de cet utilisateur pour les modifications apportées à d’autres services.

### <a name="multiple-vm-creation-activities"></a>Activités de création de plusieurs machines virtuelles

Activités dans une session unique indiquant qu’un utilisateur a effectué un nombre inhabituel d’actions de création de machine virtuelle par rapport à la ligne de base apprise. Plusieurs créations de machines virtuelles sur une infrastructure cloud dépendante peuvent indiquer une tentative d’exécution d’opérations d’exploration de données de chiffrement à partir de votre organisation.

**Période d’apprentissage**

L’établissement du modèle d’activité d’un nouvel utilisateur nécessite une période d’apprentissage initiale de sept jours pendant laquelle les alertes ne sont pas déclenchées pour les nouveaux emplacements.

**TP**, **B-TP**ou **FP**?

Pour améliorer la précision et l’alerte uniquement lorsqu’il existe une indication forte d’une violation, cette détection établit une ligne de base sur chaque environnement de l’organisation afin de réduire les incidents de **B-TP** , par exemple un administrateur ayant légitimement créé plus de machines virtuelles que la ligne de base établie, et alerte uniquement lorsque le comportement inhabituel est détecté.

- **TP**: Si vous êtes en mesure de vérifier que les activités de création n’ont pas été effectuées par un utilisateur légitime.

    **Action recommandée**: suspendre l’utilisateur, réinitialiser son mot de passe et analyser tous les appareils à la recherche de menaces malveillantes. Examinez toutes les activités des utilisateurs pour d’autres indicateurs de compromission et explorez l’étendue de l’impact. En outre, contactez l’utilisateur, confirmez les actions légitimes, puis veillez à désactiver ou supprimer les machines virtuelles compromises.
- **B-TP**: si, après votre investigation, vous êtes en mesure de vérifier que l’administrateur a été autorisé à effectuer ces activités de création.

    **Action recommandée**: ignorez l’alerte.

**Comprendre l’étendue de la violation**

1. Examinez toutes les activités des utilisateurs pour d’autres indicateurs de compromission.
1. Passez en revue les ressources créées ou modifiées par l’utilisateur et vérifiez qu’elles sont conformes aux stratégies de votre organisation.

### <a name="suspicious-creation-activityfor-cloudregion-preview"></a>Activité de création suspecte pour la région du Cloud (version préliminaire)

Activités indiquant qu’un utilisateur a effectué une action de création de ressource inhabituelle dans une région AWS rare par rapport à la ligne de base apprise. La création de ressources dans des régions de Cloud inhabituelles peut indiquer une tentative d’exécution d’une activité malveillante telle que des opérations d’exploration de données de chiffrement à partir de votre organisation.

**Période d’apprentissage**

L’établissement du modèle d’activité d’un nouvel utilisateur nécessite une période d’apprentissage initiale de sept jours pendant laquelle les alertes ne sont pas déclenchées pour les nouveaux emplacements.

**TP**, **B-TP**ou **FP**?

Pour améliorer la précision et l’alerte uniquement lorsqu’il existe une indication forte d’une violation, cette détection établit une ligne de base sur chaque environnement de l’organisation afin de réduire les incidents de **B-TP** .

- **TP**: Si vous êtes en mesure de vérifier que les activités de création n’ont pas été effectuées par un utilisateur légitime.

    **Action recommandée**: suspendre l’utilisateur, réinitialiser son mot de passe et analyser tous les appareils à la recherche de menaces malveillantes. Examinez toutes les activités des utilisateurs pour d’autres indicateurs de compromission et explorez l’étendue de l’impact. En outre, contactez l’utilisateur, confirmez ses actions légitimes, puis veillez à désactiver ou supprimer les ressources cloud compromises.
- **B-TP**: si, après votre investigation, vous êtes en mesure de vérifier que l’administrateur a été autorisé à effectuer ces activités de création.

    **Action recommandée**: ignorez l’alerte.

**Comprendre l’étendue de la violation**

1. Examinez toutes les activités des utilisateurs pour d’autres indicateurs de compromission.
1. Passez en revue les ressources créées et vérifiez qu’elles sont conformes aux stratégies de votre organisation.

## <a name="persistence-alerts"></a>Alertes de persistance

Cette section décrit les alertes indiquant qu’un acteur malveillant peut tenter de conserver son point de vue dans votre organisation.

### <a name="activity-performed-by-terminated-user"></a>Activité effectuée par utilisateur résilié

L’activité effectuée par un utilisateur terminé peut indiquer qu’un employé terminé qui a toujours accès aux ressources de l’entreprise tente d’effectuer une activité malveillante. Cloud App Security Profile les utilisateurs de l’organisation et déclenche une alerte lorsqu’un utilisateur terminé effectue une activité.

**TP**, **B-TP**ou **FP**?

1. **TP**: Si vous êtes en mesure de vérifier que l’utilisateur terminé a toujours accès à certaines ressources de l’entreprise et exécute des activités.

    **Action recommandée**: désactiver l’utilisateur.
1. **B-TP**: Si vous êtes en mesure de déterminer que l’utilisateur a été temporairement désactivé ou a été supprimé puis réinscrit.

    **Action recommandée**: ignorez l’alerte.

**Comprendre l’étendue de la violation**

1. Référence croisée des enregistrements RH pour confirmer l’arrêt de l’utilisateur.
1. Validez l’existence du compte d’utilisateur Azure Active Directory (Azure AD).
    > [!NOTE]
    > Si vous utilisez Azure AD Connect, validez l’objet Active Directory local et confirmez un cycle de synchronisation réussi.
1. Identifiez toutes les applications auxquelles l’utilisateur terminé avait accès et désaffecter les comptes.
1. Mettez à jour les procédures de désaffectation.

### <a name="suspicious-change-of-cloudtrail-logging-service"></a>Modification suspecte du service de journalisation CloudTrail

Activités dans une session unique indiquant qu’un utilisateur a effectué des modifications suspectes dans le service de journalisation AWS CloudTrail. Cela peut indiquer une tentative de violation de votre organisation. Lors de la désactivation de CloudTrail, les modifications opérationnelles ne sont plus enregistrées. Une personne malveillante peut effectuer des activités malveillantes tout en évitant un événement d’audit CloudTrail, tel que la modification d’un compartiment S3 de privé à public.

**TP**, **B-TP**ou **FP**?

1. **TP**: Si vous êtes en mesure de vérifier que l’activité n’a pas été effectuée par un utilisateur légitime.

    **Action recommandée**: suspendre l’utilisateur, réinitialiser son mot de passe et inverser l’activité CloudTrail.
1. **FP**: Si vous êtes en mesure de vérifier que l’utilisateur a désactivé le service CloudTrail de manière légitime.

    **Action recommandée**: ignorez l’alerte.

**Comprendre l’étendue de la violation**

1. Examinez le journal d’activité pour rechercher d’autres indicateurs de compromission et consultez qui a apporté la modification au service CloudTrail.
1. Facultatif : créez un manuel à l’aide de Power automate pour contacter les utilisateurs et leurs responsables afin de vérifier leur activité.

### <a name="suspicious-email-deletion-activity-by-user"></a>Activité de suppression des e-mails suspects (par l’utilisateur)

Activités dans une session unique indiquant qu’un utilisateur a effectué des suppressions suspectes d’un courrier électronique. Cela peut indiquer une tentative de violation de votre organisation, par exemple des attaquants tentant de masquer des opérations en supprimant des e-mails relatifs à des activités de courrier indésirable.

**TP**, **B-TP**ou **FP**?

1. **TP**: Si vous êtes en mesure de vérifier que l’activité n’a pas été effectuée par un utilisateur légitime.

    **Action recommandée**: suspendre l’utilisateur, marquer l’utilisateur comme compromis et réinitialiser son mot de passe.
1. **FP**: Si vous êtes en mesure de vérifier que l’utilisateur a légitimement créé une règle pour supprimer des messages.

    **Action recommandée**: ignorez l’alerte.

**Comprendre l’étendue de la violation**

- Examinez toutes les activités des utilisateurs pour obtenir des indicateurs supplémentaires de compromission, tels que l’alerte de [transfert de boîte de réception suspecte](#suspicious-inbox-forwarding) , suivie d’une alerte de [voyage impossible](#impossible-travel) . Rechercher :

    1. Nouvelles règles de transfert SMTP, comme suit :
        - Vérifiez les noms des règles de transfert malveillants. Les noms de règle peuvent varier par rapport à des noms simples, tels que « transférer tous les E-mails » et « transfert automatique », ou des noms trompeurs, tels qu’un « . » à peine visible. Les noms de règle de transfert peuvent même être vides et le destinataire de transfert peut être un compte de messagerie unique ou une liste entière. Des règles malveillantes peuvent également être masquées à partir de l’interface utilisateur. Une fois détectés, vous pouvez utiliser ce billet de [blog](https://blogs.msdn.microsoft.com/hkong/2015/02/27/how-to-delete-corrupted-hidden-inbox-rules-from-a-mailbox-using-mfcmapi/) utile pour savoir comment supprimer des règles masquées des boîtes aux lettres.
        - Si vous détectez une règle de transfert non reconnue sur une adresse de messagerie interne ou externe inconnue, vous pouvez supposer que le compte de la boîte de réception a été compromis.
    1. Nouvelles règles de boîte de réception, telles que « supprimer tout », « déplacer les messages vers un autre dossier » ou avec des conventions d’affectation des noms obscures, par exemple « ... ».
    1. Augmentation des e-mails envoyés.

### <a name="suspicious-inbox-manipulation-rule"></a>Règle de manipulation suspecte de la boîte de réception

Activités indiquant qu’une personne malveillante a obtenu l’accès à la boîte de réception d’un utilisateur et créé une règle suspecte. Les règles de manipulation, telles que la suppression ou le déplacement de messages ou de dossiers, à partir de la boîte de réception d’un utilisateur peuvent être une tentative d’exfiltrer les informations de votre organisation. De même, ils peuvent indiquer une tentative de manipulation d’informations qu’un utilisateur voit ou d’utiliser dans sa boîte de réception pour distribuer le courrier indésirable, les e-mails hameçons ou les logiciels malveillants. Cloud App Security Profile votre environnement et déclenche des alertes lorsque des règles de manipulation de boîtes de réception suspectes sont détectées dans la boîte de réception d’un utilisateur. Cela peut indiquer que le compte de l’utilisateur est compromis.

**TP**, **B-TP**ou **FP**?

1. **TP**: Si vous êtes en mesure de confirmer qu’une règle de la boîte de réception malveillante a été créée et que le compte a été compromis.

    **Action recommandée**: suspendre l’utilisateur, réinitialiser son mot de passe et supprimer la règle de transfert.
1. **FP**: Si vous êtes en mesure de confirmer qu’un utilisateur a créé la règle de manière légitime.

    **Action recommandée**: ignorez l’alerte.

**Comprendre l’étendue de la violation**

1. Examinez toutes les activités des utilisateurs pour obtenir des indicateurs supplémentaires de compromission, tels que l’alerte de [transfert de boîte de réception suspecte](#suspicious-inbox-forwarding) , suivie d’une alerte de [voyage impossible](#impossible-travel) . Rechercher :
    - Nouvelles règles de transfert SMTP.
    - Nouvelles règles de boîte de réception, telles que « supprimer tout », « déplacer les messages vers un autre dossier » ou avec des conventions d’affectation des noms obscures, par exemple « ... ».
1. Collectez les informations sur l’adresse IP et l’emplacement de l’action.
1. Examinez les activités effectuées à partir de l’adresse IP utilisée pour créer la règle pour détecter d’autres utilisateurs compromis.

## <a name="privilege-escalation-alerts"></a>Alertes d’escalade de privilèges

Cette section décrit les alertes indiquant qu’un acteur malveillant peut tenter d’obtenir des autorisations de niveau supérieur dans votre organisation.

### <a name="unusual-administrative-activity-by-user"></a>Activité administrative inhabituelle (par l’utilisateur)

Activités indiquant qu’un attaquant a compromis un compte d’utilisateur et effectué des actions administratives qui ne sont pas communes à cet utilisateur. Par exemple, une personne malveillante peut tenter de modifier un paramètre de sécurité pour un utilisateur, une opération relativement rare pour un utilisateur commun. Cloud App Security crée une ligne de base basée sur le comportement de l’utilisateur et déclenche une alerte en cas de détection d’un comportement inhabituel.

**Période d’apprentissage**

L’établissement du modèle d’activité d’un nouvel utilisateur nécessite une période d’apprentissage initiale de sept jours pendant laquelle les alertes ne sont pas déclenchées pour les nouveaux emplacements.

**TP**, **B-TP**ou **FP**?

1. **TP**: Si vous êtes en mesure de vérifier que l’activité n’a pas été effectuée par un administrateur légitime.

    **Action recommandée**: suspendre l’utilisateur, marquer l’utilisateur comme compromis et réinitialiser son mot de passe.
1. **FP**: Si vous êtes en mesure de confirmer qu’un administrateur a réalisé légitimement le volume inhabituel d’activités d’administration.

    **Action recommandée**: ignorez l’alerte.

**Comprendre l’étendue de la violation**

1. Passez en revue toutes les activités des utilisateurs pour obtenir des indicateurs supplémentaires de compromission, tels que le [transfert de boîte de réception suspect](#suspicious-inbox-forwarding) ou le [déplacement impossible](#impossible-travel).
1. Examinez les autres modifications de configuration, telles que la création d’un compte d’utilisateur qui peut être utilisé pour la persistance.

## <a name="credential-access-alerts"></a>Alertes d’accès aux informations d’identification

Cette section décrit les alertes indiquant qu’un acteur malveillant peut tenter de voler les noms de compte et les mots de passe de votre organisation.

### <a name="multiple-failed-login-attempts"></a>Plusieurs tentatives de connexion infructueuses

Les tentatives de connexion ayant échoué peuvent indiquer une tentative de violation d’un compte. Toutefois, les échecs de connexion peuvent également être des comportements normaux. Par exemple, lorsqu’un utilisateur a entré un mot de passe incorrect par erreur. Pour obtenir une précision et une alerte uniquement si une tentative de violation est forte, Cloud App Security établit une ligne de base des habitudes de connexion pour chaque utilisateur de l’organisation et n’alerte que lorsque le comportement inhabituel est détecté.

**Période d’apprentissage**

L’établissement du modèle d’activité d’un nouvel utilisateur nécessite une période d’apprentissage initiale de sept jours pendant laquelle les alertes ne sont pas déclenchées pour les nouveaux emplacements.

**TP**, **B-TP**ou **FP**?

Cette stratégie est basée sur l’apprentissage du comportement de connexion normal d’un utilisateur. Lorsqu’un écart par rapport à la norme est détecté, une alerte est déclenchée. Si la détection commence à voir que le même comportement continue, l’alerte est déclenchée une seule fois.

1. **TP** (MFA échoue) : Si vous êtes en mesure de vérifier que l’authentification multifacteur fonctionne correctement, il peut s’agir d’une tentative d’attaque par force brute.

    **Actions recommandées** :
    1. Interrompez l’utilisateur, marquez l’utilisateur comme compromis et réinitialisez son mot de passe.
    1. Recherchez l’application qui a effectué les authentifications ayant échoué et reconfigurez-la.
    1. Recherchez d’autres utilisateurs connectés à l’heure de l’activité, car ils peuvent également être compromis. Interrompez l’utilisateur, marquez l’utilisateur comme compromis et réinitialisez son mot de passe.
1. **B-TP** (MFA échoue) : Si vous êtes en mesure de vérifier que l’alerte est due à un problème d’authentification mfa.

    **Action recommandée**: créez un manuel à l’aide de Power automate pour contacter l’utilisateur et vérifier s’il rencontre des problèmes avec mfa.
1. **B-TP** (application mal configurée) : Si vous êtes en mesure de confirmer qu’une application mal configurée tente de se connecter à un service à plusieurs moments avec des informations d’identification expirées.

    **Action recommandée**: ignorez l’alerte.
1. **B-TP** (mot de passe modifié) : Si vous êtes en mesure de confirmer qu’un utilisateur a modifié son mot de passe récemment, mais qu’il n’a pas affecté les informations d’identification sur les partages réseau.

    **Action recommandée**: ignorez l’alerte.
1. **B-TP** (test de sécurité) : Si vous êtes en mesure de confirmer qu’un test de sécurité ou d’intrusion est effectué par des analystes de la sécurité au nom de l’organisation.

    **Action recommandée**: ignorez l’alerte.

**Comprendre l’étendue de la violation**

1. Examinez toutes les activités des utilisateurs pour obtenir des indicateurs supplémentaires de compromission, tels que l’alerte, suivie de l’une des alertes suivantes : [voyage impossible](#impossible-travel), [activité à partir d’une adresse IP anonyme](#activity-from-anonymous-ip-address)ou [activité d’un pays peu fréquent](#activity-from-infrequent-country).
1. Passez en revue les informations suivantes sur l’appareil utilisateur et comparez-les aux informations d’appareil connues :
    - Système d’exploitation et version
    - Navigateur et version
    - Adresse IP et emplacement
1. Identifiez l’adresse IP source ou l’emplacement où la tentative d’authentification s’est produite.
1. Identifiez si l’utilisateur a récemment modifié son mot de passe et que tous les appareils et applications ont le mot de passe mis à jour.

## <a name="collection-alerts"></a>Alertes de collection

Cette section décrit les alertes indiquant qu’un acteur malveillant peut tenter de recueillir des données intéressantes pour son objectif de votre organisation.

### <a name="multiple-power-bi-report-sharing-activities"></a>Plusieurs Power BI des activités de partage de rapports

Activités dans une session unique indiquant qu’un utilisateur a effectué un nombre inhabituel d’activités de rapport de partage dans Power BI par rapport à la ligne de base apprise. Cela peut indiquer une tentative de violation de votre organisation.

**Période d’apprentissage**

L’établissement du modèle d’activité d’un nouvel utilisateur nécessite une période d’apprentissage initiale de sept jours pendant laquelle les alertes ne sont pas déclenchées pour les nouveaux emplacements.

**TP**, **B-TP**ou **FP**?

1. **TP**: Si vous êtes en mesure de vérifier que l’activité n’a pas été effectuée par un utilisateur légitime.

    **Action recommandée**: supprimer l’accès de partage de Power bi. Si vous êtes en mesure de vérifier que le compte est compromis, interrompez l’utilisateur, marquez l’utilisateur comme compromis et réinitialisez son mot de passe.
1. **FP**: Si vous êtes en mesure de vérifier que l’utilisateur a une justification pour partager ces rapports.

    **Action recommandée**: ignorez l’alerte.

**Comprendre l’étendue de la violation**

1. Examinez le journal d’activité pour mieux comprendre les autres activités effectuées par l’utilisateur. Examinez l’adresse IP à partir de laquelle ils sont connectés et les détails de l’appareil.
1. Contactez votre équipe Power BI ou Information Protection pour comprendre les instructions de partage des rapports en interne et en externe.

### <a name="suspicious-power-bi-report-sharing"></a>Partage de rapport Power BI suspect

Activités indiquant qu’un utilisateur a partagé un rapport Power BI qui peut contenir des informations sensibles identifiées à l’aide de NLP pour analyser les métadonnées du rapport. Le rapport a été partagé avec une adresse de messagerie externe, publiée sur le Web, ou un instantané a été remis à une adresse de messagerie abonnée en externe. Cela peut indiquer une tentative de violation de votre organisation.

**TP**, **B-TP**ou **FP**?

1. **TP**: Si vous êtes en mesure de vérifier que l’activité n’a pas été effectuée par un utilisateur légitime.

    **Action recommandée**: supprimer l’accès de partage de Power bi. Si vous êtes en mesure de vérifier que le compte est compromis, interrompez l’utilisateur, marquez l’utilisateur comme compromis et réinitialisez son mot de passe.
1. **FP**: Si vous êtes en mesure de vérifier que l’utilisateur a une justification pour partager ces rapports.

    **Action recommandée**: ignorez l’alerte.

**Comprendre l’étendue de la violation**

1. Examinez le journal d’activité pour mieux comprendre les autres activités effectuées par l’utilisateur. Examinez l’adresse IP à partir de laquelle ils sont connectés et les détails de l’appareil.
1. Contactez votre équipe Power BI ou Information Protection pour comprendre les instructions de partage des rapports en interne et en externe.

### <a name="unusual-impersonated-activity-by-user"></a>Activité inhabituelle empruntée (par l’utilisateur)

Dans certains logiciels, il existe des options permettant d’autoriser d’autres utilisateurs à emprunter l’identité d’autres utilisateurs. Par exemple, les services de messagerie permettent aux utilisateurs d’autoriser d’autres utilisateurs à envoyer des e-mails en leur nom. Cette activité est couramment utilisée par les attaquants pour créer des e-mails de hameçonnage en vue d’extraire des informations sur votre organisation. Cloud App Security crée une ligne de base basée sur le comportement de l’utilisateur et crée une activité quand une activité d’emprunt d’identité inhabituelle est détectée.

**Période d’apprentissage**

L’établissement du modèle d’activité d’un nouvel utilisateur nécessite une période d’apprentissage initiale de sept jours pendant laquelle les alertes ne sont pas déclenchées pour les nouveaux emplacements.

**TP**, **B-TP**ou **FP**?

1. **TP**: Si vous êtes en mesure de vérifier que l’activité n’a pas été effectuée par un utilisateur légitime.

    **Action recommandée**: suspendre l’utilisateur, marquer l’utilisateur comme compromis et réinitialiser son mot de passe.
1. **FP** (comportement inhabituel) : Si vous êtes en mesure de confirmer que l’utilisateur a effectué des activités inhabituelles ou plus d’activités que la base de référence établie.

    **Action recommandée**: ignorez l’alerte.
1. **FP**: Si vous êtes en mesure de vérifier que les applications, telles que les équipes, empruntent l’identité de l’utilisateur.

    **Action recommandée**: passez en revue les actions et ignorez l’alerte si nécessaire.

**Comprendre l’étendue de la violation**

1. Passez en revue toutes les alertes et l’activité des utilisateurs pour obtenir des indicateurs supplémentaires de compromission.
1. Passez en revue les activités d’emprunt d’identité pour identifier les activités malveillantes potentielles.
1. Passez en revue la configuration d’accès délégué.

## <a name="exfiltration-alerts"></a>Alertes d’exfiltration

Cette section décrit les alertes indiquant qu’un acteur malveillant peut tenter de voler des données de votre organisation.

### <a name="suspicious-inbox-forwarding"></a>Transfert de boîte de réception suspect

Activités indiquant qu’une personne malveillante a obtenu l’accès à la boîte de réception d’un utilisateur et créé une règle suspecte. Les règles de manipulation, telles que transférer l’ensemble ou des e-mails spécifiques à un autre compte de messagerie, peuvent être une tentative d’exfiltrer les informations de votre organisation. Cloud App Security Profile votre environnement et déclenche des alertes lorsque des règles de manipulation de boîtes de réception suspectes sont détectées dans la boîte de réception d’un utilisateur. Cela peut indiquer que le compte de l’utilisateur est compromis.

**TP**, **B-TP**ou **FP**?

1. **TP**: Si vous êtes en mesure de confirmer qu’une règle de transfert de boîte de réception malveillante a été créée et que le compte a été compromis.

    **Action recommandée**: suspendre l’utilisateur, réinitialiser son mot de passe et supprimer la règle de transfert.
1. **FP**: Si vous êtes en mesure de vérifier que l’utilisateur a créé une règle de transfert vers un compte de messagerie externe nouveau ou personnel pour des raisons légitimes.

    **Action recommandée**: ignorez l’alerte.

**Comprendre l’étendue de la violation**

1. Passez en revue toutes les activités des utilisateurs pour obtenir des indicateurs supplémentaires de compromission, tels que l’alerte, suivie d’une alerte de [voyage impossible](#impossible-travel) . Rechercher :

    1. Nouvelles règles de transfert SMTP, comme suit :
        - Vérifiez les noms des règles de transfert malveillants. Les noms de règle peuvent varier par rapport à des noms simples, tels que « transférer tous les E-mails » et « transfert automatique », ou des noms trompeurs, tels qu’un « . » à peine visible. Les noms de règle de transfert peuvent même être vides et le destinataire de transfert peut être un compte de messagerie unique ou une liste entière. Des règles malveillantes peuvent également être masquées à partir de l’interface utilisateur. Une fois détectés, vous pouvez utiliser ce billet de [blog](https://blogs.msdn.microsoft.com/hkong/2015/02/27/how-to-delete-corrupted-hidden-inbox-rules-from-a-mailbox-using-mfcmapi/) utile pour savoir comment supprimer des règles masquées des boîtes aux lettres.
        - Si vous détectez une règle de transfert non reconnue sur une adresse de messagerie interne ou externe inconnue, vous pouvez supposer que le compte de la boîte de réception a été compromis.
    1. Nouvelles règles de boîte de réception, telles que « supprimer tout », « déplacer les messages vers un autre dossier » ou avec des conventions d’affectation des noms obscures, par exemple « ... ».
1. Examinez les activités effectuées à partir de l’adresse IP utilisée pour créer la règle pour détecter d’autres utilisateurs compromis.
1. Passez en revue la liste des messages transférés à l’aide du suivi des messages Exchange Online.

### <a name="unusual-file-download-by-user"></a>Téléchargement de fichiers inhabituels (par l’utilisateur)

Activités indiquant qu’un utilisateur a effectué un nombre inhabituel de téléchargements de fichiers à partir d’une plateforme de stockage Cloud par rapport à la ligne de base apprise. Cela peut indiquer une tentative d’obtention d’informations sur l’organisation. Cloud App Security crée une ligne de base basée sur le comportement de l’utilisateur et déclenche une alerte en cas de détection d’un comportement inhabituel.

**Période d’apprentissage**

L’établissement du modèle d’activité d’un nouvel utilisateur nécessite une période d’apprentissage initiale de sept jours pendant laquelle les alertes ne sont pas déclenchées pour les nouveaux emplacements.

**TP**, **B-TP**ou **FP**?

1. **TP**: Si vous êtes en mesure de vérifier que l’activité n’a pas été effectuée par un utilisateur légitime.

    **Action recommandée**: suspendre l’utilisateur, marquer l’utilisateur comme compromis et réinitialiser son mot de passe.
1. **FP** (comportement inhabituel) : Si vous pouvez vérifier que l’utilisateur a effectué légitimement plus d’activités de téléchargement de fichiers que la base de référence établie.

    **Action recommandée**: ignorez l’alerte.
1. **FP** (synchronisation logicielle) : Si vous êtes en mesure de vérifier que le logiciel, tel que OneDrive, est synchronisé avec une sauvegarde externe qui a provoqué l’alerte.

    **Action recommandée**: ignorez l’alerte.

**Comprendre l’étendue de la violation**

1. Passez en revue les activités de téléchargement et créez une liste de fichiers téléchargés.
1. Passez en revue la sensibilité des fichiers téléchargés avec le propriétaire de la ressource et validez le niveau d’accès.

### <a name="unusual-file-share-activity-by-user"></a>Activité inhabituelle de partage de fichiers (par utilisateur)

Activités indiquant qu’un utilisateur a effectué un nombre inhabituel d’actions de partage de fichiers à partir d’une plateforme de stockage Cloud par rapport à la ligne de base apprise. Cela peut indiquer une tentative d’obtention d’informations sur l’organisation. Cloud App Security crée une ligne de base basée sur le comportement de l’utilisateur et déclenche une alerte en cas de détection d’un comportement inhabituel.

**Période d’apprentissage**

L’établissement du modèle d’activité d’un nouvel utilisateur nécessite une période d’apprentissage initiale de sept jours pendant laquelle les alertes ne sont pas déclenchées pour les nouveaux emplacements.

**TP**, **B-TP**ou **FP**?

1. **TP**: Si vous êtes en mesure de vérifier que l’activité n’a pas été effectuée par un utilisateur légitime.

    **Action recommandée**: suspendre l’utilisateur, marquer l’utilisateur comme compromis et réinitialiser son mot de passe.
1. **FP** (comportement inhabituel) : Si vous êtes en mesure de vérifier que l’utilisateur a effectué des opérations de partage de fichiers plus légitimes que la base de référence établie.

    **Action recommandée**: ignorez l’alerte.

**Comprendre l’étendue de la violation**

1. Passez en revue les activités de partage et créez une liste de fichiers partagés.
1. Passez en revue la sensibilité des fichiers partagés avec le propriétaire de la ressource et validez le niveau d’accès.
1. Créez une stratégie de fichier pour les documents similaires afin de détecter le partage futur de fichiers sensibles.

## <a name="impact-alerts"></a>Alertes d’impact

Cette section décrit les alertes indiquant qu’un acteur malveillant peut tenter de manipuler, d’interrompre ou de détruire des systèmes et des données de votre organisation.

### <a name="multiple-delete-vm-activities"></a>Plusieurs activités de suppression de machine virtuelle

Activités dans une session unique indiquant qu’un utilisateur a effectué un nombre inhabituel de suppressions de machines virtuelles par rapport à la ligne de base apprise. Plusieurs suppressions de machines virtuelles peuvent indiquer une tentative d’interruption ou de destruction d’un environnement. Toutefois, il existe de nombreux scénarios normaux où les machines virtuelles sont supprimées.

**TP**, **B-TP**ou **FP**?

Pour améliorer la précision et l’alerte uniquement lorsqu’il existe une indication forte d’une violation, cette détection établit une ligne de base sur chaque environnement de l’organisation afin de réduire les incidents de **B-TP** et alerte uniquement lorsque le comportement inhabituel est détecté.

**Période d’apprentissage**

L’établissement du modèle d’activité d’un nouvel utilisateur nécessite une période d’apprentissage initiale de sept jours pendant laquelle les alertes ne sont pas déclenchées pour les nouveaux emplacements.

- **TP**: Si vous êtes en mesure de vérifier que les suppressions n’ont pas été autorisées.

    **Action recommandée**: suspendre l’utilisateur, réinitialiser son mot de passe et analyser tous les appareils à la recherche de menaces malveillantes. Examinez toutes les activités des utilisateurs pour d’autres indicateurs de compromission et explorez l’étendue de l’impact.
- **B-TP**: si, après votre investigation, vous êtes en mesure de vérifier que l’administrateur a été autorisé à effectuer ces activités de suppression.

    **Action recommandée**: ignorez l’alerte.

**Comprendre l’étendue de la violation**

1. Contactez l’utilisateur et confirmez l’activité.
1. Examinez toutes les activités des utilisateurs pour obtenir des indicateurs supplémentaires de compromission, tels que l’alerte, suivie de l’une des alertes suivantes : [voyage impossible](#impossible-travel), [activité à partir d’une adresse IP anonyme](#activity-from-anonymous-ip-address)ou [activité d’un pays peu fréquent](#activity-from-infrequent-country).

### <a name="ransomware-activity"></a>Activité ransomware

Un ransomware est un cyberattaque dans lequel un pirate verrouille les victimes à partir de leurs appareils ou les empêche d’accéder à leurs fichiers jusqu’à ce que la victime paye un ransomware. Les ransomware peuvent être réparties par un fichier partagé malveillant ou un réseau compromis. Cloud App Security utilise l’expertise en matière de recherche de sécurité, l’intelligence des menaces et les modèles de comportement pour identifier l’activité des ransomware. Par exemple, un taux élevé de chargements de fichiers ou de suppressions de fichiers peut représenter un processus de chiffrement qui est courant parmi les opérations de ransomware.

Cette détection établit une ligne de base des modèles de travail normaux de chaque utilisateur de votre organisation, par exemple quand l’utilisateur accède au Cloud et ce qu’il fait couramment dans le Cloud.

Les stratégies de détection des menaces automatisées de Cloud App Security commencent à s’exécuter en arrière-plan à partir du moment où vous vous connectez. Grâce à notre expertise en matière de recherche en sécurité pour identifier les modèles de comportement qui reflètent l’activité des ransomware dans notre organisation, Cloud App Security fournit une couverture complète contre les attaques par ransomware sophistiquées.

**Période d’apprentissage**

L’établissement du modèle d’activité d’un nouvel utilisateur nécessite une période d’apprentissage initiale de sept jours pendant laquelle les alertes ne sont pas déclenchées pour les nouveaux emplacements.

**TP**, **B-TP**ou **FP**?

1. **TP**: Si vous êtes en mesure de vérifier que l’activité n’a pas été effectuée par l’utilisateur.

    **Action recommandée**: suspendre l’utilisateur, marquer l’utilisateur comme compromis et réinitialiser son mot de passe.
1. **FP** (comportement inhabituel) : l’utilisateur a effectué en toute légitimité plusieurs activités de suppression et de chargement de fichiers similaires dans un laps de temps réduit.

    **Action recommandée**: après avoir vérifié le journal d’activité et confirmé que les extensions de fichier ne sont pas suspectes, fermez l’alerte.
1. **FP** (extension de fichier de ransomware commun) : Si vous êtes en mesure de vérifier que les extensions des fichiers affectés correspondent à une extension connue de ransomware.

    **Action recommandée**: contactez l’utilisateur et vérifiez que les fichiers sont sûrs, puis ignorez l’alerte.

**Comprendre l’étendue de la violation**

1. Examinez le journal d’activité pour rechercher d’autres indicateurs de compromission, tels que le téléchargement en masse, ou la suppression de masse, des fichiers.
1. Si vous utilisez Microsoft Defender-protection avancée contre les menaces, passez en revue les alertes de l’ordinateur de l’utilisateur pour voir si des fichiers malveillants ont été détectés.
1. Recherchez dans le journal d’activité des activités de chargement et de partage de fichiers malveillants.

### <a name="unusual-file-deletion-activity-by-user"></a>Activité inhabituelle de suppression de fichier (par l’utilisateur)

Activités indiquant qu’un utilisateur a effectué une opération de suppression de fichier inhabituelle par rapport à la ligne de base apprise. Cela peut indiquer une attaque par ransomware. Par exemple, une personne malveillante peut chiffrer les fichiers d’un utilisateur et supprimer tous les originaux, en laissant uniquement les versions chiffrées qui peuvent être utilisées pour contraindre la victime à payer un ransomware. Cloud App Security crée une ligne de base basée sur le comportement normal de l’utilisateur et déclenche une alerte en cas de détection d’un comportement inhabituel.

**Période d’apprentissage**

L’établissement du modèle d’activité d’un nouvel utilisateur nécessite une période d’apprentissage initiale de sept jours pendant laquelle les alertes ne sont pas déclenchées pour les nouveaux emplacements.

**TP**, **B-TP**ou **FP**?

1. **TP**: Si vous êtes en mesure de vérifier que l’activité n’a pas été effectuée par un utilisateur légitime.

    **Action recommandée**: suspendre l’utilisateur, marquer l’utilisateur comme compromis et réinitialiser son mot de passe.
1. **FP**: Si vous êtes en mesure de vérifier que l’utilisateur a effectué une opération de suppression de fichiers plus grande que la base de référence établie.

    **Action recommandée**: ignorez l’alerte.

**Comprendre l’étendue de la violation**

1. Passez en revue les activités de suppression et créez une liste de fichiers supprimés. Si nécessaire, récupérez les fichiers supprimés.
1. Si vous le souhaitez, créez un manuel à l’aide de Power automate pour contacter les utilisateurs et leurs responsables afin de vérifier l’activité.

## <a name="see-also"></a>Voir aussi

> [!div class="nextstepaction"]
> [Enquêter sur les utilisateurs à risque](tutorial-ueba.md)
