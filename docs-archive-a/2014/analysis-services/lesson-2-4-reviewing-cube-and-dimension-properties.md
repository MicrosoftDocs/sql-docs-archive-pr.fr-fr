---
title: Vérification des propriétés de cube et de dimension | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: dda922b8-6d75-4662-b09e-8a317c6a1c70
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7d2551fb88071bf9666f5c3447a70db35253a999
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87600276"
---
# <a name="reviewing-cube-and-dimension-properties"></a><span data-ttu-id="3c5d9-102">Vérification des propriétés de cube et de dimension</span><span class="sxs-lookup"><span data-stu-id="3c5d9-102">Reviewing Cube and Dimension Properties</span></span>
  <span data-ttu-id="3c5d9-103">Après avoir défini un cube, vous pouvez examiner les résultats en utilisant le Concepteur de cube.</span><span class="sxs-lookup"><span data-stu-id="3c5d9-103">After you have defined a cube, you can review the results by using Cube Designer.</span></span> <span data-ttu-id="3c5d9-104">Dans la tâche suivante, vous examinez la structure du cube dans le projet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial.</span><span class="sxs-lookup"><span data-stu-id="3c5d9-104">In the following task, you review the structure of the cube in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project.</span></span>  
  
### <a name="to-review-cube-and-dimension-properties-in-cube-designer"></a><span data-ttu-id="3c5d9-105">Pour vérifier les propriétés d'un cube et des dimensions dans le Concepteur de cube</span><span class="sxs-lookup"><span data-stu-id="3c5d9-105">To review cube and dimension properties in Cube Designer</span></span>  
  
1.  <span data-ttu-id="3c5d9-106">Pour ouvrir le Concepteur de cube, double-cliquez sur le cube **Analysis Services Tutorial** dans le nœud **Cubes** de l’Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="3c5d9-106">To open the Cube Designer, double-click the **Analysis Services Tutorial** cube in the **Cubes** node of Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="3c5d9-107">Dans le volet **Mesures** de l'onglet **Structure de cube** dans le Concepteur de cube, développez le groupe de mesures **Internet Sales** pour révéler les mesures définies.</span><span class="sxs-lookup"><span data-stu-id="3c5d9-107">In the **Measures** pane of the **Cube Structure** tab in Cube Designer, expand the **Internet Sales** measure group to reveal the defined measures.</span></span>  
  
     <span data-ttu-id="3c5d9-108">Vous pouvez modifier l'ordre en faisant glisser les mesures et en les plaçant dans l'ordre de votre choix.</span><span class="sxs-lookup"><span data-stu-id="3c5d9-108">You can change the order by dragging the measures into the order that you want.</span></span> <span data-ttu-id="3c5d9-109">Cet ordre aura une incidence sur la façon dont certaines applications clientes classent ces mesures.</span><span class="sxs-lookup"><span data-stu-id="3c5d9-109">The order you create affects how certain client applications order these measures.</span></span> <span data-ttu-id="3c5d9-110">Le groupe de mesures et chaque mesure dans ce groupe ont des propriétés que vous pouvez modifier dans la fenêtre des propriétés.</span><span class="sxs-lookup"><span data-stu-id="3c5d9-110">The measure group and each measure that it contains have properties that you can edit in the Properties window.</span></span>  
  
3.  <span data-ttu-id="3c5d9-111">Dans le volet **Dimensions** de l'onglet **Structure de cube** du Concepteur de cube, vérifiez les dimensions de cube que contient le cube du didacticiel [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3c5d9-111">In the **Dimensions** pane of the **Cube Structure** tab in Cube Designer, review the cube dimensions that are in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span>  
  
     <span data-ttu-id="3c5d9-112">Notez que si seulement trois dimensions ont été créées au niveau base de données (affichées dans l'Explorateur de solutions), cinq dimensions de cube existent dans le cube du didacticiel [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3c5d9-112">Notice that although only three dimensions were created at the database level, as displayed in Solution Explorer, there are five cube dimensions in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span> <span data-ttu-id="3c5d9-113">Le cube contient davantage de dimensions que la base de données car la dimension de base de données Date est utilisée comme base pour trois dimensions de cube liées à la date distinctes, basées sur des faits liés à la date et différents dans la table de faits.</span><span class="sxs-lookup"><span data-stu-id="3c5d9-113">The cube contains more dimensions than the database because the Date database dimension is used as the basis for three separate date-related cube dimensions, based on different date-related facts in the fact table.</span></span> <span data-ttu-id="3c5d9-114">Ces dimensions liées à la date sont également appelées des *dimensions de rôle actif*.</span><span class="sxs-lookup"><span data-stu-id="3c5d9-114">These date-related dimensions are also called *role playing dimensions*.</span></span> <span data-ttu-id="3c5d9-115">Ces trois dimensions de cube liées à la date permettent aux utilisateurs de dimensionner le cube selon trois faits distincts liés à chaque vente de produits : la date de commande du produit, la date d'échéance de l'exécution de la commande et la date d'expédition de la commande.</span><span class="sxs-lookup"><span data-stu-id="3c5d9-115">The three date-related cube dimensions let users dimension the cube by three separate facts that are related to each product sale: the product order date, the due date for fulfillment of the order, and the ship date for the order.</span></span> <span data-ttu-id="3c5d9-116">En réutilisant une seule dimension de base de données pour plusieurs dimensions de cube, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] simplifie la gestion des dimensions, utilise moins d'espace disque et réduit la durée globale de traitement.</span><span class="sxs-lookup"><span data-stu-id="3c5d9-116">By reusing a single database dimension for multiple cube dimensions, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] simplifies dimension management, uses less disk space, and reduces overall processing time.</span></span>  
  
