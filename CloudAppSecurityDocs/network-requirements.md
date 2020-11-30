---
title: Configuration requise pour le réseau
description: Cet article décrit les adresses IP et les ports à ouvrir pour utiliser Cloud App Security.
ms.date: 11/01/2019
ms.topic: how-to
ms.openlocfilehash: 78f054b4ba8ea1a2d11ddfd70e40aa2cbd7b8430
ms.sourcegitcommit: d87372b47ca98e942c2bf94032a6a61902627d69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96310870"
---
# <a name="network-requirements"></a>Configuration requise pour le réseau

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Cet article fournit une liste de ports et d’adresses IP que vous devez autoriser et autoriser à utiliser avec Microsoft Cloud App Security.

## <a name="view-your-data-center"></a>Afficher votre centre de données

Certaines exigences stipulées ci-dessous varient en fonction du centre de données auquel vous êtes connecté.

Pour savoir à quel centre de données vous vous connectez, effectuez les étapes suivantes :

1. Dans le portail Cloud App Security, cliquez sur l’**icône de point d’interrogation** dans la barre de menus. Ensuite, sélectionnez **À propos de**.

    ![cliquez sur À propos de](media/about-menu.png)

2. Dans l’écran de la version Cloud App Security, vous pouvez voir la région et le centre de données.

    ![Afficher votre centre de données](media/data-center.png)

## <a name="portal-access"></a>Accès au portail

Pour accéder au portail Cloud App Security, ajoutez le **port de sortie 443** pour les adresses IP et les noms DNS suivants à la liste verte de votre pare-feu :

```ini
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
```

Pour les clients du gouvernement des États-Unis, il est également nécessaire d’ajouter les noms DNS suivants à la liste verte de votre pare-feu pour fournir l’accès au portail Cloud App Security GCC High :

```ini
portal.cloudappsecurity.us
*.portal.cloudappsecurity.us
cdn.cloudappsecurity.com
```

En outre, les éléments suivants doivent être autorisés, en fonction du centre de données que vous utilisez :

|Centre de données|Adresses IP|Nom DNS|
|----|----|----|
|US1|13.64.26.88, 13.64.29.32, 13.80.125.22, 13.91.91.243, 40.74.1.235, 40.74.6.204, 51.143.58.207, 52.137.89.147, 52.183.75.62|\*.us.portal.cloudappsecurity.com|
|US2|13.80.125.22, 20.36.222.59, 20.36.222.60, 40.74.1.235, 40.74.6.204, 51.143.58.207, 52.137.89.147, 52.183.75.62, 52.184.165.82|\*.us2.portal.cloudappsecurity.com|
|US3|13.80.125.22, 40.74.1.235, 40.74.6.204, 40.90.218.196, 40.90.218.198, 51.143.58.207, 52.137.89.147, 52.183.75.62|*.us3.portal.cloudappsecurity.com|
|EU1|13.80.125.22, 40.74.1.235, 40.74.6.204, 40.119.154.72, 51.143.58.207, 52.137.89.147, 52.157.238.58, 52.174.56.180, 52.183.75.62|\*.eu.portal.cloudappsecurity.com<|
|EU2|13.80.125.22, 40.74.1.235, 40.74.6.204, 40.81.156.154, 40.81.156.156, 51.143.58.207, 52.137.89.147, 52.183.75.62|*.eu2.portal.cloudappsecurity.com|
|Gov US1|13.72.19.4, 52.227.143.223|*. us1.portal.cloudappsecurity.us|

> [!NOTE]
> Au lieu d’un caractère générique (\*) vous pouvez ouvrir seulement l’URL de votre locataire spécifique. Par exemple, d’après la capture d’écran ci-dessus, vous pouvez ouvrir : mod244533.us.portal.cloudappsecurity.com

## <a name="access-and-session-controls"></a>Contrôles d’accès et de session

Configurez votre pare-feu pour le proxy inverse à l’aide des paramètres relatifs à votre environnement.

### <a name="commercial-customers"></a>Clients commerciaux

Pour les clients commerciaux, pour activer Cloud App Security proxy inverse, ajoutez le **port de sortie 443** pour les adresses IP et les noms DNS suivants à la liste verte de votre pare-feu :

