---
title: Implémentation d’assemblys | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration], implementing
ms.assetid: c228d7bf-a906-4f37-a057-5d464d962ff8
author: rothja
ms.author: jroth
ms.openlocfilehash: 3cb3818ed644eede3cf4f2c256a0dcb94ec58c3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704183"
---
# <a name="implementing-assemblies"></a><span data-ttu-id="b7754-102">Implémentation d'assemblys</span><span class="sxs-lookup"><span data-stu-id="b7754-102">Implementing Assemblies</span></span>
  <span data-ttu-id="b7754-103">Cette rubrique fournit des informations sur les concepts suivants, afin de vous aider à implémenter et à utiliser les assemblys dans vos bases de données :</span><span class="sxs-lookup"><span data-stu-id="b7754-103">This topic provides information about the following areas to help you implement and work with assemblies in the database:</span></span>  
  
-   <span data-ttu-id="b7754-104">Création d'assemblys</span><span class="sxs-lookup"><span data-stu-id="b7754-104">Creating assemblies</span></span>  
  
-   <span data-ttu-id="b7754-105">Modification des assemblys</span><span class="sxs-lookup"><span data-stu-id="b7754-105">Modifying assemblies</span></span>  
  
-   <span data-ttu-id="b7754-106">Suppression, désactivation et activation d’assemblys</span><span class="sxs-lookup"><span data-stu-id="b7754-106">Dropping, disabling, and enabling assemblies</span></span>  
  
-   <span data-ttu-id="b7754-107">Gestion des versions d’assembly</span><span class="sxs-lookup"><span data-stu-id="b7754-107">Managing assembly versions</span></span>  
  
## <a name="creating-assemblies"></a><span data-ttu-id="b7754-108">Création d'assemblys</span><span class="sxs-lookup"><span data-stu-id="b7754-108">Creating Assemblies</span></span>  
 <span data-ttu-id="b7754-109">Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les assemblys sont créés à l'aide de l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE ASSEMBLY, et dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], au moyen de l'éditeur assisté d'assemblys.</span><span class="sxs-lookup"><span data-stu-id="b7754-109">Assemblies are created in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE ASSEMBLY statement, or in the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] by using the Assembly Assisted Editor.</span></span> <span data-ttu-id="b7754-110">En outre, le déploiement d’un projet de SQL Server dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] inscrit un assembly dans la base de données qui a été spécifiée pour le projet.</span><span class="sxs-lookup"><span data-stu-id="b7754-110">Additionally, deploying a SQL Server Project in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] registers an assembly in the database that was specified for the project.</span></span> <span data-ttu-id="b7754-111">Pour plus d’informations, consultez [Déploiement d’objets de base de données CLR](deploying-clr-database-objects.md).</span><span class="sxs-lookup"><span data-stu-id="b7754-111">For more information, see [Deploying CLR Database Objects](deploying-clr-database-objects.md).</span></span>  
  
 <span data-ttu-id="b7754-112">**Pour créer un assembly à l'aide de Transact-SQL**</span><span class="sxs-lookup"><span data-stu-id="b7754-112">**To create an assembly by using Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="b7754-113">CREATE ASSEMBLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b7754-113">CREATE ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-assembly-transact-sql)  
  
 <span data-ttu-id="b7754-114">**Pour créer un assembly à l'aide de SQL Server Management Studio**</span><span class="sxs-lookup"><span data-stu-id="b7754-114">**To create an assembly by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="b7754-115">Propriétés de l’assembly &#40;&#41;page général</span><span class="sxs-lookup"><span data-stu-id="b7754-115">Assembly Properties &#40;General Page&#41;</span></span>](assemblies-properties.md)  
  
## <a name="modifying-assemblies"></a><span data-ttu-id="b7754-116">Modification des assemblys</span><span class="sxs-lookup"><span data-stu-id="b7754-116">Modifying Assemblies</span></span>  
 <span data-ttu-id="b7754-117">Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous modifiez les assemblys au moyen de l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY. Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], vous utilisez pour cela l'éditeur assisté d'assemblys.</span><span class="sxs-lookup"><span data-stu-id="b7754-117">Assemblies are modified in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY statement or in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] by using the Assembly Assisted Editor.</span></span> <span data-ttu-id="b7754-118">Vous pouvez modifier un assembly pour effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="b7754-118">You can modify an assembly when you want to do the following:</span></span>  
  
