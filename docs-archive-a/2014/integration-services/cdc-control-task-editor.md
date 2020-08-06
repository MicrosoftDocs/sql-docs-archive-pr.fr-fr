---
title: Éditeur de tâche de contrôle CDC | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdccontroltask.config.f1
ms.assetid: 4f09d040-9ec8-4aaa-b684-f632d571f0a8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6b60f2a9126dbbda934124b39f36ccd90b4e6cc6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613586"
---
# <a name="cdc-control-task-editor"></a><span data-ttu-id="23157-102">Éditeur de tâche de contrôle CDC</span><span class="sxs-lookup"><span data-stu-id="23157-102">CDC Control Task Editor</span></span>
  <span data-ttu-id="23157-103">Utilisez la boîte de dialogue **Éditeur de tâche de contrôle CDC** pour configurer la tâche de contrôle CDC.</span><span class="sxs-lookup"><span data-stu-id="23157-103">Use the **CDC Control Task Editor** dialog box to configure the CDC Control task.</span></span> <span data-ttu-id="23157-104">La configuration de la tâche de contrôle CDC inclut la définition d'une connexion à la base de données CDC, l'opération de la tâche CDC et des informations de gestion d'état.</span><span class="sxs-lookup"><span data-stu-id="23157-104">The CDC Control task configuration includes defining a connection to the CDC database, the CDC task operation and the state management information.</span></span>  
  
 <span data-ttu-id="23157-105">Pour en savoir plus sur la tâche de contrôle CDC, consultez [CDC Control Task](control-flow/cdc-control-task.md).</span><span class="sxs-lookup"><span data-stu-id="23157-105">To learn more about the CDC Control task, see [CDC Control Task](control-flow/cdc-control-task.md).</span></span>  
  
 <span data-ttu-id="23157-106">**Pour ouvrir l'Éditeur de tâche de contrôle CDC**</span><span class="sxs-lookup"><span data-stu-id="23157-106">**To open the CDC Control Task Editor**</span></span>  
  
1.  <span data-ttu-id="23157-107">Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], ouvrez le package [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] doté de la tâche de contrôle CDC.</span><span class="sxs-lookup"><span data-stu-id="23157-107">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] package that has the CDC Control task.</span></span>  
  
2.  <span data-ttu-id="23157-108">Sous l’onglet **Flux de contrôle** , double-cliquez sur la tâche de contrôle CDC.</span><span class="sxs-lookup"><span data-stu-id="23157-108">On the **Control Flow** tab, double-click the CDC Control task.</span></span>  
  
## <a name="options"></a><span data-ttu-id="23157-109">Options</span><span class="sxs-lookup"><span data-stu-id="23157-109">Options</span></span>  
 <span data-ttu-id="23157-110">**Gestionnaire de connexions ADO.NET de base de données CDC SQL Server**</span><span class="sxs-lookup"><span data-stu-id="23157-110">**SQL Server CDC database ADO.NET connection manager**</span></span>  
 <span data-ttu-id="23157-111">Sélectionnez un gestionnaire de connexions existant dans la liste ou cliquez sur **Nouveau** pour créer une connexion.</span><span class="sxs-lookup"><span data-stu-id="23157-111">Select an existing connection manager from the list, or click **New** to create a new connection.</span></span> <span data-ttu-id="23157-112">La connexion doit être établie avec une base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] activée pour la capture de données modifiées et dans laquelle la table de modifications sélectionnée est localisée.</span><span class="sxs-lookup"><span data-stu-id="23157-112">The connection must be to a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database that is enabled for CDC and where the selected change table is located.</span></span>  
  
 <span data-ttu-id="23157-113">**Opération de contrôle de capture de données modifiées**</span><span class="sxs-lookup"><span data-stu-id="23157-113">**CDC Control Operation**</span></span>  
 <span data-ttu-id="23157-114">Sélectionnez l'opération à exécuter pour cette tâche.</span><span class="sxs-lookup"><span data-stu-id="23157-114">Select the operation to run for this task.</span></span> <span data-ttu-id="23157-115">Toutes les opérations utilisent la variable d'état qui est stockée dans une variable de package SSIS qui stocke l'état et le passe entre les différents composants du package.</span><span class="sxs-lookup"><span data-stu-id="23157-115">All operations use the state variable that is stored in an SSIS package variable that stores the state and passes it between the different components in the package.</span></span>  
  
