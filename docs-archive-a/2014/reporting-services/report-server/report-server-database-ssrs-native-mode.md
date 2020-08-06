---
title: Base de données du serveur de rapports (SSRS en mode natif) | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- databases [Reporting Services]
- report servers [Reporting Services], databases
- temporary databases [Reporting Services]
- report server database
- reportservertempdb
- reportserver database
ms.assetid: 0fc5c033-3fe1-4cea-86c7-66ea5e424d65
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 40c0574a0c49ca2be1f9c06636ae6776646db252
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613283"
---
# <a name="report-server-database-ssrs-native-mode"></a><span data-ttu-id="6a735-102">Base de données du serveur de rapports (SSRS en mode natif)</span><span class="sxs-lookup"><span data-stu-id="6a735-102">Report Server Database (SSRS Native Mode)</span></span>
  <span data-ttu-id="6a735-103">Un serveur de rapports est un serveur sans état qui utilise [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] pour stocker les métadonnées et les définitions d'objets.</span><span class="sxs-lookup"><span data-stu-id="6a735-103">A report server is a stateless server that uses the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] to store metadata and object definitions.</span></span> <span data-ttu-id="6a735-104">Une installation [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif utilise deux bases de données pour distinguer le stockage de données persistantes des obligations de stockage temporaire.</span><span class="sxs-lookup"><span data-stu-id="6a735-104">A native mode [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation uses two databases to separate persistent data storage from temporary storage requirements.</span></span> <span data-ttu-id="6a735-105">Les bases de données sont créées ensemble et liées par le nom.</span><span class="sxs-lookup"><span data-stu-id="6a735-105">The databases are created together and bound by name.</span></span> <span data-ttu-id="6a735-106">Les noms par défaut de ces bases de données sont respectivement **reportserver** et **reportservertempdb**.</span><span class="sxs-lookup"><span data-stu-id="6a735-106">By default, the database names are **reportserver** and **reportservertempdb**, respectively.</span></span>  
  
 <span data-ttu-id="6a735-107">Une installation de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint crée également une base de données pour la fonctionnalité d'alertes de données.</span><span class="sxs-lookup"><span data-stu-id="6a735-107">A SharePoint mode [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation will also create a database for the data alerting feature.</span></span> <span data-ttu-id="6a735-108">Les trois bases de données en mode SharePoint sont associées aux applications de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6a735-108">The three databases in SharePoint mode are associated with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service applications.</span></span> <span data-ttu-id="6a735-109">Pour plus d’informations, consultez [Gérer une application de service SharePoint Reporting Services](../manage-a-reporting-services-sharepoint-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="6a735-109">For more information, see [Manage a Reporting Services SharePoint Service Application](../manage-a-reporting-services-sharepoint-service-application.md)</span></span>  
  
 <span data-ttu-id="6a735-110">Les bases de données peuvent s'exécuter sur une instance locale ou distante du [!INCLUDE[ssDE](../../includes/ssde-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6a735-110">The databases can run on a local or remote [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance.</span></span> <span data-ttu-id="6a735-111">Le choix d'une instance locale est utile si vous possédez suffisamment de ressources système ou si vous voulez économiser des licences logicielles, mais l'exécution des bases de données sur un ordinateur distant permet d'améliorer les performances.</span><span class="sxs-lookup"><span data-stu-id="6a735-111">Choosing a local instance is useful if you have sufficient system resources or want to conserve software licenses, but running the databases on a remote computer can improve performance.</span></span>  
  
 <span data-ttu-id="6a735-112">Vous pouvez déplacer ou réutiliser une base de données de serveur de rapports existante provenant d'une installation précédente ou d'une instance différente avec une autre instance de serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="6a735-112">You can port or reuse an existing report server database from previous installation or a different instance with another report server instance.</span></span> <span data-ttu-id="6a735-113">Le schéma de la base de données du serveur de rapports doit être compatible avec l'instance du serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="6a735-113">The schema of the report server database must be compatible with the report server instance.</span></span> <span data-ttu-id="6a735-114">Si la base de données est dans un format plus ancien, vous serez invité à le mettre à niveau au format actuel.</span><span class="sxs-lookup"><span data-stu-id="6a735-114">If the database is in an older format, you will be prompted to upgrade it to the current format.</span></span> <span data-ttu-id="6a735-115">Les versions plus récentes ne peuvent pas être réajustées vers une version antérieure.</span><span class="sxs-lookup"><span data-stu-id="6a735-115">Newer versions cannot be down graded to an older version.</span></span> <span data-ttu-id="6a735-116">Si vous possédez une base de données de serveur de rapports récente, vous ne pouvez pas l'utiliser avec une version antérieure d'une instance de serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="6a735-116">If you have a newer report server database, you cannot use it with an earlier version of a report server instances.</span></span> <span data-ttu-id="6a735-117">Pour plus d’informations sur la façon dont les bases de données de serveur de rapports sont mises à niveau vers des formats plus récents, consultez [Mettre à niveau une base de données du serveur de rapports](../install-windows/upgrade-a-report-server-database.md).</span><span class="sxs-lookup"><span data-stu-id="6a735-117">For more information about how report server databases are upgraded to newer formats, see [Upgrade a Report Server Database](../install-windows/upgrade-a-report-server-database.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6a735-118">La structure de table des bases de données est optimisée pour les opérations serveur et ne doit pas être modifiée ou ajustée.</span><span class="sxs-lookup"><span data-stu-id="6a735-118">The table structure for the databases is optimized for server operations and should not be modified or tuned.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="6a735-119">peut éventuellement modifier la structure de table d'une version à une autre.</span><span class="sxs-lookup"><span data-stu-id="6a735-119">might change the table structure from one release to the next.</span></span> <span data-ttu-id="6a735-120">Si vous modifiez ou agrandissez la base de données, vous pouvez limiter voire supprimer la possibilité d'effectuer des mises à jour ou d'appliquer des Service Packs.</span><span class="sxs-lookup"><span data-stu-id="6a735-120">If you modify or extend the database, you might limit or prevent the capability to perform future upgrades or apply service packs.</span></span> <span data-ttu-id="6a735-121">Vous risquez également de créer des perturbations sur le serveur de rapports par les modifications que vous effectuez.</span><span class="sxs-lookup"><span data-stu-id="6a735-121">You might also introduce changes that impair report server operations.</span></span> <span data-ttu-id="6a735-122">Par exemple si vous activez READ_COMMITTED_SNAPSHOT sur la base de données ReportServer, vous arrêterez des fonctionnalités interactives de tri.</span><span class="sxs-lookup"><span data-stu-id="6a735-122">For example if you turn on READ_COMMITTED_SNAPSHOT on the ReportServer database, you will break the interactive sorting feature.</span></span>  
  
 <span data-ttu-id="6a735-123">Tous les accès à une base de données du serveur de rapports doivent être gérés par le biais du serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="6a735-123">All access to a report server database must be handled through the report server.</span></span> <span data-ttu-id="6a735-124">Pour accéder au contenu d’une base de données du serveur de rapports, vous pouvez utiliser les outils de gestion du serveur de rapports (tels que Gestionnaire de rapports et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] ), ou des interfaces de programmation telles que l’accès URL, le service Web Report Server ou le fournisseur Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="6a735-124">To access content in a report server database, you can use report server management tools, (such as Report Manager and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]), or programmatic interfaces such as URL access, Report Server Web service, or the Windows Management Instrumentation (WMI) provider.</span></span>  
  
 <span data-ttu-id="6a735-125">La connexion à la base de données du serveur de rapports est généralement définie par l'intermédiaire du Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6a735-125">The connection to the report server database is usually defined through the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="6a735-126">Toutefois, cette connexion peut être configurée au cours de l'installation si vous choisissez d'installer la configuration par défaut.</span><span class="sxs-lookup"><span data-stu-id="6a735-126">However, it can be defined during setup if you choose to install the default configuration.</span></span> <span data-ttu-id="6a735-127">Pour plus d’informations sur la connexion du serveur de rapports à la base de données, consultez [Configurer une connexion à la base de données du serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).</span><span class="sxs-lookup"><span data-stu-id="6a735-127">For more information about the report server connection to the database, see [Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).</span></span>  
  
