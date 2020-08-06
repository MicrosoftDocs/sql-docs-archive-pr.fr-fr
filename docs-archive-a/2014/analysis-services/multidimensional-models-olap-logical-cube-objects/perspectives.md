---
title: Perspectives | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- ready-only cube view
- OLAP objects [Analysis Services], perspectives
- storing data [Analysis Services], perspectives
- perspectives [Analysis Services]
- cubes [Analysis Services], perspectives
- visibility [Analysis Services]
- storage [Analysis Services], perspectives
ms.assetid: b064171e-b1b4-4f32-95e5-59e1b831c4c9
author: minewiskan
ms.author: owend
ms.openlocfilehash: f385fd078500739d97394cd8856fc8bd6a3b87e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702035"
---
# <a name="perspectives"></a><span data-ttu-id="41cdc-102">Perspectives</span><span class="sxs-lookup"><span data-stu-id="41cdc-102">Perspectives</span></span>
  <span data-ttu-id="41cdc-103">Une perspective est une définition qui permet aux utilisateurs de consulter un cube de façon plus simple.</span><span class="sxs-lookup"><span data-stu-id="41cdc-103">A perspective is a definition that allows users to see a cube in a simpler way.</span></span> <span data-ttu-id="41cdc-104">Une perspective est un sous-ensemble des fonctionnalités d'un cube.</span><span class="sxs-lookup"><span data-stu-id="41cdc-104">A perspective is a subset of the features of a cube.</span></span> <span data-ttu-id="41cdc-105">Une perspective permet aux administrateurs de créer des vues d'un cube, aidant ainsi les utilisateurs à se concentrer sur les données les plus pertinentes pour eux.</span><span class="sxs-lookup"><span data-stu-id="41cdc-105">A perspective enables administrators to create views of a cube, helping users to focus on the most relevant data for them.</span></span> <span data-ttu-id="41cdc-106">Une perspective contient les sous-ensembles de tous les objets d'un cube.</span><span class="sxs-lookup"><span data-stu-id="41cdc-106">A perspective contains subsets of all objects from a cube.</span></span> <span data-ttu-id="41cdc-107">Une perspective ne peut pas inclure les éléments qui ne sont pas définis dans le cube parent.</span><span class="sxs-lookup"><span data-stu-id="41cdc-107">A perspective cannot include elements that are not defined in the parent cube.</span></span>  
  
 <span data-ttu-id="41cdc-108">Un objet <xref:Microsoft.AnalysisServices.Perspective> simple est composé d’informations de base, de dimensions, de groupes de mesures, de calculs, d’indicateurs de performance clé et d’actions.</span><span class="sxs-lookup"><span data-stu-id="41cdc-108">A simple <xref:Microsoft.AnalysisServices.Perspective> object is composed of: basic information, dimensions, measure groups, calculations, KPIs, and actions.</span></span> <span data-ttu-id="41cdc-109">Les informations de base comprennent le nom et la mesure par défaut de la perspective.</span><span class="sxs-lookup"><span data-stu-id="41cdc-109">Basic information includes the name and the default measure of the perspective.</span></span> <span data-ttu-id="41cdc-110">Les dimensions sont un sous-ensemble des dimensions du cube.</span><span class="sxs-lookup"><span data-stu-id="41cdc-110">The dimensions are a subset of the cube dimensions.</span></span> <span data-ttu-id="41cdc-111">Les groupes de mesures sont un sous-ensemble des groupes de mesures du cube.</span><span class="sxs-lookup"><span data-stu-id="41cdc-111">The measure groups are a subset of the cube measure groups.</span></span> <span data-ttu-id="41cdc-112">Les calculs sont un sous-ensemble des calculs du cube.</span><span class="sxs-lookup"><span data-stu-id="41cdc-112">The calculations are a subset of the cube calculations.</span></span> <span data-ttu-id="41cdc-113">Les indicateurs de performance clé sont un sous-ensemble des indicateurs de performance clé du cube.</span><span class="sxs-lookup"><span data-stu-id="41cdc-113">The KPIs are a subset of the cube KPIs.</span></span> <span data-ttu-id="41cdc-114">Les actions sont un sous-ensemble des actions du cube.</span><span class="sxs-lookup"><span data-stu-id="41cdc-114">The actions are a subset of the cube actions.</span></span>  
  
 <span data-ttu-id="41cdc-115">Un cube doit être mis à jour et traité avant que la perspective ne puisse être utilisée.</span><span class="sxs-lookup"><span data-stu-id="41cdc-115">A cube has to be updated and processed before the perspective can be used.</span></span>  
  
 <span data-ttu-id="41cdc-116">Les cubes peuvent être des objets très complexes que les utilisateurs peuvent explorer dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="41cdc-116">Cubes can be very complex objects for users to explore in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="41cdc-117">Un cube unique peut représenter le contenu d'un entrepôt de données entier, avec plusieurs groupes de mesures dans un cube représentant plusieurs tables de faits et avec plusieurs dimensions reposant sur plusieurs tables de dimension.</span><span class="sxs-lookup"><span data-stu-id="41cdc-117">A single cube can represent the contents of a complete data warehouse, with multiple measure groups in a cube representing multiple fact tables, and multiple dimensions based on multiple dimension tables.</span></span> <span data-ttu-id="41cdc-118">Ce type de cube peut être très complexe et très puissant, mais difficile à utiliser pour ceux qui n'ont besoin d'interagir qu'avec une petite partie du cube afin de répondre à leurs besoins en termes de décisionnel et de rapports.</span><span class="sxs-lookup"><span data-stu-id="41cdc-118">Such a cube can be very complex and powerful, but daunting to users who may only need to interact with a small part of the cube in order to satisfy their business intelligence and reporting requirements.</span></span>  
  
 <span data-ttu-id="41cdc-119">Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , vous pouvez utiliser une perspective pour réduire la complexité perçue d’un cube dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="41cdc-119">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can use a perspective to reduce the perceived complexity of a cube in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="41cdc-120">Une perspective définit un sous-ensemble visualisable d'un cube qui fournit des points de vue focalisés sur un domaine d'activité ou sur une application.</span><span class="sxs-lookup"><span data-stu-id="41cdc-120">A perspective defines a viewable subset of a cube that provides focused, business-specific or application-specific viewpoints on the cube.</span></span> <span data-ttu-id="41cdc-121">La perspective contrôle la visibilité des objets contenus dans un cube.</span><span class="sxs-lookup"><span data-stu-id="41cdc-121">The perspective controls the visibility of objects that are contained by a cube.</span></span> <span data-ttu-id="41cdc-122">Les objets suivants peuvent être affichés ou masqués dans une perspective :</span><span class="sxs-lookup"><span data-stu-id="41cdc-122">The following objects can be displayed or hidden in a perspective:</span></span>  
  
