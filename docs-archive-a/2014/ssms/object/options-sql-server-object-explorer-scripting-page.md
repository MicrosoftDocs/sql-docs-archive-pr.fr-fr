---
title: Options (Explorateur d’objets SQL Server-page scripts) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.ObjectExplorerScripting
- VS.ToolsOptionsPages.Sql_Server_Object_Explorer.ObjectExplorerScripting
ms.assetid: 6105aec9-1b72-4cb2-bd24-fc35f6d95240
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9966db2e5b08cd16976e2c16434cec0adca8445f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87695223"
---
# <a name="options-sql-server-object-explorer-scripting-page"></a><span data-ttu-id="691af-102">Options (Explorateur d’objets SQL Server-page script)</span><span class="sxs-lookup"><span data-stu-id="691af-102">Options (SQL Server Object Explorer-Scripting Page)</span></span>
  <span data-ttu-id="691af-103">Utilisez cette page pour définir les options de script qui s’appliquent aux commandes suivantes dans les menus contextuels d’objet de **l’Explorateur d’objets**:</span><span class="sxs-lookup"><span data-stu-id="691af-103">Use this page to set scripting options that apply to the following commands on object context menus in **Object Explorer**:</span></span>  
  
-   <span data-ttu-id="691af-104">Commandes **Edition** pour les vues et tables utilisateur.</span><span class="sxs-lookup"><span data-stu-id="691af-104">**Edit** commands for user tables and views.</span></span>  
  
-   <span data-ttu-id="691af-105">Commandes **Script \<object> en tant que** pour les objets créés par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="691af-105">**Script \<object> as** commands for user-created objects.</span></span>  
  
-   <span data-ttu-id="691af-106">Commandes **Modifier** pour les objets créés par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="691af-106">**Modify** command for user-created objects.</span></span>  
  
-   <span data-ttu-id="691af-107">Cette page définit également les valeurs par défaut des options de script de **l’Assistant Génération de scripts SQL Server**.</span><span class="sxs-lookup"><span data-stu-id="691af-107">This page also sets the scripting option defaults for the **Generate SQL Server Script Wizard**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="691af-108">Notes</span><span class="sxs-lookup"><span data-stu-id="691af-108">Remarks</span></span>  
 <span data-ttu-id="691af-109">Les commandes **Edition** et **Modifier** et peuvent produire des résultats qui sont différents de ceux de la commande **Script \<object> en tant** que pour le même paramètre d’option.</span><span class="sxs-lookup"><span data-stu-id="691af-109">The **Edit** and **Modify** commands might produce results that are different from the **Script \<object> as** command for the same option setting.</span></span> <span data-ttu-id="691af-110">Les commandes **Edition** et **Modifier** sont conçues pour modifier des objets de la base de données active durant une session de l’Éditeur de requête.</span><span class="sxs-lookup"><span data-stu-id="691af-110">The **Edit** and **Modify** commands are designed to modify objects in the current database during a Query Editor session.</span></span> <span data-ttu-id="691af-111">La commande **Script \<object> en tant que** est conçue pour générer un script pour qu’il puisse être utilisé ultérieurement pour créer des objets.</span><span class="sxs-lookup"><span data-stu-id="691af-111">The **Script \<object> as** command is designed to generate a script so that it can be used later to create objects.</span></span>  
  
## <a name="options"></a><span data-ttu-id="691af-112">Options</span><span class="sxs-lookup"><span data-stu-id="691af-112">Options</span></span>  
 <span data-ttu-id="691af-113">Spécifiez les options de script en les sélectionnant parmi les paramètres disponibles dans la liste située à droite de chaque option.</span><span class="sxs-lookup"><span data-stu-id="691af-113">Specify scripting options by selecting from the available settings in the list to the right of each option.</span></span>  
  
