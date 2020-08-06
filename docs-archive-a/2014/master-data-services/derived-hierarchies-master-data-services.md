---
title: Hiérarchies dérivées (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- derived hierarchies
- hierarchies [Master Data Services], derived hierarchies
- derived hierarchies, about derived hierarchies
ms.assetid: a0fbd519-a10e-4cbd-92e6-5de9b8d3e3f0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 92867f225a8f14e59cb9a519f174902d0739773a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615185"
---
# <a name="derived-hierarchies-master-data-services"></a><span data-ttu-id="6de5d-102">Hiérarchies dérivées (services de données de référence)</span><span class="sxs-lookup"><span data-stu-id="6de5d-102">Derived Hierarchies (Master Data Services)</span></span>
  <span data-ttu-id="6de5d-103">Une hiérarchie dérivée [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] est dérivée des relations d'attributs basés sur un domaine qui existent déjà entre des entités dans un modèle.</span><span class="sxs-lookup"><span data-stu-id="6de5d-103">A [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] derived hierarchy is derived from the domain-based attribute relationships that already exist between entities in a model.</span></span>

 <span data-ttu-id="6de5d-104">Vous pouvez créer une hiérarchie dérivée pour mettre en évidence une des relations d'attributs basés sur un domaine existantes dans le modèle.</span><span class="sxs-lookup"><span data-stu-id="6de5d-104">You can create a derived hierarchy to highlight any of the existing domain-based attribute relationships in the model.</span></span>

## <a name="leaf-members-group-other-leaf-members"></a><span data-ttu-id="6de5d-105">Les membres feuille regroupent d'autres membres feuille</span><span class="sxs-lookup"><span data-stu-id="6de5d-105">Leaf Members Group Other Leaf Members</span></span>
 <span data-ttu-id="6de5d-106">Dans une hiérarchie dérivée, les membres feuille d'une entité sont utilisés pour regrouper les membres feuille d'une autre entité.</span><span class="sxs-lookup"><span data-stu-id="6de5d-106">In a derived hierarchy, the leaf members from one entity are used to group the leaf members of another entity.</span></span> <span data-ttu-id="6de5d-107">Une hiérarchie dérivée est basée sur la relation entre ces entités.</span><span class="sxs-lookup"><span data-stu-id="6de5d-107">A derived hierarchy is based on the relationship between these entities.</span></span> <span data-ttu-id="6de5d-108">Une hiérarchie explicite, par opposition, est basée sur les membres d'une seule entité et vous êtes libre de la structurer selon vos besoins.</span><span class="sxs-lookup"><span data-stu-id="6de5d-108">An explicit hierarchy, in contrast, is based on members from a single entity only and is structured in any way you specify.</span></span>

 <span data-ttu-id="6de5d-109">Vous pouvez modifier la structure d'une hiérarchie dérivée sans affecter les données sous-jacentes.</span><span class="sxs-lookup"><span data-stu-id="6de5d-109">You can change the structure of a derived hierarchy without affecting the underlying data.</span></span> <span data-ttu-id="6de5d-110">Tant que les relations continuent d'exister dans le modèle, la suppression d'une hiérarchie dérivée n'a aucun effet sur vos données de référence.</span><span class="sxs-lookup"><span data-stu-id="6de5d-110">As long as the relationships still exist in the model, deleting a derived hierarchy has no effect on your master data.</span></span>

## <a name="explicit-hierarchies-versus-derived-hierarchies"></a><span data-ttu-id="6de5d-111">Hiérarchies explicites et hiérarchies dérivées</span><span class="sxs-lookup"><span data-stu-id="6de5d-111">Explicit Hierarchies versus Derived Hierarchies</span></span>
 <span data-ttu-id="6de5d-112">Le tableau suivant répertorie certaines différences entre les hiérarchies explicites et dérivées.</span><span class="sxs-lookup"><span data-stu-id="6de5d-112">The following table shows some of the differences between explicit and derived hierarchies.</span></span>

|<span data-ttu-id="6de5d-113">Hiérarchies explicites</span><span class="sxs-lookup"><span data-stu-id="6de5d-113">Explicit Hierarchies</span></span>|<span data-ttu-id="6de5d-114">Hiérarchies dérivées</span><span class="sxs-lookup"><span data-stu-id="6de5d-114">Derived Hierarchies</span></span>|
|--------------------------|-------------------------|
|<span data-ttu-id="6de5d-115">La structure est définie par l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="6de5d-115">Structure is defined by the user</span></span>|<span data-ttu-id="6de5d-116">La structure est dérivée des relations entre les attributs basés sur un domaine</span><span class="sxs-lookup"><span data-stu-id="6de5d-116">Structure is derived from the relationships between domain-based attributes</span></span>|
|<span data-ttu-id="6de5d-117">Contient les membres d'une seule entité</span><span class="sxs-lookup"><span data-stu-id="6de5d-117">Contains members from a single entity</span></span>|<span data-ttu-id="6de5d-118">Contient les membres de plusieurs entités</span><span class="sxs-lookup"><span data-stu-id="6de5d-118">Contains members from multiple entities</span></span>|
|<span data-ttu-id="6de5d-119">Utilise les membres consolidés pour regrouper d'autres membres</span><span class="sxs-lookup"><span data-stu-id="6de5d-119">Uses consolidated members to group other members</span></span>|<span data-ttu-id="6de5d-120">Utilise des membres feuille d'une entité pour regrouper des membres feuille d'une autre entité</span><span class="sxs-lookup"><span data-stu-id="6de5d-120">Uses leaf members from one entity to group leaf members from another entity</span></span>|
|<span data-ttu-id="6de5d-121">Peut être déséquilibré</span><span class="sxs-lookup"><span data-stu-id="6de5d-121">Can be ragged</span></span>|<span data-ttu-id="6de5d-122">Contient toujours un nombre cohérent de niveaux</span><span class="sxs-lookup"><span data-stu-id="6de5d-122">Always contains a consistent number of levels</span></span>|

## <a name="creating-a-variable-depth-hierarchy"></a><span data-ttu-id="6de5d-123">Créer une hiérarchie à profondeur variable</span><span class="sxs-lookup"><span data-stu-id="6de5d-123">Creating a Variable-Depth Hierarchy</span></span>
 <span data-ttu-id="6de5d-124">Il existe deux méthodes recommandées pour créer une hiérarchie à profondeur variable :</span><span class="sxs-lookup"><span data-stu-id="6de5d-124">There are two recommended ways to create a variable-depth hierarchy:</span></span>

-   <span data-ttu-id="6de5d-125">Si vous avez besoin que tous les niveaux aient les mêmes attributs, créez une entité unique, puis créez une hiérarchie récursive sur cette entité, avec un attribut basé sur un domaine, basé sur l'entité.</span><span class="sxs-lookup"><span data-stu-id="6de5d-125">If you need all levels to have the same attributes, create a single entity, and then create a recursive hierarchy on this entity, using a domain-based attribute that is based on the entity.</span></span>

-   <span data-ttu-id="6de5d-126">Si vous avez besoin d'un ensemble d'attributs pour les membres feuille et d'un ensemble d'attributs différent dans les niveaux supérieurs, créez deux entités pour une hiérarchie dérivée.</span><span class="sxs-lookup"><span data-stu-id="6de5d-126">If you need one set of attributes for the leaf members and another set of attributes in the upper levels, create two entities for a derived hierarchy.</span></span> <span data-ttu-id="6de5d-127">Pour l'entité de niveau feuille, utilisez un attribut basé sur un domaine qui est basé sur l'entité parente.</span><span class="sxs-lookup"><span data-stu-id="6de5d-127">For the leaf entity, use a domain-based attribute that is based upon the parent entity.</span></span> <span data-ttu-id="6de5d-128">Pour l'entité parente, utilisez un attribut basé sur un domaine qui est basé sur lui-même.</span><span class="sxs-lookup"><span data-stu-id="6de5d-128">For the parent entity, use a domain-based attribute that is based upon itself.</span></span>

## <a name="derived-hierarchy-example"></a><span data-ttu-id="6de5d-129">Exemple de hiérarchie dérivée</span><span class="sxs-lookup"><span data-stu-id="6de5d-129">Derived Hierarchy Example</span></span>
 <span data-ttu-id="6de5d-130">Dans l'exemple suivant, les membres feuille de l'entité Product sont regroupés par membres feuille de l'entité Subcategory, qui, à leur tour, sont regroupés par membres feuille de l'entité Category.</span><span class="sxs-lookup"><span data-stu-id="6de5d-130">In the following example, leaf members of the Product entity are grouped by leaf members of the Subcategory entity, which are then grouped by leaf members of the Category entity.</span></span> <span data-ttu-id="6de5d-131">Cette hiérarchie est possible parce que l'entité Product a un attribut basé sur un domaine nommé Subcategory, et que l'entité Subcategory a un attribut basé sur un domaine nommé Category.</span><span class="sxs-lookup"><span data-stu-id="6de5d-131">This hierarchy is possible because the Product entity has a domain-based attribute named Subcategory, and the Subcategory entity has a domain-based attribute named Category.</span></span>

 <span data-ttu-id="6de5d-132">La structure de hiérarchie montre comment les membres sont regroupés.</span><span class="sxs-lookup"><span data-stu-id="6de5d-132">The hierarchy structure shows how the members are grouped.</span></span> <span data-ttu-id="6de5d-133">L'entité qui compte le plus de membres se situe au niveau le plus bas.</span><span class="sxs-lookup"><span data-stu-id="6de5d-133">The entity with the most members is at the bottom.</span></span>

 <span data-ttu-id="6de5d-134">![Hiérarchie dérivée de la structure du modèle](../../2014/master-data-services/media/mds-conc-derived-hierarchy-structure.gif "Hiérarchie dérivée de la structure du modèle")</span><span class="sxs-lookup"><span data-stu-id="6de5d-134">![Hierarchy Derived from Model Structure](../../2014/master-data-services/media/mds-conc-derived-hierarchy-structure.gif "Hierarchy Derived from Model Structure")</span></span>

 <span data-ttu-id="6de5d-135">Dans une hiérarchie dérivée, vous pouvez mettre en évidence la relation entre Product et Subcategory, puis entre Subcategory et Category.</span><span class="sxs-lookup"><span data-stu-id="6de5d-135">In a derived hierarchy, you can highlight the relationship between Product and Subcategory, and then between Subcategory and Category.</span></span> <span data-ttu-id="6de5d-136">Lorsque vous affichez les membres dans cette hiérarchie, chaque niveau de l'arborescence contient des membres de la même entité.</span><span class="sxs-lookup"><span data-stu-id="6de5d-136">When you view the members in this hierarchy, each level in the tree contains members from the same entity.</span></span>

 <span data-ttu-id="6de5d-137">![Exemple de hiérarchie dérivée Mountain Bike](../../2014/master-data-services/media/mds-conc-derived-hierarchy-example.gif "Exemple de hiérarchie dérivée Mountain Bike")</span><span class="sxs-lookup"><span data-stu-id="6de5d-137">![Mountain Bike Derived Hierarchy Example](../../2014/master-data-services/media/mds-conc-derived-hierarchy-example.gif "Mountain Bike Derived Hierarchy Example")</span></span>

 <span data-ttu-id="6de5d-138">Ce type de hiérarchie vous empêche de déplacer un membre vers un niveau qui n'est pas valide.</span><span class="sxs-lookup"><span data-stu-id="6de5d-138">This type of hierarchy prevents you from moving a member to a level that is not valid.</span></span> <span data-ttu-id="6de5d-139">Par exemple, vous pouvez déplacer le vélo Road-650 d'une sous-catégorie, Road Bikes, vers une autre, Mountain Bikes.</span><span class="sxs-lookup"><span data-stu-id="6de5d-139">For example, you can move the Road-650 bike from one subcategory, Road Bikes, to another, Mountain Bikes.</span></span> <span data-ttu-id="6de5d-140">Vous ne pouvez pas déplacer directement Road-650 sous une catégorie, comme 1 {Bikes}.</span><span class="sxs-lookup"><span data-stu-id="6de5d-140">You cannot move Road-650 directly under a category, like 1 {Bikes}.</span></span> <span data-ttu-id="6de5d-141">Chaque fois que vous déplacez un membre dans l'arborescence hiérarchique, la valeur d'attribut basé sur un domaine du membre change pour refléter le déplacement.</span><span class="sxs-lookup"><span data-stu-id="6de5d-141">Each time you move a member in the hierarchy tree, the member's domain-based attribute value changes to reflect the move.</span></span>

## <a name="notes"></a><span data-ttu-id="6de5d-142">Notes</span><span class="sxs-lookup"><span data-stu-id="6de5d-142">Notes</span></span>
 <span data-ttu-id="6de5d-143">Tous les membres d'une arborescence hiérarchique dérivée sont triés par code.</span><span class="sxs-lookup"><span data-stu-id="6de5d-143">All members in a derived hierarchy tree are sorted by code.</span></span> <span data-ttu-id="6de5d-144">Vous ne pouvez pas modifier l'ordre de tri.</span><span class="sxs-lookup"><span data-stu-id="6de5d-144">You cannot change the sort order.</span></span>

 <span data-ttu-id="6de5d-145">Si l'attribut basé sur un domaine d'un membre est vide et que l'attribut est utilisé pour une hiérarchie dérivée, le membre n'est pas affiché dans la hiérarchie.</span><span class="sxs-lookup"><span data-stu-id="6de5d-145">If a member's domain-based attribute is blank and the attribute is used for a derived hierarchy, the member is not displayed in the hierarchy.</span></span> <span data-ttu-id="6de5d-146">Créez des règles d'entreprise pour requérir le remplissage des attributs.</span><span class="sxs-lookup"><span data-stu-id="6de5d-146">Create business rules to require attributes to be populated.</span></span> <span data-ttu-id="6de5d-147">Pour plus d’informations, consultez [Requérir des valeurs d’attribut &#40;Master Data Services&#41;](require-attribute-values-master-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="6de5d-147">For more information, see [Require Attribute Values &#40;Master Data Services&#41;](require-attribute-values-master-data-services.md).</span></span>

## <a name="related-tasks"></a><span data-ttu-id="6de5d-148">Tâches associées</span><span class="sxs-lookup"><span data-stu-id="6de5d-148">Related Tasks</span></span>

|<span data-ttu-id="6de5d-149">Description de la tâche</span><span class="sxs-lookup"><span data-stu-id="6de5d-149">Task Description</span></span>|<span data-ttu-id="6de5d-150">Rubrique</span><span class="sxs-lookup"><span data-stu-id="6de5d-150">Topic</span></span>|
|----------------------|-----------|
|<span data-ttu-id="6de5d-151">Créer une hiérarchie dérivée.</span><span class="sxs-lookup"><span data-stu-id="6de5d-151">Create a new derived hierarchy.</span></span>|[<span data-ttu-id="6de5d-152">Créer une hiérarchie dérivée &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6de5d-152">Create a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-derived-hierarchy-master-data-services.md)|
|<span data-ttu-id="6de5d-153">Masquer ou supprimer des niveaux dans une hiérarchie dérivée existante.</span><span class="sxs-lookup"><span data-stu-id="6de5d-153">Hide or delete levels in an existing derived hierarchy.</span></span>|[<span data-ttu-id="6de5d-154">Masquer ou supprimer des niveaux dans une hiérarchie dérivée &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6de5d-154">Hide or Delete Levels in a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/hide-or-delete-levels-in-a-derived-hierarchy-master-data-services.md)|
|<span data-ttu-id="6de5d-155">Modifier le nom d'une hiérarchie dérivée existante.</span><span class="sxs-lookup"><span data-stu-id="6de5d-155">Change the name of an existing derived hierarchy.</span></span>|[<span data-ttu-id="6de5d-156">Modifier le nom d’une hiérarchie dérivée &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6de5d-156">Change a Derived Hierarchy Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-a-derived-hierarchy-name-master-data-services.md)|
|<span data-ttu-id="6de5d-157">Supprimer une hiérarchie dérivée existante.</span><span class="sxs-lookup"><span data-stu-id="6de5d-157">Delete an existing derived hierarchy.</span></span>|[<span data-ttu-id="6de5d-158">Supprimer une hiérarchie dérivée &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6de5d-158">Delete a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-a-derived-hierarchy-master-data-services.md)|
|||

## <a name="related-content"></a><span data-ttu-id="6de5d-159">Contenu associé</span><span class="sxs-lookup"><span data-stu-id="6de5d-159">Related Content</span></span>

-   [<span data-ttu-id="6de5d-160">Attributs basés sur un domaine &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6de5d-160">Domain-Based Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/domain-based-attributes-master-data-services.md)

-   [<span data-ttu-id="6de5d-161">Hiérarchies explicites &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6de5d-161">Explicit Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)

-   [<span data-ttu-id="6de5d-162">Hiérarchies récursives &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6de5d-162">Recursive Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/recursive-hierarchies-master-data-services.md)

-   [<span data-ttu-id="6de5d-163">Hiérarchies dérivées avec un niveau supérieur composé d’une hiérarchie explicite &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6de5d-163">Derived Hierarchies with Explicit Caps &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)

-   [<span data-ttu-id="6de5d-164">Collections &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6de5d-164">Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/collections-master-data-services.md)

