---
title: Types de dimension | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- time dimensions [Analysis Services]
- quantitative dimensions [Analysis Services]
- BillOfMaterials dimension [Analysis Services]
- geography dimensions
- utility dimensions [Analysis Services]
- channel dimensions
- dimensions [Analysis Services], types
- products dimensions [Analysis Services]
- account dimensions [Analysis Services]
- organization dimensions
- currency dimensions [Analysis Services]
- rates dimensions
- promotion dimensions
- scenario dimensions [Analysis Services]
- customers dimensions [Analysis Services]
- Type property
ms.assetid: bd3195da-e762-4c98-b643-34c76e842343
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5e0c16a57081aa1d9ed3cc6964d1f17fa7135986
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87614870"
---
# <a name="dimension-types"></a><span data-ttu-id="4b5a1-102">Types de dimensions</span><span class="sxs-lookup"><span data-stu-id="4b5a1-102">Dimension Types</span></span>
  <span data-ttu-id="4b5a1-103">La valeur de la propriété `Type` fournit des informations sur le contenu d'une dimension aux applications serveur et clientes.</span><span class="sxs-lookup"><span data-stu-id="4b5a1-103">The `Type` property setting provides information about the contents of a dimension to server and client applications.</span></span> <span data-ttu-id="4b5a1-104">Dans certains cas, la valeur de `Type` fournit seulement des informations indicatives aux applications clientes et elle est facultative.</span><span class="sxs-lookup"><span data-stu-id="4b5a1-104">In some cases, the `Type` setting only provides guidance for client applications and is optional.</span></span> <span data-ttu-id="4b5a1-105">Dans d'autres cas, comme pour les dimensions `Accounts` ou `Time`, les paramètres de la propriété `Type` pour la dimension et ses attributs déterminent des fonctionnements spécifiques du serveur et peuvent être nécessaires pour implémenter certains fonctionnements du cube.</span><span class="sxs-lookup"><span data-stu-id="4b5a1-105">In other cases, such as `Accounts` or `Time` dimensions, the `Type` property settings for the dimension and its attributes determine specific server-based behaviors and may be required to implement certain behaviors in the cube.</span></span> <span data-ttu-id="4b5a1-106">Par exemple, la propriété `Type` d'une dimension peut être définie à la valeur `Accounts` pour indiquer aux applications clientes que la dimension standard contient des attributs de comptes.</span><span class="sxs-lookup"><span data-stu-id="4b5a1-106">For example, the `Type` property of a dimension can be set to `Accounts` to indicate to client applications that the standard dimension contains account attributes.</span></span> <span data-ttu-id="4b5a1-107">Pour plus d’informations sur les dimensions de temps, de compte et de devise, consultez [créer une dimension de type de date](../multidimensional-models/database-dimensions-create-a-date-type-dimension.md), [créer un compte financier de dimension de type parent-enfant](../multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md)et [créer une dimension de type devise](../multidimensional-models/database-dimensions-create-a-currency-type-dimension.md).</span><span class="sxs-lookup"><span data-stu-id="4b5a1-107">For more information about time, account, and currency dimensions, see [Create a Date type Dimension](../multidimensional-models/database-dimensions-create-a-date-type-dimension.md), [Create a Finance Account of parent-child type Dimension](../multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md), and [Create a Currency type Dimension](../multidimensional-models/database-dimensions-create-a-currency-type-dimension.md).</span></span>  
  
 <span data-ttu-id="4b5a1-108">La valeur par défaut pour le type de dimension est `Regular`, qui ne fait pas d'hypothèse quant au contenu de la dimension.</span><span class="sxs-lookup"><span data-stu-id="4b5a1-108">The default setting for the dimension type is `Regular`, which makes no assumptions about the contents of the dimension.</span></span> <span data-ttu-id="4b5a1-109">Il s'agit de la valeur par défaut pour toutes les dimensions quand vous définissez initialement une dimension, sauf si vous spécifiez `Time` en définissant la dimension avec l'Assistant Dimension.</span><span class="sxs-lookup"><span data-stu-id="4b5a1-109">This is the default setting for all dimensions when you initially define a dimension unless you specify `Time` when defining the dimension using the Dimension Wizard.</span></span> <span data-ttu-id="4b5a1-110">Il est également recommandé de laisser `Regular` comme type de dimension si aucun type approprié de Type de dimension ne figure dans l'Assistant Dimension.</span><span class="sxs-lookup"><span data-stu-id="4b5a1-110">You should also leave `Regular` as the dimension type if the Dimension Wizard does not list an appropriate type for Dimension type.</span></span>  
  
