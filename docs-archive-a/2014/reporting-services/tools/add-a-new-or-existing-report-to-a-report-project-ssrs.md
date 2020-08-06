---
title: Ajouter un nouveau rapport ou un rapport existant à un projet de rapport (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], creating
ms.assetid: 8bc0bb53-ad8a-464d-bb6a-7fea5fa62c5c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b66bf8ef0181b549900d984d20b1279f9b5005c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706188"
---
# <a name="add-a-new-or-existing-report-to-a-report-project-ssrs"></a><span data-ttu-id="cb253-102">Ajouter un nouveau rapport ou un rapport existant à un projet de rapport (SSRS)</span><span class="sxs-lookup"><span data-stu-id="cb253-102">Add a New or Existing Report to a Report Project (SSRS)</span></span>
  <span data-ttu-id="cb253-103">Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], vous pouvez ajouter un nouveau rapport en utilisant l'Assistant Rapport ou en ajoutant un nouveau rapport vide à votre projet.</span><span class="sxs-lookup"><span data-stu-id="cb253-103">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], you can add a new report by using the Report Wizard or by adding a new blank report to your project.</span></span> <span data-ttu-id="cb253-104">Vous pouvez aussi ajouter un rapport existant.</span><span class="sxs-lookup"><span data-stu-id="cb253-104">You can also add an existing report.</span></span> <span data-ttu-id="cb253-105">Après avoir ajouté un rapport, vous pouvez voir son nom sous le dossier **Rapports** de votre projet.</span><span class="sxs-lookup"><span data-stu-id="cb253-105">After you add a report, you can see the report name listed under the **Reports** folder in your project.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cb253-106">Pour afficher l'aperçu d'un rapport avec les sources de données existantes, vous devez disposer d'autorisations sur la source de données à partir du client de création de votre rapport.</span><span class="sxs-lookup"><span data-stu-id="cb253-106">To preview a report with existing data sources, you must have permissions to the data source from your report authoring client.</span></span> <span data-ttu-id="cb253-107">Pour plus d’informations, consultez [créer une source de données incorporée ou partagée &#40;SSRS&#41;](../create-an-embedded-or-shared-data-source-ssrs.md).</span><span class="sxs-lookup"><span data-stu-id="cb253-107">For more information, see [Create an Embedded or Shared Data Source &#40;SSRS&#41;](../create-an-embedded-or-shared-data-source-ssrs.md).</span></span>  
  
 <span data-ttu-id="cb253-108">Après avoir ajouté un rapport, vous pouvez définir des sources de données et des datasets, ainsi que concevoir la mise en page du rapport.</span><span class="sxs-lookup"><span data-stu-id="cb253-108">After you add a report, you can define data sources, datasets, and design a report layout.</span></span> <span data-ttu-id="cb253-109">Pour commencer, consultez [Créer un rapport de table de base &#40;didacticiel SSRS&#41;](../create-a-basic-table-report-ssrs-tutorial.md) ou [Tables &#40;Générateur de rapports et SSRS&#41;](../report-design/tables-report-builder-and-ssrs.md).</span><span class="sxs-lookup"><span data-stu-id="cb253-109">To get started, see [Create a Basic Table Report &#40;SSRS Tutorial&#41;](../create-a-basic-table-report-ssrs-tutorial.md) or [Tables &#40;Report Builder  and SSRS&#41;](../report-design/tables-report-builder-and-ssrs.md).</span></span>  
  
### <a name="to-add-a-new-report-using-the-report-wizard"></a><span data-ttu-id="cb253-110">Pour ajouter un nouveau rapport en utilisant l'Assistant Rapport</span><span class="sxs-lookup"><span data-stu-id="cb253-110">To add a new report using the Report Wizard</span></span>  
  
1.  <span data-ttu-id="cb253-111">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le dossier Rapports, puis sélectionnez **Ajouter un nouveau rapport**.</span><span class="sxs-lookup"><span data-stu-id="cb253-111">In Solution Explorer, right-click the Reports folder, and then click **Add New Report**.</span></span> <span data-ttu-id="cb253-112">La boîte de dialogue **Assistant Rapport** s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="cb253-112">The **Report Wizard** dialog box opens.</span></span>  
  
     <span data-ttu-id="cb253-113">Les étapes de l'Assistant vous guident à travers la création d'une source de données, la création d'un dataset avec une requête, la définition de groupes, la spécification d'une mise en page, le choix d'un style qui inclut la couleur et la police, et la création du rapport.</span><span class="sxs-lookup"><span data-stu-id="cb253-113">The wizard steps you through creating a data source, creating a dataset with a query, defining groups, specifying a layout, choosing a style that includes color and font, and creating the report.</span></span> <span data-ttu-id="cb253-114">Procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="cb253-114">The steps include:</span></span>  
  
    -   <span data-ttu-id="cb253-115">**Sélectionnez une source de données.**</span><span class="sxs-lookup"><span data-stu-id="cb253-115">**Select a Data Source.**</span></span> <span data-ttu-id="cb253-116">La première étape de création d'un rapport consiste à définir une source de données.</span><span class="sxs-lookup"><span data-stu-id="cb253-116">The first step in creating a report is to define a data source.</span></span> <span data-ttu-id="cb253-117">L'Assistant Rapport fournit la liste de toutes les sources de données partagées du projet de rapport et offre la possibilité de créer une nouvelle source de données.</span><span class="sxs-lookup"><span data-stu-id="cb253-117">Report Wizard provides a list of all shared data sources in the report project, in addition to an option to create a new data source.</span></span>  
  
    -   <span data-ttu-id="cb253-118">**Créez une requête.**</span><span class="sxs-lookup"><span data-stu-id="cb253-118">**Design a Query.**</span></span> <span data-ttu-id="cb253-119">L'étape suivante consiste à créer une requête.</span><span class="sxs-lookup"><span data-stu-id="cb253-119">The next step is to design a query.</span></span> <span data-ttu-id="cb253-120">Vous pouvez taper la chaîne de requête, la générer à l'aide du concepteur de requêtes ou importer une requête à partir d'un autre rapport.</span><span class="sxs-lookup"><span data-stu-id="cb253-120">You can type the query string, build it using Query Designer, or import a query from another report.</span></span> <span data-ttu-id="cb253-121">Pour plus d’informations sur les concepteurs de requêtes, consultez [Concepteurs de requêtes Reporting Services](../reporting-services-query-designers.md).</span><span class="sxs-lookup"><span data-stu-id="cb253-121">For information about Query Designers, see [Reporting Services Query Designers](../reporting-services-query-designers.md).</span></span>  
  
    -   <span data-ttu-id="cb253-122">**Choisissez un type de rapport.**</span><span class="sxs-lookup"><span data-stu-id="cb253-122">**Choose a Report Type.**</span></span> <span data-ttu-id="cb253-123">L'étape suivante consiste à sélectionner le type de rapport souhaité.</span><span class="sxs-lookup"><span data-stu-id="cb253-123">The next step is to select the type of report you want.</span></span> <span data-ttu-id="cb253-124">Vous pouvez choisir un rapport tabulaire ou de matrice.</span><span class="sxs-lookup"><span data-stu-id="cb253-124">You can choose a tabular or matrix report.</span></span> <span data-ttu-id="cb253-125">Un rapport tabulaire comporte un nombre fixe de colonnes.</span><span class="sxs-lookup"><span data-stu-id="cb253-125">A tabular report has a fixed number of columns.</span></span> <span data-ttu-id="cb253-126">Un rapport de matrice (ou tableau croisé dynamique) comporte un nombre variable de colonnes qui dépend des résultats de la requête.</span><span class="sxs-lookup"><span data-stu-id="cb253-126">A matrix, or crosstab, report has a variable number of columns based on the results of the query.</span></span> <span data-ttu-id="cb253-127">Un rapport cartographique affiche des informations analytiques sur un arrière-plan géographique.</span><span class="sxs-lookup"><span data-stu-id="cb253-127">A map report displays analytical against a geographic background.</span></span>  
  
    -   <span data-ttu-id="cb253-128">**Choisissez un style.**</span><span class="sxs-lookup"><span data-stu-id="cb253-128">**Choose a Style.**</span></span> <span data-ttu-id="cb253-129">L'étape suivante consiste à appliquer un style au rapport en utilisant un modèle de style.</span><span class="sxs-lookup"><span data-stu-id="cb253-129">The next step is to apply a style to the report using a style template.</span></span> <span data-ttu-id="cb253-130">Sélectionnez un modèle pour appliquer au rapport des styles comme des polices, des couleurs et des styles de bordure.</span><span class="sxs-lookup"><span data-stu-id="cb253-130">Select a template to apply styles such as font, color, and border style to the report.</span></span> <span data-ttu-id="cb253-131">Le Concepteur de rapports fournit six modèles de style : Ardoise, Forêt, Entreprise, Gras, Océan et Générique.</span><span class="sxs-lookup"><span data-stu-id="cb253-131">Report Designer provides six style templates: Slate, Forest, Corporate, Bold, Ocean, and Generic.</span></span> <span data-ttu-id="cb253-132">Vous pouvez également ajouter des modèles de style supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="cb253-132">You can also add additional style templates.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="cb253-133">Vous pouvez modifier les modèles existants ou en ajouter de nouveaux en modifiant le fichier StyleTemplates.xml dans le dossier \Program Files\Microsoft Visual Studio 10.0 \ Common7\IDE\PrivateAssemblies\Business intelligence Wizards\Reports\Styles \\<lang \> , où \<lang> est la langue que vous utilisez (par exemple, si vous utilisez la version anglaise de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , le nom du dossier est « en »).</span><span class="sxs-lookup"><span data-stu-id="cb253-133">You can alter existing templates or add new ones by editing the StyleTemplates.xml file in the \Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\Business Intelligence Wizards\Reports\Styles\\<lang\> folder, where \<lang> is the language you are using (for example, if you are using the English language version of [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], the folder name is "EN").</span></span> <span data-ttu-id="cb253-134">Ce dossier se trouve sur l'ordinateur sur lequel le Concepteur de rapports est installé.</span><span class="sxs-lookup"><span data-stu-id="cb253-134">This folder is located on the computer on which Report Designer is installed.</span></span> <span data-ttu-id="cb253-135">Il existe deux exemplaires du fichier StyleTemplates.xml.</span><span class="sxs-lookup"><span data-stu-id="cb253-135">There are two copies of the StyleTemplates.xml file.</span></span> <span data-ttu-id="cb253-136">Pour modifier les styles appliqués via l'Assistant Rapport, modifiez le fichier qui est dans le dossier créé pour la langue que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="cb253-136">To modify the styles that are applied through the Report Wizard, edit the file that is in the folder created for the language you are using.</span></span>  
  
    -   <span data-ttu-id="cb253-137">**Nommez le rapport.**</span><span class="sxs-lookup"><span data-stu-id="cb253-137">**Name the Report.**</span></span>  <span data-ttu-id="cb253-138">La dernière étape consiste à donner un nom au rapport et à vérifier les champs qui y seront inclus.</span><span class="sxs-lookup"><span data-stu-id="cb253-138">The final step is to name the report and verify the fields that will be included in the report.</span></span> <span data-ttu-id="cb253-139">Lorsque la procédure est terminée, le Concepteur de rapports crée le rapport et l'ajoute au projet du serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="cb253-139">When all steps are completed, Report Designer creates the report and adds it to the report server project.</span></span>  
  
### <a name="to-add-a-new-blank-report"></a><span data-ttu-id="cb253-140">Pour ajouter un rapport vide</span><span class="sxs-lookup"><span data-stu-id="cb253-140">To add a new blank report</span></span>  
  
1.  <span data-ttu-id="cb253-141">Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="cb253-141">From the **Project** menu, click **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="cb253-142">Dans **Modèles**, cliquez sur **Rapport**.</span><span class="sxs-lookup"><span data-stu-id="cb253-142">In **Templates**, click **Report**.</span></span>  
  
3.  <span data-ttu-id="cb253-143">Cliquez sur **Add**.</span><span class="sxs-lookup"><span data-stu-id="cb253-143">Click **Add**.</span></span>  
  
     <span data-ttu-id="cb253-144">Un nouveau rapport vide est ajouté au projet et affiché sur l'aire de conception.</span><span class="sxs-lookup"><span data-stu-id="cb253-144">A new blank report is added to the project and displayed on the design surface.</span></span>  
  
### <a name="to-add-an-existing-report"></a><span data-ttu-id="cb253-145">Pour ajouter un rapport existant</span><span class="sxs-lookup"><span data-stu-id="cb253-145">To add an existing report</span></span>  
  
1.  <span data-ttu-id="cb253-146">Dans le menu **projet** , cliquez sur **Ajouter**, puis sur **élément existant**.</span><span class="sxs-lookup"><span data-stu-id="cb253-146">From the **Project** menu, click **Add**, and then **Existing Item**.</span></span>  
  
2.  <span data-ttu-id="cb253-147">Naviguez jusqu’à l’emplacement du fichier .rdl, sélectionnez-le, puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="cb253-147">Navigate to the location of the .rdl file, select it, and then click **Add**.</span></span>  
  
     <span data-ttu-id="cb253-148">Le rapport est ajouté au projet sous le dossier **Rapports** .</span><span class="sxs-lookup"><span data-stu-id="cb253-148">The report is added to the project under the **Reports** folder.</span></span> <span data-ttu-id="cb253-149">Lorsque vous fermez et rouvrez le projet, les rapports sont triés alphabétiquement.</span><span class="sxs-lookup"><span data-stu-id="cb253-149">When you close and re-open the project, reports are sorted alphabetically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb253-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cb253-150">See Also</span></span>  
 [<span data-ttu-id="cb253-151">Didacticiels sur Reporting Services &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="cb253-151">Reporting Services Tutorials &#40;SSRS&#41;</span></span>](../reporting-services-tutorials-ssrs.md)  
  
  