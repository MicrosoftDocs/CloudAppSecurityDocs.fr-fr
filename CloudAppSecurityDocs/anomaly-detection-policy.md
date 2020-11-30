---
title: Créer une stratégie de détection des anomalies dans Cloud App Security
description: Cet article fournit une description des stratégies de détection des anomalies ainsi que des informations de référence sur les composantes d’une stratégie de détection des anomalies.
ms.date: 08/20/2020
ms.topic: how-to
ms.openlocfilehash: 6cddeb16149a61aa1099d4fe74c3423dbd45042f
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96314747"
---
# <a name="get-behavioral-analytics-and-anomaly-detection"></a>Bénéficiez d’une analyse comportementale et d’une détection des anomalies

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Les stratégies de détection des anomalies d’Microsoft Cloud App Security fournissent une analyse comportementale des utilisateurs et des entités (UEBA) et des Machine Learning (ML) prêts à l’emploi pour vous permettre d’exécuter la détection avancée des menaces dans votre environnement Cloud. Dans la mesure où elles sont automatiquement activées, les nouvelles stratégies de détection des anomalies démarrent immédiatement le processus de détection et de classement des résultats, ciblant de nombreuses anomalies comportementales au sein de vos utilisateurs, ainsi que les ordinateurs et les appareils connectés à votre réseau. En outre, les stratégies exposent plus de données à partir du moteur de détection Cloud App Security, afin de vous aider à accélérer le processus d’investigation et à contenir des menaces continues.

Les stratégies de détection des anomalies sont automatiquement activées, mais Cloud App Security comporte une période d’apprentissage initiale de sept jours, pendant laquelle les alertes de détection des anomalies ne sont pas toutes déclenchées. Après cela, à mesure que les données sont collectées à partir de vos connecteurs API configurés, chaque session est comparée à l’activité, lorsque les utilisateurs étaient actifs, les adresses IP, les appareils, etc. ont été détectés au cours du mois passé et le score de risque de ces activités. Sachez que la disponibilité des données à partir des connecteurs d’API peut prendre plusieurs heures. Ces détections font partie du moteur de détection des anomalies heuristique qui Profile votre environnement et déclenche des alertes en ce qui concerne une ligne de base qui a été appris sur l’activité de votre organisation. Ces détections utilisent également les algorithmes d’apprentissage automatique conçus pour profiler les utilisateurs et le modèle de connexion afin de réduire les faux positifs.

Ces anomalies sont détectées en analysant l’activité des utilisateurs. Le risque est évalué en examinant plus de 30 indicateurs de risque différents, regroupés en facteurs de risque, comme suit :

* Adresse IP à risque
* Échecs de connexion
* Activité administrative
* Comptes inactifs
* Emplacement
* Voyage impossible
* Agent Appareil et utilisateur
* Fréquence d'activité

Selon les résultats de la stratégie, des alertes de sécurité sont déclenchées. Cloud App Security examine chaque session utilisateur sur votre cloud et vous alerte en cas d’événement anormal par rapport aux activités de référence ou habituelles de votre organisation ou de l’utilisateur.

Outre les alertes de Cloud App Security natives, vous obtiendrez également les alertes de détection suivantes basées sur les informations reçues de la protection d’identité des Azure Active Directory (AD) :

