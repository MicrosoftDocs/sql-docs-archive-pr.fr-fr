---
title: SQL Server, objet Latches | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Latches object
- SQLServer:Latches
ms.assetid: 2393ea1c-2bf3-41c3-9f37-b9761144eeca
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6f49ac00114065e971c0893f9217ab883eb2d7f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602082"
---
# <a name="sql-server-latches-object"></a>SQL Server - Objet Latches
  L'objet **SQLServer:Latches** de Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit des compteurs qui permettent de surveiller les verrous des ressources internes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . La surveillance des verrous internes, afin de déterminer l'activité de l'utilisateur et son exploitation des ressources, peut permettre d'identifier les goulots d'étranglement des performances.  
  
 Ce tableau décrit les compteurs **Verrous internes** de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Compteurs des verrous internes de SQL Server|Description|  
|---------------------------------|-----------------|  
|**Temps d'attente moyen d'un verrou interne (ms)**|Temps d'attente moyen d'un verrou interne (en millisecondes) pour les requêtes en attente.|  
|**Attentes de verrous internes/s**|Nombre de requêtes de verrous internes n'ayant pas pu être accordés immédiatement.|  
|**Nombre de SuperLatch**|Nombre de verrous internes qui sont actuellement des SuperLatch.|  
|**Rétrogradations SuperLatch/sec**|Nombre de SuperLatch ayant été rétrogradés au rang de verrous internes réguliers au cours de la dernière seconde.|  
|**Promotions SuperLatch/s**|Nombre de SuperLatch ayant été promus au rang de SuperLatch au cours de la dernière seconde.|  
|**Temps d'attente total des verrous internes (ms)**|Temps d'attente total (en millisecondes) pour les verrous lors de la dernière seconde.|  
  
## <a name="see-also"></a>Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](monitor-resource-usage-system-monitor.md)  
  
  
