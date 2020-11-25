---
title: Stratégies de protection des informations
description: Cette rubrique décrit les étapes permettant de configurer de nombreuses stratégies de protection des informations dans Cloud App Security.
author: shsagir
ms.author: shsagir
ms.date: 06/13/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 379ff12d418ec6ec928817eff45da5b59b25f13f
ms.sourcegitcommit: a0a8e25bda77fb21f280a0e504896be85b89ed6f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96033852"
---
# <a name="information-protection-policies"></a>Stratégies de protection des informations

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Cloud App Security les stratégies de fichiers vous permettent d’appliquer un large éventail de processus automatisés. Les stratégies peuvent être définies de manière à fournir une protection des informations, notamment des analyses de conformité continue, des tâches eDiscovery juridiques et la protection contre la perte de contenu sensible partagée publiquement.

Cloud App Security pouvez surveiller n’importe quel type de fichier en fonction de plus de 20 filtres de métadonnées, par exemple, le niveau d’accès et le type de fichier. Pour plus d’informations, consultez [stratégies de fichier](data-protection-policies.md).

## <a name="detect-and-prevent-external-sharing-of-sensitive-data"></a>Détecter et empêcher le partage externe de données sensibles

Détectez le moment où les fichiers contenant des informations d’identification personnelle ou d’autres données sensibles sont stockés dans un service Cloud et partagés avec des utilisateurs externes à votre organisation qui enfreignent la stratégie de sécurité de votre entreprise et créent une violation potentielle de la conformité.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer d’au moins une application connectée à l’aide de [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Étapes

1. Dans la page **stratégies** , créez une **stratégie de fichier**.

2. Définissez le **niveau d’accès** du filtre sur **public (Internet)/public/External**.

3. Sous **méthode d’inspection**, sélectionnez **service de classification des données (DC)**, puis sous sélectionner un **type** , sélectionnez le type d’informations sensibles que vous voulez que les contrôleurs de service inspectent.

4. Configurez les actions de **gouvernance** à entreprendre lorsqu’une alerte est déclenchée. Par exemple, vous pouvez créer une action de gouvernance qui s’exécute sur les violations de fichiers détectés dans G suite dans laquelle vous sélectionnez l’option permettant de **Supprimer les utilisateurs externes** et de **Supprimer l’accès public**.

5. Créez la stratégie de fichier.

## <a name="detect-externally-shared-confidential-data"></a>Détecter les données confidentielles partagées en externe

Détecte quand les fichiers étiquetés comme **confidentiels** et stockés dans un service Cloud sont partagés avec des utilisateurs externes, enfreignant ainsi les stratégies de l’entreprise.

### <a name="prerequisites"></a>Prérequis

- Vous devez disposer d’au moins une application connectée à l’aide de [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

- Activez l' [intégration de Azure information protection](azip-integration.md).

### <a name="steps"></a>Étapes

1. Dans la page **stratégies** , créez une **stratégie de fichier**.

2. Définissez l' **étiquette de classification** de filtre sur **Azure information protection** est égal à l’étiquette **confidentiel** ou à l’équivalent de votre entreprise.

3. Définissez le **niveau d’accès** du filtre sur **public (Internet)/public/External**.

4. Facultatif : définissez les actions de **gouvernance** à effectuer sur les fichiers lorsqu’une violation est détectée. Les actions de gouvernance disponibles varient d’un service à l’autre.

5. Créez la stratégie de fichier.

## <a name="detect-and-encrypt-sensitive-data-at-rest"></a>Détecter et chiffrer les données sensibles au repos

Détectez les fichiers contenant des informations d’identification personnelle et d’autres données sensibles qui sont partagées dans une application Cloud et appliquez des étiquettes de classification pour limiter l’accès aux employés de votre entreprise.

### <a name="prerequisites"></a>Prérequis

- Vous devez disposer d’au moins une application connectée à l’aide de [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

- Activez l' [intégration de Azure information protection](azip-integration.md).

### <a name="steps"></a>Étapes

1. Dans la page **stratégies** , créez une **stratégie de fichier**.

2. Sous **méthode d’inspection**, sélectionnez **service de classification des données (DC)** et sous sélectionner un **type** , sélectionnez le type d’informations sensibles que vous voulez que les contrôleurs de service inspectent.

3. Sous **alerte**, activez la case à cocher **appliquer la gouvernance des étiquettes de classification** et sélectionnez l’étiquette de classification que votre entreprise utilise pour limiter l’accès aux employés de l’entreprise.

4. Créez la stratégie de fichier.

> [!NOTE]
> La possibilité d’appliquer une étiquette de classification directement dans Cloud App Security n’est actuellement prise en charge que pour Box, G suite, SharePoint Online et OneDrive entreprise.

## <a name="detect-stale-externally-shared-data"></a>Détecter les données partagées en externe obsolètes

Détectez les fichiers inutilisés et obsolètes, les fichiers qui n’ont pas été mis à jour récemment, qui sont accessibles publiquement via un lien public direct, une recherche Web ou des utilisateurs externes spécifiques.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer d’au moins une application connectée à l’aide de [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Étapes

1. Dans la page **stratégies** , créez une **stratégie de fichier**.

2. Sélectionnez et appliquez le modèle de stratégie **anciens fichiers partagés en externe**.

3. Personnaliser le filtre **modifié** pour qu’il corresponde à la stratégie de votre organisation.

4. Facultatif : définissez des actions de **gouvernance** à effectuer sur les fichiers lorsqu’une violation est détectée. Les actions de gouvernance disponibles varient d’un service à l’autre. Par exemple :

    - G suite : rendre le fichier privé et notifier le dernier éditeur de fichier

    - Box : notifier le dernier éditeur de fichier

    - SharePoint Online : rendre le fichier privé et envoyer un condensé de correspondance de stratégie au propriétaire du fichier

5. Créez la stratégie de fichier.

## <a name="detect-data-access-from-an-unauthorized-location"></a>Détecter l’accès aux données à partir d’un emplacement non autorisé

Détectez le moment où les fichiers sont accessibles à partir d’un emplacement non autorisé, en fonction des emplacements communs de votre organisation, afin d’identifier une fuite de données potentielle ou un accès malveillant.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer d’au moins une application connectée à l’aide de [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Étapes

1. Dans la page **stratégies** , créez une nouvelle **stratégie d’activité**.

2. Définissez le **type d’activité** de filtre sur les activités de fichier et de dossier qui vous intéressent, telles que l' **affichage**, le **Téléchargement**, **l’accès** et la **modification**.

3. Définissez l' **emplacement** du filtre n’est pas égal à, puis entrez les pays ou les régions à partir desquels votre organisation attend une activité.

    1. Facultatif : vous pouvez utiliser l’approche opposée et définir le filtre sur **emplacement** égal si votre organisation bloque l’accès à partir de pays ou régions spécifiques.

4. Facultatif : créez des actions de **gouvernance** à appliquer à une violation détectée (la disponibilité varie d’un service à l’autre), par exemple  **suspendre l’utilisateur**.

5. Créez la stratégie d’activité.

## <a name="detect-and-protect-confidential-data-store-in-a-non-compliant-sp-site"></a>Détecter et protéger la Banque de données confidentielles dans un site SP non conforme

Détectez les fichiers qui sont étiquetés comme confidentiels et qui sont stockés dans un site SharePoint non compatible.

### <a name="prerequisites"></a>Prérequis

Azure Information Protection étiquettes sont configurées et utilisées au sein de l’organisation.

### <a name="steps"></a>Étapes

1. Dans la page **stratégies** , créez une **stratégie de fichier**.

2. Définissez l' **étiquette de classification** de filtre sur **Azure information protection** est égal à l’étiquette **confidentiel** ou à l’équivalent de votre entreprise.

3. Définir le **dossier parent** du filtre n’est pas égal à, puis sous **Sélectionner un dossier** , choisissez tous les dossiers conformes dans votre organisation.

4. Sous **alertes** , sélectionnez **créer une alerte pour chaque fichier correspondant**.

5. Facultatif : définissez les actions de **gouvernance** à effectuer sur les fichiers lorsqu’une violation est détectée. Les actions de gouvernance disponibles varient d’un service à l’autre. Par exemple, définissez **Box** sur **Envoyer la stratégie de correspondance de la stratégie au propriétaire du fichier** et mettez-la **en quarantaine administrateur**.

6. Créez la stratégie de fichier.

## <a name="detect-externally-shared-source-code"></a>Détection du code source partagé en externe

Détectez quand des fichiers contenant du contenu pouvant être du code source sont partagés publiquement ou partagés avec des utilisateurs en dehors de votre organisation.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer d’au moins une application connectée à l’aide de [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Étapes

1. Dans la page **stratégies** , créez une **stratégie de fichier**.

2. Sélectionner et appliquer le **code source partagé en externe** du modèle de stratégie

3. Facultatif : Personnalisez la liste des **Extensions** de fichier pour qu’elles correspondent aux extensions de fichier de code source de votre organisation.

4. Facultatif : définissez les actions de **gouvernance** à effectuer sur les fichiers lorsqu’une violation est détectée. Les actions de gouvernance disponibles varient d’un service à l’autre. Par exemple, dans Box, **Envoyer une stratégie-faire correspondre le condensé au propriétaire du fichier** et **mettre en quarantaine administrateur**.

5. Sélectionner et appliquer le modèle de stratégie

## <a name="detect-unauthorized-access-to-group-data"></a>Détecter les accès non autorisés aux données de groupe

Détecte lorsque certains fichiers appartenant à un groupe d’utilisateurs spécifique sont accessibles de façon excessive par un utilisateur qui ne fait pas partie du groupe, ce qui peut constituer une menace Insider potentielle.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer d’au moins une application connectée à l’aide de [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Étapes

1. Dans la page **stratégies** , créez une nouvelle **stratégie d’activité**.

2. Sous **agir sur** sélectionner une **activité répétée** et personnaliser les **activités répétitives minimales** et définir une **plage** de temps conforme à la stratégie de votre organisation.

3. Définissez le **type d’activité** de filtre sur les activités de fichier et de dossier qui vous intéressent, telles que l' **affichage**, le **Téléchargement**, **l’accès** et la **modification**.

4. Affectez à l' **utilisateur** du filtre la valeur **à partir du groupe** égal, puis sélectionnez les groupes d’utilisateurs appropriés.

    > [!NOTE]
    > Les [groupes d’utilisateurs peuvent être importés manuellement](user-groups.md) à partir d’applications prises en charge.

5. Définissez les fichiers **et** les dossiers de filtre sur **des fichiers ou dossiers spécifiques** , puis choisissez les fichiers et les dossiers qui appartiennent au groupe d’utilisateurs audités.

6. Définissez les actions de **gouvernance** à effectuer sur les fichiers lorsqu’une violation est détectée. Les actions de gouvernance disponibles varient d’un service à l’autre. Par exemple, vous pouvez choisir de **suspendre l’utilisateur**.

7. Créez la stratégie de fichier.

## <a name="detect-publicly-accessible-s3-buckets"></a>Détecter les compartiments S3 accessibles publiquement

Détectez et protégez-vous contre les fuites de données potentielles provenant de compartiments AWS S3.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer d’une instance AWS connectée à l’aide de [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Étapes

1. Dans la page **stratégies** , créez une **stratégie de fichier**.

2. Sélectionnez et appliquez le modèle de stratégie **S3 compartiments (AWS)**.

3. Définissez les actions de **gouvernance** à effectuer sur les fichiers lorsqu’une violation est détectée. Les actions de gouvernance disponibles varient d’un service à l’autre. Par exemple, définissez AWS pour **rendre privé** , ce qui rend les compartiments S3 privés.

4. Créez la stratégie de fichier.

## <a name="detect-and-protect-gdpr-related-data-across-file-storage-apps"></a>Détectez et protégez les données liées à RGPD dans les applications de stockage de fichiers

Détectez les fichiers qui sont partagés dans les applications de stockage cloud et qui contiennent des informations d’identification personnelle et d’autres données sensibles qui sont liées par une stratégie de conformité RGPD. Ensuite, appliquez automatiquement des étiquettes de classification pour limiter l’accès uniquement au personnel autorisé.

### <a name="prerequisites"></a>Prérequis

- Vous devez disposer d’au moins une application connectée à l’aide de [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

- L' [intégration de Azure information protection (AIP)](azip-integration.md) est activée et l’étiquette RGPD est configurée dans AIP.

### <a name="steps"></a>Étapes

1. Dans la page **stratégies** , créez une **stratégie de fichier**.

2. Sous **méthode d’inspection**, sélectionnez **service de classification des données (DC)**, puis sous sélectionner un **type** , sélectionnez un ou plusieurs types d’informations conformes à la conformité RGPD, par exemple : numéro de carte de débit UE, numéro de licence des pilotes de l’UE, numéro d’identification nationale de l’UE, numéro de passeport UE, numéro d’identification de taxe de l’Union européenne.

3. Définissez les actions de **gouvernance** à effectuer sur les fichiers lors de la détection d’une violation, en sélectionnant **appliquer la gouvernance des étiquettes de classification** pour chaque application prise en charge.

4. Créer la stratégie de fichier

> [!NOTE]
> Actuellement, l' **étiquette de classification appliquer** est uniquement prise en charge pour Box, G suite, SharePoint Online et OneDrive entreprise.

## <a name="block-downloads-for-external-users-in-real-time"></a>Bloquer les téléchargements pour les utilisateurs externes en temps réel

Empêchez les données d’entreprise d’être défiltrées par des utilisateurs externes, en bloquant les téléchargements de fichiers en temps réel, en utilisant les [contrôles de session](proxy-intro-aad.md)de Cloud App Security.

### <a name="prerequisites"></a>Prérequis

- [Déployez le contrôle d’accès conditionnel aux applications pour les applications Azure ad](proxy-deployment-aad.md).

- Assurez-vous que votre application est une application basée sur SAML qui utilise Azure AD pour l’authentification unique. Pour plus d’informations sur les applications prises en charge, consultez [applications et clients pris en charge](proxy-intro-aad.md#supported-apps-and-clients).

### <a name="steps"></a>Étapes

1. Dans la page **stratégies** , créez une **stratégie de session**.

2. Sous **type de contrôle de session**, sélectionnez **contrôler le téléchargement du fichier (avec inspection)**.

3. Sous **filtres d’activité**, **Sélectionnez utilisateur** et affectez-lui la valeur **à partir du groupe** est égal à **utilisateurs externes**.

    >[!NOTE]
    > Vous n’avez pas besoin de définir de filtres d’application pour permettre à cette stratégie de s’appliquer à toutes les applications.

4. Vous pouvez utiliser le **filtre de fichiers** pour personnaliser le type de fichier. Vous bénéficiez ainsi d’un contrôle plus granulaire sur le type de fichiers contrôlés par la stratégie de session.

5. Sous **actions**, sélectionnez **bloquer**. Vous pouvez sélectionner **personnaliser le message de blocage** pour définir un message personnalisé à envoyer à vos utilisateurs afin qu’ils comprennent la raison pour laquelle le contenu est bloqué et comment il peut l’activer en appliquant l’étiquette de classification appropriée.

6. Cliquez sur **Créer**.

## <a name="enforce-read-only-mode-for-external-users-in-real-time"></a>Appliquer le mode lecture seule pour les utilisateurs externes en temps réel

Empêchez les données d’entreprise d’être défiltrées par des utilisateurs externes, en bloquant les activités d’impression et de copie/collage en temps réel, en utilisant les [contrôles de session](proxy-intro-aad.md)de Cloud App Security.

### <a name="prerequisites"></a>Prérequis

- [Déployez le contrôle d’accès conditionnel aux applications pour les applications Azure ad](proxy-deployment-aad.md).
- Assurez-vous que votre application est une application basée sur SAML qui utilise Azure AD pour l’authentification unique. Pour plus d’informations sur les applications prises en charge, consultez [applications et clients pris en charge](proxy-intro-aad.md#supported-apps-and-clients).

### <a name="steps"></a>Étapes

1. Dans la page **stratégies** , créez une **stratégie de session**.

2. Sous **type de contrôle de session**, sélectionnez **bloquer les activités**.

3. Dans le filtre de la **source d’activité** :

    1. Sélectionnez **utilisateur** et définissez **les utilisateurs externes** **dans groupe** .

    2. Sélectionnez le **type d’activité** est égal à **Imprimer** et **couper/copier l’élément**.

    > [!NOTE]
    > Vous n’avez pas besoin de définir de filtres d’application pour permettre à cette stratégie de s’appliquer à toutes les applications.

4. Facultatif : sous **méthode d’inspection**, sélectionnez le type d’inspection à appliquer et définissez les conditions requises pour l’analyse DLP.

5. Sous **actions**, sélectionnez **bloquer**. Vous pouvez sélectionner **personnaliser le message de blocage** pour définir un message personnalisé à envoyer à vos utilisateurs afin qu’ils comprennent la raison pour laquelle le contenu est bloqué et comment il peut l’activer en appliquant l’étiquette de classification appropriée.

6. Cliquez sur **Créer**.

## <a name="block-upload-of-unclassified-documents-in-real-time"></a>Bloquer le téléchargement de documents non classifiés en temps réel

Empêchez les utilisateurs de charger des données non protégées dans le Cloud, en utilisant les [contrôles de session](proxy-intro-aad.md)de Cloud App Security.

### <a name="prerequisites"></a>Prérequis

- [Déployez le contrôle d’accès conditionnel aux applications pour les applications Azure ad](proxy-deployment-aad.md).

- Assurez-vous que votre application est une application basée sur SAML qui utilise Azure AD pour l’authentification unique. Pour plus d’informations sur les applications prises en charge, consultez [applications et clients pris en charge](proxy-intro-aad.md#supported-apps-and-clients).

- Azure Information Protection étiquettes de classification doivent être configurées et utilisées au sein de votre organisation.

### <a name="steps"></a>Étapes

1. Dans la page **stratégies** , créez une **stratégie de session**.

2. Sous **type de contrôle de session**, sélectionnez **contrôler le téléchargement du fichier (avec inspection)** ou **Télécharger le fichier de contrôle (avec inspection)**.

   >[!NOTE]
   > Vous n’avez pas besoin de définir de filtres pour permettre l’application de cette stratégie à tous les utilisateurs et applications.

3. Sélectionnez l’étiquette de **classification** de filtre de fichier n’est pas égale, puis sélectionnez les étiquettes que votre entreprise utilise pour baliser les fichiers classifiés.

4. Facultatif : sous **méthode d’inspection**, sélectionnez le type d’inspection à appliquer et définissez les conditions requises pour l’analyse DLP.

5. Sous **actions**, sélectionnez **bloquer**. Vous pouvez sélectionner **personnaliser le message de blocage** pour définir un message personnalisé à envoyer à vos utilisateurs afin qu’ils comprennent la raison pour laquelle le contenu est bloqué et comment il peut l’activer en appliquant l’étiquette de classification appropriée.

6. Cliquez sur **Créer**.

> [!NOTE]
> Pour obtenir la liste des types de fichiers actuellement pris en charge par Cloud App Security pour Azure Information Protection des étiquettes de classification, voir [conditions préalables](azip-integration.md#prerequisites)à l’intégration de Azure information protection.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
