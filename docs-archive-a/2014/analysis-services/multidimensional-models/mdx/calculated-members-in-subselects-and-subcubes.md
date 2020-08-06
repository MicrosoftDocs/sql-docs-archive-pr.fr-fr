---
title: Membres calculés dans les sous-sélections et les sous-cubes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6e35e8f7-ae1c-4549-8432-accf036d2373
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6e6f4277c864b637c7fc5d93232ac6ebd8c4bb4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611367"
---
# <a name="calculated-members-in-subselects-and-subcubes"></a><span data-ttu-id="d066b-102">Membres calculés dans les sous-sélections et les sous-cubes</span><span class="sxs-lookup"><span data-stu-id="d066b-102">Calculated Members in Subselects and Subcubes</span></span>
  <span data-ttu-id="d066b-103">Dans les versions précédentes, les membres calculés n'étaient pas autorisés dans les sous-sélections ou les sous-cubes.</span><span class="sxs-lookup"><span data-stu-id="d066b-103">In previous releases, calculated members were not allowed in subselects or subcubes.</span></span> <span data-ttu-id="d066b-104">Toutefois, à partir de SQL Server 2008, ils sont autorisés et activés par une propriété de connexion.</span><span class="sxs-lookup"><span data-stu-id="d066b-104">However, starting with SQL Server 2008 they are allowed and enabled by a connection property.</span></span> <span data-ttu-id="d066b-105">De plus, un nouveau comportement pour les membres calculés, dans les sous-sélections et les sous-cubes, a été introduit dans SQL Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="d066b-105">In addition, a new behavior for calculated members, in subselects and subcubes, was introduced in SQL Server 2008 R2.</span></span>  
  
## <a name="calculated-members-in-subselects-and-subcubes"></a><span data-ttu-id="d066b-106">Membres calculés dans les sous-sélections et les sous-cubes</span><span class="sxs-lookup"><span data-stu-id="d066b-106">Calculated Members in Subselects and Subcubes</span></span>  
 <span data-ttu-id="d066b-107">La `SubQueries` propriété de chaîne de connexion dans <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> ou la `DBPROPMSMDSUBQUERIES` propriété dans les [Propriétés xmla prises en charge &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties) définit le comportement ou l’allocation des membres calculés ou des jeux calculés sur les sous-sélections ou les sous-cubes.</span><span class="sxs-lookup"><span data-stu-id="d066b-107">The `SubQueries` connection string property in <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> or the `DBPROPMSMDSUBQUERIES` property in [Supported XMLA Properties &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties) defines the behavior or allowance of calculated members or calculated sets on subselects or subcubes.</span></span> <span data-ttu-id="d066b-108">Dans le cadre de ce document, sauf indication contraire, la sous-sélection fait référence aux sous-sélections et aux sous-cubes.</span><span class="sxs-lookup"><span data-stu-id="d066b-108">In the context of this document, subselect refers to subselects and subcubes unless otherwise stated.</span></span>  
  
 <span data-ttu-id="d066b-109">La propriété SubQueries autorise les valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="d066b-109">The SubQueries property allows the following values.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d066b-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="d066b-110">Value</span></span>|<span data-ttu-id="d066b-111">Description</span><span class="sxs-lookup"><span data-stu-id="d066b-111">Description</span></span>|  
