---
title: Garbage collection de l’OLTP en mémoire | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 940140a7-4785-46fc-8bf4-151435dccd3c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 23997d3664fb48902d2be08bbb22d2189c832298
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707563"
---
# <a name="in-memory-oltp-garbage-collection"></a><span data-ttu-id="e1c7f-102">Garbage collection de l'OLTP en mémoire</span><span class="sxs-lookup"><span data-stu-id="e1c7f-102">In-Memory OLTP Garbage Collection</span></span>
  <span data-ttu-id="e1c7f-103">Une ligne de données est considérée comme obsolète si elle a été supprimée par une transaction qui n'est plus active.</span><span class="sxs-lookup"><span data-stu-id="e1c7f-103">A data row is considered stale if it was deleted by a transaction that is no longer active.</span></span> <span data-ttu-id="e1c7f-104">Une ligne périmée est éligible à l'opération de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="e1c7f-104">A stale row is eligible for garbage collection.</span></span> <span data-ttu-id="e1c7f-105">Voici quelques caractéristiques du garbage collection dans [!INCLUDE[hek_2](../../includes/hek-2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="e1c7f-105">The following are characteristics of garbage collection in [!INCLUDE[hek_2](../../includes/hek-2-md.md)]:</span></span>  
  
-   <span data-ttu-id="e1c7f-106">Non bloquant.</span><span class="sxs-lookup"><span data-stu-id="e1c7f-106">Non-blocking.</span></span> <span data-ttu-id="e1c7f-107">Le garbage collection est distribué dans le temps avec un impact minimal sur la charge de travail.</span><span class="sxs-lookup"><span data-stu-id="e1c7f-107">Garbage collection is distributed over time with minimal impact on the workload.</span></span>  
  
-   <span data-ttu-id="e1c7f-108">Coopératif.</span><span class="sxs-lookup"><span data-stu-id="e1c7f-108">Cooperative.</span></span> <span data-ttu-id="e1c7f-109">Les transactions utilisateur participent au garbage collection avec le thread garbage-collection.</span><span class="sxs-lookup"><span data-stu-id="e1c7f-109">User transactions participate in garbage collection with main garbage-collection thread.</span></span>  
  
-   <span data-ttu-id="e1c7f-110">Efficace.</span><span class="sxs-lookup"><span data-stu-id="e1c7f-110">Efficient.</span></span> <span data-ttu-id="e1c7f-111">Les transactions détachent les lignes obsolètes dans le chemin d'accès (l'index) utilisé.</span><span class="sxs-lookup"><span data-stu-id="e1c7f-111">User transactions delink stale rows in the access path (the index) being used.</span></span> <span data-ttu-id="e1c7f-112">Cela réduit le travail requis lorsque la ligne est finalement supprimée.</span><span class="sxs-lookup"><span data-stu-id="e1c7f-112">This reduces the work required when the row is finally removed.</span></span>  
  
-   <span data-ttu-id="e1c7f-113">Réactif.</span><span class="sxs-lookup"><span data-stu-id="e1c7f-113">Responsive.</span></span> <span data-ttu-id="e1c7f-114">La pression exercée sur la mémoire déclenche un garbage collection agressif.</span><span class="sxs-lookup"><span data-stu-id="e1c7f-114">Memory pressure leads to aggressive garbage collection.</span></span>  
  
-   <span data-ttu-id="e1c7f-115">Évolutif.</span><span class="sxs-lookup"><span data-stu-id="e1c7f-115">Scalable.</span></span> <span data-ttu-id="e1c7f-116">Après la validation, les transactions utilisateur exécutent une partie du travail du garbage collection.</span><span class="sxs-lookup"><span data-stu-id="e1c7f-116">After commit, user transactions do part of the work of garbage collection.</span></span> <span data-ttu-id="e1c7f-117">Plus l'activité transactionnelle est importante, plus les transactions détachent de lignes obsolètes.</span><span class="sxs-lookup"><span data-stu-id="e1c7f-117">The more transaction activity, the more the transactions delink stale rows.</span></span>  
  
 <span data-ttu-id="e1c7f-118">Le garbage collection est contrôlé par le thread principal du garbage collection.</span><span class="sxs-lookup"><span data-stu-id="e1c7f-118">Garbage collection is controlled by the main garbage collection thread.</span></span> <span data-ttu-id="e1c7f-119">Le thread garbage collection principal s'exécute toutes les minutes, ou lorsque le nombre de transactions validées dépasse un seuil interne.</span><span class="sxs-lookup"><span data-stu-id="e1c7f-119">The main garbage collection thread runs every minute, or when the number of committed transactions exceeds an internal threshold.</span></span> <span data-ttu-id="e1c7f-120">Les tâches du garbage collector sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e1c7f-120">The task of the garbage collector is to:</span></span>  
  
-   <span data-ttu-id="e1c7f-121">Identifier les transactions qui ont supprimé ou mis à jour un ensemble de lignes et qui ont été validées avant la transaction active la plus ancienne.</span><span class="sxs-lookup"><span data-stu-id="e1c7f-121">Identify transactions that have deleted or updated a set of rows and have committed before the oldest active transaction.</span></span>  
  
-   <span data-ttu-id="e1c7f-122">Identifier les versions de ligne créées par les anciennes transactions.</span><span class="sxs-lookup"><span data-stu-id="e1c7f-122">Identity row versions created by these old transactions.</span></span>  
  
-   <span data-ttu-id="e1c7f-123">Grouper les anciennes lignes dans une ou plusieurs unités de 16 lignes chacune.</span><span class="sxs-lookup"><span data-stu-id="e1c7f-123">Group old rows into one or more units of 16 rows each.</span></span> <span data-ttu-id="e1c7f-124">Cela a pour but de distribuer le travail du garbage collector dans de plus petites unités.</span><span class="sxs-lookup"><span data-stu-id="e1c7f-124">This is done to distribute the work of the garbage collector into smaller units.</span></span>  
  
-   <span data-ttu-id="e1c7f-125">Déplacer ces unités de travail dans la file d'attente du garbage collection, une pour chaque planificateur.</span><span class="sxs-lookup"><span data-stu-id="e1c7f-125">Move these work units into the garbage collection queue, one for each scheduler.</span></span> <span data-ttu-id="e1c7f-126">Pour plus de détails sur les vues de gestion dynamique du garbage collector : [sys.dm_xtp_gc_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-stats-transact-sql), [sys.dm_db_xtp_gc_cycle_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-gc-cycle-stats-transact-sql) et [sys.dm_xtp_gc_queue_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-queue-stats-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="e1c7f-126">Refer to the garbage collector DMVs for the details: [sys.dm_xtp_gc_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-stats-transact-sql), [sys.dm_db_xtp_gc_cycle_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-gc-cycle-stats-transact-sql), and [sys.dm_xtp_gc_queue_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-queue-stats-transact-sql).</span></span>  
  
 <span data-ttu-id="e1c7f-127">Après qu'une transaction utilisateur est validée, elle identifie tous les éléments de la file d'attente associés au planificateur sur lequel elle s'exécute et désalloue la mémoire.</span><span class="sxs-lookup"><span data-stu-id="e1c7f-127">After a user transaction commits, it identifies all queued items associated with the scheduler it ran on and then releases the memory.</span></span> <span data-ttu-id="e1c7f-128">Si la file d'attente du garbage collection sur le planificateur est vide, il recherche une file d'attente non vide dans le nœud NUMA actuel.</span><span class="sxs-lookup"><span data-stu-id="e1c7f-128">If the garbage collection queue on the scheduler is empty, it searches for any non-empty queue in the current NUMA node.</span></span> <span data-ttu-id="e1c7f-129">En cas de faible activité transactionnelle et en cas de sollicitation de la mémoire, le thread principal garbage-collection peut accéder aux lignes extraites de n'importe quelle file d'attente pour les nettoyer.</span><span class="sxs-lookup"><span data-stu-id="e1c7f-129">If there is low transactional activity and there is memory pressure, the main garbage-collection thread can access garbage collect rows from any queue.</span></span> <span data-ttu-id="e1c7f-130">S'il n'y a aucune activité transactionnelle, par exemple, après avoir supprimé un grand nombre de lignes et s'il n'y a aucune sollicitation de la mémoire, les lignes supprimées ne sont extraites par le garbage collector que quand l'activité transactionnelle reprend ou quant la mémoire est sollicitée.</span><span class="sxs-lookup"><span data-stu-id="e1c7f-130">If there is no transactional activity after (for example) deleting a large number of rows and there is no memory pressure, the deleted rows will not be garbage collected until the transactional activity resumes or there is memory pressure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1c7f-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1c7f-131">See Also</span></span>  
 [<span data-ttu-id="e1c7f-132">Gestion de la mémoire pour l’OLTP en mémoire</span><span class="sxs-lookup"><span data-stu-id="e1c7f-132">Managing Memory for In-Memory OLTP</span></span>](../../database-engine/managing-memory-for-in-memory-oltp.md)  
  
  