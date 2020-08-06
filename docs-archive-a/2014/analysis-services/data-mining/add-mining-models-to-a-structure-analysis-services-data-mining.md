---
title: Ajouter des modèles d’exploration de données à une structure (Analysis Services-exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], creating
- mining models [Analysis Services], creating
- mining models [Analysis Services], modifying
ms.assetid: a175daa5-58ea-474c-a82f-9648c5155dc8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2cc504016ac378a66795e7522365bd570cfca84d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601790"
---
# <a name="add-mining-models-to-a-structure-analysis-services---data-mining"></a><span data-ttu-id="6b304-102">Ajouter des modèles d'exploration de données à une structure (Analysis Services - Exploration de données)</span><span class="sxs-lookup"><span data-stu-id="6b304-102">Add Mining Models to a Structure (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="6b304-103">Une structure d'exploration de données est destinée à prendre en charge plusieurs modèles d'exploration de données.</span><span class="sxs-lookup"><span data-stu-id="6b304-103">A mining structure is intended to support multiple mining models.</span></span> <span data-ttu-id="6b304-104">Par conséquent, une fois l'exécution de l'Assistant terminée, vous pouvez ouvrir la structure et ajouter de nouveaux modèles d'exploration de données.</span><span class="sxs-lookup"><span data-stu-id="6b304-104">Therefore, after you finish the wizard, you can open the structure and add new mining models.</span></span> <span data-ttu-id="6b304-105">Chaque fois que vous créez un modèle, vous pouvez utiliser un algorithme différent, modifier les paramètres, ou appliquer des filtres pour utiliser un autre sous-ensemble des données.</span><span class="sxs-lookup"><span data-stu-id="6b304-105">Each time that you create a model, you can use a different algorithm, change the parameters, or apply filters to use a different subset of the data.</span></span>  
  
## <a name="adding-new-mining-models"></a><span data-ttu-id="6b304-106">Ajout de nouveaux modèles d'exploration de données</span><span class="sxs-lookup"><span data-stu-id="6b304-106">Adding New Mining Models</span></span>  
 <span data-ttu-id="6b304-107">Lorsque vous utilisez l'Assistant Exploration de données pour créer un nouveau modèle d'exploration de données, par défaut, vous devez toujours d'abord créer une structure d'exploration de données.</span><span class="sxs-lookup"><span data-stu-id="6b304-107">When you use the Data Mining Wizard to create a new mining model, by default you must always create a mining structure first.</span></span> <span data-ttu-id="6b304-108">L'Assistant vous donne ensuite la possibilité d'ajouter un modèle d'exploration de données initial à la structure.</span><span class="sxs-lookup"><span data-stu-id="6b304-108">The wizard then gives you the option to add an initial mining model to the structure.</span></span> <span data-ttu-id="6b304-109">Toutefois, vous n'êtes pas obligé de créer un modèle immédiatement après.</span><span class="sxs-lookup"><span data-stu-id="6b304-109">However, you don't need to create a model right away.</span></span> <span data-ttu-id="6b304-110">Si vous créez uniquement la structure, vous n'avez pas besoin de prendre de décision concernant la colonne à utiliser comme attribut prédictible ou la façon d'utiliser les données dans un modèle particulier.</span><span class="sxs-lookup"><span data-stu-id="6b304-110">If you create the structure only, you do not need to make a decision about which column to use as the predictable attribute, or how to use the data in a particular model.</span></span> <span data-ttu-id="6b304-111">Il vous suffit de définir la structure de données générale que vous souhaitez utiliser ultérieurement. Par la suite, vous pouvez utiliser le [Concepteur d’exploration de données](data-mining-designer.md) pour ajouter de nouveaux modèles d’exploration de données basés sur la structure.</span><span class="sxs-lookup"><span data-stu-id="6b304-111">Instead, you just set up the general data structure that you want to use in future, and later you can use [Data Mining Designer](data-mining-designer.md) to add new mining models that are based on the structure.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6b304-112">Dans DMX, l'instruction CREATE MINING MODEL commence par le modèle d'exploration de données.</span><span class="sxs-lookup"><span data-stu-id="6b304-112">In DMX, the CREATE MINING MODEL statement  begins with the mining model.</span></span> <span data-ttu-id="6b304-113">Autrement dit, vous définissez votre choix de modèle d'exploration de données, et [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] génère automatiquement la structure sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="6b304-113">That is, you define your choice of mining model, and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] automatically generates the underlying structure.</span></span> <span data-ttu-id="6b304-114">Par la suite, vous pouvez continuer à ajouter de nouveaux modèles d’exploration de données à cette structure à l’aide de l’instruction ALTER STRUCTURE... Ajoutez l’instruction MODEL.</span><span class="sxs-lookup"><span data-stu-id="6b304-114">Later you can continue to add new mining models to that structure, by using the ALTER STRUCTURE... ADD MODEL statement.</span></span>  
  
