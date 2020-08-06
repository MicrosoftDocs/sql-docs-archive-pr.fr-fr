---
title: Propriétés du workflow qui peuvent être définies à l’aide d’expressions | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SQL Server Integration Services packages, property expressions
- Integration Services packages, property expressions
- packages [Integration Services], properties
- SSIS packages, property expressions
- property expressions [Integration Services]
ms.assetid: cd0e171a-08be-45d6-81dc-ed94f37698b8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1763a531b1d91a60d2bb3775ae9fbe9942c6b7e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697040"
---
# <a name="data-flow-properties-that-can-be-set-by-using-expressions"></a><span data-ttu-id="a31e1-102">Propriétés du flux de données pouvant être définies à l’aide d’expressions</span><span class="sxs-lookup"><span data-stu-id="a31e1-102">Data Flow Properties that Can Be Set by Using Expressions</span></span>
  <span data-ttu-id="a31e1-103">Les valeurs de certaines propriétés d'objets de flux de données peuvent être spécifiées à l'aide d'expressions de propriété disponibles sur le conteneur de tâche de flux de données.</span><span class="sxs-lookup"><span data-stu-id="a31e1-103">The values of certain properties of data flow objects can be specified by using property expressions available on the Data Flow task container.</span></span>  
  
 <span data-ttu-id="a31e1-104">Pour plus d’informations sur l’utilisation d’expressions de propriété, consultez [Expressions de propriété dans des packages](expressions/use-property-expressions-in-packages.md).</span><span class="sxs-lookup"><span data-stu-id="a31e1-104">For information about using property expressions, see [Use Property Expressions in Packages](expressions/use-property-expressions-in-packages.md).</span></span>  
  
 <span data-ttu-id="a31e1-105">Vous pouvez utiliser des expressions de propriété pour personnaliser les configurations de chaque instance déployée d'un package.</span><span class="sxs-lookup"><span data-stu-id="a31e1-105">You can use property expressions to customize configurations for each deployed instance of a package.</span></span> <span data-ttu-id="a31e1-106">Vous pouvez également utiliser des expressions de propriété pour spécifier des contraintes d’exécution pour un package à l’aide de l’option **/set** avec l’utilitaire d’invite de commandes **dtexec** .</span><span class="sxs-lookup"><span data-stu-id="a31e1-106">You can also use property expressions to specify run-time constraints for a package by using the **/set** option with the **dtexec** command prompt utility.</span></span> <span data-ttu-id="a31e1-107">Par exemple, vous pouvez limiter le nombre maximal de threads (`MaximumThreads`) utilisés par la transformation de tri ou l'utilisation `MaxMemoryUsage` des transformations de regroupement probable et de recherche floue.</span><span class="sxs-lookup"><span data-stu-id="a31e1-107">For example, you can constrain the `MaximumThreads` used by the Sort transformation, or the `MaxMemoryUsage` of the Fuzzy Grouping and Fuzzy Lookup transformations.</span></span> <span data-ttu-id="a31e1-108">Si elles sont libres, ces transformations peuvent mettre en cache de grandes quantités de données en mémoire.</span><span class="sxs-lookup"><span data-stu-id="a31e1-108">If unconstrained, these transformations may cache large amounts of data in memory.</span></span>  
  
 <span data-ttu-id="a31e1-109">Pour spécifier une expression de propriété pour une des propriétés d’objets de flux de données répertoriées dans cette rubrique, affichez la fenêtre **Propriétés** pour la tâche de flux de données en la sélectionnant sur l’aire **Flux de contrôle** du concepteur ou en sélectionnant l’onglet **Flux de données** du concepteur sans sélectionner de composant ou de chemin individuel.</span><span class="sxs-lookup"><span data-stu-id="a31e1-109">To specify a property expression for one of the properties of data flow objects listed in this topic, display the **Properties** window for the Data Flow task by selecting the Data Flow task on the **Control Flow** surface of the designer, or by selecting the **Data Flow** tab of the designer without selecting any individual component or path.</span></span> <span data-ttu-id="a31e1-110">Sélectionnez la propriété **Expressions** , puis cliquez sur les points de suspension (...) pour afficher la boîte de dialogue de **l’Éditeur d’expressions de la propriété** .</span><span class="sxs-lookup"><span data-stu-id="a31e1-110">Select the **Expressions** property and click the ellipsis (...) to display the **Property Expressions Editor** dialog box.</span></span> <span data-ttu-id="a31e1-111">Déroulez la liste **Propriété** pour sélectionner une propriété, puis entrez une expression dans la zone de texte **Expression** ou cliquez sur les points de suspension (...) pour afficher la boîte de dialogue **Générateur d’expressions** .</span><span class="sxs-lookup"><span data-stu-id="a31e1-111">Drop down the **Property** list to select a property, then type an expression in the **Expression** text box, or click the ellipsis (...) to display the **Expression Builder** dialog box.</span></span>  
  
 <span data-ttu-id="a31e1-112">La liste **Propriété** affiche les propriétés disponibles uniquement pour les objets de flux de données que vous avez déjà placés sur l’aire **Flux de données** du concepteur.</span><span class="sxs-lookup"><span data-stu-id="a31e1-112">The **Property** list displays available properties for only those data flow objects that you have already placed on the **Data Flow** surface of the designer.</span></span> <span data-ttu-id="a31e1-113">Par conséquent, vous ne pouvez pas utiliser la liste **Propriété** pour consulter toutes les propriétés possibles des objets de flux de données qui prennent en charge les expressions de propriété.</span><span class="sxs-lookup"><span data-stu-id="a31e1-113">Therefore, you cannot use the **Property** list to view all the possible properties of data flow objects that support property expressions.</span></span> <span data-ttu-id="a31e1-114">Par exemple, si vous avez placé une source ADO .net sur l’aire du concepteur, la liste de **Propriétés** contient une entrée pour la `[ADO NET Source].[SqlCommand]` propriété.</span><span class="sxs-lookup"><span data-stu-id="a31e1-114">For example, if you have placed an ADO NET source on the designer surface, the **Property** list contains an entry for the `[ADO NET Source].[SqlCommand]` property.</span></span> <span data-ttu-id="a31e1-115">La liste affiche également de nombreuses propriétés de la tâche de flux de données elle-même.</span><span class="sxs-lookup"><span data-stu-id="a31e1-115">The list also displays many properties of the Data Flow task itself.</span></span>  
  