## <a name="available-dimension-types"></a><span data-ttu-id="4b5a1-111">Types de dimensions disponibles</span><span class="sxs-lookup"><span data-stu-id="4b5a1-111">Available Dimension Types</span></span>  
 <span data-ttu-id="4b5a1-112">Le tableau suivant décrit les types de dimensions disponibles dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4b5a1-112">The following table describes the dimension types available in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
|<span data-ttu-id="4b5a1-113">Type de dimension</span><span class="sxs-lookup"><span data-stu-id="4b5a1-113">Dimension type</span></span>|<span data-ttu-id="4b5a1-114">Description</span><span class="sxs-lookup"><span data-stu-id="4b5a1-114">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="4b5a1-115">Normal</span><span class="sxs-lookup"><span data-stu-id="4b5a1-115">Regular</span></span>|<span data-ttu-id="4b5a1-116">Une dimension dont le type n'a pas été défini avec un type de dimension spécial.</span><span class="sxs-lookup"><span data-stu-id="4b5a1-116">A dimension whose type has not been set to a special dimension type.</span></span>|  
|<span data-ttu-id="4b5a1-117">Temps</span><span class="sxs-lookup"><span data-stu-id="4b5a1-117">Time</span></span>|<span data-ttu-id="4b5a1-118">Une dimension dont les attributs représentent des périodes de temps, telles que des années, des semestres, des trimestres, des mois et des jours.</span><span class="sxs-lookup"><span data-stu-id="4b5a1-118">A dimension whose attributes represent time periods, such as years, semesters, quarters, months, and days.</span></span>|  
|<span data-ttu-id="4b5a1-119">Organisation</span><span class="sxs-lookup"><span data-stu-id="4b5a1-119">Organization</span></span>|<span data-ttu-id="4b5a1-120">Une dimension dont les attributs représentent des informations organisationnelles, telles que des employés ou des filiales.</span><span class="sxs-lookup"><span data-stu-id="4b5a1-120">A dimension whose attributes represent organizational information, such as employees or subsidiaries.</span></span>|  
|<span data-ttu-id="4b5a1-121">Geography</span><span class="sxs-lookup"><span data-stu-id="4b5a1-121">Geography</span></span>|<span data-ttu-id="4b5a1-122">Une dimension dont les attributs représentent des informations géographiques, telles que des villes ou des codes postaux.</span><span class="sxs-lookup"><span data-stu-id="4b5a1-122">A dimension whose attributes represent geographic information, such as cities or postal codes.</span></span>|  
|<span data-ttu-id="4b5a1-123">BillOfMaterials</span><span class="sxs-lookup"><span data-stu-id="4b5a1-123">BillOfMaterials</span></span>|<span data-ttu-id="4b5a1-124">Une dimension dont les attributs représentent des informations d'inventaire ou de fabrication, telles que des listes de composants pour des produits.</span><span class="sxs-lookup"><span data-stu-id="4b5a1-124">A dimension whose attributes represent inventory or manufacturing information, such as parts lists for products.</span></span>|  
|<span data-ttu-id="4b5a1-125">Comptes</span><span class="sxs-lookup"><span data-stu-id="4b5a1-125">Accounts</span></span>|<span data-ttu-id="4b5a1-126">Une dimension dont les attributs représentent un graphique de comptes utilisé à des fins de génération de rapports financiers.</span><span class="sxs-lookup"><span data-stu-id="4b5a1-126">A dimension whose attributes represent a chart of accounts for financial reporting purposes.</span></span>|  
|<span data-ttu-id="4b5a1-127">Clients</span><span class="sxs-lookup"><span data-stu-id="4b5a1-127">Customers</span></span>|<span data-ttu-id="4b5a1-128">Une dimension dont les attributs représentent des informations relatives à des clients ou des contacts.</span><span class="sxs-lookup"><span data-stu-id="4b5a1-128">A dimension whose attributes represent customer or contact information.</span></span>|  
|<span data-ttu-id="4b5a1-129">Produits</span><span class="sxs-lookup"><span data-stu-id="4b5a1-129">Products</span></span>|<span data-ttu-id="4b5a1-130">Une dimension dont les attributs représentent des informations relatives à des produits.</span><span class="sxs-lookup"><span data-stu-id="4b5a1-130">A dimension whose attributes represent product information.</span></span>|  
|<span data-ttu-id="4b5a1-131">Scénario</span><span class="sxs-lookup"><span data-stu-id="4b5a1-131">Scenario</span></span>|<span data-ttu-id="4b5a1-132">Une dimension dont les attributs représentent des informations de planification ou d'analyse stratégique.</span><span class="sxs-lookup"><span data-stu-id="4b5a1-132">A dimension whose attributes represent planning or strategic analysis information.</span></span>|  
|<span data-ttu-id="4b5a1-133">Quantitative</span><span class="sxs-lookup"><span data-stu-id="4b5a1-133">Quantitative</span></span>|<span data-ttu-id="4b5a1-134">Une dimension dont les attributs représentent des informations quantitatives.</span><span class="sxs-lookup"><span data-stu-id="4b5a1-134">A dimension whose attributes represent quantitative information.</span></span>|  
|<span data-ttu-id="4b5a1-135">Utilitaire</span><span class="sxs-lookup"><span data-stu-id="4b5a1-135">Utility</span></span>|<span data-ttu-id="4b5a1-136">Une dimension dont les attributs représentent des informations diverses.</span><span class="sxs-lookup"><span data-stu-id="4b5a1-136">A dimension whose attributes represent miscellaneous information.</span></span>|  
|<span data-ttu-id="4b5a1-137">Devise</span><span class="sxs-lookup"><span data-stu-id="4b5a1-137">Currency</span></span>|<span data-ttu-id="4b5a1-138">Ce type de dimension contient des données et des métadonnées monétaires.</span><span class="sxs-lookup"><span data-stu-id="4b5a1-138">This type of dimension contains currency data and metadata.</span></span>|  
|<span data-ttu-id="4b5a1-139">Rates</span><span class="sxs-lookup"><span data-stu-id="4b5a1-139">Rates</span></span>|<span data-ttu-id="4b5a1-140">Une dimension dont les attributs représentent des informations relatives à des taux de devises.</span><span class="sxs-lookup"><span data-stu-id="4b5a1-140">A dimension whose attributes represent currency rate information.</span></span>|  
|<span data-ttu-id="4b5a1-141">Channel</span><span class="sxs-lookup"><span data-stu-id="4b5a1-141">Channel</span></span>|<span data-ttu-id="4b5a1-142">Une dimension dont les attributs représentent des informations de canaux.</span><span class="sxs-lookup"><span data-stu-id="4b5a1-142">A dimension whose attributes represent channel information.</span></span>|  
|<span data-ttu-id="4b5a1-143">Promotion</span><span class="sxs-lookup"><span data-stu-id="4b5a1-143">Promotion</span></span>|<span data-ttu-id="4b5a1-144">Une dimension dont les attributs représentent des informations de promotion commerciale.</span><span class="sxs-lookup"><span data-stu-id="4b5a1-144">A dimension whose attributes represent marketing promotion information.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4b5a1-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b5a1-145">See Also</span></span>  
 <span data-ttu-id="4b5a1-146">[Créer une dimension à l’aide d’une table existante](../multidimensional-models/create-a-dimension-by-using-an-existing-table.md) </span><span class="sxs-lookup"><span data-stu-id="4b5a1-146">[Create a Dimension by Using an Existing Table](../multidimensional-models/create-a-dimension-by-using-an-existing-table.md) </span></span>  
 [<span data-ttu-id="4b5a1-147">Dimensions &#40;Analysis Services - Données multidimensionnelles&#41;</span><span class="sxs-lookup"><span data-stu-id="4b5a1-147">Dimensions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimensions-analysis-services-multidimensional-data.md)  
  
  