## <a name="choosing-an-algorithm"></a><span data-ttu-id="6b304-115">Choix d'un algorithme</span><span class="sxs-lookup"><span data-stu-id="6b304-115">Choosing an Algorithm</span></span>  
 <span data-ttu-id="6b304-116">Lorsque vous ajoutez un nouveau modèle à une structure existante, la première chose à faire est de sélectionner un algorithme d'exploration de données à utiliser dans ce modèle.</span><span class="sxs-lookup"><span data-stu-id="6b304-116">When you add a new model to an existing structure, the first thing you should do is select a data mining algorithm to use in that model.</span></span> <span data-ttu-id="6b304-117">Le choix de l'algorithme est important car chaque algorithme effectue un type d'analyse différent et a des exigences différentes.</span><span class="sxs-lookup"><span data-stu-id="6b304-117">Choosing the algorithm is important because each algorithm performs a different type of analysis and has different requirements.</span></span>  
  
 <span data-ttu-id="6b304-118">Lorsque vous sélectionnez un algorithme qui est incompatible avec vos données, un avertissement s'affiche.</span><span class="sxs-lookup"><span data-stu-id="6b304-118">When you select an algorithm that is incompatible with your data, you will get a warning.</span></span> <span data-ttu-id="6b304-119">Dans certains cas, vous devrez peut-être ignorer les colonnes qui ne peuvent pas être traitées par l'algorithme.</span><span class="sxs-lookup"><span data-stu-id="6b304-119">In some cases, you might need to ignore columns that cannot be processed by the algorithm.</span></span> <span data-ttu-id="6b304-120">Dans d'autres cas, l'algorithme effectuera automatiquement les ajustements.</span><span class="sxs-lookup"><span data-stu-id="6b304-120">In other cases, the algorithm will automatically make the adjustments for you.</span></span> <span data-ttu-id="6b304-121">Par exemple, si votre structure contient des données numériques et que l'algorithme ne peut fonctionner qu'avec des valeurs discrètes, il regroupera automatiquement les valeurs numériques dans des plages discrètes.</span><span class="sxs-lookup"><span data-stu-id="6b304-121">For example, if your structure contains numeric data, and the algorithm can only work with discrete values, it will group the numeric values into discrete ranges for you.</span></span> <span data-ttu-id="6b304-122">Dans certains cas, vous devrez peut-être d'abord corriger les données manuellement, en choisissant une clé ou un attribut prédictible.</span><span class="sxs-lookup"><span data-stu-id="6b304-122">In some cases, you might need to manually fix the data first, by choosing a key or choosing a predictable attribute.</span></span>  
  
 <span data-ttu-id="6b304-123">Il n'est pas nécessaire de modifier l'algorithme lorsque vous créez un modèle.</span><span class="sxs-lookup"><span data-stu-id="6b304-123">You do not need to change the algorithm when you create a new model.</span></span> <span data-ttu-id="6b304-124">Bien souvent, vous pouvez obtenir des résultats très différents en utilisant le même algorithme, mais en filtrant les données, ou en modifiant un paramètre tel que la méthode de clustering ou la taille minimale du jeu d'éléments.</span><span class="sxs-lookup"><span data-stu-id="6b304-124">Often you can get very different results by using the same algorithm, but filtering the data, or changing a parameter such as the clustering method or the minimum itemset size.</span></span> <span data-ttu-id="6b304-125">Nous vous recommandons de faire des essais avec plusieurs modèles afin de voir quels paramètres produisent les meilleurs résultats.</span><span class="sxs-lookup"><span data-stu-id="6b304-125">We recommend that you experiment with multiple models to see which parameters produce the best results.</span></span>  
  
 <span data-ttu-id="6b304-126">Notez que tous les nouveaux modèles doivent être traités avant de pouvoir être utilisés.</span><span class="sxs-lookup"><span data-stu-id="6b304-126">Note that all new models need to be processed before you can use them.</span></span>  
  
