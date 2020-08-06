---
title: Définir les propriétés d’une hiérarchie de cube | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Analysis Services], multilevel
- hierarchies [Analysis Services], cubes
ms.assetid: 819d0a4e-7815-4332-a605-b07ca2ade6ac
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8903a49754357aad9cf24ee63fffa45fbf120e4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696248"
---
# <a name="define-cube-hierarchy-properties"></a>Définir les propriétés des hiérarchies de cube
  Les propriétés des hiérarchies de cube vous permettent de spécifier des paramètres uniques pour les hiérarchies définies par l'utilisateur des dimensions de cube à partir de la même dimension de base de données. Le tableau suivant décrit les propriétés d'une hiérarchie de cube.  
  
|Propriété|Description|  
|--------------|-----------------|  
|`Enabled`|Détermine si la hiérarchie est activée pour la dimension de cube.|  
|`HierarchyID`|Contient l'identificateur unique (ID) de la hiérarchie.|  
|`OptimizedState`|Détermine le niveau d'optimisation appliqué à la hiérarchie. Cette propriété peut avoir les valeurs suivantes :<br /><br /> `FullyOptimized` : l’instance génère des index pour la hiérarchie afin d’augmenter les performances en matière de requêtes. Valeur par défaut.<br /><br /> `NotOptimized` : l’instance ne génère pas d’index supplémentaire.|  
|`Visible`|Détermine la visibilité de la hiérarchie du cube. La valeur par défaut est `True`.|  
  
## <a name="see-also"></a>Voir aussi  
 [Hiérarchies utilisateur](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)  
  
  
