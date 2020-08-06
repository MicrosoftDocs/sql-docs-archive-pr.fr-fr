---
title: Conteneur de boucles Foreach | Microsoft Docs
ms.custom: ''
ms.date: 08/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.foreachloopcontainer.f1
helpviewer_keywords:
- repeating control flow
- Foreach Loop containers
- foreach enumerators [Integration Services]
- containers [Integration Services], Foreach Loop
ms.assetid: dd6cc2ba-631f-4adf-89dc-29ef449c6933
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 386270ad24a5f3c47309c15293f8c8a53893373d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87600193"
---
# <a name="foreach-loop-container"></a><span data-ttu-id="e5313-102">Conteneur de boucles Foreach</span><span class="sxs-lookup"><span data-stu-id="e5313-102">Foreach Loop Container</span></span>
  <span data-ttu-id="e5313-103">Le conteneur de boucles Foreach définit un flux de contrôle répétitif dans un package.</span><span class="sxs-lookup"><span data-stu-id="e5313-103">The Foreach Loop container defines a repeating control flow in a package.</span></span> <span data-ttu-id="e5313-104">La mise en œuvre de la boucle est similaire à la structure de bouclage **Foreach** des langages de programmation.</span><span class="sxs-lookup"><span data-stu-id="e5313-104">The loop implementation is similar to **Foreach** looping structure in programming languages.</span></span> <span data-ttu-id="e5313-105">Dans un package, le bouclage repose sur l'utilisation d'un énumérateur Foreach.</span><span class="sxs-lookup"><span data-stu-id="e5313-105">In a package, looping is enabled by using a Foreach enumerator.</span></span>  <span data-ttu-id="e5313-106">Le conteneur de boucles Foreach répète le flux de contrôle pour chaque membre d'un énumérateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="e5313-106">The Foreach Loop container repeats the control flow for each member of a specified enumerator.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="e5313-107">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] fournit les types d’énumérateur suivants :</span><span class="sxs-lookup"><span data-stu-id="e5313-107">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] provides the following enumerator types:</span></span>  
  
-   <span data-ttu-id="e5313-108">Foreach ADO Enumerator, pour l'énumération des lignes des tables.</span><span class="sxs-lookup"><span data-stu-id="e5313-108">Foreach ADO enumerator to enumerate rows in tables.</span></span> <span data-ttu-id="e5313-109">Par exemple, vous pouvez obtenir les lignes d'un ensemble d'enregistrements ADO.</span><span class="sxs-lookup"><span data-stu-id="e5313-109">For example, you can get the rows in an ADO recordset.</span></span>  
  
     <span data-ttu-id="e5313-110">La destination de l'ensemble d'enregistrements enregistre les données en mémoire dans un ensemble d'enregistrements stocké dans une variable de package de type `Object`.</span><span class="sxs-lookup"><span data-stu-id="e5313-110">The Recordset destination saves data in memory in a recordset that is stored in a package variable of `Object` data type.</span></span> <span data-ttu-id="e5313-111">Vous devez en général utiliser un conteneur de boucles Foreach avec l'énumérateur ADO Foreach pour traiter une par une les lignes de l'ensemble d'enregistrements.</span><span class="sxs-lookup"><span data-stu-id="e5313-111">You typically use a Foreach Loop container with the Foreach ADO enumerator to process one row of the recordset at a time.</span></span> <span data-ttu-id="e5313-112">La variable spécifiée pour l'énumérateur ADO Foreach doit être de type Object.</span><span class="sxs-lookup"><span data-stu-id="e5313-112">The variable specified for the Foreach ADO enumerator must be of Object data type.</span></span> <span data-ttu-id="e5313-113">Pour plus d'informations sur la destination d'un ensemble d'enregistrements, consultez [Use a Recordset Destination](../data-flow/recordset-destination.md).</span><span class="sxs-lookup"><span data-stu-id="e5313-113">For more information about the Recordeset destination, see [Use a Recordset Destination](../data-flow/recordset-destination.md).</span></span>  
  
