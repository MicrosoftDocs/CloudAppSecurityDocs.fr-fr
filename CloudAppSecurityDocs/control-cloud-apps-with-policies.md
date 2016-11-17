---
title: "Contrôler les applications cloud avec des stratégies | Documentation Microsoft"
description: "Cette rubrique fournit des informations sur la façon dont les stratégies sont utilisées et configurées pour contrôler l’usage des applications cloud."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 14d10238-0f61-43e9-ab96-71534a27d3d4
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2cb87afa3c5342e01cfd4049669ac4b3b7efa4fe
ms.openlocfilehash: 36f249cbb900bdb516ea6909a0ed6c76b4ea3ab4


---
# <a name="control-cloud-apps-with-policies"></a>Contrôler les applications cloud avec des stratégies

Grâce aux stratégies, vous pouvez définir la façon dont vous souhaitez que vos utilisateurs se comportent dans le cloud. Vous pouvez détecter les comportements à risques, les violations ou les activités et les points de données suspects dans votre environnement cloud et, si nécessaire, intégrer des flux de travail de correction pour atténuer les risques de façon efficace. Il existe plusieurs types de stratégies suivant les différents types d’informations que vous voulez collecter sur votre environnement cloud et les types de mesures correctives que vous pouvez souhaiter prendre.  
  
Par exemple, le type de stratégie à mettre en place diffère selon que vous souhaitez mettre en quarantaine une menace de violation de données ou empêcher votre organisation d’utiliser une application cloud à risque.  
  
## <a name="policy-types"></a>Types de stratégies  
Lorsque vous examinez la page **Stratégie**, les différentes stratégies et les différents modèles peuvent être distingués par type et par icône pour savoir quelles stratégies seront disponibles. Les stratégies disponibles dépendent de la source de données et de ce que vous avez activé dans Cloud App Security pour votre organisation ; par exemple, si vous avez téléchargé des journaux Cloud Discovery, les stratégies relatives à Cloud Discovery sont affichées.

Vous pouvez créer les types de stratégies suivants :  
  
|Icône de type de stratégie|Type de stratégie|Utilisez|  
|-----|-----------------|---------|  
|![Icône de stratégie d’activité](./media/activity_policy.png)|Stratégie d’activité|Grâce aux stratégies d’activité, vous pouvez appliquer une large gamme de processus automatisés en exploitant les API du fournisseur d’application. Ces stratégies vous permettent de surveiller des activités spécifiques effectuées par différents utilisateurs ou de suivre les taux anormalement élevés d’un certain type d’activité.|  
|![Icône de stratégie de détection d’anomalie](./media/anomaly_detection_policy.png)|Stratégie de détection d’anomalie|Grâce aux stratégies de détection d’anomalie, vous pouvez rechercher les activités inhabituelles sur votre cloud en fonction des facteurs de risque que vous définissez ici, afin d’être averti en cas d’événement anormal par rapport aux activités de référence ou habituelles de votre organisation ou de l’utilisateur.|  
|![Icône de stratégie Cloud Discovery](./media/discovery_policy.png)|Stratégie de découverte d’application|Grâce aux stratégies de découverte d’application, vous pouvez définir des alertes qui vous informent quand de nouvelles applications sont détectées au sein de votre organisation.|  
|![Icône de stratégie de détection d’anomalie](./media/anomaly_detection_policy.png)|Stratégie de détection des anomalies de Cloud Discovery|Les stratégies de détection des anomalies de Cloud Discovery examinent les journaux que vous utilisez pour découvrir les applications cloud et recherchent les occurrences inhabituelles. À titre d’exemple, citons un utilisateur qui n’a jamais utilisé Dropbox et qui y charge soudainement 600 Go de données ou une application qui fait l’objet de transactions dans des proportions inhabituelles.|  
|![Icône de champ de stratégie](./media/field_policy.png)|Stratégie de champ|Les stratégies de champ vous permettent d’analyser vos applications cloud afin de rechercher les champs de votre environnement cloud susceptibles de contenir des données sensibles comme des billets, des messages de conversation, des descriptions et des champs de texte long.|  
|![Icône de stratégie de fichier](./media/file_policy.png)|Stratégie de fichier|Grâce aux stratégies de fichier, vous pouvez déterminer si vos applications cloud comportent certains fichiers ou types de fichiers (partagés, partagés avec des domaines externes) ou certaines données (informations propriétaires, PII, informations de carte de crédit, etc.) et appliquer des actions de gouvernance aux fichiers (les actions de gouvernance sont spécifiques aux applications cloud).|  
  
