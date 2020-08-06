---
title: Boîte de dialogue Règles de couleur de la carte, général | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10541"
- sql12.rtp.rptdesigner.shared.mapcolorrulesgeneral.f1
ms.assetid: 14ff5fc1-4cf8-4a45-9d98-47a1bf1c52c4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0dffc6c0b31400cb4eb9cecbbada1a52f8f41443
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613822"
---
# <a name="map-color-rules-dialog-box-general"></a>Boîte de dialogue Règles de couleur de la carte, Général
  Sélectionnez **Général** dans la boîte de dialogue **Propriétés des règles de couleur** pour définir des options de couleur pour les éléments cartographiques de cette couche. Les éléments cartographiques peuvent être des polygones, des lignes ou des points. Les règles de couleur peuvent être appliquées lorsque vous avez créé une relation entre des éléments cartographiques basés sur des données spatiales et des données analytiques provenant d'un champ de dataset ou d'un champ de source de données spatiales.  
  
 Pour afficher tous les éléments cartographiques d'une couche en spécifiant un dégradé décoratif avec des couleurs primaires et secondaires différentes, utilisez la page **Remplissage** de la boîte de dialogue Propriétés des polygones de la carte. Les règles de couleur ont priorité sur les propriétés d'affichage d'une couche. Pour plus d’informations, consultez [Personnaliser des données et l’affichage d’une carte ou d’une couche &#40;Générateur de rapports et SSRS&#41;](report-design/customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs.md).  
  
## <a name="options"></a>Options  
 **Appliquer le style de modèle**  
 Sélectionnez cette option pour utiliser une couleur en fonction du thème choisi dans l'Assistant ou définie dans les propriétés de la couche de polygones, de lignes ou de points. Un thème définit des options par défaut pour la couleur, la police et les bordures de la carte. Avec cette option, aucune règle n'est appliquée pour attribuer des couleurs à chaque élément cartographique.  
  
 **Visualiser les données à l’aide de la palette de couleurs**  
 Sélectionnez cette option pour visualiser des données analytiques en utilisant des couleurs d'une palette de couleurs spécifique.  
  
 **Visualiser les données à l’aide de plages de couleurs**  
 Sélectionnez cette option pour visualiser des données analytiques en utilisant une plage de couleurs pour chaque élément cartographique. Par exemple, si vous spécifiez Rouge comme couleur de début, Jaune comme couleur intermédiaire et Vert comme couleur de fin, les valeurs de la plage inférieure sont Rouge, celles de la plage centrale sont Jaune et celles de la plage supérieure sont Vert.  
  
 **Visualiser les données à l’aide de couleurs personnalisées**  
 Sélectionnez cette option pour visualiser des données analytiques en spécifiant votre propre liste de couleurs.  
  
 **Champ de données**  
 Cette option s'affiche lorsque vous sélectionnez l'une des options **Visualiser les données** .  
  
 Dans la liste déroulante, sélectionnez le champ de données analytiques à utiliser. Selon la source de données spatiales, la liste affiche les champs de la source de données spatiales et d'un dataset de rapport ayant une relation entre les données spatiales et les données analytiques. Pour créer une telle relation, définissez les options de données dans la page Données analytiques pour la couche sélectionnée.  
  
 **Palette**  
 Tapez ou sélectionnez le nom de la palette de couleurs.  
  
 **Couleur de début**  
 Spécifiez la couleur à utiliser pour les données comprises dans la partie inférieure de la plage de données.  
  
 **Couleur intermédiaire**  
 Spécifiez la couleur à utiliser pour les données comprises dans la partie centrale de la plage de données. Sélectionnez **Aucune couleur** pour supprimer cette plage.  
  
 **Couleur de fin**  
 Spécifiez la couleur à utiliser pour les données comprises dans la partie supérieure de la plage de données.  
  
 **Ajouter**  
 Cliquez sur **Ajouter** pour spécifier vos propres couleurs pour la règle de couleur.  
  
## <a name="see-also"></a>Voir aussi  
 [Cartes &#40;Générateur de rapports et SSRS&#41;](report-design/maps-report-builder-and-ssrs.md)   
 [Modifier les légendes de carte, l’échelle de couleurs et les règles associées &#40;Générateur de rapports et SSRS&#41;](report-design/change-map-legends-color-scale-and-associated-rules-report-builder-and-ssrs.md)  
  
  