-   <span data-ttu-id="e5313-114">Énumérateur de l'ensemble de lignes du schéma Foreach ADO.NET, pour l'énumération des informations de schéma relatives à une source de données.</span><span class="sxs-lookup"><span data-stu-id="e5313-114">Foreach ADO.NET Schema Rowset enumerator to enumerate the schema information about a data source.</span></span> <span data-ttu-id="e5313-115">Par exemple, vous pouvez énumérer les tables de la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et en obtenir la liste.</span><span class="sxs-lookup"><span data-stu-id="e5313-115">For example, you can enumerate and get a list of the tables in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.</span></span>  
  
-   <span data-ttu-id="e5313-116">Énumérateur de fichier Foreach, pour l'énumération des fichiers d'un dossier.</span><span class="sxs-lookup"><span data-stu-id="e5313-116">Foreach File enumerator to enumerate files in a folder.</span></span> <span data-ttu-id="e5313-117">L'énumérateur peut parcourir les sous-dossiers.</span><span class="sxs-lookup"><span data-stu-id="e5313-117">The enumerator can traverse subfolders.</span></span> <span data-ttu-id="e5313-118">Par exemple, vous pouvez lire tous les fichiers portant l'extension de nom de fichier \*.log stockés dans le dossier Windows et ses sous-dossiers.</span><span class="sxs-lookup"><span data-stu-id="e5313-118">For example, you can read all the files that have the \*.log file name extension in the Windows folder and its subfolders.</span></span>  
  
-   <span data-ttu-id="e5313-119">Foreach From Variable Enumerator, pour l'énumération de l'objet énumérable contenu dans une variable spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e5313-119">Foreach From Variable enumerator to enumerate the enumerable object that a specified variable contains.</span></span> <span data-ttu-id="e5313-120">L'objet énumérable peut être un tableau, un `DataTable` ADO.NET, un énumérateur [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], etc.</span><span class="sxs-lookup"><span data-stu-id="e5313-120">The enumerable object can be an array, an ADO.NET `DataTable`, an [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] enumerator, and so on.</span></span> <span data-ttu-id="e5313-121">Par exemple, vous pouvez énumérer les valeurs d'un tableau qui contient des noms de serveurs.</span><span class="sxs-lookup"><span data-stu-id="e5313-121">For example, you can enumerate the values of an array that contains the name of servers.</span></span>  
  
-   <span data-ttu-id="e5313-122">Énumérateur d'élément Foreach, pour l'énumération des éléments qui sont des collections.</span><span class="sxs-lookup"><span data-stu-id="e5313-122">Foreach Item enumerator to enumerate items that are collections.</span></span> <span data-ttu-id="e5313-123">Par exemple, vous pouvez énumérer les noms d'exécutables et de répertoires de travail qu'une tâche d'exécution de processus utilise.</span><span class="sxs-lookup"><span data-stu-id="e5313-123">For example, you can enumerate the names of executables and working directories that an Execute Process task uses.</span></span>  
  
-   <span data-ttu-id="e5313-124">Foreach NodeList Enumerator, pour l'énumération de l'ensemble de résultats d'une expression XPath (XML Path Language).</span><span class="sxs-lookup"><span data-stu-id="e5313-124">Foreach Nodelist enumerator to enumerate the result set of an XML Path Language (XPath) expression.</span></span> <span data-ttu-id="e5313-125">Par exemple, l'expression suivante énumère tous les auteurs de la période classique et en obtient la liste : `/authors/author[@period='classical']`.</span><span class="sxs-lookup"><span data-stu-id="e5313-125">For example, this expression enumerates and gets a list of all the authors in the classical period: `/authors/author[@period='classical']`.</span></span>  
  
-   <span data-ttu-id="e5313-126">Foreach SMO Enumerator, pour l'énumération des objets SMO ( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Object).</span><span class="sxs-lookup"><span data-stu-id="e5313-126">Foreach SMO enumerator to enumerate [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) objects.</span></span> <span data-ttu-id="e5313-127">Par exemple, vous pouvez énumérer les vues d'une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et en obtenir la liste.</span><span class="sxs-lookup"><span data-stu-id="e5313-127">For example, you can enumerate and get a list of the views in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.</span></span>  
  
-   <span data-ttu-id="e5313-128">Énumérateur ForEach Azure Blob pour énumérer les objets blob dans un conteneur d'objets blob dans un stockage Azure.</span><span class="sxs-lookup"><span data-stu-id="e5313-128">Foreach Azure Blob enumerator to enumerate blobs in a blob container in an Azure Storage.</span></span>  
  
