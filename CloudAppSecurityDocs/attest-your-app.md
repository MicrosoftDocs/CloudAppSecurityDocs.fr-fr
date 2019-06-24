---
title: Attester de vos applications - Cloud App Security | Microsoft Docs
description: Cet article fournit des instructions pour attester de vos applications dans Cloud App Security.
keywords: ''
author: ShlomoSagir-MS
ms.author: ShlomoSagir-MS
manager: ShlomoSagir-MS
ms.date: 6/20/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 3536c0a5-fa56-4931-9534-cc7cc4b4dfb0
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 6beaeba5c522aacb8a6d0c9612df318b267d2612
ms.sourcegitcommit: 7a03921f9e337f73ddf812105b72ea260582a3d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2019
ms.locfileid: "67333565"
---
# <a name="attest-your-app"></a>Attester votre application

Microsoft Cloud App Security vous permet d’attester de votre application, afin que vous vous assurer que la conformité et les détails de sécurité que nous permet d’évaluer votre application dans notre catalogue d’applications Cloud sont à jour.

Si votre application est déjà répertoriée dans le catalogue d’applications Cloud, ou qu’il est nouveau, envoyez un questionnaire automatique d’attestation. Pour plus d’informations sur le processus d’attestation automatique et pour obtenir le questionnaire, contactez casfeedback@microsoft.com.

Suivez les attributs de service décrites ci-dessous pour mener à bien la soumission du questionnaire :

