---
title: SQL Server, objet Buffer Manager | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Memory Manager
- Memory Manager object
ms.assetid: dbf49000-eeb0-4e9c-a361-5092363920dc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 06b58b9b6bb8a5c13e0b220ba9eeea5818682abf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602075"
---
# <a name="sql-server-memory-manager-object"></a><span data-ttu-id="ac7a1-102">Objet SQLServer:Memory Manager</span><span class="sxs-lookup"><span data-stu-id="ac7a1-102">SQL Server, Memory Manager Object</span></span>
  <span data-ttu-id="ac7a1-103">L'objet **Gestionnaire de mémoire** de Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit des compteurs permettant de surveiller l'utilisation globale de la mémoire du serveur.</span><span class="sxs-lookup"><span data-stu-id="ac7a1-103">The **Memory Manager** object in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides counters to monitor overall server memory usage.</span></span> <span data-ttu-id="ac7a1-104">La surveillance globale de l'utilisation de la mémoire du serveur afin de mesurer l'activité de l'utilisateur et son exploitation des ressources peut être utile pour détecter les goulots d'étranglement des performances.</span><span class="sxs-lookup"><span data-stu-id="ac7a1-104">Monitoring overall server memory usage to gauge user activity and resource usage can help you to identify performance bottlenecks.</span></span> <span data-ttu-id="ac7a1-105">La surveillance de la mémoire utilisée par une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vous aide à déterminer :</span><span class="sxs-lookup"><span data-stu-id="ac7a1-105">Monitoring the memory used by an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can help determine:</span></span>  
  
-   <span data-ttu-id="ac7a1-106">si des goulots d'étranglement existent en raison d'une quantité de mémoire physique disponible inadéquate pour le stockage de données fréquemment accédées dans le cache ;</span><span class="sxs-lookup"><span data-stu-id="ac7a1-106">If bottlenecks exist from inadequate physical memory for storing frequently accessed data in cache.</span></span> <span data-ttu-id="ac7a1-107">Si tel est le cas, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit extraire les données du disque.</span><span class="sxs-lookup"><span data-stu-id="ac7a1-107">If memory is inadequate, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must retrieve the data from disk.</span></span>  
  
-   <span data-ttu-id="ac7a1-108">si les performances des requêtes peuvent être améliorées en ajoutant de la mémoire ou en mettant plus de mémoire à la disposition du cache des données ou des structures internes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ac7a1-108">If query performance can be improved by adding more memory or by making more memory available to the data cache or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] internal structures.</span></span>  
  
## <a name="memory-manager-counters"></a><span data-ttu-id="ac7a1-109">Compteurs du Gestionnaire de mémoire</span><span class="sxs-lookup"><span data-stu-id="ac7a1-109">Memory Manager Counters</span></span>  
 <span data-ttu-id="ac7a1-110">Ce tableau décrit les compteurs **Gestionnaire de mémoire** de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ac7a1-110">This table describes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Memory Manager** counters.</span></span>  
  