* Informations d’identification divulguées : déclenché lorsque les informations d’identification valides d’un utilisateur ont été divulguées. Pour plus d’informations, consultez [détection des informations d’identification divulguées de Azure ad](/azure/active-directory/identity-protection/concept-identity-protection-risks#user-risk).
* Connexion risquée : combine un certain nombre de détections de connexion Azure AD Identity Protection en une seule détection. Pour plus d’informations, consultez [détection des risques de connexion de Azure ad](/azure/active-directory/identity-protection/concept-identity-protection-risks#sign-in-risk).

Ces stratégies s’affichent dans la page Cloud App Security les stratégies et peuvent être activées ou désactivées.

## <a name="anomaly-detection-policies"></a>Stratégie de détection des anomalies

Vous pouvez afficher les stratégies de détection des anomalies dans le portail en cliquant sur **Contrôle**, puis sur **Stratégies**. Sélectionnez **Stratégie de détection d’anomalie** pour le type de stratégie.

 ![nouvelles stratégies de détection des anomalies](media/new-anomaly-detection-policies.png)

Les stratégies de détection d’anomalie suivantes sont disponibles :

### <a name="impossible-travel"></a>Voyage impossible

* Cette détection identifie deux activités de l’utilisateur (dans une seule ou plusieurs sessions) provenant d’emplacements éloignés sur le plan géographique au cours d’une période plus courte que la durée nécessaire à l’utilisateur pour aller du premier emplacement au second, indiquant qu’un autre utilisateur utilise les mêmes informations d’identification. Cette détection utilise un algorithme d’apprentissage automatique qui ignore les « faux positifs » évidents contribuant à la condition de voyage impossible, comme les réseaux privés virtuels et les emplacements régulièrement utilisés par d’autres utilisateurs de l’organisation. La détection a une période d’apprentissage initiale de sept jours au cours de laquelle elle apprend le modèle d’activité d’un nouvel utilisateur. La détection de voyage impossible identifie l’activité utilisateur inhabituelle et impossible entre deux emplacements. L’activité doit être suffisamment inhabituelle pour être considérée comme un indicateur de compromission et justifier le déclenchement d’une alerte. Pour que cela fonctionne, la logique de détection inclut différents niveaux de suppression pour répondre aux besoins des scénarios susceptibles de déclencher des « faux positifs », comme les activités des réseaux privés virtuels. Le curseur de sensibilité vous permet d’agir sur l’algorithme et de définir une logique de détection plus ou moins stricte. Plus le niveau de sensibilité est élevé, plus le niveau de suppression appliqué dans le cadre de la logique de détection est bas. De cette façon, vous pouvez adapter la détection en fonction de vos besoins de couverture et de vos cibles SNR.

    > [!NOTE]
    > Lorsque les adresses IP des deux côtés du trajet sont considérées comme sûres, le voyage est approuvé et exclu du déclenchement de la détection de voyage impossible. Par exemple, les deux côtés sont considérés comme sécurisés s’ils sont [marqués comme entreprise](ip-tags.md). Toutefois, si l’adresse IP d’un seul côté du trajet est considérée comme sécurisée, la détection est déclenchée normalement.

### <a name="activity-from-infrequent-country"></a>Activité à partir de pays peu fréquents

* Cette détection prend en compte les emplacements d’activité précédents pour déterminer les emplacements nouveaux et peu fréquents. Le moteur de détection d’anomalies stocke des informations sur les emplacements précédents utilisés par les utilisateurs de l’organisation. Une alerte est déclenchée quand une activité se produit à partir d’un emplacement qui n’a pas été récemment visité ou qui ne l’a jamais été par un utilisateur de l’organisation.

### <a name="malware-detection"></a>Détection de logiciel malveillant

* Cette détection identifie les fichiers malveillants dans votre stockage cloud, qu’ils viennent de vos applications Microsoft ou tierces. Microsoft Cloud App Security utilise la Threat Intelligence de Microsoft pour savoir si certains fichiers sont associés à des attaques par programme malveillant connues et s’ils sont potentiellement dangereux. Cette stratégie intégrée est désactivée par défaut. Les fichiers ne sont pas tous analysés, mais des solutions sont utilisées pour rechercher les fichiers qui présentent un risque potentiel. Une fois que les fichiers sont détectés, vous pouvez voir une liste des **fichiers infectés**. Cliquez sur le nom du fichier de programme malveillant dans le tiroir de fichier pour ouvrir un rapport de programmes malveillants qui vous fournit des informations sur le type de programme malveillant avec lequel le fichier est infecté.

    Vous pouvez utiliser cette détection en temps réel à l’aide de stratégies de session pour contrôler les chargements de fichiers et les téléchargements.

    > [!NOTE]
    >
    > Cloud App Security prend en charge la détection de programmes malveillants pour les applications suivantes :
    >
    > * Box
    > * Dropbox
    > * G Suite
    > * Office 365 (nécessite une licence valide pour Microsoft Defender pour Office 365 P1)

### <a name="activity-from-anonymous-ip-addresses"></a>Activité depuis des adresses IP anonymes

* Cette détection identifie que les utilisateurs étaient actifs depuis une adresse IP qui a été identifiée comme une adresse IP de proxy anonyme. Ces proxys sont utilisés par les personnes qui souhaitent masquer l’adresse IP de leur appareil et peuvent être utilisés à des fins malveillantes. Cette détection utilise un algorithme d’apprentissage automatique qui réduit les « faux positifs », comme les adresses IP mal balisées qui sont couramment utilisées par les utilisateurs de l’organisation.

### <a name="ransomware-activity"></a>Activité ransomware

* Cloud App Security a étendu ses fonctionnalités de détection de ransomware à la détection d’anomalies pour garantir une couverture plus complète contre les attaques par ransomware sophistiqué. Grâce à notre expertise en matière de recherche sur la sécurité pour identifier des modèles de comportement qui reflètent l’activité des ransomware, Cloud App Security garantit une protection holistique et robuste. Si Cloud App Security identifie, par exemple, un taux élevé de chargements de fichiers ou d’activités de suppression de fichiers, cela peut représenter un processus de chiffrement indésirable. Ces données sont collectées dans les journaux reçus des API connectées, puis combinées avec des modèles comportementaux appris et des informations sur les menaces, par exemple, des extensions de ransomware. Pour plus d’informations sur la manière dont Cloud App Security détecte les ransomwares, consultez [Protection de votre organisation contre les ransomwares](use-case-ransomware.md).

### <a name="activity-performed-by-terminated-user"></a>Activité effectuée par utilisateur résilié

* Cette détection permet de déterminer si un employé en fin de contrat continue d’effectuer des actions sur vos applications SaaS. Étant donné que les données montrent que le plus grand risque de menaces internes vient des employés partis en mauvais termes, il est important de garder un œil sur l’activité des comptes des employés dont le contrat de travail est terminé. Parfois, quand un employé quitte une entreprise, son compte est déprovisionné des applications d’entreprise, mais dans de nombreux cas, il conserve quand même un accès à certaines ressources de l’entreprise. Ces menaces sont encore plus importantes quand il s’agit de comptes privilégiés, puisque le risque de dommage causé par un ancien administrateur est par définition plus élevé.
Cette détection exploite la capacité de Cloud App Security à surveiller le comportement de l’utilisateur dans toutes les applications, ce qui permet d’identifier l’activité normale de l’utilisateur, le fait que le compte a été résilié et l’activité réelle dans d’autres applications. Par exemple, un employé qui est Azure AD compte a été mis fin, mais qui a toujours accès à l’infrastructure AWS de l’entreprise, a la possibilité de provoquer des dégâts à grande échelle.

La détection recherche les utilisateurs dont le compte a été clôturé dans Azure AD, mais qui effectuent encore des activités sur d’autres plateformes comme AWS ou Salesforce. Cela est particulièrement pertinent pour les utilisateurs qui utilisent un autre compte (pas leur compte d’authentification unique principal) pour gérer les ressources, étant donné que ces comptes ne sont souvent pas clôturés lorsqu’un utilisateur quitte l’entreprise.

### <a name="activity-from-suspicious-ip-addresses"></a>Activité à partir d'adresses IP suspectes

* Cette détection identifie que des utilisateurs étaient actifs à partir d’une adresse IP qui a été identifiée comme à risque par Microsoft Threat Intelligence. Ces adresses IP sont impliquées dans des activités malveillantes, comme Botnet C&C, et peuvent être le signe de compte compromis. Cette détection utilise un algorithme d’apprentissage automatique qui réduit les « faux positifs », comme les adresses IP mal balisées qui sont couramment utilisées par les utilisateurs de l’organisation.

### <a name="suspicious-inbox-forwarding"></a>Transfert de boîte de réception suspect

* Cette détection recherche les règles de transfert des e-mails suspects, par exemple, si un utilisateur a créé une règle de boîte de réception assurant le transfert d’une copie de tous les e-mails à une adresse externe.

> [!NOTE]
> Cloud App Security vous avertit seulement pour chaque règle de transfert qui est identifiée comme suspecte, en fonction du comportement habituel pour l’utilisateur.

### <a name="suspicious-inbox-manipulation-rules"></a>Règles suspectes de manipulation de boîte de réception

* Cette détection dresse le profil de votre environnement et déclenche des alertes lorsque des règles suspectes qui suppriment ou déplacent des messages ou des dossiers sont définies dans la boîte de réception d'un utilisateur. Cela peut indiquer que le compte de l’utilisateur est compromis, que des messages sont intentionnellement masqués et que la boîte aux lettres est utilisée pour distribuer du courrier indésirable ou des programmes malveillants dans votre organisation.

### <a name="suspicious-email-deletion-activity-preview"></a>Activité de suppression des e-mails suspects (version préliminaire)

* Cette stratégie Profile votre environnement et déclenche des alertes lorsqu’un utilisateur effectue des activités de suppression d’e-mails suspectes dans une seule session. Cette stratégie peut indiquer que les boîtes aux lettres d’un utilisateur peuvent être compromises par des vecteurs d’attaque potentiels tels que la communication de commande et de contrôle (C&C/C2) par courrier électronique.

> [!NOTE]
> Cloud App Security s’intègre à Office-protection avancée contre les menaces (Office ATP) pour assurer la protection d’Exchange Online, y compris la détonation d’URL, la protection contre les programmes malveillants, etc. Une fois qu’Office ATP est activé, vous pouvez commencer à voir les alertes dans le journal d’activité Cloud App Security.

### <a name="suspicious-oauth-app-file-download-activities"></a>Activités suspectes de téléchargement de fichiers d’application OAuth

* Analyse les applications OAuth connectées à votre environnement et déclenche une alerte lorsqu’une application télécharge plusieurs fichiers à partir de Microsoft SharePoint ou Microsoft OneDrive d’une manière inhabituelle pour l’utilisateur. Cela peut indiquer que le compte d’utilisateur est compromis.

### <a name="unusual-activities-by-user"></a>Activités inhabituelles (par utilisateur)

Ces détections identifient les utilisateurs dans les cas suivants :

* Plusieurs activités inhabituelles de téléchargement de fichiers
* Activités inhabituelles de partage de fichiers
* Activités inhabituelles de suppression de fichiers
* Activités inhabituelles d'emprunt d'identité
* Activités administratives inhabituelles
* Activités de partage de rapport Power BI inhabituelles (version préliminaire)
* Activités de création de plusieurs machines virtuelles inhabituelles (version préliminaire)
* Activités de suppression de plusieurs stockages inhabituelles (version préliminaire)
* Région inhabituelle pour la ressource Cloud (version préliminaire)

Ces stratégies recherchent les activités dans une seule session en prenant en compte la base de référence apprise, ce qui peut indiquer une tentative de violation. Ces détections s’appuient sur un algorithme d’apprentissage automatique qui profile le modèle de connexion des utilisateurs et réduit les « faux positifs ». Ces détections font partie du moteur de détection des anomalies heuristique qui Profile votre environnement et déclenche des alertes en ce qui concerne une ligne de base qui a été appris sur l’activité de votre organisation.

### <a name="multiple-failed-login-attempts"></a>Plusieurs tentatives de connexion infructueuses

* Cette détection identifie des utilisateurs qui tentent de se connecter plusieurs fois sans succès dans une seule session en prenant en compte la base de référence apprise, ce qui peut indiquer une tentative de violation.

### <a name="data-exfiltration-to-unsanctioned-apps"></a>Exfiltration de données vers des applications non approuvées

* Cette stratégie est activée automatiquement pour vous avertir quand un utilisateur ou une adresse IP utilise une application qui n’est pas approuvée pour effectuer une activité qui ressemble à une tentative d’exfiltration des informations en dehors de votre organisation.

### <a name="multiple-delete-vm-activities"></a>Plusieurs activités de suppression de machine virtuelle

* Cette stratégie profile votre environnement et déclenche des alertes quand des utilisateurs suppriment plusieurs machines virtuelles dans une même session, relativement à la base de référence de votre organisation. Ceci peut indiquer une tentative de violation.

## <a name="enable-automated-governance"></a>Activer la gouvernance automatisée<a name="adp-automated-gov"></a>

Vous pouvez lancer des actions de correction automatisées sur les alertes générées par les stratégies de détection d’anomalie.

1. Cliquez sur le nom de la stratégie de détection dans la page **Stratégie**.
1. Dans la fenêtre **Modifier la stratégie de détection d’anomalie** qui s’ouvre, sous **Gouvernance**, définissez les actions de correction que vous souhaitez pour chaque application connectée ou pour toutes les applications.
1. Cliquez sur **Update**.

## <a name="tune-anomaly-detection-policies"></a>Paramétrage des stratégies de détection d’anomalie

Pour que le moteur de détection d’anomalie supprime ou déclenche des alertes en fonction de vos préférences :

* Dans la stratégie de voyage impossible, vous pouvez définir le curseur de sensibilité afin de déterminer le niveau de comportement anormal nécessaire pour déclencher une alerte. Par exemple, si vous la définissez sur faible, cela supprime les alertes de voyage impossibles à partir des emplacements communs d’un utilisateur et, si vous la définissez sur élevé, cela entraîne des alertes. Vous avez le choix entre les niveaux de sensibilité suivants :

  * **Faible**: suppressions du système, du locataire et de l’utilisateur
  * **Moyenne** : Suppression du système et de l’utilisateur
  * **Élevée** : Suppression du système uniquement

    Où :

    | Type de suppression | Description |
    | --- | --- |
    | **Système** | Détections intégrées qui sont toujours supprimées. |
    | **Locataire** | Activités courantes selon l’historique d’activité dans le locataire. Par exemple, la suppression d’activités d’un fournisseur de services Internet ayant déjà fait l’objet d’une alerte au sein de votre organisation. |
    | **Utilisateur** | Activités courantes selon l’historique d’activité de l’utilisateur. Par exemple, la suppression d’activités provenant d’un emplacement couramment utilisé par l’utilisateur. |

* Vous pouvez également configurer si les alertes relatives à l’activité à partir d’un pays/d’une région peu fréquent, d’adresses IP anonymes, d’adresses IP suspectes et de voyages impossibles doivent analyser les connexions ayant échoué ou réussi ou simplement les connexions.

> [!NOTE]
> Par défaut, les protocoles de connexion hérités, tels que ceux qui n’utilisent pas multi-Factor Authentication (par exemple, WS-Trust), ne sont pas contrôlés par la stratégie de voyage impossible. Si votre organisation utilise des protocoles hérités, pour éviter les activités pertinentes manquantes, modifiez la stratégie et, sous **Configuration avancée**, définissez **analyser les activités de connexion** à **toutes les connexions**.

## <a name="scope-anomaly-detection-policies"></a>Délimiter des stratégies de détection d’anomalie

Chaque stratégie de détection d’anomalie peut être délimitée indépendamment. Vous pouvez donc inclure et exclure les utilisateurs et les groupes de votre choix.
Par exemple, sous Activité, vous pouvez définir la détection d’une région rare ou ignorer un utilisateur spécifique qui voyage fréquemment.

Pour délimiter une stratégie de détection d’anomalie :

1. Cliquez sur stratégies de **contrôle**  >  **Policies** et définissez le filtre de **type** sur la **stratégie de détection d’anomalie**.
1. Cliquez sur la stratégie que vous souhaitez délimiter.
1. Sous **Étendue**, dans la liste déroulante, remplacez la valeur par défaut **Tous les utilisateurs et groupes** par **Utilisateurs et groupes spécifiques**.
1. Sélectionnez **Inclure** pour spécifier les utilisateurs et les groupes auxquels s’applique cette stratégie. Les utilisateurs ou les groupes qui ne sont pas sélectionnés ici ne seront pas considérés comme une menace et ne généreront pas d’alerte.
1. Sélectionnez **Exclure** pour spécifier les utilisateurs pour lesquels cette stratégie ne s’applique pas. Les utilisateurs sélectionnés ici ne seront pas considérés comme une menace et ne généreront pas d’alerte, même s’ils sont membres de groupes qui ont été sélectionnés sous **Inclure**.

    ![Délimitation des stratégies de détection d’anomalie](media/anomaly-detection-scoping.png)

## <a name="triage-anomaly-detection-alerts"></a>Alertes de détection des anomalies de triage

Vous pouvez trier rapidement les diverses alertes déclenchées par les nouvelles stratégies de détection des anomalies afin de déterminer celles qui doivent être prises en charge en priorité. Pour cela, vous avez besoin du contexte de l’alerte, afin de pouvoir obtenir une vue plus globale et identifier si une action malveillante se produit effectivement.

1. Dans le **journal d’activité**, vous pouvez ouvrir une activité afin d’afficher son contenu. Cliquez sur **utilisateur** pour afficher l’onglet Insights utilisateur. Cet onglet contient des informations telles que le nombre d’alertes, les activités et l’emplacement à partir duquel ils sont connectés, ce qui est important dans le cas d’une investigation.

    ![détection d’anomalie alert1 ](media/anomaly-alert-user1.png) ![ détection d’anomalies alert2](media/anomaly-alert-user2.png)

1. Cela vous permet d’identifier les activités suspectes que l’utilisateur a effectuées et d’obtenir ainsi plus d’indices démontrant que le compte a été compromis. Par exemple, une alerte sur plusieurs échecs de connexion peut en effet être suspecte et indiquer une éventuelle attaque par force brute, mais elle peut également signaler un problème de configuration d’application, transformant cette alerte en un « faux positif » bénin. Mais si vous voyez une alerte d’échecs de connexion pour d’autres activités suspectes, la probabilité que le compte est compromis augmente. Dans l’exemple ci-dessous, vous pouvez voir que l’alerte **Plusieurs tentatives de connexion infructueuses** a été suivie par les alertes **Activité à partir d’une adresse IP TOR** et **Activité de type Voyage impossible**, deux indicateurs flagrants d’une compromission (IOCs). Si cela n’était pas suffisamment suspect, vous pouvez voir que le même utilisateur a effectué une **activité de téléchargement de masse**, qui est souvent un indicateur de l’attaquant effectuant l’exfiltration des données.

    ![détection des anomalies alert3](media/anomaly-alert-user3.png)

1. Une fois que les fichiers infectés sont détectés, vous pouvez voir une liste des **fichiers infectés**. Cliquez sur le nom du fichier malveillant dans le tiroir de fichier pour ouvrir un rapport sur les programmes malveillants qui vous fournit des informations sur le type de programme malveillant dont le fichier est infecté.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