-   <span data-ttu-id="41cdc-123">Dimensions</span><span class="sxs-lookup"><span data-stu-id="41cdc-123">Dimensions</span></span>  
  
-   <span data-ttu-id="41cdc-124">Attributs</span><span class="sxs-lookup"><span data-stu-id="41cdc-124">Attributes</span></span>  
  
-   <span data-ttu-id="41cdc-125">Hierarchies</span><span class="sxs-lookup"><span data-stu-id="41cdc-125">Hierarchies</span></span>  
  
-   <span data-ttu-id="41cdc-126">les groupes de mesures ;</span><span class="sxs-lookup"><span data-stu-id="41cdc-126">Measure groups</span></span>  
  
-   <span data-ttu-id="41cdc-127">Mesures</span><span class="sxs-lookup"><span data-stu-id="41cdc-127">Measures</span></span>  
  
-   <span data-ttu-id="41cdc-128">les indicateurs de performance clés (KPI) ;</span><span class="sxs-lookup"><span data-stu-id="41cdc-128">Key Performance Indicators (KPIs)</span></span>  
  
-   <span data-ttu-id="41cdc-129">les calculs (membres calculés, jeux nommés et commandes script) ;</span><span class="sxs-lookup"><span data-stu-id="41cdc-129">Calculations (calculated members, named sets, and script commands)</span></span>  
  
