---
title: Filtrer un jeu d’éléments dans un modèle de règles d’association | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- itemsets [Analysis Services]
- filtering itemsets [Analysis Services]
- Mining Model Viewer [Analysis Services], itemsets
ms.assetid: 3ed919ea-8598-45d2-a4a0-b1b3357a4ab1
author: minewiskan
ms.author: owend
ms.openlocfilehash: f841280a6dd39a5f824f2e6a10975b0f80ed0761
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601169"
---
# <a name="filter-an-itemset-in-an-association-rules-model"></a>Filtrer un jeu d'éléments dans un modèle de règles d'association
  Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vous pouvez filtrer les jeux d’éléments affichés sous l’onglet **Jeux d’éléments** de la visionneuse de l’algorithme MAR ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules).  
  
### <a name="to-filter-an-itemset"></a>Pour filtrer un jeu d'éléments  
  
1.  Sous l’onglet **Visionneuse de modèle d’exploration de données** du Concepteur d’exploration de données dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], cliquez sur l’onglet **Jeux d’éléments** de la **Visionneuse de l’algorithme MAR (Microsoft Association Rules)**.  
  
2.  Entrez une condition de règle dans la zone **Filtrer le jeu d’éléments** . Par exemple, une condition de règle pourrait être « Touring-1000 = existing ».  
  
3.  Cliquez sur **Entrée**.  
  
 Les jeux d'éléments sont filtrés pour afficher uniquement ceux qui contiennent les éléments sélectionnés. La zone ne respecte pas la casse. Les filtres sont stockés en mémoire pour vous permettre de sélectionner un ancien filtre dans la liste.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches de la visionneuse de modèle d'exploration de données et procédures](mining-model-viewer-tasks-and-how-tos.md)  
  
  
