---
title: Bloquer les téléchargements des appareils non gérés avec le contrôle d'application par accès conditionnel Cloud App Security
description: Ce tutoriel décrit le scénario permettant de protéger votre organisation contre les téléchargements de données sensibles par des appareils non gérés à l’aide des fonctionnalités de proxy inverse Azure AD.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/31/2020
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: d8208d654774aefd776da4ba1b3b1cbfda4caae7
ms.sourcegitcommit: 826d2ec022647bce6c3135c115a41ee894ff8ecd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/16/2020
ms.locfileid: "84800705"
---
# <a name="tutorial-block-download-of-sensitive-information"></a>Tutoriel : Bloquer le téléchargement des informations sensibles

*S’applique à : Microsoft Cloud App Security*

Aujourd’hui, l’administrateur informatique se retrouve confronté à un véritable dilemme. Vous souhaitez augmenter la productivité de vos employés. Cela signifie que les employés peuvent accéder aux applications à tout moment et depuis n’importe quel appareil. Mais vous souhaitez protéger les ressources de l’entreprise, y compris les informations propriétaires et les informations privilégiées. Comment permettre aux employés d’accéder à vos applications cloud tout en protégeant vos données ? **Ce tutoriel vous permet de bloquer les téléchargements effectués par les utilisateurs qui ont accès à vos données sensibles dans les applications cloud d’entreprise à partir d’appareils non gérés ou d’emplacements réseau hors de l’entreprise.**

> [!div class="checklist"]
>
> * Créer une stratégie de blocage des téléchargements pour les appareils non gérés
> * Valider votre stratégie

## <a name="the-threat"></a>La menace

Un responsable de compte de votre organisation veut vérifier une information dans Salesforce de chez lui pendant le week-end, sur son ordinateur portable personnel. Les données Salesforce peuvent inclure des informations sur la carte de crédit du client ou des données personnelles. Le PC du domicile n’est pas géré. S’il télécharge des documents de Salesforce sur le PC, il risque d’être infecté par des logiciels malveillants. Si la machine est perdue ou volée, elle risque de ne pas être protégée par un mot de passe, et toute personne qui la trouve peut avoir accès à des informations sensibles.

## <a name="the-solution"></a>La solution

Protégez votre organisation en surveillant et en contrôlant l’utilisation des applications cloud à l’aide d’une solution de fournisseur d’identité et du contrôle d’application par accès conditionnel de Microsoft Cloud App Security.

## <a name="prerequisites"></a>Prérequis

* Une licence valide Azure AD Premium licence P1 ou la licence requise par votre solution de fournisseur d’identité
* Une application cloud configurée pour l’authentification unique suivant l’un des protocoles d’authentification suivants :

    |Fournisseur d’identité|Protocoles|
    |---|---|
    |Azure AD|SAML 2.0 ou OpenID Connect|
    |Autre|SAML 2.0|
* S’assurer que [l’application est déployée sur Cloud App Security](proxy-deployment-aad.md)

## <a name="create-a-block-download-policy-for-unmanaged-devices"></a>Créer une stratégie de blocage des téléchargements pour les appareils non gérés

Les stratégies de session Cloud App Security vous permettent de limiter une session en fonction de l’état de l’appareil. Pour contrôler une session en utilisant son appareil comme condition, créez à la fois une stratégie d’accès conditionnel ET une stratégie de session.

### <a name="step-1-configure-your-idp-to-work-with-cloud-app-security"></a>Étape 1 : Configurer le fournisseur d’identité pour qu’il fonctionne avec Cloud App Security

Configurez votre solution de fournisseur d’identité pour qu’elle fonctionne avec Cloud App Security :

