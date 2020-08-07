---
title: rsProcessingError - Erreur Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsProcessingError
ms.assetid: 414ee58a-8251-4367-9a8e-10c068d17280
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ca98c5532db080ab1e146e2aaa81e24fcb25579b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612163"
---
# <a name="rsprocessingerror---reporting-services-error"></a><span data-ttu-id="b68cc-102">rsProcessingError - Erreur Reporting Services</span><span class="sxs-lookup"><span data-stu-id="b68cc-102">rsProcessingError - Reporting Services Error</span></span>
    
## <a name="details"></a><span data-ttu-id="b68cc-103">Détails</span><span class="sxs-lookup"><span data-stu-id="b68cc-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b68cc-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="b68cc-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="b68cc-105">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="b68cc-105">Event ID</span></span>|<span data-ttu-id="b68cc-106">rsProcessingError</span><span class="sxs-lookup"><span data-stu-id="b68cc-106">rsProcessingError</span></span>|  
|<span data-ttu-id="b68cc-107">Source de l’événement</span><span class="sxs-lookup"><span data-stu-id="b68cc-107">Event Source</span></span>|<span data-ttu-id="b68cc-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings.resources</span><span class="sxs-lookup"><span data-stu-id="b68cc-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings.resources</span></span>|  
|<span data-ttu-id="b68cc-109">Composant</span><span class="sxs-lookup"><span data-stu-id="b68cc-109">Component</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|<span data-ttu-id="b68cc-110">Texte du message</span><span class="sxs-lookup"><span data-stu-id="b68cc-110">Message Text</span></span>|<span data-ttu-id="b68cc-111">Des erreurs se sont produites lors du traitement du rapport.</span><span class="sxs-lookup"><span data-stu-id="b68cc-111">Errors have occurred in report processing.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b68cc-112">Explication</span><span class="sxs-lookup"><span data-stu-id="b68cc-112">Explanation</span></span>  
 <span data-ttu-id="b68cc-113">Une ou plusieurs erreurs sont survenues pendant la publication, le traitement, l'aperçu local, l'affichage local depuis le serveur de rapports ou la création d'un abonnement pour un rapport.</span><span class="sxs-lookup"><span data-stu-id="b68cc-113">One or more errors were encountered while publishing, processing, previewing locally, viewing from the report server, or creating a subscription for a report.</span></span> <span data-ttu-id="b68cc-114">Ce message d'erreur indique qu'au moins une erreur a été détectée.</span><span class="sxs-lookup"><span data-stu-id="b68cc-114">This error message indicates at least one error was detected.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="b68cc-115">Causes possibles</span><span class="sxs-lookup"><span data-stu-id="b68cc-115">Possible Causes</span></span>  
 <span data-ttu-id="b68cc-116">Les causes possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="b68cc-116">Possible causes include:</span></span>  
  
-   <span data-ttu-id="b68cc-117">Une erreur de traitement s'est produite sur le serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="b68cc-117">A processing error occurred on the report server.</span></span>  
  
-   <span data-ttu-id="b68cc-118">Une erreur de traitement s'est produite pendant le traitement local d'un rapport lors de l'affichage de l'aperçu du rapport.</span><span class="sxs-lookup"><span data-stu-id="b68cc-118">A processing error occurred during local report processing when previewing a report.</span></span>  
  
-   <span data-ttu-id="b68cc-119">Une expression de groupe a retourné un type de données incorrect.</span><span class="sxs-lookup"><span data-stu-id="b68cc-119">A group expression evaluated to an incorrect data type.</span></span>  
  
-   <span data-ttu-id="b68cc-120">Une définition de filtre spécifiait deux expressions qui ont retourné des types de données qui n'ont pas pu être comparés.</span><span class="sxs-lookup"><span data-stu-id="b68cc-120">A filter definition specified two expressions that evaluated to data types that could not be compared.</span></span>  
  
-   <span data-ttu-id="b68cc-121">Une expression fait référence à un champ inexistant dans la collection de champs.</span><span class="sxs-lookup"><span data-stu-id="b68cc-121">An expression referenced a non-existing field in the Fields collection.</span></span>  
  