### <a name="general-scripting-options"></a><span data-ttu-id="691af-114">Options de script générales</span><span class="sxs-lookup"><span data-stu-id="691af-114">General Scripting Options</span></span>  
 <span data-ttu-id="691af-115">**Délimiter des instructions individuelles**</span><span class="sxs-lookup"><span data-stu-id="691af-115">**Delimit individual statements**</span></span>  
 <span data-ttu-id="691af-116">Sépare les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] par un délimiteur de traitement.</span><span class="sxs-lookup"><span data-stu-id="691af-116">Separates individual [!INCLUDE[tsql](../../includes/tsql-md.md)] statements by using a batch separator.</span></span> <span data-ttu-id="691af-117">Pour modifier le délimiteur de traitement par défaut de **l’Éditeur de requête**, sélectionnez **Outils**/**Options**/**Exécution de la requête**/**SQL Server**/**Général**/**Délimiteur de traitement**.</span><span class="sxs-lookup"><span data-stu-id="691af-117">To change the default batch separator for **Query Editor**, select **Tools**/**Options**/**Query Execution**/**SQL Server**/**General**/**Batch separator**.</span></span> <span data-ttu-id="691af-118">La valeur par défaut est FALSE.</span><span class="sxs-lookup"><span data-stu-id="691af-118">Default is False.</span></span> <span data-ttu-id="691af-119">Pour plus d’informations, consultez [GO &#40;&#41;Transact-SQL ](/sql/t-sql/language-elements/sql-server-utilities-statements-go).</span><span class="sxs-lookup"><span data-stu-id="691af-119">For more information, see [GO &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/sql-server-utilities-statements-go).</span></span>  
  
 <span data-ttu-id="691af-120">**Inclure des en-têtes descriptifs**</span><span class="sxs-lookup"><span data-stu-id="691af-120">**Include descriptive headers**</span></span>  
 <span data-ttu-id="691af-121">Ajoute des commentaires descriptifs au script en séparant le script en sections pour chaque objet.</span><span class="sxs-lookup"><span data-stu-id="691af-121">Adds descriptive comments to the script by separating the script into sections for each object.</span></span> <span data-ttu-id="691af-122">La valeur par défaut est True.</span><span class="sxs-lookup"><span data-stu-id="691af-122">Default is True.</span></span> <span data-ttu-id="691af-123">Pour plus d’informations, consultez [Comment &#40;&#41;Transact-SQL ](/sql/t-sql/language-elements/comment-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="691af-123">For more information, see [Comment &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/comment-transact-sql).</span></span>  
  
 <span data-ttu-id="691af-124">**Inclure des options VarDecimal**</span><span class="sxs-lookup"><span data-stu-id="691af-124">**Include vardecimal options**</span></span>  
 <span data-ttu-id="691af-125">Inclut les options de stockage VarDecimal.</span><span class="sxs-lookup"><span data-stu-id="691af-125">Includes the vardecimal storage options.</span></span> <span data-ttu-id="691af-126">La valeur par défaut est FALSE.</span><span class="sxs-lookup"><span data-stu-id="691af-126">Default is False.</span></span> <span data-ttu-id="691af-127">Pour plus d’informations, consultez et [sp_db_vardecimal_storage_format &#40;&#41;Transact-SQL ](/sql/relational-databases/system-stored-procedures/sp-db-vardecimal-storage-format-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="691af-127">For more information, see and [sp_db_vardecimal_storage_format &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-db-vardecimal-storage-format-transact-sql).</span></span>  
  
 <span data-ttu-id="691af-128">**Générer le script de suivi des modifications**</span><span class="sxs-lookup"><span data-stu-id="691af-128">**Script change tracking**</span></span>  
 <span data-ttu-id="691af-129">Inclut des informations de suivi des modifications dans le script.</span><span class="sxs-lookup"><span data-stu-id="691af-129">Includes change tracking information in the script.</span></span>  
  
 <span data-ttu-id="691af-130">**Générer un script pour la version du serveur**</span><span class="sxs-lookup"><span data-stu-id="691af-130">**Script for server version**</span></span>  
 <span data-ttu-id="691af-131">Crée un script qui peut être exécuté sur la version sélectionnée de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="691af-131">Creates a script that can be run on the selected version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="691af-132">Les fonctionnalités qui sont des nouveautés de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] ne peuvent pas faire l'objet d'un script pour les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="691af-132">Features that are new in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] cannot be scripted for earlier versions.</span></span> <span data-ttu-id="691af-133">Certains scripts qui sont créés pour [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] ne peuvent pas être exécutés sur les serveurs exécutant une version antérieure de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ou sur une base de données qui possède un [paramètre de niveau de compatibilité de base de données](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)antérieur.</span><span class="sxs-lookup"><span data-stu-id="691af-133">Some scripts that are created for [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] cannot be executed on servers that are running on an earlier version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], or on a database that has an earlier [database compatibility level setting](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).</span></span>  
  
 <span data-ttu-id="691af-134">**Générer un script pour les catalogues de texte intégral**</span><span class="sxs-lookup"><span data-stu-id="691af-134">**Script full-text catalogs**</span></span>  
 <span data-ttu-id="691af-135">Inclut un script pour les catalogues de texte intégral.</span><span class="sxs-lookup"><span data-stu-id="691af-135">Includes a script for full-text catalogs.</span></span> <span data-ttu-id="691af-136">La valeur par défaut est FALSE.</span><span class="sxs-lookup"><span data-stu-id="691af-136">Default is False.</span></span> <span data-ttu-id="691af-137">Pour plus d’informations, consultez [CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-catalog-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="691af-137">For more information, see [CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-catalog-transact-sql).</span></span>  
  
 <span data-ttu-id="691af-138">**UTILISER le script\<database>**</span><span class="sxs-lookup"><span data-stu-id="691af-138">**Script USE \<database>**</span></span>  
 <span data-ttu-id="691af-139">Ajoute l’instruction USE DATABASE au script pour créer des objets de base de données dans le contexte de la base de données de **l’Explorateur d’objets** active.</span><span class="sxs-lookup"><span data-stu-id="691af-139">Adds the USE DATABASE statement to the script to create database objects in the context of the current **Object Explorer** database.</span></span> <span data-ttu-id="691af-140">Lorsqu'il est prévu que le script sera utilisé dans une base de données différente, sélectionnez False afin d'omettre l'instruction.</span><span class="sxs-lookup"><span data-stu-id="691af-140">When the script is expected for use in a different database, select False to omit.</span></span> <span data-ttu-id="691af-141">La valeur par défaut est True.</span><span class="sxs-lookup"><span data-stu-id="691af-141">Default is True.</span></span> <span data-ttu-id="691af-142">Pour plus d’informations, consultez [USE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/use-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="691af-142">For more information, see [USE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/use-transact-sql).</span></span>  
  
### <a name="object-scripting-options"></a><span data-ttu-id="691af-143">Options de scripts d'objets</span><span class="sxs-lookup"><span data-stu-id="691af-143">Object Scripting Options</span></span>  
 <span data-ttu-id="691af-144">**Générer un script pour les objets dépendants**</span><span class="sxs-lookup"><span data-stu-id="691af-144">**Generate script for dependent objects**</span></span>  
 <span data-ttu-id="691af-145">Génère un script pour les objets supplémentaires qui sont requis lorsque le script de l'objet sélectionné est exécuté.</span><span class="sxs-lookup"><span data-stu-id="691af-145">Generates a script for additional objects that are required when the script for the selected object is executed.</span></span> <span data-ttu-id="691af-146">La valeur par défaut est FALSE.</span><span class="sxs-lookup"><span data-stu-id="691af-146">Default is False.</span></span>  
  
 <span data-ttu-id="691af-147">**Inclure la clause If NOT EXISTS**</span><span class="sxs-lookup"><span data-stu-id="691af-147">**Include If NOT EXISTS clause**</span></span>  
 <span data-ttu-id="691af-148">Inclut une instruction permettant de vérifier qu'un objet n'existe pas dans la base de données avant de créer l'objet.</span><span class="sxs-lookup"><span data-stu-id="691af-148">Includes a statement to check that each object does not exist in the database before trying to create the object.</span></span> <span data-ttu-id="691af-149">La valeur par défaut est FALSE.</span><span class="sxs-lookup"><span data-stu-id="691af-149">Default is False.</span></span> <span data-ttu-id="691af-150">Pour plus d’informations, consultez [If... SINON &#40;&#41;Transact-SQL](/sql/t-sql/language-elements/if-else-transact-sql) et [existe &#40;&#41;Transact-SQL ](/sql/t-sql/language-elements/exists-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="691af-150">For more information, see [IF...ELSE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/if-else-transact-sql) and [EXISTS &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/exists-transact-sql).</span></span>  
  
 <span data-ttu-id="691af-151">**Noms d'objet de qualification de schéma**</span><span class="sxs-lookup"><span data-stu-id="691af-151">**Schema qualify object names**</span></span>  
 <span data-ttu-id="691af-152">Qualifie les noms d'objets avec le schéma de l'objet.</span><span class="sxs-lookup"><span data-stu-id="691af-152">Qualifies object names with the object schema.</span></span> <span data-ttu-id="691af-153">La valeur par défaut est FALSE.</span><span class="sxs-lookup"><span data-stu-id="691af-153">Default is False.</span></span> <span data-ttu-id="691af-154">Pour plus d’informations, consultez [Créer un schéma de base de données](../../relational-databases/security/authentication-access/create-a-database-schema.md).</span><span class="sxs-lookup"><span data-stu-id="691af-154">For more information, see [Create a Database Schema](../../relational-databases/security/authentication-access/create-a-database-schema.md).</span></span>  
  
 <span data-ttu-id="691af-155">**Générer un script pour les propriétés étendues**</span><span class="sxs-lookup"><span data-stu-id="691af-155">**Script extended properties**</span></span>  
 <span data-ttu-id="691af-156">Inclut les propriétés étendues dans le script, si l'objet en possède.</span><span class="sxs-lookup"><span data-stu-id="691af-156">Includes extended properties in the script if the object has extended properties.</span></span> <span data-ttu-id="691af-157">La valeur par défaut est FALSE.</span><span class="sxs-lookup"><span data-stu-id="691af-157">Default is False.</span></span> <span data-ttu-id="691af-158">Pour plus d’informations, consultez [sp_addextendedproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproperty-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="691af-158">For more information, see [sp_addextendedproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproperty-transact-sql).</span></span>  
  
 <span data-ttu-id="691af-159">**Propriétaire de script**</span><span class="sxs-lookup"><span data-stu-id="691af-159">**Script owner**</span></span>  
 <span data-ttu-id="691af-160">Inclut le propriétaire dans le script généré.</span><span class="sxs-lookup"><span data-stu-id="691af-160">Includes the owner in the generated script.</span></span> <span data-ttu-id="691af-161">La valeur par défaut est FALSE.</span><span class="sxs-lookup"><span data-stu-id="691af-161">Default is False.</span></span>  
  
 <span data-ttu-id="691af-162">**Générer un script pour les autorisations**</span><span class="sxs-lookup"><span data-stu-id="691af-162">**Script permissions**</span></span>  
 <span data-ttu-id="691af-163">Inclut les autorisations sur les objets de base de données dans le script.</span><span class="sxs-lookup"><span data-stu-id="691af-163">Includes permissions on database objects in the script.</span></span> <span data-ttu-id="691af-164">La valeur par défaut est True.</span><span class="sxs-lookup"><span data-stu-id="691af-164">Default is True.</span></span> <span data-ttu-id="691af-165">Pour plus d’informations, consultez [autorisations &#40;Moteur de base de données&#41;](../../relational-databases/security/permissions-database-engine.md).</span><span class="sxs-lookup"><span data-stu-id="691af-165">For more information, see [Permissions &#40;Database Engine&#41;](../../relational-databases/security/permissions-database-engine.md).</span></span>  
  
### <a name="tableview-options"></a><span data-ttu-id="691af-166">Options de table/vue</span><span class="sxs-lookup"><span data-stu-id="691af-166">Table/View Options</span></span>  
 <span data-ttu-id="691af-167">Les options suivantes s'appliquent uniquement aux scripts des tables et des vues.</span><span class="sxs-lookup"><span data-stu-id="691af-167">The following options apply only to scripts for tables or views.</span></span>  
  
 <span data-ttu-id="691af-168">**Convertir les types de données définis par l'utilisateur en types de base**</span><span class="sxs-lookup"><span data-stu-id="691af-168">**Convert user-defined data types to base types**</span></span>  
 <span data-ttu-id="691af-169">Convertit les types de données définis par l'utilisateur en types de base à partir desquels ils ont été créés.</span><span class="sxs-lookup"><span data-stu-id="691af-169">Converts user-defined data types to the base types from which they were created.</span></span> <span data-ttu-id="691af-170">Utilisez True lorsque les types de données définis par l'utilisateur de la base de données source n'existent pas dans la base de données où le script sera exécuté.</span><span class="sxs-lookup"><span data-stu-id="691af-170">Use True when the source database user-defined data types do not exist in the database where the script will be run.</span></span> <span data-ttu-id="691af-171">Utilisez False pour conserver les types de données définis par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="691af-171">Use False to keep the user-defined data types.</span></span> <span data-ttu-id="691af-172">La valeur par défaut est FALSE.</span><span class="sxs-lookup"><span data-stu-id="691af-172">Default is False.</span></span> <span data-ttu-id="691af-173">Pour plus d’informations, consultez [CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="691af-173">For more information, see [CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql).</span></span>  
  
 <span data-ttu-id="691af-174">**Générer des commandes SET ANSI PADDING**</span><span class="sxs-lookup"><span data-stu-id="691af-174">**Generate SET ANSI PADDING commands**</span></span>  
 <span data-ttu-id="691af-175">Ajoute l'instruction SET ANSI_PADDING avant et après chaque instruction CREATE TABLE.</span><span class="sxs-lookup"><span data-stu-id="691af-175">Adds the SET ANSI_PADDING statement before and after each CREATE TABLE statement.</span></span> <span data-ttu-id="691af-176">La valeur par défaut est True.</span><span class="sxs-lookup"><span data-stu-id="691af-176">Default is True.</span></span> <span data-ttu-id="691af-177">Pour plus d’informations, consultez [SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="691af-177">For more information, see [SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql).</span></span>  
  
 <span data-ttu-id="691af-178">**Inclure un classement**</span><span class="sxs-lookup"><span data-stu-id="691af-178">**Include collation**</span></span>  
 <span data-ttu-id="691af-179">Inclut un classement dans la définition de colonne.</span><span class="sxs-lookup"><span data-stu-id="691af-179">Includes collation in column definition.</span></span> <span data-ttu-id="691af-180">La valeur par défaut est True.</span><span class="sxs-lookup"><span data-stu-id="691af-180">Default is True.</span></span> <span data-ttu-id="691af-181">Pour plus d’informations, consultez [Prise en charge d’Unicode et du classement](../../relational-databases/collations/collation-and-unicode-support.md).</span><span class="sxs-lookup"><span data-stu-id="691af-181">For more information, see [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).</span></span>  
  
 <span data-ttu-id="691af-182">**Inclure la propriété IDENTITY**</span><span class="sxs-lookup"><span data-stu-id="691af-182">**Include IDENTITY property**</span></span>  
 <span data-ttu-id="691af-183">Inclut des définitions pour la valeur de départ IDENTITY et l'incrément IDENTITY.</span><span class="sxs-lookup"><span data-stu-id="691af-183">Includes definitions for IDENTITY seed and IDENTITY increment.</span></span> <span data-ttu-id="691af-184">La valeur par défaut est True.</span><span class="sxs-lookup"><span data-stu-id="691af-184">Default is True.</span></span> <span data-ttu-id="691af-185">Pour plus d’informations, consultez [IDENTITY &#40;propriété&#41; &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql-identity-property).</span><span class="sxs-lookup"><span data-stu-id="691af-185">For more information, see [IDENTITY &#40;Property&#41; &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql-identity-property).</span></span>  
  
 <span data-ttu-id="691af-186">**Références aux clés étrangères de qualification de schéma**</span><span class="sxs-lookup"><span data-stu-id="691af-186">**Schema qualify foreign key references**</span></span>  
 <span data-ttu-id="691af-187">Ajoute le nom de schéma aux références de table des contraintes FOREIGN KEY.</span><span class="sxs-lookup"><span data-stu-id="691af-187">Adds the schema name to table references for FOREIGN KEY constraints.</span></span> <span data-ttu-id="691af-188">La valeur par défaut est True.</span><span class="sxs-lookup"><span data-stu-id="691af-188">Default is True.</span></span>  
  
 <span data-ttu-id="691af-189">**Valeurs par défaut et règles liées aux scripts**</span><span class="sxs-lookup"><span data-stu-id="691af-189">**Script bound defaults and rules**</span></span>  
 <span data-ttu-id="691af-190">Inclut les appels aux procédures stockées liées **sp_bindefault** et **sp_bindrule** .</span><span class="sxs-lookup"><span data-stu-id="691af-190">Includes the **sp_bindefault** and **sp_bindrule** binding stored procedure calls.</span></span> <span data-ttu-id="691af-191">La valeur par défaut est True.</span><span class="sxs-lookup"><span data-stu-id="691af-191">Default is True.</span></span> <span data-ttu-id="691af-192">Pour plus d’informations, consultez [sp_bindefault &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-bindefault-transact-sql) et [sp_bindrule &#40;transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-bindrule-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="691af-192">For more information, see [sp_bindefault &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-bindefault-transact-sql) and [sp_bindrule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-bindrule-transact-sql).</span></span>  
  
 <span data-ttu-id="691af-193">**Générer un script pour les contraintes CHECK**</span><span class="sxs-lookup"><span data-stu-id="691af-193">**Script CHECK constraints**</span></span>  
 <span data-ttu-id="691af-194">Ajoute des [contraintes CHECK](../../relational-databases/tables/unique-constraints-and-check-constraints.md) au script.</span><span class="sxs-lookup"><span data-stu-id="691af-194">Adds [CHECK constraints](../../relational-databases/tables/unique-constraints-and-check-constraints.md) to the script.</span></span> <span data-ttu-id="691af-195">La valeur par défaut est True.</span><span class="sxs-lookup"><span data-stu-id="691af-195">Default is True.</span></span>  
  
 <span data-ttu-id="691af-196">**Valeurs de script par défaut**</span><span class="sxs-lookup"><span data-stu-id="691af-196">**Script defaults**</span></span>  
 <span data-ttu-id="691af-197">Inclut les valeurs de colonne par défaut dans le script.</span><span class="sxs-lookup"><span data-stu-id="691af-197">Includes column default values in the script.</span></span> <span data-ttu-id="691af-198">La valeur par défaut est FALSE.</span><span class="sxs-lookup"><span data-stu-id="691af-198">Default is False.</span></span> <span data-ttu-id="691af-199">Pour plus d’informations, consultez [CREATE DEFAULT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-default-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="691af-199">For more information, see [CREATE DEFAULT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-default-transact-sql).</span></span>  
  
 <span data-ttu-id="691af-200">**Générer un script pour les groupes de fichiers**</span><span class="sxs-lookup"><span data-stu-id="691af-200">**Script file groups**</span></span>  
 <span data-ttu-id="691af-201">Spécifie le groupe de fichiers dans la clause ON pour des définitions de table.</span><span class="sxs-lookup"><span data-stu-id="691af-201">Specifies the filegroup in the ON clause for table definitions.</span></span> <span data-ttu-id="691af-202">La valeur par défaut est FALSE.</span><span class="sxs-lookup"><span data-stu-id="691af-202">Default is False.</span></span> <span data-ttu-id="691af-203">Pour plus d’informations, consultez [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="691af-203">For more information, see [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql).</span></span>  
  
 <span data-ttu-id="691af-204">**Générer un script pour les clés étrangères**</span><span class="sxs-lookup"><span data-stu-id="691af-204">**Script foreign keys**</span></span>  
 <span data-ttu-id="691af-205">Inclut des [contraintes FOREIGN KEY](../../relational-databases/tables/primary-and-foreign-key-constraints.md) dans le script.</span><span class="sxs-lookup"><span data-stu-id="691af-205">Includes [FOREIGN KEY constraints](../../relational-databases/tables/primary-and-foreign-key-constraints.md) in the script.</span></span> <span data-ttu-id="691af-206">La valeur par défaut est FALSE.</span><span class="sxs-lookup"><span data-stu-id="691af-206">Default is False.</span></span>  
  
 <span data-ttu-id="691af-207">**Générer un script pour les index de recherche en texte intégral**</span><span class="sxs-lookup"><span data-stu-id="691af-207">**Script full-text indexes**</span></span>  
 <span data-ttu-id="691af-208">Inclut les index de recherche en texte intégral dans le script.</span><span class="sxs-lookup"><span data-stu-id="691af-208">Includes full-text indexes in the script.</span></span> <span data-ttu-id="691af-209">La valeur par défaut est FALSE.</span><span class="sxs-lookup"><span data-stu-id="691af-209">Default is False.</span></span> <span data-ttu-id="691af-210">Pour plus d’informations, consultez [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="691af-210">For more information, see [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql).</span></span>  
  
 <span data-ttu-id="691af-211">**Générer un script pour les index**</span><span class="sxs-lookup"><span data-stu-id="691af-211">**Script indexes**</span></span>  
 <span data-ttu-id="691af-212">Inclut des index cluster, non cluster et XML dans le script.</span><span class="sxs-lookup"><span data-stu-id="691af-212">Includes clustered, nonclustered, and XML indexes in the script.</span></span> <span data-ttu-id="691af-213">La valeur par défaut est True.</span><span class="sxs-lookup"><span data-stu-id="691af-213">Default is True.</span></span> <span data-ttu-id="691af-214">Pour plus d’informations, consultez [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="691af-214">For more information, see [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
 <span data-ttu-id="691af-215">**Générer un script pour les schémas de partition**</span><span class="sxs-lookup"><span data-stu-id="691af-215">**Script partition schemes**</span></span>  
 <span data-ttu-id="691af-216">Inclut des schémas de partition de table dans le script.</span><span class="sxs-lookup"><span data-stu-id="691af-216">Includes table partitioning schemes in the script.</span></span> <span data-ttu-id="691af-217">La valeur par défaut est FALSE.</span><span class="sxs-lookup"><span data-stu-id="691af-217">Default is False.</span></span> <span data-ttu-id="691af-218">Pour plus d’informations, consultez [Create partition scheme &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-partition-scheme-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="691af-218">For more information, see [CREATE PARTITION SCHEME &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-partition-scheme-transact-sql).</span></span>  
  
 <span data-ttu-id="691af-219">**Générer un script pour les clés primaires**</span><span class="sxs-lookup"><span data-stu-id="691af-219">**Script primary keys**</span></span>  
 <span data-ttu-id="691af-220">Inclut des [contraintes de clé primaire et de clé étrangère](../../relational-databases/tables/primary-and-foreign-key-constraints.md) dans le script.</span><span class="sxs-lookup"><span data-stu-id="691af-220">Includes [Primary and Foreign Key Constraints](../../relational-databases/tables/primary-and-foreign-key-constraints.md) in the script.</span></span> <span data-ttu-id="691af-221">La valeur par défaut est True.</span><span class="sxs-lookup"><span data-stu-id="691af-221">Default is True.</span></span>  
  
 <span data-ttu-id="691af-222">**Générer un script pour les statistiques**</span><span class="sxs-lookup"><span data-stu-id="691af-222">**Script statistics**</span></span>  
 <span data-ttu-id="691af-223">Inclut des statistiques définies par l'utilisateur dans le script.</span><span class="sxs-lookup"><span data-stu-id="691af-223">Includes user-defined statistics in the script.</span></span> <span data-ttu-id="691af-224">La valeur par défaut est FALSE.</span><span class="sxs-lookup"><span data-stu-id="691af-224">Default is False.</span></span> <span data-ttu-id="691af-225">Pour plus d’informations, consultez [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="691af-225">For more information, see [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql).</span></span>  
  
 <span data-ttu-id="691af-226">**Générer un script pour les déclencheurs**</span><span class="sxs-lookup"><span data-stu-id="691af-226">**Script triggers**</span></span>  
 <span data-ttu-id="691af-227">Inclut des déclencheurs dans le script.</span><span class="sxs-lookup"><span data-stu-id="691af-227">Include triggers in the script.</span></span> <span data-ttu-id="691af-228">La valeur par défaut est FALSE.</span><span class="sxs-lookup"><span data-stu-id="691af-228">Default is False.</span></span> <span data-ttu-id="691af-229">Pour plus d’informations, consultez [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="691af-229">For more information, see [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql).</span></span>  
  
 <span data-ttu-id="691af-230">**Générer un script pour les clés uniques**</span><span class="sxs-lookup"><span data-stu-id="691af-230">**Script unique keys**</span></span>  
 <span data-ttu-id="691af-231">Inclut des [contraintes uniques et des contraintes de validation](../../relational-databases/tables/unique-constraints-and-check-constraints.md) dans le script.</span><span class="sxs-lookup"><span data-stu-id="691af-231">Includes [Unique Constraints and Check Constraints](../../relational-databases/tables/unique-constraints-and-check-constraints.md) in the script.</span></span> <span data-ttu-id="691af-232">La valeur par défaut est FALSE.</span><span class="sxs-lookup"><span data-stu-id="691af-232">Default is False.</span></span>  
  
 <span data-ttu-id="691af-233">**Générer un script pour les colonnes de vue**</span><span class="sxs-lookup"><span data-stu-id="691af-233">**Script view columns**</span></span>  
 <span data-ttu-id="691af-234">Déclare des colonnes de vue dans les en-têtes de vue.</span><span class="sxs-lookup"><span data-stu-id="691af-234">Declares view columns in view headers.</span></span> <span data-ttu-id="691af-235">La valeur par défaut est FALSE.</span><span class="sxs-lookup"><span data-stu-id="691af-235">Default is False.</span></span> <span data-ttu-id="691af-236">Pour plus d’informations, consultez [CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="691af-236">For more information, see [CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql).</span></span>  
  
 <span data-ttu-id="691af-237">**ScriptDriIncludeSystemNames**</span><span class="sxs-lookup"><span data-stu-id="691af-237">**ScriptDriIncludeSystemNames**</span></span>  
 <span data-ttu-id="691af-238">Inclut les noms de contraintes générés par le système pour appliquer l'intégrité référentielle déclarative.</span><span class="sxs-lookup"><span data-stu-id="691af-238">Includes system generated constraint names to enforce declarative referential integrity.</span></span> <span data-ttu-id="691af-239">La valeur par défaut est FALSE.</span><span class="sxs-lookup"><span data-stu-id="691af-239">Default is False.</span></span> <span data-ttu-id="691af-240">Pour plus d’informations, consultez [REFERENTIAL_CONSTRAINTS &#40;Transact-SQL&#41;](/sql/relational-databases/system-information-schema-views/referential-constraints-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="691af-240">For more information, see [REFERENTIAL_CONSTRAINTS &#40;Transact-SQL&#41;](/sql/relational-databases/system-information-schema-views/referential-constraints-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="691af-241">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="691af-241">See Also</span></span>  
 [<span data-ttu-id="691af-242">Générer des scripts &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="691af-242">Generate Scripts &#40;SQL Server Management Studio&#41;</span></span>](../../relational-databases/scripting/generate-scripts-sql-server-management-studio.md)  
  
  