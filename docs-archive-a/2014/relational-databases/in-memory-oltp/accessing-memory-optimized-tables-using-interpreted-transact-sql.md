---
title: Accès aux tables optimisées en mémoire à l’aide du Transact-SQL interprété | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 92a44d4d-0e53-4fb0-b890-de264c65c95a
author: rothja
ms.author: jroth
ms.openlocfilehash: af4b3ca7731e7ca13e697f43e76ac3cc3cacb4f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612818"
---
# <a name="accessing-memory-optimized-tables-using-interpreted-transact-sql"></a><span data-ttu-id="14a59-102">Accès aux tables optimisées en mémoire à l’aide du Transact-SQL interprété</span><span class="sxs-lookup"><span data-stu-id="14a59-102">Accessing Memory-Optimized Tables Using Interpreted Transact-SQL</span></span>
  <span data-ttu-id="14a59-103">À quelques exceptions près, vous accédez aux tables mémoire optimisées à l'aide d'une requête [!INCLUDE[tsql](../../includes/tsql-md.md)] ou d'une opération DML (SELECT, INSERT, UPDATE ou DELETE), de lots ad hoc et de modules SQL, tels que des procédures stockées, des fonctions table, des déclencheurs et des vues.</span><span class="sxs-lookup"><span data-stu-id="14a59-103">With only a few exceptions, you can access memory-optimized tables using any [!INCLUDE[tsql](../../includes/tsql-md.md)] query or DML operation (SELECT, INSERT, UPDATE, or DELETE), ad hoc batches, and SQL modules such as stored procedures, table-value functions, triggers, and views.</span></span>  
  
 <span data-ttu-id="14a59-104">Le [!INCLUDE[tsql](../../includes/tsql-md.md)] interprété fait référence à des lots ou des procédures stockées [!INCLUDE[tsql](../../includes/tsql-md.md)] autres qu'une procédure stockée compilée en mode natif.</span><span class="sxs-lookup"><span data-stu-id="14a59-104">Interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] refers to [!INCLUDE[tsql](../../includes/tsql-md.md)] batches or stored procedures other than a natively compiled stored procedure.</span></span> <span data-ttu-id="14a59-105">L'accès par [!INCLUDE[tsql](../../includes/tsql-md.md)] interprété aux tables mémoire optimisées est appelé un accès d'interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="14a59-105">Interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] access to memory-optimized tables is referred to as interop access.</span></span>  
  
 <span data-ttu-id="14a59-106">Les tables mémoire optimisées sont également accessibles à l'aide d'une procédure stockée compilée en mode natif.</span><span class="sxs-lookup"><span data-stu-id="14a59-106">Memory-optimized tables can also be accessed using a natively compiled stored procedure.</span></span> <span data-ttu-id="14a59-107">Les procédures stockées compilées en mode natif sont recommandées pour les opérations OLTP critiques pour les performances.</span><span class="sxs-lookup"><span data-stu-id="14a59-107">Natively compiled stored procedures are recommended for performance-critical OLTP operations.</span></span>  
  
 <span data-ttu-id="14a59-108">L'accès en [!INCLUDE[tsql](../../includes/tsql-md.md)] interprété est recommandé dans les scénarios suivants :</span><span class="sxs-lookup"><span data-stu-id="14a59-108">Interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] access is recommended for these scenarios:</span></span>  
  
-   <span data-ttu-id="14a59-109">Requêtes ad hoc et tâches d'administration.</span><span class="sxs-lookup"><span data-stu-id="14a59-109">Ad hoc queries and administrative tasks.</span></span>  
  
-   <span data-ttu-id="14a59-110">Requêtes de rapports qui utilisent généralement des constructions non disponibles dans les procédures stockées compilées en mode natif (telles que les fonctions de fenêtre).</span><span class="sxs-lookup"><span data-stu-id="14a59-110">Reporting queries, which typically use constructs not available in natively compiled stored procedures (such as window functions).</span></span>  
  
-   <span data-ttu-id="14a59-111">Pour migrer des parties de votre application qui ont un impact sur les performances vers des tables mémoire optimisées, avec des modifications de code minimes (ou sans aucune modification du code).</span><span class="sxs-lookup"><span data-stu-id="14a59-111">To migrate performance-critical parts of your application to memory-optimized tables, with minimal (or no) application code changes.</span></span> <span data-ttu-id="14a59-112">Potentiellement, vous constaterez de meilleures performances en migrant des tables.</span><span class="sxs-lookup"><span data-stu-id="14a59-112">You can potentially see performance improvements from migrating tables.</span></span> <span data-ttu-id="14a59-113">Si vous migrez ensuite des procédures stockées vers des procédures stockées compilées en mode natif, vous constaterez des améliorations de performances accrues.</span><span class="sxs-lookup"><span data-stu-id="14a59-113">If you then migrate stored procedures to natively compiled stored procedures, you may see further performance improvement.</span></span>  
  
