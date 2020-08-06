---
title: Groupe de fichiers à mémoire optimisée | Microsoft Docs
ms.custom: ''
ms.date: 11/19/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 14106cc9-816b-493a-bcb9-fe66a1cd4630
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a4ab6423159d0ba5a27af152cc5578905f57eec6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87614061"
---
# <a name="the-memory-optimized-filegroup"></a><span data-ttu-id="5bc1a-102">Groupe de fichiers mémoire optimisé</span><span class="sxs-lookup"><span data-stu-id="5bc1a-102">The Memory Optimized Filegroup</span></span>
  <span data-ttu-id="5bc1a-103">Pour créer des tables mémoire optimisées, vous devez d'abord créer un groupe de fichiers mémoire optimisé.</span><span class="sxs-lookup"><span data-stu-id="5bc1a-103">To create memory-optimized tables, you must first create a memory-optimized filegroup.</span></span> <span data-ttu-id="5bc1a-104">Le groupe de fichiers mémoire optimisé contient un ou plusieurs conteneurs.</span><span class="sxs-lookup"><span data-stu-id="5bc1a-104">The memory-optimized filegroup holds one or more containers.</span></span> <span data-ttu-id="5bc1a-105">Chaque conteneur contient des fichiers de données, des fichiers delta ou les deux.</span><span class="sxs-lookup"><span data-stu-id="5bc1a-105">Each container contains data files or delta files or both.</span></span>  
  
 <span data-ttu-id="5bc1a-106">Bien que les lignes de données dans les tables `SCHEMA_ONLY` ne soient pas conservées et que les métadonnées des tables à mémoire optimisée et des procédures stockées compilées en mode natif soient stockées dans des catalogues traditionnels, le moteur [!INCLUDE[hek_2](../../includes/hek-2-md.md)] requiert toujours un groupe de fichiers à mémoire optimisée pour les tables à mémoire optimisée `SCHEMA_ONLY` afin de fournir une expérience uniforme pour les bases de données avec des tables à mémoire optimisée.</span><span class="sxs-lookup"><span data-stu-id="5bc1a-106">Even though data rows from `SCHEMA_ONLY` tables are not persisted and the metadata for memory-optimized tables and natively compiled stored procedures is stored in the traditional catalogs, the [!INCLUDE[hek_2](../../includes/hek-2-md.md)] engine still requires a memory-optimized filegroup for `SCHEMA_ONLY` memory-optimized tables to provide a uniform experience for databases with memory-optimized tables.</span></span>  
  
 <span data-ttu-id="5bc1a-107">Le groupe de fichiers mémoire optimisé est basé sur le groupe de fichiers de flux de fichier, avec les différences suivantes :</span><span class="sxs-lookup"><span data-stu-id="5bc1a-107">The memory-optimized filegroup is based on filestream filegroup, with the following differences:</span></span>  
  
-   <span data-ttu-id="5bc1a-108">Vous ne pouvez créer qu'un seul groupe de fichiers mémoire optimisé par base de données.</span><span class="sxs-lookup"><span data-stu-id="5bc1a-108">You can only create one memory-optimized filegroup per database.</span></span> <span data-ttu-id="5bc1a-109">Vous devez marquer explicitement le groupe de fichiers comme contenant memory_optimized_data.</span><span class="sxs-lookup"><span data-stu-id="5bc1a-109">You need to explicitly mark the filegroup as containing memory_optimized_data.</span></span> <span data-ttu-id="5bc1a-110">Vous pouvez créer le groupe de fichiers lorsque vous créez la base de données, ou vous pouvez l' ajouter ultérieurement :</span><span class="sxs-lookup"><span data-stu-id="5bc1a-110">You can create the filegroup when you create the database or you can add it later:</span></span>  
  
    ```sql  
    ALTER DATABASE imoltp ADD FILEGROUP imoltp_mod CONTAINS MEMORY_OPTIMIZED_DATA  
    ```  
  
-   <span data-ttu-id="5bc1a-111">Vous devez ajouter un ou plusieurs conteneurs au groupe de fichiers MEMORY_OPTIMIZED_DATA.</span><span class="sxs-lookup"><span data-stu-id="5bc1a-111">You need to add one or more containers to the MEMORY_OPTIMIZED_DATA filegroup.</span></span> <span data-ttu-id="5bc1a-112">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="5bc1a-112">For example:</span></span>  
  
    ```sql  
    ALTER DATABASE imoltp ADD FILE (name='imoltp_mod1', filename='c:\data\imoltp_mod1') TO FILEGROUP imoltp_mod  
    ```  
  
