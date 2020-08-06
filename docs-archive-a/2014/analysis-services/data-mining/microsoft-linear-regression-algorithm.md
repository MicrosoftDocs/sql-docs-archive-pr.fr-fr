---
title: Algorithme de régression linéaire Microsoft | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- algorithms [data mining]
- linear regression algorithms [Analysis Services]
- linear regression [Analysis Services]
- regression algorithms [Analysis Services]
ms.assetid: 50a4abb8-c0b0-4380-ba5e-c49b305b9d22
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6d03f4d60131471d1a978fd66306cc73f274a536
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87614257"
---
# <a name="microsoft-linear-regression-algorithm"></a><span data-ttu-id="eb600-102">Algorithme MLR (Microsoft Linear Regression)</span><span class="sxs-lookup"><span data-stu-id="eb600-102">Microsoft Linear Regression Algorithm</span></span>
  <span data-ttu-id="eb600-103">L’algorithme MLR ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression) est une variante de l’algorithme MDT ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees) qui vous permet de calculer une relation linéaire entre une variable dépendante et indépendante, puis d’utiliser cette relation pour la prédiction.</span><span class="sxs-lookup"><span data-stu-id="eb600-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression algorithm is a variation of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm that helps you calculate a linear relationship between a dependent and independent variable, and then use that relationship for prediction.</span></span>

 <span data-ttu-id="eb600-104">La relation se présente sous la forme d'une équation correspondant à la droite représentant le mieux une série de données.</span><span class="sxs-lookup"><span data-stu-id="eb600-104">The relationship takes the form of an equation for a line that best represents a series of data.</span></span> <span data-ttu-id="eb600-105">Par exemple, la droite dans le diagramme suivant est la meilleure représentation linéaire possible des données.</span><span class="sxs-lookup"><span data-stu-id="eb600-105">For example, the line in the following diagram is the best possible linear representation of the data.</span></span>

 <span data-ttu-id="eb600-106">![Ligne qui modélise un ensemble de données](../media/linear-regression.gif "Ligne qui modélise un ensemble de données")</span><span class="sxs-lookup"><span data-stu-id="eb600-106">![A line that models a set of data](../media/linear-regression.gif "A line that models a set of data")</span></span>

 <span data-ttu-id="eb600-107">Pour chaque point de données du diagramme, une erreur est associée à la distance entre le point et la droite de régression.</span><span class="sxs-lookup"><span data-stu-id="eb600-107">Each data point in the diagram has an error associated with its distance from the regression line.</span></span> <span data-ttu-id="eb600-108">Les coefficients a et b de l’équation de régression ajustent l’angle et l’emplacement de la droite de régression.</span><span class="sxs-lookup"><span data-stu-id="eb600-108">The coefficients a and b in the regression equation adjust the angle and location of the regression line.</span></span> <span data-ttu-id="eb600-109">Vous pouvez obtenir l’équation de régression en ajustant a et b jusqu’à ce que la somme des erreurs associées à tous les points atteigne le plus petit nombre possible.</span><span class="sxs-lookup"><span data-stu-id="eb600-109">You can obtain the regression equation by adjusting a and b until the sum of the errors that are associated with all the points reaches its minimum.</span></span>

 <span data-ttu-id="eb600-110">Il existe d'autres types de régression qui font appel à plusieurs variables ainsi que les méthodes non linéaires de régression.</span><span class="sxs-lookup"><span data-stu-id="eb600-110">There are other kinds of regression that use multiple variables, and also nonlinear methods of regression.</span></span> <span data-ttu-id="eb600-111">Toutefois, la régression linéaire est une méthode utile et connue pour modéliser une réponse à une modification dans certain facteur sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="eb600-111">However, linear regression is a useful and well-known method for modeling a response to a change in some underlying factor.</span></span>

