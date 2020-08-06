---
title: Présentation des dimensions (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], about dimensions
- storage [Analysis Services], dimensions
- dimensions [Analysis Services], examples
- storing data [Analysis Services], dimensions
- storage [Analysis Services]
ms.assetid: ab170fdd-4144-42db-9497-690b9189fc25
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8df85723676df5f9fb1475465c8f7585384013ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601759"
---
# <a name="introduction-to-dimensions-analysis-services---multidimensional-data"></a><span data-ttu-id="4ce0c-102">Présentation des dimensions (Analysis Services - Données multidimensionnelles)</span><span class="sxs-lookup"><span data-stu-id="4ce0c-102">Introduction to Dimensions (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="4ce0c-103">Toutes les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dimensions Microsoft sont des groupes d’attributs basés sur des colonnes de tables ou de vues dans une vue de source de données.</span><span class="sxs-lookup"><span data-stu-id="4ce0c-103">All Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dimensions are groups of attributes based on columns from tables or views in a data source view.</span></span> <span data-ttu-id="4ce0c-104">Les dimensions existent indépendamment d'un cube, elles peuvent être utilisées dans plusieurs cubes et plusieurs fois dans un même cube, ainsi que liées entre les instances d'[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4ce0c-104">Dimensions exist independent of a cube, can be used in multiple cubes, can be used multiple times in a single cube, and can be linked between [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].instances.</span></span> <span data-ttu-id="4ce0c-105">Une dimension qui existe indépendamment d'un cube est appelée dimension de base de données et une instance de dimension de base de données dans un cube est appelée dimension de cube.</span><span class="sxs-lookup"><span data-stu-id="4ce0c-105">A dimension that exists independent of a cube is called a database dimension and an instance of a database dimension within a cube is called a cube dimension.</span></span>  
  
## <a name="dimension-based-on-a-star-schema-design"></a><span data-ttu-id="4ce0c-106">Dimension basée sur un schéma en étoile</span><span class="sxs-lookup"><span data-stu-id="4ce0c-106">Dimension based on a Star Schema Design</span></span>  
 <span data-ttu-id="4ce0c-107">La structure d'une dimension repose principalement sur la structure de la table ou des tables de dimension sous-jacentes.</span><span class="sxs-lookup"><span data-stu-id="4ce0c-107">The structure of a dimension is largely driven by the structure of the underlying dimension table or tables.</span></span> <span data-ttu-id="4ce0c-108">La structure la plus simple est appelée schéma en étoile, où chaque dimension est basée sur une seule table de dimension qui est directement liée à la table de faits par une relation clé primaire - clé étrangère.</span><span class="sxs-lookup"><span data-stu-id="4ce0c-108">The simplest structure is called a star schema, where each dimension is based on a single dimension table that is directly linked to the fact table by a primary key - foreign key relationship.</span></span>  
  
 <span data-ttu-id="4ce0c-109">Le diagramme suivant illustre une sous-section de l' [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)] exemple de base de données, dans laquelle la table de faits **FactResellerSales** est associée à deux tables de dimension, **DimReseller** et **DimPromotion**.</span><span class="sxs-lookup"><span data-stu-id="4ce0c-109">The following diagram illustrates a subsection of the [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)] sample database, in which the **FactResellerSales** fact table is related to two dimension tables, **DimReseller** and **DimPromotion**.</span></span> <span data-ttu-id="4ce0c-110">La colonne **ResellerKey** de la table de faits **FactResellerSales** définit une relation de clé étrangère avec la colonne de clé primaire **ResellerKey** dans la table de dimension **DimReseller** .</span><span class="sxs-lookup"><span data-stu-id="4ce0c-110">The **ResellerKey** column in the **FactResellerSales** fact table defines a foreign key relationship to the **ResellerKey** primary key column in the **DimReseller** dimension table.</span></span> <span data-ttu-id="4ce0c-111">De même, la colonne **PromotionrKey** de la table de faits **FactResellerSales** définit une relation de clé étrangère avec la colonne de clé primaire **PromotionrKey** dans la table de dimension **DimPromotion** .</span><span class="sxs-lookup"><span data-stu-id="4ce0c-111">Similarly, the **PromotionKey** column in the **FactResellerSales** fact table defines a foreign key relationship to the **PromotionKey** primary key column in the **DimPromotion** dimension table.</span></span>  
  
 <span data-ttu-id="4ce0c-112">![Schéma logique pour la relation de dimensions de fait](../../analysis-services/dev-guide/media/dimfactrelationship.gif "Schéma logique pour la relation de dimensions de fait")</span><span class="sxs-lookup"><span data-stu-id="4ce0c-112">![Logical schema for fact dimension relationship](../../analysis-services/dev-guide/media/dimfactrelationship.gif "Logical schema for fact dimension relationship")</span></span>  
  
