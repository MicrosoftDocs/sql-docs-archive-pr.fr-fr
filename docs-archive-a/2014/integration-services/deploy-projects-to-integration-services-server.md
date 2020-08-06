---
title: Déployer des projets sur Integration Services Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 6e9402f4-4d50-49ff-820d-65a77829c4a5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 944dff3531fa24344c5157a1ac90e0109c6d0387
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613565"
---
# <a name="deploy-projects-to-integration-services-server"></a><span data-ttu-id="0dd86-102">Déployer des projets sur le serveur Integration Services</span><span class="sxs-lookup"><span data-stu-id="0dd86-102">Deploy Projects to Integration Services Server</span></span>
  <span data-ttu-id="0dd86-103">Dans la version actuelle d’ [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], vous pouvez déployer vos projets sur le serveur [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0dd86-103">In the current release of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], you can deploy your projects to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="0dd86-104">Le serveur [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] vous permet de gérer les packages, d'exécuter les packages et de configurer les valeurs d'exécution des packages à l'aide d'environnements.</span><span class="sxs-lookup"><span data-stu-id="0dd86-104">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server enables you to manage packages, run packages, and configure runtime values for packages by using environments.</span></span>  
  
 <span data-ttu-id="0dd86-105">Pour plus d’informations sur les environnements, consultez [Créer et mapper un environnement serveur](../../2014/integration-services/create-and-map-a-server-environment.md).</span><span class="sxs-lookup"><span data-stu-id="0dd86-105">For more information about environments, see [Create and Map a Server Environment](../../2014/integration-services/create-and-map-a-server-environment.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0dd86-106">À l’instar des versions antérieures d’ [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], la version actuelle vous permet aussi de déployer vos packages sur une instance de SQL Server et d’utiliser le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] pour exécuter et gérer les packages.</span><span class="sxs-lookup"><span data-stu-id="0dd86-106">As in earlier versions of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], in the current release you can also deploy your packages to an instance of SQL Server and use [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service to run and manage the packages.</span></span> <span data-ttu-id="0dd86-107">Utilisez le modèle de déploiement de package.</span><span class="sxs-lookup"><span data-stu-id="0dd86-107">You use the package deployment model.</span></span> <span data-ttu-id="0dd86-108">Pour plus d’informations, consultez [déploiement de packages &#40;&#41;SSIS ](packages/legacy-package-deployment-ssis.md).</span><span class="sxs-lookup"><span data-stu-id="0dd86-108">For more information, see [Package Deployment &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md).</span></span>  
  
 <span data-ttu-id="0dd86-109">Pour déployer un projet sur le serveur [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , effectuez les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="0dd86-109">To deploy a project to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server, complete the following tasks:</span></span>  
  
1.  <span data-ttu-id="0dd86-110">Créez un catalogue SSISDB, si vous ne l’avez pas encore fait.</span><span class="sxs-lookup"><span data-stu-id="0dd86-110">Create an SSISDB catalog, if you haven't already.</span></span> <span data-ttu-id="0dd86-111">Pour plus d’informations, consultez [Créer le catalogue SSIS](catalog/ssis-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="0dd86-111">For more information, see [Create the SSIS Catalog](catalog/ssis-catalog.md).</span></span>  
  
2.  <span data-ttu-id="0dd86-112">Convertissez le projet en modèle de déploiement de projet en exécutant **l’Assistant Conversion de projet Integration Services** .</span><span class="sxs-lookup"><span data-stu-id="0dd86-112">Convert the project to the project deployment model by running the **Integration Services Project Conversion Wizard** .</span></span> <span data-ttu-id="0dd86-113">Pour plus d’informations, consultez les instructions ci-dessous : [Pour convertir un projet en modèle de déploiement de projet](#convert).</span><span class="sxs-lookup"><span data-stu-id="0dd86-113">For more information, see the instructions below: [To convert a project to the project deployment model](#convert)</span></span>  
  
    -   <span data-ttu-id="0dd86-114">Si vous avez créé le projet dans [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)], par défaut, le projet utilise le modèle de déploiement de projet.</span><span class="sxs-lookup"><span data-stu-id="0dd86-114">If you created the project in [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)], by default the project uses the project deployment model.</span></span>  
  
    -   <span data-ttu-id="0dd86-115">Si vous avez créé le projet dans une version précédente de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], après avoir ouvert le fichier projet dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], convertissez le projet en modèle de déploiement de projet.</span><span class="sxs-lookup"><span data-stu-id="0dd86-115">If you created the project in an earlier release of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], after you open the project file in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], convert the project to the project deployment model.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="0dd86-116">Si le projet contient une ou plusieurs sources de données, les sources de données sont supprimées quand la conversion du projet est terminée.</span><span class="sxs-lookup"><span data-stu-id="0dd86-116">If the project contains one or more datasources, the datasources are removed when the project conversion is completed.</span></span> <span data-ttu-id="0dd86-117">Pour créer une connexion à une source de données que les packages du projet peuvent partager, ajoutez un gestionnaire de connexions au niveau du projet.</span><span class="sxs-lookup"><span data-stu-id="0dd86-117">To create a connection to a data source that the packages in the project can share, add a connection manager at the project level.</span></span> <span data-ttu-id="0dd86-118">Pour plus d’informations, consultez [Ajouter, supprimer ou partager un gestionnaire de connexions dans un package](../../2014/integration-services/add-delete-or-share-a-connection-manager-in-a-package.md).</span><span class="sxs-lookup"><span data-stu-id="0dd86-118">For more information, see [Add, Delete, or Share a Connection Manager in a Package](../../2014/integration-services/add-delete-or-share-a-connection-manager-in-a-package.md).</span></span>  
  
         <span data-ttu-id="0dd86-119">Selon que vous exécutez **l’Assistant Conversion de projet Integration Services** à partir de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ou à partir de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], l’Assistant effectue différentes tâches de conversion.</span><span class="sxs-lookup"><span data-stu-id="0dd86-119">Depending on whether you run the **Integration Services Project Conversion Wizard** from [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] or from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], the wizard performs different conversion tasks.</span></span>  
  
        -   <span data-ttu-id="0dd86-120">Si vous exécutez l'Assistant à partir de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], les packages contenus dans le projet sont convertis de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 2005, 2008 ou 2008 R2 vers le format utilisé par la version en cours de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0dd86-120">If you run the wizard from [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], the packages contained in the project are converted from [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 2005, 2008, or 2008 R2 to the format that is used by the current version of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="0dd86-121">Les fichiers du projet d'origine (.dtproj) et de package (.dtsx) sont mis à niveau.</span><span class="sxs-lookup"><span data-stu-id="0dd86-121">The original project (.dtproj) and package (.dtsx) files are upgraded.</span></span>  
  
        -   <span data-ttu-id="0dd86-122">Si vous exécutez l’Assistant à partir de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], l’Assistant génère un fichier de déploiement de projet (.ispac) à partir des packages et des configurations contenus dans le projet.</span><span class="sxs-lookup"><span data-stu-id="0dd86-122">If you run the wizard from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], the wizard generates a project deployment file (.ispac) from the packages and configurations contained in the project.</span></span> <span data-ttu-id="0dd86-123">Les fichiers de package d'origine (.dtsx) ne sont pas mis à niveau.</span><span class="sxs-lookup"><span data-stu-id="0dd86-123">The original package (.dtsx) files are not upgraded.</span></span>  
  
             <span data-ttu-id="0dd86-124">Vous pouvez sélectionner un fichier existant ou en créer un dans la page **Destination de la sélection** de l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="0dd86-124">You can select an existing file or create a new file, in the **Selection Destination** page of the wizard.</span></span>  
  
             <span data-ttu-id="0dd86-125">Pour mettre à niveau des fichiers de package pendant la conversion d’un projet, exécutez **l’Assistant Conversion de projet Integration Services** à partir de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0dd86-125">To upgrade package files when a project is converted, run the **Integration Services Project Conversion Wizard** from [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="0dd86-126">Pour mettre à niveau des fichiers de package en dehors d’une conversion de projet, exécutez **l’Assistant Conversion de projet Integration Services** à partir de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] , puis exécutez **l’Assistant Mise à niveau de packages SSIS**.</span><span class="sxs-lookup"><span data-stu-id="0dd86-126">To upgrade package files separately from a project conversion, run the **Integration Services Project Conversion Wizard** from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] and then run the **SSIS Package Upgrade Wizard**.</span></span> <span data-ttu-id="0dd86-127">Si vous mettez à niveau les fichiers de package séparément, assurez-vous d'enregistrer les modifications.</span><span class="sxs-lookup"><span data-stu-id="0dd86-127">If you upgrade the package files separately, ensure that you save the changes.</span></span> <span data-ttu-id="0dd86-128">À défaut, lorsque vous convertissez le projet en modèle de déploiement de projet, les modifications non enregistrées dans le package ne sont pas converties.</span><span class="sxs-lookup"><span data-stu-id="0dd86-128">Otherwise, when you convert the project to the project deployment model, any unsaved changes to the package are not converted.</span></span>  
  
     <span data-ttu-id="0dd86-129">Pour plus d’informations sur la mise à niveau des packages, consultez [Mettre à niveau des packages Integration Services](install-windows/upgrade-integration-services-packages.md) et [Mettre à niveau des packages Integration Services à l’aide de l’Assistant Mise à niveau de packages SSIS](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md).</span><span class="sxs-lookup"><span data-stu-id="0dd86-129">For more information on package upgrade, see [Upgrade Integration Services Packages](install-windows/upgrade-integration-services-packages.md) and [Upgrade Integration Services Packages Using the SSIS Package Upgrade Wizard](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md).</span></span>  
  