|<span data-ttu-id="ac7a1-111">Compteurs du Gestionnaire de mémoire de SQL Server</span><span class="sxs-lookup"><span data-stu-id="ac7a1-111">SQL Server Memory Manager counters</span></span>|<span data-ttu-id="ac7a1-112">Description</span><span class="sxs-lookup"><span data-stu-id="ac7a1-112">Description</span></span>|  
|----------------------------------------|-----------------|  
|<span data-ttu-id="ac7a1-113">**Mémoire de connexion (Ko)**</span><span class="sxs-lookup"><span data-stu-id="ac7a1-113">**Connection Memory (KB)**</span></span>|<span data-ttu-id="ac7a1-114">Spécifie la quantité totale de mémoire dynamique utilisée par le serveur pour maintenir les connexions.</span><span class="sxs-lookup"><span data-stu-id="ac7a1-114">Specifies the total amount of dynamic memory the server is using for maintaining connections.</span></span>|  
|<span data-ttu-id="ac7a1-115">**Mémoire du cache de base de données (Ko)**</span><span class="sxs-lookup"><span data-stu-id="ac7a1-115">**Database Cache Memory (KB)**</span></span>|<span data-ttu-id="ac7a1-116">Spécifie la quantité de mémoire actuellement utilisée par le serveur pour le cache de la base de données.</span><span class="sxs-lookup"><span data-stu-id="ac7a1-116">Specifies the amount of memory the server is currently using for the database pages cache.</span></span>|  
|<span data-ttu-id="ac7a1-117">**Mémoire disponible (Ko)**</span><span class="sxs-lookup"><span data-stu-id="ac7a1-117">**Free Memory (KB)**</span></span>|<span data-ttu-id="ac7a1-118">Spécifie la quantité de mémoire allouée actuellement non utilisée par le serveur.</span><span class="sxs-lookup"><span data-stu-id="ac7a1-118">Specifies the amount of committed memory currently not used by the server.</span></span>|  
|<span data-ttu-id="ac7a1-119">**Mémoire réservée de l'espace de travail (Ko)**</span><span class="sxs-lookup"><span data-stu-id="ac7a1-119">**Granted Workspace Memory (KB)**</span></span>|<span data-ttu-id="ac7a1-120">Spécifie la quantité totale de mémoire actuellement réservée à l'exécution de processus tels que les opérations de hachage, de tri, de copie en bloc et de créations d'index.</span><span class="sxs-lookup"><span data-stu-id="ac7a1-120">Specifies the total amount of memory currently granted to executing processes, such as hash, sort, bulk copy, and index creation operations.</span></span>|  
|<span data-ttu-id="ac7a1-121">**Blocs de verrous**</span><span class="sxs-lookup"><span data-stu-id="ac7a1-121">**Lock Blocks**</span></span>|<span data-ttu-id="ac7a1-122">Spécifie le nombre actuel de blocs de verrous utilisés sur le serveur (mis à jour régulièrement).</span><span class="sxs-lookup"><span data-stu-id="ac7a1-122">Specifies the current number of lock blocks in use on the server (refreshed periodically).</span></span> <span data-ttu-id="ac7a1-123">Un bloc de verrous représente une ressource individuelle verrouillée, comme une table, une page ou une ligne.</span><span class="sxs-lookup"><span data-stu-id="ac7a1-123">A lock block represents an individual locked resource, such as a table, page, or row.</span></span>|  
|<span data-ttu-id="ac7a1-124">**Blocs de verrous alloués**</span><span class="sxs-lookup"><span data-stu-id="ac7a1-124">**Lock Blocks Allocated**</span></span>|<span data-ttu-id="ac7a1-125">Spécifie le nombre actuel de blocs de verrous alloués.</span><span class="sxs-lookup"><span data-stu-id="ac7a1-125">Specifies the current number of allocated lock blocks.</span></span> <span data-ttu-id="ac7a1-126">Au démarrage du serveur, le nombre de blocs de verrous alloués plus le nombre de blocs propriétaires de verrous alloués dépendent de l’option de configuration **Verrous** de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ac7a1-126">At server startup, the number of allocated lock blocks plus the number of allocated lock owner blocks depends on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Locks** configuration option.</span></span> <span data-ttu-id="ac7a1-127">Si un plus grand nombre de blocs de verrous est nécessaire, cette valeur augmente.</span><span class="sxs-lookup"><span data-stu-id="ac7a1-127">If more lock blocks are needed, the value increases.</span></span>|  
|<span data-ttu-id="ac7a1-128">**Mémoire des verrous (Ko)**</span><span class="sxs-lookup"><span data-stu-id="ac7a1-128">**Lock Memory (KB)**</span></span>|<span data-ttu-id="ac7a1-129">Spécifie la quantité totale de mémoire dynamique qu'utilise le serveur pour les verrous.</span><span class="sxs-lookup"><span data-stu-id="ac7a1-129">Specifies the total amount of dynamic memory the server is using for locks.</span></span>|  
|<span data-ttu-id="ac7a1-130">**Blocs propriétaires de verrous**</span><span class="sxs-lookup"><span data-stu-id="ac7a1-130">**Lock Owner Blocks**</span></span>|<span data-ttu-id="ac7a1-131">Spécifie le nombre actuel de blocs propriétaires de verrous utilisés sur le serveur (mis à jour régulièrement).</span><span class="sxs-lookup"><span data-stu-id="ac7a1-131">Specifies the number of lock owner blocks currently in use on the server (refreshed periodically).</span></span> <span data-ttu-id="ac7a1-132">Un bloc propriétaire de verrous représente l'appropriation d'un objet par un verrou via un thread individuel.</span><span class="sxs-lookup"><span data-stu-id="ac7a1-132">A lock owner block represents the ownership of a lock on an object by an individual thread.</span></span> <span data-ttu-id="ac7a1-133">Par conséquent, si trois threads disposent chacun d'un verrou partagé sur une page, il y aura trois blocs propriétaires de verrous.</span><span class="sxs-lookup"><span data-stu-id="ac7a1-133">Therefore, if three threads each have a shared (S) lock on a page, there will be three lock owner blocks.</span></span>|  
|<span data-ttu-id="ac7a1-134">**Blocs propriétaires de verrous alloués**</span><span class="sxs-lookup"><span data-stu-id="ac7a1-134">**Lock Owner Blocks Allocated**</span></span>|<span data-ttu-id="ac7a1-135">Spécifie le nombre actuel de blocs propriétaires de verrous alloués.</span><span class="sxs-lookup"><span data-stu-id="ac7a1-135">Specifies the current number of allocated lock owner blocks.</span></span> <span data-ttu-id="ac7a1-136">Au démarrage du serveur, le nombre de blocs propriétaires de verrous alloués et le nombre de blocs de verrous alloués dépendent de l’option de configuration **Verrous** de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ac7a1-136">At server startup, the number of allocated lock owner blocks and the number of allocated lock blocks depend on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Locks** configuration option.</span></span> <span data-ttu-id="ac7a1-137">Si un plus grand nombre de blocs propriétaires de verrous est nécessaire, cette valeur augmente dynamiquement.</span><span class="sxs-lookup"><span data-stu-id="ac7a1-137">If more lock owner blocks are needed, the value increases dynamically.</span></span>|  
|<span data-ttu-id="ac7a1-138">**Mémoire maximale de l'espace de travail (Ko)**</span><span class="sxs-lookup"><span data-stu-id="ac7a1-138">**Maximum Workspace Memory (KB)**</span></span>|<span data-ttu-id="ac7a1-139">Indique la quantité maximale de mémoire disponible pour exécuter des processus, tels que les opérations de hachage, de tri, de copie en bloc et de création d'index.</span><span class="sxs-lookup"><span data-stu-id="ac7a1-139">Indicates the maximum amount of memory available for executing processes, such as hash, sort, bulk copy, and index creation operations.</span></span>|  
|<span data-ttu-id="ac7a1-140">**Demandes de mémoire satisfaites**</span><span class="sxs-lookup"><span data-stu-id="ac7a1-140">**Memory Grants Outstanding**</span></span>|<span data-ttu-id="ac7a1-141">Spécifie le nombre total de processus qui ont acquis avec succès une allocation de mémoire de l'espace de travail.</span><span class="sxs-lookup"><span data-stu-id="ac7a1-141">Specifies the total number of processes that have successfully acquired a workspace memory grant.</span></span>|  
|<span data-ttu-id="ac7a1-142">**Demandes de mémoire en attente**</span><span class="sxs-lookup"><span data-stu-id="ac7a1-142">**Memory Grants Pending**</span></span>|<span data-ttu-id="ac7a1-143">Spécifie le nombre total de processus en attente d'une allocation de mémoire de l'espace de travail.</span><span class="sxs-lookup"><span data-stu-id="ac7a1-143">Specifies the total number of processes waiting for a workspace memory grant.</span></span>|  
|<span data-ttu-id="ac7a1-144">**Mémoire de l'optimiseur (Ko)**</span><span class="sxs-lookup"><span data-stu-id="ac7a1-144">**Optimizer Memory (KB)**</span></span>|<span data-ttu-id="ac7a1-145">Spécifie la quantité totale de mémoire dynamique utilisée par le serveur pour l'optimisation des requêtes.</span><span class="sxs-lookup"><span data-stu-id="ac7a1-145">Specifies the total amount of dynamic memory the server is using for query optimization.</span></span>|  
|<span data-ttu-id="ac7a1-146">**Mémoire réservée du serveur (Ko)**</span><span class="sxs-lookup"><span data-stu-id="ac7a1-146">**Reserved Server Memory (KB)**</span></span>|<span data-ttu-id="ac7a1-147">Indique la quantité de mémoire réservée par le serveur pour un usage futur.</span><span class="sxs-lookup"><span data-stu-id="ac7a1-147">Indicates the amount of memory the server has reserved for future usage.</span></span> <span data-ttu-id="ac7a1-148">Ce compteur affiche la quantité actuellement inutilisée de **Mémoire réservée de l’espace de travail (Ko)** octroyée initialement.</span><span class="sxs-lookup"><span data-stu-id="ac7a1-148">This counter shows the current unused amount of memory initially granted that is shown in **Granted Workspace Memory (KB)**.</span></span>|  
|<span data-ttu-id="ac7a1-149">**Mémoire du cache SQL (Ko)**</span><span class="sxs-lookup"><span data-stu-id="ac7a1-149">**SQL Cache Memory (KB)**</span></span>|<span data-ttu-id="ac7a1-150">Spécifie la quantité totale de mémoire dynamique utilisée par le serveur pour le cache SQL dynamique.</span><span class="sxs-lookup"><span data-stu-id="ac7a1-150">Specifies the total amount of dynamic memory the server is using for the dynamic SQL cache.</span></span>|  
|<span data-ttu-id="ac7a1-151">**Mémoire détournée du serveur (Ko)**</span><span class="sxs-lookup"><span data-stu-id="ac7a1-151">**Stolen Server Memory (KB)**</span></span>|<span data-ttu-id="ac7a1-152">Spécifie la quantité de mémoire utilisée par le serveur à d'autres fins que les pages de bases de données.</span><span class="sxs-lookup"><span data-stu-id="ac7a1-152">Specifies the amount of memory the server is using for purposes other than database pages.</span></span>|  
|<span data-ttu-id="ac7a1-153">**Mémoire du serveur cible (Ko)**</span><span class="sxs-lookup"><span data-stu-id="ac7a1-153">**Target Server Memory (KB)**</span></span>|<span data-ttu-id="ac7a1-154">Indique la quantité idéale de mémoire que le serveur peut consommer.</span><span class="sxs-lookup"><span data-stu-id="ac7a1-154">Indicates the ideal amount of memory the server can consume.</span></span>|  
|<span data-ttu-id="ac7a1-155">**Mémoire totale du serveur (Ko)**</span><span class="sxs-lookup"><span data-stu-id="ac7a1-155">**Total Server Memory (KB)**</span></span>|<span data-ttu-id="ac7a1-156">Spécifie la quantité de mémoire allouée par le serveur à l'aide du Gestionnaire de mémoire.</span><span class="sxs-lookup"><span data-stu-id="ac7a1-156">Specifies the amount of memory the server has committed using the memory manager.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ac7a1-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac7a1-157">See Also</span></span>  
 <span data-ttu-id="ac7a1-158">[Analyser l’utilisation des ressources &#40;Moniteur système&#41;](monitor-resource-usage-system-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="ac7a1-158">[Monitor Resource Usage &#40;System Monitor&#41;](monitor-resource-usage-system-monitor.md) </span></span>  
 <span data-ttu-id="ac7a1-159">[SQL Server, objet Gestionnaire de tampons](sql-server-buffer-manager-object.md) </span><span class="sxs-lookup"><span data-stu-id="ac7a1-159">[SQL Server, Buffer Manager Object](sql-server-buffer-manager-object.md) </span></span>  
 [<span data-ttu-id="ac7a1-160">sys.dm_os_performance_counters &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ac7a1-160">sys.dm_os_performance_counters &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
  