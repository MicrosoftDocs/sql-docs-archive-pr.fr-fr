---
title: Prise en charge d’OLTP en mémoire par SQL Server Management Studio | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: ee847b5f-6a1a-448e-a746-d61a023881ff
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 644ba0cfdbe2f0043364c633676bbc536c641efa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87600897"
---
# <a name="sql-server-management-studio-support-for-in-memory-oltp"></a><span data-ttu-id="adf13-102">Prise en charge de SQL Server Management Studio pour l'OLTP en mémoire</span><span class="sxs-lookup"><span data-stu-id="adf13-102">SQL Server Management Studio Support for In-Memory OLTP</span></span>
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="adf13-103">est un environnement intégré pour la gestion de votre infrastructure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="adf13-103">is an integrated environment for managing your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] infrastructure.</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="adf13-104">fournit des outils permettant de configurer, de surveiller et d’administrer les instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="adf13-104">provides tools to configure, monitor, and administer instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="adf13-105">Pour plus d’informations, consultez [SQL Server Management Studio](../../ssms/sql-server-management-studio-ssms.md).</span><span class="sxs-lookup"><span data-stu-id="adf13-105">For more information, see [SQL Server Management Studio](../../ssms/sql-server-management-studio-ssms.md)</span></span>  
  
 <span data-ttu-id="adf13-106">Les tâches de cette rubrique décrivent comment utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour gérer les tables mémoire optimisées ; les index sur les tables mémoire optimisées ; les procédures stockées compilées en mode natif ; et les types de tables mémoire optimisées, définis par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="adf13-106">The tasks in this topic describe how to use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to manage memory-optimized tables; indexes on memory-optimized tables; natively compiled stored procedures; and user-defined, memory-optimized table types.</span></span>  
  
 <span data-ttu-id="adf13-107">Pour plus d’informations sur la façon de créer par programmation des tables optimisées en mémoire, consultez [Création d’une table optimisée en mémoire et d’une procédure stockée compilée en mode natif](creating-a-memory-optimized-table-and-a-natively-compiled-stored-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="adf13-107">For information on how to programmatically create memory-optimized tables, see [Creating a Memory-Optimized Table and a Natively Compiled Stored Procedure](creating-a-memory-optimized-table-and-a-natively-compiled-stored-procedure.md).</span></span>  
  
### <a name="to-create-a-database-with-a-memory-optimized-data-filegroup"></a><span data-ttu-id="adf13-108">Pour créer une base de données avec un groupe de fichiers de données optimisé en mémoire</span><span class="sxs-lookup"><span data-stu-id="adf13-108">To create a database with a memory-optimized data filegroup</span></span>  
  
1.  <span data-ttu-id="adf13-109">Dans l’ **Explorateur d’objets**, connectez-vous à une instance du moteur de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et développez-la.</span><span class="sxs-lookup"><span data-stu-id="adf13-109">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Engine and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="adf13-110">Cliquez avec le bouton droit sur **Bases de données**, puis cliquez sur **Nouvelle base de données**.</span><span class="sxs-lookup"><span data-stu-id="adf13-110">Right-click **Databases**, and then click **New Database**.</span></span>  
  
3.  <span data-ttu-id="adf13-111">Pour ajouter un nouveau groupe de fichiers de données optimisé en mémoire, cliquez sur la page **Groupes de fichiers** .</span><span class="sxs-lookup"><span data-stu-id="adf13-111">To add a new memory-optimized data filegroup, click the **Filegroups** page.</span></span> <span data-ttu-id="adf13-112">Sous **MEMORY OPTIMIZED DATA**, cliquez sur **Ajouter un groupe de fichiers** , puis entrez le nom du groupe de fichiers de données optimisé en mémoire.</span><span class="sxs-lookup"><span data-stu-id="adf13-112">Under **MEMORY OPTIMIZED DATA**, click **Add filegroup** and then enter the name of the memory-optimized data filegroup.</span></span>  <span data-ttu-id="adf13-113">La colonne correspondant aux **fichiers FILESTREAM** représente le nombre de conteneurs dans le groupe de fichiers.</span><span class="sxs-lookup"><span data-stu-id="adf13-113">The column labeled **FILESTREAM Files** represents the number of containers in the filegroup.</span></span> <span data-ttu-id="adf13-114">Les conteneurs sont ajoutés à la page **Général** .</span><span class="sxs-lookup"><span data-stu-id="adf13-114">Containers are added on the **General** page.</span></span>  
  
4.  <span data-ttu-id="adf13-115">Pour ajouter un fichier (conteneur) au groupe de fichiers, cliquez sur la page **Général** .</span><span class="sxs-lookup"><span data-stu-id="adf13-115">To add a file (container) to the filegroup, click the **General** page.</span></span> <span data-ttu-id="adf13-116">Sous **Fichiers de la base de données**, cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="adf13-116">Under **Database files**, click **Add**.</span></span> <span data-ttu-id="adf13-117">Sélectionnez **Type de fichier** comme **Données FILESTREAM**, spécifiez le nom logique du conteneur, sélectionnez le groupe de fichiers optimisé en mémoire, puis assurez-vous que l’option **Croissance automatique/Taille maximale** est définie sur **Illimité**.</span><span class="sxs-lookup"><span data-stu-id="adf13-117">Select **File Type** as **FILESTREAM Data**, specify the logical name of the container, select the memory-optimized filegroup, and make sure that **Autogrowth / Maxsize** is set to **Unlimited**.</span></span>  
  
     <span data-ttu-id="adf13-118">Pour plus d’informations sur la création d’une base de données à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], consultez [Créer une base de données](../databases/create-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="adf13-118">For more information on how to create a new database by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], see [Create a Database](../databases/create-a-database.md).</span></span>  
  
