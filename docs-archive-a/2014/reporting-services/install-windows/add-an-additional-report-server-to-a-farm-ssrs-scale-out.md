---
title: Ajouter un serveur de rapports supplémentaire à un pool (montée en puissance SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c1a6b683-15cf-44ae-ac60-ceee63a60aaf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 31fd7809c4085a90dc487f9091a7f9bd0aeab58e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601977"
---
# <a name="add-an-additional-report-server-to-a-farm-ssrs-scale-out"></a><span data-ttu-id="db284-102">Ajouter un serveur de rapports supplémentaire à une batterie (montée en puissance SSRS)</span><span class="sxs-lookup"><span data-stu-id="db284-102">Add an Additional Report Server to a Farm (SSRS Scale-out)</span></span>
  <span data-ttu-id="db284-103">L'ajout d'un second serveur de rapports en mode SharePoint, ou plus, à votre batterie de serveurs SharePoint peut améliorer les performances et le temps de réponse du traitement du serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="db284-103">Adding a second or more SharePoint mode report servers to your SharePoint farm can improve the performance and response time of the report server processing.</span></span> <span data-ttu-id="db284-104">Si vous avez trouvé que les performances ralentissaient alors que vous ajoutiez des utilisateurs, des rapports et autres applications au serveur de rapports, l'ajout de serveurs de rapports peut améliorer les performances.</span><span class="sxs-lookup"><span data-stu-id="db284-104">If you find performance slowing down as you added more users, reports, and other applications to the report server, then adding additions report servers can improve performance.</span></span> <span data-ttu-id="db284-105">Il est également recommandé d'ajouter un second serveur de rapports pour augmenter la disponibilité des serveurs de rapports lorsqu'il existe des problèmes liés au matériel ou lorsque vous effectuez la maintenance générale sur des serveurs individuels de votre environnement.</span><span class="sxs-lookup"><span data-stu-id="db284-105">It is also recommended to add a second report server to increase the availability of report servers when there are issues with hardware or you are conducting general maintenance on individual servers in your environment.</span></span> <span data-ttu-id="db284-106">À compter de la version [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , les étapes de la montée en puissance parallèle d'un environnement [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint suivent le déploiement standard d'une batterie de serveurs SharePoint et exploitent les fonctionnalités d'équilibrage de charge SharePoint.</span><span class="sxs-lookup"><span data-stu-id="db284-106">Starting with the [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] release, the steps to scale-out a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] environment in SharePoint mode follows standard SharePoint farm deployment and leverages the SharePoint load balancing features.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="db284-107">Le déploiement avec montée en puissance parallèle de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] n'est pas pris en charge par toutes les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="db284-107">Scale-out of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is not supported on all editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="db284-108">Pour plus d’informations, consultez la [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] section des [fonctionnalités prises en charge par les éditions de SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span><span class="sxs-lookup"><span data-stu-id="db284-108">For more information, see the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] section of [Features Supported by the Editions of SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="db284-109">À compter de la version [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], vous n'utilisez pas le Gestionnaire de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour ajouter des serveurs et effectuer un scale-out des serveurs de rapports.</span><span class="sxs-lookup"><span data-stu-id="db284-109">Starting with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] you do not use [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager to add servers and scale out report servers.</span></span> <span data-ttu-id="db284-110">Les produits SharePoint gèrent le déploiement avec montée en puissance parallèle de Reporting Services sous forme de serveurs SharePoint avec l'ajout du service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] à la batterie de serveurs.</span><span class="sxs-lookup"><span data-stu-id="db284-110">SharePoint products manage the scale-out of reporting services as SharePoint servers with the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service are added to the farm.</span></span>  
  
 <span data-ttu-id="db284-111">Pour plus d’informations sur le déploiement de serveurs de rapports en mode natif avec montée en puissance parallèle, consultez [Configurer un déploiement par montée en puissance parallèle de serveurs de rapports en mode natif &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure-a-native-mode-report-server-scale-out-deployment.md).</span><span class="sxs-lookup"><span data-stu-id="db284-111">For information on how to scale-out native mode report servers, see [Configure a Native Mode Report Server Scale-Out Deployment &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-a-native-mode-report-server-scale-out-deployment.md).</span></span>  
  
-   [<span data-ttu-id="db284-112">Équilibrage de charge</span><span class="sxs-lookup"><span data-stu-id="db284-112">Load Balancing</span></span>](#bkmk_loadbalancing)  
  
-   [<span data-ttu-id="db284-113">Composants requis</span><span class="sxs-lookup"><span data-stu-id="db284-113">Prerequisites</span></span>](#bkmk_prerequisites)  
  
-   [<span data-ttu-id="db284-114">Étapes</span><span class="sxs-lookup"><span data-stu-id="db284-114">Steps</span></span>](#bkmk_steps)  
  
-   [<span data-ttu-id="db284-115">Configuration supplémentaire</span><span class="sxs-lookup"><span data-stu-id="db284-115">Additional Configuration</span></span>](#bkmk_additional)  
  
##  <a name="load-balancing"></a><a name="bkmk_loadbalancing"></a><span data-ttu-id="db284-116">Équilibrage de charge</span><span class="sxs-lookup"><span data-stu-id="db284-116">Load Balancing</span></span>  
 <span data-ttu-id="db284-117">L'équilibrage de la charge des applications de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sera géré automatiquement par SharePoint à moins que votre environnement n'ait une solution d'équilibrage de charge tierce ou personnalisée.</span><span class="sxs-lookup"><span data-stu-id="db284-117">The Load balancing of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service applications will be managed automatically by SharePoint unless your environment has a custom or third-party load balancing solution.</span></span> <span data-ttu-id="db284-118">Le comportement d'équilibrage de la charge SharePoint par défaut fait que chaque application de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sera équilibrée à travers tous les serveurs d'applications sur lesquels vous avez démarré le service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="db284-118">The default SharePoint load balancing behavior is that each [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Service Application will be balanced across all the application servers where you have started the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service.</span></span> <span data-ttu-id="db284-119">Pour vérifier si le service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est installé et démarré, cliquez sur **Gérer les services sur le serveur** dans l'Administration centrale de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="db284-119">To verify if the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service is installed and started, click **Manage services on server** in SharePoint Central Administration.</span></span>  
  
##  <a name="prerequisites"></a><a name="bkmk_prerequisites"></a> <span data-ttu-id="db284-120">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="db284-120">Prerequisites</span></span>  
  
-   <span data-ttu-id="db284-121">Vous devez être administrateur local pour exécuter le programme d'installation de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="db284-121">You must be a local administrator to run SQL Server Setup.</span></span>  
  
-   <span data-ttu-id="db284-122">L'ordinateur doit être attaché à un domaine.</span><span class="sxs-lookup"><span data-stu-id="db284-122">The computer must be joined to a domain.</span></span>  
  
-   <span data-ttu-id="db284-123">Vous devez connaître le nom du serveur de base de données existant qui héberge la configuration et les bases de données de contenu SharePoint.</span><span class="sxs-lookup"><span data-stu-id="db284-123">You need to know the name of the existing database server that is hosting the SharePoint configuration and content databases.</span></span>  
  
-   <span data-ttu-id="db284-124">Le serveur de base de données doit être configuré pour autoriser les connexions de base de données distantes.</span><span class="sxs-lookup"><span data-stu-id="db284-124">The database server must be configured to allow for remote database connections.</span></span>  <span data-ttu-id="db284-125">S'il ne l'est pas, vous ne pourrez pas joindre le nouveau serveur à la batterie car il ne pourra pas établir de connexion aux bases de données de configuration SharePoint.</span><span class="sxs-lookup"><span data-stu-id="db284-125">If it is not, you will not be able to join the new server to the farm because the new server will not be able to make a connection to the SharePoint configuration databases.</span></span>  
  
-   <span data-ttu-id="db284-126">Le nouveau serveur devra avoir la même version de SharePoint installée que celle exécutée par les serveurs de batterie actuels.</span><span class="sxs-lookup"><span data-stu-id="db284-126">The new server will need to have the same version of SharePoint installed that the current farm servers are running.</span></span> <span data-ttu-id="db284-127">Par exemple, si SharePoint 2010 Service Pack 1 (SP1) est déjà installé sur la batterie, vous devrez installer également le SP1 sur le nouveau serveur pour qu'il puisse rejoindre la batterie.</span><span class="sxs-lookup"><span data-stu-id="db284-127">For example if the farm already has SharePoint 2010 Service Pack 1 (SP1) installed, you will need to also install SP1 on the new server before it can join the farm.</span></span>  
  
-   <span data-ttu-id="db284-128">Consultez les rubriques supplémentaires suivantes pour comprendre les exigences du système et des versions :</span><span class="sxs-lookup"><span data-stu-id="db284-128">Review the following additional topics to understand system and version requirements:</span></span>  
  
     [<span data-ttu-id="db284-129">Instructions d'utilisation des fonctionnalités BI de SQL Server dans une batterie de serveurs SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="db284-129">Guidance for Using SQL Server BI Features in a SharePoint 2010 Farm</span></span>](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)  
  
##  <a name="steps"></a><a name="bkmk_steps"></a><span data-ttu-id="db284-130">Étapes</span><span class="sxs-lookup"><span data-stu-id="db284-130">Steps</span></span>  
 <span data-ttu-id="db284-131">Les étapes de cette rubrique partent du principe qu'un administrateur de batterie de serveurs SharePoint installe et configure le serveur.</span><span class="sxs-lookup"><span data-stu-id="db284-131">The steps in this topic assume that a SharePoint farm administrator is installing and configuring the server.</span></span> <span data-ttu-id="db284-132">Le diagramme illustre un environnement à trois niveaux classique et les éléments numérotés sont décrits dans la liste suivante :</span><span class="sxs-lookup"><span data-stu-id="db284-132">The diagram shows a typical three tier environment and the numbered items in the diagram are described in the following list:</span></span>  
  
-   <span data-ttu-id="db284-133">(1) Plusieurs serveurs Web frontaux.</span><span class="sxs-lookup"><span data-stu-id="db284-133">(1) Multiple web front-end (WFE) servers.</span></span> <span data-ttu-id="db284-134">Les serveurs Web frontaux ont besoin du complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour SharePoint 2010.</span><span class="sxs-lookup"><span data-stu-id="db284-134">The WFE servers require the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint 2010.</span></span>  
  
-   <span data-ttu-id="db284-135">(2) Un seul serveur d'applications exécutant [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et des sites Web, par exemple Administration centrale.</span><span class="sxs-lookup"><span data-stu-id="db284-135">(2) A single application server running [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and web sites, for example Central Administration.</span></span> <span data-ttu-id="db284-136">Les étapes suivantes ajoutent un deuxième serveur d'applications à cette couche.</span><span class="sxs-lookup"><span data-stu-id="db284-136">The following steps add a second application server to this tier.</span></span>  
  
-   <span data-ttu-id="db284-137">(3) Deux serveurs de base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="db284-137">(3) Two SQL Server database servers.</span></span>  
  
-   <span data-ttu-id="db284-138">(4) Représente une solution d'équilibrage de la charge réseau matérielle ou logicielle</span><span class="sxs-lookup"><span data-stu-id="db284-138">(4) Represents a software or hardware network load balancing solution (NLB)</span></span>  
  
 <span data-ttu-id="db284-139">![Ajout d'un serveur d'applications Reporting Services](../../../2014/sql-server/install/media/rs-sharepointscale.gif "Ajout d'un serveur d'applications Reporting Services")</span><span class="sxs-lookup"><span data-stu-id="db284-139">![Adding a Reporting Services application server](../../../2014/sql-server/install/media/rs-sharepointscale.gif "Adding a Reporting Services application server")</span></span>  
  
 <span data-ttu-id="db284-140">Les étapes suivantes impliquent qu'un administrateur procède à l'installation et à la configuration du serveur.</span><span class="sxs-lookup"><span data-stu-id="db284-140">The following steps assume that an administrator is installing and configuring the server.</span></span> <span data-ttu-id="db284-141">Le serveur sera installé en tant que nouveau serveur d'applications dans la batterie et ne sera pas utilisé comme serveur Web frontal.</span><span class="sxs-lookup"><span data-stu-id="db284-141">The server will be setup as a new application server in the farm and not used as a web front-end (WFE).</span></span>  
  
|<span data-ttu-id="db284-142">Étape</span><span class="sxs-lookup"><span data-stu-id="db284-142">Step</span></span>|<span data-ttu-id="db284-143">Description et lien</span><span class="sxs-lookup"><span data-stu-id="db284-143">Description and Link</span></span>|  
|----------|--------------------------|  
|<span data-ttu-id="db284-144">Exécutez l'Outil de préparation des produits SharePoint 2010.</span><span class="sxs-lookup"><span data-stu-id="db284-144">Run the SharePoint 2010 Products Preparation Tool</span></span>|<span data-ttu-id="db284-145">Vous devez disposer du support d'installation pour SharePoint 2010.</span><span class="sxs-lookup"><span data-stu-id="db284-145">You must have the SharePoint 2010 installation media.</span></span> <span data-ttu-id="db284-146">L’outil de préparation est **PrerequisiteInstaller.exe** sur le support d’installation.</span><span class="sxs-lookup"><span data-stu-id="db284-146">The preparation tool is **PrerequisiteInstaller.exe** on the installation media.</span></span>|  
|<span data-ttu-id="db284-147">Installez un produit SharePoint 2010.</span><span class="sxs-lookup"><span data-stu-id="db284-147">Install a SharePoint 2010 product.</span></span>|<span data-ttu-id="db284-148">1) sélectionnez le type d’installation de la **batterie de serveurs** .</span><span class="sxs-lookup"><span data-stu-id="db284-148">1) Select the **Server Farm** installation type.</span></span><br /><br /> <span data-ttu-id="db284-149">2) sélectionnez **terminé** pour le type de serveur.</span><span class="sxs-lookup"><span data-stu-id="db284-149">2) Select **Complete** for the server type.</span></span><br /><br /> <span data-ttu-id="db284-150">3) Lorsque l’installation est terminée, n’exécutez pas l’Assistant Configuration des produits SharePoint si SharePoint 2010 SP1 est installé sur votre batterie de serveurs SharePoint existante.</span><span class="sxs-lookup"><span data-stu-id="db284-150">3) When the installation is complete, do not run the SharePoint Products Configuration wizard if your existing SharePoint farm has SharePoint 2010 SP1 installed.</span></span> <span data-ttu-id="db284-151">Vous devez installer SharePoint SP1 avant d'exécuter l'Assistant Configuration des produits SharePoint.</span><span class="sxs-lookup"><span data-stu-id="db284-151">You should install SharePoint SP1 before running the SharePoint products configuration wizard.</span></span>|  
|<span data-ttu-id="db284-152">Installer SharePoint Server 2010 SP1</span><span class="sxs-lookup"><span data-stu-id="db284-152">Install SharePoint Server 2010 SP1.</span></span>|<span data-ttu-id="db284-153">Si SharePoint 2010 SP1 est installé sur votre batterie de serveurs SharePoint existante, téléchargez et installez SharePoint 2010 SP1 à partir de : [https://support.microsoft.com/kb/2460045](https://go.microsoft.com/fwlink/p/?linkID=219697) .</span><span class="sxs-lookup"><span data-stu-id="db284-153">If your existing SharePoint farm has SharePoint 2010 SP1 installed download and install SharePoint 2010 SP1 from:[https://support.microsoft.com/kb/2460045](https://go.microsoft.com/fwlink/p/?linkID=219697).</span></span><br /><br /> <span data-ttu-id="db284-154">Pour plus d'informations sur SharePoint 2010 SP1, consultez [Problèmes connus lors de l'installation d'Office 2010 SP1 et de SharePoint 2010 SP1](https://support.microsoft.com/kb/2532126):</span><span class="sxs-lookup"><span data-stu-id="db284-154">For more information on SharePoint 2010 SP1, see [Known issues when you install Office 2010 SP1 and SharePoint 2010 SP1](https://support.microsoft.com/kb/2532126):</span></span>|  
|<span data-ttu-id="db284-155">Exécutez l'Assistant Configuration des produits SharePoint pour ajouter le serveur à la batterie.</span><span class="sxs-lookup"><span data-stu-id="db284-155">Run the SharePoint Products Configuration wizard to add the server to the farm.</span></span>|<span data-ttu-id="db284-156">1) dans le groupe de programmes **produits Microsoft sharepoint 2010** , cliquez sur **Assistant Configuration des produits Microsoft SharePoint 2010**.</span><span class="sxs-lookup"><span data-stu-id="db284-156">1) In the **Microsoft SharePoint 2010 Products** program group, click **Microsoft SharePoint 2010 Products Configuration Wizard**.</span></span><br /><br /> <span data-ttu-id="db284-157">2) dans la page **se connecter à une batterie de serveurs** , sélectionnez **se connecter à une batterie** de serveurs existante, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="db284-157">2) On the **Connect to a Server Farm** page select **Connect to an existing Farm** and click **Next**.</span></span><br /><br /> <span data-ttu-id="db284-158">3) dans la page **spécifier les paramètres de la base de données de configuration** , tapez le nom du serveur de base de données utilisé pour la batterie de serveurs existante et le nom de la base de données de configuration.</span><span class="sxs-lookup"><span data-stu-id="db284-158">3) On the **Specify Configuration Database Settings** page, type the name of the database server used for the existing farm and the name of the configuration database.</span></span> <span data-ttu-id="db284-159">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="db284-159">Click **Next**.</span></span><br /><span data-ttu-id="db284-160">\*\* \* \* Important \* si \* \*\* vous voyez un message d’erreur semblable au suivant et que vous avez vérifié que vous disposez des autorisations, vérifiez les Protocoles activés pour la configuration réseau SQL Server dans **SQL Server Configuration Manager**: «échec de la connexion au serveur de base de données.</span><span class="sxs-lookup"><span data-stu-id="db284-160">**\*\* Important \*\*** If you see an error message similar to the following and you have verified you have permissions, then verify what protocols are enabled for the SQL Server Network Configuration in **Sql Server Configuration Manager**:"Failed to connect to the database server.</span></span> <span data-ttu-id="db284-161">Assurez-vous que la base de données existe, qu’il s’agit d’un serveur SQL Server et que vous disposez des autorisations appropriées pour accéder au serveur.»</span><span class="sxs-lookup"><span data-stu-id="db284-161">Ensure the database exists , is a Sql Server, and that you have the appropriate permissions to access the server."</span></span><br /><span data-ttu-id="db284-162">\*\* \* \* Important \* si \* \*\* vous voyez l' **État du produit et du correctif**de la batterie de serveurs de pages, vous devez passer en revue les informations de la page et mettre à jour le serveur avec les fichiers nécessaires pour pouvoir continuer à joindre le serveur à la batterie de serveurs.</span><span class="sxs-lookup"><span data-stu-id="db284-162">**\*\* Important \*\*** If you see the page **Server Farm Product and Patch Status**, you will need to review the information on the page and update the server with the needed files before you can proceed with joining the server to the farm.</span></span><br /><br /> <span data-ttu-id="db284-163">4) dans la page **spécifier les paramètres de sécurité** de la batterie, tapez le mot de passe de votre batterie de serveurs, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="db284-163">4) On the **Specify Farm Security Settings** page type your farm passphrase and click **Next**.</span></span> <span data-ttu-id="db284-164">Cliquez sur **Suivant** dans la page de confirmation pour exécuter l'Assistant.</span><span class="sxs-lookup"><span data-stu-id="db284-164">Click **Next** on the confirmation page to run the wizard.</span></span><br /><br /> <span data-ttu-id="db284-165">5) cliquez sur **suivant** pour exécuter l' **Assistant Configuration de batterie de serveurs**.</span><span class="sxs-lookup"><span data-stu-id="db284-165">5) Click **Next** to run the **Farm Configuration Wizard**.</span></span>|  
|<span data-ttu-id="db284-166">Vérifiez que le serveur a été ajouté à la batterie de serveurs SharePoint.</span><span class="sxs-lookup"><span data-stu-id="db284-166">Verify the server was added to the SharePoint farm.</span></span>|<span data-ttu-id="db284-167">1) Dans l’Administration centrale de SharePoint, cliquez sur **Gérer les serveurs de cette batterie** dans le groupe **Paramètres système** .</span><span class="sxs-lookup"><span data-stu-id="db284-167">1) In SharePoint Central Administration, click **Manage servers in this farm** in the **System Settings** group.</span></span><br /><br /> <span data-ttu-id="db284-168">2) Vérifiez que le nouveau serveur est ajouté et que l'état est correct.</span><span class="sxs-lookup"><span data-stu-id="db284-168">2) Verify the new server is added and the status is correct.</span></span><br /><br /> <span data-ttu-id="db284-169">3) Notez que le service **SQL Server Reporting Services** service n’est pas en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="db284-169">3) Note you do not see the service **SQL Server Reporting Services Service** running.</span></span> <span data-ttu-id="db284-170">Le service sera installé à l'étape suivante.</span><span class="sxs-lookup"><span data-stu-id="db284-170">The service will be installed in the next step.</span></span><br /><br /> <span data-ttu-id="db284-171">4) pour supprimer ce serveur du rôle WFE, cliquez sur **gérer les services sur le serveur** et arrêtez l' **application Web service Microsoft SharePoint Foundation**.</span><span class="sxs-lookup"><span data-stu-id="db284-171">4) To remove this server from the WFE role, click **Manage services on server** and stop the service **Microsoft SharePoint Foundation Web Application**.</span></span>|  
|<span data-ttu-id="db284-172">Installez et configurez le mode SharePoint de Reporting Services.</span><span class="sxs-lookup"><span data-stu-id="db284-172">Install and configure Reporting Services SharePoint mode.</span></span>|<span data-ttu-id="db284-173">Exécutez l'installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="db284-173">Run [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installation.</span></span> <span data-ttu-id="db284-174">Pour plus d’informations sur l’installation du [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] mode SharePoint, consultez [installer Reporting Services mode SharePoint pour SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md) si le serveur ne sera utilisé qu’en tant que serveur d’applications et que le serveur ne sera pas utilisé comme WFE, vous n’avez pas besoin de sélectionner **Reporting Services complément pour les produits SharePoint** sur :</span><span class="sxs-lookup"><span data-stu-id="db284-174">For more information on the installation of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode, see [Install Reporting Services SharePoint Mode for SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md) If the server will only be used as an application server and the server will not be used as a WFE, you do not need to select **Reporting Services add-in for SharePoint products** on:</span></span><br /><br /> <span data-ttu-id="db284-175">la page **rôle d’installation** , sélectionnez **installation de fonctionnalités SQL Server**</span><span class="sxs-lookup"><span data-stu-id="db284-175">the **Setup Role** page, select **SQL Server Feature Installation**</span></span><br /><br /> <span data-ttu-id="db284-176">la page **sélection de fonctionnalités** , sélectionnez **Reporting Services-SharePoint**</span><span class="sxs-lookup"><span data-stu-id="db284-176">the **Feature Selection** page, select **Reporting Services - SharePoint**</span></span><br /><br /> <span data-ttu-id="db284-177">OU</span><span class="sxs-lookup"><span data-stu-id="db284-177">-OR-</span></span><br /><br /> <span data-ttu-id="db284-178">la page **configuration de Reporting Services** Vérifiez que l’option **installer uniquement** est sélectionnée pour **Reporting Services mode SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="db284-178">the **Reporting Services Configuration**  page verify the **Install Only** option is selected for **Reporting Services SharePoint Mode**.</span></span>|  
|<span data-ttu-id="db284-179">Vérifiez que Reporting Services est opérationnel.</span><span class="sxs-lookup"><span data-stu-id="db284-179">Verify that Reporting Services is operational.</span></span>|<span data-ttu-id="db284-180">1) Dans l’Administration centrale de SharePoint, cliquez sur **Gérer les serveurs de cette batterie** dans le groupe **Paramètres système** .</span><span class="sxs-lookup"><span data-stu-id="db284-180">1) In SharePoint Central Administration, click **Manage servers in this farm** in the **System Settings** group.</span></span><br /><br /> <span data-ttu-id="db284-181">2) Vérifiez le service **SQL Server Reporting Services**.</span><span class="sxs-lookup"><span data-stu-id="db284-181">2) Verify the service **SQL Server Reporting Services Service**.</span></span><br /><br /> <span data-ttu-id="db284-182">Pour plus d’informations, consultez [vérifier une installation de Reporting Services](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)</span><span class="sxs-lookup"><span data-stu-id="db284-182">For more information, see [Verify a Reporting Services Installation](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)</span></span>|  
  