-   <span data-ttu-id="e5313-129">Énumérateur foreach ADLS file pour énumérer les fichiers dans un répertoire ADLS.</span><span class="sxs-lookup"><span data-stu-id="e5313-129">Foreach ADLS File enumerator to enumerate files in an ADLS directory.</span></span>
  
 <span data-ttu-id="e5313-130">Le schéma suivant montre un conteneur de boucles Foreach ayant une tâche de système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="e5313-130">The following diagram shows a Foreach Loop container that has a File System task.</span></span> <span data-ttu-id="e5313-131">La boucle Foreach utilise l'énumérateur de fichier Foreach, tandis que la tâche de système de fichiers est configurée pour copier un fichier.</span><span class="sxs-lookup"><span data-stu-id="e5313-131">The Foreach loop uses the Foreach File enumerator, and the File System task is configured to copy a file.</span></span> <span data-ttu-id="e5313-132">Si le dossier spécifié par l'énumérateur contient quatre fichiers, la boucle se répète quatre fois et copie quatre fichiers.</span><span class="sxs-lookup"><span data-stu-id="e5313-132">If the folder that the enumerator specifies contains four files, the loop repeats four times and copies four files.</span></span>  
  
 <span data-ttu-id="e5313-133">![Conteneur de boucles Foreach énumérant un dossier](../media/ssis-foreachloop.gif "Conteneur de boucles Foreach énumérant un dossier")</span><span class="sxs-lookup"><span data-stu-id="e5313-133">![A Foreach Loop container that enumerates a folder](../media/ssis-foreachloop.gif "A Foreach Loop container that enumerates a folder")</span></span>  
  
 <span data-ttu-id="e5313-134">Vous pouvez utiliser une combinaison de variables et d'expressions de propriété pour mettre à jour la propriété de l'objet de package avec la valeur de la collection de l'énumérateur.</span><span class="sxs-lookup"><span data-stu-id="e5313-134">You can use a combination of variables and property expressions to update the property of the package object with the enumerator collection value.</span></span> <span data-ttu-id="e5313-135">Vous mappez la valeur de la collection avec une variable définie par l'utilisateur, puis vous mettez en œuvre une expression de propriété sur la propriété qui utilise la variable.</span><span class="sxs-lookup"><span data-stu-id="e5313-135">First you map the collection value to a user-defined variable, and then you implement a property expression on the property that uses the variable.</span></span> <span data-ttu-id="e5313-136">Par exemple, la valeur de collection de l’énumérateur de fichier foreach est mappée à une variable appelée `MyFile` et la variable est ensuite utilisée dans l’expression de propriété pour la propriété Subject d’une tâche Envoyer un message.</span><span class="sxs-lookup"><span data-stu-id="e5313-136">For example, the collection value of the Foreach File enumerator is mapped to a variable called `MyFile` and the variable is then used in the property expression for the Subject property of a Send Mail task.</span></span> <span data-ttu-id="e5313-137">À l’exécution du package, la propriété Subject est mise à jour avec le nom d’un fichier à chaque répétition de la boucle.</span><span class="sxs-lookup"><span data-stu-id="e5313-137">When the package runs, the Subject property is updated with the name of a file each time that the loop repeats.</span></span> <span data-ttu-id="e5313-138">Pour plus d’informations, consultez [Expressions de propriété dans des packages](../expressions/use-property-expressions-in-packages.md).</span><span class="sxs-lookup"><span data-stu-id="e5313-138">For more information, see [Use Property Expressions in Packages](../expressions/use-property-expressions-in-packages.md).</span></span>  
  
 <span data-ttu-id="e5313-139">Vous pouvez également utiliser dans des expressions et des scripts les variables mappées à la valeur de la collection de l'énumérateur.</span><span class="sxs-lookup"><span data-stu-id="e5313-139">Variables that are mapped to the enumerator collection value can also be used in expressions and scripts.</span></span>  
  
 <span data-ttu-id="e5313-140">Un conteneur de boucles Foreach peut comprendre plusieurs tâches et conteneurs, mais il ne peut utiliser qu'un type d'énumérateur.</span><span class="sxs-lookup"><span data-stu-id="e5313-140">A Foreach Loop container can include multiple tasks and containers, but it can use only one type of enumerator.</span></span> <span data-ttu-id="e5313-141">Si le conteneur de boucles Foreach comprend plusieurs tâches, vous pouvez mapper la valeur de la collection de l'énumérateur avec plusieurs propriétés de chaque tâche.</span><span class="sxs-lookup"><span data-stu-id="e5313-141">If the Foreach Loop container includes multiple tasks, you can map the enumerator collection value to multiple properties of each task.</span></span>  
  
 <span data-ttu-id="e5313-142">Vous pouvez configurer un attribut de transaction sur le conteneur de boucles Foreach afin de définir une transaction pour un sous-ensemble du flux de contrôle du package.</span><span class="sxs-lookup"><span data-stu-id="e5313-142">You can set a transaction attribute on the Foreach Loop container to define a transaction for a subset of the package control flow.</span></span> <span data-ttu-id="e5313-143">Cela vous permet de gérer les transactions au niveau de la boucle Foreach plutôt qu'au niveau du package.</span><span class="sxs-lookup"><span data-stu-id="e5313-143">In this way, you can manage transactions at the level of the Foreach Loop instead of the package level.</span></span> <span data-ttu-id="e5313-144">Par exemple, si un conteneur de boucles Foreach répète un flux de contrôle qui met à jour des dimensions et des tables de faits dans un schéma en étoile, vous pouvez configurer une transaction de manière à ce que toutes les tables de faits soient correctement mises à jour ou à ce qu'aucune des tables ne soit actualisée.</span><span class="sxs-lookup"><span data-stu-id="e5313-144">For example, if a Foreach Loop container repeats a control flow that updates dimensions and fact tables in a star schema, you can configure a transaction to ensure that all fact tables are updated successfully, or none are updated.</span></span> <span data-ttu-id="e5313-145">Pour plus d’informations, consultez [Transactions Integration Services](../integration-services-transactions.md).</span><span class="sxs-lookup"><span data-stu-id="e5313-145">For more information, see [Integration Services Transactions](../integration-services-transactions.md).</span></span>  
  
