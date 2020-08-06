---
title: 'TM: Save Tran Starting, classe d’événements | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- 'TM: Save Tran Starting event class'
ms.assetid: 6f19fe7c-a452-4323-b957-7e17d13bf8fd
author: stevestein
ms.author: sstein
ms.openlocfilehash: bc2bf8c781df287bf499f4a6d10bdd572c4129ac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87614600"
---
# <a name="tm-save-tran-starting-event-class"></a><span data-ttu-id="a3463-102">TM: Save Tran Starting, classe d'événements</span><span class="sxs-lookup"><span data-stu-id="a3463-102">TM: Save Tran Starting Event Class</span></span>
  <span data-ttu-id="a3463-103">La classe d'événements TM: Save Tran Starting indique qu'une demande SAVE TRANSACTION est en cours de démarrage.</span><span class="sxs-lookup"><span data-stu-id="a3463-103">The TM: Save Tran Starting event class indicates that a SAVE TRANSACTION request is starting.</span></span> <span data-ttu-id="a3463-104">La requête est envoyée depuis le client par le biais de l'interface de gestion des transactions.</span><span class="sxs-lookup"><span data-stu-id="a3463-104">The request is sent from the client through a transaction management interface.</span></span>  
  
## <a name="tm-save-tran-starting-event-class-data-columns"></a><span data-ttu-id="a3463-105">Colonnes de données de la classe d'événements TM: Save Tran Starting</span><span class="sxs-lookup"><span data-stu-id="a3463-105">TM: Save Tran Starting Event Class Data Columns</span></span>  
  