-   <span data-ttu-id="14a59-114">Lorsqu'une instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] n'est pas disponible pour les procédures stockées compilées en mode natif.</span><span class="sxs-lookup"><span data-stu-id="14a59-114">When a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement is not available for natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="14a59-115">Les constructions [!INCLUDE[tsql](../../includes/tsql-md.md)] suivantes ne sont pas prises en charge dans les procédures stockées [!INCLUDE[tsql](../../includes/tsql-md.md)] interprétées qui accèdent aux données dans une table mémoire optimisée.</span><span class="sxs-lookup"><span data-stu-id="14a59-115">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] constructs are not supported in interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures that access data in a memory-optimized table.</span></span>  
  
|<span data-ttu-id="14a59-116">Domaine</span><span class="sxs-lookup"><span data-stu-id="14a59-116">Area</span></span>|<span data-ttu-id="14a59-117">Non pris en charge</span><span class="sxs-lookup"><span data-stu-id="14a59-117">Unsupported</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="14a59-118">Accès aux tables</span><span class="sxs-lookup"><span data-stu-id="14a59-118">Access to tables</span></span>|<span data-ttu-id="14a59-119">TRUNCATE TABLE</span><span class="sxs-lookup"><span data-stu-id="14a59-119">TRUNCATE TABLE</span></span><br /><br /> <span data-ttu-id="14a59-120">MERGE (table mémoire optimisée comme cible).</span><span class="sxs-lookup"><span data-stu-id="14a59-120">MERGE (memory-optimized table as target)</span></span><br /><br /> <span data-ttu-id="14a59-121">Curseurs DYNAMIC et KEYSET (dégradés automatiquement en STATIC).</span><span class="sxs-lookup"><span data-stu-id="14a59-121">Dynamic and keyset cursors (these automatically degrade to static).</span></span><br /><br /> <span data-ttu-id="14a59-122">Accédez aux modules CLR à l'aide de la connexion contextuelle.</span><span class="sxs-lookup"><span data-stu-id="14a59-122">Access from CLR modules, using the context connection.</span></span><br /><br /> <span data-ttu-id="14a59-123">Référencement d'une table mémoire optimisée à partir d'une vue indexée.</span><span class="sxs-lookup"><span data-stu-id="14a59-123">Referencing a memory-optimized table from an indexed view.</span></span>|  
|<span data-ttu-id="14a59-124">Bases de données croisées</span><span class="sxs-lookup"><span data-stu-id="14a59-124">Cross-database</span></span>|<span data-ttu-id="14a59-125">Requêtes de bases de données croisées</span><span class="sxs-lookup"><span data-stu-id="14a59-125">Cross-database queries</span></span><br /><br /> <span data-ttu-id="14a59-126">Transactions de bases de données croisées</span><span class="sxs-lookup"><span data-stu-id="14a59-126">Cross-database transactions</span></span><br /><br /> <span data-ttu-id="14a59-127">Serveurs liés</span><span class="sxs-lookup"><span data-stu-id="14a59-127">Linked servers</span></span>|  
  
## <a name="table-hints"></a><span data-ttu-id="14a59-128">Indicateurs de table</span><span class="sxs-lookup"><span data-stu-id="14a59-128">Table Hints</span></span>  
 <span data-ttu-id="14a59-129">Pour plus d'informations sur les indicateurs de table, consultez.</span><span class="sxs-lookup"><span data-stu-id="14a59-129">For more information about table hints, see.</span></span> <span data-ttu-id="14a59-130">[Indicateurs de table &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table).</span><span class="sxs-lookup"><span data-stu-id="14a59-130">[Table Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table).</span></span> <span data-ttu-id="14a59-131">L’isolement d’instantané a été ajouté pour prendre en charge [!INCLUDE[hek_2](../../includes/hek-2-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="14a59-131">SNAPSHOT isolation was added to support [!INCLUDE[hek_2](../../includes/hek-2-md.md)].</span></span>  
  
 <span data-ttu-id="14a59-132">Les indicateurs de table suivants ne sont pas pris en charge lors de l'accès à une table de mémoire optimisée à l'aide du [!INCLUDE[tsql](../../includes/tsql-md.md)]interprété.</span><span class="sxs-lookup"><span data-stu-id="14a59-132">The following table hints are not supported when accessing a memory-optimized table using interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="14a59-133">HOLDLOCK</span><span class="sxs-lookup"><span data-stu-id="14a59-133">HOLDLOCK</span></span>|<span data-ttu-id="14a59-134">IGNORE_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="14a59-134">IGNORE_CONSTRAINTS</span></span>|<span data-ttu-id="14a59-135">IGNORE_TRIGGERS</span><span class="sxs-lookup"><span data-stu-id="14a59-135">IGNORE_TRIGGERS</span></span>|<span data-ttu-id="14a59-136">NOWAIT</span><span class="sxs-lookup"><span data-stu-id="14a59-136">NOWAIT</span></span>|  
