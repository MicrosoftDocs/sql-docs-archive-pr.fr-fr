---
title: affinity64 Input-Output mask (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- processor affinity [SQL Server]
- binding processors [SQL Server]
- affinity64 I/O mask option
ms.assetid: d304eae7-5116-40ee-a0fa-0a3c0bc20c01
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 19616f5718254bde5601ea1beeec21412ad867de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611306"
---
# <a name="affinity64-input-output-mask-server-configuration-option"></a>affinity64 Input-Output mask (option de configuration de serveur)
  L’option **affinity64 I/O mask** lie les E/S disque de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à un sous-ensemble spécifié d’unités centrales, de manière comparable à l’option **affinity I/O mask** . Utilisez l’option **affinity I/O mask** pour lier les 32 premiers processeurs, puis **affinity64 I/O mask** pour lier les processeurs restants de l’ordinateur. Si vous reconfigurez l’option **affinity64 I/O mask**, vous devez redémarrer l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette option est visible uniquement sur la version 64 bits de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [affinity Input-Otput mask (option de configuration de serveur)](affinity-input-output-mask-server-configuration-option.md)   
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
