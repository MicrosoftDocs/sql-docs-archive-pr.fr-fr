---
title: Interface utilisateur du Concepteur de requêtes DMX Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10012"
- sql12.rtp.rptdesigner.dataview.asquerydesigner.f1
helpviewer_keywords:
- Analysis Services [DMX]
- DMX [Analysis Services], user interface
- query designers [DMX]
ms.assetid: 5fd726a4-aed7-4e6c-9404-ccb2db66cf26
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b641423ad9563f252ba89f51fcd8cafb0ed7bbe8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601920"
---
# <a name="analysis-services-dmx-query-designer-user-interface"></a><span data-ttu-id="16c77-102">Interface utilisateur du Concepteur de requêtes DMX Analysis Services</span><span class="sxs-lookup"><span data-stu-id="16c77-102">Analysis Services DMX Query Designer User Interface</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="16c77-103">fournit des concepteurs de requêtes graphiques pour la création de requêtes DMX (Data Mining Expressions) et MDX (Multidimensional Expression) pour une source de données [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="16c77-103">provides graphical query designers for building Data Mining Expressions (DMX) queries and Multidimensional Expression (MDX) queries for an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source.</span></span> <span data-ttu-id="16c77-104">Cette rubrique offre une description du Concepteur de requêtes DMX.</span><span class="sxs-lookup"><span data-stu-id="16c77-104">This topic describes the DMX query designer.</span></span> <span data-ttu-id="16c77-105">Pour plus d’informations sur le concepteur de requêtes MDX, consultez [Interface utilisateur du Concepteur de requêtes MDX Analysis Services](analysis-services-mdx-query-designer-user-interface.md).</span><span class="sxs-lookup"><span data-stu-id="16c77-105">For more information about the MDX query designer, see [Analysis Services MDX Query Designer User Interface](analysis-services-mdx-query-designer-user-interface.md).</span></span>  
  
 <span data-ttu-id="16c77-106">Le Concepteur de requêtes graphique DMX comporte trois modes : Création, Requête et Résultat.</span><span class="sxs-lookup"><span data-stu-id="16c77-106">The DMX graphical query designer has three modes: Design, Query, and Result.</span></span> <span data-ttu-id="16c77-107">Pour passer d'un mode à l'autre, cliquez avec le bouton droit dans le volet Concepteur de requêtes et sélectionnez le mode souhaité.</span><span class="sxs-lookup"><span data-stu-id="16c77-107">To switch modes, right-click on the Query Design pane, and select the mode.</span></span> <span data-ttu-id="16c77-108">Chaque mode fournit un volet Métadonnées à partir duquel vous pouvez faire glisser des membres de cubes sélectionnés pour créer une requête DMX qui extrait des données pour un dataset lors du traitement du rapport.</span><span class="sxs-lookup"><span data-stu-id="16c77-108">Each mode provides a Metadata pane from which you can drag members from the selected cubes to build a DMX query that retrieves data for a dataset when the report is processed.</span></span>  
  
## <a name="graphical-dmx-query-designer-toolbar"></a><span data-ttu-id="16c77-109">Barres d'outils du Concepteur de requêtes graphique DMX</span><span class="sxs-lookup"><span data-stu-id="16c77-109">Graphical DMX Query Designer Toolbar</span></span>  
 <span data-ttu-id="16c77-110">La barre d'outils du Concepteur de requêtes fournit des boutons vous aidant à concevoir des requêtes DMX à l'aide de l'interface graphique.</span><span class="sxs-lookup"><span data-stu-id="16c77-110">The query designer toolbar provides buttons to help you design DMX queries using the graphical interface.</span></span> <span data-ttu-id="16c77-111">Le tableau suivant décrit ces boutons et leurs fonctions.</span><span class="sxs-lookup"><span data-stu-id="16c77-111">The following table describes the buttons and their functions.</span></span>  
  
