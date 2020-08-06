---
title: SQL Server - Objet Access Methods | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Access Methods object
- SQLServer:Access Methods
ms.assetid: 27558585-e780-48bb-a042-30d664662ebc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 23f7df8267e4eba6adfde28f833f13d5e84a1efb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602797"
---
# <a name="sql-server-access-methods-object"></a><span data-ttu-id="cbf82-102">SQL Server - Objet Access Methods</span><span class="sxs-lookup"><span data-stu-id="cbf82-102">SQL Server, Access Methods Object</span></span>
  <span data-ttu-id="cbf82-103">L'objet **Access Methods** de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit des compteurs permettant de surveiller l'accès aux données logiques de la base de données.</span><span class="sxs-lookup"><span data-stu-id="cbf82-103">The **Access Methods** object in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides counters to monitor how the logical data within the database is accessed.</span></span> <span data-ttu-id="cbf82-104">Les compteurs **Gestionnaire de tampons** permettent de surveiller l'accès physique aux pages de bases de données sur le disque.</span><span class="sxs-lookup"><span data-stu-id="cbf82-104">Physical access to the database pages on disk is monitored using the **Buffer Manager** counters.</span></span> <span data-ttu-id="cbf82-105">La surveillance des méthodes d'accès aux données de la base de données permet de déterminer s'il est possible d'améliorer les performances des requêtes en ajoutant ou en modifiant des index, en ajoutant ou en déplaçant des partitions, en ajoutant des fichiers ou des groupes de fichiers, en défragmentant des index ou en réécrivant des requêtes.</span><span class="sxs-lookup"><span data-stu-id="cbf82-105">Monitoring the methods used to access data stored in the database can help you to determine whether query performance can be improved by adding or modifying indexes, adding or moving partitions, adding files or file groups, defragmenting indexes, or by rewriting queries.</span></span> <span data-ttu-id="cbf82-106">Il est également possible d'utiliser les compteurs **Méthodes d'accès** pour surveiller le volume des données, les index ou l'espace libre dans la base de données. Ils indiquent ainsi le volume des données et leur fragmentation pour chaque instance du serveur.</span><span class="sxs-lookup"><span data-stu-id="cbf82-106">The **Access Methods** counters can also be used to monitor the amount of data, indexes, and free space within the database, thereby indicating data volume and fragmentation for each server instance.</span></span> <span data-ttu-id="cbf82-107">Une fragmentation excessive des index peut nuire aux performances.</span><span class="sxs-lookup"><span data-stu-id="cbf82-107">Excessive index fragmentation can impair performance.</span></span>  
  
 <span data-ttu-id="cbf82-108">Pour des informations détaillées sur le volume, la fragmentation et l'utilisation des données, utilisez les vues de gestion dynamique suivantes :</span><span class="sxs-lookup"><span data-stu-id="cbf82-108">For more detailed information about data volume, fragmentation and usage, use the following dynamic management views:</span></span>  
  
