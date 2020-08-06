---
title: Utiliser des objets de performance | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, monitoring
- SQL Server Agent service, monitoring
- SQL Server Agent service, performance objects
- SQL Server Agent, performance objects
- performance objects [SQL Server Agent]
- monitoring [SQL Server], SQL Server Agent
- monitoring [SQL Server Agent]
- performance counters [SQL Server], SQL Server Agent
- counters [SQL Server], SQL Server Agent
ms.assetid: 830b843a-6b2a-4620-a51b-98358e9fc54b
author: stevestein
ms.author: sstein
ms.openlocfilehash: d7c1fe3f4a7d9a5fec901f84d8e913e49a4dbd1b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611485"
---
# <a name="use-performance-objects"></a>Utiliser des objets de performance
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent comprend des compteurs et des objets de performance qui permettent de surveiller le fonctionnement du service. Ces objets de performance vous permettent d'utiliser un outil Windows, en l'occurrence l'Analyseur de performances, pour identifier la tâche réalisée en arrière-plan par le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Par exemple, vous pouvez identifier le nombre de travaux actifs en cours d'exécution par le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent afin de déterminer ceux qui sont bloqués.  
  
 Les compteurs et les objets de performance du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sont disponibles pour chaque instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installée sur un ordinateur. Un objet de performance est nommé en fonction de l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qu'il représente.  
  
 Le tableau suivant décrit la dénomination des objets de performance du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent :  
  
|Type d’instance|Nom d’objet|  
|-------------------|-----------------|  
|Par défaut|**SQLAgent:** *objet*:*compteur*|  
|named|**SQLAgent$**<br /> ***instance_name* :** *objet*:*compteur*|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] comprend les objets de performance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent suivants.  
  
|Nom d’objet|Description|  
|-----------------|-----------------|  
|[SQLAgent:Jobs](../../relational-databases/performance-monitor/sql-server-agent-jobs-object.md)|Informations de performance relatives aux travaux démarrés, aux taux de réussite et à l'état actuel|  
|[SQLAgent:JobSteps](../../relational-databases/performance-monitor/sql-server-agent-jobsteps-object.md)|Informations d'état relatives aux étapes de travail|  
|[SQLAgent:Alerts](../../relational-databases/performance-monitor/sql-server-agent-alerts-object.md)|Informations relatives au nombre d'alertes et de notifications|  
|[SQLAgent:Statistics](../../relational-databases/performance-monitor/sql-server-agent-statistics-object.md)|Informations générales sur les performances|  
  
## <a name="see-also"></a>Voir aussi  
 [Surveiller et régler les performances](../../relational-databases/performance/monitor-and-tune-for-performance.md)   
 [Démarrer le Moniteur système &#40;Windows&#41;](../../relational-databases/performance/start-system-monitor-windows.md)  
  
  