3.  <span data-ttu-id="0dd86-130">Déployez le projet sur le serveur [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0dd86-130">Deploy the project to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="0dd86-131">Pour plus d’informations, consultez les instructions ci-dessous : [Pour déployer un projet sur le serveur Integration Services](#deploy).</span><span class="sxs-lookup"><span data-stu-id="0dd86-131">For more information, see the instructions below: [To deploy a project to the Integration Services Server](#deploy).</span></span>  
  
4.  <span data-ttu-id="0dd86-132">(Facultatif) Créez un environnement pour le projet déployé.</span><span class="sxs-lookup"><span data-stu-id="0dd86-132">(Optional) Create an environment for the deployed project.</span></span> <span data-ttu-id="0dd86-133">Pour plus d’informations, consultez [Créer et mapper un environnement serveur](../../2014/integration-services/create-and-map-a-server-environment.md).</span><span class="sxs-lookup"><span data-stu-id="0dd86-133">For more information, see [Create and Map a Server Environment](../../2014/integration-services/create-and-map-a-server-environment.md).</span></span>  
  
##  <a name="to-convert-a-project-to-the-project-deployment-model"></a><a name="convert"></a><span data-ttu-id="0dd86-134">Pour convertir un projet en modèle de déploiement de projet</span><span class="sxs-lookup"><span data-stu-id="0dd86-134">To convert a project to the project deployment model</span></span>  
  
1.  <span data-ttu-id="0dd86-135">Ouvrez le projet dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], puis dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet et sélectionnez **Convertir en modèle de déploiement de projet**.</span><span class="sxs-lookup"><span data-stu-id="0dd86-135">Open the project in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], and then in Solution Explorer, right-click the project and click **Convert to Project Deployment Model**.</span></span>  
  
     <span data-ttu-id="0dd86-136">-ou-</span><span class="sxs-lookup"><span data-stu-id="0dd86-136">-or-</span></span>  
  
     <span data-ttu-id="0dd86-137">Depuis l’Explorateur d’objets dans [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], cliquez avec le bouton droit sur le nœud **Projets** et sélectionnez **Importer les packages**.</span><span class="sxs-lookup"><span data-stu-id="0dd86-137">From Object Explorer in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], right-click the **Projects** node and select **Import Packages**.</span></span>  
  