-   <span data-ttu-id="b7754-119">Changer l'implémentation de l'assembly en chargeant une nouvelle version de ses binaires.</span><span class="sxs-lookup"><span data-stu-id="b7754-119">Change the implementation of the assembly by uploading a newer version of the binaries of the assembly.</span></span> <span data-ttu-id="b7754-120">Pour plus d’informations, consultez [gestion des versions d’assembly](#_managing) plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="b7754-120">For more information, see [Managing Assembly Versions](#_managing) later in this topic.</span></span>  
  
-   <span data-ttu-id="b7754-121">Changer le jeu d'autorisations de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="b7754-121">Change the permission set of the assembly.</span></span> <span data-ttu-id="b7754-122">Pour plus d’informations, consultez [Conception d’assemblys](../../relational-databases/clr-integration/assemblies-designing.md).</span><span class="sxs-lookup"><span data-stu-id="b7754-122">For more information, see [Designing Assemblies](../../relational-databases/clr-integration/assemblies-designing.md).</span></span>  
  
-   <span data-ttu-id="b7754-123">Modifier la visibilité de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="b7754-123">Change the visibility of the assembly.</span></span> <span data-ttu-id="b7754-124">Les assemblys visibles sont disponibles pour référencement dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b7754-124">Visible assemblies are available for referencing in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b7754-125">Les assemblys non visibles ne sont pas disponibles, même s'ils ont été chargés dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="b7754-125">Nonvisible assemblies are not available, even if they have been uploaded in the database.</span></span> <span data-ttu-id="b7754-126">Par défaut, les assemblys chargés dans une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont visibles.</span><span class="sxs-lookup"><span data-stu-id="b7754-126">By default, assemblies uploaded to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are visible.</span></span>  
  
-   <span data-ttu-id="b7754-127">Ajouter ou supprimer un fichier de débogage ou source associé avec l'assembly.</span><span class="sxs-lookup"><span data-stu-id="b7754-127">Add or drop a debug or source file associated with the assembly.</span></span>  
  
 <span data-ttu-id="b7754-128">**Pour modifier un assembly à l'aide de Transact-SQL**</span><span class="sxs-lookup"><span data-stu-id="b7754-128">**To modify an assembly by using Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="b7754-129">ALTER ASSEMBLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b7754-129">ALTER ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
 <span data-ttu-id="b7754-130">**Pour modifier un assembly à l'aide de SQL Server Management Studio**</span><span class="sxs-lookup"><span data-stu-id="b7754-130">**To modify an assembly by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="b7754-131">Propriétés de l’assembly &#40;&#41;page général</span><span class="sxs-lookup"><span data-stu-id="b7754-131">Assembly Properties &#40;General Page&#41;</span></span>](assemblies-properties.md)  
  
## <a name="dropping-disabling-and-enabling-assemblies"></a><span data-ttu-id="b7754-132">Suppression, désactivation et activation des assemblys</span><span class="sxs-lookup"><span data-stu-id="b7754-132">Dropping, Disabling, and Enabling Assemblies</span></span>  
 <span data-ttu-id="b7754-133">Vous supprimez les assemblys à l'aide de l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] DROP ASSEMBLY ou dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b7754-133">Assemblies are dropped by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] DROP ASSEMBLY statement or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="b7754-134">**Pour supprimer un assembly à l'aide de Transact-SQL**</span><span class="sxs-lookup"><span data-stu-id="b7754-134">**To drop an assembly by using Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="b7754-135">DROP ASSEMBLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b7754-135">DROP ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-assembly-transact-sql)  
  
 <span data-ttu-id="b7754-136">**Pour supprimer un assembly à l'aide de SQL Server Management Studio**</span><span class="sxs-lookup"><span data-stu-id="b7754-136">**To drop an assembly by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="b7754-137">Supprimer les objets</span><span class="sxs-lookup"><span data-stu-id="b7754-137">Delete Objects</span></span>](../../ssms/object/delete-objects.md)  
  
 <span data-ttu-id="b7754-138">Par défaut, l'exécution de tous les assemblys créés dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est désactivée.</span><span class="sxs-lookup"><span data-stu-id="b7754-138">By default, all assemblies that are created in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are disabled from executing.</span></span> <span data-ttu-id="b7754-139">Vous pouvez utiliser l’option **CLR activé** de la procédure stockée système **sp_configure** pour désactiver ou activer l’exécution de tous les assemblys téléchargés dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b7754-139">You can use the **clr enabled** option of the **sp_configure** system stored procedure to disable or enable the execution of all assemblies that are uploaded in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b7754-140">La désactivation de l'exécution d'un assembly empêche l'exécution des fonctions CLR (Common Language Runtime), des procédures stockées, des déclencheurs, des agrégats et des types définis par l'utilisateur, de même qu'elle arrête leur exécution si celle-ci est en cours.</span><span class="sxs-lookup"><span data-stu-id="b7754-140">Disabling assembly execution prevents common language runtime (CLR) functions, stored procedures, triggers, aggregates, and user-defined types from executing, and stops those that are currently executing.</span></span> <span data-ttu-id="b7754-141">Elle n'entrave cependant pas la possibilité de créer, de modifier ou de supprimer des assemblys.</span><span class="sxs-lookup"><span data-stu-id="b7754-141">Disabling assembly execution does not disable the ability to create, alter, or drop assemblies.</span></span> <span data-ttu-id="b7754-142">Pour plus d’informations, consultez [clr enabled (option de configuration de serveur)](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md).</span><span class="sxs-lookup"><span data-stu-id="b7754-142">For more information, see [clr enabled Server Configuration Option](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="b7754-143">**Pour désactiver et activer la création d'assemblys**</span><span class="sxs-lookup"><span data-stu-id="b7754-143">**To disable and enable assembly execution**</span></span>  
  
-   [<span data-ttu-id="b7754-144">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b7754-144">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
##  <a name="managing-assembly-versions"></a><a name="_managing"></a><span data-ttu-id="b7754-145">Gestion des versions d’assembly</span><span class="sxs-lookup"><span data-stu-id="b7754-145">Managing Assembly Versions</span></span>  
 <span data-ttu-id="b7754-146">Quand un assembly est chargé dans une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il est stocké et géré dans les catalogues système de la base de données.</span><span class="sxs-lookup"><span data-stu-id="b7754-146">When an assembly is uploaded to an instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the assembly is stored and managed within the database system catalogs.</span></span> <span data-ttu-id="b7754-147">Toutes les modifications apportées à la définition de l’assembly dans le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] doivent être propagées à l’assembly qui est stocké dans le catalogue de la base de données.</span><span class="sxs-lookup"><span data-stu-id="b7754-147">Any changes made to the definition of the assembly in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] should be propagated to the assembly that is stored in the database catalog.</span></span>  
  
 <span data-ttu-id="b7754-148">Quand vous modifiez un assembly, vous devez émettre une instruction ALTER ASSEMBLY pour le mettre à jour dans la base de données,</span><span class="sxs-lookup"><span data-stu-id="b7754-148">When you have to modify an assembly, you must issue an ALTER ASSEMBLY statement to update the assembly in the database.</span></span> <span data-ttu-id="b7754-149">de façon à le remplacer par la dernière copie des modèles [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] contenant son implémentation.</span><span class="sxs-lookup"><span data-stu-id="b7754-149">This will update the assembly to the latest copy of [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] modules holding its implementation.</span></span>  
  
 <span data-ttu-id="b7754-150">La clause WITH UNCHECKED DATA de l'instruction ALTER ASSEMBLY prescrit à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d'actualiser jusqu'aux assemblys dont dépendent des données persistantes de la base de données.</span><span class="sxs-lookup"><span data-stu-id="b7754-150">The WITH UNCHECKED DATA clause of the ALTER ASSEMBLY statement instructs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to refresh even those assemblies upon which persisted data in the database is dependent.</span></span> <span data-ttu-id="b7754-151">En particulier, vous devez spécifier WITH UNCHECKED DATA en présence d'au moins un des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="b7754-151">Specifically, you must specify WITH UNCHECKED DATA if any of the following exist:</span></span>  
  