### <a name="to-create-a-memory-optimized-table"></a><span data-ttu-id="adf13-119">Pour créer une table optimisée en mémoire</span><span class="sxs-lookup"><span data-stu-id="adf13-119">To create a memory-optimized table</span></span>  
  
1.  <span data-ttu-id="adf13-120">Dans l’ **Explorateur d’objets**, cliquez avec le bouton droit sur le nœud **Tables** de votre base de données, cliquez sur **Nouveau**, puis cliquez sur **Table optimisée en mémoire**.</span><span class="sxs-lookup"><span data-stu-id="adf13-120">In **Object Explorer**, right-click the **Tables** node of your database, click **New**, and then click **Memory Optimized Table**.</span></span>  
  
     <span data-ttu-id="adf13-121">Un modèle pour créer des tables optimisées en mémoire s'affiche.</span><span class="sxs-lookup"><span data-stu-id="adf13-121">A template for creating memory-optimized tables is displayed.</span></span>  
  
2.  <span data-ttu-id="adf13-122">Pour remplacer les paramètres du modèle, cliquez sur **Spécifier les valeurs des paramètres du modèle** dans le menu **Requête**.</span><span class="sxs-lookup"><span data-stu-id="adf13-122">To replace the template parameters, click **Specify Values for Template Parameters** on the **Query** menu.</span></span>  
  
     <span data-ttu-id="adf13-123">Pour plus d’informations sur la manière d’utiliser les modèles, consultez [Explorateur de modèles](../../ssms/template/template-explorer.md).</span><span class="sxs-lookup"><span data-stu-id="adf13-123">For more information on how to use templates, see [Template Explorer](../../ssms/template/template-explorer.md).</span></span>  
  
3.  <span data-ttu-id="adf13-124">Dans l’ **Explorateur d’objets**, les tables sont d’abord triées en fonction des tables sur disque suivies des tables optimisées en mémoire.</span><span class="sxs-lookup"><span data-stu-id="adf13-124">In **Object Explorer**, tables will be ordered first by disk-based tables followed by memory-optimized tables.</span></span> <span data-ttu-id="adf13-125">Utilisez les **Détails de l’Explorateur d’objets** pour afficher toutes les tables classées par nom.</span><span class="sxs-lookup"><span data-stu-id="adf13-125">Use **Object Explorer Details** to see all tables ordered by name.</span></span>  
  
### <a name="to-create-a-natively-compiled-stored-procedure"></a><span data-ttu-id="adf13-126">Pour créer une procédure stockée compilée en mode natif</span><span class="sxs-lookup"><span data-stu-id="adf13-126">To create a natively compiled stored procedure</span></span>  
  
