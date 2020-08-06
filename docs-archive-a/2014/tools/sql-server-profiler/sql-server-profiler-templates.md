---
title: Modèles de SQL Server Profiler | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- default SQL Server Profiler templates
- templates [SQL Server], SQL Server Profiler
- Profiler [SQL Server Profiler], templates
- trace templates [SQL Server]
- predefined templates [SQL Server Profiler]
- SQL Server Profiler, templates
ms.assetid: b674e491-dc58-47a1-acdd-7028e9a201fc
author: stevestein
ms.author: sstein
ms.openlocfilehash: 989ae2df3b34f846f78942009d99ede39367dc0a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601858"
---
# <a name="sql-server-profiler-templates"></a><span data-ttu-id="fbee6-102">Modèles du Générateur de profils SQL Server</span><span class="sxs-lookup"><span data-stu-id="fbee6-102">SQL Server Profiler Templates</span></span>
  <span data-ttu-id="fbee6-103">Vous pouvez utiliser le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] pour créer des modèles qui définissent les classes d'événements et les colonnes de données à inclure dans les traces.</span><span class="sxs-lookup"><span data-stu-id="fbee6-103">You can use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to create templates that define the event classes and data columns to include in traces.</span></span> <span data-ttu-id="fbee6-104">Après avoir défini et enregistré le modèle, vous pouvez exécuter une trace qui enregistre les données de chaque classe d'événements sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="fbee6-104">After you define and save the template, you can run a trace that records the data for each event class you selected.</span></span> <span data-ttu-id="fbee6-105">Vous pouvez utiliser un modèle sur de nombreuses traces ; le modèle lui-même n'est pas exécuté.</span><span class="sxs-lookup"><span data-stu-id="fbee6-105">You can use a template on many traces; the template is not itself executed.</span></span>  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="fbee6-106">fournit des modèles de traces prédéfinis qui permettent de configurer aisément les classes d’événements dont vous aurez vraisemblablement besoin pour des traces spécifiques.</span><span class="sxs-lookup"><span data-stu-id="fbee6-106">offers predefined trace templates that allow you to easily configure the event classes that you will most likely need for specific traces.</span></span> <span data-ttu-id="fbee6-107">Le modèle standard, par exemple, permet de créer une trace générique pour enregistrer les connexions, les déconnexions, les traitements terminés et les informations de connexion.</span><span class="sxs-lookup"><span data-stu-id="fbee6-107">The Standard template, for example, helps you to create a generic trace for recording logins, logouts, batches completed, and connection information.</span></span> <span data-ttu-id="fbee6-108">Vous pouvez utiliser ce modèle pour exécuter des traces sans modification ou comme point de départ pour d'autres modèles avec des configurations d'événements différents.</span><span class="sxs-lookup"><span data-stu-id="fbee6-108">You can use this template to run traces without modification or as a starting point for additional templates with different event configurations.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fbee6-109">Outre les traces des modèles prédéfinis, le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] permet de créer des traces depuis un modèle vierge qui ne contient aucune classe d'événements par défaut.</span><span class="sxs-lookup"><span data-stu-id="fbee6-109">In addition to traces from predefined templates, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] also allows you to create them from a blank template, containing no event classes by default.</span></span> <span data-ttu-id="fbee6-110">Ce modèle peut s'avérer utile lorsqu'une trace planifiée ne ressemble à aucune des configurations des modèles prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="fbee6-110">Using the blank trace template can be useful when a planned trace does not resemble the configurations of any of the predefined templates.</span></span>  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="fbee6-111">peut tracer divers types de serveurs.</span><span class="sxs-lookup"><span data-stu-id="fbee6-111">can trace a variety of server types.</span></span> <span data-ttu-id="fbee6-112">Par exemple, tracez [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fbee6-112">For example you can trace [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  <span data-ttu-id="fbee6-113">Toutefois, les classes d'événements qui peuvent être incluses ne sont pas les mêmes pour chaque type de serveur.</span><span class="sxs-lookup"><span data-stu-id="fbee6-113">However, the event classes that can be included are not the same for each type of server.</span></span> <span data-ttu-id="fbee6-114">Par conséquent, le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] gère différents modèles pour différents serveurs et rend disponible le modèle spécifique qui correspond au type de serveur sélectionné.</span><span class="sxs-lookup"><span data-stu-id="fbee6-114">Therefore, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] maintains different templates for different servers, and makes available the specific template that matches the selected server type.</span></span>  
  
## <a name="predefined-templates"></a><span data-ttu-id="fbee6-115">Modèles prédéfinis</span><span class="sxs-lookup"><span data-stu-id="fbee6-115">Predefined Templates</span></span>  
 <span data-ttu-id="fbee6-116">Outre le modèle standard (celui par défaut), le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] contient divers modèles prédéfinis permettant de surveiller certains types d'événements.</span><span class="sxs-lookup"><span data-stu-id="fbee6-116">In addition to the Standard (default) template, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] includes several predefined templates for monitoring certain types of events.</span></span> <span data-ttu-id="fbee6-117">Le tableau ci-dessous répertorie les modèles prédéfinis, leur fonction et les classes d'événements pour lesquelles ils capturent des informations.</span><span class="sxs-lookup"><span data-stu-id="fbee6-117">The following table lists the predefined templates, their purpose, and the event classes for which they capture information.</span></span>  
  