-   <span data-ttu-id="b68cc-122">Une expression contenait un appel de fonction d'agrégation dont l'étendue est non valide ou incompatible.</span><span class="sxs-lookup"><span data-stu-id="b68cc-122">An expression included an aggregate function call with an invalid or conflicting scope.</span></span>  
  
-   <span data-ttu-id="b68cc-123">Une expression fait référence à un paramètre inexistant dans la collection de paramètres du rapport.</span><span class="sxs-lookup"><span data-stu-id="b68cc-123">An expression referenced a non-existing parameter in the Report Parameters collection.</span></span>  
  
-   <span data-ttu-id="b68cc-124">Un assembly personnalisé ou un assembly [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] qui a été incorrectement déployé n’a pas pu se charger.</span><span class="sxs-lookup"><span data-stu-id="b68cc-124">A custom assembly or a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] assembly that was incorrectly deployed failed to load.</span></span>  
  
-   <span data-ttu-id="b68cc-125">Un paramètre dont la propriété Nullable a la valeur `False` a détecté une valeur null dans le paramètre.</span><span class="sxs-lookup"><span data-stu-id="b68cc-125">A parameter that has the Nullable property set to `False` has detected a null value in the parameter.</span></span>  
  
-   <span data-ttu-id="b68cc-126">Une expression pour la propriété Hidden d'une région de données contient une erreur : La référence d’objet n’a pas la valeur d’une instance d’un objet.</span><span class="sxs-lookup"><span data-stu-id="b68cc-126">An expression for the Hidden property of a data region contains an error: Object reference not set to an instance of an object.</span></span>  
  
-   <span data-ttu-id="b68cc-127">Une expression contenait un appel de fonction non valide ou une erreur de syntaxe.</span><span class="sxs-lookup"><span data-stu-id="b68cc-127">An expression included an invalid function call or syntax error.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b68cc-128">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="b68cc-128">User Action</span></span>  
  
### <a name="finding-more-information"></a><span data-ttu-id="b68cc-129">Sources d'informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="b68cc-129">Finding More Information</span></span>  
 <span data-ttu-id="b68cc-130">Effectuez une ou plusieurs actions parmi les suivantes :</span><span class="sxs-lookup"><span data-stu-id="b68cc-130">Do one or more of the following actions:</span></span>  
  
-   <span data-ttu-id="b68cc-131">Si vous affichez le rapport à partir du serveur de rapports ou si vous l'affichez en tant qu'abonnement, lisez l'intégralité du texte du message d'erreur.</span><span class="sxs-lookup"><span data-stu-id="b68cc-131">If you are viewing the report from the report server or if you are viewing the report as a subscription, look at the entire text of the error message.</span></span> <span data-ttu-id="b68cc-132">Le texte développé contient des informations supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="b68cc-132">Additional information is provided in the expanded text.</span></span>  
  
-   <span data-ttu-id="b68cc-133">Si vous êtes en train de créer un rapport dans le Concepteur de rapports et que cette erreur s'affiche lors de l'aperçu ou de la publication du rapport, vous trouverez des informations supplémentaires dans la fenêtre Liste d'erreurs.</span><span class="sxs-lookup"><span data-stu-id="b68cc-133">If you are authoring a report in Report Designer and see this error when you preview or publish the report, additional information is provided in the Error List window.</span></span>  
  
-   <span data-ttu-id="b68cc-134">Si vous êtes en train de créer un rapport dans l'Aperçu du Concepteur de rapports, lisez l'intégralité du texte du message d'erreur.</span><span class="sxs-lookup"><span data-stu-id="b68cc-134">If you are authoring a report in Report Designer Preview, look at the entire text of the error message.</span></span> <span data-ttu-id="b68cc-135">Le texte développé contient des informations supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="b68cc-135">Additional information is provided in the expanded text.</span></span>  
  