## <a name="properties-of-data-flow-objects-that-support-property-expressions"></a><span data-ttu-id="a31e1-116">Propriétés des objets de flux de données qui prennent en charge les expressions de propriété</span><span class="sxs-lookup"><span data-stu-id="a31e1-116">Properties of Data Flow Objects That Support Property Expressions</span></span>  
 <span data-ttu-id="a31e1-117">Les valeurs des propriétés de la liste suivante peuvent être spécifiées à l'aide d'expressions de propriété.</span><span class="sxs-lookup"><span data-stu-id="a31e1-117">The values of the properties in the following list can be specified by using property expressions.</span></span>  
  
### <a name="data-flow-sources"></a><span data-ttu-id="a31e1-118">Sources de flux de données</span><span class="sxs-lookup"><span data-stu-id="a31e1-118">Data Flow Sources</span></span>  
  
|<span data-ttu-id="a31e1-119">Objet de flux de données</span><span class="sxs-lookup"><span data-stu-id="a31e1-119">Data Flow object</span></span>|<span data-ttu-id="a31e1-120">Propriété</span><span class="sxs-lookup"><span data-stu-id="a31e1-120">Property</span></span>|  
|----------------------|--------------|  
|<span data-ttu-id="a31e1-121">Source ADO NET</span><span class="sxs-lookup"><span data-stu-id="a31e1-121">ADO NET source</span></span>|<span data-ttu-id="a31e1-122">Propriété TableOrViewName</span><span class="sxs-lookup"><span data-stu-id="a31e1-122">TableOrViewName property</span></span><br /><br /> <span data-ttu-id="a31e1-123">Propriété SQLCommand</span><span class="sxs-lookup"><span data-stu-id="a31e1-123">SqlCommand property</span></span>|  
|<span data-ttu-id="a31e1-124">Source XML</span><span class="sxs-lookup"><span data-stu-id="a31e1-124">XML source</span></span>|<span data-ttu-id="a31e1-125">Propriété XMLData</span><span class="sxs-lookup"><span data-stu-id="a31e1-125">XMLData property</span></span><br /><br /> <span data-ttu-id="a31e1-126">Propriété XMLSchemaDefinition</span><span class="sxs-lookup"><span data-stu-id="a31e1-126">XMLSchemaDefinition property</span></span>|  
  
### <a name="data-flow-transformations"></a><span data-ttu-id="a31e1-127">Transformations du flux de données</span><span class="sxs-lookup"><span data-stu-id="a31e1-127">Data Flow Transformations</span></span>  
 <span data-ttu-id="a31e1-128">Pour plus d’informations sur ces propriétés personnalisées, consultez [Propriétés personnalisées des transformations](data-flow/transformations/transformation-custom-properties.md).</span><span class="sxs-lookup"><span data-stu-id="a31e1-128">For more information about these custom properties, see [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md).</span></span>  
  
