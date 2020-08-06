---
title: Audit Server Operation, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Audit Server Operation event class
ms.assetid: 6cc3dbb9-817e-4329-9f45-c3adcff3b511
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3a3359de449dcce4a976dec2debd9b5be99addd2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87600041"
---
# <a name="audit-server-operation-event-class"></a><span data-ttu-id="850da-102">Audit Server Operation (classe d'événements)</span><span class="sxs-lookup"><span data-stu-id="850da-102">Audit Server Operation Event Class</span></span>
  <span data-ttu-id="850da-103">La classe d'événements **Audit Server Operation** se produit lorsque des opérations d'audit de sécurité sont utilisées, telles que la modification des paramètres, des ressources, de l'accès externe ou de l'autorisation.</span><span class="sxs-lookup"><span data-stu-id="850da-103">The **Audit Server Operation** event class occurs when Security Audit operations such as altering settings, resources, external access, or authorization are used.</span></span>  
  
## <a name="audit-server-operation-event-class-data-columns"></a><span data-ttu-id="850da-104">Colonnes de données de la classe d'événements Audit Server Operation</span><span class="sxs-lookup"><span data-stu-id="850da-104">Audit Server Operation Event Class Data Columns</span></span>  
  
|<span data-ttu-id="850da-105">Nom de la colonne de données</span><span class="sxs-lookup"><span data-stu-id="850da-105">Data column name</span></span>|<span data-ttu-id="850da-106">Type de données</span><span class="sxs-lookup"><span data-stu-id="850da-106">Data type</span></span>|<span data-ttu-id="850da-107">Description</span><span class="sxs-lookup"><span data-stu-id="850da-107">Description</span></span>|<span data-ttu-id="850da-108">ID de la colonne</span><span class="sxs-lookup"><span data-stu-id="850da-108">Column ID</span></span>|<span data-ttu-id="850da-109">Filtrable</span><span class="sxs-lookup"><span data-stu-id="850da-109">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="850da-110">**ApplicationName**</span><span class="sxs-lookup"><span data-stu-id="850da-110">**ApplicationName**</span></span>|<span data-ttu-id="850da-111">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="850da-111">**nvarchar**</span></span>|<span data-ttu-id="850da-112">Nom de l’application cliente qui a créé la connexion à une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="850da-112">Name of the client application that created the connection to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="850da-113">Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.</span><span class="sxs-lookup"><span data-stu-id="850da-113">This column is populated with the values passed by the application rather than the displayed name of the program.</span></span>|<span data-ttu-id="850da-114">10</span><span class="sxs-lookup"><span data-stu-id="850da-114">10</span></span>|<span data-ttu-id="850da-115">Oui</span><span class="sxs-lookup"><span data-stu-id="850da-115">Yes</span></span>|  
|<span data-ttu-id="850da-116">**DatabaseID**</span><span class="sxs-lookup"><span data-stu-id="850da-116">**DatabaseID**</span></span>|<span data-ttu-id="850da-117">**int**</span><span class="sxs-lookup"><span data-stu-id="850da-117">**int**</span></span>|<span data-ttu-id="850da-118">ID de la base de données spécifiée par l'instruction USE *database* ou celui de la base de données par défaut si aucune instruction USE *database* n'a été spécifiée pour une instance donnée.</span><span class="sxs-lookup"><span data-stu-id="850da-118">ID of the database specified by the USE *database* statement or the default database if no USE *database* statement has been issued for a given instance.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="850da-119">affiche le nom de la base de données si la colonne de données **ServerName** du serveur est capturée dans la trace et que le serveur est disponible.</span><span class="sxs-lookup"><span data-stu-id="850da-119">displays the name of the database if the **ServerName** data column is captured in the trace and the server is available.</span></span> <span data-ttu-id="850da-120">Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.</span><span class="sxs-lookup"><span data-stu-id="850da-120">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="850da-121">3</span><span class="sxs-lookup"><span data-stu-id="850da-121">3</span></span>|<span data-ttu-id="850da-122">Oui</span><span class="sxs-lookup"><span data-stu-id="850da-122">Yes</span></span>|  
|<span data-ttu-id="850da-123">**DatabaseName**</span><span class="sxs-lookup"><span data-stu-id="850da-123">**DatabaseName**</span></span>|<span data-ttu-id="850da-124">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="850da-124">**nvarchar**</span></span>|<span data-ttu-id="850da-125">Nom de la base de données dans laquelle l'instruction de l'utilisateur est exécutée.</span><span class="sxs-lookup"><span data-stu-id="850da-125">Name of the database in which the user statement is running.</span></span>|<span data-ttu-id="850da-126">35</span><span class="sxs-lookup"><span data-stu-id="850da-126">35</span></span>|<span data-ttu-id="850da-127">Oui</span><span class="sxs-lookup"><span data-stu-id="850da-127">Yes</span></span>|  
|<span data-ttu-id="850da-128">**DBUserName**</span><span class="sxs-lookup"><span data-stu-id="850da-128">**DBUserName**</span></span>|<span data-ttu-id="850da-129">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="850da-129">**nvarchar**</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="850da-130">du client.</span><span class="sxs-lookup"><span data-stu-id="850da-130">user name of the client.</span></span>|<span data-ttu-id="850da-131">40</span><span class="sxs-lookup"><span data-stu-id="850da-131">40</span></span>|<span data-ttu-id="850da-132">Oui</span><span class="sxs-lookup"><span data-stu-id="850da-132">Yes</span></span>|  
|<span data-ttu-id="850da-133">**EventSequence**</span><span class="sxs-lookup"><span data-stu-id="850da-133">**EventSequence**</span></span>|<span data-ttu-id="850da-134">**int**</span><span class="sxs-lookup"><span data-stu-id="850da-134">**int**</span></span>|<span data-ttu-id="850da-135">Séquence d'un événement donné au sein de la demande.</span><span class="sxs-lookup"><span data-stu-id="850da-135">Sequence of a given event within the request.</span></span>|<span data-ttu-id="850da-136">51</span><span class="sxs-lookup"><span data-stu-id="850da-136">51</span></span>|<span data-ttu-id="850da-137">Non</span><span class="sxs-lookup"><span data-stu-id="850da-137">No</span></span>|  
|<span data-ttu-id="850da-138">**EventSubClass**</span><span class="sxs-lookup"><span data-stu-id="850da-138">**EventSubClass**</span></span>|<span data-ttu-id="850da-139">**int**</span><span class="sxs-lookup"><span data-stu-id="850da-139">**int**</span></span>|<span data-ttu-id="850da-140">Type de sous-classe d'événements.</span><span class="sxs-lookup"><span data-stu-id="850da-140">Type of event subclass.</span></span><br /><br /> <span data-ttu-id="850da-141">1 = administrer les opérations en bloc</span><span class="sxs-lookup"><span data-stu-id="850da-141">1=Administer Bulk Operations</span></span><br /><br /> <span data-ttu-id="850da-142">2 = modifier les paramètres</span><span class="sxs-lookup"><span data-stu-id="850da-142">2=Alter Settings</span></span><br /><br /> <span data-ttu-id="850da-143">3 = modifier les ressources</span><span class="sxs-lookup"><span data-stu-id="850da-143">3=Alter Resources</span></span><br /><br /> <span data-ttu-id="850da-144">4 = authentifier</span><span class="sxs-lookup"><span data-stu-id="850da-144">4=Authenticate</span></span><br /><br /> <span data-ttu-id="850da-145">5 = accès externe</span><span class="sxs-lookup"><span data-stu-id="850da-145">5=External Access</span></span><br /><br /> <span data-ttu-id="850da-146">6 = modifier l'état du serveur</span><span class="sxs-lookup"><span data-stu-id="850da-146">6=Alter Server State</span></span><br /><br /> <span data-ttu-id="850da-147">7 = assembly non sécurisé</span><span class="sxs-lookup"><span data-stu-id="850da-147">7=Unsafe Assembly</span></span><br /><br /> <span data-ttu-id="850da-148">8 = modifier la connexion</span><span class="sxs-lookup"><span data-stu-id="850da-148">8=Alter Connection</span></span><br /><br /> <span data-ttu-id="850da-149">9 = modifier Resource Governor</span><span class="sxs-lookup"><span data-stu-id="850da-149">9=Alter Resource Governor</span></span><br /><br /> <span data-ttu-id="850da-150">10 = utiliser n'importe quel groupe de charges de travail</span><span class="sxs-lookup"><span data-stu-id="850da-150">10=Use Any Workload Group</span></span><br /><br /> <span data-ttu-id="850da-151">11 = afficher l'état du serveur</span><span class="sxs-lookup"><span data-stu-id="850da-151">11=View Server State</span></span>|<span data-ttu-id="850da-152">21</span><span class="sxs-lookup"><span data-stu-id="850da-152">21</span></span>|<span data-ttu-id="850da-153">Oui</span><span class="sxs-lookup"><span data-stu-id="850da-153">Yes</span></span>|  
|<span data-ttu-id="850da-154">**HostName**</span><span class="sxs-lookup"><span data-stu-id="850da-154">**HostName**</span></span>|<span data-ttu-id="850da-155">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="850da-155">**nvarchar**</span></span>|<span data-ttu-id="850da-156">Nom de l'ordinateur sur lequel le client est exécuté.</span><span class="sxs-lookup"><span data-stu-id="850da-156">Name of the computer on which the client is running.</span></span> <span data-ttu-id="850da-157">La colonne de données est remplie si le client fournit le nom de l'hôte.</span><span class="sxs-lookup"><span data-stu-id="850da-157">This data column is populated if the client provides the host name.</span></span> <span data-ttu-id="850da-158">Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.</span><span class="sxs-lookup"><span data-stu-id="850da-158">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="850da-159">8</span><span class="sxs-lookup"><span data-stu-id="850da-159">8</span></span>|<span data-ttu-id="850da-160">Oui</span><span class="sxs-lookup"><span data-stu-id="850da-160">Yes</span></span>|  
|<span data-ttu-id="850da-161">**IsSystem**</span><span class="sxs-lookup"><span data-stu-id="850da-161">**IsSystem**</span></span>|<span data-ttu-id="850da-162">**int**</span><span class="sxs-lookup"><span data-stu-id="850da-162">**int**</span></span>|<span data-ttu-id="850da-163">Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur.</span><span class="sxs-lookup"><span data-stu-id="850da-163">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="850da-164">1 = système, 0 = utilisateur.</span><span class="sxs-lookup"><span data-stu-id="850da-164">1 = system, 0 = user.</span></span>|<span data-ttu-id="850da-165">60</span><span class="sxs-lookup"><span data-stu-id="850da-165">60</span></span>|<span data-ttu-id="850da-166">Oui</span><span class="sxs-lookup"><span data-stu-id="850da-166">Yes</span></span>|  
|<span data-ttu-id="850da-167">**LoginName**</span><span class="sxs-lookup"><span data-stu-id="850da-167">**LoginName**</span></span>|<span data-ttu-id="850da-168">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="850da-168">**nvarchar**</span></span>|<span data-ttu-id="850da-169">Nom de la connexion de l'utilisateur (soit la connexion de sécurité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , soit les informations d'identification de connexion [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows au format DOMAINE\nom_utilisateur).</span><span class="sxs-lookup"><span data-stu-id="850da-169">Name of the login of the user (either the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security login or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows login credentials in the form of DOMAIN\username).</span></span>|<span data-ttu-id="850da-170">11</span><span class="sxs-lookup"><span data-stu-id="850da-170">11</span></span>|<span data-ttu-id="850da-171">Oui</span><span class="sxs-lookup"><span data-stu-id="850da-171">Yes</span></span>|  
|<span data-ttu-id="850da-172">**LoginSid**</span><span class="sxs-lookup"><span data-stu-id="850da-172">**LoginSid**</span></span>|<span data-ttu-id="850da-173">**image**</span><span class="sxs-lookup"><span data-stu-id="850da-173">**image**</span></span>|<span data-ttu-id="850da-174">Numéro d'identification de sécurité (SID) de l'utilisateur connecté.</span><span class="sxs-lookup"><span data-stu-id="850da-174">Security identification number (SID) of the logged-in user.</span></span> <span data-ttu-id="850da-175">Vous pouvez trouver ces informations dans l’affichage catalogue **sys.server_principals** .</span><span class="sxs-lookup"><span data-stu-id="850da-175">You can find this information in the **sys.server_principals** catalog view.</span></span> <span data-ttu-id="850da-176">Chaque connexion possède un SID unique au niveau du serveur.</span><span class="sxs-lookup"><span data-stu-id="850da-176">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="850da-177">41</span><span class="sxs-lookup"><span data-stu-id="850da-177">41</span></span>|<span data-ttu-id="850da-178">Oui</span><span class="sxs-lookup"><span data-stu-id="850da-178">Yes</span></span>|  
|<span data-ttu-id="850da-179">**NTDomainName**</span><span class="sxs-lookup"><span data-stu-id="850da-179">**NTDomainName**</span></span>|<span data-ttu-id="850da-180">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="850da-180">**nvarchar**</span></span>|<span data-ttu-id="850da-181">Domaine Windows auquel appartient l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="850da-181">Windows domain to which the user belongs.</span></span>|<span data-ttu-id="850da-182">7</span><span class="sxs-lookup"><span data-stu-id="850da-182">7</span></span>|<span data-ttu-id="850da-183">Oui</span><span class="sxs-lookup"><span data-stu-id="850da-183">Yes</span></span>|  
|<span data-ttu-id="850da-184">**NTUserName**</span><span class="sxs-lookup"><span data-stu-id="850da-184">**NTUserName**</span></span>|<span data-ttu-id="850da-185">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="850da-185">**nvarchar**</span></span>|<span data-ttu-id="850da-186">Nom d'utilisateur Windows.</span><span class="sxs-lookup"><span data-stu-id="850da-186">Windows user name.</span></span>|<span data-ttu-id="850da-187">6</span><span class="sxs-lookup"><span data-stu-id="850da-187">6</span></span>|<span data-ttu-id="850da-188">Oui</span><span class="sxs-lookup"><span data-stu-id="850da-188">Yes</span></span>|  
|<span data-ttu-id="850da-189">**ObjectName**</span><span class="sxs-lookup"><span data-stu-id="850da-189">**ObjectName**</span></span>|<span data-ttu-id="850da-190">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="850da-190">**nvarchar**</span></span>|<span data-ttu-id="850da-191">Nom de l'objet référencé.</span><span class="sxs-lookup"><span data-stu-id="850da-191">Name of the object being referenced.</span></span>|<span data-ttu-id="850da-192">34</span><span class="sxs-lookup"><span data-stu-id="850da-192">34</span></span>|<span data-ttu-id="850da-193">Oui</span><span class="sxs-lookup"><span data-stu-id="850da-193">Yes</span></span>|  
|<span data-ttu-id="850da-194">**ObjectType**</span><span class="sxs-lookup"><span data-stu-id="850da-194">**ObjectType**</span></span>|<span data-ttu-id="850da-195">**int**</span><span class="sxs-lookup"><span data-stu-id="850da-195">**int**</span></span>|<span data-ttu-id="850da-196">Valeur représentant le type de l'objet qui intervient dans l'événement.</span><span class="sxs-lookup"><span data-stu-id="850da-196">Value representing the type of the object involved in the event.</span></span> <span data-ttu-id="850da-197">Cette valeur correspond à la colonne type de l'affichage catalogue **sys.objects** .</span><span class="sxs-lookup"><span data-stu-id="850da-197">This value corresponds to the type column in the **sys.objects** catalog view.</span></span> <span data-ttu-id="850da-198">Pour connaître les valeurs, consultez [Colonne d’événements de trace ObjectType](objecttype-trace-event-column.md).</span><span class="sxs-lookup"><span data-stu-id="850da-198">For values, see [ObjectType Trace Event Column](objecttype-trace-event-column.md).</span></span>|<span data-ttu-id="850da-199">28</span><span class="sxs-lookup"><span data-stu-id="850da-199">28</span></span>|<span data-ttu-id="850da-200">Oui</span><span class="sxs-lookup"><span data-stu-id="850da-200">Yes</span></span>|  
|<span data-ttu-id="850da-201">**OwnerName**</span><span class="sxs-lookup"><span data-stu-id="850da-201">**OwnerName**</span></span>|<span data-ttu-id="850da-202">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="850da-202">**nvarchar**</span></span>|<span data-ttu-id="850da-203">Nom d'utilisateur de base de données du propriétaire de l'objet.</span><span class="sxs-lookup"><span data-stu-id="850da-203">Database user name of the object owner.</span></span>|<span data-ttu-id="850da-204">37</span><span class="sxs-lookup"><span data-stu-id="850da-204">37</span></span>|<span data-ttu-id="850da-205">Oui</span><span class="sxs-lookup"><span data-stu-id="850da-205">Yes</span></span>|  
|<span data-ttu-id="850da-206">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="850da-206">**RequestID**</span></span>|<span data-ttu-id="850da-207">**int**</span><span class="sxs-lookup"><span data-stu-id="850da-207">**int**</span></span>|<span data-ttu-id="850da-208">ID de la demande contenant l'instruction.</span><span class="sxs-lookup"><span data-stu-id="850da-208">ID of the request containing the statement.</span></span>|<span data-ttu-id="850da-209">49</span><span class="sxs-lookup"><span data-stu-id="850da-209">49</span></span>|<span data-ttu-id="850da-210">Oui</span><span class="sxs-lookup"><span data-stu-id="850da-210">Yes</span></span>|  
|<span data-ttu-id="850da-211">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="850da-211">**ServerName**</span></span>|<span data-ttu-id="850da-212">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="850da-212">**nvarchar**</span></span>|<span data-ttu-id="850da-213">Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.</span><span class="sxs-lookup"><span data-stu-id="850da-213">Name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="850da-214">26</span><span class="sxs-lookup"><span data-stu-id="850da-214">26</span></span>|<span data-ttu-id="850da-215">Non</span><span class="sxs-lookup"><span data-stu-id="850da-215">No</span></span>|  
|<span data-ttu-id="850da-216">**SessionLoginName**</span><span class="sxs-lookup"><span data-stu-id="850da-216">**SessionLoginName**</span></span>|<span data-ttu-id="850da-217">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="850da-217">**nvarchar**</span></span>|<span data-ttu-id="850da-218">Nom de connexion de l'utilisateur à l'origine de la session.</span><span class="sxs-lookup"><span data-stu-id="850da-218">Login name of the user who originated the session.</span></span> <span data-ttu-id="850da-219">Par exemple, si vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au moyen de Login1 et que vous exécutez une commande en tant que Login2, **SessionLoginName** affiche Login1 et **LoginName** affiche Login2.</span><span class="sxs-lookup"><span data-stu-id="850da-219">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, **SessionLoginName** shows Login1 and **LoginName** shows Login2.</span></span> <span data-ttu-id="850da-220">Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Windows.</span><span class="sxs-lookup"><span data-stu-id="850da-220">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows logins.</span></span>|<span data-ttu-id="850da-221">64</span><span class="sxs-lookup"><span data-stu-id="850da-221">64</span></span>|<span data-ttu-id="850da-222">Oui</span><span class="sxs-lookup"><span data-stu-id="850da-222">Yes</span></span>|  
|<span data-ttu-id="850da-223">**SPID**</span><span class="sxs-lookup"><span data-stu-id="850da-223">**SPID**</span></span>|<span data-ttu-id="850da-224">**int**</span><span class="sxs-lookup"><span data-stu-id="850da-224">**int**</span></span>|<span data-ttu-id="850da-225">ID de la session au cours de laquelle l'événement s'est produit.</span><span class="sxs-lookup"><span data-stu-id="850da-225">ID of the session on which the event occurred.</span></span>|<span data-ttu-id="850da-226">12</span><span class="sxs-lookup"><span data-stu-id="850da-226">12</span></span>|<span data-ttu-id="850da-227">Oui</span><span class="sxs-lookup"><span data-stu-id="850da-227">Yes</span></span>|  
|<span data-ttu-id="850da-228">**StartTime**</span><span class="sxs-lookup"><span data-stu-id="850da-228">**StartTime**</span></span>|<span data-ttu-id="850da-229">**datetime**</span><span class="sxs-lookup"><span data-stu-id="850da-229">**datetime**</span></span>|<span data-ttu-id="850da-230">Heure à laquelle a débuté l'événement, si elle est connue.</span><span class="sxs-lookup"><span data-stu-id="850da-230">Time at which the event started, if available.</span></span>|<span data-ttu-id="850da-231">14</span><span class="sxs-lookup"><span data-stu-id="850da-231">14</span></span>|<span data-ttu-id="850da-232">Oui</span><span class="sxs-lookup"><span data-stu-id="850da-232">Yes</span></span>|  
|<span data-ttu-id="850da-233">**Success**</span><span class="sxs-lookup"><span data-stu-id="850da-233">**Success**</span></span>|<span data-ttu-id="850da-234">**int**</span><span class="sxs-lookup"><span data-stu-id="850da-234">**int**</span></span>|<span data-ttu-id="850da-235">1 = réussite.</span><span class="sxs-lookup"><span data-stu-id="850da-235">1 = success.</span></span> <span data-ttu-id="850da-236">0 = échec.</span><span class="sxs-lookup"><span data-stu-id="850da-236">0 = failure.</span></span> <span data-ttu-id="850da-237">Par exemple, la valeur 1 indique la réussite d'une vérification d'autorisations tandis que la valeur 0 indique son échec.</span><span class="sxs-lookup"><span data-stu-id="850da-237">For example, a value of 1 means success of a permissions check and a value of 0 means a failure of that check.</span></span>|<span data-ttu-id="850da-238">23</span><span class="sxs-lookup"><span data-stu-id="850da-238">23</span></span>|<span data-ttu-id="850da-239">Oui</span><span class="sxs-lookup"><span data-stu-id="850da-239">Yes</span></span>|  
|<span data-ttu-id="850da-240">**TextData**</span><span class="sxs-lookup"><span data-stu-id="850da-240">**TextData**</span></span>|<span data-ttu-id="850da-241">**ntext**</span><span class="sxs-lookup"><span data-stu-id="850da-241">**ntext**</span></span>|<span data-ttu-id="850da-242">Valeur texte qui dépend de la classe d'événements capturée dans la trace.</span><span class="sxs-lookup"><span data-stu-id="850da-242">Text value dependent on the event class captured in the trace.</span></span>|<span data-ttu-id="850da-243">1</span><span class="sxs-lookup"><span data-stu-id="850da-243">1</span></span>|<span data-ttu-id="850da-244">Oui</span><span class="sxs-lookup"><span data-stu-id="850da-244">Yes</span></span>|  
|<span data-ttu-id="850da-245">**TransactionID**</span><span class="sxs-lookup"><span data-stu-id="850da-245">**TransactionID**</span></span>|<span data-ttu-id="850da-246">**bigint**</span><span class="sxs-lookup"><span data-stu-id="850da-246">**bigint**</span></span>|<span data-ttu-id="850da-247">ID affecté par le système à la transaction.</span><span class="sxs-lookup"><span data-stu-id="850da-247">System-assigned ID of the transaction.</span></span>|<span data-ttu-id="850da-248">4</span><span class="sxs-lookup"><span data-stu-id="850da-248">4</span></span>|<span data-ttu-id="850da-249">Oui</span><span class="sxs-lookup"><span data-stu-id="850da-249">Yes</span></span>|  
|<span data-ttu-id="850da-250">**XactSequence**</span><span class="sxs-lookup"><span data-stu-id="850da-250">**XactSequence**</span></span>|<span data-ttu-id="850da-251">**bigint**</span><span class="sxs-lookup"><span data-stu-id="850da-251">**bigint**</span></span>|<span data-ttu-id="850da-252">Jeton utilisé pour décrire la transaction en cours.</span><span class="sxs-lookup"><span data-stu-id="850da-252">Token used to describe the current transaction.</span></span>|<span data-ttu-id="850da-253">50</span><span class="sxs-lookup"><span data-stu-id="850da-253">50</span></span>|<span data-ttu-id="850da-254">Oui</span><span class="sxs-lookup"><span data-stu-id="850da-254">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="850da-255">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="850da-255">See Also</span></span>  
 <span data-ttu-id="850da-256">[Événements étendus](../extended-events/extended-events.md) </span><span class="sxs-lookup"><span data-stu-id="850da-256">[Extended Events](../extended-events/extended-events.md) </span></span>  
 [<span data-ttu-id="850da-257">sp_trace_setevent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="850da-257">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  