|<span data-ttu-id="a3463-106">Nom de la colonne de données</span><span class="sxs-lookup"><span data-stu-id="a3463-106">Data column name</span></span>|<span data-ttu-id="a3463-107">Type de données</span><span class="sxs-lookup"><span data-stu-id="a3463-107">Data type</span></span>|<span data-ttu-id="a3463-108">Description</span><span class="sxs-lookup"><span data-stu-id="a3463-108">Description</span></span>|<span data-ttu-id="a3463-109">ID de la colonne</span><span class="sxs-lookup"><span data-stu-id="a3463-109">Column ID</span></span>|<span data-ttu-id="a3463-110">Filtrable</span><span class="sxs-lookup"><span data-stu-id="a3463-110">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="a3463-111">ApplicationName</span><span class="sxs-lookup"><span data-stu-id="a3463-111">ApplicationName</span></span>|`nvarchar`|<span data-ttu-id="a3463-112">Nom de l'application cliente qui a créé la connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a3463-112">Name of the client application that created the connection to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a3463-113">Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.</span><span class="sxs-lookup"><span data-stu-id="a3463-113">This column is populated with the values passed by the application rather than the displayed name of the program.</span></span>|<span data-ttu-id="a3463-114">10</span><span class="sxs-lookup"><span data-stu-id="a3463-114">10</span></span>|<span data-ttu-id="a3463-115">Oui</span><span class="sxs-lookup"><span data-stu-id="a3463-115">Yes</span></span>|  
|<span data-ttu-id="a3463-116">ClientProcessID</span><span class="sxs-lookup"><span data-stu-id="a3463-116">ClientProcessID</span></span>|`int`|<span data-ttu-id="a3463-117">ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente.</span><span class="sxs-lookup"><span data-stu-id="a3463-117">ID assigned by the host computer to the process where the client application is running.</span></span> <span data-ttu-id="a3463-118">Cette colonne de données est remplie si l'ID du processus du client est fourni par le client.</span><span class="sxs-lookup"><span data-stu-id="a3463-118">This data column is populated if the client process ID is provided by the client.</span></span>|<span data-ttu-id="a3463-119">9</span><span class="sxs-lookup"><span data-stu-id="a3463-119">9</span></span>|<span data-ttu-id="a3463-120">Oui</span><span class="sxs-lookup"><span data-stu-id="a3463-120">Yes</span></span>|  
|<span data-ttu-id="a3463-121">DatabaseID</span><span class="sxs-lookup"><span data-stu-id="a3463-121">DatabaseID</span></span>|`int`|<span data-ttu-id="a3463-122">ID de la base de données spécifiée par l'instruction USE *database* ou celui de la base de données par défaut si aucune instruction USE *database* n'a été spécifiée pour une instance donnée.</span><span class="sxs-lookup"><span data-stu-id="a3463-122">ID of the database specified by the USE *database* statement or the default database if no USE *database* statement has been issued for a given instance.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="a3463-123">affiche le nom de la base de données si la colonne de données ServerName est capturée dans la trace et que le serveur est disponible.</span><span class="sxs-lookup"><span data-stu-id="a3463-123">displays the name of the database if the ServerName data column is captured in the trace and the server is available.</span></span> <span data-ttu-id="a3463-124">Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.</span><span class="sxs-lookup"><span data-stu-id="a3463-124">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="a3463-125">3</span><span class="sxs-lookup"><span data-stu-id="a3463-125">3</span></span>|<span data-ttu-id="a3463-126">Oui</span><span class="sxs-lookup"><span data-stu-id="a3463-126">Yes</span></span>|  
|<span data-ttu-id="a3463-127">nom_base_de_données</span><span class="sxs-lookup"><span data-stu-id="a3463-127">DatabaseName</span></span>|`nvarchar`|<span data-ttu-id="a3463-128">Nom de la base de données dans laquelle l'instruction de l'utilisateur est exécutée.</span><span class="sxs-lookup"><span data-stu-id="a3463-128">Name of the database in which the user statement is running.</span></span>|<span data-ttu-id="a3463-129">35</span><span class="sxs-lookup"><span data-stu-id="a3463-129">35</span></span>|<span data-ttu-id="a3463-130">Oui</span><span class="sxs-lookup"><span data-stu-id="a3463-130">Yes</span></span>|  
|<span data-ttu-id="a3463-131">EventClass</span><span class="sxs-lookup"><span data-stu-id="a3463-131">EventClass</span></span>|`int`|<span data-ttu-id="a3463-132">Type d’événement = 191.</span><span class="sxs-lookup"><span data-stu-id="a3463-132">Type of event = 191.</span></span>|<span data-ttu-id="a3463-133">27</span><span class="sxs-lookup"><span data-stu-id="a3463-133">27</span></span>|<span data-ttu-id="a3463-134">Non</span><span class="sxs-lookup"><span data-stu-id="a3463-134">No</span></span>|  
|<span data-ttu-id="a3463-135">EventSequence</span><span class="sxs-lookup"><span data-stu-id="a3463-135">EventSequence</span></span>|`int`|<span data-ttu-id="a3463-136">Séquence d'un événement donné au sein de la demande.</span><span class="sxs-lookup"><span data-stu-id="a3463-136">The sequence of a given event within the request.</span></span>|<span data-ttu-id="a3463-137">51</span><span class="sxs-lookup"><span data-stu-id="a3463-137">51</span></span>|<span data-ttu-id="a3463-138">Non</span><span class="sxs-lookup"><span data-stu-id="a3463-138">No</span></span>|  
|<span data-ttu-id="a3463-139">GroupID</span><span class="sxs-lookup"><span data-stu-id="a3463-139">GroupID</span></span>|`int`|<span data-ttu-id="a3463-140">ID du groupe de charges de travail où l'événement Trace SQL se déclenche.</span><span class="sxs-lookup"><span data-stu-id="a3463-140">ID of the workload group where the SQL Trace event fires.</span></span>|<span data-ttu-id="a3463-141">66</span><span class="sxs-lookup"><span data-stu-id="a3463-141">66</span></span>|<span data-ttu-id="a3463-142">Oui</span><span class="sxs-lookup"><span data-stu-id="a3463-142">Yes</span></span>|  
|<span data-ttu-id="a3463-143">HostName</span><span class="sxs-lookup"><span data-stu-id="a3463-143">HostName</span></span>|`nvarchar`|<span data-ttu-id="a3463-144">Nom de l'ordinateur sur lequel le client est exécuté.</span><span class="sxs-lookup"><span data-stu-id="a3463-144">Name of the computer on which the client is running.</span></span> <span data-ttu-id="a3463-145">La colonne de données est remplie si le client fournit le nom de l'hôte.</span><span class="sxs-lookup"><span data-stu-id="a3463-145">This data column is populated if the client provides the host name.</span></span> <span data-ttu-id="a3463-146">Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.</span><span class="sxs-lookup"><span data-stu-id="a3463-146">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="a3463-147">8</span><span class="sxs-lookup"><span data-stu-id="a3463-147">8</span></span>|<span data-ttu-id="a3463-148">Oui</span><span class="sxs-lookup"><span data-stu-id="a3463-148">Yes</span></span>|  
|<span data-ttu-id="a3463-149">IsSystem</span><span class="sxs-lookup"><span data-stu-id="a3463-149">IsSystem</span></span>|`int`|<span data-ttu-id="a3463-150">Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a3463-150">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="a3463-151">1 = système, 0 = utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a3463-151">1 = system, 0 = user.</span></span>|<span data-ttu-id="a3463-152">60</span><span class="sxs-lookup"><span data-stu-id="a3463-152">60</span></span>|<span data-ttu-id="a3463-153">Oui</span><span class="sxs-lookup"><span data-stu-id="a3463-153">Yes</span></span>|  
|<span data-ttu-id="a3463-154">LoginName</span><span class="sxs-lookup"><span data-stu-id="a3463-154">LoginName</span></span>|`nvarchar`|<span data-ttu-id="a3463-155">Nom de la connexion de l'utilisateur (soit la connexion de sécurité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , soit les informations d'identification de connexion [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows au format DOMAINE\nom_utilisateur).</span><span class="sxs-lookup"><span data-stu-id="a3463-155">Name of the login of the user (either [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security login or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows login credentials in the form of DOMAIN\username).</span></span>|<span data-ttu-id="a3463-156">11</span><span class="sxs-lookup"><span data-stu-id="a3463-156">11</span></span>|<span data-ttu-id="a3463-157">Oui</span><span class="sxs-lookup"><span data-stu-id="a3463-157">Yes</span></span>|  
|<span data-ttu-id="a3463-158">LoginSid</span><span class="sxs-lookup"><span data-stu-id="a3463-158">LoginSid</span></span>|`image`|<span data-ttu-id="a3463-159">Identificateur de sécurité (SID) de l'utilisateur connecté.</span><span class="sxs-lookup"><span data-stu-id="a3463-159">Security identifier (SID) of the logged-in user.</span></span> <span data-ttu-id="a3463-160">Vous pouvez trouver ces informations dans l'affichage catalogue sys.server_principals.</span><span class="sxs-lookup"><span data-stu-id="a3463-160">You can find this information in the sys.server_principals catalog view.</span></span> <span data-ttu-id="a3463-161">Chaque connexion possède un SID unique au niveau du serveur.</span><span class="sxs-lookup"><span data-stu-id="a3463-161">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="a3463-162">41</span><span class="sxs-lookup"><span data-stu-id="a3463-162">41</span></span>|<span data-ttu-id="a3463-163">Oui</span><span class="sxs-lookup"><span data-stu-id="a3463-163">Yes</span></span>|  
|<span data-ttu-id="a3463-164">NTDomainName</span><span class="sxs-lookup"><span data-stu-id="a3463-164">NTDomainName</span></span>|`nvarchar`|<span data-ttu-id="a3463-165">Domaine Windows auquel appartient l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a3463-165">Windows domain to which the user belongs.</span></span>|<span data-ttu-id="a3463-166">7</span><span class="sxs-lookup"><span data-stu-id="a3463-166">7</span></span>|<span data-ttu-id="a3463-167">Oui</span><span class="sxs-lookup"><span data-stu-id="a3463-167">Yes</span></span>|  
|<span data-ttu-id="a3463-168">NTUserName</span><span class="sxs-lookup"><span data-stu-id="a3463-168">NTUserName</span></span>|`nvarchar`|<span data-ttu-id="a3463-169">Nom d'utilisateur Windows.</span><span class="sxs-lookup"><span data-stu-id="a3463-169">Windows user name.</span></span>|<span data-ttu-id="a3463-170">6</span><span class="sxs-lookup"><span data-stu-id="a3463-170">6</span></span>|<span data-ttu-id="a3463-171">Oui</span><span class="sxs-lookup"><span data-stu-id="a3463-171">Yes</span></span>|  
|<span data-ttu-id="a3463-172">RequestID</span><span class="sxs-lookup"><span data-stu-id="a3463-172">RequestID</span></span>|`int`|<span data-ttu-id="a3463-173">ID de la demande contenant l'instruction.</span><span class="sxs-lookup"><span data-stu-id="a3463-173">The ID of the request containing the statement.</span></span>|<span data-ttu-id="a3463-174">49</span><span class="sxs-lookup"><span data-stu-id="a3463-174">49</span></span>|<span data-ttu-id="a3463-175">Oui</span><span class="sxs-lookup"><span data-stu-id="a3463-175">Yes</span></span>|  
|<span data-ttu-id="a3463-176">ServerName</span><span class="sxs-lookup"><span data-stu-id="a3463-176">ServerName</span></span>|`nvarchar`|<span data-ttu-id="a3463-177">Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.</span><span class="sxs-lookup"><span data-stu-id="a3463-177">Name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="a3463-178">26</span><span class="sxs-lookup"><span data-stu-id="a3463-178">26</span></span>|<span data-ttu-id="a3463-179">Non</span><span class="sxs-lookup"><span data-stu-id="a3463-179">No</span></span>|  
|<span data-ttu-id="a3463-180">SessionLoginName</span><span class="sxs-lookup"><span data-stu-id="a3463-180">SessionLoginName</span></span>|`nvarchar`|<span data-ttu-id="a3463-181">Nom de connexion de l'utilisateur à l'origine de la session.</span><span class="sxs-lookup"><span data-stu-id="a3463-181">The login name of the user who originated the session.</span></span> <span data-ttu-id="a3463-182">Par exemple, si vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en utilisant le nom Connexion1 et que vous exécutez une instruction en tant que Connexion2, SessionLoginName affiche Connexion1 et LoginName, Connexion2.</span><span class="sxs-lookup"><span data-stu-id="a3463-182">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, SessionLoginName shows Login1 and LoginName shows Login2.</span></span> <span data-ttu-id="a3463-183">Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Windows.</span><span class="sxs-lookup"><span data-stu-id="a3463-183">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows logins.</span></span>|<span data-ttu-id="a3463-184">64</span><span class="sxs-lookup"><span data-stu-id="a3463-184">64</span></span>|<span data-ttu-id="a3463-185">Oui</span><span class="sxs-lookup"><span data-stu-id="a3463-185">Yes</span></span>|  
|<span data-ttu-id="a3463-186">SPID</span><span class="sxs-lookup"><span data-stu-id="a3463-186">SPID</span></span>|`int`|<span data-ttu-id="a3463-187">ID de la session au cours de laquelle l'événement s'est produit.</span><span class="sxs-lookup"><span data-stu-id="a3463-187">ID of the session on which the event occurred.</span></span>|<span data-ttu-id="a3463-188">12</span><span class="sxs-lookup"><span data-stu-id="a3463-188">12</span></span>|<span data-ttu-id="a3463-189">Oui</span><span class="sxs-lookup"><span data-stu-id="a3463-189">Yes</span></span>|  
|<span data-ttu-id="a3463-190">StartTime</span><span class="sxs-lookup"><span data-stu-id="a3463-190">StartTime</span></span>|`datetime`|<span data-ttu-id="a3463-191">Heure à laquelle a débuté l'événement, si disponible.</span><span class="sxs-lookup"><span data-stu-id="a3463-191">Time at which the event started, when available.</span></span>|<span data-ttu-id="a3463-192">14</span><span class="sxs-lookup"><span data-stu-id="a3463-192">14</span></span>|<span data-ttu-id="a3463-193">Oui</span><span class="sxs-lookup"><span data-stu-id="a3463-193">Yes</span></span>|  
|<span data-ttu-id="a3463-194">TextData</span><span class="sxs-lookup"><span data-stu-id="a3463-194">TextData</span></span>|`ntext`|<span data-ttu-id="a3463-195">Valeur texte qui dépend de la classe d'événements capturée dans la trace.</span><span class="sxs-lookup"><span data-stu-id="a3463-195">Text value dependent on the event class captured in the trace.</span></span>|<span data-ttu-id="a3463-196">1</span><span class="sxs-lookup"><span data-stu-id="a3463-196">1</span></span>|<span data-ttu-id="a3463-197">Oui</span><span class="sxs-lookup"><span data-stu-id="a3463-197">Yes</span></span>|  
|<span data-ttu-id="a3463-198">TransactionID</span><span class="sxs-lookup"><span data-stu-id="a3463-198">TransactionID</span></span>|`bigint`|<span data-ttu-id="a3463-199">ID affecté par le système à la transaction.</span><span class="sxs-lookup"><span data-stu-id="a3463-199">System-assigned ID of the transaction.</span></span>|<span data-ttu-id="a3463-200">4</span><span class="sxs-lookup"><span data-stu-id="a3463-200">4</span></span>|<span data-ttu-id="a3463-201">Oui</span><span class="sxs-lookup"><span data-stu-id="a3463-201">Yes</span></span>|  
|<span data-ttu-id="a3463-202">XactSequence</span><span class="sxs-lookup"><span data-stu-id="a3463-202">XactSequence</span></span>|`bigint`|<span data-ttu-id="a3463-203">Jeton qui décrit la transaction en cours.</span><span class="sxs-lookup"><span data-stu-id="a3463-203">Token that describes the current transaction.</span></span>|<span data-ttu-id="a3463-204">50</span><span class="sxs-lookup"><span data-stu-id="a3463-204">50</span></span>|<span data-ttu-id="a3463-205">Oui</span><span class="sxs-lookup"><span data-stu-id="a3463-205">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a3463-206">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a3463-206">See Also</span></span>  
 <span data-ttu-id="a3463-207">[Événements étendus](../extended-events/extended-events.md) </span><span class="sxs-lookup"><span data-stu-id="a3463-207">[Extended Events](../extended-events/extended-events.md) </span></span>  
 <span data-ttu-id="a3463-208">[ENREGISTRER la TRANSACTION &#40;&#41;Transact-SQL](/sql/t-sql/language-elements/save-transaction-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a3463-208">[SAVE TRANSACTION &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/save-transaction-transact-sql) </span></span>  
 [<span data-ttu-id="a3463-209">sp_trace_setevent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a3463-209">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  