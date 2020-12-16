---
title: Gérer la sécurité des plateformes cloud utilisées par votre organisation
description: Ce tutoriel explique comment utiliser Microsoft Cloud App Security pour sécuriser vos plateformes cloud Azure, AWS et GCP.
ms.date: 09/17/2020
ms.topic: tutorial
ms.openlocfilehash: dfdff2b5b124ee9ea9d5fe4822196fa42cbe9f0a
ms.sourcegitcommit: 72ddcd0f9a83251d588009abf506676612c50267
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2020
ms.locfileid: "97370158"
---
# <a name="tutorial-manage-cloud-platform-security"></a>Tutoriel : Gérer la sécurité des plateformes cloud

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Le travail à distance conduit souvent à une utilisation intensive d’applications et de plateformes cloud pour accomplir des tâches métier courantes, d’où la nécessité de sécuriser les environnements cloud et l’adoption de produits de sécurité pour le cloud. Selon le [modèle de responsabilité partagée](/azure/security/fundamentals/shared-responsibility), une organisation est responsable de la gestion et de la sécurisation de sa plateforme cloud : gestion des identités et des accès (IAM), machines virtuelles et leurs ressources de calcul, données et emplacements de stockage, ressources réseau, etc.

![Sécurisation de votre environnement multicloud](media/tutorial-cloud-platform-security.png)

## <a name="how-does-security-posture-management-help"></a>En quoi la gestion de la posture de sécurité est-elle utile ?

La mise en place d’outils de sécurité appropriés pour protéger les ressources qui n’ont peut-être pas été correctement protégées est essentielle. Les organisations doivent bénéficier d’une visibilité sur la posture de leurs ressources cloud, disposer de fonctionnalités de découverte pour connaître l’utilisation réelle de chaque plateforme, pouvoir superviser les activités suspectes ainsi qu’évaluer et examiner les configurations et états de conformité, et être en mesure de déployer des mécanismes de protection en temps réel.

La gestion de la posture de sécurité cloud (CSPM, Cloud Security Posture Management) s’étend au-delà de la posture de sécurité IaaS et PaaS pour couvrir également les configurations SaaS. Citons par exemple un référentiel GitHub avec un niveau d’accès public ou des applications OAuth ayant accès à des applications SaaS comme Office 365, Google Workspace ou Sales Force. Le CSPM SaaS est un nouveau domaine en pleine croissance de CSPM, qui est une extension native du produit Cloud App Security.

## <a name="protecting-multiple-clouds-from-a-single-management-portal"></a>Protection de plusieurs clouds à partir d’un seul portail de gestion

En raison de la complexité des organisations modernes qui, pour la plupart, utilisent plusieurs plateformes cloud à des fins diverses ainsi que des échelles et états de déploiement différents, un suivi régulier de l’environnement multicloud s’impose.  L’état de déploiement de certains services peut changer au fil du temps, mais les équipes de sécurité ne sont pas forcément notifiées des changements. Le regroupement de telles notifications dans un seul portail simplifie l’expérience d’administration, améliorant ainsi la gestion du temps et des ressources pour les personnes en charge de la supervision et pour celles utilisant les ressources cloud.

La posture de sécurité organisationnelle est une nouvelle fonctionnalité qui englobe toutes les plateformes cloud d’une organisation et qui s’adresse aux architectes de sécurité, administrateurs de la sécurité centrale et analystes de la conformité. Elle permet aux administrateurs de passer en revue les abonnements contenant des ressources non conformes et de piloter la correction de chaque ressource par son propriétaire.

Ce tutoriel fournit des instructions sur l’utilisation de Cloud App Security pour sécuriser vos plateformes cloud Azure, AWS et GCP.

> [!div class="checklist"]
>
> * Découvrir les ressources multiclouds, leur utilisation et le Shadow IT
> * Superviser les activités et les alertes pour détecter les comportements suspects dans les charges de travail
> * Évaluer et corriger les erreurs de configuration et l’état de conformité des plateformes cloud
> * Automatiser la protection et l’application de stratégies pour les ressources cloud en temps réel

## <a name="how-to-secure-your-multi-cloud-environment"></a>Comment sécuriser votre environnement multicloud

Pour éviter les erreurs de configuration critiques sur les plateformes cloud, il est important pour les organisations d’avoir une visibilité multicloud au niveau des locataires sur l’état de leur configuration cloud et de pouvoir améliorer leur posture de sécurité en fonction de références de sécurité et de recommandations en matière de conformité. Utilisez le processus suivant pour sécuriser l’environnement multicloud de votre organisation.