| Champ | Catégorie d’informations | type | Valeurs acceptées | Description |
|------|-------|------|---------|----------|
| Nom de l’application | Général | Chaîne | Texte libre | Le nom de votre application tel qu’il doit apparaître dans le catalogue d’applications Cloud. |
| Description | Général | Chaîne | Texte libre | Brève explication de ce à quoi votre application permet aux utilisateurs d’effectuer ou atteindre. |
| Category| Général | Chaîne | Liste Fermer - fournie dans le questionnaire | Classification de l’application selon le champ auquel elle est associée. |
| Siège social | Général | Code du pays | Liste Fermer - fournie dans le questionnaire | Le pays du siège social du fournisseur.|
| Centre de données| Général | Tableau de code de pays * | Liste Fermer - fournie dans le questionnaire (sélection multiple) | Le pays dans lequel se trouve votre centre de données (peut être pas plusieurs emplacements) |
| Société d’hébergement | Général | Chaîne | Texte libre | Le nom de la société qui fournit l’hébergement de serveur pour l’application. |
| Fondé | Général | Entier | AAAA (au plus tard 2019) | L’année dans laquelle le fournisseur a été créé. |
| Maintenant | Général | Chaîne | Private, Public | Indique si le fournisseur est une entreprise publique ou privée détenue |
| Domaine d’application | Général | Tableau d’URL * | Texte libre | La liste des domaines qui servent à interagir avec le service (par exemple, « teams.microsoft.com » pour Microsoft Teams) |
| Termes du contrat de service | Général | Adresse URL | Texte libre | Cette application propose un ensemble de réglementations que les utilisateurs doivent accepter à suivre pour utiliser l’application ? |
| politique de confidentialité | Général | Adresse URL | Texte libre | Un lien vers un document relatif à la façon dont ce fournisseur gère les informations client, client ou employé collectées dans le cadre de l’application. |
| URL de connexion | Général | Tableau d’URL * | Texte libre | L’URL via laquelle les utilisateurs se connectent à l’application. |
| Fabricant | Général | Chaîne | Texte libre | Le nom du fournisseur qui fournit cette application. |
| Types de données | Général | Chaîne | Liste Fermer - fournie dans le questionnaire | Les types de données peuvent être téléchargés par l’utilisateur à l’application ?|
| Page d’accueil | Général | Adresse URL | Texte libre | URL de page d’accueil du fournisseur. |
| Plan de récupération d’urgence | Général | Booléen | True, False | Cette application dispose d’un plan de récupération d’urgence qui inclut une stratégie de sauvegarde et restauration ? |
| Dernière violation | Sécurité | Date | MMM-JJ-AAAA | Incident le plus récent dans lequel les données sensibles, protégées ou confidentielles appartienne à l’application a été affichées, de vol ou utilisées par un individu non autorisé à le faire. |
| Méthode de chiffrement des données au repos | Sécurité | Chaîne | Liste Fermer - fournie dans le questionnaire | Le type de chiffrement des données au repos effectué sur l’application. |
| Authentification multifacteur | Sécurité | Booléen | True, False | Cette application prend-elle en charge les solutions d’authentification multifacteur ? |
| Restriction d’adresse IP | Sécurité | Booléen | True, False | Cette application prend-elle en charge la restriction des adresses IP spécifiques par l’application ? |
| Piste d’audit utilisateur | Sécurité | Booléen | True, False | Cette application prend-elle en charge la disponibilité de la piste d’audit par compte d’utilisateur ? |
| Suivi d’audit administratif | Sécurité | Booléen | True, False | Cette application prend-elle en charge la disponibilité d’une piste d’audit d’administrateur dans l’application ? |
| Piste d’audit de données | Sécurité | Booléen | True, False | Cette application prend-elle en charge la disponibilité d’une piste d’audit de données dans l’application ? |
| Utilisateur peut charger des données | Sécurité | Booléen | True, False | Est cette application en charge les données utilisateur a chargé ? |
| Classification des données | Sécurité | Booléen | True, False | Cette application active-t-elle l’option de classification des données chargées à l’application ? |
| N’oubliez pas de mot de passe | Sécurité | Booléen | True, False | Cette application active-t-elle l’option Mémoriser et l’enregistrement des mots de passe utilisateur dans l’application ? |
| Prise en charge des rôles d’utilisateur | Sécurité | Booléen | True, False | Cette application prend-elle en charge la distribution des utilisateurs par rôles et niveaux d’autorisation ? |
| Partage de fichiers | Sécurité | Booléen | True, False | Cette application comprend-elle des fonctionnalités qui permettent le partage de fichiers entre les utilisateurs ? |
| Nom de certificat valide | Sécurité | Booléen | True, False | Le serveur fournit-il un certificat SSL correspondant au nom de domaine ? |
| Certificat approuvé | Sécurité | Booléen | True, False | Le serveur fournit-il un certificat SSL approuvé (chaîne de signature pas expiré, vérifiée et approuvée, etc.) ? |
| Protocole de chiffrement | Sécurité | Chaîne | Liste Fermer - fournie dans le questionnaire | La dernière version du protocole de chiffrement de sécurité TLS (Transport Layer) pris en charge entre le fournisseur de point de terminaison et l’application utilisateur. Si le certificat du serveur est inexistant ou non valide, le chiffrement est considéré comme non pris en charge.|
| Heartbleed corrigé | Sécurité | Booléen | True, False | Est l’implémentation de SSL du serveur corrigé le bogue Heartbleed afin de réduire la vulnérabilité ? |
| En-têtes de sécurité HTTP : Strict-Transport-Security | Sécurité | Booléen | True, False | Est des en-têtes implémentées par l’application sur son site Web HTTP Strict-Transport-Security ? |
| En-têtes de sécurité HTTP : Stratégie de sécurité de contenu | Sécurité | Booléen | True, False | Est HTTP Content-Security-Policy en-têtes implémentées par l’application sur son site Web ? |
| En-têtes de sécurité HTTP : X-Frame-Options | Sécurité | Booléen | True, False | Les en-têtes HTTP X-Frame-Options sont implémentées par l’application sur son site Web ? |
| En-têtes de sécurité HTTP : X-Content-Type-Options | Sécurité | Booléen | True, False | Les en-têtes HTTP X-Content-Type-Options sont implémentées par l’application sur son site Web ? |
| En-têtes de sécurité HTTP : X-XSS-Protection | Sécurité | Booléen | True, False | Est des en-têtes implémentées par l’application sur son site Web HTTP X-XSS-Protection ? |
| Prend en charge SAML | Sécurité | Booléen | True, False | Cette application prend-elle en charge la norme SAML pour l’échange de données d’authentification et d’autorisation ? |
| Protégé contre les attaques DROWN | Sécurité | Booléen | True, False | Les serveurs d’applications sont protégés contre les attaques DROWN ? |
| Test de pénétration | Sécurité | Booléen | True, False | Cette application effectue-t-elle des tests de pénétration pour détecter et évaluer les vulnérabilités du réseau ? |
| Requiert une authentification utilisateur | Sécurité | Booléen | True, False | Cette application requièrent une authentification et interdit-elle l’utilisation anonyme ? |
| Stratégie de mot de passe : Limite de longueur de mot de passe | Sécurité | Booléen | True, False | Cette application met-elle une limite de longueur sur la création de mot de passe ? |
| Stratégie de mot de passe : Combinaison de caractères | Sécurité | Booléen | True, False | Cette application met-elle une combinaison de caractères lors de la création du mot de passe ? |
| Stratégie de mot de passe : Modifier la période de mot de passe | Sécurité | Booléen | True, False | Cette application met-elle aux utilisateurs de réinitialiser leur mot de passe régulièrement ? |
| Stratégie de mot de passe : Réutilisation et l’historique du mot de passe | Sécurité | Booléen | True, False | Cette application ne ne pas autoriser la réutilisation des anciens mots de passe ? |
| Stratégie de mot de passe : Utilisation des informations personnelles | Sécurité | Booléen | True, False | Cette application ne ne pas autoriser l’utilisation des données personnelles dans les mots de passe ? |
| stratégie de mot de passe | Sécurité | Booléen | True, False | Cette application met-elle à une stratégie de mot de passe conforme aux meilleures pratiques ? |
| FINRA | Compatibilité | Booléen | True, False, n/a | Cette application sont conformes aux FINRA, une norme définie pour les organisations à but non lucratif autorisés par le congrès qui régule et renforce l’amélioration des mesures de protection des investisseurs et l’intégrité du marché ? |
| FISMA | Compatibilité | Booléen | True, False, n/a | Cette application répond-elle à la FISMA, américaine qui définit une infrastructure complète pour protéger les informations du gouvernement, les opérations et les ressources au sein des agences fédérales, contre les menaces ? |
| GAAP | Compatibilité | Booléen | True, False, n/a | Cette application est-elle conforme avec GAAP, une collection de règles couramment suivi et de normes pour le reporting financier ? |
| HIPAA | Compatibilité | Booléen | True, False, n/a | Cette application répond-elle à la HIPAA, américaine qui définit des normes de protection de la confidentialité et la sécurité des informations de santé individuellement identifiables ? |
| ISAE 3402 | Compatibilité | Booléen | True, False, n/a | Cette application est-elle conforme avec la norme ISAE 3402, une norme mondiale fournissant l’assurance qu’un organisme de services a des contrôles appropriés en place ? |
| ISO 27001 | Compatibilité | Booléen | True, False, n/a | Est cette application certifiée ISO 27001, un certificat aux entreprises respectueuses des consignes reconnues et des principes de l’initialisation, implémenter, maintenir et d’améliorer la gestion de sécurité d’information au sein d’une organisation ? |
| ITAR | Compatibilité | Booléen | True, False, n/a | Cette application répond-elle à ITAR, lois de contrôle de l’exportation et l’importation des articles relatifs à la défense et de services, consultez la liste des Munitions nous ? |
| SOC 1 | Compatibilité | Booléen | True, False, n/a | Cette application est-elle conforme avec SOC 1, création de rapports sur les contrôles à un organisme de services qui sont pertinents pour le contrôle interne des entités utilisateur compte-rendu financier ? |
| SOC 2 | Compatibilité | Booléen | True, False, n/a | Cette application répond-elle au SOC 2, création de rapports sur le traitement non financier basé sur un ou plusieurs des critères de service de confiance sur la sécurité, confidentialité, disponibilité, la confidentialité et l’intégrité du traitement ? |
| SOC 3 | Compatibilité | Booléen | True, False, n/a | Cette application répond-elle au SOC 3, création de rapports en fonction des critères de service de confiance, qui peuvent être diffusés librement et ne contient qu’assertion de la direction qu’ils satisfont aux exigences des critères choisis ? |
| SOX | Compatibilité | Booléen | True, False, n/a | Cette application répond-elle à SOX, américaine visant à protéger les actionnaires et le grand public à partir des erreurs de comptabilité ou des fraudes, mais aussi améliorant l’exactitude des divulgations d’entreprise ? |
| SP 800-53 | Compatibilité | Booléen | True, False, n/a | Cette application répond-elle à SP 80053, des contrôles de sécurité pour les systèmes d’information fédéraux et organisations recommandés ? |
| SSAE 16 | Compatibilité | Booléen | True, False, n/a | Cette application est-elle conforme à la norme SSAE 16 pour l’audit des contrôles de conformité internes d’un organisme de services et les rapports de processus ? |
| Version de PCI DSS | Compatibilité | Chaîne | 1, 2, 3, 3.1, 3.2, N/A | La version du protocole PCI-DSS prise en charge par cette application. |
| ISO 27018 | Compatibilité | Booléen | True, False, n/a | Cette application est-elle conforme à la norme ISO 27018, qui établit couramment acceptées de contrôles et des consignes pour traiter et protéger les informations personnellement identifiables (PII) dans un public environnement de cloud computing ? |
| GLBA | Compatibilité | Booléen | True, False, n/a | Cette application est-elle conforme avec la loi Gramm-Leach-Bliley Act (GLBA), ce qui oblige les institutions financières établissent des normes pour protéger la sécurité et la confidentialité des informations personnelles des clients ? |
| Niveau FedRAMP | Compatibilité | Chaîne | Haut, moyen, faible, n/a | Le niveau de la solution compatible FedRAMP fourni par cette application. |
| Niveau CSA STAR | Compatibilité | Chaîne | Auto-évaluation, Certification, Attestation, évaluation C-STAR, surveillance continue : n/a | Le niveau du programme CSA STAR à laquelle l’application est certifiée |
| Privacy Shield | Compatibilité | Booléen | True, False, n/a | Cette application est-elle conforme avec l’infrastructure de bouclier de confidentialité des États-Unis de l’Union européenne, qui impose des obligations plus sévères aux entreprises américaines pour protéger les données personnelles des européens ? |
| ISO 27017 | Compatibilité | Booléen | True, False, n/a | Cette application est-elle conforme à la norme ISO 27017, qui établit des contrôles communément acceptés et des consignes pour traiter et protéger les informations utilisateur dans un environnement de cloud computing public ? |
| COBIT | Compatibilité | Booléen | True, False, n/a | Cette application répond-elle à COBIT, qui définit les meilleures pratiques de gouvernance et de contrôle des systèmes d’information et de la technologie et aligne informatique avec les principes de l’entreprise ? |
| COPPA | Compatibilité | Booléen | True, False, n/a | Cette application est-elle conforme avec COPPA, qui définit la configuration requise sur le site Web et les opérateurs de services en ligne qui fournissent du contenu à des enfants âgés de moins de 13 ans ? |
| FERPA | Compatibilité | Booléen | True, False, n/a | Cette application est-elle conforme avec cette loi, une loi fédérale qui protège la confidentialité des dossiers éducatifs ? |
| GAPP | Compatibilité | Booléen | True, False, n/a | Cette application est-elle conforme avec GAPP, une collection de règles de suivi couramment répondant aux risques de confidentialité d’une organisation ? |
| CSF HITRUST | Compatibilité | Booléen | True, False, n/a | Cette application est-elle conforme avec HITRUST CSF, un ensemble de contrôles qui harmonise les exigences des normes et réglementations de sécurité d’informations ? |
| Commandements de Forum de Jéricho | Compatibilité | Booléen | True, False, n/a | Cette application suit Jéricho commandements de Forum, un ensemble si principes à respecter lors de la conception des systèmes pour sécuriser fonctionnement dans les environnements perimeterized Annuler ? |
| ISO 27002 | Compatibilité | Booléen | True, False, n/a | Cette application est-elle conforme à la norme ISO 27002, qui établit des lignes directrices communes pour les normes de sécurité des informations organisationnelles et des pratiques de gestion de sécurité d’informations ? |
| FFIEC | Compatibilité | Booléen | True, False, n/a | Cette application répond-elle grâce à l’aide de la Federal Financial Institutions examen du Conseil sur les contrôles de gestion des risques nécessaires pour authentifier les services dans un environnement d’opérations bancaires Internet ? |
| Propriété des données | Juridique | Booléen | True, False | Cette application entièrement conserve la propriété de l’utilisateur de données chargées ? |
| DMCA | Juridique | Booléen | True, False | Cette application est-elle conforme avec la Digital Millennium Copyright Act (DMCA), qui criminalise toute tentative d’accès illégal à par droit d’auteur ? |
| Stratégie de conservation des données | Juridique | Booléen | True, False | Qu’est la stratégie de l’application pour la rétention des données utilisateur après l’arrêt de compte ? |
| Déclaration de compatibilité RGPD | Juridique | Adresse URL | Texte libre | Un lien vers votre site Web, le cas échéant, indiquant comment ce fournisseur envisage gérer la conformité RGPD. |
| RGPD - droite à l’effacement | Juridique | Booléen | True, False, n/a | Cette application d’interrompre le traitement et supprimer les données personnelles d’un individu à la demande ? |
| RGPD - violations de données de rapport | Juridique | Booléen | True, False, n/a | Est-ce violations de données de rapport application pour les autorités de surveillance et les personnes affectées par la violation de la sécurité dans les 72 heures de détection de violation ? |
| RGPD - évaluation de l’Impact | Juridique | Booléen | True, False, n/a | Cette application mener des évaluations d’impact de protection de données pour identifier les personnes ? |
| RGPD - contrôle de données sécurisé bordure croisée | Juridique | Booléen | True, False, n/a | Cette application transférer en toute sécurité des données au-delà des frontières ? |
| RGPD - agent de protection des données | Juridique | Booléen | True, False, n/a | Cette application nomme une données délégué à la protection de surveiller la stratégie de sécurité des données et la conformité RGPD ? |
| RGPD - droite à l’objet | Juridique | Booléen | True, False, n/a | Cette application fournit-il des personnes avec la possibilité d’objet pour le traitement de leurs données personnelles dans certaines circonstances ? |
| RGPD - droit d’accéder à | Juridique | Booléen | True, False, n/a | Cette application fournit-il des personnes avec la possibilité de connaître, à la demande, les données personnelles à l’aide d’une entreprise et son utilisation ? |
| RGPD - directement aux données Portablility | Juridique | Booléen | True, False, n/a | Cette application fournit-il des personnes avec la possibilité d’obtenir et de réutiliser ses données personnelles pour leurs propres besoins pour différents services à la demande ? |
| RGPD - droit d’information | Juridique | Booléen | True, False, n/a | Cette application informe des individus parmi les dispositifs de protection appropriés que nécessaire lorsque des données personnelles sont transférées à un pays ou une organisation internationale ? |
| RGPD - droite à la restriction de traitement | Juridique | Booléen | True, False, n/a | Cette application fournit-il des personnes avec la possibilité de bloquer ou de supprimer le traitement des données personnelles ? |
| RGPD - droits liés à la prise de décision automatisée | Juridique | Booléen | True, False, n/a | Cette application fournit-il des personnes avec la possibilité de choisir de ne pas être soumis à une décision est basée uniquement sur un traitement automatisé ? Cela inclut le profilage, qui peuvent avoir des conséquences légales. |
| RGPD - base légale pour traitement | Juridique | Booléen | True, False, n/a | Cette application traite des données personnelles légalement conformément de consentement, contrat, obligation légale, intérêts vitaux, intérêts légitimes, catégorie spéciale, données et les données de délit ? |
| RGPD - droite à rectification | Juridique | Booléen | True, False, n/a | Cette application fournit-il des personnes avec la possibilité de corriger ses données personnelles ? Le contrôleur doit répondre à toutes les demandes à partir de ses sujets de données au sein d’un mois. |


\* Champs de type *tableau* doivent être séparées par un point-virgule ( ;).

## <a name="next-steps"></a>Étapes suivantes 
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/) 

