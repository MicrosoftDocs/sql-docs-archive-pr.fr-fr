---
title: Index, élément (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Index element (DTA)
ms.assetid: 447d3964-b387-40f6-9189-71386774c29e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 110dcd8ef5f554bdf1c59ab9a15984ec8ca97c65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703632"
---
# <a name="index-element-dta"></a><span data-ttu-id="7617a-102">Index, élément (Assistant Paramétrage de base de données)</span><span class="sxs-lookup"><span data-stu-id="7617a-102">Index Element (DTA)</span></span>
  <span data-ttu-id="7617a-103">Contient les informations sur un index que vous souhaitez créer ou supprimer pour une configuration spécifiée par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7617a-103">Contains information about an index that you want to create or drop for a user-specified configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7617a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7617a-104">Syntax</span></span>  
  
```  
  
<Recommendation>  
  <Create>  
    <Index [Clustered | Unique | Online | IndexSizeInMB | NumberOfRows             | QUOTED_IDENTIFIER | ARITHABORT | CONCAT_NULL_YIELDS_NULL             | ANSI_NULLS | ANSI_PADDING | ANSI_WARNINGS  
            | NUMERIC_ROUNDABORT]  
     ...code removed here...  
    </Index>  
```  
  
## <a name="element-attributes"></a><span data-ttu-id="7617a-105">Attributs des éléments</span><span class="sxs-lookup"><span data-stu-id="7617a-105">Element Attributes</span></span>  
  
|<span data-ttu-id="7617a-106">Attribut d'index</span><span class="sxs-lookup"><span data-stu-id="7617a-106">Index attribute</span></span>|<span data-ttu-id="7617a-107">Type de données</span><span class="sxs-lookup"><span data-stu-id="7617a-107">Data type</span></span>|<span data-ttu-id="7617a-108">Description</span><span class="sxs-lookup"><span data-stu-id="7617a-108">Description</span></span>|  
|---------------------|---------------|-----------------|  
|`Clustered`|`boolean`|<span data-ttu-id="7617a-109">facultatif.</span><span class="sxs-lookup"><span data-stu-id="7617a-109">Optional.</span></span> <span data-ttu-id="7617a-110">Spécifie un index cluster.</span><span class="sxs-lookup"><span data-stu-id="7617a-110">Specifies a clustered index.</span></span> <span data-ttu-id="7617a-111">Défini sur « true » ou « false », par exemple :</span><span class="sxs-lookup"><span data-stu-id="7617a-111">Set to either "true" or "false", for example:</span></span><br /><br /> `<Index Clustered="true">`<br /><br /> <span data-ttu-id="7617a-112">Par défaut, cet attribut est défini sur « false ».</span><span class="sxs-lookup"><span data-stu-id="7617a-112">By default, this attribute is set to "false".</span></span>|  
|`Unique`|`boolean`|<span data-ttu-id="7617a-113">facultatif.</span><span class="sxs-lookup"><span data-stu-id="7617a-113">Optional.</span></span> <span data-ttu-id="7617a-114">Spécifie un index unique</span><span class="sxs-lookup"><span data-stu-id="7617a-114">Specifies a unique index.</span></span> <span data-ttu-id="7617a-115">Défini sur « true » ou « false », par exemple :</span><span class="sxs-lookup"><span data-stu-id="7617a-115">Set to either "true" or "false", for example:</span></span><br /><br /> `<Index Unique="true">`<br /><br /> <span data-ttu-id="7617a-116">Par défaut, cet attribut est défini sur « false ».</span><span class="sxs-lookup"><span data-stu-id="7617a-116">By default, this attribute is set to "false".</span></span>|  
|`Online`|`boolean`|<span data-ttu-id="7617a-117">facultatif.</span><span class="sxs-lookup"><span data-stu-id="7617a-117">Optional.</span></span> <span data-ttu-id="7617a-118">Spécifie un index qui peut effectuer des opérations alors que le serveur est connecté, ce qui nécessite de l'espace disque temporaire.</span><span class="sxs-lookup"><span data-stu-id="7617a-118">Specifies an index that can perform operations while the server is online, which requires temporary disk space.</span></span> <span data-ttu-id="7617a-119">Défini sur « true » ou « false », par exemple :</span><span class="sxs-lookup"><span data-stu-id="7617a-119">Set to either "true" or "false", for example:</span></span><br /><br /> `<Index Online="true">`<br /><br /> <span data-ttu-id="7617a-120">Par défaut, cet attribut est défini sur « false ».</span><span class="sxs-lookup"><span data-stu-id="7617a-120">By default, this attribute is set to "false".</span></span><br /><br /> <span data-ttu-id="7617a-121">Pour plus d'informations, consultez [Perform Index Operations Online](../../relational-databases/indexes/perform-index-operations-online.md).</span><span class="sxs-lookup"><span data-stu-id="7617a-121">For more information, see [Perform Index Operations Online](../../relational-databases/indexes/perform-index-operations-online.md).</span></span>|  
|`IndexSizeInMB`|`double`|<span data-ttu-id="7617a-122">facultatif.</span><span class="sxs-lookup"><span data-stu-id="7617a-122">Optional.</span></span> <span data-ttu-id="7617a-123">Spécifie la taille maximale, en mégaoctets, de l'index, par exemple :</span><span class="sxs-lookup"><span data-stu-id="7617a-123">Specifies the maximum size of the index in megabytes, for example:</span></span><br /><br /> `<Index IndexSizeInMB="873.75">`<br /><br /> <span data-ttu-id="7617a-124">Aucun paramètre par défaut.</span><span class="sxs-lookup"><span data-stu-id="7617a-124">No default setting.</span></span>|  
|`NumberOfRows`|`integer`|<span data-ttu-id="7617a-125">facultatif.</span><span class="sxs-lookup"><span data-stu-id="7617a-125">Optional.</span></span> <span data-ttu-id="7617a-126">Simule différentes tailles d'index, ce qui simule différentes tailles de tables, par exemple :</span><span class="sxs-lookup"><span data-stu-id="7617a-126">Simulates different index sizes, which effectively simulates different table sizes, for example:</span></span><br /><br /> `<Index NumberOfRows="3000">`<br /><br /> <span data-ttu-id="7617a-127">Aucun paramètre par défaut.</span><span class="sxs-lookup"><span data-stu-id="7617a-127">No default setting.</span></span>|  
|`QUOTED_IDENTIFIER`|`boolean`|<span data-ttu-id="7617a-128">facultatif.</span><span class="sxs-lookup"><span data-stu-id="7617a-128">Optional.</span></span> <span data-ttu-id="7617a-129">Force [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à suivre les règles ISO concernant les guillemets délimitant les identificateurs et les chaînes littérales.</span><span class="sxs-lookup"><span data-stu-id="7617a-129">Causes [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to follow the ISO rules regarding quotation marks delimiting identifiers and literal strings.</span></span> <span data-ttu-id="7617a-130">Cet attribut doit être activé si l'index se trouve sur une colonne calculée ou une vue.</span><span class="sxs-lookup"><span data-stu-id="7617a-130">This attribute must be turned on if the index is on a computed column or a view.</span></span> <span data-ttu-id="7617a-131">Par exemple, la syntaxe suivante active cet attribut :</span><span class="sxs-lookup"><span data-stu-id="7617a-131">For example, the following syntax sets this attribute on:</span></span><br /><br /> `<Index QUOTED_IDENTIFIER [...]>`<br /><br /> <span data-ttu-id="7617a-132">Par défaut, cet attribut est désactivé.</span><span class="sxs-lookup"><span data-stu-id="7617a-132">By default this attribute is turned off.</span></span><br /><br /> <span data-ttu-id="7617a-133">Pour plus d’informations, consultez [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="7617a-133">For more information, see [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql).</span></span>|  
|`ARITHABORT`|`boolean`|<span data-ttu-id="7617a-134">facultatif.</span><span class="sxs-lookup"><span data-stu-id="7617a-134">Optional.</span></span> <span data-ttu-id="7617a-135">Entraîne l'arrêt d'une requête lorsqu'un dépassement de capacité ou une division par zéro se produit durant son exécution.</span><span class="sxs-lookup"><span data-stu-id="7617a-135">Causes a query to terminate when an overflow or divide-by-zero error occurs during query execution.</span></span> <span data-ttu-id="7617a-136">Cet attribut doit être activé si l'index se trouve sur une colonne calculée ou une vue.</span><span class="sxs-lookup"><span data-stu-id="7617a-136">This attribute must be turned on if the index is on a computed column or a view.</span></span> <span data-ttu-id="7617a-137">Par exemple, la syntaxe suivante active cet attribut :</span><span class="sxs-lookup"><span data-stu-id="7617a-137">For example, the following syntax sets this attribute on:</span></span><br /><br /> `<Index ARITHABORT [...]>`<br /><br /> <span data-ttu-id="7617a-138">Par défaut, cet attribut est désactivé.</span><span class="sxs-lookup"><span data-stu-id="7617a-138">By default this attribute is turned off.</span></span><br /><br /> <span data-ttu-id="7617a-139">Pour plus d’informations, consultez [SET ARITHABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-arithabort-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="7617a-139">For more information, see [SET ARITHABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-arithabort-transact-sql).</span></span>|  
|`CONCAT_NULL_YIELDS_`<br /><br /> `NULL`|`boolean`|<span data-ttu-id="7617a-140">facultatif.</span><span class="sxs-lookup"><span data-stu-id="7617a-140">Optional.</span></span> <span data-ttu-id="7617a-141">Détermine si les résultats de concaténation sont considérés comme des valeurs NULL ou des chaînes vides.</span><span class="sxs-lookup"><span data-stu-id="7617a-141">Controls whether or not concatenation results are treated as null or empty string values.</span></span> <span data-ttu-id="7617a-142">Cet attribut doit être activé si l'index se trouve sur une colonne calculée ou une vue.</span><span class="sxs-lookup"><span data-stu-id="7617a-142">This attribute must be turned on if the index is on a computed column or a view.</span></span> <span data-ttu-id="7617a-143">Par exemple, la syntaxe suivante active cet attribut :</span><span class="sxs-lookup"><span data-stu-id="7617a-143">For example, the following syntax sets this attribute on:</span></span><br /><br /> `<Index CONCAT_NULL_YIELDS_NULL [...]>`<br /><br /> <span data-ttu-id="7617a-144">Par défaut, cet attribut est désactivé.</span><span class="sxs-lookup"><span data-stu-id="7617a-144">By default this attribute is turned off.</span></span><br /><br /> <span data-ttu-id="7617a-145">Pour plus d’informations, consultez [SET CONCAT_NULL_YIELDS_NULL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-concat-null-yields-null-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="7617a-145">For more information, see [SET CONCAT_NULL_YIELDS_NULL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-concat-null-yields-null-transact-sql).</span></span>|  
|`ANSI_NULLS`|`boolean`|<span data-ttu-id="7617a-146">facultatif.</span><span class="sxs-lookup"><span data-stu-id="7617a-146">Optional.</span></span> <span data-ttu-id="7617a-147">Spécifie le comportement conforme à la norme ISO pour les opérateurs de comparaison égal à (=) et différent de (<>), lorsqu'ils sont utilisés avec des valeurs Null.</span><span class="sxs-lookup"><span data-stu-id="7617a-147">Specifies ISO compliant behavior of the Equals (=) and Not Equal to (<>) comparison operators when used with null values.</span></span> <span data-ttu-id="7617a-148">Cet attribut doit être activé si l'index se trouve sur une colonne calculée ou une vue.</span><span class="sxs-lookup"><span data-stu-id="7617a-148">This attribute must be turned on if the index is on a computed column or a view.</span></span> <span data-ttu-id="7617a-149">Par exemple, la syntaxe suivante active cet attribut :</span><span class="sxs-lookup"><span data-stu-id="7617a-149">For example, the following syntax sets this attribute on:</span></span><br /><br /> `<Index ANSI_NULLS [...]>`<br /><br /> <span data-ttu-id="7617a-150">Par défaut, cet attribut est désactivé.</span><span class="sxs-lookup"><span data-stu-id="7617a-150">By default this attribute is turned off.</span></span><br /><br /> <span data-ttu-id="7617a-151">Pour plus d’informations, consultez [SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="7617a-151">For more information, see [SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql).</span></span>|  
|`ANSI_PADDING`|`boolean`|<span data-ttu-id="7617a-152">facultatif.</span><span class="sxs-lookup"><span data-stu-id="7617a-152">Optional.</span></span> <span data-ttu-id="7617a-153">Contrôle la façon dont une colonne stocke des valeurs plus courtes que sa taille définie</span><span class="sxs-lookup"><span data-stu-id="7617a-153">Controls the way a column stores values shorter than its defined size.</span></span> <span data-ttu-id="7617a-154">Cet attribut doit être activé si l'index se trouve sur une colonne calculée ou une vue.</span><span class="sxs-lookup"><span data-stu-id="7617a-154">This attribute must be turned on if the index is on a computed column or a view.</span></span> <span data-ttu-id="7617a-155">Par exemple, la syntaxe suivante active cet attribut :</span><span class="sxs-lookup"><span data-stu-id="7617a-155">For example, the following syntax sets this attribute on:</span></span><br /><br /> `<Index ANSI_PADDING [...]>`<br /><br /> <span data-ttu-id="7617a-156">Par défaut, cet attribut est désactivé.</span><span class="sxs-lookup"><span data-stu-id="7617a-156">By default this attribute is turned off.</span></span><br /><br /> <span data-ttu-id="7617a-157">Pour plus d’informations, consultez [SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="7617a-157">For more information, see [SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql).</span></span>|  
|`ANSI_WARNINGS`|`boolean`|<span data-ttu-id="7617a-158">facultatif.</span><span class="sxs-lookup"><span data-stu-id="7617a-158">Optional.</span></span> <span data-ttu-id="7617a-159">Spécifie le comportement conforme à la norme ISO pour plusieurs conditions d'erreur :</span><span class="sxs-lookup"><span data-stu-id="7617a-159">Specifies ISO standard behavior for several error conditions.</span></span> <span data-ttu-id="7617a-160">Cet attribut doit être activé si l'index se trouve sur une colonne calculée ou une vue.</span><span class="sxs-lookup"><span data-stu-id="7617a-160">This attribute must be turned on if the index is on a computed column or a view.</span></span> <span data-ttu-id="7617a-161">Par exemple, la syntaxe suivante active cet attribut :</span><span class="sxs-lookup"><span data-stu-id="7617a-161">For example, the following syntax sets this attribute on:</span></span><br /><br /> `<Index ANSI_WARNING [...]>`<br /><br /> <span data-ttu-id="7617a-162">Par défaut, cet attribut est désactivé.</span><span class="sxs-lookup"><span data-stu-id="7617a-162">By default this attribute is turned off.</span></span><br /><br /> <span data-ttu-id="7617a-163">Pour plus d’informations, consultez [SET ANSI_WARNINGS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-warnings-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="7617a-163">For more information, see [SET ANSI_WARNINGS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-warnings-transact-sql).</span></span>|  
|`NUMERIC_ROUNDABORT`|`boolean`|<span data-ttu-id="7617a-164">facultatif.</span><span class="sxs-lookup"><span data-stu-id="7617a-164">Optional.</span></span> <span data-ttu-id="7617a-165">Spécifie le niveau de gravité de l'erreur générée lorsqu'un arrondi effectué dans une expression entraîne une perte de précision.</span><span class="sxs-lookup"><span data-stu-id="7617a-165">Specifies the level of error reporting generated when rounding in an expression causes a loss of precision.</span></span> <span data-ttu-id="7617a-166">Cet attribut doit être désactivé si l'index se trouve sur une colonne calculée ou une vue.</span><span class="sxs-lookup"><span data-stu-id="7617a-166">This attribute must be off if the index is on a computed column or a view.</span></span><br /><br /> <span data-ttu-id="7617a-167">La syntaxe suivante active cet attribut :</span><span class="sxs-lookup"><span data-stu-id="7617a-167">The following syntax sets this attribute on:</span></span><br /><br /> `<Index ANSI_WARNING [...]>`<br /><br /> <span data-ttu-id="7617a-168">Par défaut, cet attribut est désactivé.</span><span class="sxs-lookup"><span data-stu-id="7617a-168">By default this attribute is turned off.</span></span><br /><br /> <span data-ttu-id="7617a-169">Pour plus d’informations, consultez [SET NUMERIC_ROUNDABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-numeric-roundabort-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="7617a-169">For more information, see [SET NUMERIC_ROUNDABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-numeric-roundabort-transact-sql).</span></span>|  
  
## <a name="element-characteristics"></a><span data-ttu-id="7617a-170">Caractéristiques de l'élément</span><span class="sxs-lookup"><span data-stu-id="7617a-170">Element Characteristics</span></span>  
  
|<span data-ttu-id="7617a-171">Caractéristique</span><span class="sxs-lookup"><span data-stu-id="7617a-171">Characteristic</span></span>|<span data-ttu-id="7617a-172">Description</span><span class="sxs-lookup"><span data-stu-id="7617a-172">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="7617a-173">**Type de données et longueur**</span><span class="sxs-lookup"><span data-stu-id="7617a-173">**Data type and length**</span></span>|<span data-ttu-id="7617a-174">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7617a-174">None.</span></span>|  
|<span data-ttu-id="7617a-175">**Valeur par défaut**</span><span class="sxs-lookup"><span data-stu-id="7617a-175">**Default value**</span></span>|<span data-ttu-id="7617a-176">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7617a-176">None.</span></span>|  
|<span data-ttu-id="7617a-177">**Occurrence**</span><span class="sxs-lookup"><span data-stu-id="7617a-177">**Occurrence**</span></span>|<span data-ttu-id="7617a-178">Obligatoire une fois pour chaque élément `Create` ou `Drop` si aucune autre structure PDS n'est spécifiée avec les éléments `Statistics` ou `Heap`.</span><span class="sxs-lookup"><span data-stu-id="7617a-178">Required once for each `Create` or `Drop` element if no other physical design structure is specified with either the `Statistics` or the `Heap` elements.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="7617a-179">Relations entre les éléments</span><span class="sxs-lookup"><span data-stu-id="7617a-179">Element Relationships</span></span>  
  
|<span data-ttu-id="7617a-180">Relation</span><span class="sxs-lookup"><span data-stu-id="7617a-180">Relationship</span></span>|<span data-ttu-id="7617a-181">Éléments</span><span class="sxs-lookup"><span data-stu-id="7617a-181">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="7617a-182">**Élément parent**</span><span class="sxs-lookup"><span data-stu-id="7617a-182">**Parent element**</span></span>|[<span data-ttu-id="7617a-183">Create, élément &#40;Assistant Paramétrage de base de données&#41;</span><span class="sxs-lookup"><span data-stu-id="7617a-183">Create Element &#40;DTA&#41;</span></span>](create-element-dta.md)<br /><br /> <span data-ttu-id="7617a-184">`Drop`Appartient.</span><span class="sxs-lookup"><span data-stu-id="7617a-184">`Drop` Element.</span></span> <span data-ttu-id="7617a-185">Pour plus d'informations, voir le schéma de l'Assistant Paramétrage du moteur de base de données.</span><span class="sxs-lookup"><span data-stu-id="7617a-185">For more information, see the Database Engine Tuning Advisor XML schema.</span></span>|  
|<span data-ttu-id="7617a-186">**Éléments enfants**</span><span class="sxs-lookup"><span data-stu-id="7617a-186">**Child elements**</span></span>|[<span data-ttu-id="7617a-187">Name, élément pour les index &#40;Assistant Paramétrage de base de données&#41;</span><span class="sxs-lookup"><span data-stu-id="7617a-187">Name Element for Index &#40;DTA&#41;</span></span>](name-element-for-index-dta.md)<br /><br /> [<span data-ttu-id="7617a-188">Column, élément pour les index &#40;Assistant Paramétrage de base de données&#41;</span><span class="sxs-lookup"><span data-stu-id="7617a-188">Column Element for Index &#40;DTA&#41;</span></span>](column-element-for-index-dta.md)<br /><br /> <span data-ttu-id="7617a-189">`PartitionScheme`Appartient.</span><span class="sxs-lookup"><span data-stu-id="7617a-189">`PartitionScheme` Element.</span></span> <span data-ttu-id="7617a-190">Pour plus d'informations, voir le schéma de l'Assistant Paramétrage du moteur de base de données.</span><span class="sxs-lookup"><span data-stu-id="7617a-190">For more information, see the Database Engine Tuning Advisor XML schema.</span></span><br /><br /> <span data-ttu-id="7617a-191">`PartitionColumn`Appartient.</span><span class="sxs-lookup"><span data-stu-id="7617a-191">`PartitionColumn` Element.</span></span> <span data-ttu-id="7617a-192">Pour plus d'informations, voir le schéma de l'Assistant Paramétrage du moteur de base de données.</span><span class="sxs-lookup"><span data-stu-id="7617a-192">For more information, see the Database Engine Tuning Advisor XML schema.</span></span><br /><br /> [<span data-ttu-id="7617a-193">Filegroup, élément pour les index &#40;Assistant Paramétrage de base de données&#41;</span><span class="sxs-lookup"><span data-stu-id="7617a-193">Filegroup Element for Index &#40;DTA&#41;</span></span>](filegroup-element-for-index-dta.md)<br /><br /> <span data-ttu-id="7617a-194">`NumberOfReferences`Appartient.</span><span class="sxs-lookup"><span data-stu-id="7617a-194">`NumberOfReferences` Element.</span></span> <span data-ttu-id="7617a-195">Pour plus d'informations, voir le schéma de l'Assistant Paramétrage du moteur de base de données.</span><span class="sxs-lookup"><span data-stu-id="7617a-195">For more information, see the Database Engine Tuning Advisor XML schema.</span></span><br /><br /> <span data-ttu-id="7617a-196">`PercentUsage`Appartient.</span><span class="sxs-lookup"><span data-stu-id="7617a-196">`PercentUsage` Element.</span></span> <span data-ttu-id="7617a-197">Pour plus d'informations, voir le schéma de l'Assistant Paramétrage du moteur de base de données.</span><span class="sxs-lookup"><span data-stu-id="7617a-197">For more information, see the Database Engine Tuning Advisor XML schema.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7617a-198">Exemple</span><span class="sxs-lookup"><span data-stu-id="7617a-198">Example</span></span>  
 <span data-ttu-id="7617a-199">Pour obtenir un exemple d’utilisation de cet élément, consultez l’[Exemple de fichier d’entrée XML avec une configuration spécifiée par l’utilisateur &#40;Assistant Paramétrage de base de données&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span><span class="sxs-lookup"><span data-stu-id="7617a-199">For a usage example of this element, see the [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md) .</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7617a-200">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7617a-200">See Also</span></span>  
 [<span data-ttu-id="7617a-201">Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;</span><span class="sxs-lookup"><span data-stu-id="7617a-201">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](../../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  