### <a name="phase-1-discover-multi-cloud-resources-usage-and-shadow-it"></a>Phase 1 : Découvrir les ressources multiclouds, leur utilisation et le Shadow IT

**Identifier la posture de sécurité** : Commencez par identifier la posture de sécurité cloud de votre organisation en exécutant Cloud Discovery pour voir ce qui se passe dans votre réseau et évaluer l’utilisation réelle des ressources dans vos plateformes cloud. Pour cela, [configurez Cloud Discovery](set-up-cloud-discovery.md) de manière à superviser et à analyser le trafic réseau dans Cloud App Security. L’analyse des journaux de trafic web avec la découverte du Shadow IT de Cloud App Security offre une meilleure visibilité sur l’utilisation des ressources cloud par le Shadow IT. Elle identifie les activités anormales au moyen du moteur de détection d’anomalie Machine Learning ou de stratégies personnalisées que vous définissez :

* **Découvrir** : Découvrez l’utilisation des ressources dans l’ensemble des plateformes cloud d’hébergement de votre organisation. Par exemple, évaluez le volume réel de données téléchargées à partir de vos ressources de stockage et identifiez les utilisations suspectes de ressources pouvant indiquer des tentatives d’exfiltration de données. De même, identifiez les activités de chargement suspectes pouvant signaler une tentative de compromission de votre environnement par injection de code malveillant dans une cible.
* **Examiner** : Utilisez la page **Ressources découvertes** pour voir l’accès aux données dans les ressources, notamment les comptes de stockage, l’infrastructure et les applications personnalisées hébergées sur Azure, AWS et GCP. Posez des questions, par exemple : « Le nombre de transactions lors de l’accès à une ressource spécifique est-il suspect ? »

    ![Voir les ressources découvertes](media/tutorial-cloud-platform-security-view-discovered-resources.png)

    Pour approfondir vos recherches, vous pouvez explorer au niveau du détail chaque ressource pour voir les types de transactions effectuées, qui y a accédé et aller encore plus loin pour en savoir plus sur les utilisateurs.

    ![Examiner les ressources découvertes](media/tutorial-cloud-platform-security-investigate-discovered-resources.png)

### <a name="phase-2-monitor-activities-and-alerts-to-detect-suspicious-behavior-across-workloads"></a>Phase 2 : Superviser les activités et les alertes pour détecter les comportements suspects dans les charges de travail

Faites le suivi des activités suspectes pouvant indiquer une violation, comme un changement de rôle IAM ou de configuration CloudTrail. Par exemple, utilisez notre [modèle de stratégie](policy-template-reference.md) prédéfini **Compartiments AWS S3 accessibles publiquement** pour suivre les changements de configuration des compartiments S3.

La supervision des journaux d’audit dans le but d’identifier des changements suspects se prête à l’utilisation d’outils de détection d’anomalie. Ceux-ci signalent les violations possibles à la suite d’une série de tentatives de connexion infructueuses ou d’activités de machine virtuelle supprimées en combinaison avec un scénario de voyage impossible.

![Afficher les alertes](media/tutorial-cloud-platform-security-view-alerts.png)

Utilisez les informations fournies par les alertes pour régler les détections de l’activité utilisateur dans le but d’identifier les vraies compromissions et de réduire la multiplication des alertes due à la gestion de gros volumes de détections de faux positifs. Vous pouvez régler les paramètres de stratégie suivants :

