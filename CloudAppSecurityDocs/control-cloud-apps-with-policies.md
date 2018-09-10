---
title: Contrôler l’utilisation des applications cloud en créant des stratégies dans Cloud App Security | Microsoft Docs
description: Cette rubrique fournit des informations sur la façon dont les stratégies sont utilisées et configurées pour contrôler l’usage des applications cloud.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 14d10238-0f61-43e9-ab96-71534a27d3d4
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 65e2d98eb6905e4723032cd1a1480158e42be492
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44144259"
---
*S’applique à : Microsoft Cloud App Security*


# <a name="control-cloud-apps-with-policies"></a>Contrôler les applications cloud avec des stratégies

Grâce aux stratégies, vous pouvez définir la façon dont vous souhaitez que vos utilisateurs se comportent dans le cloud. Vous pouvez détecter les comportements à risques, les violations ou les activités et les points de données suspects dans votre environnement cloud et, si nécessaire, intégrer des flux de travail de correction pour atténuer les risques de façon efficace. Il existe plusieurs types de stratégies suivant les différents types d’informations que vous voulez collecter sur votre environnement cloud et les types de mesures correctives que vous pouvez souhaiter prendre.  
  
Par exemple, le type de stratégie à mettre en place diffère selon que vous souhaitez mettre en quarantaine une menace de violation de données ou empêcher votre organisation d’utiliser une application cloud à risque.  
  
## <a name="policy-types"></a>Types de stratégies  
Lorsque vous examinez la page **Stratégie**, les différentes stratégies et les différents modèles peuvent être distingués par type et par icône pour savoir quelles stratégies sont disponibles. Les stratégies disponibles dépendent de la source de données et de ce que vous avez activé dans Cloud App Security pour votre organisation ; par exemple, si vous avez téléchargé des journaux Cloud Discovery, les stratégies relatives à Cloud Discovery sont affichées.

Vous pouvez créer les types de stratégies suivants :  
  
|Icône de type de stratégie|Type de stratégie|Utiliser|  
|-----|-----------------|---------|  
|![icône de stratégie d’accès](./media/proxy-policy.png)|Stratégie d’accès|Les stratégies d’accès vous offrent une surveillance et un contrôle en temps réel des connexions utilisateur à vos applications cloud.|
|![Icône de stratégie d’activité](./media/activity_policy.png)|Stratégie d’activité|Grâce aux stratégies d’activité, vous pouvez appliquer une large gamme de processus automatisés en exploitant les API du fournisseur d’application. Ces stratégies vous permettent de surveiller des activités spécifiques effectuées par différents utilisateurs ou de suivre les taux anormalement élevés d’un certain type d’activité.|  
|![Icône de stratégie de détection d’anomalie](./media/anomaly_detection_policy.png)|Stratégie de détection d’anomalie|Grâce aux stratégies de détection d’anomalie, vous pouvez rechercher les activités inhabituelles sur votre cloud en fonction des facteurs de risque que vous définissez ici, afin d’être averti en cas d’événement anormal par rapport aux activités de référence ou habituelles de votre organisation ou de l’utilisateur.|  
|![Icône de stratégie Cloud Discovery](./media/discovery_policy.png)|Stratégie de découverte d’application|Grâce aux stratégies de découverte d’application, vous pouvez définir des alertes qui vous informent quand de nouvelles applications sont détectées au sein de votre organisation.|  
|![Icône de stratégie de détection d’anomalie](./media/anomaly_detection_policy.png)|Stratégie de détection des anomalies de Cloud Discovery|Les stratégies de détection des anomalies de Cloud Discovery examinent les journaux que vous utilisez pour découvrir les applications cloud et recherchent les occurrences inhabituelles. À titre d’exemple, citons un utilisateur qui n’a jamais utilisé Dropbox et qui y charge soudainement 600 Go de données ou une application qui fait l’objet de transactions dans des proportions inhabituelles.|  
|![Icône de stratégie de fichier](./media/file_policy.png)|Stratégie de fichier|Grâce aux stratégies de fichier, vous pouvez déterminer si vos applications cloud comportent certains fichiers ou types de fichiers (partagés, partagés avec des domaines externes) ou certaines données (informations propriétaires, PII, informations de carte de crédit, etc.) et appliquer des actions de gouvernance aux fichiers (les actions de gouvernance sont spécifiques aux applications cloud).|  
|![icône de stratégie de session](./media/proxy-policy.png)|Stratégie de session|Les stratégies de session vous offrent une surveillance et un contrôle en temps réel des activités utilisateur dans vos applications cloud.|

  
## <a name="identifying-risk"></a>Identification des risques  
Cloud App Security vous permet d’atténuer différents risques dans le cloud. Vous pouvez configurer n’importe quelles stratégie et alerte à associer à un des risques suivants :  
  
