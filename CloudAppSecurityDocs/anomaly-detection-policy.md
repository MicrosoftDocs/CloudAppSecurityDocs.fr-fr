---
title: Créer des stratégies de détection des anomalies dans Cloud App Security
description: Cet article fournit une description des stratégies de détection des anomalies et fournit des informations de référence sur les blocs de construction d’une stratégie de détection d’anomalie.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/24/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: dd637bc49d65452cedc13841686ea267134ef15e
ms.sourcegitcommit: 2cf3c78a1b45a5b6ca534fdd12fd97afc51726e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291238"
---
# <a name="get-instantaneous-behavioral-analytics-and-anomaly-detection"></a>Bénéficiez d’une analyse comportementale et d’une détection des anomalies instantanées

*S’applique à : Microsoft Cloud App Security*

Les stratégies de détection des anomalies d’Microsoft Cloud App Security fournissent une analyse comportementale des utilisateurs et des entités (UEBA) et des Machine Learning (ML) prêts à l’emploi afin que vous puissiez exécuter immédiatement la détection avancée des menaces dans votre environnement Cloud. Étant donné qu’elles sont automatiquement activées, les nouvelles stratégies de détection des anomalies fournissent des résultats immédiats en fournissant des détections immédiates, ciblant de nombreuses anomalies comportementales au sein de vos utilisateurs, ainsi que les ordinateurs et les appareils connectés à votre réseau.  De plus, les nouvelles stratégies exposent davantage de données à partir du moteur de détection Cloud App Security pour vous aider à accélérer le processus d’investigation et à contenir des menaces continues.

Les stratégies de détection des anomalies sont automatiquement activées, mais Cloud App Security présente une période d’apprentissage initiale de sept jours au cours de laquelle toutes les alertes de détection d’anomalie ne sont pas générées. Après cela, chaque session est comparée à l’activité, lorsque les utilisateurs étaient actifs, les adresses IP, les appareils, etc. détectés au cours du mois passé et le score de risque de ces activités.  Ces détections font partie du moteur de détection des anomalies heuristique qui Profile votre environnement et déclenche des alertes en ce qui concerne une ligne de base qui a été appris sur l’activité de votre organisation. Ces détections utilisent également des algorithmes de Machine Learning conçus pour profiler les utilisateurs et le modèle de connexion afin de réduire les faux positifs.

Les anomalies sont détectées en analysant l’activité des utilisateurs. Le risque est évalué en examinant plus de 30 indicateurs de risque différents, regroupés en facteurs de risque, comme suit :

* Adresse IP à risque
* Échecs de connexion
* Activité d’administration
* Comptes inactifs
* Location
* Voyage impossible
* Appareil et agent utilisateur
* Taux d’activité

En fonction des résultats de la stratégie, des alertes de sécurité sont déclenchées. Cloud App Security examine chaque session utilisateur sur votre Cloud et vous alerte en cas de problème qui diffère de la ligne de base de votre organisation ou de l’activité ordinaire de l’utilisateur.

Outre les alertes de Cloud App Security natives, vous obtiendrez également les alertes de détection suivantes basées sur les informations reçues de la protection d’identité des Azure Active Directory (AD) :

