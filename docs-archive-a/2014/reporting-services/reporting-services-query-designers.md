---
title: Concepteurs de requêtes Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- query designers [Reporting Services]
ms.assetid: 07efd3f1-804f-45f7-b62a-3e727a3d9835
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4febd0b0e0bf028d16aa3ef13ce4294feb930072
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703783"
---
# <a name="reporting-services-query-designers"></a><span data-ttu-id="99097-102">Concepteurs de requêtes Reporting Services</span><span class="sxs-lookup"><span data-stu-id="99097-102">Reporting Services Query Designers</span></span>
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<span data-ttu-id="99097-103">fournit des concepteurs de requêtes graphiques et textuels pour vous aider à créer des requêtes pour chaque type de source de données dans votre rapport.</span><span class="sxs-lookup"><span data-stu-id="99097-103">provides graphical and text-based query designers to help you build queries for each data source type in your report.</span></span>  
  
 <span data-ttu-id="99097-104">Certaines sources de données prennent en charge des concepteurs graphiques qui vous aident à générer une requête de façon interactive.</span><span class="sxs-lookup"><span data-stu-id="99097-104">Some data sources support graphical designers that help you build a query interactively.</span></span> <span data-ttu-id="99097-105">D'autres sources de données utilisent un concepteur de requêtes textuel.</span><span class="sxs-lookup"><span data-stu-id="99097-105">Other data sources use a text-based query designer.</span></span> <span data-ttu-id="99097-106">Le concepteur de requêtes graphique vous permet de faire glisser des éléments de métadonnées qui représentent les données sous-jacentes sur une source de données vers l'aire de conception de la requête.</span><span class="sxs-lookup"><span data-stu-id="99097-106">By using a graphical query designer, you can drag metadata items that represent the underlying data on a data source to the query design surface.</span></span> <span data-ttu-id="99097-107">Le concepteur de requêtes textuel vous permet de taper le texte des commandes dans un volet de requête.</span><span class="sxs-lookup"><span data-stu-id="99097-107">By using a text-based query designer, you can type command text into a query pane.</span></span> <span data-ttu-id="99097-108">Vous pouvez passer d'un concepteur de requêtes graphique à un concepteur de requêtes textuel en cliquant sur l'icône du concepteur de requêtes textuel dans la barre d'outils.</span><span class="sxs-lookup"><span data-stu-id="99097-108">You can change from a graphical query designer to a text-based query designer by clicking the text-based query designer icon on the toolbar.</span></span>  
  
 <span data-ttu-id="99097-109">Les types de sources de données disponibles dans votre rapport sont déterminés par les extensions de données de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] installées sur votre client ou serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="99097-109">The data source types that are available in your report are determined by the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] data extensions installed on your client or report server.</span></span> <span data-ttu-id="99097-110">Pour plus d'informations, consultez [RSReportDesigner Configuration File](report-server/rsreportdesigner-configuration-file.md) et [RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="99097-110">For more information, see [RSReportDesigner Configuration File](report-server/rsreportdesigner-configuration-file.md) and [RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md).</span></span>  
  
 <span data-ttu-id="99097-111">Une extension pour le traitement des données et son concepteur de requêtes associé peuvent être différents au niveau de la prise en charge des sources de données comme suit :</span><span class="sxs-lookup"><span data-stu-id="99097-111">A data processing extension and its associated query designer can differ in support for data sources in the following ways:</span></span>  
  
-   <span data-ttu-id="99097-112">**Par type de concepteur de requêtes.**</span><span class="sxs-lookup"><span data-stu-id="99097-112">**By query designer type.**</span></span> <span data-ttu-id="99097-113">Par exemple, une source de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] prend en charge à la fois les concepteurs de requêtes graphiques et textuels.</span><span class="sxs-lookup"><span data-stu-id="99097-113">For example, a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] data source supports both the graphical and text-based query designers.</span></span>  
  