## <a name="enumerator-types"></a><span data-ttu-id="e5313-146">Types d'énumérateur</span><span class="sxs-lookup"><span data-stu-id="e5313-146">Enumerator Types</span></span>  
 <span data-ttu-id="e5313-147">Vous pouvez configurer les énumérateurs en indiquant différentes informations pour chacun d'eux.</span><span class="sxs-lookup"><span data-stu-id="e5313-147">Enumerators are configurable, and you must provide different information, depending on the enumerator.</span></span>  
  
 <span data-ttu-id="e5313-148">Le tableau suivant récapitule les informations requises pour chaque type d'énumérateur.</span><span class="sxs-lookup"><span data-stu-id="e5313-148">The following table summarizes the information each enumerator type requires.</span></span>  
  
|<span data-ttu-id="e5313-149">Énumérateur</span><span class="sxs-lookup"><span data-stu-id="e5313-149">Enumerator</span></span>|<span data-ttu-id="e5313-150">Exigences de configuration</span><span class="sxs-lookup"><span data-stu-id="e5313-150">Configuration requirements</span></span>|  
|----------------|--------------------------------|  
|<span data-ttu-id="e5313-151">Foreach ADO</span><span class="sxs-lookup"><span data-stu-id="e5313-151">Foreach ADO</span></span>|<span data-ttu-id="e5313-152">Spécifiez la variable source de l'objet ADO et le mode de l'énumérateur.</span><span class="sxs-lookup"><span data-stu-id="e5313-152">Specify the ADO object source variable and the enumerator mode.</span></span> <span data-ttu-id="e5313-153">La variable doit être du type Object.</span><span class="sxs-lookup"><span data-stu-id="e5313-153">The variable must be of Object data type.</span></span>|  
|<span data-ttu-id="e5313-154">Foreach ADO.NET Schema Rowset</span><span class="sxs-lookup"><span data-stu-id="e5313-154">Foreach ADO.NET Schema Rowset</span></span>|<span data-ttu-id="e5313-155">Spécifiez la connexion à une base de données et le schéma à énumérer.</span><span class="sxs-lookup"><span data-stu-id="e5313-155">Specify the connection to a database and the schema to enumerate.</span></span>|  
|<span data-ttu-id="e5313-156">Fichier Foreach</span><span class="sxs-lookup"><span data-stu-id="e5313-156">Foreach File</span></span>|<span data-ttu-id="e5313-157">Spécifiez un dossier et les fichiers à énumérer, le format du nom des fichiers extraits, et indiquez si l'opération doit parcourir les sous-dossiers.</span><span class="sxs-lookup"><span data-stu-id="e5313-157">Specify a folder and the files to enumerate, the format of the file name of the retrieved files, and whether to traverse subfolders.</span></span>|  
|<span data-ttu-id="e5313-158">Foreach From Variable</span><span class="sxs-lookup"><span data-stu-id="e5313-158">Foreach From Variable</span></span>|<span data-ttu-id="e5313-159">Spécifiez la variable qui contient les objets à énumérer.</span><span class="sxs-lookup"><span data-stu-id="e5313-159">Specify the variable that contains the objects to enumerate.</span></span>|  
|<span data-ttu-id="e5313-160">Élément Foreach</span><span class="sxs-lookup"><span data-stu-id="e5313-160">Foreach Item</span></span>|<span data-ttu-id="e5313-161">Définissez les éléments de la collection d'éléments Foreach, notamment les colonnes et leur type de données.</span><span class="sxs-lookup"><span data-stu-id="e5313-161">Define the items in the Foreach Item collection, including columns and column data types.</span></span>|  
|<span data-ttu-id="e5313-162">Foreach NodeList</span><span class="sxs-lookup"><span data-stu-id="e5313-162">Foreach Nodelist</span></span>|<span data-ttu-id="e5313-163">Spécifiez la source du document XML et configurez l'opération XPath.</span><span class="sxs-lookup"><span data-stu-id="e5313-163">Specify the source of the XML document and configure the XPath operation.</span></span>|  
|<span data-ttu-id="e5313-164">Foreach SMO</span><span class="sxs-lookup"><span data-stu-id="e5313-164">Foreach SMO</span></span>|<span data-ttu-id="e5313-165">Spécifiez la connexion à une base de données et les objets SMO à énumérer.</span><span class="sxs-lookup"><span data-stu-id="e5313-165">Specify the connection to a database and the SMO objects to enumerate.</span></span>|  
|<span data-ttu-id="e5313-166">Objet blob Azure foreach</span><span class="sxs-lookup"><span data-stu-id="e5313-166">Foreach Azure Blob</span></span>|<span data-ttu-id="e5313-167">Spécifiez le conteneur d’objets BLOB Azure qui contient les objets BLOB à énumérer.</span><span class="sxs-lookup"><span data-stu-id="e5313-167">Specify the Azure blob container that contains blobs to be enumerated.</span></span>|  
|<span data-ttu-id="e5313-168">Foreach ADLS File</span><span class="sxs-lookup"><span data-stu-id="e5313-168">Foreach ADLS File</span></span>|<span data-ttu-id="e5313-169">Spécifiez le répertoire ADLS qui contient les fichiers à énumérer, ainsi que certains filtres.</span><span class="sxs-lookup"><span data-stu-id="e5313-169">Specify the ADLS directory that contains files to be enumerated, along with some filters.</span></span>|
  
