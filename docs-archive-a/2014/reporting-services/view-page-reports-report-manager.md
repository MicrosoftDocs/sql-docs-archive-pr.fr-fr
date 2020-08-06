---
title: Page vue, rapports (Gestionnaire de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4874ba29-429b-4dd4-a8cb-d4f087237dc2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4eb5733bf6ddfc8d7ba5a1d3d6f5ebe18ce85c66
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706096"
---
# <a name="view-page-reports-report-manager"></a><span data-ttu-id="5c2fb-102">Page Vue, Rapports (Gestionnaire de rapports)</span><span class="sxs-lookup"><span data-stu-id="5c2fb-102">View Page, Reports (Report Manager)</span></span>
  <span data-ttu-id="5c2fb-103">La page Afficher des rapports vous permet d'afficher un rapport.</span><span class="sxs-lookup"><span data-stu-id="5c2fb-103">Use the View page for reports to view a report.</span></span> <span data-ttu-id="5c2fb-104">Lorsque vous ouvrez pour la première fois un rapport dans le Gestionnaire de rapports, il est au format HTML.</span><span class="sxs-lookup"><span data-stu-id="5c2fb-104">When you first open a report in Report Manager, it is formatted in HTML.</span></span> <span data-ttu-id="5c2fb-105">Les rapports HTML incluent une barre d'outils Rapport qui s'affiche en haut du rapport et vous permet de parcourir les pages du rapport, d'effectuer une recherche dans un rapport et d'exporter le rapport dans un format différent.</span><span class="sxs-lookup"><span data-stu-id="5c2fb-105">HTML reports include a report toolbar that appears at the top of the report so that you can navigate through report pages, search within a report, or export the report to a different format.</span></span> <span data-ttu-id="5c2fb-106">L'illustration suivante représente la barre d'outils Rapport :</span><span class="sxs-lookup"><span data-stu-id="5c2fb-106">The following diagram shows the report toolbar.</span></span>  
  
 <span data-ttu-id="5c2fb-107">![Barre d'outils Rapports](media/htmlviewer-toolbar.gif "Barre d'outils Rapports")</span><span class="sxs-lookup"><span data-stu-id="5c2fb-107">![Report toolbar](media/htmlviewer-toolbar.gif "Report toolbar")</span></span>  
<span data-ttu-id="5c2fb-108">Barre d'outils Rapports</span><span class="sxs-lookup"><span data-stu-id="5c2fb-108">Report toolbar</span></span>  
  
 <span data-ttu-id="5c2fb-109">Dans [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], vous pouvez configurer les rapports de manière à ce qu'ils s'exécutent à la demande ou à partir d'un instantané d'exécution de rapport.</span><span class="sxs-lookup"><span data-stu-id="5c2fb-109">In [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], reports can be configured to run on demand or from a report execution snapshot.</span></span> <span data-ttu-id="5c2fb-110">Si un rapport est exécuté à la demande, le traitement des données et du rapport s'effectue à chaque ouverture.</span><span class="sxs-lookup"><span data-stu-id="5c2fb-110">If a report is run on demand, all data processing and report processing occur each time you open the report.</span></span> <span data-ttu-id="5c2fb-111">Si vous visualisez un rapport configuré de manière à ce qu'il s'exécute en tant qu'instantané d'exécution de rapport, le traitement des données s'est produit à la création de l'instantané.</span><span class="sxs-lookup"><span data-stu-id="5c2fb-111">If you view a report that is configured to run as a report execution snapshot, data processing occurred when the snapshot was created.</span></span>  
  
## <a name="exporting-reports"></a><span data-ttu-id="5c2fb-112">Exportation des rapports</span><span class="sxs-lookup"><span data-stu-id="5c2fb-112">Exporting Reports</span></span>  
 <span data-ttu-id="5c2fb-113">Toutes les fonctionnalités de rapport ne sont pas disponibles dans tous les formats d'exportation.</span><span class="sxs-lookup"><span data-stu-id="5c2fb-113">Not all report features are available in all of the export formats.</span></span> <span data-ttu-id="5c2fb-114">Si vous exportez un rapport HTML vers un autre format, attendez-vous à voir certaines différences d'affichage du rapport.</span><span class="sxs-lookup"><span data-stu-id="5c2fb-114">If you export an HTML report to another format, you can expect to see some differences in how the report appears.</span></span> <span data-ttu-id="5c2fb-115">De plus, si le rapport inclut des fonctionnalités interactives (telles que les liens hypertexte, les signets et les explorateurs de documents), ces fonctionnalités peuvent ne pas être disponibles ou ne pas fonctionner de la même manière dans le nouveau format.</span><span class="sxs-lookup"><span data-stu-id="5c2fb-115">Also, if the report includes interactive features (such as hyperlinks, bookmarks, or document maps) those features might not be available or work the same way in the new format.</span></span>  
  
## <a name="generating-data-feeds-from-report-data"></a><span data-ttu-id="5c2fb-116">Génération de sources de données à partir de données de rapport</span><span class="sxs-lookup"><span data-stu-id="5c2fb-116">Generating Data Feeds from Report Data</span></span>  
 <span data-ttu-id="5c2fb-117">Vous pouvez générer des sources de données à partir de rapports.</span><span class="sxs-lookup"><span data-stu-id="5c2fb-117">You can generate data feeds from reports.</span></span> <span data-ttu-id="5c2fb-118">L'extension de rendu Atom [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] génère deux documents conformes à Atom : un document de service Atom qui répertorie les flux de données fournis par le rapport et les flux de données qui contiennent les données du rapport.</span><span class="sxs-lookup"><span data-stu-id="5c2fb-118">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Atom rendering extension generates two Atom-compliant documents: an Atom service document that lists the data feeds the report provides and the data feeds that contains the report data.</span></span> <span data-ttu-id="5c2fb-119">Les flux de données sont générés par [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] dans un format standardisé conforme à Atom 1.0, qu'il est possible de lire et d'échanger avec les applications qui utilisent des flux de données conformes à Atom.</span><span class="sxs-lookup"><span data-stu-id="5c2fb-119">The data feeds are generated by [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in a standardized Atom 1.0 compliant format that it readable and exchangeable with applications that consume Atom compliant data feeds.</span></span> <span data-ttu-id="5c2fb-120">Par exemple, le client [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] peut utiliser des flux de données générés à partir de rapports.</span><span class="sxs-lookup"><span data-stu-id="5c2fb-120">For example the [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] client can consume data feeds that are generated from reports.</span></span>  
  
## <a name="running-parameterized-reports"></a><span data-ttu-id="5c2fb-121">Exécuter des rapports paramétrables</span><span class="sxs-lookup"><span data-stu-id="5c2fb-121">Running Parameterized Reports</span></span>  
 <span data-ttu-id="5c2fb-122">Un rapport qui contient des champs d'entrée et un bouton **Afficher le rapport** est un rapport paramétrable.</span><span class="sxs-lookup"><span data-stu-id="5c2fb-122">A report that contains input fields and a **View Report** button is a parameterized report.</span></span> <span data-ttu-id="5c2fb-123">Pour afficher un rapport paramétrable, il est possible que vous deviez fournir des valeurs utilisées pour exécuter le rapport.</span><span class="sxs-lookup"><span data-stu-id="5c2fb-123">To view a parameterized report, you may need to provide values that are used to run the report.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5c2fb-124">Les instantanés d'exécution de rapport et certains formats d'exportation ne sont pas disponibles dans toutes les éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5c2fb-124">Report execution snapshots and some export formats are not available in all editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5c2fb-125">Pour plus d’informations, consultez [fonctionnalités prises en charge par les éditions de SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span><span class="sxs-lookup"><span data-stu-id="5c2fb-125">For more information, see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c2fb-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c2fb-126">See Also</span></span>  
 <span data-ttu-id="5c2fb-127">[Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="5c2fb-127">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="5c2fb-128">Aide F1 du Gestionnaire de rapports</span><span class="sxs-lookup"><span data-stu-id="5c2fb-128">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  