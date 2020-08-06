---
title: Concepteur de cube (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Cube Designer
ms.assetid: a6692467-da88-4312-8b03-d812f2ae5a96
author: minewiskan
ms.author: owend
ms.openlocfilehash: b6ceb921e1a9d5e5e4e7d67f1c2556e8b37d5d50
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611417"
---
# <a name="cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="3b37c-102">Concepteur de cube (Analysis Services - Données multidimensionnelles)</span><span class="sxs-lookup"><span data-stu-id="3b37c-102">Cube Designer (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="3b37c-103">Le **Concepteur de cube** de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] permet de modifier diverses propriétés d’un cube, notamment ses groupes de mesures et ses mesures, ses dimensions et les relations avec ces dimensions, les méthodes de calcul, ses indicateurs de performance clés (KPI, Key Performance Indicator), les actions qui se rattachent au cube, les partitions, ses perspectives et les traductions qui y sont inclus, ainsi que de parcourir les données qu’il contient.</span><span class="sxs-lookup"><span data-stu-id="3b37c-103">Use **Cube Designer** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to edit various properties of an existing cube, including the measure groups and measures, cube dimensions and dimension relationships, calculations, key performance indicators (KPIs), actions, partitions, perspectives, and translations included in the cube, as well as to browse the data contained by the cube.</span></span> <span data-ttu-id="3b37c-104">Pour afficher la boîte de dialogue du **Concepteur de cube** , vous disposez de deux méthodes :</span><span class="sxs-lookup"><span data-stu-id="3b37c-104">You can display the **Cube Designer** dialog box by:</span></span>  
  
-   <span data-ttu-id="3b37c-105">Vous pouvez cliquer avec le bouton droit de la souris sur un cube dans **l’Explorateur de solutions** et sélectionner **Ouvrir** ou **Concepteur de vues** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="3b37c-105">Right-clicking a cube in **Solution Explorer** and selecting **Open** or **View Designer** from the context menu.</span></span>  
  
-   <span data-ttu-id="3b37c-106">Vous pouvez également double-cliquer sur un cube dans **l’Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="3b37c-106">Double-clicking a cube in **Solution Explorer**.</span></span>  
  
 <span data-ttu-id="3b37c-107">Le **Concepteur de cube** se compose des onglets suivants :</span><span class="sxs-lookup"><span data-stu-id="3b37c-107">The **Cube Designer** contains the following tabs:</span></span>  
  
## <a name="tabs"></a><span data-ttu-id="3b37c-108">Tabulations</span><span class="sxs-lookup"><span data-stu-id="3b37c-108">Tabs</span></span>  
  
|<span data-ttu-id="3b37c-109">Onglet</span><span class="sxs-lookup"><span data-stu-id="3b37c-109">Tab</span></span>|<span data-ttu-id="3b37c-110">Définition</span><span class="sxs-lookup"><span data-stu-id="3b37c-110">Definition</span></span>|  
|---------|----------------|  
|<span data-ttu-id="3b37c-111">**Structure de cube**</span><span class="sxs-lookup"><span data-stu-id="3b37c-111">**Cube Structure**</span></span>|<span data-ttu-id="3b37c-112">Cet onglet vous permet de créer et de modifier des groupes de mesures et les mesures même, d'ajouter des dimensions au cube et d'afficher les objets inclus dans le cube et qui sont associés à la vue de source de données.</span><span class="sxs-lookup"><span data-stu-id="3b37c-112">Use this tab to create and modify measure groups and measures, add cube dimensions, and display the objects included in the cube from the associated data source view.</span></span> <span data-ttu-id="3b37c-113">Pour plus d’informations sur cet onglet, consultez [Structure de cube &#40;Concepteur de cube&#41; &#40;Analysis Services - Données multidimensionnelles&#41;](cube-structure-cube-designer-analysis-services-multidimensional-data.md).</span><span class="sxs-lookup"><span data-stu-id="3b37c-113">For more information about this tab, see [Cube Structure &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](cube-structure-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="3b37c-114">**Utilisation de la dimension**</span><span class="sxs-lookup"><span data-stu-id="3b37c-114">**Dimension Usage**</span></span>|<span data-ttu-id="3b37c-115">Cet onglet permet de créer et de modifier les relations établies entre les dimensions du cube et les groupes de mesures inclus dans ce dernier.</span><span class="sxs-lookup"><span data-stu-id="3b37c-115">Use this tab to create and modify relationships between cube dimensions and measure groups included in the cube.</span></span> <span data-ttu-id="3b37c-116">Pour plus d’informations sur cet onglet, consultez [Utilisation de la dimension &#40;Concepteur de cube&#41; &#40;Analysis Services - Données multidimensionnelles&#41;](dimension-usage-cube-designer-analysis-services-multidimensional-data.md).</span><span class="sxs-lookup"><span data-stu-id="3b37c-116">For more information about this tab, see [Dimension Usage &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](dimension-usage-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="3b37c-117">**Calculs**</span><span class="sxs-lookup"><span data-stu-id="3b37c-117">**Calculations**</span></span>|<span data-ttu-id="3b37c-118">Utilisez cet onglet pour créer et modifier des calculs, notamment les membres calculés, les jeux nommés et les scripts MDX (Multidimensional Expressions) inclus dans le cube.</span><span class="sxs-lookup"><span data-stu-id="3b37c-118">Use this tab to create and modify calculations, including calculated members, named sets, and Multidimensional Expressions (MDX) scripts, included in the cube.</span></span> <span data-ttu-id="3b37c-119">Pour plus d’informations sur cet onglet, consultez [Calculs &#40;Concepteur de cube&#41; &#40;Analysis Services - Données multidimensionnelles&#41;](calculations-cube-designer-analysis-services-multidimensional-data.md).</span><span class="sxs-lookup"><span data-stu-id="3b37c-119">For more information about this tab, see [Calculations &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculations-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="3b37c-120">**KPI**</span><span class="sxs-lookup"><span data-stu-id="3b37c-120">**KPIs**</span></span>|<span data-ttu-id="3b37c-121">Dans cet onglet, vous pouvez créer et modifier des indicateurs de performance clés (KPI) inclus dans le cube.</span><span class="sxs-lookup"><span data-stu-id="3b37c-121">Use this tab to create and modify KPIs included in the cube.</span></span> <span data-ttu-id="3b37c-122">Pour plus d’informations sur cet onglet, consultez [Indicateurs de performance clés &#40;Concepteur de cube&#41; &#40;Analysis Services - Données multidimensionnelles&#41;](kpis-cube-designer-analysis-services-multidimensional-data.md).</span><span class="sxs-lookup"><span data-stu-id="3b37c-122">For more information about this tab, see [KPIs &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](kpis-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="3b37c-123">**Actions**</span><span class="sxs-lookup"><span data-stu-id="3b37c-123">**Actions**</span></span>|<span data-ttu-id="3b37c-124">Cet onglet permet de créer et de modifier des actions incluses dans le cube, telles que les actions d'extraction et les actions du rapport.</span><span class="sxs-lookup"><span data-stu-id="3b37c-124">Use this tab to create and modify actions, including drillthrough actions and report actions, included in the cube.</span></span> <span data-ttu-id="3b37c-125">Pour plus d’informations sur cet onglet, consultez [Actions &#40;Concepteur de cube&#41; &#40;Analysis Services - Données multidimensionnelles&#41;](actions-cube-designer-analysis-services-multidimensional-data.md).</span><span class="sxs-lookup"><span data-stu-id="3b37c-125">For more information about this tab, see [Actions &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](actions-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="3b37c-126">**Partitions**</span><span class="sxs-lookup"><span data-stu-id="3b37c-126">**Partitions**</span></span>|<span data-ttu-id="3b37c-127">Celui-ci permet de créer et de modifier des partitions incluses dans le cube, comme les paramètres de mise en cache proactive concernant les groupes de mesures et les partitions.</span><span class="sxs-lookup"><span data-stu-id="3b37c-127">Use this tab to create and modify partitions, including proactive caching settings for measure groups and partitions, included in the cube.</span></span> <span data-ttu-id="3b37c-128">Pour plus d’informations sur cet onglet, consultez [Partitions &#40;Concepteur de cube&#41; &#40;Analysis Services - Données multidimensionnelles&#41;](partitions-cube-designer-analysis-services-multidimensional-data.md).</span><span class="sxs-lookup"><span data-stu-id="3b37c-128">For more information about this tab, see [Partitions &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](partitions-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="3b37c-129">**Perspectives**</span><span class="sxs-lookup"><span data-stu-id="3b37c-129">**Perspectives**</span></span>|<span data-ttu-id="3b37c-130">Cet onglet vous permet de créer et modifier les perspectives incluses dans le cube.</span><span class="sxs-lookup"><span data-stu-id="3b37c-130">Use this tab to create and modify perspectives included in the cube.</span></span> <span data-ttu-id="3b37c-131">Pour plus d’informations sur cet onglet, consultez [Perspectives &#40;Concepteur de cube&#41; &#40;Analysis Services - Données multidimensionnelles&#41;](perspectives-cube-designer-analysis-services-multidimensional-data.md).</span><span class="sxs-lookup"><span data-stu-id="3b37c-131">For more information about this tab, see [Perspectives &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](perspectives-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="3b37c-132">**Translations**</span><span class="sxs-lookup"><span data-stu-id="3b37c-132">**Translations**</span></span>|<span data-ttu-id="3b37c-133">Cet onglet sert à créer et à modifier les traductions incluses dans le cube relatives aux groupes de mesures, aux mesures, aux dimensions du cube, aux perspectives, aux indicateurs de performance clés (KPI), aux actions, aux jeux nommés et aux membres calculés.</span><span class="sxs-lookup"><span data-stu-id="3b37c-133">Use this tab to create and modify translations for measure groups, measures, cube dimensions, perspectives, KPIs, actions, named sets, and calculated members included in the cube.</span></span> <span data-ttu-id="3b37c-134">Pour plus d’informations sur cet onglet, consultez [Traductions &#40;Concepteur de cube&#41; &#40;Analysis Services - Données multidimensionnelles&#41;](translations-cube-designer-analysis-services-multidimensional-data.md).</span><span class="sxs-lookup"><span data-stu-id="3b37c-134">For more information about this tab, see [Translations &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](translations-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="3b37c-135">**Browser**</span><span class="sxs-lookup"><span data-stu-id="3b37c-135">**Browser**</span></span>|<span data-ttu-id="3b37c-136">Ce dernier onglet vous permet de parcourir les données et les métadonnées faisant partie du cube.</span><span class="sxs-lookup"><span data-stu-id="3b37c-136">Use this tab to browse data and metadata for the cube.</span></span> <span data-ttu-id="3b37c-137">Pour plus d’informations sur cet onglet, consultez [Navigateur &#40;Concepteur de cube&#41; &#40;Analysis Services - Données multidimensionnelles&#41;](browser-cube-designer-analysis-services-multidimensional-data.md).</span><span class="sxs-lookup"><span data-stu-id="3b37c-137">For more information about this tab, see [Browser &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](browser-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3b37c-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b37c-138">See Also</span></span>  
 <span data-ttu-id="3b37c-139">[Objets de cube &#40;Analysis Services-données multidimensionnelles&#41;](multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="3b37c-139">[Cube Objects &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="3b37c-140">[Cubes dans les modèles multidimensionnels](multidimensional-models/cubes-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="3b37c-140">[Cubes in Multidimensional Models](multidimensional-models/cubes-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="3b37c-141">Analysis Services les concepteurs et les boîtes de dialogue &#40;les données multidimensionnelles&#41;</span><span class="sxs-lookup"><span data-stu-id="3b37c-141">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  