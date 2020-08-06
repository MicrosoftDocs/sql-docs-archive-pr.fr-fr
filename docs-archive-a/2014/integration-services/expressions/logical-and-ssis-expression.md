---
title: '&amp;&amp; (AND logique) (expression SSIS) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '&& (logical AND)'
- AND, logical AND
- logical AND (&&)
ms.assetid: a8cb3517-d5d1-4861-9f04-905c719185ff
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8d973d7d4e86f88f7ae88c820ed4e4a5c1ce526f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697028"
---
# <a name="ampamp-logical-and-ssis-expression"></a><span data-ttu-id="759e8-102">&amp;&amp; (AND logique) (expression SSIS)</span><span class="sxs-lookup"><span data-stu-id="759e8-102">&amp;&amp; (Logical AND) (SSIS Expression)</span></span>
  <span data-ttu-id="759e8-103">Effectue une opération AND logique.</span><span class="sxs-lookup"><span data-stu-id="759e8-103">Performs a logical AND operation.</span></span> <span data-ttu-id="759e8-104">L'expression renvoie la valeur TRUE si toutes les conditions s'évaluent à TRUE.</span><span class="sxs-lookup"><span data-stu-id="759e8-104">The expression evaluates to TRUE if all conditions are TRUE.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="759e8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="759e8-105">Syntax</span></span>  
  
```  
  
boolean_expression1 && boolean_expression2  
```  
  
## <a name="arguments"></a><span data-ttu-id="759e8-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="759e8-106">Arguments</span></span>  
 <span data-ttu-id="759e8-107">*boolean_expression1, boolean_expression2*</span><span class="sxs-lookup"><span data-stu-id="759e8-107">*boolean _expression1, boolean_expression2*</span></span>  
 <span data-ttu-id="759e8-108">Expression valide qui renvoie TRUE, FALSE ou NULL.</span><span class="sxs-lookup"><span data-stu-id="759e8-108">Is any valid expression that evaluates to TRUE, FALSE, or NULL.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="759e8-109">Types des résultats</span><span class="sxs-lookup"><span data-stu-id="759e8-109">Result Types</span></span>  
 <span data-ttu-id="759e8-110">DT_BOOL</span><span class="sxs-lookup"><span data-stu-id="759e8-110">DT_BOOL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="759e8-111">Notes</span><span class="sxs-lookup"><span data-stu-id="759e8-111">Remarks</span></span>  
 <span data-ttu-id="759e8-112">Le tableau suivant indique le résultat de l'opérateur &&.</span><span class="sxs-lookup"><span data-stu-id="759e8-112">The following table shows the result of the && operator.</span></span>  
  
