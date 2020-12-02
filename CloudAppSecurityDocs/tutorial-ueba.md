---
title: Examiner des utilisateurs à risque | Microsoft Docs
description: Ce tutoriel décrit le processus permettant d’examiner les utilisateurs à risque dans Microsoft Cloud App Security, dans des environnements hybrides, en utilisant une intégration à Microsoft Defender pour Identity.
ms.date: 11/08/2020
ms.topic: tutorial
ms.openlocfilehash: 9ef0555a8fc7fa82a87fd7238d0abc2ec85e4540
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96315835"
---
# <a name="tutorial-investigate-risky-users"></a>Tutoriel : Examiner des utilisateurs à risque

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Des équipes des opérations de sécurité sont mises au défi de surveiller l’activité de l’utilisateur, suspecte ou pas, dans toutes les dimensions de la surface d’attaque d’identité, à l’aide de plusieurs solutions de sécurité qui souvent ne sont pas connectées. Alors que de nombreuses sociétés ont maintenant des équipes de chasse pour identifier de façon proactive les menaces dans leurs environnements, le fait de connaître ce que vous recherchez dans la vaste quantité de données peut être un défi. Microsoft Cloud App Security simplifie désormais le problème en éliminant la nécessité de créer des règles de corrélation complexes et vous permet de détecter les attaques qui s’étendent sur votre cloud et réseau local.

Pour vous aider à vous concentrer sur l’identité des utilisateurs, Microsoft Cloud App Security fournit l’analyse comportementale des utilisateurs et des entités (UEBA) dans le cloud. Vous pouvez l’étendre à votre environnement local en l’intégrant à Microsoft Defender pour Identity. Une fois l’intégration à Defender pour Identity terminée, vous obtiendrez également le contexte de l’identité de l’utilisateur grâce à son intégration native à Active Directory.

Que votre déclencheur soit une alerte visible dans le tableau de bord Cloud App Security ou que vous disposiez d’informations provenant d’un service de sécurité tiers, démarrez votre enquête à partir du tableau de bord Cloud App Security pour explorer en profondeur les utilisateurs à risque.

Ce tutoriel fournit des instructions sur l’utilisation de Cloud App Security pour examiner les utilisateurs à risque.

