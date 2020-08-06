---
title: Définir les propriétés d’une base de données multidimensionnelle (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- properties [Analysis Services], databases
ms.assetid: a8be5b3f-3148-448a-976c-7222705155d9
author: minewiskan
ms.author: owend
ms.openlocfilehash: f0ce2a04647413059607e4eb7ae156cf97a96605
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611973"
---
# <a name="set-multidimensional-database-properties-analysis-services"></a><span data-ttu-id="2aedb-102">Définir les propriétés de base de données multidimensionnelle (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="2aedb-102">Set Multidimensional Database Properties (Analysis Services)</span></span>
  <span data-ttu-id="2aedb-103">Il existe plusieurs [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Propriétés de base de données que vous pouvez configurer dans le [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] Concepteur de base de données.</span><span class="sxs-lookup"><span data-stu-id="2aedb-103">There are a number of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database properties that you can configure in the [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] database designer.</span></span>  
  
 <span data-ttu-id="2aedb-104">Ce concepteur vous permet d'effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="2aedb-104">In this designer, you can perform the following types of tasks:</span></span>  
  
-   <span data-ttu-id="2aedb-105">Si vous êtes connecté à la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode en ligne, vous pouvez modifier le nom de la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2aedb-105">If you are connected to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database in online mode, you can change the name of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="2aedb-106">Si vous utilisez le mode projet, vous pouvez modifier le nom du prochain déploiement du projet.</span><span class="sxs-lookup"><span data-stu-id="2aedb-106">If you are working in project mode, you can change the database name for the next deployment of the project.</span></span> <span data-ttu-id="2aedb-107">Pour plus d’informations, consultez [Renommer une base de données multidimensionnelle &#40;Analysis Services&#41;](rename-a-multidimensional-database-analysis-services.md) et [Configurer les propriétés d’un projet Analysis Services &#40;SSDT&#41;](configure-analysis-services-project-properties-ssdt.md).</span><span class="sxs-lookup"><span data-stu-id="2aedb-107">For more information, see [Rename a Multidimensional Database &#40;Analysis Services&#41;](rename-a-multidimensional-database-analysis-services.md) and [Configure Analysis Services Project Properties &#40;SSDT&#41;](configure-analysis-services-project-properties-ssdt.md).</span></span>  
  
-   <span data-ttu-id="2aedb-108">Vous pouvez fournir une description de la base de données pouvant être présentée aux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="2aedb-108">You can provide a description of the database that can be presented to users.</span></span> <span data-ttu-id="2aedb-109">En outre, vous pouvez afficher le nom de la base de données, mais pas le modifier.</span><span class="sxs-lookup"><span data-stu-id="2aedb-109">You can also view the name of the database, but cannot change it.</span></span> <span data-ttu-id="2aedb-110">Pour modifier le nom de la base de données, vous devez modifier les propriétés du projet.</span><span class="sxs-lookup"><span data-stu-id="2aedb-110">To change the database name, you must edit the properties of the project.</span></span>  
  
-   <span data-ttu-id="2aedb-111">Vous pouvez fournir la traduction du nom et de la description de la base de données dans une ou plusieurs langues.</span><span class="sxs-lookup"><span data-stu-id="2aedb-111">You can provide translations for the database name and description for one or more languages.</span></span> <span data-ttu-id="2aedb-112">Pour plus d’informations, consultez [traductions de cubes](../multidimensional-models-olap-logical-cube-objects/cube-translations.md), [traductions de dimensions](../multidimensional-models-olap-logical-dimension-objects/dimension-translations.md)et [traductions &#40;Analysis Services&#41;](../translations-analysis-services.md).</span><span class="sxs-lookup"><span data-stu-id="2aedb-112">For more information, see [Cube Translations](../multidimensional-models-olap-logical-cube-objects/cube-translations.md), [Dimension Translations](../multidimensional-models-olap-logical-dimension-objects/dimension-translations.md), and [Translations &#40;Analysis Services&#41;](../translations-analysis-services.md).</span></span>  
  
-   <span data-ttu-id="2aedb-113">Vous pouvez afficher et modifier les mappages de types de compte par défaut.</span><span class="sxs-lookup"><span data-stu-id="2aedb-113">You can view and modify default account type mappings.</span></span> <span data-ttu-id="2aedb-114">Les mappages de type de compte sont utilisés quand une ou plusieurs mesures font appel à la fonction d’agrégation *ByAccount* .</span><span class="sxs-lookup"><span data-stu-id="2aedb-114">Account type mappings are used when one or more measures use the *ByAccount* aggregation function.</span></span> <span data-ttu-id="2aedb-115">Pour chaque type de compte, vous pouvez spécifier un alias et modifier la fonction d'agrégation par défaut associé au type de compte.</span><span class="sxs-lookup"><span data-stu-id="2aedb-115">For each account type, you can specify an alias and modify the default aggregation function associated with the account type.</span></span> <span data-ttu-id="2aedb-116">Pour plus d’informations sur la modification de l’agrégation par défaut, consultez [Définir le comportement semi-additif](define-semiadditive-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="2aedb-116">For more information modifying the default aggregation, see [Define Semiadditive Behavior](define-semiadditive-behavior.md).</span></span>  
  
## <a name="database-properties"></a><span data-ttu-id="2aedb-117">Propriétés de la base de données</span><span class="sxs-lookup"><span data-stu-id="2aedb-117">Database Properties</span></span>  
 <span data-ttu-id="2aedb-118">Outre les éléments ci-dessus, vous pouvez configurer plusieurs propriétés d'une base de données dans la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="2aedb-118">In addition to the above, there are a number of properties of a database that you can configure in the Properties window.</span></span>  
  
|<span data-ttu-id="2aedb-119">Propriété</span><span class="sxs-lookup"><span data-stu-id="2aedb-119">Property</span></span>|<span data-ttu-id="2aedb-120">Description</span><span class="sxs-lookup"><span data-stu-id="2aedb-120">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="2aedb-121">Préfixe d'agrégation</span><span class="sxs-lookup"><span data-stu-id="2aedb-121">Aggregation Prefix</span></span>|<span data-ttu-id="2aedb-122">Préfixe commun pouvant être utilisé pour les noms d'agrégation de toutes les partitions d'une base de données.</span><span class="sxs-lookup"><span data-stu-id="2aedb-122">The common prefix that can be used for aggregation names for all of the partitions in a database.</span></span> <span data-ttu-id="2aedb-123">Pour plus d’informations, consultez [Élément AggregationPrefix &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/aggregationprefix-element-assl).</span><span class="sxs-lookup"><span data-stu-id="2aedb-123">For more information, see [AggregationPrefix Element &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/aggregationprefix-element-assl).</span></span>|  
|<span data-ttu-id="2aedb-124">Classement</span><span class="sxs-lookup"><span data-stu-id="2aedb-124">Collation</span></span>|<span data-ttu-id="2aedb-125">Si le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] est déployé sur une instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , la base de données hérite de la propriété de classement du serveur, sauf si une valeur différente est spécifiée ici.</span><span class="sxs-lookup"><span data-stu-id="2aedb-125">When the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project is deployed to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, the database will inherit from the Collation server property unless a different value is provided here.</span></span>|  
|<span data-ttu-id="2aedb-126">DataSourceImpersonationInfo</span><span class="sxs-lookup"><span data-stu-id="2aedb-126">DataSourceImpersonationInfo</span></span>|<span data-ttu-id="2aedb-127">Indique le mode d'emprunt d'identité par défaut pour tous les objets de source de données dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="2aedb-127">Specifies the default impersonation mode for all data source objects in the database.</span></span> <span data-ttu-id="2aedb-128">Il s’agit du mode utilisé par le service [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pendant le traitement des objets, la synchronisation des serveurs et l’exécution des instructions d’exploration de données OpenQuery et SystemOpenSchema.</span><span class="sxs-lookup"><span data-stu-id="2aedb-128">This is the mode that the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] service uses when processing objects, synchronizing servers, and executing the OpenQuery and SystemOpenSchema data mining statements.</span></span>|  
|<span data-ttu-id="2aedb-129">Taille estimée</span><span class="sxs-lookup"><span data-stu-id="2aedb-129">Estimated Size</span></span>|<span data-ttu-id="2aedb-130">Fournit la taille estimée des fichiers de base de données sur le disque.</span><span class="sxs-lookup"><span data-stu-id="2aedb-130">Provides an estimated size of the database files on disk.</span></span> <span data-ttu-id="2aedb-131">Si les données sont stockées dans plusieurs emplacements, cette estimation sera limitée aux fichiers de données stockés sous le dossier de la base de données.</span><span class="sxs-lookup"><span data-stu-id="2aedb-131">If data is stored in multiple locations, this estimate will be limited to just the data files stored under the database folder.</span></span><br /><br /> <span data-ttu-id="2aedb-132">`EstimatedSize` peut également être utilisé comme base d'estimation de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="2aedb-132">`EstimatedSize` can also be used as a basis for estimating memory.</span></span> <span data-ttu-id="2aedb-133">En général, la configuration requise pour la mémoire est supérieure à la taille des données sur le disque en raison des structures de données supplémentaires qui sont créées lors du chargement de la base de données dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="2aedb-133">Typically, memory requirements are larger than the size of data on disk due to additional data structures that are created when the database is loaded into memory.</span></span><br /><br /> <span data-ttu-id="2aedb-134">Pour affiner la configuration requise pour la mémoire, vous pouvez également utiliser le Gestionnaire des tâches afin d'examiner la mémoire de traitement Analysis Services avant et après le traitement de la base de données et observer la mémoire utilisée pour comprendre la configuration requise pour la mémoire de la base de données.</span><span class="sxs-lookup"><span data-stu-id="2aedb-134">To further estimate memory requirements, you can also use Task Manager to look at the Analysis Services process memory before and after processing the database and observe the memory utilized as a method for understanding the memory requirements of the database.</span></span>|  
|<span data-ttu-id="2aedb-135">Langage</span><span class="sxs-lookup"><span data-stu-id="2aedb-135">Language</span></span>|<span data-ttu-id="2aedb-136">Si le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] est déployé dans une instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , la base de données hérite de la propriété de langue du serveur, sauf si une valeur différente est spécifiée ici.</span><span class="sxs-lookup"><span data-stu-id="2aedb-136">When the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project is deployed to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, the database will inherit from the Language server property unless a different value is provided here.</span></span>|  
|<span data-ttu-id="2aedb-137">MasterDataSource ID</span><span class="sxs-lookup"><span data-stu-id="2aedb-137">MasterDataSource ID</span></span>|<span data-ttu-id="2aedb-138">Utilisé avec les partitions distantes.</span><span class="sxs-lookup"><span data-stu-id="2aedb-138">Used with remote partitions.</span></span> <span data-ttu-id="2aedb-139">Pour plus d’informations, consultez [Partitions distantes](../multidimensional-models-olap-logical-cube-objects/partitions-remote-partitions.md).</span><span class="sxs-lookup"><span data-stu-id="2aedb-139">For more information, see [Remote Partitions](../multidimensional-models-olap-logical-cube-objects/partitions-remote-partitions.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2aedb-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2aedb-140">See Also</span></span>  
 <span data-ttu-id="2aedb-141">[Boîte de dialogue Propriétés de la base de données &#40;SSAS-multidimensionnel&#41;](../database-properties-dialog-box-ssas-multidimensional.md) </span><span class="sxs-lookup"><span data-stu-id="2aedb-141">[Database Properties Dialog Box &#40;SSAS - Multidimensional&#41;](../database-properties-dialog-box-ssas-multidimensional.md) </span></span>  
 [<span data-ttu-id="2aedb-142">Configurer les propriétés d’un projet Analysis Services &#40;SSDT&#41;</span><span class="sxs-lookup"><span data-stu-id="2aedb-142">Configure Analysis Services Project Properties &#40;SSDT&#41;</span></span>](configure-analysis-services-project-properties-ssdt.md)  
  
  