-   <span data-ttu-id="5bc1a-113">Vous n’avez pas besoin d’activer le flux de fichier ([Activer et configurer FILESTREAM](../blob/enable-and-configure-filestream.md)) pour créer un groupe de fichiers mémoire optimisé.</span><span class="sxs-lookup"><span data-stu-id="5bc1a-113">You do not need to enable filestream ([Enable and Configure FILESTREAM](../blob/enable-and-configure-filestream.md)) to create a memory-optimized filegroup.</span></span> <span data-ttu-id="5bc1a-114">Le mappage au flux de fichier est effectué par le moteur [!INCLUDE[hek_2](../../includes/hek-2-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5bc1a-114">The mapping to filestream is done by the [!INCLUDE[hek_2](../../includes/hek-2-md.md)] engine.</span></span>  
  
-   <span data-ttu-id="5bc1a-115">Vous pouvez ajouter de nouveaux conteneurs à un groupe de fichiers mémoire optimisé.</span><span class="sxs-lookup"><span data-stu-id="5bc1a-115">You can add new containers to a memory-optimized filegroup.</span></span> <span data-ttu-id="5bc1a-116">Vous aurez peut-être besoin d’un nouveau conteneur pour étendre le stockage nécessaire à la création d’une table mémoire optimisée durable et pour distribuer des e/s sur plusieurs conteneurs.</span><span class="sxs-lookup"><span data-stu-id="5bc1a-116">You may need a new container to expand the storage needed for durable memory-optimized table and also to distribute I/O across multiple containers.</span></span>  
  
-   <span data-ttu-id="5bc1a-117">Le déplacement des données avec un groupe de fichiers mémoire optimisé est optimisé dans une configuration de groupe de disponibilité AlwaysOn.</span><span class="sxs-lookup"><span data-stu-id="5bc1a-117">Data movement with a memory-optimized filegroup is optimized in an AlwaysOn Availability Group configuration.</span></span> <span data-ttu-id="5bc1a-118">Contrairement aux fichiers de flux de fichier envoyés aux réplicas secondaires, les fichiers de point de contrôle (de données et delta) du groupe de fichiers mémoire optimisé ne sont pas envoyés aux réplicas secondaires.</span><span class="sxs-lookup"><span data-stu-id="5bc1a-118">Unlike filestream files that are sent to secondary replicas, the checkpoint files (both data and delta) within the memory-optimized filegroup are not sent to secondary replicas.</span></span> <span data-ttu-id="5bc1a-119">Les fichiers de données et delta sont construits à l'aide du journal des transactions sur le réplica secondaire.</span><span class="sxs-lookup"><span data-stu-id="5bc1a-119">The data and delta files are constructed using the transaction log on the secondary replica.</span></span>  
  
<span data-ttu-id="5bc1a-120">Limitations suivantes du groupe de fichiers mémoire optimisé,</span><span class="sxs-lookup"><span data-stu-id="5bc1a-120">The following limitations of memory-optimized filegroup,</span></span>  
  
-   <span data-ttu-id="5bc1a-121">Une fois que vous avez créé un groupe de fichiers mémoire optimisé, vous ne pouvez le supprimer qu'en supprimant la base de données.</span><span class="sxs-lookup"><span data-stu-id="5bc1a-121">Once you create a memory-optimized filegroup, you can only remove it by dropping the database.</span></span> <span data-ttu-id="5bc1a-122">Dans un environnement de production, il est peu probable que vous deviez supprimer le groupe de fichiers mémoire optimisé.</span><span class="sxs-lookup"><span data-stu-id="5bc1a-122">In a production environment, it is unlikely that you will need to remove the memory-optimized filegroup.</span></span>  
  
-   <span data-ttu-id="5bc1a-123">Vous ne pouvez pas supprimer un conteneur non vide ni déplacer des paires de fichiers de données et delta vers un autre conteneur dans le groupe de fichiers mémoire optimisé.</span><span class="sxs-lookup"><span data-stu-id="5bc1a-123">You cannot drop a non-empty container or move data and delta file pairs to another container in the memory-optimized filegroup.</span></span>  
  
## <a name="configuring-a-memory-optimized-filegroup"></a><span data-ttu-id="5bc1a-124">Configuration d'un groupe de fichiers mémoire optimisé</span><span class="sxs-lookup"><span data-stu-id="5bc1a-124">Configuring a Memory-Optimized Filegroup</span></span>  
<span data-ttu-id="5bc1a-125">Envisagez de créer plusieurs conteneurs dans le groupe de fichiers à mémoire optimisée et de les répartir sur différents lecteurs afin d’obtenir davantage de bande passante pour transmettre en continu les données en mémoire.</span><span class="sxs-lookup"><span data-stu-id="5bc1a-125">Consider creating multiple containers in the memory-optimized filegroup and distribute them on different drives to achieve more bandwidth to stream the data into memory.</span></span>  
  
<span data-ttu-id="5bc1a-126">Lors de la configuration du stockage, vous devez fournir un espace libre correspondant à quatre fois la taille des tables mémoire optimisées durables.</span><span class="sxs-lookup"><span data-stu-id="5bc1a-126">When configuring storage, you must provide free disk space that is four times the size of durable memory-optimized tables.</span></span> <span data-ttu-id="5bc1a-127">Assurez-vous que votre sous-système d’e/s prend en charge les IOPS requises pour votre charge de travail.</span><span class="sxs-lookup"><span data-stu-id="5bc1a-127">Ensure that your I/O subsystem supports the required IOPS for your workload.</span></span> <span data-ttu-id="5bc1a-128">Si les paires de fichiers de données et delta sont définies à un niveau d’IOPS donné, vous avez besoin de trois fois cette valeur d’IOPS pour tenir compte des opérations de stockage et de fusion.</span><span class="sxs-lookup"><span data-stu-id="5bc1a-128">If data and delta file pairs are populated at a given IOPS, you need three times that IOPS to account for storing and merge operations.</span></span> <span data-ttu-id="5bc1a-129">Vous pouvez ajouter une capacité de stockage et des IOPS en ajoutant un ou plusieurs conteneurs au groupe de fichiers mémoire optimisé.</span><span class="sxs-lookup"><span data-stu-id="5bc1a-129">You can add storage capacity and IOPS by adding one or more containers to the memory-optimized filegroup.</span></span>  
  
<span data-ttu-id="5bc1a-130">Dans un scénario à plusieurs conteneurs et à plusieurs lecteurs, les fichiers de données et delta sont alloués dans des conteneurs selon le principe du tourniquet.</span><span class="sxs-lookup"><span data-stu-id="5bc1a-130">In a multiple container, multiple drive scenario, data and delta files are allocated in a round-robin fashion into containers.</span></span> <span data-ttu-id="5bc1a-131">Le premier fichier de données est alloué depuis le premier conteneur, le fichier delta depuis le conteneur suivant, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="5bc1a-131">The first data file is allocated from the first container and the delta file is allocated from the next container and this allocation pattern repeats.</span></span> <span data-ttu-id="5bc1a-132">Cette méthode d'allocation répartit les fichiers de données et delta de manière uniforme entre les conteneurs si vous avez un nombre impair de lecteurs, chacun étant mappé à un conteneur.</span><span class="sxs-lookup"><span data-stu-id="5bc1a-132">This allocation scheme distributes data and delta files evenly across containers if you have an odd number of drives, each mapped to one container.</span></span> <span data-ttu-id="5bc1a-133">Toutefois, si vous avez un nombre pair de lecteurs, chacun étant mappé à un conteneur, cela peut entraîner un stockage déséquilibré, les fichiers de données étant mappés aux lecteurs impairs et les fichiers delta aux lecteurs pairs.</span><span class="sxs-lookup"><span data-stu-id="5bc1a-133">However, if you have an even number of drives, each mapped to a container, it can result in imbalanced storage with data files mapped to odd drives and delta files mapped to even drives.</span></span> <span data-ttu-id="5bc1a-134">Pour obtenir un flux équilibré d’e/s sur la récupération, envisagez de placer des paires de fichiers de données et Delta sur les mêmes piles/stockages, comme décrit dans l’exemple ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="5bc1a-134">To obtain a balanced stream of I/O on recovery, consider placing pairs of data and delta files on the same spindles/storage as described in the example below.</span></span>  

> [!CAUTION]
> <span data-ttu-id="5bc1a-135">Si une valeur `MAXSIZE` est définie pour le groupe de fichiers à mémoire optimisée et que les fichiers de point de contrôle dépassent la taille maximale du conteneur, la base de données présente l’état SUSPECT.</span><span class="sxs-lookup"><span data-stu-id="5bc1a-135">If a `MAXSIZE` value is set for the memory-optimized filegroup, and checkpoint files exceed the max size of the container, then the database will become SUSPECT.</span></span>   
> <span data-ttu-id="5bc1a-136">Dans ce cas, n’essayez pas de définir les options OFFLINE et ONLINE de base de données, ce qui amène la base de données à rester dans l’état RECOVERY_PENDING.</span><span class="sxs-lookup"><span data-stu-id="5bc1a-136">In this case do not attempt to set the database OFFLINE and ONLINE, causing the database to stay in RECOVERY_PENDING state.</span></span>
  
### <a name="example"></a><span data-ttu-id="5bc1a-137">Exemple</span><span class="sxs-lookup"><span data-stu-id="5bc1a-137">Example</span></span> 
<span data-ttu-id="5bc1a-138">imaginons un groupe de fichiers mémoire optimisé avec deux conteneurs : conteneur 1 sur le lecteur X et conteneur 2 sur le lecteur Y.</span><span class="sxs-lookup"><span data-stu-id="5bc1a-138">Consider a memory-optimized filegroup with two containers: container 1 on drive X and container 2 on drives Y.</span></span>  
<span data-ttu-id="5bc1a-139">Étant donné que l'allocation des fichiers de données et delta s'effectue selon le principe du tourniquet, le conteneur 1 aura uniquement des fichiers de données, tandis que le conteneur 2 aura uniquement les fichiers delta. Cela entraînera une persistance déséquilibrée au niveau du stockage et des opérations d'entrée/sortie par seconde, dans la mesure où les fichiers de données sont beaucoup plus volumineux que les fichiers delta.</span><span class="sxs-lookup"><span data-stu-id="5bc1a-139">Since the allocation of data and delta files is done in round-robin fashion, container 1 will only have data files and container 2 will only have delta files, which leads to imbalanced persistence for storage as well as input/output operations per second, as data files are significantly larger than the delta files.</span></span>    
<span data-ttu-id="5bc1a-140">Pour distribuer des fichiers de données et Delta de manière uniforme entre les lecteurs X et Y, créez quatre conteneurs au lieu de deux, puis mappez les deux premiers conteneurs au lecteur X et aux deux conteneurs suivants pour le lecteur Y.</span><span class="sxs-lookup"><span data-stu-id="5bc1a-140">To distribute data and delta files uniformly across drives X and Y, create four containers instead of two, and map the first two containers to drive X and the next two containers to drive Y.</span></span>  
<span data-ttu-id="5bc1a-141">Avec l’allocation par tourniquet (Round Robin), les premières données et le premier fichier Delta sont alloués à partir du conteneur-1 et du conteneur-2, qui sont mappés au lecteur X.</span><span class="sxs-lookup"><span data-stu-id="5bc1a-141">With round-robin allocation, the first data and first delta file will be allocated from container-1 and container-2 respectively, which are mapped to drive X.</span></span>   
<span data-ttu-id="5bc1a-142">De même, les fichiers de données et Delta suivants seront alloués à partir du conteneur-3 et du conteneur-4, qui sont mappés au lecteur Y. Cela permet de distribuer uniformément les fichiers de données et les fichiers delta sur deux lecteurs.</span><span class="sxs-lookup"><span data-stu-id="5bc1a-142">Similarly, the next data and delta file will be allocated from container-3 and container-4 which are mapped to drive Y. This allows distributing data and delta files across two drives uniformly.</span></span>  
 
  
## <a name="see-also"></a><span data-ttu-id="5bc1a-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5bc1a-143">See Also</span></span>  
<span data-ttu-id="5bc1a-144">[Création et gestion du stockage des objets à mémoire optimisée](creating-and-managing-storage-for-memory-optimized-objects.md)   </span><span class="sxs-lookup"><span data-stu-id="5bc1a-144">[Creating and Managing Storage for Memory-Optimized Objects](creating-and-managing-storage-for-memory-optimized-objects.md)   </span></span>  
[<span data-ttu-id="5bc1a-145">Groupes de fichiers et fichiers de base de données</span><span class="sxs-lookup"><span data-stu-id="5bc1a-145">Database Files and Filegroups</span></span>](../../relational-databases/databases/database-files-and-filegroups.md)    
  