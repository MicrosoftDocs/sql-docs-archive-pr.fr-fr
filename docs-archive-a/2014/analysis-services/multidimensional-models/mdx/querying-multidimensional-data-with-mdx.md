---
title: Interrogation de données multidimensionnelles avec MDX | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- multidimensional data [Analysis Services], querying
ms.assetid: e0a5dd60-35a3-4a4f-b36f-52ecea814886
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7b7589a98636e56e8c592cef213785544e18f4ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612563"
---
# <a name="querying-multidimensional-data-with-mdx"></a><span data-ttu-id="317e3-102">Interrogation de données multidimensionnelles à l'aide de MDX</span><span class="sxs-lookup"><span data-stu-id="317e3-102">Querying Multidimensional Data with MDX</span></span>
  <span data-ttu-id="317e3-103">Les expressions multidimensionnelles (MDX) sont le langage de requête que vous utilisez pour travailler avec et récupérer des données multidimensionnelles dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="317e3-103">Multidimensional Expressions (MDX) is the query language that you use to work with and retrieve multidimensional data in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="317e3-104">MDX est basé sur la spécification XMLA (XML for Analysis), avec des extensions spécifiques pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="317e3-104">MDX is based on the XML for Analysis (XMLA) specification, with specific extensions for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="317e3-105">MDX utilise des expressions composées d’identificateurs, de valeurs, d’instructions, de fonctions et d’opérateurs qu’ [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] peut évaluer pour extraire un objet (par exemple, un jeu ou un membre) ou une valeur scalaire (par exemple, une chaîne ou un nombre).</span><span class="sxs-lookup"><span data-stu-id="317e3-105">MDX utilizes expressions composed of identifiers, values, statements, functions, and operators that [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] can evaluate to retrieve an object (for example a set or a member), or a scalar value (for example, a string or a number).</span></span>  
  
 <span data-ttu-id="317e3-106">Les requêtes et les expressions MDX dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] sont utilisées pour effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="317e3-106">MDX queries and expressions in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] are used to do the following:</span></span>  
  
-   <span data-ttu-id="317e3-107">Retourner des données à une application cliente à partir d’un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] cube.</span><span class="sxs-lookup"><span data-stu-id="317e3-107">Return data to a client application from a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] cube.</span></span>  
  
-   <span data-ttu-id="317e3-108">Mettre en forme les résultats des requêtes.</span><span class="sxs-lookup"><span data-stu-id="317e3-108">Format query results.</span></span>  
  
-   <span data-ttu-id="317e3-109">Effectuer des tâches de conception liées aux cubes, notamment la définition de membres calculés, de jeux nommés, d'attributions d'étendues et d'indicateurs de performance clés (KPI).</span><span class="sxs-lookup"><span data-stu-id="317e3-109">Perform cube design tasks, including the definition of calculated members, named sets, scoped assignments, and key performance indicators (KPIs).</span></span>  
  
