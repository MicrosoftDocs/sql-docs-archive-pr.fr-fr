---
title: Identifier les goulots d’étranglement | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- resource bottlenecks [SQL Server]
- database monitoring [SQL Server], bottlenecks
- performance [SQL Server], bottlenecks
- tuning databases [SQL Server], bottlenecks
- monitoring server performance [SQL Server], bottlenecks
- monitoring performance [SQL Server], bottlenecks
- database performance [SQL Server], bottlenecks
- server performance [SQL Server], bottlenecks
- bottlenecks [SQL Server]
- identifying bottlenecks [SQL Server]
ms.assetid: db079e65-ee80-4105-aec9-f8230d0d6635
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e941b3f4a1185177cef007eb6a02a71ae1adece7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696743"
---
# <a name="identify-bottlenecks"></a>Identifier les goulots d'étranglement
  L'accès simultané aux ressources partagées provoque des goulots d'étranglement. En général, les goulots d'étranglement sont inévitables et existent dans tous les systèmes logiciels. Toutefois, des demandes excessives sur les ressources partagées engendrent un temps de réponse médiocre, qui impose de les identifier et de les ajuster.  
  
 Les causes des goulots d'étranglement sont notamment les suivantes :  
  
-   ressources insuffisantes nécessitant l'ajout ou la mise à niveau de composants ;  
  
-   répartition inégale des charges de travail entre les ressources de même type (ce qui peut être le cas lorsqu'un disque est monopolisé) ;  
  
-   ressources défectueuses ;  
  
-   ressources configurées incorrectement.  
  
## <a name="analyzing-bottlenecks"></a>Analyse des goulots d'étranglement  
 La durée excessive de divers événements représente un indicateur des goulots d'étranglement susceptibles d'être ajustés.  
  
 Par exemple :  
  
-   un composant peut empêcher le chargement d'un autre composant, augmentant ainsi le temps nécessaire pour terminer le chargement ;  
  
-   les demandes de client peuvent prendre plus longtemps en raison d'encombrements sur le réseau.  
  
 Voici cinq domaines clés à surveiller lors du suivi des performances du serveur pour identifier les goulots d'étranglement.  
  
|Domaine possible de goulet d'étranglement|Effets sur le serveur|  
|------------------------------|---------------------------|  
|Utilisation de la mémoire|Une quantité de mémoire insuffisante, allouée ou disponible pour Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , dégrade les performances. Les données doivent être lues sur le disque plutôt que directement à partir du cache de données. Les systèmes d'exploitation Microsoft Windows font un usage excessif des fichiers d'échange : ils transfèrent des données en provenance et à destination du disque chaque fois que les pages sont nécessaires.|  
|Utilisation du processeur|Un taux d'utilisation processeur régulièrement élevé peut indiquer que les requêtes [!INCLUDE[tsql](../../includes/tsql-md.md)] doivent être ajustées ou que l'unité centrale doit être mise à niveau.|  
|Entrées/Sorties disque (E/S)|[!INCLUDE[tsql](../../includes/tsql-md.md)] Les requêtes peuvent être ajustées pour éviter les E/S superflues, par exemple en utilisant des index.|  
|Connexions utilisateur|Un nombre trop important d'utilisateurs peuvent accéder au serveur en même temps, provoquant une dégradation des performances.|  
|Verrous bloquants|Des applications mal conçues peuvent provoquer des blocages et nuire à la simultanéité, provoquant ainsi des temps de réponse plus longs et des débits de transactions plus faibles.|  
  
## <a name="see-also"></a>Voir aussi  
 [Surveiller l'utilisation de l'UC](../performance-monitor/monitor-cpu-usage.md)   
 [Surveiller l'utilisation du disque](../performance-monitor/monitor-disk-usage.md)   
 [Surveiller l'utilisation de la mémoire](../performance-monitor/monitor-memory-usage.md)   
 [SQL Server, objet General Statistics](../performance-monitor/sql-server-general-statistics-object.md)   
 [SQL Server, objet Locks](../performance-monitor/sql-server-locks-object.md)  
  
  