## <a name="report-server-database"></a><span data-ttu-id="6a735-128">base de données du serveur de rapports</span><span class="sxs-lookup"><span data-stu-id="6a735-128">Report Server Database</span></span>  
 <span data-ttu-id="6a735-129">La base de données d'un serveur de rapports est une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui stocke le contenu suivant :</span><span class="sxs-lookup"><span data-stu-id="6a735-129">The report server database is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that stores the following content:</span></span>  
  
-   <span data-ttu-id="6a735-130">Éléments gérés par un serveur de rapports (.. /Reports et les rapports liés, les sources de données partagées, les modèles de rapport, les dossiers, les ressources) et toutes les propriétés et les paramètres de sécurité associés à ces éléments.</span><span class="sxs-lookup"><span data-stu-id="6a735-130">Items managed by a report server (../reports and linked reports, shared data sources, report models, folders, resources) and all of the properties and security settings that are associated with those items.</span></span>  
  
-   <span data-ttu-id="6a735-131">définitions des abonnements et des planifications ;</span><span class="sxs-lookup"><span data-stu-id="6a735-131">Subscription and schedule definitions.</span></span>  
  
-   <span data-ttu-id="6a735-132">instantanés de rapport (notamment les résultats de requête) et historique de rapport ;</span><span class="sxs-lookup"><span data-stu-id="6a735-132">Report snapshots (which include query results) and report history.</span></span>  
  