-   <span data-ttu-id="99097-114">**Par variation de langage de requête.**</span><span class="sxs-lookup"><span data-stu-id="99097-114">**By query language variation.**</span></span> <span data-ttu-id="99097-115">Par exemple, un langage de requête comme [!INCLUDE[tsql](../includes/tsql-md.md)] peut être différent du point de vue de la syntaxe selon le type de source de données.</span><span class="sxs-lookup"><span data-stu-id="99097-115">For example, a query language such as [!INCLUDE[tsql](../includes/tsql-md.md)] can differ in syntax depending on the data source type.</span></span> <span data-ttu-id="99097-116">Le langage [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[tsql](../includes/tsql-md.md)] et le langage Oracle SQL présentent une variation de syntaxe pour une commande de requête.</span><span class="sxs-lookup"><span data-stu-id="99097-116">The [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[tsql](../includes/tsql-md.md)] language and the Oracle SQL language have some variation in syntax for a query command.</span></span>  
  
-   <span data-ttu-id="99097-117">**Par prise en charge de la partie schéma d'un nom d'objet de base de données.**</span><span class="sxs-lookup"><span data-stu-id="99097-117">**By support for the schema part of a database object name.**</span></span> <span data-ttu-id="99097-118">Lorsqu'une source de données utilise des schémas dans l'identificateur d'objets de la base de données, le nom du schéma doit être fourni dans la requête pour les noms qui ne font pas appel au schéma par défaut.</span><span class="sxs-lookup"><span data-stu-id="99097-118">When a data source uses schemas as part of the database object identifier, the schema name must be supplied as part of the query for any names that do not use the default schema.</span></span> <span data-ttu-id="99097-119">Par exemple, `SELECT FirstName, LastName FROM [Person].[Person]`.</span><span class="sxs-lookup"><span data-stu-id="99097-119">For example, `SELECT FirstName, LastName FROM [Person].[Person]`.</span></span>  
  
-   <span data-ttu-id="99097-120">**Par prise en charge des paramètres de requête.**</span><span class="sxs-lookup"><span data-stu-id="99097-120">**By support for query parameters.**</span></span> <span data-ttu-id="99097-121">La prise en charge des paramètres varie selon les fournisseurs de données.</span><span class="sxs-lookup"><span data-stu-id="99097-121">Data providers differ in support for parameters.</span></span> <span data-ttu-id="99097-122">Certains fournisseurs de données prennent en charge des paramètres nommés ; par exemple, `SELECT Col1, Col2 FROM Table WHERE <parameter identifier><parameter name> = <value>`.</span><span class="sxs-lookup"><span data-stu-id="99097-122">Some data providers support named parameters; for example, `SELECT Col1, Col2 FROM Table WHERE <parameter identifier><parameter name> = <value>`.</span></span> <span data-ttu-id="99097-123">Certains fournisseurs de données prennent en charge des paramètres sans nom ; par exemple, `SELECT Col1, Col2 FROM Table WHERE <column name> = ?`.</span><span class="sxs-lookup"><span data-stu-id="99097-123">Some data providers support unnamed parameters; for example, `SELECT Col1, Col2 FROM Table WHERE <column name> = ?`.</span></span> <span data-ttu-id="99097-124">L’identificateur de paramètre peut varier selon le fournisseur de données. Par exemple, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] utilise l’arobase (@), alors qu’Oracle utilise les deux-points (:).</span><span class="sxs-lookup"><span data-stu-id="99097-124">The parameter identifier might differ by data provider; for example, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] uses the "at" (@) symbol, Oracle uses the colon (:).</span></span> <span data-ttu-id="99097-125">Certains fournisseurs de données ne prennent pas en charge les paramètres.</span><span class="sxs-lookup"><span data-stu-id="99097-125">Some data providers do not support parameters.</span></span>  
  
-   <span data-ttu-id="99097-126">**Par capacité à importer des requêtes.**</span><span class="sxs-lookup"><span data-stu-id="99097-126">**By ability to import queries.**</span></span> <span data-ttu-id="99097-127">Par exemple, pour une source de données de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , vous pouvez importer une requête à partir d'un fichier de définition de rapport (.rdl) ou d'un fichier .sql.</span><span class="sxs-lookup"><span data-stu-id="99097-127">For example, for a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] data source, you can import a query from a report definition file (.rdl) or from a .sql file.</span></span>  
  
