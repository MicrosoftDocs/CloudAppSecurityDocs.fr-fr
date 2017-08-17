---
title: "Créer des stratégies de session pour obtenir une meilleure visibilité des activités de session utilisateur et bloquer les téléchargements | Microsoft Docs"
description: "Cette rubrique décrit la procédure de configuration d’une stratégie de session du proxy Cloud App Security pour améliorer la visibilité des activités de session utilisateur et bloquer les téléchargements."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/8/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 745df28a-654c-4abf-9c90-203841169f90
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 4b12d52703aa6b81a76e54626f06e5732fb3a6bf
ms.sourcegitcommit: 84f358a5dd0ab7f362dd3a2cf9999a6184fba856
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2017
---
# <a name="session-policies"></a>Stratégies de session  
Les stratégies de session vous permettent de surveiller tout ce que fait un utilisateur au cours d’une session et vous donne la possibilité de bloquer les utilisateurs d’activités spécifiques effectuées dans ces sessions, comme le téléchargement de fichiers.

Avant de pouvoir créer une stratégie de session, vous devez [Déployer le proxy](proxy-deployment.md). Les stratégies de session vous permettent de définir des règles pour contrôler et surveiller les sessions de vos utilisateurs.
Par exemple, vous pouvez définir une stratégie pour effectuer les actions suivantes :
- Bloquer les téléchargements de tous les fichiers avec l’étiquette de classification « classifié » d’Azure Information Protection à partir d’appareils non gérés.
- Protéger les téléchargements de tous les fichiers sur les appareils non gérés, avec le chiffrement Azure RMS.
- 

Pour créer une stratégie de session, suivez cette procédure :  
  
1.  Dans la console, cliquez sur **Contrôle**, puis sur **Stratégies**.  
  
2.  Cliquez sur **Créer une stratégie** et sélectionnez la **Stratégie de session**.  
  
3.  Donnez à votre stratégie un nom et une description. Si vous le souhaitez, vous pouvez la baser sur un modèle ; pour plus d’informations sur les modèles de stratégie, consultez [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md).  
  
3. Définissez une **Gravité de la stratégie**. Si Cloud App Security est défini pour vous envoyer des notifications en cas de correspondances de stratégie pour un niveau de gravité de stratégie spécifique, votre sélection détermine si les correspondances de cette stratégie déclenchent une notification.

4.  Dans **Catégorie**, liez la stratégie au type de risque le plus approprié. Ce champ est à titre informatif uniquement et vous permet de rechercher ultérieurement des stratégies et alertes spécifiques, selon le type de risque.  Le risque est peut-être déjà présélectionné en fonction de la catégorie pour laquelle vous avez choisi de créer la stratégie. Par défaut, les stratégies de session sont définies sur **DLP**.  
  
5.  Pour définir les applications découvertes qui déclenchent cette stratégie, **Créer un filtre pour les fichiers sur lesquels cette stratégie s’appliquera**, 

 > [!NOTE] 
 > Quand vous utilisez des filtres de stratégie, le filtre **Contains (Contient)** recherche uniquement des mots entiers, séparés par des virgules, points, espaces ou traits de soulignement. Par exemple, si vous recherchez **malware** ou **virus**, il trouve virus_malware_file.exe, mais pas malwarevirusfile.exe. Si vous recherchez **malware.exe**, vous obtenez tous les fichiers exe dont le nom contient malware ou exe, tandis que si vous recherchez **"malware.exe"** (avec les guillemets), vous n’obtenez que les fichiers dont le nom contient exactement « malware.exe ». **Equals (Est égal à)** recherche uniquement la chaîne complète ; par exemple, si vous recherchez **malware.exe**, il trouve malware.exe, mais pas malware.exe.txt.  

