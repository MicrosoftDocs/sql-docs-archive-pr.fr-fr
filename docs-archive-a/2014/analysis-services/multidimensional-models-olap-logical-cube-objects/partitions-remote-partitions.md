---
title: Partitions distantes | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- storage [Analysis Services], partitions
- archiving remote partitions [Analysis Services]
- partitions [Analysis Services], remote
- restoring remote partitions [Analysis Services]
- backing up remote partitions [Analysis Services]
- partitions [Analysis Services], storage
- storing data [Analysis Services], partitions
- remote partitions [Analysis Services]
ms.assetid: 63f5d9f5-c6b6-4ceb-94fe-7b6c396d10bb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 32fdf05d061d4e1c1da6ec0ef9179ecd12bda172
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702047"
---
# <a name="remote-partitions"></a><span data-ttu-id="46e17-102">Partitions distantes</span><span class="sxs-lookup"><span data-stu-id="46e17-102">Remote Partitions</span></span>
  <span data-ttu-id="46e17-103">Les données d’une partition distante sont stockées sur une autre instance de Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] que l’instance qui contient les définitions (métadonnées) de la partition et de son cube parent.</span><span class="sxs-lookup"><span data-stu-id="46e17-103">The data of a remote partition is stored on a different instance of Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] than the instance that contains the definitions (metadata) of the partition and its parent cube.</span></span> <span data-ttu-id="46e17-104">Une partition distante est administrée sur la même instance d'[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans laquelle la partition et son cube parent sont définis.</span><span class="sxs-lookup"><span data-stu-id="46e17-104">A remote partition is administered on the same instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] where the partition and its parent cube are defined.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="46e17-105">Pour stocker une partition distante, l’ordinateur doit avoir une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] installée et exécuter le même niveau de Service Pack que l’instance où la partition a été définie.</span><span class="sxs-lookup"><span data-stu-id="46e17-105">To store a remote partition, the computer must have an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] installed and be running the same service pack level as the instance where the partition was defined.</span></span> <span data-ttu-id="46e17-106">Les partitions distantes sur des instances d'une version antérieure d'[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ne sont pas prises en charge.</span><span class="sxs-lookup"><span data-stu-id="46e17-106">Remote partitions on instances of an earlier version of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] are not supported.</span></span>  
  
 <span data-ttu-id="46e17-107">Lorsque les partitions distantes sont incluses dans un groupe de mesures, l'utilisation de la mémoire et de l'unité centrale du cube est répartie sur l'ensemble des partitions du groupe de mesures.</span><span class="sxs-lookup"><span data-stu-id="46e17-107">When remote partitions are included in a measure group, the memory and CPU utilization of the cube is distributed across all the partitions in the measure group.</span></span> <span data-ttu-id="46e17-108">Par exemple, lorsqu'une partition distante est traitée, seule ou dans le cadre du traitement de son cube parent, la mémoire et l'unité centrale sont essentiellement utilisées pour cette partition sur l'instance distante d'[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="46e17-108">For example, when a remote partition is processed, either alone or as part of parent cube processing, most of the memory and CPU utilization for that partition occurs on the remote instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="46e17-109">Un cube qui contient des partitions distantes peut contenir des dimensions activées en écriture ; cependant, ses performances peuvent en être affectées.</span><span class="sxs-lookup"><span data-stu-id="46e17-109">A cube that contains remote partitions can contain write-enabled dimensions; however, this may affect performance for the cube.</span></span> <span data-ttu-id="46e17-110">Pour plus d’informations sur les dimensions activées en écriture, consultez [Dimensions activées en écriture](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md).</span><span class="sxs-lookup"><span data-stu-id="46e17-110">For more information about write-enabled dimensions, see [Write-Enabled Dimensions](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md).</span></span>  
  