|<span data-ttu-id="a31e1-129">Objet de flux de données</span><span class="sxs-lookup"><span data-stu-id="a31e1-129">Data Flow object</span></span>|<span data-ttu-id="a31e1-130">Propriété</span><span class="sxs-lookup"><span data-stu-id="a31e1-130">Property</span></span>|  
|----------------------|--------------|  
|<span data-ttu-id="a31e1-131">transformation de fractionnement conditionnel</span><span class="sxs-lookup"><span data-stu-id="a31e1-131">Conditional Split transformation</span></span>|<span data-ttu-id="a31e1-132">Propriété FriendlyExpression</span><span class="sxs-lookup"><span data-stu-id="a31e1-132">FriendlyExpression property</span></span>|  
|<span data-ttu-id="a31e1-133">Transformation de colonnes dérivées</span><span class="sxs-lookup"><span data-stu-id="a31e1-133">Derived Column transformation</span></span>|<span data-ttu-id="a31e1-134">Propriété FriendlyExpression</span><span class="sxs-lookup"><span data-stu-id="a31e1-134">FriendlyExpression property</span></span>|  
|<span data-ttu-id="a31e1-135">Transformation de regroupement approximatif</span><span class="sxs-lookup"><span data-stu-id="a31e1-135">Fuzzy Grouping transformation</span></span>|<span data-ttu-id="a31e1-136">Propriété MaxMemoryUsage</span><span class="sxs-lookup"><span data-stu-id="a31e1-136">MaxMemoryUsage property</span></span>|  
|<span data-ttu-id="a31e1-137">transformation de recherche floue</span><span class="sxs-lookup"><span data-stu-id="a31e1-137">Fuzzy Lookup transformation</span></span>|<span data-ttu-id="a31e1-138">Propriété MaxMemoryUsage</span><span class="sxs-lookup"><span data-stu-id="a31e1-138">MaxMemoryUsage property</span></span>|  
|<span data-ttu-id="a31e1-139">Transformation de recherche</span><span class="sxs-lookup"><span data-stu-id="a31e1-139">Lookup transformation</span></span>|<span data-ttu-id="a31e1-140">Propriété SQLCommand</span><span class="sxs-lookup"><span data-stu-id="a31e1-140">SqlCommand property</span></span><br /><br /> <span data-ttu-id="a31e1-141">Propriété SqlCommandParam</span><span class="sxs-lookup"><span data-stu-id="a31e1-141">SqlCommandParam property</span></span>|  
|<span data-ttu-id="a31e1-142">transformation de commande OLE DB</span><span class="sxs-lookup"><span data-stu-id="a31e1-142">OLE DB Command transformation</span></span>|<span data-ttu-id="a31e1-143">Propriété SQLCommand</span><span class="sxs-lookup"><span data-stu-id="a31e1-143">SqlCommand property</span></span>|  
|<span data-ttu-id="a31e1-144">transformation de l'échantillonnage du pourcentage</span><span class="sxs-lookup"><span data-stu-id="a31e1-144">Percentage Sampling transformation</span></span>|<span data-ttu-id="a31e1-145">Propriété SamplingValue</span><span class="sxs-lookup"><span data-stu-id="a31e1-145">SamplingValue property</span></span>|  
|<span data-ttu-id="a31e1-146">transformation de tableau croisé dynamique</span><span class="sxs-lookup"><span data-stu-id="a31e1-146">Pivot transformation</span></span>|<span data-ttu-id="a31e1-147">Propriété PivotKeyValue</span><span class="sxs-lookup"><span data-stu-id="a31e1-147">PivotKeyValue property</span></span>|  
|<span data-ttu-id="a31e1-148">transformation d'échantillonnage de lignes</span><span class="sxs-lookup"><span data-stu-id="a31e1-148">Row Sampling transformation</span></span>|<span data-ttu-id="a31e1-149">Propriété SamplingValue</span><span class="sxs-lookup"><span data-stu-id="a31e1-149">SamplingValue property</span></span>|  
|<span data-ttu-id="a31e1-150">transformation de tri</span><span class="sxs-lookup"><span data-stu-id="a31e1-150">Sort transformation</span></span>|<span data-ttu-id="a31e1-151">Propriété MaximumThreads</span><span class="sxs-lookup"><span data-stu-id="a31e1-151">MaximumThreads property</span></span>|  
|<span data-ttu-id="a31e1-152">Transformation Unpivot</span><span class="sxs-lookup"><span data-stu-id="a31e1-152">Unpivot transformation</span></span>|<span data-ttu-id="a31e1-153">Propriété PivotKeyValue</span><span class="sxs-lookup"><span data-stu-id="a31e1-153">PivotKeyValue property</span></span>|  
  
### <a name="data-flow-destinations"></a><span data-ttu-id="a31e1-154">Destinations du flux de données</span><span class="sxs-lookup"><span data-stu-id="a31e1-154">Data Flow Destinations</span></span>  
  