-   <span data-ttu-id="b68cc-136">Si vous affichez un rapport sur le serveur de rapports et que vous êtes connecté en tant qu’administrateur local sur le serveur de rapports, vous pouvez consulter la pile des appels en cliquant avec le bouton droit sur la page et en sélectionnant **Afficher la source**.</span><span class="sxs-lookup"><span data-stu-id="b68cc-136">If you are viewing a report on the report server, and if you are running as local administrator on the report server, you can view the call stack if you right-click the page and select **View Source**.</span></span> <span data-ttu-id="b68cc-137">La pile des appels contient des informations supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="b68cc-137">Additional information is provided in the call stack.</span></span>  
  
-   <span data-ttu-id="b68cc-138">Si vous êtes connecté en tant qu’administrateur local sur le serveur de rapports, recherchez `ReportProcessingException`dans le fichier journal.</span><span class="sxs-lookup"><span data-stu-id="b68cc-138">If you are running as local administrator on the report server, search the log file for `ReportProcessingException`.</span></span> <span data-ttu-id="b68cc-139">Les entrées du journal contiennent des informations supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="b68cc-139">Log entries contain more information.</span></span> <span data-ttu-id="b68cc-140">Le fichier journal du serveur de rapports se trouve généralement à l’emplacement \<*drive*> suivant : \Program Files\Microsoft SQL Server\MSRS12. MSSQLSERVER\Reporting Services\LogFiles\ ReportServerService__*DateTimeStamp*. log.</span><span class="sxs-lookup"><span data-stu-id="b68cc-140">The report server log file is typically located at \<*drive*>:\Program Files\Microsoft SQL Server\MSRS12.MSSQLSERVER\Reporting Services\LogFiles\ReportServerService__*datetimestamp*.log.</span></span> <span data-ttu-id="b68cc-141">Pour plus d’informations, consultez [Fichiers journaux et sources de Reporting Services](../report-server/reporting-services-log-files-and-sources.md).</span><span class="sxs-lookup"><span data-stu-id="b68cc-141">For more information, see [Reporting Services Log Files and Sources](../report-server/reporting-services-log-files-and-sources.md).</span></span>  
  
### <a name="failed-to-load-expression-host-assembly"></a><span data-ttu-id="b68cc-142">Échec du chargement de l'assembly hôte d'expressions</span><span class="sxs-lookup"><span data-stu-id="b68cc-142">Failed to Load Expression Host Assembly</span></span>  
 <span data-ttu-id="b68cc-143">Les assemblys personnalisés doivent être signés par un nom fort et disposer de l’attribut AllowPartiallyTrustedCallers.</span><span class="sxs-lookup"><span data-stu-id="b68cc-143">Custom assemblies must have strong name signing and the attribute AllowPartiallyTrustedCallers set.</span></span> <span data-ttu-id="b68cc-144">Pour plus d’informations, consultez [Utilisation d’assemblys personnalisés avec des rapports](../custom-assemblies/using-custom-assemblies-with-reports.md) et [Présentation des stratégies de sécurité](../extensions/secure-development/understanding-security-policies.md).</span><span class="sxs-lookup"><span data-stu-id="b68cc-144">For more information, see [Using Custom Assemblies with Reports](../custom-assemblies/using-custom-assemblies-with-reports.md) and [Understanding Security Policies](../extensions/secure-development/understanding-security-policies.md).</span></span>  
  
