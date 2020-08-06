---
title: Integration Services (SSIS) dans un cluster | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 0216266d-d866-4ea2-bbeb-955965f4d7c2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 450553e97713c0acba329e5874932f1fdedee310
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704287"
---
# <a name="integration-services-ssis-in-a-cluster"></a><span data-ttu-id="8b067-102">Integration Services (SSIS) dans un cluster</span><span class="sxs-lookup"><span data-stu-id="8b067-102">Integration Services (SSIS) in a Cluster</span></span>
  <span data-ttu-id="8b067-103">Le clustering [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] n’est pas recommandé, car le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] n’est pas un service cluster ou prenant en charge les clusters. De plus, il ne prend pas en charge le basculement d’un nœud de cluster à un autre.</span><span class="sxs-lookup"><span data-stu-id="8b067-103">Clustering [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] is not recommended because the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service is not a clustered or cluster-aware service, and does not support failover from one cluster node to another.</span></span> <span data-ttu-id="8b067-104">Par conséquent, dans un environnement cluster, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] doit être installé et démarré en tant que service autonome sur chaque nœud du cluster.</span><span class="sxs-lookup"><span data-stu-id="8b067-104">Therefore, in a clustered environment, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] should be installed and started as a stand-alone service on each node in the cluster.</span></span>  
  
 <span data-ttu-id="8b067-105">Même si le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] n’est pas un service cluster, vous pouvez le configurer manuellement pour qu’il fonctionne en tant que ressource de cluster après avoir installé séparément [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur chaque nœud du cluster.</span><span class="sxs-lookup"><span data-stu-id="8b067-105">Although the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service is not a clustered service, you can manually configure the service to operate as a cluster resource after you install [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] separately on each node of the cluster.</span></span>  
  
 <span data-ttu-id="8b067-106">Toutefois, si en mettant en place un environnement matériel cluster, votre objectif est de bénéficier d'une haute disponibilité, vous pouvez y parvenir sans configurer le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] en tant que ressource de cluster.</span><span class="sxs-lookup"><span data-stu-id="8b067-106">However, if high availability is your goal in establishing a clustered hardware environment, you can achieve this goal without configuring the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service as a cluster resource.</span></span>  <span data-ttu-id="8b067-107">Pour gérer vos packages sur n’importe quel nœud du cluster à partir de n’importe quel nœud du cluster, modifiez le fichier de configuration du service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur chaque nœud du cluster.</span><span class="sxs-lookup"><span data-stu-id="8b067-107">To manage your packages on any node in the cluster from any other node in the cluster, modify the configuration file for the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service on each node in the cluster.</span></span> <span data-ttu-id="8b067-108">Vous modifiez chacun des fichiers de configuration pour pointer vers toutes les instances disponibles de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur lesquelles les packages sont stockés.</span><span class="sxs-lookup"><span data-stu-id="8b067-108">You modify each of these configuration files to point to all available instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on which packages are stored.</span></span> <span data-ttu-id="8b067-109">Cette solution apporte la haute disponibilité dont la plupart des clients ont besoin, sans les problèmes potentiels rencontrés lorsque le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est configuré en tant que ressource de cluster.</span><span class="sxs-lookup"><span data-stu-id="8b067-109">This solution provides the high availability that most customers need, without the potential problems encountered when the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service is configured as a cluster resource.</span></span> <span data-ttu-id="8b067-110">Pour plus d’informations sur la modification du fichier de configuration, consultez [Configuration du service Integration Services &#40;Service SSIS&#41;](integration-services-service-ssis-service.md).</span><span class="sxs-lookup"><span data-stu-id="8b067-110">For more information about how to change the configuration file, see [Configuring the Integration Services Service &#40;SSIS Service&#41;](integration-services-service-ssis-service.md)</span></span>  
  
 <span data-ttu-id="8b067-111">Il est essentiel de comprendre le rôle du service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pour prendre une décision informée sur la configuration du service dans un environnement cluster.</span><span class="sxs-lookup"><span data-stu-id="8b067-111">Understanding the role of the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service is critical to making an informed decision about how to configure the service in a clustered environment.</span></span> <span data-ttu-id="8b067-112">Pour plus d’informations, consultez [Service Integration Services &#40;Service SSIS&#41;](integration-services-service-ssis-service.md).</span><span class="sxs-lookup"><span data-stu-id="8b067-112">For more information, see [Integration Services Service &#40;SSIS Service&#41;](integration-services-service-ssis-service.md).</span></span>  
  
## <a name="understanding-the-disadvantages-of-configuring-integration-services-as-a-cluster-resource"></a><span data-ttu-id="8b067-113">Inconvénients de la configuration d'Integration Services en tant que ressource de cluster</span><span class="sxs-lookup"><span data-stu-id="8b067-113">Understanding the Disadvantages of Configuring Integration Services as a Cluster Resource</span></span>  
 <span data-ttu-id="8b067-114">La configuration du service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] en tant que ressource de cluster présente certains inconvénients potentiels, indiqués ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="8b067-114">Some of the potential disadvantages of configuring the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service as a cluster resource include the following:</span></span>  
  
-   <span data-ttu-id="8b067-115">Lorsqu'un basculement a lieu, l'exécution des packages ne redémarre pas.</span><span class="sxs-lookup"><span data-stu-id="8b067-115">When a failover occurs, running packages do not restart.</span></span> <span data-ttu-id="8b067-116">Vous pouvez récupérer des échecs de package en redémarrant les packages à partir des points de contrôle.</span><span class="sxs-lookup"><span data-stu-id="8b067-116">You can recover from package failures by restarting packages from checkpoints.</span></span> <span data-ttu-id="8b067-117">Vous pouvez effectuer le redémarrage à partir des points de contrôle sans configurer le service en tant que ressource de cluster.</span><span class="sxs-lookup"><span data-stu-id="8b067-117">You can restart from checkpoints without configuring the service as a cluster resource.</span></span> <span data-ttu-id="8b067-118">Pour plus d'informations, consultez [Redémarrer des packages à l'aide de points de contrôle](../packages/restart-packages-by-using-checkpoints.md).</span><span class="sxs-lookup"><span data-stu-id="8b067-118">For more information, see [Restart Packages by Using Checkpoints](../packages/restart-packages-by-using-checkpoints.md).</span></span>  
  