-   [<span data-ttu-id="cbf82-109">sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cbf82-109">sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql)  
  
-   [<span data-ttu-id="cbf82-110">sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cbf82-110">sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql)  
  
-   [<span data-ttu-id="cbf82-111">sys.dm_db_partition_stats &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cbf82-111">sys.dm_db_partition_stats &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-partition-stats-transact-sql)  
  
-   [<span data-ttu-id="cbf82-112">sys.dm_db_index_usage_stats &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cbf82-112">sys.dm_db_index_usage_stats &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-usage-stats-transact-sql)  
  
 <span data-ttu-id="cbf82-113">Pour l'utilisation de l'espace dans la base de données **tempdb** au niveau fichier, tâche et session, utilisez les vues de gestion dynamique suivantes :</span><span class="sxs-lookup"><span data-stu-id="cbf82-113">For space consumption in **tempdb** at the file, task and session level, use these dynamic management views:</span></span>  
  
-   [<span data-ttu-id="cbf82-114">sys.dm_db_file_space_usage &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cbf82-114">sys.dm_db_file_space_usage &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-file-space-usage-transact-sql)  
  
-   [<span data-ttu-id="cbf82-115">sys.dm_db_task_space_usage &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cbf82-115">sys.dm_db_task_space_usage &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-task-space-usage-transact-sql)  
  
-   [<span data-ttu-id="cbf82-116">sys.dm_db_session_space_usage &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cbf82-116">sys.dm_db_session_space_usage &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-session-space-usage-transact-sql)  
  
 <span data-ttu-id="cbf82-117">Ce tableau décrit les compteurs **Méthodes d’accès** de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cbf82-117">This table describes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Access Methods** counters.</span></span>  
  
|<span data-ttu-id="cbf82-118">Compteurs méthodes d'accès de SQL Server</span><span class="sxs-lookup"><span data-stu-id="cbf82-118">SQL Server Access Methods counters</span></span>|<span data-ttu-id="cbf82-119">Description</span><span class="sxs-lookup"><span data-stu-id="cbf82-119">Description</span></span>|  
|----------------------------------------|-----------------|  
|<span data-ttu-id="cbf82-120">**Traitements de nettoyages d'unités d'allocation/s**</span><span class="sxs-lookup"><span data-stu-id="cbf82-120">**AU cleanup batches/sec**</span></span>|<span data-ttu-id="cbf82-121">Nombre de traitements par secondes effectués par la tâche en arrière-plan qui nettoie les unités d'allocation supprimées et différées.</span><span class="sxs-lookup"><span data-stu-id="cbf82-121">The number of batches per second that were completed successfully by the background task that cleans up deferred dropped allocation units.</span></span>|  
|<span data-ttu-id="cbf82-122">**Nettoyages des unités d'allocation/s**</span><span class="sxs-lookup"><span data-stu-id="cbf82-122">**AU cleanups/sec**</span></span>|<span data-ttu-id="cbf82-123">Nombre d'unités d'allocation par secondes supprimées par la tâche en arrière-plan qui nettoie les unités d'allocation supprimées et différées.</span><span class="sxs-lookup"><span data-stu-id="cbf82-123">The number of allocation units per second that were successfully dropped the background task that cleans up deferred dropped allocation units.</span></span> <span data-ttu-id="cbf82-124">Chaque suppression d'unité d'allocation nécessite plusieurs traitements.</span><span class="sxs-lookup"><span data-stu-id="cbf82-124">Each allocation unit drop requires multiple batches.</span></span>|  
|<span data-ttu-id="cbf82-125">**Nombre de créations LOB par référence**</span><span class="sxs-lookup"><span data-stu-id="cbf82-125">**By-reference Lob Create Count**</span></span>|<span data-ttu-id="cbf82-126">Nombre de valeurs des objets de grande taille (lob) passées par référence.</span><span class="sxs-lookup"><span data-stu-id="cbf82-126">Count of large object (lob) values that were passed by reference.</span></span> <span data-ttu-id="cbf82-127">Les objets de grande taille passés par référence sont utilisés dans certaines opérations en bloc pour éviter le coût de passage par valeur.</span><span class="sxs-lookup"><span data-stu-id="cbf82-127">By-reference lobs are used in certain bulk operations to avoid the cost of passing them by value.</span></span>|  
|<span data-ttu-id="cbf82-128">**Nombre d'utilisations LOB par référence**</span><span class="sxs-lookup"><span data-stu-id="cbf82-128">**By-reference Lob Use Count**</span></span>|<span data-ttu-id="cbf82-129">Nombre de valeurs LOB par référence ayant été utilisées.</span><span class="sxs-lookup"><span data-stu-id="cbf82-129">Count of by-reference lob values that were used.</span></span> <span data-ttu-id="cbf82-130">Les objets de grande taille passés par référence sont utilisés dans certaines opérations en bloc pour éviter le coût de passage par valeur.</span><span class="sxs-lookup"><span data-stu-id="cbf82-130">By-reference lobs are used in certain bulk operations to avoid the cost of passing them by-value.</span></span>|  
|<span data-ttu-id="cbf82-131">**Nombre d'objets de grande taille lus par anticipation**</span><span class="sxs-lookup"><span data-stu-id="cbf82-131">**Count Lob Readahead**</span></span>|<span data-ttu-id="cbf82-132">Nombre de pages d'objets de grande taille sur lesquelles une lecture par anticipation a eu lieu.</span><span class="sxs-lookup"><span data-stu-id="cbf82-132">Count of lob pages on which readahead was issued.</span></span>|  
|<span data-ttu-id="cbf82-133">**Nombre d'extractions dans la ligne**</span><span class="sxs-lookup"><span data-stu-id="cbf82-133">**Count Pull In Row**</span></span>|<span data-ttu-id="cbf82-134">Nombre de valeurs des colonnes ayant été extraites dans la ligne alors qu'elles étaient hors ligne.</span><span class="sxs-lookup"><span data-stu-id="cbf82-134">Count of column values that were pulled in-row from off-row.</span></span>|  
|<span data-ttu-id="cbf82-135">**Nombre d'envois hors ligne**</span><span class="sxs-lookup"><span data-stu-id="cbf82-135">**Count Push Off Row**</span></span>|<span data-ttu-id="cbf82-136">Nombre de valeurs des colonnes ayant été envoyées hors ligne alors qu'elles étaient dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="cbf82-136">Count of column values that were pushed from in-row to off-row.</span></span>|  
|<span data-ttu-id="cbf82-137">**Unités d'allocation supprimées différées**</span><span class="sxs-lookup"><span data-stu-id="cbf82-137">**Deferred Dropped Aus**</span></span>|<span data-ttu-id="cbf82-138">Nombre d'unités d'allocation en attente de suppression par la tâche en arrière-plan qui nettoie les unités d'allocation supprimées et différées.</span><span class="sxs-lookup"><span data-stu-id="cbf82-138">The number of allocation units waiting to be dropped by the background task that cleans up deferred dropped allocation units.</span></span>|  
|<span data-ttu-id="cbf82-139">**Ensembles de lignes supprimés différés**</span><span class="sxs-lookup"><span data-stu-id="cbf82-139">**Deferred Dropped rowsets**</span></span>|<span data-ttu-id="cbf82-140">Nombre d'ensembles de lignes créés suite à des opérations abandonnées de construction d'index en ligne en attente de suppression par la tâche en arrière-plan qui nettoie les ensembles de lignes supprimés et différés.</span><span class="sxs-lookup"><span data-stu-id="cbf82-140">The number of rowsets created as a result of aborted online index build operations that are waiting to be dropped by the background task that cleans up deferred dropped rowsets.</span></span>|  
|<span data-ttu-id="cbf82-141">**Nettoyages des ensembles de lignes supprimés/s**</span><span class="sxs-lookup"><span data-stu-id="cbf82-141">**Dropped rowset cleanups/sec**</span></span>|<span data-ttu-id="cbf82-142">Nombre d'ensembles de lignes par seconde créés suite à des opérations abandonnées de construction d'index en ligne supprimés par la tâche en arrière-plan qui nettoie les ensembles de lignes supprimés et différés.</span><span class="sxs-lookup"><span data-stu-id="cbf82-142">The number of rowsets per second created as a result of aborted online index build operations that were successfully dropped by the background task that cleans up deferred dropped rowsets.</span></span>|  
|<span data-ttu-id="cbf82-143">**Ensembles de lignes supprimés et ignorés/s**</span><span class="sxs-lookup"><span data-stu-id="cbf82-143">**Dropped rowsets skipped/sec**</span></span>|<span data-ttu-id="cbf82-144">Nombre d'ensembles de lignes par seconde créés suite à des opérations abandonnées de construction d'index en ligne ignorés par la tâche en arrière-plan qui nettoie les ensembles de lignes créés, supprimés et différés.</span><span class="sxs-lookup"><span data-stu-id="cbf82-144">The number of rowsets per second created as a result of aborted online index build operations that were skipped by the background task that cleans up deferred dropped rowsets created.</span></span>|  
|<span data-ttu-id="cbf82-145">**Désallocations d'extensions/s**</span><span class="sxs-lookup"><span data-stu-id="cbf82-145">**Extent Deallocations/sec**</span></span>|<span data-ttu-id="cbf82-146">Nombre d'extensions libérées par seconde dans toutes les bases de données de cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cbf82-146">Number of extents deallocated per second in all databases in this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|<span data-ttu-id="cbf82-147">**Extensions allouées/s**</span><span class="sxs-lookup"><span data-stu-id="cbf82-147">**Extents Allocated/sec**</span></span>|<span data-ttu-id="cbf82-148">Nombre d'extensions allouées par seconde dans toutes les bases de données de cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cbf82-148">Number of extents allocated per second in all databases in this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|<span data-ttu-id="cbf82-149">**Traitements de nettoyages d'unités d'allocation/s ayant échoué**</span><span class="sxs-lookup"><span data-stu-id="cbf82-149">**Failed AU cleanup batches/sec**</span></span>|<span data-ttu-id="cbf82-150">Nombre de traitements par secondes qui ont échoué et qui ont demandé une autre tentative, effectuée par la tâche en arrière-plan qui nettoie les unités d'allocation supprimées et différées.</span><span class="sxs-lookup"><span data-stu-id="cbf82-150">The number of batches per second that failed and required retry, by the background task that cleans up deferred dropped allocation units.</span></span> <span data-ttu-id="cbf82-151">L'échec peut être dû à un manque de mémoire ou d'espace disque, à une panne matérielle ou à d'autres raisons.</span><span class="sxs-lookup"><span data-stu-id="cbf82-151">Failure could be due to lack of memory or disk space, hardware failure and other reasons.</span></span>|  
|<span data-ttu-id="cbf82-152">**Échec du cookie de page feuille**</span><span class="sxs-lookup"><span data-stu-id="cbf82-152">**Failed leaf page cookie**</span></span>|<span data-ttu-id="cbf82-153">Nombre de fois où il n'a pas été possible d'utiliser un cookie de page feuille pendant une recherche d'index depuis que des modifications sont intervenues sur la page feuille.</span><span class="sxs-lookup"><span data-stu-id="cbf82-153">The number of times that a leaf page cookie could not be used during an index search since changes happened on the leaf page.</span></span> <span data-ttu-id="cbf82-154">Le cookie accélère la recherche d'index.</span><span class="sxs-lookup"><span data-stu-id="cbf82-154">The cookie is used to speed up index search.</span></span>|  
|<span data-ttu-id="cbf82-155">**Échec du cookie de page d'arborescence**</span><span class="sxs-lookup"><span data-stu-id="cbf82-155">**Failed tree page cookie**</span></span>|<span data-ttu-id="cbf82-156">Nombre de fois où il n'a pas été possible d'utiliser un cookie de page d'arborescence pendant une recherche d'index depuis que des modifications sont intervenues sur les pages parentes de ces pages d'arborescences.</span><span class="sxs-lookup"><span data-stu-id="cbf82-156">The number of times that a tree page cookie could not be used during an index search since changes happened on the parent pages of those tree pages.</span></span> <span data-ttu-id="cbf82-157">Le cookie accélère la recherche d'index.</span><span class="sxs-lookup"><span data-stu-id="cbf82-157">The cookie is used to speed up index search.</span></span>|  
|<span data-ttu-id="cbf82-158">**Enregistrements transmis/s**</span><span class="sxs-lookup"><span data-stu-id="cbf82-158">**Forwarded Records/sec**</span></span>|<span data-ttu-id="cbf82-159">Nombre d'enregistrements extraits par seconde via des pointeurs d'enregistrements transmis.</span><span class="sxs-lookup"><span data-stu-id="cbf82-159">Number of records per second fetched through forwarded record pointers.</span></span>|  
|<span data-ttu-id="cbf82-160">**Extractions de pages d'espace libre/s**</span><span class="sxs-lookup"><span data-stu-id="cbf82-160">**FreeSpace Page Fetches/sec**</span></span>|<span data-ttu-id="cbf82-161">Nombre de pages extraites par seconde par les analyses de l'espace libre.</span><span class="sxs-lookup"><span data-stu-id="cbf82-161">Number of pages fetched per second by free space scans.</span></span> <span data-ttu-id="cbf82-162">Ces analyses recherchent l'espace libre dans les pages déjà allouées à une unité d'allocation pour satisfaire les demandes d'insertion ou de modification des fragments d'enregistrements.</span><span class="sxs-lookup"><span data-stu-id="cbf82-162">These scans search for free space within pages already allocated to an allocation unit, to satisfy requests to insert or modify record fragments.</span></span>|  
|<span data-ttu-id="cbf82-163">**Analyses d'espace libre/s**</span><span class="sxs-lookup"><span data-stu-id="cbf82-163">**FreeSpace Scans/sec**</span></span>|<span data-ttu-id="cbf82-164">Nombre d'analyses par seconde lancées pour rechercher l'espace libre dans les pages déjà allouées à une unité d'allocation pour insérer ou modifier un fragment d'enregistrement.</span><span class="sxs-lookup"><span data-stu-id="cbf82-164">Number of scans per second that were initiated to search for free space within pages already allocated to an allocation unit to insert or modify record fragment.</span></span> <span data-ttu-id="cbf82-165">Chaque analyse peut trouver plusieurs pages.</span><span class="sxs-lookup"><span data-stu-id="cbf82-165">Each scan may find multiple pages.</span></span>|  
|<span data-ttu-id="cbf82-166">**Analyses complètes/s**</span><span class="sxs-lookup"><span data-stu-id="cbf82-166">**Full Scans/sec**</span></span>|<span data-ttu-id="cbf82-167">Nombre d'analyses complètes illimitées par seconde.</span><span class="sxs-lookup"><span data-stu-id="cbf82-167">Number of unrestricted full scans per second.</span></span> <span data-ttu-id="cbf82-168">Il peut s'agir d'analyses sur la table de base ou sur l'index complet.</span><span class="sxs-lookup"><span data-stu-id="cbf82-168">These can be either base-table or full-index scans.</span></span>|  
|<span data-ttu-id="cbf82-169">**Recherches d'index/s**</span><span class="sxs-lookup"><span data-stu-id="cbf82-169">**Index Searches/sec**</span></span>|<span data-ttu-id="cbf82-170">Nombre de recherches d'index par seconde.</span><span class="sxs-lookup"><span data-stu-id="cbf82-170">Number of index searches per second.</span></span> <span data-ttu-id="cbf82-171">Ces recherches sont utilisées pour démarrer une analyse ou un repositionnement d'étendue, revalider un point d'analyse, extraire un enregistrement d'index unique et rechercher l'index pour localiser où une nouvelle ligne doit être insérée.</span><span class="sxs-lookup"><span data-stu-id="cbf82-171">These are used to start a range scan, reposition a range scan, revalidate a scan point, fetch a single index record, and search down the index to locate where to insert a new row.</span></span>|  
|<span data-ttu-id="cbf82-172">**Nombre de créations de LobHandle**</span><span class="sxs-lookup"><span data-stu-id="cbf82-172">**LobHandle Create Count**</span></span>|<span data-ttu-id="cbf82-173">Nombre d'objets de grande taille (lob) temporaires créés.</span><span class="sxs-lookup"><span data-stu-id="cbf82-173">Count of temporary lobs created.</span></span>|  
|<span data-ttu-id="cbf82-174">**Nombre de destructions de LobHandle**</span><span class="sxs-lookup"><span data-stu-id="cbf82-174">**LobHandle Destroy Count**</span></span>|<span data-ttu-id="cbf82-175">Nombre d'objets de grande taille (lob) temporaires détruits.</span><span class="sxs-lookup"><span data-stu-id="cbf82-175">Count of temporary lobs destroyed.</span></span>|  
|<span data-ttu-id="cbf82-176">**Nombre de fournisseurs de services de stockage d'objets de grande taille (LobSS) créés**</span><span class="sxs-lookup"><span data-stu-id="cbf82-176">**LobSS Provider Create Count**</span></span>|<span data-ttu-id="cbf82-177">Nombre de fournisseurs de services de stockage d'objets de grande taille (LobSSP) créés.</span><span class="sxs-lookup"><span data-stu-id="cbf82-177">Count of LOB Storage Service Providers (LobSSP) created.</span></span> <span data-ttu-id="cbf82-178">Une table de travail créée par LobSSP.</span><span class="sxs-lookup"><span data-stu-id="cbf82-178">One worktable created per LobSSP.</span></span>|  
|<span data-ttu-id="cbf82-179">**Nombre de fournisseurs de services de stockage LOB détruits**</span><span class="sxs-lookup"><span data-stu-id="cbf82-179">**LobSS Provider Destroy Count**</span></span>|<span data-ttu-id="cbf82-180">Nombre de LobSSP détruits.</span><span class="sxs-lookup"><span data-stu-id="cbf82-180">Count of LobSSP destroyed.</span></span>|  
|<span data-ttu-id="cbf82-181">**Nombre de fournisseurs de services de stockage LOB tronqués**</span><span class="sxs-lookup"><span data-stu-id="cbf82-181">**LobSS Provider Truncation Count**</span></span>|<span data-ttu-id="cbf82-182">Nombre de LobSSP tronqués.</span><span class="sxs-lookup"><span data-stu-id="cbf82-182">Count of LobSSP truncated.</span></span>|  
|<span data-ttu-id="cbf82-183">**Allocations de pages mixtes/s**</span><span class="sxs-lookup"><span data-stu-id="cbf82-183">**Mixed page allocations/sec**</span></span>|<span data-ttu-id="cbf82-184">Nombre de pages allouées par seconde à partir d'extensions mixtes.</span><span class="sxs-lookup"><span data-stu-id="cbf82-184">Number of pages allocated per second from mixed extents.</span></span> <span data-ttu-id="cbf82-185">Ces pages peuvent s'utiliser pour stocker les pages IAM et les huit premières pages allouées à une unité d'allocation.</span><span class="sxs-lookup"><span data-stu-id="cbf82-185">These could be used for storing the IAM pages and the first eight pages that are allocated to an allocation unit.</span></span>|  
|<span data-ttu-id="cbf82-186">**Tentatives de compression de page/s**</span><span class="sxs-lookup"><span data-stu-id="cbf82-186">**Page compression attempts/sec**</span></span>|<span data-ttu-id="cbf82-187">Nombre de pages évaluées pour la compression de niveau page.</span><span class="sxs-lookup"><span data-stu-id="cbf82-187">Number of pages evaluated for page-level compression.</span></span> <span data-ttu-id="cbf82-188">Inclut les pages qui n'ont pas été compressées car des économies significatives n'ont pas pu être obtenues.</span><span class="sxs-lookup"><span data-stu-id="cbf82-188">Includes pages that were not compressed because significant savings could be achieved.</span></span> <span data-ttu-id="cbf82-189">Inclut tous les objets dans l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cbf82-189">Includes all objects in the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="cbf82-190">Pour plus d’informations sur les objets spécifiques, consultez [sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="cbf82-190">For information about specific objects, see [sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql).</span></span>|  
|<span data-ttu-id="cbf82-191">**Pages désallouées/s**</span><span class="sxs-lookup"><span data-stu-id="cbf82-191">**Page Deallocations/sec**</span></span>|<span data-ttu-id="cbf82-192">Nombre de pages désallouées par seconde dans toutes les bases de données de cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cbf82-192">Number of pages deallocated per second in all databases in this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]e.</span></span> <span data-ttu-id="cbf82-193">Elles comprennent les pages d'extensions mixtes et uniformes.</span><span class="sxs-lookup"><span data-stu-id="cbf82-193">These include pages from mixed extents and uniform extents.</span></span>|  
|<span data-ttu-id="cbf82-194">**Fractionnements de pages/s**</span><span class="sxs-lookup"><span data-stu-id="cbf82-194">**Page Splits/sec**</span></span>|<span data-ttu-id="cbf82-195">Nombre de fractionnements de pages par seconde qui surviennent à la suite d'un débordement des pages d'index.</span><span class="sxs-lookup"><span data-stu-id="cbf82-195">Number of page splits per second that occur as the result of overflowing index pages.</span></span>|  
|<span data-ttu-id="cbf82-196">**Pages allouées/s**</span><span class="sxs-lookup"><span data-stu-id="cbf82-196">**Pages Allocated/sec**</span></span>|<span data-ttu-id="cbf82-197">Nombre de pages allouées par seconde dans toutes les bases de données de cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cbf82-197">Number of pages allocated per second in all databases in this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="cbf82-198">Elles comprennent les allocations des pages d'extensions mixtes et uniformes.</span><span class="sxs-lookup"><span data-stu-id="cbf82-198">These include pages allocations from both mixed extents and uniform extents.</span></span>|  
|<span data-ttu-id="cbf82-199">**Pages compressées/s**</span><span class="sxs-lookup"><span data-stu-id="cbf82-199">**Pages compressed/sec**</span></span>|<span data-ttu-id="cbf82-200">Nombre de pages de données compressées à l'aide de la compression PAGE.</span><span class="sxs-lookup"><span data-stu-id="cbf82-200">Number of data pages that are compressed by using PAGE compression.</span></span> <span data-ttu-id="cbf82-201">Inclut tous les objets dans l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cbf82-201">Includes all objects in the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="cbf82-202">Pour plus d’informations sur les objets spécifiques, consultez [sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="cbf82-202">For information about specific objects, see [sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql).</span></span>|  
|<span data-ttu-id="cbf82-203">**Analyses par sondage/s**</span><span class="sxs-lookup"><span data-stu-id="cbf82-203">**Probe Scans/sec**</span></span>|<span data-ttu-id="cbf82-204">Nombre d'analyses par sondage par seconde utilisées pour trouver directement au plus une seule ligne qualifiée dans un index ou dans une table de base.</span><span class="sxs-lookup"><span data-stu-id="cbf82-204">Number of probe scans per second that are used to find at most one single qualified row in an index or base table directly.</span></span>|  
|<span data-ttu-id="cbf82-205">**Analyses d'étendue/s**</span><span class="sxs-lookup"><span data-stu-id="cbf82-205">**Range Scans/sec**</span></span>|<span data-ttu-id="cbf82-206">Nombre d'analyses d'étendue qualifiées dans les index par seconde.</span><span class="sxs-lookup"><span data-stu-id="cbf82-206">Number of qualified range scans through indexes per second.</span></span>|  
|<span data-ttu-id="cbf82-207">**Nombre de revalidations du point d'analyse/s**</span><span class="sxs-lookup"><span data-stu-id="cbf82-207">**Scan Point Revalidations/sec**</span></span>|<span data-ttu-id="cbf82-208">Nombre de revalidations du point d'analyse par seconde nécessaires à la poursuite de l'analyse.</span><span class="sxs-lookup"><span data-stu-id="cbf82-208">Number of times per second that the scan point had to be revalidated to continue the scan.</span></span>|  
|<span data-ttu-id="cbf82-209">**Enregistrements fantômes ignorés/s**</span><span class="sxs-lookup"><span data-stu-id="cbf82-209">**Skipped Ghosted Records/sec**</span></span>|<span data-ttu-id="cbf82-210">Nombre d'enregistrements fantômes ignorés par seconde pendant des analyses.</span><span class="sxs-lookup"><span data-stu-id="cbf82-210">Number of ghosted records per second skipped during scans.</span></span>|  
|<span data-ttu-id="cbf82-211">**Escalades de verrous de tables/s**</span><span class="sxs-lookup"><span data-stu-id="cbf82-211">**Table Lock Escalations/sec**</span></span>|<span data-ttu-id="cbf82-212">Nombre de fois où les verrous sur une table ont été remontés à la granularité TABLE ou HoBT.</span><span class="sxs-lookup"><span data-stu-id="cbf82-212">Number of times locks on a table were escalated to the TABLE or HoBT granularity.</span></span>|  
|<span data-ttu-id="cbf82-213">**Utilisation du cookie de page feuille**</span><span class="sxs-lookup"><span data-stu-id="cbf82-213">**Used leaf page cookie**</span></span>|<span data-ttu-id="cbf82-214">Nombre de fois où un cookie de page feuille a été utilisé pendant une recherche d'index depuis qu'aucune modification n'est intervenue sur la page feuille.</span><span class="sxs-lookup"><span data-stu-id="cbf82-214">Number of times a leaf page cookie is used successfully during an index search since no change happened on the leaf page.</span></span> <span data-ttu-id="cbf82-215">Le cookie accélère la recherche d'index.</span><span class="sxs-lookup"><span data-stu-id="cbf82-215">The cookie is used to speed up index search.</span></span>|  
|<span data-ttu-id="cbf82-216">**Utilisation du cookie de page d'arborescence**</span><span class="sxs-lookup"><span data-stu-id="cbf82-216">**Used tree page cookie**</span></span>|<span data-ttu-id="cbf82-217">Nombre de fois où un cookie de page d'arborescence a été utilisé pendant une recherche d'index depuis qu'aucune modification n'est intervenue sur la page d'arborescence.</span><span class="sxs-lookup"><span data-stu-id="cbf82-217">Number of times a tree page cookie is used successfully during an index search since no change happened on the parent page of the tree page.</span></span> <span data-ttu-id="cbf82-218">Le cookie accélère la recherche d'index.</span><span class="sxs-lookup"><span data-stu-id="cbf82-218">The cookie is used to speed up index search.</span></span>|  
|<span data-ttu-id="cbf82-219">**Fichiers de travail créés/s**</span><span class="sxs-lookup"><span data-stu-id="cbf82-219">**Workfiles Created/sec**</span></span>|<span data-ttu-id="cbf82-220">Nombre de fichiers de travail créés par seconde.</span><span class="sxs-lookup"><span data-stu-id="cbf82-220">Number of work files created per second.</span></span> <span data-ttu-id="cbf82-221">Par exemple, il est possible d'utiliser des fichiers de travail pour enregistrer des résultats temporaires de jointures et d'agrégats de hachage.</span><span class="sxs-lookup"><span data-stu-id="cbf82-221">For example, work files could be used to store temporary results for hash joins and hash aggregates.</span></span>|  
|<span data-ttu-id="cbf82-222">**Tables de travail créées/s**</span><span class="sxs-lookup"><span data-stu-id="cbf82-222">**Worktables Created/sec**</span></span>|<span data-ttu-id="cbf82-223">Nombre de tables de travail créées par seconde.</span><span class="sxs-lookup"><span data-stu-id="cbf82-223">Number of work tables created per second.</span></span> <span data-ttu-id="cbf82-224">Par exemple, il est possible d'utiliser des tables de travail pour enregistrer des résultats temporaires de mise en attente de requêtes, de variables XML et de curseurs.</span><span class="sxs-lookup"><span data-stu-id="cbf82-224">For example, work tables could be used to store temporary results for query spool, lob variables, XML variables, and cursors.</span></span>|  
|<span data-ttu-id="cbf82-225">**Taux de tables de travail à partir du cache**</span><span class="sxs-lookup"><span data-stu-id="cbf82-225">**Worktables From Cache Ratio**</span></span>|<span data-ttu-id="cbf82-226">Pourcentage de tables de travail créées lorsque les deux premières pages de la table de travail n'étaient pas allouées mais étaient immédiatement disponibles dans la mémoire cache de la table de travail.</span><span class="sxs-lookup"><span data-stu-id="cbf82-226">Percentage of work tables created where the initial two pages of the work table were not allocated but were immediately available from the work table cache.</span></span> <span data-ttu-id="cbf82-227">(Lorsqu'une table de travail est supprimée, deux pages peuvent rester allouées : elles sont placées dans la mémoire cache de la table de travail</span><span class="sxs-lookup"><span data-stu-id="cbf82-227">(When a work table is dropped, two pages may remain allocated and they are returned to the work table cache.</span></span> <span data-ttu-id="cbf82-228">pour augmenter les performances).</span><span class="sxs-lookup"><span data-stu-id="cbf82-228">This increases performance.)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cbf82-229">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cbf82-229">See Also</span></span>  
 [<span data-ttu-id="cbf82-230">Analyser l’utilisation des ressources &#40;Moniteur système&#41;</span><span class="sxs-lookup"><span data-stu-id="cbf82-230">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  