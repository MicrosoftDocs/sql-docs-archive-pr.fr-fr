---
title: Modifier un élément dans une cellule (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 91a54778-8929-41f9-bb4c-826cec636be4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 80ef171713e6505867e00e343ce17b70cab9045a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710196"
---
# <a name="change-an-item-within-a-cell-report-builder-and-ssrs"></a>Modifier un élément dans une cellule (Générateur de rapports et SSRS)
  Seuls les éléments non-conteneurs, tels que les zones de texte, les lignes ou les images, peuvent être remplacés par un nouvel élément de rapport. Par exemple, vous pouvez faire glisser une table dans une zone de texte pour remplacer la zone de texte par une table.  
  
 Si une cellule contient un élément conteneur comme un rectangle, une liste, un tableau ou une matrice, le nouvel élément est ajouté à l'élément conteneur au lieu de le remplacer. Pour remplacer un élément de conteneur par un nouvel élément, supprimez le conteneur. Sa suppression entraîne son remplacement par une zone de texte, que vous pouvez ensuite remplacer par un autre élément.  
  
 Par défaut, toutes les cellules d'une table, matrice ou région de données de type liste contiennent une zone de texte.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-an-item-within-a-cell"></a>Pour modifier un élément dans une cellule  
  
-   Sous l'onglet **Insérer** , dans le groupe **Régions de données** ou **Éléments de rapport** , cliquez sur l'élément à ajouter au rapport, puis sur le rapport. L'élément est ajouté au rapport.  
  
> [!NOTE]  
>  La boîte de dialogue **Propriétés de l’image** s’ouvre quand vous faites glisser un élément de rapport d’image vers une cellule, où vous pouvez définir des propriétés, telles que la source de l’image, avant que l’image ne soit ajoutée à la cellule.  
  
## <a name="see-also"></a>Voir aussi  
 [Images, zones de texte, rectangles et lignes &#40;Générateur de rapports et SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md)   
 [Listes &#40;Générateur de rapports et SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
