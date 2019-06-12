---
title: Stratégies de protection des informations - Cloud App Security | Microsoft Docs
description: Cette rubrique décrit les étapes pour configurer de nombreuses stratégies de protection des informations dans Cloud App Security.
author: rkarlin
ms.author: rkarlin
ms.date: 06/13/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.assetid: 9a616767-4558-46f1-9da8-aa337920ae45
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: e4b07d47ece8da911e7d8a4a1bd210641f590b36
ms.sourcegitcommit: 9f671d5dd5e5da023d598425442d8736546ca183
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66837777"
---
# <a name="information-protection-policies"></a>Stratégies de protection des informations

*S’applique à : Microsoft Cloud App Security*

Stratégies de fichier cloud App Security permettent d’appliquer une large gamme de processus automatisés. Peuvent définir des stratégies pour assurer la protection des informations, y compris les analyses continues de conformité, des tâches eDiscovery réglementaires et DLP contenu sensible partagé publiquement.

Cloud App Security peut surveiller n’importe quel type de fichier en fonction de plus de 20 filtres de métadonnées, par exemple, type de niveau d’accès et de fichier. Pour plus d’informations, consultez [stratégies de fichier](data-protection-policies.md).

## <a name="detect-and-prevent-external-sharing-of-sensitive-data"></a>Détecter et empêcher le partage externe des données sensibles

Détecte lorsque des fichiers avec des informations d’identification personnelle ou d’autres données sensibles sont stockées dans un service Cloud et partagés avec les utilisateurs qui sont externes à votre organisation qui enfreint la stratégie de sécurité de votre entreprise et crée une violation potentielle de la conformité.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer d’au moins une application connectée à l’aide [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).
 
### <a name="steps"></a>Étapes

1. Sur le **stratégies** page, créez une nouvelle **stratégie de fichier**.

2. Définissez le filtre **niveau d’accès** est égal à **Public (Internet) / Public / externe**.

3. Sous **méthode d’Inspection**, sélectionnez **Service de Classification des données (DC)** , puis, sous **sélectionner le type** sélectionner le type d’informations sensibles que vous souhaitez que les contrôleurs de domaine à inspecter.

6. Configurer le **gouvernance** actions à prendre lorsqu’une alerte est déclenchée. Par exemple, vous pouvez créer une action de gouvernance qui s’exécute sur les violations de fichier détecté dans G Suite dans lequel vous sélectionnez l’option à **supprimer des utilisateurs externes** et **supprimer l’accès public**.

7. Créer la stratégie de fichier.

## <a name="detect-externally-shared-confidential-data"></a>Détecter les données confidentielles partagées en externe

Détecter quand les fichiers qui sont étiquetées **confidentiel** et sont stockés dans un cloud service sont partagées avec des utilisateurs externes, conformes aux stratégies d’entreprise.

### <a name="prerequisites"></a>Prérequis

