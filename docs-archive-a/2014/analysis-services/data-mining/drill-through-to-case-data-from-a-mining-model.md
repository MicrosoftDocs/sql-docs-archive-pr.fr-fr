---
title: Extraction des données de cas à partir d’un modèle d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- drillthrough [Analysis Services]
ms.assetid: b4d3f350-e543-4ea9-b3a2-b4f7c0a9ae27
author: minewiskan
ms.author: owend
ms.openlocfilehash: 74129c44fc92984a767a79c579a495084ae68754
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613216"
---
# <a name="drill-through-to-case-data-from-a-mining-model"></a><span data-ttu-id="052d1-102">Extraire des données de cas à partir d'un modèle d'exploration de données</span><span class="sxs-lookup"><span data-stu-id="052d1-102">Drill Through to Case Data from a Mining Model</span></span>
  <span data-ttu-id="052d1-103">Si un modèle d'exploration de données a été configuré pour vous autoriser à extraire des cas de modèles, lorsque vous parcourez le modèle, vous pouvez extraire des informations détaillées à propos des cas utilisés pour créer le modèle.</span><span class="sxs-lookup"><span data-stu-id="052d1-103">If a mining model has been configured to let you drill through to model cases, when you browse the model, you can retrieve detailed information about the cases that were used to create the model.</span></span> <span data-ttu-id="052d1-104">De plus, si la structure d'exploration de données sous-jacente a été configurée pour autoriser l'extraction de cas de structure et que vous avez les autorisations appropriées, vous pouvez retourner des informations à partir de la structure d'exploration de données.</span><span class="sxs-lookup"><span data-stu-id="052d1-104">Moreover, if the underlying mining structure has been configured to allow drillthrough to structure cases, and you have the appropriate permissions, you can return information from the mining structure.</span></span> <span data-ttu-id="052d1-105">Cela peut inclure des colonnes qui n'ont pas été incluses dans le modèle d'exploration de données.</span><span class="sxs-lookup"><span data-stu-id="052d1-105">This can include columns that were not included in the mining model.</span></span>  
  
 <span data-ttu-id="052d1-106">Si la structure d'exploration de données ne vous autorise pas à extraire les données sous-jacentes, mais que le modèle d'exploration de données vous y autorise, vous pouvez afficher des informations des cas de modèle, mais pas de la structure d'exploration de données.</span><span class="sxs-lookup"><span data-stu-id="052d1-106">If the mining structure does not allow you to drill through to the underlying data, but the mining model does, you can view information from the model cases, but not from the mining structure.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="052d1-107">Vous pouvez ajouter la possibilité d'extraire un modèle d'exploration de données existant en affectant la valeur `AllowDrillthrough` à la propriété `True`.</span><span class="sxs-lookup"><span data-stu-id="052d1-107">You can add the ability to drillthrough on an existing mining model by setting the property `AllowDrillthrough` to `True`.</span></span> <span data-ttu-id="052d1-108">Toutefois, après l'activation de l'extraction, le modèle doit être recyclé pour que vous puissiez afficher les données de cas.</span><span class="sxs-lookup"><span data-stu-id="052d1-108">However, after you enable drillthrough, the model must be reprocessed before you can see the case data.</span></span> <span data-ttu-id="052d1-109">Pour plus d’informations, consultez [Activer l’extraction pour un modèle d’exploration de données](enable-drillthrough-for-a-mining-model.md).</span><span class="sxs-lookup"><span data-stu-id="052d1-109">For more information, see [Enable Drillthrough for a Mining Model](enable-drillthrough-for-a-mining-model.md).</span></span>  
  
 <span data-ttu-id="052d1-110">Selon le type de visionneuse que vous utilisez, vous pouvez sélectionner le nœud pour effectuer une extraction des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="052d1-110">Depending on the type of viewer you are using, you can select the node for drillthrough in the following ways:</span></span>  
  
