---
title: Visionneuses de modèles d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- displaying data mining models
- mining models [Analysis Services], viewing
- data mining [Analysis Services], models
- viewing data mining models
- mining model content
- support [data mining]
- exploring data mining models [Analysis Services]
ms.assetid: 14c8e656-f63c-4e8a-a3af-1d580e823d28
author: minewiskan
ms.author: owend
ms.openlocfilehash: 70215231f8ed7c9c218a9c3bf15c06ce59949f69
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601176"
---
# <a name="data-mining-model-viewers"></a><span data-ttu-id="ec02d-102">Visionneuses de modèle d’exploration de données</span><span class="sxs-lookup"><span data-stu-id="ec02d-102">Data Mining Model Viewers</span></span>
  <span data-ttu-id="ec02d-103">Après l’apprentissage d’un modèle d’exploration de données dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , vous pouvez explorer le modèle pour rechercher des tendances intéressantes.</span><span class="sxs-lookup"><span data-stu-id="ec02d-103">After you train a data mining model in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can explore the model to look for interesting trends.</span></span> <span data-ttu-id="ec02d-104">Étant donné que les résultats des modèles d'exploration de données sont complexes et peuvent être difficiles à comprendre dans un format brut, l'examen visuel des données constitue souvent le moyen le plus simple pour comprendre les règles et les relations que les algorithmes découvrent au sein des données.</span><span class="sxs-lookup"><span data-stu-id="ec02d-104">Because the results of mining models are complex and can be difficult to understand in a raw format, visually investigating the data is often the easiest way to understand the rules and relationships that algorithms discover within the data.</span></span>  
  
 <span data-ttu-id="ec02d-105">Chacun des algorithmes que vous utilisez pour la construction d'un modèle renvoie un type différent de résultats.</span><span class="sxs-lookup"><span data-stu-id="ec02d-105">Each algorithm that you use to build a model returns a different type of results.</span></span> <span data-ttu-id="ec02d-106">Par conséquent, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fournit une visionneuse spécifique pour chaque algorithme.</span><span class="sxs-lookup"><span data-stu-id="ec02d-106">Therefore, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] provides a separate viewer for each algorithm.</span></span> <span data-ttu-id="ec02d-107">Quand vous explorez un modèle d’exploration de données dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], le modèle s’affiche sous l’onglet **Visionneuse de modèle d’exploration de données** du Concepteur d’exploration de données, à l’aide de la visionneuse appropriée pour ce modèle.</span><span class="sxs-lookup"><span data-stu-id="ec02d-107">When you browse a mining model in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], the model is displayed on the **Mining Model Viewer** tab of Data Mining Designer, using the appropriate viewer for the model.</span></span>  
  
## <a name="how-to-use-the-model-viewers"></a><span data-ttu-id="ec02d-108">Utilisation des visionneuses de modèle</span><span class="sxs-lookup"><span data-stu-id="ec02d-108">How to Use the Model Viewers</span></span>  
 <span data-ttu-id="ec02d-109">Vous devez sélectionner le modèle d'exploration de données, puis sélectionner une visionneuse.</span><span class="sxs-lookup"><span data-stu-id="ec02d-109">First you select the mining model and then you select a viewer.</span></span> <span data-ttu-id="ec02d-110">Chaque modèle comporte toujours deux visionneuses disponibles : une visionneuse personnalisée, qui peut inclure plusieurs onglets, et la visionneuse générique.</span><span class="sxs-lookup"><span data-stu-id="ec02d-110">Each model always has two viewers available: a custom viewer, which can include multiple tabs, and the generic viewer.</span></span>  
  
 <span data-ttu-id="ec02d-111">Selon le type du modèle sélectionné, vous verrez des options très différentes pour l'exploration du modèle.</span><span class="sxs-lookup"><span data-stu-id="ec02d-111">Depending on the type of the model that you selected, you will see very different options for exploring the model.</span></span> <span data-ttu-id="ec02d-112">Les visionneuses personnalisées associées à chaque type de modèle sont adaptées à l'algorithme que vous avez utilisé pour créer le modèle d'exploration de données sélectionné.</span><span class="sxs-lookup"><span data-stu-id="ec02d-112">The custom viewers associated with each model type are tailored to the algorithm that you used to create the selected data mining model.</span></span> <span data-ttu-id="ec02d-113">Chaque visionneuse personnalisée comporte divers outils et boîtes de dialogue qui vous permettent d'explorer les statistiques et modèles, de consulter les graphiques, d'utiliser en mode interactif des seuils de probabilité ou de filtrer des éléments par nom.</span><span class="sxs-lookup"><span data-stu-id="ec02d-113">Each custom viewer has a variety of tools and dialog boxes for helping you explore the statistics and patterns in the model, view charts, or interactively work with probability thresholds or filter out items by name.</span></span>  
  
 <span data-ttu-id="ec02d-114">Le diagramme suivant illustre la différence entre une visionneuse personnalisée et la visionneuse générique pour le même modèle.</span><span class="sxs-lookup"><span data-stu-id="ec02d-114">The following diagram illustrates the difference when you choose a custom viewer and the generic viewer for the same model.</span></span>  
  