## <a name="storage-modes-for-remote-partitions"></a><span data-ttu-id="46e17-111">Modes de stockage des partitions distantes</span><span class="sxs-lookup"><span data-stu-id="46e17-111">Storage Modes for Remote Partitions</span></span>  
 <span data-ttu-id="46e17-112">Les partitions distantes peuvent recourir à tous les types de stockage utilisés par les partitions locales : MOLAP (OLAP multidimensionnel), HOLAP (OLAP hybride) ou ROLAP (OLAP relationnel).</span><span class="sxs-lookup"><span data-stu-id="46e17-112">Remote partitions may use any of the storage types used by local partitions: multidimensional OLAP (MOLAP), hybrid OLAP (HOLAP), or relational OLAP (ROLAP).</span></span> <span data-ttu-id="46e17-113">Les partitions distantes peuvent également utiliser la mise en cache proactive.</span><span class="sxs-lookup"><span data-stu-id="46e17-113">Remote partitions may also use proactive caching.</span></span> <span data-ttu-id="46e17-114">Les données stockées sur l'instance distante d'[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dépendent du mode de stockage appliqué à la partition distante.</span><span class="sxs-lookup"><span data-stu-id="46e17-114">Depending on the storage mode of a remote partition, the following data is stored on the remote instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="46e17-115">Type de stockage</span><span class="sxs-lookup"><span data-stu-id="46e17-115">Storage Type</span></span>|<span data-ttu-id="46e17-116">Données</span><span class="sxs-lookup"><span data-stu-id="46e17-116">Data</span></span>|  
|<span data-ttu-id="46e17-117">MOLAP</span><span class="sxs-lookup"><span data-stu-id="46e17-117">MOLAP</span></span>|<span data-ttu-id="46e17-118">Agrégations de la partition et une copie des données sources de la partition</span><span class="sxs-lookup"><span data-stu-id="46e17-118">The partition's aggregations and a copy of the partition's source data</span></span>|  
|<span data-ttu-id="46e17-119">HOLAP</span><span class="sxs-lookup"><span data-stu-id="46e17-119">HOLAP</span></span>|<span data-ttu-id="46e17-120">Agrégations des partitions</span><span class="sxs-lookup"><span data-stu-id="46e17-120">The partitions aggregations</span></span>|  
|<span data-ttu-id="46e17-121">ROLAP</span><span class="sxs-lookup"><span data-stu-id="46e17-121">ROLAP</span></span>|<span data-ttu-id="46e17-122">Pas de données de partition</span><span class="sxs-lookup"><span data-stu-id="46e17-122">No partition data</span></span>|  
  
 <span data-ttu-id="46e17-123">Si un groupe de mesures contient plusieurs partitions MOLAP ou HOLAP stockées sur plusieurs instances d'[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], le cube distribue les données du groupe de mesures entre ces instances d'[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="46e17-123">If a measure group contains multiple MOLAP or HOLAP partitions stored on multiple instances of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the cube distributes the data in the measure group data among those instances of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="merging-remote-partitions"></a><span data-ttu-id="46e17-124">Fusion des partitions distantes</span><span class="sxs-lookup"><span data-stu-id="46e17-124">Merging Remote Partitions</span></span>  
 <span data-ttu-id="46e17-125">Les partitions distantes peuvent être fusionnées uniquement avec d'autres partitions distantes qui sont stockées sur la même instance distante d'[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="46e17-125">Remote partitions can be merged only with other remote partitions that are stored on the same remote instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="46e17-126">Pour plus d’informations sur la fusion de partitions, consultez [fusionner des partitions dans Analysis Services &#40;SSAS-multidimensionnel&#41;](../multidimensional-models/merge-partitions-in-analysis-services-ssas-multidimensional.md).</span><span class="sxs-lookup"><span data-stu-id="46e17-126">For more information about merging partitions, see [Merge Partitions in Analysis Services &#40;SSAS - Multidimensional&#41;](../multidimensional-models/merge-partitions-in-analysis-services-ssas-multidimensional.md).</span></span>  
  
## <a name="archiving-and-restoring-remote-partitions"></a><span data-ttu-id="46e17-127">Archivage et restauration des partitions distantes</span><span class="sxs-lookup"><span data-stu-id="46e17-127">Archiving and Restoring Remote Partitions</span></span>  
 <span data-ttu-id="46e17-128">Les données des partitions distantes peuvent être archivées ou restaurées lorsque la base de données qui stocke la partition distante est archivée ou restaurée.</span><span class="sxs-lookup"><span data-stu-id="46e17-128">Data in remote partitions can be archived or restored when the database that stores the remote partition is archived or restored.</span></span> <span data-ttu-id="46e17-129">Si vous restaurez une base de données sans restaurer une partition distante, vous devez traiter la partition distante avant d'utiliser les données de la partition.</span><span class="sxs-lookup"><span data-stu-id="46e17-129">If you restore a database without restoring a remote partition, you must process the remote partition before you can use the data in the partition.</span></span> <span data-ttu-id="46e17-130">Pour plus d’informations sur l’archivage et la restauration de bases de données, consultez [sauvegarde et restauration des bases de données Analysis Services](../multidimensional-models/backup-and-restore-of-analysis-services-databases.md).</span><span class="sxs-lookup"><span data-stu-id="46e17-130">For more information about archiving and restoring databases, see [Backup and Restore of Analysis Services Databases](../multidimensional-models/backup-and-restore-of-analysis-services-databases.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46e17-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46e17-131">See Also</span></span>  
 <span data-ttu-id="46e17-132">[Créer et gérer une partition distante &#40;Analysis Services&#41;](../multidimensional-models/create-and-manage-a-remote-partition-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="46e17-132">[Create and Manage a Remote Partition &#40;Analysis Services&#41;](../multidimensional-models/create-and-manage-a-remote-partition-analysis-services.md) </span></span>  
 [<span data-ttu-id="46e17-133">Traitement des objets Analysis Services</span><span class="sxs-lookup"><span data-stu-id="46e17-133">Processing Analysis Services Objects</span></span>](../multidimensional-models/processing-analysis-services-objects.md)  
  
  