|<span data-ttu-id="052d1-111">Nom de la visionneuse</span><span class="sxs-lookup"><span data-stu-id="052d1-111">Viewer name</span></span>|<span data-ttu-id="052d1-112">Nom du volet ou de l'onglet</span><span class="sxs-lookup"><span data-stu-id="052d1-112">Pane or tab name</span></span>|<span data-ttu-id="052d1-113">Sélection du nœud</span><span class="sxs-lookup"><span data-stu-id="052d1-113">Select node</span></span>|  
|-----------------|----------------------|-----------------|  
|<span data-ttu-id="052d1-114">**visionneuse d'arbres Microsoft**</span><span class="sxs-lookup"><span data-stu-id="052d1-114">**Microsoft Tree Viewer**</span></span>|<span data-ttu-id="052d1-115">Onglet **arbre de décision**</span><span class="sxs-lookup"><span data-stu-id="052d1-115">**Decision Tree** tab</span></span>|<span data-ttu-id="052d1-116">Cliquez sur un nœud d'arborescence.</span><span class="sxs-lookup"><span data-stu-id="052d1-116">Click a tree node.</span></span><br /><br /> <span data-ttu-id="052d1-117">**Remarque** Évitez d’utiliser l’extraction sur le `All` nœud, car le renvoi des résultats peut prendre beaucoup de temps.</span><span class="sxs-lookup"><span data-stu-id="052d1-117">**Note** Avoid using drillthrough on the `All` node, because it may take a very long time to return results.</span></span>|  
|<span data-ttu-id="052d1-118">**Microsoft Cluster Viewer**</span><span class="sxs-lookup"><span data-stu-id="052d1-118">**Microsoft Cluster Viewer**</span></span>|<span data-ttu-id="052d1-119">**Diagramme de cluster**</span><span class="sxs-lookup"><span data-stu-id="052d1-119">**Cluster Diagram**</span></span>|<span data-ttu-id="052d1-120">Cliquez sur un nœud de cluster.</span><span class="sxs-lookup"><span data-stu-id="052d1-120">Click a cluster node.</span></span>|  
|<span data-ttu-id="052d1-121">**Microsoft Cluster Viewer**</span><span class="sxs-lookup"><span data-stu-id="052d1-121">**Microsoft Cluster Viewer**</span></span>|<span data-ttu-id="052d1-122">**Profils du cluster**</span><span class="sxs-lookup"><span data-stu-id="052d1-122">**Cluster Profiles**</span></span>|<span data-ttu-id="052d1-123">Cliquez n'importe où dans la colonne de cluster.</span><span class="sxs-lookup"><span data-stu-id="052d1-123">Click anywhere in cluster column.</span></span>|  
|<span data-ttu-id="052d1-124">**Visionneuse d'associations Microsoft**</span><span class="sxs-lookup"><span data-stu-id="052d1-124">**Microsoft Association Viewer**</span></span>|<span data-ttu-id="052d1-125">Onglet **règles**</span><span class="sxs-lookup"><span data-stu-id="052d1-125">**Rules** tab</span></span>|<span data-ttu-id="052d1-126">Cliquez sur une ligne qui contient un ensemble de règles.</span><span class="sxs-lookup"><span data-stu-id="052d1-126">Click a row that contains a set of rules.</span></span>|  
|<span data-ttu-id="052d1-127">**Visionneuse d'associations Microsoft**</span><span class="sxs-lookup"><span data-stu-id="052d1-127">**Microsoft Association Viewer**</span></span>|<span data-ttu-id="052d1-128">Onglet **jeux d’éléments**</span><span class="sxs-lookup"><span data-stu-id="052d1-128">**Itemsets** tab</span></span>|<span data-ttu-id="052d1-129">Cliquez sur une ligne qui contient un jeu d'éléments.</span><span class="sxs-lookup"><span data-stu-id="052d1-129">Click a row that contains an itemset.</span></span>|  
|<span data-ttu-id="052d1-130">**Visionneuse de l'algorithme MSC (Microsoft Sequence Clustering)**</span><span class="sxs-lookup"><span data-stu-id="052d1-130">**Microsoft Sequence Clustering Viewer**</span></span>|<span data-ttu-id="052d1-131">Onglet **règles**</span><span class="sxs-lookup"><span data-stu-id="052d1-131">**Rules** tab</span></span>|<span data-ttu-id="052d1-132">Cliquez sur une ligne qui contient un ensemble de règles.</span><span class="sxs-lookup"><span data-stu-id="052d1-132">Click a row that contains a set of rules.</span></span>|  
|<span data-ttu-id="052d1-133">**Visionneuse de l'algorithme MSC (Microsoft Sequence Clustering)**</span><span class="sxs-lookup"><span data-stu-id="052d1-133">**Microsoft Sequence Clustering Viewer**</span></span>|<span data-ttu-id="052d1-134">Onglet **jeux d’éléments**</span><span class="sxs-lookup"><span data-stu-id="052d1-134">**Itemsets** tab</span></span>|<span data-ttu-id="052d1-135">Cliquez sur une ligne qui contient un jeu d'éléments.</span><span class="sxs-lookup"><span data-stu-id="052d1-135">Click a row that contains an itemset.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="052d1-136">Certains modèles ne peuvent pas utiliser la fonctionnalité d'extraction.</span><span class="sxs-lookup"><span data-stu-id="052d1-136">Some models cannot use drillthrough.</span></span> <span data-ttu-id="052d1-137">La capacité à utiliser la fonctionnalité d'extraction dépend de l'algorithme qui a été utilisé pour créer le modèle.</span><span class="sxs-lookup"><span data-stu-id="052d1-137">The ability to use drillthrough depends on the algorithm that was used to create the model.</span></span> <span data-ttu-id="052d1-138">Pour obtenir une liste des types de modèles d’exploration de données qui prennent en charge l’extraction, consultez [Requêtes d’extraction &#40;exploration de données&#41;](drillthrough-queries-data-mining.md).</span><span class="sxs-lookup"><span data-stu-id="052d1-138">For a list of the mining model types that support drillthrough, see [Drillthrough Queries &#40;Data Mining&#41;](drillthrough-queries-data-mining.md).</span></span>  
  
