---
title: Accès aux données de modèles multidimensionnels (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SSAS, data access interfaces
- objects [Analysis Services], data access interfaces
- Analysis Services data access interfaces
- data retrieval [Analysis Services]
- retrieving data
- metadata [Analysis Services]
- data access interfaces [Analysis Services]
- manipulating objects [Analysis Services]
- Analysis Services data access interfaces, about data access interfaces
ms.assetid: 46388efb-3c78-47a2-b5c9-5a69ff394d03
author: minewiskan
ms.author: owend
ms.openlocfilehash: 721cfbe160bf65c04462fca28f3b5261c1f1b00c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612565"
---
# <a name="multidimensional-model-data-access-analysis-services---multidimensional-data"></a><span data-ttu-id="f3415-102">Accès aux données de modèles multidimensionnels (Analysis Services - Données multidimensionnelles)</span><span class="sxs-lookup"><span data-stu-id="f3415-102">Multidimensional Model Data Access (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="f3415-103">Utilisez les informations de cette rubrique pour savoir comment accéder aux données multidimensionnelles de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] à l'aide des méthodes de programmation, d'un script ou d'applications clientes incluant la prise en charge intégrée pour se connecter à un serveur [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] sur votre réseau.</span><span class="sxs-lookup"><span data-stu-id="f3415-103">Use the information in this topic to learn how to access [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] multidimensional data using programmatic methods, script, or client applications that include built-in support for connecting to an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server on your network.</span></span>  
  
 <span data-ttu-id="f3415-104">Cette rubrique contient les sections suivantes :</span><span class="sxs-lookup"><span data-stu-id="f3415-104">This topic contains the following sections:</span></span>  
  
 [<span data-ttu-id="f3415-105">Applications clientes</span><span class="sxs-lookup"><span data-stu-id="f3415-105">Client Applications</span></span>](#bkmk_clientapps)  
  
 [<span data-ttu-id="f3415-106">Langages de requête</span><span class="sxs-lookup"><span data-stu-id="f3415-106">Query Languages</span></span>](#bkmk_querylang)  
  
 [<span data-ttu-id="f3415-107">Interfaces de programmation</span><span class="sxs-lookup"><span data-stu-id="f3415-107">Programmatic Interfaces</span></span>](#bkmk_api)  
  
##  <a name="client-applications"></a><a name="bkmk_clientapps"></a><span data-ttu-id="f3415-108">Applications clientes</span><span class="sxs-lookup"><span data-stu-id="f3415-108">Client Applications</span></span>  
 <span data-ttu-id="f3415-109">Bien qu'Analysis Services fournisse les interfaces qui vous permettent de générer ou intégrer les bases de données multidimensionnelles par programmation, une approche plus courante consiste à utiliser des applications clientes Microsoft et d'autres fournisseurs de logiciels existantes qui ont un accès intégré aux données Analysis Services.</span><span class="sxs-lookup"><span data-stu-id="f3415-109">Although Analysis Services provides interfaces that let you build or integrate multidimensional databases programmatically, a more common approach is to use existing client applications from Microsoft and other software vendors that have built-in data access to Analysis Services data.</span></span>  
  
 <span data-ttu-id="f3415-110">Les applications Microsoft suivantes prennent en charge les connexions natives aux données multidimensionnelles.</span><span class="sxs-lookup"><span data-stu-id="f3415-110">The following Microsoft applications support native connections to multidimensional data.</span></span>  
  
### <a name="excel"></a><span data-ttu-id="f3415-111">Excel</span><span class="sxs-lookup"><span data-stu-id="f3415-111">Excel</span></span>  
 <span data-ttu-id="f3415-112">Les données multidimensionnelles Analysis Services sont souvent présentées à l'aide de contrôles de tableaux et de graphiques croisés dynamiques dans un classeur Excel.</span><span class="sxs-lookup"><span data-stu-id="f3415-112">Analysis Services multidimensional data is often presented using pivot tables and pivot chart controls in an Excel workbook.</span></span> <span data-ttu-id="f3415-113">Les tableaux croisés dynamiques sont adaptés aux données multidimensionnelles car les hiérarchies, les agrégations et les éléments de navigation due modèle sont totalement compatibles avec les fonctionnalités de synthèse de données d'un tableau croisé dynamique.</span><span class="sxs-lookup"><span data-stu-id="f3415-113">PivotTables are suited to multidimensional data because the hierarchies, aggregations, and navigational constructs in the model pair well with the data summary features of a PivotTable.</span></span> <span data-ttu-id="f3415-114">Un fournisseur de données OLE DB Analysis Services est inclus dans une installation d'Excel pour faciliter la configuration des connexions de données.</span><span class="sxs-lookup"><span data-stu-id="f3415-114">An Analysis Services OLE DB data provider is included in an Excel installation to make setting up data connections easier.</span></span> <span data-ttu-id="f3415-115">Pour plus d'informations, consultez [Se connecter ou importer des données à partir de SQL Server Analysis Services](https://go.microsoft.com/fwlink/?linkID=215150).</span><span class="sxs-lookup"><span data-stu-id="f3415-115">For more information, see [Connect to or import data from SQL Server Analysis Services](https://go.microsoft.com/fwlink/?linkID=215150).</span></span>  
  
### <a name="reporting-services-reports"></a><span data-ttu-id="f3415-116">Rapports Reporting Services</span><span class="sxs-lookup"><span data-stu-id="f3415-116">Reporting Services Reports</span></span>  
 <span data-ttu-id="f3415-117">Vous pouvez utiliser le Générateur de rapports ou le Concepteur de rapports pour créer des rapports qui utilisent des bases de données Analysis Services contenant des données analytiques.</span><span class="sxs-lookup"><span data-stu-id="f3415-117">You can use Report Builder or Report Designer to create reports that consume Analysis Services databases that contain analytical data.</span></span> <span data-ttu-id="f3415-118">Le Générateur de rapports et le Concepteur de rapports incluent un concepteur de requêtes MDX qui vous permet de taper ou concevoir des instructions MDX qui extraient des données d'une source de données disponible.</span><span class="sxs-lookup"><span data-stu-id="f3415-118">Both Report Builder and Report Designer include an MDX query designer that you can use to type or design MDX statements that retrieve data from an available data source.</span></span> <span data-ttu-id="f3415-119">Pour plus d’informations, consultez [Sources de données prises en charge par Reporting Services &#40;SSRS&#41;](../../../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md) et [Type de connexion Analysis Services pour MDX &#40;SSRS&#41;](../../../reporting-services/report-data/analysis-services-connection-type-for-mdx-ssrs.md).</span><span class="sxs-lookup"><span data-stu-id="f3415-119">For more information, see [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../../../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md) and [Analysis Services Connection Type for MDX &#40;SSRS&#41;](../../../reporting-services/report-data/analysis-services-connection-type-for-mdx-ssrs.md).</span></span>  
  
### <a name="performancepoint-dashboards"></a><span data-ttu-id="f3415-120">Tableaux de bord PerformancePoint</span><span class="sxs-lookup"><span data-stu-id="f3415-120">PerformancePoint Dashboards</span></span>  
 <span data-ttu-id="f3415-121">Les tableaux de bord PerformancePoint servent à créer des tableaux de bord SharePoint qui communiquent les performances métier sur des mesures prédéfinies.</span><span class="sxs-lookup"><span data-stu-id="f3415-121">PerformancePoint Dashboards are used to create scorecards in SharePoint that communicate business performance against predefined measures.</span></span> <span data-ttu-id="f3415-122">PerformancePoint inclut la prise en charge des connexions de données aux données multidimensionnelles Analysis Services.</span><span class="sxs-lookup"><span data-stu-id="f3415-122">PerformancePoint includes support for data connections to Analysis Services multidimensional data.</span></span> <span data-ttu-id="f3415-123">Pour plus d’informations, consultez [Créer des connexions de données Analysis Services (PerformancePoint Services)](https://go.microsoft.com/fwlink/?linkid=232471).</span><span class="sxs-lookup"><span data-stu-id="f3415-123">For more information, [Create an Analysis Services data connection (PerformancePoint Services)](https://go.microsoft.com/fwlink/?linkid=232471).</span></span>  
  
### <a name="sql-server-data-tools"></a><span data-ttu-id="f3415-124">SQL Server Data Tools</span><span class="sxs-lookup"><span data-stu-id="f3415-124">SQL Server Data Tools</span></span>  
 <span data-ttu-id="f3415-125">Le modèle et les concepteurs de rapports utilisent des outils de données SQL Server pour créer des solutions qui incluent des modèles MDX.</span><span class="sxs-lookup"><span data-stu-id="f3415-125">Model and report designers use SQL Server Data Tools to build solutions that include multidimensional models.</span></span> <span data-ttu-id="f3415-126">Le déploiement de la solution sur une instance Analysis Services permet de crée la base de données à laquelle vous allez vous connecter par la suite à partir d'Excel, Reporting Services et d'autres applications clientes Business Intelligence.</span><span class="sxs-lookup"><span data-stu-id="f3415-126">Deploying the solution to an Analysis Services instance is what creates the database that you subsequently connect to from Excel, Reporting Services, and other business intelligence client applications.</span></span>  
  
 <span data-ttu-id="f3415-127">SQL Server Data Tools sont générés sur un shell Visual Studio et utilisent des projets pour organiser et contenir le modèle.</span><span class="sxs-lookup"><span data-stu-id="f3415-127">SQL Server Data Tools is built on a Visual Studio shell and uses projects to organize and contain the model.</span></span> <span data-ttu-id="f3415-128">Pour plus d’informations, consultez [Création de modèles MDX à l’aide des Outils de données SQL Server &#40;SSDT&#41;](../creating-multidimensional-models-using-sql-server-data-tools-ssdt.md).</span><span class="sxs-lookup"><span data-stu-id="f3415-128">For more information, see [Creating Multidimensional Models Using SQL Server Data Tools &#40;SSDT&#41;](../creating-multidimensional-models-using-sql-server-data-tools-ssdt.md).</span></span>  
  
### <a name="sql-server-management-studio"></a><span data-ttu-id="f3415-129">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f3415-129">SQL Server Management Studio</span></span>  
 <span data-ttu-id="f3415-130">Pour les administrateurs de base de données, SQL Server Management Studio est un environnement intégré qui gère vos instances de SQL Server, y compris les instances d'Analysis Services et les bases de données multidimensionnelles.</span><span class="sxs-lookup"><span data-stu-id="f3415-130">For database administrators, SQL Server Management Studio is an integrated environment for managing your SQL Server instances, including instances of Analysis Services and multidimensional databases.</span></span> <span data-ttu-id="f3415-131">Pour plus d’informations, consultez [SQL Server Management Studio](../../../ssms/sql-server-management-studio-ssms.md) et [Se connecter à Analysis Services](../../instances/connect-to-analysis-services.md).</span><span class="sxs-lookup"><span data-stu-id="f3415-131">For more information, see [SQL Server Management Studio](../../../ssms/sql-server-management-studio-ssms.md) and [Connect to Analysis Services](../../instances/connect-to-analysis-services.md).</span></span>  
  
##  <a name="query-languages"></a><a name="bkmk_querylang"></a><span data-ttu-id="f3415-132">Langages de requête</span><span class="sxs-lookup"><span data-stu-id="f3415-132">Query Languages</span></span>  
 <span data-ttu-id="f3415-133">MDX est un langage de requête et de calcul standard utilisé pour récupérer les données des bases de données OLAP.</span><span class="sxs-lookup"><span data-stu-id="f3415-133">MDX is an industry standard query and calculation language used to retrieve data from OLAP databases.</span></span> <span data-ttu-id="f3415-134">Dans Analysis Services, MDX est le langage de requête utilisé pour récupérer les données, mais prend également en charge la définition des données et la manipulation de données.</span><span class="sxs-lookup"><span data-stu-id="f3415-134">In Analysis Services, MDX is the query language used to retrieve data, but also supports data definition and data manipulation.</span></span> <span data-ttu-id="f3415-135">Les éditeurs MDX sont générés dans SQL Server Management Studio, Reporting Services et les outils de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f3415-135">MDX editors are built into SQL Server Management Studio, Reporting Services, and SQL Server Data Tools.</span></span> <span data-ttu-id="f3415-136">Vous pouvez utiliser les éditeurs MDX pour créer des requêtes ad hoc ou un script réutilisable si l'opération de données est répétée.</span><span class="sxs-lookup"><span data-stu-id="f3415-136">You can use the MDX editors to create ad hoc queries or reusable script if the data operation is repeatable.</span></span>  
  
 <span data-ttu-id="f3415-137">Certains outils et applications, par exemple Excel, utilisent une instruction MDX pour interroger en interne une source de données Analysis Services.</span><span class="sxs-lookup"><span data-stu-id="f3415-137">Some tools and applications, such as Excel, use MDX constructs internally to query an Analysis Services data source.</span></span> <span data-ttu-id="f3415-138">Vous pouvez également utiliser MDX par programmation en incluant l'instruction MDX dans une requête XMLA Execute.</span><span class="sxs-lookup"><span data-stu-id="f3415-138">You can also use MDX programmatically, by enclosing MDX statement in an XMLA Execute request.</span></span>  
  
 <span data-ttu-id="f3415-139">Pour plus d'informations sur MDX, consultez les liens suivants :</span><span class="sxs-lookup"><span data-stu-id="f3415-139">The following links provide more information about MDX:</span></span>  
  
 [<span data-ttu-id="f3415-140">Interrogation de données multidimensionnelles à l'aide de MDX</span><span class="sxs-lookup"><span data-stu-id="f3415-140">Querying Multidimensional Data with MDX</span></span>](querying-multidimensional-data-with-mdx.md)  
  
 [<span data-ttu-id="f3415-141">Concepts clés de MDX &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f3415-141">Key Concepts in MDX &#40;Analysis Services&#41;</span></span>](../key-concepts-in-mdx-analysis-services.md)  
  
 [<span data-ttu-id="f3415-142">Principes de base des requêtes MDX &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f3415-142">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-query-fundamentals-analysis-services.md)  
  
 [<span data-ttu-id="f3415-143">Principes de base des scripts MDX &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f3415-143">MDX Scripting Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-scripting-fundamentals-analysis-services.md)  
  
##  <a name="programmatic-interfaces"></a><a name="bkmk_api"></a><span data-ttu-id="f3415-144">Interfaces de programmation</span><span class="sxs-lookup"><span data-stu-id="f3415-144">Programmatic Interfaces</span></span>  
 <span data-ttu-id="f3415-145">Lorsque vous développez une application personnalisée qui utilise des données multidimensionnelles, votre approche pour accéder aux données tombera très probablement dans l'une des catégories suivantes :</span><span class="sxs-lookup"><span data-stu-id="f3415-145">If you are building a custom application that uses multidimensional data, your approach for accessing the data will most likely fall into one of the following categories:</span></span>  
  
-   <span data-ttu-id="f3415-146">**XMLA**.</span><span class="sxs-lookup"><span data-stu-id="f3415-146">**XMLA**.</span></span> <span data-ttu-id="f3415-147">Utilisez XMLA lorsque vous avez besoin d'assurer la compatibilité avec une grande variété de systèmes d'exploitation et de protocoles.</span><span class="sxs-lookup"><span data-stu-id="f3415-147">Use XMLA when you require compatibility with a wide variety of operating systems and protocols.</span></span> <span data-ttu-id="f3415-148">XMLA offre une plus grande souplesse, mais souvent au détriment des performances et de la facilité de programmation.</span><span class="sxs-lookup"><span data-stu-id="f3415-148">XMLA offers the greatest flexibility, but often at the cost of improved performance and ease of programming.</span></span>  
  
-   <span data-ttu-id="f3415-149">**Bibliothèques clientes**.</span><span class="sxs-lookup"><span data-stu-id="f3415-149">**Client libraries**.</span></span> <span data-ttu-id="f3415-150">Utilisez les bibliothèques clientes Analysis Services, telles qu'ADOMD.NET, AMO et OLE DB lorsque vous souhaitez accéder aux données par programmation à partir des applications clientes qui s'exécutent sur un système d'exploitation Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="f3415-150">Use Analysis Services client libraries, such as ADOMD.NET, AMO, and OLE DB when you want to access data programmatically from client applications that run on a Microsoft Windows operating system.</span></span> <span data-ttu-id="f3415-151">Les bibliothèques clientes encapsulent XMLA avec un modèle objet et des optimisations qui offrent de meilleures performances.</span><span class="sxs-lookup"><span data-stu-id="f3415-151">The client libraries wrap XMLA with an object model and optimizations that provide better performance.</span></span>  
  
     <span data-ttu-id="f3415-152">Les bibliothèques clientes ADOMD.NET et AMO (Analysis Management Objects) sont destinées aux applications écrites en code managé.</span><span class="sxs-lookup"><span data-stu-id="f3415-152">ADOMD.NET and AMO client libraries are for applications written in managed code.</span></span> <span data-ttu-id="f3415-153">Utilisez OLE DB pour Analysis Services si votre application est écrite en code natif.</span><span class="sxs-lookup"><span data-stu-id="f3415-153">Use OLE DB for Analysis Services if your application is written in native code.</span></span>  
  
 <span data-ttu-id="f3415-154">Le tableau suivant fournit des détails supplémentaires et des liens sur les bibliothèques clientes utilisées pour connecter Analysis Services à une application personnalisée.</span><span class="sxs-lookup"><span data-stu-id="f3415-154">The following table provides additional detail and links about the client libraries used for connecting Analysis Services to a custom application.</span></span>  
  
|<span data-ttu-id="f3415-155">Interface</span><span class="sxs-lookup"><span data-stu-id="f3415-155">Interface</span></span>|<span data-ttu-id="f3415-156">Description</span><span class="sxs-lookup"><span data-stu-id="f3415-156">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f3415-157">Objets AMO (Analysis Management Objects) Analysis Services</span><span class="sxs-lookup"><span data-stu-id="f3415-157">Analysis Services Management Objects (AMO)</span></span>|<span data-ttu-id="f3415-158">AMO est le modèle d'objet principal pour administrer des instances d'Analysis Services et des bases de données multidimensionnelles dans le code.</span><span class="sxs-lookup"><span data-stu-id="f3415-158">AMO is the primary object model for administering Analysis Services instances and multidimensional databases in code.</span></span> <span data-ttu-id="f3415-159">Par exemple, SQL Server Management Studio utilise AMO pour prendre en charge l'administration de serveur et de base de données.</span><span class="sxs-lookup"><span data-stu-id="f3415-159">For example, SQL Server Management Studio uses AMO to support server and database administration.</span></span> <span data-ttu-id="f3415-160">Pour plus d’informations, consultez [Développement avec AMO &#40;Analysis Management Objects&#41;](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo).</span><span class="sxs-lookup"><span data-stu-id="f3415-160">For more information, see [Developing with Analysis Management Objects &#40;AMO&#41;](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo).</span></span>|  
|<span data-ttu-id="f3415-161">ADOMD.NET</span><span class="sxs-lookup"><span data-stu-id="f3415-161">ADOMD.NET</span></span>|<span data-ttu-id="f3415-162">ADOMD.NET est le modèle d'objet principal de création et d'accès aux données multidimensionnelles dans les applications personnalisées.</span><span class="sxs-lookup"><span data-stu-id="f3415-162">ADOMD.NET is the primary object model creating and accessing multidimensional data in custom applications.</span></span> <span data-ttu-id="f3415-163">Vous pouvez utiliser ADOMD.NET dans une application cliente managée pour récupérer des informations [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] à l'aide des interfaces d'accès aux données classiques de Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f3415-163">You can use ADOMD.NET in a managed client application to retrieve [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] information using common Microsoft .NET Framework data access interfaces.</span></span> <span data-ttu-id="f3415-164">Pour plus d’informations, consultez [Développement avec ADOMD.NET](https://docs.microsoft.com/bi-reference/adomd/developing-with-adomd-net) et [Programmation du client ADOMD.NET](https://docs.microsoft.com/analysis-services/adomd/multidimensional-models-adomd-net-client/adomd-net-client-programming).</span><span class="sxs-lookup"><span data-stu-id="f3415-164">For more information, see [Developing with ADOMD.NET](https://docs.microsoft.com/bi-reference/adomd/developing-with-adomd-net) and [ADOMD.NET Client Programming](https://docs.microsoft.com/analysis-services/adomd/multidimensional-models-adomd-net-client/adomd-net-client-programming).</span></span>|  
|<span data-ttu-id="f3415-165">Fournisseur OLE DB pour Analysis Services (MSOLAP.dll)</span><span class="sxs-lookup"><span data-stu-id="f3415-165">Analysis Services OLE DB Provider (MSOLAP.dll)</span></span>|<span data-ttu-id="f3415-166">Vous pouvez utiliser le fournisseur OLE DB natif pour accéder à [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] par programmation à partir d'une API non-gérée.</span><span class="sxs-lookup"><span data-stu-id="f3415-166">You can use the native OLE DB provider to access [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] programmatically from a non-managed API.</span></span> <span data-ttu-id="f3415-167">Pour plus d’informations, consultez [Fournisseur OLE DB Analysis Services &#40;Analysis Services - Données multidimensionnelles&#41;](../../dev-guide/analysis-services-ole-db-provider-analysis-services-multidimensional-data.md).</span><span class="sxs-lookup"><span data-stu-id="f3415-167">For more information, see [Analysis Services OLE DB Provider &#40;Analysis Services - Multidimensional Data&#41;](../../dev-guide/analysis-services-ole-db-provider-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="f3415-168">Ensembles de lignes de schéma</span><span class="sxs-lookup"><span data-stu-id="f3415-168">Schema Rowsets</span></span>|<span data-ttu-id="f3415-169">Les tables d'ensemble de lignes de schéma sont des structures de données qui contiennent des informations descriptives sur un modèle multidimensionnel déployé sur le serveur, ainsi que des informations sur l'activité du serveur.</span><span class="sxs-lookup"><span data-stu-id="f3415-169">Schema rowset tables are data structures that contain descriptive information about a multidimensional model that is deployed on the server, as well as information about current activity on the server.</span></span> <span data-ttu-id="f3415-170">En tant que programmeur, vous pouvez interroger les tables d'ensemble de lignes de schéma dans les applications clientes pour examiner des métadonnées stockées et récupérer des informations de support et de surveillance sur une instance de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f3415-170">As a programmer, you can query schema rowset tables in client applications to examine metadata stored on, and retrieve support and monitoring information from, an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="f3415-171">Vous pouvez utiliser les ensembles de lignes de schéma avec ces interfaces de programmation : OLE DB, OLE DB pour Analysis Services, OLE DB pour l'exploration de données, ou XMLA.</span><span class="sxs-lookup"><span data-stu-id="f3415-171">You can use schema rowsets with these programmatic interfaces: OLE DB, OLE DB for Analysis Services, OLE DB for Data Mining, or XMLA.</span></span> <span data-ttu-id="f3415-172">Pour plus d’informations, consultez [Ensembles de lignes de schéma Analysis Services](https://docs.microsoft.com/bi-reference/schema-rowsets/analysis-services-schema-rowsets).</span><span class="sxs-lookup"><span data-stu-id="f3415-172">For more information, see [Analysis Services Schema Rowsets](https://docs.microsoft.com/bi-reference/schema-rowsets/analysis-services-schema-rowsets).</span></span><br /><br /> <span data-ttu-id="f3415-173">Voici les approches possibles pour utiliser des ensembles de lignes de schéma :</span><span class="sxs-lookup"><span data-stu-id="f3415-173">The following list explains several approaches for using schema rowsets:</span></span><br /><br /> <span data-ttu-id="f3415-174">Exécuter des requêtes DMV dans SQL Server Management Studio ou dans des rapports personnalisés pour accéder aux ensembles de lignes de schéma à l'aide de la syntaxe SQL.</span><span class="sxs-lookup"><span data-stu-id="f3415-174">Run DMV queries in SQL Server Management Studio or in custom reports to access schema rowsets using SQL syntax.</span></span> <span data-ttu-id="f3415-175">Pour plus d’informations, consultez [Utiliser des vues de gestion dynamique &#40;DMVs&#41; pour surveiller Analysis Services](../../instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md).</span><span class="sxs-lookup"><span data-stu-id="f3415-175">For more information, see [Use Dynamic Management Views &#40;DMVs&#41; to Monitor Analysis Services](../../instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md).</span></span><br /><br /> <span data-ttu-id="f3415-176">Écrire du code ADOMD.NET qui appelle un ensemble de lignes de schéma.</span><span class="sxs-lookup"><span data-stu-id="f3415-176">Write ADOMD.NET code that calls a schema rowset.</span></span><br /><br /> <span data-ttu-id="f3415-177">Exécuter directement la méthode XMLA `Discover` sur une instance de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] pour récupérer les informations sur l'ensemble de lignes de schéma.</span><span class="sxs-lookup"><span data-stu-id="f3415-177">Run the XMLA `Discover` method directly against an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance to retrieve schema rowset information.</span></span> <span data-ttu-id="f3415-178">Pour plus d’informations, consultez [Méthode Discover &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover).</span><span class="sxs-lookup"><span data-stu-id="f3415-178">For more information, see [Discover Method &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover).</span></span>|  
|<span data-ttu-id="f3415-179">XMLA</span><span class="sxs-lookup"><span data-stu-id="f3415-179">XMLA</span></span>|<span data-ttu-id="f3415-180">XMLA est l'API de niveau le plus bas à la disposition d'un programmeur Analysis Services, et le dénominateur commun sous-jacent de toutes les méthodologies d'accès aux données Analysis Services.</span><span class="sxs-lookup"><span data-stu-id="f3415-180">XMLA is the lowest level API available to an Analysis Services programmer, and is the common denominator that underlies all Analysis Services data access methodologies.</span></span> <span data-ttu-id="f3415-181">XMLA est une norme de l'industrie, un protocole XML basé sur SOAP qui prend en charge l'accès universel aux données sur n'importe quelle source de données multidimensionnelle standard disponible via une connexion HTTP.</span><span class="sxs-lookup"><span data-stu-id="f3415-181">XMLA is an industry standard, SOAP based XML protocol that supports universal data access to any standard multidimensional data source available over an HTTP connection.</span></span> <span data-ttu-id="f3415-182">Elle utilise SOAP pour formuler les requêtes et les réponses pour les données multidimensionnelles.</span><span class="sxs-lookup"><span data-stu-id="f3415-182">It uses SOAP to formulate requests and responses for multidimensional data.</span></span> <span data-ttu-id="f3415-183">Si votre application s'exécute sur une plateforme autre que Windows, vous pouvez utiliser XMLA pour accéder à une base de données multidimensionnelle qui s'exécute sur un serveur Windows de votre réseau.</span><span class="sxs-lookup"><span data-stu-id="f3415-183">If your application runs on a non-Windows platform, you can use XMLA to access a multidimensional database that is running on a Windows server on your network.</span></span> <span data-ttu-id="f3415-184">Pour plus d’informations, consultez [Développement avec XMLA dans Analysis Services](../../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md).</span><span class="sxs-lookup"><span data-stu-id="f3415-184">For more information, see [Developing with XMLA in Analysis Services](../../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md).</span></span>|  
|<span data-ttu-id="f3415-185">ASSL (Analysis Services Scripting Language)</span><span class="sxs-lookup"><span data-stu-id="f3415-185">Analysis Services Scripting Language (ASSL)</span></span>|<span data-ttu-id="f3415-186">ASSL est un terme descriptif qui s'applique aux extensions Analysis Services du protocole XMLA.</span><span class="sxs-lookup"><span data-stu-id="f3415-186">ASSL is a descriptive term that applies to Analysis Services extensions of the XMLA protocol.</span></span> <span data-ttu-id="f3415-187">Les extensions ASSL permettent à Analysis Services d'utiliser des éléments XMLA dépassant les fonctions de base du protocole et autorisant la prise en charge de la définition, de la manipulation et du contrôle des données.</span><span class="sxs-lookup"><span data-stu-id="f3415-187">ASSL extensions enable Analysis Services to use XMLA constructs beyond the basic provisions of the protocol, adding data definition, data manipulation, and data control support.</span></span>  <span data-ttu-id="f3415-188">Alors que les méthodes Execute et Discover sont décrites par le protocole XMLA, ASSL ajoute la fonction suivante :</span><span class="sxs-lookup"><span data-stu-id="f3415-188">Whereas the Execute and Discover methods are described by the XMLA protocol, ASSL adds the following capability:</span></span><br /><br /> <span data-ttu-id="f3415-189">Script XMLA</span><span class="sxs-lookup"><span data-stu-id="f3415-189">XMLA script</span></span><br /><br /> <span data-ttu-id="f3415-190">Définition d'objets XMLA</span><span class="sxs-lookup"><span data-stu-id="f3415-190">XMLA object definitions</span></span><br /><br /> <span data-ttu-id="f3415-191">Commandes XMLA</span><span class="sxs-lookup"><span data-stu-id="f3415-191">XMLA commands</span></span><br /><br /> <br /><br /> <span data-ttu-id="f3415-192">Pour plus d'informations, consultez [Développement avec le langage de script Analysis Services &#40;ASSL&#41;](../scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).</span><span class="sxs-lookup"><span data-stu-id="f3415-192">For more information, see [Developing with Analysis Services Scripting Language &#40;ASSL&#41;](../scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f3415-193">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3415-193">See Also</span></span>  
 <span data-ttu-id="f3415-194">[Se connecter à Analysis Services](../../instances/connect-to-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="f3415-194">[Connect to Analysis Services](../../instances/connect-to-analysis-services.md) </span></span>  
 <span data-ttu-id="f3415-195">[Développement avec le langage de script Analysis Services &#40;ASSL&#41;](../scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md) </span><span class="sxs-lookup"><span data-stu-id="f3415-195">[Developing with Analysis Services Scripting Language &#40;ASSL&#41;](../scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md) </span></span>  
 <span data-ttu-id="f3415-196">[Développement avec XMLA dans Analysis Services](../../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="f3415-196">[Developing with XMLA in Analysis Services](../../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="f3415-197">Accès aux données de modèle tabulaire</span><span class="sxs-lookup"><span data-stu-id="f3415-197">Tabular Model Data Access</span></span>](../../tabular-models/tabular-model-data-access.md)  
  
  