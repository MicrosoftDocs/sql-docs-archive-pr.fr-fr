---
title: Architecture des objets serveur ADOMD.NET | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- ADOMD.NET, object model
- object model [ADOMD.NET]
ms.assetid: bdc81de9-b390-4654-b62a-cd6c0c9ca10d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 33a8f420f985c9e62c7d7f275e7de370a6988e8d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696276"
---
# <a name="adomdnet-server-object-architecture"></a><span data-ttu-id="cda33-102">Architecture des objets serveur ADOMD.NET</span><span class="sxs-lookup"><span data-stu-id="cda33-102">ADOMD.NET Server Object Architecture</span></span>
  <span data-ttu-id="cda33-103">Les objets serveur ADOMD.NET sont des objets d’assistance qui peuvent être utilisés pour créer des fonctions définies par l’utilisateur (UDF) ou des procédures stockées dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="cda33-103">The ADOMD.NET server objects are helper objects that can be used to create user defined functions (UDFs) or stored procedures in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cda33-104">Pour utiliser l'espace de noms `Microsoft.AnalysisServices.AdomdServer` (et ces objets), une référence à msmgdsrv.dll doit être ajoutée au projet UDF ou à la procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="cda33-104">To use the `Microsoft.AnalysisServices.AdomdServer` namespace (and these objects), a reference to the msmgdsrv.dll must be added to UDF project or stored procedure.</span></span>  
  
 <span data-ttu-id="cda33-105">![Affiche les relations d'objet dans le serveur ADOMD.NET](../../analysis-services/dev-guide/media/adomdnetserverobjectmodel.gif "Affiche les relations d'objet dans le serveur ADOMD.NET")</span><span class="sxs-lookup"><span data-stu-id="cda33-105">![Shows the object relationships in ADOMD.NET Server](../../analysis-services/dev-guide/media/adomdnetserverobjectmodel.gif "Shows the object relationships in ADOMD.NET Server")</span></span>  
<span data-ttu-id="cda33-106">Modèle objet ADOMD.NET</span><span class="sxs-lookup"><span data-stu-id="cda33-106">ADOMD.NET Object Model</span></span>  
  
 <span data-ttu-id="cda33-107">L'interaction avec la hiérarchie d'objets ADOMD.NET débute généralement avec un ou plusieurs objets de la couche de niveau supérieur, comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="cda33-107">Interaction with the ADOMD.NET object hierarchy typically starts with one or more of the objects in the topmost layer, as described in the following table.</span></span>  
  
|<span data-ttu-id="cda33-108">À</span><span class="sxs-lookup"><span data-stu-id="cda33-108">To</span></span>|<span data-ttu-id="cda33-109">Utiliser cet objet</span><span class="sxs-lookup"><span data-stu-id="cda33-109">Use this object</span></span>|  
|--------|---------------------|  
|<span data-ttu-id="cda33-110">Évaluer des instructions MDX (Multidimensional Expressions)</span><span class="sxs-lookup"><span data-stu-id="cda33-110">Evaluate Multidimensional Expressions (MDX) expressions</span></span>|<span data-ttu-id="cda33-111">[Microsoft. AnalysisServices. AdomdServer. expression](/previous-versions/sql/sql-server-2014/ms143609(v=sql.120))</span><span class="sxs-lookup"><span data-stu-id="cda33-111">[Microsoft.AnalysisServices.AdomdServer.Expression](/previous-versions/sql/sql-server-2014/ms143609(v=sql.120))</span></span><br /> <span data-ttu-id="cda33-112">L’objet [Microsoft. AnalysisServices. AdomdServer. expression](/previous-versions/sql/sql-server-2014/ms143609(v=sql.120)) offre un moyen d’exécuter une expression MDX et d’évaluer cette expression sous un tuple spécifié.</span><span class="sxs-lookup"><span data-stu-id="cda33-112">The [Microsoft.AnalysisServices.AdomdServer.Expression](/previous-versions/sql/sql-server-2014/ms143609(v=sql.120)) object provides a way to run an MDX expression and evaluate that expression under a specified tuple.</span></span>|  
|<span data-ttu-id="cda33-113">Offrir la possibilité d'exécuter des fonctions MDX sans construire l'instruction MDX entière</span><span class="sxs-lookup"><span data-stu-id="cda33-113">Provide support for executing MDX functions without constructing the full MDX statement</span></span>|<span data-ttu-id="cda33-114">[Microsoft. AnalysisServices. AdomdServer. MDX](/previous-versions/sql/sql-server-2014/ms143616(v=sql.120))</span><span class="sxs-lookup"><span data-stu-id="cda33-114">[Microsoft.AnalysisServices.AdomdServer.MDX](/previous-versions/sql/sql-server-2014/ms143616(v=sql.120))</span></span><br /> <span data-ttu-id="cda33-115">L’objet [Microsoft. AnalysisServices. AdomdServer. MDX](/previous-versions/sql/sql-server-2014/ms143616(v=sql.120)) est pratique pour appeler des fonctions MDX prédéfinies sans utiliser l’objet [Microsoft. AnalysisServices. AdomdServer. expression](/previous-versions/sql/sql-server-2014/ms143609(v=sql.120)) .</span><span class="sxs-lookup"><span data-stu-id="cda33-115">The [Microsoft.AnalysisServices.AdomdServer.MDX](/previous-versions/sql/sql-server-2014/ms143616(v=sql.120)) object is convenient for calling predefined MDX functions without using the [Microsoft.AnalysisServices.AdomdServer.Expression](/previous-versions/sql/sql-server-2014/ms143609(v=sql.120)) object.</span></span> <span data-ttu-id="cda33-116">Des fonctions supplémentaires pour l’objet [Microsoft. AnalysisServices. AdomdServer. MDX](/previous-versions/sql/sql-server-2014/ms143616(v=sql.120)) doivent être disponibles dans les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="cda33-116">Additional functions for the [Microsoft.AnalysisServices.AdomdServer.MDX](/previous-versions/sql/sql-server-2014/ms143616(v=sql.120)) object should be available in future releases.</span></span>|  
|<span data-ttu-id="cda33-117">Représenter le contexte d'exécution actuel pour la fonction définie par l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="cda33-117">Represent the current execution context for the UDF</span></span>|<span data-ttu-id="cda33-118">[Microsoft. AnalysisServices. AdomdServer. Context](/previous-versions/sql/sql-server-2014/ms143353(v=sql.120))</span><span class="sxs-lookup"><span data-stu-id="cda33-118">[Microsoft.AnalysisServices.AdomdServer.Context](/previous-versions/sql/sql-server-2014/ms143353(v=sql.120))</span></span><br /> <span data-ttu-id="cda33-119">L’objet [Microsoft. AnalysisServices. AdomdServer. Context](/previous-versions/sql/sql-server-2014/ms143353(v=sql.120)) expose des informations telles que le cube ou le modèle d’exploration de données actuel et diverses collections de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="cda33-119">The [Microsoft.AnalysisServices.AdomdServer.Context](/previous-versions/sql/sql-server-2014/ms143353(v=sql.120)) object exposes information such as the current cube or mining model and various metadata collections.</span></span> <span data-ttu-id="cda33-120">L’une des principales utilisation de l’objet [Microsoft. AnalysisServices. AdomdServer. Context](/previous-versions/sql/sql-server-2014/ms143353(v=sql.120)) est la propriété [Microsoft. AnalysisServices. AdomdServer. Hierarchy. CurrentMember \*](/previous-versions/sql/sql-server-2014/ms137044(v=sql.120)) de l’objet [Microsoft. AnalysisServices. AdomdServer. Hierarchy](/previous-versions/sql/sql-server-2014/ms143578(v=sql.120)) .</span><span class="sxs-lookup"><span data-stu-id="cda33-120">One key use of the [Microsoft.AnalysisServices.AdomdServer.Context](/previous-versions/sql/sql-server-2014/ms143353(v=sql.120)) object is the [Microsoft.AnalysisServices.AdomdServer.Hierarchy.CurrentMember\*](/previous-versions/sql/sql-server-2014/ms137044(v=sql.120)) property of the [Microsoft.AnalysisServices.AdomdServer.Hierarchy](/previous-versions/sql/sql-server-2014/ms143578(v=sql.120)) object.</span></span> <span data-ttu-id="cda33-121">Cette utilisation clé permet à l'auteur de la fonction définie par l'utilisateur ou de la procédure stockée de prendre des décisions en fonction du membre d'une certaine dimension sur lequel la requête porte.</span><span class="sxs-lookup"><span data-stu-id="cda33-121">This key usage enables the author of the UDF or stored procedure to make decisions based on what member from a certain dimension the query is on.</span></span>|  
|<span data-ttu-id="cda33-122">Créer des ensembles et des tuples</span><span class="sxs-lookup"><span data-stu-id="cda33-122">Create sets and tuples</span></span>|<span data-ttu-id="cda33-123">[Microsoft. AnalysisServices. AdomdServer. SetBuilder](/previous-versions/sql/sql-server-2014/ms144510(v=sql.120)), [Microsoft. AnalysisServices. AdomdServer. TupleBuilder](/previous-versions/sql/sql-server-2014/ms145407(v=sql.120))</span><span class="sxs-lookup"><span data-stu-id="cda33-123">[Microsoft.AnalysisServices.AdomdServer.SetBuilder](/previous-versions/sql/sql-server-2014/ms144510(v=sql.120)), [Microsoft.AnalysisServices.AdomdServer.TupleBuilder](/previous-versions/sql/sql-server-2014/ms145407(v=sql.120))</span></span><br /> <span data-ttu-id="cda33-124">[Microsoft. AnalysisServices. AdomdServer. SetBuilder](/previous-versions/sql/sql-server-2014/ms144510(v=sql.120)) fournit un moyen de créer des ensembles immuables, tandis que [Microsoft. AnalysisServices. AdomdServer. TupleBuilder](/previous-versions/sql/sql-server-2014/ms145407(v=sql.120)) fournit un moyen de créer des tuples immuables.</span><span class="sxs-lookup"><span data-stu-id="cda33-124">The [Microsoft.AnalysisServices.AdomdServer.SetBuilder](/previous-versions/sql/sql-server-2014/ms144510(v=sql.120)) provides a way to create immutable sets, while the [Microsoft.AnalysisServices.AdomdServer.TupleBuilder](/previous-versions/sql/sql-server-2014/ms145407(v=sql.120)) provides a way to create immutable tuples.</span></span>|  
|<span data-ttu-id="cda33-125">Prendre en charge une conversion implicite entre les six types de base du langage MDX</span><span class="sxs-lookup"><span data-stu-id="cda33-125">Support implicit conversion and casting among the six basic types of the MDX language</span></span>|<span data-ttu-id="cda33-126">[Microsoft. AnalysisServices. AdomdServer. MDXValue](/previous-versions/sql/sql-server-2014/ms143573(v=sql.120))</span><span class="sxs-lookup"><span data-stu-id="cda33-126">[Microsoft.AnalysisServices.AdomdServer.MDXValue](/previous-versions/sql/sql-server-2014/ms143573(v=sql.120))</span></span><br /> <span data-ttu-id="cda33-127">L’objet [Microsoft. AnalysisServices. AdomdServer. MDXValue](/previous-versions/sql/sql-server-2014/ms143573(v=sql.120)) fournit une conversion implicite et un cast parmi les types suivants :</span><span class="sxs-lookup"><span data-stu-id="cda33-127">The [Microsoft.AnalysisServices.AdomdServer.MDXValue](/previous-versions/sql/sql-server-2014/ms143573(v=sql.120)) object provides implicit conversion and casting among the following types:</span></span><br /><br /> <span data-ttu-id="cda33-128">-   [Microsoft. AnalysisServices. AdomdServer. Hierarchy](/previous-versions/sql/sql-server-2014/ms143578(v=sql.120))</span><span class="sxs-lookup"><span data-stu-id="cda33-128">-   [Microsoft.AnalysisServices.AdomdServer.Hierarchy](/previous-versions/sql/sql-server-2014/ms143578(v=sql.120))</span></span><br /><span data-ttu-id="cda33-129">-   [Microsoft. AnalysisServices. AdomdServer. Level](/previous-versions/sql/sql-server-2014/ms143581(v=sql.120))</span><span class="sxs-lookup"><span data-stu-id="cda33-129">-   [Microsoft.AnalysisServices.AdomdServer.Level](/previous-versions/sql/sql-server-2014/ms143581(v=sql.120))</span></span><br /><span data-ttu-id="cda33-130">-   [Microsoft. AnalysisServices. AdomdServer. Member](/previous-versions/sql/sql-server-2014/ms143820(v=sql.120))</span><span class="sxs-lookup"><span data-stu-id="cda33-130">-   [Microsoft.AnalysisServices.AdomdServer.Member](/previous-versions/sql/sql-server-2014/ms143820(v=sql.120))</span></span><br /><span data-ttu-id="cda33-131">-   [Microsoft. AnalysisServices. AdomdServer. Tuple](/previous-versions/sql/sql-server-2014/ms145330(v=sql.120))</span><span class="sxs-lookup"><span data-stu-id="cda33-131">-   [Microsoft.AnalysisServices.AdomdServer.Tuple](/previous-versions/sql/sql-server-2014/ms145330(v=sql.120))</span></span><br /><span data-ttu-id="cda33-132">-   [Microsoft. AnalysisServices. AdomdServer. Set](/previous-versions/sql/sql-server-2014/ms144530(v=sql.120))</span><span class="sxs-lookup"><span data-stu-id="cda33-132">-   [Microsoft.AnalysisServices.AdomdServer.Set](/previous-versions/sql/sql-server-2014/ms144530(v=sql.120))</span></span><br /><span data-ttu-id="cda33-133">-Scalaires ou types valeur</span><span class="sxs-lookup"><span data-stu-id="cda33-133">-   Scalar, or value types</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cda33-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cda33-134">See Also</span></span>  
 [<span data-ttu-id="cda33-135">Programmation du serveur ADOMD.NET</span><span class="sxs-lookup"><span data-stu-id="cda33-135">ADOMD.NET Server Programming</span></span>](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-server/adomd-net-server-programming)  
  
  