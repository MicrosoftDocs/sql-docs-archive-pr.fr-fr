---
title: Options de démarrage du service moteur de base de données | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- single-user mode [SQL Server], startup option
- overriding default startup options
- minimal configuration mode [SQL Server], startup option
- default startup options
- temporarily override default startup options [SQL Server]
- startup options [SQL Server]
- starting SQL Server, options
ms.assetid: d373298b-f6cf-458a-849d-7083ecb54ef5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 844c0813453d371ed204dff6f8976f08bad63fe5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611276"
---
# <a name="database-engine-service-startup-options"></a><span data-ttu-id="efd9b-102">Options de démarrage du service moteur de base de données</span><span class="sxs-lookup"><span data-stu-id="efd9b-102">Database Engine Service Startup Options</span></span>
  <span data-ttu-id="efd9b-103">Les options de démarrage désignent certains emplacements de fichiers nécessaires lors du démarrage et spécifient certaines conditions applicables à l'échelle du serveur.</span><span class="sxs-lookup"><span data-stu-id="efd9b-103">Startup options designate certain file locations needed during startup, and specify some server wide conditions.</span></span> <span data-ttu-id="efd9b-104">La plupart des utilisateurs n'ont pas besoin de spécifier d'options de démarrage, à moins de dépanner le [!INCLUDE[ssDE](../../includes/ssde-md.md)] ou d'avoir un problème inhabituel et que le support technique de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne leur demande d'utiliser une option de démarrage.</span><span class="sxs-lookup"><span data-stu-id="efd9b-104">Most users do not need to specify startup options unless you are troubleshooting the [!INCLUDE[ssDE](../../includes/ssde-md.md)] or you have an unusual problem and are directed to use a startup option by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Customer Support.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="efd9b-105">Toute utilisation incorrecte des options de démarrage peut affecter les performances du serveur et empêcher le démarrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="efd9b-105">Improper use of startup options can affect server performance and can prevent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from starting.</span></span>  
  
