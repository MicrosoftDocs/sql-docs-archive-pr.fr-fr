---
title: 'TM: Save Tran Completed, classe d’événements | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- 'TM: Save Tran Completed event class'
ms.assetid: e6b37780-5ad8-4d50-89a3-d8a22496faac
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4ed85038d9cfc6281d1f9dbd84d4c0b0afeb43b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87695647"
---
# <a name="tm-save-tran-completed-event-class"></a><span data-ttu-id="24e7a-102">TM: Save Tran Completed, classe d'événements</span><span class="sxs-lookup"><span data-stu-id="24e7a-102">TM: Save Tran Completed Event Class</span></span>
  <span data-ttu-id="24e7a-103">La classe d'événements TM: Save Tran Completed indique qu'une demande SAVE TRANSACTION est terminée.</span><span class="sxs-lookup"><span data-stu-id="24e7a-103">The TM: Save Tran Completed event class indicates that a SAVE TRANSACTION request has completed.</span></span> <span data-ttu-id="24e7a-104">La demande a été envoyée à partir du client via l'interface de gestion des transactions.</span><span class="sxs-lookup"><span data-stu-id="24e7a-104">The request was sent from the client through the transaction management interface.</span></span>  
  
## <a name="tm-save-tran-completed-event-class-data-columns"></a><span data-ttu-id="24e7a-105">Colonnes de données de la classe d'événements TM: Save Tran Completed</span><span class="sxs-lookup"><span data-stu-id="24e7a-105">TM: Save Tran Completed Event Class Data Columns</span></span>  
  
