---
title: Algorithme de réseau neuronal Microsoft | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- training neural networks
- output neurons [Analysis Services]
- algorithms [data mining]
- neural network algorithms [Analysis Services]
- neurons [Analysis Services]
- classification algorithms [Analysis Services]
- neural networks
- multilayer perceptron network of neurons [Analysis Services]
- hidden neurons
- Back-Propagated Delta Rule network
- input neurons [Analysis Services]
- regression algorithms [Analysis Services]
ms.assetid: 61eb4861-8a6a-4214-a4b8-1dd278ad7a68
author: minewiskan
ms.author: owend
ms.openlocfilehash: 389df77299bbf357e1b8b0f0695f03a74420f786
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87600346"
---
# <a name="microsoft-neural-network-algorithm"></a><span data-ttu-id="f81ec-102">Microsoft Neural Network Algorithm</span><span class="sxs-lookup"><span data-stu-id="f81ec-102">Microsoft Neural Network Algorithm</span></span>
  <span data-ttu-id="f81ec-103">Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , l' [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithme de réseau neuronal associe chaque état possible de l’attribut d’entrée à chaque état possible de l’attribut prévisible et utilise les données d’apprentissage pour calculer les probabilités.</span><span class="sxs-lookup"><span data-stu-id="f81ec-103">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm combines each possible state of the input attribute with each possible state of the predictable attribute, and uses the training data to calculate probabilities.</span></span> <span data-ttu-id="f81ec-104">Vous pouvez utiliser ces probabilités ultérieurement pour procéder à une classification ou à une régression ainsi que pour prédire le résultat de l'attribut prédit en fonction des attributs d'entrée.</span><span class="sxs-lookup"><span data-stu-id="f81ec-104">You can later use these probabilities for classification or regression, and to predict an outcome of the predicted attribute, based on the input attributes.</span></span>  
  
 <span data-ttu-id="f81ec-105">Un modèle d'exploration de données généré avec l'algorithme MNN ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network) peut contenir plusieurs réseaux, en fonction du nombre de colonnes utilisées soit pour l'entrée et la prédiction, soit uniquement pour la prédiction.</span><span class="sxs-lookup"><span data-stu-id="f81ec-105">A mining model that is constructed with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm can contain multiple networks, depending on the number of columns that are used for both input and prediction, or that are used only for prediction.</span></span> <span data-ttu-id="f81ec-106">Le nombre de réseaux d'un modèle d'exploration de données dépend du nombre d'états figurant dans les colonnes d'entrée et dans les colonnes prédictibles utilisées par ce modèle d'exploration de données.</span><span class="sxs-lookup"><span data-stu-id="f81ec-106">The number of networks that a single mining model contains depends on the number of states that are contained by the input columns and predictable columns that the mining model uses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f81ec-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="f81ec-107">Example</span></span>  
 <span data-ttu-id="f81ec-108">L'algorithme MNN ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network) permet d'analyser des données d'entrée complexes, telles que les données d'un processus commercial ou de fabrication, ou des problèmes d'entreprise pour lesquels une quantité significative de données d'apprentissage est disponible, mais pour lesquels des règles ne peuvent pas être facilement dérivées en utilisant d'autres algorithmes.</span><span class="sxs-lookup"><span data-stu-id="f81ec-108">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm is useful for analyzing complex input data, such as from a manufacturing or commercial process, or business problems for which a significant quantity of training data is available but for which rules cannot be easily derived by using other algorithms.</span></span>  
  
 <span data-ttu-id="f81ec-109">Voici quelques suggestions de scénarios d'utilisation de l'algorithme MNN ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network) :</span><span class="sxs-lookup"><span data-stu-id="f81ec-109">Suggested scenarios for using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm include the following:</span></span>  
  
-   <span data-ttu-id="f81ec-110">analyse de marketing et de promotion des ventes, par exemple pour mesurer le succès d'une campagne de publicité directe ou radiophonique ;</span><span class="sxs-lookup"><span data-stu-id="f81ec-110">Marketing and promotion analysis, such as measuring the success of a direct mail promotion or a radio advertising campaign.</span></span>  
  
-   <span data-ttu-id="f81ec-111">prédiction des mouvements des stocks, des fluctuations monétaires ou d'autres informations financières extrêmement inconstantes à partir des données d'historique ;</span><span class="sxs-lookup"><span data-stu-id="f81ec-111">Predicting stock movement, currency fluctuation, or other highly fluid financial information from historical data.</span></span>  
  
-   <span data-ttu-id="f81ec-112">analyse de processus de fabrication et de processus industriels.</span><span class="sxs-lookup"><span data-stu-id="f81ec-112">Analyzing manufacturing and industrial processes.</span></span>  
  
