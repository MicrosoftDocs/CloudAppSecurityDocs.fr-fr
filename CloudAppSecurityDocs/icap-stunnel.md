---
title: "Intégration DLP externe de Cloud App Security sur ICAP sécurisé | Microsoft Docs"
description: "Cette rubrique décrit les étapes nécessaires pour configurer la connexion ICAP dans Cloud App Security ainsi qu’un stunnel."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/23/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 9656f6c6-7dd4-4c4c-a0eb-f22afce78071
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: b3c9181bf1d56fe515d3e1356d38d631fee2cac5
ms.sourcegitcommit: c6f917ed0fc2329a72b1e5cbb8ccd5e4832c8695
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2017
---
# <a name="external-dlp-integration"></a>Intégration DLP externe

> [!NOTE] 
> Cette fonctionnalité est en préversion. Veuillez contacter <Cloud App Securitypreview@microsoft.com> pour essayer cette fonctionnalité dans votre client.

Cloud App Security peut s’intégrer à des solutions DLP existantes pour étendre ces contrôles au cloud tout en conservant une stratégie cohérente et unifiée pour les activités locales et dans le cloud. La plateforme exporte des interfaces faciles à utiliser, notamment l’API REST et ICAP, qui permettent d’intégrer des systèmes de classification du contenu comme Symantec Data Loss Prevention (anciennement Vontu Data Loss Prevention) ou Forcepoint DLP. 