-   <span data-ttu-id="8b067-119">Lorsque vous configurez le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] dans un groupe de ressources différent de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous ne pouvez pas utiliser [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] à partir d’ordinateurs clients pour gérer les packages stockés dans la base de données msdb.</span><span class="sxs-lookup"><span data-stu-id="8b067-119">When you configure the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service in a different resource group from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you cannot use [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] from client computers to manage packages that are stored in the msdb database.</span></span> <span data-ttu-id="8b067-120">Le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ne peut pas déléguer d’informations d’identification dans ce scénario à deux tronçons.</span><span class="sxs-lookup"><span data-stu-id="8b067-120">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service cannot delegate credentials in this double-hop scenario.</span></span>  
  
-   <span data-ttu-id="8b067-121">Lorsque plusieurs groupes de ressources [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] incluent le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] dans un cluster, un basculement peut avoir des résultats inattendus.</span><span class="sxs-lookup"><span data-stu-id="8b067-121">When you have multiple [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resource groups that include the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service in a cluster, a failover could lead to unexpected results.</span></span> <span data-ttu-id="8b067-122">Considérons le scénario suivant.</span><span class="sxs-lookup"><span data-stu-id="8b067-122">Consider the following scenario.</span></span> <span data-ttu-id="8b067-123">Groupe1, qui inclut le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , s’exécute sur le Nœud A. Groupe2, qui inclut également le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , s’exécute sur le Nœud B. Groupe2 bascule sur le Nœud A. La tentative de démarrage d’une autre instance du service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur le Nœud A échoue, car le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est un service à instance unique.</span><span class="sxs-lookup"><span data-stu-id="8b067-123">Group1, which includes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service and the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service, is running on Node A. Group2, which also includes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service and the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service, is running on Node B. Group 2 fails over to Node A. The attempt to start another instance of the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service on Node A fails because the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service is a single-instance service.</span></span> <span data-ttu-id="8b067-124">Le fait que le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] essayant de basculer sur le Nœud A échoue également ou non dépend de la configuration du service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] dans Groupe2.</span><span class="sxs-lookup"><span data-stu-id="8b067-124">Whether the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service that is trying to fail over to Node A also fails depends on the configuration of the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service in Group 2.</span></span> <span data-ttu-id="8b067-125">Si le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] a été configuré pour affecter les autres services dans le groupe de ressources, le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui procède au basculement échouera car le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] a échoué.</span><span class="sxs-lookup"><span data-stu-id="8b067-125">If the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service was configured to affect the other services in the resource group, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service that is failing over will fail because the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service failed.</span></span> <span data-ttu-id="8b067-126">Si le service a été configuré pour ne pas affecter les autres services dans le groupe de ressources, le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pourra basculer sur le Nœud A. À moins que le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] dans Groupe2 n’ait été configuré pour ne pas affecter les autres services dans le groupe de ressources, l’échec du service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui procède au basculement peut aussi provoquer l’échec du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui procède au basculement.</span><span class="sxs-lookup"><span data-stu-id="8b067-126">If the service was configured not to affect the other services in the resource group, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service will be able to fail over to Node A.Unless the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service in Group 2 was configured not to affect the other services in the resource group, the failure of the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service that is failing over could cause the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service that is failing over to fail also.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="8b067-127">Tâches associées</span><span class="sxs-lookup"><span data-stu-id="8b067-127">Related Tasks</span></span>  
 <span data-ttu-id="8b067-128">Pour obtenir des instructions détaillées sur la configuration du service Integration Services dans un cluster, consultez [Configurer le service Integration Services en tant que ressource de cluster](../configure-the-integration-services-service-as-a-cluster-resource.md).</span><span class="sxs-lookup"><span data-stu-id="8b067-128">For step-by-step instructions on configuring the Integration Services service in a cluster, see [Configure the Integration Services Service as a Cluster Resource](../configure-the-integration-services-service-as-a-cluster-resource.md).</span></span>  
  
  