-   <span data-ttu-id="f81ec-113">Exploration de texte.</span><span class="sxs-lookup"><span data-stu-id="f81ec-113">Text mining.</span></span>  
  
-   <span data-ttu-id="f81ec-114">Tout modèle de prédiction qui analyse des relations complexes entre de nombreuses entrées et des sorties beaucoup moins nombreuses.</span><span class="sxs-lookup"><span data-stu-id="f81ec-114">Any prediction model that analyzes complex relationships between many inputs and relatively fewer outputs.</span></span>  
  
## <a name="how-the-algorithm-works"></a><span data-ttu-id="f81ec-115">Fonctionnement de l'algorithme</span><span class="sxs-lookup"><span data-stu-id="f81ec-115">How the Algorithm Works</span></span>  
 <span data-ttu-id="f81ec-116">L’algorithme MNN ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network) crée un réseau composé de trois couches de neurones maximum.</span><span class="sxs-lookup"><span data-stu-id="f81ec-116">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm creates a network that is composed of up to three layers of neurons.</span></span> <span data-ttu-id="f81ec-117">une couche d'entrée, une couche masquée facultative et une couche de sortie.</span><span class="sxs-lookup"><span data-stu-id="f81ec-117">These layers are an input layer, an optional hidden layer, and an output layer.</span></span>  
  
 <span data-ttu-id="f81ec-118">**Couche d’entrée :** Les neurones d’entrée définissent toutes les valeurs d’attribut d’entrée pour le modèle d’exploration de données, ainsi que leurs probabilités.</span><span class="sxs-lookup"><span data-stu-id="f81ec-118">**Input layer:** Input neurons define all the input attribute values for the data mining model, and their probabilities.</span></span>  
  
 <span data-ttu-id="f81ec-119">**Couche masquée :** Les neurones cachés reçoivent des entrées des neurones d’entrée et fournissent des sorties aux neurones de sortie.</span><span class="sxs-lookup"><span data-stu-id="f81ec-119">**Hidden layer:** Hidden neurons receive inputs from input neurons and provide outputs to output neurons.</span></span> <span data-ttu-id="f81ec-120">La couche masquée correspond à la couche où des poids sont affectés aux diverses probabilités des entrées.</span><span class="sxs-lookup"><span data-stu-id="f81ec-120">The hidden layer is where the various probabilities of the inputs are assigned weights.</span></span> <span data-ttu-id="f81ec-121">Un poids décrit la pertinence ou l’importance d'une entrée donnée par rapport au neurone masqué.</span><span class="sxs-lookup"><span data-stu-id="f81ec-121">A weight describes the relevance or importance of a particular input to the hidden neuron.</span></span> <span data-ttu-id="f81ec-122">Plus le poids assigné à une entrée est élevé, plus la valeur de cette entrée sera importante.</span><span class="sxs-lookup"><span data-stu-id="f81ec-122">The greater the weight that is assigned to an input, the more important the value of that input is.</span></span> <span data-ttu-id="f81ec-123">Les poids peuvent être négatifs, ce qui implique que l'entrée peut désactiver un résultat spécifique au lieu de l'activer.</span><span class="sxs-lookup"><span data-stu-id="f81ec-123">Weights can be negative, which means that the input can inhibit, rather than favor, a specific result.</span></span>  
  
 <span data-ttu-id="f81ec-124">**Couche de sortie :** Les neurones de sortie représentent des valeurs d’attribut prévisibles pour le modèle d’exploration de données.</span><span class="sxs-lookup"><span data-stu-id="f81ec-124">**Output layer:** Output neurons represent predictable attribute values for the data mining model.</span></span>  
  
 <span data-ttu-id="f81ec-125">Pour en savoir plus sur la construction et le notation des couches d’entrée, des couches masquées et des couches de sortie, consultez [Informations techniques de référence sur l’algorithme MNN (Microsoft Neural Network)](microsoft-neural-network-algorithm-technical-reference.md).</span><span class="sxs-lookup"><span data-stu-id="f81ec-125">For a detailed explanation of how the input, hidden, and output layers are constructed and scored, see [Microsoft Neural Network Algorithm Technical Reference](microsoft-neural-network-algorithm-technical-reference.md).</span></span>  
  