|<span data-ttu-id="d066b-112">0</span><span class="sxs-lookup"><span data-stu-id="d066b-112">0</span></span>|<span data-ttu-id="d066b-113">Les membres calculés ne sont pas autorisés dans les sous-sélections ou les sous-cubes.</span><span class="sxs-lookup"><span data-stu-id="d066b-113">Calculated members are not allowed in subselects or subcubes.</span></span><br /><br /> <span data-ttu-id="d066b-114">Une erreur est déclenchée lors de l'évaluation de la sous-sélection ou du sous-cube si un membre calculé est référencé.</span><span class="sxs-lookup"><span data-stu-id="d066b-114">An error is raised when evaluating the subselect or subcube if a calculated member is referenced.</span></span>|  
|<span data-ttu-id="d066b-115">1</span><span class="sxs-lookup"><span data-stu-id="d066b-115">1</span></span>|<span data-ttu-id="d066b-116">Les membres calculés sont autorisés dans les sous-sélections ou les sous-cubes mais aucun membre ascendant n'est introduit dans le sous-espace retourné.</span><span class="sxs-lookup"><span data-stu-id="d066b-116">Calculated members are allowed in subselects or subcubes but no ascendant members are introduced in the returning subspace.</span></span>|  
|<span data-ttu-id="d066b-117">2</span><span class="sxs-lookup"><span data-stu-id="d066b-117">2</span></span>|<span data-ttu-id="d066b-118">Les membres calculés sont autorisés dans les sous-sélections et les sous-cubes mais aucun membre ascendant n'est introduit dans le sous-espace retourné.</span><span class="sxs-lookup"><span data-stu-id="d066b-118">Calculated members are allowed in subselects or subcubes and ascendant members are introduced in the returning subspace.</span></span> <span data-ttu-id="d066b-119">Par ailleurs, la granularité mixte est autorisée dans la sélection des membres calculés.</span><span class="sxs-lookup"><span data-stu-id="d066b-119">Also, mixed granularity is allowed in the selection of calculated members.</span></span>|  
  
 <span data-ttu-id="d066b-120">La définition des valeurs 1 ou 2 dans la propriété SubQueries autorise l'utilisation des membres calculés pour filtrer le sous-espace des sous-sélections retourné.</span><span class="sxs-lookup"><span data-stu-id="d066b-120">Using values of 1 or 2 in the SubQueries property allows calculated members to be used to filter the returning subspace of subselects.</span></span>  
  
 <span data-ttu-id="d066b-121">Un exemple aidera à clarifier le concept ; en premier lieu, un membre calculé doit être créé, ensuite une requête de sous-sélection doit être émise pour afficher le comportement susmentionné.</span><span class="sxs-lookup"><span data-stu-id="d066b-121">An example will help clarify the concept; first a calculated member must be created and then a subselect query issued to show the above mentioned behavior.</span></span>  
  
 <span data-ttu-id="d066b-122">L'exemple suivant crée un membre calculé qui ajoute [Seattle Metro] comme ville à la hiérarchie [Geography].[Geography] sous l'État de Washington.</span><span class="sxs-lookup"><span data-stu-id="d066b-122">The following sample creates a calculated member that adds [Seattle Metro] as a city to the [Geography].[Geography] hierarchy under Washington state.</span></span>  
  
 <span data-ttu-id="d066b-123">Pour exécuter l'exemple, la chaîne de connexion doit contenir la propriété SubQueries avec une valeur 1 et toutes les instructions MDX doivent être exécutées dans la même session.</span><span class="sxs-lookup"><span data-stu-id="d066b-123">To run the example, the connection string must contain the SubQueries property with a value of 1 and all MDX statements must be run in the same session.</span></span>  
  
 <span data-ttu-id="d066b-124">En premier lieu, vous devez émettre l'expression MDX suivante :</span><span class="sxs-lookup"><span data-stu-id="d066b-124">First issue the following MDX expression:</span></span>  
  
```  
//Remember to set Subqueries=1 in the connection string prior  
//to issue these commands  
//--> AS2008 behavior  
CREATE MEMBER [Adventure Works].[Geography].[Geography].[State-Province].&[WA]&[US].[Seattle Metro Agg]   
   AS  AGGREGATE(   
                 {   
                   [Geography].[Geography].[City].&[Bellevue]&[WA]  
                 , [Geography].[Geography].[City].&[Issaquah]&[WA]  
                 , [Geography].[Geography].[City].&[Redmond]&[WA]  
                 , [Geography].[Geography].[City].&[Seattle]&[WA]  
                 }  
                )    
```  
  
 <span data-ttu-id="d066b-125">Ensuite, émettez la requête MDX suivante pour afficher les membres calculés autorisés dans les sous-sélections.</span><span class="sxs-lookup"><span data-stu-id="d066b-125">Then issue the following MDX query to see calculated members allowed in subselects.</span></span>  
  
```  
Select [Date].[Calendar Year].members on 0,  
       [Geography].[Geography].allmembers on 1  
from (Select {[Geography].[Geography].[State-Province].&[WA]&[US].[Seattle Metro Agg]} on 0 from [Adventure Works])  
Where [Measures].[Reseller Sales Amount]  
```  
  
 <span data-ttu-id="d066b-126">Vous obtenez les résultats suivants :</span><span class="sxs-lookup"><span data-stu-id="d066b-126">The obtained results are:</span></span>  
  
