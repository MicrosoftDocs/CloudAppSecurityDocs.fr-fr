---
title: Détection des activités suspectes des utilisateurs avec l’analyse comportementale (UEBA)
description: Ce tutoriel décrit le processus de paramétrage des détections d’activité utilisateur dans Microsoft Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 05/10/2020
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: galz
ms.suite: ems
ms.openlocfilehash: bdf58b83e01dc6ab088d3956f2a71ef52f368438
ms.sourcegitcommit: 575f2b2efa9ca4477d7e60271d21e225ef2c38ea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90881183"
---
# <a name="tutorial-detect-suspicious-user-activity-with-ueba"></a>Tutoriel : Détection des activités suspectes des utilisateurs avec UEBA

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Microsoft Cloud App Security assure des détections optimales sur toute la chaîne cybercriminelle des attaques pour les utilisateurs compromis, les menaces internes, les exfiltrations, les ransomware et plus encore. Notre solution complète combine plusieurs méthodes de détection, notamment la détection d’anomalie, l’analyse comportementale (UEBA) et des détections d’activités basées sur les règles, pour fournir une vue d’ensemble de l’usage que font vos utilisateurs des applications de votre environnement.

Pourquoi est-il important de détecter les comportements suspects ? L’impact d’un utilisateur capable de modifier votre environnement cloud peut être significatif, y compris sur votre capacité à gérer votre activité. Des ressources clés de l’entreprise, comme les serveurs qui font tourner votre site web ou le service que vous fournissez aux clients, peuvent être compromises.

Cloud App Security analyse des données capturées à partir de plusieurs sources pour en extraire les activités des applications et des utilisateurs de votre organisation, ce qui permet à vos analystes de sécurité de mieux visualiser l’utilisation du cloud. Les données collectées sont corrélées, standardisées et enrichies avec le renseignement sur les menaces, l’emplacement et bien d’autres informations pour fournir une vue précise et cohérente des activités suspectes.

Pour tirer pleinement parti des avantages de ces détections, veillez à configurer les sources suivantes :