### <a name="a-built-in-global-name-does-not-exist"></a><span data-ttu-id="b68cc-145">Un nom global intégré n'existe pas</span><span class="sxs-lookup"><span data-stu-id="b68cc-145">A Built-in Global Name Does Not Exist</span></span>  
 <span data-ttu-id="b68cc-146">Vérifiez l'orthographe dans les expressions.</span><span class="sxs-lookup"><span data-stu-id="b68cc-146">Check the spelling in expressions.</span></span> <span data-ttu-id="b68cc-147">Les noms de paramètres, de globales et de champs respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="b68cc-147">Built-in globals, parameters, and field names are case-sensitive.</span></span> <span data-ttu-id="b68cc-148">Dans l'expression source de l'erreur, vérifiez que le nom existe réellement dans le rapport et qu'il est correctement orthographié.</span><span class="sxs-lookup"><span data-stu-id="b68cc-148">In the expression causing the error, check that the name actually exists in the report and that it is spelled correctly.</span></span> <span data-ttu-id="b68cc-149">Pour plus d’informations, consultez [Collections intégrées dans les expressions &#40;Générateur de rapports et SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).</span><span class="sxs-lookup"><span data-stu-id="b68cc-149">For more information, see [Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).</span></span>  
  
### <a name="parameter-properties-and-null"></a><span data-ttu-id="b68cc-150">Propriétés de paramètre et valeur NULL</span><span class="sxs-lookup"><span data-stu-id="b68cc-150">Parameter Properties and Null</span></span>  
 <span data-ttu-id="b68cc-151">Un paramètre à valeurs multiples ne peut pas contenir la valeur NULL.</span><span class="sxs-lookup"><span data-stu-id="b68cc-151">A multivalue parameter cannot be Null.</span></span> <span data-ttu-id="b68cc-152">Pour plus d'informations, consultez [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).</span><span class="sxs-lookup"><span data-stu-id="b68cc-152">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).</span></span>  
  
### <a name="main-report-with-subreport-could-not-be-processed"></a><span data-ttu-id="b68cc-153">Le rapport principal avec le sous-rapport n'a pas pu être traité</span><span class="sxs-lookup"><span data-stu-id="b68cc-153">Main Report with Subreport Could Not Be Processed</span></span>  
 <span data-ttu-id="b68cc-154">Un rapport avec des sous-rapports doit être traité par la même version du processeur de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b68cc-154">A report with subreports must be processed by the same version of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report processor.</span></span> <span data-ttu-id="b68cc-155">Lors de la mise à niveau de rapports vers la version actuelle du schéma de la définition de rapport, le rapport principal et les sous-rapports peuvent ou non ne pas être mis à jour en même temps.</span><span class="sxs-lookup"><span data-stu-id="b68cc-155">When upgrading reports to the current version of the report definition schema, the main report and the subreports may or may not be updated at the same time.</span></span> <span data-ttu-id="b68cc-156">Si la version entre un rapport et ses sous-rapports n'est pas compatible, le message suivant est affiché : « Le sous-rapport n'a pas pu être traité ».</span><span class="sxs-lookup"><span data-stu-id="b68cc-156">If the version is not compatible between a report and its subreports, the following message is displayed: "Subreport could not be processed."</span></span>  
  
 <span data-ttu-id="b68cc-157">Vous devez modifier le rapport principal ou les sous-rapports pour que tous les rapports puissent être traités par la même version du processeur de rapports.</span><span class="sxs-lookup"><span data-stu-id="b68cc-157">You must change either the main report or the subreports so that all the reports can be processed by the same version of the report processor.</span></span> <span data-ttu-id="b68cc-158">Pour plus d’informations sur la cause de l’échec de la mise à niveau d’un rapport, consultez [Mettre à niveau des rapports](../install-windows/upgrade-reports.md).</span><span class="sxs-lookup"><span data-stu-id="b68cc-158">For information about why a report fails to upgrade, see [Upgrade Reports](../install-windows/upgrade-reports.md).</span></span>  
  
### <a name="verify-function-calls-are-visual-basic-and-not-sql"></a><span data-ttu-id="b68cc-159">Vérifier que les appels de fonction sont des appels de fonction Visual Basic et non SQL</span><span class="sxs-lookup"><span data-stu-id="b68cc-159">Verify Function Calls are Visual Basic and Not SQL</span></span>  
 <span data-ttu-id="b68cc-160">Vous pouvez utiliser des fonctions SQL dans le texte des requêtes sur une base de données relationnelle.</span><span class="sxs-lookup"><span data-stu-id="b68cc-160">You can use SQL functions in query text on a relational database.</span></span> <span data-ttu-id="b68cc-161">Vous ne pouvez pas utiliser de fonctions [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] dans le texte de requête.</span><span class="sxs-lookup"><span data-stu-id="b68cc-161">You cannot use [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] functions in query text.</span></span>  
  
 <span data-ttu-id="b68cc-162">Dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], les expressions peuvent utiliser des fonctions [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] , des fonctions System.Math ou System.String, des fonctions [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] complètes ou des fonctions personnalisées que vous fournissez dans un code personnalisé ou dans un assembly personnalisé.</span><span class="sxs-lookup"><span data-stu-id="b68cc-162">In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], expressions can use [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] functions, System.Math or System.String functions, fully qualified [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] functions, or custom functions that you provide in custom code or a custom assembly.</span></span> <span data-ttu-id="b68cc-163">Vous ne pouvez pas utiliser de fonctions SQL dans une expression.</span><span class="sxs-lookup"><span data-stu-id="b68cc-163">You cannot use SQL functions in an expression.</span></span>  
  
 <span data-ttu-id="b68cc-164">Vérifiez que les appels de fonction effectués dans la requête et les expressions sont valides.</span><span class="sxs-lookup"><span data-stu-id="b68cc-164">Verify that the function calls made in the query and in the expressions are valid.</span></span>  
  