## <a name="specifying-the-usage-of-columns-in-a-new-mining-model"></a><span data-ttu-id="6b304-127">Spécification de l'utilisation de colonnes dans un modèle d'exploration de données</span><span class="sxs-lookup"><span data-stu-id="6b304-127">Specifying the Usage of Columns in a New Mining Model</span></span>  
 <span data-ttu-id="6b304-128">Lorsque vous ajoutez de nouveaux modèles d'exploration de données à une structure d'exploration de données existante, vous devez spécifier la façon dont chaque colonne de données doit être utilisée par le modèle.</span><span class="sxs-lookup"><span data-stu-id="6b304-128">When you add new mining models to an existing mining structure, you must specify how each column of data should be used by the model.</span></span> <span data-ttu-id="6b304-129">Suivant le type d'algorithme que vous choisissez pour le modèle, certains de ces choix peut être effectués par défaut.</span><span class="sxs-lookup"><span data-stu-id="6b304-129">Depending on the type of algorithm you choose for the model, some of these choices may be made by default.</span></span> <span data-ttu-id="6b304-130">Si vous ne spécifiez pas de type d'utilisation pour une colonne, celle-ci ne sera pas incluse dans la structure d'exploration de données.</span><span class="sxs-lookup"><span data-stu-id="6b304-130">If you do not specify a usage type for a column, the column will not be included in the mining structure.</span></span> <span data-ttu-id="6b304-131">Toutefois, les données de la colonne peuvent encore être disponibles pour l'extraction, si le modèle prend en charge cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="6b304-131">However, the data in the column can still be available for drillthrough, if the model supports it.</span></span>  
  
 <span data-ttu-id="6b304-132">Les colonnes de la structure d'exploration de données qui sont utilisées par le modèle (si la valeur Ignorer ne leur a pas été affectée) doivent être une clé, une colonne d'entrée, une colonne prédictible, ou une colonne prédictible dont les valeurs sont également utilisées en tant qu'entrées pour le modèle.</span><span class="sxs-lookup"><span data-stu-id="6b304-132">Columns from the mining structure that are used by the model (if not set to Ignore) must be a key, an input column, a predictable column, or a predictable column the values of which are also used as inputs to the model.</span></span>  
  
-   <span data-ttu-id="6b304-133">Les colonnes clés contiennent un identificateur unique pour chaque ligne d'une table.</span><span class="sxs-lookup"><span data-stu-id="6b304-133">Key columns contain a unique identifier for each row in a table.</span></span> <span data-ttu-id="6b304-134">Certains modèles d'exploration de données, tels que ceux basés sur les algorithmes MSC (Microsoft Sequence Clustering) ou MTS (Microsoft Time Series), peuvent contenir plusieurs colonnes clés.</span><span class="sxs-lookup"><span data-stu-id="6b304-134">Some mining models, such as those based on the sequence clustering or time series algorithms, can contain multiple key columns.</span></span> <span data-ttu-id="6b304-135">Toutefois, ces multiples clés ne sont pas des clés composées au sens relationnel ; elles doivent être sélectionnées pour prendre en charge l'analyse de séries chronologiques et Sequence Clustering.</span><span class="sxs-lookup"><span data-stu-id="6b304-135">However, these multiple keys are not compound keys in the relational sense, but instead must be selected so as to provide support for time series and sequence clustering analysis.</span></span>  
  