-   <span data-ttu-id="b7754-152">des colonnes calculées persistantes référençant des méthodes de l'assembly, soit directement, soit indirectement via des méthodes ou des fonctions [!INCLUDE[tsql](../../includes/tsql-md.md)] ;</span><span class="sxs-lookup"><span data-stu-id="b7754-152">Persisted computed columns that reference methods in the assembly, either directly, or indirectly, through [!INCLUDE[tsql](../../includes/tsql-md.md)] functions or methods.</span></span>  
  
-   <span data-ttu-id="b7754-153">Des colonnes d’un type CLR défini par l’utilisateur dépendant de l’assembly, ce type implémentant un format de sérialisation **UserDefined** (non-**Native**).</span><span class="sxs-lookup"><span data-stu-id="b7754-153">Columns of a CLR user-defined type that depend on the assembly, and the type implements a **UserDefined** (non-**Native**) serialization format.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="b7754-154">Si WITH UNCHECKED DATA n'est pas spécifié, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tente d'empêcher ALTER ASSEMBLY de s'exécuter si la nouvelle version de l'assembly affecte des données existantes dans des tables, des index ou dans d'autres sites persistants.</span><span class="sxs-lookup"><span data-stu-id="b7754-154">If WITH UNCHECKED DATA is not specified, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tries to prevent ALTER ASSEMBLY from executing if the new assembly version affects existing data in tables, indexes, or other persistent sites.</span></span> <span data-ttu-id="b7754-155">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne garantit cependant pas que les colonnes, les index, les vues indexées ou les expressions calculés seront cohérents avec les routines et les types sous-jacents une fois l'assembly CLR mis à jour.</span><span class="sxs-lookup"><span data-stu-id="b7754-155">However, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not guarantee that computed columns, indexes, indexed views, or expressions will be consistent with the underlying routines and types when the CLR assembly is updated.</span></span> <span data-ttu-id="b7754-156">Soyez prudent lorsque vous exécutez ALTER ASSEMBLY pour vous assurer qu'il n'y a pas de discordance entre le résultat d'une expression et une valeur basée sur cette expression stockée dans l'assembly.</span><span class="sxs-lookup"><span data-stu-id="b7754-156">Be careful when you execute ALTER ASSEMBLY to make sure that there is no mismatch between the result of an expression and a value that is based on that expression stored in the assembly.</span></span>  
  
 <span data-ttu-id="b7754-157">Seuls les membres du rôle de base de données fixe **db_owner** et **db_ddlowner** peuvent exécuter l’instruction ALTER assembly à l’aide de la clause with unchecked Data.</span><span class="sxs-lookup"><span data-stu-id="b7754-157">Only members of the **db_owner** and **db_ddlowner** fixed database role can execute run ALTER ASSEMBLY by using the WITH UNCHECKED DATA clause.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b7754-158">publie un message dans le journal des événements des applications Windows indiquant que l'assembly a été modifié avec les données non vérifiées des tables.</span><span class="sxs-lookup"><span data-stu-id="b7754-158">posts a message to the Windows application event log that the assembly has been modified with unchecked data in the tables.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b7754-159">marque ensuite les tables contenant les données dépendant de l'assembly comme comportant des données non vérifiées.</span><span class="sxs-lookup"><span data-stu-id="b7754-159">then marks any tables that contain data dependent on the assembly as having unchecked data.</span></span> <span data-ttu-id="b7754-160">La colonne **has_unchecked_assembly_data** de l’affichage catalogue **sys. tables** contient la valeur 1 pour les tables qui contiennent des données non vérifiées, et 0 pour les tables sans données non vérifiées.</span><span class="sxs-lookup"><span data-stu-id="b7754-160">The **has_unchecked_assembly_data** column of the **sys.tables** catalog view contains the value 1 for tables that contain unchecked data, and 0 for tables without unchecked data.</span></span>  
  
 <span data-ttu-id="b7754-161">Pour contrôler l'intégrité des valeurs non vérifiées, exécutez DBCC CHECKTABLE sur chaque table comportant des données non vérifiées.</span><span class="sxs-lookup"><span data-stu-id="b7754-161">To resolve the integrity of unchecked data, run DBCC CHECKTABLE against each table that has unchecked data.</span></span> <span data-ttu-id="b7754-162">Si DBCC CHECKTABLE échoue, vous devez soit supprimer les lignes de la table non valides, soit modifier le code de l'assembly de façon à résoudre les problèmes, puis émettre de nouvelles instructions ALTER ASSEMBLY.</span><span class="sxs-lookup"><span data-stu-id="b7754-162">If DBCC CHECKTABLE fails, you must either delete the table rows that are not valid or modify the assembly code to address problems, and then issue additional ALTER ASSEMBLY statements.</span></span>  
  
 <span data-ttu-id="b7754-163">ALTER ASSEMBLY modifie la version de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="b7754-163">ALTER ASSEMBLY changes the assembly version.</span></span> <span data-ttu-id="b7754-164">La culture et le jeton de clé publique de l’assembly restent identiques. SQL Server n’autorise pas l’inscription de différentes versions d’un assembly avec le même nom, la même culture et la même clé publique.</span><span class="sxs-lookup"><span data-stu-id="b7754-164">The culture and public key token of the assembly remain the same.SQL Server does not allow registering different versions of an assembly with the same name, culture and public key.</span></span>  
  