## <a name="example"></a><span data-ttu-id="eb600-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="eb600-112">Example</span></span>
 <span data-ttu-id="eb600-113">Vous pouvez utiliser la régression linéaire pour déterminer une relation entre deux colonnes continues.</span><span class="sxs-lookup"><span data-stu-id="eb600-113">You can use linear regression to determine a relationship between two continuous columns.</span></span> <span data-ttu-id="eb600-114">Par exemple, vous pouvez utiliser la régression linéaire pour calculer une courbe de tendance à partir de données de fabrication ou de ventes.</span><span class="sxs-lookup"><span data-stu-id="eb600-114">For example, you can use linear regression to compute a trend line from manufacturing or sales data.</span></span> <span data-ttu-id="eb600-115">Vous pouvez aussi utiliser la régression linéaire en précurseur du développement de modèles d'exploration de données plus complexes afin d'évaluer les relations parmi les colonnes de données.</span><span class="sxs-lookup"><span data-stu-id="eb600-115">You could also use the linear regression as a precursor to development of more complex data mining models, to assess the relationships among data columns.</span></span>

 <span data-ttu-id="eb600-116">Même s’il y a de nombreuses méthodes pour calculer la régression linéaire qui ne nécessitent pas d’outils d’exploration de données, l’avantage de l’utilisation de l’algorithme MLR ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression) pour cette tâche est de pouvoir calculer et tester automatiquement toutes les relations possibles parmi les variables.</span><span class="sxs-lookup"><span data-stu-id="eb600-116">Although there are many ways to compute linear regression that do not require data mining tools, the advantage of using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression algorithm for this task is that all the possible relationships among the variables are automatically computed and tested.</span></span> <span data-ttu-id="eb600-117">Vous n'êtes pas obligé de sélectionner une méthode de calcul, telle que la résolution des moindres carrés.</span><span class="sxs-lookup"><span data-stu-id="eb600-117">You do not have to select a computation method, such as solving for least squares.</span></span> <span data-ttu-id="eb600-118">Toutefois, la régression linéaire peut simplifier à l'extrême les relations dans les scénarios où plusieurs facteurs affectent le résultat.</span><span class="sxs-lookup"><span data-stu-id="eb600-118">However, linear regression might oversimplify the relationships in scenarios where multiple factors affect the outcome.</span></span>

## <a name="how-the-algorithm-works"></a><span data-ttu-id="eb600-119">Fonctionnement de l'algorithme</span><span class="sxs-lookup"><span data-stu-id="eb600-119">How the Algorithm Works</span></span>
 <span data-ttu-id="eb600-120">L’algorithme MLR ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression) est une variante de l’algorithme MDT ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees).</span><span class="sxs-lookup"><span data-stu-id="eb600-120">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression algorithm is a variation of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm.</span></span> <span data-ttu-id="eb600-121">Quand vous sélectionnez l’algorithme MLR ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression), un cas spécial de l’algorithme MDT ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees) est appelé, avec des paramètres qui limitent le comportement de l’algorithme et requièrent certains types de données d’entrée.</span><span class="sxs-lookup"><span data-stu-id="eb600-121">When you select the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression algorithm, a special case of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm is invoked, with parameters that constrain the behavior of the algorithm and require certain input data types.</span></span> <span data-ttu-id="eb600-122">De plus, dans un modèle de régression linéaire, le jeu de données entier est utilisé pour calculer des relations dans le passage initial, alors qu'un modèle d'arbres de décision standard fractionne à plusieurs reprises les données en sous-ensembles ou arborescences plus petits.</span><span class="sxs-lookup"><span data-stu-id="eb600-122">Moreover, in a linear regression model, the whole data set is used for computing relationships in the initial pass, whereas a standard decision trees model splits the data repeatedly into smaller subsets or trees.</span></span>

## <a name="data-required-for-linear-regression-models"></a><span data-ttu-id="eb600-123">Données requises pour les modèles de régression linéaire</span><span class="sxs-lookup"><span data-stu-id="eb600-123">Data Required for Linear Regression Models</span></span>
 <span data-ttu-id="eb600-124">Lorsque vous préparez des données à utiliser dans un modèle de régression linéaire, vous devez comprendre les spécifications liées à l'algorithme.</span><span class="sxs-lookup"><span data-stu-id="eb600-124">When you prepare data for use in a linear regression model, you should understand the requirements for the particular algorithm.</span></span> <span data-ttu-id="eb600-125">Cela comprend la quantité de données requise et le mode d'utilisation de ces données.</span><span class="sxs-lookup"><span data-stu-id="eb600-125">This includes how much data is needed, and how the data is used.</span></span> <span data-ttu-id="eb600-126">Les spécifications pour ce type de modèle sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="eb600-126">The requirements for this model type are as follows:</span></span>

-   <span data-ttu-id="eb600-127">**Colonne à index unique** : chaque modèle doit contenir une colonne numérique ou une colonne de texte qui identifie de façon unique chaque enregistrement.</span><span class="sxs-lookup"><span data-stu-id="eb600-127">**A single key column** Each model must contain one numeric or text column that uniquely identifies each record.</span></span> <span data-ttu-id="eb600-128">Les clés composées ne sont pas autorisées.</span><span class="sxs-lookup"><span data-stu-id="eb600-128">Compound keys are not permitted.</span></span>