## <a name="data-required-for-neural-network-models"></a><span data-ttu-id="f81ec-126">Données requises pour les modèles Neural Network</span><span class="sxs-lookup"><span data-stu-id="f81ec-126">Data Required for Neural Network Models</span></span>  
 <span data-ttu-id="f81ec-127">Un modèle de réseau neuronal doit contenir une colonne clé, une ou plusieurs colonnes d'entrée et une ou plusieurs colonnes prédictibles.</span><span class="sxs-lookup"><span data-stu-id="f81ec-127">A neural network model must contain a key column, one or more input columns, and one or more predictable columns.</span></span>  
  
 <span data-ttu-id="f81ec-128">Les modèles d’exploration de données qui utilisent l’algorithme MNN ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network) sont fortement influencés par les valeurs que vous spécifiez pour les paramètres accessibles à l’algorithme.</span><span class="sxs-lookup"><span data-stu-id="f81ec-128">Data mining models that use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm are heavily influenced by the values that you specify for the parameters that are available to the algorithm.</span></span> <span data-ttu-id="f81ec-129">Les paramètres définissent comment les données sont échantillonnées, comment elles sont distribuées ou comment leur distribution est prévue dans chaque colonne, ainsi que le moment où la sélection de fonctionnalité est invoquée pour limiter les valeurs utilisées dans le modèle final.</span><span class="sxs-lookup"><span data-stu-id="f81ec-129">The parameters define how data is sampled, how data is distributed or expected to be distributed in each column, and when feature selection is invoked to limit the values that are used in the final model.</span></span>  
  
 <span data-ttu-id="f81ec-130">Pour plus d’informations sur la définition des paramètres permettant de personnaliser le comportement d’un modèle, consultez [Informations techniques de référence sur l’algorithme MNN (Microsoft Neural Network)](microsoft-neural-network-algorithm-technical-reference.md).</span><span class="sxs-lookup"><span data-stu-id="f81ec-130">For more information about setting parameters to customize model behavior, see [Microsoft Neural Network Algorithm Technical Reference](microsoft-neural-network-algorithm-technical-reference.md).</span></span>  
  
## <a name="viewing-a-neural-network-model"></a><span data-ttu-id="f81ec-131">Affichage d’un modèle Neural Network</span><span class="sxs-lookup"><span data-stu-id="f81ec-131">Viewing a Neural Network Model</span></span>  
 <span data-ttu-id="f81ec-132">Pour utiliser les données et voir comment le modèle met en corrélation les entrées et les sorties, vous pouvez utiliser la **Visionneuse de l’algorithme MNN (Microsoft Neural Network)**.</span><span class="sxs-lookup"><span data-stu-id="f81ec-132">To work with the data and see how the model correlates inputs with outputs, you can use the **Microsoft Neural Network Viewer**.</span></span> <span data-ttu-id="f81ec-133">Cette visionneuse personnalisée vous permet de définir des filtres sur les attributs d’entrée et leurs valeurs et présentent des graphiques qui illustrent leur impact sur les sorties.</span><span class="sxs-lookup"><span data-stu-id="f81ec-133">With this custom viewer, you can filter on input attributes and their values, and see graphs that show how they affect the outputs.</span></span> <span data-ttu-id="f81ec-134">Les info-bulles de la visionneuse montrent la probabilité et l'élévation associées à chaque paire de valeurs d'entrée et de sortie.</span><span class="sxs-lookup"><span data-stu-id="f81ec-134">The tooltips in the viewer show you the probability and lift associated with each pair of input and output values.</span></span> <span data-ttu-id="f81ec-135">Pour plus d’informations, consultez [Explorer un modèle à l’aide de la visionneuse de l’algorithme MNN (Microsoft Neural Network)](browse-a-model-using-the-microsoft-neural-network-viewer.md).</span><span class="sxs-lookup"><span data-stu-id="f81ec-135">For more information, see [Browse a Model Using the Microsoft Neural Network Viewer](browse-a-model-using-the-microsoft-neural-network-viewer.md).</span></span>  
  
 <span data-ttu-id="f81ec-136">Le moyen le plus simple d’explorer la structure du modèle est d’utiliser la **Visionneuse de l’arborescence de contenu générique Microsoft**.</span><span class="sxs-lookup"><span data-stu-id="f81ec-136">The easiest way to explore the structure of the model is to use the **Microsoft Generic Content Tree Viewer**.</span></span> <span data-ttu-id="f81ec-137">Vous pouvez consulter les entrées, les sorties et les réseaux créés par le modèle et cliquer sur n’importe quel nœud pour le développer et consulter les statistiques liées aux nœuds des couches d’entrée, de sortie ou masquée.</span><span class="sxs-lookup"><span data-stu-id="f81ec-137">You can view the inputs, outputs, and networks created by the model, and click on any node to expand it and see statistics related to the input, output, or hidden layer nodes.</span></span> <span data-ttu-id="f81ec-138">Pour plus d’informations, consultez [Explorer un modèle à l’aide de la visionneuse de l’arborescence de contenu générique Microsoft](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md).</span><span class="sxs-lookup"><span data-stu-id="f81ec-138">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md).</span></span>  
  