2.  <span data-ttu-id="0dd86-138">Effectuez toutes les étapes de l'Assistant.</span><span class="sxs-lookup"><span data-stu-id="0dd86-138">Complete the wizard.</span></span> <span data-ttu-id="0dd86-139">Pour plus d’informations, consultez [Assistant Conversion de projet Integration Services](../../2014/integration-services/integration-services-project-conversion-wizard.md).</span><span class="sxs-lookup"><span data-stu-id="0dd86-139">For more information, see [Integration Services Project Conversion Wizard](../../2014/integration-services/integration-services-project-conversion-wizard.md).</span></span>  
  
##  <a name="to-deploy-a-project-to-the-integration-services-server"></a><a name="deploy"></a><span data-ttu-id="0dd86-140">Pour déployer un projet sur le serveur Integration Services</span><span class="sxs-lookup"><span data-stu-id="0dd86-140">To deploy a project to the Integration Services Server</span></span>  
  
1.  <span data-ttu-id="0dd86-141">Ouvrez le projet dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]puis, dans le menu **Projet** , sélectionnez **Déployer** pour lancer **l’Assistant Déploiement d’Integration Services**.</span><span class="sxs-lookup"><span data-stu-id="0dd86-141">Open the project in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], and then From the **Project** menu, select **Deploy** to launch the **Integration Services Deployment Wizard**.</span></span>  
  
     <span data-ttu-id="0dd86-142">-ou-</span><span class="sxs-lookup"><span data-stu-id="0dd86-142">-or-</span></span>  
  
     <span data-ttu-id="0dd86-143">Dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] , développez le [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]  >  nœud **SSISDB** dans l’Explorateur d’objets, puis recherchez le dossier projects pour le projet que vous souhaitez déployer.</span><span class="sxs-lookup"><span data-stu-id="0dd86-143">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], expand the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] > **SSISDB** node in Object Explorer, and locate the Projects folder for the project you want to deploy.</span></span> <span data-ttu-id="0dd86-144">Cliquez avec le bouton droit sur le dossier des **projets** , puis cliquez sur **Déployer le projet**.</span><span class="sxs-lookup"><span data-stu-id="0dd86-144">Right-click the **Projects** folder, and then click **Deploy Project**.</span></span>  
  
     <span data-ttu-id="0dd86-145">-ou-</span><span class="sxs-lookup"><span data-stu-id="0dd86-145">-or-</span></span>  
  
     <span data-ttu-id="0dd86-146">À l’invite de commandes, exécutez **isdeploymentwizard.exe** à partir de **%ProgramFiles%\Microsoft SQL Server\110\DTS\Binn**.</span><span class="sxs-lookup"><span data-stu-id="0dd86-146">From the command prompt, run **isdeploymentwizard.exe** from **%ProgramFiles%\Microsoft SQL Server\110\DTS\Binn**.</span></span> <span data-ttu-id="0dd86-147">Sur les ordinateurs 64 bits, il existe aussi une version 32 bits de l’outil dans **%ProgramFiles(x86)%\Microsoft SQL Server\100\DTS\Binn**.</span><span class="sxs-lookup"><span data-stu-id="0dd86-147">On 64-bit computers, there is also a 32-bit version of the tool in **%ProgramFiles(x86)%\Microsoft SQL Server\100\DTS\Binn**.</span></span>  
  
