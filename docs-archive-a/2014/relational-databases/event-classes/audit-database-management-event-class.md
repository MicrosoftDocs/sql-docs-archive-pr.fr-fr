---
title: Audit Database Management, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Audit Database Management event class
ms.assetid: 3e3de528-c3f8-413f-a6b9-d324ca95ad8e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9fc72179193754f4e8b4d52ed0598939f587f676
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701177"
---
# <a name="audit-database-management-event-class"></a><span data-ttu-id="d21b8-102">Audit Database Management (classe d'événements)</span><span class="sxs-lookup"><span data-stu-id="d21b8-102">Audit Database Management Event Class</span></span>
  <span data-ttu-id="d21b8-103">La classe d'événements **Audit Database Management** intervient lorsqu'une base de données est créée, modifiée ou supprimée.</span><span class="sxs-lookup"><span data-stu-id="d21b8-103">The **Audit Database Management** event class occurs when a database is created, altered, or dropped.</span></span>  
  
## <a name="audit-database-management-event-class-data-columns"></a><span data-ttu-id="d21b8-104">Colonnes de données de la classe d'événements Audit Database Management</span><span class="sxs-lookup"><span data-stu-id="d21b8-104">Audit Database Management Event Class Data Columns</span></span>  
  
|<span data-ttu-id="d21b8-105">Nom de la colonne de données</span><span class="sxs-lookup"><span data-stu-id="d21b8-105">Data column name</span></span>|<span data-ttu-id="d21b8-106">Type de données</span><span class="sxs-lookup"><span data-stu-id="d21b8-106">Data type</span></span>|<span data-ttu-id="d21b8-107">Description</span><span class="sxs-lookup"><span data-stu-id="d21b8-107">Description</span></span>|<span data-ttu-id="d21b8-108">ID de la colonne</span><span class="sxs-lookup"><span data-stu-id="d21b8-108">Column ID</span></span>|<span data-ttu-id="d21b8-109">Filtrable</span><span class="sxs-lookup"><span data-stu-id="d21b8-109">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="d21b8-110">**ApplicationName**</span><span class="sxs-lookup"><span data-stu-id="d21b8-110">**ApplicationName**</span></span>|<span data-ttu-id="d21b8-111">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="d21b8-111">**nvarchar**</span></span>|<span data-ttu-id="d21b8-112">Nom de l’application cliente qui a créé la connexion à une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d21b8-112">Name of the client application that created the connection to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d21b8-113">Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.</span><span class="sxs-lookup"><span data-stu-id="d21b8-113">This column is populated with the values passed by the application rather than the displayed name of the program.</span></span>|<span data-ttu-id="d21b8-114">10</span><span class="sxs-lookup"><span data-stu-id="d21b8-114">10</span></span>|<span data-ttu-id="d21b8-115">Oui</span><span class="sxs-lookup"><span data-stu-id="d21b8-115">Yes</span></span>|  
|<span data-ttu-id="d21b8-116">**DatabaseID**</span><span class="sxs-lookup"><span data-stu-id="d21b8-116">**DatabaseID**</span></span>|<span data-ttu-id="d21b8-117">**int**</span><span class="sxs-lookup"><span data-stu-id="d21b8-117">**int**</span></span>|<span data-ttu-id="d21b8-118">ID de la base de données spécifiée par l'instruction USE *database* ou celui de la base de données par défaut si aucune instruction USE *database* n'a été spécifiée pour une instance donnée.</span><span class="sxs-lookup"><span data-stu-id="d21b8-118">ID of the database specified by the USE *database* statement or the default database if no USE *database* statement has been issued for a given instance.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="d21b8-119">affiche le nom de la base de données si la colonne de données ServerName est capturée dans la trace et que le serveur est disponible.</span><span class="sxs-lookup"><span data-stu-id="d21b8-119">displays the name of the database if the Server Name data column is captured in the trace and the server is available.</span></span> <span data-ttu-id="d21b8-120">Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.</span><span class="sxs-lookup"><span data-stu-id="d21b8-120">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="d21b8-121">3</span><span class="sxs-lookup"><span data-stu-id="d21b8-121">3</span></span>|<span data-ttu-id="d21b8-122">Oui</span><span class="sxs-lookup"><span data-stu-id="d21b8-122">Yes</span></span>|  
|<span data-ttu-id="d21b8-123">**DatabaseName**</span><span class="sxs-lookup"><span data-stu-id="d21b8-123">**DatabaseName**</span></span>|<span data-ttu-id="d21b8-124">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="d21b8-124">**nvarchar**</span></span>|<span data-ttu-id="d21b8-125">Nom de la base de données dans laquelle l'instruction de l'utilisateur est exécutée.</span><span class="sxs-lookup"><span data-stu-id="d21b8-125">Name of the database in which the user statement is running.</span></span>|<span data-ttu-id="d21b8-126">35</span><span class="sxs-lookup"><span data-stu-id="d21b8-126">35</span></span>|<span data-ttu-id="d21b8-127">Oui</span><span class="sxs-lookup"><span data-stu-id="d21b8-127">Yes</span></span>|  
|<span data-ttu-id="d21b8-128">**DBUserName**</span><span class="sxs-lookup"><span data-stu-id="d21b8-128">**DBUserName**</span></span>|<span data-ttu-id="d21b8-129">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="d21b8-129">**nvarchar**</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d21b8-130">du client.</span><span class="sxs-lookup"><span data-stu-id="d21b8-130">user name of the client.</span></span>|<span data-ttu-id="d21b8-131">40</span><span class="sxs-lookup"><span data-stu-id="d21b8-131">40</span></span>|<span data-ttu-id="d21b8-132">Oui</span><span class="sxs-lookup"><span data-stu-id="d21b8-132">Yes</span></span>|  
|<span data-ttu-id="d21b8-133">**EventSequence**</span><span class="sxs-lookup"><span data-stu-id="d21b8-133">**EventSequence**</span></span>|<span data-ttu-id="d21b8-134">**int**</span><span class="sxs-lookup"><span data-stu-id="d21b8-134">**int**</span></span>|<span data-ttu-id="d21b8-135">Séquence d'un événement donné au sein de la demande.</span><span class="sxs-lookup"><span data-stu-id="d21b8-135">Sequence of a given event within the request.</span></span>|<span data-ttu-id="d21b8-136">51</span><span class="sxs-lookup"><span data-stu-id="d21b8-136">51</span></span>|<span data-ttu-id="d21b8-137">Non</span><span class="sxs-lookup"><span data-stu-id="d21b8-137">No</span></span>|  
|<span data-ttu-id="d21b8-138">**EventSubClass**</span><span class="sxs-lookup"><span data-stu-id="d21b8-138">**EventSubClass**</span></span>|<span data-ttu-id="d21b8-139">**int**</span><span class="sxs-lookup"><span data-stu-id="d21b8-139">**int**</span></span>|<span data-ttu-id="d21b8-140">Type de sous-classe d'événements.</span><span class="sxs-lookup"><span data-stu-id="d21b8-140">Type of event subclass.</span></span><br /><br /> <span data-ttu-id="d21b8-141">1=Création</span><span class="sxs-lookup"><span data-stu-id="d21b8-141">1=Create</span></span><br /><br /> <span data-ttu-id="d21b8-142">2=Modification</span><span class="sxs-lookup"><span data-stu-id="d21b8-142">2=Alter</span></span><br /><br /> <span data-ttu-id="d21b8-143">3=Suppression</span><span class="sxs-lookup"><span data-stu-id="d21b8-143">3=Drop</span></span><br /><br /> <span data-ttu-id="d21b8-144">4=Vidage</span><span class="sxs-lookup"><span data-stu-id="d21b8-144">4=Dump</span></span><br /><br /> <span data-ttu-id="d21b8-145">11=Chargement</span><span class="sxs-lookup"><span data-stu-id="d21b8-145">11=Load</span></span>|<span data-ttu-id="d21b8-146">21</span><span class="sxs-lookup"><span data-stu-id="d21b8-146">21</span></span>|<span data-ttu-id="d21b8-147">Oui</span><span class="sxs-lookup"><span data-stu-id="d21b8-147">Yes</span></span>|  
|<span data-ttu-id="d21b8-148">**HostName**</span><span class="sxs-lookup"><span data-stu-id="d21b8-148">**HostName**</span></span>|<span data-ttu-id="d21b8-149">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="d21b8-149">**nvarchar**</span></span>|<span data-ttu-id="d21b8-150">Nom de l'ordinateur sur lequel le client est exécuté.</span><span class="sxs-lookup"><span data-stu-id="d21b8-150">Name of the computer on which the client is running.</span></span> <span data-ttu-id="d21b8-151">La colonne de données est remplie si le client fournit le nom de l'hôte.</span><span class="sxs-lookup"><span data-stu-id="d21b8-151">This data column is populated if the client provides the host name.</span></span> <span data-ttu-id="d21b8-152">Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.</span><span class="sxs-lookup"><span data-stu-id="d21b8-152">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="d21b8-153">8</span><span class="sxs-lookup"><span data-stu-id="d21b8-153">8</span></span>|<span data-ttu-id="d21b8-154">Oui</span><span class="sxs-lookup"><span data-stu-id="d21b8-154">Yes</span></span>|  
|<span data-ttu-id="d21b8-155">**IsSystem**</span><span class="sxs-lookup"><span data-stu-id="d21b8-155">**IsSystem**</span></span>|<span data-ttu-id="d21b8-156">**int**</span><span class="sxs-lookup"><span data-stu-id="d21b8-156">**int**</span></span>|<span data-ttu-id="d21b8-157">Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d21b8-157">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="d21b8-158">1 = système, 0 = utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d21b8-158">1 = system, 0 = user.</span></span>|<span data-ttu-id="d21b8-159">60</span><span class="sxs-lookup"><span data-stu-id="d21b8-159">60</span></span>|<span data-ttu-id="d21b8-160">Oui</span><span class="sxs-lookup"><span data-stu-id="d21b8-160">Yes</span></span>|  
|<span data-ttu-id="d21b8-161">**LoginName**</span><span class="sxs-lookup"><span data-stu-id="d21b8-161">**LoginName**</span></span>|<span data-ttu-id="d21b8-162">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="d21b8-162">**nvarchar**</span></span>|<span data-ttu-id="d21b8-163">Nom de la connexion de l'utilisateur (soit la connexion de sécurité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , soit les informations d'identification de connexion [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows au format DOMAINE\nom_utilisateur).</span><span class="sxs-lookup"><span data-stu-id="d21b8-163">Name of the login of the user (either the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security login or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows login credentials in the form of DOMAIN\username).</span></span>|<span data-ttu-id="d21b8-164">11</span><span class="sxs-lookup"><span data-stu-id="d21b8-164">11</span></span>|<span data-ttu-id="d21b8-165">Oui</span><span class="sxs-lookup"><span data-stu-id="d21b8-165">Yes</span></span>|  
|<span data-ttu-id="d21b8-166">**LoginSid**</span><span class="sxs-lookup"><span data-stu-id="d21b8-166">**LoginSid**</span></span>|<span data-ttu-id="d21b8-167">**image**</span><span class="sxs-lookup"><span data-stu-id="d21b8-167">**image**</span></span>|<span data-ttu-id="d21b8-168">Numéro d'identification de sécurité (SID) de l'utilisateur connecté.</span><span class="sxs-lookup"><span data-stu-id="d21b8-168">Security identification number (SID) of the logged-in user.</span></span> <span data-ttu-id="d21b8-169">Vous pouvez trouver ces informations dans l’affichage catalogue **sys.server_principals** .</span><span class="sxs-lookup"><span data-stu-id="d21b8-169">You can find this information in the **sys.server_principals** catalog view.</span></span> <span data-ttu-id="d21b8-170">Chaque connexion possède un SID unique au niveau du serveur.</span><span class="sxs-lookup"><span data-stu-id="d21b8-170">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="d21b8-171">41</span><span class="sxs-lookup"><span data-stu-id="d21b8-171">41</span></span>|<span data-ttu-id="d21b8-172">Oui</span><span class="sxs-lookup"><span data-stu-id="d21b8-172">Yes</span></span>|  
|<span data-ttu-id="d21b8-173">**NTDomainName**</span><span class="sxs-lookup"><span data-stu-id="d21b8-173">**NTDomainName**</span></span>|<span data-ttu-id="d21b8-174">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="d21b8-174">**nvarchar**</span></span>|<span data-ttu-id="d21b8-175">Domaine Windows auquel appartient l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d21b8-175">Windows domain to which the user belongs.</span></span>|<span data-ttu-id="d21b8-176">7</span><span class="sxs-lookup"><span data-stu-id="d21b8-176">7</span></span>|<span data-ttu-id="d21b8-177">Oui</span><span class="sxs-lookup"><span data-stu-id="d21b8-177">Yes</span></span>|  
|<span data-ttu-id="d21b8-178">**NTUserName**</span><span class="sxs-lookup"><span data-stu-id="d21b8-178">**NTUserName**</span></span>|<span data-ttu-id="d21b8-179">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="d21b8-179">**nvarchar**</span></span>|<span data-ttu-id="d21b8-180">Nom d'utilisateur Windows.</span><span class="sxs-lookup"><span data-stu-id="d21b8-180">Windows user name.</span></span>|<span data-ttu-id="d21b8-181">6</span><span class="sxs-lookup"><span data-stu-id="d21b8-181">6</span></span>|<span data-ttu-id="d21b8-182">Oui</span><span class="sxs-lookup"><span data-stu-id="d21b8-182">Yes</span></span>|  
|<span data-ttu-id="d21b8-183">**ObjectName**</span><span class="sxs-lookup"><span data-stu-id="d21b8-183">**ObjectName**</span></span>|<span data-ttu-id="d21b8-184">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="d21b8-184">**nvarchar**</span></span>|<span data-ttu-id="d21b8-185">Nom de l'objet référencé.</span><span class="sxs-lookup"><span data-stu-id="d21b8-185">Name of the object being referenced.</span></span>|<span data-ttu-id="d21b8-186">34</span><span class="sxs-lookup"><span data-stu-id="d21b8-186">34</span></span>|<span data-ttu-id="d21b8-187">Oui</span><span class="sxs-lookup"><span data-stu-id="d21b8-187">Yes</span></span>|  
|<span data-ttu-id="d21b8-188">**ObjectType**</span><span class="sxs-lookup"><span data-stu-id="d21b8-188">**ObjectType**</span></span>|<span data-ttu-id="d21b8-189">**int**</span><span class="sxs-lookup"><span data-stu-id="d21b8-189">**int**</span></span>|<span data-ttu-id="d21b8-190">Valeur représentant le type de l'objet qui intervient dans l'événement.</span><span class="sxs-lookup"><span data-stu-id="d21b8-190">Value representing the type of the object involved in the event.</span></span> <span data-ttu-id="d21b8-191">Cette valeur correspond à la colonne de type de la table **sysobjects** .</span><span class="sxs-lookup"><span data-stu-id="d21b8-191">This value corresponds to the type column in the **sysobjects** table.</span></span> <span data-ttu-id="d21b8-192">Pour connaître les valeurs, consultez [Colonne d’événements de trace ObjectType](objecttype-trace-event-column.md).</span><span class="sxs-lookup"><span data-stu-id="d21b8-192">For values, see [ObjectType Trace Event Column](objecttype-trace-event-column.md).</span></span>|<span data-ttu-id="d21b8-193">28</span><span class="sxs-lookup"><span data-stu-id="d21b8-193">28</span></span>|<span data-ttu-id="d21b8-194">Oui</span><span class="sxs-lookup"><span data-stu-id="d21b8-194">Yes</span></span>|  
|<span data-ttu-id="d21b8-195">**OwnerName**</span><span class="sxs-lookup"><span data-stu-id="d21b8-195">**OwnerName**</span></span>|<span data-ttu-id="d21b8-196">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="d21b8-196">**nvarchar**</span></span>|<span data-ttu-id="d21b8-197">Nom d'utilisateur de base de données du propriétaire de l'objet.</span><span class="sxs-lookup"><span data-stu-id="d21b8-197">Database user name of the object owner.</span></span>|<span data-ttu-id="d21b8-198">37</span><span class="sxs-lookup"><span data-stu-id="d21b8-198">37</span></span>|<span data-ttu-id="d21b8-199">Oui</span><span class="sxs-lookup"><span data-stu-id="d21b8-199">Yes</span></span>|  
|<span data-ttu-id="d21b8-200">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="d21b8-200">**RequestID**</span></span>|<span data-ttu-id="d21b8-201">**int**</span><span class="sxs-lookup"><span data-stu-id="d21b8-201">**int**</span></span>|<span data-ttu-id="d21b8-202">ID de la demande contenant l'instruction.</span><span class="sxs-lookup"><span data-stu-id="d21b8-202">ID of the request containing the statement.</span></span>|<span data-ttu-id="d21b8-203">49</span><span class="sxs-lookup"><span data-stu-id="d21b8-203">49</span></span>|<span data-ttu-id="d21b8-204">Oui</span><span class="sxs-lookup"><span data-stu-id="d21b8-204">Yes</span></span>|  
|<span data-ttu-id="d21b8-205">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="d21b8-205">**ServerName**</span></span>|<span data-ttu-id="d21b8-206">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="d21b8-206">**nvarchar**</span></span>|<span data-ttu-id="d21b8-207">Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.</span><span class="sxs-lookup"><span data-stu-id="d21b8-207">Name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="d21b8-208">26</span><span class="sxs-lookup"><span data-stu-id="d21b8-208">26</span></span>|<span data-ttu-id="d21b8-209">Non</span><span class="sxs-lookup"><span data-stu-id="d21b8-209">No</span></span>|  
|<span data-ttu-id="d21b8-210">**SessionLoginName**</span><span class="sxs-lookup"><span data-stu-id="d21b8-210">**SessionLoginName**</span></span>|<span data-ttu-id="d21b8-211">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="d21b8-211">**nvarchar**</span></span>|<span data-ttu-id="d21b8-212">Nom de connexion de l'utilisateur à l'origine de la session.</span><span class="sxs-lookup"><span data-stu-id="d21b8-212">Login name of the user who originated the session.</span></span> <span data-ttu-id="d21b8-213">Par exemple, si vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au moyen de Login1 et que vous exécutez une commande en tant que Login2, **SessionLoginName** affiche Login1 et **LoginName** affiche Login2.</span><span class="sxs-lookup"><span data-stu-id="d21b8-213">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, **SessionLoginName** shows Login1 and **LoginName** shows Login2.</span></span> <span data-ttu-id="d21b8-214">Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Windows.</span><span class="sxs-lookup"><span data-stu-id="d21b8-214">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows logins.</span></span>|<span data-ttu-id="d21b8-215">64</span><span class="sxs-lookup"><span data-stu-id="d21b8-215">64</span></span>|<span data-ttu-id="d21b8-216">Oui</span><span class="sxs-lookup"><span data-stu-id="d21b8-216">Yes</span></span>|  
|<span data-ttu-id="d21b8-217">**SPID**</span><span class="sxs-lookup"><span data-stu-id="d21b8-217">**SPID**</span></span>|<span data-ttu-id="d21b8-218">**int**</span><span class="sxs-lookup"><span data-stu-id="d21b8-218">**int**</span></span>|<span data-ttu-id="d21b8-219">ID de la session au cours de laquelle l'événement s'est produit.</span><span class="sxs-lookup"><span data-stu-id="d21b8-219">ID of the session on which the event occurred.</span></span>|<span data-ttu-id="d21b8-220">12</span><span class="sxs-lookup"><span data-stu-id="d21b8-220">12</span></span>|<span data-ttu-id="d21b8-221">Oui</span><span class="sxs-lookup"><span data-stu-id="d21b8-221">Yes</span></span>|  
|<span data-ttu-id="d21b8-222">**StartTime**</span><span class="sxs-lookup"><span data-stu-id="d21b8-222">**StartTime**</span></span>|<span data-ttu-id="d21b8-223">**datetime**</span><span class="sxs-lookup"><span data-stu-id="d21b8-223">**datetime**</span></span>|<span data-ttu-id="d21b8-224">Heure à laquelle a débuté l'événement, si elle est connue.</span><span class="sxs-lookup"><span data-stu-id="d21b8-224">Time at which the event started, if available.</span></span>|<span data-ttu-id="d21b8-225">14</span><span class="sxs-lookup"><span data-stu-id="d21b8-225">14</span></span>|<span data-ttu-id="d21b8-226">Oui</span><span class="sxs-lookup"><span data-stu-id="d21b8-226">Yes</span></span>|  
|<span data-ttu-id="d21b8-227">**Success**</span><span class="sxs-lookup"><span data-stu-id="d21b8-227">**Success**</span></span>|<span data-ttu-id="d21b8-228">**int**</span><span class="sxs-lookup"><span data-stu-id="d21b8-228">**int**</span></span>|<span data-ttu-id="d21b8-229">1 = réussite.</span><span class="sxs-lookup"><span data-stu-id="d21b8-229">1 = success.</span></span> <span data-ttu-id="d21b8-230">0 = échec.</span><span class="sxs-lookup"><span data-stu-id="d21b8-230">0 = failure.</span></span> <span data-ttu-id="d21b8-231">Par exemple, la valeur 1 indique la réussite d'une vérification d'autorisations tandis que la valeur 0 indique son échec.</span><span class="sxs-lookup"><span data-stu-id="d21b8-231">For example, a value of 1 means success of a permissions check and a value of 0 means a failure of that check.</span></span>|<span data-ttu-id="d21b8-232">23</span><span class="sxs-lookup"><span data-stu-id="d21b8-232">23</span></span>|<span data-ttu-id="d21b8-233">Oui</span><span class="sxs-lookup"><span data-stu-id="d21b8-233">Yes</span></span>|  
|<span data-ttu-id="d21b8-234">**TextData**</span><span class="sxs-lookup"><span data-stu-id="d21b8-234">**TextData**</span></span>|<span data-ttu-id="d21b8-235">**ntext**</span><span class="sxs-lookup"><span data-stu-id="d21b8-235">**ntext**</span></span>|<span data-ttu-id="d21b8-236">Valeur texte qui dépend de la classe d'événements capturée dans la trace.</span><span class="sxs-lookup"><span data-stu-id="d21b8-236">Text value dependent on the event class captured in the trace.</span></span>|<span data-ttu-id="d21b8-237">1</span><span class="sxs-lookup"><span data-stu-id="d21b8-237">1</span></span>|<span data-ttu-id="d21b8-238">Oui</span><span class="sxs-lookup"><span data-stu-id="d21b8-238">Yes</span></span>|  
|<span data-ttu-id="d21b8-239">**TransactionID**</span><span class="sxs-lookup"><span data-stu-id="d21b8-239">**TransactionID**</span></span>|<span data-ttu-id="d21b8-240">**bigint**</span><span class="sxs-lookup"><span data-stu-id="d21b8-240">**bigint**</span></span>|<span data-ttu-id="d21b8-241">ID affecté par le système à la transaction.</span><span class="sxs-lookup"><span data-stu-id="d21b8-241">System-assigned ID of the transaction.</span></span>|<span data-ttu-id="d21b8-242">4</span><span class="sxs-lookup"><span data-stu-id="d21b8-242">4</span></span>|<span data-ttu-id="d21b8-243">Oui</span><span class="sxs-lookup"><span data-stu-id="d21b8-243">Yes</span></span>|  
|<span data-ttu-id="d21b8-244">**XactSequence**</span><span class="sxs-lookup"><span data-stu-id="d21b8-244">**XactSequence**</span></span>|<span data-ttu-id="d21b8-245">**bigint**</span><span class="sxs-lookup"><span data-stu-id="d21b8-245">**bigint**</span></span>|<span data-ttu-id="d21b8-246">Jeton utilisé pour décrire la transaction en cours.</span><span class="sxs-lookup"><span data-stu-id="d21b8-246">Token used to describe the current transaction.</span></span>|<span data-ttu-id="d21b8-247">50</span><span class="sxs-lookup"><span data-stu-id="d21b8-247">50</span></span>|<span data-ttu-id="d21b8-248">Oui</span><span class="sxs-lookup"><span data-stu-id="d21b8-248">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d21b8-249">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d21b8-249">See Also</span></span>  
 <span data-ttu-id="d21b8-250">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d21b8-250">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 <span data-ttu-id="d21b8-251">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d21b8-251">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 <span data-ttu-id="d21b8-252">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d21b8-252">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="d21b8-253">DROP DATABASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d21b8-253">DROP DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-database-audit-specification-transact-sql)  
  
  