L’intégration s’effectue en utilisant le protocole ICAP standard, un protocole de type http décrit dans [RFC 3507](https://tools.ietf.org/html/rfc3507). Afin de sécuriser le protocole ICAP pour la transmission de vos données, vous devez configurer un tunnel SSL sécurisé (stunnel) entre votre solution DLP et Cloud App Security. La configuration d’un stunnel fournit des fonctionnalités de chiffrement TLS à vos données pendant leur transit entre votre serveur DLP et Cloud App Security. 

Ce guide décrit les étapes nécessaires pour configurer la connexion ICAP dans Cloud App Security ainsi que le stunnel qui permet de sécuriser la communication.

## <a name="architecture"></a>Architecture
Cloud App Security analyse votre environnement cloud et décide en fonction de la configuration de votre stratégie de fichier s’il faut analyser le fichier à l’aide du moteur DLP interne ou externe. Si l’analyse DLP externe est appliquée, le fichier est envoyé via le tunnel sécurisé de l’environnement client dans lequel il est relayé à l’appliance ICAP pour connaître le verdict DLP : autorisé/bloqué. Les réponses sont renvoyées à Cloud App Security via le stunnel où elles sont utilisées par la stratégie pour déterminer les actions suivantes comme les notifications, la mise en quarantaine et le contrôle de partage.

![Architecture du stunnel](./media/icap-architecture-stunnel.png)

Comme Cloud App Security s’exécute dans Azure, un déploiement dans Azure améliore les performances. Toutefois, d’autres options, notamment le déploiement sur d’autres clouds et emplacements locaux sont pris en charge. Le déploiement dans d’autres environnements peut entraîner une dégradation des performances à cause d’une latence plus élevée et de la réduction du débit. Le serveur ICAP et le stunnel doivent être déployés simultanément sur le même réseau pour assurer que le trafic est chiffré.

## <a name="prerequisites"></a>Conditions préalables
Pour que Cloud App Security envoie des données via votre stunnel à votre serveur ICAP, ouvrez le pare-feu DMZ aux adresses IP externes utilisées par Cloud App Security avec un numéro de port source dynamique. 

1.  Adresses sources : consultez [Connecter des applications, sous Prérequis](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md#prerequisites)
2.  Port TCP source : dynamique
3.  Adresse(s) de destination : une ou deux adresse IP du stunnel connecté au serveur ICAP externe que vous configurez dans les étapes suivantes
4.  Port TCP de destination : comme défini dans votre réseau

## <a name="step-1--set-up-icap-server"></a>ÉTAPE 1 : Configurer le serveur ICAP

Configurez un serveur ICAP, en notant le numéro de port et en vérifiant que vous définissez le **Mode** sur **Blocage**. Le mode blocage définit le serveur ICAP pour qu’il relaie le verdict de classification vers Cloud App Security.

Consultez la documentation de votre produit DLP externe pour obtenir des instructions sur la façon d’y parvenir. Par exemple, consultez [Annexe A : Configuration du serveur ICAP Forcepoint](#forcepoint).

## <a name="step-2--set-up-your-stunnel-server"></a>ÉTAPE 2 : Configurer votre serveur stunnel 

Dans cette étape, vous configurez le stunnel connecté à votre serveur ICAP. 

>[!NOTE]
> Cette étape, bien que fortement recommandée, est facultative et peut être ignorée pour les charges de travail de test. 

### <a name="install-stunnel-on-a-server"></a>Installer le stunnel sur un serveur

**Prérequis**

- **Un serveur**, Windows Server ou serveur Linux basé sur une distribution majeure.

Consultez le [site web du stunnel](https://www.stunnel.org/index.html) pour plus d’informations sur les types de serveurs qui prennent en charge l’installation d’un stunnel. Si vous utilisez Linux, vous pouvez utiliser le gestionnaire de distribution Linux pour l’installer.

#### <a name="install-stunnel-on-windows"></a>Installer le stunnel sur Windows

1. [Téléchargez la dernière installation pour Windows Server](https://www.stunnel.org/downloads.html) (doit fonctionner sur n’importe quelle édition récente de Windows Server).
(installation par défaut)

2. Pendant l’installation, ne créez pas de certificat auto-signé, vous en créez un dans une étape ultérieure.

3. Cliquez sur **Démarrer le serveur après l’installation**.

4. Créez un certificat de l’une des façons suivantes :

   -    Utilisez votre serveur de gestion de certificats pour créer un certificat SSL sur votre serveur ICAP, puis copiez les clés sur le serveur que vous avez préparé pour l’installation du stunnel.
   -    Sinon, sur le serveur stunnel, utilisez les commandes OpenSSL suivantes pour générer une clé privée et un certificat auto-signé. Remplacez ces variables :
       -    **key.pem** par le nom de votre clé privée
       -    **cert.pem** par le nom de votre certificat
       -    **stunnel-key** par le nom de la clé récemment créée

5. Dans le chemin d’installation de votre stunnel, ouvrez le répertoire de configuration. La valeur par défaut est : c:\Program Files (x86) \stunnel\config\
6. Exécutez la ligne de commande avec des autorisations d’administrateur : `..\bin\openssl.exe genrsa -out ey.pem 2048 `
      
     ` ..\bin\openssl.exe  req -new -x509 -config ".\openssl.cnf" -key key.pem -out .\cert.pem -days 1095`

8. Concaténez les variables cert.pem et key.pem et enregistrez-les dans le fichier : `type cert.pem key.pem >> stunnel-key.pem`

9. [Téléchargez la clé publique](https://adaprodconsole.blob.core.windows.net/icap/publicCert.pem) et enregistrez-la à cet emplacement **C:\Program Files (x86)\stunnel\config\CAfile.pem**.

10. Ajoutez les règles suivantes pour ouvrir le port dans le pare-feu Windows :

        rem Open TCP Port 11344 inbound and outbound
        netsh advfirewall firewall add rule name="Secure ICAP TCP Port 11344" dir=in action=allow protocol=TCP localport=11344
        netsh advfirewall firewall add rule name="Secure ICAP TCP Port 11344" dir=out action=allow protocol=TCP localport=11344

11. Exécutez `c:\Program Files (x86)\stunnel\bin\stunnel.exe` pour ouvrir l’application de stunnel. 

12. Cliquez sur **Configuration**, puis **Modifier la configuration**.

   ![Modifier la configuration de Windows Server](./media/stunnel-windows.png)
 
13. Ouvrez le fichier et collez les lignes de configuration de serveur suivantes, où **Adresse IP du serveur DLP** désigne l’adresse IP de votre serveur ICAP, **stunnel-key** est la clé que vous avez créée à l’étape précédente et **CAfile** est le certificat public du client stunnel de Cloud App Security. Par ailleurs, supprimez le texte d’exemple (l’exemple affiche le texte Gmail) et copiez le texte suivant dans le fichier :

        [microsoft-Cloud App Security]
        accept = 0.0.0.0:11344
        connect = **ICAP Server IP**:1344
        cert = C:\Program Files (x86)\stunnel\config\**stunnel-key**.pem
        CAfile = C:\Program Files (x86)\stunnel\config\**CAfile**.pem
        TIMEOUTclose = 0
        client = no
12. Enregistrez le fichier, puis cliquez sur **Recharger la configuration**.

13. Pour vérifier que tout s’exécute comme prévu, à partir d’une invite de commandes, exécutez `netstat -nao  | findstr 11344`
 

#### <a name="install-stunnel-on-ubuntu"></a>Installer le stunnel sur Ubuntu

L’exemple suivant est basé sur l’installation d’un serveur Ubuntu avec une connexion en tant qu’utilisateur racine. Pour les autres serveurs, utilisez des commandes parallèles. 

Sur le serveur préparé, téléchargez et installez la dernière version de stunnel en exécutant la commande suivante sur votre serveur Ubuntu qui va installer stunnel et OpenSSL :

    apt-get update
    apt-get install openssl -y
    apt-get install stunnel4 -y
Vérifiez que stunnel est installé en exécutant la commande suivante à partir d’une console. Vous devez obtenir le numéro de version et une liste des options de configuration :

    stunnel-version

### <a name="generate-certificates"></a>Générer les certificats

Le serveur ICAP et Cloud App Security utilisent une clé privée et un certificat public pour l’authentification et le chiffrement du serveur dans le stunnel. Vérifiez que vous créez la clé privée sans phrase secrète pour que le stunnel puisse s’exécuter comme un service en arrière-plan. Par ailleurs, définissez l’autorisation des fichiers sur **lisible** pour le propriétaire du stunnel et sur **aucune** pour tous les autres utilisateurs.

Vous pouvez créer les certificats de l’une des façons suivantes :
-   Utilisez votre serveur de gestion de certificats pour créer un certificat SSL sur votre serveur ICAP, puis copiez les clés sur le serveur que vous avez préparé pour l’installation du stunnel. 
-   Sinon, sur le serveur stunnel, utilisez les commandes OpenSSL suivantes pour générer une clé privée et un certificat auto-signé. Remplacez ces variables :
    - **« key.pem »** par le nom de votre clé privée
    - **« cert.pem »** par le nom de votre certificat
    - **« stunnel-key »** par le nom de la clé récemment créée
       
            openssl genrsa -out key.pem 2048
            openssl req -new -x509 -key key.pem -out cert.pem -days 1095
            cat key.pem cert.pem >> /etc/ssl/private/stunnel-key.pem

### <a name="download-the-cloud-app-security-stunnel-client-public-key"></a>Télécharger la clé publique du client stunnel de Cloud App Security

Téléchargez la clé publique à partir de cet emplacement : https://adaprodconsole.blob.core.windows.net/icap/publicCert.pem et enregistrez-la à cet emplacement : **/etc/ssl/certs/CAfile.pem**

### <a name="configure-stunnel"></a>Configurer le stunnel 

La configuration du stunnel est définie dans le fichier stunnel.conf.

1. Créez le fichier stunnel.conf dans le répertoire suivant : **vim /etc/stunnel/stunnel.conf**

3.  Ouvrez le fichier et collez les lignes de configuration de serveur suivantes, où **Adresse IP du serveur DLP** désigne l’adresse IP de votre serveur ICAP, **stunnel-key** est la clé que vous avez créée à l’étape précédente et **CAfile** est le certificat public du client stunnel de Cloud App Security :

        [microsoft-Cloud App Security]
        accept = 0.0.0.0:11344
        connect = **ICAP Server IP**:1344
        cert = /etc/ssl/private/**stunnel-key**.pem
        CAfile = /etc/ssl/certs/**CAfile**.pem
        TIMEOUTclose = 1
        client = no
> [!NOTE] 
> Par défaut, le numéro de port du stunnel a la valeur 11344. Vous pouvez le remplacer par un autre port si nécessaire, mais n’oubliez pas de noter le nouveau numéro de port, vous en aurez besoin à l’étape suivante.

### <a name="update-your-ip-table"></a>Mettre à jour votre table d’adresses IP
Mettez à jour votre table d’adresses IP avec la règle de routage suivante :
   
    iptables -I INPUT -p tcp --dport 11344 -j ACCEPT

Pour mettre à jour votre table d’adresses IP persistante, utilisez les commandes suivantes :

     sudo apt-get install iptables-persistent
     sudo /sbin/iptables-save > /etc/iptables/rules.v4
 

### <a name="run-stunnel"></a>Exécuter le stunnel
1.  Sur votre serveur stunnel, exécutez la commande suivante :

        vim /etc/default/stunnel4

2.  Remplacez la variable ENABLED par 1 :

        ENABLED=1

3.  Redémarrez le service pour que la configuration prenne effet :

        /etc/init.d/stunnel4 restart

4.  Exécutez les commandes suivantes pour vérifier que le stunnel s’exécute correctement :

        ps -A | grep stunnel

    et qu’il écoute sur le port spécifié :

        netstat -anp | grep 11344

5. Vérifiez que le réseau dans lequel le serveur stunnel a été déployé correspond aux prérequis de réseau comme indiqué précédemment. Cela est indispensable pour permettre aux connexions entrantes de Cloud App Security d’accéder correctement au serveur.

Si le processus n’est toujours pas en cours d’exécution, consultez la [documentation de stunnel](https://www.stunnel.org/docs.html) pour résoudre les problèmes.


## <a name="step-3--connect-to-cloud-app-security"></a>ÉTAPE 3 : Se connecter à Cloud App Security

1. Dans Cloud App Security, sous **Paramètres**, sélectionnez **Extensions de sécurité**, puis l’onglet **DLP externe**.

2. Cliquez sur le signe plus pour ajouter une nouvelle connexion. 

3. Dans l’Assistant **Ajouter une nouvelle DLP externe**, indiquez un **Nom de connexion** (par exemple, My Forcepoint connector) qui est utilisé pour identifier le connecteur.

4. Sélectionnez le **Type de connexion** :
    - **Symantec Vontu** : Sélectionnez cette option pour utiliser l’intégration personnalisée des appliances DLP Vontu
    - **DLP Forcepoint** : Sélectionnez cette option pour utiliser l’intégration personnalisée des appliances DLP Forcepoint
    - **ICAP générique – REQMOD** : Pour les autres appliances DLP qui utilisent [Modification de la demande](https://tools.ietf.org/html/rfc3507)
    - **ICAP générique – RESPMOD** : Pour les autres appliances DLP qui utilisent [Modification de la réponse](https://tools.ietf.org/html/rfc3507)
    ![Connexion ICAP de Cloud App Security](./media/icap-wizard1.png)

4. Recherchez l’autorité de certification racine publique de votre stunnel qui vous permet de vous connecter à votre stunnel, puis cliquez sur **Suivant**.

   > [!NOTE]
   > Il est vivement recommandé de cocher la case **Utiliser ICAP sécurisé** pour configurer une passerelle stunnel chiffrée. Si vous n’avez pas de serveur stunnel ou que vous effectuez des tests, vous pouvez décocher cette option pour une intégration directe à votre serveur DLP. 

5. Dans l’écran **Configuration du serveur**, indiquez **l’Adresse IP** et le **Port** du serveur stunnel que vous avez configuré à l’étape 2. Pour des raisons d’équilibrage de charge, vous pouvez configurer **l’Adresse IP** et le **Port** d’un serveur supplémentaire. Les adresses IP fournies doivent être les adresses IP statiques externes de vos serveurs.

   ![Connexion ICAP de Cloud App Security](./media/icap-wizard2.png)
6. Cliquez sur **Suivant**. Cloud App Security teste la connectivité au serveur que vous avez configuré. Si vous recevez une erreur, passez en revue les instructions et les paramètres réseau. Une fois connecté, vous pouvez cliquer sur **Quitter**.

7. Ensuite, pour diriger le trafic sur ce serveur DLP externe, quand vous créez une **Stratégie de fichier**, sous **Méthode d’inspection du contenu**, sélectionnez la connexion que vous venez de créer. En savoir plus sur la [création d’une stratégie de fichier](data-protection-policies.md).


## Annexe A : Configuration du serveur ICAP Forcepoint<a name="forcepoint"></a>

Dans ForcePoint, définissez votre appliance en suivant ces étapes :

1.  Dans votre appliance DLP, accédez à **Déploiement** > **Modules système**. 

    ![Déploiement ICAP](./media/icap-system-modules.png)

2.  Sous l’onglet **Général**, vérifiez que **Serveur ICAP** est **activé** et que le **Port** par défaut a la valeur **1344**. Par ailleurs, sous **Autoriser la connexion à ce serveur ICAP à partir des adresses IP suivantes**, sélectionnez **Toute adresse IP**.
 
    ![Configuration ICAP](./media/icap-ip-address.png)

3.  Sous l’onglet HTTP/HTTPS, définissez **Mode** sur **Blocage**.
 
    ![Blocage ICAP](./media/icap-blocking.png)
 

## <a name="appendix-b-symantec-deployment-guide"></a>Annexe B : Guide de déploiement de Symantec

Les versions Symantec DLP prises en charge sont 11-14.6. Comme indiqué ci-dessus, vous devez déployer un serveur de détection dans le même centre de données Azure que celui où se trouve votre client Cloud App Security. Le serveur de détection se synchronise avec le serveur d’application via un tunnel IPSec dédié. 
 
### <a name="detection-server-installation"></a>Installation du serveur de détection 
Le serveur de détection utilisé par Cloud App Security est un serveur Network Prevent for Web standard. Plusieurs options de la configuration doivent être modifiées :
1.  Désactivez le **Mode d’évaluation** :
    1. Sous **Système** > **Serveurs et détecteurs**, cliquez sur la cible ICAP. 
    
      ![Cible ICAP](./media/icap-target.png)
    
    2. Cliquez sur **Configurer**. 
    
      ![Configurer la cible ICAP](./media/configure-icap-target.png)
    
    3. Désactivez le **Mode d’évaluation**.
    
      ![désactiver le mode d’évaluation](./media/icap-disable-trial-mode.png)
    
2. Sous **ICAP** > **Filtrage de réponse**, définissez la valeur de l’option **Ignorer les réponses inférieures à** sur 1.

3. Et ajoutez « application/* » à la liste **Inspecter le type de contenu**.
     ![inspecter le type de contenu](./media/icap-inspect-content-type.png)
4. Cliquez sur **Enregistrer**.


### <a name="policy-configuration"></a>Configuration de la stratégie
Cloud App Security prend parfaitement en charge tous les types de règle de détection inclus avec Symantec DLP, il est donc inutile de modifier les règles existantes. Toutefois, il existe une modification de configuration qui doit être appliquée à toutes les stratégies existantes et nouvelles pour activer l’intégration complète. Cette modification correspond à l’ajout d’une règle de réponse spécifique pour toutes les stratégies. Ajoutez la modification de configuration à Vontu :
1.  Accédez à **Gérer** > **Stratégies** > **Règles de réponse** et cliquez sur **Ajouter une règle de réponse**.
    
    ![ajouter une règle de réponse](./media/icap-add-response-rule.png)

2.  Vérifiez que l’option **Réponse automatique** est sélectionnée et cliquez sur **Suivant**.

    ![réponse automatique](./media/icap-automated-response.png)

3. Tapez un nom pour la règle, par exemple, **Bloquer HTTP/HTTPS**. Sous **Actions** sélectionnez **Bloquer HTTP/HTTPS** et cliquez sur **Enregistrer**.

    ![bloquer http](./media/icap-block-http.png)

Ajoutez la règle que vous avez créée à des stratégies existantes :
1. Dans chaque stratégie, accédez à l’onglet **Réponse**.
2. Dans la liste déroulante **Règle de réponse**, sélectionnez la règle de réponse de blocage que vous avez créée ci-dessus.
3. Enregistrez la stratégie.
   
    ![désactiver le mode d’évaluation](./media/icap-add-policy.png)

Cette règle doit être ajoutée à toutes les stratégies existantes.