-   <span data-ttu-id="eb600-129">**Colonne prédictible** : nécessite au moins une colonne prédictible.</span><span class="sxs-lookup"><span data-stu-id="eb600-129">**A predictable column** Requires at least one predictable column.</span></span> <span data-ttu-id="eb600-130">Vous pouvez inclure dans un modèle plusieurs attributs prédictibles, mais ces attributs doivent être des types de données numériques continues.</span><span class="sxs-lookup"><span data-stu-id="eb600-130">You can include multiple predictable attributes in a model, but the predictable attributes must be continuous numeric data types.</span></span> <span data-ttu-id="eb600-131">Vous ne pouvez pas utiliser un type de données datetime comme attribut prédictible même si le stockage natif pour les données est numérique.</span><span class="sxs-lookup"><span data-stu-id="eb600-131">You cannot use a datetime data type as a predictable attribute even if the native storage for the data is numeric.</span></span>

-   <span data-ttu-id="eb600-132">**Colonnes d’entrée** Les colonnes d’entrée doivent contenir des données numériques continues et recevoir le type de données approprié.</span><span class="sxs-lookup"><span data-stu-id="eb600-132">**Input columns** Input columns must contain continuous numeric data and be assigned the appropriate data type.</span></span>

 <span data-ttu-id="eb600-133">Pour plus d’informations, consultez la section Configuration requise de [Références techniques relatives à l’algorithme MLR (Microsoft Linear Regression)](microsoft-linear-regression-algorithm-technical-reference.md).</span><span class="sxs-lookup"><span data-stu-id="eb600-133">For more information, see the Requirements section of [Microsoft Linear Regression Algorithm Technical Reference](microsoft-linear-regression-algorithm-technical-reference.md).</span></span>

## <a name="viewing-a-linear-regression-model"></a><span data-ttu-id="eb600-134">Affichage d'un modèle de régression linéaire</span><span class="sxs-lookup"><span data-stu-id="eb600-134">Viewing a Linear Regression Model</span></span>
 <span data-ttu-id="eb600-135">Pour explorer le modèle, utilisez la **visionneuse d’arborescences Microsoft**.</span><span class="sxs-lookup"><span data-stu-id="eb600-135">To explore the model, you use the **Microsoft Tree Viewer**.</span></span> <span data-ttu-id="eb600-136">L'arborescence d'un modèle de régression linéaire est très simple, toutes les informations relatives à l'équation de régression sont contenues dans un nœud unique.</span><span class="sxs-lookup"><span data-stu-id="eb600-136">The tree structure for a linear regression model is very simple, with all the information about the regression equation contained in a single node.</span></span> <span data-ttu-id="eb600-137">Pour plus d’informations, consultez [Explorer un modèle à l’aide de la visionneuse d’arborescences Microsoft](browse-a-model-using-the-microsoft-tree-viewer.md).</span><span class="sxs-lookup"><span data-stu-id="eb600-137">For more information, see [Browse a Model Using the Microsoft Tree Viewer](browse-a-model-using-the-microsoft-tree-viewer.md).</span></span>

 <span data-ttu-id="eb600-138">Si vous voulez en savoir plus sur l’équation, vous pouvez également afficher les coefficients et autres informations à l’aide de la [visionneuse de l’arborescence de contenu générique Microsoft](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md).</span><span class="sxs-lookup"><span data-stu-id="eb600-138">If you want to know more detail about the equation, you can also view the coefficients and other details by using the [Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md).</span></span>

 <span data-ttu-id="eb600-139">Pour un modèle de régression linéaire, le contenu du modèle inclut des métadonnées, la formule de régression et les statistiques relatives à la distribution de valeurs d'entrée.</span><span class="sxs-lookup"><span data-stu-id="eb600-139">For a linear regression model, the model content includes metadata, the regression formula, and statistics about the distribution of input values.</span></span> <span data-ttu-id="eb600-140">Pour plus d’informations, consultez [Contenu du modèle d’exploration de données pour les modèles de régression linéaire &#40;Analysis Services - Exploration de données&#41;](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md).</span><span class="sxs-lookup"><span data-stu-id="eb600-140">For more information, see [Mining Model Content for Linear Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md).</span></span>