* **[Journal d’activité](activity-filters.md)**  
Activités de vos [applications connectées API](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).
* **[Journal de détection](tutorial-shadow-it.md)**  
Activités extraites des journaux de trafic du pare-feu et du proxy qui sont transférés à Cloud App Security. Les journaux sont analysés par rapport au [catalogue d’applications cloud](risk-score.md), classés et évalués en fonction de plus de 80 facteurs de risque.
* **[Journal du proxy](proxy-intro-aad.md)**  
Activités de vos [applications de contrôle d’application par accès conditionnel](tutorial-proxy.md#phase-1-monitor-user-activities-for-anomalies).

Ensuite, vous devez paramétrer vos stratégies. Les stratégies suivantes peuvent être ajustées en définissant des filtres et des seuils dynamiques (UEBA) pour faciliter l’apprentissage de leurs modèles de détection, ainsi que des suppressions pour réduire les détections courantes de faux positifs :

* Détection d’anomalie
* Détection d’anomalie Cloud Discovery
* Détection d’activité basée sur les règles

Ce tutoriel donne des instructions de paramétrage des détections d’activité utilisateur dans le but d’identifier les compromissions véritables et de réduire la multiplication des alertes due à la gestion de gros volumes de détections de faux positifs.

> [!div class="checklist"]
>
> * Configuration des plages d’adresses IP
> * Paramétrage des stratégies de détection d’anomalie
> * Paramétrage des stratégies de détection d’anomalie Cloud Discovery
> * Paramétrage des stratégies de détection basées sur les règles
> * Configuration des alertes
> * Examen et correction

## <a name="phase-1-configure-ip-address-ranges"></a>Phase 1 : Configuration des plages d’adresses IP

Avant de configurer des stratégies individuelles, il est recommandé de configurer des plages d’adresses IP de sorte qu’elles puissent être utilisées pour ajuster n’importe quel type de stratégie de détection des activités suspectes des utilisateurs.

Dans la mesure où les informations d’adresse IP sont essentielles pour la quasi-totalité des investigations, la [configuration des adresses IP connues](ip-tags.md) aide nos algorithmes Machine Learning à identifier les emplacements connus et à les prendre en compte dans le cadre des modèles Machine Learning. Par exemple, en ajoutant la plage d’adresses IP de votre VPN, vous permettrez au modèle de la classer correctement et de l’exclure automatiquement des détections de voyage impossible, car l’emplacement VPN ne représente pas l’emplacement réel de cet utilisateur.

Remarque :  Les plages d’adresses IP configurées ne se limitent pas aux détections : elles sont utilisées dans l’ensemble de Cloud App Security, dans des domaines comme les activités du journal d’activité, l’accès conditionnel, etc. Gardez cela à l’esprit lorsque vous configurez les plages. Par exemple, l’identification des adresses IP physiques de votre bureau vous permet de personnaliser la façon dont les journaux et les alertes sont affichés et examinés.

### <a name="review-out-of-the-box-anomaly-detection-alerts"></a>Vérification des alertes de détection d’anomalie prêtes à l’emploi

Cloud App Security comprend un ensemble d’alertes de détection d’anomalie permettant d’identifier différents scénarios de sécurité. Ces détections, prêtes à l’emploi et automatiquement activées, commencent à profiler l’activité des utilisateurs et à générer des alertes dès que les [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md) concernés sont connectés.

Commencez par vous familiariser avec les [différentes stratégies de détection](control-cloud-apps-with-policies.md), traitez en priorité les grands scénarios les plus pertinents pour votre organisation et paramétrez les stratégies en conséquence.

## <a name="phase-2-tune-anomaly-detection-policies"></a>Phase 2 : Paramétrage des stratégies de détection d’anomalie

Plusieurs stratégies intégrées de détection d’anomalie disponibles dans Cloud App Security sont préconfigurées pour les cas d’utilisation de sécurité courants. Prenez le temps de vous familiariser avec les détections les plus utilisées :

* **Voyage impossible**  
Activités d’un même utilisateur se trouvant à différents emplacements au cours d’une période plus courte que le temps de trajet attendu entre les deux.
* **Activité à partir de pays peu fréquents**  
Activité provenant d’un emplacement qui n’a été visité (récemment) par aucun utilisateur de l’organisation.
* **Détection de logiciel malveillant**  
Analyse les fichiers de vos applications cloud et traite les fichiers suspects avec le moteur de renseignement sur les menaces de Microsoft afin de déterminer s’ils sont associés à des programmes malveillants connus.
* **Activité ransomware**  
Chargement sur le cloud de fichiers susceptibles d’être infectés par un ransomware.
* **Activité à partir d'adresses IP suspectes**  
Activité provenant d’une adresse IP identifiée comme à risque par Microsoft Threat Intelligence.
* **Transfert de boîte de réception suspect**  
Détecte les règles de transfert de boîte de réception suspect définies dans la boîte de réception d’un utilisateur.
* **Activités inhabituelles de téléchargement de plusieurs fichiers**  
Détecte les activités de téléchargement de plusieurs fichiers au cours d’une même session par rapport à la base de référence apprise, susceptibles d’indiquer une tentative de violation.
* **Activités administratives inhabituelles**  
Détecte les activités administratives multiples au cours d’une même session par rapport à la base de référence apprise, susceptibles d’indiquer une tentative de violation.

Pour connaître la liste complète des détections et leur rôle, consultez [Stratégies de détection d’anomalie](anomaly-detection-policy.md#anomaly-detection-policies).

Après avoir pris connaissance des stratégies, réfléchissez à la façon dont vous souhaitez les adapter aux besoins spécifiques de votre organisation afin de mieux cibler les activités à approfondir.

1. **Étendre les stratégies à des utilisateurs ou à des groupes spécifiques**

    Des stratégies couvrant des utilisateurs spécifiques contribuent à réduire le bruit provenant d’alertes non pertinentes pour votre organisation. Chaque stratégie peut être [configurée de façon à inclure ou exclure des utilisateurs et des groupes spécifiques](anomaly-detection-policy.md#scope-anomaly-detection-policies), comme dans les exemples suivants :

    * **Simulations d’attaques**  
    De nombreuses organisations ont recours à un utilisateur ou à un groupe pour simuler en permanence des attaques. Il n’est évidemment pas judicieux de recevoir constamment des alertes provenant des activités de ces utilisateurs. Par conséquent, vous pouvez configurer vos stratégies de façon à exclure ces utilisateurs ou ces groupes. Par ailleurs, les modèles Machine Learning peuvent ainsi identifier ces utilisateurs et ajuster leurs seuils dynamiques en conséquence.
    * **Détections ciblées**  
    Votre organisation souhaite peut être examiner un groupe spécifique d’utilisateurs VIP, comme les membres d’un groupe d’administrateurs ou de CXO. Dans ce scénario, vous pouvez créer une stratégie pour les activités que vous souhaitez détecter et choisir d’inclure uniquement l’ensemble d’utilisateurs ou de groupes qui vous intéresse.

2. **Paramétrer les détections d’anomalie de connexion**

    Certaines organisations souhaitent voir les alertes résultant [d’activités d’échec de connexion](anomaly-detection-policy.md#multiple-failed-login-attempts), susceptibles d’indiquer que quelqu’un tente de cibler un ou plusieurs comptes d’utilisateur. En revanche, des attaques par force brute sur des comptes d’utilisateur se produisent tout le temps dans le cloud, sans que les entreprises aient le moyen de les empêcher. C’est pourquoi les grandes organisations décident généralement de ne recevoir des alertes que pour les activités de connexion suspecte ayant abouti, car ces dernières peuvent représenter de vraies compromissions.

    L’usurpation d’identité est une grande source de compromission, qui constitue un vecteur de menace majeur pour l’organisation. Nos alertes de détection [voyage impossible](anomaly-detection-policy.md#impossible-travel), [adresses IP anonymes](anomaly-detection-policy.md#activity-from-anonymous-ip-addresses) et [pays peu fréquents](anomaly-detection-policy.md#activity-from-infrequent-country) aident à découvrir les activités qui suggèrent qu’un compte est potentiellement compromis. Il peut être intéressant de personnaliser ces stratégies pour se concentrer uniquement sur les connexions réussies qui indiquent une menace actionnable imminente, afin de prendre rapidement des mesures à leur sujet. Par exemple, vous pouvez personnaliser la stratégie de pays peu fréquent de sorte qu’elle ne signale que les connexions réussies provenant d’emplacements qui n’ont été visités récemment par aucun utilisateur de votre organisation. Pour cela, [modifiez la stratégie](anomaly-detection-policy.md#tune-anomaly-detection-policies) et, sous Configuration avancée, définissez Analyser les activités de connexion sur l’une des options de connexion réussie.

3. **Paramétrer la sensibilité du [voyage impossible](anomaly-detection-policy.md#impossible-travel)** 
   [Configurez le curseur de sensibilité](anomaly-detection-policy.md#tune-anomaly-detection-policies), qui détermine le niveau des suppressions appliquées au comportement anormal avant de déclencher une alerte de voyage impossible. Par exemple, les organisations intéressées par la haute fidélité peuvent augmenter le niveau de sensibilité. À l’inverse, si votre organisation comprend de nombreux utilisateurs itinérants, envisagez de réduire le niveau de sensibilité pour supprimer les activités des emplacements courants de l’utilisateur, qui ont été appris des activités précédentes. Vous avez le choix entre les niveaux de sensibilité suivants :

    * **Faible** : Suppression du système, du locataire et de l’utilisateur
    * **Moyenne** : Suppression du système et de l’utilisateur
    * **Élevée** : Suppression du système uniquement

    Où :

    | Type de suppression | Description |
    | --- | --- |
    | **Système** | Détections intégrées qui sont toujours supprimées. |
    | **Locataire** | Activités courantes selon l’historique d’activité dans le locataire. Par exemple, la suppression d’activités d’un fournisseur de services Internet ayant déjà fait l’objet d’une alerte au sein de votre organisation. |
    | **Utilisateur** | Activités courantes selon l’historique d’activité de l’utilisateur. Par exemple, la suppression d’activités provenant d’un emplacement couramment utilisé par l’utilisateur. |

## <a name="phase-3-tune-cloud-discovery-anomaly-detection-policies"></a>Phase 3 : Paramétrage des stratégies de détection d’anomalie Cloud Discovery

Comme pour les stratégies de détection d’anomalie, il existe plusieurs [stratégies intégrées de détection d’anomalie Cloud Discovery](cloud-discovery-anomaly-detection-policy.md) qui peuvent être ajustées. Par exemple, la stratégie d’exfiltration des données vers des applications non approuvées, qui envoie une alerte lorsque des données sont exfiltrées vers une application non approuvée, est préconfigurée avec des paramètres qui s’appuient sur l’expérience de Microsoft dans le domaine de la sécurité.

Toutefois, vous pouvez ajuster les stratégies intégrées ou créer vos propres stratégies pour mieux identifier d’autres scénarios qui vous intéressent. Comme elles se basent sur des journaux Cloud Discovery, ces stratégies offrent des [possibilités de paramétrage](cloud-discovery-anomaly-detection-policy.md#cloud-discovery-anomaly-detection-policy-reference) différentes, plus axées sur le comportement anormal des applications et sur l’exfiltration des données.

1. **Paramétrer l’analyse de l’utilisation**  
Définissez les filtres d’utilisation pour contrôler la base de référence, la portée et la période d’activité de la détection des comportements anormaux. Par exemple, vous pouvez recevoir des alertes en cas d’activité anormale liée aux employés membres de la direction.

2. **Paramétrer la sensibilité des alertes**  
Pour empêcher la multiplication des alertes, configurez leur sensibilité. Vous pouvez utiliser le curseur de sensibilité pour contrôler le nombre d’alertes à haut risque envoyées par 1 000 utilisateurs par semaine. Plus la sensibilité est élevée, plus l’écart nécessaire pour être considéré comme une anomalie est faible et plus il y a d’alertes générées. En règle générale, définissez une faible sensibilité pour les utilisateurs qui n’ont pas accès à des données confidentielles.

## <a name="phase-4-tune-rule-based-detection-activity-policies"></a>Phase 4 : Paramétrage des stratégies (d’activité) de détection basées sur les règles

Les [stratégies de détection basée sur les règles](user-activity-policies.md) offrent la possibilité de compléter les stratégies de détection d’anomalie avec des exigences propres à l’organisation. Nous recommandons, pour créer des stratégies de ce type, d’utiliser l’un de nos modèles de stratégie d’activité (accédez à **Contrôle** > **Modèles** et définissez le filtre **Type** sur **Stratégie d’activité**), puis de [le configurer](activity-filters-queries.md) de façon à détecter les comportements qui ne sont pas normaux pour votre environnement. Par exemple, dans le cas d’une organisation non présente dans un pays ou une région spécifique, il peut être judicieux de créer une stratégie qui détecte les activités anormales provenant de ce pays et envoie une alerte à ce sujet. Pour d’autres, qui disposent de grandes succursales dans ce pays, les activités de ce pays sont normales ; il n’est donc pas pertinent de les détecter.

1. **Paramétrer le volume d’activité**  
Choisissez le volume d’activité nécessaire pour que la détection déclenche une alerte. Dans notre exemple, si votre organisation n’est pas présente dans un pays ou une région, même une seule activité est importante et justifie une alerte. Toutefois, un seul échec de connexion peut provenir d’une erreur humaine et ne présenter d’intérêt que si de nombreux échecs surviennent sur une courte période.
2. **Paramétrer les [filtres d’activité](activity-filters-queries.md)**  
Définissez les filtres dont vous avez besoin pour détecter le type d’activité sur lequel vous souhaitez recevoir une alerte. Par exemple, pour détecter l’activité provenant d’un pays, utilisez le paramètre **Emplacement**.
3. **Paramétrer les alertes**  
Pour empêcher la multiplication des alertes, définissez la **limite journalière d’alertes**.

## <a name="phase-5-configure-alerts"></a>Phase 5 : Configuration des alertes

Vous pouvez choisir de recevoir des alertes dans le format et sur le support les plus adaptés à vos besoins. Pour obtenir des alertes immédiates à tout moment de la journée, il peut être préférable de les recevoir par e-mail ou par SMS.

Vous souhaiterez peut-être également analyser les alertes dans le contexte d’autres alertes déclenchées par d’autres produits de votre organisation afin d’obtenir une vision globale d’une menace potentielle. Par exemple, vous pouvez mettre en corrélation des événements cloud et locaux pour voir s’il existe d’autres preuves d’atténuation susceptibles de confirmer une attaque.

Il est également possible de déclencher l’automatisation des alertes personnalisées grâce à notre intégration avec [Microsoft Power Automate](flow-integration.md). Par exemple, vous pouvez configurer un playbook de façon à créer automatiquement un problème dans [ServiceNow](/connectors/service-now/) ou à envoyer un e-mail d’approbation pour exécuter une action de gouvernance personnalisée lorsqu’une alerte est déclenchée.

Suivez les instructions suivantes pour configurer vos alertes :

1. **E-mail/SMS**  
Choisissez votre préférence de distribution pour recevoir des alertes : par e-mail, par SMS ou les deux.
2. **SIEM**  
Il existe plusieurs options d’intégration SIEM, notamment [Azure Sentinel](siem-sentinel.md), [l’API Microsoft Graph Security](/graph/security-integration#list-of-connectors-from-microsoft) et d’autres [SIEM génériques](siem.md). Choisissez celle qui répond le mieux à vos besoins.
3. **Automatisation Power Automate**  
Créez les playbooks d’automatisation dont vous avez besoin et définissez-les comme alertes de la stratégie pour l’action Power Automate.

## <a name="phase-6-investigate-and-remediate"></a>Phase 6 : Examen et correction

Maintenant que vous avez configuré vos stratégies, vous commencez à recevoir des alertes d’activité suspecte. Qu’en faire ? Pour commencer, vous devez prendre les mesures nécessaires pour examiner l’activité. Vous pouvez par exemple examiner les activités qui indiquent [qu’un utilisateur a été compromis](tutorial-ueba.md#identify).

Pour optimiser votre protection, envisagez de configurer des actions de correction automatique afin de réduire le risque pour votre organisation. Nos stratégies vous permettent d’appliquer des [actions de gouvernance](control.md) conjointement avec les alertes de sorte à limiter ce risque même avant de commencer l’examen. Les actions disponibles, notamment la suspension d’un utilisateur ou le blocage de l’accès à la ressource demandée, sont déterminées par le type de stratégie.

[!INCLUDE [Open support ticket](includes/support.md)]
