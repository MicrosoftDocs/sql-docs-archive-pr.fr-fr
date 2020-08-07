---
title: Composant WebPart Visionneuse de rapports sur un site SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SharePoint integration [Reporting Services], viewing reports
- Web Parts [Reporting Services]
- SharePoint integration [Reporting Services], Web Parts
- Report Viewer Web Part [Reporting Services]
ms.assetid: b6341a73-172f-4632-a9e9-cc79fed3f36b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d867df9fca54a74b846c6100f4f6734cd2e28a05
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703827"
---
# <a name="report-viewer-web-part-on-a-sharepoint-site"></a><span data-ttu-id="8ca00-102">Composant WebPart Visionneuse de rapports sur un site SharePoint</span><span class="sxs-lookup"><span data-stu-id="8ca00-102">Report Viewer Web Part on a SharePoint Site</span></span>
  <span data-ttu-id="8ca00-103">Le composant WebPart Visionneuse de rapports est un composant WebPart personnalisé qui est installé par le complément [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pour les produits SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8ca00-103">The Report Viewer Web Part is a custom Web Part that is installed by the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Add-in for SharePoint Products.</span></span> <span data-ttu-id="8ca00-104">Vous pouvez utiliser le composant WebPart pour afficher les rapports, naviguer parmi ces derniers, les imprimer et les exporter sur un serveur de rapports configuré pour s'exécuter en mode intégré SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8ca00-104">You can use the Web Part to view, navigate, print, and export reports on a report server that is configured to run in SharePoint integrated mode.</span></span> <span data-ttu-id="8ca00-105">Le composant WebPart Visionneuse de rapports est associé aux fichiers de définition de rapport (. rdl) qui sont traités par un [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="8ca00-105">The Report Viewer Web Part is associated with report definition (.rdl) files that are processed by a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server.</span></span> <span data-ttu-id="8ca00-106">Vous ne pouvez pas l'utiliser avec d'autres documents de rapport que vous créez dans d'autres produits logiciels.</span><span class="sxs-lookup"><span data-stu-id="8ca00-106">You cannot use it with other report documents that you create in other software products.</span></span>  
  
 <span data-ttu-id="8ca00-107">Pour installer le composant WebPart, vous devez exécuter le programme d'installation du complément [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="8ca00-107">To install the Web Part, you must run Setup for the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Add-in.</span></span> <span data-ttu-id="8ca00-108">Vous ne devez pas installer ou désinstaller le composant WebPart indépendamment.</span><span class="sxs-lookup"><span data-stu-id="8ca00-108">You should not install or uninstall the Web Part independently.</span></span> <span data-ttu-id="8ca00-109">Celui-ci fait partie du complément et ne peut être installé que par le package d'installation du complément.</span><span class="sxs-lookup"><span data-stu-id="8ca00-109">It is part of the add-in and can only be installed through the add-in setup package.</span></span> <span data-ttu-id="8ca00-110">Le nom de fichier du composant WebPart Visionneuse de rapports est ReportViewer.dwp.</span><span class="sxs-lookup"><span data-stu-id="8ca00-110">The Report Viewer Web Part file name is ReportViewer.dwp.</span></span> <span data-ttu-id="8ca00-111">Ce fichier est situé dans le dossier Program Files\Fichiers communs\Microsoft Shared\web server extensions\12\template\features\reportserver et ne doit pas être déplacé vers d'autres dossiers.</span><span class="sxs-lookup"><span data-stu-id="8ca00-111">It is located in the Program Files\Common Files\Microsoft Shared\web server extensions\12\template\features\reportserver folder and should not be moved to other folders.</span></span>  
  
 <span data-ttu-id="8ca00-112">Pour pouvoir utiliser le composant WebPart, vous devez avoir installé et configuré le complément [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] et avoir configuré le serveur de rapports pour l'intégration SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8ca00-112">To use the Web Part, you must have installed and configured the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Add-in and configured the report server for SharePoint integration.</span></span> <span data-ttu-id="8ca00-113">Vous devez également disposer de rapports à afficher dans la visionneuse.</span><span class="sxs-lookup"><span data-stu-id="8ca00-113">You must also have reports to display in the viewer.</span></span> <span data-ttu-id="8ca00-114">Vous ne pouvez ouvrir que les rapports qui se trouvent dans une bibliothèque, un dossier de bibliothèque ou un historique de rapport, ou ceux qui sont liés entre un composant WebPart de bibliothèque et un composant WebPart Visionneuse de rapports.</span><span class="sxs-lookup"><span data-stu-id="8ca00-114">You can only open reports that are in a library, a library folder, report history, or a link from a Library Web Part to a Report Viewer Web Part.</span></span> <span data-ttu-id="8ca00-115">Vous ne pouvez pas ouvrir les rapports enregistrés en tant que pièces jointes d'un élément dans une liste personnalisée.</span><span class="sxs-lookup"><span data-stu-id="8ca00-115">You cannot open reports that are saved as an attachment to an item in a custom list.</span></span>  
  
 <span data-ttu-id="8ca00-116">Vous pouvez définir les propriétés du composant WebPart Visionneuse de rapports afin de contrôler l'apparence de la barre d'outils et des zones d'affichage, ainsi que pour lier le composant WebPart à un rapport spécifique.</span><span class="sxs-lookup"><span data-stu-id="8ca00-116">You can set properties on the Report Viewer Web Part to control the appearance of the toolbar and view areas, and to link the Web Part to a specific report.</span></span> <span data-ttu-id="8ca00-117">La visionneuse de rapports affiche soit un rapport vers lequel vous définissez un lien explicite, soit un fichier .rdl que vous ouvrez.</span><span class="sxs-lookup"><span data-stu-id="8ca00-117">The Report Viewer either shows a report that you explicitly link to it, or it shows any .rdl file that you open.</span></span>  
  
 <span data-ttu-id="8ca00-118">Vous ne pouvez pas lier plusieurs rapports à une seule instance de visionneuse de rapports, mais si vous souhaitez regrouper les rapports, vous pouvez créer un tableau de bord ou une page Web qui intègre plusieurs instances du composant WebPart Visionneuse de rapports sur une seule page.</span><span class="sxs-lookup"><span data-stu-id="8ca00-118">You cannot link multiple reports to a single Report Viewer instance, but if you want to group reports together, you can create a dashboard or a Web Part page that embeds multiple Report Viewer Web Part instances on a single page.</span></span>  
  
 <span data-ttu-id="8ca00-119">Le composant WebPart comprend une zone d'affichage, une barre d'outils, une zone réductible pour la définition des informations d'identification et des paramètres, ainsi que des propriétés.</span><span class="sxs-lookup"><span data-stu-id="8ca00-119">The Web Part includes a view area, a toolbar, a collapsible area for setting credentials and parameters, and properties.</span></span> <span data-ttu-id="8ca00-120">L'image suivante illustre le composant WebPart et l'exemple de rapport Company Sales ainsi que les options d'exportation que vous pouvez sélectionner à partir de la barre d'outils.</span><span class="sxs-lookup"><span data-stu-id="8ca00-120">The following image shows the Web Part with the sample Company Sales report and the export options that you can select from the toolbar.</span></span>  
  
 <span data-ttu-id="8ca00-121">![Composant WebPart Visionneuse de rapports](media/rs-sharepointrvwebpart.gif "Composant WebPart Visionneuse de rapports")</span><span class="sxs-lookup"><span data-stu-id="8ca00-121">![Report Viewer Web Part](media/rs-sharepointrvwebpart.gif "Report Viewer Web Part")</span></span>  
  
## <a name="web-part-components"></a><span data-ttu-id="8ca00-122">Composants WebPart</span><span class="sxs-lookup"><span data-stu-id="8ca00-122">Web Part components</span></span>  
 <span data-ttu-id="8ca00-123">La zone d'affichage montre un rapport au format HTML.</span><span class="sxs-lookup"><span data-stu-id="8ca00-123">The view area displays a report in HTML.</span></span> <span data-ttu-id="8ca00-124">Selon la configuration du composant WebPart, la zone d'affichage peut soit être agrandie à sa taille maximale afin de montrer le rapport en mode page entière, soit partager l'espace disponible avec les volets adjacents et une barre d'outils.</span><span class="sxs-lookup"><span data-stu-id="8ca00-124">Depending on how the Web Part is configured, the view area might be maximized to show the report in full-page mode, or it might share the available space with adjacent panes and a toolbar.</span></span>  
  
 <span data-ttu-id="8ca00-125">La barre d'outils fournit des fonctionnalités de navigation entre les pages, de recherche, de zoom et d'exportation, de sorte que vous puissiez afficher un rapport dans un autre format d'application.</span><span class="sxs-lookup"><span data-stu-id="8ca00-125">The toolbar provides page navigation, search, zoom, and export features so that you can view a report in another application format.</span></span> <span data-ttu-id="8ca00-126">Elle fournit également une fonctionnalité d'impression facultative, elle permet d'obtenir une sortie imprimée paginée pour les rapports HTML et de modifier les paramètres relatifs à la mise en page et aux marges.</span><span class="sxs-lookup"><span data-stu-id="8ca00-126">It also provides optional print functionality, offering paginated print output for HTML reports and the ability to change page layout and margin settings.</span></span> <span data-ttu-id="8ca00-127">Le menu**Imprimer**, **Ouvrir avec le Générateur de rapports, S’abonner**, **Exporter** et **Imprimer** .</span><span class="sxs-lookup"><span data-stu-id="8ca00-127">**Open with Report Builder, Subscribe**, **Export**, and **Print** are provided in the **Actions** menu on the toolbar.</span></span> <span data-ttu-id="8ca00-128">Les contrôles de navigation entre les pages et de zoom se trouvent directement sur la barre d'outils.</span><span class="sxs-lookup"><span data-stu-id="8ca00-128">Page navigation and zoom controls are directly on the toolbar.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8ca00-129">Vous ne pouvez pas personnaliser la barre d'outils sauf si vous écrivez le code correspondant ; toutefois, vous pouvez définir des propriétés permettant de masquer une partie ou l'ensemble de ses contrôles.</span><span class="sxs-lookup"><span data-stu-id="8ca00-129">You cannot customize the toolbar unless you write code to do so, but you can set properties to hide all or some of its controls.</span></span>  
  
### <a name="export-action-on-the-report-toolbar"></a><span data-ttu-id="8ca00-130">Action d'exportation sur la barre d'outils Rapport</span><span class="sxs-lookup"><span data-stu-id="8ca00-130">Export Action on the Report Toolbar</span></span>  
 <span data-ttu-id="8ca00-131">Dans le menu**Exporter** , la commande **Exporter** affiche les formats d’application associés aux extensions de rendu déployées sur un serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="8ca00-131">**Export** on the **Actions** menu shows application formats that are associated with rendering extensions deployed on a report server.</span></span> <span data-ttu-id="8ca00-132">Pour déterminer si un format spécifique est disponible, vous pouvez ajouter ou supprimer une extension de rendu sur le serveur de rapports ; par ailleurs, vous pouvez également modifier les paramètres de configuration afin de supprimer un format d'exportation particulier de la liste.</span><span class="sxs-lookup"><span data-stu-id="8ca00-132">To determine the availability of a specific format, you can add or remove a rendering extension on the report server, or you can modify configuration settings to remove a particular export format from the list.</span></span> <span data-ttu-id="8ca00-133">Vous pouvez également spécifier des paramètres de configuration sur le serveur de rapports afin de contrôler les formats disponibles.</span><span class="sxs-lookup"><span data-stu-id="8ca00-133">You can also specify configuration settings on the report server to control which formats are available.</span></span> <span data-ttu-id="8ca00-134">Vous pouvez modifier le comportement par défaut d'un format spécifique en ajoutant et en modifiant les paramètres de configuration de l'extension de rendu correspondante.</span><span class="sxs-lookup"><span data-stu-id="8ca00-134">You can modify the default behavior of a specific format by adding and modifying configuration settings for that rendering extension.</span></span>  
  
### <a name="print-action-on-the-report-toolbar"></a><span data-ttu-id="8ca00-135">Action d'impression sur la barre d'outils Rapport</span><span class="sxs-lookup"><span data-stu-id="8ca00-135">Print Action on the Report Toolbar</span></span>  
 <span data-ttu-id="8ca00-136">La commande**Imprimer** du menu **Actions** fournit des fonctionnalités d’impression personnalisées via [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8ca00-136">**Print** on the **Actions** menu is custom print functionality that is provided through [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="8ca00-137">Quand vous cliquez sur **Imprimer**, un contrôle d’impression ActiveX côté client est téléchargé sur l’ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="8ca00-137">When you click **Print**, an ActiveX client-side print control is downloaded to the client computer.</span></span> <span data-ttu-id="8ca00-138">Dans la plupart des cas, l’utilisateur qui clique sur **Imprimer** doit avoir les autorisations d’administrateur sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8ca00-138">In most cases, the user who clicks **Print** must have Administrator permissions on the local computer.</span></span> <span data-ttu-id="8ca00-139">Il est usuel de restreindre les téléchargements de contrôles ActiveX aux utilisateurs qui disposent d'autorisations d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="8ca00-139">It is common practice to restrict ActiveX control downloads to only those users who have Administrator permissions.</span></span> <span data-ttu-id="8ca00-140">Vous pouvez utiliser l’administration centrale de SharePoint pour activer ou désactiver le téléchargement du contrôle d’impression côté client.</span><span class="sxs-lookup"><span data-stu-id="8ca00-140">You can use SharePoint Central Administration to enable or disable the download of the client-side print control.</span></span>  
  
### <a name="find-action-on-the-report-toolbar"></a><span data-ttu-id="8ca00-141">Action de Recherche sur la barre d'outils Rapport</span><span class="sxs-lookup"><span data-stu-id="8ca00-141">Find Action on the Report Toolbar</span></span>  
 <span data-ttu-id="8ca00-142">La commande**Rechercher** du menu **Actions** permet d’accéder à un emplacement cible dans le rapport.</span><span class="sxs-lookup"><span data-stu-id="8ca00-142">**Find** on the **Actions** menu provides a way to move to a target location in the report.</span></span> <span data-ttu-id="8ca00-143">Vous pouvez rechercher un contenu dans un rapport en tapant un mot ou une expression que vous souhaitez rechercher.</span><span class="sxs-lookup"><span data-stu-id="8ca00-143">You can search for content in a report by typing a word or phrase that you want to find.</span></span> <span data-ttu-id="8ca00-144">La valeur maximale d'une chaîne de recherche est 256 caractères.</span><span class="sxs-lookup"><span data-stu-id="8ca00-144">The maximum value of a search term is 256 characters.</span></span> <span data-ttu-id="8ca00-145">Si votre recherche trouve une valeur correspondante dans le rapport, le focus est placé sur la partie du rapport qui contient cette valeur.</span><span class="sxs-lookup"><span data-stu-id="8ca00-145">When your search finds a matching value in the report, focus is moved to the part of the report that contains that value.</span></span>  
  
 <span data-ttu-id="8ca00-146">Quand vous entrez une valeur à rechercher, tapez-la telle qu’elle est censée apparaître dans le rapport.</span><span class="sxs-lookup"><span data-stu-id="8ca00-146">When you enter a value to search on, type the value as you expect it to appear in the report.</span></span> <span data-ttu-id="8ca00-147">Ne posez pas une question de type « quel est le bénéfice moyen pour ce mois-ci » à moins que chaque mot de la phrase ne soit censé figurer dans le rapport.</span><span class="sxs-lookup"><span data-stu-id="8ca00-147">Do not pose a question, such as "what is the average profit for this month" unless you expect every word in the sentence to be in the report.</span></span>  
  
 <span data-ttu-id="8ca00-148">Vous ne pouvez rechercher qu'un seul terme ou une seule valeur à la fois.</span><span class="sxs-lookup"><span data-stu-id="8ca00-148">You can only search for one term or value at a time.</span></span> <span data-ttu-id="8ca00-149">Vous ne pouvez pas utiliser d'opérateurs de recherche (par exemple `AND` ou `OR`), de symboles ou de caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="8ca00-149">You cannot use search operators (such as `AND` or `OR`), or symbols and wildcards.</span></span> <span data-ttu-id="8ca00-150">Vous ne pouvez pas effectuer de recherche dans une section croisée des données (par exemple rechercher le chiffre d'affaires correspondant à un mois spécifique pour un produit particulier).</span><span class="sxs-lookup"><span data-stu-id="8ca00-150">You cannot perform a search on a cross-section of the data (for example, searching for net sales for specific month for a particular product).</span></span> <span data-ttu-id="8ca00-151">Pour ce type d'analyse, utilisez le Générateur de rapports afin de créer des rapports générés interactifs.</span><span class="sxs-lookup"><span data-stu-id="8ca00-151">For that kind of analysis, use Report Builder to create clickthrough reports.</span></span>  
  
 <span data-ttu-id="8ca00-152">Les paramètres de sécurité de base de données et de modèle qui restreignent l'accès aux données de rapport s'appliquent également aux opérations de recherche.</span><span class="sxs-lookup"><span data-stu-id="8ca00-152">Database and model security settings that restrict access to report data apply to search operations.</span></span> <span data-ttu-id="8ca00-153">Si vous recherchez une valeur dans un rapport généré interactif qui utilise un modèle comme source de données, et si vous n'avez pas accès à une partie du modèle, les données représentées par cette partie du modèle sont exclues de la recherche.</span><span class="sxs-lookup"><span data-stu-id="8ca00-153">If you are searching for a value in a clickthrough report that uses a model as a data source, and you do not have access to part of the model, data that is represented by that part of the model will be excluded from the search.</span></span>  
  
### <a name="panes-for-specifying-credentials-and-parameters"></a><span data-ttu-id="8ca00-154">Volets destinés à la définition des paramètres et des informations d'identification</span><span class="sxs-lookup"><span data-stu-id="8ca00-154">Panes for Specifying Credentials and Parameters</span></span>  
 <span data-ttu-id="8ca00-155">Les volets**Informations d’identification** et **Paramètres** apparaissent en regard de la zone d’affichage.</span><span class="sxs-lookup"><span data-stu-id="8ca00-155">**Credentials** and **Parameters** are panes that appear next to the view area.</span></span> <span data-ttu-id="8ca00-156">Le volet**Informations d’identification** s’affiche quand la connexion à la source de données du rapport est configurée pour inviter l’utilisateur à entrer un compte et un mot de passe ayant des droits d’accès à la source de données.</span><span class="sxs-lookup"><span data-stu-id="8ca00-156">**Credentials** appears when the data source connection for the report is configured to prompt the user for an account and password that has rights to access the data source.</span></span> <span data-ttu-id="8ca00-157">Le volet**Paramètres** s’affiche quand le rapport accepte une entrée utilisateur liée aux paramètres définis dans le rapport.</span><span class="sxs-lookup"><span data-stu-id="8ca00-157">**Parameters** appears when the report accepts user input for parameters defined in the report.</span></span>  
  
### <a name="setting-properties-on-the-report-viewer-web-part"></a><span data-ttu-id="8ca00-158">Définition des propriétés du composant WebPart Visionneuse de rapports</span><span class="sxs-lookup"><span data-stu-id="8ca00-158">Setting Properties on the Report Viewer Web Part</span></span>  
 <span data-ttu-id="8ca00-159">Les propriétés du composant WebPart incluent des propriétés personnalisées qui sont propres à la visionneuse de rapports et des propriétés générales que vous pouvez définir pour n'importe quel composant WebPart.</span><span class="sxs-lookup"><span data-stu-id="8ca00-159">Properties on the Web Part include custom properties that are specific to Report Viewer and general properties that you can set for any Web Part.</span></span> <span data-ttu-id="8ca00-160">Pour plus d’informations, consultez [Personnaliser le composant WebPart Visionneuse de rapports](../../2014/reporting-services/customize-the-report-viewer-web-part.md).</span><span class="sxs-lookup"><span data-stu-id="8ca00-160">For more information, see [Customize the Report Viewer Web Part](../../2014/reporting-services/customize-the-report-viewer-web-part.md).</span></span>  
  
 <span data-ttu-id="8ca00-161">Par défaut, les rapports s'ouvrent en mode page entière.</span><span class="sxs-lookup"><span data-stu-id="8ca00-161">Reports open in full-page mode by default.</span></span> <span data-ttu-id="8ca00-162">Le mode page entière permet d'afficher la barre d'outils qui fournit les fonctionnalités de navigation entre les pages, de recherche, etc.</span><span class="sxs-lookup"><span data-stu-id="8ca00-162">Full-page mode shows the toolbar that provides page navigation, search, and other functionality.</span></span> <span data-ttu-id="8ca00-163">Vous pouvez personnaliser le composant WebPart afin de modifier l'apparence ou le comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="8ca00-163">You can customize the Web Part to change appearance or default behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ca00-164">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ca00-164">See Also</span></span>  
 <span data-ttu-id="8ca00-165">[Installer ou désinstaller le complément Reporting Services pour SharePoint &#40;SharePoint 2010 et SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="8ca00-165">[Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md) </span></span>  
 [<span data-ttu-id="8ca00-166">Ajouter le composant WebPart Visionneuse de rapports à une page web &#40;Reporting Services en mode intégré SharePoint&#41;</span><span class="sxs-lookup"><span data-stu-id="8ca00-166">Add the Report Viewer Web Part to a Web Page &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md)  
  
  