4.  <span data-ttu-id="3c5d9-117">Dans le volet **Dimensions** de l'onglet **Structure de cube** , développez **Customer**, puis cliquez sur **Edit Customer** pour ouvrir la dimension dans le Concepteur de dimensions.</span><span class="sxs-lookup"><span data-stu-id="3c5d9-117">In the **Dimensions** pane of the **Cube Structure** tab, expand **Customer**, and then click **Edit Customer** to open the dimension in Dimension Designer.</span></span>  
  
     <span data-ttu-id="3c5d9-118">Le Concepteur de dimensions contient ces onglets : **Structure de dimension**, **Relations d'attributs**, **Traductions**et **Navigateur**.</span><span class="sxs-lookup"><span data-stu-id="3c5d9-118">Dimension Designer contains these tabs: **Dimension Structure**, **Attribute Relationships**, **Translations**, and **Browser**.</span></span> <span data-ttu-id="3c5d9-119">Notez que l'onglet **Structure de dimension** comporte trois volets : **Attributs**, **Hiérarchies et niveaux**et **Vue de source de données**.</span><span class="sxs-lookup"><span data-stu-id="3c5d9-119">Notice that the **Dimension Structure** tab includes three panes: **Attributes**, **Hierarchies**, and **Data Source View**.</span></span> <span data-ttu-id="3c5d9-120">Les attributs que la dimension contient apparaissent dans le volet **Attributs** .</span><span class="sxs-lookup"><span data-stu-id="3c5d9-120">The attributes that the dimension contains appear in the **Attributes** pane.</span></span> <span data-ttu-id="3c5d9-121">Pour plus d’informations, consultez [référence des propriétés d’attribut de dimension](multidimensional-models/dimension-attribute-properties-reference.md), créer des [hiérarchies définies par l’utilisateur](multidimensional-models/user-defined-hierarchies-create.md).</span><span class="sxs-lookup"><span data-stu-id="3c5d9-121">For more information, see [Dimension Attribute Properties Reference](multidimensional-models/dimension-attribute-properties-reference.md), [Create User-Defined Hierarchies](multidimensional-models/user-defined-hierarchies-create.md).</span></span>  
  
5.  <span data-ttu-id="3c5d9-122">Pour basculer vers le Concepteur de cube, cliquez avec le bouton droit sur le cube **Analysis Services Tutorial** dans le nœud **Cubes** de l’Explorateur de solutions, puis cliquez sur **Concepteur de vues**.</span><span class="sxs-lookup"><span data-stu-id="3c5d9-122">To switch to Cube Designer, right-click the **Analysis Services Tutorial** cube in the **Cubes** node in Solution Explorer, and then click **View Designer**.</span></span>  
  