> [!div class="checklist"]
>
> * 1 : [Se connecter aux applications à protéger](#connect-apps-protect)
> * 2 : [Identifier les principaux utilisateurs à risque](#identify)
> * 3 : [Examiner davantage les utilisateurs](#investigate)
> * 4 : [Protéger votre organisation](#protect)

## <a name="understand-the-investigation-priority-score"></a>Comprendre le score de priorité d’examen<a name="risk-score"></a>

Le score de priorité d’examen est fourni par Cloud App Security à chaque utilisateur pour vous permettre de savoir quel risque présente un utilisateur par rapport à d’autres utilisateurs de votre organisation.

Utilisez le **score de priorité d’examen** pour identifier les utilisateurs à examiner en premier. Cloud App Security crée des profils d'utilisateur pour chaque utilisateur en fonction de diverses analyses prenant en compte l’heure, les groupes homologues et l’activité attendue. Toute activité jugée anormale par rapport à la référence d'un utilisateur est évaluée et notée. Une fois le score évalué, les calculs homologues dynamiques propriétaires de Microsoft et l'apprentissage automatique sont exécutés sur les activités de l'utilisateur pour calculer la priorité d'examen pour chaque utilisateur.

Le **score de priorité d'examen** vous permet de détecter à la fois les employés malveillants et les menaces externes qui se propagent latéralement dans votre organisation, sans avoir à vous fier aux détections déterministes standard.

Le score de priorité d’examen est basé sur les alertes de sécurité, les activités anormales et l’impact potentiel sur les activités et les ressources de chaque utilisateur pour vous aider à déterminer à quel point il est urgent d’examiner chaque utilisateur spécifique.

Si vous cliquez sur le score d'une alerte ou d'une activité, vous pouvez voir les preuves sur lesquelles Cloud App Security s’est appuyé pour noter l'activité.

Chaque utilisateur Azure AD dispose d’un score de priorité d’examen dynamique, constamment mis à jour en fonction du comportement et de l’impact récents, calculé à partir des données évaluées par Defender pour Identity et Cloud App Security. Vous pouvez maintenant identifier immédiatement les principaux utilisateurs à risque en les filtrant par **score de priorité d’examen**, puis vérifier directement leur impact sur l’entreprise et examiner toutes les activités connexes, qu’il s’agisse d’informations compromises, de données exfiltrées ou de menaces provenant des employés.

Cloud App Security utilise les fonctionnalités suivantes pour mesurer le risque :

* **Score d’alerte**  
Le score d'alerte représente l'impact potentiel d'une alerte spécifique sur chaque utilisateur. Le score d’alerte est basé sur la gravité, l'impact sur les utilisateurs ainsi que le niveau de propagation chez les autres utilisateurs et dans toutes les entités de l'organisation.

* **Score d’activité**  
Le score d'activité détermine la probabilité qu'un utilisateur donné effectue une activité spécifique, en fonction de l'apprentissage comportemental de l'utilisateur et de ses collègues. Les activités identifiées comme étant les plus anormales reçoivent les scores les plus élevés.

## <a name="phase-1-connect-to-the-apps-you-want-to-protect"></a>Phase 1 : Se connecter aux applications à protéger<a name="connect-apps-protect"></a>

1. Connectez au moins une application à Microsoft Cloud App Security à l’aide de [connecteurs API](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md). Pour commencer, nous vous recommandons de connecter [Office 365](connect-office-365-to-microsoft-cloud-app-security.md).
1. Connectez des applications supplémentaires à l’aide du [proxy pour mettre en place le contrôle d’application par accès conditionnel](proxy-deployment-aad.md).
1. Pour activer les insights sur votre environnement local, configurez Cloud App Security pour [s’intégrer à votre environnement Defender pour Identity](mdi-integration.md).

## <a name="phase-2-identify-top-risky-users"></a>Phase 2 : Identifier les principaux utilisateurs à risque<a name="identify"></a>

Pour identifier vos utilisateurs présentant le plus de risques dans Cloud App Security :

1. Accédez au tableau de bord Cloud App Security et recherchez les personnes identifiées dans la mosaïque **Top users by investigation priority** (Principaux utilisateurs par priorité d’examen), puis examinez une à une la page de ces utilisateurs.  
Le **numéro de priorité d’examen**, affiché en regard du nom d’utilisateur, correspond à la somme de toutes les activités à risque de l’utilisateur au cours de la semaine dernière.

   ![Tableau de bord des principaux utilisateurs](media/dashboard-top-users.png)

1. Cliquez sur un utilisateur pour accéder à la page **Utilisateur**.
    ![Page Utilisateur](media/user-page.png)

1. Passez en revue les informations de la page Utilisateur pour obtenir une vue d’ensemble de l’utilisateur et vérifier s’il existe des cas où l’utilisateur a effectué des activités inhabituelles pour lui ou si elles ont été réalisées à un moment inhabituel. Le **score de l’utilisateur par rapport à l’organisation** représente le centile de cet utilisateur dans le classement dans votre organisation, c’est-à-dire à quel niveau il figure sur la liste des utilisateurs que vous devriez examiner, par rapport aux autres utilisateurs de votre organisation. Le chiffre s’affiche en rouge si un utilisateur se situe dans ou au-dessus du 90e centile des utilisateurs à risque de votre organisation.  
La page Utilisateur vous aide à répondre aux questions suivantes :
    * Qui est l’utilisateur ?  
    Consultez le volet de gauche pour obtenir des informations sur l’identité de l’utilisateur et ce que l’on sait sur lui. Ce volet vous fournit des informations sur le rôle de l'utilisateur dans votre entreprise et son service. L'utilisateur est-il un ingénieur DevOps qui effectue souvent des activités inhabituelles dans le cadre de son travail ? L'utilisateur est-il un employé mécontent qui s’est vu refuser une promotion ?

    * S’agit-il d’un utilisateur à risque ?  
    Consultez la partie supérieure du volet de droite pour savoir l’examen de cet utilisateur est justifié. Quel est le [score de risque](#risk-score) de l'employé ?
    * Quel risque l’utilisateur présente-t-il pour votre organisation ?  
    Consultez la liste dans le volet inférieur, qui vous indique chaque activité et chaque alerte liées à l'utilisateur. Cette liste vous aide à comprendre quel type de risque l'utilisateur représente. Dans la chronologie, cliquez sur chaque ligne afin de descendre encore plus dans la hiérarchie de l’activité ou de l’alerte elle-même. Vous pouvez cliquer également sur le numéro en regard de l’activité afin que vous puissiez comprendre la preuve qui influence le score lui-même.
    * Quels sont les risques pour les autres ressources de votre organisation ?  
    Sélectionnez l’onglet **Chemins de mouvement latéral** pour identifier les chemins qu’un attaquant peut utiliser pour prendre le contrôle d’autres ressources de votre organisation. Par exemple, même si le compte de l’utilisateur que vous examinez n’est pas sensible, l’attaquant peut se servir des connexions au compte pour découvrir et tenter de compromettre des comptes sensibles dans votre réseau. Pour plus d’informations, consultez [Utilisation des chemins de mouvement latéral](/defender-for-identity/investigate-lateral-movement-path).

  >[!NOTE]
  >Remarque importante : même si la page Utilisateur fournit des informations sur les appareils, les ressources et les comptes pour toutes les activités, le score de priorité d’examen correspond à la somme de toutes les activités et alertes à risque identifiées au cours des 7 derniers jours.

## <a name="phase-3-further-investigate-users"></a>Phase 3 : Examiner davantage les utilisateurs<a name="investigate"></a>

Lorsque vous examinez un utilisateur en fonction d’une alerte ou si vous avez vu une alerte dans un système externe, il peut y avoir des activités qui peuvent ne pas être la cause d’une alerte seules, mais lorsque Cloud App Security les agrège avec d’autres activités, l’alerte peut indiquer un événement suspect.

Lorsque vous examinez un utilisateur, posez-vous ces questions sur les activités et les alertes affichées :

* Y a-t-il une justification métier pour que cet employé effectue ces activités ? Par exemple, si une personne du Marketing accède à la base de code ou une personne du Développement accède à une base de données Finance, vous devez suivre l’employé pour vous assurer qu’il s’agissait d’une activité intentionnelle et justifiée.

* Accédez au **journal d’activité** pour comprendre pourquoi cette activité a reçu un score élevé, tandis que d’autres n’ont pas reçu ce score. Vous pouvez définir la **Priorité d’examen** sur **Est défini** pour comprendre quelles activités sont suspectes. Par exemple, vous pouvez filtrer selon la Priorité d’examen pour toutes les activités qui se sont produites en Ukraine. Vous verrez alors si d’autres activités à risque se sont produites et à quel endroit l'utilisateur s'est connecté. Pour poursuivre l’examen, il est très facile de basculer vers d’autres aspects, par exemple les dernières activités non anormales dans le cloud et localement.

## <a name="phase-4-protect-your-organization"></a>Phase 4 : Protéger votre organisation<a name="protect"></a>

Si votre enquête débouche sur la conclusion qu’un utilisateur est compromis, effectuez les étapes suivantes pour réduire le risque.

* Contactez l’utilisateur : utilisez les informations de contact de l’utilisateur intégrées à Cloud App Security à partir d’Active Directory pour explorer au niveau du détail chaque alerte et activité afin de résoudre l’identité de l’utilisateur. Assurez-vous que l’utilisateur est familiarisé avec les activités.

* Directement sur le portail Cloud App Security, cliquez sur le contrôle **Actions de l’utilisateur** et indiquez si vous souhaitez demander à l’utilisateur de se reconnecter, le suspendre ou confirmer qu’il est compromis.

* Dans le cas d’une identité compromise, vous pouvez demander à l’utilisateur de réinitialiser son mot de passe et de vérifier que le mot de passe répond aux bonnes pratiques en matière de longueur et de complexité.
* Si vous examinez une alerte et estimez que l'activité n'aurait pas dû déclencher cette alerte, dans le [tiroir Activité](activity-filters.md), cliquez sur le lien **Envoyez-nous des commentaires** pour nous permettre d'ajuster notre système d'alerte en fonction de votre organisation.
* Une fois le problème résolu, fermez l’alerte.

## <a name="see-also"></a>Voir aussi

> [!div class="nextstepaction"]
> [Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
