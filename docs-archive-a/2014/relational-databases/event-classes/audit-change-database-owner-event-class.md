---
title: Audit Change Database Owner, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Audit Change Database Owner event class
ms.assetid: 2f1dd4fc-2540-423c-80ad-c5bc712c42e0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 11f3a12c892a76277063827393b682809478ce46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701178"
---
# <a name="audit-change-database-owner-event-class"></a><span data-ttu-id="0ea69-102">Classe d'événements Audit Change Database Owner</span><span class="sxs-lookup"><span data-stu-id="0ea69-102">Audit Change Database Owner Event Class</span></span>
  <span data-ttu-id="0ea69-103">La classe d’événements **Audit Change Database Owner** se produit lorsque vous utilisez l’instruction ALTER AUTHORIZATION pour changer le propriétaire d’une base de données et que les autorisations requises à cet effet sont activées.</span><span class="sxs-lookup"><span data-stu-id="0ea69-103">The **Audit Change Database Owner** event class occurs when you use the ALTER AUTHORIZATION statement to change the owner of a database, and the permissions required to do that are checked.</span></span>  
  
## <a name="audit-change-database-owner-event-class-data-columns"></a><span data-ttu-id="0ea69-104">Colonnes de la classe d'événements Audit Change Database Owner</span><span class="sxs-lookup"><span data-stu-id="0ea69-104">Audit Change Database Owner Event Class Data Columns</span></span>  
  