6.  <span data-ttu-id="3c5d9-123">Dans le Concepteur de cube, cliquez sur l'onglet **Utilisation de la dimension** .</span><span class="sxs-lookup"><span data-stu-id="3c5d9-123">In Cube Designer, click the **Dimension Usage** tab.</span></span>  
  
     <span data-ttu-id="3c5d9-124">Dans cette vue du cube du didacticiel [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , vous pouvez voir les dimensions du cube qui sont utilisées par le groupe de mesures Internet Sales.</span><span class="sxs-lookup"><span data-stu-id="3c5d9-124">In this view of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, you can see the cube dimensions that are used by the Internet Sales measure group.</span></span> <span data-ttu-id="3c5d9-125">Vous pouvez également définir le type de relation entre chaque dimension et chaque groupe de mesures dans lequel elles sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="3c5d9-125">Also, you can define the type of relationship between each dimension and each measure group in which it is used.</span></span>  
  
7.  <span data-ttu-id="3c5d9-126">Cliquez sur l’onglet **partitions** .</span><span class="sxs-lookup"><span data-stu-id="3c5d9-126">Click the **Partitions** tab.</span></span>  
  
     <span data-ttu-id="3c5d9-127">L'Assistant Cube définit une seule partition pour le cube en utilisant le mode de stockage MOLAP (Multidimensional Online Analytical Processing) sans agrégations.</span><span class="sxs-lookup"><span data-stu-id="3c5d9-127">The Cube Wizard defines a single partition for the cube, by using the multidimensional online analytical processing (MOLAP) storage mode without aggregations.</span></span> <span data-ttu-id="3c5d9-128">Avec MOLAP, toutes les données de niveau feuille et toutes les agrégations sont stockées dans le cube de façon à obtenir des performances maximales.</span><span class="sxs-lookup"><span data-stu-id="3c5d9-128">With MOLAP, all leaf-level data and all aggregations are stored within the cube for maximum performance.</span></span> <span data-ttu-id="3c5d9-129">Les agrégations sont des données de synthèse précalculées qui améliorent les temps de réponse des requêtes, tout simplement parce que les réponses sont prêtes avant que les questions ne soient posées.</span><span class="sxs-lookup"><span data-stu-id="3c5d9-129">Aggregations are precalculated summaries of data that improve query response time by having answers ready before questions are asked.</span></span> <span data-ttu-id="3c5d9-130">Vous pouvez définir des partitions supplémentaires, des paramètres de stockage et des paramètres d’écriture différée dans l’onglet **partitions** . Pour plus d’informations, consultez [partitions &#40;Analysis Services-&#41;de données multidimensionnelles ](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md), [agrégations et conceptions d’agrégation](multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md).</span><span class="sxs-lookup"><span data-stu-id="3c5d9-130">You can define additional partitions, storage settings, and writeback settings on the **Partitions** tab. For more information, see [Partitions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md), [Aggregations and Aggregation Designs](multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md).</span></span>  
  
8.  <span data-ttu-id="3c5d9-131">Cliquez sur l'onglet **Navigateur** .</span><span class="sxs-lookup"><span data-stu-id="3c5d9-131">Click the **Browser** tab.</span></span>  
  
     <span data-ttu-id="3c5d9-132">Notez que le cube ne peut pas être exploré car il n'a pas encore été déployé sur une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3c5d9-132">Notice that the cube cannot be browsed because it has not yet been deployed to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="3c5d9-133">À ce stade, le cube du projet du didacticiel [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] est simplement une définition de cube que vous pouvez déployer sur une instance quelconque de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3c5d9-133">At this point, the cube in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project is just a definition of a cube, which you can deploy to any instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="3c5d9-134">Lorsque vous déployez et traitez un cube, vous créez les objets définis dans une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] et remplissez les objets à partir des données issues des sources de données sous-jacentes.</span><span class="sxs-lookup"><span data-stu-id="3c5d9-134">When you deploy and process a cube, you create the defined objects in an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] and populate the objects with data from the underlying data sources.</span></span>  
  
9. <span data-ttu-id="3c5d9-135">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **Analysis Services Tutorial** dans le nœud **Cubes** , puis cliquez sur **Afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="3c5d9-135">In Solution Explorer, right-click **Analysis Services Tutorial** in the **Cubes** node, and then click **View Code**.</span></span> <span data-ttu-id="3c5d9-136">Cela peut prendre un certain temps.</span><span class="sxs-lookup"><span data-stu-id="3c5d9-136">You might need to wait.</span></span>  
  
     <span data-ttu-id="3c5d9-137">Le code XML du [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cube du didacticiel est affiché sous l’onglet \*\* [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial. cube [XML]\*\* . Il s’agit du code réel utilisé pour créer le cube dans une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] au cours du déploiement.</span><span class="sxs-lookup"><span data-stu-id="3c5d9-137">The XML code for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube is displayed on the **[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial.cube [XML]** tab. This is the actual code that is used to create the cube in an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] during deployment.</span></span> <span data-ttu-id="3c5d9-138">Pour plus d’informations, consultez [Afficher le code XML d’un projet Analysis Services &#40;SSDT&#41;](multidimensional-models/view-the-xml-for-an-analysis-services-project-ssdt.md).</span><span class="sxs-lookup"><span data-stu-id="3c5d9-138">For more information, see [View the XML for an Analysis Services Project &#40;SSDT&#41;](multidimensional-models/view-the-xml-for-an-analysis-services-project-ssdt.md).</span></span>  
  
10. <span data-ttu-id="3c5d9-139">Fermez l'onglet du code XML.</span><span class="sxs-lookup"><span data-stu-id="3c5d9-139">Close the XML code tab.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="3c5d9-140">Tâche suivante de la leçon</span><span class="sxs-lookup"><span data-stu-id="3c5d9-140">Next Task in Lesson</span></span>  
 [<span data-ttu-id="3c5d9-141">Déploiement d'un projet Analysis Services</span><span class="sxs-lookup"><span data-stu-id="3c5d9-141">Deploying an Analysis Services Project</span></span>](lesson-2-5-deploying-an-analysis-services-project.md)  
  
## <a name="see-also"></a><span data-ttu-id="3c5d9-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c5d9-142">See Also</span></span>  
 [<span data-ttu-id="3c5d9-143">Explorer les données d’une dimension dans le Concepteur de dimensions</span><span class="sxs-lookup"><span data-stu-id="3c5d9-143">Browse Dimension Data in Dimension Designer</span></span>](multidimensional-models/database-dimensions-browse-dimension-data-in-dimension-designer.md)  
  
  