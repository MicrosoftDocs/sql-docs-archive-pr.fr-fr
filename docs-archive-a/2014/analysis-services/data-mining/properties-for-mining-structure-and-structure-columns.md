---
title: Propriétés de la structure d’exploration de données et des colonnes de structure | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], column properties
- data mining [Analysis Services], properties
- columns [data mining], properties
- properties [data mining]
ms.assetid: ce90f684-bb8c-4eca-b9e6-000794dbee16
author: minewiskan
ms.author: owend
ms.openlocfilehash: d83052c91b62f2c8873a80084b02200f276b4aac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703424"
---
# <a name="properties-for-mining-structure-and-structure-columns"></a><span data-ttu-id="b638f-102">Propriétés des colonnes de structure et des structure d'exploration de données</span><span class="sxs-lookup"><span data-stu-id="b638f-102">Properties for Mining Structure and Structure Columns</span></span>
  <span data-ttu-id="b638f-103">Vous pouvez définir ou modifier les propriétés pour une structure d’exploration de données ainsi que pour ses colonnes et colonnes imbriquées associées en utilisant l’onglet **Structure d’exploration de données** du Concepteur d’exploration de données.</span><span class="sxs-lookup"><span data-stu-id="b638f-103">You can set or change the properties for a mining structure and for its associated columns and nested tables by using the **Mining Structure** tab of Data Mining Designer.</span></span> <span data-ttu-id="b638f-104">Les propriétés que vous définissez sous cet onglet sont propagées à chaque modèle d'exploration de données associé à la structure.</span><span class="sxs-lookup"><span data-stu-id="b638f-104">Properties that you set in this tab are propagated to each mining model that is associated with the structure.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b638f-105">Si vous modifiez la valeur d'une propriété dans la structure d'exploration de données, y compris des métadonnées telles qu'un nom ou une description, la structure d'exploration de données et ses modèles doivent être retraités pour que vous puissiez afficher ou interroger le modèle.</span><span class="sxs-lookup"><span data-stu-id="b638f-105">If you change the value of any property in the mining structure, even metadata such as a name or description, the mining structure and its models must be reprocessed before you can view or query the model.</span></span>  
  
## <a name="properties-of-mining-structures-and-mining-structure-columns"></a><span data-ttu-id="b638f-106">Propriétés des structures d'exploration de données et des colonnes de structure d'exploration de données</span><span class="sxs-lookup"><span data-stu-id="b638f-106">Properties of Mining Structures and Mining Structure Columns</span></span>  
 <span data-ttu-id="b638f-107">Le tableau suivant décrit les propriétés de la structure d’exploration de données et les colonnes de structure d’exploration de données qui sont spécifiques à l’exploration de données, et que vous pouvez afficher ou configurer sous l’onglet **structure d’exploration** de données. Pour afficher ou configurer ces propriétés, cliquez avec le bouton droit sur un élément dans l’arborescence, puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="b638f-107">The following table describes the properties for the mining structure and the mining structure columns that are specific to data mining, and that you can view or configure in the **Mining Structure** tab. To view or configure these properties, right-click an element in the tree view, and then click **Properties**.</span></span>  
  
-   <span data-ttu-id="b638f-108">Cliquez sur l'en-tête de la structure d'exploration de données pour afficher ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="b638f-108">To view the properties of the structure, click the mining structure heading.</span></span>  
  
-   <span data-ttu-id="b638f-109">Pour afficher les propriétés d'une colonne ou d'une table imbriquée, cliquez sur le nom de la colonne.</span><span class="sxs-lookup"><span data-stu-id="b638f-109">To view the properties of a column or a nested table, click the column name.</span></span>  
  
### <a name="properties-of-the-mining-structure"></a><span data-ttu-id="b638f-110">Propriétés de la structure d'exploration de données</span><span class="sxs-lookup"><span data-stu-id="b638f-110">Properties of the Mining Structure</span></span>  
  
