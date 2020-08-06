---
title: Créer un rapport d’extraction (RDLC) avec des paramètres à l’aide de ReportViewer (didacticiel SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 628c8775-c62d-45ac-b349-23db86fa4e6c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 02864ea8bdd80d6f46b7aad552fa30241322370c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706264"
---
# <a name="create-a-drillthrough-rdlc-report-with-parameters-using-reportviewer-ssrs-tutorial"></a><span data-ttu-id="3aed6-102">Créer un rapport d'extraction (RDLC) avec des paramètres à l'aide de ReportViewer (didacticiel SSRS)</span><span class="sxs-lookup"><span data-stu-id="3aed6-102">Create a Drillthrough (RDLC) Report with Parameters using ReportViewer (SSRS Tutorial)</span></span>
  <span data-ttu-id="3aed6-103">Un rapport [d’extraction](https://technet.microsoft.com/library/ff519554.aspx) est un rapport que l’utilisateur ouvre en cliquant sur un lien situé dans un autre rapport.</span><span class="sxs-lookup"><span data-stu-id="3aed6-103">A [drillthrough](https://technet.microsoft.com/library/ff519554.aspx) report is a report that a user opens by clicking a link within another report.</span></span> <span data-ttu-id="3aed6-104">Il contient en général des détails sur un élément figurant dans le rapport de synthèse d'origine.</span><span class="sxs-lookup"><span data-stu-id="3aed6-104">Drillthrough reports commonly contain details about an item that is contained in an original summary report.</span></span> <span data-ttu-id="3aed6-105">Ce tutoriel vous guide tout au long des leçons suivantes pour créer un rapport d’extraction avec des paramètres et une requête, en [mode local](local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md).</span><span class="sxs-lookup"><span data-stu-id="3aed6-105">This tutorial will walk you through the following lessons of creating a drillthrough report with parameters and a query, in [local mode reporting](local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3aed6-106">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3aed6-106">Requirements</span></span>  
 <span data-ttu-id="3aed6-107">Pour utiliser cette procédure pas à pas, vous devez avoir accès à l’exemple de base de données **AdventureWorks2008** .</span><span class="sxs-lookup"><span data-stu-id="3aed6-107">To use this walkthrough, you must have access to the **AdventureWorks2008** sample database.</span></span> <span data-ttu-id="3aed6-108">La requête utilisée dans cette procédure pas à pas fonctionne également avec la base de données **AdventureWorks2012** .</span><span class="sxs-lookup"><span data-stu-id="3aed6-108">The query used in this walkthrough will also work with **AdventureWorks2012** database.</span></span> <span data-ttu-id="3aed6-109">Pour plus d’informations sur l’obtention de l’exemple de base de données **AdventureWorks2008** , consultez [procédure pas à pas : installation de la base de données AdventureWorks](https://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx) pour Microsoft Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="3aed6-109">For more information about how to get the **AdventureWorks2008** sample database, see [Walkthrough: Installing the AdventureWorks Database](https://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx) for Microsoft Visual Studio 2010.</span></span>  
  
 <span data-ttu-id="3aed6-110">Cette procédure pas à pas part du principe que vous connaissez les requêtes Transaction-SQL et les objets ADO.NET [DataSet](https://msdn.microsoft.com/library/system.data.dataset\(v=vs.100\).aspx) et [DataTable](https://msdn.microsoft.com/library/system.data.datatable\(v=vs.100\).aspx) .</span><span class="sxs-lookup"><span data-stu-id="3aed6-110">This walkthrough assumes that you are familiar with Transaction-SQL queries and ADO.NET [DataSet](https://msdn.microsoft.com/library/system.data.dataset\(v=vs.100\).aspx) and [DataTable](https://msdn.microsoft.com/library/system.data.datatable\(v=vs.100\).aspx) objects.</span></span>  
  
 <span data-ttu-id="3aed6-111">Utilisez Visual Studio 2010 ou Visual Studio 2012, ainsi que le modèle de site Web ASP.NET. pour créer une page Web ASP.NET avec un contrôle ReportViewer.</span><span class="sxs-lookup"><span data-stu-id="3aed6-111">Use Visual Studio 2010, or Visual Studio 2012, and the ASP.NET website template to create an ASP.NET webpage with a ReportViewer control.</span></span> <span data-ttu-id="3aed6-112">Le contrôle est configuré en vue d'afficher un rapport que vous créez.</span><span class="sxs-lookup"><span data-stu-id="3aed6-112">The control is configured to view a report that you create.</span></span> <span data-ttu-id="3aed6-113">Pour cette procédure pas à pas, vous créez l'application dans Microsoft Visual C#.</span><span class="sxs-lookup"><span data-stu-id="3aed6-113">For this walkthrough, you create the application in Microsoft Visual C#.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="3aed6-114">Tâches</span><span class="sxs-lookup"><span data-stu-id="3aed6-114">Tasks</span></span>  
 <span data-ttu-id="3aed6-115">[Leçon 1 : créer un nouveau site Web](../reporting-services/lesson-1-create-a-new-web-site.md) </span><span class="sxs-lookup"><span data-stu-id="3aed6-115">[Lesson 1: Create a New Web Site](../reporting-services/lesson-1-create-a-new-web-site.md) </span></span>  
 <span data-ttu-id="3aed6-116">[Leçon 2 : définir une connexion de données et une table de données pour le rapport parent](../reporting-services/lesson-2-define-a-data-connection-and-data-table-for-parent-report.md) </span><span class="sxs-lookup"><span data-stu-id="3aed6-116">[Lesson 2: Define a Data Connection and Data Table for Parent Report](../reporting-services/lesson-2-define-a-data-connection-and-data-table-for-parent-report.md) </span></span>  
 <span data-ttu-id="3aed6-117">[Leçon 3 : concevoir le rapport parent à l’aide de l’Assistant Rapport](../reporting-services/lesson-3-design-the-parent-report-using-the-report-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="3aed6-117">[Lesson 3: Design the Parent Report using the Report Wizard](../reporting-services/lesson-3-design-the-parent-report-using-the-report-wizard.md) </span></span>  
 <span data-ttu-id="3aed6-118">[Leçon 4 : définir une connexion de données et une table de données pour le rapport enfant](../reporting-services/lesson-4-define-a-data-connection-and-data-table-for-child-report.md) </span><span class="sxs-lookup"><span data-stu-id="3aed6-118">[Lesson 4: Define a Data Connection and Data Table for Child Report](../reporting-services/lesson-4-define-a-data-connection-and-data-table-for-child-report.md) </span></span>  
 <span data-ttu-id="3aed6-119">[Leçon 5 : concevoir le rapport enfant à l’aide de l’Assistant Rapport](../reporting-services/lesson-5-design-the-child-report-using-the-report-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="3aed6-119">[Lesson 5: Design the Child Report using the Report Wizard](../reporting-services/lesson-5-design-the-child-report-using-the-report-wizard.md) </span></span>  
 <span data-ttu-id="3aed6-120">[Leçon 6 : ajouter un contrôle ReportViewer à l’application](../reporting-services/lesson-6-add-a-reportviewer-control-to-the-application.md) </span><span class="sxs-lookup"><span data-stu-id="3aed6-120">[Lesson 6: Add a ReportViewer Control to the Application](../reporting-services/lesson-6-add-a-reportviewer-control-to-the-application.md) </span></span>  
 <span data-ttu-id="3aed6-121">[Leçon 7 : ajouter une action d’extraction au rapport parent](../reporting-services/lesson-7-add-drillthrough-action-on-parent-report.md) </span><span class="sxs-lookup"><span data-stu-id="3aed6-121">[Lesson 7: Add Drillthrough Action on Parent Report](../reporting-services/lesson-7-add-drillthrough-action-on-parent-report.md) </span></span>  
 <span data-ttu-id="3aed6-122">[Leçon 8 : créer un filtre de données](../reporting-services/lesson-8-create-a-data-filter.md) </span><span class="sxs-lookup"><span data-stu-id="3aed6-122">[Lesson 8: Create a Data Filter](../reporting-services/lesson-8-create-a-data-filter.md) </span></span>  
 [<span data-ttu-id="3aed6-123">Leçon 9 : Générer et exécuter l'application</span><span class="sxs-lookup"><span data-stu-id="3aed6-123">Lesson 9: Build and Run the Application</span></span>](../reporting-services/lesson-9-build-and-run-the-application.md)  
  
## <a name="see-also"></a><span data-ttu-id="3aed6-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3aed6-124">See Also</span></span>  
 <span data-ttu-id="3aed6-125">[Didacticiels de Reporting Services &#40;SSRS&#41;](../reporting-services/reporting-services-tutorials-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3aed6-125">[Reporting Services Tutorials &#40;SSRS&#41;](../reporting-services/reporting-services-tutorials-ssrs.md) </span></span>  
 [<span data-ttu-id="3aed6-126">Concevoir des rapports à l’aide du Concepteur de rapports &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="3aed6-126">Design Reports with Report Designer &#40;SSRS&#41;</span></span>](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  
  