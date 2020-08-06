---
title: Choix entre l’accès URL et SOAP | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- SOAP [Reporting Services], vs. URL access
- Report Server Web service, application integration
- URL access [Reporting Services], vs. SOAP
- Web service [Reporting Services], application integration
ms.assetid: bccdc243-4366-4ce5-8e63-3dd6c463fa52
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8075d92c51960c36d52d1a6ed5dc742a943177ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87600675"
---
# <a name="choosing-between-url-access-and-soap"></a><span data-ttu-id="ad5af-102">Choix entre l'accès URL et SOAP</span><span class="sxs-lookup"><span data-stu-id="ad5af-102">Choosing Between URL Access and SOAP</span></span>
  <span data-ttu-id="ad5af-103">L'intégration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans des applications personnalisées peut s'avérer difficile.</span><span class="sxs-lookup"><span data-stu-id="ad5af-103">Integrating [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into custom applications can be challenging.</span></span> <span data-ttu-id="ad5af-104">Toutefois, la difficulté ne se trouve pas dans la complexité du modèle de programmation ou les API, mais dans les nombreuses méthodes possibles pour l'intégrer.</span><span class="sxs-lookup"><span data-stu-id="ad5af-104">The challenge, however, is not the complexity of the programming model or APIs, but the many possible ways to integrate it.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="ad5af-105">a été conçu dès le départ comme une plate-forme de développeur, et en tant que tel, a été créé avec une flexibilité de la programmation à l'esprit.</span><span class="sxs-lookup"><span data-stu-id="ad5af-105">was designed from the ground up as a developer platform, and as such, it is built with programming flexibility in mind.</span></span> <span data-ttu-id="ad5af-106">Avec la flexibilité apparaît le besoin de prendre des décisions importantes concernant l'intégration de la navigation entre les rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et les fonctionnalités de gestion dans vos applications de gestion existantes.</span><span class="sxs-lookup"><span data-stu-id="ad5af-106">With flexibility comes the need to make important decisions about integrating [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report navigation and management functionality into your existing business applications.</span></span>

 <span data-ttu-id="ad5af-107">![Scénarios de programmation Reporting Services](../../../2014/reporting-services/media/bk-ext-04.gif "Scénarios de programmation de Reporting Services") La programmation Reporting Services prend en charge un large éventail de scénarios.</span><span class="sxs-lookup"><span data-stu-id="ad5af-107">![Reporting Services programming scenarios](../../../2014/reporting-services/media/bk-ext-04.gif "Reporting Services programming scenarios") Reporting Services programming supports a wide range of scenarios.</span></span>

 <span data-ttu-id="ad5af-108">Il existe deux manières d'intégrer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans des applications personnalisées : l'accès URL et l'API SOAP de Reporting Services.</span><span class="sxs-lookup"><span data-stu-id="ad5af-108">There are two ways to integrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into custom applications: URL access and the Reporting Services SOAP API.</span></span> <span data-ttu-id="ad5af-109">Celle à utiliser dépend de plusieurs facteurs.</span><span class="sxs-lookup"><span data-stu-id="ad5af-109">Which to use depends on several factors.</span></span> <span data-ttu-id="ad5af-110">Dans certains cas, l'intégration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans vos applications de gestion personnalisées nécessite que vous utilisiez à la fois l'accès URL et SOAP.</span><span class="sxs-lookup"><span data-stu-id="ad5af-110">In some cases, integrating [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into your custom business applications requires a you to use both URL access and SOAP.</span></span> <span data-ttu-id="ad5af-111">Vous devez vous poser les questions suivantes :</span><span class="sxs-lookup"><span data-stu-id="ad5af-111">You should ask the following questions:</span></span>

-   <span data-ttu-id="ad5af-112">De quel type de fonctionnalités de création de rapports d'entreprise vos utilisateurs finals et vous avez-vous besoin ?</span><span class="sxs-lookup"><span data-stu-id="ad5af-112">What type of enterprise reporting functionality do you or your end users require?</span></span> <span data-ttu-id="ad5af-113">Avez-vous besoin d'une manière simple de générer et parcourir des rapports ou de fonctionnalités de gestion de serveur de rapports plus avancées dans votre solution d'entreprise personnalisée ?</span><span class="sxs-lookup"><span data-stu-id="ad5af-113">Do you need a simple way to launch and navigate reports, or do you need more advanced report server management features from your custom business solution?</span></span>

-   <span data-ttu-id="ad5af-114">Dans quel type d'environnement vos utilisateurs travaillent-ils habituellement ?</span><span class="sxs-lookup"><span data-stu-id="ad5af-114">In which type of environment do your users typically operate?</span></span> <span data-ttu-id="ad5af-115">Votre application d'entreprise est-elle une application Web ou une application Windows ?</span><span class="sxs-lookup"><span data-stu-id="ad5af-115">Is your business application a Web application or a Windows application?</span></span> <span data-ttu-id="ad5af-116">Vos utilisateurs finals peuvent-ils parvenir facilement à basculer d'un environnement Win32 vers un environnement Web ?</span><span class="sxs-lookup"><span data-stu-id="ad5af-116">How easily can your end users switch from a Win32 environment to a Web environment?</span></span> <span data-ttu-id="ad5af-117">De quel type de contrôle avez-vous besoin sur l'environnement dans lequel les rapports sont exécutés et gérés ?</span><span class="sxs-lookup"><span data-stu-id="ad5af-117">What type of control do you need over the environment in which reports are run and managed?</span></span>

 <span data-ttu-id="ad5af-118">Une fois que vous avez répondu aux questions précédentes, vous pouvez déterminer comment intégrer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans votre infrastructure informatique.</span><span class="sxs-lookup"><span data-stu-id="ad5af-118">Once you have answered the previous questions, you can decide how to integrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into your IT infrastructure.</span></span> <span data-ttu-id="ad5af-119">En général, l'accès URL est préféré pour consulter et parcourir des rapports individuels.</span><span class="sxs-lookup"><span data-stu-id="ad5af-119">Typically, URL access is preferred for viewing and navigating individual reports.</span></span> <span data-ttu-id="ad5af-120">L'accès URL vous permet de parcourir librement et rapidement des rapports sans le traitement du service Web.</span><span class="sxs-lookup"><span data-stu-id="ad5af-120">URL access enables you to freely and quickly navigate reports without the overhead of the Web service.</span></span> <span data-ttu-id="ad5af-121">De plus, l'accès URL est actuellement la seule technique de programmation qui utilise la Visionneuse HTML complète pour la navigation entre les rapports, laquelle inclut la barre d'outils Rapports.</span><span class="sxs-lookup"><span data-stu-id="ad5af-121">In addition, URL access is currently the only programming technique that uses the full HTML Viewer for report navigation, which includes the report toolbar.</span></span> <span data-ttu-id="ad5af-122">En outre, l'accès URL est plus performant que SOAP parce qu'il ignore le marshaling des demandes SOAP vers et depuis le serveur.</span><span class="sxs-lookup"><span data-stu-id="ad5af-122">In addition, URL access provides better performance than SOAP because it bypasses the marshalling of SOAP requests to and from the server.</span></span> <span data-ttu-id="ad5af-123">Dans les scénarios d'intégration qui requièrent un accès rapide et facile aux rapports avec des outils intégrés pour la consultation et la navigation, l'accès URL constitue le meilleur choix.</span><span class="sxs-lookup"><span data-stu-id="ad5af-123">In integration scenarios that require quick and easy access to reports with built-in tools for viewing and navigation, URL access is the better choice.</span></span>

> [!NOTE]
>  <span data-ttu-id="ad5af-124">L'accès URL du serveur de rapports prend en charge la Visionneuse HTML et les fonctionnalités étendues de la barre d'outils Rapports.</span><span class="sxs-lookup"><span data-stu-id="ad5af-124">Report server URL access supports HTML Viewer and the extended functionality of the report toolbar.</span></span> <span data-ttu-id="ad5af-125">L'API SOAP ne prend pas en charge ce type de rapport rendu.</span><span class="sxs-lookup"><span data-stu-id="ad5af-125">The SOAP API does not support this type of rendered report.</span></span> <span data-ttu-id="ad5af-126">Vous devez concevoir et développer votre propre barre d'outils Rapports, si vous effectuez le rendu des rapports à l'aide de SOAP.</span><span class="sxs-lookup"><span data-stu-id="ad5af-126">You need to design and develop your own report toolbar, if you render reports using SOAP.</span></span>

 <span data-ttu-id="ad5af-127">Pour plus d’informations sur la barre d’outils du rapport, consultez [Visionneuse HTML et barre d’outils Rapports](../html-viewer-and-the-report-toolbar.md).</span><span class="sxs-lookup"><span data-stu-id="ad5af-127">For more information about the report toolbar, see [HTML Viewer and the Report Toolbar](../html-viewer-and-the-report-toolbar.md).</span></span>

 <span data-ttu-id="ad5af-128">Pour plus d’informations sur l’accès URL, consultez [accès url &#40;&#41;SSRS ](../url-access-ssrs.md).</span><span class="sxs-lookup"><span data-stu-id="ad5af-128">For more information about URL access, see [URL Access &#40;SSRS&#41;](../url-access-ssrs.md).</span></span>

 <span data-ttu-id="ad5af-129">L'accès URL s'avère utile pour consulter des rapports, mais il ne fournit pas de fonctionnalités de gestion de rapports et d'espaces de noms, lesquelles peuvent s'avérer essentielles à tout scénario de création de rapports d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="ad5af-129">URL access is useful for viewing reports, but it does not provide the report and namespace management functionality that can be essential to any enterprise reporting scenario.</span></span> <span data-ttu-id="ad5af-130">Dans ce cas, les riches fonctionnalités générales de l'API SOAP de Reporting Services sont recommandées.</span><span class="sxs-lookup"><span data-stu-id="ad5af-130">In this case, the broad and rich functionality of the Reporting Services SOAP API is recommended.</span></span> <span data-ttu-id="ad5af-131">Avec l'API SOAP, vous pouvez gérer et déployer des rapports, créer des planifications, configurer des propriétés de serveur, gérer l'espace de noms du serveur de rapports, créer des abonnements, etc.</span><span class="sxs-lookup"><span data-stu-id="ad5af-131">With the SOAP API you can manage and deploy reports, create schedules, configure server properties, manage the report server namespace, create subscriptions, and more.</span></span> <span data-ttu-id="ad5af-132">L'API SOAP présente le jeu complet de fonctionnalités de gestion dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ad5af-132">The SOAP API exposes the complete set of management functionality in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="ad5af-133">L'API SOAP peut également permettre de consulter et de parcourir des rapports via la méthode <xref:ReportExecution2005.ReportExecutionService.Render%2A> de l'API.</span><span class="sxs-lookup"><span data-stu-id="ad5af-133">The SOAP API can also enable report viewing and navigation through the <xref:ReportExecution2005.ReportExecutionService.Render%2A> method of the API.</span></span> <span data-ttu-id="ad5af-134">Toutefois, la consultation de rapports via l'API SOAP n'active pas les fonctionnalités d'affichage intégrées de la barre d'outils Rapports et ne gère pas automatiquement l'interactivité des rapports que l'accès URL fournit.</span><span class="sxs-lookup"><span data-stu-id="ad5af-134">However, viewing reports through the SOAP API does not enable the built-in viewing functionality of the report toolbar, nor does it automatically handle the report interactivity that URL access provides.</span></span>

 <span data-ttu-id="ad5af-135">Pour plus d’informations sur l’API SOAP de Reporting Services, consultez [Service web Report Server](../report-server-web-service/report-server-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="ad5af-135">For more information about the Reporting Services SOAP API, see [Report Server Web Service](../report-server-web-service/report-server-web-service.md).</span></span>

 <span data-ttu-id="ad5af-136">Dans la majorité des cas, l'accès URL et les appels SOAP sont requis pour satisfaire vos besoins de création de rapports.</span><span class="sxs-lookup"><span data-stu-id="ad5af-136">In the majority of cases, URL access and SOAP calls are both required to meet your reporting needs.</span></span> <span data-ttu-id="ad5af-137">SOAP est utilisé lors de la connexion initiale à la base de données du serveur de rapports et lors de la présentation de la liste de rapports disponible dans une interface utilisateur tandis que l'accès URL est utilisé pour accéder réellement aux rapports individuels et les parcourir.</span><span class="sxs-lookup"><span data-stu-id="ad5af-137">SOAP is used when initially connecting to the report server database and presenting the available list of reports in a user interface and URL access is used to actually access and navigate individual reports.</span></span>

 <span data-ttu-id="ad5af-138">Pour obtenir un exemple de combinaison de l’accès URL et du service web à des fins de création de rapports intégrée, consultez [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889) (Exemples Reporting Services pour le produit SQL Server).</span><span class="sxs-lookup"><span data-stu-id="ad5af-138">For an example of combining URL access and the Web service to provide integrated reporting, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>

## <a name="see-also"></a><span data-ttu-id="ad5af-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad5af-139">See Also</span></span>
 <span data-ttu-id="ad5af-140">[Intégration de Reporting Services dans des applications](../../../2014/reporting-services/application-integration/integrating-reporting-services-into-applications.md) [intégrant Reporting Services à l’aide de SOAP](../application-integration/integrating-reporting-services-using-soap.md) [intégration de Reporting Services à l’aide](../application-integration/integrating-reporting-services-using-url-access.md) de la référence technique de l’accès URL [&#40;SSRS&#41;](../../../2014/reporting-services/technical-reference-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="ad5af-140">[Integrating Reporting Services into Applications](../../../2014/reporting-services/application-integration/integrating-reporting-services-into-applications.md) [Integrating Reporting Services Using SOAP](../application-integration/integrating-reporting-services-using-soap.md) [Integrating Reporting Services Using URL Access](../application-integration/integrating-reporting-services-using-url-access.md) [Technical Reference &#40;SSRS&#41;](../../../2014/reporting-services/technical-reference-ssrs.md)</span></span>