|<span data-ttu-id="16c77-112">Bouton</span><span class="sxs-lookup"><span data-stu-id="16c77-112">Button</span></span>|<span data-ttu-id="16c77-113">Description</span><span class="sxs-lookup"><span data-stu-id="16c77-113">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="16c77-114">**Modifier en tant que texte**</span><span class="sxs-lookup"><span data-stu-id="16c77-114">**Edit As Text**</span></span>|<span data-ttu-id="16c77-115">Désactivé pour ce type de source de données.</span><span class="sxs-lookup"><span data-stu-id="16c77-115">Disabled for this data source type.</span></span>|  
|<span data-ttu-id="16c77-116">**Importer**</span><span class="sxs-lookup"><span data-stu-id="16c77-116">**Import**</span></span>|<span data-ttu-id="16c77-117">Importe une requête existante à partir d'un fichier de définition de rapport (.rdl) sur le système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="16c77-117">Import an existing query from a report definition (.rdl) file on the file system.</span></span> <span data-ttu-id="16c77-118">Pour plus d’informations, consultez [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span><span class="sxs-lookup"><span data-stu-id="16c77-118">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>|  
|<span data-ttu-id="16c77-119">![Basculer vers l'affichage des requêtes MDX](../media/rsqdicon-commandtypemdx.gif "Basculer vers l'affichage des requêtes MDX")</span><span class="sxs-lookup"><span data-stu-id="16c77-119">![Change to MDX query view](../media/rsqdicon-commandtypemdx.gif "Change to MDX query view")</span></span>|<span data-ttu-id="16c77-120">Bascule vers le mode Concepteur de requêtes MDX.</span><span class="sxs-lookup"><span data-stu-id="16c77-120">Switch to the MDX query designer mode.</span></span>|  
|<span data-ttu-id="16c77-121">![Basculer vers l'affichage de langage de requête DMX](../media/rsqdicon-commandtypedmx.gif "Basculer vers l'affichage de langage de requête DMX")</span><span class="sxs-lookup"><span data-stu-id="16c77-121">![Change to DMX query language view](../media/rsqdicon-commandtypedmx.gif "Change to DMX query language view")</span></span>|<span data-ttu-id="16c77-122">Bascule vers le mode Concepteur de requêtes DMX.</span><span class="sxs-lookup"><span data-stu-id="16c77-122">Switch to the DMX query designer mode.</span></span>|  
|<span data-ttu-id="16c77-123">![Actualiser les données du résultat](../media/rsqdicon-refresh.gif "Actualiser les données du résultat")</span><span class="sxs-lookup"><span data-stu-id="16c77-123">![Refresh result data](../media/rsqdicon-refresh.gif "Refresh result data")</span></span>|<span data-ttu-id="16c77-124">Actualise les métadonnées à partir de la source de données.</span><span class="sxs-lookup"><span data-stu-id="16c77-124">Refresh metadata from the data source.</span></span>|  
|<span data-ttu-id="16c77-125">![Supprimer](../media/rsqdicon-delete.gif "DELETE")</span><span class="sxs-lookup"><span data-stu-id="16c77-125">![Delete](../media/rsqdicon-delete.gif "Delete")</span></span>|<span data-ttu-id="16c77-126">Supprime de la requête la colonne sélectionnée dans le volet Données.</span><span class="sxs-lookup"><span data-stu-id="16c77-126">Delete the selected column in the Data pane from the query.</span></span>|  
|<span data-ttu-id="16c77-127">![Icône de la boîte de dialogue Paramètres de la requête](../media/iconqueryparameter.gif "Icône de la boîte de dialogue Paramètres de la requête")</span><span class="sxs-lookup"><span data-stu-id="16c77-127">![Icon for the Query Parameters dialog box](../media/iconqueryparameter.gif "Icon for the Query Parameters dialog box")</span></span>|<span data-ttu-id="16c77-128">Affiche la boîte de dialogue **Paramètres de la requête** .</span><span class="sxs-lookup"><span data-stu-id="16c77-128">Display the **Query Parameters** dialog box.</span></span> <span data-ttu-id="16c77-129">Si vous affectez une valeur par défaut à une variable, un paramètre de rapport correspondant est créé lorsque vous basculez vers la vue Mise en page dans le Concepteur de rapports.</span><span class="sxs-lookup"><span data-stu-id="16c77-129">When you assign a default value to a variable, a corresponding report parameter is created when you switch to the Layout view in Report Designer.</span></span>|  
|<span data-ttu-id="16c77-130">![Exécuter la requête](../media/rsqdicon-run.gif "Exécuter la requête")</span><span class="sxs-lookup"><span data-stu-id="16c77-130">![Run the query](../media/rsqdicon-run.gif "Run the query")</span></span>|<span data-ttu-id="16c77-131">Prépare la requête.</span><span class="sxs-lookup"><span data-stu-id="16c77-131">Prepare the query.</span></span>|  
|<span data-ttu-id="16c77-132">![Passer en mode Conception](../media/rsqdicon-designmode.gif "Passer en mode Création")</span><span class="sxs-lookup"><span data-stu-id="16c77-132">![Switch to Design mode](../media/rsqdicon-designmode.gif "Switch to Design mode")</span></span>|<span data-ttu-id="16c77-133">Bascule entre le mode Création et le mode Requête.</span><span class="sxs-lookup"><span data-stu-id="16c77-133">Toggle between Design mode and Query mode.</span></span> <span data-ttu-id="16c77-134">Pour passer d’une vue de résultat à l’autre, cliquez avec le bouton droit dans le volet Création et choisissez **Résultat**.</span><span class="sxs-lookup"><span data-stu-id="16c77-134">To change to result view, right-click on the Design pane and choose **Result**.</span></span>|  
  
## <a name="graphical-dmx-query-designer-in-design-mode"></a><span data-ttu-id="16c77-135">Concepteur de requêtes graphique DMX en mode Création</span><span class="sxs-lookup"><span data-stu-id="16c77-135">Graphical DMX Query Designer in Design Mode</span></span>  
 <span data-ttu-id="16c77-136">Lorsque vous modifiez un dataset qui utilise une source de données [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] qui n'a aucun cube valide, mais dispose de modèles d'exploration de données valides, le concepteur de requêtes graphique s'ouvre en mode Création.</span><span class="sxs-lookup"><span data-stu-id="16c77-136">When you edit a dataset that uses an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source that has no valid cubes but that does have valid mining models, the graphical query designer opens in Design mode.</span></span> <span data-ttu-id="16c77-137">La figure suivante présente les différents volets du mode Création.</span><span class="sxs-lookup"><span data-stu-id="16c77-137">The following figure labels the panes for Design mode.</span></span>  
  
 <span data-ttu-id="16c77-138">![Concepteur de requêtes DMX Analysis Services, mode Conception](../media/rsqd-dsawas-dmx-designmode.gif "Concepteur de requêtes DMX Analysis Services, mode Conception")</span><span class="sxs-lookup"><span data-stu-id="16c77-138">![Analysis Services DMX query designer, design view](../media/rsqd-dsawas-dmx-designmode.gif "Analysis Services DMX query designer, design view")</span></span>  
  
 <span data-ttu-id="16c77-139">Le tableau ci-dessous décrit la fonction de chaque volet.</span><span class="sxs-lookup"><span data-stu-id="16c77-139">The following table describes the function of each pane.</span></span>  
  
|<span data-ttu-id="16c77-140">Volet</span><span class="sxs-lookup"><span data-stu-id="16c77-140">Pane</span></span>|<span data-ttu-id="16c77-141">Fonction</span><span class="sxs-lookup"><span data-stu-id="16c77-141">Function</span></span>|  
|----------|--------------|  
|<span data-ttu-id="16c77-142">Volet Concepteur de requêtes</span><span class="sxs-lookup"><span data-stu-id="16c77-142">Query Design pane</span></span>|<span data-ttu-id="16c77-143">Utilisez la boîte de dialogue **Modèle d’exploration de données** et **Sélectionner une ou plusieurs tables d’entrée** pour créer la requête DMX.</span><span class="sxs-lookup"><span data-stu-id="16c77-143">Use the **Mining Model** and **Select Input Table** dialog boxes to build the DMX query.</span></span>|  
|<span data-ttu-id="16c77-144">Volet Grille</span><span class="sxs-lookup"><span data-stu-id="16c77-144">Grid pane</span></span>|<span data-ttu-id="16c77-145">Pour chaque ligne de la grille, utilisez la liste déroulante **Source** pour sélectionner une fonction ou une expression, puis choisissez les champs, les groupes, les critères ou les arguments à utiliser dans votre requête DMX.</span><span class="sxs-lookup"><span data-stu-id="16c77-145">For each row in the grid, use the **Source** drop-down list to select a function or expression, and choose fields, groups, and criteria or arguments to use in your DMX query.</span></span> <span data-ttu-id="16c77-146">Pour afficher le texte de la requête DMX résultant de vos sélections, cliquez sur le bouton **Mode Création** dans la barre d’outils.</span><span class="sxs-lookup"><span data-stu-id="16c77-146">To see the DMX query text generated by your selections, click the **Design Mode** button on the toolbar.</span></span>|  
  
 <span data-ttu-id="16c77-147">Pour exécuter la requête DMX et afficher les résultats dans le volet Résultat, cliquez avec le bouton droit dans le volet Concepteur de requêtes et sélectionnez **Résultat**.</span><span class="sxs-lookup"><span data-stu-id="16c77-147">To run the DMX query and show results in the Result pane, right-click on the Query Design pane and select **Result**.</span></span>  
  
## <a name="graphical-dmx-query-designer-in-query-mode"></a><span data-ttu-id="16c77-148">Concepteur de requêtes graphique DMX en mode Requête</span><span class="sxs-lookup"><span data-stu-id="16c77-148">Graphical DMX Query Designer in Query Mode</span></span>  
 <span data-ttu-id="16c77-149">Pour passer en mode Requête dans le concepteur de requêtes graphique, cliquez sur le bouton **Mode Création** dans la barre d’outils ou cliquez avec le bouton droit dans la zone de conception, puis choisissez **Requête** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="16c77-149">To change the graphical query designer to Query mode, click the **Design Mode** button on the toolbar or right-click on the query design surface, and choose **Query** from the shortcut menu.</span></span> <span data-ttu-id="16c77-150">Utilisez ce mode pour taper du texte DMX directement dans le volet Requête.</span><span class="sxs-lookup"><span data-stu-id="16c77-150">Use this mode to enter DMX text directly into the Query pane.</span></span>  
  
 <span data-ttu-id="16c77-151">La figure suivante présente les différents volets du mode Requête.</span><span class="sxs-lookup"><span data-stu-id="16c77-151">The following figure labels the panes for Query mode.</span></span>  
  
 <span data-ttu-id="16c77-152">![Concepteur de requêtes DMX Analysis Services, mode Requête](../media/rsqd-dsawas-dmx-querymode.gif "Concepteur de requêtes DMX Analysis Services, mode Requête")</span><span class="sxs-lookup"><span data-stu-id="16c77-152">![Analysis Services DMX query designer, query view](../media/rsqd-dsawas-dmx-querymode.gif "Analysis Services DMX query designer, query view")</span></span>  
  
 <span data-ttu-id="16c77-153">Le tableau ci-dessous décrit la fonction de chaque volet.</span><span class="sxs-lookup"><span data-stu-id="16c77-153">The following table describes the function of each pane.</span></span>  
  
|<span data-ttu-id="16c77-154">Volet</span><span class="sxs-lookup"><span data-stu-id="16c77-154">Pane</span></span>|<span data-ttu-id="16c77-155">Fonction</span><span class="sxs-lookup"><span data-stu-id="16c77-155">Function</span></span>|  
|----------|--------------|  
|<span data-ttu-id="16c77-156">Volet Concepteur de requêtes</span><span class="sxs-lookup"><span data-stu-id="16c77-156">Query Design pane</span></span>|<span data-ttu-id="16c77-157">Utilisez la boîte de dialogue **Modèle d’exploration de données** et **Sélectionner une ou plusieurs tables d’entrée** pour créer la requête DMX.</span><span class="sxs-lookup"><span data-stu-id="16c77-157">Use the **Mining Model** and **Select Input Table** dialog boxes to build the DMX query.</span></span>|  
|<span data-ttu-id="16c77-158">Volet Requête</span><span class="sxs-lookup"><span data-stu-id="16c77-158">Query pane</span></span>|<span data-ttu-id="16c77-159">Affiche ou modifie le texte de la requête DMX directement dans le volet.</span><span class="sxs-lookup"><span data-stu-id="16c77-159">View or edit DMX query text directly in the pane.</span></span> <span data-ttu-id="16c77-160">Les modifications apportées au texte de la requête DMX ne sont pas conservées si vous passez de nouveau en mode **Création** .</span><span class="sxs-lookup"><span data-stu-id="16c77-160">Changes to the DMX query text do not persist if you change back to **Design** mode.</span></span>|  
  
 <span data-ttu-id="16c77-161">Pour exécuter la requête DMX et afficher les résultats dans le volet Résultat, cliquez avec le bouton droit dans le volet Concepteur de requêtes et sélectionnez **Résultat**.</span><span class="sxs-lookup"><span data-stu-id="16c77-161">To run the DMX query and show results in the Result pane, right-click on the Query Design pane and select **Result**.</span></span>  
  
## <a name="graphical-dmx-query-designer-in-result-mode"></a><span data-ttu-id="16c77-162">Concepteur de requêtes graphique DMX en mode Résultat</span><span class="sxs-lookup"><span data-stu-id="16c77-162">Graphical DMX Query Designer in Result Mode</span></span>  
 <span data-ttu-id="16c77-163">Pour afficher le mode Résultat, cliquez avec le bouton droit dans l’aire de conception de requête, puis choisissez **Résultat** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="16c77-163">To display the Result mode, right-click the query design surface and choose **Result** from the shortcut menu.</span></span> <span data-ttu-id="16c77-164">Lorsque vous basculez vers le mode Résultat, la requête DMX s'exécute automatiquement.</span><span class="sxs-lookup"><span data-stu-id="16c77-164">When you switch to Result mode, the DMX query runs automatically.</span></span>  
  
 <span data-ttu-id="16c77-165">La figure suivante présente le Concepteur de requêtes en mode Résultat.</span><span class="sxs-lookup"><span data-stu-id="16c77-165">The following figure shows the query designer in Result mode.</span></span>  
  
 <span data-ttu-id="16c77-166">![Concepteur de requêtes DMX Analysis Services, mode Résultat](../media/rsqd-dsawas-dmx-resultmode.gif "Concepteur de requêtes DMX Analysis Services, mode Résultat")</span><span class="sxs-lookup"><span data-stu-id="16c77-166">![Analysis Services DMX query designer, result view](../media/rsqd-dsawas-dmx-resultmode.gif "Analysis Services DMX query designer, result view")</span></span>  
  
 <span data-ttu-id="16c77-167">Pour repasser en mode Création ou en mode Requête, cliquez avec le bouton droit dans le volet Résultat et sélectionnez **Conception** ou **Requête**.</span><span class="sxs-lookup"><span data-stu-id="16c77-167">To switch back to Design mode or Query mode, right-click on the Result pane and select **Design** or **Query**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16c77-168">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16c77-168">See Also</span></span>  
 <span data-ttu-id="16c77-169">[Définir des paramètres dans le Concepteur de requêtes MDX pour Analysis Services &#40;Générateur de rapports et SSRS&#41;](define-parameters-in-the-mdx-query-designer-for-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="16c77-169">[Define Parameters in the MDX Query Designer for Analysis Services &#40;Report Builder and SSRS&#41;](define-parameters-in-the-mdx-query-designer-for-analysis-services.md) </span></span>  
 <span data-ttu-id="16c77-170">[Créer un dataset partagé ou incorporé &#40;Générateur de rapports et SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="16c77-170">[Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="16c77-171">[Type de connexion Analysis Services pour DMX &#40;SSRS&#41;](analysis-services-connection-type-for-dmx-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="16c77-171">[Analysis Services Connection Type for DMX &#40;SSRS&#41;](analysis-services-connection-type-for-dmx-ssrs.md) </span></span>  
 <span data-ttu-id="16c77-172">[Récupérer des données d’un modèle d’exploration de données &#40;DMX&#41; &#40;SSRS&#41;](retrieve-data-from-a-data-mining-model-dmx-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="16c77-172">[Retrieve Data from a Data Mining Model &#40;DMX&#41; &#40;SSRS&#41;](retrieve-data-from-a-data-mining-model-dmx-ssrs.md) </span></span>  
 <span data-ttu-id="16c77-173">[Fichier de configuration RSReportDesigner](../report-server/rsreportdesigner-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="16c77-173">[RSReportDesigner Configuration File](../report-server/rsreportdesigner-configuration-file.md) </span></span>  
 <span data-ttu-id="16c77-174">[Type de connexion Analysis Services pour MDX &#40;SSRS&#41;](analysis-services-connection-type-for-mdx-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="16c77-174">[Analysis Services Connection Type for MDX &#40;SSRS&#41;](analysis-services-connection-type-for-mdx-ssrs.md) </span></span>  
 [<span data-ttu-id="16c77-175">Type de connexion Analysis Services pour DMX &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="16c77-175">Analysis Services Connection Type for DMX &#40;SSRS&#41;</span></span>](analysis-services-connection-type-for-dmx-ssrs.md)  
  
  