|<span data-ttu-id="0ea69-105">Nom de la colonne de données</span><span class="sxs-lookup"><span data-stu-id="0ea69-105">Data column name</span></span>|<span data-ttu-id="0ea69-106">Type de données</span><span class="sxs-lookup"><span data-stu-id="0ea69-106">Data type</span></span>|<span data-ttu-id="0ea69-107">Description</span><span class="sxs-lookup"><span data-stu-id="0ea69-107">Description</span></span>|<span data-ttu-id="0ea69-108">ID de la colonne</span><span class="sxs-lookup"><span data-stu-id="0ea69-108">Column ID</span></span>|<span data-ttu-id="0ea69-109">Filtrable</span><span class="sxs-lookup"><span data-stu-id="0ea69-109">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="0ea69-110">**ApplicationName**</span><span class="sxs-lookup"><span data-stu-id="0ea69-110">**ApplicationName**</span></span>|<span data-ttu-id="0ea69-111">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="0ea69-111">**nvarchar**</span></span>|<span data-ttu-id="0ea69-112">Nom de l’application cliente qui a créé la connexion à une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0ea69-112">Name of the client application that created the connection to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0ea69-113">Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.</span><span class="sxs-lookup"><span data-stu-id="0ea69-113">This column is populated with the values passed by the application rather than the displayed name of the program.</span></span>|<span data-ttu-id="0ea69-114">10</span><span class="sxs-lookup"><span data-stu-id="0ea69-114">10</span></span>|<span data-ttu-id="0ea69-115">Oui</span><span class="sxs-lookup"><span data-stu-id="0ea69-115">Yes</span></span>|  
|<span data-ttu-id="0ea69-116">**ClientProcessID**</span><span class="sxs-lookup"><span data-stu-id="0ea69-116">**ClientProcessID**</span></span>|<span data-ttu-id="0ea69-117">**int**</span><span class="sxs-lookup"><span data-stu-id="0ea69-117">**int**</span></span>|<span data-ttu-id="0ea69-118">ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente.</span><span class="sxs-lookup"><span data-stu-id="0ea69-118">ID assigned by the host computer to the process where the client application is running.</span></span> <span data-ttu-id="0ea69-119">La colonne de données est remplie si le client fournit l'ID du processus client.</span><span class="sxs-lookup"><span data-stu-id="0ea69-119">This data column is populated if the client provides the client process ID.</span></span>|<span data-ttu-id="0ea69-120">9</span><span class="sxs-lookup"><span data-stu-id="0ea69-120">9</span></span>|<span data-ttu-id="0ea69-121">Oui</span><span class="sxs-lookup"><span data-stu-id="0ea69-121">Yes</span></span>|  
|<span data-ttu-id="0ea69-122">**DatabaseID**</span><span class="sxs-lookup"><span data-stu-id="0ea69-122">**DatabaseID**</span></span>|<span data-ttu-id="0ea69-123">**int**</span><span class="sxs-lookup"><span data-stu-id="0ea69-123">**int**</span></span>|<span data-ttu-id="0ea69-124">ID de la base de données spécifiée par l'instruction USE *database* ou celui de la base de données par défaut si aucune instruction USE *database* n'a été spécifiée pour une instance donnée.</span><span class="sxs-lookup"><span data-stu-id="0ea69-124">ID of the database specified by the USE *database* statement or the default database if no USE *database* statement has been issued for a given instance.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="0ea69-125">affiche le nom de la base de données si la colonne de données **ServerName** du serveur est capturée dans la trace et que le serveur est disponible.</span><span class="sxs-lookup"><span data-stu-id="0ea69-125">displays the name of the database if the **ServerName** data column is captured in the trace and the server is available.</span></span> <span data-ttu-id="0ea69-126">Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.</span><span class="sxs-lookup"><span data-stu-id="0ea69-126">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="0ea69-127">3</span><span class="sxs-lookup"><span data-stu-id="0ea69-127">3</span></span>|<span data-ttu-id="0ea69-128">Oui</span><span class="sxs-lookup"><span data-stu-id="0ea69-128">Yes</span></span>|  
|<span data-ttu-id="0ea69-129">**DatabaseName**</span><span class="sxs-lookup"><span data-stu-id="0ea69-129">**DatabaseName**</span></span>|<span data-ttu-id="0ea69-130">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="0ea69-130">**nvarchar**</span></span>|<span data-ttu-id="0ea69-131">Nom de la base de données dans laquelle l'instruction de l'utilisateur est exécutée.</span><span class="sxs-lookup"><span data-stu-id="0ea69-131">Name of the database in which the user statement is running.</span></span>|<span data-ttu-id="0ea69-132">35</span><span class="sxs-lookup"><span data-stu-id="0ea69-132">35</span></span>|<span data-ttu-id="0ea69-133">Oui</span><span class="sxs-lookup"><span data-stu-id="0ea69-133">Yes</span></span>|  
|<span data-ttu-id="0ea69-134">**DBUserName**</span><span class="sxs-lookup"><span data-stu-id="0ea69-134">**DBUserName**</span></span>|<span data-ttu-id="0ea69-135">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="0ea69-135">**nvarchar**</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="0ea69-136">du client.</span><span class="sxs-lookup"><span data-stu-id="0ea69-136">user name of the client.</span></span>|<span data-ttu-id="0ea69-137">40</span><span class="sxs-lookup"><span data-stu-id="0ea69-137">40</span></span>|<span data-ttu-id="0ea69-138">Oui</span><span class="sxs-lookup"><span data-stu-id="0ea69-138">Yes</span></span>|  
|<span data-ttu-id="0ea69-139">**EventClass**</span><span class="sxs-lookup"><span data-stu-id="0ea69-139">**EventClass**</span></span>|<span data-ttu-id="0ea69-140">**int**</span><span class="sxs-lookup"><span data-stu-id="0ea69-140">**int**</span></span>|<span data-ttu-id="0ea69-141">Type d’événement = 152.</span><span class="sxs-lookup"><span data-stu-id="0ea69-141">Type of event = 152.</span></span>|<span data-ttu-id="0ea69-142">27</span><span class="sxs-lookup"><span data-stu-id="0ea69-142">27</span></span>|<span data-ttu-id="0ea69-143">Non</span><span class="sxs-lookup"><span data-stu-id="0ea69-143">No</span></span>|  
|<span data-ttu-id="0ea69-144">**EventSequence**</span><span class="sxs-lookup"><span data-stu-id="0ea69-144">**EventSequence**</span></span>|<span data-ttu-id="0ea69-145">**int**</span><span class="sxs-lookup"><span data-stu-id="0ea69-145">**int**</span></span>|<span data-ttu-id="0ea69-146">Séquence d'un événement donné au sein de la demande.</span><span class="sxs-lookup"><span data-stu-id="0ea69-146">Sequence of a given event within the request.</span></span>|<span data-ttu-id="0ea69-147">51</span><span class="sxs-lookup"><span data-stu-id="0ea69-147">51</span></span>|<span data-ttu-id="0ea69-148">Non</span><span class="sxs-lookup"><span data-stu-id="0ea69-148">No</span></span>|  
|<span data-ttu-id="0ea69-149">**HostName**</span><span class="sxs-lookup"><span data-stu-id="0ea69-149">**HostName**</span></span>|<span data-ttu-id="0ea69-150">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="0ea69-150">**nvarchar**</span></span>|<span data-ttu-id="0ea69-151">Nom de l'ordinateur sur lequel le client est exécuté.</span><span class="sxs-lookup"><span data-stu-id="0ea69-151">Name of the computer on which the client is running.</span></span> <span data-ttu-id="0ea69-152">La colonne de données est remplie si le client fournit le nom de l'hôte.</span><span class="sxs-lookup"><span data-stu-id="0ea69-152">This data column is populated if the client provides the host name.</span></span> <span data-ttu-id="0ea69-153">Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.</span><span class="sxs-lookup"><span data-stu-id="0ea69-153">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="0ea69-154">8</span><span class="sxs-lookup"><span data-stu-id="0ea69-154">8</span></span>|<span data-ttu-id="0ea69-155">Oui</span><span class="sxs-lookup"><span data-stu-id="0ea69-155">Yes</span></span>|  
|<span data-ttu-id="0ea69-156">**IsSystem**</span><span class="sxs-lookup"><span data-stu-id="0ea69-156">**IsSystem**</span></span>|<span data-ttu-id="0ea69-157">**int**</span><span class="sxs-lookup"><span data-stu-id="0ea69-157">**int**</span></span>|<span data-ttu-id="0ea69-158">Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0ea69-158">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="0ea69-159">1 = système, 0 = utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0ea69-159">1 = system, 0 = user.</span></span>|<span data-ttu-id="0ea69-160">60</span><span class="sxs-lookup"><span data-stu-id="0ea69-160">60</span></span>|<span data-ttu-id="0ea69-161">Oui</span><span class="sxs-lookup"><span data-stu-id="0ea69-161">Yes</span></span>|  
|<span data-ttu-id="0ea69-162">**LoginName**</span><span class="sxs-lookup"><span data-stu-id="0ea69-162">**LoginName**</span></span>|<span data-ttu-id="0ea69-163">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="0ea69-163">**nvarchar**</span></span>|<span data-ttu-id="0ea69-164">Nom de la connexion de l'utilisateur (soit la connexion de sécurité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , soit les informations d'identification de connexion [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows au format DOMAINE\nom_utilisateur).</span><span class="sxs-lookup"><span data-stu-id="0ea69-164">Name of the login of the user (either the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security login or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows login credentials in the form of DOMAIN\username).</span></span>|<span data-ttu-id="0ea69-165">11</span><span class="sxs-lookup"><span data-stu-id="0ea69-165">11</span></span>|<span data-ttu-id="0ea69-166">Oui</span><span class="sxs-lookup"><span data-stu-id="0ea69-166">Yes</span></span>|  
|<span data-ttu-id="0ea69-167">**LoginSid**</span><span class="sxs-lookup"><span data-stu-id="0ea69-167">**LoginSid**</span></span>|<span data-ttu-id="0ea69-168">**image**</span><span class="sxs-lookup"><span data-stu-id="0ea69-168">**image**</span></span>|<span data-ttu-id="0ea69-169">Numéro d'identification de sécurité (SID) de l'utilisateur connecté.</span><span class="sxs-lookup"><span data-stu-id="0ea69-169">Security identification number (SID) of the logged-in user.</span></span> <span data-ttu-id="0ea69-170">Vous pouvez trouver ces informations dans l’affichage catalogue **sys.server_principals** .</span><span class="sxs-lookup"><span data-stu-id="0ea69-170">You can find this information in the **sys.server_principals** catalog view.</span></span> <span data-ttu-id="0ea69-171">Chaque connexion possède un SID unique au niveau du serveur.</span><span class="sxs-lookup"><span data-stu-id="0ea69-171">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="0ea69-172">41</span><span class="sxs-lookup"><span data-stu-id="0ea69-172">41</span></span>|<span data-ttu-id="0ea69-173">Oui</span><span class="sxs-lookup"><span data-stu-id="0ea69-173">Yes</span></span>|  
|<span data-ttu-id="0ea69-174">**NTDomainName**</span><span class="sxs-lookup"><span data-stu-id="0ea69-174">**NTDomainName**</span></span>|<span data-ttu-id="0ea69-175">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="0ea69-175">**nvarchar**</span></span>|<span data-ttu-id="0ea69-176">Domaine Windows auquel appartient l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0ea69-176">Windows domain to which the user belongs.</span></span>|<span data-ttu-id="0ea69-177">7</span><span class="sxs-lookup"><span data-stu-id="0ea69-177">7</span></span>|<span data-ttu-id="0ea69-178">Oui</span><span class="sxs-lookup"><span data-stu-id="0ea69-178">Yes</span></span>|  
|<span data-ttu-id="0ea69-179">**NTUserName**</span><span class="sxs-lookup"><span data-stu-id="0ea69-179">**NTUserName**</span></span>|<span data-ttu-id="0ea69-180">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="0ea69-180">**nvarchar**</span></span>|<span data-ttu-id="0ea69-181">Nom d'utilisateur Windows.</span><span class="sxs-lookup"><span data-stu-id="0ea69-181">Windows user name.</span></span>|<span data-ttu-id="0ea69-182">6</span><span class="sxs-lookup"><span data-stu-id="0ea69-182">6</span></span>|<span data-ttu-id="0ea69-183">Oui</span><span class="sxs-lookup"><span data-stu-id="0ea69-183">Yes</span></span>|  
|<span data-ttu-id="0ea69-184">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="0ea69-184">**RequestID**</span></span>|<span data-ttu-id="0ea69-185">**int**</span><span class="sxs-lookup"><span data-stu-id="0ea69-185">**int**</span></span>|<span data-ttu-id="0ea69-186">ID de la demande contenant l'instruction.</span><span class="sxs-lookup"><span data-stu-id="0ea69-186">ID of the request containing the statement.</span></span>|<span data-ttu-id="0ea69-187">49</span><span class="sxs-lookup"><span data-stu-id="0ea69-187">49</span></span>|<span data-ttu-id="0ea69-188">Oui</span><span class="sxs-lookup"><span data-stu-id="0ea69-188">Yes</span></span>|  
|<span data-ttu-id="0ea69-189">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="0ea69-189">**ServerName**</span></span>|<span data-ttu-id="0ea69-190">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="0ea69-190">**nvarchar**</span></span>|<span data-ttu-id="0ea69-191">Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.</span><span class="sxs-lookup"><span data-stu-id="0ea69-191">Name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="0ea69-192">26</span><span class="sxs-lookup"><span data-stu-id="0ea69-192">26</span></span>|<span data-ttu-id="0ea69-193">Non</span><span class="sxs-lookup"><span data-stu-id="0ea69-193">No</span></span>|  
|<span data-ttu-id="0ea69-194">**SessionLoginName**</span><span class="sxs-lookup"><span data-stu-id="0ea69-194">**SessionLoginName**</span></span>|<span data-ttu-id="0ea69-195">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="0ea69-195">**nvarchar**</span></span>|<span data-ttu-id="0ea69-196">Nom de connexion de l'utilisateur à l'origine de la session.</span><span class="sxs-lookup"><span data-stu-id="0ea69-196">Login name of the user who originated the session.</span></span> <span data-ttu-id="0ea69-197">Par exemple, si vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au moyen de Login1 et que vous exécutez une commande en tant que Login2, **SessionLoginName** affiche Login1 et **LoginName** affiche Login2.</span><span class="sxs-lookup"><span data-stu-id="0ea69-197">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, **SessionLoginName** shows Login1 and **LoginName** shows Login2.</span></span> <span data-ttu-id="0ea69-198">Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Windows.</span><span class="sxs-lookup"><span data-stu-id="0ea69-198">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows logins.</span></span>|<span data-ttu-id="0ea69-199">64</span><span class="sxs-lookup"><span data-stu-id="0ea69-199">64</span></span>|<span data-ttu-id="0ea69-200">Oui</span><span class="sxs-lookup"><span data-stu-id="0ea69-200">Yes</span></span>|  
|<span data-ttu-id="0ea69-201">**SPID**</span><span class="sxs-lookup"><span data-stu-id="0ea69-201">**SPID**</span></span>|<span data-ttu-id="0ea69-202">**int**</span><span class="sxs-lookup"><span data-stu-id="0ea69-202">**int**</span></span>|<span data-ttu-id="0ea69-203">ID de la session au cours de laquelle l'événement s'est produit.</span><span class="sxs-lookup"><span data-stu-id="0ea69-203">ID of the session on which the even occurred.</span></span>|<span data-ttu-id="0ea69-204">12</span><span class="sxs-lookup"><span data-stu-id="0ea69-204">12</span></span>|<span data-ttu-id="0ea69-205">Oui</span><span class="sxs-lookup"><span data-stu-id="0ea69-205">Yes</span></span>|  
|<span data-ttu-id="0ea69-206">**StartTime**</span><span class="sxs-lookup"><span data-stu-id="0ea69-206">**StartTime**</span></span>|<span data-ttu-id="0ea69-207">**datetime**</span><span class="sxs-lookup"><span data-stu-id="0ea69-207">**datetime**</span></span>|<span data-ttu-id="0ea69-208">Heure à laquelle a débuté l'événement, si elle est connue.</span><span class="sxs-lookup"><span data-stu-id="0ea69-208">Time at which the event started, if available.</span></span>|<span data-ttu-id="0ea69-209">14</span><span class="sxs-lookup"><span data-stu-id="0ea69-209">14</span></span>|<span data-ttu-id="0ea69-210">Oui</span><span class="sxs-lookup"><span data-stu-id="0ea69-210">Yes</span></span>|  
|<span data-ttu-id="0ea69-211">**Success**</span><span class="sxs-lookup"><span data-stu-id="0ea69-211">**Success**</span></span>|<span data-ttu-id="0ea69-212">**int**</span><span class="sxs-lookup"><span data-stu-id="0ea69-212">**int**</span></span>|<span data-ttu-id="0ea69-213">1 = réussite.</span><span class="sxs-lookup"><span data-stu-id="0ea69-213">1 = success.</span></span> <span data-ttu-id="0ea69-214">0 = échec.</span><span class="sxs-lookup"><span data-stu-id="0ea69-214">0 = failure.</span></span> <span data-ttu-id="0ea69-215">Exemple : 1 indique la réussite de la vérification d'autorisations, 0 l'échec de cette vérification.</span><span class="sxs-lookup"><span data-stu-id="0ea69-215">For example, a value of 1 indicates success of a permissions check and a value of 0 indicates a failure of that check).</span></span>|<span data-ttu-id="0ea69-216">23</span><span class="sxs-lookup"><span data-stu-id="0ea69-216">23</span></span>|<span data-ttu-id="0ea69-217">Oui</span><span class="sxs-lookup"><span data-stu-id="0ea69-217">Yes</span></span>|  
|<span data-ttu-id="0ea69-218">**TargetLoginName**</span><span class="sxs-lookup"><span data-stu-id="0ea69-218">**TargetLoginName**</span></span>|<span data-ttu-id="0ea69-219">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="0ea69-219">**nvarchar**</span></span>|<span data-ttu-id="0ea69-220">Pour les actions qui ciblent une connexion, le nom de la connexion ciblée.</span><span class="sxs-lookup"><span data-stu-id="0ea69-220">For actions that target a login, the name of the targeted login.</span></span>|<span data-ttu-id="0ea69-221">42</span><span class="sxs-lookup"><span data-stu-id="0ea69-221">42</span></span>|<span data-ttu-id="0ea69-222">Oui</span><span class="sxs-lookup"><span data-stu-id="0ea69-222">Yes</span></span>|  
|<span data-ttu-id="0ea69-223">**TargetLoginSid**</span><span class="sxs-lookup"><span data-stu-id="0ea69-223">**TargetLoginSid**</span></span>|<span data-ttu-id="0ea69-224">**image**</span><span class="sxs-lookup"><span data-stu-id="0ea69-224">**image**</span></span>|<span data-ttu-id="0ea69-225">Pour les actions qui ciblent une connexion, le numéro d'identification de sécurité de la connexion ciblée.</span><span class="sxs-lookup"><span data-stu-id="0ea69-225">For actions that target a login, the security identification number (SID) of the targeted login.</span></span>|<span data-ttu-id="0ea69-226">43</span><span class="sxs-lookup"><span data-stu-id="0ea69-226">43</span></span>|<span data-ttu-id="0ea69-227">Oui</span><span class="sxs-lookup"><span data-stu-id="0ea69-227">Yes</span></span>|  
|<span data-ttu-id="0ea69-228">**TargetUserName**</span><span class="sxs-lookup"><span data-stu-id="0ea69-228">**TargetUserName**</span></span>|<span data-ttu-id="0ea69-229">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="0ea69-229">**nvarchar**</span></span>|<span data-ttu-id="0ea69-230">Pour les actions qui ciblent un utilisateur de base de données (par exemple, accorder une autorisation à un utilisateur), le nom de cet utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0ea69-230">For actions that target a database user (for example, granting permission to a user), the name of that user.</span></span>|<span data-ttu-id="0ea69-231">39</span><span class="sxs-lookup"><span data-stu-id="0ea69-231">39</span></span>|<span data-ttu-id="0ea69-232">Oui</span><span class="sxs-lookup"><span data-stu-id="0ea69-232">Yes</span></span>|  
|<span data-ttu-id="0ea69-233">**TransactionID**</span><span class="sxs-lookup"><span data-stu-id="0ea69-233">**TransactionID**</span></span>|<span data-ttu-id="0ea69-234">**bigint**</span><span class="sxs-lookup"><span data-stu-id="0ea69-234">**bigint**</span></span>|<span data-ttu-id="0ea69-235">ID affecté par le système à la transaction.</span><span class="sxs-lookup"><span data-stu-id="0ea69-235">System-assigned ID of the transaction.</span></span>|<span data-ttu-id="0ea69-236">4</span><span class="sxs-lookup"><span data-stu-id="0ea69-236">4</span></span>|<span data-ttu-id="0ea69-237">Oui</span><span class="sxs-lookup"><span data-stu-id="0ea69-237">Yes</span></span>|  
|<span data-ttu-id="0ea69-238">**XactSequence**</span><span class="sxs-lookup"><span data-stu-id="0ea69-238">**XactSequence**</span></span>|<span data-ttu-id="0ea69-239">**bigint**</span><span class="sxs-lookup"><span data-stu-id="0ea69-239">**bigint**</span></span>|<span data-ttu-id="0ea69-240">Jeton utilisé pour décrire la transaction en cours.</span><span class="sxs-lookup"><span data-stu-id="0ea69-240">Token used to describe the current transaction.</span></span>|<span data-ttu-id="0ea69-241">50</span><span class="sxs-lookup"><span data-stu-id="0ea69-241">50</span></span>|<span data-ttu-id="0ea69-242">Oui</span><span class="sxs-lookup"><span data-stu-id="0ea69-242">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0ea69-243">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0ea69-243">See Also</span></span>  
 <span data-ttu-id="0ea69-244">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0ea69-244">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 [<span data-ttu-id="0ea69-245">ALTER AUTHORIZATION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0ea69-245">ALTER AUTHORIZATION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-authorization-transact-sql)  
  
  