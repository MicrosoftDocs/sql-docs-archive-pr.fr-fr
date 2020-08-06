---
title: Log File Auto Shrink, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Log File Auto Shrink event class
ms.assetid: 4bf82a13-9985-4f20-9ef8-0083f104d124
author: stevestein
ms.author: sstein
ms.openlocfilehash: 59bcc5bda489edcd337bba78bd07d55ff0a28806
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612371"
---
# <a name="log-file-auto-shrink-event-class"></a><span data-ttu-id="b5f96-102">Log File Auto Shrink (classe d'événements)</span><span class="sxs-lookup"><span data-stu-id="b5f96-102">Log File Auto Shrink Event Class</span></span>
  <span data-ttu-id="b5f96-103">La classe d’événements **Log File Auto Shrink** indique que le fichier journal s’est réduit automatiquement.</span><span class="sxs-lookup"><span data-stu-id="b5f96-103">The **Log File Auto Shrink** event class indicates that the log file shrank automatically.</span></span> <span data-ttu-id="b5f96-104">Cet événement ne se déclenche pas si le fichier journal se réduit à la suite d'une instruction explicite ALTER DATABASE.</span><span class="sxs-lookup"><span data-stu-id="b5f96-104">This event is not triggered if the log file shrinks because of an explicit ALTER DATABASE statement.</span></span>  
  
 <span data-ttu-id="b5f96-105">Incluez la classe d’événements **Log File Auto Shrink** dans les traces chargées de surveiller la réduction du fichier journal.</span><span class="sxs-lookup"><span data-stu-id="b5f96-105">Include the **Log File Auto Shrink** event class in traces that monitor the shrinking of the log file.</span></span> <span data-ttu-id="b5f96-106">Quand cette classe d’événements est incluse dans une trace, la surcharge supportée est faible, sauf si le fichier rétrécit fréquemment.</span><span class="sxs-lookup"><span data-stu-id="b5f96-106">When thisevent class is included in a trace the amount of overhead incurred will be low unless the file frequently shrinks.</span></span>  
  
## <a name="log-file-auto-shrink-event-class-data-columns"></a><span data-ttu-id="b5f96-107">Colonnes de données de la classe d'événements Log File Auto Shrink</span><span class="sxs-lookup"><span data-stu-id="b5f96-107">Log File Auto Shrink Event Class Data Columns</span></span>  
  
