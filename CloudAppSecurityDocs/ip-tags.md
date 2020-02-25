---
title: Définir des plages d’adresses IP et des balises-Cloud App Security | Microsoft Docs
description: Cet article fournit des instructions sur l’utilisation des balises IP et des catégories d’adresses IP.
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
ms.openlocfilehash: c26c5cea5a366220c5f8fdff030db1240a7e1a73
ms.sourcegitcommit: 9fe879ce7f07933866191724de5f108f43e3f923
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2020
ms.locfileid: "77566930"
---
#  <a name="IPtagsandRanges"></a>Utilisation des balises et des plages d’adresses IP

*S’applique à : Microsoft Cloud App Security*

Pour identifier facilement les adresses IP connues, telles que les adresses IP de votre bureau physique, vous devez définir des plages d’adresses IP. Les plages d’adresses IP vous permettent d’étiqueter, de classer et de personnaliser la façon dont les journaux et les alertes sont affichés et examinés. Chaque groupe de plages IP peut être classé selon une liste prédéfinie de catégories d’adresses IP. Vous pouvez également créer des balises d’adresse IP personnalisées pour vos plages d’adresses IP. En outre, vous pouvez remplacer les informations de géolocalisation publiques en fonction de la connaissance de votre réseau interne. IPv4 et IPv6 sont pris en charge.

Cloud App Security est préconfiguré avec des plages d’adresses IP intégrées pour les fournisseurs de Cloud populaires tels qu’Azure et Office 365. En outre, nous disposons d’un marquage intégré basé sur les informations sur les menaces de Microsoft, notamment le proxy anonyme, le botnet et les TDR. Vous pouvez voir la liste complète dans la liste déroulante de la page plages d’adresses IP.

> [!NOTE]
>
> - Pour utiliser ces balises intégrées dans le cadre d’une recherche, reportez-vous à leur ID dans la documentation de l’API Cloud App Security.
> - Vous pouvez ajouter des plages IP en bloc en créant un script à l’aide de l' **API de plages d’adresses IP**.
> - Vous ne pouvez pas ajouter de plages IP avec des adresses IP qui se chevauchent.
> - Pour afficher la documentation de l’API, dans la barre de menus Cloud App Security portail, cliquez sur le point d’interrogation, puis sur documentation de l' **API**.

Les balises d’adresse IP intégrées et les balises IP personnalisées sont considérées comme hiérarchiques. Les balises IP personnalisées sont prioritaires sur les balises IP intégrées. Par exemple, si une adresse IP est marquée comme **risquée** en fonction de l’intelligence des menaces, mais qu’il existe une balise IP personnalisée qui l’identifie en tant qu' **entreprise**, les balises et la catégorie personnalisées sont prioritaires.

>[!NOTE]
> Quand une adresse IP est marquée comme entreprise, elle est reflétée dans le portail, et les adresses IP sont exclues du déclenchement de détections spécifiques (par exemple, [voyage impossible](anomaly-detection-policy.md#impossible-travel)), car ces adresses IP sont considérées comme approuvées.

## <a name="create-an-ip-address-range"></a>Créer une plage d’adresses IP

Dans la barre de menus, cliquez sur l’icône Paramètres. Sélectionnez **plages d’adresses IP**. Cliquez sur le signe plus (+) pour ajouter des plages d’adresses IP et définir les champs suivants :

1. **Nommez** votre plage d’adresses IP. Le nom n’apparaît pas dans le journal des activités, il est utilisé uniquement pour gérer votre plage d’adresses IP.

    Pour inclure la plage d’adresses IP dans une catégorie d’adresses IP, sélectionnez une catégorie dans le menu déroulant.

2. Entrez la **plage d’adresses IP** que vous souhaitez configurer, puis cliquez sur le bouton « + ». Vous pouvez ajouter autant d’adresses IP et de sous-réseaux que vous le souhaitez à l’aide de la notation de préfixe réseau (également appelée notation CIDR), par exemple 192.168.1.0/32.

3. Les **catégories** sont utilisées pour reconnaître facilement les activités à partir d’adresses IP intéressantes. Les catégories sont disponibles dans le portail. Toutefois, ils nécessitent généralement une configuration utilisateur pour déterminer les adresses IP qui sont incluses dans chaque catégorie. L’exception à cette configuration est la catégorie « risquée », qui comprend deux balises IP : proxy anonyme et TDR.

    Les catégories d’adresses IP suivantes sont disponibles :

    - **Administration**: ces adresses IP doivent correspondre à toutes les adresses IP de vos administrateurs.

    - **Fournisseur de Cloud**: ces adresses IP doivent être les adresses IP utilisées par votre fournisseur de Cloud.

    - **Entreprise**: ces adresses IP doivent être toutes les adresses IP de votre réseau interne, de vos succursales et de vos adresses d’itinérance Wi-Fi.

    - **Risqué**: ces adresses IP doivent être toutes les adresses IP que vous considérez comme risquées. Ils peuvent inclure des adresses IP suspectes que vous avez vues dans le passé, des adresses IP dans les réseaux de vos concurrents, et ainsi de suite.

    - **VPN**: ces adresses IP doivent être toutes les adresses IP que vous utilisez pour les travailleurs à distance.

4. Pour **baliser** les activités à partir de ces adresses IP, entrez une balise. La saisie d’un mot dans la zone crée la balise. Une fois que vous avez déjà configuré une étiquette, vous pouvez l’ajouter facilement à des plages d’adresses IP supplémentaires en la sélectionnant dans la liste. Vous pouvez ajouter autant de balises IP que vous le souhaitez pour chaque plage. Les balises IP peuvent être utilisées lors de la création de stratégies.  Avec les balises IP que vous configurez, Cloud App Security contient des balises intégrées qui ne sont pas configurables. Vous pouvez voir la liste des balises sous le [filtre des balises IP](activity-filters.md).
    > [!NOTE]
    > - L’emplacement et le fournisseur de services Internet inscrits remplacent les valeurs par défaut.
    > - Les balises IP sont ajoutées à l’activité sans remplacer les données.

5. Pour **remplacer les** champs d’emplacement ou d’organisation (ISP) pour ces adresses, entrez une nouvelle valeur. Par exemple, imaginons que vous avez une adresse IP qui est considérée publiquement en Irlande. Toutefois, vous savez que l’adresse IP se trouve aux États-Unis. Vous allez remplacer l’emplacement de cette plage d’adresses IP.

6. Entrez un **fournisseur de services Internet inscrit**. Ce paramètre remplace les données dans vos activités.

7. Lorsque vous avez terminé, cliquez sur **créer**.

    ![plage plage](media/newipaddress-range.png "plage plage")

## <a name="next-steps"></a>Étapes suivantes :

> [!div class="nextstepaction"]
> [Configurer Cloud Discovery](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]
