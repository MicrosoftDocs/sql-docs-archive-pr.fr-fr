---
title: Extraction sur les structures d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a0b00a3b-f9db-4289-a8cb-ddf600cd64ac
author: minewiskan
ms.author: owend
ms.openlocfilehash: e8b3dad28227547f88956f1ac49e2878b2940f91
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87614909"
---
# <a name="drillthrough-on-mining-structures"></a><span data-ttu-id="07db2-102">Extraction sur des structures d'exploration de données</span><span class="sxs-lookup"><span data-stu-id="07db2-102">Drillthrough on Mining Structures</span></span>
  <span data-ttu-id="07db2-103">*L'extraction* désigne la capacité d'interroger un modèle d'exploration de données ou une structure d'exploration de données pour obtenir des informations détaillées qui ne sont pas exposées dans le modèle.</span><span class="sxs-lookup"><span data-stu-id="07db2-103">*Drillthrough* means the ability to query either a mining model or a mining structure and get detailed data that is not exposed in the model.</span></span>  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="07db2-104">fournit deux options différentes pour l'extraction des données de cas.</span><span class="sxs-lookup"><span data-stu-id="07db2-104">provides two different options for drilling through into case data.</span></span> <span data-ttu-id="07db2-105">Vous pouvez extraire les données utilisées pour générer le modèle d'exploration de données ou les données sources de la structure d'exploration de données.</span><span class="sxs-lookup"><span data-stu-id="07db2-105">You can drill through to the data that were used to build the mining model, or you can drill through to the source data in the mining structure.</span></span>  
  
## <a name="drillthrough-to-model-cases-vs-drillthrough-to-structure"></a><span data-ttu-id="07db2-106">Extraction dans des cas de modèle et dans la structure</span><span class="sxs-lookup"><span data-stu-id="07db2-106">Drillthrough to Model Cases vs. Drillthrough to Structure</span></span>  
 <span data-ttu-id="07db2-107">L'extraction dans des **cas de modèle** est utile pour rechercher des informations supplémentaires sur les règles, les modèles ou les clusters dans un modèle.</span><span class="sxs-lookup"><span data-stu-id="07db2-107">Drilling through to **model cases** is useful for finding additional details about rules, patterns or clusters in a model.</span></span>  
  
 <span data-ttu-id="07db2-108">Par opposition, **l'extraction dans les données de la structure** est conçue pour fournir un accès aux informations qui n'ont pas été mises à disposition dans le modèle.</span><span class="sxs-lookup"><span data-stu-id="07db2-108">In contrast, **drillthrough to structure** data is intended to provide access to information that was not made available in the model.</span></span> <span data-ttu-id="07db2-109">Par exemple, si vous disposez des autorisations appropriées, vous pouvez identifier les lignes de données qui ont été utilisées pour l'apprentissage du modèle et celles qui ont utilisées pour le test.</span><span class="sxs-lookup"><span data-stu-id="07db2-109">For example, if you have the appropriate permissions, you might want to find out which rows of data were used for training the model and which were used for testing.</span></span>  
  
 <span data-ttu-id="07db2-110">Vous pouvez également consulter les attributs des données qui n'ont pas été utilisées dans l'analyse, si elles ont été incluses dans la définition de la structure.</span><span class="sxs-lookup"><span data-stu-id="07db2-110">You can also view attributes of the data that were not used in analysis, provided they have been included in the structure definition.</span></span> <span data-ttu-id="07db2-111">Par exemple, souvent les structures d'exploration de données prennent en charge différents types de modèles, et certaines colonnes de structure peuvent avoir été exclues d'un modèle, car le type de données est incompatible ou les données ne sont pas utiles pour l'analyse.</span><span class="sxs-lookup"><span data-stu-id="07db2-111">For example, often mining structures support many different kinds of models, and some structure columns might have been excluded from a model because the data type was incompatible or the data was not useful for analysis.</span></span> <span data-ttu-id="07db2-112">Par exemple, vous ne devez pas utiliser les informations de contact client dans un modèle de clustering, même si les données ont été incluses dans la structure, mais en activant l'extraction vous accédez à ces informations sans exécuter de requêtes distinctes sur la source de données.</span><span class="sxs-lookup"><span data-stu-id="07db2-112">For example, you would not use customer contact information in a clustering model, even if the data was included in the structure, but by enabling drillthrough you gain access to this information without running separate queries against the data source.</span></span>  
  
## <a name="enabling-drillthrough-to-structure-data"></a><span data-ttu-id="07db2-113">Activation de l'extraction pour structurer les données</span><span class="sxs-lookup"><span data-stu-id="07db2-113">Enabling Drillthrough to Structure Data</span></span>  
 <span data-ttu-id="07db2-114">Pour utiliser l'extraction sur la structure d'exploration de données, les conditions suivantes doivent être remplies :</span><span class="sxs-lookup"><span data-stu-id="07db2-114">To use drillthrough on the mining structure, the following conditions must be met:</span></span>  
  