## <a name="dimension-based-on-a-snowflake-schema-design"></a><span data-ttu-id="4ce0c-113">Dimension basée sur un schéma en flocon</span><span class="sxs-lookup"><span data-stu-id="4ce0c-113">Dimension based on a Snowflake Schema Design</span></span>  
 <span data-ttu-id="4ce0c-114">Une structure plus complexe est fréquemment requise parce que des informations provenant de plusieurs tables sont nécessaires pour définir la dimension.</span><span class="sxs-lookup"><span data-stu-id="4ce0c-114">Frequently, a more complex structure is required because information from multiple tables is required to define the dimension.</span></span> <span data-ttu-id="4ce0c-115">Dans cette structure, appelée un schéma en flocon, chaque dimension est basée sur les attributs de plusieurs tables liées les unes aux autres ainsi qu'à la table de faits par des relations clé primaire - clé étrangère.</span><span class="sxs-lookup"><span data-stu-id="4ce0c-115">In this structure, called a snowflake schema, each dimension is based on attributes from columns in multiple tables linked to each other and ultimately to the fact table by primary key - foreign key relationships.</span></span> <span data-ttu-id="4ce0c-116">Par exemple, le diagramme suivant illustre les tables nécessaires pour décrire complètement la dimension Product dans l’exemple de projet **AdventureWorksDW** :</span><span class="sxs-lookup"><span data-stu-id="4ce0c-116">For example, the following diagram illustrates the tables required to completely describe the Product dimension in the **AdventureWorksDW** sample project:</span></span>  
  
 <span data-ttu-id="4ce0c-117">![Tables pour la dimension Product d'AdventureWorksAS](../../analysis-services/dev-guide/media/dimproduct.gif "Tables pour la dimension Product d'AdventureWorksAS")</span><span class="sxs-lookup"><span data-stu-id="4ce0c-117">![Tables for AdventureWorksAS Product dimension](../../analysis-services/dev-guide/media/dimproduct.gif "Tables for AdventureWorksAS Product dimension")</span></span>  
  
 <span data-ttu-id="4ce0c-118">Pour décrire complètement un produit, la catégorie et la sous-catégorie du produit doivent être incluses dans la dimension Product.</span><span class="sxs-lookup"><span data-stu-id="4ce0c-118">To completely describe a product, the product's category and subcategory must be included in the Product dimension.</span></span> <span data-ttu-id="4ce0c-119">Toutefois, ces informations ne résident pas directement dans la table principale pour la dimension **DimProduct** .</span><span class="sxs-lookup"><span data-stu-id="4ce0c-119">However, that information does not reside directly in the main table for the **DimProduct** dimension.</span></span> <span data-ttu-id="4ce0c-120">Une relation de clé étrangère entre **DimProduct** et **DimProductSubcategory**, qui a à son tour une relation de clé étrangère avec la table **DimProductCategory** , permet d’inclure les informations pour les catégories de produits et les sous-catégories dans la dimension Product.</span><span class="sxs-lookup"><span data-stu-id="4ce0c-120">A foreign key relationship from **DimProduct** to **DimProductSubcategory**, which in turn has a foreign key relationship to the **DimProductCategory** table, makes it possible to include the information for product categories and subcategories in the Product dimension.</span></span>  
  
## <a name="snowflake-schema-versus-reference-relationship"></a><span data-ttu-id="4ce0c-121">Schéma en flocon et relation de référence</span><span class="sxs-lookup"><span data-stu-id="4ce0c-121">Snowflake Schema versus Reference Relationship</span></span>  
 <span data-ttu-id="4ce0c-122">Parfois, vous pouvez être amené à choisir entre l'utilisation d'un schéma en flocons pour définir les attributs d'une dimension à partir de plusieurs tables ou la définition de deux dimensions distinctes avec l'établissement d'une relation de dimensions de référence entre celles-ci.</span><span class="sxs-lookup"><span data-stu-id="4ce0c-122">Sometimes, you may have a choice between using a snowflake schema to define attributes in a dimension from multiple tables, or defining two separate dimensions and defining a reference dimension relationship between them.</span></span> <span data-ttu-id="4ce0c-123">Le diagramme suivant montre ce scénario.</span><span class="sxs-lookup"><span data-stu-id="4ce0c-123">The following diagram illustrates such a scenario.</span></span>  
  
 <span data-ttu-id="4ce0c-124">![Schéma logique pour un exemple de dimension référencée](../../analysis-services/dev-guide/media/dimindirect.gif "Schéma logique pour un exemple de dimension référencée")</span><span class="sxs-lookup"><span data-stu-id="4ce0c-124">![Logical schema for sample referenced dimension](../../analysis-services/dev-guide/media/dimindirect.gif "Logical schema for sample referenced dimension")</span></span>  
  
 <span data-ttu-id="4ce0c-125">Dans le diagramme précédent, la table de faits **FactResellerSales** n’a pas de relation de clé étrangère avec la table de dimension **DimGeography** .</span><span class="sxs-lookup"><span data-stu-id="4ce0c-125">In the previous diagram, the **FactResellerSales** fact table does not have a foreign key relationship with the **DimGeography** dimension table.</span></span> <span data-ttu-id="4ce0c-126">Toutefois, la table de faits **FactResellerSales** a une relation de clé étrangère avec la table de dimension **DimReseller** qui, à son tour, a une relation de clé étrangère avec la table de dimension **DimGeography** .</span><span class="sxs-lookup"><span data-stu-id="4ce0c-126">However, the **FactResellerSales** fact table does have a foreign key relationship with the **DimReseller** dimension table, which in turn has a foreign key relationship with the **DimGeography** dimension table.</span></span> <span data-ttu-id="4ce0c-127">Pour définir une dimension Reseller qui contient des informations géographiques sur chaque revendeur, vous devez récupérer ces attributs à partir des tables de dimension **DimGeography** et **DimReseller** .</span><span class="sxs-lookup"><span data-stu-id="4ce0c-127">To define a Reseller dimension that contains geography information about each reseller, you would have to retrieve these attributes from the **DimGeography** and the **DimReseller** dimension tables.</span></span> <span data-ttu-id="4ce0c-128">Cependant, dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vous pouvez obtenir le même résultat en créant deux dimensions distinctes et en les liant avec un groupe de mesures en définissant une relation de dimensions de référence entre les deux dimensions.</span><span class="sxs-lookup"><span data-stu-id="4ce0c-128">However, in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can achieve the same result by creating two separate dimensions and linking them in a measure group by defining a reference dimension relationship between the two dimensions.</span></span> <span data-ttu-id="4ce0c-129">Pour plus d’informations sur les relations de dimension de référence, consultez [relations de dimension](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md).</span><span class="sxs-lookup"><span data-stu-id="4ce0c-129">For more information about reference dimension relationships, see [Dimension Relationships](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md).</span></span>  
  
 <span data-ttu-id="4ce0c-130">Un avantage des relations de dimensions de référence dans ce scénario est que vous pouvez créer une seule dimension Geography, puis créer plusieurs dimensions de cube basés sur cette dimension, sans qu'un espace de stockage supplémentaire soit nécessaire.</span><span class="sxs-lookup"><span data-stu-id="4ce0c-130">One advantage of using reference dimension relationships in this scenario is that you could create a single geography dimension and then create multiple cube dimensions based on the geography dimension, without requiring any additional storage space.</span></span> <span data-ttu-id="4ce0c-131">Par exemple, vous pouvez lier une des dimensions de cube Geography à une dimension Reseller, et une autre dimension de cube Geography à une dimension Customer.</span><span class="sxs-lookup"><span data-stu-id="4ce0c-131">For example, you could link one of the geography cube dimensions to a reseller dimension and another of the geography cube dimensions to a customer dimension.</span></span> <span data-ttu-id="4ce0c-132">**Rubriques connexes :**[relations de dimension](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md), [définir une relation référencée et des propriétés de relation référencée](../multidimensional-models/define-a-referenced-relationship-and-referenced-relationship-properties.md)</span><span class="sxs-lookup"><span data-stu-id="4ce0c-132">**Related topics:**[Dimension Relationships](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md), [Define a Referenced Relationship and Referenced Relationship Properties](../multidimensional-models/define-a-referenced-relationship-and-referenced-relationship-properties.md)</span></span>  
  
## <a name="processing-a-dimension"></a><span data-ttu-id="4ce0c-133">Traitement d'une dimension</span><span class="sxs-lookup"><span data-stu-id="4ce0c-133">Processing a Dimension</span></span>  
 <span data-ttu-id="4ce0c-134">Après avoir créé une dimension, vous devez traiter celle-ci avant de pouvoir afficher les membres des attributs et des hiérarchies dans la dimension.</span><span class="sxs-lookup"><span data-stu-id="4ce0c-134">After you create a dimension, you must process the dimension before you can view the members of the attributes and hierarchies in the dimension.</span></span> <span data-ttu-id="4ce0c-135">Après avoir modifié la structure d'une dimension ou après la mise à jour des informations de ses tables sous-jacentes, vous devez traiter à nouveau la dimension pour pouvoir afficher les modifications.</span><span class="sxs-lookup"><span data-stu-id="4ce0c-135">After the structure of a dimension is changed or the information in its underlying tables is updated, you have to process the dimension again before you can view the changes.</span></span> <span data-ttu-id="4ce0c-136">Lorsque vous traitez une dimension après des changements structuraux, vous devez également traiter les cubes qui comprennent cette dimension, sinon le cube ne sera pas visible.</span><span class="sxs-lookup"><span data-stu-id="4ce0c-136">When you process a dimension after structural changes, you must also process any cubes that include the dimension - or the cube will not be viewable.</span></span>  
  
## <a name="security"></a><span data-ttu-id="4ce0c-137">Sécurité</span><span class="sxs-lookup"><span data-stu-id="4ce0c-137">Security</span></span>  
 <span data-ttu-id="4ce0c-138">Tous les objets subordonnés d'une dimension, y compris les hiérarchies, les niveaux et les membres, sont protégés en utilisant des rôles dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4ce0c-138">All the subordinate objects of a dimension, including hierarchies, levels, and members, are secured using roles in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="4ce0c-139">La sécurité d'une dimension peut être appliquée à tous les cubes de la base de données qui utilisent la dimension, ou à un cube donné seulement.</span><span class="sxs-lookup"><span data-stu-id="4ce0c-139">Dimension security can be applied for all the cubes in the database that use the dimension, or for only a specific cube.</span></span> <span data-ttu-id="4ce0c-140">Pour plus d’informations sur la sécurité des dimensions, consultez [accorder des autorisations sur une dimension &#40;Analysis Services&#41;](../multidimensional-models/grant-permissions-on-a-dimension-analysis-services.md).</span><span class="sxs-lookup"><span data-stu-id="4ce0c-140">For more information about dimension security, see [Grant permissions on a dimension &#40;Analysis Services&#41;](../multidimensional-models/grant-permissions-on-a-dimension-analysis-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ce0c-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ce0c-141">See Also</span></span>  
 <span data-ttu-id="4ce0c-142">[Stockage de dimension](../multidimensional-models-olap-logical-dimension-objects/dimensions-storage.md) </span><span class="sxs-lookup"><span data-stu-id="4ce0c-142">[Dimension Storage](../multidimensional-models-olap-logical-dimension-objects/dimensions-storage.md) </span></span>  
 <span data-ttu-id="4ce0c-143">[Traductions de dimensions](../multidimensional-models-olap-logical-dimension-objects/dimension-translations.md) </span><span class="sxs-lookup"><span data-stu-id="4ce0c-143">[Dimension Translations](../multidimensional-models-olap-logical-dimension-objects/dimension-translations.md) </span></span>  
 [<span data-ttu-id="4ce0c-144">Dimensions activées en écriture</span><span class="sxs-lookup"><span data-stu-id="4ce0c-144">Write-Enabled Dimensions</span></span>](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  