```ini
*.cas.ms
*.mcas.ms
*.admin-mcas.ms
mcasproxy.azureedge.net
```

En outre, les éléments suivants doivent être autorisés, en fonction du centre de données que vous utilisez :

|Centre de données|Adresses IP|Nom DNS|
|----|----|----|----|----|
|US1|20.40.134.94, 20.40.161.119, 20.40.161.135, 20.40.163.97, 20.40.163.133, 20.184.63.216, 20.184.63.232, 40.65.169.46, 40.65.169.97, 40.65.169.196, 40.65.169.236, 40.65.170.17, 40.66.59.41, 40.66.60.118, 40.66.60.180, 40.66.60.185, 40.66.60.200, 40.66.60.206, 40.66.60.207, 40.66.60.208, 40.66.62.78, 40.81.62.255, 40.81.63.1, 40.81.63.2, 40.81.63.4, 40.81.63.5, 40.81.63.8, 40.81.120.187, 40.81.121.107, 40.81.121.108, 40.81.121.111, 40.81.121.127, 40.81.122.76, 40.81.123.124, 40.81.127.140, 40.81.227.134, 40.81.227.152, 40.81.227.160, 40.81.227.163, 40.90.220.37, 40.91.114.44, 40.91.114.45, 40.91.114.46, 40.91.114.47, 40.91.114.48, 40.91.114.49, 40.91.126.157, 40.91.127.44, 40.119.215.167, 51.105.163.8, 51.105.163.43, 51.105.164.8, 51.105.165.31, 51.105.165.37, 51.105.165.63, 51.105.165.116, 51.105.166.102, 51.105.166.103, 51.105.166.106, 51.137.136.13, 51.137.136.14, 51.143.111.58, 52.142.112.145, 52.142.112.146, 52.142.116.135, 52.142.116.174, 52.142.116.250, 52.142.117.183, 52.142.121.6, 52.142.121.75, 52.148.115.238, 52.148.116.37, 52.156.197.254, 52.156.198.196|\*. us.cas.ms, \* . us.Access-Control.cas.ms, \* . us.SAML.cas.ms|
|US2|20.40.132.195, 20.40.161.140, 20.40.161.141, 20.40.163.88, 20.40.163.96, 40.65.170.26, 40.65.170.123, 40.65.170.125, 40.65.170.128, 40.65.170.133, 40.65.170.137, 40.66.56.158, 40.66.60.209, 40.66.60.210, 40.66.60.215, 40.66.60.216, 40.66.60.217, 40.66.60.219, 40.66.62.130, 40.66.63.148, 40.67.251.0, 40.81.58.180, 40.81.58.184, 40.81.58.193, 40.81.59.90, 40.81.59.93, 40.81.63.7, 40.81.121.135, 40.81.121.140, 40.81.122.62, 40.81.124.185, 40.81.127.25, 40.81.127.139, 40.81.127.141, 40.81.127.230, 40.119.207.131, 40.119.207.144, 51.137.137.118, 51.137.137.121, 52.139.245.40, 52.139.245.48, 52.142.127.127, 52.149.59.151, 52.149.60.12, 52.149.61.128, 52.149.61.214, 52.149.63.211, 52.151.237.243, 52.151.238.5, 52.155.166.50, 52.156.88.69, 52.156.88.173, 52.156.89.175, 52.156.89.188, 52.156.90.38, 52.156.197.208, 52.156.204.99, 52.156.205.222, 52.156.205.226, 52.156.206.45, 52.156.206.46, 52.156.206.47, 52.191.237.188, 52.191.238.65, 104.45.170.182, 104.45.170.184, 104.45.170.185, 104.45.170.188, 104.45.170.194, 104.45.170.196, 191.235.117.31, 191.235.119.253, 191.235.120.17, 191.235.121.69, 191.235.121.164, 191.235.122.60, 191.235.122.101, 191.235.122.224, 191.235.123.114, 191.235.123.242|\*. us2.cas.ms, \* . US2.Access-Control.cas.ms, \* . US2.SAML.cas.ms|
|US3|20.40.106.51, 20.40.107.84, 20.40.161.160, 20.40.161.161, 20.40.162.86, 20.40.162.200, 20.184.61.253, 20.184.63.158, 40.65.170.80, 40.65.170.81, 40.65.170.82, 40.65.170.83, 40.65.170.112, 40.65.170.113, 40.66.59.193, 40.66.59.195, 40.66.59.196, 40.66.59.246, 40.66.60.224, 40.66.60.226, 40.66.61.158, 40.66.61.193, 40.66.62.7, 40.66.62.9, 40.81.62.162, 40.81.62.179, 40.81.62.193, 40.81.62.220, 40.81.62.223, 40.81.62.224, 40.81.120.191, 40.81.120.192, 40.81.121.66, 40.81.123.157, 40.81.127.229, 40.81.127.239, 40.82.186.166, 40.82.186.168, 40.82.186.168, 40.82.186.169, 40.82.186.169, 40.82.186.176, 40.82.186.177, 40.82.186.177, 40.82.186.182, 40.82.186.182, 40.91.74.37, 40.91.78.105, 40.91.114.40, 40.91.114.41, 40.91.114.42, 40.91.114.43, 51.137.136.34, 51.137.137.69, 51.143.122.59, 51.143.122.60, 52.139.1.156, 52.139.1.156, 52.139.2.0, 52.139.2.0, 52.139.9.176, 52.139.9.198, 52.139.16.105, 52.139.16.105, 52.139.21.70, 52.139.21.70, 52.139.245.1, 52.139.245.21, 52.148.161.45, 52.148.161.53, 52.155.164.131, 52.155.167.231, 52.155.177.13, 52.155.178.247, 52.155.179.84, 52.155.180.208, 52.155.180.209, 52.155.180.210, 52.155.180.211, 52.155.182.138, 52.224.190.225, 52.224.191.62, 52.224.202.86, 52.224.202.91, 104.45.170.70, 104.45.170.178, 104.45.170.180, 104.45.170.183, 104.45.170.186, 104.45.170.191|\*. us3.cas.ms, \* . US3.Access-Control.cas.ms, \* . US3.SAML.cas.ms|
|EU1|20.40.106.50, 20.40.161.131, 20.40.161.132, 20.40.163.178, 20.40.163.179, 20.188.72.248, 40.67.254.233, 40.80.219.49, 40.80.220.215, 40.80.220.246, 40.80.221.77, 40.80.222.91, 40.80.222.197, 40.81.57.138, 40.81.57.141, 40.81.57.144, 40.81.57.157, 40.81.57.164, 40.81.57.169, 40.81.120.13, 40.81.120.24, 40.81.120.25, 40.81.121.76, 40.81.121.78, 40.81.122.63, 40.81.122.203, 40.119.207.164, 40.119.207.166, 40.119.207.174, 40.119.207.182, 40.119.207.193, 40.119.207.200, 51.137.137.200, 51.137.137.237, 51.145.181.195, 51.145.181.214, 52.139.251.219, 52.139.252.105, 52.148.115.188, 52.148.115.194, 52.151.244.65, 52.151.247.27, 52.153.240.107, 52.155.161.88, 52.155.161.91, 52.156.203.22, 52.156.203.199, 52.156.204.24, 52.156.204.51, 52.156.204.139, 52.156.205.137, 52.156.205.182, 52.157.218.219, 52.157.218.232, 52.157.232.147, 52.157.233.205, 52.157.234.160, 52.157.235.144, 52.157.237.107, 52.157.237.213, 52.224.201.216, 52.224.201.223, 52.249.25.160, 52.249.25.165, 104.45.168.103, 104.45.168.104, 104.45.168.106, 104.45.168.108, 104.45.168.111, 104.45.168.114|\*. eu1.cas.ms, \* . EU1.Access-Control.cas.ms, \* . EU1.SAML.cas.ms|
|EU2|20.40.134.79, 20.40.160.184, 20.40.161.142, 20.40.161.143, 20.40.163.130, 20.184.58.46, 20.184.60.77, 20.184.61.67, 40.66.57.203, 40.66.60.101, 40.66.60.220, 40.66.60.221, 40.66.60.222, 40.66.60.225, 40.66.60.232, 40.66.62.154, 40.66.62.225, 40.81.62.199, 40.81.62.206, 40.81.62.209, 40.81.62.212, 40.81.62.221, 40.81.62.222, 40.90.191.153, 40.119.145.130, 40.119.147.102, 40.119.203.98, 40.119.203.99, 40.119.203.158, 40.119.203.159, 40.119.203.208, 40.119.203.209, 51.105.164.234, 51.105.164.241, 52.142.124.23, 52.155.168.45, 52.155.181.180, 52.155.181.181, 52.155.181.182, 52.155.181.183, 52.155.182.48, 52.155.182.49, 52.155.182.50, 52.156.202.7, 52.157.233.49, 52.157.234.222, 52.157.235.27, 52.157.236.195, 52.157.237.255, 52.157.239.132, 52.190.26.220, 52.190.31.62, 52.224.188.157, 52.224.188.168, 104.45.170.127, 104.45.170.161, 104.45.170.173, 104.45.170.174, 104.45.170.175, 104.45.170.176|\*. eu2.cas.ms, \* . EU2.Access-Control.cas.ms, \* . EU2.SAML.cas.ms|