-   <span data-ttu-id="6b304-136">Les colonnes d'entrée fournissent les informations à partir desquelles les prédictions sont effectuées.</span><span class="sxs-lookup"><span data-stu-id="6b304-136">Input columns provide the information from which predictions are made.</span></span> <span data-ttu-id="6b304-137">L’Assistant Exploration de données fournit la fonctionnalité **Suggérer** , qui est activée quand vous sélectionnez une colonne prédictible.</span><span class="sxs-lookup"><span data-stu-id="6b304-137">The Data Mining Wizard provides the **Suggest** feature, which is enabled when you select a predictable column.</span></span> <span data-ttu-id="6b304-138">Si vous cliquez sur ce bouton, l'Assistant échantillonne les valeurs prédictibles et détermine les autres colonnes de la structure qui constituent de bonnes variables.</span><span class="sxs-lookup"><span data-stu-id="6b304-138">If you click this button, the wizard will sample the predictable values and determine which of the other columns in the structure make good variables.</span></span> <span data-ttu-id="6b304-139">Il rejette les colonnes clés ou les autres colonnes comportant de nombreuses valeurs uniques, et suggère les colonnes qui semblent être en corrélation avec le résultat.</span><span class="sxs-lookup"><span data-stu-id="6b304-139">It will reject key columns or other columns with many unique values, and suggest columns that appear to be correlated with the outcome.</span></span>  
  
     <span data-ttu-id="6b304-140">Cette fonctionnalité est particulièrement pratique lorsque les datasets contiennent plus de colonnes que nécessaire pour générer un modèle d'exploration de données.</span><span class="sxs-lookup"><span data-stu-id="6b304-140">This feature is particularly handy when datasets contain more columns than you really need to build a mining model.</span></span> <span data-ttu-id="6b304-141">La fonctionnalité **Suggérer** calcule un score compris entre 0 et 1, qui décrit la relation entre chaque colonne du jeu de données et la colonne prédictible.</span><span class="sxs-lookup"><span data-stu-id="6b304-141">The **Suggest** feature calculates a numeric score, from 0 to 1, that describes the relationship between each column in the dataset and the predictable column.</span></span> <span data-ttu-id="6b304-142">En fonction de ce score, la fonctionnalité suggère les colonnes à utiliser comme entrée pour le modèle d'exploration de données.</span><span class="sxs-lookup"><span data-stu-id="6b304-142">Based on this score, the feature suggests columns to use as input for the mining model.</span></span> <span data-ttu-id="6b304-143">Si vous utilisez la fonctionnalité **Suggérer** , vous pouvez utiliser les colonnes suggérées, modifier les choix pour les adapter à vos besoins ou ignorer les suggestions.</span><span class="sxs-lookup"><span data-stu-id="6b304-143">If you use the **Suggest** feature, you can use the suggested columns, modify the selections to fit your needs, or ignore the suggestions.</span></span>  
  