-   **Contrôle d’accès :** Qui accède à quoi à partir d’où ?  
  
     Surveillez le comportement et détectez les activités anormales en continu, notamment les attaques externes et internes à haut risque, et appliquez une stratégie d’alerte, de blocage ou de vérification d’identité pour toute application ou action spécifique dans une application. Cette approche permet de mettre en place des stratégies de contrôle d’accès locales et mobiles basées sur l’utilisateur, l’appareil et la zone géographique, avec un blocage grossier et des procédures d’affichage, de modification et de blocage précises. Détectez les événements de connexion suspects, notamment les échecs d’authentification multifacteur, les échecs de connexion de compte désactivé et les événements d’emprunt d’identité.  
  
-   **Conformité :** Vos contraintes de conformité sont-elles enfreintes ?  
  
     Classez et identifiez les données sensibles ou réglementées, notamment les autorisations de partage pour chaque fichier, stockées dans des services de synchronisation de fichier pour assurer la conformité aux réglementations telles que PCI, SOX et HIPAA  
  
-   **Contrôle de configuration :**  Votre configuration fait-elle l’objet de modifications non autorisées ?  
  
     Surveillez les modifications de configuration, notamment la manipulation de la configuration à distance.  
  
-   **Cloud Discovery :**  Des applications nouvelles sont-elles utilisées dans votre organisation ? Des applications Shadow IT que vous ignorez sont-elles utilisées ?  
  
     L’évaluation du risque global pour chaque application cloud en fonction des certifications réglementaires et du secteur et des bonnes pratiques vous permet de surveiller le nombre d’utilisateurs, les activités, le volume du trafic et les heures d’utilisation classiques pour  
    chaque application cloud.  
  
-   **DLP :** Des fichiers propriétaires sont-ils partagés publiquement ? Devez-vous mettre des fichiers en quarantaine ?  
  
     L’intégration locale de DLP permet une intégration aux solutions DLP locales existantes et une correction en circuit fermé.  
  
-   **Comptes privilégiés :** Devez-vous surveiller les comptes d’administrateur ?  
  
     Surveillez les activités des administrateurs et utilisateurs disposant de privilèges et créez des rapports associés en temps réel.  
  
-   **Contrôle partagé :** Comment les données sont-elles partagées dans votre environnement cloud ?  
  
     Inspectez le contenu des fichiers et du cloud et appliquez des stratégies de partage interne et externe. Surveillez la collaboration et appliquez des stratégies de partage, telles que l’interdiction de partager des fichiers à l’extérieur de votre organisation.  
  
-   **Détection de menaces :** Des activités suspectes menacent-elles votre environnement cloud ?  
  
     Recevez des notifications en temps réel pour toute violation de stratégie ou franchissement de seuil d’activité par SMS ou e-mail. En appliquant des algorithmes Machine Learning, Cloud App Security vous permet de détecter un comportement qui peut indiquer qu’un utilisateur exploite des données de manière inappropriée.  
  
## <a name="how-to-control-risk"></a>Comment contrôler le risque  
Procédez comme suit pour contrôle le risque avec des stratégies :  
  
1.  Créez une stratégie à partir d’un modèle ou d’une requête.  
  
2.  Affinez la stratégie pour atteindre les résultats attendus.  
  
3.  Ajoutez des actions automatisées pour réagir et remédier aux risques automatiquement.  
  
### <a name="create-a-policy"></a>Créer une stratégie  
Vous pouvez baser toutes vos stratégies sur les modèles de stratégie de Cloud App Security ou créer des stratégies à partir d’une requête.  
  
Les modèles de stratégie vous aident à définir les filtres et configurations nécessaires pour détecter dans votre environnement des événements spécifiques dignes d’intérêt. Les modèles comprennent des stratégies de tous types et peuvent s’appliquer à divers services.  
  
Pour créer une stratégie à partir de **modèles de stratégie**, effectuez les étapes suivantes :  
  
1. Dans la console, cliquez sur **Contrôle**, puis sur **Modèles**.  
  
    ![](./media/create-policy-from-template.png)  
  
2. Cliquez sur le signe **+** tout à droite de la ligne du modèle à utiliser. Une page de création de stratégie s’ouvre, contenant la configuration prédéfinie du modèle.  
  
3. Modifiez le modèle en fonction des besoins de votre stratégie personnalisée. Vous pouvez modifier librement chaque propriété et champ de cette nouvelle stratégie basée sur un modèle.  
   > [!NOTE] 
   >Quand vous utilisez des filtres de stratégie, le filtre **Contains (Contient)** recherche uniquement des mots entiers, séparés par des virgules, points, espaces ou traits de soulignement. Par exemple, si vous recherchez **malware** ou **virus**, il trouve virus_malware_file.exe, mais pas malwarevirusfile.exe. Si vous recherchez *malware.exe*, vous obtenez TOUS les fichiers exe dont le nom contient malware ou exe, tandis que si vous recherchez **"malware.exe"** (avec les guillemets), vous n’obtenez que les fichiers dont le nom contient exactement « malware.exe ». 
    **Equals (Est égal à)** recherche uniquement la chaîne complète ; par exemple, si vous recherchez *malware.exe*, il trouve malware.exe, mais pas malware.exe.txt.  