-   <span data-ttu-id="07db2-115">L'extraction sur le modèle doit également être activée.</span><span class="sxs-lookup"><span data-stu-id="07db2-115">Drillthrough on the model must also be enabled.</span></span> <span data-ttu-id="07db2-116">Par défaut, l'extraction des deux types est désactivée.</span><span class="sxs-lookup"><span data-stu-id="07db2-116">By default, drillthrough of both kinds is disabled.</span></span> <span data-ttu-id="07db2-117">Pour activer l'extraction dans l'Assistant Exploration de données, sélectionnez l'option d'activation de l'extraction vers les cas de modèles sur la dernière page de l'Assistant.</span><span class="sxs-lookup"><span data-stu-id="07db2-117">To enable drillthrough in the Data Mining Wizard, select the option to enable drillthrough to model cases on the final page of the wizard.</span></span> <span data-ttu-id="07db2-118">Vous pouvez également ajouter la capacité d'extraction sur un modèle ultérieurement en modifiant la propriété `AllowDrillthrough`.</span><span class="sxs-lookup"><span data-stu-id="07db2-118">You can also add the ability to drillthrough on a model later by changing the `AllowDrillthrough` property.</span></span>  
  
-   <span data-ttu-id="07db2-119">Si vous créez la structure d'exploration de données avec DMX, utilisez la clause WITH DRILLTHROUGH.</span><span class="sxs-lookup"><span data-stu-id="07db2-119">If you create the mining structure by using DMX, use the WITH DRILLTHROUGH clause.</span></span> <span data-ttu-id="07db2-120">Pour plus d’informations, consultez [CREATE MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx).</span><span class="sxs-lookup"><span data-stu-id="07db2-120">For more information, see [CREATE MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx).</span></span>  
  
-   <span data-ttu-id="07db2-121">Le principe de l'extraction consiste à extraire des informations sur les cas d'apprentissage mis en cache lorsque vous avez traité la structure d'exploration de données.</span><span class="sxs-lookup"><span data-stu-id="07db2-121">Drillthrough works by retrieving information about the training cases that was cached when you processed the mining structure.</span></span> <span data-ttu-id="07db2-122">Par conséquent, si vous effacez les données mises en cache après avoir traité la structure en modifiant la <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> propriété en `ClearAfterProcessing` , l’extraction ne fonctionnera pas.</span><span class="sxs-lookup"><span data-stu-id="07db2-122">Therefore, if you clear the cached data after processing the structure by changing the <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> property to `ClearAfterProcessing`, drillthrough will not work.</span></span> <span data-ttu-id="07db2-123">Pour activer l'extraction aux colonnes de structure, vous devez modifier la propriété <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> en `KeepTrainingCases`, puis retraiter la structure.</span><span class="sxs-lookup"><span data-stu-id="07db2-123">To enable drillthrough to structure columns, you must change the <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> property to `KeepTrainingCases` and then reprocess the structure.</span></span>  
  