* Pour [l’accès conditionnel Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal), consultez [Configuration de l’intégration avec Azure AD](proxy-deployment-aad.md#configure-integration-with-azure-ad).
* Pour les autres solutions de fournisseur d’identité, consultez [Configuration de l’intégration avec d’autres solutions de fournisseur d’identité](proxy-deployment-aad.md#configure-integration-with-other-idp-solutions).

Une fois cette tâche terminée, accédez au portail Cloud App Security et créez une stratégie de session pour surveiller et contrôler les téléchargements de fichiers dans la session.

### <a name="step-2-create-a-session-policy"></a>Étape 2 : Créer une stratégie de session

1. Dans le portail Cloud App Security, sélectionnez **Contrôle**, puis **Stratégies**.

2. Dans la page **stratégies**, cliquez sur **créer une stratégie**, puis sur **Stratégie de session**.

3. Dans la page **Créer une stratégie de session**, attribuez un nom et une description à votre stratégie. Par exemple, **Bloquer les téléchargements à partir de Salesforce pour les appareils non gérés**.

4. Définissez la **gravité de la stratégie** et la **catégorie**.

5. Pour le **type de contrôle de session**, sélectionnez **Contrôler le téléchargement du fichier (avec inspection)** . Ce paramètre vous permet de surveiller toutes les activités de vos utilisateurs dans une session Salesforce et de contrôler le blocage et la protection des téléchargements en temps réel.

6. Sous **Source de l’activité** dans la section **Activités remplissant toutes les conditions suivantes**, sélectionnez les filtres :

   * **Balise de l'appareil** : Sélectionnez **Différent de**. Sélectionnez ensuite **Conforme Intune**, **Joint à une version hybride d’Azure AD** ou **Certification client valide**. Votre sélection dépend de la méthode utilisée dans votre organisation pour identifier les appareils gérés.

   * **Application** : sélectionnez l’application que vous voulez contrôler.

   * **Utilisateurs** : sélectionnez les utilisateurs que vous souhaitez surveiller.

7. Vous pouvez également bloquer les téléchargements pour les emplacements qui ne font pas partie de votre réseau d’entreprise. Sous **Source de l’activité** dans la section **Activités remplissant toutes les conditions suivantes**, définissez les filtres suivants :

   * **Adresse IP** ou **Emplacement** : Vous pouvez utiliser l’un de ces deux paramètres pour identifier les emplacements externes à l’entreprise ou inconnus, à partir desquels un utilisateur peut tenter d’accéder à des données sensibles.

     > [!NOTE]
     > Si vous souhaitez bloquer les téléchargements À LA FOIS à partir d’appareils non gérés et d’emplacements externes à l’entreprise, vous devez créer deux stratégies de session. Une stratégie définit la **source de l’activité** à l’aide de l’emplacement. L’autre stratégie définit la **source de l’activité** sur des appareils non gérés.

   * **Application** : sélectionnez l’application que vous voulez contrôler.

   * **Utilisateurs** : sélectionnez les utilisateurs que vous souhaitez surveiller.

8. Sous **Source de l’activité** dans la section **Fichiers remplissant toutes les conditions suivantes**, définissez les filtres suivants :

   * **Étiquettes de classification** : Si vous utilisez les étiquettes de classification Azure Information Protection, filtrez les fichiers en fonction d’une étiquette de classification Azure Information Protection spécifique.

   * Sélectionnez **Nom du fichier** ou **Type de fichier** pour appliquer des restrictions basées sur le nom ou le type de fichier.
9. Activez **Inspection du contenu** pour permettre au moteur DLP interne d’analyser vos fichiers à la recherche de contenu sensible.

10. Sous **Actions**, sélectionnez **bloquer**. Personnalisez le message de blocage que recevront vos utilisateurs lorsqu’ils ne parviennent pas à télécharger des fichiers.

11. Définissez les alertes que vous souhaitez recevoir lorsque la stratégie est mise en correspondance. Vous pouvez définir une limite pour ne pas recevoir trop d’alertes. Indiquez si vous souhaitez recevoir les alertes sous la forme d’un e-mail, d’un message texte, ou les deux.

12. Cliquez sur **Créer**

## <a name="validate-your-policy"></a>Valider votre stratégie

1. Pour simuler le téléchargement d’un fichier bloqué à partir d’un appareil non géré ou d’un emplacement réseau externe à l’entreprise, connectez-vous à l’application. Ensuite, essayez de télécharger un fichier.

2. Ce fichier doit être bloqué et vous devez recevoir le message que vous avez défini sous **Personnaliser les messages de blocage**.

3. Sur le portail Cloud App Security, cliquez sur **Contrôle**, **Stratégies**, puis sur la stratégie que vous avez créée pour afficher le rapport de stratégie. Une correspondance de stratégie de session doit apparaître rapidement.

4. Dans le rapport de stratégie, vous pouvez voir quelles connexions ont été redirigées vers Microsoft Cloud App Security pour le contrôle de session, et quels fichiers ont été téléchargés ou bloqués depuis les sessions surveillées.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Guide pratique pour créer une stratégie d’accès](access-policy-aad.md)

> [!div class="nextstepaction"]
> [Guide pratique pour créer une stratégie de session](session-policy-aad.md)

[!INCLUDE [Open support ticket](includes/support.md)]