- Vous devez disposer d’au moins une application connectée à l’aide [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

- Activer [intégration d’Azure Information Protection](azip-integration.md).

### <a name="steps"></a>Étapes

1.  Sur le **stratégies** page, créez une nouvelle **stratégie de fichier**.

2.  Définissez le filtre **étiquette de Classification** à **Azure Information Protection** est égale à la **confidentiel** équivalent du étiquette, ou votre entreprise.

3.  Définissez le filtre **niveau d’accès** est égal à **Public (Internet) / Public / externe**.

1.  Facultatif : Définir le **gouvernance** actions à entreprendre sur les fichiers lorsqu’une violation est détectée. Les actions de gouvernance disponibles varient entre les services.

5.  Créer la stratégie de fichier.

## <a name="detect-and-encrypt-sensitive-data-at-rest"></a>Détecter et de chiffrer les données sensibles au repos

Détecter les fichiers contenant des informations d’identification personnelle et d’autres données sensibles sont partagent dans une application cloud et appliquent des étiquettes de classification pour limiter l’accès uniquement aux employés de votre société.

### <a name="prerequisites"></a>Prérequis

- Vous devez disposer d’au moins une application connectée à l’aide [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

- Activer [intégration d’Azure Information Protection](azip-integration.md).
 
### <a name="steps"></a>Étapes

1.  Sur le **stratégies** page, créez une nouvelle **stratégie de fichier**.

2.  Sous **méthode d’Inspection**, sélectionnez **Service de Classification des données (DC)** et sous **sélectionner le type** sélectionner le type d’informations sensibles que vous souhaitez que les contrôleurs de domaine à inspecter.

5.  Sous **alerte**, vérifiez **appliquer la gouvernance d’étiquette de classification** et sélectionnez l’étiquette de classification que votre entreprise utilise pour restreindre l’accès aux employés de la société. 

6.  Créer la stratégie de fichier.

> [!NOTE]
> La possibilité d’appliquer une étiquette de classification directement dans Cloud App Security est actuellement uniquement pris en charge pour Box, G Suite, SharePoint online et OneDrive entreprise.

## <a name="detect-stale-externally-shared-data"></a>Détecter les de données partagées en externe obsolètes

Détecter les fichiers inutilisés et obsolètes, les fichiers qui n’étaient pas mis à jour récemment, et qui sont accessibles publiquement via un lien public direct, recherche web, ou à des utilisateurs externes spécifiques.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer d’au moins une application connectée à l’aide [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Étapes

1.  Sur le **stratégies** page, créez une nouvelle **stratégie de fichier**.

2.  Sélectionner et appliquer le modèle de stratégie **obsolètes partagés en externe fichiers**.

3.  Personnaliser le filtre **dernière modification** pour correspondre à la stratégie de votre organisation.

4.  Facultatif : Définissez **gouvernance** actions à entreprendre sur les fichiers lorsqu’une violation est détectée. Les actions de gouvernance disponibles varient entre les services. Exemple :

    - G Suite : Rendre le fichier privé et notifier le dernier éditeur du fichier

    - Zone : Notifier le dernier éditeur du fichier

    - SharePoint online : Le fichier privé et d’envoyer un résumé des correspondances de stratégie au propriétaire du fichier

6.  Créer la stratégie de fichier.

## <a name="detect-data-access-from-an-unauthorized-location"></a>Détecter l’accès aux données à partir d’un emplacement non autorisé

Détecter quand les fichiers sont accessibles à partir d’un emplacement non autorisé, en fonction des emplacements courants de votre organisation, pour identifier une fuite de données ou d’un accès malveillant.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer d’au moins une application connectée à l’aide [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).
### <a name="steps"></a>Étapes

1. Sur le **stratégies** page, créez une nouvelle **stratégie d’activité**.

2. Définissez le filtre **type d’activité** pour les activités de fichiers et dossiers qui vous intéressent, tels que **vue**, **télécharger**, **accès**et  **Modifier**.

3. Définissez le filtre **emplacement** ne pas égaux et puis entrez les pays à partir de laquelle votre organisation souhaite activité. 

    1.  Facultatif : Vous pouvez utiliser l’approche contraire et définissez le filtre sur **emplacement** est égal à si les blocs de votre organisation accèdent à des pays spécifiques.

4.  Facultatif : Créer **gouvernance** actions à appliquer au détecté violation (disponibilité varie entre les services), tel que **suspendre l’utilisateur**.

6.  Créer la stratégie d’activité.

## <a name="detect-and-protect-confidential-data-store-in-a-non-compliant-sp-site"></a>Détecter et de protéger la banque de données confidentielles dans un site SP non conforme

Détecter les fichiers qui sont étiquetés comme confidentiels et sont stockés dans un site SharePoint non conforme.

### <a name="prerequisites"></a>Prérequis

Les étiquettes Azure Information Protection sont configurés et utilisés dans l’entreprise.

### <a name="steps"></a>Étapes

1.  Sur le **stratégies** page, créez une nouvelle **stratégie de fichier**.

2.  Définissez le filtre **étiquette de Classification** à **Azure Information Protection** est égale à la **confidentiel** équivalent du étiquette, ou votre entreprise.

3.  Définissez le filtre **dossier Parent** n’est pas égale, puis sous **sélectionner un dossier** choisissez tous les dossiers conformes dans votre organisation.

6.  Sous **alertes** sélectionnez **créer une alerte pour chaque fichier correspondant**.

7.  Facultatif : Définir le **gouvernance** actions à entreprendre sur les fichiers lorsqu’une violation est détectée. Les actions de gouvernance disponibles varient entre les services. Par exemple, définissez **boîte** à **digest de correspondance de stratégie d’envoi au propriétaire du fichier** et **mettre en quarantaine administrateur**.

8.  Créer la stratégie de fichier.

## <a name="detect-externally-shared-source-code"></a>Détecter le code source partagé en externe

Détecter lorsque des fichiers qui contiennent du contenu qui peut être de code source sont partagés publiquement ou sont partagés avec les utilisateurs en dehors de votre organisation.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer d’au moins une application connectée à l’aide [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Étapes

1.  Sur le **stratégies** page, créez une nouvelle **stratégie de fichier**.

2.  Sélectionner et appliquer le modèle de stratégie **partagées en externe de code source**

3.  Facultatif : Personnaliser la liste des fichiers **Extensions** pour faire correspondre les extensions de fichier de code source de votre organisation.

4. Facultatif : Définir le **gouvernance** actions à entreprendre sur les fichiers lorsqu’une violation est détectée. Les actions de gouvernance disponibles varient entre les services. Par exemple, dans la zone, **digest de correspondance de stratégie d’envoi au propriétaire du fichier** et **mettre en quarantaine administrateur**.

5. Sélectionner et appliquer le modèle de stratégie

## <a name="detect-unauthorized-access-to-group-data"></a>Détecter tout accès non autorisé aux données de groupe

Détecter lorsque certains fichiers qui appartiennent à un groupe d’utilisateurs spécifique sont excessivement accédés par un utilisateur qui ne fait pas partie du groupe, ce qui pourrait être une menace interne potentiels.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer d’au moins une application connectée à l’aide [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Étapes

1. Sur le **stratégies** page, créez une nouvelle **stratégie d’activité**.

2.  Sous **agir sur** sélectionnez **activité répétée** et personnaliser le **au Minimum les activités répétées** et définir un **laps de temps** pour se conformer à votre stratégie de l’organisation.

3.  Définissez le filtre **type d’activité** pour les activités de fichiers et dossiers qui vous intéressent, tels que **vue**, **télécharger**, **accès**et  **Modifier**.

4.  Définissez le filtre **utilisateur** à **groupe** est égal à, puis sélectionnez les groupes d’utilisateurs appropriés. 

> [!NOTE]
> [Groupes d’utilisateurs peuvent être importés manuellement](user-groups.md) à partir d’applications prises en charge.

6.  Définissez le filtre **fichiers et dossiers** à **certains fichiers ou dossiers** est égal à, puis choisissez les fichiers et dossiers qui appartiennent au groupe d’utilisateurs audités.

9.  Définir le **gouvernance** actions à entreprendre sur les fichiers lorsqu’une violation est détectée. Les actions de gouvernance disponibles varient entre les services. Par exemple, vous pouvez choisir à **suspendre l’utilisateur**.

11. Créer la stratégie de fichier.

## <a name="detect-publicly-accessible-s3-buckets"></a>Détecter les compartiments S3 accessibles publiquement

Détecter et de protection contre les fuites de données potentielles à partir de compartiments de AWS S3.

### <a name="prerequisites"></a>Prérequis

Vous devez disposer d’une instance AWS connectée à l’aide de [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

### <a name="steps"></a>Étapes

1.  Sur le **stratégies** page, créez une nouvelle **stratégie de fichier**.

2.  Sélectionner et appliquer le modèle de stratégie **compartiments S3 accessibles publiquement (AWS)** .

3.  Définir le **gouvernance** actions à entreprendre sur les fichiers lorsqu’une violation est détectée. Les actions de gouvernance disponibles varient entre les services. Par exemple, la valeur AWS **rendre privé** qui rendrait la S3 compartiments privé.

5.  Créer la stratégie de fichier.

## <a name="detect-and-protect-gdpr-related-data-across-file-storage-apps"></a>Détecter et RGPD de protéger des données liées entre des applications de stockage de fichiers 

Détecter les fichiers qui sont partagés dans les applications de stockage cloud et contiennent des informations d’identification personnelle et d’autres données sensibles qui sont liées par une stratégie de conformité RGPD. Ensuite, appliquer automatiquement des étiquettes de classification pour limiter l’accès uniquement au personnel autorisé.

### <a name="prerequisites"></a>Prérequis

- Vous devez disposer d’au moins une application connectée à l’aide [connecteurs d’application](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md).

- [Intégration d’Azure Information Protection](azip-integration.md) est activé et l’étiquette de RGPD est configurée dans AIP.

### <a name="steps"></a>Étapes

1.  Sur le **stratégies** page, créez une nouvelle **stratégie de fichier**.

2.  Sous **méthode d’Inspection**, sélectionnez **Service de Classification des données (DC)** , puis, sous **sélectionner le type** sélectionner un ou plusieurs types d’informations que respecter la législation GDPR conformité, par exemple : Numéro de carte de crédit de l’Union européenne, de pilotes de l’Union européenne licence numéro, numéro national d’identification de l’Union européenne, numéro de passeport de l’Union européenne, numéro d’identification de taxe SSN de l’Union européenne, les unités de recherche.

5.  Définir le **gouvernance** actions à entreprendre sur les fichiers lorsqu’une violation est détectée, en sélectionnant **gouvernance d’étiquette de Classification s’appliquent** pour chaque application de prise en charge.

7.  Créer la stratégie de fichier

> [!NOTE]
>  Actuellement, **appliquer l’étiquette de classification** est uniquement pris en charge pour Box, G Suite, SharePoint online et OneDrive entreprise.

## <a name="block-downloads-for-external-users-in-real-time"></a>Bloquer les téléchargements pour les utilisateurs externes en temps réel

Empêcher les données d’entreprise à partir d’en cours exfiltrated par des utilisateurs externes, en bloquant les téléchargements de fichiers en temps réel, en utilisant Cloud App Security [contrôles de session](proxy-intro-aad.md).

### <a name="prerequisites"></a>Prérequis

- [Déployer le contrôle d’accès conditionnel aux applications Azure AD](proxy-deployment-aad.md).

- Assurez-vous que votre application est une application basée sur SAML qui utilise Azure AD pour l’authentification unique. Pour plus d’informations sur les applications prises en charge, consultez [prise en charge des applications et clients](proxy-intro-aad.md#supported-apps-and-clients).

### <a name="steps"></a>Étapes

1. Sur le **stratégies** page, créez une nouvelle **stratégie de Session**.

2. Sous **Type de contrôle de session**, sélectionnez **Contrôler le téléchargement du fichier (avec DLP)** .

3. Sous **filtres d’activité**, sélectionnez **utilisateur** et affectez-lui la valeur **groupe** est égal à **des utilisateurs externes**.

   >[!NOTE]
   > Vous n’avez pas besoin de définir des filtres d’application pour activer cette stratégie à appliquer à toutes les applications.

1. Vous pouvez utiliser la **filtre de fichier** pour personnaliser le type de fichier. Cela vous donne un contrôle plus précis sur le type de fichiers que les contrôles de stratégie de session.

2. Sous **Actions**, sélectionnez **bloc**. Vous pouvez sélectionner **personnaliser le message de bloc** pour définir un message personnalisé à envoyer à vos utilisateurs afin qu’ils comprennent la raison pour laquelle le contenu est bloqué et comment ils peuvent l’activer en appliquant l’étiquette de classification appropriée.

3. Cliquez sur **Create (Créer)** .

  
## <a name="enforce-read-only-mode-for-external-users-in-real-time"></a>Appliquer le mode en lecture seule pour les utilisateurs externes en temps réel

Empêcher les données d’entreprise ne soient pas exfiltrated par des utilisateurs externes, en bloquant les imprimer et copier/coller des activités en temps réel, en utilisant Cloud App Security [contrôles de session](proxy-intro-aad.md).

### <a name="prerequisites"></a>Prérequis

-   [Déployer le contrôle d’accès conditionnel aux applications Azure AD](proxy-deployment-aad.md).
-   Assurez-vous que votre application est une application basée sur SAML qui utilise Azure AD pour l’authentification unique. Pour plus d’informations sur les applications prises en charge, consultez [prise en charge des applications et clients](proxy-intro-aad.md#supported-apps-and-clients).
 
### <a name="steps"></a>Étapes

1. Sur le **stratégies** page, créez une nouvelle **stratégie de Session**.

2. Sous **type de contrôle de Session**, sélectionnez **bloquer les activités**.

3. Dans le **source d’activité** filtre :
   
    1. Sélectionnez **utilisateur** et définissez **groupe** à **des utilisateurs externes**.

    2. Sélectionnez **type d’activité** est égal à **impression** et **couper/copier un élément**.

    > [!NOTE]
    > Vous n’avez pas besoin de définir des filtres d’application pour activer cette stratégie à appliquer à toutes les applications.

4. Facultatif : Sous **méthode d’Inspection**, sélectionnez le type de contrôle à appliquer et de définir les conditions nécessaires pour l’analyse DLP.

5. Sous **Actions**, sélectionnez **bloc**. Vous pouvez sélectionner **personnaliser le message de bloc** pour définir un message personnalisé à envoyer à vos utilisateurs afin qu’ils comprennent la raison pour laquelle le contenu est bloqué et comment ils peuvent l’activer en appliquant l’étiquette de classification appropriée.

6. Cliquez sur **Create (Créer)** .

## <a name="block-upload-of-unclassified-documents-in-real-time"></a>Chargement de bloc de documents non classifiées en temps réel

Empêcher les utilisateurs de télécharger des données non protégées dans le cloud, en utilisant Cloud App Security [contrôles de session](proxy-intro-aad.md).

### <a name="prerequisites"></a>Prérequis

- [Déployer le contrôle d’accès conditionnel aux applications Azure AD](proxy-deployment-aad.md).

- Assurez-vous que votre application est une application basée sur SAML qui utilise Azure AD pour l’authentification unique. Pour plus d’informations sur les applications prises en charge, consultez [prise en charge des applications et clients](proxy-intro-aad.md#supported-apps-and-clients).

- Étiquettes de classification Azure Information Protection doivent être configurés et utilisés à l’intérieur de votre organisation.

### <a name="steps"></a>Étapes

1. Sur le **stratégies** page, créez une nouvelle **stratégie de Session**.

2. Sous **type de contrôle de Session**, sélectionnez **chargement de fichiers de contrôle (avec DLP)** ou **contrôler le téléchargement du fichier (avec DLP)** .

   >[!NOTE]
   > Vous n’avez pas besoin de définir des filtres pour activer cette stratégie à appliquer à tous les utilisateurs et applications.

3. Sélectionnez le filtre de fichier **étiquette de Classification** ne pas égaux et puis sélectionnez les étiquettes de votre entreprise utilise pour baliser les fichiers classifiés.

2. Facultatif : Sous **méthode d’Inspection**, sélectionnez le type de contrôle à appliquer et de définir les conditions nécessaires pour l’analyse DLP.

3. Sous **Actions**, sélectionnez **bloc**. Vous pouvez sélectionner **personnaliser le message de bloc** pour définir un message personnalisé à envoyer à vos utilisateurs afin qu’ils comprennent la raison pour laquelle le contenu est bloqué et comment ils peuvent l’activer en appliquant l’étiquette de classification appropriée.

4. Cliquez sur **Create (Créer)** .

> [!NOTE]
> Pour la liste des types de fichiers Cloud App Security prend actuellement en charge pour les étiquettes de classification Azure Information Protection, consultez [prérequis de l’intégration d’Azure Information Protection](azip-integration.md#prerequisites).


## <a name="next-steps"></a>Étapes suivantes 

[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)  
  
  