### <a name="interactions-with-computer-wide-policy-for-version-binding"></a><span data-ttu-id="b7754-165">Interactions avec la stratégie de l'ordinateur en matière de liaison des versions</span><span class="sxs-lookup"><span data-stu-id="b7754-165">Interactions with Computer-wide Policy for Version Binding</span></span>  
 <span data-ttu-id="b7754-166">Si des références à des assemblys stockés dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont redirigées vers des versions spécifiques à l'aide de la stratégie du serveur de publication ou de la stratégie de l'administrateur de l'ordinateur, vous devez procéder de l'une des façons suivantes :</span><span class="sxs-lookup"><span data-stu-id="b7754-166">If references to assemblies stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are redirected to specific versions by using publisher policy or computer-wide administrator policy, you must do either of the following:</span></span>  
  
-   <span data-ttu-id="b7754-167">Assurez-vous que la nouvelle version vers laquelle s'effectue cette redirection se trouve dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="b7754-167">Make sure the new version to which this redirection is made is in the database.</span></span>  
  
-   <span data-ttu-id="b7754-168">Modifiez les instructions pointant vers les fichiers de stratégie externes de l'ordinateur ou la stratégie du serveur de publication pour vous assurer qu'elles référencent la version spécifique figurant dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="b7754-168">Modify any statements to the external policy files of the computer or publisher policy to make sure that they reference the specific version that is in the database.</span></span>  
  
 <span data-ttu-id="b7754-169">Sans cela, la tentative de chargement d'une nouvelle version d'assembly dans l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] échouera.</span><span class="sxs-lookup"><span data-stu-id="b7754-169">Otherwise, an attempt to load a new assembly version to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will fail.</span></span>  
  
 <span data-ttu-id="b7754-170">**Pour mettre à jour la version de l'assembly**</span><span class="sxs-lookup"><span data-stu-id="b7754-170">**To update the version of an assembly**</span></span>  
  
-   [<span data-ttu-id="b7754-171">ALTER ASSEMBLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b7754-171">ALTER ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="b7754-172">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7754-172">See Also</span></span>  
 <span data-ttu-id="b7754-173">[Assemblys &#40;Moteur de base de données&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="b7754-173">[Assemblies &#40;Database Engine&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md) </span></span>  
 [<span data-ttu-id="b7754-174">Obtention d'informations sur les assemblys</span><span class="sxs-lookup"><span data-stu-id="b7754-174">Getting Information About Assemblies</span></span>](../../relational-databases/clr-integration/assemblies-getting-information.md)  
  
  