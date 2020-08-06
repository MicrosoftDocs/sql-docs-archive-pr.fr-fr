---
title: Tri interactif (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 00cafed5-1a3c-4ce0-a1fb-ff1e2613f495
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 92f8a63ebd3d16c84dc12bb4a08549efa91e949a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707103"
---
# <a name="interactive-sort-report-builder-and-ssrs"></a><span data-ttu-id="8ad16-102">Tri interactif (Générateur de rapports et SSRS)</span><span class="sxs-lookup"><span data-stu-id="8ad16-102">Interactive Sort (Report Builder and SSRS)</span></span>
  <span data-ttu-id="8ad16-103">Vous pouvez ajouter des boutons de tri interactifs pour permettre à un utilisateur de basculer entre l'ordre croissant et l'ordre décroissant pour les lignes d'une table ou pour les lignes et les colonnes d'une matrice.</span><span class="sxs-lookup"><span data-stu-id="8ad16-103">You can add interactive sort buttons to enable a user to toggle between ascending and descending order for rows in a table or for rows and columns in a matrix.</span></span> <span data-ttu-id="8ad16-104">L'utilisation la plus courante du tri interactif consiste à ajouter un bouton de tri à chaque en-tête de colonne.</span><span class="sxs-lookup"><span data-stu-id="8ad16-104">The most common use of interactive sort is to add a sort button to every column header.</span></span> <span data-ttu-id="8ad16-105">L'utilisateur peut alors choisir la colonne en fonction de laquelle trier le contenu.</span><span class="sxs-lookup"><span data-stu-id="8ad16-105">The user can then choose which column to sort by.</span></span>  
  
 <span data-ttu-id="8ad16-106">Toutefois, vous pouvez ajouter un bouton de tri interactif à n'importe quelle zone de texte, pas seulement les en-têtes de colonne.</span><span class="sxs-lookup"><span data-stu-id="8ad16-106">However, you can add an interactive sort button to any text box, not just column headers.</span></span> <span data-ttu-id="8ad16-107">Par exemple, pour une zone de texte placée à l'extérieur d'un groupe de lignes, vous pouvez préciser un tri pour les lignes ou les colonnes du groupe parent, pour les lignes ou les colonnes du groupe enfant ou pour les lignes ou colonnes de détails.</span><span class="sxs-lookup"><span data-stu-id="8ad16-107">For example, for a text box in a row outside a row group, you can specify a sort for the parent group rows or columns, for child group rows or columns, or for the detail rows or columns.</span></span> <span data-ttu-id="8ad16-108">Vous pouvez également combiner des champs en une expression de groupe unique, puis trier en fonction de plusieurs champs.</span><span class="sxs-lookup"><span data-stu-id="8ad16-108">You can also combine fields into a single group expression, and then sort by multiple fields.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="8ad16-109">Lorsque vous ajoutez un tri interactif, vous devez spécifier les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="8ad16-109">When you add an interactive sort, you must specify the following items:</span></span>  
  
-   <span data-ttu-id="8ad16-110">**Que trier** : lignes ou colonnes ?</span><span class="sxs-lookup"><span data-stu-id="8ad16-110">**What to sort:** Rows or columns?</span></span>  
  
-   <span data-ttu-id="8ad16-111">**Sur quel élément trier** : un champ affiché dans une colonne de la table ?</span><span class="sxs-lookup"><span data-stu-id="8ad16-111">**What to sort by:** A field that is displayed in a table column?</span></span> <span data-ttu-id="8ad16-112">Un champ non affiché ?</span><span class="sxs-lookup"><span data-stu-id="8ad16-112">A field that is not displayed?</span></span>  
  
-   <span data-ttu-id="8ad16-113">**Dans quel contexte trier** : par exemple, vous pouvez trier sur les lignes associées aux groupes de lignes ; sur les colonnes associées aux groupes de colonnes ; sur les lignes de détails ; sur les groupes enfants dans un groupe parent ; ou encore sur le groupe parent et enfant ensemble.</span><span class="sxs-lookup"><span data-stu-id="8ad16-113">**What context to sort in:** For example, you can sort on rows associated with row groups; columns associated with column groups; detail rows; child groups within a parent group; or parent and child group together.</span></span>  
  
-   <span data-ttu-id="8ad16-114">**À quelle zone de texte ajouter le bouton de tri** : dans l’en-tête de colonne ou dans l’en-tête de ligne de groupe ?</span><span class="sxs-lookup"><span data-stu-id="8ad16-114">**Which text box to add the sort button to:** In the column header or in the group row header?</span></span>  
  
-   <span data-ttu-id="8ad16-115">**Faut-il synchroniser le tri pour plusieurs régions de données** : vous pouvez concevoir un rapport afin que lorsque l’utilisateur bascule l’ordre de tri, d’autres régions de données avec le même ancêtre soient également triées.</span><span class="sxs-lookup"><span data-stu-id="8ad16-115">**Whether to synchronize the sort for multiple data regions:** You can design a report so that when the user toggles the sort order, other data regions with the same ancestor also sort.</span></span>  
  
 <span data-ttu-id="8ad16-116">Pour obtenir des instructions détaillées, consultez [Ajouter un tri interactif à un tableau ou une matrice &#40;Générateur de rapports et SSRS&#41;](add-interactive-sort-to-a-table-or-matrix-report-builder-and-ssrs.md).</span><span class="sxs-lookup"><span data-stu-id="8ad16-116">For step-by-step instructions, see [Add Interactive Sort to a Table or Matrix &#40;Report Builder and SSRS&#41;](add-interactive-sort-to-a-table-or-matrix-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="8ad16-117">Le tableau suivant récapitule les effets que vous pouvez obtenir en utilisant des boutons de tri interactifs.</span><span class="sxs-lookup"><span data-stu-id="8ad16-117">The following table summarizes the effects you can achieve by using interactive sort buttons.</span></span>  
  
|<span data-ttu-id="8ad16-118">Action</span><span class="sxs-lookup"><span data-stu-id="8ad16-118">Action</span></span>|<span data-ttu-id="8ad16-119">Que trier</span><span class="sxs-lookup"><span data-stu-id="8ad16-119">What to sort</span></span>|<span data-ttu-id="8ad16-120">Où ajouter le bouton de tri</span><span class="sxs-lookup"><span data-stu-id="8ad16-120">Where to add the sort button</span></span>|<span data-ttu-id="8ad16-121">Sur quel élément trier</span><span class="sxs-lookup"><span data-stu-id="8ad16-121">What to sort on</span></span>|<span data-ttu-id="8ad16-122">Étendue du tri</span><span class="sxs-lookup"><span data-stu-id="8ad16-122">Sort scope</span></span>|  
|------------|------------------|----------------------------------|---------------------|----------------|  
|<span data-ttu-id="8ad16-123">Tri des lignes de détails dans une table sans groupe</span><span class="sxs-lookup"><span data-stu-id="8ad16-123">Sort detail rows for a table with no groups</span></span>|<span data-ttu-id="8ad16-124">Détails</span><span class="sxs-lookup"><span data-stu-id="8ad16-124">Details</span></span>|<span data-ttu-id="8ad16-125">En-tête de colonne</span><span class="sxs-lookup"><span data-stu-id="8ad16-125">Column header</span></span>|<span data-ttu-id="8ad16-126">Champ Dataset lié à cette colonne</span><span class="sxs-lookup"><span data-stu-id="8ad16-126">Dataset field bound to this column</span></span>|<span data-ttu-id="8ad16-127">Région de données</span><span class="sxs-lookup"><span data-stu-id="8ad16-127">Data region</span></span>|  
|<span data-ttu-id="8ad16-128">Tri des instances de groupe de niveau supérieur pour une matrice</span><span class="sxs-lookup"><span data-stu-id="8ad16-128">Sort top-level group instances for a matrix</span></span>|<span data-ttu-id="8ad16-129">Groupes</span><span class="sxs-lookup"><span data-stu-id="8ad16-129">Groups</span></span>|<span data-ttu-id="8ad16-130">En-tête de colonne</span><span class="sxs-lookup"><span data-stu-id="8ad16-130">Column header</span></span>|<span data-ttu-id="8ad16-131">Expression de groupe pour un groupe parent</span><span class="sxs-lookup"><span data-stu-id="8ad16-131">Group expression for parent group</span></span>|<span data-ttu-id="8ad16-132">Région de données</span><span class="sxs-lookup"><span data-stu-id="8ad16-132">Data region</span></span>|  
|<span data-ttu-id="8ad16-133">Tri des lignes de détails pour un groupe enfant dans une table</span><span class="sxs-lookup"><span data-stu-id="8ad16-133">Sort detail rows for a child group in a table</span></span>|<span data-ttu-id="8ad16-134">Détails</span><span class="sxs-lookup"><span data-stu-id="8ad16-134">Details</span></span>|<span data-ttu-id="8ad16-135">Ligne d'en-tête de groupe enfant</span><span class="sxs-lookup"><span data-stu-id="8ad16-135">Child group header row</span></span>|<span data-ttu-id="8ad16-136">Champ Dataset sur lequel trier</span><span class="sxs-lookup"><span data-stu-id="8ad16-136">Dataset field to sort by</span></span>|<span data-ttu-id="8ad16-137">Groupe enfant</span><span class="sxs-lookup"><span data-stu-id="8ad16-137">Child group</span></span>|  
|<span data-ttu-id="8ad16-138">Tri de lignes pour plusieurs groupes de lignes et lignes de détails dans une table</span><span class="sxs-lookup"><span data-stu-id="8ad16-138">Sort rows for multiple row groups and detail rows in a table</span></span>|<span data-ttu-id="8ad16-139">Groupes, mais vous devez redéfinir l'expression de groupe</span><span class="sxs-lookup"><span data-stu-id="8ad16-139">Groups, but you must redefine the group expression</span></span>|<span data-ttu-id="8ad16-140">En-tête de colonne</span><span class="sxs-lookup"><span data-stu-id="8ad16-140">Column header</span></span>|<span data-ttu-id="8ad16-141">Agrégation du champ de dataset sur lequel trier</span><span class="sxs-lookup"><span data-stu-id="8ad16-141">Aggregate of dataset field to sort by</span></span>|<span data-ttu-id="8ad16-142">Région de données</span><span class="sxs-lookup"><span data-stu-id="8ad16-142">Data region</span></span>|  
|<span data-ttu-id="8ad16-143">Synchroniser l’ordre de tri pour plusieurs régions de données</span><span class="sxs-lookup"><span data-stu-id="8ad16-143">Synchronize the sort order for multiple data regions</span></span>|<span data-ttu-id="8ad16-144">Groupes</span><span class="sxs-lookup"><span data-stu-id="8ad16-144">Groups</span></span>|<span data-ttu-id="8ad16-145">En principe, en-tête de la colonne</span><span class="sxs-lookup"><span data-stu-id="8ad16-145">Typically, column header</span></span>|<span data-ttu-id="8ad16-146">Expression de groupe</span><span class="sxs-lookup"><span data-stu-id="8ad16-146">Group expression</span></span>|<span data-ttu-id="8ad16-147">Dataset</span><span class="sxs-lookup"><span data-stu-id="8ad16-147">Dataset</span></span>|  
  
 <span data-ttu-id="8ad16-148">Le processeur de rapport applique le tri interactif après que toutes les expressions de tri des groupes et régions de données ont été appliquées.</span><span class="sxs-lookup"><span data-stu-id="8ad16-148">The report processor applies interactive sort after all data region and group sort expressions are applied.</span></span> <span data-ttu-id="8ad16-149">Pour plus d’informations, consultez [Filtrer, regrouper et trier des données &#40;Générateur de rapports et SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md).</span><span class="sxs-lookup"><span data-stu-id="8ad16-149">For more information, see [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md).</span></span>  
  
## <a name="adding-interactive-sort-for-multiple-groups"></a><span data-ttu-id="8ad16-150">Ajout du tri interactif à plusieurs groupes</span><span class="sxs-lookup"><span data-stu-id="8ad16-150">Adding Interactive Sort for Multiple Groups</span></span>  
 <span data-ttu-id="8ad16-151">Dans une table comportant des groupes de lignes imbriqués basés chacun sur un champ de dataset unique, vous pouvez ajouter un bouton de tri interactif qui trie les valeurs du groupe parent, les valeurs du groupe enfant ou les lignes de détails.</span><span class="sxs-lookup"><span data-stu-id="8ad16-151">In a table with nested row groups each based on a single dataset field, you can add an interactive sort button that sorts parent group values, child group values, or detail rows.</span></span> <span data-ttu-id="8ad16-152">Toutefois, vous pouvez souhaiter permettre à l'utilisateur de trier la table à la fois par les valeurs des groupes parent et enfant sans devoir cliquer plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="8ad16-152">However, you might want to provide the user with the ability to sort the table by both the parent and child group values without having to click multiple times.</span></span>  
  
 <span data-ttu-id="8ad16-153">Pour ce faire, vous devez modifier la conception de la table pour effectuer le groupement sur une expression qui combine plusieurs champs.</span><span class="sxs-lookup"><span data-stu-id="8ad16-153">To do this, you must redesign the table to group on an expression that combines multiple fields.</span></span> <span data-ttu-id="8ad16-154">Par exemple, pour un dataset comprenant des éléments d'inventaire, si la table d'origine est regroupée par taille puis par couleur, vous pouvez spécifier un groupe unique avec une expression de groupe qui est une combinaison de taille et couleur.</span><span class="sxs-lookup"><span data-stu-id="8ad16-154">For example, for a dataset with inventory counts, if the original table grouped by size and then by color, you can specify a single group with a group expression that is a combination of size and color.</span></span> <span data-ttu-id="8ad16-155">Pour plus d’informations, consultez [Ajouter un tri interactif à un tableau ou une matrice &#40;Générateur de rapports et SSRS&#41;](add-interactive-sort-to-a-table-or-matrix-report-builder-and-ssrs.md).</span><span class="sxs-lookup"><span data-stu-id="8ad16-155">For more information, see [Add Interactive Sort to a Table or Matrix &#40;Report Builder and SSRS&#41;](add-interactive-sort-to-a-table-or-matrix-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ad16-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ad16-156">See Also</span></span>  
 <span data-ttu-id="8ad16-157">[Trier des données dans une région de données &#40;Générateur de rapports et SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8ad16-157">[Sort Data in a Data Region &#40;Report Builder and SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="8ad16-158">[Filtrer, regrouper et trier des données &#40;Générateur de rapports et SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8ad16-158">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="8ad16-159">Ajouter un tri interactif à un tableau ou une matrice &#40;Générateur de rapports et SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="8ad16-159">Add Interactive Sort to a Table or Matrix &#40;Report Builder and SSRS&#41;</span></span>](add-interactive-sort-to-a-table-or-matrix-report-builder-and-ssrs.md)  
  
  