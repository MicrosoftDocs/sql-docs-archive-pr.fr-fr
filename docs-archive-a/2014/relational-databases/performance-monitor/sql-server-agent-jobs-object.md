---
title: SQL Server Agent, objet Jobs | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLAgent:Jobs
- Jobs object
ms.assetid: 225b5e2d-4a78-4178-b2b6-b419df83c4aa
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 82ee57eba20d44c08eadc125e9dfd69e73c35751
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602791"
---
# <a name="sql-server-agent-jobs-object"></a>Agent SQL Server, Objet Jobs
  L'objet de performances **Jobs** de SQL Server Agent contient des compteurs qui fournissent des informations sur les travaux de SQL Server Agent. Le tableau ci-dessous répertorie les compteurs inclus dans cet objet.  
  
 Le tableau ci-dessous contient les compteurs **SQLAgent:Jobs** .  
  
|Nom|Description|  
|----------|-----------------|  
|**Travaux actifs**|Nombre de travaux en cours d'exécution.|  
|**Travaux non réussis**|Nombre de travaux qui se sont terminés par un échec.|  
|**Taux de travaux réussis**|Pourcentage de travaux exécutés et terminés.|  
|**Travaux activés/minute**|Nombre de travaux lancés au cours de la dernière minute.|  
|**Travaux en attente**|Nombre de travaux prêts à l'exécution par l'Agent SQL Server, mais dont l'exécution n'a pas commencé.|  
|**Travaux réussis**|Nombre de travaux terminés.|  
  
 Chaque compteur de l'objet contient les instances suivantes :  
  
|Instance|Description|  
|--------------|-----------------|  
|**_Total**|Informations sur tous les travaux.|  
|**Alertes**|Informations sur les travaux lancés par des alertes.|  
|**Autres**|Informations sur les travaux qui n'ont pas été lancés par des alertes ou des planifications. Il s’agit généralement de travaux lancés manuellement au moyen de **sp_start_job**.|  
|**Planifications**|Informations sur les travaux lancés par des planifications.|  
  
## <a name="see-also"></a>Voir aussi  
 [Implémenter des travaux](../../ssms/agent/implement-jobs.md)   
 [Utiliser des objets de performance](../../ssms/agent/use-performance-objects.md)   
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](monitor-resource-usage-system-monitor.md)  
  
  
