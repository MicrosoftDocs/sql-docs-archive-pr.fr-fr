---
title: Considérations sur la relecture des traces (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 73fa339f-b71a-4be4-97ca-d4ae84c8b90b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0c2f030a0191596e40ef1ee9e2b0b2d4da34c773
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694963"
---
# <a name="considerations-for-replaying-traces-sql-server-profiler"></a>Considérations sur la relecture des traces (SQL Server Profiler)
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ne peut pas relire les types de traces suivants :  
  
-   Les traces qui contiennent une réplication transactionnelle et d'autres activités de journal de transactions. Ces événements sont ignorés. Les autres types de réplication ne sont pas affectés car ils ne font pas d'écritures dans le journal des transactions.  
  
-   Les traces qui contiennent des opérations impliquant des identificateurs globaux uniques (GUID). Ces événements sont ignorés.  
  
-   Les traces qui contiennent des opérations sur des colonnes **text**, **ntext**et **image** ayant recours à l’utilitaire **bcp** , aux instructions BULK INSERT, READTEXT, WRITETEXT et UPDATETEXT ainsi qu’aux opérations de texte intégral. Ces événements sont ignorés.  
  
-   Les traces contenant des liaisons de session : procédures stockées système **sp_getbindtoken** et **sp_bindsession** . Ces événements sont ignorés.  
  
> [!NOTE]  
>  Si vous n’utilisez pas le modèle de relecture préconfigurée (**TSQL_Replay**) et que vous ne capturez pas toutes les données requises, le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ne relit pas la trace. Pour plus d’informations, consultez [Conditions préalables à la relecture](replay-requirements.md).  
  
 Pour savoir quelles autorisations sont nécessaires pour relire une trace, consultez [Autorisations nécessaires pour exécuter SQL Server Profiler](sql-server-profiler.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire bcp](../bcp-utility.md)   
 [Informations de référence sur la classe d’événements SQL Server](../../relational-databases/event-classes/sql-server-event-class-reference.md)   
 [sp_getbindtoken &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-getbindtoken-transact-sql)   
 [sp_bindsession &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-bindsession-transact-sql)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [READTEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/readtext-transact-sql)   
 [WRITETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/writetext-transact-sql)   
 [UPDATETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/updatetext-transact-sql)  
  
  