1.  <span data-ttu-id="ec02d-115">Tout d'abord, vous pouvez voir la visionneuse personnalisée qui apparaît lorsque vous sélectionnez un modèle d'exploration de données basé sur l'algorithme MTS (Microsoft Time Series).</span><span class="sxs-lookup"><span data-stu-id="ec02d-115">First, you see the custom viewer that is displayed when you select a mining model based on the Microsoft Time Series algorithm.</span></span>  
  
     <span data-ttu-id="ec02d-116">Cette visionneuse personnalisée particulière crée automatiquement un graphique de la série chronologique et fournit cinq prédictions.</span><span class="sxs-lookup"><span data-stu-id="ec02d-116">This particular custom viewer automatically creates a graph of the time series and provides five predictions.</span></span>  
  
2.  <span data-ttu-id="ec02d-117">Ensuite, vous pouvez voir le même modèle, affiché à l’aide de la **Visionneuse de l’arborescence de contenu générique Microsoft**.</span><span class="sxs-lookup"><span data-stu-id="ec02d-117">Next, you see the same model, displayed using the **Microsoft Generic Content Tree Viewer**.</span></span>  
  
     <span data-ttu-id="ec02d-118">À gauche, la visionneuse générique affiche une liste des nœuds du modèle.</span><span class="sxs-lookup"><span data-stu-id="ec02d-118">On the left, the generic viewer displays a list of the nodes in the model.</span></span> <span data-ttu-id="ec02d-119">Vous pouvez cliquer sur un nœud pour afficher son contenu dans le volet droit.</span><span class="sxs-lookup"><span data-stu-id="ec02d-119">You can click a node to view its contents in the right-hand pane.</span></span>  
  
 <span data-ttu-id="ec02d-120">![Vue d'ensemble d'un concepteur de modèle d'exploration de données](../media/generic-mining-model-tab1.gif "Vue d'ensemble d'un concepteur de modèle d'exploration de données")</span><span class="sxs-lookup"><span data-stu-id="ec02d-120">![Overview of mining model designer](../media/generic-mining-model-tab1.gif "Overview of mining model designer")</span></span>  
  
## <a name="more-about-the-microsoft-generic-content-tree-viewer"></a><span data-ttu-id="ec02d-121">En savoir plus sur la visionneuse de l'arborescence de contenu générique Microsoft</span><span class="sxs-lookup"><span data-stu-id="ec02d-121">More about the Microsoft Generic Content Tree Viewer</span></span>  
 <span data-ttu-id="ec02d-122">Chaque modèle peut également être affiché à l’aide de la [Visionneuse de l’arborescence de contenu générique Microsoft &#40;exploration de données&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).</span><span class="sxs-lookup"><span data-stu-id="ec02d-122">Each model can also be viewed using the [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span> <span data-ttu-id="ec02d-123">Cette visionneuse affiche le contenu du modèle d'exploration de données en respectant un format de table HTML standard.</span><span class="sxs-lookup"><span data-stu-id="ec02d-123">This viewer presents the contents of the mining model according to a standard HTML table format.</span></span> <span data-ttu-id="ec02d-124">Toutefois, la disposition des nœuds et le contenu de chaque nœud diffèrent considérablement selon l'algorithme utilisé pour générer les résultats.</span><span class="sxs-lookup"><span data-stu-id="ec02d-124">However, the arrangement of the nodes and the content of each node will differ greatly depending on the algorithm used to generate the results.</span></span>  
  
 <span data-ttu-id="ec02d-125">Alors que les visionneuses personnalisées sont conçues pour explorer et comprendre le modèle, la visionneuse générique est plus adaptée lorsque vous comprenez déjà le modèle et souhaitez extraire d'un nœud spécifique des statistiques ou des règles.</span><span class="sxs-lookup"><span data-stu-id="ec02d-125">Whereas the custom viewers are designed for exploring and understanding the model, the generic viewer is more useful when you already understand the model and want to extract statistics or rules from a specific node.</span></span> <span data-ttu-id="ec02d-126">Par exemple, vous pouvez utiliser la visionneuse générique quand vous voulez afficher des informations détaillées sur les modèles et les statistiques capturés par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pendant l’analyse, notamment la probabilité d’un nœud, ou une formule de régression.</span><span class="sxs-lookup"><span data-stu-id="ec02d-126">For example, you would use the generic viewer when you want to view detailed information about the patterns and statistics that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] captured during analysis, such as the probability of a node, or a regression formula.</span></span>  
  
 <span data-ttu-id="ec02d-127">Vous pouvez également écrire des *requêtes de contenu* à l’aide de DMX pour obtenir toutes les informations présentées dans cette visionneuse.</span><span class="sxs-lookup"><span data-stu-id="ec02d-127">You can also write *content queries* using DMX to get all of the information that is presented in this viewer.</span></span> <span data-ttu-id="ec02d-128">Pour plus d’informations, consultez [Requêtes de contenu &#40;Exploration de données&#41;](content-queries-data-mining.md).</span><span class="sxs-lookup"><span data-stu-id="ec02d-128">For more information, see [Content Queries &#40;Data Mining&#41;](content-queries-data-mining.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ec02d-129">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ec02d-129">In This Section</span></span>  
 <span data-ttu-id="ec02d-130">Les rubriques suivantes décrivent plus en détail chacune des visionneuses, et expliquent comment interpréter les informations qu'elles contiennent.</span><span class="sxs-lookup"><span data-stu-id="ec02d-130">The following topics describe in more detail each of the viewers, and how to interpret the information in them.</span></span>  
  
 [<span data-ttu-id="ec02d-131">Explorer un modèle à l'aide de la visionneuse d'arborescences Microsoft</span><span class="sxs-lookup"><span data-stu-id="ec02d-131">Browse a Model Using the Microsoft Tree Viewer</span></span>](browse-a-model-using-the-microsoft-tree-viewer.md)  
 <span data-ttu-id="ec02d-132">Décrit la Visionneuse d'arborescences [!INCLUDE[msCoName](../../includes/msconame-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ec02d-132">Describes the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Tree Viewer.</span></span> <span data-ttu-id="ec02d-133">Cette visionneuse affiche les modèles d'exploration de données qui sont générés avec l'algorithme MDT ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees) et l'algorithme MLR ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression).</span><span class="sxs-lookup"><span data-stu-id="ec02d-133">This viewer displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression algorithm.</span></span>  
  
 [<span data-ttu-id="ec02d-134">Explorer un modèle à l’aide de Microsoft Sequence Cluster</span><span class="sxs-lookup"><span data-stu-id="ec02d-134">Browse a Model Using the Microsoft Cluster Viewer</span></span>](browse-a-model-using-the-microsoft-cluster-viewer.md)  
 <span data-ttu-id="ec02d-135">Décrit le composant [!INCLUDE[msCoName](../../includes/msconame-md.md)] Cluster Viewer.</span><span class="sxs-lookup"><span data-stu-id="ec02d-135">Describes the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Cluster Viewer.</span></span> <span data-ttu-id="ec02d-136">Cette visionneuse affiche les modèles d’exploration de données qui sont générés avec l’algorithme MC ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering).</span><span class="sxs-lookup"><span data-stu-id="ec02d-136">This viewer displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm.</span></span>  
  
 [<span data-ttu-id="ec02d-137">Explorer un modèle à l'aide de la visionneuse de l'algorithme MTS (Microsoft Time Series)</span><span class="sxs-lookup"><span data-stu-id="ec02d-137">Browse a Model Using the Microsoft Time Series Viewer</span></span>](browse-a-model-using-the-microsoft-time-series-viewer.md)  
 <span data-ttu-id="ec02d-138">Décrit la Visionneuse de l’algorithme MTS ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series).</span><span class="sxs-lookup"><span data-stu-id="ec02d-138">Describes the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series Viewer.</span></span> <span data-ttu-id="ec02d-139">Cette visionneuse affiche les modèles d’exploration de données qui sont générés avec l’algorithme MTS ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series).</span><span class="sxs-lookup"><span data-stu-id="ec02d-139">This viewer displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series algorithm.</span></span>  
  
 [<span data-ttu-id="ec02d-140">Explorer un modèle à l'aide de la visionneuse de l'algorithme MNB (Microsoft Naive Bayes)</span><span class="sxs-lookup"><span data-stu-id="ec02d-140">Browse a Model Using the Microsoft Naive Bayes Viewer</span></span>](browse-a-model-using-the-microsoft-naive-bayes-viewer.md)  
 <span data-ttu-id="ec02d-141">Décrit la Visionneuse de l’algorithme MNB ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes).</span><span class="sxs-lookup"><span data-stu-id="ec02d-141">Describes the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes viewer.</span></span> <span data-ttu-id="ec02d-142">Cette visionneuse affiche les modèles d'exploration de données qui sont générés avec l'algorithme MNB ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes).</span><span class="sxs-lookup"><span data-stu-id="ec02d-142">This viewer displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm.</span></span>  
  
 [<span data-ttu-id="ec02d-143">Explorer un modèle à l'aide de la visionneuse de l'algorithme MSC (Microsoft Sequence Cluster)</span><span class="sxs-lookup"><span data-stu-id="ec02d-143">Browse a Model Using the Microsoft Sequence Cluster Viewer</span></span>](browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)  
 <span data-ttu-id="ec02d-144">Décrit la Visionneuse de l'algorithme MSC ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering).</span><span class="sxs-lookup"><span data-stu-id="ec02d-144">Describes the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Cluster Viewer.</span></span> <span data-ttu-id="ec02d-145">Cette visionneuse affiche les modèles d’exploration de données qui sont générés avec l’algorithme MSC ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering).</span><span class="sxs-lookup"><span data-stu-id="ec02d-145">This viewer displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering algorithm.</span></span>  
  
 [<span data-ttu-id="ec02d-146">Explorer un modèle à l'aide de la visionneuse de l'algorithme MAR (Microsoft Association Rules)</span><span class="sxs-lookup"><span data-stu-id="ec02d-146">Browse a Model Using the Microsoft Association Rules Viewer</span></span>](browse-a-model-using-the-microsoft-association-rules-viewer.md)  
 <span data-ttu-id="ec02d-147">Décrit la Visionneuse de l’algorithme MAR ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules).</span><span class="sxs-lookup"><span data-stu-id="ec02d-147">Describes the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules Viewer.</span></span> <span data-ttu-id="ec02d-148">Cette visionneuse affiche les modèles d'exploration de données qui sont générés avec l'algorithme MAR ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules).</span><span class="sxs-lookup"><span data-stu-id="ec02d-148">This viewer displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association algorithm.</span></span>  
  
 [<span data-ttu-id="ec02d-149">Explorer un modèle à l'aide de la visionneuse de l'algorithme MNN (Microsoft Neural Network)</span><span class="sxs-lookup"><span data-stu-id="ec02d-149">Browse a Model Using the Microsoft Neural Network Viewer</span></span>](browse-a-model-using-the-microsoft-neural-network-viewer.md)  
 <span data-ttu-id="ec02d-150">Décrit la Visionneuse de l'algorithme MNN ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network).</span><span class="sxs-lookup"><span data-stu-id="ec02d-150">Describes the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network Viewer.</span></span> <span data-ttu-id="ec02d-151">Cette visionneuse affiche les modèles d'exploration de données qui sont générés avec l'algorithme MNN ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network), y compris les modèles qui utilisent l'algorithme MLR ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Logistic Regression).</span><span class="sxs-lookup"><span data-stu-id="ec02d-151">This viewer displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm, including models that use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Logistic Regression algorithm.</span></span>  
  
 [<span data-ttu-id="ec02d-152">Explorer un modèle à l'aide de la visionneuse de l'arborescence de contenu générique Microsoft</span><span class="sxs-lookup"><span data-stu-id="ec02d-152">Browse a Model Using the Microsoft Generic Content Tree Viewer</span></span>](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)  
 <span data-ttu-id="ec02d-153">Décrit les informations détaillées qui sont disponibles dans la visionneuse générique pour tous les modèles d'exploration de données et fournit des exemples sur l'interprétation des informations pour chaque algorithme.</span><span class="sxs-lookup"><span data-stu-id="ec02d-153">Describes the detailed information that is available in the generic viewer for all data mining models and provides examples of how to interpret the information for each algorithm.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec02d-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec02d-154">See Also</span></span>  
 <span data-ttu-id="ec02d-155">[Algorithmes d’exploration de données &#40;Analysis Services d’exploration de données&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="ec02d-155">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="ec02d-156">Concepteur d’exploration de données</span><span class="sxs-lookup"><span data-stu-id="ec02d-156">Data Mining Designer</span></span>](data-mining-designer.md)  
  
  