-   <span data-ttu-id="6a735-133">propriétés système et paramètres de sécurité au niveau système ;</span><span class="sxs-lookup"><span data-stu-id="6a735-133">System properties and system-level security settings.</span></span>  
  
-   <span data-ttu-id="6a735-134">données du journal d'exécution des rapports ;</span><span class="sxs-lookup"><span data-stu-id="6a735-134">Report execution log data.</span></span>  
  
-   <span data-ttu-id="6a735-135">clés symétriques, ainsi que connexions et informations d'identification chiffrées pour les sources de données des rapports.</span><span class="sxs-lookup"><span data-stu-id="6a735-135">Symmetric keys and encrypted connection and credentials for report data sources.</span></span>  
  
 <span data-ttu-id="6a735-136">Étant donné que la base de données du serveur de rapports stocke l'état de l'application ainsi que des données permanentes, vous devez créer une planification de sauvegarde pour cette base de données afin d'éviter toute perte de données.</span><span class="sxs-lookup"><span data-stu-id="6a735-136">Because the report server database stores application state and persistent data, you should create a backup schedule for this database to prevent data loss.</span></span> <span data-ttu-id="6a735-137">Pour obtenir des recommandations et des instructions sur la sauvegarde de la base de données, consultez [Déplacement des bases de données du serveur de rapports vers un autre ordinateur &#40;en mode natif SSRS&#41;](moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md).</span><span class="sxs-lookup"><span data-stu-id="6a735-137">For recommendations and instructions on how to back up the database, see [Moving the Report Server Databases to Another Computer &#40;SSRS Native Mode&#41;](moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md).</span></span>  
  