* Configurer des [plages d’adresses IP](tutorial-suspicious-activity.md#phase-1-configure-ip-address-ranges)
* Régler des [stratégies de détection d’anomalie](tutorial-suspicious-activity.md#phase-2-tune-anomaly-detection-policies) : activités d’administration inhabituelles, activités de téléchargement de plusieurs fichiers inhabituelles, activité liée à des rançongiciels, connexions infructueuses à des plateformes cloud, etc.
* Régler des [stratégies de détection d’anomalie Cloud Discovery](tutorial-suspicious-activity.md#phase-3-tune-cloud-discovery-anomaly-detection-policies) en ajustant la supervision de l’utilisation et la sensibilité des alertes
* Régler [des stratégies de détection basée sur des règles et des stratégies d’activité](tutorial-suspicious-activity.md#phase-4-tune-rule-based-detection-activity-policies), notamment les compartiments AWS S3 accessibles publiquement
* Configurer des [alertes](tutorial-suspicious-activity.md#phase-5-configure-alerts)
* [Investiguer et corriger](tutorial-suspicious-activity.md#phase-6-investigate-and-remediate)

### <a name="phase-3-assess-and-remediate-cloud-platform-misconfigurations-and-compliance-status"></a>Phase 3 : Évaluer et corriger les erreurs de configuration et l’état de conformité des plateformes cloud

Évaluez l’état de votre conformité en matière de sécurité par locataire, sur toutes les plateformes cloud publiques, notamment les abonnements Azure, les comptes AWS et les projets GCP. Ces évaluations vous permettent de communiquer les lacunes de configuration et les détails des recommandations aux propriétaires des ressources et de piloter la correction.

Chaque plateforme cloud fournit une liste des ressources mal configurées en fonction des bonnes pratiques en matière de conformité réglementaire.

Les architectes cloud ou les analystes de la conformité peuvent évaluer les lacunes de configuration pour chaque environnement cloud et piloter la correction par les propriétaires de ressources. Par exemple, les recommandations peuvent être évaluées par :

* Abonnement pour différencier les environnements de production des environnements hors production
* Gravité pour identifier les recommandations de gravité élevée qui ont souvent des SLA et des processus différents de ceux des recommandations de faible gravité

Pour les recommandations concernant la configuration de la sécurité Azure, nous présentons les recommandations du locataire Azure dans sa totalité et de tous ses abonnements en fonction des bonnes pratiques d’Azure Security Center. Si vous sélectionnez une recommandation, vous êtes redirigé vers la page correspondante dans Azure Security Center où vous pouvez obtenir des détails supplémentaires sur la recommandation et les utiliser pour piloter la correction par le propriétaire de l’abonnement. Certaines recommandations proposent des **correctifs rapides** pour remédier au problème. Pour plus d’informations sur les recommandations de sécurité Azure, consultez [Configuration de la sécurité pour Azure](security-config-azure.md).

![Voir les recommandations Azure](media/tutorial-cloud-platform-security-view-azure-recommendations.png)

Pour les recommandations concernant la configuration de la sécurité AWS, vous pouvez sélectionner une recommandation et explorer au niveau du détail les ressources affectées. Par exemple, la recommandation AWS CIS 2.9 « Vérifier que la journalisation de flux VPC est activée dans tous les VPC » présente les ressources pour lesquelles la journalisation VPC n’est pas activée. Parmi les détails fournis figurent les noms des VPC, le compte dans lequel la ressource est hébergée et la région. Vous pouvez sélectionner le lien AWS pour voir le résultat approprié et modifier les paramètres associés dans AWS pour vous conformer à la recommandation. Pour plus d’informations, consultez [Configuration de la sécurité pour AWS](security-config-aws.md).

![Voir les recommandations AWS](media/tutorial-cloud-platform-security-view-aws-recommendations.png)

Pour les recommandations concernant la configuration de la sécurité GCP, sélectionnez une recommandation pour obtenir des informations détaillées et les étapes de correction à suivre. Vous pourrez ainsi mieux comprendre l’impact du problème et évaluer les efforts à fournir pour y remédier. Sélectionnez ensuite le lien Centre de commandes de sécurité GCP pour corriger le problème indiqué dans la plateforme. Pour plus d’informations sur les recommandations GCP, consultez [Configuration de la sécurité pour GCP](security-config-gcp.md).

![Voir les recommandations GCP](media/tutorial-cloud-platform-security-view-gcp-recommendations.png)

### <a name="phase-4-automate-protection-and-policy-enforcement-for-cloud-resources-in-real-time"></a>Phase 4 : Automatiser la protection et l’application de stratégies pour les ressources cloud en temps réel

Protégez les ressources de votre organisation contre les fuites et le vol de données en temps réel en appliquant des stratégies de contrôle d’accès et de session. Pour plus d’informations, consultez [Protéger des applications en temps réel](tutorial-proxy.md).

* Empêchez l’exfiltration des données en [bloquant les téléchargements](session-policy-aad.md#block-download) vers des appareils non gérés ou risqués ou au cours d’une session risquée.
* Empêchez le [chargement de fichiers malveillants](session-policy-aad.md#block-malware-on-upload) sur vos plateformes cloud et bloquez l’accès à des utilisateurs spécifiques en fonction de divers facteurs de risque.

![Spécifier une action de correction de stratégie](media/tutorial-cloud-platform-security-remediation.png)

## <a name="see-also"></a>Voir aussi

> [!div class="nextstepaction"]
> [Protéger votre environnement Azure](protect-azure.md)

> [!div class="nextstepaction"]
> [Protéger votre environnement AWS](protect-aws.md)

> [!div class="nextstepaction"]
> [Protéger votre environnement GCP](protect-gcp.md)

[!INCLUDE [Open support ticket](includes/support.md)]
