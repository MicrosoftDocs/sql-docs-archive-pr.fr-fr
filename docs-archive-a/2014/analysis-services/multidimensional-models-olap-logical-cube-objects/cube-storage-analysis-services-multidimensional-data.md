---
title: Stockage de cube (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- measure groups [Analysis Services], cubes
- cubes [Analysis Services], storage
- linked measure groups [Analysis Services]
- storing data [Analysis Services], cubes
- partitions [Analysis Services], cubes
- storage [Analysis Services], cubes
ms.assetid: 1b1ad360-9a9b-4996-bee9-84238a2bb4ac
author: minewiskan
ms.author: owend
ms.openlocfilehash: eef1dd188b0038c637dc15750a6538c929359299
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87610895"
---
# <a name="cube-storage-analysis-services---multidimensional-data"></a>Stockage de cube (Analysis Services - Données multidimensionnelles)
  Il se peut que le stockage n'inclue que les métadonnées de cube, ou toutes les données sources de la table de faits ainsi que les agrégations définies par des dimensions liées au groupe de mesures. La quantité de données stockée dépend du mode de stockage sélectionné et du nombre d'agrégations défini. Cette quantité de données stockées influence directement les performances des requêtes. [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilise plusieurs techniques pour réduire l’espace requis pour le stockage des données et des agrégations du cube :  
  
-   Les options de stockage permettent de choisir les modes et emplacements de stockage qui conviennent le mieux aux données de cube.  
  
-   Un algorithme complexe permet de créer des agrégations de synthèse efficaces et de minimiser l'espace de stockage sans faire de compromis au niveau de la vitesse de réponse.  
  
-   Aucun stockage n'est alloué pour les cellules vides.  
  
 La définition du stockage est basée sur la partition, et au moins une partition existe pour chaque groupe de mesures d'un cube. Pour plus d’informations, consultez [partitions &#40;Analysis Services-données multidimensionnelles&#41;](partitions-analysis-services-multidimensional-data.md), [modes de stockage des partitions et traitement](partitions-partition-storage-modes-and-processing.md), [mesures et groupes](../multidimensional-models/measures-and-measure-groups.md)de mesures, et [créer des mesures et des groupes de mesures dans les modèles multidimensionnels](../multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md).  
  
## <a name="partition-storage"></a>Stockage des partitions  
 Le stockage d'un groupe de mesures peut être divisé en plusieurs partitions. Les partitions permettent de répartir un groupe de mesures en segments discrets sur un ou plusieurs serveurs, ainsi que d'optimiser le stockage et les performances des requêtes. Chaque partition d'un groupe de mesures peut être basée sur une source de données différente et être stockée en utilisant des paramètres de stockage différents.  
  
 Vous spécifiez la source de données d'une partition lorsque vous la créez. Vous pouvez aussi changer la source de données d'une partition existante. Un groupe de mesures peut être partitionné verticalement ou horizontalement. Chaque partition dans un groupe de mesures partitionné verticalement est basée sur une vue filtrée d'une seule table source. Par exemple, si un groupe de mesures est basé sur une seule table qui contient plusieurs années de données, vous pouvez créer une partition séparée pour les données de chaque année. En revanche, chaque partition dans un groupe de mesures partitionné horizontalement est basée sur une table séparée. Vous utiliserez donc les partitions horizontales si la source de données stocke les données de chaque année dans une table séparée.  
  
 Les partitions sont initialement créées avec les mêmes paramètres de stockage que le groupe de mesures dans lequel elles sont créées. Les paramètres de stockage déterminent si les données de détails et d'agrégations sont stockées dans un format multidimensionnel sur l'instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], dans un format relationnel sur le serveur source ou dans une combinaison des deux. Les paramètres de stockage déterminent également si la mise en cache proactive est employée pour répercuter automatiquement les modifications des données sources sur les données multidimensionnelles stockées sur le serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 L'utilisateur ne voit pas les partitions des cubes. Cependant, le choix des paramètres de stockage des différentes partitions peut affecter la disponibilité immédiate des données, la quantité d'espace disque utilisé et les performances des requêtes. Des partitions peuvent être stockées sur plusieurs instances [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Vous disposez ainsi d'une approche en cluster du stockage du cube et d'une répartition de la charge entre plusieurs serveurs [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Pour plus d’informations, consultez [modes de stockage des partitions et traitement](partitions-partition-storage-modes-and-processing.md), [partitions distantes](partitions-remote-partitions.md)et [partitions &#40;Analysis Services-données multidimensionnelles&#41;](partitions-analysis-services-multidimensional-data.md).  
  
## <a name="linked-measure-groups"></a>Groupes de mesures liés  
 Cette approche peut nécessiter un espace disque considérable afin de stocker plusieurs copies d'un cube sur différentes instances [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], mais elle permet de réduire tangiblement l'espace nécessaire en remplaçant les copies du groupe de mesures par des groupes de mesures liés. Un groupe de mesures lié est basé sur un groupe de mesures d'un cube dans une autre base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], sur la même instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou sur une instance différente. Un groupe de mesures lié peut également être utilisé avec des dimensions liées provenant du même cube source. Les dimensions et les groupes de mesures liés utilisent les agrégations du cube source et n'ont aucun besoin de stockage de données propre. Par conséquent, en conservant les groupes de mesures et les dimensions sources dans une base de données et en créant des cubes et des dimensions liés dans des cubes d'autres bases de données, vous pouvez économiser de l'espace disque destiné autrement au stockage. Pour plus d’informations, consultez [groupes de mesures liés](../multidimensional-models/linked-measure-groups.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Agrégations et conceptions d'agrégation](aggregations-and-aggregation-designs.md)  
  
  