## <a name="report-server-temporary-database"></a><span data-ttu-id="6a735-138">Base de données temporaire du serveur de rapports</span><span class="sxs-lookup"><span data-stu-id="6a735-138">Report Server Temporary Database</span></span>  
 <span data-ttu-id="6a735-139">Chaque base de données de serveur de rapports utilise une base de données temporaire associée pour stocker les données d'exécution et de session, les rapports mis en cache et les tables de travail qui sont générées par le serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="6a735-139">Each report server database uses a related temporary database to store session and execution data, cached reports, and work tables that are generated by the report server.</span></span> <span data-ttu-id="6a735-140">Les processus serveur d'arrière-plan supprimeront périodiquement des éléments plus anciens et inutilisés des tables dans la base de données temporaire.</span><span class="sxs-lookup"><span data-stu-id="6a735-140">Background server processes will periodically remove older and unused items from the tables in the temporary database.</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="6a735-141">ne recrée pas la base de données temporaire si elle est manquante, pas plus qu’il ne répare les tables manquantes ou modifiées.</span><span class="sxs-lookup"><span data-stu-id="6a735-141">does not re-create the temporary database if it is missing, nor does it repair missing or modified tables.</span></span> <span data-ttu-id="6a735-142">Bien qu'une base de données temporaire ne contienne pas de données permanentes, il est conseillé malgré tout d'en sauvegarder un exemplaire pour éviter d'être obligé de la recréer lors d'une opération de récupération suite à une défaillance majeure.</span><span class="sxs-lookup"><span data-stu-id="6a735-142">Although the temporary database does not contain persistent data, you should back up a copy of the database anyway so that you can avoid having to re-create it as part of a failure recovery operation.</span></span>  
  
 <span data-ttu-id="6a735-143">Si vous sauvegardez la base de données temporaire et la restaurez ensuite, il est recommandé d'en supprimer le contenu.</span><span class="sxs-lookup"><span data-stu-id="6a735-143">If you back up the temporary database and subsequently restore it, you should delete the contents.</span></span> <span data-ttu-id="6a735-144">En règle générale, il n'est pas risqué de supprimer le contenu de la base de données temporaire à quelque moment que ce soit.</span><span class="sxs-lookup"><span data-stu-id="6a735-144">Generally, it is safe to delete the contents of the temporary database at any time.</span></span> <span data-ttu-id="6a735-145">Toutefois, vous devez redémarrer le service Windows Report Server après avoir supprimé le contenu.</span><span class="sxs-lookup"><span data-stu-id="6a735-145">However, you must restart the Report Server Windows service after you delete the contents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a735-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a735-146">See Also</span></span>  
 <span data-ttu-id="6a735-147">[Héberger une base de données du serveur de rapports dans un cluster de basculement SQL Server](../install-windows/host-a-report-server-database-in-a-sql-server-failover-cluster.md) </span><span class="sxs-lookup"><span data-stu-id="6a735-147">[Host a Report Server Database in a SQL Server Failover Cluster](../install-windows/host-a-report-server-database-in-a-sql-server-failover-cluster.md) </span></span>  
 <span data-ttu-id="6a735-148">[Stocker des données chiffrées du serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) </span><span class="sxs-lookup"><span data-stu-id="6a735-148">[Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) </span></span>  
 <span data-ttu-id="6a735-149">[Serveur de rapports Reporting Services](../reporting-services-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="6a735-149">[Reporting Services Report Server](../reporting-services-report-server.md) </span></span>  
 <span data-ttu-id="6a735-150">[Administrer une base de données du serveur de rapports &#40;SSRS en mode natif&#41;](report-server-database-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="6a735-150">[Administer a Report Server Database &#40;SSRS Native Mode&#41;](report-server-database-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="6a735-151">[Créer une base de données du serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="6a735-151">[Create a Report Server Database  &#40;SSRS Configuration Manager&#41;](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md) </span></span>  
 [<span data-ttu-id="6a735-152">Opérations de sauvegarde et de restauration pour Reporting Services</span><span class="sxs-lookup"><span data-stu-id="6a735-152">Backup and Restore Operations for Reporting Services</span></span>](../install-windows/backup-and-restore-operations-for-reporting-services.md)  
  
  