---
title: Configurer des instances du moteur de base de données (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 84e36fcb-2c78-48e8-8e4b-bf784a3ee557
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: af7408ff66d1f0e41369ba095ce51ea590d316e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87614849"
---
# <a name="configure-database-engine-instances-sql-server"></a><span data-ttu-id="0554e-102">Configurer des instances du moteur de base de données (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0554e-102">Configure Database Engine Instances (SQL Server)</span></span>
  <span data-ttu-id="0554e-103">Chaque instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] doit être configurée pour répondre aux exigences en matière de performances et de disponibilité définies pour les bases de données hébergées par l'instance.</span><span class="sxs-lookup"><span data-stu-id="0554e-103">Each instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] must be configured to meet the performance and availability requirements defined for the databases hosted by the instance.</span></span> <span data-ttu-id="0554e-104">Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] comprend des options de configuration qui contrôlent des comportements (tels que l'utilisation des ressources) et la disponibilité de fonctionnalités (telles que l'audit ou la récursivité des déclencheurs).</span><span class="sxs-lookup"><span data-stu-id="0554e-104">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] includes configuration options that control behaviors such as resource usage and the availability of features such as auditing or trigger recursion.</span></span>  
  
## <a name="instance-configuration"></a><span data-ttu-id="0554e-105">Configuration de l'instance</span><span class="sxs-lookup"><span data-stu-id="0554e-105">Instance Configuration</span></span>  
 <span data-ttu-id="0554e-106">Lorsqu'une base de données est déployée dans l'environnement de production, il existe souvent un contrat de niveau de service (SLA) qui définit des zones telles que les niveaux de performances requis de la base de données et le niveau de disponibilité requis de la base de données.</span><span class="sxs-lookup"><span data-stu-id="0554e-106">When a database is deployed into production there is often a service level agreement (SLA) defining areas such as the levels of performance required from the database and the required availability level of the database.</span></span> <span data-ttu-id="0554e-107">Les termes du contrat de niveau de service définissent généralement les exigences de configuration pour l'instance.</span><span class="sxs-lookup"><span data-stu-id="0554e-107">The terms of the SLA typically drive configuration requirements for the instance.</span></span>  
  
 <span data-ttu-id="0554e-108">Une instance est généralement configurée dès son installation terminée.</span><span class="sxs-lookup"><span data-stu-id="0554e-108">An instance is usually configured immediately after it has been installed.</span></span> <span data-ttu-id="0554e-109">La configuration initiale est généralement déterminée par les exigences du contrat de niveau de service concernant les types de bases de données dont le déploiement sur l'instance est planifié.</span><span class="sxs-lookup"><span data-stu-id="0554e-109">The initial configuration is usually determined by the SLA requirements of the types of databases planned to be deployed to the instance.</span></span> <span data-ttu-id="0554e-110">Une fois les bases de données déployées, les administrateurs de base de données surveillent les performances de l'instance et règlent les paramètres de configuration en conséquence si les métriques de performances indiquent que l'instance ne répond pas aux spécifications du contrat de niveau de service.</span><span class="sxs-lookup"><span data-stu-id="0554e-110">After the databases have been deployed, the database administrators monitor the performance of the instance and adjust the configuration settings as needed if the performance metrics show the instance is not meeting the SLA requirements.</span></span>  
  
## <a name="configuration-tasks"></a><span data-ttu-id="0554e-111">Tâches de configuration</span><span class="sxs-lookup"><span data-stu-id="0554e-111">Configuration Tasks</span></span>  
  
|<span data-ttu-id="0554e-112">Description de la tâche</span><span class="sxs-lookup"><span data-stu-id="0554e-112">Task Description</span></span>|<span data-ttu-id="0554e-113">Rubrique</span><span class="sxs-lookup"><span data-stu-id="0554e-113">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="0554e-114">Décrit les différentes options de configuration de l'instance et explique comment afficher ou modifier ces options.</span><span class="sxs-lookup"><span data-stu-id="0554e-114">Describes the various instance configuration options and how to view or change these options.</span></span>|[<span data-ttu-id="0554e-115">Options de configuration de serveur &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0554e-115">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)|  
|<span data-ttu-id="0554e-116">Explique comment afficher et configurer les emplacements par défaut des nouveaux fichiers de données et fichiers journaux de l'instance.</span><span class="sxs-lookup"><span data-stu-id="0554e-116">Describes how to view and configure the default locations of new data and log files in the instance.</span></span>|[<span data-ttu-id="0554e-117">Afficher ou modifier les emplacements par défaut des fichiers de données et des fichiers journaux &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="0554e-117">View or Change the Default Locations for Data and Log Files &#40;SQL Server Management Studio&#41;</span></span>](view-or-change-the-default-locations-for-data-and-log-files.md)|  
|<span data-ttu-id="0554e-118">Explique comment configurer SQL Server pour utiliser soft-NUMA.</span><span class="sxs-lookup"><span data-stu-id="0554e-118">Describes how to configure SQL Server to use soft-NUMA.</span></span>|[<span data-ttu-id="0554e-119">Configurez SQL Server pour utiliser le &#40;soft-NUMA SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0554e-119">Configure SQL Server to Use Soft-NUMA &#40;SQL Server&#41;</span></span>](soft-numa-sql-server.md)|  
|<span data-ttu-id="0554e-120">Explique comment mapper un port TCP/IP à une affinité de nœud NUMA.</span><span class="sxs-lookup"><span data-stu-id="0554e-120">Describes how to map a TCP/IP port to non-uniform memory access (NUMA) node affinity.</span></span>|[<span data-ttu-id="0554e-121">Mapper les ports TCP/IP aux nœuds NUMA &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0554e-121">Map TCP IP Ports to NUMA Nodes &#40;SQL Server&#41;</span></span>](map-tcp-ip-ports-to-numa-nodes-sql-server.md)|  
|<span data-ttu-id="0554e-122">Explique comment activer la stratégie Verrouiller les pages en mémoire de Windows.</span><span class="sxs-lookup"><span data-stu-id="0554e-122">Describes how to enable the Windows Lock Pages In Memory policy.</span></span> <span data-ttu-id="0554e-123">Cette stratégie détermine quels comptes peuvent utiliser un processus destiné à conserver les données en mémoire physique pour éviter leur pagination en mémoire virtuelle sur le disque.</span><span class="sxs-lookup"><span data-stu-id="0554e-123">This policy determines which accounts can use a process to keep data in physical memory, preventing the system from paging the data to virtual memory on disk.</span></span>|[<span data-ttu-id="0554e-124">Activer l’option Lock Pages in Memory &#40;Windows&#41;</span><span class="sxs-lookup"><span data-stu-id="0554e-124">Enable the Lock Pages in Memory Option &#40;Windows&#41;</span></span>](enable-the-lock-pages-in-memory-option-windows.md)|  
  
## <a name="see-also"></a><span data-ttu-id="0554e-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0554e-125">See Also</span></span>  
 [<span data-ttu-id="0554e-126">Instances du moteur de base de données &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0554e-126">Database Engine Instances &#40;SQL Server&#41;</span></span>](database-engine-instances-sql-server.md)  
  
  