|<span data-ttu-id="b638f-111">Propriété</span><span class="sxs-lookup"><span data-stu-id="b638f-111">Property</span></span>|<span data-ttu-id="b638f-112">Description</span><span class="sxs-lookup"><span data-stu-id="b638f-112">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="b638f-113">**CacheMode**</span><span class="sxs-lookup"><span data-stu-id="b638f-113">**CacheMode**</span></span>|<span data-ttu-id="b638f-114">Spécifie si les cas utilisés dans le cadre de l'apprentissage doivent être mis en cache ou supprimés à la fin de la formation.</span><span class="sxs-lookup"><span data-stu-id="b638f-114">Specifies whether cases used in training should be cached or discarded after training is completed.</span></span><br /><br /> <span data-ttu-id="b638f-115">Remarque : cette propriété doit avoir la valeur `KeepTrainingCases` pour activer l’extraction et exclusion.</span><span class="sxs-lookup"><span data-stu-id="b638f-115">Note: This property must be set to `KeepTrainingCases` to enable drillthrough and holdout.</span></span>|  
|<span data-ttu-id="b638f-116">**Classement**</span><span class="sxs-lookup"><span data-stu-id="b638f-116">**Collation**</span></span>|<span data-ttu-id="b638f-117">Spécifie le classement par défaut de la colonne.</span><span class="sxs-lookup"><span data-stu-id="b638f-117">Specifies the default collation for the column.</span></span> <span data-ttu-id="b638f-118">Si aucun n'est spécifié, le classement du serveur est utilisé.</span><span class="sxs-lookup"><span data-stu-id="b638f-118">If a collation is not specified, the collation of the server is used.</span></span>|  
|<span data-ttu-id="b638f-119">**Description**</span><span class="sxs-lookup"><span data-stu-id="b638f-119">**Description**</span></span>|<span data-ttu-id="b638f-120">Décrit la structure d'exploration de données.</span><span class="sxs-lookup"><span data-stu-id="b638f-120">Describes the mining structure.</span></span> <span data-ttu-id="b638f-121">Il est recommandé que la description indique la fonction et la composition des données dans la structure.</span><span class="sxs-lookup"><span data-stu-id="b638f-121">As a best practice, the description should state the purpose and composition of the data in the structure.</span></span>|  
|<span data-ttu-id="b638f-122">**ErrorConfiguration (par défaut)**</span><span class="sxs-lookup"><span data-stu-id="b638f-122">**ErrorConfiguration (default)**</span></span>|<span data-ttu-id="b638f-123">Spécifie les options relatives à la gestion spéciale des erreurs, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="b638f-123">Specifies options for special handling of errors, if any.</span></span>|  
|<span data-ttu-id="b638f-124">**HoldoutMaxCases**</span><span class="sxs-lookup"><span data-stu-id="b638f-124">**HoldoutMaxCases**</span></span>|<span data-ttu-id="b638f-125">Spécifie le nombre maximal de cas de structure qui peuvent être réservés en tant que jeu de données de test.</span><span class="sxs-lookup"><span data-stu-id="b638f-125">Specifies the maximum number of structure cases that can be reserved as a test data set.</span></span>  <span data-ttu-id="b638f-126">Si des valeurs sont spécifiées pour **HoldoutMaxCases** et **HoldoutPercent**, les conditions sont combinées.</span><span class="sxs-lookup"><span data-stu-id="b638f-126">If values are specified for both **HoldoutMaxCases** and **HoldoutPercent**, the conditions are combined.</span></span><br /><br /> <span data-ttu-id="b638f-127">Remarque : pour définir cette propriété, <xref:Microsoft.AnalysisServices.MiningStructure.CacheMode%2A> doit avoir la valeur `KeepTrainingCases` .</span><span class="sxs-lookup"><span data-stu-id="b638f-127">Note: To set this property, <xref:Microsoft.AnalysisServices.MiningStructure.CacheMode%2A> must be set to `KeepTrainingCases`.</span></span>|  
|<span data-ttu-id="b638f-128">**HoldoutPercent**</span><span class="sxs-lookup"><span data-stu-id="b638f-128">**HoldoutPercent**</span></span>|<span data-ttu-id="b638f-129">Spécifie le pourcentage de cas de structure à réserver comme jeu de données de test.</span><span class="sxs-lookup"><span data-stu-id="b638f-129">Specifies the percentage of the structure cases to reserve as a test data set.</span></span> <span data-ttu-id="b638f-130">Si des valeurs sont spécifiées pour **HoldoutMaxCases** et **HoldoutPercent**, les conditions sont combinées.</span><span class="sxs-lookup"><span data-stu-id="b638f-130">If values are specified for both **HoldoutMaxCases** and **HoldoutPercent**, the conditions are combined.</span></span><br /><br /> <span data-ttu-id="b638f-131">Remarque : pour définir cette propriété, <xref:Microsoft.AnalysisServices.MiningStructure.CacheMode%2A> doit avoir la valeur `KeepTrainingCases` .</span><span class="sxs-lookup"><span data-stu-id="b638f-131">Note: To set this property, <xref:Microsoft.AnalysisServices.MiningStructure.CacheMode%2A> must be set to `KeepTrainingCases`.</span></span>|  
|<span data-ttu-id="b638f-132">**HoldoutSeed**</span><span class="sxs-lookup"><span data-stu-id="b638f-132">**HoldoutSeed**</span></span>|<span data-ttu-id="b638f-133">Spécifie une valeur de départ pour initialiser le partitionnement du jeu de test d'exclusion, afin de garantir que le jeu de données de test pourra être recréé.</span><span class="sxs-lookup"><span data-stu-id="b638f-133">Specifies a seed to initialize partitioning of the holdout test set, to ensure that the test data set can be re-created.</span></span><br /><br /> <span data-ttu-id="b638f-134">Remarque : pour définir cette propriété, <xref:Microsoft.AnalysisServices.MiningStructure.CacheMode%2A> doit avoir la valeur `KeepTrainingCases` .</span><span class="sxs-lookup"><span data-stu-id="b638f-134">Note: To set this property, <xref:Microsoft.AnalysisServices.MiningStructure.CacheMode%2A> must be set to `KeepTrainingCases`.</span></span>|  
|<span data-ttu-id="b638f-135">**Identifiant**</span><span class="sxs-lookup"><span data-stu-id="b638f-135">**ID**</span></span>|<span data-ttu-id="b638f-136">Affiche l'identificateur unique de la structure d'exploration de données.</span><span class="sxs-lookup"><span data-stu-id="b638f-136">Displays the unique identifier of the mining structure.</span></span><br /><br /> <span data-ttu-id="b638f-137">Le nom que vous avez attribué à la structure d'exploration de données lorsque vous l'avez créée est utilisé comme ID.</span><span class="sxs-lookup"><span data-stu-id="b638f-137">The name that you assigned to the mining structure when you created the structure is used as the ID.</span></span> <span data-ttu-id="b638f-138">Si vous modifiez ultérieurement le nom en tapant une nouvelle valeur pour la propriété `Name`, le nouveau nom est uniquement utilisé comme alias ; l'ID ne change pas.</span><span class="sxs-lookup"><span data-stu-id="b638f-138">If you later change the name by typing a new value for the `Name` property, the new name is used as an alias only; the ID does not change.</span></span>|  
|<span data-ttu-id="b638f-139">**Langage**</span><span class="sxs-lookup"><span data-stu-id="b638f-139">**Language**</span></span>|<span data-ttu-id="b638f-140">Spécifie la langue des légendes dans la structure d'exploration de données.</span><span class="sxs-lookup"><span data-stu-id="b638f-140">Specifies the language for the captions in the mining structure.</span></span>|  
|`Name`|<span data-ttu-id="b638f-141">Spécifie le nom ou l'alias de la structure d'exploration de données.</span><span class="sxs-lookup"><span data-stu-id="b638f-141">Specifies the name or alias of the mining structure.</span></span><br /><br /> <span data-ttu-id="b638f-142">Si vous modifiez la valeur de la propriété Name, le nouveau nom est utilisé comme légende ou alias uniquement ; l'identificateur de la structure d'exploration de données ne change pas.</span><span class="sxs-lookup"><span data-stu-id="b638f-142">If you change the value for the Name property, the new name is used as a caption or alias only; the identifier for the mining structure does not change.</span></span>|  
|<span data-ttu-id="b638f-143">**Source**</span><span class="sxs-lookup"><span data-stu-id="b638f-143">**Source**</span></span>|<span data-ttu-id="b638f-144">Affiche le nom et le type de la source de données.</span><span class="sxs-lookup"><span data-stu-id="b638f-144">Displays the name of the data source, and the type of data source.</span></span>|  
  
