---
title: Exploration du cube | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 3819946e-d3fa-4c1d-afe3-599c938b1b2e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7cbf35866bb0a1f65074a7e106ecf556e98aa30b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87600268"
---
# <a name="browsing-the-cube"></a><span data-ttu-id="c6b64-102">Exploration du cube</span><span class="sxs-lookup"><span data-stu-id="c6b64-102">Browsing the Cube</span></span>
  <span data-ttu-id="c6b64-103">Une fois le cube déployé, il est possible d'afficher les données de cube sous l'onglet **Navigateur** du Concepteur de cube et les données de dimension sous l'onglet **Navigateur** du Concepteur de dimensions.</span><span class="sxs-lookup"><span data-stu-id="c6b64-103">After you deploy a cube, the cube data is viewable on the **Browser** tab in Cube Designer, and the dimension data is viewable on the **Browser** tab in Dimension Designer.</span></span> <span data-ttu-id="c6b64-104">L'exploration du cube et des données de dimension permet de vérifier votre travail de façon incrémentielle.</span><span class="sxs-lookup"><span data-stu-id="c6b64-104">Browsing cube and dimension data is way to check your work incrementally.</span></span> <span data-ttu-id="c6b64-105">Vous pouvez vérifier que de petites modifications apportées aux propriétés, aux relations et d'autres objets ont l'effet souhaité une fois que l'objet est traité.</span><span class="sxs-lookup"><span data-stu-id="c6b64-105">You can verify that small changes to properties, relationships, and other objects have the desired effect once the object is processed.</span></span> <span data-ttu-id="c6b64-106">Lorsque l'onglet Navigateur est utilisé pour afficher à la fois le cube et les données de dimension, l'onglet fournit différentes fonctions en fonction de l'objet parcouru.</span><span class="sxs-lookup"><span data-stu-id="c6b64-106">While the Browser tab is used to view both cube and dimension data, the tab provides different capabilities based on the object you are browsing.</span></span>  
  
 <span data-ttu-id="c6b64-107">Pour les dimensions, l'onglet Navigateur permet d'afficher les membres ou de parcourir une hiérarchie jusqu'au nœud terminal.</span><span class="sxs-lookup"><span data-stu-id="c6b64-107">For dimensions, the Browser tab provides a way to view members or navigate a hierarchy all the way down to the leaf node.</span></span> <span data-ttu-id="c6b64-108">Vous pouvez parcourir les données de dimension dans différentes langues, en supposant que vous avez ajouté les traductions à votre modèle.</span><span class="sxs-lookup"><span data-stu-id="c6b64-108">You can browse dimension data in different languages, assuming you have added the translations to your model.</span></span>  
  
 <span data-ttu-id="c6b64-109">Pour les cubes, l'onglet Navigateur fournit deux approches d'exploration des données.</span><span class="sxs-lookup"><span data-stu-id="c6b64-109">For cubes, the Browser tab provides two approaches for exploring data.</span></span> <span data-ttu-id="c6b64-110">Vous pouvez utiliser le Concepteur de requêtes MDX intégré pour créer des requêtes qui renvoient un ensemble de lignes aplati à partir d'une base de données multidimensionnelle.</span><span class="sxs-lookup"><span data-stu-id="c6b64-110">You can use the built-in MDX Query Designer to build queries that return a flattened rowset from a multidimensional database.</span></span> <span data-ttu-id="c6b64-111">Sinon, vous pouvez utiliser un raccourci Excel.</span><span class="sxs-lookup"><span data-stu-id="c6b64-111">Alternatively, you can use an Excel shortcut.</span></span> <span data-ttu-id="c6b64-112">Lorsque vous démarrez Excel à partir de [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], Excel s'ouvre avec un tableau croisé dynamique dans la feuille de calcul et une connexion prédéfinie à la base de données d'espace de travail du modèle.</span><span class="sxs-lookup"><span data-stu-id="c6b64-112">When you start Excel from within [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], Excel opens with a PivotTable already in the worksheet and a predefined connection to the model workspace database.</span></span>  
  
 <span data-ttu-id="c6b64-113">Excel offre généralement une meilleure navigation car vous pouvez explorer les données du cube de façon interactive, avec des axes horizontaux et verticaux pour analyser les relations entre vos données.</span><span class="sxs-lookup"><span data-stu-id="c6b64-113">Excel generally offers a better browsing experience because you can explore cube data interactively, using horizontal and vertical axes to analyze the relationships in your data.</span></span> <span data-ttu-id="c6b64-114">En revanche, le Concepteur de requêtes MDX est limité à un seul axe.</span><span class="sxs-lookup"><span data-stu-id="c6b64-114">In contrast, the MDX Query Designer is limited to a single axis.</span></span> <span data-ttu-id="c6b64-115">De plus, étant donné que l'ensemble de lignes est aplati, vous ne bénéficiez pas de la fonction d'exploration fournit par un tableau croisé dynamique Excel.</span><span class="sxs-lookup"><span data-stu-id="c6b64-115">Moreover, because the rowset is flattened, you do not get the drilldown that an Excel PivotTable provides.</span></span> <span data-ttu-id="c6b64-116">Au fur et à mesure que vous ajoutez des dimensions et hiérarchies à votre cube, ce que vous ferez dans les leçons suivantes, Excel devient la solution la plus appropriée pour parcourir les données.</span><span class="sxs-lookup"><span data-stu-id="c6b64-116">As you add more dimensions and hierarchies to your cube, which you will do in subsequent lessons, Excel will be the preferred solution for browsing data.</span></span>  
  