-   <span data-ttu-id="07db2-124">Vérifiez que la propriété [AllowDrillThrough](https://docs.microsoft.com/bi-reference/assl/properties/allowdrillthrough-element-assl) de la structure d’exploration de données et du modèle d’exploration de données est définie sur `True` .</span><span class="sxs-lookup"><span data-stu-id="07db2-124">Verify that both the mining structure and the mining model have the [AllowDrillThrough](https://docs.microsoft.com/bi-reference/assl/properties/allowdrillthrough-element-assl) property set to `True`.</span></span> <span data-ttu-id="07db2-125">De plus, vous devez être membre d'un rôle ayant les autorisations d'extraction sur la structure et le modèle.</span><span class="sxs-lookup"><span data-stu-id="07db2-125">Moreover, you must be a member of a role that has drillthrough permissions on both the structure and the model.</span></span>  
  
## <a name="security-issues-for-drillthrough"></a><span data-ttu-id="07db2-126">Problèmes de sécurité pour l'extraction</span><span class="sxs-lookup"><span data-stu-id="07db2-126">Security Issues for Drillthrough</span></span>  
 <span data-ttu-id="07db2-127">Les autorisations d'extraction sont définies séparément sur la structure et le modèle.</span><span class="sxs-lookup"><span data-stu-id="07db2-127">Drillthrough permissions are set separately on the structure and model.</span></span> <span data-ttu-id="07db2-128">L'autorisation de modèle permet d'effectuer une extraction à partir du modèle, même si vous n'avez pas d'autorisations sur la structure.</span><span class="sxs-lookup"><span data-stu-id="07db2-128">The model permission lets you drill through from the model, even if you do not have permissions on the structure.</span></span> <span data-ttu-id="07db2-129">Les autorisations d’extraction sur la structure permettent en outre d’inclure des colonnes de structure dans les requêtes d’extraction à partir du modèle, à l’aide de la fonction [StructureColumn &#40;DMX&#41;](/sql/dmx/structurecolumn-dmx).</span><span class="sxs-lookup"><span data-stu-id="07db2-129">Drillthrough permissions on the structure provide the additional ability to include structure columns in drillthrough queries from the model, by using the [StructureColumn &#40;DMX&#41;](/sql/dmx/structurecolumn-dmx) function.</span></span>  
  
 <span data-ttu-id="07db2-130">Pour plus d’informations sur la création de rôles et l’attribution d’autorisations dans Analysis Services, consultez [Concepteur de rôle &#40;Analysis Services - Données multidimensionnelles&#41;](https://msdn.microsoft.com/library/ms189696(v=sql.120).aspx).</span><span class="sxs-lookup"><span data-stu-id="07db2-130">For information about how to create roles and assign permissions in Analysis Services, see [Role Designer &#40;Analysis Services - Multidimensional Data&#41;](https://msdn.microsoft.com/library/ms189696(v=sql.120).aspx).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="07db2-131">Si vous activez l'extraction à la fois sur la structure d'exploration de données et le modèle d'exploration de données, tout utilisateur membre d'un rôle ayant les autorisations d'extraction sur le modèle d'exploration de données peut également consulter les colonnes de la structure d'exploration de données, même si ces colonnes ne sont pas incluses dans le modèle d'exploration de données.</span><span class="sxs-lookup"><span data-stu-id="07db2-131">If you enable drillthrough on both the mining structure and the mining model, any user who is a member of a role that has drillthrough permissions on the mining model can also view columns in the mining structure, even if those columns are not included in the mining model.</span></span> <span data-ttu-id="07db2-132">Par conséquent, afin de protéger les informations sensibles, vous devez configurer la vue de la source de données de façon à masquer les informations personnelles et à n'autoriser l'accès en extraction sur la structure d'exploration de données qu'en cas de nécessité.</span><span class="sxs-lookup"><span data-stu-id="07db2-132">Therefore, to protect sensitive data, you should set up the data source view to mask personal information, and allow drillthrough access on the mining structure only when necessary.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="07db2-133">Tâches associées</span><span class="sxs-lookup"><span data-stu-id="07db2-133">Related Tasks</span></span>  
 <span data-ttu-id="07db2-134">Consultez les rubriques suivantes pour plus d'informations sur l'utilisation de l'extraction avec des modèles d'exploration de données.</span><span class="sxs-lookup"><span data-stu-id="07db2-134">See the following topics for more information about how to use drillthrough with mining models.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="07db2-135">Utiliser l'extraction dans la structure des visionneuses de modèle d'exploration de données</span><span class="sxs-lookup"><span data-stu-id="07db2-135">Use drillthrough to structure from the mining model viewers</span></span>|[<span data-ttu-id="07db2-136">Utiliser l'extraction des visionneuses de modèle</span><span class="sxs-lookup"><span data-stu-id="07db2-136">Use Drillthrough from the Model Viewers</span></span>](use-drillthrough-from-the-model-viewers.md)|  
|<span data-ttu-id="07db2-137">Consulter les exemples de requêtes d'extraction pour les types de modèles spécifiques.</span><span class="sxs-lookup"><span data-stu-id="07db2-137">See examples of drillthrough queries for specific model types.</span></span>|[<span data-ttu-id="07db2-138">Requêtes d’exploration de données</span><span class="sxs-lookup"><span data-stu-id="07db2-138">Data Mining Queries</span></span>](data-mining-queries.md)|  
|<span data-ttu-id="07db2-139">Obtenir des informations sur l'assignation d'autorisations qui s'appliquent à des structures d'exploration de données et à des modèles d'exploration de données spécifiques.</span><span class="sxs-lookup"><span data-stu-id="07db2-139">Get information about permissions that apply to specific mining structures and mining models.</span></span>|[<span data-ttu-id="07db2-140">Octroyer des autorisations sur des modèles et des structures d’exploration de données &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="07db2-140">Grant permissions on data mining structures and models &#40;Analysis Services&#41;</span></span>](../multidimensional-models/grant-permissions-on-data-mining-structures-and-models-analysis-services.md)|  
  
## <a name="see-also"></a><span data-ttu-id="07db2-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07db2-141">See Also</span></span>  
 [<span data-ttu-id="07db2-142">Extraction sur des modèles d'exploration de données</span><span class="sxs-lookup"><span data-stu-id="07db2-142">Drillthrough on Mining Models</span></span>](drillthrough-on-mining-models.md)  
  
  