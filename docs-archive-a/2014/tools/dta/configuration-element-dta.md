---
title: Configuration, élément (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Configuration element
ms.assetid: 1478e56f-57c4-4441-bac9-1ac91453839b
author: stevestein
ms.author: sstein
ms.openlocfilehash: d11938d9a9a694f994a3ea977022a393cbae23d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87695039"
---
# <a name="configuration-element-dta"></a><span data-ttu-id="72ab0-102">Configuration, élément (Assistant Paramétrage de base de données)</span><span class="sxs-lookup"><span data-stu-id="72ab0-102">Configuration Element (DTA)</span></span>
  <span data-ttu-id="72ab0-103">Spécifie une configuration spécifiée par l'utilisateur se composant de structures PDS existantes et hypothétiques en vue d'être analysée par l'Assistant Paramétrage du moteur de base de données lors du paramétrage d'une charge de travail.</span><span class="sxs-lookup"><span data-stu-id="72ab0-103">Specifies a user-specified configuration consisting of existing and hypothetical physical design structures for the Database Engine Tuning Advisor to analyze when tuning a workload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72ab0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72ab0-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
    <Server>...</Server>  
    <Workload>...</Workload>  
    <TuningOptions>...</TuningOptions  
    <Configuration [SpecificationMode="Relative" | "Absolute"]>  
    ...code removed here...  
    </Configuration>  
</DTAInput>  
```  
  
## <a name="element-attributes"></a><span data-ttu-id="72ab0-105">Attributs des éléments</span><span class="sxs-lookup"><span data-stu-id="72ab0-105">Element Attributes</span></span>  
  
|<span data-ttu-id="72ab0-106">Attribut de configuration</span><span class="sxs-lookup"><span data-stu-id="72ab0-106">Configuration Attribute</span></span>|<span data-ttu-id="72ab0-107">Description</span><span class="sxs-lookup"><span data-stu-id="72ab0-107">Description</span></span>|  
|-----------------------------|-----------------|  
|`SpecificationMode`|<span data-ttu-id="72ab0-108">facultatif.</span><span class="sxs-lookup"><span data-stu-id="72ab0-108">Optional.</span></span> <span data-ttu-id="72ab0-109">Spécifie si l'Assistant Paramétrage du moteur de base de données doit analyser la configuration spécifiée en relation avec la configuration existante active ou comme une configuration autonome entièrement nouvelle.</span><span class="sxs-lookup"><span data-stu-id="72ab0-109">Specifies whether Database Engine Tuning Advisor should analyze the specified configuration in relation to the current existing configuration, or as a completely new, standalone one.</span></span> <span data-ttu-id="72ab0-110">Utilisez un type de données **string** pour spécifier cet attribut avec l'une des valeurs autorisées suivantes :</span><span class="sxs-lookup"><span data-stu-id="72ab0-110">Use a **string** data type to specify this attribute with one of the following allowed values:</span></span><br /><br /> <span data-ttu-id="72ab0-111">`Relative`:</span><span class="sxs-lookup"><span data-stu-id="72ab0-111">`Relative`:</span></span> <br />                  <span data-ttu-id="72ab0-112">Évalue la configuration spécifiée en relation avec la configuration existante active des structures PDS (index, vues indexées, partitions) dans la base de données en cours de paramétrage.</span><span class="sxs-lookup"><span data-stu-id="72ab0-112">Evaluates the specified configuration in relation to the current existing configuration of physical design structures (indexes, indexed views, partitioning) in the database that is being tuned.</span></span> <span data-ttu-id="72ab0-113">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="72ab0-113">For example:</span></span> <br />`<Configuration SpecificationMode="Relative">`<br /><br /> <span data-ttu-id="72ab0-114">`Absolute`:</span><span class="sxs-lookup"><span data-stu-id="72ab0-114">`Absolute`:</span></span> <br />                  <span data-ttu-id="72ab0-115">Évalue la configuration spécifiée comme une configuration autonome.</span><span class="sxs-lookup"><span data-stu-id="72ab0-115">Evaluates the specified configuration as a standalone configuration.</span></span> <span data-ttu-id="72ab0-116">Lorsque la valeur Absolute est spécifiée, l'Assistant Paramétrage du moteur de base de données ne prend pas en compte la configuration existante.</span><span class="sxs-lookup"><span data-stu-id="72ab0-116">When Absolute is specified, Database Engine Tuning Advisor does not consider the existing configuration.</span></span> <span data-ttu-id="72ab0-117">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="72ab0-117">For example:</span></span><br />`<Configuration SpecificationMode="Absolute">`|  
  
## <a name="element-characteristics"></a><span data-ttu-id="72ab0-118">Caractéristiques de l'élément</span><span class="sxs-lookup"><span data-stu-id="72ab0-118">Element Characteristics</span></span>  
  
|<span data-ttu-id="72ab0-119">Caractéristique</span><span class="sxs-lookup"><span data-stu-id="72ab0-119">Characteristic</span></span>|<span data-ttu-id="72ab0-120">Description</span><span class="sxs-lookup"><span data-stu-id="72ab0-120">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="72ab0-121">**Type de données et longueur**</span><span class="sxs-lookup"><span data-stu-id="72ab0-121">**Data type and length**</span></span>|<span data-ttu-id="72ab0-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="72ab0-122">None.</span></span>|  
|<span data-ttu-id="72ab0-123">**Valeur par défaut**</span><span class="sxs-lookup"><span data-stu-id="72ab0-123">**Default value**</span></span>|<span data-ttu-id="72ab0-124">Aucun.</span><span class="sxs-lookup"><span data-stu-id="72ab0-124">None.</span></span>|  
|<span data-ttu-id="72ab0-125">**Occurrence**</span><span class="sxs-lookup"><span data-stu-id="72ab0-125">**Occurrence**</span></span>|<span data-ttu-id="72ab0-126">facultatif.</span><span class="sxs-lookup"><span data-stu-id="72ab0-126">Optional.</span></span> <span data-ttu-id="72ab0-127">Peut être utilisé une seule fois pour chaque élément `DTAInput`.</span><span class="sxs-lookup"><span data-stu-id="72ab0-127">Can use once for each `DTAInput` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="72ab0-128">Relations entre les éléments</span><span class="sxs-lookup"><span data-stu-id="72ab0-128">Element Relationships</span></span>  
  
|<span data-ttu-id="72ab0-129">Relation</span><span class="sxs-lookup"><span data-stu-id="72ab0-129">Relationship</span></span>|<span data-ttu-id="72ab0-130">Éléments</span><span class="sxs-lookup"><span data-stu-id="72ab0-130">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="72ab0-131">**Élément parent**</span><span class="sxs-lookup"><span data-stu-id="72ab0-131">**Parent element**</span></span>|[<span data-ttu-id="72ab0-132">DTAInput, élément &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="72ab0-132">DTAInput Element &#40;DTA&#41;</span></span>](dtainput-element-dta.md)|  
|<span data-ttu-id="72ab0-133">**Éléments enfants**</span><span class="sxs-lookup"><span data-stu-id="72ab0-133">**Child elements**</span></span>|[<span data-ttu-id="72ab0-134">Server, élément pour les configurations &#40;Assistant Paramétrage de base de données&#41;</span><span class="sxs-lookup"><span data-stu-id="72ab0-134">Server Element for Configuration &#40;DTA&#41;</span></span>](server-element-for-configuration-dta.md)|  
  
## <a name="example"></a><span data-ttu-id="72ab0-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="72ab0-135">Example</span></span>  
 <span data-ttu-id="72ab0-136">Pour obtenir un exemple d’utilisation de cet élément, consultez l’[Exemple de fichier d’entrée XML avec une configuration spécifiée par l’utilisateur &#40;Assistant Paramétrage de base de données&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span><span class="sxs-lookup"><span data-stu-id="72ab0-136">For a usage example of this element, see the [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72ab0-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72ab0-137">See Also</span></span>  
 [<span data-ttu-id="72ab0-138">Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;</span><span class="sxs-lookup"><span data-stu-id="72ab0-138">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  