4. Une fois la stratégie basée sur un modèle créée, un lien vers celle-ci s’affiche dans la colonne **Stratégies liées** de la table des modèles de stratégie, en regard du modèle à partir duquel la stratégie a été créée.   
    Vous pouvez, à partir de chaque modèle, créer autant de stratégies que vous le souhaitez, qui seront toutes liées au modèle d’origine ; ainsi, vous pouvez effectuer le suivi de toutes les stratégies créées à l’aide du même modèle.  
  
Vous pouvez également **créer une stratégie au cours d’un examen**. Si vous examinez le **Journal d’activité**, les **Fichiers** ou les **Comptes** à la recherche d’un élément spécifique, à tout moment, vous pouvez créer une stratégie basée sur les résultats de votre examen.  
  
Cela peut arriver si vous examinez le **Journal d’activité** et que vous constatez qu’une activité d’administration ne provient pas de la plage d’adresses IP de votre bureau.

  
Pour créer une stratégie basée sur les résultats de l’examen, effectuez les étapes suivantes :  
  
1.  Dans la console, cliquez sur **Examiner**, puis sur **Journal d’activité**, **Fichiers** ou **Comptes**.  
  
2.  Utilisez les filtres en haut de la page pour limiter les résultats de la recherche à la zone suspecte. Par exemple, dans la page Journal d’activité, cliquez sur **Activité** et sélectionnez **Ouverture de session administrateur**. Ensuite, sous **Adresse IP**, sélectionnez **Catégorie** et définissez la valeur de manière à ne pas inclure les catégories d’adresses IP que vous avez créées pour vos domaines reconnus, notamment les adresses IP de l’administrateur, de l’entreprise et du réseau privé virtuel.  
  
     ![Créer un fichier à la suite d’un examen](./media/create-file-from-investigation.png)  
  
3.  Dans l’angle supérieur droit de la console, cliquez sur **Nouvelle stratégie à partir de la recherche**![](./media/new-policy-from-search-button.png)  
  
4.  Une page de création de stratégie s’ouvre, contenant les filtres que vous avez utilisés dans votre examen.  
  
5.  Modifiez le modèle en fonction des besoins de votre stratégie personnalisée. Vous pouvez modifier librement chaque propriété et champ de cette nouvelle stratégie basée sur un examen.  
   
> [!NOTE] 
> Quand vous utilisez des filtres de stratégie, le filtre **Contains (Contient)** recherche uniquement des mots entiers, séparés par des virgules, points, espaces ou traits de soulignement. Par exemple, si vous recherchez **malware** ou **virus**, il trouve virus_malware_file.exe, mais pas malwarevirusfile.exe.  
     **Equals (Est égal à)** recherche uniquement la chaîne complète ; par exemple, si vous recherchez **malware.exe**, il trouve malware.exe, mais pas malware.exe.txt.  
  
 
 
![créer une stratégie d’activité basée sur un examen](./media/create-activity-policy-from-investigation.png)
 
 
  
> [!NOTE]  
>  Pour plus d’informations sur la définition des champs d’une stratégie, consultez la documentation de stratégie correspondante :  
>   
>  [Stratégies d’activité utilisateur](user-activity-policies.md)  
>   
>  [Stratégies de protection des données](data-protection-policies.md)  
>   
>  [Stratégies Cloud Discovery](cloud-discovery-policies.md)  

  
### <a name="add-automated-actions-to-respond-and-remediate-risks-automatically"></a>Ajouter des actions automatisées pour réagir et remédier aux risques automatiquement

Pour obtenir la liste des actions de gouvernance disponibles par application, consultez [Gouvernance des applications connectées](governance-actions.md).

Vous pouvez également définir la stratégie pour qu’elle vous envoie une alerte par e-mail ou message texte lors de la détection de correspondances. 

Pour définir vos préférences de notification, vous devez [personnaliser le portail](general-setup.md) 
  
> [!NOTE] 
> Le nombre maximal d’alertes envoyées via SMS est de 10 par numéro de téléphone par jour. Le jour est calculé selon le fuseau horaire UTC. 


## <a name="enable-and-disable-policies"></a>Activer et désactiver des stratégies

Une fois que vous avez créé une stratégie, vous pouvez l’activer ou la désactiver. Cela vous évite de devoir la supprimer pour l’arrêter. Donc, si vous souhaitez arrêter une stratégie pour une raison ou une autre, désactivez-la. Vous pouvez la réactiver à tout moment.

- Pour activer une stratégie, dans la page **Stratégie**, cliquez sur les trois points situés à la fin de la ligne de la stratégie à activer, puis sélectionnez **Activer**. 

![Activer une stratégie](./media/enable-policy.png)

- Pour désactiver une stratégie, dans la page **Stratégie**, cliquez sur les trois points situés à la fin de la ligne de la stratégie à désactiver, puis sélectionnez **Désactiver**.

![Désactiver une stratégie](./media/disable-policy.png)

Quand vous créez une stratégie, celle-ci est activée par défaut.

## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  