## <a name="about-startup-options"></a><span data-ttu-id="efd9b-106">À propos des options de démarrage</span><span class="sxs-lookup"><span data-stu-id="efd9b-106">About Startup Options</span></span>  
 <span data-ttu-id="efd9b-107">Lorsque vous installez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le programme d'installation inscrit un ensemble d'options de démarrage par défaut dans le Registre de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.</span><span class="sxs-lookup"><span data-stu-id="efd9b-107">When you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Setup writes a set of default startup options in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows registry.</span></span> <span data-ttu-id="efd9b-108">Vous pouvez utiliser ces options de démarrage pour spécifier un autre fichier de base de données master, un autre fichier journal de base de données master ou un autre fichier journal des erreurs.</span><span class="sxs-lookup"><span data-stu-id="efd9b-108">You can use these startup options to specify an alternate master database file, master database log file, or error log file.</span></span> <span data-ttu-id="efd9b-109">Si le [!INCLUDE[ssDE](../../includes/ssde-md.md)] ne peut pas localiser les fichiers nécessaires, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne démarre pas.</span><span class="sxs-lookup"><span data-stu-id="efd9b-109">If the [!INCLUDE[ssDE](../../includes/ssde-md.md)] cannot locate the necessary files, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will not start.</span></span>  
  
 <span data-ttu-id="efd9b-110">Il est possible de définir les options de démarrage en utilisant le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="efd9b-110">Startup options can be set by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="efd9b-111">Pour plus d’informations, consultez [Configurer les options de démarrage du serveur &#40;SQL Server Configuration Manager&#41;](scm-services-configure-server-startup-options.md).</span><span class="sxs-lookup"><span data-stu-id="efd9b-111">For information, see [Configure Server Startup Options &#40;SQL Server Configuration Manager&#41;](scm-services-configure-server-startup-options.md).</span></span>  
  
## <a name="list-of-startup-options"></a><span data-ttu-id="efd9b-112">Liste des options de démarrage</span><span class="sxs-lookup"><span data-stu-id="efd9b-112">List of Startup Options</span></span>  
  
|<span data-ttu-id="efd9b-113">Options de démarrage par défaut</span><span class="sxs-lookup"><span data-stu-id="efd9b-113">Default startup options</span></span>|<span data-ttu-id="efd9b-114">Description</span><span class="sxs-lookup"><span data-stu-id="efd9b-114">Description</span></span>|  
|-----------------------------|-----------------|  
|<span data-ttu-id="efd9b-115">**-d**  *master_file_path*</span><span class="sxs-lookup"><span data-stu-id="efd9b-115">**-d**  *master_file_path*</span></span>|<span data-ttu-id="efd9b-116">Représente le chemin d’accès complet au fichier de base de données MASTER (il s’agit généralement de C:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Data\master.mdf).</span><span class="sxs-lookup"><span data-stu-id="efd9b-116">Is the fully qualified path for the master database file (typically, C:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Data\master.mdf).</span></span> <span data-ttu-id="efd9b-117">Si vous ne spécifiez pas cette option, les paramètres du Registre existant sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="efd9b-117">If you do not provide this option, the existing registry parameters are used.</span></span>|  
|<span data-ttu-id="efd9b-118">**-e**  *error_log_path*</span><span class="sxs-lookup"><span data-stu-id="efd9b-118">**-e**  *error_log_path*</span></span>|<span data-ttu-id="efd9b-119">Représente le chemin d’accès complet au fichier journal des erreurs (il s’agit généralement de C:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\LOG\ERRORLOG).</span><span class="sxs-lookup"><span data-stu-id="efd9b-119">Is the fully qualified path for the error log file (typically, C:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\LOG\ERRORLOG).</span></span> <span data-ttu-id="efd9b-120">Si vous ne spécifiez pas cette option, les paramètres du Registre existant sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="efd9b-120">If you do not provide this option, the existing registry parameters are used.</span></span>|  
|<span data-ttu-id="efd9b-121">**-l**  *master_log_path*</span><span class="sxs-lookup"><span data-stu-id="efd9b-121">**-l**  *master_log_path*</span></span>|<span data-ttu-id="efd9b-122">Représente le chemin d’accès complet au fichier journal de la base de données MASTER (il s’agit généralement de C:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Data\mastlog.ldf).</span><span class="sxs-lookup"><span data-stu-id="efd9b-122">Is the fully qualified path for the master database log file (typically C:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Data\mastlog.ldf).</span></span> <span data-ttu-id="efd9b-123">Si vous ne spécifiez pas cette option, les paramètres de Registre existants sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="efd9b-123">If you do not specify this option, the existing registry parameters are used.</span></span>|  
  
|<span data-ttu-id="efd9b-124">Autres options de démarrage</span><span class="sxs-lookup"><span data-stu-id="efd9b-124">Other startup options</span></span>|<span data-ttu-id="efd9b-125">Description</span><span class="sxs-lookup"><span data-stu-id="efd9b-125">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="efd9b-126">**-c**</span><span class="sxs-lookup"><span data-stu-id="efd9b-126">**-c**</span></span>|<span data-ttu-id="efd9b-127">Raccourcit la durée nécessaire au démarrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir de l'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="efd9b-127">Shortens startup time when starting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the command prompt.</span></span> <span data-ttu-id="efd9b-128">En général, le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] démarre en tant que service en appelant le gestionnaire de contrôle de services.</span><span class="sxs-lookup"><span data-stu-id="efd9b-128">Typically, the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] starts as a service by calling the Service Control Manager.</span></span> <span data-ttu-id="efd9b-129">Comme [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ne démarre pas en tant que service pendant le démarrage à partir de l’invite de commandes, vous devez utiliser **-c** pour ignorer cette étape.</span><span class="sxs-lookup"><span data-stu-id="efd9b-129">Because the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] does not start as a service when starting from the command prompt, use **-c** to skip this step.</span></span>|  
|<span data-ttu-id="efd9b-130">**-f**</span><span class="sxs-lookup"><span data-stu-id="efd9b-130">**-f**</span></span>|<span data-ttu-id="efd9b-131">Démarre une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec une configuration minimale.</span><span class="sxs-lookup"><span data-stu-id="efd9b-131">Starts an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with minimal configuration.</span></span> <span data-ttu-id="efd9b-132">Cette option est utile lorsqu'une valeur de configuration définie (espace mémoire insuffisant, par exemple) a empêché le serveur de démarrer.</span><span class="sxs-lookup"><span data-stu-id="efd9b-132">This is useful if the setting of a configuration value (for example, over-committing memory) has prevented the server from starting.</span></span> <span data-ttu-id="efd9b-133">Le démarrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode de configuration minimal place [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode mono-utilisateur.</span><span class="sxs-lookup"><span data-stu-id="efd9b-133">Starting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in minimal configuration mode places [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode.</span></span> <span data-ttu-id="efd9b-134">Pour plus d’informations, consultez la description de l’option **-m** ci-après.</span><span class="sxs-lookup"><span data-stu-id="efd9b-134">For more information, see the description for **-m** that follows.</span></span>|  
|<span data-ttu-id="efd9b-135">**g -**  *mémoire_à_réserver*</span><span class="sxs-lookup"><span data-stu-id="efd9b-135">**-g**  *memory_to_reserve*</span></span>|<span data-ttu-id="efd9b-136">Spécifie un nombre entier de mégaoctets (Mo) de mémoire que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conservera disponible pour les allocations de mémoire dans le processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , mais en dehors du pool de mémoire de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="efd9b-136">Specifies an integer number of megabytes (MB) of memory that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will leave available for memory allocations within the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process, but outside the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory pool.</span></span> <span data-ttu-id="efd9b-137">La mémoire en dehors du pool de mémoire est la zone utilisée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour le chargement d'éléments, tels que les fichiers .dll des procédures stockées étendues, les fournisseurs OLE DB référencés par les requêtes distribuées et les objets automation référencés dans les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="efd9b-137">The memory outside of the memory pool is the area used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for loading items, such as extended procedure .dll files, the OLE DB providers referenced by distributed queries, and automation objects referenced in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="efd9b-138">La valeur par défaut est 256 Mo.</span><span class="sxs-lookup"><span data-stu-id="efd9b-138">The default is 256 MB.</span></span><br /><br /> <span data-ttu-id="efd9b-139">Cette option peut faciliter l'ajustement de l'allocation de mémoire, mais uniquement lorsque la mémoire physique dépasse la limite configurée définie par le système d'exploitation sur la mémoire virtuelle disponible pour les applications.</span><span class="sxs-lookup"><span data-stu-id="efd9b-139">Use of this option might help tune memory allocation, but only when physical memory exceeds the configured limit set by the operating system on virtual memory available to applications.</span></span> <span data-ttu-id="efd9b-140">L'utilisation de cette option peut s'avérer appropriée avec des configurations de mémoire importantes, dans lesquelles les besoins en utilisation de la mémoire de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne sont pas standard et l'espace d'adressage virtuel du processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est utilisé dans son intégralité.</span><span class="sxs-lookup"><span data-stu-id="efd9b-140">Use of this option might be appropriate in large memory configurations in which the memory usage requirements of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are atypical and the virtual address space of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process is totally in use.</span></span> <span data-ttu-id="efd9b-141">L'utilisation incorrecte de cette option peut mener à des situations dans lesquelles une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne démarre pas ou rencontre des erreurs lors de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="efd9b-141">Incorrect use of this option can lead to conditions under which an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] may not start or may encounter run-time errors.</span></span><br /><br /> <span data-ttu-id="efd9b-142">Utilisez la valeur par défaut du paramètre **-g** , sauf si l’un des avertissements suivants figure dans le journal des erreurs de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="efd9b-142">Use the default for the **-g** parameter unless you see any of the following warnings in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log:</span></span><br /><br /> <span data-ttu-id="efd9b-143">-« Octets virtuels alloués ayant échoué : FAIL_VIRTUAL_RESERVE \<size> »</span><span class="sxs-lookup"><span data-stu-id="efd9b-143">-"Failed Virtual Allocate Bytes: FAIL_VIRTUAL_RESERVE \<size>"</span></span><br /><br /> <span data-ttu-id="efd9b-144">-« Octets virtuels alloués ayant échoué : FAIL_VIRTUAL_COMMIT \<size> »</span><span class="sxs-lookup"><span data-stu-id="efd9b-144">-"Failed Virtual Allocate Bytes: FAIL_VIRTUAL_COMMIT \<size>"</span></span><br /><br /> <span data-ttu-id="efd9b-145">Ces messages peuvent indiquer que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tente de libérer des parties du pool de la mémoire de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] afin de trouver de l'espace pour des éléments tels que les fichiers .dll de procédure stockée étendue ou des objets Automation.</span><span class="sxs-lookup"><span data-stu-id="efd9b-145">These messages might indicate that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is trying to free parts of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory pool in order to find space for items, such as extended stored procedure .dll files or automation objects.</span></span> <span data-ttu-id="efd9b-146">Dans ce cas, envisagez d’augmenter la quantité de mémoire réservée par le commutateur **-g** .</span><span class="sxs-lookup"><span data-stu-id="efd9b-146">In this case, consider increasing the amount of memory reserved by the **-g** switch.</span></span><br /><br /> <span data-ttu-id="efd9b-147">L'utilisation d'une valeur inférieure à celle par défaut augmente la quantité de mémoire disponible dans le pool de mémoires géré par le Gestionnaire de mémoire de SQL Server ou les piles de threads ; cela permet de profiter de l'amélioration des performances pour les charges de travail qui ont recours de manière intensive à la mémoire dans les systèmes qui n'utilisent pas de nombreuses procédures stockées étendues, requêtes distribuées ou objets automation.</span><span class="sxs-lookup"><span data-stu-id="efd9b-147">Using a value lower than the default will increase the amount of memory available to the memory pool managed by the SQL Server Memory Manager and thread stacks; this may, in turn, provide some performance benefit to memory-intensive workloads in systems that do not use many extended stored procedures, distributed queries, or automation objects.</span></span>|  
|<span data-ttu-id="efd9b-148">**-m**</span><span class="sxs-lookup"><span data-stu-id="efd9b-148">**-m**</span></span>|<span data-ttu-id="efd9b-149">Démarre une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode mono-utilisateur.</span><span class="sxs-lookup"><span data-stu-id="efd9b-149">Starts an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode.</span></span> <span data-ttu-id="efd9b-150">Lorsque vous démarrez une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode mono-utilisateur, un seul utilisateur peut se connecter et le processus CHECKPOINT n'est pas démarré.</span><span class="sxs-lookup"><span data-stu-id="efd9b-150">When you start an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode, only a single user can connect, and the CHECKPOINT process is not started.</span></span> <span data-ttu-id="efd9b-151">CHECKPOINT garantit l'écriture régulière des transactions terminées de la mémoire cache du disque vers l'unité de base de données.</span><span class="sxs-lookup"><span data-stu-id="efd9b-151">CHECKPOINT guarantees that completed transactions are regularly written from the disk cache to the database device.</span></span> <span data-ttu-id="efd9b-152">(Cette option est généralement utilisée si vous rencontrez des problèmes avec des bases de données système qui doivent être réparées). Active l’option sp_configure allow updates.</span><span class="sxs-lookup"><span data-stu-id="efd9b-152">(Typically, this option is used if you experience problems with system databases that should be repaired.) Enables the sp_configure allow updates option.</span></span> <span data-ttu-id="efd9b-153">Par défaut, l'option allow updates est désactivée.</span><span class="sxs-lookup"><span data-stu-id="efd9b-153">By default, allow updates is disabled.</span></span> <span data-ttu-id="efd9b-154">Le démarrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode mono-utilisateur permet à tout membre du groupe Administrateurs local de l'ordinateur de se connecter à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en tant que membre du rôle serveur fixe sysadmin.</span><span class="sxs-lookup"><span data-stu-id="efd9b-154">Starting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode enables any member of the computer's local Administrators group to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as a member of the sysadmin fixed server role.</span></span> <span data-ttu-id="efd9b-155">Pour plus d’informations, consultez [Se connecter à SQL Server lorsque les administrateurs système n’y ont plus accès](connect-to-sql-server-when-system-administrators-are-locked-out.md). Pour plus d’informations sur le mode mono-utilisateur, consultez [Démarrer SQL Server en mode mono-utilisateur](start-sql-server-in-single-user-mode.md).</span><span class="sxs-lookup"><span data-stu-id="efd9b-155">For more information, see [Connect to SQL Server When System Administrators Are Locked Out](connect-to-sql-server-when-system-administrators-are-locked-out.md). For more information about single-user mode, see [Start SQL Server in Single-User Mode](start-sql-server-in-single-user-mode.md).</span></span>|  
|<span data-ttu-id="efd9b-156">**-m « nom de l’application cliente »**</span><span class="sxs-lookup"><span data-stu-id="efd9b-156">**-m"Client Application Name"**</span></span>|<span data-ttu-id="efd9b-157">Limite les connexions à une application cliente spécifiée quand vous utilisez l’option **-m** avec **SQLCMD** ou [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span><span class="sxs-lookup"><span data-stu-id="efd9b-157">Limits the connections to a specified client application, when you use the **-m** option with **SQLCMD** or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="efd9b-158">Par exemple, **-m"SQLCMD"** limite les connexions à une connexion unique, laquelle doit s’identifier en tant que programme client **SQLCMD**.</span><span class="sxs-lookup"><span data-stu-id="efd9b-158">For example, **-m"SQLCMD"** limits connections to a single connection and that connection must identify itself as the **SQLCMD** client program.</span></span> <span data-ttu-id="efd9b-159">Utilisez cette option lorsque vous démarrez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode mono-utilisateur et qu'une application cliente inconnue utilise la seule connexion disponible.</span><span class="sxs-lookup"><span data-stu-id="efd9b-159">Use this option when you are starting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode and an unknown client application is taking the only available connection.</span></span> <span data-ttu-id="efd9b-160">Pour vous connecter par le biais de l’éditeur de requête dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], utilisez **-m"Microsoft SQL Server Management Studio - Query"** .</span><span class="sxs-lookup"><span data-stu-id="efd9b-160">To connect through the Query Editor in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], use **-m"Microsoft SQL Server Management Studio - Query"**.</span></span><br /><br /> <span data-ttu-id="efd9b-161">Le nom de l'application cliente respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="efd9b-161">Client Application Name is case sensitive.</span></span><br /><br /> <span data-ttu-id="efd9b-162">Note de sécurité n’utilisez pas cette option comme fonctionnalité de sécurité. \*\* \* \* \* \* \*\*</span><span class="sxs-lookup"><span data-stu-id="efd9b-162">**\*\* Security Note \*\*** Do not use this option as a security feature.</span></span> <span data-ttu-id="efd9b-163">L'application cliente fournit le nom d'application cliente et peut fournir un nom erroné dans la chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="efd9b-163">The client application provides the client application name, and can provide a false name as part of the connection string.</span></span>|  
|<span data-ttu-id="efd9b-164">**-n**</span><span class="sxs-lookup"><span data-stu-id="efd9b-164">**-n**</span></span>|<span data-ttu-id="efd9b-165">N'utilise pas le journal des applications Windows pour enregistrer les événements [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="efd9b-165">Does not use the Windows application log to record [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] events.</span></span> <span data-ttu-id="efd9b-166">Si vous démarrez une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec **-n**, nous vous recommandons d’utiliser également l’option de démarrage **-e** .</span><span class="sxs-lookup"><span data-stu-id="efd9b-166">If you start an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with **-n**, we recommend that you also use the **-e** startup option.</span></span> <span data-ttu-id="efd9b-167">Sinon, les événements [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne seront pas consignés.</span><span class="sxs-lookup"><span data-stu-id="efd9b-167">Otherwise, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] events are not logged.</span></span>|  
|<span data-ttu-id="efd9b-168">**-s**</span><span class="sxs-lookup"><span data-stu-id="efd9b-168">**-s**</span></span>|<span data-ttu-id="efd9b-169">Permet de démarrer une instance nommée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="efd9b-169">Allows you to start a named instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="efd9b-170">Si le paramètre **-s** n’est pas défini, l’instance par défaut va tenter de démarrer.</span><span class="sxs-lookup"><span data-stu-id="efd9b-170">Without the **-s** parameter set, the default instance will try to start.</span></span> <span data-ttu-id="efd9b-171">Vous devez accéder au répertoire BINN de l’instance, dans l’invite de commandes, avant de démarrer **sqlservr.exe**.</span><span class="sxs-lookup"><span data-stu-id="efd9b-171">You must switch to the appropriate BINN directory for the instance at a command prompt before starting **sqlservr.exe**.</span></span> <span data-ttu-id="efd9b-172">Par exemple, si Instance1 doit utiliser \mssql$Instance1 pour ses fichiers binaires, l’utilisateur doit être dans le répertoire \mssql$Instance1\binn pour démarrer **sqlservr.exe -s instance1**.</span><span class="sxs-lookup"><span data-stu-id="efd9b-172">For example, if Instance1 were to use \mssql$Instance1 for its binaries, the user must be in the \mssql$Instance1\binn directory to start **sqlservr.exe -s instance1**.</span></span>|  
|<span data-ttu-id="efd9b-173">**-T**  *trace#*</span><span class="sxs-lookup"><span data-stu-id="efd9b-173">**-T**  *trace#*</span></span>|<span data-ttu-id="efd9b-174">Indique qu’une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être démarrée avec un indicateur de trace spécifique (*trace#* ) en vigueur.</span><span class="sxs-lookup"><span data-stu-id="efd9b-174">Indicates that an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should be started with a specified trace flag (*trace#*) in effect.</span></span> <span data-ttu-id="efd9b-175">Les indicateurs de trace permettent de démarrer le serveur avec un comportement non standard.</span><span class="sxs-lookup"><span data-stu-id="efd9b-175">Trace flags are used to start the server with nonstandard behavior.</span></span> <span data-ttu-id="efd9b-176">Pour plus d’informations, consultez [Indicateurs de trace &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="efd9b-176">For more information, see [Trace Flags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).</span></span><br /><br /> <span data-ttu-id="efd9b-177">\*\* \* \* Important \* quand \* \*\* vous spécifiez un indicateur de trace avec l’option **-t** , utilisez un « T » majuscule pour transmettre le numéro d’indicateur de trace.</span><span class="sxs-lookup"><span data-stu-id="efd9b-177">**\*\* Important \*\*** When specifying a trace flag with the **-T** option, use an uppercase "T" to pass the trace flag number.</span></span> <span data-ttu-id="efd9b-178">Le caractère minuscule « t » est accepté par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mais il permet de définir d'autres indicateurs de trace internes qui ne servent qu'aux ingénieurs du support technique de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="efd9b-178">A lowercase "t" is accepted by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], but this sets other internal trace flags that are required only by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support engineers.</span></span> <span data-ttu-id="efd9b-179">(Les paramètres spécifiés dans la fenêtre de démarrage du Panneau de configuration ne sont pas lus.)</span><span class="sxs-lookup"><span data-stu-id="efd9b-179">(Parameters specified in the Control Panel startup window are not read.)</span></span>|  
|<span data-ttu-id="efd9b-180">**-x**</span><span class="sxs-lookup"><span data-stu-id="efd9b-180">**-x**</span></span>|<span data-ttu-id="efd9b-181">Désactive les fonctionnalités d'analyse suivantes :</span><span class="sxs-lookup"><span data-stu-id="efd9b-181">Disables the following monitoring features:</span></span><br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="efd9b-182">Les compteurs de l’Analyseur de performances</span><span class="sxs-lookup"><span data-stu-id="efd9b-182">performance monitor counters</span></span><br /><br /> <span data-ttu-id="efd9b-183">Le suivi des statistiques relatives au temps processeur et au taux d'accès au cache</span><span class="sxs-lookup"><span data-stu-id="efd9b-183">Keeping CPU time and cache-hit ratio statistics</span></span><br /><br /> <span data-ttu-id="efd9b-184">La collecte d'informations pour la commande DBCC SQLPERF</span><span class="sxs-lookup"><span data-stu-id="efd9b-184">Collecting information for the DBCC SQLPERF command</span></span><br /><br /> <span data-ttu-id="efd9b-185">La collecte d'informations pour certaines vues de gestion dynamique</span><span class="sxs-lookup"><span data-stu-id="efd9b-185">Collecting information for some dynamic management views</span></span><br /><br /> <span data-ttu-id="efd9b-186">De nombreux points d'événements étendus</span><span class="sxs-lookup"><span data-stu-id="efd9b-186">Many extended-events event points</span></span><br /><br /> <br /><br /> <span data-ttu-id="efd9b-187">\*\* \* \* Avertissement \* lorsque \* \*\* vous utilisez l’option **de démarrage-x** , les informations dont vous disposez pour diagnostiquer les problèmes de performances et de fonctionnement avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont très réduites.</span><span class="sxs-lookup"><span data-stu-id="efd9b-187">**\*\* Warning \*\*** When you use the **-x** startup option, the information that is available for you to diagnose performance and functional problems with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is greatly reduced.</span></span>|  
|<span data-ttu-id="efd9b-188">**-E**</span><span class="sxs-lookup"><span data-stu-id="efd9b-188">**-E**</span></span>|<span data-ttu-id="efd9b-189">Augmente le nombre d'étendues allouées à chaque fichier d'un groupe de fichiers.</span><span class="sxs-lookup"><span data-stu-id="efd9b-189">Increases the number of extents that are allocated for each file in a filegroup.</span></span> <span data-ttu-id="efd9b-190">Cette option peut être utile pour les applications d'entrepôt de données qui ont un nombre limité d'utilisateurs exécutant des index ou des analyses de données.</span><span class="sxs-lookup"><span data-stu-id="efd9b-190">This option may be helpful for data warehouse applications that have a limited number of users running index or data scans.</span></span> <span data-ttu-id="efd9b-191">Elle ne doit pas être utilisée dans d'autres applications car elle peut diminuer les performances.</span><span class="sxs-lookup"><span data-stu-id="efd9b-191">It should not be used in other applications because it might adversely affect performance.</span></span> <span data-ttu-id="efd9b-192">Cette option n'est pas prise en charge dans les versions 32 bits de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="efd9b-192">This option is not supported in 32-bit releases of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
  
## <a name="using-startup-options-for-troubleshooting"></a><span data-ttu-id="efd9b-193">Utilisation des options de démarrage pour le dépannage</span><span class="sxs-lookup"><span data-stu-id="efd9b-193">Using Startup Options for Troubleshooting</span></span>  
 <span data-ttu-id="efd9b-194">Certaines options de démarrage, telles que le mode mono-utilisateur et le mode de configuration minimale, sont principalement utilisées pour le dépannage.</span><span class="sxs-lookup"><span data-stu-id="efd9b-194">Some startup options, such as single-user mode and minimal configuration mode, are principally used during troubleshooting.</span></span> <span data-ttu-id="efd9b-195">Le démarrage du serveur à des fins de dépannage avec les options **-m** ou **-f** est plus facilement réalisable sur la ligne de commande pendant le démarrage manuel de sqlservr.exe.</span><span class="sxs-lookup"><span data-stu-id="efd9b-195">Starting the server for troubleshooting with the **-m** or **-f** options is easiest at the command line, while manually starting sqlservr.exe.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="efd9b-196">Au moment d’un démarrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec l’instruction **net start**, les options de démarrage utilisent une barre oblique (/) au lieu d’un trait d’union (-).</span><span class="sxs-lookup"><span data-stu-id="efd9b-196">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is started by using **net start**, startup options use a slash (/) instead of a hyphen (-).</span></span>  
  
## <a name="using-startup-options-during-normal-operations"></a><span data-ttu-id="efd9b-197">Utilisation des options de démarrage au cours d'opérations normales</span><span class="sxs-lookup"><span data-stu-id="efd9b-197">Using Startup Options During Normal Operations</span></span>  
 <span data-ttu-id="efd9b-198">Il peut être intéressant d'utiliser certaines options de démarrage à chaque fois que vous démarrez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="efd9b-198">You may want to use some startup options every time you start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="efd9b-199">Ces options, telles que **-g** ou commençant par un indicateur de trace, sont plus faciles à effectuer en configurant les paramètres de démarrage à l’aide de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="efd9b-199">These options, such as **-g** or starting with a trace flag, are most easily done by configuring the startup parameters by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="efd9b-200">Cet outil enregistre les options de démarrage sous forme de clés du Registre, de sorte que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] démarre toujours en tenant compte des options de démarrage.</span><span class="sxs-lookup"><span data-stu-id="efd9b-200">These tool saves the startup options as registry keys, enabling [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to always start with the startup options.</span></span>  
  
## <a name="compatibility-support"></a><span data-ttu-id="efd9b-201">Prise en charge de la compatibilité</span><span class="sxs-lookup"><span data-stu-id="efd9b-201">Compatibility Support</span></span>  
 <span data-ttu-id="efd9b-202">Le paramètre **-h**  n’est pas pris en charge dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span><span class="sxs-lookup"><span data-stu-id="efd9b-202">The **-h**  parameter is not supported in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="efd9b-203">Ce paramètre a été utilisé dans les versions antérieures des instances 32 bits de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour réserver l'espace d'adressage de mémoire virtuelle pour les métadonnées d'ajout de mémoire à chaud lorsque AWE est activé.</span><span class="sxs-lookup"><span data-stu-id="efd9b-203">This parameter was used in earlier versions of 32-bit instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to reserve virtual memory address space for Hot Add memory metadata when AWE is enabled.</span></span> <span data-ttu-id="efd9b-204">Pour plus d’informations, consultez [Fonctionnalités SQL Server supprimées dans SQL Server 2014](../../getting-started/discontinued-sql-server-features-in-sql-server-2014.md).</span><span class="sxs-lookup"><span data-stu-id="efd9b-204">For more information, see [Discontinued SQL Server Features in SQL Server 2014](../../getting-started/discontinued-sql-server-features-in-sql-server-2014.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="efd9b-205">Tâches associées</span><span class="sxs-lookup"><span data-stu-id="efd9b-205">Related Tasks</span></span>  
 [<span data-ttu-id="efd9b-206">Configurer l'option de configuration du serveur scan for startup procs</span><span class="sxs-lookup"><span data-stu-id="efd9b-206">Configure the scan for startup procs Server Configuration Option</span></span>](configure-the-scan-for-startup-procs-server-configuration-option.md)  
  
 [<span data-ttu-id="efd9b-207">Démarrer, arrêter, suspendre, reprendre, redémarrer le moteur de base de données, SQL Server Agent ou le service SQL Server Browser</span><span class="sxs-lookup"><span data-stu-id="efd9b-207">Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service</span></span>](start-stop-pause-resume-restart-sql-server-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="efd9b-208">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="efd9b-208">See Also</span></span>  
 <span data-ttu-id="efd9b-209">[CHECKPOINT &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/checkpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="efd9b-209">[CHECKPOINT &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/checkpoint-transact-sql) </span></span>  
 [<span data-ttu-id="efd9b-210">Application sqlservr</span><span class="sxs-lookup"><span data-stu-id="efd9b-210">sqlservr Application</span></span>](../../tools/sqlservr-application.md)  
  
  