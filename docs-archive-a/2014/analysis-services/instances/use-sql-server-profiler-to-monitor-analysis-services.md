---
title: Utiliser SQL Server Profiler pour analyser Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Profiler, Analysis Services
- monitoring Analysis Services [SQL Server]
- performance [Analysis Services], SQL Server Profiler
- Profiler [SQL Server Profiler], Analysis Services
ms.assetid: 8b77dafc-4584-4e93-8ad7-299304391bfd
author: minewiskan
ms.author: owend
ms.openlocfilehash: e144c1d858670f8a46b164ffc9885e6e082c4b0a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602411"
---
# <a name="use-sql-server-profiler-to-monitor-analysis-services"></a>Utiliser SQL Server Profiler pour contrôler Analysis Services
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] Le assure le suivi des événements de processus du moteur, notamment le début d’un lot ou d’une transaction, et capture des données à propos de ces événements, ce qui vous permet de surveiller l’activité des serveurs et des bases de données (par exemple, les requêtes des utilisateurs ou les connexions). Vous pouvez capturer les données du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] dans une table ou un fichier [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , en vue d'une analyse ultérieure, et relire les événements capturés sur la même instance d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou sur une autre instance pour voir exactement ce qui s'est passé. Vous pouvez relire les événements en temps réel ou pas à pas. Il est également très utile d'exécuter sur la même machine les événements de trace et les compteurs de performances. SQL Profiler peut corréler les deux en fonction de l'heure et les afficher ensemble sur une même chronologie. Les événements de trace vous donneront plus de détails, tandis que les compteurs de performances vous fourniront une vue agrégée. Pour plus d’informations sur la création et l’exécution de traces, consultez [Créer des traces de SQL Server Profiler pour la relecture &#40;Analysis Services&#41;](create-profiler-traces-for-replay-analysis-services.md).  
  
 Le tableau suivant décrit les rubriques de cette section.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Introduction à la surveillance d’Analysis Services à l’aide de SQL Server Profiler](introduction-to-monitoring-analysis-services-with-sql-server-profiler.md)|Explique comment utiliser le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] pour contrôler une instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|[Créer des traces de SQL Server Profiler pour la relecture &#40;Analysis Services&#41;](create-profiler-traces-for-replay-analysis-services.md)|Indique les conditions requises pour créer une trace afin d'effectuer une relecture en utilisant le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].|  
|[Événements de trace Analysis Services](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events)|Décrit les classes d'événements [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Ces classes d'événements sont associées aux actions générées par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et utilisées pour les relectures de traces.|  
  
## <a name="see-also"></a>Voir aussi  
 [Monitor an Analysis Services Instance](monitor-an-analysis-services-instance.md)  
  
  