-   <span data-ttu-id="317e3-110">Effectuer des tâches administratives, notamment les tâches liées à la sécurité des dimensions et des cellules.</span><span class="sxs-lookup"><span data-stu-id="317e3-110">Perform administrative tasks, including dimension and cell security.</span></span>  
  
 <span data-ttu-id="317e3-111">À plusieurs égards, MDX s'apparente en surface à la syntaxe SQL généralement adoptée pour les bases de données relationnelles.</span><span class="sxs-lookup"><span data-stu-id="317e3-111">MDX is superficially similar in many ways to the SQL syntax that is typically used with relational databases.</span></span> <span data-ttu-id="317e3-112">Toutefois, MDX n'est pas une extension du langage SQL et présente de nombreuses différences par rapport à SQL.</span><span class="sxs-lookup"><span data-stu-id="317e3-112">However, MDX is not an extension of the SQL language and is different from SQL in many ways.</span></span> <span data-ttu-id="317e3-113">Pour être en mesure de créer des expressions MDX destinées à concevoir ou sécuriser des cubes, ou bien de créer des requêtes MDX en vue de retourner et de mettre en forme des données multidimensionnelles, vous devez maîtriser les concepts de base du langage MDX, la modélisation dimensionnelle, les éléments de syntaxe MDX, ainsi que les opérateurs, les instructions et les fonctions MDX.</span><span class="sxs-lookup"><span data-stu-id="317e3-113">In order to create MDX expressions used to design or secure cubes, or to create MDX queries to return and format multidimensional data, you need to understand basic concepts in MDX and dimensional modeling, MDX syntax elements, MDX operators, MDX statements, and MDX functions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="317e3-114">Pour plus d’informations, consultez la section ressources supplémentaires de la page [SQL Server 2005-Analysis Services](https://go.microsoft.com/fwlink/?LinkId=80853) sur le site Web Microsoft TechNet.</span><span class="sxs-lookup"><span data-stu-id="317e3-114">For more information, see the Additional Resources section on the [SQL Server 2005 - Analysis Services](https://go.microsoft.com/fwlink/?LinkId=80853) page on the Microsoft TechNet Web site.</span></span> <span data-ttu-id="317e3-115">Pour plus d’informations sur les problèmes de performances liés aux calculs et requêtes MDX, consultez la section « écriture d’expressions MDX efficaces » dans le [Guide des performances SQL Server 2005 Analysis Services](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide).</span><span class="sxs-lookup"><span data-stu-id="317e3-115">For more information about performance issues related to MDX queries and calculations, see the section "Writing Efficient MDX" in the [SQL Server 2005 Analysis Services Performance Guide](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="317e3-116">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="317e3-116">In This Section</span></span>  
  
|<span data-ttu-id="317e3-117">Rubrique</span><span class="sxs-lookup"><span data-stu-id="317e3-117">Topic</span></span>|<span data-ttu-id="317e3-118">Description</span><span class="sxs-lookup"><span data-stu-id="317e3-118">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="317e3-119">Concepts clés de MDX &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="317e3-119">Key Concepts in MDX &#40;Analysis Services&#41;</span></span>](../key-concepts-in-mdx-analysis-services.md)|<span data-ttu-id="317e3-120">Vous pouvez utiliser des expressions multidimensionnelles (MDX) pour interroger des données multidimensionnelles ou créer des expressions MDX à utiliser dans un cube, mais vous devez d’abord comprendre les [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] concepts et la terminologie de la dimension.</span><span class="sxs-lookup"><span data-stu-id="317e3-120">You can use Multidimensional Expressions (MDX) to query multidimensional data or to create MDX expressions for use within a cube, but first you should understand [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] dimension concepts and terminology.</span></span>|  
|[<span data-ttu-id="317e3-121">Principes de base des requêtes MDX &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="317e3-121">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-query-fundamentals-analysis-services.md)|<span data-ttu-id="317e3-122">La syntaxe MDX (Multidimensional Expressions) vous permet d'interroger les objets multidimensionnels, tels que des cubes, et de retourner des ensembles de cellules multidimensionnels contenant les données du cube.</span><span class="sxs-lookup"><span data-stu-id="317e3-122">Multidimensional Expressions (MDX) enables you to query multidimensional objects, such as cubes, and return multidimensional cellsets that contain the cube's data.</span></span> <span data-ttu-id="317e3-123">Cette rubrique et ses sous-rubriques donnent une vue d'ensemble des requêtes MDX.</span><span class="sxs-lookup"><span data-stu-id="317e3-123">This topic and its subtopics provide an overview of MDX queries.</span></span>|  
|[<span data-ttu-id="317e3-124">Principes de base des scripts MDX &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="317e3-124">MDX Scripting Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-scripting-fundamentals-analysis-services.md)|<span data-ttu-id="317e3-125">Dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], un script MDX (Multidimensional Expressions) est constitué d’une ou plusieurs expressions ou instructions MDX qui remplissent un cube avec des calculs.</span><span class="sxs-lookup"><span data-stu-id="317e3-125">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], a Multidimensional Expressions (MDX) script is made up of one or more MDX expressions or statements that populate a cube with calculations.</span></span><br /><br /> <span data-ttu-id="317e3-126">Un script MDX définit le processus de calcul pour un cube.</span><span class="sxs-lookup"><span data-stu-id="317e3-126">An MDX script defines the calculation process for a cube.</span></span> <span data-ttu-id="317e3-127">Il est également considéré comme un élément du cube proprement dit.</span><span class="sxs-lookup"><span data-stu-id="317e3-127">An MDX script is also considered part of the cube itself.</span></span> <span data-ttu-id="317e3-128">Par conséquent, la modification d'un script MDX associé à un cube entraîne immédiatement la modification de son processus de calcul.</span><span class="sxs-lookup"><span data-stu-id="317e3-128">Therefore, changing an MDX script associated with a cube immediately changes the calculation process for the cube.</span></span><br /><br /> <span data-ttu-id="317e3-129">Pour créer des scripts MDX, vous pouvez utiliser le Concepteur de cube disponible dans [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span><span class="sxs-lookup"><span data-stu-id="317e3-129">To create MDX scripts, you can use Cube Designer in the [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="317e3-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="317e3-130">See Also</span></span>  
 <span data-ttu-id="317e3-131">[Éléments de syntaxe MDX &#40;&#41;MDX](/sql/mdx/mdx-syntax-elements-mdx) </span><span class="sxs-lookup"><span data-stu-id="317e3-131">[MDX Syntax Elements &#40;MDX&#41;](/sql/mdx/mdx-syntax-elements-mdx) </span></span>  
 [<span data-ttu-id="317e3-132">Guide de référence du langage MDX &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="317e3-132">MDX Language Reference &#40;MDX&#41;</span></span>](/sql/mdx/mdx-language-reference-mdx)  
  
  