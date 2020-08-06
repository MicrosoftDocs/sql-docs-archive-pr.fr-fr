---
title: Ajouter un total à un groupe ou à une région de données de tableau matriciel (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: cf1b96c3-7f0f-4c94-ad08-5239c77ccfe4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f626621a37a327ae32664ab9444e72ce4931ac0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87600539"
---
# <a name="add-a-total-to-a-group-or-tablix-data-region-report-builder-and-ssrs"></a><span data-ttu-id="88374-102">Ajouter un total à un groupe ou à une région de données de tableau matriciel (Générateur de rapports et SSRS)</span><span class="sxs-lookup"><span data-stu-id="88374-102">Add a Total to a Group or Tablix Data Region (Report Builder and SSRS)</span></span>
  <span data-ttu-id="88374-103">Vous pouvez ajouter des totaux à une région de données de tableau matriciel pour un groupe ou pour la totalité de la région de données.</span><span class="sxs-lookup"><span data-stu-id="88374-103">You can add totals in a tablix data region for a group or for the entire data region.</span></span> <span data-ttu-id="88374-104">Par défaut, un total est la somme des données numériques non Null d'un groupe ou d'une région de données, après application des filtres.</span><span class="sxs-lookup"><span data-stu-id="88374-104">By default, a total is the sum of the numeric, non-null data in a group or in the data region, after filters are applied.</span></span> <span data-ttu-id="88374-105">Pour ajouter des totaux pour un groupe, cliquez sur **Ajouter un total** dans le menu contextuel du groupe dans le volet Regroupement.</span><span class="sxs-lookup"><span data-stu-id="88374-105">To add totals for a group, click **Add Total** on the shortcut menu for the group in the Grouping pane.</span></span> <span data-ttu-id="88374-106">Pour ajouter des totaux pour une cellule individuelle dans la zone du corps du tableau matriciel, cliquez sur **Ajouter un total** dans le menu contextuel de la cellule.</span><span class="sxs-lookup"><span data-stu-id="88374-106">To add totals for an individual cell in the tablix body area, click **Add Total** on the shortcut menu for the cell.</span></span> <span data-ttu-id="88374-107">La commande **Ajouter un total** est contextuelle et active uniquement pour les champs de type numérique.</span><span class="sxs-lookup"><span data-stu-id="88374-107">The **Add Total** command is context-sensitive and enabled only for numeric fields.</span></span> <span data-ttu-id="88374-108">Selon la cellule de tableau matriciel que vous sélectionnez, vous pouvez ajouter un total pour une cellule unique en sélectionnant une cellule dans la zone du corps du tableau matriciel ou pour la totalité du groupe en sélectionnant une cellule dans la zone du groupe de lignes ou la zone du groupe de colonnes du tableau matriciel.</span><span class="sxs-lookup"><span data-stu-id="88374-108">Depending on the tablix cell that you select, you can add a total for a single cell by selecting a cell in the tablix body area or for the entire group by selecting a cell in the tablix row group area or the tablix column group area.</span></span> <span data-ttu-id="88374-109">Pour plus d’informations sur les zones de tableau matriciel, consultez [Région de données de tableau matriciel &#40;Générateur de rapports et SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md).</span><span class="sxs-lookup"><span data-stu-id="88374-109">For more information about tablix areas, see [Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="88374-110">Après avoir ajouté un total, vous pouvez remplacer la fonction par défaut Sum par une autre fonction d’agrégation de la liste des fonctions de rapport intégrées.</span><span class="sxs-lookup"><span data-stu-id="88374-110">After you add a total, you can change the default function Sum to a different aggregate function from the list of built-in report functions.</span></span> <span data-ttu-id="88374-111">Pour plus d’informations, consultez informations de [référence sur les fonctions d’agrégation &#40;générateur de rapports et&#41;SSRS ](report-builder-functions-aggregate-functions-reference.md).[!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88374-111">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).[!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]</span></span>  
  
### <a name="to-add-a-total-for-an-individual-value-in-the-tablix-body-area"></a><span data-ttu-id="88374-112">Pour ajouter un total pour une valeur individuelle dans la zone du corps du tableau matriciel</span><span class="sxs-lookup"><span data-stu-id="88374-112">To add a total for an individual value in the tablix body area</span></span>  
  
-   <span data-ttu-id="88374-113">Dans la zone du corps de la région de données du tableau matriciel, cliquez avec le bouton droit dans la cellule où vous souhaitez ajouter le total.</span><span class="sxs-lookup"><span data-stu-id="88374-113">In the tablix data region body area, right-click the cell where you want to add the total.</span></span> <span data-ttu-id="88374-114">La cellule doit contenir un champ de type numérique.</span><span class="sxs-lookup"><span data-stu-id="88374-114">The cell must contain a numeric field.</span></span> <span data-ttu-id="88374-115">Pointez sur **Ajouter un total**, puis cliquez sur **Ligne** ou **Colonne**.</span><span class="sxs-lookup"><span data-stu-id="88374-115">Point to **Add Total**, and then click **Row** or **Column**.</span></span>  
  
     <span data-ttu-id="88374-116">Une nouvelle ligne ou colonne à l'extérieur du groupe actuel est ajoutée à la région de données, avec un total par défaut pour le champ dans la cellule où vous avez cliqué.</span><span class="sxs-lookup"><span data-stu-id="88374-116">A new row or column outside the current group is added to the data region, with a default total for the field in the cell you clicked.</span></span>  
  
     <span data-ttu-id="88374-117">Si la région de données de tableau matriciel est une table, une ligne est ajoutée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="88374-117">If the tablix data region is a table, a row is automatically added.</span></span>  
  
### <a name="to-add-totals-for-a-row-group"></a><span data-ttu-id="88374-118">Pour ajouter des totaux pour un groupe de lignes</span><span class="sxs-lookup"><span data-stu-id="88374-118">To add totals for a row group</span></span>  
  
-   <span data-ttu-id="88374-119">Dans la zone de groupe de lignes d’une région de données du tableau matriciel, cliquez avec le bouton droit sur une cellule dans le groupe de lignes pour lequel vous souhaitez ajouter un total, pointez sur **Ajouter un total**, puis cliquez sur **Avant** ou **Après**.</span><span class="sxs-lookup"><span data-stu-id="88374-119">In the tablix data region row group area, right-click a cell in the row group area for which you want totals, point to **Add Total**, and then click **Before** or **After**.</span></span>  
  
     <span data-ttu-id="88374-120">Une nouvelle ligne à l'extérieur du groupe actuel est ajoutée à la région de données, et un total par défaut est ajouté pour chaque champ de type numérique dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="88374-120">A new row outside the current group is added to the data region, and then a default total is added for each numeric field in the row.</span></span>  
  
### <a name="to-add-totals-for-a-column-group"></a><span data-ttu-id="88374-121">Pour ajouter des totaux pour un groupe de colonnes</span><span class="sxs-lookup"><span data-stu-id="88374-121">To add totals for a column group</span></span>  
  
-   <span data-ttu-id="88374-122">Dans la zone de groupe de lignes d’une région de données du tableau matriciel, cliquez avec le bouton droit sur une cellule dans le groupe de colonnes pour lequel vous souhaitez ajouter un total, pointez sur **Ajouter un total**, puis cliquez sur **Avant** ou **Après**.</span><span class="sxs-lookup"><span data-stu-id="88374-122">In the tablix data region row group area, right-click a cell in the column group area for which you want totals, then point to **Add Total**, and click **Before** or **After**.</span></span>  
  
     <span data-ttu-id="88374-123">Une nouvelle colonne à l'extérieur du groupe actuel est ajoutée à la région de données, et un total par défaut est ajouté pour chaque champ de type numérique dans la colonne.</span><span class="sxs-lookup"><span data-stu-id="88374-123">A new column outside the current group is added to the data region, and then a default total is added for each numeric field in the column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88374-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88374-124">See Also</span></span>  
 <span data-ttu-id="88374-125">[Étendue des expressions pour les totaux, les agrégats et les collections intégrées &#40;Générateur de rapports et SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md) </span><span class="sxs-lookup"><span data-stu-id="88374-125">[Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md) </span></span>  
 <span data-ttu-id="88374-126">[Région de données de tableau matriciel &#40;Générateur de rapports et SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="88374-126">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="88374-127">[Tables &#40;Générateur de rapports et SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="88374-127">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="88374-128">[Matrices &#40;Générateur de rapports et SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="88374-128">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="88374-129">[Répertorie &#40;Générateur de rapports et SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="88374-129">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="88374-130">Tables, matrices et listes &#40;Générateur de rapports et SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="88374-130">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  