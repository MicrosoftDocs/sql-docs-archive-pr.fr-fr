---
title: SQL Server, nœud de mémoire | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 55b28ba9-b6d5-4ea9-8103-db8a72f42982
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d5bbc3f581ea9ececeb7d55a614ef27c3c72de7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613996"
---
# <a name="sql-server-memory-node"></a>SQL Server, nœud de mémoire
  L'objet **Nœud de mémoire** de Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit des compteurs permettant de surveiller l'utilisation globale de la mémoire sur des nœuds NUMA.  
  
## <a name="memory-node-counters"></a>Compteurs de nœuds de mémoire  
 Ce tableau décrit les compteurs **Nœud de mémoire** de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Compteurs du Gestionnaire de mémoire de SQL Server|Description|  
|----------------------------------------|-----------------|  
|**Mémoire de nœud de base de données (Ko)**|Spécifie la quantité de mémoire que le serveur utilise actuellement sur ce nœud pour les pages de bases de données.|  
|**Mémoire disponible du nœud (Ko)**|Spécifie la quantité de mémoire que le serveur n'utilise pas sur ce nœud.|  
|**Mémoire distante du nœud (Ko)**|Spécifie la quantité de mémoire non-NUMA locale sur ce nœud.|  
|**Mémoire détournée du nœud (Ko)**|Spécifie la quantité de mémoire utilisée par le serveur sur ce nœud à d'autres fins que les pages de bases de données.|  
|**Mémoire cible du nœud**|Spécifie la quantité de mémoire idéale pour ce nœud.|  
|**Mémoire totale du nœud**|Indique la quantité totale de mémoire validée par le serveur sur ce nœud.|  
  
## <a name="see-also"></a>Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](monitor-resource-usage-system-monitor.md)   
 [SQL Server, objet Gestionnaire de tampons](sql-server-buffer-manager-object.md)   
 [sys.dm_os_performance_counters &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
  