### <a name="us-government-gcc-high-customers"></a>Clients du gouvernement des États-Unis, GCC

Pour les clients des États-Unis, GCC High Customers, pour activer Cloud App Security proxy inverse, ajoutez le **port de sortie 443** pour les noms DNS suivants à la liste verte de votre pare-feu :

```ini
*.mcas-gov.us
*.admin-mcas-gov.us
mcasproxy.azureedge.net
```

## <a name="siem-agent-connection"></a>Connexion de l’agent SIEM

Pour permettre à Cloud App Security de se connecter à votre serveur SIEM, ajoutez le **port de sortie 443** pour les adresses IP suivantes à la liste verte de votre pare-feu :

|Centre de données|Adresses IP|
|----|----|
|US1|13.64.26.88, 13.64.29.32, 13.80.125.22, 13.91.91.243, 40.74.1.235, 40.74.6.204, 51.143.58.207, 52.137.89.147, 52.183.75.62|
|US2|13.80.125.22, 20.36.222.59, 20.36.222.60, 40.74.1.235, 40.74.6.204, 51.143.58.207, 52.137.89.147, 52.183.75.62, 52.184.165.82|
|US3|13.80.125.22, 40.74.1.235, 40.74.6.204, 40.90.218.196, 40.90.218.198, 51.143.58.207, 52.137.89.147, 52.183.75.62|
|EU1|13.80.125.22, 40.74.1.235, 40.74.6.204, 40.119.154.72, 51.143.58.207, 52.137.89.147, 52.157.238.58, 52.174.56.180, 52.183.75.62|
|EU2|13.80.125.22, 40.74.1.235, 40.74.6.204, 40.81.156.154, 40.81.156.156, 51.143.58.207, 52.137.89.147, 52.183.75.62|
|Gov US1|13.72.19.4, 52.227.143.223|

