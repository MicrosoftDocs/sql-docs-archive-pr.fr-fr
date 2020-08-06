---
title: Utiliser des objets SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- server performance [SQL Server], objects for monitoring
- database monitoring [SQL Server], objects for monitoring
- charts [SQL Server]
- System Monitor [SQL Server], counters
- counters [SQL Server], listed
- objects [SQL Server], performance monitoring
- objects [SQL Server], Windows System Monitor
- performance counters [SQL Server], about performance counters
- System Monitor [SQL Server], objects
- performance counters [SQL Server]
- counters [SQL Server], about performance counters
- tuning databases [SQL Server], objects for monitoring
- database performance [SQL Server], objects for monitoring
- SQL Server, objects
- monitoring performance [SQL Server], objects for monitoring
- Windows System Monitor [SQL Server], objects
- Windows System Monitor [SQL Server], counters
- counters [SQL Server]
- performance counters [SQL Server], listed
ms.assetid: bcd731b1-3c4e-4086-b58a-af7a3af904ad
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c073b0f438ec022e1b05f481652d6f08ef34cc53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698016"
---
# <a name="use-sql-server-objects"></a><span data-ttu-id="775b6-102">Utiliser des objets SQL Server</span><span class="sxs-lookup"><span data-stu-id="775b6-102">Use SQL Server Objects</span></span>
  <span data-ttu-id="775b6-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit des objets et des compteurs qui peuvent être utilisés par le Moniteur système pour surveiller l'activité des ordinateurs exécutant une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="775b6-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides objects and counters that can be used by System Monitor to monitor activity in computers running an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="775b6-104">Un objet peut être n'importe quelle ressource [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , telle qu'un verrou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou un processus Windows.</span><span class="sxs-lookup"><span data-stu-id="775b6-104">An object is any [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resource, such as a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lock or Windows process.</span></span> <span data-ttu-id="775b6-105">Chaque objet contient un ou plusieurs compteurs qui déterminent divers aspects de l'objet à surveiller.</span><span class="sxs-lookup"><span data-stu-id="775b6-105">Each object contains one or more counters that determine various aspects of the objects to monitor.</span></span> <span data-ttu-id="775b6-106">Par exemple, l’objet **SQL Server Locks** contient des compteurs appelés **Nombre d’interblocages/s** et **Dépassement du délai d’attente des verrous/s**.</span><span class="sxs-lookup"><span data-stu-id="775b6-106">For example, the **SQL Server Locks** object contains counters called **Number of Deadlocks/sec** and **Lock Timeouts/sec**.</span></span>  
  
 <span data-ttu-id="775b6-107">Certains objets disposent de plusieurs instances si plusieurs ressources d'un type donné sont présentes sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="775b6-107">Some objects have several instances if multiple resources of a given type exist on the computer.</span></span> <span data-ttu-id="775b6-108">Par exemple, le type d'objet **Processor** possède plusieurs instances si le système est multiprocesseur.</span><span class="sxs-lookup"><span data-stu-id="775b6-108">For example, the **Processor** object type will have multiple instances if a system has multiple processors.</span></span> <span data-ttu-id="775b6-109">Le type d'objet **Databases** dispose d'une instance pour chaque base de données sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="775b6-109">The **Databases** object type has one instance for each database on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="775b6-110">Certains types d’objets (l’objet **Memory Manager** , par exemple) ne disposent que d’une seule instance.</span><span class="sxs-lookup"><span data-stu-id="775b6-110">Some object types (for example, the **Memory Manager** object) have only one instance.</span></span> <span data-ttu-id="775b6-111">Si un type d'objet dispose de plusieurs instances, vous pouvez ajouter des compteurs pour suivre les statistiques de chaque instance ou, le plus souvent, de toutes les instances à la fois.</span><span class="sxs-lookup"><span data-stu-id="775b6-111">If an object type has multiple instances, you can add counters to track statistics for each instance, or in many cases, all instances at once.</span></span> <span data-ttu-id="775b6-112">Les compteurs de l'instance par défaut apparaissent au format **SQLServer:** _\<object name>_ .</span><span class="sxs-lookup"><span data-stu-id="775b6-112">Counters for the default instance appear in the format **SQLServer:**_\<object name>_.</span></span> <span data-ttu-id="775b6-113">Les compteurs pour les instances nommées apparaissent au format **MSSQL$** _\<instance name>_ **:** _\<counter name>_ ou **SQLAgent$** _\<instance name>_ **:** _\<counter name>_ .</span><span class="sxs-lookup"><span data-stu-id="775b6-113">Counters for named instances appear in the format **MSSQL$**_\<instance name>_**:**_\<counter name>_ or **SQLAgent$**_\<instance name>_**:**_\<counter name>_.</span></span>  
  
 <span data-ttu-id="775b6-114">En ajoutant ou en supprimant des compteurs du graphique et en enregistrant les valeurs du graphique, vous pouvez spécifier les objets et compteurs de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] surveillés lors du démarrage du Moniteur système.</span><span class="sxs-lookup"><span data-stu-id="775b6-114">By adding or removing counters to the chart and saving the chart settings, you can specify the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objects and counters that are monitored when System Monitor is started.</span></span>  
  
 <span data-ttu-id="775b6-115">Vous pouvez configurer le Moniteur système pour qu'il affiche des statistiques provenant de n'importe quel compteur de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="775b6-115">You can configure System Monitor to display statistics from any [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] counter.</span></span> <span data-ttu-id="775b6-116">De plus, vous pouvez fixer une valeur seuil pour n'importe quel compteur de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et générer ensuite une alerte quand le compteur dépasse ce seuil.</span><span class="sxs-lookup"><span data-stu-id="775b6-116">In addition, you can set a threshold value for any [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] counter and then generate an alert when a counter exceeds a threshold.</span></span> <span data-ttu-id="775b6-117">Pour plus d’informations sur la définition d’une alerte, consultez [Créer une alerte de base de données SQL Server](create-a-sql-server-database-alert.md).</span><span class="sxs-lookup"><span data-stu-id="775b6-117">For more information about setting an alert, see [Create a SQL Server Database Alert](create-a-sql-server-database-alert.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="775b6-118">ne sont affichées que lorsqu'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est installée.</span><span class="sxs-lookup"><span data-stu-id="775b6-118">statistics are displayed only when an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed.</span></span> <span data-ttu-id="775b6-119">Si vous arrêtez puis relancez une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l'affichage des statistiques est interrompu, puis reprend automatiquement.</span><span class="sxs-lookup"><span data-stu-id="775b6-119">If you stop and restart an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the display of statistics is interrupted and resumes automatically.</span></span> <span data-ttu-id="775b6-120">Remarquez également que vous pouvez voir des compteurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans le composant logiciel enfichable Moniteur système même si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'est pas exécuté.</span><span class="sxs-lookup"><span data-stu-id="775b6-120">Also note that you will see [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] counters in the System Monitor snap-in even if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not running.</span></span> <span data-ttu-id="775b6-121">Sur une instance cluster, les compteurs de performances ne fonctionnent sur le nœud que lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est exécuté.</span><span class="sxs-lookup"><span data-stu-id="775b6-121">On a clustered instance, performance counters only function on the node where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span>  
  
 <span data-ttu-id="775b6-122">Cette rubrique contient les sections suivantes :</span><span class="sxs-lookup"><span data-stu-id="775b6-122">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="775b6-123">Objets de performance de l'Agent SQL Server</span><span class="sxs-lookup"><span data-stu-id="775b6-123">SQL Server Agent Performance Objects</span></span>](#SQLServerAgentPOs)  
  