|<span data-ttu-id="24e7a-106">Nom de la colonne de données</span><span class="sxs-lookup"><span data-stu-id="24e7a-106">Data column name</span></span>|<span data-ttu-id="24e7a-107">Type de données</span><span class="sxs-lookup"><span data-stu-id="24e7a-107">Data type</span></span>|<span data-ttu-id="24e7a-108">Description</span><span class="sxs-lookup"><span data-stu-id="24e7a-108">Description</span></span>|<span data-ttu-id="24e7a-109">ID de la colonne</span><span class="sxs-lookup"><span data-stu-id="24e7a-109">Column ID</span></span>|<span data-ttu-id="24e7a-110">Filtrable</span><span class="sxs-lookup"><span data-stu-id="24e7a-110">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="24e7a-111">ApplicationName</span><span class="sxs-lookup"><span data-stu-id="24e7a-111">ApplicationName</span></span>|`nvarchar`|<span data-ttu-id="24e7a-112">Nom de l'application cliente qui a créé la connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="24e7a-112">Name of the client application that created the connection to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="24e7a-113">Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.</span><span class="sxs-lookup"><span data-stu-id="24e7a-113">This column is populated with the values passed by the application rather than the displayed name of the program.</span></span>|<span data-ttu-id="24e7a-114">10</span><span class="sxs-lookup"><span data-stu-id="24e7a-114">10</span></span>|<span data-ttu-id="24e7a-115">Oui</span><span class="sxs-lookup"><span data-stu-id="24e7a-115">Yes</span></span>|  
|<span data-ttu-id="24e7a-116">ClientProcessID</span><span class="sxs-lookup"><span data-stu-id="24e7a-116">ClientProcessID</span></span>|`int`|<span data-ttu-id="24e7a-117">ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente.</span><span class="sxs-lookup"><span data-stu-id="24e7a-117">ID assigned by the host computer to the process where the client application is running.</span></span> <span data-ttu-id="24e7a-118">Cette colonne de données est remplie si l'ID du processus du client est fourni par le client.</span><span class="sxs-lookup"><span data-stu-id="24e7a-118">This data column is populated if the client process ID is provided by the client.</span></span>|<span data-ttu-id="24e7a-119">9</span><span class="sxs-lookup"><span data-stu-id="24e7a-119">9</span></span>|<span data-ttu-id="24e7a-120">Oui</span><span class="sxs-lookup"><span data-stu-id="24e7a-120">Yes</span></span>|  
|<span data-ttu-id="24e7a-121">DatabaseID</span><span class="sxs-lookup"><span data-stu-id="24e7a-121">DatabaseID</span></span>|`int`|<span data-ttu-id="24e7a-122">ID de la base de données spécifiée par l'instruction USE *database* ou celui de la base de données par défaut si aucune instruction USE *database* n'a été spécifiée pour une instance donnée.</span><span class="sxs-lookup"><span data-stu-id="24e7a-122">ID of the database specified by the USE *database* statement or the default database if no USE *database* statement has been issued for a given instance.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="24e7a-123">affiche le nom de la base de données si la colonne de données ServerName est capturée dans la trace et que le serveur est disponible.</span><span class="sxs-lookup"><span data-stu-id="24e7a-123">displays the name of the database if the ServerName data column is captured in the trace and the server is available.</span></span> <span data-ttu-id="24e7a-124">Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.</span><span class="sxs-lookup"><span data-stu-id="24e7a-124">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="24e7a-125">3</span><span class="sxs-lookup"><span data-stu-id="24e7a-125">3</span></span>|<span data-ttu-id="24e7a-126">Oui</span><span class="sxs-lookup"><span data-stu-id="24e7a-126">Yes</span></span>|  
|<span data-ttu-id="24e7a-127">nom_base_de_données</span><span class="sxs-lookup"><span data-stu-id="24e7a-127">DatabaseName</span></span>|`nvarchar`|<span data-ttu-id="24e7a-128">Nom de la base de données dans laquelle l'instruction de l'utilisateur est exécutée.</span><span class="sxs-lookup"><span data-stu-id="24e7a-128">Name of the database in which the user statement is running.</span></span>|<span data-ttu-id="24e7a-129">35</span><span class="sxs-lookup"><span data-stu-id="24e7a-129">35</span></span>|<span data-ttu-id="24e7a-130">Oui</span><span class="sxs-lookup"><span data-stu-id="24e7a-130">Yes</span></span>|  
|<span data-ttu-id="24e7a-131">Error</span><span class="sxs-lookup"><span data-stu-id="24e7a-131">Error</span></span>|`int`|<span data-ttu-id="24e7a-132">Numéro d'erreur d'un événement donné.</span><span class="sxs-lookup"><span data-stu-id="24e7a-132">Error number of a given event.</span></span> <span data-ttu-id="24e7a-133">Il s'agit souvent du numéro d'erreur stocké dans l'affichage catalogue sys.messages.</span><span class="sxs-lookup"><span data-stu-id="24e7a-133">Often this is the error number stored in the sys.messages catalog view.</span></span>|<span data-ttu-id="24e7a-134">31</span><span class="sxs-lookup"><span data-stu-id="24e7a-134">31</span></span>|<span data-ttu-id="24e7a-135">Oui</span><span class="sxs-lookup"><span data-stu-id="24e7a-135">Yes</span></span>|  
|<span data-ttu-id="24e7a-136">EventClass</span><span class="sxs-lookup"><span data-stu-id="24e7a-136">EventClass</span></span>|`int`|<span data-ttu-id="24e7a-137">Type d’événement = 192.</span><span class="sxs-lookup"><span data-stu-id="24e7a-137">Type of event = 192.</span></span>|<span data-ttu-id="24e7a-138">27</span><span class="sxs-lookup"><span data-stu-id="24e7a-138">27</span></span>|<span data-ttu-id="24e7a-139">Non</span><span class="sxs-lookup"><span data-stu-id="24e7a-139">No</span></span>|  
|<span data-ttu-id="24e7a-140">EventSequence</span><span class="sxs-lookup"><span data-stu-id="24e7a-140">EventSequence</span></span>|`int`|<span data-ttu-id="24e7a-141">Séquence d'un événement donné au sein de la demande.</span><span class="sxs-lookup"><span data-stu-id="24e7a-141">Sequence of a given event within the request.</span></span>|<span data-ttu-id="24e7a-142">51</span><span class="sxs-lookup"><span data-stu-id="24e7a-142">51</span></span>|<span data-ttu-id="24e7a-143">Non</span><span class="sxs-lookup"><span data-stu-id="24e7a-143">No</span></span>|  
|<span data-ttu-id="24e7a-144">GroupID</span><span class="sxs-lookup"><span data-stu-id="24e7a-144">GroupID</span></span>|`int`|<span data-ttu-id="24e7a-145">ID du groupe de charges de travail où l'événement Trace SQL se déclenche.</span><span class="sxs-lookup"><span data-stu-id="24e7a-145">ID of the workload group where the SQL Trace event fires.</span></span>|<span data-ttu-id="24e7a-146">66</span><span class="sxs-lookup"><span data-stu-id="24e7a-146">66</span></span>|<span data-ttu-id="24e7a-147">Oui</span><span class="sxs-lookup"><span data-stu-id="24e7a-147">Yes</span></span>|  
|<span data-ttu-id="24e7a-148">HostName</span><span class="sxs-lookup"><span data-stu-id="24e7a-148">HostName</span></span>|`nvarchar`|<span data-ttu-id="24e7a-149">Nom de l'ordinateur sur lequel le client est exécuté.</span><span class="sxs-lookup"><span data-stu-id="24e7a-149">Name of the computer on which the client is running.</span></span> <span data-ttu-id="24e7a-150">Cette colonne de données est remplie si le nom de l'hôte est fourni par le client.</span><span class="sxs-lookup"><span data-stu-id="24e7a-150">This data column is populated if the host name is provided by the client.</span></span> <span data-ttu-id="24e7a-151">Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.</span><span class="sxs-lookup"><span data-stu-id="24e7a-151">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="24e7a-152">8</span><span class="sxs-lookup"><span data-stu-id="24e7a-152">8</span></span>|<span data-ttu-id="24e7a-153">Oui</span><span class="sxs-lookup"><span data-stu-id="24e7a-153">Yes</span></span>|  
|<span data-ttu-id="24e7a-154">IsSystem</span><span class="sxs-lookup"><span data-stu-id="24e7a-154">IsSystem</span></span>|`int`|<span data-ttu-id="24e7a-155">Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur.</span><span class="sxs-lookup"><span data-stu-id="24e7a-155">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="24e7a-156">1 = système, 0 = utilisateur.</span><span class="sxs-lookup"><span data-stu-id="24e7a-156">1 = system, 0 = user.</span></span>|<span data-ttu-id="24e7a-157">60</span><span class="sxs-lookup"><span data-stu-id="24e7a-157">60</span></span>|<span data-ttu-id="24e7a-158">Oui</span><span class="sxs-lookup"><span data-stu-id="24e7a-158">Yes</span></span>|  
|<span data-ttu-id="24e7a-159">LoginName</span><span class="sxs-lookup"><span data-stu-id="24e7a-159">LoginName</span></span>|`nvarchar`|<span data-ttu-id="24e7a-160">Nom de la connexion de l'utilisateur (soit la connexion de sécurité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , soit les informations d'identification de connexion [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows au format DOMAINE\nom_utilisateur).</span><span class="sxs-lookup"><span data-stu-id="24e7a-160">Name of the login of the user (either [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security login or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows login credentials in the form of DOMAIN\username).</span></span>|<span data-ttu-id="24e7a-161">11</span><span class="sxs-lookup"><span data-stu-id="24e7a-161">11</span></span>|<span data-ttu-id="24e7a-162">Oui</span><span class="sxs-lookup"><span data-stu-id="24e7a-162">Yes</span></span>|  
|<span data-ttu-id="24e7a-163">LoginSid</span><span class="sxs-lookup"><span data-stu-id="24e7a-163">LoginSid</span></span>|`image`|<span data-ttu-id="24e7a-164">Identificateur de sécurité (SID) de l'utilisateur connecté.</span><span class="sxs-lookup"><span data-stu-id="24e7a-164">Security identifier (SID) of the logged-in user.</span></span> <span data-ttu-id="24e7a-165">Vous pouvez trouver ces informations dans l'affichage catalogue sys.server_principals.</span><span class="sxs-lookup"><span data-stu-id="24e7a-165">You can find this information in the sys.server_principals catalog view.</span></span> <span data-ttu-id="24e7a-166">Chaque connexion possède un SID unique au niveau du serveur.</span><span class="sxs-lookup"><span data-stu-id="24e7a-166">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="24e7a-167">41</span><span class="sxs-lookup"><span data-stu-id="24e7a-167">41</span></span>|<span data-ttu-id="24e7a-168">Oui</span><span class="sxs-lookup"><span data-stu-id="24e7a-168">Yes</span></span>|  
|<span data-ttu-id="24e7a-169">NTDomainName</span><span class="sxs-lookup"><span data-stu-id="24e7a-169">NTDomainName</span></span>|`nvarchar`|<span data-ttu-id="24e7a-170">Domaine Windows auquel appartient l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="24e7a-170">Windows domain to which the user belongs.</span></span>|<span data-ttu-id="24e7a-171">7</span><span class="sxs-lookup"><span data-stu-id="24e7a-171">7</span></span>|<span data-ttu-id="24e7a-172">Oui</span><span class="sxs-lookup"><span data-stu-id="24e7a-172">Yes</span></span>|  
|<span data-ttu-id="24e7a-173">NTUserName</span><span class="sxs-lookup"><span data-stu-id="24e7a-173">NTUserName</span></span>|`nvarchar`|<span data-ttu-id="24e7a-174">Nom d'utilisateur Windows.</span><span class="sxs-lookup"><span data-stu-id="24e7a-174">Windows user name.</span></span>|<span data-ttu-id="24e7a-175">6</span><span class="sxs-lookup"><span data-stu-id="24e7a-175">6</span></span>|<span data-ttu-id="24e7a-176">Oui</span><span class="sxs-lookup"><span data-stu-id="24e7a-176">Yes</span></span>|  
|<span data-ttu-id="24e7a-177">RequestID</span><span class="sxs-lookup"><span data-stu-id="24e7a-177">RequestID</span></span>|`int`|<span data-ttu-id="24e7a-178">ID de la demande contenant l'instruction.</span><span class="sxs-lookup"><span data-stu-id="24e7a-178">ID of the request containing the statement.</span></span>|<span data-ttu-id="24e7a-179">49</span><span class="sxs-lookup"><span data-stu-id="24e7a-179">49</span></span>|<span data-ttu-id="24e7a-180">Oui</span><span class="sxs-lookup"><span data-stu-id="24e7a-180">Yes</span></span>|  
|<span data-ttu-id="24e7a-181">ServerName</span><span class="sxs-lookup"><span data-stu-id="24e7a-181">ServerName</span></span>|`nvarchar`|<span data-ttu-id="24e7a-182">Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.</span><span class="sxs-lookup"><span data-stu-id="24e7a-182">Name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="24e7a-183">26</span><span class="sxs-lookup"><span data-stu-id="24e7a-183">26</span></span>|<span data-ttu-id="24e7a-184">Non</span><span class="sxs-lookup"><span data-stu-id="24e7a-184">No</span></span>|  
|<span data-ttu-id="24e7a-185">SessionLoginName</span><span class="sxs-lookup"><span data-stu-id="24e7a-185">SessionLoginName</span></span>|`nvarchar`|<span data-ttu-id="24e7a-186">Nom de connexion de l'utilisateur à l'origine de la session.</span><span class="sxs-lookup"><span data-stu-id="24e7a-186">Login name of the user who originated the session.</span></span> <span data-ttu-id="24e7a-187">Par exemple, si vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en utilisant le nom Connexion1 et que vous exécutez une instruction en tant que Connexion2, SessionLoginName affiche Connexion1 et LoginName, Connexion2.</span><span class="sxs-lookup"><span data-stu-id="24e7a-187">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, SessionLoginName shows Login1 and LoginName shows Login2.</span></span> <span data-ttu-id="24e7a-188">Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Windows.</span><span class="sxs-lookup"><span data-stu-id="24e7a-188">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows logins.</span></span>|<span data-ttu-id="24e7a-189">64</span><span class="sxs-lookup"><span data-stu-id="24e7a-189">64</span></span>|<span data-ttu-id="24e7a-190">Oui</span><span class="sxs-lookup"><span data-stu-id="24e7a-190">Yes</span></span>|  
|<span data-ttu-id="24e7a-191">SPID</span><span class="sxs-lookup"><span data-stu-id="24e7a-191">SPID</span></span>|`int`|<span data-ttu-id="24e7a-192">ID de la session au cours de laquelle l'événement s'est produit.</span><span class="sxs-lookup"><span data-stu-id="24e7a-192">ID of the session on which the event occurred.</span></span>|<span data-ttu-id="24e7a-193">12</span><span class="sxs-lookup"><span data-stu-id="24e7a-193">12</span></span>|<span data-ttu-id="24e7a-194">Oui</span><span class="sxs-lookup"><span data-stu-id="24e7a-194">Yes</span></span>|  
|<span data-ttu-id="24e7a-195">StartTime</span><span class="sxs-lookup"><span data-stu-id="24e7a-195">StartTime</span></span>|`datetime`|<span data-ttu-id="24e7a-196">Heure à laquelle a débuté l'événement, si elle est connue.</span><span class="sxs-lookup"><span data-stu-id="24e7a-196">Time at which the event started, if available.</span></span>|<span data-ttu-id="24e7a-197">14</span><span class="sxs-lookup"><span data-stu-id="24e7a-197">14</span></span>|<span data-ttu-id="24e7a-198">Oui</span><span class="sxs-lookup"><span data-stu-id="24e7a-198">Yes</span></span>|  
|<span data-ttu-id="24e7a-199">Succès</span><span class="sxs-lookup"><span data-stu-id="24e7a-199">Success</span></span>|`int`|<span data-ttu-id="24e7a-200">1 = réussite.</span><span class="sxs-lookup"><span data-stu-id="24e7a-200">1 = success.</span></span> <span data-ttu-id="24e7a-201">0 = échec (1 signifie la réussite de la vérification d'autorisations et 0 l'échec de cette vérification, par exemple).</span><span class="sxs-lookup"><span data-stu-id="24e7a-201">0 = failure (for example, a 1 means success of a permissions check and a 0 means a failure of that check).</span></span>|<span data-ttu-id="24e7a-202">23</span><span class="sxs-lookup"><span data-stu-id="24e7a-202">23</span></span>|<span data-ttu-id="24e7a-203">Oui</span><span class="sxs-lookup"><span data-stu-id="24e7a-203">Yes</span></span>|  
|<span data-ttu-id="24e7a-204">TextData</span><span class="sxs-lookup"><span data-stu-id="24e7a-204">TextData</span></span>|`ntext`|<span data-ttu-id="24e7a-205">Valeur texte qui dépend de la classe d'événements capturée dans la trace.</span><span class="sxs-lookup"><span data-stu-id="24e7a-205">Text value dependent on the event class captured in the trace.</span></span>|<span data-ttu-id="24e7a-206">1</span><span class="sxs-lookup"><span data-stu-id="24e7a-206">1</span></span>|<span data-ttu-id="24e7a-207">Oui</span><span class="sxs-lookup"><span data-stu-id="24e7a-207">Yes</span></span>|  
|<span data-ttu-id="24e7a-208">TransactionID</span><span class="sxs-lookup"><span data-stu-id="24e7a-208">TransactionID</span></span>|`bigint`|<span data-ttu-id="24e7a-209">ID affecté par le système à la transaction.</span><span class="sxs-lookup"><span data-stu-id="24e7a-209">System-assigned ID of the transaction.</span></span>|<span data-ttu-id="24e7a-210">4</span><span class="sxs-lookup"><span data-stu-id="24e7a-210">4</span></span>|<span data-ttu-id="24e7a-211">Oui</span><span class="sxs-lookup"><span data-stu-id="24e7a-211">Yes</span></span>|  
|<span data-ttu-id="24e7a-212">XactSequence</span><span class="sxs-lookup"><span data-stu-id="24e7a-212">XactSequence</span></span>|`bigint`|<span data-ttu-id="24e7a-213">Jeton qui décrit la transaction en cours.</span><span class="sxs-lookup"><span data-stu-id="24e7a-213">Token that describes the current transaction.</span></span>|<span data-ttu-id="24e7a-214">50</span><span class="sxs-lookup"><span data-stu-id="24e7a-214">50</span></span>|<span data-ttu-id="24e7a-215">Oui</span><span class="sxs-lookup"><span data-stu-id="24e7a-215">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="24e7a-216">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="24e7a-216">See Also</span></span>  
 <span data-ttu-id="24e7a-217">[Événements étendus](../extended-events/extended-events.md) </span><span class="sxs-lookup"><span data-stu-id="24e7a-217">[Extended Events](../extended-events/extended-events.md) </span></span>  
 <span data-ttu-id="24e7a-218">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="24e7a-218">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 [<span data-ttu-id="24e7a-219">SAVE TRANSACTION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="24e7a-219">SAVE TRANSACTION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/save-transaction-transact-sql)  
  
  