-   <span data-ttu-id="23157-116">**Marquer le début de la charge initiale**: cette opération est utilisée en exécutant une charge initiale d'une base de données active sans instantané.</span><span class="sxs-lookup"><span data-stu-id="23157-116">**Mark initial load start**: This operation is used when executing an initial load from an active database without a snapshot.</span></span> <span data-ttu-id="23157-117">Elle est invoquée au début d'un package de chargement initial pour enregistrer le numéro LSN actuel dans la base de données source avant que le package de chargement initial commence à lire les tables sources.</span><span class="sxs-lookup"><span data-stu-id="23157-117">It is invoked at the beginning of an initial-load package to record the current LSN in the source database before the initial-load package starts reading the source tables.</span></span> <span data-ttu-id="23157-118">Cela requiert une connexion à la base de données source.</span><span class="sxs-lookup"><span data-stu-id="23157-118">This requires a connection to the source database.</span></span>  
  
     <span data-ttu-id="23157-119">Si vous sélectionnez **Marquer le début de la charge initiale** quand vous travaillez sur la capture de données modifiées [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] (autrement dit, hors d’Oracle) l’utilisateur spécifié dans le gestionnaire de connexions doit être  **db_owner** ou **sysadmin**.</span><span class="sxs-lookup"><span data-stu-id="23157-119">If you select **Mark Initial Load Start** when working on [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] CDC (that is, not Oracle) the user specified in the connection manager must be either  **db_owner** or **sysadmin**.</span></span>  
  
-   <span data-ttu-id="23157-120">**Marquer la fin de la charge initiale**: cette opération est utilisée en exécutant une charge initiale d'une base de données active sans instantané.</span><span class="sxs-lookup"><span data-stu-id="23157-120">**Mark initial load end**: This operation is used when executing an initial load from an active database without a snapshot.</span></span> <span data-ttu-id="23157-121">Elle est invoquée à la fin d'un package de chargement initial pour enregistrer le numéro LSN actuel dans la base de données source une fois que le package de chargement initial a fini de lire les tables sources.</span><span class="sxs-lookup"><span data-stu-id="23157-121">It is invoked at the end of an initial-load package to record the current LSN in the source database after the initial-load package finished reading the source tables.</span></span> <span data-ttu-id="23157-122">Ce numéro LSN est déterminé en enregistrant l'heure à laquelle cette opération s'est produite, puis en interrogeant la table de mappage `cdc.lsn_time_`dans la base de données CDC afin de rechercher une modification survenue après cette heure.</span><span class="sxs-lookup"><span data-stu-id="23157-122">This LSN is determined by recording nthe current time when this operation occurred and then querying the `cdc.lsn_time_`mapping table in the CDC database looking for a change that occurred after that time</span></span>  
  
     <span data-ttu-id="23157-123">Si vous sélectionnez **Marquer la fin de la charge initiale** quand vous travaillez sur la capture de données modifiées [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] (autrement dit, hors d’Oracle) l’utilisateur spécifié dans le gestionnaire de connexions doit être  **db_owner** ou **sysadmin**.</span><span class="sxs-lookup"><span data-stu-id="23157-123">If you select **Mark Initial Load End** when working on [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] CDC (that is, not Oracle) the user specified in the connection manager must be either  **db_owner** or **sysadmin**.</span></span>  
  