|||||||  
|-|-|-|-|-|-|  
||<span data-ttu-id="d066b-127">All Periods</span><span class="sxs-lookup"><span data-stu-id="d066b-127">All Periods</span></span>|<span data-ttu-id="d066b-128">CY 2001</span><span class="sxs-lookup"><span data-stu-id="d066b-128">CY 2001</span></span>|<span data-ttu-id="d066b-129">CY 2002</span><span class="sxs-lookup"><span data-stu-id="d066b-129">CY 2002</span></span>|<span data-ttu-id="d066b-130">CY 2003</span><span class="sxs-lookup"><span data-stu-id="d066b-130">CY 2003</span></span>|<span data-ttu-id="d066b-131">CY 2004</span><span class="sxs-lookup"><span data-stu-id="d066b-131">CY 2004</span></span>|  
|<span data-ttu-id="d066b-132">Seattle Metro Agg</span><span class="sxs-lookup"><span data-stu-id="d066b-132">Seattle Metro Agg</span></span>|<span data-ttu-id="d066b-133">2 383 545,69 $</span><span class="sxs-lookup"><span data-stu-id="d066b-133">$2,383,545.69</span></span>|<span data-ttu-id="d066b-134">291 248,93 $</span><span class="sxs-lookup"><span data-stu-id="d066b-134">$291,248.93</span></span>|<span data-ttu-id="d066b-135">763 557,02 $</span><span class="sxs-lookup"><span data-stu-id="d066b-135">$763,557.02</span></span>|<span data-ttu-id="d066b-136">915 832,36 $</span><span class="sxs-lookup"><span data-stu-id="d066b-136">$915,832.36</span></span>|<span data-ttu-id="d066b-137">412 907,37 $</span><span class="sxs-lookup"><span data-stu-id="d066b-137">$412,907.37</span></span>|  
  
 <span data-ttu-id="d066b-138">Comme expliqué plus haut, les ascendants de [Seattle Metro] n'existent pas dans le sous-espace retourné lorsque SubQueries=1, par conséquent [Géographie].[Géographie].allmembers contient seulement le membre calculé.</span><span class="sxs-lookup"><span data-stu-id="d066b-138">As said before, the ascendants of [Seattle Metro] do not exist in the returned subspace, when SubQueries=1, hence [Geography].[Geography].allmembers only contains the calculated member.</span></span>  
  
 <span data-ttu-id="d066b-139">Si l'exemple est exécuté en utilisant SubQueries=2, dans la chaîne de connexion, vous obtenez les résultats suivants :</span><span class="sxs-lookup"><span data-stu-id="d066b-139">If the example is run using SubQueries=2, in the connection string, the obtained results are:</span></span>  
  
