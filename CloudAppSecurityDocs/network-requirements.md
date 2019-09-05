---
title: Configuration requise du réseau - Cloud App Security | Microsoft Docs
description: Cet article décrit les adresses IP et les ports à ouvrir pour utiliser Cloud App Security.
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: ShlomoSagir-MS
ms.date: 8/4/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 4de606f2-a09e-4e48-a578-e223de8b5e69
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 0ef957575f3bb3047c6b0f73057dd0a78abd9e1f
ms.sourcegitcommit: dc8b370e62e61a4f2f8a2baea75b564c3bdbc345
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70259879"
---
# <a name="network-requirements"></a>Configuration requise pour le réseau

*S’applique à : Microsoft Cloud App Security*

Cet article fournit une liste de ports et d’adresses IP que vous devez autoriser et autoriser à utiliser avec Microsoft Cloud App Security.

## <a name="view-your-data-center"></a>Afficher votre centre de données

Certaines exigences stipulées ci-dessous varient en fonction du centre de données auquel vous êtes connecté.

Pour savoir à quel centre de données vous vous connectez, effectuez les étapes suivantes :

1. Dans le portail Cloud App Security, cliquez sur l’**icône de point d’interrogation** dans la barre de menus. Ensuite, sélectionnez **À propos de**.

    ![cliquez sur À propos de](./media/about-menu.png)

2. Dans l’écran de la version Cloud App Security, vous pouvez voir la région et le centre de données.

    ![Afficher votre centre de données](./media/data-center.png)

## <a name="portal-access"></a>Accès au portail

Pour accéder au portail Cloud App Security, ajoutez le **port de sortie 443** pour les adresses IP et les noms DNS suivants à la liste verte de votre pare-feu :

    portal.cloudappsecurity.com
    *.portal.cloudappsecurity.com
    cdn.cloudappsecurity.com
    https://adaproddiscovery.azureedge.net
    *.s-microsoft.com
    *.msecnd.net
    dev.virtualearth.net
    *.cloudappsecurity.com
    flow.microsoft.com
    static2.sharepointonline.com
    dc.services.visualstudio.com
    *.blob.core.windows.net

En outre, les éléments suivants doivent figurer dans la liste verte, en fonction du centre de données que vous utilisez :
> [!div class="mx-tableFixed"]
>
> |Centre de données|Adresses IP|Nom DNS|
> |----|----|----|
> |US1|13.64.26.88<br>13.64.29.32<br>13.80.125.22<br>13.91.91.243<br>40.74.1.235<br>40.74.6.204<br>51.143.58.207<br>52.137.89.147<br>52.183.75.62|\*.us.portal.cloudappsecurity.com|
> |US2|13.80.125.22<br>20.36.222.59<br>20.36.222.60<br>40.74.1.235<br>40.74.6.204<br>51.143.58.207<br>52.137.89.147<br>52.183.75.62<br>52.184.165.82|\*.us2.portal.cloudappsecurity.com|
> |US3|13.80.125.22<br>40.74.1.235<br>40.74.6.204<br>40.90.218.196<br>40.90.218.198<br>51.143.58.207<br>52.137.89.147<br>52.183.75.62|*.us3.portal.cloudappsecurity.com|
> |EU1|13.80.125.22<br>40.119.154.72<br>40.74.1.235<br>40.74.6.204<br>51.143.58.207<br>52.137.89.147<br>52.157.238.58<br>52.174.56.180<br>52.183.75.62|\*.eu.portal.cloudappsecurity.com<|
> |EU2|13.80.125.22<br>40.74.1.235<br>40.74.6.204<br>40.81.156.154<br>40.81.156.156<br>51.143.58.207<br>52.137.89.147<br>52.183.75.62|*.eu2.portal.cloudappsecurity.com|

> [!NOTE]
> Au lieu d’un caractère générique (\*) vous pouvez ouvrir seulement l’URL de votre locataire spécifique. Par exemple, d’après la capture d’écran ci-dessus, vous pouvez ouvrir : mod244533.us.portal.cloudappsecurity.com

## <a name="siem-agent-connection"></a>Connexion de l’agent SIEM

Pour permettre à Cloud App Security de se connecter à votre serveur SIEM, ajoutez le **port de sortie 443** pour les adresses IP suivantes à la liste verte de votre pare-feu :

> [!div class="mx-tableFixed"]
>
> |Centre de données|Adresses IP|
> |----|----|
> |US1|13.64.26.88<br>13.64.29.32<br>13.80.125.22<br>13.91.91.243<br>40.74.1.235<br>40.74.6.204<br>51.143.58.207<br>52.137.89.147<br>52.183.75.62|
> |US2|13.80.125.22<br>20.36.222.59<br>20.36.222.60<br>40.74.1.235<br>40.74.6.204<br>51.143.58.207<br>52.137.89.147<br>52.183.75.62<br>52.184.165.82|
> |US3|13.80.125.22<br>40.74.1.235<br>40.74.6.204<br>40.90.218.196<br>40.90.218.198<br>51.143.58.207<br>52.137.89.147<br>52.183.75.62|
> |EU1|13.80.125.22<br>40.119.154.72<br>40.74.1.235<br>40.74.6.204<br>51.143.58.207<br>52.137.89.147<br>52.157.238.58<br>52.174.56.180<br>52.183.75.62|
> |EU2|13.80.125.22<br>40.74.1.235<br>40.74.6.204<br>40.81.156.154<br>40.81.156.156<br>51.143.58.207<br>52.137.89.147<br>52.183.75.62|