## <a name="property-expressions-in-foreach-loop-containers"></a><span data-ttu-id="e5313-170">Expressions de propriété dans des conteneurs de boucles Foreach</span><span class="sxs-lookup"><span data-stu-id="e5313-170">Property Expressions in Foreach Loop Containers</span></span>  
 <span data-ttu-id="e5313-171">Les packages peuvent être configurés pour exécuter simultanément plusieurs exécutables.</span><span class="sxs-lookup"><span data-stu-id="e5313-171">Packages can be configured to concurrently run multiple executables.</span></span> <span data-ttu-id="e5313-172">Cette configuration doit être utilisée avec précaution lorsque le package inclut un conteneur de boucles Foreach qui implémente des expressions de propriété.</span><span class="sxs-lookup"><span data-stu-id="e5313-172">This configuration should be used with caution when the package includes a Foreach Loop container that implements property expressions.</span></span>  
  
 <span data-ttu-id="e5313-173">Il est souvent pratique d’implémenter une expression de propriété pour définir la valeur de la propriété ConnectionString des gestionnaires de connexions que les énumérateurs de boucles Foreach utilisent.</span><span class="sxs-lookup"><span data-stu-id="e5313-173">It is often useful to implement a property expression to set the value of the ConnectionString property of the connection managers that the Foreach Loop enumerators use.</span></span> <span data-ttu-id="e5313-174">L’expression de la propriété ConnectionString est définie par une variable qui est mappée à la valeur de la collection de l’énumérateur et mise à jour à chaque itération de la boucle.</span><span class="sxs-lookup"><span data-stu-id="e5313-174">The property expression of ConnectionString is set by a variable that maps to the collection value of the enumerator and is updated at each iteration of the loop.</span></span>  
  
 <span data-ttu-id="e5313-175">Pour éviter les conséquences négatives d'une synchronisation non déterminante d'une exécution parallèle de tâches dans la boucle, le package doit être configuré pour exécuter un seul exécutable à la fois.</span><span class="sxs-lookup"><span data-stu-id="e5313-175">To avoid negative consequences of nondeterminative timing of parallel execution of tasks in the loop, the package should be configured to run only one executable at a time.</span></span> <span data-ttu-id="e5313-176">Par exemple, si un package peut exécuter plusieurs tâches simultanément, un conteneur de boucles Foreach qui énumère les fichiers dans le dossier, récupère les noms de fichiers, puis utilise une tâche d'exécution SQL pour insérer les noms de fichiers dans une table peut provoquer des conflits d'écriture lorsque deux instances de la tâche d'exécution SQL tentent d'écrire simultanément.</span><span class="sxs-lookup"><span data-stu-id="e5313-176">For example, if a package can run multiple tasks concurrently, a Foreach Loop container that enumerates files in the folder, retrieves the file names, and then uses an Execute SQL task to insert the file names into a table may incur write conflicts when two instances of the Execute SQL task attempt to write at the same time.</span></span> <span data-ttu-id="e5313-177">Pour plus d’informations, consultez [Expressions de propriété dans des packages](../expressions/use-property-expressions-in-packages.md).</span><span class="sxs-lookup"><span data-stu-id="e5313-177">For more information, see [Use Property Expressions in Packages](../expressions/use-property-expressions-in-packages.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="e5313-178">Tâches associées</span><span class="sxs-lookup"><span data-stu-id="e5313-178">Related Tasks</span></span>  
 <span data-ttu-id="e5313-179">Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programmation.</span><span class="sxs-lookup"><span data-stu-id="e5313-179">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="e5313-180">Pour plus d'informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , cliquez sur l'une des rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="e5313-180">For details about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="e5313-181">Configurer un conteneur de boucles Foreach</span><span class="sxs-lookup"><span data-stu-id="e5313-181">Configure a Foreach Loop Container</span></span>](foreach-loop-container.md)  
  
