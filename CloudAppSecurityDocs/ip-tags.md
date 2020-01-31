---
title: Définir des plages d’adresses IP et des balises - Cloud App Security | Microsoft Docs
description: Cet article fournit des instructions sur l’utilisation des balises et des catégories d’adresses IP.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/16/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: fbea8df8a5fb16fabde89a48d8ac8227fb37a1c5
ms.sourcegitcommit: f81dd93841d7e5d01a1edaaf464c8656c4e7efda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76814231"
---
#  <a name="IPtagsandRanges"></a> Utilisation des balises et des plages d’adresses IP

*S’applique à : Microsoft Cloud App Security*

Pour identifier facilement les adresses IP connues, telles que celles de votre bureau, vous devez définir des plages d’adresses IP. Les plages d’adresses IP vous permettent de baliser, classer et personnaliser la façon dont les journaux et les alertes sont affichés et examinés. Chaque groupe de plages IP peut être classé selon une liste prédéfinie de catégories d’adresses IP. Vous pouvez également créer des balises IP personnalisées pour vos plages d’adresses IP. En outre, vous pouvez remplacer les informations de géolocalisation publiques en fonction de votre connaissance du réseau interne. IPv4 et IPv6 sont pris en charge.

Cloud App Security est préconfiguré avec des plages d’adresses IP intégrées pour les fournisseurs de cloud répandus comme Azure et Office 365. De plus, nous avons des balises intégrées basées sur Microsoft Threat Intelligence, notamment pour le proxy anonyme, Botnet et Tor. Vous pouvez voir la liste complète dans la liste déroulante de la page des plages d’adresses IP.

> [!NOTE]
>
> - Pour utiliser ces balises intégrées dans le cadre d’une recherche, reportez-vous à leur ID dans la documentation des API Cloud App Security.
> - Vous pouvez ajouter des plages d’adresses IP en bloc en créant un script à l’aide de l’**API des plages d’adresses IP**.
> - Vous ne pouvez pas ajouter de plages IP avec des adresses IP qui se chevauchent.
> - Pour afficher la documentation de l’API, dans la barre de menus du portail Cloud App Security, cliquez sur le point d’interrogation puis sur **Documentation sur les API**.

Les balises d’adresse IP intégrées et les balises IP personnalisées sont considérées de manière hiérarchique. Les balises IP personnalisées sont prioritaires par rapport aux balises IP intégrées. Par exemple, si une adresse IP est marquée comme étant **Risquée** en fonction de l’intelligence des menaces, mais qu’il existe une balise IP personnalisée qui l’identifie comme appartenant à l’**Entreprise**, les balises et la catégorie personnalisées sont prioritaires.

>[!NOTE]
> Lorsqu’une adresse IP est marquée comme une adresse d’entreprise, elle est indiquée dans le portail, et les adresses IP sont exclues du déclenchement de détections spécifiques (par exemple, un déplacement impossible), car ces adresses IP sont considérées comme approuvées.
>

## <a name="create-an-ip-address-range"></a>Créer une plage d’adresses IP

Dans la barre de menus, cliquez sur l’icône des paramètres. Sélectionnez **Plage d’adresses IP**. Cliquez sur le signe + pour ajouter des plages d’adresses IP et définissez les champs suivants :

1. Affectez un **Nom** à votre plage IP. Le nom n’apparaît pas dans le journal des activités ; il sert uniquement à gérer votre plage IP.

    Pour inclure la plage IP dans une catégorie d’adresses IP, sélectionnez une catégorie dans le menu déroulant.

2. Entrez la **plage d’adresses IP** que vous souhaitez configurer, puis cliquez sur le bouton « + ». Vous pouvez ajouter autant d’adresses et de sous-réseaux IP que vous le souhaitez en utilisant la notation de préfixe réseau (également appelée notation CIDR), par exemple 192.168.1.0/32.

3. Les **catégories** permettent d’identifier facilement les activités liées aux adresses IP intéressantes. Les catégories sont disponibles dans le portail. Toutefois, elles nécessitent généralement une configuration de la part de l’utilisateur afin de déterminer quelles adresses IP sont incluses dans chaque catégorie. L’exception à cette configuration est la catégorie « Risqué », qui comprend deux balises IP : proxy anonyme et Tor.

    Les catégories IP suivantes sont disponibles :

    - **Administratif** : toutes les adresses IP de vos administrateurs.

    - **Fournisseur de cloud** : adresses IP utilisées par votre fournisseur de cloud.

    - **Entreprise** : toutes les adresses IP de votre réseau interne, de vos succursales et de vos adresses d’itinérance Wi-Fi.

    - **Risqué** : toutes les adresses IP que vous considérez comme risquées. Celles-ci peuvent inclure les adresses IP suspectes déjà constatées, les adresses IP appartenant aux réseaux de vos concurrents, et ainsi de suite.

    - **VPN** : toutes les adresses IP que vous utilisez pour les télétravailleurs.

4. Pour **baliser** les activités liées à ces adresses IP, entrez une balise. Il suffit d’entrer un mot dans la zone pour créer la balise. Une fois la balise configurée, vous pouvez l’ajouter facilement à des plages IP supplémentaires en la sélectionnant dans la liste. Vous pouvez ajouter autant de balises IP que vous le souhaitez pour chaque plage. Vous pouvez utiliser des balises IP quand vous créez des stratégies.  En plus des balises IP que vous configurez, Cloud App Security a des balises intégrées qui ne sont pas configurables. Vous pouvez voir la liste des balises sous le [filtre de balises IP](activity-filters.md).
    > [!NOTE]
    > - L’emplacement et l’ISP enregistré remplacent les valeurs par défaut.
    > - Les balises IP sont ajoutées à l’activité sans remplacer les données.

5. Dans les champs qui permettent de **remplacer l’emplacement** ou l’ISP de l’organisation associés à ces adresses, entrez la nouvelle valeur. Par exemple, supposez que vous avez une adresse IP considérée comme publique en Irlande. Toutefois, vous savez que cette adresse IP est aux États-Unis. Vous allez remplacer l’emplacement de cette plage d’adresses IP.

6. Entrez un **ISP enregistré**. Ce paramètre remplace les données dans vos activités.

7. Quand vous avez terminé, cliquez sur **Créer**.

    ![plage plage](media/newipaddress-range.png "plage de nouvelles adresses IP")

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Configurer Cloud Discovery](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]