|<span data-ttu-id="759e8-113">Résultats</span><span class="sxs-lookup"><span data-stu-id="759e8-113">Result</span></span>|<span data-ttu-id="759e8-114">Expression</span><span class="sxs-lookup"><span data-stu-id="759e8-114">Expression</span></span>|<span data-ttu-id="759e8-115">Expression</span><span class="sxs-lookup"><span data-stu-id="759e8-115">Expression</span></span>|  
|------------|----------------|----------------|  
|<span data-ttu-id="759e8-116">TRUE</span><span class="sxs-lookup"><span data-stu-id="759e8-116">TRUE</span></span>|<span data-ttu-id="759e8-117">TRUE</span><span class="sxs-lookup"><span data-stu-id="759e8-117">TRUE</span></span>|<span data-ttu-id="759e8-118">TRUE</span><span class="sxs-lookup"><span data-stu-id="759e8-118">TRUE</span></span>|  
|<span data-ttu-id="759e8-119">FALSE</span><span class="sxs-lookup"><span data-stu-id="759e8-119">FALSE</span></span>|<span data-ttu-id="759e8-120">TRUE</span><span class="sxs-lookup"><span data-stu-id="759e8-120">TRUE</span></span>|<span data-ttu-id="759e8-121">FALSE</span><span class="sxs-lookup"><span data-stu-id="759e8-121">FALSE</span></span>|  
|<span data-ttu-id="759e8-122">FALSE</span><span class="sxs-lookup"><span data-stu-id="759e8-122">FALSE</span></span>|<span data-ttu-id="759e8-123">FALSE</span><span class="sxs-lookup"><span data-stu-id="759e8-123">FALSE</span></span>|<span data-ttu-id="759e8-124">FALSE</span><span class="sxs-lookup"><span data-stu-id="759e8-124">FALSE</span></span>|  
|<span data-ttu-id="759e8-125">NULL</span><span class="sxs-lookup"><span data-stu-id="759e8-125">NULL</span></span>|<span data-ttu-id="759e8-126">NULL</span><span class="sxs-lookup"><span data-stu-id="759e8-126">NULL</span></span>|<span data-ttu-id="759e8-127">NULL</span><span class="sxs-lookup"><span data-stu-id="759e8-127">NULL</span></span>|  
|<span data-ttu-id="759e8-128">NULL</span><span class="sxs-lookup"><span data-stu-id="759e8-128">NULL</span></span>|<span data-ttu-id="759e8-129">NULL</span><span class="sxs-lookup"><span data-stu-id="759e8-129">NULL</span></span>|<span data-ttu-id="759e8-130">TRUE</span><span class="sxs-lookup"><span data-stu-id="759e8-130">TRUE</span></span>|  
|<span data-ttu-id="759e8-131">FALSE</span><span class="sxs-lookup"><span data-stu-id="759e8-131">FALSE</span></span>|<span data-ttu-id="759e8-132">NULL</span><span class="sxs-lookup"><span data-stu-id="759e8-132">NULL</span></span>|<span data-ttu-id="759e8-133">FALSE</span><span class="sxs-lookup"><span data-stu-id="759e8-133">FALSE</span></span>|  
  
## <a name="expression-examples"></a><span data-ttu-id="759e8-134">Exemples d'expressions</span><span class="sxs-lookup"><span data-stu-id="759e8-134">Expression Examples</span></span>  
 <span data-ttu-id="759e8-135">L’exemple suivant utilise les colonnes **StandardCost** et **ListPrice** .</span><span class="sxs-lookup"><span data-stu-id="759e8-135">This example uses the **StandardCost** and the **ListPrice** columns.</span></span> <span data-ttu-id="759e8-136">L’exemple renvoie la valeur TRUE si la valeur de la colonne **StandardCost** est inférieure à 300 et que celle de la colonne **ListPrice** est supérieure à 500.</span><span class="sxs-lookup"><span data-stu-id="759e8-136">The example evaluates to TRUE if the value of the **StandardCost** column is less than 300 and the **ListPrice** column is greater than 500.</span></span>  
  
```  
StandardCost < 300 && ListPrice > 500  
```  
  
 <span data-ttu-id="759e8-137">L’exemple suivant utilise les variables **SPrice** et **LPrice** au lieu de littéraux.</span><span class="sxs-lookup"><span data-stu-id="759e8-137">This example uses the variables **SPrice** and **LPrice** instead of literals.</span></span>  
  
```  
StandardCost < @SPrice && ListPrice > @LPrice  
```  
  
## <a name="see-also"></a><span data-ttu-id="759e8-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="759e8-138">See Also</span></span>  
 <span data-ttu-id="759e8-139">[& &#40;AND au niveau du bit&#41; &#40;expression SSIS&#41;](bitwise-and-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="759e8-139">[& &#40;Bitwise AND&#41; &#40;SSIS Expression&#41;](bitwise-and-ssis-expression.md) </span></span>  
 <span data-ttu-id="759e8-140">[Priorités et associativité des opérateurs](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="759e8-140">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="759e8-141">Opérateurs &#40;expression SSIS&#41;</span><span class="sxs-lookup"><span data-stu-id="759e8-141">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  