---
title: Supprimer des jointures (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- removing joins
- joins [SQL Server], removing
- deleting joins
ms.assetid: ccc212a1-fd13-48d6-85e5-5ff310c34bbd
author: stevestein
ms.author: sstein
ms.openlocfilehash: b037e317b629671f6ec5ea1fa90edfca6fafa627
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599725"
---
# <a name="remove-joins-visual-database-tools"></a>Supprimer des jointures (Visual Database Tools)
  Si vous ne souhaitez pas que les tables soient liées par une jointure interne ou externe, vous pouvez supprimer celle-ci. Vous pouvez par exemple supprimer une jointure créée automatiquement entre deux tables par le [Concepteur de requêtes et de vues](visual-database-tools.md) .  
  
> [!NOTE]  
>  La suppression d'une jointure n'a aucune répercussion sur la relation sous-jacente existant dans la base de données.  
  
 Si deux tables jointes font partie de votre requête et que vous supprimez toutes les conditions de jointure entre elles, la requête obtenue devient le produit des deux tables, en d’autres termes une instruction CROSS JOIN.  
  
### <a name="to-remove-a-join"></a>Pour supprimer une jointure  
  
-   Dans le [volet Schéma](diagram-pane-visual-database-tools.md), sélectionnez la ligne de jointure à supprimer, puis appuyez sur la touche Suppr. Il est possible de sélectionner et supprimer plusieurs lignes de jointure à la fois.  
  
 Le Concepteur de requêtes et de vues supprime la ligne de jointure et modifie l’instruction dans le [volet SQL](sql-pane-visual-database-tools.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Joindre automatiquement des tables &#40;Visual Database Tools&#41;](join-tables-automatically-visual-database-tools.md)   
 [Joindre des tables manuellement &#40;Visual Database Tools&#41;](join-tables-manually-visual-database-tools.md)   
 [Interroger avec des jointures &#40;Visual Database Tools&#41;](query-with-joins-visual-database-tools.md)  
  
  
