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
# <a name="considerations-for-replaying-traces-sql-server-profiler"></a><span data-ttu-id="aa33c-102">Considérations sur la relecture des traces (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="aa33c-102">Considerations for Replaying Traces (SQL Server Profiler)</span></span>
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="aa33c-103">ne peut pas relire les types de traces suivants :</span><span class="sxs-lookup"><span data-stu-id="aa33c-103">cannot replay the following kinds of traces:</span></span>  
  
-   <span data-ttu-id="aa33c-104">Les traces qui contiennent une réplication transactionnelle et d'autres activités de journal de transactions.</span><span class="sxs-lookup"><span data-stu-id="aa33c-104">Traces that contain transactional replication and other transaction log activity.</span></span> <span data-ttu-id="aa33c-105">Ces événements sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="aa33c-105">These events are skipped.</span></span> <span data-ttu-id="aa33c-106">Les autres types de réplication ne sont pas affectés car ils ne font pas d'écritures dans le journal des transactions.</span><span class="sxs-lookup"><span data-stu-id="aa33c-106">Other types of replication do not mark the transaction log so they are not affected.</span></span>  
  
-   <span data-ttu-id="aa33c-107">Les traces qui contiennent des opérations impliquant des identificateurs globaux uniques (GUID).</span><span class="sxs-lookup"><span data-stu-id="aa33c-107">Traces that contain operations that involve globally unique identifiers (GUID).</span></span> <span data-ttu-id="aa33c-108">Ces événements sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="aa33c-108">These events will be skipped.</span></span>  
  
-   <span data-ttu-id="aa33c-109">Les traces qui contiennent des opérations sur des colonnes **text**, **ntext**et **image** ayant recours à l’utilitaire **bcp** , aux instructions BULK INSERT, READTEXT, WRITETEXT et UPDATETEXT ainsi qu’aux opérations de texte intégral.</span><span class="sxs-lookup"><span data-stu-id="aa33c-109">Traces that contain operations on **text**, **ntext**, and **image** columns involving the **bcp** utility, the BULK INSERT, READTEXT, WRITETEXT, and UPDATETEXT statements, and full-text operations.</span></span> <span data-ttu-id="aa33c-110">Ces événements sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="aa33c-110">These events are skipped.</span></span>  
  
-   <span data-ttu-id="aa33c-111">Les traces contenant des liaisons de session : procédures stockées système **sp_getbindtoken** et **sp_bindsession** .</span><span class="sxs-lookup"><span data-stu-id="aa33c-111">Traces that contain session binding: **sp_getbindtoken** and **sp_bindsession** system stored procedures.</span></span> <span data-ttu-id="aa33c-112">Ces événements sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="aa33c-112">These events are skipped.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aa33c-113">Si vous n’utilisez pas le modèle de relecture préconfigurée (**TSQL_Replay**) et que vous ne capturez pas toutes les données requises, le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ne relit pas la trace.</span><span class="sxs-lookup"><span data-stu-id="aa33c-113">If you do not use the preconfigured replay template (**TSQL_Replay**), and do not capture all required data, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] does not replay the trace.</span></span> <span data-ttu-id="aa33c-114">Pour plus d’informations, consultez [Conditions préalables à la relecture](replay-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa33c-114">For more information, see [Replay Requirements](replay-requirements.md).</span></span>  
  
 <span data-ttu-id="aa33c-115">Pour savoir quelles autorisations sont nécessaires pour relire une trace, consultez [Autorisations nécessaires pour exécuter SQL Server Profiler](sql-server-profiler.md).</span><span class="sxs-lookup"><span data-stu-id="aa33c-115">For information about what permissions are required to replay a trace, see [Permissions Required to Run SQL Server Profiler](sql-server-profiler.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa33c-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aa33c-116">See Also</span></span>  
 <span data-ttu-id="aa33c-117">[Utilitaire bcp](../bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="aa33c-117">[bcp Utility](../bcp-utility.md) </span></span>  
 <span data-ttu-id="aa33c-118">[Informations de référence sur la classe d’événements SQL Server](../../relational-databases/event-classes/sql-server-event-class-reference.md) </span><span class="sxs-lookup"><span data-stu-id="aa33c-118">[SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md) </span></span>  
 <span data-ttu-id="aa33c-119">[sp_getbindtoken &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-getbindtoken-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="aa33c-119">[sp_getbindtoken &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-getbindtoken-transact-sql) </span></span>  
 <span data-ttu-id="aa33c-120">[sp_bindsession &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-bindsession-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="aa33c-120">[sp_bindsession &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-bindsession-transact-sql) </span></span>  
 <span data-ttu-id="aa33c-121">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="aa33c-121">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="aa33c-122">[READTEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/readtext-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="aa33c-122">[READTEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/readtext-transact-sql) </span></span>  
 <span data-ttu-id="aa33c-123">[WRITETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/writetext-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="aa33c-123">[WRITETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/writetext-transact-sql) </span></span>  
 [<span data-ttu-id="aa33c-124">UPDATETEXT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="aa33c-124">UPDATETEXT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/updatetext-transact-sql)  
  
  