-   [<span data-ttu-id="e5313-182">Définir les propriétés d'une tâche ou d'un conteneur</span><span class="sxs-lookup"><span data-stu-id="e5313-182">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
 <span data-ttu-id="e5313-183">Pour plus d'informations sur la définition par programmation de ces propriétés, cliquez sur la rubrique suivante :</span><span class="sxs-lookup"><span data-stu-id="e5313-183">For details about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop>  
  
## <a name="related-content"></a><span data-ttu-id="e5313-184">Contenu associé</span><span class="sxs-lookup"><span data-stu-id="e5313-184">Related Content</span></span>  
 <span data-ttu-id="e5313-185">Entrée de blog, [SSIS For Each Node List Enumerator](https://go.microsoft.com/fwlink/?LinkId=220671), sur bidn.com.</span><span class="sxs-lookup"><span data-stu-id="e5313-185">Blog entry, [SSIS For Each Node List Enumerator](https://go.microsoft.com/fwlink/?LinkId=220671), on bidn.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5313-186">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5313-186">See Also</span></span>  
 <span data-ttu-id="e5313-187">[Flux de contrôle](control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="e5313-187">[Control Flow](control-flow.md) </span></span>  
 [<span data-ttu-id="e5313-188">Conteneurs Integration Services</span><span class="sxs-lookup"><span data-stu-id="e5313-188">Integration Services Containers</span></span>](integration-services-containers.md)  
  
  