|||||||  
|-|-|-|-|-|-|  
||<span data-ttu-id="d066b-140">All Periods</span><span class="sxs-lookup"><span data-stu-id="d066b-140">All Periods</span></span>|<span data-ttu-id="d066b-141">CY 2001</span><span class="sxs-lookup"><span data-stu-id="d066b-141">CY 2001</span></span>|<span data-ttu-id="d066b-142">CY 2002</span><span class="sxs-lookup"><span data-stu-id="d066b-142">CY 2002</span></span>|<span data-ttu-id="d066b-143">CY 2003</span><span class="sxs-lookup"><span data-stu-id="d066b-143">CY 2003</span></span>|<span data-ttu-id="d066b-144">CY 2004</span><span class="sxs-lookup"><span data-stu-id="d066b-144">CY 2004</span></span>|  
|<span data-ttu-id="d066b-145">All Geographies</span><span class="sxs-lookup"><span data-stu-id="d066b-145">All Geographies</span></span>|<span data-ttu-id="d066b-146">(Null)</span><span class="sxs-lookup"><span data-stu-id="d066b-146">(null)</span></span>|<span data-ttu-id="d066b-147">(Null)</span><span class="sxs-lookup"><span data-stu-id="d066b-147">(null)</span></span>|<span data-ttu-id="d066b-148">(Null)</span><span class="sxs-lookup"><span data-stu-id="d066b-148">(null)</span></span>|<span data-ttu-id="d066b-149">(Null)</span><span class="sxs-lookup"><span data-stu-id="d066b-149">(null)</span></span>|<span data-ttu-id="d066b-150">(Null)</span><span class="sxs-lookup"><span data-stu-id="d066b-150">(null)</span></span>|  
|<span data-ttu-id="d066b-151">États-Unis</span><span class="sxs-lookup"><span data-stu-id="d066b-151">United States</span></span>|<span data-ttu-id="d066b-152">(Null)</span><span class="sxs-lookup"><span data-stu-id="d066b-152">(null)</span></span>|<span data-ttu-id="d066b-153">(Null)</span><span class="sxs-lookup"><span data-stu-id="d066b-153">(null)</span></span>|<span data-ttu-id="d066b-154">(Null)</span><span class="sxs-lookup"><span data-stu-id="d066b-154">(null)</span></span>|<span data-ttu-id="d066b-155">(Null)</span><span class="sxs-lookup"><span data-stu-id="d066b-155">(null)</span></span>|<span data-ttu-id="d066b-156">(Null)</span><span class="sxs-lookup"><span data-stu-id="d066b-156">(null)</span></span>|  
|<span data-ttu-id="d066b-157">Washington</span><span class="sxs-lookup"><span data-stu-id="d066b-157">Washington</span></span>|<span data-ttu-id="d066b-158">(Null)</span><span class="sxs-lookup"><span data-stu-id="d066b-158">(null)</span></span>|<span data-ttu-id="d066b-159">(Null)</span><span class="sxs-lookup"><span data-stu-id="d066b-159">(null)</span></span>|<span data-ttu-id="d066b-160">(Null)</span><span class="sxs-lookup"><span data-stu-id="d066b-160">(null)</span></span>|<span data-ttu-id="d066b-161">(Null)</span><span class="sxs-lookup"><span data-stu-id="d066b-161">(null)</span></span>|<span data-ttu-id="d066b-162">(Null)</span><span class="sxs-lookup"><span data-stu-id="d066b-162">(null)</span></span>|  
|<span data-ttu-id="d066b-163">Seattle Metro Agg</span><span class="sxs-lookup"><span data-stu-id="d066b-163">Seattle Metro Agg</span></span>|<span data-ttu-id="d066b-164">2 383 545,69 $</span><span class="sxs-lookup"><span data-stu-id="d066b-164">$2,383,545.69</span></span>|<span data-ttu-id="d066b-165">291 248,93 $</span><span class="sxs-lookup"><span data-stu-id="d066b-165">$291,248.93</span></span>|<span data-ttu-id="d066b-166">763 557,02 $</span><span class="sxs-lookup"><span data-stu-id="d066b-166">$763,557.02</span></span>|<span data-ttu-id="d066b-167">915 832,36 $</span><span class="sxs-lookup"><span data-stu-id="d066b-167">$915,832.36</span></span>|<span data-ttu-id="d066b-168">412 907,37 $</span><span class="sxs-lookup"><span data-stu-id="d066b-168">$412,907.37</span></span>|  
  
 <span data-ttu-id="d066b-169">Comme expliqué plus haut, lorsqu'on utilise SubQueries=2, les ascendants de [Seattle Metro] existent dans le sous-espace retourné mais aucune valeur n'existe pour ces membres parce qu'il n'y a pas de membres standard à fournir pour les agrégations.</span><span class="sxs-lookup"><span data-stu-id="d066b-169">As said before, when using SubQueries=2, the ascendants of [Seattle Metro] exist in the returned subspace but no values exist for those members because there is no regular members to provide for the aggregations.</span></span> <span data-ttu-id="d066b-170">Par conséquent, des valeurs de type Null sont fournies pour tous les membres ascendants du membre calculé dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="d066b-170">Therefore, NULL values are provided for all ascendant members of the calculated member in this example.</span></span>  
  
 <span data-ttu-id="d066b-171">Pour comprendre le comportement ci-dessus, vous devez comprendre que les membres calculés ne contribuent pas aux agrégations de leurs parents, contrairement aux membres standard ; pour plus d'informations à ce sujet, consultez ; ce qui précède implique que filtrer par les membres calculés seuls aboutira à des ascendants vides parce qu'il n'y a pas de membres standard qui contribuent aux valeurs d'agrégation du sous-espace résultant.</span><span class="sxs-lookup"><span data-stu-id="d066b-171">To understand the above behavior, it helps to understand that calculated members do not contribute to the aggregations of their parents as regular members do; the former implies that filtering by calculated members alone will lead to empty ascendants because there are no regular members to contribute to the aggregated values of the resulting subspace.</span></span> <span data-ttu-id="d066b-172">Si vous ajoutez des membres standard à l'expression de filtrage, les valeurs d'agrégation proviendront de ces membres standard.</span><span class="sxs-lookup"><span data-stu-id="d066b-172">If you add regular members to the filtering expression then the aggregated values will come from those regular members.</span></span> <span data-ttu-id="d066b-173">Pour poursuivre avec l'exemple ci-dessus, si les villes de Portland, Oregon, et la ville de Spokane, Washington, sont ajoutées au même axe où apparaît le membre calculé, comme indiqué dans l'expression MDX suivante :</span><span class="sxs-lookup"><span data-stu-id="d066b-173">Continuing with the above example, if the cities of Portland, in Oregon, and the city of Spokane, in Washington, are added to the same axis where the calculated member appears; as shown in the next MDX expression:</span></span>  
  
