---
title: Anonymisation des données d’utilisateur dans Cloud App Security
description: Cet article fournit des informations sur la façon de protéger la confidentialité des utilisateurs en anonymisant les noms d’utilisateur dans vos données Cloud Discovery.
ms.date: 04/20/2020
ms.topic: how-to
ms.openlocfilehash: bb8befb8c65f766118f6a3221b382c6699b17a0e
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96313523"
---
# <a name="cloud-discovery-data-anonymization"></a>Anonymisation des données Cloud Discovery

[!INCLUDE [Banner for top of topics](includes/banner.md)]

L’anonymisation de données Cloud Discovery vous permet de protéger la confidentialité des utilisateurs. Une fois que le journal des données est téléchargé sur le portail Microsoft Cloud App Security, il est purgé et toutes les informations des noms d’utilisateur sont remplacées par des noms d’utilisateur chiffrés. De cette façon, toutes les activités cloud restent anonymes. Quand c’est nécessaire, pour une enquête de sécurité spécifique (par exemple une violation de la sécurité ou une activité utilisateur suspecte), les administrateurs peuvent résoudre le nom d’utilisateur réel. Si un administrateur a une raison de suspecter un utilisateur spécifique, il peut également rechercher le nom d’utilisateur chiffré d’un nom d’utilisateur connu, puis commencer son investigation avec le nom d’utilisateur chiffré. Chaque conversion de nom d’utilisateur est auditée dans le **Journal de gouvernance** du portail.

Points clés :

- Aucune information privée n’est stockée ou affichée. Seulement des informations chiffrées.
- Les données privées sont chiffrées en utilisant AES-128 avec une clé dédiée par client.
- La résolution des noms d’utilisateur est correctement effectuée, par nom d’utilisateur en déchiffrant un nom d’utilisateur chiffré donné.

## <a name="how-data-anonymization-works"></a>Fonctionnement de l’anonymisation des données

1. Il existe trois façons d’appliquer l’anonymisation des données :

    - Vous pouvez anonymiser les données d’un fichier journal spécifique en [créant un rapport de capture instantanée](create-snapshot-cloud-discovery-reports.md) et en sélectionnant **Anonymiser les informations privées**.  
    ![Anonymiser des données de capture instantanée](media/anonymize-log.png)

    - Vous pouvez anonymiser les données d’un [chargement automatisé d’une nouvelle source de données](configure-automatic-log-upload-for-continuous-reports.md) en sélectionnant **Anonymiser les informations privées** quand vous ajoutez la nouvelle source de données.  
    ![Anonymiser les données des journaux](media/anonymize-autolog.png)

    - Vous pouvez définir le comportement par défaut dans Cloud App Security pour anonymiser toutes les données des rapports de capture instantanée des fichiers journaux chargés et celles des rapports continus du collecteur de journaux comme suit :

    1. Sélectionnez **paramètres**  >  **Cloud Discovery paramètres**.

    2. Dans l’onglet **anonymisation** , pour anonymiser les noms d’utilisateur par défaut, sélectionnez **anonymiser les informations privées par défaut dans les nouveaux rapports et les nouvelles sources de données**. Vous pouvez également sélectionner **rendre les informations d’appareil anonymes par défaut dans le rapport « utilisateurs du point de terminaison Win10 »**.
    3. Cliquez sur **Enregistrer**.

    ![Page Paramètres d’anonymisation](media/anonymizer1.png)

2. Quand l’anonymisation est sélectionnée, Cloud App Security analyse le journal du trafic et extrait les attributs de données spécifiques.
3. Cloud App Security remplace le nom d’utilisateur par un nom d’utilisateur chiffré.
4. Il analyse ensuite les données d’utilisation cloud et génère des rapports Cloud Discovery basés sur les données anonymisées.

    ![Anonymiser le tableau de bord Cloud Discovery](media/anonymize-dashboard.png)

5. Pour une investigation spécifique, telle que l’examen d’une alerte d’utilisation anormale, vous pouvez résoudre le nom d’utilisateur spécifique dans le portail et fournir une justification commerciale.

    > [!NOTE]
    > Les étapes suivantes fonctionnent également pour les noms de périphériques sous l’onglet **périphériques** .

    **Pour résoudre un nom d’utilisateur unique**

    1. Cliquez sur les trois points à la fin de la ligne de l’utilisateur que vous souhaitez résoudre, puis sélectionnez l’option de **désanonymisation** de l’utilisateur.

        ![Anonymiser la table utilisateur](media/anonymize-user-table.png)

    1. Dans la fenêtre contextuelle, entrez la justification de la résolution du nom d’utilisateur, puis cliquez sur **résoudre**. Dans la ligne appropriée, le nom d’utilisateur résolu s’affiche.

        > [!NOTE]
        > Cette action est auditée.

        ![Rendre anonyme résoudre le menu contextuel](media/anonymize-resolve-dialog.png)

    La méthode alternative suivante pour résoudre les noms d’utilisateur uniques peut également être utilisée pour rechercher le nom d’utilisateur chiffré d’un nom d’utilisateur connu.

    1. Sous l’roue dentée paramètres, sélectionnez **paramètres de Cloud Discovery**.

    1. Sous l’onglet **Anonymisation**, sous **Anonymiser et résoudre les noms d’utilisateur**, entrez une justification expliquant pourquoi vous effectuez la résolution.
    1. Sous **Entrer le nom d’utilisateur à résoudre**, sélectionnez **À partir du nom anonymisé** et entrez le nom d’utilisateur anonymisé, ou sélectionnez **À anonymiser** et entrez le nom d’utilisateur d’origine à résoudre. Cliquez sur **Résoudre**.

        ![Résoudre la fenêtre contextuelle d’anonymisation](media/anonymizer.png)

    **Pour résoudre plusieurs noms d’utilisateur**

    1. Activez les cases à cocher qui s’affichent lorsque vous pointez sur les icônes utilisateur par les utilisateurs que vous souhaitez résoudre ou, dans l’angle supérieur gauche, sélectionnez la case à cocher **sélection en bloc** .

        ![Anonymiser la résolution en bloc](media/anonymize-bulk-resolve.png)

    1. Cliquez sur **désanonymiser l’utilisateur**.
    1. Dans la fenêtre contextuelle, entrez la justification de la résolution du nom d’utilisateur, puis cliquez sur **résoudre**. Dans les lignes pertinentes, les noms d’utilisateur résolus sont affichés.

        > [!NOTE]
        > Cette action est auditée.

        ![Rendre anonyme résoudre le menu contextuel](media/anonymize-resolve-dialog.png)

6. L’action est auditée dans le journal de **gouvernance** du portail.

    ![Action d’anonymisation dans le journal de gouvernance](media/anonymize-gov-log.png)

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