-   <span data-ttu-id="23157-124">**Marquer le début CDC** : cette opération est utilisée lorsque la charge initiale est effectuée à partir d'un fichier de base de données d'instantanés ou d'une base de données inactive.</span><span class="sxs-lookup"><span data-stu-id="23157-124">**Mark CDC start**: This operation is used when then the initial load is made from a snapshot database or from a quiescence database.</span></span> <span data-ttu-id="23157-125">Elle est appelée à n'importe quel stade du package de charge initiale.</span><span class="sxs-lookup"><span data-stu-id="23157-125">It is invoked at any point within the initial load package.</span></span> <span data-ttu-id="23157-126">L'opération accepte un paramètre qui peut être un numéro LSN d'instantané, un nom de base de données d'instantanés (de laquelle le numéro LSN d'instantané dérive automatiquement) ou qui peut être laissé vide, auquel cas le numéro LSN de la base de données actuelle est utilisé comme dernier numéro LSN pour le package de traitement des modifications.</span><span class="sxs-lookup"><span data-stu-id="23157-126">The operation accepts a parameter that can be a snapshot LSN, a name of a snapshot database (from which the snapshot LSN will be derived automatically) or it can be left empty, in which case the current database LSN is used as the start LSN for the change processing package.</span></span>  
  
     <span data-ttu-id="23157-127">Cette opération est utilisée à la place des opérations Marquer le début/la fin de la charge initiale.</span><span class="sxs-lookup"><span data-stu-id="23157-127">This operation is used instead of the Mark Initial Load Start/End operations.</span></span>  
  
     <span data-ttu-id="23157-128">Si vous sélectionnez **Marquer le début CDC** quand vous travaillez sur la capture de données modifiées [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] (autrement dit, hors d’Oracle) l’utilisateur spécifié dans le gestionnaire de connexions doit être  **db_owner** ou **sysadmin**.</span><span class="sxs-lookup"><span data-stu-id="23157-128">If you select **Mark CDC Start** when working on [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] CDC (that is, not Oracle) the user specified in the connection manager must be either  **db_owner** or **sysadmin**.</span></span>  
  
-   <span data-ttu-id="23157-129">**Get processing range**: cette opération est utilisée dans un package de traitement des modifications avant d'appeler le flux de données qui utilise le flux de données source CDC.</span><span class="sxs-lookup"><span data-stu-id="23157-129">**Get processing range**: This operation is used in a change processing package before invoking the data flow that uses the CDC Source data flow.</span></span> <span data-ttu-id="23157-130">Elle établit une plage de numéros LSN que le flux de données de la source CDC lit lorsqu'il est appelé.</span><span class="sxs-lookup"><span data-stu-id="23157-130">It establishes a range of LSNs that the CDC Source data flow reads when invoked.</span></span> <span data-ttu-id="23157-131">La plage est stockée dans une variable de package SSIS qui est utilisée par la source CDC pendant le traitement du flux de données.</span><span class="sxs-lookup"><span data-stu-id="23157-131">The range is stored in an SSIS package variable that is used by the CDC Source during data-flow processing.</span></span>  
  
     <span data-ttu-id="23157-132">Pour plus d’informations sur les états CDC stockés, consultez [Définir une variable d’état](data-flow/define-a-state-variable.md).</span><span class="sxs-lookup"><span data-stu-id="23157-132">For more information about the possible CDC states that are stored, see [Define a State Variable](data-flow/define-a-state-variable.md).</span></span>  
  
-   <span data-ttu-id="23157-133">**Marquer la plage traitée**: cette opération est utilisée dans un package de traitement des modifications à la fin d’une exécution CDC (après que le flux de données CDC s’est terminé correctement) pour inscrire le dernier numéro LSN qui était complètement traité dans l’exécution CDC.</span><span class="sxs-lookup"><span data-stu-id="23157-133">**Mark processed range**: This operation is used in a change processing package at the end of a  CDC run (after the CDC data flow is completed successfully) to record the last LSN that was fully processed in the CDC run.</span></span> <span data-ttu-id="23157-134">Lors de la prochaine exécution de `GetProcessingRange` , cette position détermine le début de la prochaine plage de traitement.</span><span class="sxs-lookup"><span data-stu-id="23157-134">The next time `GetProcessingRange` is executed, this position determines the start of the next processing range.</span></span>  
  