2.  <span data-ttu-id="0dd86-148">Dans la page **Sélectionner une source** , cliquez sur **Fichier de déploiement de projet** pour sélectionner le fichier de déploiement du projet.</span><span class="sxs-lookup"><span data-stu-id="0dd86-148">On the **Select Source** page, click **Project deployment file** to select the deployment file for the project.</span></span>  
  
     <span data-ttu-id="0dd86-149">OU</span><span class="sxs-lookup"><span data-stu-id="0dd86-149">-OR-</span></span>  
  
     <span data-ttu-id="0dd86-150">Cliquez sur **Catalogue Integration Services** pour sélectionner un projet qui a déjà été déployé dans le catalogue SSISDB.</span><span class="sxs-lookup"><span data-stu-id="0dd86-150">Click **Integration Services catalog** to select a project that has already been deployed to the SSISDB catalog.</span></span>  
  
3.  <span data-ttu-id="0dd86-151">Effectuez toutes les étapes de l'Assistant.</span><span class="sxs-lookup"><span data-stu-id="0dd86-151">Complete the wizard.</span></span> <span data-ttu-id="0dd86-152">Pour plus d’informations, consultez [Assistant Déploiement d’Integration Services](../../2014/integration-services/integration-services-deployment-wizard.md).</span><span class="sxs-lookup"><span data-stu-id="0dd86-152">For more information, see [Integration Services Deployment Wizard](../../2014/integration-services/integration-services-deployment-wizard.md).</span></span>  
  
  