> [!NOTE]
> Si vous n’avez pas spécifié de proxy lors de la configuration de l’agent SIEM Cloud App Security, vous devez autoriser les connexions http sur le port 80 pour les URL listées dans la page [modifications du certificat TLS Azure](/azure/security/fundamentals/tls-certificate-changes#will-this-change-affect-me) . Il est utilisé pour vérifier l’état de révocation du certificat lorsque vous vous connectez au portail Cloud App Security.

## <a name="app-connector"></a>Connecteur d’applications

Pour que certaines applications tierces soient accessibles par Cloud App Security, ces adresses IP peuvent être utilisées. Les adresses IP permettent à Cloud App Security de collecter les journaux et de fournir un accès pour la console Cloud App Security.

> [!NOTE]
> Vous verrez peut-être ces adresses IP dans les journaux d’activité du fournisseur, car Cloud App Security effectue des actions de gouvernance et des analyses à partir de ces adresses IP.

Pour se connecter à des applications tierces, autorisez Cloud App Security à se connecter à partir de ces adresses IP :

|Centre de données|Adresses IP|
|----|----|----|
|US1|13.64.26.88, 13.64.29.32, 13.64.30.76, 13.64.30.117, 13.64.30.118, 13.64.31.116, 13.64.196.27, 13.64.198.19, 13.64.198.97, 13.64.199.41, 13.68.76.47, 13.86.176.189, 13.86.176.211, 13.91.61.249, 13.91.91.243, 13.91.98.185, 13.93.216.68, 13.93.233.42, 40.118.211.172, 104.42.54.148, 104.209.35.177|
|US2|13.68.76.47, 20.36.222.59, 20.36.222.60, 40.67.152.91, 40.67.154.160, 40.67.155.146, 40.67.159.55, 40.84.2.83, 40.84.4.93, 40.84.4.119, 52.184.165.82, 52.232.224.227, 52.232.225.84, 104.42.54.148, 104.46.116.211, 104.46.116.211, 104.46.121.72, 104.46.121.72, 104.46.122.189, 104.46.122.189|
|US3|13.68.76.47, 40.90.218.196, 40.90.218.197, 40.90.218.198, 40.90.218.203, 40.90.220.190, 40.90.220.196, 51.143.120.236, 51.143.120.242, 104.42.54.148|
|EU1|13.80.22.71, 13.95.29.177, 13.95.30.46, 40.67.219.133, 40.114.217.8, 40.114.217.8, 40.115.24.65, 40.115.24.65, 40.115.25.50, 40.115.25.50, 40.119.154.72, 51.105.55.62, 51.105.179.157, 51.137.200.32, 52.157.232.110, 52.157.233.92, 52.157.233.133, 52.157.238.58, 52.157.239.110, 52.174.56.180|
|EU2|40.81.152.171, 40.81.152.172, 40.81.156.153, 40.81.156.154, 40.81.156.155, 40.81.156.156, 51.105.55.62, 51.137.200.32, 51.145.108.227, 51.145.108.250|
|Gov US1|52.227.138.248, 52.227.142.192, 52.227.143.223|

## <a name="third-party-dlp-integration"></a>Intégration de solutions DLP tierces

Pour que Cloud App Security puisse envoyer des données via votre stunnel à votre serveur ICAP, ouvrez votre pare-feu DMZ à ces adresses IP avec un numéro de port source dynamique.

1. **Adresses sources** : ces adresses doivent être autorisées comme indiqué ci-dessus pour les applications tierces du connecteur d’API
2. **Port TCP source** : dynamique
3. **Adresse(s) de destination** : une ou deux adresses IP du stunnel connecté au serveur ICAP externe
4. **Port TCP de destination** : comme défini dans votre réseau

> [!NOTE]
>
> - Par défaut, le numéro de port du stunnel a la valeur 11344. Vous pouvez le remplacer par un autre port si nécessaire, mais n’oubliez pas de noter le nouveau numéro de port.
> - Vous verrez peut-être ces adresses IP dans les journaux d’activité du fournisseur, car Cloud App Security effectue des actions de gouvernance et des analyses à partir de ces adresses IP.

Pour se connecter à des applications tierces et s’intégrer à des solutions DLP externes, autorisez Cloud App Security à se connecter à partir de ces adresses IP :

|Centre de données|Adresses IP|
|----|----|----|
|US1|13.64.26.88, 13.64.29.32, 13.64.30.76, 13.64.30.117, 13.64.30.118, 13.64.31.116, 13.64.196.27, 13.64.198.19, 13.64.198.97, 13.64.199.41, 13.86.176.189, 13.86.176.211, 13.91.61.249, 13.91.91.243, 13.91.98.185, 13.93.216.68, 13.93.233.42, 40.118.211.172, 104.209.35.177|
|US2|20.36.222.59, 20.36.222.60, 40.67.152.91, 40.67.154.160, 40.67.155.146, 40.67.159.55, 40.84.2.83, 40.84.4.93, 40.84.4.119, 52.184.165.82, 52.232.224.227, 52.232.225.84, 104.46.116.211, 104.46.116.211, 104.46.121.72, 104.46.121.72, 104.46.122.189, 104.46.122.189|
|US3|40.90.218.196, 40.90.218.197, 40.90.218.198, 40.90.218.203, 40.90.220.190, 40.90.220.196, 51.143.120.236, 51.143.120.242|
|EU1|13.80.22.71, 13.95.29.177, 13.95.30.46, 40.67.219.133, 40.114.217.8, 40.114.217.8, 40.115.24.65, 40.115.24.65, 40.115.25.50, 40.119.154.72, 51.105.179.157, 52.157.232.110, 52.157.233.92, 52.157.233.133, 52.157.238.58, 52.157.239.110, 52.174.56.180|
|EU2|40.81.152.171, 40.81.152.172, 40.81.156.153, 40.81.156.154, 40.81.156.155, 40.81.156.156, 51.145.108.227, 51.145.108.250|

## <a name="mail-server"></a>Serveur de messagerie

Pour permettre l’envoi de notifications à partir du modèle et des paramètres par défaut, ajoutez ces adresses IP à votre liste d’autorisation anti-spam. Les adresses IP de courrier dédiées à Cloud App Security sont les suivantes :

- 65.55.234.192/26
- 207.46.50.192/26
- 65.55.52.224/27
- 94.245.112.0/27
- 111.221.26.0/27
- 207.46.200.0/27

Si vous souhaitez personnaliser l’identité de l’expéditeur du courrier électronique, Microsoft Cloud App Security active la personnalisation à l’aide de MailChimp &reg; , un service de messagerie tiers. Pour cela, dans le portail Microsoft Cloud App Security, accédez à **Paramètres**. Sélectionnez **paramètres de messagerie** et passez en revue les conditions d’entretien et la déclaration de confidentialité de MailChimp. Ensuite, autorisez Microsoft à utiliser MailChimp en votre nom.

Si vous ne personnalisez pas l’identité de l’expéditeur, vos notifications par courrier électronique sont envoyées à l’aide de tous les paramètres par défaut.

Pour utiliser MailChimp, ajoutez cette adresse IP à votre liste d’autorisation anti-spam pour permettre l’envoi de notifications : 198.2.134.139 (mail1.cloudappsecurity.com)

## <a name="log-collector"></a>Collecteur de journaux

Pour activer les fonctionnalités Cloud Discovery à l’aide d’un collecteur de journaux et détecter l’informatique fantôme dans votre organisation, ouvrez les éléments suivants :

- Autorisez le collecteur de journaux à recevoir le trafic FTP et Syslog entrant.
- Autorisez le collecteur de journaux à lancer le trafic sortant sur le portail (par exemple, contoso.cloudappsecurity.com) sur le port 443.
- Autorisez le collecteur de journaux à initier le trafic sortant vers le stockage Blob Azure sur le port 443 :

  | Centre de données |                        URL                                 |
  |-------------|------------------------------------------------------------|
  |     US1     | https : \/ /adaprodconsole.blob.Core.Windows.net/             |
  |     US2     | https : \/ /prod03use2console1.blob.Core.Windows.net/         |
  |     US3     | https : \/ /prod5usw2console1.blob.Core.Windows.net/          |
  |     EU1     | https : \/ /prod02euwconsole1.blob.Core.Windows.net/          |
  |     EU2     | https : \/ /prod4uksconsole1.blob.Core.Windows.net/           |
  |   Gov US1   | https : \/ /gprd1usgvconsole1.blob.Core.usgovcloudapi.net/    |

> [!NOTE]
>
> - Si votre pare-feu nécessite une liste d’accès à une adresse IP statique et ne prend pas en charge l’autorisation basée sur l’URL, autorisez le collecteur de journaux à initier le trafic sortant vers les [plages IP du centre de Microsoft Azure Datacenter](https://www.microsoft.com/download/details.aspx?id=56519) sur le port 443.
> - Autorisez le collecteur de journaux à diriger le trafic sortant vers le portail Cloud App Security.
> - Si vous n’avez pas spécifié de proxy lors de la configuration du collecteur de journaux, vous devez autoriser les connexions http sur le port 80 pour les URL listées dans la page [modifications du certificat TLS Azure](/azure/security/fundamentals/tls-certificate-changes#will-this-change-affect-me) . Il est utilisé pour vérifier l’état de révocation du certificat lorsque vous vous connectez au portail Cloud App Security.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