### <a name="cannot-compare-data-types-for-a-filter"></a><span data-ttu-id="b68cc-165">Impossible de comparer des types de données pour un filtre</span><span class="sxs-lookup"><span data-stu-id="b68cc-165">Cannot Compare Data Types for a Filter</span></span>  
 <span data-ttu-id="b68cc-166">Dans une équation de filtre, l'expression de filtre qui définit le contenu du filtre et la valeur du filtre doit être le même type de données pour être comparé.</span><span class="sxs-lookup"><span data-stu-id="b68cc-166">In a filter equation, the filter expression that defines what to filter on and the filter value must be the same data type in order to be compared.</span></span> <span data-ttu-id="b68cc-167">Si l'une des erreurs suivantes s'affichent, modifiez l'expression de champ ou la valeur de filtre pour que les types de données correspondent :</span><span class="sxs-lookup"><span data-stu-id="b68cc-167">If you see one of the following errors, modify the field expression or the filter value so that the data types match:</span></span>  
  
-   <span data-ttu-id="b68cc-168">Le traitement de *\<report item type>* pour *\<report item name>* ne peut pas être effectué.</span><span class="sxs-lookup"><span data-stu-id="b68cc-168">The processing of *\<report item type>* for the *\<report item name>* cannot be performed.</span></span> <span data-ttu-id="b68cc-169">Impossible de comparer les données de types *\<type>* et *\<type>* .</span><span class="sxs-lookup"><span data-stu-id="b68cc-169">Cannot compare data of types *\<type>* and *\<type>*.</span></span> <span data-ttu-id="b68cc-170">Vérifiez le type de données retourné par *\<report item name>* .</span><span class="sxs-lookup"><span data-stu-id="b68cc-170">Please check the data type returned by the *\<report item name>*.</span></span>  
  
-   <span data-ttu-id="b68cc-171">Échec de l’évaluation de *\<property name>* .</span><span class="sxs-lookup"><span data-stu-id="b68cc-171">Failed to evaluate the *\<property name>*.</span></span>  
  
