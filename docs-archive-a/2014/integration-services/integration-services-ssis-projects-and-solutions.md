---
title: Projets Integration Services (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- projects [Integration Services], creating
- folders [Integration Services], projects
- files [Integration Services], projects
- folders [Integration Services]
- projects [Integration Services], about projects
ms.assetid: 28ea8120-0a79-4029-93f0-07d521b32bee
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f71555a5339412bd0b79492607769d744c0d1a89
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605612"
---
# <a name="integration-services-ssis-projects"></a><span data-ttu-id="9d250-102">Projets Integration Services (SSIS)</span><span class="sxs-lookup"><span data-stu-id="9d250-102">Integration Services (SSIS) Projects</span></span>
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="9d250-103">fournit [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour le développement de packages [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9d250-103">provides [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] for the development of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span>

 <span data-ttu-id="9d250-104">Lorsque vous déployez des packages sur une [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] base de données ou le magasin de packages [!INCLUDE[ssIS](../includes/ssis-md.md)] , vous utilisez le [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service pour gérer les packages.</span><span class="sxs-lookup"><span data-stu-id="9d250-104">When you deploy packages to a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database or the [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Store, you use the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service to manage the packages.</span></span> <span data-ttu-id="9d250-105">Le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] n'est disponible que dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9d250-105">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is available only in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="9d250-106">Pour plus d’informations sur le service, consultez [Service Integration Services &#40;Service SSIS&#41;](service/integration-services-service-ssis-service.md).</span><span class="sxs-lookup"><span data-stu-id="9d250-106">For more information about the service, see [Integration Services Service &#40;SSIS Service&#41;](service/integration-services-service-ssis-service.md).</span></span> <span data-ttu-id="9d250-107">Pour plus d’informations sur le déploiement de packages, consultez [déploiement de packages &#40;&#41;SSIS ](packages/legacy-package-deployment-ssis.md).</span><span class="sxs-lookup"><span data-stu-id="9d250-107">For more information about package deployment, see [Package Deployment &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md).</span></span>

 <span data-ttu-id="9d250-108">Lorsque vous déployez des projets [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur le serveur [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], vous utilisez des procédures stockées et des vues Transact-SQL dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour gérer les projets.</span><span class="sxs-lookup"><span data-stu-id="9d250-108">When you deploy [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server, you use Transact-SQL views and stored procedures in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to manage the projects.</span></span> <span data-ttu-id="9d250-109">Pour plus d'informations sur le déploiement de projets, consultez [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md).</span><span class="sxs-lookup"><span data-stu-id="9d250-109">For more information about project deployment, see [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md).</span></span> <span data-ttu-id="9d250-110">Pour plus d’informations sur le serveur [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], consultez [Serveur Integration Services &#40;SSIS&#41;](catalog/integration-services-ssis-server-and-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="9d250-110">For more information about the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server, see [Integration Services &#40;SSIS&#41; Server](catalog/integration-services-ssis-server-and-catalog.md).</span></span>

 <span data-ttu-id="9d250-111">Pour obtenir une vue d’ensemble de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] et [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], consultez [Integration Services &#40;SSIS&#41; et environnements de Studio](integration-services-ssis-development-and-management-tools.md).</span><span class="sxs-lookup"><span data-stu-id="9d250-111">For an overview of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], see [Integration Services &#40;SSIS&#41; and Studio Environments](integration-services-ssis-development-and-management-tools.md).</span></span>

## <a name="understanding-integration-services-projects"></a><span data-ttu-id="9d250-112">Fonctionnement des projets Integration Services</span><span class="sxs-lookup"><span data-stu-id="9d250-112">Understanding Integration Services Projects</span></span>
 <span data-ttu-id="9d250-113">Un projet est un conteneur dans lequel vous développez des packages [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9d250-113">A project is a container in which you develop [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span>

 <span data-ttu-id="9d250-114">Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] stocke et groupe les fichiers associés au package.</span><span class="sxs-lookup"><span data-stu-id="9d250-114">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project stores and groups the files that are related to the package.</span></span> <span data-ttu-id="9d250-115">Par exemple, un projet inclut les fichiers requis pour créer une solution d'extraction, de transfert et de chargement (ETL) spécifique.</span><span class="sxs-lookup"><span data-stu-id="9d250-115">For example, a project includes the files that are required to create a specific extract, transfer, and load (ETL) solution.</span></span>

 <span data-ttu-id="9d250-116">Avant de créer un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , vous devez vous familiariser avec le contenu de base de ce type de projet.</span><span class="sxs-lookup"><span data-stu-id="9d250-116">Before you create an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, you should become familiar with the basic contents of this kind of project.</span></span> <span data-ttu-id="9d250-117">Une fois que vous connaissez le contenu d'un projet, vous pouvez commencer à créer et à utiliser un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9d250-117">After you understand what a project contains, you can begin creating and working with an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>

### <a name="folders-in-integration-services-projects"></a><span data-ttu-id="9d250-118">Dossiers des projets Integration Services</span><span class="sxs-lookup"><span data-stu-id="9d250-118">Folders in Integration Services Projects</span></span>
 <span data-ttu-id="9d250-119">Le diagramme qui suit montre les dossiers d'un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9d250-119">The following diagram shows the folders in an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>

 <span data-ttu-id="9d250-120">![Dossiers d'un projet Integration Services](media/solutionexplorer.gif "Dossiers d'un projet Integration Services")</span><span class="sxs-lookup"><span data-stu-id="9d250-120">![Folders in an Integration Services project](media/solutionexplorer.gif "Folders in an Integration Services project")</span></span>

 <span data-ttu-id="9d250-121">Le tableau suivant décrit les dossiers d'un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9d250-121">The following table describes the folders that appear in an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>

|<span data-ttu-id="9d250-122">Dossier</span><span class="sxs-lookup"><span data-stu-id="9d250-122">Folder</span></span>|<span data-ttu-id="9d250-123">Description</span><span class="sxs-lookup"><span data-stu-id="9d250-123">Description</span></span>|
|------------|-----------------|
|[!INCLUDE[ssIS](../includes/ssis-md.md)] <span data-ttu-id="9d250-124">.</span><span class="sxs-lookup"><span data-stu-id="9d250-124">Packages</span></span>|<span data-ttu-id="9d250-125">Contient les packages.</span><span class="sxs-lookup"><span data-stu-id="9d250-125">Contains packages.</span></span> <span data-ttu-id="9d250-126">Pour plus d’informations, consultez [Integration Services &#40;SSIS&#41;, packages](../../2014/integration-services/integration-services-ssis-packages.md).</span><span class="sxs-lookup"><span data-stu-id="9d250-126">For more information, see [Integration Services &#40;SSIS&#41; Packages](../../2014/integration-services/integration-services-ssis-packages.md).</span></span>|
|<span data-ttu-id="9d250-127">Divers</span><span class="sxs-lookup"><span data-stu-id="9d250-127">Miscellaneous</span></span>|<span data-ttu-id="9d250-128">Contient d'autres fichiers que les fichiers de package.</span><span class="sxs-lookup"><span data-stu-id="9d250-128">Contains files other than package files.</span></span>|

### <a name="files-in-integration-services-projects"></a><span data-ttu-id="9d250-129">Fichiers des projets Integration Services</span><span class="sxs-lookup"><span data-stu-id="9d250-129">Files in Integration Services Projects</span></span>
 <span data-ttu-id="9d250-130">Lorsque vous ajoutez un nouveau projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ou un projet existant à une solution, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] crée des fichiers projet portant les extensions .dtproj, .dtproj.user et .database.</span><span class="sxs-lookup"><span data-stu-id="9d250-130">When you add a new or an existing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project to a solution, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] creates project files that have the extensions .dtproj and .dtproj.user and .database.</span></span>

-   <span data-ttu-id="9d250-131">Le fichier \*.dtproj contient des informations sur les configurations du projet et sur d'autres éléments tels que les packages.</span><span class="sxs-lookup"><span data-stu-id="9d250-131">The \*.dtproj file contains information about project configurations and items such as packages.</span></span>

-   <span data-ttu-id="9d250-132">Le fichier \*.dtproj.user contient des informations sur vos préférences de travail avec le projet.</span><span class="sxs-lookup"><span data-stu-id="9d250-132">The \*.dtproj.user file contains information about your preferences for working with the project.</span></span>

-   <span data-ttu-id="9d250-133">Le fichier \*.database contient des informations requises par [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour ouvrir le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9d250-133">The \*.database file contains information that [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] requires to open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>

## <a name="understanding-solutions"></a><span data-ttu-id="9d250-134">Fonctionnement des solutions</span><span class="sxs-lookup"><span data-stu-id="9d250-134">Understanding Solutions</span></span>
 <span data-ttu-id="9d250-135">Une solution est un conteneur qui regroupe et gère les projets que vous utilisez lorsque vous développez des solutions d'entreprise de bout en bout.</span><span class="sxs-lookup"><span data-stu-id="9d250-135">A solution is a container that groups and manages the projects that you use when you develop end-to-end business solutions.</span></span> <span data-ttu-id="9d250-136">Une solution vous permet de gérer plusieurs projets en une même unité et de regrouper plusieurs projets qui contribuent à une solution d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="9d250-136">A solution lets you handle multiple projects as one unit and to bring together one or more related projects that contribute to a business solution.</span></span>

 <span data-ttu-id="9d250-137">Une solution peut contenir des projets de différents types.</span><span class="sxs-lookup"><span data-stu-id="9d250-137">Solutions can include different types of projects.</span></span> <span data-ttu-id="9d250-138">Si vous souhaitez utiliser le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] pour créer un package [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , vous travaillez dans un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] dans une solution fournie par [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9d250-138">If you want to use [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer to create an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package, you work in an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in a solution provided by [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>

 <span data-ttu-id="9d250-139">Lorsque vous créez une nouvelle solution, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ajoute un dossier Solution à l'Explorateur de solutions et crée des fichiers portant les extensions .sln et .suo :</span><span class="sxs-lookup"><span data-stu-id="9d250-139">When you create a new solution, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] adds a Solution folder to Solution Explorer, and creates files that have the extensions, .sln and .suo:</span></span>

-   <span data-ttu-id="9d250-140">Le fichier \*.sln contient des informations sur la configuration de la solution et répertorie les projets de la solution.</span><span class="sxs-lookup"><span data-stu-id="9d250-140">The \*.sln file contains information about the solution configuration and lists the projects in the solution.</span></span>

-   <span data-ttu-id="9d250-141">Le fichier \*.suo contient des informations sur vos préférences concernant l'utilisation de la solution.</span><span class="sxs-lookup"><span data-stu-id="9d250-141">The \*.suo file contains information about your preferences for working with the solution.</span></span>

 <span data-ttu-id="9d250-142">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] crée automatiquement une solution lorsque vous créez un projet, mais vous pouvez aussi créer une solution vierge et lui ajouter ultérieurement des projets.</span><span class="sxs-lookup"><span data-stu-id="9d250-142">While [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] automatically creates a solution when you create a new project, you can also create a blank solution, and then add projects later.</span></span>

> [!NOTE]
>  <span data-ttu-id="9d250-143">Par défaut, lorsque vous créez un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], la solution n'est pas affichée dans le volet **Explorateur de projets** .</span><span class="sxs-lookup"><span data-stu-id="9d250-143">By default, when you create a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], the solution is not shown in the **Project Explorer** pane.</span></span> <span data-ttu-id="9d250-144">Pour modifier ce comportement par défaut, dans le menu **Outils** , cliquez sur **Options**.</span><span class="sxs-lookup"><span data-stu-id="9d250-144">To change this default behavior, on the **Tools** menus, click **Options**.</span></span> <span data-ttu-id="9d250-145">Dans la boîte de dialogue **Options** , développez **Projets et solutions**, puis cliquez sur **Général**.</span><span class="sxs-lookup"><span data-stu-id="9d250-145">In the **Options** dialog box, expand **Projects and Solutions**, and then click **General**.</span></span> <span data-ttu-id="9d250-146">Dans la page **Général** , sélectionnez **Toujours afficher la solution**.</span><span class="sxs-lookup"><span data-stu-id="9d250-146">On the **General** page, select **Always show solution**.</span></span>

## <a name="related-tasks"></a><span data-ttu-id="9d250-147">Tâches associées</span><span class="sxs-lookup"><span data-stu-id="9d250-147">Related Tasks</span></span>
 [<span data-ttu-id="9d250-148">Ajouter ou supprimer un projet Integration Services dans une solution</span><span class="sxs-lookup"><span data-stu-id="9d250-148">Add or Remove an Integration Services Project in a Solution</span></span>](../../2014/integration-services/add-or-remove-an-integration-services-project-in-a-solution.md)

 [<span data-ttu-id="9d250-149">Créer un projet de Integration Services</span><span class="sxs-lookup"><span data-stu-id="9d250-149">Create a New Integration Services Project</span></span>](../../2014/integration-services/create-a-new-integration-services-project.md)

 [<span data-ttu-id="9d250-150">Ajouter un élément à un projet Integration Services</span><span class="sxs-lookup"><span data-stu-id="9d250-150">Add an Item to an Integration Services Project</span></span>](../../2014/integration-services/add-an-item-to-an-integration-services-project.md)

 [<span data-ttu-id="9d250-151">Copier des éléments de projet</span><span class="sxs-lookup"><span data-stu-id="9d250-151">Copy Project Items</span></span>](../../2014/integration-services/copy-project-items.md)

## <a name="related-content"></a><span data-ttu-id="9d250-152">Contenu associé</span><span class="sxs-lookup"><span data-stu-id="9d250-152">Related Content</span></span>
 [<span data-ttu-id="9d250-153">Développement d'un projet Integration Services</span><span class="sxs-lookup"><span data-stu-id="9d250-153">Development of an Integration Services Project</span></span>](../../2014/integration-services/development-of-an-integration-services-project.md)