* Informations d’identification divulguées : déclenché lorsque les informations d’identification valides d’un utilisateur ont été divulguées. Pour plus d’informations, consultez [détection des informations d’identification divulguées de Azure ad](/azure/active-directory/identity-protection/concept-identity-protection-risks#user-risk).
* Connexion risquée : combine un certain nombre de détections de connexion Azure AD Identity Protection en une seule détection (désactivée par défaut). Pour plus d’informations, consultez [détection des risques de connexion de Azure ad](/azure/active-directory/identity-protection/concept-identity-protection-risks#sign-in-risk).

Ces stratégies s’affichent dans la page Cloud App Security les stratégies et peuvent être activées ou désactivées, mais pas modifiées.

## <a name="anomaly-detection-policies"></a>Stratégie de détection des anomalies

Vous pouvez voir les stratégies de détection des anomalies dans le portail en cliquant sur **contrôle** , puis sur **stratégies**. Sélectionnez **stratégie de détection d’anomalies** pour le type de stratégie.

 ![nouvelles stratégies de détection des anomalies](media/new-anomaly-detection-policies.png)

Les stratégies de détection des anomalies suivantes sont disponibles :

### <a name="impossible-travel"></a>Voyage impossible

* Cette détection identifie deux activités de l’utilisateur (une seule ou plusieurs sessions) provenant d’emplacements éloignés géographiquement au cours d’une période plus longue que le temps qu’il aurait fallu à l’utilisateur pour se déplacer du premier emplacement au second, ce qui indique qu’un autre utilisateur utilise les mêmes informations d’identification. Cette détection utilise un algorithme de Machine Learning qui ignore les « faux positifs » évidents contribuant à la condition de voyage impossible, tels que les VPN et les emplacements régulièrement utilisés par d’autres utilisateurs de l’organisation. La détection a une période d’apprentissage initiale de sept jours au cours de laquelle elle apprend le modèle d’activité d’un nouvel utilisateur. La détection de voyage impossible identifie les activités utilisateur inhabituelles et impossibles entre deux emplacements. L’activité doit être suffisamment inhabituelle pour être considérée comme un indicateur de compromission et digne d’une alerte. Pour que cela fonctionne, la logique de détection comprend différents niveaux de suppression des scénarios qui peuvent déclencher des faux positifs, tels que des activités VPN. Le curseur sensibilité vous permet d’avoir un impact sur l’algorithme et de définir la rigueur de la logique de détection. Plus le niveau de sensibilité est élevé, plus la suppression appliquée dans le cadre de la logique de détection est faible. De cette façon, vous pouvez adapter la détection en fonction de vos besoins de couverture et de vos cibles SNR.

    > [!NOTE]
    > Lorsque les adresses IP des deux côtés du voyage sont [marquées comme étant professionnelles](ip-tags.md), le voyage est considéré comme approuvé et exclu du déclenchement de la détection de voyage impossible. Toutefois, si l’adresse IP d’un seul côté du voyage est marquée comme entreprise, la détection est déclenchée normalement.

### <a name="activity-from-infrequent-country"></a>Activité à partir d’un pays peu fréquent

* Cette détection prend en compte les emplacements d’activité passés pour déterminer les emplacements nouveaux et peu fréquents. Le moteur de détection des anomalies stocke les informations sur les emplacements précédents utilisés par les utilisateurs de l’organisation. Une alerte est déclenchée lorsqu’une activité se produit à partir d’un emplacement qui n’a jamais été visité récemment ou jamais par un utilisateur de l’organisation.

### <a name="malware-detection"></a>Détection de logiciel malveillant

* Cette détection identifie les fichiers malveillants dans votre stockage cloud, qu’ils proviennent de vos applications Microsoft ou d’applications tierces. Microsoft Cloud App Security utilise les informations sur les menaces de Microsoft pour déterminer si certains fichiers sont associés à des attaques de programmes malveillants connus et sont potentiellement malveillants. Cette stratégie intégrée est désactivée par défaut. Tous les fichiers ne sont pas analysés, mais les heuristiques sont utilisées pour rechercher des fichiers potentiellement dangereux. Une fois les fichiers détectés, vous pouvez voir la liste des **fichiers infectés**. Cliquez sur le nom du fichier de programme malveillant dans le tiroir de fichier pour ouvrir un rapport de programmes malveillants qui vous fournit des informations sur ce type de programme malveillant avec lequel le fichier est infecté.

    > [!NOTE]
    > * Pour la détection de programmes malveillants Office 365, vous avez besoin d’une licence valide pour Office 365-protection avancée contre les menaces P1.
    > * Cloud App Security prend en charge la détection de programmes malveillants pour les applications suivantes :
    >   * Box
    >   * Dropbox
    >   * G Suite
    >   * Office 365

### <a name="activity-from-anonymous-ip-addresses"></a>Activité à partir d’adresses IP anonymes

* Cette détection identifie que les utilisateurs étaient actifs à partir d’une adresse IP qui a été identifiée comme une adresse IP de proxy anonyme. Ces proxys sont utilisés par les personnes qui souhaitent masquer l’adresse IP de leur appareil et peuvent être utilisés à des fins malveillantes. Cette détection utilise un algorithme de Machine Learning qui réduit les « faux positifs », tels que les adresses IP mal identifiées qui sont largement utilisées par les utilisateurs de l’organisation.

### <a name="ransomware-activity"></a>Activité de ransomware

* Cloud App Security a étendu ses fonctionnalités de détection de ransomware à la détection d’anomalies pour garantir une couverture plus complète contre les attaques par ransomware sophistiqué. Grâce à notre expertise en matière de recherche sur la sécurité pour identifier des modèles de comportement qui reflètent l’activité des ransomware, Cloud App Security garantit une protection holistique et robuste. Si Cloud App Security identifie, par exemple, un taux élevé de chargements de fichiers ou d’activités de suppression de fichiers, il peut représenter un processus de chiffrement défavorable. Ces données sont collectées dans les journaux reçus à partir des API connectées et sont ensuite associées à des modèles comportementals appris et à des informations sur les menaces, par exemple, des extensions de ransomware connues. Pour plus d’informations sur la façon dont Cloud App Security détecte les ransomware, consultez [protection de votre organisation contre les ransomware](use-case-ransomware.md).

### <a name="activity-performed-by-terminated-user"></a>Activité effectuée par l’utilisateur terminé

* Cette détection vous permet de déterminer quand un employé terminé continue d’effectuer des actions sur vos applications SaaS. Dans la mesure où les données montrent que le plus grand risque de menaces internes provient d’employés qui ont quitté des termes incorrects, il est important de garder un œil sur l’activité sur les comptes des employés mis en service. Parfois, quand les employés quittent une société, leurs comptes sont désapprovisionnés à partir d’applications d’entreprise, mais dans de nombreux cas, ils conservent toujours l’accès à certaines ressources de l’entreprise. Cela est encore plus important lors de l’examen de comptes privilégiés, car les dommages potentiels qu’un administrateur précédent peut faire sont par nature plus importants.
Cette détection tire parti de la capacité de Cloud App Security d’analyser le comportement des utilisateurs entre les applications, ce qui permet d’identifier l’activité normale de l’utilisateur, le fait que le compte a été arrêté et l’activité réelle sur d’autres applications. Par exemple, un employé qui est Azure AD compte a été mis fin, mais qui a toujours accès à l’infrastructure AWS de l’entreprise, a la possibilité de provoquer des dégâts à grande échelle.

La détection recherche les utilisateurs dont le compte a été terminé dans Azure AD, tout en effectuant des activités sur d’autres plateformes telles que AWS ou Salesforce. Cela est particulièrement utile pour les utilisateurs qui utilisent un autre compte (pas leur compte d’authentification unique principal) pour gérer les ressources, car ces comptes ne sont souvent pas terminés lorsqu’un utilisateur quitte l’entreprise.

### <a name="activity-from-suspicious-ip-addresses"></a>Activité à partir d’adresses IP suspectes

* Cette détection identifie que les utilisateurs étaient actifs à partir d’une adresse IP identifiée comme risquée par Microsoft Threat Intelligence. Ces adresses IP sont impliquées dans des activités malveillantes, telles que le botnet C & C, et peuvent indiquer un compte compromis. Cette détection utilise un algorithme de Machine Learning qui réduit les « faux positifs », tels que les adresses IP mal identifiées qui sont largement utilisées par les utilisateurs de l’organisation.

### <a name="suspicious-inbox-forwarding"></a>Transfert de boîte de réception suspect

* Cette détection recherche les règles de transfert d’e-mails suspectes, par exemple, si un utilisateur a créé une règle de boîte de réception qui transmet une copie de tous les messages électroniques à une adresse externe.

> [!NOTE]
> Cloud App Security vous alerte uniquement pour chaque règle de transfert identifiée comme suspecte, en fonction du comportement classique de l’utilisateur.

### <a name="suspicious-inbox-manipulation-rules"></a>Règles de manipulation de boîtes de réception suspectes

* Cette détection Profile votre environnement et déclenche des alertes lorsque des règles suspectes qui suppriment ou déplacent des messages ou des dossiers sont définies dans la boîte de réception d’un utilisateur. Cela peut indiquer que le compte de l’utilisateur est compromis, que les messages sont intentionnellement masqués et que la boîte aux lettres est utilisée pour distribuer le courrier indésirable ou les logiciels malveillants dans votre organisation.

### <a name="suspicious-email-deletion-activity-preview"></a>Activité de suppression des e-mails suspects (version préliminaire)

* Cette stratégie Profile votre environnement et déclenche des alertes lorsqu’un utilisateur effectue des activités de suppression d’e-mails suspectes dans une seule session. Cette stratégie peut indiquer qu’une boîte aux lettres utilisateur peut être compromise par des vecteurs d’attaque potentiels, tels que la communication de commande et de contrôle (C & C/C2) par courrier électronique.

### <a name="unusual-activities-by-user"></a>Activités inhabituelles (par utilisateur)

Ces détections identifient les utilisateurs qui effectuent les opérations suivantes :

* Activités de téléchargement de plusieurs fichiers inhabituelles
* Activités de partage de fichiers inhabituelles
* Activités de suppression de fichiers inhabituelles
* Activités d’emprunt d’identité inhabituelles
* Activités administratives inhabituelles
* Activités de partage de rapport Power BI inhabituelles (version préliminaire)
* Activités de création de plusieurs machines virtuelles inhabituelles (version préliminaire)
* Activités de suppression de plusieurs stockages inhabituelles (version préliminaire)
* Région inhabituelle pour la ressource Cloud (version préliminaire)

Ces stratégies recherchent les activités au sein d’une seule session par rapport à la ligne de base apprise, ce qui peut indiquer une tentative de violation. Ces détections tirent parti d’un algorithme de Machine Learning qui Profile le modèle de connexion des utilisateurs et réduit le nombre de faux positifs. Ces détections font partie du moteur de détection des anomalies heuristique qui Profile votre environnement et déclenche des alertes en ce qui concerne une ligne de base qui a été appris sur l’activité de votre organisation.

### <a name="multiple-failed-login-attempts"></a>Plusieurs tentatives de connexion ayant échoué

* Cette détection identifie les utilisateurs ayant échoué plusieurs tentatives de connexion dans une seule session en ce qui concerne la ligne de base apprise, ce qui peut indiquer une tentative de violation.

### <a name="data-exfiltration-to-unsanctioned-apps"></a>Exfiltration de données en applications non approuvées

* Cette stratégie est automatiquement activée pour vous avertir lorsqu’un utilisateur ou une adresse IP utilise une application qui n’est pas approuvée pour effectuer une activité qui ressemble à une tentative d’exfiltrer des informations de votre organisation.

### <a name="multiple-delete-vm-activities"></a>Plusieurs activités de suppression de machines virtuelles

* Cette stratégie Profile votre environnement et déclenche des alertes lorsque les utilisateurs suppriment plusieurs machines virtuelles dans une seule session, par rapport à la ligne de base de votre organisation. Cela peut indiquer une tentative de violation.

## <a name="enable-automated-governance"></a>Activer la gouvernance automatisée<a name="adp-automated-gov"></a>

Vous pouvez activer les actions de correction automatisées sur les alertes générées par les stratégies de détection des anomalies.

1. Cliquez sur le nom de la stratégie de détection dans la page **stratégie** .
1. Dans la fenêtre **modifier la stratégie de détection d’anomalie** qui s’ouvre, sous **gouvernance** , définissez les actions de correction souhaitées pour chaque application connectée ou pour toutes les applications.
1. Cliquez sur **Mettre à jour**.

## <a name="tune-anomaly-detection-policies"></a>Régler les stratégies de détection des anomalies

Pour affecter le moteur de détection des anomalies à la suppression ou à la surface des alertes en fonction de vos préférences :

* Dans la stratégie de voyage impossible, vous pouvez définir le curseur de sensibilité afin de déterminer le niveau de comportement anormal nécessaire pour déclencher une alerte. Par exemple, si vous la définissez sur faible, cela supprime les alertes de voyage impossibles à partir des emplacements communs d’un utilisateur et, si vous la définissez sur élevé, cela entraîne des alertes. Vous pouvez choisir parmi les niveaux de sensibilité suivants :

  * **Faible**: suppressions du système, du locataire et de l’utilisateur
  * **Moyenne**: suppressions du système et de l’utilisateur
  * **Haute**: uniquement les suppressions du système

    Où :

    | Type de suppression | Description |
    | --- | --- |
    | **Système** | Détections intégrées qui sont toujours supprimées. |
    | **Locataire** | Activités courantes basées sur l’activité précédente dans le locataire. Par exemple, la suppression d’activités d’un fournisseur de services Internet ayant précédemment été alerté au sein de votre organisation. |
    | **Utilisateur** | Activités courantes basées sur l’activité précédente de l’utilisateur spécifique. Par exemple, la suppression d’activités à partir d’un emplacement couramment utilisé par l’utilisateur. |

* Vous pouvez également configurer si les alertes d’activité dans un pays peu fréquent, les adresses IP anonymes, les adresses IP suspectes et le voyage impossible doivent analyser les connexions ayant échoué et celles ayant réussi, ou uniquement les connexions ayant réussi.

> [!NOTE]
> Par défaut, les protocoles de connexion hérités, tels que ceux qui n’utilisent pas multi-Factor Authentication (par exemple, WS-Trust), ne sont pas contrôlés par la stratégie de voyage impossible. Si votre organisation utilise des protocoles hérités, pour éviter les activités pertinentes manquantes, modifiez la stratégie et, sous **Configuration avancée**, définissez **analyser les activités de connexion** à **toutes les connexions**.

## <a name="scope-anomaly-detection-policies"></a>Stratégies de détection des anomalies d’étendue

Chaque stratégie de détection d’anomalie peut être étendue de manière indépendante pour s’appliquer uniquement aux utilisateurs et aux groupes que vous souhaitez inclure et exclure de la stratégie.
Par exemple, sous Activité, vous pouvez définir la détection d’une région rare ou ignorer un utilisateur spécifique qui voyage fréquemment.

Pour étendre une stratégie de détection d’anomalie :

1. Cliquez sur **contrôler** les **stratégies**de > et définissez le filtre de **type** sur la stratégie de **détection des anomalies**.
1. Cliquez sur la stratégie que vous souhaitez étendre.
1. Sous **étendue**, définissez la liste déroulante des paramètres par défaut de **tous les utilisateurs et groupes**, sur des **utilisateurs et des groupes spécifiques**.
1. Sélectionnez **inclure** pour spécifier les utilisateurs et les groupes auxquels cette stratégie s’applique. Tout utilisateur ou groupe non sélectionné ici n’est pas considéré comme une menace et ne génère pas d’alerte.
1. Sélectionnez **exclure** pour spécifier les utilisateurs auxquels cette stratégie ne s’applique pas. Les utilisateurs sélectionnés ici ne sont pas considérés comme une menace et ne génèrent pas d’alerte, même s’ils sont membres de groupes sélectionnés sous **inclure**.

    ![étendue de détection des anomalies](media/anomaly-detection-scoping.png)

## <a name="triage-anomaly-detection-alerts"></a>Trier les alertes de détection des anomalies

Vous pouvez trier rapidement les diverses alertes déclenchées par les nouvelles stratégies de détection des anomalies et déterminer celles qui doivent être prises en charge en premier. Pour ce faire, vous avez besoin du contexte de l’alerte, ce qui vous permet de voir la plus grande image et de savoir si un problème malveillant se produit.

1. Dans le **Journal d’activité**, vous pouvez ouvrir une activité pour afficher le tiroir d’activité. Cliquez sur **utilisateur** pour afficher l’onglet Insights utilisateur. Cet onglet contient des informations telles que le nombre d’alertes, les activités et l’emplacement à partir duquel ils sont connectés, ce qui est important dans le cas d’une investigation.

    ![détection des anomalies alert1](media/anomaly-alert-user1.png) ![alert1 de détection des anomalies](media/anomaly-alert-user2.png)

1. Cela vous permet de comprendre ce que les activités suspectes sont effectuées par l’utilisateur et d’obtenir une confiance plus poussée quant à la compromission du compte. Par exemple, une alerte sur plusieurs échecs de connexion peut être suspecte et peut indiquer une attaque par force brute potentielle, mais il peut également s’agir d’une configuration inappropriée de l’application, provoquant ainsi un vrai positif sans gravité. Toutefois, si vous voyez une alerte plusieurs échecs de connexion avec des activités suspectes supplémentaires, il est plus probable que le compte soit compromis. Dans l’exemple ci-dessous, vous pouvez voir que l’alerte **plusieurs échecs de tentative de connexion** a été suivie d' **une activité à partir d’une adresse IP** et d’une **activité de voyage impossibles**, à la fois d’indicateurs forts de compromission (IOCs). Si cela n’était pas suffisamment suspect, vous pouvez voir que le même utilisateur a effectué une **activité de téléchargement de masse**, qui est souvent un indicateur de l’attaquant effectuant l’exfiltration des données.

    ![détection des anomalies alert1](media/anomaly-alert-user3.png)

1. Pour les fichiers infectés par des logiciels malveillants, une fois les fichiers détectés, vous pouvez voir la liste des **fichiers infectés**. Cliquez sur le nom du fichier de programme malveillant dans le tiroir de fichier pour ouvrir un rapport de programmes malveillants qui vous fournit des informations sur ce type de programme malveillant avec lequel le fichier est infecté.

## <a name="next-steps"></a>Étapes suivantes :

> [!div class="nextstepaction"]
> [Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
