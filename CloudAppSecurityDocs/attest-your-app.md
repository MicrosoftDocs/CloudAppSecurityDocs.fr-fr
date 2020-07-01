---
title: Certifiez vos applications-Cloud App Security
description: Cet article fournit des instructions pour l’attestation de vos applications dans Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 01/30/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 55bbd68f012dbfd8053154e8f3e44c1af8cce9ae
ms.sourcegitcommit: b15034dd50142afd8e95de22a9232f711b1eae6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85624344"
---
# <a name="attest-your-app"></a>Attester votre application

Microsoft Cloud App Security vous permet d’attester votre application pour vous assurer que les détails de conformité et de sécurité que nous utilisons pour évaluer votre application dans le catalogue d’applications Cloud sont à jour.

Si votre application est déjà listée dans le catalogue d’applications Cloud, ou si elle est nouvelle, soumettez un [questionnaire d’auto-attestation](https://go.microsoft.com/fwlink/?linkid=2106624). Pour plus d’informations sur le processus d’auto-attestation, contactez casfeedback@microsoft.com .

Suivez les attributs de service décrits ci-dessous pour terminer avec succès la soumission du questionnaire :

| Champ | Catégorie d’informations | Type | Valeurs acceptées | Description |
|------|-------|------|---------|----------|
| Nom de l’application | Général | String | Texte libre | Nom de votre application tel qu’il doit apparaître dans le catalogue d’applications Cloud. |
| Description | Général | String | Texte libre | Brève explication de ce que votre application permet aux utilisateurs d’effectuer ou d’atteindre. |
| Category| Général | String | Fermer la liste-fourni dans le questionnaire | Classification de l’application en fonction du champ auquel elle se rapporte. |
| Siège social | Général | Code pays | Fermer la liste-fourni dans le questionnaire | Pays du siège du fournisseur.|
| Centre de données| Général | Tableau de codes de pays * | Fermer la liste-fourni dans le questionnaire (sélection multiple) | Le pays dans lequel se trouve votre centre de données (peut être plusieurs emplacements) |
| Société d’hébergement | Général | String | Texte libre | Nom de la société qui fournit l’hébergement de serveur pour l’application. |
| Doutes | Général | Integer | AAAA (pas plus de 2019) | Année de Fondation du fournisseur. |
| Holding | Général | String | Privé, public | Indique si le fournisseur est une société publique ou privée |
| Domaine d’application | Général | Tableau d’URL * | Texte libre | Liste des domaines spécifiques qui sont utilisés pour interagir avec le service. Par exemple, « teams.microsoft.com » pour Microsoft teams et non le domaine générique « microsoft.com ». |
| Conditions d'utilisation | Général | URL | Texte libre | Cette application fournit-elle un ensemble de réglementations que les utilisateurs doivent accepter de suivre pour pouvoir utiliser l’application ? |
| Politique de confidentialité | Général | URL | Texte libre | Lien vers un document juridiquement contraignant relatif à la façon dont ce fournisseur gère les informations sur les clients, les clients ou les employés rassemblées dans le cadre de l’application. |
| URL de connexion | Général | Tableau d’URL * | Texte libre | URL via laquelle les utilisateurs se connectent à l’application. |
| Fournisseur | Général | String | Texte libre | Nom du fournisseur qui fournit cette application. |
| Types de données | Général | String | Fermer la liste-fourni dans le questionnaire | Quels types de données peuvent être téléchargés par l’utilisateur vers l’application ?|
| Page d’accueil | Général | URL | Texte libre | URL de la page d’hébergement du fournisseur. |
| Plan de récupération d’urgence | Général | Booléen | True, False | Cette application a-t-elle un plan de récupération d’urgence qui comprend une stratégie de sauvegarde et de restauration ? |
| Dernière violation | Sécurité | Date | MMM-jj-aaaa | Incident le plus récent dans lequel les données sensibles, protégées ou confidentielles détenues par l’application ont été affichées, volées ou utilisées par un individu non autorisé à cette fin. |
| Méthode de chiffrement des données au repos | Sécurité | String | Fermer la liste-fourni dans le questionnaire | Type de chiffrement des données au repos effectuées sur l’application. |
| Authentification multifacteur | Sécurité | Booléen | True, False | Cette application prend-elle en charge les solutions multi-Factor Authentication ? |
| Restriction d’adresse IP | Sécurité | Booléen | True, False | Cette application prend-elle en charge la restriction d’adresses IP spécifiques par l’application ? |
| Piste d’audit de l’utilisateur | Sécurité | Booléen | True, False | Cette application prend-elle en charge la disponibilité de la piste d’audit par compte d’utilisateur ? |
| Piste d’audit de l’administrateur | Sécurité | Booléen | True, False | Cette application prend-elle en charge la disponibilité d’une piste d’audit de l’administrateur dans l’application ? |
| Piste d’audit des données | Sécurité | Booléen | True, False | Cette application prend-elle en charge la disponibilité d’une piste d’audit des données dans l’application ? |
| L’utilisateur peut charger des données | Sécurité | Booléen | True, False | Cette application prend-elle en charge les données chargées par l’utilisateur ? |
| Classification des données | Sécurité | Booléen | True, False | Cette application active-t-elle l’option de classification des données chargées dans l’application ? |
| Se souvenir du mot de passe | Sécurité | Booléen | True, False | Cette application active-t-elle l’option de mémorisation et d’enregistrement des mots de passe utilisateur dans l’application ? |
| Prise en charge des rôles d’utilisateur | Sécurité | Booléen | True, False | Cette application prend-elle en charge la distribution des utilisateurs par rôles et niveaux d’autorisation ? |
| Partage de fichiers | Sécurité | Booléen | True, False | Cette application inclut-elle des fonctionnalités qui permettent le partage de fichiers entre les utilisateurs ? |
| Prend en charge SAML | Sécurité | Booléen | True, False | Cette application prend-elle en charge la norme SAML pour l’échange de données d’authentification et d’autorisation ? |
| Protégé contre les NOYERs | Sécurité | Booléen | True, False | Les serveurs d’applications sont-ils protégés contre les attaques par noyer ? |
| Test de pénétration | Sécurité | Booléen | True, False | Cette application effectue-t-elle des tests d’intrusion pour détecter et évaluer les vulnérabilités du réseau ? |
| Nécessite l’authentification de l’utilisateur | Sécurité | Booléen | True, False | Cette application nécessite-t-elle une authentification et interdit l’utilisation anonyme ? |
| Stratégie de mot de passe : limite de longueur du mot de passe | Sécurité | Booléen | True, False | Cette application applique-t-elle une longueur limite à la création du mot de passe ? |
| Stratégie de mot de passe : combinaison de caractères | Sécurité | Booléen | True, False | Cette application applique-t-elle une combinaison de caractères lors de la création du mot de passe ? |
| Stratégie de mot de passe : modifier la période de mot de passe | Sécurité | Booléen | True, False | Cette application impose-t-elle aux utilisateurs de réinitialiser leur mot de passe régulièrement ? |
| Stratégie de mot de passe : historique et réutilisation des mots de passe | Sécurité | Booléen | True, False | Cette application interdit-t-elle la réutilisation des anciens mots de passe ? |
| Stratégie de mot de passe : utilisation des informations personnelles | Sécurité | Booléen | True, False | Cette application interdit-t-elle l’utilisation d’informations personnelles dans les mots de passe ? |
| Stratégie de mot de passe | Sécurité | Booléen | True, False | Cette application applique-t-elle une stratégie de mot de passe conforme aux meilleures pratiques ? |
| FINRA | Compatibilité | Booléen | True, false, N/A | Cette application est-elle conforme à FINRA, un ensemble standard pour les organisations à but non lucratif autorisées par le Congrès, qui réglemente et applique l’amélioration de la protection des investisseurs et de l’intégrité du marché ? |
| FISMA | Compatibilité | Booléen | True, false, N/A | Cette application est-elle conforme à FISMA, la législation américaine qui définit une infrastructure complète pour protéger les informations, les opérations et les ressources gouvernementales au sein des agences fédérales, contre les menaces ? |
| PCGR | Compatibilité | Booléen | True, false, N/A | Cette application est-elle conforme à PCGR, une collection de règles et de normes de comptabilité couramment suivies pour la création de rapports financiers ? |
| HIPAA | Compatibilité | Booléen | True, false, N/A | Cette application est-elle conforme à la loi HIPAA, la législation américaine qui définit des normes pour la protection de la confidentialité et de la sécurité des informations d’intégrité identifiables individuellement ? |
| ISAE 3402 | Compatibilité | Booléen | True, false, N/A | Cette application est-elle conforme à ISAE 3402, la norme mondiale fournissant l’assurance qu’une organisation de service a des contrôles appropriés en place ? |
| ISO 27001 | Compatibilité | Booléen | True, False | Cette application est-elle conforme à la norme ISO 27001, un certificat donné aux entreprises qui a fourni aux entreprises des directives et des principes généraux reconnus au niveau international pour initier, implémenter, maintenir et améliorer la gestion de la sécurité des informations au sein d’une organisation ? |
| ITAR | Compatibilité | Booléen | True, false, N/A | Cette application est-elle conforme à ITAR, règlements contrôlant l’exportation et l’importation d’articles et de services liés à la défense figurant dans la liste des munitions des États-Unis ? |
| SOC 1 | Compatibilité | Booléen | True, false, N/A | Cette application est-elle conforme à SOC 1 et signale-t-elle les contrôles d’une organisation de service qui sont pertinents pour le contrôle interne des entités utilisateur sur les rapports financiers ? |
| SOC 2 | Compatibilité | Booléen | True, False | Cette application est-elle conforme à la société SOC 2, qui signale un traitement non financier basé sur un ou plusieurs des critères de service d’approbation relatifs à la sécurité, la confidentialité, la disponibilité, la confidentialité et l’intégrité du traitement ? |
| SOC 3 | Compatibilité | Booléen | True, False | Cette application est-elle conforme à la société SOC 3, qui signale les critères du service d’approbation, qui peuvent être distribués librement et qui ne contiennent que l’assertion de la direction selon laquelle ils ont répondu aux exigences des critères choisis. |
| SOX | Compatibilité | Booléen | True, false, N/A | Cette application est-elle conforme à la législation SOX et aux États-Unis visant à protéger les actionnaires et le grand public contre les erreurs et les fraudes comptables, ainsi qu’à améliorer la précision des divulgations d’entreprise ? |
| SP 800-53 | Compatibilité | Booléen | True, False | Cette application est-elle conforme à SP80053, les contrôles de sécurité recommandés pour les organisations et les systèmes d’information fédéraux ? |
| SSAE 16 | Compatibilité | Booléen | True, false, N/A | Cette application est-elle conforme à la norme SSAE 16 pour l’audit des contrôles de conformité internes et des processus de création de rapports d’une organisation de service ? |
| Version de PCI DSS | Compatibilité | String | 1, 2, 3, 3,1, 3,2, N/A | Version du protocole PCI-DSS prise en charge par cette application. |
| ISO 27018 | Compatibilité | Booléen | True, false, N/A | Cette application est-elle conforme à la norme ISO 27018, qui établit des contrôles et des instructions couramment acceptés pour le traitement et la protection des informations d’identification personnelle (PII) dans un environnement de cloud computing public ? |
| GLBA | Compatibilité | Booléen | True, false, N/A | Cette application est-elle conforme à la loi Gramm-Leach-Bliley Act (GLBA), qui exige que les institutions financières établissent des normes de protection de la sécurité et de la confidentialité des informations personnelles des clients ? |
| Niveau FedRAMP | Compatibilité | String | Haute, modéré, faible, Li-SaaS | Niveau de la solution conforme à FedRAMP fournie par cette application. |
| Niveau CSA STAR | Compatibilité | String | Auto-évaluation, certification, attestation, évaluation C-STAR, surveillance continue | Niveau du programme CSA STAR sur lequel l’application est certifiée |
| Bouclier de protection des données | Compatibilité | Booléen | True, false, N/A | Cette application est-elle conforme à l’infrastructure de protection de la confidentialité UE-US, qui impose des obligations plus fortes aux entreprises américaines pour protéger les données personnelles des européens ? |
| ISO 27017 | Compatibilité | Booléen | True, False | Cette application est-elle conforme à la norme ISO 27017, qui établit des contrôles et des recommandations couramment acceptés pour le traitement et la protection des informations utilisateur dans un environnement de Cloud Computing public ? |
| COBIT | Compatibilité | Booléen | True, False | Cette application est-elle conforme à COBIT, qui définit les meilleures pratiques pour la gouvernance et le contrôle des systèmes d’information et de la technologie, et l’aligne sur les principes de l’entreprise ? |
| COPPA | Compatibilité | Booléen | True, false, N/A | Cette application est-elle conforme à la réglementation COPPA, qui définit les exigences relatives au site Web et aux opérateurs de services en ligne qui fournissent du contenu aux enfants âgés de moins de 13 ans ? |
| FERPA | Compatibilité | Booléen | True, false, N/A | Cette application est-elle conforme à FERPA, une loi fédérale qui protège la confidentialité des dossiers de formation des élèves ? |
| GAPP | Compatibilité | Booléen | True, false, N/A | Cette application est-elle conforme à GAPP, un ensemble de règles couramment suivies qui répondent aux risques de confidentialité dans une organisation ? |
| CSF HITRUST | Compatibilité | Booléen | True, false, N/A | Cette application est-elle conforme à HITRUST CSF, un ensemble de contrôles qui harmonise les exigences des normes et des réglementations en matière de sécurité des informations ? |
| Commandes du Forum Jéricho | Compatibilité | Booléen | True, False | Cette application suit-elle les commandes de Forum Jéricho, une série de principes à observer lors de l’architecture de systèmes pour une opération sécurisée dans des environnements désous-périmètres ? |
| ISO 27002 | Compatibilité | Booléen | True, false, N/A | Cette application est-elle conforme à la norme ISO 27002, qui établit des recommandations communes pour les normes de sécurité des informations de l’organisation et les pratiques de gestion de la sécurité des informations ? |
| FFIEC | Compatibilité | Booléen | True, false, N/A | Cette application est-elle conforme aux conseils du Conseil de l’examen des institutions financières fédérales sur les contrôles de gestion des risques nécessaires à l’authentification des services dans un environnement bancaire Internet ? |
| Propriété des données | Informations juridiques | Booléen | True, False | Cette application conserve-t-elle entièrement la propriété des données téléchargées par l’utilisateur ? |
| DMCA | Informations juridiques | Booléen | True, False | Cette application est-elle conforme à la DMCA (Digital Millenium Copyright Act), qui criminalise toute tentative d’accès illégal à des documents protégés par des droits d’auteur ? |
| Stratégie de conservation des données | Informations juridiques | Booléen | True, False | Quelle est la stratégie de l’application pour la rétention des données utilisateur après l’arrêt du compte ? |
| RGPD Readiness (instruction) | Informations juridiques | URL | Texte libre | Un lien vers votre site Web, le cas échéant, lié à la façon dont ce fournisseur prévoit de gérer la conformité RGPD. |
| RGPD-droit d’effacement | Informations juridiques | Booléen | True, false, N/A | Cette application arrête-t-elle le traitement et supprime les données personnelles d’un individu à la demande ? |
| RGPD-violations de données de rapport | Informations juridiques | Booléen | True, false, N/A | Cette application signale-t-elle les violations de données aux autorités de supervision et aux personnes concernées par la violation, dans un délai de 72 heures de détection de violation ? |
| RGPD-impact de l’évaluation | Informations juridiques | Booléen | True, false, N/A | Cette application effectue-t-elle des évaluations d’impact sur la protection des données pour identifier les risques pour les individus ? |
| RGPD-contrôle de données croisées sécurisées | Informations juridiques | Booléen | True, false, N/A | Cette application transfère-t-elle les données en toute sécurité entre les bordures ? |
| RGPD-responsable de la protection des données | Informations juridiques | Booléen | True, false, N/A | Cette application désigne-t-elle un responsable de la protection des données pour superviser la stratégie de sécurité des données et la conformité RGPD ? |
| RGPD-droit à Object | Informations juridiques | Booléen | True, false, N/A | Cette application fournit-elle aux individus la possibilité d’effectuer des objets sur le traitement de leurs données personnelles dans certaines circonstances ? |
| RGPD-droit d’accès | Informations juridiques | Booléen | True, false, N/A | Cette application fournit-elle aux individus la possibilité de savoir, à la demande, quelles données personnelles une société utilise et comment elle est utilisée ? |
| RGPD-Right to Data portablility | Informations juridiques | Booléen | True, false, N/A | Cette application fournit-elle aux individus la possibilité d’obtenir et de réutiliser leurs données personnelles à des fins différentes sur différents services à la demande ? |
| RGPD-right pour être informé | Informations juridiques | Booléen | True, false, N/A | Cette application informe-elle les individus des protections appropriées qu’elle prend lorsque les données personnelles sont transférées à un pays non-UE ou à une organisation internationale ? |
| RGPD-droit à la restriction du traitement | Informations juridiques | Booléen | True, false, N/A | Cette application fournit-elle aux individus la possibilité de bloquer ou de supprimer le traitement des données personnelles ? |
| RGPD-droits liés à la prise de décision automatisée | Informations juridiques | Booléen | True, false, N/A | Cette application fournit-elle aux individus la possibilité de choisir de ne pas être soumis à une décision basée uniquement sur le traitement automatisé ? Cela comprend le profilage, qui peut avoir des ramifications légales. |
| RGPD-licite pour le traitement | Informations juridiques | Booléen | True, false, N/A | Cette application traite-t-elle les données personnelles licitement conformément à l’accord, au contrat, à l’obligation légale, aux intérêts essentiels, aux intérêts légitimes, aux catégories spéciales, aux données et au délit criminel ? |
| RGPD-droit à rectification | Informations juridiques | Booléen | True, false, N/A | Cette application fournit-elle aux individus la possibilité de corriger leurs données personnelles ? Le contrôleur doit répondre à toutes les demandes de ses sujets de données dans un délai d’un mois. |

\*Les champs de type *tableau* doivent être séparés par un point-virgule (;).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
