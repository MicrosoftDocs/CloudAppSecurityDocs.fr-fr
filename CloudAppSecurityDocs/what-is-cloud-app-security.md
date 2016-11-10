---
title: "Qu’est-ce que Cloud App Security ? | Documentation Microsoft"
description: Cette rubrique fournit des informations sur Cloud App Security et son fonctionnement.
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: d46756b1-7dd8-4190-9799-3a97688f1266
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: d2ece0e3a47dc0febbb1314c496045abdc5c8d61


---
# <a name="what-is-cloud-app-security"></a>Qu’est-ce que Cloud App Security ?
 
> [!NOTE] 
> Pour plus d’informations sur la gestion de la sécurité avancée - Fonctionnalités Cloud App Security dans Office 365, voir [Prise en main de la gestion avancée de sécurité](https://support.office.com/article/Get-started-with-Advanced-Management-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a). 
 
Alors que le passage au cloud est synonyme d’une plus grande flexibilité pour les employés et d’une réduction des coûts informatiques, il apporte également une nouvelle complexité et de nouveaux défis au maintien de la sécurité de votre organisation. Pour tirer le meilleur parti des applications cloud, les équipes informatiques doivent trouver le juste équilibre entre l’activation de l’accès et la conservation du contrôle dans l’intérêt de la protection des données critiques.  
  
Cloud App Security est un composant essentiel de la pile Microsoft Cloud Security. Il s’agit d’une solution complète qui permet aux organisations de tirer pleinement parti de la promesse des applications cloud tout en conservant le contrôle avec une visibilité de l’activité améliorée. Elle renforce également la protection des données critiques entre les applications cloud. Avec des outils permettant de découvrir le Shadow IT, d’évaluer les risques, d’appliquer des stratégies, d’examiner les activités et de stopper les menaces, les organisations peuvent passer tranquillement au cloud tout en conservant le contrôle de leurs données critiques.  
  
## <a name="the-cloud-app-security-framework"></a>Infrastructure de Cloud App Security  

|       |   |   |
|-------|---|:---|
|![Découvrir](./media/discovery-icon.png)|Découvrir|Découvrez l’informatique fantôme avec Cloud App Security. Gagnez en visibilité en découvrant les applications, les activités, les utilisateurs, les données et les fichiers de votre environnement cloud, ainsi que les applications tierces connectées à votre cloud.|
|![Étudier](./media/investigate-icon.png)|Étudier|Décortiquez vos applications cloud à l’aide d’outils d’investigation cloud pour étudier en profondeur les applications risquées, des utilisateurs spécifiques et des fichiers de votre réseau ainsi que trouver des modèles dans les données collectées à partir de votre cloud et générer des rapports pour surveiller votre cloud.|
|![Control](./media/protect-icon.png)|Control|Atténuez les risques en définissant des stratégies et des alertes pour obtenir un contrôle maximal sur le trafic cloud réseau. Utilisez Cloud App Security pour migrer vos utilisateurs vers des applications cloud alternatives approuvées et sécurisées.|
|![Protéger](./media/protect-icon.png)|Protéger|Utilisez Cloud App Security pour approuver/ne pas approuver des applications, appliquer une protection contre la perte de données (DLP, Data Loss Prevention), contrôler les autorisations et le partage, ainsi que générer des alertes et rapports personnalisés.|


## <a name="architecture"></a>Architecture  

Cloud App Security permet d’intégrer une visibilité à votre cloud comme suit :  
  
-   Visibilité en utilisant Cloud Discovery pour mapper et identifier votre environnement cloud et les applications cloud en cours d’utilisation.  
-   Possibilité d’approuver et de ne pas approuver des applications dans votre cloud.  
-   Visibilité et gouvernance des applications auxquelles vous vous connectez à l’aide de nos connecteurs d’applications faciles à déployer qui exploitent les API du fournisseur.  
-   Contrôle continu en vous permettant de définir et d’ajuster en permanence des stratégies.  
  
![](./media/architecture.png)  
  
> [!NOTE]  
>  Quand Cloud App Security exécute une inspection du contenu, la confidentialité des données est respectée. Vos données ne sont pas stockées dans la base de données Cloud App Security, mais seulement les métadonnées des enregistrements de fichiers et les violations qui ont été identifiées. Pour plus d’informations sur la rétention de données, voir notre [politique de confidentialité](http://go.microsoft.com/fwlink/?LinkId=512132) et le [Centre de gestion de la confidentialité](https://www.microsoft.com/TrustCenter/Privacy/You-are-in-control-of-your-data).
Cloud App Security conserve les données comme suit :
>- Journal d’activité : 180 jours
>- Données de découverte : 90 jours
>- Alertes : illimité 

Une fois que les données sont collectées auprès de ces sources, Cloud App Security exécute une analyse complexe sur elles, en vous avertissant immédiatement des activités anormales et en vous donnant une visibilité approfondie. Vous pouvez ensuite configurer une stratégie dans Cloud App Security et l’utiliser pour protéger tout ce qui se trouve dans votre environnement cloud.  
  
###  <a name="how-cloud-discovery-works"></a>Comment fonctionne Cloud Discovery  

Cloud Discovery utilise vos journaux de trafic pour découvrir et analyser dynamiquement les applications cloud utilisées dans votre organisation.  
  
Vous pouvez créer un rapport d’instantané de l’utilisation du cloud par votre organisation en chargeant manuellement les fichiers journaux à partir de vos pare-feu ou proxys pour l’analyse, ou vous pouvez configurer des rapports continus à l’aide des collecteurs de journaux de Cloud App Security pour transférer les journaux régulièrement.  

Pour plus d’informations sur Cloud Discovery, voir [Configurer Cloud Discovery](set-up-cloud-discovery.md).
  
### <a name="how-sanctioning-and-unsanctioning-an-app-works"></a>Comment fonctionne l’approbation et la non-approbation d’une application  

Cloud App Security vous permet d’approuver/de ne pas approuver des applications dans votre organisation en utilisant notre **catalogue d’applications cloud**.  
  
L’équipe d’analystes Microsoft dispose d’un catalogue fourni et en constante évolution de plus de 13 000 applications cloud, classées et évaluées selon les normes du secteur. Le **catalogue d’applications cloud** évalue les risques pour vos applications cloud selon les certifications réglementaires, les normes du secteur et les bonnes pratiques. Vous pouvez alors personnaliser les scores et l’importance des différents paramètres selon les besoins de votre organisation. Avec ces scores, Cloud App Security vous indique le degré de risque lié à l’application en fonction de plus de 50 facteurs de risque susceptibles d’affecter votre environnement.  
  
### <a name="how-app-connectors-work"></a>Comment fonctionne les connecteurs d’applications  
Les connecteurs d’applications exploitent les API fournies par divers fournisseurs d’applications cloud pour permettre au cloud Cloud App Security de s’intégrer à d’autres applications cloud et d’étendre le contrôle et la protection. Cela permet à Cloud App Security d’extraire directement des informations des applications cloud à des fins d’analyse.  
Pour connecter une application et étendre la protection, l’administrateur de l’application autorise Cloud App Security à accéder à l’application, puis Cloud App Security interroge l’application pour obtenir les journaux d’activité, analyse les données, les comptes et le contenu cloud. Cloud App Security peut alors appliquer des stratégies, détecter les menaces et proposer des actions de gouvernance pour résoudre les problèmes.  
  
Cloud App Security s’appuie sur les API données par le fournisseur de cloud, et chaque application a ses propres infrastructure et limitations d’API. Cloud App Security fonctionne avec les fournisseurs d’applications pour optimiser l’utilisation des API et garantir des performances optimales. Compte tenu des différentes limitations qu’imposent les applications aux API (telles que les limites d’API et les fenêtres d’API de décalage temporel dynamique), les moteurs Cloud App Security tirent parti de la capacité autorisée. Certaines opérations, comme l’analyse de tous les fichiers dans le client, nécessitent une grande quantité d’API et sont donc réparties sur une longue période. Il est normal que certaines stratégies s’exécutent pendant plusieurs heures ou jours.  
  
### <a name="how-policy-control-works"></a>Comment fonctionne le contrôle de stratégie  

Grâce aux stratégies, vous pouvez définir la façon dont vous souhaitez que vos utilisateurs se comportent dans le cloud. Vous pouvez détecter les comportements à risques, les violations ou les activités et les points de données suspects dans votre environnement cloud et, si nécessaire, intégrer des processus de correction pour atténuer les risques de façon efficace. Il existe plusieurs types de stratégies suivant les différents types d’informations que vous voulez collecter sur votre environnement cloud et les types de mesures correctives que vous pouvez souhaiter prendre.  
  
## <a name="see-also"></a>Voir aussi  

[Bien démarrer avec Cloud App Security](getting-started-with-cloud-app-security.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO4-->


