---
title: Récupération d’urgence WSFC par le quorum forcé (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- quorum [SQL Server], AlwaysOn and WSFC quorum
- failover clustering [SQL Server], AlwaysOn Availability Groups
ms.assetid: 6cefdc18-899e-410c-9ae4-d6080f724046
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b2c9399472c6e67c9e2121a008f9283ba05943da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605001"
---
# <a name="wsfc-disaster-recovery-through-forced-quorum-sql-server"></a><span data-ttu-id="9ca3c-102">Récupération d'urgence WSFC par le quorum forcé (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9ca3c-102">WSFC Disaster Recovery through Forced Quorum (SQL Server)</span></span>
  <span data-ttu-id="9ca3c-103">L'échec du quorum est généralement dû à un problème systémique grave, à un échec de communication persistant ou à une mauvaise configuration impliquant plusieurs nœuds dans le cluster WSFC.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-103">Quorum failure is usually caused by a systemic disaster, or a persistent communications failure, or a misconfiguration involving several nodes in the WSFC cluster.</span></span>  <span data-ttu-id="9ca3c-104">Une intervention manuelle est nécessaire pour la récupération d'une défaillance de quorum.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-104">Manual intervention is required to recovery from a quorum failure.</span></span>  
  
-   <span data-ttu-id="9ca3c-105">**Avant de commencer :**  [Conditions préalables](#Prerequisites), [Sécurité](#Security)</span><span class="sxs-lookup"><span data-stu-id="9ca3c-105">**Before you start:**  [Prerequisites](#Prerequisites), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="9ca3c-106">**Procédure de récupération d'urgence WSFC par le quorum forcé** [Procédure de récupération d'urgence WSFC par le quorum forcé](#Main)</span><span class="sxs-lookup"><span data-stu-id="9ca3c-106">**WSFC Disaster Recovery through the Forced Quorum Procedure** [WSFC Disaster Recovery through the Forced Quorum Procedure](#Main)</span></span>  
  
-   [<span data-ttu-id="9ca3c-107">Tâches associées</span><span class="sxs-lookup"><span data-stu-id="9ca3c-107">Related Tasks</span></span>](#RelatedTasks)  
  
-   [<span data-ttu-id="9ca3c-108">Contenu connexe</span><span class="sxs-lookup"><span data-stu-id="9ca3c-108">Related Content</span></span>](#RelatedContent)  
  
##  <a name="before-you-start"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9ca3c-109">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="9ca3c-109">Before You Start</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="9ca3c-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="9ca3c-110">Prerequisites</span></span>  
 <span data-ttu-id="9ca3c-111">La procédure de quorum forcé suppose qu'un quorum sain existait avant l'échec de quorum.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-111">The Forced Quorum Procedure assumes that a healthy quorum existed before the quorum failure.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="9ca3c-112">L'utilisateur doit bien connaître les concepts et les interactions du clustering de basculement Windows Server, des modèles de quorum WSFC, de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]et de la configuration de déploiement spécifique à l'environnement.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-112">The user should be well-informed on the concepts and interactions of Windows Server Failover Clustering, WSFC Quorum Models, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], and the environment's specific deployment configuration.</span></span>  
>   
>  <span data-ttu-id="9ca3c-113">Pour plus d’informations, consultez :  [Clustering de basculement Windows Server (WSFC) avec SQL Server](https://msdn.microsoft.com/library/hh270278\(v=SQL.110\).aspx), [Modes de quorum WSFC et configuration de vote (SQL Server)](https://msdn.microsoft.com/library/hh270280\(v=SQL.110\).aspx).</span><span class="sxs-lookup"><span data-stu-id="9ca3c-113">For more information, see:  [Windows Server Failover Clustering (WSFC) with SQL Server](https://msdn.microsoft.com/library/hh270278\(v=SQL.110\).aspx), [WSFC Quorum Modes and Voting Configuration (SQL Server)](https://msdn.microsoft.com/library/hh270280\(v=SQL.110\).aspx)</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9ca3c-114">Sécurité</span><span class="sxs-lookup"><span data-stu-id="9ca3c-114">Security</span></span>  
 <span data-ttu-id="9ca3c-115">L'utilisateur doit être un compte de domaine qui est membre du groupe Administrateurs local sur chaque nœud du cluster WSFC.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-115">The user must be a domain account that is member of the local Administrators group on each node of the WSFC cluster.</span></span>  
  
##  <a name="wsfc-disaster-recovery-through-the-forced-quorum-procedure"></a><a name="Main"></a> <span data-ttu-id="9ca3c-116">Récupération d'urgence WSFC par le quorum forcé</span><span class="sxs-lookup"><span data-stu-id="9ca3c-116">WSFC Disaster Recovery through the Forced Quorum Procedure</span></span>  
 <span data-ttu-id="9ca3c-117">N'oubliez pas qu'un échec de quorum met hors ligne tous les services cluster, toutes les instances SQL Server et [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]dans le cluster WSFC, car le cluster, tel que configuré, ne peut pas garantir la tolérance de panne au niveau du nœud.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-117">Remember that quorum failure will cause all clustered services, SQL Server instances, and [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], in the WSFC cluster to be set offline, because the cluster, as configured, cannot ensure node-level fault tolerance.</span></span>  <span data-ttu-id="9ca3c-118">Un échec de quorum signifie que les nœuds votants sains dans le cluster WSFC ne satisfont plus le modèle de quorum.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-118">A quorum failure means that healthy voting nodes in the WSFC cluster no longer satisfy the quorum model.</span></span> <span data-ttu-id="9ca3c-119">Certains nœuds ont peut-être échoué complètement, et d'autres ont peut-être simplement arrêté le service WSFC et sont sains par ailleurs, sauf en ce qui concerne la perte de la capacité de communiquer avec un quorum.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-119">Some nodes may have failed completely, and some may have just shut down the WSFC service and are otherwise healthy, except for the loss of the ability to communicate with a quorum.</span></span>  
  
 <span data-ttu-id="9ca3c-120">Pour remettre le cluster WSFC en ligne, vous devez corriger la cause première de l'échec de quorum dans la configuration existante, récupérer les bases de données concernées si nécessaire et, éventuellement, reconfigurer les nœuds restants dans le cluster WSFC pour refléter la topologie de cluster survivante.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-120">To bring the WSFC cluster back online, you must correct the root cause of the quorum failure under the existing configuration, recover the affected databases as needed, and you may want to reconfigure the remaining nodes in the WSFC cluster to reflect the surviving cluster topology.</span></span>  
  
 <span data-ttu-id="9ca3c-121">Vous pouvez utiliser la procédure de *quorum forcé* sur un nœud de cluster WSFC pour remplacer les contrôles de sécurité qui ont mis le cluster hors connexion.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-121">You can use the *forced quorum* procedure on a WSFC cluster node to override the safety controls that took the cluster offline.</span></span>  <span data-ttu-id="9ca3c-122">Cela est efficace pour indiquer au cluster d'interrompre les contrôles de vote du quorum et vous permet de remettre en ligne les ressources du cluster WSFC et SQL Server sur tous les nœuds dans le cluster.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-122">This effectively tells the cluster to suspend the quorum voting checks, and lets you bring the WSFC cluster resources and SQL Server back online on any of the nodes in the cluster.</span></span>  
  
 <span data-ttu-id="9ca3c-123">Ce type de processus de récupération d'urgence doit inclure les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="9ca3c-123">This type of disaster recovery process should include the following steps:</span></span>  
  
#### <a name="to-recover-from-quorum-failure"></a><span data-ttu-id="9ca3c-124">Pour une récupération en cas d'échec de quorum :</span><span class="sxs-lookup"><span data-stu-id="9ca3c-124">To Recover from Quorum Failure:</span></span>  
  
1.  <span data-ttu-id="9ca3c-125">**Déterminez l'étendue de l'échec.**</span><span class="sxs-lookup"><span data-stu-id="9ca3c-125">**Determine the scope of the failure.**</span></span> <span data-ttu-id="9ca3c-126">Identifiez les groupes de disponibilité ou les instances de SQL Server non sensibles et les nœuds du cluster qui sont en ligne et disponibles à l'utilisation post-incident, puis examinez les journaux des événements Windows et les journaux système de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-126">Identify which availability groups or SQL Server instances are non-responsive, which cluster nodes are online and available for post-disaster use, and examine the Windows event logs and the SQL Server system logs.</span></span>  <span data-ttu-id="9ca3c-127">Si possible, vous devez conserver les données d'analyse et les journaux système pour les examiner ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-127">Where practical, you should preserve forensic data and system logs for later analysis.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="9ca3c-128">Sur une instance de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]qui répond, vous pouvez obtenir des informations sur l’état d’intégrité des groupes de disponibilité qui possèdent un réplica de disponibilité sur l’instance de serveur local en interrogeant la vue de gestion dynamique (DMV) [sys.dm_hadr_availability_group_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-group-states-transact-sql) .</span><span class="sxs-lookup"><span data-stu-id="9ca3c-128">On a responsive instance of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], you can obtain information about the health of availability groups that possess an availability replica on the local server instance by querying the [sys.dm_hadr_availability_group_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-group-states-transact-sql) dynamic management view (DMV).</span></span>  
  
2.  <span data-ttu-id="9ca3c-129">**Démarrez le cluster WSFC en utilisant le quorum forcé sur un nœud unique.**</span><span class="sxs-lookup"><span data-stu-id="9ca3c-129">**Start the WSFC cluster by using forced quorum on a single node.**</span></span> <span data-ttu-id="9ca3c-130">Identifiez un nœud avec un nombre minime de défaillances de composant, autre que celui qui a arrêté le service de cluster WSFC.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-130">Identify a node with a minimal number of component failures, other than that the WSFC cluster service was shut down.</span></span>  <span data-ttu-id="9ca3c-131">Vérifiez que ce nœud peut communiquer avec la majorité des autres nœuds.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-131">Verify that this node can communicate with a majority of the other nodes.</span></span>  
  
     <span data-ttu-id="9ca3c-132">Sur ce nœud, forcez manuellement la mise en ligne du cluster à l'aide de la procédure de quorum forcé.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-132">On this node, manually force the cluster to come online using the forced quorum procedure.</span></span>  <span data-ttu-id="9ca3c-133">Pour réduire au minimum la perte de données, sélectionnez le dernier nœud qui hébergeait un réplica principal de groupe de disponibilité.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-133">To minimize potential data loss, select a node that was last hosting an availability group primary replica.</span></span>  
  
     <span data-ttu-id="9ca3c-134">Pour plus d'informations, consultez :  [Forcer un cluster WSFC à démarrer sans quorum](https://msdn.microsoft.com/library/hh270275\(v=SQL.110\).aspx)</span><span class="sxs-lookup"><span data-stu-id="9ca3c-134">For more information, see:  [Force a WSFC Cluster to Start Without a Quorum](https://msdn.microsoft.com/library/hh270275\(v=SQL.110\).aspx)</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9ca3c-135">L'application d'un quorum forcé bloque les contrôles de quorum sur l'ensemble du cluster jusqu'à ce que le cluster WSFC logique atteigne une majorité des votes et passe automatiquement à un mode d'opération de quorum standard.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-135">The forced quorum setting has a cluster-wide affect to block quorum checks until the logical WSFC cluster achieves a majority of votes and automatically transitions to a regular quorum mode of operation.</span></span>  
  
3.  <span data-ttu-id="9ca3c-136">**Démarrez le service WSFC normalement sur chaque nœud par ailleurs sain, en procédant avec un nœud à la fois.**</span><span class="sxs-lookup"><span data-stu-id="9ca3c-136">**Start the WSFC service normally on each otherwise healthy node, one at a time.**</span></span> <span data-ttu-id="9ca3c-137">Vous ne devez pas spécifier l'option de quorum forcé lorsque vous démarrez le service de cluster sur les autres nœuds.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-137">You do not have to specify the forced quorum option when you start the cluster service on the other nodes.</span></span>  
  
     <span data-ttu-id="9ca3c-138">Lorsque le service WSFC revient en ligne sur chaque nœud, il négocie avec les autres nœuds sains pour synchroniser le nouvel état de configuration du cluster.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-138">As the WSFC service on each node comes back online, it negotiates with the other healthy nodes to synchronize the new cluster configuration state.</span></span>  <span data-ttu-id="9ca3c-139">N'oubliez pas d'effectuer ces opérations sur un nœud à la fois, afin d'éviter des conditions potentielles de concurrence lors de la résolution du dernier état connu du cluster.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-139">Remember to do this one node at a time to prevent potential race conditions in resolving the last known state of the cluster.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="9ca3c-140">Vérifiez que chaque nœud que vous démarrez peut communiquer avec les autres nœuds récemment mis en ligne.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-140">Ensure that each node that you start can communicate with the other newly online nodes.</span></span>  <span data-ttu-id="9ca3c-141">Éventuellement, désactivez le service WSFC sur les autres nœuds.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-141">Consider disabling the WSFC service on the other nodes.</span></span>  <span data-ttu-id="9ca3c-142">Sinon, vous courez le risque de créer plusieurs jeux de nœuds de quorum et de créer un scénario de fractionnement des partitions.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-142">Otherwise,  you run the risk of creating more than one quorum node set; that is a split-brain scenario.</span></span> <span data-ttu-id="9ca3c-143">Si vos résultats à l'étape 1 étaient précis, cela ne devrait pas se produire.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-143">If your findings in step 1 were accurate, this should not occur.</span></span>  
  
4.  <span data-ttu-id="9ca3c-144">**Appliquez le nouveau mode de quorum et la nouvelle configuration de vote des nœuds.**</span><span class="sxs-lookup"><span data-stu-id="9ca3c-144">**Apply new quorum mode and node vote configuration.**</span></span> <span data-ttu-id="9ca3c-145">Si l'application forcée d'un quorum a redémarré tous les nœuds du cluster et la cause première de l'échec de quorum a été corrigée, le mode de quorum d'origine et la configuration de vote des nœuds n'ont pas besoin d'être modifiés.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-145">If forcing quorum successfully restarted all the nodes in the cluster and the root cause of the quorum failure has been corrected, changes to the original quorum mode and node vote configuration are unnecessary.</span></span>  
  
     <span data-ttu-id="9ca3c-146">Sinon, vous devez évaluer la topologie de nœud de cluster et de réplica de disponibilité nouvellement créée et modifier le mode de quorum et les affectations de vote pour chaque nœud, comme il convient.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-146">Otherwise, you should evaluate the newly recovered cluster node and availability replica topology, and change the quorum mode and vote assignments for each node as appropriate.</span></span> <span data-ttu-id="9ca3c-147">Les nœuds non récupérés doivent être mis hors connexion, ou bien leurs votes de nœud doivent être définis sur zéro.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-147">Un-recovered nodes should be set offline or have their node votes set to zero.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="9ca3c-148">À ce stade, les nœuds et les instances de SQL Server dans le cluster peuvent apparaître comme restaurés et sembler fonctionner normalement.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-148">At this point, the nodes and SQL Server instances in the cluster may appear to be restored back to regular operation.</span></span>  <span data-ttu-id="9ca3c-149">Toutefois, il est possible qu'il n'y ait pas encore de quorum sain.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-149">However, a healthy quorum may still not exist.</span></span>  <span data-ttu-id="9ca3c-150">À l'aide du Gestionnaire du cluster de basculement, ou du Tableau de bord AlwaysOn dans SQL Server Management Studio, ou des vues DMV appropriées, vérifiez qu'un quorum a été restauré.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-150">Using the Failover Cluster Manager, or the AlwaysOn Dashboard within SQL Server Management Studio, or the appropriate DMVs, verify that a quorum has been restored.</span></span>  
  
5.  <span data-ttu-id="9ca3c-151">**Récupérez les réplicas de base de données du groupe de disponibilité si nécessaire.**</span><span class="sxs-lookup"><span data-stu-id="9ca3c-151">**Recover availability group database replicas as needed.**</span></span> <span data-ttu-id="9ca3c-152">Les bases de données qui n'appartiennent pas au groupe de disponibilité doivent être restaurées et remises en ligne au cours du processus de démarrage normal de SQL Server, sans autre intervention.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-152">Non-availability group databases should recover and come back online on their own as part of the regular SQL Server startup process.</span></span>  
  
     <span data-ttu-id="9ca3c-153">Vous pouvez minimiser la perte potentielle de données et le temps de récupération pour les réplicas de groupe de disponibilité en les remettant en ligne dans cette séquence : réplica principal, réplicas secondaires synchrones, réplicas secondaires asynchrones.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-153">You can minimize potential data loss and recovery time for the availability group replicas by bringing them back online in this sequence:  primary replica, synchronous secondary replicas, asynchronous secondary replicas.</span></span>  
  
6.  <span data-ttu-id="9ca3c-154">**Réparez ou remplacez les composants en échec et re-validez le cluster.**</span><span class="sxs-lookup"><span data-stu-id="9ca3c-154">**Repair or replace failed components and re-validate cluster.**</span></span> <span data-ttu-id="9ca3c-155">Maintenant que vous avez récupéré le sinsitre et l'échec de quorum, vous devez réparer ou remplacer les nœuds ayant échoué et modifier les configurations WSFC et AlwaysOn relatives en conséquence.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-155">Now that you have recovered from the initial disaster and quorum failure, you should repair or replace the failed nodes and adjust related WSFC and AlwaysOn configurations accordingly.</span></span>  <span data-ttu-id="9ca3c-156">Cela peut inclure la suppression des réplicas de groupe de disponibilité, l'éviction des nœuds du cluster ou la mise à plat et la réinstallation des logiciels sur un nœud.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-156">This can include dropping availability group replicas, evicting nodes from the cluster, or flattening and re-installing software on a node.</span></span>  
  
     <span data-ttu-id="9ca3c-157">Vous devez réparer ou supprimer tous les réplicas de disponibilité.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-157">You must repair or remove all failed availability replicas.</span></span>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="9ca3c-158">ne tronquera pas le journal des transactions après le dernier point connu du réplica de disponibilité le plus lointain.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-158">will not truncate the transaction log past the last known point of the farthest behind availability replica.</span></span>   <span data-ttu-id="9ca3c-159">Si un réplica n'est pas réparé ou n'est pas supprimé du groupe de disponibilité, les journaux des transactions vont prendre du volume et vous allez courir le risque de manquer d'espace pour les autres réplicas.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-159">If a failed replica is not repaired or removed from the availability group, the transaction logs will grow and you will run the risk of running out of transaction log space on the other replicas.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9ca3c-160">Si vous exécutez l'Assistant WSFC Valider une configuration alors qu'un écouteur du groupe de disponibilité existe sur le cluster WSFC, l'Assistant génère le message d'avertissement incorrect suivant :</span><span class="sxs-lookup"><span data-stu-id="9ca3c-160">If you run the WSFC Validate a Configuration Wizard when an availability group listener exists on the WSFC cluster, the wizard generates the following incorrect warning message:</span></span>  
    >   
    >  <span data-ttu-id="9ca3c-161">« La propriété RegisterAllProviderIP du nom réseau 'Name:<nom_réseau>' est définie sur 1. Pour la configuration de cluster actuelle, cette valeur doit être définie sur 0. »</span><span class="sxs-lookup"><span data-stu-id="9ca3c-161">"The RegisterAllProviderIP property for network name 'Name:<network_name>' is set to 1 For the current cluster configuration this value should be set to 0."</span></span>  
    >   
    >  <span data-ttu-id="9ca3c-162">Veuillez ignorer ce message.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-162">Please ignore this message.</span></span>  
  
7.  <span data-ttu-id="9ca3c-163">**Répétez l'étape 4 si nécessaire.**</span><span class="sxs-lookup"><span data-stu-id="9ca3c-163">**Repeat step 4 as needed.**</span></span> <span data-ttu-id="9ca3c-164">L'objectif est de rétablir le niveau de la tolérance de panne approprié et une haute disponibilité pour des opérations saines.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-164">The goal is to re-establish the appropriate level of fault tolerance and high availability for healthy operations.</span></span>  
  
8.  <span data-ttu-id="9ca3c-165">**Effectuez une analyse RPO/RTO.**</span><span class="sxs-lookup"><span data-stu-id="9ca3c-165">**Conduct RPO/RTO analysis.**</span></span> <span data-ttu-id="9ca3c-166">Vous devez analyser les journaux système SQL Server, les horodateurs de base de données et les journaux des événements Windows pour déterminer la cause première de l'échec et pour documenter les expériences de point et de temps de récupération actuelles.</span><span class="sxs-lookup"><span data-stu-id="9ca3c-166">You should analyze SQL Server system logs, database timestamps, and Windows event logs to determine root cause of the failure, and to document actual recovery point and recovery time experiences.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="9ca3c-167">Tâches associées</span><span class="sxs-lookup"><span data-stu-id="9ca3c-167">Related Tasks</span></span>  
  
-   [<span data-ttu-id="9ca3c-168">Forcer un cluster WSFC à démarrer sans quorum</span><span class="sxs-lookup"><span data-stu-id="9ca3c-168">Force a WSFC Cluster to Start Without a Quorum</span></span>](force-a-wsfc-cluster-to-start-without-a-quorum.md)  
  
-   [<span data-ttu-id="9ca3c-169">Effectuer un basculement manuel forcé d’un groupe de disponibilité &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9ca3c-169">Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;</span></span>](../../../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="9ca3c-170">Afficher les paramètres NodeWeight pour le quorum de cluster</span><span class="sxs-lookup"><span data-stu-id="9ca3c-170">View Cluster Quorum NodeWeight Settings</span></span>](view-cluster-quorum-nodeweight-settings.md)  
  
-   [<span data-ttu-id="9ca3c-171">Configurer les paramètres NodeWeight pour un quorum de cluster</span><span class="sxs-lookup"><span data-stu-id="9ca3c-171">Configure Cluster Quorum NodeWeight Settings</span></span>](configure-cluster-quorum-nodeweight-settings.md)  
  
-   [<span data-ttu-id="9ca3c-172">Utiliser le tableau de bord Always On &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="9ca3c-172">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md) 
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="9ca3c-173">Contenu associé</span><span class="sxs-lookup"><span data-stu-id="9ca3c-173">Related Content</span></span>  
  
-   <span data-ttu-id="9ca3c-174">[Afficher les événements et journaux pour un cluster de basculement](https://technet.microsoft.com/library/cc772342\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="9ca3c-174">[View Events and Logs for a Failover Cluster](https://technet.microsoft.com/library/cc772342\(WS.10\).aspx)</span></span>  
  
-   [<span data-ttu-id="9ca3c-175">Applets de commande de cluster de basculement Get-ClusterLog</span><span class="sxs-lookup"><span data-stu-id="9ca3c-175">Get-ClusterLog Failover Cluster Cmdlet</span></span>](https://technet.microsoft.com/library/ee461045.aspx)  
  
## <a name="see-also"></a><span data-ttu-id="9ca3c-176">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ca3c-176">See Also</span></span>  
 [<span data-ttu-id="9ca3c-177">Clustering de basculement Windows Server &#40;WSFC&#41; avec SQL Server</span><span class="sxs-lookup"><span data-stu-id="9ca3c-177">Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server</span></span>](windows-server-failover-clustering-wsfc-with-sql-server.md)  
  
  