## <a name="creating-predictions"></a><span data-ttu-id="f81ec-139">Création de prédictions</span><span class="sxs-lookup"><span data-stu-id="f81ec-139">Creating Predictions</span></span>  
 <span data-ttu-id="f81ec-140">Une fois le modèle traité, vous pouvez utiliser le réseau et les poids stockés au sein de chaque nœud pour faire des prédictions.</span><span class="sxs-lookup"><span data-stu-id="f81ec-140">After the model has been processed, you can use the network and the weights stored within each node to make predictions.</span></span> <span data-ttu-id="f81ec-141">Un modèle de réseau neuronal prend en charge la régression, l’association et l’analyse de classification. Par conséquent, la signification de chaque prédiction peut être différente.</span><span class="sxs-lookup"><span data-stu-id="f81ec-141">A neural network model supports regression, association, and classification analysis, Therefore, the meaning of each prediction might be different.</span></span> <span data-ttu-id="f81ec-142">Vous pouvez également interroger le modèle lui-même pour examiner les corrélations qui ont été trouvées et extraire les statistiques connexes.</span><span class="sxs-lookup"><span data-stu-id="f81ec-142">You can also query the model itself, to review the correlations that were found and retrieve related statistics.</span></span> <span data-ttu-id="f81ec-143">Pour obtenir des exemples de création de requêtes sur un modèle de réseau neuronal, consultez [Exemples de requêtes de modèle de réseau neuronal](neural-network-model-query-examples.md).</span><span class="sxs-lookup"><span data-stu-id="f81ec-143">For examples of how to create queries against a neural network model, see [Neural Network Model Query Examples](neural-network-model-query-examples.md).</span></span>  
  
 <span data-ttu-id="f81ec-144">Pour obtenir des informations générales sur la création d’une requête sur un modèle d’exploration de données, consultez [Requêtes d’exploration de données](data-mining-queries.md).</span><span class="sxs-lookup"><span data-stu-id="f81ec-144">For general information about how to create a query on a data mining model, see [Data Mining Queries](data-mining-queries.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f81ec-145">Notes</span><span class="sxs-lookup"><span data-stu-id="f81ec-145">Remarks</span></span>  
  
-   <span data-ttu-id="f81ec-146">Ne prend pas en charge l’extraction ou les dimensions d’exploration de données.</span><span class="sxs-lookup"><span data-stu-id="f81ec-146">Does not support drillthrough or data mining dimensions.</span></span> <span data-ttu-id="f81ec-147">Cela est dû au fait que la structure des nœuds du modèle d'exploration de données ne correspond pas nécessairement directement aux données sous-jacentes.</span><span class="sxs-lookup"><span data-stu-id="f81ec-147">This is because the structure of the nodes in the mining model does not necessarily correspond directly to the underlying data.</span></span>  
  
-   <span data-ttu-id="f81ec-148">Ne prend pas en charge la création de modèles au format de langage PMML (Predictive Model Markup Language).</span><span class="sxs-lookup"><span data-stu-id="f81ec-148">Does not support the creation of models in Predictive Model Markup Language (PMML) format.</span></span>  
  
-   <span data-ttu-id="f81ec-149">Prend en charge l'utilisation de modèles d'exploration de données OLAP.</span><span class="sxs-lookup"><span data-stu-id="f81ec-149">Supports the use of OLAP mining models.</span></span>  
  
-   <span data-ttu-id="f81ec-150">Ne prend pas en charge la création de dimensions d’exploration de données.</span><span class="sxs-lookup"><span data-stu-id="f81ec-150">Does not support the creation of data mining dimensions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f81ec-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f81ec-151">See Also</span></span>  
 <span data-ttu-id="f81ec-152">[Informations techniques de référence sur l’algorithme Microsoft neuronal Network](microsoft-neural-network-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="f81ec-152">[Microsoft Neural Network Algorithm Technical Reference](microsoft-neural-network-algorithm-technical-reference.md) </span></span>  
 <span data-ttu-id="f81ec-153">[Contenu du modèle d’exploration de données pour les modèles de réseau neuronal &#40;Analysis Services d’exploration de données&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="f81ec-153">[Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="f81ec-154">[Exemples de requêtes de modèle de réseau neuronal](neural-network-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="f81ec-154">[Neural Network Model Query Examples](neural-network-model-query-examples.md) </span></span>  
 [<span data-ttu-id="f81ec-155">Algorithme MLR (Microsoft Logistic Regression)</span><span class="sxs-lookup"><span data-stu-id="f81ec-155">Microsoft Logistic Regression Algorithm</span></span>](microsoft-logistic-regression-algorithm.md)  
  
  