-   <span data-ttu-id="23157-135">**Réinitialiser l'état CDC**: cette opération est utilisée pour réinitialiser l'état de capture de données modifiées (CDC) permanent associé au contexte CDC actuel.</span><span class="sxs-lookup"><span data-stu-id="23157-135">**Reset CDC state**: This operation is used to reset the persistent CDC state associated with the current CDC context.</span></span> <span data-ttu-id="23157-136">Une fois cette opération effectuée, le numéro LSN maximal actuel de la table d’horodatage des LSN `sys.fn_cdc_get_max_lsn` devient le début de la plage de traitement suivante.</span><span class="sxs-lookup"><span data-stu-id="23157-136">After this operation is run, the current maximum LSN from the LSN-timestamp `sys.fn_cdc_get_max_lsn` table becomes the start of the range for the next processing range.</span></span> <span data-ttu-id="23157-137">Cette opération requiert une connexion à la base de données source.</span><span class="sxs-lookup"><span data-stu-id="23157-137">This operation requires a connection to the source database.</span></span>  
  
     <span data-ttu-id="23157-138">Cette opération est notamment utilisée lorsque vous souhaitez traiter uniquement les enregistrements de modifications récents et ignorer tous les anciens enregistrements de modifications.</span><span class="sxs-lookup"><span data-stu-id="23157-138">An example of when this operation is used is when you want to process only the newly created change records and ignore all old change records.</span></span>  
  
 <span data-ttu-id="23157-139">**Variable contenant l'état CDC**</span><span class="sxs-lookup"><span data-stu-id="23157-139">**Variable containing the CDC state**</span></span>  
 <span data-ttu-id="23157-140">Sélectionnez la variable de package SSIS qui stocke les informations d'état de l'opération de tâche.</span><span class="sxs-lookup"><span data-stu-id="23157-140">Select the SSIS package variable that stores the state information for the task operation.</span></span> <span data-ttu-id="23157-141">Vous devez définir une variable avant de commencer.</span><span class="sxs-lookup"><span data-stu-id="23157-141">You should define a variable before you begin.</span></span> <span data-ttu-id="23157-142">Si vous sélectionnez **Persistance d'état automatique**, la variable d'état est chargée et enregistrée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="23157-142">If you select **Automatic state persistence**, the state variable is loaded and saved automatically.</span></span>  
  
 <span data-ttu-id="23157-143">Pour plus d’informations sur la définition de la variable d’état, consultez [Définir une variable d’état](data-flow/define-a-state-variable.md).</span><span class="sxs-lookup"><span data-stu-id="23157-143">For more information about defining the state variable, see [Define a State Variable](data-flow/define-a-state-variable.md).</span></span>  
  
 <span data-ttu-id="23157-144">**Numéro séquentiel dans le journal (LSN) SQL Server pour démarrer le nom CDC/instantané :**</span><span class="sxs-lookup"><span data-stu-id="23157-144">**SQL Server LSN to start the CDC/Snapshot name:**</span></span>  
 <span data-ttu-id="23157-145">Entrez le numéro LSN de la base de données source ou de la base de données d'instantanés à partir de laquelle la charge initiale est effectuée pour déterminer le début de la capture de données modifiées.</span><span class="sxs-lookup"><span data-stu-id="23157-145">Type the current source database LSN or the name of the snapshot database from which the initial load is performed to determine where the CDC starts.</span></span> <span data-ttu-id="23157-146">Le numéro est disponible uniquement si **Opération de contrôle CDC** est défini sur **Marquer le début CDC**.</span><span class="sxs-lookup"><span data-stu-id="23157-146">This is available only if the **CDC Control Operation** is set to **Mark CDC Start**.</span></span>  
  
 <span data-ttu-id="23157-147">Pour plus d'informations sur ces opérations, consultez [CDC Control Task](control-flow/cdc-control-task.md).</span><span class="sxs-lookup"><span data-stu-id="23157-147">For more information about these operations, see [CDC Control Task](control-flow/cdc-control-task.md)</span></span>  
  
 <span data-ttu-id="23157-148">**Stockage automatique de l'état dans une table de base de données**</span><span class="sxs-lookup"><span data-stu-id="23157-148">**Automatically store state in a database table**</span></span>  
 <span data-ttu-id="23157-149">Activez cette case à cocher pour que la tâche de contrôle CDC gère automatiquement le chargement et le stockage de l'état CDC dans une table d'états contenue dans la base de données spécifiée.</span><span class="sxs-lookup"><span data-stu-id="23157-149">Select this check box for the CDC Control task to automatically handle loading and storing the CDC state in a state table contained in the specified database.</span></span> <span data-ttu-id="23157-150">Si cette case n'est pas sélectionnée, le développeur doit charger l'état CDC au démarrage du package et l'enregistrer dès qu'il change.</span><span class="sxs-lookup"><span data-stu-id="23157-150">When not selected, the developer must load the CDC State when the package starts and save it whenever the CDC State changes.</span></span>  
  
 <span data-ttu-id="23157-151">**Gestionnaire de connexions de la base de données où l'état est stocké**</span><span class="sxs-lookup"><span data-stu-id="23157-151">**Connection manager for the database where the state is stored**</span></span>  
 <span data-ttu-id="23157-152">Sélectionnez un gestionnaire de connexions ADO.NET existant dans la liste ou cliquez sur Nouveau pour créer une nouvelle connexion.</span><span class="sxs-lookup"><span data-stu-id="23157-152">Select an existing ADO.NET connection manager from the list, or click New to create a new connection.</span></span> <span data-ttu-id="23157-153">La connexion concerne une base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] qui contient la table State.</span><span class="sxs-lookup"><span data-stu-id="23157-153">This connection is to a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database that contains the State table.</span></span> <span data-ttu-id="23157-154">La table State contient les informations d'état.</span><span class="sxs-lookup"><span data-stu-id="23157-154">The State table contains the State information.</span></span>  
  
 <span data-ttu-id="23157-155">Ces informations sont disponibles uniquement si vous avez sélectionné **Persistance d'état automatique** et il s'agit d'un paramètre obligatoire.</span><span class="sxs-lookup"><span data-stu-id="23157-155">This is available only if **Automatic state persistence** is selected and it is a required parameter.</span></span>  
  
 <span data-ttu-id="23157-156">**Table à utiliser pour stocker l'état**</span><span class="sxs-lookup"><span data-stu-id="23157-156">**Table to use for storing state**</span></span>  
 <span data-ttu-id="23157-157">Tapez le nom de la table d'état à utiliser pour stocker l'état CDC.</span><span class="sxs-lookup"><span data-stu-id="23157-157">Type the name of the state table to be used for storing the CDC state.</span></span> <span data-ttu-id="23157-158">La table spécifiée doit être composée de deux colonnes appelées **name** et **state** avec le type de données **varchar (256)**.</span><span class="sxs-lookup"><span data-stu-id="23157-158">The table specified must have two columns called **name** and **state** and both columns must be of the data type **varchar (256)**.</span></span>  
  
 <span data-ttu-id="23157-159">Vous pouvez éventuellement sélectionner **Nouveau** pour obtenir un script SQL qui génère une nouvelle table d'état avec les colonnes requises.</span><span class="sxs-lookup"><span data-stu-id="23157-159">You can optionally select **New** to get an SQL script that builds a new State table with the required columns.</span></span> <span data-ttu-id="23157-160">Lorsque **Persistance d'état automatique** est sélectionné, le développeur doit créer une table d'état en fonction des spécifications ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="23157-160">When **Automatic state persistence** is selected, the developer must create a state table according to the requirements listed above.</span></span>  
  
 <span data-ttu-id="23157-161">Ces informations sont disponibles uniquement si vous avez sélectionné **Persistance d'état automatique** et il s'agit d'un paramètre obligatoire.</span><span class="sxs-lookup"><span data-stu-id="23157-161">This is available only if **Automatic state persistence** is selected and it is a required parameter.</span></span>  
  
 <span data-ttu-id="23157-162">**Nom de l’état**</span><span class="sxs-lookup"><span data-stu-id="23157-162">**State name**</span></span>  
 <span data-ttu-id="23157-163">Entrez le nom à associer à l'état CDC persistant.</span><span class="sxs-lookup"><span data-stu-id="23157-163">Type a name to associate with the persistent CDC state.</span></span> <span data-ttu-id="23157-164">La charge complète et les packages CDC qui fonctionnent avec le même contexte CDC auront un nom d'état commun.</span><span class="sxs-lookup"><span data-stu-id="23157-164">The full load and CDC packages that work with the same CDC context will specify a common state name.</span></span> <span data-ttu-id="23157-165">Ce nom est utilisé pour surveiller la ligne d'état dans la table d'état.</span><span class="sxs-lookup"><span data-stu-id="23157-165">This name is used for looking up the state row in the state table</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23157-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23157-166">See Also</span></span>  
 [<span data-ttu-id="23157-167">Propriétés personnalisées de la tâche de contrôle de capture de données modifiées</span><span class="sxs-lookup"><span data-stu-id="23157-167">CDC Control Task Custom Properties</span></span>](control-flow/cdc-control-task-custom-properties.md)  
  
  