## <a name="identifying-risk"></a>Identification des risques  
Cloud App Security vous permet d’atténuer différents risques dans le cloud. Vous pouvez configurer n’importe quelles stratégie et alerte à associer à un des risques suivants :  
  
-   **Contrôle d’accès :** Qui accède à quoi à partir d’où ?  
  
     Surveillez le comportement et détectez les activités anormales en continu, notamment les attaques externes et internes à haut risque, et appliquez une stratégie d’alerte, de blocage ou de vérification d’identité pour toute application ou action spécifique dans une application. Cette approche permet de mettre en place des stratégies de contrôle d’accès locales et mobiles basées sur l’utilisateur, l’appareil et la zone géographique, avec un blocage grossier et des procédures d’affichage, de modification et de blocage précises. Détectez les événements de connexion suspects, notamment les échecs d’authentification multifacteur, les échecs de connexion de compte désactivé et les événements d’emprunt d’identité.  
  
-   **Conformité :** Vos contraintes de conformité sont-elles enfreintes ?  
  
     Classez et identifiez les données sensibles ou réglementées, notamment les autorisations de partage pour chaque fichier, stockées dans des services de synchronisation de fichier pour assurer la conformité aux réglementations telles que PCI, SOX et HIPAA  
  
-   **Contrôle de configuration : ** Votre configuration fait-elle l’objet de modifications non autorisées ?  
  
     Surveillez les modifications de configuration, notamment la manipulation de la configuration à distance.  
  
-   **Cloud Discovery : ** Des applications nouvelles et non approuvées sont-elles utilisées dans votre organisation ? Des applications Shadow IT que vous ignorez sont-elles utilisées ?  
  
     Évaluez le risque global pour chaque application cloud en fonction de la réglementation, ainsi que des bonnes pratiques et certifications de l’industrie.  
    Grâce à cette approche, vous pouvez surveiller le nombre d’utilisateurs, les activités, le volume de trafic et les heures d’utilisation classiques pour  
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
  
Pour créer une stratégie à partir d’un **modèle de stratégie**, procédez comme suit :  
  
1.  Dans la console, cliquez sur **Contrôle**, puis sur **Modèles**.  
  
     ![](./media/create-policy-from-template.png)  
  
2.  Cliquez sur le signe **+** tout à droite de la ligne du modèle à utiliser. Une page de création de stratégie s’ouvre, contenant la configuration prédéfinie du modèle.  
  
3.  Modifiez le modèle en fonction des besoins de votre stratégie personnalisée. Vous pouvez modifier librement chaque propriété et champ de cette nouvelle stratégie basée sur un modèle.  
> [!NOTE] 
>Quand vous utilisez des filtres de stratégie, le filtre **Contains (Contient)** recherche uniquement des mots entiers, séparés par des virgules, points, espaces ou traits de soulignement. Par exemple, si vous recherchez **malware** ou **virus**, il trouve virus_malware_file.exe, mais pas malwarevirusfile.exe. Si vous recherchez **malware.exe**, vous obtenez tous les fichiers exe dont le nom contient malware ou exe, tandis que si vous recherchez **"malware.exe"** (avec les guillemets), vous n’obtenez que les fichiers dont le nom contient exactement « malware.exe ». 
     **Equals (Est égal à)** recherche uniquement la chaîne complète ; par exemple, si vous recherchez **malware.exe**, il trouve malware.exe, mais pas malware.exe.txt.  
4.  Une fois la stratégie basée sur un modèle créée, un lien vers celle-ci s’affiche dans la colonne **Stratégies liées** de la table des modèles de stratégie, en regard du modèle à partir duquel la stratégie a été créée.  
     Vous pouvez, à partir de chaque modèle, créer autant de stratégies que vous le souhaitez, qui seront toutes liées au modèle d’origine ; ainsi, vous pouvez effectuer le suivi de toutes les stratégies créées à l’aide du même modèle.  
  