-   <span data-ttu-id="b68cc-172">Échec de l’évaluation de *\<property name>* .</span><span class="sxs-lookup"><span data-stu-id="b68cc-172">Failed to evaluate the *\<property name>*.</span></span> <span data-ttu-id="b68cc-173">Elle fait référence à un champ de DataSet qui contient une erreur : *\<error string>* .</span><span class="sxs-lookup"><span data-stu-id="b68cc-173">It references a dataset field which has an error: *\<error string>*.</span></span>  
  
 <span data-ttu-id="b68cc-174">Pour plus d’informations, consultez [Filtrer, regrouper et trier des données &#40;Générateur de rapports et SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md).</span><span class="sxs-lookup"><span data-stu-id="b68cc-174">For more information, see [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md).</span></span>  
  
### <a name="invalid-or-conflicting-scope-specification-in-an-aggregate-function-call"></a><span data-ttu-id="b68cc-175">Spécification d'étendue non valide et incompatible dans un appel de fonction d'agrégation</span><span class="sxs-lookup"><span data-stu-id="b68cc-175">Invalid or Conflicting Scope Specification in an Aggregate Function Call</span></span>  
 <span data-ttu-id="b68cc-176">Lorsque vous incluez des appels de fonction d'agrégation à une expression dans une cellule de tableau matriciel, le processeur de rapports évalue l'expression dans l'étendue des groupes intimes auxquels la cellule appartient.</span><span class="sxs-lookup"><span data-stu-id="b68cc-176">When you include aggregate function calls to an expression in a Tablix cell, the report processor evaluates the expression in the scope of the innermost groups to which the cell belongs.</span></span>  
  
 <span data-ttu-id="b68cc-177">Vous pouvez également passer le nom d'une étendue spécifique à une fonction d'agrégation.</span><span class="sxs-lookup"><span data-stu-id="b68cc-177">You can also pass the name of a specific scope to an aggregate function.</span></span> <span data-ttu-id="b68cc-178">L'étendue peut faire référence au nom d'un dataset, une région de données ou le nom d'une étendue plus élevée dans la hiérarchie de données.</span><span class="sxs-lookup"><span data-stu-id="b68cc-178">Scope can refer to the name of a dataset, a data region, or the name of a scope higher on the data hierarchy.</span></span> <span data-ttu-id="b68cc-179">Cela s'applique aux messages suivants :</span><span class="sxs-lookup"><span data-stu-id="b68cc-179">This applies to the following messages:</span></span>  
  
-   <span data-ttu-id="b68cc-180">La portée « » de « » n’est *\<report item type>* *\<report item name>* pas valide *\<scope name>* .</span><span class="sxs-lookup"><span data-stu-id="b68cc-180">The *\<report item type>* '*\<report item name>*' has an invalid scope "*\<scope name>*".</span></span> <span data-ttu-id="b68cc-181">L'étendue doit être l'étendue actuelle ou doit se trouver dans l'étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="b68cc-181">The scope must be the current scope, or contained within the current scope.</span></span>  
  
-   <span data-ttu-id="b68cc-182">L' *\<property name>* expression de *\<report item type>* ' *\<report item name>* 'a un paramètre d’étendue qui n’est pas valide pour une fonction d’agrégation.</span><span class="sxs-lookup"><span data-stu-id="b68cc-182">The *\<property name>* expression for the *\<report item type>* '*\<report item name>*' has a scope parameter that is not valid for an aggregate function.</span></span> <span data-ttu-id="b68cc-183">Le paramètre d'étendue doit être défini sur une constante de chaîne qui est égale au nom d'un groupe conteneur, au nom d'une région de données conteneur, ou au nom d'un dataset.</span><span class="sxs-lookup"><span data-stu-id="b68cc-183">The scope parameter must be set to a string constant that is equal to either the name of a containing group, the name of a containing data region, or the name of a dataset.</span></span>  
  
 <span data-ttu-id="b68cc-184">Pour les fonctions d'agrégation qui calculent des totaux cumulés (`Previous`, `RunningValue` ou `RowNumber`), vous pouvez spécifier un paramètre d'étendue qui est un nom de groupe de lignes ou un nom de groupe de colonnes, mais pas les deux.</span><span class="sxs-lookup"><span data-stu-id="b68cc-184">For aggregate functions that calculate running totals (`Previous`, `RunningValue`, or `RowNumber`), you can specify a scope parameter that is either a row group name or a column group name, but not both.</span></span> <span data-ttu-id="b68cc-185">Cela s'applique au message d'erreur suivant :</span><span class="sxs-lookup"><span data-stu-id="b68cc-185">This applies to the following error message:</span></span>  
  
-   <span data-ttu-id="b68cc-186">`Previous`, `RunningValue` ou les `RowNumber` fonctions d’agrégation utilisées dans les cellules de données du *\<report item type>* ' *\<report item name>* 'font référence à des étendues de regroupement dans les colonnes et les lignes de *\<report item type>* .</span><span class="sxs-lookup"><span data-stu-id="b68cc-186">`Previous`, `RunningValue` or `RowNumber` aggregate functions used in the data cells of the *\<report item type>* '*\<report item name>*' refer to grouping scopes in both the columns and rows of the *\<report item type>*.</span></span> <span data-ttu-id="b68cc-187">Les paramètres d’étendue de toutes les `Previous` `RunningValue` fonctions d' `RowNumber` agrégation dans un objet *\<report item type>* peuvent faire référence à des regroupements de lignes ou à des regroupements de colonnes de données, mais pas les deux.</span><span class="sxs-lookup"><span data-stu-id="b68cc-187">The scope parameters of all `Previous`, `RunningValue` and `RowNumber` aggregate functions within a *\<report item type>* can refer to row groupings or data column groupings, but not both.</span></span>  
  
 <span data-ttu-id="b68cc-188">Pour plus d’informations, consultez [Étendue des expressions pour les totaux, les agrégats et les collections intégrées &#40;Générateur de rapports et SSRS&#41;](../report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md) et [Collections intégrées dans les expressions &#40;Générateur de rapports et SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).</span><span class="sxs-lookup"><span data-stu-id="b68cc-188">For more information, see [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](../report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md) and [Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).</span></span>  
  
### <a name="default-dataset-scope-for-a-top-level-text-box"></a><span data-ttu-id="b68cc-189">Étendue de dataset par défaut pour une zone de texte de niveau supérieur</span><span class="sxs-lookup"><span data-stu-id="b68cc-189">Default Dataset Scope for a Top Level Text Box</span></span>  
 <span data-ttu-id="b68cc-190">N'utilisez pas d'étendue par défaut pour une zone de texte ajoutée à l'aire de conception du rapport lorsque le rapport a plusieurs dataset.</span><span class="sxs-lookup"><span data-stu-id="b68cc-190">Do not use a default scope for a text box added to the report design surface when the report has more than one dataset.</span></span> <span data-ttu-id="b68cc-191">Utilisez une expression qui inclut le nom du dataset comme étendue, et une fonction d'agrégation.</span><span class="sxs-lookup"><span data-stu-id="b68cc-191">Use an expression that includes the name of the dataset as the scope, and an aggregate function.</span></span> <span data-ttu-id="b68cc-192">Par exemple : `=First(Fields!FieldName.Value, "DataSet2")`.</span><span class="sxs-lookup"><span data-stu-id="b68cc-192">For example, `=First(Fields!FieldName.Value, "DataSet2")`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b68cc-193">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b68cc-193">See Also</span></span>  
 <span data-ttu-id="b68cc-194">[Expressions &#40;Générateur de rapports et SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b68cc-194">[Expressions &#40;Report Builder and SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="b68cc-195">[Informations de référence sur les fonctions d’agrégation &#40;Générateur de rapports et SSRS&#41;](../report-design/report-builder-functions-aggregate-functions-reference.md) </span><span class="sxs-lookup"><span data-stu-id="b68cc-195">[Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](../report-design/report-builder-functions-aggregate-functions-reference.md) </span></span>  
 <span data-ttu-id="b68cc-196">[Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](../report-design/expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b68cc-196">[Expression Examples &#40;Report Builder and SSRS&#41;](../report-design/expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="b68cc-197">[Ajouter des données à un rapport &#40;Générateur de rapports et SSRS&#41;](../report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b68cc-197">[Add Data to a Report &#40;Report Builder and SSRS&#41;](../report-data/report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="b68cc-198">[Filtres couramment utilisés &#40;Générateur de rapports et SSRS&#41;](../report-design/commonly-used-filters-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b68cc-198">[Commonly Used Filters &#40;Report Builder and SSRS&#41;](../report-design/commonly-used-filters-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="b68cc-199">[Collection de champs de dataset &#40;Générateur de rapports et SSRS&#41;](../report-data/dataset-fields-collection-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b68cc-199">[Dataset Fields Collection &#40;Report Builder and SSRS&#41;](../report-data/dataset-fields-collection-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="b68cc-200">[Code personnalisé et références d’assembly dans les expressions du Concepteur de rapports &#40;SSRS&#41;](../report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b68cc-200">[Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](../report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md) </span></span>  
 [<span data-ttu-id="b68cc-201">Références à la collection Parameters &#40;Générateur de rapports et SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="b68cc-201">Parameters Collection References &#40;Report Builder and SSRS&#41;</span></span>](../report-design/built-in-collections-parameters-collection-references-report-builder.md)  
  
  