### <a name="properties-of-the-mining-structure-columns"></a><span data-ttu-id="b638f-145">Oropriétés des colonnes de la structure d'exploration de données</span><span class="sxs-lookup"><span data-stu-id="b638f-145">Properties of the Mining Structure Columns</span></span>  
  
|<span data-ttu-id="b638f-146">Propriété</span><span class="sxs-lookup"><span data-stu-id="b638f-146">Property</span></span>|<span data-ttu-id="b638f-147">Description</span><span class="sxs-lookup"><span data-stu-id="b638f-147">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="b638f-148">**ClassifiedColumns**</span><span class="sxs-lookup"><span data-stu-id="b638f-148">**ClassifiedColumns**</span></span>|<span data-ttu-id="b638f-149">Identifie la colonne qu'une colonne classifiée décrit.</span><span class="sxs-lookup"><span data-stu-id="b638f-149">Identifies the column that a classified column describes.</span></span>|  
|<span data-ttu-id="b638f-150">**Contenu**</span><span class="sxs-lookup"><span data-stu-id="b638f-150">**Content**</span></span>|<span data-ttu-id="b638f-151">Type de contenu de la colonne.</span><span class="sxs-lookup"><span data-stu-id="b638f-151">The content type of the column.</span></span>|  
|<span data-ttu-id="b638f-152">**Description**</span><span class="sxs-lookup"><span data-stu-id="b638f-152">**Description**</span></span>|<span data-ttu-id="b638f-153">Décrit la colonne.</span><span class="sxs-lookup"><span data-stu-id="b638f-153">Describes the column.</span></span> <span data-ttu-id="b638f-154">Il est recommandé que la description de la colonne fournisse des informations sur la manière dont les données dans la colonne ont été dérivées ou modifiées pour l'exploration de données.</span><span class="sxs-lookup"><span data-stu-id="b638f-154">As a best practice, the description of the column should provide information about how the data in the column has been derived or altered for data mining.</span></span>|  
|<span data-ttu-id="b638f-155">**DiscretizationBucketCount**</span><span class="sxs-lookup"><span data-stu-id="b638f-155">**DiscretizationBucketCount**</span></span>|<span data-ttu-id="b638f-156">Affiche le nombre de compartiments dans la colonne discrétisée.</span><span class="sxs-lookup"><span data-stu-id="b638f-156">Displays the number of buckets in the discretized column.</span></span><br /><br /> <span data-ttu-id="b638f-157">Activé uniquement si le type de contenu a la valeur `Discretized`.</span><span class="sxs-lookup"><span data-stu-id="b638f-157">Enabled only if the content type is set to `Discretized`.</span></span><br /><br /> <span data-ttu-id="b638f-158">Cette propriété est en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="b638f-158">This property is read-only.</span></span>|  
|<span data-ttu-id="b638f-159">**DiscretizationMethod**</span><span class="sxs-lookup"><span data-stu-id="b638f-159">**DiscretizationMethod**</span></span>|<span data-ttu-id="b638f-160">Affiche la méthode utilisée pour discrétiser la colonne.</span><span class="sxs-lookup"><span data-stu-id="b638f-160">Displays the method that was used to discretize the column.</span></span><br /><br /> <span data-ttu-id="b638f-161">Activé uniquement si le type de contenu a la valeur `Discretized`.</span><span class="sxs-lookup"><span data-stu-id="b638f-161">Enabled only if the content type is set to `Discretized`.</span></span><br /><br /> <span data-ttu-id="b638f-162">Cette propriété est en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="b638f-162">This property is read-only.</span></span>|  
|<span data-ttu-id="b638f-163">**Distribution**</span><span class="sxs-lookup"><span data-stu-id="b638f-163">**Distribution**</span></span>|<span data-ttu-id="b638f-164">Spécifie la distribution de contenu dans la colonne.</span><span class="sxs-lookup"><span data-stu-id="b638f-164">Specifies the distribution of content in the column.</span></span>|  
|<span data-ttu-id="b638f-165">**Identifiant**</span><span class="sxs-lookup"><span data-stu-id="b638f-165">**ID**</span></span>|<span data-ttu-id="b638f-166">Affiche l'identificateur de la colonne.</span><span class="sxs-lookup"><span data-stu-id="b638f-166">Displays the identifier of the column.</span></span><br /><br /> <span data-ttu-id="b638f-167">Modifier la valeur de la propriété Name de la colonne n'affecte pas la valeur de la propriété ID.</span><span class="sxs-lookup"><span data-stu-id="b638f-167">If you change the value of the Name property of the column, it does not affect the value of the ID property.</span></span>|  
|<span data-ttu-id="b638f-168">**IsKey**</span><span class="sxs-lookup"><span data-stu-id="b638f-168">**IsKey**</span></span>|<span data-ttu-id="b638f-169">Indique si la colonne est une colonne clé.</span><span class="sxs-lookup"><span data-stu-id="b638f-169">Indicates whether the column is a key column.</span></span>|  
|<span data-ttu-id="b638f-170">**KeyColumns**</span><span class="sxs-lookup"><span data-stu-id="b638f-170">**KeyColumns**</span></span>|<span data-ttu-id="b638f-171">Contient la définition d'une colonne qui représente la clé ou une partie de la clé d'un attribut.</span><span class="sxs-lookup"><span data-stu-id="b638f-171">Contains the definition of a column that is the key or is part of the key for an attribute.</span></span>|  
|<span data-ttu-id="b638f-172">**ModelingFlags**</span><span class="sxs-lookup"><span data-stu-id="b638f-172">**ModelingFlags**</span></span>|<span data-ttu-id="b638f-173">Spécifie des paramètres supplémentaires rendus disponibles par l'algorithme.</span><span class="sxs-lookup"><span data-stu-id="b638f-173">Sets additional parameters that are made available by the algorithm.</span></span>|  
|`Name`|<span data-ttu-id="b638f-174">Nom de la colonne.</span><span class="sxs-lookup"><span data-stu-id="b638f-174">The name of the column.</span></span>|  
|<span data-ttu-id="b638f-175">**NameColumn**</span><span class="sxs-lookup"><span data-stu-id="b638f-175">**NameColumn**</span></span>|<span data-ttu-id="b638f-176">Identifie la colonne qui fournit le nom de l'élément parent.</span><span class="sxs-lookup"><span data-stu-id="b638f-176">Identifies the column that provides the name of the parent element.</span></span>|  
|<span data-ttu-id="b638f-177">**Source**</span><span class="sxs-lookup"><span data-stu-id="b638f-177">**Source**</span></span>|<span data-ttu-id="b638f-178">Affiche la source de la colonne.</span><span class="sxs-lookup"><span data-stu-id="b638f-178">Displays the source of the column.</span></span><br /><br /> <span data-ttu-id="b638f-179">Pour les sources de données relationnelles, la valeur est toujours **(aucun)**.</span><span class="sxs-lookup"><span data-stu-id="b638f-179">For relational data sources, the value is always **(none)**.</span></span><br /><br /> <span data-ttu-id="b638f-180">Pour les structures basées sur un cube OLAP, la valeur est l'instruction MDX qui définit la coupe utilisée comme source pour la table imbriquée.</span><span class="sxs-lookup"><span data-stu-id="b638f-180">For structures based on an OLAP cube, the value is the MDX statement that defines the slice used as the source for the nested table.</span></span>|  
|<span data-ttu-id="b638f-181">**SourceMeasureGroup**</span><span class="sxs-lookup"><span data-stu-id="b638f-181">**SourceMeasureGroup**</span></span>|<span data-ttu-id="b638f-182">Affiche la source du groupe de mesures.</span><span class="sxs-lookup"><span data-stu-id="b638f-182">Displays the source of the measure group.</span></span><br /><br /> <span data-ttu-id="b638f-183">Pour les sources de données relationnelles, la valeur est toujours **(aucun)**.</span><span class="sxs-lookup"><span data-stu-id="b638f-183">For relational data sources, the value is always **(none)**.</span></span><br /><br /> <span data-ttu-id="b638f-184">Pour les structures basées sur un cube OLAP, la valeur est l'instruction MDX qui définit la coupe utilisée comme source pour la table imbriquée.</span><span class="sxs-lookup"><span data-stu-id="b638f-184">For structures based on an OLAP cube, the value is the MDX statement that defines the slice used as the source for the nested table.</span></span>|  
|<span data-ttu-id="b638f-185">**Type**</span><span class="sxs-lookup"><span data-stu-id="b638f-185">**Type**</span></span>|<span data-ttu-id="b638f-186">Type de données pour le contenu de la colonne.</span><span class="sxs-lookup"><span data-stu-id="b638f-186">The data type for the content in the column.</span></span>|  
  
 <span data-ttu-id="b638f-187">Pour plus d’informations sur la définition ou la modification des propriétés, consultez [Tâches de la structure d’exploration de données et procédures](mining-structure-tasks-and-how-tos.md).</span><span class="sxs-lookup"><span data-stu-id="b638f-187">For more information about setting or changing properties, see [Mining Structure Tasks and How-tos](mining-structure-tasks-and-how-tos.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b638f-188">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b638f-188">See Also</span></span>  
 <span data-ttu-id="b638f-189">[Créer une structure d’exploration de données relationnelle](create-a-relational-mining-structure.md) </span><span class="sxs-lookup"><span data-stu-id="b638f-189">[Create a Relational Mining Structure](create-a-relational-mining-structure.md) </span></span>  
 [<span data-ttu-id="b638f-190">Colonnes de structure d'exploration de données</span><span class="sxs-lookup"><span data-stu-id="b638f-190">Mining Structure Columns</span></span>](mining-structure-columns.md)  
  
  