##  <a name="additional-configuration"></a><a name="bkmk_additional"></a><span data-ttu-id="db284-183">Configuration supplémentaire</span><span class="sxs-lookup"><span data-stu-id="db284-183">Additional Configuration</span></span>  
 <span data-ttu-id="db284-184">Vous pouvez optimiser des serveurs [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] individuels dans un déploiement avec montée en puissance parallèle afin d'effectuer un traitement en arrière-plan uniquement, de sorte que ces serveurs ne soient pas en concurrence en matière d'utilisation des ressources pour l'exécution de rapports interactifs.</span><span class="sxs-lookup"><span data-stu-id="db284-184">You can optimize individual [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] servers in a scaled out deployment to perform background processing only so they do not compete for resources with interactive report execution.</span></span> <span data-ttu-id="db284-185">Le traitement en arrière-plan comprend les planifications, les abonnements et les alertes de données.</span><span class="sxs-lookup"><span data-stu-id="db284-185">Background processing includes schedules, subscriptions, and data alerts.</span></span>  
  
 <span data-ttu-id="db284-186">Pour modifier le comportement des serveurs de rapports individuels, affectez la valeur **\<IsWebServiceEnable>** false dans le fichier de configuration **RSreportServer.config** .</span><span class="sxs-lookup"><span data-stu-id="db284-186">To change the behavior of individual report servers, set **\<IsWebServiceEnable>** to false in the **RSreportServer.config** configuration file.</span></span>  
  
 <span data-ttu-id="db284-187">Par défaut, les serveurs de rapports sont configurés avec la \<IsWebServiceEnable> valeur true.</span><span class="sxs-lookup"><span data-stu-id="db284-187">By default reports servers are configured with \<IsWebServiceEnable> set to TRUE.</span></span> <span data-ttu-id="db284-188">Lorsque tous les serveurs sont configurés avec la valeur TRUE, les charges de traitement interactif et de traitement en arrière-plan sont équilibrées sur tous les nœuds de la batterie de serveurs.</span><span class="sxs-lookup"><span data-stu-id="db284-188">When all servers are configured for TRUE, interactive and background will be load balanced across all nodes in the farm.</span></span>  
  
 <span data-ttu-id="db284-189">Si vous configurez tous les serveurs de rapports avec \<IsWebServiceEnable> la valeur false, un message d’erreur semblable au suivant s’affiche lorsque vous essayez d’utiliser les [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fonctionnalités :</span><span class="sxs-lookup"><span data-stu-id="db284-189">If you configure all report servers with \<IsWebServiceEnable> set to False, you will see an error message similar to the following when you try to use [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features:</span></span>  
  
 <span data-ttu-id="db284-190">Le service Web Reporting Services n'est pas activé.</span><span class="sxs-lookup"><span data-stu-id="db284-190">The Reporting Services Web Service is not enabled.</span></span> <span data-ttu-id="db284-191">Configurez au moins une instance du service Reporting Services SharePoint pour avoir la \<IsWebServiceEnable> valeur true.</span><span class="sxs-lookup"><span data-stu-id="db284-191">Configure at least one instance of the Reporting Services SharePoint Service to have \<IsWebServiceEnable> set to true.</span></span> <span data-ttu-id="db284-192">Pour plus d’informations, consultez [modifier un fichier de Configuration Reporting Services &#40;RSreportserver.config&#41;](../report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)</span><span class="sxs-lookup"><span data-stu-id="db284-192">For more information, see [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](../report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db284-193">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db284-193">See Also</span></span>  
 <span data-ttu-id="db284-194">[Ajouter des serveurs Web ou d’applications aux batteries de serveurs dans SharePoint 2013](https://technet.microsoft.com/library/cc261752.aspx) </span><span class="sxs-lookup"><span data-stu-id="db284-194">[Add web or application servers to farms in SharePoint 2013](https://technet.microsoft.com/library/cc261752.aspx) </span></span>  
 [<span data-ttu-id="db284-195">Configurer les services (SharePoint Server 2010)</span><span class="sxs-lookup"><span data-stu-id="db284-195">Configure services (SharePoint Server 2010)</span></span>](https://technet.microsoft.com/library/ee794878.aspx)  
  
  