## <a name="creating-predictions"></a><span data-ttu-id="eb600-141">Création de prédictions</span><span class="sxs-lookup"><span data-stu-id="eb600-141">Creating Predictions</span></span>
 <span data-ttu-id="eb600-142">Une fois le modèle traité, les résultats sont stockés sous la forme d'un jeu de statistiques avec le formulaire de régression linéaire que vous pouvez utiliser pour élaborer des prédictions.</span><span class="sxs-lookup"><span data-stu-id="eb600-142">After the model has been processed, the results are stored as a set of statistics together with the linear regression formula, which you can use to compute future trends.</span></span> <span data-ttu-id="eb600-143">Pour obtenir des exemples de requêtes à utiliser avec un modèle de régression linéaire, consultez [Exemples de requête de modèle de régression linéaire](linear-regression-model-query-examples.md).</span><span class="sxs-lookup"><span data-stu-id="eb600-143">For examples of queries to use with a linear regression model, see [Linear Regression Model Query Examples](linear-regression-model-query-examples.md).</span></span>

 <span data-ttu-id="eb600-144">Pour obtenir des informations générales sur la création de requêtes sur des modèles d’exploration de données, consultez [Requêtes d’exploration de données](data-mining-queries.md).</span><span class="sxs-lookup"><span data-stu-id="eb600-144">For general information about how to create queries against mining models, see [Data Mining Queries](data-mining-queries.md).</span></span>

 <span data-ttu-id="eb600-145">En plus de créer un modèle de régression linéaire en sélectionnant l’algorithme MLR ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression), si l’attribut prédictible est un type de données numérique continu, vous pouvez créer un modèle d’arbre de décision qui contient des régressions.</span><span class="sxs-lookup"><span data-stu-id="eb600-145">In addition to creating a linear regression model by selecting the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression algorithm, if the predictable attribute is a continuous numeric data type, you can create a decision tree model that contains regressions.</span></span> <span data-ttu-id="eb600-146">Dans ce cas, l'algorithme fractionne les données lorsqu'il recherche des points de séparation appropriés, mais pour certaines régions de données, il crée à la place une formule de régression.</span><span class="sxs-lookup"><span data-stu-id="eb600-146">In this case, the algorithm will split the data when it finds appropriate separation points, but for some regions of data, will create a regression formula instead.</span></span> <span data-ttu-id="eb600-147">Pour plus d’informations sur les arbres de régression dans un modèle d’arbres de décision, consultez [Contenu du modèle d’exploration de données pour les modèles d’arbre de décision &#40;Analysis Services – Exploration de données&#41;](mining-model-content-for-decision-tree-models-analysis-services-data-mining.md).</span><span class="sxs-lookup"><span data-stu-id="eb600-147">For more information about regression trees within a decision trees model, see [Mining Model Content for Decision Tree Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-decision-tree-models-analysis-services-data-mining.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="eb600-148">Notes</span><span class="sxs-lookup"><span data-stu-id="eb600-148">Remarks</span></span>

-   <span data-ttu-id="eb600-149">Ne prend pas en charge l’utilisation du langage PMML (Predictive Model Markup Language) pour créer des modèles d’exploration de données.</span><span class="sxs-lookup"><span data-stu-id="eb600-149">Does not support the use of Predictive Model Markup Language (PMML) to create mining models.</span></span>

-   <span data-ttu-id="eb600-150">Ne prend pas en charge la création de dimensions d’exploration de données.</span><span class="sxs-lookup"><span data-stu-id="eb600-150">Does not support the creation of data mining dimensions.</span></span>

-   <span data-ttu-id="eb600-151">Prend en charge l’extraction.</span><span class="sxs-lookup"><span data-stu-id="eb600-151">Supports drillthrough.</span></span>

-   <span data-ttu-id="eb600-152">Prend en charge l'utilisation de modèles d'exploration de données OLAP.</span><span class="sxs-lookup"><span data-stu-id="eb600-152">Supports the use of OLAP mining models.</span></span>

## <a name="see-also"></a><span data-ttu-id="eb600-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb600-153">See Also</span></span>
 <span data-ttu-id="eb600-154">[Algorithmes d’exploration de données &#40;Analysis Services d’exploration de données&#41;](data-mining-algorithms-analysis-services-data-mining.md) de [référence technique de l’algorithme](microsoft-linear-regression-algorithm-technical-reference.md) de régression linéaire Microsoft de régression [linéaire exemples de requêtes](linear-regression-model-query-examples.md) [de modèle d’exploration de données pour les modèles de régression linéaire &#40;Analysis Services-exploration de données&#41;](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="eb600-154">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md) [Microsoft Linear Regression Algorithm Technical Reference](microsoft-linear-regression-algorithm-technical-reference.md) [Linear Regression Model Query Examples](linear-regression-model-query-examples.md) [Mining Model Content for Linear Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)</span></span>