-   <span data-ttu-id="6b304-144">Les colonnes prédictibles contiennent les informations que vous tentez de prévoir dans le modèle d'exploration de données.</span><span class="sxs-lookup"><span data-stu-id="6b304-144">Predictable columns contain the information that you try to predict in the mining model.</span></span> <span data-ttu-id="6b304-145">Vous pouvez sélectionner plusieurs colonnes comme attributs prédictibles.</span><span class="sxs-lookup"><span data-stu-id="6b304-145">You can select multiple columns as the predictable attributes.</span></span> <span data-ttu-id="6b304-146">Les modèles de clustering sont l'exception car un attribut prédictible est facultatif.</span><span class="sxs-lookup"><span data-stu-id="6b304-146">Clustering models are the exception in that a predictable attribute is optional.</span></span>  
  
     <span data-ttu-id="6b304-147">Suivant le type de modèle, la colonne prédictible devra peut-être être un type de données spécifique : par exemple, un modèle de régression linéaire requiert une colonne numérique comme valeur prédite ; l'algorithme Naïve Bayes requiert une valeur discrète (et toutes les entrées doivent également être discrètes).</span><span class="sxs-lookup"><span data-stu-id="6b304-147">Depending on the model type, the predictable column might need to be a specific data type: for example, a linear regression model requires a numeric column as the predicted value; Naïve Bayes algorithm requires a discrete value (and all the inputs must be discrete as well).</span></span>  
  
## <a name="specifying-column-content"></a><span data-ttu-id="6b304-148">Spécification du contenu des colonnes</span><span class="sxs-lookup"><span data-stu-id="6b304-148">Specifying Column Content</span></span>  
 <span data-ttu-id="6b304-149">Pour certaines colonnes, vous devrez peut-être spécifier le *contenu de colonne*.</span><span class="sxs-lookup"><span data-stu-id="6b304-149">For some columns, you might also need to specify the *column content*.</span></span> <span data-ttu-id="6b304-150">Dans l'exploration de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , la propriété Type de contenu de chaque colonne de données indique à l'algorithme comment il doit traiter les données dans cette colonne.</span><span class="sxs-lookup"><span data-stu-id="6b304-150">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data mining, the Content Type property of each data columns tells the algorithm how it should process the data in that column.</span></span> <span data-ttu-id="6b304-151">Par exemple, si vos données ont une colonne Income, vous devez spécifier que la colonne contient des nombres continus en définissant Continu comme type de contenu.</span><span class="sxs-lookup"><span data-stu-id="6b304-151">For example, if your data has an Income column, you must specify that the column contains continuous numbers by setting the content type to Continuous.</span></span> <span data-ttu-id="6b304-152">Vous pouvez aussi spécifier que les nombres dans la colonne Revenu doivent être regroupés dans des compartiments en attribuant au contenu le type Discrétisé et en indiquant éventuellement le nombre exact de compartiments.</span><span class="sxs-lookup"><span data-stu-id="6b304-152">However, you could also specify that the numbers in the Income column be grouped into buckets by setting the content type to Discretized and optionally specifying the exact number of buckets.</span></span> <span data-ttu-id="6b304-153">Vous pouvez créer des modèles distincts qui gèrent les colonnes différemment : par exemple, vous pouvez faire des essais avec un modèle qui répartit les clients en trois groupes d'âge et un autre modèle qui répartit les clients en dix groupes d'âge.</span><span class="sxs-lookup"><span data-stu-id="6b304-153">You can create different models that handle columns differently: for example, you might try one model that buckets customers into three age groups, and another model that buckets customers into 10 age groups.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b304-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b304-154">See Also</span></span>  
 <span data-ttu-id="6b304-155">[Structures d’exploration de données &#40;Analysis Services d’exploration de données&#41;](mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="6b304-155">[Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="6b304-156">[Créer une structure d’exploration de données relationnelle](create-a-relational-mining-structure.md) </span><span class="sxs-lookup"><span data-stu-id="6b304-156">[Create a Relational Mining Structure](create-a-relational-mining-structure.md) </span></span>  
 <span data-ttu-id="6b304-157">[Propriétés du modèle d’exploration de données](mining-model-properties.md) </span><span class="sxs-lookup"><span data-stu-id="6b304-157">[Mining Model Properties](mining-model-properties.md) </span></span>  
 [<span data-ttu-id="6b304-158">Colonnes d'un modèle d'exploration de données</span><span class="sxs-lookup"><span data-stu-id="6b304-158">Mining Model Columns</span></span>](mining-model-columns.md)  
  
  