### <a name="to-browse-the-deployed-cube"></a><span data-ttu-id="c6b64-117">Pour parcourir le cube déployé</span><span class="sxs-lookup"><span data-stu-id="c6b64-117">To browse the deployed cube</span></span>  
  
1.  <span data-ttu-id="c6b64-118">Basculez vers le **Concepteur de dimensions** pour la dimension Product dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c6b64-118">Switch to **Dimension Designer** for the Product dimension in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="c6b64-119">Pour cela, double-cliquez sur la dimension **Product** du nœud **Dimensions** de l’Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="c6b64-119">To do this, double-click the **Product** dimension in the **Dimensions** node of Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="c6b64-120">Cliquez sur l’onglet **navigateur** pour afficher le membre **tous** de la `Product Key` hiérarchie d’attribut.</span><span class="sxs-lookup"><span data-stu-id="c6b64-120">Click the **Browser** tab to display the **All** member of the `Product Key` attribute hierarchy.</span></span> <span data-ttu-id="c6b64-121">Dans la leçon 3, vous allez définir une hiérarchie utilisateur pour la dimension Product qui vous permettra de parcourir la dimension.</span><span class="sxs-lookup"><span data-stu-id="c6b64-121">In lesson three, you will define a user hierarchy for the Product dimension that will let you browse the dimension.</span></span>  
  
3.  <span data-ttu-id="c6b64-122">Basculez vers le **Concepteur de cube** dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c6b64-122">Switch to **Cube Designer** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="c6b64-123">Pour ce faire, double-cliquez sur le cube **Analysis Services Tutorial** dans le nœud **cubes** de Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="c6b64-123">To do this, double-click the **Analysis Services Tutorial** cube in the **Cubes** node of Solution Explorer.</span></span>  
  
4.  <span data-ttu-id="c6b64-124">Sélectionnez l'onglet **Navigateur** , puis cliquez sur l'icône **Reconnecter** dans la barre d'outils du concepteur.</span><span class="sxs-lookup"><span data-stu-id="c6b64-124">Select the **Browser** tab, and then click the **Reconnect** icon on the toolbar of the designer.</span></span>  
  
     <span data-ttu-id="c6b64-125">Le volet gauche du concepteur affiche les objets du cube Didacticiel [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c6b64-125">The left pane of the designer shows the objects in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span> <span data-ttu-id="c6b64-126">Sur le côté droit de l'onglet **Navigateur** se trouvent deux volets : le volet supérieur est le volet **Filtre** et le volet inférieur est le volet **Données** .</span><span class="sxs-lookup"><span data-stu-id="c6b64-126">On the right side of the **Browser** tab, there are two panes: the upper pane is the **Filter** pane, and the lower pane is the **Data** pane.</span></span> <span data-ttu-id="c6b64-127">Dans une prochaine leçon, vous utiliserez le navigateur de cube pour effectuer l'analyse.</span><span class="sxs-lookup"><span data-stu-id="c6b64-127">In an upcoming lesson, you will use the cube browser to do analysis.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="c6b64-128">Leçon suivante</span><span class="sxs-lookup"><span data-stu-id="c6b64-128">Next Lesson</span></span>  
 [<span data-ttu-id="c6b64-129">Leçon 3 : Modification des mesures, des attributs et des hiérarchies</span><span class="sxs-lookup"><span data-stu-id="c6b64-129">Lesson 3: Modifying Measures, Attributes and Hierarchies</span></span>](lesson-3-modifying-measures-attributes-and-hierarchies.md)  
  
## <a name="see-also"></a><span data-ttu-id="c6b64-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6b64-130">See Also</span></span>  
 [<span data-ttu-id="c6b64-131">Éditeur de requête MDX &#40;Analysis Services - Données multidimensionnelles&#41;</span><span class="sxs-lookup"><span data-stu-id="c6b64-131">MDX Query Editor &#40;Analysis Services - Multidimensional Data&#41;</span></span>](mdx-query-editor-analysis-services-multidimensional-data.md)  
  
  