## <a name="query-designers"></a><span data-ttu-id="99097-128">Concepteurs de requêtes</span><span class="sxs-lookup"><span data-stu-id="99097-128">Query Designers</span></span>  
 <span data-ttu-id="99097-129">Les rubriques suivantes décrivent l'interface utilisateur pour chaque concepteur de requêtes.</span><span class="sxs-lookup"><span data-stu-id="99097-129">The following topics describe the user interface for each query designer.</span></span>  
  
-   [<span data-ttu-id="99097-130">Interface utilisateur du Concepteur de requêtes MDX Analysis Services</span><span class="sxs-lookup"><span data-stu-id="99097-130">Analysis Services MDX Query Designer User Interface</span></span>](report-data/analysis-services-mdx-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="99097-131">Interface utilisateur du Concepteur de requêtes DMX Analysis Services</span><span class="sxs-lookup"><span data-stu-id="99097-131">Analysis Services DMX Query Designer User Interface</span></span>](report-data/analysis-services-dmx-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="99097-132">Interface utilisateur du concepteur de requêtes graphique</span><span class="sxs-lookup"><span data-stu-id="99097-132">Graphical Query Designer User Interface</span></span>](report-data/graphical-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="99097-133">Interface utilisateur du Concepteur de requêtes relationnelles</span><span class="sxs-lookup"><span data-stu-id="99097-133">Relational Query Designer User Interface</span></span>](../../2014/reporting-services/relational-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="99097-134">Interface utilisateur du Concepteur de requêtes Hyperion Essbase</span><span class="sxs-lookup"><span data-stu-id="99097-134">Hyperion Essbase Query Designer User Interface</span></span>](report-data/hyperion-essbase-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="99097-135">Interface utilisateur du concepteur de requêtes de modèle de rapport</span><span class="sxs-lookup"><span data-stu-id="99097-135">Report Model Query Designer User Interface</span></span>](report-data/report-model-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="99097-136">Interface utilisateur du Concepteur de requêtes SAP NetWeaver BI</span><span class="sxs-lookup"><span data-stu-id="99097-136">SAP NetWeaver BI Query Designer User Interface</span></span>](report-data/sap-netweaver-bi-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="99097-137">Concepteur de requêtes de liste SharePoint</span><span class="sxs-lookup"><span data-stu-id="99097-137">SharePoint List Query Designer</span></span>](../../2014/reporting-services/sharepoint-list-query-designer.md)  
  
-   [<span data-ttu-id="99097-138">Interface utilisateur du Concepteur de requêtes textuel</span><span class="sxs-lookup"><span data-stu-id="99097-138">Text-based Query Designer User Interface</span></span>](../../2014/reporting-services/text-based-query-designer-user-interface.md)  
  
## <a name="see-also"></a><span data-ttu-id="99097-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99097-139">See Also</span></span>  
 <span data-ttu-id="99097-140">[Sources de données prises en charge par Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md) </span><span class="sxs-lookup"><span data-stu-id="99097-140">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md) </span></span>  
 <span data-ttu-id="99097-141">[Ajouter des données à partir de sources de données externes &#40;SSRS&#41;](report-data/add-data-from-external-data-sources-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="99097-141">[Add Data from External Data Sources &#40;SSRS&#41;](report-data/add-data-from-external-data-sources-ssrs.md) </span></span>  
 <span data-ttu-id="99097-142">[Extensions pour le traitement des données et fournisseurs de données de .NET Framework &#40;SSRS&#41;](report-data/data-processing-extensions-and-net-framework-data-providers-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="99097-142">[Data Processing Extensions and .NET Framework Data Providers &#40;SSRS&#41;](report-data/data-processing-extensions-and-net-framework-data-providers-ssrs.md) </span></span>  
 [<span data-ttu-id="99097-143">Extensions &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="99097-143">Extensions &#40;SSRS&#41;</span></span>](extensions-ssrs.md)  
  
  