|<span data-ttu-id="b5f96-108">Nom de la colonne de données</span><span class="sxs-lookup"><span data-stu-id="b5f96-108">Data column name</span></span>|<span data-ttu-id="b5f96-109">Type de données</span><span class="sxs-lookup"><span data-stu-id="b5f96-109">Data type</span></span>|<span data-ttu-id="b5f96-110">Description</span><span class="sxs-lookup"><span data-stu-id="b5f96-110">Description</span></span>|<span data-ttu-id="b5f96-111">ID de la colonne</span><span class="sxs-lookup"><span data-stu-id="b5f96-111">Column ID</span></span>|<span data-ttu-id="b5f96-112">Filtrable</span><span class="sxs-lookup"><span data-stu-id="b5f96-112">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="b5f96-113">**ApplicationName**</span><span class="sxs-lookup"><span data-stu-id="b5f96-113">**ApplicationName**</span></span>|<span data-ttu-id="b5f96-114">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="b5f96-114">**nvarchar**</span></span>|<span data-ttu-id="b5f96-115">Nom de l'application cliente qui a créé la connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b5f96-115">Name of the client application that created the connection to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b5f96-116">Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.</span><span class="sxs-lookup"><span data-stu-id="b5f96-116">This column is populated with the values passed by the application rather than the displayed name of the program.</span></span>|<span data-ttu-id="b5f96-117">10</span><span class="sxs-lookup"><span data-stu-id="b5f96-117">10</span></span>|<span data-ttu-id="b5f96-118">Oui</span><span class="sxs-lookup"><span data-stu-id="b5f96-118">Yes</span></span>|  
|<span data-ttu-id="b5f96-119">**ClientProcessID**</span><span class="sxs-lookup"><span data-stu-id="b5f96-119">**ClientProcessID**</span></span>|<span data-ttu-id="b5f96-120">**Int**</span><span class="sxs-lookup"><span data-stu-id="b5f96-120">**Int**</span></span>|<span data-ttu-id="b5f96-121">ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente.</span><span class="sxs-lookup"><span data-stu-id="b5f96-121">ID assigned by the host computer to the process where the client application is running.</span></span> <span data-ttu-id="b5f96-122">La colonne de données est remplie si le client fournit l'ID du processus client.</span><span class="sxs-lookup"><span data-stu-id="b5f96-122">This data column is populated if the client provides the client process ID.</span></span>|<span data-ttu-id="b5f96-123">9</span><span class="sxs-lookup"><span data-stu-id="b5f96-123">9</span></span>|<span data-ttu-id="b5f96-124">Oui</span><span class="sxs-lookup"><span data-stu-id="b5f96-124">Yes</span></span>|  
|<span data-ttu-id="b5f96-125">**DatabaseID**</span><span class="sxs-lookup"><span data-stu-id="b5f96-125">**DatabaseID**</span></span>|<span data-ttu-id="b5f96-126">**int**</span><span class="sxs-lookup"><span data-stu-id="b5f96-126">**int**</span></span>|<span data-ttu-id="b5f96-127">ID de la base de données spécifiée par l'instruction USE *database* ou celui de la base de données par défaut si aucune instruction USE *database* n'a été spécifiée pour une instance donnée.</span><span class="sxs-lookup"><span data-stu-id="b5f96-127">ID of the database specified by the USE *database* statement or the default database if no USE *database* statement has been issued for a given instance.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="b5f96-128">affiche le nom de la base de données si la colonne de données **ServerName** du serveur est capturée dans la trace et que le serveur est disponible.</span><span class="sxs-lookup"><span data-stu-id="b5f96-128">displays the name of the database if the **ServerName** data column is captured in the trace and the server is available.</span></span> <span data-ttu-id="b5f96-129">Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.</span><span class="sxs-lookup"><span data-stu-id="b5f96-129">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="b5f96-130">3</span><span class="sxs-lookup"><span data-stu-id="b5f96-130">3</span></span>|<span data-ttu-id="b5f96-131">Oui</span><span class="sxs-lookup"><span data-stu-id="b5f96-131">Yes</span></span>|  
|<span data-ttu-id="b5f96-132">**DatabaseName**</span><span class="sxs-lookup"><span data-stu-id="b5f96-132">**DatabaseName**</span></span>|<span data-ttu-id="b5f96-133">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="b5f96-133">**nvarchar**</span></span>|<span data-ttu-id="b5f96-134">Nom de la base de données dans laquelle l'instruction de l'utilisateur est exécutée.</span><span class="sxs-lookup"><span data-stu-id="b5f96-134">Name of the database in which the user statement is running.</span></span>|<span data-ttu-id="b5f96-135">35</span><span class="sxs-lookup"><span data-stu-id="b5f96-135">35</span></span>|<span data-ttu-id="b5f96-136">Oui</span><span class="sxs-lookup"><span data-stu-id="b5f96-136">Yes</span></span>|  
|<span data-ttu-id="b5f96-137">**Durée**</span><span class="sxs-lookup"><span data-stu-id="b5f96-137">**Duration**</span></span>|<span data-ttu-id="b5f96-138">**bigint**</span><span class="sxs-lookup"><span data-stu-id="b5f96-138">**bigint**</span></span>|<span data-ttu-id="b5f96-139">Durée (en millisecondes) requise pour étendre le fichier.</span><span class="sxs-lookup"><span data-stu-id="b5f96-139">Length of time (in milliseconds) necessary to extend the file.</span></span>|<span data-ttu-id="b5f96-140">13</span><span class="sxs-lookup"><span data-stu-id="b5f96-140">13</span></span>|<span data-ttu-id="b5f96-141">Oui</span><span class="sxs-lookup"><span data-stu-id="b5f96-141">Yes</span></span>|  
|<span data-ttu-id="b5f96-142">**EndTime**</span><span class="sxs-lookup"><span data-stu-id="b5f96-142">**EndTime**</span></span>|<span data-ttu-id="b5f96-143">**datetime**</span><span class="sxs-lookup"><span data-stu-id="b5f96-143">**datetime**</span></span>|<span data-ttu-id="b5f96-144">Heure de fin de la **réduction automatique** du fichier journal.</span><span class="sxs-lookup"><span data-stu-id="b5f96-144">Time that the log file **Auto Shrink** ended.</span></span>|<span data-ttu-id="b5f96-145">18</span><span class="sxs-lookup"><span data-stu-id="b5f96-145">18</span></span>|<span data-ttu-id="b5f96-146">Oui</span><span class="sxs-lookup"><span data-stu-id="b5f96-146">Yes</span></span>|  
|<span data-ttu-id="b5f96-147">**EventClass**</span><span class="sxs-lookup"><span data-stu-id="b5f96-147">**EventClass**</span></span>|<span data-ttu-id="b5f96-148">**int**</span><span class="sxs-lookup"><span data-stu-id="b5f96-148">**int**</span></span>|<span data-ttu-id="b5f96-149">Type d’événement = 95.</span><span class="sxs-lookup"><span data-stu-id="b5f96-149">Type of event = 95.</span></span>|<span data-ttu-id="b5f96-150">27</span><span class="sxs-lookup"><span data-stu-id="b5f96-150">27</span></span>|<span data-ttu-id="b5f96-151">Non</span><span class="sxs-lookup"><span data-stu-id="b5f96-151">No</span></span>|  
|<span data-ttu-id="b5f96-152">**EventSequence**</span><span class="sxs-lookup"><span data-stu-id="b5f96-152">**EventSequence**</span></span>|<span data-ttu-id="b5f96-153">**int**</span><span class="sxs-lookup"><span data-stu-id="b5f96-153">**int**</span></span>|<span data-ttu-id="b5f96-154">Séquence de la classe d’événements **CursorClose** dans le lot.</span><span class="sxs-lookup"><span data-stu-id="b5f96-154">Sequence of the **CursorClose** event class in the batch.</span></span>|<span data-ttu-id="b5f96-155">51</span><span class="sxs-lookup"><span data-stu-id="b5f96-155">51</span></span>|<span data-ttu-id="b5f96-156">Non</span><span class="sxs-lookup"><span data-stu-id="b5f96-156">No</span></span>|  
|<span data-ttu-id="b5f96-157">**Nom du fichier**</span><span class="sxs-lookup"><span data-stu-id="b5f96-157">**Filename**</span></span>|<span data-ttu-id="b5f96-158">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="b5f96-158">**nvarchar**</span></span>|<span data-ttu-id="b5f96-159">Nom logique du fichier étendu</span><span class="sxs-lookup"><span data-stu-id="b5f96-159">Logical name of the file being extended.</span></span>|<span data-ttu-id="b5f96-160">36</span><span class="sxs-lookup"><span data-stu-id="b5f96-160">36</span></span>|<span data-ttu-id="b5f96-161">Oui</span><span class="sxs-lookup"><span data-stu-id="b5f96-161">Yes</span></span>|  
|<span data-ttu-id="b5f96-162">**HostName**</span><span class="sxs-lookup"><span data-stu-id="b5f96-162">**HostName**</span></span>|<span data-ttu-id="b5f96-163">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="b5f96-163">**nvarchar**</span></span>|<span data-ttu-id="b5f96-164">Nom de l'ordinateur sur lequel le client est exécuté.</span><span class="sxs-lookup"><span data-stu-id="b5f96-164">Name of the computer on which the client is running.</span></span> <span data-ttu-id="b5f96-165">La colonne de données est remplie si le client fournit le nom de l'hôte.</span><span class="sxs-lookup"><span data-stu-id="b5f96-165">This data column is populated if the client provides the host name.</span></span> <span data-ttu-id="b5f96-166">Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.</span><span class="sxs-lookup"><span data-stu-id="b5f96-166">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="b5f96-167">8</span><span class="sxs-lookup"><span data-stu-id="b5f96-167">8</span></span>|<span data-ttu-id="b5f96-168">Oui</span><span class="sxs-lookup"><span data-stu-id="b5f96-168">Yes</span></span>|  
|<span data-ttu-id="b5f96-169">**IntegerData**</span><span class="sxs-lookup"><span data-stu-id="b5f96-169">**IntegerData**</span></span>|<span data-ttu-id="b5f96-170">**Int**</span><span class="sxs-lookup"><span data-stu-id="b5f96-170">**Int**</span></span>|<span data-ttu-id="b5f96-171">Nombre de pages de 8 kilo-octets (Ko) duquel le fichier a augmenté.</span><span class="sxs-lookup"><span data-stu-id="b5f96-171">Number of 8-kilobyte (KB) pages by which the file increased.</span></span>|<span data-ttu-id="b5f96-172">25</span><span class="sxs-lookup"><span data-stu-id="b5f96-172">25</span></span>|<span data-ttu-id="b5f96-173">Oui</span><span class="sxs-lookup"><span data-stu-id="b5f96-173">Yes</span></span>|  
|<span data-ttu-id="b5f96-174">**IsSystem**</span><span class="sxs-lookup"><span data-stu-id="b5f96-174">**IsSystem**</span></span>|<span data-ttu-id="b5f96-175">**int**</span><span class="sxs-lookup"><span data-stu-id="b5f96-175">**int**</span></span>|<span data-ttu-id="b5f96-176">Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b5f96-176">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="b5f96-177">1 = système, 0 = utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b5f96-177">1 = system, 0 = user.</span></span>|<span data-ttu-id="b5f96-178">60</span><span class="sxs-lookup"><span data-stu-id="b5f96-178">60</span></span>|<span data-ttu-id="b5f96-179">Oui</span><span class="sxs-lookup"><span data-stu-id="b5f96-179">Yes</span></span>|  
|<span data-ttu-id="b5f96-180">**LoginName**</span><span class="sxs-lookup"><span data-stu-id="b5f96-180">**LoginName**</span></span>|<span data-ttu-id="b5f96-181">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="b5f96-181">**nvarchar**</span></span>|<span data-ttu-id="b5f96-182">Nom de la connexion de l'utilisateur (soit la connexion de sécurité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , soit les informations d'identification de connexion [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows au format DOMAINE\nom_utilisateur).</span><span class="sxs-lookup"><span data-stu-id="b5f96-182">Name of the login of the user (either [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security login or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows login credentials in the form of DOMAIN\Username).</span></span>|<span data-ttu-id="b5f96-183">11</span><span class="sxs-lookup"><span data-stu-id="b5f96-183">11</span></span>|<span data-ttu-id="b5f96-184">Oui</span><span class="sxs-lookup"><span data-stu-id="b5f96-184">Yes</span></span>|  
|<span data-ttu-id="b5f96-185">**LoginSid**</span><span class="sxs-lookup"><span data-stu-id="b5f96-185">**LoginSid**</span></span>|<span data-ttu-id="b5f96-186">**image**</span><span class="sxs-lookup"><span data-stu-id="b5f96-186">**image**</span></span>|<span data-ttu-id="b5f96-187">Identificateur de sécurité (SID) de l'utilisateur connecté.</span><span class="sxs-lookup"><span data-stu-id="b5f96-187">Security identifier (SID) of the logged-in user.</span></span> <span data-ttu-id="b5f96-188">Vous pouvez trouver ces informations dans l’affichage catalogue **sys.server_principals** .</span><span class="sxs-lookup"><span data-stu-id="b5f96-188">You can find this information in the **sys.server_principals** catalog view.</span></span> <span data-ttu-id="b5f96-189">Chaque connexion possède un SID unique au niveau du serveur.</span><span class="sxs-lookup"><span data-stu-id="b5f96-189">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="b5f96-190">41</span><span class="sxs-lookup"><span data-stu-id="b5f96-190">41</span></span>|<span data-ttu-id="b5f96-191">Oui</span><span class="sxs-lookup"><span data-stu-id="b5f96-191">Yes</span></span>|  
|<span data-ttu-id="b5f96-192">**NTDomainName**</span><span class="sxs-lookup"><span data-stu-id="b5f96-192">**NTDomainName**</span></span>|<span data-ttu-id="b5f96-193">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="b5f96-193">**nvarchar**</span></span>|<span data-ttu-id="b5f96-194">Domaine Windows auquel appartient l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b5f96-194">Windows domain to which the user belongs.</span></span>|<span data-ttu-id="b5f96-195">7</span><span class="sxs-lookup"><span data-stu-id="b5f96-195">7</span></span>|<span data-ttu-id="b5f96-196">Oui</span><span class="sxs-lookup"><span data-stu-id="b5f96-196">Yes</span></span>|  
|<span data-ttu-id="b5f96-197">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="b5f96-197">**ServerName**</span></span>|<span data-ttu-id="b5f96-198">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="b5f96-198">**nvarchar**</span></span>|<span data-ttu-id="b5f96-199">Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.</span><span class="sxs-lookup"><span data-stu-id="b5f96-199">Name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="b5f96-200">26</span><span class="sxs-lookup"><span data-stu-id="b5f96-200">26</span></span>|<span data-ttu-id="b5f96-201">Non</span><span class="sxs-lookup"><span data-stu-id="b5f96-201">No</span></span>|  
|<span data-ttu-id="b5f96-202">**SessionLoginName**</span><span class="sxs-lookup"><span data-stu-id="b5f96-202">**SessionLoginName**</span></span>|<span data-ttu-id="b5f96-203">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="b5f96-203">**nvarchar**</span></span>|<span data-ttu-id="b5f96-204">Nom de connexion de l'utilisateur à l'origine de la session.</span><span class="sxs-lookup"><span data-stu-id="b5f96-204">Login name of the user who originated the session.</span></span> <span data-ttu-id="b5f96-205">Par exemple, si vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au moyen de Login1 et que vous exécutez une commande en tant que Login2, **SessionLoginName** affiche Login1 et **LoginName** affiche Login2.</span><span class="sxs-lookup"><span data-stu-id="b5f96-205">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, **SessionLoginName** shows Login1 and **LoginName** shows Login2.</span></span> <span data-ttu-id="b5f96-206">Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Windows.</span><span class="sxs-lookup"><span data-stu-id="b5f96-206">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows logins.</span></span>|<span data-ttu-id="b5f96-207">64</span><span class="sxs-lookup"><span data-stu-id="b5f96-207">64</span></span>|<span data-ttu-id="b5f96-208">Oui</span><span class="sxs-lookup"><span data-stu-id="b5f96-208">Yes</span></span>|  
|<span data-ttu-id="b5f96-209">**SPID**</span><span class="sxs-lookup"><span data-stu-id="b5f96-209">**SPID**</span></span>|<span data-ttu-id="b5f96-210">**Int**</span><span class="sxs-lookup"><span data-stu-id="b5f96-210">**Int**</span></span>|<span data-ttu-id="b5f96-211">ID de la session au cours de laquelle l'événement s'est produit.</span><span class="sxs-lookup"><span data-stu-id="b5f96-211">ID of the session on which the event occurred.</span></span>|<span data-ttu-id="b5f96-212">12</span><span class="sxs-lookup"><span data-stu-id="b5f96-212">12</span></span>|<span data-ttu-id="b5f96-213">Oui</span><span class="sxs-lookup"><span data-stu-id="b5f96-213">Yes</span></span>|  
|<span data-ttu-id="b5f96-214">**StartTime**</span><span class="sxs-lookup"><span data-stu-id="b5f96-214">**StartTime**</span></span>|<span data-ttu-id="b5f96-215">**datetime**</span><span class="sxs-lookup"><span data-stu-id="b5f96-215">**datetime**</span></span>|<span data-ttu-id="b5f96-216">Heure à laquelle a débuté l'événement, si elle est connue.</span><span class="sxs-lookup"><span data-stu-id="b5f96-216">Time at which the event started, if available.</span></span>|<span data-ttu-id="b5f96-217">14</span><span class="sxs-lookup"><span data-stu-id="b5f96-217">14</span></span>|<span data-ttu-id="b5f96-218">Oui</span><span class="sxs-lookup"><span data-stu-id="b5f96-218">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b5f96-219">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5f96-219">See Also</span></span>  
 [<span data-ttu-id="b5f96-220">sp_trace_setevent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b5f96-220">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  