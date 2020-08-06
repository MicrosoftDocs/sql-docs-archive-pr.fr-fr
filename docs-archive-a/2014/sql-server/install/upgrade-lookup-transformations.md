---
title: Mettre à niveau les transformations de recherche | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Lookup transformation and upgrading
- upgrading caching for Lookup transformation
- upgrading Lookup transformation
ms.assetid: d9b2c281-91ee-4e20-bdf0-0cd77d4a4241
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 74430ab1bed232b8d510a8c28a8a690d88d1f6ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601264"
---
# <a name="upgrade-lookup-transformations"></a><span data-ttu-id="48dca-102">Mettre à niveau des transformations de recherche</span><span class="sxs-lookup"><span data-stu-id="48dca-102">Upgrade Lookup Transformations</span></span>
  <span data-ttu-id="48dca-103">Lorsque vous effectuez une mise à niveau de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], pensez à modifier les packages pour tirer parti des nouvelles fonctionnalités de la transformation de recherche.</span><span class="sxs-lookup"><span data-stu-id="48dca-103">When you upgrade from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] consider modifying packages to take advantage of the new features in the Lookup Transformation.</span></span> <span data-ttu-id="48dca-104">Cette transformation prend en charge les types de mise en cache et les options de sortie des données disponibles dans [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)].</span><span class="sxs-lookup"><span data-stu-id="48dca-104">The transformation supports the caching types and data output options available in [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)].</span></span> <span data-ttu-id="48dca-105">Pour plus d’informations sur la mise en cache et les sorties de données supplémentaires, consultez [Lookup transformation](../../integration-services/data-flow/transformations/lookup-transformation.md).</span><span class="sxs-lookup"><span data-stu-id="48dca-105">For more information about additional the caching and data outputs, see [Lookup Transformation](../../integration-services/data-flow/transformations/lookup-transformation.md).</span></span>  
  
 <span data-ttu-id="48dca-106">Dans [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)], les types de mise en cache disponibles sont la mise en cache complète, la mise en cache partielle et l'absence de mise en cache.</span><span class="sxs-lookup"><span data-stu-id="48dca-106">In [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)], the available caching types are full caching, partial caching, and no caching.</span></span> <span data-ttu-id="48dca-107">Dans [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)], vous pouvez configurer une transformation de recherche afin d'utiliser l'un de ces types de mise en cache.</span><span class="sxs-lookup"><span data-stu-id="48dca-107">In [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)], you can configure a Lookup transformation to use one of these caching types.</span></span> <span data-ttu-id="48dca-108">Pour plus d’informations sur la façon d’implémenter une mise en cache partielle ou aucune mise en cache, consultez [implémenter une recherche en mode aucun cache ou cache partiel](../../integration-services/data-flow/transformations/implement-a-lookup-in-no-cache-or-partial-cache-mode.md).</span><span class="sxs-lookup"><span data-stu-id="48dca-108">For more information about how to implement partial caching or no caching, see [Implement a Lookup in No Cache or Partial Cache Mode](../../integration-services/data-flow/transformations/implement-a-lookup-in-no-cache-or-partial-cache-mode.md).</span></span> <span data-ttu-id="48dca-109">Pour plus d’informations sur l’implémentation de la mise en cache complète, consultez [implémenter une transformation de recherche en mode cache complet à l’aide du gestionnaire de connexions du cache](../../integration-services/connection-manager/lookup-transformation-full-cache-mode-cache-connection-manager.md) et [implémenter une transformation de recherche en mode cache complet à l’aide du gestionnaire de connexions OLE DB](../../integration-services/connection-manager/lookup-transformation-full-cache-mode-ole-db-connection-manager.md).</span><span class="sxs-lookup"><span data-stu-id="48dca-109">For information about how to implement full caching, see [Implement a Lookup Transformation in Full Cache Mode Using the Cache Connection Manager](../../integration-services/connection-manager/lookup-transformation-full-cache-mode-cache-connection-manager.md) and [Implement a Lookup Transformation in Full Cache Mode Using the OLE DB Connection Manager](../../integration-services/connection-manager/lookup-transformation-full-cache-mode-ole-db-connection-manager.md).</span></span>  
  
 <span data-ttu-id="48dca-110">Dans [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)], la transformation de recherche comportait une entrée, une sortie et une sortie d'erreur.</span><span class="sxs-lookup"><span data-stu-id="48dca-110">In [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)], the Lookup transformation had an input, an output, and an error output.</span></span> <span data-ttu-id="48dca-111">Les lignes de l'entrée qui possédaient des entrées correspondantes dans le jeu de données de référence étaient gérées par la sortie.</span><span class="sxs-lookup"><span data-stu-id="48dca-111">Rows in the input that had matching entries in the reference dataset were handled by the output.</span></span> <span data-ttu-id="48dca-112">Les lignes de l'entrée qui ne possédaient pas d'entrées correspondantes étaient traitées en tant qu'erreurs et pouvaient être redirigées vers la sortie d'erreur.</span><span class="sxs-lookup"><span data-stu-id="48dca-112">Rows in the input that did not have matching entries were treated as errors and could be redirected to the error output.</span></span> <span data-ttu-id="48dca-113">Dans [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)], la transformation de recherche comporte deux sorties : une sortie avec correspondance et une sortie sans correspondance.</span><span class="sxs-lookup"><span data-stu-id="48dca-113">In [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)], the Lookup transformation has two outputs: a match output and a no match output.</span></span>  
  
 <span data-ttu-id="48dca-114">Par défaut, lorsque vous exécutez une transformation de recherche créée dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] traite les lignes sans entrées correspondantes comme des erreurs et vous permet de rediriger ces lignes vers une sortie d'erreur.</span><span class="sxs-lookup"><span data-stu-id="48dca-114">By default, when you run a Lookup transformation that was created in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] treats the rows without matching entries as errors and enables you to redirect the rows to an error output.</span></span> <span data-ttu-id="48dca-115">Vous avez la possibilité de configurer la transformation de recherche afin de traiter les lignes comme si elles n'étaient pas des erreurs et de rediriger ces lignes vers la sortie sans correspondance.</span><span class="sxs-lookup"><span data-stu-id="48dca-115">You have the option of configuring the Lookup transformation to treat the rows as non-errors and redirect the rows to the no match output.</span></span>  
  
 <span data-ttu-id="48dca-116">Pour plus d’informations, consultez [éditeur de transformation de recherche &#40;&#41;de page général ](../../integration-services/general-page-of-integration-services-designers-options.md).</span><span class="sxs-lookup"><span data-stu-id="48dca-116">For more information, see [Lookup Transformation Editor &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48dca-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48dca-117">See Also</span></span>  
 [<span data-ttu-id="48dca-118">Transformation de recherche</span><span class="sxs-lookup"><span data-stu-id="48dca-118">Lookup Transformation</span></span>](../../integration-services/data-flow/transformations/lookup-transformation.md)  
  
  