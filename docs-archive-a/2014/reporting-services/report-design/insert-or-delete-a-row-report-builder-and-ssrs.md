---
title: Insérer ou supprimer une ligne (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b9642af3-b3ae-4f78-b0be-8f96b79fc313
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fdec24801d1fae3b95c7d75acb5a3add650d523b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707104"
---
# <a name="insert-or-delete-a-row-report-builder-and-ssrs"></a>Insérer ou supprimer une ligne (Générateur de rapports et SSRS)
  Vous pouvez ajouter ou supprimer des lignes dans une région de données de tableau matriciel. Cette région peut être une table, une matrice ou une liste. Les procédures suivantes ne s'appliquent pas aux régions de données de graphique ou de jauge.  
  
 Dans une région de données de tableau matriciel, vous pouvez ajouter des lignes associées à un groupe (à l'intérieur d'un groupe) ou non associées à un groupe (à l'extérieur d'un groupe). Une ligne qui se trouve à l'intérieur d'un groupe n'est utilisée qu'à une seule reprise pour chaque valeur de groupe unique. Par exemple, une ligne située à l'intérieur d'un groupe dont les données sont regroupées en colonnes contenant des noms de couleur n'est utilisée qu'une seule fois par nom de couleur distinct. Pour les groupes imbriqués, une ligne peut être à l'extérieur du groupe enfant mais à l'intérieur du groupe parent. Dans ce cas, la ligne est utilisée une fois pour chaque valeur unique dans le groupe parent.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-select-a-data-region-so-the-row-and-column-handles-appear"></a>Pour sélectionner une région de données de manière à afficher les poignées de ligne et de colonne  
  
-   En mode Conception, cliquez dans l'angle supérieur gauche de la région de données de tableau matriciel pour faire apparaître les poignées de colonne et de ligne au-dessus et en regard de cette région.  
  
     Pour plus d’informations sur les zones de région de données, consultez [listes &#40;générateur de rapports et SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md).  
  
### <a name="to-insert-a-row-in-a-selected-data-region"></a>Pour insérer une ligne dans une région de données sélectionnée  
  
-   Cliquez avec le bouton droit sur un handle de ligne à l’emplacement où vous souhaitez insérer une ligne, puis cliquez sur **Insérer une ligne**et sur **Au-dessus** ou **En dessous**.  
  
     \- ou -  
  
-   Cliquez avec le bouton droit sur une cellule de la région de données au niveau de laquelle vous souhaitez insérer une ligne, cliquez sur **Insérer une ligne**, puis sur **Au-dessus** ou **En dessous**.  
  
### <a name="to-delete-a-row-from-a-selected-data-region"></a>Pour supprimer une ligne d'une région de données sélectionnée  
  
-   Sélectionnez chaque ligne à supprimer, cliquez avec le bouton droit sur le handle d’une ligne sélectionnée, puis cliquez sur **Supprimer les lignes**.  
  
     \- ou -  
  
-   Cliquez avec le bouton droit sur une cellule de la région de données au niveau de laquelle vous souhaitez supprimer une ligne, puis cliquez sur **Supprimer les lignes**.  
  
### <a name="to-insert-a-row-in-a-group-in-a-selected-data-region"></a>Pour insérer une ligne dans un groupe dans une région de données sélectionnée  
  
-   Dans la zone de groupe de lignes d’une région de données de tableau matriciel, cliquez avec le bouton droit sur une cellule de groupe de lignes au niveau de laquelle vous souhaitez insérer une ligne, cliquez sur **Insérer une ligne**, puis cliquez sur **Au-dessus - En dehors du groupe**, **Au-dessus - Dans le groupe**, **En dessous - Dans le groupe**ou **En dessous - En dehors du groupe**.  
  
     Une ligne est ajoutée à l'intérieur ou à l'extérieur du groupe représenté par la cellule de groupe de lignes sur laquelle vous avez cliqué.  
  
### <a name="to-delete-a-row-from-a-group-in-a-selected-data-region"></a>Pour supprimer une ligne d'un groupe dans une région de données sélectionnée  
  
-   Dans la zone de groupe de lignes d’une région de données de tableau matriciel, cliquez avec le bouton droit sur une cellule de groupe de lignes au niveau de laquelle vous souhaitez supprimer une ligne, puis cliquez sur **Supprimer les lignes**.  
  
## <a name="see-also"></a>Voir aussi  
 [Région de données de tableau matriciel &#40;Générateur de rapports et SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md)   
 [Fonctionnement des groupes &#40;Générateur de rapports et SSRS&#41;](understanding-groups-report-builder-and-ssrs.md)   
 [Tables &#40;Générateur de rapports et SSRS&#41;](tables-report-builder-and-ssrs.md)   
 [Matrices &#40;Générateur de rapports et SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md)   
 [Listes &#40;Générateur de rapports et SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [Listes &#40;Générateur de rapports et SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