|<span data-ttu-id="a31e1-155">Objet de flux de données</span><span class="sxs-lookup"><span data-stu-id="a31e1-155">Data Flow object</span></span>|<span data-ttu-id="a31e1-156">Propriété</span><span class="sxs-lookup"><span data-stu-id="a31e1-156">Property</span></span>|  
|----------------------|--------------|  
|<span data-ttu-id="a31e1-157">Destination ADO NET</span><span class="sxs-lookup"><span data-stu-id="a31e1-157">ADO NET Destination</span></span>|<span data-ttu-id="a31e1-158">Propriété TableOrViewName</span><span class="sxs-lookup"><span data-stu-id="a31e1-158">TableOrViewName property</span></span><br /><br /> <span data-ttu-id="a31e1-159">Propriété BatchSize</span><span class="sxs-lookup"><span data-stu-id="a31e1-159">BatchSize property</span></span><br /><br /> <span data-ttu-id="a31e1-160">Propriété CommandTimeout</span><span class="sxs-lookup"><span data-stu-id="a31e1-160">CommandTimeout property</span></span>|  
|<span data-ttu-id="a31e1-161">Destination de fichier plat</span><span class="sxs-lookup"><span data-stu-id="a31e1-161">Flat File destination</span></span>|<span data-ttu-id="a31e1-162">Propriété Header</span><span class="sxs-lookup"><span data-stu-id="a31e1-162">Header property</span></span>|  
|<span data-ttu-id="a31e1-163">Destination [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact</span><span class="sxs-lookup"><span data-stu-id="a31e1-163">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact destination</span></span>|<span data-ttu-id="a31e1-164">Propriété TableName</span><span class="sxs-lookup"><span data-stu-id="a31e1-164">TableName property</span></span>|  
|<span data-ttu-id="a31e1-165">Destination [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a31e1-165">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] destination</span></span>|<span data-ttu-id="a31e1-166">Propriété BulkInsertTableName</span><span class="sxs-lookup"><span data-stu-id="a31e1-166">BulkInsertTableName property</span></span><br /><br /> <span data-ttu-id="a31e1-167">Propriété BulkInsertFirstRow</span><span class="sxs-lookup"><span data-stu-id="a31e1-167">BulkInsertFirstRow property</span></span><br /><br /> <span data-ttu-id="a31e1-168">Propriété BulkInsertLastRow</span><span class="sxs-lookup"><span data-stu-id="a31e1-168">BulkInsertLastRow property</span></span><br /><br /> <span data-ttu-id="a31e1-169">Propriété BulkInsertOrder</span><span class="sxs-lookup"><span data-stu-id="a31e1-169">BulkInsertOrder property</span></span><br /><br /> <span data-ttu-id="a31e1-170">Propriété Timeout</span><span class="sxs-lookup"><span data-stu-id="a31e1-170">Timeout property</span></span>|  
  
## <a name="related-tasks"></a><span data-ttu-id="a31e1-171">Tâches associées</span><span class="sxs-lookup"><span data-stu-id="a31e1-171">Related Tasks</span></span>  
  
-   [<span data-ttu-id="a31e1-172">Ajouter ou modifier une expression de propriété</span><span class="sxs-lookup"><span data-stu-id="a31e1-172">Add or Change a Property Expression</span></span>](expressions/add-or-change-a-property-expression.md)  
  
## <a name="related-content"></a><span data-ttu-id="a31e1-173">Contenu associé</span><span class="sxs-lookup"><span data-stu-id="a31e1-173">Related Content</span></span>  
 <span data-ttu-id="a31e1-174">Article technique, [SSIS Expression Cheat Sheet](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet), sur pragmaticworks.com</span><span class="sxs-lookup"><span data-stu-id="a31e1-174">Technical article, [SSIS Expression Cheat Sheet](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet), on pragmaticworks.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a31e1-175">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a31e1-175">See Also</span></span>  
 <span data-ttu-id="a31e1-176">[Utiliser des expressions de propriété dans des packages](expressions/use-property-expressions-in-packages.md) </span><span class="sxs-lookup"><span data-stu-id="a31e1-176">[Use Property Expressions in Packages](expressions/use-property-expressions-in-packages.md) </span></span>  
 <span data-ttu-id="a31e1-177">[Propriétés communes](../../2014/integration-services/common-properties.md) </span><span class="sxs-lookup"><span data-stu-id="a31e1-177">[Common Properties](../../2014/integration-services/common-properties.md) </span></span>  
 <span data-ttu-id="a31e1-178">[Transformation, propriétés personnalisées](data-flow/transformations/transformation-custom-properties.md) </span><span class="sxs-lookup"><span data-stu-id="a31e1-178">[Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md) </span></span>  
 [<span data-ttu-id="a31e1-179">Propriétés du chemin</span><span class="sxs-lookup"><span data-stu-id="a31e1-179">Path Properties</span></span>](../../2014/integration-services/path-properties.md)  
  
  