```  
Select [Date].[Calendar Year].members on 0,  
       [Geography].[Geography].allmembers on 1  
from (Select {  
               [Seattle Metro Agg]  
             , [Geography].[Geography].[City].&[Portland]&[OR]  
             , [Geography].[Geography].[City].&[Spokane]&[WA]  
             } on 0 from [Adventure Works]  
     )  
Where [Measures].[Reseller Sales Amount]  
```  
  
 <span data-ttu-id="d066b-174">Vous obtenez les résultats suivants.</span><span class="sxs-lookup"><span data-stu-id="d066b-174">The following results are obtained.</span></span>  
  
|||||||  
|-|-|-|-|-|-|  
||<span data-ttu-id="d066b-175">All Periods</span><span class="sxs-lookup"><span data-stu-id="d066b-175">All Periods</span></span>|<span data-ttu-id="d066b-176">CY 2001</span><span class="sxs-lookup"><span data-stu-id="d066b-176">CY 2001</span></span>|<span data-ttu-id="d066b-177">CY 2002</span><span class="sxs-lookup"><span data-stu-id="d066b-177">CY 2002</span></span>|<span data-ttu-id="d066b-178">CY 2003</span><span class="sxs-lookup"><span data-stu-id="d066b-178">CY 2003</span></span>|<span data-ttu-id="d066b-179">CY 2004</span><span class="sxs-lookup"><span data-stu-id="d066b-179">CY 2004</span></span>|  
|<span data-ttu-id="d066b-180">All Geographies</span><span class="sxs-lookup"><span data-stu-id="d066b-180">All Geographies</span></span>|<span data-ttu-id="d066b-181">$235,171.62</span><span class="sxs-lookup"><span data-stu-id="d066b-181">$235,171.62</span></span>|<span data-ttu-id="d066b-182">$419.46</span><span class="sxs-lookup"><span data-stu-id="d066b-182">$419.46</span></span>|<span data-ttu-id="d066b-183">$4,996.25</span><span class="sxs-lookup"><span data-stu-id="d066b-183">$4,996.25</span></span>|<span data-ttu-id="d066b-184">$131,788.82</span><span class="sxs-lookup"><span data-stu-id="d066b-184">$131,788.82</span></span>|<span data-ttu-id="d066b-185">$97,967.09</span><span class="sxs-lookup"><span data-stu-id="d066b-185">$97,967.09</span></span>|  
|<span data-ttu-id="d066b-186">États-Unis</span><span class="sxs-lookup"><span data-stu-id="d066b-186">United States</span></span>|<span data-ttu-id="d066b-187">$235,171.62</span><span class="sxs-lookup"><span data-stu-id="d066b-187">$235,171.62</span></span>|<span data-ttu-id="d066b-188">$419.46</span><span class="sxs-lookup"><span data-stu-id="d066b-188">$419.46</span></span>|<span data-ttu-id="d066b-189">$4,996.25</span><span class="sxs-lookup"><span data-stu-id="d066b-189">$4,996.25</span></span>|<span data-ttu-id="d066b-190">$131,788.82</span><span class="sxs-lookup"><span data-stu-id="d066b-190">$131,788.82</span></span>|<span data-ttu-id="d066b-191">$97,967.09</span><span class="sxs-lookup"><span data-stu-id="d066b-191">$97,967.09</span></span>|  
|<span data-ttu-id="d066b-192">Oregon</span><span class="sxs-lookup"><span data-stu-id="d066b-192">Oregon</span></span>|<span data-ttu-id="d066b-193">$30,968.25</span><span class="sxs-lookup"><span data-stu-id="d066b-193">$30,968.25</span></span>|<span data-ttu-id="d066b-194">$419.46</span><span class="sxs-lookup"><span data-stu-id="d066b-194">$419.46</span></span>|<span data-ttu-id="d066b-195">$4,996.25</span><span class="sxs-lookup"><span data-stu-id="d066b-195">$4,996.25</span></span>|<span data-ttu-id="d066b-196">$17,442.97</span><span class="sxs-lookup"><span data-stu-id="d066b-196">$17,442.97</span></span>|<span data-ttu-id="d066b-197">$8,109.56</span><span class="sxs-lookup"><span data-stu-id="d066b-197">$8,109.56</span></span>|  
|<span data-ttu-id="d066b-198">Portland</span><span class="sxs-lookup"><span data-stu-id="d066b-198">Portland</span></span>|<span data-ttu-id="d066b-199">$30,968.25</span><span class="sxs-lookup"><span data-stu-id="d066b-199">$30,968.25</span></span>|<span data-ttu-id="d066b-200">$419.46</span><span class="sxs-lookup"><span data-stu-id="d066b-200">$419.46</span></span>|<span data-ttu-id="d066b-201">$4,996.25</span><span class="sxs-lookup"><span data-stu-id="d066b-201">$4,996.25</span></span>|<span data-ttu-id="d066b-202">$17,442.97</span><span class="sxs-lookup"><span data-stu-id="d066b-202">$17,442.97</span></span>|<span data-ttu-id="d066b-203">$8,109.56</span><span class="sxs-lookup"><span data-stu-id="d066b-203">$8,109.56</span></span>|  
|<span data-ttu-id="d066b-204">97205</span><span class="sxs-lookup"><span data-stu-id="d066b-204">97205</span></span>|<span data-ttu-id="d066b-205">$30,968.25</span><span class="sxs-lookup"><span data-stu-id="d066b-205">$30,968.25</span></span>|<span data-ttu-id="d066b-206">$419.46</span><span class="sxs-lookup"><span data-stu-id="d066b-206">$419.46</span></span>|<span data-ttu-id="d066b-207">$4,996.25</span><span class="sxs-lookup"><span data-stu-id="d066b-207">$4,996.25</span></span>|<span data-ttu-id="d066b-208">$17,442.97</span><span class="sxs-lookup"><span data-stu-id="d066b-208">$17,442.97</span></span>|<span data-ttu-id="d066b-209">$8,109.56</span><span class="sxs-lookup"><span data-stu-id="d066b-209">$8,109.56</span></span>|  
|<span data-ttu-id="d066b-210">Washington</span><span class="sxs-lookup"><span data-stu-id="d066b-210">Washington</span></span>|<span data-ttu-id="d066b-211">$204,203.37</span><span class="sxs-lookup"><span data-stu-id="d066b-211">$204,203.37</span></span>|<span data-ttu-id="d066b-212">(Null)</span><span class="sxs-lookup"><span data-stu-id="d066b-212">(null)</span></span>|<span data-ttu-id="d066b-213">(Null)</span><span class="sxs-lookup"><span data-stu-id="d066b-213">(null)</span></span>|<span data-ttu-id="d066b-214">$114,345.85</span><span class="sxs-lookup"><span data-stu-id="d066b-214">$114,345.85</span></span>|<span data-ttu-id="d066b-215">$89,857.52</span><span class="sxs-lookup"><span data-stu-id="d066b-215">$89,857.52</span></span>|  
|<span data-ttu-id="d066b-216">Spokane</span><span class="sxs-lookup"><span data-stu-id="d066b-216">Spokane</span></span>|<span data-ttu-id="d066b-217">$204,203.37</span><span class="sxs-lookup"><span data-stu-id="d066b-217">$204,203.37</span></span>|<span data-ttu-id="d066b-218">(Null)</span><span class="sxs-lookup"><span data-stu-id="d066b-218">(null)</span></span>|<span data-ttu-id="d066b-219">(Null)</span><span class="sxs-lookup"><span data-stu-id="d066b-219">(null)</span></span>|<span data-ttu-id="d066b-220">$114,345.85</span><span class="sxs-lookup"><span data-stu-id="d066b-220">$114,345.85</span></span>|<span data-ttu-id="d066b-221">$89,857.52</span><span class="sxs-lookup"><span data-stu-id="d066b-221">$89,857.52</span></span>|  
|<span data-ttu-id="d066b-222">99202</span><span class="sxs-lookup"><span data-stu-id="d066b-222">99202</span></span>|<span data-ttu-id="d066b-223">$204,203.37</span><span class="sxs-lookup"><span data-stu-id="d066b-223">$204,203.37</span></span>|<span data-ttu-id="d066b-224">(Null)</span><span class="sxs-lookup"><span data-stu-id="d066b-224">(null)</span></span>|<span data-ttu-id="d066b-225">(Null)</span><span class="sxs-lookup"><span data-stu-id="d066b-225">(null)</span></span>|<span data-ttu-id="d066b-226">$114,345.85</span><span class="sxs-lookup"><span data-stu-id="d066b-226">$114,345.85</span></span>|<span data-ttu-id="d066b-227">$89,857.52</span><span class="sxs-lookup"><span data-stu-id="d066b-227">$89,857.52</span></span>|  
|<span data-ttu-id="d066b-228">Seattle Metro Agg</span><span class="sxs-lookup"><span data-stu-id="d066b-228">Seattle Metro Agg</span></span>|<span data-ttu-id="d066b-229">2 383 545,69 $</span><span class="sxs-lookup"><span data-stu-id="d066b-229">$2,383,545.69</span></span>|<span data-ttu-id="d066b-230">291 248,93 $</span><span class="sxs-lookup"><span data-stu-id="d066b-230">$291,248.93</span></span>|<span data-ttu-id="d066b-231">763 557,02 $</span><span class="sxs-lookup"><span data-stu-id="d066b-231">$763,557.02</span></span>|<span data-ttu-id="d066b-232">915 832,36 $</span><span class="sxs-lookup"><span data-stu-id="d066b-232">$915,832.36</span></span>|<span data-ttu-id="d066b-233">412 907,37 $</span><span class="sxs-lookup"><span data-stu-id="d066b-233">$412,907.37</span></span>|  
  
 <span data-ttu-id="d066b-234">Dans les résultats ci-dessus, les valeurs d'agrégation pour [All Geographies], [United States], [Oregon] et [Washington] proviennent de l'agrégation sur les descendants de &[Portland]&[OR] et &[Spokane]&[WA].</span><span class="sxs-lookup"><span data-stu-id="d066b-234">In the above results the aggregated values for [All Geographies], [United States], [Oregon] and [Washington] come from aggregating over the descendants of &[Portland]&[OR] and &[Spokane]&[WA].</span></span> <span data-ttu-id="d066b-235">Rien ne provient du membre calculé.</span><span class="sxs-lookup"><span data-stu-id="d066b-235">Nothing comes from the calculated member.</span></span>  
  