6. Sélectionnez le **type de contrôle de session**.
    - Surveillez toutes les activités : Si vous sélectionnez Surveiller, les activités de session des applications sont surveillées, mais pas bloquées. Vous pouvez surveiller chaque page interne spécifique de l’application cloud qui a été consultée et chaque téléchargement effectué dans chaque application spécifique. Par défaut, les alertes sont automatiquement envoyées au portail Cloud App Security. Cela vous permet également [d’Exporter le journal d’audit entier](#export-the-audit-log) pour les activités de session à partir de l’onglet Proxy.
    - Surveiller toutes les activités et contrôler le téléchargement de fichiers : en sélectionnant Surveiller et contrôler, vous avez accès à toutes les fonctionnalités répertoriées sous **Surveiller toutes les activités** avec la couche supplémentaire de contrôle qui vous permet de bloquer des activités spécifiques, comme le téléchargement de fichiers, en temps réel. Vous pouvez aussi filtrer le contenu du fichier à partir du DLP intégré à Cloud App Security ou d’un DLP externe.
 
7. Sous **Source d’activité**, sélectionnez les applications auxquelles la stratégie doit être appliquée : toutes les applications ou des applications spécifiques.

8. Utilisez les filtres pour sélectionner les utilisateurs, les applications et les appareils pour lesquels vous voulez déclencher une correspondance de stratégie. Pour obtenir la liste complète des filtres, consultez [Filtres de stratégie de session](#session-policy-filters).
  
9. Si vous avez choisi de **Surveiller toutes les activités et contrôler le téléchargement de fichiers**, vous pouvez également définir des [filtres de fichiers](#session-file-filters)

10. Si vous avez choisi de **Surveiller toutes les activités et contrôler le téléchargement de fichiers**, vous pouvez également définir des options **d’Inspection du contenu**. La protection contre la perte de données (DLP) intégrée vous permet de filtrer les fichiers par leur contenu. Pour analyser le contenu des fichiers, sélectionnez ensuite DLP intégré. Une fois que l’inspection du contenu est activée, vous pouvez choisir d’utiliser des expressions prédéfinies ou de rechercher d’autres expressions personnalisées, sous forme de sous-chaîne ou d’expression régulière de votre choix.
De plus, vous pouvez spécifier une expression régulière pour exclure un fichier des résultats. Cette possibilité s’avère très utile si vous avez des mots clés de classification interne standard à exclure de la stratégie.
Vous pouvez décider de définir le nombre minimal de violations de contenu à atteindre avant que le fichier ne soit considéré comme une violation. Par exemple, vous pouvez choisir 10 si vous souhaitez être alerté pour les fichiers comportant au moins 10 numéros de carte de crédit détectés dans leur contenu.
Quand du contenu correspond à l’expression sélectionnée, le texte de la violation est remplacé par des caractères « X ». Par défaut, les violations sont entièrement masquées. Seul leur contexte, 40 caractères avant et après la violation, est affiché. Les chiffres dans le contexte de l’expression sont remplacés par des caractères « # » et ne sont jamais stockés dans Cloud App Security. Vous pouvez sélectionner l’option permettant de Montrer les 4 derniers caractères d’une violation pour annuler le masquage des 4 derniers caractères de la violation elle-même.

10. Si vous avez choisi de **Surveiller toutes les activités et contrôler le téléchargement de fichiers**, vous pouvez également définir des **Actions** à effectuer quand la stratégie trouve une correspondance :
    - Autoriser : Si vous sélectionnez Autoriser, les utilisateurs sont autorisés à télécharger les fichiers. 
    - Bloquer : Si vous sélectionnez **Bloquer**, quand les exigences de la stratégie sont remplies, l’utilisateur ne peut pas télécharger les fichiers. L’utilisateur reçoit un message lui indiquant qu’il n’a pas l’autorisation de télécharger les fichiers.
    - Protéger : Si vous sélectionnez **Protéger**, l’utilisateur peut télécharger les fichiers, mais ils sont chiffrés avec Azure RMS. Vous pouvez également définir une action par défaut à effectuer si le chiffrement échoue (bloquer ou autoriser le téléchargement).
 >[!WARNING]
 >Il est vivement recommandé de créer d’abord la stratégie à l’aide de l’action **Autoriser** et de vérifier les résultats. Une fois seulement que vous avez déterminé que la stratégie ne bloque pas accidentellement des personnes, vous pouvez la définir sur **Bloquer** l’accès.
 
 9. Définissez les alertes que vous voulez recevoir quand la stratégie trouve une correspondance. Vous pouvez définir une limite pour ne pas recevoir trop d’alertes et choisir de recevoir les alertes par e-mail ou SMS, ou les deux.

10. Pour afficher les correspondances de stratégie de session, cliquez sur **Contrôle**, puis sur **Stratégies**. Filtrez les résultats pour afficher uniquement les stratégies de session à l’aide du filtre **Type** en haut. Pour plus d’informations sur les correspondances pour chaque stratégie, cliquez sur une stratégie. Cliquez sur l’onglet **Historique** pour consulter un historique remontant jusqu’à 6 mois de correspondances de stratégie.     
  
## <a name="session-policy-reference"></a>Informations de référence sur les stratégies de session  

Cette section fournit des informations de référence sur les filtres de stratégie de session. 

### Filtres de session <a name="session-policy-filters"></a>

- Balise de l’appareil : La balise de l’appareil vous permet de filtrer les appareils gérés en sélectionnant **Conforme**, **Joint à un domaine** et **Certificat client valide**.
- Type d’appareil : Aucune valeur, PC, Mobile, Tablette, Autres
-   Adresse IP : Adresse IP brute, catégorie IP ou balise IP à partir de laquelle l’activité a été réalisée.  
    - Adresse IP brute : Vous permet de rechercher des activités qui ont été réalisées sur ou par des adresses IP brutes qui sont égales à/ne sont pas égales à ou commencent par/ne commencent pas par une séquence particulière, ou des adresses IP brutes qui sont définies/ne sont pas définies. 
    - Catégorie IP : Catégorie de l’adresse IP à partir de laquelle l’activité a été réalisée, par exemple, toutes les activités de la plage d’adresses IP administratives. Les catégories doivent être configurées de façon à inclure les adresses IP appropriées, à l’exception de la catégorie « Risqué », qui est préconfigurée et inclut deux balises IP : Proxy anonyme et Tor. Pour découvrir comment configurer les catégories IP, consultez [Organiser les données selon vos besoins](ip-tags.md).  
    - Balise IP : Balise de l’adresse IP à partir de laquelle l’activité a été exécutée, par exemple toutes les activités des adresses IP de proxy anonyme. Cloud App Security crée un ensemble de balises IP prédéfinies qui ne sont pas configurables. Vous pouvez aussi configurer vos propres balises IP. Pour plus d’informations sur la configuration de vos propres balises IP, consultez [Organiser les données selon vos besoins](ip-tags.md).
   Les balises IP prédéfinies sont les suivantes :
    - Applications Microsoft (14 applications)
    - Proxy anonyme
    - Botnet (vous voyez que l’activité a été effectuée par un botnet avec un lien qui vous permet d’en savoir plus sur le botnet spécifique)
    - Adresse IP d’analyse du darknet
    - Serveur de commande et contrôle de programmes malveillants
    - Analyseur de connectivité à distance
    - Fournisseurs par satellite
    - Proxy intelligent et proxy d’accès (délibérément omis)
    - Nœuds de sortie Tor
    - Zscaler

-   Emplacement : Pays à partir duquel la demande d’accès a été effectuée.    

- ISP inscrit : 

-   Utilisateur : Utilisateur qui a exécuté l’activité, qui peut être filtré en domaine, groupe, nom ou organisation. Pour filtrer les activités sans utilisateur spécifique, vous pouvez utiliser l’opérateur « n’est pas défini ».  
    -   Organisation utilisateur : Unité d’organisation de l’utilisateur qui a effectué l’activité, par exemple toutes les activités effectuées par les utilisateurs EMEA_marketing.  
    -   Groupe d’utilisateurs : Groupes d’utilisateurs spécifiques que vous pouvez importer à partir d’applications connectées, par exemple, les administrateurs Office 365.  
    -   Nom d’utilisateur : Recherchez un nom d’utilisateur spécifique. Pour afficher la liste des utilisateurs membres d’un groupe d’utilisateurs spécifique, dans le **tiroir Activité**, cliquez sur le nom du groupe d’utilisateurs. Vous accédez alors à la page Comptes qui liste tous les utilisateurs figurant dans le groupe. À partir de cette page, vous pouvez explorer plus en détail les comptes d’utilisateurs spécifiques dans le groupe.
       -  Vous pouvez affiner les filtres **Groupe d’utilisateurs** et **Nom d’utilisateur** en choisissant le filtre **En tant que**, puis en sélectionnant le rôle de l’utilisateur parmi les rôles suivants :
            - Objet d’activité uniquement : cela signifie que l’utilisateur ou le groupe d’utilisateurs sélectionné n’a pas effectué l’activité en question, mais qu’il était l’objet de l’activité
            - Acteur uniquement : cela signifie que l’utilisateur ou le groupe d’utilisateurs a effectué l’activité
            - N’importe quel rôle : cela signifie que l’utilisateur ou le groupe d’utilisateurs a participé à l’activité, soit en effectuant l’activité, soit en étant l’objet de l’activité

-   Agent utilisateur : Agent utilisateur à partir duquel l’activité a été effectuée.  
  
-   Étiquette agent utilisateur : Balise d’agent utilisateur intégrée, par exemple toutes les activités d’un navigateur obsolète ou d’anciens systèmes d’exploitation.  

### Filtres de fichier de session <a name="session-file-filters"></a>

-   Étiquette de classification : Rechercher des fichiers avec des balises spécifiques définies. Il peut s’agir des balises suivantes :
    - Balises Azure Information Protection. Une intégration à Azure Information Protection est alors nécessaire.
    - Balises Cloud App Security. Fournit désormais un meilleur insight sur les fichiers qu’il analyse. Pour chaque fichier analysé par Cloud App Security DLP, vous pouvez maintenant savoir si les fichiers n’ont pas pu être inspectés parce qu’ils ont été chiffrés ou corrompus. Par exemple, vous pouvez configurer des stratégies pour vous alerter et mettre en quarantaine les fichiers protégés par mot de passe qui sont partagés en externe, comme suit : 
        - Chiffré par Azure RMS : Les fichiers dont le contenu n’a pas été inspecté parce qu’ils ont un chiffrement Azure RMS défini.
        - Chiffré par mot de passe : Les fichiers dont le contenu n’a pas été inspecté parce qu’ils sont protégés par un mot de passe de l’utilisateur.
        - Fichier corrompu : Les fichiers dont le contenu n’a pas été inspecté parce qu’il n’a pas pu être lu.

-   Type de fichier : Cloud App Security accepte le type MIME reçu du service et analyse le fichier pour déterminer le type de fichier réel. Notez que cette analyse concerne les fichiers qui sont appropriés pour l’analyse de données (documents, images, présentations, feuilles de calcul, fichiers texte et compressés/d’archive). Le filtre fonctionne selon le type de fichier/dossier, par exemple Tous les dossiers qui... ou Tous les fichiers de feuille de calcul qui...
-   Extension : Concentrez-vous sur des extensions de fichier spécifiques, par exemple tous les fichiers exécutables (exe).  
  
-   Nom de fichier : Nom de fichier ou sous-chaîne du nom comme défini dans l’application cloud, par exemple, Tous les fichiers avec un mot de passe dans leur nom.   
  
-   Taille du fichier : Taille de fichier en Mo, supérieure à une taille donnée, inférieure à une taille donnée ou dans une plage de tailles.    


>[!NOTE]
> Si vous voulez effacer les filtres, vous pouvez le faire à tout moment en cliquant sur l’icône d’effacement des filtres ![icône d’effacement des filtres](./media/clear-filters.png).

  
## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  