---
title: Showplan XML, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Showplan XML event class
ms.assetid: 8e22de84-8890-414a-93e4-aebfaa057d7f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 93f00d2bfdcee43d22f54544d1aecfb4ceb9e394
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612368"
---
# <a name="showplan-xml-event-class"></a><span data-ttu-id="2409e-102">Showplan XML (classe d'événements)</span><span class="sxs-lookup"><span data-stu-id="2409e-102">Showplan XML Event Class</span></span>
  <span data-ttu-id="2409e-103">La classe d’événements Showplan XML intervient quand [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] exécute une instruction SQL.</span><span class="sxs-lookup"><span data-stu-id="2409e-103">The Showplan XML event class occurs when [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] executes an SQL statement.</span></span> <span data-ttu-id="2409e-104">Incluez la classe d'événements Showplan XML pour identifier les opérateurs Showplan.</span><span class="sxs-lookup"><span data-stu-id="2409e-104">Include the Showplan XML event class to identify the Showplan operators.</span></span> <span data-ttu-id="2409e-105">Cette classe d'événements stocke chaque événement sous la forme d'un document XML bien défini.</span><span class="sxs-lookup"><span data-stu-id="2409e-105">This event class stores each event as a well-defined XML document.</span></span>  
  
 <span data-ttu-id="2409e-106">Lorsque la classe d'événements Showplan XML est incluse dans une trace, la charge de gestion induite compromet les performances de façon significative.</span><span class="sxs-lookup"><span data-stu-id="2409e-106">When the Showplan XML event class is included in a trace, the amount of overhead will significantly impede performance.</span></span> <span data-ttu-id="2409e-107">Showplan XML stocke un plan de requête qui est créé lors de l'optimisation de la requête.</span><span class="sxs-lookup"><span data-stu-id="2409e-107">Showplan XML stores a query plan that is created when the query is optimized.</span></span> <span data-ttu-id="2409e-108">Pour minimiser la charge de gestion associée, limitez l'utilisation de cette classe d'événements aux traces qui analysent des problèmes spécifiques pendant de brèves périodes de temps.</span><span class="sxs-lookup"><span data-stu-id="2409e-108">To minimize the overhead incurred, limit use of this event class to traces that monitor specific problems for brief periods of time.</span></span>  
  
 <span data-ttu-id="2409e-109">Les documents Showplan XML ont un schéma qui leur est associé.</span><span class="sxs-lookup"><span data-stu-id="2409e-109">The Showplan XML documents have a schema associated with them.</span></span> <span data-ttu-id="2409e-110">Ce schéma se trouve sur le [site web de Microsoft](https://go.microsoft.com/fwlink/?LinkId=41740) ou dans votre installation [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2409e-110">This schema can be found at the [Microsoft Web Site](https://go.microsoft.com/fwlink/?LinkId=41740), or as part of your [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.</span></span>  
  
## <a name="showplan-xml-event-class-data-columns"></a><span data-ttu-id="2409e-111">Colonnes de données de la classe d'événements Showplan XML</span><span class="sxs-lookup"><span data-stu-id="2409e-111">Showplan XML Event Class Data Columns</span></span>  
  
|<span data-ttu-id="2409e-112">Nom de la colonne de données</span><span class="sxs-lookup"><span data-stu-id="2409e-112">Data column name</span></span>|<span data-ttu-id="2409e-113">Type de données</span><span class="sxs-lookup"><span data-stu-id="2409e-113">Data type</span></span>|<span data-ttu-id="2409e-114">Description</span><span class="sxs-lookup"><span data-stu-id="2409e-114">Description</span></span>|<span data-ttu-id="2409e-115">ID de la colonne</span><span class="sxs-lookup"><span data-stu-id="2409e-115">Column ID</span></span>|<span data-ttu-id="2409e-116">Filtrable</span><span class="sxs-lookup"><span data-stu-id="2409e-116">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="2409e-117">ApplicationName</span><span class="sxs-lookup"><span data-stu-id="2409e-117">ApplicationName</span></span>|`nvarchar`|<span data-ttu-id="2409e-118">Nom de l'application cliente qui a créé la connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2409e-118">Name of the client application that created the connection to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2409e-119">Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.</span><span class="sxs-lookup"><span data-stu-id="2409e-119">This column is populated with the values passed by the application rather than the displayed name of the program.</span></span>|<span data-ttu-id="2409e-120">10</span><span class="sxs-lookup"><span data-stu-id="2409e-120">10</span></span>|<span data-ttu-id="2409e-121">Oui</span><span class="sxs-lookup"><span data-stu-id="2409e-121">Yes</span></span>|  
|<span data-ttu-id="2409e-122">BinaryData</span><span class="sxs-lookup"><span data-stu-id="2409e-122">BinaryData</span></span>|`image`|<span data-ttu-id="2409e-123">Coût estimé de la requête.</span><span class="sxs-lookup"><span data-stu-id="2409e-123">Estimated cost of the query.</span></span>|<span data-ttu-id="2409e-124">2</span><span class="sxs-lookup"><span data-stu-id="2409e-124">2</span></span>|<span data-ttu-id="2409e-125">Non</span><span class="sxs-lookup"><span data-stu-id="2409e-125">No</span></span>|  
|<span data-ttu-id="2409e-126">ClientProcessID</span><span class="sxs-lookup"><span data-stu-id="2409e-126">ClientProcessID</span></span>|`int`|<span data-ttu-id="2409e-127">ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente.</span><span class="sxs-lookup"><span data-stu-id="2409e-127">ID assigned by the host computer to the process where the client application is running.</span></span> <span data-ttu-id="2409e-128">Cette colonne de données est remplie si l'ID du processus du client est fourni par le client.</span><span class="sxs-lookup"><span data-stu-id="2409e-128">This data column is populated if the client process ID is provided by the client.</span></span>|<span data-ttu-id="2409e-129">9</span><span class="sxs-lookup"><span data-stu-id="2409e-129">9</span></span>|<span data-ttu-id="2409e-130">Oui</span><span class="sxs-lookup"><span data-stu-id="2409e-130">Yes</span></span>|  
|<span data-ttu-id="2409e-131">DatabaseID</span><span class="sxs-lookup"><span data-stu-id="2409e-131">DatabaseID</span></span>|`int`|<span data-ttu-id="2409e-132">ID de la base de données spécifiée par l’instruction USE *database* ou ID de la base de données par défaut si aucune instruction USE *database*n’a été émise pour une instance donnée.</span><span class="sxs-lookup"><span data-stu-id="2409e-132">ID of the database specified by the USE *database* statement or the default database if no USE *database*statement has been issued for a given instance.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="2409e-133">affiche le nom de la base de données si la colonne de données ServerName est capturée dans la trace et que le serveur est disponible.</span><span class="sxs-lookup"><span data-stu-id="2409e-133">displays the name of the database if the ServerName data column is captured in the trace and the server is available.</span></span> <span data-ttu-id="2409e-134">Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.</span><span class="sxs-lookup"><span data-stu-id="2409e-134">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="2409e-135">3</span><span class="sxs-lookup"><span data-stu-id="2409e-135">3</span></span>|<span data-ttu-id="2409e-136">Oui</span><span class="sxs-lookup"><span data-stu-id="2409e-136">Yes</span></span>|  
|<span data-ttu-id="2409e-137">nom_base_de_données</span><span class="sxs-lookup"><span data-stu-id="2409e-137">DatabaseName</span></span>|`nvarchar`|<span data-ttu-id="2409e-138">Nom de la base de données.</span><span class="sxs-lookup"><span data-stu-id="2409e-138">Name of the database.</span></span>|<span data-ttu-id="2409e-139">35</span><span class="sxs-lookup"><span data-stu-id="2409e-139">35</span></span>|<span data-ttu-id="2409e-140">Non</span><span class="sxs-lookup"><span data-stu-id="2409e-140">No</span></span>|  
|<span data-ttu-id="2409e-141">Classe d'événements</span><span class="sxs-lookup"><span data-stu-id="2409e-141">Event Class</span></span>|`int`|<span data-ttu-id="2409e-142">Type d'événement = 122.</span><span class="sxs-lookup"><span data-stu-id="2409e-142">Type of Event = 122.</span></span>|<span data-ttu-id="2409e-143">27</span><span class="sxs-lookup"><span data-stu-id="2409e-143">27</span></span>|<span data-ttu-id="2409e-144">Non</span><span class="sxs-lookup"><span data-stu-id="2409e-144">No</span></span>|  
|<span data-ttu-id="2409e-145">EventSequence</span><span class="sxs-lookup"><span data-stu-id="2409e-145">EventSequence</span></span>|`int`|<span data-ttu-id="2409e-146">Séquence d'un événement donné au sein de la demande.</span><span class="sxs-lookup"><span data-stu-id="2409e-146">The sequence of a given event within the request.</span></span>|<span data-ttu-id="2409e-147">51</span><span class="sxs-lookup"><span data-stu-id="2409e-147">51</span></span>|<span data-ttu-id="2409e-148">Non</span><span class="sxs-lookup"><span data-stu-id="2409e-148">No</span></span>|  
|<span data-ttu-id="2409e-149">GroupID</span><span class="sxs-lookup"><span data-stu-id="2409e-149">GroupID</span></span>|`int`|<span data-ttu-id="2409e-150">ID du groupe de charges de travail où l'événement Trace SQL se déclenche.</span><span class="sxs-lookup"><span data-stu-id="2409e-150">ID of the workload group where the SQL Trace event fires.</span></span>|<span data-ttu-id="2409e-151">66</span><span class="sxs-lookup"><span data-stu-id="2409e-151">66</span></span>|<span data-ttu-id="2409e-152">Oui</span><span class="sxs-lookup"><span data-stu-id="2409e-152">Yes</span></span>|  
|<span data-ttu-id="2409e-153">HostName</span><span class="sxs-lookup"><span data-stu-id="2409e-153">HostName</span></span>|`nvarchar`|<span data-ttu-id="2409e-154">Nom de l'ordinateur sur lequel le client est exécuté.</span><span class="sxs-lookup"><span data-stu-id="2409e-154">Name of the computer on which the client is running.</span></span> <span data-ttu-id="2409e-155">Cette colonne de données est remplie si le nom de l'hôte est fourni par le client.</span><span class="sxs-lookup"><span data-stu-id="2409e-155">This data column is populated if the host name is provided by the client.</span></span> <span data-ttu-id="2409e-156">Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.</span><span class="sxs-lookup"><span data-stu-id="2409e-156">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="2409e-157">8</span><span class="sxs-lookup"><span data-stu-id="2409e-157">8</span></span>|<span data-ttu-id="2409e-158">Oui</span><span class="sxs-lookup"><span data-stu-id="2409e-158">Yes</span></span>|  
|<span data-ttu-id="2409e-159">Integer Data</span><span class="sxs-lookup"><span data-stu-id="2409e-159">Integer Data</span></span>|`integer`|<span data-ttu-id="2409e-160">Estimation du nombre de lignes retournées</span><span class="sxs-lookup"><span data-stu-id="2409e-160">Estimated number of rows returned.</span></span>|<span data-ttu-id="2409e-161">25</span><span class="sxs-lookup"><span data-stu-id="2409e-161">25</span></span>|<span data-ttu-id="2409e-162">Oui</span><span class="sxs-lookup"><span data-stu-id="2409e-162">Yes</span></span>|  
|<span data-ttu-id="2409e-163">IsSystem</span><span class="sxs-lookup"><span data-stu-id="2409e-163">IsSystem</span></span>|`int`|<span data-ttu-id="2409e-164">Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2409e-164">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="2409e-165">1 = système, 0 = utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2409e-165">1 = system, 0 = user.</span></span>|<span data-ttu-id="2409e-166">60</span><span class="sxs-lookup"><span data-stu-id="2409e-166">60</span></span>|<span data-ttu-id="2409e-167">Oui</span><span class="sxs-lookup"><span data-stu-id="2409e-167">Yes</span></span>|  
|<span data-ttu-id="2409e-168">LineNumber</span><span class="sxs-lookup"><span data-stu-id="2409e-168">LineNumber</span></span>|`int`|<span data-ttu-id="2409e-169">Affiche le numéro de la ligne qui contient l'erreur.</span><span class="sxs-lookup"><span data-stu-id="2409e-169">Displays the number of the line containing the error.</span></span>|<span data-ttu-id="2409e-170">5</span><span class="sxs-lookup"><span data-stu-id="2409e-170">5</span></span>|<span data-ttu-id="2409e-171">Oui</span><span class="sxs-lookup"><span data-stu-id="2409e-171">Yes</span></span>|  
|<span data-ttu-id="2409e-172">LoginName</span><span class="sxs-lookup"><span data-stu-id="2409e-172">LoginName</span></span>|`nvarchar`|<span data-ttu-id="2409e-173">Nom de la connexion de l'utilisateur (soit la connexion de sécurité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , soit les informations d'identification de connexion [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows au format DOMAINE\nom_utilisateur).</span><span class="sxs-lookup"><span data-stu-id="2409e-173">Name of the login of the user (either [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security login or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows login credentials in the form of DOMAIN\username).</span></span>|<span data-ttu-id="2409e-174">11</span><span class="sxs-lookup"><span data-stu-id="2409e-174">11</span></span>|<span data-ttu-id="2409e-175">Oui</span><span class="sxs-lookup"><span data-stu-id="2409e-175">Yes</span></span>|  
|<span data-ttu-id="2409e-176">LoginSID</span><span class="sxs-lookup"><span data-stu-id="2409e-176">LoginSID</span></span>|`image`|<span data-ttu-id="2409e-177">Numéro d'identification de sécurité (SID) de l'utilisateur connecté.</span><span class="sxs-lookup"><span data-stu-id="2409e-177">Security identification number (SID) of the logged-in user.</span></span> <span data-ttu-id="2409e-178">Vous pouvez trouver ces informations dans l'affichage catalogue sys.server_principals.</span><span class="sxs-lookup"><span data-stu-id="2409e-178">You can find this information in the sys.server_principals catalog view.</span></span> <span data-ttu-id="2409e-179">Chaque connexion possède un SID unique au niveau du serveur.</span><span class="sxs-lookup"><span data-stu-id="2409e-179">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="2409e-180">41</span><span class="sxs-lookup"><span data-stu-id="2409e-180">41</span></span>|<span data-ttu-id="2409e-181">Non</span><span class="sxs-lookup"><span data-stu-id="2409e-181">No</span></span>|  
|<span data-ttu-id="2409e-182">NestLevel</span><span class="sxs-lookup"><span data-stu-id="2409e-182">NestLevel</span></span>|`int`|<span data-ttu-id="2409e-183">Entier représentant les données retournées par @@NESTLEVEL.</span><span class="sxs-lookup"><span data-stu-id="2409e-183">Integer representing the data returned by @@NESTLEVEL.</span></span>|<span data-ttu-id="2409e-184">29</span><span class="sxs-lookup"><span data-stu-id="2409e-184">29</span></span>|<span data-ttu-id="2409e-185">Oui</span><span class="sxs-lookup"><span data-stu-id="2409e-185">Yes</span></span>|  
|<span data-ttu-id="2409e-186">NTDomainName</span><span class="sxs-lookup"><span data-stu-id="2409e-186">NTDomainName</span></span>|`nvarchar`|<span data-ttu-id="2409e-187">Domaine Windows auquel appartient l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2409e-187">Windows domain to which the user belongs.</span></span>|<span data-ttu-id="2409e-188">7</span><span class="sxs-lookup"><span data-stu-id="2409e-188">7</span></span>|<span data-ttu-id="2409e-189">Oui</span><span class="sxs-lookup"><span data-stu-id="2409e-189">Yes</span></span>|  
|<span data-ttu-id="2409e-190">ObjectID</span><span class="sxs-lookup"><span data-stu-id="2409e-190">ObjectID</span></span>|`int`|<span data-ttu-id="2409e-191">ID affecté à l'objet par le système.</span><span class="sxs-lookup"><span data-stu-id="2409e-191">System-assigned ID of the object.</span></span>|<span data-ttu-id="2409e-192">22</span><span class="sxs-lookup"><span data-stu-id="2409e-192">22</span></span>|<span data-ttu-id="2409e-193">Oui</span><span class="sxs-lookup"><span data-stu-id="2409e-193">Yes</span></span>|  
|<span data-ttu-id="2409e-194">ObjectName</span><span class="sxs-lookup"><span data-stu-id="2409e-194">ObjectName</span></span>|`nvarchar`|<span data-ttu-id="2409e-195">Nom de l'objet référencé.</span><span class="sxs-lookup"><span data-stu-id="2409e-195">Name of the object being referenced.</span></span>|<span data-ttu-id="2409e-196">34</span><span class="sxs-lookup"><span data-stu-id="2409e-196">34</span></span>|<span data-ttu-id="2409e-197">Oui</span><span class="sxs-lookup"><span data-stu-id="2409e-197">Yes</span></span>|  
|<span data-ttu-id="2409e-198">ObjectType</span><span class="sxs-lookup"><span data-stu-id="2409e-198">ObjectType</span></span>|`int`|<span data-ttu-id="2409e-199">Valeur représentant le type de l'objet qui intervient dans l'événement.</span><span class="sxs-lookup"><span data-stu-id="2409e-199">Value representing the type of the object involved in the event.</span></span> <span data-ttu-id="2409e-200">Cette valeur correspond à la colonne type de l'affichage catalogue sys.objects.</span><span class="sxs-lookup"><span data-stu-id="2409e-200">This value corresponds to the type column in the sys.objects catalog view.</span></span> <span data-ttu-id="2409e-201">Pour connaître les valeurs, consultez [Colonne d’événements de trace ObjectType](objecttype-trace-event-column.md).</span><span class="sxs-lookup"><span data-stu-id="2409e-201">For values, see [ObjectType Trace Event Column](objecttype-trace-event-column.md).</span></span>|<span data-ttu-id="2409e-202">28</span><span class="sxs-lookup"><span data-stu-id="2409e-202">28</span></span>|<span data-ttu-id="2409e-203">Oui</span><span class="sxs-lookup"><span data-stu-id="2409e-203">Yes</span></span>|  
|<span data-ttu-id="2409e-204">RequestID</span><span class="sxs-lookup"><span data-stu-id="2409e-204">RequestID</span></span>|`int`|<span data-ttu-id="2409e-205">ID de la demande contenant l'instruction.</span><span class="sxs-lookup"><span data-stu-id="2409e-205">ID of the request containing the statement.</span></span>|<span data-ttu-id="2409e-206">49</span><span class="sxs-lookup"><span data-stu-id="2409e-206">49</span></span>|<span data-ttu-id="2409e-207">Oui</span><span class="sxs-lookup"><span data-stu-id="2409e-207">Yes</span></span>|  
|<span data-ttu-id="2409e-208">ServerName</span><span class="sxs-lookup"><span data-stu-id="2409e-208">ServerName</span></span>|`nvarchar`|<span data-ttu-id="2409e-209">Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.</span><span class="sxs-lookup"><span data-stu-id="2409e-209">Name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="2409e-210">26</span><span class="sxs-lookup"><span data-stu-id="2409e-210">26</span></span>|<span data-ttu-id="2409e-211">Non</span><span class="sxs-lookup"><span data-stu-id="2409e-211">No</span></span>|  
|<span data-ttu-id="2409e-212">SessionLoginName</span><span class="sxs-lookup"><span data-stu-id="2409e-212">SessionLoginName</span></span>|`nvarchar`|<span data-ttu-id="2409e-213">Nom de connexion de l'utilisateur à l'origine de la session.</span><span class="sxs-lookup"><span data-stu-id="2409e-213">Login name of the user who originated the session.</span></span> <span data-ttu-id="2409e-214">Par exemple, si vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en utilisant le nom Connexion1 et que vous exécutez une instruction en tant que Connexion2, SessionLoginName affiche Connexion1 et LoginName, Connexion2.</span><span class="sxs-lookup"><span data-stu-id="2409e-214">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, SessionLoginName shows Login1 and LoginName shows Login2.</span></span> <span data-ttu-id="2409e-215">Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Windows.</span><span class="sxs-lookup"><span data-stu-id="2409e-215">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows logins.</span></span>|<span data-ttu-id="2409e-216">64</span><span class="sxs-lookup"><span data-stu-id="2409e-216">64</span></span>|<span data-ttu-id="2409e-217">Oui</span><span class="sxs-lookup"><span data-stu-id="2409e-217">Yes</span></span>|  
|<span data-ttu-id="2409e-218">SPID</span><span class="sxs-lookup"><span data-stu-id="2409e-218">SPID</span></span>|`int`|<span data-ttu-id="2409e-219">ID de la session au cours de laquelle l'événement s'est produit.</span><span class="sxs-lookup"><span data-stu-id="2409e-219">ID of the session on which the event occurred.</span></span>|<span data-ttu-id="2409e-220">12</span><span class="sxs-lookup"><span data-stu-id="2409e-220">12</span></span>|<span data-ttu-id="2409e-221">Oui</span><span class="sxs-lookup"><span data-stu-id="2409e-221">Yes</span></span>|  
|<span data-ttu-id="2409e-222">StartTime</span><span class="sxs-lookup"><span data-stu-id="2409e-222">StartTime</span></span>|`datetime`|<span data-ttu-id="2409e-223">Heure à laquelle a débuté l'événement, si elle est connue.</span><span class="sxs-lookup"><span data-stu-id="2409e-223">Time at which the event started, if available.</span></span>|<span data-ttu-id="2409e-224">14</span><span class="sxs-lookup"><span data-stu-id="2409e-224">14</span></span>|<span data-ttu-id="2409e-225">Oui</span><span class="sxs-lookup"><span data-stu-id="2409e-225">Yes</span></span>|  
|<span data-ttu-id="2409e-226">TextData</span><span class="sxs-lookup"><span data-stu-id="2409e-226">TextData</span></span>|`ntext`|<span data-ttu-id="2409e-227">Valeur texte qui dépend de la classe d'événements capturée dans la trace.</span><span class="sxs-lookup"><span data-stu-id="2409e-227">Text value dependent on the event class captured in the trace.</span></span>|<span data-ttu-id="2409e-228">1</span><span class="sxs-lookup"><span data-stu-id="2409e-228">1</span></span>|<span data-ttu-id="2409e-229">Oui</span><span class="sxs-lookup"><span data-stu-id="2409e-229">Yes</span></span>|  
|<span data-ttu-id="2409e-230">TransactionID</span><span class="sxs-lookup"><span data-stu-id="2409e-230">TransactionID</span></span>|`bigint`|<span data-ttu-id="2409e-231">ID affecté par le système à la transaction.</span><span class="sxs-lookup"><span data-stu-id="2409e-231">System-assigned ID of the transaction.</span></span>|<span data-ttu-id="2409e-232">4</span><span class="sxs-lookup"><span data-stu-id="2409e-232">4</span></span>|<span data-ttu-id="2409e-233">Oui</span><span class="sxs-lookup"><span data-stu-id="2409e-233">Yes</span></span>|  
|<span data-ttu-id="2409e-234">XactSequence</span><span class="sxs-lookup"><span data-stu-id="2409e-234">XactSequence</span></span>|`bigint`|<span data-ttu-id="2409e-235">Jeton utilisé pour décrire la transaction en cours.</span><span class="sxs-lookup"><span data-stu-id="2409e-235">Token used to describe the current transaction.</span></span>|<span data-ttu-id="2409e-236">50</span><span class="sxs-lookup"><span data-stu-id="2409e-236">50</span></span>|<span data-ttu-id="2409e-237">Oui</span><span class="sxs-lookup"><span data-stu-id="2409e-237">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2409e-238">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2409e-238">See Also</span></span>  
 <span data-ttu-id="2409e-239">[Événements étendus](../extended-events/extended-events.md) </span><span class="sxs-lookup"><span data-stu-id="2409e-239">[Extended Events](../extended-events/extended-events.md) </span></span>  
 <span data-ttu-id="2409e-240">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2409e-240">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 [<span data-ttu-id="2409e-241">Guide de référence des opérateurs Showplan logiques et physiques</span><span class="sxs-lookup"><span data-stu-id="2409e-241">Showplan Logical and Physical Operators Reference</span></span>](../showplan-logical-and-physical-operators-reference.md)  
  
  