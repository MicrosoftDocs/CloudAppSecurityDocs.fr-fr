---
title: "Activités | Documentation Microsoft"
description: "Cette rubrique fournit une liste des activités, filtres et paramètres de correspondance qui peuvent être appliqués aux stratégies d’activité."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: f3af2d25-9286-4e9b-b2ad-35653bec72ff
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: 401801da8a4439b3dc0cf5c2f150c72e169a6d16


---

# <a name="activities"></a>Activités
Vous trouverez ci-dessous une liste des filtres d’activité qui peuvent être appliqués. La plupart des filtres prennent en charge plusieurs valeurs, ainsi que NOT, afin de vous fournir un outil très puissant pour créer des stratégies.  
  
-   Activité : Recherchez uniquement des activités spécifiques, par exemple, tous les chargements de fichiers, les connexions à partir d’un nouvel appareil et les échecs de connexion.  
  
-   ID activité : Recherchez uniquement des activités spécifiques par leur ID. Ce filtre s’avère très utile quand vous connectez MCAS à votre SIEM (à l’aide de l’agent SIEM) et que vous voulez examiner davantage les alertes au sein du portail MCAS.  
  
-   Activité administrative : Recherchez uniquement les activités administratives.  
  
-   Activité représentée : Recherchez uniquement les activités qui ont été effectuées au nom d’un autre utilisateur.  
  
-   Application : Recherchez uniquement des activités au sein d’applications spécifiques.  
  
-   Date : Date à laquelle l’activité s’est produite. Le filtre prend en charge des dates antérieures/ultérieures ainsi qu’une plage de dates.  
  
-   Utilisateur : Utilisateur qui a effectué l’activité. Pour filtrer les activités sans utilisateur spécifique, vous pouvez utiliser l’opérateur « n’est pas défini ».  
  
     ![activité, ref1](./media/activity-ref1.png "activity ref1")  
  
-   Adresse IP : Adresse IP à partir de laquelle l’activité a été effectuée.  
  
-   Catégorie IP : Catégorie de l’adresse IP à partir de laquelle l’activité a été effectuée, par exemple, toutes les activités de la plage d’adresses IP administratives. Pour plus d’informations sur les catégories d’adresses IP, consultez [Organiser les données selon vos besoins](general-setup.md#IPtagsandRanges).  
  
-   Balise IP : Balise de l’adresse IP à partir de laquelle l’activité a été exécutée, par exemple toutes les activités des adresses IP de proxy anonyme. Pour plus d’informations sur les balises IP, consultez [Organiser les données selon vos besoins](general-setup.md#IPtagsandRanges).  
  
-   Emplacement : Pays à partir duquel l’activité a été effectuée.  
  
-   ISP enregistré : Fournisseur de services Internet à partir duquel l’activité a été effectuée.  
  
     ![stratégie d’activité ref2](./media/activity-policy-ref2.png "activity policy ref2")  
  
-   Type d’appareil : Recherchez uniquement les activités qui ont été effectuées à l’aide d’un type d’appareil spécifique, par exemple toutes les activités des appareils mobiles.  
  
-   Agent utilisateur : Agent utilisateur à partir duquel l’activité a été effectuée.  
  
-   Étiquette agent utilisateur : Balise d’agent utilisateur intégrée, par exemple toutes les activités à partir d’un navigateur obsolète ou d’anciens systèmes d’exploitation.  
  
-   Organisation utilisateur : Unité d’organisation de l’utilisateur qui a effectué l’activité, par exemple toutes les activités effectuées par les utilisateurs EMEA_marketing.  
  
- Objet cible : Vous permet de sélectionner un fichier spécifique. 

-   Groupe d’utilisateurs : Groupes d’utilisateurs spécifiques automatiquement importés par MCAS à partir de l’application cloud, par exemple, toutes les activités effectuées par les administrateurs Office 365.  
  
-   Description : Mot clé spécifique dans la description de l’activité, par exemple, toutes les activités qui contiennent la chaîne **utilisateur** dans leur description.  
  
-   Stratégie correspondante : Recherchez les activités qui correspondent à une stratégie spécifique qui a été définie dans le portail.  
  
     ![Stratégie d’activité ref3](./media/activity-policy-ref3.png "Activity policy ref3")  
  
## <a name="activity-match-parameters"></a>Paramètres de correspondance de l’activité  
Spécifiez le nombre requis de répétitions de l’activité pour correspondre à la stratégie, par exemple, en définissant une stratégie qui émet une alerte quand un utilisateur effectue sans succès 10 tentatives de connexion dans un délai d’exécution de 2 minutes.  
Le paramètre par défaut, **Paramètres de correspondance de l’activité**, déclenche une correspondance pour chaque activité unique qui satisfait à tous les filtres d’activité.   
À l’aide de l’option **Activité répétée**, vous pouvez définir le nombre d’activités répétées, la durée du délai d’exécution dans lequel les activités sont comptabilisées et même spécifier que toutes les activités doivent être effectuées par le même utilisateur et dans la même application cloud.  
  
### <a name="actions"></a>Actions  
Notifications  
  
-   Alertes : Les alertes peuvent se déclencher dans le système et se propager par le biais de messages électroniques et texte, selon leur niveau de gravité.  
  
-   Notification par e-mail à l’utilisateur : Les e-mails sont personnalisables et envoyés à tous les propriétaires de fichiers en situation de violation.  
  
-   Mettre en copie le responsable : Selon l’intégration de l’annuaire des utilisateurs, des notifications par e-mail peuvent également être envoyées au responsable de la personne qui viole une stratégie.  
  
-   Notifier d’autres utilisateurs : Liste spécifique d’adresses e-mail qui reçoivent ces notifications.  
  
Actions de gouvernance dans les applications  
  
-   Des actions précises peuvent être appliquées par application. Ces actions spécifiques varient selon la terminologie de l’application.  
  
-   Suspendre l’utilisateur : Excluez temporairement l’utilisateur de l’application.  
  
-   Révoquer le mot de passe : Révoquez le mot de passe de l’utilisateur et obligez-le à définir un nouveau mot de passe lors de sa prochaine connexion.  
  
     ![stratégie d’activité ref6](./media/activity-policy-ref6.png "activity policy ref6")  
  
## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO4-->