### <a name="to-view-drillthrough-data-from-a-mining-model"></a><span data-ttu-id="052d1-139">Pour afficher des données d'extraction à partir d'un modèle d'exploration de données</span><span class="sxs-lookup"><span data-stu-id="052d1-139">To view drillthrough data from a mining model</span></span>  
  
1.  <span data-ttu-id="052d1-140">Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez la structure d'exploration de données qui contient le modèle d'exploration de données souhaité.</span><span class="sxs-lookup"><span data-stu-id="052d1-140">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the mining structure that contains the mining model you want.</span></span>  
  
2.  <span data-ttu-id="052d1-141">Dans le Concepteur d'exploration de données, cliquez sur l'onglet **Visionneuse de modèle d'exploration de données** .</span><span class="sxs-lookup"><span data-stu-id="052d1-141">In Data Mining Designer, click the **Mining Model Viewer** tab.</span></span>  
  
3.  <span data-ttu-id="052d1-142">Sélectionnez le modèle dans la liste déroulante **Modèle d’exploration de données** .</span><span class="sxs-lookup"><span data-stu-id="052d1-142">Select the model from the **Mining Model** drop-down list.</span></span>  
  
4.  <span data-ttu-id="052d1-143">Dans la liste déroulante **Visionneuse** , sélectionnez une visionneuse, puis cliquez avec le bouton droit sur le nœud spécifique.</span><span class="sxs-lookup"><span data-stu-id="052d1-143">Select a viewer from the **Viewer** drop-down list, and right-click the specific node.</span></span>  
  
5.  <span data-ttu-id="052d1-144">Sélectionnez **Extraire**, puis sélectionnez **Colonnes de modèle uniquement**ou **Colonnes de structure et de modèle** pour ouvrir la fenêtre **Extraire** .</span><span class="sxs-lookup"><span data-stu-id="052d1-144">Select **Drill Through**, and then select either **Models Columns Only**, or **Model and Structure Columns** to open the **Drill Through** window.</span></span>  
  
6.  <span data-ttu-id="052d1-145">Pour copier les données vers le Presse-papiers, cliquez avec le bouton droit sur une ligne dans la table et sélectionnez **Copier tout**.</span><span class="sxs-lookup"><span data-stu-id="052d1-145">To copy the data to the Clipboard, right-click any row in the table, and select **Copy All**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="052d1-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="052d1-146">See Also</span></span>  
 [<span data-ttu-id="052d1-147">Requêtes d’extraction &#40;exploration de données&#41;</span><span class="sxs-lookup"><span data-stu-id="052d1-147">Drillthrough Queries &#40;Data Mining&#41;</span></span>](drillthrough-queries-data-mining.md)  
  
  