> [!NOTE]
> Si vous n’avez pas spécifié de proxy lors de la configuration de l’agent Siem Cloud App Security, vous devez autoriser les http://ocsp.msocsp.com/ connexions http à et OCSP.DigiCert.com sur le port 80. Il est utilisé pour vérifier l’état de révocation du certificat lorsque vous vous connectez au portail Cloud App Security.

## <a name="app-connector"></a>Connecteur d’applications

Pour que certaines applications tierces soient accessibles par Cloud App Security, ces adresses IP peuvent être utilisées. Les adresses IP permettent à Cloud App Security de collecter les journaux et de fournir un accès pour la console Cloud App Security.

> [!NOTE]
>Vous verrez peut-être ces adresses IP dans les journaux d’activité du fournisseur, car Cloud App Security effectue des actions de gouvernance et des analyses à partir de ces adresses IP.

Pour se connecter à des applications tierces, autorisez Cloud App Security à se connecter à partir de ces adresses IP :

> [!div class="mx-tableFixed"]
>
> |Centre de données|Adresses IP||
> |----|----|----|
> |US1|13.64.196.27<br>13.64.198.19<br>13.64.198.97<br>13.64.199.41<br>13.64.26.88<br>13.64.29.32<br>13.64.30.117<br>13.64.30.118<br>13.64.30.76<br>13.64.31.116<br>13.68.76.47|13.86.176.189<br>13.86.176.211<br>13.91.61.249<br>13.91.91.243<br>13.91.98.185<br>13.93.216.68<br>13.93.233.42<br>40.118.211.172<br>104.42.54.148<br>104.209.35.177<br><br>|
> |US2|13.68.76.47<br>20.36.222.59<br>20.36.222.60<br>40.67.152.91<br>40.67.154.160<br>40.67.155.146<br>40.67.159.55<br>40.84.2.83<br>40.84.4.119<br>40.84.4.93|52.184.165.82<br>52.232.224.227<br>52.232.225.84<br>104.46.116.211<br>104.46.116.211<br>104.46.121.72<br>104.46.121.72<br>104.46.122.189<br>104.42.54.148<br>104.46.122.189<br>|
> |US3|13.68.76.47<br>40.90.218.196<br>40.90.218.197<br>40.90.218.198<br>40.90.218.203<br>40.90.220.190<br>40.90.220.196<br>51.143.120.236<br>51.143.120.242<br>104.42.54.148||
> |EU1|13.80.22.71<br>13.95.29.177<br>13.95.30.46<br>40.114.217.8<br>40.114.217.8<br>40.115.24.65<br>40.115.24.65<br>40.115.25.50<br>40.115.25.50<br>40.119.154.72|40.67.219.133<br>51.105.55.62<br>51.105.179.157<br>51.137.200.32<br>52.157.232.110<br>52.157.233.133<br>52.157.233.92<br>52.157.238.58<br>52.157.239.110<br>52.174.56.180|
> |EU2|40.81.152.171<br>40.81.152.172<br>40.81.156.153<br>40.81.156.154<br>40.81.156.155<br>40.81.156.156<br>51.105.55.62<br>51.137.200.32<br>51.145.108.227<br>51.145.108.250|

## <a name="third-party-dlp-integration"></a>Intégration de solutions DLP tierces

Pour que Cloud App Security puisse envoyer des données via votre stunnel à votre serveur ICAP, ouvrez votre pare-feu DMZ à ces adresses IP avec un numéro de port source dynamique.

1. **Adresses sources** : ces adresses doivent figurer sur la liste verte, comme mentionné ci-dessus pour les applications tierces du connecteur d’API
2. **Port TCP source** : dynamique
3. **Adresse(s) de destination** : une ou deux adresses IP du stunnel connecté au serveur ICAP externe
4. **Port TCP de destination** : comme défini dans votre réseau

> [!NOTE]
> - Par défaut, le numéro de port du stunnel a la valeur 11344. Vous pouvez le remplacer par un autre port si nécessaire, mais n’oubliez pas de noter le nouveau numéro de port.
> - Vous verrez peut-être ces adresses IP dans les journaux d’activité du fournisseur, car Cloud App Security effectue des actions de gouvernance et des analyses à partir de ces adresses IP.

Pour se connecter à des applications tierces et s’intégrer à des solutions DLP externes, autorisez Cloud App Security à se connecter à partir de ces adresses IP :