-   <span data-ttu-id="41cdc-130">Actions</span><span class="sxs-lookup"><span data-stu-id="41cdc-130">Actions</span></span>  
  
 <span data-ttu-id="41cdc-131">Par exemple, le cube **Adventure Works** de l' [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] exemple [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de base de données contient onze groupes de mesures et vingt-et-une dimensions de cube différentes, représentant les ventes, les prévisions de ventes et les données financières.</span><span class="sxs-lookup"><span data-stu-id="41cdc-131">For example, the **Adventure Works** cube in the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] sample [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database contains eleven measure groups and twenty-one different cube dimensions, representing sales, sales forecasting, and financial data.</span></span> <span data-ttu-id="41cdc-132">Une application cliente peut faire directement référence à la totalité du cube, mais ce point de vue peut être trop important si un utilisateur tente d'extraire des informations de base sur les ventes prévisionnelles.</span><span class="sxs-lookup"><span data-stu-id="41cdc-132">A client application can directly reference the complete cube, but this viewpoint may be overwhelming to a user trying to extract basic sales forecasting information.</span></span> <span data-ttu-id="41cdc-133">Au lieu de cela, le même utilisateur peut utiliser la perspective **Sales targets** pour limiter l’affichage du cube **Adventure Works** aux objets pertinents pour les prévisions de ventes.</span><span class="sxs-lookup"><span data-stu-id="41cdc-133">Instead, the same user can use the **Sales Targets** perspective to limit the view of the **Adventure Works** cube to only those objects relevant to sales forecasting.</span></span>  
  
 <span data-ttu-id="41cdc-134">Les objets d'un cube qui ne sont pas visibles pour l'utilisateur via une perspective peuvent cependant être directement référencés et récupérés à l'aide de XML for Analysis, des expressions MDX (Multidimensional Expressions) ou des instructions DMX (Data Mining Extensions).</span><span class="sxs-lookup"><span data-stu-id="41cdc-134">Objects in a cube that are not visible to the user through a perspective can still be directly referenced and retrieved using XML for Analysis (XMLA), Multidimensional Expressions (MDX), or Data Mining Extensions (DMX) statements.</span></span> <span data-ttu-id="41cdc-135">Les perspectives ne restreignent pas l'accès aux objets d'un cube et ne doivent pas être utilisées à cette fin. Elles doivent au contraire servir à optimiser l'expérience de l'utilisateur lorsqu'il accède à un cube.</span><span class="sxs-lookup"><span data-stu-id="41cdc-135">Perspectives do not restrict access to objects in a cube and should not be used as such; instead, perspectives are used to provide a better user experience while accessing a cube.</span></span>  
  
 <span data-ttu-id="41cdc-136">Une perspective est une vue en lecture seule du cube ; les objets du cube ne peuvent pas être renommés ni modifiés à l'aide d'une perspective.</span><span class="sxs-lookup"><span data-stu-id="41cdc-136">A perspective is a read-only view of the cube; objects in the cube cannot be renamed or changed by using a perspective.</span></span> <span data-ttu-id="41cdc-137">De la même façon, le comportement ou les fonctionnalités d'un cube, comme l'utilisation de valeurs visibles, ne peuvent pas être modifiés à l'aide d'une perspective.</span><span class="sxs-lookup"><span data-stu-id="41cdc-137">Similarly, the behavior or features of a cube, such as the use of visual totals, cannot be changed by using a perspective.</span></span>  
  
## <a name="security"></a><span data-ttu-id="41cdc-138">Sécurité</span><span class="sxs-lookup"><span data-stu-id="41cdc-138">Security</span></span>  
 <span data-ttu-id="41cdc-139">Les perspectives ne sont pas censées servir de mécanisme de sécurité, mais elles constituent plutôt un outil qui optimise l'expérience de l'utilisateur dans les applications de décisionnel.</span><span class="sxs-lookup"><span data-stu-id="41cdc-139">Perspectives are not meant to be used as a security mechanism, but as a tool for providing a better user experience in business intelligence applications.</span></span> <span data-ttu-id="41cdc-140">L'intégralité de la sécurité d'une perspective donnée est héritée du cube sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="41cdc-140">All security for a particular perspective is inherited from the underlying cube.</span></span> <span data-ttu-id="41cdc-141">Par exemple, les perspectives ne peuvent pas donner accès aux objets d'un cube auxquels un utilisateur n'a pas déjà accès.</span><span class="sxs-lookup"><span data-stu-id="41cdc-141">For example, perspectives cannot provide access to objects in a cube to which a user does not already have access.</span></span> <span data-ttu-id="41cdc-142">La sécurité du cube doit d'abord être résolue, avant que l'utilisateur ne puisse accéder aux objets d'un cube par le biais d'une perspective.</span><span class="sxs-lookup"><span data-stu-id="41cdc-142">- Security for the cube must be resolved before access to objects in the cube can be provided through a perspective.</span></span>  
  
  