|<span data-ttu-id="14a59-137">PAGLOCK</span><span class="sxs-lookup"><span data-stu-id="14a59-137">PAGLOCK</span></span>|<span data-ttu-id="14a59-138">READCOMMITTED</span><span class="sxs-lookup"><span data-stu-id="14a59-138">READCOMMITTED</span></span>|<span data-ttu-id="14a59-139">READCOMMITTEDLOCK</span><span class="sxs-lookup"><span data-stu-id="14a59-139">READCOMMITTEDLOCK</span></span>|<span data-ttu-id="14a59-140">READPAST</span><span class="sxs-lookup"><span data-stu-id="14a59-140">READPAST</span></span>|  
|<span data-ttu-id="14a59-141">READUNCOMMITTED</span><span class="sxs-lookup"><span data-stu-id="14a59-141">READUNCOMMITTED</span></span>|<span data-ttu-id="14a59-142">ROWLOCK</span><span class="sxs-lookup"><span data-stu-id="14a59-142">ROWLOCK</span></span>|<span data-ttu-id="14a59-143">SPATIAL_WINDOW_MAX_CELLS = *integer*</span><span class="sxs-lookup"><span data-stu-id="14a59-143">SPATIAL_WINDOW_MAX_CELLS = *integer*</span></span>|<span data-ttu-id="14a59-144">TABLOCK</span><span class="sxs-lookup"><span data-stu-id="14a59-144">TABLOCK</span></span>|  
|<span data-ttu-id="14a59-145">TABLOCKXX</span><span class="sxs-lookup"><span data-stu-id="14a59-145">TABLOCKXX</span></span>|<span data-ttu-id="14a59-146">UPDLOCK</span><span class="sxs-lookup"><span data-stu-id="14a59-146">UPDLOCK</span></span>|<span data-ttu-id="14a59-147">XLOCK</span><span class="sxs-lookup"><span data-stu-id="14a59-147">XLOCK</span></span>||  
  
 <span data-ttu-id="14a59-148">Lors de l'accès à une table mémoire optimisée à partir d'une transaction explicite ou implicite à l'aide du [!INCLUDE[tsql](../../includes/tsql-md.md)] interprété, vous devez inclure un indicateur de table de niveau d'isolement tel que SNAPSHOT, REPEATABLEREAD ou SERIALIZABLE, ou utiliser MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT.</span><span class="sxs-lookup"><span data-stu-id="14a59-148">When accessing a memory-optimized table from an explicit or implicit transaction using interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] you must include either an isolation level table hint such as SNAPSHOT, REPEATABLEREAD, or SERIALIZABLE, or you can use MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT.</span></span> <span data-ttu-id="14a59-149">Pour plus d’informations, consultez [instructions pour les niveaux d’isolation des transactions avec des tables optimisées en mémoire](memory-optimized-tables.md) et [options ALTER database SET &#40;&#41;Transact-SQL ](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span><span class="sxs-lookup"><span data-stu-id="14a59-149">For more information, see [Guidelines for Transaction Isolation Levels with Memory-Optimized Tables](memory-optimized-tables.md) and [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="14a59-150">Un indicateur de table de niveau d'isolation n'est pas obligatoire pour les tables mémoire optimisées accessibles par des requêtes qui s'exécutent en mode de validation automatique.</span><span class="sxs-lookup"><span data-stu-id="14a59-150">An isolation level table hint is not required for memory-optimized tables accessed by queries running in auto-commit mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14a59-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14a59-151">See Also</span></span>  
 <span data-ttu-id="14a59-152">[Prise en charge d'OLTP en mémoire par Transact-SQL](transact-sql-support-for-in-memory-oltp.md) </span><span class="sxs-lookup"><span data-stu-id="14a59-152">[Transact-SQL Support for In-Memory OLTP](transact-sql-support-for-in-memory-oltp.md) </span></span>  
 [<span data-ttu-id="14a59-153">Migration vers OLTP en mémoire</span><span class="sxs-lookup"><span data-stu-id="14a59-153">Migrating to In-Memory OLTP</span></span>](migrating-to-in-memory-oltp.md)  
  
  