-   [<span data-ttu-id="775b6-124">Objets de performance de Service Broker</span><span class="sxs-lookup"><span data-stu-id="775b6-124">Service Broker Performance Objects</span></span>](#ServiceBrokerPOs)  
  
-   [<span data-ttu-id="775b6-125">Objets de performance de SQL Server</span><span class="sxs-lookup"><span data-stu-id="775b6-125">SQL Server Performance Objects</span></span>](#SQLServerPOs)  
  
-   [<span data-ttu-id="775b6-126">Objets de performance de la réplication de SQL Server</span><span class="sxs-lookup"><span data-stu-id="775b6-126">SQL Server Replication Performance Objects</span></span>](#SQLServerReplicationPOs)  
  
-   [<span data-ttu-id="775b6-127">Compteurs de pipeline SSIS</span><span class="sxs-lookup"><span data-stu-id="775b6-127">SSIS Pipeline Counters</span></span>](#SsisPipelineCounters)  
  
-   [<span data-ttu-id="775b6-128">Autorisations requises</span><span class="sxs-lookup"><span data-stu-id="775b6-128">Required Permissions</span></span>](#RequiredPermissions)  
  
##  <a name="sql-server-agent-performance-objects"></a><a name="SQLServerAgentPOs"></a> <span data-ttu-id="775b6-129">Objets de performance de l'Agent SQL Server</span><span class="sxs-lookup"><span data-stu-id="775b6-129">SQL Server Agent Performance Objects</span></span>  
 <span data-ttu-id="775b6-130">Le tableau suivant répertorie les objets de performance fournis pour l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="775b6-130">The following table lists the performance objects provided for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent:</span></span>  
  
|<span data-ttu-id="775b6-131">Objet de performance</span><span class="sxs-lookup"><span data-stu-id="775b6-131">Performance object</span></span>|<span data-ttu-id="775b6-132">Description</span><span class="sxs-lookup"><span data-stu-id="775b6-132">Description</span></span>|  
|------------------------|-----------------|  
|[<span data-ttu-id="775b6-133">SQLAgent:Alerts</span><span class="sxs-lookup"><span data-stu-id="775b6-133">SQLAgent:Alerts</span></span>](sql-server-agent-alerts-object.md)|<span data-ttu-id="775b6-134">Fournit des informations sur les alertes de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="775b6-134">Provides information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts.</span></span>|  
|[<span data-ttu-id="775b6-135">SQLAgent:Jobs</span><span class="sxs-lookup"><span data-stu-id="775b6-135">SQLAgent:Jobs</span></span>](sql-server-agent-jobs-object.md)|<span data-ttu-id="775b6-136">Fournit des informations sur les travaux de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="775b6-136">Provides information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span>|  
|[<span data-ttu-id="775b6-137">SQLAgent:JobSteps</span><span class="sxs-lookup"><span data-stu-id="775b6-137">SQLAgent:JobSteps</span></span>](sql-server-agent-jobsteps-object.md)|<span data-ttu-id="775b6-138">Fournit des informations sur les étapes de travail de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="775b6-138">Provides information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job steps.</span></span>|  
|[<span data-ttu-id="775b6-139">SQLAgent:Statistics</span><span class="sxs-lookup"><span data-stu-id="775b6-139">SQLAgent:Statistics</span></span>](sql-server-agent-statistics-object.md)|<span data-ttu-id="775b6-140">Fournit des informations générales sur l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="775b6-140">Provides general information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>|  
  
##  <a name="service-broker-performance-objects"></a><a name="ServiceBrokerPOs"></a> <span data-ttu-id="775b6-141">Objets de performance de Service Broker</span><span class="sxs-lookup"><span data-stu-id="775b6-141">Service Broker Performance Objects</span></span>  
 <span data-ttu-id="775b6-142">Le tableau suivant répertorie les objets de performance fournis pour [!INCLUDE[ssSB](../../includes/sssb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="775b6-142">The following table lists the performance objects provided for [!INCLUDE[ssSB](../../includes/sssb-md.md)].</span></span>  
  
|<span data-ttu-id="775b6-143">Objet de performance</span><span class="sxs-lookup"><span data-stu-id="775b6-143">Performance object</span></span>|<span data-ttu-id="775b6-144">Description</span><span class="sxs-lookup"><span data-stu-id="775b6-144">Description</span></span>|  
|------------------------|-----------------|  
|[<span data-ttu-id="775b6-145">SQLServer:Broker Activation</span><span class="sxs-lookup"><span data-stu-id="775b6-145">SQLServer:Broker Activation</span></span>](sql-server-broker-activation-object.md)|<span data-ttu-id="775b6-146">Fournit des informations sur les tâches activées par [!INCLUDE[ssSB](../../includes/sssb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="775b6-146">Provides information about [!INCLUDE[ssSB](../../includes/sssb-md.md)]-activated tasks.</span></span>|  
|[<span data-ttu-id="775b6-147">SQLServer:Broker Statistics</span><span class="sxs-lookup"><span data-stu-id="775b6-147">SQLServer:Broker Statistics</span></span>](sql-server-broker-statistics-object.md)|<span data-ttu-id="775b6-148">Fournit des informations générales sur [!INCLUDE[ssSB](../../includes/sssb-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="775b6-148">Provides general [!INCLUDE[ssSB](../../includes/sssb-md.md)] information.</span></span>|  
|[<span data-ttu-id="775b6-149">SQLServer:Broker Transport</span><span class="sxs-lookup"><span data-stu-id="775b6-149">SQLServer:Broker Transport</span></span>](sql-server-broker-dbm-transport-object.md)|<span data-ttu-id="775b6-150">Fournit des informations sur le réseau [!INCLUDE[ssSB](../../includes/sssb-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="775b6-150">Provides information on [!INCLUDE[ssSB](../../includes/sssb-md.md)] networking.</span></span>|  
  
##  <a name="sql-server-performance-objects"></a><a name="SQLServerPOs"></a> <span data-ttu-id="775b6-151">Objets de performance de SQL Server</span><span class="sxs-lookup"><span data-stu-id="775b6-151">SQL Server Performance Objects</span></span>  
 <span data-ttu-id="775b6-152">Le tableau ci-dessous décrit les objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="775b6-152">The following table describes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objects.</span></span>  
  
|<span data-ttu-id="775b6-153">Objet de performance</span><span class="sxs-lookup"><span data-stu-id="775b6-153">Performance object</span></span>|<span data-ttu-id="775b6-154">Description</span><span class="sxs-lookup"><span data-stu-id="775b6-154">Description</span></span>|  
|------------------------|-----------------|  
|[<span data-ttu-id="775b6-155">SQLServer:Access Methods</span><span class="sxs-lookup"><span data-stu-id="775b6-155">SQLServer:Access Methods</span></span>](sql-server-access-methods-object.md)|<span data-ttu-id="775b6-156">Recherche et mesure l'allocation des objets de bases de données de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (par exemple, le nombre de recherches d'index ou de pages allouées aux index et aux données).</span><span class="sxs-lookup"><span data-stu-id="775b6-156">Searches through and measures allocation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database objects (for example, the number of index searches or number of pages that are allocated to indexes and data).</span></span>|  
|[<span data-ttu-id="775b6-157">SQLServer:Backup Device</span><span class="sxs-lookup"><span data-stu-id="775b6-157">SQLServer:Backup Device</span></span>](sql-server-backup-device-object.md)|<span data-ttu-id="775b6-158">Fournit des informations sur les unités de sauvegarde utilisées pour les opérations de sauvegarde et de restauration, comme le débit de l'unité de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="775b6-158">Provides information about backup devices used by backup and restore operations, such as the throughput of the backup device.</span></span>|  
|[<span data-ttu-id="775b6-159">SQLServer:Buffer Manager</span><span class="sxs-lookup"><span data-stu-id="775b6-159">SQLServer:Buffer Manager</span></span>](sql-server-buffer-manager-object.md)|<span data-ttu-id="775b6-160">Fournit des informations sur les mémoires tampon utilisées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], comme les **pages libres** et le **taux d'accès au cache des tampons**.</span><span class="sxs-lookup"><span data-stu-id="775b6-160">Provides information about the memory buffers used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], such as **freememory** and **buffer cache hit ratio**.</span></span>|  
|[<span data-ttu-id="775b6-161">SQL Server:Buffer Node</span><span class="sxs-lookup"><span data-stu-id="775b6-161">SQL Server:Buffer Node</span></span>](sql-server-buffer-node.md)|<span data-ttu-id="775b6-162">Fournit des informations sur la fréquence à laquelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] effectue des demandes et accède aux pages libres.</span><span class="sxs-lookup"><span data-stu-id="775b6-162">Provides information about how frequently [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requests and accesses free pages.</span></span>|  
|[<span data-ttu-id="775b6-163">SQLServer:CLR</span><span class="sxs-lookup"><span data-stu-id="775b6-163">SQLServer:CLR</span></span>](sql-server-clr-object.md)|<span data-ttu-id="775b6-164">Fournit des informations à propos du common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="775b6-164">Provides information about the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="775b6-165">SQLServer:Cursor Manager by Type</span><span class="sxs-lookup"><span data-stu-id="775b6-165">SQLServer:Cursor Manager by Type</span></span>](sql-server-cursor-manager-by-type-object.md)|<span data-ttu-id="775b6-166">Fournit des informations sur les curseurs.</span><span class="sxs-lookup"><span data-stu-id="775b6-166">Provides information about cursors.</span></span>|  
|[<span data-ttu-id="775b6-167">SQLServer:Cursor Manager Total</span><span class="sxs-lookup"><span data-stu-id="775b6-167">SQLServer:Cursor Manager Total</span></span>](sql-server-cursor-manager-total-object.md)|<span data-ttu-id="775b6-168">Fournit des informations sur les curseurs.</span><span class="sxs-lookup"><span data-stu-id="775b6-168">Provides information about cursors.</span></span>|  
|[<span data-ttu-id="775b6-169">SQLServer:Database Mirroring</span><span class="sxs-lookup"><span data-stu-id="775b6-169">SQLServer:Database Mirroring</span></span>](sql-server-database-mirroring-object.md)|<span data-ttu-id="775b6-170">Fournit des informations sur la mise en miroir de bases de données.</span><span class="sxs-lookup"><span data-stu-id="775b6-170">Provides information about database mirroring.</span></span>|  
|[<span data-ttu-id="775b6-171">SQLServer:Databases</span><span class="sxs-lookup"><span data-stu-id="775b6-171">SQLServer:Databases</span></span>](sql-server-databases-object.md)|<span data-ttu-id="775b6-172">Fournit des informations sur une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , comme la quantité d'espace journal disponible ou le nombre de transactions actives dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="775b6-172">Provides information about a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, such as the amount of free log space available or the number of active transactions in the database.</span></span> <span data-ttu-id="775b6-173">Cet objet peut avoir plusieurs instances.</span><span class="sxs-lookup"><span data-stu-id="775b6-173">There can be multiple instances of this object.</span></span>|  
|[<span data-ttu-id="775b6-174">SQL Server : Fonctionnalités déconseillées</span><span class="sxs-lookup"><span data-stu-id="775b6-174">SQL Server:Deprecated Features</span></span>](sql-server-deprecated-features-object.md)|<span data-ttu-id="775b6-175">Compte le nombre d'utilisations de fonctions déconseillées.</span><span class="sxs-lookup"><span data-stu-id="775b6-175">Counts the number of times that deprecated features are used.</span></span>|  
|[<span data-ttu-id="775b6-176">SQLServer:Exec Statistics</span><span class="sxs-lookup"><span data-stu-id="775b6-176">SQLServer:Exec Statistics</span></span>](sql-server-execstatistics-object.md)|<span data-ttu-id="775b6-177">Fournit des informations sur les statistiques d'exécution.</span><span class="sxs-lookup"><span data-stu-id="775b6-177">Provides information about execution statistics.</span></span>|  
|[<span data-ttu-id="775b6-178">SQLServer:General Statistics</span><span class="sxs-lookup"><span data-stu-id="775b6-178">SQLServer:General Statistics</span></span>](sql-server-general-statistics-object.md)|<span data-ttu-id="775b6-179">Fournit des informations sur l'activité générale à l'échelle du serveur, comme le nombre d'utilisateurs connectés à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="775b6-179">Provides information about general server-wide activity, such as the number of users who are connected to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="775b6-180">SQL Server:HADR Availability Replica</span><span class="sxs-lookup"><span data-stu-id="775b6-180">SQL Server:HADR Availability Replica</span></span>](sql-server-availability-replica.md)|<span data-ttu-id="775b6-181">Fournit des informations sur les alertes de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssHADR](../../includes/sshadr-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="775b6-181">Provides information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssHADR](../../includes/sshadr-md.md)] availability replicas.</span></span>|  
|[<span data-ttu-id="775b6-182">SQL Server:HADR Database Replica</span><span class="sxs-lookup"><span data-stu-id="775b6-182">SQL Server:HADR Database Replica</span></span>](sql-server-database-replica.md)|<span data-ttu-id="775b6-183">Fournit des informations sur les réplicas de bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssHADR](../../includes/sshadr-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="775b6-183">Provides information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssHADR](../../includes/sshadr-md.md)] database replicas.</span></span>|  
|[<span data-ttu-id="775b6-184">SQLServer:Latches</span><span class="sxs-lookup"><span data-stu-id="775b6-184">SQLServer:Latches</span></span>](sql-server-latches-object.md)|<span data-ttu-id="775b6-185">Fournit des informations sur les verrous de ressources internes, comme les pages de bases de données, utilisés par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="775b6-185">Provides information about the latches on internal resources, such as database pages, that are used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="775b6-186">SQLServer:Locks</span><span class="sxs-lookup"><span data-stu-id="775b6-186">SQLServer:Locks</span></span>](sql-server-locks-object.md)|<span data-ttu-id="775b6-187">Fournit des informations sur les demandes de verrous individuelles émises par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], comme les dépassements du délai d'attente des verrous et les interblocages.</span><span class="sxs-lookup"><span data-stu-id="775b6-187">Provides information about the individual lock requests made by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], such as lock time-outs and deadlocks.</span></span> <span data-ttu-id="775b6-188">Cet objet peut avoir plusieurs instances.</span><span class="sxs-lookup"><span data-stu-id="775b6-188">There can be multiple instances of this object.</span></span>|  
|[<span data-ttu-id="775b6-189">SQLServer:Memory Manager</span><span class="sxs-lookup"><span data-stu-id="775b6-189">SQLServer:Memory Manager</span></span>](sql-server-memory-manager-object.md)|<span data-ttu-id="775b6-190">Fournit des informations sur l'utilisation de la mémoire de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , comme le nombre total de structures de verrous actuellement allouées.</span><span class="sxs-lookup"><span data-stu-id="775b6-190">Provides information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory usage, such as the total number of lock structures currently allocated.</span></span>|  
|[<span data-ttu-id="775b6-191">SQLServer:Plan Cache</span><span class="sxs-lookup"><span data-stu-id="775b6-191">SQLServer:Plan Cache</span></span>](sql-server-plan-cache-object.md)|<span data-ttu-id="775b6-192">Fournit des informations sur le cache de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisé pour stocker des objets tels que les procédures stockées, les déclencheurs et les plans de requête.</span><span class="sxs-lookup"><span data-stu-id="775b6-192">Provides information about the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cache used to store objects such as stored procedures, triggers, and query plans.</span></span>|  
|[<span data-ttu-id="775b6-193">SQLServer : Statistiques des pools de ressources</span><span class="sxs-lookup"><span data-stu-id="775b6-193">SQLServer: Resource Pool Stats</span></span>](sql-server-resource-pool-stats-object.md)|<span data-ttu-id="775b6-194">Fournit des informations à propos des statistiques du pool de ressources de Resource Governor.</span><span class="sxs-lookup"><span data-stu-id="775b6-194">Provides information about Resource Governor resource pool statistics.</span></span>|  
|[<span data-ttu-id="775b6-195">SQLServer:SQL Errors</span><span class="sxs-lookup"><span data-stu-id="775b6-195">SQLServer:SQL Errors</span></span>](sql-server-sql-errors-object.md)|<span data-ttu-id="775b6-196">Fournit des informations sur les erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="775b6-196">Provides information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] errors.</span></span>|  
|[<span data-ttu-id="775b6-197">SQLServer:SQL Statistics</span><span class="sxs-lookup"><span data-stu-id="775b6-197">SQLServer:SQL Statistics</span></span>](sql-server-sql-statistics-object.md)|<span data-ttu-id="775b6-198">Fournit des informations sur les aspects des requêtes [!INCLUDE[tsql](../../includes/tsql-md.md)] , comme le nombre de lots d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] reçus par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="775b6-198">Provides information about aspects of [!INCLUDE[tsql](../../includes/tsql-md.md)] queries, such as the number of batches of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements received by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="775b6-199">SQLServer:Transactions</span><span class="sxs-lookup"><span data-stu-id="775b6-199">SQLServer:Transactions</span></span>](sql-server-transactions-object.md)|<span data-ttu-id="775b6-200">Fournit des informations sur les transactions actives dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], telles que le nombre total de transactions et le nombre de transactions d'instantané.</span><span class="sxs-lookup"><span data-stu-id="775b6-200">Provides information about the active transactions in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], such as the overall number of transactions and the number of snapshot transactions.</span></span>|  
|[<span data-ttu-id="775b6-201">SQLServer:User Settable</span><span class="sxs-lookup"><span data-stu-id="775b6-201">SQLServer:User Settable</span></span>](sql-server-user-settable-object.md)|<span data-ttu-id="775b6-202">Réalise une surveillance personnalisée.</span><span class="sxs-lookup"><span data-stu-id="775b6-202">Performs custom monitoring.</span></span> <span data-ttu-id="775b6-203">Chaque compteur peut être une procédure stockée personnalisée ou toute instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] qui renvoie une valeur à surveiller.</span><span class="sxs-lookup"><span data-stu-id="775b6-203">Each counter can be a custom stored procedure or any [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that returns a value to be monitored.</span></span>|  
|[<span data-ttu-id="775b6-204">SQLServer : Statistiques d’attente</span><span class="sxs-lookup"><span data-stu-id="775b6-204">SQLServer: Wait Statistics</span></span>](sql-server-wait-statistics-object.md)|<span data-ttu-id="775b6-205">Fournit des informations sur les attentes.</span><span class="sxs-lookup"><span data-stu-id="775b6-205">Provides information about waits.</span></span>|  
|[<span data-ttu-id="775b6-206">SQLServer : Statistiques des groupes de charges de travail</span><span class="sxs-lookup"><span data-stu-id="775b6-206">SQLServer: Workload Group Stats</span></span>](sql-server-workload-group-stats-object.md)|<span data-ttu-id="775b6-207">Fournit des informations à propos des statistiques du groupe de charges de travail de Resource Governor.</span><span class="sxs-lookup"><span data-stu-id="775b6-207">Provides information about Resource Governor workload group statistics.</span></span>|  
  
##  <a name="sql-server-replication-performance-objects"></a><a name="SQLServerReplicationPOs"></a> <span data-ttu-id="775b6-208">Objets de performance de la réplication de SQL Server</span><span class="sxs-lookup"><span data-stu-id="775b6-208">SQL Server Replication Performance Objects</span></span>  
 <span data-ttu-id="775b6-209">Le tableau suivant répertorie les objets de performance fournis pour la réplication [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="775b6-209">The following table lists the performance objects provided for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication:</span></span>  
  
|<span data-ttu-id="775b6-210">Objet de performance</span><span class="sxs-lookup"><span data-stu-id="775b6-210">Performance object</span></span>|<span data-ttu-id="775b6-211">Description</span><span class="sxs-lookup"><span data-stu-id="775b6-211">Description</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="775b6-212">**SQLServer:Replication Agents**</span><span class="sxs-lookup"><span data-stu-id="775b6-212">**SQLServer:Replication Agents**</span></span><br /><br /> <span data-ttu-id="775b6-213">**SQLServer:Replication Snapshot**</span><span class="sxs-lookup"><span data-stu-id="775b6-213">**SQLServer:Replication Snapshot**</span></span><br /><br /> <span data-ttu-id="775b6-214">**SQLServer:Replication Logreader**</span><span class="sxs-lookup"><span data-stu-id="775b6-214">**SQLServer:Replication Logreader**</span></span><br /><br /> <span data-ttu-id="775b6-215">**SQLServer:Replication Dist.**</span><span class="sxs-lookup"><span data-stu-id="775b6-215">**SQLServer:Replication Dist.**</span></span><br /><br /> <span data-ttu-id="775b6-216">**SQLServer:Replication Merge**</span><span class="sxs-lookup"><span data-stu-id="775b6-216">**SQLServer:Replication Merge**</span></span><br /><br /> <span data-ttu-id="775b6-217">Pour plus d’informations, voir [Monitoring Replication with System Monitor](../replication/monitor/monitoring-replication-with-system-monitor.md).</span><span class="sxs-lookup"><span data-stu-id="775b6-217">For more information, see [Monitoring Replication with System Monitor](../replication/monitor/monitoring-replication-with-system-monitor.md).</span></span>|<span data-ttu-id="775b6-218">Fournit des informations sur l'activité de l'agent de réplication.</span><span class="sxs-lookup"><span data-stu-id="775b6-218">Provides information about replication agent activity.</span></span>|  
  
##  <a name="ssis-pipeline-counters"></a><a name="SsisPipelineCounters"></a> <span data-ttu-id="775b6-219">Compteurs de pipeline SSIS</span><span class="sxs-lookup"><span data-stu-id="775b6-219">SSIS Pipeline Counters</span></span>  
 <span data-ttu-id="775b6-220">Pour le compteur **Pipeline SSIS** , consultez [Compteur de performances](../../integration-services/performance/performance-counters.md).</span><span class="sxs-lookup"><span data-stu-id="775b6-220">For the **SSIS Pipeline** counter, see [Performance Counters](../../integration-services/performance/performance-counters.md).</span></span>  
  
##  <a name="required-permissions"></a><a name="RequiredPermissions"></a> <span data-ttu-id="775b6-221">Autorisations requises</span><span class="sxs-lookup"><span data-stu-id="775b6-221">Required Permissions</span></span>  
 <span data-ttu-id="775b6-222">L'utilisation des objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dépend des autorisations Windows, sauf **SQLAgent:Alerts**.</span><span class="sxs-lookup"><span data-stu-id="775b6-222">Use of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objects depends on Windows permissions, except **SQLAgent:Alerts**.</span></span> <span data-ttu-id="775b6-223">Pour utiliser **SQLAgent:Alerts** , les utilisateurs doivent être membres du rôle de serveur fixe **sysadmin**.</span><span class="sxs-lookup"><span data-stu-id="775b6-223">Users must be a member of the **sysadmin** fixed server role to use **SQLAgent:Alerts**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="775b6-224">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="775b6-224">See Also</span></span>  
 <span data-ttu-id="775b6-225">[Utiliser des objets de performance](../../ssms/agent/use-performance-objects.md) </span><span class="sxs-lookup"><span data-stu-id="775b6-225">[Use Performance Objects](../../ssms/agent/use-performance-objects.md) </span></span>  
 [<span data-ttu-id="775b6-226">sys.dm_os_performance_counters &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="775b6-226">sys.dm_os_performance_counters &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
  