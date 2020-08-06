---
title: Objets de cube (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- cubes [Analysis Services], objects
ms.assetid: 5cee362e-3f95-4467-bc6c-29b1518ecbf3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0e6dfb75be696ab26893e668b99dc36c7340f86c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87610896"
---
# <a name="cube-objects-analysis-services---multidimensional-data"></a>Objets de cube (Analysis Services - Données multidimensionnelles)
    
## <a name="introducing-cube-objects"></a>Présentation des objets de cube  
 Un objet <xref:Microsoft.AnalysisServices.Cube> simple est composé d'informations de base, de dimensions et de groupes de mesures. Les informations de base incluent le nom du cube, la mesure par défaut du cube, la source de données, le mode de stockage et d'autres informations.  
  
 La collection Dimensions contient le jeu réel de dimensions utilisé dans le cube depuis la collection de dimensions de la base de données. Toutes les dimensions doivent être définies dans la collection de dimensions de la base de données avant d'être référencées dans le cube. Les dimensions privées ne sont pas disponibles dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Les groupes de mesures sont les jeux de mesures du cube. Un groupe de mesures est une collection de mesures qui ont en commun une vue de source de données et un jeu de dimensions. Un groupe de mesures est l'unité du processus pour les mesures ; les groupes de mesures peuvent être traités individuellement, puis parcourus.  
  
## <a name="in-this-section"></a>Contenu de cette section  
  
|||  
|-|-|  
|Rubrique||  
|[Actions &#40;Analysis Services - Données multidimensionnelles&#41;](../multidimensional-models/actions-analysis-services-multidimensional-data.md)||  
|[Agrégations et conceptions d'agrégation](aggregations-and-aggregation-designs.md)||  
|[Calculs](calculations.md)||  
|[Cellules de cube &#40;Analysis Services-données multidimensionnelles&#41;](cube-cells-analysis-services-multidimensional-data.md)||  
|[Propriétés de cube](cube-properties-multidimensional-model-programming.md)||  
|[Stockage cube &#40;Analysis Services-données multidimensionnelles&#41;](cube-storage-analysis-services-multidimensional-data.md)||  
|[Traductions de cube](cube-translations.md)||  
|[Relations de dimension](dimension-relationships.md)||  
|[Indicateurs de performance clés &#40;KPI&#41; dans les modèles multidimensionnels](../multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md)||  
|[Mesures et groupes de mesures](../multidimensional-models/measures-and-measure-groups.md)||  
|[Partitions &#40;Analysis Services - Données multidimensionnelles&#41;](partitions-analysis-services-multidimensional-data.md)||  
|[Perspectives](perspectives.md)||  
  
  