|<span data-ttu-id="fbee6-118">Nom du modèle</span><span class="sxs-lookup"><span data-stu-id="fbee6-118">Template name</span></span>|<span data-ttu-id="fbee6-119">Fonction</span><span class="sxs-lookup"><span data-stu-id="fbee6-119">Template purpose</span></span>|<span data-ttu-id="fbee6-120">Classes d’événements</span><span class="sxs-lookup"><span data-stu-id="fbee6-120">Event classes</span></span>|  
|-------------------|----------------------|-------------------|  
|<span data-ttu-id="fbee6-121">SP_Counts</span><span class="sxs-lookup"><span data-stu-id="fbee6-121">SP_Counts</span></span>|<span data-ttu-id="fbee6-122">Capture le comportement de l'exécution des procédures stockées dans le temps.</span><span class="sxs-lookup"><span data-stu-id="fbee6-122">Captures stored procedure execution behavior over time.</span></span>|<span data-ttu-id="fbee6-123">**SP:Starting**</span><span class="sxs-lookup"><span data-stu-id="fbee6-123">**SP:Starting**</span></span>|  
|<span data-ttu-id="fbee6-124">standard</span><span class="sxs-lookup"><span data-stu-id="fbee6-124">Standard</span></span>|<span data-ttu-id="fbee6-125">Point de départ générique de création d'une trace.</span><span class="sxs-lookup"><span data-stu-id="fbee6-125">Generic starting point for creating a trace.</span></span> <span data-ttu-id="fbee6-126">Capture toutes les procédures stockées et tous les traitements [!INCLUDE[tsql](../../includes/tsql-md.md)] exécutés.</span><span class="sxs-lookup"><span data-stu-id="fbee6-126">Captures all stored procedures and [!INCLUDE[tsql](../../includes/tsql-md.md)] batches that are run.</span></span> <span data-ttu-id="fbee6-127">Permet de surveiller l'activité générale du serveur de base de données.</span><span class="sxs-lookup"><span data-stu-id="fbee6-127">Use to monitor general database server activity.</span></span>|<span data-ttu-id="fbee6-128">**Audit Login**</span><span class="sxs-lookup"><span data-stu-id="fbee6-128">**Audit Login**</span></span><br /><br /> <span data-ttu-id="fbee6-129">**Audit Logout**</span><span class="sxs-lookup"><span data-stu-id="fbee6-129">**Audit Logout**</span></span><br /><br /> <span data-ttu-id="fbee6-130">**ExistingConnection**</span><span class="sxs-lookup"><span data-stu-id="fbee6-130">**ExistingConnection**</span></span><br /><br /> <span data-ttu-id="fbee6-131">**RPC:Completed**</span><span class="sxs-lookup"><span data-stu-id="fbee6-131">**RPC:Completed**</span></span><br /><br /> <span data-ttu-id="fbee6-132">**SQL:BatchCompleted**</span><span class="sxs-lookup"><span data-stu-id="fbee6-132">**SQL:BatchCompleted**</span></span><br /><br /> <span data-ttu-id="fbee6-133">**SQL:BatchStarting**</span><span class="sxs-lookup"><span data-stu-id="fbee6-133">**SQL:BatchStarting**</span></span>|  
|<span data-ttu-id="fbee6-134">TSQL</span><span class="sxs-lookup"><span data-stu-id="fbee6-134">TSQL</span></span>|<span data-ttu-id="fbee6-135">Capture toutes les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] soumises à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par les clients, ainsi que l'heure de leur émission.</span><span class="sxs-lookup"><span data-stu-id="fbee6-135">Captures all [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that are submitted to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by clients and the time issued.</span></span> <span data-ttu-id="fbee6-136">Permet de déboguer les applications clientes.</span><span class="sxs-lookup"><span data-stu-id="fbee6-136">Use to debug client applications.</span></span>|<span data-ttu-id="fbee6-137">**Audit Login**</span><span class="sxs-lookup"><span data-stu-id="fbee6-137">**Audit Login**</span></span><br /><br /> <span data-ttu-id="fbee6-138">**Audit Logout**</span><span class="sxs-lookup"><span data-stu-id="fbee6-138">**Audit Logout**</span></span><br /><br /> <span data-ttu-id="fbee6-139">**ExistingConnection**</span><span class="sxs-lookup"><span data-stu-id="fbee6-139">**ExistingConnection**</span></span><br /><br /> <span data-ttu-id="fbee6-140">**RPC:Starting**</span><span class="sxs-lookup"><span data-stu-id="fbee6-140">**RPC:Starting**</span></span><br /><br /> <span data-ttu-id="fbee6-141">**SQL:BatchStarting**</span><span class="sxs-lookup"><span data-stu-id="fbee6-141">**SQL:BatchStarting**</span></span>|  
|<span data-ttu-id="fbee6-142">TSQL_Duration</span><span class="sxs-lookup"><span data-stu-id="fbee6-142">TSQL_Duration</span></span>|<span data-ttu-id="fbee6-143">Capture toutes les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] soumises à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par les clients, leur délai d'exécution (en millisecondes) et les regroupe en fonction de leur durée.</span><span class="sxs-lookup"><span data-stu-id="fbee6-143">Captures all [!INCLUDE[tsql](../../includes/tsql-md.md)] statements submitted to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by clients, their execution time (in milliseconds), and groups them by duration.</span></span> <span data-ttu-id="fbee6-144">Permet d'identifier les requêtes lentes.</span><span class="sxs-lookup"><span data-stu-id="fbee6-144">Use to identify slow queries.</span></span>|<span data-ttu-id="fbee6-145">**RPC:Completed**</span><span class="sxs-lookup"><span data-stu-id="fbee6-145">**RPC:Completed**</span></span><br /><br /> <span data-ttu-id="fbee6-146">**SQL:BatchCompleted**</span><span class="sxs-lookup"><span data-stu-id="fbee6-146">**SQL:BatchCompleted**</span></span>|  
|<span data-ttu-id="fbee6-147">TSQL_Grouped</span><span class="sxs-lookup"><span data-stu-id="fbee6-147">TSQL_Grouped</span></span>|<span data-ttu-id="fbee6-148">Capture toutes les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] soumises à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et l’heure à laquelle elles ont été émises.</span><span class="sxs-lookup"><span data-stu-id="fbee6-148">Captures all [!INCLUDE[tsql](../../includes/tsql-md.md)] statements submitted to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the time they were issued.</span></span> <span data-ttu-id="fbee6-149">Regroupe les informations en fonction du client ou de l'utilisateur qui a émis l'instruction.</span><span class="sxs-lookup"><span data-stu-id="fbee6-149">Groups information by user or client that submitted the statement.</span></span> <span data-ttu-id="fbee6-150">Permet d'analyser les requêtes d'un client ou d'un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="fbee6-150">Use to investigate queries from a particular client or user.</span></span>|<span data-ttu-id="fbee6-151">**Audit Login**</span><span class="sxs-lookup"><span data-stu-id="fbee6-151">**Audit Login**</span></span><br /><br /> <span data-ttu-id="fbee6-152">**Audit Logout**</span><span class="sxs-lookup"><span data-stu-id="fbee6-152">**Audit Logout**</span></span><br /><br /> <span data-ttu-id="fbee6-153">**ExistingConnection**</span><span class="sxs-lookup"><span data-stu-id="fbee6-153">**ExistingConnection**</span></span><br /><br /> <span data-ttu-id="fbee6-154">**RPC:Starting**</span><span class="sxs-lookup"><span data-stu-id="fbee6-154">**RPC:Starting**</span></span><br /><br /> <span data-ttu-id="fbee6-155">**SQL:BatchStarting**</span><span class="sxs-lookup"><span data-stu-id="fbee6-155">**SQL:BatchStarting**</span></span>|  
|<span data-ttu-id="fbee6-156">TSQL_Locks</span><span class="sxs-lookup"><span data-stu-id="fbee6-156">TSQL_Locks</span></span>|<span data-ttu-id="fbee6-157">Capture toutes les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] soumises à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par les clients, ainsi que les événements de verrou exceptionnels.</span><span class="sxs-lookup"><span data-stu-id="fbee6-157">Captures all of the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that are submitted to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by clients along with exceptional lock events.</span></span> <span data-ttu-id="fbee6-158">Permet de dépanner les blocages, les délais d'expiration de verrou et les événements d'escalade de verrous.</span><span class="sxs-lookup"><span data-stu-id="fbee6-158">Use to troubleshoot deadlocks, lock time-out, and lock escalation events.</span></span>|<span data-ttu-id="fbee6-159">**Blocked Process Report**</span><span class="sxs-lookup"><span data-stu-id="fbee6-159">**Blocked Process Report**</span></span><br /><br /> <span data-ttu-id="fbee6-160">**SP:StmtCompleted**</span><span class="sxs-lookup"><span data-stu-id="fbee6-160">**SP:StmtCompleted**</span></span><br /><br /> <span data-ttu-id="fbee6-161">**SP:StmtStarting**</span><span class="sxs-lookup"><span data-stu-id="fbee6-161">**SP:StmtStarting**</span></span><br /><br /> <span data-ttu-id="fbee6-162">**SQL:StmtCompleted**</span><span class="sxs-lookup"><span data-stu-id="fbee6-162">**SQL:StmtCompleted**</span></span><br /><br /> <span data-ttu-id="fbee6-163">**SQL:StmtStarting**</span><span class="sxs-lookup"><span data-stu-id="fbee6-163">**SQL:StmtStarting**</span></span><br /><br /> <span data-ttu-id="fbee6-164">**Deadlock Graph**</span><span class="sxs-lookup"><span data-stu-id="fbee6-164">**Deadlock Graph**</span></span><br /><br /> <span data-ttu-id="fbee6-165">**Lock:Canceled**</span><span class="sxs-lookup"><span data-stu-id="fbee6-165">**Lock:Cancel**</span></span><br /><br /> <span data-ttu-id="fbee6-166">**Lock:Deadlock**</span><span class="sxs-lookup"><span data-stu-id="fbee6-166">**Lock:Deadlock**</span></span><br /><br /> <span data-ttu-id="fbee6-167">**Lock:Deadlock Chain**</span><span class="sxs-lookup"><span data-stu-id="fbee6-167">**Lock:Deadlock Chain**</span></span><br /><br /> <span data-ttu-id="fbee6-168">**Lock:Escalation**</span><span class="sxs-lookup"><span data-stu-id="fbee6-168">**Lock:Escalation**</span></span><br /><br /> <span data-ttu-id="fbee6-169">**Lock:Timeout (timeout>0)**</span><span class="sxs-lookup"><span data-stu-id="fbee6-169">**Lock:Timeout (timeout>0)**</span></span>|  
|<span data-ttu-id="fbee6-170">TSQL_Replay</span><span class="sxs-lookup"><span data-stu-id="fbee6-170">TSQL_Replay</span></span>|<span data-ttu-id="fbee6-171">Capture des informations détaillées sur les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] , qui sont nécessaires si la trace doit être réexécutée.</span><span class="sxs-lookup"><span data-stu-id="fbee6-171">Captures detailed information about [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that is required if the trace will be replayed.</span></span> <span data-ttu-id="fbee6-172">Permet d'effectuer un paramétrage itératif, tel qu'un test d'évaluation.</span><span class="sxs-lookup"><span data-stu-id="fbee6-172">Use to perform iterative tuning, such as benchmark testing.</span></span>|<span data-ttu-id="fbee6-173">**CursorClose**</span><span class="sxs-lookup"><span data-stu-id="fbee6-173">**CursorClose**</span></span><br /><br /> <span data-ttu-id="fbee6-174">**CursorExecute**</span><span class="sxs-lookup"><span data-stu-id="fbee6-174">**CursorExecute**</span></span><br /><br /> <span data-ttu-id="fbee6-175">**CursorOpen**</span><span class="sxs-lookup"><span data-stu-id="fbee6-175">**CursorOpen**</span></span><br /><br /> <span data-ttu-id="fbee6-176">**CursorPrepare**</span><span class="sxs-lookup"><span data-stu-id="fbee6-176">**CursorPrepare**</span></span><br /><br /> <span data-ttu-id="fbee6-177">**CursorUnprepare**</span><span class="sxs-lookup"><span data-stu-id="fbee6-177">**CursorUnprepare**</span></span><br /><br /> <span data-ttu-id="fbee6-178">**Audit Login**</span><span class="sxs-lookup"><span data-stu-id="fbee6-178">**Audit Login**</span></span><br /><br /> <span data-ttu-id="fbee6-179">**Audit Logout**</span><span class="sxs-lookup"><span data-stu-id="fbee6-179">**Audit Logout**</span></span><br /><br /> <span data-ttu-id="fbee6-180">**Connexion existante**</span><span class="sxs-lookup"><span data-stu-id="fbee6-180">**Existing Connection**</span></span><br /><br /> <span data-ttu-id="fbee6-181">**RPC Output Parameter**</span><span class="sxs-lookup"><span data-stu-id="fbee6-181">**RPC Output Parameter**</span></span><br /><br /> <span data-ttu-id="fbee6-182">**RPC:Completed**</span><span class="sxs-lookup"><span data-stu-id="fbee6-182">**RPC:Completed**</span></span><br /><br /> <span data-ttu-id="fbee6-183">**RPC:Starting**</span><span class="sxs-lookup"><span data-stu-id="fbee6-183">**RPC:Starting**</span></span><br /><br /> <span data-ttu-id="fbee6-184">**Exec Prepared SQL**</span><span class="sxs-lookup"><span data-stu-id="fbee6-184">**Exec Prepared SQL**</span></span><br /><br /> <span data-ttu-id="fbee6-185">**Prepare SQL**</span><span class="sxs-lookup"><span data-stu-id="fbee6-185">**Prepare SQL**</span></span><br /><br /> <span data-ttu-id="fbee6-186">**SQL:BatchCompleted**</span><span class="sxs-lookup"><span data-stu-id="fbee6-186">**SQL:BatchCompleted**</span></span><br /><br /> <span data-ttu-id="fbee6-187">**SQL:BatchStarting**</span><span class="sxs-lookup"><span data-stu-id="fbee6-187">**SQL:BatchStarting**</span></span>|  
|<span data-ttu-id="fbee6-188">TSQL_SPs</span><span class="sxs-lookup"><span data-stu-id="fbee6-188">TSQL_SPs</span></span>|<span data-ttu-id="fbee6-189">Capture des informations détaillées sur toutes les procédures stockées en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="fbee6-189">Captures detailed information about all executing stored procedures.</span></span> <span data-ttu-id="fbee6-190">Permet d'analyser les étapes composantes des procédures stockées.</span><span class="sxs-lookup"><span data-stu-id="fbee6-190">Use to analyze the component steps of stored procedures.</span></span> <span data-ttu-id="fbee6-191">Ajoutez l’événement **SP:Recompile** si vous pensez que des procédures sont recompilées.</span><span class="sxs-lookup"><span data-stu-id="fbee6-191">Add the **SP:Recompile** event if you suspect that procedures are being recompiled.</span></span>|<span data-ttu-id="fbee6-192">**Audit Login**</span><span class="sxs-lookup"><span data-stu-id="fbee6-192">**Audit Login**</span></span><br /><br /> <span data-ttu-id="fbee6-193">**Audit Logout**</span><span class="sxs-lookup"><span data-stu-id="fbee6-193">**Audit Logout**</span></span><br /><br /> <span data-ttu-id="fbee6-194">**ExistingConnection**</span><span class="sxs-lookup"><span data-stu-id="fbee6-194">**ExistingConnection**</span></span><br /><br /> <span data-ttu-id="fbee6-195">**RPC:Starting**</span><span class="sxs-lookup"><span data-stu-id="fbee6-195">**RPC:Starting**</span></span><br /><br /> <span data-ttu-id="fbee6-196">**SP:Completed**</span><span class="sxs-lookup"><span data-stu-id="fbee6-196">**SP:Completed**</span></span><br /><br /> <span data-ttu-id="fbee6-197">**SP:Starting**</span><span class="sxs-lookup"><span data-stu-id="fbee6-197">**SP:Starting**</span></span><br /><br /> <span data-ttu-id="fbee6-198">**SP:StmtStarting**</span><span class="sxs-lookup"><span data-stu-id="fbee6-198">**SP:StmtStarting**</span></span><br /><br /> <span data-ttu-id="fbee6-199">**SQL:BatchStarting**</span><span class="sxs-lookup"><span data-stu-id="fbee6-199">**SQL:BatchStarting**</span></span>|  
|<span data-ttu-id="fbee6-200">Réglage</span><span class="sxs-lookup"><span data-stu-id="fbee6-200">Tuning</span></span>|<span data-ttu-id="fbee6-201">Capture des informations sur l'exécution des procédures stockées et des traitements [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="fbee6-201">Captures information about stored procedures and [!INCLUDE[tsql](../../includes/tsql-md.md)] batch execution.</span></span> <span data-ttu-id="fbee6-202">Permet de produire des résultats de trace que l'Assistant Paramétrage du [!INCLUDE[ssDE](../../includes/ssde-md.md)] peut utiliser comme charge de travail pour régler les bases de données.</span><span class="sxs-lookup"><span data-stu-id="fbee6-202">Use to produce trace output that [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor can use as a workload to tune databases.</span></span>|<span data-ttu-id="fbee6-203">**RPC:Completed**</span><span class="sxs-lookup"><span data-stu-id="fbee6-203">**RPC:Completed**</span></span><br /><br /> <span data-ttu-id="fbee6-204">**SP:StmtCompleted**</span><span class="sxs-lookup"><span data-stu-id="fbee6-204">**SP:StmtCompleted**</span></span><br /><br /> <span data-ttu-id="fbee6-205">**SQL:BatchCompleted**</span><span class="sxs-lookup"><span data-stu-id="fbee6-205">**SQL:BatchCompleted**</span></span>|  
  
 <span data-ttu-id="fbee6-206">Pour plus d’informations sur les classes d’événements, consultez [SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md).</span><span class="sxs-lookup"><span data-stu-id="fbee6-206">For information about the event classes, see [SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md).</span></span>  
  
## <a name="default-template"></a><span data-ttu-id="fbee6-207">Modèle par défaut</span><span class="sxs-lookup"><span data-stu-id="fbee6-207">Default Template</span></span>  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="fbee6-208">définit automatiquement le modèle **Standard** comme modèle par défaut appliqué aux nouvelles traces.</span><span class="sxs-lookup"><span data-stu-id="fbee6-208">automatically designates the **Standard** template as the default template applied to any new trace.</span></span> <span data-ttu-id="fbee6-209">Toutefois, vous pouvez remplacer le modèle par défaut par n'importe quel autre modèle prédéfini ou défini par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="fbee6-209">However you can change the default template to any other predefined or user-defined template.</span></span> <span data-ttu-id="fbee6-210">Pour modifier le modèle par défaut, cochez la case **Utiliser comme modèle par défaut pour le type de serveur sélectionné** lorsque vous créez ou modifiez un modèle en utilisant l’onglet **Général** de la boîte de dialogue **Propriétés du modèle de trace** .</span><span class="sxs-lookup"><span data-stu-id="fbee6-210">To change the default template, select the **Use as a default template for selected server type** check box when you create or edit a template by using the **General** tab of the **Trace Template Properties** dialog box.</span></span>  
  
 <span data-ttu-id="fbee6-211">Pour accéder à la boîte de dialogue **Propriétés du modèle de trace**, dans le menu [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **Fichier**, choisissez **Modèles** et cliquez sur **Nouveau modèle** ou **Modifier le modèle**.</span><span class="sxs-lookup"><span data-stu-id="fbee6-211">To navigate to the **Trace Template Properties** dialog box, on the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **File** menu, choose **Templates**, and then click **New Template** or **Edit Template**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fbee6-212">Le modèle par défaut est spécifique à un type de serveur donné.</span><span class="sxs-lookup"><span data-stu-id="fbee6-212">The default template is specific for a given server type.</span></span> <span data-ttu-id="fbee6-213">Le remplacement du modèle par défaut d'un type de serveur n'affecte pas le modèle par défaut d'un autre type de serveur.</span><span class="sxs-lookup"><span data-stu-id="fbee6-213">Changing the default for one server type does not affect the default template for any other server type.</span></span> <span data-ttu-id="fbee6-214">Pour plus d’informations sur le paramétrage du modèle par défaut d’un serveur, consultez [Définir les valeurs par défaut des définitions de trace &#40;SQL Server Profiler&#41;](set-trace-definition-defaults-sql-server-profiler.md).</span><span class="sxs-lookup"><span data-stu-id="fbee6-214">For more information about setting a default template for a specific server, see [Set Trace Definition Defaults &#40;SQL Server Profiler&#41;](set-trace-definition-defaults-sql-server-profiler.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbee6-215">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fbee6-215">See Also</span></span>  
 <span data-ttu-id="fbee6-216">[Créer un modèle de trace &#40;SQL Server Profiler&#41;](create-a-trace-template-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="fbee6-216">[Create a Trace Template &#40;SQL Server Profiler&#41;](create-a-trace-template-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="fbee6-217">[Modifier un modèle de trace &#40;SQL Server Profiler&#41;](../../database-engine/modify-a-trace-template-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="fbee6-217">[Modify a Trace Template &#40;SQL Server Profiler&#41;](../../database-engine/modify-a-trace-template-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="fbee6-218">[Exporter un modèle de trace &#40;SQL Server Profiler&#41;](export-a-trace-template-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="fbee6-218">[Export a Trace Template &#40;SQL Server Profiler&#41;](export-a-trace-template-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="fbee6-219">Importer un modèle de trace &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="fbee6-219">Import a Trace Template &#40;SQL Server Profiler&#41;</span></span>](import-a-trace-template-sql-server-profiler.md)  
  
  