> [!div class="mx-tableFixed"]
>
> |Centre de données|Adresses IP||
> |----|----|----|
> |US1|13.64.196.27<br>13.64.198.19<br>13.64.198.97<br>13.64.199.41<br>13.64.26.88<br>13.64.29.32<br>13.64.30.117<br>13.64.30.118<br>13.64.30.76<br>13.64.31.116|13.86.176.189<br>13.86.176.211<br>13.91.61.249<br>13.91.91.243<br>13.91.98.185<br>13.93.216.68<br>13.93.233.42<br>40.118.211.172<br>104.209.35.177<br><br>|
> |US2|20.36.222.59<br>20.36.222.60<br>40.67.152.91<br>40.67.154.160<br>40.67.155.146<br>40.67.159.55<br>40.84.2.83<br>40.84.4.119<br>40.84.4.93|52.184.165.82<br>52.232.224.227<br>52.232.225.84<br>104.46.116.211<br>104.46.116.211<br>104.46.121.72<br>104.46.121.72<br>104.46.122.189<br>104.46.122.189|
> |US3|40.90.218.196<br>40.90.218.197<br>40.90.218.198<br>40.90.218.203<br>40.90.220.190<br>40.90.220.196<br>51.143.120.236<br>51.143.120.242||
> |EU1|13.80.22.71<br>13.95.29.177<br>13.95.30.46<br>40.67.219.133<br>40.114.217.8<br>40.114.217.8<br>40.115.24.65<br>40.115.24.65<br>40.115.25.50|40.119.154.72<br>51.105.179.157<br>52.157.232.110<br>52.157.233.133<br>52.157.233.92<br>52.157.238.58<br>52.157.239.110<br>52.174.56.180<br><br>|
> |EU2|40.81.152.171<br>40.81.152.172<br>40.81.156.153<br>40.81.156.154<br>40.81.156.155<br>40.81.156.156<br>51.145.108.227<br>51.145.108.250||

## <a name="mail-server"></a>Serveur de messagerie

Pour permettre l’envoi de notifications à partir du modèle et des paramètres par défaut, ajoutez ces adresses IP à votre liste d’autorisation anti-spam. Les adresses IP de courrier dédiées à Cloud App Security sont les suivantes :

- 65.55.234.192/26
- 207.46.200.0/27
- 65.55.52.224/27
- 94.245.112.0/27
- 111.221.26.0/27
- 207.46.50.192/26

Si vous voulez personnaliser l’identité de l’expéditeur de l’e-mail, Microsoft Cloud App Security vous permet de le faire à l’aide de MailChimp®, un service de messagerie tiers. Pour cela, dans le portail Microsoft Cloud App Security, accédez à **Paramètres**. Sélectionnez **Paramètres de messagerie** et passez en revue les termes du contrat de service et la déclaration de confidentialité de MailChimp. Ensuite, autorisez Microsoft à utiliser MailChimp en votre nom.

Si vous ne personnalisez pas l’identité de l’expéditeur, vos notifications par e-mail seront envoyées avec tous les paramètres par défaut.

Pour utiliser MailChimp, ajoutez cette adresse IP à votre liste d’autorisation anti-spam pour permettre l’envoi de notifications : 198.2.134.139 (mail1.cloudappsecurity.com)

## <a name="log-collector"></a>Collecteur de journaux

Pour activer les fonctionnalités Cloud Discovery à l’aide d’un collecteur de journaux et détecter l’informatique fantôme dans votre organisation, ouvrez les éléments suivants :

- Autorisez le collecteur de journaux à recevoir le trafic FTP et Syslog entrant.
- Autorisez le collecteur de journaux à lancer le trafic sortant sur le portail (par exemple, contoso.cloudappsecurity.com) sur le port 443.
- Autorisez le collecteur de journaux à initier le trafic sortant vers le stockage Blob Azure sur le port 443 :

  | Centre de données |                        URL                        |
  |-------------|---------------------------------------------------|
  |     US1     | https :\//adaprodconsole.blob.Core.Windows.net/     |
  |     US2     | https :\//prod03use2console1.blob.Core.Windows.net/ |
  |     US3     | https :\//prod5usw2console1.blob.Core.Windows.net/  |
  |     EU1     | https :\//prod02euwconsole1.blob.Core.Windows.net/  |
  |     EU2     | https :\//prod4uksconsole1.blob.Core.Windows.net/   |

> [!NOTE]
> - Si votre pare-feu nécessite une liste d’accès à d’adresses IP statiques et qu’il ne prend pas en charge une liste verte basée sur des URL, autorisez le collecteur de journaux à émettre le trafic sortant vers les [plages IP du centre de données Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653) sur le port 443.
>- Autorisez le collecteur de journaux à diriger le trafic sortant vers le portail Cloud App Security.
>- Si vous n’avez pas spécifié de proxy lors de la configuration du collecteur de journaux, vous devez autoriser http://ocsp.msocsp.com/ les connexions http à et OCSP.DigiCert.com sur le port 80. Il est utilisé pour vérifier l’état de révocation du certificat lorsque vous vous connectez au portail Cloud App Security.

## <a name="next-steps"></a>Étapes suivantes

[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[Les clients Premier peuvent également créer une demande de support directement dans le portail Premier.](https://premier.microsoft.com/)