Vous pouvez également **créer une stratégie au cours d’un examen**. Si vous examinez le **Journal d’activité**, les **Fichiers** ou les **Comptes** à la recherche d’un élément spécifique, à tout moment, vous pouvez créer une stratégie basée sur les résultats de votre examen.  
  
Par exemple, si vous examinez le **Journal d’activité** et que vous constatez qu’un de vos comptes d’administrateur fait l’objet d’une connexion à partir d’un emplacement géographique inattendu, vous pouvez filtrer les résultats du **Journal d’activité** pour afficher toutes activités de connexion par cet administrateur, puis créer un rapport qui vous avertit la prochaine fois qu’une activité est détectée de la part de cet utilisateur.  
  
Pour créer une stratégie basée sur les résultats de l’examen, procédez comme suit :  
  
1.  Dans la console, cliquez sur **Examiner**, puis sur **Journal d’activité**, **Fichiers** ou **Comptes**.  
  
2.  Utilisez les filtres en haut de la page pour limiter les résultats de la recherche à la zone suspecte ; par exemple, dans la page Journal d’activité, cliquez sur **Utilisateur** et sélectionnez l’administrateur dont le compte enregistre une activité inhabituelle. Ensuite, sous **Activité**, sélectionnez **Copy file**, **Copy folder** (Copier fichier, copier dossier).  
  
     ![](./media/create-file-from-investigation.png)  
  
3.  Dans l’angle supérieur droit de la console, cliquez sur **Nouvelle stratégie à partir de la recherche**![](./media/new-policy-from-search-button.png)  
  
4.  Une page de création de stratégie s’ouvre, contenant les filtres que vous avez utilisés dans votre examen.  
  
5.  Modifiez le modèle en fonction des besoins de votre stratégie personnalisée. Vous pouvez modifier librement chaque propriété et champ de cette nouvelle stratégie basée sur un examen.  
   
> [!NOTE] 
> Quand vous utilisez des filtres de stratégie, le filtre **Contains (Contient)** recherche uniquement des mots entiers, séparés par des virgules, points, espaces ou traits de soulignement. Par exemple, si vous recherchez **malware** ou **virus**, il trouve virus_malware_file.exe, mais pas malwarevirusfile.exe.  
     **Equals (Est égal à)** recherche uniquement la chaîne complète ; par exemple, si vous recherchez **malware.exe**, il trouve malware.exe, mais pas malware.exe.txt.  
  
 
 
![créer une stratégie d’activité basée sur un examen](./media/create-activity-policy-from-investigation.png)
 
 
  
> [!NOTE]  
>  Pour plus d’informations sur la définition des champs d’une stratégie, reportez-vous à la documentation de stratégie correspondante :  
>   
>  [Stratégies d’activité utilisateur](user-activity-policies.md)  
>   
>  [Stratégies de protection des données](data-protection-policies.md)  
>   
>  [Stratégies Cloud Discovery](cloud-discovery-policies.md)  
  
### <a name="policy-conflicts"></a>Conflits de stratégies
Après avoir créé plusieurs stratégies, il peut arriver que les stratégies se chevauchent. Dans ce cas, Cloud App Security traite les stratégies comme suit :
* Si deux stratégies contiennent des actions qui sont contenues dans l’autre (par exemple, **Remove external shares** (Supprimer des partages externes) figure dans **Rendre privé**), Cloud App Security peut résoudre le conflit et l’action la plus forte est appliquée.
* Si les actions sont complètement indépendantes (par exemple, **Notifier le propriétaire** et **Rendre privé**), les deux actions ont lieu.
* Si les actions sont en conflit, (par exemple **Change owner to user A** [Remplacer le propriétaire par l’utilisateur A] et **Change owner to user B** [Remplacer le propriétaire par l’utilisateur B]), différents résultats peuvent provenir de chaque correspondance. Il est important de modifier vos stratégies pour éviter les conflits, car elles peuvent entraîner des modifications indésirables dans le lecteur qui seront difficiles à détecter. 


## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  


<!--HONumber=Oct16_HO5-->