1.  <span data-ttu-id="adf13-127">Dans l’ **Explorateur d’objets**, cliquez avec le bouton droit sur le nœud **Procédures stockées** de votre base de données, cliquez sur **Nouveau**, puis cliquez sur **Procédure stockée compilée en mode natif**.</span><span class="sxs-lookup"><span data-stu-id="adf13-127">In **Object Explorer**, right-click the **Stored Procedures** node of your database, click **New**, and then click **Natively Compiled Stored Procedure**.</span></span>  
  
     <span data-ttu-id="adf13-128">Un modèle pour créer des procédures stockées compilées en mode natif s'affiche.</span><span class="sxs-lookup"><span data-stu-id="adf13-128">A template for creating natively compiled stored procedures is displayed.</span></span>  
  
2.  <span data-ttu-id="adf13-129">Pour remplacer les paramètres du modèle, cliquez sur **Spécifier les valeurs des paramètres du modèle** dans le menu **Requête**.</span><span class="sxs-lookup"><span data-stu-id="adf13-129">To replace the template parameters, click **Specify Values for Template Parameters** on the **Query menu**.</span></span>  
  
     <span data-ttu-id="adf13-130">Pour plus d’informations sur la création de procédures stockées, consultez [Créer une procédure stockée](../stored-procedures/create-a-stored-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="adf13-130">For more information on how to create a new stored procedure, see [Create a Stored Procedure](../stored-procedures/create-a-stored-procedure.md).</span></span>  
  
### <a name="to-create-a-user-defined-memory-optimized-table-type"></a><span data-ttu-id="adf13-131">Pour créer un type de table optimisée en mémoire, défini par l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="adf13-131">To create a user-defined memory-optimized table type</span></span>  
  
1.  <span data-ttu-id="adf13-132">Dans l’ **Explorateur d’objets**, développez le nœud **Types** de votre base de données, cliquez avec le bouton droit sur le nœud **Types de tables définis par l’utilisateur** , cliquez sur **Nouveau**, puis cliquez sur **Type de table optimisée en mémoire défini par l’utilisateur**.</span><span class="sxs-lookup"><span data-stu-id="adf13-132">In **Object Explorer**, expand the **Types** node of your database, right-click the **User-Defined Table Types** node, click **New**, and then click **User-Defined Memory Optimized Table Type**.</span></span>  
  
     <span data-ttu-id="adf13-133">Un modèle pour créer un type de table optimisée en mémoire défini par l'utilisateur s'affiche.</span><span class="sxs-lookup"><span data-stu-id="adf13-133">A template for creating user-defined memory-optimized table type is displayed.</span></span>  
  
2.  <span data-ttu-id="adf13-134">Pour remplacer les paramètres du modèle, cliquez sur **Spécifier les valeurs des paramètres du modèle** dans le menu **Requête**.</span><span class="sxs-lookup"><span data-stu-id="adf13-134">To replace the template parameters, click **Specify Values for Template Parameters** on the **Query** menu.</span></span>  
  
     <span data-ttu-id="adf13-135">Pour plus d’informations sur la création de procédures stockées, consultez [CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="adf13-135">For more information on how to create a new stored procedure, see [CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql).</span></span>  
  
## <a name="memory-monitoring"></a><span data-ttu-id="adf13-136">Surveillance de la mémoire</span><span class="sxs-lookup"><span data-stu-id="adf13-136">Memory Monitoring</span></span>  
  
#### <a name="view-memory-usage-by-memory-optimized-objects-report"></a><span data-ttu-id="adf13-137">Consulter l'utilisation de la mémoire à l'aide du rapport des objets optimisés en mémoire</span><span class="sxs-lookup"><span data-stu-id="adf13-137">View Memory Usage by Memory-Optimized Objects Report</span></span>  
  
-   <span data-ttu-id="adf13-138">Dans l’ **Explorateur d’objets**, cliquez avec le bouton droit sur la base de données, cliquez sur **Rapports**, cliquez sur **Rapports standard**, puis cliquez sur **Utilisation de la mémoire par les objets mémoire optimisés**.</span><span class="sxs-lookup"><span data-stu-id="adf13-138">In **Object Explorer**, right-click your database, click **Reports**, click **Standard Reports**, and then click **Memory Usage By Memory Optimized Objects**.</span></span>  
  
     <span data-ttu-id="adf13-139">Ce rapport fournit des informations détaillées sur l'utilisation de l'espace mémoire par des objets optimisés en mémoire au sein de la base de données.</span><span class="sxs-lookup"><span data-stu-id="adf13-139">This report provides detailed data on the utilization of memory space by memory-optimized objects within the database.</span></span>  
  
#### <a name="view-properties-for-allocated-and-used-memory-for-a-table-database"></a><span data-ttu-id="adf13-140">Afficher les propriétés de la mémoire allouée et utilisée pour une table ou une base de données</span><span class="sxs-lookup"><span data-stu-id="adf13-140">View Properties for Allocated and Used Memory for a Table, Database</span></span>  
  
1.  <span data-ttu-id="adf13-141">Pour obtenir des informations sur l'utilisation de la mémoire :</span><span class="sxs-lookup"><span data-stu-id="adf13-141">To get information about in-memory usage:</span></span>  
  
    -   <span data-ttu-id="adf13-142">Dans l’ **Explorateur d’objets**, cliquez avec le bouton droit sur la table optimisée en mémoire, cliquez sur **Propriétés**, puis cliquez sur la page **Stockage** .</span><span class="sxs-lookup"><span data-stu-id="adf13-142">In **Object Explorer**, right-click on your memory-optimized table, click **Properties**, and then the **Storage** page.</span></span> <span data-ttu-id="adf13-143">La valeur de la propriété **Espace de données** indique la mémoire utilisée par les données dans la table.</span><span class="sxs-lookup"><span data-stu-id="adf13-143">The value for the **Data Space** property indicates the memory used by the data in the table.</span></span> <span data-ttu-id="adf13-144">La valeur de la propriété **Espace d’index** indique la mémoire utilisée par les index dans la table.</span><span class="sxs-lookup"><span data-stu-id="adf13-144">The value for the **Index Space** property indicates the memory used by the indexes on table.</span></span>  
  
    -   <span data-ttu-id="adf13-145">Dans l’ **Explorateur d’objets**, cliquez avec le bouton droit sur la base de données, cliquez sur **Propriétés**, puis cliquez sur la page **Général** .</span><span class="sxs-lookup"><span data-stu-id="adf13-145">In **Object Explorer**, right-click on your database, click **Properties**, and then click the **General** page.</span></span> <span data-ttu-id="adf13-146">La valeur de la propriété **Mémoire allouée aux objets mémoire optimisés** indique la mémoire allouée aux objets optimisés en mémoire dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="adf13-146">The value for the **Memory Allocated To Memory Optimized Objects** property indicates the memory allocated to memory-optimized objects in the database.</span></span> <span data-ttu-id="adf13-147">La valeur de la propriété **Mémoire utilisée par les objets mémoire optimisés** indique la mémoire utilisée par les objets optimisés en mémoire dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="adf13-147">The value for the **Memory Used By Memory Optimized Objects** property indicates the memory used by memory-optimized objects in the database.</span></span>  
  
## <a name="supported-features-in-ssmanstudiofull"></a><span data-ttu-id="adf13-148">Fonctionnalités prises en charge dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adf13-148">Supported Features in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span></span>  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="adf13-149">prend en charge les fonctionnalités et les opérations prises en charge par le moteur de base de données sur les bases de données contenant un groupe de fichiers de données optimisé en mémoire, des tables optimisées en mémoire, des index et des procédures stockées compilées en mode natif.</span><span class="sxs-lookup"><span data-stu-id="adf13-149">supports features and operations that are supported by the database engine on databases with memory-optimized data filegroup, memory-optimized tables, indexes, and natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="adf13-150">Pour la base de données, la table, la procédure stockée, le type de table défini par l'utilisateur ou les objets Index, les fonctionnalités de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] suivantes ont été mises à jour ou étendues pour prendre en charge OLTP en mémoire.</span><span class="sxs-lookup"><span data-stu-id="adf13-150">For database, table, stored procedure, user-defined table type, or index objects, the following [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] features have been updated or extended to support In-Memory OLTP.</span></span>  
  
-   <span data-ttu-id="adf13-151">Explorateur d’objets</span><span class="sxs-lookup"><span data-stu-id="adf13-151">Object Explorer</span></span>  
  
    -   <span data-ttu-id="adf13-152">Menu contextuels</span><span class="sxs-lookup"><span data-stu-id="adf13-152">Context menus</span></span>  
  
    -   <span data-ttu-id="adf13-153">Paramètres du filtre</span><span class="sxs-lookup"><span data-stu-id="adf13-153">Filter settings</span></span>  
  
    -   <span data-ttu-id="adf13-154">Script en tant que</span><span class="sxs-lookup"><span data-stu-id="adf13-154">Script As</span></span>  
  
    -   <span data-ttu-id="adf13-155">Tâches</span><span class="sxs-lookup"><span data-stu-id="adf13-155">Tasks</span></span>  
  
    -   <span data-ttu-id="adf13-156">Rapports</span><span class="sxs-lookup"><span data-stu-id="adf13-156">Reports</span></span>  
  
    -   <span data-ttu-id="adf13-157">Propriétés</span><span class="sxs-lookup"><span data-stu-id="adf13-157">Properties</span></span>  
  
    -   <span data-ttu-id="adf13-158">Tâche de base de données :</span><span class="sxs-lookup"><span data-stu-id="adf13-158">Database tasks:</span></span>  
  
        -   <span data-ttu-id="adf13-159">Attachez et détachez une base de données qui contient des tables optimisées en mémoire.</span><span class="sxs-lookup"><span data-stu-id="adf13-159">Attach and detach a database that contains memory-optimized tables.</span></span>  
  
             <span data-ttu-id="adf13-160">L’interface utilisateur **Attacher des bases de données** n’affiche pas le groupe de fichiers de données optimisés en mémoire.</span><span class="sxs-lookup"><span data-stu-id="adf13-160">The **Attach Databases** user interface does not display the memory-optimized data filegroup.</span></span> <span data-ttu-id="adf13-161">Toutefois, vous pouvez poursuivre l'attachement de la base de données et celle-ci sera attachée correctement.</span><span class="sxs-lookup"><span data-stu-id="adf13-161">However, you can proceed with attaching the database and the database will be attached correctly.</span></span>  
  
            > [!NOTE]  
            >  <span data-ttu-id="adf13-162">Si vous voulez utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour attacher une base de données qui contient un conteneur de groupe de fichiers de données optimisés en mémoire et, si celui-ci a été créé sur un autre ordinateur, l'emplacement de ce conteneur doit être le même sur les deux ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="adf13-162">If you want to use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to attach a database that has a memory-optimized data filegroup container, and if the database's memory-optimized data filegroup container was created on another computer, the location of the memory-optimized data filegroup container must be the same on both computers.</span></span> <span data-ttu-id="adf13-163">Si vous voulez que l'emplacement du conteneur de groupe de fichiers de données optimisés en mémoire de la base de données soit différent sur le nouvel ordinateur, utilisez [!INCLUDE[tsql](../../includes/tsql-md.md)] pour attacher la base de données.</span><span class="sxs-lookup"><span data-stu-id="adf13-163">If you want the location of the database's memory-optimized data filegroup container to be different on the new computer, you can, use [!INCLUDE[tsql](../../includes/tsql-md.md)] to attach the database.</span></span> <span data-ttu-id="adf13-164">Dans l'exemple suivant, l'emplacement du conteneur de groupe de fichiers de données optimisés en mémoire sur le nouvel ordinateur est C:\Folder2.</span><span class="sxs-lookup"><span data-stu-id="adf13-164">In the following example, the location of the memory-optimized data filegroup container on the new computer is C:\Folder2.</span></span> <span data-ttu-id="adf13-165">Cependant, lors de la création du conteneur de groupe de fichier de données optimisés en mémoire sur le premier ordinateur, l'emplacement était C:\Folder1.</span><span class="sxs-lookup"><span data-stu-id="adf13-165">But when the memory-optimized data filegroup container was created, on the first computer, the location was C:\Folder1.</span></span>  
            >   
            >  `CREATE DATABASE[imoltp] ON`  
            >   
            >  `(NAME =N'imoltp',FILENAME=N'C:\Folder2\imoltp.mdf'),`  
            >   
            >  `(NAME =N'imoltp_mod1',FILENAME=N'C:\Folder2\imoltp_mod1'),`  
            >   
            >  `(NAME =N'imoltp_log',FILENAME=N'C:\Folder2\imoltp_log.ldf')`  
            >   
            >  `FOR ATTACH`  
            >   
            >  `GO`  
  
        -   <span data-ttu-id="adf13-166">Générez des &amp;scripts.</span><span class="sxs-lookup"><span data-stu-id="adf13-166">Generate scripts.</span></span>  
  
             <span data-ttu-id="adf13-167">Dans l’**Assistant Générer et publier des scripts**, la valeur par défaut de l’option de script **Vérifier l’existence de l’objet** est FALSE.</span><span class="sxs-lookup"><span data-stu-id="adf13-167">In the **Generate and Publish Scripts Wizard**, the default value for **Check for object existence** scripting option is FALSE.</span></span> <span data-ttu-id="adf13-168">Si la valeur de l’option de script **Vérifier l’existence de l’objet** est TRUE dans l’écran **Définir les options de script** de l’Assistant, le script généré contient « CREATE PROCEDURE <nom_procédure> AS » et « ALTER PROCEDURE <nom_procédure> <définition_procédure> ».</span><span class="sxs-lookup"><span data-stu-id="adf13-168">If the value of **Check for object existence** scripting option is set to TRUE in the **Set Scripting Options** screen of the wizard, the script generated would contain "CREATE PROCEDURE <procedure_name> AS" and "ALTER PROCEDURE <procedure_name> <procedure_definition>".</span></span> <span data-ttu-id="adf13-169">Lorsqu'il est exécuté, le script généré retourne une erreur, car ALTER PROCEDURE n'est pas pris en charge sur les procédures stockées compilées en mode natif.</span><span class="sxs-lookup"><span data-stu-id="adf13-169">When executed, the generated script will return an error as ALTER PROCEDURE is not supported on natively compiled stored procedures.</span></span>  
  
             <span data-ttu-id="adf13-170">Pour modifier le script généré pour chaque procédure stockée compilée en mode natif :</span><span class="sxs-lookup"><span data-stu-id="adf13-170">To change the generated script for each natively compiled stored procedure:</span></span>  
  
            1.  <span data-ttu-id="adf13-171">Dans « CREATE PROCEDURE <nom_procédure> AS », remplacez « AS » par « <définition_procédure> ».</span><span class="sxs-lookup"><span data-stu-id="adf13-171">In "CREATE PROCEDURE <procedure_name> AS", replace "AS" with "<procedure_definition>".</span></span>  
  
            2.  <span data-ttu-id="adf13-172">Supprimez « ALTER PROCEDURE <nom_procédure> <définition_procédure> ».</span><span class="sxs-lookup"><span data-stu-id="adf13-172">Delete "ALTER PROCEDURE <procedure_name> <procedure_definition>".</span></span>  
  
        -   <span data-ttu-id="adf13-173">Copie de bases de données.</span><span class="sxs-lookup"><span data-stu-id="adf13-173">Copy databases.</span></span> <span data-ttu-id="adf13-174">Pour les bases de données contenant des objets optimisés en mémoire, la création de la base de données sur le serveur de destination et le transfert des données ne seront pas exécutés dans une transaction.</span><span class="sxs-lookup"><span data-stu-id="adf13-174">For databases with memory-optimized objects, the creation of the database on the destination server and transfer of data will not be executed within a transaction.</span></span>  
  
        -   <span data-ttu-id="adf13-175">Importez et exportez des données.</span><span class="sxs-lookup"><span data-stu-id="adf13-175">Import and export data.</span></span> <span data-ttu-id="adf13-176">Utilisez l’ **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , et l’option Copier les données à partir d’une ou plusieurs tables ou vues** .</span><span class="sxs-lookup"><span data-stu-id="adf13-176">Use the **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export WizardCopy data from one or more tables or views** option.</span></span> <span data-ttu-id="adf13-177">Si la table de destination est une table optimisée en mémoire qui n'existe pas dans la base de données de destination :</span><span class="sxs-lookup"><span data-stu-id="adf13-177">If the destination table is a memory-optimized table that does not exist in the destination database:</span></span>  
  
            1.  <span data-ttu-id="adf13-178">Dans l’**Assistant Importation et Exportation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** , dans l’écran **Spécifier la copie ou l’interrogation de table**, sélectionnez **Copier les données à partir d’une ou plusieurs tables ou vues**.</span><span class="sxs-lookup"><span data-stu-id="adf13-178">In the **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard**, in the **Specify Table Copy or Query** screen, select **Copy data from one or more tables or views**.</span></span> <span data-ttu-id="adf13-179">Cliquez ensuite sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="adf13-179">Then click **Next**.</span></span>  
  
            2.  <span data-ttu-id="adf13-180">Cliquez sur **Modifier les mappages**.</span><span class="sxs-lookup"><span data-stu-id="adf13-180">Click **Edit Mappings**.</span></span> <span data-ttu-id="adf13-181">Sélectionnez ensuite **Créer la table de destination** puis cliquez sur **Modifier SQL**.</span><span class="sxs-lookup"><span data-stu-id="adf13-181">Then select **Create destination table** and click **Edit SQL**.</span></span> <span data-ttu-id="adf13-182">Entrez la syntaxe CREATE TABLE pour créer une table optimisée en mémoire sur la base de données de destination.</span><span class="sxs-lookup"><span data-stu-id="adf13-182">Enter the CREATE TABLE syntax for creating a memory-optimized table on the destination database.</span></span> <span data-ttu-id="adf13-183">Cliquez sur **OK** et suivez les étapes restantes de l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="adf13-183">Click **OK** and complete the remaining steps in the wizard.</span></span>  
  
        -   <span data-ttu-id="adf13-184">Plans de maintenance.</span><span class="sxs-lookup"><span data-stu-id="adf13-184">Maintenance plans.</span></span> <span data-ttu-id="adf13-185">Les tâches de maintenance de réorganisation et de reconstruction d'index ne sont pas prises en charge sur les tables optimisées en mémoire et leurs index.</span><span class="sxs-lookup"><span data-stu-id="adf13-185">The maintenance tasks reorganize index and rebuild index are not supported on memory-optimized tables and their indexes.</span></span> <span data-ttu-id="adf13-186">Par conséquent, lorsqu'un plan de maintenance pour reconstruire et réorganiser l'index est exécuté, les tables optimisées en mémoire et leurs index dans les bases de données sélectionnées sont omis.</span><span class="sxs-lookup"><span data-stu-id="adf13-186">Therefore, when a maintenance plan for rebuild index and reorganize index are executed, the memory-optimized tables and their indexes in the selected databases are omitted.</span></span>  
  
             <span data-ttu-id="adf13-187">Les statistiques de mise à jour des tâches de maintenance ne sont pas prises en charge avec une analyse d'échantillons sur les tables optimisées en mémoire et leurs index.</span><span class="sxs-lookup"><span data-stu-id="adf13-187">The maintenance task update statistics are not supported with a sample scan on memory-optimized tables and their indexes.</span></span> <span data-ttu-id="adf13-188">Par conséquent, lorsqu'un plan de maintenance des statistiques de mise à jour est exécuté, les statistiques des tables mémoire optimisées et leurs index sont toujours mis à jour avec `WITH FULLSCAN, NORECOMPUTE`.</span><span class="sxs-lookup"><span data-stu-id="adf13-188">Therefore, when a maintenance plan for update statistics is executed, the statistics for memory-optimized tables and their indexes are always updated to `WITH FULLSCAN, NORECOMPUTE`.</span></span>  
  
-   <span data-ttu-id="adf13-189">Volet Détails de l'Explorateur d'objets</span><span class="sxs-lookup"><span data-stu-id="adf13-189">Object Explorer details pane</span></span>  
  
-   <span data-ttu-id="adf13-190">Explorateur de modèles</span><span class="sxs-lookup"><span data-stu-id="adf13-190">Template Explorer</span></span>  
  
## <a name="unsupported-features-in-ssmanstudiofull"></a><span data-ttu-id="adf13-191">Fonctionnalités non prises en charge dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adf13-191">Unsupported Features in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span></span>  
 <span data-ttu-id="adf13-192">Pour les objets OLTP en mémoire, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ne prend pas en charge les fonctionnalités et les opérations qui ne sont pas non plus prises en charge par le moteur de base de données.</span><span class="sxs-lookup"><span data-stu-id="adf13-192">For In-Memory OLTP objects, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] does not support features and operations that are also not supported by the database engine.</span></span>  
  
 <span data-ttu-id="adf13-193">Pour plus d’informations sur les fonctionnalités non prises en charge [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , consultez [fonctionnalités de SQL Server prises en](unsupported-sql-server-features-for-in-memory-oltp.md)charge.</span><span class="sxs-lookup"><span data-stu-id="adf13-193">For more information on unsupported [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features, see [Supported SQL Server Features](unsupported-sql-server-features-for-in-memory-oltp.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adf13-194">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="adf13-194">See Also</span></span>  
 [<span data-ttu-id="adf13-195">Prise en charge d'OLTP en mémoire par SQL Server</span><span class="sxs-lookup"><span data-stu-id="adf13-195">SQL Server Support for In-Memory OLTP</span></span>](sql-server-support-for-in-memory-oltp.md)  
  
  