### <a name="remarks"></a><span data-ttu-id="d066b-236">Notes</span><span class="sxs-lookup"><span data-stu-id="d066b-236">Remarks</span></span>  
 <span data-ttu-id="d066b-237">Seuls les membres calculés globaux ou de session sont autorisés dans les expressions de sous-sélection ou de sous-cube.</span><span class="sxs-lookup"><span data-stu-id="d066b-237">Only global or session calculated members are allowed in the subselect or subcube expressions.</span></span> <span data-ttu-id="d066b-238">Si des membres calculés sont demandés dans l'expression MDX, une erreur est déclenchée lorsque l'expression de sous-sélection ou de sous-cube est évaluée.</span><span class="sxs-lookup"><span data-stu-id="d066b-238">Having query calculated members in the MDX expression will raise an error when the subselect or subcube expression is evaluated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d066b-239">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d066b-239">See Also</span></span>  
 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>   
 <span data-ttu-id="d066b-240">[Sous-sélections dans les requêtes](subselects-in-queries.md) </span><span class="sxs-lookup"><span data-stu-id="d066b-240">[Subselects in Queries](subselects-in-queries.md) </span></span>  
 [<span data-ttu-id="d066b-241">Propriétés XMLA prises en charge &#40;XMLA&#41;</span><span class="sxs-lookup"><span data-stu-id="d066b-241">Supported XMLA Properties &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties)  
  
  